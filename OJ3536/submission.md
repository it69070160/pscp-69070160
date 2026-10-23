# บันทึกการแก้โจทย์

## 1. ข้อมูล OJ

หมายเลข/ชื่อโจทย์ OJ: OJ3536 - [LEARNING LOGS] isPrime_large

OJ submission ID ถ้ามีการส่งแล้ว: __695338__

สถานะ OJ:

```text
Pass
```

เวลาที่ใช้คิดและทำโจทย์ด้วยตนเอง:

```text
0-15 minutes
```

## 2. ความเข้าใจโจทย์ของฉัน

โจทย์ให้เช็คว่าจำนวนนับที่รับมาเป็นจำนวนเฉพาะหรือไม่ คือมีแค่ 1 กับตัวมันเองที่หารลงตัว

input: จำนวนนับ 1 บรรทัด รับมาเป็นint

output: YES ถ้าเป็นจำนวนเฉพาะ NO ถ้าไม่เป็น

constraints: ตัวเลขใหญ่ได้มาก อย่างตัวอย่างที่ 6 คือ 1000000007 ถ้าวนloop ไล่หารตั้งแต่ 2 ถึง n จะช้าเกิน 1 วินาที
ต้องทำให้เป็น O(n**0.5) ถึงจะผ่านครบ และต้องดักเลข 1 ไว้ด้วยเพราะ 1 ไม่ใช่จำนวนเฉพาะ

## 3. แผนแรกของฉัน

```text
1 เอาโปรแกรมข้อ isPrime_small มาลองก่อน คือรับค่า n แล้วใช้for loop ไล่หารตั้งแต่ 2 ถึง n-1
2 ถ้ามีตัวไหนหารลงตัวให้ตอบ NO ถ้าไม่มีเลยให้ตอบ YES
3 ลองรันกับตัวอย่างที่ 6 คือ 1000000007 แล้วช้ามาก ไม่ทันเวลาแน่นอน
```

## 4. วิธีสุดท้ายที่ใช้จริง

ปรับจากวิธีแรก เพราะถ้า n หารด้วยเลขที่มากกว่ารากที่สองของ n ลงตัว จะต้องมีอีกตัวที่น้อยกว่ารากที่สองหารลงตัวด้วยเสมอ เลยเช็คแค่ถึงรากที่สองก็พอ

```text
1 รับค่า n เป็นint ถ้า n <= 1 ให้print NO แล้วreturn ออกเลย
2 ตั้งตัวแปร is_prime = True ไว้ก่อน
3 ใช้for loop ตั้งแต่ 2 ถึง int(n ** 0.5) + 1 ที่ใช้ ** 0.5 เพราะไม่ต้องimport math
ที่ต้อง +1 เพราะ range ไม่รวมตัวสุดท้าย ถ้าไม่บวกจะไม่ได้เช็คตัวรากที่สองพอดี เช่น 49 จะไม่ได้เช็ค 7
4 ถ้า n % i เป็น 0 ให้ is_prime = False แล้วbreak ออกจากloop เลย ไม่ต้องเช็คต่อ
5 print YES หรือ NO ตามค่า is_prime
```

## 5. การทดสอบของฉัน

### Test Case 1

ทำไมเลือก case นี้: ทดสอบว่า 1 ต้องตอบ NO เพราะ 1 มีตัวหารแค่ตัวเดียว ไม่ใช่จำนวนเฉพาะ

Input:

```text
1
```

Expected output:

```text
NO
```

Actual output:

```text
NO
```

Result:

```text
Pass
```

### Test Case 2

ทำไมเลือก case นี้: ทดสอบเลขที่เป็นกำลังสองของจำนวนเฉพาะ ว่า +1 ใน range ทำให้เช็คถึงรากที่สองพอดีมั้ย ถ้าลืม +1 จะตอบ YES ผิด

Input:

```text
49
```

Expected output:

```text
NO
```

Actual output:

```text
NO
```

Result:

```text
Pass
```

### Test Case 3

ทำไมเลือก case นี้: ทดสอบจำนวนเฉพาะที่ใหญ่กว่าตัวอย่างในโจทย์มาก ว่ายังทำงานทันเวลามั้ย

Input:

```text
999999999989
```

Expected output:

```text
YES
```

Actual output:

```text
YES
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
