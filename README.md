# Hướng dẫn Build Paper: Generating Story Illustrations with OmniGen

Dự án này sử dụng LaTeX với format IEEE Conference (`IEEEtran`). Dưới đây là hướng dẫn chi tiết để cài đặt môi trường và build file PDF.

## 1. Cài đặt Môi trường (Prerequisites)

Để biên dịch được file `.tex`, máy tính cần cài bộ biên dịch LaTeX.

### Trên Ubuntu/Linux (Khuyên dùng)
Chạy lệnh sau trong Terminal để cài đặt đầy đủ các gói cần thiết:
```bash
sudo apt update
sudo apt install -y texlive-latex-extra texlive-science texlive-fonts-recommended latexmk
```

### Trên Windows
Tải và cài đặt **MiKTeX** hoặc **TeX Live**.

### Trên macOS
Cài đặt **MacTeX** thông qua Homebrew: `brew install --cask mactex`.

## 2. Cài đặt VS Code Extension

Để soạn thảo và build thuận tiện nhất trong VS Code, bạn hãy cài extension sau:

*   **Tên**: LaTeX Workshop
*   **ID**: `james-yu.latex-workshop`
*   **Link**: [LaTeX Workshop trên Marketplace](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)

Extension này hỗ trợ tự động build khi lưu file (Auto-build on save), xem PDF ngay trong VS Code, và nhắc lệnh thông minh.

## 3. Cách Build (Biên dịch ra PDF)

### Cách 1: Dùng VS Code Extension (Dễ nhất)
1.  Mở file `paper.tex`.
2.  Nhấn tổ hợp phím `Ctrl + Alt + B` (hoặc mở Command Palette `Ctrl+Shift+P` -> gõ `LaTeX Workshop: Build with recipe`).
3.  Sau khi build xong, nhấn `Ctrl + Alt + V` để xem file PDF ở tab bên cạnh.
4.  Mỗi lần bạn nhấn `Ctrl + S` (Lưu), extension sẽ tự động build lại.

### Cách 2: Dùng Terminal (Command Line)
Nếu máy bạn không có VS Code hoặc muốn build thủ công, chạy lần lượt các lệnh sau tại thư mục gốc của dự án:
```bash
# 1. Biên dịch lần đầu để tạo file aux
pdflatex paper.tex

# 2. Xử lý tài liệu tham khảo (Bibliography)
bibtex paper

# 3. Biên dịch lại 2 lần để cập nhật tham chiếu và mục lục
pdflatex paper.tex
pdflatex paper.tex
```
Kết quả sẽ là file `paper.pdf`.

## 4. Cấu trúc Thư mục

*   `paper.tex`: File mã nguồn chính chứa nội dung bài báo.
*   `references.bib`: File chứa danh sách tài liệu tham khảo (BibTeX format).
*   `IEEEtran.cls`: File cấu hình định dạng của IEEE Conference (đừng xóa file này).
*   `IEEEtran.bst`: File cấu hình định dạng trích dẫn.
*   `.gitignore`: Cấu hình để Git bỏ qua các file rác khi build (như .aux, .log).

## 5. Lưu ý về Git

File `.gitignore` đã được cấu hình sẵn để bỏ qua các file tạm sinh ra trong quá trình build như `*.aux`, `*.log`, `*.out`.
Khi bạn push code lên GitHub, chỉ những file mã nguồn quan trọng mới được đẩy lên, giữ cho repo sạch sẽ.
