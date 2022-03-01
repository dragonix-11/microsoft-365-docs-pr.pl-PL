---
title: Rozwiązywanie problemów z analizą użycia platformy Microsoft 365
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a73632a1-62c8-4a13-8115-913773b30f93
description: Dowiedz się, jak rozwiązywać problemy z aplikacją Microsoft 365 szablonu analizy użycia.
ms.openlocfilehash: afa9841b38beefcfdd091f27e7b1f328cdf52a5e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017903"
---
# <a name="troubleshooting-microsoft-365-usage-analytics"></a>Rozwiązywanie problemów z analizą użycia platformy Microsoft 365

Zapoznaj się z następującą listą komunikatów o błędach, aby uzyskać pomoc w zakresie najczęściej występujących problemów dotyczących analizy użycia platformy Microsoft 365.
  
    
## <a name="we-are-unable-to-process-your-request-you-have-to-first-subscribe-to-this-data-from-the-microsoft-365-admin-center"></a>Nie można przetworzyć żądania. Musisz najpierw zasubskrybować te dane z centrum administracyjne platformy Microsoft 365

 **Kod błędu:** 422 
  
 **Miejsce, w którym zostanie wyświetlony ten komunikat:** W Power BI podczas nawiązywania połączenia z aplikacją szablonu analizy Microsoft 365 użycia lub podczas bezpośredniego wywoływania interfejsów API Microsoft 365 Raportowanie. 
  
 **Przyczyna:** Aby można było nawiązać połączenie z aplikacją, musisz zasubskrybować dane z centrum administracyjne platformy Microsoft 365. Jeśli ten krok nie zostanie najpierw wykonane, nie będzie można nawiązać połączenia z aplikacją szablonów, nawet jeśli po podajasz identyfikator Microsoft 365 dzierżawy. 
  
 **Aby naprawić ten błąd:** Aby zasubskrybować dane, \>  \> przejdź do centrum administracyjnego Raporty Użycia i Microsoft 365 kafelka analizy użycia na głównej stronie pulpitu nawigacyjnego.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> Wybierz przycisk **Wprowadzenie**, a następnie w okienku  Raporty, które zostanie otwarte, włącz ustawienie Udostępnij dane Microsoft 365 analizy użycia dla **Power BI i pozycję** **Zapisz**.
  
## <a name="we-are-processing-your-data"></a>Trwa przetwarzanie danych

 **Miejsce, w którym zostanie wyświetlony ten komunikat:** Na **kafelku Microsoft 365 analizy** użycia na pulpicie **nawigacyjnym** Użycie w centrum administracyjne platformy Microsoft 365. 
  
 **Przyczyna:** Gdy [zdecydujesz się na wyświetlanie](enable-usage-analytics.md) danych w aplikacji szablonów z centrum administracyjne platformy Microsoft 365, system Microsoft 365 rozpocznie generowanie historycznych danych użycia dla organizacji. W zależności od wielkości dzierżawy ten krok może trwać od 2 do 48 godzin. 
  
 **Aby rozwiązać ten problem:** Jednak jeśli po upływie 3 dni komunikat nie zmieni się na Twoje  dane są gotowe, skontaktuj się z Microsoft 365 pomocą techniczną dla firm](Uzyskaj pomoc techniczną](.. /get-help-support.md).
  
## <a name="we-are-unable-to-process-your-request-at-this-time-we-are-still-preparing-the-data-for-your-organization"></a>Nie można obecnie przetworzyć żądania. Dane dla Twojej organizacji są nadal przygotowywane

 **Kod błędu:** 423 
  
 **Miejsce, w którym zostanie wyświetlony ten komunikat:** W Power BI, gdy łączysz się z aplikacją szablonu analizy użycia usługi Microsoft 365 lub podczas bezpośredniego wywoływania interfejsów API Microsoft 365 Raportowanie. 
  
 **Przyczyna:** Gdy [zdecydujesz się na wyświetlanie](enable-usage-analytics.md) danych w aplikacji szablonów w centrum administracyjnym, system Microsoft 365 rozpocznie generowanie historycznych danych użycia dla organizacji. W zależności od rozmiaru dzierżawy ten krok może trwać od dwóch do 48 godzin. 
  
 **Aby rozwiązać ten problem:** Po prostu ujmij w cierpliwość, ale jeśli  po 3 dniach od zainicjowania komunikat nie zmieni się na Twoje dane są gotowe, skontaktuj się z Microsoft 365 [pomocą techniczną dla firm](../../business-video/get-help-support.md).
  
## <a name="the-tenant-id-you-provided-is-not-in-the-correct-format"></a>Podany identyfikator dzierżawy ma niepoprawny format

 **Kod błędu:** 400 
  
 **Miejsce, w którym zostanie wyświetlony ten komunikat:** W Power BI, gdy łączysz się z aplikacją szablonu analizy użycia usługi Microsoft 365 lub podczas bezpośredniego wywoływania interfejsów API Microsoft 365 Raportowanie. 
  
 **Przyczyna:** Identyfikator dzierżawy to identyfikator GUID i musi mieć format xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx. Ten błąd będzie wyświetlany w przypadku wprowadzenia innego ciągu w polu wprowadzania danych dzierżawy. 
  
 **Aby naprawić ten błąd:** Przejdź do centrum administracyjnego **Raporty** \> \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycia</a> i Microsoft 365 kafelka analizy użycia na głównej stronie pulpitu nawigacyjnego. Identyfikator dzierżawy znajduje się na kafelku. Możesz go skopiować i wkleić w oknie dialogowym, aby połączyć się z aplikacją szablonów. 
  
## <a name="the-tenant-id-you-provided-is-not-recognized-by-our-system"></a>Podany identyfikator dzierżawy nie jest rozpoznawany przez nasz system

 **Kod błędu:** 404 
  
 **Miejsce, w którym zostanie wyświetlony ten komunikat:** W Power BI podczas nawiązywania połączenia z aplikacją szablonu analizy Microsoft 365 użycia lub podczas bezpośredniego wywoływania interfejsów API Microsoft 365 Raportowanie. 
  
 **Przyczyna:** Podany identyfikator dzierżawy jest nieprawidłowy lub nie istnieje. 
  
 **Aby naprawić ten błąd:** Przejdź do centrum administracyjnego **Raporty** \> \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycia</a> i Microsoft 365 kafelka analizy użycia na głównej stronie pulpitu nawigacyjnego. Identyfikator dzierżawy znajduje się na kafelku. Możesz go skopiować i wkleić w oknie dialogowym, aby połączyć się z aplikacją szablonów. 
  
## <a name="please-re-enter-your-credentials-to-sign-in-to-power-bi-again"></a>Wprowadź ponownie poświadczenia, aby zalogować się do usługi Power BI

Kod błędu: 302
  
 **Miejsce, w którym zostanie wyświetlony ten komunikat:** W Power BI podczas nawiązywania połączenia z aplikacją szablonu analizy Microsoft 365 użycia lub podczas bezpośredniego wywoływania interfejsów API Microsoft 365 Raportowanie. 
  
 **Przyczyna:** Autoryzacja przy użyciu kodu nie powiodła się i może być konieczne ponowne wprowadzenie poświadczeń. 
  
 **Aby naprawić ten błąd:** Wyloguj się z programu Power BI, a następnie zaloguj się ponownie. 
  
## <a name="you-do-not-have-the-right-authorization-to-access-to-this-data-to-be-able-to-gain-access-to-the-data-from-this-service-you-need-to-be-either-a-global-admin-or-any-one-of-the-product-admins"></a>Nie masz odpowiednich uprawnień do uzyskiwania dostępu do tych danych. Aby uzyskać dostęp do danych z tej usługi, musisz być administratorem globalnym lub dowolnym z administratorów produktu

 **Kod błędu:** 403 
  
 **Miejsce, w którym zostanie wyświetlony ten komunikat:** W Power BI podczas nawiązywania połączenia z aplikacją szablonu analizy Microsoft 365 użycia lub podczas bezpośredniego wywoływania interfejsów API Microsoft 365 Raportowanie. 
  
 **Przyczyna:** Autoryzacja przy tym kodzie nie powiodła się, ponieważ użytkownik, który próbował nałączyć połączenie z aplikacją szablonu, nie ma odpowiedniego poziomu uprawnień do uzyskiwania dostępu do tych danych. 
  
 **Aby naprawić ten błąd:** Podaj poświadczenia użytkownika, który jest administratorem **globalnym, administratorem** **Exchange, administratorem** **Skype dla firm, administratorem** **SharePoint, czytelnikiem** globalnym lub czytelnikiem raportów, aby nawiązać połączenie z  aplikacją szablonów.  Aby [uzyskać więcej informacji, zobacz](../add-users/about-admin-roles.md) Informacje o rolach administratorów. 
  
## <a name="refresh-failed"></a>Odświeżanie nie powiodło się

 **Miejsce wyświetlania tego komunikatu:** Wiadomość e-mail z usługi Power BI lub stan niepowodzenia w historii odświeżania. 
  
 **Przyczyna:** Czasami poświadczenia użytkownika połączonego z aplikacją szablonu są resetowane, a nie aktualizowane w ustawieniach połączenia aplikacji szablonów, co powoduje wyświetlanie błędów odświeżania. 
  
 **Aby naprawić ten błąd:** W Power BI znajdź zestaw danych odpowiadający aplikacji szablonu analizy użycia usługi Microsoft 365, wybierz pozycję Zaplanuj odświeżanie i podaj poświadczenia  administratora. 
  
Jeśli to nie zadziała, wyczyść pamięć podręczną i ponownie utwórz aplikację szablonu.
  
  
