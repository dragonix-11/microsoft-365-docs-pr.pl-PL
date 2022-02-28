---
title: Przestarzała aplikacja do szyfrowania wiadomości
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6336cabb-b06e-402f-9e85-8bb9eb4ce68f
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Aplikacja przeglądarka Szyfrowanie wiadomości usługi Office 365 (OME) została usunięta ze sklepów Android i Apple w 2018 roku.
ms.openlocfilehash: 0eded17f4da5347e1f1a88031a780cee5f8b1dee
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983168"
---
# <a name="deprecating-message-encryption-viewer-app"></a>Przestarzała aplikacja do szyfrowania wiadomości

15 sierpnia 2018 r. usunęliśmy aplikację mobilną Szyfrowanie wiadomości usługi Office 365 (OME) Viewer ze sklepów Android i Apple. Ta przeglądarka szyfrowanych wiadomości usługi Office 365 mobilna była wymagana do odczytywania wiadomości e-mail i załączników, które były szyfrowane przy użyciu poprzedniej wersji OME na telefonach firmy Apple i z systemem Android. Oprócz usunięcia aplikacji Przeglądarka OME nie wprowadzamy żadnych innych zmian w poprzedniej wersji usługi OME.
  
## <a name="changes-from-august-2018"></a>Zmiany z sierpnia 2018 r.

Zgodnie z ogłoszeniami z września 2017 r. opublikowano nową wersję pakietu [Szyfrowanie wiadomości usługi Office 365](https://aka.ms/ome2017), która umożliwia użytkownikom wysyłanie zaszyfrowanych i chronionych wiadomości do wszystkich osób w organizacji i poza nią bez wymagania aplikacji mobilnej. Od tego czasu dodaliśmy kolejne funkcje:
  
- [Szablon tylko do szyfrowania](https://aka.ms/encryptonly)

- [Kontrolka do odszyfrowywania załączników](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)

Dzięki tej zmianie użytkownicy nie będą już mogli pobierać aplikacji mobilnej przeglądarka szyfrowanych wiadomości usługi Office 365 od 1 sierpnia. W efekcie adresaci poczty mogą nie być w stanie odczytać wiadomości zaszyfrowanych przy użyciu poprzedniej wersji OME na niektórych urządzeniach przenośnych z systemami Android i Apple. Jednak nadal będą mogli czytać te wiadomości na komputerach osobistych (za pośrednictwem przeglądarek komputerowych). Użytkownicy, którzy już pobrali aplikację, nadal będą mogli jej używać.
  
## <a name="why-this-change-was-made"></a>Dlaczego ta zmiana została w w związku z tym w wąsach

Nowa wersja narzędzia OME nie wymaga już aplikacji mobilnej do odczytywania chronionych wiadomości e-mail i załączników. Klienci korzystający z nowych funkcji OME mogą wyświetlać chronioną wiadomość w aplikacji Outlook, a osoby, które nie są klientami, mogą wyświetlać chronione wiadomości w przeglądarce.
  
Konieczność pobierania aplikacji mobilnej przez użytkowników stanowi kolejną przeszkodę dla klientów do wyświetlania chronionych wiadomości. Nowe funkcje Szyfrowanie wiadomości usługi Office 365 zapewniają lepsze środowisko dla urządzeń przenośnych.
  
## <a name="can-i-still-use-the-previous-version-of-office-365-message-encryption"></a>Czy mimo to mogę używać poprzedniej wersji Szyfrowanie wiadomości usługi Office 365

Poprzednia wersja pakietu Szyfrowanie wiadomości usługi Office 365 nie będzie w tej chwili przestarzała, jednak wprowadzono istotne ulepszenia w nowej wersji pakietu Szyfrowanie wiadomości usługi Office 365 , które ułatwiają szyfrowanie i ochronę praw ważnych danych dowolnej osoby i na dowolnym urządzeniu — w tym możliwość odczytywania chronionych wiadomości przez użytkowników bezpośrednio w aplikacji Outlook (na komputerze stacjonarnym, urządzeniu przenośnym i w sieci Web). 
  
## <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Co muszę zrobić, aby przygotować się na tę zmianę

Jeśli Twoja organizacja obecnie wysyła zaszyfrowane załączniki do adresatów, którzy wymagają aplikacji Przeglądarka OME, zaktualizuj dokumentację i zasoby szkoleniowe.
  
Zalecamy zaktualizowanie istniejących Exchange przepływu poczty e-mail, aby używać bieżącej wersji OME, tak aby Twoja organizacja skorzystała z nowych i ulepszonych możliwości. Po skonfigurowaniu nowych funkcji OME adresaci nie będą potrzebni aplikacji Przeglądarka OME do odczytywania zaszyfrowanych wiadomości na urządzeniach przenośnych.
  
Firma Microsoft zaleca zaplanowanie przeniesienia się do nowych funkcji OME, gdy tylko będzie to uzasadnione dla Twojej organizacji. Aby uzyskać instrukcje, [zobacz Konfigurowanie nowych Szyfrowanie wiadomości usługi Office 365 funkcji](set-up-new-message-encryption-capabilities.md). Jeśli chcesz dowiedzieć się więcej o tym, jak nowe funkcje działają najpierw[, zobacz Szyfrowanie wiadomości usługi Office 365](ome.md).
  

