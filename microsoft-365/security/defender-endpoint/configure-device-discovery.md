---
title: Konfigurowanie odnajdowania urządzeń
description: Dowiedz się, jak skonfigurować odnajdowanie urządzeń w aplikacji Microsoft 365 Defender przy użyciu odnajdowania podstawowego lub standardowego
keywords: podstawowe, standardowe, konfigurowanie odnajdowania punktów końcowych, odnajdowanie urządzeń
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
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7b98ebf38d0e2e5ab5ec086e75002d0d660cff4c
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010442"
---
# <a name="configure-device-discovery"></a>Konfigurowanie odnajdowania urządzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Odnajdowanie można skonfigurować tak, aby było w trybie standardowym lub podstawowym. Użyj standardowej opcji, aby aktywnie znaleźć urządzenia w twojej sieci, co będzie lepiej zagwarantować odnajdowanie punktów końcowych i zapewnić bogatszą klasyfikację urządzeń.

Możesz dostosować listę urządzeń używanych do odnajdowania standardowego. Możesz włączyć standardowe odnajdowanie na wszystkich urządzeniach wewnych, które również obsługują tę funkcję (obecnie jest Windows 10 lub nowszym i tylko na urządzeniach z programem Windows Server 2019 lub nowszym) lub wybrać podzbiór lub podzbiór urządzeń, określając ich tagi urządzeń.

## <a name="set-up-device-discovery"></a>Konfigurowanie odnajdowania urządzeń

Aby skonfigurować odnajdowanie urządzeń, w portalu Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">czynności konfiguracyjne</a>:

Przechodzenie **do Ustawienia** >  **uzysłowego odnajdowania**

1. Jeśli chcesz skonfigurować jako tryb odnajdowania w trybie odnajdowania na urządzeniach w trybie odnajdowania, wybierz pozycję **Podstawowe** , a następnie wybierz pozycję **Zapisz.**
2. Jeśli wybrano opcję odnajdowania standardowego, wybierz urządzenia, które mają być używane do aktywnego probowania: wszystkie urządzenia lub podzbiór, określając ich tagi urządzeń, a następnie wybierz pozycję **Zapisz.**

> [!NOTE]
>Standardowe odnajdowanie używa różnych skryptów programu PowerShell do aktywnego połączenia urządzeń w sieci. Te skrypty programu PowerShell są podpisane przez firmę Microsoft i są wykonywane z następującej lokalizacji: `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps`. Na przykład `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\UnicastScannerV1.1.0.ps1`.

## <a name="exclude-devices-from-being-actively-probed-in-standard-discovery"></a>Wykluczanie urządzeń z aktywnego wykrywania standardowego

Jeśli w Twojej sieci znajdują się urządzenia, które nie powinny być aktywnie skanowane (na przykład urządzenia używane jakopotki dla innego narzędzia zabezpieczeń), możesz również zdefiniować listę wykluczeń, aby uniemożliwić ich skanowanie. Pamiętaj, że urządzenia nadal można wykryć przy użyciu podstawowego trybu odnajdowania, a także mogą być one odnajdowanie przy użyciu wielu prób odnajdowania. Te urządzenia będą pasywnie wykryte, ale nie będą aktywnie wykryte.

Na stronie Wykluczenia możesz skonfigurować urządzenia tak, **aby ich nie wykluczały** .

## <a name="select-networks-to-monitor"></a>Wybieranie sieci do monitorowania

 Program Microsoft Defender for Endpoint analizuje sieć i określa, czy jest to sieć firmowa, która musi być monitorowana, czy sieć nienarzędna, która może być ignorowana. Sieci firmowe są zazwyczaj wybierane do monitorowania. Możesz jednak zastąpić tę decyzję, wybierając monitorowanie sieci innych niż firmowe, w których znajdują się urządzenia.

Możesz skonfigurować, gdzie można odnajdować urządzenia, określając sieci, które mają być monitorowane. Jeśli sieć jest monitorowana, można na jej podstawie odnajdowania urządzeń.

Lista sieci, w których można odnajdowywały urządzenia, jest wyświetlana na stronie **Monitorowane sieci** .

> [!NOTE]
> Lista zawiera sieci zidentyfikowane jako sieci firmowe. Jeśli mniej niż 50 sieci zostanie zidentyfikowanych jako sieci firmowe, lista będzie zawierała maksymalnie 50 sieci z urządzeniami najbardziej onboarded.

Lista monitorowanych sieci jest sortowana według całkowitej liczby urządzeń widocznych w sieci w ciągu ostatnich 7 dni.

Filtr można zastosować w celu wyświetlenia dowolnego z następujących stanów odnajdowania sieci:

- **Monitorowane sieci** — sieci, w których jest przeprowadzane odnajdowanie urządzeń.
- **Zignorowane** sieci — ta sieć zostanie zignorowana, a odnajdowanie urządzeń nie będzie na nim przeprowadzane.
- **Wszystkie** — zostaną wyświetlone zarówno sieci monitorowane, jak i zignorowane.

### <a name="configure-the-network-monitor-state"></a>Konfigurowanie stanu monitora sieci

Możesz kontrolować, gdzie ma się odbywać odnajdowanie urządzeń. Monitorowane sieci to sieci, w których będą przeprowadzane odnajdowania urządzeń, i zwykle są to sieci firmowe. Możesz także zignorować sieci lub wybrać wstępną klasyfikację odnajdowania po zmodyfikowaniu stanu.

Wybranie wstępnej klasyfikacji odnajdowania oznacza zastosowanie domyślnego stanu monitora sieciowego wprowadzonego przez system. Wybranie domyślnego stanu monitora sieci wprowadzonego przez system oznacza, że sieci zidentyfikowane jako firmowe będą monitorowane, a sieci zidentyfikowane jako nie firmowe będą automatycznie ignorowane.

1. Wybierz **Ustawienia > Odnajdowanie urządzeń**.
2. Wybierz **pozycję Monitorowane sieci**.
3. Wyświetl listę sieci.
4. Wybierz trzy kropki obok nazwy sieci.
5. Określ, czy chcesz monitorować, zignorować lub użyć początkowej klasyfikacji odnajdowania.

    > [!WARNING]
    >
    > - Wybranie opcji monitorowania sieci, która nie została zidentyfikowana przez usługę Microsoft Defender for Endpoint jako sieć firmową, może spowodować odnajdowanie urządzeń poza siecią firmową, a zatem może wykryć urządzenia domowe lub inne urządzenia spoza firmy.
    > - Wybranie opcji ignorowania sieci zatrzyma monitorowanie i wykrywanie urządzeń w tej sieci. Urządzenia, które zostały już odkryte, nie zostaną usunięte ze spisu, ale nie będą już aktualizowane, a szczegóły będą przechowywane do czasu wygaśnięcia okresu przechowywania danych w uchwale Defender for Endpoint.
    > - Przed podjęciem wyboru opcji monitorowania sieci innych niż firmowe należy się upewnić, że masz na to zgodę. <br>

6. Potwierdź, że chcesz wprowadzić zmianę.

## <a name="explore-devices-in-the-network"></a>Eksplorowanie urządzeń w sieci

Za pomocą poniższego zaawansowanego zapytania wyszukiwania możesz uzyskać więcej kontekstu dla każdej nazwy sieciowej opisanej na liście sieci. Zapytanie zawiera listę wszystkich urządzeń, które były połączone z określoną siecią w ciągu ostatnich 7 dni.

```kusto
DeviceNetworkInfo
| where Timestamp > ago(7d)
| where ConnectedNetworks  != ""
| extend ConnectedNetworksExp = parse_json(ConnectedNetworks)
| mv-expand bagexpansion = array ConnectedNetworks=ConnectedNetworksExp
| extend NetworkName = tostring(ConnectedNetworks ["Name"]), Description = tostring(ConnectedNetworks ["Description"]), NetworkCategory = tostring(ConnectedNetworks ["Category"])
| where NetworkName == "<your network name here>"
| summarize arg_max(Timestamp, *) by DeviceId
```

## <a name="get-information-on-device"></a>Uzyskiwanie informacji na urządzeniu

Aby uzyskać najnowsze pełne informacje na temat określonego urządzenia, możesz użyć następującego zaawansowanego zapytania wyszukiwania.

```kusto
DeviceInfo
| where DeviceName == "<device name here>" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId
```

## <a name="see-also"></a>Zobacz też

- [Omówienie odnajdowania urządzeń](device-discovery.md)
- [Odnajdowanie urządzeń : często zadawane pytania](device-discovery-faq.md)
