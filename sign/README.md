### Signing
hash လုပ်ပေးတာက အခြား value အဖြစ်ပဲပြောင်းပေးတာ။ security ဘက်ကကြည့်ရင် သိပ်မထူးဘူး။ one way conversion တစ်ခုသက်သက်ပါပဲ။ data ကို မကာကွယ်နိုင်ဘူး။
```
sha1sum test.txt
```
အဲ့တော့ data ကို private key နဲ့ ကာကွယ်ရအောင်။ sign ထိုးမှာပေါ့။ ဒါဆို ကျတော့်ရဲ့ public key ရှိတဲ့ သူတွေသည် data ကို orginal ဟုတ်/ မဟုတ် verify လုပ်စစ်ဆေးနိုင်မှာပါ။ 

encrypt / decrypt မှာက  public key သည် encryption လုပ်နိုင်ပြီးတော့ private key ကိုင်ထားသူသည် အဲဒီဖိုင်ကို decrypt လုပ်နိုင်မှာဖြစ်ပါတယ်။
encrypt / decrypt နဲ့ signing မတူတာက private key သည် signing အတွက်ဖြစ်ပြီး public key သည် verify လုပ်ဖို့အတွက်ဖြစ်ပါတယ်။

#### signing test.txt with data
```
gpg --list-secret-keys
gpg --sign test.txt
// enter passphrase
cat test.txt.gpg
// gpg သည် data ကို enculapte လုပ်ပေးတယ်။ encrypt လုပ်မပေးပါဘူး။ ဒါကြောင့် xxd နဲ့ ကြည့်လို့ရနေပါတယ်။
xxd test.txt.gpg
```
#### အခြားသူသည် test.txt.gpg ကို ရယူပြီး verify လုပ်ပြီး data ကို extract ပြန်လုပ်ရမယ်။
```
gpg --verify test.txt.gpg
// ခုချိန်မှာ test.txt ကို ပြင်ရင်လဲ ဘာမှ ပြမှာမဟုတ်ပါဘူး။ ဘာလို့ဆိုတော့ data သည် test.txt.gpg ထဲမှာပဲရှိပြီး test.txt နဲ့ မပါက်သက်လို့ဖြစ်ပါတယ်။
```

#### signing test.txt without data
နောက်ဥပမာတစ်ခု ထပ်စမ်းကြည့်မယ်။
```
echo "hello" > hello
gpg --detach-sign hello
// hello.sig ဒီကောင်က signature ပဲပါတယ်။ data မပါဘူး။ ဒီကောင်နဲ့ မူရင်းဖိုင်သည် dir တစ်ခုထဲမှာရှိရပါမယ်။

// verify လုပ်ကြည့်မယ်။ ( Good signature လို့ပြပါမယ်။ )
gpg --verify hello.sig

// မူရင်းဖိုင်ကို နဲနဲပြင်ပြီး verify လုပ်မယ်။ ( Bad signature ဖြစ်သွားမယ်။ )
echo "world" >> hello
gpg --verify hello.sig

// ဒီဥပမာအရ ကျတော်တို့က မူရင်းဖိုင်ရော signature ဖိုင်ရော် user ဆီကို ပေးပို့ထားဖို့လိုတယ်။
```
