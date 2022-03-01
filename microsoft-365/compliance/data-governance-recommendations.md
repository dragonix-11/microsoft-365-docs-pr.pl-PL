---
title: W jaki sposób zawartość jest identyfikowana na przykład w celu zalecenia w zakresie zarządzania danymi
f1.keywords:
- NOCSH
ms.author: brendonb
author: cabailey
manager: laurawi
ms.date: 1/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.custom: admindeeplinkDEFENDER
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Portal Microsoft 365 Defender i Centrum zgodności platformy Microsoft 365 zawierają zalecenia dotyczące zarządzania danymi oparte na bieżącej konfiguracji Twojej organizacji i umożliwiają konfigurowanie wszystkich danych kilkoma kliknięciami. Niektóre z tych zaleceń wykryły określoną zawartość w organizacji, a następnie podały zalecane kroki zarządzania zawartością. Na przykład zalecenie może wykryć elementy, które zawierają treści o krytycznym znaczeniu dla firmy (takie jak uprawnienia klienta lub informacje o prawach klienta), a następnie pozwolić na automatyczne zastosowanie etykiety przechowywania do tych elementów w celu zapewnienia, że będą one klasyfikowane i zachowywane zgodnie z potrzebami. Ten temat zawiera listę wyświetlonych zaleceń dotyczących zarządzania danymi oraz opis wykrywanych zawartości w celu wyzwalania poszczególnych z nich.
ms.openlocfilehash: cddd73fdd0c21605549450968db182883ab7e6ad
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006171"
---
# <a name="how-content-is-identified-for-data-governance-recommendations"></a>W jaki sposób zawartość jest identyfikowana na przykład w celu zalecenia w zakresie zarządzania danymi

Portal <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender i</a> Centrum zgodności platformy Microsoft 365 zawierają zalecenia dotyczące <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank"></a> zarządzania danymi oparte na bieżącej konfiguracji Twojej organizacji i umożliwiają konfigurowanie wszystkich konfiguracji za pomocą kilku kliknięć. Niektóre z tych zaleceń wykryły określoną zawartość w organizacji, a następnie podały zalecane kroki zarządzania zawartością. Na przykład zalecenie może wykryć elementy, które zawierają treści o krytycznym znaczeniu dla firmy (takie jak uprawnienia klienta lub informacje o prawach klienta), a następnie pozwolić na automatyczne zastosowanie etykiety przechowywania do tych elementów w celu zapewnienia, że będą one klasyfikowane i zachowywane zgodnie z potrzebami.

Ten temat zawiera listę wyświetlonych zaleceń dotyczących zarządzania danymi oraz opis wykrywanych zawartości w celu wyzwalania poszczególnych z nich.

## <a name="clean-up-voicemail"></a>Oczyszczanie poczty głosowej

To zalecenie pojawia się, gdy wiadomości e-mail zidentyfikowane jako "poczta głosowa" są wykrywane w skrzynkach pocztowych użytkowników. Dowiedz się więcej o [właściwościach wiadomości w programie Exchange](/exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange).

## <a name="label-attorney-client-privilege-content"></a>Etykieta zawartości z uprawnieniami klienta

To zalecenie jest wyświetlane, gdy zostanie spełnione którekolwiek z poniższych kryteriów.

- Dowolna kombinacja tych słów kluczowych jest wykrywana w treści wiadomości e-mail:
  - ACP
  - Uprawnienie klienta obsługi klienta obsługi klienta
  - Attorney-Client uprawnień
  - Attorney-Client z uprawnieniami

- Dowolna kombinacja tych słów kluczowych jest wykrywana w SharePoint lub OneDrive plikach:
  - ACP
  - Uprawnienie klienta obsługi klienta prawni*
  - Uprawnienie AC

## <a name="retain-audio-files"></a>Zachowywanie plików audio

To zalecenie pojawia się, gdy dowolny z poniższych typów plików zostanie wykryty w SharePoint lub OneDrive.

- .MP3
- . WMA
- . WAV
- . RA
- . Pamięć RAM
- RM
- . MID
- . OGG
- . AIFF
- . PCM
- . AAC
- . FLAC
- . ALAC

## <a name="retain-cad-files"></a>Zachowywanie plików programu CAD

To zalecenie pojawia się, gdy dowolny z poniższych typów plików zostanie wykryty w SharePoint lub OneDrive.

- 3DXML
- . ACIS
- . ARC
- . ASM
- CAT*
- . CGR
- . DW*
- . DX*
- . EDRW
- . IAM
- . IGES
- . IGS
- . IPT
- . JT
- . MF1
- . NEU
- . PAR
- . PKG
- . ChRL
- . PRT
- . PSM
- . PWD
- . SLD*
- . KROK
- . STL (Czas wygaśnięcia)
- . STP
- . U3D
- . UNV
- . VRML
- . WRL
- . X_*
- . XAS
- . XMT*
- . XPR

## <a name="retain-image-files"></a>Zachowywanie plików obrazów

To zalecenie pojawia się, gdy dowolny z poniższych typów plików zostanie wykryty w SharePoint lub OneDrive.

- . JPEG
- .GIF
- . TIF*
- .BMP
- .PNG
- . RAW
- .PSD
- . PSP
- .JPG
- . EXIF
- . PPM
- . PGM
- . PBM
- . PNM
- . WEBP

## <a name="retain-nda-content"></a>Zachowywanie zawartości NDA

To zalecenie jest wyświetlane, gdy zostanie spełnione którekolwiek z poniższych kryteriów.

- Dowolna kombinacja tych słów kluczowych jest wykrywana w treści wiadomości e-mail:
  - NDA
  - "Umowa o nieu ujawnianiu informacji"
  - "Umowa o nieu ujawnianiu informacji"

- Dowolna kombinacja tych słów kluczowych jest wykrywana w .PDF lub .DOC w SharePoint lub OneDrive:
  - NDA
  - Umowa o nieu ujawnianiu informacji

## <a name="retain-software-development-files"></a>Zachowywanie plików tworzenia oprogramowania

To zalecenie pojawia się, gdy dowolny z poniższych typów plików zostanie wykryty w SharePoint lub OneDrive.

- . ASAX
- . ASM
- . ASP*
- .BAT
- .CONFIG
- CS
- . CSS
- . DISCO
- .HTM*
- . INC
- . JAR
- . JAVA
- .JS*
- . LIB
- . O
- . PHP
- . RC
- . RESX
- . RPT
- . RSS
- . SCPT
- . SRC
- . VB*
- . WSF
- . XCODEPROJ
- .XML
- . XSD
- . XSL*

## <a name="retain-video-files"></a>Zachowywanie plików wideo

To zalecenie pojawia się, gdy dowolny z poniższych typów plików zostanie wykryty w SharePoint lub OneDrive.

- . AVCHD
- .AVI
- . FLV
- . MOV
- . MP2V
- .MP4
- . MP4V
- . MPE
- .MPEG
- . MPEG1
- . MPEG2
- . MPEG4
- .MPG
- . MPG2
- . MPG4
- . WMV
- . XMV
