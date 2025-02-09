12:42 PM 11/20/2024
## Mô hình chấm công nhân viên sử dụng Vân tay và Khuôn mặt - MCU ESP32 và ESP32CAM
### 1. Sơ đồ phần cứng gồm: 
- MCU ESP32, ESP32Cam - AI Thinker
- Sensor AS608
- LCD 20x04
- Keypad 4x4
- TFT LCD 1.8 inch
- Opto PC817, Resistor, LED,...
### 2. Mạch chính
<p align="center">
  <img src="PCB_Mach_Chinh/mach_chinh_schematic_pbl5.jpg" alt="Schematic Mạch chính" width="300">
  <img src="PCB_Mach_Chinh/mach_chinh_PCB_3D_pbl5.jpg" alt="PCB_3D Mạch chính" width="390">
</p>

### 3. Mạch nguồn
<p align="center">
  <img src="PCB_Mach_Nguon/mach_nguon_schematic_pbl5.jpg" alt="Schematic Mạch nguồn" width="300">
  <img src="PCB_Mach_Nguon/mach_nguon_PCB_3D_pbl5.jpg" alt="PCB_3D Mạch nguồn" width="370">
</p>

### 4. Mô hình AI nhận diện khuôn mặt và chấm công
- Mô hình AI sử dụng thư viện Face_recognition
- Đầu vào sẽ lấy hình ảnh từ Web server
- Đầu ra là thông tin chấm công của nhân viên
### 4. Nguyên lý hoạt động
#### Vân tay quét thành công thì khung camera mới khởi động!!!
- Chức năng thêm nhân viên: Thêm vân tay thành công -> ESP32 gửi tín hiệu điều khiển qua PC817 -> ESP32CAM nhận tín hiệu điều khiển và bật khung camera của ESP32CAM để thêm khuôn mặt -> Tắt Camera
- Chức năng chấm công nhân viên: Quét vân tay thành công -> ESP32 gửi tín hiệu điều khiển qua PC817 -> ESP32CAM nhận tín hiệu điều khiển và bật khung camera của ESP32CAM để quét khuôn mặt -> Chấm công thành công -> Gửi thông tin chấm công (tên, trạng thái, thời gian) lên Web server -> Tắt Camera
- Chức năng xóa nhân viên: Thực hiện xóa vân tay nhân viên
- Hình ảnh được ESP32CAM chụp lại và gửi lên Web server
### 5. Giao diện chấm công
<p align="center">
  <img src="htdocs/employee_attendance_view.jpg" alt="employee_attendance_view" width="600">
  <img src="htdocs/esp32cam_stream_view.jpg" alt="esp32cam_stream_view" width="370">
</p>

#### Giao diện của bảng chấm công và hình ảnh stream từ ESP32CAM

## Mô hình hệ thống
<p align="center">
  <img src="mo_hinh_pbl5.png" alt="Mô hình" width="800">
</p>
