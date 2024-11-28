### **1. Subsystem Context Diagrams**

![Subsystem Context Diagram](https://www.planttext.com/api/plantuml/png/RD71IWCn40RWUvvYoBqKFNgGRjIAjzBYgVGmtHsgD9kiCxEWI9-i1n_9Lp3T3QiGSyl_3ry6ydt-MeWYQzzw8yVNq25Z2qorOZXuWay3wJYiZmUEVMZkeeyCA_Jqo4HXR2Ctn6FZV1eTqcKC-ZSx6VFBsis7ABLGMK21AZ-ptVHxoSNLheYkT_yZRa1SYRWISGNoyAx40JsCcWpO56PpkbUhfspUe-8UXGQlWjdiDgrm0tPDRps9pjSaNGn2DfSJaMQMfFKBN0HhND5USdZk6bGIQyo2GfE-vmS00F__0m00)

#### **Giải thích:**
- **Subsystem Context Diagram** minh họa cách các thành phần (subsystems) tương tác với nhau và với các hệ thống bên ngoài.
- **Các thành phần chính:**
  - `System A` và `System B`: Hai hệ thống chính với các subsystems A1, A2, B1, B2.
  - `External Systems`: Bao gồm các hệ thống bên ngoài như API hoặc cơ sở dữ liệu.
- **Quan hệ:**
  - **A --> B**: `System A` gửi yêu cầu và nhận phản hồi từ `System B`.
  - **A --> External**: `System A` tương tác với hệ thống bên ngoài để lấy dữ liệu.
  - **B --> External**: `System B` gửi dữ liệu đã xử lý đến hệ thống ngoài (ví dụ: cập nhật cơ sở dữ liệu).

---

### **2. Analysis Class to Design Element Map**

![Analysis Class to Design Element Map](https://www.planttext.com/api/plantuml/png/DCwn3e9030RW_PwYkKa71jOR30GOcNo20WqsEGv2YuanFfc3Z-GhU81qQl-aN_jzVp9Hd7KPl6azYe3D0_g7i42npXPG82_WQM0jL9svMPHI1zVOXdxF1zBRsAMditcP0of9k0zGUHeew0QLrHzAffdlg9GVdWCEkblJqdXkwqtSmNW_IIxhjWDRuoIWepKPXIx-_GC00F__0m00)

#### **Giải thích:**
- **Analysis Class**:
  - Là lớp trong giai đoạn phân tích, mô tả các yêu cầu chức năng cơ bản.
  - Ví dụ: Có thuộc tính `attribute1` và phương thức `method1()`.
- **Design Element**:
  - Lớp cụ thể hóa từ Analysis Class, triển khai các chức năng chi tiết hơn.
  - Ví dụ: Bao gồm `privateAttribute` và `publicMethod()`.
- **Quan hệ**: `AC --> DE` chỉ ra rằng Analysis Class ánh xạ (maps to) thành một Design Element.

---

### **3. Design Element to Owning Package Map**

![Design Element to Owning Package Map](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bT1Od9sOdggWf9pVb6gGW24fwHGpQK01CavYSN52aekgSMPwNaAhZcfkQbv9Gg6IWg9nGekhePur1X1rHXnrN8Xx0WjoSp9BAd4OOr7Qav1Qf62CuW7rkxX3D8Dj4X1LzSEo5Em0XfHd5gi11GpGX9pIIr8pKifLiZFK-9o0BA0_W80003__mC0)

#### **Giải thích:**
- **Package**:
  - Tập hợp các lớp (classes) theo chức năng cụ thể.
  - Ví dụ: 
    - **Core Package** chứa các lớp chính (`Design Element 1` và `Design Element 2`).
    - **Utility Package** chứa lớp hỗ trợ (`Helper Class`).
- **Quan hệ**:
  - `DE1 --> HC`: `Design Element 1` sử dụng `Helper Class` để thực hiện chức năng (ví dụ: tính toán).
  - `DE2 --> HC`: `Design Element 2` phụ thuộc vào `Helper Class`. Nếu Helper Class thay đổi, DE2 cũng bị ảnh hưởng.

---

### **4. Architectural Layers and Their Dependencies**

![Architectural Layers and Their Dependencies](https://www.planttext.com/api/plantuml/png/Z9F1JeD048Rl-nGJxho0QKWnUcZIGsFrP3YCsv5k2hkuiwZ4zCay-4Y-WWj5e1ICUzhmppV_x3_X-_DhoGwjA_DCy45fi8P9Y0Bb0LE2O8qLMGxWGu0_tUUuA38bqIcZ0rWiihegYjgg-Zm-C5bOQKVs6IKbq2i35jOcLJ9fjACujxWkMMbYXYtPLoM9Puowka6lHcYvVWYUDhf1Xn1BhyzPD1LtL1XMpjWgELUUaAdbfmrkt_q06ZFOLkmedtEvtokx2pT-6LNtve5Ll5cTzx-8E0oZgNJX2aec5ZFXdx1HYfwHc6KjD1OROYBUcZ9vNkhQWHZUbDkBkLsSkeoZzIrUIhBgTzuBlQE6iNiAcnlzDV5am1vLzL0etRy6RjRGGgdjdtaKIzAx-ZVw0G00__y30000)

#### **Giải thích:**

- **User Interface**: 
  - Sử dụng **Application Logic** để thực hiện các chức năng của hệ thống.
  
- **Application Logic**: 
  - Gọi đến **Business Logic** để xử lý các yêu cầu nghiệp vụ.
  
- **Business Logic**: 
  - Giao tiếp với **Service Interfaces** để nhận và gửi dữ liệu.
  
- **Service Interfaces**: 
  - Thực hiện các truy vấn đến **Data Repository** để truy xuất dữ liệu.
  
- **Data Repository**: 
  - Tương tác với **Database Access** để lưu trữ và lấy dữ liệu.
  
- **Business Logic**: 
  - Có thể tương tác với **Third-Party Services** và **APIs** để mở rộng chức năng của hệ thống.
