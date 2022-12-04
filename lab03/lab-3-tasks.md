## My example

1. gen public and private key => pub.pem and priv.pem
2. echo -n "hello world" > message.txt
3. openssl pkeyutl **_-encrypt_** -inkey pub.pem -pubin -in message.txt -out message.enc

```
?�+a��?���������������w,�b*��   ׭�>-���Ap�������
                                                v ��KZ(���]�]���#��pҊ�(HA��5YLp�S�ﱘPgT��|3���D�C
           ����V`�I$Gs�a�p�qj6/�b%▒�▒����n�v� i���      �˟�Na�ru����    ��6��<�}i��?o������F�!�~W���El͵:I�P��m�▒�b0
                              4�Gg#ٸaٹ��F�?/�JŜ��z�a6t�▒�vڐ�����<�]��~I�����5$�ՠv��>X�<�c�u4�d��Pc�lEԇ���Ӂ�&:
                        ��%P޷
��=�ą{ե�a�a;                 �p�%�>���_zI���!
            u����e�Y�O�m������ 5R6����c9�|���<���T�*.��)�rU��R��������q��Q\�H��/A��u��6���jI��ӥ?�����7QuOՊL|,[8O�^U��s�?�MX����Z�ufD��6"��0���
```

4. openssl pkeyutl **_-decrypt_** -in message.enc -inkey priv.pem

```
hello world
```

## Zadanie 1

Wykorzystując bibliotekę **openssl**, wygeneruj **4096-bitowy** klucz prywatny oraz przypisany mu klucz publiczny (wformacie \*.pem) korzystając z algorytmu **RSA**. Oba klucze w czytelnej formie zapisz do pliku/ów.

## Rozwiazanie

1. openssl genrsa -out priv.pem 4096

```
-----BEGIN PRIVATE KEY-----
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
tiy4e/nrimjAqF9XgR18p+atqqEI4w==
-----END PRIVATE KEY-----
```

2. openssl rsa -in priv.pem -pubout -out pub.pem

```
-----BEGIN PUBLIC KEY-----
IICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAorCc0+sGObhWSB9Yx5SY
Dsalb1OtzajHOa97fV81AVWURPX9vfifDDd68Hdlw104Eujrb4gi5DPpvo285Z/r
30PNipYlG3cU6H0hSrOKBNdNvhFC9tHZeBuP3ljA1ISaUI4imoNhRj4rrwKmPDPq
kGXoECpFLycz64rlTpA9Uxk/u1Aim8I5NWwkVFOtdnM09rL+h/I3YwuxMGv2kuc5
c5NZU6Avl/hUdHJ7q3x3zG9Ucuej9vg1CvL1Nex4x3he+z7zFhHs+MyaunqTzeZO
aEG3EmZOh3hD6uMc6KhifCvTefGQNGdtycc8bsX4N42muM+LqtEpx9G3olXBcBD9
VPjeKjad5iUNQMRtwAObTX2DrUHprnj6jinh46pouptxbLiC6i/5rmdGyzrOC/or
7nYrTDO9g6oXgnuJ0S6yq2aMxucxm85HZmGk+AKkUV825rG5lczn5ZqEIOldTCfC
8fPwyehXAe7wdjMjaK8iLqRmYUeEoeNxO+IR30VuMrWifL6eG/Lnl4Wqmy5DJQDj
VlwXDIvOoWOwod4hR5ezIIjJf/tp+x8Js0XZXOHWTqlw+GwTZGpEm+NOS+j4Yk9l
ADSaC6FF0e4BvXc8ilEEHup4fLSWc0mngtLl53+byGQWG5rbfBbV/cGVsfhG6w6q
qndhoJXAbphnxtUhEQBhca0CAwEAAQ==
-----END PUBLIC KEY-----
```

3. openssl rsa -in priv.pem --text > privkey.txt

```
Private-Key: (4096 bit, 2 primes)
modulus:
    00:a2:b0:9c:d3:eb:06:39:b8:56:48:1f:58:c7:94:
    98:0e:c6:a5:6f:53:ad:cd:a8:c7:39:af:7b:7d:5f:
    35:01:55:94:44:f5:fd:bd:f8:9f:0c:37:7a:f0:77:
    65:c3:5d:38:12:e8:eb:6f:88:22:e4:33:e9:be:8d:
    bc:e5:9f:eb:df:43:cd:8a:96:25:1b:77:14:e8:7d:
    21:4a:b3:8a:04:d7:4d:be:11:42:f6:d1:d9:78:1b:
    8f:de:58:c0:d4:84:9a:50:8e:22:9a:83:61:46:3e:
    2b:af:02:a6:3c:33:ea:90:65:e8:10:2a:45:2f:27:
    33:eb:8a:e5:4e:90:3d:53:19:3f:bb:50:22:9b:c2:
    39:35:6c:24:54:53:ad:76:73:34:f6:b2:fe:87:f2:
    37:63:0b:b1:30:6b:f6:92:e7:39:73:93:59:53:a0:
    2f:97:f8:54:74:72:7b:ab:7c:77:cc:6f:54:72:e7:
    a3:f6:f8:35:0a:f2:f5:35:ec:78:c7:78:5e:fb:3e:
    f3:16:11:ec:f8:cc:9a:ba:7a:93:cd:e6:4e:68:41:
    b7:12:66:4e:87:78:43:ea:e3:1c:e8:a8:62:7c:2b:
    d3:79:f1:90:34:67:6d:c9:c7:3c:6e:c5:f8:37:8d:
    a6:b8:cf:8b:aa:d1:29:c7:d1:b7:a2:55:c1:70:10:
    fd:54:f8:de:2a:36:9d:e6:25:0d:40:c4:6d:c0:03:
    9b:4d:7d:83:ad:41:e9:ae:78:fa:8e:29:e1:e3:aa:
    68:ba:9b:71:6c:b8:82:ea:2f:f9:ae:67:46:cb:3a:
    ce:0b:fa:2b:ee:76:2b:4c:33:bd:83:aa:17:82:7b:
    89:d1:2e:b2:ab:66:8c:c6:e7:31:9b:ce:47:66:61:
    a4:f8:02:a4:51:5f:36:e6:b1:b9:95:cc:e7:e5:9a:
    84:20:e9:5d:4c:27:c2:f1:f3:f0:c9:e8:57:01:ee:
    f0:76:33:23:68:af:22:2e:a4:66:61:47:84:a1:e3:
    71:3b:e2:11:df:45:6e:32:b5:a2:7c:be:9e:1b:f2:
    e7:97:85:aa:9b:2e:43:25:00:e3:56:5c:17:0c:8b:
    ce:a1:63:b0:a1:de:21:47:97:b3:20:88:c9:7f:fb:
    69:fb:1f:09:b3:45:d9:5c:e1:d6:4e:a9:70:f8:6c:
    13:64:6a:44:9b:e3:4e:4b:e8:f8:62:4f:65:00:34:
    9a:0b:a1:45:d1:ee:01:bd:77:3c:8a:51:04:1e:ea:
    78:7c:b4:96:73:49:a7:82:d2:e5:e7:7f:9b:c8:64:
    16:1b:9a:db:7c:16:d5:fd:c1:95:b1:f8:46:eb:0e:
    aa:aa:77:61:a0:95:c0:6e:98:67:c6:d5:21:11:00:
    61:71:ad
publicExponent: 65537 (0x10001)
privateExponent:
    07:fe:a6:f0:af:3f:3c:52:32:d6:d9:61:80:8a:79:
    76:40:d2:de:e4:66:dc:8a:bd:15:92:10:98:85:11:
    29:33:f9:8e:71:ca:64:4d:d8:f8:37:5e:bd:7d:7e:
    29:c3:eb:ce:40:e2:a3:c2:82:b8:d5:3b:3f:62:eb:
    6a:34:b9:ff:a8:c8:c5:08:3c:88:48:89:72:57:ed:
    06:d8:16:1b:7a:b1:b3:2d:59:ad:a0:7b:3c:b0:b3:
    3f:41:62:95:ab:bf:e8:92:32:ba:6c:97:12:65:f3:
    d3:4c:b3:e1:47:fc:d6:f1:3a:44:f0:b1:3b:29:eb:
    11:80:2b:e5:45:9a:99:e0:5a:36:5c:16:36:7f:2c:
    89:a0:7b:2d:8d:7a:22:61:8c:a7:32:b0:b2:e1:3d:
    b7:d7:5a:7f:c8:cf:38:ce:8f:8f:3e:90:18:70:e3:
    97:73:ae:db:2e:ae:72:38:25:ab:f3:a0:02:36:ec:
    fc:72:02:2b:48:b9:17:98:08:6f:9a:27:59:23:7e:
    6f:18:dc:e9:a8:73:1f:13:88:7a:fc:3e:47:d7:65:
    ac:3f:3f:e6:5e:72:73:92:f1:77:fc:d4:56:8a:11:
    ce:02:ba:ab:f4:95:ce:d4:91:5d:24:65:11:cb:01:
    ab:26:99:d4:4d:25:54:37:00:56:1d:bb:69:b7:c3:
    37:24:c4:86:77:c5:49:97:5f:de:f9:e1:02:09:5c:
    20:4c:31:3b:7b:e1:ea:be:3b:cb:7a:c7:ae:48:57:
    69:98:64:6b:d2:71:cf:5d:f4:c5:6a:41:3e:9c:8a:
    06:53:cf:0b:d3:c5:f2:37:38:89:4f:7c:2e:65:1f:
    28:9f:40:66:03:b4:ff:d7:11:22:87:9b:ee:03:49:
    7e:6c:f0:4e:62:46:e0:b5:89:23:ff:96:0b:22:80:
    a6:c1:5f:4a:c8:f4:da:ac:27:6d:b5:c5:80:2f:0b:
    aa:d7:01:36:b4:aa:92:d2:49:68:a3:0d:ee:23:7b:
    df:eb:40:0f:8e:0d:10:42:ee:9c:1c:69:08:4c:45:
    e1:c0:16:e8:83:d9:13:ad:81:ef:b7:48:24:37:ac:
    3d:aa:04:e7:78:f9:7b:a0:5a:1e:ef:f0:68:5f:39:
    c0:ea:fc:fa:9e:0b:83:2b:1b:c4:28:36:11:24:70:
    93:58:68:99:ea:e1:35:5a:2d:e6:be:20:6d:01:9b:
    cd:f5:e3:b1:67:9a:1e:f2:8e:77:0c:ef:d7:75:0d:
    02:d3:01:cc:b0:86:9a:e0:bd:9a:b5:1b:be:c6:72:
    c9:f6:3b:90:79:9a:05:e8:77:d8:5b:67:91:ed:73:
    5d:9d:4e:d6:03:6a:98:bf:95:cf:8f:f8:7d:b4:c6:
    67:61
prime1:
    00:df:63:44:aa:31:06:8a:8a:25:18:56:c6:a7:2f:
    df:58:7f:9b:15:43:01:4b:58:e6:ed:b2:2c:ae:c6:
    2b:a5:40:ea:5c:72:f1:2e:04:95:7c:06:33:2c:68:
    5e:44:de:5c:be:8f:3a:25:49:cb:18:95:1a:8f:34:
    f2:11:75:9b:b9:56:ec:5d:c7:df:31:75:4f:03:b6:
    80:1b:3d:11:75:94:a9:48:d5:a9:ea:69:d0:b2:96:
    da:8e:0e:94:68:4b:99:ca:3a:c6:9c:e8:2e:e4:d9:
    ea:4f:a1:85:90:70:41:23:6d:f4:fe:a5:65:4a:7f:
    26:e1:28:bb:aa:a4:3f:95:53:54:87:0d:9d:2a:e3:
    32:6b:bb:5a:f3:05:a7:0e:51:52:31:19:0c:af:4c:
    3b:0f:e6:d4:4e:16:3d:f1:c5:ea:3d:35:fb:a0:db:
    91:97:31:92:d4:e2:ed:60:7b:5c:ab:af:40:64:67:
    c2:2e:0f:d7:d6:0d:10:76:e3:6a:ef:22:75:c8:af:
    e5:1e:9d:80:44:0c:c2:52:67:6d:3c:9b:3e:48:c0:
    c8:5a:7f:fe:2a:91:81:0e:95:31:cc:19:ba:f1:bc:
    8a:fb:10:0f:d4:55:a5:82:77:92:b8:97:ec:fa:78:
    23:1a:4d:2c:26:0f:ed:91:aa:47:14:2f:11:31:13:
    84:e1
prime2:
    00:ba:70:dd:c2:46:69:57:91:ad:b0:c5:df:a7:16:
    4d:e7:f9:37:f5:65:d8:c5:2f:e9:20:3f:bc:21:d1:
    74:4f:fb:c8:5d:63:27:51:24:4f:fb:b6:bd:ef:2d:
    c3:a9:1a:7c:83:08:8e:03:da:18:d6:22:24:49:09:
    30:a7:5c:a3:1e:08:60:bf:e3:a2:5c:94:98:af:e5:
    88:62:2c:20:a5:92:ea:58:98:50:f4:1b:a7:f4:36:
    8b:2e:48:ea:19:c5:68:a3:f5:35:bc:17:b2:0b:29:
    3d:53:d3:67:22:3b:e5:0c:9c:79:be:c2:f6:7c:8f:
    11:d5:7b:b3:93:3c:63:c9:7d:32:af:29:32:ac:73:
    a9:9a:8b:41:b6:a0:e3:3a:f8:e7:d9:2d:4f:ca:79:
    fc:9e:0a:bf:20:05:a5:f2:14:ef:11:5d:d0:20:e2:
    76:03:df:3b:8e:a5:48:9d:06:db:25:d2:4d:d7:e5:
    54:13:0a:f0:b9:f5:ab:bf:d9:a6:44:43:22:5e:f9:
    0f:a7:55:6c:7e:f8:90:e8:6d:69:36:f2:d0:ec:d8:
    7d:ef:97:fd:6c:90:99:6d:e3:41:be:ae:18:52:44:
    4a:f0:1f:e9:65:17:63:d3:2c:b2:cd:1c:f7:b9:dd:
    b3:47:99:0a:aa:d6:3a:83:3a:61:99:ce:f1:36:d7:
    ba:4d
exponent1:
    00:8d:aa:cc:af:0a:2c:55:cb:ca:3e:a7:39:90:69:
    81:c1:04:1b:fb:dd:e4:82:3e:3d:25:5d:2b:8d:23:
    4c:26:9f:06:81:de:bb:29:2d:eb:07:1e:7f:71:98:
    36:c0:82:2c:5b:05:46:20:c3:ad:b3:47:4b:f2:a9:
    e7:22:3f:6d:a4:9a:85:87:eb:eb:95:d8:09:66:17:
    65:22:e1:15:a3:75:c5:ed:d4:e2:cf:30:90:13:d2:
    2b:84:8f:a6:7a:86:07:60:02:ea:56:33:c1:19:8d:
    41:55:82:df:cb:7c:05:33:4c:d6:64:6f:cb:ce:f4:
    d8:59:4e:95:c5:60:28:9a:b0:a0:18:8d:ff:b0:65:
    29:62:bd:0c:ae:b6:54:fd:75:81:24:75:f8:5f:6b:
    7e:c1:54:e8:2b:25:5b:df:6a:5e:64:b7:49:7e:f8:
    00:5a:dc:2b:7c:2a:f5:d3:8c:28:77:10:cb:4b:61:
    a9:f9:c0:3e:67:17:1d:eb:e7:c9:b7:22:29:84:3e:
    58:95:93:d8:f6:4f:09:25:6d:46:0f:7b:7c:82:73:
    10:1c:a4:b3:31:97:d9:3a:c0:4f:36:5a:d2:fd:df:
    4e:5c:6e:11:3b:dd:9c:fb:22:8d:bf:d7:49:88:86:
    8b:ec:70:28:a1:72:d4:7c:de:79:f9:48:e8:24:31:
    76:c1
exponent2:
    4f:8d:71:52:40:31:1a:c8:72:50:87:5e:13:31:95:
    34:72:46:ca:53:16:d7:ac:c5:d0:98:e1:71:9c:aa:
    00:a6:f2:ab:c6:6f:34:54:46:3c:a5:91:0d:c9:7d:
    3f:5e:a9:da:4f:80:29:6c:9a:44:64:75:0f:24:f8:
    b9:b0:f1:79:13:22:15:3e:d0:3c:a8:bb:2d:f2:c6:
    ea:fc:e1:41:45:1a:f1:8a:ac:a0:3c:5c:c1:fb:b4:
    0f:9f:d5:24:01:f3:d0:62:04:f7:a9:34:b3:46:79:
    80:97:27:de:97:a7:f8:65:9c:1d:25:9b:7f:32:9c:
    ed:76:c6:fd:00:3b:a3:f1:e3:fa:91:9d:a9:b0:00:
    a2:8c:e1:11:48:3d:2d:20:9f:ed:2f:44:68:a4:fc:
    81:83:1c:62:51:86:a9:70:fd:41:6f:c2:2b:05:f6:
    4d:58:a7:55:0a:79:9d:67:1b:83:5b:e5:13:46:2b:
    45:a4:d9:6a:bf:c4:f5:2b:ad:a2:5a:f3:03:8b:4a:
    7e:a0:18:97:65:00:8f:ec:7f:84:8e:bf:4f:10:61:
    4c:26:92:60:0c:a3:2b:1c:59:25:3f:ab:e9:0e:72:
    db:5b:02:7f:bc:27:40:28:46:72:f6:f5:4d:3d:a8:
    0d:d8:e3:90:59:b0:c5:e5:d7:57:85:d1:af:11:05:
    d1
coefficient:
    1c:cf:eb:84:e6:55:d1:91:25:7d:23:64:1f:2a:f6:
    70:eb:22:ad:2e:dc:1b:98:54:82:ce:21:20:12:9b:
    c9:98:98:9c:d3:10:9a:c4:65:34:bd:b4:d0:ea:54:
    a3:db:b2:f2:57:01:06:1f:bb:b2:66:6b:a6:bf:e3:
    1d:ca:36:f9:9b:61:4f:2c:bb:c5:1a:db:25:2b:70:
    3f:f3:b4:36:02:69:74:86:2a:97:ea:99:9d:19:ad:
    f9:ed:f4:c8:31:5b:8a:5a:c5:b6:64:a9:b6:9b:2a:
    30:3b:57:b2:1a:c1:c8:c6:a2:4d:45:da:7e:86:2e:
    ce:bd:be:c7:c5:85:bf:76:04:16:d3:09:c6:ef:3a:
    fc:b4:68:55:c7:58:df:77:15:eb:5e:2a:ce:19:f8:
    5c:9c:c8:32:e2:f6:54:0a:ac:eb:e8:6f:bb:27:fe:
    75:45:b8:df:75:64:93:44:6d:4f:ce:52:f9:99:c3:
    6b:bb:de:cf:f4:4b:60:1f:7f:d2:98:0c:8d:c5:93:
    3e:b3:c6:1f:fc:e9:88:47:b3:4a:8a:7c:12:a3:30:
    1b:19:71:19:29:60:01:ae:12:f7:49:a6:85:d7:92:
    7b:33:33:ad:78:77:e1:29:a6:b6:2c:b8:7b:f9:eb:
    8a:68:c0:a8:5f:57:81:1d:7c:a7:e6:ad:aa:a1:08:
    e3
-----BEGIN PRIVATE KEY-----
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
tiy4e/nrimjAqF9XgR18p+atqqEI4w==
-----END PRIVATE KEY-----
```

4. openssl rsa -in pub.pem --pubin --text > pubkey.txt

```
Public-Key: (4096 bit)
Modulus:
    00:a2:b0:9c:d3:eb:06:39:b8:56:48:1f:58:c7:94:
    98:0e:c6:a5:6f:53:ad:cd:a8:c7:39:af:7b:7d:5f:
    35:01:55:94:44:f5:fd:bd:f8:9f:0c:37:7a:f0:77:
    65:c3:5d:38:12:e8:eb:6f:88:22:e4:33:e9:be:8d:
    bc:e5:9f:eb:df:43:cd:8a:96:25:1b:77:14:e8:7d:
    21:4a:b3:8a:04:d7:4d:be:11:42:f6:d1:d9:78:1b:
    8f:de:58:c0:d4:84:9a:50:8e:22:9a:83:61:46:3e:
    2b:af:02:a6:3c:33:ea:90:65:e8:10:2a:45:2f:27:
    33:eb:8a:e5:4e:90:3d:53:19:3f:bb:50:22:9b:c2:
    39:35:6c:24:54:53:ad:76:73:34:f6:b2:fe:87:f2:
    37:63:0b:b1:30:6b:f6:92:e7:39:73:93:59:53:a0:
    2f:97:f8:54:74:72:7b:ab:7c:77:cc:6f:54:72:e7:
    a3:f6:f8:35:0a:f2:f5:35:ec:78:c7:78:5e:fb:3e:
    f3:16:11:ec:f8:cc:9a:ba:7a:93:cd:e6:4e:68:41:
    b7:12:66:4e:87:78:43:ea:e3:1c:e8:a8:62:7c:2b:
    d3:79:f1:90:34:67:6d:c9:c7:3c:6e:c5:f8:37:8d:
    a6:b8:cf:8b:aa:d1:29:c7:d1:b7:a2:55:c1:70:10:
    fd:54:f8:de:2a:36:9d:e6:25:0d:40:c4:6d:c0:03:
    9b:4d:7d:83:ad:41:e9:ae:78:fa:8e:29:e1:e3:aa:
    68:ba:9b:71:6c:b8:82:ea:2f:f9:ae:67:46:cb:3a:
    ce:0b:fa:2b:ee:76:2b:4c:33:bd:83:aa:17:82:7b:
    89:d1:2e:b2:ab:66:8c:c6:e7:31:9b:ce:47:66:61:
    a4:f8:02:a4:51:5f:36:e6:b1:b9:95:cc:e7:e5:9a:
    84:20:e9:5d:4c:27:c2:f1:f3:f0:c9:e8:57:01:ee:
    f0:76:33:23:68:af:22:2e:a4:66:61:47:84:a1:e3:
    71:3b:e2:11:df:45:6e:32:b5:a2:7c:be:9e:1b:f2:
    e7:97:85:aa:9b:2e:43:25:00:e3:56:5c:17:0c:8b:
    ce:a1:63:b0:a1:de:21:47:97:b3:20:88:c9:7f:fb:
    69:fb:1f:09:b3:45:d9:5c:e1:d6:4e:a9:70:f8:6c:
    13:64:6a:44:9b:e3:4e:4b:e8:f8:62:4f:65:00:34:
    9a:0b:a1:45:d1:ee:01:bd:77:3c:8a:51:04:1e:ea:
    78:7c:b4:96:73:49:a7:82:d2:e5:e7:7f:9b:c8:64:
    16:1b:9a:db:7c:16:d5:fd:c1:95:b1:f8:46:eb:0e:
    aa:aa:77:61:a0:95:c0:6e:98:67:c6:d5:21:11:00:
    61:71:ad
Exponent: 65537 (0x10001)
-----BEGIN PUBLIC KEY-----
IICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAorCc0+sGObhWSB9Yx5SY
Dsalb1OtzajHOa97fV81AVWURPX9vfifDDd68Hdlw104Eujrb4gi5DPpvo285Z/r
30PNipYlG3cU6H0hSrOKBNdNvhFC9tHZeBuP3ljA1ISaUI4imoNhRj4rrwKmPDPq
kGXoECpFLycz64rlTpA9Uxk/u1Aim8I5NWwkVFOtdnM09rL+h/I3YwuxMGv2kuc5
c5NZU6Avl/hUdHJ7q3x3zG9Ucuej9vg1CvL1Nex4x3he+z7zFhHs+MyaunqTzeZO
aEG3EmZOh3hD6uMc6KhifCvTefGQNGdtycc8bsX4N42muM+LqtEpx9G3olXBcBD9
VPjeKjad5iUNQMRtwAObTX2DrUHprnj6jinh46pouptxbLiC6i/5rmdGyzrOC/or
7nYrTDO9g6oXgnuJ0S6yq2aMxucxm85HZmGk+AKkUV825rG5lczn5ZqEIOldTCfC
8fPwyehXAe7wdjMjaK8iLqRmYUeEoeNxO+IR30VuMrWifL6eG/Lnl4Wqmy5DJQDj
VlwXDIvOoWOwod4hR5ezIIjJf/tp+x8Js0XZXOHWTqlw+GwTZGpEm+NOS+j4Yk9l
ADSaC6FF0e4BvXc8ilEEHup4fLSWc0mngtLl53+byGQWG5rbfBbV/cGVsfhG6w6q
qndhoJXAbphnxtUhEQBhca0CAwEAAQ==
-----END PUBLIC KEY-----
```

## Zadanie 2

Wygeneruj parę kluczy opartych na krzywej eliptycznej **NIST P-256 prime256v1**.

## Rozwiazanie

1. openssl ecparam -list_curves

```
?lista krzywych eliptycznych?
```

2. openssl ecparam -name prime256v1 -genkey -out priv.pem

```
-----BEGIN EC PARAMETERS-----
BggqhkjOPQMBBw==
-----END EC PARAMETERS-----
-----BEGIN EC PRIVATE KEY-----
MHcCAQEEILs4QMOxR10mhw/CIHWXEzIFGHNqJhQhpxp6NixDE7k/oAoGCCqGSM49
AwEHoUQDQgAEEqMy5QpohAcWcUfOsIG7p921hG3oSvpAfX4BV44Pdc+ZecP6Lo9D
If13pX3ks9jwz24XBjXBjgVq5p6ws4sV2g==
-----END EC PRIVATE KEY-----
```

3. openssl ec -in priv.pem -pubout -out pub.pem

```
-----BEGIN PUBLIC KEY-----
MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEEqMy5QpohAcWcUfOsIG7p921hG3o
SvpAfX4BV44Pdc+ZecP6Lo9DIf13pX3ks9jwz24XBjXBjgVq5p6ws4sV2g==
-----END PUBLIC KEY-----
```

## Zadanie 3

Zaszyfruj ciąg znaków **96c91ac9c4b92882c105db9846caa31b** otrzymanym kluczem publicznym RSA znajdującym się w pliku **pub.pem**. Zaszyfrowane dane zakoduj algorytmem **Base64** i zapisz do pliku **myenc3.3.txt**. Prawidłowa odpowiedź znajduje się w pliku **enc3.3.txt**. Porównaj swoją odpowiedź z prawidłową odpowiedzią. Jakiego narzędzia możesz użyć do porównania?

## Rozwiazanie

1. echo -n "96c91ac9c4b92882c105db9846caa31b" > message.txt
2. openssl pkeyutl -encrypt -inkey pub.pem -pubin -in message.txt | base64 > message.enc

```
SLw0nEchfDZ5f7i5jc7KcPlHgYjTs+ydFfCqbjQEonAbSCYWHVB02RMMe/s/5C7Bgb280cvgEyzo
/MPftcUvaQOM8Dy9RxxUzp1vKeHTKBssw1vaPMqlrWGOJC+CEMKiZK03x7Kz9/ACtW8DjcgYRm2M
i3wGIb9H7ZeFKy25qrGfVwNijHEEaRCE+OljSTImFSNPl715StKLcwNUbIqP2Zyc4fPnGQCKbBrg
1d/zxpBNufz8d7cjGUL7kdgNv5hFxUXBqTk/fybQ9JWp8MJmdyjDgoEcEOw+YbZx1FpfV3q7vpsO
Z4yoQStWHA1McgyIR4MR0Zd/LOmdNbXiC6K69Z2CfVfEHYZNZDvtT7Sv9hkmBWxjb675iNyn8D6b
PPn3RSD8JvD8F2DWUjmUPMiIKlgf//+QpuxOHhFEC0/Lk6NflLOA9c5YZlOYFBUOiyvcYW7gJEAq
yG/y4rqN9rc5a9WtYpGjyhkkZzRfjPep1idQSjfo3MmpY0pQyQ6hIkcHZyKGcy2sR2hr/GZ4UKnt
pdjwHLagPNnlLg988RVIG/yrW/TwoS1nJCBv4eyfe7vpHCSLcYIIjuKUo+utwWHUt7uPsxZT2KBf
OgGvcduo9J63OyOxeVn6IZbHkrkp5duSrP5KQvXCJDmqEsVnkhe4YAsYCGZ7K8MFytwPK06Fdws=
```

## Zadanie 4

Posiadając parę kluczy **priv3.4.pem** odszyfruj plik **enc3.4.txt**. Wynik zapisz do pliku **dec3.4.txt**.

## Rozwiazanie

1. openssl pkeyutl -decrypt -in ex3.4.enc -inkey ex3.4keys.pem -out dec3.4.txt

```
dW1jcw==
```

## Zadanie 4

Posiadając parę kluczy **priv3.5.pem**, zweryfikuj podpis znajdujący się w pliku **sig3.5.txt**.

## Rozwiazanie

1.