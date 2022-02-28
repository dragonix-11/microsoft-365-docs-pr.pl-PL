---
title: Wdrażanie uwierzytelniania federeracyjnie o wysokiej dostępności Microsoft 365 na platformie Azure
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'Podsumowanie: Skonfiguruj uwierzytelnianie federowane o wysokiej dostępności dla swojej Microsoft 365 subskrypcji Microsoft Azure.'
ms.openlocfilehash: 70d597663a1920706dbab164dda05b7142f7fd04
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983952"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>Wdrażanie uwierzytelniania federeracyjnie o wysokiej dostępności Microsoft 365 na platformie Azure

Ten artykuł zawiera linki do instrukcji krok po kroku dotyczących wdrażania uwierzytelniania federacyjne o wysokiej dostępności dla usługi Microsoft Microsoft 365 w usługach infrastruktury platformy Azure z tymi maszynami wirtualnymi:
  
- Dwa serwery proxy aplikacji sieci Web
    
- Dwa serwery usług feder serverowych Active Directory (AD FS)
    
- Dwa repliki kontrolerów domeny
    
- Jeden serwer synchronizacji katalogów z uruchomionymi usługami Azure AD Połączenie
    
Oto konfiguracja z nazwami zastępczymi dla każdego serwera.
  
**Uwierzytelnianie federowane o wysokiej dostępności dla infrastruktury Microsoft 365 na platformie Azure**

![Ostateczna konfiguracja wysokiej dostępności usługi Microsoft 365 uwierzytelniania federacyjne na platformie Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Wszystkie maszyny wirtualne znajdują się w jednej lokalnej sieci wirtualnej platformy Azure (VNet). 
  
> [!NOTE]
> Uwierzytelnianie federowane pojedynczych użytkowników nie polega na żadnym zasobie lokalnym. Jeśli jednak połączenie między siedzibą firmy stanie się niedostępne, kontrolery domen w sieci VNet nie będą otrzymywać aktualizacji kont użytkowników i grup w lokalnym programie Usługi domenowe w usłudze Active Directory (AD DS). Aby tego nie zrobić, możesz skonfigurować wysoką dostępność dla połączenia między siedzibą firmy. Aby uzyskać więcej informacji, zobacz [Wysoce dostępna łączność między siedzibą firmy i między siecią VNet.](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Każda para maszyn wirtualnych dla określonej roli znajduje się w własnym zestawie podsieci i dostępności.
  
> [!NOTE]
> Ponieważ ta sieć VNet jest połączona z siecią lokalną, ta konfiguracja nie obejmuje skrzynki nadawczej ani monitorowania maszyn wirtualnych w podsieci zarządzania. Aby uzyskać więcej informacji, zobacz [Uruchamianie Windows maszyn wirtualnych dla architektury N-warstwy](/azure/guidance/guidance-compute-n-tier-vm). 
  
Wynikiem tej konfiguracji jest to, że u wszystkich użytkowników usługi Microsoft 365 będzie używane uwierzytelnianie federacyjne, w którym będą oni mogą logować się za pomocą swoich poświadczeń programu AD DS, a nie kont Microsoft 365. W infrastrukturze uwierzytelniania feder sądowego jest używany nadmiarowy zestaw serwerów, które są łatwiej wdrażane w usługach infrastruktury platformy Azure, a nie w twojej lokalnej sieci brzegowej.
  
## <a name="bill-of-materials"></a>Rachunki za materiały

Ta konfiguracja podstawowa wymaga następującego zestawu usług i składników platformy Azure:
  
- Siedem maszyn wirtualnych
    
- Jedna międzysieciowa sieć wirtualna z czterema podsieciami
    
- Cztery grupy zasobów
    
- Trzy zestawy dostępności
    
- Jedna subskrypcja platformy Azure
    
Oto maszyny wirtualne i ich domyślne rozmiary w tej konfiguracji.
  
|**Element**|**Opis maszyny wirtualnej**|**Galeria platformy Azure**|**Rozmiar domyślny**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Pierwszy kontroler domeny  <br/> |Windows Server 2016 Centrum danych  <br/> |D2  <br/> |
|2.  <br/> |Drugi kontroler domeny  <br/> |Windows Server 2016 Centrum danych  <br/> |D2  <br/> |
|3.  <br/> |Serwer usługi Azure AD Połączenie usługi  <br/> |Windows Server 2016 Centrum danych  <br/> |D2  <br/> |
|4.  <br/> |Pierwszy serwer usług AD FS  <br/> |Windows Server 2016 Centrum danych  <br/> |D2  <br/> |
|5.  <br/> |Drugi serwer usług AD FS  <br/> |Windows Server 2016 Centrum danych  <br/> |D2  <br/> |
|6.  <br/> |Pierwszy serwer proxy aplikacji sieci Web  <br/> |Windows Server 2016 Centrum danych  <br/> |D2  <br/> |
|7.  <br/> |Drugi serwer proxy aplikacji sieci Web  <br/> |Windows Server 2016 Centrum danych  <br/> |D2  <br/> |
   
Aby obliczyć szacowane koszty dla tej konfiguracji, zobacz kalkulator [cen platformy Azure](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>Fazy wdrażania

To obciążenie można wdrożyć w następujących fazach:
  
- [Etap 1. Konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Tworzenie grup zasobów, kont magazynu, zestawów dostępności i między siedzibą sieci wirtualnej.
    
- [Etap 2. Konfigurowanie kontrolerów domeny](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Utwórz i skonfiguruj repliki AD DS domeny i serwera synchronizacji katalogów.
    
- [Etap 3. Konfigurowanie serwerów usług AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Utwórz i skonfiguruj dwa serwery usług AD FS.
    
- [Etap 4. Konfigurowanie serwerów proxy aplikacji sieci Web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Utwórz i skonfiguruj dwa serwery proxy aplikacji sieci Web.
    
- [Etap 5. Konfigurowanie uwierzytelniania feder służącego do Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Skonfiguruj uwierzytelnianie federowane na Microsoft 365 subskrypcji usługi.
    
W tych artykułach za pomocą przewodnika z preskrybowanymi etapami dla wstępnie zdefiniowanej architektury utworzysz funkcjonalne uwierzytelnianie federacyjne o wysokiej dostępności dla usług Microsoft 365 infrastruktury platformy Azure. Należy pamiętać o następujących kwestiach:
  
- Jeśli jesteś doświadczonym implementatorem usług AD FS, zachęcamy do dostosowywania instrukcji w fazach 3 i 4 oraz tworzenia zestawu serwerów, który najlepiej odpowiada Twoim potrzebom.
    
- Jeśli masz już istniejące wdrożenie hybrydowe platformy Azure w chmurze z istniejącą między siedzibą sieci wirtualnej, zachęcamy do dostosowywania się lub pomijania instrukcji w fazach 1 i 2 oraz umieszczać serwery proxy usług AD FS i aplikacji sieci Web w odpowiednich podsieciach.
    
Aby utworzyć środowisko deweloper/test lub dowód koncepcji tej konfiguracji, zobacz Tożsamość federacyjna dla Twojego Microsoft 365 [deweloper/test.](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
## <a name="next-step"></a>Następny krok

Rozpocznij konfigurację tego obciążenia pracą [od fazy 1. Konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
