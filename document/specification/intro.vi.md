Tìm hiểu về định dạng Portable Document (PDF)

Lời nói đầu: Tôi muốn thừa nhận rằng bài viết này đã được viết với tài liệu tham khảo đầy đủ để http://www.adobe.com/devnet/acrobat/pdfs/PDF32000_2008.pdf . Hầu hết tất cả những gì tôi đã học được về các file PDF từ các tài liệu tham khảo ở trên. Nếu bạn đang thực sự quan tâm dành thời gian để đọc nó. Đáng ngạc nhiên, nó rất dễ dàng và thú vị để đọc! Tôi viết bài hướng dẫn này ra khỏi quan tâm của tôi khi biết đặc tả PDF. Nhiệm vụ của tôi bắt đầu khi tôi cố gắng hết sức nhưng thất bại trong việc trích xuất văn bản từ một tập tin PDF đơn giản mà chứa một trang duy nhất của văn bản. Xin vui lòng cho tôi biết ( steve@printmyfolders.com ) Nếu bạn tìm thấy bất kỳ lỗi nào. Tôi đã dựa vào các đặc điểm kỹ thuật PDF (liên kết trên trang đầu) để tạo hướng dẫn này. Hướng dẫn này bao gồm tập tin PDF phù hợp với đặc điểm kỹ thuật ISO 32.000-1 (Trang vi đến viii trong PDF32000_2008.pdf cung cấp thêm thông tin về vấn đề này).
 

Hãy tưởng tượng bạn đang một mình trên một hòn đảo không có internet, không có phương tiện truyền thông ngoài một chiếc điện thoại mà bạn chỉ có thể thực hiện cuộc gọi bằng giọng nói. Ngoài ra, bạn có tất cả nhu cầu của bạn gặp - bạn có một ngôi nhà để ở lại, bạn có đủ thức ăn để ăn và bạn cảm thấy thoải mái. Một chiếc máy bay sẽ đến trong thời gian một tuần để đưa bạn về nhà. Đột nhiên, bạn nên nhớ rằng một tài liệu quan trọng, hiện tại với bạn phải được gửi đến một máy in trong thời gian một ngày. Đó là một lời mời một trang đơn giản chỉ chứa văn bản. Làm thế nào bạn sẽ giao tiếp thông tin này đến máy in của bạn?

Dưới đây là một cách để làm việc đó. Bạn sẽ lấy một người cai trị, đo chiều rộng và chiều cao của trang của bạn và lưu ý nó xuống. Bạn sẽ đo vị trí chính xác nơi mỗi dòng bắt đầu. Bạn sẽ ghi lại các font chữ, kích thước và màu sắc của tất cả các văn bản của bạn. Sau đó bạn sẽ gọi cho máy in của bạn và cho cô ấy tất cả những chi tiết này. Miễn là bạn đã có đủ thông tin chi tiết của mình, cô sẽ có thể sao chép tài liệu của bạn chính xác như nó được.

PDF làm việc trong một cách tương tự. Chúng tôi cung cấp hướng dẫn do đó, các ứng dụng xem PDF như Adobe Reader có thể hiểu được các hướng dẫn của chúng tôi và hiển thị cách chúng ta muốn nó. Tất nhiên, có quá nhiều điều để PDF hơn thế. Thay vì nói chuyện với một người, chúng ta đang hướng dẫn một phần mềm. Vì vậy, chúng ta cần cấu trúc, và làm theo quy tắc cụ thể.

Giữ hình ảnh này trong tâm trí và nó sẽ giúp bạn hiểu rõ hơn.


tập tin PDF là thú vị. Nếu bạn đã mở một tập tin PDF trong một trình soạn thảo văn bản như Notepad, các nội dung có thể trông giống như rác và có lẽ không phải là rất thú vị. Nhưng nó sẽ có ý nghĩa nhiều hơn một chút khi bạn hiểu rằng các file PDF theo một khuôn mẫu quy định.
 
" Cốt lõi của PDF là một mô hình nâng cao hình ảnh bắt nguồn từ ngôn ngữ mô tả trang PostScript®. Đây PDF Imaging mẫu cho phép mô tả của văn bản và đồ họa một cách thiết bị độc lập và giải quyết độc lập. Để cải thiện hiệu suất để xem tương tác, PDF định nghĩa một định dạng cấu trúc nhiều hơn thế được sử dụng bởi hầu hết các chương trình ngôn ngữ PostScript. Không giống như Postscript, mà là một ngôn ngữ lập trình, PDF dựa trên một định dạng tập tin nhị phân có cấu trúc được tối ưu hóa cho hiệu suất cao trong xem tương tác. PDF cũng bao gồm các đối tượng, chẳng hạn như chú thích và các liên kết siêu văn bản, mà không phải là một phần của nội dung trang đó nhưng rất hữu ích cho việc xem tương tác và trao đổi tài liệu. "(trích dẫn từ trang vii của PDF32000_2008.pdf).
 
Các khối xây dựng cơ bản của một tập tin PDF là các đối tượng. Có tám loại đối tượng được sử dụng trong các tập tin PDF. Trước khi chúng ta nhìn vào họ, chúng tôi sẽ xem xét một thời gian ngắn tại bộ ký tự của các file PDF. Có 3 loại ký tự - trắng không gian, dấu phân cách và các nhân vật thường xuyên.
 
Nhân vật white-space: Null, tab ngang, thức ăn đường, thức ăn Mẫu, vận chuyển trở lại và Không gian. Mẹo: Nếu bạn cần phải nhớ chúng, hãy tưởng tượng nhìn thấy chúng trong chuỗi (trừ for null tất nhiên) được đánh máy trên một máy đánh chữ tưởng tượng. Ký tự trắng-không gian tên và các đối tượng khác tách rời nhau. Điều thú vị là, PDF đối xử với tất cả các ký tự trắng-không gian bên ngoài một bình luận, chuỗi hoặc dòng giống nhau. Bên ngoài một nhận xét, chuỗi hoặc dòng, PDF xem xét bất kỳ chuỗi liên tiếpký tự trắng-không gian như một ký tự. Điều này có nghĩa là bạn có thể có 5 ô trống nhưng trong thực tế nó được coi là một. Lưu ý rằng điều này không áp dụng đối với các ký tự trắng-không gian bên trong chuỗi, suối và ý kiến. Sự trở lại vận chuyển và thức ăn hàng được coi là dấu mốc end-of-line (EOL). đánh dấu EOL đóng một vai trò rất quan trọng trong việc thể hiện nơi một dòng mới bắt đầu. Vận chuyển trở lại ngay sau đó một thức ăn đường được coi là một dấu hiệu EOL.
 
Nhân vật delimiter: (,), <,>, [,], {,}, / và% (4 cặp và 2 duy nhất). Chúng được sử dụng trong các đối tượng, chúng tôi sẽ xem xét sau. Họ về cơ bản đóng vai trò như delimiters (đánh dấu ranh giới hay biên giới) cho các tổ chức. Mẹo: Nếu bạn cần phải nhớ chúng, hãy tưởng tượng những nhân vật này () là uốn cong <> và sau đó kéo dài [] và sau đó uốn cong lại {} và sau đó cuối cùng làm phẳng /%.
 
Nhân vật thường xuyên: Tất cả các nhân vật khác hơn trắng-không gian và nhân vật Delimiter kể cả những người mà không phải là một phần của bộ ký tự ASCII chuẩn . Xin vui lòng đọc các lưu ý dưới đây vì nó là rất quan trọng bạn hiểu điều này.

Một điều thú vị cần lưu ý là một PDF có thể bao gồm toàn bộ các ký tự ASCII chỉ hoặc có thể bao gồm các ký tự ASCII và dữ liệu nhị phân. Trong thuật ngữ đơn giản, nhân vật trong các tập tin ASCII chỉ sử dụng 7 trong số 8 bit trong một byte trong khi các nhân vật trong các tập tin nhị phân sử dụng tất cả 8 bit trong byte. Điều này cho phép một khả năng của 128 nhân vật độc đáo cho các tập tin ASCII và 256 nhân vật độc đáo cho các tập tin nhị phân. Hầu hết các tập tin PDF được mã hóa hoặc chứa hình ảnh sẽ có dữ liệu nhị phân (hình ảnh được biểu diễn ở dạng nhị phân). Tập tin PDF có chứa dữ liệu nhị phân bị hỏng khi thay đổi nội dung hoặc thậm chí mở ra và lưu trong soạn thảo văn bản thông thường như Notepad. Điều quan trọng là chúng ta hiểu sự khác biệt giữa ASCII và các tập tin nhị phân như các khu vực khác của đặc tả PDF lạc trên chúng. Dưới đây là một liên kết thú vị mà giải thích sự khác biệt giữa các tập tin nhị phân và ASCII. http://www.cs.umd.edu/class/spring2003/cmsc311/Notes/BitOp/asciiBin.html  

Bạn cũng có thể tự hỏi tại sao bạn không nhìn thấy bất kỳ văn bản (có thể được nhìn thấy khi mở bằng một reader) hoặc tương đương của nó khi mở một tập tin PDF trong một trình soạn thảo văn bản hoặc thậm chí biên tập nhị phân. Có thể có hai lý do. Lý do đầu tiên và phổ biến nhất là luồng nội dung (trong đó văn bản được lưu trữ / giữ) được mã hóa (chuyển / thay đổi) để tiết kiệm không gian. Đây là những gì xảy ra với hầu hết các lý do thứ hai files.The có thể là các tập tin PDF được mã hóa cố để giữ cho các văn bản an toàn.
 
Các đối tượng:

Dưới đây là các đối tượng mà tận dụng các ký tự, chúng tôi đã xem xét ở trên.

Mỗi đối tượng có một lớp học tương ứng trong PDFBox. Có một cái nhìn tại liên kết này https://pdfbox.apache.org/1.8/architecture.html dưới phần "Các COS Model"
 
1. Đối tượng Boolean: Các từ khóa đúng và sai . 
2. Đối tượng Numeric: Có hai loại; số nguyên & thực. Số nguyên là những con số mà không cần bất kỳ điểm thập phân và có thể có một + hoặc - biểu tượng trước nó. Ví dụ, số 10 số Bất động phải có một dấu thập phân. Ví dụ, 10.5, 0.0, 5,0, -1.0. Số thực không thể được thể hiện dưới dạng mũ. 

3. Chuỗi Đối tượng: Strings chứa các ký tự (có thể không nhân vật cũng). Chúng có thể là ký tự chữ trong ngoặc đơn hoặc thập lục phân dữ liệu bên trong dấu ngoặc nhọn. Chú ý rằng các dấu ngoặc đơn và góc ngoặc là ký tự dấu phân cách. 

(I love Java (and PDF))
Có những nhân vật thoát có thể được sử dụng. Hãy tham khảo các đặc điểm kỹ thuật PDF để biết thêm chi tiết. Chuỗi \ ddd nơi ddd là một mã ký tự bát phân có thể được sử dụng để đại diện cho nhân vật bên ngoài bộ ký tự ASCII in được. Hãy nhận biết rằng, một số các ký tự thoát, đặc biệt là những người khiến nhân vật bị di chuyển, ví dụ \ n (newline), không có bất kỳ hiệu ứng hình ảnh khi chúng tôi được gửi đến một chuỗi hiển thị bởi PDF. Bạn có thể thay thế một trong những nhân vật trong chuỗi Tôi đã sử dụng trong mẫu PDF  và nhận thấy có sự khác biệt.

Chúng tôi cũng có thể sử dụng ký tự bát phân (thường là để đại diện cho nhân vật bên ngoài có thể in ký tự ASCII) khi sử dụng dấu ngoặc đơn. Một nhân vật bát phân được biểu diễn trong các định dạng \ ddd. Trong ví dụ sau \ 052 đại diện * (dấu sao), một ký tự ASCII in.

(I love Java (and \052PDF))
Dưới đây là một ví dụ về một String đại diện với số thập lục phân. 

<48454C4C4F>
Mỗi cặp được thực hiện như là một giá trị. Trong ví dụ trên, giá trị thập lục phân 48 là số thập phân 72 là ASCII tương đương với H. Tương tự như vậy 45 là E, 4C là L và 4F là O. Chuỗi trên là tương tự như các chuỗi (Hello). Nếu chữ số thập lục phân cuối cùng là ngày của riêng mình (không có chữ số khác để thực hiện một cặp) một số không được gắn vào phần cuối.

<4845C>

sẽ được coi là

<4845C0>

4. Tên Objects: Tên bao gồm một chuỗi các ký tự (ngoại trừ null). Một dấu gạch chéo / phải được sử dụng để giới thiệu tên. Trong trường hợp thăng (#) là một phần của tên, sử dụng # tiếp theo là mã thập lục phân 23. Đại diện cho nhân vật sử dụng hệ thập lục phân của họ sử dụng giá trị # tiếp theo là giá trị thập lục phân. Tất cả các nhân vật mà không phải là nhân vật thường xuyên phải được đại diện bởi các # tiếp theo giá trị thập lục phân của họ. Vui lòng tham khảo thông số kỹ thuật PDF để biết thêm chi tiết.

/MyName represents MyName

/My#20Name represents My Name

/All#20#23Numbers represents All #Numbers


5. Mảng các đối tượng: Đây là những giống với mảng tìm thấy trong các ngôn ngữ máy tính nhưng khác biệt ở chỗ chúng có thể chứa các loại đối tượng khác nhau (bao gồm cả chuỗi, tên và thậm chí mảng khác). Mảng được đại diện trong dấu ngoặc vuông. Như bạn có thể thấy, các giá trị được tách bằng dấu cách.
 
[false 170 85.5 (Hello) /My#20Name]
 
Mảng là đơn chiều nhưng có thể bao gồm các mảng khác mà có thể giữ mảng mình.
 
6. Đối tượng điển: 
Đây là tương tự như một cuốn từ điển thực tế, nơi một mô tả sau một từ. Mô tả ở đây có thể là bất kỳ đối tượng (bao gồm cả từ điển khác) nhưng tên luôn luôn là một Tên đối tượng mà chúng ta vừa thảo luận. Chìa khóa (Name) là duy nhất (không thể có hai tên tương tự). Một từ điển được biểu diễn trong vòng << >>.

<< /Name (Steve)

/Age 99

/Address << /Number 1234

                /Street (Java Street)

                /Suburb (Java Town)

                /PostCode (4321)

>>

>> 


7. Suối Objects: Streams cũng tương tự như chuỗi trừ có thể có độ dài không giới hạn. Chúng thường được sử dụng để đại diện cho dữ liệu lớn mà không thể phù hợp với một String. Một hình ảnh, ví dụ, có thể được biểu diễn dưới dạng một dòng suối. Như bạn sẽ thấy sau này, nội dung của mỗi trang trong PDF được biểu diễn dưới dạng dòng một 'Nội dung'. Nó bao gồm một cuốn từ điển tiếp theo từ khoá 'dòng', xuống dòng, dữ liệu của dòng và từ khoá 'endstream'.
 
dictionary
stream

……….

endstream

Trong khi các dòng bao gồm các dữ liệu, từ điển chứa thông tin về các dòng riêng của mình. Dưới đây là các phím được phổ biến đối với hầu hết các từ điển suối. Trong số những chìa khóa bắt buộc duy nhất là chiều dài.
Chiều dài - nhập bắt buộc có chứa độ dài (số byte) của luồng. Một lỗi đã xảy ra nếu con suối có nhiều byte dữ liệu có độ dài nêu trong từ điển.

Lọc - Tên (s) của bộ lọc (s) được sử dụng để giải mã các dữ liệu trên suối. Có thể là một tên hoặc một mảng. Các bộ lọc được sử dụng theo trình tự cung cấp

DecodeParms - Từ điển Parameter được sử dụng bởi các bộ lọc. Có thể là một từ điển hoặc mảng. Thông số là những giá trị được sử dụng bởi các bộ lọc. Nếu bộ lọc sử dụng các thông số mặc định, nó có thể được bỏ qua.

F - Từ đặc điểm kỹ thuật PDF phiên bản 1.2, các nội dung dòng có thể được lưu trữ trong một tập tin bên ngoài. Điều này cho thấy các tập tin mà nó được lưu trữ. Trong trường hợp này các nội dung giữa dòng và endstream được bỏ qua.

FFilter - Tương tự như Lọc entry nhưng đối với tập tin bên ngoài của dòng.

FDecodeParms - Tương tự như DecodeParms nhưng đối với bộ lọc tập tin bên ngoài của luồng của

DL - Một kích thước gần đúng của các nội dung (sau khi giải mã) trong dòng. Điều này sẽ giúp xác định xem có đủ không gian đĩa cho suối.


8. đối tượng Null - Đề cập đến một đối tượng không tồn tại và biểu hiện bằng các từ khóa rỗng . 


Các thành phần khác của một tập tin PDF. 
Bình luận: Các bình luận được thể hiện bằng các dấu hiệu tỷ lệ phần trăm tức là%. Điều này thường được dùng để mô tả phiên bản của đặc tả PDF được sử dụng trong việc tạo ra các tập tin PDF.

%PDF-1.7
 
Đối tượng gián tiếp: 
Một đối tượng (ví dụ, một chuỗi) đã được đưa ra một nhận dạng đối tượng duy nhất, đó là các đối tượng khác có thể sử dụng để ám chỉ bản thân được gọi là một đối tượng gián tiếp. Đây là khác biệt so với ' Tên đối tượng' mà chúng ta đã xem xét trước đó. Nhìn vào bất kỳ tập tin PDF dưới dạng thô (ví dụ, bằng cách mở nó trong một trình soạn thảo văn bản), bạn sẽ thấy rất nhiều các đối tượng gián tiếp.
 
Từ định danh có hai phần. Phần thứ nhất là số đối tượng có thể được bất kỳ số nguyên dương. Phần thứ hai là số thế hệ mà luôn luôn là số không trong phiên bản đầu tiên không được cập nhật của tập tin PDF. Bạn khai báo một đối tượng gián tiếp trong các từ khóa 'obj' và 'endobj'. Hãy nhận biết rằng sự kết hợp của số đối tượng và hệ số phải là duy nhất. 

1 0 obj

(my biography)

endobj

Số đối tượng là 1 và số thế hệ là 0. Các đối tượng gián tiếp là đối tượng chuỗi (tiểu sử của tôi) .   Nếu đối tượng khác muốn tham khảo đối tượng này, nó sẽ đưa ra con số đối tượng, tiếp theo là không gian, số thế hệ, tiếp theo là không gian và sau đó R.

1 0 R
Nó không phải là một lỗi nếu một lần để đề cập đến một đối tượng gián tiếp không tồn tại.

Cấu trúc tập tin: Một tập tin PDF ban đầu sẽ có cấu trúc sau. Tuy nhiên, nếu tập tin được cập nhật hoặc thay đổi nội dung, các yếu tố bổ sung có thể được thêm vào cuối của tập tin.
 
1.       Một Header (không quá một dòng) cho thấy các đặc điểm kỹ PDF tập tin này sau.

2.       một tệp Body có các đối tượng của tập tin

3.       Một bảng Cross-tài liệu tham khảo có thông tin về các đối tượng gián tiếp

4.       Một Trailer cho thấy vị trí của bảng tham chiếu chéo và các đối tượng đặc biệt trong cơ thể của tập tin.



Nộp Tiêu đề: Điều này nói lên phiên bản đặc tả PDF của tập tin PDF. % PDF- tiếp theo phiên bản số 1.N, trong đó N là một chữ số từ 0 & 7.

%PDF-1.2
Như đã đề cập trước đó này thực sự là một lời nhận xét đó được sử dụng để xác định phiên bản PDF.

 
Bắt đầu với phiên bản 1.4 Danh mục từ điển của tài liệu được sử dụng thay vì điều này. Nếu tập tin có dữ liệu nhị phân, sẽ có ít nhất bốn ký tự nhị phân, ngay sau khi tiêu đề. Điều này là để hiển thị các ứng dụng PDF đọc (như Adobe reader) rằng PDF có dữ liệu nhị phân. Một lần nữa, khi mở một số tập tin PDF ở dạng raw (như trong một trình soạn thảo văn bản), bạn có thể nhận thấy bốn ký tự nhị phân ngay sau khi nhận xét đầu tiên.

Nộp Body: Thân tập tin bao gồm các đối tượng gián tiếp (được thảo luận trước đó). Những đối tượng đại diện cho văn bản và các chi tiết khác (như kiểu font, vv) được sử dụng trong việc hiển thị PDF.  Tính đến phiên bản 1.5, cơ thể cũng có thể chứa các dòng đối tượng. 

Cross-Reference Table: Bảng này cũng tương tự như một thư mục. Nó chứa các vị trí của từng đối tượng bên trong file PDF. Bằng cách nhìn vào các mục trong bảng này, ứng dụng PDF đọc (ví dụ, Adobe Reader), có thể dễ dàng xác định vị trí một đối tượng bên trong file. Điều này tiết kiệm thời gian khi đối tượng được truy cập một cách ngẫu nhiên (chứ không phải đọc mỗi dòng của tập tin). Bảng tham chiếu chéo có thể có một hoặc nhiều phần. Mỗi phần có thể có một hoặc nhiều phần phụ.

Lưu ý: Từ phiên bản PDF 1.5 trở đi các bảng tham chiếu chéo có thể được lưu trữ như một dòng suối và nếu như vậy bạn sẽ không thể để xem bảng như hình dưới đây khi mở với một trình soạn thảo văn bản.

Mỗi phần bắt đầu bằng từ ' xref . Sau dòng này là hai số cách nhau bởi một dấu cách trống. Con số đầu tiên là số đối tượng của đầu tiên của loạt của các đối tượng được liệt kê bên dưới nó. Số thứ hai đề cập đến số lượng các mục trong tiểu mục đó. Đối với một tập tin PDF đã được tạo ra lần đầu tiên hoặc một tập tin PDF mà chưa được cập nhật từng bước, có phải chỉ có một tiểu mục và đối tượng đánh số bắt đầu bằng 0. Chú ý rằng những con số đối tượng cần phải liên tục. Trong ví dụ dưới đây, nó là an toàn để giả định rằng mục cho đối tượng 1, 2, 3 & 4 sẽ làm theo. 

xref

0 5  

Sau này được các mục cho từng đối tượng. Mỗi mục sẽ được chính xác 20 byte dài. Các mục có định dạng các

nnnnnnnnnn ggggg meol
nnnnnnnnnn - Đây là một giá trị mười chữ số. Điều này cho thấy cách xa đối tượng là từ khi bắt đầu của tập tin. Ví dụ, giá trị 100 biểu thị rằng đối tượng là 100 byte từ khi bắt đầu của tập tin. 

ggggg - số thế hệ 5 chữ số

m - có thể là 'n' hoặc 'f'. 'n' biểu thị rằng đối tượng vẫn đang được sử dụng và 'f' biểu thị rằng đối tượng đã bị xóa và được miễn phí. 

eol - cuối dòng. Bao gồm 2 ký tự.

Mười chữ số, tiếp theo là không gian, tiếp theo là năm chữ số, tiếp theo là không gian, tiếp theo là một ký tự đơn và eol thực hiện chính xác 20 chữ số. Nếu hai số đầu tiên là không đủ dài, để được mười năm chữ số tương ứng, zero được thêm vào phía trước. 

Chúng ta hãy quay trở lại 0 5 mà chúng ta thấy trong ví dụ earlier.The 0 biểu thị số đối tượng của đối tượng đầu tiên trong tiểu mục này. Giá trị 5 biểu thị rằng có 5 mục (bao gồm cả một số 0) và bốn mục còn lại là các đối tượng với số lượng đối tượng 1, 2, 3 và 4. Các entry đầu tiên tại bảng tham chiếu chéo là dành cho đối tượng 0. Object 0 sẽ có 0000000000 như nó mười chữ số đầu tiên (nếu không có đối tượng miễn phí khác) và sẽ luôn luôn có 65535 là số thế hệ 5 chữ số của nó. Nó cũng sẽ có 'f' như nhân vật.  

xref

0 2
0000000000 65535 f
...........
 
Nếu có đối tượng (s) đã bị xóa và được tự do sau đó số mười chữ số sẽ được thay đổi để biểu thị n th xâm nhập của đối tượng miễn phí tiếp theo. Để làm cho nó dễ hiểu chúng ta hãy xem xét một ví dụ.

xref
0 4
0000000003 65535 f
0000000015 00000 n
0000000075 00000 n
0000000000 00005 f
  
0 4 biểu thị rằng có bốn mục - Entry for object 0 tiếp theo mục cho đối tượng 1, 2 & 3 . Mười chữ số đầu tiên ( 0000000003) của các mục nhập đầu tiên cho đối tượng 0 điểm cho các đối tượng miễn phí tiếp theo, đó là, đối tượng 3. Nếu đã có một đối tượng miễn phí, sau đó mục thứ 4 sẽ có số đối tượng của đối tượng miễn phí tiếp theo. Trong trường hợp này, vì không có đối tượng miễn phí khác nó trỏ lại phản đối 0. Đối tượng 1 & 2 là 15 & 75 byte (tương ứng) đi từ khi bắt đầu của tập tin. Này về cơ bản thông báo cho phép các ứng dụng PDF biết rằng đối tượng 3 là miễn phí và do đó nó có thể được sử dụng để tham khảo dữ liệu khác.
 
Hãy xem xét một ví dụ khác
  
xref
0 4
0000000003 65535 f
0000000015 00000 n
0000000075 00000 n
0000000000 00005 f
9 2
0000000099 00000 n
0000000150 00000 n
 
Trong trường hợp trên, ngoài các đối tượng 0, 1, 2, 3 có hai đối tượng khác 9 & 10.
 
Một đối tượng không thể được nhập vào nhiều hơn một tiểu mục trong vòng một phần.
 
Khi một đối tượng gián tiếp bị xóa, nhập cảnh của nó được đánh dấu là miễn phí (bằng cách thay đổi n f) và liên kết với danh sách liên kết của các đối tượng miễn phí. số thế hệ của nó được tăng 1. Số thế hệ của đối tượng được cập nhật mỗi khi đối tượng bị xóa và có thể đi tối đa tối đa là 65.535. Ví dụ, một đối tượng gián tiếp đã được tham chiếu như 1 0 sẽ trở thành 1 1 khi tái sử dụng.
 
Trailer: Sự kết thúc của một tập tin PDF được đọc đầu tiên của ứng dụng PDF đọc. Đoạn trailer chứa thông tin về vị trí và thông tin chi tiết của bảng chéo tham khảo. Đoạn trailer có ba phần. Phần đầu có từ khóa Trailer tiếp theo một cuốn từ điển chứa các giá trị cho các lĩnh vực nhất định.  
Phần thứ hai có từ khóa startxref , và các dòng tiếp theo, một số. Số biểu thị thế nào đến nay (tính theo byte) từ khóa xref (của phần cuối cùng của bảng tham chiếu chéo) là từ khi bắt đầu của tập tin. Điểm mấu hôm sau có EOF giá trị %% để biểu thị sự kết thúc của tập tin.  
Một PDF ngẫu nhiên lấy từ máy tính của tôi có trailer này. Nhìn vào trailer này tôi có thể giả định rằng xref của phần cuối cùng của bảng tham chiếu chéo được tìm thấy 361.441 byte từ đầu tập tin. 
 
trailer
<< /Size 62 /Root 1 0 R /Info 2 0 R
/ID [(X$X@>66...)(X$X@>66...)]
>>
startxref
361441
%%EOF
 
 Các phím sau đây là bắt buộc đối với các từ điển trailer.
 
Kích - Tổng số các mục trong bảng tham chiếu chéo (sự kết hợp của phần gốc & cập nhật). Giá trị phải là một số nguyên. Trong ví dụ trên có 62 mục trong đó có một mục nhập cho đối tượng 0.
 
Gốc - là một tham chiếu gián tiếp vào danh mục của PDF (mà chúng ta sẽ học sau). Trong ví dụ trên, tôi có thể giả định rằng đối tượng gián tiếp 1 là danh mục.
 
Một số phím là bắt buộc khi khả năng nhất định được sử dụng. Chúng tôi có thể nhìn vào Thông tin & ID phím sau. 
 
Incremental Cập nhật: Các nhóm phát triển đặc tả PDF là đủ thông minh để bao gồm một tính năng đặc biệt. Khi một tập tin PDF được cập nhật, những thay đổi được thêm vào cuối của tập tin chứ không phải là cập nhật các nội dung ban đầu. Tính năng này tiết kiệm thời gian (như toàn bộ tập tin không cần phải được sửa đổi). Tuy nhiên, điều này cũng làm cho tôi tự hỏi điều gì sẽ xảy ra khi có nhiều thay đổi diễn ra. Có kích thước của file PDF tăng ồ ạt?
 
Khi một tập tin PDF được một bản cập nhật gia tăng, ngoài các dữ liệu được bổ sung, một phần chéo tham chiếu mới được tạo ra. phần mới này chứa mục cho tất cả các đối tượng mà đã bị xóa, thay thế hoặc thay đổi. Như chúng ta đã học trước đây đối tượng bị xóa có chữ 'e' ở cuối mục tham chiếu chéo. Điều này có nghĩa rằng nếu nói đối tượng 5, tồn tại trước và đã bị xóa trong khi cập nhật mặt cắt mới sẽ có sự xâm nhập tương tự nhưng với 'f' là ký tự cuối cùng trong mục nhập cho đối tượng 5.
 
Khi các tập tin PDF được cập nhật, cùng với một phần tham chiếu chéo mới một trailer mới được thêm vào. Này chứa tất cả các mục từ trailer trước nhưng sẽ có một giá trị khác nhau cho các Prev mục trong từ điển. Các Trước entry sẽ có vị trí của mặt cắt ngang tham khảo trước.
 
%% EOF sẽ tiếp tục là dòng cuối cùng cho trailer mới là tốt. Hy vọng rằng chúng tôi sẽ thảo luận chi tiết sau.
 
PDF Document Cấu trúc:
Cấu trúc của một tập tin PDF cũng giống như các cấp độ khác nhau của hệ thống phân cấp được tìm thấy trong một công ty điển hình. Tương tự như các giám đốc điều hành, từ điển Document Catalogue nằm ở phía trên cùng của hệ thống phân cấp. Bạn thực sự có thể xem cấu trúc của một file PDF bằng cách sử dụng công cụ PDFDebugger - Tôi đã đưa thêm chi tiết tại trang web này http://www.printmyfolders.com/view-structure-of-a-pdf
 
Như chúng ta đã thấy ở trên một ứng dụng đọc PDF sẽ nhìn vào trailer của PDF đầu tiên. Đoạn trailer sẽ có một mục gốc có vị trí của các cửa hàng. Đây là tương tự như một người ( ứng dụng đọc PDF ) tiếp cận các Giám đốc điều hành ( Tài liệu Catalog ) sau khi tìm thấy chi tiết liên lạc của mình qua phần tiếp xúc ( Trailer ) trên website của công ty ( PDF file ).
 
Tài liệu Catalog: Các tài liệu Catalog là một cuốn từ điển đó đề cập đến các đối tượng khác để xác định các tập tin PDF. Về cơ bản, Catalog Tài liệu cũng giống như trung tâm từ nơi mà mọi thông tin về các tập tin PDF có thể được tìm thấy. Là một cuốn từ điển nó bao gồm các phím khác nhau. Chúng tôi sẽ lần là chỉ nhìn vào các phím bắt buộc.
 
 
Loại - sẽ luôn luôn được Catalog (loại Name)
Trang - Một tài liệu tham khảo gián tiếp đến đối tượng đó là gốc rễ của cây trang (sẽ xem xét sau này)
 
Một tập tin PDF mà tôi tạo ra bằng cách sử dụng PDF miễn phí tạo ra phần mềm có từ điển Catalogue này 
 
1 0 obj
<</Type /Catalog /Pages 3 0 R
>>
endobj
 
Bạn sẽ nhận thấy rằng mỗi người trong số các bộ từ điển luôn luôn bắt đầu với một '/ Loại' entry mà descirbes loại từ điển nó được. Trong trường hợp này, nó là một 'Catalogue' từ điển.
 
Đơn mà đọc trên từ điển Catolog sẽ biết rằng nó cần phải đọc từ điển 'Trang' (gián tiếp đối tượng 3) để có được thông tin về các trang trong file PDF này.
 
 
Trang Tree:   Trang Tree là tên của cấu trúc dùng để mô tả các trang trong một tập tin PDF. Nó có hai loại nút - trang nút cây và đối tượng trang. Mỗi trang trong một tập tin PDF được biểu diễn dưới dạng một đối tượng trang. Mỗi đối tượng được gọi là 'lá' nút trong trang Tree.
 
Trang Tree Nodes: Các phím bắt buộc là
 
Loại - sẽ luôn là trang cho một nút trang Tree
Mẹ - cây trang nút đó là cha mẹ của nút này. Không được phép vào nút gốc.
Kids - một mảng đề cập đến những đứa trẻ của nút này. Những đứa trẻ chỉ có thể là trang nút cây hoặc các vật trang
Đếm - số lượng đối tượng trang đó là hậu duệ của nút này
 
PDF mà tôi đã tạo ra trước đó có này cây trang (nhớ rằng Catalogue từ điển đã được trỏ đến đối tượng gián tiếp 3). 
 
3 0 obj
<< /Type /Pages /Kids [
4 0 R
] /Count 1
/Rotate 0>>
endobj
 
Nút trang của cây này chỉ có một đứa trẻ là đối tượng 4. Chánh chính là mất tích và do đó đây là nút gốc.
 
Là / Count là 1, chúng ta có thể yên tâm rằng chỉ có 1 trang dưới trang này cây (mà dựa trên các mảng / Kids là gián tiếp đối tượng 4.
 
Như menioned trước đó, bạn sẽ nhận thấy rằng từ điển này quá có một mục '/ Loại' mà tiết lộ những gì loại từ điển nó được.
 
Trang đối tượng : Đây là một cuốn từ điển đó cho thấy những đặc điểm trang riêng của mình. Một số trong những chìa khóa là
 
Lưu ý: Hầu hết các phím là mới với tôi. Tôi đã cố tình bỏ qua các phím mà làm cho không có ý nghĩa với tôi tại thời điểm này. Như tôi đã tìm hiểu thêm về thông số kỹ thuật PDF Tôi hy vọng sẽ giới thiệu một cách chi tiết.
 
Loại - Sẽ luôn trang
Mẹ - Một tài liệu tham khảo gián tiếp cho phụ huynh của trang này
LastModified - Ngày và thời gian khi trang này được sửa đổi lần cuối
Tài nguyên - Các nguồn lực cần thiết bởi trang này. Điều này thường đề cập đến các phông chữ được sử dụng trên trang này và thông tin khác.
MediaBox - Một hình chữ nhật xác định ranh giới bên trong mà trang phải được hiển thị.
Nội dung - Một dòng nội dung mô tả nội dung của trang này.
Xoay - Trong bội số của 90. Xoay trang bằng cách cho số của độ trước khi hiển thị.
Thumb - Một đối tượng dòng cung cấp cho hình ảnh thu nhỏ cho trang này.
Dur - số giây trang sẽ được hiển thị trong các bài thuyết trình trước khi tự động chuyển sang trang tiếp theo.
Trans - Một từ điển tham mưu gì chuyển đổi sang sử dụng khi hiển thị trang trong trình bày.
Annots - Đây là một loạt các từ điển có chứa tài liệu tham khảo cho tất cả các chú thích cho trang này
AA - Đây là hình thức ngắn để biết thêm hành động. Từ điển này quy định các hành động mà cần phải được thực hiện khi các tập tin được mở hoặc đóng cửa.
Metadata - Một dòng có chứa siêu dữ liệu cho trang này
  
Đây là một lấy từ một PDF mẫu mà tôi tạo ra bằng cách sử dụng PDF miễn phí tạo ra phần mềm.
 
 
4 0 obj
<</Type/Page/MediaBox [0 0 595 842]
/Rotate 0/Parent 3 0 R
/Resources<</ProcSet[/PDF /Text]
/ExtGState 10 0 R
/Font 11 0 R
>>
/Contents 5 0 R
>>
endobj
 
3 0 obj
<< /Type /Pages /Kids [
4 0 R
] /Count 1
/Rotate 0>>
endobj
 
1 0 obj
<</Type /Catalog /Pages 3 0 R
>>
endobj
 
Như bạn có thể thấy đối tượng 1 là các cửa hàng mà chỉ đạo các ứng dụng đọc PDF vào thư mục gốc của cây trang (Object 3). Đối tượng 3, nút gốc chỉ có một đứa trẻ (đối tượng 4) và rõ ràng là không thể có cha mẹ. Đối tượng 4 được 'trưng bày' trong một hình chữ nhật (0 0 595 842) và không xoay (Rotate 0) và đã Object 3 như mẹ của nó. Đó là 'tài nguyên' cũng như nội dung của nó (đối tượng 5) được bao gồm. Đây là đối tượng 5 từ tập tin của tôi.
 
Như chúng ta đã thảo luận trước đó, dòng trong đối tượng này bắt đầu với một cuốn từ điển cho thấy chiều dài của dòng (được lưu trữ trong Object 6). Chúng tôi sẽ thảo luận thêm về các dòng nội dung tiếp tục xuống.
 
5 0 obj
<</Length 6 0 R/Filter /FlateDecode>>
stream
xMK.1.鶵u*j.czi2& 7KnSK..Z?]."6.3w>^&s@MQ...K.d\>}q...    ).|.ѣ'o1lA.ۥ
S-lE,.C.W.&#xf01d2;YGKM\vjEG.'|F[j.:..2f2Ź^.uujNWǌY::si/.L9,ČGPY1k/.%'f!endstream
endobj
 
 Trang thuộc tính được thừa hưởng: Dưới đây là một thực tế thú vị. Một số thuộc tính trong một trang có thể được thừa hưởng từ cha mẹ của mình hoặc bất kỳ tổ tiên của nó trong cây trang. Các loại bỏ sự cần thiết phải tiếp tục lặp đi lặp lại các thuộc tính tương tự cho mọi trẻ em, cháu vv Nếu tổ tiên xác định một giá trị cho một thuộc tính, giá trị đó có thể được thay thế hoặc thay đổi bởi đứa trẻ.
 
Đặt tên cho từ điển: Thay vì đề cập đến các đối tượng bởi tài liệu tham khảo của họ, một số đối tượng có thể được gọi bằng tên của họ. Mối liên hệ giữa tên và tài liệu tham khảo của họ được lưu trữ trong tập tin PDF của từ điển tên . Một trong những chìa khóa tùy chọn trong Catalogue, tên được sử dụng để sử dụng để xác định các từ điển Name . Vui lòng tham khảo thông số kỹ thuật PDF để biết thêm chi tiết.
 
Nội dung Luồng: Đây là một dòng (một đối tượng trong PDF, nếu bạn nhớ) có hướng dẫn về việc làm thế nào để hiển thị văn bản và đồ họa trên các trang tương ứng. Trong Object 5, các tập tin PDF của tôi, đã đề cập trước và lặp đi lặp lại dưới đây chúng ta có thể nhìn thấy hình ảnh. Dòng này cung cấp cho người đọc PDF (ví dụ Adobe Reader) hướng dẫn về cách để hiển thị.

5 0 obj
<</Length 6 0 R/Filter /FlateDecode>>
stream
xMK.1.鶵u*j.czi2& 7KnSK..Z?]."6.3w>^&s@MQ...K.d\>}q...    ).|.ѣ'o1lA.ۥ
S-lE,.C.W.&#xf01d2;YGKM\vjEG.'|F[j.:..2f2Ź^.uujNWǌY::si/.L9,ČGPY1k/.%'f!endstream
endobj
 
Các dữ liệu trong dòng làm cho không có ý nghĩa bởi vì các dữ liệu đã được mã hóa (chuyển đổi từ hình thức ban đầu của nó khác). Trong phần tiếp theo chúng ta sẽ xem xét chi tiết hơn về cấu trúc của những dữ liệu này và hiểu cách chúng tạo hướng dẫn việc áp dụng PDF đọc để hiển thị trang.
 
Lưu ý rằng không giống như các đối tượng khác trong một tập tin PDF, các hướng dẫn trong dòng đối tượng được đọc và theo tuần tự (một sau khi khác).
 
Trước khi tiếp tục, chúng tôi sẽ cố gắng tạo ra một tập tin PDF đơn giản từ những gì chúng ta đã học được cho đến nay.
 
Mẫu tập tin PDF: Đây là một tập tin PDF mẫu mà tôi tạo ra với sự giúp đỡ từ các đặc điểm kỹ thuật. Bạn có thể sao chép tập tin này từ đây và lưu nó trong một trình soạn thảo văn bản như notepad. Lưu nó với một tên tập tin nhưng có phần mở rộng tập tin "pdf". Trong notepad, bạn sẽ phải save as "filename.pdf" (Báo giá đã bao gồm). Sau đó bạn có thể xem nó với một trình đọc PDF (ví dụ sử dụng Acrobat Reader). Lưu ý: Không phải tất cả các file PDF đơn giản như này. Tập tin PDF này có nghĩa là rất cơ bản và chỉ hiển thị một dòng văn bản.

Điều tiếp tục tại  Hiểu Portable Document Format (PDF): Phần 2
 
 
Tôi yêu những phản hồi và đề xuất của bạn. Hãy để lại nhận xét dưới đây hoặc liên hệ với tôi tại  steve@printmyfolders.com.