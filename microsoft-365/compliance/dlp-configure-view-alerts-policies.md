---
title: Konfigurowanie i wyświetlanie alertów dla zasad DLP
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
description: Dowiedz się, jak definiować alerty dotyczące zasad ochrony przed utratą danych i zarządzać nimi.
ms.openlocfilehash: 60d5188b9288b1e131e36e145f7abb98a34d5ead
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627652"
---
# <a name="configure-and-view-alerts-for-data-loss-prevention-polices"></a>Konfigurowanie i wyświetlanie alertów dotyczących zasad ochrony przed utratą danych

zasady Ochrona przed utratą danych w Microsoft Purview (DLP) mogą podejmować działania ochronne, aby zapobiec niezamierzonemu udostępnianiu poufnych elementów. Po wykonaniu akcji na poufnym elemencie można otrzymywać powiadomienia, konfigurując alerty dla usługi DLP. W tym artykule przedstawiono sposób definiowania zaawansowanych zasad alertów połączonych z zasadami ochrony przed utratą danych (DLP). Zobaczysz, jak używać nowego pulpitu nawigacyjnego zarządzania alertami DLP w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> do wyświetlania alertów, zdarzeń i skojarzonych metadanych naruszeń zasad DLP.

## <a name="features"></a>Funkcje

Poniżej przedstawiono następujące funkcje:

-   **Pulpit nawigacyjny zarządzania alertami DLP**: na <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> ten pulpit nawigacyjny zawiera alerty dotyczące zasad DLP, które są wymuszane w następujących obciążeniach:

    -   Exchange
    -   SharePoint
    -   OneDrive
    -   Teams
    -   Urządzeń
-   **Zaawansowane opcje konfiguracji alertów**: te opcje są częścią przepływu tworzenia zasad DLP. Użyj ich do tworzenia rozbudowanych konfiguracji alertów. Alert z pojedynczym zdarzeniem lub alert zagregowany można utworzyć na podstawie liczby zdarzeń lub rozmiaru wyciekłych danych.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem upewnij się, że masz wymagane wymagania wstępne:

-   Licencjonowanie pulpitu nawigacyjnego zarządzania alertami DLP
-   Licencjonowanie opcji konfiguracji alertów
-   Ról

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licencjonowanie pulpitu nawigacyjnego zarządzania alertami DLP

Wszystkie kwalifikujące się dzierżawy Office 365 DLP mogą uzyskać dostęp do nowego pulpitu nawigacyjnego zarządzania alertami DLP. Aby rozpocząć pracę, należy kwalifikować się do Office 365 DLP dla usług Exchange Online, SharePoint Online i OneDrive dla Firm. Aby uzyskać więcej informacji na temat wymagań licencyjnych dotyczących Office 365 DLP, zobacz [Jakie licencje zapewniają użytkownikowi prawa do korzystania z usługi?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Klienci korzystający z programu [Endpoint DLP](endpoint-dlp-learn-about.md) , którzy kwalifikują się do korzystania z usługi [Teams DLP](dlp-microsoft-teams.md) , zobaczą alerty zasad DLP punktu końcowego i alerty zasad DLP usługi Teams na pulpicie nawigacyjnym zarządzania alertami DLP.

### <a name="licensing-for-alert-configuration-options"></a>Licencjonowanie opcji konfiguracji alertów

- **Konfiguracja alertu pojedynczego zdarzenia**: organizacje, które mają subskrypcję E1, F1 lub G1 lub subskrypcję E3 lub G3, mogą tworzyć zasady alertów tylko wtedy, gdy alert jest wyzwalany za każdym razem, gdy występuje działanie.
- **Zagregowana konfiguracja alertów**: Aby skonfigurować zasady alertów agregujących na podstawie progu, musisz mieć jedną z następujących konfiguracji:
  - Subskrypcja E5 lub G5
  - Subskrypcja E1, F1 lub G1 albo subskrypcja E3 lub G3, która obejmuje jedną z następujących funkcji:
    - Office 365 advanced threat protection plan 2
    - Zgodność platformy Microsoft 365 E5
    - Licencja dodatku Microsoft 365 eDiscovery and Audit

### <a name="roles"></a>Ról

Jeśli chcesz wyświetlić pulpit nawigacyjny zarządzania alertami DLP lub edytować opcje konfiguracji alertów w zasadach DLP, musisz być członkiem jednej z tych grup ról:

-   Administrator zgodności
-   Administrator danych zgodności
-   Administrator zabezpieczeń
-   Operator zabezpieczeń
-   Czytelnik zabezpieczeń

Aby uzyskać dostęp do pulpitu nawigacyjnego zarządzania alertami DLP, potrzebna jest rola Zarządzanie alertami i dowolna z następujących ról:

-   Zarządzanie zgodnością DLP
-   zarządzanie zgodnością View-Only DLP

## <a name="alert-configuration-experience"></a>Środowisko konfiguracji alertów

Jeśli kwalifikujesz się do [zagregowanych opcji konfiguracji alertów](#licensing-for-alert-configuration-options), w środowisku tworzenia zasad DLP zostaną wyświetlone następujące opcje.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Zrzut ekranu przedstawiający opcje raportów o zdarzeniach dla użytkowników, którzy kwalifikują się do zagregowanych opcji konfiguracji alertów." border="false":::

Ta konfiguracja umożliwia skonfigurowanie zasad w celu wygenerowania alertu:

- za każdym razem, gdy działanie jest zgodne z warunkami zasad
- gdy zdefiniowany próg zostanie osiągnięty lub przekroczony
- na podstawie liczby działań
- na podstawie ilości danych eksfiltrowanych

Aby zapobiec zalewowi wiadomości e-mail z powiadomieniami, wszystkie dopasowania, które występują w ciągu jednej minuty i są dla tej samej reguły DLP i w tej samej lokalizacji, są grupowane razem w tym samym alercie. Funkcja przedziału czasu agregacji jednej minuty jest dostępna w następujących miejscach: 

- Subskrypcja E5 lub G5
- Subskrypcja E1, F1 lub G1 albo subskrypcja E3 lub G3, która obejmuje jedną z następujących funkcji:
    - Office 365 advanced threat protection plan 2
    - Zgodność platformy Microsoft 365 E5
    - Licencja dodatku Microsoft 365 eDiscovery and Audit
 
W przypadku organizacji, które mają subskrypcję E1, F1 lub G1 albo subskrypcję E3 lub G3, przedział czasu agregacji wynosi 15 minut.

## <a name="dlp-alert-management-dashboard"></a>Pulpit nawigacyjny zarządzania alertami DLP

Aby pracować z pulpitem nawigacyjnym zarządzania alertami DLP:

1.  W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> przejdź do obszaru **Zapobieganie utracie danych**.

2.  Wybierz kartę **Alerty** , aby wyświetlić pulpit nawigacyjny alertów DLP.

    -   Wybierz filtry, aby uściślić listę alertów. Wybierz pozycję **Dostosuj kolumny** , aby wyświetlić listę właściwości, które chcesz wyświetlić. Możesz również posortować alerty w kolejności rosnącej lub malejącej w dowolnej kolumnie.
    -   Wybierz alert, aby wyświetlić szczegóły:

        :::image type="content" source="../media/alert-details.png" alt-text="Zrzut ekranu przedstawiający szczegóły alertu na pulpicie nawigacyjnym zarządzania alertami DLP." border="false":::

1.  Wybierz kartę **Zdarzenia** , aby wyświetlić wszystkie zdarzenia skojarzone z alertem. Możesz wybrać określone zdarzenie, aby wyświetlić jego szczegóły. W poniższej tabeli przedstawiono niektóre szczegóły zdarzenia.
    
    | Kategoria          | Nazwa właściwości                 | Opis                                                                | Odpowiednie typy zdarzeń                   |
    |-------------------|-------------------------------|----------------------------------------------------------------------------|------------------------------------------|
    |*Szczegóły zdarzenia*||
    |      | Id                            | Unikatowy identyfikator skojarzony ze zdarzeniem                                        | Wszystkie zdarzenia                               |
    |                   | Lokalizacja                      | Obciążenie, w którym wykryto zdarzenie                                      | Wszystkie zdarzenia                               |
    |                   | Czas działania              | Czas działania użytkownika, które spowodowało naruszenie DLP                    | Wszystkie zdarzenia                               |
    |*Jednostki, na które ma to wpływ*||
    |  | Użytkownik                          | Użytkownik, który spowodował naruszenie DLP                                          | Wszystkie zdarzenia                               |
    |                   | Nazwa hosta                      | Nazwa hosta maszyny, na której wykryto naruszenie DLP              | Zdarzenia urządzeń                           |
    |                   | Adres IP                    | Adres IP maszyny                                                  | Zdarzenia urządzeń                           |
    |                   | Ścieżka pliku                     | Ścieżka bezwzględna pliku biorącego udział w naruszeniu                        | Zdarzenia programu SharePoint, usługi OneDrive i urządzeń |
    |                   | Adresaci wiadomości e-mail              | Adresaci wiadomości e-mail, która naruszyła zasady DLP                       | Zdarzenia programu Exchange                          |
    |                   | Temat wiadomości e-mail                 | Temat wiadomości e-mail, która naruszyła zasady DLP                          | Zdarzenia programu Exchange                          |
    |                   | Załączniki wiadomości e-mail             | Nazwy załączników w wiadomości e-mail, które naruszyły zasady DLP         | Zdarzenia programu Exchange                          |
    |                   | Właściciel witryny                    | Nazwa właściciela witryny                                                     | Zdarzenia programu SharePoint i usługi OneDrive           |
    |                   | Adres URL witryny                      | Pełny adres URL witryny programu SharePoint lub usługi OneDrive                                | Zdarzenia programu SharePoint i usługi OneDrive           |
    |                   | Utworzony plik                  | Czas tworzenia pliku                                                      | Zdarzenia programu SharePoint i usługi OneDrive           |
    |                   | Ostatnia modyfikacja pliku            | Czas ostatniej modyfikacji pliku                                  | Zdarzenia programu SharePoint i usługi OneDrive           |
    |                   | Rozmiar pliku                     | Rozmiar pliku                                                           | Zdarzenia programu SharePoint i usługi OneDrive           |
    |                   | Właściciel pliku                    | Właściciel pliku                                                          | Zdarzenia programu SharePoint i usługi OneDrive           |
    |*Szczegóły zasad*||
    |     | Dopasowane zasady DLP            | Nazwa dopasowanych zasad DLP                                    | Wszystkie zdarzenia                               |
    |                   | Dopasowana reguła                  | Nazwa reguły DLP w dopasowanych zasadach DLP                    | Wszystkie zdarzenia                               |
    |                   | Wykryto typy informacji poufnych | Typy informacji poufnych, które zostały wykryte w ramach zasad DLP | Wszystkie zdarzenia                               |
    |                   | Podjęte działania                 | Akcje podejmowane w ramach dopasowanych zasad DLP                          | Wszystkie zdarzenia                               |
    |                   | Zasady zastępowania użytkowników          | Czy użytkownik przekroczył zasady za pośrednictwem porady dotyczącej zasad                | Wszystkie zdarzenia                               |
    |                   | Zastępowanie tekstu uzasadnienia   | Uzasadnienie, które ma zastąpić poradę dotyczącą zasad                          | Wszystkie zdarzenia                               |
    
1.  Wybierz kartę **Typy informacji poufnych** , aby wyświetlić szczegóły dotyczące typów informacji poufnych wykrytych w zawartości. Szczegóły obejmują pewność siebie i liczbę.

2.  Po zbadaniu alertu wybierz pozycję **Zarządzaj alertem** , aby zmienić stan (**Aktywny**, **Badanie**, **Odrzucony** lub **Rozwiązany**). Możesz również dodać komentarze i przypisać alert do kogoś w organizacji.

    -   Aby wyświetlić historię zarządzania przepływami pracy, wybierz pozycję **Dziennik zarządzania**.
    -   Po wykonaniu wymaganej akcji dla alertu ustaw stan alertu na **Rozwiązano**.
