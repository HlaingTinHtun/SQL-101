## Triggers

SQL ရဲ့ data manipulation action (INSERT, UPDATE, DELETE) ပေါ်မှာမူတည်ပြီး automatic query တွေ ထပ်ပြီး run ချင်တဲ့နေရာမျိုးမှာ Trigger တွေကိုအသုံးပြုနိုင်ပါတယ်။ ဥပမာ `student` ဆိုတဲ့ table ထဲကို `INSERT` ထည့်တဲ့အချိန်မှာ `student_logs` table ထဲကို data ထပ်သွင်းနိုင်ဖို့ trigger ကိုအသုံးပြုပြီး define လုပ်ထားနိုင်ပါတယ်။

Trigger နှစ်မျိုးရှိပါတယ်။

#### Before Triggers
- Before ကတော့ မူလ query event execute မလုပ်ခင်မှာ triggering လုပ်ပါတယ်။
- များသောအားဖြင့် DB ထဲမှာပြောင်းလဲမှုတွေမလုပ်ခင် validation လုပ်ဖို့အတွက်အသုံးပြုပါတယ်။

#### After Triggers
- After ကတော့မူလ query event က execute လုပ်ပြီးတော့မှ triggering လုပ်ပါတယ်။
- DB ထဲမှာပြောင်းလဲမှုတွေပြီးမှ trigger လုပ်တဲ့အတွက်များသောအားဖြင့် logging, reporting တို့အတွက်အသုံးပြုပါတယ်။

Schema ကတော့အောက်ပါအတိုင်းဖြစ်ပါတယ်။
```
CREATE TRIGGER trigger_name
BEFORE INSERT ON table_name
FOR EACH ROW
BEGIN
    -- Trigger statements
END;
```

နမူနာ query လေးတွေစမ်းလုပ်ကြည့်ပါမယ်။

`products` table ထဲကို data update လုပ်တဲ့အချိန်မှာ `price` column ရဲ့ တန်ဖိုးကို 0 အောက်မရောက်ဖို့ validation check လုပ်ကြည့်ပါမယ်။ Execute မလုပ်ခင်မှာ check လုပ်ချင်တာဖြစ်တဲ့အတွက် `BEFORE` ကိုသုံးနိုင်ပါတယ်။ 

```
DELIMITER //

CREATE TRIGGER check_price
BEFORE UPDATE ON products
FOR EACH ROW
BEGIN
    IF NEW.price < 0 THEN
        SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Price cannot be negative';
    END IF;
END; //

DELIMITER ;
```

![trigger](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/tri/tr1.png)

---

`DELIMITER` ထည့်သုံးရခြင်းကတော့ trigger လို stored procedure တွေမှာ statements တွေတစ်ခုထက်ပိုပါနိုင်ပြီး `;` အများအပြားရှိနိုင်ပြီး syntax error ဖြစ်နိုင်တဲ့အတွက် `DELIMITER` ကိုသုံးပြီးတော့ ယာယီအစားထိုးထားလိုက်ခြင်းဖြစ်ပါတယ်။ DELIMITER အကြောင်းအသေးစိတ်ကိုအောက်ကလင့်ခ်မှာဆက်ဖတ်နိုင်ပါတယ်။
https://www.mysqltutorial.org/mysql-stored-procedure/mysql-delimiter/

ဆောက်လိုက်တဲ့ trigger ကိုဒီလိုပြန်ထည့်နိုင်ပါတယ်။

##### Schema
```
SHOW TRIGGERS WHERE `Table` = 'your_table_name';
```
`products` table မှာဆောက်ခဲ့တာဖြစ်တဲ့အတွက်
```
SHOW TRIGGERS WHERE `Table` = 'products';
```
ပြန်စစ်တဲ့အနေနဲ့ `price` column ကို negative value ထည့်ပြီး query တစ်ခု execute လုပ်ကြည့်ပါမယ်။
```
UPDATE products SET price = -100 WHERE product_id = 1;
```

![trigger](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/tri/tr2.png)

ဆောက်ထားတဲ့ `check_price` trigger ကဝင်လာပြီး `error` ပြပေးသွားတာကိုမြင်ရမှာဖြစ်ပါတယ်။


နောက်ထပ်နမူနာတစ်ခုအနေနဲ့ `employee` table ကိုပြောင်းလဲမှုပြုလုပ်တိုင်းမှာ table နောက်တစ်ခုမှာ `audit` logs တွေသိမ်းထားချင်တယ်ဆိုအောက်ပါအတိုင်း `AFTER` trigger တစ်ခုဖန်တီးထားနိုင်ပါတယ်။ သဘောတရားကိုနားလည်သွားပြီလို့ယူဆတဲ့အတွက် Table နောက်တစ်လုံးအသစ်ထပ်မဆောက်တော့ပါဘူး၊ မိမိဘာသာလေ့ကျင့်တဲ့အနေနဲ့စမ်းလုပ်ကြည့်လို့လည်းရပါတယ်။

-	`employee_audit` table အသစ်တစ်လုံးဆောက်မယ်။
-	`employees` table ပေါ်မှာအောက်က query နဲ့ trigger တစ်ခုဖန်တီးမယ်။
-	`employees` table မှာ `UPDATE` query တစ်ခု run ကြည့်မယ်။
	- ဒါဆိုရင် trigger ကအသက်ဝင်သွားပြီး audit table မှာ data အသစ်ထည့်သွားတာကိုမြင်နိုင်မှာဖြစ်ပါတယ်။

```
DELIMITER //

CREATE TRIGGER log_employee_changes
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
    INSERT INTO employee_audit (employee_id, action, timestamp)
    VALUES (OLD.employee_id, 'UPDATE', NOW());
      END; //

DELIMITER ;
```

ဒီလောက်ဆိုရင် `triggers` တွေအကြောင်းကိုအခြေခံအားဖြင့်နားလည်သွားမယ်လို့ထင်ပါတယ်၊ project domain ပေါ်မူတည်ပြီး trigger တွေဟာ ယခုထက်ပိုပြီး complex ဖြစ်နိုင်ပါတယ်။ များသောအားဖြင့်လက်ရှိအသုံးပြုနေတဲ့ programming language နဲ့ framework တွေမှာ support ရှိတဲ့အတွက် `trigger` တွေသီးသန့်မဖန်တီးဘဲ `application` layer မှာတင် `before` & `after` hook တွေနဲ့ develop လုပ်နိုင်ပါတယ်။ သို့ပေမယ့်လည်း `trigger` တွေကိုအသုံးပြုမယ့်အခြေအနေတွေလည်းရှိနေနိုင်သေးပါတယ်။

Trigger တွေသုံးမယ်ဆို
-	Performance overhead မဖြစ်အောင်ဂရုစိုက်ပြီး တတ်နိုင်သမျှ lightweight ဖြစ်အောင်ဖန်တီးသင့်ပါတယ်။
-	Trigger တွေမှာပုံမှန် query တွေထက်အနည်းငယ်ဖတ်ရခက်နိုင်တဲ့အတွက် over complex မဖြစ်အောင်၊ ရေရှည်မှာ maintainability issues တွေမရှိအောင် review လုပ်ထားသင့်ပါတယ်။ သင့်တော်တဲ့ comments တွေနဲ့တစ်ပါတည်း document လုပ်ထားသင့်ပါတယ်။
-	Triggers တွေဆောက်ပြီးတာနဲ့ ကိုယ်လိုအပ်သလို trigger ဖြစ်ရဲ့လားဆိုတာကိုလည်း Test သေချာလုပ်ထားသင့်ပါတယ်၊ မဟုတ်ရင် `triggers` တွေကအတော်လေး risk ကြီးပါတယ်။

Conclude လုပ်ရမယ်ဆို `triggers` တွေကိုအသုံးပြုခြင်းဖြင့် DB ဘက်ခြမ်းမှာတင် automation tasks တွေဖန်တီးနိုင်တဲ့အတွက်အလွန်အသုံးဝင်နိုင်သလို best practices တွေမလိုက်နာရင်လည်း database အတွက် risk များတတ်နိုင်တဲ့အတွက်ကြောင့်ဂရုပြုပြီးဖန်တီးသင့်ပါတယ်။
