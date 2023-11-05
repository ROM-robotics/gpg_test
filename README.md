pgp --> gpg

sudo apt install gpg

first need is you have gpg keys 2 keys, public, private keys ( all functionality )

$ gpg --full-generate-key

key size ရွေးပေး 4096
0 --> never expire


passphrase --> ghostman


lets check key
gpg --list-public-keys

check private key
gpg --list-secret-keys

setup gpg key for encryption
echo "this is hello" > hello

gpg --encrypt --output hello.gpg --recipient server01.psa1981@gmail.com hello

https://www.youtube.com/watch?v=5qg3QRRmJt0
