---
title: Nowe zasady alertów w Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkDEFENDER
ROBOTS: noindex,nofollow
description: Udostępniamy nowe zasady alertów dla Ochrona usługi Office 365 w usłudze Microsoft Defender. Wycofujemy również dwie istniejące zasady alertów, które zostały zastąpione przez nowe.
ms.openlocfilehash: 0f9a8b74febe3ea59d022baceff7c15c3ee2e5d1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634011"
---
# <a name="new-alert-policies-in-microsoft-defender-for-office-365"></a>Nowe zasady alertów w Ochrona usługi Office 365 w usłudze Microsoft Defender

Ochrona usługi Office 365 w usłudze Microsoft Defender wprowadza nowe i ulepszone zasady alertów związane z wykrywaniem po dostarczeniu. Obejmuje to ulepszenia podręczników automatycznego badania & odpowiedzi (AIR) skojarzonych z nimi. Ponadto modyfikujemy klasyfikację ważności dla sześciu domyślnych zasad alertów, aby lepiej dopasować alerty generowane przez te zasady do ich wpływu na organizację.

## <a name="post-delivery-detections"></a>Wykrywanie po dostarczeniu

Wprowadzimy cztery nowe domyślne zasady alertów związane z wykrywaniem po dostarczeniu po usunięciu komunikatów ze skrzynki odbiorczej przez Ochrona usługi Office 365 w usłudze Microsoft Defender Automatyczne przeczyszczanie zerogodzin (ZAP). Te cztery nowe zasady alertów zastąpią dwie istniejące domyślne zasady alertów, które obejmują scenariusze zap i zapewnią organizacjom rozszerzone szczegóły dotyczące podstawowego wykrywania i powiązanych wskaźników. Te alerty (i podręczniki AIR, które zostaną wyzwolone z tych alertów) będą dokładnie przechwytywać zagrożenia wiadomości e-mail i jednostek, w tym, czy adres URL wskazuje złośliwy plik lub czy plik zawiera złośliwy adres URL.

W poniższej tabeli wymieniono nowe zasady alertów i istniejące zasady alertów, które zostaną usunięte. Zobacz sekcję [Jak wpłynie to na organizację](#how-this-will-affect-your-organization) , aby uzyskać szczegółowe informacje o wdrożeniu.

|Nowe lub istniejące zasady alertów|Nazwa zasad alertu|Identyfikator zasad alertu|
|---|---|---|
|Nowy|**Wiadomości e-mail zawierające złośliwy adres URL usunięte po dostarczeniu**|8e6ba277-ef39-404e-aaf1-294f6d9a2b88|
|Nowy|**Wiadomości e-mail zawierające złośliwy plik usunięte po dostarczeniu**|4b1820ec-39dc-45f3-abf6-5ee80df51fd2|
|Nowy|**Wiadomości e-mail z kampanii zostały dostarczone, a później usunięte**|c8522cbb-9368-4e25-4ee9-08d8d899dfab|
|Nowy|**Wiadomości e-mail usunięte po dostarczeniu**|b8f6b088-5487-4c70-037c-08d8d71a43fe|
|Istniejące (zostaną usunięte)|**Wiadomości e-mail zawierające fałszywe adresy URL usunięte po dostarczeniu**|EA8169FA-0678-4751-8854-AEBEA7ADECEB|
|Istniejące (zostaną usunięte)|**Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu**|0179B3F7-3FDA-40C3-8F24-278563978DBB|

## <a name="alert-severity-enhancements"></a>Ulepszenia ważności alertów

W poniższej tabeli określono domyślne zasady alertów, których klasyfikacje ważności są modyfikowane. Zmieniamy klasyfikację ważności dla tych zasad alertów, aby lepiej dopasować je do potencjalnego ryzyka i wpływu na organizację oraz pomóc zespołom zabezpieczeń w ustalaniu priorytetów alertów generowanych przez te zasady.

|Alert|Identyfikator zasad alertu|Stara ważność|Nowa ważność|
|---|---|---|---|
|**Podejrzane działania w zakresie przesyłania dalej wiadomości e-mail**|BFD48F06-0865-41A6-85FF-ADB746423EBF|Średni|High (Wysoki)|
|**Wiadomość e-mail zgłoszona przez użytkownika jako złośliwe oprogramowanie lub phish**|B26A5770-0C38-434A-9380-3A3C2C27BBB3|Informacyjny|Niskie|
|**Nietypowy wzrost liczby wiadomości e-mail zgłoszonych jako phish**|A00D8C62-9320-4EEA-A7E5-966B9AC09558|High (Wysoki)|Średni|
|**Administracja ukończono przesyłanie wyników**|AE9B83DD-6039-4EA9-B675-6B0AC3BF4A41|Niskie|Informacyjny|
|**Tworzenie reguły przekazywania/przekierowania**|D59A8FD4-1272-41EE-9408-86F7BCF72479|Niskie|Informacyjny|
|**Rozpoczęto lub wyeksportowano wyszukiwanie zbierania elektronicznych materiałów dowodowych**|6FDC5710-3998-47F0-AFBB-57CEFD7378A|Meduim|Informacyjny|

## <a name="when-will-these-changes-happen"></a>Kiedy nastąpią te zmiany

W poniższej tabeli określono, kiedy nowe zasady alertów zaczną wyzwalać alerty po dostarczeniu. W tabeli określono również, kiedy zostaną usunięte dwie istniejące zasady alertów.

|Zasady alertów|Data|
|---|---|
|**Wiadomości e-mail zawierające złośliwy adres URL usunięte po dostarczeniu** (nowe)|Alerty rozpoczną się 11 kwietnia 2021 r.|
|**Wiadomości e-mail zawierające złośliwy plik usunięte po dostarczeniu** (nowe)|Alerty rozpoczną się 11 kwietnia 2021 r.|
|**Wiadomości e-mail z kampanii zostały dostarczone, a później usunięte** (nowe)|Alerty rozpoczną się 28 maja 2021 r.|
|**Dostarczono złośliwe wiadomości e-mail, a później usunięto** (nowe)|Alerty rozpoczną się 28 maja 2021 r.|
|**Wiadomości e-mail zawierające adresy URL języka phish usunięte po dostarczeniu** (istniejące zostaną usunięte)|Zasady alertów zostały usunięte w czerwcu 2021 r. Zobacz sekcję [Co należy zrobić, aby przygotować się do wprowadzenia tych zmian](#what-you-need-to-do-to-prepare-for-these-changes) .|
|**Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu** (istniejące zostaną usunięte)|Zasady alertów zostały usunięte w czerwcu 2021 r. Zobacz sekcję [Co należy zrobić, aby przygotować się do wprowadzenia tych zmian](#what-you-need-to-do-to-prepare-for-these-changes) .|

Zmiany ważności alertów zostaną wprowadzone we wszystkich organizacjach do 14 maja 2021 r.

## <a name="how-this-will-affect-your-organization"></a>Jak wpłynie to na organizację

Nowe alerty rozpoczną wyzwalanie i wyzwalanie badań AIR w organizacji w terminach wymienionych powyżej. Aby zmniejszyć wpływ na organizacje zabezpieczeń, które zoperatywizowały dwa alerty, które mają zostać usunięte, zobaczysz alerty wyzwalane przez istniejące zasady alertów *i* alerty wyzwalane przez nowe zasady alertów między 5 kwietnia 2021 r. a 28 maja 2021 r. Ma to zapewnić zespołom ds. zabezpieczeń czas na obsługę wymaganych zmian. Aby pomóc zespołom zabezpieczeń w zwiększeniu liczby alertów w tym krótkim czasie, zarówno istniejące alerty, jak i nowe alerty zostaną skorelowane z tym samym badaniem AIR i skorelowane z tym samym zdarzeniem. W szczególności obejmuje to następujące zachowanie alertów, badań AIR i zdarzeń:

- **Alerty**: Zgodnie z projektem zobaczysz następujące pary alertów w istniejących i nowych alertach:

  - **Wiadomości e-mail zawierające fałszywe adresy URL usunięte po dostarczeniu** WIADOMOŚCI **e-mail zawierające złośliwy adres URL usunięte po dostarczeniu**

  - **Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu** WIADOMOŚCI **e-mail zawierające złośliwy plik usunięte po dostarczeniu**

  ![Pary alertów dla nowych i istniejących alertów.](../media/DefenderAlerts.png)

   Aby uzyskać więcej informacji na temat zarządzania tymi parami alertów, zobacz sekcję [Co należy zrobić, aby przygotować się do tych zmian](#what-you-need-to-do-to-prepare-for-these-changes) .

- **Badania AIR**: Alerty będą skorelowane z pojedynczym badaniem AIR, a jeden z alertów zostanie sklasyfikowany jako "wyzwalający", a drugi jako "powtarzający się".

  ![Pary alertów w badaniach AIR.](../media/AIRAlerts.png)

- **Zdarzenia**: oba alerty będą skorelowane z tym samym zdarzeniem

  ![Pary alertów w obszarze Zdarzenia.](../media/IncidentsAlerts.png)

## <a name="what-you-need-to-do-to-prepare-for-these-changes"></a>Co należy zrobić, aby przygotować się na te zmiany

Sposób, w jaki organizacja korzysta z tych alertów, określi, co należy zrobić, aby się przygotować. Jeśli alerty zostały zoperatyzowane i są używane lub używane za pośrednictwem interfejsu API, powiadomienia e-mail z alertem lub w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> lub <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>, musisz zmodyfikować przepływy pracy.

**Jeśli te alerty nie zostały zoperatyzowane, możesz wykonać jedną z następujących czynności:**

- Wyłącz następujące zasady alertów (usuwane), aby zmniejszyć liczbę alertów w organizacji:

  - **Wiadomości e-mail zawierające fałszywe adresy URL usunięte po dostarczeniu**

  - **Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu**

- Nic nie rób. 28 maja 2021 r. wyłączymy istniejące zasady alertów.

**Jeśli te alerty zostały zoperatyzowane:**

- Rozpocznij korzystanie z nowych alertów w ramach przepływów pracy w oczekiwaniu na usunięcie istniejących zasad alertów 28 maja 2021 r. Jeśli masz logikę niestandardową w systemie biletów, skrzynkę pocztową zabezpieczeń, w której otrzymujesz powiadomienia e-mail z alertami, lub rozwiązanie SIEM, które zależy od nazwy alertu lub identyfikatora zasad alertu (CorrelationId), musisz zmodyfikować logikę, aby dostosować tę zmianę.

  > [!NOTE]
  > Informacje w alertach, badaniach i zdarzeniach nie uległy zmianie. W rzeczywistości te informacje zostały rozszerzone o dodatkowe szczegóły dotyczące powiązanych z nimi zagrożeń.

- Po wprowadzeniu modyfikacji możesz wyłączyć istniejące zasady alertów, aby zmniejszyć liczbę alertów w organizacji:

  - **Wiadomości e-mail zawierające fałszywe adresy URL usunięte po dostarczeniu**

  - **Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu**

  Możesz też pozostawić te zasady alertów włączone, dopóki nie usuniemy ich 28 maja 2021 r.
