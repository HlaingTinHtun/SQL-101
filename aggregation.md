
## Aggregation

Data တွေကိုစုပေါင်းပြီးတော့တွက်ချက်မှုတွေ၊ report ပုံစံမျိုးတွေထုတ်ပေးနိုင်ဖို့အတွက် SQL က Aggregations ဆိုတဲ့ functions တွေကို support လုပ်ပေးထားပါတယ်။ သဘောတရားကိုပိုနားလည်နိုင်ဖို့အတွက်အောက်က query တွေစမ်းရေးကြည့်ပြီး results တွေကိုကြည့်နိုင်ပါတယ်။

သုံးနေကျ `students` table ကိုပဲဆက်သုံးကြပါမယ်။


### COUNT

ထွက်လာမယ့် result set တစ်ခုရဲ့data rows တွေကိုတွက်ချင်တဲ့အချိန်မှာ COUNT ဆိုတဲ့ function ကိုသုံးနိုင်ပါတယ်။

```
SELECT COUNT(*) AS TotalStudents
FROM students;
```

![ag1](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ag/ag1.png)

---
COUNT(*) ဆိုပြီး `*` ကိုသုံးပြီးတော့အားလုံးးရဲ့ results ကိုယူပါမယ်။ 
`AS TotalStudents` ဆိုတာကတော့ `alias` ပေးလိုက်တာဖြစ်ပါတယ်။ `alias` ဆိုတာကတော့အသုံးပြု (ပြန်ခေါ်လို့ရမယ့်)နာမည်တစ်ခုပေးလိုက်တာလို့ဆိုနိုင်ပါတယ်။ လောလောဆယ်သိပ်နားမလည်လည်းရပါတယ်။

`alias` မပါဘဲတန်းသုံးလည်းရပါတယ်။ ထွက်လာတဲ့ column နာမည်နေရာမှာတော့ `alias` နာမည်မဟုတ်တော့ဘဲ  `COUNT(*)` ဆိုပြီးတော့ဘဲပါလာပါမယ်။ ဒါကြောင့်ပြန်ခေါ်သုံးရလွယ်အောင် နားလည်ရလွယ်ကူတဲ့ `alias` နာမည်လေးတွေပေးပြီး query ရေးလေ့ရှိကြပါတယ်။

![ag2](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ag/ag2.png)

---

### SUM

ကိန်းဂဏန်းတွေရှိတဲ့ column တွေရဲ့တန်ဖိုးတွေကိုစုပြီးပေါင်းချင်တဲ့အချိန်မှာ `SUM` ကိုသုံးနိုင်ပါတယ်။ ဥပမာ `students` table ထဲက `age` column တွေအကုန်ပေါင်းချင်တယ်ဆိုပါစို့၊ အောက်ကလိုမျိုး `SUM` ကိုသုံးပြီးရေးနိုင်ပါတယ်။
```
SELECT SUM(age) AS TotalAge
FROM students;
```

![ag3](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ag/ag3.png)

---

### AVG

AVG ကတော့ `SUM`နဲ့ပုံစံတူပဲ၊ သို့ပေမယ့်ပေါင်းတာမဟုတ်ဘဲနဲ့ Average ကိုတွက်ပေးတာဖြစ်ပါတယ်။ `students` table ထဲက `age` column ရဲ့ average ကိုတွက်ကြည့်ရအောင်။ (ဥပမာဒီကျောင်းကကျောင်းသားတွေရဲ့ average age ကဘယ်လောက်လဲဆိုတာမျိုးတွက်တဲ့နေရာမျိုးမှာအသုံးဝင်ပါတယ်။)

```
SELECT AVG(age) AS AverageAge
FROM students;
```

![ag4](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ag/ag4.png)

### MIN
`MIN` ကတော့အသေးဆုံးကိန်းဂဏန်းကိုဆွဲထုတ်ချင်တဲ့အချိန်မျိုးမှာသုံးပါတယ်။ `students` table ထဲကအသက်အငယ်ဆုံးကျောင်းသားကိုသိချင်တယ်ဆိုရင် ဒီလိုမျိုးထုတ်ကြည့်နိုင်ပါတယ်။
```
SELECT MIN(age) AS YoungestAge
FROM students;
```
![ag5](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ag/ag5.png)

---

### MAX

`MAX` ကတော့ `MIN` နဲ့ပြောင်းပြန်အကြီးဆုံးကိုဆွဲထုတ်တာဖြစ်ပါတယ်။
```
SELECT MAX(age) AS OldestAge
FROM students;
```
![ag6](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ag/ag6.png)

---

### GROUP BY

`GROUP BY` ကိုအရှေ့မှာတွေ့ပြီးသားဖြစ်မှာပါ။ ထပ်ဖော်ပြရတဲ့အကြောင်းရင်းက Aggregation function တွေသုံးပြီး query ဆွဲတဲ့အချိန်မှာ `GROUP BY` ကိုသုံးပြီး group လေးတွေခွဲပြီး data တွေကိုထုတ်ကြည့်လို့ရပါတယ်။ ဥပမာ `major` တစ်ခုချင်းစီမှာကျောင်းသားဘယ်နှစ်ယောက်ရှိလဲဆိုတာမျိုးသိချင်ရင် `GROUP BY` ကို Aggregation function တွေနဲ့ပေါင်းပြီးအောက်ကလိုသုံးနိုင်ပါတယ်။

```
SELECT major, COUNT(*) AS NumberOfStudents
FROM students
GROUP BY major;
```

![ag7](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ag/ag7.png)

---
### HAVING

`HAVING` ကတော့ အရှေ့အပိုင်းတွေမှာဖော်ပြခဲ့တဲ့ `WHERE` နဲ့အတူတူပါပဲ။ Aggregation functions တွေမှာ `WHERE` ကိုအသုံးပြုလို့မရနိုင်တဲ့အတွက် `HAVING` ကိုသုံးခြင်းဖြစ်ပါတယ်။ အပေါ်က query ကိုပဲ `HAVING` နဲ့ filter ခံကြည့်ရအောင်။ `major` group ထဲကမှကျောင်းသားတစ်ယောက်အထက်ရှိတဲ့ `major` ကိုပဲလိုချင်တယ်ဆိုပါစို့။

```
SELECT major, COUNT(*) AS NumberOfStudents
FROM students
GROUP BY major
HAVING COUNT(*) > 1;
```

![ag8](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ag/ag8.png)

---

Aggregation functions တွေက real world မှာလည်းအသုံးဝင်တဲ့ functions တွေဖြစ်ပါတယ်။ သူ့ချည်းပဲဆိုမသိသာပေမယ့် `GROUP BY` တို့ `HAVING` တို့ခံပြီးသုံးမယ်ဆိုအရမ်း powerful ဖြစ်တဲ့အပြင် query ကများတဲ့အခါရေးရတာလဲ နည်းနည်း tricky ဖြစ်တတ်ပါတယ်။ အပေါ်ကကျနော့်နမူနာကို စုတုပြုပြီး မိမိဘာသာဆက်ပြီးလေ့ကျင့်ကြည့်ကြပါဦး။
