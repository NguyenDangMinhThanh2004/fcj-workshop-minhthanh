---
title: "Package và upload Lambda PostConfirmation"
date: 2026-07-04
weight: 2
chapter: false
pre: " <b> 5.4.2. </b> "
---

Lambda PostConfirmation du?c Amazon Cognito g?i sau khi ngu?i dùng xác nh?n tài kho?n. Lambda này ghi thông tin user vào Amazon RDS MySQL.

V?n gi? c?a s? terminal cu t? bu?c tru?c và ch?y các l?nh bên du?i trong chính c?a s? này. Terminal này dang ch?a các bi?n tri?n khai:

```powershell
$REGION = "ap-southeast-1"
$ACCOUNT_ID = $(aws sts get-caller-identity --query Account --output text)
$ARTIFACT_BUCKET = "hashop-artifacts-$ACCOUNT_ID-$REGION"
```

Di chuy?n vào thu m?c source c?a Lambda:

```powershell
cd D:\HaShop-release\cognito-post-confirmation-db
```

Cài dependency c?n thi?t:

```powershell
npm install mysql2
```

Nén source code thành `function.zip`:

```powershell
Compress-Archive `
  -Path .\index.js, .\node_modules, .\package.json, .\package-lock.json `
  -DestinationPath .\function.zip `
  -Force
```

Upload package lên artifact bucket:

```powershell
aws s3 cp .\function.zip "s3://$ARTIFACT_BUCKET/lambda/post-confirmation/function.zip" --region $REGION
```

Ki?m tra file dã du?c upload:

```powershell
aws s3 ls "s3://$ARTIFACT_BUCKET/lambda/post-confirmation/function.zip" --region $REGION
```

![Upload Lambda PostConfirmation package](/images/5-Workshop/hashop-deployment/image2.png)
