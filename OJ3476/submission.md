# บันทึกการแก้โจทย์

## 1. ข้อมูล OJ

หมายเลข/ชื่อโจทย์ OJ: OJ3476 - [LEARNING LOGS] CuteCat CuteFox

OJ submission ID ถ้ามีการส่งแล้ว: 687567

สถานะ OJ:

```text
Pass
```

เวลาที่ใช้คิดและทำโจทย์ด้วยตนเอง:

```text
15-30 minutes
```

## 2. ความเข้าใจโจทย์ของฉัน

โจทย์ให้หาว่าในฝูงมีแมวกับจิ้งจอกทั้งหมดกี่ตัว แล้วแสดงชื่อพร้อมหมายเลขเรียงตามหมายเลข
ถ้าไม่มีใครเป็น Cat01 ให้มี Garfield เป็น Cat01 และถ้าไม่มีใครเป็น Fox01 ให้มี Fubuki เป็น Fox01

input: บรรทัดแรกคือจำนวน n อีก n บรรทัดเป็นdict ที่มี key เป็นชื่อ และ value เป็นชนิดกับหมายเลข เช่น {"Chi" : "Cat06"}

output: บรรทัดแรกคือจำนวนแมว บรรทัดที่สองคือจำนวนจิ้งจอก แล้วตามด้วยชื่อ : หมายเลข ของแมวทั้งหมดก่อน แล้วค่อยเป็นจิ้งจอก เรียงตามหมายเลข

constraints: ตอนแรกคิดว่าแค่ไม่มี Cat01 ก็เติม Garfield ได้เลย แต่พอดูตัวอย่างที่ 3 ไม่มี Cat01 แต่ไม่มี Garfield ออกมา
เพราะ Garfield ถูกใช้เป็นชื่อของ Fox06 ไปแล้ว และโจทย์บอกว่าชื่อห้ามซ้ำ เลยต้องเช็คทั้งหมายเลขและชื่อก่อนจะเติมตัว default
อีกอย่างคือต้องเรียงตามตัวเลขจริงๆ ไม่ใช่เรียงตามstr เผื่อมีหมายเลขที่หลักไม่เท่ากัน

## 3. แผนแรกของฉัน

```text
1 รับค่า n เป็นint แล้วสร้างdict ว่างไว้เก็บข้อมูลฝูง
2 ใช้for loop ตามจำนวน n รับแต่ละบรรทัดมาแปลงเป็นdict ด้วย ast.literal_eval แล้วใช้ update รวมเข้าdict หลัก
3 เช็คว่า Cat01 ไม่อยู่ใน values() และชื่อ Garfield ไม่อยู่ใน keys ถ้าใช่ทั้งคู่ให้เพิ่ม Garfield : Cat01
  ทำแบบเดียวกันกับ Fox01 และ Fubuki
4 ใช้items() แยกแมวกับจิ้งจอกออกเป็น2 list โดยดูว่า value ขึ้นต้นด้วย Cat หรือ Fox
5 sort ทั้ง2 list โดยใช้key เป็นตัวเลขหลังชนิด คือ int(value[3:])
6 print จำนวนแมว จำนวนจิ้งจอก แล้วfor loop print ชื่อ : หมายเลข ของแมวก่อนแล้วตามด้วยจิ้งจอก
7 ทดสอบกับtestcase ที่โจทย์ให้มาทั้ง 3 อัน
```

## 4. วิธีสุดท้ายที่ใช้จริง

ใช้แผนเดิมแต่แก้ตรงขั้นตอนที่ 3 ตอนแรกเช็คแค่ว่าไม่มี Cat01 กับ Fox01 พอรันตัวอย่างที่ 3 แล้วมี Garfield เกินมา เลยเพิ่มเงื่อนไขเช็คชื่อซ้ำเข้าไปด้วย

## 5. การทดสอบของฉัน

### Test Case 1

ทำไมเลือก case นี้: ทดสอบว่าถ้ามีแมวแค่ตัวเดียวและไม่มีจิ้งจอกเลย จะเติม Garfield กับ Fubuki ให้ครบมั้ย

Input:

```text
1
{"Tom" : "Cat02"}
```

Expected output:

```text
Cat : 2
Fox : 1
Garfield : Cat01
Tom : Cat02
Fubuki : Fox01
```

Actual output:

```text
Cat : 2
Fox : 1
Garfield : Cat01
Tom : Cat02
Fubuki : Fox01
```

Result:

```text
Pass
```

### Test Case 2

ทำไมเลือก case นี้: ทดสอบว่าเรียงตามตัวเลขถูกมั้ย ถ้าใส่ Cat10 ก่อน Cat09 ต้องเอา Cat09 ขึ้นก่อน

Input:

```text
2
{"Mochi" : "Cat10"}
{"Momo" : "Cat09"}
```

Expected output:

```text
Cat : 3
Fox : 1
Garfield : Cat01
Momo : Cat09
Mochi : Cat10
Fubuki : Fox01
```

Actual output:

```text
Cat : 3
Fox : 1
Garfield : Cat01
Momo : Cat09
Mochi : Cat10
Fubuki : Fox01
```

Result:

```text
Pass
```

### Test Case 3

ทำไมเลือก case นี้: ทดสอบว่าถ้าชื่อ Fubuki ถูกเอาไปใช้เป็นแมวแล้ว จะไม่เติม Fubuki เป็น Fox01 ซ้ำอีก แต่ยังเติม Garfield ได้ตามปกติ

Input:

```text
2
{"Fubuki" : "Cat02"}
{"Kitsune" : "Fox03"}
```

Expected output:

```text
Cat : 2
Fox : 1
Garfield : Cat01
Fubuki : Cat02
Kitsune : Fox03
```

Actual output:

```text
Cat : 2
Fox : 1
Garfield : Cat01
Fubuki : Cat02
Kitsune : Fox03
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
