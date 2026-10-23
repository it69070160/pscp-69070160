# บันทึกการแก้โจทย์

## 1. ข้อมูล OJ

หมายเลข/ชื่อโจทย์ OJ: OJ3538 - [LEARNING LOGS] B - Fully pair?

OJ submission ID ถ้ามีการส่งแล้ว: __695366__

สถานะ OJ:

```text
Pass
```

เวลาที่ใช้คิดและทำโจทย์ด้วยตนเอง:

```text
15-30 minutes
```

## 2. ความเข้าใจโจทย์ของฉัน

โจทย์ให้หาว่าตัวอักษรไหนที่ไม่มีคู่ คือตัวที่มีจำนวนเป็นเลขคี่ เช่น aaaa ถือว่าครบคู่ แต่ aaaaa จะเหลือ a อยู่ 1 ตัว

input: ข้อความ 1 บรรทัด เป็นตัวอักษรพิมพ์เล็ก a-z รับมาเป็นstr

output: ตัวอักษรที่ไม่มีคู่ต่อกันเป็นบรรทัดเดียว เรียงตามตัวที่เจอก่อนจากซ้ายไปขวา ถ้าครบคู่ทุกตัวให้print fully paired

constraints: ต้องเรียงตามลำดับที่เจอครั้งแรก ไม่ใช่เรียงตามตัวอักษร อย่างตัวอย่างที่ 4 ต้องตอบ tg ไม่ใช่ gt
และตัวอย่างที่ 5 คือ baacbb ตัว b เจอก่อน c เลยต้องตอบ bc

## 3. แผนแรกของฉัน

```text
1 รับข้อความมาเป็นstr แล้วใช้strip ตัดช่องว่างหัวท้าย
2 สร้างdict ไว้นับจำนวนแต่ละตัวอักษร และlist ไว้เก็บลำดับตัวอักษรที่เจอครั้งแรก
3 ใช้for loop ไล่ทีละตัว ถ้าตัวนั้นยังไม่อยู่ในdict ให้ตั้งค่าเป็น 0 แล้วappend ลงlist ลำดับ จากนั้น +1 ให้ตัวนั้น
4 ใช้for loop ไล่ตามlist ลำดับ ถ้าจำนวนของตัวนั้น % 2 เหลือเศษ แปลว่าเป็นเลขคี่ ไม่มีคู่ ให้append ลงlist ที่ไม่มีคู่
5 ถ้าlist ที่ไม่มีคู่มีค่า ให้ใช้ join ต่อกันแล้วprint ถ้าว่างให้print fully paired
6 ทดสอบกับtestcase ที่โจทย์ให้มาทั้ง 5 อันว่าตรงมั้ย
```

## 4. วิธีสุดท้ายที่ใช้จริง

ใช้วิธีแรกที่คิดได้ เพราะใช้list เก็บลำดับที่เจอครั้งแรกไว้ ทำให้ตอบตามลำดับซ้ายไปขวาได้เลย ไม่ต้องมาหาตำแหน่งใหม่

## 5. การทดสอบของฉัน

### Test Case 1

ทำไมเลือก case นี้: ทดสอบว่าถ้ามีตัวอักษรตัวเดียว จะตอบตัวนั้นออกมามั้ย

Input:

```text
z
```

Expected output:

```text
z
```

Actual output:

```text
z
```

Result:

```text
Pass
```

### Test Case 2

ทำไมเลือก case นี้: ทดสอบว่าถ้ามีตัวเดียวกันเกิน 1 คู่แต่เป็นเลขคี่ (5 ตัว) จะเหลือ a 1 ตัวตามที่โจทย์บอกมั้ย

Input:

```text
aaaaa
```

Expected output:

```text
a
```

Actual output:

```text
a
```

Result:

```text
Pass
```

### Test Case 3

ทำไมเลือก case นี้: ทดสอบว่าเรียงตามลำดับที่เจอจริงๆ ไม่ได้เรียงตามตัวอักษร ถ้าเรียงตามตัวอักษรจะได้ xyz ซึ่งผิด

Input:

```text
zyx
```

Expected output:

```text
zyx
```

Actual output:

```text
zyx
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
