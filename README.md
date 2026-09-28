# Device F/U Form

Web form (Medtronic Pacemaker / ICD / CRT / CRT-D follow-up) ที่อ่านค่าจาก PDF แล้วกรอกให้อัตโนมัติ
Export ได้เป็น PDF, PNG, Text

## วิธีขึ้น GitHub Pages

1. สร้าง repo ใหม่บน GitHub (เช่น `fu-form`)
2. กด **Add file → Upload files** แล้วลาก `index.html` และ `README.md` เข้าไป → **Commit changes**
3. ไปที่ **Settings → Pages**
4. ที่ *Build and deployment* เลือก **Deploy from a branch**, Branch = `main`, Folder = `/ (root)` → **Save**
5. รอ 1–2 นาที ได้ลิงก์ `https://<username>.github.io/fu-form/`

ใช้งานในเครื่องก็ได้: ดับเบิลคลิก `index.html` (ต้องต่ออินเทอร์เน็ต เพราะโหลด pdf.js / html2canvas / jsPDF จาก CDN)

## การใช้งาน

- กด **Upload PDF** → ระบบอ่านและกรอกฟอร์ม; หรือพิมพ์ในช่องเองได้ทุกช่อง
- `-` = ไม่พบค่า, `?` หรือช่องสีส้ม = ไม่แน่ใจ (ควรตรวจกับ PDF)
- ช่อง Episode ด้านล่างพิมพ์แก้ไข/เพิ่ม note ได้
- ประเภท Pacemaker / ICD / CRT / CRT-D: ถ้าอ่านไม่ได้ ให้คลิกเลือกเอง
- ข้อมูลประมวลผลในเบราว์เซอร์ทั้งหมด ไม่มีการอัปโหลดไฟล์ผู้ป่วยไปที่ server

## ปรับ rule การอ่านค่า

Regex ทั้งหมดอยู่ในฟังก์ชัน `extract()` และ `sections()` ใน `index.html`
PDF ของแต่ละรุ่น/รุ่นซอฟต์แวร์ layout ต่างกัน ถ้าช่องไหนอ่านผิด ให้ปรับ regex ของช่องนั้น
(PDF ต้องเป็นแบบมี text ไม่ใช่รูปสแกน)
