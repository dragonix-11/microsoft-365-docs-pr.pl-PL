---
title: Zarządzanie dokładnym schematem dopasowania danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak edytować lub usuwać schemat dokładnego dopasowania danych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c3ce2620a95401fcd34d2a84378d2e544cd66e4d
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009717"
---
# <a name="manage-your-exact-data-match-schema"></a>Zarządzanie dokładnym schematem dopasowania danych

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>Ręczne edytowanie schematu klasyfikacji na podstawie usługi EDM

Jeśli chcesz zmienić schemat usługi EDM, na przykład plikedm.xml, na przykład zmienić **** pola używane w klasyfikacji na podstawie usługi EDM, wykonaj następujące czynności:

> [!TIP]
> Schemat usługi EDM i plik źródłowy tabeli z informacjami poufnymi możesz zmienić, aby skorzystać z możliwości skonfigurowania **dopasowania**. Po skonfigurowaniu program EDM ignoruje różnice między literami i niektóre ograniczniki podczas oceny elementu. Ułatwia to definiowanie schematu XML i plików danych poufnych. Aby uzyskać więcej informacji, [zobacz Korzystanie z pól caseInsensitive i ignorowanychDelimiters](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields).

1. Edytuj plik **edm.xml** (jest to plik omówiony w artykule Tworzenie schematu w celu dokładnego dopasowania danych [do typów informacji poufnych](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)).

2. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

3. Aby zaktualizować schemat bazy danych, uruchom następujące polecenie:

      ```powershell
      Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Zostanie wyświetlony monit o potwierdzenie w następujący sposób:

      > Potwierdź
      >
      > Czy na pewno chcesz wykonać tę akcję?
      >
      > Schemat usługi EDM dla magazynu danych (patientrecords) zostanie zaktualizowany.
      >
      > \[Y Yes A Yes to All \[N\] No \[L\] No to All \[?\]\] \[\] Pomoc (domyślna wartość to "Y"):

      > [!TIP]
      > Jeśli chcesz, aby zmiany wprowadzały się bez potwierdzenia, nie używaj ich w kroku `-Confirm:$true` 3.

      > [!NOTE]
      > Zaktualizowanie programu EDMSmSema przy użyciu dodatków może potrwać od 10 do 60 minut. Aktualizacja musi zostać ukończona przed wykonaniem kroków z zastosowaniem dodatków.

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>Ręczne usuwanie schematu klasyfikacji na podstawie usługi EDM

Jeśli chcesz usunąć schemat, którego używasz na podstawie klasyfikacji na podstawie usługi EDM, wykonaj następujące czynności:

1. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom następujące polecenie, zastępując nazwą magazynu danych "dokumentację pacjentów" na nazwę pacjenta, którą chcesz usunąć (na przykład przy użyciu magazynu dokumentacji pacjenta):

      ```powershell
      Remove-DlpEdmSchema -Identity 'patientrecords'
      ```

      Zostanie wyświetlony monit o potwierdzenie:

      > Potwierdź
      >
      > Czy na pewno chcesz wykonać tę akcję?
      >
      > Schemat usługi EDM dla magazynu danych (patientrecords) zostanie usunięty.
      >
      > \[Y Yes A Yes to All \[N\] No \[L\] No to All \[?\]\] \[\] Pomoc (domyślna wartość to "Y"):

      > [!TIP]
      > Jeśli chcesz wprowadzić zmiany bez potwierdzenia, nie używaj ich w kroku `-Confirm:$true` 2.

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>Edytowanie lub usuwanie schematu EDM za pomocą kreatora

1. Otwórz **centrum zgodności Klasyfikacja** \> **danych** \> **Dokładne dopasowania danych**.

2. Wybierz **schematy EDM**.

3. Wybierz pozycję EDM SIT, którą chcesz edytować.

4. Wybierz **pozycję Edytuj schemat EDM** **lub Usuń schemat EDM** z wysuwanych menu.

> [!IMPORTANT]
> Jeśli chcesz usunąć schemat, który jest już skojarzony z typem informacji poufnych usługi EDM, musisz najpierw usunąć typ informacji poufnych EDM, a następnie usunąć schemat.
