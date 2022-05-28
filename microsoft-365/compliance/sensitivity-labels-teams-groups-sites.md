---
title: Używanie etykiet poufności z witrynami Microsoft Teams, Grupy Microsoft 365 i SharePoint
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkSPO
search.appverid:
- MOE150
- MET150
description: Użyj etykiet poufności, aby chronić zawartość w witrynach SharePoint i Microsoft Teams oraz w grupach Microsoft 365.
ms.openlocfilehash: 125be09f9d3d9a519e1985a37c0880e3f2465245
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772688"
---
# <a name="use-sensitivity-labels-to-protect-content-in-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Używanie etykiet poufności do ochrony zawartości w witrynach Microsoft Teams, Microsoft 365 i SharePoint

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Oprócz używania [etykiet poufności](sensitivity-labels.md) do klasyfikowania i ochrony dokumentów i wiadomości e-mail można również używać etykiet poufności do ochrony zawartości w następujących kontenerach: Microsoft Teams witrynach, grupach Microsoft 365 ([dawniej Office 365 grupach](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) i witrynach SharePoint. W przypadku tej klasyfikacji i ochrony na poziomie kontenera użyj następujących ustawień etykiety:

- Prywatność (publiczna lub prywatna) witryn zespołów i grup Microsoft 365
- Dostęp użytkowników zewnętrznych
- Udostępnianie zewnętrzne z witryn SharePoint
- Dostęp z urządzeń niezarządzanych
- Konteksty uwierzytelniania (w wersji zapoznawczej)
- Domyślny link do udostępniania witryny SharePoint (konfiguracja tylko programu PowerShell)
- W wersji zapoznawczej: ustawienia udostępniania witryn (konfiguracja tylko programu PowerShell)

> [!IMPORTANT]
> Ustawienia urządzeń niezarządzanych i kontekstów uwierzytelniania działają w połączeniu z dostępem warunkowym Azure Active Directory. Należy skonfigurować tę funkcję zależną, jeśli chcesz użyć etykiety poufności dla tych ustawień. Dodatkowe informacje znajdują się w poniższych instrukcjach.

Po zastosowaniu tej etykiety poufności do obsługiwanego kontenera etykieta automatycznie stosuje klasyfikację i skonfigurowane ustawienia ochrony do lokacji lub grupy.

Zawartość w tych kontenerach nie dziedziczy jednak etykiet klasyfikacji ani ustawień plików i wiadomości e-mail, takich jak oznaczenia wizualne i szyfrowanie. Aby umożliwić użytkownikom etykietowanie dokumentów w witrynach SharePoint lub witrynach zespołu, upewnij się, że [włączono etykiety poufności dla Office plików w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="using-sensitivity-labels-for-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Używanie etykiet poufności dla Microsoft Teams, grup Microsoft 365 i witryn SharePoint

Przed włączeniem etykiet poufności dla kontenerów i skonfigurowaniem etykiet poufności dla nowych ustawień użytkownicy mogą wyświetlać i stosować etykiety poufności w swoich aplikacjach. Na przykład z programu Word:

![Etykieta poufności wyświetlana w aplikacji klasycznej programu Word.](../media/sensitivity-label-word.png)

Po włączeniu i skonfigurowaniu etykiet poufności dla kontenerów użytkownicy mogą dodatkowo wyświetlać i stosować etykiety poufności do witryn zespołu firmy Microsoft, grup Microsoft 365 i witryn SharePoint. Na przykład podczas tworzenia nowej witryny zespołu z SharePoint:

![Etykieta poufności podczas tworzenia witryny zespołu z SharePoint.](../media/sensitivity-labels-new-team-site.png)

> [!NOTE]
> Etykiety poufności dla kontenerów obsługują [Teams kanałów udostępnionych](/MicrosoftTeams/shared-channels), obecnie w wersji zapoznawczej. Jeśli zespół ma jakiekolwiek kanały udostępnione, automatycznie dziedziczy ustawienia etykiet poufności po swoim zespole nadrzędnym, a etykiety nie można usunąć ani zastąpić inną etykietą.

## <a name="how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels"></a>Jak włączyć etykiety poufności dla kontenerów i synchronizować etykiety

Jeśli nie włączono jeszcze etykiet poufności dla kontenerów, wykonaj następujący zestaw kroków jako jednorazową procedurę:

1. Ponieważ ta funkcja korzysta z funkcji Azure AD, postępuj zgodnie z instrukcjami z dokumentacji Azure AD, aby włączyć obsługę etykiet poufności: [Przypisz etykiety poufności do grup Microsoft 365 w Azure Active Directory](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels).

2. Teraz musisz zsynchronizować etykiety poufności z Azure AD. Najpierw [połącz się z programem PowerShell Security & Compliance Center](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   Na przykład w sesji programu PowerShell uruchamianej jako administrator zaloguj się przy użyciu konta administratora globalnego.

3. Następnie uruchom następujące polecenie, aby upewnić się, że etykiety poufności mogą być używane z grupami Microsoft 365:

    ```powershell
    Execute-AzureAdLabelSync
    ```

## <a name="how-to-configure-groups-and-site-settings"></a>Jak skonfigurować grupy i ustawienia witryny

Po włączeniu etykiet poufności dla kontenerów zgodnie z opisem w poprzedniej sekcji można skonfigurować ustawienia ochrony dla grup i lokacji w konfiguracji etykietowania poufności. Dopóki etykiety poufności nie zostaną włączone dla kontenerów, ustawienia będą widoczne, ale nie można ich skonfigurować.

1. Postępuj zgodnie z ogólnymi instrukcjami, aby [utworzyć lub edytować etykietę poufności](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) i upewnij się, że wybrano pozycję **Grupy & lokacje** dla zakresu etykiety: 
    
    ![Opcje zakresu etykiet poufności dla plików i wiadomości e-mail.](../media/groupsandsites-scope-options-sensitivity-label.png)
    
    Jeśli tylko ten zakres jest wybrany dla etykiety, etykieta nie będzie wyświetlana w aplikacjach Office obsługujące etykiety poufności i których nie można zastosować do plików i wiadomości e-mail. Rozdzielenie etykiet może być przydatne zarówno dla użytkowników, jak i administratorów, ale może również zwiększać złożoność wdrażania etykiet.
    
    Na przykład należy dokładnie przejrzeć [kolejność etykiet](sensitivity-labels.md#label-priority-order-matters), ponieważ SharePoint wykrywa, kiedy dokument z etykietą jest przekazywany do witryny z etykietą. W tym scenariuszu zdarzenie inspekcji i wiadomość e-mail są generowane automatycznie, gdy dokument ma etykietę poufności o wyższym priorytecie niż etykieta witryny. Aby uzyskać więcej informacji, zobacz sekcję [Auditing sensitivity label activities (Inspekcja działań etykiet poufności](#auditing-sensitivity-label-activities) ) na tej stronie. 

2. Następnie na stronie **Definiowanie ustawień ochrony dla grup i witryn** wybierz jedną lub obie dostępne opcje:
    
    - **Ustawienia prywatności i dostępu użytkowników zewnętrznych** w celu skonfigurowania ustawień dostępu **prywatność** i **użytkownicy zewnętrzni** . 
    - **Ustawienia udostępniania zewnętrznego i dostępu warunkowego** w celu skonfigurowania **zewnętrznego udostępniania kontrolki z oznaczonych etykietami witryn SharePoint** i **używania dostępu warunkowego Azure AD w celu ochrony oznaczonych etykietami SharePoint lokacji**.

3. Jeśli wybrano **ustawienia prywatności i dostępu użytkowników zewnętrznych**, skonfiguruj teraz następujące ustawienia:
    
    - **Prywatność**: zachowaj wartość domyślną **Publiczne** , jeśli chcesz, aby ktokolwiek w organizacji miał dostęp do witryny zespołu lub grupy, w której zastosowano tę etykietę.
        
        Wybierz pozycję **Prywatny** , jeśli chcesz, aby dostęp był ograniczony tylko do zatwierdzonych członków w organizacji.
        
        Wybierz pozycję **Brak** , jeśli chcesz chronić zawartość w kontenerze przy użyciu etykiety poufności, ale nadal zezwalaj użytkownikom na samodzielne konfigurowanie ustawienia prywatności.
        
        Ustawienia **zestawu publicznego** lub **prywatnego** i blokują ustawienie prywatności po zastosowaniu tej etykiety do kontenera. Wybrane ustawienie zastępuje wszystkie poprzednie ustawienia prywatności, które mogą być skonfigurowane dla zespołu lub grupy, i blokuje wartość prywatności, aby można je było zmienić tylko przez usunięcie etykiety poufności z kontenera. Po usunięciu etykiety poufności ustawienie prywatności z etykiety pozostaje i użytkownicy mogą teraz zmienić ją ponownie.
    
    - **Dostęp użytkowników zewnętrznych**: określ, czy właściciel grupy może [dodawać gości do grupy](/office365/admin/create-groups/manage-guest-access-in-groups).

4. Jeśli wybrano **ustawienia udostępniania zewnętrznego i dostępu warunkowego**, skonfiguruj teraz następujące ustawienia:
    
    - **Kontrolowanie udostępniania zewnętrznego z witryn z etykietami SharePoint**: wybierz tę opcję, aby wybrać udostępnianie zewnętrzne dla wszystkich osób, nowych i istniejących gości, istniejących gości lub tylko osób w organizacji. Aby uzyskać więcej informacji na temat tej konfiguracji i ustawień, zobacz dokumentację SharePoint [Włączanie i wyłączanie udostępniania zewnętrznego dla witryny](/sharepoint/change-external-sharing-site).
    
    - **Użyj Azure AD dostępu warunkowego, aby chronić witryny z etykietami SharePoint**: wybierz tę opcję tylko wtedy, gdy twoja organizacja została skonfigurowana i korzysta z [Azure Active Directory dostępu warunkowego](/azure/active-directory/conditional-access/overview). Następnie wybierz jedno z następujących ustawień:
    
        - **Określ, czy użytkownicy mogą uzyskiwać dostęp do witryn SharePoint z urządzeń niezarządzanych**: ta opcja używa funkcji SharePoint, która używa dostępu warunkowego Azure AD do blokowania lub ograniczania dostępu do zawartości SharePoint i OneDrive z urządzeń niezarządzanych. Aby uzyskać więcej informacji, zobacz [Kontrolowanie dostępu z urządzeń niezarządzanych](/sharepoint/control-access-from-unmanaged-devices) z dokumentacji SharePoint. Opcja określona dla tego ustawienia etykiety jest odpowiednikiem uruchamiania polecenia programu PowerShell dla lokacji, zgodnie z opisem w krokach 3–5 z sekcji [Blokuj lub ogranicz dostęp do określonej witryny SharePoint lub OneDrive](/sharepoint/control-access-from-unmanaged-devices#block-or-limit-access-to-a-specific-sharepoint-site-or-onedrive) z instrukcji SharePoint.
            
            Aby uzyskać dodatkowe informacje o konfiguracji, zobacz [Więcej informacji o zależnościach dla opcji urządzeń niezarządzanych](#more-information-about-the-dependencies-for-the-unmanaged-devices-option) na końcu tej sekcji.
            
        - **Wybierz istniejący kontekst uwierzytelniania**: obecnie w wersji zapoznawczej ta opcja umożliwia wymuszanie bardziej rygorystycznych warunków dostępu, gdy użytkownicy uzyskują dostęp do SharePoint witryn, w których zastosowano tę etykietę. Te warunki są wymuszane po wybraniu istniejącego kontekstu uwierzytelniania, który został utworzony i opublikowany dla wdrożenia dostępu warunkowego w organizacji. Jeśli użytkownicy nie spełniają skonfigurowanych warunków lub używają aplikacji, które nie obsługują kontekstów uwierzytelniania, odmawia im dostępu.
            
            Aby uzyskać dodatkowe informacje o konfiguracji, zobacz [Więcej informacji o zależnościach dla opcji kontekstu uwierzytelniania](#more-information-about-the-dependencies-for-the-authentication-context-option) na końcu tej sekcji.
            
            Przykłady dla tej konfiguracji etykiety:
            
             - Należy wybrać kontekst uwierzytelniania skonfigurowany do wymagania [uwierzytelniania wieloskładnikowego (MFA).](/azure/active-directory/conditional-access/untrusted-networks) Etykieta ta jest następnie stosowana do witryny SharePoint zawierającej wysoce poufne elementy. W związku z tym, gdy użytkownicy z niezaufanej sieci próbują uzyskać dostęp do dokumentu w tej witrynie, widzą monit uwierzytelniania wieloskładnikowego o ukończenie, zanim będą mogli uzyskać dostęp do dokumentu.
             
             - Należy wybrać kontekst uwierzytelniania skonfigurowany dla [zasad warunków użytkowania (ToU](/azure/active-directory/conditional-access/terms-of-use)). Etykieta ta jest następnie stosowana do witryny SharePoint zawierającej elementy, które wymagają akceptacji warunków użytkowania ze względów prawnych lub zgodności. W związku z tym, gdy użytkownicy próbują uzyskać dostęp do dokumentu w tej witrynie, widzą dokument warunków użytkowania, który muszą zaakceptować, zanim będą mogli uzyskać dostęp do oryginalnego dokumentu.

> [!IMPORTANT]
> Tylko te ustawienia witryny i grupy obowiązują po zastosowaniu etykiety do zespołu, grupy lub witryny. Jeśli [zakres etykiety](sensitivity-labels.md#label-scopes) obejmuje pliki i wiadomości e-mail, inne ustawienia etykiet, takie jak szyfrowanie i oznaczanie zawartości, nie są stosowane do zawartości w zespole, grupie lub witrynie.

Jeśli etykieta poufności nie została jeszcze opublikowana, opublikuj [ją, dodając ją do zasad etykiet poufności](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy). Użytkownicy, którzy mają przypisane zasady etykiet poufności zawierające tę etykietę, będą mogli wybrać ją dla witryn i grup.

##### <a name="more-information-about-the-dependencies-for-the-unmanaged-devices-option"></a>Więcej informacji o zależnościach dla opcji urządzeń niezarządzanych

Jeśli nie skonfigurujesz zasad dostępu warunkowego zależnego dla SharePoint zgodnie z dokumentem w [temacie Korzystanie z ograniczeń wymuszonych przez aplikację](/sharepoint/app-enforced-restrictions), opcja określona w tym miejscu nie będzie miała żadnego wpływu. Ponadto nie będzie to miało wpływu, jeśli jest mniej restrykcyjne niż skonfigurowane ustawienie na poziomie dzierżawy. Jeśli skonfigurowano ustawienie dla całej organizacji dla urządzeń niezarządzanych, wybierz ustawienie etykiety, które jest takie samo lub bardziej restrykcyjne

Jeśli na przykład dzierżawa jest skonfigurowana pod kątem **zezwalania na ograniczony dostęp tylko do Sieci Web**, ustawienie etykiety, które zezwala na pełny dostęp, nie będzie miało wpływu, ponieważ jest mniej restrykcyjne. W przypadku tego ustawienia na poziomie dzierżawy wybierz ustawienie etykiety, aby zablokować dostęp (bardziej restrykcyjne) lub ustawienie etykiety dla ograniczonego dostępu (takie samo jak ustawienie dzierżawy).

Ponieważ można skonfigurować ustawienia SharePoint niezależnie od konfiguracji etykiety, nie ma kontroli konfiguracji etykiet poufności, że zależności są w miejscu. Te zależności można skonfigurować po utworzeniu i opublikowaniu etykiety, a nawet po zastosowaniu etykiety. Jeśli jednak etykieta jest już zastosowana, ustawienie etykiety zostanie zastosowane dopiero po następnym uwierzytelnieniu użytkownika.

##### <a name="more-information-about-the-dependencies-for-the-authentication-context-option"></a>Więcej informacji o zależnościach dla opcji kontekstu uwierzytelniania

Aby można było wyświetlić konteksty uwierzytelniania na liście rozwijanej do wyboru, należy utworzyć, skonfigurować i opublikować konteksty uwierzytelniania w ramach konfiguracji dostępu do warunku Azure Active Directory. Aby uzyskać więcej informacji i instrukcji, zobacz sekcję [Konfigurowanie kontekstów uwierzytelniania](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#configure-authentication-contexts) w dokumentacji Azure AD dostępu warunkowego.

Nie wszystkie aplikacje obsługują konteksty uwierzytelniania. Jeśli użytkownik z nieobsługiwaną aplikacją nawiąże połączenie z witryną skonfigurowaną pod kątem kontekstu uwierzytelniania, zobaczy komunikat o odmowie dostępu lub zostanie wyświetlony monit o uwierzytelnienie, ale odrzucony. Aplikacje, które obecnie obsługują konteksty uwierzytelniania:

- Office dla sieci web, w tym Outlook dla sieci Web

- Microsoft Teams dla Windows i macOS (z wyłączeniem aplikacji internetowej Teams)

- Microsoft Planner

- Aplikacje Microsoft 365 dla programu Word, Excel i PowerPoint; wersje minimalne:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 2.48.303
    - Android: 16.0.13924.10000

- Aplikacje Microsoft 365 dla Outlook; minimalne wersje:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 4.2109.0
    - Android: 4.2025.1

- synchronizacja usługi OneDrive aplikacji, minimalne wersje:
    - Windows: 21.002
    - macOS: 21.002
    - iOS: Wprowadzenie w wersji 12.30
    - Android: jeszcze nieobsługiwane

Znane ograniczenia dotyczące tej wersji zapoznawczej:

- W przypadku aplikacji synchronizacja usługi OneDrive jest ona obsługiwana tylko dla OneDrive, a nie dla innych witryn.

- Następujące funkcje i aplikacje mogą być niezgodne z kontekstami uwierzytelniania, dlatego zachęcamy do sprawdzenia, czy nadal działają po pomyślnym uzyskaniu przez użytkownika dostępu do witryny przy użyciu kontekstu uwierzytelniania:
    
    - Przepływy pracy korzystające z Power Apps lub Power Automate
    - Aplikacje innych firm

### <a name="configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings"></a>Konfigurowanie ustawień domyślnego typu łącza udostępniania witryny przy użyciu ustawień zaawansowanych programu PowerShell

Oprócz ustawień etykiet dla witryn i grup, które można skonfigurować z portal zgodności Microsoft Purview, można również skonfigurować domyślny typ linku udostępniania dla witryny. Etykiety poufności dokumentów można również skonfigurować dla domyślnego typu łącza udostępniania. Te ustawienia, które pomagają zapobiegać nadmiernemu udostępnianiu, są wybierane automatycznie, gdy użytkownicy wybierają przycisk **Udostępnij** w swoich aplikacjach Office. 

Aby uzyskać więcej informacji i instrukcji, zobacz [Używanie etykiet poufności do konfigurowania domyślnego typu linku udostępniania witryn i dokumentów w SharePoint i OneDrive](sensitivity-labels-default-sharing-link.md).

### <a name="configure-site-sharing-permissions-by-using-powershell-advanced-settings"></a>Konfigurowanie uprawnień do udostępniania witryn przy użyciu zaawansowanych ustawień programu PowerShell

> [!NOTE]
> To ustawienie etykiety jest obecnie dostępne w wersji zapoznawczej.

Innym zaawansowanym ustawieniem programu PowerShell, które można skonfigurować w celu zastosowania etykiety poufności do witryny SharePoint, jest **MembersCanShare**. To ustawienie jest równoważną konfiguracją, którą można ustawić z poziomu centrum administracyjnego SharePoint > **uprawnienia do** >  udostępniania **witryn** > **— Zmiana sposobu udostępniania** > **uprawnień udostępniania** przez członków. 

Te trzy opcje są wyświetlane z równoważnymi wartościami dla ustawienia zaawansowanego programu PowerShell **MembersCanShare**:

|Opcja z centrum administracyjnego SharePoint |Równoważna wartość programu PowerShell dla elementu MembersCanShare |
|----------------------------------------|------------------------------------------------|
|**Właściciele i członkowie witryny mogą udostępniać pliki, foldery i witrynę. Osoby z uprawnieniami do edycji mogą udostępniać pliki i foldery.**| MemberShareAll|
|**Właściciele i członkowie witryny oraz osoby z uprawnieniami do edycji mogą udostępniać pliki i foldery, ale tylko właściciele witryn mogą udostępniać witrynę.**|MemberShareFileAndFolder|
|**Tylko właściciele witryn mogą udostępniać pliki, foldery i witrynę.**|MemberShareNone|

Aby uzyskać więcej informacji na temat tych opcji konfiguracji, zobacz [Zmienianie sposobu udostępniania elementów członkowskich](/microsoft-365/community/sharepoint-security-a-team-effort#change-how-members-can-share) z dokumentacji SharePoint społeczności.

Przykład, gdzie identyfikator GUID etykiety poufności to **8faca7b8-8d20-48a3-8ea2-0f96310a848e**:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{MembersCanShare="MemberShareNone"}
````

Aby uzyskać więcej pomocy w określaniu ustawień zaawansowanych programu [PowerShell, zobacz Porady programu PowerShell dotyczące określania ustawień zaawansowanych](sensitivity-labels-default-sharing-link.md#powershell-tips-for-specifying-the-advanced-settings).

## <a name="sensitivity-label-management"></a>Zarządzanie etykietami poufności

Skorzystaj z poniższych wskazówek dotyczących tworzenia, modyfikowania lub usuwania etykiet poufności skonfigurowanych dla witryn i grup.

### <a name="creating-and-publishing-labels-that-are-configured-for-sites-and-groups"></a>Tworzenie i publikowanie etykiet skonfigurowanych dla witryn i grup

Skorzystaj z poniższych wskazówek, aby opublikować etykietę dla użytkowników, gdy etykieta jest skonfigurowana dla ustawień witryny i grupy:

1. Po utworzeniu i skonfigurowaniu etykiety poufności dodaj tę etykietę do zasad etykiet, które dotyczą tylko kilku użytkowników testowych.

2. Zaczekaj na replikację zmiany:
    
   - Nowa etykieta: Poczekaj co najmniej jedną godzinę.
   - Istniejąca etykieta: poczekaj co najmniej 24 godziny.
    
    Aby uzyskać więcej informacji na temat czasu etykiet, zobacz [When to expect new labels and changes to take effect (Kiedy można oczekiwać wprowadzenia nowych etykiet i zmian](create-sensitivity-labels.md#when-to-expect-new-labels-and-changes-to-take-effect)).

3. Po tym okresie oczekiwania użyj jednego z testowych kont użytkowników, aby utworzyć zespół, Microsoft 365 grupę lub SharePoint lokację z etykietą utworzoną w kroku 1.

4. Jeśli podczas tej operacji tworzenia nie występują błędy, wiesz, że publikowanie etykiety dla wszystkich użytkowników w dzierżawie jest bezpieczne.

### <a name="modifying-published-labels-that-are-configured-for-sites-and-groups"></a>Modyfikowanie opublikowanych etykiet skonfigurowanych dla witryn i grup

Najlepszym rozwiązaniem jest nie zmienianie ustawień witryny i grupy etykiety poufności po zastosowaniu etykiety do zespołów, grup lub witryn. Jeśli to zrobisz, pamiętaj, aby poczekać co najmniej 24 godziny na replikowanie zmian do wszystkich kontenerów, które mają zastosowana etykietę.

Ponadto jeśli zmiany obejmują ustawienie **dostępu użytkowników zewnętrznych** :

- Nowe ustawienie dotyczy nowych użytkowników, ale nie do istniejących użytkowników. Jeśli na przykład to ustawienie zostało wcześniej wybrane i w rezultacie użytkownicy-goście uzyskiwali dostęp do witryny, ci użytkownicy-goście nadal mogą uzyskać dostęp do witryny po wyczyszczeniu tego ustawienia w konfiguracji etykiety.

- Ustawienia prywatności właściwości grupy hiddenMembership i roleEnabled nie są aktualizowane.

### <a name="deleting-published-labels-that-are-configured-for-sites-and-groups"></a>Usuwanie opublikowanych etykiet skonfigurowanych dla witryn i grup

Jeśli usuniesz etykietę poufności z włączonymi ustawieniami lokacji i grupy, a etykieta zostanie uwzględniona w co najmniej jednej zasadach etykiet, ta akcja może spowodować błędy tworzenia dla nowych zespołów, grup i witryn. Aby uniknąć tej sytuacji, skorzystaj z następujących wskazówek:

1. Usuń etykietę poufności ze wszystkich zasad etykiet zawierających etykietę.

2. Poczekaj co najmniej jedną godzinę.

3. Po tym okresie oczekiwania spróbuj utworzyć zespół, grupę lub witrynę i upewnij się, że etykieta nie jest już widoczna.

4. Jeśli etykieta poufności nie jest widoczna, możesz teraz bezpiecznie usunąć etykietę.

## <a name="how-to-apply-sensitivity-labels-to-containers"></a>Jak stosować etykiety poufności do kontenerów

Teraz możesz zastosować etykietę poufności lub etykiety do następujących kontenerów:

- [grupa Microsoft 365 w Azure AD](#apply-sensitivity-labels-to-microsoft-365-groups)
- [witryna zespołu Microsoft Teams](#apply-a-sensitivity-label-to-a-new-team)
- [grupa Microsoft 365 w Outlook w sieci Web](#apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web)
- [witryna SharePoint](#apply-a-sensitivity-label-to-a-new-site)

Jeśli chcesz [zastosować etykietę poufności do wielu lokacji](#use-powershell-to-apply-a-sensitivity-label-to-multiple-sites), możesz użyć programu PowerShell.

### <a name="apply-sensitivity-labels-to-microsoft-365-groups"></a>Stosowanie etykiet poufności do grup Microsoft 365

Teraz możesz przystąpić do stosowania etykiet lub etykiet poufności do Microsoft 365 grup. Wróć do dokumentacji Azure AD, aby uzyskać instrukcje:

- [Przypisz etykietę do nowej grupy w Azure Portal](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-a-new-group-in-azure-portal)

- [Przypisz etykietę do istniejącej grupy w Azure Portal](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-an-existing-group-in-azure-portal)

- [Usuń etykietę z istniejącej grupy w Azure Portal](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#remove-a-label-from-an-existing-group-in-azure-portal).

### <a name="apply-a-sensitivity-label-to-a-new-team"></a>Stosowanie etykiety poufności do nowego zespołu

Użytkownicy mogą wybierać etykiety poufności podczas tworzenia nowych zespołów w Microsoft Teams. Po wybraniu etykiety z listy rozwijanej **Poufność** ustawienie prywatności może ulec zmianie, aby odzwierciedlić konfigurację etykiety. W zależności od ustawienia dostępu użytkowników zewnętrznych wybranego dla etykiety użytkownicy mogą dodawać do zespołu osoby spoza organizacji lub nie mogą ich dodawać.

[Dowiedz się więcej o etykietach poufności dla Teams](/microsoftteams/sensitivity-labels)

![Ustawienie prywatności podczas tworzenia nowego zespołu.](../media/privacy-setting-new-team.png)

Po utworzeniu zespołu etykieta poufności zostanie wyświetlona w prawym górnym rogu wszystkich kanałów.

![Etykieta poufności jest wyświetlana w zespole.](../media/privacy-setting-teams.png)

Usługa automatycznie stosuje tę samą etykietę poufności do grupy Microsoft 365 i połączonej witryny zespołu SharePoint.

### <a name="apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web"></a>Stosowanie etykiety poufności do nowej grupy w Outlook w sieci Web

W Outlook w sieci Web podczas tworzenia nowej grupy można wybrać lub zmienić opcję **Poufności** dla opublikowanych etykiet:

![Tworzenie grupy i wybieranie opcji w obszarze Poufność.](../media/sensitivity-label-new-group.png)

### <a name="apply-a-sensitivity-label-to-a-new-site"></a>Stosowanie etykiety poufności do nowej witryny

Administratorzy i użytkownicy końcowi mogą wybierać etykiety poufności podczas [tworzenia nowoczesnych witryn zespołu i witryn komunikacyjnych](/sharepoint/create-site-collection) oraz rozwijać **ustawienia zaawansowane**:

![Tworzenie witryny i wybieranie opcji w obszarze Poufność.](../media/sensitivity-label-new-communication-site.png)

W polu listy rozwijanej są wyświetlane nazwy etykiet dla zaznaczenia, a ikona pomocy wyświetla wszystkie nazwy etykiet z etykietą narzędzia, co może pomóc użytkownikom określić poprawną etykietę do zastosowania.

Gdy etykieta zostanie zastosowana, a użytkownicy będą przeglądać witrynę, zobaczą nazwę etykiety i zastosowane zasady. Na przykład ta witryna została oznaczona jako **Poufne**, a ustawienie prywatności jest ustawione na **Wartość Prywatna**:

![Witryna z zastosowaną etykietą poufności.](../media/sensitivity-label-site.png)

### <a name="use-powershell-to-apply-a-sensitivity-label-to-multiple-sites"></a>Stosowanie etykiety poufności do wielu lokacji przy użyciu programu PowerShell

Aby zastosować etykietę poufności do wielu witryn, można użyć polecenia cmdlet [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) i [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) z parametrem *SensitivityLabel* z bieżącej [powłoki zarządzania usługi SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online). Witryny mogą być dowolnymi SharePoint zbiorem witryn lub witryną OneDrive.

Upewnij się, że masz wersję 16.0.19418.12000 lub nowszą powłokę zarządzania usługi SharePoint Online.

1. Otwórz sesję programu PowerShell z opcją **Uruchom jako administrator** .

2. Jeśli nie znasz identyfikatora GUID etykiety: [Połączenie do programu PowerShell Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell) i uzyskaj listę etykiet poufności i ich identyfikatorów GUID.

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. Teraz [połącz się z programem SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) i zapisz identyfikator GUID etykiety jako zmienną. Przykład:

   ```powershell
   $Id = [GUID]("e48058ea-98e8-4940-8db0-ba1310fd955e")
   ```

4. Utwórz nową zmienną, która identyfikuje wiele witryn, które mają wspólny ciąg identyfikacyjny w adresie URL. Przykład:

   ```powershell
   $sites = Get-SPOSite -IncludePersonalSite $true -Limit all -Filter "Url -like 'documents"
   ```

5. Uruchom następujące polecenie, aby zastosować etykietę do tych witryn. Korzystając z naszych przykładów:

   ```powershell
   $sites | ForEach-Object {Set-SPOTenant $_.url -SensitivityLabel $Id}
   ```

Ta seria poleceń umożliwia etykietowanie wielu lokacji w dzierżawie przy użyciu tej samej etykiety poufności, dlatego używasz polecenia cmdlet Set-SPOTenant, a nie polecenia cmdlet Set-SPOSite, które jest przeznaczone do konfiguracji poszczególnych lokacji. Jednak użyj polecenia cmdlet Set-SPOSite, gdy musisz zastosować inną etykietę do określonych witryn, powtarzając następujące polecenie dla każdej z tych witryn: `Set-SPOSite -Identity <URL> -SensitivityLabel "<labelguid>"`

## <a name="view-and-manage-sensitivity-labels-in-the-sharepoint-admin-center"></a>Wyświetlanie etykiet poufności i zarządzanie nimi w centrum administracyjnym SharePoint

Aby wyświetlić, posortować i przeszukać zastosowane etykiety poufności, użyj <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**aktywnych witryn**</a> w nowym centrum administracyjnym SharePoint. Może być konieczne najpierw dodanie kolumny **Poufność** :

![Kolumna Poufność na stronie Aktywne witryny.](../media/manage-site-sensitivity-labels.png)

Aby uzyskać więcej informacji na temat zarządzania witrynami ze strony Aktywne witryny, w tym sposobu dodawania kolumny, zobacz [Zarządzanie witrynami w nowym centrum administracyjnym SharePoint](/sharepoint/manage-sites-in-new-admin-center).

Możesz również zmienić i zastosować etykietę z tej strony:

1. Wybierz nazwę witryny, aby otworzyć okienko szczegółów.

2. Wybierz kartę **Zasady** , a następnie wybierz pozycję **Edytuj** dla ustawienia **Czułość** .

3. W okienku **Edytuj ustawienie poufności** wybierz etykietę poufności, którą chcesz zastosować do witryny. W przeciwieństwie do aplikacji użytkowników, w których etykiety poufności można przypisać do określonych użytkowników, centrum administracyjne wyświetla wszystkie etykiety poufności dla dzierżawy. Po wybraniu etykiety wybierz pozycję **Zapisz**.

## <a name="support-for-sensitivity-labels"></a>Obsługa etykiet poufności

W przypadku korzystania z centrów administracyjnych, które obsługują etykiety poufności, z wyjątkiem portalu Azure Active Directory, zobaczysz wszystkie etykiety poufności dla dzierżawy. Dla porównania aplikacje i usługi użytkowników, które filtrują etykiety poufności zgodnie z zasadami publikowania, mogą spowodować wyświetlenie podzbioru tych etykiet. Portal Azure Active Directory filtruje również etykiety zgodnie z zasadami publikowania.

Następujące aplikacje i usługi obsługują etykiety poufności skonfigurowane dla witryn i ustawień grupy:

- centra Administracja:

  - centrum administracyjne programu SharePoint
  - centrum administracyjne Teams
  - Centrum administracyjne platformy Microsoft 365
  - Portal zgodności platformy Microsoft Purview

- Aplikacje i usługi użytkownika:

  - SharePoint
  - Teams
  - Outlook w sieci Web i dla Windows, macOS, iOS i Android
  - Formularzy
  - Stream
  - Planner 

Następujące aplikacje i usługi nie obsługują obecnie etykiet poufności skonfigurowanych dla witryn i ustawień grupy:

- centra Administracja:

  - centrum administracyjne Exchange

- Aplikacje i usługi użytkownika:

  - Dynamics 365
  - Yammer
  - Project
  - Power BI
  - portal Moje aplikacje

## <a name="classic-azure-ad-group-classification"></a>Klasyczna klasyfikacja grup Azure AD

Po włączeniu etykiet poufności dla kontenerów klasyfikacje grup z Azure AD nie są już obsługiwane przez Microsoft 365 i nie będą wyświetlane w witrynach, które obsługują etykiety poufności. Można jednak przekonwertować stare klasyfikacje na etykiety poufności.

Jako przykład użycia starej klasyfikacji grup dla SharePoint zobacz [klasyfikację "nowoczesnych" lokacji SharePoint](/sharepoint/dev/solution-guidance/modern-experience-site-classification).

Te klasyfikacje zostały skonfigurowane przy użyciu Azure AD programu PowerShell lub biblioteki PnP Core i zdefiniowania wartości dla `ClassificationList` tego ustawienia. Jeśli dzierżawa ma zdefiniowane wartości klasyfikacji, są one wyświetlane podczas uruchamiania następującego polecenia z [modułu AzureADPreview programu PowerShell](https://www.powershellgallery.com/packages/AzureADPreview):

```powershell
($setting["ClassificationList"])
```

Aby przekonwertować stare klasyfikacje na etykiety poufności, wykonaj jedną z następujących czynności:

- Użyj istniejących etykiet: określ ustawienia etykiet dla witryn i grup, edytując istniejące etykiety poufności, które zostały już opublikowane.

- Tworzenie nowych etykiet: określ ustawienia etykiet dla witryn i grup, tworząc i publikując nowe etykiety poufności, które mają takie same nazwy jak istniejące klasyfikacje.

Następnie:

1. Użyj programu PowerShell, aby zastosować etykiety poufności do istniejących grup Microsoft 365 i SharePoint lokacji przy użyciu mapowania nazw. Instrukcje można znaleźć w następnej sekcji.

2. Usuń stare klasyfikacje z istniejących grup i lokacji.

Chociaż nie można uniemożliwić użytkownikom tworzenia nowych grup w aplikacjach i usługach, które nie obsługują jeszcze etykiet poufności, można uruchomić cykliczny skrypt programu PowerShell w celu wyszukania nowych grup utworzonych przez użytkowników ze starymi klasyfikacjami i przekonwertowania ich na etykiety poufności.

Aby ułatwić zarządzanie współistnieniem etykiet poufności i klasyfikacji Azure AD dla lokacji i grup, zobacz [Azure Active Directory klasyfikacji i etykiet poufności dla grup Microsoft 365](migrate-aad-classification-sensitivity-labels.md).

### <a name="use-powershell-to-convert-classifications-for-microsoft-365-groups-to-sensitivity-labels"></a>Konwertowanie klasyfikacji grup Microsoft 365 na etykiety poufności przy użyciu programu PowerShell

1. Najpierw [połącz się z programem PowerShell Security & Compliance Center](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   Na przykład w sesji programu PowerShell uruchamianej jako administrator zaloguj się przy użyciu konta administratora globalnego:

2. Pobierz listę etykiet poufności i ich identyfikatorów GUID przy użyciu polecenia cmdlet [Get-Label](/powershell/module/exchange/get-label) :

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. Zanotuj identyfikatory GUID etykiet poufności, które chcesz zastosować do grup Microsoft 365.

4. Teraz [połącz się z programem Exchange Online Programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w osobnym oknie Windows PowerShell.

5. Użyj następującego polecenia jako przykładu, aby uzyskać listę grup, które obecnie mają klasyfikację "Ogólne":

   ```PowerShell
   $Groups= Get-UnifiedGroup | Where {$_.classification -eq "General"}
   ```

6. Dla każdej grupy dodaj nowy identyfikator GUID etykiety poufności. Przykład:

    ```PowerShell
    foreach ($g in $groups)
    {Set-UnifiedGroup -Identity $g.Identity -SensitivityLabelId "457fa763-7c59-461c-b402-ad1ac6b703cc"}
    ```

7. Powtórz kroki 5 i 6 dla pozostałych klasyfikacji grup.

## <a name="auditing-sensitivity-label-activities"></a>Inspekcja działań etykiet poufności

> [!IMPORTANT]
> Jeśli używasz separacji etykiet, wybierając tylko zakres **Grupy & lokacje** dla etykiet, które chronią kontenery: ze względu na wykryte zdarzenie inspekcji **poufności dokumentu** i wiadomość e-mail opisaną w tej sekcji, rozważ [uporządkowanie etykiet](sensitivity-labels.md#label-priority-order-matters) przed etykietami, które mają zakres **dla wiadomości e-mail & plików**. 

Jeśli ktoś przekaże dokument do witryny chronionej etykietą poufności, a jej dokument ma [etykietę poufności o wyższym priorytecie](sensitivity-labels.md#label-priority-order-matters) niż etykieta poufności zastosowana do witryny, ta akcja nie jest zablokowana. Na przykład etykieta **Ogólne** została zastosowana do witryny SharePoint, a ktoś przekazuje do tej witryny dokument z etykietą **Poufne**. Ponieważ etykieta poufności o wyższym priorytecie identyfikuje zawartość o większej poufności niż zawartość o niższym priorytecie, taka sytuacja może stanowić problem z zabezpieczeniami.

Mimo że akcja nie jest zablokowana, jest ona poddana inspekcji i domyślnie automatycznie generuje wiadomość e-mail do osoby, która przekazała dokument, i administratora witryny. W związku z tym zarówno użytkownik, jak i administratorzy mogą identyfikować dokumenty, które mają tę niezgodność priorytetu etykiety, i podejmować działania w razie potrzeby. Na przykład usuń lub przenieś przekazany dokument z witryny.

Nie byłoby to problemem dla zabezpieczeń, gdyby dokument miał etykietę poufności o niższym priorytecie niż etykieta poufności zastosowana do witryny. Na przykład dokument z etykietą **Ogólne** jest przekazywany do witryny z etykietą **Poufne**. W tym scenariuszu zdarzenie inspekcji i wiadomość e-mail nie są generowane.

> [!NOTE]
> Podobnie jak w przypadku opcji zasad, która wymaga od użytkowników podania uzasadnienia zmiany etykiety na niższą klasyfikację, wszystkie etykiety podrzędne dla tej samej etykiety nadrzędnej są uważane za mające ten sam priorytet.

Aby wyszukać w dzienniku inspekcji to zdarzenie, poszukaj **niezgodności poufności wykrytego dokumentu** z kategorii **Działania dotyczące plików i stron** .

Automatycznie wygenerowana wiadomość e-mail zawiera **wykrytą niezgodną etykietę poufności** podmiotu, a wiadomość e-mail wyjaśnia niezgodność etykietowania z linkiem do przekazanego dokumentu i witryny. Zawiera również link do dokumentacji, który wyjaśnia, jak użytkownicy mogą zmieniać etykietę poufności. Tych automatycznych wiadomości e-mail nie można dostosować, ale można uniemożliwić ich wysyłanie podczas korzystania z następującego polecenia programu PowerShell z [polecenia Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant):

```PowerShell
Set-SPOTenant -BlockSendLabelMismatchEmail $True
```

Gdy ktoś dodaje lub usuwa etykietę poufności do lub z witryny lub grupy, działania te są również poddawane inspekcji, ale bez automatycznego generowania wiadomości e-mail.

Wszystkie te zdarzenia inspekcji można znaleźć w kategorii [działania etykiety poufności](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) . Aby uzyskać instrukcje dotyczące przeszukiwania dziennika inspekcji, zobacz [Przeszukiwanie dziennika inspekcji w Centrum zgodności & zabezpieczeń](search-the-audit-log-in-security-and-compliance.md).

## <a name="how-to-disable-sensitivity-labels-for-containers"></a>Jak wyłączyć etykiety poufności dla kontenerów

Etykiety poufności dla Microsoft Teams, grup Microsoft 365 i witryn SharePoint można wyłączyć, korzystając z tych samych instrukcji z sekcji [Włączanie obsługi etykiet poufności w programie PowerShell](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#enable-sensitivity-label-support-in-powershell). Aby jednak wyłączyć tę funkcję, w kroku 5 określ wartość `$setting["EnableMIPLabels"] = "False"`.

Oprócz tego, że wszystkie ustawienia są niedostępne dla grup i witryn podczas tworzenia lub edytowania etykiet poufności, ta akcja przywraca właściwość używaną przez kontenery do ich konfiguracji. Włączenie etykiet poufności dla Microsoft Teams, grup Microsoft 365 i lokacji SharePoint powoduje przełączenie właściwości używanej z **klasyfikacji** (używanej do [klasyfikacji grup Azure AD](#classic-azure-ad-group-classification)) na **poufność**. Po wyłączeniu etykiet poufności dla kontenerów kontenery ignorują właściwość Sensitivity i ponownie używają właściwości Classification.

Oznacza to, że żadne ustawienia etykiet z witryn i grup wcześniej stosowanych do kontenerów nie będą wymuszane, a kontenery nie będą już wyświetlać etykiet.

Jeśli te kontenery mają Azure AD wartości klasyfikacji stosowane do nich, kontenery powrócić do korzystania z klasyfikacji ponownie. Należy pamiętać, że wszystkie nowe witryny lub grupy utworzone po włączeniu funkcji nie będą wyświetlać etykiety ani klasyfikacji. W przypadku tych kontenerów i wszystkich nowych kontenerów można teraz stosować wartości klasyfikacji. Aby uzyskać więcej informacji, zobacz [SharePoint klasyfikację "nowoczesnych" lokacji](/sharepoint/dev/solution-guidance/modern-experience-site-classification) i [Tworzenie klasyfikacji dla grup Office w organizacji](../enterprise/manage-microsoft-365-groups-with-powershell.md).

## <a name="additional-resources"></a>Dodatkowe materiały

Zobacz rejestrowanie seminarium internetowego i odpowiedzi na pytania dotyczące [używania etykiet poufności z witrynami Microsoft Teams, O365 Groups i SharePoint Online](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/using-sensitivity-labels-with-microsoft-teams-o365-groups-and/ba-p/1221885#M1380).

To seminarium internetowe zostało zarejestrowane, gdy funkcja była jeszcze w wersji zapoznawczej, więc można zauważyć pewne rozbieżności w interfejsie użytkownika. Jednak informacje dotyczące tej funkcji są nadal dokładne, a wszelkie nowe możliwości są udokumentowane na tej stronie.

Aby uzyskać więcej informacji na temat zarządzania Teams połączonych witryn i witryn kanałów, zobacz [Zarządzanie Teams połączonych witryn i witryn kanałów](/SharePoint/teams-connected-sites).
