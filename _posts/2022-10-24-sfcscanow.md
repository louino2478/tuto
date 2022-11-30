---
layout: post
title: Réparer Windows avec SFC
description: Réparer Windows avec SFC
tags: []
---



cette documentation recueil des commande Windows pour réparer des problème (BSOD, ereur, ect...) pour Windows 11,10,8.1,8,ect...

# **vérification de l'image de Windows :**

Avant d'effectuer une réparation de Windows, nous devons d'abord s'assurer son image soit en bon état. Et si nécessaire la réparait.

## avec  Windows update

```powershell
Dism /Online /Cleanup-Image /ScanHealth
Dism /Online /Cleanup-Image /RestoreHealth
```

## sans Windows update 
Si les commandes précédentes ont échoué car Windows Update est défectueux, vous pouvez utiliser une ISO de Windows comme source de réparation.
```powershell
DISM.exe /Online /Cleanup-Image /RestoreHealth /Source:C:\RepairSource\Windows /LimitAccess
```

**NOTE :**  remplacé ```C:\RepairSource\Windows``` par l'emplacement de votre source de réparation dans votre ISO.

# **réparation de Windows :**

Ces commandes sont a faire après avoir vérifié l'image de Windows. Elles vont permettre de comparer votre installation de Windows et celle de son image. afin de réparer des fichiers corrompus quand cela est possible.

## dans un cmd normal en admin

```powershell
sfc /scannow
```

## depuis la console de récupération d'une clef USB bootable

il faut abord trouver sur qu'elle lecteur se trouve Windows
```powershell
bcdedit /enumlist
```

puis:

```powershell
sfc /scannow /offbootdir=C:\ /offwindir=C:\Windows
```

remplacer `C:\` par la lettre de lecteur de votre installation Windows

---

cette documentation est disponible dans un repo GitHub public, vous pouvais contribuer [ici](https://github.com/louino2478/tuto/tree/master/_posts).
