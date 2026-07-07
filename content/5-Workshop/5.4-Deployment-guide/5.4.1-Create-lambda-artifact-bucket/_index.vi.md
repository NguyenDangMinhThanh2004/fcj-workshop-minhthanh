---
title: "T?o S3 bucket ch?a Lambda artifact"
date: 2026-07-04
weight: 1
chapter: false
pre: " <b> 5.4.1. </b> "
---

Ð?u tiên, t?o thu m?c `D:\HaShop-release`. Ðây s? là thu m?c thao tác chính cho toàn b? quá trình tri?n khai HaShop, dùng d? luu source code c?a d? án, package Lambda, template CloudFormation và các artifact c?n thi?t trong các bu?c tri?n khai phía sau. Sau khi t?o thu m?c làm vi?c này, clone repository c?a Lambda PostConfirmation vào bên trong.

```powershell
mkdir D:\HaShop-release
cd D:\HaShop-release
git clone https://github.com/Leviethaidang/cognito-post-confirmation-db.git
```

Khai báo các bi?n tri?n khai:

```powershell
$REGION = "ap-southeast-1"
$ACCOUNT_ID = $(aws sts get-caller-identity --query Account --output text)
$ARTIFACT_BUCKET = "hashop-artifacts-$ACCOUNT_ID-$REGION"
```

T?o artifact bucket:

```powershell
aws s3api create-bucket `
  --bucket $ARTIFACT_BUCKET `
  --region $REGION `
  --create-bucket-configuration LocationConstraint=$REGION
```

B?t Block Public Access:

```powershell
aws s3api put-public-access-block `
  --bucket $ARTIFACT_BUCKET `
  --public-access-block-configuration BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true
```

B?t server-side encryption:

```powershell
$SSE_CONFIG = "$env:TEMP\hashop-s3-sse.json"
@'
{"Rules": [{"ApplyServerSideEncryptionByDefault": {"SSEAlgorithm": "AES256"}}]}
'@ | Set-Content -Path $SSE_CONFIG -Encoding ascii

aws s3api put-bucket-encryption `
  --bucket $ARTIFACT_BUCKET `
  --server-side-encryption-configuration "file://$SSE_CONFIG"
```

![T?o Lambda artifact bucket](/images/5-Workshop/hashop-deployment/image1.png)
