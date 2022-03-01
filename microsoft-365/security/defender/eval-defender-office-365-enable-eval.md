---
title: Włączanie środowiska oceny dla programu Microsoft Defender dla Office 365 w środowisku produkcyjnym
description: Kroki aktywowania usługi Microsoft Defender Office 365 oceny, za pomocą licencji próbnych, obsługi rekordów MX, & inspekcji zaakceptowanych domen i połączeń przychodzących.
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
ms.openlocfilehash: 4d2f77b41dccd5620b96d816869d7d7b6458a798
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013698"
---
# <a name="enable-the-evaluation-environment"></a>Włączanie środowiska oceny

**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł zawiera [krok 2 z 3](eval-defender-office-365-overview.md) w procesie konfigurowania środowiska oceny dla programu Microsoft Defender dla programu Office 365. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-office-365-overview.md).

Aby włączyć ocenę działania usługi Microsoft Defender dla systemu Office 365, należy wykonać poniższe Office 365.

![Procedura włączania usługi Microsoft Defender dla Office 365 w środowisku oceny usługi Microsoft Defender.](../../media/defender/m365-defender-office-eval-enable-steps.png)

- [Krok 1. Aktywowanie licencji wersji próbnej](#step-1-activate-trial-licenses)
- [Krok 2. Inspekcja i weryfikowanie publicznego rekordu MX](#step-2-audit-and-verify-the-public-mx-record)
- [Krok 3. Inspekcja zaakceptowanych domen](#step-3-audit-accepted-domains)
- [Krok 4. Inspekcja łączników ruchu przychodzącego](#step-4-audit-inbound-connectors)
- [Krok 5. Aktywowanie oceny](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>Krok 1. Aktywowanie licencji wersji próbnej

Zaloguj się do istniejącego programu Microsoft Defender dla Office 365 lub portalu administracji dzierżawy.

1. Przejdź do portalu administracyjnego.
2. Wybierz pozycję Zakup usług na pasku Szybkie uruchamianie.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="Kliknij pozycję Zakup usług w okienku nawigacji w Office 365.":::

3. Przewiń w dół do Add-On (lub wyszukaj "Defender"), aby znaleźć usługę Microsoft Defender dla Office 365 planów.
4. Kliknij pozycję Szczegóły obok planu, który chcesz ocenić.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Kliknij przycisk Szczegóły, a następnie.":::

5. Kliknij link *Rozpocznij bezpłatny okres próbny* .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Kliknij w tym panelu pozycję Rozpocznij bezpłatną wersję próbną *hiperlink*.":::

6. Potwierdź swoją prośbę i kliknij *przycisk Wypróbuj* teraz.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Teraz kliknij przycisk Wypróbuj teraz*.":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>Krok 2. Inspekcja i weryfikowanie publicznego rekordu MX

Aby skutecznie ocenić usługę Microsoft Defender Office 365, należy przekazywanie przychodzącej zewnętrznej poczty e-mail przez wystąpienie usługi Exchange Online Protection (EOP) skojarzone z dzierżawą.

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

Skorzystaj z instrukcji tutaj, aby aktywować usługę Microsoft Defender Office 365 oceny z portalu Microsoft 365 Defender sieci.

1. Zaloguj się do dzierżawy przy użyciu konta, które ma dostęp do portalu Microsoft 365 Defender dzierżawy.
2. Określ, czy chcesz, aby **Microsoft 365 Defender portalu** sieciowym był interfejsem domyślnym programu Microsoft Defender Office 365 administracji (zalecane).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="Kliknij przycisk Włącz ustawienia, aby korzystać ze scentralizowanego i ulepszonego Microsoft 365 Defender administracyjnego.":::

3. Z menu nawigacji wybierz pozycję **Zasady i reguły & w** obszarze Poczta *e-mail & współpracy*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="Oto obraz menu Współpraca & e-mail z zasadami i & reguł. Kliknij to!":::

4. Na *pulpicie nawigacyjnym & reguł zasad* kliknij pozycję **Zasady zagrożeń**.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="Obraz pulpitu nawigacyjnego & zasad i strzałki wskazującej zasady zagrożeń. Kliknij ten przycisk dalej!":::

5. Przewiń w dół *do przycisku Dodatkowe zasady* i wybierz kafelek **Szacowanie** Office 365 Defender.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="Kafelek Eval Defender for Office 365 z informacją, że jest to 30-dniowa wersja próbna w & e-mail i wektorach współpracy. Kliknij.":::

6. Teraz określ, czy zewnętrzne trasy poczty e-mail Exchange Online się bezpośrednio, czy do bramy lub usługi innej firmy, i kliknij przycisk Dalej.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="Program Defender for Office 365 będzie oceniać wysyłanie poczty do Twoich Exchange Online pocztowych. Podaj szczegóły dotyczące sposobu rozsyłania poczty, w tym nazwę łącznika ruchu wychodzącego służącego do rozsyłania poczty. Jeśli używasz tylko Exchange Online Protection (EOP), nie będziesz mieć łącznika. Wybierz jedną z opcji Użyj innego dostawcy lub lokalnego albo używam tylko usługi EOP.":::

7. Jeśli używasz bramy innej firmy, wybierz z listy rozwijanej nazwę dostawcy wraz z łącznikiem ruchu przychodzącego skojarzonym z tym rozwiązaniem. Po wyli czasie, gdy znajdziesz odpowiedzi, kliknij przycisk Dalej.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="W tym oknie dialogowym wybierz usługę innego dostawcy używaną przez Twoją organizację lub *Inne*. W następnym oknie dialogowym w dół wybierz łącznik ruchu przychodzącego. Następnie kliknij przycisk Dalej.":::

8. Przejrzyj ustawienia i kliknij przycisk **Utwórz ocenę** .

   |Przed|Po|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="W tym okienku znajduje się lista rozwijana do przeglądania ustawień. W razie potrzeby zawiera ona również link, który można kliknąć, aby edytować typ routingu. Gdy wszystko będzie gotowe, kliknij duży niebieski przycisk Utwórz ocenę.":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="Teraz konfiguracja jest ukończona. Niebieski przycisk na tej stronie informuje: &quot;Przejdź do oceny&quot;.":::|
   |

## <a name="next-steps"></a>Następne kroki

Krok 3 z 3. Konfigurowanie programu pilotażowego programu Microsoft Defender dla systemu Office 365

Wróć do przeglądu [szacowania programu Microsoft Defender dla programu Office 365](eval-defender-office-365-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
