---
title: Wykrywanie i korygowanie zgodzie niedozwolonych
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
description: Dowiedz się, jak rozpoznać i rozwiązać ten temat w Microsoft 365.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: db401231a2db0bddf1115cbdf14ae14cc9897f57
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021363"
---
# <a name="detect-and-remediate-illicit-consent-grants"></a>Wykrywanie i korygowanie zgodzie niedozwolonych

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Podsumowanie**  Dowiedz się, jak rozpoznać i rozwiązać ten temat w Microsoft 365.

## <a name="what-is-the-illicit-consent-grant-attack-in-microsoft-365"></a>Co to jest atak zgody po udzieleniu zgody w Microsoft 365?

W przypadku ataku ze zgodą wsadową przez administratora użytkownik tworzy aplikację zarejestrowaną na platformie Azure, która prosi o dostęp do danych, takich jak dane kontaktowe, wiadomości e-mail czy dokumenty. Następnie atakujący nakłoni użytkownika końcowego do udzielenia tej aplikacji zgody na dostęp do jego danych w ramach ataku służącego do wyłudzania informacji lub przez wsuń kod źródłowy do zaufanej witryny internetowej. Po przyznaniu zgody aplikacji mobilnej ma ona dostęp do danych na poziomie konta bez konieczności stosowania konta organizacji. Normalne kroki rozwiązywania problemów, takie jak resetowanie haseł dla naruszeń kont lub wymaganie uwierzytelniania wieloskładnikowego na kontach, nie są skuteczne w przypadku tego typu ataków, ponieważ są to aplikacje innych firm i zewnętrzni organizacje.

W tych atakach wykorzystuje się model interakcji, który zakłada, że podmiot, który nazywa się informacjami, to automatyzacja, a nie ludzie.

> [!IMPORTANT]
> Czy podejrzewasz, że właśnie teraz występują problemy z wyrażeniem zgody przez aplikację? Program Microsoft Defender for Cloud Apps oferuje narzędzia do wykrywania, badanie i rozwiązywania problemów z aplikacjami OAuth. Ten artykuł dotyczący usługi Defender for Cloud Apps zawiera samouczek, w którym przedstawiono, jak badać [ryzykowne aplikacje OAuth](/cloud-app-security/investigate-risky-oauth). Możesz również ustawić zasady aplikacji [protokołu OAuth](/cloud-app-security/app-permission-policy) w celu zbadania uprawnień żądanych przez aplikację, które użytkownicy zatwierdzają te aplikacje, oraz do szerokiego zatwierdzania lub blokowania tych żądań uprawnień.

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-microsoft-365"></a>Jak wygląda atak ze zgodą osoby, która udzieli zgody, w programie Microsoft 365?

Musisz przeszukać dziennik inspekcji, aby znaleźć znaki, nazywane również wskaźnikami naruszenia zabezpieczeń (IOC, Indicators of Compromise) tego ataku. W przypadku organizacji z wieloma zarejestrowanymi aplikacjami na platformie Azure i dużą bazą użytkowników najlepszym rozwiązaniem jest co tydzień przeglądanie organizacji, na które się zgadzasz.

### <a name="steps-for-finding-signs-of-this-attack"></a>Procedura znajdowania znaków tego ataku

1. Otwórz portal Microsoft 365 Defender, a <https://security.microsoft.com> następnie wybierz pozycję **Inspekcja**. Możesz też przejść bezpośrednio do strony **Inspekcja**, używając <https://security.microsoft.com/auditlogsearch>.

2. Na stronie **Inspekcja** sprawdź, **czy jest** zaznaczona karta Wyszukiwanie, a następnie skonfiguruj następujące ustawienia:
   - **Zakres dat i godzin**
   - **Działania**: upewnij się **, że jest zaznaczona opcja Pokaż wyniki dla wszystkich** działań.

   Po zakończeniu kliknij pozycję **Wyszukaj**.

3. Kliknij **kolumnę Działanie** , aby posortować wyniki i odszukaj pozycję **Zgoda na aplikację**.

4. Wybierz pozycję z listy, aby wyświetlić szczegóły działania. Sprawdź, czy wartość IsAdminContent ma ustawioną wartość True (Prawda).

> [!NOTE]
>
> Może upłynieć od 30 minut do 24 godzin, aby wpis dziennika inspekcji został wyświetlony w wynikach wyszukiwania po zdarzeniu.
>
> Czas zachowywania i przeszukiwania rekordu inspekcji w dzienniku inspekcji zależy od subskrypcji usługi Microsoft 365, a w szczególności od typu licencji przypisanej do określonego użytkownika. Aby uzyskać więcej informacji, zobacz [Dziennik inspekcji](../../compliance/search-the-audit-log-in-security-and-compliance.md).
>
> Jeśli ta wartość jest prawdziwa, oznacza to, że osoba z uprawnieniami administratora globalnego może udzieliła szerokiego dostępu do danych. Jeśli jest to nieoczekiwane, należy podjąć kroki [w celu potwierdzenia ataków](#how-to-confirm-an-attack).

## <a name="how-to-confirm-an-attack"></a>Jak potwierdzić atak

Jeśli masz co najmniej jedno wystąpienie wymienionych powyżej zdarzeń IOCs, musisz wykonać dalsze badanie w celu pozytywnego potwierdzenia, że wystąpił atak. Możesz użyć dowolnej z tych trzech metod, aby potwierdzić atak:

- Spis aplikacji i ich uprawnień przy użyciu portalu Azure Active Directory sieci Web. Ta metoda jest dokładna, ale można sprawdzać tylko jednego użytkownika jednocześnie, co może być bardzo czasochłonne, jeśli masz wielu użytkowników do sprawdzenia.
- Spis aplikacji i ich uprawnień przy użyciu programu PowerShell. Jest to najszybsza i najbardziej dokładna metoda przy jak najmniejszym narzucie.
- Zachęć użytkowników, aby indywidualnie sprawdzali swoje aplikacje i uprawnienia i zgłaszali wyniki z powrotem administratorom w celu ich rozwiązania.

## <a name="inventory-apps-with-access-in-your-organization"></a>Spis aplikacji z dostępem w Twojej organizacji

Możesz to zrobić dla użytkowników za pomocą portalu Azure Active Directory lub programu PowerShell albo z jednego wyliczenia dostępu do aplikacji przez twoich użytkowników.

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Procedura korzystania z portalu Azure Active Directory a

Aplikacje, do których każdy użytkownik udzielił uprawnień, możesz sprawdzić, korzystając z portalu Azure Active Directory witryny <https://portal.azure.com>.

1. Zaloguj się do portalu Azure Portal z prawami administracyjnymi.
2. Wybierz grot Azure Active Directory grota.
3. Wybierz pozycję **Użytkownicy**.
4. Wybierz użytkownika, którego chcesz przejrzeć.
5. Wybierz pozycję **Aplikacje**.

Spowoduje to pokazanie aplikacji przypisanych do użytkownika oraz uprawnień, jakie mają te aplikacje.

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>Procedura wyliczania dostępu do aplikacji przez użytkowników

Niech Twoi użytkownicy będą tam mieli dostęp <https://myapps.microsoft.com> do swoich aplikacji i mogą je przejrzeć. Powinny mieć możliwość wyświetlania wszystkich aplikacji z dostępem, wyświetlania szczegółów dotyczących tych aplikacji (w tym zakresu dostępu) oraz odwoływania uprawnień podejrzanych lub podejrzanych aplikacji.

### <a name="steps-for-doing-this-with-powershell"></a>Procedura wykonywania tej czynności przy użyciu programu PowerShell

Najprostszym sposobem zweryfikowania ataków na udzielenie zgody w celu udzielenia zgody jest uruchomienie programu [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09), co spowoduje ponowne zrzucie wszystkich uprawnień protokołu OAuth oraz aplikacji OAuth dla wszystkich użytkowników w ramach umowy odpowiedzialności w jednym .csv pliku.

#### <a name="pre-requisites"></a>Wymagania wstępne

- Zainstalowano bibliotekę programu PowerShell usługi Azure AD.
- Prawa administratora globalnego dzierżawy, dla których zostanie uruchomiony skrypt.
- Administrator lokalny na komputerze, z którego będą uruchamiane skrypty.

> [!IMPORTANT]
> Zdecydowanie ***zalecamy wymaganie*** uwierzytelniania wieloskładnikowego na koncie administracyjnym. Ten skrypt obsługuje uwierzytelnianie uwierzytelniania MFA.

1. Zaloguj się na komputerze, z których zostanie uruchomiony skrypt, z uprawnieniami administratora lokalnego.

2. Pobierz lub skopiuj [ skryptGet-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09) z GitHub do folderu, z którego zostanie uruchomiony skrypt. Będzie to ten sam folder, w którym zostanie zapisany plik wyjściowy "permissions.csv".

3. Otwórz sesję programu PowerShell jako administrator i otwórz folder, w którym zapisano skrypt.

4. Połączenie do katalogu za pomocą polecenia [cmdlet Połączenie-AzureAD](/powershell/module/azuread/connect-azuread).

5. Uruchom to polecenie programu PowerShell:

   ```powershell
   .\Get-AzureADPSPermissions.ps1 | Export-csv -Path "Permissions.csv" -NoTypeInformation
   ```

Skrypt tworzy jeden plik o nazwie Permissions.csv. Wykonaj poniższe czynności, aby poszukać niedozwolonych uprawnień aplikacji:

1. W kolumnie ConsentType (kolumna G) wyszukaj wartość "AllPrinciples". Uprawnienie AllPrincipals (Wszystkie kapipaly) umożliwia aplikacji klienckiej dostęp do zawartości wszystkich osób w tym waty. Aby Microsoft 365 natywne aplikacje muszą mieć to uprawnienie. Wszystkie aplikacje inne niż firmy Microsoft z tym uprawnieniem powinny być dokładnie przeglądane.

2. W kolumnie Uprawnienie (kolumna F) sprawdź uprawnienia, które każda aplikacja delegowana ma do zawartości. Odszukaj uprawnienia "Odczyt" i "Zapis" lub "*. Wszystkie" i przejrzyj je uważnie, ponieważ mogą być one nieumyślne.

3. Przejrzyj użytkowników, którzy mają udzielone zgody. Jeśli użytkownicy o wysokim profilu lub w dużym wpływie mają udzielone nieodpowiednie zgody, należy dokładniej zbadać problem.

4. W kolumnie ClientDisplayName (kolumna C) poszukaj aplikacji, które wyglądają podejrzanie. Aplikacje z błędnie napisanymi nazwami, nazwami super-bland lub nazwami hakerów powinny być dokładnie przeglądane.

## <a name="determine-the-scope-of-the-attack"></a>Określanie zakresu ataków

Po zakończeniu inwentaryzacji dostępu do aplikacji przejrzyj **dziennik** inspekcji, aby ustalić pełny zakres naruszenia. Wyszukaj użytkowników, których dotyczy problem, ramki czasowe, do których dostęp miała aplikacja szukąca, i uprawnienia, które ta aplikacja miała. Dziennik inspekcji można **przeszukiwać** w portalu [Microsoft 365 Defender sieci.](../../compliance/search-the-audit-log-in-security-and-compliance.md)

> [!IMPORTANT]
> [Inspekcja skrzynek](../../compliance/enable-mailbox-auditing.md) pocztowych i [inspekcja działań dla administratorów](../../compliance/turn-audit-log-search-on-or-off.md) i użytkowników muszą zostać włączone przed atakiem w celu uzyskania tych informacji.

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant-attack"></a>Jak zatrzymać i rozwiązać ataki ze zgodą użytkownika.

Po zidentyfikowaniu aplikacji, która ma uprawnienia, można usunąć ten dostęp na kilka sposobów.

- Możesz cofnąć uprawnienia aplikacji w portalu Azure Active Directory w:
  1. Przejdź do użytkownika, u którego został Azure Active Directory **blade.**
  2. Wybierz pozycję **Aplikacje**.
  3. Wybierz aplikację schłodną.
  4. Kliknij **pozycję Usuń** w menu przechodzenia do szczegółów.

- Możesz odwołać udzielenie zgody protokołu OAuth w programie PowerShell, wykonać czynności opisane w te sposób: [Remove-AzureADOAuth2PermissionGrant](/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant).

- Można odwołać przypisanie roli aplikacji usługi za pomocą programu PowerShell, korzystając z procedury opisanej w te sposób: [Remove-AzureADServiceAppRoleAssignment](/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment).

- Możesz również całkowicie wyłączyć logowanie dla konta, którego dotyczy problem, co z kolei spowoduje wyłączenie dostępu aplikacji do danych na tym koncie. Oczywiście nie jest to idealne rozwiązanie dla wydajności pracy użytkownika końcowego, ale jeśli pracujesz nad krótkim ograniczeniem czasu, może to być rentowne i długoterminowe rozwiązanie.

- Zintegrowane aplikacje można wyłączyć dla swojego wywalanych przez ciebie usług. Jest to znacząco zmiana, która uniemożliwi użytkownikom końcowy udzielenie zgody na udzielenie zgody dla całej dzierżawy. Zapobiega to przypadkowemu przyznaniu użytkownikom dostępu do złośliwej aplikacji. Nie jest to stanowczo zalecane, ponieważ znacznie utrudni użytkownikom wydajną pracę z aplikacjami innych firm. Możesz to zrobić, robiąc tak: włączanie i wyłączanie zintegrowanych [aplikacji](../../admin/misc/user-consent.md).

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Zabezpieczanie Microsoft 365 jak najbezpieczniejsi

Subskrypcja Microsoft 365 jest wyposażona w zaawansowany zestaw funkcji zabezpieczeń, za pomocą których można chronić dane i użytkowników. Korzystaj z planu Microsoft 365 zabezpieczeń — najważniejsze priorytety w ciągu pierwszych [30, 90](security-roadmap.md) dni i nie tylko, aby wdrożyć zalecane przez firmę Microsoft najważniejsze wskazówki dotyczące zabezpieczania Microsoft 365 dzierżawy.

- Zadania, które można wykonać w ciągu pierwszych 30 dni. Mają one natychmiastowy wpływ i mają niski wpływ na twoich użytkowników.
- Zadania, które można wykonać w ciągu 90 dni. Planowanie i implementacja tych aplikacji trwa nieco dłużej, ale znacznie poprawia twoje działania w zakresie zabezpieczeń.
- Dłużej niż 90 dni. Te ulepszenia działają w ciągu pierwszych 90 dni.

## <a name="see-also"></a>Zobacz też

- [Nieoczekiwana aplikacja na liście aplikacji](/azure/active-directory/application-access-unexpected-application) przechodzi administratorów przez różne działania, które mogą chcieć podjąć, gdy uświadomią sobie, że istnieją nieoczekiwane aplikacje mające dostęp do danych.
- [Integrowanie aplikacji z usługą Azure Active Directory](/azure/active-directory/active-directory-apps-permissions-consent) to ogólne omówienie uprawnień i zgody.
- [Problemy podczas opracowywania aplikacji udostępnia](/azure/active-directory/active-directory-application-dev-development-content-map) linki do różnych artykułów powiązanych ze zgodą.
- Obiekty główne aplikacji i usług w usłudze [Azure Active Directory (Azure AD)](/azure/active-directory/develop/active-directory-application-objects) zawiera omówienie podstawowych obiektów aplikacji i usługi w modelu aplikacji.
- [Zarządzanie dostępem do aplikacji](/azure/active-directory/active-directory-managing-access-to-apps) zawiera omówienie funkcji, które administratorzy muszą zarządzać dostępem użytkowników do aplikacji.
