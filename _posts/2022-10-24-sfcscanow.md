---
layout: post
title: Réparer Windows avec SFC
description: Réparer Windows avec SFC
tags: []
---



# vérification de l'image de Windows

## avec Windows update

```powershell
Dism /Online /Cleanup-Image /ScanHealth
Dism /Online /Cleanup-Image /RestoreHealth
```

## sans Windows update
documentation non finis


# réparation de Windows

## dans un cmd normal en admin

```powershell
sfc /scannow
```

## depuis la console de récupération

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
