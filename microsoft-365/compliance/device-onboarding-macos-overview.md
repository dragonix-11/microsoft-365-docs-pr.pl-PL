---
title: Dołączanie urządzeń z systemem macOS do Microsoft 365 omówienie
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
ms.openlocfilehash: 6cc3323a94ee609c3c6674c12eb99fad3f18f3b4
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952741"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview"></a>Dołączanie urządzeń z systemem macOS do Microsoft 365 omówienie

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Urządzenia z systemem MacOS można dołączyć do rozwiązań usługi Microsoft Purview przy użyciu Intune lub jamf Pro. Procedury dołączania różnią się w zależności od używanego rozwiązania do zarządzania. Jeśli urządzenia z systemem macOS zostały już dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender (MDE), jest mniej kroków. Aby uzyskać linki do odpowiednich procedur, zobacz [Następne kroki](#next-steps) .

**Dotyczy:**

- [Ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed rozpoczęciem pracy z programem Endpoint DLP na urządzeniach z systemem macOS (Catalina 10.15 lub nowszym) zapoznaj się z następującymi artykułami:

- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md)
- [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md)

Jeśli w ogóle nie znasz DLP, zapoznaj się również z następującymi artykułami:

- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Planowanie zapobiegania utracie danych (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Dokumentacja dotycząca zasad ochrony przed utratą danych](dlp-policy-reference.md#data-loss-prevention-policy-reference)

Jeśli nie znasz ryzyka związanego z niejawnymi testerami, zapoznaj się z następującymi artykułami:

 - [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)
 - [Zaplanuj zarządzanie ryzykiem wewnętrznym](insider-risk-management-plan.md#plan-for-insider-risk-management)

Urządzenia z systemem macOS muszą być już zarządzane za pośrednictwem Intune lub jamf Pro.
 
- Aby dołączyć do Intune, zobacz [Przewodnik wdrażania: Zarządzanie urządzeniami z systemem macOS w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) i [Rejestrowanie komputera Mac przy użyciu Intune — Portal firmy](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Aby dołączyć do jamf Pro zobacz [jamf Pro administratorów](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) przewodnik i [jamf Pro instalacji i konfiguracji przewodnik dla komputerów Mac](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
- Instalowanie przeglądarki v95+ Edge na urządzeniach z systemem macOS 

## <a name="licensing-guidance"></a>Wskazówki dotyczące licencjonowania

Zobacz [Microsoft 365 wskazówki dotyczące licencjonowania dotyczące ochrony informacji](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="activities-that-can-be-restricted-on-macos"></a>Działania, które mogą być ograniczone w systemie macOS 

Po dodaniu urządzenia z systemem macOS do rozwiązań usługi Microsoft Purview można monitorować i ograniczać te akcje za pomocą zasad ochrony przed utratą danych (DLP).

**Kopiowanie na nośnik wymienny USB** — w przypadku wymuszania ta akcja blokuje, ostrzega lub przeprowadza inspekcję kopiowania lub przenoszenia chronionych plików z urządzenia punktu końcowego na nośnik wymienny USB 

**Kopiowanie do udziałów sieciowych** — w przypadku wymuszania ta akcja blokuje, ostrzega lub przeprowadza inspekcję kopiowania lub przenoszenia chronionych plików z urządzenia punktu końcowego do dowolnego udziału sieciowego 

**Drukowanie** — w przypadku wymuszania ta akcja blokuje, ostrzega lub przeprowadza inspekcję, gdy chronione pliki są drukowane z urządzenia punktu końcowego 

**Kopiowanie do schowka** — w przypadku wymuszania ta akcja blokuje, ostrzega lub przeprowadza inspekcję danych w chronionym pliku, który jest kopiowany do schowka na urządzeniu punktu końcowego 

**Upload do chmury** — ta akcja blokuje, ostrzega lub przeprowadza inspekcję, gdy chronione pliki nie mogą być przekazywane do usług w chmurze lub mogą być przekazywane do nich na podstawie listy dozwolonych/niedozwolonych domen w ustawieniach globalnych. Gdy ta akcja jest ustawiona na ostrzeżenie lub zablokowanie, inne przeglądarki (zdefiniowane na liście niedozwolonych przeglądarek w obszarze Ustawienia globalne) nie mają dostępu do pliku. 

**Dostęp do aplikacji, do których nie można uzyskać dostępu** — po wymuszeniu tej akcji uniemożliwia aplikacjom znajdującym się na liście nieobsługiwanych aplikacji (zgodnie z definicją w ustawieniach globalnych) dostęp do chronionych plików na urządzeniu punktu końcowego. Przykładowe scenariusze 

## <a name="onboarding-devices-into-device-management"></a>Dołączanie urządzeń do zarządzania urządzeniami

Aby można było monitorować i chronić poufne elementy na urządzeniu, należy włączyć monitorowanie urządzeń i dołączać do nich punkty końcowe. Obie te akcje są wykonywane w portalu zgodności usługi Microsoft Purview.

Jeśli chcesz dołączyć urządzenia, które nie zostały jeszcze dołączone, pobierzesz odpowiedni skrypt i wdrożysz go na tych urządzeniach. <!--Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).-->

<!--If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list.-->

1. Otwórz [stronę Ustawienia portalu zgodności usługi Microsoft Purview](https://compliance.microsoft.com)  i wybierz pozycję **Włącz monitorowanie urządzeń**.

   > [!NOTE]
   > Włączenie dołączania urządzenia zwykle trwa około 60 sekund, ale przed rozpoczęciem angażowania się w pomoc techniczną firmy Microsoft poczekaj do 30 minut.

2. Otwórz stronę Ustawienia Centrum zgodności i wybierz pozycję **Włącz monitorowanie urządzeń z systemem macOS**.

## <a name="next-steps"></a>Następne kroki

Aby odbierać dane telemetryczne czujnika DLP i wymuszać zasady ochrony przed utratą danych, wymagane jest dołączenie urządzeń do rozwiązań usługi Microsoft Purview. 

Temat | Opis
:---|:---
|[Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu Intune](device-onboarding-offboarding-macos-intune.md)|W przypadku urządzeń z systemem macOS zarządzanych za pośrednictwem Intune
|[Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu Intune dla klientów Ochrona punktu końcowego w usłudze Microsoft Defender](device-onboarding-offboarding-macos-intune-mde.md) |W przypadku urządzeń z systemem macOS, które są zarządzane za pośrednictwem Intune i które mają wdrożone Ochrona punktu końcowego w usłudze Microsoft Defender (MDE)
|[Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu narzędzia JAMF Pro](device-onboarding-offboarding-macos-jamfpro.md) | W przypadku urządzeń z systemem macOS zarządzanych za pośrednictwem Pro JAMF
|[Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu Pro JAMF dla klientów Ochrona punktu końcowego w usłudze Microsoft Defender](device-onboarding-offboarding-macos-jamfpro-mde.md)|W przypadku urządzeń z systemem macOS, które są zarządzane za pośrednictwem Pro JAMF i które mają wdrożone Ochrona punktu końcowego w usłudze Microsoft Defender (MDE)


## <a name="related-topics"></a>Tematy pokrewne

- [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [Macierz pomocy technicznej dotycząca porad dotyczących zasad DLP w aplikacjach firmy Microsoft](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
