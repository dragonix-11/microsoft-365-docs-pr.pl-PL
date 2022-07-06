---
title: Konfiguruj usługę IRM do korzystania z lokalnego serwera usług AD RMS
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
description: Dowiedz się, jak skonfigurować zarządzanie prawami do informacji (IRM) w Exchange Online do korzystania z serwera usługi Active Directory Rights Management (AD RMS).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5bd4a104d4cceedbdb82c1ff2baac0b547b74fbe
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637510"
---
# <a name="configure-irm-to-use-an-on-premises-ad-rms-server"></a>Konfiguruj usługę IRM do korzystania z lokalnego serwera usług AD RMS

Do użytku z wdrożeniami lokalnymi usługa Zarządzanie prawami do informacji (IRM) w Exchange Online korzysta z usług Active Directory Rights Management Services (AD RMS), technologii ochrony informacji w systemie Windows Server 2008 lub nowszym. Ochrona za pomocą usługi IRM jest stosowana do poczty e-mail przez zastosowanie szablonu zasad praw usług AD RMS do wiadomości e-mail. Prawa są dołączane do samego komunikatu, aby ochrona odbywała się w trybie online i offline oraz wewnątrz i na zewnątrz zapory organizacji.

W tym temacie pokazano, jak skonfigurować usługę IRM do korzystania z serwera usług AD RMS. Aby uzyskać informacje o korzystaniu z Szyfrowanie wiadomości w Microsoft Purview z usługami Azure Active Directory i Azure Rights Management, zobacz [Często zadawane pytania dotyczące szyfrowania komunikatów](./ome-faq.yml).

Aby dowiedzieć się więcej na temat usługi IRM w Exchange Online, zobacz [Zarządzanie prawami do informacji w Exchange Online](information-rights-management-in-exchange-online.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Szacowany czas wykonania tego zadania: 30 minut

- Do wykonania tych procedur musisz mieć przypisane uprawnienia. Aby zobaczyć, jakich uprawnień potrzebujesz, zobacz wpis "Zarządzanie prawami do informacji" w [temacie Zasady obsługi komunikatów i uprawnienia zgodności](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions) .

- Na serwerze usług AD RMS musi działać system Windows Server 2008 lub nowszy. Aby uzyskać szczegółowe informacje o sposobie wdrażania usług AD RMS, zobacz [Instalowanie klastra usług AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc726041(v=ws.11)).

- Aby uzyskać szczegółowe informacje na temat sposobu instalowania i konfigurowania Windows PowerShell i nawiązywania połączenia z usługą, zobacz [Nawiązywanie połączenia z Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby uzyskać informacje o skrótach klawiaturowych, które mogą mieć zastosowanie do procedur w tym temacie, zobacz [Skróty klawiaturowe centrum administracyjnego programu Exchange w Exchange Online](/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Masz problemy? Poproś o pomoc na forach programu Exchange. Odwiedź fora pod adresem [Exchange Server,Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=60612) lub [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).[](https://go.microsoft.com/fwlink/p/?linkId=267542)

## <a name="how-do-you-do-this"></a>Jak to zrobić?
<a name="sectionSection1"> </a>

### <a name="step-1-use-the-ad-rms-console-to-export-a-trusted-publishing-domain-tpd-from-an-ad-rms-server"></a>Krok 1. Eksportowanie zaufanej domeny publikowania (TPD) z serwera usług AD RMS przy użyciu konsoli usług AD RMS

Pierwszym krokiem jest wyeksportowanie zaufanej domeny publikowania (TPD) z lokalnego serwera usług AD RMS do pliku XML. TPD zawiera następujące ustawienia potrzebne do korzystania z funkcji usługi RMS:

- Certyfikat licencjodawcy serwera (SLC) używany do podpisywania i szyfrowania certyfikatów i licencji

- Adresy URL używane do licencjonowania i publikowania

- Szablony zasad praw usług AD RMS, które zostały utworzone przy użyciu określonego protokołu SLC dla tego TPD

Po zaimportowaniu dysku TPD jest on przechowywany i chroniony w Exchange Online.

1. Otwórz konsolę usług Active Directory Rights Management Services, a następnie rozwiń klaster usług AD RMS.

2. W drzewie konsoli rozwiń węzeł **Zasady zaufania**, a następnie kliknij pozycję **Zaufane domeny publikowania**.

3. W okienku wyników wybierz certyfikat dla domeny, którą chcesz wyeksportować.

4. W okienku **Akcje** kliknij pozycję **Eksportuj zaufaną domenę publikowania**.

5. W **polu Plik domeny publikowania** kliknij pozycję **Zapisz jako** , aby zapisać plik w określonej lokalizacji na komputerze lokalnym. Wpisz nazwę pliku, upewniając się, że określono rozszerzenie nazwy `.xml` pliku, a następnie kliknij przycisk **Zapisz**.

6. W polach **Hasło** i **Potwierdź hasło** wpisz silne hasło, które będzie używane do szyfrowania zaufanego pliku domeny publikowania. Musisz określić to hasło podczas importowania dysku TPD do organizacji poczty e-mail opartej na chmurze.

### <a name="step-2-use-the-exchange-management-shell-to-import-the-tpd-to-exchange-online"></a>Krok 2. Zaimportuj identyfikator TPD do Exchange Online za pomocą powłoki zarządzania programu Exchange

Po wyeksportowaniu dysku TPD do pliku XML należy go zaimportować, aby Exchange Online. Po zaimportowaniu TPD importowane są również szablony usług AD RMS organizacji. Po zaimportowaniu pierwszego dysku TPD staje się on domyślnym identyfikatorem TPD dla organizacji opartej na chmurze. W przypadku importowania innego TPD można użyć **przełącznika domyślnego** , aby ustawić domyślny identyfikator TPD, który jest dostępny dla użytkowników.

Aby zaimportować TPD, uruchom następujące polecenie w programie Exchange Online programu PowerShell:

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('<path to exported TPD file>')) -Name "<name of TPD>" -ExtranetLicensingUrl <URL> -IntranetLicensingUrl <URL>
```

Wartości parametrów _ExtranetLicensingUrl_ i _IntranetLicensingUrl_ można uzyskać w konsoli usług Active Directory Rights Management Services. Wybierz klaster usług AD RMS w drzewie konsoli. Adresy URL licencjonowania są wyświetlane w okienku wyników. Te adresy URL są używane przez klientów poczty e-mail, gdy zawartość musi zostać odszyfrowana, a Exchange Online musi określić, którego dysku TPD użyć.

Po uruchomieniu tego polecenia zostanie wyświetlony monit o podanie hasła. Wprowadź hasło określone podczas eksportowania dysku TPD z serwera usług AD RMS.

Na przykład następujące polecenie importuje identyfikator TPD o nazwie Wyeksportowany identyfikator TPD przy użyciu pliku XML wyeksportowanego z serwera usług AD RMS i zapisanego na pulpicie konta administratora. Parametr Name służy do określania nazwy TPD.

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('C:\Users\Administrator\Desktop\ExportTPD.xml')) -Name "Exported TPD" -ExtranetLicensingUrl https://corp.contoso.com/_wmcs/licensing -IntranetLicensingUrl https://rmsserver/_wmcs/licensing
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain).

#### <a name="how-do-you-know-that-you-successfully-imported-the-tpd"></a>Skąd wiesz, że pomyślnie zaimportowano TPD?

Aby sprawdzić, czy usługa TPD została pomyślnie zaimportowana, uruchom polecenie cmdlet **Get-RMSTrustedPublishingDomain**, aby pobrać identyfikatory TPD w organizacji Exchange Online. Aby uzyskać szczegółowe informacje, zobacz przykłady w [temacie Get-RMSTrustedPublishingDomain](/powershell/module/exchange/get-rmstrustedpublishingdomain).

### <a name="step-3-use-the-exchange-management-shell-to-distribute-an-ad-rms-rights-policy-template"></a>Krok 3. Dystrybuowanie szablonu zasad praw usług AD RMS przy użyciu powłoki zarządzania programu Exchange

Po zaimportowaniu dysku TPD należy upewnić się, że szablon zasad praw usług AD RMS jest rozproszony. Szablon rozproszony jest widoczny dla użytkowników Outlook w sieci Web (wcześniej znanych jako Outlook Web App), którzy mogą następnie stosować szablony do wiadomości e-mail.

Aby zwrócić listę wszystkich szablonów zawartych w domyślnym dysku TPD, uruchom następujące polecenie:

```powershell
Get-RMSTemplate -Type All | fl
```

Jeśli wartość parametru _Type_ to `Archived`, szablon nie jest widoczny dla użytkowników. Tylko szablony rozproszone w domyślnym dysku TPD są dostępne w Outlook w sieci Web.

Aby rozpowszechnić szablon, uruchom następujące polecenie:

```powershell
Set-RMSTemplate -Identity "<name of the template>" -Type Distributed
```

Na przykład następujące polecenie importuje szablon Poufne firmy.

```powershell
Set-RMSTemplate -Identity "Company Confidential" -Type Distributed
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate) i [Set-RMSTemplate](/powershell/module/exchange/set-rmstemplate).

#### <a name="the-do-not-forward-template"></a>Szablon Nie przesyłaj dalej

Podczas importowania domyślnego identyfikatora TPD z organizacji lokalnej do Exchange Online importowany jest jeden szablon zasad praw usług AD RMS o nazwie Nie przesyłaj **dalej**. Domyślnie ten szablon jest dystrybuowany podczas importowania domyślnego TPD. Nie można użyć polecenia cmdlet **Set-RMSTemplate** w celu zmodyfikowania szablonu **Nie przesyłaj dalej** .

Po zastosowaniu szablonu **Nie przesyłaj dalej** do wiadomości tylko adresaci adresaci w wiadomości mogą odczytać wiadomość. Ponadto adresaci nie mogą wykonywać następujących czynności:

- Przekaż wiadomość innej osobie.
- Skopiuj zawartość z wiadomości.
- Wydrukuj wiadomość.

> [!IMPORTANT]
> Szablon **Nie przesyłaj dalej** nie może uniemożliwić kopiowania informacji w wiadomości za pomocą programów przechwytywania ekranu innych firm, aparatów fotograficznych lub użytkowników ręcznie transkrypcji informacji

Możesz utworzyć dodatkowe szablony zasad praw usług AD RMS na serwerze usług AD RMS w organizacji lokalnej, aby spełnić wymagania dotyczące ochrony usługi IRM. Jeśli utworzysz dodatkowe szablony zasad praw usług AD RMS, musisz ponownie wyeksportować TPD z lokalnego serwera usług AD RMS i odświeżyć identyfikator TPD w organizacji poczty e-mail opartej na chmurze.

#### <a name="how-do-you-know-that-you-successfully-distributed-the-ad-rms-rights-policy-template"></a>Skąd wiesz, że pomyślnie rozproszono szablon zasad praw usług AD RMS?

Aby sprawdzić, czy pomyślnie rozproszono szablon zasad praw usług AD RMS, uruchom polecenie cmdlet **Get-RMSTemplate** , aby sprawdzić właściwości szablonu. Aby uzyskać szczegółowe informacje, zobacz przykłady w [temacie Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate).

### <a name="step-4-use-the-exchange-management-shell-to-enable-irm"></a>Krok 4. Włączanie usługi IRM za pomocą powłoki zarządzania programu Exchange

Po zaimportowaniu dysku TPD i dystrybucji szablonu zasad praw usług AD RMS uruchom następujące polecenie, aby włączyć usługę IRM dla organizacji poczty e-mail opartej na chmurze.

```powershell
Set-IRMConfiguration -InternalLicensingEnabled $true
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration).

#### <a name="how-do-you-know-that-you-successfully-enabled-irm"></a>Skąd wiesz, że pomyślnie włączono usługę IRM?

Aby sprawdzić, czy usługa IRM została pomyślnie włączona, uruchom polecenie cmdlet [Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration), aby sprawdzić konfigurację usługi IRM w organizacji Exchange Online.

## <a name="how-do-you-know-this-task-worked"></a>Skąd wiesz, że to zadanie zadziałało?
<a name="sectionSection2"> </a>

Aby sprawdzić, czy pomyślnie zaimportowano usługę TPD i włączono usługę IRM, wykonaj następujące czynności:

- Użyj polecenia cmdlet **Test-IRMConfiguration** , aby przetestować funkcjonalność usługi IRM. Aby uzyskać szczegółowe informacje, zobacz "Przykład 1" w [temacie Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

- Utwórz nowy komunikat w Outlook w sieci Web i IRM-protect, wybierając opcję **Ustaw uprawnienia** z menu rozszerzonego (![Ikona więcej opcji).](../media/ITPro-EAC-MoreOptionsIcon.gif)
