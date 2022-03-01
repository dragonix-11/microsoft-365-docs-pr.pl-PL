---
title: Konfigurowanie i wyświetlanie alertów dotyczących zasad ochrony przed utratą danych
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Dowiedz się, jak definiować alerty na temat zasad ochrony przed utratą danych i zarządzać nimi.
ms.openlocfilehash: 9b8ee897502f76dbdb63e3fbac99e4223f378a1a
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017847"
---
# <a name="configure-and-view-alerts-for-data-loss-prevention-polices"></a>Konfigurowanie i wyświetlanie alertów dotyczących zasad ochrony przed utratą danych

Zasady ochrony przed utratą danych (DLP, Data loss prevention) mogą zapobiegać niezamierzonemu udostępnianiu poufnych elementów. Jeśli zostanie wykonane działanie na poufnym elementie, możesz uzyskać powiadomienie, konfigurując alerty dotyczące zasad DLP. W tym artykule pokazano, jak zdefiniować rozbudowane zasady alertów, które są połączone z zasadami ochrony przed utratą danych (DLP). Dowiesz się, jak za pomocą nowego pulpitu nawigacyjnego zarządzania alertami DLP w aplikacji usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> wyświetlać alerty, zdarzenia i skojarzone metadane dotyczące naruszeń zasad DLP.

## <a name="features"></a>Funkcje

W tym celu są dostępne następujące funkcje:

-   **Pulpit nawigacyjny alertów DLP**: na <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank"></a>Centrum zgodności platformy Microsoft 365 pulpitu nawigacyjnego są Centrum zgodności platformy Microsoft 365 alerty dotyczące zasad DLP, które są wymuszane dla następujących obciążeń:

    -   Exchange
    -   SharePoint
    -   OneDrive
    -   Teams
    -   Urządzenia
-   **Zaawansowane opcje konfiguracji alertów**: Te opcje są częścią przepływu tworzenia zasad DLP. Za ich pomocą można tworzyć rozbudowane konfiguracje alertów. Możesz utworzyć alert pojedynczego zdarzenia lub zagregowany alert na podstawie liczby zdarzeń lub rozmiaru wyciekanych danych.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem upewnij się, że są wymagane wymagania wstępne:

-   Licencjonowanie pulpitu nawigacyjnego zarządzania alertami DLP
-   Licencjonowanie opcji konfiguracji alertów
-   Role

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licencjonowanie pulpitu nawigacyjnego zarządzania alertami DLP

Wszystkie dzierżawy, które są uprawnione do Office 365 DLP, mogą uzyskać dostęp do nowego pulpitu nawigacyjnego zarządzania alertami DLP. Aby rozpocząć, warto mieć uprawnienia do korzystania z zasad Office 365 DLP dla usług Exchange Online, SharePoint Online i OneDrive dla Firm. Aby uzyskać więcej informacji na temat wymagań licencjonowania dotyczących usługi Office 365 DLP, zobacz Które licencje zapewniają użytkownikowi prawa do korzystania [z usługi?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Klienci, którzy używają funkcji [DLP](endpoint-dlp-learn-about.md) punktu końcowego, którzy są uprawnieni do korzystania z usługi [Teams DLP](dlp-microsoft-teams.md), zobaczą alerty zasad DLP punktu końcowego oraz alerty zasad DLP Teams na pulpicie nawigacyjnym zarządzania alertami DLP.

### <a name="licensing-for-alert-configuration-options"></a>Licencjonowanie opcji konfiguracji alertów

- **Konfiguracja** alertów zdarzeń pojedynczych: Organizacje z subskrypcją E1, F1 lub G1 albo subskrypcją E3 lub G3 mogą tworzyć zasady alertów tylko wtedy, gdy alert jest wyzwalany za każdym razem, gdy występuje działanie.
- **Zagregowana konfiguracja alertów**: Aby skonfigurować zagregowane zasady alertów na podstawie progu, musisz mieć jedną z następujących konfiguracji:
  - Subskrypcja E5 lub G5
  - Subskrypcja E1, F1 lub G1 albo subskrypcja E3 lub G3, która zawiera jedną z następujących funkcji:
    - Office 365 Zaawansowanej ochrony przed zagrożeniami (Plan 2)
    - Zgodność platformy Microsoft 365 E5
    - Microsoft 365 zbierania elektronicznych materiałów dowodowych i licencji dodatku Inspekcja

### <a name="roles"></a>Role

Jeśli chcesz wyświetlić pulpit nawigacyjny zarządzania alertami DLP lub edytować opcje konfiguracji alertów w zasadach DLP, musisz być członkiem jednej z tych grup ról:

-   Administrator zgodności
-   Administrator danych dotyczących zgodności
-   Administrator zabezpieczeń
-   Operator zabezpieczeń
-   Czytnik zabezpieczeń

Aby uzyskać dostęp do pulpitu nawigacyjnego zarządzania alertami DLP, potrzebujesz roli Zarządzanie alertami i jednej z następujących ról:

-   Zarządzanie zgodnością DLP
-   View-Only zarządzania zgodnością DLP

## <a name="alert-configuration-experience"></a>Środowisko konfiguracji alertów

Jeśli kwalifikujesz się do opcji konfiguracji [alertów](#licensing-for-alert-configuration-options) zagregowanych, w środowisko tworzenia zasad DLP zobaczysz następujące opcje w tekście.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Zrzut ekranu przedstawiający opcje raportów o incydentach dla użytkowników, którzy kwalifikują się do opcji konfiguracji alertów zagregowanych." border="false":::

Ta konfiguracja umożliwia skonfigurowanie zasad na podstawie wygenerowania alertu:

- za każdym razem, gdy działanie jest spełnione warunki zasad
- po przekroczeniu lub przekroczeniu zdefiniowanego progu
- na podstawie liczby działań
- na podstawie liczby przefiltrowanych danych

Aby zapobiec zalaniu wiadomości e-mail powiadomień, wszystkie dopasowania, które występują w ciągu jednej minuty i są dla tej samej reguły DLP i w tej samej lokalizacji, są grupowane razem w tym samym alercie. Funkcja minutowego okna agregacji jest dostępna w: 

- Subskrypcja E5 lub G5
- Subskrypcja E1, F1 lub G1 albo subskrypcja E3 lub G3, która zawiera jedną z następujących funkcji:
    - Office 365 Zaawansowanej ochrony przed zagrożeniami (Plan 2)
    - Zgodność platformy Microsoft 365 E5
    - Microsoft 365 zbierania elektronicznych materiałów dowodowych i licencji dodatku Inspekcja
 
W przypadku organizacji, które mają subskrypcję E1, F1 lub G1 albo subskrypcję E3 lub G3, czas agregacji wynosi 15 minut.

## <a name="dlp-alert-management-dashboard"></a>Pulpit nawigacyjny zarządzania alertami DLP

Aby pracować z pulpitem nawigacyjnym zarządzania alertami DLP:

1.  W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365 przejdź</a> do **tematu Ochrona przed utratą danych**.

2.  Wybierz **kartę Alerty** , aby wyświetlić pulpit nawigacyjny alertów DLP.

    -   Wybierz filtry, aby uściślić listę alertów. Wybierz **pozycję Dostosuj kolumny** , aby wyświetlić listę właściwości, które chcesz wyświetlić. Można też sortować alerty w kolejności rosnącej lub malejącej w dowolnej kolumnie.
    -   Wybierz alert, aby wyświetlić szczegóły:

        :::image type="content" source="../media/alert-details.png" alt-text="Zrzut ekranu przedstawiający szczegóły alertów na pulpicie nawigacyjnym zarządzania alertami DLP." border="false":::

1.  Wybierz **kartę Zdarzenia** , aby wyświetlić wszystkie zdarzenia skojarzone z alertem. Możesz wybrać konkretne zdarzenie, aby wyświetlić jego szczegóły. W poniższej tabeli przedstawiono niektóre szczegóły zdarzenia.
    
    | Kategoria          | Nazwa właściwości                 | Opis                                                                | Odpowiednie typy zdarzeń                   |
    |-------------------|-------------------------------|----------------------------------------------------------------------------|------------------------------------------|
    |*Szczegóły zdarzenia*||
    |      | Identyfikator                            | Unikatowy identyfikator skojarzony ze zdarzeniem                                        | Wszystkie zdarzenia                               |
    |                   | Lokalizacja                      | Obciążenie pracą, w przypadku którego zdarzenie zostało wykryte                                      | Wszystkie zdarzenia                               |
    |                   | Czas działania              | Czas działania użytkownika, które spowodowało naruszenie zasad DLP                    | Wszystkie zdarzenia                               |
    |*Jednostki, których to wpływa*||
    |  | Użytkownik                          | Użytkownik, który spowodował naruszenie zasad DLP                                          | Wszystkie zdarzenia                               |
    |                   | Nazwa hosta                      | Nazwa hosta komputera, na którym wykryto naruszenie zasad DLP              | Zdarzenia urządzeń                           |
    |                   | Adres IP                    | Adres IP komputera                                                  | Zdarzenia urządzeń                           |
    |                   | Ścieżka pliku                     | Ścieżka bezwzględna pliku, w przypadku których dotyczy naruszenie                        | SharePoint, OneDrive i Urządzenia |
    |                   | Adresaci wiadomości e-mail              | Adresaci wiadomości e-mail, którzy naruszali zasady DLP                       | Exchange zdarzenia                          |
    |                   | Temat wiadomości e-mail                 | Temat wiadomości e-mail, która naruszyła zasady DLP                          | Exchange zdarzenia                          |
    |                   | Załączniki wiadomości e-mail             | Nazwy załączników w wiadomości e-mail, które naruszyły zasady DLP         | Exchange zdarzenia                          |
    |                   | Właściciel witryny                    | Nazwa właściciela witryny                                                     | SharePoint i OneDrive zdarzenia           |
    |                   | Adres URL witryny                      | Pełny adres URL SharePoint lub OneDrive witryny                                | SharePoint i OneDrive zdarzenia           |
    |                   | Utworzono plik                  | Godzina utworzenia pliku                                                      | SharePoint i OneDrive zdarzenia           |
    |                   | Plik z ostatnią modyfikacją            | Godzina ostatniej modyfikacji pliku                                  | SharePoint i OneDrive zdarzenia           |
    |                   | Rozmiar pliku                     | Rozmiar pliku                                                           | SharePoint i OneDrive zdarzenia           |
    |                   | Właściciel pliku                    | Właściciel pliku                                                          | SharePoint i OneDrive zdarzenia           |
    |*Szczegóły zasad*||
    |     | Dopasowane zasady DLP            | Nazwa dopasowanej zasady DLP                                    | Wszystkie zdarzenia                               |
    |                   | Reguła dopasowana                  | Nazwa reguły DLP w dopasowanych zasadach DLP                    | Wszystkie zdarzenia                               |
    |                   | Wykryte typy informacji poufnych | Typy informacji poufnych wykryte w ramach zasad DLP | Wszystkie zdarzenia                               |
    |                   | Wykonane działania                 | Akcje podejmowane w ramach dopasowanej zasady DLP                          | Wszystkie zdarzenia                               |
    |                   | Zasady dotyczące overrode użytkowników          | Czy użytkownik nie korzysta z zasad za pośrednictwem porady dotyczącej zasad                | Wszystkie zdarzenia                               |
    |                   | Zastępowanie tekstu justowania   | Uzasadnienie zastąpienia porady dotyczącej zasad                          | Wszystkie zdarzenia                               |
    
1.  Wybierz **kartę Typy informacji poufnych** , aby wyświetlić szczegółowe informacje o typach informacji poufnych wykrytych w zawartości. Szczegóły obejmują ufność i liczbę.

2.  Po zbadaniu alertu wybierz pozycję Zarządzaj **alertem** , aby zmienić **stan (Aktywne**, **Badanie**, **Odrzucone** lub **Rozwiązane**). Możesz również dodawać komentarze i przypisywać alerty do osób w organizacji.

    -   Aby wyświetlić historię zarządzania przepływem pracy, wybierz pozycję **Dziennik zarządzania**.
    -   Po podjęciu wymaganej akcji dla alertu ustaw stan alertu na **Rozwiązano**.
