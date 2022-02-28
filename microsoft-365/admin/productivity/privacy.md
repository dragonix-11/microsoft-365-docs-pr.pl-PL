---
title: Wynik produktywności firmy Microsoft — prywatność
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Jak prywatność jest chroniona za pomocą wyników produktywności.
ms.openlocfilehash: 1bbc9c7459d29e9aef8dea102d1d98eed9c30550
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984440"
---
# <a name="privacy-controls-for-productivity-score"></a>Mechanizmy kontroli prywatności dotyczące wyników produktywności

Wynik produktywności zapewnia wgląd w transformację cyfrową organizacji dzięki jej użyciu Microsoft 365 technologii, które obsługują ten wynik.  Wyniki Twojej organizacji odzwierciedlają pomiary osób i technologii oraz mogą być porównywane z poziomami odniesienia organizacji podobnymi do Twoich. Aby uzyskać więcej informacji, zobacz [Omówienie wyników produktywności](productivity-score.md).

Twoja prywatność jest ważna dla firmy Microsoft. Aby dowiedzieć się, jak chronimy Twoją prywatność, zobacz [Oświadczenie o ochronie prywatności firmy Microsoft](https://privacy.microsoft.com/privacystatement). Ocena wydajności daje administratorowi IT w organizacji dostęp do ustawień prywatności, aby zapewnić możliwość działania wszelkich przeglądanych informacji wyników produktywności bez naruszania zaufania, które Twoja organizacja umieszcza w firmie Microsoft.

W obszarze doświadczeń osób metryki są dostępne tylko na poziomie organizacji. W tym obszarze opisano sposób korzystania Microsoft 365, patrząc na kategorie współpracy nad zawartością, mobilności, spotkań, pracy zespołowej i komunikacji. Umożliwiamy dostęp do kilku poziomów kontrolek, które ułatwiają spełnianie wymagań dotyczących wewnętrznych zasad zachowania poufności informacji.
Kontrolki zapewniają:

- Elastyczne role administratorów, aby kontrolować, kto może widzieć informacje w wynikach produktywności.
- Możliwość rezygnacji z możliwości rezygnacji z obszaru doświadczeń użytkowników.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Elastyczne role administratora, aby kontrolować, kto może widzieć informacje w wynikach produktywności

Aby wyświetlić cały wynik produktywności, musisz mieć jedną z następujących ról administratora:

- Administrator globalny
- Administratorzy serwera Exchange
- Administrator programu SharePoint
- Administrator programu Skype dla firm
- Administrator aplikacji Teams
- Czytnik globalny
- Czytelnik raportów
- Czytnik raportów podsumowujących użycie

Przypisz rolę Czytnik raportów lub Czytnik podsumowań użycia do każdego, kto jest odpowiedzialny za zarządzanie zmianami i ich stosowanie, ale nie musi być administratorem IT. Ta rola zapewnia im dostęp do pełnego interfejsu wyników produktywności w centrum administracyjnym Microsoft 365 administracyjnego.

Do czasu przydzielenia roli czytnika raportów podsumowujących użycia w programie PowerShell należy ją przypisywać za pomocą poleceń cmdlet programu PowerShell centrum administracyjne platformy Microsoft 365 później w 2020 r.

Aby przypisać rolę czytnika raportów podsumowujących użycia za pomocą programu PowerShell:

- Uruchom następujący program PowerShell:

```powershell
Connect-AzureAD
Enable-AzureADDirectoryRole -RoleTemplateId '75934031-6c7e-415a-99d7-48dbd49e875e'
$role=Get-AzureADDirectoryRole -Filter "roleTemplateId eq '75934031-6c7e-415a-99d7-48dbd49e875e'"
Get-AzureADDirectoryRoleMember -ObjectId $role.ObjectId
$u=Get-AzureADUser -ObjectId <user upn>
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId $u.ObjectId
```

</br>


## <a name="capability-to-opt-out-of-people-experiences"></a>Możliwość rezygnacji z możliwości obsługi osób

Możesz również zrezygnować z obszaru wyników pracy osób. Jeśli się zrezygnuje, nikt z Twojej organizacji nie będzie mógł wyświetlać tych metryk, a Twoja organizacja zostanie usunięta ze wszystkich obliczeń dotyczących komunikacji, spotkań, pracy zespołowej, współpracy nad zawartością i mobilności. Musisz być administratorem globalnym, aby wyłączyć w organizacji raporty dotyczące osób.

Aby zrezygnować:

1. W centrum administracyjnym **przejdź do pozycji** Ustawienia   >  **Org Ustawienia** >  **Productivity Score (Wynikiproduktu**).
2. Nie zaznaczaj pola wyboru **Zezwalaj na Microsoft 365** danych dotyczących użycia, które będą używane do analizy doświadczeń osób. Aby dowiedzieć się, jak zmodyfikować ustawienia udostępniania danych dla funkcji Endpoint Analytics w menedżerze konfiguracji usługi Intune, wybierz pozycję **Dowiedz się więcej**.
3. Wybierz  **pozycję Zapisz**.

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="Strona ustawień organizacji, na której można zrezygnować z otrzymywania od użytkowników opcji obsługi.":::
