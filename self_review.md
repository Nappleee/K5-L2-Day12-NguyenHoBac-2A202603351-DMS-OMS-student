# Tự đánh giá — Nguyễn Hồ Bắc · G05

Đây là rà soát từ XML và log với AI hỗ trợ, chưa phải xác nhận đã mở lại ảnh trên CVAT. Không dùng AI xem ảnh cabin.

## 1. Tự rà soát 4 cảnh

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S03_ir.png | frame_meta | missing | check_cpA.txt ghi thiếu tag; final hiện có đúng một tag modality=ir | Đã hết lỗi trong final |
| S04_ir.png | frame_meta | missing | Cùng lỗi checkpoint A; final hiện có đúng một tag modality=ir | Đã hết lỗi trong final |
| D01.png | object | extra | 2 box object; GUIDE §4.2 không gán object trong DMS | Chưa; cần xử lý trên CVAT |
| D02.png | object, face13 | extra | 2 box object ngoài phạm vi DMS; skeleton có 13 điểm, left_eye_outer có y lớn hơn right_eye_outer | Chưa sửa object; chưa kiểm vị trí điểm bằng ảnh |

## 2. Lỗi lặp lại có bằng chứng

Thiếu frame_meta ở hai ảnh IR trong checkpoint A; lỗi này đã hết ở final. Nguyên nhân thao tác thực tế chưa được người học xác nhận. Cách tránh: tạo tag trước box đầu tiên, kiểm modality theo tên ảnh và chạy --only đúng phạm vi.

Một lỗi phạm vi còn lại: object xuất hiện ở cả D01–D06, tổng 9 box (D01: 2; D02: 2; D03: 2; D04: 1; D05: 1; D06: 1). Cách xử lý đề xuất: mở CVAT, bỏ các box object thuộc phần DMS theo §4.2, export lại và kiểm lại. Chưa thực hiện; không sửa XML bằng tay.

## 3. Ghi chú về disagreement_log

Cả 4 dòng diff đều giữ bản mình theo guideline: infant_seat ở S06 không thể nằm ở seat=driver trong phần OMS; child_seat ở S08 không có occupied=yes. Không có dòng nào chứng minh peer đúng và mình sai, nên không tạo một ví dụ giả cho mục này. Kết luận giữ rear_right không thay thế kiểm vị trí thực tế theo xe trên ảnh.

## 4. Giới hạn tự kiểm

- Script final: 0 lỗi, 0 cảnh báo; không chứng minh vị trí box, lớp và thuộc tính đều đúng.
- D01 và D04 không có face. Cần người học xác nhận lý do không thấy mặt theo §4.5; không thể kết luận từ XML.
- D03 có mắt/kính unknown và gaze_zone=other: cần người học bổ sung lý do nhìn thấy thực tế.
- ir_log.csv ghi bằng chứng nhãn và nguyên tắc, chưa xác nhận hiện tượng thị giác gây ra các giá trị unknown.
