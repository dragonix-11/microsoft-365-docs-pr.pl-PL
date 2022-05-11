---
title: Ochrona punktu końcowego w usłudze Microsoft Defender Storage Access Control wymienne kontrolki urządzenia, wymienne nośniki magazynu
description: Przewodnik po Ochrona punktu końcowego w usłudze Microsoft Defender
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
ms.date: 05/09/2022
ms.openlocfilehash: a472a2183d642ca8c3231e6ca5129fdf79cad8fd
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317631"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Ochrona punktu końcowego w usłudze Microsoft Defender Storage Access Control wymienna kontrolki urządzenia

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

> [!NOTE]
> Zarządzanie zasady grupy i zarządzanie Intune OMA-URI/niestandardowe zarządzanie zasadami tego produktu są teraz ogólnie dostępne (4.18.2106): Zobacz [blog Tech Community: Ochrona wymiennego magazynu i drukarki za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

Ochrona punktu końcowego w usłudze Microsoft Defender Storage Access Control wymiennych kontroli urządzeń umożliwia wykonanie następującego zadania:

- inspekcja, zezwalanie na odczyt, zapis lub wykonywanie dostępu do magazynu wymiennego z wykluczeniem lub bez nich

|Uprawnień|Uprawnienia|
|---|---|
|Access|Odczyt, zapis, wykonanie|
|Tryb akcji|Inspekcja, Zezwalaj, Zapobiegaj|
|Obsługa programu CSP|Tak|
|Obsługa obiektu zasad grupy|Tak|
|Obsługa oparta na użytkownikach|Tak|
|Obsługa oparta na maszynie|Tak|

|Możliwości|Opis|Wdrażanie za pośrednictwem Intune|Wdrażanie za pośrednictwem zasady grupy|
|---|---|---|---|
|Tworzenie wymiennej grupy multimediów|Umożliwia tworzenie wymiennej grupy multimediów wielokrotnego użytku|Krok 1 w sekcji [Wdrażanie zasad za pośrednictwem identyfikatora OMA-URI](#deploying-policy-via-oma-uri) | Krok 1 w sekcji [Wdrażanie zasad za pośrednictwem zasady grupy](#deploying-policy-via-group-policy)|
|Tworzenie zasad|Umożliwia tworzenie zasad wymuszania każdej wymiennej grupy multimediów|Krok 2 w sekcji [Wdrażanie zasad za pośrednictwem identyfikatora OMA-URI](#deploying-policy-via-oma-uri) | Kroki 2 i 3 w sekcji [Wdrażanie zasad za pośrednictwem zasady grupy](#deploying-policy-via-group-policy) |
|Domyślne wymuszanie|Umożliwia ustawienie domyślnego dostępu (Odmów lub Zezwalaj) na nośnik wymienny, jeśli nie ma żadnych zasad|Krok 3 w sekcji [Wdrażanie zasad za pośrednictwem identyfikatora OMA-URI](#deploying-policy-via-oma-uri) | Krok 4 w sekcji [Wdrażanie zasad za pośrednictwem zasady grupy](#deploying-policy-via-group-policy) |
|Włączanie lub wyłączanie Storage Access Control wymiennych|Jeśli ustawisz opcję Wyłącz, spowoduje to wyłączenie zasad Storage Access Control wymiennych na tym komputerze| Krok 4 w sekcji [Wdrażanie zasad za pośrednictwem identyfikatora OMA-URI](#deploying-policy-via-oma-uri) | Krok 5 w sekcji [Wdrażanie zasad za pośrednictwem zasady grupy](#deploying-policy-via-group-policy) |
|Przechwytywanie informacji o pliku|Umożliwia tworzenie zasad w celu przechwytywania informacji o plikach w przypadku korzystania z dostępu do zapisu| Kroki 2 i 5 w sekcji [Wdrażanie zasad za pośrednictwem identyfikatora OMA-URI](#deploying-policy-via-oma-uri) | Krok 2 i 6 w sekcji [Wdrażanie zasad za pośrednictwem zasady grupy](#deploying-policy-via-group-policy) |

## <a name="prepare-your-endpoints"></a>Przygotowywanie punktów końcowych

Wdróż Storage Access Control wymienne na urządzeniach Windows 10 i Windows 11, które mają klienta ochrony przed złośliwym kodem w wersji **4.18.2103.3 lub nowszej**.

- **4.18.2104 lub nowszy**: Dodaj identyfikator SerialNumberId, VID_PID, obsługę obiektów zasad grupy opartych na ścieżce plików, ComputerSid

- **4.18.2105 lub nowszy**: Dodaj obsługę symboli wieloznacznych dla hardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId, kombinacji określonego użytkownika na określonej maszynie, wymiennego dysku SSD (SanDisk Extreme SSD)/obsługa dołączonego interfejsu SCSI (UAS) usb

- **4.18.2107 lub nowszy**: dodaj obsługę Windows Portable Device (WPD) (dla urządzeń przenośnych, takich jak tablety), dodaj nazwę konta do [zaawansowanego wyszukiwania zagrożeń](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

:::image type="content" source="images/powershell.png" alt-text="Interfejs programu PowerShell" lightbox="images/powershell.png":::

> [!NOTE]
> Żaden ze składników Zabezpieczenia Windows nie musi być aktywny, ponieważ można uruchamiać Storage Access Control wymienne niezależnie od stanu Zabezpieczenia Windows.

## <a name="policy-properties"></a>Właściwości zasad

Aby utworzyć grupę magazynu wymiennego, można użyć następujących właściwości:

> [!NOTE]
> Komentarze korzystające z notacji `<!-- COMMENT -->` komentarzy XML mogą być używane w plikach XML reguły i grupy, ale muszą znajdować się wewnątrz pierwszego tagu XML, a nie pierwszego wiersza pliku XML.

### <a name="removable-storage-group"></a>Wymienna grupa Storage

|Nazwa właściwości|Opis|Opcje|
|---|---|---|
|**Identyfikator grupy**|Identyfikator GUID, unikatowy identyfikator, reprezentuje grupę i będzie używany w zasadach jako GroupId||
|**DeskryptorIdList**|Wyświetl listę właściwości urządzenia, których chcesz użyć do pokrycia w grupie. Aby uzyskać więcej szczegółów, zobacz [Właściwości urządzenia](device-control-removable-storage-protection.md) dla każdej właściwości urządzenia. Wszystkie właściwości uwzględniają wielkość liter. |**PrimaryId**: `RemovableMediaDevices`, , `CdRomDevices``WpdDevices`<p>**BusId**: na przykład USB, SCSI<p>**Deviceid**<p>**HardwareId**<p>**InstancePathId**: InstancePathId to ciąg, który jednoznacznie identyfikuje urządzenie w systemie, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`na przykład . Numer na końcu (na przykład &0) reprezentuje dostępne miejsce i może ulec zmianie z urządzenia na urządzenie. Aby uzyskać najlepsze wyniki, użyj symbolu wieloznacznego na końcu. Na przykład `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: dopasuj tę dokładną parę VID/PID<p>`_55E0`: dopasuj dowolne nośniki do PID=55E0 <p>`0751_`: dopasuj dowolny nośnik do VID=0751|
|**Typ dopasowania**|W przypadku użycia wielu właściwości urządzenia w parametrze `DescriptorIDList`MatchType definiuje relację.|**MatchAll**: Wszystkie atrybuty w obszarze `DescriptorIdList` będą **i relacji** , na przykład, jeśli administrator stawia `DeviceID` i `InstancePathID`, dla każdego podłączonego USB, system sprawdzi, czy USB spełnia obie wartości. <p> **MatchAny**: atrybuty w obszarze DescriptorIdList będą mieć wartość **Lub** . Na przykład, jeśli administrator umieszcza `DeviceID` i `InstancePathID`, dla każdego podłączonego USB, system wykona wymuszanie tak długo, jak usb ma identyczną wartość **DeviceID** lub **InstanceID** . |

### <a name="access-control-policy"></a>zasady Access Control

| Nazwa właściwości | Opis | Opcje |
|---|---|---|
| **Identyfikator reguły zasad** | Identyfikator GUID, unikatowy identyfikator, reprezentuje zasady i będzie używany w raportowaniu i rozwiązywaniu problemów. | |
| **IncludedIdList** | Grupy, do których zostaną zastosowane zasady. Jeśli zostanie dodanych wiele grup, zasady zostaną zastosowane do dowolnego nośnika we wszystkich tych grupach.|W tym wystąpieniu należy użyć identyfikatora/identyfikatora GUID grupy. <p> W poniższym przykładzie przedstawiono użycie identyfikatora GroupID: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | Grupy, do których zasady nie zostaną zastosowane. | W tym wystąpieniu należy użyć identyfikatora/identyfikatora GUID grupy. |
| **Identyfikator wpisu** | Jedna reguła zasad może zawierać wiele wpisów; Każdy wpis z unikatowym identyfikatorem GUID informuje kontrolkę urządzenia o jednym ograniczeniu.| |
| **Type** | Definiuje akcję dla wymiennych grup magazynów w obszarze IncludedIDList. <p>Wymuszanie: zezwalanie lub odrzucanie <p>Inspekcja: AuditAllowed lub AuditDenied<p> | Zezwalaj<p>Odmów <p>AuditAllowed: definiuje powiadomienia i zdarzenia, gdy dostęp jest dozwolony <p>AuditDenied: definiuje powiadomienia i zdarzenia, gdy odmowa dostępu; musi współpracować **z** odmową wpisu.<p> Jeśli istnieją typy konfliktów dla tego samego nośnika, system zastosuje pierwszy z nich w zasadach. Przykładem typu konfliktu są **Zezwalaj** i **Odmów**. |
| **Sid** | Identyfikator Sid użytkownika lokalnego, grupa sid użytkownika lub identyfikator Sid obiektu usługi AD określa, czy te zasady mają być stosowane względem określonego użytkownika lub grupy użytkowników; Jeden wpis może mieć maksymalnie jeden identyfikator Sid, a wpis bez identyfikatora Sid oznacza zastosowanie zasad na maszynie. |  |
| **ComputerSid** | Identyfikator SID komputera lokalnego lub grupa sid komputera lub identyfikator Sid obiektu usługi AD określa, czy te zasady mają być stosowane do określonej maszyny lub grupy maszyn; Jeden wpis może mieć maksymalnie jeden ComputerSid i wpis bez żadnych ComputerSid oznacza zastosowanie zasad na maszynie. Jeśli chcesz zastosować wpis do określonego użytkownika i konkretnej maszyny, dodaj identyfikator Sid i ComputerSid do tego samego wpisu. |  |
| **Opcje** | Określa, czy ma być wyświetlane powiadomienie, czy nie |**Po wybraniu opcji Zezwalaj na typ:** <p>0: nic<p>4: wyłącz **auditAllowed** i **AuditDenied** dla tego wpisu. Nawet jeśli ustawienie **Zezwalaj** zostanie skonfigurowane, a ustawienie AuditAllowed zostanie skonfigurowane, system nie wyśle zdarzenia. <p>8: przechwytywanie informacji o pliku i posiadanie kopii pliku jako dowodu na dostęp do zapisu. <p>16: przechwytywanie informacji o pliku na potrzeby dostępu do zapisu. <p>**Po wybraniu opcji Odmów typu**: <p>0: nic<p>4: wyłącz **wartość AuditDenied** dla tego wpisu. Nawet jeśli ustawienie **Blokuj** nastąpi i skonfigurowano ustawienie AuditDenied, system nie wyświetli powiadomienia. <p>**Po **wybraniu opcji Typ AuditAllowed**:** <p>0: nic <p>1: nic <p>2: wyślij zdarzenie<p> **Po **wybraniu opcji Type AuditDenied****: <p>0: nic <p>1: pokaż powiadomienie <p>2: wyślij zdarzenie<p>3: pokaż powiadomienie i wyślij zdarzenie |
|Maska dostępu|Definiuje dostęp. | **Dostęp na poziomie dysku**: <p>1: Odczyt <p>2: Zapis <p>4: Wykonywanie <p>**Dostęp na poziomie systemu plików**: <p>8: Odczyt systemu plików <p>16: Zapis systemu plików <p>32: Wykonywanie systemu plików <p><p>Możesz mieć wiele dostępu, wykonując operację binarną LUB, na przykład maska dostępu do odczytu i zapisu i wykonywania będzie miała wartość 7; Maska dostępu dla odczytu i zapisu będzie mieć wartość 3.|

## <a name="common-removable-storage-access-control-scenarios"></a>Typowe scenariusze Storage Access Control wymiennych

Aby ułatwić zapoznanie się z Ochrona punktu końcowego w usłudze Microsoft Defender Storage Access Control wymiennych, przygotowaliśmy kilka typowych scenariuszy, które należy wykonać.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scenariusz 1. Uniemożliwiaj dostęp do zapisu i wykonywania wszystkim, ale zezwalaj na określone zatwierdzone obiekty USB

1. Tworzenie grup

    1. Grupa 1. Dowolny magazyn wymienny i dysk CD/DVD. Przykładem magazynu wymiennego i dysków CD/DVD jest grupa **9b28fae8-72f7-4267-a1a5-685f747a7146** w przykładowym pliku [Group.xmlAny Removable Storage and CD-DVD.](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)

    2. Grupa 2. Zatwierdzone bazy danych USB na podstawie właściwości urządzenia. Przykładem tego przypadku użycia jest: Identyfikator wystąpienia — grupa **65fa649a-a111-4912-9294-fb6337a25038** w przykładowym pliku [Group.xmlZatwierdzone obiekty USB](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > Zastąp `&` element `&amp;` wartością .

2. Tworzenie zasad

    1. Zasady 1: blokuj dostęp do zapisu i wykonywania, ale zezwalaj na zatwierdzone obiekty USB. Przykładem tego przypadku użycia jest: PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** w przykładowym [scenariuszu 1 Blokuj dostęp do zapisu i wykonywania, ale zezwalaj na zatwierdzony plik USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. Zasady 2: Inspekcja dostępu do zapisu i wykonywania dozwolonych baz danych USB. Przykładem tego przypadku użycia jest: PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** w przykładowym [scenariuszu 1 Inspekcja zapisu i wykonywania dostępu do zatwierdzonego pliku USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Scenariusz 2. Inspekcja dostępu do zapisu i wykonywania dla wszystkich niezatwierdowanych obiektów USB, z wyłączeniem bloku

1. Tworzenie grup

    1. Grupa 1. Dowolny magazyn wymienny i dysk CD/DVD. Przykładem tego przypadku użycia jest grupa **9b28fae8-72f7-4267-a1a5-685f747a7146** w przykładowym pliku [Storage wymiennym i cd-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples).

    2. Grupa 2: Niezatwierdzone obiekty USB oparte na właściwościach urządzenia, na przykład identyfikator dostawcy / identyfikator produktu, przyjazna nazwa — grupa **65fa649a-a111-4912-9294-fb6337a25038** w przykładowym pliku [Group.xmlniezatwierdzone obiekty USBs](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > Zastąp `&` element `&amp;` wartością .

2. Tworzenie zasad

    1. Zasady 1: blokuj dostęp do zapisu i wykonywania dla wszystkich niezatwierdzone obiekty USB, ale blokuj je. Przykładem tego przypadku użycia jest: PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** w przykładowym [scenariuszu 2 Audit Write and Execute access to all but block specific unapproved USBs.xmlfile ( Reguła zasad 2 Inspekcja zapisu i wykonywania) do wszystkich niezatwierdzone USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) pliku.

    2. Zasady 2: Inspekcja dostępu do zapisu i wykonywania dla innych osób. Przykładem tego przypadku użycia jest: PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** w przykładowym [scenariuszu 2 Inspekcja zapisu i wykonywania dostępu do pliku others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

## <a name="deploying-and-managing-policy-via-group-policy"></a>Wdrażanie zasad i zarządzanie nimi za pośrednictwem zasady grupy

Funkcja wymiennego Storage Access Control umożliwia stosowanie zasad za pośrednictwem zasady grupy do użytkownika lub urządzenia lub obu tych elementów.

### <a name="licensing"></a>Licencjonowanie

Przed rozpoczęciem pracy z usługą Removable Storage Access Control musisz potwierdzić [subskrypcję Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Aby uzyskać dostęp do Storage Access Control wymiennych i korzystać z nich, musisz mieć Microsoft 365 E3 lub Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>Wdrażanie zasad za pośrednictwem zasady grupy

1. Połącz wszystkie grupy w jednym `<Groups>` `</Groups>` pliku XML.

    Na poniższej ilustracji przedstawiono przykład [scenariusza 1: Zapobieganie dostępowi do zapisu i wykonywania do wszystkich, ale zezwalanie na określone zatwierdzone obiekty USB](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="Ustawienia konfiguracji, które zezwalają na określone zatwierdzone obiekty USB na urządzeniach" lightbox="images/prevent-write-access-allow-usb.png":::

2. Połącz wszystkie reguły w jednym `<PolicyRules>` `</PolicyRules>` pliku XML.

    Jeśli chcesz ograniczyć określonego użytkownika, użyj właściwości SID do pozycji Wpis. Jeśli w wpisie zasad nie ma identyfikatora SID, pozycja Entry zostanie zastosowana do wszystkich wystąpień logowania dla maszyny.

    Jeśli chcesz monitorować informacje o pliku pod kątem dostępu do zapisu, użyj odpowiedniej maski dostępu z odpowiednią opcją (16); oto przykład przechwytywania [informacji o pliku](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml).

    Na poniższej ilustracji przedstawiono użycie właściwości SID oraz przykład [scenariusza 1: Zapobieganie dostępowi do zapisu i wykonywania do wszystkich, ale zezwalaj na określone zatwierdzone obiekty USB](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/usage-sid-property.png" alt-text="Kod wskazujący użycie atrybutu właściwości IDENTYFIKATORA SID" lightbox="images/usage-sid-property.png":::

3. Zapisz pliki XML reguły i grupy w folderze udziału sieciowego i umieść ścieżkę folderu udziału sieciowego w ustawieniu zasady grupy: **Konfiguracja** \> komputera **Szablony** \> administracyjne **Windows Składniki** \> **Program antywirusowy Microsoft Defender** \> **Kontrolka urządzenia**: **"Definiowanie grup zasad sterowania urządzeniami"** i **"Definiowanie reguł zasad sterowania urządzeniami"**.

   Jeśli nie możesz znaleźć środowiska użytkownika konfiguracji zasad w zasady grupy, możesz pobrać pliki [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) i [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx), wybierając pozycję **Nieprzetworzone**, a następnie **zapisz jako**.

   - Aby mieć zasady, maszyna docelowa musi mieć dostęp do udziału sieciowego. Jednak po odczytaniu zasad połączenie udziału sieciowego nie jest już wymagane, nawet po ponownym uruchomieniu komputera.

    :::image type="content" source="images/device-control.png" alt-text="Ekran Kontrolka urządzenia" lightbox="images/device-control.png":::

4. Domyślne wymuszanie: umożliwia ustawienie domyślnego dostępu (Odmów lub Zezwalaj) na nośnik wymienny, jeśli nie ma żadnych zasad. Na przykład masz tylko zasady (odmów lub zezwalaj) dla urządzeń RemovableMediaDevices, ale nie masz żadnych zasad dla urządzeń CdRomDevices lub WpdDevices, a domyślne ustawienie Odmów za pomocą tych zasad spowoduje zablokowanie dostępu odczytu/zapisu/wykonywania do urządzeń CdRomDevices lub WpdDevices.

   - Po wdrożeniu tego ustawienia zostanie **wyświetlone ustawienie Domyślne zezwalanie** lub **Domyślna odmowa**.
   - Podczas konfigurowania tego ustawienia należy wziąć pod uwagę zarówno poziom dysków, jak i poziom systemu plików, na przykład jeśli chcesz domyślnie odmawiać, ale zezwalać na określony magazyn, musisz zezwolić na dostęp na poziomie dysku i na poziomie systemu plików, musisz ustawić właściwość AccessMask na wartość 63.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="Domyślny kod zezwalania lub domyślnego odmowy programu PowerShell":::

5. Włącz lub wyłącz Storage Access Control wymienne: możesz ustawić tę wartość, aby tymczasowo wyłączyć Storage Access Control wymienne.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="Ustawienia kontrolki urządzenia":::

   - Po wdrożeniu tego ustawienia zobaczysz pozycję **Włączone** lub **Wyłączone**. Wyłączone oznacza, że ta maszyna nie ma uruchomionych zasad Storage Access Control wymiennych.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="Włączone lub wyłączone sterowanie urządzeniem w kodzie programu PowerShell":::

6. Ustaw lokalizację kopii pliku: jeśli chcesz mieć kopię pliku w przypadku dostępu do zapisu, musisz ustawić lokalizację, w której system może zapisać kopię.

    Wdróż to razem z odpowiednią maską dostępu i opcją — zobacz krok 2 powyżej.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="zasady grupy - Ustaw locaiton dla dowodów pliku":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Wdrażanie zasad i zarządzanie nimi za pośrednictwem Intune identyfikatora OMA-URI

Funkcja wymiennego Storage Access Control umożliwia stosowanie zasad za pośrednictwem identyfikatora OMA-URI do użytkownika lub urządzenia lub obu tych elementów.

### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Przed rozpoczęciem pracy z usługą Removable Storage Access Control musisz potwierdzić [subskrypcję Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Aby uzyskać dostęp do Storage Access Control wymiennych i korzystać z nich, musisz mieć Microsoft 365 E3 lub Microsoft 365 E5.

### <a name="permission"></a>Uprawnienia

W przypadku wdrażania zasad w Intune konto musi mieć uprawnienia do tworzenia, edytowania, aktualizowania lub usuwania profilów konfiguracji urządzeń. Możesz utworzyć role niestandardowe lub użyć dowolnej z wbudowanych ról z tymi uprawnieniami.

- Rola Menedżera zasad i profilu

- Rola niestandardowa z włączonymi uprawnieniami Utwórz/Edytuj/Aktualizuj/Odczyt/Usuń/Wyświetl raporty dla profilów konfiguracji urządzenia

- Administrator globalny

### <a name="deploying-policy-via-oma-uri"></a>Wdrażanie zasad za pośrednictwem identyfikatora OMA-URI

Microsoft Endpoint Manager w centrum administracyjnym (<https://endpoint.microsoft.com/>) \> **Profile konfiguracji** **urządzeń** \> **Tworzenie profilu** \> **Platforma: Windows 10 i nowsze** \> profile &: niestandardowe

1. Dla każdej grupy utwórz regułę OMA-URI:

    - Identyfikator OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      Na przykład dla **dowolnego magazynu wymiennego i grupy dysków CD/DVD** w przykładzie link musi być następujący:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - Typ danych: ciąg (plik XML)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="Pole Typ danych na stronie Dodawanie wiersza" lightbox="images/xml-data-type-string.png":::

2. Dla każdej zasady utwórz również identyfikator OMA-URI:

    - Identyfikator OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      Na przykład dla reguły **Blokuj dostęp do zapisu i wykonywania, ale zezwalaj na zatwierdzoną regułę USBs** w przykładzie, link musi być następujący:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - Typ danych: ciąg (plik XML)

    Jeśli chcesz monitorować informacje o pliku pod kątem dostępu do zapisu, użyj odpowiedniej maski dostępu z odpowiednią opcją (16); oto przykład przechwytywania [informacji o pliku](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml).

3. Domyślne wymuszanie: umożliwia ustawienie domyślnego dostępu (Odmów lub Zezwalaj) na nośnik wymienny, jeśli nie ma żadnych zasad. Na przykład masz tylko zasady (odmów lub zezwalaj) dla urządzeń RemovableMediaDevices, ale nie masz żadnych zasad dla urządzeń CdRomDevices lub WpdDevices, a domyślne ustawienie Odmów za pomocą tych zasad spowoduje zablokowanie dostępu odczytu/zapisu/wykonywania do urządzeń CdRomDevices lub WpdDevices.

    - Identyfikator OMA-URI: `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - Typ danych: Int

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - Po wdrożeniu tego ustawienia zostanie wyświetlone **ustawienie Domyślne zezwalanie** lub **Domyślne odmawianie**
    - Podczas konfigurowania tego ustawienia należy wziąć pod uwagę zarówno poziom dysków, jak i poziom systemu plików, na przykład jeśli chcesz domyślnie odmawiać, ale zezwalać na określony magazyn, musisz zezwolić na dostęp na poziomie dysku i na poziomie systemu plików, musisz ustawić właściwość AccessMask na wartość 63.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="Domyślne wymuszanie zezwala na kod programu PowerShell":::

4. Włącz lub wyłącz Storage Access Control wymienne: możesz ustawić tę wartość, aby tymczasowo wyłączyć Storage Access Control wymienne.

   - Identyfikator OMA-URI: `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - Typ danych: Int `Disable: 0`
     `Enable: 1`

   - Po wdrożeniu tego ustawienia zobaczysz pozycję **Włączone** lub **Wyłączone**

    **Wyłączone** oznacza, że ta maszyna nie ma uruchomionych zasad Storage Access Control wymiennych

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="Usuwanie Storage Access Control w kodzie programu PowerShell":::

5. Ustaw lokalizację kopii pliku: jeśli chcesz mieć kopię pliku podczas zapisu, musisz ustawić lokalizację, w której system może zapisać kopię.

    - OMA-URI: './Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation

    - Typ danych: ciąg

    Musisz wdrożyć tę funkcję razem z odpowiednią maską dostępu i właściwą opcją — zobacz krok 2 powyżej.

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="Ustaw locaiton dla dowodów pliku":::

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Wdrażanie zasad i zarządzanie nimi przy użyciu interfejsu użytkownika Intune

(*Wkrótce!*) Ta funkcja będzie dostępna w centrum administracyjnym Microsoft Endpoint Manager (<https://endpoint.microsoft.com/>). Przejdź do **obszaru Zabezpieczenia** >  punktu **końcowegoZasuń redukcję** >  **powierzchniUtwórz zasady**. Wybierz **pozycję Platforma: Windows 10 i nowsze** z **opcją Profil: Kontrola urządzenia**.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Wyświetlanie danych Storage Access Control wymiennych kontrolek urządzenia w Ochrona punktu końcowego w usłudze Microsoft Defender

W [portalu Microsoft 365 Defender](https://security.microsoft.com/advanced-hunting) są wyświetlane zdarzenia wyzwalane przez Storage Access Control wymienne kontrolki urządzenia. Aby uzyskać dostęp do zabezpieczeń Microsoft 365, musisz mieć następującą subskrypcję:

- Microsoft 365 raportowania E5

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
//information of file written to removable storage 
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
| extend FileInformationOperation = tostring(parsed.DuplicatedOperation)
| extend FileEvidenceLocation = tostring(parsed.TargetFileLocation) 
| project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, Policy, PolicyRuleId, FileInformationOperation, MediaClassName, MediaInstanceId, MediaName, MediaProductId, MediaVendorId, MediaSerialNumber, FileName, FolderPath, FileSize, FileEvidenceLocation, AdditionalFields
| order by Timestamp desc
```

:::image type="content" source="images/block-removable-storage.png" alt-text="Ekran przedstawiający blokadę magazynu wymiennego.":::

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="how-to-generate-guid-for-group-idpolicyrule-identry-id"></a>Jak wygenerować identyfikator GUID dla identyfikatora grupy/identyfikatora reguły zasad/identyfikatora wpisu?

Identyfikator GUID można wygenerować za pośrednictwem open source online lub za pomocą programu PowerShell — [jak wygenerować identyfikator GUID za pomocą programu PowerShell](/powershell/module/microsoft.powershell.utility/new-guid)

![Obrazu](https://user-images.githubusercontent.com/81826151/159046476-26ea0a21-8087-4f01-b8ae-5aa73b392d8f.png)

### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>Jakie jest ograniczenie nośnika magazynu wymiennego dla maksymalnej liczby usb?

Zweryfikowaliśmy jedną grupę USB ze 100 000 nośników o rozmiarze do 7 MB. Zasady działają zarówno w Intune, jak i w obiekcie zasad grupy bez problemów z wydajnością.

### <a name="why-does-the-policy-not-work"></a>Dlaczego zasady nie działają?

1. Najczęstszą przyczyną jest brak wymaganej [wersji klienta ochrony przed złośliwym kodem](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

2. Innym powodem może być to, że plik XML nie jest poprawnie sformatowany, na przykład nie używa poprawnego formatowania znacznika markdown dla znaku "&" w pliku XML lub edytor tekstów może dodać znak kolejności bajtów (BOM) 0xEF 0xBB 0xBF na początku plików, co powoduje, że analizowanie XML nie działa. Jednym z prostych rozwiązań jest pobranie [przykładowego pliku](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (wybierz pozycję **Nieprzetworzone** , a następnie **zapisz jako**), a następnie zaktualizowanie.

3. Jeśli wdrażasz zasady i zarządzasz nimi za pośrednictwem zasady grupy, upewnij się, że łączysz wszystkie reguły PolicyRule w jeden plik XML w węźle nadrzędnym o nazwie PolicyRules i wszystkie grupy w jeden plik XML w węźle nadrzędnym o nazwie Grupy. Jeśli zarządzasz za pośrednictwem Intune, zachowaj jeden plik XML PolicyRule, czyli jeden plik XML Grupuj jeden.

Jeśli nadal nie działa, możesz skontaktować się z nami i udostępnić kabinę pomocy technicznej, uruchamiając polecenie cmd z administratorem: "%programfiles%\Windows Defender\MpCmdRun.exe" -GetFiles

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Nie ma środowiska użytkownika konfiguracji dla opcji "Definiowanie grup zasad sterowania urządzeniami" i "Definiowanie reguł zasad sterowania urządzeniami" w zasady grupy

Nie tworzymy kopii zapasowej środowiska użytkownika konfiguracji zasady grupy, ale nadal możesz pobrać powiązane pliki adml i admx, klikając pozycje "Nieprzetworzone" i "Zapisz jako" w plikach [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) i [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx).

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>Skąd mogę wiedzieć, czy najnowsze zasady zostały wdrożone na maszynie docelowej?

Jako administrator możesz uruchomić polecenie "Get-MpComputerStatus" w programie PowerShell. Poniższa wartość pokaże, czy najnowsze zasady zostały zastosowane do maszyny docelowej.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>Skąd mogę wiedzieć, która maszyna używa nieaktualizowej wersji klienta ochrony przed złośliwym kodem w organizacji?

Następujące zapytanie umożliwia pobranie wersji klienta ochrony przed złośliwym kodem w portalu zabezpieczeń Microsoft 365:

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
