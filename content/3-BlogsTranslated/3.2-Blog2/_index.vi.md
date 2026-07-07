---
title: "Blog 2"
date: 2026-07-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Amazon DynamoDB - Ch?n Ch? Ð? Throughput Phù H?p Cho ?ng D?ng

## Gi?i thi?u

Trong quá trình phát tri?n ?ng d?ng trên AWS, vi?c l?a ch?n co s? d? li?u phù h?p ?nh hu?ng tr?c ti?p d?n hi?u nang, kh? nang m? r?ng và chi phí v?n hành. V?i nh?ng ?ng d?ng có luu lu?ng l?n ho?c thay d?i liên t?c nhu thuong m?i di?n t?, game online hay h? th?ng serverless, Amazon DynamoDB là m?t l?a ch?n ph? bi?n.

DynamoDB là d?ch v? NoSQL du?c AWS qu?n lý hoàn toàn. Ngu?i dùng không c?n cài d?t máy ch?, b?o trì hay m? r?ng h? t?ng. Tuy nhiên, ngu?i phát tri?n c?n hi?u rõ cách DynamoDB x? lý throughput d? ch?n ch? d? phù h?p.

![DynamoDB Throughput](/fcj-workshop-minhthanh/images/3-BlogsTranslated/blog2/image1.jpeg)

## Capacity Mode trong DynamoDB

Khi t?o b?ng DynamoDB, ngu?i dùng c?n ch?n Capacity Mode. Ðây là co ch? qu?n lý tài nguyên d? x? lý yêu c?u d?c và ghi.

DynamoDB cung c?p hai ch? d? chính:

* On-Demand Capacity
* Provisioned Capacity

Hai ch? d? này d?u ph?c v? m?c tiêu x? lý d? li?u nhanh chóng nhung khác nhau v? cách ho?t d?ng và mô hình tính phí.

## On-Demand Capacity

On-Demand Capacity là ch? d? trong dó AWS t? d?ng qu?n lý kh? nang x? lý c?a b?ng DynamoDB. Ngu?i dùng không c?n khai báo tru?c s? lu?ng Read Capacity Unit (RCU) hay Write Capacity Unit (WCU). DynamoDB s? t? m? r?ng ho?c thu h?p theo luu lu?ng th?c t?.

Ch? d? này phù h?p v?i ?ng d?ng m?i phát tri?n ho?c có luu lu?ng khó d? doán. Ví d?, m?t startup v?a ra m?t ?ng d?ng d?t d? an s? khó bi?t chính xác s? lu?ng ngu?i dùng trong nh?ng ngày d?u. On-Demand giúp h? th?ng dáp ?ng khi traffic tang mà không c?n c?u hình tru?c.

### Uu di?m

* D? tri?n khai, không c?n tính toán RCU/WCU.
* T? d?ng m? r?ng theo nhu c?u th?c t?.
* Ch? tr? ti?n theo s? request d?c và ghi th?c t?.
* Phù h?p v?i ki?n trúc serverless, Lambda và API Gateway.

### H?n ch?

N?u h? th?ng luôn có luu lu?ng l?n và ?n d?nh, On-Demand có th? d?t hon Provisioned Capacity. Ngoài ra, vì chi phí ph? thu?c vào request th?c t? nên ngân sách có th? khó d? doán hon.

### Khi nào nên dùng On-Demand?

On-Demand phù h?p cho ?ng d?ng m?i, h? th?ng dang th? nghi?m, startup chua có d? li?u d? báo, website flash sale, game online có traffic theo s? ki?n và các h? th?ng serverless.

## Provisioned Capacity

Provisioned Capacity là ch? d? ngu?i dùng khai báo tru?c lu?ng tài nguyên mà b?ng DynamoDB s? s? d?ng.

* **Read Capacity Unit (RCU):** don v? do kh? nang d?c d? li?u.
* **Write Capacity Unit (WCU):** don v? do kh? nang ghi d? li?u.

Ví d?, n?u m?t website x? lý 500 don hàng m?i giây và m?i don hàng kho?ng 1 KB, b?ng c?n t?i thi?u 500 WCU d? ghi d? li?u ?n d?nh.

### Auto Scaling

Provisioned Capacity có th? k?t h?p v?i Auto Scaling. Khi m?c s? d?ng vu?t ngu?ng nhu 70%, DynamoDB có th? t? tang RCU/WCU. Khi luu lu?ng gi?m, h? th?ng t? gi?m capacity d? ti?t ki?m chi phí.

### Uu di?m

* Ti?t ki?m chi phí n?u luu lu?ng ?n d?nh.
* Ch? d?ng ki?m soát tài nguyên.
* Phù h?p v?i h? th?ng l?n nhu ERP, CRM, qu?n lý kho ho?c API n?i b?.

### H?n ch?

N?u c?u hình quá th?p, DynamoDB có th? b? throttling. N?u c?u hình quá cao nhung s? d?ng ít, doanh nghi?p v?n ph?i tr? ti?n cho ph?n capacity không dùng d?n. Vi?c theo dõi CloudWatch và di?u ch?nh capacity cung dòi h?i kinh nghi?m v?n hành.

## Warm Throughput

Warm Throughput giúp DynamoDB chu?n b? s?n nang l?c x? lý cho các d?t tang luu lu?ng l?n. Tính nang này h?u ích cho flash sale, h? th?ng bán vé, game online ra m?t phiên b?n m?i ho?c chi?n d?ch marketing có th?i di?m truy c?p cao.

## Throttling và Hot Partition

Throttling x?y ra khi lu?ng request vu?t quá kh? nang x? lý hi?n t?i c?a b?ng ho?c t?ng partition. Ví d?, b?ng ch? có 500 WCU nhung ?ng d?ng g?i 2.000 yêu c?u ghi m?i giây, DynamoDB s? gi?i h?n t?c d? x? lý.

Hot Partition x?y ra khi ph?n l?n request t?p trung vào m?t partition key duy nh?t. Ð? tránh tình tr?ng này, c?n thi?t k? partition key sao cho d? li?u du?c phân b? d?u.

## Nên ch?n Capacity Mode nào?

Nên ch?n **On-Demand Capacity** khi ?ng d?ng m?i phát tri?n, chua d? doán du?c ngu?i dùng, có traffic d?t bi?n ho?c xây d?ng theo ki?n trúc serverless.

Nên ch?n **Provisioned Capacity** khi h? th?ng dã ?n d?nh, có d? li?u l?ch s? d? d? doán luu lu?ng, mu?n t?i uu chi phí dài h?n và có d?i ngu v?n hành theo dõi capacity.

Trong th?c t?, nhi?u doanh nghi?p b?t d?u v?i On-Demand d? gi?m công s?c qu?n tr?. Khi ?ng d?ng phát tri?n và luu lu?ng ?n d?nh hon, h? chuy?n sang Provisioned Capacity d? ti?t ki?m chi phí.

## K?t lu?n

Throughput là y?u t? quan tr?ng khi làm vi?c v?i DynamoDB vì nó ?nh hu?ng d?n hi?u nang, kh? nang m? r?ng và chi phí. On-Demand don gi?n và linh ho?t, còn Provisioned giúp ki?m soát chi phí t?t hon v?i workload ?n d?nh.

Bên c?nh Capacity Mode, các khái ni?m nhu Warm Throughput, Throttling và Hot Partition cung cho th?y r?ng thi?t k? partition key, theo dõi CloudWatch và s? d?ng Auto Scaling dúng cách là di?u c?n thi?t d? h? th?ng DynamoDB v?n hành hi?u qu?.
