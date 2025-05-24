Khi bạn gặp lỗi "Docker is turning off" hoặc Docker tự động tắt ngay sau khi mở, có thể do một số nguyên nhân phổ biến. Dưới đây là các bước kiểm tra và khắc phục:

---

### 🚀 **1. Kiểm tra cấu hình hệ thống**

Docker Desktop yêu cầu:

* **Windows 10 64-bit: Pro, Enterprise, hoặc Education (bản Home cần dùng WSL2).**
* **Enable Virtualization trong BIOS.**
* **Enable Hyper-V và WSL2.**

#### 👉 Cách kiểm tra nhanh:

* Mở `Task Manager` → tab `Performance` → xem mục **Virtualization** có đang "Enabled" không.
* Chạy lệnh sau trong PowerShell (Admin):

```powershell
systeminfo | findstr /i "Virtualization"
```

---

### 🛠 **2. Kiểm tra WSL2 (với bản Windows Home)**

Docker sử dụng WSL2 để hoạt động.

* Chạy lệnh sau để xem phiên bản WSL:

```powershell
wsl --list --verbose
```

* Nếu WSL chưa là v2 hoặc Ubuntu chưa được cài:

```powershell
wsl --set-default-version 2
```

* Tải Ubuntu từ Microsoft Store (nếu chưa có) và khởi chạy một lần.

---

### 🔧 **3. Bật các tính năng cần thiết**

Mở PowerShell với quyền Admin và chạy:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V-All /all /norestart
```

Sau đó **khởi động lại máy**.

---

### 📦 **4. Kiểm tra Docker logs**

* Mở Docker Desktop → Help → Troubleshoot → View log file.
* Hoặc mở file log tại:

```
%APPDATA%\Docker\log\host-com.docker.service.log
```

Tìm các lỗi như:

* "WSL kernel not found"
* "Timeout while connecting to Docker engine"

---

### 🔄 **5. Cài lại Docker**

Nếu lỗi vẫn tiếp diễn:

* Gỡ Docker Desktop hoàn toàn.
* Xoá thư mục cấu hình cũ:

  * `%APPDATA%\Docker`
  * `%LOCALAPPDATA%\Docker`
  * `%USERPROFILE%\.docker`

Sau đó, tải lại phiên bản mới nhất từ: [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

---

### ✅ Nếu vẫn lỗi: Bạn hãy cung cấp thêm:

1. Bạn đang dùng **Windows bản nào** (Home, Pro...)?
2. Docker phiên bản mấy?
3. Máy đã bật WSL2, Hyper-V chưa?
4. Ảnh chụp lỗi hoặc log lỗi nếu có.

Mình sẽ hỗ trợ chi tiết hơn theo tình huống cụ thể của bạn.
