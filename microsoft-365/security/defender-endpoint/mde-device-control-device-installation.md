---
title: Ochrona punktu końcowego w usłudze Microsoft Defender instalacja urządzenia sterującego urządzeniem
description: Ten temat zawiera instrukcje dotyczące instalacji Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia sterującego urządzeniem
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ccef3ec748983db89b6ceca9b8092eafbef0d899
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472622"
---
# <a name="microsoft-defender-for-endpoint-device-control-device-installation"></a>Ochrona punktu końcowego w usłudze Microsoft Defender instalacja urządzenia sterującego urządzeniem

**Dotyczy**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ochrona punktu końcowego w usłudze Microsoft Defender instalacja urządzenia sterującego urządzeniem umożliwia wykonania następującego zadania:

- Uniemożliwianie innym osobom instalowania określonych urządzeń.
- Zezwalaj użytkownikom na instalowanie określonych urządzeń, ale uniemożliwiaj innym.

> [!NOTE]
> Aby znaleźć różnicę między instalacją urządzenia a wymiennym nośnikiem dostępu do magazynu, zobacz Ochrona punktu końcowego w usłudze Microsoft Defender [Wymienna Storage urządzenia](/microsoft-365/security/defender-endpoint/device-control-removable-storage-protection?view=o365-worldwide&preserve-view=true).

|Uprawnienie|Uprawnienie|
|---|---|
|Access|Instalacja urządzenia |
|Tryb akcji|Zezwalaj, Zapobiegaj |
|Pomoc techniczna CSP|Tak|
|Obsługa zasad grupy|Tak|
|Pomoc techniczna oparta na użytkownikach|Nie|
|Obsługa maszynowa|Tak|

## <a name="prepare-your-endpoints"></a>Przygotowywanie punktów końcowych

Wdrażanie instalacji urządzeń na Windows 10, Windows 11 urządzeniach i Windows Server 2022.

## <a name="device-properties"></a>Właściwości urządzenia

Następujące właściwości urządzenia są obsługiwane przez pomoc techniczną w związku z instalacją urządzenia:

- Identyfikator urządzenia
- Identyfikator sprzętu
- Zgodny identyfikator
- Klasa urządzenia
- Typ urządzenia przenośnego: Niektóre urządzenia mogą być klasyfikowane jako Urządzenia wymienne. Urządzenie jest traktowane jako wymienne, gdy sterownik urządzenia, do którego jest podłączone, wskazuje, że urządzenie jest wymienne. Na przykład urządzenie USB jest zgłaszane jako wymienne przez sterowniki koncentratora USB, do którego jest podłączone.
Aby uzyskać więcej informacji, zobacz [Instalacja urządzenia w aplikacji Windows](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="policies"></a>Policies (zasady)

### <a name="allow-installation-of-devices-that-match-any-of-these-device-ids"></a>Zezwalaj na instalację urządzeń, które są zgodne z dowolnym z tych identyfikatorów urządzeń

To ustawienie zasad umożliwia określenie listy identyfikatorów Plug and Play i zgodnych identyfikatorów dla urządzeń Windows które mogą instalować. To ustawienie zasad jest przeznaczone do stosowania tylko wtedy, gdy  jest włączone ustawienie Zasad zastosuj kolejność warstwową oceny dla opcji Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach z kryteriami.

Jeśli to ustawienie zasad jest włączone wraz z ustawieniem Zastosuj kolejność oceny w warstwie Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach zgodnie z ustawieniem zasad kryteriów, program Windows może zainstalować lub zaktualizować każde urządzenie z identyfikatorem sprzętu lub zgodnym identyfikatorem Plug and Play wyświetlone na tworzyć listę, chyba że inne ustawienie zasad na tej samej lub wyższej warstwie hierarchii jest specjalnie zabronione   instalacji, na przykład następujące ustawienia zasad:

- Zapobiegaj instalacji urządzeń, które są zgodne z tymi identyfikatorami.
- Uniemożliwiaj instalację urządzeń, które są zgodne z dowolnymi identyfikatorami wystąpień tych urządzeń.

Jeśli ustawienie Zastosuj **porządek** oceny w warstwie dla opcji Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach jest włączone dla tego ustawienia zasad, wszystkie inne ustawienia zasad zapobiegające instalacji będą miały pierwszeństwo.

> [!NOTE]
> Ustawienie  zasad Zapobiegaj instalacji urządzeń, które nie zostały opisane przez inne ustawienia zasad, zostało zastąpione ustawieniem Zasad Zastosuj kolejność oceny w warstwie do wyboru dla opcji Zezwalaj i Zapobiegaj zasadom instalacji urządzeń na wszystkich urządzeniach zgodnie z ustawieniem zasad dopasowania do obsługiwanych wersji docelowych i Windows 11. Windows 10  Zalecane jest użycie ustawienia Zastosuj kolejność oceny w warstwie dla opcji **Zezwalaj** i Zapobiegaj zasadom instalacji urządzeń na wszystkich urządzeniach, jeśli to możliwe.

### <a name="allow-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Zezwalaj na instalację urządzeń, które są zgodne z dowolnym identyfikatorem wystąpienia tych urządzeń

To ustawienie zasad umożliwia określenie listy identyfikatorów wystąpień Plug and Play urządzeń dla urządzeń Windows które mogą zainstalować. To ustawienie zasad jest przeznaczone do stosowania tylko wtedy, gdy  jest włączone ustawienie Zasad zastosuj kolejność warstwową oceny dla opcji Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach z kryteriami.

Gdy to ustawienie zasad jest włączone wraz z ustawieniem Zastosuj kolejność oceny w warstwie Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach zgodnie z ustawieniem zasad kryterium, program Windows może zainstalować lub zaktualizować każde urządzenie, na którym identyfikator wystąpienia urządzenia programu Plug and Play jest wyświetlany na tworzyć listę, chyba że inne ustawienie zasad na tej samej lub wyższej warstwie w hierarchii wyraźnie zapobiega temu   instalacji, na przykład następujące ustawienia zasad:

- Zapobieganie instalacji urządzeń, które są zgodne z dowolnymi identyfikatorami wystąpień tych urządzeń

Jeśli ustawienie Zastosuj **porządek** oceny w warstwie dla opcji Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach jest włączone dla tego ustawienia zasad, wszystkie inne ustawienia zasad zapobiegające instalacji będą miały pierwszeństwo.

### <a name="allow-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Zezwalaj na instalację urządzeń przy użyciu sterowników, które są zgodne z tymi klasami konfiguracji urządzenia

To ustawienie zasad umożliwia globalne określenie listy unikatowych identyfikatorów (GUID) klasy konfiguracji urządzenia dla pakietów sterowników, które mogą Windows zainstalować. To ustawienie zasad jest przeznaczone do stosowania tylko wtedy, gdy  jest włączone ustawienie Zasad zastosuj kolejność warstwową oceny dla opcji Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach z kryteriami.

Jeśli to ustawienie zasad jest włączone wraz z ustawieniem Zastosuj kolejność oceny w warstwie Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach zgodnie z ustawieniem zasad kryterium, pakiet Windows może instalować lub aktualizować pakiety sterowników, których identyfikatory GUID klasy konfiguracji urządzenia są wyświetlane na tworzyć listę, chyba że inne ustawienie zasad w tej samej lub wyższej warstwie hierarchii uniemożliwia taką instalację.  na przykład następujące ustawienia zasad:

- Zapobieganie instalacji urządzeń dla tych klas urządzeń
- Zapobieganie instalacji urządzeń, które są zgodne z tymi identyfikatorami
- Zapobieganie instalacji urządzeń, które są zgodne z dowolnymi identyfikatorami wystąpień tych urządzeń

Jeśli ustawienie Zastosuj **porządek** oceny w warstwie dla opcji Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach jest włączone dla tego ustawienia zasad, wszystkie inne ustawienia zasad zapobiegające instalacji będą miały pierwszeństwo.

### <a name="apply-layered-order-of-evaluation-for-allow-and-prevent-device-installation-policies-across-all-device-match-criteria"></a>Stosowanie kolejności oceny w warstwie dla ustawień Zezwalaj i Uniemożliwiaj instalację urządzeń we wszystkich kryteriach dopasowania do urządzenia

To ustawienie zasad spowoduje zmianę kolejności oceny, w jakiej ustawienia zasad Zezwalaj i Nie zezwalaj są stosowane, gdy dla danego urządzenia ma zastosowanie więcej niż jedno ustawienie zasad instalacji. Włącz to ustawienie zasad, aby zapewnić, że nakładające się kryteria zgodne urządzenia będą stosowane na podstawie ustalonej hierarchii, w której bardziej szczegółowe kryteria dopasowania nie są stosowane w mniejszym stopniu. Hierarchiczna kolejność określania ustawień zasad określających kryteria dopasowania urządzenia jest następująca:

**Identyfikatory wystąpień urządzeń** \> **Identyfikatory urządzeń** \> **Klasa konfiguracji urządzenia** \> **Urządzenia przenośne**

#### <a name="device-instance-ids"></a>Identyfikatory wystąpień urządzeń

1. Zapobiegaj instalacji urządzeń przy użyciu sterowników, które są zgodne z identyfikatorami wystąpień tych urządzeń.
2. Zezwalaj na instalację urządzeń przy użyciu sterowników, które są zgodne z identyfikatorami wystąpień tych urządzeń.

#### <a name="device-ids"></a>Identyfikatory urządzeń

1. Zapobiegaj instalacji urządzeń, używając sterowników, które są zgodne z tymi identyfikatorami.
2. Zezwalaj na instalację urządzeń przy użyciu sterowników, które są zgodne z tymi identyfikatorami.

#### <a name="device-setup-class"></a>Klasa konfiguracji urządzenia

1. Zapobiegaj instalacji urządzeń, używając sterowników, które są zgodne z tymi klasami konfiguracji urządzenia.
2. Zezwalaj na instalację urządzeń, używając sterowników, które pasują do tych klas konfiguracji urządzenia.

#### <a name="removable-devices"></a>Urządzenia przenośne

Zapobieganie instalacji urządzeń wymiennych

> [!NOTE]
> To ustawienie zasad zapewnia bardziej szczegółową kontrolę niż ustawienie Zapobiegaj **instalacji urządzeń, które nie są opisane przez inne ustawienia** zasad. Jeśli te ustawienia zasad powodujące konflikty są włączone jednocześnie, ustawienie Zastosuj kolejność oceny w warstwie Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach jest włączone, a drugie ustawienie zasad jest ignorowane.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-ids"></a>Zapobieganie instalacji urządzeń, które są zgodne z dowolnymi identyfikatorami tych urządzeń

To ustawienie zasad umożliwia określenie listy identyfikatorów Plug and Play sprzętu i zgodnych identyfikatorów dla urządzeń, Windows których instalacja jest Windows. Domyślnie to ustawienie zasad ma pierwszeństwo przed innymi ustawieniami zasad, które umożliwiają Windows instalacji urządzenia.

> [!NOTE]
> Aby włączyć  ustawienie zasad Zezwalaj na instalację urządzeń zgodne z dowolnym z tych ustawień zasad identyfikatorów wystąpień urządzeń w celu zmiany ustawienia zasad na odpowiednie urządzenia, włącz  ustawienie Zastosuj kolejność oceny w warstwie dla opcji Zezwalaj i Zapobiegaj instalacji urządzeń na wszystkich urządzeniach z ustawieniem zasad kryteriów.

Włączenie tego ustawienia zasad uniemożliwi zainstalowanie Windows urządzenia, na którym jest wyświetlany identyfikator sprzętu lub zgodny identyfikator na tworzyć. Włączenie tego ustawienia zasad na serwerze pulpitu zdalnego ma wpływ na przekierowywanie określonych urządzeń z klienta pulpitu zdalnego do serwera pulpitu zdalnego.

Jeśli wyłączysz lub nie skonfigurujesz tego ustawienia zasad, urządzenia można instalować i aktualizować zgodnie z dozwolonymi lub zabronione innymi ustawieniami zasad.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Zapobieganie instalacji urządzeń, które są zgodne z dowolnymi identyfikatorami wystąpień tych urządzeń

To ustawienie zasad umożliwia określenie listy identyfikatorów wystąpień Plug and Play urządzeń dla urządzeń, Windows których instalacja nie będzie Windows. To ustawienie zasad ma pierwszeństwo przed innymi ustawieniami zasad, które umożliwiają Windows instalacji urządzenia.

Włączenie tego ustawienia zasad uniemożliwi Windows instalacji urządzenia, na którym identyfikator wystąpienia urządzenia jest wyświetlany na tworzyć listę. Włączenie tego ustawienia zasad na serwerze pulpitu zdalnego ma wpływ na przekierowywanie określonych urządzeń z klienta pulpitu zdalnego do serwera pulpitu zdalnego.

Jeśli wyłączysz lub nie skonfigurujesz tego ustawienia zasad, urządzenia można instalować i aktualizować zgodnie z dozwolonymi lub zabronione innymi ustawieniami zasad.

### <a name="prevent-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Zapobieganie instalacji urządzeń przy użyciu sterowników, które są zgodne z tymi klasami konfiguracji urządzenia

To ustawienie zasad umożliwia globalne określenie listy unikatowych identyfikatorów (GUID) klasy konfiguracji urządzenia dla pakietów sterowników, których zainstalowanie Windows jest niemożliwe. Domyślnie to ustawienie zasad ma pierwszeństwo przed innymi ustawieniami zasad, które umożliwiają Windows instalacji urządzenia.

> [!NOTE]
> Aby włączyć  ustawienia zasad Zezwalaj na instalację urządzeń zgodne z każdym z tych identyfikatorów urządzeń i Zezwalaj na instalację urządzeń, które są zgodne z dowolnymi ustawieniami zasad identyfikatorów wystąpienia tych urządzeń, aby zmienić to ustawienie zasad  dla odpowiednich urządzeń, włącz ustawienie Zastosuj kolejność oceny w warstwie dla opcji Zezwalaj i Zapobiegaj zasadom instalacji urządzeń na wszystkich urządzeniach zgodnie z ustawieniem zasad kryterium.

Włączenie tego ustawienia zasad uniemożliwi zainstalowanie Windows zaktualizowanie pakietów sterowników, których identyfikatory GUID zajęć konfigurowania urządzenia są wyświetlane na tworzyć listę. Włączenie tego ustawienia zasad na serwerze pulpitu zdalnego ma wpływ na przekierowywanie określonych urządzeń z klienta pulpitu zdalnego do serwera pulpitu zdalnego.

Jeśli wyłączysz lub nie skonfigurujesz tego ustawienia zasad, może Windows instalować i aktualizować urządzenia zgodnie z dozwolonymi lub zabronione przez inne ustawienia zasad.

### <a name="prevent-installation-of-removable-devices"></a>Zapobieganie instalacji urządzeń wymiennych

To ustawienie zasad pozwala zapobiec instalowaniu Windows wymiennych. Urządzenie jest traktowane jako wymienne, gdy sterownik urządzenia, do którego jest podłączone, wskazuje, że urządzenie jest wymienne. Na przykład sterownik koncentratora USB (Universal Serial Bus) jest zgłaszany jako wymienny przez sterowniki koncentratora USB, do którego jest podłączone. Domyślnie to ustawienie zasad ma pierwszeństwo przed innymi ustawieniami zasad, które umożliwiają Windows instalacji urządzenia.

> [!NOTE]
> Aby włączyć opcje Zezwalaj na instalację urządzeń przy użyciu sterowników, które pasują do tych klas konfiguracji **urządzeń, Zezwalaj** na instalację urządzeń, które pasują  do dowolnego z tych identyfikatorów **urządzeń, i** Zezwalaj na instalację urządzeń, które są zgodne z dowolnymi ustawieniami zasad wystąpienia tych urządzeń, aby  te ustawienia zasad były dodatkowe dla odpowiednich urządzeń, włącz ustawienie Zastosuj kolejność oceny w warstwie dla opcji Zezwalaj i Zapobiegaj zasadom instalacji urządzeń na wszystkich urządzeniach z ustawieniem zasad dopasowania do kryteriów.

Włączenie tego ustawienia zasad uniemożliwi zainstalowanie Windows wymiennych i zaktualizowanie sterowników istniejących urządzeń wymiennych będzie niemożliwe. Włączenie tego ustawienia zasad na serwerze pulpitu zdalnego ma wpływ na przekierowywanie urządzeń wymiennych z klienta pulpitu zdalnego do serwera pulpitu zdalnego.

Jeśli wyłączysz lub nie skonfigurujesz tego ustawienia zasad, program Windows i aktualizować pakiety sterowników dla urządzeń wymiennych, o ile dozwolone lub zabronione są inne ustawienia zasad.

## <a name="common-removable-storage-access-control-scenarios"></a>Typowe scenariusze Storage Access Control wymiennych

Aby ułatwić zapoznanie się z Ochrona punktu końcowego w usłudze Microsoft Defender wymiennymi Storage Access Control, możemy ci pomóc w kilku typowych scenariuszach.

### <a name="scenario-1-prevent-installation-of-all-usb-devices-while-allowing-an-installation-of-only-an-authorized-usb-thumb-drive"></a>Scenariusz 1. Uniemożliwianie instalowania wszystkich urządzeń USB, zezwalając jednocześnie na instalację tylko autoryzowanego usb usb-drive

W tym scenariuszu będą używane następujące zasady:

- Zapobiegaj instalacji urządzeń, używając sterowników, które są zgodne z tymi klasami konfiguracji urządzenia.
- Zastosuj kolejność oceny w warstwie dla ustawień Zezwalaj i Uniemożliwiaj instalację urządzeń we wszystkich kryteriach dopasowania urządzenia.
- Zezwalaj na instalację urządzeń, które są zgodne z dowolnym z tych identyfikatorów wystąpień lub Zezwalaj na instalację urządzeń, które są zgodne z dowolnym z tych identyfikatorów urządzeń.

#### <a name="deploying-and-managing-policy-via-intune"></a>Wdrażanie zasad i zarządzanie nimi za pośrednictwem Intune

Funkcja instalacji urządzenia umożliwia stosowanie zasad za pośrednictwem Intune urządzenia.

#### <a name="licensing"></a>Licencjonowanie

Przed rozpoczęciem instalacji urządzenia potwierdź swoją Microsoft 365 [urządzenia](https://www.microsoft.com/en-in/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Aby uzyskać dostęp do instalacji urządzenia i korzystać z niego, musisz mieć Microsoft 365 E3.

#### <a name="permission"></a>Uprawnienie

W przypadku wdrażania Intune w programie Intune konto musi mieć uprawnienia do tworzenia, edytowania, aktualizowania lub usuwania profilów konfiguracji urządzenia. Możesz utworzyć role niestandardowe lub użyć dowolnej z wbudowanych ról z tymi uprawnieniami:

- Rola Menedżera zasad i profilu
- Lub rola niestandardowa z włączonymi uprawnieniami Tworzenie/Edycja/Aktualizacja/Odczyt/Usuwanie/Wyświetlanie raportów dla profilów konfiguracji urządzenia
- Lub administrator globalny

#### <a name="deploying-policy"></a>Zasady wdrażania

W Microsoft Endpoint Manager [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)

1. Konfigurowanie **Zapobiegaj instalacji urządzeń za pomocą sterowników, które są zgodne z tymi klasami konfiguracji urządzenia**.

    - Otwórz okno Endpoint security > Attack surface reduction > Create Policy > Platform: Windows 10 (lub nowsza) & Profile: Device control.
    
      :::image type="content" source="../../media/devicepolicy-editprofile.png" alt-text="Strona Edytowanie profilu" lightbox="../../media/devicepolicy-editprofile.png":::
    
2. Podłącz urządzenie USB. Zostanie wyświetlony następujący komunikat o błędzie:

      :::image type="content" source="../../media/devicepolicy-errormsg.png" alt-text="Komunikat o błędzie" lightbox="../../media/devicepolicy-errormsg.png":::

3. Włącz **opcję Zastosuj kolejność oceny w warstwie dla ustawienia Zezwalaj i Uniemożliwiaj zasady instalacji urządzeń we wszystkich kryteriach dopasowania urządzeń**.

    - **obecnie obsługuje tylko interfejs OMA-URI**: Urządzenia > Profile konfiguracji > Utwórz profil > Platformę: Windows 10 (lub nowsza) & Profil: Niestandardowy
    
      :::image type="content" source="../../media/devicepolicy-editrow.png" alt-text="Strona Edytowanie wiersza" lightbox="../../media/devicepolicy-editrow.png":::

4. Włącz i dodaj dozwolony identyfikator wystąpienia USB — **zezwalaj na instalację urządzeń, które pasują do dowolnego z tych identyfikatorów**.

    - Aktualizowanie profilu sterowania urządzeniem w kroku 1
    
      :::image type="content" source="../../media/devicepolicy-devicecontrol.png" alt-text="Identyfikator na stronie Sterowanie urządzeniem" lightbox="../../media/devicepolicy-devicecontrol.png":::
       
    Dodawanie PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; Usb\USB20_HUB on above screen capture is because it's not enough to enable only a single hardware ID to enable a single USB thumb-drive. Należy się upewnić, że wszystkie urządzenia USB poprzedzające urządzenie docelowe także nie są blokowane (dozwolone). Możesz otworzyć Menedżer urządzeń i zmienić widok na "Urządzenia według połączeń", aby zobaczyć sposób instalacji urządzeń w drzewie sieciPnP. W naszym przypadku następujące urządzenia muszą być dozwolone, więc może być również dozwolony docelowy dysk USB: 

    Dodawanie PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; Usb\USB20_HUB on above screen capture is because it's not enough to enable only a single hardware ID to enable a single USB thumb-drive. Należy się upewnić, że wszystkie urządzenia USB poprzedzające urządzenie docelowe także nie są blokowane (dozwolone). Możesz otworzyć Menedżer urządzeń i zmienić widok na "Urządzenia według połączeń", aby zobaczyć sposób instalacji urządzeń w drzewie sieciPnP. W naszym przypadku następujące urządzenia muszą być dozwolone, więc może być również dozwolony docelowy dysk USB:

    - "Intel(R) USB 3.0 eXtensible Host Controller – 1.0 (Microsoft)" -> PCI\CC_0C03
    - "Koncentrator główny USB (USB 3.0)" -> USB\ROOT_HUB30
    - "Generic USB Hub" -> USB\USB20_HUB

    :::image type="content" source="../../media/devicepolicy-devicemgr.png" alt-text="Element menu Widok na Menedżer urządzeń widoku" lightbox="../../media/devicepolicy-devicemgr.png":::

    > [!NOTE]
    > Niektóre urządzenia w systemie mają kilka warstw łączności w celu zdefiniowania ich instalacji w systemie. Usb thumb drives are such devices. Dlatego podczas blokowania lub zezwalania na nie w systemie należy zrozumieć ścieżkę łączności dla każdego urządzenia. Istnieje kilka ogólnych identyfikatorów urządzeń, które są często używane w systemach i w takich przypadkach mogą stanowić dobry początek tworzenia listy "Zezwalaj". Poniżej przedstawiono przykład (nie zawsze jest to to samo w przypadku wszystkich kodów USB; musisz zrozumieć drzewo PnP urządzenia, którym chcesz zarządzać za pośrednictwem Menedżer urządzeń):
    >
    > PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST (dla kontrolerów hostów)/ USB\ROOT_HUB30; USB\ROOT_HUB20 (w przypadku głównych koncentratorów USB)/ USB\USB20_HUB (w przypadku ogólnych koncentratorów USB)/
    >
    > W szczególności w przypadku komputerów stacjonarnych, na powyższej liście należy wyświetlić listę wszystkich urządzeń USB, przy użyciu których są podłączone klawiatury i myszy. W przeciwnym razie użytkownik nie będzie mógł uzyskać dostępu do swojego komputera za pomocą urządzeń HID.
    >
    > Różni producenci komputerów czasami mają różne sposoby zagnieżdżania urządzeń USB w drzewie sieci PnP, ale na ogół tak się robi.

5. Podłącz ponownie dozwolone połączenie USB. Zobaczysz, że jest teraz dozwolone i dostępne.

    :::image type="content" source="../../media/devicepolicy-removedrive.png" alt-text="Strona Usuń szczegóły dysku" lightbox="../../media/devicepolicy-removedrive.png":::

#### <a name="deploying-and-managing-policy-via-group-policy"></a>Wdrażanie zasad i zarządzanie nimi za pośrednictwem zasady grupy

Funkcja instalacji urządzenia umożliwia stosowanie zasad za pośrednictwem zasady grupy.

#### <a name="licensing"></a>Licencjonowanie

Aby uzyskać dostęp do instalacji urządzenia i korzystać z niego, musisz mieć Windows E3.

#### <a name="deploying-policy"></a>Zasady wdrażania

Szczegóły wdrażania można znaleźć tutaj: Zarządzanie instalacją urządzeń za [zasady grupy (Windows 10) — Windows klienta](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Wyświetlanie danych kontrolek urządzeń wymiennych Storage Access Control w programie Ochrona punktu końcowego w usłudze Microsoft Defender

W [portalu Microsoft 365 zabezpieczeń jest](https://sip.security.microsoft.com/homepage) pokazana pamięć wymienna zablokowana przez instalację urządzenia sterującego urządzeniem. Aby uzyskać dostęp Microsoft 365 zabezpieczeń, musisz mieć następującą subskrypcję:

- Microsoft 365 raportów E5

```kusto
//events triggered by Device Installation policies
DeviceEvents
| where ActionType == "PnpDeviceBlocked" or ActionType == "PnpDeviceAllowed"
| extend parsed=parse_json(AdditionalFields)
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId)
| extend MediaDeviceId = tostring(parsed.MatchingDeviceId)
| project Timestamp , DeviceId, DeviceName, ActionType, MediaClassGuid, MediaDeviceId, MediaInstanceId, AdditionalFields
| order by Timestamp desc
```

:::image type="content" source="../../media/block-removable-storage2.png" alt-text="Blokowanie miejsca do magazynowania" lightbox="../../media/block-removable-storage2.png":::

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="how-can-i-know-whether-the-target-machine-gets-the-deployed-policy"></a>Jak ustalić, czy na komputerze docelowym są stosowane zasady wdrażane?

Możesz użyć następującego zapytania w celu uzyskania wersji klienta ochrony przed złośliwym kodem w portalu Microsoft 365 zabezpieczeń:

```kusto
//check whether the Device installation policy has been deployed to the target machine, event only when modification happens
DeviceRegistryEvents
| where RegistryKey contains "HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows\\DeviceInstall\\"
| order by Timestamp desc
```

## <a name="why-the-allow-policy-doesnt-work"></a>Dlaczego zasady Zezwalaj nie działają?

Nie wystarczy włączyć tylko jednego identyfikatora sprzętu, aby włączyć jeden dysk USB. Upewnij się, że wszystkie urządzenia USB poprzedzające urządzenie docelowe także nie są blokowane (dozwolone).

:::image type="content" source="../../media/devicemgrscrnshot.png" alt-text="Często zadawane pytania dotyczące instalacji urządzenia" lightbox="../../media/devicemgrscrnshot.png":::

