# Elm Basic

Nội dung được dịch tóm tắt từ sách [基礎からわかる Elm](https://www.amazon.co.jp/%E5%9F%BA%E7%A4%8E%E3%81%8B%E3%82%89%E3%82%8F%E3%81%8B%E3%82%8B-Elm-%E9%B3%A5%E5%B1%85-%E9%99%BD%E4%BB%8B/dp/4863542224) - Dịch từ chương 3 cho đến hết

## Chương 3 - Khởi tạo ứng dụng

### HTML

Để sử dụng các thẻ HTML trong Elm, ta chỉ cần **import** các modules **Html** và **Html.Attributes** của package **elm/html**

Cấu trúc chung sẽ là

> tên thẻ [ danh sách các thuộc tính ] [ danh sách các phần tử con ]

VD:

```elm
a [ href "google.com" ] [ text "Elm" ]
```

Sử dụng câu lệnh sau để compile code

> elm make src/Main.elm

> Trước đó cần khởi tạo elm project bằng câu lệnh: elm init

Tất cả các phần tử HTML đều có kiểu là **Html msg**, tất cả các thuộc tính đều có kiểu **Attribute msg**

Ở đây, gía trị của kiểu **Html msg** đều là **object Virtual DOM**

Trong các thuộc tính của các hàm Html trong Elm, ta có thể sử dụng biểu thức điều kiện hoặc một vài cách viết đặc biệt như sau

```elm
div
    -- viết class thành các hàng
    [ class "large"
    , class "foo bar"
    , class (if good then "good" else "bad")
    -- tương tự với style
    , style "color" "red"
    , style "font-weight" "bold"
    ]
    []
```

### Kiến trúc của Elm

Một ứng dụng Elm có 3 phần: Model, View, Update

- Model: Trạng thái của application
- Update: Xử lí các thay đổi với model
- View: Hiển thị dữ liệu dưới dạng HTML

Khi phát triển ứng dụng, **Model** nên là yếu tố xem xét đến đầu tiên (chủ yếu là xem xem ứng dụng sẽ có những trạng thái nào)

> Câu lệnh elm make với option --debug sẽ giúp chúng ta có thể sử dụng debugger của elm

> Program () - () có nghĩa là flag và port, biểu thị flag nhận vào khi chương trình khởi động. Nếu không có gì nghĩa là không nhận flag nào cả

**Browser.sandbox** sẽ đóng gói và kết nối **mode**, **update** và **view** lại với nhau

### Input form

