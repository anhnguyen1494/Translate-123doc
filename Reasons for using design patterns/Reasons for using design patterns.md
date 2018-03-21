[Source](https://www.codeproject.com/Tips/808058/Reasons-for-using-design-patterns "Permalink to Reasons for using design patterns")

# Lý do sử dụng design patterns

## Giới thiệu

Tiếp tục từ một bài báo có tựa đề [Why design is Critical to Software Development][1], Tôi muốn giải quyết một khía cạnh nâng cao hơn một chút về thiết kế phần mềm được gọi là `Design Patterns`.
 Như bài báo trước của tôi, ý tưởng đến trong một cuộc thảo luận liên quan đến sự thành công của thiết kế phần mềm với một đồng nghiệp làm việc.
 Nhân vật chính của cuộc thảo luận là ý kiến ​​cho rằng `Design Patterns` quá tốn thời gian để sử dụng trong lĩnh vực phát triển phần mềm thương mại.
 Mục đích của tôi ở đây là để chứng minh tại sao tôi tin rằng đó là sai.

Tôi sẽ không đi vào bất kỳ chi tiết về kiến trúc hoặc thực hiện của bất kỳ `Design Patterns` cụ thể nào. Có rất nhiều nguồn tuyệt vời có sẵn từ những nơi khác.

## Design Pattern là gì?

Bắt đầu nhé,`Design Pattern` chính xác là gì? Dưới đây là một vài định nghĩa cho thuật ngữ:
Trích từ [Wikipedia][2]:

> "Design pattern trong kiến ​​trúc và khoa học máy tính là một cách chính để ghi lại một giải pháp cho một vấn đề thiết kế trong một lĩnh vực chuyên môn cụ thể."

Trích từ [Data & Object Factory][3]:

> "Design patterns là các giải pháp định kỳ cho các vấn đề thiết kế phần mềm mà bạn tìm thấy trong phát triển ứng dụng trong thế giới thực.Patterns là về thiết kế và tương tác của các đối tượng, cũng như cung cấp một nền tảng truyền thông liên quan đến **elegant**, các giải pháp tái sử dụng được đối với các thách thức lập trình thông thường gặp phải."

`Design Pattern` là một mục đích chung của việc giải quyết vấn đề, có thể được áp dụng cho một giải pháp cụ thể. Khi các nhà phát triển phần mềm có xu hướng giải quyết nhiều loại vấn đề tương tự, nó có ý nghĩa rằng bất kỳ giải pháp phần mềm sẽ kết hợp các yếu tố tương tự từ các giải pháp khác. Tại sao phải phát minh lại **wheel**?

## Tài liệu tốt và hiểu nó

Theo `Design Patterns` được tghi ài liệu và hiểu rõ bởi các kiến ​​trúc sư phần mềm, nhà thiết kế và phát triển, thì ứng dụng của họ trong một giải pháp cụ thể cũng sẽ được hiểu rõ.

`Design Patterns` cung cấp cho một nhà phát triển phần mềm một loạt các giải pháp được thử và được thử nghiệm cho các vấn đề phổ biến, do đó giảm nguy cơ kỹ thuật cho dự án bằng cách không phải sử dụng một thiết kế mới và chưa được kiểm tra.

`Design Patterns` có thể ban đầu dẫn đến giảm thời gian phát triển, ~~as there is a learning curve if the team are unfamiliar with them. However, looking further down the development pipeline, once familiarity with them increases, development timescales should gradually reduce.~~

## Sự tương đồng với kỹ thuật xây dựng

Để chỉ ra sự tương tự của một `Design Pattern` từ lĩnh vực kỹ thuật xâyd ựng (như tôi đã nêu trong bài báo của tôi [Why design is Critical to Software Development][1]) có những điểm tương đồng gần giống với công nghệ phần mềm),sẽ là một giải pháp để vượt sông. Đây là vấn đề thường xuyên đối với các kỹ sư xây dựng, mà có một vài giải pháp được chứng minh và hiểu rõ. Các kỹ sư dân dụng có thể xây dựng một cây cầu hoặc một đường hầm.

Tại sao một kỹ sư xây dựng cố gắng giải quyết vấn đề này từ đầu khi có những giải pháp thế giới thực có thể được đề cập đến? Có sự tương đồng gần gũi giữa kỹ sư xây dựng giải quyết vấn đề về sông, và kỹ sư phần mềm giải quyết vấn đề phần mềm:

* Các giải pháp (cầu hoặc đường hầm) đều được hiểu và ghi lại
* Các giải pháp (cầu hoặc đường hầm) được giải quyết thường xuyên các vấn đề kỹ thuật xây dựng
* Các cách giải quyết (bắc cầu hay đường hầm xây dựng nguyên liệu để các ví dụ có thể được lựa chọn định hướng cụ thể) **thiếu** 

Lập luận chống lại `Design Patterns` cho thấy chúng không phù hợp với mục đích thương mại do quá trình thực hiện quá lâu và không làm chủ được nó. `Design Patterns` tiết kiệm thời gian (khi được xem xét qua suốt đời của ứng dụng) bằng cách cho nhà phát triển lựa chọn các giải pháp đã được thử và thử nghiệm sẵn có mà họ có thể tùy chỉnh theo nhu cầu cụ thể của riêng họ.

Chỉ có một vấn đề tôi đã gặp với `Design Patterns` là họ mất quá nhiều thời gian để học. Một vài trong số đó có thể khó khăn để hiểu và nắm chắc.  Đây là một lời chỉ trích thích hợp, vì nó đòi hỏi một nhà phát triển có tay nghề cao hơn để sử dụng chúng. Điều này có thể làm tăng các chi phí ban đầu cho dự án. Tuy nhiên, nhìn tổng quan cả quãng thời gian của một ứng dụng tôi hoàn toàn mong đợi những chi phí phát triển ban đầu được bù đắp do các chi phí bảo trì liên tục sẽ thấp hơn và khả năng mở rộng dễ dàng hơn. (làm cho ứng dụng dễ dàng mở rộng trong tương lai để đáp ứng những cơ hội mới và sẽ nổi lên).

`Design Patterns` giảm sự phức tạp và do đó giải pháp trở nên dễ hiểu hơn.

`Design Patterns` là các giải pháp được thử và thử nghiệm, nhà phát triển không cần phải bắt đầu từ đầu, và có thể chạy nền với một giải pháp đã được chứng minh là có hiệu quả (miễn là  `Design Pattern` được sử dụng giải quyết một vấn đề tương tự). Sẽ là sai khi mong đợi một cây cầu để giải quyết vấn đề băng qua đại dương, nơi mà cây cầu chỉ đơn giản là không phù hợp.

## Lợi ích của việc sử dụng Design Paterns

`Design Patterns` cung cấp các lợi ích sau.

* Chúng cung cấp cho nhà phát triển một loạt các giải pháp thử và thử nghiệm để làm việc tốt
* Chúng là ngôn ngữ trung lập do vậy bạn có thể áp dụng vào bất cứ ngôn ngữ nào hỗ trợ hướng đối tượng.
* Chúng hỗ trợ truyền thông bởi thực tế là họ có tài liệu tốt và có thể được nghiên cứu nếu đó không phải là trường hợp khác.
* Chúng có ghi lại cái theo dõi kiểm chứng khi được sử dụng rộng rãi và vì thế giảm thiểu rủi ro công nghệ trong dự án.
* Chúng rất linh hoạt và có thể sư dụng thực tế trong bất kỳ loại ứng dụng hoặc tên miền nào

## Kết luận

`Design Patterns`, mặc dù khó khăn học tập ban đầu, là một sự đầu tư rất đáng giá. Họ sẽ cho phép bạn thực hiện các giải pháp được thử và thử nghiệm cho các vấn đề, do đó tiết kiệm thời gian và nỗ lực trong giai đoạn triển khai của vòng đời phát triển phần mềm. Bằng cách sử dụng các giải pháp được hiểu rõ và có tài liệu, sản phẩm cuối cùng sẽ có một mức độ hiểu biết cao hơn nhiều. Nếu giải pháp được dễ dàng hơn để hiểu, sau đó bằng cách mở rộng, nó cũng sẽ được dễ dàng hơn để duy trì.

[1]: http://www.codeproject.com/Tips/806867/Why-Design-is-Critical-to-Software-Development
[2]: http://en.wikipedia.org/wiki/Design_pattern
[3]: http://www.dofactory.com/Patterns/Patterns.aspx

## Luyện tập
- https://coderoncode.com/design-patterns/programming/php/coding/development/2014/01/19/design-patterns-php-factories.html
- https://www.binpress.com/tutorial/the-factory-design-pattern-explained-by-example/142
- https://www.codeproject.com/Articles/852232/PHP-Singleton-Pattern-A-Step-by-Step-And-Problem-s
- http://www.fluffycat.com/PHP-Design-Patterns/

**Từ khóa:** `how to separate code to package php`, `step by step php design pattern singleton`(thay đổi singleton sang các thứ khác để có nhiều kết quả hơn)
