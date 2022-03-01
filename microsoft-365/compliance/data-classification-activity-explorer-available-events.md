---
title: Oznaczanie akcji zgłoszonych w Eksploratorze aktywności
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Lista działań etykiet dostępnych w Eksploratorze aktywności.
ms.openlocfilehash: feed9d29deb94263d242967bdef38209cda660e1
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006534"
---
# <a name="labeling-activities-that-are-available-in-activity-explorer"></a>Oznaczanie działań dostępnych w Eksploratorze aktywności

## <a name="sensitivity-label-applied"></a>Zastosowana etykieta wrażliwości

To zdarzenie jest generowane za każdym razem, gdy dokument bez etykiety jest oznaczony lub wiadomość e-mail zostanie wysłana z etykietą wrażliwości.

- Są przechwytywane w czasie zapisywania w Office i aplikacjach sieci Web.
- Dane są przechwytywane w momencie wystąpienia w dodatku usługi Azure Information Protection.
- Działania związane z uaktualnianiem i obniżeniem poziomu etykiet można również monitorować za pomocą filtru *i pola typu* zdarzenia Etykieta.

|Źródło  |Raporty w Eksploratorze aktywności | Uwaga  |
|---------|---------|---------|
| Word, Excel, PowerPoint|Tak |
|Outlook| Tak | |
|SharePoint online, OneDrive|Tak | |
|Exchange        |Tak         | |
|Ujednolicony klient usługi Azure Information Protection (AIP) i ujednolicony skaner AIP |Tak |Nowa *akcja* etykiety programu AIP jest mapowana na *etykietę zastosowaną w* Eksploratorze aktywności   |
|ochrona informacji firmy Microsoft SDK (MIP)         |Tak|Nowa *akcja* etykiety programu AIP jest mapowana na *etykietę zastosowaną w* Eksploratorze aktywności|
|Usługa zarządzania prawami (RMS)         |Nie dotyczy         | |
|Power BI komputer stacjonarny i aplikacja internetowa        | Nie| Dostępne w dziennikach Microsoft 365 inspekcji         |
|Usługa Microsoft Defender dla aplikacji w chmurze         |Nie|         |

## <a name="sensitivity-label-changed"></a>Zmieniono etykietę wrażliwości

To zdarzenie jest generowane za każdym razem, gdy etykieta wrażliwości jest aktualizowana w dokumencie lub wiadomości e-mail.

- W przypadku klienta ujednoliconego programu AIP, źródła zestawu SDK programu Unified Scanner i programu MIP zmieniono  etykietę uaktualniania programu *AIP i* zmieniono mapę akcji etykiety na etykietę *Eksploratora aktywności*

- Jest on przechwytywany w miejscu zapisywania w Office natywnych aplikacjach i aplikacjach sieci Web.
- Jest on przechwytywany w momencie wystąpienia w ujednoliconych dodatekach klienta i wymuszaniach skanera w usłudze Azure Information Protection
- Działania związane z uaktualnianiem i obniżeniem poziomu etykiet można również monitorować za pomocą filtru *i pola typu* zdarzenia Etykieta. Tekst *justowania* jest również przechwytywany z wyjątkiem pól SharePoint Online i OneDrive.
- Etykiety wrażliwości wykonywane w Office natywnych aplikacjach w systemie Outlook zbiera ostatnią akcję wygenerowaną przed zapisaniem pliku lub wysłaniem wiadomości e-mail. Jeśli na przykład użytkownik wielokrotnie zmienia etykietę w wiadomości e-mail przed jej wysłaniem, ostatnia etykieta znaleziona w wysyłanej wiadomości e-mail jest rejestrowana w dzienniku inspekcji, a następnie raportowana w Eksploratorze aktywności.

|Źródło  |Raporty w Eksploratorze aktywności|Uwaga  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Tak         |
|Outlook         |Tak         |
|SharePoint Online, OneDrive         |Tak         |
|Exchange         |Tak         |
|Ujednolicony klient AIP         |Tak         |
|Ujednolicony skaner AIP         |Tak         |
|MIP SDK         |Tak         |
|Usługa RMS         |Nie dotyczy         |
|Power BI aplikacji klasycznej i sieci Web         |Nie         |Dostępne w dziennikach Microsoft 365 inspekcji |
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie         |         |

## <a name="sensitivity-label-removed"></a>Usunięto etykietę wrażliwości

To zdarzenie jest generowane za każdym razem, gdy etykieta wrażliwości zostanie usunięta z pliku lub dokumentu.

- To zdarzenie jest przechwytywane w czasie zapisywania w Office natywnych aplikacjach i aplikacjach sieci Web.
- Dane są przechwytywane w momencie wystąpienia w dodatku usługi Azure Information Protection.
- Etykiety wrażliwości z natywnymi Office MIP na Outlook zbiera ostatnie zdarzenie etykiet wygenerowane przed zapisaniem pliku lub wysłaniem wiadomości e-mail.

|Źródło  |Raporty w Eksploratorze aktywności | Uwaga  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Tak         |
|Outlook         |Tak         ||
|SharePoint Online, OneDrive         |Tak         |
|Exchange         |Tak         |
|Ujednolicony klient AIP         |Tak         |Akcja usuwania etykiety *usługi* AIP jest mapowana *na akcję usunięcia* etykiety w Eksploratorze aktywności|
|Ujednolicony skaner AIP         |Tak         |Akcja usuwania etykiety *usługi* AIP jest mapowana *na akcję usunięcia* etykiety w Eksploratorze aktywności |
|MIP SDK         |Tak         |Akcja usuwania etykiety *usługi* AIP jest mapowana *na akcję usunięcia* etykiety w Eksploratorze aktywności |
|Usługa RMS         |Nie dotyczy         |
|Power BI aplikacji klasycznej i sieci Web         |Nie         |Dostępne w dziennikach Microsoft 365 inspekcji |
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie         |         |

## <a name="sensitivity-label-file-read"></a>Odczytanie pliku etykiet wrażliwości

To zdarzenie jest generowane przy każdym otwarciu dokumentu wrażliwości oznaczonego lub chronionego.

|Źródło  |Raporty w Eksploratorze aktywności | Uwaga  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Tak         |
|Outlook         |Nie         |
|SharePoint Online, OneDrive         |Nie         |
|Exchange         |Nie         |
|Ujednolicony klient AIP         |Tak         |Akcja dostępu *do usługi* AIP jest mapowana na akcję *odczytu pliku* w Eksploratorze aktywności|
|Ujednolicony skaner AIP         |Tak         |Akcja dostępu *do usługi* AIP jest mapowana na akcję *odczytu pliku* w Eksploratorze aktywności|
|MIP SDK         |Tak         |Akcja dostępu *do usługi* AIP jest mapowana na akcję *odczytu pliku* w Eksploratorze aktywności|
|Usługa RMS         |Tak         |Akcja *dostępu* jest zamapowana na akcję odczytu *pliku* w Eksploratorze aktywności |
|Power BI aplikacji klasycznej i sieci Web         |Nie         |Dostępne w dziennikach Microsoft 365 inspekcji |
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie         |         |

## <a name="files-discovered"></a>Odnaleziono pliki

To zdarzenie jest generowane za każdym razem, gdy pliki zostaną wykryte, gdy skaner AIP zostanie użyty do skanowania poufnych danych w różnych lokalizacjach i znajdzie pliki.

|Źródło  |Raporty w Eksploratorze aktywności | Uwaga  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Nie dotyczy         |
|Outlook         |Nie dotyczy         |
|SharePoint Online, OneDrive         |Nie dotyczy         |
|Exchange         |Nie dotyczy         |
|Ujednolicony klient AIP         |Nie dotyczy       |
|Ujednolicony skaner AIP         |Tak         |Akcja odnajdu *usługi* AIP jest zamapowana na akcję *odnajdowanie plików w* Eksploratorze aktywności|
|MIP SDK         |Tak         |Akcja odnajdowanie *przy uchyłce* AIP jest mapowana na akcję odnajdowanie *pliku w* Eksploratorze aktywności|
|Usługa RMS         |Nie dotyczy         |
|Power BI aplikacji klasycznej i sieci Web         |Nie dotyczy         |
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie dotyczy         |         |

## <a name="sensitivity-label-file-renamed"></a>Zmieniono nazwę pliku etykiety wrażliwości

To zdarzenie jest generowane za każdym razem, gdy dokument z etykietą wrażliwości zostanie zmieniony.

|Źródło  | Raporty w Eksploratorze aktywności | Uwaga  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Tak         |
|Outlook         |Nie dotyczy         |
|SharePoint Online, OneDrive         |Nie        |
|Exchange         |Nie dotyczy         |
|Ujednolicony klient AIP         |Nie         |
|Ujednolicony skaner AIP         |Nie         |
|MIP SDK         |Nie         |
|Usługa RMS         |Nie      |
|Power BI aplikacji klasycznej i sieci Web         |Nie         |
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie         |         |

## <a name="file-removed"></a>Usunięto plik

To zdarzenie jest generowane za każdym razem, gdy skaner AIP wykryje, że poprzednio zeskanowany plik został usunięty.

|Źródło  |Raporty w Eksploratorze aktywności | Uwaga  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Nie dotyczy         |
|Outlook         |Nie dotyczy         |
|SharePoint Online, OneDrive         |Nie dotyczy           |
|Exchange         |Nie dotyczy         |
|Ujednolicony klient AIP         |Nie dotyczy            |
|Ujednolicony skaner AIP         |Tak         |
|MIP SDK         |Nie dotyczy            |
|Usługa RMS         |Nie dotyczy         |
|Power BI aplikacji klasycznej i sieci Web         |Nie dotyczy  |
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie dotyczy        |         |

### <a name="protection-applied"></a>Zastosowano ochronę

To zdarzenie jest generowane, gdy ochrona po raz pierwszy jest dodawana ręcznie do elementu, który nie ma etykiety.

|Źródło  |Raporty w Eksploratorze aktywności | Uwaga  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Nie         |
|Outlook         |Nie         |
|SharePoint Online, OneDrive         |Nie dotyczy           |
|Exchange         |Nie       |
|Ujednolicony klient AIP         |Tak            |
|Ujednolicony skaner AIP         |Nie dotyczy         |
|MIP SDK         |Tak            |
|Usługa RMS         |Nie dotyczy         |
|Power BI aplikacji klasycznej i sieci Web         |Nie dotyczy            |
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie dotyczy        |         |

## <a name="protection-changed"></a>Zmieniono ochronę

To zdarzenie jest generowane za każdym razem, gdy ochrona w dokumencie bez etykiety jest zmieniana ręcznie.

|Źródło  |Raporty w Eksploratorze aktywności |
|---------|---------|
|Word, Excel, PowerPoint         |Nie         |
|Outlook         |Nie         |
|SharePoint Online, OneDrive         |Nie dotyczy           |
|Exchange         |Nie       |
|Ujednolicony klient AIP         |Tak            |
|Ujednolicony skaner AIP         |Nie dotyczy         |
|MIP SDK         |Tak            |
|Usługa RMS         |Nie dotyczy         |
|Power BI aplikacji klasycznej i sieci Web         |Nie dotyczy            |
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie dotyczy        |

## <a name="protection-removed"></a>Usunięto ochronę

To zdarzenie jest generowane za każdym razem, gdy ochrona w dokumencie bez etykiety jest zmieniana ręcznie.

|Źródło  |Raporty w Eksploratorze aktywności |
|---------|---------|
|Word, Excel, PowerPoint         |Nie         |
|Outlook         |Nie         |
|SharePoint Online, OneDrive         |Nie dotyczy           |
|Exchange         |Nie       |
|Ujednolicony klient AIP         |Tak            |
|Ujednolicony skaner AIP         |Nie dotyczy         |
|MIP SDK         |Tak            |
|Usługa RMS         |Nie dotyczy         |
|Power BI aplikacji klasycznej i sieci Web         |Nie dotyczy            |
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie dotyczy        |

## <a name="dlp-policy-matched"></a>Dopasowane zasady DLP

To zdarzenie jest generowane za każdym razem, gdy zasady DLP są dopasowane do dokumentu lub wiadomości e-mail.

|Źródło  |Raporty w Eksploratorze aktywności |
|---------|---------|
|Exchange         |Tak       |
|SharePoint Online|Tak          |
|OneDrive |Tak|
|Teams |Tak   |
|Windows 10 urządzenia         |Tak |
|MAC         |Nie     |
|Lokalnie         |Nie|
|Usługa Microsoft Defender dla aplikacji w chmurze     |Nie        |

Zdarzenia dotyczące urządzeń Windows 10 (DLP punktu końcowego) to:

- Usunięto plik
- Utworzono plik
- Plik skopiowany do schowka
- Zmodyfikowano plik
- Odczyt pliku
- Wydrukowano plik
- Nazwa pliku została zmieniona
- Plik skopiowany do udziału sieciowego
- Plik, do którego uzyskano dostęp za pomocą aplikacji niedozwolonej

## <a name="retention-label-applied"></a>Zastosowano etykietę przechowywania

To zdarzenie jest generowane za każdym razem, gdy dokument bez etykiety jest oznaczony lub wiadomość e-mail jest wysyłana z etykietą przechowywania.

- Jest on przechwytywany w czasie zapisywania dokumentu i w czasie wysyłania wiadomości e-mail.

|Źródło  |Raporty w Eksploratorze aktywności |
|---------|---------|
|Exchange         |Nie       |
|SharePoint Online|Tak          |
|OneDrive |Tak|

## <a name="retention-label-changed"></a>Zmieniono etykietę przechowywania

To zdarzenie jest generowane za każdym razem, gdy etykieta jest aktualizowana w dokumencie lub wiadomości e-mail.

- Jest on przechwytywany w czasie zapisywania dokumentu i w czasie wysyłania wiadomości e-mail.

|Źródło  |Raporty w Eksploratorze aktywności |
|---------|---------|
|Exchange         |Nie       |
|SharePoint Online|Tak          |
|OneDrive |Tak|

## <a name="retention-label-removed"></a>Usunięto etykietę przechowywania

To zdarzenie jest generowane za każdym razem, gdy etykieta jest usuwana z pliku lub dokumentu.

- Jest on przechwytywany w czasie zapisywania dokumentu i w czasie wysyłania wiadomości e-mail.

|Źródło  |Raporty w Eksploratorze aktywności |
|---------|---------|
|Exchange         |Nie       |
|SharePoint Online|Tak          |
|OneDrive |Tak|

## <a name="known-issues"></a>Znane problemy
  
- Etykietka zalecana dla użytkownika końcowego nie jest przechwycona. Jeśli jednak użytkownik zdecyduje się zastosować zalecaną etykietę, etykieta będzie wyświetlana w polu *Jak* zastosować jako *zalecane*.

- Tekst uzasadnienia nie jest obecnie dostępny na etykietach wrażliwości na starszą wersję SharePoint i OneDrive.

- Typy informacji poufnych nie są obecnie dostępne dla działań autolabeli z aplikacji Word, Excel, PowerPoint i Outlook, a także w SharePoint Online i OneDrive.
