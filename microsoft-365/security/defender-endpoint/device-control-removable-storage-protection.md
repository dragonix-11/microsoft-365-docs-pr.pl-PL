---
title: Ochrona punktu końcowego w usłudze Microsoft Defender ochrony Storage wymiennej kontrolki urządzenia
description: Zapoznaj się z możliwościami, które pomagają uniemożliwić użytkownikom lub komputerom korzystanie z nieautoryzowanych wymiennych nośników magazynu
keywords: wymienny nośnik magazynu
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
ms.openlocfilehash: 5210530bb9102436e66667a0482aa09d941e26f9
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939416"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Ochrona punktu końcowego w usłudze Microsoft Defender ochrony Storage wymiennej kontrolki urządzenia


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Ochrona magazynu wymiennego sterowania urządzeniami w Ochrona punktu końcowego w usłudze Microsoft Defender uniemożliwia użytkownikom, punktom końcowym lub obu osobom korzystanie z nieautoryzowanych wymiennych nośników magazynu.

## <a name="protection-policies"></a>Zasady ochrony

### <a name="removable-storage-access-control"></a>Kontrola dostępu do magazynu wymiennego

**Możliwości**

- *Inspekcji* Dostęp do odczytu lub zapisu lub wykonywania do magazynu wymiennego na podstawie różnych właściwości urządzenia z wykluczeniem lub bez.
- *Zapobiec* Dostęp do odczytu lub zapisu lub wykonywania z wykluczeniem lub bez nich — zezwalaj na określone urządzenie na podstawie różnych właściwości urządzenia.

**szczegóły pomocy technicznej Windows 10 i Windows 11**:

- Stosowane na poziomie urządzenia, na poziomie użytkownika. lub obu tych elementów. Zezwalaj tylko określonym osobom wykonującym dostęp do odczytu/zapisu/wykonywania do określonego magazynu wymiennego na określonej maszynie.
- Obsługa identyfikatora OMA-URI i obiektu zasad grupy MEM.
- Obsługiwane "[Właściwości urządzenia](#device-properties)" na liście.
- Aby uzyskać informacje o funkcji w Windows, zobacz [Access Control magazynu wymiennego](device-control-removable-storage-access-control.md).

**Obsługiwana platforma** — Windows 10, Windows 11

**Szczegóły pomocy technicznej systemu macOS**:

- Stosowane na poziomie urządzenia: te same zasady mają zastosowanie do każdego zalogowanego użytkownika.
- Aby uzyskać informacje o konkretnym systemie macOS, zobacz [Kontrola urządzenia dla systemu macOS](mac-device-control-overview.md).

**Obsługiwana platforma** — macOS Catalina 10.15.4+ (z włączonymi rozszerzeniami systemowymi)


### <a name="device-installation"></a>Instalacja urządzenia

**Możliwości** — zapobiegaj instalacji z wykluczeniem lub bez wykluczeń na podstawie różnych właściwości urządzenia.

**szczegóły pomocy technicznej Windows 10 i Windows 11**:

- Stosowane na poziomie urządzenia: te same zasady mają zastosowanie do każdego zalogowanego użytkownika.
- Obsługuje obiekty Microsoft Endpoint Manager i zasady grupy.
- Obsługiwane "[Właściwości urządzenia](#device-properties)" na liście.
- Aby uzyskać więcej informacji na temat Windows, zobacz [Jak kontrolować urządzenia USB i inne nośniki wymienne przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender](control-usb-devices-using-intune.md).

**Obsługiwana platforma** — Windows 10, Windows 11

**Szczegóły pomocy technicznej systemu macOS**:

- Stosowane na poziomie urządzenia: te same zasady mają zastosowanie do każdego zalogowanego użytkownika
- Aby uzyskać informacje o konkretnym systemie macOS, zobacz [Kontrola urządzenia dla systemu macOS](mac-device-control-overview.md).

**Obsługiwana platforma** — macOS Catalina 10.15.4+ (z włączonymi rozszerzeniami systemowymi) lub nowszym

### <a name="endpoint-dlp-removable-storage"></a>Magazyn wymienny DLP punktu końcowego

**Możliwości** — inspekcja, ostrzeganie lub uniemożliwianie użytkownikowi kopiowania elementu lub informacji na nośnik wymienny lub urządzenie USB.

**Opis** — aby uzyskać więcej informacji na temat Windows, zobacz [Dowiedz się więcej o zapobieganiu utracie danych punktu końcowego](../../compliance/endpoint-dlp-learn-about.md).

**Obsługiwana platforma** — Windows 10, Windows 11

### <a name="bitlocker"></a>Funkcją bitlocker

**Możliwości**:

- Blokuj dane, które mają być zapisywane na dyskach wymiennych, które nie są chronione przez funkcję BitLocker.
- Blokuj dostęp do dysków wymiennych, chyba że zostały one zaszyfrowane na komputerze należącym do organizacji

**Opis** — aby uzyskać więcej informacji na temat Windows, zobacz [Funkcja BitLocker — dysk wymienny Ustawienia](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Obsługiwana platforma** — Windows 10, Windows 11

## <a name="device-properties"></a>Właściwości urządzenia

Ochrona punktu końcowego w usłudze Microsoft Defender Device Control Removable Storage Protection umożliwia ograniczenie dostępu do magazynu wymiennego na podstawie właściwości opisanych w poniższej tabeli:

<br/><br/>

|Nazwa właściwości|Odpowiednie zasady|Dotyczy systemów operacyjnych|Opis|
|---|---|---|---|
|Klasa urządzenia|[Jak kontrolować urządzenia USB i inne nośniki wymienne przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender](control-usb-devices-using-intune.md)|System Windows|Aby uzyskać informacje o formatach identyfikatorów urządzeń, zobacz [klasa konfiguracji urządzenia](/windows-hardware/drivers/install/overview-of-device-setup-classes). Poniższe dwa linki zawierają pełną listę klas konfiguracji urządzeń. Klasy "System Use" odnoszą się głównie do urządzeń z komputerem/maszyną z fabryki, natomiast klasy "Dostawca" odnoszą się głównie do urządzeń, które mogą być podłączone do istniejącego komputera/maszyny: [klasy konfiguracji urządzeń zdefiniowane przez system dostępne dla dostawców — sterowniki Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) i [klasy konfiguracji urządzeń zdefiniowane przez system zarezerwowane do użytku systemowego — sterowniki Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use). **Uwaga**: Instalacja urządzenia może być stosowana do wszystkich urządzeń, a nie tylko do magazynu wymiennego.|
|Identyfikator podstawowy|[Wymienny Access Control magazynu](device-control-removable-storage-access-control.md)|System Windows|Identyfikator podstawowy obejmuje magazyn wymienny oraz dysk CD/DVD i Windows Urządzenia przenośne/WPD.|
|Identyfikator urządzenia|[magazyn wymienny Access Control](device-control-removable-storage-access-control.md); <p> [Jak kontrolować urządzenia USB i inne nośniki wymienne przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender](control-usb-devices-using-intune.md)|System Windows|Aby uzyskać informacje o formatach identyfikatorów urządzeń, zobacz [Standardowe identyfikatory USB](/windows-hardware/drivers/install/standard-usb-identifiers), na przykład USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|Identyfikator sprzętu|[Wymienny Access Control magazynu](device-control-removable-storage-access-control.md) <p> [Jak kontrolować urządzenia USB i inne nośniki wymienne przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender](control-usb-devices-using-intune.md)|System Windows|Ciąg zidentyfikował urządzenie w systemie, na przykład USBSTOR\DiskGeneric_Flash_Disk___8.07; **Uwaga**: identyfikator sprzętu nie jest unikatowy; różne urządzenia mogą współużytkować tę samą wartość.|
|Identyfikator wystąpienia|[Wymienny Access Control magazynu](device-control-removable-storage-access-control.md) <p> Instalowanie urządzenia|System Windows|Ciąg jednoznacznie identyfikuje urządzenie w systemie, na przykład USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|Przyjazna nazwa|[Wymienny Access Control magazynu](device-control-removable-storage-access-control.md)|System Windows|Ciąg dołączony do urządzenia, na przykład ogólne urządzenie USB z dyskiem flash|
|Identyfikator dostawcy/identyfikator produktu|[Wymienny Access Control magazynu](device-control-removable-storage-access-control.md)|System Windows <p> macOS|Identyfikator dostawcy to czterocyfrowy kod dostawcy przypisywany przez komitet USB do dostawcy. Identyfikator produktu to czterocyfrowy kod produktu przypisany do urządzenia przez dostawcę; Obsługa symbolu wieloznaczowego.|
|Identyfikator numeru seryjnego|[Wymienny Access Control magazynu](device-control-removable-storage-access-control.md)|System Windows <p> macOS |Na przykład `<SerialNumberId>002324B534BCB431B000058A</SerialNumberId>`|
