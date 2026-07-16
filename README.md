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

``` 
Here's the English version with a style placeholder:


**Prompt:**

Create a landing page to be used as a browser homepage, in a single HTML file (HTML, CSS, and JavaScript only — no frameworks, no external CDNs).

**Style / Theme:**
[ INSERT YOUR DESIRED STYLE HERE — e.g. color palette, dark/light mode, typography, overall visual mood, any signature visual element like a background animation ]

**Requirements:**
- Responsive, works well on both desktop and mobile
- Loads fast and works offline (except parts that genuinely require internet, like favicons)
- All data persisted with LocalStorage under a single namespaced key
- Clean, readable code structure with comments explaining key sections
- Clicking/opening any link (Bookmark, Quick URL, Search) navigates in the same tab — never opens a new tab

**Features:**

1. **Bookmark Manager**
   - Displayed as a card grid, click to open in the same tab
   - Add / edit / delete bookmarks
   - Drag & drop to reorder
   - Favicon fetched automatically from the DuckDuckGo Favicon API (`icons.duckduckgo.com/ip3/{domain}.ico`), with a fallback to the bookmark's first letter if it fails to load
   - Starts empty — no sample/default bookmarks included

2. **Categories**
   - Add / delete / rename categories via a management modal
   - Starts with a single category called "Other" as a permanent fallback — it cannot be deleted or renamed
   - Deleting a category that has bookmarks in it moves those bookmarks to "Other" automatically, with a confirmation prompt first
   - Filter tabs above the bookmark grid, each showing a count

3. **Quick URL**
   - Paste a link and press Enter or a button to save it; supports adding unlimited entries
   - List shows newest first, each with its favicon
   - Click an entry to open it in the same tab; hover to reveal a delete button per item

4. **Command Palette**
   - Opens with Ctrl+K (Cmd+K on Mac)
   - Real-time search across bookmarks (by name, URL, or category)
   - Arrow keys ↑↓ to navigate, Enter to open in the same tab, Esc to close
   - If no bookmark matches, pressing Enter falls back to a Google search (same tab)

5. **Statistics Panel**
   - Total bookmark count
   - Total category count
   - Current time (real-time, updating)
   - Total saved Quick URLs

6. **Backup (Export / Import)**
   - Export all data (bookmarks, categories, Quick URLs) as a downloadable .json file with the date in the filename
   - Import a previously exported .json file, with structure validation and a confirmation prompt before overwriting existing data
   - Gracefully handles older backup files missing newer fields (fills in sensible defaults instead of erroring)

7. **Reset Data**
   - A "reset all data" button that requires typing a confirmation word (e.g. "RESET") before actually wiping data — to prevent accidental clicks

**Quality:**
- Good accessibility (aria-labels, keyboard navigation, visible focus rings)
- Everything lives in a single index.html file, no external libraries
- Works immediately when the file is opened in a browser

**Note:** Do not include a Header section (dashboard title/clock/greeting) and do not include a separate Universal Search section.


```