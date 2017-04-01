libamiibo.noimage
========
amiibo™ parsing library (without images)
This is a drop in replacement for libamiibo that will reduce the filesize substantially for projects that do not need images (command line apps, etc)


Usage
=====
**libamiibo expects a binary dump. It will not work with XMLs or hexadecimal text files**.  See the unix program `xxd` to convert from hexadecimal to binary.

It offers support for encryption/decryption, figurine data, amiibo settings and AppData.

To parse a tag directly from a binary (encrypted) dump, use ```LibAmiibo.Data.AmiiboTag.FromNtagData()```.

When using an encrypted binary, the AmiiboSettings and AppData information will not contain any valid information.


Examples
--------

- Decrypting a NTAG215 dump "mario.bin" with the "retail.bin" keys:
Configure the paths for AmiiboKeys and CDNKeys in libamiibo.dll.config to direct to your key files.
```
byte[] encryptedNtagData = System.IO.File.ReadAllBytes("mario.bin");
LibAmiibo.Data.AmiiboTag amiiboTag = LibAmiibo.Data.AmiiboTag.DecryptWithKeys(encryptedNtagData);
```

- Parsing a NTAG215 dump "mario.bin" only for the non-encrypted information:
```
byte[] encryptedNtagData = System.IO.File.ReadAllBytes("mario.bin");
LibAmiibo.Data.AmiiboTag amiiboTag = LibAmiibo.Data.AmiiboTag.FromNtagData(encryptedNtagData);
```

Special Thanks
==============
- Benjamin Krämer for the libamiibo project that this is forked from. He deserves all the credit for any use of this library https://github.com/Falco20019/libamiibo
- Lucas "MacGuffen" Romo for his great work with https://docs.google.com/spreadsheets/d/1WJ4HxS9hkLquq-ATt1Rq9mioH6RDgP3qQrtYVaOdimM
- N3vin and CheatFreak for their great work with https://docs.google.com/spreadsheets/d/19E7pMhKN6x583uB6bWVBeaTMyBPtEAC-Bk59Y6cfgxA
- The people over at 3dbrew.org for there work on http://3dbrew.org/wiki/Amiibo and http://3dbrew.org/wiki/Mii
- socram8888 for his great work on https://github.com/socram8888/amiitool
- John "LouieGeetoo" Pray for his great work with http://www.amiibo.life
- HouseBreaker for the CDN parts I borrowed from https://github.com/HouseBreaker/NintendoCDN-TicketParser
- https://code.google.com/archive/p/3dsexplorer/ for the image processing parts
- http://www.codeproject.com/Articles/31702/NET-Targa-Image-Reader for the TGA processing part
