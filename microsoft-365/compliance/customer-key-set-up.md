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
description: Dowiedz się, jak skonfigurować klucz klienta.
ms.openlocfilehash: d285d19eb00afdaea6c5c591caf32a9b4a482987
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642201"
---
# <a name="set-up-customer-key"></a>Konfigurowanie klucza klienta

Za pomocą klucza klienta kontrolujesz klucze szyfrowania organizacji, a następnie konfigurujesz usługę Microsoft 365 tak, aby używała ich do szyfrowania danych magazynowanych w centrach danych firmy Microsoft. Innymi słowy, klucz klienta umożliwia klientom dodawanie warstwy szyfrowania, która należy do nich wraz z kluczami.

Skonfiguruj platformę Azure przed użyciem klucza klienta. W tym artykule opisano kroki, które należy wykonać, aby utworzyć i skonfigurować wymagane zasoby platformy Azure, a następnie przedstawiono kroki konfigurowania klucza klienta. Po skonfigurowaniu platformy Azure należy określić, które zasady, a w związku z tym, które klucze należy przypisać do szyfrowania danych w różnych obciążeniach platformy Microsoft 365 w organizacji. Aby uzyskać więcej informacji na temat klucza klienta lub ogólnego przeglądu, zobacz [Szyfrowanie usługi za pomocą klucza klienta usługi Microsoft Purview](customer-key-overview.md).
  
> [!IMPORTANT]
> Zdecydowanie zalecamy stosowanie najlepszych rozwiązań w tym artykule. Są one wywoływane jako **PORADA** i **WAŻNE**. Klucz klienta zapewnia kontrolę nad głównymi kluczami szyfrowania, których zakres może być tak duży, jak cała organizacja. Oznacza to, że błędy popełniane przy użyciu tych kluczy mogą mieć duży wpływ i mogą powodować przerwy w świadczeniu usług lub nieodwołalną utratę danych.
  
## <a name="before-you-set-up-customer-key"></a>Przed skonfigurowanie klucza klienta

Przed rozpoczęciem upewnij się, że masz odpowiednie subskrypcje platformy Azure i licencje M365/O365 dla swojej organizacji. Musisz używać płatnych subskrypcji platformy Azure. Subskrypcje, które zostały objęte bezpłatną, próbną, sponsorowaną, subskrypcją MSDN i subskrypcjami starszej wersji pomocy technicznej, nie kwalifikują się.

> [!IMPORTANT]
> Prawidłowe licencje M365/O365, które oferują klucz klienta M365, to:
>
> - Office 365 E5
> - Microsoft 365 E5
> - Zgodność platformy Microsoft 365 E5
> - jednostki SKU ładu Microsoft 365 E5 Information Protection &
> - Zabezpieczenia i zgodność platformy Microsoft 365 dla platformy FLW

Istniejące licencje Office 365 Advanced Compliance będą nadal obsługiwane.

Aby zrozumieć pojęcia i procedury opisane w tym artykule, zapoznaj się z dokumentacją [usługi Azure Key Vault](/azure/key-vault/). Zapoznaj się również z terminami używanymi na platformie Azure, na przykład [Azure AD dzierżawy](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant).
  
Jeśli potrzebujesz większej pomocy technicznej poza dokumentacją, skontaktuj się z firmą Microsoft Consulting Services (MCS), Premier Field Engineering (PFE) lub z partnerem firmy Microsoft w celu uzyskania pomocy. Aby przekazać opinię na temat klucza klienta, w tym dokumentację, wyślij swoje pomysły, sugestie i perspektywy do customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Omówienie kroków konfigurowania klucza klienta

Aby skonfigurować klucz klienta, wykonaj te zadania w wymienionej kolejności. W pozostałej części tego artykułu znajdują się szczegółowe instrukcje dotyczące każdego zadania lub linki do dodatkowych informacji dotyczących każdego kroku procesu.
  
**Na platformie Azure i w Microsoft FastTrack:**
  
Większość tych zadań wykonasz zdalnie łącząc się z Azure PowerShell. Aby uzyskać najlepsze wyniki, użyj wersji 4.4.0 lub nowszej Azure PowerShell.
  
- [Tworzenie dwóch nowych subskrypcji platformy Azure](#create-two-new-azure-subscriptions)

- [Prześlij żądanie aktywowania klucza klienta dla Office 365](#submit-a-request-to-activate-customer-key-for-office-365)

- [Rejestrowanie subskrypcji platformy Azure w celu korzystania z obowiązkowego okresu przechowywania](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  Ten proces rejestracji potrwa pięć dni roboczych.
- [Skontaktuj się z odpowiednim aliasem firmy Microsoft, aby kontynuować proces](#contact-the-corresponding-microsoft-alias-to-proceed-with-the-process)

- [Tworzenie Key Vault platformy Azure w warstwie Premium w każdej subskrypcji](#create-a-premium-azure-key-vault-in-each-subscription)

- [Przypisywanie uprawnień do każdego magazynu kluczy](#assign-permissions-to-each-key-vault)

- [Upewnij się, że usuwanie nietrwałe jest włączone w magazynach kluczy](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [Dodawanie klucza do każdego magazynu kluczy przez utworzenie lub zaimportowanie klucza](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Weryfikowanie daty wygaśnięcia kluczy](#verify-expiration-date-of-your-keys)

- [Sprawdzanie poziomu odzyskiwania kluczy](#check-the-recovery-level-of-your-keys)

- [Tworzenie kopii zapasowej usługi Azure Key Vault](#back-up-azure-key-vault)

- [Uzyskiwanie identyfikatora URI dla każdego klucza Key Vault platformy Azure](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Wykonywanie zadań w usłudze Azure Key Vault i Microsoft FastTrack for Customer Key

Wykonaj te zadania na platformie Azure Key Vault. Należy wykonać te kroki dla wszystkich adresów IP używanych z kluczem klienta.
  
### <a name="create-two-new-azure-subscriptions"></a>Tworzenie dwóch nowych subskrypcji platformy Azure

Klucz klienta wymaga dwóch subskrypcji platformy Azure. Najlepszym rozwiązaniem jest, aby firma Microsoft zaleca tworzenie nowych subskrypcji platformy Azure do użycia z kluczem klienta. Klucze usługi Azure Key Vault mogą być autoryzowane tylko dla aplikacji w tej samej dzierżawie usługi Azure Active Directory (Microsoft Azure Active Directory), należy utworzyć nowe subskrypcje przy użyciu tej samej dzierżawy Azure AD używanej w organizacji, do której zostaną przypisane adresy IP. Na przykład przy użyciu konta służbowego, które ma uprawnienia administratora globalnego w organizacji. Aby uzyskać szczegółowe instrukcje, zobacz [Tworzenie konta na platformie Azure jako organizacja](/azure/active-directory/fundamentals/sign-up-organization).
  
> [!IMPORTANT]
> Klucz klienta wymaga dwóch kluczy dla każdej zasady szyfrowania danych (DEP). Aby to osiągnąć, należy utworzyć dwie subskrypcje platformy Azure. Najlepszym rozwiązaniem jest, aby firma Microsoft zaleca, aby w każdej subskrypcji członkowie organizacji konfigurowali jeden klucz. Należy używać tych subskrypcji platformy Azure tylko do administrowania kluczami szyfrowania dla Office 365. Chroni to organizację w przypadku przypadkowego, celowego lub złośliwego usunięcia lub niewłaściwego zarządzania kluczami, za które są odpowiedzialni przez jednego z operatorów.

Nie ma praktycznego limitu liczby subskrypcji platformy Azure, które można utworzyć dla swojej organizacji. Zastosowanie tych najlepszych rozwiązań zminimalizuje wpływ błędu ludzkiego, pomagając jednocześnie zarządzać zasobami używanymi przez klucz klienta.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Prześlij żądanie aktywowania klucza klienta dla Office 365

Po utworzeniu dwóch nowych subskrypcji platformy Azure należy przesłać odpowiednie żądanie oferty klucza klienta w [portalu Microsoft FastTrack](https://fasttrack.microsoft.com/). Wybory w formularzu oferty dotyczące autoryzowanych oznaczeń w organizacji są krytyczne i niezbędne do ukończenia rejestracji klucza klienta. Funkcjonariusze w tych wybranych rolach w organizacji zapewniają autentyczność każdego żądania odwołania i zniszczenia wszystkich kluczy używanych z zasadami szyfrowania danych klucza klienta. Ten krok należy wykonać raz dla każdego typu dep klucza klienta, który ma być używany w organizacji.

**Zespół rozwiązania FastTrack nie zapewnia pomocy dotyczącej klucza klienta. Office 365 po prostu używa portalu FastTrack, aby umożliwić przesłanie formularza i ułatwić nam śledzenie odpowiednich ofert klucza klienta. Po przesłaniu żądania rozwiązania FastTrack skontaktuj się z odpowiednim zespołem ds. dołączania kluczy klienta, aby rozpocząć proces dołączania.**
  
Aby przesłać ofertę aktywowania klucza klienta, wykonaj następujące kroki:
  
1. Zaloguj się do [portalu Microsoft FastTrack](https://fasttrack.microsoft.com/) przy użyciu konta służbowego z uprawnieniami administratora globalnego w organizacji.

2. Po zalogowaniu wybierz odpowiednią domenę.

3. W przypadku wybranej domeny wybierz pozycję **Wdróż** na górnym pasku nawigacyjnym i przejrzyj listę dostępnych ofert.

4. Wybierz kartę informacyjną dla oferty, która ma zastosowanie do Ciebie:

   - **Wiele obciążeń platformy Microsoft 365:** Wybierz **pomoc dotyczącą żądania klucza szyfrowania dla oferty platformy Microsoft 365** .

   - **Exchange Online i Skype dla firm:** wybierz **pomoc Dotyczącą żądania klucza szyfrowania dla oferty programu Exchange**.

   - **Pliki usługi SharePoint Online, OneDrive i Teams:** Wybierz **pomoc dotyczącą żądania klucza szyfrowania dla programu SharePoint i** oferty OneDrive dla Firm.

5. Po przejrzeniu szczegółów oferty wybierz pozycję **Kontynuuj do kroku 2**.

6. Wypełnij wszystkie odpowiednie szczegóły i zażądaj informacji w formularzu oferty. Zwróć szczególną uwagę na wybrane opcje, dla których członkowie organizacji mają być upoważnieni do zatwierdzania trwałego i nieodwracalnego niszczenia kluczy szyfrowania i danych. Po ukończeniu formularza wybierz pozycję **Prześlij**.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Rejestrowanie subskrypcji platformy Azure w celu korzystania z obowiązkowego okresu przechowywania

Tymczasowa lub trwała utrata głównych kluczy szyfrowania może być destrukcyjna lub nawet katastrofalna dla działania usługi i może spowodować utratę danych. Z tego powodu zasoby używane z kluczem klienta wymagają silnej ochrony. Wszystkie zasoby platformy Azure używane z kluczem klienta oferują mechanizmy ochrony wykraczają poza konfigurację domyślną. Możesz tagować lub rejestrować subskrypcje platformy Azure na *obowiązkowy okres przechowywania*. Obowiązkowy okres przechowywania uniemożliwia natychmiastowe i nieodwołalne anulowanie subskrypcji platformy Azure. Kroki wymagane do zarejestrowania subskrypcji platformy Azure na obowiązkowy okres przechowywania wymagają współpracy z zespołem platformy Microsoft 365. Wcześniej obowiązkowy okres przechowywania był czasami określany jako "Nie anuluj". Ten proces potrwa pięć dni roboczych.
  
> [!IMPORTANT]
> Przed skontaktowaniem się z zespołem platformy Microsoft 365 należy wykonać następujące kroki dla **każdej** subskrypcji platformy Azure używanej z kluczem klienta. Przed rozpoczęciem upewnij się, że masz zainstalowany moduł [Azure PowerShell Az](/powershell/azure/new-azureps-module-az).

1. Zaloguj się przy użyciu Azure PowerShell. Aby uzyskać instrukcje, zobacz [Logowanie za pomocą Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Uruchom polecenie cmdlet Register-AzProviderFeature, aby zarejestrować subskrypcje w celu korzystania z obowiązkowego okresu przechowywania. Wykonaj tę akcję dla **każdej** subskrypcji.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

### <a name="contact-the-corresponding-microsoft-alias-to-proceed-with-the-process"></a>Skontaktuj się z odpowiednim aliasem firmy Microsoft, aby kontynuować proces

>[!NOTE]
> Przed skontaktowaniem się z odpowiednim aliasem firmy Microsoft sprawdź, czy wykonano żądania rozwiązania FastTrack dotyczące klucza klienta M365.

- Aby włączyć klucz klienta do przypisywania programu DEP do poszczególnych skrzynek pocztowych Exchange Online, skontaktuj się z [exock@microsoft.com](mailto:exock@microsoft.com).

- Aby włączyć klucz klienta do przypisywania adresów IP do szyfrowania usługi SharePoint Online i OneDrive dla Firm zawartości (w tym plików usługi Teams) dla wszystkich użytkowników dzierżawy, skontaktuj się z [spock@microsoft.com](mailto:spock@microsoft.com).

- Aby włączyć klucz klienta do przypisywania adresów IP do szyfrowania zawartości w wielu obciążeniach platformy Microsoft 365 (Exchange Online, Teams, Microsoft Purview Information Protection) dla wszystkich użytkowników dzierżawy, skontaktuj się z [m365-ck@service.microsoft.com](mailto:m365-ck@service.microsoft.com).

- Dołącz następujące informacje do wiadomości e-mail:

     **Temat**: Klucz klienta dla \<*Your tenant's fully qualified domain name*\>

     **Treść**: uwzględnij identyfikatory żądań rozwiązania FastTrack i identyfikatory subskrypcji dla **każdej** usługi Klucz klienta, do których chcesz się dołączyć. Te identyfikatory subskrypcji to te, które chcesz ukończyć obowiązkowy okres przechowywania i dane wyjściowe Get-AzProviderFeature dla każdej subskrypcji.

Umowa dotycząca poziomu usług (SLA) do ukończenia tego procesu wynosi pięć dni roboczych od powiadomienia (i zweryfikowania) firmy Microsoft o zarejestrowaniu subskrypcji w celu korzystania z obowiązkowego okresu przechowywania.

### <a name="verify-the-status-of-each-your-azure-subscriptions"></a>Weryfikowanie stanu poszczególnych subskrypcji platformy Azure

Po otrzymaniu od firmy Microsoft powiadomienia o zakończeniu rejestracji sprawdź stan rejestracji, uruchamiając polecenie Get-AzProviderFeature w następujący sposób. W przypadku zweryfikowania polecenie Get-AzProviderFeature zwraca wartość **Zarejestrowano** dla właściwości **Stan rejestracji** . Wykonaj ten krok dla **każdej** subskrypcji.

   ```powershell
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

> [!TIP]
> Przed przejściem upewnij się, że wartość "RegistrationState" jest ustawiona na wartość "Zarejestrowano", tak jak na poniższej ilustracji.
>
> ![Obowiązkowy okres przechowywania](../media/MandatoryRetentionPeriod.png)

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Tworzenie Key Vault platformy Azure w warstwie Premium w każdej subskrypcji

Kroki tworzenia magazynu kluczy zostały udokumentowane w [Wprowadzenie z usługą Azure Key Vault](/azure/key-vault/general/overview), która przeprowadzi Cię przez proces instalowania i uruchamiania Azure PowerShell, nawiązywania połączenia z subskrypcją platformy Azure, tworzenia grupy zasobów i tworzenia magazynu kluczy w tej grupie zasobów.
  
Podczas tworzenia magazynu kluczy należy wybrać jednostkę SKU: Standardowa lub Premium. Standardowa jednostka SKU umożliwia ochronę kluczy usługi Azure Key Vault za pomocą oprogramowania — nie ma ochrony kluczy sprzętowego modułu zabezpieczeń (HSM), a jednostka SKU Premium umożliwia korzystanie z modułów HSM w celu ochrony kluczy Key Vault. Klucz klienta akceptuje magazyny kluczy korzystające z dowolnej jednostki SKU, chociaż firma Microsoft zdecydowanie zaleca użycie tylko jednostki SKU Premium. Koszt operacji z kluczami dowolnego typu jest taki sam, więc jedyną różnicą w kosztach jest koszt miesięcznie dla każdego klucza chronionego przez moduł HSM. Aby uzyskać szczegółowe informacje[, zobacz cennik Key Vault](https://azure.microsoft.com/pricing/details/key-vault/).
  
> [!IMPORTANT]
> Używaj magazynów kluczy jednostki SKU w warstwie Premium i kluczy chronionych przez moduł HSM na potrzeby danych produkcyjnych i używaj tylko magazynów kluczy i kluczy jednostki SKU w warstwie Standardowa do celów testowych i walidacyjnych.
  
Dla każdej usługi platformy Microsoft 365, za pomocą której będziesz używać klucza klienta, utwórz magazyn kluczy w każdej z dwóch utworzonych subskrypcji platformy Azure. Aby na przykład umożliwić kluczowi klienta używanie funkcji DEPs w scenariuszach Exchange Online, SharePoint Online i wielu obciążeniach, utworzysz trzy pary magazynów kluczy.
  
Użyj konwencji nazewnictwa dla magazynów kluczy, która odzwierciedla zamierzone użycie programu DEP, z którym będą skojarzone magazyny. Zapoznaj się z sekcją Najlepsze rozwiązania poniżej, aby uzyskać zalecenia dotyczące konwencji nazewnictwa.
  
Utwórz oddzielny, sparowany zestaw magazynów dla każdej zasady szyfrowania danych. W przypadku Exchange Online zakres zasad szyfrowania danych jest wybierany przez Ciebie podczas przypisywania zasad do skrzynki pocztowej. Skrzynka pocztowa może mieć przypisane tylko jedną zasadę i można utworzyć maksymalnie 50 zasad. Zakres zasad usługi SharePoint Online obejmuje wszystkie dane w organizacji w lokalizacji geograficznej lub *geograficznej*. Zakres zasad obejmujących wiele obciążeń obejmuje wszystkie dane w obsługiwanych obciążeniach dla wszystkich użytkowników.

Tworzenie magazynów kluczy wymaga również utworzenia grup zasobów platformy Azure, ponieważ magazyny kluczy wymagają pojemności magazynu (choć małej) i rejestrowania Key Vault, jeśli są włączone, również generują przechowywane dane. Jako najlepsze rozwiązanie firma Microsoft zaleca używanie oddzielnych administratorów do zarządzania każdą grupą zasobów z administracją zgodną z zestawem administratorów, którzy będą zarządzać wszystkimi powiązanymi zasobami klucza klienta.
  
### <a name="assign-permissions-to-each-key-vault"></a>Przypisywanie uprawnień do każdego magazynu kluczy

W zależności od implementacji musisz zdefiniować trzy oddzielne zestawy uprawnień dla każdego magazynu kluczy. Na przykład należy zdefiniować jeden zestaw uprawnień dla każdego z następujących elementów:
  
- **Administratorzy magazynu kluczy** , którzy wykonują codzienne zarządzanie magazynem kluczy w organizacji. Te zadania obejmują tworzenie kopii zapasowych, tworzenie, pobieranie, importowanie, wyświetlanie listy i przywracanie.

  > [!IMPORTANT]
  > Zestaw uprawnień przypisanych do administratorów magazynu kluczy nie zawiera uprawnień do usuwania kluczy. Jest to celowe i ważne rozwiązanie. Usuwanie kluczy szyfrowania zwykle nie jest wykonywane, ponieważ trwale niszczy dane. Najlepszym rozwiązaniem jest domyślne przyznanie tego uprawnienia administratorom magazynu kluczy. Zamiast tego zarezerwuj tę wartość dla współautorów magazynu kluczy i przypisz ją administratorowi tylko w krótkim okresie, gdy poznasz jasne zrozumienie konsekwencji.
  
  Aby przypisać te uprawnienia do użytkownika w organizacji, zaloguj się do subskrypcji platformy Azure przy użyciu Azure PowerShell. Aby uzyskać instrukcje, zobacz [Logowanie za pomocą Azure PowerShell](/powershell/azure/authenticate-azureps).

  - Uruchom polecenie cmdlet Set-AzKeyVaultAccessPolicy, aby przypisać niezbędne uprawnienia.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Przykład:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **Współautorzy magazynu kluczy**, którzy mogą zmieniać uprawnienia na platformie Azure Key Vault. Musisz zmienić te uprawnienia, gdy pracownicy odejdą lub dołączą do Twojego zespołu. W rzadkich sytuacjach, gdy administratorzy magazynu kluczy zgodnie z prawem potrzebują uprawnień do usuwania lub przywracania klucza, musisz również zmienić uprawnienia. Ten zestaw współautorów magazynu kluczy musi mieć przypisaną rolę **Współautor** w magazynie kluczy. Tę rolę można przypisać przy użyciu usługi Azure Resource Manager. Aby uzyskać szczegółowe instrukcje, zobacz [Używanie Role-Based Access Control do zarządzania dostępem do zasobów subskrypcji platformy Azure](/azure/active-directory/role-based-access-control-configure). Administrator, który tworzy subskrypcję, ma ten dostęp niejawnie oraz możliwość przypisywania innych administratorów do roli Współautor.

- **Uprawnienia do aplikacji platformy Microsoft 365** dla każdego magazynu kluczy, którego używasz dla klucza klienta, należy nadać kluczowi wrapKey, unwrapKey i uzyskać uprawnienia do odpowiedniej jednostki usługi Platformy Microsoft 365.

  Aby nadać uprawnienia jednostce usługi Platformy Microsoft 365, uruchom polecenie cmdlet **Set-AzKeyVaultAccessPolicy** przy użyciu następującej składni:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Gdzie:
   - *Nazwa magazynu* to nazwa utworzonego magazynu kluczy.
   - W przypadku Exchange Online i Skype dla firm zastąp *Office 365 identyfikatorem appID*`00000002-0000-0ff1-ce00-000000000000`
   - W przypadku plików usługi SharePoint Online, OneDrive dla Firm i Teams zastąp *Office 365 identyfikatorem appID*`00000003-0000-0ff1-ce00-000000000000`
   - W przypadku zasad obejmujących wiele obciążeń (Exchange, Teams, Microsoft Purview Information Protection), które mają zastosowanie do wszystkich użytkowników dzierżawy, zastąp *Office 365 identyfikatorem appID*`c066d759-24ae-40e7-a56f-027002b5d3e4`

  Przykład: ustawianie uprawnień dla Exchange Online i Skype dla firm:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Przykład: ustawianie uprawnień dla plików usługi SharePoint Online, OneDrive dla Firm i Teams:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

  Potwierdź, że do **każdego** magazynu kluczy są przyznawane polecenia cmdlet *Get, wrapKey i unwrapKey*, uruchamiając polecenie cmdlet *Get-AzKeyVault*.

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```  

> [!Tip]
> Przed przejściem upewnij się, że uprawnienia są prawidłowo skonfigurowane dla magazynu *kluczy. Uprawnienia do kluczy będą zwracać* **wartość wrapKey, unwrapKey i get**.
> Upewnij się, że uprawnienia zostały poprawione do odpowiedniej usługi, do którą się dołączasz. Poniżej wymieniono *nazwę wyświetlaną* każdej usługi:  
  >
  > - Exchange Online i Skype dla firm: *Office 365 Exchange Online*
  > - Pliki usługi SharePoint Online, OneDrive i Teams: *Office 365 SharePoint Online*
  > - Wiele obciążeń platformy Microsoft 365: *M365DataAtRestEncryption*
  >  
  > Na przykład poniższy fragment kodu jest przykładem upewnienia się, że uprawnienia są skonfigurowane dla biblioteki M365DataAtRestEncryption. Poniższe polecenie cmdlet z magazynem o nazwie *mmcexchangevault* wyświetli następujące pola.
  >
  > ```powershell
  >   Get-AzKeyVault -VaultName mmcexchangevault | fl
  >   ```  
  >
  >
  > ![Szyfry szyfrowania dla Exchange Online klucza klienta.](../media/KeyVaultPermissions.png)

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>Upewnij się, że usuwanie nietrwałe jest włączone w magazynach kluczy

Jeśli możesz szybko odzyskać klucze, rzadziej występuje rozszerzona awaria usługi z powodu przypadkowego lub złośliwego usunięcia kluczy. Włącz tę konfigurację, nazywaną usuwaniem nietrwałym, zanim będzie można używać kluczy z kluczem klienta. Włączenie usuwania nietrwałego umożliwia odzyskanie kluczy lub magazynów w ciągu 90 dni od usunięcia bez konieczności przywracania ich z kopii zapasowej.
  
Aby włączyć usuwanie nietrwałe w magazynach kluczy, wykonaj następujące kroki:
  
1. Zaloguj się do subskrypcji platformy Azure przy użyciu Windows PowerShell. Aby uzyskać instrukcje, zobacz [Logowanie za pomocą Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Uruchom polecenie cmdlet [Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) . W tym *przykładzie nazwa magazynu* to nazwa magazynu kluczy, dla którego włączasz usuwanie nietrwałe:

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. Potwierdź, że dla magazynu kluczy skonfigurowano usuwanie nietrwałe, uruchamiając polecenie cmdlet **Get-AzKeyVault** . Jeśli usuwanie nietrwałe jest poprawnie skonfigurowane dla magazynu kluczy, właściwość *Soft Delete Enabled* zwraca wartość **True**:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

> [!TIP]
> Przed przejściem upewnij się, że opcja "Usuwanie nietrwałe jest włączona?" jest ustawiona na wartość "True", podobnie jak na poniższej ilustracji.
>
> <img src="../media/SoftDeleteEnabled.png" alt="SoftDelete" width="400"/>

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>Dodawanie klucza do każdego magazynu kluczy przez utworzenie lub zaimportowanie klucza

Istnieją dwa sposoby dodawania kluczy do Key Vault platformy Azure. Klucz można utworzyć bezpośrednio w Key Vault lub zaimportować klucz. Tworzenie klucza bezpośrednio w Key Vault jest mniej skomplikowane, ale importowanie klucza zapewnia całkowitą kontrolę nad sposobem generowania klucza. Użyj kluczy RSA. Usługa Azure Key Vault nie obsługuje opakowywania i rozpakowywania za pomocą kluczy krzywej eliptycznej.

Aby uzyskać instrukcje dotyczące dodawania klucza do każdego magazynu, zobacz [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey).

 Aby uzyskać szczegółowe instrukcje tworzenia klucza lokalnego i importowania go do magazynu kluczy, zobacz [Jak generować i transferować klucze chronione przez moduł HSM dla usługi Azure Key Vault](/azure/key-vault/keys/hsm-protected-keys). Użyj instrukcji platformy Azure, aby utworzyć klucz w każdym magazynie kluczy.

### <a name="verify-expiration-date-of-your-keys"></a>Weryfikowanie daty wygaśnięcia kluczy

Aby sprawdzić, czy data wygaśnięcia nie jest ustawiona dla kluczy, uruchom polecenie cmdlet [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) w następujący sposób:
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

Klucz klienta nie może używać wygasłego klucza. Operacje podejmowane przy użyciu wygasłego klucza nie powiodą się i prawdopodobnie spowodują awarię usługi. Zdecydowanie zalecamy, aby klucze używane z kluczem klienta nie miały daty wygaśnięcia. Nie można usunąć daty wygaśnięcia po ustawieniu, ale można ją zmienić na inną datę. Jeśli należy użyć klucza z ustawioną datą wygaśnięcia, zmień wartość wygaśnięcia na 12/31/9999. Klucze z datą wygaśnięcia ustawioną na datę inną niż 12/31/9999 nie przejdą weryfikacji platformy Microsoft 365.
  
Aby zmienić datę wygaśnięcia ustawioną na dowolną wartość inną niż 12/31/9999, uruchom polecenie cmdlet [Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) w następujący sposób:
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Nie ustawiaj dat wygaśnięcia kluczy szyfrowania używanych z kluczem klienta.  

### <a name="check-the-recovery-level-of-your-keys"></a>Sprawdzanie poziomu odzyskiwania kluczy

Platforma Microsoft 365 wymaga, aby subskrypcja usługi Azure Key Vault została ustawiona na Nie anuluj, a klucze używane przez klucz klienta mają włączone usuwanie nietrwałe. Możesz potwierdzić ustawienia subskrypcji, sprawdzając poziom odzyskiwania kluczy.
  
Aby sprawdzić poziom odzyskiwania klucza, w Azure PowerShell uruchom polecenie cmdlet Get-AzKeyVaultKey w następujący sposób:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

> [!Tip]
> Przed przejściem dalej, jeśli właściwość *Poziom odzyskiwania* zwraca coś innego niż wartość **Recoveryable+ProtectedSubscription**, upewnij się, że *zarejestrowano funkcję MandatoryRetentionPeriodEnabled* w subskrypcji i czy dla każdego z magazynów kluczy włączono usuwanie nietrwałe.
>
>    <img src="../media/RecoveryLevel.png" alt="drawing" width="500"/>

### <a name="back-up-azure-key-vault"></a>Tworzenie kopii zapasowej usługi Azure Key Vault

Bezpośrednio po utworzeniu lub zmianie klucza wykonaj kopię zapasową i zapisz kopie kopii zapasowej, zarówno w trybie online, jak i offline.
Aby utworzyć kopię zapasową klucza usługi Azure Key Vault, uruchom polecenie cmdlet [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey).

### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Uzyskiwanie identyfikatora URI dla każdego klucza Key Vault platformy Azure

Po skonfigurowaniu magazynów kluczy i dodaniu kluczy uruchom następujące polecenie, aby uzyskać identyfikator URI klucza w każdym magazynie kluczy. Te identyfikatory URI będą używane podczas tworzenia i przypisywania każdego programu DEP później, więc zapisz te informacje w bezpiecznym miejscu. Uruchom to polecenie raz dla każdego magazynu kluczy.
  
W Azure PowerShell:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>Następne kroki

Po wykonaniu kroków opisanych w tym artykule możesz przystąpić do tworzenia i przypisywania adresów IP. Aby uzyskać instrukcje, zobacz [Zarządzanie kluczem klienta](customer-key-manage.md).

## <a name="related-articles"></a>Powiązane artykuły:

- [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md)

- [Zarządzanie kluczem klienta](customer-key-manage.md)

- [Tocz lub obracaj klucz klienta lub klucz dostępności](customer-key-availability-key-roll.md)

- [Dowiedz się więcej o kluczu dostępności](customer-key-availability-key-understand.md)

- [Szyfrowanie usługi](office-365-service-encryption.md)
