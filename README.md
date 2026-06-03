# Báo cáo phân tích dữ liệu

## Dự đoán giao dịch thương mại điện tử bằng phân tích hành vi người tiêu dùng

## 1. Giới thiệu

Đề tài tập trung vào việc phân tích hành vi truy cập website thương mại điện tử và dự đoán khả năng khách hàng có phát sinh giao dịch mua hàng hay không.

Dataset được sử dụng là **Online Shoppers Purchasing Intention Dataset**, lấy từ Kaggle. Bộ dữ liệu này có nguồn gốc từ **UCI Machine Learning Repository**, gồm **12.330 phiên truy cập**, với biến mục tiêu là `Revenue`, cho biết phiên truy cập đó có kết thúc bằng giao dịch mua hàng hay không.

Theo mô tả của UCI, dữ liệu gồm các phiên truy cập trong vòng 1 năm nhằm hạn chế thiên lệch do chiến dịch, ngày đặc biệt, hồ sơ người dùng hoặc thời điểm cụ thể.

---

## 2. Mục tiêu nghiên cứu

### 2.1. Chủ đề phân tích

Báo cáo phân tích hành vi truy cập website thương mại điện tử nhằm dự đoán khả năng một phiên truy cập có phát sinh giao dịch mua hàng hay không.

Trong thương mại điện tử, không phải mọi khách truy cập website đều mua hàng. Vì vậy, việc nhận biết sớm nhóm khách hàng có khả năng mua giúp doanh nghiệp tối ưu hoạt động kinh doanh và nâng cao hiệu quả tiếp thị.

### 2.2. Lý do chọn đề tài

Việc dự đoán ý định mua hàng có ý nghĩa thực tiễn cao đối với các website bán hàng trực tuyến. Nếu nhận diện được nhóm khách hàng tiềm năng, doanh nghiệp có thể:

* Tối ưu chiến dịch marketing.
* Cá nhân hóa nội dung hiển thị.
* Gợi ý sản phẩm hoặc ưu đãi phù hợp.
* Tăng tỷ lệ chuyển đổi từ truy cập thành mua hàng.
* Giảm chi phí tiếp thị cho nhóm khách hàng ít tiềm năng.

### 2.3. Đối tượng phân tích

Đối tượng phân tích là **các phiên truy cập của người dùng trên website thương mại điện tử**.

Mỗi dòng dữ liệu tương ứng với một phiên truy cập, bao gồm các thông tin như:

* Số lượng trang người dùng đã xem.
* Thời gian ở lại từng loại trang.
* Tỷ lệ thoát trang.
* Giá trị trang.
* Tháng truy cập.
* Loại khách truy cập.
* Thiết bị, trình duyệt, khu vực và nguồn truy cập.
* Việc phiên truy cập có tạo ra doanh thu hay không.

### 2.4. Mục tiêu tổng quát

Mục tiêu tổng quát của báo cáo là phân tích các yếu tố ảnh hưởng đến hành vi mua hàng của khách truy cập website thương mại điện tử và xây dựng mô hình dự đoán khả năng phát sinh doanh thu từ một phiên truy cập.

### 2.5. Mục tiêu cụ thể

Báo cáo hướng đến các mục tiêu cụ thể sau:

* Khám phá cấu trúc và đặc điểm của bộ dữ liệu **Online Shoppers Purchasing Intention**.
* Phân tích tỷ lệ mua hàng và không mua hàng trong các phiên truy cập.
* Xác định các biến có ảnh hưởng lớn đến khả năng phát sinh doanh thu.
* Phân tích sự khác biệt về tỷ lệ mua hàng theo loại khách truy cập.
* Phân tích ảnh hưởng của thời điểm truy cập theo tháng đến khả năng mua hàng.
* Xây dựng và so sánh một số mô hình phân loại để dự đoán biến `Revenue`.
* Đề xuất ý nghĩa thực tiễn từ kết quả phân tích cho hoạt động kinh doanh thương mại điện tử.

---

## 3. Thông tin dataset

| Thông tin             | Mô tả                                        |
| --------------------- | -------------------------------------------- |
| Tên dataset           | Online Shoppers Purchasing Intention Dataset |
| Nguồn                 | Kaggle / UCI Machine Learning Repository     |
| Số dòng               | 12.330                                       |
| Số cột                | 18                                           |
| Số thuộc tính đầu vào | 17                                           |
| Biến mục tiêu         | Revenue                                      |
| Kiểu bài toán         | Phân loại nhị phân                           |

### 3.1. Biến mục tiêu

Biến mục tiêu của bài toán là `Revenue`.

Trong đó:

* `Revenue = True`: phiên truy cập có phát sinh giao dịch mua hàng.
* `Revenue = False`: phiên truy cập không phát sinh giao dịch mua hàng.

Khi đưa vào mô hình học máy, biến mục tiêu có thể được mã hóa thành:

* `0`: Không mua hàng.
* `1`: Có mua hàng.

### 3.2. Ý nghĩa dữ liệu

Mỗi dòng dữ liệu đại diện cho một phiên truy cập của người dùng trên website thương mại điện tử, không nhất thiết tương ứng với một khách hàng duy nhất.

Các thuộc tính trong dataset mô tả hành vi truy cập và bối cảnh truy cập của người dùng, ví dụ như thời gian xem trang, số lượng trang đã truy cập, tỷ lệ thoát, tháng truy cập, loại khách truy cập và nguồn truy cập.

---

## 4. Câu hỏi nghiên cứu

### 4.1. Câu hỏi nghiên cứu chính

> Liệu các đặc điểm hành vi trực tuyến và bối cảnh truy cập có thể dự báo chính xác khả năng khách hàng phát sinh giao dịch mua hàng hay không?

Đây là câu hỏi chính của bài toán vì mục tiêu cuối cùng là phân loại một phiên truy cập thành hai nhóm:

* Có mua hàng.
* Không mua hàng.

### 4.2. Câu hỏi nghiên cứu phụ

Để trả lời câu hỏi chính, báo cáo tập trung vào các câu hỏi phụ sau:

1. Tỷ lệ phiên truy cập có phát sinh doanh thu là bao nhiêu?
2. Những biến nào ảnh hưởng mạnh nhất đến khả năng mua hàng?
3. Khách truy cập mới và khách truy cập quay lại có sự khác biệt về tỷ lệ mua hàng không?
4. Thời điểm truy cập theo tháng có ảnh hưởng đến khả năng mua hàng không?
5. Các chỉ số hành vi như `PageValues`, `BounceRates`, `ExitRates` và `ProductRelated_Duration` ảnh hưởng như thế nào đến khả năng mua hàng?
6. Mô hình học máy nào cho kết quả dự đoán tốt nhất trên dataset này?

---

## 5. Kiểu bài toán

Đây là bài toán **phân loại nhị phân**.

Biến mục tiêu là `Revenue`, gồm hai nhãn:

| Nhãn | Ý nghĩa        |
| ---- | -------------- |
| 0    | Không mua hàng |
| 1    | Có mua hàng    |

Mục tiêu của mô hình là học từ các đặc điểm hành vi trực tuyến và bối cảnh truy cập để dự đoán một phiên truy cập có khả năng phát sinh giao dịch mua hàng hay không.

---

## 6. Ý nghĩa bài toán

Nếu mô hình dự đoán tốt, doanh nghiệp có thể xác định sớm nhóm khách hàng tiềm năng để áp dụng các chiến lược phù hợp, chẳng hạn như:

* Hiển thị mã giảm giá cho khách hàng có khả năng mua cao.
* Gợi ý sản phẩm phù hợp với hành vi truy cập.
* Gửi thông báo nhắc mua hàng.
* Tối ưu giao diện các trang có tỷ lệ chuyển đổi cao.
* Giảm tỷ lệ thoát trang.
* Tập trung ngân sách marketing vào nhóm khách hàng có tiềm năng chuyển đổi.

---

## 7. Phương pháp thực hiện

Quy trình phân tích dữ liệu gồm các bước chính:

### 7.1. Thu thập dữ liệu

Dataset được lấy từ Kaggle và có nguồn gốc từ UCI Machine Learning Repository.

### 7.2. Tiền xử lý dữ liệu

Các bước tiền xử lý bao gồm:

* Kiểm tra dữ liệu thiếu.
* Kiểm tra kiểu dữ liệu của các cột.
* Mã hóa các biến phân loại nếu cần.
* Chuyển đổi biến mục tiêu `Revenue` sang dạng nhãn số.
* Chia dữ liệu thành tập huấn luyện và tập kiểm tra.

### 7.3. Phân tích khám phá dữ liệu

Báo cáo tiến hành phân tích các yếu tố ảnh hưởng đến hành vi mua hàng, bao gồm:

* Tỷ lệ mua hàng và không mua hàng.
* Mối quan hệ giữa `PageValues` và `Revenue`.
* Ảnh hưởng của `BounceRates` và `ExitRates`.
* Sự khác biệt giữa `New Visitor` và `Returning Visitor`.
* Ảnh hưởng của tháng truy cập đến tỷ lệ mua hàng.
* Mối liên hệ giữa thời gian xem trang sản phẩm và khả năng mua hàng.

### 7.4. Xây dựng mô hình học máy

Một số mô hình phân loại được sử dụng để dự đoán biến `Revenue`, bao gồm:

* Logistic Regression
* Decision Tree
* Random Forest
* Gradient Boosting

### 7.5. Đánh giá mô hình

Các mô hình được đánh giá bằng các chỉ số:

* Accuracy
* Precision
* Recall
* F1-score
* AUC
* Confusion Matrix

Do dữ liệu có sự mất cân bằng giữa nhóm mua hàng và không mua hàng, báo cáo ưu tiên đánh giá thêm `Recall` và `F1-score` của nhãn `Revenue = 1`.

---

## 8. Kết quả kỳ vọng

Thông qua quá trình phân tích và xây dựng mô hình, báo cáo kỳ vọng:

* Xác định được các yếu tố ảnh hưởng mạnh đến khả năng mua hàng.
* Làm rõ sự khác biệt giữa các nhóm khách truy cập.
* Đánh giá được ảnh hưởng của yếu tố thời gian đến hành vi mua hàng.
* Chọn được mô hình học máy phù hợp nhất cho bài toán dự đoán `Revenue`.
* Đưa ra các đề xuất thực tiễn cho doanh nghiệp thương mại điện tử.

---

## 9. Kết luận

Bài toán dự đoán giao dịch thương mại điện tử bằng phân tích hành vi người tiêu dùng là một bài toán có ý nghĩa thực tiễn cao.

Thông qua việc phân tích các phiên truy cập website, doanh nghiệp có thể hiểu rõ hơn hành vi của khách hàng, nhận diện các yếu tố ảnh hưởng đến khả năng mua hàng và sử dụng mô hình học máy để dự đoán sớm nhóm khách hàng tiềm năng.

Kết quả của báo cáo có thể hỗ trợ doanh nghiệp tối ưu chiến dịch marketing, cải thiện trải nghiệm người dùng và tăng tỷ lệ chuyển đổi trên website thương mại điện tử.

---

## 10. Thành viên thực hiện

| Mã sinh viên | Họ và tên         |
| ------------ | ----------------- |
| 24021549     | Doãn Duy Lợi      |
| 24021629     | Nguyễn Phúc Thành |
| 24021605     | Nguyễn Minh Quân  |

---

## 11. Tài liệu tham khảo

* Kaggle: Online Shoppers Purchasing Intention Dataset
* UCI Machine Learning Repository: Online Shoppers Purchasing Intention Dataset
* Báo cáo và slide phân tích dữ liệu của nhóm
