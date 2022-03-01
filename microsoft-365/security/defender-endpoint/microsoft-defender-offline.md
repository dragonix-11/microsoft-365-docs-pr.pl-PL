---
title: Microsoft Defender Offline w programie Windows
description: Możesz używać aplikacji Microsoft Defender Offline bezpośrednio z Program antywirusowy Windows Defender aplikacji. Możesz także zarządzać wdrażaniem tego rozwiązania w sieci.
keywords: skanowanie, defender, offline
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 75179fc3daf8e375ace6cc4c1566abf1e18cdfaa
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2021
ms.locfileid: "63018911"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>Uruchamianie i przeglądanie wyników skanowania Microsoft Defender Offline aplikacji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Offline to narzędzie do skanowania przed złośliwym kodem, które umożliwia uruchamianie i uruchamianie skanowania z zaufanego środowiska. Skanowanie jest uruchamiane poza normalnym procesem Windows, więc może kierować złośliwe oprogramowanie, które próbuje obejść powłokę Windows, takie jak wirusy i zestawy główne, które infekują lub zastąpią główny rekord rozruchu (MBR).

Możesz użyć Microsoft Defender Offline, jeśli podejrzewasz zainfekowanie złośliwym oprogramowaniem lub chcesz potwierdzić dokładny oczyszczanie punktu końcowego po epidemii złośliwego oprogramowania.

W Windows 10 i Windows 11 można uruchamiać Microsoft Defender Offline jednym kliknięciem bezpośrednio z Zabezpieczenia Windows [aplikacji](microsoft-defender-security-center-antivirus.md). W poprzednich wersjach pakietu Windows użytkownik musiał zainstalować aplikację Microsoft Defender Offline, aby uruchomić ponownie punkt końcowy i załadować nośnik startowy.

## <a name="prerequisites-and-requirements"></a>wymagania wstępne i wymagania

Microsoft Defender Offline w Windows 10 i Windows 11 mają takie same wymagania sprzętowe jak w Windows 10.

Aby uzyskać więcej informacji Windows 10 i Windows 11, zobacz następujące tematy:

- [Minimalne wymagania sprzętowe](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [Wskazówki dotyczące składników sprzętowych](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender Offline nie jest obsługiwane na komputerach z ARM ani na Windows magazynowych serwera.

Aby można Microsoft Defender Offline z punktu końcowego, użytkownik musi być zalogowany z uprawnieniami administratora.

## <a name="microsoft-defender-offline-updates"></a>Microsoft Defender Offline aktualizacji

Microsoft Defender Offline korzysta z najnowszych aktualizacji ochrony dostępnych w punkcie końcowym; jest on aktualizowany Program antywirusowy Windows Defender aktualizacji.

> [!NOTE]
> Przed uruchomieniem skanowania w trybie offline należy spróbować zaktualizować ochronę audio/wideo programu Microsoft Defender. Możesz wymusić aktualizację za pomocą programu zasady grupy lub jednak normalnie wdrażasz aktualizacje w punktach końcowych lub ręcznie pobrać i zainstalować najnowsze aktualizacje ochrony z poziomu [Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem.](https://www.microsoft.com/security/portal/definitions/adl.aspx)

Aby uzyskać [więcej informacji, Program antywirusowy Microsoft Defender](manage-protection-updates-microsoft-defender-antivirus.md) temat Zarządzanie aktualizacjami analizy zabezpieczeń.

## <a name="usage-scenarios"></a>Scenariusze użycia

W Windows 10 wersji 1607 można ręcznie wymusić skanowanie w trybie offline. Ewentualnie, jeśli Windows Defender, że uruchamianie Microsoft Defender Offline, zostanie wyświetlony monit dla użytkownika na punkcie końcowym.

Konieczność przeprowadzenia skanowania w trybie offline pojawi się również w Microsoft Endpoint Manager, jeśli używasz jej do zarządzania punktami końcowymi.

Monit może zostać wyświetlony za pośrednictwem powiadomienia, podobnego do następującego:

:::image type="content" source="../../media/notification.png" alt-text="Powiadomienie o uruchomieniu Microsoft Defender Offline.":::

Użytkownik zostanie także powiadomiony w Windows Defender klienta.

W Menedżer konfiguracji można określić stan punktów końcowych, przechodząc do tematu Monitorowanie > Przegląd > przegląd > Endpoint Protection stan **> System Center Endpoint Protection zabezpieczeń**.

Microsoft Defender Offline skanowania są oznaczone w obszarze Stan **rozwiązywania problemów ze złośliwym oprogramowaniem jako** **wymagane skanowanie w trybie offline**.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="Microsoft Defender Offline skanowania jest wymagane.":::

## <a name="configure-notifications"></a>Konfigurowanie powiadomień

Microsoft Defender Offline są skonfigurowane w tym samym ustawieniu zasad co inne powiadomienia audio/wideo programu Microsoft Defender.

Aby uzyskać więcej informacji na temat powiadomień Windows Defender, zobacz temat Konfigurowanie powiadomień [wyświetlanych w temacie Punkty końcowe](configure-notifications-microsoft-defender-antivirus.md).

## <a name="run-a-scan"></a>Uruchamianie skanowania

> [!IMPORTANT]
> Przed użyciem programu Microsoft Defender Offline zapisz wszystkie pliki i zamknij uruchomione programy. Skanowanie Microsoft Defender Offline trwa około 15 minut. Po zakończeniu skanowania zostanie on ponownie uruchomiony. Skanowanie odbywa się poza zwykłym środowiskiem Windows środowisku operacyjnym. Interfejs użytkownika będzie wyglądać inaczej niż normalne skanowanie wykonywane przez Windows Defender. Po zakończeniu skanowania punkt końcowy zostanie ponownie uruchomiony i Windows ładowanie normalnie.

Możesz uruchomić skanowanie Microsoft Defender Offline za pomocą następujących czynności:

- PowerShell
- Windows instrumentacja zarządzania (WMI)
- Aplikacja Zabezpieczenia Windows aplikacji



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>Uruchamianie skanowania w trybie offline przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących polecenia cmdlet:

```PowerShell
Start-MpWDOScan
```

Aby [uzyskać więcej informacji na](use-powershell-cmdlets-microsoft-defender-antivirus.md) temat używania programu PowerShell z programem PowerShell z programem Program antywirusowy Microsoft Defender, zobacz Konfigurowanie i uruchamianie poleceń cm Program antywirusowy Microsoft Defender dlet programu PowerShell oraz poleceń [cmdlet programu Defender](/powershell/module/defender/) oraz Program antywirusowy Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>Korzystanie Windows zarządzania (WMI) w celu uruchomienia skanowania w trybie offline

Skorzystaj z [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uruchomić skanowanie w trybie offline.

Poniższy fragment skryptu WMI natychmiast uruchomi skan Microsoft Defender Offline, co spowoduje ponowne uruchomienie punktu końcowego, uruchomienie skanowania w trybie offline, a następnie ponowne uruchomienie i uruchomienie komputera Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

Aby uzyskać więcej informacji, zobacz następujące informacje:

- [Windows Defender interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>Korzystanie z aplikacji Windows Defender Security w celu uruchomienia skanowania w trybie offline

1. Otwórz aplikację Zabezpieczenia Windows, klikając ikonę tarczy na pasku zadań lub wyszukując w menu **startowym pozycję Defender for Cloud**.

2. Kliknij **kafelek Ochrona przed & wirusami** (lub ikonę tarczy na lewym pasku menu), a następnie **etykietę Skanowanie** zaawansowane:

3. Wybierz **Microsoft Defender Offline skanowania i** kliknij przycisk **Skanuj teraz**.

    > [!NOTE]
    > W Windows 10 wersji 1607 skanowanie w trybie offline można było uruchomić z programu **Windows Ustawienia** \> **Update & security** \> **Windows Defender** lub z Windows Defender klienta.

## <a name="review-scan-results"></a>Przeglądanie wyników skanowania

Microsoft Defender Offline wyników skanowania zostaną wyświetlone w sekcji Historia [skanowania w aplikacji Zabezpieczenia Windows skanowania](microsoft-defender-security-center-antivirus.md).

## <a name="related-articles"></a>Artykuły pokrewne

- [Dostosowywanie, inicjowanie i przeglądanie wyników skanów i środków zaradczych](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
