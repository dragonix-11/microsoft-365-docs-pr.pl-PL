---
title: Określanie, czy scentralizowane wdrażanie dodatków działa w Twojej organizacji
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
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b4527d49-4073-4b43-8274-31b7a3166f92
description: Określ, czy dzierżawa i użytkownicy spełniają wymagania, aby można było używać funkcji scentralizowanego wdrażania Office dodatków.
ms.openlocfilehash: 4a64a9dd9a15c9bc877288aa9ac8fc62c40cee51
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019255"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>Określanie, czy scentralizowane wdrażanie dodatków działa w Twojej organizacji

Scentralizowane wdrażanie jest zalecaną dla większości klientów, najbogatszą w funkcje sposobem wdrażania dodatków Office u użytkowników i grup w organizacji. Jeśli jesteś administratorem, użyj tych wskazówek, aby określić, czy Twoja organizacja i użytkownicy spełniają wymagania dotyczące korzystania z funkcji scentralizowanego wdrażania.

Scentralizowane wdrażanie zapewnia następujące korzyści:

- Administrator może wdrożyć i przypisać dodatek bezpośrednio do użytkownika, do wielu użytkowników za pośrednictwem grupy lub do wszystkich osób w organizacji (zobacz sekcję Wymagania administratora, aby uzyskać informacje).

- Gdy zostanie uruchomiony odpowiedni Office, dodatek zostanie automatycznie pobrany. Jeśli dodatek obsługuje polecenia dodatku, automatycznie pojawi się na wstążce w Office aplikacji.

- Dodatki nie są już wyświetlane dla użytkowników, jeśli administrator wyłączy lub usunie dodatek albo jeśli został on usunięty z programu Azure Active Directory lub z grupy, do których został przypisany.

Scentralizowane wdrażanie obsługuje trzy platformy klasyczne, Windows komputerów Mac oraz aplikacje online Office komputerów Mac. Scentralizowane wdrażanie obsługuje również systemy iOS i Android (Outlook tylko dodatki dla urządzeń przenośnych).

Może upłynąć do 24 godzin, aż dodatek będzie widoczny u klienta dla wszystkich użytkowników.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Scentralizowane wdrażanie dodatków wymaga, aby użytkownicy korzystali z licencji usług Microsoft 365 Business (Business Basic, Business Standard, Business Premium), Office 365 Enterprise (E1/E3/E5/F3) lub Microsoft 365 Enterprise (E3/E5/F3) (i są zalogowani Office identyfikator organizacji), licencje Office 365 Education (A1/A3/A5) lub licencje Microsoft 365 Education (A3/A5) oraz mają Exchange Online i aktywne Exchange Online pocztowe. Katalog subskrypcji musi być w organizacji lub w federacji z Azure Active Directory.
Możesz sprawdzić konkretne wymagania dotyczące funkcji Office i Exchange lub skorzystać z funkcji sprawdzania zgodności funkcji Scentralizowane [wdrażanie](#centralized-deployment-compatibility-checker).

W ramach funkcji scentralizowanego wdrażania nie są obsługiwane następujące elementy:

- Dodatki, które są kierowane do Office MSI (z wyjątkiem Outlook 2016)
- Lokalna usługa katalogowa
- Wdrażanie dodatków do skrzynki Exchange w konfiguracji wstępnej
- Wdrażanie dodatków do programu SharePoint
- Teams aplikacji
- Wdrażanie dodatków COM (Component Object Model) i Visual Studio Tools dla pakietu Office (VSTO)
- Wdrożenia usług Microsoft 365, które nie obejmują Exchange Online, takie jak jednostki SKU: Aplikacje Microsoft 365 dla firm i Aplikacje Microsoft 365 dla Enterprise.

### <a name="office-requirements"></a>Office wymagania

- W przypadku Excel, dodatków PowerPoint i innych aplikacji użytkownicy muszą korzystać z jednej z następujących usług:
  - Na Windows, w wersji 1704 lub nowszej licencji programu Microsoft 365 Business (Business Basic, Business Standard, Business Premium), Office 365 Enterprise (E1/E3/E5/F3) lub Microsoft 365 Enterprise (E3/E5/F3).
  - Na komputerze Mac w wersji 15.34 lub nowszej.

- Na Outlook użytkownicy muszą korzystać z jednej z następujących usług:
  - Wersja 1701 lub nowsza z licencji programu Microsoft 365 Business (Business Basic, Business Standard, Business Premium), Office 365 Enterprise (E1/E3/E5/F3) lub Microsoft 365 Enterprise (E3/E5/F3).
  - Wersja 1808 lub nowsza z Office Professional Plus 2019 lub Office Standard 2019.
  - Wersja 16.0.4494.1000 lub nowsza Office Professional Plus 2016 (MSI) lub Office Standard 2016 (MSI)\*
  - Wersja 15.0.4937.1000 lub nowsza z Office Professional Plus 2013 (MSI) lub Office Standard 2013 (MSI)\*
  - Wersja 16.0.9318.1000 lub nowsza z Office 2016 dla komputerów Mac
- Wersja 2.75.0 lub nowsza pakietu Outlook dla systemu iOS
- Wersja 2.2.145 lub nowsza pakietu Outlook dla systemu Android

    *Wersje MSI programu Outlook dodatki zainstalowane przez administratora na odpowiedniej wstążce programu Outlook, a nie w sekcji "Moje dodatki".

### <a name="exchange-online-requirements"></a>Exchange Online wymagań

Manifesty dodatków są przechowywane przez program Microsoft Exchange w dzierżawie organizacji. Administrator wdrażający dodatki i użytkownicy otrzymujący te dodatki muszą znajdować się w wersji programu Exchange Online obsługującej uwierzytelnianie OAuth.

Skontaktuj się z administratorem programu Exchange w organizacji, aby dowiedzieć się, jaka konfiguracja jest używana. Łączność protokołu OAuth dla poszczególnych użytkowników można sprawdzić przy użyciu polecenia cmdlet [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) programu PowerShell.

### <a name="admin-requirements"></a>Wymagania administratora

Aby wdrożyć dodatek za pośrednictwem scentralizowanego wdrażania, musisz być administratorem globalnym lub administratorem Exchange w organizacji.

> [!NOTE]
> Administrator Exchange aplikacji może wdrożyć dodatek, jeśli dodano rolę **Administratora** aplikacji lub jeśli dla właściwości Rejestracja aplikacji ustawiono wartość true w centrum Azure Active Directory administracyjnym aplikacji, jak pokazano na poniższej ilustracji:
>
> ![obraz](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)


### <a name="centralized-deployment-compatibility-checker"></a>Sprawdzanie zgodności w ramach scentralizowanego wdrażania

Za pomocą narzędzia sprawdzania zgodności funkcji Scentralizowane wdrażanie możesz sprawdzić, czy użytkownicy w Twojej dzierżawie są skonfigurowani do korzystania z funkcji Scentralizowane wdrażanie dla programów Word, Excel i PowerPoint. Narzędzie sprawdzania zgodności nie jest wymagane na potrzeby obsługi programu Outlook. Pobierz sprawdzanie [zgodności](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).

#### <a name="run-the-compatibility-checker"></a>Uruchamianie sprawdzania zgodności

1. Otwórz okno programu PowerShell.exe z podwyższonym poziomem uprawnień.

2. Uruchom następujące polecenie:

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. Uruchom polecenie **Invoke-CompatabilityCheck** :

   ```powershell
   Invoke-CompatibilityCheck
   ```
   To polecenie monituje o  *_polecenie TenantDomain_* (na przykład *TailspinToysIncorporated.onmicrosoft).</span> com*) i  *_TenantAdmin_* (użyj poświadczeń administratora globalnego), a następnie zażąda zgody.

   > [!NOTE]
   > W zależności od liczby użytkowników w dzierżawie narzędzie sprawdzania może ukończyć pracę w ciągu kilku minut lub godzin. 
  
Gdy narzędzie zakończy pracę, utworzy plik wyjściowy w formacie CSV. Plik jest domyślnie zapisywany **w bieżącym katalogu** roboczym. Plik wyjściowy zawiera następujące informacje:

- Nazwa użytkownika

- Identyfikator użytkownika (adres e-mail użytkownika)

- Gotowość do używania funkcji Scentralizowane wdrażanie  jeśli pozostałe punkty są prawdziwe

- Office plan — plan Office licencji na

- Aktywowany pakiet Office  jeśli pakiet Office został aktywowany

- Obsługiwana skrzynka pocztowa  jeśli skrzynka pocztowa obsługuje protokół OAuth

> [!NOTE]
> Uwierzytelnianie wieloskładnikowe nie jest obsługiwane w przypadku korzystania z modułu programu PowerShell dla wdrożenia centralnego. Ten moduł działa tylko w przypadku uwierzytelniania podstawowego.

## <a name="user-and-group-assignments"></a>Przypisania użytkowników i grup

Funkcja scentralizowanego wdrażania obsługuje obecnie większość grup obsługiwanych przez program Azure Active Directory, w tym grupy Microsoft 365, listy dystrybucyjne i grupy zabezpieczeń.

> [!NOTE]
> Grupy bez włączonej obsługi poczty nie są obecnie obsługiwane.

Scentralizowane wdrażanie obsługuje przypisania do poszczególnych użytkowników, grup i wszystkich osób w dzierżawie. W ramach funkcji scentralizowanego wdrażania są obsługiwani użytkownicy w grupach najwyższego poziomu, czyli niemających grupy nadrzędnej, natomiast użytkownicy w grupach zagnieżdżonych, czyli należących do grupy nadrzędnej, nie są obsługiwani.

Zapoznaj się z następującym przykładem, w którym do dodatku przypisano Anetę, Joannę oraz grupę Dział sprzedaży. Ponieważ Dział sprzedaży Zachód jest grupą zagnieżdżoną, Wojciech i Tomasz nie są przypisani do dodatku.

![MicrosoftTeams-image](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)


### <a name="find-out-if-a-group-contains-nested-groups"></a>Określanie, czy grupa zawiera grupy zagnieżdżone

Najłatwiejszym sposobem określenia, czy grupa zawiera grupy zagnieżdżone, jest wyświetlenie wizytówki grupy w programie Outlook. Jeśli w polu Do wiadomości e-mail  zostanie wprowadzeniu nazwy grupy, a następnie podczas jej rozpoznawania wybierzesz jej nazwę, będzie ona pokazywana, czy zawiera użytkowników lub grupy zagnieżdżone. W poniższym przykładzie karta **Członkowie** wizytówki grupy Test w programie Outlook nie zawiera użytkowników, ale zawiera dwie podgrupy.

![Karta Członkowie na Outlook wizytówki.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Można także przeprowadzić wyszukiwanie odwrotnie, sprawdzając, czy dana grupa należy do innej grupy. W poniższym przykładzie na karcie **Członkostwo** wizytówki grupy Podgrupa 1 w programie Outlook widać, że należy ona do grupy Test.

![Karta Członkostwo na Outlook wizytówki.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Możesz także użyć interfejsu API Graph w usłudze Azure Active Directory, aby uruchomić zapytanie w celu znalezienia listy grup należących do danej grupy. Aby uzyskać więcej informacji, zobacz [Operacje na grupach | Materiały referencyjne interfejsu API Graph](/previous-versions/azure/ad/graph/api/groups-operations).

### <a name="contacting-microsoft-for-support"></a>Kontaktowanie się z firmą Microsoft w celu uzyskania pomocy technicznej

Jeśli u Ciebie lub u Twoich użytkowników wystąpią problemy podczas ładowania dodatku podczas korzystania z aplikacji sieci Web firmy Office (Word, Excel itp.), które zostały wdrożone w sposób scentralowany, może być konieczne skontaktowanie się z pomocą techniczną firmy Microsoft (dowiedz się, jak to [zrobić](../../business-video/get-help-support.md)). Podaj następujące informacje o swoim środowisku Microsoft 365 w bilecie pomocy technicznej.

| Platforma | Informacje dotyczące debugowania |
|:-----|:-----|
|Pakiet Office | Dzienniki Charles/Fiddler  <br/>  Identyfikator dzierżawy ([dowiedz się, jak to zrobić](/onedrive/find-your-office-365-tenant-id))  <br/>  Identyfikator korelacji. Wyświetl źródło jednej ze stron pakietu Office i poszukaj wartości Identyfikator korelacji, a następnie wyślij ją do pomocy technicznej:  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">`  <br/>  `<input name="user_id" type="hidden" value="1003bffd96933623"></form>` |
|Klienci rozbudowani (system Windows, komputery Mac) | Dzienniki Charles/Fiddler  <br/>  Numery kompilacji aplikacji klienckiej (najlepiej jako zrzut ekranu **z pliku/konta**) |

## <a name="related-content"></a>Zawartość pokrewna

[Wdrażanie dodatków w centrum](../manage/manage-deployment-of-add-ins.md) administracyjnym (artykuł)\
[Zarządzanie dodatki w centrum administracyjnym](manage-addins-in-the-admin-center.md) (artykuł)\
[Często zadawane pytania dotyczące scentralizowanego](../manage/centralized-deployment-faq.yml) wdrażania (artykuł)\
[Uaktualnianie Microsoft 365 dla firm do najnowszej wersji Office klienta](../setup/upgrade-users-to-latest-office-client.md) (artykuł)
 
