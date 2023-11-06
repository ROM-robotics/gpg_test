## ros2 package release

### Developer Guide

####  pre-build ပြုလုပ်နည်း
```
$ sudo apt install -y python3-bloom python3-rosdep fakeroot dh-make
$ cd your_workspace
$ colcon build
$ source install/setup.bash
$ sudo rosdep init
$ cd your_package
$ bloom-generate rosdebian

# you will get debian directory and rules file
# generate .deb package
$ fakeroot debian/rules binary

# You sholud check up one directory and there will exist *.deb file
```

#### ခုဆိုရင် local host ပေါ်မှာ Install/ Remove ပြုလုပ်နိုင်ပါပြီ။
```
# install
$ sudo dpkg -i ros-distro-your-pkg.deb
# NOW YOU CAN TEST ros2 run xxx xxx or ros2 launch xxx xxx
# where
$ sudo dpkg -L ros-distro-your-pkg
# remove
$ sudo dpkg -P ros-distro-your-pkg
```

#### gpg key ထုတ်လုပ်ခြင်း
```
# generate private/public key pair
$ gpg --full-generate-key

# check your private key
$ gpg --export-secret-key "blabla@gmail.com"

# export your private key
# gpg --export-secret-key "blabla@gmail.com" > private.asc

# export your public key
$ gpg --armor -export "blabla@gmail.com" > romrobot-public.gpg

# install public key on local host
# $ apt-key add romrobot-public.gpg
```

#### In your github repo's deb directory
```
$ dpkg-scanpackages --multiversion . > Packages
$ gzip -k -f Packages

# Creating Release, Release.gpg and InRelease files
$ apt-ftparchive release . > Release
$ gpg --default-key "romrobotics@gmail.com" -abs -o - Release > Release.gpg
$ gpg --default-key "romrobotics@gmail.com" --clearsign -o - Release > InRelease

# Creating rom_robot.list
$ echo "deb [signed-by=/etc/apt/trusted.gpg.d/romrobot-public.gpg] https://rom-robotics.github.io/romrobotics.repo/dists ./" > rom_robotics.list
```
ပြီးရင် commit ထုတ်ပြီး push တင်ပြီးတာနဲ့ အသုံးပြုလို့ရပါပြီ။

#### နောက်ထပ် Debian packages အသစ်တွေထပ်ထည့်မည့် developer တွေကတော့
debian package တွေ upload လုပ်ပါ။
```
# Packages & Packages.gz
$ dpkg-scanpackages --multiversion . > Packages
$ gzip -k -f Packages

# Release, Release.gpg & InRelease
$ apt-ftparchive release . > Release
$ gpg --default-key "${EMAIL}" -abs -o - Release > Release.gpg
$ gpg --default-key "${EMAIL}" --clearsign -o - Release > InRelease

# Commit & push
$ git add -A
$ git commit -m update
$ git push
```

































