---
title: Microsoft Defender for Endpoint Device Control Printer Protection
description: Program Microsoft Defender for Endpoint Device Control Printer Protection blokuje drukowanie przez drukarki USB, które nie są firmowe lub niezatwierdzoną drukarką.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: dansimp
author: lovina-saldanha
ms.reviewer: dansimp
manager: dansimp
audience: ITPro
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 496d9bf729eaaff6cf12e9734ae80eedacf98a63
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019278"
---
# <a name="device-control-printer-protection"></a>Ochrona drukarki sterowania urządzeniem

**Dotyczy**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Program Microsoft Defender for Endpoint Device Control Printer Protection blokuje drukowanie przez drukarki USB, które nie są firmowe lub niezatwierdzoną drukarką.

## <a name="licensing"></a>Licencjonowanie

Przed rozpoczęciem pracy z usługą Ochrona drukarki należy potwierdzić [subskrypcję Microsoft 365 drukarki](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). Aby uzyskać dostęp do ochrony drukarki i korzystać z niego, musisz mieć następujące ustawienia:

- Microsoft 365 E3 funkcji/wdrożenia zasad
- Microsoft 365 E5 do raportowania

## <a name="permission"></a>Uprawnienie

W przypadku wdrażania zasad w usłudze Intune w celu wdrożenia zasad za pośrednictwem interfejsu OMA-URI konto musi mieć uprawnienia do tworzenia, edytowania, aktualizowania i usuwania profilów konfiguracji urządzeń. Możesz utworzyć role niestandardowe lub użyć dowolnej z wbudowanych ról z tymi uprawnieniami:

- Rola Menedżera zasad i profilu.
- Lub rola niestandardowa z włączonymi uprawnieniami Tworzenie/Edycja/Aktualizacja/Odczyt/Usuwanie/Wyświetlanie raportów dla profilów konfiguracji urządzenia
- Lub administrator globalny

Aby wyświetlić raporty o konfiguracji urządzenia, konto musi mieć uprawnienia do wyświetlania raportów. Możesz tworzyć role niestandardowe lub używać wbudowanych ról z tymi uprawnieniami:

- Administrator globalny zabezpieczeń
- Administrator zabezpieczeń
- Czytnik zabezpieczeń

## <a name="prepare-your-endpoints"></a>Przygotowywanie punktów końcowych

Upewnij się, że Windows 10 lub Windows 11 urządzeń, które planujesz wdrożyć ochronę drukarki, aby spełnić te wymagania.

1. Następujące aktualizacje Windows są zainstalowane.
    - Dla Windows 1809: instalowanie Windows [KB5003217](https://support.microsoft.com/topic/may-20-2021-kb5003217-os-build-17763-1971-preview-08687c95-0740-421b-a205-54aa2c716b46)
    - Dla Windows 1909: instalowanie Windows [KB5003212](https://support.microsoft.com/topic/may-20-2021-kb5003212-os-build-18363-1593-preview-05381524-8380-4b30-b783-e330cad3d4a1)
    - Dla Windows 2004 lub nowszego

2. Jeśli planujesz wdrożenie zasad za pośrednictwem programu zasady grupy, urządzenie musi być połączone z programem Microsoft Defender for Endpoint. jeśli zamierzasz wdrożyć zasady za pośrednictwem Microsoft Endpoint Manager, urządzenie musi zostać połączone przy użyciu aplikacji Microsoft Intune.

## <a name="deploy-device-control-printer-protection-policy"></a>Wdrażanie zasad ochrony drukarki kontrolek urządzeń

Zasady możesz wdrożyć za pośrednictwem zasady grupy Lub Intune.

<br>

****

|Tytuł|Opis|Pomoc techniczna CSP | Obsługa zasad grupy | Pomoc techniczna oparta na użytkownikach | Obsługa maszynowa |
|---|---|:---:|:---:|:---:|:---:|
|**Włącz ograniczenia drukowania sterowania urządzeniem**|Blokowanie drukowania za pomocą drukarki nie firmowej|Tak|Tak|Tak|Tak|
|**Lista zatwierdzonych urządzeń do drukowania połączonych przez USB**\*|Zezwalaj na określoną drukarkę USB|Tak|Tak|Tak|Tak|
|

\* Te zasady muszą być używane razem z **ograniczeniami drukowania Włącz sterowanie urządzeniem**.

## <a name="deploy-policy-via-intune"></a>Wdrażanie zasad za pośrednictwem usługi Intune

W przypadku usługi Intune ochrona drukarki sterowania urządzeniem obsługuje tylko OMA-URI.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-intune"></a>Scenariusz 1. Blokowanie drukowania przez osoby za pośrednictwem dowolnej drukarki nie firmowej za pomocą usługi Intune

- Stosowanie zasad na komputerze:

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControl`

- Stosowanie zasad do użytkowników:

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControlUser`

Ciąg obsługi języka CSP z:`<enabled/>`

:::image type="content" source="../../media/customeditrow.png" alt-text="niestandardowy wiersz edycji.":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-intune"></a>Scenariusz 2. Zezwalanie na określone zatwierdzone drukarki USB przy użyciu usługi Intune

- Stosowanie zasad na komputerze:

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevices`

- Stosowanie zasad do użytkowników:

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevicesUser`

Ciąg obsługi formatu CSP z zatwierdzonymi drukarkami USB za pośrednictwem właściwości "ApprovedUsbPrintDevices", na przykład `<enabled><data id="ApprovedUsbPrintDevices_List" value="03F0/0853,0351/0872"/>`:

:::image type="content" source="../../media/editrow.png" alt-text="edytuj wiersz.":::

## <a name="deploy-policy-via-group-policy"></a>Wdrażanie zasad za pośrednictwem zasady grupy

Jeśli urządzenie nie jest przyłączone do usługi Intune, możesz także wdrożyć zasady za pośrednictwem zasady grupy.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-group-policy"></a>Scenariusz 1. Blokowanie drukowania za pośrednictwem jakichkolwiek drukarek niesąpornych przy użyciu zasady grupy

- Stosowanie zasad na komputerze:

  Drukarka szablonów administracyjnych \> konfiguracji komputera \> : włącz ograniczenia drukowania sterowania urządzeniem

- Stosowanie zasad do użytkowników:

  Drukarki w szablonach \> administracyjnych \> konfiguracji \> użytkownika: Włącz ograniczenia drukowania sterowania urządzeniem

:::image type="content" source="../../media/enable-device-ctrl-printing-restrictions.png" alt-text="włącz ograniczenia drukowania na urządzeniach.":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-group-policy"></a>Scenariusz 2. Zezwalanie na określone zatwierdzone drukarki USB przy użyciu zasady grupy

- Stosowanie zasad na komputerze:

  Drukarka szablonów administracyjnych \> konfiguracji \> komputera: lista zatwierdzonych urządzeń drukujących połączonych przez USB

- Stosowanie zasad do użytkowników:

  Drukarki z \> szablonami administracyjnymi \> konfiguracji \> użytkownika: lista zatwierdzonych urządzeń drukujących połączonych przez USB

:::image type="content" source="../../media/list-of-approved-connected-print-devices.png" alt-text="listę zatwierdzonych urządzeń do drukowania połączonych przez USB.":::

## <a name="view-device-control-printer-protection-data-in-microsoft-defender-for-endpoint-portal"></a>Wyświetlanie danych ochrony drukarki sterowania urządzeniem w portalu programu Microsoft Defender dla punktu końcowego

Portal <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender zawiera</a> informacje o drukowaniu zablokowanym przez powyższe zasady ochrony drukarki kontrolki urządzenia.

```kusto
DeviceEvents
| where ActionType == 'PrintJobBlocked'
| extend parsed=parse_json(AdditionalFields)
| extend PrintedFile=tostring(parsed.JobOrDocumentName)
| extend PrintPortName=tostring(parsed.PortName)
| extend PrinterName=tostring(parsed.PrinterName)
| extend Policy=tostring(parsed.RestrictionReason) 
| project Timestamp, DeviceId, DeviceName, ActionType, InitiatingProcessAccountName, Policy, PrintedFile, PrinterName, PrintPortName, AdditionalFields
| order by Timestamp desc
```

 :::image type="content" source="../../media/device-control-advanced-hunting.png" alt-text="zaawansowane myśliwce.":::

 Przy użyciu zdarzenia PnP można znaleźć drukarkę USB używaną w organizacji:

```kusto
//find the USB Printer VID/PID
DeviceEvents
| where ActionType == "PnpDeviceConnected"
| extend parsed=parse_json(AdditionalFields)
| extend DeviceDescription = tostring(parsed.DeviceDescription) 
| extend PrinterDeviceId = tostring(parsed.DeviceId) 
| extend VID_PID_Array = split(split(PrinterDeviceId, "\\")[1], "&")
| extend VID_PID = replace_string(strcat(VID_PID_Array[0], '/', VID_PID_Array[1]), 'VID_', '')
| extend VID_PID = replace_string(VID_PID, 'PID_', '')
| extend ClassId = tostring(parsed.ClassId) 
| extend VendorIds = tostring(parsed.VendorIds) 
| where DeviceDescription == 'USB Printing Support'
| project Timestamp , DeviceId, DeviceName, ActionType, DeviceDescription, VID_PID, ClassId, PrinterDeviceId, VendorIds, parsed
| order by Timestamp desc
```

 :::image type="content" source="https://user-images.githubusercontent.com/81826151/128954383-71df3009-77ef-40db-b575-79c73fda332b.png" alt-text="zaawansowane szukanie":::
