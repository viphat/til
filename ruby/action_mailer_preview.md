
Xuất phát từ nhu cầu của mình là phải ngồi mần một Email Template cho tác vụ gửi Newsletter của dự án đang làm nên phải thay đổi và kiểm tra thường xuyên. Vì vậy, không thể cứ mỗi lần thay đổi một chút là lại phải gửi Email đi, vừa mất thời gian (Gửi Mail qua **SMTP Server** xong lại phải mở hộp mail để check, và cũng không chắc là mail đến nhanh như mong đợi không) và tốn kém chi phí (nếu bạn sử dụng các dịch vụ Email Delivery như **Sendgrid** và **Mailchimp**...). Thử Google trên mạng thì có 2 giải pháp là dùng **Mail Catcher** để bắt hết tất cả Mail gửi đi trong môi trường Development và nhét về lại một chỗ - http://mailcatcher.me/. Cách thứ hai, đơn giản hơn nữa là Rails có hỗ trợ **Action Mailer Previews** giúp bạn nhanh chóng và dễ dàng để xem trước Email của bạn bằng trình duyệt Web.

Ở đây, tôi giả định bạn đã có một class UserMailer với method new_user():

<small>**app/mailers/user_mailer.rb**</small>
```
class UserMailer < ActionMailer::Base
  default from: "from@example.com"

  def new_user(user)
    @user = user
    mail to: user.email, subject: "Hello!"
  end
end
```

và một Email Template tương ứng với Method đó tại:

<small>**app/views/user\_mailer/new\_user.html.erb**</small>
```
<h1>Hello <%= @user.first_name %>!</h1>

<p>
  Welcome to my website!
</p>
```

Để Preview Mail này trên trình duyệt Web, ta tiến hành các bước sau:

Tạo File **test/mailers/previews/user\_mailer\_preview.rb** với nội dung:

```
class UserMailerPreview < ActionMailer::Preview

  def new_user
    user = User.first
    UserMailer.new_user(user)
  end

end
```
Khởi động lại Server bằng `rails server` và truy cập **http://localhost:3000/rails/mailers/user\_mailer/new\_user** để xem kết quả.

Nếu bạn không muốn Class **UserMailerPreview** phải đặt trong thư mục **test/mailers/previews/** (Trường hợp Dự án dùng rspec nên không có thư mục test chẳng hạn) thì bạn có thể đặt lại Path trong **config/environments/development.rb**
```
config.action_mailer.preview_path = "#{Rails.root}/app/mailers/previews"
```

##### Bonus Tip

**\#1** - Để sử dụng **Views Helpers** trong Email Template, bạn thêm dòng sau vào trong class UserMailer của bạn:


```
add_template_helper(TimelineHelper)
```
- TimelineHelper là tên Helper cần đưa vào

**\#2** - Sử dụng chung một Layout cho nhiều loại Mail.

Thêm dòng sau vào trong class UserMailer:

```
layout 'mail_layout'
```
(với mail_layout là tên File dùng làm Layout đặt trong thư mục **app/views/layouts/**)

Nếu có sử dụng Devise thì thêm dòng sau vào **config/application.rb** để sử dụng chung Layout cho các Mail gửi từ Devise:

```
config.to_prepare do
  Devise::Mailer.layout "mail_layout"
end
```

><span style="color: #f92672;"> Bài viết trong loạt bài Today I Learned, ghi nhanh và tổng hợp các kiến thức, tips mới mà tôi học được trong ngày.</span>
