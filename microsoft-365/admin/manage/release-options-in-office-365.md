---
title: Konfigurowanie opcji wersji Standardowa lub Docelowa
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
description: Dowiedz się, jak skonfigurować opcję wydania dla nowych aktualizacji produktów i funkcji w Centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: 176558448f31fadea0b0cf865bca5d1156e3eefe
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129425"
---
# <a name="set-up-the-standard-or-targeted-release-options"></a>Konfigurowanie opcji wersji Standardowa lub Docelowa

> [!IMPORTANT]
> Aktualizacje Microsoft 365 opisane w tym artykule dotyczą Microsoft 365, SharePoint Online i Exchange Online. Te opcje wydania są ukierunkowane i najlepiej sprawdzają się sposoby wydawania zmian w Microsoft 365, ale nie można ich zagwarantować przez cały czas ani dla wszystkich aktualizacji. Nie mają one zastosowania do usług Aplikacje Microsoft 365, Skype dla firm, Microsoft Teams i powiązanych. Aby uzyskać informacje o opcjach wydania dla Aplikacje Microsoft 365, zobacz [Omówienie kanałów aktualizacji dla Aplikacje Microsoft 365](/deployoffice/overview-update-channels).

Dzięki Microsoft 365 otrzymujesz nowe aktualizacje produktów i funkcje, ponieważ stają się one dostępne zamiast kosztownych aktualizacji co kilka lat. Możesz zarządzać sposobem otrzymywania tych aktualizacji przez organizację. Możesz na przykład zarejestrować się w celu uzyskania wcześniejszej wersji, aby organizacja najpierw otrzymywała aktualizacje. Można wyznaczyć, że aktualizacje otrzymują tylko niektóre osoby. Możesz też pozostać w domyślnym harmonogramie wydania i otrzymywać aktualizacje później. W tym artykule wyjaśniono różne opcje wydania i sposób ich używania w organizacji.

## <a name="how-it-works---release-validation"></a>Jak to działa  weryfikacja wydania

Każda nowa wersja jest najpierw testowana i weryfikowana przez zespół funkcji, a następnie przez cały zespół Microsoft 365 funkcji, a następnie przez całą firmę Microsoft. Po przeprowadzeniu wewnętrznych testów i walidacji następnym krokiem jest **Udostępnianie kierowane** (kiedyś nazywane udostępnianiem natychmiastowym) dla klientów, którzy wybrali tę opcję. W każdym pierścieniu wydania firma Microsoft zbiera opinie i dalej weryfikuje jakość, monitorując kluczowe metryki użycia. Ta seria stopniowej weryfikacji jest stosowana po to, aby zapewnić najwyższą możliwą jakość wydania światowego. Wydania zostały przedstawione na poniższym rysunku. 
  
![Pierścienie sprawdzania poprawności wydania dla Microsoft 365.](../../media/73611ed3-2d8c-4e7b-8074-9f03b239f9ed.png)
  
W przypadku istotnych aktualizacji klienci są początkowo powiadamiani przez [plan Microsoft 365](https://products.office.com/business/office-365-roadmap). Gdy aktualizacja zbliża się do wdrożenia, jest ona przekazywana za pośrednictwem [centrum Microsoft 365 komunikatów](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter).

> [!NOTE]
> Aby uzyskać dostęp do centrum wiadomości za pośrednictwem [centrum administracyjnego](/office365/admin/admin-overview/admin-center-overview), potrzebujesz konta Microsoft 365 lub Azure AD. Microsoft 365 użytkownicy planu domowego nie mają centrum administracyjnego.

## <a name="standard-release"></a>Udostępnianie standardowe

Jest to domyślna opcja, w której ty i Twoi użytkownicy otrzymujecie najnowsze aktualizacje, gdy zostaną ogólnie wydane wszystkim klientom.
  
Dobrym rozwiązaniem jest pozostawienie większości użytkowników w **wersji Standardowa** oraz specjalistów IT i zaawansowanych użytkowników w **wersji docelowej** w celu oceny nowych funkcji i przygotowania zespołów do obsługi użytkowników biznesowych i kadry kierowniczej. 
  
> [!NOTE]
> Jeśli zmienisz ścieżkę udostępniania kierowanego z powrotem na ścieżkę udostępniania standardowego, Twoi użytkownicy mogą utracić dostęp do funkcji, które jeszcze nie są dostępne w ramach udostępniania standardowego. 
  
## <a name="targeted-release"></a>Udostępnianie kierowane

W ramach tej opcji najnowsze aktualizacje są dostarczane dla Ciebie i Twoich użytkowników w pierwszej kolejności. Masz wpływ na kształt produktu dzięki możliwości przekazywania wczesnych opinii. Możesz wybrać opcję dostarczania wczesnych aktualizacji dla poszczególnych użytkowników lub dla całej organizacji.
  
> [!IMPORTANT]
> - Wdrażanie dużych lub złożonych aktualizacji może trwać dłużej niż pozostałych aktualizacji. Dzięki temu nie mają one negatywnego wpływu na jakichkolwiek użytkowników. Nie ma żadnych gwarancji dotyczących dokładnego harmonogramu udostępniania.
> - Docelowa wersja nie jest obecnie dostępna dla klientów z planem Office 365 GCC lub planem Office 365 GCC High i DoD.
  
### <a name="targeted-release-for-entire-organization"></a>Udostępnianie kierowane dla całej organizacji

Jeśli [skonfigurujesz opcję wydania w centrum administracyjnym](#set-up-the-release-option-in-the-admin-center) dla tej opcji, wszyscy użytkownicy otrzymają środowisko docelowej wersji. W przypadku organizacji posiadających ponad 300 użytkowników zalecamy skorzystanie z testowej subskrypcji tej opcji. Aby uzyskać informacje o subskrypcji testowej, skontaktuj się ze swoim przedstawicielem firmy Microsoft. 
  
### <a name="targeted-release-for-selected-users"></a>Udostępnianie kierowane dla wybranych użytkowników

Jeśli [skonfigurujesz opcję wydania w centrum administracyjnym](#set-up-the-release-option-in-the-admin-center) dla tej opcji, możesz zdefiniować określonych użytkowników, zazwyczaj użytkowników zaawansowanych, aby otrzymywać wczesny dostęp do funkcji i funkcji.

> [!IMPORTANT]
> Niektóre funkcje są wdrażane tylko w organizacji. Oznacza to, że cała organizacja otrzyma dostęp do tej funkcji w tym samym czasie. W przypadku takich funkcji nie jest możliwe wczesne pobranie funkcji przez wybranych użytkowników w docelowym programie wydawniczym. Oznacza to, że twoja organizacja nie będzie mogła otrzymywać tych funkcji wcześniej, jeśli skonfigurowano wybranych użytkowników w docelowej wersji. Aby upewnić się, że wszystkie funkcje są widoczne w docelowej wersji, należy skonfigurować docelową wersję dla całej organizacji lub skonfigurować organizację testową.
  
## <a name="benefits-of-targeted-release"></a>Zalety udostępniania kierowanego

Docelowa wersja umożliwia administratorom, menedżerom zmian lub innym osobom odpowiedzialnym za aktualizacje Microsoft 365 przygotowanie się do nadchodzących zmian, umożliwiając im:
  
- testowania i weryfikowania nowych aktualizacji zanim zostaną udostępnione wszystkim użytkownikom w organizacji,
    
- przygotowania powiadomień dla użytkowników i dokumentacji przed udostępnieniem aktualizacji na całym świecie,
    
- przygotowanie pracowników wewnętrznej pomocy technicznej na nadchodzące zmiany,
    
- zapoznanie się z kwestiami związanymi z zabezpieczeniami i zgodnością,
    
- zastosowanie mechanizmów sterowania funkcjami (tam, gdzie to możliwe) w celu kontrolowania udostępniania aktualizacji użytkownikom końcowym.
    
## <a name="set-up-the-release-option-in-the-admin-center"></a>Konfigurowanie opcji wydania w centrum administracyjnym

Możesz zmienić sposób otrzymywania aktualizacji Microsoft 365 przez organizację, wykonując następujące kroki. Aby wyrazić zgodę, musisz być administratorem globalnym w Microsoft 365.
  
> [!IMPORTANT]
> Może upłynąć do 24 godzin, aż poniższe zmiany wejdą w życie w Microsoft 365. Jeśli po włączeniu udostępniania kierowanego zrezygnujesz z niego, Twoi użytkownicy mogą utracić dostęp do funkcji, które jeszcze nie są dostępne w ramach udostępniania według harmonogramu. 
  
1. W centrum administracyjnym przejdź do **ustawienia Ustawienia** >  **Org**, a następnie na <a href="https://go.microsoft.com/fwlink/p/?linkid=2067339" target="_blank">karcie **Profil organizacji**</a> wybierz pozycję **Preferencje wydania**.

5. Aby wyłączyć wersję docelową, wybierz pozycję **Wersja standardowa**, a następnie wybierz pozycję **Zapisz zmiany**. 
    
6. Aby włączyć wersję docelową dla wszystkich użytkowników w organizacji, wybierz pozycję **Docelowa wersja dla wszystkich**, a następnie wybierz pozycję **Zapisz zmiany**. 
    
7. Aby włączyć docelową wersję dla niektórych osób w organizacji, wybierz pozycję **Docelowa wersja dla wybranych użytkowników**, a następnie wybierz pozycję **Zapisz zmiany**. 
    
8. Wybierz **pozycję Wybierz użytkowników**, aby dodawać użytkowników pojedynczo, lub **Upload użytkowników**, aby dodawać ich zbiorczo.
    
9. Po zakończeniu dodawania użytkowników wybierz pozycję **Zapisz zmiany**.
  
## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak [zarządzać komunikatami](/office365/admin/manage/message-center) w [centrum wiadomości Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter), aby otrzymywać powiadomienia o nadchodzących aktualizacjach i wydaniach Microsoft 365.

## <a name="related-content"></a>Zawartość pokrewna

[Dołącz do programu Office Insider Program](https://insider.office.com/join/windows) (artykuł)
