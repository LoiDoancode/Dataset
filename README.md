BÁO CÁO PHÂN TÍCH DỮ LIỆU
Dự đoán giao dịch thương mại điện tử bằng cách sử dụng phân tích hành vi người tiêu dùng.

1. Mục tiêu
1.1. Chủ đề phân tích
Đề tài tập trung vào việc phân tích hành vi truy cập website thương mại điện tử và dự đoán khả năng khách hàng có phát sinh giao dịch mua hàng hay không.
Dataset được sử dụng là Online Shoppers Purchasing Intention Dataset, lấy từ Kaggle. Bộ dữ liệu này có nguồn gốc từ UCI Machine Learning Repository, gồm 12.330 phiên truy cập, với biến mục tiêu là Revenue cho biết phiên truy cập đó có kết thúc bằng giao dịch mua hàng hay không. Theo mô tả của UCI, dữ liệu gồm các phiên truy cập trong vòng 1 năm nhằm hạn chế thiên lệch do chiến dịch, ngày đặc biệt, hồ sơ người dùng hoặc thời điểm cụ thể.
1.2. Lý do chọn đề tài
Trong thương mại điện tử, không phải mọi khách truy cập website đều mua hàng. Việc nhận biết sớm nhóm khách hàng có khả năng mua giúp doanh nghiệp:
Tối ưu chiến dịch marketing.
Cá nhân hóa nội dung hiển thị.
Gợi ý sản phẩm hoặc ưu đãi phù hợp.
Tăng tỷ lệ chuyển đổi từ truy cập thành mua hàng.
Giảm chi phí tiếp thị cho nhóm khách hàng ít tiềm năng.
Vì vậy, bài toán dự đoán ý định mua hàng có ý nghĩa thực tiễn cao đối với các website bán hàng trực tuyến.
1.3. Đối tượng phân tích
Đối tượng phân tích là các phiên truy cập của người dùng trên website thương mại điện tử.
Mỗi dòng dữ liệu tương ứng với một phiên truy cập, bao gồm thông tin về:
Số lượng trang người dùng đã xem.
Thời gian ở lại từng loại trang.
Tỷ lệ thoát trang.
Giá trị trang.
Tháng truy cập.
Loại khách truy cập.
Thiết bị, trình duyệt, khu vực, nguồn truy cập.
Việc phiên truy cập có tạo ra doanh thu hay không.
1.4. Mục tiêu tổng quát
Mục tiêu tổng quát của báo cáo là phân tích các yếu tố ảnh hưởng đến hành vi mua hàng của khách truy cập website thương mại điện tử và xây dựng mô hình dự đoán khả năng phát sinh doanh thu từ một phiên truy cập.
1.5. Mục tiêu cụ thể
Bài báo cáo hướng đến các mục tiêu cụ thể sau:
Khám phá cấu trúc và đặc điểm của bộ dữ liệu Online Shoppers Purchasing Intention.
Phân tích tỷ lệ mua hàng và không mua hàng trong các phiên truy cập.
Xác định các biến có ảnh hưởng lớn đến khả năng phát sinh doanh thu.
Xây dựng và so sánh một số mô hình phân loại để dự đoán biến Revenue.
Đề xuất ý nghĩa thực tiễn từ kết quả phân tích cho hoạt động kinh doanh thương mại điện tử.
1.6. Giới thiệu dataset
Dataset sử dụng: Online Shoppers Purchasing Intention Dataset
Nguồn: Online Shoppers Purchasing Intention Dataset 
Số dòng trong file phân tích: 12.330 dòng
Số cột: 18 cột
Biến mục tiêu: Revenue
Trong đó:
Revenue = True: phiên truy cập có phát sinh giao dịch mua hàng.
Revenue = False: phiên truy cập không phát sinh giao dịch mua hàng.
Theo UCI, dataset có 17 thuộc tính đầu vào và biến Revenue có thể được dùng làm nhãn phân loại.
2. Câu hỏi nghiên cứu
2.1. Câu hỏi nghiên cứu chính
Liệu các đặc điểm hành vi trực tuyến và bối cảnh truy cập có thể dự báo chính xác khả năng khách hàng phát sinh giao dịch mua hàng hay không? 
Đây là câu hỏi chính của bài toán vì mục tiêu cuối cùng là phân loại một phiên truy cập thành hai nhóm:
Có mua hàng.
Không mua hàng.
2.2. Câu hỏi nghiên cứu phụ
Để trả lời câu hỏi chính, báo cáo tập trung vào các câu hỏi phụ sau:
Câu hỏi 1: Tỷ lệ phiên truy cập có phát sinh doanh thu là bao nhiêu?
Câu hỏi 2: Những biến nào ảnh hưởng mạnh nhất đến khả năng mua hàng?
Câu hỏi 3: Khách truy cập mới và khách truy cập quay lại có sự khác biệt về tỷ lệ mua hàng không?
Câu hỏi 4: Thời điểm truy cập theo tháng có ảnh hưởng đến khả năng mua hàng không?
Câu hỏi 5: Liệu độ tuổi và giới tính có ảnh hưởng tới khả năng mua hàng hay không?
Câu hỏi 6: Mô hình học máy nào cho kết quả dự đoán tốt nhất trên dataset này?
2.3. Kiểu bài toán
Đây là bài toán phân loại nhị phân.
Biến mục tiêu là Revenue.
Nhãn 0: Không mua hàng.
Nhãn 1: Có mua hàng.
2.4. Ý nghĩa bài toán
Nếu mô hình dự đoán tốt, doanh nghiệp có thể xác định sớm nhóm khách hàng tiềm năng để áp dụng các chiến lược như:
Hiển thị mã giảm giá.
Gợi ý sản phẩm phù hợp.
Gửi thông báo nhắc mua hàng.
Tối ưu giao diện các trang có tỷ lệ chuyển đổi cao.
