---
title: Wyświetlanie raportów dotyczących zapobiegania utracie danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/7/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Użyj raportów DLP w Office 365, aby wyświetlić liczbę dopasowań, przesłoń lub wyników fałszywie dodatnich zasad DLP i sprawdzić, czy są one trendy w górę lub w dół w czasie.
ms.openlocfilehash: b264a0e0b76397be99d7586ac793dac501b6672e
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66011633"
---
# <a name="view-the-reports-for-data-loss-prevention"></a>Wyświetlanie raportów dotyczących zapobiegania utracie danych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po utworzeniu zasad ochrony przed utratą danych (DLP) w usłudze Microsoft Purview należy sprawdzić, czy działają one zgodnie z oczekiwaniami i pomagają zachować zgodność. Raporty DLP w portalu zgodności usługi Microsoft Purview umożliwiają szybkie wyświetlanie następujących elementów:

- **Dopasowania zasad DLP** Ten raport przedstawia liczbę dopasowań zasad DLP w czasie. Raport można filtrować według daty, lokalizacji, zasad lub akcji. Ten raport umożliwia:

  - Dostosuj lub uściślij zasady DLP podczas uruchamiania ich w trybie testowym. Możesz wyświetlić określoną regułę zgodną z zawartością.

  - Skoncentruj się na określonych okresach i poznaj przyczyny wzrostów i trendów.

  - Odnajdywanie procesów biznesowych naruszających zasady DLP organizacji.

  - Zapoznaj się z wpływem zasad DLP na działalność biznesową, widząc, jakie akcje są stosowane do zawartości.

  - Sprawdź zgodność z określonymi zasadami DLP, wyświetlając wszystkie dopasowania dla tych zasad.

  - Wyświetl listę najlepszych użytkowników i powtarzających się użytkowników, którzy przyczyniają się do zdarzeń w organizacji.

  - Wyświetl listę najważniejszych typów informacji poufnych w organizacji.

- **Zdarzenia DLP** Ten raport pokazuje również dopasowania zasad w czasie, takie jak raport dopasowania zasad. Jednak raport dopasowania zasad pokazuje dopasowania na poziomie reguły; Jeśli na przykład wiadomość e-mail jest zgodna z trzema różnymi regułami, w raporcie zasad są wyświetlane trzy różne elementy wiersza. Natomiast raport zdarzeń pokazuje dopasowania na poziomie elementu; Jeśli na przykład wiadomość e-mail jest zgodna z trzema różnymi regułami, raport zdarzeń pokazuje pojedynczy element wiersza dla tego elementu zawartości.

  Ponieważ liczby raportów są agregowane inaczej, raport dopasowania zasad jest lepszy do identyfikowania dopasowań z określonymi regułami i dostrajania zasad DLP. Raport zdarzeń jest lepszy do identyfikowania określonych elementów zawartości, które są problematyczne dla zasad DLP.

- **Wyniki fałszywie dodatnie i przesłonięcia DLP** Jeśli zasady DLP umożliwiają użytkownikom ich zastępowanie lub zgłaszanie wyników fałszywie dodatnich, ten raport pokazuje liczbę takich wystąpień w czasie. Raport można filtrować według daty, lokalizacji lub zasad. Ten raport umożliwia:

  - Dostosuj lub uściślij zasady DLP, widząc, które zasady mają dużą liczbę wyników fałszywie dodatnich.

  - Wyświetl uzasadnienia przesłane przez użytkowników, gdy rozwiążą poradę dotyczącą zasad, przesłaniając zasady.

  - Dowiedz się, gdzie zasady DLP powodują konflikt z prawidłowymi procesami biznesowymi, powodując dużą liczbę przesłonięcia użytkowników.

Wszystkie raporty DLP mogą wyświetlać dane z ostatniego czteromiesięcznego okresu. Wyświetlenie najnowszych danych w raportach może potrwać do 24 godzin.

Te raporty można znaleźć na **pulpicie nawigacyjnym** **raportów** \> portalu \> zgodności usługi Microsoft Purview.

![Zasady DLP są zgodne z raportem.](../media/117d20c9-d379-403f-ad68-1f5cd6c4e5cf.png)

## <a name="view-the-justification-submitted-by-a-user-for-an-override"></a>Wyświetlanie uzasadnienia przesłanego przez użytkownika w celu zastąpienia

Jeśli zasady DLP zezwalają użytkownikom na ich zastąpienie, możesz użyć raportu fałszywie dodatniego i zastąpić go, aby wyświetlić tekst przesłany przez użytkowników w poradę dotyczącą zasad.

![Pole uzasadnienie w szczegółach raportu DLP z wynikiem fałszywie dodatnim i przesłonięcia.](../media/e11e3126-026d-4e77-a16d-74a0686d1fa3.png)

## <a name="take-action-on-insights-and-recommendations"></a>Podjęcie akcji na podstawie szczegółowych informacji i zaleceń

Raporty mogą wyświetlać szczegółowe informacje i zalecenia, w których można kliknąć czerwoną ikonę ostrzeżenia, aby wyświetlić szczegółowe informacje o potencjalnych problemach i podjąć możliwe działania naprawcze.

![Kliknij ikonę szczegółowych informacji, aby wyświetlić szczegóły i akcje do wykonania.](../media/51782036-7299-4960-8175-75c2b1637159.png)

## <a name="permissions-for-dlp-reports"></a>Uprawnienia do raportów DLP

Aby wyświetlić raporty DLP w Centrum zgodności & zabezpieczeń, musisz mieć przypisane następujące elementy:

- Rola **Czytelnik zabezpieczeń** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a>. Domyślnie ta rola jest przypisywana do grup ról Zarządzanie organizacjami i Czytelnik zabezpieczeń w centrum administracyjnym Exchange.

- **Wyświetl tylko rolę DLP Compliance Management** w Centrum zgodności & zabezpieczeń. Domyślnie ta rola jest przypisywana do grup ról Administrator zgodności, Zarządzanie organizacją, Administrator zabezpieczeń i Czytelnik zabezpieczeń w Centrum zgodności & zabezpieczeń.

- **Rola Adresaci tylko do wyświetlania** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a>. Domyślnie ta rola jest przypisywana do grup ról Zarządzanie zgodnością, Zarządzanie organizacją i View-Only Zarządzanie organizacją w centrum administracyjnym Exchange.

## <a name="find-the-cmdlets-for-the-dlp-reports"></a>Znajdowanie poleceń cmdlet dla raportów DLP

Aby użyć poleceń cmdlet raportowania DLP, wykonaj następujące kroki:

1. [Połączenie do programu PowerShell zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell)

2. Użyj następujących poleceń cmdlet:

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-DlpDetectionsRaport](/powershell/module/exchange/get-dlpdetectionsreport)
   - [Get-DlpSiDetectionsRaport](/powershell/module/exchange/get-dlpsidetectionsreport)

Jednak raporty DLP wymagają ściągania danych z różnych Microsoft 365, w tym Exchange Online. Z tego powodu następujące polecenia cmdlet dla raportów DLP są dostępne w programie Exchange Online powershell. Aby użyć poleceń cmdlet dla tych raportów DLP, wykonaj następujące kroki:

1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Użyj następujących poleceń cmdlet:

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-MailDetailDlpPolicyReport](/powershell/module/exchange/get-maildetaildlppolicyreport)
