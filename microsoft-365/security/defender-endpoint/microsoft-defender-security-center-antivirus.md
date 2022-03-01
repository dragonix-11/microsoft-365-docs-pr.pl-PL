---
title: Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia Windows aplikacji
description: Dzięki Program antywirusowy Microsoft Defender do aplikacji Zabezpieczenia Windows możesz przeglądać, porównywać i wykonywać typowe zadania.
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
ms.openlocfilehash: 5ad0d64ff2f296d0e8282afb02cbe7fc2bb21470
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032092"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia Windows aplikacji

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

W Windows 10 1703 i nowszych wersjach aplikacja Windows Defender jest częścią Zabezpieczenia Windows.

Ustawienia, które były wcześniej częścią klienta Windows Defender i głównego pakietu Windows Ustawienia zostały połączone i przeniesione do nowej aplikacji, która jest domyślnie instalowana jako część Windows 10, wersja 1703.

> [!IMPORTANT]
> Wyłączenie usługi Zabezpieczenia Windows nie powoduje wyłączenia Program antywirusowy Microsoft Defender sieci [Windows Defender sieciowej](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Są one wyłączane automatycznie po zainstalowaniu i aktualizacji produktu oprogramowania antywirusowego lub zapory innej firmy.
>
> Jeśli wyłączysz usługę aplikacji Zabezpieczenia Windows lub skonfigurujesz skojarzone z nią ustawienia programu zasady grupy, aby uniemożliwić jej uruchamianie, aplikacja Zabezpieczenia Windows może wyświetlać nieaktualne lub niedokładne informacje o produktach antywirusowych lub zapory zainstalowanych na urządzeniu.
> Może to również zapobiegać Program antywirusowy Microsoft Defender się, jeśli masz stare lub nieaktualne oprogramowanie antywirusowe innej firmy lub jeśli odinstalujesz jakiekolwiek programy antywirusowe innych firm, które mogły zostać wcześniej zainstalowane.
> Spowoduje to znacznie obniżenie ochrony urządzenia i może spowodować zainfekowanie złośliwym oprogramowaniem.

Aby uzyskać [Zabezpieczenia Windows](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) na temat innych funkcji zabezpieczeń Windows, które mogą być monitorowane w tej aplikacji, zobacz ten artykuł.

Ta Zabezpieczenia Windows to interfejs klienta w Windows 10 wersji 1703 i nowszych. Nie jest to pierwszy Microsoft 365 Defender sieci Web używany do przeglądania programu [Microsoft Defender dla punktu końcowego i zarządzania nim](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>Przeglądanie ustawień ochrony przed wirusami i zagrożeniami w Zabezpieczenia Windows aplikacji

:::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Ustawienia ochrony przed wirusami i zagrożeniami w Zabezpieczenia Windows aplikacji.":::

1. Otwórz aplikację Zabezpieczenia Windows, klikając ikonę tarczy na pasku zadań lub wyszukując w menu start przycisk **Zabezpieczenia Windows**.

2. Wybierz **kafelek Ochrona przed & wirusami** (lub ikonę tarczy na lewym pasku menu).

W poniższych sekcjach opisano sposób wykonywania niektórych z najczęściej wykonywanych zadań podczas przeglądania lub interakcji z ochroną przed zagrożeniami zapewnianą przez aplikację Program antywirusowy Microsoft Defender w Zabezpieczenia Windows aplikacji.

> [!NOTE]
> Jeśli te ustawienia są skonfigurowane i wdrożone przy użyciu programu zasady grupy, ustawienia opisane w tej sekcji będą wyszzarowane i niedostępne do użycia w poszczególnych punktach końcowych. Zmiany wprowadzone za pośrednictwem zasady grupy obiekt musi najpierw zostać wdrożony w poszczególnych punktach końcowych, aby ustawienie było aktualizowane w Windows Ustawienia. W [temacie Konfigurowanie interakcji użytkownika końcowego z programem Program antywirusowy Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md) opisano, jak można skonfigurować ustawienia zastępowania zasad lokalnych.

## <a name="run-a-scan-with-the-windows-security-app"></a>Uruchamianie skanowania za pomocą Zabezpieczenia Windows aplikacji

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując w menu Start pozycję **Zabezpieczenia**, a następnie **wybierając pozycję Zabezpieczenia Windows**.

2. Wybierz **kafelek Ochrona przed & wirusami** (lub ikonę tarczy na lewym pasku menu).

3. Wybierz **pozycję Szybkie skanowanie**. Aby uruchomić pełne skanowanie, wybierz pozycję **Opcje** skanowania, a następnie wybierz opcję, taką jak **Pełne skanowanie**.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>Przejrzyj wersję aktualizacji analizy zabezpieczeń i pobierz najnowsze aktualizacje w aplikacji usługi Zabezpieczenia Windows.

:::image type="content" source="../../media/wdav-wdsc-defs.png" alt-text="Numer wersji analizy zabezpieczeń.":::

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując w menu Start pozycję *Zabezpieczenia*, a następnie **wybierając pozycję Zabezpieczenia Windows**.

2. Wybierz **kafelek Ochrona przed & wirusami** (lub ikonę tarczy na lewym pasku menu).

3. Wybierz **pozycję Aktualizacje & ochrony przed zagrożeniami**. Zostanie wyświetlona obecnie zainstalowana wersja wraz z informacjami na temat tego, kiedy została pobrana. Możesz sprawdzić bieżącą wersję w stosunku do najnowszej wersji dostępnej do ręcznego pobrania lub przejrzeć dziennik zmian dla tej wersji. Zobacz [Aktualizacje analizy zabezpieczeń dla oprogramowania Program antywirusowy Microsoft Defender i innego oprogramowania firmy Microsoft w celu ochrony przed złośliwym kodem](https://www.microsoft.com/wdsi/defenderupdates).

4. Wybierz **pozycję Sprawdź aktualizacje,** aby pobrać nowe aktualizacje ochrony (jeśli istnieją).

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>Upewnij Program antywirusowy Microsoft Defender jest włączona w Zabezpieczenia Windows aplikacji

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując w menu Start pozycję *Zabezpieczenia*, a następnie **wybierając pozycję Zabezpieczenia Windows**.

2. Wybierz **kafelek Ochrona przed & wirusami** (lub ikonę tarczy na lewym pasku menu).

3. Wybierz **pozycję & ustawienia ochrony przed zagrożeniami**.

4. Przełącz ochronę **w czasie rzeczywistym na** **włączoną**.

    > [!NOTE]
    > Jeśli **wyłączysz ochronę w czasie rzeczywistym** , zostanie ona automatycznie włączyć ponownie po krótkiej chwili. Ma to na celu zapewnienie ochrony przed złośliwym oprogramowaniem i zagrożeniami.
    > Jeśli zainstalujesz inny produkt antywirusowy, Program antywirusowy Microsoft Defender automatycznie wyłącza się i jest wskazywany jako na przykład w Zabezpieczenia Windows aplikacji. Zostanie wyświetlone ustawienie umożliwiające włączenie ograniczonego skanowania [okresowego](limited-periodic-scanning-microsoft-defender-antivirus.md).

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>Dodawanie wykluczeń dla Program antywirusowy Microsoft Defender w Zabezpieczenia Windows aplikacji

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując w menu Start pozycję *Zabezpieczenia*, a następnie **wybierając pozycję Zabezpieczenia Windows**.

2. Wybierz **kafelek Ochrona przed & wirusami** (lub ikonę tarczy na lewym pasku menu).

3. W **obszarze & ochrony przed zagrożeniami** wybierz pozycję **Zarządzaj ustawieniami**.

4. W **obszarze Wyjątki** wybierz **pozycję Dodaj lub usuń wykluczenia**.

5. Wybierz ikonę plus (**+**), aby wybrać typ i ustawić opcje dla każdego wykluczenia.

W poniższej tabeli podsumowano typy wykluczeń i to, co się dzieje:

<br>

****
|Typ wykluczenia|Zdefiniowana przez|Co się dzieje|
|---|---|---|
|**Plik**|Lokalizacja <br/>Przykład: `c:\sample\sample.test`|Określony plik zostanie pominięty przez Program antywirusowy Microsoft Defender.|
|**Folder**|Lokalizacja <br/>Przykład: `c:\test\sample`|Wszystkie elementy w określonym folderze są pomijane przez Program antywirusowy Microsoft Defender.|
|**Typ pliku**|Rozszerzenie pliku <br/>Przykład: `.test`|Wszystkie pliki z rozszerzeniem `.test` w dowolnym miejscu na urządzeniu są pomijane przez Program antywirusowy Microsoft Defender.|
|**Proces**|Wykonywalna ścieżka pliku <br>Przykład: `c:\test\process.exe`|Konkretnej procedury i wszystkich plików otwieranych w tym procesie pomija Program antywirusowy Microsoft Defender.|
|

Aby dowiedzieć się więcej, zobacz następujące zasoby:

- [Konfigurowanie i sprawdzanie poprawności wykluczeń na podstawie rozszerzenia pliku i lokalizacji folderu](./configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurowanie wykluczeń dla plików otwieranych przez procesy](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-for-cloud-app"></a>Przeglądanie historii wykrywania zagrożeń w aplikacji Windows Defender dla aplikacji w chmurze

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując w menu Start pozycję *Zabezpieczenia*, a następnie **wybierając pozycję Zabezpieczenia Windows**.

2. Wybierz **kafelek Ochrona przed & wirusami** (lub ikonę tarczy na lewym pasku menu).

3. Wybierz **pozycję Historia ochrony**. Zostaną wyświetlone wszystkie ostatnio dostępne elementy.

## <a name="set-ransomware-protection-and-recovery-options"></a>Ustawianie opcji ochrony i odzyskiwania oprogramowania wymuszającego okup

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując w menu Start pozycję *Zabezpieczenia*, a następnie **wybierając pozycję Zabezpieczenia Windows**.

2. Wybierz **kafelek Ochrona przed & wirusami** (lub ikonę tarczy na lewym pasku menu).

3. W **obszarze Ochrona przed oprogramowaniem wymuszającym** okup wybierz **pozycję Zarządzaj ochroną oprogramowania wymuszającego okup**.

4. Aby zmienić **ustawienia kontrolowanego dostępu do folderu** , zobacz [Chroninie ważnych folderów za pomocą kontrolowanego dostępu do folderu](/microsoft-365/security/defender-endpoint/controlled-folders).

5. Aby skonfigurować opcje odzyskiwania oprogramowania wymuszającego okup, wybierz  pozycję Skonfiguruj w obszarze Odzyskiwanie danych oprogramowania wymuszającego okup i postępuj zgodnie z instrukcjami dotyczącymi łączenia lub konfigurowania konta OneDrive, aby można było łatwo odzyskać oprogramowanie po atakach oprogramowania wymuszającego okup.

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)
