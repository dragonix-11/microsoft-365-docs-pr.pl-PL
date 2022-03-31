---
title: Tabele danych w zaawansowanym schemacie Microsoft 365 Defender myśliwski
description: Informacje o tabelach w zaawansowanym schemacie chłoniania, aby zrozumieć dane, na których można uruchamiać zapytania wyszukiwania przed zagrożeniami
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, informacje o schemacie, kusto, tabela, dane
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: a496e0e293e72821016d6efa5fbd9622f669ab0b
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755542"
---
# <a name="understand-the-advanced-hunting-schema"></a>Opis zaawansowanego schematu chłoniania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Zaawansowany [schemat chłoniania](advanced-hunting-overview.md) składa się z wielu tabel, które dostarczają informacji o wydarzeniach lub urządzeniach, alertach, tożsamościach i innych typach encji. Aby skutecznie tworzyć zapytania obejmujące wiele tabel, musisz zrozumieć tabele i kolumny w zaawansowanym schemacie wyszukiwania.

<a name="get-schema-information-in-the-security-center"></a>

## <a name="get-schema-information"></a>Uzyskiwanie informacji o schemacie

Podczas konstruowania zapytań użyj wbudowanego odwołania do schematu, aby szybko uzyskać następujące informacje o każdej tabeli w schemacie:

- **Opis tabeli** — typ danych zawartych w tabeli i źródło tych danych.
- **Kolumny** — wszystkie kolumny w tabeli.
- **Typy** akcji — możliwe wartości w kolumnie `ActionType` reprezentujące typy zdarzeń obsługiwane przez tabelę. Te informacje są udostępniane tylko w przypadku tabel zawierających informacje o zdarzeniach.
- **Przykładowe** zapytanie — przykładowe zapytania, które oferują możliwości korzystania z tabeli.

### <a name="access-the-schema-reference"></a>Uzyskiwanie dostępu do informacji o schemacie
Aby szybko uzyskać dostęp do odwołania do schematu, wybierz akcję **Wyświetl** odwołanie obok nazwy tabeli w reprezentacji schematu. Możesz również wybrać pozycję **Odwołanie do schematu** , aby wyszukać tabelę.

:::image type="content" source="../../media/understand-schema-1.png" alt-text="The Schema Reference page on the Advanced Hunting page in the Microsoft 365 Defender portal" lightbox="../../media/understand-schema-1.png":::

## <a name="learn-the-schema-tables"></a>Informacje o tabelach schematów
Poniższe informacje zawierają listę wszystkich tabel w schemacie. Każda nazwa tabeli zawiera linki do stron z opisami nazw kolumn dla tej tabeli. Nazwy tabel i kolumn są również wymienione w usłudze Defender dla chmury jako część reprezentacji schematu na zaawansowanym ekranie wyszukiwania.

| Nazwa tabeli | Opis |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Pliki, adresy IP, adresy URL, użytkownicy lub urządzenia skojarzone z alertami |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Alerty z programu Microsoft Defender dla punktu końcowego, programu Microsoft Defender dla programu Office 365, programu Microsoft Defender dla aplikacji w chmurze i usługi Microsoft Defender dla tożsamości, w tym informacje o ważności i kategoryzacji zagrożeń  |
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)** | Zdarzenia obejmujące konta i obiekty w usłudze Office 365 oraz inne aplikacje i usługi w chmurze |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | Wiele typów zdarzeń, w tym zdarzenia wyzwalane przez mechanizmy kontroli zabezpieczeń, takie jak Program antywirusowy Windows Defender i exploit protection |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** | Informacje o certyfikatach podpisanych plików uzyskanych ze zdarzeń weryfikacji certyfikatu w punktach końcowych |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Tworzenie plików, modyfikacje i inne zdarzenia systemowe plików |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Zdarzenia ładowania biblioteki DLL |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Informacje o komputerze, w tym informacje o komputerze z systemu operacyjnego |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Logowania i inne zdarzenia uwierzytelniania na urządzeniach |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | Połączenie sieciowe i powiązane zdarzenia |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Właściwości sieciowe urządzeń, w tym karty fizyczne, adresy IP i MAC, a także połączone sieci i domeny |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Tworzenie procesów i powiązane zdarzenia |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Tworzenie i modyfikowanie wpisów rejestru |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | Zagrożenia & zdarzeń oceny luk w zabezpieczeniach, które wskazują stan różnych konfiguracji zabezpieczeń na urządzeniach |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | Baza wiedzy na temat różnych konfiguracji zabezpieczeń używanych przez funkcje zarządzania & zagrożeniami i lukami w zabezpieczeniach do oceny urządzeń; obejmuje mapowania na różne standardy i punkty odniesienia  |
| **[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)** | Spis oprogramowania zainstalowanego na urządzeniach, w tym informacje o ich wersji i stanie zakończenia pomocy technicznej |
| **[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)** | Luki w zabezpieczeniach oprogramowania na urządzeniach oraz lista dostępnych aktualizacji zabezpieczeń, które mają na celu ochronę przed każdą luką |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | Baza wiedzy na temat luk w zabezpieczeniach dostępnych publicznie, w tym tego, czy kod wykorzystujący lukę jest publicznie dostępny |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Informacje o plikach dołączonych do wiadomości e-mail |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Microsoft 365 e-mail, w tym dostarczanie i blokowanie zdarzeń wiadomości e-mail |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Zdarzenia zabezpieczeń występujące po dostarczeniu po Microsoft 365 wiadomości e-mail do skrzynki pocztowej adresata |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Informacje o adresach URL w wiadomościach e-mail |
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)** | Zdarzenia dotyczące lokalnego kontrolera domeny z uruchomionym usługą Active Directory (AD). W poniższej tabeli o zajmę się szeregiem zdarzeń związanych z tożsamością i zdarzeń systemowych na kontrolerze domeny. |
| **[IdentityInfo](advanced-hunting-identityinfo-table.md)** | Informacje o koncie z różnych źródeł, w tym Azure Active Directory |
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)** | Zdarzenia uwierzytelniania w usługach Active Directory i Microsoft Online Services |
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)** | Zapytania dotyczące obiektów usługi Active Directory, takich jak użytkownicy, grupy, urządzenia i domeny |

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytań](advanced-hunting-query-results.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
