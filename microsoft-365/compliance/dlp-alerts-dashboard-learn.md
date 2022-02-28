---
title: Informacje na temat pulpitu nawigacyjnego alertów dotyczących ochrony przed utratą danych
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
description: Dowiedz się więcej o alertach ochrony przed utratą danych i pulpicie nawigacyjnym alertów.
ms.openlocfilehash: 375b16a3072f40ef8f366f7c1c4e8f714f195d63
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62989761"
---
# <a name="learn-about-the-data-loss-prevention-alerts-dashboard"></a>Informacje na temat pulpitu nawigacyjnego alertów dotyczących ochrony przed utratą danych

Gdy kryteria zasad ochrony przed utratą danych (DLP, Data loss prevention) są do siebie dopasowane przez akcje, które użytkownik przyjmuje na poufny element, te zasady mogą wygenerować alert. W takiej sytuacji może być duża liczba alertów. Alerty DLP są zbierane na pulpicie nawigacyjnym alertów. Pulpit nawigacyjny alertów umożliwia szczegółowe badanie wszystkich szczegółów dotyczących dopasowania zasad.  

<!-- [Microsoft 365 compliance center](https://compliance.microsoft.com/)-->

## <a name="workloads"></a>Obciążenia pracą

Na [pulpicie nawigacyjnym zarządzania alertami DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365 alerty</a> dotyczące zasad DLP dotyczących tych obciążeń:

- Exchange
- SharePoint
- OneDrive
- Teams
- Windows 10 urządzenia 

> [!TIP]
> Klienci, którzy używają funkcji [DLP](endpoint-dlp-learn-about.md) punktu końcowego, którzy są uprawnieni do korzystania z usługi [Teams DLP](dlp-microsoft-teams.md), zobaczą alerty zasad DLP punktu końcowego oraz alerty zasad DLP Teams na pulpicie nawigacyjnym zarządzania alertami DLP.

## <a name="single-alert-and-aggregate-alert"></a>Alerty pojedyncze i alerty agregowane

Istnieją dwa typy alertów, które można skonfigurować w zasadach DLP.

Alerty o pojedynczych zdarzeniach są zazwyczaj używane w zasadach monitorowania bardzo ważnych zdarzeń, które mają niską głośność, na przykład w przypadku jednej wiadomości **e-mail** z co najmniej 10 numerami kart kredytowych klientów wysyłanymi poza organizację.

**Alerty dotyczące zdarzeń agregowania** są zazwyczaj używane w zasadach monitorowania zdarzeń, które występują w dłuższym okresie. Alert zagregowany może na przykład zostać wyzwolony, gdy w ciągu 48 godzin na zewnątrz organizacji zostanie wysłanych 10 pojedynczych wiadomości e-mail z jednym numerem karty kredytowej klienta.

## <a name="types-of-events"></a>Typy zdarzeń

Oto niektóre zdarzenia skojarzone z alertem. W interfejsie użytkownika możesz wybrać konkretne zdarzenie, aby wyświetlić jego szczegóły. 

### <a name="event-details"></a>Szczegóły zdarzenia

|Nazwa właściwości  |Opis  |Typy zdarzeń  |
|---------|---------|---------|
|Identyfikator |unikatowy identyfikator skojarzony ze zdarzeniem |wszystkie zdarzenia |
|Lokalizacja |obciążenie pracą, w przypadku którego zdarzenie zostało wykryte|wszystkie zdarzenia |
|czas działania     |czas działania użytkownika zgodnego z kryteriami zasad DLP |

### <a name="affected-entities"></a>Jednostki, których dotyczy problem

|Nazwa właściwości |Opis| Typy zdarzeń|
|---------|---------|---------|
|użytkownik | użytkownik, który podjęł działanie, które spowodowało dopasowanie zasad | wszystkie zdarzenia|
|nazwa hosta | Nazwa hosta komputera, na którym wystąpiło dopasowanie zasad DLP | zdarzenia urządzenia|
|Adres IP | Adres IP komputera, na którym wystąpiło dopasowanie zasad DLP | zdarzenia urządzenia|
|sha1 |Skrót SHA-1 pliku | zdarzenia urządzenia|
|sha256 | Skrót SHA-256 pliku | zdarzenia urządzenia|
|Identyfikator urządzenia MDATP | identyfikator MDATP urządzenia końcowego|
|rozmiar pliku | rozmiar pliku| SharePoint, OneDrive i zdarzenia urządzenia|
|ścieżka pliku | Ścieżka bezwzględna elementu związanego z zasadami DLP | SharePoint, OneDrive i urządzenia|
|adresaci wiadomości e-mail |jeśli wiadomość e-mail była poufnym elementem, który był zgodne z zasadami DLP, to pole zawiera adresatów tej wiadomości e-mail| Exchange zdarzenia|
|temat wiadomości e-mail |temat wiadomości e-mail zgodnej z zasadami DLP |Exchange zdarzenia|
|załączniki wiadomości e-mail | Nazwy załączników w wiadomości e-mail, które są zgodne z zasadami DLP| Exchange zdarzenia|
|właściciel witryny |nazwa właściciela witryny| SharePoint i OneDrive zdarzenia|
|adres URL witryny |pełny adres URL witryny SharePoint lub OneDrive, w której wystąpiło dopasowanie zasad DLP |SharePoint i OneDrive zdarzenia|
|utworzono plik |czas tworzenia pliku zgodnego z zasadami DLP |SharePoint i OneDrive zdarzenia|
|plik z ostatnią modyfikacją | Po ostatniej zmianie pliku zgodnego z zasadami DLP | SharePoint i OneDrive zdarzenia|
|rozmiar pliku | rozmiar pliku zgodnego z zasadami DLP |SharePoint i OneDrive zdarzenia|
|właściciel pliku |właściciel pliku, który był zgodne z zasadami DLP |SharePoint i OneDrive zdarzenia|  

### <a name="policy-details"></a>Szczegóły zasad

|Nazwa właściwości |Opis |Typy zdarzeń |
|---------|---------|---------|
|Dopasowane zasady DLP |Nazwa dopasowanej zasady DLP |wszystkie zdarzenia|
|reguła jest dopasowana |Nazwa dopasowanej reguły zasad DLP |wszystkie zdarzenia|
|wykryty typ informacji poufnych (SIT)|Identyfikatory SIT wykryte w ramach dopasowania zasad DLP |wszystkie zdarzenia|
|akcje wykonane |Akcje, które zostały wykonane, które spowodowały dopasowanie zasad DLP| wszystkie zdarzenia|
|działanie naruszające | akcja na urządzeniu końcowym, które podniesieło alert DLP| zdarzenia urządzenia | 
|zasady dotyczące zaogodniania użytkowników |czy użytkownik zastępować zasady za pomocą porady dotyczącej zasad | wszystkie zdarzenia|
|stosowanie justowania zastępowania |tekst przyczyny zastąpienia podany przez użytkownika | wszystkie zdarzenia|   

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do pulpitu nawigacyjnego alertów ochrony przed utratą danych](dlp-alerts-dashboard-get-started.md)
- [Od czego zacząć od ochrony przed utratą danych](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention)
