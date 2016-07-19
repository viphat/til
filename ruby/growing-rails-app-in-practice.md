- Thin Controller But not Fat Model.

- Giảm tầm quan trọng của Controller bằng cách tách nhỏ controllers, chỉ giữ lại các method CRUD (Standard Controller Design):

### Normalizing user interactions
How to come up with a default controller design when your application has many different kinds of
user interactions? The pattern we use is to reduce every user interaction to a Rails CRUD resource. We employ this mapping even if the user interface is not necessarily a typical CRUD interface at
first glance. Even interactions that do not look like plain old CRUD resources can be modeled as such. A screen to cancel a subscription can be thought of as destroying a subscription or creating a new cancellation. A screen to upload multiple images at once can be seen as creating an image batch (even if there is no ImageBatch model). By normalizing every user interaction to a CRUD interaction, we can design a beautiful controller layout and reuse it again and again with little changes.

### We believe that controllers deserve better:

• Controllers should receive the same amount of programming discipline as any other type of class. They should be short, DRY² and easy to read.

• Controllers should provide the minimum amount of glue code to negotiate between request and model.

• Unless there are good reasons against it, controllers should be built against a standard, proven implementation blueprint.

-----

- Cách mấy thằng như inherited_resource ra vì nó chứa đựng quá nhiều magic mà không phải người mới nào cũng nắm, và việc cấu hình đòi hỏi phải đọc documents kỹ, tùy biến, can thiệp cũng khó khăn.

### Hiểu về ActiveRecord

> Never rely on other code to use the custom model methods that you provide. To enforce
an API in ActiveRecord, you must express it in validations and callbacks.

Tận dụng Validations và Callbacks

http://brewhouse.io/blog/2014/04/30/gourmet-service-objects.html
