---
title: Analizator konfiguracji dla zasad zabezpieczeń
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak za pomocą analizatora konfiguracji znaleźć i naprawić zasady zabezpieczeń, które znajdują się poniżej ustawień w zakresie Standardowa ochrona i Ścisła ochrona w wstępnie ustawionych zasadach zabezpieczeń.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0acdf6d300984c00bb1b1b060d3e36562983ebca
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021221"
---
# <a name="configuration-analyzer-for-protection-policies-in-eop-and-microsoft-defender-for-office-365"></a>Analizator konfiguracji do obsługi zasad ochrony w usługach EOP i Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Analizator konfiguracji w portalu Microsoft 365 Defender udostępnia centralną lokalizację do odnajdować i naprawiać zasady zabezpieczeń w miejscach, w których ustawienia znajdują się poniżej ustawień Standardowa ochrona i Ścisłe ustawienia profilu ochrony w wstępnie ustawionych [zasadach zabezpieczeń](preset-security-policies.md).

Analizator konfiguracji analizuje następujące typy zasad:

- **Exchange Online Protection (EOP**): Dotyczy Microsoft 365 firm z Exchange Online pocztowymi i autonomicznymi organizacjami usługi EOP bez Exchange Online skrzynek pocztowych:
  - [Zasady ochrony przed spamem](configure-your-spam-filter-policies.md).
  - [Zasady ochrony przed złośliwym oprogramowaniem](configure-anti-malware-policies.md).
  - [Zasady ochrony przed wyłudzaniem informacji w uchcie EOP](set-up-anti-phishing-policies.md#spoof-settings).

- **Zasady programu Microsoft Defender dla Office 365**: Dotyczy to również organizacji z pakietem Microsoft 365 E5 lub usługi Defender Office 365 subskrypcji dodatków:
  - Zasady ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365, które obejmują:
    - Te same [ustawienia fałszowania](set-up-anti-phishing-policies.md#spoof-settings) , które są dostępne w zasadach ochrony przed wyłudzaniem informacji eOP.
    - [Ustawienia personifikacji](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Zaawansowane progi wyłudzania informacji](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Sejf linki](set-up-safe-links-policies.md).
  - [Sejf zasady dotyczące załączników](set-up-safe-attachments-policies.md).

Wartości ustawień zasad Standardowe i Ścisłe używane jako linie bazowe opisano w tece Zalecane ustawienia usług [EOP i Microsoft Defender Office 365 zabezpieczeń](recommended-settings-for-eop-and-office365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do **strony Analizatora konfiguracji** , użyj narzędzia <https://security.microsoft.com/configurationAnalyzer>.

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby można było wykonać procedury z tego artykułu, musisz mieć przypisane uprawnienia Microsoft 365 Defender portalu administracyjnego:
  - Aby korzystać z analizatora konfiguracji  i do aktualizacji zasad zabezpieczeń, musisz być członkiem grup ról Zarządzanie **organizacją** lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do analizatora konfiguracji, musisz być członkiem grup ról czytnika  globalnego lub **czytnika zabezpieczeń**.

  Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej roli Azure Active Directory zapewnia użytkownikom wymagane uprawnienia w portalu usługi Microsoft 365 Defender oraz uprawnienia do innych funkcji w  aplikacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  > - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

## <a name="use-the-configuration-analyzer-in-the-microsoft-365-defender-portal"></a>Korzystanie z analizatora konfiguracji w portalu Microsoft 365 Defender sieci Microsoft 365 Defender.

W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji & e-mail  i zasad współpracy **& analizatora** \>  \> konfiguracji reguł zagrożeń w sekcji Zasady **szablonowe**. Aby przejść bezpośrednio do **strony Analizatora konfiguracji** , użyj narzędzia <https://security.microsoft.com/configurationAnalyzer>.

Strona **Analizatora konfiguracji** zawiera trzy główne karty:

- **Zalecenia standardowe**: porównaj istniejące zasady zabezpieczeń z zaleceniami standardowymi. Możesz dostosować wartości ustawień, aby przywrócić je na tym samym poziomie, na który jest w wersji Standardowe.
- **Ścisłe zalecenia**: Porównaj istniejące zasady zabezpieczeń z rygorystycznymi zaleceniami. Wartości ustawień można dostosować, aby przywrócić je na tym samym poziomie co wartości Ścisłe.
- **Analiza i historia konfiguracji**: Inspekcja i śledzenie zmian zasad w czasie.

### <a name="standard-recommendations-and-strict-recommendations-tabs-in-the-configuration-analyzer"></a>Karty Zalecenia standardowe i Ścisłe zalecenia w analizatorze konfiguracji

Domyślnie analizator konfiguracji jest otwierany na karcie **Zalecenia** standardowe. Możesz przejść na **kartę Ścisłe zalecenia** . Ustawienia, układ i akcje są takie same na obu kartach.

![Ustawienia i rekomendacji w Analizatorze konfiguracji.](../../media/configuration-analyzer-settings-and-recommendations-view.png)

W pierwszej sekcji karty jest wyświetlana liczba ustawień w poszczególnych typach zasad, które wymagają ulepszenia w porównaniu do ochrony standardowej lub ścisłej. Istnieją następujące typy zasad:

- **Ochrona przed spamem**
- **Ochrona przed wyłudzaniem informacji**
- **Ochrona przed złośliwym oprogramowaniem**
- **Sejf załączników** (jeśli twoja subskrypcja zawiera program Microsoft Defender dla Office 365)
- **Sejf linki (** jeśli twoja subskrypcja zawiera program Microsoft Defender dla Office 365)

Jeśli typ i liczba zasad nie są wyświetlane, wszystkie zasady tego typu spełniają zalecane ustawienia Standardowa lub Ścisła ochrona.

Pozostała część karty to tabela ustawień, które należy wyzsymać na poziomie Standardowa lub Ścisła ochrona. Tabela zawiera następujące kolumny:

- **Rekomendacje**: Wartość ustawienia w profilu ochrony standardowej lub ścisłej.
- **Zasady**: nazwa zasad, których dotyczy problem, które zawierają ustawienie.
- **Nazwa grupy/ustawienia zasad**: nazwa ustawienia wymagającego Twojej uwagi.
- **Typ zasad**: Ochrona przed spamem, ochrona przed wyłudzaniem informacji, ochrona przed złośliwym oprogramowaniem, linki Sejf wiadomości i załączniki Sejf wiadomości.
- **Bieżąca konfiguracja**: Bieżąca wartość ustawienia.
- **Ostatnia modyfikacja**: data ostatniej modyfikacji zasad.
- **Stan**: Zazwyczaj ta wartość to **Not started**.

### <a name="change-a-policy-setting-to-the-recommended-value"></a>Zmienianie ustawienia zasad na zalecaną wartość

Na karcie **Standardowa** ochrona **lub Ścisła** ochrona analizatora konfiguracji zaznacz wiersz w tabeli. Zostaną wyświetlone następujące przyciski:

- **Zastosuj zalecenie**
- **Wyświetl zasady**
- **Odświeżanie**:

Po zaznaczeniu wiersza i kliknięciu przycisku **Zastosuj** zalecenie zostanie wyświetlone okno dialogowe potwierdzenia (z opcją nie pokazywania ponownie tego okna dialogowego). Kliknięcie **przycisku OK** będzie się odbywało w następujący sposób:

- Ustawienie zostanie zaktualizowane do zalecanej wartości.
- Zasady **Zastosuj zalecenia i** **Widok znikną** (pozostanie **tylko przycisk Odśwież** ).
- Wartość **w** wierszu zmieni się na **Complete (Ukończono**).

Jeśli zaznaczysz wiersz i klikniesz  pozycję Wyświetl zasady, zostanie otwarte wysuwne szczegóły zasad, których dotyczy problem, w portalu Microsoft 365 Defender, gdzie możesz ręcznie zaktualizować to ustawienie.

Po automatycznej lub ręcznej aktualizacji ustawienia kliknij pozycję Odśwież,  aby wyświetlić ograniczoną liczbę zaleceń i usunięcie zaktualizowanego wiersza z wyników.

### <a name="configuration-drift-analysis-and-history-tab-in-the-configuration-analyzer"></a>Karta Analiza konfiguracji i historia w analizatorze konfiguracji

Ta karta umożliwia śledzenie zmian wprowadzonych w zasadach zabezpieczeń i ich porównanie z ustawieniami standardowymi i ścisłymi. Domyślnie są wyświetlane następujące informacje:

- **Ostatnia modyfikacja**
- **Zmodyfikowane przez**
- **Nazwa ustawienia**
- **Zasady**: nazwa zasad, których dotyczy problem.
- **Typ**: Ochrona przed spamem, ochrona przed wyłudzaniem informacji, ochrona przed złośliwym oprogramowaniem, linki Sejf wiadomości lub Sejf załączników.
- **Zmiana konfiguracji**: Stara wartość i nowa wartość ustawienia
- **Konfiguracja chcesz**: Wartość **Zwiększ lub Zmniejsz**, która wskazuje, że ustawienie jest zwiększone lub zmniejszone w porównaniu z zalecanym ustawieniem Standardowy lub Ścisłe.

Aby filtrować wyniki, kliknij pozycję **Filtruj**. W **wyświetlonym** wysuwanych filtrach możesz wybrać jeden z następujących filtrów:

- **Godzina rozpoczęcia** **i Godzina zakończenia** (data): Od dzisiaj możesz wrócić nawet o 90 dni.
- **Ochrona standardowa** lub **ścisła ochrona**

Po zakończeniu kliknij przycisk **Zastosuj**.

Aby wyeksportować wyniki do pliku .csv, kliknij pozycję **Eksportuj**.

Aby filtrować wyniki według określonej wartości Zmodyfikowane **przez**, **Nazwa ustawienia** lub Typ, użyj **pola** Wyszukaj.

![Widok analizy konfiguracji i historii w analizatorze konfiguracji.](../../media/configuration-analyzer-configuration-drift-analysis-view.png)
