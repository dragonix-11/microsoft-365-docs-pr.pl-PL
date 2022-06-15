---
title: Włączanie etykiet poufności dla plików Office
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.date: ''
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Administratorzy mogą włączyć obsługę etykiet poufności dla plików programu Word, Excel i PowerPoint w SharePoint i OneDrive.
ms.openlocfilehash: 0c9ba0a72b9bd02097817bcea04bf25200fca657
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078388"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive"></a>Włącz etykiety poufności dla plików pakietu Office w programie SharePoint i usłudze OneDrive

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Włącz wbudowane etykietowanie [obsługiwanych plików Office](sensitivity-labels-office-apps.md#office-file-types-supported) w SharePoint i OneDrive, aby użytkownicy mogli stosować [etykiety poufności](sensitivity-labels.md) w Office dla sieci web. Po włączeniu tej funkcji użytkownicy zobaczą przycisk **Czułość** na wstążce, aby mogli zastosować etykiety i wyświetlić dowolną nazwę zastosowanej etykiety na pasku stanu.

Włączenie tej funkcji powoduje również, że SharePoint i OneDrive mogą przetwarzać zawartość plików Office, które zostały zaszyfrowane przy użyciu etykiety poufności. Etykietę można stosować w Office dla sieci web lub w Office aplikacjach klasycznych oraz przekazywać lub zapisywać w SharePoint i OneDrive. Do momentu włączenia tej funkcji te usługi nie mogą przetwarzać zaszyfrowanych plików, co oznacza, że współtworzenie, zbieranie elektronicznych materiałów dowodowych, Microsoft Purview zapobieganie utracie danych, wyszukiwanie i inne funkcje współpracy nie będą działać dla tych plików.

Po włączeniu etykiet poufności dla plików Office w SharePoint i OneDrive dla nowych i zmienionych plików, które mają etykietę poufności, która stosuje szyfrowanie przy użyciu klucza opartego na chmurze (i nie używa [szyfrowania podwójnego klucza](double-key-encryption.md):

- W przypadku plików programu Word, Excel i PowerPoint SharePoint i OneDrive rozpoznawać etykietę, a teraz mogą przetwarzać zawartość zaszyfrowanego pliku.

- Gdy użytkownicy pobierają te pliki lub uzyskują do nich dostęp z SharePoint lub OneDrive, etykieta poufności i wszelkie ustawienia szyfrowania z etykiety są wymuszane i pozostają w pliku, gdziekolwiek są przechowywane. Upewnij się, że udostępniasz wskazówki dla użytkowników, aby używać tylko etykiet do ochrony dokumentów. Aby uzyskać więcej informacji, zobacz [Opcje Rights Management informacji (IRM) i etykiety poufności](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels).

- Gdy użytkownicy przekazują pliki oznaczone etykietami i zaszyfrowane do SharePoint lub OneDrive, muszą mieć co najmniej prawa do wyświetlania tych plików. Na przykład mogą otwierać pliki poza SharePoint. Jeśli nie mają tego prawa do minimalnego użycia, przekazywanie zakończy się pomyślnie, ale usługa nie rozpoznaje etykiety i nie może przetworzyć zawartości pliku.

- Użyj programu Office dla sieci web (Word, Excel, PowerPoint), aby otwierać i edytować pliki Office z etykietami poufności, które stosują szyfrowanie. Uprawnienia przypisane przy użyciu szyfrowania są wymuszane. Możesz również użyć [automatycznego etykietowania](apply-sensitivity-label-automatically.md) dla tych dokumentów.

- Użytkownicy zewnętrzni mogą uzyskiwać dostęp do dokumentów oznaczonych etykietą szyfrowania przy użyciu kont gościa. Aby uzyskać więcej informacji, zobacz [Pomoc techniczna dla użytkowników zewnętrznych i zawartość oznaczona etykietami](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Office 365 eDiscovery obsługuje wyszukiwanie pełnotekstowe dla tych plików, a zasady ochrony przed utratą danych (DLP) obsługują zawartość w tych plikach.

> [!NOTE]
> Jeśli szyfrowanie zostało zastosowane przy użyciu klucza lokalnego (topologia zarządzania kluczami często określana jako "hold your own key" lub HYOK) lub przy użyciu [szyfrowania podwójnym kluczem](double-key-encryption.md), zachowanie usługi do przetwarzania zawartości pliku nie ulega zmianie. Dlatego w przypadku tych plików współtworzenie, zbieranie elektronicznych materiałów dowodowych, zapobieganie utracie danych, wyszukiwanie i inne funkcje współpracy nie będą działać.
>
> Zachowanie SharePoint i OneDrive również nie zmienia się w przypadku istniejących plików w tych lokalizacjach, które są oznaczone etykietą szyfrowania przy użyciu jednego klucza opartego na platformie Azure. Aby te pliki korzystały z nowych możliwości po włączeniu etykiet poufności dla Office plików w SharePoint i OneDrive, pliki muszą zostać pobrane i przekazane ponownie lub edytowane.

Po włączeniu etykiet poufności dla plików Office w SharePoint i OneDrive dostępne są trzy nowe [zdarzenia inspekcji](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) na potrzeby monitorowania etykiet poufności stosowanych do dokumentów w SharePoint i OneDrive:

- **Zastosowana etykieta poufności do pliku**
- **Zmieniono etykietę poufności stosowaną do pliku**
- **Usunięto etykietę poufności z pliku**

Obejrzyj następujące wideo (bez dźwięku), aby zobaczyć nowe możliwości w działaniu:

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

Zawsze masz możliwość wyłączenia etykiet poufności dla Office plików w SharePoint i OneDrive ([rezygnacja](#how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out)) w dowolnym momencie.

Jeśli obecnie chronisz dokumenty w SharePoint przy użyciu SharePoint Information Rights Management (IRM), sprawdź [sekcję SharePoint Information Rights Management (IRM) i etykiety poufności](#sharepoint-information-rights-management-irm-and-sensitivity-labels) na tej stronie.

## <a name="requirements"></a>Wymagania

Te nowe możliwości działają tylko z [etykietami poufności](sensitivity-labels.md) . Jeśli obecnie masz etykiety usługi Azure Information Protection, najpierw zmigruj je do etykiet poufności, aby umożliwić włączenie tych funkcji dla nowych przekazanych plików. Aby uzyskać [instrukcje, zobacz How to migrate Azure Information Protection labels to unified sensitivity labels (Jak migrować etykiety usługi Azure Information Protection do ujednoliconych etykiet poufności](/azure/information-protection/configure-policy-migrate-labels)).

Użyj aplikacji synchronizacja usługi OneDrive w wersji 19.002.0121.0008 lub nowszej w Windows i wersji 19.002.0107.0008 lub nowszej na komputerze Mac. Obie te wersje zostały wydane 28 stycznia 2019 r. i są obecnie dostępne dla wszystkich pierścieni. Aby uzyskać więcej informacji, zobacz [informacje o wersji OneDrive](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0). Po włączeniu etykiet poufności dla plików Office w SharePoint i OneDrive użytkownicy, którzy uruchamiają starszą wersję aplikacji synchronizacji, zostaną poproszeni o jej zaktualizowanie.

## <a name="limitations"></a>Ograniczenia

- SharePoint i OneDrive nie mogą przetwarzać plików, które są oznaczone etykietami i szyfrowane z Office aplikacji klasycznych, gdy te pliki zawierają dane powerquery, dane przechowywane przez dodatki niestandardowe lub niestandardowe części XML, takie jak właściwości strony tytułowej, schematy typów zawartości, niestandardowy panel informacji o dokumencie i niestandardowa nazwa XSN. To ograniczenie dotyczy również plików zawierających [bibliografię](https://support.microsoft.com/en-us/office/create-a-bibliography-citations-and-references-17686589-4824-4940-9c69-342c289fa2a5) oraz plików z [identyfikatorem dokumentu](https://support.microsoft.com/office/enable-and-configure-unique-document-ids-ea7fee86-bd6f-4cc8-9365-8086e794c984) dodanym podczas przekazywania.

    W przypadku tych plików zastosuj etykietę bez szyfrowania, aby później można je było otworzyć w Office w sieci Web, lub poproś użytkowników o otwarcie plików w aplikacjach klasycznych. Nie ma to wpływu na pliki oznaczone etykietami i szyfrowane tylko w Office w sieci Web.

- SharePoint i OneDrive nie stosują automatycznie etykiet poufności do istniejących plików, które zostały już zaszyfrowane przy użyciu etykiet usługi Azure Information Protection. Zamiast tego, aby funkcje działały po włączeniu etykiet poufności dla plików Office w SharePoint i OneDrive, wykonaj następujące zadania:

    1. Upewnij się, że [zmigrowano etykiety usługi Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels) do etykiet poufności i [opublikowano je](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) z portal zgodności Microsoft Purview.
    2. Pobierz pliki oznaczone etykietą, a następnie przekaż je do oryginalnej lokalizacji w SharePoint lub OneDrive.

- SharePoint i OneDrive nie mogą przetwarzać zaszyfrowanych plików, gdy etykieta, która zastosowała szyfrowanie, ma dowolną z [następujących konfiguracji szyfrowania](encryption-sensitivity-labels.md#configure-encryption-settings):
  - **Zezwalaj użytkownikom na przypisywanie uprawnień, gdy zastosują etykietę** i pole wyboru **W programie Word, PowerPoint i Excel, zostanie wybrany monit o określenie uprawnień**. To ustawienie jest czasami określane jako "uprawnienia zdefiniowane przez użytkownika".
  - **Dostęp użytkownika do zawartości wygasa** jest ustawiony na wartość inną niż **Nigdy**.
  - **Wybrano opcję Podwójne szyfrowanie kluczy** .

    W przypadku etykiet z żadną z tych konfiguracji szyfrowania etykiety nie są wyświetlane użytkownikom w Office dla sieci web. Ponadto nowych możliwości nie można używać z dokumentami z etykietami, które mają już te ustawienia szyfrowania. Na przykład te dokumenty nie zostaną zwrócone w wynikach wyszukiwania, nawet jeśli zostaną zaktualizowane.

- Ze względu na wydajność podczas przekazywania lub zapisywania dokumentu do SharePoint, a etykieta pliku nie stosuje szyfrowania, **kolumna Poufności** w bibliotece dokumentów może trochę potrwać, aby wyświetlić nazwę etykiety. Uwzględnij to opóźnienie, jeśli używasz skryptów lub automatyzacji, które zależą od nazwy etykiety w tej kolumnie.

- Jeśli dokument jest oznaczony etykietą podczas [wyewidencjonowania w SharePoint](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de), **kolumna Poufność** w bibliotece dokumentów nie będzie wyświetlać nazwy etykiety, dopóki dokument nie zostanie zaewidencjonowany i otwarty w SharePoint.

- Jeśli dokument oznaczony etykietą i zaszyfrowany jest pobierany z SharePoint lub OneDrive przez aplikację lub usługę używającą głównej nazwy usługi, a następnie przekazany ponownie z etykietą, która stosuje różne ustawienia szyfrowania, przekazywanie zakończy się niepowodzeniem. Przykładowy scenariusz to Microsoft Defender for Cloud Apps zmienia etykietę poufności w pliku z **Poufne** na **Wysoce poufne** lub **Poufne** na **Ogólne**.

    Przekazywanie nie kończy się niepowodzeniem, jeśli aplikacja lub usługa najpierw uruchomi polecenie cmdlet [Unlock-SPOSensitivityLabelEncryptedFile, jak wyjaśniono](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) w sekcji [Usuwanie szyfrowania dla oznaczonego dokumentu](#remove-encryption-for-a-labeled-document) . Lub przed przekazaniem oryginalny plik zostanie usunięty lub nazwa pliku zostanie zmieniona.

- Użytkownicy mogą mieć opóźnienia w otwieraniu zaszyfrowanych dokumentów w następującym scenariuszu Zapisz jako: Korzystając z klasycznej wersji Office, użytkownik wybiera pozycję Zapisz jako dla dokumentu z etykietą poufności, która stosuje szyfrowanie. Użytkownik wybiera SharePoint lub OneDrive dla lokalizacji, a następnie natychmiast próbuje otworzyć ten dokument w Office dla sieci web. Jeśli usługa nadal przetwarza szyfrowanie, użytkownik zobaczy komunikat, że dokument musi zostać otwarty w aplikacji klasycznej. Jeśli spróbują ponownie za kilka minut, dokument zostanie pomyślnie otwarty w Office dla sieci web.

- W przypadku zaszyfrowanych dokumentów drukowanie nie jest obsługiwane w Office dla sieci web.

- W przypadku zaszyfrowanych dokumentów w Office dla sieci web kopiowanie do schowka i przechwytywania ekranu nie jest niemożliwe. Aby uzyskać więcej informacji, zobacz [Czy Rights Management zapobiegać przechwytywaniu ekranu?](/azure/information-protection/faqs-rms#can-rights-management-prevent-screen-captures)

- Domyślnie Office aplikacje klasyczne i aplikacje mobilne nie obsługują współtworzenia plików oznaczonych etykietą szyfrowania. Te aplikacje nadal otwierają pliki oznaczone etykietami i zaszyfrowane w trybie edycji wyłącznej.

    > [!NOTE]
    > Współtworzenie jest teraz obsługiwane w przypadku Windows i macOS oraz w wersji zapoznawczej dla iOS i Android. Aby uzyskać więcej informacji, zobacz [Enable co-authoring for files encrypted with sensitivity labels (Włączanie współtworzynia plików zaszyfrowanych przy użyciu etykiet poufności](sensitivity-labels-coauthoring.md)).

- Jeśli administrator zmieni ustawienia opublikowanej etykiety, która jest już stosowana do plików pobranych do klienta synchronizacji użytkowników, użytkownicy mogą nie być w stanie zapisać zmian wprowadzonych w pliku w folderze OneDrive Sync. Ten scenariusz dotyczy plików oznaczonych etykietą szyfrowania, a także gdy zmiana etykiety pochodzi z etykiety, która nie zastosowała szyfrowania do etykiety, która stosuje szyfrowanie. Użytkownicy widzą [czerwony okrąg z błędem białej ikony krzyżowej](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3) i są proszeni o zapisanie nowych zmian jako oddzielnej kopii. Zamiast tego mogą zamknąć i ponownie otworzyć plik lub użyć Office dla sieci web.

- Użytkownicy mogą napotkać problemy z zapisywaniem po przejściu w tryb offline lub w tryb uśpienia, gdy zamiast korzystać z Office dla sieci web, używają aplikacji klasycznych i mobilnych dla programu Word, Excel lub PowerPoint. W przypadku tych użytkowników po wznowieniu sesji aplikacja pakietu Office i próbie zapisania zmian zostanie wyświetlony komunikat o niepowodzeniu przekazywania z opcją zapisania kopii zamiast zapisywania oryginalnego pliku.

- W Office dla sieci web nie można otwierać dokumentów zaszyfrowanych w następujący sposób:
  - Szyfrowanie używające klucza lokalnego ("hold your own key" lub HYOK)
  - Szyfrowanie zastosowane przy użyciu [szyfrowania podwójnego klucza](double-key-encryption.md)
  - Szyfrowanie, które zostało zastosowane niezależnie od etykiety, na przykład przez bezpośrednie zastosowanie szablonu ochrony Rights Management.

- Etykiety skonfigurowane dla [innych języków](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-powershell) nie są obsługiwane i wyświetlają tylko oryginalny język.

- Jeśli usuniesz etykietę, która została zastosowana do dokumentu w SharePoint lub OneDrive, zamiast usuwać etykietę z odpowiednich zasad etykiet, pobrany dokument nie zostanie oznaczony etykietą ani zaszyfrowany. Dla porównania, jeśli dokument z etykietą jest przechowywany poza SharePoint lub OneDrive, dokument pozostaje zaszyfrowany, jeśli etykieta zostanie usunięta. Należy pamiętać, że chociaż etykiety można usunąć w fazie testowania, bardzo rzadko można usunąć etykietę w środowisku produkcyjnym.

## <a name="how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in"></a>Jak włączyć etykiety poufności dla SharePoint i OneDrive (zgoda)

Nowe możliwości można włączyć przy użyciu portal zgodności Microsoft Purview lub programu PowerShell. Podobnie jak w przypadku wszystkich zmian konfiguracji na poziomie dzierżawy dla SharePoint i OneDrive, wprowadzenie zmiany trwa około 15 minut.

### <a name="use-the-microsoft-purview-compliance-portal-to-enable-support-for-sensitivity-labels"></a>Użyj portal zgodności Microsoft Purview, aby włączyć obsługę etykiet poufności

Ta opcja jest najprostszym sposobem włączenia etykiet poufności dla SharePoint i OneDrive, ale musisz zalogować się jako administrator globalny dzierżawy.

1. Zaloguj się do [portal zgodności Microsoft Purview](https://compliance.microsoft.com/) jako administrator globalny i przejdź do pozycji **Etykiety** **ochrony** >  informacji **rozwiązania** > 

2. Jeśli zostanie wyświetlony komunikat umożliwiający włączenie możliwości przetwarzania zawartości w Office plikach online, wybierz pozycję **Włącz teraz**:

    ![Włącz teraz przycisk , aby włączyć etykiety poufności dla Office Online.](../media/sensitivity-labels-turn-on-banner.png)

    Polecenie zostanie uruchomione natychmiast, a po następnym odświeżeniu strony nie będzie już widoczny komunikat ani przycisk.

> [!NOTE]
> Jeśli masz Microsoft 365 multi-geo, musisz użyć programu PowerShell, aby włączyć te możliwości dla wszystkich lokalizacji geograficznych. Aby uzyskać szczegółowe informacje, zobacz następną sekcję.

### <a name="use-powershell-to-enable-support-for-sensitivity-labels"></a>Używanie programu PowerShell do włączania obsługi etykiet poufności

Alternatywnie do używania portal zgodności Microsoft Purview można włączyć obsługę etykiet poufności przy użyciu polecenia cmdlet [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) z programu PowerShell usługi SharePoint Online.

Jeśli masz Microsoft 365 multi-geo, musisz użyć programu PowerShell, aby włączyć tę obsługę wszystkich lokalizacji geograficznych.

#### <a name="prepare-the-sharepoint-online-management-shell"></a>Przygotowywanie powłoki zarządzania SharePoint Online

Przed uruchomieniem polecenia programu PowerShell, aby włączyć etykiety poufności dla plików Office w SharePoint i OneDrive, upewnij się, że używasz programu SharePoint Online Management Shell w wersji 16.0.19418.12000 lub nowszej. Jeśli masz już najnowszą wersję, możesz przejść do [następnej procedury](#run-the-powershell-command-to-enable-support-for-sensitivity-labels) , aby uruchomić polecenie programu PowerShell.

1. Jeśli zainstalowano poprzednią wersję powłoki zarządzania usługi SharePoint Online z galerii programu PowerShell, możesz zaktualizować moduł, uruchamiając następujące polecenie cmdlet.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. Alternatywnie, jeśli zainstalowano poprzednią wersję powłoki zarządzania SharePoint Online z Centrum pobierania Microsoft, możesz również przejść do obszaru **Dodawanie lub usuwanie programów** i odinstalować powłokę zarządzania SharePoint Online.

3. W przeglądarce internetowej przejdź do strony Centrum pobierania i [pobierz najnowszą powłokę zarządzania SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251).

4. Wybierz swój język, a następnie kliknij pozycję **Pobierz**.

5. Wybierz między plikiem .msi x64 i x86. Pobierz plik x64, jeśli uruchomisz 64-bitową wersję Windows lub plik x86, jeśli zostanie uruchomiona wersja 32-bitowa. Jeśli nie wiesz, zobacz[, która wersja systemu operacyjnego Windows jest uruchomiona?](https://support.microsoft.com/help/13443/windows-which-operating-system)

6. Po pobraniu pliku uruchom plik i wykonaj kroki opisane w Kreatorze instalacji.

#### <a name="run-the-powershell-command-to-enable-support-for-sensitivity-labels"></a>Uruchom polecenie programu PowerShell, aby włączyć obsługę etykiet poufności

Aby włączyć nowe możliwości, użyj polecenia cmdlet [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) z parametrem *EnableAIPIntegration* :

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego lub administratora SharePoint w Microsoft 365, połącz się z SharePoint. Aby dowiedzieć się, jak to zrobić, zobacz [Wprowadzenie do usługi SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

    > [!NOTE]
    > Jeśli masz Microsoft 365 Multi-Geo, użyj parametru -Url z [Połączenie-SPOService](/powershell/module/sharepoint-online/connect-sposervice) i określ adres URL witryny centrum administracji online SharePoint dla jednej z lokalizacji geograficznych.

2. Uruchom następujące polecenie i naciśnij **klawisz Y,** aby potwierdzić:

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true
    ```
3. W przypadku Microsoft 365 Multi-Geo: powtórz kroki 1 i 2 dla każdej z pozostałych lokalizacji geograficznych.

## <a name="publishing-and-changing-sensitivity-labels"></a>Publikowanie i zmienianie etykiet poufności

W przypadku używania etykiet poufności z SharePoint i OneDrive należy pamiętać, że należy zezwolić na czas replikacji podczas publikowania nowych etykiet poufności lub aktualizowania istniejących etykiet poufności. Jest to szczególnie ważne w przypadku nowych etykiet, które stosują szyfrowanie.

Na przykład: tworzysz i publikujesz nową etykietę poufności, która stosuje szyfrowanie i bardzo szybko pojawia się w aplikacji klasycznej użytkownika. Użytkownik stosuje tę etykietę do dokumentu, a następnie przekazuje ją do SharePoint lub OneDrive. Jeśli replikacja etykiet nie została ukończona dla usługi, nowe możliwości nie zostaną zastosowane do tego dokumentu podczas przekazywania. W związku z tym dokument nie zostanie zwrócony podczas wyszukiwania ani zbierania elektronicznych materiałów dowodowych, a dokumentu nie można otworzyć w Office dla sieci web.

Aby uzyskać więcej informacji na temat czasu etykiet, zobacz [When to expect new labels and changes to take effect (Kiedy można oczekiwać wprowadzenia nowych etykiet i zmian](create-sensitivity-labels.md#when-to-expect-new-labels-and-changes-to-take-effect)).

Jako zabezpieczenie zalecamy publikowanie nowych etykiet tylko dla kilku użytkowników testowych, odczekanie co najmniej jednej godziny, a następnie zweryfikowanie zachowania etykiet na SharePoint i OneDrive. Poczekaj co najmniej dzień, zanim etykieta będzie dostępna dla większej liczby użytkowników, dodając więcej użytkowników do istniejących zasad etykiet lub dodając etykietę do istniejących zasad etykiet dla użytkowników standardowych. Gdy użytkownicy standardowi zobaczą etykietę, została ona już zsynchronizowana z SharePoint i OneDrive.

## <a name="sharepoint-information-rights-management-irm-and-sensitivity-labels"></a>SharePoint Etykiety informacji Rights Management (IRM) i poufności

[SharePoint Information Rights Management (IRM)](set-up-irm-in-sp-admin-center.md) to starsza technologia do ochrony plików na poziomie listy i biblioteki przez zastosowanie szyfrowania i ograniczeń podczas pobierania plików. Ta starsza technologia ochrony została zaprojektowana tak, aby uniemożliwić nieautoryzowanym użytkownikom otwieranie pliku, gdy znajduje się on poza SharePoint.

Dla porównania etykiety poufności zapewniają ustawienia ochrony oznaczeń wizualnych (nagłówków, stopek, znaków wodnych) oprócz szyfrowania. Ustawienia szyfrowania obsługują pełny zakres [praw użytkowania](/azure/information-protection/configure-usage-rights) , aby ograniczyć możliwości użytkowników związane z zawartością, a te same etykiety poufności są obsługiwane w [wielu scenariuszach](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). Użycie tej samej metody ochrony ze spójnymi ustawieniami w obciążeniach i aplikacjach skutkuje spójną strategią ochrony.

Można jednak używać zarówno rozwiązań ochrony, jak i zachowania w następujący sposób:

- Jeśli przekażesz plik z etykietą poufności, która stosuje szyfrowanie, SharePoint nie może przetworzyć zawartości tych plików, więc współtworzenie, wykrywanie elektroniczne, DLP i wyszukiwanie nie są obsługiwane dla tych plików.

- W przypadku etykietowania pliku przy użyciu Office dla sieci web wymuszane są wszelkie ustawienia szyfrowania z etykiety. W przypadku tych plików obsługiwane są współtworzenie, wykrywanie elektroniczne, DLP i wyszukiwanie.

- Jeśli pobierzesz plik oznaczony etykietą przy użyciu Office dla sieci web, etykieta zostanie zachowana, a wszystkie ustawienia szyfrowania z etykiety zostaną wymuszone, a nie ustawienia ograniczeń usługi IRM.

- Jeśli pobierzesz plik Office lub PDF, który nie jest zaszyfrowany za pomocą etykiety poufności, zostaną zastosowane ustawienia usługi IRM.

- Jeśli włączono dowolne z dodatkowych ustawień biblioteki IRM, które obejmują uniemożliwianie użytkownikom przekazywania dokumentów, które nie obsługują usługi IRM, te ustawienia są wymuszane.

Dzięki temu zachowaniu można mieć pewność, że wszystkie pliki Office i PDF są chronione przed nieautoryzowanym dostępem, jeśli zostaną pobrane, nawet jeśli nie są oznaczone etykietą. Jednak pliki oznaczone etykietami, które są przekazywane, nie będą korzystać z nowych możliwości.

## <a name="search-for-documents-by-sensitivity-label"></a>Wyszukiwanie dokumentów według etykiety poufności

Użyj właściwości zarządzanej **InformationProtectionLabelId**, aby znaleźć wszystkie dokumenty w SharePoint lub OneDrive, które mają określoną etykietę poufności. Użyj następującej składni: `InformationProtectionLabelId:<GUID>`

Aby na przykład wyszukać wszystkie dokumenty oznaczone jako "Poufne", a etykieta ma identyfikator GUID "8faca7b8-8d20-48a3-8ea2-0f96310a848e", w polu wyszukiwania wpisz:

```
InformationProtectionLabelId:8faca7b8-8d20-48a3-8ea2-0f96310a848e
```

Wyszukiwanie nie będzie znajdować dokumentów oznaczonych etykietami w skompresowanym pliku, takim jak plik .zip.

Aby uzyskać identyfikatory GUID etykiet poufności, użyj polecenia cmdlet [Get-Label](/powershell/module/exchange/get-label) :

1. Najpierw [połącz się z programem PowerShell Office 365 Security & Compliance](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

    Na przykład w sesji programu PowerShell uruchamianej jako administrator zaloguj się przy użyciu konta administratora globalnego.

2. Następnie uruchom następujące polecenie:

    ```powershell
    Get-Label |ft Name, Guid
    ```

Aby uzyskać więcej informacji na temat korzystania z właściwości zarządzanych, zobacz [Zarządzanie schematem wyszukiwania w SharePoint](/sharepoint/manage-search-schema).

## <a name="remove-encryption-for-a-labeled-document"></a>Usuwanie szyfrowania dla dokumentu oznaczonego etykietą

Mogą wystąpić rzadkie sytuacje, gdy administrator SharePoint musi usunąć szyfrowanie z dokumentu przechowywanego w SharePoint. Każdy użytkownik, który ma [przypisane Rights Management prawa użytkowania](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) programu Export lub Full Control dla tego dokumentu, może usunąć szyfrowanie zastosowane przez usługę Azure Rights Management z usługi Azure Information Protection. Na przykład użytkownicy z dowolną z tych praw użytkowania mogą zastąpić etykietę, która stosuje szyfrowanie etykietą bez szyfrowania. [Administrator](/azure/information-protection/configure-super-users) może również pobrać plik i zapisać kopię lokalną bez szyfrowania.

Alternatywnie administrator globalny lub [administrator SharePoint](/sharepoint/sharepoint-admin-role) może uruchomić polecenie cmdlet [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile), które usuwa zarówno etykietę poufności, jak i szyfrowanie. To polecenie cmdlet jest uruchamiane nawet wtedy, gdy administrator nie ma uprawnień dostępu do witryny lub pliku lub jeśli usługa Azure Rights Management jest niedostępna.

Przykład:

```powershell
Unlock-SPOSensitivityLabelEncryptedFile -FileUrl "https://contoso.com/sites/Marketing/Shared Documents/Doc1.docx" -JustificationText "Need to decrypt this file"
```

Wymagania:

- SharePoint powłoki zarządzania online w wersji 16.0.20616.12000 lub nowszej.

- Szyfrowanie zostało zastosowane przez etykietę poufności z ustawieniami szyfrowania zdefiniowanymi przez administratora (ustawienia [przypisz uprawnienia teraz](encryption-sensitivity-labels.md#assign-permissions-now) etykiety). [Szyfrowanie podwójnym kluczem](encryption-sensitivity-labels.md#double-key-encryption) nie jest obsługiwane dla tego polecenia cmdlet.

Tekst uzasadnienia jest dodawany do [zdarzenia inspekcji](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) **Usunięto etykietę poufności z pliku**, a akcja odszyfrowywania jest również rejestrowana w [rejestrowaniu użycia ochrony dla usługi Azure Information Protection](/azure/information-protection/log-analyze-usage).

## <a name="how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out"></a>Jak wyłączyć etykiety poufności dla SharePoint i OneDrive (rezygnacja)

Jeśli wyłączysz te nowe możliwości, pliki przekazane po włączeniu etykiet poufności dla SharePoint i OneDrive nadal będą chronione przez etykietę, ponieważ ustawienia etykiety będą nadal wymuszane. Po zastosowaniu etykiet poufności do nowych plików po wyłączeniu tych nowych możliwości wyszukiwanie pełnotekstowe, pozyskiwanie elektronicznych materiałów dowodowych i współtworzenie nie będzie już działać.

Aby wyłączyć te nowe możliwości, należy użyć programu PowerShell. Za pomocą powłoki zarządzania usługi SharePoint Online i polecenia cmdlet [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) określ ten sam parametr *EnableAIPIntegration* zgodnie z opisem w sekcji [Używanie programu PowerShell do włączania obsługi etykiet poufności](#use-powershell-to-enable-support-for-sensitivity-labels). Ale tym razem ustaw wartość parametru na false i naciśnij **klawisz Y** , aby potwierdzić:

```PowerShell
Set-SPOTenant -EnableAIPIntegration $false
```

Jeśli masz Microsoft 365 Multi-Geo, musisz uruchomić to polecenie dla każdej lokalizacji geograficznej.

## <a name="next-steps"></a>Następne kroki

Po włączeniu etykiet poufności dla plików Office w SharePoint i OneDrive rozważ automatyczne etykietowanie tych plików przy użyciu zasad automatycznego etykietowania. Aby uzyskać więcej informacji, zobacz [Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md).

Chcesz udostępnić dokumenty oznaczone etykietami i zaszyfrowane osobom spoza organizacji?  Zobacz [Udostępnianie zaszyfrowanych dokumentów użytkownikom zewnętrznym](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
