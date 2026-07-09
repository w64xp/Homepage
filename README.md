# Personal Dashboard

แดชบอร์ดส่วนตัวสำหรับจัดการ Bookmark และลิงก์สำคัญ พร้อมระบบค้นหา, หมวดหมู่, Quick URL, Backup/Restore และ Command Palette ในหน้าเดียว

## Features

### 🔖 Bookmark Manager

* เพิ่ม แก้ไข และลบ Bookmark
* จัดหมวดหมู่ Bookmark ได้
* ลากและวาง (Drag & Drop) เพื่อจัดลำดับ
* แสดง Favicon อัตโนมัติ
* เปิดเว็บไซต์ในแท็บใหม่

### 📂 Category Management

* สร้างหมวดหมู่ใหม่
* เปลี่ยนชื่อหมวดหมู่
* ลบหมวดหมู่
* ย้าย Bookmark ไปยังหมวดหมู่สำรองอัตโนมัติเมื่อหมวดหมู่ถูกลบ

### 🔍 Universal Search

* ค้นหาผ่าน Google ได้ทันที
* รองรับการเปิด URL โดยตรง
* ตรวจจับ URL อัตโนมัติ

### ⚡ Command Palette

* เปิดด้วย `Ctrl + K`
* ค้นหา Bookmark อย่างรวดเร็ว
* เปิดเว็บไซต์จากคีย์บอร์ดได้ทันที
* รองรับ Navigation ด้วย Arrow Keys

### 🌐 Quick URL

* วางลิงก์แล้วบันทึกได้ทันที
* เปิดลิงก์ด้วยคลิกเดียว
* จัดเก็บรายการลิงก์สำคัญแยกจาก Bookmark

### 💾 Backup & Restore

* Export ข้อมูลทั้งหมดเป็นไฟล์ JSON
* Import ข้อมูลกลับเข้าระบบ
* สำรองข้อมูล Bookmark, Categories และ Quick URLs

### 📊 Dashboard Statistics

* จำนวน Bookmark ทั้งหมด
* จำนวนหมวดหมู่
* เวลาปัจจุบัน
* จำนวน Quick URLs

### 🕒 Live Clock

* แสดงเวลาปัจจุบันแบบ Real-time
* แสดงวันที่ภาษาไทย
* Greeting เปลี่ยนตามช่วงเวลา

### 🎨 Modern UI

* Dark Theme
* Responsive Design
* Animated Background
* Accessibility Support
* Keyboard Shortcuts

---

## Data Storage

ข้อมูลทั้งหมดถูกจัดเก็บใน Local Storage ของ Browser

Key ที่ใช้:

```text
homepage_dashboard_v1
```

โครงสร้างข้อมูล:

```json
{
  "categories": [],
  "bookmarks": [],
  "quickUrls": [],
  "activeCategory": "all"
}
```

---

## Keyboard Shortcuts

| Shortcut | Action                   |
| -------- | ------------------------ |
| Ctrl + K | เปิด/ปิด Command Palette |
| Enter    | เปิด Bookmark ที่เลือก   |
| Esc      | ปิด Modal หรือ Palette   |
| ↑ ↓      | เลื่อนรายการใน Palette   |

---

## Installation

1. ดาวน์โหลดไฟล์ `index.html`
2. เปิดด้วย Web Browser
3. เริ่มใช้งานได้ทันที

หรือรันผ่าน Local Server:

```bash
python -m http.server 8000
```

แล้วเปิด:

```text
http://localhost:8000
```

---

## Technologies Used

* HTML5
* CSS3
* Vanilla JavaScript
* LocalStorage API
* Canvas API

---

## Browser Support

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Brave
* Opera

---

## License

This project is provided for personal and educational use.
