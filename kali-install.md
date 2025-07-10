# Kali Linux ကို VirtualBox မှာ သွင်းနည်း
- Kali Linux ကို VirtualBox ပေါ်မှာ သွင်းဖို့အတွက် အဆင့်ဆင့်လမ်းညွှန်ချက်တွေကို အောက်မှာ ဖော်ပြထားပါတယ်။
- လိုအပ်သော အရာများ
    - VirtualBox (သွင်းပြီးဖြစ်ရမည်)
    - Kali Linux ISO File (Official Website မှ ဒေါင်းလုဒ်ရယူနိုင်သည်)
    - RAM (အနည်းဆုံး 2GB – 4GB ပေးရန် သင့်တော်သည်)
    - Disk Space (အနည်းဆုံး 20GB)

## Kali Linux VM အသစ်ဖန်တီးနည်း
  1. VirtualBox ကိုဖွင့်ပါ
  2. "New" ကိုနှိပ်ပြီး VM အသစ်ဖန်တီးပါ
       - Name: Kali Linux (သို့) ကိုယ်နှစ်သက်ရာ အမည်)
       - Type: Linux
       - Version: Debian (64-bit)
       - Next ကိုနှိပ်ပါ။
  4. Memory (RAM) သတ်မှတ်ပါ
       - အနည်းဆုံး 2048MB (2GB) ပေးပါ (PC မှာ RAM 8GB+ ရှိရင် 4GB ပေးလို့ရပါတယ်)
       - Next နှိပ်ပါ။
  6. Hard Disk ဖန်တီးပါ
       - "Create a virtual hard disk now" ကိုရွေးပြီး Create နှိပ်ပါ။
       - Hard Disk File Type: VDI (VirtualBox Disk Image)
       - Storage on Physical Hard Disk:
       - Dynamically allocated (ဒါက disk space ကို အလိုအလျောက် စီမံပေးမှာဖြစ်ပါတယ်)
       - File Location & Size:
       - အနည်းဆုံး 20GB သတ်မှတ်ပေးပါ (Kali Linux အတွက် 25GB-50GB ဆိုပိုကောင်းပါတယ်)
    - Create နှိပ်ပါ။

## Kali Linux ISO ကို VM မှာ ချိတ်ဆက်ပါ
  1. VM Settings ကိုဝင်ပါ
    - Kali Linux VM ကို Right-Click နှိပ်ပြီး Settings ကိုရွေးပါ။
  2. Storage ထဲမှာ ISO ချိတ်ပါ
     - Storage > Empty (Under Controller: IDE) ကိုရွေးပါ။
     - CD Icon (Optical Drive) ဘေးက ▼ ကိုနှိပ်ပြီး Choose a disk file... ကိုရွေးပါ။
     - Kali Linux ISO ဖိုင်ကိုရွေးပြီး Open နှိပ်ပါ။
     - OK နှိပ်ပြီး Settings ကိုပိတ်ပါ။

## Kali Linux Installation
  1. VM ကိုစတင်ပါ
    - Kali Linux VM ကိုရွေးပြီး Start နှိပ်ပါ။
  2. Boot Menu မှာ "Graphical Install" ရွေးပါ
    - Install (သို့) Graphical Install ကိုရွေးပါ (အကြံပြုချက်: Graphical Install က ပိုလွယ်ပါတယ်)
  3. Language & Region Settings
    - Language: English (သို့) ကိုယ်နှစ်သက်ရာ
    - Country: United States (သို့) Myanmar
    - Keymap: American English
  4. Network & Hostname
    - Hostname: kali (Default အတိုင်းထားလို့ရပါတယ်)
  5. Disk Partitioning
    - Partitioning Method: Guided - Use Entire Disk
    - Select Disk: SCSI3 (0,0,0) (sda) - XX.X GB
    - Partition Scheme: All files in one partition
    - Finish partitioning and write changes to disk ကိုရွေးပါ။
    - "Yes" နှိပ်ပြီး changes တွေကို confirm လုပ်ပါ။
  6. System Installation
    - GRUB Bootloader ကို Yes နှိပ်ပြီး install လုပ်ပါ။
    - Installation ပြီးသွားရင် Continue နှိပ်ပြီး VM ကို reboot လုပ်ပါ။
  7. Login & First Boot
    - Username: kali
    - Password: kali (Default Password)

## Post-Installation Setup
  1. Guest Additions သွင်းပါ (Optional)
     - VirtualBox Menu မှာ Devices > Insert Guest Additions CD Image ကိုနှိပ်ပါ။
     - Terminal ဖွင့်ပြီး:
       ```shell
        sudo apt update && sudo apt install -y build-essential dkms linux-headers-$(uname -r)
        sudo ./media/cdrom0/VBoxLinuxAdditions.run
        ```
     - Reboot လုပ်ပါ။
  3. Update & Upgrade
       ```bash
       sudo apt update && sudo apt upgrade -y
       ```

အဆင်ပြေပါစေ!

အခုဆိုရင် Kali Linux ကို VirtualBox မှာ အသုံးပြုနိုင်ပါပြီ။ Penetration Testing, Cybersecurity လေ့လာမယ့်သူတွေအတွက် အဆင်ပြေစေမယ့် Environment တစ်ခုရပါပြီ။
