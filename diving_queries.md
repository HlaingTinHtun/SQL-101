# Diving Into SQL Queries

Diving လုပ်တယ်လို့ဆိုထားပေမယ့် ဒီအပိုင်းမှာတော့ Query ဆိုတာဘယ်လိုသဘောရှိလဲဆိုတာကို သဘောပေါက်ရုံလောက်ပဲ intro အရင်ဝင်ပြီးတော့ဖြည်းဖြည်းခြင်း step up လုပ်ပြီးလေ့လာသွားကြပါမယ်။ 

Query တွေရေးတဲ့အချိန်မှာ CLI (command line interface) ကိုအသုံးပြုသွားပါမယ်။ CLI နဲ့ရင်းနှီးစေချင်တာကတစ်ကြောင်း၊ CLI မကျွမ်းကျင်သေးဘဲနဲ့ GUI (graphical user interface) ကိုတန်းမသုံးစေချင်တာကြောင့်လည်းပါပါတယ်။

စလိုက်ကြရအောင်၊ ကျနော်ကတော့ window OS ကိုအသုံးပြုနေပါတယ်။ တစ်ခြား OS အသုံးပြုနေတဲ့သူတွေကလည်းသက်ဆိုင်ရာ application ကိုဖွင့်ပြီးလိုက်လုပ်ကြည့်နိုင်ပါတယ်။ နားမလည်ရင် environment setup အပိုင်းကိုပြန်ဖတ်ကြည့်ပေးပါခင်ဗျ။

MySQL 8.0 command line client ကို window start menu ကနေတစ်ဆင့်ဖွင့်လိုက်ပါမယ်။ password ရိုက်ထည့်ပြီးရင်အသုံးပြုနိုင်ပါပြီ။

![Opening CLI](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds1.png) 

Query တွေစမ်းရေးကြည့်နိုင်ဖို့အတွက် Database တစ်လုံးအရင်ဆောက်ကြည့်ရအောင်။
Database ဆောက်ဖို့အတွက် schema ပါ။
#### Schema
`CREATE DATABASE database_name;`

`database_name` မှာကျနော်တို့ဆောက်မည့် နာမည်ကိုအစားထိုးလိုက်ပါမယ်။
ဒီတစ်ခေါက်စားသောက်ဆိုင်ဆိုတဲ့ restaurant db ကိုဆောက်ပါမယ်။
#### Query
`CREATE DATABASE restaurant;`

`show databases` ကိုသုံးပြီးပြန်စစ်ကြည့်မယ်ဆို restaurant db ကိုတွေ့ရပါမယ်။

![Creating database](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds2.png) 

ဆောက်ထားတဲ့ restaurant db ကိုအသုံးပြုရန်
`use restaurant` ဆိုပြီးရိုက်လိုက်ပါမယ်။

![Using database](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds3.png) 

ဆိုင်မှာရနိုင်တဲ့ဟင်းပွဲတွေကိုသိမ်းဖို့အတွက် menu ဆိုတဲ့ table ဆောက်ပါမယ်။

#### Schema

```
CREATE TABLE table_name (
    column_name1 data_type1 constraints,
    column_name2 data_type2 constraints,
    ...
);
```
table_name နေရာမှာ table နာမည်
column_name နေရာမှာထည့်ချင်တဲ့ column နာမည်
data_type နေရာမှာသိမ်းဆည်းချင်တဲ့ပုံစံ
constraints မှာလိုတဲ့ပမာဏကိုထည့်ပြီး table ဆောက်ပါမယ်။

#### Query
```
CREATE TABLE menu (name VARCHAR(100), price INTEGER(10), category VARCHAR(50), created_date DATE, updated_date DATE );
```
`show tables` နဲ့ပြန်စစ်ကြည့်မယ်ဆို ဒီလိုမြင်ရပါလိမ့်မယ်။

![Creating table](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds4.png) 

Table structure ကိုပါကြည့်ချင်တယ်ဆို 
`DESCRIBE` ဆိုတဲ့ keyword ကိုအသုံးပြုနိုင်ပါတယ်။

![Checking table structure](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds5.png) 

Table ဆောက်ပြီးပြီဆိုတော့ data နည်းနည်းထည့်ကြည့်ရအောင်။
#### Schema
```
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...),
       (value1, value2, ...),
       ...;
```
column နေရာမှာ column name တွေအစားထိုးပြီး value နေရာမှာထည့်ချင်တဲ့တန်ဖိုးတွေကိုအစားထိုးလိုက်ပါမယ်။
#### Query
```
INSERT INTO menu (name, price, category, created_date, updated_date) VALUES ('Dish A', 10000, 'Main Course', '2023-07-28', '2023-07-28'), ('Dish B', 6000, 'Appetizer', '2023-07-28', '2023-07-28'), ('Dish C', 5000, 'Dessert', '2023-07-28', '2023-07-28');
```
![Inserting data](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds6.png) 

Data တွေကိုပြန်စစ်ကြည့်ရအောင်။

`select * from menu`

![Selecting data](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds7.png) 
menu table ထဲမှာရှိတဲ့ data အားလုံးကိုပြပါလို့ဆိုလိုတာဖြစ်ပါတယ်။ SELECT နဲ့ FROM keyword ကိုအသုံးပြုပါတယ်။ 
`*` ကတော့အားလုံးကိုဆိုလိုခြင်းဖြစ်ပါတယ်။

အားလုံးကိုမဆွဲထုတ်ချင်ဘူး၊ column တစ်ခုတည်းဆွဲချင်တယ်ဆိုလည်းရပါတယ်။
`*` နေရာမှာ column name ကိုအစားထိုးလိုက်ရုံပါပဲ။

#### Query
`select name from menu;`

![Selecting a column](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds8.png) 

တစ်ခုထက်ပိုတဲ့ column ကိုဆွဲချင်တယ်ဆိုရင်လည်း comma ခံပြီးဆွဲထုတ်လို့ရပါတယ်။
#### Query
`select name,price from menu;`

![Selecting multiple columns](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds9.png)

ရိုးရိုး SELECT ကိုသုံးပြီး data ထုတ်ရာကနေ condition လေးတွေခံပြီးထုတ်ကြည့်ရအောင်။ `menu` table ထဲကမှ `category` က `Main Course` ဖြစ်တဲ့ item ကိုပဲလိုချင်တယ်ဆိုပါစို့။
`WHERE` ဆိုတဲ့ keyword ကိုသုံးပြီးဒီလိုဆွဲထုတ်လို့ရပါတယ်။
#### Schema
```
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

condition နေရာမှာ category က Main Course ပါဆိုတဲ့ category = 'Main Course' ကကိုအစားထိုးပေးလိုက်ပါမယ်ဆို Main Course 
ဖြစ်တဲ့ record တစ်ကြောင်းပဲထွက်လာတာကိုမြင်ရပါမယ်။
#### Query
```
SELECT * FROM menu WHERE category = 'Main Course';
```
![Select where](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds10.png) 

သတိထားမိလားမသိဘူး၊ ကျနော် sql keywords တွေကို စာလုံးအသေးနဲ့ရောအကြီးနဲ့ရောသုံးသွားတယ်၊ နှစ်ခုလုံးအလုပ်လုပ်ပါတယ်။
သို့သော်ဖတ်ရလွယ်ကူရန်နဲ့ sql keywords တွေမှန်းသိသာအောင် capital letter ကိုသုံးတာကပိုပြီးသင့်တော်စေပါတယ်။

`menu` table ထဲကဈေး 10000 ထက်နည်းတဲ့ items တွေကိုဆွဲထုတ်ကြည့်ရအောင်။ `<`  less than character ကိုအသုံးပြုပါမယ်။
#### Query
```
SELECT * FROM menu WHERE price < 10000;
```
10000 ထက်နည်းတဲ့ items နှစ်ခုကိုတွေ့ရပါမယ်။

![Select where](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds11.png) 

လောလောဆယ်တော့ဒီလောက်ထိပဲသွားထားပါမယ်။ နောက်ပိုင်း queries တွေဆက်ရေးကြပါဦးမယ်။
table ကို delete ပြန်ချကြည့်ရအောင်။
#### Schema
```
DROP TABLE table_name;
```
#### Query
table_name မှာ `menu` ကိုအစားထိုးလိုက်ပါမယ်။
```
DROP TABLE menu;
```
![Deleting table](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ds12.png) 


Queries အကြောင်းနည်းနည်းတီးမိခေါက်မိရှိသွားပြီဆိုတော့ DDL, DQL, DML ဒီသုံးခုအကြောင်းကိုဆက်ရှင်းပေးသွားပါမယ်။
SQL queries ကိုအဓိကအားဖြင့်သုံးမျိုးခွဲခြားနိုင်ပါတယ်။

### Data Definition Language (DDL):
DDL ကတော့ database structure တွေကိုစီမံဖို့အတွက်အသုံးပြုတဲ့ query တွေကိုဆိုလိုခြင်းဖြစ်ပါတယ်။
data တွေကိုစီမံတာမဟုတ်ဘဲ database objects တွေကိုကိုင်တွယ်နိုင်ဖို့အတွက်အသုံးပြုတာဖြစ်ပါတယ်။

### Data Query Language (DQL):
DQL ကတော့ database ထဲက data တွေကိုဆွဲထုတ်ဖို့အတွက်အသုံးပြုတဲ့ query တွေကိုဆိုလိုခြင်းဖြစ်ပါတယ်။
များသောအားဖြင့် SELECT statements တွေဖြစ်ပါတယ်။

### Data Manipulation Language (DML):
DML ကတော့ database ထဲက data တွေကိုသိမ်းဆည်း၊ပြုပြင်၊ဖျက်ဆည်းခြင်း INSERT, UPDATE, DELETE လုပ်ဖို့အတွက်အသုံးပြုတဲ့ query တွေကိုဆိုလိုခြင်းဖြစ်ပါတယ်။

နောက်အပိုင်းတွေကစပြီး ဒီ categories သုံးခုကိုကျောရိုးထားပြီးတော့ query တွေလက်တွေ့ရေးသားပြီးလေ့လာသွားကြပါမယ်။
