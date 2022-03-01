---
title: Przygotowywanie mapowanych dysków dla Microsoft Managed Desktop
description: Ważne kroki mające na celu zapewnianie użytkownikom dostępu do danych na zamapowanych dyskach
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: d8100323350b11cb2329d752892cd64b1bc764a0
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016078"
---
# <a name="prepare-mapped-drives-for-microsoft-managed-desktop"></a>Przygotowywanie mapowanych dysków dla Microsoft Managed Desktop

Wiele środowisk przedsiębiorstwa ma starsze wymagania dotyczące zamapowanych dysków, aby umożliwić użytkownikom lub zespołom udostępnianie i przechowywanie plików lub aplikacji lokalnych.

Firma Microsoft nie zaleca używania zamapowanych dysków ze Microsoft Managed Desktop. Zamiast tego zalecamy unowocześninie rozwiązań dostępu do plików w następujący sposób:
  
- Przemigruj zamapowane dyski używane przez poszczególnych użytkowników do OneDrive dla Firm.
- Przemigruj zamapowane dyski używane przez zespoły w celu udostępniania plików do usługi SharePoint Online.
- Unowocześnij lub zastąp wszelkie aplikacje, które korzystają z lokalnych udziałów plików, w celu usunięcia tego wymagania.
  
Unowocześnisz te usługi, aby jak najlepiej świadczyć usługi dla Microsoft Managed Desktop. Usługi FastTrack firmy Microsoft mogą pomóc w dostosowywaniu środowiska za pomocą usług firmy Microsoft w chmurze. Możesz sprawdzić, czy kwalifikujesz się do korzystania z usług FastTrack w [kwalifikujących się usługach i planach](/fasttrack/m365-eligible-services-and-plans). Następnie skontaktuj się z nimi bezpośrednio, aby przygotować się do Microsoft Managed Desktop. Aby uzyskać więcej informacji na FastTrack OneDrive dla Firm migracji SharePoint online, zobacz [Migracja danych](/fasttrack/o365-data-migration).

## <a name="mapped-drives-on-microsoft-managed-desktop"></a>Mapowane dyski na Microsoft Managed Desktop

Jeśli w niektórych przypadkach użycia nie można usunąć ani zamienić zamapowanych dysków, należy zgłosić żądanie pomocy technicznej w portalu administracyjnym usługi Microsoft Managed Desktop, aby wdrożyć je u Microsoft Managed Desktop użytkowników.

W przypadku takiego wniosku o pomoc techniczną musisz podać następujące szczegóły:

- Wszystkie ścieżki UNC do lokalizacji udziału plików, które trzeba będzie zamapować na Microsoft Managed Desktop urządzeniach.
- Grupy użytkowników, które wymagają dostępu do tych lokalizacji udziału plików.
- Każda konkretną litera dysku, która musi zostać przypisana (jeśli to konieczne).

Przykład:

| Litera dysku | Ścieżka UNC | Grupa użytkowników |
|--------------|----------|------------|
| X:  | \\\server\share\Marketing | ContosoMarketing |

Pełną odpowiedzialnością użytkownika jest:

- Upewniaj się, że użytkownicy i grupy mają odpowiednie uprawnienia do uzyskiwania dostępu do lokalizacji udostępniania plików
- Lokalne usługi plików mają ułatwienia dostępu.

Wymagania dotyczące takich udziałów plików należy usunąć jak najszybciej.

**Aby wdrożyć mapowane dyski w programie Microsoft Managed Desktop:**

Przed przesłaniem wniosku o pomoc techniczną upewnij się, że nie można uniknąć zamapowanych dysków i dokładnie przejrzyj wymagania.

1. Przejdź do [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i wybierz pozycję **Rozwiązywanie problemów + pomoc techniczna**.
1. W sekcji **Microsoft Managed Desktop** wybierz pozycję **Żądania usługi**.
1. Prześlij wniosek o pomoc techniczną zatytułowany "Wdrożenie mapowanych dysków" i podaj wszystkie wymagane szczegóły udziału plików.  
1. Microsoft Managed Desktop ona będzie zalecać korzystanie z aktualizacji wniosku o pomoc techniczną po jego ukończeniu. Początkowo ta konfiguracja zostanie wdrożona tylko na urządzeniach w grupie Testowanie wdrożenia.  
1. Należy przetestować i potwierdzić, czy konfiguracja wdrożona przez Microsoft Managed Desktop działa zgodnie z oczekiwaniami.
1. W tym samym wniosku o pomoc techniczną odpowiedz za  pomocą karty Dyskusja, Microsoft Managed Desktop informacji i operacji IT po ukończeniu testowania.  
1. Microsoft Managed Desktop operacyjni IT wdroży konfigurację w innych grupach wdrożeniowych.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Procedura przygotuj się do Microsoft Managed Desktop

1. Przejrzyj [wymagania wstępne dotyczące Microsoft Managed Desktop](prerequisites.md).
1. Uruchom [narzędzia do oceny gotowości](readiness-assessment-tool.md).
1. Kup [Portal firmy](../get-started/company-portal.md).
1. Przejrzyj [wymagania wstępne dotyczące kont gości](guest-accounts.md).
1. Sprawdź [konfigurację sieci](network.md).
1. [Przygotowywanie certyfikatów i profilów sieci](certs-wifi-lan.md).
1. [Przygotowywanie dostępu użytkownika do danych](authentication.md).
1. [Przygotowywanie aplikacji](apps.md).
1. Przygotowywanie zamapowanych dysków (ten artykuł).
1. [Przygotowywanie zasobów do drukowania](printing.md).
1. Nazwy [urządzeń adresowych](address-device-names.md).
