---
title: Sejf dokumenty w Ochrona usługi Office 365 w usłudze Microsoft Defender
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: kshi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Dowiedz się więcej o dokumentach Sejf w zabezpieczeniach Microsoft 365 E5/A5 lub Microsoft 365 E5/A5.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3fa1c7e07c1e1cd117ee20f4712dbbadad3c2b5c
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174136"
---
# <a name="safe-documents-in-microsoft-365-e5a5"></a>Sejf dokumenty w Microsoft 365 E5/A5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Sejf Documents to funkcja premium, która używa zaplecza chmury [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) do skanowania otwartych Office dokumentów w [widoku chronionym](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) lub [funkcji Application Guard w celu Office](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46).

Użytkownicy nie potrzebują programu Defender for Endpoint zainstalowanego na swoich urządzeniach lokalnych, aby uzyskać ochronę dokumentów Sejf. Użytkownicy uzyskują ochronę dokumentów Sejf, jeśli spełnione są wszystkie następujące wymagania:

- Sejf Documents jest włączona w organizacji zgodnie z opisem w tym artykule.
- Licencje z wymaganego planu licencjonowania są przypisywane do użytkowników. Sejf Documents jest kontrolowana przez **plan usługi Office 365 SafeDocs** (lub **SAFEDOCS** lub **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**) (znany również jako usługa). Ten plan usługi jest dostępny w następujących planach licencjonowania (nazywanych również planami licencji, planami Microsoft 365 lub produktami):
  - Microsoft 365 A5 dla wykładowców
  - Microsoft 365 A5 for Students
  - Zabezpieczenia platformy Microsoft 365 E5

  Sejf Documents nie jest uwzględniona w planach licencjonowania Ochrona usługi Office 365 w usłudze Microsoft Defender.

  Aby uzyskać więcej informacji, zobacz [Product names and service plan identifiers for licensing (Nazwy produktów i identyfikatory planu usługi na potrzeby licencjonowania).](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

- Używają Aplikacje Microsoft 365 dla przedsiębiorstw (wcześniej znanej jako Office 365 ProPlus) w wersji 2004 lub nowszej.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Przed wykonaniem procedur w tym artykule potrzebne są uprawnienia w **Exchange Online**:
  - Aby skonfigurować ustawienia Sejf Dokumenty, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń**.
  - Aby uzyskać dostęp tylko do odczytu do ustawień dokumentów Sejf, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń**.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  >
  > - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

### <a name="how-does-microsoft-handle-your-data"></a>Jak firma Microsoft obsługuje Twoje dane?

Aby zapewnić ochronę, Sejf Documents wysyła pliki do [chmury Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) w celu analizy. Szczegółowe informacje na temat sposobu obsługi danych przez Ochrona punktu końcowego w usłudze Microsoft Defender można znaleźć tutaj: [Ochrona punktu końcowego w usłudze Microsoft Defender magazyn danych i prywatność](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

Pliki wysyłane przez Sejf Documents nie są przechowywane w usłudze Defender for Endpoint dłużej niż czas potrzebny do analizy (zazwyczaj mniej niż 24 godziny).

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>Konfigurowanie dokumentów Sejf przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& reguły** \> **zagrożeń** \> **Sejf załączniki** w sekcji Zasady. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **Sejf Załączniki** kliknij pozycję **Ustawienia globalne**.

3. W wyświetlonym menu **Ustawienia globalne** skonfiguruj następujące ustawienia:
   - **Włącz Sejf Documents for Office clients**: przenieś przełącznik w prawo, aby włączyć funkcję: ![Włącz.](../../media/scc-toggle-on.png)
   - **Zezwalaj użytkownikom na klikanie widoku chronionego, nawet jeśli Sejf Dokumenty zidentyfikowały plik jako złośliwy**: zalecamy pozostawienie tej opcji wyłączonej (pozostaw przełącznik po lewej stronie: ![Wyłącz).](../../media/scc-toggle-off.png)

   Po zakończeniu kliknij przycisk **Zapisz**.

   :::image type="content" source="../../media/safe-docs-global-settings.png" alt-text="Ustawienia Sejf Dokumenty po wybraniu ustawień globalnych na stronie załączników Sejf" lightbox="../../media/safe-docs-global-settings.png":::

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Konfigurowanie dokumentów Sejf przy użyciu programu Exchange Online PowerShell

Jeśli wolisz, aby użytkownik programu PowerShell skonfigurował Sejf Documents, użyj następującej składni w programie Exchange Online programu PowerShell:

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- Parametr _EnableSafeDocs_ włącza lub wyłącza Sejf Documents dla całej organizacji.
- Parametr _AllowSafeDocsOpen_ zezwala użytkownikom na opuszczanie widoku chronionego (czyli otwierania dokumentu), jeśli dokument został zidentyfikowany jako złośliwy.

Ten przykład umożliwia Sejf dokumentów dla całej organizacji i uniemożliwia użytkownikom otwieranie dokumentów, które zostały zidentyfikowane jako złośliwe w widoku chronionym.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>Konfigurowanie indywidualnego dostępu do dokumentów Sejf

Jeśli chcesz selektywnie zezwalać na dostęp do funkcji Sejf Documents lub blokować go, wykonaj następujące kroki:

1. Włącz Sejf dokumenty w portalu Microsoft 365 Defender lub Exchange Online programu PowerShell zgodnie z wcześniejszym opisem w tym artykule.
2. Użyj Azure AD programu PowerShell, aby wyłączyć dokumenty Sejf dla określonych użytkowników zgodnie z [opisem w temacie Wyłączanie określonych usług Microsoft 365 dla określonych użytkowników dla określonego planu licencjonowania](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan).

  Nazwa planu usługi do wyłączenia w programie PowerShell to **SAFEDOCS**.

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Wyświetlanie licencji i usług Microsoft 365 przy użyciu programu PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [Wyświetlanie licencji Microsoft 365 konta i szczegółów usługi za pomocą programu PowerShell](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [Nazwy produktów i identyfikatory planów usług na potrzeby licencjonowania](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>Dołączanie do usługi Ochrona punktu końcowego w usłudze Microsoft Defender w celu włączenia możliwości inspekcji

Aby włączyć możliwości inspekcji, urządzenie lokalne musi mieć zainstalowane Ochrona punktu końcowego w usłudze Microsoft Defender. Aby wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender, należy przejść przez różne fazy wdrażania. Po dołączeniu można skonfigurować możliwości inspekcji w portalu Microsoft 365 Defender.

Aby dowiedzieć się więcej, zobacz [Dołączanie do usługi Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/onboarding). Jeśli potrzebujesz dodatkowej pomocy, zapoznaj się [z tematem Rozwiązywanie problemów z dołączaniem Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding).

### <a name="how-do-i-know-this-worked"></a>Jak mogę wiedzieć, że to zadziałało?

Aby sprawdzić, czy włączono i skonfigurowano Sejf Documents, wykonaj dowolne z następujących kroków:

- W portalu Microsoft 365 Defender przejdź  do obszaru Zasady współpracy \> **& poczty e-mail** **& zasady dotyczące zagrożeń** \>  \> **Sejf Załączniki** w sekcji \> Zasady **Ustawienia globalne** i sprawdź **włączanie Sejf dokumentów dla klientów Office** i **Zezwalaj użytkownikom na klikanie widoku chronionego, nawet jeśli Sejf Documents identyfikuje plik jako złośliwe** ustawienia.

- Uruchom następujące polecenie w programie Exchange Online programu PowerShell i sprawdź wartości właściwości:

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Następujące pliki są dostępne do testowania ochrony dokumentów Sejf. Pliki te są podobne do pliku EICAR.TXT do testowania rozwiązań chroniących przed złośliwym oprogramowaniem i antywirusowymi. Pliki nie są szkodliwe, ale będą wyzwalać ochronę dokumentów Sejf.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
