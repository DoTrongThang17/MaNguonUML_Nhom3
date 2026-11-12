# 🎵 Nhóm 11 — Ứng dụng Nghe Nhạc Di Động

**Sóng** là ứng dụng nghe nhạc trên thiết bị di động lấy cảm hứng từ **SoundCloud**, được phát triển bằng **Flutter**. Dự án tập trung vào trải nghiệm tương tác âm nhạc trực quan thông qua thanh sóng âm (Waveform) và hệ thống bình luận theo mốc thời gian thực của bài hát (Timed Comments).

---

## 📋 Thông tin môn học & Nhóm thực hiện

- **Trường:** Đại học Phenikaa
- **Môn học:** Lập trình cho thiết bị di động (`2026_2027_1_1_LTTBDD_N02_Nhom_11`)
- **Lớp:** N02 · **Nhóm:** 11
- **Giảng viên hướng dẫn:** Nguyễn Xuân Quế

| STT | Họ và tên | Mã sinh viên | Vai trò & Nhiệm vụ chính |
| :---: | :--- | :---: | :--- |
| 1 | **Đỗ Trọng Thắng** | `24100316` | **Nhóm trưởng** · Kiến trúc dự án, trình phát nhạc (`just_audio`), Waveform & Timed Comments |
| 2 | **Nguyễn Anh Tuấn** | `24100400` | Thiết kế UI/UX, Trang chủ (Feed), Trang nghệ sĩ & Bảng xếp hạng |
| 3 | **Nguyễn Thế Tuấn** | `24100315` | Quản lý thư viện (Playlist, Yêu thích), Tìm kiếm, Đa ngôn ngữ & Giao diện Sáng/Tối |

---

## ✨ Tính năng nổi bật

### 🔥 Điểm nhấn đặc trưng (SoundCloud-inspired)
- **Thanh sóng âm (Waveform):** Hiển thị biên độ âm thanh trực quan, hỗ trợ chạm/vuốt trực tiếp trên sóng âm để tua nhanh tới vị trí mong muốn.
- **Bình luận theo thời điểm (Timed Comments):** Cho phép người dùng để lại bình luận gắn với từng giây cụ thể của bài hát và hiển thị đồng bộ theo thời gian thực khi nhạc phát tới mốc đó.

### 🎧 Trình phát nhạc & Tiện ích
- Phát nhạc cục bộ (`assets`) mượt mà với đầy đủ điều khiển: Phát / Tạm dừng, Bài trước / Bài sau và **Mini Player** xuyên suốt toàn bộ ứng dụng.
- Tùy chỉnh tốc độ phát (`0.5x` – `2.0x`) và điều chỉnh âm lượng trực tiếp.
- Hẹn giờ tắt nhạc tự động (Sleep Timer) với các mốc: `1`, `15`, `30`, `45`, `60` phút.

### 🔍 Khám phá & Cá nhân hóa
- **Trang chủ & Feed:** Gợi ý bài hát, duyệt nhạc theo thể loại và trang chi tiết nghệ sĩ (hỗ trợ sắp xếp theo *Phổ biến / Mới nhất / A-Z*).
- **Bảng xếp hạng:** Thống kê top bài hát theo 3 tiêu chí: *Nghe nhiều nhất / Yêu thích nhất / Nhiều bình luận nhất*.
- **Quản lý thư viện:** Thích bài hát, theo dõi nghệ sĩ, tạo/đổi tên/xóa Playlist cá nhân và tính năng tải lên bài hát (giả lập).
- **Tìm kiếm thông minh:** Tìm kiếm nhanh bài hát/nghệ sĩ kèm lưu trữ lịch sử tìm kiếm cục bộ.

### ⚙️ Hệ thống
- Chuyển đổi linh hoạt **Giao diện Sáng / Tối** (Light / Dark Mode).
- Hỗ trợ **Đa ngôn ngữ**: Tiếng Việt 🇻🇳 / English 🇬🇧.
- Tích hợp trang thông tin nhóm thực hiện ngay trong phần cài đặt ứng dụng.

---

## 🏗️ Kiến trúc & Công nghệ

### Tech Stack & Thư viện
- **Framework & Ngôn ngữ:** Flutter SDK & Dart
- **Xử lý âm thanh:** [`just_audio`](https://pub.dev/packages/just_audio) — Quản lý luồng phát nhạc, điều chỉnh tốc độ phát và trạng thái trình phát.
- **Lưu trữ cục bộ:** [`shared_preferences`](https://pub.dev/packages/shared_preferences) — Lưu lịch sử tìm kiếm, cấu hình giao diện Sáng/Tối và tùy chọn ngôn ngữ.
- **Đồ họa trực quan:** Custom Canvas (`CustomPainter`) vẽ thanh sóng âm tương tác.

### Cấu trúc thư mục

```text
2026_2027_1_1_LTTBDD_N02_Nhom_11/
├── assets/
│   ├── audio/                  # Kho tệp âm thanh mẫu (.mp3)[cite: 2, 8]
│   └── imgs/                   # Ảnh bìa bài hát, avatar nghệ sĩ[cite: 2, 8]
├── lib/
│   ├── main.dart               # Điểm khởi chạy ứng dụng[cite: 1]
│   ├── models/                 # Các lớp dữ liệu (Song, Artist, Playlist, Comment...)[cite: 1, 2]
│   ├── screens/                # Toàn bộ giao diện các màn hình[cite: 1]
│   │   ├── main_screen.dart    # Điều hướng chính (BottomNavigationBar)[cite: 1]
│   │   ├── home/               # Màn hình Trang chủ[cite: 1]
│   │   ├── feed/               # Màn hình Bảng tin (Feed)[cite: 1]
│   │   ├── genre/              # Duyệt nhạc theo thể loại[cite: 1]
│   │   ├── artist/             # Chi tiết nghệ sĩ[cite: 1]
│   │   ├── charts/             # Bảng xếp hạng[cite: 1]
│   │   ├── player/             # Trình phát nhạc chi tiết & bình luận[cite: 1]
│   │   ├── playlist/           # Quản lý danh sách phát[cite: 1]
│   │   ├── library/            # Thư viện cá nhân[cite: 1]
│   │   ├── search/             # Tìm kiếm & lịch sử tìm kiếm[cite: 1]
│   │   ├── upload/             # Tải lên bài hát (giả lập)[cite: 1]
│   │   └── settings/           # Cài đặt giao diện, ngôn ngữ & thông tin nhóm[cite: 1]
│   ├── services/               # Xử lý âm thanh (AudioService) & dữ liệu (DataService)[cite: 1, 2]
│   ├── theme/                  # Cấu hình giao diện Sáng / Tối (Light / Dark Mode)[cite: 1]
│   └── widgets/                # Thành phần dùng chung (Waveform, SongTile...)[cite: 1]
└── pubspec.yaml                # Khai báo thư viện và tài nguyên[cite: 2]
