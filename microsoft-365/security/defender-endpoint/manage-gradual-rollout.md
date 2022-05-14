---
title: Zarządzanie procesem stopniowego wdrażania aktualizacji usługi Microsoft Defender
description: Dowiedz się więcej o procesie i kontrolkach stopniowej aktualizacji
keywords: aktualizacja, proces aktualizacji, kontrolki, wydanie
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
ms.openlocfilehash: 8f1f2add8196afef6e8bd738586957d7fea15c84
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416337"
---
# <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a>Zarządzanie procesem stopniowego wdrażania aktualizacji usługi Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Ważne jest, aby upewnić się, że składniki klienta są aktualne w celu zapewnienia krytycznych możliwości ochrony i zapobiegania atakom.

Możliwości są udostępniane za pośrednictwem kilku składników:

- [Odpowiedź & wykrywania punktów końcowych](overview-endpoint-detection-response.md)
- [Ochrona nowej generacji](microsoft-defender-antivirus-windows.md) z [ochroną dostarczaną przez chmurę](cloud-protection-microsoft-defender-antivirus.md)
- [Zmniejszanie obszaru podatnego na ataki](overview-attack-surface-reduction.md)

Aktualizacje są wydawane co miesiąc przy użyciu stopniowego procesu wydawania. Ten proces pomaga w umożliwieniu wczesnego wykrywania awarii wychwycenia wpływu w miarę jego występowania i szybkiego rozwiązania problemu przed większym wdrożeniem.

> [!NOTE]
> Aby uzyskać więcej informacji na temat kontrolowania codziennych aktualizacji analizy zabezpieczeń, zobacz [Planowanie aktualizacji Program antywirusowy Microsoft Defender ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md). Aktualizacje zapewniają, że ochrona nowej generacji może chronić przed nowymi zagrożeniami, nawet jeśli ochrona dostarczana przez chmurę nie jest dostępna dla punktu końcowego.

## <a name="microsoft-gradual-rollout-model"></a>Model stopniowego wdrażania firmy Microsoft

W przypadku comiesięcznych aktualizacji usługi Defender jest przestrzegany następujący model stopniowego wdrażania:

1. Pierwsza wersja trafi do subskrybentów kanału beta.
2. Po walidacji, opinii i poprawkach rozpoczynamy proces stopniowego wdrażania w ograniczony sposób i najpierw do subskrybentów kanału w wersji zapoznawczej.
3. Następnie przejdziemy do wydania aktualizacji dla pozostałej części populacji globalnej, skalując w poziomie od 10 do 100%.

Nasi inżynierowie stale monitorują wpływ i eskalują wszelkie problemy, aby w razie potrzeby utworzyć poprawkę.

## <a name="how-to-customize-your-internal-deployment-process"></a>Jak dostosować wewnętrzny proces wdrażania

Jeśli maszyny otrzymują aktualizacje usługi Defender z Windows Update, stopniowy proces wdrażania może spowodować, że niektóre maszyny będą otrzymywać aktualizacje usługi Defender wcześniej niż inne. W poniższej sekcji wyjaśniono, jak zdefiniować strategię, która umożliwi automatyczne aktualizacje przepływać inaczej do określonych grup urządzeń, korzystając z konfiguracji kanału aktualizacji.

> [!NOTE]
> Podczas planowania własnej wersji stopniowej upewnij się, że zawsze masz wybór urządzeń subskrybowanych w wersji zapoznawczej i kanałach etapowych. Zapewni to organizacji, a także firmie Microsoft możliwość zapobiegania lub znajdowania i rozwiązywania problemów specyficznych dla danego środowiska.

W przypadku maszyn odbierających aktualizacje za pośrednictwem, na przykład Windows Server Update Services (WSUS) lub Microsoft Endpoint Configuration Manager (MECM), dostępne są dodatkowe opcje dla wszystkich Windows aktualizacji, w tym opcje dla Ochrona punktu końcowego w usłudze Microsoft Defender.

- Dowiedz się więcej na temat używania rozwiązania, takiego jak WSUS, MECM, do zarządzania dystrybucją i stosowaniem aktualizacji w sekcji [Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych — Windows zabezpieczeń](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).

## <a name="update-channels-for-monthly-updates"></a>Aktualizowanie kanałów dla aktualizacji miesięcznych

Maszynę można przypisać do kanału aktualizacji w celu zdefiniowania okresu, w którym maszyna otrzymuje miesięczne aktualizacje aparatu i platformy.

Aby uzyskać więcej informacji na temat konfigurowania aktualizacji, zobacz [Tworzenie niestandardowego procesu stopniowego wdrażania aktualizacji usługi Microsoft Defender](configure-updates.md).

Dostępne są następujące kanały aktualizacji:

<br>

****

|Nazwa kanału|Opis|Aplikacja|
|---|---|---|
|Kanał beta — wersja wstępna|Testowanie aktualizacji przed innymi|Urządzenia ustawione na ten kanał będą pierwszymi, które będą otrzymywać nowe miesięczne aktualizacje. Wybierz pozycję Beta Channel, aby wziąć udział w identyfikowaniu i zgłaszaniu problemów firmie Microsoft. Urządzenia w Niejawny program testów systemu Windows są domyślnie subskrybowane w tym kanale. Do użytku tylko w środowiskach testowych.|
|Bieżący kanał (wersja zapoznawcza)|Pobieranie aktualizacji bieżącego kanału **wcześniej** podczas stopniowego wydawania|Urządzenia ustawione na ten kanał będą oferowane najwcześniej podczas stopniowego cyklu wydawania. Sugerowane dla środowisk przedprodukcyjnych/walidacyjnych.|
|Bieżący kanał (etapowy)|Pobieranie aktualizacji bieżącego kanału później podczas stopniowego wydawania|Aktualizacje urządzeń będą oferowane później podczas stopniowego cyklu wydawania. Sugerowane zastosowanie do niewielkiej, reprezentatywnej części populacji urządzeń (~10%).|
|Bieżący kanał (szeroki)|Pobieranie aktualizacji po zakończeniu stopniowego wydawania|Urządzenia będą oferowane aktualizacje dopiero po zakończeniu stopniowego cyklu wydawania. Sugerowane zastosowanie do szerokiego zestawu urządzeń w populacji produkcyjnej (~10–100%).|
|Krytyczne: opóźnienie czasu|Opóźnij aktualizacje usługi Defender|Urządzenia będą oferowane aktualizacje z 48-godzinnym opóźnieniem. Najlepiej w przypadku maszyn centrów danych, które otrzymują tylko ograniczone aktualizacje. Sugerowane tylko dla środowisk krytycznych.|
|(wartość domyślna)||Jeśli te zasady zostaną wyłączone lub nie zostaną skonfigurowane, urządzenie pozostanie w bieżącym kanale (domyślnym): bądź na bieżąco automatycznie podczas stopniowego cyklu wydawania. Nadaje się do większości urządzeń.|
|

### <a name="update-channels-for-daily-updates"></a>Aktualizowanie kanałów dla codziennych aktualizacji

Możesz również przypisać maszynę do kanału, aby zdefiniować kadencję, w której otrzymuje codzienne aktualizacje. Należy pamiętać, że w przeciwieństwie do procesu miesięcznego nie ma kanału beta i ten stopniowy cykl wydawania występuje wiele razy dziennie.

<br>

****

|Nazwa kanału|Opis|Aplikacja|
|---|---|---|
|Bieżący kanał (etapowy)|Pobieranie aktualizacji bieżącego kanału później podczas stopniowego wydawania|Aktualizacje urządzeń będą oferowane później podczas stopniowego cyklu wydawania. Sugerowane zastosowanie do niewielkiej, reprezentatywnej części populacji urządzeń (~10%).|
|Bieżący kanał (szeroki)|Pobieranie aktualizacji po zakończeniu stopniowego wydawania|Urządzenia będą oferowane aktualizacje po stopniowej wersji cyklu. Najlepiej w przypadku maszyn centrów danych, które otrzymują tylko ograniczone aktualizacje. Uwaga: to ustawienie dotyczy wszystkich aktualizacji usługi Defender.|
|(wartość domyślna)||Jeśli te zasady zostaną wyłączone lub nie zostaną skonfigurowane, urządzenie pozostanie w bieżącym kanale (domyślnym): bądź na bieżąco automatycznie podczas stopniowego cyklu wydawania. Odpowiedni dla większości urządzeń|
|

> [!NOTE]
> Jeśli chcesz wymusić aktualizację najnowszego podpisu, zamiast korzystać z opóźnienia czasu, musisz najpierw usunąć te zasady.

## <a name="update-guidance"></a>Wskazówki dotyczące aktualizacji

W większości przypadków zalecana konfiguracja podczas korzystania z Windows Update polega na umożliwieniu punktom końcowym otrzymywania i stosowania comiesięcznych aktualizacji usługi Defender w miarę ich pojawiania się. Zapewnia to najlepszą równowagę między ochroną a możliwym wpływem związanym ze zmianami, które mogą wprowadzić.

W przypadku środowisk, w których istnieje potrzeba bardziej kontrolowanego stopniowego wdrażania automatycznych aktualizacji usługi Defender, rozważ podejście do grup wdrożeń:

1. Weź udział w programie Windows Insider lub przypisz grupę urządzeń do kanału beta.
2. Wyznaczyć grupę pilotażową, która decyduje się na dostęp do kanału w wersji zapoznawczej, zazwyczaj środowisk walidacji, w celu wczesnego otrzymywania nowych aktualizacji.
3. Wyznaczyć grupę maszyn, które będą otrzymywać aktualizacje później podczas stopniowego wdrażania z kanału etapowego. Zazwyczaj jest to reprezentatywne ok. 10% populacji.
4. Wyznaczyć grupę maszyn, które odbierają aktualizacje po zakończeniu stopniowego cyklu wydawania. Są to zazwyczaj ważne systemy produkcyjne.

W przypadku pozostałych urządzeń ustawieniem domyślnym jest otrzymywanie nowych aktualizacji w miarę ich pojawiania się podczas procesu stopniowego wdrażania firmy Microsoft i nie jest wymagana żadna dalsza konfiguracja.

Przyjęcie tego modelu:

- Umożliwia testowanie wczesnych wersji, zanim dotrą one do środowiska produkcyjnego
- Upewnij się, że środowisko produkcyjne nadal otrzymuje regularne aktualizacje i zapewnia ochronę przed zagrożeniami krytycznymi.

## <a name="management-tools"></a>Narzędzia do zarządzania

Aby utworzyć własny niestandardowy proces stopniowego wdrażania aktualizacji miesięcznych, możesz użyć następujących narzędzi:

- Zasady grupy
- Microsoft Endpoint Manager
- PowerShell

Aby uzyskać szczegółowe informacje na temat korzystania z tych narzędzi, zobacz [Tworzenie niestandardowego procesu stopniowego wdrażania aktualizacji usługi Microsoft Defender](configure-updates.md).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)