# Bai 4: gitignore va amend
## Bối cảnh

Lỡ commit nhầm file chứa thông tin bảo mật `credentials.txt`. Cần gỡ file khỏi sự theo dõi của Git, giữ lại file trên đĩa, cấu hình bỏ qua file này và sửa thông điệp commit gần nhất.

## Các bước thực hiện

1. Tạo repo, tạo `credentials.txt` rồi commit nhầm bằng `git add` và `git commit`.
2. Gỡ file khỏi cache của Git: `git rm --cached credentials.txt`.
3. Tạo `.gitignore` chứa `credentials.txt`, `.idea/`, `Thumbs.db`, `*.log`.
4. `git add .gitignore`, rồi `git commit --amend -m "chore: go credentials.txt khoi theo doi va them .gitignore"`.
5. Kiểm tra bằng `git status` và `git log -n 1`.

## Giải thích git rm --cached

Mặc định `git rm` xóa file khỏi chỉ mục (cache) của Git và xóa luôn file vật lý. Thêm `--cached` thì Git chỉ gỡ file khỏi chỉ mục, tức là ngừng theo dõi, còn file trong thư mục làm việc vẫn nguyên vẹn. Sau đó `.gitignore` giúp Git không theo dõi lại file này.

`.gitignore` chỉ có tác dụng với file chưa được theo dõi, nên file đã commit phải gỡ bằng `git rm --cached` trước.

## Giải thích git commit --amend

`--amend` sửa commit gần nhất: đổi thông điệp và/hoặc gộp thêm thay đổi đang staged vào commit đó. Git tạo commit mới thay thế commit cũ nên mã hash thay đổi.

## Kết quả

commit 2d6cb83edb0cf952e605cde963552678c1574ac1 (HEAD -> main)
Author: thaominh2006 <dothaominh2401@gmail.com>

    chore: go credentials.txt khoi theo doi va them .gitignore

Trạng thái: `nothing to commit, working tree clean`. File `credentials.txt` vẫn còn trên đĩa nhưng không còn được Git theo dõi.

