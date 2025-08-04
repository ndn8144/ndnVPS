# 🐳 Multi-Environment DevContainer

Môi trường phát triển dùng trong GitHub Codespaces hoặc local dev container với đầy đủ:

- 🐧 Ubuntu 22.04
- 🐍 Python 3 & pip
- 🐳 Docker & Docker Compose
- 📦 Node.js (LTS)
- 🦫 Rust (qua rustup)
- 🐹 Go (v1.22)

## 🚀 Cách dùng với GitHub Codespaces

1. **Fork repo này** vào tài khoản GitHub của bạn
2. Vào repo → Click **Code > Codespaces > Create codespace on main**
3. Chờ build Dockerfile (~2-5 phút)
4. Bạn sẽ có đầy đủ môi trường như đã liệt kê bên trên

## 🧪 Test các môi trường

```bash
node -v
npm -v
go version
rustc --version
docker --version
