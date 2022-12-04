## Zadanie 1

Za pomocą narzędzia **rand** dostarczonego wraz z pakietem OpenSSL, wygeneruj 4 bitowe hasło i zakoduj go zapomocą Base64. Następnie, za pomocą narzędzia OpenSSL, wygeneruj hash MD5 tego hasła. Nie korzystaj z pomocniczych plików.

## Rozwiazanie

1. openssl rand 4 | base64\
   **output: X1RGUQ==**
2. opensll rand 4 | base64 | openssl dgst -md5\
   **output: MD5(stdin)= 5828a83f6b567d4035c4e182b8c5d48d**

## Zadanie 2

Korzystając z poleceń systemowych (np.**tr**,**head**,**cut**,**base64**) oraz pliku /dev/urandom wygeneruj bezpieczne hasło dla użytkownika (hasło ma mieć długość 16 znaków, nie może posiadać nie-alfanumerycznych znaków) a następnie wygeneruj, za pomocą narzędzia OpenSSL, funkcję skrótu MD5 dla wygenerowanego wcześniej hasła. Nie korzystaj z pomocniczych plików.

## Rozwiazanie

1. cat /dev/urandom | base64 | head -n 1 | tr -dc '[0-9A-Za-z]' | cut -c -16\
   **_-> head -n 1 - n pierwszych linii z pliku(1)_**\
   **_->cut -c -16 - okreslona liczba znakow(16)_**\
   **_->tr -dc '[0-9A-Za-z]' - usuwanie wszystkich znakow oprocz tych_**\
   **output: K5cSs1aXLnnt2J7v**
2. cat /dev/urandom | base64 | head -n 1 | tr -dc '[0-9A-Za-z]' | cut -c -16 | openssl dgst -md5\
   **output: MD5(stdin)= 57b8d745384127342f95660d97e1c9c2**

## Zadanie 3

Korzystając z narzędzia **crunch**, wygeneruj do pliku listę haseł składających się z samych cyfr o długości 3 znaków. Zapisz je do pliku. Za pomocą narzędzia OpenSSL wygeneruj funkcje skrótu SHA-1 dla wszystkich wygenerowanych haseł.

## Rozwiązanie

1. [crunch 3 3 0123456789 -o output.txt] or [crunch 3 3 -t %%% -o output.txt]<br/>
   **_->min-length max-length pattern_**
2. while read line;  
   while> do  
   while> echo "$line" | openssl dgst -sha1\
   while> done < output.txt

## Zadanie 4

Korzystając z narzędzia **crunch**, wygeneruj do pliku listę haseł o długości 5 znaków według wzoru, gdzie:

- pierwszy znak hasła to cyfra
- drugi znak hasła to mała literaa
- trzeci znak hasła to znak specjalny
- czwarty znak hasła to mała litera b
- piąty znak hasła to cyfra

## Rozwiazanie

1. crunch 5 5 -t %a^b% -o output.txt<br/>
   **_% - wszystkie cyfry<br/>^ - wszystkie znaki specjalne<br/>@ - wszystkie male litery_**

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
   **_->na stronie sa checksums - z nimi trzeba porownac_**

## Zadanie 9

Napisz skrypt w języku Python, w którym wygenerujesz hash MD5 dowolnego ciągu znaków podawanego jako argument wywołania skryptu. Sprawdź poprawność wygenerowanego hasha porównując go z wynikiem otrzymanym przy pomocy md5sum lub openssl.

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
   **_output: 5eb63bbbe01eeed093cb22bb8f5acdc3_**
2. echo -n "hello world" | openssl dgst -md5<br/>
   **_output: MD5(stdin)= 5eb63bbbe01eeed093cb22bb8f5acdc3_**

## Zadanie 10

Napisz skrypt w języku Python, w którym wygenerujesz hash SHA-1 dowolnego pliku podawanego jako argument wywołania skryptu. Sprawdź poprawność wygenerowanego hasha porównując go z wynikiem otrzymanym przy pomocy sha1sum lub openssl.

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
   **_output: 2c37eee0a27d96f0ed079e0f2c73b4809e153a7c_**
2. openssl dgst -sha1 hash.txt<br/>
   **_output: SHA1(hash.txt)= 2c37eee0a27d96f0ed079e0f2c73b4809e153a7c_**

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
   **_output: ripemd160_**

## Zadanie 12

Sprawdź, czy pliki **a.txt** oraz **b.txt** mają taką samą zawartość.

## Rozwiazanie

1. md5sum a.txt

```
65a7ad3ce593981059a3250600421319  a.txt
```

2. md5sum b.txt

```
5544cf5b584793733f5f61c9b049c225  b.txt
```

## Zadanie 13

Wykonaj zadanie 6 za pomocą narzędzia hashcat.

## Rozwiazanie

1. hashcat -a 0 -m 0 hash.txt rockyou.txt<br/>
   **_->-a 0 - atak slownikowy<br/>->-m 0 md5(hash-mode)_**
2. hashcat --show -m 0 hash.txt<br/>
   **_output: 8afa847f50a716e64932d995c8e7435a:princess_**

## Zadanie 14

Za pomocą słownika rockyou.txt oraz oprogramowania **JohnTheRipper** sprawdź jakie hasła mają użytkownicy u1 i u2 (plik z2.shadow). Hasła te mają charakter słów słownikowych.

## Rozwiazanie

1. john z2.shadow --wordlist="rockyou.txt"<br/>
   **_output:_**<br/>
   **...**<br/>
   **google (u1)**<br/>
   **onelove (u12)**<br/>
   **...**
2. john z2.shadow --show<br/>
   **_output:_**<br/>
   **u1:google:16026:0:99999:7:::**<br/>
   **u2:onelove:16026:0:99999:7:::**<br/>
   **2 password hashes cracked, 0 left**

## Zadanie 15

Użytkownik ma hasło (plik z5.shadow) składające się z 3 dowolnych znaków. Jakie to hasło? Do rozwiązaniazadania użyj oprogramowania JohnTheRipper.

## Rozwiazanie

1. sudo nano /etc/john/john.conf

```
[Incremental:Zadanie15]
File = $JOHN/utf8.chr
MinLen = 3
MaxLen = 3
CharCount = 196
```

2. john --incremental:Zadanie15 z5.shadow

```
Using default input encoding: UTF-8
Loaded 2 password hashes with 2 different salts (sha512crypt, crypt(3) $6$ [SHA512 128/128 ASIMD 2x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
123              (u9)
dhw              (u10)
2g 0:00:00:03 DONE (2022-12-04 15:58) 0.5780g/s 3255p/s 3403c/s 3403C/s aa1..28+
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```

3. john --show z5.shadow

```
u9:123:16026:0:99999:7:::
u10:dhw:16026:0:99999:7:::

2 password hashes cracked, 0 left
```

## Zadanie 16

Użytkownik ma hasło (plik z6.shadow) składające się z 5 dowolnych znaków. Jakie to hasło? Do rozwiązaniazadania użyj oprogramowania JohnTheRipper.

## Rozwiazanie

1. sudo nano /etc/john/john.conf

```
[Incremental:Zadanie16]
File = $JOHN/utf8.chr
MinLen = 5
MaxLen = 5
CharCount = 196
```

2. john --incremetal:Zadanie16 z6.shadow

3. john --show z6.shadow

```
u12:12345:17139:0:99999:7:::

1 password hash cracked, 1 left
```

## Zadanie 17

W pliku **z7.shadow** jest wiersz z hasłem użytkownika **user1**. Hasło ma charakter słownikowy, przy czym jest zapisane w taki sposób, że niektóre litery zamienione są na cyfry i tak: każde wystąpienie małego **a** zamienione jest na **@**, małego **i** na **1**, małego **e** na **3**. Ponadto hasło ma jeszcze na początku i na końcu znak **#(hash)**. Dorozwiązania zadania użyj oprogramowania JohnTheRipper

## Rozwiazanie

1. sudo nano /etc/john/john.conf

```
[List.Rules:Zadanie17]
^[#]si1sa@se3$[#]
```

2. john --wordlist="rockyou.txt" --rules=Zadanie17 z7.shadow

```
Warning: detected hash type "sha512crypt", but the string is also recognized as "HMAC-SHA256"
Use the "--format=HMAC-SHA256" option to force loading these as that type instead
Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 128/128 ASIMD 2x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
#p1n3@ppl3#      (user1)
1g 0:00:00:00 DONE (2022-12-04 16:23) 1.282g/s 1312p/s 1312c/s 1312C/s #hock3y#..#b3th@ny#
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```

3. john --show z7.shadow

## Zadanie 18

Wykonaj zadanie **1.14** za pomocą narzędzia **hashcat**.

## Rozwiazanie

1. hashcat -a 0 -m 1800 z2.shadow rockyou.txt

```
...
$6$jTfZyjJr$xzqXw3CFldUMA3JESiGMyE2N2jr9YE062otJsiwLSWn9yWc/n0J0UszKzia/3IFnPh6c7ZSUaahgnRP/cuAYJ.:google
$6$pmqtr7vg$j3NPrwFohrNYY3VTTVAlYdWja.pNnrce7nNbP.Uiq8WksCUkfFFtRJ3udehVjk8rVpanXxYFmlHHMzouP2Iyv.:onelove
...
```

2. hashcat -a0 -m 1800 z2.shadow --show

```
$6$jTfZyjJr$xzqXw3CFldUMA3JESiGMyE2N2jr9YE062otJsiwLSWn9yWc/n0J0UszKzia/3IFnPh6c7ZSUaahgnRP/cuAYJ.:google
$6$pmqtr7vg$j3NPrwFohrNYY3VTTVAlYdWja.pNnrce7nNbP.Uiq8WksCUkfFFtRJ3udehVjk8rVpanXxYFmlHHMzouP2Iyv.:onelove
```

## Zadanie 19

Wykonaj zadanie **1.15** za pomocą narzędzia **hashcat**.

## Rozwiazanie

1. hashcat -a 3 -m 1800 z5.shadow -i --increment-min=3 --increment-max=3<br/>
   **_-> -a 3 => brute-force_**

```
...
$6$3tVyi50r$TvxtOe7bNTtJE7QmYSWC7HTLlxxhaOXHgDi0fRceOBnsFpp0Cue/zkz21gO7wPEUimLCEhd33oWF7HD4JUns21:123
$6$FPMAFD62$GhrAXEUS359cBy3bh0.uY6VKqZx/Byx91M9wyFPLMYMTltSbfT9WU6sFtjUHMl8rTfijWeSLplFDkyY6YY9WE.:dhw
...
```

2. hashcat -a 3 -m 1800 z5.shadow -i --increment-min=3 --increment-max=3 --show

```
$6$3tVyi50r$TvxtOe7bNTtJE7QmYSWC7HTLlxxhaOXHgDi0fRceOBnsFpp0Cue/zkz21gO7wPEUimLCEhd33oWF7HD4JUns21:123
$6$FPMAFD62$GhrAXEUS359cBy3bh0.uY6VKqZx/Byx91M9wyFPLMYMTltSbfT9WU6sFtjUHMl8rTfijWeSLplFDkyY6YY9WE.:dhw
```

## Zadanie 20

Wykonaj zadanie **1.16** za pomocą narzędzia **hashcat**.

## Rozwiazanie

1. hashcat -a 3 -m 1800 z6.shadow -i --increment-min=5 --increment-max=5<br/>
   **_udaja sie znalezc tylko haslo: 12345_**

## Zadanie 21

Wykonaj zadanie **1.17** za pomocą narzędzia **hashcat**.

## Rozwiazanie

1. touch rules.txt
2. nano rules.txt

```
^# sa@ si1 se3 $#
```

3. hashcat -a 0 -m 1800 z7.shadow rockyou.txt -r rules.txt

```
...
$6$jZY/qU5z$3X7zLVRm8t.tLy46e0lNzL.pZ.3iP.w7huXCnzU6aIc2HAfV54Fv.Vx/kkHvG5V9sI2LH6kCVav6bClYjg0M2/:#p1n3@ppl3#
...
```
