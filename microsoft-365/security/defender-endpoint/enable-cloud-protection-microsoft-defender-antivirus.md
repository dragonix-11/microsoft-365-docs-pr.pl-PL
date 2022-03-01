---
title: Włączanie ochrony chmury w aplikacji Program antywirusowy Microsoft Defender
description: Włącz ochronę w chmurze, aby korzystać z szybkich i zaawansowanych funkcji ochrony.
keywords: Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, chmura, blok na pierwszy rzut oka
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.date: 02/03/2022
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 95abb603983ea16192d93b12757cde6fba026047
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015944"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>Włączanie ochrony chmury w aplikacji Program antywirusowy Microsoft Defender

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Program antywirusowy Microsoft Defender

[Ochrona chmury w Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) zapewnia dokładną, inteligentną ochronę w czasie rzeczywistym. Ochrona chmury powinna być domyślnie włączona; można jednak skonfigurować ochronę chmury odpowiednio do potrzeb organizacji.

## <a name="methods-to-configure-cloud-protection"></a>Metody konfigurowania ochrony chmury

Ochronę Program antywirusowy Microsoft Defender w chmurze możesz włączyć lub wyłączyć, używając jednej z kilku metod:

- Microsoft Endpoint Manager, które obejmują Microsoft Intune i Menedżer konfiguracji
- zasady grupy
- Polecenia cmdlet programu PowerShell

Możesz również włączyć lub wyłączyć ochronę w chmurze dla poszczególnych punktów końcowych przy Zabezpieczenia Windows aplikacji. 

Aby uzyskać więcej informacji na temat określonych wymagań dotyczących łączności sieciowej w celu zapewnienia, że punkty końcowe mogą łączyć się z usługą ochrony w chmurze, zobacz Konfigurowanie i weryfikowanie [połączeń sieciowych](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> W Windows 10 i Windows 11 nie ma żadnej różnicy między opcjami raportowania podstawowego i zaawansowanego opisanymi w tym artykule.  Jest to starsza różnica i wybranie jednego z tych ustawień spowoduje taki sam poziom ochrony w chmurze. Nie ma żadnej różnicy w typie ani ilości udostępnianych informacji. Aby uzyskać więcej informacji na temat tego, co zbieramy, zobacz [Oświadczenie o ochronie prywatności firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>Włączanie ochrony w chmurze za pomocą usługi Intune

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. W **okienku Narzędzia** domowe wybierz **pozycję Konfiguracja urządzenia > Profile**.

3. Wybierz typ **profilu Ograniczenia** urządzeń, który chcesz skonfigurować. Jeśli chcesz utworzyć nowy **typ profilu Ograniczenia** urządzeń, zobacz Konfigurowanie ustawień ograniczeń urządzeń w przeglądarce [Microsoft Intune](/intune/device-restrictions-configure).

4. Wybierz **pozycję Ustawienia** \> **konfiguracji właściwości: Edytuj** \> **Program antywirusowy Microsoft Defender**.

5. Na **przełączniku Ochrona dostarczana w** chmurze wybierz pozycję **Włącz**.

6. Z listy **rozwijanej Monituj użytkowników przed przykładowym przesłaniem** wybierz pozycję **Automatycznie wyślij wszystkie dane**.

Aby uzyskać więcej informacji o profilach urządzeń w usłudze Intune, w tym o tworzeniu i konfigurowaniu ich ustawień, zobacz Co to są Microsoft Intune [profilów urządzeń?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>Włączanie Microsoft Endpoint Manager w chmurze za pomocą aplikacji Microsoft Microsoft Endpoint Manager

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz pozycję **Endpoint security Antivirus (Zabezpieczenia punktu końcowego**\>).

3. Wybierz profil antywirusowy. (Jeśli nie masz jeszcze profilu lub chcesz utworzyć nowy profil, zobacz Konfigurowanie ustawień ograniczeń urządzeń w aplikacji [Microsoft Intune](/intune/device-restrictions-configure).

4. Wybierz **pozycję Właściwości**. Następnie obok ustawień **konfiguracji wybierz** pozycję **Edytuj**.

5. **Rozwiń pozycję Ochrona** w chmurze, a następnie na liście **Poziom ochrony w** chmurze wybierz jedną z następujących opcji:
   - **Wysoka**: stosuje wysoki poziom wykrywania.
   - **Wysoka plus**: korzysta **z wysokiego** poziomu i stosuje więcej zabezpieczeń (może mieć wpływ na wydajność klienta).
   - **Zero tolerancji**: Blokuje wszystkie nieznane pliki wykonywalne.

6. Wybierz **pozycję Recenzja + zapisywanie**, a następnie wybierz **pozycję Zapisz**.

Aby uzyskać więcej informacji na temat Microsoft Endpoint Configuration Manager, zobacz Jak tworzyć i wdrażać zasady ochrony przed [złośliwym oprogramowaniem: usługa ochrony przed złośliwym oprogramowaniem](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>Włączanie zasady grupy w chmurze za pomocą usługi Zasady grupy

1. Na zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W zasady grupy **zarządzania przejdź** do **konfiguracja komputera**.

3. Wybierz **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki** >  **Program antywirusowy Microsoft Defender > MAPY**

    > [!NOTE]
    > Ustawienia aplikacji MAPY są równe ochronie w chmurze.

5. Kliknij dwukrotnie pozycję **Dołącz do aplikacji Microsoft MAPS**. Upewnij się, że ta opcja jest włączona i ustawiona na wartość **MAPY podstawowe** lub **MAPY zaawansowane**. Wybierz przycisk **OK**.

    Możesz wysyłać podstawowe lub dodatkowe informacje o wykrytym oprogramowaniu:

    - Podstawowe MAPY: Członkostwo podstawowe wysyła do firmy Microsoft podstawowe informacje o złośliwym oprogramowaniu i potencjalnie niechcianym oprogramowaniu, które zostało wykryte na urządzeniu. Informacje obejmują miejsce, z którego pochodziło oprogramowanie (takie jak adresy URL i częściowe ścieżki), akcje wykonane w celu rozwiązania zagrożeń oraz to, czy akcje zostały wykonane pomyślnie.

    - MAPY zaawansowane. Oprócz podstawowych informacji członkostwo zaawansowane będzie wysyłać szczegółowe informacje o złośliwym oprogramowaniu i potencjalnie niechcianym oprogramowaniu, w tym pełną ścieżkę do oprogramowania oraz szczegółowe informacje o wpływie oprogramowania na urządzenie.

6. Kliknij dwukrotnie **pozycję Wyślij próbki plików podczas dalszej analizy**. Upewnij się, że dla pierwszej opcji ustawiono wartość **Włączone** , a dla pozostałych opcji ustawiono jedną z tych opcji:

   - **Wysyłanie bezpiecznych próbek** (1)
   - **Wysyłanie wszystkich próbek** (3)

   >[!NOTE]
   > Opcja **Wyślij bezpieczne próbki** (1) oznacza, że większość próbek zostanie wysłana automatycznie. Pliki, które mogą zawierać informacje osobiste, nadal będą wymagały dodatkowego potwierdzenia.
   > Ustawienie opcji Zawsze **monituj** (0) spowoduje obniżenie stanu ochrony urządzenia. Ustawienie wartości **Nigdy nie wysyłaj** (2) oznacza, że funkcja Blokuj od pierwszego rzutu [w programie](configure-block-at-first-sight-microsoft-defender-antivirus.md) Microsoft Defender dla punktu końcowego nie będzie działać.

7. Wybierz przycisk **OK**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>Włączanie ochrony w chmurze za pomocą poleceń cmdlet programu PowerShell

Następujące polecenia cmdlet mogą włączyć ochronę chmury:

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

Aby uzyskać więcej informacji na temat używania programu PowerShell z programem Program antywirusowy Microsoft Defender, zobacz Konfigurowanie i uruchamianie poleceń [cmdlet programu PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) Program antywirusowy Microsoft Defender oraz [ Program antywirusowy Microsoft Defender polecenia cmdlet](/powershell/module/defender/). [CSP zasad — Defender](/windows/client-management/mdm/policy-csp-defender) ma również więcej informacji, zwłaszcza [na temat -SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> Możesz ustawić **wartość -SubmitSamplesConsent na** `SendSafeSamples` (ustawienie domyślne, zalecane) `NeverSend`lub `AlwaysPrompt`. To `SendSafeSamples` ustawienie oznacza, że większość próbek zostanie wysłana automatycznie. Pliki, które mogą zawierać informacje osobiste, będą zawierać monit o kontynuowanie i będą wymagały potwierdzenia.
> Ustawienia `NeverSend` obniżą `AlwaysPrompt` poziom ochrony urządzenia. Ponadto to ustawienie `NeverSend` oznacza, że funkcja Blokuj [na pierwszy rzut](configure-block-at-first-sight-microsoft-defender-antivirus.md) oka programu Microsoft Defender dla punktu końcowego nie będzie działać.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>Włączanie Windows ochrony w chmurze za pomocą instrukcji zarządzania danymi (WMI)

Użyj metody [**Set** klasy **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) , aby uzyskać następujące właściwości:

```WMI
MAPSReporting
SubmitSamplesConsent
```

Aby uzyskać więcej informacji na temat dozwolonych parametrów, zobacz Windows Defender [interfejsów API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>Włączanie ochrony chmury dla poszczególnych klientów za pomocą Zabezpieczenia Windows klienta

> [!NOTE]
> Jeśli dla ustawienia Skonfiguruj lokalne zastępowanie ustawień raportowania usługi **Microsoft MAPS** zasady grupy jest ustawiona wartość **Wyłączone, ustawienie** ochrony oparte na chmurze w programie Windows Ustawienia będzie wyszatywne i niedostępne. Zmiany wprowadzone za pośrednictwem zasady grupy obiekt musi najpierw zostać wdrożony w poszczególnych punktach końcowych, aby ustawienie było aktualizowane w Windows Ustawienia.

1. Otwórz aplikację Zabezpieczenia Windows, wybierając ikonę tarczy na pasku zadań lub wyszukując w menu **Start Zabezpieczenia Windows.**

2. Wybierz **kafelek Ochrona przed &** przed zagrożeniami (lub ikonę tarczy na lewym pasku menu), a następnie w obszarze Zarządzanie  ustawieniami **wybierz & ustawienia ochrony przed zagrożeniami**.

3. Upewnij się **, że funkcja Ochrona w chmurze** **i Automatyczne przesyłanie próbki** są przełączone do **włączoną**.

   > [!NOTE]
   > Jeśli automatyczne przesyłanie próbek zostało skonfigurowane z zasady grupy, ustawienie będzie wyszańone i niedostępne.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z ochrony chmury firmy Microsoft w Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- [Jak tworzyć i wdrażać zasady ochrony przed złośliwym oprogramowaniem: usługa ochrony przed chmurą](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [Zarządzanie poleceniami cmdlet programu PowerShell Program antywirusowy Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
