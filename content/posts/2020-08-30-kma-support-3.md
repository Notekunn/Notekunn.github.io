---
draft: false
template: "post"
title: Hướng dẫn setup KMA Support (Phần 3)
slug: 2020/08/30/huong-dan-setup-kma-support-phan-3/
date: 2020-08-30T13:00:00.000Z
description: Cài đặt và cấu hình kma schedule bot
socialImage: https://i.imgur.com/qAw4VrB.png
category: "Hướng Dẫn"
tags:
  - Javascript
  - Programming
  - Tutorial
  - KMA
---

## LỜI MỞ ĐẦU

[Xem phần trước](/posts/2020/08/30/huong-dan-setup-kma-support-phan-1).

Phần này mình sẽ hướng dẫn deploy service `bot`.

[Source code](https://github.com/kma-academy/kma-schedule-bot)
## Cài đặt

- Tải source code về
```bash
git clone https://github.com/kma-academy/kma-schedule-bot
cd kma-schedule-bot
```
- Install package
```bash
npm install
```

## Cấu hình

Cấu hình file `.env`.

Trong đó:
- `HOST_URL`,`PORT`: Địa chỉ, port trang webhook bot(VD: `http://localhost:3000`,`3000`)
- `TIME_ZONE`, `TIME_FORMAT`: Time zone, time format server(VD: `Asia/Ho_Chi_Minh`, `DD/MM/YYYY`).
- `PAGE_TOKEN`, `PAGE_ID`: token, id page.
- `APP_ID`, `APP_SECRET`: id và secret key
- `VERIFY_TOKEN`, `ADMIN_TOKEN`: chuỗi verify webhook và token admin full quyền.
- `SCHEDULE_SERVER`: Server api đã deploy.
- `MONGODB_STRING`: Mongodb uri (`mongodb+srv://<user>:<pass>@<host>/<api_database>?retryWrites=true&w=majority`).
- `NODE_ENV`: Môi trường làm việc (`development` | `production`).

## Cấu hình app

- Mở developer dashboard facebook
- Chọn app đã tạo thêm sản phẩm messenger:
![Ảnh minh họa](https://i.imgur.com/O3v0edY.png)
- Ở phần mã truy cập chọn thêm trang đã tạo:
![Ảnh minh họa](https://i.imgur.com/FMYHq6V.png)
- Lấy token page:
![Ảnh minh họa](https://i.imgur.com/ACaYRl9.png)
- Cấu hình url webhook `HOST_URL/webhook`(yêu cầu https) và `VERIFY_TOKEN`:
![Ảnh minh họa](https://i.imgur.com/CbOQ6YO.png)
- Đăng ký event:
![Ảnh minh họa](https://i.imgur.com/WhWbJYT.png)
- Chuyển sang chế độ hoạt động
- Lấy token admin [tại đây](https://sharescript.net/2019/02/10/huong-dan-lay-token-facebook-full-quyen-02-2019/)

## Xét duyệt ứng dụng

Đang cập nhật...

## Deploy 

```bash
npm start
```

## Develop

```bash
npm run develop
```

## Hướng dẫn trỏ host khác về localhost

Trong quá trình develop facebook cần 1 callback url, dùng localhost thì không được.
Ta sẽ sử dụng inlets deploy lên heroku như 1 cầu nối 

Xem hướng dẫn chi tiết [tại đây](https://blog.ngxson.com/31-truy-cap-localhost-tu-heroku/)

Chúc các bạn thành công.
