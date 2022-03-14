---
title: Program Microsoft Defender for Endpoint Device Control Removable Storage Access Control, nośnik magazynu wymiennych
description: A walk-through about Microsoft Defender for Endpoint
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.date: 03/09/2022
ms.openlocfilehash: f696cd3631573bdb2206c665340f35601e4624ac
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2022
ms.locfileid: "63468988"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Program Microsoft Defender for Endpoint Device Control Removable Storage Access Control

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Zarządzanie zasady grupy i OMA-URI Intune/zarządzanie zasadami niestandardowymi tego produktu są teraz ogólnie dostępne (4.18.2106): Zobacz blog poświęcony technologii Community: Chronienie wymiennych magazynów i drukarki za pomocą programu [Microsoft Defender for Endpoint](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).


Program Microsoft Defender for Endpoint Device Control Wymienny Storage kontroli dostępu umożliwia następujące zadanie:

- inspekcja, zezwalanie na odczytywanie, pisanie lub wykonywanie dostępu do magazynu wymiennych z wyłączeniem lub bez tego

|Uprawnienie|Uprawnienie|
|---|---|
|Access|Odczyt, pisanie, wykonywanie|
|Tryb akcji|Inspekcja, Zezwalaj, Zapobieganie|
|Pomoc techniczna CSP|Tak|
|Obsługa zasad grupy|Tak|
|Pomoc techniczna oparta na użytkownikach|Tak|
|Obsługa maszynowa|Tak|

|Funkcja|Opis|Wdrażanie za pośrednictwem usługi Intune|Wdrażanie za pośrednictwem zasady grupy|
|---|---|---|---|
|Tworzenie grupy multimediów wymiennych|Umożliwia utworzenie grupy nośników wymiennych wielokrotnego użytku|Krok 1 i krok 3 w sekcji [Wdrażanie zasad za pośrednictwem usługi OMA-URI](#deploying-policy-via-oma-uri) | Krok 1 w sekcji [Wdrażanie zasad za pośrednictwem usługi zasady grupy](#deploying-policy-via-group-policy)|
|Tworzenie zasad|Umożliwia tworzenie zasad wymuszania poszczególnych grup nośników wymiennych|Kroki 2 i 3 w sekcji [Wdrażanie zasad za pośrednictwem usługi OMA-URI](#deploying-policy-via-oma-uri) | Krok 2 w sekcji [Wdrażanie zasad za pośrednictwem usługi zasady grupy](#deploying-policy-via-group-policy) |
|Domyślne wymusze|Umożliwia ustawienie dostępu domyślnego (odmów lub zezwalania) na nośnik wymienny, jeśli nie ma żadnych zasad|Krok 4 w sekcji [Wdrażanie zasad za pośrednictwem usługi OMA-URI](#deploying-policy-via-oma-uri) | Krok 3 w sekcji [Wdrażanie zasad za pośrednictwem zasady grupy](#deploying-policy-via-group-policy) |
|Włączanie lub wyłączanie wymiennych Storage Access Control|Jeśli ustawisz opcję Wyłącz, zasady Kontrola dostępu wymiennych Storage wymiennych na tym komputerze| Krok 5 w sekcji [Wdrażanie zasad za pośrednictwem usługi OMA-URI](#deploying-policy-via-oma-uri) | Krok 4 w sekcji [Wdrażanie zasad za pośrednictwem zasady grupy](#deploying-policy-via-group-policy) |
|Przechwytywanie informacji o pliku|Umożliwia tworzenie zasad umożliwiających przechwytywanie informacji z pliku w przypadku uzyskiwania dostępu do zapisu| Krok 2 i 6 w sekcji [Wdrażanie zasad za pośrednictwem usługi OMA-URI](#deploying-policy-via-oma-uri) | Krok 2 i 5 w sekcji [Wdrażanie zasad za pośrednictwem zasady grupy](#deploying-policy-via-group-policy) |

## <a name="prepare-your-endpoints"></a>Przygotowywanie punktów końcowych

Wdrażanie kontrolki programu Access Storage wymiennych na Windows 10 i urządzeniach z systemem Windows 11, które mają klienta ochrony przed złośliwym oprogramowaniem w wersji **4.18.2103.3 lub nowszej**.

- **4.18.2104** lub nowsza: Dodawanie numeru seryjnego, VID_PID, obsługa zasad GPO opartych na programie FilePath, ComputerSid

- **4.18.2105** lub nowsza: Dodawanie obsługi symboli wieloznacznych dla hardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId, kombinacji określonego użytkownika na konkretnym komputerze, odłączanego dysku SSD (San Jakas Extreme SSD)/USB Attached OWĄ (UAS)

- **4.18.2107** lub nowsza: Dodaj obsługę usługi Windows Portable Device (WPD) (dla urządzeń przenośnych, takich jak tablety), dodaj AccountName do wyszukiwania [zaawansowanego](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

- **4.18.2111** lub nowsza: Dodawanie "Włącz lub wyłącz kontrolkę dostępu wymiennych Storage Access", "Domyślne wymuszanie", czas aktualizacji zasad komputera klienckiego za pomocą programu PowerShell, informacje o pliku

- **4.18.2201** lub nowszy: Obsługa kopii pliku zapisanej w dozwolonym magazynie za pośrednictwem usługi OMA-URI

:::image type="content" source="images/powershell.png" alt-text="Interfejs programu PowerShell.":::

> [!NOTE]
> Żaden z Zabezpieczenia Windows wymiennych nie musi być aktywny, ponieważ można uruchamiać kontrolkę wymienną Storage Access niezależnie od Zabezpieczenia Windows stanu.

## <a name="policy-properties"></a>Właściwości zasad

Aby utworzyć grupę magazynów wymiennych, możesz użyć następujących właściwości:

> [!NOTE]
> Komentarze korzystające z `<!-- COMMENT -->` notacji komentarzy XML mogą być używane w plikach XML reguł i grup, ale muszą znajdować się wewnątrz pierwszego tagu XML, a nie pierwszego wiersza pliku XML.

### <a name="removable-storage-group"></a>Grupa wymiennych Storage wymiennych

|Nazwa właściwości|Opis|Opcje|
|---|---|---|
|**GroupId**|Identyfikator GUID (unikatowy identyfikator) reprezentuje grupę i będzie używany w zasadach.||
|**DescriptorIdList**|W tym celu należy wyświetlić listę właściwości urządzeń, które mają zostać zasłaniane w grupie. Aby uzyskać szczegółowe informacje na temat poszczególnych właściwości [urządzenia, zobacz Właściwości](device-control-removable-storage-protection.md) urządzenia. We wszystkich właściwościach jest wielkość liter. |**PrimaryId**: `RemovableMediaDevices`, , `CdRomDevices``WpdDevices`<p>**BusId**: Na przykład USB, ZIM<p>**DeviceId**<p>**HardwareId**<p>**InstancePathId**: InstancePathId to ciąg jednoznacznie identyfikujący urządzenie w systemie, na przykład `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`. Numer na końcu (na przykład &0) reprezentuje dostępne miejsce i może się zmienić z urządzenia na urządzenie. Aby uzyskać najlepsze wyniki, użyj symbolu wieloznacznego na końcu. Na przykład `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**PRZEC**<p>**Identyfikator PID**<p>**VID_PID**<p>`0751_55E0`: dopasuj dokładnie tę parę GDY/PID<p>`_55E0`: dopasuj dowolny nośnik do PID=55E0 <p>`0751_`: dopasuj dowolny nośnik do dowolnej chwili z programem ICHN=0751|
|**MatchType**|Gdy w urządzeniu jest używanych wiele `DescriptorIDList`właściwości, typ MatchType definiuje relację.|**MatchAll**: Wszystkie `DescriptorIdList` atrybuty w relacji będzie oraz. Jeśli na przykład administrator `DeviceID` `InstancePathID`umieści i , dla każdego podłączonego usb, system sprawdzi, czy port USB spełnia obie wartości. <p> **MatchAny**: Atrybuty w obszarze DescriptorIdList to **Lub** relacja. Jeśli na przykład administrator `DeviceID` `InstancePathID`umieści w pamięci i , dla każdego podłączonego usb system będzie wymuszał, o ile usb ma identyczny **deviceID** lub **wartość InstanceID** . |

### <a name="access-control-policy"></a>Zasady kontroli dostępu

| Nazwa właściwości | Opis | Opcje |
|---|---|---|
| **PolicyRuleId** | Unikatowy identyfikator GUID reprezentuje zasady i będzie używany w raportowaniu i rozwiązywaniu problemów. | |
| **IncludedIdList** | Grupy, do których zostaną zastosowane zasady. Jeśli dodano wiele grup, zasady zostaną zastosowane do wszystkich multimediów we wszystkich tych grupach.|W tym wystąpieniu należy użyć identyfikatora grupy/identyfikatora GUID. <p> W poniższym przykładzie pokazano użycie groupID: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | Grupy, do których zasady nie zostaną zastosowane. | W tym wystąpieniu należy użyć identyfikatora grupy/identyfikatora GUID. |
| **Identyfikator wpisu** | Jedna zasada może mieć wiele wpisów. Każda pozycja z unikatowym identyfikatorem GUID informuje o jednym ograniczeniu w kontrolce urządzenia.| |
| **Type** | Definiuje akcję dla grup magazynu wymiennych na liście IncludedIDList. <p>Wymuszanie: Zezwalaj lub Odmów <p>Inspekcja: InspekcjaWszystkie lub Odrzucone inspekcja<p> | Zezwalaj<p>Odmów <p>AuditAllowed: Definiuje powiadomienie i zdarzenie, gdy dostęp jest dozwolony <p>Odmowa inspekcji: definiuje powiadomienie i zdarzenie, gdy dostęp zostanie odrzucony. musi współpracować z **wpisem Deny (** Odmów).<p> Jeśli istnieją typy konfliktów dla tego samego nośnika, system zastosuje pierwszy z nich w zasadach. Przykładem typu konfliktu jest Allow ( **Zezwalaj) i** **Deny (Odmów**). |
| **Sid** | Lokalny użytkownik Sid lub grupa sid użytkownika lub sid obiektu AD definiuje, czy te zasady mają być stosowane do określonego użytkownika lub grupy użytkowników. jedna pozycja może mieć maksymalnie jeden identyfikator Sid i wpis bez żadnego identyfikatora Sid oznacza zastosowanie zasad za pośrednictwem komputera. |  |
| **ComputerSid** | Na komputerze lokalnym Sid lub computer Sid grupa lub Sid obiektu AD, definiuje, czy te zasady mają być stosowane do określonego komputera lub grupy komputerów. jedna pozycja może mieć maksymalnie jeden wartość ComputerSid, a wpis bez użycia dowolnego computerSid oznacza zastosowanie zasad na komputerze. Jeśli chcesz zastosować wpis do określonego użytkownika i konkretnego komputera, dodaj do tego samego wpisu zarówno identyfikator Sid, jak i ComputerSid. |  |
| **Opcje** | Określa, czy powiadomienia mają być wyświetlane |**Gdy jest zaznaczona opcja Wpisz zezwalaj**: <p>0: nic<p>4. Wyłącz **ustawienie AuditAllowed i** **AuditDenied** dla tego wpisu. Nawet jeśli **dzieje** się zezwalanie i skonfigurowano ustawienie AuditAllowed, system nie wysyła zdarzeń. <p>8. Przechwyć informacje o pliku i mieć kopię pliku jako dowód na dostęp do zapisu. <p>16: przechwytywanie informacji o pliku na temat dostępu do zapisu. <p>**Gdy wybrano opcję Wpisz odmów**: <p>0: nic<p>4. Wyłącz **odmowę inspekcji** dla tego wpisu. Nawet jeśli **dzieje się** blokowanie i jest skonfigurowane ustawienie Odrzucona inspekcja, system nie wyświetla powiadomień. <p>**Gdy jest **zaznaczona opcja Wpisz inspekcjęWszystkie****: <p>0: nic <p>1: nic <p>2: wysyłanie zdarzenia<p>3: wysyłanie zdarzenia <p> **Gdy jest **zaznaczona opcja Typ odrzuconej** inspekcji**: <p>0: nic <p>1: pokaż powiadomienie <p>2: wysyłanie zdarzenia<p>3. Wyświetlanie powiadomienia i wysyłanie zdarzenia |
|AccessMask|Definiuje dostęp. | **Dostęp na poziomie dysku**: <p>1: Odczyt <p>2. Pisanie <p>4. Wykonywanie <p>**Dostęp na poziomie systemu plików**: <p>8: Odczyt w systemie plików <p>16: Pisanie w systemie plików <p>32: File system Execute <p><p>Możesz mieć wiele dostępu, wykonując operację binarną LUB, na przykład AccessMask for Read and Write and Execute będzie mieć 7; AccessMask for Read and Write will be 3.|

## <a name="common-removable-storage-access-control-scenarios"></a>Typowe scenariusze sterowania kontrolkami Storage wymiennymi w programie Access

Aby ułatwić Ci zapoznanie się z programem Microsoft Defender for Endpoint Removable Storage Access Control, firma Microsoft umieściła kilka typowych scenariuszy do obserwowania.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scenariusz 1. Uniemożliwianie pisania i wykonywania dostępu do wszystkich, ale ze względu na zezwalanie na określone zatwierdzone usb

1. Tworzenie grup

    1. Grupa 1: Dowolne nośniki wymiennych i dyski CD/DVD. Przykładowy nośnik wymienny i dysk CD/DVD to: Grupa **9b28fae8-72f7-4267-a1a5-685f747a7146** z przykładowego pliku Group.xmlKażdy nośnik [Storage wymienny i dysk CD-DVD](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples).

    2. Grupa 2. Zatwierdzone obiekty USB na podstawie właściwości urządzenia. Przykład takiego przypadku użycia to: Identyfikator wystąpienia — grupa **65fa649a-a111-4912-9294-fb6337a25038** w przykładowym zatwierdzonym pliku Group.xml [USBs](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > Zamień `&` na `&amp;` wartość.

2. Tworzenie zasad

    1. Zasady 1. Blokuj pisanie i wykonywanie dostępu, ale zezwalaj na zatwierdzone usb. Przykład takiego przypadku użycia: PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** w przykładowym scenariuszu 1 Blokuj pisanie i wykonywanie dostępu, ale zezwłącz na zatwierdzenie [USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) pliku.

    2. Zasady 2. Inspekcja zapisu i wykonywania dostępu do dozwolonych usb. Przykład takiego przypadku użycia: ZasadyWłączanie **36ae1037-a639-4cff-946b-b36c53089a4c** w przykładowym scenariuszu 1. Inspekcja zapisu i wykonywania dostępu do zatwierdzonego pliku [USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Scenariusz 2. Inspekcja zapisu i wykonywania dostępu do wszystkich, ale zablokowanych określonych niezatwierdzonych spedytów

1. Tworzenie grup

    1. Grupa 1: Dowolne nośniki wymiennych i dyski CD/DVD. Przykład takiego przypadku: Grupa **9b28fae8-72f7-4267-a1a5-685f747a7146** w przykładowym pliku programu [Any Wymienny Storage i DYSK CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples).

    2. Grupa 2. Niezastosowane typy usB oparte na właściwościach urządzenia, na przykład Identyfikator dostawcy/Identyfikator produktu, Przyjazna nazwa — grupa **65fa649a-a111-4912-9294-fb6337a25038** w przykładowym pliku Group.xml [UsBs](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) bez aplikacji.

    > [!TIP]
    > Zamień `&` na `&amp;` wartość.

2. Tworzenie zasad

    1. Zasady 1. Blokuj dostęp do zapisu i wykonywania do wszystkich, ale blokowane są określone bez obsługi spłacowanych kodów USB. Przykład takiego przypadku użycia: ZasadyWłaściwą **zasadą 23b8e437-66ac-4b32-b3d7-24044637fc98** w przykładowym scenariuszu [2](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) . Inspekcja zapisu i wykonywania dostępu do wszystkich plików bez zastosowania w programie USBs.xml.

    2. Zasady 2. Inspekcja zapisu i wykonywania dostępu do innych osób. Przykład takiego przypadku użycia: Zasada **B58ab853-9a6f-405c-a194-740e69422b48** w przykładowym scenariuszu 2. Inspekcja zapisu i wykonywania dostępu [do](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) others.xmlpliku.

## <a name="deploying-and-managing-policy-via-group-policy"></a>Wdrażanie zasad i zarządzanie nimi za pośrednictwem zasady grupy

Funkcja kontrolki Storage wymiennych umożliwia stosowanie zasad za pośrednictwem zasady grupy użytkownika lub urządzenia albo obu tych urządzeń.

### <a name="licensing"></a>Licencjonowanie

Przed rozpoczęciem pracy z wymiennymi Storage Access Control należy potwierdzić subskrypcję Microsoft 365 [Wymienny](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Aby uzyskać dostęp do wymiennych Storage kontroli dostępu, musisz mieć Microsoft 365 E3 lub Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>Wdrażanie zasad za pośrednictwem zasady grupy

1. Wszystkie grupy można połączyć w `<Groups>` `</Groups>` jeden plik XML.

    Na poniższej ilustracji przedstawiono przykład scenariusza 1: Uniemożliwianie pisania i wykonywania dostępu do wszystkich danych, ale zezwoną [na określone zatwierdzone spz](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="Ekran z ustawieniami konfiguracji, które umożliwiają określone zatwierdzone usbs na urządzeniach.":::

2. Wszystkie reguły w jednym pliku `<PolicyRules>` `</PolicyRules>` XML można połączyć.

    Jeśli chcesz ograniczyć określonego użytkownika, użyj właściwości SID we wpisie. Jeśli we wpisie zasad nie ma identyfikatora SID, wpis zostanie zastosowany do każdego wystąpienia logowania na komputerze.
    
    Jeśli chcesz monitorować informacje o pliku pod celu uzyskania dostępu do zapisu, użyj odpowiedniej maski programu Access z odpowiednią opcją (16). oto przykład przechwytywania [informacji o pliku](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml).

    Na poniższej ilustracji przedstawiono użycie właściwości SID i przykład scenariusza 1: Zapobieganie zapisywaniu i uruchamianiu dostępu do wszystkich, ale ze względu na zezwalanie na określone [zatwierdzone usb](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/usage-sid-property.png" alt-text="Ekran z wyświetlonym kodem wskazującym użycie atrybutu właściwości SID.":::

3. Zapisz zarówno plik XML reguły, jak i grupy w folderze udziału sieciowego i umieść ścieżkę folderu udziału sieciowego w ustawieniu **zasady grupy:** \>  \> Szablony administracyjne konfiguracji komputera **Windows Składniki** \> **Program antywirusowy Microsoft Defender** \> **Sterowanie** urządzeniem: **"****Definiowanie grup zasad sterowania urządzeniem" oraz "Definiuj reguły zasad sterowania urządzeniami"**.

   Jeśli nie możesz znaleźć interfejsu użytkownika konfiguracji zasad w programie zasady grupy, możesz pobrać pliki [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) i [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) , wybierając pozycję **Nieprzetworzone** , a następnie pozycję **Zapisz jako**.

   - Aby zasady były dostępne, komputer docelowy musi mieć dostęp do udziału sieciowego. Jednak po przeczytaniu zasad połączenie udziału sieciowego nie jest już wymagane nawet po ponownym uruchomieniu komputera.

    :::image type="content" source="images/device-control.png" alt-text="Ekran Sterowanie urządzeniem.":::

4. Domyślne wymusze: umożliwia ustawienie dostępu domyślnego (odmów lub zezwalania) na nośnik wymienny, jeśli nie ma żadnych zasad. Na przykład masz zasady (Odmów lub Zezwalaj) dla urządzeń wymiennychMediaDevices, ale nie masz żadnych zasad dla cdRomDevices lub WpdDevices i ustawisz domyślną opcję Odmów za pośrednictwem tych zasad, a dostęp do odczytu/zapisu/wykonywania do cdRomDevices lub WpdDevices zostanie zablokowany.

   - Po wdrożeniu tego ustawienia zobaczysz domyślny język **Allow (Zezwalaj domyślny** ) lub **Default Deny (Odmów domyślne**).
   - Podczas konfigurowania tego ustawienia weź pod uwagę zarówno poziom dysku, jak i poziom systemu plikówMask, jeśli na przykład chcesz ustawić wartość Default Deny (Odmów domyślne), ale zezwolić na określone miejsce do magazynowania, musisz zezwolić zarówno na dostęp na poziomie dysku, jak i na poziomie systemu plików. Musisz ustawić wartość AccessMask na 63.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="Domyślny kod zezwalania lub domyślnego odrzucania programu PowerShell":::

5. Włączanie lub wyłączanie kontrolek Storage wymiennych: tę wartość można ustawić w taki sposób, aby tymczasowo wyłączyć kontrolkę programu Access dla Storage wymiennych.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="Ustawienia sterowania urządzeniami":::

   - Po wdrożeniu tego ustawienia zobaczysz **włączoną lub** **wyłączoną**. Wyłączone oznacza, że ten komputer nie ma wymiennych Storage kontroli dostępu.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="Włączone lub wyłączone sterowanie urządzeniem w kodzie programu PowerShell":::

6. Ustawianie lokalizacji kopii pliku: jeśli chcesz mieć kopię pliku podczas uzyskiwania dostępu do zapisu, musisz ustawić lokalizację, w której system może zapisać kopię.
    
    Wdeksuj to razem z odpowiednią opcją i maski dostępu — zobacz krok 2 powyżej.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="zasady grupy — ustawianie informacji o plikach":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Wdrażanie zasad I zarządzanie nimi za pośrednictwem usługi Intune OMA-URI

Funkcja kontrolki Storage wymiennych umożliwia stosowanie zasad za pośrednictwem interfejsu OMA-URI do użytkownika, urządzenia lub obu tych urządzeń.

### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Przed rozpoczęciem pracy z wymiennymi Storage Access Control należy potwierdzić subskrypcję Microsoft 365 [Wymienny](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Aby uzyskać dostęp do wymiennych Storage kontroli dostępu, musisz mieć Microsoft 365 E3 lub Microsoft 365 E5.

### <a name="permission"></a>Uprawnienie

Do wdrożenia zasad w usłudze Intune konto musi mieć uprawnienia do tworzenia, edytowania, aktualizowania i usuwania profilów konfiguracji urządzenia. Możesz utworzyć role niestandardowe lub użyć dowolnej z wbudowanych ról z tymi uprawnieniami.

- Rola Menedżera zasad i profilu

- Rola niestandardowa z włączonymi uprawnieniami Tworzenie/Edycja/Aktualizacja/Odczyt/Usuwanie/Wyświetlanie raportów dla profilów konfiguracji urządzenia

- Administrator globalny

### <a name="deploying-policy-via-oma-uri"></a>Wdrażanie zasad za pośrednictwem usługi OMA-URI

Microsoft Endpoint Manager administracyjnego (<https://endpoint.microsoft.com/>)   \> **Urządzenia** \> \> \> Profile konfiguracji Utwórz **platformę profilów: Windows 10 lub** nowsza & Profil: Niestandardowy

1. Dla każdej grupy utwórz regułę OMA-URI:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      Na przykład w przypadku **dowolnego magazynu wymiennych i grup dysków CD/DVD** w próbce link musi mieć grupę:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - Typ danych: Ciąg (plik XML)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="Plik XML dla typu danych STRING.":::

2. Dla każdej zasady utwórz również OMA-URI:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      Na przykład dla reguł Blokuj **pisanie i wykonywanie dostępu** , ale zezwalaj na zatwierdzone reguły USBs w przykładzie, łącze musi być takie:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - Typ danych: Ciąg (plik XML)
       
    Jeśli chcesz monitorować informacje o pliku pod celu uzyskania dostępu do zapisu, użyj odpowiedniej maski programu Access z odpowiednią opcją (16). oto przykład przechwytywania [informacji o pliku](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml).

3. Domyślne wymusze: umożliwia ustawienie dostępu domyślnego (odmów lub zezwalania) na nośnik wymienny, jeśli nie ma żadnych zasad. Na przykład masz zasady (Odmów lub Zezwalaj) dla urządzeń wymiennychMediaDevices, ale nie masz żadnych zasad dla cdRomDevices lub WpdDevices i ustawisz domyślną opcję Odmów za pośrednictwem tych zasad, a dostęp do odczytu/zapisu/wykonywania do cdRomDevices lub WpdDevices zostanie zablokowany.

    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - Typ danych: Int

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - Po wdrożeniu tego ustawienia zobaczysz domyślny język **Allow (Zezwalaj)** lub **Default Deny (Odmów domyślne)**
    - Podczas konfigurowania tego ustawienia weź pod uwagę zarówno poziom dysku, jak i poziom systemu plikówMask, jeśli na przykład chcesz ustawić wartość Default Deny (Odmów domyślne), ale zezwolić na określone miejsce do magazynowania, musisz zezwolić zarówno na dostęp na poziomie dysku, jak i na poziomie systemu plików. Musisz ustawić wartość AccessMask na 63.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="Domyślne wymuszanie kodu zezwalania na stosowanie programu PowerShell":::

4. Włączanie lub wyłączanie kontrolek Storage wymiennych: tę wartość można ustawić w taki sposób, aby tymczasowo wyłączyć kontrolkę programu Access dla Storage wymiennych.

   - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - Typ danych: Int `Disable: 0`
     `Enable: 1`

   - Po wdrożeniu tego ustawienia zobaczysz **włączoną lub** **wyłączoną**

    **Wyłączone** oznacza, że ten komputer nie ma uruchomionej Storage Kontroli dostępu

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="Usuwalny Storage dostępu w kodzie programu PowerShell":::

5. Ustawianie lokalizacji kopii pliku: jeśli chcesz mieć kopię pliku podczas uzyskiwania dostępu do zapisu, musisz ustawić lokalizację, w której system może zapisać kopię.
    
    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation;**username**;**password**`

    - Typ danych: Ciąg
    
    Musisz wdrożyć to razem z odpowiedniąmask AccessMask i odpowiednią opcją — zobacz krok 2 powyżej.

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="Ustawianie locaitonu jako dowodu pliku":::
    
## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Wdrażanie zasad i zarządzanie nimi przy użyciu interfejsu użytkownika usługi Intune

Ta funkcja jest dostępna w centrum Microsoft Endpoint Manager administracyjnego (<https://endpoint.microsoft.com/>). Przejdź do **zabezpieczeń punktu końcowegoWłącz** >  **zmniejszanie** **powierzchniZatworzenie** >  zasad. Wybierz **platformę: Windows 10 i nowsze z** **profilem: Device Control**.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Wyświetlanie danych kontrolki urządzenia wymiennych Storage kontroli dostępu w programie Microsoft Defender for Endpoint

Portal [Microsoft 365 Defender zawiera zdarzenia](https://security.microsoft.com/advanced-hunting) wywoływane przez wymienną kontrolkę sterowania Storage Access Control. Aby uzyskać dostęp Microsoft 365 zabezpieczeń, musisz mieć następującą subskrypcję:

- Microsoft 365 raportów E5

```kusto
//RemovableStoragePolicyTriggered: event triggered by Disk level enforcement
DeviceEvents
| where ActionType == "RemovableStoragePolicyTriggered"
| extend parsed=parse_json(AdditionalFields)
| extend RemovableStorageAccess = tostring(parsed.RemovableStorageAccess)
| extend RemovableStoragePolicyVerdict = tostring(parsed.RemovableStoragePolicyVerdict)
| extend MediaBusType = tostring(parsed.BusType)
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaDeviceId = tostring(parsed.DeviceId)
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend RemovableStoragePolicy = tostring(parsed.RemovableStoragePolicy)
| extend MediaProductId = tostring(parsed.ProductId)
| extend MediaVendorId = tostring(parsed.VendorId)
| extend MediaSerialNumber = tostring(parsed.SerialNumber)
|project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, RemovableStorageAccess, RemovableStoragePolicyVerdict, MediaBusType, MediaClassGuid, MediaClassName, MediaDeviceId, MediaInstanceId, MediaName, RemovableStoragePolicy, MediaProductId, MediaVendorId, MediaSerialNumber
| order by Timestamp desc
```

```kusto
//RemovableStorageFileEvent: event triggered by File level enforcement, information of files written to removable storage 
DeviceEvents
| where ActionType contains "RemovableStorageFileEvent"
| extend parsed=parse_json(AdditionalFields)
| extend Policy = tostring(parsed.Policy) 
| extend PolicyRuleId = tostring(parsed.PolicyRuleId) 
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaInstanceId = tostring(parsed.InstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend MediaProductId = tostring(parsed.ProductId) 
| extend MediaVendorId = tostring(parsed.VendorId) 
| extend MediaSerialNumber = tostring(parsed.SerialNumber) 
| extend DuplicatedOperation = tostring(parsed.DuplicatedOperation)
| extend FileEvidenceLocation = tostring(parsed.TargetFileLocation) 
| project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, 
    ActionType, Policy, PolicyRuleId, DuplicatedOperation, 
    MediaClassName, MediaInstanceId, MediaName, MediaProductId, MediaVendorId, MediaSerialNumber,
    FileName, FolderPath, FileSize, FileEvidenceLocation,
    AdditionalFields
| order by Timestamp desc
```
    
:::image type="content" source="images/block-removable-storage.png" alt-text="Ekran przedstawiający blokadę magazynu wymiennych.":::

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>Jakie jest ograniczenie maksymalnej liczby nośników wymiennych?

Sprawdziliśmy, czy jedna grupa USB ma rozmiar 100 000 multimediów — do 7 MB. Te zasady działają zarówno w usłudze Intune, jak i w usłudze GPO bez problemów z wydajnością.

### <a name="why-does-the-policy-not-work"></a>Dlaczego zasady nie działają?

Najczęstszą przyczyną jest brak wymaganej wersji klienta ochrony [przed złośliwym oprogramowaniem](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

Innym powodem może być to, że plik XML nie został prawidłowo sformatowany, na przykład nie używa prawidłowego formatowania znaczników dla znaku "&" w pliku XML lub edytor tekstu może dodać znak kolejności bajtów (BOM) 0xEF 0xBB 0xBF na początku plików, co powoduje, że analizowanie JĘZYKA XML nie działa. Jedno proste rozwiązanie to pobranie przykładowego pliku (wybierz pozycję **Nieprzetworzone**, a następnie Zapisz **jako**), a następnie zaktualizowanie.[](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)

Jeśli wdrażasz zasady i zarządzasz nimi za pośrednictwem programu zasady grupy, upewnij się, że wszystkie zasadyRule są w jeden plik XML w węźle nadrzędnym o nazwie PolicyRules i wszystkie grupy w jeden plik XML w węźle nadrzędnym o nazwie Grupy. jeśli zarządzasz za pomocą usługi Intune, zachowaj jedną ZasadyWłasność jednego pliku XML, tego samego elementu, jednego grupowania jednego pliku XML.

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Nie ma żadnego interfejsu użytkownika konfiguracji dla opcji "Definiowanie grup zasad sterowania urządzeniem" i "Definiuj reguły zasad sterowania urządzeniami" na moim zasady grupy

Nie są nam rzutowane środowiska użytkownika konfiguracji programu zasady grupy, ale nadal można uzyskać powiązane pliki adml i admx, klikając pozycję "Nieprzetworzone" i "Zapisz jako" w plikach [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) i [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) .

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>Skąd wiadomo, czy najnowsze zasady zostały wdrożone na komputerze docelowym?

W programie PowerShell możesz uruchomić statystykę "Get-MpComputerStatus" jako administrator. Następująca wartość będzie określać, czy najnowsze zasady zostały zastosowane do komputera docelowego.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>Skąd wiadomo, że na którym komputerze jest obecnie w organizacji klient korzystający z najnowszej wersji oprogramowania antywirusowego?

Możesz użyć następującego zapytania w celu uzyskania wersji klienta ochrony przed złośliwym kodem w portalu Microsoft 365 zabezpieczeń:

```kusto
//check the antimalware client version
DeviceFileEvents
|where FileName == "MsMpEng.exe"
|where FolderPath contains @"C:\ProgramData\Microsoft\Windows Defender\Platform\"
|extend PlatformVersion=tostring(split(FolderPath, "\\", 5))
//|project DeviceName, PlatformVersion // check which machine is using legacy platformVersion
|summarize dcount(DeviceName) by PlatformVersion // check how many machines are using which platformVersion
|order by PlatformVersion desc
```
