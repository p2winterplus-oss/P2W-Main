# P2W INTERPLUS — หน้าหลัก (Main Hub)

## Architecture รวม
ดู `C:\Users\witta\OneDrive\Claude AI Backup\P2W-ARCHITECTURE.md`

## โปรเจกต์นี้คืออะไร
Entry point ของ P2W INTERPLUS ทั้งหมด — ลูกค้าเข้ามาแล้วเลือก service ที่ต้องการ ไม่มีรายละเอียดเชิงลึก หน้าย่อยแต่ละอันดูแลเอง

- **Live URL**: https://p2winterplus.com (รอซื้อโดเมน)
- **GitHub Pages**: https://p2winterplus-oss.github.io/P2W-Main/ (hosting ปัจจุบัน)
- **Repo**: https://github.com/p2winterplus-oss/P2W-Main ✅
- **Hosted**: GitHub Pages
- **Stack**: HTML + Tailwind CSS CDN + Vanilla JavaScript (single file: index.html)

## Design System
- **Primary color**: Gold `#D4AF37`
- **Dark bg**: `#0B1120` / **Light bg**: `#F9F8F6`
- **Font**: Prompt (body)
- **Style**: Luxury dark accordion hub — slanted expanding panels with background images
- **Dark/Light mode toggle**: localStorage (`color-theme`) — default = dark

## โครงสร้างหน้า (ปัจจุบัน)
1. **Navbar** — Logo (logo.png) + dark mode toggle — centered logo, toggle ขวา
2. **Hero** — "Welcome to The Hub" + headline + คำอธิบาย
3. **Accordion Hub** — 6 panels เรียงแนวนอน (desktop) / แนวตั้ง (mobile) พร้อม animated border
4. **Footer** — Logo + Branding + Contact + Social links + hidden admin trigger

## Logo
- ไฟล์: `logo.png`
- Dark mode: pulse outer stroke animation (gold, 1px, 5s) ใช้ CSS `drop-shadow` 8 ทิศทาง
- CSS class: `logo-strobe` (ใช้ทั้ง navbar และ footer)

## Accordion Hub Border (Light/Dark)
- **Outer wrapper**: `bg-[#1E293B]` (light) / `bg-gray-800` (dark) — dark slate ทำให้เห็นกรอบชัดใน light mode
- **Inner container**: `bg-gray-50` (light) / `bg-gray-800` (dark)
- **Animated spark**: CSS class `.hub-spark`
  - Dark mode: gold trail + white tip
  - Light mode (`:not(.dark) .hub-spark`): deep amber trail + bright gold tip (ไม่ใช้ white เพราะกลืนกับพื้น)

## Links ไปแต่ละ Service (URL ปัจจุบัน — GitHub Pages)
| Service | URL ปัจจุบัน | หมายเหตุ |
|---------|-------------|---------|
| วิศวกรรม | `https://p2winterplus-oss.github.io/P2W-Engineer/#home` | เปลี่ยนเมื่อซื้อโดเมน |
| ที่ปรึกษาการตลาด | `https://p2winterplus-oss.github.io/P2W-Consult/` | เปลี่ยนเมื่อซื้อโดเมน |
| ขายสินค้า | `/shop` | ยังไม่มีหน้า |
| คอนเทนต์/อินฟลูเอนเซอร์ | `https://p2w-influ-production.up.railway.app/` | Railway hosting |
| ประกันภัย | `/insurance` | ยังไม่มีหน้า |
| โมดิฟายรถ / Remap | `https://www.shiftupperformance.com/` | แยกเว็บ (ไม่เปลี่ยน) |

## Contact Info
- Phone: 088-788-8364 / 088-788-8634
- Email: p2w.interplus@gmail.com
- Line OA: https://lin.ee/QJax26d
- Address: 49/306 ซ.นิมิตใหม่40 ถ.นิมิตใหม่ แขวงสามวาตะวันออก เขตคลองสามวา กรุงเทพฯ

## ไฟล์ในโปรเจกต์
| ไฟล์ | หน้าที่ |
|------|---------|
| `index.html` | หน้าหลักทั้งหมด (single file) |
| `logo.png` | โลโก้บริษัท |
| `robots.txt` | อนุญาต bot และ AI crawler ทุกเจ้า |
| `llms.txt` | ข้อมูลสำหรับ LLM / AI ที่ crawl เว็บ |

## Visitor Tracking
- **Script**: ฝังใน index.html (บน visitor tracker ก่อน `</body>`)
- **IP/Location API**: ipapi.co (free 1,000 req/day)
- **Backend**: Google Apps Script Web App
- **Apps Script URL**: `https://script.google.com/macros/s/AKfycbz6ya72gdmELmCECrO28zACTdoVLcchVJXOoluHpjPTKsZnCRmYkRk5B74vvD57jHLB/exec`
- **Google Sheet**: P2W Visitors
- **ข้อมูลที่เก็บ**: วัน/เวลาไทย, IP, ประเทศ/เมือง, ISP, อุปกรณ์, Browser, OS, Referrer, มนุษย์/บอท, หน้า
- **การส่งข้อมูล**: POST ด้วย `mode: 'no-cors'` + `Content-Type: text/plain`

## Admin Dashboard
- **Trigger**: ไอคอนกุญแจใน footer (opacity ต่ำมาก กดเพื่อเปิด modal)
- **รหัสผ่าน**: `Chev9872`
- **Feature ใน Dashboard**:
  - Dark/Light mode toggle (sync กับหน้าหลัก)
  - การ์ด 4 ใบ: วันนี้, ทั้งหมด, มนุษย์, บอท
  - ตาราง visitor ล่าสุด 100 รายการ (live จาก Google Sheet)
  - ปุ่ม Refresh
- **การดึงข้อมูล**: `fetch(SHEET_URL, { redirect: 'follow' })` → Apps Script `doGet()`
- **⚠️ ต้องทำ**: เพิ่ม `doGet()` ใน Apps Script แล้ว Deploy ใหม่ ถึงจะดึงข้อมูลได้
- **Script order**: Admin script ต้องอยู่หลัง modal/dashboard HTML เสมอ (ไม่งั้น getElementById คืน null)

## Git / Deploy
- ทุกครั้งที่แก้ไขให้ push ขึ้น GitHub เลย ไม่ต้องถาม
- Branch: `main`
- Remote: `https://github.com/p2winterplus-oss/P2W-Main.git`

## Progress
### Done ✅
- สร้าง index.html — accordion hub design
- สร้าง GitHub repo + deploy GitHub Pages
- ใส่โลโก้ (logo.png) + dark mode stroke animation
- robots.txt (allow all bots + AI crawlers)
- llms.txt (LLM-friendly site description)
- Visitor tracking → Google Sheets (real-time)
- Light mode accordion: dark slate border + amber spark (ไม่กลืนกับพื้นอีกต่อไป)
- Admin Dashboard: hidden login, password modal, stats cards, visitor table, theme toggle

### Next ❌
- เพิ่ม doGet() ใน Apps Script + Deploy ใหม่ (เพื่อให้ Dashboard ดึงข้อมูลได้)
- ซื้อโดเมน p2winterplus.com
- ตั้ง Cloudflare DNS routing
- สร้างหน้าย่อย /shop, /insurance (engineer + consult + review มีแล้ว)
