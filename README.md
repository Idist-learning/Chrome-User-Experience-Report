
[Source](https://developers.google.com/web/tools/chrome-user-experience-report/ "Permalink to Chrome User Experience Report  |  Tools for Web Developers  |  Google Developers")

# Chrome User Experience Report  |  Tools for Web Developers  |  Google Developers
# Báo cáo về trải nghiệm người dùng | Các công cụ cho các web developer | Google Developer
![][1]

Chrome User Experience Report cung cấp các số liệu từ trải nghiệm người dùng đến cách mà người dùng Chrome trải nghiệm trong thế giới thực với các địa điểm cụ thể.

## Methodology
## Các phương pháp luận

Chrome User Experience Report được hỗ trợ đo đạc các chỉ số về trải nghiệm người dùng trên chính các web công cộng, được tổng hợp từ những người dùng được chọn tham gia đồng bộ hoá lịch sử trình duyệt của họ, không thiết lập mật khẩu cho đồng bộ hoá, và bật tính năng [báo cáo thống kê sử dụng][2]. Dữ liệu về kết quả được thông qua:

1. [PageSpeed Insights][3] cung cấp các chỉ số về trải nghiệm người dùng của mỗi mức URL đối với các URL phổ phiến mà công cụ crawler các web của Google biết.
2. [Dự án cộng đồng Google BigQuery][4] tổng hợp các chỉ số về trải nghiệm của người dùng theo nguồn gốc, áp dụng với mọi nguồn gốc mà trình thu thập dữ liệu của Google biết được và chia nhỏ dữ liệu theo những mục được nêu dưới đây:

### Metrics
### Các chỉ số

Các chỉ số được cung cấp bởi Chrome User Experience Report một cách công khai, lưu trữ trên Google BigQuery được cung cấp dựa trên các nền tảng web thông qua API được hiển thị trên các trình duyệt hiện đại, và tổng hợp theo các phân bố ban đầu. Chủ sở hữu trang wbe muốn phân tích chi tiết hơn (phân tích theo URL) và hiểu rõ hơn về hiệu suất trang web của họ và có thể sử dụng cùng 1 API để thu thập dữ liệu phục vụ việc đo lường chi tiết trong thực tế (RUM) về dữ liệu gốc của họ.

**Lưu ý:** Hiện tại, Chrome User Experience Report tập trung vào hiệu suất tải trang. Theo thời gian, chúng tôi hy vọng sẽ thêm nhiều chỉ số và các thành phần mở rộng hơn, cả hai đều cung cấp thông tin chi tiết hơn về tải trang và [các yếu tố quan trọng khác ảnh hưởng nhiều nhất đến trải nghiệm người dùng] [5].

Để được hướng dẫn về số liệu nào cần theo dõi, tối ưu hóa và các phương pháp hay nhất về cách diễn giải dữ liệu được đo lường từ phía người dùng thực, hãy tham khảo tài liệu [tâm điểm hiệu suất người dùng] [5] của chúng tôi.

#### First Paint
#### Khung màn hình đầu tiên
Được xác định bởi [Paint Timing API][6] và [khả dụng trên Chrome M60+][7]:

> "First Paint báo cáo thời gian khi trình duyệt xuất hiện lần đầu tiên sau khi điều hướng. Điều này không bao gồm khung nền màn hình mặc định, nhưng bao gồm khung màn hình không mặc định. Đây là thời điểm quan trọng đầu tiên mà nhà phát triển quan tâm khi tải trang - khi trình duyệt bắt đầu hiển thị trang."

#### First Contentful Paint
#### Màn hình có nội dung đầu tiên
Được xác định bởi [Paint Timing API][8] và [khả dụng trên Chrome M60+][7]:

> "First Contentful Paint báo cáo thời gian khi trình duyệt hiển thị bất kỳ văn bản, hình ảnh nào (bao gồm hình nền), canvas không phải màu trắng hoặc SVG. Điều này bao gồm văn bản có webfonts đang chờ xử lý. Đây là lần đầu tiên người dùng có thể bắt đầu sử dụng nội dung trang".

#### DOMContentLoaded
#### DOMContentLoaded

Được định nghĩa bởi [HTML specification][9]:

> "DOMContentLoaded báo cáo thời gian khi tài liệu HTML ban đầu đã được tải và phân tích cú pháp hoàn thiện, mà không cần đợi bảng định kiểu, hình ảnh và các frame phụ để kết thúc việc tải trang". - [MDN] [10].

#### onload
#### đang tải trang

Được định nghĩa bởi [HTML specification][11]:

> "Sự kiện tải được kích hoạt khi trang và các tài nguyên phụ thuộc của nó tải xong." - [MDN] [12].

### Dimensions
### Các biểu mẫu

Hiệu suất của nội dung web có thể thay đổi đáng kể dựa trên loại thiết bị, thuộc tính của mạng và các biến khác. Để giúp phân đoạn và hiểu trải nghiệm người dùng trên các phân đoạn chính như vậy, Chrome User Experience Report cung cấp các biểu mẫu sau.

#### Effective Connection Type
#### Loại kết nối hiệu quả

Được xác định bởi [API thông tin mạng] [13] và [có sẵn trong Chrome M62 +] [14]:

> "Cung cấp loại kết nối hiệu quả (" chậm-2g "," 2g "," 3g "," 4g "hoặc" ngoại tuyến ") được xác định theo giá trị vòng lặp và băng thông dựa trên các quan sát đo lường thực tế của người dùng."

#### Loại thiết bị

Phân loại thiết bị thô ("điện thoại", "máy tính bảng" hoặc "máy tính để bàn"), như [được liên lạc qua Tác nhân người dùng] [15].

#### Quốc gia

Vị trí địa lý của người dùng ở cấp quốc gia, được suy ra theo địa chỉ IP của họ. Các quốc gia được xác định theo [mã số ISO 3166-1 alpha-2 tương ứng] [16].

### Định dạng dữ liệu

Báo cáo được cung cấp qua [Google BigQuery] [17] dưới dạng tập hợp các tập dữ liệu chứa các chỉ số trải nghiệm người dùng được tổng hợp thành độ phân giải gốc. Mỗi tập dữ liệu đại diện cho một quốc gia duy nhất, `country_rs` nắm bắt dữ liệu trải nghiệm người dùng cho người dùng ở Serbia (` rs` là mã [ISO 31611-1] [16] cho Serbia). Ngoài ra, có một tập dữ liệu tổng hợp toàn cầu (`tất cả`) thu thập trải nghiệm trên toàn thế giới. Mỗi hàng trong tập dữ liệu chứa bản ghi trải nghiệm người dùng lồng nhau cho một nguồn gốc cụ thể, được chia cho các thứ nguyên chính.

| ----- |
| Dimension |  
| `origin` |  "https://example.com" |  
| `effective_connection_type.name` |  4G |  
| `form_factor.name` |  "phone" |  
| `first_paint.histogram.start` |  1000 |  
| `first_paint.histogram.end` |  1200 |  
| `first_paint.histogram.density` |  0.123 | 

Ví dụ: ở trên cho thấy một bản ghi mẫu từ Báo cáo trải nghiệm người dùng Chrome, cho biết rằng 12,3% tải trang có đo lường "lần sơn đầu tiên" trong khoảng 1000-1200 mili giây khi tải "http://example.com "trên thiết bị" điện thoại "qua kết nối giống như" 4G ". Để có được giá trị tích lũy của người dùng trải qua thời gian sơn đầu tiên dưới 1200 mili giây, bạn có thể thêm tất cả các bản ghi có giá trị "kết thúc" của biểu đồ nhỏ hơn hoặc bằng 1200.

**Lưu ý:** Báo cáo trải nghiệm người dùng Chrome không cung cấp giá trị định lượng (ví dụ: trung vị). Các giá trị như vậy có thể xấp xỉ từ dữ liệu được cung cấp, nhưng không được báo cáo tiếp xúc trực tiếp.

## Bắt đầu

Báo cáo trải nghiệm người dùng Chrome được cung cấp dưới dạng dự án công khai trên [Google BigQuery] [17]. Để truy cập dự án, bạn cần có tài khoản Google và Dự án Google Cloud: [tham khảo hướng dẫn từng bước của chúng tôi] [18] và [hướng dẫn về cách truy vấn dự án] [19].

## Mẹo phân tích và phương pháp hay nhất

### Xem xét sự khác biệt về dân số giữa các quốc gia sản xuất

Các số liệu được cung cấp bởi Báo cáo trải nghiệm người dùng Chrome được cung cấp bởi dữ liệu đo lường người dùng thực. Kết quả là, dữ liệu phản ánh cách người dùng thực sự trải nghiệm nguồn gốc truy cập và không giống như thử nghiệm tổng hợp hoặc địa phương nơi thử nghiệm được thực hiện trong điều kiện cố định và mô phỏng, nắm bắt đầy đủ các yếu tố bên ngoài hình thành và đóng góp cho trải nghiệm người dùng cuối cùng.

Ví dụ: sự khác biệt về dân số người dùng truy cập nguồn gốc cụ thể có thể đóng góp những khác biệt có ý nghĩa cho trải nghiệm người dùng. Nếu trang web thường xuyên được nhiều khách truy cập hơn với các thiết bị hiện đại hơn hoặc thông qua mạng nhanh hơn, kết quả có thể xuất hiện "nhanh" ngay cả khi trang web không được tối ưu hóa tốt. Ngược lại, một trang web được tối ưu hóa tốt thu hút một lượng người dùng rộng hơn hoặc dân số có số lượng người dùng lớn hơn trên các thiết bị hoặc mạng chậm hơn, có thể xuất hiện "chậm".

Khi thực hiện so sánh trực tiếp giữa các nguồn gốc, điều quan trọng là phải tính toán và kiểm soát sự khác biệt về dân số: phân đoạn theo thứ nguyên được cung cấp, chẳng hạn như loại thiết bị và loại kết nối và xem xét các yếu tố bên ngoài như quy mô dân số, quốc gia mà từ đó nguồn gốc được truy cập, v.v.

### Xem xét sự khác biệt về kích thước dân số trên nguồn gốc

Báo cáo trải nghiệm người dùng Chrome tổng hợp dữ liệu cho mỗi nguồn gốc, với các giá trị "mật độ" trên tất cả các biểu đồ thứ nguyên-số liệu tổng hợp với giá trị là "1.0". Điều này cung cấp thông tin chi tiết về phân phối trải nghiệm trên các thứ nguyên chính cho một nguồn gốc duy nhất.

Tuy nhiên, khi tổng hợp dữ liệu từ nhiều nguồn gốc, ví dụ trong ngành dọc hoặc khu vực địa lý, hãy cẩn thận với các loại kết luận được rút ra: việc tăng mật độ cho cùng một số liệu trên nhiều nguồn gốc không tính đến sự khác biệt về dân số tương đối trên nguồn gốc.

Ví dụ: trang web A có thể có mười triệu khách truy cập, trong khi trang web B có mười nghìn. Trong cả hai trường hợp, mật độ biểu đồ cho mỗi tổng nguồn gốc là "1.0" và tập dữ liệu không cung cấp bất kỳ số liệu tuyệt đối nào về quy mô dân số của nguồn gốc riêng lẻ hoặc sự khác biệt về kích thước dân số tương đối trên nguồn gốc. Kết quả là, nếu bạn cộng các mật độ từ A và B, và trung bình kết quả, bạn sẽ coi chúng là bằng nhau mặc dù A có ba đơn vị lưu lượng truy cập lớn hơn.

### Cân nhắc sự khác biệt về dân số của Chrome

Báo cáo trải nghiệm người dùng Chrome được hỗ trợ bởi đo lường người dùng thực được tổng hợp từ những người dùng Chrome đã chọn tham gia đồng bộ hóa lịch sử duyệt web của họ, chưa thiết lập cụm mật khẩu đồng bộ hóa và đã bật báo cáo thống kê sử dụng. Dân số này có thể không đại diện cho cơ sở người dùng rộng hơn cho một nguồn gốc cụ thể và nhiều nguồn gốc có thể có sự khác biệt về dân số giữa nhau. Hơn nữa, dữ liệu này không tính đến người dùng có trình duyệt khác nhau và sự khác biệt trong việc chấp nhận trình duyệt ở các khu vực địa lý khác nhau.

Do đó, hãy cẩn thận với các loại kết luận được rút ra khi nhìn vào mặt cắt ngang của nguồn gốc và khi so sánh nguồn gốc cá nhân: tránh sử dụng so sánh tuyệt đối và xem xét các yếu tố dân số khác được nêu trong các phần ở trên.

## Phản hồi và đề xuất

Chúng tôi muốn nghe phản hồi, câu hỏi và đề xuất của bạn để giúp chúng tôi cải thiện Báo cáo trải nghiệm người dùng Chrome. Vui lòng tham gia cuộc trò chuyện trên [Nhóm Google công khai] của chúng tôi] [20].

## Giấy phép

Bộ dữ liệu "Báo cáo trải nghiệm người dùng Chrome" của Google được cấp phép theo [Giấy phép quốc tế Creative Commons Attribution 4.0] [21].

[1]: https://developers.google.com/web/tools/chrome-user-experience-report/images/dataset.png
[2]: https://www.google.com/chrome/browser/privacy/whitepaper.html#usagestats
[3]: https://developers.google.com/speed/pagespeed/insights/
[4]: https://bigquery.cloud.google.com/dataset/chrome-ux-report:all
[5]: https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics
[6]: https://w3c.github.io/paint-timing/#first-paint
[7]: https://www.chromestatus.com/feature/5688621814251520
[8]: https://w3c.github.io/paint-timing/#first-contentful-paint
[9]: https://html.spec.whatwg.org/#event-domcontentloaded
[10]: https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded
[11]: https://html.spec.whatwg.org/#event-load
[12]: https://developer.mozilla.org/en-US/docs/Web/Events/load
[13]: https://wicg.github.io/netinfo/#dfn-effective-connection-types
[14]: https://www.chromestatus.com/feature/5108786398232576
[15]: https://developer.chrome.com/multidevice/user-agent
[16]: https://en.wikipedia.org/wiki/ISO_3166-1#Officially_assigned_code_elements
[17]: https://cloud.google.com/bigquery/
[18]: https://developers.google.com/web/tools/chrome-user-experience-report/getting-started#access-dataset
[19]: https://developers.google.com/web/tools/chrome-user-experience-report/getting-started#example-queries
[20]: https://groups.google.com/a/chromium.org/forum/#!forum/chrome-ux-report
[21]: https://creativecommons.org/licenses/by/4.0/

  
