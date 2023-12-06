## Relationships in SQL

ဒီအပိုင်းမှာတော့ execute လုပ်တဲ့ screenshots တွေမပါသေးပါဘူး။ SQL ရဲ့ `relationship` အကြောင်းကိုပေါ်လွင်အောင်ရှင်းပြပေးပြီးတော့ နောက်အပိုင်းတွေမှာတစ်ခုခြင်းဆီကို နမူနာတွေနဲ့တကွ run ကြည့်သွားပါမယ်။

SQL မှာ `relationship` ဆိုတာက Tables တွေကိုချိတ်ဆက်ပြီးလိုအပ်သလို data တွေကိုဆွဲထုတ်ခြင်းကိုဆိုလိုပါတယ်။ Table တစ်လုံးခြင်းဆီတိုင်းက သီးသန့်ရပ်တည်နိုင်သလို တစ်လုံးနှင့်တစ်လုံး `ပတ်သက်ဆက်နွယ်ခြင်း` မျိုးတွေလည်းရှိနိုင်ပါတယ်၊ ဒီလိုပတ်သက်ဆက်နွယ်ခြင်းကို `relationship` အနေနဲ့သတ်မှတ်နိုင်ပြီး Table တစ်လုံးနဲ့တစ်လုံးဘယ်လိုချိတ်ဆက်နိုင်မလဲဆိုတာကို အောက်မှာဥပမာတွေပေးပြီးရှင်းပြပေးသွားပါမယ်။

### Primary Key

Primary Key ဆိုတာကတော့ Table တစ်လုံးမှာရှိတဲ့ unique identifier column ဖြစ်ပါတယ်။ `unique` ဖြစ်တယ်ဆိုတာ record (row) တိုင်းမှာပါတဲ့ အဲ့ဒီ column ရဲ့ value မှာ `ထပ်` နေခြင်းမရှိတာကိုဆိုလိုခြင်းဖြစ်ပါတယ်။

ဥပမာအောက်က `employees`ဆိုတဲ့ Table မှာ `employee_id` ဆိုတဲ့ column ဟာအမြဲတမ်း `unique` ဖြစ်နေနိုင်တဲ့အတွက် `PRIMARY KEY` အဖြစ်သတ်မှတ်ထားလို့ရပါတယ်။

```
CREATE Table employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    department_id INT
);
```

ဒီ `PRIMARY KEY`  ကို Table တွေ `relationship` ချိတ်ဆက်တဲ့နေရာမှာလည်းပြန်လည်အသုံးပြုပါတယ်။

### Foreign Keys

Foreign Key ဆိုတာကတော့တစ်ခြား Table တစ်လုံးက primary key ဖြစ်ပါတယ်။ Table နှစ်လုံးကိုချိတ်ဆက်တဲ့အခါအသုံးပြုတဲ့အရာပဲဖြစ်ပါတယ်။ Table B က Table A ကိုချိတ်ဆက်ချင်တယ်ဆို Table B ထဲမှာ Table A ရဲ့ primary key ကိုထည့်လိုက်ခြင်းဖြင့်ချိတ်ဆက်နိုင်ပါတယ်။
အောက်ကဥပမာကိုကြည့်လိုက်ရင်ပိုပြီးမြင်သွားလိုက်ပါမယ်။
```
CREATE Table departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(50)
);
```

`departments` ဆိုတဲ့ Table တစ်လုံးရှိပါမယ်၊ `department_id` ကို `PRIMARY KEY` အဖြစ်သတ်မှတ်ထားပါတယ်။

```
CREATE Table employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(department_id)
);
```

`employees` ဆိုတဲ့ Table ထဲမှာ `department_id` ထည့်ထားပြီး `FOREIGN KEY` အဖြစ်သတ်မှတ်လိုက်မယ်ဆို `employees` Table ကနေတစ်ဆင့် `departments` Table ထဲက data တွေကိုပါဆွဲထုတ်နိုင်သွားမှာဖြစ်ပါတယ်။ `department_id` က `departments` Table ထဲမှာတော့ `PRIMARY KEY` ဖြစ်ပေမယ့် `employees` Table ထဲမှာတော့ `FOREIGN KEY` အနေနဲ့ဖြစ်သွားပါတယ်။

``` 
FOREIGN KEY (department_id) REFERENCES departments(department_id)
```

ဒါကတော့ `FOREIGN KEY` အဖြစ်သတ်မှတ်ကြောင်းရေးတဲ့အပိုင်းဖြစ်ပါတယ်။ ဘယ် Table ကို `REFERENCES (link)` လုပ်မလဲဆိုတာကိုပါထည့်သွင်းပေးရပါမယ်။

### Types of Relationships
Relationship ရဲ့သဘောတရားကိုနားလည်သွားပြီဆိုတော့ relationship `type` အကြောင်းလေးတွေကိုဆက်ရှင်းပေးသွားပါမယ်။ Table တစ်လုံးနဲ့တစ်လုံးချိတ်ဆက်တဲ့အချိန်မှာ ချိတ်ဆက်နိုင်တဲ့ `အမျိုးအစား` တွေလို့လည်းဆိုနိုင်ပါတယ်။

#### One To One Relationship
Table တစ်ခုနဲ့တစ်ခုဟာ `one to one` ပုံစံမျိုးနဲ့ပဲချိတ်ဆက်ထားတာကို one to one relationship လို့ခေါ်ပါတယ်။ ဥပမာအောက်ကနမူနာမှာဆို `students` Table နဲ့ `student_details` ဆိုတဲ့ Table နှစ်လုံးရှိပါတယ်။ `student` တစ်ယောက်ဟာ သူနဲ့ပတ်သတ်တဲ့ `detail` record တစ်ခုပဲရှိနိုင်ပါတယ်။ ဒါကြောင့်မို့ ဒီ Table နှစ်လုံးရဲ့ relationship ပုံစံဟာ `one to one` ဖြစ်ပါတယ်။

```
CREATE Table students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50)
);
```

```
CREATE Table student_details (
    student_id INT PRIMARY KEY,
    address VARCHAR(100),
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);
```
#### One To Many Relationship

Tableတစ်လုံးက record သည် နောက် Table တစ်လုံးမှာ တစ်ခုထက်ပိုသော records တွေအဖြစ်ချိတ်ဆက်နိုင်ခြေရှိတယ်ဆို `one to many` relationship ပုံစံမျိုးဖြစ်နိုင်ပါတယ်။

ဥပမာအောက်ကနမူနာမှာဆို `author` Table တစ်လုံးရှိပါမယ်။ `author` တစ်ယောက်ကစာအုပ်တွေတစ်အုပ်ထက်ပိုပြီးရေးနိုင်ပါတယ်။ ဒါကြောင့် `books` Table မှာ `author_id` ကို foreign key အဖြစ်ထားပြီး `one to many` relationship ပုံစံမျိုးချိတ်ဆက်နိုင်ပါတယ်။
`authors` -> one , `books` -> many ဖြစ်သွားပါမယ်။

ဒီလိုချိတ်ဆက်လိုက်ခြင်းအားဖြင့် `books` Table ထဲက records တွေကိုဆွဲထုတ်တဲ့အချိန်မှာ အဲ့ဒီ book record ရဲ့ `author` information တွေကိုတစ်ပါတည်းဆွဲနိုင်မှာဖြစ်ပါတယ်။

```
CREATE Table authors (
    author_id INT PRIMARY KEY,
    name VARCHAR(50)
);
```
```
CREATE Table books (
    book_id INT PRIMARY KEY,
    title VARCHAR(100),
    author_id INT,
    FOREIGN KEY (author_id) REFERENCES authors(author_id)
);	
```

#### Many To Many Relationship
Table နှစ်လုံးလုံးဟာအခြင်းခြင်း တစ်ခုထက်ပိုတဲ့ records တွေအပြန်အလှန်ရှိနိုင်ခြေရှိတယ်ဆို `many to many` relationship ပုံစံမျိုးဖြစ်သွားနိုင်ပါတယ်။ ဒီလိုအခြေအနေမှာတော့ကြည့်ရတာပိုပြီးရှင်းလင်းအောင် ကြားခံ Table တစ်လုံးဆောက်လေ့ရှိကြပါတယ်။ Table နှစ်လုံးကို ကြားခံဆက်သွယ်ပေးတဲ့ပုံစံဖြစ်ပါတယ်။ `junction` Table, `associative` Table လို့လည်းခေါ်ကြပါတယ်။

အောက်ကနမူနာကိုကြည့်မယ်ဆို `students` Table နဲ့ `courses` Table ကိုမြင်ရပါမယ်။ student တစ်ယောက်ဟာ course တွေအများကြီးရှိနိုင်သလို course တစ်ခုမှာလည်း student တွေအများကြီးတက်ရောက်နေတာမျိုးရှိပါတယ်။ ဒီလိုအခြေအနေကို `many to many` လို့ခေါ်ဆိုနိုင်ပြီး ဒီနှစ်ခုကိုလွယ်ကူစွာချိတ်ဆက်နိုင်ရန်အတွက် `student_courses` ဆိုပြီးကြားခံ `junction` Table တစ်ခုဆောက်နိုင်ပါတယ်။ Junction Table ထဲမှာ `students` Table နဲ့ `courses` Table ကို reference လုပ်နိုင်တဲ့ `FOREIGN KEYS` တွေထည့်လိုက်ရုံပါပဲ။
```
CREATE Table students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50)
);
```

```
CREATE Table courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100)
);
```
```
CREATE Table student_courses (
	student_course_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

ဒီအပိုင်းမှာ relationship ဆိုတာကို theoretically အရ နားလည်ရလွယ်ကူအောင်အရင်ရှင်းပြပေးခဲ့ပါတယ်။ relationship ဆိုတာဘာလဲ၊ ဘယ်လိုမျိုးချိတ်ဆက်နိုင်တယ်၊ ဘယ်လို relationship အမျိုးအစားတွေရှိမယ်ဆိုတာတွေကိုရေးခဲ့ပါတယ်။ လက်တွေ့ query တွေကို execute မလုပ်ရသေးတဲ့အတွက်နည်းနည်းနားလည်ရခက်နိုင်ပေမယ့် နောက်အပိုင်းတွေမှာ relationship အမျိုးအစားတွေကို တစ်ခုခြင်းဆီအသေးစိတ်ပြန်ရေးရင်း query တွေ run ကြည့်သွားမှာဖြစ့်တဲ့အတွက် ပိုပြီးနားလည်သွားမယ်လို့ထင်ပါတယ်။
