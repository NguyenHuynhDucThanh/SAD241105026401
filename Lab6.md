# Thiết kế lớp - Payroll System

## **Lớp TimecardForm (Boundary)**
### Operations:
- `displayTimecard()`: Hiển thị thông tin chấm công.
- `enterHoursForChargeNumbers()`: Nhập số giờ làm việc theo mã charge.
- `displayChargeCodes()`: Hiển thị danh sách mã charge.
- `saveTimecard()`: Lưu thông tin chấm công.
- `maintainTimecard()`: Quản lý thông tin chấm công.

---

## **Lớp TimecardController (Control)**
### Operations:
- `getCurrentTimecard(forEmployee: Employee): Timecard`: Lấy thông tin chấm công hiện tại.
- `getChargeNums(): ChargeNumList`: Lấy danh sách mã charge.
- `updateTimecard(withEntry: TimecardEntry)`: Cập nhật thông tin chấm công.
- `saveTimecard()`: Lưu thông tin chấm công vào hệ thống.

---

## **Lớp Employee (Entity)**
### Attributes:
- `employeeID: int`: Mã định danh nhân viên.
- `name: String`: Tên nhân viên.
### Operations:
- `add(theTimecard: Timecard)`: Thêm thông tin chấm công cho nhân viên.
- `getEmployeeID(): int`: Lấy mã nhân viên.

---

## **Lớp Timecard (Entity)**
### Attributes:
- `payPeriod: PayPeriod`: Chu kỳ trả lương.
- `entries: List<TimecardEntry>`: Danh sách thông tin giờ làm việc.
### Operations:
- `getTotalHours(): float`: Tính tổng số giờ làm việc.
- `updateTimecard(withTimecardEntry: TimecardEntry)`: Cập nhật thông tin chấm công.
- `save()`: Lưu thông tin chấm công.

---

## **Lớp TimecardEntry (Entity)**
### Attributes:
- `dayOfWeek: Date`: Ngày làm việc.
- `numHours: float`: Số giờ làm việc.
### Operations:
- `new()`: Tạo một mục chấm công mới.

---

## **Lớp ChargeNumList (Entity)**
### Operations:
- `create()`: Tạo danh sách mã charge mới.
- `add()`: Thêm mã charge.
- `delete()`: Xóa mã charge.

---

## **Lớp IProjectManagementDatabase (Interface)**
### Operations:
- `getChargeNumbers(criteria: String): ChargeNumList`: Lấy danh sách mã charge theo tiêu chí.
- `initialize()`: Khởi tạo kết nối với cơ sở dữ liệu.

---

### 2. **Biểu đồ lớp (PlantUML)**

![Biểu đồ](https://www.planttext.com/plantuml/png/VLHjQzim4FuUo7yG_THGyWTC28KqOuLs2wompnVhacZJIpZ9BTxOVzzPgIovjHC8MBvxddkUqvtlVG0AZT7psNnMQ_1Ul2Y3DP3yuiY8rMhl6Yk1slLQ_9tF1F_kX5J-hA5DcRUB540RaBwwXZoZDoUW8tvhp1x9vvnty2MwSHABc8TN_CngGDd0_pBoxxFWZRE1dDP8BBk-74hLHmoRXeWrzaG7Hrjprgv5h4HwMbGzPGbDRbXk9VhJa_8XPJLd2I7hVrFXj6KLRUQBnqctXQUaXPsmNXMAzYy5lWSV7oh1dKclBHXsyIEGiiTK0gIy3QU-IbQoAAnjUxxEMcGSQU-eb3EqEoJbc7cN7dkPR5QXhqJNezMW1UkY-eiBeEFCTDKFsi6rXWvehZLsOaXYugWL2Uttmq_4tvLuuAfzLniJnNsGPl7jGuN1I8nKk1Cr8HFdkUuk9wy5QWnPjUeswG0rYiSTkLzOXsUmS4J3j2mFzk1nEDg3RQj9CLv1ceUfaLLM1GLQ_ScL1_k_NAx7zgiIDr4WrC6BxbfkCgv8Az4TnaGBVZfvs4D647Opz3h036WlzycPtSBpD-8AURzJdCsBFvrufUCCRNnKCv_TevNno_aV "Biểu đồ UML")

### 3. **Biểu đồ trạng thái**

![Biểu đồ](https://www.planttext.com/plantuml/png/FOwn2W8n44Jx_OebfN0_O25tXQqSg9LOBDa5Wxb4TdFA_Rs9fnO3mxnNJ6-5jCnJ1B1xIAZP100kcojstGuFyeAQJpy_c8emRj4DpBXFHHS7lxKPHtgkl1KyXKayAJjOzsOCwc_XAusqQ8uHHyrUpAIAVzpS-W6WbyJrtHi0 "Biểu đồ trạng thái") 
