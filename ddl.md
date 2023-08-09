# Data Definition Language (DDL)

Data Definition လို့ဆိုတဲ့အတိုင်း DDL သည် database ရဲ့ structure တွေကိုသတ်မှတ်တည်ဆောက်ခြင်း၊ ပြောင်းလဲခြင်းတွေပြုလုပ်တဲ့ query တွေအတွက်သတ်မှတ်ထားတဲ့ category ဖြစ်ပါတယ်။ 
Database တစ်ခုတည်ဆောက်တဲ့နေရာမှာအရေးပါတဲ့ table, column data structure တွေကိုစီမံခန့်ခွဲခြင်း၊ data integrity ကောင်းရန်အတွက် အခြားသောလိုအပ်တဲ့ စည်းမျဉ်းများကို define လုပ်ရန်အတွက်အသုံးပြုပါတယ်။ 
data integrity ကိုအဓိပ္ပါယ်ရှိပြီးမှန်ကန်တဲ့ dataတွေလို့အကြမ်းဖျင်းသတ်မှတ်နိုင်ပါတယ်။ 

DDL ကိုဝါကျတစ်ကြောင်းတည်းနဲ့နားလည်အောင်ပြောရမယ်ဆို  Database တစ်ခုရုပ်လုံးပေါ်လာအောင် structure တွေသတ်မှတ်(define) လုပ်ပေးရတဲ့ query များဆိုပြီးပြောနိုင်မယ်ထင်တယ်။ 
ဒီအပိုင်းမှာတော့အရေးကြီးပြီးအသုံးများတဲ့ DDL queries တွေကိုလေ့လာသွားကြပါမယ်။

## CREATE DATABASE: Defining a New Database
စမ်းချင်တာတွေစမ်းဖို့အတွက် `ddl_test` ဆိုတဲ့ database တစ်လုံးအရင်တည်ဆောက်လိုက်ရအောင်။

```
CREATE DATABASE ddl_test;
```

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl1.png)

## CREATE TABLE: Defining a New Table
အရှေ့အပိုင်းမှာကျနော်တို့တွေ့ခဲ့ပြီးသားဖြစ်ပါတယ်။ database ထဲမှာ table တစ်လုံးတည်ဆောက်ရန်အတွက်အသုံးပြုပါတယ်။ လိုအပ်တဲ့ column နာမည်၊ structure တို့ကို define လုပ်ပြီးတည်ဆောက်နိုင်ပါတယ်။

#### Schema:
```
CREATE TABLE table_name (
    column_name data_type,
    ...,
    constraint_definition
);
```

Students ဆိုတဲ့ table တစ်လုံးတည်ဆောက်ရအောင်။

#### Query
```
CREATE TABLE students(
    student_id INT,
    name VARCHAR(50),
    age INT,
    remark VARCHAR (50)
 );
```

`SHOW TABLES;` နဲ့ပြန်ပြီးစစ်ကြည့်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl2.png)

## ALTER TABLE: Modifying Table Structure

ရှိပြီးသား table ရဲ့ structure ကိုပြောင်းလဲ `ALTER TABLE` ဆိုတဲ့ command ကိုအသုံးပြုပါတယ်။ 
table ထဲကို column အသစ်ထည့်တာ၊ ရှိပြီးသား column name ကိုပြောင်းတာ၊ column ကိုဖျက်တာစသည်ဖြင့်လုပ်ဆောင်နိုင်ပါတယ်။

### Adding a new column (column အသစ်ထည့်ခြင်း)

#### Schema
```
ALTER TABLE table_name
    ADD column_name data_type constraint_definition,
    ...;
```
#### Query
```
ALTER TABLE students
ADD nick_name VARCHAR(50);
````

`DESCRIBE` keyword ကိုသုံးပြီးပြန်စစ်ကြည့်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl3.png)

### Changing column name (column အမည်ပြောင်းခြင်း)

#### Schema
```
ALTER TABLE table_name
    RENAME COLUMN old_column_name TO new_column_name;
```

#### Query

```
ALTER TABLE students
RENAME COLUMN name TO formal_name;
```

`DESCRIBE` keyword ကိုသုံးပြီးပြန်စစ်ကြည့်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl4.png)

###Dropping a column (column ဖျက်ခြင်း)

#### Schema
```
ALTER TABLE table_name
    DROP COLUMN column_name;
```

#### Query
```
ALTER TABLE students
DROP COLUMN remarks;
```

`DESCRIBE` keyword ကိုသုံးပြီးပြန်စစ်ကြည့်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl5.png)

## DROP TABLE: Removing a Table (Table ဖျက်ခြင်း)

Table တစ်လုံးကိုဖျက်ချင်တဲ့အချိန်မှာတော့ DROP TABLE command ကိုအသုံးပြုနိုင်ပါတယ်။ table ထဲမှာသိမ်းဆည်းထားတဲ့ data တွေပါဖျက်တာဖြစ်တဲ့အတွက် ဂရုပြုဖို့လိုအပ်ပါတယ်။

#### Schema
```
DROP TABLE table_name;
```

#### Query
```
DROP TABLE students;
```

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl6.png)

## Constraints: Ensuring Data Integrity

Table column တွေသတ်မှတ်တဲ့အချိန် data integrity ရှိဖို့အတွက်အပြင် business logic အရ constraints ဆိုတာမျိုးတွေထည့်ပေးဖို့လိုအပ်တဲ့အချိန်တွေရှိပါတယ်။ 
constraints အကြောင်းကိုအောက်က query တွေကြည့်ပြီးဆက်လေ့လာသွားကြပါမယ်။

### PRIMARY KEY Constraint:

`PRIMARY KEY` ဆိုတဲ့ constraint ပေးလိုက်တဲ့ column ဟာ record တိုင်းမှာ unique (မထပ်စေရ) ဖြစ်ပြီးတော့ NULL မဖြစ်ရဘူးဆိုပြီး define လုပ်ခြင်းခံလိုက်ရပါတယ်။

Table ထဲမှာရှိတဲ့ column တစ်ခုကို primary key အဖြစ်သတ်မှတ်လိုက်မယ်ဆို အဲ့ဒီ column ဟာ record တိုင်းမှာ unique ဖြစ်သွားမယ် (duplicate value မရှိတော့ဘူးလို့ဆိုလိုခြင်း)၊ column value ကို null value အလွတ်ထည့်ပေးလို့မရတော့ပါဘူး။

#### Schema
```
CREATE TABLE table_name (
    column_name data_type PRIMARY KEY,
    ...,
    constraint_definition
);
```

students table ကိုအရင်ဖျက်ပါမယ်။
students table မှာ student_id ကို Primary key constraint ထည့်ပြီးတော့ဆောက်ကြည့်ပါမယ်။

#### Query
```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);
```
`DESCRIBE` keyword ကိုသုံးပြီးပြန်စစ်ကြည့်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl7.png)

### FOREIGN KEY Constraint:

DDL အကြောင်းရေးရင်းနဲ့မို့ တစ်လက်စတည်း `FOREIGN KEY` အကြောင်းပါထည့်ရေးလိုက်တာပါ။ အခုဖတ်တဲ့အချိန်နားလည်ရခက်နိုင်ပေမယ့် relationships လုပ်ရတဲ့ query တွေလေ့လာတဲ့အချိန်မှာပိုနားလည်လာပါလိမ့်မယ်။ 
FK ဆိုတာကတော့ column တစ်ခုရဲ့ value ကိုသုံးပြီးတော့ table တစ်လုံးနဲ့တစ်လုံးချိတ်ဆက်တဲ့နေရာမှာအသုံးပြုပါတယ်။ 

`students` table အပြင် `clubs` ဆိုတဲ့နော် table တစ်ခု create လုပ်ရအောင်။ ကျောင်းသားတစ်ယောက်က book club, chess club စသည်ဖြင့် club တစ်ခုခုနဲ့ချိတ်ဆက်နိုင်တဲ့ဆိုတဲ့သဘောပေါ့ဗျာ။

```
CREATE TABLE clubs(
    club_id INT PRIMARY KEY,
    club_name VARCHAR(50)
);
```

`DROP students table;`
ပြီးရင်လက်ရှိ club_id ဆိုတဲ့ column ထပ်ဖြည့်ပြီး students ပြန် create လုပ်ပါမယ်။ 
students table ထဲက club_id ကို FK အဖြစ်သတ်မှတ်ပြီး clubs ဆိုတဲ့ table ရဲ့ primary key `club_id` ကိုလှမ်း reference လုပ်လိုက်ပါမယ်။

#### Schema
```
CREATE TABLE table_name (
    column_name data_type,
    ...,
    CONSTRAINT constraint_name FOREIGN KEY (column_name) REFERENCES referenced_table(referenced_column)
);
```

#### Query
```
CREATE TABLE students(
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    club_id INT,
    CONSTRAINT fk_club FOREIGN KEY (club_id) REFERENCES clubs(club_id)
);
```

`DESCRIBE` keyword ကိုသုံးပြီးပြန်စစ်ကြည့်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl8.png)

ကိုယ်ဆောက်ခဲ့တဲ့ reference key ဝင်မဝင်ဆိုတာကို `SHOW CREATE TABLE` သုံးပြီးကြည့်ရင်ပိုမြင်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl9.png)

### NOT NULL Constraint:

Column value ကို NULL အထည့်မခံစေချင်တဲ့အချိန်မှာတော့ NOT NULL constraint ကိုအသုံးပြုပါတယ်။

#### Schema
```
CREATE TABLE table_name (
    column_name data_type NOT NULL,
    ...,
    constraint_definition
);
```

`students` table ကိုပြန်ဖျက်ပြီး `name` column ကို `NOT NULL` သုံးပြီးပြန်တည်ဆောက်ကြည့်ရအောင်။
ကျနော် `students` table ကိုပြန်ဖျက်ပြီးသုံးနေရတာက လောလောဆယ်မှာ table, column နာမည်တွေနဲ့မရှုပ်သွားစေချင်တာရယ်၊ `ALTER` command သုံးပြီးလုပ်လို့ရပေမယ့်လိုက်လုပ်ရတာခက်သွားမှာစိုးရိမ်မိလို့ပါ။

#### Query
```
CREATE TABLE students(
    student_id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INT NOT NULL
);
```

`DESCRIBE` keyword ကိုသုံးပြီးပြန်စစ်ကြည့်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl10.png)

### DEFAULT Constraint:

Data insert လုပ်တဲ့အချိန်မှာ NULL value ပါလာတဲ့အခါအစားထိုးအနေနဲ့သွင်းဖို့ default value တစ်ခုခု define လုပ်တဲ့နေရာမှာအသုံးပြုပါတယ်။

#### Schema
```
CREATE TABLE table_name (
    column_name data_type DEFAULT default_value,
    ...,
    constraint_definition
);
```

Students table ကိုပြန်ဖျက်ပြီး age column ကို DEFAULT သုံးပြီးပြန်တည်ဆောက်ကြည့်ရအောင်။
age value က null ဖြစ်ပြီဆို 14 ကို default အနေနဲ့ထည့်ပေးမယ်ဆိုတဲ့သဘောပါ။

#### Query
```
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT DEFAULT 14
);
```

`DESCRIBE` keyword ကိုသုံးပြီးပြန်စစ်ကြည့်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl11.png)

### UNIQUE Constraint:

Table ထဲမှာပါတဲ့ columns တွေထဲမှာမှ unique ဖြစ်စေချင်တဲ့ column ရှိတဲ့အခါမှာအသုံးပြုပါတယ်။

#### Schema
```
CREATE TABLE table_name (
    column_name data_type UNIQUE,
    ...,
    constraint_definition
);
```

Students table ကိုဖျက်ပြီးတော့ name column ကို unique constraint ပေးပြီးပြန် create လုပ်ကြည့်ပါမယ်။

#### Query
```
CREATE TABLE students(
    student_id INT PRIMARY KEY,
    name VARCHAR(50) UNIQUE,
    age INT
);
```
`DESCRIBE` keyword ကိုသုံးပြီးပြန်စစ်ကြည့်နိုင်ပါတယ်။

![creating db](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/ddl/ddl12.png)

အသုံးများတဲ့ DDL queries တွေဖော်ပြပေးခဲ့တာဖြစ်ပါတယ်။ တိကျသေချာတဲ့ database schema တစ်ခုထွက်လာအောင်တည်ဆောက်တဲ့နေရာမှာ DDL ကိုကျွမ်းကျင်ဖို့က အလွန်အရေးပါပါတယ်။ 
နောက်အပိုင်းမှာ DQL အကြောင်းကိုဆက်လေ့လာသွားကြပါမယ်။
