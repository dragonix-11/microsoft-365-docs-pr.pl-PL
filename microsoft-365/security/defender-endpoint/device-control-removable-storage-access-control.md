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
ms.date: 06/20/2022
ms.openlocfilehash: 78eb4f9cb65fb5eec54747a256abf290a43deb2f
ms.sourcegitcommit: af2b570e76e074bbef98b665b5f9a731350eda58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2022
ms.locfileid: "66185464"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Ochrona punktu końcowego w usłudze Microsoft Defender Storage Access Control wymienna kontrolki urządzenia

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

> [!NOTE]
> Zarządzanie zasady grupy i zarządzanie Intune OMA-URI/niestandardowe zarządzanie zasadami tego produktu są teraz ogólnie dostępne (4.18.2106): Zobacz [blog Tech Community: Ochrona wymiennego magazynu i drukarki za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

## <a name="device-control-removable-storage-access-control-overview"></a>Omówienie Storage Access Control wymiennych kontrolek urządzeń

Ochrona punktu końcowego w usłudze Microsoft Defender funkcja Storage Access Control wymiennego sterowania urządzeniami umożliwia przeprowadzanie inspekcji, zezwalanie na odczyt, zapis lub wykonywanie dostępu do magazynu wymiennego z wykluczeniem lub bez nich.

|Uprawnień|Uprawnienia|
|---|---|
|Access|Odczyt, zapis, wykonanie|
|Tryb akcji|Inspekcja, Zezwalaj, Zapobiegaj|
|Obsługa programu CSP|Tak|
|Obsługa obiektu zasad grupy|Tak|
|Obsługa oparta na użytkownikach|Tak|
|Obsługa oparta na maszynie|Tak|

Ochrona punktu końcowego w usłudze Microsoft Defender funkcja Storage Access Control wymiennego sterowania urządzeniami zapewnia następujące możliwości:

|Możliwości|Opis|Wdrażanie za pośrednictwem Intune|Wdrażanie za pośrednictwem zasady grupy|
|---|---|---|---|
|Tworzenie wymiennej grupy multimediów|Umożliwia tworzenie wymiennej grupy multimediów wielokrotnego użytku|Krok 4 i 6 w sekcji [Deploying Removable Storage Access Control by using Intune OMA-URI (Wdrażanie Storage Access Control wymiennych przy użyciu identyfikatora OMA-URI Intune](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| Krok 4 i 6 w sekcji [Wdrażanie wymiennych Storage Access Control przy użyciu zasady grupy](#deploying-removable-storage-access-control-by-using-group-policy)|
|Tworzenie zasad|Umożliwia tworzenie zasad wymuszania każdej wymiennej grupy multimediów|Krok 5 i 7 w sekcji [Deploying Removable Storage Access Control by using Intune OMA-URI (Wdrażanie wymiennych Storage Access Control przy użyciu identyfikatora OMA-URI Intune](#deploying-removable-storage-access-control-by-using-intune-oma-uri))| Kroki 5 i 7 w sekcji [Wdrażanie wymiennych Storage Access Control przy użyciu zasady grupy](#deploying-removable-storage-access-control-by-using-group-policy)|
|Domyślne wymuszanie|Umożliwia ustawienie domyślnego dostępu (Odmów lub Zezwalaj) na nośnik wymienny, jeśli nie ma żadnych zasad|Krok 2 w sekcji [Deploying Removable Storage Access Control by using Intune OMA-URI (Wdrażanie wymiennych Storage Access Control przy użyciu identyfikatora OMA-URI Intune](#deploying-removable-storage-access-control-by-using-intune-oma-uri) | Krok 2 w sekcji [Deploying Removable Storage Access Control by using zasady grupy (Wdrażanie wymiennych Storage Access Control przy użyciu zasady grupy](#deploying-removable-storage-access-control-by-using-group-policy)|
|Włączanie lub wyłączanie Storage Access Control wymiennych|Jeśli ustawisz opcję Wyłącz, spowoduje to wyłączenie zasad Storage Access Control wymiennych na tym komputerze| Krok 1 w sekcji [Deploying Removable Storage Access Control by using Intune OMA-URI (Wdrażanie wymiennych Storage Access Control przy użyciu Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri))| Krok 1 w sekcji [Wdrażanie wymiennych Storage Access Control przy użyciu zasady grupy](#deploying-removable-storage-access-control-by-using-group-policy)|
|Przechwytywanie informacji o pliku|Umożliwia tworzenie zasad w celu przechwytywania informacji o plikach w przypadku korzystania z dostępu do zapisu|  | Krok 10 w sekcji [Wdrażanie wymiennych Storage Access Control przy użyciu zasady grupy](#deploying-removable-storage-access-control-by-using-group-policy) |

### <a name="prepare-your-endpoints"></a>Przygotowywanie punktów końcowych

Wdróż Storage Access Control wymienne na urządzeniach Windows 10 i Windows 11, które mają klienta ochrony przed złośliwym kodem w wersji **4.18.2103.3 lub nowszej**.

- **4.18.2104 lub nowszy**: Dodaj identyfikator SerialNumberId, VID_PID, obsługę obiektów zasad grupy opartych na ścieżce plików, ComputerSid

- **4.18.2105 lub nowszy**: Dodaj obsługę symboli wieloznacznych dla hardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId, kombinacji określonego użytkownika na określonej maszynie, wymiennego dysku SSD (SanDisk Extreme SSD)/obsługa dołączonego interfejsu SCSI (UAS) usb

- **4.18.2107 lub nowszy**: dodaj obsługę Windows Portable Device (WPD) (dla urządzeń przenośnych, takich jak tablety), dodaj nazwę konta do [zaawansowanego wyszukiwania zagrożeń](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

:::image type="content" source="images/powershell.png" alt-text="Interfejs programu PowerShell" lightbox="images/powershell.png":::

> [!NOTE]
> Żaden ze składników Zabezpieczenia Windows nie musi być aktywny, ponieważ można uruchamiać Storage Access Control wymienne niezależnie od stanu Zabezpieczenia Windows.

## <a name="device-control-removable-storage-access-control-policies"></a>Zasady Storage Access Control wymiennych kontrolek urządzeń

Aby utworzyć grupę magazynu wymiennego, można użyć następujących właściwości:

> [!NOTE]
> Komentarze korzystające z notacji `<!-- COMMENT -->` komentarzy XML mogą być używane w plikach XML reguły i grupy, ale muszą znajdować się wewnątrz pierwszego tagu XML, a nie pierwszego wiersza pliku XML.

### <a name="removable-storage-group"></a>Wymienna grupa Storage

|Nazwa właściwości|Opis|Opcje|
|---|---|---|
|**Groupid**|Identyfikator GUID, unikatowy identyfikator, reprezentuje grupę i będzie używany w zasadach.||
|**DeskryptorIdList**|Wyświetl listę właściwości urządzenia, których chcesz użyć do pokrycia w grupie. Aby uzyskać więcej szczegółów, zobacz [Właściwości urządzenia](device-control-removable-storage-protection.md) dla każdej właściwości urządzenia. Wszystkie właściwości uwzględniają wielkość liter. |**PrimaryId**: `RemovableMediaDevices`, , `CdRomDevices``WpdDevices`<p>**BusId**: na przykład USB, SCSI<p>**Deviceid**<p>**HardwareId**<p>**InstancePathId**: InstancePathId to ciąg, który jednoznacznie identyfikuje urządzenie w systemie, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`na przykład . Numer na końcu (na przykład &0) reprezentuje dostępne miejsce i może ulec zmianie z urządzenia na urządzenie. Aby uzyskać najlepsze wyniki, użyj symbolu wieloznacznego na końcu. Na przykład `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: dopasuj tę dokładną parę VID/PID<p>`_55E0`: dopasuj dowolne nośniki do PID=55E0 <p>`0751_`: dopasuj dowolny nośnik do VID=0751|
|**Typ dopasowania**|W przypadku użycia wielu właściwości urządzenia w parametrze `DescriptorIDList`MatchType definiuje relację.|**MatchAll**: Wszystkie atrybuty w obszarze `DescriptorIdList` będą **i relacji** , na przykład, jeśli administrator stawia `DeviceID` i `InstancePathID`, dla każdego podłączonego USB, system sprawdzi, czy USB spełnia obie wartości. <p> **MatchAny**: atrybuty w obszarze DescriptorIdList będą mieć wartość **Lub** . Na przykład, jeśli administrator umieszcza `DeviceID` i `InstancePathID`, dla każdego podłączonego USB, system wykona wymuszanie tak długo, jak usb ma identyczną wartość **DeviceID** lub **InstanceID** .|

### <a name="access-control-policy"></a>zasady Access Control
Aby utworzyć zasady kontroli dostępu, można użyć następujących właściwości:

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

## <a name="device-control-removable-storage-access-control-scenarios"></a>Scenariusze Storage Access Control wymiennych kontrolek urządzeń

Aby ułatwić zapoznanie się z Ochrona punktu końcowego w usłudze Microsoft Defender wymiennymi Storage Access Control, przygotowaliśmy kilka typowych scenariuszy, które należy wykonać.

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

    2. Grupa 2: Niezatwierdzone bazy danych USB na podstawie właściwości urządzenia, na przykład identyfikator dostawcy / identyfikator produktu, przyjazna nazwa — grupa **65fa649a-a111-4912-9294-fb6337a25038** w przykładowym pliku [Group.xmlniezatwierdzone obiekty USBs](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > Zastąp `&` element `&amp;` wartością .

2. Tworzenie zasad

    1. Zasady 1: blokuj dostęp do zapisu i wykonywania dla wszystkich niezatwierdzone obiekty USB, ale blokuj je. Przykładem tego przypadku użycia jest: PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** w przykładowym [scenariuszu 2 Audit Write and Execute access to all but block specific unapproved USBs.xmlfile ( Reguła zasad 2 Inspekcja zapisu i wykonywania) do wszystkich niezatwierdzone USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) pliku.

    2. Zasady 2: Inspekcja dostępu do zapisu i wykonywania dla innych osób. Przykładem tego przypadku użycia jest: PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** w przykładowym [scenariuszu 2 Inspekcja zapisu i wykonywania dostępu do pliku others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

## <a name="deploying-and-managing-removable-storage-access-control-by-using-intune-oma-uri"></a>Wdrażanie Storage Access Control wymiennych i zarządzanie nimi przy użyciu identyfikatora OMA-URI Intune

Funkcja wymiennych Storage Access Control umożliwia stosowanie zasad przy użyciu identyfikatora OMA-URI do użytkownika lub urządzenia lub obu tych elementów.

### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Przed rozpoczęciem pracy z usługą Removable Storage Access Control musisz potwierdzić [subskrypcję Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Aby uzyskać dostęp do Storage Access Control wymiennych i korzystać z nich, musisz mieć Microsoft 365 E3 lub Microsoft 365 E5.

### <a name="permission"></a>Uprawnienia

W przypadku wdrażania zasad w Intune konto musi mieć uprawnienia do tworzenia, edytowania, aktualizowania lub usuwania profilów konfiguracji urządzeń. Możesz utworzyć role niestandardowe lub użyć dowolnej z wbudowanych ról z tymi uprawnieniami.

- Rola Menedżera zasad i profilu
- Rola niestandardowa z włączonymi uprawnieniami Utwórz/Edytuj/Aktualizuj/Odczyt/Usuń/Wyświetl raporty dla profilów konfiguracji urządzenia
- Administrator globalny

### <a name="deploying-removable-storage-access-control-by-using-intune-oma-uri"></a>Wdrażanie wymiennych Storage Access Control przy użyciu identyfikatora OMA-URI Intune

Przejdź do centrum administracyjnego Microsoft Endpoint Manager (<https://endpoint.microsoft.com/>) **> Urządzenia > Tworzenie profilu > Platform: Windows 10 i nowszych, Typ profilu: Szablony > Niestandardowe**

1. Włącz lub wyłącz wymienne Storage Access Control (RSAC):

   Można włączyć Storage Access Control wymienne w następujący sposób:

   - W obszarze **Ustawienia konfiguracji > niestandardowej** kliknij pozycję **Dodaj**.
   - W okienku **Dodawanie wiersza** wprowadź:
     - **Nazwa** jako **Włącz funkcję RSAC**
     - **Identyfikator OMA-URI** jako `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`
     - **Typ danych** jako **liczba całkowita**
     - **Wartość** **1**

       `Disable: 0`
       `Enable: 1`

     - Kliknij **Zapisz**.

   :::image type="content" source="images/enable-rsac.png" alt-text="Zrzut ekranu przedstawiający włączanie zasad Storage Access Control wymiennych" lightbox="images/enable-rsac.png":::

2. Ustaw domyślne wymuszanie:

   Możesz ustawić domyślny dostęp (Odmów lub Zezwalaj) na nośnik wymienny, jeśli nie ma żadnych zasad.

   Na przykład masz zasady Odmów lub Zezwalaj dla urządzeń RemovableMediaDevices, ale nie masz żadnych zasad dla urządzeń CdRomDevices lub WpdDevices. Za pomocą tych zasad ustawiono opcję Odmów domyślny, a następnie dostęp odczytu/zapisu/wykonywania do urządzeń CdRomDevices lub WpdDevices zostanie zablokowany.

   - W okienku **Dodawanie wiersza** wprowadź:
     - **Nazwa** jako **domyślna odmowa**
     - **Identyfikator OMA-URI** jako `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`
     - **Typ danych** jako **liczba całkowita**
     - **Wartość** **1** lub **2**

       `DefaultEnforcementAllow = 1`
       `DefaultEnforcementDeny = 2`

     - Kliknij **Zapisz**.

   :::image type="content" source="images/default-deny.png" alt-text="Zrzut ekranu przedstawiający ustawienie domyślnego wymuszania jako odmowy" lightbox="images/default-deny.png":::

3. Domyślna odmowa inspekcji:

   Zasady inspekcji dla domyślnego odmów można utworzyć w następujący sposób:

   - W okienku **Dodawanie wiersza** wprowadź:
     - **Nazwa** jako **Domyślna odmowa inspekcji**
     - **Identyfikator OMA-URI** jako `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf3520ea7-fd1b-4237-8ebc-96911db44f8e%7d/RuleData`

       :::image type="content" source="images/audit-default-deny-1.png" alt-text="Zrzut ekranu przedstawiający tworzenie domyślnych zasad odmowy inspekcji" lightbox="images/audit-default-deny-1.png":::

     - **Typ danych** jako **ciąg (plik XML)**
     - **Niestandardowy plik XML** jako domyślny plik **Deny.xmlinspekcji** .

       Ścieżka pliku XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20Default%20Deny.xml>

       Użyj następujących danych XML, aby utworzyć zasady inspekcji dla domyślnego odmów:

       :::image type="content" source="images/audit-default-deny-xml-file-1.png" alt-text="Zrzut ekranu przedstawiający domyślny plik XML odmowy inspekcji":::

4. ReadOnly — grupa:

   Grupę magazynu wymiennego można utworzyć z dostępem ReadOnly w następujący sposób:

   - W okienku **Dodawanie wiersza** wprowadź:
     - **Nazwa** **dowolnej grupy Storage wymiennych**
     - **Identyfikator OMA-URI** jako `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

       :::image type="content" source="images/any-removable-storage-group.png" alt-text="Zrzut ekranu przedstawiający tworzenie dowolnej grupy Storage wymiennych" lightbox="images/any-removable-storage-group.png":::

     - **Typ danych** jako **ciąg (plik XML)**
       - **Niestandardowy plik XML** jako **dowolny plik Storage wymienny i CD-DVD i WPD Group.xml**

         Ścieżka pliku XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Any%20Removable%20Storage%20and%20CD-DVD%20and%20WPD%20Group.xml>

         Użyj następujących danych XML, aby utworzyć "Dowolny wymienny Storage i CD-DVD i grupa WPD" z dostępem ReadOnly:

         :::image type="content" source="images/read-only-group-xml-file.png" alt-text="Zrzut ekranu przedstawiający plik XML grupy tylko do odczytu":::

5. ReadOnly — zasady:

   Możesz utworzyć zasady ReadOnly i zastosować je do grupy magazynów wymiennych ReadOnly, aby zezwolić na działanie odczytu w następujący sposób:

   - W okienku **Dodawanie wiersza** wprowadź:
     - **Nazwa** jako **Zezwalaj na działanie odczytu**
     - **Identyfikator OMA-URI** jako `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf7e75634-7eec-4e67-bec5-5e7750cb9e02%7d/RuleData`

       :::image type="content" source="images/allow-read-activity.png" alt-text="Zrzut ekranu przedstawiający zasady zezwalania na działanie odczytu" lightbox= "images/allow-read-activity.png":::

     - **Typ danych** jako **ciąg (plik XML)**
     - **Niestandardowy plik XML** jako **zezwalaj na plik Read.xml**

       Ścieżka pliku XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20Read.xml>

       Użyj następujących danych XML, aby utworzyć zasady ReadOnly i zastosować je do grupy magazynów wymiennych ReadOnly:

       :::image type="content" source="images/read-only-policy-xml-file.png" alt-text="Zrzut ekranu przedstawiający plik XML zasad tylko do odczytu":::

6. Utwórz grupę dla dozwolonych nośników: możesz utworzyć dozwoloną grupę multimediów w następujący sposób:
   - W okienku **Dodawanie wiersza** wprowadź:
     - **Nazwa** grupy **zatwierdzonych baz danych USB**
     - **Identyfikator OMA-URI** jako `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b65fa649a-a111-4912-9294-fb6337a25038%7d/GroupData`

       :::image type="content" source="images/create-group-allowed-medias.png" alt-text="Zrzut ekranu przedstawiający tworzenie zatwierdzonej grupy usb" lightbox="images/create-group-allowed-medias.png":::

     - **Typ danych** jako **ciąg (plik XML)**
     - **Niestandardowy kod XML** jako **zatwierdzony plik Group.xmlusb**

       Ścieżka pliku XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Approved%20USBs%20Group.xml>

       Użyj następujących danych XML, aby utworzyć dozwoloną grupę multimediów:

       :::image type="content" source="images/create-group-allowed-medias-xml-file.png" alt-text="Zrzut ekranu przedstawiający tworzenie grupy dla pliku XML dozwolonych multimediów":::

7. Utwórz zasady zezwalające na zatwierdzoną grupę USB: możesz utworzyć zasady zezwalające na zatwierdzoną grupę USB w następujący sposób:
   - W okienku **Dodawanie wiersza** wprowadź:
     - **Nazwa** jako **Zezwalaj na dostęp i Informacje o pliku inspekcji**
     - **Identyfikator OMA-URI** jako `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bb2061588-029e-427d-8404-6dfec096a571%7d/RuleData`

       :::image type="content" source="images/allow-access-audit-file-information-1.png" alt-text="Zrzut ekranu przedstawiający informacje o pliku zezwalania na dostęp i inspekcji" lightbox= "images/allow-access-audit-file-information-1.png":::

     - **Typ danych** jako **ciąg (plik XML)**
     - **Niestandardowy kod XML** jako **Zezwalaj na pełny dostęp i inspekcję pliku file.xml**

       Ścieżka pliku XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20full%20access%20and%20audit%20file.xml>

       Użyj następujących danych XML, aby utworzyć zasady zezwalające na zatwierdzoną grupę USB:

       :::image type="content" source="images/create-policy-allow-approved-usb-group-xml-intune.png" alt-text="Zrzut ekranu przedstawiający tworzenie zasad zezwalania na zatwierdzony plik XML grupy USB":::

       Co oznacza "47" w zasadach? Jest to 9 + 2 + 36 = 47:

       - Dostęp do odczytu: 1 + 8 = 9.
       - Dostęp do zapisu: poziom dysku 2.
       - Wykonaj: 4 + 32 = 36.

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Wdrażanie zasad i zarządzanie nimi przy użyciu interfejsu użytkownika Intune

Ta funkcja jest dostępna w centrum administracyjnym Microsoft Endpoint Manager (<https://endpoint.microsoft.com/>). Przejdź do obszaru Tworzenie **zasad tworzenia** obszaru **podatnego** >  **na ataki zabezpieczeń** >  punktu końcowego. Wybierz **pozycję Platforma: Windows 10 i nowsze** z **opcją Profil: Kontrola urządzenia**.

## <a name="deploying-and-managing-removable-storage-access-control-by-using-group-policy"></a>Wdrażanie Storage Access Control wymiennych i zarządzanie nimi przy użyciu zasady grupy

Funkcja wymiennych Storage Access Control umożliwia stosowanie zasad przy użyciu zasady grupy do użytkownika lub urządzenia lub obu tych elementów.

### <a name="licensing"></a>Licencjonowanie

Przed rozpoczęciem pracy z usługą Removable Storage Access Control musisz potwierdzić [subskrypcję Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Aby uzyskać dostęp do Storage Access Control wymiennych i korzystać z nich, musisz mieć Microsoft 365 E3 lub Microsoft 365 E5.

### <a name="deploying-removable-storage-access-control-by-using-group-policy"></a>Wdrażanie Storage Access Control wymiennych przy użyciu zasady grupy

1. Włącz lub wyłącz Storage Access Control wymienne:

   Funkcję Wymienne Storage Access Control (RSAC) można włączyć w następujący sposób:

   - Przejdź do pozycji **Konfiguracja komputera > szablony administracyjne > Windows składniki > Program antywirusowy Microsoft Defender > funkcje > kontrolki urządzenia**
   - W oknie **Kontrola urządzenia** wybierz pozycję **Włączone**.

   :::image type="content" source="images/enable-rsac-gp.png" alt-text="Zrzut ekranu przedstawiający włączanie funkcji RSAC przy użyciu zasady grupy " lightbox="images/enable-rsac-gp.png":::

2. Ustaw domyślne wymuszanie:

   Możesz ustawić domyślny dostęp (Odmów lub Zezwalaj) na nośnik wymienny, jeśli nie ma żadnych zasad w następujący sposób:

   - Przejdź do pozycji **Konfiguracja komputera > Szablony administracyjne > Windows składniki > Program antywirusowy Microsoft Defender > funkcje > kontrolce urządzenia > wybierz domyślne wymuszanie kontroli urządzenia**

   - W oknie **Wybieranie domyślnego wymuszania kontrolki urządzenia** wybierz opcję **Odmów domyślny**:

   :::image type="content" source="images/set-default-enforcement-deny-gp.png" alt-text="Zrzut ekranu przedstawiający ustawienie domyślne wymuszanie = odmowa przy użyciu zasady grupy" lightbox="images/set-default-enforcement-deny-gp.png":::

3. Domyślna odmowa inspekcji:

   Użyj następujących danych XML, aby utworzyć zasady inspekcji dla domyślnego odmów:

   :::image type="content" source="images/audit-default-deny-gp.png" alt-text="Zrzut ekranu przedstawiający domyślne dane xml odmowy inspekcji":::

4. ReadOnly — grupa:

   Użyj następujących danych XML, aby utworzyć grupę magazynu wymiennego z dostępem ReadOnly:

   :::image type="content" source="images/read-only-group-gp.png" alt-text="Zrzut ekranu przedstawiający dane XML grupy magazynów wymiennych tylko do odczytu":::

5. ReadOnly — zasady:

   Użyj następujących danych XML, aby utworzyć zasady ReadOnly i zastosować je do grupy magazynów wymiennych ReadOnly, aby zezwolić na działanie odczytu:

    :::image type="content" source="images/read-only-policy-gp.png" alt-text="Zrzut ekranu przedstawiający dane XML zasad tylko do odczytu" lightbox="images/read-only-policy-gp.png":::

6. Utwórz grupę dla dozwolonych nośników:

   Użyj następujących danych XML, aby utworzyć grupę nośników dozwolonych dla magazynu wymiennego:

   :::image type="content" source="images/create-group-allowed-medias-gp.png" alt-text="Zrzut ekranu przedstawiający dane XML służące do tworzenia grupy dla dozwolonych nośników" lightbox="images/create-group-allowed-medias-gp.png":::

7. Utwórz zasady zezwalające na zatwierdzoną grupę USB:

   Użyj następujących danych XML, aby utworzyć zasady zezwalające na zatwierdzoną grupę USB:

   :::image type="content" source="images/create-policy-allow-approved-usb-group-xml.png" alt-text="Zrzut ekranu przedstawiający dane XML umożliwiające utworzenie zasad zezwalania zatwierdzonej grupie USB przy użyciu zasady grupy" lightbox="images/create-policy-allow-approved-usb-group-xml.png":::

   Co oznacza "47" w zasadach? Jest to 9 + 2 + 36 = 47:

   - Dostęp do odczytu: 1+8 = 9.
   - Dostęp do zapisu: poziom dysku 2.
   - Wykonaj: 4 + 32 = 36.

8. Połącz grupy w jeden plik XML:

   Grupy zasad sterowania urządzeniami można połączyć w jeden plik XML w następujący sposób:

   - Przejdź do pozycji **Konfiguracja** \> komputera **Szablony** \> administracyjne **Windows Składniki** \> **Program antywirusowy Microsoft Defender** \> **Kontrolka** \> **urządzenia Zdefiniuj grupy zasad sterowania urządzeniami**.

    :::image type="content" source="images/define-device-control-policy-grps-gp.png" alt-text="Zrzut ekranu przedstawiający definiowanie grup zasad sterowania urządzeniami" lightbox="images/define-device-control-policy-grps-gp.png":::

   - W oknie **Definiowanie grup zasad sterowania urządzeniami** wprowadź ścieżkę pliku zawierającą dane grup XML.

     Ścieżka pliku XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Groups.xml>

     Poniżej przedstawiono schemat xml grup zasad sterowania urządzeniami:

     :::image type="content" source="images/combine-grps-xml-file-gp.png" alt-text="Zrzut ekranu przedstawiający łączenie grup w jeden plik XML":::

9. Połącz zasady w jeden plik XML:

   Reguły zasad sterowania urządzeniami można połączyć w jeden plik XML w następujący sposób:

   - Przejdź do pozycji **Konfiguracja komputera > Szablony administracyjne > Windows Składniki > Program antywirusowy Microsoft Defender > Kontrolka urządzenia > Definiowanie reguł zasad sterowania urządzeniami**

     :::image type="content" source="images/define-device-cntrl-policy-rules-gp.png" alt-text="Zrzut ekranu przedstawiający definiowanie reguł zasad sterowania urządzeniami" lightbox="images/define-device-cntrl-policy-rules-gp.png":::

   - W oknie **Definiowanie reguł zasad sterowania urządzeniami** wybierz pozycję **Włączone** i wprowadź ścieżkę pliku zawierającą dane reguł XML.

     Ścieżka pliku XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Policies.xml>

     Poniżej przedstawiono schemat xml reguł zasad sterowania urządzeniami:

    :::image type="content" source="images/combine-policies-xml-gp.png" alt-text="Zrzut ekranu przedstawiający łączenie zasad w jeden plik XML":::

10. Ustaw lokalizację kopii pliku (dowód):

    Jeśli chcesz mieć kopię pliku (dowody) podczas dostępu do zapisu, musisz ustawić lokalizację, w której system może zapisać kopię.

    - Przejdź do **obszaru Konfiguracja komputera > Szablony administracyjne > Windows Składniki > Program antywirusowy Microsoft Defender > Kontrolka urządzenia > Zdefiniuj zdalną lokalizację danych dowodowych kontrolki urządzenia**.

    - W oknie **Definiowanie zdalnej lokalizacji danych dowodowych kontrolki urządzenia** wybierz pozycję **Włączone** i wprowadź ścieżkę folderu udziału lokalnego lub sieciowego.

      :::image type="content" source="images/evidence-data-remote-location-gp.png" alt-text="Zrzut ekranu przedstawiający zdalną lokalizację danych dowodowych definiowania kontrolki urządzenia" lightbox="images/evidence-data-remote-location-gp.png":::

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

### <a name="what-are-the-removable-storage-media-and-policy-limitations"></a>Jakie są ograniczenia dotyczące wymiennych nośników magazynu i zasad?

W centrum administracyjnym Microsoft Endpoint Manager (Intune) lub za pośrednictwem interfejs Graph API firmy Microsoft wywołanie zaplecza odbywa się za pośrednictwem identyfikatora OMA-URI (pobierz do odczytu lub poprawki w celu zaktualizowania), a zatem ograniczenie jest takie samo jak dowolny niestandardowy profil konfiguracji OMA-URI w firmie Microsoft, który oficjalnie zawiera 350 000 znaków dla plików XML.

Na przykład jeśli potrzebujesz dwóch bloków wpisów na identyfikator SID użytkownika do "Zezwalaj"/"Inspekcja dozwolonych" określonych użytkowników i dwóch bloków wpisów na końcu "Odmów" wszystkim, będziesz mógł zarządzać 2276 użytkownikami.

### <a name="why-does-the-policy-not-work"></a>Dlaczego zasady nie działają?

1. Najczęstszą przyczyną jest brak wymaganej [wersji klienta ochrony przed złośliwym kodem](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

2. Innym powodem może być to, że plik XML nie jest poprawnie sformatowany, na przykład nie używa poprawnego formatowania znacznika markdown dla znaku "&" w pliku XML lub edytor tekstów może dodać znak kolejności bajtów (BOM) 0xEF 0xBB 0xBF na początku plików, co powoduje, że analizowanie XML nie działa. Jednym z prostych rozwiązań jest pobranie [przykładowego pliku](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (wybierz pozycję **Nieprzetworzone** , a następnie **zapisz jako**), a następnie zaktualizowanie.

3. Jeśli wdrażasz zasady i zarządzasz nimi przy użyciu zasady grupy, pamiętaj, aby połączyć wszystkie reguły PolicyRule w jeden plik XML w węźle nadrzędnym o nazwie PolicyRules i wszystkie grupy w jeden plik XML w węźle nadrzędnym o nazwie Grupy; jeśli zarządzasz za pośrednictwem Intune, zachowaj jeden plik XML PolicyRule, czyli jeden plik XML Grupuj jeden.

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
