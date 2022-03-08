---
title: Zarządzanie procesem stopniowego wdrażanie aktualizacji programu Microsoft Defender
description: Informacje na temat procesu stopniowej aktualizacji i kontrolek
keywords: aktualizowanie, proces aktualizacji, kontrolki, zwalnianie
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 177a7965d3e5a2d4ddd2e62bdde95fbc2762645b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329603"
---
# <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a>Zarządzanie procesem stopniowego wdrażanie aktualizacji programu Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ważne jest, aby zapewnić, że składniki klienta są aktualne, aby zapewnić krytyczne funkcje ochrony i zapobiec atakom.

Możliwości są zapewniane przez kilka składników:

- [Wykrywanie punktu końcowego & odpowiedzi](overview-endpoint-detection-response.md)
- [Ochrona następnej generacji z](microsoft-defender-antivirus-windows.md) [ochroną dostarczaną w chmurze](cloud-protection-microsoft-defender-antivirus.md)
- [Zmniejszenie powierzchni ataków](overview-attack-surface-reduction.md)

Aktualizacje są zwalniane co miesiąc w procesie stopniowego wydania. Ten proces ułatwia wykrywanie wczesnego błędu w celu uchwycenia wpływu jego wystąpienia i szybkiego rozwiązania tego problemu przed większymi awarii.

> [!NOTE]
> Aby uzyskać więcej informacji na temat kontrolowania aktualizacji codziennej analizy zabezpieczeń, zobacz Planowanie [Program antywirusowy Microsoft Defender aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md). Aktualizacje zapewniają, że ochrona następnej generacji może chronić się przed nowymi zagrożeniami, nawet jeśli ochrona dostarczana w chmurze nie jest dostępna dla punktu końcowego.

## <a name="microsoft-gradual-rollout-model"></a>Model stopniowego wdrażanie firmy Microsoft

W przypadku comiesięcznych aktualizacji usługi Defender następuje następujący model stopniowego wdrażanie:

1. Pierwsza wersja trafia do subskrybentów kanału Beta.
2. Po weryfikacji, opiniach i poprawkach rozpoczynamy proces stopniowego wdrażanie w sposób ograniczany, a najpierw zaczynamy od wersji Preview dla subskrybentów kanału.
3. Następnie przechodzimy do wydania aktualizacji dla reszty populacji globalnej, skalując skalowanie z 10 do 100%.

Nasi inżynierowie nieustannie monitorują wpływ i eskalują wszelkie problemy, aby utworzyć poprawkę zgodnie z potrzebami.

## <a name="how-to-customize-your-internal-deployment-process"></a>Jak dostosować wewnętrzny proces wdrażania

Jeśli Twoje komputery otrzymują aktualizacje usługi Defender z usługi Windows Update, proces stopniowego wdrażanie może spowodować, że niektóre komputery będą otrzymywać aktualizacje programu Defender wcześniej niż inne. W poniższej sekcji wyjaśniono, jak zdefiniować strategię, która umożliwi innym przepływ aktualizacji automatycznych do określonych grup urządzeń przez wykorzystanie konfiguracji kanału aktualizacji.

> [!NOTE]
> Podczas planowania własnego, stopniowego wydania pamiętaj, aby zawsze mieć wybór urządzeń z subskrypcją wersji Preview i kanałów etapowych. Pozwoli to Twojej organizacji i firmie Microsoft na zapobieganie problemom specyficznym dla Twojego środowiska oraz rozwiązywanie tych problemów.

W przypadku komputerów otrzymujących aktualizacje za pośrednictwem na przykład programu Windows Server Update Services (WSUS) lub Microsoft Endpoint Configuration Manager (MECM) dostępnych jest więcej opcji dla wszystkich aktualizacji programu Windows, w tym opcje programu Microsoft Defender dla punktu końcowego.

- Aby dowiedzieć się więcej o tym, jak używać rozwiązania, takiego jak WSUS i MECM, do zarządzania dystrybucją i stosowaniem aktualizacji, zobacz Zarządzanie aktualizacjami programu Program antywirusowy Microsoft Defender i stosowanie linii bazowych — [Windows zabezpieczeń](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).

## <a name="update-channels-for-monthly-updates"></a>Aktualizowanie kanałów w celu comiesięcznych aktualizacji

Możesz przypisać komputer do kanału aktualizacji, aby zdefiniować czas, w którym komputer otrzymuje comiesięczne aktualizacje aparatu i platformy.

Aby uzyskać więcej informacji na temat konfigurowania aktualizacji, zobacz Tworzenie niestandardowego procesu stopniowego [wdrażanie aktualizacji programu Microsoft Defender](configure-updates.md).

Dostępne są następujące kanały aktualizacji:

<br>

****

|Nazwa kanału|Opis|Aplikacja|
|---|---|---|
|Kanał Beta — wersja wstępna|Testowanie aktualizacji przed innymi|Urządzenia ustawione dla tego kanału będą pierwszymi użytkownikami, które będą otrzymywać nowe comiesięczne aktualizacje. Wybierz pozycję Kanał Beta, aby wziąć udział w identyfikowaniu problemów i zgłaszaniu problemów firmie Microsoft. Urządzenia w niejawnym Windows są domyślnie subskrybowane w tym kanale. Do używania tylko w środowiskach testowych.|
|Bieżący kanał (wersja Preview)|Wcześniejsze uzyskiwanie aktualizacji bieżącego **kanału** w trakcie stopniowego wydania|Urządzenia ustawione dla tego kanału będą oferowane najwcześniej w trakcie stopniowego cyklu wydania. Sugerowane dla środowisk przedprodukennych/sprawdzania poprawności.|
|Bieżący kanał (etapowy)|Późniejsze uzyskiwanie aktualizacji z bieżącego kanału w trakcie stopniowego wydania|Urządzenia będą oferowane w późniejszym czasie w ramach stopniowego cyklu wydania. Sugerowane zastosowanie do małej, reprezentatywnej części populacji urządzenia (~10%).|
|Bieżący kanał (szeroki)|Uzyskiwanie aktualizacji na końcu stopniowego wydania|Urządzenia będą oferowane aktualizacje dopiero po zakończeniu stopniowego cyklu wydań. Sugerowane zastosowanie do szerokiego zestawu urządzeń w populacji produkcyjnej (~10–100%).|
|Krytyczne: Opóźnienie czasu|Opóźnianie aktualizacji usługi Defender|Za urządzenia będą oferowane aktualizacje z 48-godzinnym opóźnieniem. Najlepsze w przypadku komputerów centrów danych, które otrzymują tylko ograniczone aktualizacje. Sugerowane tylko w środowiskach krytycznych.|
|(domyślne)||Jeśli wyłączysz lub nie skonfigurujesz tych zasad, urządzenie pozostanie w bieżącym kanale (ustawienie domyślne): Bądź na bieżąco automatycznie w trakcie stopniowego cyklu wydania. Ta możliwość jest przeznaczona dla większości urządzeń.|
|

### <a name="update-channels-for-daily-updates"></a>Aktualizowanie kanałów na codzienne aktualizacje

Możesz również przypisać komputer do kanału, aby zdefiniować cadence, w którym otrzymuje on codzienne aktualizacje. Należy zauważyć, że w przeciwieństwie do procesu miesięcznego nie ma kanału beta i ten stopniowy cykl wydania występuje wiele razy dziennie.

<br>

****

|Nazwa kanału|Opis|Aplikacja|
|---|---|---|
|Bieżący kanał (etapowy)|Późniejsze uzyskiwanie aktualizacji z bieżącego kanału w trakcie stopniowego wydania|Urządzenia będą oferowane w późniejszym czasie w ramach stopniowego cyklu wydania. Sugerowane zastosowanie do małej, reprezentatywnej części populacji urządzenia (~10%).|
|Bieżący kanał (szeroki)|Uzyskiwanie aktualizacji na końcu stopniowego wydania|Urządzenia będą oferowane aktualizacje po stopniowym cyklu wydania. Najlepsze w przypadku komputerów centrów danych, które otrzymują tylko ograniczone aktualizacje. Uwaga: to ustawienie dotyczy wszystkich aktualizacji programu Defender.|
|(domyślne)||Jeśli wyłączysz lub nie skonfigurujesz tych zasad, urządzenie pozostanie w bieżącym kanale (ustawienie domyślne): Bądź na bieżąco automatycznie w trakcie stopniowego cyklu wydania. Odpowiednie dla większości urządzeń|
|

> [!NOTE]
> Jeśli chcesz wymusić aktualizację najnowszego podpisu, zamiast skorzystać z opóźnień, będzie konieczne najpierw usunięcie tych zasad.

## <a name="update-guidance"></a>Wskazówki dotyczące aktualizacji

W większości przypadków zalecaną konfiguracją podczas korzystania z usługi Windows jest umożliwienie punktom końcowym odbierania i stosowania comiesięcznych aktualizacji usługi Defender w momencie ich otrzymania. Zapewnia to najlepszą równowagę między ochroną a możliwym wpływem skojarzonym ze zmianami, które mogą wprowadzać.

W środowiskach, w których istnieje potrzeba bardziej kontrolowanego stopniowego wdrażania automatycznych aktualizacji usługi Defender, rozważ podejście do grup wdrożeń:

1. Weź udział w niejawnym Windows niejawnym programie testów lub przypisz grupę urządzeń do kanału Beta.
2. Wyznacz grupę pilotażową, która zdecyduje się na otrzymywanie nowych aktualizacji wcześnie w kanale wersji Preview, zazwyczaj w środowiskach sprawdzania poprawności.
3. Wyznaczyć grupę komputerów, które otrzymają aktualizacje później podczas stopniowego etapu z kanału etapowego. Zazwyczaj będzie to reprezentatywna próbka ~10% populacji.
4. Wyznaczyć grupę komputerów, które otrzymują aktualizacje po zakończeniu stopniowego cyklu wydań. Są to zazwyczaj ważne systemy produkcyjne.

W przypadku pozostałych urządzeń domyślnie jest odbierane nowe aktualizacje w trakcie procesu stopniowego wdrażanie firmy Microsoft i nie jest wymagana żadna dalsza konfiguracja.

Zaadoptowanie tego modelu:

- Umożliwia testowanie wczesnych wersji, zanim dotrą do środowiska produkcyjnego
- Upewnij się, że środowisko produkcyjne nadal otrzymuje regularne aktualizacje i zapewnij ochronę przed krytycznymi zagrożeniami.

## <a name="management-tools"></a>Narzędzia do zarządzania

Aby utworzyć własny niestandardowy proces stopniowego wdrażanie aktualizacji miesięcznych, możesz użyć następujących narzędzi:

- Zasady grupy
- Microsoft Endpoint Manager
- PowerShell

Aby uzyskać szczegółowe informacje na temat korzystania z tych narzędzi, zobacz Tworzenie niestandardowego procesu stopniowego [wdrażanie aktualizacji programu Microsoft Defender](configure-updates.md).
