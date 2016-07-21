Có một sự thật không thể chối cãi là Large application are large. Large application không tránh khỏi việc sẽ phức tạp hơn những app nhỏ hơn và những gì chúng ta có thể làm là tổ chức codebase tốt hơn để "scales logarithmically" - Twice as many models should not mean twice as many problems. Đây là những kiến thức mình đọc trong quyển **Growing Rails Applications in Practice**: Bài viết này chỉ tập trung vào 2 phần **Beautiful Controller** và **Thin model** để áp dụng ngay cho dự án mới của mình.

![http://i.imgur.com/Pmtki8w.png](http://i.imgur.com/Pmtki8w.png)

### Beautiful Controller

Trong mô hình MVC thì controller chỉ nên đảm nhận các công việc chính sau đây (đừng nhiều hơn):

- Security (Authentication, Authorization).
- Parsing and white-listing parameters.
- Loading and instantiating the model.
- Deciding which view to render.

Một **Beautiful Controller** sẽ bao gồm các yếu tố này:

- They should be short, DRY and easy to read.
- Controller should provide the minimum amount of glue code to negotiate between request and model.
- Controller should be build against a standard design (RESTful).

> Even interactions that do not look like plain old CRUD resources can be modeled as such. A screen to cancel a subscription can be thought of as destroying a subscription or creating a new cancellation.

Không dùng controller abstractions như inherited_resources hoặc Resource Controller bởi vì tiện ích nó mang lại không đáng để đánh đổi vì nó chứa đựng quá nhiều magic và khi gặp vấn đề muốn tùy biến và can thiệp thì phải chịu khó đọc document và cấu hình chúng đều rất mệt.

Ví dụ:

**Một controller trước khi refactoring**:

```ruby
class AccountsController < ApplicationController

  def merge_form
   @source_missing = false
   @target_missing = false
  en
  def do_merge
    source_id = params[:source_id]
    target_id = params[:target_id]

    if source_id.blank?
      @source_missing = true
    end

    if target_id.blank?
      @target_missing = true
    end

    if source_id.present? && target_id.present?
      source = Account.find(source_id)
      target = Account.find(target_id)
      Account.transaction do
        target.update_attributes!(:credits => target.credits + source.credits)
        source.subscriptions.each do |subscription|
          subscription.update_attributes!(:account => target)
        end

        Mailer.account_merge_notification(source, target).deliver
        source.destroy
      end
      redirect_to target
    else
      render 'merge_form'
    end
  end
end
```

**Template View tương ứng để Merge 2 account với controller trên**:

``` ruby

<h1>Merge two accounts</h1>
<%= form_tag do_merge_accounts_path do %>
  <%= label_tag :source_id, 'Source account' %>
  <% if @source_missing %>
    <div class="error">
     You must select a source account!
    </div>
  <% end %>

  <% selectable_accounts = Account.all.collect { |a| [a.name, a.id] } %>
  <%= select_tag :source_id, options_for_select(selectable_accounts) %>
  <%= label_tag :target_id, 'Target account' %>

  <% if @target_missing %>
    <div class="error">
      You must select a target account!
    </div>
  <% end %>

  <%= select_tag :target_id, options_for_select(selectable_accounts) %>
  <%= submit_tag %>

<% end %>

```

### Thin Model

Sử dụng gem [**Active Type**](https://github.com/makandra/active_type)
