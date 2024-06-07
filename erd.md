## Entity Relationship Diagram

ဒီ article series လေးရဲ့နောက်ဆုံးအပိုင်းအဖြစ် ERD (Entity Relationship Diagram) တစ်ခုတည်ဆောက်တဲ့ပုံစံလေးကိုပြောပြပေးသွားချင်ပါတယ်။

Database တစ်ခုကို design ချတော့မယ်ဆိုရင် ERD ကအရေးပါတဲ့အခန်းကဏ္ဍတစ်ခုအဖြစ်ပါဝင်ပါတယ်။ အကြမ်းဖျင်းရှင်းပြရမယ်ဆိုရင် ERD ဆိုတာ Database တစ်ခုမှာရှိနိုင်တဲ့ entities တွေရဲ့ ဆက်နွယ်မှုပုံစံကိုဖော်ပြဖို့အတွက်အဓိကအသုံးပြုတာဖြစ်ပါတယ်။ အောက်မှာ components တစ်ခုခြင်းဆီအတွက်အသေးစိတ်ထပ်ပြောပြပေးသွားပါမယ်။

#### Entities
Entities ဆိုတာကတော့ object တစ်ခု၊ solid concept တစ်ခုလို့သတ်မှတ်နိုင်ပါတယ်။ ဥပမာ E-commerce project တစ်ခုမှာဆိုရှိနိုင်တဲ့ entities တွေက `customer` `products` `orders` အစရှိသဖြင့်ပါဝင်နိုင်ပါတယ်။ 

#### Attributes
Entity ထဲမှာပါတဲ့ properties တွေကို attributes လို့သတ်မှတ်နိုင်ပါတယ်။ ဥပမာ `customer` entity မှာဆို `customer_id, name, email` အစရှိသဖြင့် attributes တွေပါဝင်နိုင်ပါတယ်။ 

#### Relationships
Entities တွေတစ်ခုနှင့်တစ်ခုဆက်နွယ်မှုကိုတော့ relationship လို့ခေါ်ဆိုပြီး relationship ပုံစံတွေကတော့ one-to-one, one-to-many, many-to-many ရှိတတ်ပါတယ်။

#### Primary Key
Entity တစ်ခုမှာ unique ဖြစ်နိုင်တဲ့ attribute တစ်ခု သို့ attributes အစုကို Primary key အဖြစ်သတ်မှတ်ပါတယ်။

#### Foreign Key
Entities တွေတစ်ခုနှင့်တစ်ခုချိတ်ဆက်ဖို့အတွက် အခြား entity ရဲ့ primary ကို reference လုပ်တဲ့နေရာမှာအသုံးပြုပါတယ်။

---

ERD နဲ့ပတ်သတ်လာလို့ components တစ်ခုခြင်းဆီကိုခွဲထုတ်ပြီးရှင်းပြလိုက်ပေမယ့် အားလုံးကိုရှေ့က articles တွေမှာဖော်ပြဖူးတဲ့အတွက်နားလည်ရလွယ်ကူမယ်လို့ထင်ပါတယ်။

ERD ရဲ့ components တွေကိုသိသွားပြီဆိုတော့တစ်လက်စတည်း ERD တစ်ခုဆွဲကြည့်သွားကြပါမယ်။ ERD တစ်ခုဆွဲတော့မယ်ဆို
1. အရင်ဆုံးပါဝင်တဲ့ entities တွေကိုသတ်မှတ်ဖို့လိုပါတယ်။ အထက်မှာကျနော်ပြောခဲ့တဲ့ e-commerce system တစ်ခုမှာဆို `customers, products, orders, order_details` တွေပါဝင်နိုင်ပါတယ်။ အခြားသော entities တွေလည်းအများကြီးရှိနိုင်ပါသေးတယ်။ ဒါပေမယ့်ဒီအပိုင်းမှာတော့ learning purpose ဖြစ်တဲ့အတွက်လက်ရှိ entities 4 ခုနဲ့ပဲဆွဲကြည့်ကြပါမယ်။
2. Entity တစ်ခုခြင်းဆီအတွက် attributes တွေသတ်မှတ်ကြပါမယ်။
	I.	`customers`
	- customer_id (Primary Key)
	- name
	- email
	- address
	
	II.	`products`
	- product_id (Primary Key)
	- name
	- price
	- stock_left
	
	III.	`orders`
	- order_id (Primary Key)
	- order_date
	- customer_id (Foreign Key)
	
	IV.	`order_details`
	- order_detail_id (Primary Key)
	- order_id (Foreign Key)
	- product _id (Foreign Key)
	- quantity

ကျနော်ကတော့ `order` နဲ့ `order_details` table ကိုခွဲပြီးတော့သိမ်းလေ့ရှိပါတယ်။ မိမိအဆင်ပြေသလိုတွဲပြီးသုံးမယ်ဆိုလည်းရပါတယ်။ Data amount များလာရင်တော့ခွဲပြီးသိမ်းတဲ့ပုံစံက `performance` အရရော `structure` အရရောပိုပြီးကောင်းစေပါတယ်။

3. Entities တွေရဲ့ဆက်နွယ်မှုပုံစံတွေကိုသတ်မှတ်ကြပါမယ်။ 
- Customer တစ်ယောက်ဟာ orders တွေအများကြီးတင်နိုင်တယ်။
- Order တစ်ခုမှာလည်း order_details တွေထပ်ရှိနိုင်တယ်။
- Product တစ်ခုကလည်း order_details တွေထဲရှိနိုင်ပါတယ်။

Entities, attributes တွေနဲ့ relationships တွေသတ်မှတ်ပြီးပြီဆိုမိမိနှစ်သက်ရာ drawing tool နဲ့ ERD ကိုဆွဲချနိုင်ပါပြီ။ အောက်ကပုံကတော့ကျနော်ဆွဲထားတဲ့ပုံလေးဖြစ်ပါတယ်။

![ERD](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/erd.png)

စနစ်ကျတဲ့ database တစ်လုံးတည်ဆောက်ရန်အတွက် ERD ဆွဲကြည့်ခြင်းဟာအလွန်အရေးပါပါတယ်။ Entities, attributes နဲ့ relationships တွေသတ်မှတ်ခြင်းအားဖြင့် တည်ဆောက်နေတဲ့ application ရဲ့လိုအပ်တဲ့ data structure ကိုထောက်ပံ့ပေးနိုင်မှာလည်းဖြစ်ပါတယ်။

