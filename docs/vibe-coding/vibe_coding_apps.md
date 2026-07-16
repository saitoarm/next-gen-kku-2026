---
slug: /
sidebar_position: 1
title: "🚀 คู่มือ Vibe Coding: ระบบรายรับรายจ่าย (Bootstrap + Node.js - No DB & Free Deploy)"
sidebar_label: "Vibe Coding - รายรับรายจ่าย"
---

ยินดีต้อนรับสู่คู่มือการเรียนรู้ **Vibe Coding** ยุคใหม่! ในบทเรียนนี้เราจะพาคุณสร้าง **"ระบบบันทึกรายรับรายจ่าย"** ซึ่งเป็น Mini Project ยอดนิยมสำหรับนักพัฒนาเว็บแอปพลิเคชันมืออาชีพ 

โดยในเวอร์ชันนี้เราจะปรับเปลี่ยน Stack ให้เรียบง่ายและเป็นมิตรกับผู้เริ่มต้นที่สุด:
*   **Frontend:** ใช้โครงสร้างพื้นฐานทั่วไป (HTML, CSS, JavaScript) ร่วมกับ **Bootstrap 5 (ผ่าน CDN)** เพื่อตกแต่งหน้าตาให้สวยงามทันทีโดยไม่ต้องลงแอปพลิเคชันหรือลงแพ็คเกจหนักๆ
*   **Backend:** เขียนหลังบ้านด้วย **Node.js (Express)** สำหรับเป็นตัวจัดการ API และจำลองการจัดเก็บข้อมูลผ่าน **In-Memory Storage (ตัวแปรชั่วคราว)** หรือ **LocalStorage** (ทำให้ไม่ต้องเชื่อมต่อ Database จริง)
*   **Deployment:** สอนวิธีนำขึ้นระบบคลาวด์ฟรีแบบ 100% ทั้งแบบฟูลสแต็กบน **Vercel** และแถมโบนัสสายฟรีด้วยการแยก Deployment เอาหน้าบ้านขึ้น **GitHub Pages**!

---

## 🧭 Roadmap การพัฒนา (The Vibe Coding Way)

เพื่อประหยัด Token และป้องกันไม่ให้ AI เขียนโค้ดหลุดขอบเขต เราจะหักห้ามใจไม่ให้ Opus เขียนโค้ดจริงทั้งหมดในคราวเดียว แต่จะแบ่งเป็น **"Micro-Phases"** เพื่อตรวจรับงานทีละขั้น:

```
[Phase 1: วางพิมพ์เขียว] ──> [Phase 2: สร้าง & ทดสอบ Backend API] ──> [Phase 3: สร้าง & เชื่อมต่อ Frontend (Bootstrap)] ──> [Phase 4: Deploy เผยแพร่]
```

---

## 🎯 ขอบเขตและโครงสร้างโปรเจกต์ (Project Structure)

โปรเจกต์นี้จะสร้างภายใต้โครงสร้างไฟล์ที่พร้อมนำขึ้นทั้ง Vercel และ GitHub Pages:

```text
my-budget-app/
├── api/
│   └── index.js       # Backend Node.js/Express (Vercel Serverless Entry Point)
├── public/
│   ├── index.html     # หน้าแรกของเว็บ (ใช้ Bootstrap CDN)
│   ├── app.js         # Logic จัดการและ Fetch หา Backend API
│   └── styles.css     # CSS ตกแต่งเพิ่มเติม
├── vercel.json        # ไฟล์ตั้งค่าสำหรับ Deploy บน Vercel
├── package.json       # ไฟล์ระบุ Dependencies
└── SYSTEM_SPEC.md     # แผนงานที่ร่างโดย Opus
```

---

## 🧠 ขั้นตอนที่ 1: การใช้ Antigravity (Opus) วางแผนงาน (Phase 1)

เปิดใช้งาน **Antigravity** เลือกโมเดล **Opus** แล้วคัดลอกพรอมต์ด้านล่างนี้เพื่อสั่งให้ AI ช่วยสร้างแผนงานเฉพาะส่วนสถาปัตยกรรม (Architecture) ก่อน

### พรอมต์เฟสที่ 1: วางแผน Blueprint
```text
ฉันกำลังทำ Mini Project "ระบบบันทึกรายรับรายจ่าย" โดยเลือกใช้ Tech Stack ดังนี้:
- Frontend: HTML/CSS/JS ธรรมดา ใช้ Bootstrap 5 ผ่าน CDN ตกแต่งหน้าจอ
- Backend: Node.js (Express)
- Database: ไม่ใช้ฐานข้อมูลจริง ให้เขียน Logic บันทึกข้อมูลแบบ In-Memory Array บน Backend ชั่วคราว (หรือให้เก็บลง LocalStorage แนะนำแนวทางที่ดีที่สุดสำหรับการเอาขึ้น Serverless Vercel)

ช่วยทำหน้าที่เป็น Principal System Architect ช่วยสรุปและออกแบบ:
1. โครงสร้าง JSON Schema สำหรับข้อมูลรายรับรายจ่าย (เช่น ID, Type, Category, Amount, Date, Note)
2. แผนผัง API Endpoints ที่ต้องใช้ในการทำ CRUD (GET, POST, PUT, DELETE) และ Endpoint สรุปยอดเงินคงเหลือ
3. แนวทางการเชื่อมต่อระหว่างหน้าบ้านกับหลังบ้าน

(ขอเฉพาะข้อความอธิบายโครงสร้างและ Blueprint เท่านั้น *ห้ามเขียนโค้ดตัวเต็มมาให้เด็ดขาด*)
```

เมื่อ Opus ส่งคำตอบที่ถูกต้องมาแล้ว ให้ทำการคัดลอกข้อมูลนั้นไปสร้างเป็นไฟล์ชื่อ `SYSTEM_SPEC.md` ไว้ที่ Root ของโฟลเดอร์โปรเจกต์ของคุณ

---

## 🛠️ ขั้นตอนที่ 2: เริ่มเขียนโค้ดทีละสเต็ปบน VS Code ด้วย Cline (DeepSeek)

ติดตั้ง Extension **Cline** บนหน้าต่าง VS Code และเชื่อมต่อกับ **DeepSeek (ผ่าน OpenRouter หรือ Ollama ฟรี)** จากนั้นเราจะเริ่มสั่งงานทีละส่วนแบบจำกัดขอบเขตเพื่อประหยัด Token สูงสุด:

### 📥 สเต็ปที่ 2.1: เตรียมไฟล์ควบคุมแพ็คเกจ
สร้างไฟล์ `package.json` เปล่าขึ้นมาในเครื่อง และสั่ง Cline ว่า:
```text
ช่วยเขียนไฟล์ package.json โดยกำหนดให้โปรเจกต์นี้ใช้ Express.js และ CORS สำหรับการพัฒนาเว็บแบบ Serverless บน Vercel
```

### ⚙️ สเต็ปที่ 2.2: เขียนและทดสอบ Backend API (Phase 2)
สร้างไฟล์ `api/index.js` ขึ้นมา และป้อนพรอมต์ข้อกำหนดด้านล่างนี้ให้ Cline ทำงาน:
```text
อ้างอิงจากแผนงานใน `SYSTEM_SPEC.md` ช่วยสร้าง Backend API ด้วย Node.js และ Express.js ในไฟล์ `api/index.js` 
โดยให้เก็บข้อมูลชั่วคราวเป็น Array ในหน่วยความจำ (In-Memory) และสร้าง Endpoint ทั้งหมดดังนี้:
1. GET /api/transactions - ดึงรายการทั้งหมด
2. POST /api/transactions - เพิ่มรายการใหม่
3. PUT /api/transactions/:id - แก้ไขรายการ
4. DELETE /api/transactions/:id - ลบรายการ
5. GET /api/health - เช็คสถานะการทำงานของหลังบ้าน (ส่งค่า {"status": "ok"} กลับมา)

*หมายเหตุ: อย่าลืมเปิดใช้งาน CORS และส่งออก (export) ตัวแปร app เพื่อรองรับการทำงานของ Vercel Serverless ด้วย*
```

:::info การทดสอบหลังบ้าน (Health Check)
เมื่อ Cline เขียนไฟล์ `api/index.js` เสร็จแล้ว ให้ทดสอบรันในเครื่องของคุณโดยใช้ Terminal พิมพ์คำสั่ง `node api/index.js` (หรือใช้คำสั่งอื่นๆ ที่ตั้งค่าไว้) จากนั้นลองเปิดเบราว์เซอร์แล้วเข้าไปที่ `http://localhost:3000/api/health` หากพบข้อความ `{"status":"ok"}` แปลว่าระบบหลังบ้านทำงานผ่านฉลุย!
:::

### 🎨 สเต็ปที่ 2.3: เขียน Frontend (HTML/Bootstrap + JS) (Phase 3)
เมื่อหลังบ้านทำงานถูกต้องแล้ว ให้เคลียร์หน้าต่างแชทของ Cline เพื่อเซฟ Token สะสม แล้วสั่งทำหน้าต่างหน้าบ้านต่อ:
```text
อ้างอิงจาก API ที่ทำไว้แล้ว ช่วยสร้างส่วนของหน้าบ้าน (Frontend) ในโฟลเดอร์ `public/` โดยมีไฟล์ดังนี้:
1. `public/index.html`: ใช้ Bootstrap 5 CDN สร้างหน้าจอบันทึกรายรับรายจ่ายแบบทันสมัย มีฟอร์มกรอกข้อมูล, การ์ดสรุปยอดคงเหลือ, ตารางแสดงรายการพร้อมปุ่มแก้ไข/ลบ, และตัวกรองประเภทข้อมูล
2. `public/app.js`: เขียน JavaScript เพื่อจัดการ Event ในหน้าเว็บ, บันทึกข้อมูลลงใน LocalStorage (หากหลังบ้านหยุดทำงาน) หรือยิงยิ้ม Fetch เพื่อดึง-ส่งข้อมูลกับ Backend API ที่เตรียมไว้แบบสลับโหมดได้
```

---

## 🚀 ขั้นตอนที่ 3: การ Deploy บนคลาวด์ฟรี (Vercel & GitHub Pages)

เมื่อพัฒนาและทดสอบระบบในเครื่องคอมพิวเตอร์ผ่านหมดเรียบร้อยแล้ว ได้เวลาส่งงานและนำระบบขึ้นออนไลน์ให้คนอื่นทดสอบใช้งานจริงครับ!

### 🌍 ทางเลือกที่ 1: Deploy บน Vercel (ฟูลสแต็กทั้งตัวหลังบ้านและหน้าบ้าน)

Vercel มีฟังก์ชันรองรับการเขียน Node.js Backend ภายใต้โฟลเดอร์ `/api` แบบ Serverless Functions ได้อย่างดีเยี่ยม

1. **สร้างไฟล์ตั้งค่า `vercel.json` ไว้ที่ Root โฟลเดอร์เพื่อบอกเส้นทาง Router:**
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
2. **สร้าง Git Repository และส่งโค้ดขึ้น GitHub:**
   เปิด Terminal ของคุณและรันคำสั่งกลุ่มนี้:
   ```bash
   git init
   git add .
   git commit -m "feat: first deploy of financial tracker"
   git remote add origin <ลิงก์-Repository-บน-GitHub-ของคุณ>
   git branch -M main
   git push -u origin main
   ```
3. **ผูกและสั่งใช้งานบน Vercel:**
   * ล็อกอินเข้าสู่ระบบ [Vercel](https://vercel.com) ด้วยบัญชี GitHub ของคุณ
   * กดปุ่ม **"Add New..."** -> **"Project"**
   * มองหาชื่อ Repository ของคุณแล้วคลิก **"Import"**
   * สำหรับหน้าต่างตั้งค่า ไม่จำเป็นต้องแก้ปุ่มใดๆ ให้คลิก **"Deploy"** ได้ทันที
   * รอระบบประมวลผลประมาณ 1 นาที คุณจะได้รับ URL สาธารณะของหน้าบ้านที่สามารถยิงหา API หลังบ้านบนเซิร์ฟเวอร์เดียวกันได้ทันที!

---

### 🎁 [Bonus] ทางเลือกที่ 2: เอาเฉพาะหน้าบ้านขึ้น GitHub Pages 

สำหรับใครที่ต้องการประหยัดทรัพยากร หรืออยากแยกส่วนงานโดยให้หน้าบ้าน (Frontend) โฮสต์อยู่บน GitHub Pages เพื่อความเร็ว และอยากแยกยิง API หาหลังบ้านที่อยู่บน Vercel (หรือคลาวด์อื่น):

1. **สร้างกิ่ง (Branch) สำหรับ GitHub Pages:**
   ตามหลักแล้ว GitHub Pages จะอ่านไฟล์ HTML จากโฟลเดอร์ Root เป็นหลัก ดังนั้นเราสามารถนำไฟล์ในโฟลเดอร์ `public/` ขึ้นไปได้โดยตรงผ่าน Terminal:
   ```bash
   # สร้างโฟลเดอร์ย่อยหรือเตรียมไฟล์แยก
   git subtree push --prefix public origin gh-pages
   ```
2. **เปิดการใช้งาน GitHub Pages บนหน้าเว็บ:**
   * เปิดหน้าต่าง Repository ของคุณบนเว็บไซต์ GitHub
   * ไปที่แท็บ **Settings** ด้านบน
   * มองหาแถบเมนูด้านซ้าย เลือก **Pages**
   * ในหัวข้อ **Build and deployment** -> **Branch** ให้เลือกปลายทางเป็นกิ่ง `gh-pages` แล้วเลือกโฟลเดอร์ `/root` จากนั้นกด **Save**
   * รอประมาณ 2-3 นาที เว็บไซต์หน้าบ้านของคุณจะถูกเปิดให้ผู้ใช้ทั่วโลกเข้าถึงผ่าน URL: `https://ชื่อบัญชีผู้ใช้.github.io/ชื่อเรโป/` ได้ทันทีแบบฟรีถาวร!

:::success ข้อควรระวังในการแยก Deploy
หากคุณใช้หน้าบ้านบน GitHub Pages ยิงไปหา API บน Vercel อย่าลืมเข้าไปแก้ไขตัวแปร API URL ในไฟล์ `public/app.js` ของคุณให้ชี้ไปยังโดเมนเนมของ Vercel (เช่น `https://my-backend.vercel.app/api`) และตรวจสอบว่าฝั่ง API ของ Vercel ได้เปิดระบบ CORS ให้อนุญาตให้โดเมนของ GitHub Pages เข้ามาดึงข้อมูลได้เรียบร้อยแล้ว!
:::
