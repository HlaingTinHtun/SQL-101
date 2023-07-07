# Data Types in SQL

ဒီအပိုင်းမှာတော့ SQL မှာရှိတဲ့ data types တွေအကြောင်းကိုဆွေးနွေးသွားပြီးတော့ နောက်အပိုင်းကနေစပြီးတော့ environment setup (လိုအပ်တဲ့ software တွေသွင်း) လုပ်မယ်၊ လက်တွေ့ query တွေရေးပြီးတော့ ဆက်လက်လေ့လာသွားကြပါမယ်။

အရှေ့မှာ SQL ရဲ့ table, row, column တွေအကြောင်းကိုအဓိပ္ပါယ်ဖွင့်ဆိုခဲ့ပါတယ်။ Column တစ်ခုမှာ data သိမ်းတော့မယ်ဆို သိမ်းချင်တဲ့ data ရဲ့ပုံစံကိုပါထည့်သွင်းဖော်ပြပေးရပါတယ်။ ဥပမာမြင်သာအောင်ပြောရရင် programmers ဆိုတဲ့ programmer တွေရဲ့ data ကိုသိမ်းမယ့် table တစ်ခုရှိတယ်ဆိုပါစို့။ name, email, gender, age ဆိုတဲ့ column လေးခုသိမ်းဆည်းကြပါမယ်။

* name ကို စာသား
* email ကိုလည်းစာသား
* gender ကိုလည်းစာသားသိမ်းမယ်၊ Male, Female
  * ဒါမှမဟုတ် ကိန်းကဏန်းအနေနဲ့ 1,2 နဲ့သိမ်းလည်းရတာပဲ၊ 1 က male, 2 က female
* age ကိုတော့ ကိန်းကဏန်းအနေနဲ့သိမ်းမယ်။ 20, 30 စသည်ဖြင့်ပေါ့။

ဘာလို့ဒီလိုတွေခွဲပြီးသိမ်းနေရတာလဲ၊ တစ်မျိုးတည်းသတ်မှတ်ပြီးသိမ်းလည်းရတာပဲမဟုတ်လားလို့မေးစရာရှိပါတယ်။ ဘာကြောင့် data types တွေခွဲသိမ်းဖို့လိုတယ်၊ အရေးကြီးတယ်ဆိုတာကို ဒီ article conclude လုပ်တဲ့အချိန်မှာ ထည့်ရေးပေးသွားပါမယ်။

လောလောဆယ်ဘယ်လိုမျိုး data types တွေရှိတယ်ဆိုတာကြည့်ရအောင်။ ဒီ article မှာတော့ common data types အသုံးများတဲ့ data types တွေအကြောင်းကိုထည့်ပေးသွားပါမယ်။ data types တွေကအများကြီးရှိတဲ့အပြင် အရှေ့မှာပြောခဲ့တဲ့ DBMS software တွေပေါ်မူတည်ပြီးတော့လည်းအမျိုးမျိုးကွဲပြားနိုင်သေးတယ်။ သို့သော် အခုရေးထားတဲ့ data types တွေနားလည်ထားမယ်ဆို စတင်လေ့လာတဲ့သူတစ်ယောက်အနေနဲ့ လုံလောက်မယ်လို့ယူဆပါတယ်။

* Numeric data type - ကိန်းကဏန်းတွေသိမ်းဆည်းရန်
* Character data type - စာသားတွေသိမ်းဆည်းရန်
* Date & Time data type - နေ့ရက်နှင့်အချိန်ကာလတွေသိမ်းဆည်းရန်

တစ်ခုခြင်းဆီကိုအသေးစိတ်ပြန်ကြည့်ရရင်

## Numeric Data Types

* TINYINT – 1-byte size ကိန်းကဏန်းတွေသိမ်းဆည်းရန်
* SMALLINT – 2-byte size ကိန်းကဏန်းတွေသိမ်းဆည်းရန်
* INT – 4-byte size ကိန်းကဏန်းတွေသိမ်းဆည်းရန်
* BIGINT – 8-byte size ကိန်းကဏန်းတွေသိမ်းဆည်းရန်
* DECIMAL – precise ဖြစ်တဲ့၊တိကျသေချာတဲ့ ဒဿမကိန်းကဏန်းတွေသိမ်းဆည်းရန်
* FLOAT – approximate ဖြစ်တဲ့၊ မှန်းခြေ ဒဿမကိန်းကဏန်းတွေသိမ်းဆည်းရန်
* DOUBLE – FLOAT ထက်ပို precise ဖြစ်၊ range များများလိုတဲ့အချိန်မှာ DOUBLE ကိုသုံးပါတယ်။
* BOOLEAN – TRUE/FALSE တန်ဖိုးနှစ်ခုထဲသာရှိတဲ့ Logical value သိမ်းဆည်းရန်

## Character Data Types

* CHAR – fixed-length ဖြစ်တဲ့စာသားတွေသိမ်းဆည်းရန်။
* VARCHAR – maximum length ကို define လုပ်ပြီးသိမ်းဆည်းနိုင်ပါတယ်။
* TEXT – သိမ်းဆည်းရမယ့် စာသားကိုများတယ်ဆို TEXT ကိုအသုံးပြုနိုင်ပါတယ်။ MEDIUMTEXT, LONGTEXT အစရှိတာတွေကိုအသုံးပြုနိုင်ပါတယ်။

## Date & Time Data Types

* Date – YYYY-MM-DD format နဲ့ Year, Month, Date တန်ဖိုးတွေသိမ်းဆည်းရန်
* Time – HH:MM:SS format နဲ့ နာရီ၊မိနစ်၊ စက္ကန့် တန်ဖိုးတွေသိမ်းဆည်းရန်
* DATETIME/TIMESTAMP – Date နဲ့ Time ကိုပေါင်းစည်းပြီးသိမ်းဖို့လိုတဲ့အချိန်တွေအသုံးပြုရန်

အခုအပေါ်မှာပြောခဲ့တာတွေကတော့ အသုံးပြုတာများတဲ့ data types တွေပဲဖြစ်ပါတယ်။ storage size တွေကိုတော့ ကျနော်လည်းအလွတ်မရပါဘူး၊ လိုအပ်တဲ့အချိန်မှသာသက်ဆိုင်ရာ documentation ကိုပြေးကြည့်လိုက်တာပဲ။ W3Schools မှာတော့ data types တွေကိုဒီလိုပိုမိုတိတိကျကျဖော်ပြထားပါတယ်။ Reference အနေနဲ့ထည့်သွင်းဖော်ပြပေးလိုက်ပါတယ်။ MySQL Data Types (Version 8.0) အတွက်ဖြစ်ပါတယ်။ (DBMS အလိုက်ပြောင်းလဲနိုင်တာကြောင့် အသုံးပြုတဲ့ DBMS နဲ့ version ကိုပူးတွဲဖော်ပြခြင်းဖြစ်ပါတယ်)

![Numeric DataTypes](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/numeric\_datatypes.png) ![String DataTypes](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/string\_datatypes.png) ![DateTime DataTypes](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/datetime\_datatypes.png)

[https://www.w3schools.com/sql/sql\_datatypes.asp](https://www.w3schools.com/sql/sql\_datatypes.asp)

ဒီ URL ကနေတစ်ဆင့်လည်းသွားရောက်ဖတ်ရှုနိုင်ပါတယ်။

## Why Data Types?

ဘာလို့ data types တွေကအရေးကြီးတာလဲဆိုတော့

### Data Integrity

Product description သိမ်းဆည်းရမယ့်နေရာမှာ TEXT လိုမျိုး data type သုံးခြင်းအားဖြင့် description text data တွေပြတ်တောက်ခြင်းမရှိဘဲခိုင်မာမှုကောင်းကောင်းနဲ့သိမ်းဆည်းနိုင်ပါတယ်။ ဥပမာ Varchar ကို size 20 လောက်သတ်မှတ်ပြီးသိမ်းလိုက်မယ်ဆို data ဖြတ်ချခံရနိုင်တဲ့ဖြစ်နိုင်ချေရှိပါတယ်။

### Storage Optimization

Data ကိုလိုသလောက်ပဲ data type တွေခွဲခြားသတ်မှတ်ပေးခြင်းအားဖြင့် data storage ပမာဏကိုလျော့ချနိုင်ပါတယ်။ ဥပမာ ဒီ row ကဖျက်ထားလားဆိုတဲ့ is\_deleted ဆိုတဲ့ column လိုမျိုးကို BOOLEAN လို value ကိုသုံးသင့်ပါတယ်။ INT တို့ MEDIUMINT တို့သုံးလိုက်မယ်ဆို မလိုအပ်ဘဲ storage ပမာဏပိုပေးရပါတယ်။

### Query Optimization

Data တွေကို filter, sort လုပ်ဖို့အတွက် data type တွေခွဲထားမှသာအဆင်ပြေပါမယ်။ ဥပမာ monthly data ဆွဲမယ်ဆို column ကို DATE data type နဲ့သိမ်းထားမှသာ query ကိုကောင်းမွန်စွာ ဆွဲနိုင်မှာဖြစ်ပါတယ်။

### Calculation

အတွက်အချက်နဲ့ပတ်သတ်တဲ့ query တွေ run ဖို့လိုအပ်လာချိန်မှာလည်း သင့်တော်တဲ့ data type တွေခွဲထားမှသာ calculation ကောင်းကောင်းလုပ်နိုင်မှာဖြစ်ပါတယ်။ ဥပမာ INT သိမ်းရမယ့် column လိုနေရာမျိုးမှာ TEXT နဲ့သိမ်းထားမယ်ဆို calculation လုပ်တဲ့နေရာမှာအခက်အခဲတွေရှိနိုင်ပါတယ်။
