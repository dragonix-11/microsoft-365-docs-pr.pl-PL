---
title: Dowiedz się więcej o rozszerzeniu usługi Microsoft Purview
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Rozszerzenie Microsoft Purview rozszerza monitorowanie i kontrolę działań dotyczących plików i akcji ochronnych na przeglądarkę Google Chrome
ms.openlocfilehash: a74cfeb734f41622d491c8aaffe3a5e054479a2a
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172252"
---
# <a name="learn-about-the-microsoft-purview-extension"></a>Dowiedz się więcej o rozszerzeniu usługi Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

[Ochrona przed utratą danych punktu końcowego (endpoint DLP)](endpoint-dlp-learn-about.md) rozszerza możliwości monitorowania aktywności i ochrony usługi [Microsoft Purview przed utratą danych (DLP)](dlp-learn-about-dlp.md) na poufne elementy znajdujące się na urządzeniach Windows 10. Po dołączeniu urządzeń do rozwiązań Usługi Microsoft Purview informacje o tym, co użytkownicy robią z poufnymi elementami, są widoczne w [Eksploratorze aktywności](data-classification-activity-explorer.md) i można wymuszać akcje ochronne na tych elementach za pośrednictwem [zasad DLP](create-test-tune-dlp-policy.md).

Po zainstalowaniu rozszerzenia na urządzeniu Windows 10 organizacje mogą monitorować, kiedy użytkownik próbuje uzyskać dostęp do poufnego elementu lub przekazać go do usługi w chmurze przy użyciu przeglądarki Google Chrome i wymusić działania ochronne za pośrednictwem usługi DLP.  

## <a name="activities-you-can-monitor-and-take-action-on"></a>Działania, które można monitorować i podejmować działania

Rozszerzenie umożliwia przeprowadzanie inspekcji i zarządzanie następującymi typami działań wykonywanych przez użytkowników na poufnych elementach na urządzeniach z uruchomionymi Windows 10.

Działania |Opis  | obsługiwane akcje zasad|
|---------|---------|---------|
|plik skopiowany do chmury  | Wykrywa, kiedy użytkownik próbuje przekazać poufny element do domeny usługi z ograniczeniami za pośrednictwem przeglądarki Chrome |audit, block with override, block|
|plik drukowany  |Wykrywa, kiedy użytkownik próbuje wydrukować poufny element otwarty w przeglądarce Chrome na drukarce lokalnej lub sieciowej |audit, block with override, block|
|plik skopiowany do schowka |Wykrywa, kiedy użytkownik próbuje skopiować informacje z poufnego elementu wyświetlanego w przeglądarce Chrome, a następnie wkleić je do innej aplikacji, procesu lub elementu. |audit, block with override, block|
|plik skopiowany do magazynu wymiennego    | Wykrywa, kiedy użytkownik próbuje skopiować poufny element lub informacje z poufnego elementu otwartego w przeglądarce Chrome na nośnik wymienny lub urządzenie USB |audit, block with override, block|
|plik skopiowany do udziału sieciowego  |Wykrywa, kiedy użytkownik próbuje skopiować poufny element lub informacje z poufnego elementu otwartego w przeglądarce Chrome na udział sieciowy lub zamapowany dysk sieciowy.|audit, block with override, block |

## <a name="deployment-process"></a>Proces wdrażania
1. [Wprowadzenie z zapobieganiem utracie danych punktu końcowego](endpoint-dlp-getting-started.md)
2. [Narzędzia i metody dołączania dla urządzeń Windows 10](device-onboarding-overview.md)
3. [Instalowanie rozszerzenia na urządzeniach Windows 10](dlp-chrome-get-started.md)
4. [Tworzenie lub edytowanie zasad DLP](create-test-tune-dlp-policy.md) ograniczających przekazywanie do usługi w chmurze lub dostęp przez niedozwolone akcje przeglądarek i stosowanie ich do urządzeń Windows 10

## <a name="next-steps"></a>Następne kroki

Zobacz [Wprowadzenie z rozszerzeniem Microsoft Purview](dlp-chrome-get-started.md), aby zapoznać się z kompletnymi procedurami i scenariuszami wdrażania.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie z rozszerzeniem Microsoft Purview](dlp-chrome-get-started.md)
- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md)
- [Wprowadzenie do zapobiegania utracie danych punktu końcowego](endpoint-dlp-getting-started.md)
- [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie za pomocą Eksploratora działań](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)
