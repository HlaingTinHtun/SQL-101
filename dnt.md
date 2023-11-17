# Date and Time

ဒီအပိုင်းမှာတော့ date, time ရဲ့ data type အကြောင်းနဲ့အသုံးပြုပုံ functions တွေအကြောင်းကိုရေးသွားမှာဖြစ်ပါတယ်။

`DATE, TIME` data type အသစ်တွေကိုစမ်းမှာဖြစ်တဲ့အတွက်လက်ရှိရှိပြီးသား `students` table ကိုဖြုတ်ချပြီး table အသစ်ဆောက်လိုက်ပါမယ်။ 

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt1.png)

column အသစ်သုံးခုထည့်ပါမယ်။
`birth_date` ကို `Date`
`class_time` အတန်းထဲရှိတဲ့အချိန်ကို `TIME`
`last_updated` လက်ရှိ record/row ကိုနောက်ဆုံးပြင်ဆင်ထားချိန်ကို `DATETIME`
အဖြစ်သတ်မှတ်ပေးထားလိုက်ပါတယ်။ သုံးမျိုးလုံးကိုစမ်းပြပေးချင်လို့ပါ။

အောက်က `CREATE` query နဲ့ data ထည့်မယ့် `INSERT` query ကိုအသုံးပြုနိုင်ပါတယ်။

```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    nick_name VARCHAR(50),
    age INT,
    major VARCHAR(50),
    birth_date DATE,
    class_time TIME,
    last_updated DATETIME
);
```

```
INSERT INTO students (student_id, name, nick_name, age, major, birth_date, class_time, last_updated)
VALUES
    (1, 'John Doe', 'JD', 20, 'Computer Science', '2000-05-15', '14:30:00', '2022-10-18 08:45:00'),
    (2, 'Jane Smith', 'JS', 22, 'Mathematics', '1999-09-10', '10:45:00', '2021-08-25 15:20:00'),
    (3, 'Alice Johnson', 'AJ', 21, 'History', '2002-03-01', '18:15:00', '2023-01-12 12:30:00'),
    (4, 'Bob Williams', 'BW', 20, 'Chemistry', '2001-08-12', '08:00:00', '2022-05-07 20:10:00'),
    (5, 'Eva Brown', 'EB', 22, 'Biology', '1999-12-05', '21:20:00', '2021-11-30 11:55:00'),
    (6, 'Charlie Davis', 'CD', 21, 'Physics', '2000-06-20', '12:10:00', '2022-03-17 17:40:00'),
    (7, 'John Doe', 'JD', 20, 'Computer Science', '2000-05-15', '14:30:00', '2022-10-18 08:45:00'),  -- Duplicate name data
    (8, 'Alice Johnson', 'AJ', 21, 'History', '2002-03-01', '18:15:00', '2023-01-12 12:30:00');  -- Duplicate name data
```
![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt2.png)

---


များသောအားဖြင့်ကျနော်တို့မြင်တွေ့ရမယ့် type ပုံစံတွေက
DATE (နေ့စွဲ)
TIME (အချိန်)
DATETIME (နေ့စွဲ+အချိန်)

Format ကတော့
DATE ဆို (YYYY-MM-DD)
TIME ဆို (HH:MI:SS)
DATETIME ဆို (YYYY-MM-DD HH:MI:SS) ဆိုပြီးရှိပါတယ်။
ဒီ format အထားအသိုကိုလည်းလိုသလိုပြောင်းနိုင်ပါတယ်။ 
```
YYYY - year
MM - month
DD - date
HH - hour
MI - minute
SS- second
```

Keyword တွေကအသုံးပြုတဲ့ DBMS ပေါ်လိုက်ပြီးတော့ပြောင်းနိုင်တာကိုလည်းသတိချပ်ထားရပါတယ်။ အခုကျနော်တို့က MySQL ကိုသုံးနေတာဖြစ်ပါတယ်။

## NOW, CURRENT_DATE, CURRENT_TIMESTAMP

လက်ရှိအချိန်၊နေ့ရက်တွေကိုရချင်တယ်ဆို ဒီ function တွေကိုအောက်ကလိုအသုံးပြုနိုင်ပါတယ်။

```
SELECT NOW() AS CurrentDateAndTime;
```

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt3.png)

---
```
SELECT CURRENT_DATE AS CurrentDate;
```
![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt4.png)

```
SELECT CURRENT_TIMESTAMP AS CurrentTimestamp;
```
![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt5.png)

---

## TIMESTAMPDIFF

အချိန်ကွာခြားချက်ကိုသိနိုင်ဖို့အတွက် `TIMESTAMPDIFF` ကိုအသုံးပြုနိုင်ပါတယ်။


ကျောင်းသားတွေရဲ့အသက်ကိုတွက်ကြည့်ရအောင်။
တွက်ဖို့ဆိုလက်ရှိအချိန်နဲ့ `birth_date` column ကိုတန်ဖိုးကွာခြားချက်ကို `YEAR` ဆိုတဲ့ filter နဲ့ချလိုက်မယ်ဆိုကျောင်းသားတွေရဲ့ လက်ရှိအသက်ရလာနိုင်ပါတယ်။ အောက်ကရေးပုံကိုကြည့်နိုင်ပါတယ်။

```
SELECT name, TIMESTAMPDIFF(YEAR, birth_date, CURDATE()) AS AgeInYears
FROM students;
```
![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt6.png)

---

ဒီတစ်ခါအသက်တွေကို YEAR နဲ့မဟုတ်ဘဲ  MONTH နဲ့ကြည့်ရအောင်။ `YEAR` keyword အစား `MONTH` ဆိုတဲ့ keyword ကိုအစားထိုးအသုံးပြုနိုင်ပါတယ်။

```
SELECT name, TIMESTAMPDIFF(MONTH, birth_date, CURDATE()) AS AgeInMonths
FROM students;
```

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt7.png)

---

## DATE_ADD, DATE_SUB

နေ့ရက်အချိန်တွေကိုပေါင်းခြင်း၊ နုတ်ခြင်းတို့လည်းလုပ်ဆောင်နိုင်ပါတယ်။
ပေါင်းတာနုတ်တာမြင်သာအောင် query မ run ခင်အရင် select * နဲ့ အချိန်၊နေ့စွဲတွေကိုကြည့်ထားနိုင်ပါတယ်။

`last_updated` ဆိုတဲ့ column ရဲ့တန်ဖိုးကို အချိန် ၂ နှစ်ထည့်ပေါင်းကြည့်ရအောင်။

```
SELECT name, DATE_ADD(last_updated, INTERVAL 2 YEAR) AS NewLastUpdated
FROM students;
```

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt8.png)

---

`class_time` column ရဲ့အချိန်တန်ဖိုးထဲကမိနစ်သုံးဆယ်နုတ်ကြည့်ရအောင်။

```
SELECT name, DATE_SUB(class_time, INTERVAL 30 MINUTE) AS NewClassTime
FROM students;
```

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt9.png)

---

## EXTRACT 

column ထဲက date time တန်ဖိုးထဲကမှကိုယ်လိုချင်တဲ့အပိုင်းကိုပဲထုတ်ယူလို့လည်းရပါတယ်။
ဥပမာ `YYYY-MM-HH` ထဲ က `YYYY` ကိုလည်းလိုချင်တယ်၊ `MM` ပဲလိုချင်တယ်ဆိုတဲ့အခြေအနေမျိုးတွေမှာ `EXTRACT`ကိုသုံးနိုင်ပါတယ်။

`birth_date` column ထဲကမှ `year` ကိုပဲဆွဲထုတ်ကြည့်ကြည့်ရအောင်။ 
```
SELECT name, EXTRACT(YEAR FROM birth_date) AS BirthYear
FROM students;
```

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt10.png)

---

`class_time` column ထဲက `hour` ကိုပဲဆွဲထုတ်ကြည့်ရအောင်။
```
SELECT name, EXTRACT(HOUR FROM class_time) AS ClassHour
FROM students;
```

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt11.png)

---

## DATE_FORMAT 

အရှေ့မှာ date, time format တွေကိုလိုသလိုပြောင်းလို့ရတယ်လို့ကျနော်ပြောခဲ့ပါတယ်။
`DATE_FORMAT` ဆိုတဲ့ function ကိုသုံးပြီးတော့ပြောင်းနိုင်ပါတယ်။

`birth_date` ကို format နောက်တစ်မျိုးဖြစ်တဲ့  `Month DD, YYYY` အဖြစ်ပြောင်းကြည့်ပါမယ်။
```
SELECT name, DATE_FORMAT(birth_date, '%M %d, %Y') AS FormattedBirthDate
FROM students;
```

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt12.png)

---

`last_updated` ကိုလည်း `YYYY-MM-DD HH:MI AM/PM` အဖြစ်ပြောင်းကြည့်ပါမယ်။

```
SELECT name, DATE_FORMAT(last_updated, '%Y-%m-%d %h:%i %p') AS FormattedLastUpdated
FROM students;
```

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt13.png)

---

`class_time` ကိုလည်း `HH:MI AM/PM` အဖြစ်ပြောင်းကြည့်ပါမယ်။

```
SELECT name, DATE_FORMAT(class_time, '%h:%i %p') AS FormattedClassTime
FROM students;
```

![dnt](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dnt/dnt14.png)

---

တစ်ခြားသော function တွေလည်းများစွာရှိပါသေးတယ်၊ ကျနော်လိုသလောက်ပဲထုတ်နုတ်ထားလိုက်တာပါ။အခုအပိုင်းကအရင်ရေးခဲ့တဲ့ queries တွေနဲ့မတူဘဲနည်းနည်းလေးခက်ကောင်းခက်နိုင်ပါတယ်။ function တွေအသုံးပြုတာပါလာတာရယ်၊ format လေးတွေပါလာတာရယ်ကြောင့်ပါ။ သို့ပေမယ့် များများလေ့ကျင့်လိုက်ရင်တော့ကျင့်သားရလာမှာပါ။ 

`DATE & TIME` data တွေကမရှိမဖြစ်ပါလေ့ရှိတာကြောင့် ကိုယ်လိုသလိုဆွဲထုတ်ချင်လာတဲ့အချိန်မှာအခုပြောခဲ့တဲ့အရာလေးတွေကအသုံးဝင်လာမယ်လို့ထင်ပါတယ်။
