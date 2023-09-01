# DQL (Data Query Language)

Database ထဲက data တွေကိုဆွဲထုတ်လိုတဲ့အချိန်မှာ DQLလို့ခေါ်တဲ့ query တွေကိုအသုံးပြုပါတယ်။ `SELECT` ကိုအသုံးပြုပြီးတော့ အနောက်မှာ condition အခြေအနေအမျိုးမျိုးလိုက်ပြီးတော့ data တွေကို filter လုပ်နိုင်ပါတယ်။ Condition အခြေအနေတွေသတ်မှတ်ဖို့အတွက် `WHERE` ဆိုတဲ့ statement ကိုသုံးပါတယျ။ WHERE statement ရဲ့နောက်မှာလိုသလို filter လုပ်သွားနိုင်ပါတယ်။ဒီအပိုင်းမှာတော့ DQL ကိုပေါ်လွင်အောင်ရိုးရှင်းတဲ့ နမူနာ queries တွေနဲ့အတူလေ့လာသွားကြပါမယ်။

MySQL command line client ကိုဖွင့်ပြီးတော့ DQL queries တွေစမ်းရေးကြည့်ဖို့အတွက် database အသစ်တစ်ခုဆောက်ရအောင်။

`CREATE DATABASE dql_test;`
ဆောက်ပီးရင်သုံးဖို့အတွက် ready ဖြစ်အောင်
`use dql_test;` ဆိုပြီးလုပ်ပေးထားလိုက်ပါမယ်။

![DQL1](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql1.png)

  
DQL queries တွေစမ်းဖို့အတွက် `products` ဆိုတဲ့ table တစ်ခုဆောက်ပါမယ်။ 

```
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(255),
    category VARCHAR(50),
    price DECIMAL(10, 2),
    stock_quantity INT,
    supplier VARCHAR(100)
);
```

![DQL2](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql2.png)

Table ဆောက်ပြီးပြီးဆိုတော့ dummy data တစ်ချို့ထည့်သွင်းပါမယ်။
`INSERT` statement ကိုသုံးပါမယ်။
```
INSERT INTO products VALUES
(1, 'Laptop', 'Electronics', 899.99, 25, 'TechCorp'),
(2, 'Smartphone', 'Electronics', 599.99, 50, 'GadgetZone'),
(3, 'T-shirt', 'Clothing', 19.99, 100, 'FashionRUs'),
(4, 'Desk', 'Furniture', 149.99, 15, 'HomeFurnish'),
(5, 'Headphones', 'Electronics', 89.99, 75, 'AudioTech'),
(6, 'Shoes', 'Footwear', 59.99, 40, NULL),
(7, 'Backpack', 'Accessories', 39.99, 30, 'GearUp'),
(8, 'Watch', 'Accessories', 129.99, 10, 'TimePieces');
```

![DQL3](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql3.png)

DQL ဖြစ်တဲ့အတွက်ဒီအပိုင်းမှာ `SELECT` statement နဲ့ `WHERE` statement ကိုအဓိကသုံးသွားမှာဖြစ်ပြီးတော့ query schema ကတော့အောက်ပါအတိုင်းဖြစ်ပါတယ်။
```
SELECT column1, column2, ...
FROM products
WHERE condition;
```
Condition နေရာမှာတော့လိုအပ်သလိုပုံစံမျိုးစုံလိုက်နိုင်ပါတယ်။ အောက်ကနမူနာတွေမှာဆက်ဖော်ပြပေးထားပါတယ်။

ပထမဦးဆုံး products table ထဲကနေ `category` column က `Electronics` ဖြစ်တဲ့ value ကိုဆွဲထုတ်ကြည့်ပါမယ်။
column value အားလုံးလိုချင်တဲ့အတွက် * ကိုသုံးပါမယ်။

```
SELECT *
FROM products
WHERE category = 'Electronics';
```
တူညီတဲ့ value ကိုလိုချင်တဲ့အတွက် `=` sign ကိုအသုံးပြုပါတယ်။

![DQL4](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql4.png)

ဈေးနှုန်း price column ကို 100 ကျော်တဲ့ records တွေကိုဆွဲထုတ်ကြည့်ပါမယ်။
`*` မသုံးဘဲနဲ့လိုချင်တဲ့ column တွေကိုပဲ comma နဲ့ဖြတ်ပြီးသတ်မှတ်ပေးလိုက်ပါမယ်။

```
SELECT product_name, price
FROM products
WHERE price > 100;
```
100`ကျော်`တဲ့ records ဆိုတဲ့အတွက် `>` sign ကိုအသုံးပြုပါတယ်။
အောက်ရောက်တယ်ဆိုရင် `<` less than sign ကိုသုံးပါမယ်။</br>
အားလုံးသိပြီးထားတဲ့ sign တွေအတိုင်းပါပဲ </br>
less than and equal ဆို `≤`</br>
greater than and equal ဆို `≥`  အသုံးပြုပါတယ်။</br>

![DQL5](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql5.png)

ဒီတစ်ခါ `AND` ဆိုတဲ့ keyword ကိုသုံးပြီး condition နှစ်ခု combine လုပ်ကြည့်ပါမယ်။ လွယ်ကူပါတယ်၊ condition နှစ်ခုကြားမှာအောက်ကလို `AND` ဆိုပြီးခံပေးလိုက်ရုံပါပဲ။ condition ကတော့ stock_quantity column ကို 50 အောက်ရောက်နေပြီးတော့ ဈေးနှုန်းက 20 ထက်ကြီးတဲ့ records တွေကိုဆွဲထုတ်ပါမယ်။

```
SELECT product_name, stock_quantity, price
FROM products
WHERE stock_quantity < 50 AND price > 20;
```
![DQL6](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql6.png)

ဒီတစ်ခါတော့ `product_name` မှာ `Smart` ဆိုတဲ့ value ပါတဲ့ records တွေကိုဆွဲထုတ်ပါမယ်။
keyword နဲ့တိုက်ပီးရှာချင်တယ်ဆိုရင် `%` sign ကိုအသုံးပြုပါတယ်။

```
SELECT product_name, category
FROM products
WHERE product_name LIKE '%Smart%';
```

`WHERE column_name LIKE 'abc%'`
% sign ကနောက်မှာ value ကရှေ့မှာဆို abc နဲ့စတဲ့ values ရှာမယ်။
`WHERE column_name LIKE '%a' `
% sign ကရှေ့မှာ value ကနောက်မှာဆို abc နဲ့ဆုံးတဲ့ values ရှာမယ်။
`WHERE column_name LIKE '%abc%' `
% sign ကိုရှေ့နောက်နှစ်ခုလုံးကပ်ထားမယ်ဆိုနေရာမရွေးဘဲရှာမယ်။

![DQL7](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql7.png)


`supplier` တန်ဖိုးက `NULL` ဖြစ်နေ (မရှိနေ)တဲ့ records တွေကိုဆွဲထုတ်ကြည့်ပါမယ်။

```
SELECT product_name, supplier
FROM products
WHERE supplier IS NULL;
```

![DQL8](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql8.png)
----------
Range တန်ဖိုးတွေဆက်ဆွဲထုတ်ကြည့်ရအောင်၊ ဘယ်တန်ဖိုးကနေ ဘယ်တန်ဖိုးအထိဆိုတာမျိုးပေါ့။

`WHERE` နောက်မှာ `BETWEEN` နဲ့ `AND` keyword ကိုလိုက်ပြီးအသုံးပြုနိုင်ပါတယ်။
`BETWEEN` နောက်မှာအစတန်ဖိုး၊ `AND` နောက်မှာအဆုံးတန်ဖိုးထည့်ပါမယ်။

```
SELECT product_name, price
FROM products
WHERE price BETWEEN 50 AND 100;
```

![DQL9](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql9.png)
အပေါ်မှာတုန်းကတူတဲ့ value ဆိုချင်ရင် `=` ဆိုတဲ့ sign ကိုအသုံးပြုခဲ့တယ်။
`=` က value တစ်ခုပဲ assign လုပ်ချင်ပေမယ့် value တစ်ခုထက်ပိုပြီးထည့်သုံးချင်တဲ့အခါ `IN` ဆိုတဲ့ keyword ကိုပြောင်းသုံးရပါမယ်။

`category` column က `Clothing` ဒါမှမဟုတ် `Accessories` ဖြစ်တဲ့ records တွေကိုဆွဲထုတ်ကြည့်ပါမယ်။
```
SELECT product_name, category
FROM products
WHERE category IN ('Clothing', 'Accessories');
```

![DQL10](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql10.png)
`IN` ရဲ့ပြောင်းပြန် `NOT IN` ကိုသုံးလိုက်မယ်ဆိုရင်တော့အဲ့ဒီ value တွေမပါတဲ့ records တွေကိုဆွဲထုတ်ပေးပါလိမ့်မယ်။
အောက်က screenshot မှာ result ကိုကြည့်နိုင်ပါတယ်။

![DQL11](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql11.png)
value ကတစ်ခုတည်းဆိုရင်တော့ `NOT IN` ကိုမသုံးဘဲ `NOT` ဆိုတဲ့ keyword တစ်ခုတည်းနဲ့လည်းအသုံးပြုနိုင်ပါတယ်။
အောက်မှာဆိုရင် `category` က `Furniture` မဟုတ်တဲ့ records တွေကိုဆွဲထုတ်ထားတာဖြစ်ပါတယ်။

```
SELECT product_name, category
FROM products
WHERE NOT category = 'Furniture';
```

![DQL12](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dql/dql12.png)

DQL ရဲ့သဘောက data တွေကိုမိမိလိုချင်သလိုဆွဲထုတ်နိုင်ဖို့ပါပဲ၊ ဒီလိုဆွဲထုတ်ဖို့အတွက် SELECT နဲ့ WHERE ကဘယ်လောက်ထိအရေးပါလဲဆိုတာအထက်က queries တွေကိုကြည့်ရင်မြင်နိုင်ပါတယ်။ အခု article မှာတော့ DQL သဘောပေါ်လွင်အောင် ရိုးရှင်းတဲ့ query တွေကိုပဲအသုံးပြုထားပါသေးတယ်။ နောက်ပိုင်းမှာ advance ဖြစ်တဲ့ query တွေနဲ့ data ဆွဲထုတ်ပုံတွေကိုလည်းဆက်လက်ရေးသားပေးပါမယ်။
