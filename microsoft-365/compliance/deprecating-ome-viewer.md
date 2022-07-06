---
title: Wycofywanie aplikacji OME Viewer
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
description: Aplikacja przeglądarki Office 365 Message Encryption (OME) została usunięta ze sklepów z systemami Android i Apple w 2018 roku.
ms.openlocfilehash: 2e1e0ead7d34761a3159b4b51368ea4460acb596
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630086"
---
# <a name="deprecating-message-encryption-viewer-app"></a>Przestarzała aplikacja przeglądarki szyfrowania komunikatów

15 sierpnia 2018 r. usunęliśmy aplikację mobilną Office 365 Message Encryption (OME) Viewer ze sklepów z systemami Android i Apple. Aplikacja mobilna Office 365 Message Encryption Viewer była wymagana do odczytywania wiadomości e-mail i załączników zaszyfrowanych przy użyciu poprzedniej wersji protokołu OME na telefonach firmy Apple i Android. Oprócz usunięcia aplikacji OME Viewer nie wprowadzamy żadnych innych zmian w poprzedniej wersji OME.
  
## <a name="changes-from-august-2018"></a>Zmiany z sierpnia 2018 r.

Zgodnie z zapowiedzią z września 2017 r. opublikowaliśmy nową wersję [szyfrowania komunikatów Office 365](https://aka.ms/ome2017), dzięki czemu użytkownicy mogą wysyłać zaszyfrowane i chronione wiadomości do wszystkich osób w organizacji lub poza nią bez konieczności używania aplikacji mobilnej. Od tego czasu dodaliśmy dodatkowe możliwości:
  
- [Szablon tylko do szyfrowania](https://aka.ms/encryptonly)

- [Kontrolka do odszyfrowywania załączników](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)

Dzięki tej zmianie użytkownicy nie będą już mogli pobierać aplikacji mobilnej Office 365 Message Encryption Viewer od 1 sierpnia. W związku z tym adresaci poczty mogą nie być w stanie odczytywać wiadomości zaszyfrowanych przy użyciu poprzedniej wersji protokołu OME na niektórych urządzeniach przenośnych z systemami Android i Apple. Jednak nadal będą mogli odczytywać te komunikaty na komputerach osobistych (za pośrednictwem przeglądarek klasycznych). Użytkownicy, którzy już pobrali aplikację, nadal będą mogli z niej korzystać.
  
## <a name="why-this-change-was-made"></a>Dlaczego ta zmiana została wprowadzona

Nowa wersja protokołu OME nie wymaga już od aplikacji mobilnej odczytywania chronionych wiadomości e-mail i załączników. Klienci korzystający z Szyfrowanie wiadomości w Microsoft Purview mogą wyświetlać chroniony komunikat w programie Outlook dla urządzeń przenośnych, a użytkownicy niebędący klientami mogą wyświetlać chronione komunikaty w przeglądarce.
  
Wymaganie od użytkowników pobierania aplikacji mobilnej to kolejna przeszkoda dla klientów w wyświetlaniu chronionych komunikatów. Szyfrowanie wiadomości w Microsoft Purview zapewnia lepsze środowisko mobilne.
  
## <a name="can-i-still-use-the-previous-version-of-office-365-message-encryption"></a>Czy nadal mogę używać poprzedniej wersji szyfrowania komunikatów Office 365

Poprzednia wersja szyfrowania komunikatów Office 365 nie będzie obecnie przestarzała, jednak wprowadziliśmy znaczące ulepszenia Szyfrowanie wiadomości w Microsoft Purview, które ułatwiają szyfrowanie i ochronę poufnych danych wszystkim osobom i na dowolnym urządzeniu, w tym możliwość odczytywania chronionych wiadomości bezpośrednio w programie Outlook  (komputery stacjonarne, urządzenia przenośne i sieć Web).
  
## <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Co muszę zrobić, aby przygotować się do tej zmiany

Jeśli organizacja wysyła obecnie zaszyfrowane załączniki do adresatów, którzy wymagają aplikacji OME Viewer, należy zaktualizować dokumentację i zasoby szkoleniowe.
  
Zalecamy zaktualizowanie istniejących reguł przepływu poczty programu Exchange w celu użycia Szyfrowanie wiadomości w Microsoft Purview, aby organizacja mogła korzystać z nowych i ulepszonych możliwości. Po skonfigurowaniu Szyfrowanie wiadomości w Microsoft Purview adresaci nie będą potrzebować aplikacji OME Viewer do odczytywania zaszyfrowanych wiadomości na urządzeniach przenośnych.
  
Firma Microsoft zaleca, aby zaplanować przejście do Szyfrowanie wiadomości w Microsoft Purview, gdy tylko będzie to uzasadnione dla Twojej organizacji. Aby uzyskać instrukcje, zobacz [Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](set-up-new-message-encryption-capabilities.md). Jeśli chcesz dowiedzieć się więcej na temat sposobu działania szyfrowania komunikatów, zobacz [Szyfrowanie komunikatów](ome.md).
