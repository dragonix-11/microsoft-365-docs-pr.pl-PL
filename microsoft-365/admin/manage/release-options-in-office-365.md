---
title: Konfigurowanie opcji wydania standardowego lub kierowanego
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 3b3adfa4-1777-4ff0-b606-fb8732101f47
description: Dowiedz się, jak skonfigurować opcję wydania dla nowych produktów i funkcji aktualizacji w centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: 6e3cf1987d6b3c22ed1414bd8e352da7acf49e60
ms.sourcegitcommit: e246725b0935067aad886530d5178972c0f895d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2021
ms.locfileid: "63012509"
---
# <a name="set-up-the-standard-or-targeted-release-options"></a>Konfigurowanie opcji wydania standardowego lub kierowanego

> [!IMPORTANT]
> Aktualizacje Microsoft 365 opisane w tym artykule dotyczą aplikacji Microsoft 365, SharePoint Online i Exchange Online. Te opcje wydania są kierowane w celu wykorzystania najlepszych starań, aby wprowadzić zmiany w Microsoft 365, ale nie są gwarantowane przez cały czas ani w przypadku wszystkich aktualizacji. Nie dotyczą one usług Aplikacje Microsoft 365, Skype dla firm, Microsoft Teams ani powiązanych usług. Aby uzyskać informacje o opcjach wydania Aplikacje Microsoft 365, zobacz [Omówienie kanałów](/deployoffice/overview-update-channels) aktualizacji dla Aplikacje Microsoft 365.

Dzięki Microsoft 365 otrzymujesz nowe aktualizacje i funkcje produktów od teraz, gdy stają się dostępne, zamiast kosztować co kilka lat. Możesz zarządzać tym, jak Twoja organizacja otrzymuje te aktualizacje. Na przykład możesz utworzyć konto w celu wcześniejszego wydania, aby Twoja organizacja najpierw otrzymuje aktualizacje. Możesz wskazać, że aktualizacje będą dostępne tylko dla określonych osób. Możesz też pozostać przy domyślnym harmonogramie wersji i otrzymywać aktualizacje później. W tym artykule opisano różne opcje wydania oraz sposoby używania ich w organizacji.

## <a name="how-it-works---release-validation"></a>Jak to działa  weryfikacja wydania

Każde nowe wydanie jest najpierw testowane i weryfikowane przez zespół funkcji, a następnie przez cały zespół funkcji pakietu Microsoft 365, a następnie przez wszystkie firmy Microsoft. Po przeprowadzeniu wewnętrznych testów i walidacji następnym krokiem jest **Udostępnianie kierowane** (kiedyś nazywane udostępnianiem natychmiastowym) dla klientów, którzy wybrali tę opcję. W każdym pierścieniu wydania firma Microsoft zbiera opinie i dalej weryfikuje jakość, monitorując kluczowe metryki użycia. Ta seria stopniowej weryfikacji jest stosowana po to, aby zapewnić najwyższą możliwą jakość wydania światowego. Wydania zostały przedstawione na poniższym rysunku. 
  
![Pierścienie weryfikacji wydania dla Microsoft 365.](../../media/73611ed3-2d8c-4e7b-8074-9f03b239f9ed.png)
  
W przypadku znaczących aktualizacji klienci są wstępnie powiadamiani przez Przewodnik Microsoft 365 [klientów](https://products.office.com/business/office-365-roadmap). O zbliżaniu się aktualizacji jest ona powiadamiana za pośrednictwem [Microsoft 365 wiadomości](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter).

> [!NOTE]
> Aby uzyskać dostęp do Centrum wiadomości za pośrednictwem centrum administracyjnego, potrzebujesz konta usługi Microsoft 365 lub Azure [AD](/office365/admin/admin-overview/about-the-admin-center). Microsoft 365 plan dla użytkowników planu domu nie mają centrum administracyjnego.


## <a name="standard-release"></a>Udostępnianie standardowe

Jest to opcja domyślna, w której Ty i Twoi użytkownicy otrzymujecie najnowsze aktualizacje, gdy są one ogólnie publikowane dla wszystkich klientów.
  
Dobrym rozwiązaniem jest pozostawienie większości użytkowników w standardowych wersjach,  a informatycy i użytkownicy potęgowi  w wersji docelowej będą oceniać nowe funkcje i przygotowywać zespoły do obsługi użytkowników biznesowych i kadry kierowniczej. 
  
> [!NOTE]
> Jeśli zmienisz ścieżkę udostępniania kierowanego z powrotem na ścieżkę udostępniania standardowego, Twoi użytkownicy mogą utracić dostęp do funkcji, które jeszcze nie są dostępne w ramach udostępniania standardowego. 
  
## <a name="targeted-release"></a>Udostępnianie kierowane

W ramach tej opcji najnowsze aktualizacje są dostarczane dla Ciebie i Twoich użytkowników w pierwszej kolejności. Masz wpływ na kształt produktu dzięki możliwości przekazywania wczesnych opinii. Możesz wybrać opcję dostarczania wczesnych aktualizacji dla poszczególnych użytkowników lub dla całej organizacji.
  
> [!IMPORTANT]
> - Wdrażanie dużych lub złożonych aktualizacji może trwać dłużej niż pozostałych aktualizacji. Dzięki temu nie mają one negatywnego wpływu na jakichkolwiek użytkowników. Nie ma żadnych gwarancji dotyczących dokładnego harmonogramu udostępniania.
> - Wersja kierowane nie jest obecnie dostępna dla klientów z planem Office 365 GCC ani planem Office 365 GCC dod.
  
### <a name="targeted-release-for-entire-organization"></a>Udostępnianie kierowane dla całej organizacji

Jeśli [skonfigurujemy opcję wydania w](#set-up-the-release-option-in-the-admin-center) centrum administracyjnym dla tej opcji, wszyscy użytkownicy otrzymają środowisko wersji kierowanej. W przypadku organizacji posiadających ponad 300 użytkowników zalecamy skorzystanie z testowej subskrypcji tej opcji. Aby uzyskać informacje o subskrypcji testowej, skontaktuj się ze swoim przedstawicielem firmy Microsoft. 
  
### <a name="targeted-release-for-selected-users"></a>Udostępnianie kierowane dla wybranych użytkowników

Jeśli dla [tej](#set-up-the-release-option-in-the-admin-center) opcji skonfigurujemy opcję wydania w centrum administracyjnym, możesz zdefiniować konkretnych użytkowników (zwykle użytkowników końcowych), którzy będą otrzymywać wczesny dostęp do funkcji. 
  
## <a name="benefits-of-targeted-release"></a>Zalety udostępniania kierowanego

Wersja kierowane umożliwia administratorom, menedżerom zmian i innym osobom odpowiedzialnym za aktualizacje Microsoft 365 przygotowanie się na nadchodzące zmiany przez umożliwienie im:
  
- testowania i weryfikowania nowych aktualizacji zanim zostaną udostępnione wszystkim użytkownikom w organizacji,
    
- przygotowania powiadomień dla użytkowników i dokumentacji przed udostępnieniem aktualizacji na całym świecie,
    
- przygotowanie pracowników wewnętrznej pomocy technicznej na nadchodzące zmiany,
    
- zapoznanie się z kwestiami związanymi z zabezpieczeniami i zgodnością,
    
- zastosowanie mechanizmów sterowania funkcjami (tam, gdzie to możliwe) w celu kontrolowania udostępniania aktualizacji użytkownikom końcowym.
    
## <a name="set-up-the-release-option-in-the-admin-center"></a>Konfigurowanie opcji wydania w centrum administracyjnym

Sposób otrzymywania aktualizacji przez Organizację możesz Microsoft 365, korzystając z poniższych kroków. Aby do tego dorezygnować, musisz być Microsoft 365 globalnym.
  
> [!IMPORTANT]
> Może upłynie do 24 godzin, aby poniższe zmiany zadadają się w Microsoft 365. Jeśli po włączeniu udostępniania kierowanego zrezygnujesz z niego, Twoi użytkownicy mogą utracić dostęp do funkcji, które jeszcze nie są dostępne w ramach udostępniania według harmonogramu. 
  
1. W centrum administracyjnym przejdź do pozycji Ustawienia  >  Ustawienia **Org** i na karcie Profil <a href="https://go.microsoft.com/fwlink/p/?linkid=2067339" target="_blank"> organizacji wybierz pozycję</a> **Preferencje dotyczące wersji**.

5. Aby wyłączyć wydanie kierowane, wybierz pozycję **Wydanie standardowe**, a następnie wybierz pozycję **Zapisz zmiany**. 
    
6. Aby włączyć kierowane wydanie dla wszystkich użytkowników w organizacji, wybierz pozycję Wersja **kierowane** dla wszystkich użytkowników, a następnie wybierz pozycję **Zapisz zmiany**. 
    
7. Aby włączyć wersję ukierunkowaną dla niektórych osób w organizacji, wybierz pozycję Wersja **kierowane** dla wybranych użytkowników, a następnie wybierz pozycję **Zapisz zmiany**. 
    
8. Wybierz **pozycję Wybierz użytkowników**, aby dodawać użytkowników po jednym użytkowniku na raz, lub wybierz pozycję Wybierz Upload **użytkowników**, aby dodać ich zbiorczo.
    
9. Po dodaniu użytkowników wybierz pozycję **Zapisz zmiany**.
  
## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak [zarządzać wiadomościami](/office365/admin/manage/message-center) w Centrum [Microsoft 365 wiadomości](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter), aby otrzymywać powiadomienia o nadchodzących Microsoft 365 aktualizacjach i wersjach.

## <a name="related-content"></a>Zawartość pokrewna

[Dołączanie do Office niejawnego programu testów](https://insider.office.com/join/windows) (artykuł)
