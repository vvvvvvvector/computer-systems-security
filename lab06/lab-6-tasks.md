## Zadanie 1 (LICZBA LINII W PLIKU)

Ze strony kursu pobierz plik syslog.txt. To plik z rejestrem zdarzeń (log), które wystąpiły w systemie. Z pliku syslog1.txt wyświetl wiersz o numerze równym liczbie linii tego pliku.

## Rozwiazanie

1. cat syslog1.txt | wc -l

```
24891
```

## Zadanie 2

Ze strony kursu pobierz plik syslog1.txt. To plik z rejestrem zdarzeń (log), które wystąpiły w systemie. Z pliku syslog1.txt wyświetl wpis (linię) dodany 3 października o godzinie 10:39:01.

## Rozwiazanie

1. cat syslog1.txt | grep "Oct 3 10:39:01"

```
Oct  3 10:39:01 kali CRON[2266]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
```

## Zadanie 3

Ze strony kursu pobierz plik access_log1.txt. To plik z przykładowymi żądaniami wysłanymi do serwera Apache. Oblicz, ile żądań wysłano do serwera z adresu IP 127.0.0.1. Wynikiem powinna być pojedyncza liczba.

## Rozwiazanie

1. cat access_log1.txt | grep 127.0.0.1 | wc -l

```
8
```

1. grep -c 127.0.0.1 access_log1.txt

```
8
```

## Zadanie 4 (LICZBA SYMBOLI [A, B])

Ze strony kursu pobierz plik syslog1.txt. To plik z rejestrem zdarzeń (log), które wystąpiły w systemie. Z pliku syslog1.txt wyświetl wpis (linię) który ma więcej niż 150, ale mniej niż 180 znaków (na końcu linii).

## Rozwiazanie

1. cat syslog1.txt | grep -E "^.{150,180}$"

```
...
Oct  5 19:50:58 kali NetworkManager[514]: <info>  [1633456258.0346] device (eth0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Oct  5 19:51:03 kali usbmuxd[12856]: [19:51:03.076][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
Oct  5 19:51:08 kali usbmuxd[12856]: [19:51:08.076][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
Oct  5 19:51:13 kali usbmuxd[12856]: [19:51:13.074][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
```

## Zadanie 5 (DOKLADNIE N-RAZY ZNAKOW)

Ze strony kursu pobierz plik syslog1.txt. To plik z rejestrem zdarzeń (log), które wystąpiły w systemie. Z pliku syslog1.txt wyświetl wpis (linię) który ma dokładnie 360 znaków.

## Rozwiazanie

1. cat syslog1.txt | grep -E "^.{360,360}$"

```
nie ma w tym pliku takich linii
```

## Zadanie 6

Ze strony kursu pobierz plik syslog1.txt. To plik z rejestrem zdarzeń (log), które wystąpiły w systemie. Z pliku syslog1.txt wyświetl wpis (linię) który został dodany między 19:00, a 19:02 (na początku linii).

## Rozwiazanie

1. cat syslog1.txt | grep -E "19:0[0-1]:[0-5][0-9]"

```
Sep 29 19:00:14 kali dbus-daemon[476]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.253' (uid=1000 pid=39047 comm="x-www-browser ")
Sep 29 19:00:14 kali systemd[1]: Starting Hostname Service...
Sep 29 19:00:14 kali dbus-daemon[476]: [system] Successfully activated service 'org.freedesktop.hostname1'
Sep 29 19:00:14 kali systemd[1]: Started Hostname Service.
Sep 29 19:00:24 kali kernel: [21372.394359] ieee80211 phy0: brcmf_psm_watchdog_notify: PSM's watchdog has fired!
Sep 29 19:01:09 kali systemd[1]: systemd-hostnamed.service: Succeeded.
Oct  5 19:00:00 kali usbmuxd[9003]: [19:00:00.072][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
Oct  5 19:00:05 kali usbmuxd[9003]: [19:00:05.073][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
Oct  5 19:00:10 kali usbmuxd[9003]: [19:00:10.074][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
Oct  5 19:00:15 kali usbmuxd[9003]: [19:00:15.074][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
Oct  5 19:00:20 kali usbmuxd[9003]: [19:00:20.073][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
Oct  5 19:00:25 kali usbmuxd[9003]: [19:00:25.072][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
Oct  5 19:00:27 kali kernel: [14811.669108] apple-mfi-fastcharge 3-1: USB disconnect, device number 50
...
Oct  5 19:01:49 kali dbus-daemon[513]: [system] Activating via systemd: service name='org.freedesktop.Avahi' unit='dbus-org.freedesktop.Avahi.service' requested by ':1.241' (uid=132 pid=9168 comm="/usr/libexec/colord-sane ")
Oct  5 19:01:49 kali dbus-daemon[513]: [system] Activation via systemd failed for unit 'dbus-org.freedesktop.Avahi.service': Unit dbus-org.freedesktop.Avahi.service not found.
Oct  5 19:01:52 kali ModemManager[591]: <info>  [base-manager] couldn't check support for device '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/0000:02:02.0/0000:39:00.0/usb3/3-1': not supported by any plugin
Oct  5 19:01:55 kali usbmuxd[9180]: [19:01:55.079][1] ERROR: Failed to read '/var/lib/lockdown/00008030-001E11222E13402E.plist': No such file or directory
```

## Zadanie 7 (ZNALESC JAKIES STRINGI W LINIACH W PLIKU)

Ze strony kursu pobierz plik syslog2.txt. To plik z rejestrem zdarzeń (log), które wystąpiły w systemie. Z pliku syslog2.txt wyświetl wpis (linię) który dotyczy usługi MySQL lub Postfix.

## Rozwiazanie

1. cat syslog2.txt | grep "mysql\|postfix"
1. cat syslog2.txt | grep -e "mysql" -e "postfix" (chyba to samo)

## Zadanie 8 (.\* - to znaczy wszystko)

Ze strony kursu pobierz plik auth1.log. To plik z rejestrem zdarzeń (log), które dotyczą logowania przez SSH. Jest wśród nich również wpis o nieudanej próbie logowania. Z pliku auth1.log wyświetl wpis (linię) który dotyczy nieudanego logowania SSH.

## Rozwiazanie

1. cat auth1.log | grep -E "sshd.\*invalid"

```
Feb  4 12:05:33 ip-172-31-1-163 sshd[5322]: input_userauth_request: invalid user gpadmin [preauth]
Feb  4 12:05:37 ip-172-31-1-163 sshd[5326]: input_userauth_request: invalid user prueba [preauth]
Feb  4 12:05:40 ip-172-31-1-163 sshd[5328]: input_userauth_request: invalid user ts3server [preauth]
Feb  4 12:05:42 ip-172-31-1-163 sshd[5330]: input_userauth_request: invalid user demo [preauth]
Feb  4 14:44:21 ip-172-31-1-163 sshd[5618]: input_userauth_request: invalid user ubutu [preauth]
```

## Zadanie 9

Ze strony kursu pobierz plik auth1.log. To plik z rejestrem zdarzeń (log), które dotyczą logowania przez SSH. Z pliku auth1.log wyświetl wpis (linię) która zawiera udaną próbę logowania (co oznacza, że intruz uzyskał dostęp do serwera).

## Rozwiazanie

1. cat auth1.log | grep "session opened"

```
...
Feb  4 13:20:02 ip-172-31-1-163 CRON[5472]: pam_unix(cron:session): session opened for user smmsp by (uid=0)
Feb  4 13:40:01 ip-172-31-1-163 CRON[5506]: pam_unix(cron:session): session opened for user smmsp by (uid=0)
Feb  4 14:00:01 ip-172-31-1-163 CRON[5527]: pam_unix(cron:session): session opened for user smmsp by (uid=0)
Feb  4 14:17:01 ip-172-31-1-163 CRON[5561]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb  4 14:20:01 ip-172-31-1-163 CRON[5564]: pam_unix(cron:session): session opened for user smmsp by (uid=0)
Feb  4 14:40:01 ip-172-31-1-163 CRON[5598]: pam_unix(cron:session): session opened for user smmsp by (uid=0)
Feb  4 14:44:38 ip-172-31-1-163 sshd[5620]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
Feb  4 14:45:42 ip-172-31-1-163 sudo: pam_unix(sudo:session): session opened for user root by ubuntu(uid=0)
```

## Zadanie 10 (grep -v slowo -> USUWA Z WYSWIETLEN)

Z udanych prób logowania SSH (rozwiązanie zadania 6.9) odfiltruj próby logowania użytkownika root (usuń z wyświetleń).

## Rozwiazanie

1. cat auth1.log | grep "session opened" | grep -v root

## Zadanie 11 (USUWAN Z WYSWIETLEN LINII W KTORYCH WYSTEPUJA ROOT LUB SMMSP)

Z udanych prób logowania SSH (rozwiązanie zadania 6.9) odfiltruj próby logowania użytkownika root oraz użytkownika smmsp (usuń z wyświetleń).

## Rozwiazanie

1. cat auth1.log | grep "session opened" | grep -v "root\|smmsp"

```
Jan 11 01:56:37 ip-172-31-1-163 sshd[1303]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
Jan 11 12:07:15 ip-172-31-1-163 sshd[2434]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
Jan 13 02:31:48 ip-172-31-1-163 sshd[4944]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
Jan 16 16:19:25 ip-172-31-1-163 sshd[11978]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
Feb  1 13:23:24 ip-172-31-1-163 sshd[26207]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
Feb  1 20:24:21 ip-172-31-1-163 sshd[29424]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
Feb  4 14:44:38 ip-172-31-1-163 sshd[5620]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
```

1. cat auth1.log | grep "session opened" | grep -v root | grep -v smmsp

```
taki sam wynik
```

## Zadanie 12 (GREP LICZY LICZBE LINII W PLIKU)

Ze strony kursu pobierz plik access_log1.txt. To plik z rejestrem zdarzeń (log), które dotyczą dostępu do serwera WWW. Napisz zapytanie **grep**, które sprawdzi ile jest wierszy w pliku access_log1.txt. Użyj **TYLKO** polecenia grep.

## Rozwiazanie

1. grep -c '' access_log1.txt

```
16

cat access_log1.txt | wc -l -> 16
```

## Zadanie 13 (SZUKA STRING:>)

Ze strony kursu pobierz plik auth2.log. To plik z rejestrem zdarzeń (log), które dotyczą logowania przez SSH. Napisz zapytanie grep, które wyświetli wiersze w których znajduje się numer portu 43996.

## Rozwiazanie

1. cat auth2.log | grep "port 43996"

```
Aug  4 22:10:14 devbox sshd[316284]: Received disconnect from 1.15.38.28 port 43996:11: Bye Bye [preauth]
Aug  4 22:10:14 devbox sshd[316284]: Disconnected from authenticating user root 1.15.38.28 port 43996 [preauth]
```

## Zadanie 14 (SZUKA JAKIES LICZBY)

Ze strony kursu pobierz plik access_log2.txt. To plik z rejestrem zdarzeń (log), które dotyczą dostępu do serwera WWW. Napisz zapytanie grep, które zapisze do pliku linie, w których znajdują się cyfry 8 lub 9.

## Rozwiazanie

1. cat access_log2.txt | grep -E "[8-9]"

## Zadanie 15 (LINIA ZACZYNA SIE NA Feb I KONCZY SIE NA root)

Ze strony kursu pobierz plik auth1.txt. To plik z rejestrem zdarzeń (log), które dotyczą logowania przez SSH. Napisz zapytanie **grep**, które wyświetli wiersze które rozpoczynają się od wyrazu Feb i kończą na root.

## Rozwiazanie

1. cat auth1.log | grep -E "^Feb.*root$"
```
...
Feb  4 10:17:01 ip-172-31-1-163 CRON[5045]: pam_unix(cron:session): session closed for user root
Feb  4 11:17:01 ip-172-31-1-163 CRON[5155]: pam_unix(cron:session): session closed for user root
Feb  4 12:17:01 ip-172-31-1-163 CRON[5364]: pam_unix(cron:session): session closed for user root
Feb  4 13:17:01 ip-172-31-1-163 CRON[5469]: pam_unix(cron:session): session closed for user root
Feb  4 14:17:01 ip-172-31-1-163 CRON[5561]: pam_unix(cron:session): session closed for user root
```


