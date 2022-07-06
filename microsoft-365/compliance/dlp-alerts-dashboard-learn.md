---
title: Dowiedz się więcej o pulpicie nawigacyjnym alertów DLP
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
description: Dowiedz się więcej o alertach zapobiegania utracie danych i pulpicie nawigacyjnym alertów.
ms.openlocfilehash: 1551b247e3302af6dc8ed9af62a88f2c24415122
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636166"
---
# <a name="learn-about-the-data-loss-prevention-alerts-dashboard"></a>Dowiedz się więcej o pulpicie nawigacyjnym alertów ochrony przed utratą danych

Gdy kryteria w zasadach Ochrona przed utratą danych w Microsoft Purview (DLP) są dopasowane do akcji wykonywanych przez użytkownika w przypadku elementu poufnego, zasady mogą generować alert. Taka sytuacja może spowodować dużą liczbę alertów. Alerty DLP są zbierane na pulpicie nawigacyjnym alertów. Pulpit nawigacyjny alertów zapewnia pojedyncze miejsce do dokładnego zbadania wszystkich szczegółów dotyczących dopasowania zasad.  

<!-- [Microsoft Purview compliance portal](https://compliance.microsoft.com/)-->

## <a name="workloads"></a>Obciążeń

[Pulpit nawigacyjny zarządzania alertami DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> zawiera alerty dotyczące zasad DLP dla tych obciążeń:

- Exchange
- SharePoint
- OneDrive
- Teams
- urządzenia Windows 10 

> [!TIP]
> Klienci korzystający z programu [Endpoint DLP](endpoint-dlp-learn-about.md) , którzy kwalifikują się do korzystania z usługi [Teams DLP](dlp-microsoft-teams.md) , zobaczą alerty zasad DLP punktu końcowego i alerty zasad DLP usługi Teams na pulpicie nawigacyjnym zarządzania alertami DLP.

## <a name="single-alert-and-aggregate-alert"></a>Pojedynczy alert i alert agregacji

Istnieją dwa typy alertów, które można skonfigurować w zasadach DLP.

**Alerty z pojedynczym zdarzeniem** są zwykle używane w zasadach, które monitorują wysoce poufne zdarzenia występujące w małej ilości, takie jak pojedyncza wiadomość e-mail z co najmniej 10 numerami kart kredytowych klienta wysyłanymi poza organizację.

**Alerty agregacji zdarzeń** są zwykle używane w zasadach, które monitorują zdarzenia występujące w większym woluminie w danym okresie. Na przykład alert agregowany może zostać wyzwolony, gdy 10 pojedynczych wiadomości e-mail z jednym numerem karty kredytowej klienta zostanie wysłanych poza organizację w ciągu 48 godzin.

## <a name="types-of-events"></a>Typy zdarzeń

Poniżej przedstawiono niektóre zdarzenia skojarzone z alertem. W interfejsie użytkownika możesz wybrać określone zdarzenie, aby wyświetlić jego szczegóły. 

### <a name="event-details"></a>Szczegóły zdarzenia

|Nazwa właściwości  |Opis  |Typy zdarzeń  |
|---------|---------|---------|
|ID |unikatowy identyfikator skojarzony ze zdarzeniem |wszystkie zdarzenia |
|Lokalizacja |obciążenie, w którym wykryto zdarzenie|wszystkie zdarzenia |
|czas działania     |czas działania użytkownika zgodny z kryteriami zasad DLP |

### <a name="affected-entities"></a>Jednostki, których dotyczy problem

|Nazwa właściwości |Opis| Typy zdarzeń|
|---------|---------|---------|
|Użytkownika | użytkownik, który wykonał akcję, która spowodowała dopasowanie zasad | wszystkie zdarzenia|
|Nazwa hosta | nazwa hosta komputera, na którym wystąpiło dopasowanie zasad DLP | zdarzenia urządzenia|
|Adres IP | Adres IP komputera, na którym wystąpiło dopasowanie zasad DLP | zdarzenia urządzenia|
|sha1 |Skrót SHA-1 pliku | zdarzenia urządzenia|
|sha256 | Skrót SHA-256 pliku | zdarzenia urządzenia|
|Identyfikator urządzenia MDATP | identyfikator MDATP urządzenia punktu końcowego|
|rozmiar pliku | rozmiar pliku| Zdarzenia programu SharePoint, usługi OneDrive i urządzenia|
|ścieżka pliku | ścieżka bezwzględna elementu związanego z dopasowaniem zasad DLP | Zdarzenia programu SharePoint, usługi OneDrive i urządzeń|
|adresaci poczty e-mail |Jeśli wiadomość e-mail była poufnym elementem zgodnym z zasadami DLP, to pole zawiera adresatów tej wiadomości e-mail| Zdarzenia programu Exchange|
|temat wiadomości e-mail |temat wiadomości e-mail zgodnej z zasadami DLP |Zdarzenia programu Exchange|
|załączniki wiadomości e-mail | nazwy załączników w wiadomości e-mail zgodne z zasadami DLP| Zdarzenia programu Exchange|
|właściciel witryny |nazwa właściciela witryny| Zdarzenia programu SharePoint i usługi OneDrive|
|adres URL witryny |pełny adres URL witryny programu SharePoint lub usługi OneDrive, w której wystąpiło dopasowanie zasad DLP |Zdarzenia programu SharePoint i usługi OneDrive|
|utworzony plik |czas tworzenia pliku zgodnego z zasadami DLP |Zdarzenia programu SharePoint i usługi OneDrive|
|plik ostatniej modyfikacji | czas ostatniej zmiany pliku zgodnego z zasadami DLP | Zdarzenia programu SharePoint i usługi OneDrive|
|rozmiar pliku | rozmiar pliku zgodnego z zasadami DLP |Zdarzenia programu SharePoint i usługi OneDrive|
|właściciel pliku |właściciel pliku zgodnego z zasadami DLP |Zdarzenia programu SharePoint i usługi OneDrive|  

### <a name="policy-details"></a>Szczegóły zasad

|Nazwa właściwości |Opis |Typy zdarzeń |
|---------|---------|---------|
|Dopasowane zasady DLP |nazwa dopasowanych zasad DLP |wszystkie zdarzenia|
|dopasowana reguła |nazwa dopasowanej reguły zasad DLP |wszystkie zdarzenia|
|wykryto poufne typy informacji (SIT)|SIC, które zostały wykryte w ramach dopasowania zasad DLP |wszystkie zdarzenia|
|podjęte działania |podjęte akcje, które spowodowały dopasowanie zasad DLP| wszystkie zdarzenia|
|naruszenie akcji | akcja na urządzeniu punktu końcowego, które zgłosiło alert DLP| zdarzenia urządzenia | 
|zasady przesuwu użytkownika |czy użytkownik przesłonięcia zasad za pośrednictwem poradę zasad | wszystkie zdarzenia|
|uzasadnienie zastąpienia użycia |tekst przyczyny podanej przez użytkownika dla przesłonięcia | wszystkie zdarzenia|   

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do pulpitu nawigacyjnego alertu ochrony przed utratą danych](dlp-alerts-dashboard-get-started.md)
- [Od czego zacząć od zapobiegania utracie danych](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention)
