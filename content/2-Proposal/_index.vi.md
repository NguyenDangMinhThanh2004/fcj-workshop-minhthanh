---
title: "B?n d? xu?t"
date: 2026-07-02
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# HaShop E-commerce Platform
## Gi?i pháp thuong m?i di?n t? Microservices trên AWS k?t h?p Event-Driven Architecture

### 1. Tóm t?t di?u hành

HaShop là n?n t?ng thuong m?i di?n t? bán qu?n áo tr?c tuy?n du?c xây d?ng trên Amazon Web Services (AWS). D? án áp d?ng ki?n trúc **Microservices** k?t h?p **Event-Driven Architecture** nh?m t?o ra m?t h? th?ng có kh? nang m? r?ng, d? b?o trì, b?o m?t t?t và phù h?p d? tri?n khai trong môi tru?ng cloud-native.

H? th?ng s? d?ng **Amazon ECS Fargate** d? ch?y các backend service d?ng container, **Amazon Cognito** d? xác th?c ngu?i dùng, **Amazon RDS MySQL** d? luu tr? d? li?u nghi?p v?, **Amazon S3** và **Amazon CloudFront** d? phân ph?i frontend và hình ?nh s?n ph?m. Các tác v? b?t d?ng b? nhu x? lý thanh toán, c?p nh?t tr?ng thái don hàng và g?i email thông báo du?c tri?n khai b?ng **Amazon SNS**, **Amazon SQS** và các worker service ch?y trên ECS Fargate.

M?c tiêu c?a d? án không ch? là xây d?ng m?t website thuong m?i di?n t? d?y d? ch?c nang co b?n, mà còn là co h?i d? th?c hành các thành ph?n AWS quan tr?ng nhu networking, security, container orchestration, service discovery, event-driven processing, observability và infrastructure as code thông qua AWS CloudFormation.

### 2. Tuyên b? v?n d?

#### V?n d? hi?n t?i

Các website thuong m?i di?n t? truy?n th?ng n?u xây d?ng theo mô hình monolithic thu?ng g?p khó khan khi h? th?ng phát tri?n l?n hon. Khi toàn b? ch?c nang nhu ngu?i dùng, s?n ph?m, gi? hàng, don hàng, thanh toán và thông báo n?m trong cùng m?t ?ng d?ng, vi?c s?a d?i ho?c m? r?ng m?t ch?c nang có th? ?nh hu?ng d?n toàn b? h? th?ng.

Bên c?nh dó, m?t s? tác v? nhu thanh toán, g?i email ho?c c?p nh?t tr?ng thái don hàng không nh?t thi?t ph?i x? lý d?ng b? trong cùng request c?a ngu?i dùng. N?u m?i tác v? d?u x? lý tr?c ti?p trong lu?ng chính, h? th?ng d? b? ch?m, khó m? r?ng và khó ki?m soát l?i khi m?t thành ph?n ph? g?p s? c?.

#### Gi?i pháp d? xu?t

HaShop tách h? th?ng thành nhi?u microservice d?c l?p nhu User Service, Product Service, Inventory Service, Cart Service, Order Service, Payment Service và các worker x? lý b?t d?ng b?. Các service du?c dóng gói b?ng Docker và tri?n khai trên Amazon ECS Fargate trong private subnet d? gi?m nhu c?u qu?n lý máy ch? và tang m?c d? b?o m?t.

Frontend du?c tri?n khai du?i d?ng static website trên Amazon S3 và phân ph?i qua Amazon CloudFront. CloudFront Function du?c dùng d? rewrite các clean route nhu `/login`, `/profile`, `/cart` ho?c `/products/:id` v? các file HTML tuong ?ng. Các API request có ti?n t? `/api/*` du?c CloudFront chuy?n ti?p d?n Application Load Balancer, sau dó ALB d?nh tuy?n request d?n backend service phù h?p.

Amazon Cognito qu?n lý dang ký, xác nh?n tài kho?n, dang nh?p và phát hành JWT token. Backend service ki?m tra token b?ng middleware tru?c khi x? lý các API c?n xác th?c. Sau khi ngu?i dùng xác nh?n tài kho?n, Cognito kích ho?t Lambda PostConfirmation d? d?ng b? thông tin user vào Amazon RDS MySQL.

Các tác v? b?t d?ng b? du?c x? lý b?ng Amazon SNS và Amazon SQS. Khi ngu?i dùng d?t hàng b?ng MOMO ho?c BANK, Order Service publish s? ki?n thanh toán vào SNS Topic. Message du?c fanout d?n SQS Queue d? Payment Worker x? lý. Sau dó k?t qu? thanh toán ti?p t?c du?c publish qua SNS/SQS d? Order Worker c?p nh?t tr?ng thái don hàng và Notification Worker g?i email thông báo.

#### L?i ích

Gi?i pháp giúp h? th?ng d? m? r?ng theo t?ng domain nghi?p v?, gi?m r?i ro khi tri?n khai thay d?i và giúp t?ng service có th? du?c ki?m th? d?c l?p. Event-Driven Architecture giúp các tác v? n?ng ho?c không c?n ph?n h?i ngay du?c tách kh?i request chính, t? dó c?i thi?n tr?i nghi?m ngu?i dùng và tang kh? nang ch?u l?i c?a h? th?ng.

### 3. Ki?n trúc gi?i pháp

HaShop s? d?ng ki?n trúc cloud-native trên AWS v?i các l?p chính: **Edge/Frontend Layer**, **Authentication Layer**, **Application Layer**, **Async Processing Layer**, **Data Layer** và **Management/Observability Layer**.

![HaShop AWS Architecture](/fcj-workshop-minhthanh/images/2-Proposal/hashop-architecture.png)

? l?p Edge/Frontend, ngu?i dùng truy c?p website thông qua Amazon CloudFront. CloudFront phân ph?i static frontend t? S3, áp d?ng CloudFront Function cho route rewrite và chuy?n ti?p request `/api/*` d?n Application Load Balancer. AWS WAF du?c d?t ? phía tru?c d? tang kh? nang b?o v? ?ng d?ng kh?i các request b?t thu?ng.

Authentication Layer s? d?ng Amazon Cognito d? qu?n lý user pool, app client, xác nh?n tài kho?n và phát hành JWT token. Lambda PostConfirmation du?c dùng d? ghi thông tin ngu?i dùng m?i vào database sau khi tài kho?n du?c xác nh?n.

Application Layer du?c tri?n khai b?ng Amazon ECS Fargate. Các API service và worker service ch?y trong private subnet, không gán public IP. Các service giao ti?p n?i b? thông qua ECS Service Connect k?t h?p AWS Cloud Map namespace.

Async Processing Layer s? d?ng SNS và SQS. SNS Topic dóng vai trò phát s? ki?n, SQS Queue luu message d? worker x? lý theo co ch? long polling. Payment Worker, Order Worker và Notification Worker x? lý message d?c l?p, giúp gi?m coupling gi?a các service.

Data Layer s? d?ng Amazon RDS MySQL tri?n khai trong private DB subnet và có Multi-AZ Replication d? tang tính s?n sàng. H? th?ng chia d? li?u theo domain nhu user, product, inventory, cart, order và payment d? phù h?p v?i ki?n trúc microservices.

Management/Observability Layer s? d?ng AWS Secrets Manager d? luu thông tin nh?y c?m và Amazon CloudWatch Logs d? thu th?p log t? ECS service, worker và Lambda.

### 4. D?ch v? AWS s? d?ng

| D?ch v? | Vai trò trong h? th?ng |
|---|---|
| Amazon CloudFront | Phân ph?i frontend, forward API request và phân ph?i hình ?nh s?n ph?m. |
| CloudFront Function | Rewrite clean route c?a frontend v? các file HTML tuong ?ng. |
| AWS WAF | B?o v? ?ng d?ng ? l?p edge tru?c các request b?t thu?ng. |
| Amazon S3 | Luu tr? static frontend và hình ?nh s?n ph?m. |
| Application Load Balancer | Nh?n request `/api/*` và route d?n ECS service theo path. |
| Amazon ECS Fargate | Ch?y backend API service và worker service d?ng container. |
| ECS Service Connect / AWS Cloud Map | H? tr? service discovery và giao ti?p n?i b? gi?a các microservice. |
| Amazon Cognito | Qu?n lý dang ký, xác nh?n tài kho?n, dang nh?p và JWT token. |
| AWS Lambda | X? lý PostConfirmation trigger t? Cognito. |
| Amazon RDS MySQL | Luu tr? d? li?u user, product, inventory, cart, order và payment. |
| Amazon SNS | Phát s? ki?n thanh toán và thông báo. |
| Amazon SQS | Luu message d? worker x? lý b?t d?ng b?. |
| Amazon SES | G?i email thông báo cho ngu?i dùng và qu?n tr? viên. |
| AWS Secrets Manager | Luu tr? database credentials, Cognito config và internal API key. |
| Amazon CloudWatch Logs | Theo dõi log và h? tr? ki?m tra l?i. |
| AWS IAM | Phân quy?n cho ECS task, Lambda và các AWS service. |
| AWS CloudFormation | T? d?ng hóa tri?n khai h? t?ng. |
| VPC Endpoints | Cho phép ECS trong private subnet truy c?p AWS service qua du?ng private. |

### 5. Thi?t k? thành ph?n

- **Frontend:** Giao di?n HTML/CSS/JavaScript du?c luu trên S3 và phân ph?i qua CloudFront.
- **User Service:** X? lý dang ký, dang nh?p, h? so ngu?i dùng và qu?n tr? user; tích h?p v?i Amazon Cognito.
- **Product Service:** Qu?n lý s?n ph?m, danh m?c, size, màu s?c, bi?n th? s?n ph?m và hình ?nh.
- **Inventory Service:** Qu?n lý t?n kho theo t?ng bi?n th? s?n ph?m.
- **Cart Service:** Qu?n lý gi? hàng và ki?m tra thông tin s?n ph?m/t?n kho thông qua service n?i b?.
- **Order Service:** X? lý d?t hàng, qu?n lý tr?ng thái don hàng và phát s? ki?n thanh toán.
- **Payment Service:** Qu?n lý phuong th?c thanh toán c?a ngu?i dùng.
- **Payment Worker:** X? lý yêu c?u thanh toán b?t d?ng b? t? SQS.
- **Order Worker:** Nh?n k?t qu? thanh toán và c?p nh?t tr?ng thái don hàng.
- **Notification Worker:** Nh?n s? ki?n thông báo và g?i email qua Amazon SES.
- **RDS MySQL:** Luu d? li?u chính c?a h? th?ng nhu user, product, inventory, cart, order và payment.

### 6. Tri?n khai k? thu?t

#### Các giai do?n tri?n khai

1. **Phân tích yêu c?u và thi?t k? ki?n trúc:** Xác d?nh các ch?c nang chính c?a website bán qu?n áo, l?a ch?n ki?n trúc microservices, thi?t k? so d? AWS, xác d?nh backend service, database và lu?ng x? lý b?t d?ng b?.
2. **Xây d?ng backend microservices:** Phát tri?n các service Node.js/Express g?m User, Product, Inventory, Cart, Order, Payment và Notification. M?i service có trách nhi?m riêng, s? d?ng database riêng theo domain và giao ti?p qua API n?i b?.
3. **Tích h?p xác th?c và phân quy?n:** Tích h?p Amazon Cognito d? qu?n lý dang ký, xác nh?n tài kho?n, dang nh?p và JWT token. Backend service dùng middleware d? verify access token. Cognito Groups du?c dùng d? phân quy?n Admin và Customer.
4. **Xây d?ng lu?ng event-driven:** S? d?ng SNS và SQS d? x? lý thanh toán và notification b?t d?ng b?. Các worker service ch?y trên ECS Fargate và long-poll SQS Queue d? x? lý message.
5. **Tri?n khai h? t?ng AWS và ki?m th?:** Ban d?u h? th?ng du?c tri?n khai th? công trên AWS Console d? ki?m tra t?ng thành ph?n nhu VPC, RDS, ECS, ALB, CloudFront, SNS/SQS, Cognito và Lambda.
6. **Ki?m th?, s?a l?i và t?i uu:** Ki?m th? toàn b? flow t? frontend d?n backend, bao g?m dang ký, dang nh?p, qu?n lý s?n ph?m, thêm vào gi? hàng, checkout COD, checkout MOMO/BANK, x? lý worker và g?i email.

#### Yêu c?u k? thu?t

- **Backend:** Node.js, Express.js, MySQL client, AWS SDK, Cognito JWT verifier.
- **Frontend:** HTML, CSS, JavaScript, static hosting trên S3.
- **Containerization:** Docker image cho t?ng service, luu trên Amazon ECR.
- **Compute:** Amazon ECS Fargate cho API service và worker service.
- **Database:** Amazon RDS MySQL.
- **Authentication:** Amazon Cognito User Pool, App Client và Cognito Groups.
- **Networking:** VPC, public subnet, private app subnet, private DB subnet, NAT Gateway, VPC Endpoint và Security Group.
- **Event-driven processing:** Amazon SNS, Amazon SQS và ECS worker service.
- **Storage:** S3 Frontend Bucket và S3 Product Images Bucket.
- **Observability:** Amazon CloudWatch Logs.

### 7. L? trình & m?c tri?n khai

| Giai do?n | N?i dung chính |
|---|---|
| Giai do?n 1: Phân tích và thi?t k? | Xác d?nh yêu c?u nghi?p v?, thi?t k? ki?n trúc microservices trên AWS, xác d?nh service, database và lu?ng x? lý chính. |
| Giai do?n 2: Phát tri?n backend và frontend | Xây d?ng các service User, Product, Inventory, Cart, Order, Payment, Notification và giao di?n HTML/CSS/JavaScript. |
| Giai do?n 3: Tri?n khai AWS | T?o VPC, subnet, security group, RDS, Cognito, Lambda, S3, CloudFront, ECS, ALB, SNS và SQS b?ng AWS Console. |
| Giai do?n 4: Ki?m th? và t?i uu | Ki?m th? ch?c nang, s?a l?i c?u hình, b? sung VPC Endpoint, hoàn thi?n so d? ki?n trúc và chu?n b? CloudFormation template. |

### 8. U?c tính ngân sách

Chi phí c?a h? th?ng ph? thu?c vào th?i gian ch?y ECS Fargate, s? lu?ng RDS instance, NAT Gateway, CloudFront, S3, SNS/SQS và lu?ng request th?c t?. Do d? án ph?c v? m?c dích h?c t?p và demo, c?u hình du?c gi? ? m?c nh? nh?t có th?.

| Nhóm chi phí | C?u hình u?c tính | Chi phí/tháng |
|---|---|---:|
| Amazon ECS Fargate | 9 tasks, m?i task 0.5 vCPU và 1 GB RAM | 198.43 USD |
| Amazon RDS MySQL | 2 DB instances db.t3.micro, Single-AZ, 20 GB storage m?i DB | 43.48 USD |
| Application Load Balancer | 1 ALB ch?y liên t?c, u?c tính 1 LCU | 25.55 USD |
| NAT Gateway | 1 NAT Gateway ch?y liên t?c, kho?ng 1 GB data x? lý | 43.13 USD |
| VPC Endpoints | 6 Interface Endpoints trên 2 AZ; S3 Gateway Endpoint không tính phí hourly | 122.65 USD |
| Amazon S3 | Kho?ng 6 GB luu frontend, hình ?nh s?n ph?m và artifact | 0.16 USD |
| Amazon CloudFront | Kho?ng 1 GB data transfer và 20,000 HTTPS requests | 0.00 USD |
| AWS WAF | 1 CloudFront Web ACL, 3 AWS Managed Rule Groups, 1 rate-based rule, kho?ng 20,000 requests/tháng | 9.01 USD |
| Amazon SNS/SQS | Kho?ng 10,000 messages/tháng | 0.01 USD |
| Amazon Cognito | Kho?ng 20 monthly active users | 0.00 USD |
| AWS Lambda | Kho?ng 1,000 invocations/tháng, 256 MB | 0.00 USD |
| CloudWatch Logs | Kho?ng 1 GB log ingested và 1 GB log stored | 0.53 USD |
| Amazon SES | Kho?ng 1,000 email/tháng | 0.10 USD |
| AWS Secrets Manager | 4 secrets, kho?ng 10,000 API calls/tháng | 1.65 USD |
| Amazon ECR | 7 Docker images, kho?ng 3.5 GB private repository storage | 0.35 USD |

**T?ng chi phí u?c tính:** kho?ng **444.92 USD/tháng**, tuong duong **5,339.04 USD cho 12 tháng**.

### 9. Ðánh giá r?i ro

| R?i ro | M?c ?nh hu?ng | Xác su?t | Chi?n lu?c gi?m thi?u |
|---|---|---|---|
| Sai c?u hình networking ho?c security group | Cao | Trung bình | Chu?n hóa h? t?ng b?ng CloudFormation, ki?m tra target group health check và rule security group sau m?i l?n deploy. |
| Sai c?u hình Cognito ho?c JWT verification | Cao | Trung bình | Ki?m th? dang ký, dang nh?p, token expiration và API authorization tru?c khi tích h?p toàn h? th?ng. |
| Sai c?u hình Service Connect | Trung bình d?n cao | Trung bình | Ki?m tra DNS n?i b?, namespace Cloud Map và log c?a t?ng service. |
| Worker không x? lý du?c message t? SQS | Cao | Trung bình | Theo dõi SQS, DLQ và CloudWatch Logs c?a worker service. |
| Vu?t chi phí AWS | Trung bình | Trung bình | Dùng AWS Budget, t?t tài nguyên không c?n thi?t và gi? c?u hình ? m?c demo. |

N?u m?t service g?p l?i, nhóm có th? ki?m tra log riêng trong CloudWatch và c?p nh?t task definition ho?c CloudFormation template. N?u worker x? lý message l?i, có th? ki?m tra SQS Queue, DLQ và log worker d? xác d?nh nguyên nhân tru?c khi replay ho?c x? lý l?i message.

### 10. K?t qu? k? v?ng

Sau khi hoàn thành, HaShop cung c?p m?t h? th?ng thuong m?i di?n t? d?y d? các ch?c nang co b?n g?m dang ký, dang nh?p, qu?n lý s?n ph?m, qu?n lý t?n kho, gi? hàng, d?t hàng, thanh toán mô ph?ng và g?i email thông báo.

V? m?t k? thu?t, d? án ch?ng minh kh? nang áp d?ng ki?n trúc Microservices và Event-Driven Architecture trên AWS trong m?t bài toán th?c t?. Nhóm có th? n?m du?c cách tri?n khai ?ng d?ng container trên ECS Fargate, s? d?ng Cognito d? xác th?c, thi?t k? database theo domain, x? lý tác v? b?t d?ng b? b?ng SNS/SQS và phân ph?i frontend b?ng S3/CloudFront.

V? giá tr? dài h?n, d? án có th? ti?p t?c m? r?ng thành m?t n?n t?ng thuong m?i di?n t? hoàn ch?nh hon, b? sung các ch?c nang nhu d?t may theo s? do, qu?n lý khuy?n mãi, dánh giá s?n ph?m, thanh toán th?t v?i c?ng thanh toán bên ngoài, dashboard phân tích doanh thu và CI/CD t? d?ng.
