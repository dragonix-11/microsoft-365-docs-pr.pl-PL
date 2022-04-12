---
title: Rozwiązywanie problemów z wynikami fałszywie pozytywnymi/negatywnymi w ochronie punktu końcowego w usłudze Microsoft Defender
description: Dowiedz się, jak obsługiwać wyniki fałszywie dodatnie lub fałszywie ujemne w Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: antivirus, exception, exclusion, Ochrona punktu końcowego w usłudze Microsoft Defender, false positive, false negative, blocked file, blocked url
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
- m365solution-scenario
- m365scenario-fpfn
ms.topic: how-to
ms.date: 12/02/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs, yonghree, jcedola
ms.custom:
- FPFN
- admindeeplinkDEFENDER
ms.openlocfilehash: d7477c2006acd04008e6cb56cb22261a4db4a92b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789930"
---
# <a name="address-false-positivesnegatives-in-microsoft-defender-for-endpoint"></a>Rozwiązywanie problemów z wynikami fałszywie pozytywnymi/negatywnymi w ochronie punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

W rozwiązaniach ochrony punktu końcowego wynikiem fałszywie dodatnim jest jednostka, taka jak plik lub proces, która została wykryta i zidentyfikowana jako złośliwa, mimo że jednostka w rzeczywistości nie stanowi zagrożenia. Fałszywie ujemny jest jednostką, która nie została wykryta jako zagrożenie, mimo że w rzeczywistości jest złośliwa. Wyniki fałszywie dodatnie/ujemne mogą wystąpić w przypadku dowolnego rozwiązania ochrony przed zagrożeniami, w tym [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md).

:::image type="content" source="images/false-positives-overview.png" alt-text="Definicja wartości fałszywie dodatnich i ujemnych w portalu Ochrona punktu końcowego w usłudze Microsoft Defender" lightbox="images/false-positives-overview.png":::

Na szczęście można podjąć kroki w celu rozwiązania i zmniejszenia tego rodzaju problemów. Jeśli widzisz wyniki fałszywie dodatnie/ujemne w [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender), twoje operacje zabezpieczeń mogą podjąć kroki w celu ich rozwiązania przy użyciu następującego procesu:

1. [Przeglądanie i klasyfikowanie alertów](#part-1-review-and-classify-alerts)
2. [Przejrzyj podjęte akcje korygowania](#part-2-review-remediation-actions)
3. [Przeglądanie i definiowanie wykluczeń](#part-3-review-or-define-exclusions)
4. [Przesyłanie jednostki do analizy](#part-4-submit-a-file-for-analysis)
5. [Przeglądanie i dostosowywanie ustawień ochrony przed zagrożeniami](#part-5-review-and-adjust-your-threat-protection-settings)

Możesz uzyskać pomoc, jeśli nadal masz problemy z wynikami fałszywie dodatnimi/ujemnymi po wykonaniu zadań opisanych w tym artykule. Zobacz [Nadal potrzebujesz pomocy?](#still-need-help)

:::image type="content" source="images/false-positives-step-diagram.png" alt-text="Kroki rozwiązywania problemów z fałszywymi alarmami i negatywami" lightbox="images/false-positives-step-diagram.png":::

> [!NOTE]
> Ten artykuł jest przeznaczony jako wskazówki dla operatorów zabezpieczeń i administratorów zabezpieczeń, którzy używają [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md).

## <a name="part-1-review-and-classify-alerts"></a>Część 1. Przeglądanie i klasyfikowanie alertów

Jeśli zostanie wyświetlony [alert](alerts.md) , który został wyzwolony, ponieważ coś zostało wykryte jako złośliwe lub podejrzane, które nie powinno być, możesz pominąć alert dla tej jednostki. Można również pominąć alerty, które niekoniecznie są fałszywie dodatnie, ale są nieistotne. Zalecamy również sklasyfikowanie alertów.

Zarządzanie alertami i klasyfikowanie wyników prawdziwie/fałszywie dodatnich pomaga wytrenować rozwiązanie do ochrony przed zagrożeniami i może zmniejszyć liczbę wyników fałszywie dodatnich lub fałszywie ujemnych w czasie. Wykonanie tych kroków pomaga również zmniejszyć szum na pulpicie nawigacyjnym operacji zabezpieczeń, dzięki czemu zespół ds. zabezpieczeń może skupić się na elementach roboczych o wyższym priorytecie.

### <a name="determine-whether-an-alert-is-accurate"></a>Określanie, czy alert jest dokładny

Przed sklasyfikowaniem lub pominięciem alertu określ, czy alert jest dokładny, fałszywie dodatni, czy niegroźny.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Kolejka alertów**.

3. Wybierz alert, aby uzyskać więcej szczegółów na temat alertu. (Zobacz [Przeglądanie alertów w Ochrona punktu końcowego w usłudze Microsoft Defender](review-alerts.md)).

4. W zależności od stanu alertu wykonaj kroki opisane w poniższej tabeli:

   |Stan alertu|Co robić|
   |---|---|
   |Alert jest dokładny|Przypisz alert, a następnie [zbadaj go](investigate-alerts.md) dalej.|
   |Alert jest fałszywie dodatni|1. [Sklasyfikowanie alertu](#classify-an-alert) jako fałszywie dodatniego.<br/><br/>2. [Pomiń alert](#suppress-an-alert).<br/><br/>3. [Utwórz wskaźnik](#indicators-for-microsoft-defender-for-endpoint) dla Ochrona punktu końcowego w usłudze Microsoft Defender.<br/><br/>4. [Prześlij plik do firmy Microsoft do analizy](#part-4-submit-a-file-for-analysis).|
   |Alert jest dokładny, ale niegroźny (nieistotny)|[Zaklasyfikuj alert](#classify-an-alert) jako prawdziwie dodatni, a następnie [pomiń alert](#suppress-an-alert).|

### <a name="classify-an-alert"></a>Klasyfikowanie alertu

Alerty można klasyfikować jako fałszywie dodatnie lub prawdziwie dodatnie w Microsoft 365 Defender. Klasyfikowanie alertów ułatwia trenowanie Ochrona punktu końcowego w usłudze Microsoft Defender, dzięki czemu z czasem zobaczysz więcej prawdziwych alertów i mniej fałszywych alertów.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Wybierz **pozycję Kolejka alertów**, a następnie wybierz alert.

3. Dla wybranego alertu wybierz pozycję **Akcje** \> **Zarządzaj alertem**. Zostanie otwarte okienko wysuwane.

4. W sekcji **Zarządzanie alertem** wybierz alert **True** lub **False**. (Użyj **alertu False** , aby sklasyfikować wynik fałszywie dodatni).

> [!TIP]
> Aby uzyskać więcej informacji na temat pomijania alertów, zobacz [Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/manage-alerts). Jeśli organizacja korzysta z serwera zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM), należy również zdefiniować tam regułę pomijania.

### <a name="suppress-an-alert"></a>Pomijanie alertu

Jeśli masz alerty, które są wynikiem fałszywie dodatnim lub są prawdziwie dodatnie, ale dla nieistotnych zdarzeń, możesz pominąć te alerty w Microsoft 365 Defender. Pomijanie alertów pomaga zmniejszyć szum na pulpicie nawigacyjnym operacji zabezpieczeń.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Kolejka alertów**.

3. Wybierz alert, który chcesz pominąć, aby otworzyć **okienko Szczegóły** .

4. W okienku **Szczegóły** wybierz wielokropek (**...**), a następnie **utwórz regułę pomijania**.

5. Określ wszystkie ustawienia reguły pomijania, a następnie wybierz pozycję **Zapisz**.

> [!TIP]
> Potrzebujesz pomocy dotyczącej reguł pomijania? Zobacz [Pomijanie alertu i tworzenie nowej reguły pomijania](/microsoft-365/security/defender-endpoint/manage-alerts#suppress-an-alert-and-create-a-new-suppression-rule).

## <a name="part-2-review-remediation-actions"></a>Część 2. Przegląd akcji korygowania

[Akcje korygowania](manage-auto-investigation.md#remediation-actions), takie jak wysłanie pliku do kwarantanny lub zatrzymanie procesu, są podejmowane w przypadku jednostek (takich jak pliki), które są wykrywane jako zagrożenia. Kilka typów akcji korygowania odbywa się automatycznie za pośrednictwem zautomatyzowanego badania i Program antywirusowy Microsoft Defender:

- Kwarantanna pliku
- Usuwanie klucza rejestru
- Zabij proces
- Zatrzymywanie usługi
- Wyłączanie sterownika
- Usuwanie zaplanowanego zadania

Inne akcje, takie jak uruchamianie skanowania antywirusowego lub zbieranie pakietu badania, są wykonywane ręcznie lub za pośrednictwem [odpowiedzi na żywo](live-response.md). Nie można cofnąć akcji wykonywanych za pośrednictwem odpowiedzi na żywo.

Po przejrzeniu alertów następnym krokiem jest [przejrzenie akcji korygowania](manage-auto-investigation.md). Jeśli jakiekolwiek akcje zostały podjęte w wyniku wyników fałszywie dodatnich, można cofnąć większość rodzajów akcji korygowania. W szczególności możesz:

- [Przywracanie pliku poddanej kwarantannie z Centrum akcji](#restore-a-quarantined-file-from-the-action-center)
- [Cofnij wiele akcji jednocześnie](#undo-multiple-actions-at-one-time)
- [Usuń plik z kwarantanny na wielu urządzeniach](#remove-a-file-from-quarantine-across-multiple-devices). i
- [Przywróć plik z kwarantanny](#restore-file-from-quarantine)

Po zakończeniu przeglądania i cofania akcji, które zostały wykonane w wyniku wyników fałszywie dodatnich, przejdź do [przeglądu lub zdefiniowania wykluczeń](#part-3-review-or-define-exclusions).

### <a name="review-completed-actions"></a>Przejrzyj ukończone akcje

1. W okienku nawigacji po lewej stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> kliknij pozycję **Centrum akcji**.

2. Wybierz kartę **Historia** , aby wyświetlić listę wykonanych akcji.

3. Wybierz element, aby wyświetlić więcej szczegółów dotyczących podjętej akcji korygowania.

### <a name="restore-a-quarantined-file-from-the-action-center"></a>Przywracanie pliku poddanej kwarantannie z Centrum akcji

1. W okienku nawigacji po lewej stronie portalu Microsoft 365 Defender kliknij pozycję **Centrum akcji**.

2. Na karcie **Historia** wybierz akcję, którą chcesz cofnąć.

3. W okienku wysuwanym wybierz pozycję **Cofnij**. Jeśli nie można cofnąć akcji za pomocą tej metody, nie zostanie wyświetlony przycisk **Cofnij** . (Aby dowiedzieć się więcej, zobacz [Cofnij ukończone akcje](manage-auto-investigation.md#undo-completed-actions)).

### <a name="undo-multiple-actions-at-one-time"></a>Cofnij wiele akcji jednocześnie

1. W okienku nawigacji po lewej stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> kliknij pozycję **Centrum akcji**.

2. Na karcie **Historia** wybierz akcje, które chcesz cofnąć.

3. W okienku po prawej stronie ekranu wybierz pozycję **Cofnij**.

### <a name="remove-a-file-from-quarantine-across-multiple-devices"></a>Usuwanie pliku z kwarantanny na wielu urządzeniach

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/autoir-quarantine-file-1.png" alt-text="Plik kwarantanny" lightbox="images/autoir-quarantine-file-1.png":::

1. W okienku nawigacji po lewej stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> kliknij pozycję **Centrum akcji**.

2. Na karcie **Historia** wybierz plik z **plikiem Kwarantanna typu Akcja**.

3. W okienku po prawej stronie ekranu wybierz pozycję **Zastosuj do X więcej wystąpień tego pliku**, a następnie wybierz pozycję **Cofnij**.

### <a name="restore-file-from-quarantine"></a>Przywróć plik z kwarantanny

Możesz wycofać i usunąć plik z kwarantanny, jeśli ustalono, że jest on czysty po badaniu. Uruchom następujące polecenie na każdym urządzeniu, na którym plik został poddany kwarantannie.

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu:

   1. Przejdź do **pozycji Start** i wpisz _cmd_.
   2. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij **klawisz Enter**:

    ```console
    "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
    ```

    > [!IMPORTANT]
    > W niektórych scenariuszach **nazwa zagrożenia** może być wyświetlana jako `EUS:Win32/CustomEnterpriseBlock!cl`. Usługa Defender for Endpoint przywróci wszystkie niestandardowe zablokowane pliki, które zostały poddane kwarantannie na tym urządzeniu w ciągu ostatnich 30 dni.
    >
    > Plik, który został poddany kwarantannie jako potencjalne zagrożenie sieciowe, może nie być możliwy do odzyskania. Jeśli użytkownik spróbuje przywrócić plik po kwarantannie, ten plik może być niedostępny. Może to być spowodowane tym, że system nie ma już poświadczeń sieciowych umożliwiających dostęp do pliku. Zazwyczaj jest to wynikiem tymczasowego logowania do systemu lub folderu udostępnionego, a tokeny dostępu wygasły.

3. W okienku po prawej stronie ekranu wybierz pozycję **Zastosuj do X więcej wystąpień tego pliku**, a następnie wybierz pozycję **Cofnij**.

## <a name="part-3-review-or-define-exclusions"></a>Część 3. Przeglądanie lub definiowanie wykluczeń

Wykluczenie to jednostka, taka jak plik lub adres URL, określona jako wyjątek dla akcji korygowania. Wykluczona jednostka nadal może stać się wykryta, ale nie są podejmowane żadne akcje korygujące dla tej jednostki. Oznacza to, że wykryty plik lub proces nie zostanie zatrzymany, wysłany do kwarantanny, usunięty lub w inny sposób zmieniony przez Ochrona punktu końcowego w usłudze Microsoft Defender.

Aby zdefiniować wykluczenia w Ochrona punktu końcowego w usłudze Microsoft Defender, wykonaj następujące zadania:

- [Definiowanie wykluczeń dla Program antywirusowy Microsoft Defender](#exclusions-for-microsoft-defender-antivirus)
- [Tworzenie wskaźników "zezwalaj" dla Ochrona punktu końcowego w usłudze Microsoft Defender](#indicators-for-microsoft-defender-for-endpoint)

> [!NOTE]
> Program antywirusowy Microsoft Defender wykluczenia dotyczą tylko ochrony antywirusowej, a nie innych Ochrona punktu końcowego w usłudze Microsoft Defender możliwości. Aby ogólnie wykluczyć pliki, użyj wykluczeń dla Program antywirusowy Microsoft Defender i [niestandardowych wskaźników](/microsoft-365/security/defender-endpoint/manage-indicators) dla Ochrona punktu końcowego w usłudze Microsoft Defender.

Procedury opisane w tej sekcji opisują sposób definiowania wykluczeń i wskaźników.

### <a name="exclusions-for-microsoft-defender-antivirus"></a>Wykluczenia dla Program antywirusowy Microsoft Defender

Ogólnie rzecz biorąc, nie należy definiować wykluczeń dla Program antywirusowy Microsoft Defender. Upewnij się, że wykluczenia są definiowane oszczędnie i że uwzględniane są tylko pliki, foldery, procesy i pliki otwierane przez proces, które są wynikiem fałszywie dodatnim. Ponadto należy regularnie przeglądać zdefiniowane wykluczenia. Zalecamy używanie [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) do definiowania lub edytowania wykluczeń programu antywirusowego, jednak można użyć innych metod, takich jak [zasady grupy](/azure/active-directory-domain-services/manage-group-policy) (zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender](manage-mde-post-migration.md).

> [!TIP]
> Potrzebujesz pomocy dotyczącej wykluczeń oprogramowania antywirusowego? Zobacz [Konfigurowanie i weryfikowanie wykluczeń dla skanowania Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md).

#### <a name="use-microsoft-endpoint-manager-to-manage-antivirus-exclusions-for-existing-policies"></a>Zarządzanie wykluczeniami antywirusowymi (dla istniejących zasad) przy użyciu Microsoft Endpoint Manager

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) i zaloguj się.

2. Wybierz pozycję **Program antywirusowy** zabezpieczeń \> **punktu końcowego**, a następnie wybierz istniejące zasady. (Jeśli nie masz istniejących zasad lub chcesz utworzyć nowe zasady, przejdź do [następnej procedury](#use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions)).

3. Wybierz pozycję **Właściwości**, a następnie obok pozycji **Ustawienia konfiguracji** wybierz pozycję **Edytuj**.

4. Rozwiń **węzeł Program antywirusowy Microsoft Defender Wykluczenia,** a następnie określ wykluczenia.

5. Wybierz **pozycję Przeglądanie i zapisywanie**, a następnie wybierz pozycję **Zapisz**.

#### <a name="use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions"></a>Tworzenie nowych zasad ochrony antywirusowej z wykluczeniami przy użyciu Microsoft Endpoint Manager

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) i zaloguj się.

2. Wybierz pozycję **Program antywirusowy** \> zabezpieczeń \> **punktu końcowego** **i utwórz zasady**.

3. Wybierz platformę (taką jak **Windows 10 i nowsze**, **macOS** lub **Windows 10 i serwer Windows**).

4. W obszarze **Profil** wybierz **pozycję Program antywirusowy Microsoft Defender wykluczeń**, a następnie wybierz pozycję **Utwórz**.

5. Określ nazwę i opis profilu, a następnie wybierz pozycję **Dalej**.

6. Na **karcie Ustawienia konfiguracji** określ wykluczenia programu antywirusowego, a następnie wybierz pozycję **Dalej**.

7. Jeśli używasz tagów zakresu w organizacji, na karcie **Tagi zakresu** określ tagi zakresu dla utworzonych zasad. (Zobacz [tagi zakresu](/mem/intune/fundamentals/scope-tags)).

8. Na **karcie Przypisania** określ użytkowników i grupy, do których mają być stosowane zasady, a następnie wybierz pozycję **Dalej**. (Jeśli potrzebujesz pomocy dotyczącej przypisań, zobacz [Przypisywanie profilów użytkowników i urządzeń w Microsoft Intune](/mem/intune/configuration/device-profile-assign)).

9. Na karcie **Przeglądanie i tworzenie** przejrzyj ustawienia, a następnie wybierz pozycję **Utwórz**.

### <a name="indicators-for-microsoft-defender-for-endpoint"></a>Wskaźniki dla Ochrona punktu końcowego w usłudze Microsoft Defender

[Wskaźniki](/microsoft-365/security/defender-endpoint/manage-indicators) (w szczególności wskaźniki naruszenia zabezpieczeń lub IoCs) umożliwiają zespołowi ds. operacji zabezpieczeń definiowanie wykrywania, zapobiegania i wykluczania jednostek. Można na przykład określić niektóre pliki, które mają zostać pominięte podczas skanowania i akcji korygowania w Ochrona punktu końcowego w usłudze Microsoft Defender. Wskaźniki mogą też służyć do generowania alertów dla niektórych plików, adresów IP lub adresów URL.

Aby określić jednostki jako wykluczenia dla Ochrona punktu końcowego w usłudze Microsoft Defender, utwórz wskaźniki "zezwalaj" dla tych jednostek. Takie wskaźniki "zezwalaj" w Ochrona punktu końcowego w usłudze Microsoft Defender mają zastosowanie do [ochrony nowej generacji](microsoft-defender-antivirus-in-windows-10.md), [wykrywanie i reagowanie w punktach końcowych](overview-endpoint-detection-response.md) i [zautomatyzowanego badania & korygowania](/microsoft-365/security/defender-endpoint/automated-investigations).

Wskaźniki "Zezwalaj" można utworzyć dla:

- [Pliki](#indicators-for-files)
- [Adresy IP, adresy URL i domeny](#indicators-for-ip-addresses-urls-or-domains)
- [Certyfikaty aplikacji](#indicators-for-application-certificates)

:::image type="content" source="images/false-positives-indicators.png" alt-text="Typy wskaźników" lightbox="images/false-positives-indicators.png":::

#### <a name="indicators-for-files"></a>Wskaźniki dla plików

[Utworzenie wskaźnika "zezwalaj" dla pliku, takiego jak plik wykonywalny](/microsoft-365/security/defender-endpoint/indicator-file), pomaga zapobiegać blokowi plików używanych przez organizację. Pliki mogą zawierać przenośne pliki wykonywalne (PE), takie jak `.exe` i `.dll` pliki.

Przed utworzeniem wskaźników dla plików upewnij się, że zostały spełnione następujące wymagania:

- Program antywirusowy Microsoft Defender jest skonfigurowana z włączoną ochroną opartą na chmurze (zobacz [Zarządzanie ochroną opartą na chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus))
- Wersja klienta ochrony przed złośliwym kodem to 4.18.1901.x lub nowsza wersja
- Urządzenia są uruchomione Windows 10, wersja 1703 lub nowsza lub Windows 11; Windows Server 2016, Windows Server 2019 lub Windows Server 2022
- [Funkcja Blokuj lub zezwalaj jest włączona](/microsoft-365/security/defender-endpoint/advanced-features)

#### <a name="indicators-for-ip-addresses-urls-or-domains"></a>Wskaźniki adresów IP, adresów URL lub domen

[Utworzenie wskaźnika "zezwalaj" dla adresu IP, adresu URL lub domeny](/microsoft-365/security/defender-endpoint/indicator-ip-domain) pomaga zapobiegać blokowi witryn lub adresów IP używanych przez organizację.

Przed utworzeniem wskaźników dla adresów IP, adresów URL lub domen upewnij się, że zostały spełnione następujące wymagania:

- Ochrona sieci w usłudze Defender dla punktu końcowego jest włączona w trybie bloku (zobacz [Włączanie ochrony sieci](/microsoft-365/security/defender-endpoint/enable-network-protection))
- Wersja klienta ochrony przed złośliwym kodem to 4.18.1906.x lub nowsza wersja
- Urządzenia są uruchomione Windows 10, wersja 1709 lub nowsza lub Windows 11

Niestandardowe wskaźniki sieciowe są włączone w [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Aby dowiedzieć się więcej, zobacz [Funkcje zaawansowane](/microsoft-365/security/defender-endpoint/advanced-features).

#### <a name="indicators-for-application-certificates"></a>Wskaźniki certyfikatów aplikacji

[Utworzenie wskaźnika "zezwalania" dla certyfikatu aplikacji](/microsoft-365/security/defender-endpoint/indicator-certificates) pomaga zapobiegać blokom aplikacji, takich jak aplikacje opracowane wewnętrznie, których używa organizacja. `.CER` lub `.PEM` rozszerzenia plików są obsługiwane.

Przed utworzeniem wskaźników dla certyfikatów aplikacji upewnij się, że zostały spełnione następujące wymagania:

- Program antywirusowy Microsoft Defender jest skonfigurowana z włączoną ochroną opartą na chmurze (zobacz [Zarządzanie ochroną opartą na chmurze](deploy-manage-report-microsoft-defender-antivirus.md)
- Wersja klienta ochrony przed złośliwym kodem to 4.18.1901.x lub nowsza wersja
- Urządzenia są uruchomione Windows 10, wersja 1703 lub nowsza lub Windows 11; Windows Server 2016, Windows Server 2019 lub Windows Server 2022
- Definicje ochrony przed wirusami i zagrożeniami są aktualne

> [!TIP]
> Podczas tworzenia wskaźników można zdefiniować je jeden po drugim lub zaimportować wiele elementów jednocześnie. Należy pamiętać, że istnieje limit 15 000 wskaźników dla jednej dzierżawy. Ponadto może być konieczne zebranie pewnych szczegółów, takich jak informacje o skrótie pliku. Przed [utworzeniem wskaźników](manage-indicators.md) należy zapoznać się z wymaganiami wstępnymi.

## <a name="part-4-submit-a-file-for-analysis"></a>Część 4. Przesyłanie pliku do analizy

Jednostki, takie jak pliki i wykrywanie bez plików, można przesyłać do firmy Microsoft w celu analizy. Badacze zabezpieczeń firmy Microsoft analizują wszystkie zgłoszenia, a ich wyniki pomagają informować Ochrona punktu końcowego w usłudze Microsoft Defender możliwości ochrony przed zagrożeniami. Po zalogowaniu się w witrynie przesyłania możesz śledzić swoje zgłoszenia.

### <a name="submit-a-file-for-analysis"></a>Przesyłanie pliku do analizy

Jeśli masz plik, który został błędnie wykryty jako złośliwy lub został pominięty, wykonaj następujące kroki, aby przesłać plik do analizy.

1. Zapoznaj się z wytycznymi tutaj: [Prześlij pliki do analizy](/windows/security/threat-protection/intelligence/submission-guide).

2. Odwiedź [witrynę przesyłania Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)i prześlij pliki).

### <a name="submit-a-fileless-detection-for-analysis"></a>Przesyłanie wykrywania bez plików do analizy

Jeśli coś zostało wykryte jako złośliwe oprogramowanie na podstawie zachowania i nie masz pliku, możesz przesłać `Mpsupport.cab` plik do analizy. Plik *.cab* można uzyskać za pomocą narzędzia Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe) w Windows 10 lub Windows 11.

1. Przejdź do ` C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`pozycji , a następnie uruchom polecenie `MpCmdRun.exe` jako administrator.

2. Wpisz `mpcmdrun.exe -GetFiles`, a następnie naciśnij **klawisz Enter**.

   Generowany jest plik .cab zawierający różne dzienniki diagnostyczne. Lokalizacja pliku jest określona w danych wyjściowych wiersza polecenia. Domyślnie lokalizacja to `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

3. Zapoznaj się z wytycznymi tutaj: [Prześlij pliki do analizy](/windows/security/threat-protection/intelligence/submission-guide).

4. Odwiedź [witrynę przesyłania Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)i prześlij pliki .cab.

### <a name="what-happens-after-a-file-is-submitted"></a>Co się stanie po przesłaniu pliku?

Twoje przesłanie jest natychmiast skanowane przez nasze systemy, aby dać Ci najnowszą determinację, nawet zanim analityk zacznie zajmować się Twoją sprawą. Możliwe, że plik mógł już zostać przesłany i przetworzony przez analityka. W takich przypadkach decyzja jest podejmowana szybko.

W przypadku zgłoszeń, które nie zostały jeszcze przetworzone, są one traktowane jako priorytetowe dla analizy w następujący sposób:

- Powszechnie stosowane pliki, które mogą mieć wpływ na dużą liczbę komputerów, mają wyższy priorytet.
- Uwierzytelnieni klienci, zwłaszcza klienci korporacyjni z [prawidłowymi identyfikatorami Software Assurance (SAID),](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) mają wyższy priorytet.
- Zgłoszenia oflagowane jako wysoki priorytet przez posiadaczy SAID są natychmiast zwracane na uwagę.

Aby sprawdzić aktualizacje dotyczące przesyłania, zaloguj się w [witrynie przesyłania Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission).

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Przesyłanie plików do analizy](/windows/security/threat-protection/intelligence/submission-guide#how-does-microsoft-prioritize-submissions).

## <a name="part-5-review-and-adjust-your-threat-protection-settings"></a>Część 5. Przeglądanie i dostosowywanie ustawień ochrony przed zagrożeniami

Ochrona punktu końcowego w usłudze Microsoft Defender oferuje szeroką gamę opcji, w tym możliwość dostosowywania ustawień dla różnych funkcji i możliwości. Jeśli otrzymujesz wiele wyników fałszywie dodatnich, przejrzyj ustawienia ochrony przed zagrożeniami w organizacji. Może być konieczne wprowadzenie pewnych zmian:

- [Ochrona dostarczana przez chmurę](#cloud-delivered-protection)
- [Korygowanie potencjalnie niechcianych aplikacji](#remediation-for-potentially-unwanted-applications)
- [Zautomatyzowane badanie i korygowanie](#automated-investigation-and-remediation)

### <a name="cloud-delivered-protection"></a>Ochrona dostarczana przez chmurę

Sprawdź poziom ochrony dostarczanej w chmurze pod kątem Program antywirusowy Microsoft Defender. Domyślnie ochrona dostarczana w chmurze jest ustawiona na **Wartość Nieskonfigurowane**, co odpowiada normalnemu poziomowi ochrony większości organizacji. Jeśli ochrona dostarczana w chmurze jest ustawiona na **wysoką**, **wysoką lub** **zerową tolerancję**, może wystąpić większa liczba wyników fałszywie dodatnich.

> [!TIP]
> Aby dowiedzieć się więcej na temat konfigurowania ochrony dostarczanej w chmurze, zobacz [Określanie poziomu ochrony dostarczanej w chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/specify-cloud-protection-level-microsoft-defender-antivirus).

Zalecamy używanie [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) do edytowania lub ustawiania ustawień ochrony dostarczanej w chmurze. Można jednak użyć innych metod, takich jak [zasady grupy](/azure/active-directory-domain-services/manage-group-policy) (zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-review-and-edit-cloud-delivered-protection-settings-for-existing-policies"></a>Używanie Microsoft Endpoint Manager do przeglądania i edytowania ustawień ochrony dostarczanych przez chmurę (dla istniejących zasad)

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) i zaloguj się.

2. Wybierz pozycję **Program antywirusowy** zabezpieczeń \> **punktu końcowego**, a następnie wybierz istniejące zasady. (Jeśli nie masz istniejących zasad lub chcesz utworzyć nowe zasady, przejdź do [następnej procedury](#use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy)).

3. W obszarze **Zarządzanie** wybierz pozycję **Właściwości**. Następnie obok pozycji **Ustawienia konfiguracji** wybierz pozycję **Edytuj**.

4. Rozwiń węzeł **Ochrona w chmurze** i przejrzyj bieżące ustawienie w wierszu **poziom ochrony dostarczanej w chmurze** . Zalecamy ustawienie ochrony dostarczanej w chmurze na **wartość Nie skonfigurowano**, co zapewnia silną ochronę przy jednoczesnym zmniejszeniu prawdopodobieństwa uzyskania wyników fałszywie dodatnich.

5. Wybierz **pozycję Przejrzyj i zapisz**, a następnie **pozycję Zapisz**.

#### <a name="use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy"></a>Użyj Microsoft Endpoint Manager, aby ustawić ustawienia ochrony dostarczanej w chmurze (dla nowych zasad)

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) i zaloguj się.

2. Wybierz pozycję **Program antywirusowy** \> zabezpieczeń \> **punktu końcowego** **i utwórz zasady**.

3. W obszarze **Platforma** wybierz opcję, a następnie w polu **Profil** wybierz pozycję **Program antywirusowy** lub **Program antywirusowy Microsoft Defender** (konkretna opcja zależy od wybranej opcji **platformy**). Następnie wybierz pozycję **Utwórz**.

4. Na **karcie Podstawy** określ nazwę i opis zasad. Następnie wybierz pozycję **Dalej**.

5. Na karcie **Ustawienia konfiguracji** rozwiń węzeł **Ochrona w chmurze** i określ następujące ustawienia:

   - Ustaw **opcję Włącz ochronę dostarczaną w chmurze na** **wartość Tak**.
   - Ustaw **poziom ochrony dostarczanej w chmurze** na **nieskonfigurowane**. (Ten poziom domyślnie zapewnia wysoki poziom ochrony przy jednoczesnym zmniejszeniu prawdopodobieństwa uzyskania wyników fałszywie dodatnich).

6. Na karcie **Tagi zakresu** , jeśli używasz tagów zakresu w organizacji, określ tagi zakresu dla zasad. (Zobacz [tagi zakresu](/mem/intune/fundamentals/scope-tags)).

7. Na **karcie Przypisania** określ użytkowników i grupy, do których mają być stosowane zasady, a następnie wybierz pozycję **Dalej**. (Jeśli potrzebujesz pomocy dotyczącej przypisań, zobacz [Przypisywanie profilów użytkowników i urządzeń w Microsoft Intune](/mem/intune/configuration/device-profile-assign)).

8. Na karcie **Przeglądanie i tworzenie** przejrzyj ustawienia, a następnie wybierz pozycję **Utwórz**.

### <a name="remediation-for-potentially-unwanted-applications"></a>Korygowanie potencjalnie niechcianych aplikacji

Potencjalnie niechciane aplikacje (PUA) to kategoria oprogramowania, która może powodować powolne działanie urządzeń, wyświetlanie nieoczekiwanych reklam lub instalowanie innego oprogramowania, które może być nieoczekiwane lub niepożądane. Przykłady PUA obejmują oprogramowanie reklamowe, oprogramowanie do tworzenia pakietów i oprogramowanie do uchylania się od płacenia podatków, które zachowuje się inaczej w przypadku produktów zabezpieczających. Chociaż pua nie jest uważany za złośliwe oprogramowanie, niektóre rodzaje oprogramowania są PUA na podstawie ich zachowania i reputacji.

> [!TIP]
> Aby dowiedzieć się więcej na temat usługi PUA, zobacz [Wykrywanie i blokowanie potencjalnie niechcianych aplikacji](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

W zależności od aplikacji używanych przez organizację wyniki fałszywie dodatnie mogą być wynikiem ustawień ochrony pua. W razie potrzeby rozważ uruchomienie ochrony pua w trybie inspekcji przez pewien czas lub zastosuj ochronę pua do podzestawu urządzeń w organizacji. Ochronę pua można skonfigurować dla przeglądarki Microsoft Edge i dla Program antywirusowy Microsoft Defender.

Zalecamy używanie [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) do edytowania lub ustawiania ustawień ochrony pua, jednak można użyć innych metod, takich jak [zasady grupy](/azure/active-directory-domain-services/manage-group-policy) (zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-edit-pua-protection-for-existing-configuration-profiles"></a>Użyj Microsoft Endpoint Manager, aby edytować ochronę pua (dla istniejących profilów konfiguracji)

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) i zaloguj się.

2. Wybierz pozycję Profile **konfiguracji** **urządzeń**\>, a następnie wybierz istniejące zasady. (Jeśli nie masz istniejących zasad lub chcesz utworzyć nowe zasady, przejdź do [następnej procedury](#use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile)).

3. W obszarze **Zarządzanie** wybierz pozycję **Właściwości**, a następnie obok pozycji **Ustawienia konfiguracji** wybierz pozycję **Edytuj**.

4. Na **karcie Ustawienia konfiguracji** przewiń w dół i rozwiń **Program antywirusowy Microsoft Defender**.

5. Ustaw **opcję Wykryj potencjalnie niechciane aplikacje** na **Wartość Inspekcja**. (Możesz go wyłączyć, ale przy użyciu trybu inspekcji będzie można zobaczyć wykrycia).

6. Wybierz **pozycję Przeglądanie i zapisywanie**, a następnie wybierz pozycję **Zapisz**.

#### <a name="use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile"></a>Użyj Microsoft Endpoint Manager, aby ustawić ochronę pua (dla nowego profilu konfiguracji)

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) i zaloguj się.

2. Wybierz pozycję Profile **konfiguracji** \> **urządzeń** \> **+ Utwórz profil**.

3. W obszarze **Platforma** wybierz **pozycję Windows 10 i nowsze**, a w obszarze **Profil** wybierz pozycję **Ograniczenia urządzenia**.

4. Na **karcie Podstawy** określ nazwę i opis zasad. Następnie wybierz pozycję **Dalej**.

5. Na **karcie Ustawienia konfiguracji** przewiń w dół i rozwiń **Program antywirusowy Microsoft Defender**.

6. Ustaw **pozycję Wykryj potencjalnie niechciane aplikacje** na **Wartość Inspekcja**, a następnie wybierz pozycję **Dalej**. (Możesz wyłączyć ochronę pua, ale przy użyciu trybu inspekcji będzie można zobaczyć wykrycia).

7. Na **karcie Przypisania** określ użytkowników i grupy, do których mają być stosowane zasady, a następnie wybierz pozycję **Dalej**. (Jeśli potrzebujesz pomocy dotyczącej przypisań, zobacz [Przypisywanie profilów użytkowników i urządzeń w Microsoft Intune](/mem/intune/configuration/device-profile-assign)).

8. Na karcie **Reguły stosowania** określ wersje lub wersje systemu operacyjnego do uwzględnienia lub wykluczenia z zasad. Można na przykład ustawić zasady, które mają być stosowane do wszystkich urządzeń w niektórych wersjach Windows 10. Następnie wybierz pozycję **Dalej**.

9. Na karcie **Przeglądanie i tworzenie** przejrzyj ustawienia, a następnie wybierz pozycję **Utwórz**.

### <a name="automated-investigation-and-remediation"></a>Zautomatyzowane badanie i korygowanie

[Funkcje zautomatyzowanego badania i korygowania](automated-investigations.md) (AIR) mają na celu zbadanie alertów i podjęcie natychmiastowych działań w celu rozwiązania problemów z naruszeniami. Po wyzwoleniu alertów i uruchomieniu zautomatyzowanego dochodzenia dla każdego badanego dowodu jest generowany werdykt. Werdykty mogą być *złośliwe*, *podejrzane* lub *nie znaleziono zagrożeń*.

W zależności od [poziomu automatyzacji ustawionego](/microsoft-365/security/defender-endpoint/automation-levels) dla organizacji i innych ustawień zabezpieczeń akcje korygowania są podejmowane w przypadku artefaktów, które są uważane za *złośliwe* lub *podejrzane*. W niektórych przypadkach akcje korygowania są wykonywane automatycznie; W innych przypadkach akcje korygowania są wykonywane ręcznie lub tylko po zatwierdzeniu przez zespół ds. operacji zabezpieczeń.

- [Dowiedz się więcej o poziomach automatyzacji](/microsoft-365/security/defender-endpoint/automation-levels); a następnie
- [Konfigurowanie funkcji AIR w usłudze Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation).

> [!IMPORTANT]
> Zalecamy korzystanie z *pełnej automatyzacji* w celu zautomatyzowanego badania i korygowania. Nie wyłączaj tych możliwości z powodu fałszywie dodatniego wyniku. Zamiast tego użyj [wskaźników "zezwalaj" w celu zdefiniowania wyjątków](#indicators-for-microsoft-defender-for-endpoint) i zachowania ustawień zautomatyzowanego badania i korygowania, aby automatycznie podejmować odpowiednie działania. Poniższe [wskazówki pomagają](automation-levels.md#levels-of-automation) zmniejszyć liczbę alertów, które musi obsłużyć zespół ds. operacji zabezpieczeń.

## <a name="still-need-help"></a>Nadal potrzebujesz pomocy?

Jeśli udało Ci się wykonać wszystkie kroki opisane w tym artykule i nadal potrzebujesz pomocy, skontaktuj się z pomocą techniczną.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> i zaloguj się.

2. W prawym górnym rogu wybierz znak zapytania (**?**), a następnie wybierz pozycję **Pomoc techniczna firmy Microsoft**.

3. W oknie **Asystent pomocy technicznej** opisz swój problem, a następnie wyślij wiadomość. W tym miejscu możesz otworzyć żądanie obsługi.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md) 

## <a name="see-also"></a>Zobacz też

[Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender](manage-mde-post-migration.md)

[Omówienie portalu Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
