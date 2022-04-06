---
title: Dołączanie przy użyciu Microsoft Endpoint Manager
description: Dowiedz się, jak korzystać z Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Microsoft Endpoint Manager
keywords: onboarding, configuration, deploy, deployment, endpoint manager, Ochrona punktu końcowego w usłudze Microsoft Defender, collection creation, endpoint detection response, next generation protection, attack surface reduction, microsoft endpoint manager
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
ms.openlocfilehash: ca4c3e4992e9beb10e9369aede9d5ad8b9d73709
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466988"
---
# <a name="onboarding-using-microsoft-endpoint-manager"></a>Dołączanie przy użyciu Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ten artykuł jest częścią przewodnika wdrażania i pełni rolę przykładowej metody wdrażania.

W [temacie](deployment-strategy.md) Planowanie zapewniono kilka metod dołączania urządzeń do usługi. W tym temacie o zagadnieniach o architekturze natywnej chmury.

:::image type="content" source="images/cloud-native-architecture.png" alt-text="Architektura natywna chmury" lightbox="images/cloud-native-architecture.png":::
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
- [Intune bazowe zabezpieczeń](/mem/intune/protect/security-baseline-settings-defender-atp#microsoft-defender)

Aby uzyskać więcej informacji na Microsoft Endpoint Manager, zapoznaj się z tymi zasobami:

- [Microsoft Endpoint Manager stronie](/mem/)
- [Wpis w blogu na temat Intune i ConfigMgr](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace/)
- [Klip wideo wprowadzający na temat MEM](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace)

## <a name="step-1-onboard-devices-by-creating-a-group-in-mem-to-assign-configurations-on"></a>Krok 1. Na urządzeniach przez utworzenie grupy w programie MEM w celu przypisania konfiguracji do

### <a name="identify-target-devices-or-users"></a>Identyfikowanie urządzeń docelowych lub użytkowników

W tej sekcji utworzymy grupę testową, w przypadku których będą przypisywane Konfiguracje.

> [!NOTE]
> Intune zarządzać urządzeniami i użytkownikami Azure Active Directory (Azure AD). Jako administrator Intune możesz skonfigurować grupy odpowiednio do potrzeb organizacji.
>
> Aby uzyskać więcej informacji, zobacz [Dodawanie grup w celu organizowania użytkowników i urządzeń](/mem/intune/fundamentals/groups-add).

### <a name="create-a-group"></a>Tworzenie grupy

1. Otwórz portal MEM.

2. Otwórz **okno Grupy > nowa grupa**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/66f724598d9c3319cba27f79dd4617a4.png" alt-text="Portal Microsoft Endpoint Manager 1" lightbox="images/66f724598d9c3319cba27f79dd4617a4.png":::

3. Wprowadź szczegóły i utwórz nową grupę.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/b1e0206d675ad07db218b63cd9b9abc3.png" alt-text="Portal Microsoft Endpoint Manager 2" lightbox="images/b1e0206d675ad07db218b63cd9b9abc3.png":::

4. Dodaj użytkownika lub urządzenie testowe.

5. W **okienku > Grupy** otwórz nową grupę.

6. Wybierz  **pozycję Członkowie > Dodaj członków**.

7. Znajdź użytkownika lub urządzenie testowe i wybierz je.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/149cbfdf221cdbde8159d0ab72644cd0.png" alt-text="Portal Microsoft Endpoint Manager 3" lightbox="images/149cbfdf221cdbde8159d0ab72644cd0.png":::

8. Grupa testów ma teraz członka do przetestowania.

## <a name="step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities"></a>Krok 2. Tworzenie zasad konfiguracji w celu skonfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender konfiguracji

W poniższej sekcji utworzysz szereg zasad konfiguracji.

Po pierwsze, zasady konfiguracji dotyczące wybierania grup użytkowników lub urządzeń, które zostaną włoowane do usługi Defender for Endpoint:

- [Wykrywanie i reagowanie dotyczące punktów końcowych](#endpoint-detection-and-response)

Następnie należy kontynuować tworzenie kilku różnych typów zasad zabezpieczeń punktów końcowych:

- [Ochrona nowej generacji](#next-generation-protection)
- [Zmniejszanie obszaru podatnego na ataki](#attack-surface-reduction---attack-surface-reduction-rules)

### <a name="endpoint-detection-and-response"></a>Wykrywanie i reagowanie dotyczące punktów końcowych

1. Otwórz portal MEM.

2. Przejdź do **punktu końcowego wykrywania > odpowiedzi i wykrywania punktu końcowego**. Kliknij pozycję **Utwórz profil**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/58dcd48811147feb4ddc17212b7fe840.png" alt-text="Portal Microsoft Endpoint Manager 4" lightbox="images/58dcd48811147feb4ddc17212b7fe840.png":::

3. W **obszarze Platforma wybierz pozycję Windows 10 i nowszą pozycję Profil — wykrywanie punktu** końcowego i > Utwórz.

4. Wprowadź nazwę i opis, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/a5b2d23bdd50b160fef4afd25dda28d4.png" alt-text="Portal Microsoft Endpoint Manager 5" lightbox="images/a5b2d23bdd50b160fef4afd25dda28d4.png":::

5. Wybierz ustawienia zgodnie z wymaganiami, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/cea7e288b5d42a9baf1aef0754ade910.png" alt-text="Portal Microsoft Endpoint Manager 6" lightbox="images/cea7e288b5d42a9baf1aef0754ade910.png":::

    > [!NOTE]
    > W tym przypadku zostało to automatycznie wypełnione, ponieważ program Defender dla punktu końcowego został już zintegrowany z usługą Intune. Aby uzyskać więcej informacji na temat integracji, zobacz [Włączanie Ochrona punktu końcowego w usłudze Microsoft Defender w Intune](/mem/intune/protect/advanced-threat-protection-configure#to-enable-microsoft-defender-atp).
    >
    > Na poniższej ilustracji przedstawiono przykład tego, co się dzieje, gdy Ochrona punktu końcowego w usłudze Microsoft Defender nie jest zintegrowana z programem Intune:
    >
    > :::image type="content" source="images/2466460812371ffae2d19a10c347d6f4.png" alt-text="Portal Microsoft Endpoint Manager 7" lightbox="images/2466460812371ffae2d19a10c347d6f4.png":::

6. W razie potrzeby dodaj tagi zakresu, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ef844f52ec2c0d737ce793f68b5e8408.png" alt-text="Portal Microsoft Endpoint Manager 8" lightbox="images/ef844f52ec2c0d737ce793f68b5e8408.png":::

7. Dodaj grupę testową, klikając pozycję **Wybierz grupy do dołączyć** i wybrać grupę, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/fc3525e20752da026ec9f46ab4fec64f.png" alt-text="Portal Microsoft Endpoint Manager 9" lightbox="images/fc3525e20752da026ec9f46ab4fec64f.png":::

8. Przejrzyj i zaakceptuj, a następnie wybierz  **pozycję Utwórz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/289172dbd7bd34d55d24810d9d4d8158.png" alt-text="Portal Microsoft Endpoint Manager 10" lightbox="images/289172dbd7bd34d55d24810d9d4d8158.png":::

9. Ukończone zasady możesz wyświetlić.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/5a568b6878be8243ea2b9d82d41ed297.png" alt-text="Portal Microsoft Endpoint Manager 11" lightbox="images/5a568b6878be8243ea2b9d82d41ed297.png":::

### <a name="next-generation-protection"></a>Ochrona nowej generacji

1. Otwórz portal MEM.

2. Przejdź do **punktu końcowego > oprogramowania antywirusowego > Utwórz zasady**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/6b728d6e0d71108d768e368b416ff8ba.png" alt-text="Portal Microsoft Endpoint Manager 12" lightbox="images/6b728d6e0d71108d768e368b416ff8ba.png":::

3. Wybierz **platformę — Windows 10 lub nowszą — Windows i profil — Program antywirusowy Microsoft Defender > Utwórz**.

4. Wprowadź nazwę i opis, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/a7d738dd4509d65407b7d12beaa3e917.png" alt-text="Portal Microsoft Endpoint Manager 13" lightbox="images/a7d738dd4509d65407b7d12beaa3e917.png":::

5. Na stronie **Ustawienia konfiguracji**: Ustaw konfiguracje wymagane dla usługi Program antywirusowy Microsoft Defender (Ochrona chmury, Wykluczenia, Ochrona Real-Time i Działania naprawcze).

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/3840b1576d6f79a1d72eb14760ef5e8c.png" alt-text="Portal Microsoft Endpoint Manager 14" lightbox="images/3840b1576d6f79a1d72eb14760ef5e8c.png":::

6. W razie potrzeby dodaj tagi zakresu, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/2055e4f9b9141525c0eb681e7ba19381.png" alt-text="Portal Microsoft Endpoint Manager 15" lightbox="images/2055e4f9b9141525c0eb681e7ba19381.png":::

7. Wybierz grupy do dołączyć, przypisz je do grupy testowej, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/48318a51adee06bff3908e8ad4944dc9.png" alt-text="Portal Microsoft Endpoint Manager 16" lightbox="images/48318a51adee06bff3908e8ad4944dc9.png":::

8. Przejrzyj i utwórz, a następnie wybierz  **pozycję Utwórz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/dfdadab79112d61bd3693d957084b0ec.png" alt-text="Portal Microsoft Endpoint Manager 17" lightbox="images/dfdadab79112d61bd3693d957084b0ec.png":::

9. Zobaczysz utworzone zasady konfiguracji.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/38180219e632d6e4ec7bd25a46398da8.png" alt-text="Portal Microsoft Endpoint Manager 18" lightbox="images/38180219e632d6e4ec7bd25a46398da8.png":::

### <a name="attack-surface-reduction---attack-surface-reduction-rules"></a>Zmniejszenie powierzchni ataków — reguły ograniczania powierzchni ataków

1. Otwórz portal MEM.

2. Przejdź do **punktu końcowego i > zmniejszenie powierzchni ataków**.

3. Wybierz  **pozycję Utwórz zasady**.

4. Wybierz **platformę — Windows 10 lub nowszą — Profil — Reguły** ograniczania powierzchni ataków > Utwórz.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/522d9bb4288dc9c1a957392b51384fdd.png" alt-text="Portal Microsoft Endpoint Manager 19" lightbox="images/522d9bb4288dc9c1a957392b51384fdd.png":::

5. Wprowadź nazwę i opis, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/a5a71fd73ec389f3cdce6d1a6bd1ff31.png" alt-text="Portal Microsoft Endpoint Manager 20" lightbox="images/a5a71fd73ec389f3cdce6d1a6bd1ff31.png":::

6. Na stronie **Ustawienia konfiguracji**: Ustaw konfiguracje wymagane dla reguł zmniejszania powierzchni ataków, a następnie wybierz pozycję  **Dalej**.

    > [!NOTE]
    > Wszystkie reguły ograniczania powierzchni ataków skonfigurujemy na inspekcję.
    >
    > Aby uzyskać więcej informacji, zobacz [Reguły ograniczania powierzchni ataków](attack-surface-reduction.md).

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/dd0c00efe615a64a4a368f54257777d0.png" alt-text="Portal Microsoft Endpoint Manager 21" lightbox="images/dd0c00efe615a64a4a368f54257777d0.png":::

7. Dodaj tagi zakresu zgodnie z wymaganiami, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/6daa8d347c98fe94a0d9c22797ff6f28.png" alt-text="Portal Microsoft Endpoint Manager 22" lightbox="images/6daa8d347c98fe94a0d9c22797ff6f28.png":::

8. Wybierz grupy, które chcesz dołączyć i przypisać do grupy testowej, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/45cefc8e4e474321b4d47b4626346597.png" alt-text="Portal Microsoft Endpoint Manager 23" lightbox="images/45cefc8e4e474321b4d47b4626346597.png":::

9. Przejrzyj szczegóły, a następnie wybierz  **pozycję Utwórz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/2c2e87c5fedc87eba17be0cdeffdb17f.png" alt-text="Portal Microsoft Endpoint Manager 24" lightbox="images/2c2e87c5fedc87eba17be0cdeffdb17f.png":::

10. Wyświetl zasady.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/7a631d17cc42500dacad4e995823ffef.png" alt-text="Portal Microsoft Endpoint Manager 25" lightbox="images/7a631d17cc42500dacad4e995823ffef.png":::

### <a name="attack-surface-reduction---web-protection"></a>Zmniejszenie tabletu Surface w przypadku ataków — ochrona sieci Web

1. Otwórz portal MEM.

2. Przejdź do **punktu końcowego i > zmniejszenie powierzchni ataków**.

3. Wybierz  **pozycję Utwórz zasady**.

4. Wybierz **pozycję Windows 10 i nowsze — ochrona sieci Web > Utwórz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/cd7b5a1cbc16cc05f878cdc99ba4c27f.png" alt-text="Portal Microsoft Endpoint Manager 26" lightbox="images/cd7b5a1cbc16cc05f878cdc99ba4c27f.png":::

5. Wprowadź nazwę i opis, a następnie wybierz pozycję  **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/5be573a60cd4fa56a86a6668b62dd808.png" alt-text="Portal Microsoft Endpoint Manager 27" lightbox="images/5be573a60cd4fa56a86a6668b62dd808.png":::

6. Na stronie **Ustawienia konfiguracji**: Ustaw konfiguracje wymagane do ochrony sieci Web, a następnie wybierz pozycję  **Dalej**.

    > [!NOTE]
    > Konfigurujemy ochronę sieci Web w celu blokowania.
    >
    > Aby uzyskać więcej informacji, zobacz [Ochrona sieci Web](web-protection-overview.md).

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/6104aa33a56fab750cf30ecabef9f5b6.png" alt-text="Portal Microsoft Endpoint Manager 28" lightbox="images/6104aa33a56fab750cf30ecabef9f5b6.png":::

7. Dodaj **tagi zakresu jako wymagane do > Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/6daa8d347c98fe94a0d9c22797ff6f28.png" alt-text="Portal Microsoft Endpoint Manager 29" lightbox="images/6daa8d347c98fe94a0d9c22797ff6f28.png":::

8. Wybierz **pozycję Przypisz, aby przetestować > Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/45cefc8e4e474321b4d47b4626346597.png" alt-text="Portal Microsoft Endpoint Manager 30" lightbox="images/45cefc8e4e474321b4d47b4626346597.png":::

9. Wybierz **pozycję Recenzja i > Utwórz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/8ee0405f1a96c23d2eb6f737f11c1ae5.png" alt-text="Portal Microsoft Endpoint Manager 31" lightbox="images/8ee0405f1a96c23d2eb6f737f11c1ae5.png":::

10. Wyświetl zasady.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/e74f6f6c150d017a286e6ed3dffb7757.png" alt-text="Portal Microsoft Endpoint Manager 32" lightbox="images/e74f6f6c150d017a286e6ed3dffb7757.png":::

## <a name="validate-configuration-settings"></a>Sprawdzanie poprawności ustawień konfiguracji

### <a name="confirm-policies-have-been-applied"></a>Potwierdzanie zastosowania zasad

Po przypisaniu zasad konfiguracji zastosowanie ich zajmie trochę czasu.

Aby uzyskać informacje o chronometrażu, [Intune informacje o konfiguracji](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

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
    > :::image type="content" source="images/88efb4c3710493a53f2840c3eac3e3d3.png" alt-text="Strona ustawień 1" lightbox="images/88efb4c3710493a53f2840c3eac3e3d3.png":::

2. Po zastosowaniu zasad nie można ręcznie zarządzać ustawieniami.

    > [!NOTE]
    > Na poniższej **ilustracji Włączanie ochrony w** chmurze i **Włączanie ochrony w** czasie rzeczywistym są wyświetlane jako zarządzane.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/9341428b2d3164ca63d7d4eaa5cff642.png" alt-text="Strona ustawień 2" lightbox="images/9341428b2d3164ca63d7d4eaa5cff642.png":::

### <a name="confirm-attack-surface-reduction---attack-surface-reduction-rules"></a>Potwierdź zmniejszenie powierzchni ataków — reguły ograniczania powierzchni ataków

1. Przed zastosowaniem zasad na urządzeniu testowym wpisz piórem okno programu PowerShell `Get-MpPreference`.

2. Powinno to odpowiadać w następujących wierszach bez zawartości:

    > AttackSurfaceReductionOnlyExclusions:
    >
    > AttackSurfaceReductionRules_Actions:
    >
    > AttackSurfaceReductionRules_Ids:

    :::image type="content" source="images/cb0260d4b2636814e37eee427211fe71.png" alt-text="Wiersz polecenia (1)" lightbox="images/cb0260d4b2636814e37eee427211fe71.png":::

3. Po zastosowaniu zasad na urządzeniu testowym otwórz okno programu PowerShell i Windows wpisz `Get-MpPreference`.

4. Powinno to odpowiadać na następujące wiersze z zawartością, jak pokazano poniżej:

   :::image type="content" source="images/619fb877791b1fc8bc7dfae1a579043d.png" alt-text="Wiersz polecenia (2)" lightbox="images/619fb877791b1fc8bc7dfae1a579043d.png":::

### <a name="confirm-attack-surface-reduction---web-protection"></a>Potwierdź zmniejszenie powierzchni ataków — ochrona sieci Web

1. Na urządzeniu testowym otwórz program PowerShell i Windows wpisz `(Get-MpPreference).EnableNetworkProtection`.

2. Powinna to być odpowiedź z wartością 0, jak pokazano poniżej.

   :::image type="content" source="images/196a8e194ac99d84221f405d0f684f8c.png" alt-text="Wiersz polecenia 3" lightbox="images/196a8e194ac99d84221f405d0f684f8c.png":::

3. Po zastosowaniu zasad otwórz okno programu PowerShell i Windows wpisz `(Get-MpPreference).EnableNetworkProtection`.

4. Powinna to być odpowiedź przy użyciu wartości 1, jak pokazano poniżej.

   :::image type="content" source="images/c06fa3bbc2f70d59dfe1e106cd9a4683.png" alt-text="Wiersz polecenia (4)" lightbox="images/c06fa3bbc2f70d59dfe1e106cd9a4683.png":::
