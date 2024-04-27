## Transactions

Database ပေါ်ကို execute လုပ်သွားမယ့် operation တစ်ခု သို့ တစ်ခုထပ်ပိုတဲ့ operation sequence set တစ်ခုကို transaction လို့သတ်မှတ်နိုင်ပါတယ်။ Transaction တွေရဲ့ပုံစံက All or Nothing ဖြစ်ပါတယ်။ ဥပမာ TableA ကို Insert operation, TableB ကို Update operation လုပ်မယ့် transaction တစ်ခုရှိတယ်ဆိုပါစို့။ နှစ်ခုလုံးရဲ့ insert & update operation က success ဖြစ်ရမယ်။ Partial success, partial failure state ကိုလက်မခံဘူး၊ All or nothing result ပဲဖြစ်သွားမှာဖြစ်ပါတယ်။ ပိုပြီးနားလည်ရလွယ်အောင် အောက်မှာ query တွေ run ပြပြီး နမူနာတွေထပ်ပေးထားပါတယ်။

Query တွေမ run ခင်မှာ Transactions အကြောင်းရေးပြီဆိုမပါလို့မဖြစ်တဲ့ `ACID` property ကိုအရင်ထည့်ရေးချင်ပါတယ်။ Transaction ရယ်လို့ဖြစ်လာပြီဆို Atomicity, Consistency, Isolation, and Durability ဆိုတဲ့ key characteristic တွေပါဝင်ပါတယ်။

#### Atomicity
Transactions တွေက atomic ဖြစ်ပါတယ်။ ပါဝင်တဲ့ operation sequences တွေအားလုံး success ဖြစ်ရင်ဖြစ်၊ partial failure တစ်ခုပါတာနဲ့ အားလုံးဟာ roll back ပြန်ဖြစ်သွားပါမယ်။

#### Consistency
Before and after Transactions execution တွေမှာ data တွေကမှန်ကန်စွာကျန်ရှိနေခဲ့ရမယ်၊ partial failure တစ်ခုခုဖြစ်သွားရင် data consistency ကိုထိခိုက်နိုင်ပါတယ်၊ ဆိုတော့ somehow related with above atomicity property.

#### Isolation
Transaction တစ်ခုနဲ့တစ်ခုအပေါ်မှာမှီခိုဆက်စပ်ခြင်းရှိမနေဘဲနဲ့ concurrently execution လုပ်နိုင်မယ်။

#### Durability
Transaction execution (commit) လုပ်ပြီးသွားတာနဲ့ system failure, power outage တွေရှိသည့်တိုင်အောင် data တွေ persist ဖြစ်နေမယ်။

Geeksforgeeks က ဒီပုံလေးနဲ့ဆိုပိုပြီးမြင်သာသွားမယ်ထင်ပါတယ်။
![Credit : GeeksforGeeks](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/tran/tr8.png)

ACID properties ကိုအတိုချုပ်ရေးထားပေမယ့်အသေးစိတ်ကို ဒီမှာဝင်ဖတ်ကြည့်လို့ရပါတယ်။
https://www.geeksforgeeks.org/acid-properties-in-dbms/

### Sample Queries

Transaction query နမူနာလေးတွေစမ်းရေးကြည့်သွားပါမယ်။

Transaction တစ်ခုစဖို့အတွက် `BEGIN` ဆိုတဲ့ keyword ကိုသုံးသွားပါမယ်။
```
BEGIN;
INSERT INTO products VALUES(10, 'Energy Drink', 'Electronics', 20, 50, 'SupplierA');
```
`products` table ထဲကို data တစ်ကြောင်းသွင်းပါမယ်။ ရလဒ်ကိုအောက်ပါအတိုင်းကြည့်နိုင်ပါတယ်။

![tran](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/tran/tr1.png)

BEGIN နဲ့ transaction တစ်ခုစထားတာဖြစ်တဲ့အတွက် သွင်းလိုက်တဲ့ record ကို `ROLLBACK` လုပ်ပြီး `undo` ပြန်လုပ်နိုင်ပါတယ်။

![tran](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/tran/tr2.png)

ID 10 ပြန်ပျောက်သွားတာကိုမြင်ရပါမယ်။

သွင်းဖို့သေချာသွားပြီဆိုရင်တော့ `COMMIT ` ကိုသုံးပြီးတော့ finalize လုပ်လိုက်လို့ရပါပြီ။

![tran](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/tran/tr3.png)

UPDATE operation နှစ်ခုပါတဲ့ transaction တစ်ခု run ကြည့်ပါမယ်။
```
BEGIN;

UPDATE products SET price = price + 100 WHERE category = 'Electronics';
UPDATE products SET price = price + 100 WHERE category = 'Clothing';

COMMIT;
```
![tran](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/tran/tr4.png)

မ run ခင်က data တွေနဲ့ပြန်ယှဉ်ကြည့်မယ်ဆိုသက်ဆိုင်ရာ category တွေမှာ price 100 ထပ်ပေါင်းသွားတာကိုမြင်ရပါမယ်။

#### Transactions with Savepoints

Transaction ကို `SAVEPOINT ` တွေသုံးပြီးတော့လည်းအသုံးပြုနိုင်ပါတယ်။ မိမိလိုတဲ့ `SAVEPOINT` ကိုအောက်ပါအတိုင်း `ROLLBACK` လည်းလုပ်နိုင်ပါတယ်။

```
SAVEPOINT before_update;
UPDATE products SET price = price + 100 WHERE category = 'Electronics';

SAVEPOINT before_second_update;
UPDATE products SET price = price + 100 WHERE category = 'Clothing';

-- Rollback to the second savepoint
ROLLBACK TO before_second_update;

COMMIT;
```
![tran](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/tran/tr6.png)

ဒီ transaction မှာဆို `before_second_update`  အထိပြန် `ROLLBACK` သွားပြီး clothing category အတွက် effect ဖြစ်သွားတော့မှာမဟုတ်ပါဘူး။

![tran](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/tran/tr7.png)

### Tips when using transactions
Transactions တွေသုံးတဲ့အချိန်မှာ
-	တတ်နိုင်သလောက် simple ဖြစ်နိုင်ရင်ပိုကောင်းပါတယ်။
-	Long running transactions တွေဟာ concurrency နဲ့ performance issues ရှိနိုင်တာကိုသတိချပ်ထားရပါမယ်။
-	လိုအပ်သလို error handling exceptions တွေလည်းထည့်သုံးသင့်ပါတယ်။

Data integrity နဲ့ consistency ကောင်းဖို့အတွက် Transactions တွေကအရေးပါတဲ့အစိတ်အပိုင်းတစ်ခုဖြစ်ပါတယ်။ ဒီအပိုင်းနဲ့ပတ်သတ်လို့ထပ်လေ့လာစရာအများကြီးကျန်ပါသေးတယ်၊ သို့သော်ဒီနေရာကနေလမ်းစတစ်ခုရသွားဖို့မျှော်လင့်ပါတယ်။
