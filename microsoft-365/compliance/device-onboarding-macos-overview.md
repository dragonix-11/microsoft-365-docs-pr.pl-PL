---
title: Omówienie dołączania urządzeń z systemem macOS do platformy Microsoft 365 (wersja zapoznawcza)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Dowiedz się więcej o dołączaniu urządzeń z systemem macOS do rozwiązań zgodności
ms.openlocfilehash: 783179ae749ac7cd6de671435927ba5bbdbdacad
ms.sourcegitcommit: 9d563faeaa50b59b0b468dbb373d886e5270f58e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "64387020"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview-preview"></a>Omówienie dołączania urządzeń z systemem macOS do platformy Microsoft 365 (wersja zapoznawcza)

Urządzenia z systemem MacOS można dołączać do Microsoft 365 zgodności przy Intune albo usługi JAMF Pro. Procedury dołączania różnią się w zależności od tego, które rozwiązanie zarządzania jest stosowane. Jeśli Twoje urządzenia z systemem macOS zostały już podłączone do Ochrona punktu końcowego w usłudze Microsoft Defender (MDE), jest mniej kroków. Zobacz [Następne kroki](#next-steps) , aby uzyskać linki do odpowiednich procedur.

**Dotyczy:**

- [Zapobieganie utracie danych w punkcie końcowym (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem pracy z zasadą DLP punktu końcowego na urządzeniach z systemem macOS (Catalina 10.15 lub nowszym) zapoznaj się z tymi artykułami:

- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
- [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)

Jeśli w ogóle nie znasz zasad DLP, zapoznaj się również z tymi artykułami:

- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Planowanie ochrony przed utratą danych (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Informacje dotyczące zasad ochrony przed utratą danych](dlp-policy-reference.md#data-loss-prevention-policy-reference)

Jeśli nie znasz ryzyka niejawnego programu testów, zapoznaj się z tymi artykułami:

 - [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
 - [Zaplanuj zarządzanie ryzykiem wewnętrznym](insider-risk-management-plan.md#plan-for-insider-risk-management)

Urządzenia z systemem macOS muszą być już zarządzane za pośrednictwem usługi Intune lub JAMF Pro.
 
- Aby do usługi Intune, zobacz Przewodnik wdrażania: Zarządzanie urządzeniami [z systemem macOS](/mem/intune/fundamentals/deployment-guide-platform-macos) w programie Microsoft Intune i [Rejestrowanie komputera Mac](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp) za pomocą Intune — Portal firmy. 
- Aby wdąć do usługi JAMF Pro zobacz przewodnik administratorów usługi [JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) oraz Przewodnik po instalacji i konfiguracji usługi [JAMF Pro dla komputerów Mac](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/).
- Instalowanie przeglądarki Edge w wersji 95+ na urządzeniach z systemem macOS 

## <a name="licensing-guidance"></a>Wskazówki dotyczące licencjonowania

Zobacz Microsoft 365 [licencjonowania informacji](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="activities-that-can-be-restricted-on-macos"></a>Działania, które można ograniczyć w systemie macOS 

Po dojechaniu urządzenia z systemem macOS do rozwiązań Microsoft 365 zgodności możesz monitorować i ograniczać te akcje przy użyciu zasad ochrony przed utratą danych (DLP).

**Kopiowanie na nośnik wymienny USB** — jeśli to wymusza, ta akcja blokuje, ostrzega lub przeprowadza inspekcje kopiowania lub przenoszenia plików chronionych z urządzenia końcowego na nośnik wymienny USB 

**Kopiowanie do udziałów sieciowych** — jeśli są wymuszane, te bloki akcji, ostrzeżenia lub inspekcje kopiowania lub przenoszenia plików chronionych z urządzenia końcowego do dowolnego udziału sieciowego 

**Drukowanie** — jeśli są wymuszane, te bloki akcji, ostrzeżenia lub inspekcje po wydrukowaniu plików chronionych z urządzenia końcowego 

**Kopiuj do schowka** — jeśli są wymuszane, te bloki akcji, ostrzeżenia lub inspekcje danych w pliku chronionym, które są kopiowane do schowka na urządzeniu końcowym 

**Upload** do chmury — ta lista akcji blokuje, ostrzega lub przeprowadza inspekcje, jeśli nie można przekazać chronionych plików do usług w chmurze lub zezwolić na nie na podstawie listy domen dozwolonych/zabronionej w ustawieniach globalnych. Gdy ta akcja jest ustawiona tak, aby ostrzegać lub blokować, inne przeglądarki (zdefiniowane na liście odblokowanych przeglądarek w obszarze Ustawienia globalne) są blokowane z dostępem do pliku. 

**Dostępne przez aplikacje** niedozwolone — jeśli są wymuszane, ta akcja uniemożliwia aplikacjom na liście aplikacji odblokowanych (zgodnie z definicją w ustawieniach globalnych) uzyskiwanie dostępu do plików chronionych na urządzeniu końcowym. Przykładowe scenariusze 

## <a name="onboarding-devices-into-device-management"></a>Dołączanie urządzeń do zarządzania urządzeniami

Aby monitorować i chronić poufne elementy na urządzeniu, musisz włączyć monitorowanie urządzeń i włączyć swoje punkty końcowe. Obie te czynności są wykonywane w portalu Microsoft 365 zgodności.

Jeśli chcesz wboardować urządzenia, które nie zostały jeszcze w nim podłączone, pobierzesz odpowiedni skrypt i wdrożysz go na tych urządzeniach. <!--Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).-->

<!--If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list.-->

1. Otwórz stronę [centrum zgodności firmy Microsoft](https://compliance.microsoft.com) **Ustawienia** i wybierz pozycję **Włącz monitorowanie urządzeń**.

   > [!NOTE]
   > Włączanie dołączania do urządzenia trwa zwykle około 60 sekund, ale skontaktuj się z pomocą techniczną firmy Microsoft na maksymalnie 30 minut przed jej rozpoczęciem.

2. Otwórz stronę ustawień Centrum zgodności i wybierz **pozycję Włącz monitorowanie urządzeń w systemie macOS**.

## <a name="next-steps"></a>Następne kroki

Aby móc odbierać telemetrię czujnika DLP i wymuszać zasady ochrony przed utratą danych Microsoft 365 urządzenia są wymagane do uzyskiwania rozwiązań zgodności z przepisami. 

Temat | Opis
:---|:---
|[Urządzenia z systemem macOS w nowych i Microsoft 365 zgodności przy Intune (wersja zapoznawcza)](device-onboarding-offboarding-macos-intune.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview)|W przypadku urządzeń z systemem macOS zarządzanych za pośrednictwem systemu Intune
|[Dołączanie i odłączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu usługi Intune dla klientów usługi Ochrony punktu końcowego w usłudze Microsoft Defender (wersja zapoznawcza)](device-onboarding-offboarding-macos-intune-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview) |W przypadku urządzeń z systemem macOS zarządzanych za Intune i Ochrona punktu końcowego w usłudze Microsoft Defender (MDE)
|[Urządzenia z systemem macOS w nowych Microsoft 365 zgodności przy użyciu usługi JAMF Pro (wersja zapoznawcza)](device-onboarding-offboarding-macos-jamfpro.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview) | W przypadku urządzeń macOS zarządzanych za pośrednictwem usługi JAMF Pro
|[Dołączanie i odłączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu narzędzia JAMF Pro dla klientów usługi Ochrony punktu końcowego w usłudze Microsoft Defender (wersja zapoznawcza)](device-onboarding-offboarding-macos-jamfpro-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview)|W przypadku urządzeń z systemem macOS zarządzanych za pośrednictwem usługi JAMF Pro, Ochrona punktu końcowego w usłudze Microsoft Defender w nich wdrożono aplikację MDE


## <a name="related-topics"></a>Tematy pokrewne

- [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [Macierz obsługi dla porad dotyczących zasad DLP w aplikacjach firmy Microsoft](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
