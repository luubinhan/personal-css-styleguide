# Quy ước viết CSS của mình

## Nguyên tắc chung

> Luôn format code bằng prettier

1. Không sử dụng `id` selector
2. Gạch ngang `-` hoặc gạch dưới `_` khi đặt tên, không dùng dạng `camelCase`
3. Comment ngay trên
   1. `z-index`
   2. hack để fix bug trình duyệt cụ thế
   3. `!important `
4. Khi khai báo *block* (dùng phương pháp BEM), đặt tên dạng *PascalCase*

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

1. Muốn bỏ border: dùng `0` thay cho `none`
2. `@include` đặt sau các property riêng biệt của

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

12. Không dùng thẻ HTML trong selector

```css
// NOT prefer
div.o-modal {}

// prefer
.o-modal {}
```

13. Không dùng `margin-top`, dùng `padding-top` hoặc `margin-bottom` để thay thế
14. Không dùng cách viết tắt nếu không cần thiết (trừ trường hợp có chủ đích rõ ràng)

```css
// NOT prefer
.css {
    background: #fff;
}

// Prefer
.css {
    background-color: #fff;
}
```

## Namespace

Đặt thêm tiền tố để chia namespace theo mục đích sử dụng

1. `.h-` helper, một mục đích duy nhất, ưu tiên cao nhất
2. `.is-`, `.has-` cho state cụ thể
3. `._` trong trường hợp muốn áp dụng một đoạn hack, như phải dùng `!important`
4. `.c-` cho component
5. `.js-` cho tên class được thêm bằng JS

## Media Query

1. Đưa vào trong selector

```css
$_screen_sm_max: "max-width: 767px";

.selector {
      float: left;

      @media only screen and ($_screen_sm_max) {
        float: none;
      }
}
```



