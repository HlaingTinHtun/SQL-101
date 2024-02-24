## Indexing
အရင်ဆုံး Indexing ဆိုတာဘာအတွက်လိုတာလဲနဲ့ဘယ်လိုအလုပ်လုပ်တယ်ဆိုတာကို theory introduction လုပ်ပေးပါရစေ။ ပြီးရင်လက်တွေ့ query run ကြည့်ပြီးကွဲပြားချက်ကိုဆန်းစစ်ကြည့်ပါမယ်။

SELECT * FROM users WHERE name = ‘John’

Database ထဲမှာ ဒီလို query တစ်ကြောင်း run လိုက်တဲ့အချိန်မှာ users table ထဲက name column မှာ John ဆိုတဲ့ value ရှိတဲ့ records တွေပြန်ပေးပါတယ်။ ဒီလိုပြန်ပေးဖို့အတွက် users table ထဲမှာရှိတဲ့ row အားလုံးကို query ကလိုက်ကြည့်ရပါတယ်၊ ဒါကို Full table scan, table တစ်ခုလုံးကိုလိုက်ရှာရတယ်လို့လည်းဆိုပါတယ်။ 

Index ဆိုတာကတော့ Full table scan, table တစ်ခုလုံးကို scan/lookup လုပ်စရာမလိုတော့ဘဲနဲ့ လိုအပ်တဲ့ scan operation ကိုသာလုပ်ပြီး လိုချင်တဲ့ results တွေကိုရအောင် လုပ်ပေးနိုင်တဲ့ data structure တစ်ခုဖြစ်ပါတယ်။ တစ်နည်းအားဖြင့် query efficiency (read) ကိုမြှင့်ပေးနိုင်တဲ့ အရာတစ်ခုလို့ဆိုနိုင်ပါတယ်။ 

ပုံမှန်အားဖြင့် data တွေသိမ်းထားတဲ့ table တွေက order စီထားခြင်းမရှိပါဘူး၊ ဒီအတွက်ကြောင့်လည်း condition တစ်ခုကို lookup လုပ်တဲ့အချိန်မှာ table ထဲမှာရှိတဲ့ record အားလုံးကိုဖတ်ရတယ်၊ Linear lookup ပုံစံမျိုးအလုပ်လုပ်ရပါတယ်။ data ပမာဏနည်းသေးတဲ့အချိန်မှာ အဆင်ပြေနေသေးမယ့် data ပမာဏများလာတဲ့အချိန်မှာတော့ query execution time ကပိုပြီးကြာလာနိုင်ပါတယ်၊ ဒါမှမဟုတ် table တစ်ခုနဲ့တစ်ခု Join ပြီး lookup လုပ်တဲ့အချိန်တွေမှာလည်း နှစ်ဆလောက်ပိုပြီးကြာသွားနိုင်ပါတယ်။

အလွယ်ကူဆုံးဥပမာတစ်ခုပေးရရင် အကယ်လို့သိမ်းထားတဲ့ data တွေသာ order အစီအစဉ်တကျစီထားနိုင်မယ်ဆို အပေါ်က John ဆိုတဲ့ value ကိုရှာတဲ့အချိန်မှာ ပုံမှန်အတိုင်း full table scan လုပ်ရပေမယ့် first alphabet က J ကိုကျော်သွားတဲ့အချိန်မှာ scan ထပ်ပြီးလုပ်စရာမလိုတော့တဲ့အတွက် scan လုပ်ရမယ့် operation ကို ပမာဏတစ်ခုအထိ လျော့ချနိုင်သွားမှာဖြစ်ပါတယ် (This’s just a metaphor)။

ဒါပေမယ့်တစ်ကယ်တမ်းမှာတော့ table တွေက order စီထားခြင်းမရှိဘူး၊ ကျနော်တို့ရှာချင်တဲ့ query condition တွေကလည်း dynamic ဖြစ်တဲ့အတွက် scan operation မလုပ်ခင်မှာ table column တွေကိုလည်းအဲ့အတိုင်းလိုက်ပြောင်းပြီး order လိုက်စီပေးဖို့မလွယ်ကူပါဘူး။ ဒီနေရာမှာ index ဆိုတဲ့အရာကို သုံးနိုင်ပါတယ်။ Index က ဘာလုပ်ပေးလဲဆိုတော့ data structure တစ်ခုဖန်တီးပေးလိုက်ပါတယ်၊ များသောအားဖြင့် Binary Tree structure (တစ်ခြားသော structure တွေလည်းဖြစ်နိုင်ပါတယ်)။ B-Tree အကြောင်းမသိဘူးဆိုရင် အရင်ရှာဖတ်ကြည့်ဖို့တိုက်တွန်းပါတယ်။ အဓိကရည်ရွယ်ချက်ကတော့ sorting/order လုပ်ထားတဲ့ structure တစ်ခုရလာဖို့ရယ်၊ searching/scanning quality ကိုလည်းအများကြီးကောင်းမွန်သွားစေမှာဖြစ်ပါတယ်။

Index တစ်ခု create လုပ်ပြီဆိုရင်ဘယ် column ကို index ထားမလဲဆိုတာ ပြောပေးရပါတယ်။ ဥပမာကိုယ်က name ဆိုတဲ့ column ကိုပဲ index လုပ်မယ်ဆိုရင် table ထဲမှာရှိတဲ့ name မဟုတ်တဲ့တစ်ခြားသော column တွေကတော့ index ဖြစ်မှာမဟုတ်ပါဘူး။ name ဆိုတဲ့ column အတွက်ပဲ index ဖန်တီးပေးသွားမှာဖြစ်ပါတယ်။

Index ဘယ်လိုဖန်တီးသွားလဲဆိုတော့ index လုပ်ချင်တဲ့ column ကို key အဖြစ်နဲ့ value နေရာမှာ table ထဲမှာရှိတဲ့ record ကိုဆီကိုသွားနိုင်မယ့် reference pointer တစ်ခုသိမ်းထားလိုက်ပါတယ်။ ဆိုတော့ Index structure ထဲမှာ key က index လုပ်ထားတဲ့ column, value နေရာမှာ record reference pointer. Structure ကလည်း sorting စီထားပြီးသားဖြစ်မယ်။ query condition တစ်ခု run လိုက်ပြီဆို table ကိုသွားပြီး full scan မလုပ်တော့ဘဲ ခုနက index structure ထဲမှာပဲ သုံးထားတဲ့ structure အတိုင်း lookup လုပ်မယ် (လက်ရှိမှာတော့ B-tree) ၊ key ရလာပြီဆို reference pointer ကနေမှတစ်ဆင့် တစ်ကယ့် record ကိုသွားပြီးယူလိုက်ရုံပဲ၊ ဒါကြောင့်မို့လို့ lookup လုပ်တဲ့နေရာမှာ linear scanning မဟုတ်တော့ဘဲနဲ့ သုံးထားတဲ့ structure အတိုင်း efficiency ကောင်းကောင်းနဲ့ lookup လုပ်သွားနိုင်မှာဖြစ်ပါတယ်။

ဒါပေမယ့်ကိုယ့်ဘက်ကပေးရမယ့် cost ကလည်းရှိတယ်။ Index တွေအတွက် space ပြန်ပေးရတယ်၊ key , value ပုံစံနဲ့ sorted structure တစ်ခုဖန်တီးရတာကိုး။ နောက်တစ်ခုက lookup/read operation တွေမှာ efficiency ကောင်းပေမယ့် row အသစ်တစ်ခု insert လုပ်တဲ့ operation မှာ index ထောက်ထားတဲ့အတွက် index ပါဖန်တီးပေးဖို့လိုတဲ့အတွက်ကြောင့် ပုံမှန်ထက်တော့ ပိုနှေးသွားမှာဖြစ်ပါတယ်။ update, delete တွေမှာလည်းသဘောတရားကအတူတူပါပဲ။ ဒီလိုပဲ တစ်ခုလိုချင် တစ်ခုပြန်ပေးရတဲ့ trade-off သဘောတရားကတော့ အမြဲရှိတတ်ပါတယ်။

Theory ကတော့ဒီလောက်ဆိုလုံလောက်ပြီလို့ထင်ပါတယ်၊ လက်တွေ့စမ်းပြီးလုပ်ကြည့်ပါမယ်။

`employees` ဆိုတဲ့ table တစ်လုံးဆောက်လိုက်ပါမယ်။ အဆင်ပြေတဲ့ database ကိုအသုံးပြုနိုင်ပါတယ်။

```
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    department_id INT
);
```
![index](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/index/index1.png) 

---
ပြီးရင် data row 100,000 ကို program ရေးပြီးထည့်လိုက်ပါမယ်။ လက်ရှိဒီ program ကိုနားလည်စရာမလိုသေးပါဘူး၊ data ထည့်ပြီး test လုပ်ကြည့်ဖို့အတွက်လောက်ပါပဲ။ ပါဝင်တဲ့ keyword တစ်ခုခြင်းဆီကို မိမိဘာသာ research လုပ်ကြည့်ပြီး program ကိုနားလည်အောင်ကြိုးစားကြည့်လို့လည်းရပါတယ်။

```
DELIMITER $$
CREATE PROCEDURE generate_sample_data()
BEGIN
    DECLARE i INT DEFAULT 1;
    WHILE i <= 100000 DO
        INSERT INTO employees (employee_id, name, department_id)
        VALUES (i, CONCAT('Employee', i), FLOOR(RAND() * 3) + 1);
        SET i = i + 1;
    END WHILE;
END $$
DELIMITER ;

CALL generate_sample_data();
```
 > Row 100,000 ဖြစ်တဲ့အတွက် program run တာပြီးအောင်အနည်းငယ်တော့စောင့်ရပါမယ်။

![index](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/index/index2.png) 

---

`select count(*)` နဲ့အောက်ပါအတိုင်း row count ကိုစစ်ကြည့်လို့ရပါတယ်။
![index](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/index/index3.png) 

---
အရင်ဆုံး query performance ကိုစစ်နိုင်ဖို့အတွက် profile ကို on ထားလိုက်ပါမယ်။ `SHOW PROFILES` နဲ့ပြန်စစ်ကြည့်မယ်ဆို run ခဲ့တဲ့ query list ရဲ့ Profiles တွေကိုတွေ့နိုင်ပါတယ်။

![index](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/index/index4.png) 

---

Index create မလုပ်ခင်မှာ query တစ်ကြောင်းအရင် run ကြည့်ပါမယ်။ ရိုးရိုးရှင်းရှင်း employees table ထဲက လိုချင်တဲ့ name ကိုလှမ်းဆွဲထုတ်ကြည့်ပါမယ်။

```
SELECT * FROM employees WHERE name = “Employee500”
```
ပြီးတာနဲ့ `SHOW PROFILES` နဲ့ပါတစ်ခါတည်းစစ်ကြည့်လိုက်မယ်ဆို QUERY ID, Duration တွေကိုတွေ့နိုင်ပါတယ်။

![index](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/index/index5.png) 

---
နောက်တစ်ဆင့်အနေနဲ့ `employees` table ထဲက name အပေါ်မှာ `index` တစ်ခုဖန်တီးသွားပါမယ်။ ပြီးရင် ခုနက run ခဲ့တဲ့ query ကို ပြန် run ကြည့်ပါမယ်။ index ကြောင့် query performance ကတက်လာသင့်ပါတယ်။

```
CREATE INDEX idx_employee_name ON employees(name);
```

![index](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/index/index6.png) 

---

ဒီ query ကိုပြန် run ကြည့်ပြီး `SHOW PROFILES` နဲ့စစ်ကြည့်ပါမယ်။
```
SELECT * FROM employees WHERE name = “Employee500”
```

![index](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/index/index7.png) 

---

Duration မှာ index တည်ဆောက်ခဲ့ပြီးမှ run ခဲ့တဲ့ query ကသိသိသာသာနည်းသွားတာကိုကြည့်ခြင်းအားဖြင့် query performance တက်လာကိုမြင်နိုင်ပါတယ်။

နိဂုံးချုပ်ရမယ်ဆို Indexing ဟာ query performance နဲ့ overall efficiency ကိုသိသာစွာမြှင့်တင်ပေးနိုင်ပါတယ်။ သို့ပေမယ့်အပေါ်မှာပြောပြခဲ့တဲ့အတိုင်း trade off တစ်ချို့ရှိပါတယ်။ over-indexing မဖြစ်အောင် မကြာခဏအသုံးပြုလေ့ရှိတဲ့ columns တွေကိုပဲ index ထည့်မယ်၊ ရေရှည်အားဖြင့် index တွေကို monitor & maintain လုပ်ခြင်းအားဖြင့်သင့်လျှော်စွာအသုံးပြုသင့်ကြောင်းကိုလည်းသတိချပ်ထားသင့်ပါတယ်။



