---
title: Wdrażanie Microsoft 365 katalogów w programie Microsoft Azure
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: Dowiedz się, jak wdrożyć usługę Azure AD Połączenie na maszyny wirtualnej na platformie Azure w celu synchronizowania kont między katalogiem lokalnym a dzierżawą usługi Azure AD.
ms.openlocfilehash: 6535b46fb360cf326d8daf07662cb7fa366ae6c2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984453"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>Wdrażanie Microsoft 365 katalogów w programie Microsoft Azure

Azure Active Directory (Azure AD) Połączenie (wcześniej znany jako narzędzie do synchronizacji katalogów, narzędzie do synchronizacji katalogów lub narzędzie DirSync.exe) to aplikacja instalowana na serwerze przyłączony do domeny w celu zsynchronizowania lokalnych użytkowników usługi Usługi domenowe w usłudze Active Directory (AD DS) z dzierżawą usługi Azure AD subskrypcji usługi Microsoft 365. Microsoft 365 usługi katalogowej używa usługi Azure AD. Twoja Microsoft 365 obejmuje dzierżawę usługi Azure AD. Ta dzierżawa może być również używana do zarządzania tożsamościami Twojej organizacji za pomocą innych obciążeń chmurowych, w tym innych aplikacji i aplikacji SaaS na platformie Azure.

Usługę Azure AD Połączenie możesz zainstalować na serwerze lokalnym, ale możesz również zainstalować ją na maszyny wirtualnej na platformie Azure z tych powodów:
  
- Możesz szybciej zapewniać i konfigurować serwery w chmurze, co przyspieszy udostępnianie usług użytkownikom.
- Platforma Azure zapewnia lepszą dostępność witryn przy mniejszym nałocie pracy.
- Możesz zmniejszyć liczbę serwerów lokalnych w organizacji.

To rozwiązanie wymaga łączności między siecią lokalną a siecią wirtualną platformy Azure. Aby uzyskać więcej informacji, [Połączenie połączenie z](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) siecią lokalną Microsoft Azure wirtualną. 
  
> [!NOTE]
> W tym artykule opisano synchronizację pojedynczej domeny w jednym lesie. Usługa Azure AD Połączenie synchronizuje wszystkie domeny AD DS w lesie usługi Active Directory z Microsoft 365. Jeśli masz wiele lasów usługi Active Directory do zsynchronizowania z Microsoft 365, zobacz Scenariusz synchronizacji katalogów z jednym [Sign-On](/azure/active-directory/hybrid/whatis-hybrid-identity) lasów. 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>Omówienie wdrażania synchronizacji Microsoft 365 katalogów na platformie Azure

Poniższy diagram przedstawia usługę Azure AD Połączenie na maszyny wirtualnej na platformie Azure (serwer synchronizacji katalogów), która synchronizuje lokalną AD DS z subskrypcją usługi Microsoft 365.
  
![Narzędzie azure AD Połączenie na maszyny wirtualnej na platformie Azure do synchronizowania kont lokalnych z dzierżawą usługi Azure AD subskrypcji usługi Microsoft 365 z przepływem ruchu.](../media/CP-DirSyncOverview.png)
  
Na diagramie istnieją dwie sieci połączone za pomocą połączenia VPN między witrynami lub przez usługę ExpressRoute. Istnieje sieć lokalna, w której znajdują się kontrolery domeny AD DS, oraz istnieje sieć wirtualna platformy Azure z serwerem synchronizacji katalogów, która jest maszyną wirtualną z uruchomionymi kontrolerami usługi [Azure AD Połączenie](https://www.microsoft.com/download/details.aspx?id=47594). Istnieją dwa główne przepływy ruchu pochodzące z serwera synchronizacji katalogów:
  
-  Usługa Azure AD Połączenie wysyła zapytanie dotyczące kontrolera domeny w sieci lokalnej w celu zmiany kont i haseł.
-  Usługa Azure AD Połączenie wysyła zmiany do kont i haseł do wystąpienia subskrypcji usługi Azure AD Microsoft 365 konta. Ponieważ serwer synchronizacji katalogów znajduje się w rozszerzonej części sieci lokalnej, zmiany te są wysyłane za pośrednictwem serwera proxy sieci lokalnej.
    
> [!NOTE]
> To rozwiązanie opisuje synchronizację pojedynczej domeny usługi Active Directory w jednym lesie usługi Active Directory. Usługa Azure AD Połączenie synchronizuje wszystkie domeny usługi Active Directory w lesie usługi Active Directory z Microsoft 365. Jeśli masz wiele lasów usługi Active Directory do zsynchronizowania z Microsoft 365, zobacz Scenariusz synchronizacji katalogów z jednym [Sign-On](/azure/active-directory/hybrid/whatis-hybrid-identity) lasów. 
  
Wdrożenie tego rozwiązania jest opisane w dwóch głównych krokach:
  
1. Utwórz sieć wirtualną platformy Azure i nawiąń połączenie vpn między witrynami z siecią lokalną. Aby uzyskać więcej informacji, [Połączenie połączenie z](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) siecią lokalną Microsoft Azure wirtualną.
    
2. Zainstaluj [usługę Azure AD Połączenie](https://www.microsoft.com/download/details.aspx?id=47594) na maszyny wirtualnej przyłączonej do domeny na platformie Azure, a następnie zsynchronizuj lokalną AD DS, aby Microsoft 365. Obejmuje to:
    
    Tworzenie maszyny wirtualnej platformy Azure do uruchamiania usługi Azure AD Połączenie.
    
    Instalowanie i konfigurowanie usługi [Azure AD Połączenie](https://www.microsoft.com/download/details.aspx?id=47594).
    
    Konfigurowanie usługi Azure AD Połączenie wymaga poświadczeń (nazwy użytkownika i hasła) konta administratora usługi Azure AD i konta administratora AD DS przedsiębiorstwa. Usługa Azure AD Połączenie działa natychmiast i na bieżąco w celu zsynchronizowania lokalnego lasu AD DS do Microsoft 365.
    
Przed wdrożeniem tego rozwiązania w środowisku produkcyjnym można użyć instrukcji podanych [](simulated-ent-base-configuration-microsoft-365-enterprise.md) w symulowanej konfiguracji podstawowej przedsiębiorstwa w celu skonfigurowania tej konfiguracji jako dowodu koncepcji, dla pokazów lub na eksperymentach.
  
> [!IMPORTANT]
> Po zakończeniu konfiguracji Połączenie usługi Azure AD nie są AD DS poświadczenia administratora przedsiębiorstwa. 
  
> [!NOTE]
> To rozwiązanie opisano synchronizowanie pojedynczego AD DS z Microsoft 365. Topologia omówiona w tym artykule to tylko jeden sposób wdrożenia tego rozwiązania. Topologia organizacji może się różnić w zależności od Twoich unikatowych wymagań sieciowych i kwestii zabezpieczeń. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>Planowanie hostingu serwera synchronizacji katalogów dla usługi Microsoft 365 Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem przejrzyj następujące wymagania wstępne dotyczące tego rozwiązania:
  
- Zapoznaj się z powiązaną zawartością planowania w [tesłudze Planowanie sieci wirtualnej platformy Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).
    
- Upewnij się, że są spełnione wszystkie [wymagania wstępne](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) dotyczące konfigurowania sieci wirtualnej platformy Azure.
    
- Posiadaj Microsoft 365, która zawiera funkcję integracji z usługą Active Directory. Aby uzyskać informacje Microsoft 365 subskrypcji, przejdź do strony Microsoft 365 [subskrypcji](https://products.office.com/compare-all-microsoft-office-products?tab=2).
    
- Inicjowanie obsługi jednej maszyny wirtualnej platformy Azure z Połączenie Azure AD w celu synchronizowania lokalnego lasu AD DS z Microsoft 365.
    
    Musisz mieć poświadczenia (nazwy i hasła) dla konta administratora AD DS przedsiębiorstwa i konta administratora usługi Azure AD.
    
### <a name="solution-architecture-design-assumptions"></a>Założenia projektowe architektury rozwiązań

Na poniższej liście opisano opcje projektu dla tego rozwiązania.
  
- To rozwiązanie korzysta z pojedynczej sieci wirtualnej platformy Azure z połączeniem VPN między witrynami. Sieć wirtualna Azure hostuje pojedynczą podsieci, która ma jeden serwer: serwer synchronizacji katalogów z uruchomionym usługą Azure AD Połączenie. 
    
- W sieci lokalnej istnieje kontroler domeny i serwery DNS.
    
- Usługa Azure AD Połączenie przeprowadza synchronizację skrótów haseł zamiast logowania pojedynczego. Nie musisz wdrażać infrastruktury usług federalnych Active Directory (AD FS). Aby dowiedzieć się więcej o synchronizacji skrótów haseł i opcjach logowania pojedynczego, zobacz Wybieranie odpowiedniej metody uwierzytelniania dla Azure Active Directory [hybrydowego rozwiązania tożsamości](/azure/active-directory/hybrid/choose-ad-authn).
    
Istnieją dodatkowe opcje projektu, które można rozważyć podczas wdrażania tego rozwiązania w środowisku. Są to między innymi następujące elementy:
  
- Jeśli w istniejącej sieci wirtualnej Azure istnieją serwery DNS, określ, czy chcesz, aby serwer synchronizacji katalogów ich używać do rozpoznawania nazw zamiast serwerów DNS w sieci lokalnej.
    
- Jeśli w istniejącej sieci wirtualnej Azure istnieją kontrolery domeny, określ, czy skonfigurowanie witryn i usług Active Directory może być lepszym rozwiązaniem. Serwer synchronizacji katalogów może zwracać się do kontrolerów domen w wirtualnej sieci Azure w celu zmiany kont i haseł zamiast kontrolerów domen w sieci lokalnej.
    
## <a name="deployment-roadmap"></a>Plan wdrażania

Wdrażanie usługi Azure AD Połączenie na maszynie wirtualnej na platformie Azure składa się z trzech etapów:
  
- Etap 1. Tworzenie i konfigurowanie sieci wirtualnej platformy Azure
    
- Etap 2. Tworzenie i konfigurowanie maszyny wirtualnej platformy Azure
    
- Etap 3. Instalowanie i konfigurowanie usługi Azure AD Połączenie
    
Po wdrożeniu musisz również przypisać lokalizacje i licencje dla nowych kont użytkowników w programie Microsoft 365.


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Etap 1. Tworzenie i konfigurowanie sieci wirtualnej platformy Azure

Aby utworzyć i skonfigurować sieć wirtualną platformy Azure, ukończ etap [1.](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) Przygotowanie sieci lokalnej i etap [2.](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) Tworzenie między siedzibą sieci wirtualnej na platformie Azure w planie wdrażania usługi [Połączenie](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) sieci lokalnej do sieci Microsoft Azure wirtualnej.
  
Jest to wynikowa konfiguracja.
  
![Etap 1. serwera synchronizacji katalogów dla usług Microsoft 365 na platformie Azure.](../media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Na tej ilustracji przedstawiono sieć lokalną połączną z siecią wirtualną platformy Azure za pośrednictwem połączenia VPN między witrynami lub usługi ExpressRoute.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Etap 2. Tworzenie i konfigurowanie maszyny wirtualnej platformy Azure

Utwórz maszynę wirtualną na platformie Azure, korzystając z instrukcji [Utwórz pierwszą Windows wirtualną w portalu Azure Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Użyj następujących ustawień:
  
- W **okienku Podstawy** wybierz tę samą subskrypcję, lokalizację i grupę zasobów, co twoja sieć wirtualna. Zanotuj nazwę użytkownika i hasło w bezpiecznym miejscu. Będą one potrzebne później do nawiązania połączenia z maszyną wirtualną.
    
- W **okienku Wybierz rozmiar** wybierz rozmiar **standardowy A2** .
    
- W **okienku** Ustawienia **w sekcji Storage** wybierz pozycję **Standardowy** typ przestrzeni dyskowej. W sekcji **Network** (Sieć) wybierz nazwę swojej sieci wirtualnej i podsieci hostowania serwera synchronizacji katalogów (nie nazwy GatewaySubnet). Pozostaw wszystkie inne ustawienia na ich wartości domyślne.
    
Sprawdź, czy serwer synchronizacji katalogów używa prawidłowo systemu DNS, sprawdzając wewnętrzny system DNS, aby upewnić się, że do maszyny wirtualnej został dodany rekord adresu (A) z jego adresem IP. 
  
Skorzystaj z instrukcji Połączenie [się z maszyną wirtualną](/azure/virtual-machines/windows/connect-logon) i zaloguj się, aby połączyć się z serwerem synchronizacji katalogów za pomocą połączenia pulpitu zdalnego. Po zalogowaniu się dołącz maszynę wirtualną do domeny AD DS domeny.
  
Aby usługa Azure AD Połączenie uzyskać dostęp do zasobów internetowych, musisz skonfigurować serwer synchronizacji katalogów do używania lokalnego serwera proxy sieci. W celu wykonania wszystkich dodatkowych czynności konfiguracyjnych należy skontaktować się z administratorem sieci.
  
Jest to wynikowa konfiguracja.
  
![Etap 2 serwera synchronizacji katalogów dla usług Microsoft 365 na platformie Azure.](../media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Na tej ilustracji przedstawiono maszynę wirtualną serwera synchronizacji katalogów w między siedzibą sieci wirtualnej platformy Azure.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Etap 3. Instalowanie i konfigurowanie usługi Azure AD Połączenie

Wykonaj następujące czynności:
  
1. Połączenie z serwerem synchronizacji katalogów przy użyciu połączenia pulpitu zdalnego z kontem AD DS domeny z uprawnieniami administratora lokalnego. Zobacz [Połączenie do maszyny wirtualnej i zaloguj się](/azure/virtual-machines/windows/connect-logon).
    
2. Na serwerze synchronizacji katalogów otwórz artykuł Konfigurowanie [](set-up-directory-synchronization.md) synchronizacji katalogów Microsoft 365 i postępuj zgodnie z instrukcjami synchronizacji katalogów z synchronizacją skrótów haseł.
    
> [!CAUTION]
> Instalator tworzy konto **AAD_xxxxxxxxxxxx** organizacji Użytkownicy lokalni. Przenoszenie lub usuwanie tego konta nie powiedzie się. Synchronizacja nie powiedzie się.
  
Jest to wynikowa konfiguracja.
  
![Etap 3. serwera synchronizacji katalogów dla Microsoft 365 na platformie Azure.](../media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Na tej ilustracji przedstawiono serwer synchronizacji katalogów z usługą Azure AD Połączenie w między siedzibą sieci wirtualnej platformy Azure.
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>Przypisywanie lokalizacji i licencji użytkownikom w Microsoft 365

Usługa Azure AD Połączenie dodaje konta do Twojej subskrypcji usługi Microsoft 365 z lokalnego programu AD DS, ale aby użytkownicy logowali się do usługi Microsoft 365 i korzystali z jej usług, konta muszą być skonfigurowane z lokalizacją i licencjami. Aby dodać lokalizację i aktywować licencje dla odpowiednich kont użytkowników, użyj poniższych instrukcji:
  
1. Zaloguj się do centrum [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com), a następnie kliknij pozycję **Administrator**.
    
2. W lewym okienku nawigacji kliknij pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UżytkownicyAktywowanie**</a> >  użytkowników.
3. Na liście kont użytkowników zaznacz pole wyboru obok użytkownika, którego chcesz aktywować.
    
4. Na stronie użytkownika kliknij pozycję **Edytuj** w **przypadku licencji produktu**.
    
5. Na **stronie Licencje na produkty** wybierz dla użytkownika lokalizację **Lokalizacji, a** następnie włącz odpowiednie licencje dla użytkownika.
    
6. Po zakończeniu kliknij przycisk **Zapisz**, a następnie kliknij przycisk **Zamknij** dwa razy.
    
7. Wróć do kroku 3 w przypadku dodatkowych użytkowników.
    
## <a name="see-also"></a>Zobacz też

[Microsoft 365 rozwiązania i architektury](../solutions/index.yml)
  
[Połączenie sieci lokalnej do sieci Microsoft Azure wirtualnej](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Pobierz aplikację Azure AD Połączenie](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Konfigurowanie synchronizacji katalogów dla Microsoft 365](set-up-directory-synchronization.md)
