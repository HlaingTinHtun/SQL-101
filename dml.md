## DML (Data Manipulation Language) 

Database ထဲမှာရှိတဲ့ data တွေကိုလိုသလိုပြင်ဆင်ဖို့အတွက်(Manipulationလုပ်ဖို့အတွက်)အသုံးပြုပါတယ်။ DML queries တွေမှာ အဓိကအားဖြင့် SELECT, INSERT, UPDATE, DELETE keyword တွေကိုတွေ့ရမှာဖြစ်ပါတယ်။

SELECT နဲ့ INSERT query ကိုတော့ရှေ့အပိုင်းတွေမှာလည်းတွေ့ပြီးသားဖြစ်တဲ့အတွက် ဒီအပိုင်းမှာတော့ UPDATE, DELETE queries တွေကိုအာရုံစိုက်ပြီးကြည့်သွားကြပါမယ်။

### INSERT 
အရှေ့အပိုင်းမှာသုံးခဲ့တဲ့ `products` table ကိုဆက်သုံးကြရအောင်။</br>
`select` အရင်ဆွဲကြည့်မယ်၊ records 8ကြောင်းရှိတာကိုတွေ့ပါမယ်၊ INSERT query ပြန်နွေးတဲ့အနေနဲ့ တစ်ကြောင်းထပ်ထည့်ကြည့်ပါမယ်။

`INSERT INTO products VALUES(9, 'Tablet', 'Electronics', 500, 50, 'SupplierA');`

![DML1](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dml/dml1.png)

---
### UPDATE
Table ထဲမှာရှိတဲ့ data တွေကို update လုပ်ကြပါမယ်။ 
`UPDATE` ဆိုတဲ့ command ကိုသုံးပါတယ်။

#### Schema
```
UPDATE table_name
SET column_name = value
WHERE column_name = value;
```

Products table ထဲမှာရှိတဲ့ `product_name` က `Smartphone` ဖြစ်တဲ့ records တွေရဲ့ price တန်ဖိုးကိုပြင်ကြည့်ပါမယ်။ ဒါဆို query ကဒီလိုဖြစ်ပါမယ်။

```
UPDATE products
SET price = 649.99
WHERE product_name = 'Smartphone';
```

`select` နဲ့ပြန်ခေါ်ကြည့်မယ်ဆို `product_name` က `Smartphone` ဖြစ်တဲ့ record ရဲ့ `price` တန်ဖိုးပြောင်းသွားတာကိုမြင်နိုင်မှာဖြစ်ပါတယ်။ </br>
`select` ဆွဲတဲ့နေရာမှာလေ့ကျင့်တဲ့အနေနဲ့ အောက်က screenshot ကိုမကြည့်သေးဘဲမိမိဘာသာစမ်းပြီးရေးကြည့်ဖို့တိုက်တွန်းချင်ပါတယ်။

Schema
`select * from table_name where condition`
![DML2](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dml/dml2.png)
 ---
`product_name` က `Desk` ဖြစ်တဲ့ records တွေရဲ့ `stock_quantity` တန်ဖိုးကိုထပ်ပြီးပြင်ဆင်ကြည့်ပါမယ်။ 

```
UPDATE products
SET stock_quantity = 20
WHERE product_name = 'Desk';
```
ထုံးစံအတိုင်း update query ရဲ့ result ကို select query ပြန်ရေးပြီးကြည့်နိုင်ပါတယ်။

![DML3](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dml/dml3.png)

--- 

ဒီတစ်ခါတော့ value set လုပ်တဲ့နေရာမှာ calculation လုပ်ပြီးပြင်ဆင်ကြည့်ရအောင်။ </br>

`category` က `Electronics` ဖြစ်တဲ့ records တွေရဲ့ `stock_quantity` တန်ဖိုးကို မူလရှိရင်းစွဲတန်ဖိုးထက် ၁၀ခုပေါင်းထည့်ချင်တယ်ဆိုပါစို့၊ ဒီလိုမျိုးရေးနိုင်ပါတယ်။

```
UPDATE products
SET stock_quantity = stock_quantity + 10
WHERE category = 'Electronics';
```
အလားတူအခြားသော ပေါင်း၊နုတ်၊မြောက်၊စား signs တွေလည်းသုံးနိုင်ပါတယ်။

![DML4](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dml/dml4.png)
 
---

အောက်က example မှာတော့ multiplication sign ကိုသုံးပြထားပါတယ်။</br>
`category` က `Clothing` ဖြစ်တဲ့ records တွေရဲ့ `price` ကိုနှစ်ဆတင်ပြထားပါတယ်။

```
UPDATE products
SET price = price * 2
WHERE category = 'Clothing';
```

![DML5](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dml/dml5.png)
 
---

### DELETE

#### Schema
```
DELETE FROM table_name WHERE condition;
```

`product_name` က `Shoes` ဖြစ်တဲ့ records တွေကိုဖျက်ချပါမယ်။</br>
ဒါဆို query ကဒီလိုဖြစ်ပါမယ်။

```
DELETE FROM products
WHERE product_name = 'Shoes';
```

ပျက်သွားလားဆိုတာကို select ပြန်ဆွဲပြီးကြည့်နိုင်ပါတယ်။ Delete ချတဲ့နေရာမှာ WHERE condition မလိုက်လို့လည်းရပါတယ်။</br>
မလိုက်ဘူးဆိုရင်တော့ table ထဲမှာရှိတဲ့ data တွေအကုန်ပျက်သွားမှာဖြစ်ပါတယ်။

![DML6](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dml/dml6.png)

---
အရှေ့မှာ example တွေပြခဲ့တဲ့အတိုင်း WHERE condition တွေနောက်မှာ filter လုပ်တဲ့ signs တွေလိုက်နိုင်ပါတယ်(=, <, > etc.)။ </br>
DELETE query တွေမှာလည်းဒီလို filter တွေလုပ်ပြီးသုံးနိုင်ပါတယ်။

`stock_quantity` 30 အောက်ရောက်နေတဲ့ records တွေဖျက်ချင်တယ်ဆိုပါစို့။

```
DELETE FROM products
WHERE stock_quantity < 10;
```

![DML7](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/dml/dml7.png)
 

အရှေ့က DQL မှာရေးခဲ့တဲ့ `NULL`,  `NOT NULL` ဒီလို filter တွေခံပြီးတော့လည်းသုံးနိုင်ပါတယ်။
ဥပမာ `supplier` တန်ဖိုးက `NULL` ဖြစ်နေတဲ့ records တွေကိုဖျက်ချင်တယ်ဆို

```
DELETE FROM products
WHERE supplier IS NULL;
```

DML ရဲ့ကြောရိုးက ဒီ command ၄ခုပဲဖြစ်ပါတယ်။ သဘောတရားကိုအရင်နားလည်စေချင်တဲ့အတွက်ရိုးရှင်းတဲ့ example queries တွေနဲ့ပဲရေးပြပေးထားပါတယ်။ 


DDL, DQL, DML ရဲ့သဘောတရားကိုနားလည်သွားပြီဆိုနောက်အပိုင်းတွေမှာပိုပြီး advanced ဖြစ်တဲ့ queries ကိုလေ့လာသွားကြပါမယ်။ 

advanced ဖြစ်တဲ့ queries လို့ဆိုပေမယ့်လည်းလေ့လာခဲ့တဲ့ DDL, DQL, DML ဆိုတဲ့ category သုံးခုပေါ်မှာပဲ based လုပ်သွားမှာဖြစ်တဲ့အတွက်လေ့လာရလွယ်ကူမှာဖြစ်ပါတယ်။
