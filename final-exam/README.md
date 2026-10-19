# Playwright Final Exam

ระบบที่ทดสอบ: [SauceDemo](https://www.saucedemo.com/)

## รายละเอียดผู้ส่ง

- รหัสนักศึกษา: `ใส่รหัสนักศึกษา`
- ชื่อ-นามสกุล: `ใส่ชื่อและนามสกุล`
- GitHub Repository: `https://github.com/USERNAME/final-student-id`

ก่อนส่ง ให้เปลี่ยน `student-id`, `USERNAME` และข้อมูลผู้ส่งให้เป็นข้อมูลจริง ตั้งชื่อ repository เป็น `final-รหัสนักศึกษา` และเพิ่มผู้สอนเป็น collaborator หาก repository เป็น private

## โครงสร้าง

- `tests/unit/UT-01.spec.ts`: ตรวจสอบ validation ของ Login Form 3 กรณี
- `tests/unit/UT-02.spec.ts`: ตรวจสอบสถานะ Add to cart, Remove และ Cart Badge
- `tests/integration/IT-01.spec.ts`: Top-Down โดย Login ผ่าน SauceDemo จริง แล้วแทนเนื้อหาใน browser ด้วย Inventory Stub ผ่าน `page.setContent()`
- `tests/integration/IT-02.spec.ts`: Bottom-Up โดย Driver เพิ่ม `session-username` cookie และเปิด Inventory จริงโดยตรง จากนั้นทดสอบ Cart จริง
- `tests/system/ST-01.spec.ts`: ซื้อ Backpack และ Bike Light จนสำเร็จ
- `tests/system/ST-02.spec.ts`: ตรวจสอบ validation ของ Checkout และแก้ไขข้อมูลจนสั่งซื้อสำเร็จ

IT-01 ใช้ระบบจริงเฉพาะการ Login และตรวจ URL ก่อนจำลอง DOM ของ Inventory ระดับ browser; Stub ไม่ได้แทน internal module ของ SauceDemo ส่วน IT-02 ใช้ Driver เตรียม session cookie ขณะที่ Inventory และ Shopping Cart เป็นหน้าและการทำงานจริงของ SauceDemo

## ติดตั้งและรันทดสอบ

```powershell
npm install
npx playwright install chromium
npx playwright test
```

Reporter จะบันทึก HTML Report ที่ `playwright-report/` และ JSON Report ที่ `reports/results.json` แม้บาง test จะ fail ให้ใช้ผลที่รันจริงสร้างสรุปใน `reports/test-summary.md` ห้ามแก้ผลรายงานด้วยตนเอง

ดูรายงาน HTML ด้วย:

```powershell
npx playwright show-report
```

## ส่งงาน

หลังรันทดสอบ ให้ตรวจสอบ source code และรายงาน จากนั้น commit รวม `playwright-report/` และ `reports/` ไปยัง repository `final-รหัสนักศึกษา` และส่ง GitHub Repository URL เพียง 1 ลิงก์