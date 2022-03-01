---
title: Nowe zasady alertów w programie Microsoft Defender dla systemu Office 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Publikujemy nowe zasady alertów dotyczące programu Microsoft Defender dla systemu Office 365. Wycofuje też dwie istniejące zasady alertów, które zostały zastąpione przez nowe.
ms.openlocfilehash: 895a1fa51b9db5991bdb5235fd467bbac581d02e
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005260"
---
# <a name="new-alert-policies-in-microsoft-defender-for-office-365"></a>Nowe zasady alertów w programie Microsoft Defender dla systemu Office 365

Usługa Microsoft Defender for Office 365 wprowadza nowe i ulepszone zasady alertów dotyczące wykrywania po dostarczeniu. Zawiera on ulepszenia podręczników funkcji Automated Investigation & Response (AIR) skojarzonych z nimi. Ponadto modyfikujemy klasyfikację ważności dla sześciu domyślnych zasad alertów, aby lepiej dopasować alerty generowane przez te zasady do ich wpływu na Twoją organizację.

## <a name="post-delivery-detections"></a>Wykrywanie po dostarczeniu

Po programie Microsoft Defender dla programu Office 365 Autowyczyszczenie bez godzin (ZAP) wprowadzimy cztery nowe domyślne zasady alertów dotyczące wykrywania po dostarczeniu, które usuwają wiadomości ze skrzynki odbiorczej. Te cztery nowe zasady alertów zastąpią dwie istniejące domyślne zasady alertów, które obejmują scenariusze zap i będą dostarczać organizacjom bardziej szczegółowych informacji dotyczących wykrywania źródłowego i powiązanych wskaźników. Alerty (oraz podręczniki air, które będą wyzwalane z tych alertów) dokładnie przechwytują zagrożenia związane z wiadomościami e-mail i jednostkami, w tym jeśli adres URL wskazuje złośliwy plik lub zawiera złośliwy adres URL.

W poniższej tabeli wymieniono nowe zasady alertów oraz istniejące zasady alertów, które zostaną usunięte. Zobacz [sekcję Jaki będzie to miało wpływ na Twoją organizację](#how-this-will-affect-your-organization) , aby uzyskać szczegółowe informacje na temat tego rzutowania.

| Nowe lub istniejące zasady alertów | Nazwa zasad alertu | Identyfikator zasad alertu|
|:-----------------------------|:----------------|:--------------|
| Nowy| **Wiadomości e-mail zawierające złośliwy adres URL usunięte po dostarczeniu**   | 8e6ba277-ef39-404e-aaf1-294f6d9a2b88 |
| Nowy| **Wiadomości e-mail zawierające złośliwy plik usunięte po dostarczeniu**  | 4b1820ec-39dc-45f3-abf6-5ee80df51fd2 |
| Nowy| **Wiadomości e-mail z kampanii zostały dostarczone, a później usunięte** | c8522cbb-9368-4e25-4ee9-08d8d899dfab |
| Nowy|**Wiadomości e-mail usunięte po dostarczeniu**                | b8f6b088-5487-4c70-037c-08d8d71a43fe |
| Istniejące (zostaną usunięte)| **Wiadomości e-mail zawierające adresy URL wyłudające informacje usunięte po dostarczeniu**| EA8169FA-0678-4751-8854-AEBEA7ADECEB |
| Istniejące (zostaną usunięte)| **Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu**| 0179B3F7-3FDA-40C3-8F24-278563978DBB |
||||

## <a name="alert-severity-enhancements"></a>Alert o ulepszeniach ważności

W poniższej tabeli przedstawiono domyślne zasady alertów, których klasyfikacje ważności są modyfikowane. Zmieniamy klasyfikację ważności tych zasad alertów, aby lepiej dopasować je do potencjalnego ryzyka i wpływu na Twoją organizację oraz aby ułatwić zespołom zabezpieczeń określanie priorytetów alertów generowanych przez te zasady.

| Alert| Identyfikator zasad alertu| Stara ważność| Nowa ważność  |
|:----------|:---------------|:------------|:--------------|
| **Podejrzane działania w zakresie przesyłania dalej poczty e-mail**| BFD48F06-0865-41A6-85FF-ADB746423EBF | Średni| High (Wysoki)|
| **Wiadomości e-mail zgłoszone przez użytkownika jako złośliwe oprogramowanie lub wyłudzy** | B26A5770-0C38-434A-9380-3A3C2C27BBB3 | Informacyjne | Niska|
| **Nietypowy wzrost liczby wiadomości e-mail zgłoszonych jako wyłudzy** | A00D8C62-9320-4EEA-A7E5-966B9AC09558 | High (Wysoki)| Średni |
| **Ukończono wynik przesyłania przez administratora** | AE9B83DD-6039-4EA9-B675-6B0AC3BF4A41 | Niska| Informacyjne |
| **Tworzenie reguły przesyłania dalej/przekierowywania** | D59A8FD4-1272-41EE-9408-86F7BCF72479 | Niska| Informacyjne |
| **Rozpoczęte lub wyeksportowane wyszukiwanie zbierania elektronicznych materiałów dowodowych** | 6FDC5710-3998-47F0-AFBB-57CEFD7378A | Meduim | Informacyjne |
|||||

## <a name="when-will-these-changes-happen"></a>Kiedy nastąpią te zmiany

W poniższej tabeli po określono, kiedy nowe zasady alertów zaczną wyzwalać alerty po dostarczeniu. W tabeli po określono również, kiedy dwie istniejące zasady alertów zostaną usunięte.

| Zasady alertów| Data |
|:------------|:-----|
| **Wiadomości e-mail zawierające złośliwy adres URL usunięte po dostarczeniu** (nowe) | Alerty zaczną wyzwalać się 11 kwietnia 2021 r.|
| **Wiadomości e-mail zawierające złośliwy plik usunięte po dostarczeniu** (nowe) | Alerty zaczną wyzwalać się 11 kwietnia 2021 r. |
| **Wiadomości e-mail z kampanii zostały dostarczone, a później usunięte** (nowe) | Alerty zaczną wyzwalać się 28 maja 2021 r.|
| **Złośliwe wiadomości e-mail zostały dostarczone, a później usunięte** (nowe) | Alerty zaczną wyzwalać się 28 maja 2021 r.|
| **Wiadomości e-mail zawierające adresy URL wyłudające informacje usunięte po** dostarczeniu (istniejące zostaną usunięte)| Zasady alertów zostały usunięte w czerwcu 2021 r. Zobacz [sekcję Co należy zrobić, aby przygotować się na te](#what-you-need-to-do-to-prepare-for-these-changes) zmiany.|
| **Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu** (istniejące zostaną usunięte) | Zasady alertów zostały usunięte w czerwcu 2021 r. Zobacz [sekcję Co należy zrobić, aby przygotować się na te](#what-you-need-to-do-to-prepare-for-these-changes) zmiany. |
|||

Zmiany ważności alertów zostaną wprowadzone we wszystkich organizacjach do 14 maja 2021 r.

## <a name="how-this-will-affect-your-organization"></a>Jak wpłynie to na Twoją organizację

Nowe alerty zaczną uruchamiać się uruchamiająco badania air w organizacji na datach wymienionych powyżej. Aby ograniczyć wpływ na organizacje zabezpieczeń, które operacyjnie aktywowały dwa alerty do usunięcia, będą widziały alerty wyzwalane przez istniejące zasady alertów oraz  alerty wyzwalane przez nowe zasady alertów między 5 kwietnia 2021 a 28 maja 2021 r. Dzięki temu zespoły zabezpieczeń mają czas na obsługę wymaganych zmian. Aby ułatwić zespołom zabezpieczeń zwiększenie liczby alertów w tym krótkim czasie, zarówno istniejące alerty, jak i nowe alerty będą skorelowane z tym samym badaniem air i skorelowane z tym samym zdarzeniem. Dotyczy to w szczególności alertów, badań AIR i zdarzeń:

- **Alerty**: W ramach istniejących i nowych alertów są domyślnie wyświetlanie następujących par alertów:

  - **Wiadomości e-mail zawierające adresy URL wyłudające informacje usunięte po dostarczeniu** ORAZ **Wiadomości e-mail zawierające złośliwy adres URL usunięte po dostarczeniu**

  - **Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu** AND **Email messages containing malicious file removed after delivery**

  ![Par alertów dla nowych i istniejących alertów.](../media/DefenderAlerts.png)

   Aby uzyskać więcej informacji na temat zarządzania tymi parami alertów, zobacz sekcję Co należy [zrobić, aby przygotować się na te zmiany](#what-you-need-to-do-to-prepare-for-these-changes) .

- **Badania AIR**: Alerty będą skorelowane z jednym badaniem AIR, przy użyciu jednego z alertów sklasyfikowanych jako "wyzwalające", a drugiego jako "powtarzające się".

  ![Pary alertów w programie AIR Investigations.](../media/AIRAlerts.png)

- **Zdarzenia**: Oba alerty są skorelowane z tym samym zdarzeniem

  ![Par alertów w zdarzeniach.](../media/IncidentsAlerts.png)

## <a name="what-you-need-to-do-to-prepare-for-these-changes"></a>Co należy zrobić, aby przygotować się na te zmiany

Sposób korzystania z tych alertów w Organizacji decyduje o tym, co należy zrobić, aby się przygotować. Jeśli alerty zostały operacyjnie zarchiwizowane i korzystasz z nich lub korzystasz z nich za pośrednictwem interfejsu API, powiadomienia e-mail alertu albo w portalu usługi Centrum zgodności platformy Microsoft 365 lub <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu</a> programu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Defender</a>, musisz zmodyfikować przepływy pracy.

**Jeśli te alerty nie zostały jeszcze operacyjne, możesz wykonać jedną z następujących czynności:**

- Wyłącz następujące zasady alertów (które są usuwane), aby zmniejszyć liczbę alertów w organizacji:

  - **Wiadomości e-mail zawierające adresy URL wyłudające informacje usunięte po dostarczeniu**

  - **Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu**

- Nic nie robisz. 28 maja 2021 r. wyłączymy istniejące zasady alertów.

**Jeśli zarchiwizowane zostały te alerty:**

- Zacznij konsumować nowe alerty w ramach przepływów pracy w przewidywaniu usunięcia istniejących zasad alertów z 28 maja 2021 r. Jeśli w systemie biletowania masz logikę niestandardową, skrzynkę pocztową zabezpieczeń, w której otrzymujesz powiadomienia e-mail alertów lub rozwiązanie SIEM zależne od nazwy alertu lub identyfikatora zasad alertu (identyfikator korelacji), musisz zmodyfikować logikę w celu uwzględnienia tej zmiany.

  > [!NOTE]
  > Informacje w alertach, badaniach i zdarzeniach nie uległy zmianie. W rzeczywistości te informacje zostały rozszerzone o dodatkowe szczegóły dotyczące zagrożeń, które są z nimi skojarzone.

- Po w modyfikowaniu możesz wyłączyć istniejące zasady alertów, aby zmniejszyć głośność alertów w organizacji:

  - **Wiadomości e-mail zawierające adresy URL wyłudające informacje usunięte po dostarczeniu**

  - **Wiadomości e-mail zawierające złośliwe oprogramowanie usunięte po dostarczeniu**

  Ewentualnie możesz pozostawić włączone te zasady alertów do momentu ich usunięcia 28 maja 2021 r.
