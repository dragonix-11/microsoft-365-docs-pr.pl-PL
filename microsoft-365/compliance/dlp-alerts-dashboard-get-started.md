---
title: Wprowadzenie do pulpitu nawigacyjnego alertów ochrony przed utratą danych
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
description: Wprowadzenie do definiowania alertów i zarządzania nimi w celu ochrony przed utratą danych.
ms.openlocfilehash: d295a04c27231b937ca552feb06628f857528e34
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009834"
---
# <a name="get-started-with-the-data-loss-prevention-alert-dashboard"></a>Wprowadzenie do pulpitu nawigacyjnego alertów ochrony przed utratą danych

Zasady ochrony przed utratą danych (DLP, Data loss prevention) mogą zapobiegać niezamierzonemu udostępnianiu poufnych elementów. Jeśli zostanie wykonane działanie na poufnym elementie, możesz uzyskać powiadomienie, konfigurując alerty dotyczące zasad DLP. W tym artykule pokazano, jak zdefiniować rozbudowane zasady alertów, które są połączone z zasadami ochrony przed utratą danych (DLP). Dowiesz się, jak za pomocą pulpitu nawigacyjnego zarządzania [alertami DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) w aplikacji Centrum zgodności platformy Microsoft 365 wyświetlać alerty, zdarzenia i skojarzone metadane dla naruszeń zasad DLP.<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank"></a>

Jeśli nie masz jeszcze dostępu do alertów ochrony przed utratą danych, zapoznaj się z informacjami na temat pulpitu nawigacyjnego alertów ochrony [przed utratą danych.](dlp-alerts-dashboard-learn.md)

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem upewnij się, że są wymagane wymagania wstępne:

-   Licencjonowanie pulpitu nawigacyjnego zarządzania alertami DLP
-   Licencjonowanie opcji konfiguracji alertów
-   Role

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>Licencjonowanie pulpitu nawigacyjnego zarządzania alertami DLP

Wszystkie dzierżawy, które są uprawnione do Office 365 DLP, mogą uzyskać dostęp do pulpitu nawigacyjnego zarządzania alertami DLP. Aby rozpocząć, warto mieć uprawnienia do korzystania z zasad Office 365 DLP dla usług Exchange Online, SharePoint Online i OneDrive dla Firm. Aby uzyskać więcej informacji na temat wymagań licencjonowania dotyczących usługi Office 365 DLP, zobacz Które licencje zapewniają użytkownikowi prawa do korzystania [z usługi?](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

Klienci, którzy używają funkcji [DLP](endpoint-dlp-learn-about.md) punktu końcowego, którzy są uprawnieni do korzystania z usługi [Teams DLP](dlp-microsoft-teams.md), zobaczą alerty zasad DLP punktu końcowego oraz alerty zasad DLP Teams na pulpicie nawigacyjnym zarządzania alertami DLP.

Funkcja **podglądu** zawartości jest dostępna tylko dla tych licencji:

- Microsoft 365 (E5)
- Office 365 (E5)
- Dodatek Advanced Compliance (E5)
- Microsoft 365 E5/A5 Ochrona informacji i zarządzanie informacjami
- zgodność Microsoft 365 E5/A5

### <a name="licensing-for-alert-configuration-options"></a>Licencjonowanie opcji konfiguracji alertów

**Konfiguracja** alertów zdarzeń pojedynczych: Organizacje z subskrypcją E1, F1 lub G1 albo subskrypcją E3 lub G3 mogą tworzyć zasady alertów tylko wtedy, gdy alert jest wyzwalany za każdym razem, gdy występuje działanie.

**Zagregowana konfiguracja alertów**: Aby skonfigurować zagregowane zasady alertów na podstawie progu, musisz wykonać jedną z tych konfiguracji licencjonowania:

- Subskrypcja E5 lub G5
- Subskrypcja E1, F1 lub G1 albo subskrypcja E3 lub G3, która zawiera jedną z następujących funkcji:
    - Office 365 Zaawansowanej ochrony przed zagrożeniami (Plan 2)
    - Zgodność platformy Microsoft 365 E5
    - Microsoft 365 zbierania elektronicznych materiałów dowodowych i licencji dodatku Inspekcja

### <a name="roles"></a>Role

Jeśli chcesz wyświetlić pulpit nawigacyjny zarządzania alertami DLP lub edytować opcje konfiguracji alertów w zasadach DLP, musisz być członkiem jednej z tych grup ról:

- Administrator zgodności
- Administrator danych dotyczących zgodności
- Administrator zabezpieczeń
- Operator zabezpieczeń
- Czytnik zabezpieczeń

Aby uzyskać dostęp do pulpitu nawigacyjnego zarządzania alertami DLP, potrzebujesz:

- Zarządzanie alertami

i jedną z tych dwóch ról:

- Zarządzanie zgodnością DLP
- View-Only zarządzania zgodnością DLP

Aby uzyskać dostęp do funkcji Podgląd zawartości oraz dopasowanej poufnej zawartości i funkcji kontekstowych, musisz być członkiem:

- Grupa ról Podgląd zawartości w Eksploratorze zawartości

która wstępnie przypisana jest rola podglądu zawartości klasyfikacji danych.

### <a name="roles-and-role-groups-in-preview"></a>Role i grupy ról w wersji Preview

W wersji Preview są dostępne role i grupy ról, które możesz przetestować, aby precyzyjnie dostosować kontrolki dostępu.

Oto lista dostępnych w wersji Microsoft Information Protection (MIP), które są dostępne w wersji zapoznawczej. Aby dowiedzieć się więcej na ich temat, zobacz [Role w Centrum & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administrator ochrony informacji
- Analityk ochrony informacji
- Ochrona informacji
- Czytnik ochrony informacji

Poniżej znajdziesz listę grup ról miP, które są dostępne w wersji Preview. Aby dowiedzieć się więcej na ten temat, [zobacz Grupy ról w Centrum & zabezpieczeń.](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Ochrona informacji
- Administratorzy ochrony informacji
- Analitycy ochrony informacji
- Schoweki ochrony informacji
- Czytniki informacji

## <a name="dlp-alert-configuration"></a>Konfiguracja alertu DLP

Aby dowiedzieć się, jak skonfigurować alert w zasadach ochrony przed utratą danych, zobacz Od czego zacząć [od ochrony przed utratą danych](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention).

> [!IMPORTANT]
> Konfiguracja zasad przechowywania dziennika inspekcji organizacji steruje tym, jak długo alert pozostaje widoczny w konsoli. Aby uzyskać więcej informacji, zobacz Zarządzanie [zasadami przechowywania dziennika](audit-log-retention-policies.md#manage-audit-log-retention-policies) inspekcji.

### <a name="aggregate-event-alert-configuration"></a>Agregowanie konfiguracji alertów o zdarzeniu

Jeśli Twoja organizacja ma licencję na zagregowane [opcje konfiguracji alertów](#licensing-for-alert-configuration-options), te opcje będą dostępne podczas tworzenia lub edytowania zasad DLP.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="Zrzut ekranu przedstawiający opcje raportów o incydentach dla użytkowników, którzy kwalifikują się do opcji konfiguracji alertów zagregowanych." border="false":::

Ta konfiguracja umożliwia skonfigurowanie zasad w celu generowania alertu za każdym razem, gdy działanie jest takie, jakie są spełnione lub gdy przekroczono określony próg, na podstawie liczby działań lub na podstawie liczby przefiltrowanych danych.

### <a name="single-event-alert-configuration"></a>Konfiguracja alertów o jednym zdarzeniu

Jeśli Twoja organizacja ma licencję na opcje konfiguracji [alertów](#licensing-for-alert-configuration-options) zdarzeń pojedynczych, te opcje będą dostępne podczas tworzenia lub edytowania zasad DLP. Użyj tej opcji, aby utworzyć alert, który będzie uruchamiany za każdym razem, gdy reguła DLP będzie odpowiadać.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="Zrzut ekranu przedstawiający opcje raportów o incydentach dla użytkowników, którzy kwalifikują się do opcji konfiguracji alertów zdarzeń pojedynczych." border="false":::

## <a name="investigate-a-dlp-alert"></a>Badanie alertu DLP

Aby pracować z pulpitem nawigacyjnym zarządzania alertami DLP:

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365 przejdź</a> do **tematu Ochrona przed utratą danych**.
2. Wybierz **kartę Alerty** , aby wyświetlić pulpit nawigacyjny alertów DLP.
3. Wybierz alert, aby wyświetlić szczegóły:

:::image type="content" source="../media/alert-details.png" alt-text="Zrzut ekranu przedstawiający szczegóły alertów na pulpicie nawigacyjnym zarządzania alertami DLP." border="false":::

4. Wybierz **kartę Zdarzenia** , aby wyświetlić wszystkie zdarzenia skojarzone z alertem. Możesz wybrać konkretne zdarzenie, aby wyświetlić jego szczegóły. Aby uzyskać listę niektórych dostępnych szczegółów zdarzenia, zobacz Informacje na temat pulpitu nawigacyjnego alertów [ochrony przed utratą danych](dlp-alerts-dashboard-learn.md).
5. Wybierz **pozycję Szczegóły** , aby otworzyć **stronę Przegląd** alertu. Strona przeglądu zawiera podsumowanie:
    1. co się stało
    1. kto wykonał działania, które spowodowały dopasowanie zasad
    1. informacje o dopasowanych zasadach i nie tylko 

6. Wybierz **kartę Zdarzenia** , aby uzyskać dostęp do:
    1. zawartość
    1. Dopasowane typy informacji poufnych
    1. metadane

7. Wybierz **kartę Typy informacji poufnych** , aby wyświetlić szczegółowe informacje o typach informacji poufnych wykrytych w zawartości. Szczegóły obejmują ufność, liczbę oraz zawartość, która jest taka, jaka jest taka, jak typ informacji poufnych.

8. Po zbadaniu alertu wróć do karty Przegląd, na której możesz zarządzać sprawdzaniem i ich rozsyłaniem oraz dodawać komentarze.

- Aby wyświetlić historię zarządzania przepływem pracy, wybierz pozycję **Dziennik zarządzania**.
- Po podjęciu wymaganej akcji dla alertu ustaw stan alertu na **Rozwiązano**.

## <a name="see-also"></a>Zobacz też

- [Informacje na temat alertów ochrony przed utratą danych i pulpitu nawigacyjnego alertów](dlp-alerts-dashboard-learn.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
