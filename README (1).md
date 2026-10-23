# GREENLANE V4 — Green Passport / Route Choice Studio

## Chạy ứng dụng

Giải nén ZIP, mở thư mục trong VS Code, chọn **Open with Live Server** tại `index.html` (hoặc chạy `python3 -m http.server 8080` và mở localhost:8080). Cần Internet cho Leaflet, OpenStreetMap, Photon và OSRM.

## Điểm mới so với V3

- **Logo nguyên bản** trích từ hình người dùng cung cấp, chỉ cắt khoảng trắng ngoài, không vẽ lại chữ, biểu tượng hay tagline.
- **Route Choice Studio**: xem rõ tuyến nhanh nhất so với ít tiếp xúc bụi ước tính nhất, thời gian đánh đổi, % thay đổi chỉ số tiếp xúc; nút chọn/zoom vào tuyến ít tiếp xúc.
- **Green Passport**: lưu tối đa 15 cặp điểm đi–đến vào localStorage trên trình duyệt; mở lại sẽ yêu cầu tìm tuyến mới. Không lưu GPS lịch sử hay thông tin định danh.
- **Discovery Challenge**: thử ba hành động khám phá trong một phiên, không khẳng định lợi ích sức khỏe hoặc đo lường tiết kiệm phát thải.
- Giữ nguyên tìm điểm đi/đến Photon, tối đa 3 tuyến OSRM, Google Maps handoff, zoom theo tuyến và các lớp DEMO từ V3.

## Giới hạn trung thực

- PM2.5, xe, số xe 5 phút, lớp bụi, chỉ số tiếp xúc đều là **DEMO**, không kết nối IoT. Thời gian và hình dạng tuyến từ dịch vụ OSRM công cộng khi gọi thành công.
- Điểm tiếp xúc là nồng độ mẫu × phút, không phải liều hít vào hoặc kết luận y tế. % dựa trên cùng một bộ mẫu DEMO.
- Google Maps có thể tính lại đường; waypoint chỉ là cố gắng truyền tuyến gần đúng. Không cam kết Google Maps giữ nguyên tuyến.
- Dịch vụ công cộng cần Internet, chịu giới hạn truy cập và số tuyến thực sự tìm được; không dùng như production SLA.
- Để triển khai thật: MQTT/TLS → dữ liệu xe/PM2.5 đã hiệu chuẩn → PostGIS spatial/time aggregation → routing provider có SLA → quyền riêng tư và chất lượng dữ liệu.
