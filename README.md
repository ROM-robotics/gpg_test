### What is gpg
သူက data protection, signing တို့အတွက် public, private key အတွဲကို အသုံးပြုတဲ့ encryption စနစ်ပါပဲ။ သူ့မှာဆိုရင် public key encryption ကို သုံးတယ်။ ဆိုလိုတာက အခြားသူတွေရဲ့ public key ကို သုံးပြီး encryption လုပ်နိုင်တယ်။
pgp --> gpg

Cryptography မှာ mode နှစ်မျိုးရှိတယ်။ symmetric single key နဲ့ Asymmetric keys ပေါ့။ ဘာလဲဆိုတော့ symmetric single key ဆိုတာက sender ရော receiver ရော secret key တစ်ခုထဲကို သုံးပြီး encrypt/decrypt လုပ်ကြတာ။

Assymmetric ကတော့ public/private တစ်စုံနဲ့ အလုပ်လုပ်တယ်။ အဲ့ key နှစ်ခုက mathematics အရ ဆက်စပ်မှုရှိတယ်။ public/private key တွေနဲ့  encrypt လုပ်ပြီး private key ကို decrypt လုပ်ဖို့သုံးနိုင်တယ်။ 

private key ကို digital signatures နဲ့ authentication case တွေမှာလဲသုံးနိုင်သေးတယ်။
```
sudo apt install gpg
```
#### first need is you have gpg keys 2 keys, public, private keys ( all functionality )
```
gpg --full-generate-key
# key size ရွေးပေး 4096
# 0 --> never expire
# passphrase --> ghostman
# key ထုတ်ပြီးရင် gpg --gen-revoke လုပ်ပြီး certificate ကို လုံခြုံတဲ့နေရာမှာသိမ်းနိုင်တယ်။
```
#### lets check key
```
gpg --list-public-keys
# check private key
gpg --list-secret-keys
```
#### setup gpg key for encryption ( public key )
```
echo "this is hello" > hello
gpg --encrypt --output hello.gpg --recipient server01.psa1981@gmail.com hello
```
#### decryption ( private key )
```
rm hello
gpg --decrypt --output hello hello.gpg
cat hello
```

#### export ပြုလုပ်ခြင်း ( .asc format ဖြင့် armor version လည်း ထုတ်နိုင်ပါတယ်။ )
အခြားသူတွေက ကျတော်တို့ရဲ့ public key ကို သုံးပြီး encrypt လုပ်ပြီး ကျတော်တို့ဆီ data, email စတာတွေပို့ရင် ကျတော်တို့က private key ဖြင် decrypt လုပ်လို့ရမှာဖြစ်ပါတယ်။
```
gpg --list-public-keys
// pub rsa xxx FGDDFG334DFGFFDG
gpg --output yourpubkey.gpg --export FGDDFG334DFGFFDG
// gpg --export blabla@gmail.com > youpubkey.gpg
// gpg --export-secret-keys --armor > secret.gpg.key
// gpg --armor --export uid > yourpubkey.asc
// cat yourpubkey.asc

// xxd yourpubkey.gpg | less
```

#### import ပြုလုပ်ခြင်း
```
gpg --import key.gpg
... gpg: key 09232221
gpg --fingerprint 09232221 // check fingerprint
```

#### edit ပြုလုပ်ခြင်း
```
gpg --edit-key FGDDFG334DFGFFDG
# gpg> fbi
# gpg> sign
```

#### သင့်တော်ရာ keyserver တွေမှာ publish key ကို တင်ထားနိုင်ပါတယ်။
အဲ့ဒီ public key ရဲ့ fingerprint ကို email signature တွေ bussiness cards တွေမှာ သုံးနိင်ပါတယ်။
```
gpg --send-key uid
```

#### Keyring
သူကသော့ချိတ်တပ်တဲ့ကွင်းလို သော့တွေအများကြီးပါတဲ့ကောင်။
တနည်းအားဖြင့် ကျတော်တို့ရဲ့ public keys တွေနဲ့ imported လုပ်ထားတဲ့ public keys တွေပါတယ်ပေါ့။
 ```
 gpg --list-keys

 // list all keys with signatures
 gpg --list-sigs

 // delete a key
 gpg --delete-key uid
 ```
