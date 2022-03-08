---
title: Szyfrowanie dwukluczowych (DKE, Double Key Encryption)
description: Funkcja DKE umożliwia ochronę bardzo ważnych danych przy zachowaniu pełnej kontroli nad kluczem.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: b16733a1d42ca245f096038f567be6fbd0c3fb2a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320609"
---
# <a name="double-key-encryption-for-microsoft-365"></a>Szyfrowanie dwukluczowych danych dla Microsoft 365

> *Dotyczy: szyfrowania dwukluczowych w celu Microsoft 365, [Microsoft 365 zgodności z przepisami](https://www.microsoft.com/microsoft-365/business/compliance-management), [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Instrukcje dotyczące: [Ujednolicony klient etykiet usługi Azure Information Protection dla komputerów Windows](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*


> *Opis usługi dla: [Microsoft 365 zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

W celu uzyskania dostępu do zawartości chronionej szyfrowanie dwukluczowych (DKE, Double Key Encryption) jest używane razem z dwoma kluczami. Firma Microsoft przechowuje jeden klucz w Microsoft Azure, a Ty przytrzymując drugi klucz. Pełna kontrola nad jednym z kluczy jest utrzymywana za pomocą usługi szyfrowania dwucyfrowego. Ochronę można stosować przy użyciu ujednoliconego klienta etykiet usługi Azure Information Protection do wysoce poufnej zawartości.

Szyfrowanie dwucyfrowe obsługuje zarówno wdrożenia w chmurze, jak i lokalne. Te wdrożenia pomagają zapewnić, że zaszyfrowane dane pozostają nieprzezroczyste w miejscach, w których przechowujesz chronione dane.

Aby uzyskać więcej informacji na temat domyślnych kluczy głównych dzierżawy w chmurze, zobacz [Planowanie i implementowanie klucza dzierżawy usługi Azure Information Protection](/azure/information-protection/plan-implement-tenant-key).

## <a name="when-your-organization-should-adopt-dke"></a>Kiedy Twoja organizacja powinna stosować projekt DKE

Szyfrowanie podwójnym kluczem jest przeznaczone dla najbardziej poufnych danych, które podlegają najsustszym wymogom ochrony. DKE nie jest przeznaczona dla wszystkich danych. Ogólnie rzecz biorąc, będziesz używać szyfrowania dwukluczowych w celu ochrony tylko niewielkiej części ogólnych danych. Przed wdrożeniem tego rozwiązania należy zdąć zidentyfikować odpowiednie dane, które mają zostać na nim zasłaniane. W niektórych przypadkach może być konieczne zawężenie zakresu i zastosowanie innych rozwiązań dla większości danych, takich jak Microsoft Information Protection z kluczami zarządzanymi przez firmę Microsoft lub programem BYOK. Te rozwiązania są wystarczające dla dokumentów, które nie podlegają rozszerzonym ochronie i wymogom prawa. Ponadto te rozwiązania umożliwiają korzystanie z najbardziej zaawansowanych Office 365 danych, czyli usług, których nie można używać z zaszyfrowaną zawartością DKE. Przykład:

- Reguły transportu, w tym złośliwe oprogramowanie i spam, które wymagają wglądu w załącznik
- Microsoft Delve
- zbierania elektronicznych materiałów dowodowych
- Przeszukiwanie i indeksowanie zawartości
- Office Web Apps, w tym funkcje współtworzenie

Żadne aplikacje lub usługi zewnętrzne, które nie są zintegrowane z usługą DKE za pośrednictwem zestawu SDK Microsoft Information Protection (MIP), nie będą mogły wykonywać akcji na zaszyfrowanych danych.

Zestaw Microsoft Information Protection SDK 1.7+ obsługuje szyfrowanie dwucyfrowe. Aplikacje integracyjne z zestawem SDK mogą mieć uzasadnienie dla tych danych z wystarczającymi uprawnieniami i integracjami.

Użyj funkcji ochrony informacji firmy Microsoft (klasyfikacji i etykiet), aby chronić większość poufnych danych, i używaj funkcji DKE tylko do obsługi najważniejszych danych. Szyfrowanie dwukluczowych ma zastosowanie w przypadku danych poufnych w ściśle uregulowanych branżach, takich jak usługi finansowe i opieka zdrowotna.

Jeśli Twoja organizacja ma dowolne z następujących wymagań, możesz zabezpieczyć zawartość przy użyciu funkcji DKE:

- Chcesz mieć pewność, że *w* wszystkich okolicznościach będzie można odszyfrować tylko chronioną zawartość.
- Nie chcesz, aby firma Microsoft samodzielnie zapewniała dostęp do chronionych danych.
- Musisz mieć wymagania prawne dotyczące przechowywania kluczy w obrębie granic geograficznych. Wszystkie klucze do szyfrowania i odszyfrowywania danych są utrzymywane w Twoim centrum danych.

## <a name="system-and-licensing-requirements-for-dke"></a>Wymagania dotyczące systemu i licencjonowania DKE

**Szyfrowanie dwukluczowych dla Microsoft 365** jest dostarczany z Microsoft 365 E5. Jeśli nie masz licencji licencji Microsoft 365 E5, możesz utworzyć konta w celu nabycia wersji [próbnej](https://aka.ms/M365E5ComplianceTrial). Aby uzyskać więcej informacji na temat tych licencji, zobacz Microsoft 365 [licencjonowania w celu zapewnienia & zgodnością](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Azure Information Protection**. Narzędzie DKE współpracuje z etykietami wrażliwości i wymaga usługi Azure Information Protection.

Etykiety wrażliwości funkcji DKE są dostępne dla użytkowników końcowych za pomocą przycisku wrażliwości w kliencie ujednoliconej etykiet AIP w aplikacji Office klasycznych. Zainstaluj te wymagania wstępne na każdym komputerze klienckim, na którym chcesz chronić chronione dokumenty i korzystać z nich.

**Microsoft Office dla przedsiębiorstw w** wersji 2009 lub nowszej (wersje klasyczne programów Word, PowerPoint i Excel) na Windows.

**Ujednolicony klient etykiet usługi Azure Information Protection w** wersji 2.7.93.0 lub nowszej. Pobierz i zainstaluj klienta etykiet ujednoliconych z Centrum [pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>Obsługiwane środowiska do przechowywania i wyświetlania zawartości chronionej przez DKE

**Obsługiwane aplikacje**. [Aplikacje Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) klientów usługi Windows, takich jak Word, Excel i PowerPoint.

**Obsługa zawartości online**. Dokumenty i pliki, które są chronione przy użyciu szyfrowania dwucyfrowego, można przechowywać w trybie online zarówno w usługach firmy Microsoft, SharePoint, jak i w OneDrive dla Firm. Przed przekazaniem ich do tych lokalizacji musisz o etykiecie i chronić dokumenty i pliki przy użyciu klawisza DKE przez obsługiwane aplikacje. Zaszyfrowaną zawartość można udostępnić pocztą e-mail, ale nie można wyświetlać zaszyfrowanych dokumentów i plików w trybie online. Zamiast tego należy wyświetlić zawartość chronioną przy użyciu obsługiwanych aplikacji klasycznych i klientów na komputerze lokalnym.

## <a name="overview-of-deploying-dke"></a>Omówienie wdrażania funkcji DKE

Wykonaj poniższe ogólne czynności, aby skonfigurować DKE. Po zakończeniu tych czynności użytkownicy końcowi mogą chronić bardzo poufne dane za pomocą szyfrowania dwucyfrowego.

1. Wdeksuj usługę DKE zgodnie z opisem w tym artykule.

2. Utwórz etykietę przy użyciu szyfrowania dwukluczowych. W Centrum zgodności platformy Microsoft 365 do aplikacji **Ochrona** informacji i utwórz nową etykietę z szyfrowaniem podwójnym klawiszem. Aby [zastosować szyfrowanie, zobacz Ograniczanie dostępu do zawartości przy użyciu etykiet wrażliwości](./encryption-sensitivity-labels.md).

3. Użyj etykiet szyfrowania z podwójnymi kluczami. Chroń dane, wybierając etykietę Double Key Encrypted na wstążce Sensitivity (Czułość) w Microsoft Office.

Istnieje kilka sposobów wykonania niektórych czynności, aby wdrożyć szyfrowanie dwukluczowych. Ten artykuł zawiera szczegółowe instrukcje, dzięki którym mniej doświadczeni administratorzy pomyślnie wdrożyli usługę. Jeśli wiesz, jak to zrobić, możesz użyć własnych metod.

## <a name="deploy-dke"></a>Wdrażanie usługi DKE

W tym artykule i klipie wideo o wdrażaniu jako miejsca docelowego wdrożenia usługi DKE używa się platformy Azure. Jeśli wdrażasz w innej lokalizacji, musisz podać własne wartości.

Obejrzyj klip [wideo na temat wdrażania](https://youtu.be/vDWfHN_kygg) szyfrowania dwucyfrowego, aby zobaczyć szczegółowe omówienie pojęć kluczowych w tym artykule. Ukończenie klipu wideo trwa około 18 minut.

Aby skonfigurować szyfrowanie dwukluczowych dla organizacji, należy wykonać poniższe ogólne czynności.

1. [Instalowanie wymagań wstępnych oprogramowania dla usługi DKE](#install-software-prerequisites-for-the-dke-service)
1. [Sklonowanie repozytorium szyfrowania dwucyfrowego GitHub klucza](#clone-the-dke-github-repository)
1. [Modyfikowanie ustawień aplikacji](#modify-application-settings)
1. [Generowanie kluczy testowych](#generate-test-keys)
1. [Tworzenie projektu](#build-the-project)
1. [Wdrażanie usługi DKE i publikowanie magazynu kluczy](#deploy-the-dke-service-and-publish-the-key-store)
1. [Sprawdzanie poprawności wdrożenia](#validate-your-deployment)
1. [Zarejestruj swój magazyn kluczy](#register-your-key-store)
1. [Tworzenie etykiet wrażliwości przy użyciu funkcji DKE](#create-sensitivity-labels-using-dke)
1. [Włączanie funkcji DKE w kliencie](#enable-dke-in-your-client)
1. [Migrowanie plików chronionych z etykiet HYOK do etykiet DKE](#migrate-protected-files-from-hyok-labels-to-dke-labels)

Gdy to zrobisz, możesz zaszyfrować dokumenty i pliki przy użyciu funkcji DKE. Aby uzyskać informacje, zobacz [Stosowanie etykiet wrażliwości do plików i wiadomości](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) e-mail w Office.

### <a name="install-software-prerequisites-for-the-dke-service"></a>Instalowanie wymagań wstępnych oprogramowania dla usługi DKE

Zainstaluj te wymagania wstępne na komputerze, na którym chcesz zainstalować usługę DKE.

**ZESTAW SDK platformy .NET Core 3.1**. Pobierz zestaw SDK i zainstaluj go z [programu Download .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio Code**. Pobierz Visual Studio Code z [https://code.visualstudio.com/](https://code.visualstudio.com). Po zainstalowaniu uruchom program Visual Studio Code wybierz **pozycję Wyświetl** \> **rozszerzenia**. Zainstaluj te rozszerzenia.

- C# dla Visual Studio Code

- NuGet Menedżer pakietów

**Git resources (Zasoby Git**). Pobierz i zainstaluj jedną z następujących instalacji.

- [Git](https://git-scm.com/downloads)

- [GitHub pulpitu](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**OpenSSL** Do [wygenerowania kluczy testowych](https://slproweb.com/products/Win32OpenSSL.html) po wdrożeniu [](#generate-test-keys) klucza testowego musi być zainstalowany program OpenSSL. Upewnij się, że poprawnie nawołuje się na ścieżkę zmiennych środowiskowych. Aby uzyskać szczegółowe informacje, zobacz na przykład "Dodawanie katalogu instalacji do ścieżki [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) ".

### <a name="clone-the-dke-github-repository"></a>Sklonowanie repozytorium GitHub DKE

Firma Microsoft dostarcza pliki źródłowe DKE w repozytorium GitHub danych. Sklonuj repozytorium, aby utworzyć projekt lokalnie na użytek organizacji. Repozytorium DKE GitHub znajduje się w .[https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService)

Poniższe instrukcje są przeznaczone dla niedoświadczonych użytkowników Visual Studio Code git:

1. W przeglądarce przejdź do: [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

2. U prawej strony ekranu wybierz pozycję **Kod**. W Twojej wersji interfejsu użytkownika może być pokazywany przycisk **Clone or download (Sklonuj lub pobierz** ). Następnie z wyświetlonej listy rozwijanej wybierz ikonę kopiowania, aby skopiować adres URL do schowka.

    Przykład:

   > [!div class="mx-imgBorder"]
   > ![Sklonuj repozytorium usługi szyfrowania dwucyfrowego z GitHub.](../media/dke-clone.png)

3. W Visual Studio Code wybierz **pozycję Wyświetl paletę** \> **poleceń** i wybierz **pozycję Git: Clone**. Aby przejść do opcji na liście, zacznij wpisywać w `git: clone` celu filtrowania wpisów, a następnie wybierz ją z listy rozwijanej. Przykład:

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Code opcji GIT:Clone.](../media/dke-vscode-clone.png)

4. W polu tekstowym wklej adres URL skopiowany z witryny Git i wybierz pozycję **Clone z witryny GitHub**.

5. W **wyświetlonym oknie** dialogowym Wybieranie folderu przejdź do lokalizacji przechowywania repozytorium i wybierz ją. Po wyświetleniu monitu wybierz pozycję **Otwórz**.

    Repozytorium zostanie otwarte w Visual Studio Code i wyświetli bieżącą gałąź Git w lewym dolnym rogu. Na przykład gałąź **powinna być główna**. Przykład:

   ![Zrzut ekranu przedstawiający repo usługi DKE w Visual Studio Code z wyświetloną gałęzią główną.](../media/dke-vscode-main-branch.jpg)

6. Jeśli nie jesteś w głównej gałęzi, musisz ją wybrać. W Visual Studio Code wybierz gałąź i wybierz pozycję **główna** z wyświetlonej listy gałęzi.

   > [!IMPORTANT]
   > Wybranie głównej gałęzi zapewnia, że masz odpowiednie pliki do skompilowania projektu. Jeśli nie wybierzesz odpowiedniej gałęzi wdrożenia, nie powiedzie się.

Masz teraz swoje repozytorium źródłowe DKE, skonfiguruj je lokalnie. Następnie [zmodyfikuj ustawienia](#modify-application-settings) aplikacji dla organizacji.

### <a name="modify-application-settings"></a>Modyfikowanie ustawień aplikacji

Aby wdrożyć usługę DKE, musisz zmodyfikować następujące typy ustawień aplikacji:

- [Ustawienia dostępu do klawiszy](#key-access-settings)
- [Ustawienia dzierżawy i klucza](#tenant-and-key-settings)

Ustawienia aplikacji można modyfikować w pliku appsettings.json. Ten plik znajduje się w lokalizacji repo DoubleKeyEncryptionService,która została sklonowana lokalnie w lokalizacji DoubleKeyEncryptionService\src\customer-key-store. Na przykład w Visual Studio Code możesz przejść do pliku, jak pokazano na poniższym obrazie.

![Lokalizowanie pliku appsettings.json dla pliku DKE.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>Ustawienia dostępu do klawiszy

Określ, czy chcesz używać poczty e-mail lub autoryzacji roli. DKE obsługuje tylko jedną z tych metod uwierzytelniania na raz.

- **Autoryzacja poczty e-mail**. Umożliwia Twojej organizacji autoryzowanie dostępu do kluczy tylko na podstawie adresów e-mail.

- **Autoryzacja roli**. Umożliwia Twojej organizacji autoryzowanie dostępu do kluczy na podstawie grup usługi Active Directory i wymaga, aby usługa sieci Web umożliwiała wykonywanie zapytań na poziomie LDAP.

##### <a name="to-set-key-access-settings-for-dke-using-email-authorization"></a>Aby skonfigurować ustawienia dostępu klucza dla usługi DKE przy użyciu autoryzacji poczty e-mail

1. Otwórz **plik appsettings.json** i znajdź ustawienie `AuthorizedEmailAddress` .

2. Dodaj adres e-mail lub adresy, które chcesz autoryzować. Oddziel wiele adresów e-mail podwójnymi cudzysłowami i przecinkami. Przykład:

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. Znajdź ustawienie `LDAPPath` i usuń tekst między `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` podwójnymi cudzysłowami. Nie umieszczaj podwójnych cudzysłowów w miejscu. Po zakończeniu ustawienie powinno wyglądać tak.

   ```json
   "LDAPPath": ""
   ```

4. Znajdź ustawienie `AuthorizedRoles` i usuń cały wiersz.

Na tym obrazie **przedstawiono plik appsettings.json** poprawnie sformatowany w celu autoryzacji poczty e-mail.

   ![Plik appsettings.json przedstawiający metodę autoryzacji poczty e-mail.](../media/dke-email-accesssetting.png)

##### <a name="to-set-key-access-settings-for-dke-using-role-authorization"></a>Aby ustawić ustawienia dostępu klucza dla usługi DKE przy użyciu autoryzacji ról

1. Otwórz **plik appsettings.json** i znajdź ustawienie `AuthorizedRoles` .

2. Dodaj nazwy grup usługi Active Directory, które chcesz autoryzować. Oddziel wiele nazw grup podwójnymi cudzysłowami i przecinkami. Przykład:

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. Znajdź ustawienie `LDAPPath` i dodaj domenę usługi Active Directory. Przykład:

   ```json
   "LDAPPath": "contoso.com"
   ```

4. Znajdź ustawienie `AuthorizedEmailAddress` i usuń cały wiersz.

Na tym obrazie **przedstawiono plik appsettings.json** poprawnie sformatowany w celu autoryzacji roli.

   ![plik appsettings.json przedstawiający metodę autoryzacji ról.](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>Ustawienia dzierżawy i klucza

Ustawienia dzierżawy DKE i klucza znajdują się w pliku **appsettings.json** .

##### <a name="to-configure-tenant-and-key-settings-for-dke"></a>Aby skonfigurować ustawienia dzierżawy i klucza dla usługi DKE

1. Otwórz **plik appsettings.json** .

2. Znajdź ustawienie `ValidIssuers` i zamień je `<tenantid>` na identyfikator dzierżawy. Identyfikator dzierżawy możesz znaleźć, przechodząc do portalu Azure Portal i wyświetlając [właściwości dzierżawy](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). Przykład:

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

> [!NOTE]
> Jeśli chcesz włączyć zewnętrzny dostęp B2B do magazynu kluczy, musisz także uwzględnić te dzierżawy zewnętrzne jako część prawidłowej listy wystawców.

Zlokalizuj ikonę `JwtAudience`. Zamień `<yourhostname>` plik na nazwę hosta komputera, na którym będzie uruchamiana usługa DKE. Przykład:

  > [!IMPORTANT]
  > Wartość dla musi `JwtAudience` dokładnie odpowiadać *nazwie hosta.* Podczas **debugowania możesz użyć skryptu localhost:5001** . Po rezygnacji z debugowania pamiętaj o zaktualizowaniu tej wartości do nazwy hosta serwera.

- `TestKeys:Name`. Wprowadź nazwę klucza. Na przykład: `TestKey1`
- `TestKeys:Id`. Utwórz identyfikator GUID i wprowadź go jako `TestKeys:ID` wartość. Na przykład `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. Aby losowo wygenerować identyfikator GUID, można użyć witryny, na przykład [generatora](https://guidgenerator.com/) identyfikatorów GUID w trybie online.

Na tym obrazie przedstawiono prawidłowy format ustawień dzierżawy i kluczy w **pliku appsettings.json**. `LDAPPath` skonfigurowano do autoryzacji ról.

![Pokazuje poprawne ustawienia dzierżawy i klucza dla pliku DKE w pliku appsettings.json.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>Generowanie kluczy testowych

Po zdefiniowanych ustawieniach aplikacji możesz generować publiczne i prywatne klucze testowe.

Aby wygenerować klucze:

1. Z otwartej Windows menu Start uruchom wiersz polecenia OpenSSL.

1. Zmień folder, w którym chcesz zapisać klawisze testowe. Pliki, które tworzysz, wykonując kroki w tym zadaniu, są przechowywane w tym samym folderze.

1. Wygeneruj nowy klucz testowy.

   ```console
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

1. Wygeneruj klucz prywatny.

   Jeśli zainstalowano program OpenSSL w wersji 3 lub nowszej, uruchom następujące polecenie:
  
  ```console
  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM -traditional
  ```
  
>  W przeciwnym razie uruchom następujące polecenie:
>  ```console
>  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM
>  ```

1. Wygeneruj klucz publiczny.

   ```console
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

1. W edytorze tekstów otwórz **plik pubkeyonly.pem**. Skopiuj całą zawartość w pliku **pubkeyonly.pem** , oprócz pierwszego i ostatniego wiersza, `PublicPem` do sekcji **pliku appsettings.json** .

1. W edytorze tekstów otwórz **plik privkeynopass.pem**. Skopiuj całą zawartość pliku **privkeynopass.pem** ( `PrivatePem` oprócz pierwszego i ostatniego wiersza) do sekcji **pliku appsettings.json** .

1. Usuń wszystkie puste miejsca i nowe linie zarówno w sekcjach, jak `PublicPem` i w sekcjach `PrivatePem` .

    > [!IMPORTANT]
    > Podczas kopiowania tej zawartości nie usuwaj żadnych danych PEM.

1. W Visual Studio Code przejdź do pliku **Autostart.cs**. Ten plik znajduje się w pliku Repo DoubleKeyEncryptionService, który został sklonowany lokalnie w lokalizacji DoubleKeyEncryptionService\src\customer-key-store\.

1. Znajdź następujące wiersze:

    ```csharp
        #if USE_TEST_KEYS
        #error !!!!!!!!!!!!!!!!!!!!!! Use of test keys is only supported for testing,
        DO NOT USE FOR PRODUCTION !!!!!!!!!!!!!!!!!!!!!!!!!!!!!
        services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
        #endif
    ```

1. Zamień te wiersze na następujący tekst:

    ```csharp
    services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
    ```

    Wyniki końcowe powinny wyglądać podobnie do poniższych.

    ![plik startup.cs, aby wyświetlić podgląd publiczny.](../media/dke-startupcs-usetestkeys.png)

Teraz możesz rozpocząć tworzenie [projektu WBK](#build-the-project).

### <a name="build-the-project"></a>Tworzenie projektu

Użyj poniższych instrukcji, aby utworzyć projekt DKE lokalnie:

1. W Visual Studio Code usługi DKE wybierz pozycję **Wyświetl** \> paletę poleceń, a następnie wpisz **kompilację** w wierszu polecenia.

2. Z listy wybierz pozycję **Zadania: Uruchamianie zadania kompilacji**.

   Jeśli nie znaleziono żadnych zadań kompilacji, wybierz pozycję **Konfiguruj zadanie kompilacji** i utwórz je dla .NET Core w następujący sposób.

   ![Konfigurowanie brakującego zadania kompilacji dla usługi .NET.](../media/dke-configurebuildtask.png)

   1. Wybierz **pozycję Create tasks.json z szablonu**.

      ![Utwórz plik tasks.json na podstawie szablonu dla pliku DKE.](../media/dke-createtasksjsonfromtemplate.png)

   2. Z listy typów szablonów wybierz pozycję **.NET Core**.

      ![Wybierz odpowiedni szablon dla usługi DKE.](../media/dke-tasksjsontemplate.png)

   3. W sekcji kompilacji znajdź ścieżkę do pliku **customerkeystore.csproj** . Jeśli jej tam nie ma, dodaj następujący wiersz:

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. Uruchom ponownie kompilację.

3. Sprawdź, czy w oknie wyników nie wystąpiły żadne czerwone błędy.

   Jeśli występują czerwone błędy, sprawdź dane wyjściowe konsoli. Upewnij się, że wszystkie poprzednie kroki zostały wykonane poprawnie i że są dostępne poprawne wersje kompilacji.

4. Wybierz **pozycję Uruchom** \> **debugowanie startowe** , aby debugowanie procesu. Jeśli zostanie wyświetlony monit o wybranie środowiska, wybierz pozycję **.NET core**.

   Debugowanie podstawowe programu .NET jest zwykle uruchamiane w programie `https://localhost:5001`. Aby wyświetlić klucz testowy, przejdź do `https://localhost:5001` pola i dołącz ukośnik (/) oraz nazwę klucza. Przykład:

   ```https
   https://localhost:5001/TestKey1
   ```

   Klucz powinien być wyświetlany w formacie JSON.

Konfiguracja jest teraz ukończona. Przed opublikowaniem magazynu kluczy w jwtAudience w jwtAudience upewnij się, że wartość nazwy hosta jest dokładnie taka sama jak nazwa hosta usługi App Service. Być może zmieniono go na localhost, aby rozwiązać problemy z kompilacją.

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>Wdrażanie usługi DKE i publikowanie magazynu kluczy

W przypadku wdrożeń produkcyjnych wdaj usługę w chmurze innej firmy lub [opublikuj ją w systemie lokalnym](/aspnet/core/tutorials/publish-to-iis?preserve-view=true&tabs=netcore-cli&view=aspnetcore-3.1).

Możesz preferować inne metody wdrażania kluczy. Wybierz metodę najlepszą dla Twojej organizacji.

W przypadku wdrożeń pilotażowych możesz wdrożyć na platformie Azure i od razu rozpocząć pracę.

#### <a name="to-create-an-azure-web-app-instance-to-host-your-dke-deployment"></a>Aby utworzyć wystąpienie aplikacji Azure Web App na celu hostować wdrożenie usługi DKE

Aby opublikować magazyn kluczy, należy utworzyć wystąpienie usługi aplikacji Azure w celu hostowania wdrożenia usługi DKE. Następnie opublikujesz wygenerowane klucze na platformie Azure.

1. W przeglądarce zaloguj się do portalu [Microsoft Azure aplikacji](https://ms.portal.azure.com) i przejdź do strony **App** **ServicesAdd** > .

2. Wybierz swoją subskrypcję i grupę zasobów, a następnie zdefiniuj szczegóły swojego wystąpienia.

   - Wprowadź nazwę hosta komputera, na którym chcesz zainstalować usługę DKE. Upewnij się, że jest to nazwa taka sama jak nazwa zdefiniowana dla ustawienia JwtAudience w pliku [**appsettings.json**](#tenant-and-key-settings) . Wartością podaną dla nazwy jest również WebAppInstanceName.

   - W **przypadku opcji** Publikuj wybierz **kod**, a w przypadku stosu **środowiska uruchomieniowego** wybierz **pozycję .NET Core 3.1**.

   Przykład:

   > [!div class="mx-imgBorder"]
   > ![Dodaj usługę aplikacji.](../media/dke-azure-add-app-service.png)

3. U dołu strony wybierz pozycję **Recenzja + utwórz**, a następnie wybierz pozycję **Dodaj**.

4. Aby opublikować wygenerowane klucze, wykonaj jedną z następujących czynności:

   - [Publikowanie za pośrednictwem zipDeployUI](#publish-via-zipdeployui)
   - [Publikowanie za pośrednictwem protokołu FTP](#publish-via-ftp)
   - [Publikowanie za pośrednictwem Visual Studio 2019 r. lub nowszego](/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>Publikowanie za pośrednictwem zipDeployUI

1. Przejdź do `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI`.

   Na przykład: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

2. W bazie danych dla magazynu kluczy przejdź do folderu **customer-key-store\src\customer-key-store** i sprawdź, czy ten folder zawiera plik **customerkeystore.csproj** .

3. Uruchom: **dotnet publish**

   W oknie wyników jest wyświetlany katalog, w którym wdrożono publikowanie.

   Na przykład: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. Wyślij wszystkie pliki z katalogu publikowania do .zip pliku. Podczas tworzenia .zip upewnij się, że wszystkie pliki w katalogu znajdują się na poziomie głównym .zip pliku.

5. Przeciągnij i upuść .zip, który utworzysz, do witryny ZipDeployUI otwartej powyżej. Na przykład: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

Klucz dostępu jest wdrożony i możesz przejść do utworzonych przez Ciebie kluczy testowych. Kontynuuj sprawdzanie [poprawności wdrożenia](#validate-your-deployment) poniżej.

#### <a name="publish-via-ftp"></a>Publikowanie za pośrednictwem protokołu FTP

1. Połączenie do utworzonej [powyżej usługi aplikacji](#deploy-the-dke-service-and-publish-the-key-store).

   W przeglądarce przejdź do strony: **Azure PortalApp** >  **ServiceDeployment** >  **CenterManual** >  **DeploymentFTPDashboard** >  > .

2. Skopiuj wyświetlone parametry połączenia do pliku lokalnego. Użyjesz tych ciągów do nawiązania połączenia z usługą aplikacji sieci Web i przekazania plików za pośrednictwem protokołu FTP.

   Przykład:

   ![Kopiowanie ciągów połączeń z pulpitu nawigacyjnego FTP.](../media/dke-ftp-dashboard.png)

3. W bazie danych dla magazynu kluczy przejdź do katalogu **customer-key-store\src\customer-key-store**.

4. Sprawdź, czy ten katalog zawiera **plik customerkeystore.csproj** .

5. Uruchom: **dotnet publish**

   Dane wyjściowe zawierają katalog, w którym wdrożono publikowanie.

   Na przykład: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. Wyślij wszystkie pliki z katalogu publikowania do pliku zip. Podczas tworzenia .zip upewnij się, że wszystkie pliki w katalogu znajdują się na poziomie głównym .zip pliku.

7. W kliencie FTP użyj skopiowanych informacji o połączeniu, aby połączyć się z usługą aplikacji. Upload pliku .zip utworzonym w poprzednim kroku katalogu głównego aplikacji sieci Web.

DKE jest wdrażana i możesz przejść do utworzonych przez Ciebie kluczy testowych. Następnie sprawdź [poprawność wdrożenia](#validate-your-deployment).

### <a name="validate-your-deployment"></a>Sprawdzanie poprawności wdrożenia

Po wdrożeniu funkcji DKE przy użyciu jednej z opisanych powyżej metod sprawdź poprawność wdrożenia i kluczowych ustawień magazynu.

Uruchamianie:

```powershell
src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/mykey
```

Przykład:

```powershell
key_store_tester.ps1 https://mydkeservice.com/mykey
```

Upewnij się, że w wynikach nie są wyświetlane żadne błędy. Gdy wszystko będzie gotowe, [zarejestruj swój magazyn kluczy](#register-your-key-store).

W nazwie klucza jest zróżnicowa wielkość liter. Wprowadź nazwę klucza wyświetlaną w pliku appsettings.json.

## <a name="register-your-key-store"></a>Zarejestruj swój magazyn kluczy

Poniższe kroki umożliwiają zarejestrowanie usługi DKE. Zarejestrowanie usługi DKE jest ostatnim krokiem wdrożenia usługi DKE przed rozpoczęciem tworzenia etykiet.

Aby zarejestrować usługę DKE:

1. W przeglądarce otwórz portal tożsamości [usługi Microsoft Azure](https://ms.portal.azure.com/) i przejdź do strony **Wszystkie rejestracje** \>  \> aplikacji tożsamości **usług**.

2. Wybierz **pozycję Nowa rejestracja** i wprowadź opisową nazwę.

3. Wybierz typ konta z wyświetlonych opcji.

   Jeśli używasz konta Microsoft Azure domenie niestandardowej, takiej jak **onmicrosoft.com**, wybierz pozycję Konta tylko w tym katalogu organizacyjnym **(tylko firma Microsoft — jedna dzierżawa).**

   Przykład:

   > [!div class="mx-imgBorder"]
   > ![Rejestracja nowej aplikacji.](../media/dke-app-registration.png)

4. U dołu strony wybierz pozycję Zarejestruj, aby  utworzyć nową rejestrację aplikacji.

5. W nowym uwierzytelnianiem aplikacji w okienku po lewej stronie w **obszarze Zarządzanie** wybierz pozycję **Uwierzytelnianie**.

6. Wybierz **pozycję Dodaj platformę**.

7. W **wyskakującym okienku** Konfiguruj platformy wybierz pozycję **Sieć Web**.

8. W **obszarze Przekieruj** URI wprowadź numer URI usługi szyfrowania dwucyfrowego. Wprowadź adres URL usługi aplikacji, w tym zarówno nazwę hosta, jak i domenę.

   Na przykład: `https://mydkeservicetest.com`

   - Wprowadzany adres URL musi być zgodne z nazwą hosta, na którym jest wdrożona Usługa DKE.
   - Domena musi być [zweryfikowaną domeną](/azure/active-directory/develop/reference-breaking-changes#appid-uri-in-single-tenant-applications-will-require-use-of-default-scheme-or-verified-domains).
   - Jeśli testowasz lokalnie za pomocą Visual Studio, użyj .`https://localhost:5001`
   - We wszystkich przypadkach schemat musi mieć **https**.

   Upewnij się, że nazwa hosta jest dokładnie taka jak nazwa hosta usługi App Service. Być może zmieniono go na rozwiązywanie `localhost` problemów z kompilacją. W **pliku appsettings.json** ta wartość jest nazwą hosta ustawioną dla `JwtAudience`.

9. W **obszarze Udzielanie niejawne** zaznacz **pole wyboru Tokeny** identyfikatorów.

10. Wybierz **pozycję Zapisz** , aby zapisać zmiany.

11. W okienku po lewej stronie wybierz pozycję **Udostępnij interfejs API** obok identyfikatora URI aplikacji, wprowadź adres URL usługi aplikacji, w tym nazwę hosta i domenę, a następnie wybierz pozycję **Ustaw**.

12. Nadal na stronie **Udostępnianie interfejsu API** w **obszarze Zakresy zdefiniowane przez** ten interfejs API wybierz **pozycję Dodaj zakres**. W nowym zakresie:

    1. Zdefiniuj nazwę zakresu jako **user_impersonation**.

    2. Wybierz administratorów i użytkowników, którzy mogą wyrażać zgodę.

    3. Zdefiniuj wszystkie pozostałe wartości wymagane.

    4. Wybierz **pozycję Dodaj zakres**.

    5. Wybierz **pozycję** Zapisz u góry, aby zapisać zmiany.

13. Nadal na stronie **Udostępnianie interfejsu API** w obszarze **Autoryzowane aplikacje klienckie** wybierz **pozycję Dodaj aplikację kliencową**.

    W nowej aplikacji klienckiej:

    1. Zdefiniuj identyfikator klienta jako `d3590ed6-52b3-4102-aeff-aad2292ab01c`. Ta wartość to identyfikator Microsoft Office klienta i umożliwia Office tokenu dostępu dla magazynu kluczy.

    2. W **obszarze Zakresy autoryzowane** wybierz **user_impersonation** zakres.

    3. Wybierz **pozycję Dodaj aplikację**.

    4. Wybierz **pozycję** Zapisz u góry, aby zapisać zmiany.

    5. Powtórz te czynności, ale tym razem zdefiniuj identyfikator klienta jako `c00e9d32-3c8d-4a7d-832b-029040e7db99`. Ta wartość to ujednolicony identyfikator klienta usługi Azure Information Protection z etykietami.

Usługa DKE zostanie zarejestrowana. Kontynuuj tworzenie [etykiet przy użyciu funkcji DKE](#create-sensitivity-labels-using-dke).

## <a name="create-sensitivity-labels-using-dke"></a>Tworzenie etykiet wrażliwości przy użyciu funkcji DKE

W Centrum zgodności platformy Microsoft 365 utwórz nową etykietę wrażliwości i zastosuj szyfrowanie tak, jak w przeciwnym razie. Wybierz **pozycję Użyj szyfrowania dwukrotnie** i wprowadź adres URL punktu końcowego klucza. W adresie URL należy uwzględnić nazwę klucza podaną w sekcji "TestKeys" pliku appsettings.json.

Na przykład: `https://testingdke1.azurewebsites.net/KEYNAME`

> [!div class="mx-imgBorder"]
> ![Wybierz pozycję Użyj szyfrowania podwójnie klawiszowego w Centrum zgodności platformy Microsoft 365.](../media/dke-use-dke.png)

Wszelkie etykiety DKE, które dodajesz, zaczną pojawiać się dla użytkowników w najnowszych wersjach Aplikacje Microsoft 365 dla przedsiębiorstw.

> [!NOTE]
> Odświeżenie etykiet przez klientów może potrwać do 24 godzin.

### <a name="enable-dke-in-your-client"></a>Włączanie funkcji DKE w kliencie

Jeśli jesteś niejawnym testerem Office włączono dla Ciebie funkcję DKE. W przeciwnym razie włącz funkcję DKE dla swojego klienta, dodając następujące klucze rejestru:

```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>Migrowanie plików chronionych z etykiet HYOK do etykiet DKE

Jeśli chcesz, po zakończeniu konfigurowania funkcji DKE możesz przeprowadzić migrację zawartości, która jest chroniona, przy użyciu etykiet HYOK do etykiet funkcji DKE. Do migrowania użyjesz skanera AIP. Aby rozpocząć korzystanie ze skanera, zobacz Co [to jest ujednolicony skaner etykiet usługi Azure Information Protection?](/azure/information-protection/deploy-aip-scanner).

Jeśli nie przeprowadzasz migracji zawartości, zawartość chroniona przez HYOK pozostanie nienaruszona.

## <a name="other-deployment-options"></a>Inne opcje wdrażania

Zdajemy sobie sprawę, że w przypadku niektórych klientów korzystających z dobrze uregulowanych branż ta standardowa implementacja odniesienia przy użyciu kluczy opartych na oprogramowaniu może nie być wystarczająca do spełnienia ich rozszerzonych zobowiązań i potrzeb dotyczących zgodności z przepisami. Współpracujemy z dostawcami modułu zabezpieczeń sprzętowych (HSM, Hardware Security Module) innych firm, aby obsługiwać rozszerzone opcje zarządzania kluczami w usłudze DKE, takie jak:

- [Powierzenie](https://www.entrust.com/digital-security/hsm/services/packaged-services/double-key-encryption-integration#:~:text=Entrust%20Double%20Key%20Encryption%20for%20Microsoft%20AIP%2C%20offered,trust%20for%20the%20protection%20of%20sensitive%20cryptographic%20keys.)

- [Jak to się owie,](https://cpl.thalesgroup.com/cloud-security/encryption/double-key-encryption)

Aby uzyskać więcej informacji i wskazówki na temat sprzedawców rozwiązań DKE HSM, można się bezpośrednio do tych dostawców.
