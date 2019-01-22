### Framgia git standard
Tham khảo [Framgia Git Flow](https://github.com/framgia/coding-standards/blob/master/vn/git/flow.md), [standard-version](https://github.com/conventional-changelog/standard-version), [conventional-changelog-cli](https://github.com/conventional-changelog/conventional-changelog/tree/master/packages/conventional-changelog-cli)

## Mục đích của tài liệu
- Quy chuẩn đặt tên đồng nhất của các dự án.
- Tạo file CHANGELOG.md từ các nguyên tắc đặt tên.

## Nguyên tắc đặt tên branch

**Tùy vào dự án sẽ có nhưng quy tắc đặt branch khác nhau**

*Đối với dự án quản lý issue trên github/ waffle qua label*

- Đối với tính năng mới: `feature/#issue_id-ten-nhanh (ví dụ: `feature/#2-create-readme-file`)
- Đối với bug: `fix/#issue_id-ten-nhanh` (ví dụ: `fix/#3-login-with-facebook`)

## Nguyên tắc đặt tên commit
Nguyên tắc đặt tên commit sẽ đóng vai trò quyết định nội dung trong file CHANGLOG.md sẽ được tạo ra

**Mỗi loại issue tương ứng sẽ đặt tên commit theo format tương ứng**

*Tính năng mới:*

- `feat: nội dung commit` (ví dụ: `feat: user management`)
- `feat(scope): nội dung commit` (ví dụ: `feat(lang): added vietnamese language`)

*Bug:*
- `fix: nội dung commit` (ví dụ: fix: spelling correction)
- `fix(scope): nội dung commit` (ví dụ: `fix(login): can not login with facebook`)

*Có tính năng hoặc sự thay đổi lớn nào đó:*

  ```
  feat(scope) nội dung commit
  BREAKING CHANGE: thông tin thay đổi
  ```
  Ví dụ:
  ```
  feat: renew ux/ui
  BREAKING CHANGE: New user interface
  ```

*Trường hợp khác*

- `docs: nội dung commit` (ví dụ: `docs: hot fix readme`)

## Releases
### Release thủ công
Các dự án cần release đặt tên version theo format: `vx.y.z` bắt đầu từ `v1.0.0`

**Quy tắc tăng version**
1. Trường hợp chỉ có sửa lỗi => z tăng thêm 1

*Ví dụ:*

Nội dung của các commit trong version mới:
```
fix(login): can not login with facebook
fix: spelling correction
```
version được tăng từ `v1.0.0` lên `v1.0.1`

2. Trường hợp sửa lỗi và có những tính năng nhỏ => y tăng thêm 1, z trở về 0

*Ví dụ*

Nội dung các commit trong version mới:
```
fix(login): can not login with facebook
feat(login): login with twitter
fix: spelling correction
```
version được tăng từ `v1.0.1` lên `v1.1.0`

3. Trường hợp có một thay đổi lớn (BREAKING CHANGE) => x tăng thêm 1, y và z trở về 0

*Ví dụ*
```
fix: spelling correction
feat: change icon on head title
feat: renew ux/ui
BREAKING CHANGE: New user interface
```
version được tăng từ `v1.1.0` lên `v2.0.0`

**Hướng dẫn sử dụng tools tạo changelog**

Cài đặt tools qua câu lệnh:
```
npm install -g conventional-changelog-cli
```

Tại thư mục dự án muốn tạo changelog chạy câu lệnh:
```
conventional-changelog -p angular -i CHANGELOG.md -s -r 0
```
sau đó file CHANGELOG.md được tạo ra theo các commit và version hiện tại của dự án.

### Sử dụng công cụ hỗ trợ release

*Cài đặt công cụ qua câu lệnh*
```
npm i -g standard-version
```
*Chạy lệnh sau để release version mới*
```
standard-version
```

*Chú ý:* Công cụ sẽ tự động đặt tên version dựa vào nội dung commit của version sắp release.
Nguyên tắc tăng version giống với [release thủ công](#release-thủ-công)

*Một số options:*
- `release-as`: chỉ định rõ tên của version tiếp theo (ví dụ: `standard-version --release-as 1.1.0` => version được tạo có tên `v1.1.0`)
- `prerelease`: tạo một bản prerelease (ví dụ: `standard-version --prerelease` => bạn sẽ tạo ra version dạng `1.0.1-0`
- `--no-verify`: bỏ qua git hooks


Chi tiết: `standard-version --help`