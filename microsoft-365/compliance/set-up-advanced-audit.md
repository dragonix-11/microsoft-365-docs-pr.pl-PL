---
title: Konfigurowanie inspekcji (Premium) na platformie Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: W tym artykule opisano sposób konfigurowania inspekcji (Premium), aby można było przeprowadzać badania kryminalistyczne w przypadku naruszenia zabezpieczeń kont użytkowników lub badania innych zdarzeń związanych z zabezpieczeniami.
ms.openlocfilehash: adffd696a3eca2d51fb5325cd79c1ba26e58936c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639341"
---
# <a name="set-up-microsoft-purview-audit-premium"></a>Konfigurowanie Inspekcja w Microsoft Purview (Premium)

Jeśli Twoja organizacja ma subskrypcję i licencje użytkowników końcowych, które obsługują inspekcję (Premium), wykonaj następujące kroki, aby skonfigurować i wykorzystać dodatkowe możliwości w obszarze Inspekcja (Premium).

![Przepływ pracy do skonfigurowania inspekcji (Premium).](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-audit-premium-for-users"></a>Krok 1. Konfigurowanie inspekcji (Premium) dla użytkowników

Funkcje inspekcji (Premium), takie jak możliwość rejestrowania kluczowych zdarzeń, takich jak MailItemsAccessed i Send, wymagają odpowiedniej licencji E5 przypisanej do użytkowników. Ponadto dla tych użytkowników należy włączyć plan aplikacji/usługi inspekcji zaawansowanej. Aby sprawdzić, czy aplikacja Zaawansowana inspekcja jest przypisana do użytkowników, wykonaj następujące kroki dla każdego użytkownika:

1. W Centrum administracyjne platformy Microsoft 365 przejdź do pozycji **Użytkownicy** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**aktywni użytkownicy**</a> i wybierz użytkownika.

2. Na stronie wysuwanej właściwości użytkownika kliknij pozycję **Licencje i aplikacje**.

3. W sekcji **Licencje** sprawdź, czy użytkownikowi przypisano licencję E5 lub masz przypisaną odpowiednią licencję dodatku. Aby uzyskać listę licencji obsługujących inspekcję (Premium), zobacz [Wymagania dotyczące licencjonowania inspekcji (Premium](auditing-solutions-overview.md#audit-premium-1)).

4. Rozwiń sekcję **Aplikacje** i sprawdź, czy zaznaczono pole wyboru **Zaawansowana inspekcja platformy Microsoft 365** .

5. Jeśli pole wyboru nie jest zaznaczone, zaznacz je, a następnie kliknij przycisk **Zapisz zmiany.**

   Rejestrowanie rekordów inspekcji dla elementów MailItemsAccessed i Send rozpocznie się w ciągu 24 godzin. Aby rozpocząć rejestrowanie dwóch innych zdarzeń inspekcji (Premium), należy wykonać krok 3: SearchQueryInitiatedExchange i SearchQueryInitiatedSharePoint.

Ponadto jeśli dostosowano akcje skrzynki pocztowej, które są rejestrowane w skrzynkach pocztowych użytkowników lub udostępnionych skrzynkach pocztowych, żadne nowe zdarzenia inspekcji (Premium) wydane przez firmę Microsoft nie będą automatycznie poddawane inspekcji w tych skrzynkach pocztowych. Aby uzyskać informacje o zmianie akcji skrzynki pocztowej, które są poddawane inspekcji dla każdego typu logowania, zobacz sekcję "Zmień lub przywróć akcje skrzynki pocztowej zarejestrowane domyślnie" w sekcji [Zarządzanie inspekcją skrzynek pocztowych](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="step-2-enable-audit-premium-events"></a>Krok 2. Włączanie zdarzeń inspekcji (Premium)

Należy włączyć dwa zdarzenia inspekcji (Premium) (SearchQueryInitiatedExchange i SearchQueryInitiatedSharePoint), które mają być rejestrowane, gdy użytkownicy wykonują wyszukiwania w usługach Exchange Online i SharePoint Online. Aby umożliwić inspekcję tych dwóch zdarzeń dla użytkowników, uruchom następujące polecenie (dla każdego użytkownika) w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

W środowisku z wieloma obszarami geograficznymi należy uruchomić poprzednie polecenie **Set-Mailbox** w lesie, w którym znajduje się skrzynka pocztowa użytkownika. Aby zidentyfikować lokalizację skrzynki pocztowej użytkownika, uruchom następujące polecenie: 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

Jeśli polecenie umożliwiające włączenie inspekcji zapytań wyszukiwania zostało wcześniej uruchomione w lesie innym niż skrzynka pocztowa użytkownika, musisz usunąć wartość SearchQueryInitiated ze skrzynki pocztowej użytkownika, uruchamiając `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` polecenie, a następnie dodaj ją do skrzynki pocztowej użytkownika w lesie, w którym znajduje się skrzynka pocztowa użytkownika.

## <a name="step-3-set-up-audit-retention-policies"></a>Krok 3. Konfigurowanie zasad przechowywania inspekcji

Oprócz domyślnych zasad, które zachowują rekordy inspekcji programu Exchange, SharePoint i Azure AD przez jeden rok, można utworzyć dodatkowe zasady przechowywania dzienników inspekcji w celu spełnienia wymagań zespołów ds. operacji zabezpieczeń, IT i zgodności organizacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasadami przechowywania dzienników inspekcji](audit-log-retention-policies.md).

## <a name="step-4-search-for-audit-premium-events"></a>Krok 4. Wyszukiwanie zdarzeń inspekcji (Premium)

Teraz, gdy masz skonfigurowaną usługę Audit (Premium) dla swojej organizacji, możesz wyszukiwać kluczowe zdarzenia inspekcji (Premium) i inne działania podczas prowadzenia dochodzeń kryminalistycznych. Po ukończeniu kroków 1 i 2 możesz przeszukać dziennik inspekcji pod kątem zdarzeń inspekcji (Premium) i innych działań podczas badania kryminalistycznego naruszonego konta i innych typów badań zabezpieczeń lub zgodności. Aby uzyskać więcej informacji na temat przeprowadzania badania kryminalistycznego kont użytkowników, których bezpieczeństwo zostało naruszone, przy użyciu zdarzenia Inspekcja MailItemsAccessed (Premium), zobacz [Używanie inspekcji (Premium) do badania naruszonych kont](mailitemsaccessed-forensics-investigations.md).
