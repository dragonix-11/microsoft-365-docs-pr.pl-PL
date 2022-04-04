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
description: 'Wymagania dotyczące wszystkich Microsoft Information Protection: Tworzenie, konfigurowanie i publikowanie etykiet wrażliwości w celu klasyfikowania i chroninia danych organizacji.'
ms.openlocfilehash: 5c80147c18cff8c27f8c205ab1ed600e892f7335
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499578"
---
# <a name="create-and-configure-sensitivity-labels-and-their-policies"></a>Tworzenie i konfigurowanie etykiet wrażliwości oraz ich zasad

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Wszystkie Microsoft Information Protection (czasami skrócone do miP) są implementowane za pomocą etykiet [wrażliwości](sensitivity-labels.md). Aby utworzyć i opublikować te etykiety, przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a>.

Najpierw utwórz i skonfiguruj etykiety wrażliwości, które chcesz udostępnić aplikacjom i innym usługom. Na przykład etykiety, które użytkownicy mają widzieć i stosować z Office aplikacji.

Następnie utwórz jedną lub więcej zasad dotyczących etykiet, które zawierają skonfigurowane etykiety i ustawienia zasad. Zasady etykiet publikują etykiety i ustawienia dla wybranych użytkowników i lokalizacji.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny Twojej organizacji ma pełne uprawnienia do tworzenia wszystkich aspektów etykiet wrażliwości i zarządzania nimi. Jeśli nie logujesz się jako administrator globalny, zobacz Uprawnienia wymagane do tworzenia etykiet wrażliwości [i zarządzania nimi](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels).

## <a name="create-and-configure-sensitivity-labels"></a>Tworzenie i konfigurowanie etykiet wrażliwości

1. Z poziomu [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/) wybierz **pozycję** **SolutionsInformation** >  Protection
    
    Jeśli nie widzisz tej opcji od razu, najpierw wybierz pozycję **Pokaż wszystko**.

2. Na stronie **Etykiety** wybierz pozycję **+ Utwórz etykietę, aby** rozpocząć konfigurację Nowa etykieta wrażliwości. 

    Na przykład z Centrum zgodności platformy Microsoft 365:

    ![Utwórz etykietę wrażliwości.](../media/create-sensitivity-label-full.png)

    > [!NOTE]
    > Domyślnie dzierżawcy nie mają żadnych etykiet i trzeba je utworzyć. Etykiety na przykładzie pokazują etykiety domyślne, które zostały [zmigrowane z usługi Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels).

3. Na **stronie Definiowanie** zakresu tej etykiety wybrane opcje określają zakres etykiety dla ustawień, które można skonfigurować, oraz miejsce, w którym będą one widoczne po ich opublikowaniu:

    ![Zakresy etykiet wrażliwości.](../media/sensitivity-labels-scopes.png)

    - Jeśli **zaznaczono &** e-mail, możesz skonfigurować ustawienia dotyczące aplikacji, które obsługują etykiety wrażliwości, takich jak pliki Office Word i Outlook. Jeśli ta opcja nie jest zaznaczona, zostanie wyświetlony pierwszy strona tych ustawień, ale nie możesz ich skonfigurować, a etykiety nie będą dostępne do wyboru dla użytkowników w tych aplikacjach.

    - Jeśli **zaznaczono &** Grupy dla witryn, możesz skonfigurować ustawienia dotyczące grup Microsoft 365, a także witryn dla grup Teams i SharePoint. Jeśli ta opcja nie jest zaznaczona, zostanie zaznaczona pierwsza strona tych ustawień, ale nie możesz ich skonfigurować, a użytkownicy nie będą mieć możliwości wyboru grup i witryn.

    Aby uzyskać informacje na **temat zakresu Schematowane zasoby danych** , zobacz [Automatyczne oznaczanie zawartości w aplikacji Azure Purview](/azure/purview/create-sensitivity-label).

4. Postępuj zgodnie z monitami konfiguracyjnymi ustawień etykiet.

    Aby uzyskać więcej informacji na temat ustawień etykiet, zobacz [Jakie](sensitivity-labels.md#what-sensitivity-labels-can-do) etykiety wrażliwości mogą robić z poziomu informacji przeglądowych i skorzystaj z pomocy w interfejsie użytkownika w poszczególnych ustawieniach.

5. Powtórz te czynności, aby utworzyć więcej etykiet. Jeśli jednak chcesz utworzyć etykietę podrzędną, najpierw zaznacz etykietę nadrzędną i wybierz pozycję **...** dla opcji **Więcej** akcji, a następnie wybierz pozycję **Dodaj etykietę podrzędną**.

6. Po utworzeniu wszystkich potrzebnych etykiet przejrzyj ich kolejność i w razie potrzeby przenieś je w górę lub w dół. Aby zmienić kolejność etykiet, wybierz pozycję **...** w przypadku opcji **Więcej** akcji, a następnie wybierz pozycję **Przenieś w** górę lub **Przenieś w dół**. Aby uzyskać więcej informacji, zobacz [Priorytet etykiety (ważne zamówienie) z](sensitivity-labels.md#label-priority-order-matters) informacji o przeglądzie.

Aby edytować istniejącą etykietę, zaznacz ją, a następnie wybierz **przycisk Edytuj etykietę** :

![Przycisk Edytuj etykietę umożliwia edytowanie etykiety wrażliwości.](../media/edit-sensitivity-label-full.png)

Ten przycisk powoduje rozpoczęcie **konfiguracji Edytuj etykietę wrażliwości** , która umożliwia zmianę wszystkich ustawień etykiet w kroku 4.

Nie usuwaj etykiety, jeśli nie rozumiesz wpływu na użytkowników. Aby uzyskać więcej informacji, zobacz [sekcję Usuwanie i usuwanie etykiet](#removing-and-deleting-labels) . 

> [!NOTE]
> Jeśli edytujesz etykietę, która została już opublikowana przy użyciu zasad etykiet, po zakończeniu konfiguracji nie są wymagane żadne dodatkowe czynności. Nie musisz na przykład dodawać ich do nowych zasad etykiet, aby zmiany stały się dostępne dla tych samych użytkowników. Zmiany można jednak zreplikować do wszystkich aplikacji i usług w ciągu 24 godzin.

Do czasu opublikowania etykiet nie będą one dostępne do wyboru w aplikacjach ani usługach. Aby opublikować etykiety, należy [je dodać do zasad etykiet](#publish-sensitivity-labels-by-creating-a-label-policy).

> [!IMPORTANT]
> Na tej **karcie Etykiety** nie wybieraj karty  Publikuj etykiety (ani przycisku Publikuj etykietę podczas edytowania etykiety), chyba że musisz utworzyć nowe zasady etykiet. Wiele zasad etykiet jest potrzebnych tylko wtedy, gdy użytkownicy potrzebują różnych etykiet lub różnych ustawień zasad. Celem jest, aby zasady dotyczące etykiet były jak najmniejsze — nie jest rzadkością zasady dotyczące etykiet dla organizacji.

### <a name="additional-label-settings-with-security--compliance-center-powershell"></a>Dodatkowe ustawienia etykiet za pomocą programu PowerShell & Security & Compliance Center

Dodatkowe ustawienia etykiet są dostępne za pomocą polecenia cmdlet [Set-Label](/powershell/module/exchange/set-label) z witryny [Security & Compliance Center w programie PowerShell](/powershell/exchange/scc-powershell).

Przykład:

- Użyj *parametru LocaleSettings* dla wdrożeń międzynarodowej, aby użytkownicy widzili etykietkę i etykietkę narzędzia w swoim języku lokalnym. W [poniższej sekcji](#example-configuration-to-configure-a-sensitivity-label-for-different-languages) przedstawiono przykładową konfigurację określającą nazwę etykiety i tekst etykiety narzędzia dla języka francuskiego, włoskiego i niemieckiego.

- Klient ujednoliconej Information Protection Azure Information Protection rozbudowaną listę ustawień zaawansowanych, takich jak ustawianie [](/azure/information-protection/rms-client/clientv2-admin-guide-customizations) koloru etykiety i stosowanie właściwości niestandardowej podczas stosowania etykiety. Aby uzyskać pełną listę, zobacz [Dostępne zaawansowane ustawienia etykiet w](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-labels) przewodniku administratora tego klienta.

#### <a name="example-configuration-to-configure-a-sensitivity-label-for-different-languages"></a>Przykładowa konfiguracja konfigurowania etykiety wrażliwości dla różnych języków

W poniższym przykładzie pokazano konfigurację programu PowerShell dla etykiety o nazwie "Publiczna" z tekstem zastępczym etykietki narzędzia. W tym przykładzie nazwa etykiety i tekst etykiety narzędzia są skonfigurowane dla języka francuskiego, włoskiego i niemieckiego.

W wyniku tej konfiguracji użytkownicy korzystający z Office korzystających z tych języków wyświetlania widzą nazwy etykiet i etykietki narzędzi w tym samym języku. Podobnie, jeśli masz zainstalowanego klienta ujednoliconego etykiet usługi Azure Information Protection w celu oznaczania plików z usługi Eksplorator plików, użytkownicy, którzy mają te wersje językowe programu Windows, zobaczą nazwy etykiet i etykietki narzędzi w języku lokalnym, gdy używają akcji oznaczonych etykietami prawym przyciskiem myszy.

W przypadku języków, które chcesz obsługiwać, użyj identyfikatorów języka języka [Office (](/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016#language-identifiers)nazywanych również tagami języków) i określ własne tłumaczenie nazwy etykiety i etykietki narzędzia.

Przed uruchomieniem poleceń w programie PowerShell należy najpierw połączyć się z programem [PowerShell w centrum zabezpieczeń & zgodności](/powershell/exchange/connect-to-scc-powershell).

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

## <a name="publish-sensitivity-labels-by-creating-a-label-policy"></a>Publikowanie etykiet wrażliwości przez utworzenie zasad etykiet

1. Z poziomu [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/) wybierz **pozycję** **SolutionsInformation** >  Protection
    
    Jeśli nie widzisz tej opcji od razu, najpierw wybierz pozycję **Pokaż wszystko**.

2. Wybierz **kartę Zasady etykiet** , a następnie pozycję **Publikuj etykietę** , aby uruchomić **konfigurację Tworzenie** zasad:

    Na przykład z Centrum zgodności platformy Microsoft 365:

    ![Publikowanie etykiet.](../media/publish-sensitivity-labels-full.png)

    > [!NOTE]
    > Domyślnie dzierżawcy nie mają żadnych zasad tworzenia etykiet i należy je utworzyć. 

3. Na **stronie Wybierz etykiety wrażliwości do opublikowania** wybierz link Wybierz **etykiety wrażliwości do opublikowania** . Wybierz etykiety, które chcesz udostępnić w aplikacjach i usługach, a następnie wybierz pozycję **Dodaj**.

    > [!IMPORTANT]
    > Jeśli wybierzesz etykietę podrzędną, upewnij się, że jest również zaznaczana etykieta nadrzędna.

4. Przejrzyj zaznaczone etykiety i aby wprowadzić zmiany, wybierz pozycję **Edytuj**. W przeciwnym razie wybierz pozycję **Dalej**.

5. Postępuj zgodnie z monitami, aby skonfigurować ustawienia zasad.

    Wybrane ustawienia zasad są zgodne z zakresem wybranych etykiet. Jeśli na przykład zaznaczono etykiety, które mają zakres wiadomości e-mail Pliki **&**, ustawienia zasad Domyślnie zastosuj tę etykietę do grup  i witryn oraz Wymagaj od użytkowników stosowania etykiety do grup i **witryn.**

    Aby uzyskać więcej informacji o tych ustawieniach[](sensitivity-labels.md#what-label-policies-can-do), zobacz Jakie zasady dotyczące etykiet można stosować na stronie informacji przeglądowych i korzystać z pomocy w interfejsie użytkownika w przypadku poszczególnych ustawień.

    W przypadku etykiet skonfigurowanych dla zasobów **usługi Azure Purview (wersja Preview)**: Te etykiety nie mają skojarzonych ustawień zasad.

6. Powtórz te czynności, jeśli potrzebujesz różnych ustawień zasad dla różnych użytkowników lub zakresów. Chcesz na przykład dodać etykiety dla grupy użytkowników lub inną etykietę domyślną dla podzbioru użytkowników. Jeśli natomiast skonfigurowano etykiety o różnych zakresach.

7. Jeśli utworzysz więcej niż jedną zasady etykiet, które mogą powodować konflikty u użytkownika, przejrzyj kolejność zasad i w razie potrzeby przenieś je w górę lub w dół. Aby zmienić kolejność zasad etykiet, wybierz pozycję **...** w przypadku opcji **Więcej** akcji, a następnie wybierz pozycję **Przenieś w** górę lub **Przenieś w dół**. Aby uzyskać więcej informacji, zobacz [Priorytet zasad dotyczących etykiet (ważne zamówienie)](sensitivity-labels.md#label-policy-priority-order-matters) z informacji o przeglądzie.

Ukończenie **konfiguracji zasad Create (** Utwórz) spowoduje automatyczne opublikowanie zasad etykiet. Aby wprowadzić zmiany w opublikowanych zasadach, po prostu je edytuj. Nie ma żadnych konkretnych akcji publikowania ani ponownego publikowania, które chcesz wybrać.

Aby edytować istniejące zasady etykiet, zaznacz je, a następnie wybierz przycisk **Edytuj zasady** : 

![Edytuj etykietę wrażliwości.](../media/edit-sensitivity-label-policy-full.png)

Ten przycisk powoduje rozpoczęcie **konfiguracji Utwórz zasady** , która pozwala edytować zawarte etykiety i ustawienia etykiet. Po ukończeniu konfiguracji wszystkie zmiany są automatycznie replikowane do wybranych użytkowników i usług.

### <a name="additional-label-policy-settings-with-security--compliance-center-powershell"></a>Dodatkowe ustawienia zasad etykiet z programem PowerShell & Centrum zgodności zabezpieczeń

Dodatkowe ustawienia zasad etykiet są dostępne za pomocą polecenia [cmdlet Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) z programu [Security & Compliance Center w programie PowerShell](/powershell/exchange/scc-powershell).

Klient ujednoliconej etykiet usługi Azure Information Protection obsługuje wiele ustawień zaawansowanych, takich [](/azure/information-protection/rms-client/clientv2-admin-guide-customizations) jak migracja z innych rozwiązań etykiet i wyskakujące wiadomości w programie Outlook, które ostrzegają, wyjustują lub blokują wysyłane wiadomości e-mail. Aby uzyskać pełną listę, zobacz [Dostępne zaawansowane ustawienia zasad etykiet](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies) z przewodnika administratora tego klienta.

## <a name="when-to-expect-new-labels-and-changes-to-take-effect"></a>Kiedy można oczekiwać, że nowe etykiety i zmiany zostaną wprowadzone

W przypadku etykiet i ustawień zasad etykiet należy zezwolić na propagację zmian w usługach po 24 godzinach. Istnieje wiele zależności zewnętrznych, które mają własne cykle chronometrażu, dlatego warto poczekać ten 24-godzinny okres, zanim poświęcisz czas na rozwiązywanie problemów z etykietami i zasadami etykiet na potrzeby ostatnich zmian.

Jednak w niektórych sytuacjach zmiany zasad etykiet i etykiet mogą być wprowadzone znacznie szybciej lub dłużej niż 24 godziny. Na przykład w przypadku nowych i usuniętych etykiet wrażliwości programu Word, Excel i PowerPoint w sieci Web aktualizacje mogą być replikowane w ciągu godziny. Jednak w przypadku konfiguracji zależnych od wypełniania zmian członkostwa w nowych grupach i grupach lub ograniczeń przepustowości i opóźnień replikacji sieci te zmiany mogą potrwać 24–48 godzin.

## <a name="use-powershell-for-sensitivity-labels-and-their-policies"></a>Etykiety wrażliwości i ich zasady można stosować w programie PowerShell

Teraz możesz użyć programu [PowerShell &](/powershell/exchange/scc-powershell) zabezpieczeń i zgodności, aby utworzyć i skonfigurować wszystkie ustawienia, które są dostępne w Twoim centrum administracyjnym z etykietami. Oznacza to, że oprócz używania programu PowerShell do obsługi ustawień, które nie są dostępne w centrach aadministracyjnym z etykietami, możesz teraz w pełni skrybować tworzenie i konserwację etykiet wrażliwości i zasad wrażliwości. 

Zapoznaj się z następującą dokumentacją, aby uzyskać obsługiwane parametry i wartości:

- [New-Label](/powershell/module/exchange/new-label)
- [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy)
- [Set-Label](/powershell/module/exchange/set-label)
- [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy)

Za pomocą polecenia [Remove-Label](/powershell/module/exchange/remove-label) i [Remove-LabelPolicy](/powershell/module/exchange/remove-labelpolicy) można również utworzyć skrypt usuwania etykiet wrażliwości lub zasad wrażliwości. Jednak przed usunięciem etykiet wrażliwości należy przeczytać następującą sekcję.

## <a name="removing-and-deleting-labels"></a>Usuwanie etykiet

W środowisku produkcyjnym prawdopodobnie trzeba będzie usunąć etykiety wrażliwości z zasad wrażliwości lub usunąć etykiety wrażliwości. Jest prawdopodobne, że trzeba będzie wykonać jedną lub jedną z tych czynności na etapie testowania początkowego. Upewnij się, że rozumiesz, co się dzieje w przypadku jednej z tych akcji.

Usuwanie etykiety z zasad etykiet jest mniej ryzykowne niż usuwanie etykiet i zawsze można je później dodać z powrotem do zasad etykiet, jeśli zajdą taka potrzeba:

- Po usunięciu etykiety z zasad etykiet, tak aby etykieta nie była już opublikowana u pierwotnie określonych użytkowników, przy następnym odświeżaniu zasad etykiet użytkownicy nie będą już widzieć tej etykiety do wybrania w swoich aplikacja pakietu Office. Jednak jeśli etykieta została zastosowana do dokumentów lub wiadomości e-mail, nie zostanie ona usunięta z tej zawartości. Wszelkie szyfrowania zastosowane na etykiecie pozostają, a źródłowy szablon ochrony pozostaje opublikowany. 

- W przypadku etykiet, które zostały usunięte, ale wcześniej zastosowano do zawartości, użytkownicy, którzy mają wbudowane etykiety dla aplikacji Word, Excel i PowerPoint, nadal będą widzieć nazwę zastosowanej etykiety na pasku stanu. Podobnie etykiety, które zostały usunięte w witrynach sieci SharePoint, nadal wyświetlają nazwę etykiety w **kolumnie** Charakter.

Dla porównania: po usunięciu etykiety:

- Jeśli etykieta zastosowano szyfrowanie, źródłowy szablon ochrony jest archiwizowany, aby nadal można było otwierać wcześniej chronioną zawartość. Z powodu tego zarchiwizowanego szablonu ochrony nie będzie można utworzyć nowej etykiety o tej samej nazwie. Chociaż za pomocą programu [PowerShell](/powershell/module/aipservice/remove-aipservicetemplate) można usunąć szablon ochrony, nie należy tego robić, chyba że masz pewność, że nie musisz otwierać zawartości zaszyfrowanej za pomocą zarchiwizowanego szablonu.

- W przypadku aplikacji klasycznych: Informacje o etykietach w metadanych pozostają, ale ponieważ nie jest już możliwe mapowanie identyfikatora etykiety na nazwę, użytkownicy nie widzą zastosowanej nazwy etykiety (na przykład na pasku stanu), więc użytkownicy będą zakładać, że zawartość nie jest oznaczona etykietą. Jeśli etykieta ma zastosowane szyfrowanie, szyfrowanie pozostaje, a po otwarciu zawartości użytkownicy nadal widzą nazwę i opis obecnie zarchiwizowanego szablonu ochrony.

- Na Office w sieci Web: Użytkownicy nie widzą nazwy etykiety na pasku stanu ani w **kolumnie** Charakter. Informacje o etykietach w metadanych pozostają tylko wtedy, gdy etykieta nie zastosuje szyfrowania. Jeśli etykieta zastosowano szyfrowanie i włączono etykiety wrażliwości dla SharePoint i [OneDrive](sensitivity-labels-sharepoint-onedrive-files.md), informacje o etykietach w metadanych zostaną usunięte, a szyfrowanie zostanie usunięte. 

Usunięcie etykiety wrażliwości z zasad etykiety lub usunięcie etykiety wrażliwości może potrwać do 24 godzin, aby zreplikować ją we wszystkich użytkownikach i usługach.

## <a name="next-steps"></a>Następne kroki

Aby skonfigurować etykiety wrażliwości i używać ich w określonych scenariuszach, skorzystaj z następujących artykułów:

- [Ograniczanie dostępu do zawartości przy użyciu szyfrowania etykiet wrażliwości](encryption-sensitivity-labels.md)

- [Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md)

- [Używaj etykiet poufności z zespołami, grupami i witrynami](sensitivity-labels-teams-groups-sites.md)

- [Włącz etykiety poufności dla plików pakietu Office w programie SharePoint i usłudze OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)

Aby monitorować sposób, w jaki etykiety są używane, Wprowadzenie [z klasyfikacją danych](data-classification-overview.md).
