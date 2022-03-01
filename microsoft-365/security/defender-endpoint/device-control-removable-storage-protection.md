---
title: Program Microsoft Defender for Endpoint Device Control Removable Storage Protection
description: Opis funkcji, które pomagają uniemożliwić użytkownikowi lub komputerowi korzystanie z nieautoryzowanego nośnika magazynu wymiennych
keywords: nośnik magazynu wymiennych
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: cc1c2a5fc05b795c0fc69ebc8a3b50dbf556960b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997854"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Program Microsoft Defender for Endpoint Device Control Removable Storage Protection


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Ochrona magazynu urządzenia kontrolą wymienną w programie Microsoft Defender dla punktu końcowego uniemożliwia użytkownikom, punktom końcowym i/lub innym osobom korzystanie z nieautoryzowanego nośnika magazynu wymiennych.

## <a name="protection-policies"></a>Zasady ochrony

### <a name="removable-storage-access-control"></a>Kontrolka dostępu do magazynu wymiennych

**Możliwości**

- *Inspekcja* Odczyt, pisanie lub wykonywanie dostępu do magazynu wymiennych na podstawie różnych właściwości urządzenia z wyłączeniem lub wyłączeniem.
- *Zapobiegaj* Odczyt, pisanie lub wykonywanie dostępu z wykluczeniem lub bez nich — zezwalanie na określone urządzenie na podstawie różnych właściwości urządzenia.

**Windows 10 i Windows 11 szczegółów pomocy technicznej**:

- Stosowane na poziomie urządzenia, na poziomie użytkownika. lub oba. Zezwalaj tylko określonym osobom na wykonywanie operacji odczytu/zapisu/wykonywania na określonym magazynie wymiennym na określonym komputerze.
- Obsługa MEM OMA-URI i zasad GPO.
- Obsługiwane są ["Właściwości](#device-properties) urządzenia" zgodnie z ich ustawieniami.
- Aby uzyskać informacje na temat Windows wymiennych [kontrolek dostępu do magazynu.](device-control-removable-storage-access-control.md)

**Obsługiwana platforma** — Windows 10, Windows 11

**Szczegóły pomocy technicznej dla systemu macOS**:

- Stosowane na poziomie urządzenia: te same zasady mają zastosowanie do każdego zalogowanego użytkownika.
- Aby uzyskać informacje dotyczące systemu macOS, zobacz [Sterowanie urządzeniem dla systemu macOS](mac-device-control-overview.md).

**Obsługiwana platforma** — system macOS Catalina 10.15.4+ (z włączonymi rozszerzeniami systemu)


### <a name="device-installation"></a>Instalacja urządzenia

**Możliwości** — zapobieganie instalacji z wyłączeniem lub z wyłączeniem na podstawie różnych właściwości urządzenia.

**Windows 10 i Windows 11 szczegółów pomocy technicznej**:

- Stosowane na poziomie urządzenia: te same zasady mają zastosowanie do każdego zalogowanego użytkownika.
- Obsługuje Microsoft Endpoint Manager i zasady grupy obiektów.
- Obsługiwane są ["Właściwości](#device-properties) urządzenia" zgodnie z ich ustawieniami.
- Aby uzyskać więcej informacji na Windows, zobacz Jak sterować urządzeniami USB i innymi nośnikami [wymiennymi za pomocą programu Microsoft Defender for Endpoint](control-usb-devices-using-intune.md).

**Obsługiwana platforma** — Windows 10, Windows 11

**Szczegóły pomocy technicznej dla systemu macOS**:

- Zastosowane na poziomie urządzenia: te same zasady mają zastosowanie do każdego zalogowanego użytkownika
- Aby uzyskać informacje dotyczące systemu macOS, zobacz [Sterowanie urządzeniem dla systemu macOS](mac-device-control-overview.md).

**Obsługiwana platforma** — system macOS Catalina 10.15.4+ (z włączonymi rozszerzeniami systemu) lub nowszy

### <a name="endpoint-dlp-removable-storage"></a>Magazyn wymienny DLP punktu końcowego

**Możliwości** — inspekcja, ostrzeganie lub uniemożliwianie użytkownikowi kopiowania elementu lub informacji na nośnik wymienny lub urządzenie USB.

**Opis** — aby uzyskać więcej informacji na temat Windows, zobacz [Informacje Microsoft 365 ochrony przed utratą danych w punktach końcowych](../../compliance/endpoint-dlp-learn-about.md).

**Obsługiwana platforma** — Windows 10, Windows 11

### <a name="bitlocker"></a>BitLocker

**Możliwości**:

- Blokuj dane, które mają być zapisywane na dyskach wymiennych, które nie są chronione funkcją BitLocker.
- Blokowanie dostępu do dysków wymiennych, chyba że zostały zaszyfrowane na komputerze należącym do Twojej organizacji

**Opis** — aby uzyskać więcej informacji na temat funkcji Windows, zobacz [BitLocker — dysk wymienny Ustawienia](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Obsługiwana platforma** — Windows 10, Windows 11

## <a name="device-properties"></a>Właściwości urządzenia

Program Microsoft Defender for Endpoint Device Control Removable Storage Protection umożliwia ograniczenie dostępu do magazynu wymiennych w oparciu o właściwości opisane w poniższej tabeli:

<br/><br/>

|Nazwa właściwości|Odpowiednie zasady|Dotyczy systemów operacyjnych|Opis|
|---|---|---|---|
|Klasa urządzenia|[Jak sterować urządzeniami USB i innymi nośnikami wymiennymi przy użyciu programu Microsoft Defender for Endpoint](control-usb-devices-using-intune.md)|System Windows|Aby uzyskać informacje na temat formatów identyfikatora urządzenia, zobacz [Klasa konfiguracji urządzenia](/windows-hardware/drivers/install/overview-of-device-setup-classes). Dwa poniższe linki zawierają pełną listę klas konfiguracji urządzenia. Klasy "System Use" dotyczą głównie urządzeń, które pochodzą z fabrycznego komputera/komputera, natomiast klasy "Dostawca" dotyczą głównie urządzeń, które mogą być połączone z istniejącym komputerem/komputerem: Zdefiniowane przez system zajęcia konfiguracji urządzeń dostępne dla dostawców [— sterowniki Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) i Klasy konfiguracji urządzeń zdefiniowane przez system zarezerwowane do użycia przez system [— Windows sterowniki](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use). **Uwaga**: Instalację urządzenia można stosować do dowolnych urządzeń, nie tylko do magazynu wymiennych.|
|Identyfikator podstawowy|[Kontrolka programu Access dla magazynu wymiennych](device-control-removable-storage-access-control.md)|System Windows|Identyfikator podstawowy zawiera nośnik wymienny, dysk CD/DVD i Windows Portable Device/WPD.|
|Identyfikator urządzenia|[Kontrolka programu Access dla magazynu wymiennych](device-control-removable-storage-access-control.md); <p> [Jak sterować urządzeniami USB i innymi nośnikami wymiennymi przy użyciu programu Microsoft Defender for Endpoint](control-usb-devices-using-intune.md)|System Windows|Aby uzyskać informacje na temat formatów identyfikatorów urządzeń, zobacz Standardowe identyfikatory [USB](/windows-hardware/drivers/install/standard-usb-identifiers), na przykład USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07.|
|Identyfikator sprzętu|[Kontrolka programu Access dla magazynu wymiennych](device-control-removable-storage-access-control.md) <p> [Jak sterować urządzeniami USB i innymi nośnikami wymiennymi przy użyciu programu Microsoft Defender for Endpoint](control-usb-devices-using-intune.md)|System Windows|Ciąg zidentyfikował urządzenie w systemie, na przykład USBSTOR\DiskGeneric_Flash_Disk___8.07; **Uwaga**: Identyfikator sprzętu nie jest unikatowy. różne urządzenia mogą mieć taką samą wartość.|
|Identyfikator wystąpienia|[Kontrolka programu Access dla magazynu wymiennych](device-control-removable-storage-access-control.md) <p> Instalacja urządzenia|System Windows|Ciąg jednoznacznie identyfikuje urządzenie w systemie, na przykład USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|Przyjazna nazwa|[Kontrolka programu Access dla magazynu wymiennych](device-control-removable-storage-access-control.md)|System Windows|Ciąg dołączony do urządzenia, na przykład Generic Flash Disk USB Device|
|Identyfikator dostawcy / identyfikator produktu|[Kontrolka programu Access dla magazynu wymiennych](device-control-removable-storage-access-control.md)|System Windows <p> macOS|Identyfikator dostawcy to czterocyfrowy kod dostawcy przypisany mu przez komitet USB. Identyfikator produktu to czterocyfrowy kod produktu przypisany przez dostawcę do urządzenia. Symbol wieloznaczny Pomocy technicznej.|
|Numer seryjny|[Kontrolka programu Access dla magazynu wymiennych](device-control-removable-storage-access-control.md)|System Windows <p> macOS |Na przykład <SerialNumberId>: 002324B534BCB431B000058A</SerialNumberId>|
