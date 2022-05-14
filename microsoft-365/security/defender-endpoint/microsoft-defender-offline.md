---
title: Microsoft Defender Offline w Windows
description: Możesz użyć Microsoft Defender Offline bezpośrednio z aplikacji Program antywirusowy Windows Defender. Możesz również zarządzać sposobem jej wdrażania w sieci.
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
ms.openlocfilehash: 690437de177ce1f6c466166970a8b7143d230916
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415645"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>Uruchom i przejrzyj wyniki skanowania programu Microsoft Defender Offline

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Microsoft Defender Offline to narzędzie do skanowania oprogramowania chroniącego przed złośliwym kodem, które umożliwia rozruch i uruchamianie skanowania z zaufanego środowiska. Skanowanie jest uruchamiane spoza normalnego jądra Windows, dzięki czemu może być ukierunkowane na złośliwe oprogramowanie, które próbuje ominąć powłokę Windows, takie jak wirusy i zestawy rootkit, które infekują lub zastępują główny rekord rozruchowy (MBR).

Możesz użyć Microsoft Defender Offline, jeśli podejrzewasz infekcję złośliwym oprogramowaniem lub chcesz potwierdzić dokładne oczyszczenie punktu końcowego po wybuchu złośliwego oprogramowania.

W Windows 10 i Windows 11 można uruchamiać Microsoft Defender Offline jednym kliknięciem bezpośrednio z [aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md). W poprzednich wersjach Windows użytkownik musiał zainstalować Microsoft Defender Offline na nośniku rozruchowym, ponownie uruchomić punkt końcowy i załadować nośnik rozruchowy.

## <a name="prerequisites-and-requirements"></a>wymagania wstępne i wymagania

Microsoft Defender Offline w Windows 10 i Windows 11 ma takie same wymagania sprzętowe jak Windows 10.

Aby uzyskać więcej informacji na temat wymagań Windows 10 i Windows 11, zobacz następujące tematy:

- [Minimalne wymagania sprzętowe](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [Wskazówki dotyczące składników sprzętowych](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender Offline nie jest obsługiwana na maszynach z procesorami ARM ani w jednostkach przechowywania zapasów serwera Windows.

Aby uruchomić Microsoft Defender Offline z punktu końcowego, użytkownik musi być zalogowany z uprawnieniami administratora.

## <a name="microsoft-defender-offline-updates"></a>aktualizacje Microsoft Defender Offline

Microsoft Defender Offline korzysta z najnowszych aktualizacji ochrony dostępnych w punkcie końcowym; jest ona aktualizowana za każdym razem, gdy Program antywirusowy Windows Defender jest aktualizowana.

> [!NOTE]
> Przed uruchomieniem skanowania w trybie offline należy podjąć próbę zaktualizowania ochrony usługi Microsoft Defender AV. Możesz wymusić aktualizację za pomocą zasady grupy lub normalnie wdrażać aktualizacje w punktach końcowych lub ręcznie pobrać i zainstalować najnowsze aktualizacje ochrony z [Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem](https://www.microsoft.com/security/portal/definitions/adl.aspx).

Aby uzyskać więcej informacji, zobacz temat [Manage Program antywirusowy Microsoft Defender Security intelligence updates (Zarządzanie aktualizacjami analizy zabezpieczeń Program antywirusowy Microsoft Defender](manage-protection-updates-microsoft-defender-antivirus.md)).

## <a name="usage-scenarios"></a>Scenariusze użycia

W Windows 10 wersji 1607 możesz ręcznie wymusić skanowanie w trybie offline. Alternatywnie, jeśli Windows Defender określi, że Microsoft Defender Offline musi zostać uruchomiona, zostanie wyświetlony monit użytkownika w punkcie końcowym.

Konieczność przeprowadzenia skanowania w trybie offline zostanie również ujawniona w Microsoft Endpoint Manager, jeśli używasz go do zarządzania punktami końcowymi.

Monit może wystąpić za pośrednictwem powiadomienia podobnego do następującego:

:::image type="content" source="../../media/notification.png" alt-text="Powiadomienie o uruchomieniu Microsoft Defender Offline" lightbox="../../media/notification.png":::

Użytkownik zostanie również powiadomiony w ramach klienta Windows Defender.

W Configuration Manager możesz zidentyfikować stan punktów końcowych, przechodząc do pozycji **Monitorowanie > Przegląd > Stan > Endpoint Protection zabezpieczeń > System Center Endpoint Protection stan**.

Microsoft Defender Offline skanowania są wskazywane w **obszarze Stan korygowania złośliwego oprogramowania** jako **wymagane skanowanie w trybie offline**.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="Wskaźnik skanowania pod kątem Microsoft Defender Offline" lightbox="../../media/sccm-wdo.png":::

## <a name="configure-notifications"></a>Konfigurowanie powiadomień

Microsoft Defender Offline powiadomienia są konfigurowane w tym samym ustawieniu zasad co inne powiadomienia av usługi Microsoft Defender.

Aby uzyskać więcej informacji na temat powiadomień w Windows Defender, zobacz [Temat Konfigurowanie powiadomień wyświetlanych w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md).

## <a name="run-a-scan"></a>Uruchamianie skanowania

> [!IMPORTANT]
> Przed użyciem Microsoft Defender Offline pamiętaj o zapisaniu plików i zamknięciu uruchomionych programów. Skanowanie Microsoft Defender Offline trwa około 15 minut. Po zakończeniu skanowania zostanie ponownie uruchomiony punkt końcowy. Skanowanie jest wykonywane poza zwykłym środowiskiem operacyjnym Windows. Interfejs użytkownika będzie wyglądać inaczej niż normalne skanowanie wykonywane przez Windows Defender. Po zakończeniu skanowania punkt końcowy zostanie uruchomiony ponownie, a Windows będzie ładowany normalnie.

Możesz uruchomić skanowanie Microsoft Defender Offline przy użyciu następujących funkcji:

- PowerShell
- Instrumentacja zarządzania Windows (WMI)
- Aplikacja Zabezpieczenia Windows



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>Uruchamianie skanowania w trybie offline przy użyciu poleceń cmdlet programu PowerShell

Użyj następujących poleceń cmdlet:

```PowerShell
Start-MpWDOScan
```

Zobacz [Konfigurowanie i uruchamianie poleceń cmdlet programu PowerShell Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) i [poleceń cmdlet programu antywirusowego Defender](/powershell/module/defender/), aby uzyskać więcej informacji na temat używania programu PowerShell z Program antywirusowy Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>Uruchamianie skanowania w trybie offline przy użyciu instrukcji zarządzania Windows (WMI)

Użyj klasy [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) , aby uruchomić skanowanie w trybie offline.

Poniższy fragment kodu WMI natychmiast uruchomi skanowanie Microsoft Defender Offline, co spowoduje ponowne uruchomienie punktu końcowego, uruchomienie skanowania w trybie offline, a następnie ponowne uruchomienie i rozruch w Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

Aby uzyskać więcej informacji, zobacz następujące informacje:

- [interfejsy API Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>Uruchamianie skanowania w trybie offline przy użyciu aplikacji Windows Defender Security

1. Otwórz aplikację Zabezpieczenia Windows, klikając ikonę osłony na pasku zadań lub wyszukując menu Start w poszukiwaniu **Defender dla Chmury**.

2. Kliknij kafelek **Ochrona przed zagrożeniami & wirusami** (lub ikonę osłony na pasku menu po lewej stronie), a następnie etykietę **Skanowanie zaawansowane** :

3. Wybierz **pozycję Microsoft Defender Offline skanowania** i kliknij pozycję **Skanuj teraz**.

    > [!NOTE]
    > W Windows 10 wersji 1607 skanowanie w trybie offline może być uruchamiane z poziomu **Windows Ustawienia** \> **update & Windows Defender zabezpieczeń** \> lub klienta Windows Defender.

## <a name="review-scan-results"></a>Przeglądanie wyników skanowania

Microsoft Defender Offline wyniki skanowania zostaną wyświetlone w [sekcji Historia skanowania aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="related-articles"></a>Artykuły pokrewne

- [Dostosowywanie, inicjowanie i przeglądanie wyników skanowania i korygowania](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
