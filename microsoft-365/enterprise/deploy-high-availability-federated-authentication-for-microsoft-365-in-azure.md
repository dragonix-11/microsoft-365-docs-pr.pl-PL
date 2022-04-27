---
title: Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: Skonfiguruj uwierzytelnianie federacyjne o wysokiej dostępności dla subskrypcji Microsoft 365 w Microsoft Azure.'
ms.openlocfilehash: 64fc02e6ecaa400da6d6130cb9ae630279102fcc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093421"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure

Ten artykuł zawiera linki do instrukcji krok po kroku dotyczących wdrażania uwierzytelniania federacyjnego o wysokiej dostępności dla usługi Microsoft Microsoft 365 w usługach infrastruktury platformy Azure z następującymi maszynami wirtualnymi:
  
- Dwa serwery proxy aplikacji internetowej
    
- Dwa serwery Active Directory Federation Services (AD FS)
    
- Dwa repliki kontrolerów domeny
    
- Jeden serwer synchronizacji katalogów z uruchomioną usługą Azure AD Połączenie
    
Oto konfiguracja z nazwami zastępczymi dla każdego serwera.
  
**Uwierzytelnianie federacyjne o wysokiej dostępności dla infrastruktury Microsoft 365 na platformie Azure**

![Ostateczna konfiguracja wysokiej dostępności Microsoft 365 infrastruktury uwierzytelniania federacyjnego na platformie Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Wszystkie maszyny wirtualne znajdują się w jednej sieci wirtualnej platformy Azure( cross-premises). 
  
> [!NOTE]
> Uwierzytelnianie federacyjne poszczególnych użytkowników nie opiera się na żadnych zasobach lokalnych. Jeśli jednak połączenie między lokalami stanie się niedostępne, kontrolery domeny w sieci wirtualnej nie otrzymają aktualizacji kont użytkowników i grup wprowadzonych w usługach lokalna usługa Active Directory Domain Services (AD DS). Aby upewnić się, że tak się nie stanie, można skonfigurować wysoką dostępność dla połączenia między środowiskami lokalnymi. Aby uzyskać więcej informacji, zobacz [Highly Available Cross-Premises and VNet-to-VNet Connectivity (Łączność między sieciami wirtualnymi i między sieciami wirtualnymi](/azure/vpn-gateway/vpn-gateway-highlyavailable))
  
Każda para maszyn wirtualnych dla określonej roli znajduje się we własnej podsieci i zestawie dostępności.
  
> [!NOTE]
> Ponieważ ta sieć wirtualna jest połączona z siecią lokalną, ta konfiguracja nie obejmuje przesiadki ani monitorowania maszyn wirtualnych w podsieci zarządzania. Aby uzyskać więcej informacji, zobacz [Running Windows VMs for an N-tier architecture (Uruchamianie maszyn wirtualnych Windows dla architektury N-warstwowej](/azure/guidance/guidance-compute-n-tier-vm)). 
  
Wynikiem tej konfiguracji jest to, że będziesz mieć uwierzytelnianie federacyjne dla wszystkich użytkowników Microsoft 365, w których mogą oni używać swoich poświadczeń usług AD DS do logowania, a nie konta Microsoft 365. Infrastruktura uwierzytelniania federacyjnego korzysta z nadmiarowego zestawu serwerów, które są łatwiej wdrażane w usługach infrastruktury platformy Azure, a nie w lokalnej sieci brzegowej.
  
## <a name="bill-of-materials"></a>Rachunek za materiały

Ta konfiguracja punktu odniesienia wymaga następującego zestawu usług i składników platformy Azure:
  
- Siedem maszyn wirtualnych
    
- Jedna lokalna sieć wirtualna z czterema podsieciami
    
- Cztery grupy zasobów
    
- Trzy zestawy dostępności
    
- Jedna subskrypcja platformy Azure
    
Poniżej przedstawiono maszyny wirtualne i ich domyślne rozmiary dla tej konfiguracji.
  
|**Element**|**Opis maszyny wirtualnej**|**Obraz galerii platformy Azure**|**Rozmiar domyślny**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Pierwszy kontroler domeny  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |Drugi kontroler domeny  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Serwer Połączenie usługi Azure AD  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |Pierwszy serwer usług AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |Drugi serwer usług AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |Pierwszy serwer proxy aplikacji internetowej  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |Drugi serwer proxy aplikacji internetowej  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
Aby obliczyć szacowane koszty tej konfiguracji, zobacz [kalkulator cen platformy Azure](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>Fazy wdrażania

To obciążenie jest wdrażane w następujących fazach:
  
- [Faza 1. Konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Tworzenie grup zasobów, kont magazynu, zestawów dostępności i sieci wirtualnej między środowiskami.
    
- [Faza 2. Konfigurowanie kontrolerów domeny](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Utwórz i skonfiguruj repliki kontrolerów domeny usług AD DS i serwer synchronizacji katalogów.
    
- [Faza 3. Konfigurowanie serwerów usług AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Utwórz i skonfiguruj dwa serwery usług AD FS.
    
- [Faza 4. Konfigurowanie serwerów proxy aplikacji internetowej](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Utwórz i skonfiguruj dwa serwery proxy aplikacji internetowej.
    
- [Faza 5. Konfigurowanie uwierzytelniania federacyjnego dla Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Skonfiguruj uwierzytelnianie federacyjne dla subskrypcji Microsoft 365.
    
Te artykuły zawierają opisowy przewodnik fazy po fazie dla wstępnie zdefiniowanej architektury w celu utworzenia funkcjonalnego uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 w usługach infrastruktury platformy Azure. Należy pamiętać o następujących kwestiach:
  
- Jeśli jesteś doświadczonym implementatorem usług AD FS, możesz dostosować instrukcje w fazach 3 i 4 i skompilować zestaw serwerów, które najlepiej odpowiadają Twoim potrzebom.
    
- Jeśli masz już istniejące wdrożenie chmury hybrydowej platformy Azure z istniejącą siecią wirtualną między środowiskami lokalnymi, możesz dostosować lub pominąć instrukcje w fazach 1 i 2 oraz umieścić usługi AD FS i serwery proxy aplikacji internetowej w odpowiednich podsieciach.
    
Aby utworzyć środowisko deweloperskie/testowe lub weryfikację tej konfiguracji, zobacz [Tożsamość federacyjna dla środowiska deweloperskiego/testowego Microsoft 365](federated-identity-for-your-microsoft-365-dev-test-environment.md).
  
## <a name="next-step"></a>Następny krok

Rozpocznij konfigurację tego obciążenia od [fazy 1: konfigurowanie platformy Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
