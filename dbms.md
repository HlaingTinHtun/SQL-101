# DBMS

သိမ်းဆည်းထားတဲ့ data တွေကို manage လုပ်ဖို့အတွက်ဆိုရင် DBMS ဆိုတဲ့အရာတွေကလိုအပ်လာပါတယ်။ 

DBMS အကြောင်းကိုရေးရင်းနဲ့တစ်လက်စတည်း database models အကြောင်းနဲ့ RDBMS အကြောင်းကိုရေးပေးသွားပါမယ်။

DBMS ဆိုတာက software တစ်ခုပါပဲ။ အဲ့ဒီ software ကိုအသုံးပြုပြီးတော့ database ထဲမှာရှိတဲ့ data တွေကို ထုတ်ယူ၊သိမ်းဆည်း၊ပြုပြင်တာတွေကိုလုပ်ဆောင်နိုင်ပါတယ်။ 
ပြောရမယ်ဆိုရင် အသုံးပြုသူနဲ့ database နှစ်ခုကြားထဲမှာ data တွေကို manipulate လုပ်ဖို့ interface တစ်ခုအနေနဲ့တည်ရှိနေပါတယ်။ 
User -> DBMS -> Database ပုံစံမျိုးပေါ့။ အသုံးပြုသူကနေတစ်ဆင့် လိုသလို data တွေကို manage လုပ်နိုင်ဖို့အတွက် DMBS ကို inputs (queries) တွေပေးဖို့လိုပါသေးတယ်။ 
ဒီအပိုင်းကိုတော့နောက်အပိုင်းတွေမှာထပ်ရေးသွားပါမယ်။

DBMS တွေကအမျိုးမျိုးရှိတယ်၊ ရွေးချယ်ထားတဲ့ database models ပေါ်မူတည်ပြီးတော့ DBMS ပုံစံတွေကလည်းကွဲပြားတယ်။ Database model ဆိုတာကတော့ database system တစ်ခုမှာ data တွေကိုဘယ်လို structure တွေနဲ့သိမ်းဆည်းမယ်၊ ချိတ်ဆက်မယ်ဆိုတာတွေကိုသတ်မှတ်ထားတဲ့ ပုံစံဖြစ်ပါတယ်။ ဥပမာ Model A ဆိုရင် Excel ထဲမှာ rows တွေ column တွေနဲ့မှတ်ပြီးသိမ်းမယ်၊ Model B ဆိုရင် Notepad ထဲမှာပဲ key value pair ပုံစံတွေနဲ့သိမ်းမယ် စသည်ဖြင့် model ပေါ်မူတည်ပြီး data တွေကိုစီမံခန့်ခွဲပုံကလည်း ကွဲပြောင်းသွားပါတယ်။
Database Models တွေအများကြီးထဲကမှအသုံးများတဲ့ models တွေကို list down လုပ်ပေးထားလိုက်ပါမယ်။

- Relational Model
- Hierarchical Model
- Network Model
- Object-Oriented Model
- Document Model
- Graph Model
စသည်ဖြင့်ရှိကြပါတယ်။ DB Engines ranking ဆိုပြီးရိုက်ရှာကြည့်လိုက်မယ်ဆိုရင်လည်းအသုံးများတဲ့ model တွေကိုတွေ့နိုင်ပါတယ်။

https://db-engines.com/en/ranking

ဒီ article series မှာကတော့ Structure Query Language (SQL) ကိုအသုံးပြုတဲ့ Relational Model အကြောင်းကိုပဲလေ့လာသွားကြပါမယ်။ 
Relational model ကိုအသုံးပြုတဲ့ RDBMS မှာလည်း provider ပေါ်မူတည်ပြီးတော့ DBMS software တွေကအနည်းနဲ့အများကွဲပြားသွားနိုင်ပါသေးတယ်။ 
သို့ပေမယ့် SQL oriented approach နဲ့သွားတာဖြစ်တဲ့အတွက်အများကြီးပြောင်းလဲသွားတာတော့မရှိပါဘူး။
ဥပမာ
- Oracle Database
- MySQL
- PostgreSQL
- Microsoft SQL Server
စသည်ဖြင့်ပေါ့။ အားလုံးက RDBMS ဖြစ်ပေမယ့် company ပေါ်မူတည်ပြီးအသုံးပြုပုံအနည်းငယ်ကွာဟသွားနိုင်ပါတယ်။

Relational Model တွေက data တွေကိုဘယ်လိုသိမ်းဆည်းလဲဆိုတာနဲ့ပြန်ဆက်ရအောင်။ 

သူတို့က data တွေကို table ပုံစံ၊ row , column နှစ်ခုပါတဲ့ two dimensional structures နဲ့သိမ်းဆည်းပါတယ်။ 
table တစ်လုံးခြင်းဆီတိုင်းမှာ rows (records) , columns (fields) ပုံစံတွေနဲ့သက်ဆိုင်ရာ data တွေကိုထည့်သွင်းသိမ်းဆည်းပါတယ်။ 
row (record) တစ်ခုခြင်းဆီတိုင်းကို unique ဖြစ်စေဖို့ (row အချင်းချင်း duplicate/conflict) မဖြစ်စေရန် primary key သတ်မှတ်ပေးပြီးတော့ table တစ်လုံးက field တစ်ခုကနေပြီးတော့ နောက် table တစ်လုံးက primary key ကိုလှမ်း reference လုပ်ချင်တဲ့အချိန်မှာ foreign key အဖြစ်သတ်မှတ်တာမျိုးတွေလည်းရှိပါတယ်။

လောလောဆယ်တော့နည်းနည်းရှုပ်နေနိုင်သေးပေမယ့် နောက်လာမယ့်အပိုင်းတွေမှာ query တွေရေးကြည့်တဲ့အခါလွယ်ကူသွားပါလိမ့်မယ်။
