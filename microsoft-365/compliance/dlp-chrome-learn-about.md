---
title: Dowiedz się więcej o rozszerzeniu zgodności firmy Microsoft
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
description: Rozszerzenie zgodności firmy Microsoft rozszerza monitorowanie i kontrolowanie działań dotyczących plików oraz akcji zabezpieczających do przeglądarki Google Chrome
ms.openlocfilehash: 15c62369bb8b4fc02926fa0e2b0bfc4834c371ac
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015422"
---
# <a name="learn-about-the-microsoft-compliance-extension"></a>Dowiedz się więcej o rozszerzeniu zgodności firmy Microsoft

[Ochrona przed utratą danych w punkcie końcowym (DLP, endpoint](endpoint-dlp-learn-about.md) data loss prevention) rozszerza możliwości monitorowania aktywności i ochrony usługi Microsoft 365 ochrony przed utratą danych [(DLP, data loss prevention)](dlp-learn-about-dlp.md) do poufnych elementów, które znajdują się Windows 10 urządzeniach. Po dojechiniu urządzeń do rozwiązań zgodności usługi Microsoft 365 informacje o tym, co użytkownicy robią z poufnymi elementami, są widoczne [](data-classification-activity-explorer.md) w Eksploratorze aktywności i można wymusić akcje zabezpieczające przed tymi elementami za pośrednictwem zasad [DLP](create-test-tune-dlp-policy.md).

Po zainstalowaniu rozszerzenia zgodności firmy Microsoft na urządzeniu z systemem Windows 10 organizacje mogą monitorować, kiedy użytkownik próbuje uzyskać dostęp do usługi w chmurze lub przekazać do usługi w chmurze poufny element przy użyciu przeglądarki Google Chrome, i wymuszać akcje zabezpieczające za pośrednictwem funkcji DLP.  

## <a name="activities-you-can-monitor-and-take-action-on"></a>Działania, w których można monitorować i podjąć działania

Rozszerzenie zgodności firmy Microsoft umożliwia inspekcję następujących typów działań, które użytkownicy mogą podjąć w związku z poufnymi elementami na urządzeniach z systemem Windows 10.

działanie |opis  | obsługiwane akcje zasad|
|---------|---------|---------|
|plik skopiowany do chmury  | Wykrywa, kiedy użytkownik próbuje przekazać poufny element do domeny usługi z ograniczeniami za pośrednictwem przeglądarki Chrome. |inspekcja, blokowanie z zastępowaniem, blokowanie|
|wydrukowano plik  |Wykrywa, kiedy użytkownik próbuje wydrukować poufny element otwarty w przeglądarce Chrome na drukarce lokalnej lub sieciowej. |inspekcja, blokowanie z zastępowaniem, blokowanie|
|Plik skopiowany do schowka |Wykrywa, kiedy użytkownik próbuje skopiować informacje z poufnego elementu, który jest przeglądany w przeglądarce Chrome, a następnie wkleja go do innej aplikacji, procesu lub elementu. |inspekcja, blokowanie z zastępowaniem, blokowanie|
|Plik skopiowany do magazynu wymiennego    | Wykrywa, kiedy użytkownik próbuje skopiować poufny element lub informacje z poufnego elementu otwartego w przeglądarce Chrome na nośnik wymienny lub urządzenie USB. |inspekcja, blokowanie z zastępowaniem, blokowanie|
|Plik skopiowany do udziału sieciowego  |Wykrywa, kiedy użytkownik próbuje skopiować poufny element lub informacje z poufnego elementu otwartego w przeglądarce Chrome do udziału sieciowego lub zamapego dysku sieciowego.|inspekcja, blokowanie z zastępowaniem, blokowanie |

## <a name="deployment-process"></a>Proces wdrażania
1. [Wprowadzenie do ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-getting-started.md)
2. [Narzędzia i metody dołączania do Windows 10 urządzeniach](device-onboarding-overview.md)
3. [Zainstaluj rozszerzenie na Windows 10 urządzeniach](dlp-chrome-get-started.md)
4. [Tworzenie lub edytowanie zasad DLP ograniczające](create-test-tune-dlp-policy.md) przekazywanie do usługi w chmurze lub uzyskiwanie do nich dostępu przez niedozwolone akcje przeglądarek i stosowanie ich do twoich Windows 10 urządzeniach

## <a name="next-steps"></a>Następne kroki

Zobacz [Wprowadzenie do rozszerzenia zgodności firmy Microsoft, aby](dlp-chrome-get-started.md) uzyskać pełne procedury i scenariusze wdrażania.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do rozszerzenia zgodności firmy Microsoft](dlp-chrome-get-started.md)
- [Dowiedz się więcej Microsoft 365 ochrony przed utratą danych w punktach końcowych](endpoint-dlp-learn-about.md)
- [Wprowadzenie do ochrony przed utratą danych w punktach końcowych firmy Microsoft](endpoint-dlp-getting-started.md)
- [Korzystanie z ochrony przed utratą danych w punkcie końcowym firmy Microsoft](endpoint-dlp-using.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md)
