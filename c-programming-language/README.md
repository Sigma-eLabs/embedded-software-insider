# :rocket: C Programming Language - Ngôn ngữ lập trình C :rocket:
<p align="center">
  <a href="./README.md" title="C programming language">
    <img src="/assests/images/clanguage/clanguage.png" title="C programming language" style="width: 20vw; min-width: 200px"/>
  </a>
</p>

***

## Giới thiệu :microphone:
Bài hôm nay mình sẽ nói về một chủ đề cơ bản nhất, nhưng cũng là một trong những chủ đề quan trọng nhất, đóng vài trò nền tảng để có thể làm việc với hệ thống nhúng.\
Đó là Ngôn ngữ lập trình C.\
*Lưu ý: Các bài viết mình cố gắng việt hóa các thuật ngữ nhưng có thể không đúng/sát nghĩa. Các bạn nên tham khảo các nguồn tại liệu tiếng Anh.*

## Vậy tại sao phải là ngôn ngữ C? :question:
Theo như cuộc khảo sát được thực hiện bởi [2024 survey by Statista](https://www.statista.com/statistics/793628/worldwide-developer-survey-most-used-languages/) với đối tượng là các kỹ sư phần mềm, thì 20.3% trong số họ sử dụng ngôn ngữ lập trình C.\
Thêm nữa, theo như bản xếp hạng [TIOBE Index for November 2024](https://www.tiobe.com/tiobe-index/) thì ngôn ngữ C vẫn được xếp thứ hạng cap (thời điểm viết bài này thì C đang ở thứ #4).\
Vậy lý do tại sao ngôn ngữ lập trình C lại được sử dụng rộng rãi, đắc biệt là trong hệ thống điều khiển nhúng? Có rất nhiều lý do, nhưng có thể nhấn mạnh về:
* Efficiency\
  Ngôn ngữ C là ngôn ngữ thân thiện với hardware (1 thành phần không thể thiếu của hệ thống nhúng). Có nghĩa là chương trình C thực thi hiệu quả hơn ngôn ngữ khác về mặt thời gian thực thi và đáp ứng nhanh hơn (ít mã lệnh, bỏ qua các bước exception check), sử dụng ít tài nguyên hơn (ROM, RAM), tiêu thụ năng lượng ít hơn.\
  Đặc biệt, ngôn ngữ C mang tính ứng dụng cao đối với những chương trình điều khiển đòi hỏi độ chính xác, an toàn cao thì xử lý nhanh và chính xác trong vòng vài milisecond là yêu cầu bắt buộc..
* Pointer & Assembly support\
  Khi làm việc với vi điều khiển, thì việc đọc và ghi thanh ghi hoặc vùng nhớ là những tác vụ cơ bản nhất. Với C, chúng ta có thể làm điều đó vô cùng dễ dàng.\
  Mặc khác, việc hỗ trợ ngôn ngữ cấp thấp như Assembly, giúp chương trình có thể can thiệp sâu hơn xuống phần hardware, thanh ghi của hệ thống nhúng.
* Control over hardware\
  C có khả năng điều khiển hardware ở mức độ mà đối với ngôn ngữ khác là điều không thể. Đó là hệ quả từ ưu điểm ở trên.

## Đặc điểm của ngôn ngữ C :pencil2:
* Là ngôn ngữ lập trình hướng cấu trúc, ngôn ngữ cấp cao
* Thân thiện với máy tính/hardware: khả năng tương thích cao khi làm việc với vùng địa chỉ, thanh ghi và ngoại vi của vi điều khiển
* Tương đối khó để học: cú pháp sử dụng hay debug lúc bị lỗilúc runtime (runtime error)
* Không hỗ trợ việc phát hiện lỗi exception (lúc runtime) như các ngôn ngữ khác

## Cấu trúc chương trình C :wrench:
* File extension:
  * Source file: *.c
  * Header file: *.h
* Một chương trình C cơ bản:
  ```c
  #include <stdio.h>

  int main() 
  {
    printf("Hello World!");

    return 0;
  }
  ```
* Một số thành phần chính:
  * #include <stdio.h>: với từ khóa #include, ta có thể sử dụng thư viện chuẩn <stdio.h> được xây dựng bởi các nhà phát triển
  * main: main luôn là tên chương trình chính
  * printf("Hello World!"): một câu lệnh C
 
* Ngoài ra, chương trình C còn có thêm một số thành phần khác như:
  * Function: hàm
  * Variable: biến chứa giá trị dữ liệu
  * Constant: hằng số không thay đổi giá trị theo thời gian
  * Macro
  * Predefined statements

* Công việc của người kỹ sư là làm sao thiết kế các câu lệnh, hàm, biến làm việc với nhau để một chương trình thực thi tốt những tác vụ được yêu cầu.

## Biên dịch chương trình và chạy chương trình :hammer:
* Dĩ nhiên, việc đọc hiểu một chương trình C đó đang làm gì là điều khả dĩ nếu bạn có đủ kiến thức và kinh nghiệm, bởi vì ngôn ngữ C là ngôn ngữ lập trình cấp cao và có những keywork, statements được xây dựng dựa trên tiếng Anh.
* Tuy nhiên, máy tính hày vi điều khiển không thể hiểu được chương trình C được viết để thực hiện các tác vụ. Vì vậy, chúng ta cần một công cụ hỗ trợ thể biên dịch ngôn ngữ C sang "ngôn ngữ máy" mà hệ thống máy tính, công cụ đó được gọi là Complier.
* Compiler có nhiệm vụ biên dịch chương trình C thành một file thực thi (định dạng *.exe, *.hex, ...). Khi file thực thi này được gọi, hay được nhúng vào hệ thống nhúng thì máy tính/hệ thống nhúng có để đọc hiểu được và thược hiện tác vụ theo yêu cầu.
* Một lưu ý nữa, tùy theo target device, mà kiến trúc vi xử lý, vi điều khiển khác nhau (Intel, Apple Silicon, Arm,...), do đó sẽ có những Complier tương ứng. Đây cũng là một điểm hạn chế của ngôn ngữ C. Khi chúng ta port chương trình C qua dòng kiến trúc chip khác thì bắt buộc phải biên dịch lại chương trình để có được file thực thi phù hợp với dòng chip đó.

## Học ngôn ngữ C từ nguồn nào? :mortar_board:
* Các trường đại học, cao đẳng là nơi đạo tạo đầy đủ và bài bản kiến thức lập trình ngôn ngữ C.
* Không thể không kể đến internet - mảnh đất màu mỡ chứa vô số tài liệu hay về ngôn ngữ lập trình C.
* Các khóa học lập trình cơ bản và nâng cao ở các trung tâm đào tạo.

## Kết luận :dart: 
* Hy vọng những tóm tắt ở trên có thể cho các bạn một số kiến thức tổng quan về ngôn ngữ lập trình C. Tuy nhiên, hiểu biết của mình còn hạn chế và quá trình tổng hợp còn rời rạc và thiếu sót.
* Lời khuyên chân thành là các bạn nên dành thời gian tìm hiểu thêm trên internet, hay học hỏi từ bạn bè và các anh chị có kinh nghiệm trong lĩnh vực.
* Ngoài ra, nắm vững ngôn ngữ C là chưa đủ. Các bạn cần phải trang bị những kiến thức liên quan đến vi điều khiển, phần cứng, cơ cấu chấp hành,... để có thể làm việc tốt với hệ thống nhúng.

## [Danh sách bài viết liên quan](/posts/) :link:

# Contact & Discussion
Vui lòng liên hệ [Sigma eLabs](https://github.com/Sigma-eLabs) qua email: [Ho Thien Ai](mailto:thienaiho95@gmail.com) để đóng góp ý kiến và trao đổi. Mình rất trân trọng và chân thành cảm ơn!
