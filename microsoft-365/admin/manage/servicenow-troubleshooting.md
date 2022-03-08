---
title: Rozwiązywanie problemów Microsoft 365 pomocą techniczną z serwisem ServiceNow
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
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Przewodnik po instalacji i konfiguracji certyfikowanej dla programu ServiceNow z zakresem.
ms.openlocfilehash: bac3981b728ac997839e7ac99a9411a8da244add
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324945"
---
# <a name="troubleshooting-microsoft-365-support-integration-with-servicenow"></a>Rozwiązywanie problemów Microsoft 365 pomocą techniczną z serwisem ServiceNow

| \#  | Problem  | Akcja diagnostyki     |
|-----|--------------------------------|----------------------|
| 1   | Nie widać Microsoft 365 **pomocy** technicznej                                                                                                                                                                                    | Sprawdzanie bieżącego widoku i **dzienników systemowych za** &gt; pomocą filtru xmiomsm365assit \_\_\_                        |
| 2   | Wybierz **pozycję Microsoft polecane rozwiązania,** ale otrzymuj błąd "Skontaktuj się z administratorem ServiceNow i poproś go o ukończenie kroków konfigurowania aplikacji".                                                                      | Sprawdzanie komunikatu o błędzie u góry formularza i dzienniki **systemowe Wszystkie** &gt; za pomocą filtru xmiomsm365assit \_\_\_     |
| 3   | Wybierz **pozycję Microsoft polecane rozwiązania,** ale otrzymuję komunikat o błędzie "Skontaktuj się z administratorem ServiceNow i poproś go o ukończenie ostatniego kroku instalacji aplikacji".                                                                | Sprawdzanie komunikatu o błędzie u góry formularza i dzienniki **systemowe Wszystkie** &gt; za pomocą filtru xmiomsm365assit \_\_\_     |
| 4   | Wpisz problem w polu wyszukiwania i wybierz pozycję **Microsoft** zalecane rozwiązania, ale pojawia się błąd "Skontaktuj się z administratorem ServiceNow i poproś go o ukończenie kroków konfiguracji aplikacji".                                   | Sprawdzanie komunikatu o błędzie u góry formularza i dzienniki **systemowe Wszystkie** &gt; za pomocą filtru xmiomsm365assit \_\_\_     |
| 5   | Wpisz problem w polu wyszukiwania i wybierz pozycję **Microsoft** polecane rozwiązania, ale pojawia się błąd "Skontaktuj się z administratorem ServiceNow i poproś go o ukończenie ostatniego kroku instalacji aplikacji".                                 | Sprawdzanie komunikatu o błędzie u góry formularza i dzienniki **systemowe Wszystkie** &gt; za pomocą filtru xmiomsm365assit \_\_\_     |
| 6   | Wybierz **pozycję Skontaktuj się z pomocą techniczną firmy Microsoft**, ale zostanie wyświetlany komunikat o błędzie "Skontaktuj się z administratorem ServiceNow i poproś go o ukończenie procedury konfigurowania aplikacji".                                                                       | Sprawdzanie komunikatu o błędzie u góry formularza i dzienniki **systemowe Wszystkie** &gt; za pomocą filtru xmiomsm365assit \_\_\_     |
| 7   | Wybierz **pozycję Skontaktuj się z pomocą techniczną firmy Microsoft**, ale zostanie wyświetlany komunikat o błędzie "Skontaktuj się z administratorem ServiceNow i poproś go o ukończenie ostatniego kroku instalacji aplikacji".                                                                 | Sprawdzanie komunikatu o błędzie u góry formularza i dzienniki **systemowe Wszystkie** &gt; za pomocą filtru xmiomsm365assit \_\_\_     |
| 8   | Wybierz **pozycję Skontaktuj się z pomocą techniczną firmy Microsoft**, ale zostanie wyświetlany komunikat o błędzie "{EmailAddress} nie jest prawidłowym Microsoft 365 administratora. Aby otworzyć Microsoft 365 usługi, musisz mieć odpowiednie uprawnienia administratora. W aplikacji połącz konto administratora". | Sprawdzanie komunikatu o błędzie u góry formularza i dzienniki **systemowe Wszystkie** &gt; za pomocą filtru xmiomsm365assit \_\_\_     |
| 9   | Wybierz **zalecane rozwiązania firmy Microsoft,** ale nic się nie pojawia                                                                                                                                                            | Sprawdzanie **dzienników systemowych — wychodzące dzienniki HTTP** z filtrami login.microsoftonline.com i connector.rave.microsoft.com |
| 10  | Wybierz **pozycję Zalecane rozwiązania firmy Microsoft,** ale otrzymuję komunikat o błędzie "Skontaktuj się z pomocą techniczną aplikacji".                                                                                                                                     | Sprawdzanie komunikatu o błędzie u góry formularza i dzienniki **systemowe Wszystkie** &gt; za pomocą filtru xmiomsm365assit \_\_\_     |
| 11  | Wpisz problem w polu wyszukiwania i wybierz pozycję **Microsoft polecane rozwiązania** , ale nic się nie pojawia                                                                                                                             | Sprawdzanie **dzienników systemowych — wychodzące dzienniki HTTP** z filtrami login.microsoftonline.com i connector.rave.microsoft.com |
| 12  | Wpisz problem w polu wyszukiwania i wybierz pozycję **Microsoft zalecane rozwiązania** , ale pojawia się błąd "Skontaktuj się z pomocą techniczną aplikacji".                                                                                                      | Sprawdzanie komunikatu o błędzie u góry formularza i dzienniki **systemowe Wszystkie** &gt; za pomocą filtru xmiomsm365assit \_\_\_     |
| 13  | Użytkownik wybiera pozycję Skontaktuj **się z pomocą techniczną firmy Microsoft**, ale nic się nie dzieje                                                                                                                                                            | Sprawdzanie **dzienników systemowych — wychodzące dzienniki HTTP** z filtrami login.microsoftonline.com i connector.rave.microsoft.com |
| 14  | Nie widać zalecanego rozwiązania przez firmę Microsoft po ponownym otwarciu zdarzenia                                                                                                                                                      | Check **System Logs** &gt; **All** with filter xmiomsm365assit\_\_\_                                              |
| 15  | Nie widać spraw firmy Microsoft po ponownym otwarciu zdarzenia, które zostało przekazane do pomocy technicznej firmy Microsoft                                                                                                                            | Check **System Logs** &gt; **All** with filter xmiomsm365assit\_\_\_                                              |
| 16  | Nie można zapisać szczegółów biletu, pojawia się błąd "Nie można zapisać szczegółów biletu. Skontaktuj się z pomocą techniczną aplikacji".                                                                                                                          | Sprawdzanie komunikatu o błędzie u góry formularza                                                                            |
