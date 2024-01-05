## Relationships In Queries

အရှေ့အပိုင်းမှာရေးခဲ့တဲ့ one to one, one to many, many to many relationship တွေအကြောင်းကိုအခုအပိုင်းမှာလက်တွေ့ query တွေရေးကြည့်ပြီးထပ်လေ့လာသွားကြပါမယ်။ INNER နဲ့ LEFT JOIN တွေကိုအဓိကထားပြီးသုံးသွားမှာဖြစ်လို့ဘယ်လိုပုံစံမျိုးလိုချင်တဲ့အခါ ဘယ် JOIN ကိုသုံးနိုင်တယ်ဆိုတာမျိုးကိုပါတစ်ပါတည်းမှတ်သွားစေချင်ပါတယ်။

### One to one
Query တွေစမ်းပြီးရေးကြည့်ဖို့အတွက် `students` နဲ့ `student_details`table နှစ်လုံးကိုအသုံးပြုပါမယ်။ `student` တစ်ယောက်မှာ detail info တစ်ခုသာရှိနိုင်ပါတယ်။ (One to one relationship type)

`students` table ထဲမှာရှိတဲ့ records တွေကိုသက်ဆိုင်ရာ `student_details` records တွေနဲ့အတူ JOIN လုပ်ပြီးဆွဲထုတ်ကြည့်ပါမယ်
```
SELECT students.student_id, students.name, student_details.address FROM students JOIN student_details ON students.student_id = student_details.student_id;
```

![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq1.png)

---

`student_details` ဘက်မှာ records မရှိတဲ့ `students` တွေကိုထုတ်ကြည့်ပါမယ်။
```
SELECT students.student_id, students.name FROM students LEFT JOIN student_details ON students.student_id = student_details.student_id WHERE student_details.student_id IS NULL;
```
![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq2.png)

---
`students` တစ်ယောက်တည်းကိုပဲသူ့ရဲ့ details record နဲ့အတူဆွဲထုတ်ကြည့်ပါမယ်။
```
SELECT students.name, student_details.address FROM students LEFT JOIN student_details ON students.student_id = student_details.student_id WHERE students.student_id = 2;
```
![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq3.png)

---

### One-to-Many Relationship:

Relationship အပိုင်းမှာတုန်းက create လုပ်ခဲ့တဲ့ `authors` နဲ့ `books` table ကိုအသုံးပြုပါမယ်။ `authors` တစ်ယောက်မှာရေးခဲ့တဲ့ `books` တွေအများကြီးရှိနိုင်တယ်ဆိုတဲ့ **one to many** relationship ပုံစံဖြစ်ပါတယ်။ Table အလွတ်တွေဖြစ်တဲ့အတွက် data တွေအရင်ထည့်ပါမယ်။
```
-- Insert authors
INSERT INTO authors (author_id, name) VALUES
(1, 'Jane Doe'),
(2, 'John Smith'),
(3, 'Alice Johnson');
```
```
-- Insert books
INSERT INTO books (book_id, title, author_id) VALUES
(101, 'The Art of SQL', 1),
(102, 'Database Design Mastery', 1),
(103, 'Query Optimization Techniques', 2),
(104, 'Introduction to Relational Databases', 3);
```
![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq4.png)
![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq5.png)

---
စာအုပ်တွေကိုဆွဲထုတ်ရင်းတစ်ပါတည်းရေးခဲ့တဲ့ author တွေကိုပါထုတ်ကြည့်ပါမယ်။
```
SELECT books.book_id, books.title, authors.name AS author_name FROM books JOIN authors ON books.author_id = authors.author_id;
```

![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq6.png)

---

စာအုပ်မရေးဖူးတဲ့ author record ကိုဆွဲထုတ်ကြည့်ပါမယ်။
```
SELECT authors.author_id, authors.name FROM authors LEFT JOIN books ON authors.author_id = books.author_id WHERE books.book_id IS NULL;
```

![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq7.png)

---

လောလောဆယ်သွင်းထားတဲ့ data အရ စာအုပ်မရေးထားတဲ့ author record မရှိတဲ့အတွက်ကြောင့် author record အသစ်တစ်ကြောင်းထည့်ကြည့်ပြီး query ကိုပြန် run ကြည့်ပါမယ်။

![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq8.png)

book record မရှိတဲ့ author တစ်ယောက်ဖန်တီးလိုက်ပါပြီ။ Query ကိုပြန် run ကြည့်မယ်ဆို book record reference မရှိတဲ့ author record ကိုမြင်ရမှာဖြစ်ပါတယ်။



### Many-to-Many Relationship:

`students` တစ်ယောက်မှာ `courses` တွေအများကြီးရှိနိုင်သလို `courses` တစ်ခုမှာလည်း `students` အများကြီးရှိနေနိုင်တဲ့ many to many relationship type ဖြစ်ပါတယ်။
Table အလွတ်တွေဖြစ်တဲ့အတွက်ထုံးစံအတိုင်း data တွေအရင်ထည့်ပါမယ်။
```
-- Insert courses
INSERT INTO courses (course_id, course_name) VALUES
(201, 'Database Fundamentals'),
(202, 'Advanced SQL Queries'),
(203, 'Data Modeling and Design'),
(204, 'Database Administration');
```
![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq10.png)

---

```
-- Insert student courses
INSERT INTO student_courses (student_course_id, student_id, course_id) VALUES
(1, 1, 201),
(2, 1, 202),
(3, 2, 202),
(4, 2, 203),
(5, 3, 201),
(6, 3, 204);
```
![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq11.png)

---

`student_id` 1 ဖြစ်တဲ့ကျောင်းသားကဘယ်လို `courses` တွေယူထားလဲဆိုတာဆွဲကြည့်ရအောင်။ Many to many relation ဖြစ်တဲ့ဒီနေရာမှာ junction table တစ်ခုခံထားတဲ့အတွက် JOIN ကနှစ်ခါဖြစ်သွားတာကိုသတိချပ်ထားရပါမယ်။

```
SELECT students.name, courses.course_name FROM students JOIN student_courses ON students.student_id = student_courses.student_id JOIN courses ON student_courses.course_id = courses.course_id WHERE students.student_id = 1;
```

![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq12.png)

---

`course_id` 201 မှာတက်ရောက်နေတဲ့ `students` တွေကိုလည်းထုတ်ကြည့်နိုင်ပါတယ်။
```
SELECT courses.course_name, students.name FROM courses JOIN student_courses ON courses.course_id = student_courses.course_id JOIN students ON student_courses.student_id = students.student_id WHERE courses.course_id = 201;
```

![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq13.png)

---

`students` ရော `courses` တွေရောအားလုံးကိုဆွဲထုတ်ကြည့်ပါမယ်။ `courses` တွေတက်ရောက်ထားခြင်းမရှိတဲ့ကျောင်းသားတွေတော့ `COALESCE` ဆိုတဲ့ function ကိုသုံးပြီးတော့ `course_name` နေရာမှာ `No Course`ဆိုတဲ့စာသားတစ်ခုအစားထိုးထည့်ပေးလိုက်ပါမယ်။

```
SELECT students.name, COALESCE(courses.course_name, 'No Course') AS course_name FROM students LEFT JOIN student_courses ON students.student_id = student_courses.student_id LEFT JOIN courses ON student_courses.course_id = courses.course_id;
```

![rtq](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/rtq/rtq14.png)

---

ဒီအပိုင်းထိရောက်လာပီဆိုရင် query တွေနည်းနည်းအဆင့်မြင့်လာတာနဲ့အတူသူတို့ရဲ့ complexity ရှုပ်ထွေးမှုအပိုင်းလေးတွေကိုပါအနည်းငယ်ခံစားလာရမှာဖြစ်ပါတယ်။ သို့ပေမယ့် အရှေ့နှစ်ပိုင်းမှာရေးခဲ့တဲ့ relationship types , joins တွေအကြောင်းကိုသေချာလိုက်လုပ်ထားမယ်ဆို ဒီအပိုင်းကိုလည်းလိုက်နိုင်မယ်လို့ထင်ပါတယ်။ စာသိပ်မလိုက်နိုင်ဘူးဆို relationship နဲ့ join အပိုင်းကို revision ပြန်လုပ်ပြီးပြန်ဖတ်ပါလို့တိုက်တွန်းချင်ပါတယ်။



