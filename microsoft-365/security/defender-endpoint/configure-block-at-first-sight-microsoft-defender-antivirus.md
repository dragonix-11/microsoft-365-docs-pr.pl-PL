---
title: Włączanie bloku od pierwszego wejrzenia w celu wykrywania złośliwego oprogramowania w ciągu kilku sekund
description: Włącz funkcję bloku od pierwszego wejrzenia, aby wykryć i zablokować złośliwe oprogramowanie w ciągu kilku sekund.
keywords: skanowanie, blokowanie od pierwszego wejrzenia, złośliwe oprogramowanie, pierwszy rzut oka, chmura, obrońca, oprogramowanie antywirusowe
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.reviewer: marcmcc
manager: dansimp
ms.custom: nextgen
ms.date: 10/18/2021
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: fb65e1ad898427c3f0a2fc1ba9a13685c1617bc1
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416283"
---
# <a name="turn-on-block-at-first-sight"></a>Włącz blokowanie od pierwszego wejrzenia

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender 

**Platformy**
- System Windows

W tym artykule opisano funkcję ochrony antywirusowej/ochrony przed złośliwym kodem znaną jako "blokuj od pierwszego wejrzenia" i opisano sposób włączania bloku od pierwszego wejrzenia dla organizacji.

> [!TIP]
> Ten artykuł jest przeznaczony dla administratorów przedsiębiorstwa i specjalistów IT, którzy zarządzają ustawieniami zabezpieczeń dla organizacji. Jeśli nie jesteś administratorem enteprise lub Pro IT, ale masz pytania dotyczące bloku od pierwszego wejrzenia, zobacz [sekcję Nie administrator przedsiębiorstwa lub Pro IT?](#not-an-enterprise-admin-or-it-pro)

## <a name="what-is-block-at-first-sight"></a>Co to jest "blok od pierwszego wejrzenia"?

Blokuj od pierwszego wejrzenia to funkcja ochrony przed zagrożeniami w ramach ochrony nowej generacji, która wykrywa nowe złośliwe oprogramowanie i blokuje go w ciągu kilku sekund. Pozycja Blokuj od pierwszego wejrzenia jest włączona po włączeniu określonych ustawień zabezpieczeń. Te ustawienia obejmują:

- Ochrona dostarczana przez chmurę;
- Określony limit czasu przesyłania przykładowego (na przykład 50 sekund); I
- Wysoki poziom blokowania plików.

W większości organizacji korporacyjnych ustawienia wymagane do włączenia bloku od pierwszego wejrzenia są konfigurowane przy użyciu wdrożeń Program antywirusowy Microsoft Defender.

## <a name="how-it-works"></a>Jak to działa

Gdy Program antywirusowy Microsoft Defender napotka podejrzany, ale niewykryty plik, wysyła zapytanie do naszego zaplecza ochrony w chmurze. Zaplecze chmury stosuje heurystykę, uczenie maszynowe i zautomatyzowaną analizę pliku, aby określić, czy pliki są złośliwe, czy nie.

Program antywirusowy Microsoft Defender używa wielu technologii wykrywania i zapobiegania, aby zapewnić dokładną, inteligentną i w czasie rzeczywistym ochronę.

:::image type="content" source="images/microsoft-defender-atp-next-generation-protection-engines.png" alt-text="Lista aparatów av usługi Microsoft Defender" lightbox="images/microsoft-defender-atp-next-generation-protection-engines.png":::

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [(Blog) Zapoznanie się z zaawansowanymi technologiami, które są podstawą Ochrona punktu końcowego w usłudze Microsoft Defender ochrony nowej generacji](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/).

## <a name="a-few-things-to-know-about-block-at-first-sight"></a>Kilka rzeczy, które należy wiedzieć o bloku od pierwszego wejrzenia

- W Windows 10, wersji 1803 lub nowszej, blok od pierwszego wejrzenia może blokować nie przenośne pliki wykonywalne (takie jak JS, VBS lub makra) i pliki wykonywalne.

- Pozycja Blokuj od pierwszego wejrzenia używa zaplecza ochrony chmury tylko dla plików wykonywalnych i nie przenośnych plików wykonywalnych pobieranych z Internetu lub pochodzących ze strefy internetowej. Wartość skrótu pliku .exe jest sprawdzana za pośrednictwem zaplecza chmury w celu ustalenia, czy plik jest wcześniej niewykrytym plikiem.

- Jeśli zaplecze chmury nie może dokonać ustalenia, Program antywirusowy Microsoft Defender blokuje plik i przekazuje kopię do chmury. Chmura wykonuje więcej analiz w celu ustalenia, zanim umożliwi uruchomienie pliku lub zablokowanie go we wszystkich przyszłych spotkaniach, w zależności od tego, czy określa on plik jako złośliwy, czy nie.

- W wielu przypadkach ten proces może skrócić czas odpowiedzi na nowe złośliwe oprogramowanie z godzin do sekund.

- Możesz [określić, jak długo plik powinien nie być uruchomiony](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) , podczas gdy usługa ochrony oparta na chmurze analizuje plik. Możesz również [dostosować komunikat wyświetlany na pulpitach użytkowników](/windows/security/threat-protection/windows-defender-security-center/wdsc-customize-contact-information) , gdy plik jest zablokowany. Możesz zmienić nazwę firmy, informacje kontaktowe i adres URL wiadomości.

## <a name="turn-on-block-at-first-sight-with-microsoft-intune"></a>Włącz blok od pierwszego wejrzenia za pomocą Microsoft Intune

> [!TIP]
> Microsoft Intune jest teraz częścią Microsoft Endpoint Manager.

1. W centrum administracyjnym Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) przejdź do **pozycji Profile konfiguracji** **urządzeń**\>.

2. Wybierz lub utwórz profil przy użyciu typu profilu **Ograniczenia urządzenia** .

3. W **ustawieniach konfiguracji** profilu Ograniczenia urządzenia ustaw lub potwierdź następujące ustawienia w **obszarze Program antywirusowy Microsoft Defender**:

   - **Ochrona dostarczana przez chmurę**: włączona
   - **Poziom blokowania plików**: wysoki
   - **Rozszerzenie czasu skanowania plików przez chmurę**: 50
   - **Monituj użytkowników przed przesłaniem przykładu**: Wyślij wszystkie dane bez monitowania

   :::image type="content" source="../../media/intune-block-at-first-sight.png" alt-text="Intune blok konfiguracji od pierwszego wejrzenia" lightbox="../../media/intune-block-at-first-sight.png":::

4. Zapisz ustawienia.

> [!TIP]
>
> - Ustawienie wysokiego poziomu blokowania plików **powoduje zastosowanie** silnego poziomu wykrywania. W mało prawdopodobnym przypadku, gdy blokowanie plików powoduje fałszywie dodatnie wykrywanie legalnych plików, zespół ds. operacji zabezpieczeń może [przywrócić pliki poddane kwarantannie](./restore-quarantined-files-microsoft-defender-antivirus.md).
> - Aby uzyskać więcej informacji na temat konfigurowania ograniczeń urządzeń Program antywirusowy Microsoft Defender w Intune, zobacz [Konfigurowanie ustawień ograniczeń urządzenia w Microsoft Intune](/intune/device-restrictions-configure).
> - Aby uzyskać listę ograniczeń urządzeń Program antywirusowy Microsoft Defender w Intune, zobacz [Ograniczenia dotyczące urządzeń dla ustawień Windows 10 (i nowszych) w Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="turn-on-block-at-first-sight-with-microsoft-endpoint-manager"></a>Włącz blok od pierwszego wejrzenia za pomocą Microsoft Endpoint Manager

> [!TIP]
> Jeśli szukasz Microsoft Endpoint Configuration Manager, jest to teraz część Microsoft Endpoint Manager.

1. W Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) przejdź do pozycji **Program antywirusowy** **zabezpieczeń** \> punktu końcowego.

2. Wybierz istniejące zasady lub utwórz nowe zasady przy użyciu typu **profilu Program antywirusowy Microsoft Defender**.

3. Ustaw lub potwierdź następujące ustawienia konfiguracji:

   - **Włącz ochronę dostarczaną przez chmurę**: Tak
   - **Poziom ochrony dostarczanej w chmurze**: wysoki
   - **Program antywirusowy Microsoft Defender rozszerzony limit czasu w sekundach**: 50

   :::image type="content" source="images/endpointmgr-antivirus-cloudprotection.png" alt-text="Blokuj ustawienia od pierwszego wejrzenia w portalu Microsoft Endpoint Manager" lightbox="images/endpointmgr-antivirus-cloudprotection.png":::

4. Zastosuj profil Program antywirusowy Microsoft Defender do grupy, takiej jak **Wszyscy użytkownicy**, **Wszystkie urządzenia** lub **Wszyscy użytkownicy i urządzenia**.

## <a name="turn-on-block-at-first-sight-with-group-policy"></a>Włącz blok od pierwszego wejrzenia za pomocą zasady grupy

> [!NOTE]
> Zalecamy używanie Intune lub Microsoft Endpoint Manager do włączania bloku od pierwszego wejrzenia.

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

2. Za pomocą **edytora zarządzania zasady grupy** przejdź do pozycji **Konfiguracja** \> komputera **Szablony** \> administracyjne **Windows Składniki** \> **Program antywirusowy Microsoft Defender** \> **MAPS**.

3. W sekcji MAPS kliknij dwukrotnie pozycję **Skonfiguruj funkcję "Blokuj od pierwszego wejrzenia",** ustaw ją na **wartość Włączone**, a następnie wybierz przycisk **OK**.

    > [!IMPORTANT]
    > Ustawienie opcji **Zawsze monituj (0)** spowoduje obniżenie stanu ochrony urządzenia. Ustawienie wartości **Nigdy nie wysyłaj (2)** oznacza, że blok od pierwszego wejrzenia nie będzie działać.

4. W sekcji MAPS kliknij dwukrotnie pozycję **Wyślij przykłady plików, gdy wymagana jest dalsza analiza**, i ustaw ją na **wartość Włączone**. W obszarze **Wyślij przykłady plików, gdy wymagana jest dalsza analiza**, wybierz pozycję **Wyślij wszystkie przykłady**, a następnie wybierz przycisk **OK**.

5. Ponownie wdróż obiekt zasady grupy w sieci, tak jak zwykle.

## <a name="confirm-block-at-first-sight-is-enabled-on-individual-client-devices"></a>Potwierdzanie włączenia bloku od pierwszego wejrzenia na poszczególnych urządzeniach klienckich

Możesz potwierdzić, że blok od pierwszego wejrzenia jest włączony na poszczególnych urządzeniach klienckich przy użyciu aplikacji Zabezpieczenia Windows. Opcja Blokuj od pierwszego wejrzenia jest włączana automatycznie, o ile **włączono ochronę dostarczaną przez chmurę** i **automatyczne przesyłanie przykładów** .

1. Otwórz aplikację Zabezpieczenia Windows.

2. Wybierz pozycję **Ochrona przed zagrożeniami & wirusami**, a następnie w obszarze **Ustawienia ochrony przed zagrożeniami & wirusów** wybierz pozycję **Zarządzaj Ustawienia**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Etykieta ustawień ochrony przed zagrożeniami & wirusów w aplikacji Zabezpieczenia Windows" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. Upewnij się, że **ochrona dostarczana w chmurze** i **automatyczne przesyłanie przykładów** są włączone.

> [!NOTE]
>
> - Jeśli ustawienia wymagań wstępnych zostaną skonfigurowane i wdrożone przy użyciu zasady grupy, ustawienia opisane w tej sekcji będą wyszarzone i niedostępne do użycia w poszczególnych punktach końcowych.
> - Zmiany wprowadzone za pośrednictwem obiektu zasady grupy należy najpierw wdrożyć w poszczególnych punktach końcowych, zanim ustawienie zostanie zaktualizowane w Windows Ustawienia.

## <a name="validate-block-at-first-sight-is-working"></a>Sprawdzanie poprawności działania bloku od pierwszego wejrzenia

Aby sprawdzić, czy funkcja działa, pobierz [przykładowy plik Blokuj od pierwszego wejrzenia](https://demo.wd.microsoft.com/Page/BAFS). Aby pobrać plik, musisz mieć konto w Azure AD z przypisaną rolą administratora zabezpieczeń lub administratora globalnego.

Aby sprawdzić, czy ochrona z obsługą chmury działa, postępuj zgodnie ze [wskazówkami w temacie Weryfikowanie połączeń między siecią a chmurą](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud).

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="turn-off-block-at-first-sight"></a>Wyłącz blok od pierwszego wejrzenia

> [!CAUTION]
> Wyłączenie bloku od pierwszego wejrzenia spowoduje obniżenie stanu ochrony urządzeń i sieci.

Możesz wyłączyć blok od pierwszego wejrzenia, jeśli chcesz zachować ustawienia wymagań wstępnych bez używania ochrony przed blokowaniem od pierwszego wejrzenia. Możesz tymczasowo wyłączyć blokadę od pierwszego wejrzenia, aby zobaczyć, jak ta funkcja wpływa na sieć. Nie zalecamy jednak trwałego wyłączania ochrony bloku od pierwszego wejrzenia.

### <a name="turn-off-block-at-first-sight-with-microsoft-endpoint-manager"></a>Wyłącz blok od pierwszego wejrzenia za pomocą Microsoft Endpoint Manager

1. Przejdź do Microsoft Endpoint Manager centrum administracyjnego (<https://endpoint.microsoft.com>) i zaloguj się.

2. Przejdź do pozycji **Program antywirusowy** zabezpieczeń \> **punktu końcowego**, a następnie wybierz zasady Program antywirusowy Microsoft Defender.

3. W obszarze **Zarządzanie** wybierz pozycję **Właściwości**.

4. Obok pozycji **Ustawienia konfiguracji** wybierz pozycję **Edytuj**.

5. Zmień co najmniej jedno z następujących ustawień:

   - Ustaw **opcję Włącz ochronę dostarczaną w chmurze na** **wartość Nie** lub **Nie skonfigurowano**.
   - Ustaw **poziom ochrony dostarczanej w chmurze** na **nieskonfigurowane**.
   - Wyczyść pole wyboru **Program antywirusowy Microsoft Defender limit czasu rozszerzonego w sekundach**.

6. Przejrzyj i zapisz ustawienia.

### <a name="turn-off-block-at-first-sight-with-group-policy"></a>Wyłącz blok od pierwszego wejrzenia za pomocą zasady grupy

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. Za pomocą **edytora zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo za pomocą **składników** \> Windows **Program antywirusowy Microsoft Defender** \> **MAPS**.

4. Kliknij **dwukrotnie pozycję Skonfiguruj funkcję "Blokuj od pierwszego wejrzenia"** i ustaw opcję **Wyłączone**.

    > [!NOTE]
    > Wyłączenie bloku od pierwszego wejrzenia nie powoduje wyłączenia ani zmiany zasad grupy wymagań wstępnych.

## <a name="not-an-enterprise-admin-or-it-pro"></a>Nie jesteś administratorem przedsiębiorstwa ani Pro IT?

Jeśli nie jesteś administratorem przedsiębiorstwa ani Pro IT, ale masz pytania dotyczące bloku od pierwszego wejrzenia, ta sekcja jest dla Ciebie. Blokuj od pierwszego wejrzenia to funkcja ochrony przed zagrożeniami, która wykrywa i blokuje złośliwe oprogramowanie w ciągu kilku sekund. Chociaż nie ma określonego ustawienia o nazwie "Blokuj od pierwszego wejrzenia", funkcja jest włączona, gdy niektóre ustawienia są skonfigurowane na urządzeniu.

### <a name="how-to-manage-block-at-first-sight-on-or-off-on-your-own-device"></a>Jak zarządzać blokiem od pierwszego wejrzenia na lub wył. na własnym urządzeniu

Jeśli masz urządzenie osobiste, które nie jest zarządzane przez organizację, możesz się zastanawiać, jak włączyć lub wyłączyć blokadę od pierwszego wejrzenia. Możesz użyć aplikacji Zabezpieczenia Windows do zarządzania blokiem od pierwszego wejrzenia.

1. Na komputerze Windows 10 lub Windows 11 otwórz aplikację Zabezpieczenia Windows.

2. Wybierz pozycję **Ochrona przed wirusami i zagrożeniami**.

3. W obszarze **Ustawienia ochrony przed wirusami i zagrożeniami** wybierz opcję **Zarządzaj ustawieniami**.

4. Wykonaj jedną z następujących czynności:

   - Aby włączyć blok od pierwszego wejrzenia, upewnij się, że zarówno **ochrona dostarczana w chmurze** , jak i **automatyczne przesyłanie przykładów** są włączone.

   - Aby wyłączyć blok od pierwszego wejrzenia, wyłącz **ochronę dostarczaną w chmurze** lub **automatyczne przesyłanie przykładów**.

     > [!CAUTION]
     > Wyłączenie bloku od pierwszego wejrzenia obniża poziom ochrony urządzenia. Nie zalecamy trwałego wyłączania bloku od pierwszego wejrzenia.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Włączanie ochrony dostarczanej w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Ochrona przy użyciu Zabezpieczenia Windows](https://support.microsoft.com/windows/stay-protected-with-windows-security-2ae0363d-0ada-c064-8b56-6a39afb6a963)
