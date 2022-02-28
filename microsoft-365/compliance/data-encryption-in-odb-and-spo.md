---
title: Data Encryption in OneDrive for Business and SharePoint Online
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 9/20/2021
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
description: Opis podstawowych elementów szyfrowania dla zabezpieczeń danych w usługach OneDrive dla Firm i SharePoint Online.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 25bebc8fd5ab9b820667f5220785b021230ca6e1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985643"
---
# <a name="data-encryption-in-onedrive-for-business-and-sharepoint-online"></a>Data Encryption in OneDrive for Business and SharePoint Online

Opis podstawowych elementów szyfrowania dla zabezpieczeń danych w usługach OneDrive dla Firm i SharePoint Online.
  
## <a name="security-and-data-encryption-in-office-365"></a>Zabezpieczenia i szyfrowanie danych w Office 365

Microsoft 365 to wysoce bezpieczne środowisko, które zapewnia obszerną ochronę na wielu warstwach: fizyczne zabezpieczenia centrum danych, zabezpieczenia sieci, zabezpieczenia dostępu, zabezpieczenia aplikacji i zabezpieczenia danych. W tym artykule skupiono się w szczególności na stronie szyfrowania danych podczas przesyłania i szyfrowania danych w miejscu dla aplikacji OneDrive dla Firm i SharePoint Online.
  
Obejrzyj poniższy klip wideo, aby dowiedzieć się, jak działa szyfrowanie danych.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/dea0dec4-4077-4095-9a32-19b94ea2da4b?autoplay=false]
  
## <a name="encryption-of-data-in-transit"></a>Szyfrowanie danych podczas przesyłania

W OneDrive dla Firm i SharePoint Online istnieją dwa scenariusze, w których dane są wprowadzane i zamykane przez centra danych.
  
- **Komunikacja z klientem z serwerem** Komunikacja z OneDrive dla Firm Internecie korzysta z połączeń SSL/TLS. Wszystkie połączenia SSL są ustanowione przy użyciu kluczy 2048-bitowych.

- **Ruch danych między centrami danych** Główną przyczyną przenoszenia danych między centrami danych jest replikacja geograficzna w celu umożliwienia odzyskiwania po awarii. Na przykład dzienniki SQL Server i różnicy magazynu obiektów blob są przemieszczane wzdłuż tej potoku. Te dane są już przesyłane przy użyciu sieci prywatnej, ale są dodatkowo chronione przy użyciu najlepszego szyfrowania w swojej klasie. 

## <a name="encryption-of-data-at-rest"></a>Szyfrowanie danych w spoczynku

Szyfrowanie w spoczynku obejmuje dwa składniki: szyfrowanie na poziomie dysku funkcji BitLocker i szyfrowanie zawartości dla plików klientów.
  
BitLocker jest wdrażana dla OneDrive dla Firm i SharePoint Online w całej usłudze. Szyfrowanie według plików jest również dostępne w usługach OneDrive dla Firm i SharePoint Online Microsoft 365 wielodostępnych i nowych środowisk dedykowanych, które są zbudowane na technologii wielodostępnych.
  
Mimo że funkcja BitLocker szyfruje wszystkie dane na dysku, szyfrowanie dla poszczególnych plików działa jeszcze bardziej, uwzględniając unikatowy klucz szyfrowania dla każdego pliku. Ponadto każda aktualizacja każdego pliku jest szyfrowana przy użyciu własnego klucza szyfrowania. Klucze zaszyfrowanej zawartości są przechowywane w fizycznie oddzielnej lokalizacji od tej zawartości. Każdy krok tego szyfrowania korzysta Advanced Encryption Standard (AES) z kluczami 256-bitowym i jest zgodny ze standardem Federal Information Processing Standard (FIPS) 140-2. Zaszyfrowana zawartość jest rozpowszechniana w wielu kontenerach w całym centrum danych, a każdy kontener ma unikatowe poświadczenia. Te poświadczenia są przechowywane w oddzielnej lokalizacji fizycznej, od zawartości lub kluczy zawartości.
  
Aby uzyskać dodatkowe informacje na temat zgodności z standardem FIPS 140-2, zobacz Zgodność z normą [FIPS 140-2](/previous-versions/sql/sql-server-2008-r2/bb326611(v=sql.105)).
  
Szyfrowanie na poziomie pliku w spoczynku wykorzystuje magazyn obiektów blob, aby zapewnić praktycznie nieograniczony wzrost przestrzeni dyskowej i włączyć ochronę przed niebem. Cała zawartość klientów w usługach OneDrive dla Firm i SharePoint Online zostanie migrowana do magazynu obiektów blob. Oto jak te dane są zabezpieczone:
  
1. Cała zawartość jest szyfrowana, potencjalnie za pomocą wielu kluczy i rozłożona w obrębie centrum danych. Każdy plik, który ma być przechowywany, jest po podziale na jeden lub więcej fragmentów, w zależności od jego rozmiaru. Następnie każdy fragment jest szyfrowany przy użyciu własnego unikatowego klucza. Aktualizacje są obsługiwane podobnie: zestaw zmian (różnic) przesłany przez użytkownika jest rozbity na fragmenty i każda z nich jest szyfrowana przy użyciu własnego klucza.

2. Wszystkie te fragmenty — pliki, fragmenty plików i zmiany aktualizacji — są przechowywane jako obiekty blob w naszym magazynie obiektów blob. Są one również rozmieszczone losowo między wieloma kontenerami obiektów blob.

3. "Mapa" używana do ponownego zeskładu pliku na jego składników jest przechowywana w bazie danych zawartości.

4. Każdy kontener obiektów blob ma własne unikatowe poświadczenia dla każdego typu dostępu (odczyt, zapis, wyliczenie i usuwanie). Każdy zestaw poświadczeń jest przechowywane w bezpiecznym magazynie kluczy i regularnie odświeżany.

Innymi słowy istnieją trzy różne typy magazynów związane z szyfrowaniem dla każdego pliku w spoczynku, z których każdy ma odrębną funkcję:
  
- Zawartość jest przechowywana jako zaszyfrowane obiekty blob w magazynie obiektów blob. Klucz do każdego fragmentu zawartości jest zaszyfrowany i przechowywany oddzielnie w bazie danych zawartości. Sama zawartość nie zawiera wskazówki, w jaki sposób można ją odszyfrować.

- Baza danych zawartości jest bazą SQL Server danych. Zawiera mapę wymaganą do lokalizowania i ponownego zesowywania wszystkich obiektów blob zawartości w magazynie obiektów blob, a także kluczy potrzebnych do odszyfrowywania tych obiektów blob.

Każdy z tych trzech składników magazynu — magazyn obiektów blob, baza danych zawartości i magazyn kluczy — są fizycznie oddzielone. Informacje przechowywane w jednym ze składników nie będą samodzielnie używane. Zapewnia to wysoki poziom zabezpieczeń. Bez dostępu do wszystkich trzech fragmentów nie można pobrać kluczy do fragmentów, odszyfrować klucze, aby były użyteczne, skojarzyć klucze z odpowiadającymi im fragmentami, odszyfrować każdy fragment lub odtworzyć dokument na jego fragmentach składowych.