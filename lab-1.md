### Funkcja haszuaca MD5 [nie uzywa sie]

1. md5sum
2. echo "Ala ma kota" | md5sum => 59e4f8f04c0571616989ce77e669cfb9
3. echo "Ala ma kota" | hexdump -C  => 00000000  41 6c 61 20 6d 61 20 6b  6f 74 61 0a  |Ala ma kota.| ...and so on


### Funkcja haszujaca SHA [secure hash algorithm]
1. echo -n "Ala ma kota" | sha256sum => 124bfb6284d82f3b1105f88e3e7a0ee02d0e525193413c05b75041917022cd6e

### Kodowanie transportowe [base64] (dla transporu danych binarnych; transformacja do widomosci tekstowej)
1. echo -n "a" | base64 => YQ==
2. echo -n "ala ma kota" | base64 | base64 -d => ala ma kota

### Biblioteka OpenSSL
1. openssl dgst -list => spis dostepnych funkcji haszujacych
2. echo -n "ala ma kota" | openssl dgst -sha3-256 => 804a8f1f4c9958f43e5f82d6af81df1568ac25d6abdbcc26004623089e795a00
3. openssl rand 10 => 10 losowych bajtow
4. openssl rand 12 | base64 => np tak mozna generowac hasla
5. cat /dev/urandom | head -c 20 => 20 losowych znakow
6. dd bs=20 count=1 if=/dev/urandom of=file.txt => 20 losowych bajtow z /dev/urandom do pliku file.txt

