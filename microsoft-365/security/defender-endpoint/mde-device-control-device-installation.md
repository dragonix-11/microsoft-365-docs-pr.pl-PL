---
title: Ochrona punktu końcowego w usłudze Microsoft Defender instalacji urządzenia sterowania urządzeniami
description: W tym temacie przedstawiono omówienie instalacji urządzenia Ochrona punktu końcowego w usłudze Microsoft Defender Device Control
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
ms.openlocfilehash: dc05633d1badfc29b2179915ac6d318dd9523834
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666399"
---
# <a name="microsoft-defender-for-endpoint-device-control-device-installation"></a>Ochrona punktu końcowego w usłudze Microsoft Defender instalacji urządzenia sterowania urządzeniami

**Dotyczy**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

Ochrona punktu końcowego w usłudze Microsoft Defender Instalacja urządzenia sterowania urządzeniami umożliwia wykonanie następującego zadania:

- Uniemożliwiaj użytkownikom instalowanie określonych urządzeń.
- Zezwalaj użytkownikom na instalowanie określonych urządzeń, ale uniemożliwianie innym urządzeniom.

> [!NOTE]
> Aby znaleźć różnicę między instalacją urządzenia a kontrolą dostępu do magazynu wymiennego, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender Device Control Removable Storage Protection (Kontrola urządzenia wymienna Storage Protection](/microsoft-365/security/defender-endpoint/device-control-removable-storage-protection?view=o365-worldwide&preserve-view=true)).

|Uprawnień|Uprawnienia|
|---|---|
|Access|Instalacja urządzenia |
|Tryb akcji|Zezwalaj, zapobiegaj |
|Obsługa programu CSP|Tak|
|Obsługa obiektu zasad grupy|Tak|
|Obsługa oparta na użytkownikach|Nie|
|Obsługa oparta na maszynie|Tak|

## <a name="prepare-your-endpoints"></a>Przygotowywanie punktów końcowych

Wdrażanie instalacji urządzenia na Windows 10, urządzeniach Windows 11, Windows Server 2022.

## <a name="device-properties"></a>Właściwości urządzenia

Następujące właściwości urządzenia są obsługiwane przez obsługę instalacji urządzenia:

- Identyfikator urządzenia
- Identyfikator sprzętu
- Zgodny identyfikator
- Klasa urządzenia
- Typ urządzenia wymiennego: niektóre urządzenia można sklasyfikować jako urządzenie wymienne. Urządzenie jest uważane za wymienne, gdy sterownik urządzenia, z którym jest połączony, wskazuje, że urządzenie jest wymienne. Na przykład urządzenie USB jest zgłaszane jako wymienne przez sterowniki koncentratora USB, z którym urządzenie jest podłączone.
Aby uzyskać więcej informacji, zobacz [Device Installation in Windows (Instalacja urządzenia w Windows](/windows/client-management/manage-device-installation-with-group-policy)).

## <a name="policies"></a>Policies (zasady)

### <a name="allow-installation-of-devices-that-match-any-of-these-device-ids"></a>Zezwalaj na instalację urządzeń zgodnych z dowolnym z tych identyfikatorów urządzeń

To ustawienie zasad umożliwia określenie listy Plug and Play identyfikatorów sprzętu i zgodnych identyfikatorów dla urządzeń, które Windows mogą instalować. To ustawienie zasad jest przeznaczone do użycia tylko wtedy, gdy **włączono ustawienie zasad Zastosuj kolejność warstw ewaluacyjną dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich ustawieniach kryteriów dopasowania urządzenia** .

Jeśli to ustawienie zasad jest włączone razem z ustawieniem Zasad **zezwalania na instalację urządzeń w warstwie Zastosuj kolejność oceny dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich ustawieniach kryteriów dopasowania urządzenia**, Windows może instalować lub aktualizować dowolne urządzenie, którego identyfikator sprzętu Plug and Play lub zgodny identyfikator pojawi się na utworzonej liście, chyba że inne ustawienie zasad w tej samej lub wyższej warstwie w hierarchii wyraźnie uniemożliwia  tej instalacji, na przykład następujące ustawienia zasad:

- Zapobiegaj instalowaniu urządzeń zgodnych z tymi identyfikatorami urządzeń.
- Zapobiegaj instalacji urządzeń zgodnych z dowolnym z tych identyfikatorów wystąpienia urządzenia.

Jeśli ustawienie zasad **Zastosuj warstwowe kolejność oceny dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich ustawieniach zasad zgodności urządzeń** nie jest włączone z tym ustawieniem zasad, pierwszeństwo będą miały wszelkie inne ustawienia zasad uniemożliwiające instalację.

> [!NOTE]
> Ustawienie zasad **Zapobiegaj instalacji urządzeń, które nie jest opisane w innych ustawieniach zasad**, zostało zastąpione przez **kolejność oceny Zastosuj warstwowe dla zasad zezwalania na instalację urządzeń i uniemożliwiania jej dla wszystkich ustawień zasad zgodności urządzeń** dla obsługiwanych wersji Windows 10 docelowych i Windows 11. Zaleca się użycie warstwy **Zastosuj kolejność oceny dla zezwalania i zapobiegania zasad instalacji urządzeń we wszystkich urządzeniach dopasowania kryteriów** ustawienia, jeśli jest to możliwe.

### <a name="allow-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Zezwalaj na instalację urządzeń zgodnych z dowolnym z tych identyfikatorów wystąpienia urządzenia

To ustawienie zasad umożliwia określenie listy identyfikatorów wystąpień urządzeń Plug and Play dla urządzeń, które Windows mogą instalować. To ustawienie zasad jest przeznaczone do użycia tylko wtedy, gdy **włączono ustawienie zasad Zastosuj kolejność warstw ewaluacyjną dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich ustawieniach kryteriów dopasowania urządzenia** .

Jeśli to ustawienie zasad jest włączone razem z ustawieniem Zasad **zezwalania na instalację urządzeń w warstwie Zastosuj kolejność oceny dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich ustawieniach kryteriów dopasowania urządzenia**, Windows może instalować lub aktualizować dowolne urządzenie, którego identyfikator wystąpienia urządzenia Plug and Play jest wyświetlany na utworzonej liście, chyba że inne ustawienie zasad w tej samej lub wyższej warstwie w hierarchii wyraźnie uniemożliwia to  instalacja, na przykład następujące ustawienia zasad:

- Uniemożliwianie instalacji urządzeń zgodnych z dowolnym z tych identyfikatorów wystąpień urządzeń

Jeśli ustawienie zasad **Zastosuj warstwowe kolejność oceny dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich ustawieniach zasad zgodności urządzeń** nie jest włączone z tym ustawieniem zasad, pierwszeństwo będą miały wszelkie inne ustawienia zasad uniemożliwiające instalację.

### <a name="allow-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Zezwalaj na instalację urządzeń przy użyciu sterowników zgodnych z tymi klasami konfiguracji urządzeń

To ustawienie zasad umożliwia określenie listy globalnie unikatowych identyfikatorów (GUID) klasy konfiguracji urządzenia dla pakietów sterowników, które Windows mogą być instalowane. To ustawienie zasad jest przeznaczone do użycia tylko wtedy, gdy **włączono ustawienie zasad Zastosuj kolejność warstw ewaluacyjną dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich ustawieniach kryteriów dopasowania urządzenia** .

Po włączeniu tego ustawienia zasad wraz z **opcją Zastosuj kolejność warstw oceny dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich ustawieniach zasad dopasowania urządzenia** Windows może instalować lub aktualizować pakiety sterowników, których identyfikatory GUID klasy konfiguracji urządzenia są wyświetlane na utworzonej liście, chyba że inne ustawienie zasad w tej samej lub wyższej warstwie w hierarchii w szczególności uniemożliwia instalację,  takie jak następujące ustawienia zasad:

- Zapobieganie instalacji urządzeń dla tych klas urządzeń
- Uniemożliwianie instalacji urządzeń zgodnych z tymi identyfikatorami urządzeń
- Uniemożliwianie instalacji urządzeń zgodnych z dowolnym z tych identyfikatorów wystąpień urządzeń

Jeśli ustawienie zasad **Zastosuj warstwowe kolejność oceny dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich ustawieniach zasad zgodności urządzeń** nie jest włączone z tym ustawieniem zasad, pierwszeństwo będą miały wszelkie inne ustawienia zasad uniemożliwiające instalację.

### <a name="apply-layered-order-of-evaluation-for-allow-and-prevent-device-installation-policies-across-all-device-match-criteria"></a>Stosowanie warstwowej kolejności oceny dla zasad zezwalania na instalację urządzeń i zapobiegania jej we wszystkich kryteriach dopasowania urządzenia

To ustawienie zasad zmieni kolejność oceny, w której są stosowane ustawienia zasad Zezwalaj i Zapobiegaj, gdy dla danego urządzenia ma zastosowanie więcej niż jedno ustawienie zasad instalacji. Włącz to ustawienie zasad, aby upewnić się, że nakładające się kryteria dopasowania urządzenia są stosowane w oparciu o ustaloną hierarchię, w której bardziej szczegółowe kryteria dopasowania zastępuje mniej specyficzne kryteria dopasowania. Hierarchiczna kolejność oceny ustawień zasad określających kryteria dopasowania urządzenia jest następująca:

**Identyfikatory wystąpień** \> urządzeń **Identyfikatory** \> urządzeń Klasa \> **konfiguracji urządzenia** **Urządzenia wymienne**

#### <a name="device-instance-ids"></a>Identyfikatory wystąpień urządzeń

1. Zapobiegaj instalowaniu urządzeń przy użyciu sterowników zgodnych z tymi identyfikatorami wystąpień urządzeń.
2. Zezwalaj na instalację urządzeń przy użyciu sterowników zgodnych z tymi identyfikatorami wystąpień urządzeń.

#### <a name="device-ids"></a>Identyfikatory urządzeń

1. Zapobiegaj instalowaniu urządzeń przy użyciu sterowników zgodnych z tymi identyfikatorami urządzeń.
2. Zezwalaj na instalację urządzeń przy użyciu sterowników zgodnych z tymi identyfikatorami urządzeń.

#### <a name="device-setup-class"></a>Klasa konfiguracji urządzenia

1. Zapobiegaj instalowaniu urządzeń przy użyciu sterowników zgodnych z tymi klasami konfiguracji urządzeń.
2. Zezwalaj na instalację urządzeń przy użyciu sterowników zgodnych z tymi klasami konfiguracji urządzeń.

#### <a name="removable-devices"></a>Urządzenia wymienne

Zapobieganie instalacji urządzeń wymiennych

> [!NOTE]
> To ustawienie zasad zapewnia bardziej szczegółową kontrolę niż ustawienie zasad **Zapobiegaj instalacji urządzeń, które nie zostało opisane przez inne ustawienia zasad** . Jeśli te ustawienia zasad powodujących konflikt są włączone w tym samym czasie, ustawienie zasad **Zezwalaj na instalację urządzeń i Zapobiegaj dla zasad zezwalania na instalację urządzeń w ramach wszystkich kryteriów dopasowania urządzenia** zostanie włączone, a inne ustawienie zasad zostanie zignorowane.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-ids"></a>Uniemożliwianie instalacji urządzeń zgodnych z dowolnym z tych identyfikatorów urządzeń

To ustawienie zasad umożliwia określenie listy Plug and Play identyfikatorów sprzętu i zgodnych identyfikatorów dla urządzeń, które Windows nie mogą być instalowane. Domyślnie to ustawienie zasad ma pierwszeństwo przed każdym innym ustawieniem zasad, które umożliwia Windows zainstalowanie urządzenia.

> [!NOTE]
> Aby włączyć ustawienie zasad **Zezwalaj na instalację urządzeń zgodnych z dowolnym z tych ustawień zasad identyfikatorów wystąpienia urządzenia** , aby zastąpić to ustawienie zasad dla odpowiednich urządzeń, włącz ustawienie zasad **Zastosuj warstwowe kolejność oceny dla zasad zezwalania i zapobiegania instalacji urządzeń na wszystkich urządzeniach zgodnych z kryteriami** .

Jeśli to ustawienie zasad zostanie włączone, Windows nie będzie mógł zainstalować urządzenia, którego identyfikator sprzętu lub zgodny identyfikator pojawi się na utworzonej liście. Jeśli to ustawienie zasad zostanie włączone na serwerze pulpitu zdalnego, ustawienie zasad ma wpływ na przekierowanie określonych urządzeń z klienta pulpitu zdalnego do serwera pulpitu zdalnego.

Jeśli to ustawienie zasad zostanie wyłączone lub nie zostanie skonfigurowane, urządzenia mogą być instalowane i aktualizowane zgodnie z dozwolonym lub uniemożliwianym przez inne ustawienia zasad.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Uniemożliwianie instalacji urządzeń zgodnych z dowolnym z tych identyfikatorów wystąpień urządzeń

To ustawienie zasad umożliwia określenie listy identyfikatorów wystąpień urządzeń Plug and Play dla urządzeń, które Windows nie mogą instalować. To ustawienie zasad ma pierwszeństwo przed innymi ustawieniami zasad, które umożliwiają Windows zainstalowanie urządzenia.

Jeśli to ustawienie zasad zostanie włączone, Windows nie będzie mogła zainstalować urządzenia, którego identyfikator wystąpienia urządzenia zostanie wyświetlony na utworzonej liście. Jeśli to ustawienie zasad zostanie włączone na serwerze pulpitu zdalnego, ustawienie zasad ma wpływ na przekierowanie określonych urządzeń z klienta pulpitu zdalnego do serwera pulpitu zdalnego.

Jeśli to ustawienie zasad zostanie wyłączone lub nie zostanie skonfigurowane, urządzenia mogą być instalowane i aktualizowane zgodnie z dozwolonym lub uniemożliwianym przez inne ustawienia zasad.

### <a name="prevent-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Zapobieganie instalowaniu urządzeń przy użyciu sterowników zgodnych z tymi klasami konfiguracji urządzeń

To ustawienie zasad umożliwia określenie listy unikatowych identyfikatorów globalnie unikatowych (GUID) klasy konfiguracji urządzenia dla pakietów sterowników, które Windows nie mogą być instalowane. Domyślnie to ustawienie zasad ma pierwszeństwo przed każdym innym ustawieniem zasad, które umożliwia Windows zainstalowanie urządzenia.

> [!NOTE]
> Aby włączyć **opcję Zezwalaj na instalację urządzeń zgodnych z dowolnym z tych identyfikatorów urządzeń** i **Zezwalaj na instalację urządzeń zgodnych z dowolnym z tych ustawień zasad identyfikatorów wystąpień urządzeń** , aby zastąpić to ustawienie zasad dla odpowiednich urządzeń, włącz ustawienie zasad **Zezwalaj na instalację urządzeń w warstwie Zastosuj warstwę dla zasad zezwalania na instalację urządzeń i zapobiegania ich instalowaniu we wszystkich urządzeniach zgodnych z kryteriami** .

Jeśli to ustawienie zasad zostanie włączone, Windows nie będzie można instalować ani aktualizować pakietów sterowników, których identyfikatory GUID klasy konfiguracji urządzenia są wyświetlane na utworzonej liście. Jeśli to ustawienie zasad zostanie włączone na serwerze pulpitu zdalnego, ustawienie zasad ma wpływ na przekierowanie określonych urządzeń z klienta pulpitu zdalnego do serwera pulpitu zdalnego.

Jeśli to ustawienie zasad zostanie wyłączone lub nie zostanie skonfigurowane, Windows może instalować i aktualizować urządzenia zgodnie z dozwolonym lub uniemożliwiającym użyciem innych ustawień zasad.

### <a name="prevent-installation-of-removable-devices"></a>Zapobieganie instalacji urządzeń wymiennych

To ustawienie zasad umożliwia zapobieganie instalowaniu urządzeń wymiennych przez Windows. Urządzenie jest uważane za wymienne, gdy sterownik urządzenia, z którym jest połączony, wskazuje, że urządzenie jest wymienne. Na przykład urządzenie uniwersalnej magistrali szeregowej (USB) jest zgłaszane jako wymienne przez sterowniki koncentratora USB, z którym urządzenie jest połączone. Domyślnie to ustawienie zasad ma pierwszeństwo przed każdym innym ustawieniem zasad, które umożliwia Windows zainstalowanie urządzenia.

> [!NOTE]
> Aby włączyć **opcję Zezwalaj na instalację urządzeń przy użyciu sterowników zgodnych z tymi klasami konfiguracji urządzeń**, **zezwalaj na instalację urządzeń zgodnych z dowolnymi z tych identyfikatorów** urządzeń, aby zastąpić to ustawienie zasad dla odpowiednich urządzeń, włącz ustawienie zasad **Zastosuj warstwowe kolejność oceny dla ustawienia zasad Zezwalaj na instalację urządzeń i Uniemożliwiaj ich instalowanie we wszystkich ustawieniach kryteriów zgodności urządzeń**.

Jeśli to ustawienie zasad zostanie włączone, Windows nie będzie mogła instalować urządzeń wymiennych, a istniejące urządzenia wymienne nie mogą mieć zaktualizowanych sterowników. Jeśli to ustawienie zasad zostanie włączone na serwerze pulpitu zdalnego, ustawienie zasad wpływa na przekierowanie urządzeń wymiennych z klienta pulpitu zdalnego do serwera pulpitu zdalnego.

Jeśli to ustawienie zasad zostanie wyłączone lub nie zostanie skonfigurowane, Windows może instalować i aktualizować pakiety sterowników dla urządzeń wymiennych zgodnie z innymi ustawieniami zasad.

## <a name="common-removable-storage-access-control-scenarios"></a>Typowe scenariusze Storage Access Control wymiennych

Aby ułatwić zapoznanie się z Ochrona punktu końcowego w usłudze Microsoft Defender Storage Access Control wymiennych, przygotowaliśmy kilka typowych scenariuszy, które należy wykonać.

### <a name="scenario-1-prevent-installation-of-all-usb-devices-while-allowing-an-installation-of-only-an-authorized-usb-thumb-drive"></a>Scenariusz 1. Zapobieganie instalacji wszystkich urządzeń USB przy jednoczesnym umożliwieniu instalacji tylko autoryzowanego dysku USB

W tym scenariuszu zostaną użyte następujące zasady:

- Zapobiegaj instalowaniu urządzeń przy użyciu sterowników zgodnych z tymi klasami konfiguracji urządzeń.
- Zastosuj kolejność oceny warstwowej dla zasad zezwalania na instalację urządzeń i zapobiegania jej we wszystkich kryteriach dopasowania urządzenia.
- Zezwalaj na instalację urządzeń zgodnych z dowolnym z tych identyfikatorów wystąpienia urządzenia lub zezwalaj na instalację urządzeń zgodnych z dowolnym z tych identyfikatorów urządzeń.

#### <a name="deploying-and-managing-policy-via-intune"></a>Wdrażanie zasad i zarządzanie nimi za pośrednictwem Intune

Funkcja instalacji urządzenia umożliwia stosowanie zasad za pośrednictwem Intune do urządzenia.

#### <a name="licensing"></a>Licencjonowanie

Przed rozpoczęciem instalacji urządzenia należy potwierdzić [subskrypcję Microsoft 365](https://www.microsoft.com/en-in/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Aby uzyskać dostęp do instalacji urządzenia i korzystać z niej, musisz mieć Microsoft 365 E3.

#### <a name="permission"></a>Uprawnienia

W przypadku wdrażania zasad w Intune konto musi mieć uprawnienia do tworzenia, edytowania, aktualizowania lub usuwania profilów konfiguracji urządzeń. Możesz utworzyć role niestandardowe lub użyć dowolnej z wbudowanych ról z następującymi uprawnieniami:

- Rola Menedżera zasad i profilu
- Lub rola niestandardowa z włączonymi uprawnieniami Utwórz/Edytuj/Aktualizuj/Odczyt/Usuń/Wyświetl raporty dla profilów konfiguracji urządzenia
- Lub administrator globalny

#### <a name="deploying-policy"></a>Wdrażanie zasad

W Microsoft Endpoint Manager [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)

1. **Skonfiguruj opcję Zapobiegaj instalacji urządzeń przy użyciu sterowników zgodnych z tymi klasami konfiguracji urządzeń**.

    - Otwórz obszar zabezpieczeń punktu końcowego > Zmniejszanie obszaru ataków > Tworzenie platformy > zasad: Windows 10 (i nowsze) & profil: kontrola urządzenia.

      :::image type="content" source="../../media/devicepolicy-editprofile.png" alt-text="Strona Edytuj profil" lightbox="../../media/devicepolicy-editprofile.png":::

2. Podłącz usb, urządzenie, a zobaczysz następujący komunikat o błędzie:

      :::image type="content" source="../../media/devicepolicy-errormsg.png" alt-text="Komunikat o błędzie" lightbox="../../media/devicepolicy-errormsg.png":::

3. Włącz **opcję Zastosuj warstwowe kolejność oceny dla zasad zezwalania i zapobiegania instalacji urządzeń we wszystkich kryteriach dopasowania urządzenia**.

    - **Na razie obsługują tylko identyfikator OMA-URI**: Urządzenia > profile konfiguracji > Tworzenie profilu > Platform: Windows 10 (i nowszych) profil &: niestandardowy

      :::image type="content" source="../../media/devicepolicy-editrow.png" alt-text="Strona Edytowanie wiersza" lightbox="../../media/devicepolicy-editrow.png":::

4. Włącz i dodaj dozwolony identyfikator wystąpienia USB — **zezwalaj na instalację urządzeń zgodnych z dowolnym z tych identyfikatorów urządzeń**.

    - Aktualizowanie profilu sterowania urządzeniami w kroku 1

      :::image type="content" source="../../media/devicepolicy-devicecontrol.png" alt-text="Identyfikator na stronie Kontrola urządzenia" lightbox="../../media/devicepolicy-devicecontrol.png":::

    Dodawanie interfejsu PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; USB\USB20_HUB na powyższym przechwytywaniu ekranu jest spowodowane tym, że nie wystarczy włączyć tylko jednego identyfikatora sprzętu, aby włączyć pojedynczy dysk usb. Musisz upewnić się, że wszystkie urządzenia USB poprzedzające urządzenie docelowe również nie są blokowane (dozwolone). Możesz otworzyć Menedżer urządzeń i zmienić widok na "Urządzenia według połączeń", aby zobaczyć sposób instalowania urządzeń w drzewie PnP. W naszym przypadku należy zezwolić na następujące urządzenia, aby można było również zezwolić na docelowy dysk USB:

    Dodawanie interfejsu PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; USB\USB20_HUB na powyższym przechwytywaniu ekranu jest spowodowane tym, że nie wystarczy włączyć tylko jednego identyfikatora sprzętu, aby włączyć pojedynczy dysk usb. Musisz upewnić się, że wszystkie urządzenia USB poprzedzające urządzenie docelowe również nie są blokowane (dozwolone). Możesz otworzyć Menedżer urządzeń i zmienić widok na "Urządzenia według połączeń", aby zobaczyć sposób instalowania urządzeń w drzewie PnP. W naszym przypadku należy zezwolić na następujące urządzenia, aby można było również zezwolić na docelowy dysk USB:

    - "Intel(R) USB 3.0 eXtensible Host Controller – 1.0 (Microsoft)" -> PCI\CC_0C03
    - "KONCENTRATOR USB (USB 3.0)" -> USB\ROOT_HUB30
    - "Generic USB Hub" -> USB\USB20_HUB

    :::image type="content" source="../../media/devicepolicy-devicemgr.png" alt-text="Element menu Widok na stronie Menedżer urządzeń" lightbox="../../media/devicepolicy-devicemgr.png":::

    > [!NOTE]
    > Niektóre urządzenia w systemie mają kilka warstw łączności, aby zdefiniować instalację w systemie. Takie urządzenia są dyskami usb. W związku z tym w przypadku blokowania lub zezwalania na nie w systemie ważne jest zrozumienie ścieżki łączności dla każdego urządzenia. Istnieje kilka ogólnych identyfikatorów urządzeń, które są często używane w systemach i mogą zapewnić dobry początek tworzenia "listy dozwolonych" w takich przypadkach. Poniżej przedstawiono jeden przykład (nie zawsze jest taki sam dla wszystkich usb; musisz zrozumieć drzewo PnP urządzenia, które chcesz zarządzać za pośrednictwem Menedżer urządzeń):
    >
    > PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST (dla kontrolerów hostów)/ USB\ROOT_HUB30; USB\ROOT_HUB20 (dla koncentratorów głównych USB)/ USB\USB20_HUB (dla ogólnych koncentratorów USB)/
    >
    > W szczególności w przypadku komputerów stacjonarnych należy wymienić wszystkie urządzenia USB, za pomocą których klawiatury i myszy są połączone na powyższej liście. Nie można tego zrobić, może zablokować użytkownikowi dostęp do swojej maszyny za pośrednictwem urządzeń HID.
    >
    > Różni producenci komputerów pc czasami mają różne sposoby zagnieżdżania urządzeń USB w drzewie PnP, ale ogólnie tak jest.

5. Ponownie podłącz dozwolone usb. Zobaczysz, że jest ona teraz dozwolona i dostępna.

    :::image type="content" source="../../media/devicepolicy-removedrive.png" alt-text="Strona Remove drive details (Usuwanie dysku)" lightbox="../../media/devicepolicy-removedrive.png":::

#### <a name="deploying-and-managing-policy-via-group-policy"></a>Wdrażanie zasad i zarządzanie nimi za pośrednictwem zasady grupy

Funkcja instalacji urządzenia umożliwia stosowanie zasad za pośrednictwem zasady grupy.

#### <a name="licensing"></a>Licencjonowanie

Aby uzyskać dostęp do instalacji urządzenia i korzystać z niej, musisz mieć Windows E3.

#### <a name="deploying-policy"></a>Wdrażanie zasad

Szczegóły wdrożenia można znaleźć tutaj: [Zarządzanie instalacją urządzenia za pomocą zasady grupy (Windows 10) — klient Windows](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Wyświetlanie danych Storage Access Control wymiennych kontrolek urządzenia w Ochrona punktu końcowego w usłudze Microsoft Defender

W portalu [zabezpieczeń Microsoft 365](https://sip.security.microsoft.com/homepage) jest wyświetlany magazyn wymienny zablokowany przez instalację urządzenia sterowania urządzeniami. Aby uzyskać dostęp do zabezpieczeń Microsoft 365, musisz mieć następującą subskrypcję:

- Microsoft 365 raportowania E5

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

:::image type="content" source="../../media/block-removable-storage2.png" alt-text="Magazyn blokowy" lightbox="../../media/block-removable-storage2.png":::

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="how-can-i-know-whether-the-target-machine-gets-the-deployed-policy"></a>Skąd mogę wiedzieć, czy maszyna docelowa pobiera wdrożone zasady?

Następujące zapytanie umożliwia pobranie wersji klienta ochrony przed złośliwym kodem w portalu zabezpieczeń Microsoft 365:

```kusto
//check whether the Device installation policy has been deployed to the target machine, event only when modification happens
DeviceRegistryEvents
| where RegistryKey contains "HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows\\DeviceInstall\\"
| order by Timestamp desc
```

## <a name="why-the-allow-policy-doesnt-work"></a>Dlaczego zasady Zezwalaj nie działają?

Nie wystarczy włączyć tylko jeden identyfikator sprzętu, aby włączyć pojedynczy dysk USB. Upewnij się, że wszystkie urządzenia USB poprzedzające urządzenie docelowe również nie są blokowane (dozwolone).

:::image type="content" source="../../media/devicemgrscrnshot.png" alt-text="Często zadawane pytania dotyczące instalacji urządzenia" lightbox="../../media/devicemgrscrnshot.png":::
