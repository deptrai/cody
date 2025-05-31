# Tài liệu chi tiết về dự án Cody

## 1. Tổng quan
Cody là trợ lý lập trình AI mã nguồn mở được phát triển bởi Sourcegraph, giúp các nhà phát triển hiểu, viết và sửa code nhanh hơn bằng cách sử dụng các mô hình ngôn ngữ lớn (LLM) tiên tiến.

### 1.1 Thông tin cơ bản
- **Giấy phép**: Apache 2.0
- **Nhà phát triển**: Sourcegraph
- **Ngôn ngữ chính**: TypeScript/JavaScript
- **Trạng thái**: Đang phát triển tích cực

## 2. Kiến trúc hệ thống

### 2.1 Tổng quan kiến trúc
- **Mô hình**: Client-Server với agent trung tâm
- **Giao thức giao tiếp**: JSON-RPC 2.0
- **Hỗ trợ đa nền tảng**:
  - VS Code (extension)
  - JetBrains (plugin)
  - Giao diện web

### 2.2 Các thành phần chính

#### 2.2.1 Agent (`/agent`)
- **Vai trò**: Xử lý logic chính, kết nối với các mô hình ngôn ngữ lớn (LLM)
- **Các module chính**:
  - `src/agent.ts`: Lớp Agent chính
  - `src/global-state/`: Quản lý trạng thái toàn cục
  - `src/auth/`: Xử lý xác thực và ủy quyền

#### 2.2.2 Thư viện dùng chung (`/lib`)
- **Mục đích**: Chứa các thành phần dùng chung
- **Các module**:
  - `shared/`: Code dùng chung
  - `prompt-editor/`: Công cụ chỉnh sửa prompt
  - `noxide/`: Module xử lý Rust (nếu có)

#### 2.2.3 Giao diện người dùng
- **VS Code Extension** (`/vscode`): Tích hợp với Visual Studio Code
- **JetBrains Plugin** (`/jetbrains`): Tích hợp với các IDE của JetBrains
- **Giao diện Web** (`/web`): Giao diện web tương tác

## 3. Công nghệ sử dụng

### 3.1 Ngôn ngữ chính
- **TypeScript/JavaScript**
- **Node.js** cho phía server

### 3.2 Công cụ phát triển
- **Quản lý gói**: pnpm (workspace)
- **Testing**: Vitest
- **Linting**: Biome
- **Định dạng code**: Prettier

### 3.3 Thư viện chính
- **vscode-jsonrpc**: Xử lý giao tiếp RPC
- **vscode-languageclient**: Hỗ trợ ngôn ngữ LSP
- **langchain**: Tích hợp với các mô hình ngôn ngữ

## 4. Tính năng chính

### 4.1 Hỗ trợ chat
- Tương tác tự nhiên với mã nguồn
- Hỏi đáp về codebase
- Giải thích code

### 4.2 Tự động hoàn thành code
- Gợi ý code thông minh
- Hỗ trợ nhiều ngôn ngữ lập trình
- Tích hợp với trình soạn thảo

### 4.3 Sửa đổi code nội tuyến
- Đề xuất sửa lỗi
- Tái cấu trúc code
- Tạo unit test tự động

### 4.4 Hỗ trợ nhiều mô hình ngôn ngữ
- Claude Sonnet 4
- GPT-4
- Mixtral
- Gemini 1.5

## 5. Bảo mật và quyền riêng tư

### 5.1 Bảo mật dữ liệu
- Mã hóa dữ liệu nhạy cảm
- Lưu trữ an toàn thông tin xác thực
- Kiểm soát quyền truy cập chi tiết

### 5.2 Xác thực
- Hỗ trợ xác thực qua Sourcegraph.com
- Quản lý phiên đăng nhập
- Ủy quyền OAuth2

## 6. Phát triển

### 6.1 Cài đặt môi trường
```bash
# Cài đặt dependencies
pnpm install

# Build dự án
pnpm build

# Chạy extension VS Code
cd vscode
pnpm run dev
```

### 6.2 Kiến trúc code
- Sử dụng mẫu thiết kế hướng đối tượng
- Module hóa rõ ràng
- Tách biệt giữa logic nghiệp vụ và giao diện

### 6.3 Kiểm thử
- Unit tests
- Integration tests
- End-to-end tests

## 7. Đóng góp

### 7.1 Quy trình đóng góp
1. Fork repository
2. Tạo nhánh mới cho tính năng/sửa lỗi
3. Tạo pull request
4. Kiểm tra CI/CD
5. Đánh giá code
6. Merge vào nhánh chính

### 7.2 Nguyên tắc phát triển
- Tuân thủ quy ước đặt tên
- Viết test đầy đủ
- Tài liệu rõ ràng
- Giữ lịch sử commit sạch sẽ

## 8. Tài liệu tham khảo

### 8.1 Tài liệu chính thức
- `README.md`: Hướng dẫn cài đặt và sử dụng cơ bản
- `ARCHITECTURE.md`: Tài liệu kiến trúc chi tiết
- `CONTRIBUTING.md`: Hướng dẫn đóng góp

### 8.2 Liên hệ
- GitHub Issues: Báo cáo lỗi và yêu cầu tính năng
- GitHub Discussions: Thảo luận và hỏi đáp
- Discord: Cộng đồng người dùng và nhà phát triển

---
*Tài liệu được cập nhật lần cuối: 29/05/2025*
