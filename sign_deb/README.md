- apt-key is depracated

#### ဖိုင်နှစ်ခုကို သိဖို့လိုပါတယ်။
- /etc/apt/sources.list.d/your_source.list
- /usr/share/keyrings/your_key.gpg
your_source.list ထဲမှာ url ရှိရမှာဖြစ်ပြီး your_key.gpg သည် ASCII-armored ဖြစ်ရပါမယ်။ binary ဖိုင်မဖြစ်ရပါ။ 
gpg key သည် binary ဖိုင်ဖြစ်နေရင် ascii ပြောင်းပေးပြီး keyrings/ ထဲထည့်ထားဖို့လိုပါတယ်။ 

#### sources.list.d
မှာထည့်ရမည့်ပုံစံက
TYPE [PATH] URL DISTRIBUTION COMPONENT 
ဖြစ်ပါတယ်။ နမူနာ ပြရရင်
```
deb [signed-by=/usr/share/keyrings/your_key.gpg] https://dl.google.com/linux/chrome/deb/ stable main
```
DISTRIBUTION ဆိုတာက debian release ရဲ့ codename သို့မဟုတ် စာသား phase တစ်ခုဖြစ်ပါတယ်။
COMPONENT ဆိုတာကတော့ debian package ရဲ့ categories ဖြစ်ပါတယ်။ 

#### Key ရယူဖို့
curl သို့မဟုတ် wget -O နဲ့ သုံးနိုင်တယ်။ ပြီးရင် pipe "|" နဲ့ gpg ထဲ ထည့်ပြီး dearmour လုပ် keyrings ထဲထည့်ရမှာဖြစ်ပါတယ်။ key မရှိဘဲ sources.list ထဲထည့်ထားရင် apt update လုပ်တဲ့အခါ error ပြပါမယ်။
```
curl https://xx/xx/your_key.pub | gpg -dearmor > /usr/share/keyrings/your_key.gpg
apt update
apt search your_software | grep your_software
// your_software-beta/stable 1.1.0 amd64
// your_software-stable/stable,now 1.1.0 amd64
// your_software-unstable/stable 1.1.0 amd64
apt install your_software-stable

```

google.com/linuxrepositories
