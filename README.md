# chessGameProject

Link video demo: https://youtu.be/L870Yks0yno
Trong video chúng em cho model đánh với 1 con bot có elo 1700 trên chess.com và thắng.

## Tính Năng

Triển khai đầy đủ luật cờ vua bao gồm các nước đi đặc biệt:
- Nhập thành (cả bên vua và bên hậu)
- Bắt tốt qua đường (En passant)
- Phong cấp tốt
Các chế độ chơi:
  - Người chơi với AI (nhấn phím 1)
  - AI với Người chơi (nhấn phím 2)
  - AI với AI (nhấn phím 3)
  - Người với Người (nhấn phím 4)
Bảng hiển thị lịch sử nước đi với ký hiệu đại số tiêu chuẩn
Khởi động lại ván đấu (nhấn phím R)

## Cấu Trúc Dự Án

Dự án bao gồm bốn module Python chính:

- `main.py`: Điểm khởi đầu của ứng dụng
- `gui.py`: Giao diện người dùng đồ họa sử dụng Pygame
- `chess_engine.py`: Luật cờ vua và kiểm tra nước đi hợp lệ
- `chess_ai.py`: Triển khai AI cho máy tính

### Logic Cờ Vua

Logic trò chơi trong `chess_engine.py` triển khai:

- **Tạo Nước Đi**: Tính toán tất cả các nước đi hợp lệ cho từng loại quân cờ
- **Phát Hiện Chiếu**: Xác định các mối đe dọa đối với quân vua và áp dụng các giới hạn thích hợp
- **Phát Hiện Ghim**: Xác định và xử lý các quân cờ bị ghim không thể di chuyển tự do
- **Nước Đi Đặc Biệt**: Xử lý nhập thành, bắt tốt qua đường và phong cấp tốt

### Triển Khai AI

AI trong `chess_ai.py` sử dụng một số kỹ thuật và thuật toán sau:

1. **Minimax với Alpha-Beta Pruning**: Tìm kiếm cây trò chơi đến độ sâu xác định (mặc định: 3) đồng thời cắt tỉa các nhánh không thể ảnh hưởng đến quyết định cuối cùng, cải thiện hiệu suất đáng kể.

2. **Sắp Xếp Nước Đi**: Sắp xếp các nước đi theo giá trị ước tính để cải thiện hiệu quả cắt tỉa alpha-beta:
   - Bắt quân giá trị cao bằng quân giá trị thấp
   - Phong cấp tốt
   - Các nước bắt quân và nước đi khác

3. **Tìm Kiếm Yên Tĩnh (Quiescence Search)**: Tiếp tục tìm kiếm các vị trí không ổn định vượt quá độ sâu tìm kiếm thông thường để tránh hiệu ứng đường chân trời.

4. **Đánh Giá Vị Trí**: Xem xét nhiều yếu tố để đánh giá vị trí trên bàn cờ:
   - **Vật Liệu**: Giá trị các quân (Tốt=100, Mã=320, Tượng=330, Xe=500, Hậu=900)
   - **Vị Trí Quân Cờ**: Các ô khác nhau có giá trị khác nhau cho từng loại quân cờ
   - **Cấu Trúc Tốt**: Phạt tốt cô lập và tốt đôi
   - **An Toàn Của Vua**: Thưởng cho nhập thành, tốt che chắn, và phạt cho cột mở gần vua
   - **Vị Trí Xe**: Thưởng cho xe trên cột mở và hàng 7
   - **Tốt Thông**: Thưởng cho tốt không bị chặn bởi tốt đối phương

## Tính Năng Giao Diện

Giao diện đồ họa trong `gui.py` cung cấp:

- Bàn cờ có màu sắc với các ô sáng và tối xen kẽ
- Đánh dấu trực quan cho quân cờ được chọn và các nước đi hợp lệ
- Bảng hiển thị lịch sử nước đi với ký hiệu cờ vua tiêu chuẩn
- Hoạt ảnh di chuyển quân cờ
- Chỉ báo trực quan cho các điều kiện kết thúc trò chơi (chiếu bí, hòa cờ)

## Cách Chơi

1. Chạy trò chơi bằng cách thực thi `python main.py`
2. Chọn chế độ chơi bằng cách sử dụng phím 1-4:
   - 1: Người chơi (Trắng) với AI (Đen)
   - 2: AI (Trắng) với Người chơi (Đen)
   - 3: AI với AI (biểu diễn)
   - 4: Người với Người
3. Thực hiện nước đi bằng cách nhấp vào quân cờ và sau đó nhấp vào ô đích
4. Sử dụng phím 'R' để khởi động lại trò chơi


## CONTRIBUTION:

- Nhóm gồm 2 thành viên là Vũ Huy Đông - 23021529 và Trịnh Trung Đức - 23021537
- Bạn Đông tạo logic cờ vua và xử lí đồ họa (chess_engine và gui)
- Bạn Đức xử lí logic AI (chess_ai)
- Trong quá trình làm thì cả 2 vẫn hỗ trợ phần của nhau

