## Logical & Comparison Operators
ဒီ article မှာတော့ Operators တွေအကြောင်းကိုရေးသွားမှာဖြစ်ပါတယ်။ Logical and Comparison operators တွေကိုများသောအားဖြင့် data ဆွဲထုတ်တဲ့ queries တွေမှာအသုံးပြုကြပါတယ်။ Operators ဆိုလို့ထူးထူးဆန်းဆန်းတော့မဟုတ်ဘူး၊ အများစုကို အရှေ့ကအပိုင်းတွေမှာတွေ့ပြီးသားဖြစ်ပါတယ်၊ section တစ်ခုအနေနဲ့သီးသန့်ဖော်ပြချင်တဲ့အတွက်သာရေးလိုက်ခြင်းဖြစ်ပါတယ်။ Easy going ဖြစ်တဲ့အတွက် သိပြီးသား query တွေအတွက်ကျနော် screenshots တွေမထည့်ပေးထားပါဘူး။

### Logical Operators
#### AND
`AND` keyword ကိုတော့တစ်ခုထက်ပိုတဲ့ conditions တွေကိုချိတ်ဆက်ပြီး data ဆွဲချင်တဲ့အချိန်မှာအသုံးပြုပါတယ်။ သုံးနေကျ `students` table က အသက် `20` ဖြစ်ပြီး `Computer Science` major ယူထားတဲ့ကျောင်းသားကိုထုတ်ကြည့်ရအောင်။

```
SELECT * FROM students
WHERE major = 'Computer Science'
AND age = 20;
```
#### OR 
`OR` ကတော့တစ်ခုထက်ပိုတဲ့ conditions တွေထဲကမှ တစ်ခုခုက valid ဖြစ်တယ်ဆိုရင် data ဆွဲထုတ်ချင်တဲ့နေရာမှာသုံးပါတယ်။ `students` table ထဲကနေ `major` က `Physics` `သို့မဟုတ် (OR)` `Mathematics` ဖြစ်တဲ့ကျောင်းသားတွေကိုဆွဲထုတ်ကြည့်ရအောင်။ 

```
SELECT * FROM students
WHERE major = 'Mathematics'
OR major = 'Physics';
```

#### NOT 

`NOT` ကိုတော့ ဒီ `condition` ကလွဲလို့ကျန်တဲ့ data ကအကုန်ပြပေးပါဆိုတဲ့အခြေအနေတွေမှာအသုံးပြုပါတယ်။ သိပ်မသုံးလောက်ဘူးထင်ရပေမယ့် အသုံးဝင်တဲ့ထဲမှာပါပါတယ်။ `students`table ထဲမှာ `Chemistry` major ကကျောင်းသားလွှဲလို့ကျန်တဲ့ကျောင်းသား data အကုန်ဆွဲထုတ်ချင်တယ်ဆိုပါစို့။
```
SELECT * FROM students
WHERE NOT major = 'Chemistry';
```

#### LIKE
 
`%` sign ကိုအသုံးပြုပြီး pattern ကိုက်ညီတဲ့ data တွေကိုဆွဲထုတ်လိုတဲ့အချိန်မှာအသုံးပြုပါတယ်၊ Search လုပ်တယ်လို့လဲခေါ်နိုင်ပါတယ်။ % sign နဲ့ပတ်သတ်တဲ့ pattern အသေးစိတ်ကိုအရှေ့ပိုင်းတွေမှာပြောခဲ့ပါတယ်၊ မေ့နေရင်ပြန်ရှာဖတ်နိုင်ပါတယ်။

`students` table ထဲက `name` ဆိုတဲ့ column မှာ `John` ဆိုတဲ့စာသားပါတဲ့ data တွေကိုဆွဲထုတ်ချင်တယ်ဆိုပါစို့။
```
SELECT * FROM students
WHERE name LIKE '%John%';
```
![OP1](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/op/op1.png)

---

#### NOT LIKE 

`LIKE` keyword ရဲ့ပြောင်းပြန်ပဲပေါ့။ LIKE ကကိုက်ညီတဲ့စာသားကိုပြတယ်၊ `NOT LIKE` ဆိုရင်တော့အဲ့ဒီ pattern (စာသား) မပါတဲ့ data တွေကိုပြမယ်။

`students` table ထဲမှာ `name` column က `Alice` ဆိုတဲ့စာသားမပါတဲ့ data တွေကိုလိုချင်တယ်ဆိုအောက်ကအတိုင်း `NOT LIKE` ကိုသုံးပြီးရေးနိုင်ပါတယ်။
```
SELECT * FROM students
WHERE name NOT LIKE '%Alice%';
```

![OP2](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/op/op2.png)

---

### Comparison Operators

#### Equal (=)

နှိုင်းယှဉ်ကြည့်ပြီး တူညီတဲ့တန်ဖိုးရှိတဲ့ data တွေကိုဆွဲထုတ်နိုင်ပါတယ်။
`students` table ထဲမှာ `age` ဆိုတဲ့ column က `21` ဖြစ်တဲ့ data တွေကိုလိုချင်တယ်ဆိုပါစို့။
```
SELECT * FROM students
WHERE age = 21;
```

#### Not Equal (<>)
`Equal =` နဲ့ပြောင်းပြန်ဖြစ်သွားပါမယ်။ နှိုင်းယှဉ်ကြည့်ပြီးမတူညီတဲ့ data ပေါ့။
`students` table ထဲမှာ `major` column က `Physics` မဟုတ်တဲ့ data တွေကိုလိုချင်တယ်ဆိုအောက်ကအတိုင်းရေးနိုင်ပါတယ်။
```
SELECT * FROM students
WHERE major <> 'Physics';
```

#### Greater Than (>), Less Than (<)

နှိုင်းယှဉ်ကြည့်ပြီး ကြီးသလား၊ ငယ်သလားဆိုတဲ့ condition ပေါ်မူတည်ပြီး data တွေဆွဲထုတ်နိုင်ပါတယ်။ 
`students` table ထဲမှာ `age` column ကို `22` ထက်ငယ်တဲ့ data တွေကိုလိုချင်တယ်။

```
SELECT * FROM students
WHERE age < 22;
```

`22`ထက်ကြီးတဲ့ data လိုချင်တယ်ဆိုရင်တော့ greater than `>` sign ကိုသုံးနိုင်ပါတယ်။

#### Greater Than or Equal To (>=), Less Than or Equal To (<=)
ကြီးပြီးတော့တူတယ်၊ ငယ်ပြီးတော့တူတယ် ဆိုတဲ့ conditions တွေရှိတဲ့အချိန်မှာ `>=, <=` signs တွေကိုသုံးပါတယ်။

 `students` table ထဲမှာ `age` column တန်ဖိုးက `20` ထက်ကြီးရမယ်၊ တူလည်းရတယ် ဆိုတဲ့အခြေအနေမှာအောက်က query လိုမျိုးအသုံးပြုနိုင်ပါတယ်။
```
SELECT * FROM students
WHERE age >= 20;
```
![OP3](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/queries/op/op3.png)

---
အထက်မှာဖော်ပြခဲ့တဲ့ Logical & comparison operators တွေဟာအခြေခံကျပြီး နေ့တဓူဝအသုံးပြုမယ့် queries တွေထဲပါဝင်ပါတယ်။ ရေးရတာလွယ်ကူပေမယ့် အသုံးဝင်တဲ့အရာတွေမို့လို့ သေချာလေးမိမိဘာသာထပ်ပြီးတော့လေ့ကျင့်ထားစေချင်ပါတယ်။

