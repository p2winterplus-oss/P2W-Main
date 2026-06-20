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
3. **Accordion Hub** — 6 panels เรียงแนวนอน (desktop) / แนวตั้ง (mobile) พร้อม animated gold border
4. **Footer** — Logo + Branding + Contact + Social links

## Logo
- ไฟล์: `logo.png`
- Dark mode: pulse outer stroke animation (gold, 1px, 5s) ใช้ CSS `drop-shadow` 8 ทิศทาง
- CSS class: `logo-strobe` (ใช้ทั้ง navbar และ footer)

## Links ไปแต่ละ Service
| Service | URL |
|---------|-----|
| วิศวกรรม | /engineer |
| ที่ปรึกษา | /consult |
| ขายสินค้า | /shop |
| คอนเทนต์/อินฟลูเอนเซอร์ | /review |
| ประกันภัย | /insurance |
| โมดิฟายรถ / Remap | https://www.shiftupperformance.com/ (แยกเว็บ) |

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
- **Script**: ฝังใน index.html ก่อน `</body>`
- **IP/Location API**: ipapi.co (free 1,000 req/day)
- **Backend**: Google Apps Script Web App
- **Apps Script URL**: `https://script.google.com/macros/s/AKfycbz6ya72gdmELmCECrO28zACTdoVLcchVJXOoluHpjPTKsZnCRmYkRk5B74vvD57jHLB/exec`
- **Google Sheet**: P2W Visitors (ID: ดูจาก URL ของ Sheet)
- **ข้อมูลที่เก็บ**: วัน/เวลาไทย, IP, ประเทศ/เมือง, ISP, อุปกรณ์, Browser, OS, Referrer, มนุษย์/บอท

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

### Next ❌
- ซื้อโดเมน p2winterplus.com
- ตั้ง Cloudflare DNS routing
- สร้างหน้าย่อย /engineer, /consult, /shop, /review, /insurance
