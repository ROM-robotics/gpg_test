### Linux Release

##### Release ဖိုင်
Release ဖိုင်တွေမှာ repository နဲ့ပက်သက်တဲ့ metadata တွေ repository မှာတင်ထားတဲ့ package indexes အားလုံးရဲ့ signature တွေပါဝင်ပါတယ်။
```
Origin: Ubuntu
Label: Ubuntu
Suite: kinetic
Version: 22.10
Codename: kinetic
Date: Thu, 20 Oct 2022 19:47:56 UTC
Architectures: amd64 arm64 armhf i386 ppc64el riscv64 s390x
Components: main restricted universe multiverse
Description: Ubuntu Kinetic 22.10
```
The Release file lists the index files for the distribution and their hashes (the index file listed are relative to Release file location).

##### InRelease ဖိုင်
InRelease ဖိုင်တွေသည် သူ့မှာ Inline gpg signature ပါရှိပြီး ကျန်အပိုင်းတွေကတော့ Release ဖိုင်တွေနဲ့ အတူတူပဲဖြစ်ပါတယ်။
ဆိုလိုတာက Release ဖိုင်တွေသည် Release.gpg ကို download ချဖို့လိုပါတယ်။ ပြိုင်တူ download  မဆွဲမိအောင် အသုံးပြုတယ်လို့ဆိုပါတယ်။
InRelease files are signed in-line while Release files should have an accompanying Release.gpg file.


#### Questions/ Ansters
##### Q: apt က ဘယ်လို download လုပ်သလဲ?
```
To download packages from a repository apt would download an InRelease or Release file from the $ARCHIVE_ROOT/dists/$DISTRIBUTION directory.
```
##### Q: မတူတဲ့စက်နှစ်ခုက apt repo တစ်ခုမှာ application တွေ host ထားလို့ရသလား?
```
မသိ
```
##### Q: private gpg key ကို စက်နှစ်ခုမှာ ထားလို့ရသလား?
```
ရပါတယ်။
gpg --import private.key
```

##### Q: How to release ?
```
https://www.digitalocean.com/community/tutorials/how-to-use-reprepro-for-a-secure-package-repository-on-ubuntu-14-04
```