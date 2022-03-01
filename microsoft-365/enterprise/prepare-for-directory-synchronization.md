---
title: Przygotowywanie do synchronizacji katalogów z Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: W tym artykule opisano, jak przygotować się do zapewnienia Microsoft 365 użytkowników na Microsoft 365 przy użyciu synchronizacji katalogów oraz długoterminowe korzyści wynikające z używania tej metody.
ms.openlocfilehash: 5a8914091eb8df62ba71c8ddff35c3fb355fa031
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013880"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a>Przygotowywanie do synchronizacji katalogów z Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli wybrano model tożsamości hybrydowej i skonfigurowano ochronę kont administratora w kroku [2](protect-your-global-administrator-accounts.md) i kontach użytkowników w kroku [3](microsoft-365-secure-sign-in.md) tego rozwiązania, następnym zadaniem jest wdrożenie synchronizacji katalogów. Zalety synchronizacji katalogów dla organizacji obejmują:

- Zmniejszenie liczby programów administracyjnych w organizacji
- Opcjonalne włączenie scenariusza logowania pojedynczego
- Automatyzowanie zmian na koncie w Microsoft 365

Aby uzyskać więcej informacji o zaletach korzystania z synchronizacji katalogów, zobacz Tożsamość hybrydowa z usługą [Azure Active Directory (Azure AD).](/azure/active-directory/hybrid/whatis-hybrid-identity)

Jednak synchronizacja katalogów wymaga planowania i przygotowywania w celu zapewnienia, że Usługi domenowe w usłudze Active Directory (AD DS) synchronizuje się z dzierżawą usługi Azure AD Twojej subskrypcji usługi Microsoft 365 z minimalnymi błędami.

Aby uzyskać najlepsze wyniki, wykonaj poniższe czynności.

> [!NOTE]
> Znaki inne niż ASCII nie są synchronizowane dla żadnych atrybutów na AD DS użytkownika.

## <a name="ad-ds-preparation"></a>AD DS przygotowania

Aby zapewnić bezproblemowe przejście do programu Microsoft 365 przy użyciu synchronizacji, musisz przygotować las AD DS przed rozpoczęciem wdrażania synchronizacji Microsoft 365 katalogów.
  
Przygotowanie katalogu powinno być skoncentrowane na następujących zadaniach:

- Usuń **zduplikowane atrybuty proxyAddress** i **userPrincipalName** .
- Aktualizowanie pustych i nieprawidłowych **atrybutów userPrincipalName** prawidłowymi **atrybutami userPrincipalName** .
- Usunięcie nieprawidłowych i kwestionowanych znaków w atrybutach **givenName**, nazwisko ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname** i **userPrincipalName** . Aby uzyskać szczegółowe informacje na temat przygotowywania atrybutów, zobacz Lista atrybutów synchronizowanych przez narzędzie [Azure Active Directory synchronizacji](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Są to te same atrybuty, które są synchronizowane Połączenie Azure AD. 
  
## <a name="multi-forest-deployment-considerations"></a>Zagadnienia dotyczące wdrażania wielu lasów

W przypadku korzystania z wielu lasów i opcji logowania jednokrotnego użyj opcji [Niestandardowa instalacja usługi Azure AD Połączenie](/azure/active-directory/hybrid/how-to-connect-install-custom).
  
Jeśli Twoja organizacja ma wiele lasów uwierzytelniania (lasów logowania), zdecydowanie zalecamy:
  
- **Rozważ skonsolidowanie swoich lasów.** Na ogół utrzymywanie wielu lasów jest o wiele większe obciążenie. Jeśli w Twojej organizacji nie ma ograniczeń dotyczących zabezpieczeń, które wymagają osobnych lasów, rozważ uproszczenie środowiska lokalnego.
- **Używaj tylko w podstawowym lesie logowania.** Rozważ wdrożenie Microsoft 365 tylko w podstawowym lesie logowania na początku wdrożenia usługi Microsoft 365. 

Jeśli nie możesz skonsolidować wdrożenia usługi multi-forest AD DS lub zarządzasz tożsamościami za pomocą innych usług katalogowych, możesz zsynchronizować je z pomocą firmy Microsoft lub partnera.
  
Aby [uzyskać więcej informacji, zobacz Topologii usługi Azure AD Połączenie](/azure/active-directory/hybrid/plan-connect-topologies).
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Funkcje zależne od synchronizacji katalogów
  
Synchronizacja katalogów jest wymagana dla następujących funkcji:
  
- Bezproblemowe logowanie jednokrotne Sign-On w usłudze Azure AD
- Skype współistnienie
- Exchange hybrydowe, w tym:
  - Całkowicie udostępniona globalna lista adresowa (GAL) między lokalnym środowiskiem Exchange a Microsoft 365.
  - Synchronizowanie informacji na temat listy adresowej z różnych systemów poczty.
  - Możliwość dodawania i usuwania użytkowników z Microsoft 365 usług. Wymagane są następujące elementy:
  - Podczas konfigurowania synchronizacji katalogów należy skonfigurować synchronizację dwukierunkową. Domyślnie narzędzia do synchronizacji katalogów zapisuje informacje z katalogu tylko w chmurze. Po skonfigurowaniu synchronizacji dwukierunkowej włącz funkcję zapisu, aby ograniczona liczba atrybutów obiektów było kopiowana z chmury, a następnie zapisywana z powrotem w lokalnym programie AD DS. Cofanie jest również nazywane Exchange trybem hybrydowym. 
  - Lokalne wdrożenie Exchange hybrydowe
  - Możliwość przenoszenia niektórych skrzynek pocztowych użytkowników do Microsoft 365 przy zachowaniu innych skrzynek pocztowych użytkowników lokalnie.
  - Sejf i zablokowani nadawcy lokalnie są replikowane do Microsoft 365.
  - Delegowanie podstawowe i funkcja wysyłania w imieniu poczty e-mail.
  - Masz zintegrowane lokalne karty inteligentne lub rozwiązanie do uwierzytelniania wieloskładnikowego.
- Synchronizacja zdjęć, miniatur, sal konferencyjnych i grup zabezpieczeń

## <a name="1-directory-cleanup-tasks"></a>1. Zadania oczyszczania katalogu

Przed zsynchronizowaniem danych AD DS dzierżawy usługi Azure AD należy wyczyścić konto AD DS.

> [!IMPORTANT]
> Jeśli nie wykonasz oczyszczania AD DS synchronizacji, może to mieć znaczący negatywny wpływ na proces wdrażania. Cykl synchronizacji katalogów, identyfikowania błędów i ponownej synchronizacji może zająć kilka dni lub nawet kilka tygodni.

W AD DS wykonaj następujące zadania oczyszczania dla każdego konta użytkownika, do których zostanie przypisana Microsoft 365 licencji:

1. Upewnij się, że w atrybutu **proxyAddresses jest prawidłowy i unikatowy adres e-mail** .

2. Usuń wszelkie zduplikowane wartości **atrybutu proxyAddresses** .

3. Jeśli to możliwe, upewnij się, że wartość **atrybutu userPrincipalName** jest prawidłowa i **unikatowa** w obiekcie użytkownika. Aby zapewnić najlepsze środowisko synchronizacji, upewnij się, że AD DS upn jest taka, jak w usłudze Azure AD UPN. Jeśli atrybut **userPrincipalName** użytkownika nie ma wartości, obiekt user musi zawierać prawidłową i  **unikatową wartość atrybutu sAMAccountName**. Usuń wszelkie zduplikowane wartości **atrybutu userPrincipalName** .

4. Aby optymalnie korzystać z globalnej listy adresowej, upewnij się, że informacje w następujących atrybutach konta AD DS są poprawne:

   - givenName
   - nazwisko
   - displayName
   - Stanowisko
   - Department
   - Pakiet Office
   - Tel. w biurze
   - Telefon komórkowy
   - Numer faksu
   - Ulica
   - Miasto
   - Województwo
   - Kod pocztowy
   - Kraj lub region

## <a name="2-directory-object-and-attribute-preparation"></a>2. Przygotowywanie atrybutów i obiektów katalogu

Pomyślna synchronizacja katalogów między AD DS i Microsoft 365 wymaga odpowiedniego przygotowania AD DS atrybutów katalogów. Na przykład należy się upewnić, że w pewnych atrybutach synchronizowanych ze środowiskiem użytkownika nie są używane Microsoft 365 znaki. Nieoczekiwane znaki nie powodują, że synchronizacja katalogów nie powiedzie się, ale może spowodować zwrócenie ostrzeżenia. Nieprawidłowe znaki powodują niepowodzenie synchronizacji katalogów.

Synchronizacja katalogów również nie powiedzie się, jeśli niektórzy użytkownicy AD DS mają co najmniej jeden zduplikowany atrybut. Każdy użytkownik musi mieć unikatowe atrybuty.

Poniżej wymieniono atrybuty, które należy przygotować:

- **displayName**

  - Jeśli ten atrybut istnieje w obiekcie użytkownika, zostanie zsynchronizowany z Microsoft 365.
  - Jeśli ten atrybut istnieje w obiekcie użytkownika, musi mieć wartość. Oznacza to, że ten atrybut nie może być pusty.
  - Maksymalna liczba znaków: 256

- **givenName**

  - Jeśli ten atrybut istnieje w obiekcie użytkownika, zostanie zsynchronizowany z Microsoft 365, ale Microsoft 365 nie wymaga go ani nie używa.
  - Maksymalna liczba znaków: 64

- **mail**

  - Wartość atrybutu musi być unikatowa w katalogu.

    > [!NOTE]
    > Jeśli istnieją wartości zduplikowane, zsynchronizowany zostanie pierwszy użytkownik z wartością. Kolejni użytkownicy nie pojawią się w Microsoft 365. Aby obaj użytkownicy pojawiali się w Microsoft 365, należy zmodyfikować albo wartość w Microsoft 365 lub obie wartości w AD DS.

- **mailNickname** (alias Exchange poczty)

  - Wartość atrybutu nie może rozpoczynać się od okresu (.).
  - Wartość atrybutu musi być unikatowa w katalogu.

    > [!NOTE]
    > Znaki podkreślenia ("_") w zsynchronizowanej nazwie oznaczają, że oryginalna wartość tego atrybutu zawiera nieprawidłowe znaki. Aby uzyskać więcej informacji na temat tego atrybutu, [Exchange atrybut aliasu](/powershell/module/exchange/set-mailbox).
    >

- **proxyAddresses**

  - Atrybut wielo wartości
  - Maksymalna liczba znaków na wartość: 256
  - Wartość atrybutu nie może zawierać spacji.
  - Wartość atrybutu musi być unikatowa w katalogu.
  - Nieprawidłowe znaki: \< \> () ; , [ ] "
  - Litery ze znakami diakrytycznymi, takimi jak umlauty, akcenty i tyldy, to nieprawidłowe znaki.

    Nieprawidłowe znaki dotyczą znaków następujących po ograniczniku typu i znaków ":", co oznacza, że SMTP:User@contso.com dozwolone, ale SMTP:user:M@contoso.com nie jest.

    > [!IMPORTANT]
    > Wszystkie adresy SMTP (Simple Mail Transport Protocol) powinny być zgodne ze standardami wiadomości e-mail. Usuń zduplikowane lub niechciane adresy, jeśli istnieją.

- **sAMAccountName**

  - Maksymalna liczba znaków: 20
  - Wartość atrybutu musi być unikatowa w katalogu.
  - Nieprawidłowe znaki: [ \ " | , / : \< \> + = ; ? \* ']
  - Jeśli użytkownik ma nieprawidłowy atrybut **sAMAccountName**, ale ma prawidłowy atrybut **userPrincipalName**, konto użytkownika jest tworzone w programie Microsoft 365.
  - Jeśli oba **atrybuty sAMAccountName** i **userPrincipalName** są nieprawidłowe, należy zaktualizować AD DS **userPrincipalName** .

- **sn** (surname)

  - Jeśli ten atrybut istnieje w obiekcie użytkownika, zostanie zsynchronizowany z Microsoft 365, ale Microsoft 365 nie wymaga go ani nie używa.

- **targetAddress**

    Wymagane jest, aby atrybut **targetAddress** (na przykład SMTP:tom@contoso.com), który jest wypełniony dla użytkownika, był widoczny na Microsoft 365 GAL. W scenariuszach z migracją wiadomości innych firm wymagałoby to rozszerzenia schematu Microsoft 365 dla AD DS. Rozszerzenie Microsoft 365 schematu dodałoby również inne przydatne atrybuty do zarządzania obiektami Microsoft 365, które są wypełniane za pomocą narzędzia do synchronizacji katalogów z usługi AD DS. Na przykład zostanie dodany **atrybut msExchHideFromAddressLists** do zarządzania ukrytymi skrzynkami pocztowymi lub grupami dystrybucyjnmi.

  - Maksymalna liczba znaków: 256
  - Wartość atrybutu nie może zawierać spacji.
  - Wartość atrybutu musi być unikatowa w katalogu.
  - Nieprawidłowe znaki: \ \< \> ( ) ; , [ ] "
  - Wszystkie adresy SMTP (Simple Mail Transport Protocol) powinny być zgodne ze standardami wiadomości e-mail.

- **userPrincipalName**

  - Atrybut **userPrincipalName** musi mieć format logowania typu internetowego, po którym po nazwie użytkownika musi znajdować się znak "@" i nazwa domeny, na przykład user@contoso.com. Wszystkie adresy SMTP (Simple Mail Transport Protocol) powinny być zgodne ze standardami wiadomości e-mail.
  - Maksymalna liczba znaków **atrybutu userPrincipalName** wynosi 113. Przed znakiem "@" i po nim są dozwolone określone liczby znaków:
  - Maksymalna liczba znaków nazwy użytkownika przed znakiem "@": 64
  - Maksymalna liczba znaków nazwy domeny po znaku "@": 48
  - Nieprawidłowe znaki: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "
  - Dozwolone znaki: A – Z, a - z, 0 – 9, ' . - _ ! # ^ ~
  - Litery ze znakami diakrytycznymi, takimi jak umlauty, akcenty i tyldy, to nieprawidłowe znaki.
  - Każda wartość **userPrincipalName wymaga znaku** @.
  - Znak @ nie może być pierwszym znakiem w każdej wartości **userPrincipalName** .
  - Nazwa użytkownika nie może kończyć się znakiem spacji (.), znakiem "i" (&amp;), znakiem spacji ani znakiem @.
  - Nazwa użytkownika nie może zawierać spacji.
  - Należy używać domen routowalnych; nie można na przykład używać domen lokalnych ani wewnętrznych.
  - Znaki Unicode są konwertowane na znaki podkreślenia.
  - **Wartość userPrincipalName** nie może zawierać zduplikowanych wartości w katalogu.

## <a name="3-prepare-the-userprincipalname-attribute"></a>3. Przygotowywanie atrybutu userPrincipalName

Usługa Active Directory została zaprojektowana tak, aby umożliwić użytkownikom końcowy w Twojej organizacji logowanie się do katalogu za pomocą nazwy **sAMAccountName** lub **userPrincipalName**. Podobnie użytkownicy końcowi mogą zalogować się Microsoft 365 przy użyciu głównej nazwy użytkownika (UPN) swojego konta służbowego. Synchronizacja katalogów próbuje utworzyć nowych użytkowników w usłudze Azure Active Directory przy użyciu tej samej upn, która jest w Twojej AD DS. UpN jest formatowana jak adres e-mail.

W Microsoft 365 adres e-mail jest domyślnym atrybutem używanym do wygenerowania upn. Możesz łatwo uzyskać wartość **userPrincipalName** (w usłudze AD DS i usłudze Azure AD) oraz podstawowy adres e-mail w adresie **proxyAddresses** ustawionym na inne wartości. Gdy są ustawione różne wartości, administratorzy i użytkownicy końcowi mogą mieć wątpliwości.

Najlepiej jest wyrównać te atrybuty, aby uniknąć nieporozumień. Aby spełnić wymagania logowania pojedynczego w usługach feder biznesowych Active Directory (AD FS) 2.0, należy się upewnić, że nazwy UPN w usłudze Azure Active Directory i Twojej usłudze AD DS są zgodne i że korzystasz z prawidłowej przestrzeni nazw domen.

## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. Dodawanie alternatywnego sufiksu upn do listy AD DS

Może być konieczne dodanie alternatywnego sufiksu upn w celu skojarzenia firmowych poświadczeń użytkownika ze środowiskiem Microsoft 365 sieci. Sufiks głównej nazwy użytkownika jest częścią głównej nazwy użytkownika po prawej stronie znaku @. Głównych numerów telefonów (UPN) używanych do logowania pojedynczego mogą zawierać litery, cyfry, kropki, kreski i podkreślenia, ale nie mogą zawierać znaków innych typów.

Aby uzyskać więcej informacji na temat dodawania alternatywnego sufiksu upn do usługi Active Directory, zobacz [Przygotowanie do synchronizacji katalogów](https://go.microsoft.com/fwlink/p/?LinkId=525430).

## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a>5. Dopasuj AD DS UPN do Microsoft 365 UPN

Jeśli została już ustawiona synchronizacja katalogów, główny nazwa użytkownika w programie Microsoft 365 może być nie do siebie dopasowana do nazwy upn AD DS użytkownika zdefiniowanej w AD DS. Może się tak zdarzyć, gdy użytkownikowi przypisano licencję przed zweryfikowaniem domeny. Aby rozwiązać ten problem, za pomocą programu PowerShell napraw zduplikowaną nazwę [UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) w celu zaktualizowania upn użytkownika w celu upewninia się, że Microsoft 365 upn jest taka sama jak firmowa nazwa użytkownika i domena. Jeśli aktualizujesz nazwę UPN w programie AD DS i chcesz zsynchronizować ją z tożsamością programu Azure Active Directory, przed wprowadzeniem zmian w programie AD DS należy usunąć licencję użytkownika w programie Microsoft 365.

Zobacz też [Jak przygotować domenę nie routowaną (taką jak domena .local) do synchronizacji katalogów](prepare-a-non-routable-domain-for-directory-synchronization.md).

## <a name="next-steps"></a>Następne kroki

Po zakończeniu synchronizacji katalogów (od 1 do 5 powyżej) zobacz [Konfigurowanie synchronizacji katalogów](set-up-directory-synchronization.md).
