---
title: Zarządzaj schematem dokładnego dopasowania danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak edytować lub usunąć dokładny schemat dopasowania danych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fb8a9d014bb4654ce39b0bb6312f8b20cd6d781e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629150"
---
# <a name="manage-your-exact-data-match-schema"></a>Zarządzaj schematem dokładnego dopasowania danych

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>Ręczne edytowanie schematu klasyfikacji opartej na protokole EDM

Jeśli chcesz wprowadzić zmiany w schemacie EDM, na przykład plik **edm.xml** , taki jak zmiana pól używanych do klasyfikacji opartej na programie EDM, wykonaj następujące kroki:

> [!TIP]
> Możesz zmienić schemat EDM i plik źródłowy tabeli informacji poufnych, aby korzystać z **konfigurowalnego dopasowania**. Po skonfigurowaniu program EDM zignoruje różnice wielkości liter i niektóre ograniczniki podczas oceniania elementu. Dzięki temu definiowanie schematu XML i poufnych plików danych jest łatwiejsze. Aby dowiedzieć się więcej, zobacz [Using the caseInsensitive and ignoredDelimiters fields (Używanie pól caseInsensitive i ignoredDelimiters).](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields)

1. Edytuj **plikedm.xml** (jest to plik omówiony w sekcji [Tworzenie schematu dla dokładnych typów informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

2. [Połącz się z programem PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell).

3. Aby zaktualizować schemat bazy danych, uruchom następujące polecenie:

      ```powershell
      Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Zostanie wyświetlony monit o potwierdzenie w następujący sposób:

      > Potwierdzić
      >
      > Czy na pewno chcesz wykonać tę akcję?
      >
      > Schemat EDM dla magazynu danych "patientrecords" zostanie zaktualizowany.
      >
      > \[Y\] Tak tak \[\] do wszystkich \[N\] Nie \[L\] Nie dla wszystkich\[?\] Pomoc (wartość domyślna to "Y"):

      > [!TIP]
      > Jeśli chcesz, aby zmiany wystąpiły bez potwierdzenia, nie używaj ich `-Confirm:$true` w kroku 3.

      > [!NOTE]
      > Aktualizacja pakietu EDMSchema z dodatkami może potrwać od 10 do 60 minut. Aktualizacja musi zostać ukończona przed wykonaniem kroków korzystających z dodatków.

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>Ręczne usuwanie schematu klasyfikacji opartej na protokole EDM

Jeśli chcesz usunąć schemat używany do klasyfikacji opartej na programie EDM, wykonaj następujące kroki:

1. [Połącz się z programem PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom następujące polecenie, zastępując nazwę magazynu danych "rekordami pacjentów" tą, którą chcesz usunąć (na przykład używając magazynu patientrecords):

      ```powershell
      Remove-DlpEdmSchema -Identity 'patientrecords'
      ```

      Zostanie wyświetlony monit o potwierdzenie:

      > Potwierdzić
      >
      > Czy na pewno chcesz wykonać tę akcję?
      >
      > Schemat EDM dla magazynu danych "patientrecords" zostanie usunięty.
      >
      > \[Y\] Tak tak \[\] do wszystkich \[N\] Nie \[L\] Nie dla wszystkich\[?\] Pomoc (wartość domyślna to "Y"):

      > [!TIP]
      > Jeśli chcesz, aby zmiany wystąpiły bez potwierdzenia, nie używaj ich `-Confirm:$true` w kroku 2.

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>Edytowanie lub usuwanie schematu EDM za pomocą kreatora

1. Otwórz **centrum** \> zgodności **Klasyfikacja** \> **danych Dokładne dopasowania danych**.

2. Wybierz **pozycję Schematy EDM**.

3. Wybierz pozycję EDM SIT, którą chcesz edytować.

4. Wybierz pozycję **Edytuj schemat EDM** lub **Usuń schemat EDM** z wysuwanego menu.

> [!IMPORTANT]
> Jeśli chcesz usunąć schemat i jest on już skojarzony z typem informacji poufnych EDM, musisz najpierw usunąć typ informacji poufnych EDM, a następnie usunąć schemat.
