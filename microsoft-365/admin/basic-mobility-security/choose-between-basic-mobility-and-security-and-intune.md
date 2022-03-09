---
title: Wybierz między pakietem Basic Mobility i Zabezpieczeniami a usługą Intune
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Podstawowa mobilność i zabezpieczenia są częścią Microsoft 365 mobilnych.
ms.openlocfilehash: 79e5a641ad4c7c1966d1014376c9f1698caeff16
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400381"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Wybierz między pakietem Basic Mobility a zabezpieczeniami lub Intune

[Microsoft Intune](/mem/intune/) to autonomiczny produkt dostępny w niektórych Microsoft 365 pakietu Microsoft 365, natomiast pakiet Basic Mobility i Zabezpieczenia jest częścią Microsoft 365 mobilnych.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Dostępność pakietu Basic Mobility i zabezpieczeń oraz intune

Pakiet Basic Mobility i Security oraz usługa Intune są dostępne w różnych planach, co opisano w poniższej tabeli.

| Planowanie | Podstawowa mobilność i zabezpieczenia | Microsoft Intune |
|:-----|:-----|:-----|
|Aplikacje Microsoft 365|Tak|Nie|
|Microsoft 365 Business Basic|Tak|Nie|
|Microsoft 365 Business Standard|Tak|Nie|
|Office 365 E1 |Tak|Nie|
|Office 365 E3 |Tak|Nie|
|Office 365 E5 |Tak|Nie|
|Microsoft 365 Business Premium |Tak|Tak|
|Microsoft 365 firstline 3 |Tak|Tak|
|Microsoft 365 Enterprise E3 |Tak|Tak|
|Microsoft 365 Enterprise E5 |Tak|Tak|
|Microsoft 365 Education A1 |Tak|Tak|
|Microsoft 365 Education A3 |Tak|Tak|
|Microsoft 365 Education A5 |Tak|Tak|
|Microsoft Intune |Nie|Tak|
|Enterprise Mobility & Security E3 |Nie|Tak|
|Enterprise Mobility & Security E5 |Nie|Tak|

> [!NOTE]
> Nie możesz rozpocząć korzystania z pakietu Basic Mobility and Security, jeśli korzystasz już z pakietu Microsoft Intune.

 Aby uzyskać szczegółowe informacje, [Microsoft 365 i Office 365 opisy usług platformy](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>Różnice w możliwościach

Microsoft Intune podstawowe rozwiązania mobilne i zabezpieczenia zapewniają możliwość zarządzania urządzeniami przenośnymi w organizacji, ale istnieją istotne różnice w funkcjach opisane w poniższej tabeli.

> [!NOTE]
> Możesz zarządzać użytkownikami i ich urządzeniami przenośnymi zarówno za pomocą usługi Intune, jak i platformy Basic Mobility i zabezpieczeń w tej samej organizacji usługi Microsoft 365 Business Standard, najpierw przez skonfigurowanie mobilności podstawowej i zabezpieczeń, a następnie dodanie pakietu *Microsoft Intune*. Dzięki temu możesz wybrać rozwiązanie Basic Mobility and Security lub bardziej rozbudowane rozwiązanie Intune. Przypisywanie licencji usługi Intune w celu włączenia funkcji usługi Intune.

| Obszar funkcji | Najważniejsze cechy funkcji | Podstawowa mobilność i zabezpieczenia | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Typy urządzeń|Zarządzanie różnymi platformami systemu operacyjnego i wariantami głównych trybów zarządzania. |System Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|System Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>Mac OS, iPad OS|
|Zgodność urządzenia|Ustawianie zasad zabezpieczeń, takich jak blokowanie na poziomie urządzenia i wykrywanie kodu PIN na poziomie urządzenia, oraz zarządzanie nimi. |Ograniczenia dotyczące urządzeń z systemem Android. Zobacz [szczegóły](capabilities.md). |Tak|
|Dostęp warunkowy oparty na zgodności urządzenia |Uniemożliwiaj niecompliantom uzyskiwanie dostępu do firmowej poczty e-mail i danych z chmury. |Nie jest obsługiwane w Windows 10.<br/>Ograniczony do kontrolowania dostępu do Exchange Online, SharePoint Online i Outlook. |Tak |
|Konfiguracja urządzenia  |Konfigurowanie ustawień urządzenia (na przykład wyłączanie kamery)|Ograniczony zestaw ustawień.|Tak|
|Profile poczty e-mail  |Inicjowanie obsługi natywnego profilu poczty e-mail na urządzeniu. |Tak|Tak|
|Profile Wi-Fi |Inicjowanie obsługi natywnego profilu Wi-Fi na urządzeniu. |Nie|Tak|
|Profile VPN |Inicjowanie obsługi natywnego profilu VPN na urządzeniu. |Nie|Tak|
|Zarządzanie aplikacją mobilną  |Wdrażaj wewnętrzne aplikacje firmowe i sklepy z aplikacjami u użytkowników. |Nie|Tak|
|Ochrona aplikacji mobilnych  |Umożliwiaj użytkownikom bezpieczny dostęp do informacji firmowych przy użyciu aplikacji mobilnych i biznesowych firmy Office, które znają, a jednocześnie zapewniaj bezpieczeństwo danych, pomagając ograniczyć działania, takie jak kopiowanie, wycinanie, wklejanie i zapisywanie jako tylko w tych aplikacjach zarządzanych dla danych firmowych. Działa nawet wtedy, gdy urządzenia nie są zarejestrowane na pakiet Basic Mobility and Security. Zobacz Ochrona danych aplikacji za pomocą zasad zarządzania aplikacjami mobilnymi. |Nie|Tak|
|Zarządzana przeglądarka  |Włącz bezpieczniejsze przeglądanie Internetu za pomocą aplikacji Edge. |Nie|Tak|
|Zerowe programy rejestracji dotykowej (AutoPilot) |Zarejestruj dużą liczbę urządzeń firmowych, upraszczając konfigurację dla użytkowników. |Nie|Tak|
|||

Poza funkcjami wymienionymi w powyższej tabeli pakiet Basic Mobility i zabezpieczenia oraz Intune obejmują zestaw akcji zdalnych, które wysyłają polecenia na urządzenia przez Internet. Możesz na przykład usunąć dane programu Office z urządzenia pracownika podczas pozostawiania danych osobowych na miejscu (wycofywanie), usunąć aplikacje Office z urządzenia pracownika (wyczyścić) lub zresetować urządzenie do jego ustawień fabrycznych (czyszczenie pełne).

Akcje zdalne podstawowej mobilności i zabezpieczeń obejmują wycofywanie, czyszczenie i czyszczenie pełne. Aby uzyskać więcej informacji na temat akcji dotyczących mobilności podstawowej i zabezpieczeń, zobacz [Możliwości mobilności podstawowej i zabezpieczeń](capabilities.md).

W usłudze Intune masz następujący zestaw akcji:

-   Resetowanie rozwiązania Autopilot (tylko Windows rozwiązania
-  [Obrót klawisza BitLocker](/mem/intune/protect/encrypt-devices#rotate-bitlocker-recovery-keys)  (Windows tylko)
-  [Używanie czyszczenia, wycofywania lub ręcznego wycofywania urządzenia](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
-  [Wyłączanie lokalizacji aktywacji](/mem/intune/remote-actions/device-activation-lock-disable)  (tylko system iOS)
-  [Rozpoczęcie od początku](/mem/intune/remote-actions/device-fresh-start)  (Windows tylko)
- [Pełne skanowanie](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)  (Windows 10 tylko)
- [Lokalizowanie urządzenia](/mem/intune/remote-actions/device-locate)  (tylko system iOS)
- [Tryb utracony](/mem/intune/remote-actions/device-lost-mode)  (tylko system iOS)- [Szybkie skanowanie](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)(Windows 10)
- [Zdalne sterowanie dla systemu Android](/mem/intune/remote-actions/teamviewer-support)
- [Blokada zdalna](/mem/intune/remote-actions/device-remote-lock)
- [Zmienianie nazwy urządzenia](/mem/intune/remote-actions/device-rename)
-  [Resetuj kod](/mem/intune/remote-actions/device-passcode-reset) [dostępu Uruchom ponownie](/mem/intune/remote-actions/device-restart) (Windows)
-  Aktualizowanie Windows Defender zabezpieczeń (tylko Windows)
-  Windows 10 numeru PIN (tylko Windows)
-  [Wysyłanie niestandardowych powiadomień](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)  (Android, iOS, iPad OS)
-  [Synchronizowanie urządzenia](/mem/intune/remote-actions/device-sync)

Aby uzyskać więcej informacji na temat akcji usługi Intune, [Microsoft Intune dokumentację](/mem/intune/).
