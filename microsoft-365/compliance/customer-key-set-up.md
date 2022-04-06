---
title: Konfigurowanie klucza klienta
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak skonfigurować klucz klienta dla Microsoft 365.
ms.openlocfilehash: f3d7da27e0c9a5e27f0c3e7bcc3adb48dad5d42c
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634520"
---
# <a name="set-up-customer-key"></a>Konfigurowanie klucza klienta

Za pomocą klucza klienta możesz sterować kluczami szyfrowania swojej organizacji, a następnie skonfigurować Microsoft 365 ich używać do szyfrowania danych w spoczynku w centrach danych firmy Microsoft. Oznacza to, że klucz klienta umożliwia klientom dodanie warstwy szyfrowania, która należy do nich, wraz z ich kluczami.

Skonfiguruj platformę Azure, aby można było używać klucza klienta dla Office 365. W tym artykule opisano kroki, które należy wykonać, aby utworzyć i skonfigurować wymagane zasoby platformy Azure, a następnie przedstawiono kroki konfigurowania klucza klienta w Office 365. Po skonfigurowaniu platformy Azure określasz zasady, które z tego powodu należy przypisać do szyfrowania danych w różnych Microsoft 365 obciążeniach pracą w organizacji. Aby uzyskać więcej informacji o kluczu klienta lub aby uzyskać ogólne informacje, zobacz Szyfrowanie usługi przy użyciu klucza [klienta](customer-key-overview.md) w p Office 365.
  
> [!IMPORTANT]
> Zdecydowanie zalecamy, aby postępować zgodnie z najlepszymi rozwiązaniami w tym artykule. Są one nazywane **PORADĄ i** **WAŻNE**. Klucz klienta zapewnia ci kontrolę nad głównymi kluczami szyfrowania, których zakres może być tak duży, jak cała organizacja. Oznacza to, że błędy popełnione za pomocą tych kluczy mogą mieć szeroki wpływ i mogą skutkować przerwami w działaniu usługi lub nieodwołalnym utratą danych.
  
## <a name="before-you-set-up-customer-key"></a>Przed skonfigurowaniem klucza klienta

Przed rozpoczęciem upewnij się, że masz odpowiednie subskrypcje i licencje platformy Azure dla swojej organizacji. Korzystaj z płatnych subskrypcji platformy Azure, Enterprise Agreement lub od dostawcy usług w chmurze. Płatności kartą kredytową nie są akceptowane. Zatwierdź i skonfiguruj potrzeby dotyczące konta dla fakturowania. Abonamenty dostępne w ramach bezpłatnej, wersji próbnej, sponsoringu, subskrypcji MSDN i osób objętej starszą pomocą techniczną nie są uprawnione.

Office 365 E5, Microsoft 365 E5, Zgodność platformy Microsoft 365 E5 i Microsoft 365 E5 Information Protection & SKU zarządzania oferują klucz klienta. Office 365 Advanced Compliance licencji (SKU) nie jest już dostępna dla nowych licencji. Istniejące Office 365 Advanced Compliance będą nadal obsługiwane.

Aby poznać pojęcia i procedury w tym artykule, zapoznaj się z dokumentacją usługi [Azure Key Vault](/azure/key-vault/) aplikacji. Zapoznaj się także z terminami używanymi na platformie Azure, na przykład z dzierżawą [usługi Azure AD](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant).
  
Jeśli potrzebujesz pomocy technicznej wykraczającej poza dokumentację, skontaktuj się z firmą Microsoft Consulting Services (MCS), Premier Field Engineering (PFE) lub z partnerem firmy Microsoft w celu uzyskania pomocy. Aby przekazać opinię na temat klucza klienta, w tym dokumentacji, wyślij swoje pomysły, sugestie i perspektywy do customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Omówienie czynności w celu skonfigurowania klucza klienta

Aby skonfigurować klucz klienta, wykonaj te zadania w podanej kolejności. Pozostała część tego artykułu zawiera szczegółowe instrukcje dotyczące poszczególnych zadań lub zawiera linki do dodatkowych informacji na temat poszczególnych kroków procesu.
  
**Na platformie Azure Microsoft FastTrack:**
  
Większość tych zadań można wykonać, łącząc się zdalnie z Azure PowerShell. Aby uzyskać najlepsze wyniki, użyj wersji 4.4.0 lub nowszej Azure PowerShell.
  
- [Utwórz dwie nowe subskrypcje platformy Azure](#create-two-new-azure-subscriptions)

- [Prześlij żądanie aktywowania klucza klienta dla Office 365](#submit-a-request-to-activate-customer-key-for-office-365)
 
- [Rejestrowanie subskrypcji platformy Azure w celu korzystania z obowiązkowego okresu przechowywania](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  Ten proces rejestracji potrwa pięć dni roboczych.

- [Utwórz subskrypcję premium usługi Azure Key Vault w każdej subskrypcji](#create-a-premium-azure-key-vault-in-each-subscription)

- [Przypisywanie uprawnień do każdego magazynu kluczy](#assign-permissions-to-each-key-vault)

- [Upewnij się, że w magazynach kluczy jest włączona opcja nie programowego usuwania](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [Dodawanie klucza do każdego magazynu kluczy przez utworzenie lub zaimportowanie klucza](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Sprawdzanie poziomu odzyskiwania kluczy](#check-the-recovery-level-of-your-keys)

- [Kopię zapasową usługi Azure Key Vault](#back-up-azure-key-vault)

- [Sprawdzanie poprawności ustawień Key Vault Azure](#validate-azure-key-vault-configuration-settings)

- [Uzyskiwanie URI dla każdego klucza Key Vault Azure](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Wykonywanie zadań na platformie Azure Key Vault i Microsoft FastTrack kluczem klienta

Wykonaj te zadania na platformie Azure Key Vault. Musisz wykonać te czynności dla wszystkich dezp. klientów, których używasz z kluczem klienta.
  
### <a name="create-two-new-azure-subscriptions"></a>Utwórz dwie nowe subskrypcje platformy Azure

Klucz klienta wymaga dwóch subskrypcji platformy Azure. W ramach najlepszych rozwiązań firma Microsoft zaleca tworzenie nowych subskrypcji platformy Azure do używania z kluczem klienta. Klucze usługi Azure Key Vault mogą być autoryzowane tylko do aplikacji w tej samej dzierżawie usługi Azure Active Directory (Microsoft Azure Active Directory), musisz utworzyć nowe subskrypcje przy użyciu tej samej dzierżawy usługi Azure AD używanej z Twoją organizacją, do której zostaną przypisane dezp. Na przykład za pomocą konta służbowego z uprawnieniami administratora globalnego w organizacji. Aby uzyskać szczegółowe instrukcje, zobacz [Rejestracja w usłudze Azure jako organizacja](/azure/active-directory/fundamentals/sign-up-organization).
  
> [!IMPORTANT]
> Klucz klienta wymaga dwóch kluczy dla każdej zasady szyfrowania danych (DEP). Aby to osiągnąć, musisz utworzyć dwie subskrypcje platformy Azure. W ramach najlepszych rozwiązań firma Microsoft zaleca skonfigurowanie jednego klucza w każdej subskrypcji przez oddzielnych członków organizacji. Tych subskrypcji platformy Azure należy używać tylko do administrowania kluczami szyfrowania dla Office 365. Chroni to organizację na wypadek przypadkowego, celowego, celowego usunięcia jednego z operatorów lub w inny sposób błędnego ustawienia kluczy, za które odpowiadają.

Nie ma praktycznego limitu liczby subskrypcji platformy Azure, które można utworzyć dla organizacji. Aby zminimalizować skutki błędów ludzkich i jednocześnie zarządzać zasobami używanymi przez klucz klienta, należy stosować się do poniższych najważniejszych rozwiązań.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Prześlij żądanie aktywowania klucza klienta dla Office 365

Po utworzeniu dwóch nowych subskrypcji platformy Azure musisz przesłać odpowiednie żądanie oferty klucza klienta w portalu Microsoft FastTrack [klienta](https://fasttrack.microsoft.com/). Wybory dokonane w formularzu oferty dotyczące autoryzowanych oznaczeń w organizacji mają kluczowe znaczenie i są niezbędne do ukończenia rejestracji kluczy klienta. Selekci z wybranych ról w Twojej organizacji zapewniają autentyczność każdego żądania cofnięcia i zniszczynia wszystkich kluczy używanych w zasadach szyfrowania danych klucza klienta. Ten krok musisz wykonać jeden raz dla każdego typu funkcji DEP klucza klienta, który ma być potrzebny w Twojej organizacji.

**Zespół FastTrack nie udziela pomocy przy użyciu klucza klienta. Office 365 po prostu za pomocą portalu FastTrack umożliwiają przesłanie formularza i ułatwiają śledzenie odpowiednich ofert dla klucza klienta. Po przesłaniu żądania FastTrack się do odpowiedniego zespołu dołączania do klucza klienta, aby rozpocząć proces dołączania.**
  
Aby przesłać ofertę aktywowania klucza klienta, wykonaj następujące czynności:
  
1. Za pomocą konta służbowego z uprawnieniami administratora globalnego w organizacji zaloguj się do portalu Microsoft FastTrack [konta](https://fasttrack.microsoft.com/).

2. Po zalogowaniu wybierz odpowiednią domenę.

3. Dla wybranej domeny wybierz pozycję **Zażądaj usług** na górnym pasku nawigacyjnym i przejrzyj listę dostępnych ofert.

4. Wybierz kartę informacji dla oferty, która dotyczy Ciebie:

   - **Wiele Microsoft 365 obciążenia pracą: Wybierz** pozycję Poproś o pomoc **przy szyfrowaniu klucza Microsoft 365** ofertę.

   - **Exchange Online i Skype dla firm: Wybierz** pomoc **w żądaniu klucza szyfrowania dla Exchange** szyfrowania.

   - **SharePoint online, OneDrive** i Teams: Wybierz pozycję Poproś o pomoc przy szyfrowaniu klucza SharePoint **i OneDrive dla Firm** ofertę.

5. Po przejrzenia szczegółów oferty wybierz pozycję **Przejdź do kroku 2**.

6. Wypełnij wszystkie odpowiednie szczegóły i wymagane informacje w formularzu oferty. Zwróć szczególną uwagę na wybóry, których służby z Twojej organizacji chcesz autoryzować, aby zatwierdzać trwałe i nieodwracalne klucze szyfrowania i dane. Po zakończeniu pracy z formularzem wybierz pozycję **Prześlij**.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Rejestrowanie subskrypcji platformy Azure w celu korzystania z obowiązkowego okresu przechowywania

Tymczasowa lub trwała utrata głównych kluczy szyfrowania może zakłócić lub nawet spowodować utratę danych. Dlatego zasoby używane z kluczem klienta wymagają silnej ochrony. Wszystkie zasoby platformy Azure używane w mechanizmach ochrony przy użyciu klucza klienta wykraczają poza domyślną konfigurację. Możesz oznaczać lub rejestrować subskrypcje platformy Azure na *obowiązkowy okres przechowywania*. Obowiązkowy okres przechowywania zapobiega natychmiastowemu i nieodwołalnemu anulowaniu subskrypcji platformy Azure. Kroki wymagane do zarejestrowania subskrypcji platformy Azure na potrzeby obowiązkowego okresu przechowywania wymagają współpracy Microsoft 365 zespołem. Ten proces potrwa pięć dni roboczych. Wcześniej obowiązkowy okres przechowywania był czasami nazywany "Nie anuluj".
  
Przed kontaktem Microsoft 365 zespołu musisz wykonać następujące czynności dla każdej subskrypcji platformy Azure, która jest używania z kluczem klienta. Przed rozpoczęciem upewnij się, [że Azure PowerShell moduł Az](/powershell/azure/new-azureps-module-az).
  
1. Zaloguj się przy użyciu Azure PowerShell. Aby uzyskać instrukcje, [zobacz Logowanie się za pomocą Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Uruchom Register-AzProviderFeature cmdlet, aby zarejestrować subskrypcje w celu korzystania z obowiązkowego okresu przechowywania. Wykonaj tę czynność dla każdej subskrypcji.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

3. Skontaktuj się z firmą Microsoft, aby ukończyć proces.

   - W celu włączenia klucza klienta na potrzeby przypisywania funkcji DEP do poszczególnych Exchange Online pocztowych skontaktuj się z [exock@microsoft.com.](mailto:exock@microsoft.com)

   - W celu włączenia klucza klienta na potrzeby przypisywania sekcji DEP w celu szyfrowania SharePoint Online i OneDrive dla Firm (w tym plików Teams) dla wszystkich użytkowników dzierżawy, skontaktuj się z administratorem [spock@microsoft.com.](mailto:spock@microsoft.com)

   - W celu włączenia klucza klienta na potrzeby przypisywania sekcji DEP w celu szyfrowania zawartości w wielu obciążeniach pracą Microsoft 365 (Exchange Online, Teams, Microsoft Information Protection) dla wszystkich użytkowników dzierżawy, skontaktuj się z [m365-ck@service.microsoft.com.](mailto:m365-ck@service.microsoft.com)

   - W wiadomości e-mail uwzględnij następujące informacje:

     **Temat**: Klucz klienta dla \<*Your tenant's fully qualified domain name*\>

     **Treść**: Uwzględnij identyfikatory subskrypcji, dla których chcesz ukończyć obowiązkowy okres przechowywania, oraz wynik Get-AzProviderFeature dla każdej subskrypcji.

     Zakończenie tego procesu w umowie dotyczącej poziomu usług trwa pięć dni roboczych po powiadomieniu (i zweryfikowaniu) przez firmę Microsoft, że zarejestrowano subskrypcje w celu korzystania z obowiązkowego okresu przechowywania.

4. Po otrzymaniu od firmy Microsoft powiadomienia o ukończeniu rejestracji sprawdź jej stan, uruchamiając Get-AzProviderFeature w następujący sposób. Jeśli zostało zweryfikowane, Get-AzProviderFeature zwraca wartość **właściwości Stan** **rejestracji.** Wykonaj ten krok dla każdej subskrypcji.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

5. Aby ukończyć ten proces, uruchom Register-AzResourceProvider wiersza. Wykonaj ten krok dla każdej subskrypcji.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Utwórz subskrypcję premium usługi Azure Key Vault w każdej subskrypcji

Procedura tworzenia magazynu kluczy jest udokumentowana w usłudze Wprowadzenie w usłudze [Azure Key Vault](/azure/key-vault/general/overview), która przeprowadzi Cię przez proces instalowania i uruchamiania usługi Azure PowerShell, nawiązywania połączenia z subskrypcją platformy Azure, tworzenia grupy zasobów i tworzenia magazynu kluczy w tej grupie zasobów.
  
Podczas tworzenia magazynu kluczy należy wybrać element SKU: Standardowy lub Premium. Standardowa Key Vault umożliwia ochronę kluczy platformy Azure Key Vault za pomocą oprogramowania — nie ma ochrony klucza modułu zabezpieczeń sprzętu (HSM), Premium SKU umożliwia stosowanie hsm w celu ochrony Key Vault kluczy. Klucz klienta akceptuje magazyny kluczy, które używają jednej z tych kopii SKU, jednak firma Microsoft zdecydowanie zaleca używanie tylko Premium SKU. Koszt operacji z kluczami każdego typu jest taki sam, dlatego jedyną różnicą w kosztach jest miesięczny koszt każdego klucza chronionego przez HSM. Zobacz [Key Vault cen,](https://azure.microsoft.com/pricing/details/key-vault/) aby uzyskać szczegółowe informacje.
  
> [!IMPORTANT]
> Magazyny kluczy Premium SKU i klucze chronione przez HSM należy stosować do danych produkcyjnych, a do celów testowania i sprawdzania poprawności należy używać jedynie standardowych magazynów i kluczy kluczowych wersji SKU.
  
Dla każdej Microsoft 365 Azure, w której będzie można używać klucza klienta, utwórz magazyn klucza w każdej z dwóch utworzonych subskrypcji platformy Azure. Aby na przykład umożliwić kluczowi klienta używanie dezp Exchange Online dla scenariuszy z obsługą SharePoint, usługi SharePoint Online i wielu obciążeń pracą, utworzysz trzy pary magazynów kluczy.
  
Użyj konwencji nazewnictwa dla magazynów kluczy odzwierciedlających zamierzone użycie funkcji DEP, z którą będziesz skojarzyć magazyny. Zobacz sekcję Najlepsze rozwiązania poniżej, aby uzyskać zalecenia dotyczące konwencji nazewnictwa.
  
Utwórz osobny zestaw połączonych ze sobą magazynów dla poszczególnych zasad szyfrowania danych. Na Exchange Online skrzynki pocztowej zakres zasad szyfrowania danych jest wybierany przez Ciebie. Do skrzynki pocztowej mogą być przypisane tylko jedne zasady, a można utworzyć maksymalnie 50 zasad. Zakres zasad usługi SharePoint online obejmuje wszystkie dane w organizacji w lokalizacji geograficznej lub lokalizacji _geograficznej_. Zakres zasad wielu obciążeń obejmuje wszystkie dane w obsługiwanych obciążeniach pracą wszystkich użytkowników.

Tworzenie magazynów kluczy wymaga również utworzenia grup zasobów platformy Azure, ponieważ magazyny kluczy wymagają pojemności magazynu (choć niewielkiego), a rejestrowanie Key Vault, jeśli jest włączone, generuje również przechowywane dane. Jako najlepsze rozwiązanie firma Microsoft zaleca używanie osobnych administratorów do zarządzania każdą grupą zasobów przy użyciu administracji zgodnej z zestawem administratorów, którzy będą zarządzać wszystkimi powiązanymi zasobami klucza klienta.
  
> [!IMPORTANT]
> Aby zmaksymalizować dostępność, umieść magazyny kluczy w regionach blisko twojej usługi Microsoft 365 Jeśli na przykład Twoja organizacja usługi Exchange Online znajduje się w programie Ameryka Północna, umieść swoje magazyny kluczy w Ameryka Północna. Jeśli Twoja Exchange Online znajduje się w Europie, umieść swoje magazyny kluczy w Europie.
>
> Użyj wspólnego prefiksu dla magazynów kluczy i dołącz skrót nazwy użycia i zakresu magazynu kluczy (np. dla usługi Contoso SharePoint, w której będą umieszczone magazyny w usłudze Ameryka Północna. Możliwa para nazw to Contoso-CK-SP-NA-VaultA1 i Contoso-CK-SP-NA-VaultA2. Nazwy magazynu są globalnie unikatowymi ciągami w obrębie platformy Azure, więc może być konieczne wypróbowanie odmian żądanych nazw, jeśli odpowiednie nazwy są już żądane przez innych klientów usługi Azure. Od lipca 2017 r. nie można zmieniać nazw magazynu, więc najlepszym rozwiązaniem jest pisemne zaplanowanie konfiguracji i użycie drugiej osoby do sprawdzenia, czy plan został poprawnie wykonany.
>
> Jeśli to możliwe, utwórz swoje magazyny w regionach sparowanych. Sparowane regiony platformy Azure zapewniają wysoką dostępność w różnych domenach błędów usługi. Dlatego pary regionalne można przemyśleć jako region tworzenia kopii zapasowej innych osób. Oznacza to, że zasób platformy Azure, który znajduje się w jednym regionie, automatycznie wykrywa błędy tolerancji za pośrednictwem sparowanego regionu. Z tego powodu wybranie regionów dla dwóch magazynów używanych w zasadach szyfrowania danych, w których regiony są sparowane, oznacza, że są używane tylko dwa regiony dostępności. Większość obszarów geograficznych ma tylko dwa regiony, więc nie można jeszcze wybrać regionów sparowanych. Jeśli to możliwe, wybierz dwa niedo sparowane regiony dla dwóch magazynów używanych z zasadami szyfrowania danych. Korzysta to z czterech regionów dostępności. Aby uzyskać więcej informacji, zobacz Zapewnianie ciągłości działania i odzyskiwanie po awarii [(BCDR):](/azure/best-practices-availability-paired-regions) regiony sparowane platformy Azure, aby uzyskać bieżącą listę par regionalnych.
  
### <a name="assign-permissions-to-each-key-vault"></a>Przypisywanie uprawnień do każdego magazynu kluczy

W zależności od implementacji musisz zdefiniować trzy oddzielne zestawy uprawnień dla każdego magazynu kluczy. Na przykład należy zdefiniować jeden zestaw uprawnień dla każdej z następujących czynności:
  
- **Administratorzy magazynu kluczy** , którzy codziennie zarządzanie magazynem kluczy twojej organizacji. Zadania te obejmują tworzenie, tworzenie, uzyskiwanie, importowanie, tworzenie list i przywracanie.

  > [!IMPORTANT]
  > Zestaw uprawnień przypisanych do administratorów magazynu kluczy nie obejmuje uprawnień do usuwania kluczy. Jest to celowe i ważne rozwiązanie. Usuwanie kluczy szyfrowania nie jest zwykle wykonywane, ponieważ wykonanie tego działania trwale zniszczy dane. W ramach najlepszych rozwiązań domyślnie nie należy udzielać tego uprawnienia administratorom magazynu kluczy. Zamiast tego należy zarezerwować te informacje dla kluczowych współautorów magazynu i przypisać je administratorowi tylko w krótkim czasie, gdy zrozumiałe jest zrozumienie konsekwencji.
  
  Aby przypisać te uprawnienia do użytkownika w twojej organizacji, zaloguj się do swojej subskrypcji platformy Azure za pomocą konta Azure PowerShell. Aby uzyskać instrukcje, [zobacz Logowanie się za pomocą Azure PowerShell](/powershell/azure/authenticate-azureps).

- Uruchom Set-AzKeyVaultAccessPolicy cmdlet, aby przypisać niezbędne uprawnienia.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Przykład:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **Współautorzy kluczowego magazynu,** które mogą zmieniać uprawnienia na platformie Azure Key Vault się. Gdy pracownicy opuszczają Twój zespół lub dołączają do niego, musisz zmienić te uprawnienia. W rzadkich przypadkach, gdy administratorzy magazynu kluczy w uzasadniony sposób potrzebują uprawnienia do usuwania lub przywracania klucza, konieczne jest również zmienianie uprawnień. Ten zestaw kluczowych współautorów magazynu musi mieć udzieloną rolę **Współautor** w Twoim magazynie kluczy. Tę rolę można przypisać przy użyciu usługi Azure Resource Manager. Aby uzyskać szczegółowe instrukcje, [zobacz Role-Based Access Control zarządzania dostępem do zasobów subskrypcji platformy Azure](/azure/active-directory/role-based-access-control-configure). Administrator, który tworzy subskrypcję, ma niejawny dostęp do tej funkcji oraz możliwość przypisywania innych administratorów do roli współautora.

- **Uprawnienia do Microsoft 365** dla każdego magazynu kluczy, który jest potrzebny na potrzeby klucza klienta, musisz nadać zawijanieKey, zakończyć zawijanieKey i uzyskać uprawnienia do odpowiedniego podmiotu zabezpieczeń usługi Microsoft 365 service. 

  Aby nadać uprawnienia do Microsoft 365 zabezpieczeń usługi, uruchom polecenie cmdlet **Set-AzKeyVaultAccessPolicy** przy użyciu następującej składni:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Gdzie:

   - *Nazwa magazynu* to nazwa utworzonego magazynu kluczy.
   - Aby Exchange Online i Skype dla firm, zamień *Office 365 appID na*`00000002-0000-0ff1-ce00-000000000000`
   - W SharePoint plikach online, OneDrive dla Firm i Teams zamień Office 365 *appID* na`00000003-0000-0ff1-ce00-000000000000`
   - W przypadku zasad wielu obciążeń (Exchange, Teams, Microsoft Information Protection) które dotyczą wszystkich użytkowników dzierżawy, zastąp Office 365 *appID*`c066d759-24ae-40e7-a56f-027002b5d3e4`

  Przykład: Ustawianie uprawnień dla Exchange Online i Skype dla firm:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Przykład: Ustawianie uprawnień dla plików SharePoint Online, OneDrive dla Firm i Teams plików:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>Upewnij się, że w magazynach kluczy jest włączona opcja nie programowego usuwania

Gdy możesz szybko odzyskać klucze, mniej prawdopodobne jest, że wystąpi przedłużona usługa, jeśli wystąpi przypadkowe lub złośliwe usunięcie kluczy. Włącz tę konfigurację, określaną mianem "nie miękkiego usunięcia", zanim będzie można używać kluczy z kluczem klienta. Włączenie funkcji nie programowego usuwania pozwala odzyskać klucze lub magazyny w ciągu 90 dni od usunięcia bez konieczności przywracania ich z kopii zapasowej.
  
Aby włączyć opcję Nie programowe usuwanie w magazynach kluczy, wykonaj następujące czynności:
  
1. Zaloguj się do subskrypcji platformy Azure za pomocą aplikacji Windows PowerShell. Aby uzyskać instrukcje, [zobacz Logowanie się za pomocą Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Uruchom polecenie [cmdlet Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) . W tym *przykładzie nazwa magazynu to* nazwa magazynu kluczy, dla którego jest włączanie funkcji "miękkiego usunięcia":

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. Potwierdź, że dla magazynu kluczy skonfigurowano "miękkie usunięcie", uruchamiając polecenie cmdlet **Get-AzKeyVault** . Jeśli funkcja niech będzie prawidłowo skonfigurowana dla magazynu kluczy, właściwość _Niech_ będzie włączona dla tej właściwości zwraca wartość **Prawda**:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>Dodawanie klucza do każdego magazynu kluczy przez utworzenie lub zaimportowanie klucza

Istnieją dwa sposoby dodawania kluczy do usługi Azure Key Vault; klucz można utworzyć bezpośrednio w Key Vault lub zaimportować klucz. Tworzenie klucza bezpośrednio w programie Key Vault jest mniej skomplikowane, ale importowanie klucza zapewnia pełną kontrolę nad tym, jak jest generowany. Użyj klawiszy RSA. Usługa Azure Key Vault nie obsługuje zawijania i rozpakowywania za pomocą klawiszy krzywych wielokropka.
  
Aby utworzyć klucz bezpośrednio w magazynie kluczy, uruchom polecenie cmdlet [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey) w następujący sposób:
  
```powershell
Add-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Destination <HSM|Software> -KeyOps wrapKey,unwrapKey
```

Gdzie:

- *Nazwa magazynu* to nazwa magazynu kluczy, w którym chcesz utworzyć klucz.

- *nazwa klucza* to nazwa, którą chcesz nadać noweowi kluczowi.

  > [!TIP]
  > Klucze nazw używające konwencji nazewnictwa podobnej do opisanej powyżej dla magazynów kluczy. Dzięki temu w narzędziach, w których jest pokazywana tylko nazwa klucza, ciąg samoopisuje.
  
Jeśli klucz ma być zabezpiecziony za pomocą funkcji HSM, należy określić **HSM** jako wartość parametru _Destination_ . W przeciwnym razie należy określić parametr **Software**.

Przykład:
  
```powershell
Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps wrapKey,unwrapKey
```

Aby zaimportować klucz bezpośrednio do magazynu kluczy, musisz mieć moduł nCipher nShield Hardware Security Module.
  
Niektóre organizacje preferują takie podejście do ustanawiania dowiedzenia się, jak korzystać ze swoich kluczy, a następnie ta metoda dostarcza również następujących poświadczenie:
  
- Zestaw narzędzi użyty do importowania zawiera atestowania z nCi Exchange pher, że klucz klucza (KEK) używany do szyfrowania wygenerowanego klucza nie jest eksportowalny i jest generowany wewnątrz oryginalnego HSM, który został wygenerowany przez nCipher.

- Zestaw narzędzi zawiera ateterie z witryny nCipher, że system Azure Key Vault został również wygenerowany na oryginalnym hsm, który jest generowany przez nCipher. Te atestacje udowadniają, że firma Microsoft używa również oryginalnego sprzętu do szyfrowania nCipher.

Skontaktuj się ze swoją grupą zabezpieczeń, aby ustalić, czy wymagane są powyższe atestacje. Aby uzyskać szczegółowy opis kroków tworzenia klucza lokalnie i importowania go do magazynu kluczy, zobacz Jak generować i przenosić klucze chronione przez [HSM dla systemu Azure Key Vault](/azure/key-vault/keys/hsm-protected-keys). Skorzystaj z instrukcji dotyczących platformy Azure, aby utworzyć klucz w każdym magazynie kluczy.
  
### <a name="check-the-recovery-level-of-your-keys"></a>Sprawdzanie poziomu odzyskiwania kluczy

Microsoft 365, aby subskrypcja usługi Azure Key Vault była ustawiona na wartość Nie anulować i że klucze używane przez klucz klienta mają włączone niechybne usuwanie. Możesz potwierdzić ustawienia subskrypcji, patrząc na poziom odzyskiwania kluczy.
  
Aby sprawdzić poziom odzyskiwania klucza, w programie Azure PowerShell uruchom polecenie cmdlet Get-AzKeyVaultKey w następujący sposób:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

Jeśli właściwość _Poziom_ odzyskiwania zwraca inną wartość niż Wartość Subskrypcji Odzyskiwalne **+ChronioneSubskrypcje**, upewnij się, że umieścisz subskrypcję na liście Nie anuluj i że włączono "miękkie usunięcie" dla każdego magazynu kluczy.
  
### <a name="back-up-azure-key-vault"></a>Kopię zapasową usługi Azure Key Vault

Natychmiast po utworzeniu klucza lub jakiejkolwiek zmianie, wykonaj kopię zapasową kopii zapasowej i przechowuj jej kopie zapasowe, zarówno w trybie online, jak i w trybie offline. Nie łącz kopii w trybie offline z dowolną siecią. Zamiast tego należy przechowywać je w lokalizacji offline, takiej jak magazyn fizyczny lub komercyjny. Co najmniej jedna kopia zapasowa powinna być przechowywana w lokalizacji dostępnej na wypadek awarii. Obiekty blob kopii zapasowej są jedynym sposobem przywracania kluczowego materiału w przypadku trwałego Key Vault trwałych trwałych lub renderowania w inny sposób niedziałających obiektów blob. Klucze, które są zewnętrzne dla usługi Azure Key Vault i zaimportowane do usługi Azure Key Vault nie są kwalifikowane jako kopia zapasowa, ponieważ metadane niezbędne do użycia klucza klienta nie istnieją z kluczem zewnętrznym. Tylko kopia zapasowa z platformy Azure Key Vault może być używana do operacji przywracania przy użyciu klucza klienta. Dlatego po przesłaniu lub utworzeniu klucza należy Key Vault kopię zapasową usługi Azure.
  
Aby utworzyć kopię zapasową klucza usługi Azure Key Vault, uruchom polecenie cmdlet [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey) w następujący sposób:

```powershell
Backup-AzKeyVaultKey -VaultName <vault name> -Name <key name>
-OutputFile <filename.backup>
```

Upewnij się, że w pliku wyjściowym jest używany sufiks `.backup`.
  
Plik wyjściowy wynikowy tego polecenia cmdlet jest zaszyfrowany i nie można go używać poza usługą Azure Key Vault. Kopię zapasową można przywrócić tylko w subskrypcji platformy Azure, z której została wykonane kopia zapasowa.
  
> [!TIP]
> Dla pliku wyjściowego wybierz kombinację nazwy magazynu i nazwy klucza. Dzięki temu nazwa pliku będzie samoopisywania. Zapewni to również, że nazwy plików kopii zapasowych nie będą się ze sobą zwijać.
  
Przykład:
  
```powershell
Backup-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -OutputFile Contoso-CK-EX-NA-VaultA1-Key001-Backup-20170802.backup
```

### <a name="validate-azure-key-vault-configuration-settings"></a>Sprawdzanie poprawności ustawień Key Vault Azure

Po poprawności przed użyciem kluczy w funkcji DEP jest opcjonalna, ale zdecydowanie zalecana. Jeśli użyjesz czynności w celu skonfigurowania kluczy i magazynów innych niż opisane w tym artykule, sprawdź kondycję zasobów usługi Azure Key Vault przed skonfigurowaniem klucza klienta.
  
Aby sprawdzić, czy klawisze mają włączoną `get`funkcję , `wrapKey`i `unwrapKey` operacje:
  
Uruchom polecenie [cmdlet Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) w następujący sposób:
  
```powershell
Get-AzKeyVault -VaultName <vault name>
```

W danych wyjściowych odszukaj zasady programu Access i identyfikator Exchange Online (GUID) lub identyfikator SharePoint online (GUID), jeśli to konieczne. Wszystkie trzy z powyższych uprawnień muszą zostać wyświetlone w obszarze Uprawnienia do kluczy.
  
Jeśli konfiguracja zasad dostępu jest niepoprawna, uruchom polecenie cmdlet Set-AzKeyVaultAccessPolicy w następujący sposób:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
```

Na przykład dla Exchange Online i Skype dla firm:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
```

Na przykład dla usług SharePoint Online i OneDrive dla Firm:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
```

Aby sprawdzić, czy data wygaśnięcia nie jest ustawiona dla kluczy, uruchom polecenie cmdlet [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) w następujący sposób:
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

Klucz klienta nie może używać wygasłego klucza. Operacje próbowane z kluczem wygasłym nie powiodą się i prawdopodobnie spowoduje to niepowodzenie usługi. Zdecydowanie zalecamy, aby klucze używane z kluczem klienta nie mają daty wygaśnięcia. Raz ustawionej daty wygaśnięcia nie można usunąć, ale można ją zmienić na inną datę. Jeśli musisz użyć klucza z ustawioną datą wygaśnięcia, zmień wartość wygaśnięcia na 2099-12-31. Klucze z datą wygaśnięcia inną niż 31/12/9999 nie przechodzą Microsoft 365 weryfikacji.
  
Aby zmienić datę wygaśnięcia ustawioną na dowolną wartość inną niż 31/12/9999, uruchom polecenie cmdlet [Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) w następujący sposób:
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Nie ustawiaj dat wygaśnięcia w kluczach szyfrowania, których używasz z kluczem klienta.
  
### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Uzyskiwanie URI dla każdego klucza Key Vault Azure

Po skonfigurowaniu magazynów kluczy i dodaniu kluczy uruchom następujące polecenie, aby uzyskać URI klucza w każdym magazynie kluczy. Tych  URI użyjesz podczas późniejszego tworzenia i przypisywania funkcji DEP, dlatego zapisz te informacje w bezpiecznym miejscu. Uruchom to polecenie raz dla każdego magazynu kluczy.
  
W Azure PowerShell:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>Następne kroki

Po zakończeniu czynności  opisanej w tym artykule możesz już tworzyć i przypisywać dezpops. Aby uzyskać instrukcje, [zobacz Zarządzanie kluczem klienta](customer-key-manage.md).

## <a name="related-articles"></a>Artykuły pokrewne

- [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md)

- [Zarządzanie kluczem klienta](customer-key-manage.md)

- [Tocz lub obracaj klucz klienta lub klucz dostępności](customer-key-availability-key-roll.md)

- [Informacje o kluczu dostępności](customer-key-availability-key-understand.md)

- [Szyfrowanie usługi](office-365-service-encryption.md)