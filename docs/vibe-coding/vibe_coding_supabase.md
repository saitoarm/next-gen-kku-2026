---
sidebar_position: 1
title: "🚀 คู่มือ Vibe Coding: ระบบรายรับรายจ่าย (Bootstrap + Node.js + Supabase Postgres & Vercel)"
sidebar_label: "Vibe Coding - รายรับรายจ่าย (Full Stack & DB)"
---

ยินดีต้อนรับสู่คู่มือ **Vibe Coding** ขั้นสูง! ในบทเรียนนี้เราจะอัปเกรดระบบ **"ระบบบันทึกรายรับรายจ่าย"** จากระบบชั่วคราวให้กลายเป็นแอปพลิเคชันแบบ Full Stack ที่สมบูรณ์แบบ:
*   **Frontend:** ใช้ HTML, CSS, JavaScript ร่วมกับ **Bootstrap 5 (ผ่าน CDN)** เพื่อหน้าจอที่สวยงาม รวดเร็ว และไม่ต้องติดตั้งเครื่องมือซับซ้อน
*   **Backend:** เขียนหลังบ้านด้วย **Node.js (Express.js)** เพื่อทำหน้าที่เป็น REST API ทำงานแบบ Serverless บน Vercel
*   **Database:** บันทึกข้อมูลจริงอย่างถาวรลงในฐานข้อมูล **PostgreSQL** บน **Supabase** (Free Tier รองรับได้สบายๆ)
*   **Deployment:** สอนวิธีร้อยสายเชื่อมต่อระหว่าง **Supabase (DB)** และ **Vercel (Backend + Frontend)** ผ่าน Environment Variables และวิธีสั่งออนไลน์แบบฟรี 100%!

---

## 🧭 Roadmap การพัฒนา (The Vibe Coding Way)

เรายังคงยึดหลักจงใจคุม Token เพื่อเซฟต้นทุนของ AI โดยแบ่งงานออกเป็น 5 ช่วงสั้นๆ (Micro-Phases) เพื่อให้เราตรวจรับงานและควบคุมความถูกต้องได้ดีที่สุด:

```
[Phase 1: วางสเปกโครงสร้าง] ──> [Phase 2: ตั้งค่า DB บน Supabase] ──> [Phase 3: พัฒนา & ทดสอบ API] ──> [Phase 4: สร้าง UI หน้าบ้าน] ──> [Phase 5: ผูกเชื่อมและ Deploy คลาวด์]
```

---

## 🎯 ขอบเขตและโครงสร้างโปรเจกต์ (Project Structure)

โปรเจกต์จะใช้โครงสร้างเดิมแต่มีการเชื่อมต่อฐานข้อมูล Postgres จริง และระบุตัวแปรความปลอดภัยในเครื่องผ่านไฟล์ `.env`:

```text
my-budget-app/
├── api/
│   └── index.js       # Backend Node.js/Express (Vercel Serverless + pg Client)
├── public/
│   ├── index.html     # หน้าแรกของเว็บ (ใช้ Bootstrap CDN)
│   ├── app.js         # Logic ฝั่ง Client เชื่อมต่อผ่าน Fetch API
│   └── styles.css     # สไตล์ตกแต่งเพิ่มเติม
├── vercel.json        # ไฟล์ตั้งค่าสำหรับ Deploy บน Vercel
├── package.json       # ไฟล์ระบุ Dependencies (รวม 'pg' และ 'dotenv')
├── .env               # ไฟล์เก็บค่าเชื่อมต่อฐานข้อมูล (ห้ามอัปขึ้น Git!)
├── .gitignore         # ไฟล์ระบุความปลอดภัย ไม่เอา .env ขึ้น Git
└── SYSTEM_SPEC.md     # แผนงานที่ร่างโดย Opus
```

---

## 🧠 ขั้นตอนที่ 1: ใช้ Antigravity (Opus) ร่าง Blueprint คอนเซปต์ (Phase 1)

เปิดใช้งาน **Antigravity** เลือกโมเดล **Opus** แล้วคัดลอกพรอมต์เพื่อทำพิมพ์เขียวเฉพาะส่วนสถาปัตยกรรมและ Schema ฐานข้อมูล

### พรอมต์เฟสที่ 1: ออกแบบ Schema และ API ด้วย PostgreSQL
```text
ฉันกำลังทำ Mini Project "ระบบบันทึกรายรับรายจ่าย" โดยเลือกใช้ Tech Stack ดังนี้:
- Frontend: HTML/CSS/JS + Bootstrap 5 CDN
- Backend: Node.js (Express) รันบน Serverless Vercel
- Database: PostgreSQL บน Supabase (เชื่อมโยงผ่าน Connection String)

ช่วยทำหน้าที่เป็น Principal System Architect ออกแบบและอธิบาย:
1. SQL Schema (DDL) สำหรับตาราง `transactions` บน PostgreSQL (กำหนดชนิดข้อมูล วันที่ และ Primary Key ให้ถูกต้อง)
2. แผนผัง API Endpoints สำหรับทำ CRUD (GET, POST, PUT, DELETE) 
3. แนะนำโครงสร้าง Config และการเรียกใช้ Connection Pool ใน Node.js โดยใช้ไลบรารี 'pg' ให้รองรับสถาปัตยกรรม Serverless

(ขอเฉพาะ Blueprint, SQL และคู่มือ API เท่านั้น *ยังไม่ต้องเขียนโค้ดหลังบ้านเต็มรูปแบบ*)
```

เมื่อ Opus ส่ง Blueprint ให้สร้างไฟล์ `SYSTEM_SPEC.md` ไว้ที่ Root ของโปรเจกต์ แล้วคัดลอกเนื้อหาทั้งหมดไปวางไว้ทันที

---

## 🗄️ ขั้นตอนที่ 2: ตั้งค่าฐานข้อมูล PostgreSQL บน Supabase (Phase 2)

ก่อนจะให้ AI เริ่มเขียนโค้ด เราต้องมีระบบฐานข้อมูลรองรับไว้ก่อน:

1. สมัครใช้งานและล็อกอินเข้าสู่ [Supabase](https://supabase.com) ด้วยบัญชี GitHub ของคุณ
2. คลิก **"New Project"** -> กรอกชื่อโครงการและเลือก Location เป็นสิงคโปร์ (หรือใกล้ประเทศไทยที่สุด) -> ตั้งรหัสผ่านของ Database (จดจำรหัสนี้ไว้)
3. เมื่อเปิดโครงการเสร็จแล้ว ให้ไปที่เมนู **SQL Editor** ที่แถบเมนูด้านซ้าย
4. คลิก **"New Query"** แล้วนำ **SQL Schema (DDL)** ที่ได้จากก้าวแรกที่บันทึกไว้ใน `SYSTEM_SPEC.md` มาวางและกดปุ่ม **"Run"** เพื่อสร้างตาราง `transactions` ทันที
5. ไปที่เมนู **Settings** (รูปฟันเฟือง) -> **Database** 
6. มองหาหัวข้อ **Connection string** ให้คัดลอกค่าในแท็บ **URI** (เลือกโหมด Transaction 6543) นำมาเก็บไว้ในไฟล์ชื่อ `.env` ในเครื่องของคุณดังนี้:
   ```env
   DATABASE_URL="postgres://postgres.xxxxxx:password@aws-0-ap-southeast-1.pooler.supabase.com:6543/postgres?pgbouncer=true"
   ```
   *(อย่าลืมแทนที่ `password` ด้วยรหัสผ่านฐานข้อมูลที่คุณตั้งไว้จริง)*

---

## 🛠️ ขั้นตอนที่ 3: เริ่มเขียนโค้ดทีละสเต็ปด้วย Cline (DeepSeek)

ติดตั้ง Extension **Cline** บน VS Code เชื่อมต่อกับ **DeepSeek (ผ่าน OpenRouter หรือ Ollama)** และสร้างไฟล์ `.gitignore` เพื่อป้องกันข้อมูลความลับรั่วไหล:
```text
node_modules/
.env
.next/
dist/
```

### 📥 สเต็ปที่ 3.1: เตรียมไฟล์ Dependencies
สร้างไฟล์ `package.json` ว่างในโปรเจกต์ แล้วสั่ง Cline ว่า:
```text
ช่วยสร้างไฟล์ package.json ที่ติดตั้ง 'express', 'cors', 'pg' (สำหรับเชื่อมต่อ Postgres) และ 'dotenv' (สำหรับอ่านค่า .env) เพื่อรันหลังบ้านเป็น Serverless บน Vercel
```

### ⚙️ สเต็ปที่ 3.2: สร้างและทดสอบ Backend API (Phase 3)
สร้างไฟล์ `api/index.js` ขึ้นมา และให้ Cline บรรเลงโค้ด:
```text
อ้างอิงจาก Blueprint ใน `SYSTEM_SPEC.md` ช่วยเขียนโค้ด Node.js/Express ลงในไฟล์ `api/index.js` 
โดยมีเงื่อนไขดังนี้:
1. โหลดค่า `process.env.DATABASE_URL` มาเพื่อเชื่อมต่อกับ PostgreSQL โดยใช้ 'pg' (แนะนำให้ใช้ pg.Pool)
2. สร้าง Endpoint ดังนี้:
   - GET /api/transactions : ดึงรายการทั้งหมดจากตาราง transactions
   - POST /api/transactions : เพิ่มข้อมูลรายการใหม่ (ประเภท, หมวดหมู่, จำนวนเงิน, วันที่, รายละเอียด)
   - PUT /api/transactions/:id : แก้ไขรายการเดิมตาม id
   - DELETE /api/transactions/:id : ลบรายการเดิมตาม id
   - GET /api/health : ทดสอบการทำงานของระบบหลังบ้านและการดึงข้อมูลด่วนจากฐานข้อมูล (Health Check)

*หมายเหตุ: เปิด CORS และ Export ค่าแอปพลิเคชันออกมาเพื่อให้พร้อมรันบน Vercel*
```

:::info การตรวจรับความสมบูรณ์หลังบ้าน
ให้ลองพิมพ์คำสั่ง `node api/index.js` หรือรันผ่านสคริปต์ใน Terminal ของคุณเพื่อทดสอบ จากนั้นเข้าไปยัง `http://localhost:3000/api/health` บนเบราว์เซอร์ หากระบบสามารถติดต่อกับฐานข้อมูล Supabase ได้และตอบกลับมาเป็นปกติ แปลว่าคุณเตรียม API ที่สมบูรณ์แบบพร้อมใช้งานแล้ว!
:::

### 🎨 สเต็ปที่ 3.3: พัฒนาและเชื่อมต่อหน้าต่าง Frontend (Phase 4)
หลังจากขั้นตอนด้านบนผ่านฉลุย ให้กดยืนยัน (Accept) บนหน้าต่าง Cline แล้ว**กดปุ่ม "Clear Chat" เพื่อเริ่มแชทใหม่สำหรับหน้าบ้าน** วิธีนี้จะป้องกันประวัติคำสั่งบวมจน Token รั่วไหล จากนั้นสั่ง Cline:
```text
ช่วยเขียนไฟล์หน้าบ้าน (Frontend) ในโฟลเดอร์ `public/` โดยประกอบไปด้วย:
1. `public/index.html`: ใช้ Bootstrap 5 CDN สร้าง UI สรุปรายรับรายจ่าย มีระบบกรอกรายละเอียดรายการแบบฟอร์ม, มีตารางประวัติย้อนหลังพร้อมปุ่มลบและแก้ไขข้อมูลแบบ Real-time
2. `public/app.js`: เขียนคำสั่งดึงค่า API โดยตรงจากหลังบ้านเพื่อทำระบบการบันทึก, อัปเดต, และลบรายการธุรกรรมทางการเงินให้ทำงานรวดเร็วแบบ Dynamic หน้าเว็บไม่รีโหลดซ้ำ
```

---

## 🚀 ขั้นตอนที่ 4: สั่ง Deploy และเชื่อมโยงบริการ (Vercel & Supabase) (Phase 5)

ตอนนี้เรามีโค้ดพร้อมรันแล้ว เราจะนำทั้งหมดขึ้นระบบของ Vercel และผูกฐานข้อมูลที่อยู่บน Supabase เข้าหากันอย่างปลอดภัย

### 1. วางไฟล์ตั้งค่า `vercel.json` ไว้ที่ Root ของโปรเจกต์:
```json
{
  "version": 2,
  "builds": [
    { "src": "api/index.js", "use": "@vercel/node" },
    { "src": "public/**/*", "use": "@vercel/static" }
  ],
  "routes": [
    { "src": "/api/(.*)", "dest": "/api/index.js" },
    { "src": "/(.*)", "dest": "/public/$1" }
  ]
}
```

### 2. นำโค้ดขึ้น GitHub:
พิมพ์คำสั่งนี้ในหน้าต่าง Terminal ของคุณ:
```bash
git init
git add .
git commit -m "feat: full stack budget app with supabase integration"
git remote add origin <ลิงก์-Repository-บน-GitHub-ของคุณ>
git branch -M main
git push -u origin main
```

### 3. ตั้งค่าการ Deploy บนเว็บ Vercel:
1. ล็อกอินเข้าใช้งาน [Vercel](https://vercel.com) ดึงโปรเจกต์นี้จาก GitHub ของคุณเข้ามาผ่านฟังก์ชัน **Import**
2. ในหน้าต่างตั้งค่าการสร้างโปรเจกต์ ให้กดเปิดส่วนของ **Environment Variables** (นี่คือขั้นตอนที่สำคัญที่สุด!)
3. ใส่ค่ากุญแจความปลอดภัยดังนี้:
   * **Key:** `DATABASE_URL`
   * **Value:** วาง Connection String ตัวจริงของ Supabase (ที่คุณใช้ในเครื่องตอนเขียนไฟล์ `.env`)
4. คลิกที่ปุ่ม **"Add"**
5. คลิกที่ปุ่ม **"Deploy"**
6. รอการติดตั้งระบบประมาณ 1 นาที คุณจะได้ URL จริงที่รันเว็บรายรับรายจ่าย และส่งค่าบันทึกลงฐานข้อมูล Supabase PostgreSQL ของคุณอย่างมั่นคงและถาวรโดยไม่มีค่าบริการใดๆ!

:::success เคล็ดลับจากผู้เชี่ยวชาญ
การใส่ `DATABASE_URL` ลงในหน้าจอตั้งค่าของ Vercel จะช่วยป้องกันไม่ให้ระบบภายนอกแอบเห็นกุญแจความลับของคุณ (เพราะเราทำการปฏิเสธไม่ให้ไฟล์ `.env` ของในเครื่องอัปขึ้น GitHub ผ่านไฟล์ `.gitignore` ไปตั้งแต่แรกแล้ว) ทำให้ข้อมูลทางการเงินของคุณมีความปลอดภัยเทียบเท่าระดับโปรดักชันจริง!
:::
