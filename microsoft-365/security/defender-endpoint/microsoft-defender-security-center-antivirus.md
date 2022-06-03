---
title: Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia Windows
description: Dzięki Program antywirusowy Microsoft Defender teraz uwzględnionym w aplikacji Zabezpieczenia Windows można przeglądać, porównywać i wykonywać typowe zadania.
keywords: wdav, oprogramowanie antywirusowe, zapora, zabezpieczenia, okna
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: bd045ac36f1685c3bf12cedf04dd074ed6c7fc5e
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873991"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia Windows

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

W Windows 10 w wersji 1703 i nowszej aplikacja Windows Defender jest częścią Zabezpieczenia Windows.

Ustawienia, które wcześniej były częścią klienta Windows Defender i głównego Windows Ustawienia, zostały połączone i przeniesione do nowej aplikacji, która jest domyślnie instalowana w ramach Windows 10, wersja 1703.

> [!IMPORTANT]
> Wyłączenie usługi aplikacji Zabezpieczenia Windows nie powoduje wyłączenia Program antywirusowy Microsoft Defender ani [Zapora Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Są one wyłączane automatycznie, gdy jest zainstalowany i aktualizowany program antywirusowy innej firmy lub produkt zapory.
> Jeśli wyłączysz usługę Zabezpieczenia Windows app service lub skonfigurujesz skojarzone z nią ustawienia zasady grupy, aby uniemożliwić jej uruchomienie lub uruchomienie, aplikacja Zabezpieczenia Windows może wyświetlać nieaktualne lub niedokładne informacje o wszelkich programach antywirusowych lub produktach zapory zainstalowanych na urządzeniu.
> Może to również uniemożliwić Program antywirusowy Microsoft Defender włączanie się, jeśli masz stary lub nieaktualny program antywirusowy innej firmy lub odinstalujesz jakiekolwiek produkty antywirusowe innych firm, które mogły być wcześniej zainstalowane.
> Znacznie obniży to ochronę urządzenia i może prowadzić do infekcji złośliwym oprogramowaniem.

Aby uzyskać więcej informacji na temat innych funkcji zabezpieczeń Windows, które można monitorować w aplikacji, zobacz [artykuł Zabezpieczenia Windows](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

Aplikacja Zabezpieczenia Windows jest interfejsem klienta w Windows 10 w wersji 1703 lub nowszej. To nie Microsoft 365 Defender portal internetowy służy do przeglądania [Ochrona punktu końcowego w usłudze Microsoft Defender i zarządzania](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) nimi.

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>Przeglądanie ustawień ochrony przed wirusami i zagrożeniami w aplikacji Zabezpieczenia Windows

:::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Ustawienia ochrony przed wirusami i zagrożeniami w aplikacji Zabezpieczenia Windows" lightbox="../../media/wdav-protection-settings-wdsc.png":::

1. Otwórz aplikację Zabezpieczenia Windows, klikając ikonę osłony na pasku zadań lub wyszukując menu Start w **poszukiwaniu Zabezpieczenia Windows**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusami (lub ikonę osłony na pasku menu po lewej stronie).

W poniższych sekcjach opisano sposób wykonywania niektórych typowych zadań podczas przeglądania lub interakcji z ochroną przed zagrożeniami zapewnianą przez Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia Windows.

> [!NOTE]
> Jeśli te ustawienia zostaną skonfigurowane i wdrożone przy użyciu zasady grupy, ustawienia opisane w tej sekcji będą wyszarzone i niedostępne do użycia w poszczególnych punktach końcowych. Zmiany wprowadzone za pośrednictwem obiektu zasady grupy należy najpierw wdrożyć w poszczególnych punktach końcowych, zanim ustawienie zostanie zaktualizowane w Windows Ustawienia. W [temacie Konfigurowanie interakcji użytkownika końcowego z Program antywirusowy Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md) opisano sposób konfigurowania ustawień zastępowania zasad lokalnych.

## <a name="run-a-scan-with-the-windows-security-app"></a>Uruchamianie skanowania przy użyciu aplikacji Zabezpieczenia Windows

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując menu Start dla pozycji **Zabezpieczenia**, a następnie wybierając **pozycję Zabezpieczenia Windows**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusami (lub ikonę osłony na pasku menu po lewej stronie).

3. Wybierz pozycję **Szybkie skanowanie**. Możesz też uruchomić pełne skanowanie, wybierz **opcję Skanuj**, a następnie wybierz opcję, taką jak **Pełne skanowanie**.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>Przejrzyj wersję aktualizacji analizy zabezpieczeń i pobierz najnowsze aktualizacje w aplikacji Zabezpieczenia Windows

:::image type="content" source="../../media/wdav-wdsc-defs.png" alt-text="Numer wersji analizy zabezpieczeń" lightbox="../../media/wdav-wdsc-defs.png":::

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując menu Start dla pozycji *Zabezpieczenia*, a następnie wybierając **pozycję Zabezpieczenia Windows**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusami (lub ikonę osłony na pasku menu po lewej stronie).

3. Wybierz pozycję **Aktualizacje ochrony przed zagrożeniami & wirusami**. Aktualnie zainstalowana wersja jest wyświetlana wraz z pewnymi informacjami o tym, kiedy została pobrana. Możesz sprawdzić bieżącą wersję pod kątem najnowszej dostępnej wersji do ręcznego pobrania lub przejrzeć dziennik zmian dla tej wersji. Zobacz [Aktualizacje analizy zabezpieczeń dla Program antywirusowy Microsoft Defender i innych programów chroniących przed złośliwym kodem firmy Microsoft](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus).

4. Wybierz pozycję **Sprawdź aktualizacje** , aby pobrać nowe aktualizacje ochrony (jeśli istnieją).

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>Upewnij się, Program antywirusowy Microsoft Defender jest włączona w aplikacji Zabezpieczenia Windows

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując menu Start dla pozycji *Zabezpieczenia*, a następnie wybierając **pozycję Zabezpieczenia Windows**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusami (lub ikonę osłony na pasku menu po lewej stronie).

3. Wybierz pozycję **Ustawienia ochrony przed zagrożeniami & wirusów**.

4. Przełącz przełącznik **ochrony w czasie rzeczywistym** na **Wł**.

    > [!NOTE]
    > Jeśli wyłączysz **ochronę w czasie rzeczywistym** , zostanie ona automatycznie włączona po krótkim opóźnieniu. Ma to na celu zapewnienie ochrony przed złośliwym oprogramowaniem i zagrożeniami.
    > Jeśli instalujesz inny produkt antywirusowy, Program antywirusowy Microsoft Defender automatycznie wyłącza się i jest wskazywany jako taki w aplikacji Zabezpieczenia Windows. Zostanie wyświetlone ustawienie umożliwiające włączenie [ograniczonego okresowego skanowania](limited-periodic-scanning-microsoft-defender-antivirus.md).

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>Dodawanie wykluczeń dla Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia Windows

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując menu Start dla pozycji *Zabezpieczenia*, a następnie wybierając **pozycję Zabezpieczenia Windows**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusami (lub ikonę osłony na pasku menu po lewej stronie).

3. W obszarze **Ustawienia ochrony przed wirusami i zagrożeniami** wybierz opcję **Zarządzaj ustawieniami**.

4. W obszarze **Wykluczenia** wybierz pozycję **Dodaj lub usuń wykluczenia**.

5. Wybierz ikonę plusa (**+**), aby wybrać typ i ustawić opcje dla każdego wykluczenia.

Poniższa tabela zawiera podsumowanie typów wykluczeń i tego, co się stanie:

|Typ wykluczenia|Zdefiniowane przez|Efekt|
|---|---|---|
|**Plik**|Lokalizacja <br/>Przykład: `c:\sample\sample.test`|Określony plik jest pomijany przez Program antywirusowy Microsoft Defender.|
|**Folder**|Lokalizacja <br/>Przykład: `c:\test\sample`|Wszystkie elementy w określonym folderze są pomijane przez Program antywirusowy Microsoft Defender.|
|**Typ pliku**|Formatem <br/>Przykład: `.test`|Wszystkie pliki z rozszerzeniem `.test` w dowolnym miejscu na urządzeniu są pomijane przez Program antywirusowy Microsoft Defender.|
|**Proces**|Ścieżka pliku wykonywalnego <br>Przykład: `c:\test\process.exe`|Określony proces i wszystkie pliki otwierane przez ten proces są pomijane przez Program antywirusowy Microsoft Defender.|

Aby dowiedzieć się więcej, zobacz następujące zasoby:

- [Konfigurowanie i weryfikowanie wykluczeń na podstawie rozszerzenia pliku i lokalizacji folderu](./configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie wykluczeń dla plików otwieranych przez procesy](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-for-cloud-app"></a>Przeglądanie historii wykrywania zagrożeń w aplikacji Windows Defender for Cloud

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując menu Start dla pozycji *Zabezpieczenia*, a następnie wybierając **pozycję Zabezpieczenia Windows**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusami (lub ikonę osłony na pasku menu po lewej stronie).

3. Wybierz pozycję **Historia ochrony**. Wszystkie ostatnie elementy są wyświetlane na liście.

## <a name="set-ransomware-protection-and-recovery-options"></a>Ustawianie opcji ochrony przed oprogramowaniem wymuszającym okup i odzyskiwania

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując menu Start dla pozycji *Zabezpieczenia*, a następnie wybierając **pozycję Zabezpieczenia Windows**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusami (lub ikonę osłony na pasku menu po lewej stronie).

3. W obszarze **Ochrona przed oprogramowaniem wymuszającym okup** wybierz pozycję **Zarządzaj ochroną przed oprogramowaniem wymuszającym okup**.

4. Aby zmienić ustawienia **dostępu do kontrolowanych folderów** , zobacz [Protect important folders with Controlled folder access (Ochrona ważnych folderów przy użyciu kontrolowanego dostępu do folderów](/microsoft-365/security/defender-endpoint/controlled-folders)).

5. Aby skonfigurować opcje odzyskiwania oprogramowania wymuszającego okup, wybierz pozycję **Skonfiguruj** w obszarze **Odzyskiwanie danych oprogramowania wymuszającego okup** i postępuj zgodnie z instrukcjami dotyczącymi łączenia lub konfigurowania konta OneDrive, aby można było łatwo odzyskać sprawności po ataku wymuszającym okup.

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)
