---
title: Microsoft Productivity Score and privacy insights (Wskaźnik produktywności firmy Microsoft i szczegółowe informacje o ochronie prywatności)
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
description: Jak prywatność jest chroniona za pomocą wskaźnika produktywności.
ms.openlocfilehash: 823e2cc087d3f0e9c486d8c0c4eca92ba42aee21
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467937"
---
# <a name="privacy-controls-for-productivity-score"></a>Mechanizmy kontroli prywatności dla współczynnika produktywności

Wynik produktywności zapewnia wgląd w proces transformacji cyfrowej organizacji dzięki wykorzystaniu Microsoft 365 i środowisk technologicznych, które ją obsługują.  Wynik twojej organizacji odzwierciedla pomiary osób i środowiska technologicznego i można go porównać z testami porównawczymi organizacji podobnymi do Twoich. Aby uzyskać więcej informacji, zapoznaj się z [omówieniem oceny produktywności](productivity-score.md).

Twoja prywatność jest ważna dla firmy Microsoft. Aby dowiedzieć się, jak chronimy Twoją prywatność, zobacz [Zasady zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement). Wynik produktywności zapewnia, jako administrator IT w organizacji, dostęp do ustawień prywatności, aby upewnić się, że wszystkie wyświetlane informacje o wyniku produktywności są możliwe do działania, a jednocześnie nie naruszają zaufania organizacji do firmy Microsoft.

W obszarze środowiska osób metryki są dostępne tylko na poziomie organizacji. W tym obszarze przedstawiono sposób, w jaki użytkownicy korzystają z Microsoft 365, przeglądając kategorie współpracy nad zawartością, mobilności, spotkań, pracy zespołowej i komunikacji. Udostępniamy kilka poziomów mechanizmów kontroli, które ułatwiają spełnienie wewnętrznych potrzeb w zakresie zasad ochrony prywatności.
Kontrolki zapewniają następujące elementy:

- Elastyczne role administratora do kontrolowania, kto może wyświetlać informacje w oceny produktywności.
- Możliwość rezygnacji z obszaru doświadczeń osób.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Elastyczne role administratora do kontrolowania, kto może wyświetlać informacje w oceny produktywności

Aby wyświetlić cały wynik produktywności, musisz być jedną z następujących ról administratora:

- Administrator globalny
- Administratorzy serwera Exchange
- Administrator programu SharePoint
- Administrator programu Skype dla firm
- Administrator aplikacji Teams
- Czytelnik globalny
- Czytelnik raportów
- Czytelnik raportów podsumowania użycia

Przypisz rolę Czytelnik raportów lub Czytelnik raportów podsumowania użycia wszystkim osobom odpowiedzialnym za zarządzanie zmianami i ich wdrażanie, ale niekoniecznie administratorowi IT. Ta rola zapewnia im dostęp do pełnego środowiska oceny wydajności w centrum administracyjnym Microsoft 365.

Rola Czytelnik raportów podsumowania użycia będzie musiała zostać przypisana za pośrednictwem poleceń cmdlet programu PowerShell, dopóki nie zostanie przypisana z Centrum administracyjne platformy Microsoft 365 później w 2020 r.

Aby przypisać rolę czytelnika raportów podsumowania użycia za pomocą programu PowerShell:

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


## <a name="capability-to-opt-out-of-people-experiences"></a>Możliwość rezygnacji z doświadczeń osób

Możesz również zrezygnować z obszaru doświadczenia osób w obszarze Ocena produktywności. Jeśli zrezygnujesz, nikt z Organizacji nie będzie mógł wyświetlać tych metryk, a Twoja organizacja zostanie usunięta z wszelkich obliczeń obejmujących komunikację, spotkania, pracę zespołową, współpracę nad zawartością i mobilność. Musisz być administratorem globalnym, aby zrezygnować z organizacji z raportów osób, które korzystają z nich.

Aby zrezygnować:

1. W centrum administracyjnym przejdź do **pozycji Ustawienia**  >   **Org Ustawienia** >  **Productivity Score (Wskaźnik Ustawienia Produktywność**).
2. Usuń zaznaczenie pola wyboru **Zezwalaj na użycie danych użycia Microsoft 365 dla osób korzystających ze szczegółowych informacji**. Aby dowiedzieć się, jak modyfikować ustawienia udostępniania danych dla usługi Endpoint Analytics w menedżerze konfiguracji Intune, wybierz pozycję **Dowiedz się więcej**.
3. Wybierz pozycję  **Zapisz**.

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="Strona ustawień organizacji, na której można zrezygnować z doświadczeń osób.":::
