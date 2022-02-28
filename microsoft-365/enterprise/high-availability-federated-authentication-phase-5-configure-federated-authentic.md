---
title: Wysoka dostępność uwierzytelniania federegonowego (etap 5) Konfigurowanie uwierzytelniania feder standardowego Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Podsumowanie: Skonfiguruj usługę Azure AD Połączenie na poziomie wysokiej dostępności uwierzytelniania federaryczne dla usługi Microsoft 365 w Microsoft Azure.'
ms.openlocfilehash: e5a11c1b94f9a0297ccfa0a18e1963fae9898f65
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977632"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-microsoft-365"></a>Wysoka dostępność uwierzytelniania federeracyjna Etap 5. Konfigurowanie uwierzytelniania feder standardowego na Microsoft 365

W tej końcowej fazie wdrażania uwierzytelniania federacyjne o wysokiej dostępności dla usługi Microsoft 365 w usługach infrastruktury platformy Azure można uzyskać i zainstalować certyfikat wydany przez publiczny urząd certyfikacji, zweryfikować konfigurację, a następnie zainstalować i uruchomić usługę Azure AD Połączenie na serwerze synchronizacji katalogów. Usługa Azure AD Połączenie konfiguruje subskrypcję usługi Microsoft 365 oraz federowane usługi Active Directory (AD FS) i serwery proxy aplikacji sieci Web na poziomie uwierzytelniania federenta internetowego.
  
Zobacz [Wdrażanie uwierzytelniania feder](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) służącego do wysokiej dostępności Microsoft 365 na platformie Azure, aby uzyskać informacje o wszystkich fazach.
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a>Uzyskiwanie certyfikatu publicznego i kopiowanie go na serwer synchronizacji katalogów

Uzyskaj certyfikat cyfrowy od publicznego urzędu certyfikacji o następujących właściwościach:
  
- Certyfikat X.509 odpowiedni do tworzenia połączeń SSL.
    
- Właściwość rozszerzona SAN (Subject Alternative Name) jest ustawiona na nazwę FQDN twojej usługi federrskiej (na przykład: fs.contoso.com).
    
- Certyfikat musi mieć klucz prywatny i być przechowywany w formacie PFX.
    
Ponadto komputery i urządzenia organizacji muszą ufać publicznemu urządowi certyfikacji, który wydaje certyfikat cyfrowy. To zaufanie jest ustanowione przez posiadanie certyfikatu głównego publicznego urzędu certyfikacji zainstalowanego w magazynie zaufanych głównych urzędów certyfikacji na komputerach i urządzeniach. Komputery z Windows Microsoft Windows mają zainstalowany zestaw tych typów certyfikatów zainstalowanych przez często używane urzędy certyfikacji. Jeśli certyfikat główny z publicznego urzędu certyfikacji nie został jeszcze zainstalowany, musisz wdrożyć go na komputerach i urządzeniach w organizacji.
  
Aby uzyskać więcej informacji na temat wymagań dotyczących certyfikatu dla uwierzytelniania federacyjne, zobacz [Wymagania wstępne dotyczące instalacji i konfiguracji federacyjnych](/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).
  
Po otrzymaniu certyfikatu skopiuj go do folderu na dysku C: serwera synchronizacji katalogów. Na przykład nazwij plik SSL.pfx i przechowuj go w folderze C:\\Certs na serwerze synchronizacji katalogów.
  
## <a name="verify-your-configuration"></a>Weryfikowanie konfiguracji

Teraz wszystko powinno być gotowe do skonfigurowania usługi Azure AD Połączenie uwierzytelniania feder służącego do Microsoft 365. Oto lista kontrolna, która pozwala upewnić się, że tak jest:
  
- Domena publiczna twojej organizacji zostanie dodana do Microsoft 365 subskrypcji usługi.
    
- Konta użytkowników Microsoft 365 organizacji są skonfigurowane jako nazwa domeny publicznej i można się zalogować.
    
- Nazwa FQDN usługi federowej jest określona na podstawie nazwy domeny publicznej.
    
- Publiczny rekord DNS A dla Twojej nazwy FQDN usługi federnej wskazuje publiczny adres IP internetowego narzędzia do równoważenia obciążenia platformy Azure dla serwerów proxy aplikacji sieci Web.
    
- Prywatny rekord DNS A dla Twojej nazwy FQDN usługi federnej wskazuje prywatny adres IP wewnętrznego narzędzia do równoważenia obciążenia platformy Azure dla serwerów usług AD FS.
    
- Publiczny certyfikat cyfrowy odpowiedni dla połączeń SSL z siecią SAN ustawioną jako nazwa FQDN Twojej usługi federyjnej to plik PFX przechowywany na serwerze synchronizacji katalogów.
    
- Certyfikat główny publicznego urzędu certyfikacji jest zainstalowany w magazynie Zaufane główne urzędy certyfikacji na komputerach i urządzeniach.
    
Oto przykład organizacji Contoso:
  
**Przykładowa konfiguracja infrastruktury uwierzytelniania federacyjne o wysokiej dostępności na platformie Azure**

![Przykładowa konfiguracja wysokiej dostępności usługi Microsoft 365 uwierzytelniania federacyjne na platformie Azure.](../media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>Uruchamianie usługi Azure AD Połączenie w celu skonfigurowania uwierzytelniania federeracyjnie

Narzędzie Azure AD Połączenie umożliwia skonfigurowanie serwerów usług AD FS, serwerów proxy aplikacji sieci Web oraz Microsoft 365 na Microsoft 365 w celu uwierzytelniania feder sądowego za pomocą poniższych kroków:
  
1. Utwórz połączenie pulpitu zdalnego z serwerem synchronizacji katalogów przy użyciu konta domeny z uprawnieniami administratora lokalnego.
    
2. Na komputerze stacjonarnym serwera synchronizacji katalogów otwórz program Internet Explorer i przejdź do strony [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
3. Na **Microsoft Azure Active Directory Połączenie kliknij** pozycję **Pobierz**, a następnie kliknij pozycję **Uruchom**.
    
4. Na stronie **konta usługi Azure AD Połączenie** Zapraszamy! kliknij pozycję **Zgadzam się,** a następnie kliknij przycisk **Kontynuuj.**
    
5. Na stronie **Ustawienia** Express kliknij pozycję **Dostosuj**.
    
6. Na stronie **Instalowanie wymaganych składników** kliknij pozycję **Zainstaluj**.
    
7. Na stronie **Logowanie użytkownika kliknij** pozycję Federacja z usługami **AD FS**, a następnie kliknij przycisk **Dalej**.
    
8. Na stronie **Połączenie do usługi Azure AD** wpisz nazwę i hasło administratora usługi **Azure AD DC** lub konta administratora globalnego subskrypcji usługi  Microsoft 365, a następnie kliknij przycisk **Dalej**.
    
9. Na **stronie Połączenie** katalogów upewnij się, że w lesie lokalnym programu Usługi domenowe w usłudze Active Directory (AD DS) jest wybrany las w **lesie, wpisz** nazwę i hasło konta administratora domeny, kliknij pozycję **Dodaj** katalog, a następnie kliknij przycisk **Dalej**.
    
10. Na stronie **Konfiguracja logowania do usługi Azure AD** kliknij przycisk **Dalej**.
    
11. Na **stronie Filtrowanie domeny i użytkowników OU** kliknij przycisk **Dalej**.
    
12. Na stronie **Unikatowe identyfikowanie użytkowników** kliknij przycisk **Dalej**.
    
13. Na stronie **Filtrowanie użytkowników i urządzeń** kliknij przycisk **Dalej**.
    
14. Na stronie **Funkcje opcjonalne** kliknij przycisk **Dalej**.
    
15. Na stronie **farmy usług AD FS** kliknij **pozycję Konfiguruj nową farmę usług AD FS**.
    
16. Kliknij **przycisk** Przeglądaj i określ lokalizację i nazwę certyfikatu SSL od publicznego urzędu certyfikacji.
    
17. Po wyświetleniu monitu wpisz hasło certyfikatu, a następnie kliknij przycisk **OK**.
    
18. Sprawdź, czy **nazwa podmiotu i** nazwa usługi federejnej są ustawione na nazwę FQDN Twojej usługi federowej, a następnie kliknij przycisk **Dalej**.
    
19. Na stronie **Serwery usług AD FS** wpisz nazwę pierwszego serwera usług AD FS (tabela M — element 4 — kolumna nazwa maszyny wirtualnej), a następnie kliknij przycisk **Dodaj**.
    
20. Wpisz nazwę drugiego serwera usług AD FS (tabela M — element 5 — kolumna nazwa maszyny wirtualnej), kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Dalej**.
    
21. Na stronie **Serwery proxy** aplikacji sieci Web wpisz nazwę serwera proxy aplikacji sieci Web (tabela M — element 6 — kolumna nazwa maszyny wirtualnej), a następnie kliknij przycisk **Dodaj**.
    
22. Wpisz nazwę serwera proxy drugiej aplikacji sieci Web (tabela M — element 7 — kolumna nazwa maszyny wirtualnej), kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Dalej**.
    
23. Na stronie **Poświadczenia administratora domeny** wpisz nazwę użytkownika i hasło konta administratora domeny, a następnie kliknij przycisk **Dalej**.
    
24. Na stronie **Konto usługi AD FS** wpisz nazwę użytkownika i hasło konta administratora przedsiębiorstwa, a następnie kliknij przycisk **Dalej**.
    
25. Na stronie **Domain (Domena) usługi Azure AD** w witrynie **Domain** (Domena) wybierz nazwę domeny DNS organizacji, a następnie kliknij przycisk **Next (Dalej**).
    
26. Na **stronie Wszystko gotowe do skonfigurowania** kliknij pozycję **Zainstaluj**.
    
27. Na stronie **Instalacja została ukończona** kliknij pozycję **Weryfikuj**. Powinny być wyświetlane dwa komunikaty informujące o pomyślnym zweryfikowaniu konfiguracji zarówno intranetu, jak i Internetu.
    
  - Wiadomość intranetowa powinna zawierać prywatny adres IP wewnętrznego narzędzia do równoważenia obciążenia platformy Azure dla serwerów usług AD FS.
    
  - Wiadomość internetowa powinna wyświetlić publiczny adres IP serwera proxy aplikacji sieci Web dostępnych w Internecie do równoważenia obciążenia systemu Azure.
    
28. Na stronie **Instalacja ukończona** kliknij pozycję **Zakończ**.
    
Oto ostateczna konfiguracja z nazwami zastępczymi serwerów.
  
**Etap 5. Ostateczna konfiguracja wysokiej dostępności federacyjnych infrastruktury uwierzytelniania na platformie Azure**

![Ostateczna konfiguracja wysokiej dostępności usługi Microsoft 365 uwierzytelniania federacyjne na platformie Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Twoja wysokiej dostępności federowana infrastruktura uwierzytelniania dla Microsoft 365 na platformie Azure jest ukończona.
  
## <a name="see-also"></a>Zobacz też

[Wdrażanie uwierzytelniania federeracyjnie o wysokiej dostępności Microsoft 365 na platformie Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Tożsamość federacyjna dla Twojego Microsoft 365 deweloper/środowisko testowania](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 rozwiązania i architektury](../solutions/index.yml)

[Tożsamość federeracyjna dla Microsoft 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)
