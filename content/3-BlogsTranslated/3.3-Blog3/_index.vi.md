---
title: "Blog 3"
date: 2026-07-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Gi?m Lãng Phí EC2 - Right-Sizing T? Ð?ng V?i Compute Optimizer, CloudWatch Và Automation

## 1. Hóa don EC2: n?i lo không c?a riêng ai

Khi v?n hành h? t?ng AWS, chi phí EC2 thu?ng là m?t trong nh?ng ph?n d? tang nh?t. Nhi?u d?i tri?n khai EC2 theo hu?ng "ch?n du cho ch?c", copy c?u hình t? d? án cu ho?c không rà soát l?i sau khi workload thay d?i. K?t qu? là nhi?u instance ch?y quá l?n so v?i nhu c?u th?c t?.

![EC2 Right-Sizing Automation](/fcj-workshop-minhthanh/images/3-BlogsTranslated/blog3/image1.png)

## 2. V?n d?: vì sao lãng phí x?y ra?

M?t s? nguyên nhân ph? bi?n:

* Overprovisioning: ch?n instance l?n hon nhu c?u th?t.
* Thi?u dánh giá d?nh k?: không có quy trình rà soát và di?u ch?nh.
* Quy trình th? công: k? su ph?i t? phân tích metrics và t? quy?t d?nh thay d?i.

H?u qu? là hóa don tang không c?n thi?t, tài nguyên b? s? d?ng kém hi?u qu? và d?i ngu k? thu?t m?t th?i gian cho các thao tác t?i uu l?p l?i.

## 3. Gi?i pháp t?ng quan: Right-sizing t? d?ng

M?c tiêu c?a right-sizing t? d?ng là phát hi?n instance dang overprovisioned ho?c underutilized, sau dó d? xu?t ho?c áp d?ng thay d?i m?t cách an toàn.

B? gi?i pháp g?m:

* **AWS Compute Optimizer:** phân tích CPU, memory, network và disk I/O d? dua ra recommendation.
* **CloudWatch:** thu th?p metrics l?ch s?, t?o dashboard và c?nh báo.
* **Automation:** s? d?ng Lambda, SSM Automation, Systems Manager Run Command ho?c Step Functions d? áp d?ng thay d?i.
* **Governance:** yêu c?u phê duy?t tru?c khi thay d?i production, s? d?ng tagging và audit trail.

## 4. Flow ho?t d?ng d? xu?t

1. Compute Optimizer thu th?p d? li?u trong 14-30 ngày và tr? v? recommendation theo t?ng instance.
2. H? th?ng l?c các recommendation có d? tin c?y cao, b? qua instance stateful, database ho?c tài nguyên quan tr?ng d?a trên tag.
3. Th? nghi?m c?u hình m?i trên staging b?ng AMI ho?c Launch Template.
4. Áp d?ng cho production b?ng rolling update trong Auto Scaling Group ho?c quy trình stop/modify/start v?i maintenance window.
5. CloudWatch theo dõi latency, error rate, CPU, memory và kích ho?t rollback n?u vu?t ngu?ng.

## 5. Hu?ng d?n tri?n khai nhanh

* B?t Compute Optimizer cho account ho?c organization.
* Ð?i ít nh?t 14 ngày d? có d? li?u d? t?t.
* B?t export recommendation sang S3 ho?c l?y d? li?u qua API/SDK.
* Vi?t Lambda ho?c script l?c recommendation h?ng ngày.
* T?o workflow phê duy?t qua Slack ho?c pull request.
* Áp d?ng thay d?i b?ng SSM Automation ho?c rolling update.
* Thi?t l?p CloudWatch dashboard và alarm cho rollback.

## 6. Checklist tri?n khai

* B?t Compute Optimizer.
* Thi?t l?p export recommendation.
* G?n tag `do-not-rightsize` cho instance không du?c t? d?ng thay d?i.
* L?c recommendation theo confidence, môi tru?ng và tag quan tr?ng.
* Ki?m th? trên staging tru?c khi áp d?ng production.
* Luu audit trail b?ng CloudTrail và S3 logs.

## 7. Khi nào nên và không nên áp d?ng?

Phù h?p v?i stateless web server, API server, worker node, batch worker, Auto Scaling Group-managed fleet và workload có th? kh?i d?ng l?i nhanh.

C?n cân nh?c k? v?i database production ch?y trên EC2, workload có local state, instance có licensing g?n v?i ph?n c?ng ho?c ?ng d?ng có boot sequence d?c thù.

## 8. Bài h?c quan tr?ng

* B?t d?u t? non-production tru?c.
* Chu?n hóa tagging và inventory.
* Luôn có quy trình test và rollback.
* K?t h?p automation v?i phê duy?t cho workload quan tr?ng.
* K?t h?p right-sizing v?i Savings Plans và Reserved Instances d? t?i uu chi phí dài h?n.

## 9. Ví d? policy l?c

Ch? xem xét recommendation khi confidence t? 70% tr? lên, instance không ph?i `prod-db`, uptime d? dài, CPU median du?i 30% và memory median du?i 40% trong 14 ngày.

V?i môi tru?ng non-production có th? t? d?ng phê duy?t. V?i production, h? th?ng nên t?o pull request ho?c Slack notification và ch? phê duy?t th? công.

## 10. K?t lu?n

Right-sizing t? d?ng là cách hi?u qu? d? gi?m chi phí EC2 mà v?n duy trì ?n d?nh h? th?ng. Khi k?t h?p Compute Optimizer, CloudWatch và automation an toàn, doanh nghi?p có th? gi?m lãng phí, gi? hi?u nang ?n d?nh và gi?m công vi?c th? công cho k? su v?n hành.
