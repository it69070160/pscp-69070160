# บันทึกการแก้โจทย์

## 1. ข้อมูล OJ

หมายเลข/ชื่อโจทย์ OJ: OJ3477 - [LEARNING LOGS] Pad Thai

OJ submission ID ถ้ามีการส่งแล้ว: 687525

สถานะ OJ:

```text
Pass
```

เวลาที่ใช้คิดและทำโจทย์ด้วยตนเอง:

```text
15-30 minutes
```

## 2. ความเข้าใจโจทย์ของฉัน

โจทย์ให้ทำผัดไทยโดยใช้วัตถุดิบตามที่เชฟกำหนด 11 อย่างเท่านั้น แล้วเช็ครสชาติว่าครบ Sweet Sour Salty มั้ย จากนั้นให้แสดงคำพูดของเชฟ

input: ชุดแรกรับข้อความทีละบรรทัดเป็นวัตถุดิบ จนกว่าจะเจอ Cook
ชุดที่สองรับข้อความทีละบรรทัดเป็นรสชาติ จนกว่าจะเจอ End

output: ประโยคที่เชฟพูด 1 บรรทัด

constraints: วัตถุดิบหรือรสชาติซ้ำกันได้ อย่างตัวอย่างที่ 2 มี Tofu กับ Egg ซ้ำ และมี Sweet ซ้ำ แต่ยังได้ Delicious! เลยต้องไม่สนตัวซ้ำ
และต้องระวังลำดับการเช็ค ถ้ามีวัตถุดิบนอกสูตรต้องตอบ This is not Pad Thai!!! ก่อนเลย ไม่ว่าวัตถุดิบในสูตรจะครบหรือไม่ครบ

## 3. แผนแรกของฉัน

```text
1 สร้างset วัตถุดิบที่เชฟกำหนดไว้ทั้ง 11 อย่าง และset รสชาติที่ต้องมีคือ Sweet Sour Salty
2 ใช้while loop รับวัตถุดิบมาเรื่อยๆ แล้วadd ลงset จนกว่าจะเจอ Cook ให้break
3 ใช้while loop อีกอันรับรสชาติมาเรื่อยๆ แล้วadd ลงset จนกว่าจะเจอ End ให้break
  ที่ใช้set เพราะตัวที่ซ้ำกันจะถูกตัดออกให้เอง ไม่ต้องมาเช็คซ้ำเอง
4 ทำเงื่อนไขเรียงตามลำดับ
  ถ้าวัตถุดิบที่รับมามีตัวที่ไม่อยู่ในสูตร (ใช้ set ลบกันแล้วยังเหลือ) ให้print This is not Pad Thai!!!
  ถ้าวัตถุดิบไม่เท่ากับสูตรพอดี แปลว่าใส่ไม่ครบ ให้print This is bad!
  ถ้ารสชาติเท่ากับ Sweet Sour Salty พอดี ให้print Delicious!
  นอกเหนือจากนั้นคือรสชาติไม่ครบหรือมีรสอื่นปน ให้print Not Bad...
5 ทดสอบกับtestcase ที่โจทย์ให้มาว่าตรงมั้ย
```

## 4. วิธีสุดท้ายที่ใช้จริง

ใช้วิธีแรกที่คิดได้ เพราะใช้set ทำให้จัดการตัวซ้ำได้ และเทียบว่าครบหรือเกินได้ง่าย

## 5. การทดสอบของฉัน

### Test Case 1

ทำไมเลือก case นี้: ทดสอบว่าถ้าใส่วัตถุดิบครบทุกอย่างและรสชาติครบ แต่มีวัตถุดิบนอกสูตรปนมา จะยังตอบ This is not Pad Thai!!! มั้ย

Input:

```text
Pad Thai Sauce
Tofu
Pickle Turnip
Shrimp
Bean Sprouts
Noodle
Chives
Lime
Egg
Oil
Peanuts
Pork
Cook
Sweet
Sour
Salty
End
```

Expected output:

```text
This is not Pad Thai!!!
```

Actual output:

```text
This is not Pad Thai!!!
```

Result:

```text
Pass
```

### Test Case 2

ทำไมเลือก case นี้: ทดสอบว่าถ้าไม่ใส่วัตถุดิบอะไรเลย แต่รสชาติครบ จะตอบ This is bad! มั้ย

Input:

```text
Cook
Sweet
Sour
Salty
End
```

Expected output:

```text
This is bad!
```

Actual output:

```text
This is bad!
```

Result:

```text
Pass
```

### Test Case 3

ทำไมเลือก case นี้: ทดสอบว่าถ้าวัตถุดิบครบ แต่รสชาติขาดไป 1 อย่าง ถึงจะใส่รสซ้ำหลายรอบก็ต้องตอบ Not Bad... มั้ย

Input:

```text
Pad Thai Sauce
Tofu
Pickle Turnip
Shrimp
Bean Sprouts
Noodle
Chives
Lime
Egg
Oil
Peanuts
Cook
Sweet
Salty
Sweet
Salty
End
```

Expected output:

```text
Not Bad...
```

Actual output:

```text
Not Bad...
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
