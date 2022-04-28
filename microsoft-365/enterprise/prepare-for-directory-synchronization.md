---
title: Przygotowanie do synchronizacji katalogów w celu Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: W tym artykule opisano sposób przygotowywania użytkowników do aprowizowania Microsoft 365 przy użyciu synchronizacji katalogów i długoterminowych korzyści wynikających z korzystania z tej metody.
ms.openlocfilehash: 03182d4cb0e9ed1da2687ab23ffae11369f3765a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090778"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a>Przygotowanie do synchronizacji katalogów w celu Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli wybrano model tożsamości hybrydowej i skonfigurowano ochronę kont administratorów w [kroku 2](protect-your-global-administrator-accounts.md) i kont użytkowników w [kroku 3](microsoft-365-secure-sign-in.md) tego rozwiązania, następnym zadaniem jest wdrożenie synchronizacji katalogów. Zalety synchronizacji katalogów w organizacji obejmują:

- Zmniejszanie programów administracyjnych w organizacji
- Opcjonalne włączanie scenariusza logowania jednokrotnego
- Automatyzowanie zmian konta w Microsoft 365

Aby uzyskać więcej informacji na temat zalet korzystania z synchronizacji katalogów, zobacz [tożsamość hybrydowa z usługą Azure Active Directory (Azure AD)](/azure/active-directory/hybrid/whatis-hybrid-identity).

Jednak synchronizacja katalogów wymaga planowania i przygotowania, aby upewnić się, że Active Directory Domain Services (AD DS) synchronizuje się z dzierżawą usługi Azure AD subskrypcji Microsoft 365 z minimalną ilością błędów.

Wykonaj następujące kroki, aby uzyskać najlepsze wyniki.

> [!NOTE]
> Znaki inne niż ASCII nie są synchronizowane dla żadnych atrybutów na koncie użytkownika usług AD DS.

## <a name="ad-ds-preparation"></a>Przygotowywanie usług AD DS

Aby zapewnić bezproblemowe przejście do Microsoft 365 przy użyciu synchronizacji, należy przygotować las usług AD DS przed rozpoczęciem wdrażania synchronizacji katalogów Microsoft 365.
  
Przygotowanie katalogu powinno koncentrować się na następujących zadaniach:

- Usuń zduplikowane atrybuty **proxyAddress** i **userPrincipalName** .
- Zaktualizuj puste i nieprawidłowe atrybuty **userPrincipalName** przy użyciu prawidłowych atrybutów **userPrincipalName** .
- Usuń nieprawidłowe i wątpliwe znaki w atrybutach **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname** i **userPrincipalName** . Aby uzyskać szczegółowe informacje na temat przygotowywania atrybutów, zobacz [List of attributes that are synced by the Azure Active Directory Sync Tool (Lista atrybutów synchronizowanych przez narzędzie Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719)).

    > [!NOTE]
    > Są to te same atrybuty, które Połączenie usługi Azure AD synchronizuje. 
  
## <a name="multi-forest-deployment-considerations"></a>Zagadnienia dotyczące wdrażania wielu lasów

W przypadku wielu lasów i opcji logowania jednokrotnego użyj [instalacji niestandardowej usługi Azure AD Połączenie](/azure/active-directory/hybrid/how-to-connect-install-custom).
  
Jeśli Twoja organizacja ma wiele lasów do uwierzytelniania (lasy logowania), zdecydowanie zalecamy następujące kwestie:
  
- **Rozważ skonsolidowanie lasów.** Ogólnie rzecz biorąc, do utrzymania wielu lasów jest wymaganych więcej narzutów. Jeśli organizacja nie ma ograniczeń zabezpieczeń, które dyktują potrzebę oddzielnych lasów, rozważ uproszczenie środowiska lokalnego.
- **Użyj tylko w podstawowym lesie logowania.** Rozważ wdrożenie Microsoft 365 tylko w podstawowym lesie logowania na potrzeby początkowego wdrożenia Microsoft 365. 

Jeśli nie możesz skonsolidować wdrożenia usług AD DS w wielu lasach lub używasz innych usług katalogowych do zarządzania tożsamościami, możesz zsynchronizować je z pomocą firmy Microsoft lub partnera.
  
Aby uzyskać więcej informacji[, zobacz Topologie dla usługi Azure AD Połączenie](/azure/active-directory/hybrid/plan-connect-topologies).
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Funkcje zależne od synchronizacji katalogów
  
Synchronizacja katalogów jest wymagana dla następujących funkcji i funkcji:
  
- Bezproblemowe Sign-On jednokrotne usługi Azure AD
- współistnienie Skype
- Exchange wdrożenie hybrydowe, w tym:
  - W pełni udostępniona globalna lista adresów (GAL) między lokalnym środowiskiem Exchange i Microsoft 365.
  - Synchronizowanie informacji gal z różnych systemów poczty.
  - Możliwość dodawania użytkowników do oferty usług Microsoft 365 i usuwania ich z niej. Wymaga to następujących czynności:
  - Podczas konfigurowania synchronizacji katalogów należy skonfigurować synchronizację dwukierunkową. Domyślnie narzędzia synchronizacji katalogów zapisuje informacje o katalogu tylko w chmurze. Podczas konfigurowania synchronizacji dwukierunkowej włączasz funkcję zapisu zwrotnego, dzięki czemu ograniczona liczba atrybutów obiektów jest kopiowana z chmury, a następnie zapisywana z powrotem w lokalnych usługach AD DS. Zapisywanie zwrotne jest również nazywane trybem hybrydowym Exchange. 
  - Lokalne wdrożenie hybrydowe Exchange
  - Możliwość przenoszenia niektórych skrzynek pocztowych użytkowników do Microsoft 365 przy jednoczesnym zachowaniu lokalnych skrzynek pocztowych innych użytkowników.
  - Sejf nadawców i zablokowanych nadawców lokalnych są replikowane do Microsoft 365.
  - Podstawowe funkcje delegowania i wysyłania wiadomości e-mail w imieniu.
  - Masz zintegrowaną lokalną kartę inteligentną lub rozwiązanie do uwierzytelniania wieloskładnikowego.
- Synchronizacja zdjęć, miniatur, sal konferencyjnych i grup zabezpieczeń

## <a name="1-directory-cleanup-tasks"></a>1. Zadania oczyszczania katalogów

Przed zsynchronizowanie usług AD DS z dzierżawą usługi Azure AD należy wyczyścić usługi AD DS.

> [!IMPORTANT]
> Jeśli nie wykonasz oczyszczania usług AD DS przed synchronizacją, może to prowadzić do znaczącego negatywnego wpływu na proces wdrażania. Może upłynąć kilka dni, a nawet tygodni, aby przejść przez cykl synchronizacji katalogów, identyfikowania błędów i ponownej synchronizacji.

W usługach AD DS wykonaj następujące zadania oczyszczania dla każdego konta użytkownika, do których zostanie przypisana licencja Microsoft 365:

1. Upewnij się, że prawidłowy i unikatowy adres e-mail w atrybucie **proxyAddresses** .

2. Usuń wszystkie zduplikowane wartości w atrybucie **proxyAddresses** .

3. Jeśli to możliwe, upewnij się prawidłową i unikatową wartość atrybutu **userPrincipalName** w obiekcie **użytkownika** użytkownika. Aby uzyskać najlepsze środowisko synchronizacji, upewnij się, że nazwa UPN usług AD DS jest zgodna z nazwą UPN usługi Azure AD. Jeśli użytkownik nie ma wartości atrybutu **userPrincipalName** , obiekt **użytkownika** musi zawierać prawidłową i unikatową wartość atrybutu **sAMAccountName** . Usuń wszystkie zduplikowane wartości w atrybucie **userPrincipalName** .

4. Aby optymalnie wykorzystać globalną listę adresów (GAL), upewnij się, że informacje zawarte w następujących atrybutach konta użytkownika usług AD DS są poprawne:

   - Givenname
   - Nazwisko
   - displayName
   - Stanowisko
   - Department
   - Pakiet Office
   - Tel. w biurze
   - Telefon komórkowy
   - Numer faksu
   - Adres ulicy
   - Miasto
   - Województwo
   - Kod pocztowy lub pocztowy
   - Kraj lub region

## <a name="2-directory-object-and-attribute-preparation"></a>2. Przygotowywanie obiektu katalogu i atrybutu

Pomyślna synchronizacja katalogów między usługami AD DS i Microsoft 365 wymaga odpowiedniego przygotowania atrybutów usług AD DS. Na przykład należy upewnić się, że określone znaki nie są używane w niektórych atrybutach, które są synchronizowane ze środowiskiem Microsoft 365. Nieoczekiwane znaki nie powodują niepowodzenia synchronizacji katalogów, ale mogą zwracać ostrzeżenie. Nieprawidłowe znaki spowodują niepowodzenie synchronizacji katalogów.

Synchronizacja katalogów również zakończy się niepowodzeniem, jeśli niektórzy użytkownicy usług AD DS mają co najmniej jeden zduplikowany atrybut. Każdy użytkownik musi mieć unikatowe atrybuty.

Atrybuty, które należy przygotować, są wymienione tutaj:

- **displayName**

  - Jeśli atrybut istnieje w obiekcie użytkownika, zostanie zsynchronizowany z Microsoft 365.
  - Jeśli ten atrybut istnieje w obiekcie użytkownika, musi być dla niego wartość. Oznacza to, że atrybut nie może być pusty.
  - Maksymalna liczba znaków: 256

- **Givenname**

  - Jeśli atrybut istnieje w obiekcie użytkownika, zostanie zsynchronizowany z Microsoft 365, ale Microsoft 365 nie wymaga ani nie używa go.
  - Maksymalna liczba znaków: 64

- **mail**

  - Wartość atrybutu musi być unikatowa w katalogu.

    > [!NOTE]
    > Jeśli istnieją zduplikowane wartości, pierwszy użytkownik z wartością zostanie zsynchronizowany. Kolejni użytkownicy nie będą pojawiać się w Microsoft 365. Aby obaj użytkownicy pojawili się w Microsoft 365, musisz zmodyfikować wartość w Microsoft 365 lub zmodyfikować obie wartości w usługach AD DS.

- **mailNickname** (alias Exchange)

  - Wartość atrybutu nie może zaczynać się kropką (.).
  - Wartość atrybutu musi być unikatowa w katalogu.

    > [!NOTE]
    > Podkreślenia ("_") w zsynchronizowanej nazwie wskazują, że oryginalna wartość tego atrybutu zawiera nieprawidłowe znaki. Aby uzyskać więcej informacji na temat tego atrybutu, zobacz [Exchange atrybut aliasu](/powershell/module/exchange/set-mailbox).
    >

- **Proxyaddresses**

  - Atrybut wielokrotnej wartości
  - Maksymalna liczba znaków na wartość: 256
  - Wartość atrybutu nie może zawierać spacji.
  - Wartość atrybutu musi być unikatowa w katalogu.
  - Nieprawidłowe znaki: \< \> ( ) ; , [ ] "
  - Litery ze znakami diakrytycznymi, takimi jak umlauts, akcenty i kafelki, są nieprawidłowymi znakami.

    Należy pamiętać, że nieprawidłowe znaki mają zastosowanie do znaków następujących po ograniczniku typu i ":", tak że SMTP:User@contso.com jest dozwolone, ale SMTP:user:M@contoso.com nie jest.

    > [!IMPORTANT]
    > Wszystkie adresy protokołu SMTP (Simple Mail Transport Protocol) powinny być zgodne ze standardami obsługi wiadomości e-mail. Usuń zduplikowane lub niepożądane adresy, jeśli istnieją.

- **Samaccountname**

  - Maksymalna liczba znaków: 20
  - Wartość atrybutu musi być unikatowa w katalogu.
  - Nieprawidłowe znaki: [ \ " | , / : \< \> + = ; ? \* ']
  - Jeśli użytkownik ma nieprawidłowy atrybut **sAMAccountName**, ale ma prawidłowy atrybut **userPrincipalName**, konto użytkownika jest tworzone w Microsoft 365.
  - Jeśli zarówno **sAMAccountName** , jak i **userPrincipalName** są nieprawidłowe, należy zaktualizować atrybut **userPrincipalName** usług AD DS.

- **sn** (nazwisko)

  - Jeśli atrybut istnieje w obiekcie użytkownika, zostanie zsynchronizowany z Microsoft 365, ale Microsoft 365 nie wymaga ani nie używa go.

- **Targetaddress**

    Wymagane jest, aby atrybut **targetAddress** (na przykład SMTP:tom@contoso.com) wypełniony dla użytkownika musiał pojawić się w Microsoft 365 GAL. W scenariuszach migracji komunikatów innych firm wymagałoby to rozszerzenia schematu Microsoft 365 dla usług AD DS. Rozszerzenie schematu Microsoft 365 doda również inne przydatne atrybuty do zarządzania obiektami Microsoft 365, które są wypełniane przy użyciu narzędzia do synchronizacji katalogów z usług AD DS. Na przykład atrybut **msExchHideFromAddressLists** do zarządzania ukrytymi skrzynkami pocztowymi lub grupami dystrybucyjnymi zostanie dodany.

  - Maksymalna liczba znaków: 256
  - Wartość atrybutu nie może zawierać spacji.
  - Wartość atrybutu musi być unikatowa w katalogu.
  - Nieprawidłowe znaki: \ \< \> ( ) ; , [ ] "
  - Wszystkie adresy protokołu SMTP (Simple Mail Transport Protocol) powinny być zgodne ze standardami obsługi wiadomości e-mail.

- **Userprincipalname**

  - Atrybut **userPrincipalName** musi mieć format logowania w stylu internetowym, w którym po nazwie użytkownika następuje znak at (@) i nazwa domeny: na przykład user@contoso.com. Wszystkie adresy protokołu SMTP (Simple Mail Transport Protocol) powinny być zgodne ze standardami obsługi wiadomości e-mail.
  - Maksymalna liczba znaków atrybutu **userPrincipalName** wynosi 113. Określona liczba znaków jest dozwolona przed i po znaku at (@), w następujący sposób:
  - Maksymalna liczba znaków dla nazwy użytkownika, która znajduje się przed znakiem at (@): 64
  - Maksymalna liczba znaków dla nazwy domeny po znaku at (@): 48
  - Nieprawidłowe znaki: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "
  - Dozwolone znaki: A – Z, a - z, 0 – 9, ' . - _ ! # ^ ~
  - Litery ze znakami diakrytycznymi, takimi jak umlauts, akcenty i kafelki, są nieprawidłowymi znakami.
  - Znak @jest wymagany w każdej wartości **userPrincipalName** .
  - Znak @nie może być pierwszym znakiem w każdej wartości **userPrincipalName** .
  - Nazwa użytkownika nie może kończyć się kropką (.), znakiem ampersand (&amp;), spację lub znakiem at (@).
  - Nazwa użytkownika nie może zawierać żadnych spacji.
  - Należy używać domen routingu; Na przykład nie można używać domen lokalnych lub wewnętrznych.
  - Unicode jest konwertowany na znaki podkreślenia.
  - **userPrincipalName** nie może zawierać żadnych zduplikowanych wartości w katalogu.

## <a name="3-prepare-the-userprincipalname-attribute"></a>3. Przygotowanie atrybutu userPrincipalName

Usługa Active Directory została zaprojektowana tak, aby umożliwić użytkownikom końcowym w organizacji logowanie się do katalogu przy użyciu **nazwy sAMAccountName** lub **userPrincipalName**. Podobnie użytkownicy końcowi mogą logować się do Microsoft 365 przy użyciu głównej nazwy użytkownika (UPN) swojego konta służbowego. Synchronizacja katalogów próbuje utworzyć nowych użytkowników w Azure Active Directory przy użyciu tej samej nazwy UPN, która jest w usługach AD DS. Nazwa UPN jest sformatowana jak adres e-mail.

W Microsoft 365 nazwa UPN jest atrybutem domyślnym używanym do generowania adresu e-mail. Łatwo jest pobrać **właściwość userPrincipalName** (w usługach AD DS i w usłudze Azure AD) oraz podstawowy adres e-mail w **pliku proxyAddresses** ustawiony na różne wartości. Gdy są one ustawione na różne wartości, mogą wystąpić nieporozumienia dla administratorów i użytkowników końcowych.

Najlepiej jest dostosować te atrybuty, aby zmniejszyć zamieszanie. Aby spełnić wymagania logowania jednokrotnego z usługą Active Directory Federation Services (AD FS) 2.0, musisz upewnić się, że nazwy UPN w Azure Active Directory i usługi AD DS są zgodne i używają prawidłowej przestrzeni nazw domeny.

## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. Dodawanie alternatywnego sufiksu nazwy UPN do usług AD DS

Może być konieczne dodanie alternatywnego sufiksu nazwy UPN, aby skojarzyć poświadczenia firmowe użytkownika ze środowiskiem Microsoft 365. Sufiks nazwy UPN jest częścią nazwy UPN po prawej stronie znaku @. Nazwy UPN używane do logowania jednokrotnego mogą zawierać litery, cyfry, kropki, kreski i podkreślenia, ale bez innych typów znaków.

Aby uzyskać więcej informacji na temat dodawania alternatywnego sufiksu nazwy UPN do usługi Active Directory, zobacz [Przygotowywanie do synchronizacji katalogów](https://go.microsoft.com/fwlink/p/?LinkId=525430).

## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a>5. Dopasuj nazwę UPN usług AD DS do nazwy UPN Microsoft 365

Jeśli synchronizacja katalogów została już skonfigurowana, nazwa UPN użytkownika dla Microsoft 365 może nie być zgodna z nazwą UPN usług AD DS użytkownika zdefiniowaną w usługach AD DS. Może to wystąpić, gdy użytkownikowi przypisano licencję przed zweryfikowaniem domeny. Aby rozwiązać ten problem, użyj programu [PowerShell, aby naprawić zduplikowaną nazwę UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730), aby zaktualizować nazwę UPN użytkownika, aby upewnić się, że nazwa UPN Microsoft 365 jest zgodna z firmową nazwą użytkownika i domeną. Jeśli aktualizujesz nazwę UPN w usługach AD DS i chcesz ją zsynchronizować z tożsamością Azure Active Directory, musisz usunąć licencję użytkownika w Microsoft 365 przed wprowadzeniem zmian w usługach AD DS.

Zobacz również [Jak przygotować domenę bez routingu (taką jak domena lokalna) do synchronizacji katalogów](prepare-a-non-routable-domain-for-directory-synchronization.md).

## <a name="next-steps"></a>Następne kroki

Po wykonaniu od 1 do 5 powyższych czynności zobacz [Konfigurowanie synchronizacji katalogów](set-up-directory-synchronization.md).
