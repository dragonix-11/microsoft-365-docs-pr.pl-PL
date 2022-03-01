---
title: Konfigurowanie usługi IRM do używania lokalnego serwera USŁUG AD RMS
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 3ecde857-4b7c-451d-b4aa-9eeffc8a8c61
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak skonfigurować usługę Zarządzanie prawami do informacji (IRM) w usłudze Exchange Online na korzystanie z serwera usługi zarządzania prawami dostępu w usłudze Active Directory (AD RMS).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f87992fc9be676b9485d6ec7a7b7ff1f3a4d39d9
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009683"
---
# <a name="configure-irm-to-use-an-on-premises-ad-rms-server"></a>Konfigurowanie usługi IRM do używania lokalnego serwera USŁUG AD RMS

Do użytku we wdrożeniach lokalnych zarządzanie prawami do informacji (IRM) w programie Exchange Online korzysta z usługi Usługi Active Directory Rights Management (AD RMS), technologii ochrony informacji w programie Windows Server 2008 i nowszych. Ochrona usługi IRM jest stosowana do wiadomości e-mail przez zastosowanie szablonu zasad praw usług AD RMS do wiadomości e-mail. Do wiadomości są dołączane prawa, dzięki czemu ochrona jest chroniony w trybie online i offline oraz wewnątrz i poza zaporą organizacji.

W tym temacie pokazano, jak skonfigurować usługę IRM do korzystania z serwera usług AD RMS. Aby uzyskać informacje na temat korzystania z nowych możliwości Szyfrowanie wiadomości usługi Office 365 usługami Azure Active Directory i Azure Rights Management, zobacz często zadawane [Szyfrowanie wiadomości usługi Office 365 pytania](./ome-faq.yml).

Aby dowiedzieć się więcej na temat usługi IRM w u Exchange Online, zobacz [Zarządzanie prawami do informacji w programie Exchange Online](information-rights-management-in-exchange-online.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Szacowany czas wykonania tego zadania: 30 minut

- Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby sprawdzić, jakich uprawnień potrzebujesz, zobacz wpis "Zarządzanie prawami do informacji" w temacie Uprawnienia dotyczące zasad obsługi wiadomości [i zgodności](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions) .

- Serwer AD RMS musi mieć uruchomiony Windows Server 2008 lub nowszy. Aby uzyskać szczegółowe informacje na temat wdrażania usług AD RMS, zobacz [Instalowanie klastra usług AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc726041(v=ws.11)).

- Aby uzyskać szczegółowe informacje na temat instalowania i konfigurowania Windows PowerShell łączenia się z usługą, zobacz Połączenie do Exchange Online [używania zdalnej obsługi programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby uzyskać informacje na temat skrótów klawiaturowych, które mogą dotyczyć procedur zobacz Skróty klawiaturowe w centrum administracyjnym programu [Exchange w programie Exchange Online](/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Masz problemy? Poproś o pomoc na forach Exchange. Odwiedź fora w [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) lub [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## <a name="how-do-you-do-this"></a>Jak to zrobić?
<a name="sectionSection1"> </a>

### <a name="step-1-use-the-ad-rms-console-to-export-a-trusted-publishing-domain-tpd-from-an-ad-rms-server"></a>Krok 1. Używanie konsoli AD RMS do eksportowania zaufanej domeny publikowania (TPD) z serwera USŁUG AD RMS

Pierwszym krokiem jest wyeksportowanie zaufanej domeny publikowania (TPD) z lokalnego serwera USŁUG AD RMS do pliku XML. TpD zawiera następujące ustawienia wymagane do korzystania z funkcji RMS:

- Certyfikat licencjodawcy serwera (SLC) używany do podpisywania i szyfrowania certyfikatów i licencji

- Adresy URL używane do licencjonowania i publikowania

- Szablony zasad praw usług AD RMS, które zostały utworzone przy użyciu określonego szablonu SLC dla danej usługi TPD

Po zaimportowaniu pliku TPD jest on przechowywany i chroniony w Exchange Online.

1. Otwórz konsolę Usługi Active Directory Rights Management, a następnie rozwiń klaster usług AD RMS.

2. W drzewie konsoli rozwiń pozycję **Zasady zaufania**, a następnie kliknij pozycję **Zaufane domeny publikowania**.

3. W okienku wyników wybierz certyfikat dla domeny, którą chcesz wyeksportować.

4. W **okienku Akcje** kliknij pozycję **Eksportuj zaufaną domenę publikowania**.

5. W **polu Plik domeny publikowania** kliknij pozycję **Zapisz jako** , aby zapisać plik w określonej lokalizacji na komputerze lokalnym. Wpisz nazwę pliku, upewniąc się, że określono `.xml` rozszerzenie nazwy pliku, a następnie kliknij przycisk **Zapisz**.

6. W **polach Hasło** i **Potwierdź** hasło wpisz silne hasło, które będzie używane do szyfrowania zaufanego pliku domeny publikowania. To hasło należy określić podczas importowania pliku TPD do chmurowej organizacji poczty e-mail.

### <a name="step-2-use-the-exchange-management-shell-to-import-the-tpd-to-exchange-online"></a>Krok 2. Zaimportuj usługę TPD do Exchange przy użyciu powłoki zarządzania danymi Exchange Online

Po wyeksportowaniu pliku TPD do pliku XML należy go zaimportować w celu Exchange Online. W przypadku importowania TPD są również importowane szablony usług AD RMS w organizacji. Po zaimportowaniu pierwszej aplikacji TPD staje się ona domyślną bazą danych TPD dla organizacji opartej na chmurze. Jeśli importujesz inną usługę TPD, możesz użyć przełącznika **Domyślne** , aby ustawić ją jako domyślną usługę TPD dostępną dla użytkowników.

Aby zaimportować dane TPD, uruchom następujące polecenie w programie Windows PowerShell:

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('<path to exported TPD file>')) -Name "<name of TPD>" -ExtranetLicensingUrl <URL> -IntranetLicensingUrl <URL>
```

Możesz uzyskać wartości parametrów _ExtranetLicensingUrl_ i _IntranetLicensingUrl_ na konsoli Usługi Active Directory Rights Management sieci. Wybierz klaster usług AD RMS w drzewie konsoli. Adresy URL licencji są wyświetlane w okienku wyników. Te adresy URL są używane przez klientów poczty e-mail, gdy zawartość musi zostać odszyfrowana i gdy Exchange Online określić, której protokołu TPD użyć.

Po uruchomieniu tego polecenia zostanie wyświetlony monit o hasło. Wprowadź hasło określone podczas eksportowania danych TPD z serwera USŁUG AD RMS.

Na przykład następujące polecenie importuje plik TPD o nazwie Exported TPD przy użyciu pliku XML wyeksportowanego z serwera USŁUG AD RMS i zapisany na pulpicie konta administratora. Parametr Name służy do określania nazwy dla parametru TPD.

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('C:\Users\Administrator\Desktop\ExportTPD.xml')) -Name "Exported TPD" -ExtranetLicensingUrl https://corp.contoso.com/_wmcs/licensing -IntranetLicensingUrl https://rmsserver/_wmcs/licensing
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain).

#### <a name="how-do-you-know-that-you-successfully-imported-the-tpd"></a>Skąd wiadomo, że dane TPD zostały pomyślnie zaimportowane?

Aby sprawdzić, czy dane tpd zostały pomyślnie zaimportowane, uruchom polecenie cmdlet **Get-RMSTrustedPublishingDomain** w celu pobrania identyfikatorów TPD w Exchange Online organizacji. Aby uzyskać szczegółowe informacje, zobacz przykłady w [temacie Get-RMSTrustedPublishingDomain](/powershell/module/exchange/get-rmstrustedpublishingdomain).

### <a name="step-3-use-the-exchange-management-shell-to-distribute-an-ad-rms-rights-policy-template"></a>Krok 3. Używanie powłoki zarządzania Exchange do rozpowszechniania szablonu zasad praw usług AD RMS

Po zaimportowaniu pliku TPD należy się upewnić, że jest rozpowszechniany szablon zasad praw usług AD RMS. Szablon rozłożony jest widoczny dla Outlook w sieci Web użytkowników (dawniej nazywanych Outlook Web App), którzy następnie mogą stosować szablony do wiadomości e-mail.

Aby zwrócić listę wszystkich szablonów zawartych w domyślnej aplikacji TPD, uruchom następujące polecenie:

```powershell
Get-RMSTemplate -Type All | fl
```

Jeśli parametr _Type ma wartość_ `Archived`, szablon nie jest widoczny dla użytkowników. W programach Outlook w sieci Web są dostępne tylko szablony rozpowszechniane w domyślnej Outlook w sieci Web.

Aby rozpowszechnić szablon, uruchom następujące polecenie:

```powershell
Set-RMSTemplate -Identity "<name of the template>" -Type Distributed
```

Na przykład następujące polecenie importuje szablon Poufne informacje firmowe.

```powershell
Set-RMSTemplate -Identity "Company Confidential" -Type Distributed
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate) i [Set-RMSTemplate](/powershell/module/exchange/set-rmstemplate).

#### <a name="the-do-not-forward-template"></a>Szablon Nie przesyłaj dalej

Po zaimportowaniu domyślnej usługi TPD z organizacji lokalnej do programu Exchange Online jest importowany jeden szablon zasad praw usług AD RMS o nazwie **Nie** przesyłaj dalej. Domyślnie ten szablon jest rozpowszechniany podczas importowania domyślnej wartości TPD. Za pomocą polecenia cmdlet **Set-RMSTemplate** nie można modyfikować szablonu **Nie przesyłaj dalej** .

Po **zastosowaniu szablonu Nie przesyłaj** dalej do wiadomości tylko adresaci adresaci wiadomości mogą ją odczytać. Ponadto adresaci nie mogą wykonać następujących czynności:

- Przesyłanie wiadomości dalej do innej osoby.
- Skopiować zawartość z wiadomości.
- Wydrukuj wiadomość.

> [!IMPORTANT]
> Szablon **Nie przesyłaj dalej** nie może zapobiec kopiowaniu informacji w wiadomości za pomocą programów do przechwytywania zawartości ekranu innych firm, aparatów ani użytkowników, którzy ręcznie je transskrybują

Na serwerze usług AD RMS w organizacji lokalnej możesz utworzyć dodatkowe szablony zasad praw usług AD RMS, aby spełnić wymagania dotyczące ochrony usługi IRM. Jeśli utworzysz dodatkowe szablony zasad praw usług AD RMS, musisz ponownie wyeksportować usługę TPD z lokalnego serwera usług AD RMS i odświeżyć tpd w opartej na chmurze organizacji poczty e-mail.

#### <a name="how-do-you-know-that-you-successfully-distributed-the-ad-rms-rights-policy-template"></a>Skąd wiadomo, że szablon zasad praw usług AD RMS został pomyślnie rozpowszechniony?

Aby sprawdzić, czy pomyślnie rozpowszechniano i czy szablon zasad praw usług AD RMS został pomyślnie rozłożony, uruchom polecenie cmdlet **Get-RMSTemplate** w celu sprawdzenia właściwości szablonu. Aby uzyskać szczegółowe informacje, zobacz przykłady w te [dotyczące usługi Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate).

### <a name="step-4-use-the-exchange-management-shell-to-enable-irm"></a>Krok 4. Włączanie usługi IRM Exchange powłoki zarządzania danymi

Po zaimportowaniu pliku TPD i rozpowszechnieniu szablonu zasad praw usług AD RMS uruchom następujące polecenie, aby włączyć usługę IRM dla chmurowej organizacji poczty e-mail.

```powershell
Set-IRMConfiguration -InternalLicensingEnabled $true
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration).

#### <a name="how-do-you-know-that-you-successfully-enabled-irm"></a>Skąd wiadomo, że funkcja IRM została pomyślnie włączona?

Aby sprawdzić, czy funkcja IRM została pomyślnie włączona, uruchom polecenie cmdlet [Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration) w celu sprawdzenia konfiguracji usługi IRM w Exchange Online organizacji.

## <a name="how-do-you-know-this-task-worked"></a>Skąd wiadomo, że to zadanie zadziałało?
<a name="sectionSection2"> </a>

Aby sprawdzić, czy funkcja TPD została pomyślnie zaimportowana i włączona funkcja IRM, wykonaj następujące czynności:

- Użyj polecenia **cmdlet Test-IRMConfiguration** , aby przetestować funkcję usługi IRM. Aby uzyskać szczegółowe informacje, zobacz "Przykład 1" w [teście -IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

- Zredagotuj nową wiadomość w Outlook w sieci Web i chroń ją za pomocą usługi  IRM, wybierając pozycję Ustaw uprawnienia z menu rozszerzonego (![ikona Więcej opcji).](../media/ITPro-EAC-MoreOptionsIcon.gif)
