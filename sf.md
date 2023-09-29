## Sorting & filtering

ဒီအပိုင်းမှာတော့ db ထဲက  data တွေကို sorting စီတာတွေနဲ့ လိုအပ်တဲ့ data ကိုပဲသီးသန့်ဆွဲထုတ်တဲ့ `filtering` queries တွေကိုလေ့လာသွားကြပါမယ်။

`sql_test` ဆိုတဲ့ database ထဲမှာ `students` table တစ်လုံးဆောက်ထားလိုက်ပြီး `INSERT` command နဲ့ data တစ်ချို့ထည့်သွင်းထားပါမယ်။ ဒီ students table ကိုအသုံးပြုပြီး sorting နဲ့ filtering လုပ်တဲ့ queries တွေစမ်းသပ်သွားပါမယ်။

![SF1](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf1.png)

---
```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    nick_name VARCHAR(50),
    age INT,
    major VARCHAR(50)
);
```
```
INSERT INTO students (student_id, name, nick_name, age, major)
VALUES
    (1, 'John Doe', 'JD', 20, 'Computer Science'),
    (2, 'Jane Smith', 'JS', 22, 'Mathematics'),
    (3, 'Alice Johnson', 'AJ', 21, 'History'),
    (4, 'Bob Williams', 'BW', 20, 'Chemistry'),
    (5, 'Eva Brown', 'EB', 22, 'Biology'),
    (6, 'Charlie Davis', 'CD', 21, 'Physics'),
    (7, 'John Doe', 'JD', 20, 'Computer Science'),
    (8, 'Alice Johnson', 'AJ', 21, 'History');
```
`select *` နဲ့ data တွေကိုပြန်စစ်ကြည့်နိုင်ပါတယ်။

![SF2](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf2.png)

---

#### ORDER BY

Sorting စီဖို့အတွက် SQL မှာတော့ `ORDER BY` ဆိုတဲ့ command ကိုအသုံးပြုပါတယ်။ လိုအပ်သလို `ASC` ascending, `DESC` descending options တွေကိုအသုံးပြုနိုင်ပါတယ်။
`students` table ထဲက `name` တွေကို `ORDER BY` command အသုံးပြုပြီး `ASC`option နဲ့အစဉ်လိုက်စီကြည့်ပါမယ်။
```
SELECT * FROM students
ORDER BY name ASC;
```
![SF3](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf3.png)

---
`DESC` descending နဲ့စီမယ်ဆိုရင်တော့အခုရနေတဲ့ result `a to z` ကနေ `z to a` အဖြစ်ပြောင်းပြန်ရမှာဖြစ်ပါတယ်။

အသက် `age` column ကိုထောက်ပြီး `DESC` option နဲ့စီကြည့်ရအောင်၊ အသက်ကြီးဆုံးလူအရင်ပြဆိုတဲ့သဘောပေါ့။

```
SELECT * FROM students
ORDER BY age DESC;
```

![SF4](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf4.png)

---
`ASC` နဲ့စီမယ်ဆိုရင်တော့ထုံးစံအတိုင်းပြောင်းပြန် ပြန်ဖြစ်သွားပြီးတော့ အငယ်ဆုံး student ကိုအရင်ပြမှာဖြစ်ပါတယ်။


#### DISTINCT
`select` ဆွဲတဲ့နေရာမှာ unique ဖြစ်တဲ့ record တွေပဲလိုချင်တဲ့အချိန်မှာ `DISTINCT` ဆိုတဲ့ keyword ကိုသုံးပါတယ်။
ဥပမာ `students` table ထဲက `major` နာမည်တွေလိုချင်တယ်၊ သို့ပေမယ့် ထပ်နေတဲ့ (duplicate) record တွေမပါချင်ဘူးဆိုတဲ့အခြေအနေမှာ `DISTINCT` ကိုသုံးနိုင်ပါတယ်
```
SELECT DISTINCT major FROM students;
```

![SF5](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf5.png)

---
#### LIMIT
Table ထဲက records တွေအကုန်လုံးပါမလာချင်ဘူး၊ record ၂ခုပဲပါချင်တယ်၊ ၃ခုပဲပါချင်တယ်ဆိုတဲ့အခြေအနေမှာ `LIMIT` ခံပြီး select ဆွဲနိုင်ပါတယ်။
```
SELECT * FROM students LIMIT 2;
```
![SF6](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf6.png)

---
#### OFFSET
select ဆွဲတဲ့နေရာမှာ records တစ်ချို့ကိုကျော်ပြီးဆွဲချင်တယ် သို့ စမှတ်ကိုပြောင်းပြီးသတ်မှတ်ချင်တယ်ဆိုရင် `OFFSET` ကိုသုံးနိုင်ပါတယ်။ query နဲ့ screenshot ကိုတွဲပြီးကြည့်မယ်ဆိုပိုသဘောပေါက်လွယ်ပါမယ်။
Records ၃ခုကိုကျော်ပြီး LIMIT ကို 2လို့ခံပြီးဆွဲမယ်ဆို result အဖြစ် 4 ကစမယ်၊ LIMIT 2 ဖြစ်တဲ့အတွက် 2 rows ပဲထုတ်သွားမှာဖြစ်ပါတယ်။

```
SELECT * FROM students LIMIT 2 OFFSET 3;
```

![SF7](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf7.png)

---
#### Filtering

Filtering ကစိမ်းတဲ့အရာတစ်ခုတော့မဟုတ်ပါဘူး၊ အရှေ့က DQL အပိုင်းမှာ `WHERE` keyword ကိုသုံးပြီး query တွေဆွဲခဲ့ပါသေးတယ်။ Data တွေကို filter လုပ်တဲ့နေရာမှာ `WHERE` ကိုအသုံးပြုနိုင်ပါတယ်။ ဒီအပိုင်းမှာတော့ `WHERE` ကိုတစ်ချို့ commands လေးတွေပါ conjunction လုပ်ပြီးသုံးကြည့်ကြပါမယ်။

Computer Science `major` နဲ့ကျောင်းသားတွေကိုဆွဲထုတ်ကြည့်ရအောင်။
```
SELECT * FROM students
WHERE major = 'Computer Science';
```

![SF8](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf8.png)

---
#### LIKE
LIKE ကိုလည်းအရှေ့မှာတစ်ခေါက်ပြောထားပြီးသားဖြစ်ပါတယ်။ search လုပ်မယ့်နေရာမှာသုံးပါတယ်။ နာမည်မှာ J နဲ့ စတဲ့ကျောင်းသားတွေကိုဆွဲထုတ်ကြည့်ချင်တယ်ဆိုပါစို့။ 

```
SELECT * FROM students
WHERE name LIKE 'J%';
```

![SF9](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf9.png)

---
#### BETWEEN
Range condition တစ်ခုကြားထဲက data တွေကိုဆွဲထုတ်ချင်တဲ့အချိန်မှာသုံးပါတယ်။
ဥပမာ အသက် 20 နဲ့ 21 ကြားထဲကကျောင်းသားတွေကိုလိုချင်တယ်ဆိုပါစို့။

```
SELECT * FROM students
WHERE age BETWEEN 20 AND 21;
```

![SF10](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf10.png)

---
#### Combining
အထက်မှာဖော်ပြခဲ့တဲ့ sorting နဲ့ filter commands တွေကိုပေါင်းပြီးအသုံးပြုကြည့်ပါမယ်။
အသက်ကို ငယ်စဉ်ကြီးလိုက်နဲ့ Biology major ဖြစ်တဲ့ကျောင်းသားတွေကိုဆွဲထုတ်ကြည့်ပါမယ်။
```
SELECT * FROM students
WHERE major = 'Biology'
ORDER BY age ASC;
```

![SF11](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf11.png)

---
အရှေ့အပိုင်းတွေမှာ WHERE ကို AND, OR ခံပြီးသုံးတာတွေရှိခဲ့ပါတယ်။ အခု query မှာ WHERE ကို နည်းနည်းပို advance ဖြစ်တဲ့နည်းနဲ့သုံးကြည့်ပါမယ်။

Table ထဲမှာ age 22 ဖြစ်တဲ့ကျောင်းသားကိုဆွဲမယ်၊ ပြီးတော့ကျောင်းသားက Computer Science သို့ Mathematics major ဖြစ်ရမယ်။ ဒီလိုမျိုး case မှာအောက်က query လိုမျိုး `( )` ရေးပေးခြင်းက conflict ဖြစ်နိုင်မယ့်အခြေအနေကိုကာကွယ်ပေးနိုင်ပါတယ်။
 
```
SELECT * FROM students
WHERE (major = 'Computer Science' OR major = 'Mathematics')
AND age = 22;
 ```
 
![SF12](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/sf/sf12.png)

---
Sorting & filtering အပိုင်းမှာအသုံးများတဲ့ဥပမာတွေနဲ့တကွရေးသားပေးခဲ့ပါတယ်။ တစ်ချို့အရှေ့မှာပါပြီးသား commands တွေပြန်ပါတာတွေ့ရပါမယ်။ မျက်မှန်းတန်းမိသွားစေချင်တာအပြင် conjunction လုပ်ပြီးစမ်းသုံးကြည့်စေချင်ပါတယ်။ query တစ်ခုမှာ keyword ၃ ၄ ခုထည့်ပြီး select တွေဆွဲကြည့်ခြင်းဖြင့် နားလည်ထားတဲ့အရာတွေကိုပိုမို strong ဖြစ်လာစေတဲ့အပြင် real world queries တွေနဲ့လည်းပိုနီးစပ်လာနိုင်မှာဖြစ်ပါတယ်။
