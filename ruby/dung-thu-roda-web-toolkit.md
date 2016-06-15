---
layout: default
title: ""
date: 2016-06-16 00:00:00
permalink: /:slug
tags: [ruby, roda]
---

Vậy là cũng gần 2 năm kể từ khi mình trở lại với con đường Coder - [**Tôi đã học Ruby như thế nào**](http://notes.viphat.work/toi-da-bat-dau-hoc-ruby-nhu-the-nao). Và cũng ngần ấy thời gian, mình đã gắn bó với Ruby, ăn ngủ cùng Rails. Tuy nhiên, Ruby không chỉ có Rails, việc sử dụng Rails quá nhiều dẫn đến mình bị lệ thuộc vào Rails và các magic, monkey patching của Rails. Vì vậy, mình quyết định sẽ tìm hiểu thử các framework khác của Ruby và áp dụng cho các dự án [side project](http://notes.viphat.work/moi-lap-trinh-vien-deu-can-co-it-nhat-mot-side-project) sắp tới của mình.

Ban đầu, mình định quay lại với Sinatra, dù gì thì trước kia, mình đã từng dùng Sinatra và ít ra đã đọc và follow hết quyển [**Jump Start Sinatra**](https://www.sitepoint.com/store/jump-start-sinatra/) rồi. Sau đó, một số cái tên đã được thêm vào short list của mình như **Hanami** (**Lotus**), **CUBA** và **Roda**. Và mình đã chọn Roda bởi vì...

### Giới thiệu

- Roda đơn giản và siêu gọn nhẹ, nó không phải một framework đầy đủ và nặng nề như Rails (được phát triển bởi một người độc đoán như DHH). Nếu bạn cần một framework tốt nhưng không phải **Rails** thì **Hanami** khá là hứa hẹn. Bản thân tác giả Roda chỉ giới thiệu Roda là một **Routing Tree Web Toolkit**.
- Đáng tin cậy.
- Roda có khả năng mở rộng bằng cách sử dụng plugins. Tuy cộng đồng của Roda không đông đảo, nhưng vẫn có đủ các plugins cần thiết, kết hợp với hệ thống gems dành cho Ruby cũng đủ đáp ứng phần lớn các yêu cầu của bạn.
- Hiệu suất tốt hơn hẳn Rails (dĩ nhiên rồi), và nhanh hơn 2.5X so với **Sinatra** (Một framework cũng siêu nhẹ khác).

Tham khảo bài viết [Why Roda?](http://viphat.me/1UcgEvi)

### Liên kết hữu ích

#### Một số liên kết đáng tham khảo khác:

- [Roda Conventions](http://viphat.me/1YrR45i) - Vào học cách tổ chức folder dự án như thế nào? (Áp dụng cho ứng dụng nhỏ/lớn).
- [**Roda Documents**](http://roda.jeremyevans.net/documentation.html) - Tập hợp các tài liệu chính thức của Roda và các plugins có sẵn của Roda.
- [Roda Skeleton with Sequel](http://viphat.me/1PtTY2d) - application skeleton cho ứng dụng viết bằng Roda với [**Sequel**](http://viphat.me/1VZmNu3) làm ORM.
- [Roda-app](http://viphat.me/1UUJtX4) - Cũng là một application skeleton nhưng chỉ thuần Roda.
- [Develop API with Roda](http://viphat.me/1Op9wJB)
- [Setup and deploy Roda app from scratch](http://viphat.me/1XXbl3W)
- [Introduction to Roda](http://twin.github.io/introduction-to-roda/) - Bạn có thể xem cách tác giả sử dụng Roda cho API, Web Sockets, Caching... như thế nào.
- [Simple Roda Blog Tutorial](http://mrcook.uk/simple-roda-blog-tutorial) - Tutorial hướng dẫn tạo một blog đơn giản bằng Roda, thích hợp cho các bạn chuộng học theo kiểu thực hành theo guide hướng dẫn.

#### Ứng dụng OpenSource viết bằng roda:

- [**Kontana Server**](https://github.com/kontena/kontena/tree/master/server), bài viết liên quan - [Roda + Mutations + Jbuilder = Perfect fit for JSON API](http://viphat.me/24QRguM) , mình học được nhiều thứ cũng như chôm chỉa được cách cấu hình, tổ chức thư mục dự án từ Kontana.

Trong quá trình phát triển ứng dụng, một phần không thể thiếu (nếu ứng dụng có tương tác với database) là ORM và Authentication. Với Roda, ORM tốt nhất là **Sequel** và Authentication thích hợp nhất là [**Rodauth**](http://viphat.me/1Opa16p), bởi cả 2 gem này đều do tác giả của **Roda** là Jeremy Evans phát triển và duy trì. Trong đó, Sequel được đánh giá là không thua kém so với **ActiveRecord** quen thuộc của Rails (Nói về Performance thì Sequel ăn đứt ActiveRecord nhé - [xem chi tiết](http://viphat.me/1XXcgl7)).

#### Một số liên kết hữu ích khi tìm hiểu vể Sequel:

- [**Sequel cheat sheet**](http://viphat.me/23aimxB) - Tra cứu nhanh một số cách sử dụng Sequel.
- [**Sequel for ActiveRecord users**](http://viphat.me/24QRnGw)
- [Ode to Sequel](http://viphat.me/1twkZhm)
- [ActiveRecord is reinventing Sequel](http://viphat.me/1YrVqJL)
- [Why you should stop using ActiveRecord and start using Sequel](http://viphat.me/1YrTgtx)


> Khi còn dev app bằng Sinatra thì mình dùng DataMapper cho ORM.

#### Các plugins mình đã dùng cho side project đầu tiên - [Worklog Assistant](http://viphat.me/1Q4KboP) - được viết bằng roda:
- render
- environments
- multi_route
- mailer
- json
- all_verbs
- default_headers
- head
- error_handler
- Sequel Extensions Seed

Đọc thêm bài [**The Plugin System of Sequel and Roda**](http://viphat.me/1rq3Sf1) để hiểu mô hình này so với các gem của Rails như thế nào.

### Deploy
Có thể áp dụng các tutorial deploy dành cho sinatra, bởi vì roda cũng giống sinatra, cũng thuộc dạng Rack-based.

- [Sinatra + Puma + Nginx](http://viphat.me/1Uzmu47)
- [Sinatra + Puma + Nginx](http://viphat.me/1YrsGR8)
