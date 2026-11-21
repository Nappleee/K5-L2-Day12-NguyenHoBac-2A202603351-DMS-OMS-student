# Danh sách lớp v0 — Nguyễn Hồ Bắc · G05

Bản nháp chức năng dựa trên GUIDE Cabin v1.0; các hàng thuộc tính không phải yêu cầu tạo thêm label trong CVAT.

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person / seat | driver | Xác định người lái để liên kết mặt và tay đúng người | Có nếu phần cơ thể đủ rõ |
| 2 | person / seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Nhận biết trạng thái dây an toàn | Có thể; bị che hoặc không phân biệt được thì unknown |
| 3 | face / eye_left, eye_right | open / closed / unknown, riêng từng mắt | Cung cấp trạng thái mắt từng khung; chuỗi thời gian hỗ trợ phát hiện nhắm mắt kéo dài | Có thể; phản xạ và kính có thể làm mất chi tiết |
| 4 | face / glasses | unknown / none / clear / sun | Nhận biết kính và điều kiện che khuất vùng mắt | Có giới hạn; NIR có thể làm kính râm trông trong suốt |
| 5 | face / gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Ước lượng vùng nhìn, hỗ trợ theo dõi chú ý | Có thể từ mắt và đầu; không chắc dùng other và ghi lý do |
| 6 | face13 | 13 điểm, cờ occluded / outside | Biểu diễn hình học mắt, mũi, miệng; hỗ trợ các tác vụ mặt | Có thể nếu mặt đủ lớn và chi tiết đủ rõ; mặt dưới 60 px không gán |
| 7 | hand / whose, side, on_wheel | driver / passenger; left / right; yes / no / unknown | Phân biệt tay và tình trạng chạm vô lăng | Có thể; trái/phải theo người |
| 8 | phone / state | held / mounted / lap | Nhận biết vị trí điện thoại để hỗ trợ đánh giá hành vi | Chỉ gán khi thấy cạnh, góc hoặc màn hình máy |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person | Có box khi có người | Phát hiện người trong cabin, hỗ trợ kiểm kê hành khách | Có nếu cơ thể đủ rõ |
| 2 | face | Box mặt người lớn thấy rõ | Bổ sung vị trí mặt cho người trong cabin | Có thể; không gán nếu mặt không thấy theo §4.5 |
| 3 | seat | driver / front_passenger / rear_left / rear_middle / rear_right | Liên kết người hoặc vật với vị trí trong xe | Suy từ vị trí theo xe, không dựa vào màu |
| 4 | child_seat / occupied | no / unknown | Nhận biết ghế trẻ em trống; phân biệt ghế với người và đồ vật | Có thể từ hình dạng; không rõ bên trong dùng unknown |
| 5 | infant_seat / facing | rear / front | Phân biệt nôi và hướng đặt theo xe | Có thể nếu hình dạng đủ rõ |
| 6 | object / type | bag / box / cup / other | Phân biệt đồ vật với người và ghế trẻ em; kiểm kê đồ mang theo | Có thể từ hình dạng; không đoán bằng màu |
| 7 | person / seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Gắn trạng thái dây với người trên ghế | Có giới hạn; riêng SVIRO chỉ not_worn hoặc unknown |
| 8 | frame_meta | modality: rgb / ir; light: day / night / unknown; camera_blocked: yes / no | Ghi điều kiện khung ảnh cho phân tích chất lượng | Đây là metadata; SVIRO có light=unknown |

## 2 câu hỏi leo thang

1. **D03.png:** khi mắt và kính đều unknown, tiêu chí nào đủ để đặt điểm ước lượng với occluded thay vì outside? Cần ngưỡng hoặc ví dụ chuẩn để hai người gán nhất quán. Bản hiện tại có các điểm outside; giữ nguyên để người gán kiểm trên CVAT theo §4.6, không suy vị trí từ ảnh khác.
2. **S05_rgb.png / S05_ir.png:** OMS chỉ yêu cầu box face, vậy các thuộc tính gaze_zone tự có trong schema có cần đánh giá và đồng bộ giữa hai ảnh không? XML hiện là mirror_r ở RGB và other ở IR. Tạm giữ nguyên vì §4.1 chỉ yêu cầu box ở OMS; không sao chép hướng nhìn từ RGB để đoán IR. Cần coach xác định có bỏ qua các thuộc tính này khi chấm OMS hay không.
