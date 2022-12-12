openssl enc -ciphers -> lista algorytmow

## Zadanie 1

Wykonaj szyfrowanie ciągu znaków elJSK3h3aC8vTHZDSU4ydFpSdGNjMUZkZjhpckxEYm1yMm5uVW53OHQxND0K zapomocą algorytmu AES-256-ECB z użyciem podanego klucza. Klucz znajduje się w pliku ex2.1.key. Odpowiedź(zaszyfrowany tekst) zakoduj kodowaniem Base64. Klucz użyty podczas szyfrowania powinien być podawany z linii komend. Prawidłowa odpowiedź do zadania to:O4nGnWb8DPrNGEUISBwKmOJ5b/0H58kBFmowcpfOjFaE7+KiQi9vW/su9xHD/w4HQdM4CjOvQ1vlGsjuaCqTRA==

## Rozwiazanie (cos nie dziala tak jak trzeba)

1. openssl enc -aes-256-ecb -in somefile.txt -K heresomekey.key | base64

## Zadanie 2

Wykonaj deszyfrowanie pliku **ex2.2.enc** za pomocą algorytmu AES-256-ECB z użyciem podanego klucza: **8b5636e632bf3c0f2cb2becd9a1113a80198e7aa3e01dfda047abf26f1be2dd0**. Klucz powinien być podawany w linii komend. Wynikiem powinien być zrozumiały tekst.

## Rozwiazanie

1. openssl enc -d -aes-256-ecb -in ex2.2.enc -out ex2.2.dec -a -K 8b5636e632bf3c0f2cb2becd9a1113a80198e7aa3e01dfda047abf26f1be2dd0

2. cat ex2.2.dec | base64 -d

```
linux
```

## Zadanie 3

Wykonaj deszyfrowanie pliku **ex2.3.enc** za pomocą algorytmu **CAMELLIA-128-ECB** z użyciem podanego hasła: **g4X6ZiYokdM=**. Hasło powinno być podawane z pliku.

## Rozwiazanie (nie wiem nie dziala)

1. openssl enc -d -camellia-128-ecb -in ex2.3.enc -a -kfile ex2.3.key

```
bad magic number
```

## Zadanie 4

Wykonaj deszyfrowanie pliku **ex2.4.enc** za pomocą algorytmu **AES-256-CBC** z użyciem podanego hasła: **a961debab3d97475f919e70b00608508**, wiedząc, że funkcja generowania klucza to **PBKDF2**.

## Rozwiazanie

1. openssl enc -d -aes-256-cbc -in ex2.4.enc -a -kfile ex2.4.pass -pbkdf2 | base64 -d

```
/home/kali
```

1. openssl enc -d -aes-256-cbc -in ex2.4.enc -a -k a961debab3d97475f919e70b00608508 -pbkdf2 | base64 -d

```
/home/kali
```

## Zadanie 5

Wykonaj deszyfrowanie pliku **ex2.5.enc** za pomocą algorytmu 3DES z użyciem podanego klucza: **b8a6c5dab155f2120629d0fc68f15ff9**, wiedząc, że funkcja generowania klucza to PBKDF2.

## Rozwiazanie (dalo sie rozszyfrowac ale chyba zla tresc w tym zadaniu)

1. openssl enc -d -des-ede3 -in ex2.5.enc -a -K 06bd612eeb826eb5a400245e2c6afbb26c670c3b7c474be3

```
1e7mrYTzO1pKzw3BkydmLflzvVs=
```

2. cat ex2.5.dec

```
1e7mrYTzO1pKzw3BkydmLflzvVs=
```

## Zadanie 6

Wykonaj szyfrowanie pliku **ex.2.6.txt** za pomocą algorytmu **BLOWFISH-ECB** z użyciem klucza, który wygenerujesz za pomocą **OpenSSL rand**. Następnie wykonaj deszyfrowanie pliku, zapisując wynik deszyfrowania dopliku **dec2.6.txt**. Za pomocą polecenia **diff** lub **md5sum** sprawdź, czy pliki **ex.2.6.txt** oraz **dec2.6.txt** są identyczne.

## Rozwiazanie

1. openssl rand -hex 16 > ex2.6.key

```
c37158f66ed83e98b628629a0c4f4fa9
```

2. openssl enc -bf-ecb -in ex2.6.txt -out ex2.6.enc -K c37158f66ed83e98b628629a0c4f4fa9

```
O�:�iߒ����AUl���kC��
```

3. openssl enc -d -bf-ecb -in ex2.6.enc -out ex2.6.dec -K c37158f66ed83e98b628629a0c4f4fa9

```
V354GQB1OkuXlQ==
```

4. cat ex2.6.txt

```
V354GQB1OkuXlQ==
```

5. diff ex2.6.txt ex2.6.dec

```

```

## Zadanie 7

Wykonaj deszyfrowanie pliku **enc.2.7.txt** za pomocą algorytmu **AES-256-ECB** z użyciem podanego klucza: **b4c9c888546eac5587dc5f2e41f9c0c33601ce9a3fb080a5d4f73cada27ebeca**, algorytmu generowania klucza **PBKDF1** oraz wskazanej ilości **iteracji** algorytmu równej **356**.

## Rozwiazanie

1. openssl enc -d -aes-256-ecb -in ex2.7.enc -a -K b4c9c888546eac5587dc5f2e41f9c0c33601ce9a3fb080a5d4f73cada27ebeca -iter 356

```
3h8d8+opvd+cYs5i/MyTu0VGvnIEHpxxrwA+Qrdm4Ac=
```

2. cat ex.2.7.dec

```
3h8d8+opvd+cYs5i/MyTu0VGvnIEHpxxrwA+Qrdm4Ac=
```

## Zadanie 8

Wykonaj deszyfrowanie pliku **ex2.8.enc** za pomocą algorytmu **AES-256-CBC** z użyciem podanego hasła: **0311fab728530ebe**, algorytmu generowania klucza **PBKDF2** oraz wskazanej ilości iteracji algorytmu równej 41331.

## Rozwiazanie

```
co nie tak z tym zadaniem:<
```

## Zadanie 9

Ze strony kursu pobierz plik secured.zip. Plik ten jest zabezpieczony hasłem. Jest to jedno z najczęściej używanych przez użytkowników haseł. Za pomocą programu JohnTheRipper spróbuj złamać hasło, którym zaszyfrowany jest plik.

## Rozwiazanie

1. zip2john ex2.9.zip > secured.hash
2. john secured.hash --wordlist="rockyou.txt"

```
...cos tam
222222 ....
...costam
```

3. john secured.hash --show

```
ex2.9.zip/ex2.9.txt:222222:ex2.9.txt:ex2.9.zip::ex2.9.zip

1 password hash cracked, 0 left
```

4. w tym pliku w tym zipie

```
bsk 2022/2023
```

## Zadanie 10

Ze strony kursu pobierz plik secret.zip. Plik ten jest zabezpieczony hasłem. Wiedząc, że plik ten jest zabezpieczony hasłem o długości pomiędzy 5-6 znaków, i zawiera jedynie cyfry, za pomocą programu JohnTheRipper spróbuj złamać hasło, którym zaszyfrowany jest plik. Wygeneruj listę możliwych haseł za pomocą programu crunch.

## Rozwiazanie

1. crunch 5 6 0123456789 -o possible.txt

```
Crunch will now generate the following amount of data: 7600000 bytes
7 MB
0 GB
0 TB
0 PB
Crunch will now generate the following number of lines: 1100000

crunch: 100% completed generating output
```

2. zip2john ex2.10.zip > secured.hash
3. john secured.hash --wordlist="possible.txt"

```
Using default input encoding: UTF-8
Loaded 1 password hash (PKZIP [32/64])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
598494           (ex2.10.zip/ex2.10.txt)
1g 0:00:00:00 DONE (2022-12-11 17:55) 16.66g/s 11741Kp/s 11741Kc/s 11741KC/s 588128..604511
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```

4. co znajduje sie w tym pliku z haslem:

```
tajny tekst
```

## Zadanie 11

Wykonaj zadanie 9 za pomocą narzędzia **fcrackzip**.

## Rozwiazanie

1. fcrackzip -u -D -p rockyou.txt lab_files/ex2.9.zip

```
PASSWORD FOUND!!!!: pw == 222222
```

## Zadanie 12

Zidentyfikuj, jaki algorytm szyfrujący został wykorzystany do zaszyfrowania tekstu: **Z8CerTOLe1JlDKWfvDeifw==** przy pomocy klucza **a35febba42490abe**.

## Rozwiazanie

1. openssl list --cipher-commands | xargs -n1 > commands.txt

```
wszystkie algorytmy w jednej kolumnie w pliku
```

2. touch scrypt
3. chmode +x scrypt
4. nano scrypt

```
#!/bin/bash

while read algorithm; do
  echo "--------------"
  echo "$algorithm"
  openssl enc -d "-$algorithm" -in message.enc -a -K a35febba42490abe
  echo "--------------"
done < $1
```

## Zadanie 14

Ze strony kursu pobierz plik ex2.14.zip. Plik ten jest zabezpieczony hasłem. Spróbuj złamać hasło za pomocą narzędzia **hashcat**.

## Rozwiazanie

1. zip2john ex2.14.zip > secured.hash
2. nano secured.hash

```
$pkzip$1*2*2*0*14*8*b2a2b920*0*44*0*14*7f48*55743a29a0d2f17818316364261f0d4f641a1c7c*$/pkzip$

tak powinien wygladac
```

3. szukamy w internecie hashmode w hashcat dla tego hashu

```
-m 17210
```

4. hashcat -a -m 17210 secured.hash rockyou.txt

```
...
$pkzip$1*2*2*0*14*8*b2a2b920*0*44*0*14*7f48*55743a29a0d2f17818316364261f0d4f641a1c7c*$/pkzip$:bruceflea
...
```

5. w tym pliku znajduje sie:

```
treamae
```
