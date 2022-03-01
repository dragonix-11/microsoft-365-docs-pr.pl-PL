---
title: Kontrolka aplikacji
description: Jak używać kontroli aplikacji i zaufania w aplikacjach
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 108c4d3d64f503d2221aed9df9724faee85b2998
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014799"
---
# <a name="app-control"></a>Kontrolka aplikacji

Kontrola aplikacji to opcjonalne rozwiązanie w zakresie zabezpieczeń w Microsoft Managed Desktop które ograniczają wykonywanie kodu na urządzeniach klienckich.

Ta kontrolka ogranicza ryzyko złośliwego oprogramowania lub złośliwych skryptów. Ta kontrolka wymaga uruchamiania tylko kodów podpisanych przez listę wydawców zatwierdzonych przez klienta. Z tej kontrolki korzysta się wiele korzyści związanych z zabezpieczeniami, ale przede wszystkim warto ich chronić przed danymi i tożsamościami przed zagrożeniami opartymi na klientach.

Microsoft Managed Desktop zarządzanie zasadami kontroli aplikacji przez utworzenie podstawowych zasad, które umożliwią korzystanie z podstawowych scenariuszy zwiększających wydajność. Możesz rozszerzyć zaufanie do innych osób podpisujących, które są specyficzne dla aplikacji i skryptów w Twoim środowisku.

Każda technologia zabezpieczeń wymaga równowagi między doświadczeniem użytkownika, zabezpieczeniami i kosztami. Kontrola aplikacji zmniejsza zagrożenie złośliwym oprogramowaniem w środowisku, ale użytkownik może mieć konsekwencje oraz dalsze działania ze strony administratora IT.

| Dodatkowe zabezpieczenia i obowiązki | Opis |
| ------ | ------ |
| Dodatkowe zabezpieczenia | Uruchamianie aplikacji lub skryptów, które nie są zaufane przez zasady kontroli aplikacji, jest blokowane na urządzeniach. |
| Dodatkowe obowiązki użytkownika | <ul><li>Ty ponosisz odpowiedzialność za testowanie aplikacji w celu ustalenia, czy zostaną one zablokowane przez zasady kontroli aplikacji.</li><li>Jeśli aplikacja jest (lub zostałaby) zablokowana, odpowiadasz za zidentyfikowanie wymaganych danych osoby podpisującej. Należy zażądać zmiany za pośrednictwem portalu administracyjnego.</li></ul>
| Microsoft Managed Desktop obowiązki | <ul><li>Microsoft Managed Desktop podstawowe zasady, które umożliwiają korzystanie z podstawowych produktów firmy Microsoft, takich jak Aplikacje Microsoft 365, Windows, Teams, OneDrive itp.</li><li>Microsoft Managed Desktop wstawianie zaufanych podpisów i wdrażanie zaktualizowanych zasad na Twoich urządzeniach.</li></ul>

## <a name="managing-trust-in-applications"></a>Zarządzanie zaufaniem w aplikacjach

Microsoft Managed Desktop politykę podstawową, która ufa podstawowym składnikom technologii firmy Microsoft. Następnie możesz *dodać zaufanie* do swoich aplikacji i skryptów, informując Microsoft Managed Desktop, które aplikacje i skrypty są już zaufane.

### <a name="base-policy"></a>Zasady podstawowe

Microsoft Managed Desktop, we współpracy z ekspertami firmy Microsoft ds. bezpieczeństwa, tworzy i utrzymuje standardową politykę. Te zasady standardowe:

- Włącza większość aplikacji wdrożonych za pośrednictwem Microsoft Intune.
- Blokuje niebezpieczne działania, takie jak kompilacja kodu lub wykonywanie niezaufanych plików.

W celu ograniczenia wykonywania oprogramowania zasady podstawowe przybierają następujące podejście:

- Pliki uruchamiane przez administratorów będą mogły być uruchamiane.
- Pliki w lokalizacjach, których  nie można zapisywać w katalogach użytkownika, będą mogły być uruchamiane.
- Pliki są podpisane przez [zaufanego podpisatora](#signer-requests).
- Większość plików podpisanych przez firmę Microsoft zostanie uruchomionych, jednak niektóre z nich są blokowane, aby uniemożliwić akcje wysokiego ryzyka, takie jak kompilacja kodu.

Jeśli użytkownik (inny niż administrator) mógł dodać aplikację lub skrypt do urządzenia (czyli do katalogu, w którym można zapisywać dane użytkownika), nie zezwolimy na jego wykonanie. Zezwolimy na wykonanie, jeśli aplikacja lub skrypt zostały już dozwolone przez administratora.

Nasze zasady zatrzymają wykonywanie aplikacji w następujących scenariuszach:

- Jeśli użytkownik ma kłopoty z próbą zainstalowania złośliwego oprogramowania.
- W przypadku luki w zabezpieczeniach aplikacji użytkownik próbuje zainstalować złośliwe oprogramowanie.
- Jeśli użytkownik celowo spróbuje uruchomić nieautoryzowaną aplikację lub skrypt.

### <a name="signer-requests"></a>Prośby osób podpisują

Informujesz nas, które aplikacje są dostarczane przez zaufanych wydawców oprogramowania, składając *wniosek o podpis.* W ten sposób:

- Dodaj te informacje o zaufaniu do podstawowych zasad kontroli aplikacji.
- Zezwalaj na uruchamianie na twoich urządzeniach dowolnego oprogramowania podpisanego certyfikatem tego wydawcy.

## <a name="audit-and-enforced-policies"></a>Zasady inspekcji i wymuszone

Microsoft Managed Desktop aplikacji Microsoft Intune aplikacji za pomocą zasad programu Windows:

### <a name="audit-policy"></a>Zasady inspekcji

Te zasady tworzą dzienniki w celu nagrywania, czy aplikacja lub skrypt zostaną zablokowane przez zasady Wymuszone.

Zasady inspekcji nie wymuszają reguł kontroli aplikacji. Są one przeznaczone do celów testowych w celu ustalenia, czy aplikacja będzie wymagać zwolnienia od wydawcy. Dzienniki wyświetla ostrzeżenia (zdarzenia 8003 lub 8006) w podglądzie zdarzeń, zamiast blokować wykonywanie lub instalowanie określonych aplikacji lub skryptu.

### <a name="enforced-policy"></a>Wymuszone zasady

Te zasady blokują uruchamianie niezaufanych aplikacji i skryptów oraz tworzą dzienniki po zablokowaniu aplikacji lub skryptu. Wymuszone zasady uniemożliwiają standardowym użytkownikom uruchamianie aplikacji lub skryptów przechowywanych w katalogach, w których można zapisywać dane użytkownika.

Do urządzeń w grupie Testowanie zastosowano zasady inspekcji w celu sprawdzenia, czy któreś z aplikacji nie będzie powodować problemów. Wszystkie pozostałe grupy (najpierw, szybko i szeroko) używają zasad wymuszonych. Użytkownicy w tych grupach nie będą mogli uruchamiać niezaufanych aplikacji ani skryptów.
