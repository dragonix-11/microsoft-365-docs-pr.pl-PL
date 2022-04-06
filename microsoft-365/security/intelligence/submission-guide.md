---
title: Przesyłanie plików do analizy przez firmę Microsoft
description: Dowiedz się, jak przesyłać pliki do firmy Microsoft w celu analizy złośliwego oprogramowania, śledzenia przesyłanych plików i wykrywania sporów.
ms.reviewer: ''
keywords: zabezpieczenia, przykładowa pomoc przy przesyłaniu, plik złośliwego oprogramowania, plik antywirusowy, plik trojański, prześlij, wyślij do firmy Microsoft, prześlij próbkę, wirus, trojański, robak, niezakrywony, nie wykrywa, wysyłaj wiadomości e-mail do firmy Microsoft, wysyłaj wiadomości e-mail z złośliwym oprogramowaniem, sądzę, że jest to wirus, do którego mogę wysłać wirusa, to ten wirus, MSE, nie wykrywa, nie ma podpisu, nie wykrywa, podejrzewa plik,  MMPC, Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem, analityk, WDSI, analizy zabezpieczeń
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 78f1e00555d36880f24f05d213f42725f4ac0133
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705700"
---
# <a name="submit-files-for-analysis"></a>Przesyłanie plików do analizy

Jeśli masz plik, który podejrzewasz, że jest złośliwym oprogramowaniem lub jest nieprawidłowo wykryty, możesz przesłać go do nas w celu analizy. Ta strona zawiera odpowiedzi na często zadawane pytania dotyczące przesyłania pliku do analizy.

## <a name="how-do-i-send-a-malware-file-to-microsoft"></a>Jak wysłać plik złośliwego oprogramowania do firmy Microsoft?

Możesz wysłać nam pliki, które według Ciebie mogą być złośliwym oprogramowaniem lub plikami, które zostały niepoprawnie wykryte za pośrednictwem [przykładowego portalu przesyłania](https://www.microsoft.com/en-us/wdsi/filesubmission).

Otrzymujemy dużą liczbę próbek z wielu źródeł. W analizie priorytetu jest podana liczba wykrycia plików i typ przesyłania. Możesz pomóc nam szybko wykonać analizę, podając szczegółowe informacje o produkcie, który był przez Ciebie podczas używania, i co robisz, gdy znalazłeś plik.

Po zalogowaniu się możesz śledzić swoje przesłania.

## <a name="can-i-send-a-sample-by-email"></a>Czy mogę wysłać przykład w wiadomości e-mail?

Nie, akceptujemy zgłoszenia tylko za pośrednictwem naszego [przykładowego portalu przesyłania](https://www.microsoft.com/en-us/wdsi/filesubmission).

## <a name="can-i-submit-a-sample-without-signing-in"></a>Czy mogę przesłać przykład bez logowania?

L.p. Jeśli jesteś klientem korporacyjnym, musisz się zalogować, abyśmy w odpowiedni sposób ustalili priorytety Twojego zgłoszenia. W przypadku wystąpienia epidemii lub zdarzenia związanego z zabezpieczeniami należy skontaktować się z wyznaczonym specjalistą pomocy technicznej firmy Microsoft lub przejść do pomocy technicznej [firmy Microsoft](https://support.microsoft.com/) w celu uzyskania natychmiastowej pomocy.

## <a name="what-is-the-software-assurance-id-said"></a>Co to jest identyfikator Software Assurance (SAID)?

Identyfikator [Software Assurance (SAID)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) jest dla klientów korporacyjnych w celu śledzenia uprawnień do pomocy technicznej. Portal przesyłania akceptuje i przechowuje informacje SAID oraz umożliwia klientom z prawidłowymi kodami SAID tworzenie przesyłania o wyższym priorytecie.

### <a name="how-do-i-dispute-the-detection-of-my-program"></a>Jak zaprzecić wykrywaniu programu?

[Prześlij plik jako](https://www.microsoft.com/en-us/wdsi/filesubmission) dewelopera oprogramowania. Zaczekaj na ostateczną oznaczenie zgłoszenia.

Jeśli nie podoba Ci się nasze określenie zgłoszenia, skontaktuj się z firmą Microsoft za pomocą formularza kontaktu dewelopera dostarczonego z wynikami przesyłania. Podane informacje zostaną przez nas wykorzystać do dalszego zbadania w razie potrzeby.

Zachęcamy wszystkich dostawców oprogramowania i deweloperów do przeczytania informacji o tym, jak firma [Microsoft identyfikuje złośliwe oprogramowanie i niechciane oprogramowanie](criteria.md).

## <a name="how-do-i-track-or-view-past-sample-submissions"></a>Jak śledzić lub wyświetlać wcześniejsze przykładowe przesłania?

Możesz śledzić swoje zgłoszenia za pośrednictwem [strony historii przesyłania](https://www.microsoft.com/en-us/wdsi/submissionhistory).

## <a name="what-does-the-submission-status-mean"></a>Co oznacza stan przesyłania?

Pokazywane jest, że każde przesyłanie znajduje się w jednym z następujących typów stanu:

* Przesłano — plik został odebrany

* W toku — analityk rozpoczął sprawdzanie pliku

* Zamknięty — ostateczną wyznaczanie zostało przez analityka

Stan plików, które przesłasz do nas, możesz sprawdzić na [stronie historii przesyłania](https://www.microsoft.com/en-us/wdsi/submissionhistory).

## <a name="how-does-microsoft-prioritize-submissions"></a>Jak firma Microsoft określa priorytety przesyłania

Przetwarzanie przesyłania przejmuje dedykowane zasoby dla analityków. Ponieważ regularnie otrzymujemy wiele zgłoszeń, obsługujemy je w oparciu o priorytet. Na sposób priorytetu przesyłania mają wpływ następujące czynniki:

* Mają one priorytet w przypadku plików, które mogą mieć wpływ na dużą liczbę komputerów.

* Uwierzytelnieni klienci, zwłaszcza klienci w przedsiębiorstwach z prawidłowymi [identyfikatorami Software Assurance (SAIDS](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx)), mają wyższy priorytet.

* Zgłoszenia oznaczone jako o wysokim priorytecie przez właścicieli said są natychmiast przyciągane uwagę.

Twoje zgłoszenia są natychmiast skanowane przez nasze systemy, aby dać Ci najnowsze wyznaczanie jeszcze przed rozpoczęciem postępowania przez analityka nad sprawą. Pamiętaj, że ten sam plik mógł zostać już przetworzony przez analityka. Aby sprawdzić aktualizacje tej wyznaczania, należy ponownie wybrać opcję na stronie szczegółów przesyłania.
