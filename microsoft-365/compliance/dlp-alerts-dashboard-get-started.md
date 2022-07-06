---
title: Wprowadzenie do pulpitu nawigacyjnego alertów DLP
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
description: Wprowadzenie do definiowania alertów dotyczących zasad ochrony przed utratą danych i zarządzania nimi.
ms.openlocfilehash: de980fadbc6b6091a0257c032dacab4220704f62
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625462"
---
# <a name="get-started-with-the-data-loss-prevention-alerts-dashboard"></a>Wprowadzenie do pulpitu nawigacyjnego alertów dotyczących zapobiegania utracie danych

zasady Ochrona przed utratą danych w Microsoft Purview (DLP) mogą podejmować działania ochronne, aby zapobiec niezamierzonemu udostępnianiu poufnych elementów. Po wykonaniu akcji na poufnym elemencie można otrzymywać powiadomienia, konfigurując alerty dla usługi DLP. W tym artykule przedstawiono sposób definiowania zaawansowanych zasad alertów połączonych z zasadami ochrony przed utratą danych (DLP). Zobaczysz, jak używać [pulpitu nawigacyjnego zarządzania alertami DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> do wyświetlania alertów, zdarzeń i skojarzonych metadanych naruszeń zasad DLP.

Jeśli dopiero korzystasz z alertów DLP, zapoznaj się z [pulpitem nawigacyjnym Alerty dotyczące zapobiegania utracie danych](dlp-alerts-dashboard-learn.md)

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem upewnij się, że masz wymagane wymagania wstępne:

-   Licencjonowanie pulpitu nawigacyjnego zarządzania alertami DLP
-   Licencjonowanie opcji konfiguracji alertów
-   Ról

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licencjonowanie pulpitu nawigacyjnego zarządzania alertami DLP

Wszyscy uprawnieni dzierżawcy DLP mogą uzyskać dostęp do pulpitu nawigacyjnego zarządzania alertami DLP. Aby rozpocząć pracę, należy kwalifikować się do programu Microsoft Purview DLP dla Exchange Online, sharepoint online i OneDrive dla Firm. Aby uzyskać więcej informacji na temat wymagań licencyjnych dotyczących DLP, zobacz [Jakie licencje zapewniają użytkownikowi prawa do korzystania z usługi?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Klienci korzystający z programu [Endpoint DLP](endpoint-dlp-learn-about.md) , którzy kwalifikują się do korzystania z usługi [Teams DLP](dlp-microsoft-teams.md) , zobaczą alerty zasad DLP punktu końcowego i alerty zasad DLP usługi Teams na pulpicie nawigacyjnym zarządzania alertami DLP.

Funkcja **podglądu zawartości** jest dostępna tylko dla tych licencji:

- Microsoft 365 (E5)
- Office 365 (E5)
- Dodatek Advanced Compliance (E5)
- Microsoft 365 E5/A5 Information Protection i ład
- Zgodność Microsoft 365 E5/A5

### <a name="licensing-for-alert-configuration-options"></a>Licencjonowanie opcji konfiguracji alertów

**Konfiguracja alertu pojedynczego zdarzenia**: organizacje, które mają subskrypcję E1, F1 lub G1 lub subskrypcję E3 lub G3, mogą tworzyć zasady alertów tylko wtedy, gdy alert jest wyzwalany za każdym razem, gdy występuje działanie.

**Konfiguracja zagregowanego alertu**: Aby skonfigurować zasady alertów agregujących na podstawie progu, należy wykonać jedną z następujących konfiguracji licencjonowania:

- Subskrypcja E5 lub G5
- Subskrypcja E1, F1 lub G1 albo subskrypcja E3 lub G3, która obejmuje jedną z następujących funkcji:
    - Office 365 advanced threat protection plan 2
    - Zgodność platformy Microsoft 365 E5
    - Licencja dodatku Microsoft 365 eDiscovery and Audit

### <a name="roles"></a>Ról

Jeśli chcesz wyświetlić pulpit nawigacyjny zarządzania alertami DLP lub edytować opcje konfiguracji alertów w zasadach DLP, musisz być członkiem jednej z tych grup ról:

- Administrator zgodności
- Administrator danych zgodności
- Administrator zabezpieczeń
- Operator zabezpieczeń
- Czytelnik zabezpieczeń

Aby uzyskać dostęp do pulpitu nawigacyjnego zarządzania alertami DLP, potrzebne są następujące elementy:

- Zarządzaj alertami

i jedną z tych dwóch ról:

- Zarządzanie zgodnością DLP
- zarządzanie zgodnością View-Only DLP

Aby uzyskać dostęp do funkcji podglądu zawartości i dopasowanych funkcji poufnych zawartości i kontekstu, musisz być członkiem następujących elementów:

- Grupa ról Przeglądarki zawartości Eksploratora zawartości

która ma przypisaną wstępnie rolę przeglądarki zawartości klasyfikacji danych.

### <a name="roles-and-role-groups-in-preview"></a>Role i grupy ról w wersji zapoznawczej

W wersji zapoznawczej dostępne są role i grupy ról, które można przetestować, aby dostosować mechanizmy kontroli dostępu.

Oto lista odpowiednich ról w wersji zapoznawczej. Aby dowiedzieć się więcej na ich temat, zobacz [Role w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Administracja
- analityk Information Protection
- badacz Information Protection
- czytelnik Information Protection

Oto lista odpowiednich grup ról, które są w wersji zapoznawczej. Aby dowiedzieć się więcej na ich temat, zobacz [Grupy ról w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- administratorzy Information Protection
- analitycy Information Protection
- Information Protection śledczy
- czytniki Information Protection

## <a name="dlp-alert-configuration"></a>Konfiguracja alertu DLP

Aby dowiedzieć się, jak skonfigurować alert w zasadach DLP, zobacz [Od czego zacząć od zapobiegania utracie danych](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention).

> [!IMPORTANT]
> Konfiguracja zasad przechowywania dzienników inspekcji organizacji określa, jak długo alert pozostaje widoczny w konsoli programu . Aby uzyskać więcej informacji, zobacz [Zarządzanie zasadami przechowywania dzienników inspekcji](audit-log-retention-policies.md#manage-audit-log-retention-policies) .

### <a name="aggregate-event-alert-configuration"></a>Agregowanie konfiguracji alertów o zdarzeniach

Jeśli organizacja ma licencję na [opcje konfiguracji zagregowanych alertów](#licensing-for-alert-configuration-options), te opcje zostaną wyświetlone podczas tworzenia lub edytowania zasad DLP.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Zrzut ekranu przedstawiający opcje raportów o zdarzeniach dla użytkowników, którzy kwalifikują się do zagregowanych opcji konfiguracji alertów." border="false":::

Ta konfiguracja umożliwia skonfigurowanie zasad w celu wygenerowania alertu za każdym razem, gdy działanie spełnia warunki zasad lub gdy określony próg zostanie przekroczony, na podstawie liczby działań lub na podstawie ilości danych eksfiltrowanych.

### <a name="single-event-alert-configuration"></a>Konfiguracja alertu pojedynczego zdarzenia

Jeśli organizacja ma licencję na [opcje konfiguracji alertów o pojedynczym zdarzeniu](#licensing-for-alert-configuration-options), te opcje zostaną wyświetlone podczas tworzenia lub edytowania zasad DLP. Użyj tej opcji, aby utworzyć alert, który jest zgłaszany za każdym razem, gdy występuje dopasowanie regułY DLP.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Zrzut ekranu przedstawiający opcje raportów o zdarzeniach dla użytkowników, którzy kwalifikują się do opcji konfiguracji alertów o pojedynczym zdarzeniu." border="false":::

## <a name="investigate-a-dlp-alert"></a>Badanie alertu DLP

Aby pracować z pulpitem nawigacyjnym zarządzania alertami DLP:

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> przejdź do obszaru **Zapobieganie utracie danych**.
2. Wybierz kartę **Alerty** , aby wyświetlić pulpit nawigacyjny alertów DLP.
3. Wybierz alert, aby wyświetlić szczegóły:

:::image type="content" source="../media/alert-details.png" alt-text="Zrzut ekranu przedstawiający szczegóły alertu na pulpicie nawigacyjnym zarządzania alertami DLP." border="false":::

4. Wybierz kartę **Zdarzenia** , aby wyświetlić wszystkie zdarzenia skojarzone z alertem. Możesz wybrać określone zdarzenie, aby wyświetlić jego szczegóły. Aby uzyskać listę niektórych dostępnych szczegółów zdarzenia, zobacz [Pulpit nawigacyjny Alerty dotyczące zapobiegania utracie danych](dlp-alerts-dashboard-learn.md).
5. Wybierz pozycję **Szczegóły** , aby otworzyć stronę **Przegląd** alertu. Strona przeglądu zawiera podsumowanie:
    1. o tym, co się stało
    1. kto wykonał akcje, które spowodowały dopasowanie zasad
    1. informacje o dopasowanych zasadach i nie tylko 

6. Wybierz kartę **Zdarzenia** , aby uzyskać dostęp do:
    1. zawartość
    1. dopasowane typy informacji poufnych
    1. Metadanych

7. Wybierz kartę **Typy informacji poufnych** , aby wyświetlić szczegóły dotyczące typów informacji poufnych wykrytych w zawartości. Szczegóły obejmują pewność siebie, liczbę i zawartość zgodną z typem informacji poufnych.

8. Po zbadaniu alertu wróć do karty **Przegląd** , na której możesz zarządzać klasyfikacją i zarządzać dyspozycją alertu oraz dodawać komentarze.

- Aby wyświetlić historię zarządzania przepływami pracy, wybierz pozycję **Dziennik zarządzania**.
- Po wykonaniu wymaganej akcji dla alertu ustaw stan alertu na **Rozwiązano**.

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o alertach zapobiegania utracie danych i pulpicie nawigacyjnym alertów](dlp-alerts-dashboard-learn.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
