---
title: Konfigurowanie dostępu warunkowego w programie Microsoft Defender dla punktu końcowego
description: Informacje o czynnościach, które należy wykonać w usłudze Intune, usłudze Microsoft 365 Defender i platformie Azure w celu wdrożenia dostępu warunkowego
keywords: dostęp warunkowy, warunkowy, dostęp, ryzyko urządzenia, poziom ryzyka, integracja, integracja z usługą Intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8706f756b4e8d0ba87a747396e8f7ef71d66460c
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996230"
---
# <a name="configure-conditional-access-in-microsoft-defender-for-endpoint"></a>Konfigurowanie dostępu warunkowego w programie Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Ta sekcja przeprowadzi Cię przez wszystkie kroki, które należy wykonać, aby prawidłowo zaimplementować dostęp warunkowy.

## <a name="before-you-begin"></a>Przed rozpoczęciem

> [!WARNING]
> Należy pamiętać, że zarejestrowane urządzenia w usłudze Azure AD nie są obsługiwane w tym scenariuszu.</br>
> Obsługiwane są tylko urządzenia zarejestrowane w usłudze Intune.

Musisz się upewnić, że wszystkie Twoje urządzenia są zarejestrowane w usłudze Intune. Aby zarejestrować urządzenia w usłudze Intune, możesz użyć dowolnej z następujących opcji:

- Administrator IT: Aby uzyskać więcej informacji na temat włączania automatycznego rejestrowania, zobacz Windows [rejestracja](/intune/windows-enroll#enable-windows-10-automatic-enrollment)
- Użytkownik końcowy: Aby uzyskać więcej informacji na temat rejestrowania urządzenia z systemem Windows 10 i Windows 11 w usłudze Intune, zobacz Rejestrowanie urządzenia Windows 10 [w usłudze Intune.](/intune/quickstart-enroll-windows-device)
- Alternatywa dla użytkowników końcowych: Aby uzyskać więcej informacji na temat dołączania do domeny usługi Azure AD, zobacz Jak [zaplanować implementację dołączania do usługi Azure AD](/azure/active-directory/devices/azureadjoin-plan).

W programie Microsoft 365 Defender, portalu Intune i portalu Azure AD należy wykonać kilka czynności.

Ważne jest, aby zanotować wymagane role, aby uzyskać dostęp do tych portali i zaimplementować dostęp warunkowy:

- **Microsoft 365 Defender** — musisz zalogować się do portalu przy użyciu roli administratora globalnego, aby włączyć integrację.
- **Intune** — musisz zalogować się do portalu z uprawnieniami administratora zabezpieczeń z uprawnieniami zarządzania.
- **Portal usługi Azure AD** — musisz zalogować się jako administrator globalny, administrator zabezpieczeń lub administrator dostępu warunkowego.

> [!NOTE]
> Potrzebne jest środowisko programu Microsoft Intune z zarządzanym usługą Intune oraz sprzężeniami usługi Azure AD Windows 10 i Windows 11 urządzeń.

Aby włączyć dostęp warunkowy, zrób tak:

- Krok 1. Włączanie połączenia Microsoft Intune z Microsoft 365 Defender
- Krok 2. Włączanie integracji usługi Defender for Endpoint w usłudze Intune
- Krok 3. Tworzenie zasad zgodności w usłudze Intune
- Krok 4. Przypisywanie zasad 
- Krok 5. Tworzenie zasad dostępu warunkowego w usłudze Azure AD

### <a name="step-1-turn-on-the-microsoft-intune-connection"></a>Krok 1. Włączanie połączenia Microsoft Intune sieciowego

1. W okienku nawigacji **wybierz pozycję Ustawienia** \> **punkty końcowe** \> **Ogólne** \> **funkcje** \> zaawansowane Microsoft Intune **nawigacji**.
2. Przełącz przełącznik Microsoft Intune na **włączoną**.
3. Kliknij **pozycję Zapisz preferencje**.

### <a name="step-2-turn-on-the-defender-for-endpoint-integration-in-intune"></a>Krok 2. Włączanie integracji usługi Defender for Endpoint w usłudze Intune

1. Zaloguj się do witryny [Azure Portal](https://portal.azure.com).
2. Wybierz **pozycję Zgodność urządzenia** \> **Microsoft Defender ATP**.
3. Ustaw **Połączenie Windows 10.0.15063+ na wartość Zaawansowana ochrona przed** zagrożeniami w programie Microsoft Defender na **wartość Wł**.
4. Kliknij **Zapisz**.

### <a name="step-3-create-the-compliance-policy-in-intune"></a>Krok 3. Tworzenie zasad zgodności w usłudze Intune

1. W portalu [Azure wybierz](https://portal.azure.com) pozycję **Wszystkie usługi**, przefiltruj w **usłudze Intune**, a następnie wybierz pozycję **Microsoft Intune**.
2. Wybierz **pozycję Zasady zgodności** \> **urządzeń** \> **Utwórz zasady**.
3. Wprowadź nazwę **i** **opis**.
4. Na **platformie** wybierz pozycję **Windows 10 lub nowsze.**
5. W **ustawieniach Kondycja** urządzenia **ustaw na** preferowanym poziomie wymaganie, aby poziom zagrożeń urządzenia był ustawiony na lub poniżej tego poziomu:

   - **Zabezpieczone**: ten poziom jest najbardziej bezpieczny. Urządzenie nie może mieć żadnych istniejących zagrożeń, a mimo to uzyskać dostęp do zasobów firmy. Jeśli zostaną znalezione jakiekolwiek zagrożenia, urządzenie zostanie ocenione jako niezgodne.
   - **Niska**: Urządzenie jest zgodne, jeśli istnieją tylko zagrożenia niskiego poziomu. Urządzenia o średnim lub wysokim poziomie zagrożeń są niezgodne.
   - **Średnia**: Urządzenie jest zgodne, jeśli zagrożenia na urządzeniu są niskie lub średnie. W przypadku wykrycia zagrożeń wysokiego poziomu urządzenie zostanie określone jako niezgodne.
   - **Wysoka**: ten poziom jest najmniej bezpieczny i pozwala na wszystkie poziomy zagrożeń. Oznacza to, że urządzenia o wysokim, średnim i niskim poziomie zagrożeń są uznawane za zgodne.

6. Wybierz **przycisk OK** i **pozycję Utwórz,** aby zapisać zmiany (i utworzyć zasady).

### <a name="step-4-assign-the-policy"></a>Krok 4. Przypisywanie zasad

1. W portalu [Azure wybierz](https://portal.azure.com) pozycję **Wszystkie usługi**, przefiltruj w **usłudze Intune**, a następnie wybierz pozycję **Microsoft Intune**.
2. Wybierz **pozycję Zasady zgodności** \> **>** i wybierz zasady zgodności programu Microsoft Defender dla punktu końcowego.
3. Wybierz **pozycję Zadania**.
4. Dołącz lub wyklucz grupy usługi Azure AD, aby przypisać im zasady.
5. Aby wdrożyć zasady w grupach, wybierz pozycję **Zapisz**. Urządzenia użytkowników kierowane przez zasady są oceniane pod celu zapewnienia zgodności.

### <a name="step-5-create-an-azure-ad-conditional-access-policy"></a>Krok 5. Tworzenie zasad dostępu warunkowego w usłudze Azure AD

1. W portalu [Azure otwórz](https://portal.azure.com) nowe **Azure Active Directory** \> **dostęp warunkowy**\>.
2. Wprowadź nazwę **zasad, a** następnie wybierz **pozycję Użytkownicy i grupy**. Użyj opcji Dołącz lub Wyklucz, aby dodać grupy do zasad, a następnie wybierz pozycję **Gotowe**.
3. Wybierz **pozycję Aplikacje w** chmurze, a następnie wybierz aplikacje do ochrony. Na przykład wybierz pozycję **Wybierz aplikacje**, a następnie wybierz pozycję Office 365 SharePoint **Online i** **Office 365 Exchange Online**. Wybierz **pozycję Gotowe** , aby zapisać zmiany.

4. Wybierz **pozycję Warunki** \> **Aplikacje klienckie** , aby zastosować zasady do aplikacji i przeglądarek. Na przykład wybierz pozycję **Tak**, a następnie **włącz aplikacje** **przeglądarki i urządzenia przenośne oraz klientów klasycznych**. Wybierz **pozycję Gotowe** , aby zapisać zmiany.

5. Wybierz pozycję **Ułań** , aby zastosować dostęp warunkowy w zależności od zgodności urządzenia. Na przykład wybierz pozycję **Ułań dostęp** \> **Wymagaj oznaczania urządzenia jako zgodnego**. Wybierz **pozycję Wybierz** , aby zapisać zmiany.

6. Wybierz **pozycję Włącz zasady**, a następnie **pozycję Utwórz,** aby zapisać zmiany.

Aby uzyskać więcej informacji, zobacz Wymuszanie zgodności dla programu [Microsoft Defender dla punktu końcowego za pomocą dostępu warunkowego w usłudze Intune](/intune/advanced-threat-protection).

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-belowfoldlink)
