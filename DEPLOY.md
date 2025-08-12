# Hướng dẫn triển khai lên GitHub Pages

## Bước 1: Chuẩn bị repository

1. Tạo repository mới trên GitHub
2. Clone repository về máy local hoặc push code hiện tại lên

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git
git push -u origin main
```

## Bước 2: Cấu hình GitHub Pages

1. Vào **Settings** của repository
2. Chọn **Pages** trong menu bên trái
3. Trong **Source**, chọn **GitHub Actions**

## Bước 3: Cập nhật baseURL

Sửa file `config.toml`:
```toml
baseURL = "https://YOUR_USERNAME.github.io/YOUR_REPOSITORY_NAME/"
```

## Bước 4: Push và deploy

```bash
git add .
git commit -m "Add GitHub Pages deployment"
git push origin main
```

## Kết quả

- GitHub Actions sẽ tự động build và deploy site
- Site sẽ có sẵn tại: `https://YOUR_USERNAME.github.io/YOUR_REPOSITORY_NAME/`
- Mỗi lần push code mới, site sẽ tự động cập nhật

## Lưu ý

- Thay `YOUR_USERNAME` và `YOUR_REPOSITORY_NAME` bằng thông tin thực tế
- Đảm bảo repository là public hoặc có GitHub Pro để sử dụng GitHub Pages với private repo
- Quá trình deploy có thể mất 5-10 phút