---
title: "Xem log trong CloudWatch"
date: 2026-07-04
weight: 7
chapter: false
pre: " <b> 5.5.7. </b> "
---

Trên AWS Console, m?:

```text
CloudWatch -> Log groups
```

Tìm log group c?a các ECS service và Lambda liên quan. Ki?m tra log c?a:

- `user-api`
- `product-api`
- `inventory-api`
- `cart-api`
- `order-api`
- `payment-api`
- `payment-worker`
- `order-worker`
- `notification-worker`
- Lambda PostConfirmation

![CloudWatch log groups](/images/5-Workshop/hashop-test-cleanup/image9.png)

K?t qu? mong d?i:

- Không có l?i nghiêm tr?ng nhu `CannotPullContainerError`.
- Không có l?i k?t n?i database.
- Không có l?i JWT verify failed.
- Không có l?i SQS permission denied.
