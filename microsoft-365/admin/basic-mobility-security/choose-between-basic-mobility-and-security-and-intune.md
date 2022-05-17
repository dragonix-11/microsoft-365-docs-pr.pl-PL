---
title: Wybór między pakietami Basic Mobility i Security i Intune
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
description: Usługa Basic Mobility and Security jest częścią planów Microsoft 365, a Microsoft Intune jest autonomicznym produktem dołączonym do niektórych planów Microsoft 365.
ms.openlocfilehash: 1d04beea6ece35d5d28bdd961041b30c1f8f2793
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435772"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Wybierz opcję Podstawowa mobilność i zabezpieczenia lub Intune

[Microsoft Intune](/mem/intune/) jest autonomicznym produktem dołączonym do niektórych planów Microsoft 365, podczas gdy usługa Basic Mobility and Security jest częścią planów Microsoft 365.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Dostępność pakietu Basic Mobility and Security i Intune

Zarówno pakiety Basic Mobility, jak i Security oraz Intune są uwzględniane w różnych planach opisanych w poniższej tabeli.

| Plan | Funkcja Podstawowa mobilność i zabezpieczenia | Microsoft Intune |
|:-----|:-----|:-----|
|Aplikacje Microsoft 365|Tak|Nie|
|Microsoft 365 dla Firm w warstwie Podstawowa|Tak|Nie|
|Microsoft 365 Business Standard|Tak|Nie|
|Office 365 E1 |Tak|Nie|
|Office 365 E3 |Tak|Nie|
|Office 365 E5 |Tak|Nie|
|Microsoft 365 Business Premium |Tak|Tak|
|Microsoft 365 pierwszej linii 3 |Tak|Tak|
|Microsoft 365 Enterprise E3 |Tak|Tak|
|Microsoft 365 Enterprise E5 |Tak|Tak|
|Microsoft 365 Education A1 |Tak|Tak|
|Microsoft 365 Education A3 |Tak|Tak|
|Microsoft 365 Education A5 |Tak|Tak|
|Microsoft Intune |Nie|Tak|
|Enterprise Mobility & Security E3 |Nie|Tak|
|Enterprise Mobility & Security E5 |Nie|Tak|

> [!NOTE]
> Nie można rozpocząć korzystania z pakietu Basic Mobility and Security, jeśli już używasz Microsoft Intune.

 Aby uzyskać szczegółowe informacje, zobacz [opisy usług platformy Microsoft 365 i Office 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>Różnice w możliwościach

Microsoft Intune i wbudowane rozwiązania Basic Mobility and Security umożliwiają zarządzanie urządzeniami przenośnymi w organizacji, ale istnieją kluczowe różnice w możliwościach opisane w poniższej tabeli.

> [!NOTE]
> Możesz zarządzać użytkownikami i ich urządzeniami przenośnymi przy użyciu Intune i pakietu Basic Mobility and Security w tej samej organizacji Microsoft 365 Business Standard *, najpierw konfigurując pakiet Basic Mobility and Security, a następnie dodając Microsoft Intune*. Dzięki temu możesz wybrać opcję Podstawowa mobilność i zabezpieczenia lub bardziej rozbudowane rozwiązanie Intune. Przypisz licencję Intune, aby włączyć funkcje Intune.

| Obszar funkcji | Wyróżnienia funkcji | Funkcja Podstawowa mobilność i zabezpieczenia | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Typy urządzeń|Zarządzanie różnymi platformami systemu operacyjnego i głównymi wariantami trybu zarządzania. |System Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|System Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>mac OS, iPad OS|
|Zgodność urządzeń|Ustawianie zasad zabezpieczeń i zarządzanie nimi, takich jak blokada numeru PIN na poziomie urządzenia i wykrywanie jailbreaku. |Ograniczenia dotyczące urządzeń Android. Zobacz [szczegóły](capabilities.md). |Tak|
|Dostęp warunkowy na podstawie zgodności urządzeń |Uniemożliwiaj niezgodnym urządzeniom uzyskiwanie dostępu do firmowej poczty e-mail i danych z chmury. |Nieobsługiwane w Windows 10.<br/>Ograniczone do kontrolowania dostępu do Exchange Online, SharePoint Online i Outlook. |Tak |
|Konfiguracja urządzenia  |Konfigurowanie ustawień urządzenia (na przykład wyłączanie aparatu)|Ograniczony zestaw ustawień.|Tak|
|Profile poczty e-mail  |Aprowizowanie natywnego profilu poczty e-mail na urządzeniu. |Tak|Tak|
|Profile sieci Wi-Fi |Aprowizowanie natywnego profilu sieci Wi-Fi na urządzeniu. |Nie|Tak|
|Profile sieci VPN |Aprowizowanie natywnego profilu sieci VPN na urządzeniu. |Nie|Tak|
|Zarządzanie aplikacjami mobilnymi  |Wdrażanie wewnętrznych aplikacji biznesowych i sklepów z aplikacjami dla użytkowników. |Nie|Tak|
|Ochrona aplikacji mobilnych  |Umożliwianie użytkownikom bezpiecznego dostępu do informacji firmowych przy użyciu Office aplikacji mobilnych i biznesowych, które znają, przy jednoczesnym zapewnieniu bezpieczeństwa danych, pomagając ograniczyć akcje, takie jak kopiowanie, wycinanie, wklejanie i zapisywanie jako, tylko do tych aplikacji zarządzanych przez firmowe dane. Działa nawet wtedy, gdy urządzenia nie są zarejestrowane w usłudze Basic Mobility and Security. Zobacz Ochrona danych aplikacji przy użyciu zasad zarządzania aplikacjami mobilnymi. |Nie|Tak|
|Zarządzana przeglądarka  |Włącz bezpieczniejsze przeglądanie internetu przy użyciu aplikacji Edge. |Nie|Tak|
|Programy rejestracji bez dotyku (AutoPilot) |Zarejestruj dużą liczbę urządzeń należących do firmy, jednocześnie upraszczając konfigurację użytkownika. |Nie|Tak|

Oprócz funkcji wymienionych w poprzedniej tabeli, pakiety Basic Mobility and Security i Intune zawierają zestaw akcji zdalnych, które wysyłają polecenia do urządzeń przez Internet. Możesz na przykład usunąć dane Office z urządzenia pracownika, pozostawiając dane osobowe na miejscu (wycofać), usunąć aplikacje Office z urządzenia pracownika (czyszczenie) lub zresetować urządzenie do ustawień fabrycznych (pełne czyszczenie).

Akcje zdalne usługi Basic Mobility and Security obejmują wycofywanie, czyszczenie i pełne czyszczenie. Aby uzyskać więcej informacji na temat podstawowych akcji związanych z mobilnością i zabezpieczeniami, zobacz [możliwości pakietu Basic Mobility and Security](capabilities.md).

W przypadku Intune masz następujący zestaw akcji:

- [Resetowanie rozwiązania Autopilot](/mem/autopilot/windows-autopilot-reset) (tylko Windows)
- [Odzyskiwanie klucza funkcji Bitlocker](https://support.microsoft.com/windows/finding-your-bitlocker-recovery-key-in-windows-6b71ad27-0b89-ea08-f143-056f5ab347d6) (tylko Windows)
- [Używanie czyszczenia, wycofywania lub ręcznego wyrejestrowania urządzenia](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
- [Wyłącz blokadę aktywacji](/mem/intune/remote-actions/device-activation-lock-disable) (tylko iOS)
- [Rozpoczęcie od nowa](/mem/intune/remote-actions/device-fresh-start) (tylko Windows)
- [Pełne skanowanie](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) (tylko Windows 10)
- [Lokalizowanie urządzenia](/mem/intune/remote-actions/device-locate) (tylko iOS)
- [Tryb zgubienia](/mem/intune/remote-actions/device-lost-mode) (tylko iOS) — [szybkie skanowanie](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) (tylko Windows 10)
- [Zdalne sterowanie Android](/mem/intune/remote-actions/teamviewer-support)
- [Zdalne blokowanie](/mem/intune/remote-actions/device-remote-lock)
- [Zmienianie nazwy urządzenia](/mem/intune/remote-actions/device-rename)
- [Resetowanie ponownego uruchamiania kodu dostępu](/mem/intune/remote-actions/device-passcode-reset) [](/mem/intune/remote-actions/device-restart) (tylko Windows)
- [Aktualizowanie analizy zabezpieczeń Windows Defender](https://www.microsoft.com/en-us/wdsi/defenderupdates) (tylko Windows)
- [Windows 10 resetowanie numeru PIN](/windows/security/identity-protection/hello-for-business/hello-feature-pin-reset) (tylko Windows)
- [Wysyłanie powiadomień niestandardowych](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device) (Android, iOS, iPad systemu operacyjnego)
- [Synchronizowanie urządzenia](/mem/intune/remote-actions/device-sync)

Aby uzyskać więcej informacji na temat akcji Intune, zobacz [dokumentację Microsoft Intune](/mem/intune/).
