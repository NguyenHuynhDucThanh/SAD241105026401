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
      ![Diagram](https://www.planttext.com/plantuml/png/NCv12i9030NGVKynIrtq0aMaOXSMf8ZY0K8dbi1qfYIf8EB9N7Waho1MAnsNUVdm__F-o4M1jMzTKZiGCJjGGg_ccXXZngiiCdDG9jyCMa6B4QoiPHI9R1syGgsbFuN82uB61o7Pa6ZWIsQs9BhuyV9Jp2WrKwSKV1oSVjxPD1qdVCVEvWCSEmkAiUrHcV3yfmKwd2PlIOxUzgrx0G00__y30000)

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
      ![Diagram](https://www.planttext.com/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niO9ZGK5-Pbv9RcfUYK8rbuA20hA8fukLGd19KMPUEbWc8B4a4rFK9R4aDIGpDzKApW8B1vSabfGM8wdKrOM8L-Ob8rbHhA495WufIapEziqiBavDmI8Rb5gSd96QKfgJYYIfeSbLo-MGcfTIcfi30000__y30000)

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
      ![Diagram](https://www.planttext.com/plantuml/png/N8n12i8m44NtESKiMsWlq5M52Wfj4Nk2q8vrC9b0Cj55wSbSU2Il8Cr2nELx__7VprSTH7k9rgZHw13WJE6sC-W55WK0YOzD1ODuuZcfanP2bZ-xXItUqLImvsXXWTOz2kXmecWBED1yXVLRDYYQJFXvACiqTev9dD-QB4zcG9usx9tGXKOjv3ZBrQfgv2bQym400F__0m00)

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
    ![Diagram](https://www.planttext.com/plantuml/png/L8qn3e9054JxFSKlDP4BKA52Z8MDS84VcH0IzaEMlqOadCp28ta5uqgCbE_DPERrU2QzibDl6tDfkE_fZAvrIgCXeXcEQKovkbggFraC7MBAn5iQwSJ25In4DxILLWPRtr7I5Ffx1rQKks6nah9YJk80HMrXYA8en0S872k-Pwjra3bVboAxVU2d9fD0Ic-RDm000F__0m00)

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
      ![Diagram](https://www.planttext.com/plantuml/png/B8r12i8m44NtESKiMsWlK4HQr8LGGImU8CHf7KYca9aifFHaBZoILv2sRX__l_TzVsfH6pK5Rvot8j2XIv7q1PC10BWBnlEnWauZyR2Ys-YnWXEd01CqZq1SmC4JaxE-Kzlt1Lmism4ZpElXYZ6G28qi5RGakjjiUmDGbkkaIVf4Ld9MSKbc-OP5QE0b-0VjE3JEeKYMczdKo8yK_0y00F__0m00)
