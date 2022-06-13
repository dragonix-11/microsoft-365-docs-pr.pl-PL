---
title: Jak skonfigurować uprawnienia i zasady kwarantanny
description: Kroki konfigurowania zasad kwarantanny i uprawnień w różnych grupach, w tym AdminOnlyPolicy, ograniczony dostęp, pełny dostęp oraz zapewnienie administratorom zabezpieczeń i użytkownikom prostego sposobu zarządzania folderami fałszywie dodatnimi.
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
ms.openlocfilehash: c8f739a82223a9315e5082377b4951a88b1ea1df
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043673"
---
# <a name="how-to-configure-quarantine-permissions-and-policies"></a>Jak skonfigurować uprawnienia i zasady kwarantanny

Zapewnienie administratorom zabezpieczeń i użytkownikom bardzo prostego sposobu zarządzania folderami fałszywie dodatnimi jest niezbędne, biorąc pod uwagę zwiększone zapotrzebowanie na bardziej agresywną postawę bezpieczeństwa wraz z ewolucją pracy hybrydowej. Przyjmując podejście nakazowe, administratorzy i użytkownicy mogą to osiągnąć, korzystając ze wskazówek poniżej.

> [!TIP]
> Aby uzyskać krótki film wideo skierowany do administratorów próbujących ustawić uprawnienia i zasady kwarantanny, [zobacz ten link](https://www.youtube.com/watch?v=vnar4HowfpY). Jeśli jesteś użytkownikiem końcowym, wybierz ten [1-minutowy przegląd](https://www.youtube.com/watch?v=s-vozLO43rI) procesu.

## <a name="what-you-will-need"></a>Co będzie potrzebne
- Wystarczające uprawnienia (rola administratora zabezpieczeń)
- 5 minut na wykonanie poniższych kroków.

## <a name="creating-custom-quarantine-policies-with-request-release-flow"></a>Tworzenie niestandardowych zasad kwarantanny przy użyciu przepływu żądania wydania

Nasze zasady niestandardowe dają administratorom możliwość decydowania, jakie elementy użytkownicy mogą sklasyfikować w folderze ***Fałszywie dodatni** _ z rozszerzoną możliwością umożliwienia użytkownikowi żądania _release* tych elementów z folderu.

1. Zdecyduj, jaką kategorię werdyktów (zbiorczo, spam, phish, phish o wysokiej pewności lub złośliwego oprogramowania) elementów, które chcesz sklasyfikować, a nie klasyfikować.
1. W przypadku tych kategorii, które nie mają być klasyfikowane przez użytkowników, przypisz elementy do **elementu AdminOnlyPolicy**. Jeśli chodzi o kategorię, którą użytkownicy mają klasyfikować z ograniczonym dostępem, możesz *utworzyć zasady niestandardowe* z dostępem do wersji żądania i przypisać użytkowników do tej kategorii.
1. **Zdecydowanie zaleca** się przypisanie złośliwego oprogramowania i wysoce zaufanych elementów phish do **adminOnlyPolicy**, regularne elementy phish zaufania mają *ograniczony dostęp z wydaniem żądania*, podczas gdy zbiorcze i spamowe mogą być pozostawione jako pełny dostęp dla użytkowników.

> [!IMPORTANT]
> Aby uzyskać więcej informacji na temat sposobu tworzenia szczegółowych zasad niestandardowych, zobacz [Zasady kwarantanny — Office 365 | Microsoft Docs](../../office-365-security/quarantine-policies.md).

## <a name="assigning-quarantine-policies-and-enabling-notification-with-organization-branding"></a>Przypisywanie zasad kwarantanny i włączanie powiadomień za pomocą znakowania organizacji

Po podjęciu decyzji o kategoriach elementów, które użytkownicy mogą klasyfikować lub nie klasyfikować, i utworzeniu odpowiednich zasad kwarantanny administratorzy powinni przypisać te zasady do odpowiednich użytkowników i włączyć powiadomienia.

1. Zidentyfikuj użytkowników, grupy lub domeny, które chcesz uwzględnić w kategorii *pełnego dostępu* w porównaniu z kategorią *ograniczony dostęp* w porównaniu z *kategorią Tylko administrator* .
1. Zaloguj się do [portalu zabezpieczeń firmy Microsoft](https://security.microsoft.com).
1. Wybierz pozycję Zasady współpracy  > **& poczty e-mail****& reguły**.
1. Wybierz pozycję **Zasady zagrożeń**.
1. Wybierz jedną z następujących opcji: **Zasady ochrony przed spamem**, **zasady ochrony przed wyłudzaniem informacji**, **zasady ochrony przed złośliwym oprogramowaniem**.
1. Wybierz pozycję **Utwórz zasady** i wybierz pozycję **Przychodzące**.
1. Dodaj nazwę zasad, użytkowników, grupy lub domeny, do których mają zostać zastosowane zasady, i **Dalej**.
1. Na karcie **Akcje** wybierz pozycję **Komunikat kwarantanny** dla kategorii. Zauważysz dodatkowy panel dla *wybranych zasad kwarantanny*, korzystając z tej listy rozwijanej, aby wybrać utworzone wcześniej zasady kwarantanny.
1. Przejdź do sekcji **Przegląd** i kliknij przycisk **Potwierdź** , aby utworzyć nowe zasady.
1. Powtórz te same kroki dla innych zasad: **zasad ochrony przed wyłudzaniem informacji**, **zasad ochrony przed złośliwym oprogramowaniem** i **zasad załączników Sejf**.

> [!TIP]
> Aby uzyskać bardziej szczegółowe informacje na temat zdobytych do tej pory informacji, zobacz [Konfigurowanie zasad filtrowania spamu — Office 365 | ](../../office-365-security/configure-your-spam-filter-policies.md)|  Microsoft Docs [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w ramach EOP — Office 365 | ](../../office-365-security/configure-anti-phishing-policies-eop.md) |  Microsoft Docs [Konfiguruj zasady ochrony przed złośliwym oprogramowaniem — Office 365 | ](../../office-365-security/configure-anti-malware-policies.md)|  Microsoft Docs [Konfiguruj zasady załączników Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender — Office 365 | Microsoft Docs](../../office-365-security/set-up-safe-attachments-policies.md)

## <a name="next-steps"></a>Następne kroki

- Użyj **zasad globalnych** dostępnych w zasadach kwarantanny, aby włączyć logo znakowania organizacji, nazwę wyświetlaną i zastrzeżenie.
- Ustaw również **częstotliwość użytkownika na 1 dzień** dla powiadomienia o kwarantannie.

## <a name="more-information"></a>Więcej informacji

Dowiedz się więcej o ustawieniach znakowania i powiadomień organizacji tutaj [Zasady kwarantanny — Office 365 | Microsoft Docs](../../office-365-security/quarantine-policies.md)
