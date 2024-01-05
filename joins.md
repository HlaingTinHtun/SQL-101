## SQL Joins

Relationship အပိုင်းမှာ table တွေကိုချိတ်ဆက်ပြီး data တွေယူတယ်လို့ပြောခဲ့ပါတယ်။ ဒီလိုချိတ်ဆက်ဖို့အတွက် `JOIN` ဆိုတဲ့ keyword ကိုသုံးပြီး query တွေရေးပါတယ်။ အခုအပိုင်းမှာတော့ အသုံးများတဲ့ JOIN အမျိုးအစားတွေကိုရှင်းပြရင်း JOIN အသုံးပြုနည်းကိုပါ query တွေ run ကြည့်သွားရင်းလေ့လာသွားကြပါမယ်။

ဒါကတော့ JOIN query ရဲ့ schema ပဲဖြစ်ပါတယ်။
```
SELECT column1, column2, ...
FROM table1
INNER JOIN table2 ON table1.column_name = table2.column_name;
```

`ON table1.column_name = table2.column_name` ဆိုတာကတော့ table နှစ်လုံးရဲ့ `primary key`, `foreign key` ကိုချိတ်ဆက်မယ့် condition တစ်ခုကိုဖော်ပြတဲ့သဘောဖြစ်ပါတယ်။

`INNER JOIN` ဆိုတာကတော့အဲ့ဒီ `condition` အပေါ်မှာ match ဖြစ်တဲ့ records သီးသန့်ကိုပဲလိုချင်တယ်လို့ဆိုတာပါ။ `INNER JOIN` က JOIN အမျိုးအစားတစ်ခုပဲဖြစ်ပါတယ်။ 

အောက်မှာတစ်ခြားသော `JOIN` တွေကိုဆက်ကြည့်ရင်း JOIN queries တွေကိုပိုသဘောပေါက်အောင်ကြိုးစားကြည့်ပါမယ်။

Join query တွေမရေးခင်မှာ tables တွေနဲ့ data တွေပြင်ဆင်ထားပါမယ်။

ရှိပြီးသား `students`table နဲ့ `student_details` ဆိုတဲ့ table နှစ်ခုကိုသုံးပြီးတော့ JOIN queries တွေစမ်းရေးသွားပါမယ်။

`student_details` table ဆောက်ပါမယ်၊ ရှိပြီးသားသူတွေကတော့ဆောက်စရာမလိုပါဘူး။
```
CREATE TABLE student_details (
    student_id INT PRIMARY KEY,
    address VARCHAR(100),
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);
```

တစ်ခါတည်း student_id ကို `students` table ရဲ့ foreign key အဖြစ်သတ်မှတ်ထားလိုက်ပါတယ်။

`student_details`table ထဲကို data ထည့်ပါမယ်။
```
INSERT INTO student_details (student_id, address) VALUES
(1, 'Yangon, Myanmar'),
(2, 'Mandalay, Myanmar'),
(3, 'Naypyidaw, Myanmar'),
(4, 'Bago, Myanmar'),
(5, 'Magway, Myanmar');
```
![join](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/join/j1.png)

### Inner Join
Inner Join ဆိုတာကတော့ table နှစ်လုံးထဲကမှ သတ်မှတ်လိုက်တဲ့ **condition** ပေါ်မူတည်ပြီး `match` ဖြစ်တဲ့ records တွေကိုသာ join ဖြစ်စေပါတယ်။ **condition** က match မဖြစ်ဘူးဆိုရင် records မထွက်တဲ့အခါမျိုးလည်းရှိတတ်ပါတယ်။

![join](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/join/j2.1.png)
*Image Credit : W3Schools*

ဥပမာ `students`table နဲ့ `student_details` table ကို **JOIN** ပြီးတော့ data တွေကိုဆွဲထုတ်ပါမယ်။ သို့ပေမယ့် table နှစ်ခုလုံးမှာ **match** ဖြစ်တဲ့ results ကိုသာယူမယ်ဆိုရင်အောက်ကလိုမျိုးရေးနိုင်ပါတယ်။
```
SELECT students.student_id, students.name, student_details.address FROM students INNER JOIN student_details ON students.student_id = student_details.student_id;
```

`student_details` မှာက `student_id` 1 to 5 အထိသာရှိတဲ့အတွက် table နှစ်ခုလုံးမှာ match ဖြစ်တဲ့ condition ဟာ student_id 1 to 5 ဖြစ်တဲ့ records ငါးကြောင်းသာဖြစ်ပါတယ်။ `students`table မှာရှိတဲ့ `student_id` 6,7,8 ဟာ `student_details` ထဲမှာမရှိတဲ့အတွက်ပါလာမှာမဟုတ်ပါဘူး။

![join](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/join/j2.png)

### Left Join

Left Join ကတော့ဘယ်ဘက်ခြမ်းက records အားလုံးနဲ့ ညာဘက်ခြမ်းက **match** ဖြစ်တဲ့ records တွေကိုဆွဲပေးပါတယ်၊ သို့ပေမယ့်ဘယ်ဘက်ခြမ်းက records တွေကအားလုံးပါတာဖြစ်တဲ့အတွက်ညာဘက်ခြမ်းက **match** မဖြစ်တဲ့ records တွေရဲ့ column တန်ဖိုးနေရာမှာတော့ `NULL` values တွေပါလာမှာဖြစ်ပါတယ်။

![join](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/join/j3.1.png)
*Image Credit : W3Schools*

```
SELECT students.student_id, students.name, student_details.address FROM students LEFT JOIN student_details ON students.student_id = student_details.student_id;
```

ဒီ query မှာဆို LEFT JOIN သုံးထားပြီးတော့  `Left` side table က `stuents` ဖြစ်မယ်။ `Right` side table က `student_details` ဖြစ်မယ်။ `student_details` table မှာမရှိတဲ့ `students` table က records တွေက `address` column မှာ NULL value တွေဖြစ်နေမှာဖြစ်ပါတယ်။ အောက်ကပုံနဲ့တွဲကြည့်ရင်ပိုနားလည်ပါလိမ့်မယ်။

![join](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/join/j3.png)

### Right Join

Right join ကတော့ Left join နဲ့သဘောတရားချင်းတူတူပါပဲကိုမှ `right` table က records ကအကုန်ပါမယ်၊ `left` ဘက်က **match** မဖြစ်တဲ့ records တွေကတော့ `students`table က column တွေနေရာမှာ NULL value တွေဖြစ်သွားပါမယ်။

![join](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/join/j4.1.png)
*Image Credit : W3Schools*

```
SELECT students.student_id, students.name, student_details.address FROM students RIGHT JOIN student_details ON students.student_id = student_details.student_id;
```
Result ပုံနဲ့တွဲကြည့်ရင်ပိုနားလည်သွားပါမယ်။ လက်ရှိ table ထဲမှာတော့ right table `student_details` ထဲက records တွေအားလုံး left table `students` မှာ match records ရှိနေတဲ့အတွက် NULL values မတွေ့နိုင်ပါဘူး။ `student_details` ထဲမှာ `students` table ထဲမှာမရှိတဲ့ `student_id` တစ်ခုခုနဲ့ records ဖန်တီးပြီးပြန် run ကြည့်လိုက်မယ်ဆိုမတူတဲ့ result တစ်မျိုးရပါလိမ့်မယ်၊ စမ်းပြီးလုပ်ကြည့်ပါ။

![join](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/join/j4.png)

### Full Join

Full join ကတော့အရှင်းဆုံးပြောရရင် Left join နဲ့ Right Join ကိုပေါင်းထားတဲ့သဘောပါပဲ။ အပြန်အလှန် **match** မဖြစ်တဲ့ records တွေမှာတော့ NULL values တွေဝင်သွားပါမယ်။ 

![join](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/join/j5.1.png)
*Image Credit : W3Schools*

ကျနော်တို့အခုသုံးနေတဲ့ MySQL DBMS မှာ `FULL JOIN` ဆိုတဲ့ keyword မရှိပါဘူး။ အဲ့အတွက်ကြောင့် `UNION` ဆိုတဲ့ keyword သုံးပြီးတော့ left နဲ့ right ကိုပေါင်းလိုက်ပါတယ်။ အောက်ကနမူနာ query ကို run ကြည့်နိုင်ပါတယ်။
```
SELECT students.student_id, students.name, student_details.address
FROM students
LEFT JOIN student_details ON students.student_id = student_details.student_id

UNION

SELECT students.student_id, students.name, student_details.address
FROM students
RIGHT JOIN student_details ON students.student_id = student_details.student_id
WHERE students.student_id IS NULL;
--- WHERE case ကမထည့်လည်းရပါတယ်။ ကျနော်ရေးတာပိုသွားတာပါ။
```
![join](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/join/j5.png)



Full Join တွေက records တွေကိုဘယ်ညာအကုန်ပြန်ထုတ်ပေးတဲ့အတွက်ပုံမှန်ထက်ပိုပြီးနှေးပါတယ်၊ data တွေမြောက်မြားစွာသိမ်းထားတဲ့ table တွေကို `full join` လုပ်တော့မယ်ဆို **efficiency** သိသိသာသာကျစေတဲ့အတွက် ဒီတစ်ချက်ကိုတော့သတိပြုထားသင့်ပါတယ်။

Recap လုပ်ရမယ်ဆို 
Inner join ဆိုတာ match ဖြစ်တဲ့ records သီးသန့်။
Left join ဆိုတာ left ကအကုန်၊ right က match records သီးသန့်။
Right join ဆိုတာ right ကအကုန်၊ left က match records သီးသန့်။
Full join ဆိုတာ filter မရှိဘဲ ဘယ်ညာအကုန်။ 

များသောအားဖြင့် development လုပ်ပြီဆို database ထဲမှာ table relations တွေများစွာပါတတ်ပါတယ်။ Join တွေကိုနားလည်ထားမှသာမိမိလိုသလို table တွေကိုချိတ်ဆက်ပြီး data တွေကို efficiency ကောင်းကောင်းနဲ့ထုတ်သွားနိုင်မှာဖြစ်ပါတယ်။ ဒီအပိုင်းမှာ section တစ်ခုစီကို query တစ်ကြောင်းပဲရေးပြထားပါတယ်၊ ရှုပ်သွားမှာစိုးလို့ပါ။ နောက်အပိုင်းမှာ relationship type တွေအကြောင်းထပ်ရှင်းပြရင်း join queries တွေဆက်လေ့လာသွားကြပါမယ်။

