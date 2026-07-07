---
title: "Tri?n khai CloudFormation stack"
date: 2026-07-04
weight: 5
chapter: false
pre: " <b> 5.4.5. </b> "
---

## Stack 0: Global WAF

Chuy?n AWS Console sang region **United States (N. Virginia) `us-east-1`**. M? CloudFormation và t?o stack b?ng template có s?n. Upload file `00-cf-hashop-global-waf.yaml`.

![Upload WAF template](/images/5-Workshop/hashop-deployment/image7.png)

Ch?n **Next**.

![Thông tin WAF stack](/images/5-Workshop/hashop-deployment/image8.png)

Ð?t stack name là `HaShop-WAF`, sau dó ti?p t?c ch?n **Next**.

![Ð?t tên WAF stack](/images/5-Workshop/hashop-deployment/image9.png)

Ki?m tra l?i c?u hình và ch?n **Submit**.

![Submit WAF stack](/images/5-Workshop/hashop-deployment/image10.png)

Sau khi stack t?o xong, m? tab **Outputs** và ghi l?i `FrontendWebAclArn`. ARN này s? du?c dùng khi tri?n khai foundation stack.

## Stack 01: Foundation

Chuy?n AWS Console v? region **Singapore `ap-southeast-1`**. T?o CloudFormation stack m?i và upload file `01-cf-hashop-foundation.yaml`.

![Upload foundation template](/images/5-Workshop/hashop-deployment/image11.png)

Ð?t stack name chính xác là `cf-hashop-foundation`.

![Ð?t tên foundation stack](/images/5-Workshop/hashop-deployment/image12.png)

Nh?p các parameter c?n thi?t:

- `DbPassword`: m?t kh?u cho database.
- `InternalApiKey`: internal API key g?m 16 ký t?.
- `AdminEmail`: email c?a ngu?i qu?n tr?.
- `SesFromEmail`: email g?i dã du?c xác th?c trong SES.

![Parameter c?a foundation stack](/images/5-Workshop/hashop-deployment/image13.png)

Thi?t l?p parameter cho Lambda artifact:

- `LambdaCodeS3Bucket`: `hashop-artifacts-<ACCOUNT_ID>-ap-southeast-1`
- `LambdaCodeS3Key`: `lambda/post-confirmation/function.zip`
- `FrontendWebAclArn`: ARN dã l?y t? Stack 0

![Parameter Lambda và WAF](/images/5-Workshop/hashop-deployment/image14.png)

Ti?p t?c d?n trang review, tích ch?n xác nh?n CloudFormation có th? t?o IAM resource v?i custom name, r?i submit stack.

N?u ECS task b? fail do IAM role chua k?p propagate, có th? delete stack b? l?i và ch?y l?i.

## Stack 02: ECS services

Ð?i Stack 01 tri?n khai xong. Quá trình này có th? m?t kho?ng 20 phút. Sau dó t?o CloudFormation stack m?i b?ng file `02-cf-hashop-ecs-services.yaml`. Ð?t stack name là `cf-hashop-ecs`.

![T?o ECS services stack](/images/5-Workshop/hashop-deployment/image15.png)

? ph?n container image, thay `<ACCOUNT_ID>` b?ng AWS account ID th?t.

![Parameter container image c?a ECS](/images/5-Workshop/hashop-deployment/image16.png)

## Stack 03: Database initialization

Stack 03 có th? b?t d?u sau khi Stack 02 dã du?c submit. T?o CloudFormation stack m?i b?ng file `03-cf-hashop-db-init.yaml`.

![Upload database initialization template](/images/5-Workshop/hashop-deployment/image17.png)

Ð?t tên cho database initialization stack.

![Ð?t tên database initialization stack](/images/5-Workshop/hashop-deployment/image18.png)

Ki?m tra l?i c?u hình stack.

![Review database initialization stack](/images/5-Workshop/hashop-deployment/image19.png)

Tích ch?n xác nh?n CloudFormation có th? t?o IAM resource v?i custom name, sau dó submit stack.
