---
title: Włączanie środowiska oceny dla Ochrona usługi Office 365 w usłudze Microsoft Defender w środowisku produkcyjnym
description: Kroki aktywowania oceny Ochrona usługi Office 365 w usłudze Microsoft Defender za pomocą licencji wersji próbnej, obsługi rekordów MX, & inspekcji zaakceptowanych domen i połączeń przychodzących.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: a5a14d507f7cd10ff4f7ab62b552ab256f0e4a5e
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499006"
---
# <a name="enable-the-evaluation-environment"></a>Włączanie środowiska oceny

**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł dotyczy [kroku 2 z 3](eval-defender-office-365-overview.md) w procesie konfigurowania środowiska oceny dla Ochrona usługi Office 365 w usłudze Microsoft Defender. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-office-365-overview.md).

Aby włączyć ocenę dla Ochrona usługi Office 365 w usłudze Microsoft Defender, należy wykonać poniższe Ochrona usługi Office 365 w usłudze Microsoft Defender.

:::image type="content" source="../../media/defender/m365-defender-office-eval-enable-steps.png" alt-text="Procedura włączania programu Ochrona usługi Office 365 w usłudze Microsoft Defender w środowisku oceny usługi Microsoft Defender" lightbox="../../media/defender/m365-defender-office-eval-enable-steps.png":::


- [Krok 1. Aktywowanie licencji wersji próbnej](#step-1-activate-trial-licenses)
- [Krok 2. Inspekcja i weryfikowanie publicznego rekordu MX](#step-2-audit-and-verify-the-public-mx-record)
- [Krok 3. Inspekcja zaakceptowanych domen](#step-3-audit-accepted-domains)
- [Krok 4. Inspekcja łączników ruchu przychodzącego](#step-4-audit-inbound-connectors)
- [Krok 5. Aktywowanie oceny](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>Krok 1. Aktywowanie licencji wersji próbnej

Zaloguj się do istniejącego portalu Ochrona usługi Office 365 w usłudze Microsoft Defender lub portalu administracji dzierżawy.

1. Przejdź do portalu administracyjnego.
2. Wybierz pozycję Zakup usług na pasku Szybkie uruchamianie.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="Opcja Zakup usług do kliknięcia w Centrum administracyjne platformy Microsoft 365" lightbox="../../media/mdo-eval/1_m365-purchase-services.png":::

3. Przewiń w dół do Add-On (lub wyszukaj tekst "Defender"), aby znaleźć Ochrona usługi Office 365 w usłudze Microsoft Defender planów.
4. Kliknij pozycję Szczegóły obok planu, który chcesz ocenić.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Przycisk Szczegóły do kliknięcia" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

5. Kliknij link *Rozpocznij bezpłatny okres próbny* .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Hiperlink Rozpocznij bezpłatny okres próbny" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

6. Potwierdź swoją prośbę i kliknij *przycisk Wypróbuj* teraz.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Przycisk Wypróbuj teraz" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>Krok 2. Inspekcja i weryfikowanie publicznego rekordu MX

Aby skutecznie Ochrona usługi Office 365 w usłudze Microsoft Defender wiadomości e-mail, należy przekazywanie przychodzącej zewnętrznej poczty e-mail przez wystąpienie usługi Exchange Online Protection (EOP) skojarzone z dzierżawą.

1. Zaloguj się do portalu administracyjnego usługi M365, rozwiń Ustawienia i wybierz pozycję Domeny.
2. Wybierz zweryfikowaną domenę poczty e-mail i kliknij pozycję Zarządzaj systemem DNS.
3. Zanotuj rekord MX wygenerowany i przypisany do dzierżawy usługi EOP.
4. Uzyskaj dostęp do zewnętrznej (publicznej) strefy DNS i sprawdź podstawowy rekord MX skojarzony z twoją domeną poczty e-mail.
    - *Jeśli twój publiczny rekord MX odpowiada* obecnie adresowi przypisanej usługi EOP (np. tenant-com.mail.protection.outlook.com), nie należy wprowadzać żadnych dodatkowych zmian routingu.
    - Jeśli publiczny rekord MX rozpozna obecnie bramę SMTP innej firmy lub lokalnej, mogą być wymagane dodatkowe konfiguracje routingu.
    - Jeśli publiczny rekord MX rozpozna obecnie rekord mx na Exchange lokalnym, być może nadal korzystasz z modelu hybrydowego, w którym niektóre skrzynki pocztowe adresatów nie zostały jeszcze zmigrowane do usługi EXO.

## <a name="step-3-audit-accepted-domains"></a>Krok 3. Inspekcja zaakceptowanych domen

1. Zaloguj się do Exchange Online administracyjnego, wybierz pozycję Poczta Flow, a następnie kliknij pozycję Zaakceptowane domeny.
2. Z listy zaakceptowanych domen, które zostały dodane i zweryfikowane w Dzierżawie, zanotuj typ **domeny dla podstawowej** domeny poczty e-mail.
    - Jeśli dla typu domeny ustawiono wartość ***Autorytatywny***, zakłada się, że wszystkie skrzynki pocztowe adresatów w Twojej organizacji znajdują się obecnie Exchange Online.
    - Jeśli dla typu domeny ustawiono wartość Przekazywanie ***wewnętrzne, nadal*** możesz być w modelu hybrydowym, w którym niektóre skrzynki pocztowe adresatów nadal znajdują się lokalnie.

## <a name="step-4-audit-inbound-connectors"></a>Krok 4. Inspekcja łączników ruchu przychodzącego

1. Zaloguj się do Exchange Online administracyjnego, wybierz pozycję Poczta Flow, a następnie kliknij pozycję Łączniki.
2. Z listy skonfigurowanych łączników zanotuj wszelkie wpisy od organizacji partnerskiej, które mogą skorelować z bramą SMTP innej firmy.
3. Z listy skonfigurowanych łączników zanotuj wszystkie wpisy oznaczone etykietą  Z serwera poczty e-mail organizacji, co może wskazywać, że jesteś nadal w scenariuszu hybrydowym.

## <a name="step-5-activate-the-evaluation"></a>Krok 5. Aktywowanie oceny

Skorzystaj z instrukcji tutaj, aby aktywować Ochrona usługi Office 365 w usłudze Microsoft Defender oceny z Microsoft 365 Defender sieci.

1. Zaloguj się do dzierżawy przy użyciu konta, które ma dostęp do portalu Microsoft 365 Defender dzierżawy.
2. Określ, czy chcesz, aby **portal sieci Microsoft 365 Defender** był interfejsem domyślnym dla Ochrona usługi Office 365 w usłudze Microsoft Defender sieci (zalecane).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="Przycisk Włącz w Ustawienia umożliwia scentralizowany i ulepszony Microsoft 365 Defender administracji" lightbox="../../media/mdo-eval/1_mdo-eval-activate-eval.png":::

3. Z menu nawigacji wybierz pozycję **Zasady i reguły & w** obszarze Poczta *e-mail & współpracy*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="Polecenie Zasady & element menu Reguły do kliknięcia" lightbox="../../media/mdo-eval/2_mdo-eval-activate-eval.png":::

4. Na *pulpicie nawigacyjnym & reguł zasad* kliknij pozycję **Zasady zagrożeń**.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="Element menu Zasady zagrożeń do kliknięcia" lightbox="../../media/mdo-eval/3_mdo-eval-activate-eval.png":::

5. Przewiń w dół *do przycisku Dodatkowe zasady* i wybierz **kafelek Ochrona usługi Office 365 w usłudze Defender** strony.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="Kafelek Eval Ochrona usługi Office 365 w usłudze Defender Eval" lightbox="../../media/mdo-eval/4_mdo-eval-activate-eval.png":::

6. Teraz określ, czy zewnętrzne trasy poczty e-mail Exchange Online się bezpośrednio, czy do bramy lub usługi innej firmy, i kliknij przycisk Dalej.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="Okienko ustawień Routing w Ochrona usługi Office 365 w usłudze Microsoft Defender sieci Ochrona usługi Office 365 w usłudze Microsoft Defender" lightbox="../../media/mdo-eval/5_mdo-eval-activate-eval.png":::

7. Jeśli używasz bramy innej firmy, wybierz z listy rozwijanej nazwę dostawcy wraz z łącznikiem ruchu przychodzącego skojarzonym z tym rozwiązaniem. Po wyli czasie, gdy znajdziesz odpowiedzi, kliknij przycisk Dalej.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="Okienko ustawień innych firm lub lokalnych w portalu Ochrona usługi Office 365 w usłudze Microsoft Defender sieci Ochrona usługi Office 365 w usłudze Microsoft Defender" lightbox="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png":::

8. Przejrzyj ustawienia i kliknij przycisk **Utwórz ocenę** .

   |Przed|Po|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="Okienko Przeglądanie ustawień w portalu Ochrona usługi Office 365 w usłudze Microsoft Defender sieci" lightbox="../../media/mdo-eval/7-mdo-eval-activate-review.png":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="Powiadomienie o ukończeniu konfiguracji oceny w portalu Ochrona usługi Office 365 w usłudze Microsoft Defender sieci Ochrona usługi Office 365 w usłudze Microsoft Defender." lightbox="../../media/mdo-eval/8-mdo-eval-activate-complete.png":::|
   |

## <a name="next-steps"></a>Następne kroki

Krok 3 z 3. Konfigurowanie programu pilotażowego dla programu Ochrona usługi Office 365 w usłudze Microsoft Defender

Powrót do omówieniem [funkcji Szacowanie Ochrona usługi Office 365 w usłudze Microsoft Defender](eval-defender-office-365-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
