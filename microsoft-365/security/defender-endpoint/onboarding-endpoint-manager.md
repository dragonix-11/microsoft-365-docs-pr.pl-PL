---
title: Dołączanie przy użyciu Microsoft Endpoint Manager
description: Dowiedz się, jak korzystać z programu Microsoft Defender dla punktu końcowego przy użyciu programu Microsoft Endpoint Manager
keywords: onboarding, configuration, deploy, deployment, endpoint manager, Microsoft Defender for Endpoint, collection creation, endpoint detection response, next generation protection, attack surface reduction, microsoft endpoint manager
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 261cb8af0f1fbb4c118aca649945f66015f1d25c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322785"
---
# <a name="onboarding-using-microsoft-endpoint-manager"></a>Dołączanie przy użyciu Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ten artykuł jest częścią przewodnika wdrażania i pełni rolę przykładowej metody wdrażania.

W [temacie](deployment-strategy.md) Planowanie zapewniono kilka metod dołączania urządzeń do usługi. W tym temacie o zagadnieniach o architekturze natywnej chmury.

![Obraz architektury natywnej chmury.](images/cloud-native-architecture.png)
 *Diagram architektury środowiska*

Chociaż program Defender for Endpoint obsługuje dołączanie różnych punktów końcowych i narzędzi, ten artykuł nie obejmuje ich. Aby uzyskać informacje na temat ogólnego wdrażania przy użyciu innych obsługiwanych narzędzi i metod wdrażania, zobacz [Omówienie wdrażania](onboarding.md).

[Microsoft Endpoint Manager](/mem/endpoint-manager-overview) rozwiązaniami, które ujednolicono kilka usług. Obejmuje on [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) oparte na urządzeniach.

W tym temacie podano dla użytkowników:

- Krok 1. Dołączanie urządzeń do usługi przez utworzenie grupy w programie Microsoft Endpoint Manager (MEM) do przypisywania konfiguracji w
- Krok 2. Konfigurowanie funkcji programu Defender for Endpoint przy użyciu programu Microsoft Endpoint Manager

W ramach tych wskazówek dotyczących dołączania należy wykonać następujące podstawowe czynności, które należy wykonać podczas korzystania z Microsoft Endpoint Manager:

- [Identyfikowanie urządzeń docelowych lub użytkowników](#identify-target-devices-or-users)
  - Tworzenie grupy Azure Active Directory użytkownika (użytkownika lub urządzenia)
- [Tworzenie profilu konfiguracji](#step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities)
  - W Microsoft Endpoint Manager tworzymy osobne zasady dla poszczególnych funkcji.

## <a name="resources"></a>Zasoby

Oto linki potrzebne do pozostałych części procesu:

- [Portal MEM](https://aka.ms/memac)
- [Microsoft 365 Defender](https://security.microsoft.com)
- [Ustawienia bazowe zabezpieczeń usługi Intune](/mem/intune/protect/security-baseline-settings-defender-atp#microsoft-defender)

Aby uzyskać więcej informacji na Microsoft Endpoint Manager, zapoznaj się z tymi zasobami:

- [Microsoft Endpoint Manager stronie](/mem/)
- [Wpis w blogu poświęcony usłudze Intune i ConfigMgr](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace/)
- [Klip wideo wprowadzający na temat MEM](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace)

## <a name="step-1-onboard-devices-by-creating-a-group-in-mem-to-assign-configurations-on"></a>Krok 1. Na urządzeniach przez utworzenie grupy w programie MEM w celu przypisania konfiguracji do

### <a name="identify-target-devices-or-users"></a>Identyfikowanie urządzeń docelowych lub użytkowników

W tej sekcji utworzymy grupę testową, w przypadku których będą przypisywane Konfiguracje.

> [!NOTE]
> W usłudze Intune Azure Active Directory (Azure AD) do zarządzania urządzeniami i użytkownikami. Jako administrator usługi Intune możesz skonfigurować grupy odpowiednio do potrzeb organizacji.
>
> Aby uzyskać więcej informacji, zobacz [Dodawanie grup w celu organizowania użytkowników i urządzeń](/mem/intune/fundamentals/groups-add).

### <a name="create-a-group"></a>Tworzenie grupy

1. Otwórz portal MEM.

2. Otwórz **okno Grupy > nowa grupa**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu1.](images/66f724598d9c3319cba27f79dd4617a4.png)

3. Wprowadź szczegóły i utwórz nową grupę.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu2.](images/b1e0206d675ad07db218b63cd9b9abc3.png)

4. Dodaj użytkownika lub urządzenie testowe.

5. W **okienku > Grupy** otwórz nową grupę.

6. Wybierz  **pozycję Członkowie > Dodaj członków**.

7. Znajdź użytkownika lub urządzenie testowe i wybierz je.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal3.](images/149cbfdf221cdbde8159d0ab72644cd0.png)

8. Grupa testów ma teraz członka do przetestowania.

## <a name="step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities"></a>Krok 2. Tworzenie zasad konfiguracji w celu skonfigurowania programu Microsoft Defender pod zakresie możliwości punktu końcowego

W poniższej sekcji utworzysz szereg zasad konfiguracji.

Po pierwsze, zasady konfiguracji dotyczące wybierania grup użytkowników lub urządzeń, które zostaną włoowane do usługi Defender for Endpoint:

- [Wykrywanie punktu końcowego i odpowiedź](#endpoint-detection-and-response)

Następnie należy kontynuować tworzenie kilku różnych typów zasad zabezpieczeń punktów końcowych:

- [Ochrona następnej generacji](#next-generation-protection)
- [Zmniejszenie powierzchni ataków](#attack-surface-reduction---attack-surface-reduction-rules)

### <a name="endpoint-detection-and-response"></a>Wykrywanie punktu końcowego i odpowiedź

1. Otwórz portal MEM.

2. Przejdź do **punktu końcowego wykrywania > odpowiedzi i wykrywania punktu końcowego**. Kliknij pozycję **Utwórz profil**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu4.](images/58dcd48811147feb4ddc17212b7fe840.png)

3. W **obszarze Platforma wybierz pozycję Windows 10 i nowszą pozycję Profil — wykrywanie punktu** końcowego i > Utwórz.

4. Wprowadź nazwę i opis, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu5.](images/a5b2d23bdd50b160fef4afd25dda28d4.png)

5. Wybierz ustawienia zgodnie z wymaganiami, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal6.](images/cea7e288b5d42a9baf1aef0754ade910.png)

    > [!NOTE]
    > W tym przypadku zostało to automatycznie wypełnione, ponieważ usługa Defender for Endpoint została już zintegrowana z usługą Intune. Aby uzyskać więcej informacji na temat integracji, zobacz [Włączanie programu Microsoft Defender dla punktu końcowego w usłudze Intune](/mem/intune/protect/advanced-threat-protection-configure#to-enable-microsoft-defender-atp).
    >
    > Na poniższej ilustracji przedstawiono przykład tego, co się dzieje, gdy program Microsoft Defender for Endpoint nie jest zintegrowany z usługą Intune:
    >
    > ![Obraz Microsoft Endpoint Manager portalu7.](images/2466460812371ffae2d19a10c347d6f4.png)

6. W razie potrzeby dodaj tagi zakresu, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu8.](images/ef844f52ec2c0d737ce793f68b5e8408.png)

7. Dodaj grupę testową, klikając pozycję **Wybierz grupy do dołączyć** i wybrać grupę, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu9.](images/fc3525e20752da026ec9f46ab4fec64f.png)

8. Przejrzyj i zaakceptuj, a następnie wybierz  **pozycję Utwórz**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu10.](images/289172dbd7bd34d55d24810d9d4d8158.png)

9. Ukończone zasady możesz wyświetlić.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu11.](images/5a568b6878be8243ea2b9d82d41ed297.png)

### <a name="next-generation-protection"></a>Ochrona następnej generacji

1. Otwórz portal MEM.

2. Przejdź do **punktu końcowego > oprogramowania antywirusowego > Utwórz zasady**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu12.](images/6b728d6e0d71108d768e368b416ff8ba.png)

3. Wybierz **platformę — Windows 10 lub nowszą — Windows i profil — Program antywirusowy Microsoft Defender > Utwórz**.

4. Wprowadź nazwę i opis, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu13.](images/a7d738dd4509d65407b7d12beaa3e917.png)

5. Na stronie **Ustawienia konfiguracji**: Ustaw konfiguracje wymagane dla usługi Program antywirusowy Microsoft Defender (Ochrona chmury, Wykluczenia, Ochrona Real-Time i Działania naprawcze).

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu14.](images/3840b1576d6f79a1d72eb14760ef5e8c.png)

6. W razie potrzeby dodaj tagi zakresu, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu15.](images/2055e4f9b9141525c0eb681e7ba19381.png)

7. Wybierz grupy do dołączyć, przypisz je do grupy testowej, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu16.](images/48318a51adee06bff3908e8ad4944dc9.png)

8. Przejrzyj i utwórz, a następnie wybierz  **pozycję Utwórz**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu17.](images/dfdadab79112d61bd3693d957084b0ec.png)

9. Zobaczysz utworzone zasady konfiguracji.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu18.](images/38180219e632d6e4ec7bd25a46398da8.png)

### <a name="attack-surface-reduction---attack-surface-reduction-rules"></a>Zmniejszenie powierzchni ataków — reguły ograniczania powierzchni ataków

1. Otwórz portal MEM.

2. Przejdź do **punktu końcowego i > zmniejszenie powierzchni ataków**.

3. Wybierz  **pozycję Utwórz zasady**.

4. Wybierz **platformę — Windows 10 lub nowszą — Profil — Reguły** ograniczania powierzchni ataków > Utwórz.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu19.](images/522d9bb4288dc9c1a957392b51384fdd.png)

5. Wprowadź nazwę i opis, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal20.](images/a5a71fd73ec389f3cdce6d1a6bd1ff31.png)

6. Na stronie **Ustawienia konfiguracji**: Ustaw konfiguracje wymagane dla reguł zmniejszania powierzchni ataków, a następnie wybierz pozycję  **Dalej**.

    > [!NOTE]
    > Wszystkie reguły ograniczania powierzchni ataków skonfigurujemy na inspekcję.
    >
    > Aby uzyskać więcej informacji, zobacz [Reguły ograniczania powierzchni ataków](attack-surface-reduction.md).

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal21.](images/dd0c00efe615a64a4a368f54257777d0.png)

7. Dodaj tagi zakresu zgodnie z wymaganiami, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal22.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. Wybierz grupy, które chcesz dołączyć i przypisać do grupy testowej, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu23.](images/45cefc8e4e474321b4d47b4626346597.png)

9. Przejrzyj szczegóły, a następnie wybierz  **pozycję Utwórz**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal24.](images/2c2e87c5fedc87eba17be0cdeffdb17f.png)

10. Wyświetl zasady.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu25.](images/7a631d17cc42500dacad4e995823ffef.png)

### <a name="attack-surface-reduction---web-protection"></a>Zmniejszenie tabletu Surface w przypadku ataków — ochrona sieci Web

1. Otwórz portal MEM.

2. Przejdź do **punktu końcowego i > zmniejszenie powierzchni ataków**.

3. Wybierz  **pozycję Utwórz zasady**.

4. Wybierz **pozycję Windows 10 i nowsze — ochrona sieci Web > Utwórz**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal26.](images/cd7b5a1cbc16cc05f878cdc99ba4c27f.png)

5. Wprowadź nazwę i opis, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal27.](images/5be573a60cd4fa56a86a6668b62dd808.png)

6. Na stronie **Ustawienia konfiguracji**: Ustaw konfiguracje wymagane do ochrony sieci Web, a następnie wybierz pozycję  **Dalej**.

    > [!NOTE]
    > Konfigurujemy ochronę sieci Web w celu blokowania.
    >
    > Aby uzyskać więcej informacji, zobacz [Ochrona sieci Web](web-protection-overview.md).

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal28.](images/6104aa33a56fab750cf30ecabef9f5b6.png)

7. Dodaj **tagi zakresu jako wymagane do > Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portalu29.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. Wybierz **pozycję Przypisz, aby przetestować > Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal30.](images/45cefc8e4e474321b4d47b4626346597.png)

9. Wybierz **pozycję Recenzja i > Utwórz**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal31.](images/8ee0405f1a96c23d2eb6f737f11c1ae5.png)

10. Wyświetl zasady.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager portal32.](images/e74f6f6c150d017a286e6ed3dffb7757.png)

## <a name="validate-configuration-settings"></a>Sprawdzanie poprawności ustawień konfiguracji

### <a name="confirm-policies-have-been-applied"></a>Potwierdzanie zastosowania zasad

Po przypisaniu zasad konfiguracji zastosowanie ich zajmie trochę czasu.

Aby uzyskać informacje o chronometrażu, zobacz [Informacje o konfiguracji usługi Intune](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Aby potwierdzić, że zasady konfiguracji zostały zastosowane do urządzenia testowego, wykonaj poniższe czynności dla poszczególnych zasad konfiguracji.

1. Otwórz portal MEM i przejdź do odpowiednich zasad, jak pokazano w powyższych krokach. W poniższym przykładzie pokazano ustawienia ochrony następnej generacji.

    > [!div class="mx-imgBorder"]
    > [![Obraz Microsoft Endpoint Manager portal33.](images/43ab6aa74471ee2977e154a4a5ef2d39.png)](images/43ab6aa74471ee2977e154a4a5ef2d39.png#lightbox)

2. Wybierz pozycję **Zasady konfiguracji,** aby wyświetlić stan zasad.

    > [!div class="mx-imgBorder"]
    > [![Obraz Microsoft Endpoint Manager portal34.](images/55ecaca0e4a022f0e29d45aeed724e6c.png)](images/55ecaca0e4a022f0e29d45aeed724e6c.png#lightbox)

3. Wybierz  **pozycję Stan urządzenia** , aby wyświetlić stan.

    > [!div class="mx-imgBorder"]
    > [![Obraz Microsoft Endpoint Manager portal35.](images/18a50df62cc38749000dbfb48e9a4c9b.png)](images/18a50df62cc38749000dbfb48e9a4c9b.png#lightbox)

4. Wybierz  **pozycję Stan użytkownika** , aby wyświetlić stan.

    > [!div class="mx-imgBorder"]
    > [![Obraz Microsoft Endpoint Manager portal36.](images/4e965749ff71178af8873bc91f9fe525.png)](images/4e965749ff71178af8873bc91f9fe525.png#lightbox)

5. Wybierz  **pozycję Stan ustawienia,** aby wyświetlić stan.

    > [!TIP]
    > Ten widok jest bardzo przydatny do identyfikowania ustawień, które są w konflikcie z innymi zasadami.

    > [!div class="mx-imgBorder"]
    > [![Obraz Microsoft Endpoint Manager portal37.](images/42acc69d0128ed09804010bdbdf0a43c.png)](images/42acc69d0128ed09804010bdbdf0a43c.png#lightbox)

### <a name="confirm-endpoint-detection-and-response"></a>Potwierdź wykrywanie i reagowanie w punktach końcowych

1. Przed zastosowaniem konfiguracji usługa Defender for Endpoint Protection nie powinna zostać uruchomiona.

    > [!div class="mx-imgBorder"]
    > [![Obraz panelu1 Services (Usługi).](images/b418a232a12b3d0a65fc98248dbb0e31.png)](images/b418a232a12b3d0a65fc98248dbb0e31.png#lightbox)

2. Po zastosowaniu konfiguracji usługa Defender for Endpoint Protection powinna zostać uruchomiona.

    > [!div class="mx-imgBorder"]
    > [![Obraz panelu Usługi2.](images/a621b699899f1b41db211170074ea59e.png)](images/a621b699899f1b41db211170074ea59e.png#lightbox)

3. Po uruchomieniu usług na urządzeniu urządzenie jest wyświetlane w Microsoft 365 Defender sieci.

    > [!div class="mx-imgBorder"]
    > [![Obraz Microsoft 365 Defender portalu](images/df0c64001b9219cfbd10f8f81a273190.png)](images/df0c64001b9219cfbd10f8f81a273190.png#lightbox)

### <a name="confirm-next-generation-protection"></a>Potwierdzanie ochrony następnej generacji

1. Przed zastosowaniem zasad na urządzeniu testowym powinno być możliwe ręczne zarządzanie ustawieniami, jak pokazano poniżej.

    > [!div class="mx-imgBorder"]
    > ![Obraz ustawiania strony1.](images/88efb4c3710493a53f2840c3eac3e3d3.png)

2. Po zastosowaniu zasad nie można ręcznie zarządzać ustawieniami.

    > [!NOTE]
    > Na poniższej **ilustracji Włączanie ochrony w** chmurze i **Włączanie ochrony w** czasie rzeczywistym są wyświetlane jako zarządzane.

    > [!div class="mx-imgBorder"]
    > ![Obraz ustawiania strony2.](images/9341428b2d3164ca63d7d4eaa5cff642.png)

### <a name="confirm-attack-surface-reduction---attack-surface-reduction-rules"></a>Potwierdź zmniejszenie powierzchni ataków — reguły ograniczania powierzchni ataków

1. Przed zastosowaniem zasad na urządzeniu testowym wpisz piórem okno programu PowerShell `Get-MpPreference`.

2. Powinno to odpowiadać w następujących wierszach bez zawartości:

    > AttackSurfaceReductionOnlyExclusions:
    >
    > AttackSurfaceReductionRules_Actions:
    >
    > AttackSurfaceReductionRules_Ids:

    ![Obraz wiersza polecenia1.](images/cb0260d4b2636814e37eee427211fe71.png)

3. Po zastosowaniu zasad na urządzeniu testowym otwórz okno programu PowerShell i Windows wpisz `Get-MpPreference`.

4. Powinno to odpowiadać na następujące wiersze z zawartością, jak pokazano poniżej:

    ![Obraz wiersza polecenia2.](images/619fb877791b1fc8bc7dfae1a579043d.png)

### <a name="confirm-attack-surface-reduction---web-protection"></a>Potwierdź zmniejszenie powierzchni ataków — ochrona sieci Web

1. Na urządzeniu testowym otwórz program PowerShell i Windows wpisz `(Get-MpPreference).EnableNetworkProtection`.

2. Powinna to być odpowiedź z wartością 0, jak pokazano poniżej.

    ![Obraz wiersza polecenia3.](images/196a8e194ac99d84221f405d0f684f8c.png)

3. Po zastosowaniu zasad otwórz okno programu PowerShell i Windows wpisz `(Get-MpPreference).EnableNetworkProtection`.

4. Powinna to być odpowiedź przy użyciu wartości 1, jak pokazano poniżej.

    ![Obraz wiersza polecenia4.](images/c06fa3bbc2f70d59dfe1e106cd9a4683.png)
