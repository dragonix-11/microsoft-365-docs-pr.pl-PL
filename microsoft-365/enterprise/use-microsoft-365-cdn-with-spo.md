---
title: Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak za pomocą Office 365 Content Delivery Network (CDN) przyspieszyć dostarczenie swoich zasobów SharePoint Online.
ms.openlocfilehash: ad4eb1df63e201e49ba0b4c56c9123a04e37c184
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005269"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online

Możesz używać wbudowanych zasobów statycznych (Office 365 Content Delivery Network CDN) w celu zapewnienia lepszej wydajności stron SharePoint Online. Ten Office 365 CDN zwiększa wydajność, buforowanie statycznych zasobów bliżej przeglądarek żądających ich, co pomaga przyspieszyć pobieranie i zmniejszyć opóźnienie. Ponadto ten Office 365 CDN korzysta z [protokołu HTTP/2 w](https://en.wikipedia.org/wiki/HTTP/2) celu ulepszonej kompresji i do wytykiania potoków HTTP. Usługa Office 365 CDN jest zawarta w ramach subskrypcji usługi SharePoint Online.

> [!NOTE]
> Ta Office 365 CDN jest dostępna tylko dla dzierżawców w **chmurze produkcyjnej** (na całym świecie). Dzierżawcy chmury rządów Stanów Zjednoczonych, Chin i Niemiec obecnie nie obsługują Office 365 CDN.

Ten Office 365 CDN składa się z wielu sieci CDN, które umożliwiają hostowanie statycznych zasobów w wielu lokalizacjach lub pochodzeniech i obsługują je z globalnych sieci o wysokiej szybkości. W zależności od rodzaju zawartości, którą chcesz hostować w Office 365 CDN, możesz dodać pochodzenie **publiczne, pochodzenie** prywatne lub oba te źródła. Zobacz [Wybieranie, czy poszczególne pochodzenie ma być](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) publiczne, czy prywatne, aby uzyskać więcej informacji na temat różnic między pochodzeniem publicznym i prywatnym.

![Office 365 CDN diagram koncepcyjny.](../media/O365-CDN/o365-cdn-flow-transparent.png "Office 365 CDN diagram koncepcyjny")

Jeśli wiesz już, jak działają sieci CDN, wystarczy wykonać kilka czynności, aby włączyć obsługę sieci Office 365 CDN dzierżawy. W tym temacie opisano, jak to zrobić. Przeczytaj ten temat, aby uzyskać informacje na temat rozpoczynania hostowania statycznych zasobów.

> [!TIP]
> Istnieją inne sieci CDN hostowane przez firmę Microsoft, których można używać razem z usługą Office 365 w wyspecjalizowanych scenariuszach użycia, ale nie są one omawiane w tym temacie, ponieważ znajdują się poza zakresem Office 365 CDN. Aby uzyskać więcej informacji, zobacz [Inne sieci CDN firmy Microsoft](content-delivery-networks.md#other-microsoft-cdns).

 **Wróć do [planowania sieci i dostosowywania wydajności w celu Office 365](./network-planning-and-performance.md).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>Omówienie pracy z Office 365 CDN w u SharePoint Online

Aby skonfigurować Office 365 CDN organizacji, wykonaj następujące podstawowe czynności:

+ [Planowanie wdrożenia Office 365 CDN](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [Określ statyczne zasoby, które chcesz hostować w CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [Określ miejsce przechowywania środków trwałych](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets). Ta lokalizacja może być witryną SharePoint, biblioteką lub folderem i jest nazywana _pochodzeniem_.
  + [Określ, czy każde pochodzenie ma być publiczne, czy prywatne](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Możesz dodać wiele pochodzenia zarówno typu publicznego, jak i prywatnego.

+ Konfigurowanie i konfigurowanie CDN przy użyciu programu PowerShell lub interfejsu SharePoint interfejsu SharePoint online

  + [Konfigurowanie i konfigurowanie CDN przy użyciu powłoki zarządzania SharePoint online](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [Konfigurowanie i konfigurowanie serwera CDN przy użyciu programu PowerShell dla programu PnP](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [Konfigurowanie i konfigurowanie CDN za pomocą interfejsu Office 365 cli](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  Po zakończeniu tego kroku będziesz mieć:

  + Włączono CDN dla organizacji.
  + Dodano swoje pochodzenie, identyfikując każde pochodzenie jako publiczne lub prywatne.

Po zakończeniu konfiguracji możesz zarządzać [Office 365 CDN czasu przez](use-microsoft-365-cdn-with-spo.md#CDNManage):

+ Dodawanie, aktualizowanie i usuwanie zasobów
+ Dodawanie i usuwanie pochodzenia
+ Konfigurowanie CDN zasad
+ W razie potrzeby wyłączenie CDN

Na koniec zobacz [Korzystanie z CDN,](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) aby dowiedzieć się więcej o uzyskiwaniu dostępu do swoich CDN majątkowych zarówno z pochodzenia publicznego, jak i prywatnego.

Zobacz [Rozwiązywanie problemów z Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting), aby uzyskać wskazówki dotyczące rozwiązywania typowych problemów.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Planowanie wdrożenia Office 365 CDN

Przed wdrożeniem dzierżawy Office 365 CDN dzierżawy Office 365, w ramach procesu planowania należy wziąć pod uwagę następujące czynniki.

  + [Określanie statycznych zasobów, które mają być hostowanie w CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [Określanie miejsca przechowywania środków trwałych](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [Określ, czy każde pochodzenie ma być publiczne, czy prywatne](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Określanie statycznych zasobów, które mają być hostowanie w CDN

Ogólnie sieci CDN są najbardziej efektywne w _przypadku hostowania_ środków trwałych statycznych lub środków trwałych, które nie zmieniają się zbyt często. Dobrą regułą jest zidentyfikowanie plików spełniających niektóre lub wszystkie z tych warunków:

+ Pliki statyczne osadzone na stronie (na przykład skrypty i obrazy), które mogą mieć znaczący wpływ na czas ładowania strony
+ Duże pliki, takie jak pliki wykonywalne i pliki instalacyjne
+ Biblioteki zasobów, które obsługują kod po stronie klienta

Na przykład niewielkie pliki, o które wielokrotnie proszono, takie jak obrazy i skrypty witryny, mogą znacznie zwiększyć wydajność renderowania witryny i stopniowo zmniejszać obciążenie witryn SharePoint Online po dodaniu ich do CDN źródła. Większe pliki, takie jak pliki wykonywalne instalacji, można pobrać z witryny CDN w celu zapewnienia dodatniego wpływu na wydajność i późniejszego zmniejszenia obciążenia witryny usługi SharePoint Online, nawet jeśli nie są one dostępne tak często.

Poprawa wydajności w zależności od jednego pliku zależy od wielu czynników, takich jak odległość klienta od najbliższego punktu końcowego CDN, warunki przejściowy w sieci lokalnej i tak dalej. Wiele plików statycznych jest dosyć małych i można je pobrać Office 365 w krótszym niż sekundę. Jednak strona internetowa może zawierać wiele plików osadzonych o skumulowanym czasie pobierania kilku sekund. Wiele z tych plików w CDN znacznie skrócić czas ładowania strony. Na [przykład zobacz Jaki wzrost wydajności CDN?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Określanie miejsca przechowywania środków trwałych

Ta CDN pobiera zasoby z lokalizacji nazywanej _pochodzeniem_. Pochodzeniem może być witryna SharePoint, biblioteka dokumentów lub folder z ułatwieniami dostępu za pomocą adresu URL. Określenie pochodzenia w organizacji jest bardzo elastyczne. Możesz na przykład określić wiele pochodzenia lub jedno pochodzenie, w którym chcesz umieścić wszystkie swoje CDN majątek. Możesz wybrać pochodzenie publiczne lub prywatne swojej organizacji. Większość organizacji zdecyduje się wdrożyć połączenie tych dwóch opcji.

Możesz utworzyć nowy kontener dla swoich miejsc pochodzenia, takich jak foldery lub biblioteki dokumentów, i dodawać pliki, które chcesz udostępnić z CDN. Jest CDN dobre rozwiązanie, jeśli masz określony zestaw zasobów, które mają być dostępne w skoroszycie firmy CDN, i chcesz ograniczyć zestaw środków trwałych do tylko tych plików w kontenerze.

Możesz również skonfigurować istniejący zbiór witryn, witrynę, bibliotekę lub folder jako pochodzenie, co spowoduje, że wszystkie kwalifikujące się zasoby w kontenerze będą dostępne z CDN. Zanim dodasz istniejący kontener jako pochodzenie, upewnij się, że wiesz o jego zawartości i uprawnieniach, aby nie ujawniać przypadkowo zasobów anonimowym lub nieautoryzowanym użytkownikom.

Możesz _definiować CDN zasad wykluczania_ zawartości z Twoich pochodzenia z CDN. CDN zasad wykluczają zasoby z pochodzenia publicznego lub prywatnego przez _atrybuty, takie_ jak  typ pliku i klasyfikacja witryny, i są stosowane do wszystkich pochodzenia typu CdnType (prywatnego lub publicznego) określone w zasadach. Jeśli na przykład dodasz pochodzenie prywatne składające się z witryny zawierającej wiele podwitryn, możesz zdefiniować zasady wykluczania witryn oznaczonych jako poufne, tak  aby zawartość z witryn, do których zastosowano klasyfikację, nie była doręczowana CDN. Zasady będą stosowane do zawartości ze _wszystkich pochodzenia_ prywatnego dodanych do CDN.

Pamiętaj, że im większa liczba pochodzenia, tym większy wpływ na czas przetwarzania żądań przez usługę CDN usługi. Zalecamy jak najwięcej ograniczeń pochodzenia.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Określ, czy każde pochodzenie ma być publiczne, czy prywatne

Identyfikując pochodzenie, określasz, czy ma ono zostać określone jako _publiczne_ , czy _prywatne_. Dostęp do CDN majątek publicznych jest anonimowy, CDN zawartości z pochodzenia prywatnego jest zabezpieczona dynamicznie generowanymi tokenami w celu zwiększenia zabezpieczeń. Bez względu na to, którą opcję wybierzesz, firma Microsoft musi zrobić wszystko, co wytęża, jeśli chodzi o administrowanie samym CDN siecią. Możesz również zmienić zdanie później, po skonfigurowaniu źródła CDN i zidentyfikowaniu swojego pochodzenia.

Zarówno opcje publiczne, jak i prywatne zapewniają podobny wzrost wydajności, ale każda z nich ma unikatowe atrybuty i zalety.

**Pochodzenie** publiczne w obrębie Office 365 CDN są dostępne anonimowo, a hostowane zasoby mogą uzyskać dostęp dla wszystkich osób, które mają adres URL tego zasobu. Ponieważ dostęp do zawartości w pochodzenia publicznego jest anonimowy, należy ich używać tylko do buforowania nie poufnych treści ogólnych, takich jak pliki JavaScript, skrypty, ikony i obrazy.

**Pochodzenie** prywatne w obrębie Office 365 CDN prywatnego dostępu do zawartości użytkownika, takiej jak biblioteki SharePoint dokumentów online, witryny i własne obrazy. Dostęp do zawartości w pochodzenie prywatnej jest zabezpieczony dynamicznie generowanymi tokenami, więc dostęp do niej mogą uzyskiwać tylko użytkownicy z uprawnieniami do oryginalnej biblioteki dokumentów lub lokalizacji przechowywania. Pochodzenie prywatne w sieci Office 365 CDN może być używane tylko w przypadku zawartości online usługi SharePoint, a dostęp do zasobów w pochodzenie prywatne można uzyskać tylko za pośrednictwem przekierowania z dzierżawy usługi SharePoint Online.

Aby uzyskać więcej informacji na temat sposobu CDN do zasobów pochodzenia prywatnego, zobacz Używanie środków trwałych [w pochodzeniu prywatnym](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Atrybuty i zalety hostowania zasobów publicznie publicznie

+ Zasoby ujawnione w publicznym pochodzenia są dostępne dla wszystkich anonimowo.
    > [!IMPORTANT]
    > Nigdy nie należy umieszczać zasobów zawierających informacje o użytkownikach lub uznawanych za poufne dla organizacji w przypadku pochodzenia publicznego.

+ Po usunięciu środka trwałego z pochodzenia publicznego może on być nadal dostępny w pamięci podręcznej przez maksymalnie 30 dni. jednak w ciągu 15 minut unieważnimy linki do zasobu w CDN.

+ Gdy hostuje się arkusze stylów (pliki CSS) w pochodzeniu publicznym, można używać ścieżek względnych i  URI w kodzie. Oznacza to, że można odwoływać się do lokalizacji obrazów tła i innych obiektów względem lokalizacji zasobu, który go nazywa.

+ Chociaż można skonstruować adres URL pochodzenia publicznego, należy zachować ostrożność i upewnić się, że korzystasz z właściwości kontekstowej strony, i postępuj zgodnie z  wskazówkami w tym celu. Przyczyną tego jest to, że jeśli dostęp do witryny CDN stanie się niedostępny, adres URL nie będzie automatycznie rozpoznawał Twojej organizacji w aplikacji SharePoint Online i może spowodować przerwane linki lub inne błędy. Adres URL może również ulec zmianie, dlatego nie powinien być po prostu kodowany na dysku twardym zgodnie z bieżącą wartością.

+ Domyślnymi typami plików uwzględnionych dla pochodzenia publicznego są pliki css, eot, .gif, ico, jpeg, .jpg, .js, map, .png, svg, ttf, woff i woff2. Możesz określić dodatkowe typy plików.

+ Zasady można skonfigurować w taki sposób, aby wykluczać zasoby identyfikowane przez klasyfikacje witryn określone przez użytkownika. Na przykład możesz wyłączyć wszystkie zasoby oznaczone jako poufne lub ograniczone, nawet jeśli są one dozwolonym typem pliku i znajdują się w publicznym pochodzenia.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Atrybuty i zalety hostingu zasobów prywatnych

+ Pochodzenie prywatne może być używane tylko w przypadku SharePoint zasobów online.

+ Użytkownicy mogą uzyskać dostęp do zasobów z prywatnego pochodzenia tylko wtedy, gdy mają uprawnienia dostępu do kontenera. Dostęp anonimowy do tych zasobów jest blokowany.

+ Do zasobów  pochodzenia prywatnego należy się odwzajemnić z dzierżawy usługi SharePoint Online. Bezpośredni dostęp do prywatnych CDN nie działa.

+ Po usunięciu środka trwałego z pochodzenia prywatnego środek trwały może być nadal dostępny przez godzinę w pamięci podręcznej. jednak w ciągu 15 minut od usunięcia zasobu CDN nieprawidłowe linki do tego zasobu.

+ Domyślne typy plików, które są uwzględniane dla pochodzenia prywatnego, to: .gif, ico, jpeg, .jpg, .js i .png. Możesz określić dodatkowe typy plików.

+ Podobnie jak w przypadku pochodzenia publicznego, można skonfigurować zasady tak, aby wykluczać zasoby określone przez klasyfikacje witryn, nawet jeśli wszystkie zasoby w folderze lub bibliotece dokumentów są dołączane za pomocą symboli wieloznacznych.

Aby uzyskać więcej informacji o tym, dlaczego warto używać Office 365 CDN, ogólnych pojęć CDN i innych sieci CDN firmy Microsoft, których można używać z dzierżawą usługi Office 365, zobacz Sieci dostarczania [zawartości](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Domyślne CDN pochodzenia

Jeśli nie określono inaczej, Office 365 domyślne pochodzenie po włączeniu tej Office 365 CDN. Jeśli na początek nie zdecydujesz się na ich zainicjowanie, możesz dodać te źródła po ukończeniu konfiguracji. Jeśli nie rozumiesz konsekwencji pominięcie konfiguracji domyślnego pochodzenia i nie masz konkretnego powodu, musisz zezwolić na ich tworzenia po włączeniu tego CDN.

Domyślne pochodzenie CDN prywatne:

+ \*/userphoto.aspx
+ \*/siteassets

Domyślne pochodzenie CDN publicznych:

+ \*/masterpage
+ \*/style library
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_ jest domyślnym publicznym pochodzeniem, które zostało dodane Office 365 CDN grudnia 2017 r. To pochodzenie musi być obecne, aby SharePoint Framework rozwiązania w CDN działały. Jeśli zostało włączone Office 365 CDN przed grudniem 2017 r. lub jeśli po włączeniu CDN pominięto konfigurację domyślnych pochodzenia, możesz ręcznie dodać to pochodzenie. Aby uzyskać więcej informacji, zobacz [Mój składników Web Part po stronie SharePoint Framework nie działa](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Konfigurowanie i konfigurowanie Office 365 CDN przy użyciu powłoki zarządzania SharePoint online

Procedury w tej sekcji wymagają użycia powłoki zarządzania usługi SharePoint Online do łączenia się z usługą SharePoint Online. Aby uzyskać instrukcje, [Połączenie aby SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Wykonaj poniższe czynności, aby skonfigurować konto usługi CDN hostować zasoby w u SharePoint Online przy użyciu powłoki zarządzania usługi SharePoint online.

<details>
  <summary>Kliknij, aby rozwinąć</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Umożliwianie organizacji korzystania z Office 365 CDN

Zanim dokonasz zmian w ustawieniach CDN dzierżawy, pobierz bieżący stan prywatnej konfiguracji usługi CDN w swojej Office 365 dzierżawie. Połączenie dzierżawy przy użyciu powłoki zarządzania SharePoint online:

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Teraz użyj **polecenia cmdlet Get-SPOTenantCdnEnabled** w celu pobrania CDN stanu usługi z dzierżawy:

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

Stan określonej CDN CdnType będzie wyprowadzany do ekranu.

Użyj **polecenia cmdlet Set-SPOTenantCdnEnabled**, aby umożliwić twojej organizacji korzystanie z Office 365 CDN. Możesz umożliwić organizacji korzystanie z pochodzenia publicznego, pochodzenia prywatnego lub obu tych osób jednocześnie. Możesz również skonfigurować aplikację CDN pominąć konfigurowanie domyślnego pochodzenia po jego włączeniu. Te pochodzenie możesz dodać później, jak opisano w tym temacie.

W Windows PowerShell dla SharePoint Online:

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Aby na przykład umożliwić organizacji używanie zarówno pochodzenia publicznego, jak i prywatnego, wpisz następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Aby umożliwić organizacji używanie zarówno pochodzenia publicznego, jak i prywatnego, bez konfigurowania domyślnego pochodzenia, wpisz następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Zobacz Domyślne [CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) pochodzenia, aby uzyskać informacje o pochodzeniech, które są domyślnie aprowowane po włączeniu Office 365 CDN, oraz potencjalny wpływ na pominięcie konfiguracji domyślnego pochodzenia.

Aby umożliwić organizacji używanie pochodzenia publicznego, wpisz następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Aby umożliwić organizacji korzystanie z pochodzenia prywatnego, wpisz następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet, zobacz [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Zmienianie listy typów plików uwzględnianych w Office 365 CDN (opcjonalnie)

> [!TIP]
> Definiowanie typów plików przy użyciu polecenia cmdlet **Set-SPOTenantCdnPolicy** powoduje zastąpienie obecnie zdefiniowanej listy. Jeśli chcesz dodać do listy dodatkowe typy plików, użyj najpierw polecenia cmdlet, aby dowiedzieć się, jakie typy plików są już dozwolone, i uwzględnij je na liście razem z nowymi.

Użyj polecenia **cmdlet Set-SPOTenantCdnPolicy**, aby zdefiniować statyczne typy plików, które mogą być hostowane przez pochodzenie publiczne i prywatne w CDN. Domyślnie dozwolone są typowe typy elementów zawartości, takie jak css, .gif, .jpg i .js.

W Windows PowerShell dla SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Aby na przykład włączyć CDN do hostować pliki css i .png, wprowadź to polecenie:

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Aby sprawdzić, jakie typy plików są obecnie dozwolone przez CDN, użyj polecenia cmdlet **Get-SPOTenantCdnPolicies**:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Aby uzyskać więcej informacji o tych poleceniach cmdlet, zobacz [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) i [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Zmienianie listy klasyfikacji witryn, które chcesz wykluczyć z Office 365 CDN (opcjonalnie)

> [!TIP]
> Wyłączenie klasyfikacji witryny przy użyciu polecenia cmdlet **Set-SPOTenantCdnPolicy** powoduje zastąpienie aktualnie zdefiniowanej listy. Jeśli chcesz wykluczyć dodatkowe klasyfikacje witryny, użyj najpierw polecenia cmdlet, aby dowiedzieć się, które klasyfikacje są już wykluczone, a następnie dodaj je wraz z nowymi klasyfikacjami.

Użyj **polecenia cmdlet Set-SPOTenantCdnPolicy**, aby wykluczyć klasyfikacje witryny, które nie mają być dostępne w CDN. Domyślnie nie są wykluczane żadne klasyfikacje witryn.

W Windows PowerShell dla SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Aby sprawdzić, które klasyfikacje witryn są obecnie ograniczone, użyj polecenia cmdlet **Get-SPOTenantCdnPolicies** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Zwrócone właściwości to _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ oraz _ExcludeIfNoScriptDisabled_.

Właściwość _IncludeFileExtensions_ zawiera listę rozszerzeń plików, które będą obsługiwane z pliku CDN.

> [!NOTE]
> Domyślne rozszerzenia plików różnią się od publicznych i prywatnych.

Właściwość _ExcludeRestrictedSiteClassifications_ zawiera klasyfikacje witryn, które chcesz wykluczyć z CDN. Możesz na przykład wykluczyć witryny oznaczone jako poufne, aby zawartość z witryn, do których zastosowano klasyfikację, nie była uwzględniana w CDN.

Właściwość _ExcludeIfNoScriptDisabled_ wyklucza zawartość z CDN na podstawie ustawień atrybutów _NoScript_ na poziomie witryny. Domyślnie atrybut _NoScript ma ustawioną_ wartość **Włączone** dla _nowoczesnych witryn_ i **Wyłączone dla** witryn _klasycznych_ . Zależy to od ustawień dzierżawy.

Aby uzyskać więcej informacji o tych poleceniach cmdlet, zobacz [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) i [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Dodaj pochodzenie swoich środków trwałych

Zdefiniuj pochodzenie za pomocą polecenia cmdlet **Add-SPOTenantCdnOrigin** . Możesz zdefiniować wiele pochodzenia. Pochodzenie to adres URL, który wskazuje bibliotekę SharePoint lub folder zawierający zasoby, które mają być hostowane przez CDN.

> [!IMPORTANT]
> Nigdy nie należy umieszczać zasobów zawierających informacje o użytkownikach lub uznawanych za poufne dla organizacji w przypadku pochodzenia publicznego.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Wartość ścieżki _jest ścieżką_ względną do biblioteki lub folderu zawierającego składniki majątku. Oprócz ścieżek względnych można używać symboli wieloznacznych. Pochodzenie obsługują symbole wieloznaczne poprzedniane adresem URL. Pozwala to tworzyć pochodzenie obejmujące wiele witryn. Aby na przykład dołączyć wszystkie zasoby do folderu stron wzorcowych wszystkich witryn jako publiczne pochodzenie w CDN, wpisz następujące polecenie:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Symbol wieloznaczny ***/** może być używany tylko na początku ścieżki i będzie odpowiadać wszystkim segmentom adresu URL poniżej określonego adresu URL.
+ Ścieżka może wskazać bibliotekę dokumentów, folder lub witrynę. Na przykład ścieżka _*/site1_ będzie odpowiadać wszystkim bibliotekom dokumentów w witrynie.

Możesz dodać pochodzenie z określoną ścieżką względną. Nie można dodać pochodzenia przy użyciu pełnej ścieżki.

W tym przykładzie do biblioteki witryny jest dodano pochodzenie prywatne biblioteki witryny w konkretnej witrynie:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

W tym przykładzie do biblioteki elementów zawartości witryny zbioru witryn zostanie dodano pochodzenie prywatne folderu _folder1_ :

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Jeśli ścieżka zawiera spację, możesz ją ująć w podwójny cudzysłów lub zamienić ją na kodowanie adresu URL %20. W poniższych przykładach dodano pochodzenie prywatne _folderu 1_ w bibliotece elementów zawartości witryny zbioru witryn:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> W przypadku pochodzenia prywatnego zasoby udostępniane z pochodzenia muszą być opublikowane w wersji głównych, aby można było uzyskiwać do nich dostęp z CDN.

Po uruchomieniu tego polecenia system synchronizuje konfigurację między centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Przykład: konfigurowanie publicznego pochodzenia stron wzorcowych i biblioteki stylów dla witryny SharePoint Online

Te pochodzenie są zwykle ustawione domyślnie po włączeniu reguły Office 365 CDN. Jeśli jednak chcesz włączyć je ręcznie, wykonaj poniższe czynności.

+ Aby zdefiniować bibliotekę stylów jako źródło publiczne, użyj polecenia cmdlet **Add-SPOTenantCdnOrigin** .

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Za pomocą polecenia cmdlet **Add-SPOTenantCdnOrigin** można zdefiniować strony wzorcowe jako publiczne pochodzenie.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Po uruchomieniu tego polecenia system synchronizuje konfigurację między centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Przykład: konfigurowanie pochodzenia prywatnego dla zasobów witryny, stron witryny i obrazów publikowania w witrynie SharePoint Online

+ Użyj polecenia **cmdlet Add-SPOTenantCdnOrigin** , aby zdefiniować folder zasobów witryny jako pochodzenie prywatne.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Użyj polecenia **cmdlet Add-SPOTenantCdnOrigin** , aby zdefiniować folder stron witryny jako pochodzenie prywatne.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Użyj polecenia **cmdlet Add-SPOTenantCdnOrigin** , aby zdefiniować folder obrazów publikowania jako pochodzenie prywatne.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Po uruchomieniu tego polecenia system synchronizuje konfigurację między centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Przykład: Konfigurowanie prywatnego pochodzenia zbioru witryn dla witryny w SharePoint Online

Aby zdefiniować zbiór witryn jako pochodzenie prywatne, użyj polecenia cmdlet **Add-SPOTenantCdnOrigin** . Przykład:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Po uruchomieniu tego polecenia system synchronizuje konfigurację między centrum danych. Może zostać wyświetlony komunikat o _oczekiwaniu na konfigurację_, który jest oczekiwany, ponieważ dzierżawa usługi SharePoint Online łączy się z usługą CDN sieci. Może to potrwać do 15 minut.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Zarządzanie Office 365 CDN

Po skonfigurowaniu serwera konfiguracji CDN wprowadzać zmiany w konfiguracji w przypadku aktualizowania zawartości lub zmieniania potrzeb zgodnie z opisem w tej sekcji.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Dodawanie, aktualizowanie i usuwanie zasobów z Office 365 CDN

Po zakończeniu konfigurowania możesz w dowolnej chwili dodać nowe zasoby oraz zaktualizować lub usunąć istniejące zasoby. Po prostu dokonaj zmian w elementach zawartości w folderze SharePoint bibliotece oznaczonej jako pochodzenie. Nowy zasób jest natychmiast dostępny za pośrednictwem CDN nowego zasobu. Jednak po zaktualizowaniu zasobu propagacja nowej kopii i stanie się dostępna w nowej kopii w ciągu 15 CDN.

Jeśli chcesz pobrać lokalizację pochodzenia, możesz użyć polecenia cmdlet **Get-SPOTenantCdnOrigins** . Aby uzyskać informacje na temat używania tego polecenia cmdlet, zobacz [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Usuwanie pochodzenia z Office 365 CDN

Możesz usunąć dostęp do folderu lub biblioteki SharePoint, która jest zidentyfikowana jako pochodzenie. W tym celu użyj polecenia cmdlet **Remove-SPOTenantCdnOrigin** .

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Aby uzyskać informacje na temat używania tego polecenia cmdlet, zobacz [Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modyfikowanie pochodzenia w Office 365 CDN

Nie można modyfikować utworzonego przez Ciebie pochodzenia. Zamiast tego usuń pochodzenie, a następnie dodaj nowe. Aby uzyskać więcej informacji, zobacz [Aby](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) usunąć pochodzenie z Office 365 CDN i Aby dodać pochodzenie [dla swoich środków trwałych](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Wyłącz Office 365 CDN

Użyj **polecenia cmdlet Set-SPOTenantCdnEnabled**, aby wyłączyć CDN dla organizacji. Jeśli dla źródła danych włączono zarówno pochodzenie publiczne, jak i prywatne, CDN uruchom polecenie cmdlet dwa razy, jak pokazano w poniższych przykładach.

Aby wyłączyć używanie pochodzenia publicznego w CDN, wprowadź następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Aby wyłączyć korzystanie z pochodzenia prywatnego w CDN, wprowadź następujące polecenie:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet, zobacz [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>Konfigurowanie i konfigurowanie serwera Office 365 CDN przy użyciu programu PowerShell dla programu PnP

Procedury w tej sekcji wymagają nawiązania połączenia z usługą SharePoint Online za pomocą programu PowerShell dla programu PnP. Aby uzyskać instrukcje, [zobacz Wprowadzenie do programu PowerShell dla programu PnP](https://github.com/SharePoint/PnP-PowerShell#getting-started).

Wykonaj poniższe czynności, aby skonfigurować konto usługi CDN hostować zasoby w u SharePoint Online przy użyciu programu PowerShell dla programu PowerShell dla programuPnP.

<details>
  <summary>Kliknij, aby rozwinąć</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Umożliwianie organizacji korzystania z Office 365 CDN

Zanim dokonasz zmian w ustawieniach CDN dzierżawy, pobierz bieżący stan prywatnej konfiguracji usługi CDN w swojej Office 365 dzierżawie. Połączenie dzierżawy przy użyciu programu PowerShell dla programu PnP:

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

Teraz użyj **polecenia cmdlet Get-PnPTenantCdnEnabled** w celu pobrania CDN stanu usługi z dzierżawy:

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

Stan określonej CDN CdnType będzie wyprowadzany do ekranu.

Użyj **polecenia cmdlet Set-PnPTenantCdnEnabled**, aby umożliwić Twojej organizacji korzystanie z Office 365 CDN. Możesz umożliwić organizacji używanie jednocześnie pochodzenia publicznego, pochodzenia prywatnego lub obu tych źródeł. Możesz również skonfigurować aplikację CDN pominąć konfigurowanie domyślnego pochodzenia po jego włączeniu. Te pochodzenie możesz dodać później, jak opisano w tym temacie.

W programie PowerShell dla programu PnP:

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Aby na przykład umożliwić organizacji używanie zarówno pochodzenia publicznego, jak i prywatnego, wpisz następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

Aby umożliwić organizacji używanie zarówno pochodzenia publicznego, jak i prywatnego, bez konfigurowania domyślnego pochodzenia, wpisz następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Zobacz Domyślne [CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) pochodzenia, aby uzyskać informacje o pochodzeniech, które są domyślnie aprowowane po włączeniu Office 365 CDN, oraz potencjalny wpływ na pominięcie konfiguracji domyślnego pochodzenia.

Aby umożliwić organizacji używanie pochodzenia publicznego, wpisz następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

Aby umożliwić organizacji korzystanie z pochodzenia prywatnego, wpisz następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet, zobacz [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Zmienianie listy typów plików uwzględnianych w Office 365 CDN (opcjonalnie)

> [!TIP]
> Definiowanie typów plików za pomocą polecenia cmdlet **Set-PnPTenantCdnPolicy** powoduje zastąpienie obecnie zdefiniowanej listy. Jeśli chcesz dodać do listy dodatkowe typy plików, użyj najpierw polecenia cmdlet, aby dowiedzieć się, jakie typy plików są już dozwolone, i uwzględnij je na liście razem z nowymi.

Użyj polecenia **cmdlet Set-PnPTenantCdnPolicy**, aby zdefiniować statyczne typy plików, które mogą być hostowane przez pochodzenie publiczne i CDN. Domyślnie dozwolone są typowe typy elementów zawartości, takie jak css, .gif, .jpg i .js.

W programie PowerShell dla programu PnP:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Aby na przykład włączyć CDN do hostować pliki css i .png, wprowadź to polecenie:

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Aby sprawdzić, jakie typy plików są obecnie dozwolone przez CDN, użyj polecenia cmdlet **Get-PnPTenantCdnPolicies**:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Aby uzyskać więcej informacji o tych poleceniach cmdlet, zobacz [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) i [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Zmienianie listy klasyfikacji witryn, które chcesz wykluczyć z Office 365 CDN (opcjonalnie)

> [!TIP]
> Wyłączenie klasyfikacji witryny przy użyciu polecenia cmdlet **Set-PnPTenantCdnPolicy** powoduje zastąpienie aktualnie zdefiniowanej listy. Jeśli chcesz wykluczyć dodatkowe klasyfikacje witryny, użyj najpierw polecenia cmdlet, aby dowiedzieć się, które klasyfikacje są już wykluczone, a następnie dodaj je wraz z nowymi klasyfikacjami.

Użyj **polecenia cmdlet Set-PnPTenantCdnPolicy**, aby wykluczyć klasyfikacje witryn, które nie mają być dostępne w CDN. Domyślnie nie są wykluczane żadne klasyfikacje witryn.

W programie PowerShell dla programu PnP:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

Aby sprawdzić, które klasyfikacje witryny są obecnie ograniczone, użyj polecenia cmdlet **Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Zwrócone właściwości to _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ oraz _ExcludeIfNoScriptDisabled_.

Właściwość _IncludeFileExtensions_ zawiera listę rozszerzeń plików, które będą obsługiwane z pliku CDN.

> [!NOTE]
> Domyślne rozszerzenia plików różnią się od publicznych i prywatnych.

Właściwość _ExcludeRestrictedSiteClassifications_ zawiera klasyfikacje witryn, które chcesz wykluczyć z CDN. Możesz na przykład wykluczyć witryny oznaczone jako poufne, aby zawartość z witryn, do których zastosowano klasyfikację, nie była uwzględniana w CDN.

Właściwość _ExcludeIfNoScriptDisabled_ wyklucza zawartość z CDN na podstawie ustawień atrybutów _NoScript_ na poziomie witryny. Domyślnie atrybut _NoScript ma ustawioną_ wartość **Włączone** dla _nowoczesnych witryn_ i **Wyłączone dla** witryn _klasycznych_ . Zależy to od ustawień dzierżawy.

Aby uzyskać więcej informacji o tych poleceniach cmdlet, zobacz [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) i [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Dodaj pochodzenie swoich środków trwałych

Zdefiniuj pochodzenie za pomocą polecenia cmdlet **Add-PnPTenantCdnOrigin** . Możesz zdefiniować wiele pochodzenia. Pochodzenie to adres URL, który wskazuje bibliotekę SharePoint lub folder zawierający zasoby, które mają być hostowane przez CDN.

> [!IMPORTANT]
> Nigdy nie należy umieszczać zasobów zawierających informacje o użytkownikach lub uznawanych za poufne dla organizacji w przypadku pochodzenia publicznego.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Wartość ścieżki _jest ścieżką_ względną do biblioteki lub folderu zawierającego składniki majątku. Oprócz ścieżek względnych można używać symboli wieloznacznych. Pochodzenie obsługują symbole wieloznaczne poprzedniane adresem URL. Pozwala to tworzyć pochodzenie obejmujące wiele witryn. Aby na przykład dołączyć wszystkie zasoby do folderu stron wzorcowych wszystkich witryn jako publiczne pochodzenie w CDN, wpisz następujące polecenie:

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Symbol wieloznaczny ***/** może być używany tylko na początku ścieżki i będzie odpowiadać wszystkim segmentom adresu URL poniżej określonego adresu URL.
+ Ścieżka może wskazać bibliotekę dokumentów, folder lub witrynę. Na przykład ścieżka _*/site1_ będzie odpowiadać wszystkim bibliotekom dokumentów w witrynie.

Możesz dodać pochodzenie z określoną ścieżką względną. Nie można dodać pochodzenia przy użyciu pełnej ścieżki.

W tym przykładzie do biblioteki zasobów witryny jest dodano pochodzenie prywatne biblioteki zasobów witryny w określonej witrynie:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

W tym przykładzie do biblioteki elementów zawartości witryny zbioru witryn zostanie dodano pochodzenie prywatne folderu _folder1_ :

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Jeśli ścieżka zawiera spację, możesz ją ująć w podwójny cudzysłów lub zamienić ją na kodowanie adresu URL %20. W poniższych przykładach dodano pochodzenie prywatne _folderu 1_ w bibliotece elementów zawartości witryny zbioru witryn:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

> [!NOTE]
> W przypadku pochodzenia prywatnego zasoby udostępniane z pochodzenia muszą być opublikowane w wersji głównych, aby można było uzyskiwać do nich dostęp z CDN.

Po uruchomieniu tego polecenia system synchronizuje konfigurację między centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Przykład: konfigurowanie publicznego pochodzenia stron wzorcowych i biblioteki stylów dla witryny SharePoint Online

Te pochodzenie są zwykle ustawione domyślnie po włączeniu reguły Office 365 CDN. Jeśli jednak chcesz włączyć je ręcznie, wykonaj poniższe czynności.

+ Aby zdefiniować bibliotekę stylów jako źródło publiczne, użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** .

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Za pomocą polecenia cmdlet **Add-PnPTenantCdnOrigin** można zdefiniować strony wzorcowe jako publiczne pochodzenie.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Po uruchomieniu tego polecenia system synchronizuje konfigurację między centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Przykład: konfigurowanie pochodzenia prywatnego dla zasobów witryny, stron witryny i obrazów publikowania w witrynie SharePoint Online

+ Aby zdefiniować folder zasobów witryny jako pochodzenie prywatne, użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** .

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Aby zdefiniować folder stron witryny jako pochodzenie prywatne, użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** .

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Aby zdefiniować folder obrazów publikowania jako pochodzenie prywatne, użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** .

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Po uruchomieniu tego polecenia system synchronizuje konfigurację między centrum danych. Może to potrwać do 15 minut.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Przykład: Konfigurowanie prywatnego pochodzenia zbioru witryn dla witryny w SharePoint Online

Aby zdefiniować zbiór witryn jako pochodzenie prywatne, użyj polecenia cmdlet **Add-PnPTenantCdnOrigin** . Przykład:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Aby uzyskać więcej informacji na temat tego polecenia i jego składni, zobacz [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Po uruchomieniu tego polecenia system synchronizuje konfigurację między centrum danych. Może zostać wyświetlony komunikat o _oczekiwaniu na konfigurację_, który jest oczekiwany, ponieważ dzierżawa usługi SharePoint Online łączy się z usługą CDN sieci. Może to potrwać do 15 minut.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>Zarządzanie Office 365 CDN

Po skonfigurowaniu serwera konfiguracji CDN wprowadzać zmiany w konfiguracji w przypadku aktualizowania zawartości lub zmieniania potrzeb zgodnie z opisem w tej sekcji.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Dodawanie, aktualizowanie i usuwanie zasobów z Office 365 CDN

Po zakończeniu konfigurowania możesz w dowolnej chwili dodać nowe zasoby oraz zaktualizować lub usunąć istniejące zasoby. Po prostu dokonaj zmian w elementach zawartości w folderze SharePoint bibliotece oznaczonej jako pochodzenie. Nowy zasób jest natychmiast dostępny za pośrednictwem CDN nowego zasobu. Jednak po zaktualizowaniu zasobu propagacja nowej kopii i stanie się dostępna w nowej kopii w ciągu 15 CDN.

Jeśli chcesz pobrać lokalizację pochodzenia, możesz użyć polecenia cmdlet **Get-PnPTenantCdnOrigin** . Aby uzyskać informacje dotyczące używania tego polecenia cmdlet, zobacz [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Usuwanie pochodzenia z Office 365 CDN

Możesz usunąć dostęp do folderu lub biblioteki SharePoint, która jest zidentyfikowana jako pochodzenie. W tym celu użyj polecenia cmdlet **Remove-PnPTenantCdnOrigin** .

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Aby uzyskać informacje dotyczące używania tego polecenia cmdlet, zobacz [Remove-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modyfikowanie pochodzenia w Office 365 CDN

Nie można modyfikować utworzonego przez Ciebie pochodzenia. Zamiast tego usuń pochodzenie, a następnie dodaj nowe. Aby uzyskać więcej informacji, zobacz [Aby](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) usunąć pochodzenie z Office 365 CDN i Aby dodać pochodzenie [dla swoich środków trwałych](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Wyłącz Office 365 CDN

Za pomocą polecenia cmdlet **Set-PnPTenantCdnEnabled** wyłącz CDN dla organizacji. Jeśli dla źródła danych włączono zarówno pochodzenie publiczne, jak i prywatne, CDN uruchom polecenie cmdlet dwa razy, jak pokazano w poniższych przykładach.

Aby wyłączyć używanie pochodzenia publicznego w CDN, wprowadź następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

Aby wyłączyć korzystanie z pochodzenia prywatnego w CDN, wprowadź następujące polecenie:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet, zobacz [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>Konfigurowanie i konfigurowanie Office 365 CDN przy użyciu interfejsu Office 365 cli

Procedury w tej sekcji wymagają zainstalowania Office 365 [cli](https://aka.ms/o365cli). Następnie połącz się z dzierżawą Office 365 przy użyciu [polecenia](https://pnp.github.io/office365-cli/cmd/login/) logowania.

Wykonaj poniższe czynności, aby skonfigurować konto usługi CDN hostować zasoby w u SharePoint Online przy użyciu interfejsu Office 365 cli.

<details>
  <summary>Kliknij, aby rozwinąć</summary>

### <a name="enable-the-office-365-cdn"></a>Włącz Office 365 CDN

Możesz zarządzać stanem dzierżawy Office 365 CDN korzystając z polecenia [zestawu sieci cdn](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) usługi spo.

Aby włączyć Office 365 publiczne CDN w dzierżawie:

```cli
spo cdn set --type Public --enabled true
```

Aby włączyć Office 365 SharePoint CDN, wykonaj:

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Wyświetlanie bieżącego stanu Office 365 CDN

Aby sprawdzić, czy określony typ pliku Office 365 CDN jest włączony lub wyłączony, użyj polecenia pobierz [sieci CDN usługi](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) spo.

Aby sprawdzić, czy Office 365 publiczne CDN włączone, wykonaj polecenie:

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Wyświetlanie Office 365 CDN pochodzenia

Aby wyświetlić obecnie skonfigurowane pochodzenie Office 365 publicznych CDN:

```cli
spo cdn origin list --type Public
```

Zobacz [Domyślne CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins), aby uzyskać informacje o pochodzeniech, które są domyślnie aprowowane po włączeniu Office 365 CDN.

### <a name="add-an-office-365-cdn-origin"></a>Dodawanie Office 365 CDN pochodzenia

> [!IMPORTANT]
> Nigdy nie należy umieszczać zasobów uznanych za poufne dla organizacji w bibliotece SharePoint dokumentów skonfigurowanej jako pochodzenie publiczne.

Użyj polecenia [dodawania pochodzenia sieci cdn](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) w sieci spo, aby CDN pochodzenia. Możesz zdefiniować wiele pochodzenia. Pochodzenie to adres URL, który wskazuje bibliotekę SharePoint lub folder zawierający zasoby, które mają być hostowane przez CDN.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

Gdzie `path` znajduje się ścieżka względna do folderu zawierającego składniki majątku. Oprócz ścieżek względnych można używać symboli wieloznacznych.

Aby dołączyć wszystkie zasoby do galerii **stron** wzorcowych wszystkich witryn jako pochodzenie publiczne, wykonaj następujące polecenie:

```cli
spo cdn origin add --type Public --origin */masterpage
```

Aby skonfigurować pochodzenie prywatne dla określonego zbioru witryn, wykonaj:

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Po dodaniu CDN pochodzenia pobieranie plików za pośrednictwem CDN może potrwać do 15 minut. Możesz sprawdzić, czy dane pochodzenie zostało już włączone, za pomocą polecenia [Lista pochodzenia sieci cdn w sieci](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) Spo.

### <a name="remove-an-office-365-cdn-origin"></a>Usuwanie Office 365 CDN pochodzenia

Użyj polecenia [usuwania pochodzenia sieci cdn](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) spo, aby usunąć CDN dla określonego CDN cdn.

Aby usunąć pochodzenie publiczne z CDN, wykonaj:

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> Usunięcie CDN pochodzenia nie ma wpływu na pliki przechowywane w żadnej bibliotece dokumentów pasującej do tego pochodzenia. Jeśli do tych zasobów odwołujemy się przy użyciu ich SharePoint URL, SharePoint zostanie automatycznie przełączony z powrotem do pierwotnego adresu URL, który wskaże bibliotekę dokumentów. Jeśli jednak do zasobów odwoływno się przy użyciu publicznego adresu URL CDN, usunięcie pochodzenia spowoduje zerwanie linku i będzie konieczne ich ręczne zmienianie.

### <a name="modify-an-office-365-cdn-origin"></a>Modyfikowanie początkowego Office 365 CDN układu

Nie jest możliwe modyfikowanie istniejącego CDN pochodzenia. Zamiast tego należy usunąć wcześniej zdefiniowane pochodzenie CDN `spo cdn origin remove` przy użyciu tego polecenia i dodać nowe za pomocą `spo cdn origin add` tego polecenia.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Zmienianie typów plików uwzględnianych w Office 365 CDN

W programie CDN są domyślnie uwzględniane następujące typy plików: _css, eot, .gif, ico, jpeg, .jpg, .js, map, .png, svg, ttf, woff i woff2_. Jeśli chcesz uwzględnić dodatkowe typy plików w skoroszycie, CDN konfigurację sieci CDN za pomocą polecenia [zestawu zasad sieci cdn w uch](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/).

> [!NOTE]
> Zmiana typu listy plików powoduje zastąpienie obecnie zdefiniowanej listy. Jeśli chcesz dołączyć dodatkowe typy plików, najpierw użyj polecenia listy zasad [sieci cdn](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) w sieci spo, aby dowiedzieć się, które typy plików są obecnie skonfigurowane.

Aby dodać _typ pliku JSON_ do domyślnej listy typów plików dostępnych w publicznym CDN, wykonaj następujące polecenie:

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Zmienianie listy klasyfikacji witryn, które chcesz wykluczyć z Office 365 CDN

Użyj polecenia [zestawu zasad sieci CDN](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) usługi Spo, aby wykluczyć klasyfikacje witryn, które nie mają być dostępne w CDN. Domyślnie nie są wykluczane żadne klasyfikacje witryn.

> [!NOTE]
> Zmiana listy wykluczonych klasyfikacji witryn powoduje zastąpienie obecnie zdefiniowanej listy. Jeśli chcesz wykluczyć dodatkowe klasyfikacje, najpierw użyj polecenia listy zasad [sieci CDN usługi Spo](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) , aby dowiedzieć się, które klasyfikacje są obecnie skonfigurowane.

Aby wykluczyć witryny sklasyfikowane jako _OII_ z publicznym CDN, wykonaj

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Wyłącz Office 365 CDN

Aby wyłączyć Office 365 CDN użyj `spo cdn set` tego polecenia, na przykład:

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>Używanie zasobów CDN firmy

Po włączeniu zasad i CDN i pochodzenia możesz zacząć używać swoich CDN zasobów.

Ta sekcja pomoże Ci zrozumieć, jak używać adresów URL CDN na stronach i w zawartości witryny SharePoint, aby program SharePoint przekierowywać żądania dotyczące środków trwałych zarówno z pochodzenia publicznego, jak i prywatnego do CDN.

+ [Aktualizowanie linków do CDN zasobów](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Używanie środków trwałych pochodzenia publicznego](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Używanie środków trwałych pochodzenia prywatnego](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

Aby uzyskać informacje na temat używania CDN do hostowania składników Web Part po stronie klienta, zobacz temat Hostowanie składników Web Part po stronie klienta z witryny Office 365 CDN (Witaj świecie, część [4)](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).

> [!NOTE]
> Jeśli dodasz folder _ClientSideAssets_ do prywatnej CDN  pochodzenia, CDN niestandardowe party Web Part hostowane nie będą renderowane. Pliki używane przez składników Web Part SPFX mogą korzystać tylko z publicznego CDN, a folder ClientSideAssets jest domyślnym pochodzeniem elementów CDN.

### <a name="updating-links-to-cdn-assets"></a>Aktualizowanie linków do CDN zasobów

Aby użyć zasobów dodanych do pochodzenia, wystarczy zaktualizować linki do oryginalnego pliku ze ścieżką do tego pliku.

+ Edytuj stronę lub zawartość zawierającą linki do zasobów dodanych do pochodzenia. Możesz również użyć jednej z kilku metod, aby globalnie wyszukiwać i zamieniać linki w obrębie poszczególnych witryn lub zbiorów witryn, jeśli chcesz zaktualizować link do danego zasobu we wszystkich miejscach, w których się on pojawia.
+ W przypadku każdego linku do zasobu w pochodzeniu zamień ścieżkę na ścieżkę do pliku w CDN pochodzenia. Możesz użyć ścieżek względnych.
+ Zapisz stronę lub zawartość.

Rozważ na przykład obraz _/site/SiteAssets/images/image.png_, który został skopiowany do folderu biblioteki dokumentów _/site/CDN_origins/public/_. Aby użyć zasobu CDN, zastąp oryginalną ścieżkę lokalizacji pliku obrazu ścieżką do pochodzenia, aby nowy adres URL _/site/CDN_origins/public/image.png_.

Jeśli zamiast ścieżki względnej chcesz użyć pełnego adresu URL zasobu, skonstruuj link w ten sposób:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> Ogólnie nie należy kodować adresów URL bezpośrednio do zasobów w CDN. W razie potrzeby można jednak ręcznie skonstruować adresy URL dla zasobów publicznie pochodzenia. Aby uzyskać więcej informacji, [zobacz Hardcoding CDN URL dla zasobów publicznych](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets).

Aby dowiedzieć się, jak sprawdzić, czy mają być obsługiwane środki trwałe z CDN, zobacz Jak potwierdzić, że mają być obsługiwane przez [CDN?](use-microsoft-365-cdn-with-spo.md#CDNConfirm) w tece Rozwiązywanie problemów z [Office 365 CDN.](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting)

### <a name="using-assets-in-public-origins"></a>Używanie środków trwałych pochodzenia publicznego

Funkcja **publikowania** w usłudze SharePoint Online automatycznie ponownie zapisuje adresy URL środków trwałych przechowywanych w pochodzenia publicznym na ich CDN odpowiedniki, dzięki czemu zasoby są obsługiwane z usługi CDN zamiast SharePoint.

Jeśli Twoje pochodzenie znajduje się w witrynie z włączoną funkcją publikowania i zasoby, które chcesz rozładować do CDN, znajdują się w jednej z następujących kategorii, program SharePoint automatycznie ponownie zapisuje adresy URL środków trwałych pochodzenia, o ile nie został wykluczany przez zasady CDN.

Poniżej przedstawiono omówienie linków, które są automatycznie pisane przez funkcję publikowania SharePoint publikowania:

+ Adresy URL IMG/LINK/CSS w odpowiedziach HTML na klasycznej stronie publikowania
  + Dotyczy to obrazów dodanych przez autorów w obrębie zawartości HTML strony
+ Adresy URL obrazów w bibliotece obrazów ze składników Web Part pokazu slajdów
+ Pola obrazu w wynikach interfejsu API REST listy splist (RenderListDataAsStream)
  + Korzystanie z nowej właściwości _ImageFieldsToTryRewriteToCdnUrls_ w celu zapewnienia rozdzielonych przecinkami listy pól
  + Obsługa pól hiperlinków i pól PublishingImage
+ SharePoint odwzorowań obrazu

Poniższy diagram przedstawia przepływ pracy, gdy SharePoint żądanie strony zawierającej zasoby z publicznego pochodzenia.

![Diagram przepływu pracy: pobieranie Office 365 CDN od publicznego pochodzenia.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "Przepływ pracy: pobieranie Office 365 CDN od publicznego pochodzenia")

> [!TIP]
> Jeśli chcesz wyłączyć automatyczne ponowne pismo dla określonych adresów URL na stronie, możesz wyewidencjonować tę stronę i dodać parametr ciągu zapytania **? Na końcu każdego** linku, który chcesz wyłączyć, kliknij opcję NoAutoReWrites=true.

#### <a name="constructing-cdn-urls-for-public-assets"></a>Konstruowanie CDN URL dla zasobów publicznych

Jeśli funkcja  publikowania nie jest włączona dla pochodzenia publicznego lub zasób nie jest jednym z typów łączy obsługiwanych przez funkcję automatycznego ponownego tworzenia usługi CDN, możesz ręcznie skonstruować adresy URL do lokalizacji zasobów programu CDN i używać tych adresów URL w swojej zawartości.

> [!NOTE]
> Nie można kodować ani konstruować adresów URL CDN url do zasobów w pochodzeniu prywatnym, ponieważ wymagany token dostępu, który tworzy ostatnią sekcję adresu URL, jest generowany w momencie zażądania zasobu. Adres URL pliku publicznej można utworzyć CDN, a adres URL nie powinien być kodowany na dysku twardym, ponieważ może ulec zmianie.

W przypadku publicznych CDN adres URL będzie wyglądał następująco:

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

Zastąp **nazwę TenantHostName swoją** nazwą dzierżawy. Przykład:

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> Aby skonstruować prefiks, należy użyć właściwości kontekstowej strony zamiast kodowania "https://publiccdn.sharepointonline.com". Adres URL może ulec zmianie i nie powinien być kodowany na dysku twardym. Jeśli używasz szablonów wyświetlania w aplikacji Klasyczne SharePoint Online, możesz użyć w szablonie wyświetlania właściwości "window._spPageContextInfo.publicCdnBaseUrl" do prefiksu adresu URL. W przypadku SPFx web part dla nowoczesnego i klasycznego SharePoint można użyć właściwości "this.context.pageContext.legacyPageContext.publicCdnBaseUrl". Spowoduje to podanie prefiksu, dzięki czemu w przypadku jego zmiany implementacja zostanie wraz z nim zaktualizowana. Na przykład dla programu SPFx adres URL można skonstruowany przy użyciu właściwości "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" + "/" + "host" + "/" + "relativeURL dla elementu". Zobacz [Używanie CDN w kodzie po](https://youtu.be/IH1RbQlbhIA) stronie klienta, który jest częścią [serii wydajności 1.](https://aka.ms/sppnp-perfvideos)


### <a name="using-assets-in-private-origins"></a>Używanie środków trwałych pochodzenia prywatnego

W przypadku używania środków trwałych pochodzeniu prywatnego dodatkowa konfiguracja nie jest wymagana. SharePoint Online adresy URL dla środków trwałych  pochodzenia prywatnego są automatycznie zapisywane, więc żądania dotyczące tych środków będą zawsze obsługiwane przez CDN. Nie można ręcznie tworzyć adresów URL w celu CDN środków trwałych na pochodzenie prywatne, ponieważ zawierają one tokeny, które muszą zostać wygenerowane automatycznie przez usługę SharePoint Online w momencie zażądania zasobu.

Dostęp do zasobów w pochodzenie prywatnego jest chroniony przez dynamicznie generowane tokeny na podstawie uprawnień użytkowników do pochodzenia z zastrzeżeniem opisanym w poniższych sekcjach. Użytkownicy muszą mieć co najmniej **przeczytany** dostęp do pochodzenia, aby użytkownicy CDN renderować zawartość.

Poniższy diagram przedstawia przepływ pracy, gdy SharePoint żądanie strony zawierającej zasoby z pochodzenia prywatnego.

![Diagram przepływu pracy: pobieranie Office 365 CDN od prywatnego pochodzenia.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "Przepływ pracy: pobieranie Office 365 CDN od prywatnego pochodzenia")

#### <a name="token-based-authorization-in-private-origins"></a>Autoryzacja oparta na tokenie w pochodzenie prywatnym

Dostęp do środków trwałych pochodzenia prywatnego w sklepie Office 365 CDN jest udzielany w tokenach generowanych przez firmę SharePoint Online. Użytkownicy, którzy mają już uprawnienia dostępu do folderu lub biblioteki wskazanej przez pochodzenie, są automatycznie udzielane tokeny, które zezwalają użytkownikowi na dostęp do pliku na podstawie ich poziomu uprawnień. Te tokeny dostępu są ważne od 30 do 90 minut po ich wygenerowaniu, aby zapobiec atakom powtarzania tokenu.

Po wygenerowaniu tokenu dostępu aplikacja SharePoint Online zwraca niestandardowy URI do klienta zawierające dwa parametry autoryzacji _:_ pojedyń (token autoryzacji brzegowej) i _oat_ (token autoryzacji pochodzenia). Struktura każdego tokenu to< czasu wygaśnięcia w formacie _czasowym >__< podpisu bezpiecznego >_. Przykład:

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Każda osoba mająca token może uzyskać dostęp do tego zasobu w CDN. Adresy URL zawierające te tokeny dostępu są jednak udostępniane tylko przez protokół HTTPS, dlatego jeśli adres URL nie zostanie jawnie udostępniony przez użytkownika końcowego przed wygaśnięciem tokenu, zasób nie będzie dostępny dla nieautoryzowanych użytkowników.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Uprawnienia na poziomie elementu nie są obsługiwane w przypadku środków trwałych pochodzenia prywatnego

Należy pamiętać, że SharePoint online nie obsługuje uprawnień na poziomie elementu dla środków trwałych  pochodzenia prywatnego. Na przykład w przypadku pliku znajdującego się w `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, użytkownicy mają efektywny dostęp do pliku pod następującymi warunkami:

|Użytkownik  |Uprawnienia  |Skuteczny dostęp  |
|---------|---------|---------|
|Użytkownik 1     |Ma dostęp do folderu1         |Dostęp do image1.jpg z CDN         |
|Użytkownik 2     |Nie ma dostępu do folderu1         |Nie można image1.jpg dostępu z CDN         |
|Użytkownik 3     |Nie ma dostępu do folderu1, ale uzyskuje jawne uprawnienie dostępu do usługi image1.jpg aplikacji SharePoint Online         |Można uzyskać dostęp do składnika image1.jpg bezpośrednio z usługi SharePoint Online, ale nie z CDN         |
|Użytkownik 4     |Ma dostęp do folderu1, ale jawnie odmówiono dostępu do folderu image1.jpg aplikacji SharePoint Online         |Nie można uzyskać dostępu do zasobu z usługi SharePoint Online, ale można uzyskać dostęp do zasobu z aplikacji CDN mimo odrzuconego dostępu do pliku w u SharePoint Online         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>Rozwiązywanie problemów z Office 365 CDN

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Jak sprawdzić, czy zasoby są obsługiwane przez CDN?

Po dodaniu linków do zasobów usługi CDN do strony możesz potwierdzić, że zasób jest obsługiwany z witryny CDN, przeglądając stronę, klikając prawym przyciskiem myszy obraz po jego renderowaniu i przeglądając adres URL obrazu.

Za pomocą narzędzi deweloperowych przeglądarki możesz również wyświetlić adres URL każdego zasobu na stronie lub użyć narzędzia do śledzenia sieci innej firmy.

> [!NOTE]
> Jeśli używasz narzędzia sieciowego, takiego jak Fiddler, aby przetestować swoje zasoby poza renderowaniem go ze strony programu SharePoint, musisz ręcznie dodać nagłówek referera "Referer: `https://yourdomain.sharepoint.com`" do żądania GET, gdzie adres URL jest głównym adresem URL Dzierżawy usługi SharePoint Online.

Nie można CDN URL bezpośrednio w przeglądarce sieci Web, ponieważ musisz mieć odsyłacza z usługi SharePoint Online. Jeśli jednak dodasz adres URL zasobu CDN do strony SharePoint, a następnie otworzysz tę stronę w przeglądarce, na stronie zostanie wyświetlony CDN zawartości.

Aby uzyskać więcej informacji na temat korzystania z narzędzi deweloperskiej przeglądarki Microsoft Edge, zobacz Microsoft Edge [narzędzia programowe](/microsoft-edge/devtools-guide).

Aby obejrzeć krótki klip wideo hostowany w kanale [YouTube](https://aka.ms/sppnp-videos) wzorce dewelopera i wskazówki dotyczące programu SharePoint przedstawiający sposób sprawdzenia, czy Twój CDN działa, zobacz Weryfikowanie użycia aplikacji [CDN](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5) i zapewnianie optymalnej łączności sieciowej.

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Dlaczego środki trwałe z nowego pochodzenia są niedostępne?
Środki trwałe nowego pochodzenia nie będą od razu dostępne do użycia, ponieważ propagacja rejestracji w sieci CDN oraz sposób przekazywanych z pochodzenia do magazynu CDN magazyn. Czas potrzebny na dostęp środków trwałych w CDN zależy od liczby zasobów i rozmiarów plików.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>Mój składników Web Part lub SharePoint Framework po stronie klienta nie działa

Gdy włączysz domyślną Office 365 CDN dla pochodzenia publicznego, usługa CDN automatycznie utworzy następujące domyślne pochodzenie:

+ */MASTERPAGE
+ BIBLIOTEKA */STYLE
+ */CLIENTSIDEASSETS

Jeśli brakuje pochodzenia */clientsideassets, SharePoint Framework rozwiązania nie powiodą się i nie zostaną wygenerowane żadne ostrzeżenia ani komunikaty o błędach. Tego pochodzenia może brakować, ponieważ CDN została włączona przy użyciu parametru _-NoDefaultOrigins_ ustawionego na **$true** lub z powodu ręcznego usunięcia pochodzenia.

Aby sprawdzić, jakie pochodzenie istnieje, możesz użyć następującego polecenia programu PowerShell:

```powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

Możesz też sprawdzić za pomocą interfejsu Office 365 wideo:

```cli
spo cdn origin list
```

Aby dodać pochodzenie w programie PowerShell:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Aby dodać pochodzenie w interfejsie Office 365 wideo:

```cli
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Jakie moduły programu PowerShell i powłoki interfejsu wideo muszą być potrzebne do pracy z Office 365 CDN?

Możesz pracować z tym interfejsem, Office 365 CDN moduł **powershell SharePoint zarządzania** usługą online lub interfejs **Office 365 cli**.

+ [Wprowadzenie do powłoki SharePoint zarządzania usługi Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [Instalowanie interfejsu Office 365 cli](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>Zobacz też

[Sieci dostarczania zawartości](./content-delivery-networks.md)

[Network planning and performance tuning for Office 365](./network-planning-and-performance.md)

[SharePoint wydajność — seria Office 365 CDN wideo](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
