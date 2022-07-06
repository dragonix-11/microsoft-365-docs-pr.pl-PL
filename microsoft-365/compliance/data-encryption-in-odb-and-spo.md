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
description: Omówienie podstawowych elementów szyfrowania zabezpieczeń danych w usługach OneDrive dla Firm i SharePoint Online.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5b56caed2a93bf482509a4a90a8bbc3a828d76e7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630152"
---
# <a name="data-encryption-in-onedrive-for-business-and-sharepoint-online"></a>Data Encryption in OneDrive for Business and SharePoint Online

Omówienie podstawowych elementów szyfrowania zabezpieczeń danych w usługach OneDrive dla Firm i SharePoint Online.
  
## <a name="security-and-data-encryption-in-office-365"></a>Zabezpieczenia i szyfrowanie danych w Office 365

Microsoft 365 to wysoce bezpieczne środowisko, które oferuje szeroką ochronę w wielu warstwach: zabezpieczenia fizycznego centrum danych, zabezpieczenia sieci, zabezpieczenia dostępu, zabezpieczenia aplikacji i zabezpieczenia danych. Ten artykuł koncentruje się w szczególności na przesyłanej i spoczynkowej stronie szyfrowania zabezpieczeń danych dla usług OneDrive dla Firm i SharePoint Online.
  
Obejrzyj, jak działa szyfrowanie danych w poniższym filmie wideo.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/dea0dec4-4077-4095-9a32-19b94ea2da4b?autoplay=false]
  
## <a name="encryption-of-data-in-transit"></a>Szyfrowanie danych podczas przesyłania

W usługach OneDrive dla Firm i SharePoint Online istnieją dwa scenariusze, w których dane wchodzą do centrów danych i zamykają je.
  
- **Komunikacja klienta z serwerem** Komunikacja z OneDrive dla Firm przez Internet używa połączeń SSL/TLS. Wszystkie połączenia SSL są nawiązywane przy użyciu kluczy 2048-bitowych.

- **Przenoszenie danych między centrami danych** Głównym powodem przenoszenia danych między centrami danych jest replikacja geograficzna umożliwiająca odzyskiwanie po awarii. Na przykład SQL Server dzienniki transakcji i różnice magazynu obiektów blob przemieszczają się wzdłuż tego potoku. Chociaż te dane są już przesyłane za pomocą sieci prywatnej, są dodatkowo chronione za pomocą najlepszego w klasie szyfrowania. 

## <a name="encryption-of-data-at-rest"></a>Szyfrowanie danych magazynowanych

Szyfrowanie w spoczynku obejmuje dwa składniki: BitLocker szyfrowanie na poziomie dysku i szyfrowanie zawartości klienta według pliku.
  
BitLocker jest wdrażany dla OneDrive dla Firm i usługi SharePoint Online w całej usłudze. Szyfrowanie plików jest również dostępne w usługach OneDrive dla Firm i SharePoint Online w wielu dzierżawach platformy Microsoft 365 oraz w nowych środowiskach dedykowanych opartych na technologii wielodostępnej.
  
Chociaż BitLocker szyfruje wszystkie dane na dysku, szyfrowanie poszczególnych plików idzie jeszcze dalej, dołączając unikatowy klucz szyfrowania dla każdego pliku. Ponadto każda aktualizacja każdego pliku jest szyfrowana przy użyciu własnego klucza szyfrowania. Klucze do zaszyfrowanej zawartości są przechowywane w fizycznie oddzielonej lokalizacji od zawartości. Każdy krok tego szyfrowania używa standardu Advanced Encryption Standard (AES) z kluczami 256-bitowymi i jest zgodny ze standardem FIPS (Federal Information Processing Standard) 140-2. Zaszyfrowana zawartość jest dystrybuowana w wielu kontenerach w centrum danych, a każdy kontener ma unikatowe poświadczenia. Te poświadczenia są przechowywane w oddzielnej lokalizacji fizycznej od zawartości lub kluczy zawartości.
  
Aby uzyskać dodatkowe informacje na temat zgodności z standardem FIPS 140-2, zobacz [Zgodność FIPS 140-2](/previous-versions/sql/sql-server-2008-r2/bb326611(v=sql.105)).
  
Szyfrowanie na poziomie plików w spoczynku korzysta z magazynu obiektów blob w celu zapewnienia praktycznie nieograniczonego wzrostu magazynu i zapewnienia bezprecedensowej ochrony. Cała zawartość klienta w usługach OneDrive dla Firm i SharePoint Online zostanie zmigrowana do magazynu obiektów blob. Poniżej przedstawiono sposób zabezpieczania tych danych:
  
1. Cała zawartość jest szyfrowana, potencjalnie z wieloma kluczami i dystrybuowana w centrum danych. Każdy plik, który ma być przechowywany, jest podzielony na co najmniej jeden fragment w zależności od jego rozmiaru. Następnie każdy fragment jest szyfrowany przy użyciu własnego unikatowego klucza. Aktualizacje są obsługiwane podobnie: zestaw zmian lub różnic przesyłanych przez użytkownika jest podzielony na fragmenty, a każdy z nich jest szyfrowany przy użyciu własnego klucza.

2. Wszystkie te fragmenty — pliki, fragmenty plików i różnice aktualizacji — są przechowywane jako obiekty blob w naszym magazynie obiektów blob. Są one również losowo dystrybuowane między wieloma kontenerami obiektów blob.

3. "Mapa" używana do ponownego zmontowania pliku z jego składników jest przechowywana w bazie danych zawartości.

4. Każdy kontener obiektów blob ma własne unikatowe poświadczenia na typ dostępu (odczyt, zapis, wyliczanie i usuwanie). Każdy zestaw poświadczeń jest przechowywany w bezpiecznym magazynie kluczy i jest regularnie odświeżany.

Innymi słowy, istnieją trzy różne typy magazynów zaangażowanych w szyfrowanie poszczególnych plików magazynowanych, z których każdy ma odrębną funkcję:
  
- Zawartość jest przechowywana jako zaszyfrowane obiekty blob w magazynie obiektów blob. Klucz do każdego fragmentu zawartości jest szyfrowany i przechowywany oddzielnie w bazie danych zawartości. Sama zawartość nie ma pojęcia, jak można ją odszyfrować.

- Baza danych zawartości jest bazą danych SQL Server. Przechowuje ona mapę wymaganą do zlokalizowania i ponownego zszywania wszystkich obiektów blob zawartości przechowywanych w magazynie obiektów blob, a także kluczy potrzebnych do odszyfrowania tych obiektów blob.

Każdy z tych trzech składników magazynu — magazyn obiektów blob, baza danych zawartości i magazyn kluczy — jest fizycznie oddzielony. Informacje przechowywane w jednym ze składników są bezużyteczne samodzielnie. Zapewnia to bezprecedensowy poziom bezpieczeństwa. Bez dostępu do wszystkich trzech nie można pobrać kluczy do fragmentów, odszyfrować klucze, aby były użyteczne, skojarzyć klucze z odpowiednimi fragmentami, odszyfrować dowolny fragment lub zrekonstruować dokument z jego fragmentów składowych.
