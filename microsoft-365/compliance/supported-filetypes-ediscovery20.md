---
title: Obsługiwane typy plików zbierania elektronicznych materiałów dowodowych (Premium)
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
description: Lista obsługiwanych typów plików w Microsoft 365 eDiscovery (Premium), w tym typy plików obrazów obsługiwane przez funkcję OCR w funkcji eDiscovery (Premium).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 95adaf84f5281b943720be595b0e0e4aababd91f
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996751"
---
# <a name="supported-file-types-in-ediscovery-premium"></a>Obsługiwane typy plików zbierania elektronicznych materiałów dowodowych (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Usługa Microsoft Purview eDiscovery (Premium) obsługuje wiele typów plików na wielu różnych poziomach. Typy plików pomocy technicznej zostały opisane w poniższych tabelach w tym artykule. Ta lista nie jest finalizowana i dodamy nowe typy plików w miarę kontynuowania testowania walidacji. Te tabele wskazują, czy typ pliku jest obsługiwany w przypadku wyodrębniania tekstu (i optycznego rozpoznawania znaków lub wyodrębniania tekstu OCR dla plików obrazów), który można wyświetlać w natywnej przeglądarce, a także obsługiwać w podglądzie adnotacji w usłudze eDiscovery (Premium).

## <a name="archive--container"></a>Archiwum/kontener

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie kontenerów|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|
|application/x-7z-compressed|Tak|Tak|Tak|.7z|
|application/x-rar-compressed|Tak|Tak|Tak|.rar|
|application/x-tar|Tak|Tak|Tak|.tar|
|application/zip|Tak|Tak|Tak|.zip|
|

## <a name="audio--video"></a>Dźwięk / wideo

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/mp4|Tak|Tak|Nie|Tak|Nie|.f4v; .m4a; .m4v; .mp4; .mp4v; .mpeg; .mpeg4|
|audio/mpeg|Tak|Tak|Nie|Tak|Nie|.mpeg|
|wideo/3gpp|Tak|Tak|Nie|Tak|Nie|.3gp|
|wideo/3gpp2|Tak|Tak|Nie|Tak|Nie|.3g2; .3gp2|
|wideo/szybki czas|Tak|Tak|Nie|Tak|Nie|.moov; .mov; .qt|
|wideo/x-m4v|Tak|Tak|Nie|Tak|Nie|.m4v|
|

## <a name="database"></a>Database

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-msaccess|Tak|Tak|Tak|Nie|Nie|.mdb|
|

## <a name="email"></a>Poczta e-mail

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-outlook|Tak|Tak|Tak|Tak|Tak|.msg|
|message/rfc822|Tak|Tak|Tak|Tak|Tak|.eml|
|text/vcard-contact|Tak|Tak|Tak|Tak|Tak|.vcf|
|

## <a name="email-container"></a>Kontener poczty e-mail

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie kontenerów|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|
|application/mbox|Tak|Tak|Tak|.mbox|
|application/vnd.ms-outlook-pst|Tak|Tak|Tak|Pst|
|

## <a name="html"></a>HTML

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/xhtml+xml|Tak|Tak|Tak|Tak|Tak|.xhtml|
|application/xml|Tak|Tak|Tak|Tak|Tak|.xml|
|text/html|Tak|Tak|Tak|Tak|Tak|.htm; .html; .shtml|
|

## <a name="image"></a>Obrazu

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu OCR|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|image/bmp|Tak|Tak|Tak|Tak|Tak|.bmp|
|obraz/emf|Tak|Tak|Tak|Tak|Tak|.emf|
|obraz/gif|Tak|Tak|Tak|Tak|Tak|.gif|
|obraz/jpeg|Tak|Tak|Tak|Tak|Tak|.jpeg; .jpg|
|image/png|Tak|Tak|Tak|Tak|Tak|.png|
|image/svg+xml|Tak|Tak|Tak|Tak|Nie|.svg|
|obraz/tiff|Tak|Tak|Tak|Tak|Tak|.tif|
|image/vnd.dwg|Tak|Tak|Tak|Tak|Tak|.dwg; .dxf|
|image/wmf|Tak|Tak|Tak|Tak|Tak|.wmf|
|

## <a name="microsoft-excel"></a>Microsoft Excel

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-excel|Tak|Tak|Tak|Tak|Tak|.dat; .xls|
|application/vnd.ms-excel.sheet.binary.macroenabled.12|Tak|Tak|Tak|Tak|Nie|Xlsb|
|application/vnd.ms-excel.sheet.macroenabled.12|Tak|Tak|Tak|Tak|Tak|.xlsm|
|application/vnd.ms-excel.template.macroenabled.12|Tak|Tak|Tak|Nie|Nie|Xltm|
|application/vnd.openxmlformats-officedocument.spreadsheetml.sheet|Tak|Tak|Tak|Tak|Tak|.xlsx|
|application/vnd.openxmlformats-officedocument.spreadsheetml.template|Tak|Tak|Tak|Tak|Tak|Xltx|
|

## <a name="microsoft-onenote"></a>Microsoft OneNote

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/onenote|Tak|Tak|Tak|Nie|Nie|.one|
|

## <a name="microsoft-powerpoint"></a>Microsoft PowerPoint

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-powerpoint|Tak|Tak|Tak|Tak|Tak|.pot; pps; .ppt|
|application/vnd.openxmlformats-officedocument.presentationml.presentation|Tak|Tak|Tak|Tak|Tak|.pptx|
|application/vnd.openxmlformats-officedocument.presentationml.slideshow|Tak|Tak|Tak|Tak|Tak|.ppsx|
|application/vnd.openxmlformats-officedocument.presentationml.template|Tak|Tak|Tak|Tak|Tak|Potx|
|

## <a name="microsoft-project"></a>Microsoft Project

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-project|Tak|Tak|Tak|Nie|Tak|.mpp|
|

## <a name="microsoft-publisher"></a>Microsoft Publisher

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-mspublisher|Tak|Tak|Tak|Tak|Tak|.pub|
|

## <a name="microsoft-visio"></a>Microsoft Visio

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-visio.drawing|Tak|Tak|Tak|Tak|Nie||
|application/vnd.visio|Tak|Tak|Tak|Tak|Tak|.vsd|
|

## <a name="microsoft-word"></a>Microsoft Word

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/msword|Tak|Tak|Tak|Tak|Tak|.dat; .doc|
|application/rtf|Tak|Tak|Tak|Tak|Tak|.doc; rtf|
|application/vnd.ms-word.document.macroenabled.12|Tak|Tak|Tak|Tak|Tak|Docm|
|application/vnd.ms-word.template.macroenabled.12|Tak|Tak|Tak|Tak|Tak|Dotm|
|application/vnd.openxmlformats-officedocument.wordprocessingml.document|Tak|Tak|Tak|Tak|Tak|.docx|
|application/vnd.openxmlformats-officedocument.wordprocessingml.template|Tak|Tak|Tak|Tak|Tak|.dotx|
|

## <a name="microsoft-works"></a>Microsoft Works

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-works-ss|Tak|Tak|Nie|Nie|Nie|.wps|
|application/vnd.ms-works-wp|Tak|Tak|Nie|Nie|Nie|.wps|
|

## <a name="open-document-format"></a>Otwórz format dokumentu

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.oasis.opendocument.text|Tak|Tak|Tak|Tak|Tak|.odt|
|

## <a name="other"></a>Inne

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/json|Tak|Tak|Tak|Tak|Tak|nie dotyczy|
|application/octet-stream|Tak|Nie|Nie|Nie|Nie|.fluid|
|application/vnd.ms-graph|Tak|Tak|Nie|Nie|Nie||
|application/winhlp|Tak|Tak|Nie|Nie|Nie|Hlp|
|application/x-tnef|Tak|Tak|Nie|Nie|Nie||
|

## <a name="plain-text"></a>Zwykły tekst

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|text/csv|Tak|Tak|Tak|Tak|Tak|.csv|
|tekst/zwykły|Tak|Tak|Tak|Tak|Tak|.con; .css; .csv; .dat; .pl; .txt|
|

## <a name="portable-document-format"></a>Format dokumentu przenośnego

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/pdf|Tak|Tak|Tak|Tak|Tak|.pdf|
|

## <a name="word-perfect"></a>Word Perfect

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.wordperfect; version=5.0|Tak|Tak|Tak|Nie|Nie|.wpd|
|application/vnd.wordperfect; version=5.1|Tak|Tak|Tak|Nie|Nie|.wpd|
|application/vnd.wordperfect; version=6.x|Tak|Tak|Tak|Nie|Nie|.wpd|
|

## <a name="word-pro"></a>Pro programu Word

<br>

****

|Typ mime|Identyfikacja pliku|Wyodrębnianie metadanych|Wyodrębnianie tekstu|Przeglądarka natywna|Podgląd adnotacji|Możliwe rozszerzenia|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.lotus-wordpro|Tak|Tak|Nie|Nie|Nie|.lwp|
|
