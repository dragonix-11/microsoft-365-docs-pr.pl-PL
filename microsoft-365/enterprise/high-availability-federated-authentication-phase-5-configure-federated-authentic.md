---
title: Uwierzytelnianie federacyjne o wysokiej dostępności — faza 5. Konfigurowanie uwierzytelniania federacyjnego dla Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: 'Podsumowanie: Konfigurowanie usługi Azure AD Połączenie na potrzeby uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 w Microsoft Azure.'
ms.openlocfilehash: 9eff7f815ff5f7508da1f0e1230079a1b1802fed
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091264"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-microsoft-365"></a>Uwierzytelnianie federacyjne o wysokiej dostępności — faza 5: konfigurowanie uwierzytelniania federacyjnego dla Microsoft 365

W ostatniej fazie wdrażania uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 w usługach infrastruktury platformy Azure uzyskasz i zainstalujesz certyfikat wystawiony przez publiczny urząd certyfikacji, zweryfikujesz konfigurację, a następnie zainstalujesz i uruchomisz usługę Azure AD Połączenie na serwerze synchronizacji katalogów. Usługa Azure AD Połączenie konfiguruje subskrypcję Microsoft 365 oraz serwery Active Directory Federation Services (AD FS) i serwery proxy aplikacji internetowej na potrzeby uwierzytelniania federacyjnego.
  
Zobacz [Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) dla wszystkich faz.
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a>Pobieranie certyfikatu publicznego i kopiowanie go na serwer synchronizacji katalogów

Pobierz certyfikat cyfrowy z publicznego urzędu certyfikacji z następującymi właściwościami:
  
- Certyfikat X.509 odpowiedni do tworzenia połączeń SSL.
    
- Właściwość rozszerzona Alternatywna nazwa podmiotu (SAN) jest ustawiona na nazwę FQDN usługi federacyjnej (na przykład: fs.contoso.com).
    
- Certyfikat musi mieć klucz prywatny i być przechowywany w formacie PFX.
    
Ponadto komputery i urządzenia organizacji muszą ufać publicznemu urzędowi certyfikacji, który wystawia certyfikat cyfrowy. To zaufanie jest ustanawiane przez zainstalowanie certyfikatu głównego z publicznego urzędu certyfikacji w magazynie zaufanych głównych urzędów certyfikacji na komputerach i urządzeniach. Komputery z systemem Microsoft Windows zwykle mają zestaw tego typu certyfikatów zainstalowanych przez powszechnie używane urzędy certyfikacji. Jeśli certyfikat główny z publicznego urzędu certyfikacji nie jest jeszcze zainstalowany, należy wdrożyć go na komputerach i urządzeniach w organizacji.
  
Aby uzyskać więcej informacji na temat wymagań dotyczących certyfikatów dotyczących uwierzytelniania federacyjnego, zobacz [Wymagania wstępne dotyczące instalacji i konfiguracji federacji](/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).
  
Po otrzymaniu certyfikatu skopiuj go do folderu na dysku C: serwera synchronizacji katalogów. Na przykład nadaj plikowi nazwę SSL.pfx i zapisz go w folderze C:\\Certs na serwerze synchronizacji katalogów.
  
## <a name="verify-your-configuration"></a>Weryfikowanie konfiguracji

Teraz należy przystąpić do konfigurowania usługi Azure AD Połączenie i uwierzytelniania federacyjnego dla Microsoft 365. Aby upewnić się, że jesteś, oto lista kontrolna:
  
- Domena publiczna organizacji jest dodawana do subskrypcji Microsoft 365.
    
- Konta użytkowników Microsoft 365 organizacji są skonfigurowane pod nazwą domeny publicznej organizacji i mogą się pomyślnie zalogować.
    
- Określono nazwę domeny publicznej usługi federacyjnej FQDN.
    
- Publiczny rekord DNS Rekord FQDN usługi federacyjnej wskazuje publiczny adres IP internetowego modułu równoważenia obciążenia platformy Azure dla serwerów proxy aplikacji internetowej.
    
- Prywatny rekord DNS A dla nazwy FQDN usługi federacyjnej wskazuje prywatny adres IP wewnętrznego modułu równoważenia obciążenia platformy Azure dla serwerów usług AD FS.
    
- Certyfikat cyfrowy publiczny urząd certyfikacji isssued odpowiedni dla połączeń SSL z sieci SAN ustawionej na nazwę FQDN usługi federacyjnej to plik PFX przechowywany na serwerze synchronizacji katalogów.
    
- Certyfikat główny publicznego urzędu certyfikacji jest instalowany w magazynie zaufanych głównych urzędów certyfikacji na komputerach i urządzeniach.
    
Oto przykład dla organizacji firmy Contoso:
  
**Przykładowa konfiguracja infrastruktury uwierzytelniania federacyjnego o wysokiej dostępności na platformie Azure**

![Przykładowa konfiguracja wysokiej dostępności Microsoft 365 infrastruktury uwierzytelniania federacyjnego na platformie Azure.](../media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>Uruchamianie usługi Azure AD Połączenie w celu skonfigurowania uwierzytelniania federacyjnego

Narzędzie Połączenie usługi Azure AD konfiguruje serwery usług AD FS, serwery proxy aplikacji internetowej i Microsoft 365 na potrzeby uwierzytelniania federacyjnego, wykonując następujące kroki:
  
1. Utwórz połączenie pulpitu zdalnego z serwerem synchronizacji katalogów przy użyciu konta domeny z uprawnieniami administratora lokalnego.
    
2. Na pulpicie serwera synchronizacji katalogów otwórz program Internet Explorer i przejdź do [https://aka.ms/aadconnect](https://aka.ms/aadconnect)obszaru .
    
3. Na stronie **Microsoft Azure Active Directory Połączenie** kliknij pozycję **Pobierz**, a następnie kliknij pozycję **Uruchom**.
    
4. Na stronie **Witamy w usłudze Azure AD Połączenie** kliknij **pozycję Zgadzam się**, a następnie kliknij przycisk **Kontynuuj.**
    
5. Na stronie **Express Ustawienia** kliknij pozycję **Dostosuj**.
    
6. Na stronie **Instalowanie wymaganych składników** kliknij pozycję **Zainstaluj**.
    
7. Na stronie **Logowanie użytkownika** kliknij pozycję **Federacja z usługami AD FS**, a następnie kliknij przycisk **Dalej**.
    
8. Na stronie **Połączenie do usługi Azure AD** wpisz nazwę i hasło **administratora kontrolera domeny usługi Azure AD** lub konto **administratora globalnego** subskrypcji Microsoft 365, a następnie kliknij przycisk **Dalej**.
    
9. Na **Połączenie** katalogu upewnij się, że las usług lokalna usługa Active Directory Domain Services (AD DS) jest zaznaczony w **lesie**, wpisz nazwę i hasło konta administratora domeny, kliknij przycisk **Dodaj katalog**, a następnie kliknij przycisk **Dalej**.
    
10. Na stronie **konfiguracji logowania usługi Azure AD** kliknij przycisk **Dalej**.
    
11. Na stronie **Filtrowanie domeny i jednostki organizacyjnej** kliknij przycisk **Dalej**.
    
12. Na stronie **Unikatowe identyfikowanie użytkowników** kliknij przycisk **Dalej**.
    
13. Na stronie **Filtrowanie użytkowników i urządzeń** kliknij przycisk **Dalej**.
    
14. Na stronie **Funkcje opcjonalne** kliknij przycisk **Dalej**.
    
15. Na stronie **farmy usług AD FS** kliknij pozycję **Konfiguruj nową farmę usług AD FS**.
    
16. Kliknij przycisk **Przeglądaj** i określ lokalizację i nazwę certyfikatu SSL z publicznego urzędu certyfikacji.
    
17. Po wyświetleniu monitu wpisz hasło certyfikatu, a następnie kliknij przycisk **OK**.
    
18. Sprawdź, czy **nazwa podmiotu** i **nazwa usługi federacyjnej** są ustawione na nazwę FQDN usługi federacyjnej, a następnie kliknij przycisk **Dalej**.
    
19. Na stronie **Serwery usług AD FS** wpisz nazwę pierwszego serwera usług AD FS (tabela M — element 4 — kolumna nazwa maszyny wirtualnej), a następnie kliknij przycisk **Dodaj**.
    
20. Wpisz nazwę drugiego serwera usług AD FS (tabela M — element 5 — kolumna nazwa maszyny wirtualnej), kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Dalej**.
    
21. Na stronie **Serwery serwer proxy aplikacji sieci Web** wpisz nazwę pierwszego serwera proxy aplikacji internetowej (tabela M — element 6 — kolumna nazwa maszyny wirtualnej), a następnie kliknij przycisk **Dodaj**.
    
22. Wpisz nazwę drugiego serwera proxy aplikacji internetowej (tabela M — element 7 — kolumna nazwa maszyny wirtualnej), kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Dalej**.
    
23. Na stronie **Poświadczenia administratora domeny** wpisz nazwę użytkownika i hasło konta administratora domeny, a następnie kliknij przycisk **Dalej**.
    
24. Na stronie **Konto usługi AD FS** wpisz nazwę użytkownika i hasło konta administratora przedsiębiorstwa, a następnie kliknij przycisk **Dalej**.
    
25. Na stronie **Domena usługi Azure AD** w obszarze **Domena** wybierz nazwę domeny DNS organizacji, a następnie kliknij przycisk **Dalej**.
    
26. Na stronie **Gotowe do skonfigurowania** kliknij pozycję **Zainstaluj**.
    
27. Na stronie **Instalacja ukończona** kliknij pozycję **Sprawdź**. Powinny zostać wyświetlone dwa komunikaty wskazujące, że konfiguracja intranetu i Internetu została pomyślnie zweryfikowana.
    
  - Komunikat intranetowy powinien zawierać listę prywatnego adresu IP wewnętrznego modułu równoważenia obciążenia platformy Azure dla serwerów usług AD FS.
    
  - Komunikat internetowy powinien zawierać listę publicznego adresu IP modułu równoważenia obciążenia dostępnego z Internetu na platformie Azure dla serwerów proxy aplikacji internetowej.
    
28. Na stronie **Instalacja ukończona** kliknij pozycję **Zakończ**.
    
Oto ostateczna konfiguracja z nazwami zastępczymi serwerów.
  
**Faza 5. Ostateczna konfiguracja infrastruktury uwierzytelniania federacyjnego o wysokiej dostępności na platformie Azure**

![Ostateczna konfiguracja wysokiej dostępności Microsoft 365 infrastruktury uwierzytelniania federacyjnego na platformie Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Infrastruktura uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure została ukończona.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federacyjnego o wysokiej dostępności dla Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla środowiska deweloperskiego/testowego Microsoft 365](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Centrum rozwiązań i architektury platformy Microsoft 365](../solutions/index.yml)

[Tożsamość federacyjna dla Microsoft 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)
