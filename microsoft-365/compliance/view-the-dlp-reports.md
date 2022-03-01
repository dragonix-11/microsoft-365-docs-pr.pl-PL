---
title: Wyświetlanie raportów w celu ochrony przed utratą danych
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
description: Raporty DLP w programie Office 365 umożliwia wyświetlanie liczby wyników zasad DLP, zastępować lub wyników fałszywie dodatnich oraz sprawdzać, czy są one trendem w górę, czy w dół w czasie.
ms.openlocfilehash: cbf03a4d981d4b37bd22db8fa08c728b77318ddf
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017793"
---
# <a name="view-the-reports-for-data-loss-prevention"></a>Wyświetlanie raportów w celu ochrony przed utratą danych

Po utworzeniu zasad ochrony przed utratą danych (DLP, Data Loss Prevention), musisz upewnić się, że działają one zgodnie z twoimi zamiarami, i pomóc Ci w zachowania zgodności. Dzięki raportom ochrony przed zagrożeniami DLP w Centrum &amp; zgodności zabezpieczeń możesz szybko wyświetlić:
  
- **Dopasowania zasad DLP** Ten raport pokazuje liczbę dopasowania zasad DLP w czasie. Raport można filtrować według daty, lokalizacji, zasad lub akcji. Za pomocą tego raportu można: 
    
  - Dostosowywanie lub uściślianie zasad DLP podczas uruchamiania ich w trybie testowania. Możesz wyświetlić określoną regułę dopasowaną do zawartości.
    
  - Skoncentruj się na określonych okresach czasu i poznaj przyczyny kolekcji i trendów.
    
  - Odnajdowanie procesów biznesowych naruszających zasady ochrony przed firmami.
    
  - Dowiedz się, jakie akcje są stosowane do zawartości, aby zrozumieć skutki biznesowe zasad ochrony przed firmami.
    
  - Sprawdź zgodność z określonymi zasadami DLP, wyświetlając wszystkie dopasowania dla tych zasad.
    
  - Wyświetl listę użytkowników, którzy są najgorętsi, i powtarzaj się użytkownicy, którzy współtworują zdarzenia w organizacji.
    
  - Wyświetlanie listy najlepszych typów informacji poufnych w organizacji.
    
- **Zdarzenia DLP** W tym raporcie są również przedstawiane dopasowania zasad w czasie, na przykład raport dopasowania zasad. Jednak raport dopasowania zasad pokazuje dopasowania na poziomie reguły. Jeśli na przykład wiadomość e-mail jest dopasowana do trzech różnych reguł, raport dopasowania zasad wyświetla trzy różne elementy. Z kolei w raporcie zdarzeń dopasowania są przedstawiane na poziomie elementu. Jeśli na przykład wiadomość e-mail jest dopasowana do trzech różnych reguł, w raporcie o zdarzeniach jest przedstawiany jeden wiersz tego fragmentu zawartości. 
    
  Ze względu na to, że raporty są agregowane w inny sposób, raport dopasowania zasad jest lepszy do identyfikowania dopasowania z określonymi regułami i dostrajania zasad DLP. Raporty o incydentach są lepszym rozwiązaniem w przypadku zidentyfikowania konkretnych fragmentów zawartości, które są problematyczne w przypadku zasad DLP.
    
- **Wartości dodatnie i zasłonięcia fałszowe zasad DLP** Jeśli zasady DLP umożliwiają użytkownikom zastępowanie ich lub zgłaszanie wyników fałszywie dodatnich, ten raport pokazuje liczbę takich wystąpień w czasie. Raport można filtrować według daty, lokalizacji lub zasad. Za pomocą tego raportu można: 
    
  - Dostosowywanie lub uściślij zasady ochrony przed zasadami przez wyświetlanie, które zasady są wiąże się z dużą liczbą wyników fałszywie dodatnich.
    
  - Wyświetl justowanie przesłane przez użytkowników, gdy rozpoznają poradę o zasadach, zastępując zasady.
    
  - Dowiedz się, gdzie zasady DLP są w konflikcie z prawidłowymi procesami biznesowymi przez dużą liczbę zastępować użytkowników.
    
Wszystkie raporty DLP mogą wyświetlać dane z ostatniego czteromiesięowego okresu. Najnowsze dane mogą pojawiać się w raportach po 24 godzinach.
  
Te raporty można znaleźć na pulpicie nawigacyjnym &amp; Raporty **Centrum** \> \> **zgodności zabezpieczeń**.
  
![Zasady DLP są do dopasowania w raporcie.](../media/117d20c9-d379-403f-ad68-1f5cd6c4e5cf.png)
  
## <a name="view-the-justification-submitted-by-a-user-for-an-override"></a>Wyświetlanie justowania przesłanego przez użytkownika w celu zastąpienia

Jeśli twoje zasady DLP umożliwiają użytkownikom zastępowanie ich, możesz użyć raportu wyników fałszywie dodatnich i zastępować, aby wyświetlić tekst przesłany przez użytkowników w poradach o zasadach.
  
![Justowanie pola w szczegółach raportu błędnie dodatniego i zastępowania zasad DLP.](../media/e11e3126-026d-4e77-a16d-74a0686d1fa3.png)
  
## <a name="take-action-on-insights-and-recommendations"></a>Działanie na temat szczegółowych informacji i zaleceń

Raporty mogą wyświetlać szczegółowe informacje i zalecenia, w których można kliknąć czerwoną ikonę ostrzeżenia, aby wyświetlić szczegółowe informacje na temat potencjalnych problemów i podjąć możliwe działania naprawcze.
  
![Kliknij ikonę szczegółowych informacji, aby wyświetlić szczegóły i akcje do podjęcia.](../media/51782036-7299-4960-8175-75c2b1637159.png)
  
## <a name="permissions-for-dlp-reports"></a>Uprawnienia do raportów DLP

Aby wyświetlać raporty ochrony przed zagrożeniami w centrum & zgodności, musisz mieć przypisane:

- **Rola czytnika** zabezpieczeń w centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a>. Domyślnie ta rola jest przypisana do grup ról Zarządzanie organizacją i Czytnik zabezpieczeń w centrum Exchange administracyjnego.

- **Rola zarządzania zgodnością DLP tylko w** Centrum zabezpieczeń i & zgodności. Domyślnie ta rola jest przypisana do grup ról Administrator zgodności, Zarządzanie organizacją, Administrator zabezpieczeń i Czytnik zabezpieczeń w Centrum & zabezpieczeń.

- **Rola Tylko wyświetlanie adresatów** w centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a>. Domyślnie ta rola jest przypisana do grup ról Zarządzanie zgodnością, Zarządzanie organizacją View-Only Zarządzanie organizacją w centrum administracyjnym usługi Exchange administracyjnego.

## <a name="find-the-cmdlets-for-the-dlp-reports"></a>Znajdowanie polecenia cmdlet dla raportów dotyczących zasad DLP

Aby korzystać z większości funkcji cmdlet w Centrum &amp; zgodności zabezpieczeń, należy:
  
1. [Połączenie zabezpieczeń &amp; Centrum zgodności przy użyciu zdalnej obsługi programu PowerShell](/powershell/exchange/connect-to-scc-powershell)
    
2. Użyj dowolnego z tych [cmdlet &amp; Centrum zgodności zabezpieczeń.](/powershell/exchange/exchange-online-powershell)
    
Raporty DLP wymagają jednak ściągania danych z Office 365, w tym Exchange Online. Z tego powodu polecenia cmdlet dla raportów DLP są dostępne w programie Exchange Online PowerShell, a nie w programie &amp; PowerShell Centrum zgodności zabezpieczeń. W związku z tym, aby korzystać z funkcji cmdlet na potrzeby raportów funkcji DLP, należy:
  
1. [Łączenie się z usługą Exchange Online przy użyciu zdalnej obsługi programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
2. Użyj dowolnego z tych funkcji cmdlet dla raportów funkcji DLP:
    
      - [Get-DlpDetectionsReport](/powershell/module/exchange/get-dlpdetectionsreport)
    
      - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
