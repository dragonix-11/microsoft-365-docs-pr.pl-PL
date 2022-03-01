---
title: Włączanie blokowania na pierwszy rzut oka w celu wykrycia złośliwego oprogramowania w kilka sekund
description: Włącz funkcję blokowania na pierwszy rzut oka, aby wykrywać i blokować złośliwe oprogramowanie w ciągu kilku sekund.
keywords: skanowanie, blokowanie na pierwszy rzut oka, złośliwe oprogramowanie, pierwszy rzut oka, chmura, defender, oprogramowanie antywirusowe
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
ms.openlocfilehash: c955ab15640a8c3154e14ba0201946e109f832a9
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014699"
---
# <a name="turn-on-block-at-first-sight"></a>Włączanie bloku na pierwszy rzut oka

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

W tym artykule opisano funkcję antywirusową/ochrony przed złośliwym oprogramowaniem, określaną na pierwszy rzut oka jako "blokuj na pierwszy rzut oka" i jak włączać blokowanie na pierwszy rzut oka dla organizacji.

> [!TIP]
> Ten artykuł jest przeznaczony dla administratorów przedsiębiorstwa i informatyków, którzy zarządzają ustawieniami zabezpieczeń w organizacji. Jeśli nie jesteś zacenany administratorem ani administratorem IT Pro ale na pierwszy rzut oka masz pytania dotyczące blokowania, zobacz sekcję Nie jesteś administratorem przedsiębiorstwa ani administratorem [Pro?](#not-an-enterprise-admin-or-it-pro)

## <a name="what-is-block-at-first-sight"></a>Co to jest "blok na pierwszy rzut oka"?

Blokowanie na pierwszy rzut oka to funkcja ochrony przed zagrożeniami, która wykrywa nowe złośliwe oprogramowanie i blokuje je w ciągu kilku sekund. Blokowanie na pierwszy rzut oka jest włączone, gdy są włączone pewne ustawienia zabezpieczeń. Są to między innymi następujące ustawienia:

- Ochrona w chmurze;
- Określony limit czasu przesłania przykładowego (na przykład 50 sekund); i
- Wysoki poziom blokowania plików.

W większości przedsiębiorstw ustawienia potrzebne do włączenia blokowania na pierwszy rzut oka są skonfigurowane Program antywirusowy Microsoft Defender wdrażania.

## <a name="how-it-works"></a>Jak to działa

Jeśli Program antywirusowy Microsoft Defender napotka podejrzany, ale niezauważony plik, wysyła zapytanie do naszej bazy danych ochrony w chmurze. W zapleczam chmury stosowane są heuristics, uczenie maszynowe i automatyczna analiza pliku w celu ustalenia, czy pliki są złośliwe, czy nie stanowią zagrożenia.

Program antywirusowy Microsoft Defender technologii wykrywania i zapobiegania wielu problemom w celu zapewnienia dokładnej, inteligentnej i ochrony w czasie rzeczywistym.

![Lista aparatów audio/wideo programu Microsoft Defender.](images/microsoft-defender-atp-next-generation-protection-engines.png)  

> [!TIP]
> Aby dowiedzieć się więcej, zobacz (Blog) Poznaj zaawansowane technologie i zapoznaj się z podstawowymi tematami programu [Microsoft Defender for Endpoint ochrony następnej generacji](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/).

## <a name="a-few-things-to-know-about-block-at-first-sight"></a>Kilka rzeczy, o których należy wiedzieć, na pierwszy rzut oka na blok

- W Windows 10 1803 lub nowszym blokuj na pierwszy rzut oka mogą blokować nie przenośne pliki wykonywalne (takie jak JS, VBS lub makra) i pliki wykonywalne.

- Blokowanie na pierwszy rzut oka używa zaplecza ochrony chmury tylko dla plików wykonywalnych i niewynoszlnych plików wykonywalnych, które są pobierane z Internetu lub pochodzą ze strefy internetowej. Wartość skrótu pliku .exe jest sprawdzana za pośrednictwem zaplecza chmury w celu określenia, czy plik jest wcześniej niezauważony.

- Jeśli kopia zapasowa chmury nie może dokonać wyznaczania, Program antywirusowy Microsoft Defender blokuje plik i przesyła kopię do chmury. Chmura przeprowadza większą analizę w celu określenia, czy pozwala na uruchamianie pliku, czy blokowanie go we wszystkich przyszłych wystąpieniach, w zależności od tego, czy plik jest złośliwy, czy nie.

- W wielu przypadkach ten proces może skrócić czas reakcji nowego złośliwego oprogramowania z kilku godzin na sekundy.

- Możesz określić [, jak](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) długo plik nie będzie mógł działać, gdy usługa ochrony w chmurze będzie analizować plik. Możesz też dostosować [komunikat wyświetlany na komputerach](/windows/security/threat-protection/windows-defender-security-center/wdsc-customize-contact-information) użytkowników, gdy plik zostanie zablokowany. Możesz zmienić nazwę firmy, informacje kontaktowe i adres URL wiadomości.

## <a name="turn-on-block-at-first-sight-with-microsoft-intune"></a>Włączanie bloku na pierwszy rzut oka za pomocą Microsoft Intune

> [!TIP]
> Microsoft Intune jest teraz częścią Microsoft Endpoint Manager.

1. W centrum Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) przejdź do **pozycji Profile konfiguracji** \> **urządzeń**.

2. Wybierz lub utwórz profil, używając **typu profilu Ograniczenia** urządzeń.

3. W **ustawieniach konfiguracji** profilu Ograniczenia urządzeń ustaw lub potwierdź następujące ustawienia w **obszarze Program antywirusowy Microsoft Defender**:

   - **Ochrona w chmurze**: włączona
   - **Poziom blokowania plików**: Wysoki
   - **Rozszerzenie czasu na skanowanie plików w chmurze**: 50
   - **Monituj użytkowników przed przykładowym przesłaniem**: Wyślij wszystkie dane bez monitowania

   :::image type="content" source="../../media/intune-block-at-first-sight.png" alt-text="Blok konfiguracji usługi Intune na pierwszy rzut oka.":::

4. Zapisz ustawienia.

> [!TIP]
>
> - Ustawienie poziomu blokowania pliku na **Wysoki** powoduje zastosowanie silnego poziomu wykrywania. W przypadku mało prawdopodobnego zdarzenia, w przypadku blokowania plików powodujących wykrywanie fałszywych wyników dodatnich legalnych plików, zespół operacji zabezpieczeń może przywrócić pliki poddane [kwarantannie](./restore-quarantined-files-microsoft-defender-antivirus.md).
> - Aby uzyskać więcej informacji na temat konfigurowania Program antywirusowy Microsoft Defender urządzeń w usłudze Intune, zobacz Konfigurowanie ustawień ograniczeń [urządzeń w usłudze Microsoft Intune](/intune/device-restrictions-configure).
> - Aby uzyskać listę ograniczeń Program antywirusowy Microsoft Defender urządzeń w usłudze Intune, zobacz Ograniczenia dotyczące urządzeń [Windows 10 (i nowsze) w usłudze Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="turn-on-block-at-first-sight-with-microsoft-endpoint-manager"></a>Włączanie bloku na pierwszy rzut oka za pomocą Microsoft Endpoint Manager

> [!TIP]
> Jeśli szukasz nowych Microsoft Endpoint Configuration Manager, jest teraz częścią Microsoft Endpoint Manager.

1. W Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) przejdź do ustawienia **Zabezpieczenia punktu końcowego oprogramowania antywirusowego**\>.

2. Wybierz istniejące zasady lub utwórz nowe zasady przy **użyciu Program antywirusowy Microsoft Defender** profilu.

3. Ustaw lub potwierdź następujące ustawienia konfiguracji:

   - **Włączanie ochrony w chmurze**: Tak
   - **Poziom ochrony w chmurze**: Wysoki
   - **Program antywirusowy Microsoft Defender limit czasu w sekundach**: 50

   :::image type="content" source="images/endpointmgr-antivirus-cloudprotection.png" alt-text="Blokuj ustawienia na pierwszy rzut oka w Endpoint Manager.":::

4. Zastosuj profil Program antywirusowy Microsoft Defender do grupy, takiej jak Wszyscy **użytkownicy, Wszystkie** urządzenia lub **Wszyscy użytkownicy i urządzenia**. 

## <a name="turn-on-block-at-first-sight-with-group-policy"></a>Włączanie bloku na pierwszy rzut oka za pomocą zasady grupy

> [!NOTE]
> Zalecamy korzystanie z usługi Intune lub Microsoft Endpoint Manager aby od pierwszego rzutu oka włączyć blokowanie.

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. Za pomocą **edytora zasady grupy zarządzania przejdź** do **tematu Konfiguracja** \> **komputera** \> Szablony administracyjne dla **Windows Składniki** \> **Program antywirusowy Microsoft Defender** \> **MAPY**.

3. W sekcji MAPY kliknij dwukrotnie pozycję Konfiguruj funkcję **"** Blokuj na pierwszy rzut oka", ustaw dla tej funkcji wartość **Włączone, a** następnie wybierz przycisk **OK**.

    > [!IMPORTANT]
    > Ustawienie zawsze **wyświetlaj monit (0)** spowoduje obniżenie stanu ochrony urządzenia. Ustawienie Nigdy **nie wysyłaj (2)** oznacza, że blok na pierwszy rzut oka nie będzie działał.

4. W sekcji MAPY kliknij dwukrotnie pozycję **Wyślij próbki plików, gdy jest** wymagana dalsza analiza, i ustaw dla niego wartość **Włączone**. W **obszarze Wyślij próbki plików podczas dalszej analizy** wybierz pozycję **Wyślij wszystkie próbki**, a następnie wybierz przycisk **OK**.

5. W ten sposób możesz ponownie zasady grupy obiekt obiektowy w sieci.

## <a name="confirm-block-at-first-sight-is-enabled-on-individual-client-devices"></a>Potwierdzanie, że blokowanie na pierwszy rzut oka jest włączone na poszczególnych urządzeniach klienckich

Możesz potwierdzić, że blokowanie na pierwszy rzut oka jest włączone na poszczególnych urządzeniach klienckich przy użyciu Zabezpieczenia Windows aplikacji. Blokowanie na pierwszy rzut oka jest automatycznie włączone, o  ile jest włączona ochrona  w chmurze i Automatyczne przesyłanie próbek.

1. Otwórz Zabezpieczenia Windows aplikacji.

2. Wybierz **pozycję ochrona & przed** zagrożeniami, a następnie w obszarze **Ustawienia ochrony przed &** wirusami wybierz pozycję **Zarządzaj** Ustawienia.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Zrzut ekranu przedstawiający etykietę ustawień ochrony przed & wirusami w Zabezpieczenia Windows aplikacji":::

3. Upewnij się **, że są włączone zabezpieczenia w** **chmurze i** Automatyczne przesyłanie próbek.

> [!NOTE]
>
> - Jeśli wstępnie wymagane ustawienia zostały skonfigurowane i wdrożone przy użyciu programu zasady grupy, ustawienia opisane w tej sekcji będą wyszzarowane i niedostępne do użycia w poszczególnych punktach końcowych.
> - Zmiany wprowadzone za pośrednictwem zasady grupy obiekt musi najpierw zostać wdrożony w poszczególnych punktach końcowych, aby ustawienie było aktualizowane w Windows Ustawienia.

## <a name="validate-block-at-first-sight-is-working"></a>Sprawdzanie działania bloku na pierwszy rzut oka

Aby sprawdzić, czy funkcja działa, pobierz przykładowy plik Blokuj [na pierwszy rzut oka](https://demo.wd.microsoft.com/Page/BAFS). Do pobrania pliku potrzebne jest konto w usłudze Azure AD z przypisaną rolą Administratora zabezpieczeń lub Administratora globalnego.

Aby sprawdzić, czy ochrona w chmurze działa, postępuj zgodnie z wskazówkami w tece Weryfikowanie połączeń między siecią [a chmurą](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud).

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="turn-off-block-at-first-sight"></a>Wyłączanie bloku na pierwszy rzut oka

> [!CAUTION]
> Wyłączenie bloku na pierwszy rzut oka spowoduje obniżenie stanu ochrony twoich urządzeń i sieci.

Blokadę można wyłączyć na pierwszy rzut oka, jeśli ustawienia wymagań wstępnych mają być zachowywane bez używania ochrony bloku na pierwszy rzut oka. Możesz tymczasowo wyłączyć blokowanie na pierwszy rzut oka, aby zobaczyć, jak ta funkcja wpłynie na Twoją sieć. Nie zalecamy jednak trwałego wyłączania ochrony przed zablokowaniem na pierwszy rzut oka.

### <a name="turn-off-block-at-first-sight-with-microsoft-endpoint-manager"></a>Wyłączanie bloku na pierwszy rzut oka za pomocą Microsoft Endpoint Manager

1. Przejdź do Microsoft Endpoint Manager administracyjnego (<https://endpoint.microsoft.com>) i zaloguj się.

2. Przejdź do punktu **końcowego oprogramowania** \> **antywirusowego**, a następnie wybierz odpowiednie Program antywirusowy Microsoft Defender zabezpieczeń.

3. W **obszarze Zarządzanie** wybierz pozycję **Właściwości**.

4. Obok opcji **Ustawienia konfiguracji** wybierz pozycję **Edytuj**.

5. Zmień co najmniej jedno z następujących ustawień:

   - Ustaw **dla ustawienia Włącz ochronę w chmurze** wartość **Nie** **lub Nie skonfigurowano**.
   - Ustaw **poziom ochrony w chmurze** na **Wartość Nieskonfigurowane**.
   - Wyczyść pole wyboru obok **Program antywirusowy Microsoft Defender limit czasu (w sekundach**).

6. Przejrzyj i zapisz ustawienia.

### <a name="turn-off-block-at-first-sight-with-group-policy"></a>Wyłączanie bloku na pierwszy rzut oka za pomocą zasady grupy

1. Na komputerze zasady grupy zarządzania otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. Za pomocą zasady grupy **zarządzania przejdź** do **strony Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo przez Windows **składniki Program antywirusowy Microsoft Defender** \>  \> **MAPY**.

4. Kliknij dwukrotnie **pozycję Konfiguruj funkcję "Blokuj od pierwszego oka"** i ustaw dla opcji wartość **Wyłączone**.

    > [!NOTE]
    > Wyłączenie blokowania na pierwszy rzut oka nie powoduje wyłączenia ani zmiany wymagań wstępnych zasad grupy.

## <a name="not-an-enterprise-admin-or-it-pro"></a>Nie jest administratorem przedsiębiorstwa ani administratorem Pro?

Jeśli nie jesteś administratorem przedsiębiorstwa ani administratorem it Pro ale na pierwszy rzut oka masz pytania dotyczące blokowania, ta sekcja jest dla Ciebie. Blokowanie na pierwszy rzut oka to funkcja ochrony przed zagrożeniami, która wykrywa i blokuje złośliwe oprogramowanie w ciągu kilku sekund. Chociaż nie ma określonego ustawienia o nazwie "Blokuj na pierwszy rzut oka", ta funkcja jest włączana, gdy na Twoim urządzeniu skonfigurowano pewne ustawienia.

### <a name="how-to-manage-block-at-first-sight-on-or-off-on-your-own-device"></a>Jak zarządzać blokowaniem na pierwszym rzut oka na własnym urządzeniu

Jeśli masz urządzenie osobiste, którym nie zarządza organizacja, być może zastanawiasz się, jak od początku włączyć lub wyłączyć blokowanie. Za pomocą aplikacji Zabezpieczenia Windows możesz zarządzać blokami od pierwszego rzutu oka.

1. Na komputerze Windows 10 lub Windows 11 otwórz Zabezpieczenia Windows komputera.

2. Wybierz **pozycję Ochrona & przed zagrożeniami**.

3. W **obszarze & ochrony przed zagrożeniami** wybierz pozycję **Zarządzaj ustawieniami**.

4. Należy wykonać jedną z następujących czynności:

   - Aby od początku włączyć blokowanie, upewnij się, że  są włączone zarówno ochrona w  chmurze, jak i Automatyczne przesyłanie próbek.

   - Aby wyłączyć blokowanie na pierwszy rzut oka, wyłącz opcję **Ochrona w** chmurze lub **Automatyczne przesyłanie próbek**.

     > [!CAUTION]
     > Wyłączenie bloku na pierwszy rzut oka obniża poziom ochrony urządzenia. Nie zalecamy trwałego wyłączania blokowania na pierwszy rzut oka.


## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Zachowaj ochronę za pomocą Zabezpieczenia Windows](https://support.microsoft.com/windows/stay-protected-with-windows-security-2ae0363d-0ada-c064-8b56-6a39afb6a963)
