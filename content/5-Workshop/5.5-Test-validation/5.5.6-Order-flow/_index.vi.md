---
title: "Ki?m tra lu?ng d?t hàng"
date: 2026-07-04
weight: 6
chapter: false
pre: " <b> 5.5.6. </b> "
---

Th?c hi?n các k?ch b?n d?t hàng trên website:

1. Admin t?o category, size, color, product và t?n kho.
2. Customer thêm s?n ph?m vào gi? hàng.
3. Customer checkout b?ng COD.
4. Customer checkout b?ng phuong th?c MOMO/BANK demo.
5. Ki?m tra tr?ng thái don hàng.

K?t qu? mong d?i:

- Ðon COD du?c xác nh?n tr?c ti?p.
- Ðon MOMO/BANK chuy?n sang tr?ng thái ch? thanh toán.
- `payment-worker` x? lý message t? SQS.
- `order-worker` c?p nh?t tr?ng thái don hàng sau khi có k?t qu? thanh toán.

![Lu?ng checkout don hàng](/fcj-workshop-minhthanh/images/5-Workshop/hashop-test-cleanup/image7.png)

![Ki?m tra tr?ng thái don hàng](/fcj-workshop-minhthanh/images/5-Workshop/hashop-test-cleanup/image8.png)
