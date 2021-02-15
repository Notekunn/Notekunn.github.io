---
draft: false
template: "post"
title: Hướng dẫn setup KMA Support (Phần 1)
slug: 2020/08/30/huong-dan-setup-kma-support-phan-1/
date: 2020-08-30T12:00:00.000Z
description: Chuẩn bị môi trường cần thiết
socialImage: https://i.imgur.com/qAw4VrB.png
category: "Hướng Dẫn"
tags:
  - Javascript
  - Programming
  - Tutorial
  - KMA
---

# KMA Support là gì ?

KMA Support là hệ thống giúp sinh viên tra cứu lịch học qua các nền tảng facebook, discord,...

![Hình minh họa](https://i.imgur.com/qAw4VrB.png)

## Nguyên lý hoạt động

- Hệ thống gồm 2 service hoạt động độc lập
- `api`: Tương tác với trang web qldt, lưu thông tin tài khoản, thời khóa biểu.
- `bot`: Tương tác với người dùng trên các platform facebook, discord, ...

Hình minh họa:

![Hình minh họa](https://i.imgur.com/qAw4VrB.png)

Mỗi service sẽ hoạt động ở các port riêng biệt `api_port` và `service_port`.
Tương ứng với các database riêng.

## Setup môi trường

- Chuẩn bị 1-2 vps tùy theo điều kiện.
- Cài đặt Node.js [v12+](https://nodejs.org/dist/v12.18.3/node-v12.18.3-x64.msi).
- Cài đặt git, nginx.
- Cài đặt mongodb server hoặc sử dụng mongo atlas.

## Cấu hình nginx

- `api` listen ở port 8000.
- `bot` listen ở port 3000.

Đang cập nhật ...

## Cài đặt facebook

- Tạo 1 page facebook bất kỳ.
- Tạo 1 ứng dụng facebook [tại đây](https://developers.facebook.com/apps/).
- Thêm các thông tin cơ bản của ứng dụng (`https://developers.facebook.com/apps/<ID_APP>/settings/basic/`).

Đang cập nhật...


[Phần tiếp theo](/2020/08/30/huong-dan-setup-kma-support-phan-2) mình sẽ hướng dẫn setup service `api`.
