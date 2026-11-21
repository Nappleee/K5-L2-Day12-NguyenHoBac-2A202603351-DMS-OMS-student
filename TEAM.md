# TEAM — Ngày 12

Mã bộ ảnh: **G05** · Hình thức: **cá nhân**

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Nguyễn Hồ Bắc | 2A202603351 | Có, export chứa 22 ảnh và 22 frame_meta | Đào Bình An | 4/4 |

Đối chiếu `export_final.zip` với `peer_export_final.zip` bằng script trong repo. Cả 4 bất đồng đã có kết luận theo guideline trong `disagreement_log.csv`; chưa có xác nhận hai bên đã thảo luận trực tiếp. Không có dòng cần đổi nhãn của bản thân theo kết quả diff này. Không tạo `export_final_v2.zip` khi chưa sửa trên CVAT.

## Cá nhân

### NguyenHoBac-2A202603351

- Phần mình làm: bản export cá nhân 22 ảnh; đối chiếu với bản của Đào Bình An. Dùng AI hỗ trợ tự kiểm và soạn tài liệu, khai báo tại `prompts.md`.
- Bài học từ bằng chứng: phải đặt frame_meta trước khi vẽ; checkpoint A thiếu tag ở S03_ir và S04_ir, bản final đã đủ. Diff chỉ xác nhận sự nhất quán; vẫn phải kiểm phạm vi nhãn theo GUIDE.
- Ca cần rà lại: 9 box object trên D01–D06 nằm ngoài phạm vi DMS của GUIDE §4.2. Chưa xác nhận đã hỏi coach.
