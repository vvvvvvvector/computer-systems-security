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

