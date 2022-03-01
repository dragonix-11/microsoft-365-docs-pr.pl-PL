---
title: Reguły aplikacji/testu
description: Reguły, które mają być stosowane podczas przekazywania aplikacji/testu
search.appverid: MET150
author: andreicsibi-msft
ms.author: ancsibi
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 02/04/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: cebf888d7a17d6d589888d529cea1731b666f562
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016033"
---
# <a name="applicationtest-rules"></a>Reguły aplikacji/testu

Wszystkie aplikacje lub testy z bazy testowej muszą być zgodne z następującymi regułami:

## <a name="test-base-folders"></a>Test Base folders 

Następujące foldery są używane przez infrastrukturę bazy testowej:
* %SYSTEMDRIVE%\USL
* %SYSTEMDRIVE%\EtlExport
* %SYSTEMDRIVE%\Ffmpeg
* %SYSTEMDRIVE%\Monitoring
* %SYSTEMDRIVE%\powershell-yaml
* %SYSTEMDRIVE%\ProcMon
* %SYSTEMDRIVE%\PSTools
* %SYSTEMDRIVE%\TokenProviderTool
* %SYSTEMDRIVE%\USLPowershellModules
* %SYSTEMDRIVE%\UtcUtil
* %SYSTEMDRIVE%\WPT
* %SYSTEMDRIVE%\WULogs

> [!IMPORTANT]
> **Należy unikać następujących czynności**:
> * Blokowanie wykonywania jakiejkolwiek procedury z poziomu tych folderów. Jeśli Twoja aplikacja jest oprogramowaniem chroniącym przed złośliwym oprogramowaniem, skonfiguruj instalację aplikacji, aby umożliwić niechcący wykonanie wszystkich procesów z tych folderów.
> * Manipulowanie dowolnym z tych folderów.

## <a name="test-base-registry-keys"></a>Test Base registry keys

Aplikacje/testy nie powinny usuwać ani modyfikować kluczy rejestru związanych z:
* Windows telemetrii
* Usuwanie TLS 1.2
