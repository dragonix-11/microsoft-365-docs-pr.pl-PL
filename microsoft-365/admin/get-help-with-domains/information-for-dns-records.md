---
title: Zbieranie informacji potrzebnych do utworzenia rekordów DNS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: Zbierz wartości/informacje potrzebne do utworzenia rekordów DNS w celu połączenia Domeny z Twoją Microsoft 365 subskrypcją.
ms.openlocfilehash: 672d57babb1b26e42b3fd24da8c9dc841223e41f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316803"
---
# <a name="gather-the-information-you-need-to-create-dns-records"></a>Zbieranie informacji potrzebnych do utworzenia rekordów DNS

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>Krok 1. Znajdowanie wartości rekordu TXT i weryfikowanie

::: moniker range="o365-worldwide"

1. W centrum administracyjne platformy Microsoft 365 przejdź **do strony Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domeny</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W Centrum administracyjnym przejdź do strony **Ustawienia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domeny</a>.

::: moniker-end
    
2. Na stronie **Domeny** wybierz swoją domenę, a następnie wybierz pozycję **Rozpocznij konfigurowanie**. Nastąpi powrót do kreatora konfiguracji domen w celu wyświetlenia konkretnej wartości, którą należy dodać.
    
3. Na stronie **Domain Verification (Weryfikacja** domeny) wybierz **pozycję Add a TXT record to the domain (Dodaj rekord TXT) do rekordów DNS domeny, a** następnie wybierz pozycję **Continue (Kontynuuj**).
    
4. Skopiuj **wyświetlaną wartość TXT** . Wygląda to następująco: **MS=msXXXXXXXX**. 
    
5. Przejdź do [strony Dodawanie rekordów DNS, aby połączyć domenę](create-dns-records-at-any-dns-hosting-provider.md), i postępuj zgodnie z instrukcjami, aby dodać rekordy w witrynie internetowej hosta DNS.
    
6. Postępuj zgodnie z instrukcjami tworzenia rekordu TXT (lub rekordu MX) na swoim hoście DNS, a następnie zweryfikuj domenę z powrotem w Microsoft 365.

7. Usuń rekord TXT (lub MX) z hosta DNS po zweryfikowaniu domeny w Microsoft 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>Krok 2. Znajdowanie wartości rekordu MX dla poczty e-mail i nie tylko

::: moniker range="o365-worldwide"

1. W centrum administracyjne platformy Microsoft 365 przejdź **do strony Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domeny</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W Centrum administracyjnym przejdź do strony **Ustawienia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domeny</a>.

::: moniker-end
    
2. Na stronie **Domeny** wybierz swoją domenę.
    
3. Wybierz **pozycję Manage DNS (Zarządzaj systemem DNS**), **wybierz pozycję More OptionsAdd** >  **your own DNS** (Dodaj własny system DNS) i **wybierz pozycję Continue** (Kontynuuj), aby wyświetlić rekordy DNS do dodania.
    
    Warto zachować te informacje, aby były dostępne podczas wprowadzania zmian na hoście DNS, dlatego możesz skopiować i wkleić te wartości.
    
    Grupy rekordów DNS wymienione na tej stronie zależą od dokonanych wyborów widocznych w obszarze **Przeznaczenie domeny**.
    
4. Przejdź do [strony Dodawanie rekordów DNS, aby połączyć domenę](create-dns-records-at-any-dns-hosting-provider.md), i postępuj zgodnie z instrukcjami, aby dodać rekordy w witrynie internetowej hosta DNS.

5. Wykonaj czynności dotyczące tworzenia rekordów u Twojego hosta DNS.

## <a name="related-content"></a>Zawartość pokrewna

[Często zadawane pytania](../setup/domains-faq.yml) dotyczące domen (artykuł)\
[Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](find-and-fix-issues.md) (artykuł)\
[Zarządzanie domenami](/admin) (strona linku)