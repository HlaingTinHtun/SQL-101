# Environment Setup
SQL အသုံးပြုဖို့အတွက် MySQL DBMS ကိုအသုံးပြုသွားကြပါမယ်။ 

ဒီ article မှာတော့ MySQL ကို Window, macOS, Linux system တွေမှာ installation လုပ်ဖို့အတွက် 
screenshots တွေနဲ့တကွ guide လုပ်ပေးသွားပါမယ်။

## Window
MySQL installation url ကိုသွားလိုက်ပါမယ်။

https://dev.mysql.com/downloads/installer/

ကိုယ့် system နဲ့ကိုက်ညီတဲ့ download option ကိုရွေးပါ။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window1.png) <br/>

no thanks, just start my download ကိုနှိပ်ပြီး download ချပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window2.PNG) <br/>

exe file ကို double click လုပ်ပြီး installation ကိုစတင်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window3.PNG) <br/>

developer default ကိုရွေးပီး next နှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window4.png) <br/>


Path ကိုရွေးပြီး next နှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window5.png) <br/>

Execute ကိုနှိပ်ပြီး install စပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window6.png) <br/>

Next နှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window7.png) <br/>

Next နှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window8.png) <br/>

Setting ကိုစစ်ပြီး Next နှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window9.png) <br/>

legacy authentication method ကိုရွေးပြီး Next နှိပ်ပါမယ်။ အကယ်လို့ local environment မဟုတ်ဘဲ production environment တွေမှာဆိုရင်တော့ strong password option မျိုးကိုရွေးသင့်ပါတယ်။ local ကိုယ့်စက်ထဲမှာတော့ကြိုက်တာရွေးထည့်ထားနိုင်ပါတယ်။
![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window10.png) <br/>

Password ထည့်ပြီး Next နှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window11.png) <br/>

Next နှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window12.png) <br/>

Full access grant လုပ်ပြီး Next နှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window13.png) <br/>

Configuration တွေ applyလုပ်ဖို့အတွက် execute ကိုနှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window14.png) <br/>

Finish ကိုနှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window15.png) <br/>

Product configurationsတွေထပ်လုပ်ဖို့အတွက် next ကိုနှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window16.png) <br/>

Finish ကိုနှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window17.png) <br/>

Samples configuration အတွက် next ကိုနှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window18.png) <br/>

Username, password ထည့်ပြီး check ကိုနှိပ်ပါမယ်။ အဆင်ပြေတယ်ဆိုရင် next ကိုနှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window19.png) <br/>

Setup ပြီးပါပြီ၊ next ကိုနှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window20.png) <br/>
![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window21.png) <br/>

Finish ကိုနှိပ်ပါမယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window22.png) <br/>

Start menu ကနေ MySQL 8.0 command line client ဆိုပြီးရိုက်ရှာပြီးဖွင့်လိုက်ပါမယ်။

အရှေ့မှာထည့်ခဲ့တဲ့ password ကိုဖြည့်လိုက်မယ်ဆို MySQL အသုံးပြုနိုင်ပါပြီ။

show databases လို့ရိုက်ကြည့်ပြီး database list ကို checkup လုပ်ကြည့်ထားနိုင်ပါတယ်။

![Win Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/win/window23.png) <br/>


## macOS
Download link ကနေမှတစ်ဆင့် macOS ကိုရွေးလိုက်ပါ။

ကိုယ့်ရဲ့ macOS system ကိုအောက်ပါအတိုင်းစစ်နိုင်ပါတယ်။

apple icon ကနေမှ about this mac ကိုရွေး System Report ကိုနှိပ်လိုက်မယ်ဆို system report ကိုမြင်ရမှာဖြစ်ပါတယ်။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac1.png) <br/>

no thanks, just start my download ကိုနှိပ်ပြီး installer ကို download ချနိုင်ပါတယ်။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac2.png) <br/>

Double click လုပ်ပြီး installation ကိုစတင်ပါမယ်။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac3.png) <br/>

Allow ကိုနှိပ်ပါမယ်။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac4.png) <br/>

Continue ကိုနှိပ်ပါမယ်။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac5.png) <br/>

License agree လုပ်ပါမယ်။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac6.png) <br/>

use legacy password ကိုရွေးပြီး next ကိုနှိပ်ပါမယ်။ 
local environment ကိုယ့်စက်ထဲမှာတော့ကြိုက်တာရွေးနိုင်ပေမယ့် production environment လိုမျိုးမှာ strong password option မျိုးကိုရွေးသင့်ပါတယ်။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac7.png) <br/>

Password ရိုက်ထည့်ပါ။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac8.png) <br/>

Installation ပြီးပါပြီ၊ close ကိုနှိပ်ပါမယ်။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac9.png) <br/>

Terminal ဖွင့်ပြီး

`mysql –-version`

လို့ရိုက်ကြည့်လိုက်မယ်ဆို MySQL version ကိုမြင်ရပါမယ်။ 

`mysql -u root -p `

ရိုက်ပြီး MySQL ကို login ဝင်ကြည့်ပါမယ်။

Password ရိုက်ထည့်လိုက်မယ်ဆို MySQL အသုံးပြုနိုင်ပါပြီ။

![Mac Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/mac/mac10.png) <br/>

## Linux
Packages list ကိုအရင် update လုပ်ပါမယ်။

`sudo apt update`

![Linux Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/linux/linux1.PNG) <br/>

mysql-server သွင်းပါမယ်။

`sudo apt install mysql-server`

![Linux Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/linux/linux2.PNG) <br/>

သွင်းပြီးတဲ့အခါ MySQL version ကိုစစ်ကြည့်ပါမယ်။ version ပေါ်လာရင်သွင်းတာအောင်မြင်ပါတယ်။

`mysql --version`

![Linux Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/linux/linux3.PNG) <br/>


MySQL ကို login ဝင်ကြည့်ပါမယ်။ လောလောဆယ်တော့ password မရှိသေးတော့ ဒီအတိုင်းဝင်သွားပါလိမ့်မယ်။

`mysql -uroot`

![Linux Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/linux/linux4.PNG) <br/>

MySQL shell ထဲရောက်ပါပြီ။ password ထည့်ပါမယ်။

Password ကိုတော့ ‘password’ လို့ပဲပေးလိုက်ပါတယ်၊ ကြိုက်တာပေးလို့ရပါတယ်၊ ၈လုံးတော့ရှိဖို့လိုပါတယ်။

`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'password'`

![Linux Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/linux/linux5.PNG) <br/>

MySQL shell ထဲကနေ `exit` လို့ရိုက်ပြီးထွက်လိုက်ပါတယ်။

`mysql -u root -p`

လို့ရိုက်ပြီး password အသစ်နဲ့ Login ပြန်ဝင်ကြည့်ပါမယ်။

![Linux Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/linux/linux6.PNG) <br/>

`show databases` လို့ရိုက်ပြီး database list check လုပ်ကြည့်ပါမယ်။

![Linux Installation](https://raw.githubusercontent.com/HlaingTinHtun/SQL-101/main/assets/linux/linux7.PNG) <br/>
