---
title: Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/13/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Dowiedz się, jak przyspieszyć dostarczanie zasobów usługi SharePoint Online za pomocą Office 365 Content Delivery Network (CDN).
ms.openlocfilehash: 42836fa8a43b7251be27cfd841b67d47e12b036e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092012"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online

Wbudowane Office 365 Content Delivery Network (CDN) umożliwiają hostowanie zasobów statycznych w celu zapewnienia lepszej wydajności stron usługi SharePoint Online. Office 365 CDN zwiększa wydajność, buforując zasoby statyczne bliżej przeglądarek żądających ich, co pomaga przyspieszyć pobieranie i zmniejszyć opóźnienia. Ponadto Office 365 CDN używa [protokołu HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) w celu zwiększenia kompresji i potoków HTTP. Usługa Office 365 CDN jest uwzględniona w ramach subskrypcji usługi SharePoint Online.

> [!NOTE]
> Office 365 CDN jest dostępna tylko dla dzierżawców w chmurze **produkcyjnej** (na całym świecie). Dzierżawy w chmurach rządowych USA, Chin i Niemiec nie obsługują obecnie Office 365 CDN.

Office 365 CDN składa się z wielu sieci CDN, które umożliwiają hostowanie zasobów statycznych w wielu lokalizacjach lub _źródłach_ oraz obsługę ich z globalnych sieci o dużej szybkości. W zależności od rodzaju zawartości, którą chcesz hostować w Office 365 CDN, możesz dodać **źródła publiczne**, **źródła prywatne** lub oba te elementy. Zobacz [Wybieranie, czy każde źródło powinno być publiczne, czy prywatne](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) , aby uzyskać więcej informacji na temat różnicy między źródłami publicznymi i prywatnymi.

![Office 365 CDN diagram koncepcyjny.](../media/O365-CDN/o365-cdn-flow-transparent.png "Office 365 CDN diagram koncepcyjny")

Jeśli znasz już sposób działania sieci CDN, musisz wykonać tylko kilka kroków, aby włączyć Office 365 CDN dla dzierżawy. W tym temacie opisano sposób. Przeczytaj dalej, aby uzyskać informacje o tym, jak rozpocząć hostowanie zasobów statycznych.

> [!TIP]
> Istnieją inne sieci CDN hostowane przez firmę Microsoft, które mogą być używane z Office 365 dla wyspecjalizowanych scenariuszy użycia, ale nie są omawiane w tym temacie, ponieważ wykraczają poza zakres Office 365 CDN. Aby uzyskać więcej informacji, zobacz [Inne sieci CDN firmy Microsoft](content-delivery-networks.md#other-microsoft-cdns).

 **Wróć do [pozycji Planowanie sieci i dostrajanie wydajności dla Office 365](./network-planning-and-performance.md).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>Omówienie pracy z Office 365 CDN w usłudze SharePoint Online

Aby skonfigurować Office 365 CDN dla organizacji, wykonaj następujące podstawowe kroki:

+ [Planowanie wdrożenia Office 365 CDN](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [Określ zasoby statyczne, które chcesz hostować na CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [Określ miejsce przechowywania zasobów](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets). Ta lokalizacja może być SharePoint lokacją, biblioteką lub folderem i jest nazywana _źródłem_.
  + [Określ, czy każde źródło powinno być publiczne, czy prywatne](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Można dodać wiele źródeł typów publicznych i prywatnych.

+ Skonfiguruj i skonfiguruj CDN przy użyciu programu PowerShell lub interfejsu wiersza polecenia dla Microsoft 365

  + [Konfigurowanie i konfigurowanie CDN przy użyciu powłoki zarządzania SharePoint Online](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [Konfigurowanie i konfigurowanie CDN przy użyciu programu PowerShell PnP](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [Skonfiguruj i skonfiguruj CDN przy użyciu interfejsu wiersza polecenia dla Microsoft 365](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  Po wykonaniu tego kroku będziesz mieć następujące elementy:

  + Włączono CDN dla organizacji.
  + Dodano źródła identyfikujące każde źródło jako publiczne lub prywatne.

Po zakończeniu instalacji możesz [zarządzać Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNManage) w czasie, wykonując następujące czynności:

+ Dodawanie, aktualizowanie i usuwanie zasobów
+ Dodawanie i usuwanie źródeł
+ Konfigurowanie zasad CDN
+ W razie potrzeby wyłączenie CDN

Na koniec zobacz [Korzystanie z zasobów CDN](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets), aby dowiedzieć się więcej na temat uzyskiwania dostępu do zasobów CDN zarówno ze źródeł publicznych, jak i prywatnych.

Aby uzyskać wskazówki dotyczące rozwiązywania typowych problemów[, zobacz Rozwiązywanie problemów z Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting).

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Planowanie wdrożenia Office 365 CDN

Przed wdrożeniem Office 365 CDN dla dzierżawy Office 365 należy wziąć pod uwagę następujące czynniki w ramach procesu planowania.

  + [Określanie zasobów statycznych, które chcesz hostować w CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [Określanie miejsca przechowywania zasobów](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [Określ, czy każde źródło powinno być publiczne, czy prywatne](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Określanie zasobów statycznych, które chcesz hostować w CDN

Ogólnie rzecz biorąc, sieci CDN są najskuteczniejsze w przypadku hostowania _zasobów statycznych_ lub zasobów, które nie zmieniają się zbyt często. Dobrą regułą jest zidentyfikowanie plików spełniających niektóre lub wszystkie z tych warunków:

+ Pliki statyczne osadzone na stronie (na przykład skrypty i obrazy), które mogą mieć znaczący przyrostowy wpływ na czas ładowania strony
+ Duże pliki, takie jak pliki wykonywalne i pliki instalacyjne
+ Biblioteki zasobów obsługujące kod po stronie klienta

Na przykład małe pliki, które są wielokrotnie żądane, takie jak obrazy witryn i skrypty, mogą znacznie poprawić wydajność renderowania witryn i przyrostowo zmniejszyć obciążenie witryn usługi SharePoint Online po dodaniu ich do źródła CDN. Większe pliki, takie jak pliki wykonywalne instalacji, można pobrać z CDN, zapewniając pozytywny wpływ na wydajność, a następnie zmniejszyć obciążenie witryny SharePoint Online, nawet jeśli nie są one często dostępne.

Poprawa wydajności dla każdego pliku zależy od wielu czynników, w tym bliskości klienta do najbliższego punktu końcowego CDN, przejściowych warunków w sieci lokalnej itd. Wiele plików statycznych jest dość małych i można je pobrać z Office 365 w mniej niż sekundę. Jednak strona internetowa może zawierać wiele plików osadzonych z skumulowanym czasem pobierania wynoszącym kilka sekund. Obsługa tych plików z CDN może znacznie skrócić ogólny czas ładowania strony. Zobacz [Przykład Jaki wzrost wydajności zapewnia CDN?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Określanie miejsca przechowywania zasobów

CDN pobiera zasoby z lokalizacji nazywanej _źródłem_. Źródłem może być witryna SharePoint, biblioteka dokumentów lub folder dostępny za pomocą adresu URL. Masz dużą elastyczność podczas określania źródeł dla swojej organizacji. Można na przykład określić wiele źródeł lub pojedyncze źródło, w którym chcesz umieścić wszystkie CDN zasoby. Możesz wybrać zarówno publiczne, jak i prywatne źródła dla swojej organizacji. Większość organizacji zdecyduje się zaimplementować kombinację tych dwóch.

Możesz utworzyć nowy kontener dla źródeł, takich jak foldery lub biblioteki dokumentów, i dodać pliki, które chcesz udostępnić z CDN. Jest to dobre podejście, jeśli masz określony zestaw zasobów, które mają być dostępne z CDN i chcesz ograniczyć zestaw zasobów CDN tylko do tych plików w kontenerze.

Istnieje również możliwość skonfigurowania istniejącego zbioru witryn, witryny, biblioteki lub folderu jako źródła, co umożliwi udostępnienie wszystkich kwalifikujących się zasobów w kontenerze z CDN. Przed dodaniem istniejącego kontenera jako źródła należy upewnić się, że znasz jego zawartość i uprawnienia, aby nie ujawniać przypadkowo zasobów dostępowi anonimowemu lub nieautoryzowanym użytkownikom.

Możesz zdefiniować _zasady CDN_, aby wykluczyć zawartość w źródłach z CDN. CDN zasady wykluczają zasoby w źródłach publicznych lub prywatnych według atrybutów, takich jak _typ pliku_ i _klasyfikacja lokacji_, i są stosowane do wszystkich źródeł typu CdnType (prywatnego lub publicznego) określonego w zasadach. Jeśli na przykład dodasz prywatne źródło składające się z witryny zawierającej wiele podwitryn, możesz zdefiniować zasady wykluczające witryny oznaczone jako **Poufne**, aby zawartość z witryn z zastosowaną klasyfikacją nie była obsługiwana z CDN. Zasady zostaną zastosowane do zawartości ze _wszystkich_ źródeł prywatnych dodanych do CDN.

Należy pamiętać, że tym większa liczba źródeł, tym większy wpływ na czas przetwarzania żądań przez usługę CDN. Zalecamy maksymalne ograniczenie liczby źródeł.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Określ, czy każde źródło powinno być publiczne, czy prywatne

Podczas identyfikowania źródła należy określić, czy ma być _ono publiczne_ , czy _prywatne_. Dostęp do zasobów CDN w źródłach publicznych jest anonimowy, a zawartość CDN w prywatnych źródłach jest zabezpieczona przez dynamicznie generowane tokeny w celu zwiększenia bezpieczeństwa. Niezależnie od wybranej opcji firma Microsoft wykonuje wszystkie ciężkie operacje, jeśli chodzi o administrowanie CDN. Ponadto możesz zmienić zdanie później, po skonfigurowaniu CDN i zidentyfikowaniu źródeł.

Zarówno opcje publiczne, jak i prywatne zapewniają podobny wzrost wydajności, ale każdy z nich ma unikatowe atrybuty i zalety.

**Źródła publiczne** w Office 365 CDN są dostępne anonimowo, a dostęp do hostowanych zasobów może uzyskać każdy, kto ma adres URL zasobu. Ponieważ dostęp do zawartości w źródłach publicznych jest anonimowy, należy ich używać tylko do buforowania niewrażliwej zawartości ogólnej, takiej jak pliki JavaScript, skrypty, ikony i obrazy.

**Prywatne** źródła w Office 365 CDN zapewniają prywatny dostęp do zawartości użytkownika, takiej jak biblioteki dokumentów SharePoint Online, witryny i zastrzeżone obrazy. Dostęp do zawartości w prywatnych źródłach jest zabezpieczony za pomocą dynamicznie generowanych tokenów, dzięki czemu użytkownicy mogą uzyskiwać do niej dostęp tylko z uprawnieniami do oryginalnej biblioteki dokumentów lub lokalizacji magazynu. Źródła prywatne w Office 365 CDN mogą być używane tylko dla zawartości SharePoint Online i można uzyskiwać dostęp tylko do zasobów w prywatnych źródłach poprzez przekierowanie z dzierżawy usługi SharePoint Online.

Więcej informacji o tym, jak działa CDN dostęp do zasobów w prywatnym pochodzeniu, można znaleźć w [temacie Używanie zasobów w źródłach prywatnych](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Atrybuty i zalety hostowania zasobów w źródłach publicznych

+ Zasoby uwidocznione w publicznym pochodzeniu są dostępne dla wszystkich użytkowników anonimowo.
    > [!IMPORTANT]
    > Nigdy nie należy umieszczać zasobów, które zawierają informacje o użytkowniku lub są uważane za wrażliwe dla organizacji w publicznym pochodzeniu.

+ Jeśli usuniesz zasób ze źródła publicznego, zasób może być nadal dostępny przez maksymalnie 30 dni z pamięci podręcznej; Jednak w ciągu 15 minut unieważnimy linki do zasobu w CDN.

+ W przypadku hostowania arkuszy stylów (plików CSS) w publicznym pochodzeniu można użyć ścieżek względnych i identyfikatorów URI w kodzie. Oznacza to, że można odwoływać się do lokalizacji obrazów tła i innych obiektów względem lokalizacji elementu zawartości, który go wywołuje.

+ Chociaż możesz utworzyć adres URL źródła publicznego, należy zachować ostrożność i upewnić się, że używasz właściwości kontekstu strony i postępuj zgodnie ze wskazówkami. Przyczyną jest to, że jeśli dostęp do CDN stanie się niedostępny, adres URL nie zostanie automatycznie rozpoznany w organizacji w usłudze SharePoint Online i może spowodować przerwanie linków i inne błędy. Adres URL może również ulec zmianie, dlatego nie powinien być tylko zakodowany na stałe do bieżącej wartości.

+ Domyślne typy plików dołączone do źródeł publicznych to .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff i .woff2. Możesz określić dodatkowe typy plików.

+ Można skonfigurować zasady wykluczania zasobów, które zostały zidentyfikowane przez określone klasyfikacje lokacji. Na przykład można wykluczyć wszystkie zasoby oznaczone jako "poufne" lub "ograniczone", nawet jeśli są one dozwolonym typem pliku i znajdują się w publicznym pochodzeniu.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Atrybuty i zalety hostowania zasobów w źródłach prywatnych

+ Źródła prywatne mogą być używane tylko dla zasobów SharePoint Online.

+ Użytkownicy mogą uzyskiwać dostęp do zasobów z prywatnego źródła tylko wtedy, gdy mają uprawnienia dostępu do kontenera. Dostęp anonimowy do tych zasobów jest uniemożliwiany.

+ Zasoby w prywatnych źródłach muszą być kierowane z dzierżawy usługi SharePoint Online. Bezpośredni dostęp do zasobów prywatnych CDN nie działa.

+ Jeśli usuniesz zasób z prywatnego źródła, zasób może być nadal dostępny przez maksymalnie godzinę z pamięci podręcznej; Jednak w ciągu 15 minut od usunięcia zasobu unieważnimy linki do zasobu w CDN.

+ Domyślne typy plików dołączone do źródeł prywatnych to .gif, .ico, jpeg, .jpg, .js i .png. Możesz określić dodatkowe typy plików.

+ Podobnie jak w przypadku źródeł publicznych, można skonfigurować zasady wykluczania zasobów, które zostały zidentyfikowane przez klasyfikacje lokacji, które zostały określone, nawet jeśli używasz symboli wieloznacznych do dołączania wszystkich zasobów w bibliotece folderów lub dokumentów.

Aby uzyskać więcej informacji na temat sposobu używania Office 365 CDN, ogólnych CDN pojęć i innych sieci CDN firmy Microsoft, których można używać z dzierżawą Office 365, zobacz [Content Delivery Networks (Sieci dostarczania zawartości](content-delivery-networks.md)).

### <a name="default-cdn-origins"></a>Domyślne źródła CDN

Jeśli nie określono inaczej, Office 365 skonfigurować domyślne źródła po włączeniu Office 365 CDN. Jeśli początkowo nie chcesz ich aprowizować, możesz dodać te źródła po zakończeniu konfiguracji. Jeśli nie rozumiesz konsekwencji pominięcia konfiguracji domyślnych źródeł i nie masz do tego konkretnego powodu, należy zezwolić na ich utworzenie po włączeniu CDN.

Domyślne źródła CDN prywatnej:

+ \*/userphoto.aspx
+ \*/siteassets

Domyślne źródła CDN publicznego:

+ \*/masterpage
+ \*/style library
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_ to domyślne publiczne źródło, które zostało dodane do usługi Office 365 CDN w grudniu 2017 r. To źródło musi być obecne, aby SharePoint Framework rozwiązania w CDN działały. Jeśli włączono Office 365 CDN przed grudniem 2017 r. lub pominięto konfigurację domyślnych źródeł po włączeniu CDN, możesz ręcznie dodać to źródło. Aby uzyskać więcej informacji, zobacz [Mój składnik Web Part po stronie klienta lub SharePoint Framework rozwiązanie nie działa](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Konfigurowanie i konfigurowanie Office 365 CDN przy użyciu powłoki zarządzania SharePoint Online

Procedury opisane w tej sekcji wymagają użycia powłoki zarządzania SharePoint Online w celu nawiązania połączenia z usługą SharePoint Online. Aby uzyskać instrukcje, zobacz [Połączenie do programu PowerShell SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Wykonaj te kroki, aby skonfigurować i skonfigurować CDN do hostowania zasobów w usłudze SharePoint Online przy użyciu powłoki zarządzania SharePoint Online.

<details>
  <summary>Kliknij, aby rozwinąć</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Umożliwianie organizacji korzystania z Office 365 CDN

Przed wprowadzeniem zmian w ustawieniach CDN dzierżawy należy pobrać bieżący stan konfiguracji CDN prywatnej w dzierżawie Office 365. Połączenie do dzierżawy przy użyciu powłoki zarządzania SharePoint Online:

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Teraz użyj polecenia cmdlet **Get-SPOTenantCdnEnabled**, aby pobrać ustawienia stanu CDN z dzierżawy:

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

Stan CDN dla określonego typu CdnType zostanie wyświetlony na ekranie.

Użyj polecenia cmdlet **Set-SPOTenantCdnEnabled**, aby umożliwić organizacji korzystanie z Office 365 CDN. Możesz zezwolić organizacji na używanie źródeł publicznych, źródeł prywatnych lub obu tych źródeł jednocześnie. Można również skonfigurować CDN, aby pominąć konfigurację domyślnych źródeł po jej włączeniu. Zawsze można dodać te źródła później, zgodnie z opisem w tym temacie.

W Windows PowerShell dla usługi SharePoint Online:

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Aby na przykład umożliwić organizacji używanie źródeł publicznych i prywatnych, wpisz następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Aby umożliwić organizacji używanie źródeł publicznych i prywatnych, ale pomijanie konfigurowania domyślnych źródeł, wpisz następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Zobacz [Domyślne źródła CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins), aby uzyskać informacje o źródłach aprowizowanych domyślnie po włączeniu Office 365 CDN oraz potencjalnym wpływie pominięcia konfiguracji domyślnych źródeł.

Aby umożliwić organizacji korzystanie z źródeł publicznych, wpisz następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Aby umożliwić organizacji korzystanie z prywatnych źródeł, wpisz następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet, zobacz [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Zmień listę typów plików do uwzględnienia w Office 365 CDN (opcjonalnie)

> [!TIP]
> Podczas definiowania typów plików przy użyciu polecenia cmdlet **Set-SPOTenantCdnPolicy** należy zastąpić aktualnie zdefiniowaną listę. Jeśli chcesz dodać dodatkowe typy plików do listy, najpierw użyj polecenia cmdlet, aby dowiedzieć się, jakie typy plików są już dozwolone i uwzględnić je na liście wraz z nowymi.

Użyj polecenia cmdlet **Set-SPOTenantCdnPolicy**, aby zdefiniować statyczne typy plików, które mogą być hostowane przez źródła publiczne i prywatne w CDN. Domyślnie dozwolone są typowe typy zasobów, na przykład css, .gif, .jpg i .js.

W Windows PowerShell dla usługi SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Aby na przykład umożliwić CDN hostowanie plików css i .png, należy wprowadzić polecenie:

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Aby zobaczyć, jakie typy plików są obecnie dozwolone przez CDN, użyj polecenia cmdlet **Get-SPOTenantCdnPolicies**:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Aby uzyskać więcej informacji na temat tych poleceń cmdlet, zobacz [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) i [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Zmień listę klasyfikacji lokacji, które chcesz wykluczyć z Office 365 CDN (opcjonalnie)

> [!TIP]
> W przypadku wykluczania klasyfikacji lokacji przy użyciu polecenia cmdlet **Set-SPOTenantCdnPolicy** należy zastąpić aktualnie zdefiniowaną listę. Jeśli chcesz wykluczyć dodatkowe klasyfikacje lokacji, najpierw użyj polecenia cmdlet, aby dowiedzieć się, jakie klasyfikacje są już wykluczone, a następnie dodać je wraz z nowymi.

Użyj polecenia cmdlet **Set-SPOTenantCdnPolicy**, aby wykluczyć klasyfikacje lokacji, których nie chcesz udostępniać za pośrednictwem CDN. Domyślnie klasyfikacje witryn nie są wykluczone.

W Windows PowerShell dla usługi SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Aby zobaczyć, jakie klasyfikacje lokacji są obecnie ograniczone, użyj polecenia cmdlet **Get-SPOTenantCdnPolicies** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Właściwości, które zostaną zwrócone, to _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ i _ExcludeIfNoScriptDisabled_.

_Właściwość IncludeFileExtensions_ zawiera listę rozszerzeń plików, które będą obsługiwane z CDN.

> [!NOTE]
> Domyślne rozszerzenia plików różnią się między publicznymi i prywatnymi.

_Właściwość ExcludeRestrictedSiteClassifications_ zawiera klasyfikacje lokacji, które chcesz wykluczyć z CDN. Można na przykład wykluczyć witryny oznaczone jako **Poufne**, aby zawartość z witryn z zastosowaną klasyfikacją nie była obsługiwana z CDN.

_Właściwość ExcludeIfNoScriptDisabled_ wyklucza zawartość z CDN na podstawie ustawień atrybutu _NoScript_ na poziomie lokacji. Domyślnie atrybut _NoScript_ jest ustawiony na **wartość Włączone** dla _nowoczesnych_ witryn i **Wyłączone** dla lokacji _klasycznych_ . Zależy to od ustawień dzierżawy.

Aby uzyskać więcej informacji na temat tych poleceń cmdlet, zobacz [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) i [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Dodawanie źródła dla zasobów

Użyj polecenia cmdlet **Add-SPOTenantCdnOrigin** , aby zdefiniować źródło. Można zdefiniować wiele źródeł. Źródło to adres URL wskazujący bibliotekę SharePoint lub folder zawierający zasoby, które mają być hostowane przez CDN.

> [!IMPORTANT]
> Nigdy nie należy umieszczać zasobów, które zawierają informacje o użytkowniku lub są uważane za wrażliwe dla organizacji w publicznym pochodzeniu.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Wartość _ścieżki_ to ścieżka względna do biblioteki lub folderu zawierającego zasoby. Oprócz ścieżek względnych można używać symboli wieloznacznych. Źródła obsługują symbole wieloznaczne przed dołączeniem do adresu URL. Umożliwia to tworzenie źródeł obejmujących wiele lokacji. Aby na przykład uwzględnić wszystkie zasoby w folderze masterpages dla wszystkich witryn jako źródło publiczne w CDN, wpisz następujące polecenie:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Modyfikator symboli wieloznacznych ***/** może być używany tylko na początku ścieżki i będzie zgodny ze wszystkimi segmentami adresów URL pod określonym adresem URL.
+ Ścieżka może wskazywać bibliotekę dokumentów, folder lub witrynę. Na przykład ścieżka _*/site1_ będzie zgodna ze wszystkimi bibliotekami dokumentów w witrynie.

Możesz dodać źródło z określoną ścieżką względną. Nie można dodać źródła przy użyciu pełnej ścieżki.

W tym przykładzie dodano prywatne źródło biblioteki siteassets w określonej witrynie:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

W tym przykładzie dodano prywatne źródło folderu _folder1_ w bibliotece zasobów witryny zbioru witryn:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Jeśli w ścieżce znajduje się miejsce, możesz otoczyć ścieżkę podwójnym cudzysłowem lub zamienić miejsce na kodowanie adresu URL %20. W poniższych przykładach dodano prywatne źródło _folderu folderu 1_ w bibliotece zasobów witryny zbioru witryn:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> W przypadku źródeł prywatnych zasoby udostępniane ze źródła muszą mieć opublikowaną wersję główną, zanim będzie można uzyskać do nich dostęp z CDN.

Po uruchomieniu polecenia system synchronizuje konfigurację w centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Przykład: Skonfiguruj publiczne źródło dla stron wzorcowych i biblioteki stylów dla usługi SharePoint Online

Zwykle te źródła są domyślnie skonfigurowane po włączeniu Office 365 CDN. Jeśli jednak chcesz włączyć je ręcznie, wykonaj następujące kroki.

+ Użyj polecenia cmdlet **Add-SPOTenantCdnOrigin** , aby zdefiniować bibliotekę stylów jako źródło publiczne.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Użyj polecenia cmdlet **Add-SPOTenantCdnOrigin** , aby zdefiniować strony wzorcowe jako źródło publiczne.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Po uruchomieniu polecenia system synchronizuje konfigurację w centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Przykład: konfigurowanie prywatnego źródła zasobów witryny, stron witryny i publikowania obrazów dla usługi SharePoint Online

+ Użyj polecenia cmdlet **Add-SPOTenantCdnOrigin** , aby zdefiniować folder zasobów witryny jako źródło prywatne.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Użyj polecenia cmdlet **Add-SPOTenantCdnOrigin** , aby zdefiniować folder stron witryny jako źródło prywatne.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Użyj polecenia cmdlet **Add-SPOTenantCdnOrigin** , aby zdefiniować folder publikowania obrazów jako źródło prywatne.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Po uruchomieniu polecenia system synchronizuje konfigurację w centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Przykład: Konfigurowanie prywatnego źródła dla zbioru witryn dla usługi SharePoint Online

Użyj polecenia cmdlet **Add-SPOTenantCdnOrigin** , aby zdefiniować zbiór witryn jako źródło prywatne. Przykład:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Po uruchomieniu polecenia system synchronizuje konfigurację w centrum danych. Może zostać wyświetlony komunikat _Oczekiwanie na konfigurację_, który jest oczekiwany, gdy dzierżawa usługi SharePoint Online nawiązuje połączenie z usługą CDN. Może to potrwać do 15 minut.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Zarządzanie Office 365 CDN

Po skonfigurowaniu CDN możesz wprowadzić zmiany w konfiguracji podczas aktualizowania zawartości lub zmiany potrzeb zgodnie z opisem w tej sekcji.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Dodawanie, aktualizowanie lub usuwanie zasobów z Office 365 CDN

Po wykonaniu kroków konfiguracji można dodawać nowe zasoby oraz aktualizować lub usuwać istniejące zasoby w dowolnym momencie. Wystarczy wprowadzić zmiany w zasobach w folderze lub bibliotece SharePoint, która została zidentyfikowana jako źródło. Jeśli dodasz nowy zasób, będzie on natychmiast dostępny za pośrednictwem CDN. Jeśli jednak zaktualizujesz zasób, propagowanie nowej kopii i udostępnienie jej w CDN potrwa do 15 minut.

Jeśli musisz pobrać lokalizację źródła, możesz użyć polecenia cmdlet **Get-SPOTenantCdnOrigins** . Aby uzyskać informacje na temat korzystania z tego polecenia cmdlet, zobacz [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Usuwanie źródła z Office 365 CDN

Możesz usunąć dostęp do folderu lub biblioteki SharePoint, która została zidentyfikowana jako źródło. W tym celu użyj polecenia cmdlet **Remove-SPOTenantCdnOrigin** .

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Aby uzyskać informacje na temat korzystania z tego polecenia cmdlet, zobacz [Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modyfikowanie źródła w Office 365 CDN

Nie można zmodyfikować utworzonego źródła. Zamiast tego usuń źródło, a następnie dodaj nowe. Aby uzyskać więcej informacji, zobacz [Aby usunąć źródło z Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) i [Aby dodać źródło dla zasobów](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Wyłącz Office 365 CDN

Użyj polecenia cmdlet **Set-SPOTenantCdnEnabled**, aby wyłączyć CDN dla organizacji. Jeśli dla CDN włączono zarówno publiczne, jak i prywatne źródła, należy uruchomić polecenie cmdlet dwa razy, jak pokazano w poniższych przykładach.

Aby wyłączyć używanie źródeł publicznych w CDN, wprowadź następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Aby wyłączyć używanie źródeł prywatnych w CDN, wprowadź następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet, zobacz [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>Konfigurowanie i konfigurowanie Office 365 CDN przy użyciu programu PowerShell PnP

Procedury opisane w tej sekcji wymagają użycia programu PowerShell PnP w celu nawiązania połączenia z usługą SharePoint Online. Aby uzyskać instrukcje, zobacz [Wprowadzenie do programu PowerShell PnP](https://github.com/SharePoint/PnP-PowerShell#getting-started).

Wykonaj te kroki, aby skonfigurować i skonfigurować CDN do hostowania zasobów w usłudze SharePoint Online przy użyciu programu PowerShell PnP.

<details>
  <summary>Kliknij, aby rozwinąć</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Umożliwianie organizacji korzystania z Office 365 CDN

Przed wprowadzeniem zmian w ustawieniach CDN dzierżawy należy pobrać bieżący stan konfiguracji CDN prywatnej w dzierżawie Office 365. Połączenie do dzierżawy przy użyciu programu PowerShell PnP:

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

Teraz użyj polecenia cmdlet **Get-PnPTenantCdnEnabled**, aby pobrać ustawienia stanu CDN z dzierżawy:

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

Stan CDN dla określonego typu CdnType zostanie wyświetlony na ekranie.

Użyj polecenia cmdlet **Set-PnPTenantCdnEnabled**, aby umożliwić organizacji korzystanie z Office 365 CDN. Możesz zezwolić swojej organizacji na używanie źródeł publicznych, źródeł prywatnych lub obu tych źródeł w tym samym czasie. Można również skonfigurować CDN, aby pominąć konfigurację domyślnych źródeł po jej włączeniu. Zawsze można dodać te źródła później, zgodnie z opisem w tym temacie.

W programie PowerShell PnP:

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Aby na przykład umożliwić organizacji używanie źródeł publicznych i prywatnych, wpisz następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

Aby umożliwić organizacji używanie źródeł publicznych i prywatnych, ale pomijanie konfigurowania domyślnych źródeł, wpisz następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Zobacz [Domyślne źródła CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins), aby uzyskać informacje o źródłach aprowizowanych domyślnie po włączeniu Office 365 CDN oraz potencjalnym wpływie pominięcia konfiguracji domyślnych źródeł.

Aby umożliwić organizacji korzystanie z źródeł publicznych, wpisz następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

Aby umożliwić organizacji korzystanie z prywatnych źródeł, wpisz następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet, zobacz [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Zmień listę typów plików do uwzględnienia w Office 365 CDN (opcjonalnie)

> [!TIP]
> Podczas definiowania typów plików przy użyciu polecenia cmdlet **Set-PnPTenantCdnPolicy** należy zastąpić aktualnie zdefiniowaną listę. Jeśli chcesz dodać dodatkowe typy plików do listy, najpierw użyj polecenia cmdlet, aby dowiedzieć się, jakie typy plików są już dozwolone i uwzględnić je na liście wraz z nowymi.

Użyj polecenia cmdlet **Set-PnPTenantCdnPolicy**, aby zdefiniować statyczne typy plików, które mogą być hostowane przez źródła publiczne i prywatne w CDN. Domyślnie dozwolone są typowe typy zasobów, na przykład css, .gif, .jpg i .js.

W programie PowerShell PnP:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Aby na przykład umożliwić CDN hostowanie plików css i .png, należy wprowadzić polecenie:

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Aby zobaczyć, jakie typy plików są obecnie dozwolone przez CDN, użyj polecenia cmdlet **Get-PnPTenantCdnPolicies**:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Aby uzyskać więcej informacji na temat tych poleceń cmdlet, zobacz [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) i [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Zmień listę klasyfikacji lokacji, które chcesz wykluczyć z Office 365 CDN (opcjonalnie)

> [!TIP]
> Po wykluczeniu klasyfikacji lokacji przy użyciu polecenia cmdlet **Set-PnPTenantCdnPolicy** zastąpisz aktualnie zdefiniowaną listę. Jeśli chcesz wykluczyć dodatkowe klasyfikacje lokacji, najpierw użyj polecenia cmdlet, aby dowiedzieć się, jakie klasyfikacje są już wykluczone, a następnie dodać je wraz z nowymi.

Użyj polecenia cmdlet **Set-PnPTenantCdnPolicy**, aby wykluczyć klasyfikacje lokacji, których nie chcesz udostępniać za pośrednictwem CDN. Domyślnie klasyfikacje witryn nie są wykluczone.

W programie PowerShell PnP:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

Aby zobaczyć, jakie klasyfikacje witryn są obecnie ograniczone, użyj polecenia cmdlet **Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Właściwości, które zostaną zwrócone, to _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ i _ExcludeIfNoScriptDisabled_.

_Właściwość IncludeFileExtensions_ zawiera listę rozszerzeń plików, które będą obsługiwane z CDN.

> [!NOTE]
> Domyślne rozszerzenia plików różnią się między publicznymi i prywatnymi.

_Właściwość ExcludeRestrictedSiteClassifications_ zawiera klasyfikacje lokacji, które chcesz wykluczyć z CDN. Można na przykład wykluczyć witryny oznaczone jako **Poufne**, aby zawartość z witryn z zastosowaną klasyfikacją nie była obsługiwana z CDN.

_Właściwość ExcludeIfNoScriptDisabled_ wyklucza zawartość z CDN na podstawie ustawień atrybutu _NoScript_ na poziomie lokacji. Domyślnie atrybut _NoScript_ jest ustawiony na **wartość Włączone** dla _nowoczesnych_ witryn i **Wyłączone** dla lokacji _klasycznych_ . Zależy to od ustawień dzierżawy.

Aby uzyskać więcej informacji na temat tych poleceń cmdlet, zobacz [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) i [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Dodawanie źródła dla zasobów

Użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** , aby zdefiniować źródło. Można zdefiniować wiele źródeł. Źródło to adres URL wskazujący bibliotekę SharePoint lub folder zawierający zasoby, które mają być hostowane przez CDN.

> [!IMPORTANT]
> Nigdy nie należy umieszczać zasobów, które zawierają informacje o użytkowniku lub są uważane za wrażliwe dla organizacji w publicznym pochodzeniu.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Wartość _ścieżki_ to ścieżka względna do biblioteki lub folderu zawierającego zasoby. Oprócz ścieżek względnych można używać symboli wieloznacznych. Źródła obsługują symbole wieloznaczne przed dołączeniem do adresu URL. Umożliwia to tworzenie źródeł obejmujących wiele lokacji. Aby na przykład uwzględnić wszystkie zasoby w folderze masterpages dla wszystkich witryn jako źródło publiczne w CDN, wpisz następujące polecenie:

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Modyfikator symboli wieloznacznych ***/** może być używany tylko na początku ścieżki i będzie zgodny ze wszystkimi segmentami adresów URL pod określonym adresem URL.
+ Ścieżka może wskazywać bibliotekę dokumentów, folder lub witrynę. Na przykład ścieżka _*/site1_ będzie zgodna ze wszystkimi bibliotekami dokumentów w witrynie.

Możesz dodać źródło z określoną ścieżką względną. Nie można dodać źródła przy użyciu pełnej ścieżki.

W tym przykładzie dodano prywatne źródło biblioteki zasobów witryny w określonej witrynie:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

W tym przykładzie dodano prywatne źródło folderu _folder1_ w bibliotece zasobów witryny zbioru witryn:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Jeśli w ścieżce znajduje się miejsce, możesz otoczyć ścieżkę podwójnym cudzysłowem lub zamienić miejsce na kodowanie adresu URL %20. W poniższych przykładach dodano prywatne źródło _folderu folderu 1_ w bibliotece zasobów witryny zbioru witryn:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

> [!NOTE]
> W przypadku źródeł prywatnych zasoby udostępniane ze źródła muszą mieć opublikowaną wersję główną, zanim będzie można uzyskać do nich dostęp z CDN.

Po uruchomieniu polecenia system synchronizuje konfigurację w centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Przykład: Skonfiguruj publiczne źródło dla stron wzorcowych i biblioteki stylów dla usługi SharePoint Online

Zwykle te źródła są domyślnie skonfigurowane po włączeniu Office 365 CDN. Jeśli jednak chcesz włączyć je ręcznie, wykonaj następujące kroki.

+ Użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** , aby zdefiniować bibliotekę stylów jako źródło publiczne.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** , aby zdefiniować strony wzorcowe jako źródło publiczne.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Po uruchomieniu polecenia system synchronizuje konfigurację w centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Przykład: konfigurowanie prywatnego źródła zasobów witryny, stron witryny i publikowania obrazów dla usługi SharePoint Online

+ Użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** , aby zdefiniować folder zasobów witryny jako źródło prywatne.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** , aby zdefiniować folder stron witryny jako źródło prywatne.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** , aby zdefiniować folder publikowania obrazów jako źródło prywatne.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Po uruchomieniu polecenia system synchronizuje konfigurację w centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Przykład: Konfigurowanie prywatnego źródła dla zbioru witryn dla usługi SharePoint Online

Użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** , aby zdefiniować zbiór witryn jako źródło prywatne. Przykład:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Po uruchomieniu polecenia system synchronizuje konfigurację w centrum danych. Może zostać wyświetlony komunikat _Oczekiwanie na konfigurację_, który jest oczekiwany, gdy dzierżawa usługi SharePoint Online nawiązuje połączenie z usługą CDN. Może to potrwać do 15 minut.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>Zarządzanie Office 365 CDN

Po skonfigurowaniu CDN możesz wprowadzić zmiany w konfiguracji podczas aktualizowania zawartości lub zmiany potrzeb zgodnie z opisem w tej sekcji.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Dodawanie, aktualizowanie lub usuwanie zasobów z Office 365 CDN

Po wykonaniu kroków konfiguracji można dodawać nowe zasoby oraz aktualizować lub usuwać istniejące zasoby w dowolnym momencie. Wystarczy wprowadzić zmiany w zasobach w folderze lub bibliotece SharePoint, która została zidentyfikowana jako źródło. Jeśli dodasz nowy zasób, będzie on natychmiast dostępny za pośrednictwem CDN. Jeśli jednak zaktualizujesz zasób, propagowanie nowej kopii i udostępnienie jej w CDN potrwa do 15 minut.

Jeśli musisz pobrać lokalizację źródła, możesz użyć polecenia cmdlet **Get-PnPTenantCdnOrigin** . Aby uzyskać informacje na temat korzystania z tego polecenia cmdlet, zobacz [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Usuwanie źródła z Office 365 CDN

Możesz usunąć dostęp do folderu lub biblioteki SharePoint, która została zidentyfikowana jako źródło. W tym celu użyj polecenia cmdlet **Remove-PnPTenantCdnOrigin** .

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Aby uzyskać informacje na temat korzystania z tego polecenia cmdlet, zobacz [Remove-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modyfikowanie źródła w Office 365 CDN

Nie można zmodyfikować utworzonego źródła. Zamiast tego usuń źródło, a następnie dodaj nowe. Aby uzyskać więcej informacji, zobacz [Aby usunąć źródło z Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) i [Aby dodać źródło dla zasobów](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Wyłącz Office 365 CDN

Użyj polecenia cmdlet **Set-PnPTenantCdnEnabled**, aby wyłączyć CDN dla organizacji. Jeśli dla CDN włączono zarówno publiczne, jak i prywatne źródła, należy uruchomić polecenie cmdlet dwa razy, jak pokazano w poniższych przykładach.

Aby wyłączyć używanie źródeł publicznych w CDN, wprowadź następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

Aby wyłączyć używanie źródeł prywatnych w CDN, wprowadź następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet, zobacz [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-cli-for-microsoft-365"></a>Konfigurowanie i konfigurowanie Office 365 CDN przy użyciu interfejsu wiersza polecenia dla Microsoft 365

Procedury opisane w tej sekcji wymagają zainstalowania [interfejsu wiersza polecenia dla Microsoft 365](https://aka.ms/cli-m365). Następnie połącz się z dzierżawą Office 365 przy użyciu polecenia [logowania](https://pnp.github.io/cli-microsoft365/cmd/login/).

Wykonaj te kroki, aby skonfigurować i skonfigurować CDN do hostowania zasobów w usłudze SharePoint Online przy użyciu interfejsu wiersza polecenia dla Microsoft 365.

<details>
  <summary>Kliknij, aby rozwinąć</summary>

### <a name="enable-the-office-365-cdn"></a>Włączanie Office 365 CDN

Stanem Office 365 CDN w dzierżawie można zarządzać za pomocą polecenia [spo cdn set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-set/).

Aby włączyć Office 365 publiczne CDN w dzierżawie, wykonaj następujące czynności:

```cli
spo cdn set --type Public --enabled true
```

Aby włączyć Office 365 SharePoint CDN, wykonaj następujące czynności:

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Wyświetlanie bieżącego stanu Office 365 CDN

Aby sprawdzić, czy określony typ Office 365 CDN jest włączony lub wyłączony, użyj polecenia [spo cdn get](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-get/).

Aby sprawdzić, czy Office 365 publiczna CDN jest włączona, wykonaj następujące czynności:

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Wyświetlanie źródeł Office 365 CDN

Aby wyświetlić aktualnie skonfigurowane źródła Office 365 publiczne CDN, wykonaj następujące czynności:

```cli
spo cdn origin list --type Public
```

Zobacz [Domyślne źródła CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins), aby uzyskać informacje o źródłach, które są domyślnie aprowizowane po włączeniu Office 365 CDN.

### <a name="add-an-office-365-cdn-origin"></a>Dodawanie źródła Office 365 CDN

> [!IMPORTANT]
> Nigdy nie należy umieszczać zasobów, które są uważane za wrażliwe dla organizacji, w bibliotece dokumentów SharePoint skonfigurowanej jako źródło publiczne.

Użyj polecenia [spo cdn origin add](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-add/), aby zdefiniować źródło CDN. Można zdefiniować wiele źródeł. Źródło to adres URL wskazujący bibliotekę SharePoint lub folder zawierający zasoby, które mają być hostowane przez CDN.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

Gdzie `path` jest ścieżka względna do folderu zawierającego zasoby. Oprócz ścieżek względnych można używać symboli wieloznacznych.

Aby uwzględnić wszystkie zasoby w **galerii stron wzorcowych** wszystkich witryn jako źródło publiczne, wykonaj następujące czynności:

```cli
spo cdn origin add --type Public --origin */masterpage
```

Aby skonfigurować prywatne źródło dla określonego zbioru witryn, wykonaj następujące czynności:

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Po dodaniu źródła CDN pobieranie plików za pośrednictwem usługi CDN może potrwać do 15 minut. Możesz sprawdzić, czy konkretne źródło zostało już włączone przy użyciu polecenia [spo cdn origin list](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) .

### <a name="remove-an-office-365-cdn-origin"></a>Usuwanie źródła Office 365 CDN

Użyj polecenia [spo cdn origin remove](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-remove/), aby usunąć źródło CDN dla określonego typu CDN.

Aby usunąć źródło publiczne z konfiguracji CDN, wykonaj następujące czynności:

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> Usunięcie źródła CDN nie ma wpływu na pliki przechowywane w żadnej bibliotece dokumentów pasującej do tego źródła. Jeśli te zasoby zostały przywoływane przy użyciu adresu URL SharePoint, SharePoint automatycznie przełączy się z powrotem do oryginalnego adresu URL wskazującego bibliotekę dokumentów. Jeśli jednak odwołano się do zasobów przy użyciu publicznego adresu URL CDN, usunięcie źródła spowoduje przerwanie linku i konieczne będzie ich ręczne zmianę.

### <a name="modify-an-office-365-cdn-origin"></a>Modyfikowanie źródła Office 365 CDN

Nie można zmodyfikować istniejącego źródła CDN. Zamiast tego należy usunąć wcześniej zdefiniowane źródło CDN przy użyciu `spo cdn origin remove` polecenia i dodać nowe przy użyciu `spo cdn origin add` polecenia .

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Zmienianie typów plików do uwzględnienia w Office 365 CDN

Domyślnie w CDN znajdują się następujące typy plików: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff i .woff2_. Jeśli musisz uwzględnić dodatkowe typy plików w CDN, możesz zmienić konfigurację CDN za pomocą polecenia [spo cdn policy set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/).

> [!NOTE]
> Podczas zmieniania listy typów plików należy zastąpić aktualnie zdefiniowaną listę. Jeśli chcesz uwzględnić dodatkowe typy plików, najpierw użyj polecenia [spo cdn policy list](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) , aby dowiedzieć się, które typy plików są obecnie skonfigurowane.

Aby dodać typ pliku _JSON_ do domyślnej listy typów plików zawartych w publicznym CDN, wykonaj następujące czynności:

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Zmień listę klasyfikacji lokacji, które chcesz wykluczyć z Office 365 CDN

Użyj polecenia [spo cdn policy set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/), aby wykluczyć klasyfikacje lokacji, których nie chcesz udostępniać za pośrednictwem CDN. Domyślnie klasyfikacje witryn nie są wykluczone.

> [!NOTE]
> Podczas zmieniania listy wykluczonych klasyfikacji lokacji należy zastąpić aktualnie zdefiniowaną listę. Jeśli chcesz wykluczyć dodatkowe klasyfikacje, najpierw użyj polecenia [spo cdn policy list](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-list/) , aby dowiedzieć się, które klasyfikacje są obecnie skonfigurowane.

Aby wykluczyć lokacje sklasyfikowane jako _HBI_ z publicznej CDN, wykonaj

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Wyłącz Office 365 CDN

Aby wyłączyć Office 365 CDN, użyj `spo cdn set` polecenia, na przykład:

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>Korzystanie z zasobów CDN

Po włączeniu CDN i skonfigurowanych źródeł i zasad możesz rozpocząć korzystanie z zasobów CDN.

Ta sekcja pomoże Ci zrozumieć, jak używać adresów URL CDN na stronach SharePoint i zawartości, dzięki czemu SharePoint przekierowuje żądania dotyczące zasobów zarówno w źródłach publicznych, jak i prywatnych do CDN.

+ [Aktualizowanie linków do zasobów CDN](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Używanie zasobów w źródłach publicznych](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Używanie zasobów w źródłach prywatnych](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

Aby uzyskać informacje na temat używania CDN do hostowania składników Web Part po stronie klienta, zobacz temat [Hostowanie składnika Web Part po stronie klienta z Office 365 CDN (Hello world część 4)](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).

> [!NOTE]
> Jeśli dodasz folder _ClientSideAssets_ do listy źródeł **CDN prywatnej**, nie można renderować niestandardowych składników Web Part hostowanych CDN. Pliki używane przez składniki Web Part SPFX mogą korzystać tylko z publicznych CDN, a folder ClientSideAssets jest domyślnym źródłem dla CDN publicznych.

### <a name="updating-links-to-cdn-assets"></a>Aktualizowanie linków do zasobów CDN

Aby użyć zasobów dodanych do źródła, wystarczy zaktualizować linki do oryginalnego pliku ze ścieżką do pliku w danej oknie źródłowym.

+ Edytuj stronę lub zawartość zawierającą linki do zasobów dodanych do źródła. Możesz również użyć jednej z kilku metod do globalnego wyszukiwania i zastępowania linków w witrynie lub zbiorze witryn, jeśli chcesz zaktualizować link do danego zasobu wszędzie tam, gdzie jest wyświetlany.
+ Dla każdego linku do elementu zawartości w oknie źródłowym zastąp ścieżkę ścieżką do pliku w CDN pochodzenia. Można użyć ścieżek względnych.
+ Zapisz stronę lub zawartość.

Rozważmy na przykład obraz _/site/SiteAssets/images/image.png_, który został skopiowany do folderu biblioteki dokumentów _/site/CDN_origins/public/_. Aby użyć zasobu CDN, zastąp oryginalną ścieżkę do lokalizacji pliku obrazu ścieżką do źródła, aby utworzyć nowy adres URL _/site/CDN_origins/public/image.png_.

Jeśli chcesz użyć pełnego adresu URL zasobu zamiast ścieżki względnej, skonstruuj łącze w następujący sposób:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> Ogólnie rzecz biorąc, nie należy kodować adresów URL bezpośrednio do zasobów w CDN. W razie potrzeby można jednak ręcznie utworzyć adresy URL dla zasobów w źródłach publicznych. Aby uzyskać więcej informacji, zobacz [Hardcoding CDN URL for public assets (Kodowanie CDN adresów URL dla zasobów publicznych](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets)).

Aby dowiedzieć się, jak sprawdzić, czy zasoby są obsługiwane z CDN, zobacz [Jak mogę potwierdzić, że zasoby są obsługiwane przez CDN?](use-microsoft-365-cdn-with-spo.md#CDNConfirm) w [temacie Rozwiązywanie problemów z Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting).

### <a name="using-assets-in-public-origins"></a>Używanie zasobów w źródłach publicznych

**Funkcja publikowania** w usłudze SharePoint Online automatycznie ponownie zapisuje adresy URL zasobów przechowywanych w źródłach publicznych do ich odpowiedników CDN, tak aby zasoby były obsługiwane z usługi CDN zamiast SharePoint.

Jeśli źródło znajduje się w witrynie z włączoną funkcją publikowania, a zasoby, które chcesz odciążyć do CDN, należą do jednej z następujących kategorii, SharePoint automatycznie ponownie zapisze adresy URL dla zasobów w miejscu pochodzenia, pod warunkiem że zasób nie został wykluczony przez zasady CDN.

Poniżej przedstawiono omówienie, które linki są automatycznie ponownie zapisywane przez funkcję publikowania SharePoint:

+ Adresy URL IMG/LINK/CSS w odpowiedziach HTML klasycznej strony publikowania
  + Obejmuje to obrazy dodane przez autorów w zawartości HTML strony
+ Adresy URL obrazów składnika Web Part w bibliotece obrazów
+ Wyniki pól obrazów w interfejsie API REST listy SPList (RenderListDataAsStream)
  + Użyj nowej właściwości _ImageFieldsToTryRewriteToCdnUrls_ , aby podać rozdzielaną przecinkami listę pól
  + Obsługuje pola hiperłącza i pola PublishingImage
+ SharePoint odwzorowania obrazów

Na poniższym diagramie przedstawiono przepływ pracy, gdy SharePoint odbiera żądanie strony zawierającej zasoby z publicznego źródła.

![Diagram przepływu pracy: pobieranie zasobów Office 365 CDN z publicznego źródła.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "Przepływ pracy: pobieranie zasobów Office 365 CDN z publicznego źródła")

> [!TIP]
> Jeśli chcesz wyłączyć automatyczne ponowne zapisywanie określonych adresów URL na stronie, możesz wyewidencjonować stronę i dodać parametr ciągu zapytania **? NoAutoReWrites=true** na końcu każdego linku, który chcesz wyłączyć.

#### <a name="constructing-cdn-urls-for-public-assets"></a>Konstruowanie adresów URL CDN dla zasobów publicznych

Jeśli funkcja _publikowania_ nie jest włączona dla źródła publicznego lub zasób nie jest jednym z typów łączy obsługiwanych przez funkcję automatycznego ponownego zapisywania usługi CDN, możesz ręcznie utworzyć adresy URL do CDN lokalizacji zasobów i użyć tych adresów URL w zawartości.

> [!NOTE]
> Nie można zakodować ani utworzyć CDN adresów URL do zasobów w prywatnym pochodzeniu, ponieważ wymagany token dostępu, który tworzy ostatnią sekcję adresu URL, jest generowany w momencie żądania zasobu. Możesz utworzyć adres URL dla CDN publicznego, a adres URL nie powinien być zakodowany na stałe, ponieważ może ulec zmianie.

W przypadku zasobów CDN publicznych format adresu URL będzie wyglądać następująco:

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

Zastąp ciąg **TenantHostName** nazwą dzierżawy. Przykład:

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> Właściwość kontekstu strony powinna służyć do konstruowania prefiksu zamiast twardego kodowania "https://publiccdn.sharepointonline.com". Adres URL może ulec zmianie i nie powinien być zakodowany na stałe. Jeśli używasz szablonów wyświetlania z klasycznym SharePoint Online, możesz użyć właściwości "window._spPageContextInfo.publicCdnBaseUrl" w szablonie wyświetlania dla prefiksu adresu URL. Jeśli SPFx składników Web Part dla nowoczesnych i klasycznych SharePoint możesz użyć właściwości "this.context.pageContext.legacyPageContext.publicCdnBaseUrl". Zapewni to prefiks, aby w przypadku zmiany implementacja została zaktualizowana wraz z nim. Jako przykład dla SPFx adres URL można utworzyć przy użyciu właściwości "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" + "/" + "host" + "/" + "relativeURL dla elementu". Zobacz Using CDN in Client-side code which is part of the season 1 performance series ([Korzystanie z CDN w kodzie po stronie klienta](https://youtu.be/IH1RbQlbhIA), który jest częścią [serii wydajności 1 sezonu](https://aka.ms/sppnp-perfvideos)


### <a name="using-assets-in-private-origins"></a>Używanie zasobów w źródłach prywatnych

Do używania zasobów w prywatnych źródłach nie jest wymagana żadna dodatkowa konfiguracja. SharePoint Online automatycznie ponownie zapisuje adresy URL dla zasobów w prywatnych źródłach, aby żądania dotyczące tych zasobów zawsze były obsługiwane z CDN. Nie można ręcznie tworzyć adresów URL w celu CDN zasobów w prywatnych źródłach, ponieważ te adresy URL zawierają tokeny, które muszą być automatycznie generowane przez usługę SharePoint Online w momencie żądania zasobu.

Dostęp do zasobów w źródłach prywatnych jest chroniony przez dynamicznie generowane tokeny na podstawie uprawnień użytkownika do źródła, z zastrzeżeniami opisanymi w poniższych sekcjach. Użytkownicy muszą mieć co najmniej dostęp do **odczytu** do źródeł, aby CDN do renderowania zawartości.

Na poniższym diagramie przedstawiono przepływ pracy, gdy SharePoint odbiera żądanie strony zawierającej zasoby z prywatnego źródła.

![Diagram przepływu pracy: pobieranie zasobów Office 365 CDN z prywatnego źródła.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "Przepływ pracy: pobieranie zasobów Office 365 CDN z prywatnego źródła")

#### <a name="token-based-authorization-in-private-origins"></a>Autoryzacja oparta na tokenach w źródłach prywatnych

Dostęp do zasobów w prywatnych źródłach w Office 365 CDN jest udzielany za pomocą tokenów generowanych przez usługę SharePoint Online. Użytkownicy, którzy mają już uprawnienia dostępu do folderu lub biblioteki wyznaczonej przez źródło, automatycznie otrzymują tokeny, które umożliwiają użytkownikowi dostęp do pliku na podstawie poziomu uprawnień. Te tokeny dostępu są ważne przez 30–90 minut po ich wygenerowaniu, aby zapobiec atakom powtarzania tokenów.

Po wygenerowaniu tokenu dostępu SharePoint Online zwraca klientowi niestandardowy identyfikator URI zawierający dwa parametry autoryzacji _eat_ (token autoryzacji brzegowej) i _owies_ (token autoryzacji pochodzenia). Struktura każdego tokenu to _czas wygaśnięcia< w formacie czasu epoki >__<'secure signature'>_. Przykład:

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Każda osoba posiadająca token może uzyskać dostęp do zasobu w CDN. Jednak adresy URL zawierające te tokeny dostępu są udostępniane tylko za pośrednictwem protokołu HTTPS, więc jeśli adres URL nie zostanie jawnie udostępniony przez użytkownika końcowego przed wygaśnięciem tokenu, zasób nie będzie dostępny dla nieautoryzowanych użytkowników.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Uprawnienia na poziomie elementu nie są obsługiwane dla zasobów w źródłach prywatnych

Należy pamiętać, że usługa SharePoint Online nie obsługuje uprawnień na poziomie elementu dla zasobów w prywatnych źródłach. Na przykład dla pliku znajdującego się w programie `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`użytkownicy mają skuteczny dostęp do pliku, biorąc pod uwagę następujące warunki:

|Użytkownik  |Uprawnienia  |Skuteczny dostęp  |
|---------|---------|---------|
|Użytkownik 1     |Ma dostęp do folderu1         |Dostęp do image1.jpg z CDN         |
|Użytkownik 2     |Nie ma dostępu do folderu1         |Nie można uzyskać dostępu do image1.jpg z CDN         |
|Użytkownik 3     |Nie ma dostępu do folderu folder1, ale otrzymuje jawne uprawnienie dostępu do image1.jpg w usłudze SharePoint Online         |Może uzyskiwać dostęp do image1.jpg zasobów bezpośrednio z usługi SharePoint Online, ale nie z CDN         |
|Użytkownik 4     |Ma dostęp do folderu folder1, ale jawnie odmówiono dostępu do image1.jpg w usłudze SharePoint Online         |Nie można uzyskać dostępu do zasobu z usługi SharePoint Online, ale może uzyskać dostęp do zasobu z CDN pomimo odmowy dostępu do pliku w usłudze SharePoint Online         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>Rozwiązywanie problemów z Office 365 CDN

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Jak mogę potwierdzić, że zasoby są obsługiwane przez CDN?

Po dodaniu linków do CDN zasobów do strony możesz potwierdzić, że zasób jest obsługiwany z CDN, przechodząc do strony, klikając prawym przyciskiem myszy obraz po jego renderowaniu i przeglądając adres URL obrazu.

Możesz również użyć narzędzi deweloperskich przeglądarki, aby wyświetlić adres URL każdego zasobu na stronie lub użyć narzędzia do śledzenia sieci innej firmy.

> [!NOTE]
> Jeśli używasz narzędzia sieciowego, takiego jak Fiddler, do testowania zasobów poza renderowaniem zasobu ze strony SharePoint, musisz ręcznie dodać nagłówek odwołania "Referer: `https://yourdomain.sharepoint.com`" do żądania GET, gdzie adres URL jest głównym adresem URL dzierżawy usługi SharePoint Online.

Nie można przetestować adresów URL CDN bezpośrednio w przeglądarce internetowej, ponieważ musisz mieć odwołanie pochodzące z usługi SharePoint Online. Jeśli jednak dodasz adres URL zasobu CDN do strony SharePoint, a następnie otworzysz stronę w przeglądarce, na stronie zostanie wyświetlony CDN zasób.

Aby uzyskać więcej informacji na temat korzystania z narzędzi deweloperskich w przeglądarce Microsoft Edge, zobacz [Microsoft Edge Developer Tools](/microsoft-edge/devtools-guide).

Aby obejrzeć krótki film wideo hostowany w [kanale youTube SharePoint Developer Patterns and Practices](https://aka.ms/sppnp-videos) demonstrujący, jak sprawdzić, czy CDN działa, zobacz [Weryfikowanie użycia CDN i zapewnianie optymalnej łączności sieciowej](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Dlaczego zasoby z nowego źródła są niedostępne?
Zasoby w nowych źródłach nie będą natychmiast dostępne do użycia, ponieważ propagacja rejestracji za pośrednictwem CDN i przekazania zasobów ze źródła do magazynu CDN. Czas wymagany do udostępnienia zasobów w CDN zależy od liczby zasobów i rozmiarów plików.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>Mój składnik Web Part po stronie klienta lub rozwiązanie SharePoint Framework nie działa

Po włączeniu Office 365 CDN dla źródeł publicznych usługa CDN automatycznie tworzy te domyślne źródła:

+ */MASTERPAGE
+ */BIBLIOTEKA STYLÓW
+ */CLIENTSIDEASSETS

Jeśli nie ma źródła */clientsideassets, SharePoint Framework rozwiązania nie powiedzie się i nie są generowane żadne ostrzeżenia ani komunikaty o błędach. Tego źródła może brakować, ponieważ CDN została włączona z parametrem _-NoDefaultOrigins_ ustawionym na **$true** lub dlatego, że źródło zostało ręcznie usunięte.

Możesz sprawdzić, które źródła są obecne za pomocą następującego polecenia programu PowerShell:

```powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

Możesz też sprawdzić za pomocą interfejsu wiersza polecenia Office 365:

```cli
spo cdn origin list
```

Aby dodać źródło w programie PowerShell:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Aby dodać źródło w interfejsie wiersza polecenia Office 365:

```cli
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Jakie moduły programu PowerShell i powłoki interfejsu wiersza polecenia są potrzebne do pracy z Office 365 CDN?

Możesz pracować z Office 365 CDN przy użyciu modułu programu PowerShell **SharePoint Online Management Shell** lub **interfejsu wiersza polecenia Office 365**.

+ [Wprowadzenie do powłoki zarządzania SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [Instalowanie interfejsu wiersza polecenia Office 365](https://pnp.github.io/cli-microsoft365/user-guide/installing-cli/)

## <a name="see-also"></a>Zobacz też

[Sieci dostarczania zawartości](./content-delivery-networks.md)

[Network planning and performance tuning for Office 365](./network-planning-and-performance.md)

[SharePoint Performance Series — seria Office 365 CDN wideo](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
