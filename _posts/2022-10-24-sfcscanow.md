---
layout: post
title: Réparer Windows avec SFC
description: Réparer Windows avec SFC
tags: []
---



Cette documentation recueille des commandes Windows pour réparer des problèmes (BSOD, ereur, ect...) pour Windows 11,10,8.1,8,ect...

# **Vérification de l'image de Windows :**

Avant d'effectuer une réparation de Windows, nous devons d'abord s'assurer son image soit en bon état. Et dans le cas contraire la réparer.

## Avec Windows Update

```powershell
Dism /Online /Cleanup-Image /ScanHealth
Dism /Online /Cleanup-Image /RestoreHealth
```

## Sans Windows Update

Si les commandes précédentes échouent, cela est dû a une défaillance de Windows Update.
Pour contourner le problème, on utilise comme source une image (ISO) de Windows pour lancer la réparation.

```powershell
DISM.exe /Online /Cleanup-Image /RestoreHealth /Source:C:\RepairSource\Windows /LimitAccess
```

**NOTE :** Remplacer ```C:\RepairSource\Windows``` par l'emplacement de votre image Windows.

# **Réparation de Windows :**

Vous devez d'abord avoir vérifé l'intégrité de l'image de Windows avant de passer à cette étape.

Ces commandes vous permettront de comparer votre installation de Windows avec l'image ISO afin de réparer d'eventuels fichiers corrompus dans la mesure du possible.

## Dans une console Windows (CMD) avec droits administrateur

```powershell
sfc /scannow
```

## Depuis la console de récupération d'une clé bootable Windows

Vous devez d'abord identifier la partition contenant votre Windows avec cette commande :

```powershell
bcdedit /enumlist
```

Une fois le lecteur identifié, vous pouvez lancer la réparation :

```powershell
sfc /scannow /offbootdir=C:\ /offwindir=C:\Windows
```

Remplacez `C` par la lettre de lecteur identifié à l'étape précédente.

---

Cette documentation est disponible dans un déôt GitHub public, vous pouvez y contribuer [ici](https://github.com/louino2478/tuto/tree/master/_posts).
