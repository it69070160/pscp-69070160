# บันทึกการแก้โจทย์

## 1. ข้อมูล OJ

หมายเลข/ชื่อโจทย์ OJ: OJ3381 - [LEARNING LOGS] Point Sorting

OJ submission ID ถ้ามีการส่งแล้ว: 687206

สถานะ OJ:

```text
Pass
```

เวลาที่ใช้คิดและทำโจทย์ด้วยตนเอง:

```text
0-15 minutes
```

## 2. ความเข้าใจโจทย์ของฉัน

โจทย์ต้องการให้เรียงจุดบนระนาบตามค่า f(x,y) = x + y จากน้อยไปมาก ถ้าค่า f เท่ากันให้จุดที่ y มากกว่ามาก่อน

- input: บรรทัดแรกคือจำนวนชุดข้อมูล T แต่ละชุดจะมีบรรทัดแรกเป็นจำนวนจุด N แล้วอีก N บรรทัดเป็นพิกัด x y ต้องใช้split แยกค่าแล้วทำเป็นint
- output: พิกัดของจุดที่เรียงแล้ว บรรทัดละ 1 จุด ทำแบบนี้ทุกชุดข้อมูล
- constraints: พิกัดติดลบได้ ตั้งแต่ -10000 ถึง 10000 และตอนที่ค่า f เท่ากันต้องเรียง y จากมากไปน้อย ซึ่งกลับทางกับ f ที่เรียงจากน้อยไปมาก

## 3. แผนแรกของฉัน

```text
1. รับค่า T มาก่อนเป็นint แล้วใช้for loop ตามจำนวนชุดข้อมูล
2. ในแต่ละชุด รับค่า N แล้วใช้for loop รับพิกัด x y เก็บลงlist เป็นคู่
3. ใช้sort โดยใส่key เป็น lambda ที่คืนค่า (x + y, -y)
   ตัวแรกเรียงตามค่า f จากน้อยไปมาก ส่วนตัวที่สองใส่ - ให้ y เพื่อให้ y ที่มากกว่าได้ค่าน้อยกว่า จะได้มาก่อนตอนที่ f เท่ากัน
4. ใช้for loop print พิกัดที่เรียงแล้วทีละบรรทัด
5. ทดสอบกับtestcase ที่โจทย์ให้มาว่าตรงมั้ย
```

## 4. วิธีสุดท้ายที่ใช้จริง

ใช้วิธีแรกที่คิดได้

## 5. การทดสอบของฉัน

### Test Case 1

ทำไมเลือก case นี้: ทดสอบว่าถ้ามีจุดเดียวจะ error มั้ย

Input:

```text
1
1
0 0
```

Expected output:

```text
0 0
```

Actual output:

```text
0 0
```

Result:

```text
Pass
```

### Test Case 2

ทำไมเลือก case นี้: ทดสอบว่าถ้าค่า f เท่ากันทุกจุด จะเรียง y จากมากไปน้อยถูกมั้ย

Input:

```text
1
3
2 3
5 0
0 5
```

Expected output:

```text
0 5
2 3
5 0
```

Actual output:

```text
0 5
2 3
5 0
```

Result:

```text
Pass
```

### Test Case 3

ทำไมเลือก case นี้: ทดสอบพิกัดติดลบ ว่าการเรียงค่า f ที่ติดลบยังถูกอยู่มั้ย

Input:

```text
1
3
-3 -4
10 -20
0 0
```

Expected output:

```text
10 -20
-3 -4
0 0
```

Actual output:

```text
10 -20
-3 -4
0 0
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

ไม่ได้ใช้ AI เพราะเขียนเอง

## 7. ความช่วยเหลือจากคน / การร่วมมือ

ได้ถามเพื่อน TA ผู้สอน หรือบุคคลอื่นเพื่อขอความช่วยเหลือในโจทย์นี้หรือไม่

```text
No
```

ใครช่วยคุณ: -

เขาช่วยอะไร: -

คุณยังทำอะไรด้วยตนเอง: ทำเองทั้งหมด

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
