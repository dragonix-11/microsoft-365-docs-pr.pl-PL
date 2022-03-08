---
title: Znajdowanie i rozwiązywanie problemów po dodaniu swojej domeny lub rekordów DNS
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
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 40398b0b-bdd0-4afd-ab5e-b5ae6b7990bf
description: Dowiedz się, jak śledzić problemy, które występują podczas konfigurowania domeny niestandardowej, upewniając się, że rekordy DNS zostały poprawnie skonfigurowane.
ms.openlocfilehash: 7fa5a18ff0e4b7f0db8749f5659fefdd89cb3fcd
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316887"
---
# <a name="find-and-fix-issues-after-adding-your-domain-or-dns-records"></a>Znajdowanie i rozwiązywanie problemów po dodaniu swojej domeny lub rekordów DNS

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
Konfigurowanie domeny do współpracy z Microsoft 365 może być trudne. System DNS jest wymagający, a konfiguracja systemu DNS dla Twojej domeny wpływa na ważne działania biznesowe, takie jak obsługa poczty e-mail!

> [!NOTE]
> Możesz sprawdzić, czy nie występują problemy z domeną, sprawdzając jej stan. Przejdź do **witryny** **SetupDomains** >  i wyświetl powiadomienia w **kolumnie Stan**. Jeśli zobaczysz problem, wybierz trzy kropki (więcej akcji), a następnie wybierz pozycję **Sprawdź kondycję**. Otwarte okienko będzie opisywać wszystkie problemy występujące w Twojej domenie.
  
## <a name="whats-going-on"></a>Co się dzieje?

- [Nie możesz zweryfikować domeny?](#cant-verify-your-domain)
    
- [Outlook nie działa?](#outlook-isnt-working)
    
- [Wiadomości e-mail wszystkich osób przełączyły się Microsoft 365 i chcesz tylko przełączyć swoją pocztę e-mail?](#everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch)

- [Nie możesz potwierdzić stanu konta niedochodowego lub szkolnego?](#cant-confirm-non-profit-or-school-account-status)

- [Usługi nie działają z Twoją domeną?](#services-not-working-with-your-domain)
    
- [Uzyskiwanie dostępu do witryny sieci Web nie działa?](#accessing-your-website-isnt-working)

## <a name="cant-verify-your-domain"></a>Nie możesz zweryfikować domeny?

Istnieje kilka typowych przyczyn nieprawidłowego funkcjonowania weryfikacji domen:
  
1. **Wartość rekordu weryfikacji jest niepoprawna.** Sprawdź dokładnie, czy wartość została prawidłowo skopiowana i wklejona do rekordu weryfikacji TXT u Twojego hosta DNS. Jednym z typowych problemów jest pominięcie części „MS=" rekordu. Ta część jest również potrzebna! 
    
2. **Rekord nie został zapisany.** W przypadku niektórych hostów DNS musisz wykonać dodatkowy krok w celu zapisania pliku strefy (w którym jest przechowywany dany rekord DNS), aby został zaktualizowany w Internecie. Upewnij się, że zmiany zostały zapisane, aby Microsoft 365 i zweryfikować rekord. 
    
3. **Rekord nie został zaktualizowany w Internecie.** Zazwyczaj możemy zobaczyć nowy rekord już po kilku minutach, ale w niektórych przypadkach może to potrwać nawet kilka godzin. 
    
## <a name="outlook-isnt-working"></a>Program Outlook nie działa?

Jeśli Twój rekord MX i inne rekordy DNS zostały poprawnie skonfigurowane dla domeny, ale poczta nie działa, skorzystaj z pomocy firmy Microsoft w [rozwiązywaniu problemów z programem Outlook](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues).
  
## <a name="everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch"></a>Wiadomości e-mail wszystkich osób przełączyły się Microsoft 365 i chcesz tylko przełączyć swoją pocztę e-mail?
<a name="BKMK_EmailSwitched"> </a>

Po dodaniu domeny do usługi Microsoft 365 zwykle rekord MX domeny jest aktualizowany (przez Ciebie lub przez Ciebie lub Microsoft 365), aby wskazać usługę Microsoft 365, a WSZYSTKIE wiadomości e-mail wysyłane do tej domeny zaczną przychodzić do usługi Microsoft 365. Zanim zmienisz rekord MX, upewnij się, że zostały utworzone skrzynki pocztowe Microsoft 365 dla wszystkich osób z adresami e-mail w tej domenie.
  
Co zrobić, jeśli nie chcesz przenosić poczty e-mail wszystkich osób w domenie do Microsoft 365? Zamiast tego możesz wykonać [kroki pilotażowe Microsoft 365 tylko z kilkoma adresami e-mail](../setup/domains-faq.yml).
  
## <a name="cant-confirm-non-profit-or-school-account-status"></a>Nie możesz potwierdzić stanu konta niedochodowego lub szkolnego?
<a name="BKMK_validateAcct"> </a>

Istnieje kilka scenariuszy, gdy wystarczy zweryfikować domenę organizacji i nie skonfigurować żadnych usług. Na przykład, aby udowodnić Microsoft 365 że Twoja organizacja kwalifikuje się do subskrypcji szkolnej.
  
Zapoznaj się z wskazówkami w tece Weryfikowanie domeny Microsoft 365, aby udowodnić stan własności[, organizacji niedochodowej](../setup/domains-faq.yml) lub edukacyjnej, lub aktywować usługę Yammer, aby upewnić się, że zostały wykonane wszystkie wymagane kroki. W każdej sytuacji jest nieco inaczej. 
  
## <a name="services-not-working-with-your-domain"></a>Usługi nie współdziałają z Twoją domeną?

Możemy pomóc Ci w śledzenia problemów z konfiguracją systemu DNS Twojej domeny. Narzędzie do rozwiązywania problemów z domenami w Microsoft 365 pokaże wszystkie rekordy, które wymagają naprawy, oraz dokładnie to, co należy ustawić. 

> [!TIP]
> System DNS jest poprawnie skonfigurowany, ale poczta nie działa w programie Outlook na komputerze? Zapoznaj się z różnymi [scenariuszami](/exchange/mail-flow-best-practices/mail-flow-best-practices) przepływu poczty e-mail Microsoft 365, aby upewnić się, że wszystko jest poprawnie skonfigurowane dla Twojej firmy. Więcej pomocy w rozwiązywaniu problemów z pocztą e-mail możesz też uzyskać tutaj: [Rozwiązywanie problemów z programem Outlook](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues). 
  
## <a name="accessing-your-website-isnt-working"></a>Nie można uzyskać dostępu do Twojej witryny internetowej?

Jeśli problemy z systemem DNS zostały rozwiązane, a wciąż występują trudności, spróbuj wykonać jedną z następujących czynności.
  
- Osoby nie mogą uzyskać do Twojej witryny internetowej dostęp w witrynie *contoso.com*: [Śledzenie problemów z witryną sieci Web](../setup/add-domain.md)
    
- Nie możesz zaktualizować rekordu A lub rekordu CNAME, aby wskazać Twoją witrynę internetową: Aktualizowanie niestandardowych [rekordów DNS w Microsoft 365](../setup/add-domain.md)

## <a name="related-content"></a>Zawartość pokrewna

[Rozwiązywanie problemów: inspekcja danych dotyczących zweryfikowanych zmian domeny](/azure/active-directory/reports-monitoring/troubleshoot-audit-data-verified-domain) (artykuł)\
[Domeny — często](../setup/domains-faq.yml) zadawane pytania (artykuł)

