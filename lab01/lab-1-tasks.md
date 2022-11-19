## Zadanie 1

Za pomocą narzędzia **rand** dostarczonego wraz z pakietem OpenSSL, wygeneruj 4 bitowe hasło i zakoduj go zapomocą  Base64.  Następnie,  za  pomocą  narzędzia OpenSSL,  wygeneruj  hash  MD5  tego  hasła.  Nie  korzystaj  z pomocniczych plików.

## Rozwiazanie

1. openssl rand 4 | base64\
**output: X1RGUQ==**
2. opensll rand 4 | base64 | openssl dgst -md5\
**output: MD5(stdin)= 5828a83f6b567d4035c4e182b8c5d48d**

## Zadanie 2

Korzystając z poleceń systemowych (np.**tr**,**head**,**cut**,**base64**) oraz pliku /dev/urandom wygeneruj bezpieczne hasło  dla  użytkownika  (hasło  ma  mieć  długość  16  znaków,  nie  może  posiadać  nie-alfanumerycznych  znaków)  a następnie wygeneruj, za  pomocą  narzędzia OpenSSL, funkcję  skrótu MD5 dla wygenerowanego wcześniej hasła. Nie korzystaj z pomocniczych plików.

## Rozwiazanie

1. cat /dev/urandom | base64 | head -n 1 | tr -dc '[0-9A-Za-z]' | cut -c -16\
***-> head -n 1 - n pierwszych linii z pliku(1)***\
***->cut -c -16 - okreslona liczba znakow(16)***\
***->tr -dc '[0-9A-Za-z]' - usuwanie wszystkich znakow oprocz tych***\
**output: K5cSs1aXLnnt2J7v**
2. cat /dev/urandom | base64 | head -n 1 | tr -dc '[0-9A-Za-z]' | cut -c -16 | openssl dgst -md5\
**output: MD5(stdin)= 57b8d745384127342f95660d97e1c9c2**

## Zadanie 3 

Korzystając z narzędzia **crunch**, wygeneruj do pliku listę haseł składających się z samych cyfr o długości 3 znaków. Zapisz je do pliku. Za pomocą narzędzia OpenSSL wygeneruj funkcje skrótu SHA-1 dla wszystkich wygenerowanych haseł.

## Rozwiązanie

1. [crunch 3 3 0123456789 -o output.txt] or [crunch 3 3 -t %%% -o output.txt]<br/>
***->min-length max-length pattern***
2. while read line;                                                       
while> do                           
while> echo "$line" | openssl dgst -sha1\
while> done < output.txt   

## Zadanie 4

Korzystając z narzędzia **crunch**, wygeneruj do pliku listę haseł o długości 5 znaków według wzoru, gdzie:
* pierwszy znak hasła to cyfra
* drugi znak hasła to mała literaa
* trzeci znak hasła to znak specjalny
* czwarty znak hasła to mała litera b
* piąty znak hasła to cyfra

## Rozwiazanie

1. crunch 5 5 -t %a^b% -o output.txt<br/>
***% - wszystkie cyfry<br/>^ - wszystkie znaki specjalne<br/>@ - wszystkie male litery***


## Zadanie 6

Za pomocą słownika **rockyou.txt** oraz programu **JohnTheRipper**, spróbuj złamać hash MD5:8afa847f50a716e64932d995c8e7435a.

## Rozwiazanie

1. cp /usr/share/wordlists/rockyou.txt.gz .
2. gzip -d rockyou.txt.gz
3. john --format=raw-md5 --wordlist="rockyou.txt" hash.txt
4. john --show --format=raw-md5 hash.txt<br/>
**output: <br/>?:princess<br/><br/>1 password hash cracked, 0 left**

## Zadanie 7

Za pomocą słownika **rockyou.txt** oraz programu **JohnTheRipper**, spróbuj złamać hash SHA-256:437d9b521abe3c4102db90f7873cb4699cf9e38476c32b586cb786eb39eb6992.

## Rozwiazanie

1. john --format="Raw-SHA256" --wordlist="rockyou.txt" hash.txt<br/>
**output: i cant decrypt t!**

## Zadanie 8

Ze strony https://gparted.org/download.php pobierz plik gparted-live-1.3.1-1-amd64.iso. Za pomocą OpenSSL sprawdź integralność pobranego pliku. (Integralność polega na zapewnieniu, że przetwarzana informacjanie nie została w żaden sposób zmieniona. Zmiana taka może być przypadkowa (błąd podczas transmisji) jak i celowa(zmiana przez atakującego)).

## Rozwiazanie

1. openssl dgst -md5 gparted-live-1.3.1-1-amd64.iso<br/>
***->na stronie sa checksums - z nimi trzeba porownac***

## Zadanie 9

## Rozwiazanie

```
#!/usr/bin/env python3

import sys
import hashlib

h = hashlib.md5()
h.update(sys.argv[1].encode('utf-8'))
print(h.hexdigest())
```

1. ./main.py "hello world"<br/>
***output: 5eb63bbbe01eeed093cb22bb8f5acdc3***
2. echo -n "hello world" | openssl dgst -md5<br/>
***output: MD5(stdin)= 5eb63bbbe01eeed093cb22bb8f5acdc3***

## Zadanie 10

## Rozwiazanie

```
#!/usr/bin/env python3

import sys
import hashlib

filename = sys.argv[1]

with open(filename) as file:
   lines = file.readlines() # array of file lines

fcontent = ' '.join(lines) # my file content as string?

h = hashlib.sha1()
h.update(fcontent.encode('utf-8'))
print(h.hexdigest())
```

1. ./main.py hash.txt<br/>
***output: 2c37eee0a27d96f0ed079e0f2c73b4809e153a7c***
2. openssl dgst -sha1 hash.txt<br/>
***output: SHA1(hash.txt)= 2c37eee0a27d96f0ed079e0f2c73b4809e153a7c***

## Zadanie 11

Mając dany początkowy ciąg znaków **R3iSrSNmgU9SFHxVekUD**, który następnie został zahashowany, określ, jaka funkcja skrótu została wykorzystana do utworzenia hasha:**48cab4b54bef42fddaa6353c68a20b369f40026e**.

## Rozwiazanie

```
#!/usr/bin/env python3

import hashlib

string = 'R3iSrSNmgU9SFHxVekUD'.encode('utf-8')
hash = '48cab4b54bef42fddaa6353c68a20b369f40026e'

for algorithm in hashlib.algorithms_available:
   try: # try
      h = hashlib.new(algorithm)
      h.update(string)

      if hash == h.hexdigest():
         print(algorithm)

   except: # catch
      pass
```

1. ./main.py<br/>
***output: ripemd160***




