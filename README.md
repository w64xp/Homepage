# Personal Dashboard — Browser Homepage

Single-file HTML homepage สำหรับตั้งเป็นหน้าแรกของเบราว์เซอร์ ทำงานแบบ dark dashboard ส่วนตัว ไม่ใช้ Framework หรือ CDN ภายนอกใดๆ — เปิดไฟล์ `index.html` ได้ทันที ทำงาน offline ได้ 100% (ยกเว้นส่วน favicon และ Google Search ที่ต้องใช้อินเทอร์เน็ต)

## เริ่มใช้งาน

1. ดาวน์โหลด `index.html`
2. ตั้งเป็นหน้า Homepage / New Tab ของเบราว์เซอร์ (หรือเปิดไฟล์ตรงๆ ก็ได้)
3. ใช้งานได้เลย ไม่ต้องติดตั้งอะไรเพิ่ม

**ตั้งเป็นหน้า New Tab:**
- **Chrome/Edge**: ต้องใช้ Extension ช่วย (เช่น "Custom New Tab URL") เพราะเบราว์เซอร์ไม่อนุญาตให้ตั้ง local file เป็น New Tab โดยตรง
- **Firefox**: `about:preferences` → Home → New Windows and Tabs → Custom URLs → ใส่ path แบบ `file:///C:/path/to/index.html`

## ฟีเจอร์

### Header
- ชื่อ Dashboard พร้อมคำทักทายที่เปลี่ยนตามช่วงเวลาในวัน
- นาฬิกาเรียลไทม์ (อัปเดตทุกวินาที) พร้อมวันที่แบบไทย (พ.ศ.)

### Universal Search
- ช่องค้นหาขนาดใหญ่ กด **Enter** เพื่อค้นหาผ่าน Google
- ถ้าพิมพ์เป็น URL (เช่น `youtube.com`) จะเปิดลิงก์ตรงแทนการค้นหา
- กด **Ctrl+K** (หรือ Cmd+K บน Mac) เพื่อเปิด Command Palette

### Bookmark Manager
- แสดงเป็น Card Grid, คลิกเพื่อเปิดในแท็บใหม่
- **เพิ่ม / แก้ไข / ลบ** ได้ผ่านปุ่มและ modal
- **Drag & Drop** เพื่อจัดเรียงลำดับใหม่
- Favicon ดึงอัตโนมัติจาก **DuckDuckGo Favicon API** (`icons.duckduckgo.com`) — เจาะจงกว่าโลโก้แบรนด์แม่ ถ้าโหลดไม่ได้จะ fallback เป็นตัวอักษรแรกของชื่อ
- เริ่มต้นเป็น **หน้าว่างเปล่า** ไม่มี Bookmark ตัวอย่างติดมาด้วย

### Categories (หมวดหมู่)
- **เพิ่ม / ลบ / เปลี่ยนชื่อ** หมวดหมู่ได้ทั้งหมด ผ่านปุ่ม "หมวดหมู่" ข้างปุ่มเพิ่ม Bookmark
- หมวด **"Other"** เป็นหมวด fallback ถาวร — ลบหรือเปลี่ยนชื่อไม่ได้
- ลบหมวดหมู่ที่มี Bookmark อยู่ → Bookmark จะถูกย้ายไปที่ "Other" อัตโนมัติ ไม่มีข้อมูลหาย
- แท็บกรองหมวดหมู่อยู่เหนือ Bookmark grid พร้อมตัวนับจำนวน

### Quick URL
- วางลิงก์ในช่อง แล้วกด **Enter** หรือปุ่ม **+** เพื่อบันทึก
- เพิ่มได้หลายรายการไม่จำกัด แสดงใหม่สุดไว้บนสุด
- คลิกที่รายการเพื่อเปิดลิงก์ในแท็บใหม่ทันที, โฮเวอร์แล้วกด ✕ เพื่อลบ

### Command Palette (Ctrl+K)
- ค้นหา Bookmark แบบเรียลไทม์ (ค้นจากชื่อ, URL, หมวดหมู่)
- ใช้ลูกศร **↑ / ↓** เลือก, กด **Enter** เพื่อเปิด, **Esc** เพื่อปิด
- ถ้าพิมพ์แล้วไม่เจอ Bookmark ที่ตรงกัน กด Enter จะค้นหาผ่าน Google แทน

### Statistics Panel
- จำนวน Bookmark ทั้งหมด
- จำนวนหมวดหมู่
- เวลาปัจจุบัน
- จำนวน Quick URL ที่บันทึกไว้

### Backup (Export / Import)
- **Export**: ดาวน์โหลดข้อมูลทั้งหมด (Bookmark, หมวดหมู่, Quick URL) เป็นไฟล์ `.json` พร้อมวันที่ในชื่อไฟล์
- **Import**: เลือกไฟล์ `.json` ที่เคย export ไว้เพื่อกู้คืน — มีการตรวจสอบโครงสร้างไฟล์และ popup ยืนยันก่อนแทนที่ข้อมูลเดิม
- รองรับไฟล์ backup รุ่นเก่าที่ยังไม่มีฟีเจอร์ Quick URL (จะเติมค่าว่างให้อัตโนมัติ)

### รีเซ็ตข้อมูล
- ปุ่ม "รีเซ็ตข้อมูลทั้งหมด" อยู่ใน Danger Zone ใต้พาเนล Backup
- ต้องพิมพ์คำว่า **RESET** เพื่อยืนยัน ป้องกันการกดพลาด (ข้อมูลลบแล้วกู้คืนไม่ได้ถ้าไม่มีไฟล์ backup)

### Background Animation
- Canvas animation แบบ node network เบาๆ (constellation) ลอยตัวช้าๆ พร้อมเส้นเชื่อมจุดที่อยู่ใกล้กัน
- จำกัดจำนวนอนุภาคและ devicePixelRatio เพื่อไม่ให้กินทรัพยากรเครื่อง
- หยุดทำงานอัตโนมัติเมื่อสลับไปแท็บอื่น (`visibilitychange`)
- เคารพการตั้งค่า `prefers-reduced-motion` ของระบบปฏิบัติการ (จะวาดเฟรมนิ่งเฟรมเดียวแทน)

## การเก็บข้อมูล

ข้อมูลทั้งหมดเก็บใน **`localStorage`** ของเบราว์เซอร์ ภายใต้ key เดียว:

```
homepage_dashboard_v1
```

โครงสร้างข้อมูล (โดยประมาณ):

```json
{
  "categories": ["Other", "Study", "..."],
  "bookmarks": [
    { "id": "bm_...", "name": "Gmail", "url": "https://mail.google.com/", "category": "Other", "order": 0 }
  ],
  "quickUrls": [
    { "id": "qu_...", "url": "https://example.com", "createdAt": 1234567890 }
  ],
  "activeCategory": "all"
}
```

**ดูข้อมูลตรงๆ ผ่าน Console:**
```javascript
JSON.parse(localStorage.getItem('homepage_dashboard_v1'))
```

**ลบข้อมูลทั้งหมดผ่าน Console** (แทนการกดปุ่มรีเซ็ตในแอป):
```javascript
localStorage.removeItem('homepage_dashboard_v1');
location.reload();
```

> ⚠️ ข้อมูลผูกกับ **origin ของไฟล์** — ถ้าย้ายไฟล์ไปเปิดจากตำแหน่งอื่น หรือเปิดผ่านเบราว์เซอร์/โปรไฟล์คนละตัว จะไม่เห็นข้อมูลเดิม เพราะ `localStorage` แยกตาม origin

## คีย์ลัด (Keyboard Shortcuts)

| คีย์ | การทำงาน |
|---|---|
| `Ctrl+K` / `Cmd+K` | เปิด/ปิด Command Palette |
| `Enter` (ในช่องค้นหา) | ค้นหาผ่าน Google หรือเปิด URL |
| `↑` `↓` (ใน Command Palette) | เลื่อนเลือกรายการ |
| `Enter` (ใน Command Palette) | เปิดลิงก์ที่เลือก |
| `Esc` | ปิด modal / palette ที่เปิดอยู่ |

## ข้อจำกัดที่รู้อยู่แล้ว

- **ไม่สามารถดึงชื่อโปรไฟล์เบราว์เซอร์มาแสดงได้** เพราะเป็นข้อมูลระดับ OS ที่ JavaScript หน้าเว็บเข้าถึงไม่ได้ ด้วยเหตุผลด้านความเป็นส่วนตัว/ความปลอดภัย
- Favicon และ Google Search ต้องใช้อินเทอร์เน็ต — ส่วนอื่นทั้งหมดทำงาน offline ได้
- ข้อมูลไม่ sync ข้ามเครื่อง/เบราว์เซอร์ (เพราะเก็บใน localStorage) — ใช้ฟีเจอร์ Export/Import เพื่อย้ายข้อมูลเอง

## โครงสร้างไฟล์

```
index.html   ← ไฟล์เดียวจบ (HTML + CSS + JavaScript ทั้งหมดอยู่ในนี้)
```

ไม่มี dependency ภายนอก ไม่มี build step ไม่ต้องใช้ npm/node — เปิดไฟล์ในเบราว์เซอร์ได้ทันที