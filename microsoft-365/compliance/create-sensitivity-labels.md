---
title: Twórz o publikuj etykiety poufności
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: 'Wymaganie dotyczące wszystkich rozwiązań Microsoft Purview Information Protection: tworzenie, konfigurowanie i publikowanie etykiet poufności w celu klasyfikowania i ochrony danych organizacji.'
ms.openlocfilehash: ad7e9c9aeea0a1ef05f79214afd60ac479ba2e66
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625528"
---
# <a name="create-and-configure-sensitivity-labels-and-their-policies"></a>Tworzenie i konfigurowanie etykiet poufności i ich zasad

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Wszystkie rozwiązania Microsoft Purview Information Protection są implementowane przy użyciu [etykiet poufności](sensitivity-labels.md). Aby utworzyć i opublikować te etykiety, przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a>.

Najpierw utwórz i skonfiguruj etykiety poufności, które chcesz udostępnić aplikacjom i innym usługom. Na przykład etykiety, które użytkownicy mają wyświetlać i stosować z aplikacji pakietu Office.

Następnie utwórz co najmniej jedną zasadę etykiet zawierającą skonfigurowane etykiety i ustawienia zasad. To zasady etykiet publikują etykiety i ustawienia dla wybranych użytkowników i lokalizacji.

> [!TIP]
> Jeśli nie masz jeszcze żadnych etykiet poufności, możesz kwalifikować się do automatycznego tworzenia etykiet domyślnych i domyślnych zasad etykiet. Nawet jeśli masz jakieś etykiety, może okazać się przydatne wyświetlenie konfiguracji tych etykiet domyślnych, które tworzymy dla nowych klientów. Możesz na przykład wykonać te same konfiguracje ręczne, aby przyspieszyć wdrażanie własnej etykiety.
> 
> Aby uzyskać więcej informacji, zobacz [Domyślne etykiety i zasady dla Microsoft Purview Information Protection](mip-easy-trials.md).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny organizacji ma pełne uprawnienia do tworzenia wszystkich aspektów etykiet poufności i zarządzania nimi. Jeśli nie logujesz się jako administrator globalny, zobacz [Uprawnienia wymagane do tworzenia etykiet poufności i zarządzania nimi](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels).

## <a name="create-and-configure-sensitivity-labels"></a>Tworzenie i konfigurowanie etykiet poufności

1. Z [portal zgodności Microsoft Purview](https://compliance.microsoft.com/) wybierz pozycję **Rozwiązania Etykiety** > **ochrony** >  informacji

2. Na stronie **Etykiety** wybierz pozycję **+ Utwórz etykietę** , aby rozpocząć nową konfigurację etykiet poufności: 
    
    ![Utwórz etykietę poufności.](../media/create-sensitivity-label-full.png)

    > [!NOTE]
    > Domyślnie dzierżawy nie mają żadnych etykiet i musisz je utworzyć. Etykiety na przykładowym obrazie pokazują etykiety domyślne, które zostały [zmigrowane z usługi Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels).

3. Na stronie **Definiowanie zakresu dla tej etykiety** wybrane opcje określają zakres etykiety dla ustawień, które można skonfigurować i gdzie będą widoczne po opublikowaniu:

    ![Zakresy etykiet poufności.](../media/sensitivity-labels-scopes.png)

    - Jeśli wybrano **opcję Pliki & wiadomości e-mail** , możesz skonfigurować ustawienia, które mają zastosowanie do aplikacji obsługujące etykiety poufności, takie jak Office Word i Outlook. Jeśli ta opcja nie zostanie wybrana, zobaczysz pierwszą stronę tych ustawień, ale nie możesz ich skonfigurować, a etykiety nie będą dostępne dla użytkowników do wybrania w tych aplikacjach.

    - Jeśli wybrano **opcję Grupy & witryn** , możesz skonfigurować ustawienia dotyczące grup platformy Microsoft 365 i witryn dla aplikacji Teams i SharePoint. Jeśli ta opcja nie zostanie wybrana, zobaczysz pierwszą stronę tych ustawień, ale nie możesz ich skonfigurować, a etykiety nie będą dostępne dla użytkowników do wybrania dla grup i witryny.

    Aby uzyskać informacje o zakresie **schematyzowanych zasobów danych**, zobacz [Automatyczne etykietowanie zawartości w Mapa danych w Microsoft Purview](/azure/purview/create-sensitivity-label).

4. Postępuj zgodnie z monitami o konfigurację ustawień etykiety.

    Aby uzyskać więcej informacji na temat ustawień etykiet, zobacz [Co etykiety poufności mogą zrobić](sensitivity-labels.md#what-sensitivity-labels-can-do) z informacji przeglądowych i skorzystaj z pomocy interfejsu użytkownika dla poszczególnych ustawień.

5. Powtórz te kroki, aby utworzyć więcej etykiet. Jeśli jednak chcesz utworzyć etykietę podrzędną, najpierw wybierz etykietę nadrzędną i wybierz pozycję **...** w polu **Więcej akcji**, a następnie wybierz pozycję **Dodaj etykietę podrzędną**.

6. Po utworzeniu wszystkich potrzebnych etykiet przejrzyj ich kolejność i w razie potrzeby przenieś je w górę lub w dół. Aby zmienić kolejność etykiety, wybierz pozycję **...** w polu **Więcej akcji**, a następnie wybierz pozycję **Przenieś w górę** lub **Przenieś w dół**. Aby uzyskać więcej informacji, zobacz [Priorytet etykiety (kolejność ma znaczenie)](sensitivity-labels.md#label-priority-order-matters) z informacji przeglądowych.

Aby edytować istniejącą etykietę, wybierz ją, a następnie wybierz przycisk **Edytuj etykietę** :

![Przycisk Edytuj etykietę, aby edytować etykietę poufności.](../media/edit-sensitivity-label-full.png)

Ten przycisk uruchamia konfigurację **Edytuj etykietę poufności** , która umożliwia zmianę wszystkich ustawień etykiety w kroku 4.

Nie usuwaj etykiety, chyba że rozumiesz wpływ na użytkowników. Aby uzyskać więcej informacji, zobacz sekcję [Usuwanie i usuwanie etykiet](#removing-and-deleting-labels) . 

> [!NOTE]
> Jeśli edytujesz etykietę, która została już opublikowana przy użyciu zasad etykiety, po zakończeniu konfiguracji nie są wymagane żadne dodatkowe kroki. Na przykład nie trzeba dodawać ich do nowych zasad etykiet, aby zmiany stały się dostępne dla tych samych użytkowników. Zaczekaj jednak na replikację zmian do wszystkich aplikacji i usług przez maksymalnie 24 godziny.

Dopóki nie opublikujesz etykiet, nie będą one dostępne do wybrania w aplikacjach lub usługach. Aby opublikować etykiety, należy [je dodać do zasad etykiet](#publish-sensitivity-labels-by-creating-a-label-policy).

> [!IMPORTANT]
> Na tej **karcie Etykiety** nie wybieraj karty **Publikuj etykiety** (ani **przycisku Publikuj etykietę** podczas edytowania etykiety), chyba że musisz utworzyć nowe zasady etykiet. Wiele zasad etykiet jest potrzebnych tylko wtedy, gdy użytkownicy potrzebują różnych etykiet lub różnych ustawień zasad. Dążyć do posiadania jak najmniejszej liczby zasad etykiet — nierzadko należy mieć tylko jedną zasadę etykiet dla organizacji.

### <a name="additional-label-settings-with-security--compliance-powershell"></a>Dodatkowe ustawienia etykiet za pomocą programu PowerShell security & Compliance

Dodatkowe ustawienia etykiety są dostępne za pomocą polecenia cmdlet [Set-Label](/powershell/module/exchange/set-label) z programu [PowerShell Security & Compliance](/powershell/exchange/scc-powershell).

Przykład:

- Użyj parametru *LocaleSettings* dla wdrożeń międzynarodowych, aby użytkownicy widzieli nazwę etykiety i etykietkę narzędzia w języku lokalnym. Poniższa [sekcja](#example-configuration-to-configure-a-sensitivity-label-for-different-languages) zawiera przykładową konfigurację, która określa nazwę etykiety i tekst etykietki narzędzia dla języka francuskiego, włoskiego i niemieckiego.

- Ustawienia zaawansowane obsługiwane przez wbudowane etykietowanie są zawarte w dokumentacji programu PowerShell. Aby uzyskać więcej pomocy w określaniu tych ustawień zaawansowanych programu [PowerShell, zobacz porady programu PowerShell dotyczące określania ustawień zaawansowanych](#powershell-tips-for-specifying-the-advanced-settings) . Aby uzyskać dodatkowe zaawansowane ustawienia obsługiwane przez klienta ujednoliconego etykietowania usługi Azure Information Protection, zapoznaj się [z dokumentacją przewodnika administratora tego klienta](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-labels).

#### <a name="example-configuration-to-configure-a-sensitivity-label-for-different-languages"></a>Przykładowa konfiguracja umożliwiająca skonfigurowanie etykiety poufności dla różnych języków

W poniższym przykładzie przedstawiono konfigurację programu PowerShell dla etykiety o nazwie "Public" z tekstem zastępczym etykietki narzędzia. W tym przykładzie nazwa etykiety i tekst etykietki narzędzia są skonfigurowane dla języka francuskiego, włoskiego i niemieckiego.

W wyniku tej konfiguracji użytkownicy, którzy mają aplikacje pakietu Office korzystające z tych języków wyświetlania, widzą nazwy etykiet i etykietki narzędzi w tym samym języku. Podobnie jeśli masz zainstalowanego klienta ujednoliconego etykietowania usługi Azure Information Protection w celu etykietowania plików z Eksplorator plików, użytkownicy, którzy mają te wersje językowe systemu Windows, widzą nazwy etykiet i etykietki narzędzi w języku lokalnym, gdy używają akcji kliknięcia prawym przyciskiem myszy do etykietowania.

W przypadku języków, które należy obsługiwać, użyj [identyfikatorów języka](/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016#language-identifiers) pakietu Office (znanych również jako tagi języka) i określ własne tłumaczenie nazwy etykiety i etykietki narzędzia.

Przed uruchomieniem poleceń w programie PowerShell należy najpierw [nawiązać połączenie z programem PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell).

```powershell
$Languages = @("fr-fr","it-it","de-de")
$DisplayNames=@("Publique","Publico","Oeffentlich")
$Tooltips = @("Texte Français","Testo italiano","Deutscher text")
$label = "Public"
$DisplayNameLocaleSettings = [PSCustomObject]@{LocaleKey='DisplayName';
Settings=@(
@{key=$Languages[0];Value=$DisplayNames[0];}
@{key=$Languages[1];Value=$DisplayNames[1];}
@{key=$Languages[2];Value=$DisplayNames[2];})}
$TooltipLocaleSettings = [PSCustomObject]@{LocaleKey='Tooltip';
Settings=@(
@{key=$Languages[0];Value=$Tooltips[0];}
@{key=$Languages[1];Value=$Tooltips[1];}
@{key=$Languages[2];Value=$Tooltips[2];})}
Set-Label -Identity $Label -LocaleSettings (ConvertTo-Json $DisplayNameLocaleSettings -Depth 3 -Compress),(ConvertTo-Json $TooltipLocaleSettings -Depth 3 -Compress)
```

#### <a name="powershell-tips-for-specifying-the-advanced-settings"></a>Porady programu PowerShell dotyczące określania ustawień zaawansowanych

Mimo że można określić etykietę poufności według jej nazwy, zalecamy użycie identyfikatora GUID etykiety, aby uniknąć potencjalnych pomyłek dotyczących określania nazwy etykiety lub nazwy wyświetlanej. Nazwa etykiety jest unikatowa w dzierżawie, więc możesz mieć pewność, że konfigurujesz poprawną etykietę. Nazwa wyświetlana nie jest unikatowa i może spowodować skonfigurowanie nieprawidłowej etykiety. Aby znaleźć identyfikator GUID i potwierdzić zakres etykiety:

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid, ContentType
````

Aby usunąć ustawienie zaawansowane z etykiety poufności, użyj tej samej składni parametrów AdvancedSettings, ale określ wartość ciągu o wartości null. Przykład:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope=""}
````

Aby sprawdzić konfigurację etykiety, w tym ustawienia zaawansowane, użyj następującej składni z własnym identyfikatorem GUID etykiety:

```powershell
(Get-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e).settings
```

## <a name="publish-sensitivity-labels-by-creating-a-label-policy"></a>Publikowanie etykiet poufności przez utworzenie zasad etykiet

1. Z [portal zgodności Microsoft Purview](https://compliance.microsoft.com/) wybierz pozycję **RozwiązaniaZasady** > **etykiet** **ochrony informacji** > 

2. Na stronie **Zasady etykiet** wybierz pozycję **Publikuj etykietę** , aby rozpocząć konfigurację **tworzenia zasad** :
    
    ![Publikowanie etykiet.](../media/publish-sensitivity-labels-full.png)
    
    > [!NOTE]
    > Domyślnie dzierżawy nie mają żadnych zasad etykiet i musisz je utworzyć. 

3. Na stronie **Wybieranie etykiet poufności do opublikowania** wybierz link **Wybierz etykiety poufności do opublikowania** . Wybierz etykiety, które chcesz udostępnić w aplikacjach i usługach, a następnie wybierz pozycję **Dodaj**.

    > [!IMPORTANT]
    > Jeśli wybierzesz etykietę podrzędną, upewnij się, że wybrano również jej etykietę nadrzędną.

4. Przejrzyj wybrane etykiety i aby wprowadzić wszelkie zmiany, wybierz pozycję **Edytuj**. W przeciwnym razie wybierz pozycję **Dalej**.

5. Postępuj zgodnie z monitami, aby skonfigurować ustawienia zasad.

    Wyświetlane ustawienia zasad są zgodne z zakresem wybranych etykiet. Jeśli na przykład wybrano etykiety z zakresem **Pliki & wiadomości e-mail** , ustawienia zasad **Domyślnie zastosuj tę etykietę do grup i witryn** oraz **Wymagaj od użytkowników zastosowania etykiety do ich grup i witryn**.

    Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Jakie zasady etykiet można zrobić](sensitivity-labels.md#what-label-policies-can-do) z informacji przeglądowych i skorzystaj z pomocy w interfejsie użytkownika dla poszczególnych ustawień.

    W przypadku etykiet skonfigurowanych dla **zasobów Mapa danych w Microsoft Purview (wersja zapoznawcza)**: etykiety te nie mają żadnych skojarzonych ustawień zasad.

6. Powtórz te kroki, jeśli potrzebujesz różnych ustawień zasad dla różnych użytkowników lub zakresów. Na przykład chcesz mieć dodatkowe etykiety dla grupy użytkowników lub inną etykietę domyślną dla podzestawu użytkowników. Lub jeśli skonfigurowano etykiety tak, aby miały różne zakresy.

7. Jeśli utworzysz więcej niż jedną zasadę etykiety, która może spowodować konflikt użytkownika, przejrzyj kolejność zasad i w razie potrzeby przenieś je w górę lub w dół. Aby zmienić kolejność zasad etykiet, wybierz pozycję **...** w polu **Więcej akcji**, a następnie wybierz pozycję **Przenieś w górę** lub **Przenieś w dół**. Aby uzyskać więcej informacji, zobacz [Priorytet zasad etykiety (kolejność ma znaczenie)](sensitivity-labels.md#label-policy-priority-order-matters) z informacji przeglądowych.

Ukończenie konfiguracji **tworzenia zasad** powoduje automatyczne opublikowanie zasad etykiety. Aby wprowadzić zmiany w opublikowanych zasadach, po prostu edytuj je. Nie ma określonej akcji publikowania ani ponownego publikowania do wybrania.

Aby edytować istniejące zasady etykiet, wybierz je, a następnie wybierz przycisk **Edytuj zasady** : 

![Edytowanie etykiety poufności.](../media/edit-sensitivity-label-policy-full.png)

Ten przycisk uruchamia konfigurację **tworzenia zasad** , która umożliwia edytowanie etykiet, które są dołączone, oraz ustawień etykiet. Po zakończeniu konfiguracji wszelkie zmiany są automatycznie replikowane do wybranych użytkowników i usług.

### <a name="additional-label-policy-settings-with-security--compliance-powershell"></a>Dodatkowe ustawienia zasad etykiet za pomocą programu PowerShell & zgodności z zabezpieczeniami

Dodatkowe ustawienia zasad etykiet są dostępne za pomocą polecenia cmdlet [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) z programu [PowerShell Security & Compliance](/powershell/exchange/scc-powershell).

Ta dokumentacja zawiera zaawansowane ustawienia, które są obsługiwane przez wbudowane etykietowanie. Aby uzyskać dodatkowe zaawansowane ustawienia obsługiwane przez klienta ujednoliconego etykietowania usługi Azure Information Protection, zapoznaj się [z dokumentacją przewodnika administratora tego klienta](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies).

## <a name="when-to-expect-new-labels-and-changes-to-take-effect"></a>Kiedy należy spodziewać się wprowadzenia nowych etykiet i zmian

W przypadku ustawień zasad etykiet i etykiet zezwalaj na propagację zmian za pośrednictwem usług przez 24 godziny. Istnieje wiele zależności zewnętrznych, z których każda ma własne cykle chronometrażu, dlatego warto odczekać ten 24-godzinny okres, zanim spędzisz czas na rozwiązywaniu problemów z etykietami i zasadami etykiet dla ostatnich zmian.

Istnieją jednak pewne scenariusze, w których zmiany zasad etykiet i etykiet mogą obowiązywać znacznie szybciej lub trwać dłużej niż 24 godziny. Na przykład w przypadku nowych i usuniętych etykiet poufności dla programów Word, Excel i PowerPoint w sieci Web aktualizacje mogą być replikowane w ciągu godziny. Jednak w przypadku konfiguracji, które zależą od wprowadzenia nowych zmian członkostwa w grupie i grupie, lub ograniczeń opóźnienia replikacji sieci i przepustowości, te zmiany mogą potrwać od 24 do 48 godzin.

## <a name="use-powershell-for-sensitivity-labels-and-their-policies"></a>Używanie programu PowerShell na potrzeby etykiet poufności i ich zasad

Teraz możesz użyć programu [PowerShell security & Compliance](/powershell/exchange/scc-powershell) , aby utworzyć i skonfigurować wszystkie ustawienia widoczne w centrum administracyjnym etykietowania. Oznacza to, że oprócz używania programu PowerShell do ustawień, które nie są dostępne w centrach administracyjnych etykietowania, można teraz w pełni utworzyć skrypt tworzenia i konserwacji etykiet poufności i zasad etykiet poufności. 

Zapoznaj się z następującą dokumentacją dotyczącą obsługiwanych parametrów i wartości:

- [Nowa etykieta](/powershell/module/exchange/new-label)
- [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy)
- [Set-Label](/powershell/module/exchange/set-label)
- [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy)

> [!TIP]
> Podczas konfigurowania ustawień zaawansowanych etykiety poufności warto odwołać się do [porad programu PowerShell dotyczących określania sekcji ustawień zaawansowanych](#powershell-tips-for-specifying-the-advanced-settings) na tej stronie.

Możesz również użyć funkcji [Remove-Label](/powershell/module/exchange/remove-label) i [Remove-LabelPolicy](/powershell/module/exchange/remove-labelpolicy) , jeśli musisz wykonać skrypt usuwania etykiet poufności lub zasad etykiet poufności. Jednak przed usunięciem etykiet poufności upewnij się, że przeczytano następną sekcję.

## <a name="removing-and-deleting-labels"></a>Usuwanie i usuwanie etykiet

W środowisku produkcyjnym jest mało prawdopodobne, że konieczne będzie usunięcie etykiet poufności z zasad etykiet lub usunięcie etykiet poufności. Jest bardziej prawdopodobne, że może być konieczne przeprowadzenie jednej lub jednej z tych akcji w początkowej fazie testowania. Upewnij się, że rozumiesz, co się stanie, gdy wykonasz jedną z tych akcji.

Usunięcie etykiety z zasad etykiety jest mniej ryzykowne niż usunięcie tej etykiety i zawsze można ją dodać później, jeśli zajdzie taka potrzeba. Nie będzie można usunąć etykiety, jeśli jest ona nadal w zasadach etykiet.

Gdy usuniesz etykietę z zasad etykiety, aby etykieta nie była już publikowana dla pierwotnie określonych użytkowników, następnym razem, gdy zasady etykiet zostaną odświeżone, użytkownicy nie będą już widzieć tej etykiety do wybrania w aplikacjach pakietu Office. Jeśli ta etykieta jest już zastosowana, etykieta nie zostanie usunięta z zawartości ani kontenera. Na przykład użytkownicy, którzy używają wbudowanego etykietowania w aplikacjach klasycznych dla programów Word, Excel i PowerPoint, nadal widzą nazwę zastosowanej etykiety na pasku stanu. Zastosowana etykieta kontenera nadal chroni witrynę usługi Teams lub SharePoint.

Dla porównania po usunięciu etykiety:

- Jeśli etykieta zastosowała szyfrowanie, bazowy szablon ochrony jest archiwizowany, aby można było nadal otwierać wcześniej chronioną zawartość. Z powodu tego zarchiwizowanego szablonu ochrony nie będzie można utworzyć nowej etykiety o tej samej nazwie. Mimo że można usunąć szablon ochrony przy użyciu programu [PowerShell](/powershell/module/aipservice/remove-aipservicetemplate), nie rób tego, chyba że na pewno nie musisz otwierać zawartości zaszyfrowanej za pomocą zarchiwizowanego szablonu.

- W przypadku dokumentów przechowywanych w programie SharePoint lub OneDrive [włączono etykiety poufności dla plików pakietu Office](sensitivity-labels-sharepoint-onedrive-files.md): po otwarciu dokumentu w Office dla sieci web etykieta nie zostanie zastosowana w aplikacji, a nazwa **etykiety** nie będzie już wyświetlana w kolumnie Czułość w programie SharePoint. Jeśli usunięta etykieta zastosowała szyfrowanie, a usługi mogą przetwarzać zaszyfrowaną zawartość, szyfrowanie zostanie usunięte. Akcje ruchu wychodzącego z tych usług powodują taki sam wynik. Na przykład pobierz, skopiuj do, przejdź do i otwórz za pomocą aplikacji klasycznej lub mobilnej pakietu Office. Mimo że informacje o etykiecie pozostają w metadanych pliku, aplikacje nie mogą już mapować identyfikatora etykiety na nazwę wyświetlaną, więc użytkownicy zakładają, że plik nie jest oznaczony etykietą.

- W przypadku dokumentów przechowywanych poza programami SharePoint i OneDrive lub nie włączono etykiet poufności dla plików pakietu Office i wiadomości e-mail: Po otwarciu zawartości informacje o etykietach w metadanych pozostają, ale bez identyfikatora etykiety mapowania nazw użytkownicy nie widzą wyświetlanej zastosowanej nazwy etykiety (na przykład na pasku stanu dla aplikacji klasycznych). Jeśli usunięta etykieta zastosowała szyfrowanie, szyfrowanie pozostanie, a użytkownicy nadal będą widzieć nazwę i opis zarchiwizowanego szablonu ochrony.

- W przypadku kontenerów, takich jak witryny w programach SharePoint i Teams: etykieta jest usuwana, a wszystkie ustawienia skonfigurowane przy użyciu tej etykiety nie są już wymuszane. Ta akcja zwykle trwa od 48 do 72 godzin w witrynach programu SharePoint i może być szybsza w przypadku aplikacji Teams i Grupy Microsoft 365.

Podobnie jak w przypadku wszystkich zmian etykiet, usunięcie etykiety poufności z zasad etykiety lub usunięcie etykiety poufności wymaga czasu na replikację do wszystkich użytkowników i usług.

## <a name="next-steps"></a>Następne kroki

Aby skonfigurować i używać etykiet poufności dla określonych scenariuszy, skorzystaj z następujących artykułów:

- [Ograniczanie dostępu do zawartości przy użyciu szyfrowania w etykietach poufności](encryption-sensitivity-labels.md)

- [Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md)

- [Używaj etykiet poufności z zespołami, grupami i witrynami](sensitivity-labels-teams-groups-sites.md)

- [Włącz etykiety poufności dla plików pakietu Office w programie SharePoint i usłudze OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)

Aby monitorować sposób użycia etykiet, zobacz [Wprowadzenie do klasyfikacji danych](data-classification-overview.md).
