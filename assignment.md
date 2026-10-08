# บทที่ 1: Assignment (การบ้าน)

ส่วนหนึ่งของ [week_01.md](../week_01.md)

## เป้าหมาย

ฝึกใช้ AI assistant ใน VS Code (เช่น AI extension ที่ติดตั้งใน editor) กับ dataset ใหม่ที่ไม่ใช่ dataset ในคลาส และฝึกสังเกตประเด็น Responsible AI (hallucination/bias) จากผลลัพธ์ที่ AI assistant สร้างให้

## เตรียม Environment ก่อนเริ่มทำ

### Tools ที่ต้องมีให้ครบ

1. **VS Code** — เวอร์ชันล่าสุด ([code.visualstudio.com](https://code.visualstudio.com))
2. **Python 3.10+** ติดตั้งในเครื่อง
3. **VS Code Extension: Python** (จาก Microsoft)
4. **VS Code Extension: Jupyter** (จาก Microsoft)
5. **VS Code Extension: Github Copilot Chat** (จาก Github)
6. **AI assistant extension ที่ใช้ในคลาส** — ต้อง configure ต่อ liteLLM ของบริษัท(รับ API Key ใน Class)
7. **Python package: pandas** — ติดตั้งผ่าน `pip install pandas`

### ขั้นตอนติดตั้ง (ทำครั้งเดียว)

1. ติดตั้ง VS Code ให้เรียบร้อย (ถ้ายังไม่มี)
2. เปิด VS Code → แท็บ Extensions (`Ctrl+Shift+X` หรือ `Cmd+Shift+X` บน Mac) → ค้นหาและติดตั้ง **Python** และ **Jupyter** (ทั้งสองตัวจาก Microsoft) รวมถึง AI assistant extension ที่ใช้ในคลาส
3. Login AI assistant extension ด้วย account ของตัวเอง (ดูไอคอนที่แถบล่างของ VS Code ว่าสถานะ "Signed in" แล้ว)
4. เปิด Terminal ใน VS Code (`Terminal > New Terminal`) แล้วรัน:
   ```bash
   pip install pandas
   ```
5. เปิด **ทั้ง folder** `week_01/` ใน VS Code (`File > Open Folder...`) — **ห้ามเปิดแค่ไฟล์เดี่ยวๆ** เพราะ path ของ dataset ใน notebook อ้างอิงแบบ relative จาก folder นี้ (เช่น `datasets/homework/...`) ถ้าเปิดผิด folder จะหา dataset ไม่เจอ

### วิธีทดสอบว่า environment พร้อมแล้ว (ทำก่อนเริ่ม assignment จริงทุกครั้ง)

1. เปิดไฟล์ [assignment_template.ipynb](assignment_template.ipynb)
2. รันเซลล์แรกที่มี `import pandas as pd` — **ผ่าน** ถ้าไม่มี error (แปลว่า pandas ติดตั้งถูกต้องและ Jupyter extension ทำงานได้)
3. รันเซลล์ที่โหลด dataset (`pd.read_csv(...)`) — **ผ่าน** ถ้าเห็นตาราง `df.head()` แสดงข้อมูลออกมา (แปลว่า path ถูกต้องและ pandas อ่านไฟล์ได้)
4. เปิดไฟล์ `.py` ใหม่ว่างๆ ลองพิมพ์ comment สั้นๆ (เช่น `# function to add two numbers`) แล้วรอ 1-2 วินาที — **ผ่าน** ถ้าเห็นข้อความสีเทาโผล่ขึ้นมาให้กด `Tab` เพื่อ accept (แปลว่า AI assistant extension ทำงานและ login ถูกต้อง) — ถ้าไม่เห็นให้กลับไปเช็ค login/สถานะ extension ในขั้นตอนที่ 3 ของการติดตั้ง

ถ้าผ่านครบทั้ง 4 ข้อ ถือว่า environment พร้อม เริ่มทำ assignment ได้เลย

## รายละเอียดงาน

เลือก dataset เป็น raw data มา 1 ชุดจาก [datasets/homework/](datasets/homework/) (มีให้เลือก 12 ชุด ชุดละ ~20,000 แถว ต่างจาก messy_customers.csv/messy_orders.csv ที่ใช้ใน workshop) แล้วเขียนฟังก์ชัน data-cleaning ใน VS Code ด้วยความช่วยเหลือของ AI assistant ให้ได้อย่างน้อย 3 ฟังก์ชัน จากนั้นบันทึกกรณีที่ AI assistant สร้างโค้ดผิดหรือดูไม่ปลอดภัยอย่างน้อย 1 ครั้ง พร้อมเขียน reflection สั้นๆ เชื่อมโยงกับเรื่อง hallucination/bias ที่เรียนในคลาส

## ขั้นตอนที่ต้องทำ

0. เปิด [assignment_template.ipynb](assignment_template.ipynb) เป็นจุดเริ่มต้น (มีโครง cell ให้ครบตามขั้นตอนด้านล่าง แก้แค่ path dataset และเติมโค้ด) — ดูวิธีรัน notebook ในเซลล์แรกของไฟล์
1. เปิด VS Code และตรวจสอบว่าติดตั้ง AI assistant extension ที่ใช้ในคลาสพร้อมใช้งานแล้ว
2. เลือก dataset 1 ชุดจาก `datasets/homework/` (CSV ที่มีค่า missing/format ไม่สม่ำเสมอ) แล้วเปิดใน VS Code
3. เขียน comment อธิบาย intent ก่อนให้ AI assistant ช่วย (ตามแบบที่ demo ในคลาส)
4. เขียนฟังก์ชันทำความสะอาดข้อมูลอย่างน้อย 3 ประเด็น (เช่น missing values, format ไม่สม่ำเสมอ, ชื่อ column ไม่เรียบร้อย)
5. บันทึก 1 กรณีที่ AI assistant สร้างโค้ดผิดหรือดูไม่ปลอดภัย พร้อมอธิบายว่าแก้ไขอย่างไร
6. เขียน reflection ~150–200 คำ เชื่อมโยงกับ hallucination หรือ bias จาก lecture

## สิ่งที่ต้องส่ง

- Notebook (.ipynb) ที่มีฟังก์ชัน data-cleaning ทั้ง 3 ฟังก์ชันรันได้จริง (พัฒนาใน VS Code)
- ย่อหน้า reflection (ในไฟล์เดียวกันหรือแยกเป็น .md ก็ได้)

## เกณฑ์การให้คะแนน

| เกณฑ์ | น้ำหนัก |
| --- | --- |
| ฟังก์ชันทำความสะอาดข้อมูลทำงานถูกต้องครบ 3 ประเด็น | 50% |
| บันทึกกรณี AI assistant สร้างโค้ดผิด/ไม่ปลอดภัยพร้อมวิธีแก้ | 20% |
| Reflection เชื่อมโยงกับ Responsible AI ได้ชัดเจน | 30% |

## กำหนดส่ง

ก่อนเริ่มเรียน บทที่ 2

## เวลาที่ควรใช้โดยประมาณ

1–1.5 ชั่วโมง


## หมายเหตุ: รูปแบบการทำงาน (Reflexion Pattern)
1. Generate → สร้างคำตอบ/โค้ด/แผนงานครั้งแรก
2. Reflect → ให้ LLM ประเมินผลของตัวเอง (self-critique)
   - "คำตอบนี้ถูกไหม?"
   - "มีสิ่งที่ตกหล่นไหม?"
   - "โค้ดนี้มี edge case ที่พังไหม?"
3. Revise → แก้ไขตามข้อเสนอแนะ
4. (ทำซ้ำ 1–3 จนกว่าจะผ่านเกณฑ์)