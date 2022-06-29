# Đồ án khai phá dữ liệu
## Đề tài : Dự báo thời tiết dựa trên quan sát hằng ngày từ các trạm thời tiết ở Úc
### Nhóm 12

#### Trần Thành Quang	19133047
#### Hoàng Minh Nhật 	19133042
#### Bùi Quốc Kiệt	    19133030
#### Đỗ Minh Đức		    19133021

### Phần 1 - Giới thiệu
### Phần 2 - Dữ liệu
### Phần 3 - Kế hoạch phân tích dữ liệu

## Phần 1 - Giới thiệu
- **Tên đề tài** : Weather forecast based on daily weather observations from multiple Australian weather stations .
- **Tổng quan** : Dự báo thời tiết có một vai trò to lớn trong đời sống kinh tế, xã hội. Dự báo đúng sẽ giúp con người đưa ra những quyết định đúng đắn. 
- **Mục tiêu** : Dự báo thời tiết ngày tiếp theo ở Úc .
	Biến kết quả (Y) : RainTomorrow
- **Nguồn** : Bộ dữ liệu nguồn đến từ Cục Khí tượng Khối thịnh vượng chung Úc. Cục đã cho phép sử dụng dữ liệu với Cục Khí tượng được thừa nhận là nguồn của dữ liệu, theo email từ Cathy Toby (C.Toby@bom.gov.au) thuộc Dịch vụ Thông tin Khí hậu của Trung tâm CLimate Quốc gia, 17 Tháng 12 năm 2008.
- **Link nguồn** : https://www.rdocumentation.org/packages/rattle/versions/5.4.0/topics/weatherAUS

## Phần 2 - Dữ liệu

- **Tổng quan** : Tập dữ liệu là một khung dữ liệu quan sát hàng ngày từ hơn 45 trạm thời tiết của Úc. Tập dữ liệu có 208395 dòng và có 24 cột .

  ![image](https://user-images.githubusercontent.com/93425051/176414155-798778a7-1da3-434d-b7f2-2b50d1664acc.png) 

- **Tóm tắt** về tập dữ liệu : 
  ![image](https://user-images.githubusercontent.com/93425051/176414346-26cc6d83-2271-465e-91f8-fef19e1d1eba.png)

### Ý nghĩa các biến :

- **Date**: Ngày quan sát (một đối tượng Date).
- **Location**: Tên thông thường của vị trí của trạm thời tiết.
- **MinTemp**: Nhiệt độ tối thiểu tính bằng độ C.
- **MaxTemp**: Nhiệt độ tối đa tính bằng độ C.
- **Rainfall**: Lượng mưa được ghi lại trong ngày tính bằng mm.
- **Evaporation** : Cái gọi là độ bốc hơi của chảo loại A (mm) trong 24 giờ đến 9 giờ sáng.
- **Sunshine** : Số giờ nắng sáng trong ngày.
- **WindGustDir** : Hướng gió giật mạnh nhất trong 24 giờ  đến nửa đêm.
- **WindGustSpeed** : Tốc độ (km / h) của gió giật mạnh nhất trong 24 giờ đến nửa đêm.
- **Temp9am** : Nhiệt độ (độ C) lúc 9 giờ sáng.
- **RelHumid9am** : Độ ẩm tương đối (phần trăm) lúc 9 giờ sáng.
- **Cloud9am** : Một phần bầu trời bị mây che khuất lúc 9 giờ sáng. Điều này được đo bằng "oktas", là một đơn vị của eigth. Nó ghi lại bao nhiêu vùng trời bị mây che khuất. Số đo 0 cho biết bầu trời hoàn toàn trong khi số 8 cho biết trời hoàn toàn u ám.
- **WindSpeed9am** : Tốc độ gió (km / giờ) trung bình trong 10 phút trước 9 giờ sáng.
- **Pressure9am** : Áp suất khí quyển (hpa) giảm xuống mức trung bình của mực nước biển lúc 9 giờ sáng.
- **Temp3pm** : Nhiệt độ (độ C) lúc 3 giờ chiều.
- **RelHumid3pm** : Độ ẩm tương đối (phần trăm) lúc 3 giờ chiều.
- **Cloud3pm** : Một phần bầu trời bị mây che khuất (trong "oktas": phần tám) lúc 3 giờ chiều. Xem Cload9am để biết mô tả về các giá trị.
- **WindSpeed3pm** : Tốc độ gió (km / giờ) trung bình trong 10 phút trước 3 giờ chiều.
- **Pressure3pm** : Áp suất khí quyển (hpa) giảm xuống mức trung bình của mực nước biển lúc 3 giờ chiều.
- **ChangeTemp** : Thay đổi nhiệt độ.
- **ChangeTempDir** : Hướng thay đổi của nhiệt độ.
- **ChangeTempMag** : Độ lớn của sự thay đổi của nhiệt độ.
- **ChangeWindDirect** : Hướng gió thay đổi.
- **MaxWindPeriod** : Thời kỳ gió cực đại.
- **RainToday** : Số nguyên: 1 nếu lượng mưa (mm) trong 24 giờ đến 9 giờ sáng vượt quá 1 mm, nếu không thì 0.
- **TempRange** : Sự khác biệt giữa nhiệt độ tối thiểu và tối đa (độ C) trong 24 giờ đến 9 giờ sáng.
- **PressureChange** : Thay đổi áp suất.
- **RISK_MM** : Lượng mưa. Một loại thước đo "rủi ro".
- **RainTomorrow** : Biến mục tiêu. Ngày mai trời có mưa không?

## Phần 3 - Kế hoạch phân tích dữ liệu

##### câu 1:  Số giờ nắng và lượng mưa ghi lại trong ngày có ảnh hưởng tới thời tiết của ngày tiếp theo không ?

- Sử dụng cột Rainfall, Sunshine

##### Câu 2 : Các yếu tố Sự thay đổi nhiệt độ , áp suất thay đổi(tăng hoặc giảm) , tốc độ gió , độ ẩm thì có ảnh hưởng đến thời tiết ở ngày tiếp theo không ?

- Sử dụng cột PressureChange ,ChangeTemp ,ChangeWindDirect , cloud3pm , cloud9am…

##### Câu 3 :  Các yếu tố có ảnh hưởng như thế nào đến RainTomorrow ?

##### Câu 4 :  Đâu là yếu tố chính ảnh hưởng đến RainTomorrow ? 

##### Câu 5 :  Vị trí các trạm có ảnh hưởng đến dự đoán RainTomorrow ?

- Sử dụng cột : Location

#### Kết luận :  
  - Từ các câu hỏi trên ta trả lời câu hỏi lớn nhất cho tập dữ liệu này là: Dự đoán một ngày mai trời có mưa không , nếu có lượng là bao nhiêu
    **Biến kết quả (Y)** : RainTomorrow 
    **Biến dự đoán (X)** : Các biến còn lại .
    
#### Phương pháp thực hiện
- Xử lý dữ liệu : làm sạch giá trị NA , NULL, String ….
- Phân tích vẽ biểu đồ trực quan hóa dữ liệu
- Thống kê tóm tắt dữ liệu 
- Xây dựng mô hình hướng  đến dự báo lượng mưa
- Xây dựng mô hình dữ đoán biến đầu ra :
- Chia tập dữ liệu thành 2 phần : 80% train , 20 % test .
- Sử dụng thuật toán (decision tree , randomforest , SVM ,..)
- Đánh giá các mô hình dự đoán  :
  Confusion matrix , Precision và Recall .
  
