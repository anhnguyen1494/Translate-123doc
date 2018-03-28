## Những sai lầm phổ biến của các nhà phát triển ứng dụng trong phát triển cơ sở dữ liệu?

_source https://stackoverflow.com/questions/621884/database-development-mistakes-made-by-application-developers_

**1. Không sử dụng các chỉ số thích hợp**

Đây là một điều khá đơn giản nhưng vẫn xảy ra bất kì lúc nào. Khóa ngoài nên có các indexes. Nếu bạn đang sử dụng một trường trong một lệnh

WHERE bạn nên (có thể) có một chỉ mục trên đó. Các chỉ mục như vậy thường bao gồm nhiều cột dựa trên các truy vấn bạn cần thực hiện.

**2. Không thực thi tất cả tham chiếu**

Cơ sở dữ liệu của bạn có thể thay đổi nhưng nếu cơ sở dữ liệu của bạn hỗ trợ tất cả tham chiếu--có nghĩa là tất cả các khóa ngoài được đảm bảo trỏ đến một thực thế tồn tại--bạn nên sử dụng nó.

Rất phổ biến để thấy sự thất bại này trên cơ sở dữ liệu MySQL. Tôi không tin rằng MyISAM hỗ trợ nó. InnoDB làm được. Bạn sẽ tìm thấy những người đang sử dụng MyISAM hoặc những người đang sử dụng InnoDB nhưng dù thế nào đi nữa cũng không sử dụng nó.

Thêm nữa:

- [Những ràng buộc quan trọng như NOT NULL và FOREIGN KEY nếu tôi sẽ luôn luôn kiểm soát đầu vào cơ sở dữ liệu của tôi với php?](https://stackoverflow.com/questions/382309/how-important-are-constraints-like-not-null-and-foreign-key-if-ill-always-contr)
- [Khóa ngoài thực sự cần thiết trong một thiết kế cơ sở dữ liệu?](https://stackoverflow.com/questions/18717/are-foreign-keys-really-necessary-in-a-database-design)
- [Khóa ngoài thực sự cần thiết trong một thiết kế cơ sở dữ liệu?](http://www.diovo.com/2008/08/are-foreign-keys-really-necessary-in-a-database-design/)

**3. Sử dụng các khóa chính tự nhiên chứ không phải là để đại diện (kỹ thuật)**

Các khóa tự nhiên là các khoá dựa trên dữ liệu bên ngoài có ý nghĩa đó (có vẻ là) duy nhất.Các ví dụ phổ biến là mã sản phẩm, mã bang 2-chữ-cái (US), **social security number** và vv.... Các khóa chính thay thế hoặc kỹ thuật chính là những khoá hoàn toàn không có ý nghĩa bên ngoài hệ thống. Chúng được sinh ra hoàn toàn để xác định thực thể vàthường là các trường tự động gia tăng (SQL Server, MySQL, khác) hoặc các trình tự (nhất là Oracle).

Theo tôi, bạn nên **luôn luôn** sử dụng các khóa đại diện. Vấn đề này đã đưa ra trong những câu hỏi sau:

- [Bạn thích khóa chính của mình như thế nào?](https://stackoverflow.com/questions/404040/how-do-you-like-your-primary-keys)
- [Cách luyện tập tốt nhất cho các khóa chính trong các bảng?](https://stackoverflow.com/questions/337503/whats-the-best-practice-for-primary-keys-in-tables)
- [Bạn sử dụng định dạng khóa chính nào trong trường hợp này.](https://stackoverflow.com/questions/506164/which-format-of-primary-key-would-you-use-in-this-situation)
- [Khóa đại diên vs khóa tự nhiên/vai trò](https://stackoverflow.com/questions/63090/surrogate-vs-natural-business-keys)
- [Tôi có nên dành riêng trường khóa chính?](https://stackoverflow.com/questions/166750/should-i-have-a-dedicated-primary-key-field)

Đây là một chủ đề gây nhiều tranh cãi mà bạn sẽ không nhận được ý kiến chung.Trong khi bạn có thể tìm thấy một số người, những người nghĩ rằng các khóa tự nhiên là trong một số tình huống OK, bạn sẽ không tìm thấy bất kỳ lời chỉ trích nào khóa đại diện khác không cần thiết. Đó là một nhược điểm nhỏ nếu bạn hỏi tôi.

Nhớ lại, ngay đến [các quốc gia có thể không còn tồn tại](http://en.wikipedia.org/wiki/ISO_3166-1) (Ví dụ từ Yugoslavia).

**4. Viết các truy vấn yêu cầu

DISTINCT hoạt động**

Bạn thường thấy điều này trong các truy vấn ORM-generated. Nhìn vào đầu ra log từ Hibernate và bạn sẽ thấy tất cả các truy vấn bắt đầu với:

SELECT DISTINCT ...

Đây là một chút của một shortcut để đảm bảo bạn không trả lại các hàng trùng lặp và do đó nhận được các đối tượng trùng lặp. Đôi khi bạn cũng thấy mọi người đang làm việc này. Nếu bạn nhìn thấy nó quá nhiều đó là một flag red thực sự. Không phải cái đó

DISTINCT là xấu hoặc không có ứng dụng hợp lệ. Nó tốt (cả 2 mặt) nhưng nó không phải đại diện hoặc tạm thời để viết các câu truy vấn đúng.

Từ [Tại sao tôi gét DISTINCT](http://weblogs.sqlteam.com/markc/archive/2008/11/11/60752.aspx):

> Trường hợp mọi thứ bắt đầu trở nên tôi tệ theo ý kiến ​​của tôi là khi một nhà phát triển đang xây dựng truy vấn quan hệ, ghép bảng lại với nhau, và đột nhiên anh ta nhận ra nó **trông** như ông đang bị trùng lặp (hoặc thậm chí nhiều hơn) các hàng và phản ứng tức thời của ông..."giải pháp" của ông đối với "vấn đề" này là ném vào từ khóa DISTINCT và **POOF** tất cả những rắc rối của ông đi.

**5. Khuyến khích tập hợp các ghép nối**

Một sai lầm phổ biến khác của nhà phát triển ứng dụng cơ sở dữ liệu  là không nhận ra phép hợp(ví dụ như mệnh đề GROUP BY) tốn kém hơn thế nào so với các phép nối.

Để cung cấp cho bạn một ý tưởng về sự phổ biến rộng rãi này là, Tôi đã viết về chủ đề này nhiều lần ở đây và được downvoted rất nhiều cho nó. Ví dụ:

Từ [SQL statement - “join” vs “group by and having”](https://stackoverflow.com/questions/477006/sql-statement-join-vs-group-by-and-having/477013#477013):

> Truy vấn đầu tiên:

SELECT userid
FROM userrole
WHERE roleid IN (1, 2, 3)
GROUP by userid
HAVING COUNT(1) = 3

> Thời gian truy vấn: 0.312 s

> Truy vấn thứ 2:

SELECT t1.userid
FROM userrole t1
JOIN userrole t2 ON t1.userid = t2.userid AND t2.roleid = 2
JOIN userrole t3 ON t2.userid = t3.userid AND t3.roleid = 3
AND t1.roleid = 1

> Thời gian truy vấn: 0.016 s

> Chuẩn luôn. Ghép nối Tôi đề xuất ** nhanh gấp 2 lần nhóm.**

**6. Không đơn giản hóa các truy vấn phức tạp thông qua các view**

Không phải tất cả các nhà cung cấp cơ sở dữ liệu đều hỗ trợ views nhưng đối với những người làm, họ có thể rất đơn giản hóa các truy vấn nếu được sử dụng một cách thận trọng. Ví dụ,trên một dự án tôi sử dụng một [generic Party model](http://www.tdan.com/view-articles/5014/) cho CRM. Đây là một kỹ thuật mô hình rất mạnh mẽ và linh hoạt nhưng có thể dẫn đến nhiều ghép nôi. Trong mô hình này đã có:

- **Party**: người và tổ chức;
- **Party Role**: những điều mà các bên đã làm, ví dụ như Employee and Employer;
- **Party Role Relationship**: làm thế nào những vai trò liên quan đến nhau.

Ví dụ:

- Ted là 1 Person, là 1 tập con Party;
- Ted có nhiều luật, 1 trong số chúng là Employee;
- Intel là 1 tổ chức, là 1 tập con cửa Party;
- Intel có nhiều luật, 1 trong số chúng là Employer;
- Intel tuyển Ted, nghĩa là có quan hệ giữa các luật tương ứng của chúng.

Vì vậy, có năm table tham gia để liên kết Ted **to his employer**.Bạn giả định tất cả nhân viên là Người (không phải tổ chức) và cung cấp các helper view:

CREATE VIEW vw_employee AS
SELECT p.title, p.given_names, p.surname, p.date_of_birth, p2.party_name employer_name
FROM person p
JOIN party py ON py.id = p.id
JOIN party_role child ON p.id = child.party_id
JOIN party_role_relationship prr ON child.id = prr.child_id AND prr.type = 'EMPLOYMENT'
JOIN party_role parent ON parent.id = prr.parent_id = parent.id
JOIN party p2 ON parent.party_id = p2.id

Và đột nhiên bạn có một cái nhìn rất đơn giản về dữ liệu mà bạn muốn nhưng trên một mô hình dữ liệu có tính linh hoạt cao.

**7.  Không cải thiện đầu vào**

Đây là một cái rất lớn. Bây giờ tôi thích PHP nhưng nếu bạn không biết những gì bạn đang làm rất dễ dàng để tạo các trang web dễ bị tấn công. Không có gì kết luận nó tốt hơn so với [story of little Bobby Tables](http://xkcd.com/327/).

Dữ liệu được cung cấp bởi người dùng bằng các URL, dữ liệu biểu mẫu **và cookie** phải luôn được coi là không tốt và cần được lọc. Đảm bảo bạn đang nhận được những gì bạn mong đợi.

**8.Không sử dụng các câu lệnh được chuẩn bị**

Báo cáo chuẩn bị là khi bạn biên dịch một truy vấn trừ dữ liệu được sử dụng trong chèn, cập nhật và 

WHERE clauses và sẽ cung cấp dữ liệu cho nó sau. Ví dụ:

SELECT * FROM users WHERE username = 'bob'

vs

SELECT * FROM users WHERE username = ?

or

SELECT * FROM users WHERE username = :username

tùy thuộc vào nền tảng của bạn.

Tôi đã từng thấy các cơ sở dữ liệu bị phá hủy vì điều này. Về cơ bản,mỗi lần bất kỳ cơ sở dữ liệu hiện đại gặp một quer mới nó phải biên dịch. Nếu nó gặp một truy vấn nó được nhìn thấy trước, bạn đang cho cơ sở dữ liệu cơ hội để cache truy vấn biên dịch và kế hoạch thực hiện. Bằng cách làm các truy vấn rất nhiều bạn đang cho cơ sở dữ liệu cơ hội tìm kiếm và tối ưu thích hợp (ví dụ, bằng cách ghim truy vấn đã biên dịch trong bộ nhớ).

Sử dụng các câu lệnh chuẩn bị cũng sẽ cung cấp cho bạn số liệu thống kê có ý nghĩa Sử dụng các câu lệnh chuẩn bị cũng sẽ cung cấp cho bạn số liệu thống kê có ý nghĩa.

Các câu lệnh được chuẩn bị cũng sẽ giúp bạn chống lại các cuộc tấn công SQL injection tốt hơn.

**9. Not normalizing enough**

[Database normalization](http://en.wikipedia.org/wiki/Database_normalization) is basically the process of optimizing database design or how you organize your data into tables.

Just this week I ran across some code where someone had imploded an array and inserted it into a single field in a database. Normalizing that would be to treat element of that array as a separate row in a child table (ie a one-to-many relationship).

This also came up in [Best method for storing a list of user IDs](https://stackoverflow.com/questions/620645/best-method-for-storing-a-list-of-user-ids):

> I've seen in other systems that the list is stored in a serialized PHP array.

But lack of normalization comes in many forms.

More:

- [Normalization: How far is far enough?](http://www.techrepublic.com/article/normalization-how-far-is-far-enough/)
- [SQL by Design: Why You Need Database Normalization ](http://www.sqlmag.com/Article/ArticleID/4887/sql_server_4887.html)

**10. Normalizing too much**

This may seem like a contradiction to the previous point but normalization, like many things, is a tool. It is a means to an end and not an end in and of itself. I think many developers forget this and start treating a "means" as an "end". Unit testing is a prime example of this.

I once worked on a system that had a huge hierarchy for clients that went something like:

Licensee -&gt;  Dealer Group -&gt; Company -&gt; Practice -&gt; ...

such that you had to join about 11 tables together before you could get any meaningful data. It was a good example of normalization taken too far.

More to the point, careful and considered denormalization can have huge performance benefits but you have to be really careful when doing this.

More:

- [Why too much Database Normalization can be a Bad Thing](http://www.selikoff.net/blog/2008/11/19/why-too-much-database-normalization-can-be-a-bad-thing/)
- [How far to take normalization in database design?](https://stackoverflow.com/questions/496508/how-far-to-take-normalization-in-database-design)
- [When Not to Normalize your SQL Database](http://www.25hoursaday.com/weblog/CommentView.aspx?guid=cc0e740c-a828-4b9d-b244-4ee96e2fad4b)
- [Maybe Normalizing Isn't Normal](http://www.codinghorror.com/blog/archives/001152.html)
- [The Mother of All Database Normalization Debates on Coding Horror](http://highscalability.com/mother-all-database-normalization-debates-coding-horror)

**11. Using exclusive arcs**

An exclusive arc is a common mistake where a table is created with two or more foreign keys where one and only one of them can be non-null.  **Big mistake.** For one thing it becomes that much harder to maintain data integrity. After all, even with referential integrity, nothing is preventing two or more of these foreign keys from being set (complex check constraints notwithstanding).

From [A Practical Guide to Relational Database Design](http://books.google.com.au/books?id=7ZAk0YiKQV0C&pg=PA110&lpg=PA110&dq=%22exclusive+arc%22+database&source=bl&ots=AyNPWsac__&sig=gBFIerXckQlVpRdd6ycI5JEgq3U&hl=en&ei=PzGzSZfrFcPVkAWWyZDZBA&sa=X&oi=book_result&resnum=1&ct=result):

> We have strongly advised against exclusive arc construction wherever possible, for the good reason that they can be awkward to write code and pose more maintenance difficulties.

**12. Not doing performance analysis on queries at all**

Pragmatism reigns supreme, particularly in the database world. If you're sticking to principles to the point that they've become a dogma then you've quite probably made mistakes. Take the example of the aggregate queries from above. The aggregate version might look "nice" but its performance is woeful. A performance comparison should've ended the debate (but it didn't) but more to the point: spouting such ill-informed views in the first place is ignorant, even dangerous.

**13. Over-reliance on UNION ALL and particularly UNION constructs**

A UNION in SQL terms merely concatenates congruent data sets, meaning they have the same type and number of columns. The difference between them is that UNION ALL is a simple concatenation and should be preferred wherever possible whereas a UNION will implicitly do a DISTINCT to remove duplicate tuples.

UNIONs, like DISTINCT, have their place. There are valid applications. But if you find yourself doing a lot of them, particularly in subqueries, then you're probably doing something wrong. That might be a case of poor query construction or a poorly designed data model forcing you to do such things.

UNIONs, particularly when used in joins or dependent subqueries, can cripple a database. Try to avoid them whenever possible.

**14. Using OR conditions in queries**

This might seem harmless. After all, ANDs are OK. OR should be OK too right? Wrong. Basically an AND condition **restricts** the data set whereas an OR condition **grows** it but not in a way that lends itself to optimisation. Particularly when the different OR conditions might intersect thus forcing the optimizer to effectively to a DISTINCT operation on the result.

Bad:

... WHERE a = 2 OR a = 5 OR a = 11

Better:

... WHERE a IN (2, 5, 11)

Now your SQL optimizer may effectively turn the first query into the second. But it might not. Just don't do it.

**15. Not designing their data model to lend itself to high-performing solutions**

This is a hard point to quantify. It is typically observed by its effect. If you find yourself writing gnarly queries for relatively simple tasks or that queries for finding out relatively straightforward information are not efficient, then you probably have a poor data model.

In some ways this point summarizes all the earlier ones but it's more of a cautionary tale that doing things like query optimisation is often done first when it should be done second. First and foremost you should ensure you have a good data model before trying to optimize the performance. As Knuth said:

> Premature optimization is the root of all evil

**16. Incorrect use of Database Transactions**

All data changes for a specific process should be atomic. I.e. If the operation succeeds, it does so fully. If it fails, the data is left unchanged. - There should be no possibility of 'half-done' changes.

Ideally, the simplest way to achieve this is that the entire system design should strive to support all data changes through single INSERT/UPDATE/DELETE statements. In this case, no special transaction handling is needed, as your database engine should do so automatically.

However, if any processes do require multiple statements be performed as a unit to keep the data in a consistent state, then appropriate Transaction Control is necessary.

- Begin a Transaction before the first statement.
- Commit the Transaction after the last statement.
- On any error, Rollback the Transaction. And very NB! Don't forget to skip/abort all statements that follow after the error.

Also recommended to pay careful attention to the subtelties of how your database connectivity layer, and database engine interact in this regard. 

**17. Not understanding the 'set-based' paradigm**

The SQL language follows a specific paradigm suited to specific kinds of problems. Various vendor-specific extensions notwithstanding, the language struggles to deal with problems that are trivial in langues like Java, C#, Delphi etc.

This lack of understanding manifests itself in a few ways.

- Inappropriately imposing too much procedural or imperative logic on the databse.
- Inappropriate or excessive use of cursors. Especially when a single query would suffice.
- Incorrectly assuming that triggers fire once per row affected in multi-row updates.

Determine clear division of responsibility, and strive to use the appropriate tool to solve each problem.