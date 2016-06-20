### Intro

- Có nhiều library phụ thuộc vào Google Play Services (đặc biệt là hàng của Google, Google Cloud Messaging) > Những máy không có Google play services sẽ không work, phải tìm 3rd party.

- Deep Links (Dynamic Links)

### Life Cycle

Gối đầu giường cho Android Developers:

- [Android Life Cycle](https://github.com/xxv/android-lifecycle/blob/master/complete_android_fragment_lifecycle.png)

What is Activity Life Cycle & Fragment Life Cycle

### **Launch Mode**

#### Standard Mode

Pre Lollipop vs Lollipop

#### Single Top Mode

Nếu Activity được gọi đang ở Top Task thì không init nữa mà gọi onNewIntent() ~thay vì onCreate~

ABB > AB
ABCB > ABCB

#### Single Task Mode

##### Affinity trong Single Task Mode

#### Single Instance Mode

##### References

- [Tasks and Back Stack](https://developer.android.com/guide/components/tasks-and-back-stack.html)

### Storage & Database

#### Realm.io

Một ORM phổ biến trong Lập trình Mobile (sử dụng được Android/iOS/WindowsPhone)

http://stackoverflow.com/questions/2647542/android-threading-and-database-locking

Thread-safe

Database Read-locking, Write-locking

Waiting or throw exception?

Table-locking, Row-locking, Column-locking

Sqlite is table-locking

How about Postgres? (http://blog.nordeus.com/dev-ops/postgresql-locking-revealed.htm)

#### Codelab - Learning Realm Basic

- Android Shared Preferences (Lưu dữ liệu dạng key-value đơn giản) - http://www.tutorialspoint.com/android/android_shared_preferences.htm

- apply() vs commit() - https://developer.android.com/reference/android/content/SharedPreferences.Editor.html#apply()

-----

#### Firebase

**Anonymous authentication** - Boosts UX khá tốt vì User không cần đăng ký nhưng vẫn có thể thao tác, sử dụng các chức năng của Website, đến khi muốn thì User sẽ đăng ký, và thông tin User sẽ được merge với account Anonymous.

- Robotest
- Integration Test

- Crash Report

- **Firebase Android Codelabs** - https://codelabs.developers.google.com/codelabs/firebase-android/#0

Test trên Device thật vì trên Emulator không có Google Play Services.

> Nếu gặp lỗi Ubuntu không nhận diện được Device thật trong Android Studio, ta có thể thử khởi động lại Server adb

```
sudo apt-get install android-tools-adb
sudo adb kill-server
sudo adb start-server

```

### Performance

### Caching

LRU Cache

### Memory Leak

Eclipse Memory Analyzer

LeakCanary

Để phát hiện Memory Leak thì ngoài các công cụ hỗ trợ, cần nhất là kinh nghiệm và cảm giác, đặc biệt là các kiến thức về kỹ thuật lập trình, những thứ đằng sau hệ thống để truy ra nguồn gốc và khắc phục Memory Leak.

GPU

CPU

- [**Android Performance Patterns**](https://www.youtube.com/watch?v=qk5F6Bxqhr4&list=PLWz5rJ2EKKc9CBxr3BVjPTPoDPLdPIFCE)

### Android Architecture

Pattern: **MVP**, **MVVM**

Clean Architecture

- [Android MVVM](https://labs.ribot.co.uk/approaching-android-with-mvvm-8ceec02d5442#.9w7qjas24)

- [Android Project Structure Alternative Way](https://medium.com/google-developer-experts/android-project-structure-alternative-way-29ce766682f0#.w00pr0toa)


### Final Projects

Apply FriendlyChat MVP or MVVM > Build APK File.

### References

### Mentors

Hùng - http://henrytao.me/
Huỳnh Quang Thảo - http://github.com/hqc - https://medium.com/@huynhquangthao -  huynhquangthao@gmail.com
