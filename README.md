# Quy ước viết CSS của cá nhân mình

1. Luôn format code bằng prettier
2. Không sử dụng `id` selector
3. Gạch ngang `-` hoặc gạch dưới `_` khi đặt tên, không dùng dạng `camelCase`
4. Comment ngay trên
   1. `z-index`
   2. hack để fix bug trình duyệt cụ thế
5. Khi khai báo *block* (dùng phương pháp BEM), đặt tên dạng *PascalCase*

Ví dụ

```js
// ListingCard.jsx
function ListingCard() {
  return (
    <article class="ListingCard ListingCard--featured">

      <h1 class="ListingCard__title">Adorable 2BR in the sunny Mission</h1>

      <div class="ListingCard__content">
        <p>Vestibulum id ligula porta felis euismod semper.</p>
      </div>

    </article>
  );
}
```

```css
/* ListingCard.css */
.ListingCard { }
.ListingCard--featured { }
.ListingCard__title { }
.ListingCard__content { }
```

6. Nếu tên `class` được thêm bằng JS, thêm tiền tố **js-**
7. Muốn bỏ border: dùng `0` thay cho `none`
8. `@include` đặt sau các property riêng biệt của

```scss
.btn-green {
    background: green;
    font-weight: bold;
    @include transition(background 0.5s ease);
}
```

9. Khai báo tên biến dạng `$my-variable`, nếu biến chỉ được dùng đúng trên file được khai báo `$_my-variable`
10. Không dùng `@extend`, nhiều trường hợp bị lỗi không kiểm soát được
11. Không lồng quá 3 cấp

```css
.page-container {
  .content {
    .profile {
      // STOP!
    }
  }
}
```



