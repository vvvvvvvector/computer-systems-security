**Sprawdzenie listy dostepnych alogorytmow szyfrowania for instance**

```
gpg --version
```

**_How to delete keyring with all keys(private and public)?_**

```
rm -r ~/.gnupg
```

**_How to show all public keys?_**

```
gpg --list-keys
```

**_How to show all private keys?_**

```
gpg --list-secret-keys
```

**How to export private key?**

```
gpg --output vzhdan.priv --armour --export-secret-keys D526670B
```

**How to export public key?**

```
gpg --output vzhdan.priv --armour --export D526670B
```

**How to sign key with another key(not my ultimate)?**
```
gpg --default-key {tu ten ktorym chce podpisac} --sign-key {tu ten ktory chce podpisac}
```

## Zadanie 1

Wykorzystując oprogramowanie **gpg**, wygeneruj zestaw kluczy (publiczny-prywatny) dla dowolnego użytkownikaprzy pomocy algorytmów RSA i DSA. (Pamiętaj, że algorytmu RSA możemy używać do szyfrowania/podpisywania, natomiast DSA do podpisywania.)

## Rozwiazanie

1. gpg --full-generate-key

## Zadanie 2

Wykorzystując oprogramowanie **gpg**, wygeneruj zestaw kluczy (publiczny-prywatny) dla **użytkownika BSK**(użyj przykładowych maili) przy pomocy algorytmu DSA. (Niech będzie to klucz bez określonego terminu ważności.)

## Rozwiazanie

1. gpg --full-generate-key

## Zadanie 3

Zmień datę wygaśnięcia klucza utworzonego w zad **2** na za 3 miesiące od dziś.

## Rozwiazanie

1. gpg --list-keys

```
szukamy id klucza ktory checemy zmodyfikowac
```

2. gpg --edit-key **_key-id_**

```
...
gpg> expire
Changing expiration time for the primary key.
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 3m
gpg> quit
```

## Zadanie 4

Wyświetl listę posiadanych kluczy, zarówno publicznych jak i prywatnych (czyli swój keyring, inaczej nazywany repozytorium kluczy programu gpg).

## Rozwiazanie

1. gpg --list-keys
2. gpg --list-secret-keys

## Zadanie 5

Usuń klucz użytkownika BSK (utworzony w zadaniu 2) ze swojego repozytorium kluczy.

## Rozwiazanie

1. gpg --list-keys --keyid-format SHORT

```
/home/vvvvvector/.gnupg/pubring.kbx
-----------------------------------
pub   rsa3072/FE8DB2D2<--here 2022-12-05 [SC]
      DAC16B81637B0CBCAAEBA196E92FBE30FE8DB2D2
uid         [ultimate] zadanie pierwsze (zadanie pierwsze komentarz) <zadanie.pierwsze@gmail.com>
sub   rsa3072/42DEC9C8 2022-12-05 [E]

pub   rsa3072/6E167287<--here 2022-12-05 [SC] [expires: 2023-03-05]
      4663FA1E631ECDC364BCCEB4D44CC43F6E167287
uid         [ultimate] student 1 <student1.bsk@wp.pl>
sub   rsa3072/DDC74AED 2022-12-05 [E]
```

2. gpg --delete-secret-key 6E167287
3. gpg --delete-key 6E167287

## Zadanie 6

Wyeksportuj swój klucz publiczny do pliku w postaci tekstowej(**--armour**). Podejrzyj informacje o kluczu.

## Rozwiazanie

1. gpg --output **_keyname.pub_** --armour --export **_key-id | user email_**

```
gpg --output vzhdan.pub --armour --export D526670B
```

2. gpg --show-key vzhdan.pub

```
pub   rsa3072 2022-12-05 [SC] [expires: 2023-01-04]
      6BB169DFB6E130F1AC46D3041507AC06D526670B
uid                      Viktar Zhdanovich (viktar zhdanovich keys pair) <viktor.zhdanovich@gmail.com>
sub   rsa3072 2022-12-05 [E] [expires: 2023-01-04]
```

## Zadanie 7

Wyeksportuj swój klucz publiczny do pliku w postaci binarnej. Podejrzyj informacje o kluczu.

## Rozwiazanie

1. gpg --output vzhdanbin.pub --export viktor.zhdanovich@gmail.com
2. gpg --show-key --keyid-format SHORT vzhdanbin.pub

```
pub   rsa3072/D526670B 2022-12-05 [SC] [expires: 2023-01-04]
      6BB169DFB6E130F1AC46D3041507AC06D526670B
uid                    Viktar Zhdanovich (viktar zhdanovich keys pair) <viktor.zhdanovich@gmail.com>
sub   rsa3072/84788D67 2022-12-05 [E] [expires: 2023-01-04]
```

## Zadanie 8

Z serwera kluczy **...(pgp.mit.edu)** zaimportuj klucz o ID **...(ashish a lot of keys)**. Sprawdź ponownie swój keyring. Podpisz zaimportowany klucz. (Poprzez podpisanie klucza innej osoby naszym kluczem zatwierdzamy jego autentyczność.)

## Rozwiazanie

1. gpg --keyserver pgp.mit.edu --recv-keys 57D03E31

```
gpg: key D09FC12B57D03E31: public key "vizuryapp <ashish.saxena@affle.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
```

2. gpg --list-keys --keyid-format SHORT

```
/home/vvvvvector/.gnupg/pubring.kbx
-----------------------------------
pub   rsa3072/D526670B 2022-12-05 [SC] [expires: 2023-01-04]
      6BB169DFB6E130F1AC46D3041507AC06D526670B
uid         [ultimate] Viktar Zhdanovich (viktar zhdanovich keys pair) <viktor.zhdanovich@gmail.com>
sub   rsa3072/84788D67 2022-12-05 [E] [expires: 2023-01-04]

pub   rsa3072/57D03E31 2022-09-23 [SC] [expires: 2024-09-22]
      17444D2B5E71F7EC396C4312D09FC12B57D03E31
uid         [ unknown] vizuryapp <ashish.saxena@affle.com>
sub   rsa3072/5D05C14E 2022-09-23 [E] [expires: 2024-09-22]
```

3. gpg --sign-key 57D03E31

```
pub  rsa3072/D09FC12B57D03E31
     created: 2022-09-23  expires: 2024-09-22  usage: SC
     trust: unknown       validity: unknown
sub  rsa3072/9FACC8745D05C14E
     created: 2022-09-23  expires: 2024-09-22  usage: E
[ unknown] (1). vizuryapp <ashish.saxena@affle.com>


pub  rsa3072/D09FC12B57D03E31
     created: 2022-09-23  expires: 2024-09-22  usage: SC
     trust: unknown       validity: unknown
 Primary key fingerprint: 1744 4D2B 5E71 F7EC 396C  4312 D09F C12B 57D0 3E31

     vizuryapp <ashish.saxena@affle.com>

This key is due to expire on 2024-09-22.
Are you sure that you want to sign this key with your
key "Viktar Zhdanovich (viktar zhdanovich keys pair) <viktor.zhdanovich@gmail.com>" (1507AC06D526670B)

Really sign? (y/N) y
```

## Zadanie 9

Wygeneruj losowy plik o wielkości **1MB** korzystając z pliku **/dev/urandom**. Za pomocą **gpg** zaszyfruj plik przy pomocy szyfrowania symetrycznego i algorytmu **AES-256**. Wynik zapisz do pliku w postaci tekstowej. (Oprogramowanie **gpg** umożliwia wykonanie szyfrowania symetrycznego, jak również asymetrycznego. W przypadku szyfrowania symetrycznego klucz szyfrujący/deszyfrujący jest generowany z podanego hasła.)

## Rozwiazanie

1. head -c 1048576 < /dev/urandom > file.txt
2. gpg --symmetric --armor --cipher-alg AES256 --output file.enc file.txt

```
...
Enter a passphrase...
...
```

## Zadanie 10

Za pomocą **gpg** zaszyfrowano pewien plik przy pomocy algorytmu **CAMELLIA128**. Wynik szyfrowania zapisano do pliku **file.enc**. Hasło wykorzystane podczas szyfrowania **hello**. Odszyfruj plik **file.enc**, wynik deszyfrowania zapisz do pliku **file.dec**.

## Rozwiazanie

1. echo -n "hello world" > file.txt
2. gpg --symmetric --armor --cipher-alg CAMELLIA128 --output file.enc file.txt

```
$cat file.enc

-----BEGIN PGP MESSAGE-----

jA0ECwMCK+GQ6GoO7MX/0kgB7N6L5sYrUeWWO+enDvu1w2ER31Vs5Z6vz4vamVXa
+7Zi6LNhS32nqWI/QOowWogKBT9TinATa91kR8IGCe/FR+rRyfvp8XQ=
=AL4V
-----END PGP MESSAGE-----
```

3. gpg --decrypt --output file.dec file.enc

```
gpg: CAMELLIA128.CFB encrypted data
gpg: encrypted with 1 passphrase
```

4. cat file.dec

```
hello world
```

## Zadanie 11

Wygeneruj 2 pary kluczy: dla użytkownika **Alice** (alice.bsk@wp.pl) i **Bob** (bob.bsk@wp.pl). Zakładając, że **Alice** chce wysłać zaszyfrowaną wiadomość do **Bob**, przygotuj plik **message.txt** z przykładową wiadomością, zaszyfruj go (jako **Alice**), a następnie odszyfruj (jako **Bob**). Zaszyfrowany tekst powinien być zakodowany **Base64**.

## Rozwiazanie

1. echo -n "hello bob and alice 2010" > message.txt
2. gpg --list-keys --keyid-format SHORT

```
/home/vvvvvector/.gnupg/pubring.kbx
-----------------------------------
pub   rsa3072/D526670B 2022-12-05 [SC] [expires: 2023-01-04]
      6BB169DFB6E130F1AC46D3041507AC06D526670B
uid         [ultimate] Viktar Zhdanovich (viktar zhdanovich keys pair) <viktor.zhdanovich@gmail.com>
sub   rsa3072/84788D67 2022-12-05 [E] [expires: 2023-01-04]

pub   rsa3072/57D03E31 2022-09-23 [SC] [expires: 2024-09-22]
      17444D2B5E71F7EC396C4312D09FC12B57D03E31
uid         [  full  ] vizuryapp <ashish.saxena@affle.com>
sub   rsa3072/5D05C14E 2022-09-23 [E] [expires: 2024-09-22]

pub   rsa3072/C997AE25 2022-12-05 [SC] [expires: 2024-12-04]
      AA2CAB2380CE4C6F2F3F9B2374B5F5ACC997AE25
uid         [ultimate] Bob 2007 <bob.bsk@wp.pl>
sub   rsa3072/47F377AA 2022-12-05 [E] [expires: 2024-12-04]

pub   rsa3072/795FF797 2022-12-05 [SC] [expires: 2024-12-04]
      F3E102E5108F22356EA20463EE184CE5795FF797
uid         [ultimate] Alice 2010 <alice.bsk@wp.pl>
sub   rsa3072/488D5759 2022-12-05 [E] [expires: 2024-12-04]
```

3. gpg --encrypt --recipient 795FF797 --armour --output message.enc message.txt
4. gpg --decrypt --output message.dec message.enc

## Zadanie 12

Ze strony kursu pobierz 2 pliki: **mallory.pub**(klucz publiczny użytkownika Mallory) oraz pliki **msg.sig**(podpisanyprzez niego plik) i **msg.txt**. Zweryfikuj podpis.

## Rozwiazanie

1. gpg --import mallory.pub (in my keyring)
2. gpg --sign-key 287F20A671B4150734073F831D7D4F7D2483325B(mallory.pub)
3. gpg --verify ex4.12.sig

```
gpg: Signature made Wed 02 Nov 2022 06:08:27 PM CET
gpg:                using RSA key 287F20A671B4150734073F831D7D4F7D2483325B
gpg: Good signature from "mallory.bsk@wp.pl" [full]
```

## Zadanie 13 (SPRAWDZAM INTEGRALNOSC)

Użytkownicy systemów linuksowych mają możliwość pobrania oprogramowania z repozytoriów przygotowanych dladanej dystrybucji systemu. Niekiedy jednak dodatkowe oprogramowanie można pobrać jedynie ze strony WWW. W takim przypadku, jaka jest pewność, że plik znajdujący się na stronie, został na niej w rzeczywistości umieszczonyprzez dewelopera aplikacji, a nie hakera? Niektórzy programiści podpisują swoje oprogramowanie przy pomocyrozwiązań PGP (takich jak np. GPG). Dzięki temu, jako użytkownicy, mamy możliwość weryfikacji integralności oprogramowania. Proces weryfikacji jest prosty, należy:<br/>
(a) Pobrać klucz publiczny autora oprogramowania<br/>(b) Sprawdzić fingerprint klucza<br/>(c) Zaimportować klucz do własnego keyringa<br/> (d) Pobrać sygnaturę dla ściąganego oprogramowania<br/> (e) Użyć klucza publicznego do zweryfikowania podpisu<br/>Pobierz oprogramowanie VeraCrypt i zweryfikuj jego integralność.

## Rozwiazanie

1. (a) wget https://www.idrix.fr/VeraCrypt/VeraCrypt_PGP_public_key.asc

```
mam teraz ten klucz publiczny u siebie na komputerze
```

2. (b) gpg --show-key --fingerprint VeraCrypt_PGP_public_key.asc

```
pub   rsa4096 2018-09-11 [SC]
      5069 A233 D55A 0EEB 174A  5FC3 821A CD02 680D 16DE
uid                      VeraCrypt Team (2018 - Supersedes Key ID=0x54DDD393) <veracrypt@idrix.fr>
sub   rsa4096 2018-09-11 [E]
sub   rsa4096 2018-09-11 [A]

P.S zgadza sie z tym co na stronie
```

3. gpg --import VeraCrypt_PGP_public_key.asc

```
gpg: key 821ACD02680D16DE: 1 signature not checked due to a missing key
gpg: key 821ACD02680D16DE: public key "VeraCrypt Team (2018 - Supersedes Key ID=0x54DDD393) <veracrypt@idrix.fr>" imported
gpg: Total number processed: 1
gpg:               imported: 1
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   2  trust: 0-, 0q, 0n, 0m, 0f, 1u
gpg: depth: 1  valid:   2  signed:   0  trust: 1-, 0q, 0n, 0m, 1f, 0u
gpg: next trustdb check due at 2023-01-04
```

4. wget https://launchpad.net/veracrypt/trunk/1.25.9/+download/veracrypt-console-1.25.9-Debian-11-amd64.deb

5. wget https://launchpad.net/veracrypt/trunk/1.25.9/+download/veracrypt-console-1.25.9-Debian-11-amd64.deb.sig

6. gpg --verify veracrypt-console-1.25.9-Debian-11-amd64.deb.sig

```
gpg: assuming signed data in 'veracrypt-console-1.25.9-Debian-11-amd64.deb'
gpg: Signature made Sun 20 Feb 2022 02:13:04 PM CET
gpg:                using RSA key 5069A233D55A0EEB174A5FC3821ACD02680D16DE
gpg: Good signature from "VeraCrypt Team (2018 - Supersedes Key ID=0x54DDD393) <veracrypt@idrix.fr>" [full]
```
