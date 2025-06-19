
# Project viết README.MD

Nếu bạn muốn viết mà hiển thị dễ thì thì truy cập vào đường link sau: [readme.so](https://readme.so/editor)
  
Khi bạn muốn đưa 1 tệp lên GitHub thông qua Visual Studio Code bạn cần:

#### Tại Github
* Nếu chưa có tài khoản thì tạo tài khoản hoặc đăng nhập
* Tạo ra file `New repository` trên GitHub 
* Sau đó đặt tên nào đó bất kỳ vào ô `Repository name` (Ví dụ đặt tên là `Project`)
* Về phần mô tả (`Description`) có thể để trống hoặc mô tả gì cũng được
* Nhớ chọn `Public` (công khai) 
* Không tích vào ô `Add a README file`
* Cuối cùng ấn vô `Creat repository`

#### Tại Visual Studio Code bước 11111
* Tạo một thư mục chứa dự án cần làm
* Sau đó Tạo ra 1 hoặc nhiều file bất kỳ để đưa lên Github hoặc Vào một thư mục hay dự án nào đó để đưa lên GitHub 
* Ấn vào `New terminal`
 
#### Tại Visual Studio Code bước 22222 (quan trọng sau khi đã mở Terminal)
1. Tạo file README.md với cú pháp: `echo "Dòng_lệnh_bất_kỳ" >> README.md`
* Ví dụ: `echo "# Project" >> README.md`
2. Khởi tạo một Git repository mới trong thư mục hiện tại với cú pháp: `git init`
3. Thêm tất cả file vào staging area (vùng chuẩn bị commit) với cú pháp: `git add .`
4. Tạo một bản lưu (snapshot) với thông điệp "first commit" với cú pháp: `git commit -m "first commit"` (`first commit` chỉ là thông điệp nên là tên gì cũng được)
* Ví dụ: `git commit -m "Đây là file đầu tiên"` 
5. Đổi tên nhánh hiện tại thành main với cú pháp `git branch -M main`
6. Liên kết Git cục bộ (trên máy bạn) với repository trên GitHub qua SSH `git remote add origin git@github.com:Tên_Github_của_mình/Tên_dự_án.git`
* Ví dụ: `git remote add origin git@github.com:TRUONGANKHANG/Project.git`
7. Đẩy (push) code từ máy bạn lên GitHub `git push -u origin main`
* Tổng hợp lại:
```
echo "# Project" >> README.md
git init
git add README.md
git commit -m "Đây là file đầu tiên"
git branch -M main
git remote add origin git@github.com:TRUONGANKHANG/Project.git
git push -u origin main
```
8. Sau đó, mỗi lần cập nhật code mới: 
``` 
git add .
git commit -m "update something"
git push
```
#### Lưu ý: Ở bước 7 khi đẩy code lên có thể gặp trường hợp 
```
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
```

Ta xử lý bằng cách

🔧 ***Bước 1:*** Kiểm tra đã có SSH key chưa
```
ls -al ~/.ssh
```
Nếu thấy file như:

* `id_rsa` và `id_rsa.pub` hoặc

* `id_ed25519` và `id_ed25519.pub`

→ Nghĩa là bạn đã có SSH key. Bỏ qua ***Bước 2***.

🆕 ***Bước 2:*** Nếu chưa có SSH key → tạo mới
```
ssh-keygen -t ed25519 -C "<email của mình nhe>"
```
* Nhấn `Enter` để lưu key ở vị trí mặc định.

* Nếu hỏi passphrase thì bạn có thể bỏ qua bằng cách nhấn `Enter` 2 lần.

📋 ***Bước 3:*** Lấy public key

`cat ~/.ssh/id_ed25519.pub`

→ Copy toàn bộ nội dung kết quả (bắt đầu bằng ssh-ed25519...)

🌐 ***Bước 4:***  Gắn key lên GitHub

1. Vào GitHub: https://github.com/settings/ssh/new

2. Title: đặt tên tuỳ ý (ví dụ: MacAir)

3. Key: dán public key bạn vừa copy

4. Bấm Add SSH key

🔁 ***Bước 5:*** Kiểm tra kết nối SSH với GitHub

`ssh -T git@github.com`

Nếu hiện ra:
`Hi TRUONGANKHANG! You've successfully authenticated...`
→ Là đã OK!

🚀 ***Bước 6:*** Push lại project
`git push -u origin main`

Xong! Rồi mỗi lần cập nhật thì trở lại bước 8 làm nhé!!


CHÚC BẠN THÀNH CÔNG!