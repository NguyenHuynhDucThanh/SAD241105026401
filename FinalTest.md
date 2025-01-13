# 3.Xác định các phần tử thiết kế
 1. Phần tử dữ liệu bệnh nhân (Patient Data Element)
  - Chức năng:  
    - Lưu trữ và quản lý thông tin chi tiết về bệnh nhân, bao gồm:  
      - Thông tin cá nhân (họ tên, mã bệnh nhân, địa chỉ, thông tin liên hệ).
      - Lịch sử chẩn đoán và điều trị.
      - Hồ sơ thuốc đã kê và phản ứng phụ (nếu có).
  - Các thành phần chính:
    - Thuộc tính:
      - PatientID (Mã bệnh nhân): Unique, string.
      - Name, Address, ContactInfo: string.
      - DiagnosisHistory: list of diagnosis objects.
      - PrescriptionHistory: list of prescription objects.
    - Hành vi:
      - AddPatient(), UpdatePatient(), RetrievePatient(), DeletePatient()
   - Biểu đồ PlantText  
      ![Diagram](https://www.planttext.com/plantuml/png/NCv12i9030NGVKynIrtq0aMa2nSMN1GyGPY99J3Db2GLH3oP2u_a5SJMGiTbNZxy_tw-QZKG6_jO-0YghWKZP7FtmZddXlbgGkNE9iJTf0mzPW0X2AfcvXCRU6luaZ8F11qd9JsIMf9RvKwajZiil9-B1TKB3KQ9ys2x-dopPRbC-4tVR2SOXm26kGcQ45x_D634TV9HrCXXxEC7003__mC0)

 2. Phần tử quản lý lịch hẹn (Appointment Management Element)
  - Chức năng:
    - Đồng bộ hóa lịch hẹn từ hệ thống APPOINTMENTS.
    - Ghi nhận và quản lý các lịch hẹn bị bỏ lỡ.
  - Các thành phần chính:
    - Thuộc tính:
      - AppointmentID: Unique, string.
      - PatientID: Foreign key liên kết với bệnh nhân.
      - DateTime, Status: datetime, string.
    - Hành vi:
      - SyncAppointments(), TrackMissedAppointments(), RescheduleAppointment().
 - Biểu đồ PlanText  
      ![Diagram](https://www.planttext.com/plantuml/png/RCqn2a8n3CRnlQV8-DxmBl2c9xWuEEa5GXCqsDRIf8E89tFmI5v1g885tSBl_q6UzyUYXiLg3Cu7L8LLpcT95ZaPN1q007vbGpFih4Wwj9BHv5S9ZVSIUORrvsgiXbQrMqxJso_9Tqzr61jRGN_QYYhJdrfO_P6f1kxYCBgRMpXHZU45003__mC0)

3. Phần tử quản lý cảnh báo nguy cơ (Risk Alert Element)
 - Chức năng:
    - Phát hiện và cảnh báo các nguy cơ liên quan đến hành vi tự hại hoặc gây hại của bệnh nhân.
 - Các thành phần chính:
    - Thuộc tính:
      - RiskID: Unique, string.
      - PatientID: Foreign key.
      - RiskLevel (Low, Medium, High): enum.
      - RiskDetails: string.
    - Hành vi:
      - MonitorRisk(), SendRiskNotification().
 - Biểu đồ PlantText  
      ![Diagram](https://www.planttext.com/plantuml/png/N8un2eD044NxFSMK2de1AmDA53I1X91wqKqOt9sLdJ6DUB8KELAk4BG88UL___7vx-ShPz519cTLPpKpd927dJL1O5O0005vgFiCpXAGxXiQjQ0X-QEhs9Y7iHcKD3cOeJbU4sZBehwq2LJrleBbQnP6D5h-MKZJhNIUK7nORqJnHjXGlyQ35xnXfmKzHR5QL6wedvpz0000__y30000)

4. Phần tử quản lý báo cáo (Report Management Element)
 - Chức năng:
   - Tạo và lưu trữ các báo cáo quản lý hoặc báo cáo ẩn danh.
 - Các thành phần chính:
   - Thuộc tính:
    - ReportID: Unique, string.
    - ReportType (Management, Anonymized): enum.
    - CreatedBy: string.
    - DateCreated: datetime.
  - Hành vi:
    - GenerateReport(), SaveReport(), ExportReport().
- Biểu đồ PlantText  
    ![Diagram](https://www.planttext.com/plantuml/png/L8v12e9068NtSugtBCWBkD9oY1PEK6vgDpW_8kWaCx-HY2ThqP6wGZH2vF9zt-FntizNubaxxjj6b8ts7YVgReun2W1m8HnCZ3ExsbP_i1WwYY5jts94dgfqBtEfYWrITLIN_72L6QRGBnrf9hCT5Yj6C-rc4oFJJ4NTaW2YAEYAB3dDDDzPhGFq-hu4zFY67vf4GjRqRVC1003__mC0)

5. Phần tử bảo mật và quyền riêng tư (Security and Privacy Element)
  - Chức năng:
    - Bảo vệ dữ liệu và quản lý quyền truy cập hệ thống dựa trên vai trò.
  - Các thành phần chính:
    - Thuộc tính:
      - UserID: Unique, string.
      - Role (Admin, ClinicalStaff, Manager): enum.
      - Permissions: list of permissions.
    - Hành vi:
      - AuthenticateUser(), AssignRole(), LogAccess().
- Biểu đồ PlantText  
      ![Diagram](https://www.planttext.com/plantuml/png/BCnB2eCm58NXULPnXmgw0Id5uAC4r86s2v3qOWDvbDnaKCILTT0bTGi5xVJZF-Vx_fGKPX-YqKpgcGWcbD6hy8AL0G14GY_g0gRWbLrsyavZ0OsD1bRWTI-63AfE3ABYtNJbRPj1pmT-QKROzi4JlL54obage5CKJiVRcG7a-PxCCJpG1YNdW3T2dwG74wd5ZaxZ7xHRk9H8bAHiOoNQUpJw1m00__y30000)

### Chú thích nguồn tham khảo
  1. Phần tử dữ liệu bệnh nhân (Patient Data Element)
 - Mentcare Requirements Document (trang 3-10): Chi tiết các thông tin quản lý hồ sơ bệnh nhân như dữ liệu cá nhân, lịch sử chẩn đoán, và thuốc đã kê
 - Software Engineering: Ian Sommerville (Tenth Edition): Phân tích thiết kế dữ liệu trong hệ thống y tế
   - (https://github.com/opendesigncasestudies/Mentcare---IanSommerville)
   - (https://software-engineering-book.com/case-studies/mentcare/)

  2. Phần tử quản lý lịch hẹn (Appointment Management Element)
 - Mentcare Requirements Document (trang 11): Đồng bộ hóa và theo dõi lịch hẹn từ hệ thống APPOINTMENTS
 - Phân tích từ các bài nghiên cứu thực tế về tích hợp lịch và quản lý thời gian trong phần mềm y tế​
   - (https://fossvjcet.github.io/CS-S5/CST309%20-%20Management%20of%20Software%20Systems/Other%20Notes/Module%202.2.pdf)
   -  (https://software-engineering-book.com/case-studies/mentcare/)

  3. Phần tử quản lý cảnh báo nguy cơ (Risk Alert Element)
 - Mentcare Requirements Document (trang 10-12, 15-17): Mô tả các yêu cầu cảnh báo nguy cơ liên quan đến hành vi tự hại hoặc gây hại​
 - Software Engineering: Ian Sommerville: Đưa ra các khái niệm thiết kế về hệ thống cảnh báo trong phần mềm an toàn
   - (https://github.com/opendesigncasestudies/Mentcare-IanSommerville)
   -  (https://www.slideshare.net/slideshow/se-chapter-4-software-requirementspptx/266205338)

  4. Phần tử quản lý báo cáo (Report Management Element)
 - Mentcare Requirements Document (trang 12-14): Chi tiết các yêu cầu về tạo và lưu trữ báo cáo, đặc biệt là báo cáo ẩn danh​
 - Tài liệu về báo cáo y tế và bảo mật thông tin từ các nghiên cứu liên quan​
   - (https://github.com/opendesigncasestudies/Mentcare-IanSommerville)
   -  (https://fossvjcet.github.io/CS-S5/CST309%20-%20Management%20of%20Software%20Systems/Other%20Notes/Module%202.2.pdf)

  5. Phần tử bảo mật và quyền riêng tư (Security and Privacy Element)
 - Mentcare Requirements Document (trang 16-19): Yêu cầu bảo mật và phân quyền người dùng trong hệ thống​
 - Phân tích thiết kế hệ thống bảo mật trong tài liệu Ian Sommerville và các ví dụ tiêu chuẩn ngành​
   - (https://software-engineering-book.com/case-studies/mentcare/)
   -  (https://www.slideshare.net/slideshow/se-chapter-4-software-requirementspptx/266205338)

* Software Engineering, Ian Sommerville: Nguồn thông tin lý thuyết về kỹ thuật phần mềm, bao gồm phân tích và thiết kế hệ thống thực tế.
* Bài nghiên cứu và thực hành từ FossVCET và SlideShare: Phân tích yêu cầu và thiết kế liên quan đến các hệ thống y tế
  - (https://fossvjcet.github.io/CS-S5/CST309%20-%20Management%20of%20Software%20Systems/Other%20Notes/Module%202.2.pdf)
  - (https://www.slideshare.net/slideshow/se-chapter-4-software-requirementspptx/266205338)
