---
title: Sejf dokumenty w programie Ochrona usługi Office 365 w usłudze Microsoft Defender
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
description: Dowiedz się Sejf o dokumentach w Microsoft 365 E5/A5 lub zabezpieczeniach Microsoft 365 E5/A5.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ab5e35954cac20a18e34f418b5b9fcdc7f2fd007
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466350"
---
# <a name="safe-documents-in-microsoft-365-e5a5"></a>Sejf dokumentów w Microsoft 365 E5/A5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Sejf Dokumenty to funkcja premium, która korzysta z zaplecza w chmurze usługi Ochrona punktu końcowego w usłudze Microsoft Defender do skanowania otwartych dokumentów programu [Office](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) w widoku chronionym lub funkcji [Application Guard](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46) dla systemu Office.[](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653)

Użytkownicy nie potrzebują programu Defender for Endpoint zainstalowanego na swoich urządzeniach lokalnych, aby uzyskać Sejf dokumenty. Użytkownicy mogą Sejf dokumenty, jeśli są spełnione wszystkie poniższe wymagania:

- Sejf dokumenty są włączone w organizacji zgodnie z opisem w tym artykule.
- Licencje z wymaganego planu licencjonowania są przypisywane do użytkowników. Sejf Dokumenty są kontrolowane przez plan usługi **Office 365 SafeDocs** (lub **SAFEDOCS** lub **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**). Ten plan usługi jest dostępny w następujących planach licencjonowania (nazywanych również planami licencyjnym, planami Microsoft 365 i produktami):
  - Microsoft 365 A5 dla nauczycieli lub wykładowców
  - Microsoft 365 A5 dla uczniów
  - Microsoft 365 E5
  - Zabezpieczenia platformy Microsoft 365 E5

  Sejf dokumenty nie są zawarte w Ochrona usługi Office 365 w usłudze Microsoft Defender licencjonowania.

  Aby uzyskać więcej informacji, zobacz [Nazwy produktów i identyfikatory planu usług na temat licencjonowania](/azure/active-directory/enterprise-users/licensing-service-plan-reference).

- Używali oni programu Aplikacje Microsoft 365 dla przedsiębiorstw (dawniej znanego jako Office 365 ProPlus) w wersji 2004 lub nowszej.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby wykonać procedury Exchange Online  z tego artykułu, musisz mieć odpowiednie uprawnienia:
  - Aby skonfigurować Sejf dokumenty, musisz być członkiem grup ról Zarządzanie organizacją lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu Sejf dokumentów, musisz być członkiem grup ról Czytnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji Centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w aplikacji  Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  >
  > - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

### <a name="how-does-microsoft-handle-your-data"></a>Jak firma Microsoft obsługuje Twoje dane?

Aby zapewnić Ci ochronę, usługa Sejf wysyła pliki [do Ochrona punktu końcowego w usłudze Microsoft Defender danych](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) w celu analizy. Szczegóły dotyczące sposobu Ochrona punktu końcowego w usłudze Microsoft Defender danych można znaleźć tutaj: Ochrona punktu końcowego w usłudze Microsoft Defender [przechowywania danych i prywatności](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

Pliki wysłane przez Sejf Dokumenty nie są przechowywane w uchcie defender dla punktu końcowego poza czas potrzebny na analizę (zazwyczaj mniej niż 24 godziny).

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>Konfigurowanie dokumentów Microsoft 365 Defender za pomocą portalu Sejf dokumentów

1.  W portalu Microsoft 365 Defender  \> <https://security.microsoft.com>przejdź do sekcji Zasady & e-mail & **zasad** \> \> zagrożeń Sejf **załączników** **w** sekcji Zasady. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

2. Na stronie **Sejf załączników** kliknij pozycję **Ustawienia globalne**.

3. W **wyświetlonym wysuwanych** ustawieniach globalnych skonfiguruj następujące ustawienia:
   - **Włącz Sejf dokumenty dla Office klientów**: Przesuń przełącznik w prawo, aby włączyć funkcję: ![Włącz.](../../media/scc-toggle-on.png)
   - **Zezwalaj** użytkownikom na klikanie w widoku chronionym, nawet jeśli program Sejf Dokumenty zidentyfikował plik jako złośliwy: zalecamy pozostawienie tej opcji wyłączonej (przełącznik pozostaw przełącznik w lewo: ![](../../media/scc-toggle-off.png)Wyłącz).

   Po zakończeniu kliknij przycisk **Zapisz**.

   :::image type="content" source="../../media/safe-docs-global-settings.png" alt-text="Ustawienia Sejf dokumentów po wybraniu ustawień globalnych na Sejf Załączniki wiadomości" lightbox="../../media/safe-docs-global-settings.png":::

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Konfigurowanie Exchange Online Dokumentów za pomocą programu PowerShell Sejf Dokumentów

Jeśli wolisz, aby program PowerShell Sejf Dokumenty, użyj następującej składni w programie Exchange Online PowerShell:

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- Parametr _EnableSafeDocs_ włącza lub wyłącza Sejf dokumenty dla całej organizacji.
- Parametr _AllowSafeDocsOpen_ umożliwia użytkownikom opuszczenie widoku chronionego (czyli otwieranie dokumentu) w przypadku zidentyfikowania dokumentu jako złośliwego.

W tym przykładzie Sejf dokumenty w całej organizacji i zapobiega otwieraniu przez użytkowników dokumentów, które zostały zidentyfikowane jako złośliwe w widoku chronionym.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>Konfigurowanie indywidualnego dostępu do Sejf dokumentów

Jeśli chcesz selektywnie zezwolić na dostęp do funkcji Dokumenty Sejf lub zablokować ten dostęp, wykonaj następujące czynności:

1. Włącz dokumenty Sejf w portalu usługi Microsoft 365 Defender lub w Exchange Online PowerShell w sposób opisany wcześniej w tym artykule.
2. Za pomocą programu PowerShell usługi Azure AD wyłącz funkcje Sejf dla określonych użytkowników zgodnie z opisem w tesłudze Microsoft 365 usługi dla określonych użytkowników w ramach [określonego planu licencjonowania](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan).

  Nazwa planu usługi do wyłączenia w programie PowerShell to **SAFEDOCS**.

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Wyświetlanie Microsoft 365 i usług za pomocą programu PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [Wyświetlanie Microsoft 365 licencji konta i usługi za pomocą programu PowerShell](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [Nazwy produktów i identyfikatory planu usług na licencjonowanie](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>Włączanie usługi Ochrona punktu końcowego w usłudze Microsoft Defender w celu umożliwienia inspekcji

Aby włączyć funkcje inspekcji, na urządzeniu lokalnym musi być Ochrona punktu końcowego w usłudze Microsoft Defender zainstalowany. Aby wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender, musisz przejść przez poszczególne fazy wdrażania. Po dojechieniu możesz skonfigurować funkcje inspekcji w portalu Microsoft 365 Defender sieci.

Aby dowiedzieć się więcej, [zobacz Dołączanie do Ochrona punktu końcowego w usłudze Microsoft Defender usługi](/microsoft-365/security/defender-endpoint/onboarding). Jeśli potrzebujesz dodatkowej pomocy, zobacz Rozwiązywanie [Ochrona punktu końcowego w usłudze Microsoft Defender dotyczących dołączania](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding).

### <a name="how-do-i-know-this-worked"></a>Jak mogę, że to zadziałało?

Aby sprawdzić, czy dokumenty są włączone i skonfigurowane Sejf, wykonaj dowolną z następujących czynności:

- W portalu Microsoft 365 Defender przejdź do sekcji Zasady współpracy z pocztą e-mail **&** \> **&** \>  \> Zasady zagrożeń **Sejf** Załączniki w sekcji **Zasady Ustawienia** \> **globalne** **i sprawdź ustawienia Włącz dokumenty Sejf dla Office klientów i Zezwalaj użytkownikom na klikanie w widoku chronionym, nawet Sejf dokumenty zidentyfikuje plik jako złośliwe** ustawienia.

- Uruchom następujące polecenie w programie Exchange Online PowerShell i sprawdź wartości właściwości:

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Poniższe pliki są dostępne do testowania w Sejf Dokumenty. Te pliki są podobne do plików EICAR.TXT do testowania złośliwego oprogramowania i oprogramowania antywirusowego. Pliki nie są niebezpieczne, ale powodują Sejf ochrony dokumentów.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
