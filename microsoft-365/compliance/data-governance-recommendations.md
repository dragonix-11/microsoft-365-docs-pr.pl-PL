---
title: Jak jest identyfikowana zawartość dla zaleceń dotyczących ładu danych
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
description: Portal Microsoft 365 Defender i portal zgodności Microsoft Purview udostępniają zalecenia dotyczące zarządzania danymi na podstawie bieżącej konfiguracji organizacji i umożliwiają konfigurowanie elementów za pomocą kilku kliknięć. Niektóre z tych zaleceń wykrywają określoną zawartość w organizacji, a następnie zapewniają zalecane kroki zarządzania tą zawartością. Na przykład zalecenie może wykryć elementy zawierające zawartość o znaczeniu krytycznym dla działania firmy (na przykład uprawnienia adwokata klienta lub informacje NDA), a następnie umożliwić automatyczne stosowanie etykiety przechowywania do tych elementów, aby upewnić się, że są one klasyfikowane i przechowywane zgodnie z potrzebami. W tym temacie wymieniono zalecenia dotyczące ładu danych, które mogą być widoczne, i opisano, jaka zawartość jest wykrywana w celu wyzwolenia każdej z nich.
ms.openlocfilehash: 27fcc5dd07695be355fc15ba2145ffa5540673ca
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637312"
---
# <a name="how-content-is-identified-for-data-governance-recommendations"></a>Jak jest identyfikowana zawartość dla zaleceń dotyczących ładu danych

Portal <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> udostępniają zalecenia dotyczące zarządzania danymi na podstawie bieżącej konfiguracji organizacji i umożliwiają konfigurowanie elementów za pomocą kilku kliknięć. Niektóre z tych zaleceń wykrywają określoną zawartość w organizacji, a następnie zapewniają zalecane kroki zarządzania tą zawartością. Na przykład zalecenie może wykryć elementy zawierające zawartość o znaczeniu krytycznym dla działania firmy (na przykład uprawnienia adwokata klienta lub informacje NDA), a następnie umożliwić automatyczne stosowanie etykiety przechowywania do tych elementów, aby upewnić się, że są one klasyfikowane i przechowywane zgodnie z potrzebami.

W tym temacie wymieniono zalecenia dotyczące ładu danych, które mogą być widoczne, i opisano, jaka zawartość jest wykrywana w celu wyzwolenia każdej z nich.

## <a name="clean-up-voicemail"></a>Czyszczenie poczty głosowej

To zalecenie jest wyświetlane w przypadku wykrycia wiadomości e-mail zidentyfikowanych jako typ wiadomości "poczta głosowa" w skrzynkach pocztowych użytkowników. Dowiedz się więcej o [właściwościach komunikatów w programie Exchange](/exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange).

## <a name="label-attorney-client-privilege-content"></a>Etykieta zawartości uprawnień adwokackiego klienta

To zalecenie jest wyświetlane po spełnieniu jednego z następujących kryteriów.

- Każda kombinacja tych słów kluczowych jest wykrywana w treści wiadomości e-mail:
  - AKP
  - Uprawnienie klienta adwokackiego
  - uprawnienie Attorney-Client
  - Attorney-Client uprzywilejowane

- Każda kombinacja tych słów kluczowych jest wykrywana w plikach programu SharePoint lub OneDrive:
  - AKP
  - Uprawnienie klienta adwokata*
  - Uprawnienie ac

## <a name="retain-audio-files"></a>Zachowywanie plików audio

To zalecenie jest wyświetlane, gdy w programie SharePoint lub OneDrive zostanie wykryty dowolny z następujących typów plików.

- .MP3
- . WMA
- . WAV
- . RA
- . PAMIĘCI RAM
- .RM
- . POŁOWIE
- . OGG
- . AIFF
- . PCM
- . AAC
- . FLAC
- . ALAC

## <a name="retain-cad-files"></a>Zachowywanie plików CAD

To zalecenie jest wyświetlane, gdy w programie SharePoint lub OneDrive zostanie wykryty dowolny z następujących typów plików.

- .3DXML
- . ACIS
- . ŁUKU
- . ASM
- .CAT*
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
- . CHRL
- . PRT
- . PSM
- . PWD
- . SLD*
- . KROK
- . STL
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

To zalecenie jest wyświetlane, gdy w programie SharePoint lub OneDrive zostanie wykryty dowolny z następujących typów plików.

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

To zalecenie jest wyświetlane po spełnieniu jednego z następujących kryteriów.

- Każda kombinacja tych słów kluczowych jest wykrywana w treści wiadomości e-mail:
  - NDA
  - "Umowa o zachowaniu poufności"
  - "Umowa o zachowaniu poufności"

- Każda kombinacja tych słów kluczowych jest wykrywana w plikach .PDF lub .DOC w programie SharePoint lub OneDrive:
  - NDA
  - Umowa o zachowaniu poufności

## <a name="retain-software-development-files"></a>Przechowywanie plików programistycznych

To zalecenie jest wyświetlane, gdy w programie SharePoint lub OneDrive zostanie wykryty dowolny z następujących typów plików.

- . ASAX
- . ASM
- . ASP*
- .BAT
- .CONFIG
- .CS
- . CSS
- . DISCO
- .HTM*
- . INC
- . JAD
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

To zalecenie jest wyświetlane, gdy w programie SharePoint lub OneDrive zostanie wykryty dowolny z następujących typów plików.

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
