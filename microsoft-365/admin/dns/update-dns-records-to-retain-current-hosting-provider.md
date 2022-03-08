---
title: Aktualizowanie rekordów DNS w celu zachowania witryny sieci Web u obecnego dostawcy hostingu
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c4cf347-b897-45c1-a71f-210bdc8f1061
description: Dowiedz się, jak rozsyłać ruch do istniejącej publicznej witryny internetowej hostowanej poza firmą Microsoft, jeśli masz ustawioną przez firmę Microsoft zarządzanie rekordami DNS dla Twojej domeny niestandardowej.
ms.openlocfilehash: 9bb12d4f73e8d95717ddd90492fb9cb97c73eec9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314824"
---
# <a name="update-dns-records-to-keep-your-website-with-your-current-hosting-provider"></a>Aktualizowanie rekordów DNS w celu zachowania witryny sieci Web u obecnego dostawcy hostingu

 **Jeśli zarządzasz rekordami firmy Microsoft** swojej domeny u dostawcy hostingu DNS, nie musisz martwić się czynnościami w tym temacie. Witryna sieci Web pozostaje tam, gdzie jest, a użytkownicy nadal mogą ją odwiedzać. 
  
 **Jeśli firma Microsoft zarządza twoimi** rekordami DNS, aby po dodaniu domeny do firmy Microsoft kierowanego ruchu do istniejącej publicznej witryny internetowej hostowanej poza firmą Microsoft wykonaj następujące czynności: 
  
## <a name="update-dns-records-in-the-microsoft-365-admin-center"></a>Aktualizowanie rekordów DNS w centrum administracyjne platformy Microsoft 365
1. W Centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domeny</a>.

1. Na stronie **Domains (** Domeny) wybierz domenę, a następnie wybierz pozycję **DNS Records (Rekordy DNS**).

1. Wybierz **pozycję + Add record (Dodaj rekord** ) i wprowadź następujące informacje: 
    
   - **Wpisz enter**: **A (Adres)**
    
   - W polu **Nazwa hosta lub alias** wpisz następujący tekst: **@**
    
   - W polu **Adres IP** wpisz statyczny adres IP, pod którym witryna sieci Web jest obecnie hostowana (na przykład 172.16.140.1). 
    
   Adres IP musi być  *statyczny*  , a nie  *dynamiczny*  . Skontaktuj się z dostawcą hostingu i upewnij się, że możesz uzyskać statyczny adres IP swojej publicznej witryny sieci Web. 
    
1. Wybierz pozycję **Zapisz**. 
    
Możesz też utworzyć rekord CNAME, aby ułatwić klientom odnalezienie Twojej witryny sieci Web.
  
1. Wybierz **pozycję + Add record (Dodaj rekord** ) i wprowadź następujące informacje: 
    
   - Dla **typu** enter: **CNAME (Alias)**
    
   - W polu **Nazwa hosta lub alias** wpisz następujący tekst: **www**.
    
   - W polu **Wskazywany adres** wpisz w pełni kwalifikowaną nazwę domeny (FQDN) swojej witryny sieci Web (na przykład contoso.com). 
    
2. Wybierz pozycję **Zapisz**. 
    
Na koniec wykonaj następujące czynności:
  
[Zaktualizuj rekordy serwera nazw domeny, aby](../setup/add-domain.md) wskazały firmę Microsoft. 
  
Po zaktualizowaniu rekordów serwera nazw tak, aby wskazują firmę Microsoft, domena jest już w stanie skonfigurować. Wiadomości e-mail będą kierowane do firmy Microsoft, a ruch na adres witryny sieci Web będzie nadal przenoszony do bieżącego hosta witryny sieci Web.
