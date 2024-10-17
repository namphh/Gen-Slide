# Hướng Dẫn Sử Dụng Markdown

Markdown là một ngôn ngữ đánh dấu nhẹ, cho phép bạn định dạng văn bản một cách dễ dàng.

## Nội Dung

1. **Giới thiệu**
2. **Cú pháp cơ bản**
3. **Ví dụ**

## 1. Giới thiệu

Markdown được sử dụng rộng rãi trong viết tài liệu, tạo README, và nhiều ứng dụng khác nhờ vào sự đơn giản và dễ đọc.

## 2. Cú pháp cơ bản

### Tiêu đề

Bạn có thể tạo các tiêu đề với số lượng dấu `#`:

# Tiêu đề 1
## Tiêu đề 2
### Tiêu đề 3

### Định dạng văn bản

- **In đậm**: `**văn bản**` hoặc `__văn bản__`
- *In nghiêng*: `*văn bản*` hoặc `_văn bản_`
- ~~Gạch ngang~~: `~~văn bản~~`

### Danh sách

#### Danh sách không thứ tự

- Mục 1
- Mục 2
  - Mục con 1
  - Mục con 2

#### Danh sách có thứ tự

1. Mục 1
2. Mục 2
   1. Mục con 1
   2. Mục con 2

### Bảng

| Cột 1   | Cột 2   | Cột 3   |
|---------|---------|---------|
| Dữ liệu 1 | Dữ liệu 2 | Dữ liệu 3 |
| Dữ liệu 4 | Dữ liệu 5 | Dữ liệu 6 |

### Khối mã

Bạn có thể chèn mã nguồn bằng cách sử dụng dấu `` ` `` cho đoạn mã đơn:

`console.log('Hello, World!');`

Hoặc sử dụng ba dấu `` ` `` cho khối mã:

```javascript
function greet() {
    console.log("Hello, World!");
}
greet();
