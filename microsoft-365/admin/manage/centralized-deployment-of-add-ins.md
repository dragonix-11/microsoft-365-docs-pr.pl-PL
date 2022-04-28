---
title: Określanie, czy scentralizowane wdrażanie dodatków działa dla Twojej organizacji
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
description: Określ, czy dzierżawa i użytkownicy spełniają wymagania, aby można było wdrożyć Office dodatków za pomocą scentralizowanego wdrożenia.
ms.openlocfilehash: 4d135e76034880e1419e296f2c201536be98b4bc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093773"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>Określanie, czy scentralizowane wdrażanie dodatków działa dla Twojej organizacji

Scentralizowane wdrażanie to zalecany i najbardziej zaawansowany dla większości klientów sposób wdrażania Office dodatków dla użytkowników i grup w organizacji. Jeśli jesteś administratorem, skorzystaj z tych wskazówek, aby ustalić, czy twoja organizacja i użytkownicy spełniają wymagania, aby można było używać scentralizowanego wdrożenia.

Scentralizowane wdrażanie zapewnia następujące korzyści:

- Administrator może wdrożyć i przypisać dodatek bezpośrednio do użytkownika, wielu użytkowników za pośrednictwem grupy lub do wszystkich osób w organizacji (zobacz sekcję Wymagania administratora, aby uzyskać informacje).
- Po uruchomieniu odpowiedniej aplikacji Office dodatek zostanie automatycznie pobrany. Jeśli dodatek obsługuje polecenia dodatków, dodatek zostanie automatycznie wyświetlony na wstążce w aplikacji Office.
- Dodatki nie są już wyświetlane dla użytkowników, jeśli administrator wyłączy lub usunie dodatek lub jeśli użytkownik zostanie usunięty z Azure Active Directory lub z grupy przypisanej do dodatku.

Wdrożenie scentralizowane obsługuje trzy platformy klasyczne Windows, mac i aplikacje online Office. Wdrożenie scentralizowane obsługuje również dodatki dla systemów iOS i Android (tylko dodatki Outlook Mobile).

Może upłynąć do 24 godzin, aż dodatek będzie widoczny u klienta dla wszystkich użytkowników.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Scentralizowane wdrażanie dodatków wymaga, aby użytkownicy korzystali z licencji Microsoft 365 Business (Business Basic, Business Standard, Business Premium), licencji Office 365 Enterprise (E1/E3/E5/F3) lub licencji Microsoft 365 Enterprise (E3/E5/F3) (i są zalogowani Office przy użyciu identyfikatora organizacji), licencji Office 365 Education (A1/A3/A5) lub licencji Microsoft 365 Education (A3/A5) i mają Exchange Online i aktywne skrzynki pocztowe Exchange Online. Katalog subskrypcji musi być w katalogu lub federacyjny, aby Azure Active Directory.
Poniżej możesz wyświetlić określone wymagania dotyczące Office i Exchange lub użyć [narzędzia do sprawdzania zgodności scentralizowanego wdrożenia](#centralized-deployment-compatibility-checker).

W ramach funkcji scentralizowanego wdrażania nie są obsługiwane następujące elementy:

- Dodatki docelowe Office wersji msi (z wyjątkiem Outlook 2016)
- Lokalna usługa katalogowa
- Wdrożenie dodatku do skrzynki pocztowej Exchange on-Prem
- Wdrażanie dodatków do programu SharePoint
- aplikacje Teams
- Wdrażanie dodatków modelu obiektów składnika (COM) lub Visual Studio Tools dla pakietu Office (VSTO).
- Wdrożenia Microsoft 365, które nie obejmują Exchange Online, takich jak jednostki SKU: Aplikacje Microsoft 365 dla firm i Aplikacje Microsoft 365 dla Enterprise.

### <a name="office-requirements"></a>wymagania Office

- W przypadku dodatków programu Word, Excel i PowerPoint użytkownicy muszą korzystać z jednego z następujących elementów:
  - Na urządzeniu Windows, wersja 1704 lub nowsza licencji Microsoft 365 Business (Business Basic, Business Standard, Business Premium), licencje Office 365 Enterprise (E1/E3/E5/F3) lub licencje Microsoft 365 Enterprise (E3/E5/F3).
  - Na komputerze Mac w wersji 15.34 lub nowszej.

- W przypadku Outlook użytkownicy muszą korzystać z jednego z następujących elementów:
  - Wersja 1701 lub nowsza licencji Microsoft 365 Business (Business Basic, Business Standard, Business Premium), licencji Office 365 Enterprise (E1/E3/E5/F3) lub licencji Microsoft 365 Enterprise (E3/E5/F3).
  - Wersja 1808 lub nowsza Office Professional Plus 2019 lub Office Standard 2019 r.
  - Wersja 16.0.4494.1000 lub nowsza Office Professional Plus 2016 (MSI) lub Office Standard 2016 (MSI)\*
  - Wersja 15.0.4937.1000 lub nowsza z Office Professional Plus 2013 r. (MSI) lub Office Standard 2013 r. (MSI)\*
  - Wersja 16.0.9318.1000 lub nowsza Office 2016 dla komputerów Mac
- Wersja 2.75.0 lub nowsza Outlook mobile dla systemu iOS
- Wersja 2.2.145 lub nowsza Outlook mobile dla systemu Android

    *Wersje msi Outlook pokazują dodatki zainstalowane przez administratora na odpowiedniej wstążce Outlook, a nie w sekcji "Moje dodatki".

### <a name="exchange-online-requirements"></a>wymagania Exchange Online

Manifesty dodatków są przechowywane przez program Microsoft Exchange w dzierżawie organizacji. Administrator wdrażający dodatki i użytkownicy otrzymujący te dodatki muszą mieć wersję Exchange Online obsługującą uwierzytelnianie OAuth.

Skontaktuj się z administratorem programu Exchange w organizacji, aby dowiedzieć się, jaka konfiguracja jest używana. Łączność protokołu OAuth dla poszczególnych użytkowników można sprawdzić przy użyciu polecenia cmdlet [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) programu PowerShell.

### <a name="admin-requirements"></a>Wymagania administratora

Aby wdrożyć dodatek za pośrednictwem wdrożenia scentralizowanego, musisz być administratorem globalnym lub administratorem Exchange w organizacji.

> [!NOTE]
> Administrator Exchange może wdrożyć dodatek, jeśli zostanie dodana rola **administratora aplikacji** lub jeśli właściwość **Rejestracje aplikacji** zostanie ustawiona na wartość true w centrum administracyjnym Azure Active Directory, jak pokazano na poniższej ilustracji:
>
> ![Obrazu](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)

### <a name="centralized-deployment-compatibility-checker"></a>Scentralizowany moduł sprawdzania zgodności wdrożenia

Za pomocą narzędzia do sprawdzania zgodności scentralizowanego wdrażania możesz sprawdzić, czy użytkownicy w dzierżawie są skonfigurowani do używania scentralizowanego wdrożenia dla programu Word, Excel i PowerPoint. Narzędzie sprawdzania zgodności nie jest wymagane na potrzeby obsługi programu Outlook. Pobierz narzędzie [sprawdzania zgodności](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).

#### <a name="run-the-compatibility-checker"></a>Uruchamianie modułu sprawdzania zgodności

1. Otwórz okno programu PowerShell.exe z podwyższonym poziomem uprawnień.

2. Uruchom następujące polecenie:

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. Uruchom polecenie **Invoke-CompatibilityCheck** :

   ```powershell
   Invoke-CompatibilityCheck
   ```

   To polecenie wyświetla monit o podanie poświadczeń _TenantDomain_ (na przykład _TailspinToysIncorporated.onmicrosoft.com_) i _TenantAdmin_ (użyj poświadczeń administratora globalnego), a następnie żąda zgody.

   > [!NOTE]
   > W zależności od liczby użytkowników w dzierżawie narzędzie sprawdzania może ukończyć pracę w ciągu kilku minut lub godzin.

Gdy narzędzie zakończy pracę, utworzy plik wyjściowy w formacie CSV. Plik jest domyślnie zapisywany **w bieżącym katalogu roboczym** . Plik wyjściowy zawiera następujące informacje:

- Nazwa użytkownika
- Identyfikator użytkownika (adres e-mail użytkownika)
- Gotowość do używania funkcji Scentralizowane wdrażanie  jeśli pozostałe punkty są prawdziwe
- plan Office — plan Office są licencjonowane
- Aktywowany pakiet Office  jeśli pakiet Office został aktywowany
- Obsługiwana skrzynka pocztowa  jeśli skrzynka pocztowa obsługuje protokół OAuth

> [!NOTE]
> Uwierzytelnianie wieloskładnikowe nie jest obsługiwane w przypadku korzystania z modułu PowerShell wdrażania centralnego. Moduł działa tylko z uwierzytelnianiem podstawowym.

## <a name="user-and-group-assignments"></a>Przypisania użytkowników i grup

Funkcja Scentralizowane wdrażanie obsługuje obecnie większość grup obsługiwanych przez Azure Active Directory, w tym grupy Microsoft 365, listy dystrybucyjne i grupy zabezpieczeń.

> [!NOTE]
> Grupy bez włączonej obsługi poczty nie są obecnie obsługiwane.

Wdrożenie scentralizowane obsługuje przypisania do poszczególnych użytkowników, grup i wszystkich osób w dzierżawie. W ramach funkcji scentralizowanego wdrażania są obsługiwani użytkownicy w grupach najwyższego poziomu, czyli niemających grupy nadrzędnej, natomiast użytkownicy w grupach zagnieżdżonych, czyli należących do grupy nadrzędnej, nie są obsługiwani.

Zapoznaj się z następującym przykładem, w którym do dodatku przypisano Anetę, Joannę oraz grupę Dział sprzedaży. Ponieważ Dział sprzedaży Zachód jest grupą zagnieżdżoną, Wojciech i Tomasz nie są przypisani do dodatku.

![MicrosoftTeams-image](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Określanie, czy grupa zawiera grupy zagnieżdżone

Najłatwiejszym sposobem określenia, czy grupa zawiera grupy zagnieżdżone, jest wyświetlenie wizytówki grupy w programie Outlook. Jeśli wprowadzisz nazwę grupy w polu **Do** wiadomości e-mail, a następnie wybierzesz nazwę grupy po jej rozpoznaniu, zostanie wyświetlona wartość , jeśli zawiera ona użytkowników lub grupy zagnieżdżone. W poniższym przykładzie karta **Członkowie** wizytówki grupy Test w programie Outlook nie zawiera użytkowników, ale zawiera dwie podgrupy.

![Karta Członkowie karty Outlook wizytówki.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Można także przeprowadzić wyszukiwanie odwrotnie, sprawdzając, czy dana grupa należy do innej grupy. W poniższym przykładzie na karcie **Członkostwo** wizytówki grupy Podgrupa 1 w programie Outlook widać, że należy ona do grupy Test.

![Karta Członkostwo karty kontaktu Outlook.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Możesz także użyć interfejsu API Graph w usłudze Azure Active Directory, aby uruchomić zapytanie w celu znalezienia listy grup należących do danej grupy. Aby uzyskać więcej informacji, zobacz [Operacje na grupach| interfejs Graph API odwołania](/previous-versions/azure/ad/graph/api/groups-operations).

### <a name="contacting-microsoft-for-support"></a>Kontaktowanie się z firmą Microsoft w celu uzyskania pomocy technicznej

Jeśli Ty lub Twoi użytkownicy napotkacie problemy z ładowaniem dodatku podczas korzystania z Office aplikacji internetowych (Word, Excel itp.), które zostały wdrożone centralnie, może być konieczne skontaktowanie się z pomocą techniczną firmy Microsoft ([dowiedz się, jak to zrobić](../../business-video/get-help-support.md). Podaj następujące informacje o środowisku Microsoft 365 w bilecie pomocy technicznej.

|Platforma|Informacje dotyczące debugowania|
|---|---|
|Pakiet Office|Dzienniki Charles/Fiddler <br/> Identyfikator dzierżawy ([dowiedz się, jak](/onedrive/find-your-office-365-tenant-id)) <br/> Correlationid. Wyświetl źródło jednej ze stron pakietu Office i poszukaj wartości identyfikatora korelacji i wyślij ją do obsługi:  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">` <br/> `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`|
|Klienci rozbudowani (system Windows, komputery Mac)|Dzienniki Charles/Fiddler <br/> Numery kompilacji aplikacji klienckiej (najlepiej jako zrzut ekranu z **pliku/konta**)|

## <a name="related-content"></a>Zawartość pokrewna

[Wdrażanie dodatków w centrum administracyjnym](../manage/manage-deployment-of-add-ins.md) (artykuł)\
[Zarządzanie dodatkami w centrum administracyjnym](manage-addins-in-the-admin-center.md) (artykuł)\
[Scentralizowane wdrażanie — często zadawane pytania](../manage/centralized-deployment-faq.yml) (artykuł)\
[Uaktualnianie Microsoft 365 dla użytkowników biznesowych do najnowszego klienta Office](../setup/upgrade-users-to-latest-office-client.md) (artykuł)
