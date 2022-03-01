---
title: Microsoft Secure Score dla urządzeń
description: Twój wynik dla urządzeń przedstawia zbiorczy stan konfiguracji zabezpieczeń twoich urządzeń w aplikacjach, systemach operacyjnych, sieciach, kontach i mechanizmach kontroli zabezpieczeń.
keywords: Microsoft Secure Score for Devices, Microsoft Defender for Endpoint Microsoft Secure Score for Devices, secure score, configuration score, Zarządzanie zagrożeniami i lukami, security controls, improvement opportunities, security configuration score over time, security posture, baseline
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ccd5164839244250c5e2d908f41c35a706e0f49d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997864"
---
# <a name="microsoft-secure-score-for-devices"></a>Microsoft Secure Score dla urządzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

> [!NOTE]
> Wynik konfiguracji jest teraz częścią Zarządzanie zagrożeniami i lukami bezpiecznego wyniku microsoft dla urządzeń.

Twój wynik dla urządzeń jest widoczny na Zarządzanie zagrożeniami i lukami [nawigacyjnym](tvm-dashboard-insights.md) w portalu Microsoft 365 Defender sieci Microsoft 365 Defender sieci. Wyższy wynik bezpiecznego punktu końcowego firmy Microsoft dla urządzeń oznacza, że punkty końcowe są bardziej odporne na ataki zagrożenia bezpieczeństwa bezpieczeństwa. Odzwierciedla on zbiorczy stan konfiguracji zabezpieczeń Twoich urządzeń w następujących kategoriach:

- Aplikacja
- System operacyjny
- Sieć
- Konta
- Mechanizmy kontroli zabezpieczeń

Wybierz kategorię, aby przejść do strony [**Zalecenia dotyczące zabezpieczeń**](tvm-security-recommendation.md) i wyświetlić odpowiednie zalecenia.

## <a name="turn-on-the-microsoft-secure-score-connector"></a>Włączanie łącznika bezpiecznego wyniku firmy Microsoft

Przesyłaj dalej sygnał programu Microsoft Defender for Endpoint, co zapewnia wgląd w czas bezpieczeństwa urządzenia w programie Microsoft Secure Score. Dane przekazane są przechowywane i przetwarzane w tej samej lokalizacji, w których są przechowywane dane bezpiecznego wyniku firmy Microsoft.

Odzwierciedlenia zmian na pulpicie nawigacyjnym mogą potrwać kilka godzin.

1. W okienku nawigacji przejdź **do Ustawienia** \> **Punkty końcowe Funkcje** \> **zaawansowane ogólne**  \>

2. Przewiń w dół **do przycisku Microsoft Secure Score** i przełącz ustawienie na **włączoną.**

3. Wybierz **pozycję Zapisz preferencje**.

## <a name="how-it-works"></a>Jak to działa

> [!NOTE]
> Program Microsoft Secure Score dla urządzeń obecnie obsługuje konfiguracje ustawiane za pośrednictwem zasady grupy. Ze względu na bieżącą częściową obsługę usługi Intune konfiguracje, które mogły zostać skonfigurowane za pomocą usługi Intune, mogą być wyświetlane jako nieprawidłowo skonfigurowane. Skontaktuj się z administratorem IT, aby sprawdzić rzeczywisty stan konfiguracji, jeśli Twoja organizacja korzysta z usługi Intune do bezpiecznego zarządzania konfiguracją.

Dane na karcie Microsoft Secure Score for Devices są produktem skrupulatnego i trwającego procesu odnajdowania luk w zabezpieczeniach. Jest on agregowany z stale aktualizowaną oceną odnajdowania konfiguracji:

- Porównywanie zbieranych konfiguracji z zebranymi punktami odniesienia w celu odkrycia nieprawidłowo skonfigurowanych zasobów
- Mapowanie konfiguracji na luki, które można naprawić lub które można częściowo rozwiązać (zmniejszenie ryzyka)
- Zbieranie i obsługa wzorców konfiguracji najlepszych rozwiązań (dostawcy, kanały informacyjne zabezpieczeń, wewnętrzne zespoły ds. badań)
- Zbieranie i monitorowanie zmian stanu konfiguracji kontroli zabezpieczeń ze wszystkich zasobów

## <a name="improve-your-security-configuration"></a>Ulepszanie konfiguracji zabezpieczeń

Ulepsz konfigurację zabezpieczeń, korygowając problemy z listy zaleceń dotyczących zabezpieczeń. W ten sposób wynik bezpiecznego wyniku firmy Microsoft dla urządzeń jest zwiększany, a Twoja organizacja staje się bardziej zabezpieczona przed zagrożeniami i lukami w dostępie do danych.

1. Na karcie Microsoft Secure Score for Devices (Wynik bezpiecznego Zarządzanie zagrożeniami i lukami) na pulpicie nawigacyjnym wybierz jedną z kategorii. Zostanie wyświetlona lista zaleceń dotyczących tej kategorii. Zostanie ona przekierowyna do [**strony Zalecenia dotyczące zabezpieczeń**](tvm-security-recommendation.md) . Jeśli chcesz wyświetlić wszystkie zalecenia dotyczące zabezpieczeń, po wyświetlniu strony Zalecenia dotyczące zabezpieczeń wyczyść pole wyszukiwania.

2. Zaznacz element na liście. Zostanie otwarty panel wysuwu ze szczegółami związanymi z zaleceniem. Wybierz **pozycję Opcje rozwiązywania problemów**.

   :::image type="content" alt-text="Zalecenia dotyczące zabezpieczeń w zakresie kontroli zabezpieczeń." source="images/security-controls.png":::

3. Przeczytaj opis, aby zrozumieć kontekst problemu i dowiedzieć się, co należy zrobić. Wybierz datę zakończenia, dodaj notatki i wybierz pozycję Eksportuj wszystkie dane dotyczące działań naprawczych do pliku **CSV** , aby można było dołączyć je do wiadomości e-mail w celu powiadomienia o tym użytkownika.

4. **Prześlij wniosek**. Zostanie wyświetlony komunikat potwierdzający, że zadanie naprawcze zostało utworzone.

   :::image type="content" alt-text="Potwierdzenie utworzenia zadania rozwiązywania problemów." source="images/remediation-task-created.png":::

5. Zapisz plik CSV.

   :::image type="content" alt-text="Zapisz plik csv." source="images/tvm_save_csv_file.png":::

6. Wyślij do administratora IT wiadomość e-mail z wiadomością, która umożliwi propagację działań naprawczych w systemie.

7. Przejrzyj ponownie **kartę Microsoft Secure Score for Devices** na pulpicie nawigacyjnym. Liczba zaleceń dotyczących kontroli zabezpieczeń zmniejszy się. Po wybraniu opcji **Kontrolki zabezpieczeń** w celu powrotu  do strony Zalecenia dotyczące zabezpieczeń element, który został przez Ciebie wymieniony, nie będzie już tam wymieniony. Twój wynik bezpiecznego konta Microsoft dla urządzeń powinien zwiększyć się.

> [!IMPORTANT]
>Aby zwiększyć wskaźniki wykrywania oceny luk w zabezpieczeniach, pobierz następujące obowiązkowe aktualizacje zabezpieczeń i wdaj je w swojej sieci:
>
> - Klienci z | 19H1 [Kb 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)
> - Klienci usługi RS5 | [Kb 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
> - Klienci korzystający z RS4 | [Kb 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
> - Klienci usługi RS3 | [Kb 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
>
> Aby pobrać aktualizacje zabezpieczeń:
>
> 1. Przejdź do [wykazu usługi Microsoft Update](https://www.catalog.update.microsoft.com/home.aspx).
> 2. Klucz w numerze KB aktualizacji zabezpieczeń, który należy pobrać, a następnie kliknij pozycję **Wyszukaj**.

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zagrożeń i zarządzanie lukami w zabezpieczeniach wiadomości](next-gen-threat-and-vuln-mgt.md)
- [Pulpit nawigacyjny](tvm-dashboard-insights.md)
- [Wynik ekspozycji](tvm-exposure-score.md)
- [Zalecenia dotyczące zabezpieczeń](tvm-security-recommendation.md)
