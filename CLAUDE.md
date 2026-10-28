# P2W INTERPLUS — หน้าหลัก (Main Hub)

## Architecture รวม
ดู `C:\Users\witta\OneDrive\Claude AI Backup\P2W-ARCHITECTURE.md`

## โปรเจกต์นี้คืออะไร
Entry point ของ P2W INTERPLUS ทั้งหมด — ลูกค้าเข้ามาแล้วเลือก service ที่ต้องการ ไม่มีรายละเอียดเชิงลึก หน้าย่อยแต่ละอันดูแลเอง

- **Live URL**: https://p2winterplus.com ✅ (GoDaddy domain + Cloudflare DNS + GitHub Pages)
- **Repo**: https://github.com/p2winterplus-oss/P2W-Main ✅
- **Hosted**: GitHub Pages (CNAME → p2winterplus.com)
- **Stack**: HTML + Tailwind CSS CDN + Vanilla JavaScript

## Design System
- **Primary color**: Gold `#D4AF37`
- **Dark bg**: `#0B1120` / **Light bg**: `#F9F8F6`
- **Font**: Prompt (body)
- **Style**: Luxury dark accordion hub — slanted expanding panels with background images
- **Dark/Light mode toggle**: localStorage (`color-theme`) — default = dark

## โครงสร้างหน้า (ปัจจุบัน)

### index.html
1. **Navbar** — Logo (logo.png) + about button (left) + Line OA + theme toggle (right)
2. **Hero** — "P2W INTERPLUS GROUP" + subtitle "ขับเคลื่อนทุกความเป็นไปได้ ผ่านเครือข่ายบริการที่ครอบคลุมของเรา"
3. **Accordion Hub** — 6 panels เรียงแนวนอน (desktop) / แนวตั้ง (mobile) พร้อม animated border และ description text ใน hover state ทุก panel
4. **Footer** — Logo + Branding text ("มากกว่าการบูรณาการธุรกิจ เราคือพื้นที่รวม 'ตัวจริง' จากทุกวงการ…") + Contact + Social + hidden admin trigger

### about.html
1. **Navbar** — Back button (left) + Logo center + Line OA + theme toggle (right)
2. **Hero** — "WE DON'T JUST ADAPT. WE CREATE." + subtitle
3. **เราคือใคร** — body text (Startup culture + "คิดไว ทำจริง และปรับตัวเร็ว" in gold) + 3 feature cards (Agile Execution / Synergy of Creators / Limitless Solutions)
4. **บริการทั้งหมด** — 6 service cards พร้อม `.hex-icon` (3D hexagon icon style)
5. **ทำไมต้องเลือกเรา** — 4 items พร้อม `.hex-icon`
6. **Contact** — phone / email / address / Line

## ข้อมูลนิติบุคคล (ตรงกับหนังสือรับรอง ออก 17 เม.ย. 2569 — ใช้ยืนยันธุรกิจกับ Meta)
- ชื่อไทย: บริษัท พีทูดับบลิว อินเตอร์พลัส จำกัด
- ชื่ออังกฤษ: P2W INTERPLUS COMPANY LIMITED (ห้ามใช้ "CO.,LTD." — Meta ตรวจชื่อตามกฎหมายต้องตรงตัว)
- เลขทะเบียนนิติบุคคล: 0105569073751
- ต้องแสดงชื่อ + เลขทะเบียนให้เห็นบนหน้าเว็บ (footer ของ index/about/privacy/terms) ไม่ใช่แค่ใน JSON-LD
- Facebook เพจในเครือ (ใส่เฉพาะ JSON-LD `sameAs` ใน index.html ไม่แสดงบนหน้าเว็บ): pingstores, shiftupperformance, ipingofficial, Deepsolarbypk, Infinisfood
- Footer ไม่มีปุ่ม Facebook/Instagram (ตั้งใจไม่ให้คนกดออกจากเว็บ) เหลือแค่ LINE

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
| Service | URL | หมายเหตุ |
|---------|-----|---------|
| วิศวกรรม | `https://p2winterplus.com/engineer` | ✅ Live via Cloudflare Worker |
| ที่ปรึกษาการตลาด | `https://p2winterplus.com/consult` | ✅ Live via Cloudflare Worker |
| ขายสินค้า | `/shop` | ยังไม่มีหน้า |
| คอนเทนต์/อินฟลูเอนเซอร์ | `https://p2winterplus.com/influ` | ✅ Live via Cloudflare Worker |
| ประกันภัย | `/insurance` | ยังไม่มีหน้า |
| โมดิฟายรถ / Remap | `https://www.shiftupperformance.com/` | แยกเว็บ (ไม่เปลี่ยน) |

## Contact Info
- Phone: 088-788-8364 / 088-788-8634
- Email (แสดงบนเว็บ): info@p2winterplus.com + adm.p2winterplus@gmail.com
- Email หลังบ้าน Meta: p2w.interplus@gmail.com (ใส่เฉพาะ JSON-LD contactPoint ห้ามแสดงบนหน้าเว็บ)
- Line OA: https://lin.ee/QJax26d
- Address: 49/306 ซ.นิมิตใหม่40 ถ.นิมิตใหม่ แขวงสามวาตะวันออก เขตคลองสามวา กรุงเทพฯ

## ไฟล์ในโปรเจกต์
| ไฟล์ | หน้าที่ |
|------|---------|
| `index.html` | หน้าหลัก accordion hub |
| `about.html` | หน้าเกี่ยวกับเรา (`.hex-icon` 3D hexagon style) |
| `privacy.html` | นโยบายความเป็นส่วนตัว (`/privacy`) |
| `terms.html` | ข้อกำหนดการใช้งาน (`/terms`) |
| `logo.png` | โลโก้บริษัท |
| `robots.txt` | อนุญาต bot และ AI crawler ทุกเจ้า |
| `llms.txt` | ข้อมูลสำหรับ LLM / AI ที่ crawl เว็บ |
| `sitemap.xml` | Sitemap ส่ง Google Search Console |

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
- สร้าง index.html — accordion hub design (6 panels + description text ทุก panel)
- สร้าง GitHub repo + deploy GitHub Pages
- ใส่โลโก้ (logo.png) + dark mode stroke animation
- robots.txt (allow all bots + AI crawlers)
- llms.txt (LLM-friendly site description)
- sitemap.xml → submit Google Search Console
- SEO: meta tags, Open Graph, JSON-LD structured data, canonical tag
- Visitor tracking → Google Sheets (real-time)
- Light mode accordion: dark slate border + amber spark
- Admin Dashboard: hidden login, password modal, stats cards, visitor table, theme toggle
- ซื้อโดเมน p2winterplus.com (GoDaddy) + Cloudflare DNS + Enforce HTTPS ✅
- Cloudflare Workers routing (/engineer, /consult, /influ) ✅
- Navbar อัปเดต: about button (left), Line OA button + theme toggle (right)
- about.html: ครบทุก section + `.hex-icon` 3D hexagon icon style
- ปรับชื่อบริษัท/เลขทะเบียนให้ตรงหนังสือรับรอง + สร้างหน้า /privacy /terms + sitemap (28 ต.ค. 2569) เพื่อยืนยันธุรกิจ Meta

### Next ❌
- เพิ่ม doGet() ใน Apps Script + Deploy ใหม่ (เพื่อให้ Dashboard ดึงข้อมูลได้)
- สร้างหน้าย่อย /shop, /insurance
