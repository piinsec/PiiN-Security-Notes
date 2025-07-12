# How to increase disk size of Kali Linux in Virtual box

## Step 1

Kali linux ကို Virtual box မှာသုံးနေရင်းနဲ့ storage မလောက်တဲ့ ပြဿနာကို ကြုံတွေ့နေတယ်ဆိုရင် ဒီနည်းလမ်းနဲ့ ဖြေရှင်းလို့ရပါတယ်။

- VirtualBox ရဲ့ File menu ထဲက Tools ကို ထဲက Virtual Media Manager ကိုရွေးလိုက်ပါ။

![kali1.png](https://github.com/piinsec/PiiN-Security-Notes/blob/main/Images/kali1.png)

- Hard disks tab အောက်ထဲ က ကိုယ် storage တိုးမဲ့ virtual disk ကို Double click နှိပ်လိုက်ပါ။ (eg: kali.vdi)
- အောက်က Attributes tab ထဲက size မှာ ကိုယ်လိုချင်သလောက်တိုးလို့ရပါပီ။

![kali2.png](https://github.com/piinsec/PiiN-Security-Notes/blob/main/Images/kali2.png)

## Step 2

- VirtualBox က Kali machine ကို start လုပ်လိုက်ပါ။
- Terminal က နေ “gparted” ကို ရိုက်လိုက်ပါ။
- ခုနက တိုးထားတဲ့ disk space က unallocated space ဖြစ်နေပါလိမ့်မယ်။

![kali3.png](https://github.com/piinsec/PiiN-Security-Notes/blob/main/Images/kali3.png)

- အဲ့ဒါကို new partition (သို့) ရှိပြီးသား partition ကို extend လုပ်လို့ရပါတယ်။
- ရှိပြီးသား /dev/sda1 ကို extend လုပ်ချင်တယ်ဆိုရင်တော့ /dev/sda2 အောက်မှာရှိတဲ့ linux-swap ကို အရင်ဖျက်ပြီး /dev/sda2 ကိုလည်းဖျက်ပစ်ဖို့လိုပါတယ်။
- linux-swap ကိုဖျက်ဖို့ right click နှိပ်ပြီး swapoff အရင်လုပ်ရပါတယ်။ပြီးမှ Delete လုပ်လိုက်ပါ။
- /dev/sda1 ကို resize လုပ်ပါ။ swap အတွက် 2GB လောက်ချန်ထားပါ။
- ကျန်တဲ့ 2GB ကို right click နှိပ် new ဆိုပြီး file system မှာ linux-swap ဆိုပြီးရွေးပေးလိုက်ပါ။
- အားလုံးပြီးသွားတဲ့အခါ tool bar က အမှန်ခြစ်လေးကိုနှိပ်ပေးလိုက်ပါ။
- အပေါ်က လုပ်ခဲ့တဲ့ အဆင့် တွေအားလုံး ကို ပေါင်းလုပ်သွားမှာဖြစ်ပါတယ်။
- Linux-swap ကို right click နှိပ်ပြီး swapon ပြန်လုပ်ပေးလိုက်ပါ။

![kali4.png](https://github.com/piinsec/PiiN-Security-Notes/blob/main/Images/kali4.png)

VirtualBox မှာ Kali linux ရဲ့ storage တိုးတဲ့ လုပ်ငန်းစဉ်ပြီးသွားပါပီ။
