---
title: Uaktualnianie list dystrybucyjnych do Microsoft 365 grup w Outlook
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 787d7a75-e201-46f3-a242-f698162ff09f
description: Dowiedz się, jak uaktualnić jedną lub wiele list dystrybucyjnych do grup Microsoft 365 w programie Outlook oraz jak używać programu PowerShell do jednoczesnego uaktualniania kilku list dystrybucyjnych.
ms.openlocfilehash: 7a6e0eff49958b99df9ca59702b814b364aefb46
ms.sourcegitcommit: 27eb93a7d46bcbb9c948a50b0a8481ffd3832ca0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/28/2021
ms.locfileid: "63028014"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Uaktualnianie list dystrybucyjnych do Microsoft 365 grup w Outlook

Możesz uaktualnić listy dystrybucyjne, aby Microsoft 365 grupy w Outlook. Jest to doskonały sposób na przysłanie list dystrybucyjnych Twojej organizacji wszystkich funkcji i funkcji grup Microsoft 365 grupy. [Dlaczego należy uaktualnić listy dystrybucyjne do grup w programie Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

Możesz uaktualnić adresy DLs jeden na raz lub kilka jednocześnie.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Uaktualnianie jednej lub wielu grup list dystrybucyjnych Microsoft 365 grup w Outlook

Aby uaktualnić grupę listy dystrybucyjnej, Exchange administratorem globalnym lub administratorem globalnym. Aby można było Microsoft 365 grupy dystrybucyjne, grupa listy dystrybucyjnej musi mieć właściciela ze skrzynką pocztową.

### <a name="use-the-new-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Uaktualnianie jednej lub wielu grup list dystrybucyjnych do grup Microsoft 365 w programie Outlook

1. Przejdź do nowego centrum administracyjnego Exchange grupy > **adresatów**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>

2. Wybierz grupę listy dystrybucyjnej (nazywaną również grupą dystrybucyjną **), którą** chcesz uaktualnić do Microsoft 365 na **stronie Grupy**.

3. Wybierz **grupę dystrybucyjną Uaktualnij** na pasku narzędzi.

4. W oknie **dialogowym Czy chcesz uaktualnić?** kliknij pozycję **Uaktualnij**. Proces rozpoczyna się natychmiast. Proces ten może potrwać kilka minut lub godzin w zależności od rozmiaru i liczby uaktualnianych grup list dystrybucyjnych.

> [!NOTE]
> Transparent u góry informuje o uaktualnieniu, na przykład o uaktualnieniu grup *dystrybucyjnych. Odzwierciedlenia tych zmian zajmie 5 minut. Filtruj według Microsoft 365, aby wyświetlić uaktualnione grupy dystrybucyjne*.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Uaktualnianie jednej lub wielu grup list dystrybucyjnych do grup Microsoft 365 w programie Outlook

1. Przejdź do centrum administracyjnego Exchange grupy > **adresatów**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a><br/>Zostanie wyświetlony komunikat informujący o tym, że masz listy dystrybucyjne (nazywane również grupami dystrybucyjnmi **), które** można uaktualnić do Microsoft 365 grup.<br/> ![Wybierz przycisk Wprowadzenie.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. Wybierz co najmniej jedną listę dystrybucyjną (nazywaną również grupą **dystrybucyjną**) na **stronie grup** .<br/>![Wybierz grupę dystrybucyjną.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. Wybierz ikonę uaktualniania.<br/>![Ikona Uaktualnij do Microsoft 365 grupy.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. W oknie dialogowym informacji wybierz pozycję **Tak** , aby potwierdzić uaktualnienie. Proces rozpoczyna się natychmiast. W zależności od rozmiaru i liczby uaktualnianych adresów DLs ten proces może potrwać kilka minut lub godzin.<br/>Jeśli nie można uaktualnić listy dystrybucyjnej, zostanie wyświetlone okno dialogowe z informacją o tym. Zobacz [Jakich list dystrybucyjnych nie można uaktualnić?](#which-distribution-lists-cant-be-upgraded).

1. Jeśli uaktualniasz wiele list dystrybucyjnych, filtruj listy rozwijane, które zostały uaktualnione, za pomocą listy rozwijanej. Jeśli lista nie jest ukończona, poczekaj chwilę dłużej, a następnie wybierz pozycję  Odśwież, aby zobaczyć, co zostało pomyślnie uaktualnione.<br/>Nie ma żadnych informacji o ukończeniu procesu uaktualniania dla wszystkich wybranych adresów DLs. Możesz to sprawdzić, patrząc na listę w obszarze Dostępne do **uaktualnienia lub** **Uaktualnione adresy DLs**.

1. Jeśli wybrano bibliotekę dystrybucyjną do uaktualnienia, ale nadal jest ona dostępna na stronie jako Dostępna do uaktualnienia, uaktualnianie nie powiodło się. Zobacz [Co zrobić, jeśli uaktualnienie nie działa](#what-to-do-if-the-upgrade-doesnt-work).

> [!NOTE]
> Jeśli chcesz otrzymywać podsumowanie wiadomości e-mail od grup, może się okazać, że czasami będą one oferować Ci uaktualnienie wszelkich kwalifikujących się list dystrybucyjnych, których jesteś właścicielem. Aby [uzyskać więcej informacji na temat podsumowanie wiadomości e-mail, zobacz Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22) konwersacji grupowej w grupie.

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Co zrobić, jeśli uaktualnienie nie działa

Listy dystrybucyjne, których nie można uaktualnić, pozostaną niezmienione.

Jeśli nie można uaktualnić **jednej** lub większej liczby uprawnionych list dystrybucyjnych, 

1. Użyj [tego](https://aka.ms/DLToM365Group) skryptu, aby skanować w poszukiwaniu możliwych problemów, które mogą uniemożliwiać uaktualnienie listy dystrybucyjnej do grupy Microsoft 365, rozwiązać wszelkie problemy zgłoszone przez skrypt i spróbować uaktualnić listę dystrybucyjną jeszcze raz. 

2. Jeśli powyższy skrypt nie pomoże lub problem będzie nadal występował, otwórz bilet [pomocy technicznej](../../business-video/get-help-support.md). Aby można było ustalić problem, należy eskalować go do zespołu inżynierów grup.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Jak uaktualnić kilka list dystrybucyjnych jednocześnie za pomocą programu PowerShell

Jeśli masz doświadczenie w  używaniu programu PowerShell, możesz wybrać tę trasę zamiast interfejsu użytkownika. Mamy zestaw polecenia cmdlet, które pomogą Ci uaktualnić listy dystrybucyjne. Patrz poniżej.

### <a name="upgrade-a-single-dl"></a>Uaktualnianie pojedynczej biblioteki dystrybucyjnej

Aby uaktualnić jedną bibliotekę dystrybucyjną, uruchom następujące polecenie:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <Dl SMTP address>
```

Jeśli na przykład chcesz uaktualnić bibliotekę dystrybucyjną przy użyciu adresu SMTP dl1@contoso.com, uruchom następujące polecenie:

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com
```

> [!NOTE]
> Możesz również uaktualnić pojedynczą listę dystrybucyjną do grupy Microsoft 365 przy użyciu polecenia cmdlet programu PowerShell [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup)

### <a name="upgrade-multiple-dls-in-a-batch"></a>Uaktualnianie wielu adresów DLs w partii

Możesz również przekazać wiele adresów DLs jako partię i uaktualnić je razem:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <DL SMTP address1>, <DL SMTP address2>,
<DL SMTP address3>, <DL SMTP address4>
```

Jeśli na przykład chcesz uaktualnić pięć adresów DLs przy użyciu adresu SMTP `dl1@contoso.com` `dl2@contoso.com`i , `dl3@contoso.com``dl4@contoso.com` i `dl5@contoso.com`, uruchom następujące polecenie:

`Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com`

### <a name="upgrade-all-eligible-dls"></a>Uaktualnianie wszystkich kwalifikujących się adresów DLs

Dostępne są dwa sposoby, za pomocą których możesz uaktualnić wszystkie kwalifikujące się adresy DLs.

> [!NOTE]
> Polecenie Upgrade-DistributionGroup nie odbiera danych z potoku, dlatego do pomyślnego uruchomienia jest wymagane użycie operatora "foreach-object{}".

1. Pobierz uprawnialne adresy DLs w dzierżawie i uaktualnij je przy użyciu polecenia uaktualnienia:

```PowerShell
Get-EligibleDistributionGroupForMigration | Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

2. Uzyskaj listę wszystkich adresów DLs i uaktualnij tylko kwalifikujące się adresy DLs:

```PowerShell
Get-DistributionGroup| Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Często zadawane pytania dotyczące uaktualniania list dystrybucyjnych do grup Microsoft 365 w programie Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>Których list dystrybucyjnych nie można uaktualnić?

Uaktualnić można tylko listy dystrybucyjne zarządzane w chmurze oraz proste, nie zagnieżdżone. W poniższej tabeli wymieniono listy dystrybucyjne, **których NIE MOŻNA** uaktualnić.

|**Właściwość**|**Kwalifikujesz się?**|
|:-----|:-----|
|Lokalna zarządzana lista dystrybucyjna.  <br/> |Nie  <br/> |
|Zagnieżdżone listy dystrybucyjne. Lista dystrybucyjna zawiera grupy podrzędne lub jest członkiem innej grupy.  <br/> |Nie  <br/> |
|Listy dystrybucyjne z **typami adresatów członków innymi** niż **UserMailbox**, **SharedMailbox**, **TeamMailbox**, **MailUser**  <br/> |Nie  <br/> |
|Lista dystrybucyjna, która ma ponad 100 właścicieli  <br/> |Nie  <br/> |
|Lista dystrybucyjna, która ma tylko członków, ale nie właściciela  <br/> |Nie  <br/> |
|Lista dystrybucyjna zawierająca alias zawierający znaki specjalne  <br/> |Nie  <br/> |
|Jeśli lista dystrybucyjna jest skonfigurowana jako adres przesyłania dalej dla udostępnionej skrzynki pocztowej  <br/> |Nie  <br/> |
|Jeśli dl jest częścią ograniczenia **nadawcy w** innej dl.  <br/> |Nie  <br/> |
|Grupy zabezpieczeń  <br/> |Nie  <br/> |
|Dynamiczne listy dystrybucyjne  <br/> |Nie  <br/> |
|Listy dystrybucyjne przekonwertowane na **listy pokoi**  <br/> |Nie  <br/> |

### <a name="check-which-dls-are-eligible-for-upgrade"></a>Sprawdzanie, które adresy DLs można uaktualnić

Jeśli chcesz sprawdzić, czy lista dystrybucyjna jest kwalifikowana, możesz uruchomić poniższe polecenie:

`Get-DistributionGroup <DL SMTP address> | Get-EligibleDistributionGroupForMigration`

Jeśli chcesz sprawdzić, które adresy DLs są dostępne do uaktualnienia, uruchom następujące polecenie:

`Get-EligibleDistributionGroupForMigration`

### <a name="who-can-run-the-upgrade-scripts"></a>KtoTo uruchomić skrypty uaktualniania?

Osoby z uprawnieniami administratora globalnego Exchange uprawnieniami administratora.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Dlaczego wizytówka nadal wyświetla listę dystrybucyjną? Co należy zrobić, aby zapobiec wyświetlaniu uaktualnionej listy dystrybucyjnej na liście autosugerowania?

- For Outlook: When someone tries to send an email in Outlook by typing the Microsoft 365 group name after migration, the recipient will be resolved as the distribution list instead of the group. Wizytówka adresata będzie wizytówką listy dystrybucyjnej. Jest to spowodowane tym, że pamięć podręczna adresata lub nazwa nicku w Outlook. Wiadomość e-mail zostanie pomyślnie wysłana do grupy, ale może spowodować zamieszanie u nadawcy.<br/>Aby zresetować pamięć podręczną, możesz wykonać czynności opisane w Outlook Informacje o liście [autouzupełniania](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list), co rozwiąże ten problem.

- Na Outlook w sieci Web: W przypadku Outlook w sieci Web adresat listy dystrybucyjnej nadal pozostanie w pamięci podręcznej. Aby odświeżyć pamięć podręczną w celu zobaczenia wizytówki grupy, możesz wykonać czynności opisane w tece Usuwanie sugerowanej nazwy lub adresu [e-mail](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) z listy autouzupełnień.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Czy nowi członkowie grupy otrzymują powitaną wiadomość e-mail w swoich skrzynkach odbiorczych?

L.p. Ustawienie umożliwiające włączenie wiadomości powitalnych jest domyślnie ustawione na wartość fałsz. To ustawienie wpływa zarówno na obecnych, jak i nowych członków grupy, którzy mogą dołączyć po zakończeniu migracji. Jeśli właściciel grupy później zezwala na korzystanie z użytkowników gości, użytkownicy goście nie otrzymają powitaowej wiadomości e-mail w swoich skrzynkach odbiorczych. Członkowie goście mogą kontynuować pracę z grupą.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>Co zrobić, jeśli co najmniej jedna z adresów DLs nie zostanie uaktualniona?

W niektórych przypadkach nie można uaktualnić biblioteki dystrybucyjnej, ale nie można jej uaktualnić. Dl nie jest uaktualniana i pozostaje jako dl.

- Jeśli administrator **zastosować grupowe** zasady adresu e-mail do grup w organizacji i próbuje uaktualnić adresy DLs, które nie spełniają kryteriów, nie zostanie uaktualniona

- Nie można uaktualnić adresów DLs z ustawieniem **MemberJoinRestriction** lub **MemberDepartRestriction** ustawionym jako **Closed**

- Tworzenie Microsoft 365 grupy jest dozwolone tylko dla kilku użytkowników, korzystając z procedury [opisanej w tym artykule](/microsoft-365/solutions/manage-creation-of-groups). W tym scenariuszu, jeśli właściciel listy dystrybucyjnej nie może utworzyć grupy Microsoft 365, lista dystrybucyjna nie zostanie uaktualnina do Microsoft 365 grupy. Obejście: Użyj jednego z poniższych obejść dla powyższego scenariusza:
1)  Upewnij się, że wszyscy użytkownicy wymienini jako właściciele biblioteki dystrybucyjnej mogą tworzyć grupę M365, czyli są członkami grupy zabezpieczeń, do których dostęp jest dozwolony dla grupy M365.
LUB
2)  Tymczasowo zamień właściciela biblioteki dystrybucyjnej, dla których nie można utworzyć grupy M365, na użytkownika, który może tworzyć grupę M365

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>Co się stanie z biblioteką dystrybucyjną, jeśli uaktualnienie z EAC zakończy się niepowodzeniem?

Uaktualnienie nastąpi tylko wtedy, gdy połączenie zostanie przesłane na serwer. Jeśli uaktualnienie nie powiedzie się, twoje adresy DLs zostaną nienaruszone. Będą one działać tak jak do tego, co do tego używali.

## <a name="related-content"></a>Zawartość pokrewna

[Porównanie grup](../create-groups/compare-groups.md) (artykuł)\
[Objaśnienie Microsoft 365 grup użytkownikom](../create-groups/explain-groups-knowledge-worker.md) (artykuł)\
[Dodawanie lub usuwanie członków z Microsoft 365 przy użyciu centrum administracyjnego](../create-groups/add-or-remove-members-from-groups.md)
