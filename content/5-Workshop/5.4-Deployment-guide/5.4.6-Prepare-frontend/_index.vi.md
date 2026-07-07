---
title: "Chu?n b? và publish frontend"
date: 2026-07-04
weight: 6
chapter: false
pre: " <b> 5.4.6. </b> "
---

Clone frontend repository t? thu m?c release:

```powershell
cd D:\HaShop-release
git clone https://github.com/Leviethaidang/Front-end.git
cd Front-end
```

S? d?ng branch `main` vì dây là phiên b?n ?n d?nh dã du?c ki?m th? cho quy trình tri?n khai này.

Sau khi Stack 01 t?o thành công, m? ph?n outputs c?a stack và l?y:

- `FrontendBucketName`
- `FrontendCloudFrontDistributionId`

![Output c?a frontend stack](/fcj-workshop-minhthanh/images/5-Workshop/hashop-deployment/image20.png)

Khai báo các bi?n tri?n khai frontend:

```powershell
$FRONTEND_BUCKET = "<FrontendBucketName>"
$REGION = "ap-southeast-1"
$FRONTEND_DISTRIBUTION_ID = "<FrontendCloudFrontDistributionId>"
```

Ð?ng b? source frontend lên S3 frontend bucket:

```powershell
aws s3 sync "." "s3://$FRONTEND_BUCKET" `
  --delete `
  --region $REGION
```

T?o CloudFront invalidation d? ngu?i dùng nh?n du?c phiên b?n frontend m?i nh?t:

```powershell
aws cloudfront create-invalidation `
  --distribution-id $FRONTEND_DISTRIBUTION_ID `
  --paths "/*"
```

![Sync frontend lên S3](/fcj-workshop-minhthanh/images/5-Workshop/hashop-deployment/image21.png)

![T?o CloudFront invalidation](/fcj-workshop-minhthanh/images/5-Workshop/hashop-deployment/image22.png)
