---
title: Włączanie usługi Microsoft 365 Defender
description: Dowiedz się, jak włączyć Microsoft 365 Defender i rozpocząć integrowanie zdarzeń zabezpieczających oraz reagowania na nie.
keywords: rozpoczynanie pracy, włączanie Microsoft 365 Defender, Microsoft 365 Defender, M365, zabezpieczenia, lokalizacja danych, wymagane uprawnienia, uprawnienia do licencji, strona ustawień
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 2a99dbaf50b582df4203fc9c8e1d04e0a3f6d807
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498661"
---
# <a name="turn-on-microsoft-365-defender"></a>Włączanie usługi Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-365-defender.md) ujednolicony proces reagowania na incydenty przez zintegrowanie kluczowych funkcji Ochrona punktu końcowego w usłudze Microsoft Defender Ochrona usługi Office 365 w usłudze Microsoft Defender, Microsoft Defender for Cloud Apps i Microsoft Defender for Identity. To ujednolicone środowisko dodaje zaawansowane funkcje, do których można uzyskać dostęp w portalu Microsoft 365 Defender sieci.

Microsoft 365 Defender włącza się automatycznie, gdy uprawnieni klienci z wymaganymi uprawnieniami odwiedzają Microsoft 365 Defender portalu. Przeczytaj ten artykuł, aby poznać różne wymagania wstępne i sposób Microsoft 365 Defender zapewnienia obsługi administracyjnej.

## <a name="check-license-eligibility-and-required-permissions"></a>Sprawdzanie uprawnień do licencji i wymaganych uprawnień

Licencja na produkt Microsoft 365 na ogół uprawnia do korzystania z usługi Microsoft 365 Defender bez dodatkowych kosztów licencjonowania. Zalecamy uzyskanie licencji Microsoft 365 E5, E5 Security, A5 lub A5 Security albo prawidłowej kombinacji licencji, która zapewnia dostęp do wszystkich obsługiwanych usług.

Aby uzyskać szczegółowe informacje o [licencjonowaniu, przeczytaj wymagania dotyczące licencjonowania](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>Sprawdzanie roli

Aby włączyć funkcje, musisz mieć jedną z następujących ról Microsoft 365 Defender:

- Administrator globalny
- Administrator zabezpieczeń
- Operator zabezpieczeń
- Czytnik globalny
- Czytnik zabezpieczeń
- Administrator zgodności
- Administrator danych dotyczących zgodności
- Administrator aplikacji
- Administrator aplikacji w chmurze

[Wyświetlanie ról w usłudze Azure AD](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>Obsługiwane usługi

Microsoft 365 Defender agreguje dane z różnych obsługiwanych usług, które zostały już wdrożone. Dane są przetwarzane i przechowywane centralnie, co pozwala identyfikować nowe szczegółowe informacje i umożliwiać scentralizowane przepływy pracy odpowiedzi. Nie wpływa to na istniejące wdrożenia, ustawienia ani dane skojarzone ze zintegrowanymi usługami.

Aby uzyskać najlepszą ochronę i optymalizowanie Microsoft 365 Defender, zalecamy wdrożenie wszystkich obsługiwanych usług w Twojej sieci. Aby uzyskać więcej informacji, [przeczytaj o wdrażaniu obsługiwanych usług](deploy-supported-services.md).

## <a name="onboard-to-the-service"></a>Dołączanie do usługi
Dołączanie do Microsoft 365 Defender jest proste. Z menu nawigacji wybierz dowolny element, taki jak Alerty o zdarzeniach **&****, Myśli****, Centrum** akcji lub Analiza zagrożeń, aby  zainicjować proces dołączania. 

### <a name="data-center-location"></a>Lokalizacja centrum danych

Microsoft 365 Defender będą przechowywane i przetwarzane w tej samej lokalizacji, w których są [używane Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Jeśli nie masz dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender, nowa lokalizacja centrum danych jest wybierana automatycznie na podstawie lokalizacji aktywnych usług Microsoft 365 zabezpieczeń. Wybrana lokalizacja centrum danych jest wyświetlana na ekranie.

Wybierz **pozycję Potrzebujesz pomocy?** w portalu Microsoft 365 Defender, aby skontaktować się z pomocą techniczną firmy Microsoft w Microsoft 365 Defender obsługi administracyjnej w innej lokalizacji centrum danych.

> [!NOTE]
> W przeszłości automatyczne Ochrona punktu końcowego w usłudze Microsoft Defender w centrach danych Unii Europejskiej,gdy są włączone za pośrednictwem Microsoft Defender dla Chmury. Microsoft 365 Defender będą automatycznie zapewniane w tym samym centrum danych UE dla klientów, którzy w przeszłości obsługili usługę Defender for Endpoint w ten sposób.

### <a name="confirm-that-the-service-is-on"></a>Upewnij się, że usługa jest wł.

Po inicjowaniu obsługi administracyjnej usługi dodaje ona:

- [Zarządzanie zdarzeniami](incidents-overview.md)
- [Kolejka alertów](investigate-alerts.md)
- Centrum akcji do zarządzania automatycznym [badaniem i odpowiedziami](m365d-autoir.md)
- [Zaawansowane możliwości chłoniania](advanced-hunting-overview.md)
- Analiza zagrożeń

:::image type="content" source="../../media/overview-incident.png" alt-text="Okienko nawigacji w portalu Microsoft 365 Defender z Microsoft 365 Defender funkcjami" lightbox="../../media/overview-incident.png":::
*Microsoft 365 Defender portal z zarządzaniem zdarzeniami i innymi możliwościami*

### <a name="getting-microsoft-defender-for-identity-data"></a>Pobieranie Microsoft Defender for Identity danych 
Aby włączyć integrację z usługą Microsoft Defender for Cloud Apps, musisz zalogować się do Microsoft Defender for Cloud Apps co najmniej raz.

## <a name="get-assistance"></a>Uzyskaj pomoc

Aby uzyskać odpowiedzi na najczęściej zadawane pytania dotyczące włączania Microsoft 365 Defender, [przeczytaj Często zadawane pytania](m365d-enable-faq.md).

Pracownicy pomocy technicznej firmy Microsoft mogą pomóc w zapewnianie obsługi lub wstyczanie obsługi usługi i powiązanych zasobów w Dzierżawie. Aby uzyskać pomoc, wybierz **pozycję Potrzebujesz pomocy?** w portalu Microsoft 365 Defender witryny. Podczas kontaktowania się z pomocą techniczną wspomnimy o Microsoft 365 Defender.

## <a name="related-topics"></a>Tematy pokrewne

- [Często zadawane pytania](m365d-enable-faq.md)
- [Wymagania licencyjne i inne wymagania wstępne](prerequisites.md)
- [Wdrażanie obsługiwanych usług](deploy-supported-services.md)
- [Microsoft 365 Defender omówienie](microsoft-365-defender.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender omówienie](../defender-endpoint/microsoft-defender-endpoint.md)
- [Ochrona usługi Office 365 w usłudze Defender omówienie](../office-365-security/defender-for-office-365.md)
- [Microsoft Defender for Cloud Apps omówienie](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Defender for Identity omówienie](/azure-advanced-threat-protection/what-is-atp)
- [Ochrona punktu końcowego w usłudze Microsoft Defender danych](../defender-endpoint/data-storage-privacy.md)
