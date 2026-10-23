# บันทึกการแก้โจทย์

## 1. ข้อมูล OJ

หมายเลข/ชื่อโจทย์ OJ: OJ3537 - [LEARNING LOGS] Impostor

OJ submission ID ถ้ามีการส่งแล้ว: __695350__

สถานะ OJ:

```text
Pass
```

เวลาที่ใช้คิดและทำโจทย์ด้วยตนเอง:

```text
15-30 minutes
```

## 2. ความเข้าใจโจทย์ของฉัน

โจทย์ให้รับรายชื่อคนในยานพร้อมบทบาท Crewmate หรือ Impostor แล้วรับชื่อคนที่ถูกโหวตออก จากนั้นให้แสดงจำนวน Impostor ที่ยังเหลือ และแสดงคนที่ยังอยู่กับคนที่ถูกไล่ออกไปแล้ว

input: ชุดแรกรับทีละบรรทัดเป็นdict เช่น {"Green" : "Crewmate"} จนกว่าจะเจอ Start
ชุดที่สองรับชื่อคนที่ถูกโหวตออกทีละบรรทัด จนกว่าจะเจอ End

output: บรรทัดแรกคือจำนวน Impostor ที่เหลือตามด้วย Impostor Remains แล้วเป็น ***Alive*** ตามด้วยชื่อ : บทบาท ของคนที่รอด
แล้วเป็น ***Dead*** ตามด้วยชื่อ : บทบาท ของคนที่ถูกไล่ออก ทั้งสองกลุ่มเรียงชื่อตามตัวอักษร

constraints: ตัวอย่างที่ 2 มีคนชื่อ Impostor ที่เป็น Crewmate และคนชื่อ Crewmate ที่เป็น Impostor
เลยต้องนับ Impostor จากบทบาทที่เป็น value เท่านั้น ห้ามนับจากชื่อ และต้องนับเฉพาะคนที่ยังรอดอยู่

## 3. แผนแรกของฉัน

```text
1 สร้างdict ว่างไว้เก็บผู้เล่นทั้งหมด
2 ใช้while loop รับทีละบรรทัด ถ้าเจอ Start ให้break ถ้าไม่ใช่ให้แปลงเป็นdict ด้วย json.loads แล้วใช้ update รวมเข้าdict หลัก
3 ใช้while loop อีกอันรับชื่อคนที่ถูกโหวต เก็บลงset จนกว่าจะเจอ End ให้break
4 สร้างdict อีก 2 อันคือคนที่รอดกับคนที่ตาย แล้วใช้ items() ไล่ทุกคน ถ้าชื่ออยู่ในset คนที่ถูกโหวตให้ใส่ใน dead ถ้าไม่อยู่ให้ใส่ใน alive
5 นับ Impostor ที่ยังรอดโดยไล่ values() ของ alive แล้วนับตัวที่เป็น Impostor
6 print จำนวน Impostor แล้วprint ***Alive*** ตามด้วยชื่อที่sorted แล้ว แล้วทำแบบเดียวกันกับ ***Dead***
7 ทดสอบกับtestcase ที่โจทย์ให้มาว่าตรงมั้ย
```

## 4. วิธีสุดท้ายที่ใช้จริง

ใช้วิธีแรกที่คิดได้ เพราะแยกคนเป็น 2 dict ตั้งแต่แรก ทำให้นับ Impostor ที่รอดกับเรียงชื่อแต่ละกลุ่มได้ง่าย

## 5. การทดสอบของฉัน

### Test Case 1

ทำไมเลือก case นี้: ทดสอบว่าถ้าไม่มีใครถูกโหวตเลย ทุกคนต้องรอด และใต้ ***Dead*** ต้องไม่มีชื่อใคร

Input:

```text
{"Red" : "Impostor"}
{"Blue" : "Crewmate"}
Start
End
```

Expected output:

```text
1 Impostor Remains
***Alive***
Blue : Crewmate
Red : Impostor
***Dead***
```

Actual output:

```text
1 Impostor Remains
***Alive***
Blue : Crewmate
Red : Impostor
***Dead***
```

Result:

```text
Pass
```

### Test Case 2

ทำไมเลือก case นี้: ทดสอบว่าถ้ามีการโหวตชื่อที่ไม่มีอยู่ในยาน (Yellow) จะไม่ไปโผล่ใน Dead และไม่ error

Input:

```text
{"Red" : "Impostor"}
{"Blue" : "Crewmate"}
Start
Yellow
Blue
End
```

Expected output:

```text
1 Impostor Remains
***Alive***
Red : Impostor
***Dead***
Blue : Crewmate
```

Actual output:

```text
1 Impostor Remains
***Alive***
Red : Impostor
***Dead***
Blue : Crewmate
```

Result:

```text
Pass
```

### Test Case 3

ทำไมเลือก case นี้: ทดสอบว่าถ้าโหวตคนเดิมซ้ำ 2 รอบ ชื่อต้องขึ้นใน Dead แค่ครั้งเดียว และ Impostor ที่เหลือต้องเป็น 0

Input:

```text
{"Red" : "Impostor"}
{"Blue" : "Crewmate"}
{"Green" : "Crewmate"}
Start
Red
Red
End
```

Expected output:

```text
0 Impostor Remains
***Alive***
Blue : Crewmate
Green : Crewmate
***Dead***
Red : Impostor
```

Actual output:

```text
0 Impostor Remains
***Alive***
Blue : Crewmate
Green : Crewmate
***Dead***
Red : Impostor
```

Result:

```text
Pass
```

## 6. การใช้ AI

ใช้ AI กับโจทย์นี้หรือไม่

```text
No
```

## 7. ความช่วยเหลือจากคน / การร่วมมือ

ได้ถามเพื่อน TA ผู้สอน หรือบุคคลอื่นเพื่อขอความช่วยเหลือในโจทย์นี้หรือไม่

```text
No
```

คุณคัดลอก code จากคนอื่นหรือไม่

```text
No
```

## 8. คำรับรองของนักศึกษา

| Statement                                                 | Yes/No |
| --------------------------------------------------------- | ------ |
| I wrote this submission in my own words.                  | Yes    |
| I understand my final code.                               | Yes    |
| I recorded the real OJ status.                            | Yes    |
| I did not copy AI-generated text directly into this file. | Yes    |
| I did not copy code from another person.                  | Yes    |
| If I received human help, I disclosed it in this file.    | Yes    |
| I submitted the final code to the OJ by myself.           | Yes    |
