### Tản mạn về Best Practice khi sử dụng git

Một trong Best Practice của `git` là **Branch Early, Branch Often** - Khi code một chức năng mới hay fix một lỗi cụ thể (trừ hotfix) cho sản phẩm, chúng ta tránh tối đa việc code trực tiếp trên nhánh `master` (Một số team/công ty còn đưa ra quy định rất cụ thể về  work flow với git, không cho phép developers push code trực tiếp vào nhánh master khi chưa thông qua code review và tạo pull request) - Tham khảo chi tiết trong bài viết [**Branch Early - Branch Often**](https://thefullsnack.com/branch-early-branch-often-daadaad9468e).

Best Practice tiếp theo là **Do commit early and often**, `git` chỉ chịu trách nhiệm với dữ liệu của chúng ta khi chúng ta commit. Vì vậy, hãy tạo thói quen khi code xong một phần của feature đang làm hay cảm thấy số lượng LOC mình có tác động vào nhiều thì chúng ta nên commit chúng để dễ bề theo dõi và restore sau này. Việc này rất hữu ích vì khi tạo nhiều checkpoint như vậy, bạn kiểm soát được những gì bạn đã và đang làm. Và nếu không may có lỗi xảy ra thì dễ dàng xác định chúng xuất phát từ commit nào (`git bisect`). Tuy vậy, hạn chế của việc commit quá thường xuyên là khiến git history bị đội lên với những commit nhỏ và thừa thãi. Giải pháp cho vấn đề này là khi code hoàn chỉnh một **branch**, bạn có thể **rewriting git history** bằng `git rebase --interactive` để giữ history luôn được gọn gàng trước khi push lên remote repository.

### Rewriting history

#### git commit --amend

`git commit --amend` sử dụng trong trường hợp sau khi vừa commit xong, bạn phát hiện thiếu sót nào đó nên cần bổ sung vào commit trước hoặc là đơn giản là bạn cần sửa lại commit message. **amending** replace toàn bộ commit trước và thay nó bằng commit mới (có thể bổ sung changeset và sửa lại commit message).

Nguyên tắc cần nhớ: Không bao giờ sử dụng `git commit --amend` một khi commit trước đã được push lên remote repository bởi vì đều này sẽ gây rắc rối cho những thành viên khác trong team của bạn.

#### git rebase --interactive

Cú pháp:

```
git rebase -i [base]
```

Ví dụ muốn rebase lại 4 commit gần nhất của nhánh hiện tại thì

```
git rebase -i HEAD~4
```

- pick (giữ nguyên commit)
- commit (giữ nguyên commit và edit lại commit message)
- squash (trộn chung commit này với commit trước đó, giữ lại commit message)
- fixup (tương tự squash nhưng hủy luôn commit message của commit này)

```
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
```

Tham khảo thêm bài viết của [**Thoughtbot**](https://robots.thoughtbot.com/git-interactive-rebase-squash-amend-rewriting-history).

Dương Vì Phát
