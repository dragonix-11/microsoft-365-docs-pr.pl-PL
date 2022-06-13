---
title: Zapewnianie, że zawsze masz optymalne mechanizmy kontroli zabezpieczeń ze wstępnie ustawionymi zasadami zabezpieczeń
description: Kroki zapewniające, że zawsze masz najlepsze mechanizmy kontroli zabezpieczeń ze wstępnie ustawionymi zasadami zabezpieczeń. Wstępnie ustawione zasady umożliwiają wybranie profilu zabezpieczeń standardowego lub ścisłego. Firma Microsoft będzie zarządzać mechanizmami kontroli zabezpieczeń w Ochrona usługi Office 365 w usłudze Microsoft Defender i obsługiwać za Ciebie.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: e768635d3bb804dbf586ce652203689942901e4f
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042955"
---
# <a name="ensuring-you-always-have-the-optimal-security-controls-with-preset-security-policies"></a>Zapewnianie, że zawsze masz optymalne mechanizmy kontroli zabezpieczeń ze wstępnie ustawionymi zasadami zabezpieczeń

Wstępnie skonfigurowane zasady zabezpieczeń umożliwiają wybranie profilu zabezpieczeń standardowego lub ścisłego oraz zarządzanie kontrolami zabezpieczeń przez firmę Microsoft i utrzymywanie ich w Ochrona usługi Office 365 w usłudze Microsoft Defender dla Ciebie.

Po dodaniu nowych kontrolek lub jeśli ustawienie najlepszych rozwiązań dla kontroli zabezpieczeń zmieni się wraz ze zmieniającym się poziomem zagrożeń, firma Microsoft automatycznie zaktualizuje ustawienia kontroli zabezpieczeń dla użytkowników przypisanych do standardowych lub ścisłych wstępnie ustawionych zasad zabezpieczeń. Korzystając z zasad ustawień wstępnych zabezpieczeń, zawsze będziesz mieć zalecaną przez firmę Microsoft konfigurację najlepszych rozwiązań dla użytkowników.

## <a name="what-you-will-need"></a>Co będzie potrzebne
- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 lub nowszy (uwzględniony w wersji E5)
- Wystarczające uprawnienia (rola administratora zabezpieczeń)
- 5 minut na wykonanie poniższych kroków.

## <a name="choosing-between-standard-and-strict-policies"></a>Wybieranie między zasadami standardowymi i ścisłymi

Nasze rygorystyczne wstępnie ustawione zasady zabezpieczeń mają bardziej agresywne limity i ustawienia mechanizmów kontroli zabezpieczeń, które spowodują bardziej agresywne wykrywanie i będą obejmować administratora w podejmowaniu decyzji o tym, które zablokowane wiadomości e-mail są wydawane użytkownikom końcowym.

- Zbierz listę użytkowników, którzy wymagają bardziej agresywnego wykrywania, nawet jeśli oznacza to, że bardziej dobra poczta zostanie oflagowana jako podejrzana. Są to zazwyczaj pracownicy kadry kierowniczej, kadra kierownicza i historycznie wysoce ukierunkowani użytkownicy.

- Upewnij się, że wybrani użytkownicy mają dostęp administratora do przeglądania i wydawania wiadomości e-mail, jeśli użytkownik końcowy uzna, że poczta może być dobra, i zażąda, aby wiadomość została im udostępniona.

- Jeśli powyższe kryteria zostaną spełnione, użytkownik powinien zostać umieszczony w zasadach ścisłych zabezpieczeń wstępnie ustawionych. W przeciwnym razie użytkownik powinien zostać umieszczony w wstępnie ustawionych zasadach zabezpieczeń w warstwie Standardowa.

> [!TIP]
> Aby uzyskać informacje na temat standardowych i ścisłych zabezpieczeń, zobacz ten [artykuł](../../office-365-security/recommended-settings-for-eop-and-office365.md).

## <a name="enable-security-presets"></a>Włączanie ustawień wstępnych zabezpieczeń

Po wybraniu między standardowymi i ścisłymi zasadami wstępnie ustawionymi zabezpieczeń dla użytkowników należy wykonać kilka dalszych kroków, aby przypisać użytkowników do każdego ustawienia wstępnego.

1. Zidentyfikuj użytkowników, grupy lub domeny, które chcesz uwzględnić w standardowych i ścisłych ustawieniach wstępnych zabezpieczeń.
1. Zaloguj się do portalu microsoft security pod adresem https://security.microsoft.com.
1. Na lewym pasku nawigacyjnym w obszarze **Współpraca & poczty e-mail** wybierz pozycję **Zasady & reguły**.
1. Wybierz pozycję **Zasady zagrożeń**.
1. Wybierz pozycję **Wstępnie ustawione zasady zabezpieczeń** poniżej nagłówka **Szablony zasad**
1. Wybierz pozycję **Zarządzaj** poniżej ustawień wstępnych ochrony w warstwie Standardowa.
1. Dodaj użytkowników, grupy lub domeny, do których chcesz zastosować ustawienie wstępne Standardowa, w sekcji Ochrona EOP. Kliknij przycisk **Dalej** .
1. Dodaj użytkowników, grupy lub domeny, do których chcesz zastosować ustawienie wstępne Standardowa, w sekcji Ochrona przed atakami MDO. Kliknij przycisk **Dalej** .
1. Kliknij przycisk **Potwierdź** .
1. Wybierz link **Zarządzaj** w ustawieniu wstępnym Ścisła ochrona.
1. Dodaj użytkowników, grupy lub domeny, do których chcesz zastosować ustawienie wstępne Standardowa, w sekcji Ochrona EOP. Kliknij przycisk **Dalej** .
1. Dodaj użytkowników, grupy lub domeny, do których chcesz zastosować ustawienie wstępne Standardowa, w sekcji Ochrona przed atakami MDO. Kliknij przycisk **Dalej** .
1. Kliknij przycisk **Potwierdź** .

> [!TIP]
> Aby dowiedzieć się więcej o wstępnie ustawionych polcies kliknij [tutaj](../../office-365-security/preset-security-policies.md)

## <a name="next-steps"></a>Następne kroki

Użyj analizatora konfiguracji, aby określić, czy twoi użytkownicy są skonfigurowani zgodnie z najlepszymi rozwiązaniami firmy Microsoft.

> [!TIP]
> Analizator konfiguracji umożliwia administratorom znajdowanie i naprawianie zasad zabezpieczeń, w których ustawienia znajdują się poniżej ustawień profilu standardowej lub ścisłej ochrony w wstępnie ustawionych zasadach zabezpieczeń. Dowiedz się więcej o analizatorze konfiguracji [tutaj](../../office-365-security/configuration-analyzer-for-security-policies.md).

Bezpieczne ustawienia wstępne są zawsze sugerowane, ponieważ zapewniają, że zawsze korzystasz z najlepszych rozwiązań firmy Microsoft. Jednak w niektórych przypadkach wymagane są niestandardowe konfiguracje. Dowiedz się więcej o zasadach niestandardowych [tutaj](../../office-365-security/tenant-wide-setup-for-increased-security.md).

