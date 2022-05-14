---
title: Konfigurowanie lokalnych przesłoń dla ustawień Program antywirusowy Microsoft Defender
description: Włącz lub wyłącz użytkowników przed zmianą ustawień lokalnie w usłudze Microsoft Defender AV.
keywords: przesłonięcia lokalne, zasady lokalne, zasady grupy, obiekt zasad grupy, blokada, scalanie, listy
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 8de4450247d917f0e4d5023febf6d41c80f0688d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416645"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad Program antywirusowy Microsoft Defender lub zezwalanie na nie


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Domyślnie Program antywirusowy Microsoft Defender ustawienia wdrożone za pośrednictwem obiektu zasady grupy do punktów końcowych w sieci uniemożliwią użytkownikom lokalną zmianę ustawień. Można to zmienić w niektórych wystąpieniach.

Na przykład może być konieczne zezwolenie niektórym grupom użytkowników (takim jak badacze zabezpieczeń i badacze zagrożeń) na dalszą kontrolę nad poszczególnymi ustawieniami w używanych punktach końcowych.

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>Konfigurowanie lokalnych przesłoń dla ustawień Program antywirusowy Microsoft Defender

Ustawieniem domyślnym tych zasad jest **Wyłączone**.

Jeśli są one ustawione na **włączone**, użytkownicy w punktach końcowych mogą wprowadzać zmiany w skojarzonym ustawieniu z aplikacją [Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md), ustawieniami zasady grupy lokalnym i poleceniami cmdlet programu PowerShell (w stosownych przypadkach).

W poniższej tabeli wymieniono każde ustawienie zasad zastępowania oraz instrukcje konfiguracji skojarzonej funkcji lub ustawienia.

Aby skonfigurować następujące ustawienia:

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i kliknij pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki** >  **Program antywirusowy Microsoft Defender** a następnie **lokalizację** określoną w tabeli ustawień (w tym artykule).

4. Kliknij dwukrotnie **ustawienie** zasad, jak określono w poniższej tabeli, i ustaw opcję na żądaną konfigurację. Kliknij przycisk **OK** i powtórz dla innych ustawień.

5. Wdróż obiekt zasady grupy jak zwykle.

## <a name="table-of-settings"></a>Tabela ustawień

<br/><br/>

| Lokalizacja | Ustawienie | Artykułu |
|---|---|---|---|
| MAPY |Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby raportowania do usługi Microsoft MAPS|[Włączanie ochrony dostarczanej w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md) |
| Kwarantanna|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby usuwania elementów z folderu Kwarantanna|[Konfigurowanie korygowania na potrzeby skanowania](configure-remediation-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie zastąpienia ustawień lokalnych na potrzeby monitorowania działania plików i programów na komputerze|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby monitorowania aktywności plików przychodzących i wychodzących | [Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby skanowania wszystkich pobranych plików i załączników|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby włączania monitorowania zachowania|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Ochrona w czasie rzeczywistym|Konfigurowanie przesłonięcia ustawień lokalnych w celu włączenia ochrony w czasie rzeczywistym|[Włączanie i konfigurowanie Program antywirusowy Microsoft Defender zawsze włączonej ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Korygowania|Konfigurowanie przesłonięcia ustawień lokalnych na czas dnia w celu uruchomienia zaplanowanego pełnego skanowania w celu ukończenia korygowania|[Konfigurowanie korygowania na potrzeby skanowania](configure-remediation-microsoft-defender-antivirus.md) |
| Skanowania|Konfigurowanie przesłonięcia ustawień lokalnych dla maksymalnego procentu wykorzystania procesora CPU|[Konfigurowanie i uruchamianie skanowania](run-scan-microsoft-defender-antivirus.md) |
| Skanowania|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby zaplanowanego dnia skanowania|[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Skanowania|Konfigurowanie przesłonięcia ustawień lokalnych dla zaplanowanego czasu szybkiego skanowania|[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Skanowania|Konfigurowanie przesłonięcia ustawień lokalnych dla zaplanowanego czasu skanowania|[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Skanowania|Konfigurowanie przesłonięcia ustawienia lokalnego dla typu skanowania do użycia w przypadku zaplanowanego skanowania|[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>Konfigurowanie sposobu scalania list korygowania zagrożeń i wykluczeń zdefiniowanych lokalnie i globalnie

Można również skonfigurować sposób łączenia lub scalania list zdefiniowanych lokalnie z listami zdefiniowanymi globalnie. To ustawienie dotyczy [list wykluczeń](configure-exclusions-microsoft-defender-antivirus.md), [określonych list korygowania](configure-remediation-microsoft-defender-antivirus.md) i [zmniejszania obszaru ataków](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction).

Domyślnie listy skonfigurowane w lokalnych zasadach grupy i aplikacja Zabezpieczenia Windows są scalane z listami zdefiniowanymi przez odpowiedni obiekt zasady grupy wdrożony w sieci. W przypadku konfliktów pierwszeństwo ma lista zdefiniowana globalnie.

To ustawienie można wyłączyć, aby upewnić się, że używane są tylko listy zdefiniowane globalnie (na przykład z dowolnych wdrożonych obiektów zasad grupy).

### <a name="use-group-policy-to-disable-local-list-merging"></a>Użyj zasady grupy, aby wyłączyć scalanie listy lokalnej

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i kliknij pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender**.

4. Kliknij **dwukrotnie pozycję Konfiguruj zachowanie scalania administratora lokalnego dla list** i ustaw opcję **Wyłączone**. Kliknij przycisk **OK**.

> [!NOTE]
> Wyłączenie scalania listy lokalnej spowoduje zastąpienie kontrolowanych ustawień dostępu do folderów. Zastępuje również wszystkie chronione foldery lub dozwolone aplikacje ustawione przez administratora lokalnego. Aby uzyskać więcej informacji na temat ustawień dostępu do folderów kontrolowanych, zobacz [Zezwalaj na zablokowaną aplikację w Zabezpieczenia Windows](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="related-topics"></a>Tematy pokrewne

- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Konfigurowanie interakcji użytkownika końcowego z Program antywirusowy Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
