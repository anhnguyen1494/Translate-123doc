### Nảy khi tải trang

Hiệu ứng nảy lên khi tải trang

#### HTML

```html
<div class="bouncing-loader">
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.bouncing-loader {
  display: flex;
  justify-content: center;
}
.bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__bouncing-loader">
  	<div></div>
    <div></div>
    <div></div>
  </div>
</div>

<style>
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.snippet-demo__bouncing-loader {
  display: flex;
  justify-content: center;
}
.snippet-demo__bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.snippet-demo__bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.snippet-demo__bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
</style>

#### Giải thích

Lưu ý: `1rem` thường là `16px`.

1. `@keyframes` định nghĩa một animation có 2 trạng thái, khi thay đổi `opacity` và dịch chuyển trên mặt phẳng 2D bằng cách sử  dụng `transform: translateY()`.

2. `.bouncing-loader` đây là vùng chính của chấm tròn nảy lên và sử dụng `display: flex`
  và `justify-content: center` để đặt chúng ở giữa.

3. `.bouncing-loader > div`, chọn 3 thẻ `div`s để style theo cha nó.  `div`s sẽ có chiều rồng và dài `1rem`, sử dụng `border-radius: 50%` để biến chúng từ hình vuống thành hình tròn.

4. `margin: 3rem 0.2rem` chỉ định mỗi chấm tròn cách trên/dưới là `3rem` và trái/phải là  
    `0.2rem` để nó ko chạm vào nhau, cho nó có khoảng cách dễ thở :)).

5. `animation` là một thuộc tính chung viết tắt cho các thuộc tính khác nhau: `animation-name`, `animation-duration`, `animation-iteration-count`, `animation-direction` được sử dụng.

6. `nth-child(n)` chọn đến các phần tử con thứ n từ cha nó.

7. `animation-delay` sử dụng cho thẻ `div` thứ 2 và 3 tương ứng, để mỗi phần tử không hoạt động cùng lúc.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Tương thích tất cả.</span>

* https://caniuse.com/#feat=css-animation

<!-- tags: animation -->
### Đặt lại Box-sizing

Đặt lại mô hình hộp để `width`s và `height`s không bị ảnh hưởng bởi `border`s or `padding`.

#### CSS

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__box-sizing-reset">Demo</div>
</div>

<style>
.snippet-demo__box-sizing-reset {
  box-sizing: border-box;
  width: 200px;
  padding: 1.5em;
  color: #7983ff;
  font-family: sans-serif;
  background-color: white;
  border: 5px solid;
}
</style>

#### Giải thích

1. `box-sizing: border-box` làm cho việc thêm `padding` or `border`s không có ảnh hưởng tới `width` or `height` của phần tử.
2. `box-sizing: inherit` làm cho phần tử kế thừa `box-sizing` từ cha nó.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Tương thích tất cả.</span>

* https://caniuse.com/#feat=css3-boxsizing

<!-- tags: layout -->
### Hình tròn

Tạo ra hình tròn với CSS thuần

#### HTML

```html
<div class="circle"></div>
```

#### CSS

```css
.circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__circle"></div>
</div>

<style>
.snippet-demo__circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
</style>

#### Giải thích

`border-radius: 50%` đường cong từ viền của phần tử sẽ tạo ra hình tròn

Một hình tròn bất cứ khi nào cũng có `width` và `height` phải bằng nhau. Nếu khác nhau sẽ tạo ra hình elip

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Tương thích tất cả.</span>

* https://caniuse.com/#feat=border-radius

<!-- tags: visual -->
### Clearfix

Đảm bảo rằng một phần tử tự xóa con của mình

###### Lưu ý: Điều này chỉ hữu ích khi bản sử dụng float để hình thành bố cục. Hãy xem xét sử dụng các phương pháp xây dụng bố cục hiện đại hơn là flex và grid.

#### HTML

```html
<div class="clearfix">
  <div class="floated">float a</div>
  <div class="floated">float b</div>
  <div class="floated">float c</div>
</div>
```

#### CSS

```css
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.floated {
  float: left;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__clearfix">
    <div class="snippet-demo__floated">float a</div>
    <div class="snippet-demo__floated">float b</div>
    <div class="snippet-demo__floated">float c</div>
  </div>
</div>

<style>
.snippet-demo__clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.snippet-demo__floated {
  float: left;
}
</style>

#### Giải thích

1. `.clearfix::after` định nghĩa một phần tử giả after.
2. `content: ''` cho phép phần tử giả ấy ảnh hưởng bố cục.
3. `clear: both` chỉ ra rằng trái/phải hoặc cả 2 bên của phần tử kề với trước đó tạo thành đặt trong một khối.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Để đoạn mã này hoạt động đúng, bạn phải đảm bảo rằng không có phần tử con non-floating trong khối chứa và không có **tall floats** trước khí container clearfixed nhưng trong cùng nội dung định dạng (e.g. floated columns).</span>

<!-- tags: layout -->
### Tỷ lệ chiều rộng chiều cao không thay đổi

Phần từ có chiều rộng, nó sẽ đảm bảo chiều cao của nó vẫn tương ứng theo một cách tương ứng
(i.e., tỉ lệ width và height không thay đổi).

#### HTML

```html
<div class="constant-width-to-height-ratio"></div>
```

#### CSS

```css
.constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.constant-width-to-height-ratio::before {
  content: '';
  padding-top: 100%;
  float: left;
}
.constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
```

#### Bản mẫu

Thay đổi kích thước trình duyệt của bạn để xem tỉ lệ của phần tử vẫn giữ nguyên.

<div class="snippet-demo">
  <div class="snippet-demo__constant-width-to-height-ratio"></div>
</div>

<style>
.snippet-demo__constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.snippet-demo__constant-width-to-height-ratio::before {
  content: '';
  padding-top: 100%;
  float: left;
}
.snippet-demo__constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
</style>

#### Giải thích

`padding-top` trên `::before` phần tử giả bởi heigth bằng phần trăm width của nó.
 `100%` do đó có nghĩa là height của phần tử luôn luôn bằng `100%` width, tạo ra hình vuông tương ứng.

Phương pháp này cũng cho phép content đặt trong phần tử bình thường

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Tương thích tất cả.</span>

<!-- tags: layout -->
### Bộ đếm

Bộ đếm, về cơ bản, các biến được duy trì bởi CSS, các giá trị của nó có thể được tăng lên bởi CSS rules để theo dõi chúng sử dụng bao nhiêu lần.

#### HTML

```html
<ul>
  <li>List item</li>
  <li>List item</li>
  <li>List item</li>
</ul>
```

#### CSS

```css
ul {
  counter-reset: counter;
}

li::before {
  counter-increment: counter;
  content: counters(counter, '.') ' ';
}
```

#### Bản mẫu

<div class="snippet-demo">
	<div class="snippet-demo__countable-section">
    <ul>
      <li>List item</li>
      <li>List item</li>
      <li>
        List item
        <ul>
          <li>List item</li>
          <li>List item</li>
          <li>List item</li>
        </ul>
      </li>
    </ul>
  </div>
</div>

<style>
  .snippet-demo__countable-section ul {
    counter-reset: counter;
    list-style-type: none;
  }

  .snippet-demo__countable-section li::before {
    counter-increment: counter;
    content: counters(counter, '.') ' ';
  }
</style>

#### Giải thích

Bạn có thể tạo ra một danh sách được sắp xếp sử dụng bất kì lọai HTML nào.

1. `counter-reset` Khởi tạo bộ đếm, giá trị là tên của bộ đếm. Mặc đinh, bộ đếm bắt đầu từ 0. Thuộc tính này cũng có thể sử dụng để thay đổi giá trị của nó cho bất kì số cụ thể nào.

2. `counter-increment` Được sử dụng trong phần tử sẽ được tính. Một lần khởi tạo `counter-reset`, giá trị có thể tăng hoặc giảm.

3. `counter(name, style)` Hiện thị giá trị của một bộ đếm. Nói chúng sử dụng thuộc tính `content`. Function này có thể nhận 2 tham số, đầu tiên là tên bộ đếm và thứ 2 có thể là `decimal` or `upper-roman` (`decimal` là mặc định).

4. `counters(counter, string, style)` Hiện thị giá trị của một bộ đếm.  Nói chúng sử dụng thuộc tính `content`. Function này có thể nhận 3 tham số, đầu tiên là tên bộ đếm và thứ 2 có thể là một chuỗi , sau cùng là `decimal` or `upper-roman` (`decimal` là mặc định).

5. Một bộ đếm CSS có thể đặc biệt hữu ích cho việc tạo danh sách phác thảo, bởi vì một ví dụ mới của bộ đếm được tự động tạo trong các phần tử con. Sử dụng `counters()` function, tách văn bản có thể chèn giữa các cấp độ khác nhau của các bộ đếm nồng nhau.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Tương thích tất cả.</span>

* https://caniuse.com/#feat=css-counters

<!-- tags: visual, other -->
### Custom scrollbar

Tùy chỉnh thanh cuộn cho tài liệu và các yếu tố với **scrollable overflow**, trên nền tảng WebKit.

#### HTML

```html
<div class="custom-scrollbar">
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
/* Document scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}

/* Scrollable element */
.some-element::webkit-scrollbar {
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__custom-scrollbar">
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
  </div>
</div>

<style>
.snippet-demo__custom-scrollbar {
  height: 100px;
  overflow: auto;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar {
  width: 8px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}
</style>

#### Giải thích

1. `::-webkit-scrollbar` chọn toàn bộ phần tử thanh cuộn.
2. `::-webkit-scrollbar-track` chỉ chọn phần tử được track.
3. `::-webkit-scrollbar-thumb` chọn phần tử thanh trên thanh cuộn.

Có rất nhiều phần tử giả khác nhau có thể tạo ra thanh cuộn. Để biết thêm, hãy tham khảo [WebKit Blog](https://webkit.org/blog/363/styling-scrollbars/)

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Kiểu dáng thanh cuộn dường như không có trên bất kì tiêu chuẩn theo dõi nào.</span>

* https://caniuse.com/#feat=css-scrollbar

<!-- tags: visual -->
### Custom text selection

Thay đổi kiểu dáng của văn bản được chọn.

#### HTML

```html
<p class="custom-text-selection">Select some of this text.</p>
```

#### CSS

```css
::selection {
  background: aquamarine;
  color: black;
}
.custom-text-selection::selection {
  background: deeppink;
  color: white;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <p class="snippet-demo__custom-text-selection">Select some of this text.</p>
</div>

<style>
.snippet-demo__custom-text-selection::selection {
  background: deeppink;
  color: white;
}
.snippet-demo__custom-text-selection::-moz-selection {
  background: deeppink;
  color: white;
}
</style>

#### Giải thích

`::selection` định nghĩa một bộ chọn giả trên một phần tử để định kiểu văn bản khi được chọn.Lưu ý rằng nếu bạn không kết hợp với bộ chọn nào khác của bạn thì style sẽ được áp đụng ở **document root level**, chọn bất kì phần tử nào.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Yêu cầu **prefixes** để được hỗ trợ đầy đủ và không thực sự trong bất kì đặc điểm kĩ thuật nào.</span>

* https://caniuse.com/#feat=css-selection

<!-- tags: visual -->
### Custom variables

Các biến CSS chưa các giá trị cụ thể để được sử dụng lại trong suốt một tài liệu.

#### HTML

```html
<p class="custom-variables">CSS is awesome!</p>
```

#### CSS

```css
:root {
  --some-color: #da7800;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray, 0 0 0.2em slategray;
}

.custom-variables {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__custom-variables">
    <p>CSS is awesome!</p>
  </div>
</div>

<style>
.snippet-demo__custom-variables {
  --some-color: #686868;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray , 0 0 0.2em slategray;
}

.snippet-demo__custom-variables p {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
</style>

#### Giải thích

Các biến được định nghĩa trên toàn bộ trong `:root` CSS lớp giả tương ứng với phần tử gốc của một cây đại diện cho tài liệu. Các biến cũng có thể được đưa vào bộ chọn nếu được xác định trong khối.

Khai báo biến với `--variable-name:`.

Tái sử dụng các biến trong toàn bộ document `var(--variable-name)` function.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Tương thích với tất cả.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: other -->
### Disable selection

Làm cho không thể chọn được nội dung

#### HTML

```html
<p>You can select me.</p>
<p class="unselectable">You can't select me!</p>
```

#### CSS

```css
.unselectable {
  user-select: none;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <p>You can select me.</p>
  <p class="snippet-demo__disable-selection">You can't select me!</p>
</div>

<style>
.snippet-demo__disable-selection {
  user-select: none;
}
</style>

#### Giải thích

`user-select: none` xác định đoạn văn bản không thể chọn.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Yêu cầu prefixes để được hỗ trợ đầy đủ.</span>
<span class="snippet__support-note">⚠️ Đây không phải phương pháp an toàn để ngăn người dùng sao chép nội dung.</span>

* https://caniuse.com/#feat=user-select-none

<!-- tags: interactivity -->
### Donut spinner

Tạo ra vòng tròn xoay xoay có thể được sử dụng để chỉ việc load.

#### HTML

```html
<div class="donut"></div>
```

#### CSS

```css
@keyframes donut-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.donut {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: donut-spin 1.2s linear infinite;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__donut-spinner"></div>
</div>

<style>
@keyframes snippet-demo__donut-spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg);}
}
.snippet-demo__donut-spinner {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: snippet-demo__donut-spin 1.2s linear infinite;
}
</style>

#### Giải thích

Sử dụng độ trong suốt 50% `border` cho toàn bộ phần tử, ngoại trừ một bên sẽ đóng vai trò cho phần quay.
 Sử dụng `animation` để xoay phần tử.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Yêu cầu prefixes để được hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=css-animation
* https://caniuse.com/#feat=transforms2d

<!-- tags: animation -->
### Dynamic shadow

Tạo ra bóng tương tự như `box-shadow` mà dựa trên màu sắc của chính phần tử.

#### HTML

```html
<div class="dynamic-shadow-parent">
  <div class="dynamic-shadow"></div>
</div>
```

#### CSS

```css
.dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.dynamic-shadow::after {
  content: '';
  width: 100%;
  height: 100%;
  position: absolute;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__dynamic-shadow-parent">
    <div class="snippet-demo__dynamic-shadow"></div>
  </div>
</div>

<style>
.snippet-demo__dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.snippet-demo__dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.snippet-demo__dynamic-shadow::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
</style>

#### Giải thích

Đoạn mã yêu cầu phức tạp về bối cảnh xếp chồng mới có thể, sao cho phần tử giả được đặt dưới phần tử đó trong khi vẫn nhìn thấy được.

1. `position: relative` thiết lập định vị khối cho các phần tử con.
2. `z-index: 1` thiết lập bối cảnh xếp chồng.
3. `position: relative` trên thẻ con thiết lập định vị cho các phần tử giả .
4. `::after` định nghĩa một phần tử giả.
5. `position: absolute` lấy phần tử giả tách biệt document và định vị nó quan hệ vs cha.
6. `width: 100%` and `height: 100%`  kích thước phần tử mẫu lấp đầy kích thước cha nó, làm nó cần bằng về kích thước.
7. `background: inherit` phần tử mẫu thừa kế quy định về góc tuyến tính trên phần tử.
8. `top: 0.5rem` thêm phần tử giả xuống nhẹ từ cha. 
9. `filter: blur(0.4rem)` sẽ làm mờ phần tử giả tạo ra sự xuất hiện của bóng bên dưới.
10. `opacity: 0.7` làm cho phần tử giả trong suốt một phần.
11. `z-index: -1` định vị phần tự nấp sau phía cha.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Yêu cầu prefixes để hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=css-filters

<!-- tags: visual -->
### Easing variables

Các biến được sử dụng lại cho thuộc tính `transition-timing-function`, rõ ràng khi tích hợp sẵn với `ease`, `ease-in`, `ease-out` and `ease-in-out`.

#### HTML

```html
<div class="easing-variables"></div>
```

#### CSS

```css
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.easing-variables {
  width: 50px;
  height: 50px;
  background: #333;
  transition: transform 1s var(--ease-out-quart);
}

.easing-variables:hover {
  transform: rotate(45deg);
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__easing-variables">Hover</div>
</div>

<style>
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.snippet-demo__easing-variables {
  width: 75px;
  height: 75px;
  background: #333;
  color: white;
  font-size: 0.8rem;
  font-weight: bold;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: transform 1s var(--ease-out-quart);
}

.snippet-demo__easing-variables:hover {
  transform: rotate(45deg);
}
</style>

#### Giải thích

Các biến được định nghĩa toàn cục trong `:root` CSS **pseudo-class** khớp với phần tử gốc . ~~In HTML, `:root` represents the `<html>` element and is identical to the selector `html`, except that its specificity is higher.~~

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Tương thích với tất cả.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: animation -->
### Etched text

Tạo ra một hiệu ứng mà chữ xuất hiện sẽ được khắc hoặc khắc vào nền.

#### HTML

```html
<p class="etched-text">I appear etched into the background.</p>
```

#### CSS

```css
.etched-text {
  text-shadow: 0 2px white;
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <p class="snippet-demo__etched-text">I appear etched into the background.</p>
</div>

<style>
.snippet-demo__etched-text {
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
  text-shadow: 0 2px 0 white;
}
</style>

#### Giải thích

`text-shadow: 0 2px white` tạo ra một cái bóng bù vào `0px` theo chiều ngang và `2px` theo chiều dọc từ vị trí gốc.

Nền phải tối hơn bóng để hiệu ứng này hoạt động.

Màu văn bản nên hơi nhạt dần để làm cho nó trông giống như nó được khắc/khắc ra nền.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Tương thích với tất cả.</span>

* https://caniuse.com/#feat=css-textshadow

<!-- tags: visual -->
### Evenly distributed children

Giãn đều các phần tử con trong phần từ cha.

#### HTML

```html
<div class="evenly-distributed-children">
  <p>Item1</p>
  <p>Item2</p>
  <p>Item3</p>
</div>
```

#### CSS

```css
.evenly-distributed-children {
  display: flex;
  justify-content: space-between;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__evenly-distributed-children">
    <p>Item1</p>
    <p>Item2</p>
    <p>Item3</p>
  </div>
</div>

<style>
.snippet-demo__evenly-distributed-children {
  display: flex;
  width: 100%;  
  justify-content: space-between;
}
</style>

#### Giải thích

1. `display: flex` cho phép flexbox.
2. `justify-content: space-between` giãn đều các phần tử con theo chiều ngang. Mục đầu tiên được đặt bên cạnh trái, trong khi đó mục cuối cùng được đặt bên phải.

Cách khác, sử dụng `justify-content: space-around` giãn xung quanh thẻ con một khoảng đều, chứ không phải giữa chúng.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Needs prefixes for full support.</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->
### Flexbox centering

Thẻ con nằm giữa trung tâm theo chiều ngang dọc, trái phải thẻ cha, sử dụng `flexbox`.

#### HTML

```html
<div class="flexbox-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__flexbox-centering">
    <p class="snippet-demo__flexbox-centering__child">Centered content.</p>
  </div>
</div>

<style>
.snippet-demo__flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Giải thích

1. `display: flex` cho phép flexbox
2. `justify-content: center` ở giữa theo chiều ngang.
3. `align-items: center` ở giữa theo chiều dọc.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Needs prefixes for full support.</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->
### Gradient text

Gives text a gradient color.

#### HTML

```html
<p class="gradient-text">Gradient text</p>
```

#### CSS

```css
.gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <p class="snippet-demo__gradient-text">
    Gradient text
  </p>
</div>

<style>
.snippet-demo__gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  font-size: 2rem;
  font-weight: bold;
  margin: 0;
}
</style>

#### Giải thích

1. `background: -webkit-linear-gradient(...)` ~~gives the text element a gradient background.
2. `webkit-text-fill-color: transparent` fills the text with a transparent color.
3. `webkit-background-clip: text` clips the background with the text, filling the text with
   the gradient background as the color.~~

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Uses non-standard properties.</span>

* https://caniuse.com/#feat=text-stroke

<!-- tags: visual -->
### Grid centering

Horizontally and vertically centers a child element within a parent element using `grid`.

#### HTML

```html
<div class="grid-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
}
```

#### Bản mẫu

<div class="snippet-demo">
  <div class="snippet-demo__grid-centering">
    <p class="snippet-demo__grid-centering__child">Centered content.</p>
  </div>
</div>

<style>
.snippet-demo__grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Giải thích

~~1. `display: grid` enables grid.
2. `justify-content: center` centers the child horizontally.
3. `align-items: center` centers the child vertically.~~

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Tương thích với tất cả.</span>

* https://caniuse.com/#feat=css-grid

<!-- tags: layout -->
### Grid layout

Basic website layout using `grid`.

#### HTML

```html
<div class="grid-layout">
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">
    Content
    <br>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
  </div>
  <div class="footer">Footer</div>
</div>
```

#### CSS

```css
.grid-layout {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    'sidebar header header'
    'sidebar content content'
    'sidebar footer  footer';
  color: white;
}
.grid-layout > div {
  background: #333;
  padding: 10px;
}
.sidebar {
  grid-area: sidebar;
}
.content {
  grid-area: content;
}
.header {
  grid-area: header;
}
.footer {
  grid-area: footer;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__grid-layout">
    <div class="box snippet-demo__grid-layout__header">Header</div>
    <div class="box snippet-demo__grid-layout__sidebar">Sidebar</div>
    <div class="box snippet-demo__grid-layout__content">Content
      <br> Lorem ipsum dolor sit amet, consectetur adipisicing elit.
    </div>
    <div class="box snippet-demo__grid-layout__footer">Footer</div>
  </div>
</div>

<style>
.snippet-demo__grid-layout {
  margin: 1em;
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    "sidebar header header"
    "sidebar content content"
    "sidebar  footer  footer";
  background-color: #fff;
  color: white;
}
.snippet-demo__grid-layout > div {
  background: #333;
  padding: 10px;
}
.snippet-demo__grid-layout__sidebar {
    grid-area: sidebar;
}
.snippet-demo__grid-layout__content {
    grid-area: content;
}
.snippet-demo__grid-layout__header {
    grid-area: header;
}
.snippet-demo__grid-layout__footer {
    grid-area: footer;
}
</style>

#### Explanation

1. `display: grid` enables grid.
2. `grid-gap: 10px` defines spacing between the elements.
3. `grid-template-columns: repeat(3, 1fr)` defines 3 columns of the same size.
4. `grid-template-areas` defines the names of grid areas.
5. `grid-area: sidebar` makes the element use the area with the name `sidebar`.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-grid

<!-- tags: layout -->
### Hairline border

Gives an element a border equal to 1 native device pixel in width, which can look
very sharp and crisp.

#### HTML

```html
<div class="hairline-border">text</div>
```

#### CSS

```css
.hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hairline-border">Text with a hairline border around it.</p>
</div>

<style>
.snippet-demo__hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
</style>

#### Explanation

~~1. `box-shadow`, when only using spread, adds a pseudo-border which can use subpixels\*.
2. Use `@media (min-resolution: ...)` to check the device pixel ratio (`1dppx` equals 96 DPI),
   setting the spread of the `box-shadow` equal to `1 / dppx`.~~

#### Browser Support

<span class="snippet__support-note">⚠️ Needs alternate syntax and JavaScript user agent checking for full support.</span>

* https://caniuse.com/#feat=css-boxshadow
* https://caniuse.com/#feat=css-media-resolution

<hr>

\*Chrome does not support subpixel values on `border`. Safari does not support subpixel values on `box-shadow`. Firefox supports subpixel values on both.

<!-- tags: visual -->
### Hover underline animation

Creates an animated underline effect when the text is hovered over.

<small>**Credit:** https://flatuicolors.com/</small>

#### HTML

```html
<p class="hover-underline-animation">Hover this text to see the effect!</p>
```

#### CSS

```css
.hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hover-underline-animation">Hover this text to see the effect!</p>
</div>

<style>
.snippet-demo__hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.snippet-demo__hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.snippet-demo__hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
</style>

#### Explanation

~~1. `display: inline-block` makes the block `p` an `inline-block` to prevent the underline from
   spanning the entire parent width rather than just the content (text).
2. `position: relative` on the element establishes a Cartesian positioning context for pseudo-elements.
3. `::after` defines a pseudo-element.
4. `position: absolute` takes the pseudo element out of the flow of the document and positions it in relation to the parent.
5. `width: 100%` ensures the pseudo-element spans the entire width of the text block.
6. `transform: scaleX(0)` initially scales the pseudo element to 0 so it has no width and is not visible.
7. `bottom: 0` and `left: 0` position it to the bottom left of the block.
8. `transition: transform 0.25s ease-out` means changes to `transform` will be transitioned over 0.25 seconds
   with an `ease-out` timing function.
9. `transform-origin: bottom right` means the transform anchor point is positioned at the bottom right of the block.
10. `:hover::after` then uses `scaleX(1)` to transition the width to 100%, then changes the `transform-origin`
    to `bottom left` so that the anchor point is reversed, allowing it transition out in the other direction when~~
    hovered off.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=transforms2d
* https://caniuse.com/#feat=css-transitions

<!-- tags: animation -->
### Mouse cursor gradient tracking

A hover effect where the gradient follows the mouse cursor.

<small class="snippet__credit">**Credit:** [Tobias Reich](https://codepen.io/electerious/pen/MQrRxX)</small>

#### HTML

```html
<button class="mouse-cursor-gradient-tracking">
  <span>Hover me</span>
</button>
```

#### CSS

```css
.mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.mouse-cursor-gradient-tracking span {
  position: relative;
}

.mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, pink, transparent);
  transform: translate(-50%, -50%);
  transition: width 0.2s ease, height 0.2s ease;
}

.mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
```

#### JavaScript

```js
var btn = document.querySelector('.mouse-cursor-gradient-tracking')
btn.onmousemove = function(e) {
  var x = e.pageX - btn.offsetLeft
  var y = e.pageY - btn.offsetTop
  btn.style.setProperty('--x', x + 'px')
  btn.style.setProperty('--y', y + 'px')
}
```

#### Demo

<div class="snippet-demo">
  <button class="snippet-demo__mouse-cursor-gradient-tracking">
    <span>Hover me</span>
  </button>
</div>

<style>
.snippet-demo__mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.snippet-demo__mouse-cursor-gradient-tracking span {
  position: relative;
}

.snippet-demo__mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, aqua, rgba(0,255,255,0.0001));
  transform: translate(-50%, -50%);
  transition: width .2s ease, height .2s ease;
}

.snippet-demo__mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
</style>

<script>
(function () {
  var btn = document.querySelector('.snippet-demo__mouse-cursor-gradient-tracking')
  btn.onmousemove = function (e) {
    var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
    var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
    btn.style.setProperty('--x', x + 'px')
    btn.style.setProperty('--y', y + 'px')
  }
})()
</script>

#### Explanation

_TODO_

**Note!**

If the element's parent has a positioning context (`position: relative`), you will need to subtract
its offsets as well.

```js
var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
```

#### Browser support

<div class="snippet__requires-javascript">Requires JavaScript</div>
<span class="snippet__support-note">⚠️ Requires JavaScript.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: visual, interactivity -->
### :not selector

The `:not` psuedo selector is useful for styling a group of elements, while leaving the last (or specified) element unstyled.

#### HTML

```html
<ul class="css-not-selector-shortcut">
  <li>One</li>
  <li>Two</li>
  <li>Three</li>
  <li>Four</li>
  <li>Five</li>
</ul>
```

#### CSS

```css
.css-not-selector-shortcut {
  display: flex;
}

li {
  list-style-type: none;
  margin: 0;
  padding: 0 0.75rem;
}

li:not(:last-child) {
  border-right: 2px solid #d2d5e4;
}
```

#### Demo

<div class="snippet-demo">
  <ul class="snippet-demo__css-not-selector-shortcut">
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
    <li>Four</li>
    <li>Five</li>
  </ul>
</div>

<style>
.snippet-demo__css-not-selector-shortcut {
  display: flex;
  padding: 0;
}

.snippet-demo__css-not-selector-shortcut li {
  list-style-type: none;
  margin: 0;
  padding: 0 0.75rem;
}

.snippet-demo__css-not-selector-shortcut li:not(:last-child) {
  border-right: 2px solid #d2d5e4
}
</style>

#### Explanation

`li:not(:last-child)` specifies that the styles should apply to all `li` elements except
the `:last-child`.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-sel3

<!-- tags: visual -->

