---
title: Typy plików obsługiwane w programie Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Lista obsługiwanych typów plików w p Microsoft 365 Advanced eDiscovery, w tym typy plików obrazów obsługiwane przez funkcję OCR w Advanced eDiscovery.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 96d469d861be3392108b53811478f94d0e59f40b
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015957"
---
# <a name="supported-file-types-in-advanced-ediscovery"></a>Typy plików obsługiwane w programie Advanced eDiscovery

Advanced eDiscovery obsługuje wiele typów plików na wielu różnych poziomach. Typy plików pomocy technicznej są opisane w poniższych tabelach w tym artykule. Ta lista nie jest sfinalizowana i dodamy nowe typy plików w ramach kontynuowania testów sprawdzania poprawności. Te tabele wskazują, czy obsługiwany jest typ pliku wyodrębniania tekstu (oraz optyczne rozpoznawanie znaków lub wyodrębnianie tekstu OCR w przypadku plików obrazów), który można przeglądać w natywnej przeglądarce, a także obsługuje przeglądarkę adnotacji w programie Advanced eDiscovery.

## <a name="archive--container"></a>Archiwum / kontener

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie kontenerów|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|
|application/x-7z-compressed|Tak|Tak|Tak|0,7z|
|application/x-rar-compressed|Tak|Tak|Tak|.rar|
|application/x-tar|Tak|Tak|Tak|tar|
|application/zip|Tak|Tak|Tak|.zip|
|

## <a name="audio--video"></a>Audio/wideo

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/mp4|Tak|Tak|Nie|Tak|Nie|f4v; m4a; m4v; .mp4; mp4v; .mpeg; mpeg4|
|audio/mpeg|Tak|Tak|Nie|Tak|Nie|.mpeg|
|video/3gpp|Tak|Tak|Nie|Tak|Nie|3gp|
|video/3gpp2|Tak|Tak|Nie|Tak|Nie|3g2; 3gp2|
|wideo/quicktime|Tak|Tak|Nie|Tak|Nie|moov; mov; qt|
|video/x-m4v|Tak|Tak|Nie|Tak|Nie|m4v|
|

## <a name="database"></a>Database

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-msaccess|Tak|Tak|Tak|Nie|Nie|mdb|
|

## <a name="email"></a>Poczta e-mail

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-outlook|Tak|Tak|Tak|Tak|Tak|msg|
|message/rfc822|Tak|Tak|Tak|Tak|Tak|eml|
|text/vcard-contact|Tak|Tak|Tak|Tak|Tak|vcf|
|

## <a name="email-container"></a>Kontener poczty e-mail

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie kontenerów|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|
|application/mbox|Tak|Tak|Tak|mbox|
|application/vnd.ms-outlook-pst|Tak|Tak|Tak|pst|
|

## <a name="html"></a>HTML

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/xhtml+xml|Tak|Tak|Tak|Tak|Tak|xhtml|
|application/xml|Tak|Tak|Tak|Tak|Tak|.xml|
|text/html|Tak|Tak|Tak|Tak|Tak|.htm; .html; shtml|
|

## <a name="image"></a>Obraz

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu przez OCR|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|image/bmp|Tak|Tak|Tak|Tak|Tak|.bmp|
|image/emf|Tak|Tak|Tak|Tak|Tak|emf|
|image/gif|Tak|Tak|Tak|Tak|Tak|.gif|
|image/jpeg|Tak|Tak|Tak|Tak|Tak|jpeg; .jpg|
|obraz/png|Tak|Tak|Tak|Tak|Tak|.png|
|image/svg+xml|Tak|Tak|Tak|Tak|Nie|svg|
|image/tiff|Tak|Tak|Tak|Tak|Tak|tif|
|image/vnd.dwg|Tak|Tak|Tak|Tak|Tak|dwg; dxf|
|image/wmf|Tak|Tak|Tak|Tak|Tak|wmf|
|

## <a name="microsoft-excel"></a>Microsoft Excel

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-excel|Tak|Tak|Tak|Tak|Tak|dat; .xls|
|application/vnd.ms-excel.sheet.binary.macroenabled.12|Tak|Tak|Tak|Tak|Nie|xlsb|
|application/vnd.ms-excel.sheet.macroenabled.12|Tak|Tak|Tak|Tak|Tak|xlsm|
|application/vnd.ms-excel.template.macroenabled.12|Tak|Tak|Tak|Nie|Nie|xltm|
|application/vnd.openxmlformats-officedocument.spreadsheetml.sheet|Tak|Tak|Tak|Tak|Tak|.xlsx|
|application/vnd.openxmlformats-officedocument.spreadsheetml.template|Tak|Tak|Tak|Tak|Tak|xltx|
|

## <a name="microsoft-onenote"></a>Microsoft OneNote

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/onenote|Tak|Tak|Tak|Nie|Nie|one|
|

## <a name="microsoft-powerpoint"></a>Microsoft PowerPoint

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-powerpoint|Tak|Tak|Tak|Tak|Tak|pot; pps; .ppt|
|application/vnd.openxmlformats-officedocument.presentationml.presentation|Tak|Tak|Tak|Tak|Tak|.pptx|
|application/vnd.openxmlformats-officedocument.presentationml.slideshow|Tak|Tak|Tak|Tak|Tak|ppsx|
|application/vnd.openxmlformats-officedocument.presentationml.template|Tak|Tak|Tak|Tak|Tak|potx|
|

## <a name="microsoft-project"></a>Microsoft Project

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-project|Tak|Tak|Tak|Nie|Tak|mpp|
|

## <a name="microsoft-publisher"></a>Microsoft Publisher

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-mspublisher|Tak|Tak|Tak|Tak|Tak|pub|
|

## <a name="microsoft-visio"></a>Microsoft Visio

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-visio.drawing|Tak|Tak|Tak|Tak|Nie||
|application/vnd.visio|Tak|Tak|Tak|Tak|Tak|vsd|
|

## <a name="microsoft-word"></a>Microsoft Word

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/msword|Tak|Tak|Tak|Tak|Tak|dat; .doc|
|application/rtf|Tak|Tak|Tak|Tak|Tak|.doc; rtf|
|application/vnd.ms-word.document.macroenabled.12|Tak|Tak|Tak|Tak|Tak|docm|
|application/vnd.ms-word.template.macroenabled.12|Tak|Tak|Tak|Tak|Tak|dotm|
|application/vnd.openxmlformats-officedocument.wordprocessingml.document|Tak|Tak|Tak|Tak|Tak|.docx|
|application/vnd.openxmlformats-officedocument.wordprocessingml.template|Tak|Tak|Tak|Tak|Tak|dotx|
|

## <a name="microsoft-works"></a>Microsoft Works

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-works-ss|Tak|Tak|Nie|Nie|Nie|wps|
|application/vnd.ms-works-wp|Tak|Tak|Nie|Nie|Nie|wps|
|

## <a name="open-document-format"></a>Otwórz format dokumentu

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.oasis.opendocument.text|Tak|Tak|Tak|Tak|Tak|odt|
|

## <a name="other"></a>Inne

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/json|Tak|Tak|Tak|Tak|Tak|n/a|
|application/octet-stream|Tak|Nie|Nie|Nie|Nie|fluid|
|application/vnd.ms-graph|Tak|Tak|Nie|Nie|Nie||
|application/winhlp|Tak|Tak|Nie|Nie|Nie|hlp|
|application/x-tnef|Tak|Tak|Nie|Nie|Nie||
|

## <a name="plain-text"></a>Zwykły tekst

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|tekst/csv|Tak|Tak|Tak|Tak|Tak|.csv|
|tekst/zwykły|Tak|Tak|Tak|Tak|Tak|con; .css; .csv; dat; .pl; .txt|
|

## <a name="portable-document-format"></a>Portable Document Format

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/pdf|Tak|Tak|Tak|Tak|Tak|.pdf|
|

## <a name="word-perfect"></a>Word Perfect

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.wordperfect; version=5,0|Tak|Tak|Tak|Nie|Nie|wpd|
|application/vnd.wordperfect; version=5,1|Tak|Tak|Tak|Nie|Nie|wpd|
|application/vnd.wordperfect; version=6.x|Tak|Tak|Tak|Nie|Nie|wpd|
|

## <a name="word-pro"></a>Word Pro

<br>

****

|Typ mime|Identyfikacja plików|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Przeglądarka adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.lotus-wordpro|Tak|Tak|Nie|Nie|Nie|doc|
|
