---
draft: false
template: "post"
title: Hướng dẫn setup KMA Support (Phần 2)
slug: 2020/08/30/huong-dan-setup-kma-support-phan-2/
date: 2020-08-30T12:30:00.000Z
description: Cài đặt và cấu hình kma schedule api
socialImage: https://i.imgur.com/qAw4VrB.png
category: "Hướng Dẫn"
tags:
  - Javascript
  - Programming
  - Tutorial
  - KMA
---

## LỜI MỞ ĐẦU

[Xem phần trước](/2020/08/30/huong-dan-setup-kma-support-phan-1).

Phần này mình sẽ hướng dẫn deploy service `api`.

[Source code](https://github.com/kma-academy/kma-schedule-api)
## Cài đặt

- Tải source code về
```bash
git clone https://github.com/kma-academy/kma-schedule-api
cd kma-schedule-api
```
- Install package
```bash
npm install
```

## Cấu hình

Tạo 1 file `.env` có cấu trúc tương tự file `.env.example`
Hoặc chạy lệnh sau(linux):

```bash
cp .env.example .env
```

Trong đó:
- `PORT`: port hoạt động của api.
- `HOST_API`: Địa chỉ trang qldt(VD: `http://qldt.actvn.edu.vn`).
- `TIME_ZONE`: Time zone server(VD: `Asia/Ho_Chi_Minh`).
- `MONGODB_STRING`: Mongodb uri (`mongodb+srv://<user>:<pass>@<host>/<api_database>?retryWrites=true&w=majority`).
- `NODE_ENV`: Môi trường làm việc (`development` | `production`).

## Deploy 

Build api document:
```bash
npm run build:swagger
```
Run server:
```bash
npm start
```

## Develop

Develop api document:
```bash
npm run develop:swagger
```
Develop server:
```bash
npm run develop
```
[Phần tiếp theo](/2020/08/30/huong-dan-setup-kma-support-phan-3) mình sẽ hướng dẫn deploy service `bot`
