---
title: Konfigurowanie zespołu z izolacją zabezpieczeń przy użyciu unikatowej etykiety poufności
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkCOMPLIANCE
- admindeeplinkSPO
recommendations: false
description: Dowiedz się, jak utworzyć zespół z unikatową etykietą poufności dla zabezpieczeń.
ms.openlocfilehash: 15f155255518df38921288f68dcc9365703e4f2a
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393115"
---
# <a name="configure-a-team-with-security-isolation-by-using-a-unique-sensitivity-label"></a>Konfigurowanie zespołu z izolacją zabezpieczeń przy użyciu unikatowej etykiety poufności

Ten artykuł zawiera zalecenia i kroki konfigurowania prywatnego zespołu w Microsoft Teams i używania unikatowej etykiety poufności do szyfrowania plików, aby tylko członkowie zespołu mogli je odszyfrować.

Poza dostępem prywatnym w tym artykule opisano sposób konfigurowania skojarzonej SharePoint lokacji, do której można uzyskać dostęp z sekcji **Pliki** kanału zespołu, w celu zapewnienia dodatkowych zabezpieczeń wymaganych do przechowywania wysoce regulowanych danych.

Elementy konfiguracji dla zespołu z izolacją zabezpieczeń to:

- Prywatny zespół
- Dodatkowe zabezpieczenia skojarzonej lokacji SharePoint dla zespołu, który:
  - Uniemożliwia członkom witryny udostępnianie witryny innym osobom.
  - Uniemożliwia innym członkom witryny żądanie dostępu do witryny.
- Etykieta poufności przeznaczona specjalnie dla tego zespołu, która:
    - Uniemożliwia dostęp do zawartości SharePoint z urządzeń niezarządzanych
    - Zezwala lub odmawia dostępu gościa do zespołu, w zależności od wymagań
    - Szyfruje dokumenty, do których jest stosowana etykieta

> [!IMPORTANT]
> Przed wykonaniem kroków opisanych w tym artykule upewnij się, że włączono [etykiety poufności w celu ochrony zawartości w Microsoft Teams, grupach Office 365 i witrynach SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

Obejrzyj to wideo, aby zapoznać się z omówieniem procesu wdrażania.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mGHf]

<a name="poster"></a>Aby zapoznać się z 1-stronicowym podsumowaniem tego scenariusza, zobacz [Microsoft Teams z plakatem izolacji zabezpieczeń](../downloads/team-security-isolation-poster.pdf).

[![Microsoft Teams z plakatem izolacji zabezpieczeń.](../media/secure-teams-security-isolation/team-security-isolation-poster.png)](../downloads/team-security-isolation-poster.pdf)

Możesz również pobrać ten plakat w formacie [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/team-security-isolation-poster.pdf) lub [PowerPoint](https://download.microsoft.com/download/8/0/5/8057fc16-c044-40b6-a652-7ed555ba2895/team-security-isolation-poster.pptx) i wydrukować go na papierze letter, legal lub tabloid (11 x 17).

Wypróbuj tę konfigurację we własnym środowisku laboratorium testowego, korzystając z [tych instrukcji](team-security-isolation-dev-test.md).

Zobacz, jak firma Contoso Corporation użyła odizolowanego zespołu do ściśle tajnego projektu w [tej analizie przypadku](contoso-team-for-top-secret-project.md).

## <a name="initial-protections"></a>Początkowe zabezpieczenia

Aby pomóc w ochronie dostępu do zespołu i jego podstawowej witryny SharePoint, zapoznaj się z następującymi najlepszymi rozwiązaniami:
- [Zasady tożsamości i dostępu do urządzeń](../security/office-365-security/identity-access-policies.md)
- [zasady dostępu SharePoint Online](../security/office-365-security/sharepoint-file-access-policies.md)
- [Wdrażanie zespołów z ochroną punktu odniesienia](configure-teams-baseline-protection.md)

## <a name="guest-sharing"></a>Udostępnianie gościa

W zależności od charakteru firmy możesz lub nie chcesz włączać udostępniania gości dla tego zespołu. Jeśli planujesz współpracę z osobami spoza organizacji w zespole, włącz udostępnianie gości. 

Aby uzyskać szczegółowe informacje na temat bezpiecznego udostępniania gościom, zobacz następujące zasoby:

- [Ograniczanie przypadkowego narażenia na pliki podczas udostępniania osobom spoza organizacji](./share-limit-accidental-exposure.md)
- [Tworzenie bezpiecznego środowiska udostępniania gościa](./create-secure-guest-sharing-environment.md)

Aby zezwolić na udostępnianie gościom lub zablokować go, używamy kombinacji etykiety poufności dla zespołu i kontrolek udostępniania na poziomie witryny dla skojarzonej witryny SharePoint, które zostały omówione później.

## <a name="create-a-private-team"></a>Tworzenie zespołu prywatnego

Ponieważ tworzymy etykietę poufności specjalnie dla tego zespołu, następnym krokiem jest utworzenie zespołu. Jeśli masz istniejący zespół, możesz go użyć.

Aby utworzyć zespół na potrzeby informacji poufnych
1. W Teams kliknij **pozycję Teams** po lewej stronie aplikacji, a następnie kliknij **pozycję Dołącz lub utwórz zespół** w dolnej części listy zespołów.
2. Kliknij **pozycję Utwórz zespół** (pierwsza karta, lewy górny róg).
3. Wybierz **pozycję Skompiluj zespół od podstaw**.
4. Na liście **Czułość** zachowaj wartość domyślną.
5. W obszarze **Prywatność** kliknij pozycję **Prywatny**.
6. Wpisz nazwę zespołu, która jest powiązana z twoim poufnym projektem. Na przykład **Project Saturna**.
7. Kliknij **pozycję Utwórz**.
8. Dodaj użytkowników do zespołu, a następnie kliknij przycisk **Zamknij**.

## <a name="private-channel-settings"></a>Ustawienia kanału prywatnego

Zalecamy ograniczenie tworzenia kanałów prywatnych do właścicieli zespołów.

Aby ograniczyć tworzenie kanału prywatnego
1. W zespole kliknij pozycję **Więcej opcji**, a następnie kliknij pozycję **Zarządzaj zespołem**.
2. Na karcie **Ustawienia** rozwiń pozycję **Uprawnienia członka**.
3. Wyczyść pole wyboru **Zezwalaj członkom na tworzenie kanałów prywatnych** .

Zasady [aplikacji Teams](/MicrosoftTeams/teams-policies) umożliwiają również kontrolowanie, kto może tworzyć kanały prywatne.

## <a name="create-a-sensitivity-label"></a>Tworzenie etykiety poufności

Aby skonfigurować zespół do izolacji zabezpieczeń, będziemy używać etykiety poufności utworzonej specjalnie dla tego zespołu. Ta etykieta jest używana na poziomie zespołu do kontrolowania udostępniania gości i blokowania dostępu z urządzeń niezarządzanych. Może również służyć do klasyfikowania i szyfrowania pojedynczych plików w zespole, aby tylko właściciele zespołu i członkowie mogli je otworzyć.

Jeśli masz partnera wewnętrznego lub grupę uczestników projektu, którzy powinni mieć możliwość wyświetlania zaszyfrowanych dokumentów, ale nie ich edytować, możesz dodać je do etykiety z uprawnieniami tylko do wyświetlania. Następnie możesz dodać te osoby do SharePoint witryny zespołu z uprawnieniami czytelnika i będą oni mieli dostęp tylko do odczytu do witryny, w której przechowywane są dokumenty, ale nie do samego zespołu.

Aby utworzyć etykietę poufności

1. Otwórz portal zgodności Microsoft Purview, a następnie w obszarze **Rozwiązania** wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Ochrona informacji**</a>.
1. Kliknij **pozycję Utwórz etykietę**.
1. Nadaj etykiecie nazwę. Sugerujemy nadanie nazwy zespołowi, z którą będziesz go używać.
1. Dodaj nazwę wyświetlaną i opis, a następnie kliknij przycisk **Dalej**.
1. Na **stronie Definiowanie zakresu dla tej etykiety** wybierz pozycję **Pliki & wiadomości e-mail** i **grupy & witrynach** , a następnie kliknij przycisk **Dalej**.
1. Na stronie **Wybieranie ustawień ochrony plików i wiadomości e-mail** wybierz pozycję **Szyfruj pliki i wiadomości e-mail**, a następnie kliknij przycisk **Dalej**.
1. Na stronie **Szyfrowanie** wybierz pozycję **Konfiguruj ustawienia szyfrowania**.
1. Kliknij **pozycję Dodaj użytkowników lub grupy**, wybierz utworzony zespół, a następnie kliknij przycisk **Dodaj**
1. Kliknij **pozycję Wybierz uprawnienia**.
1. Wybierz pozycję **Współautor** z listy rozwijanej, a następnie kliknij przycisk **Zapisz**.
1. Jeśli chcesz dołączyć użytkowników lub grupy z dostępem tylko do odczytu do plików z etykietą:
    1. Kliknij **pozycję Przypisz uprawnienia**.
    1. Kliknij **pozycję Dodaj użytkowników lub grupy**, wybierz użytkowników lub grupy, które chcesz dodać, a następnie kliknij przycisk **Dodaj**.
    1. Kliknij **pozycję Wybierz uprawnienia**.
    1. Wybierz pozycję **Przeglądarka** z listy rozwijanej, a następnie kliknij pozycję **Zapisz**.
13.  Kliknij przycisk **Zapisz**, a następnie kliknij przycisk **Dalej**.
14. Na stronie *Automatyczne etykietowanie plików i wiadomości e-mail** kliknij przycisk **Dalej**.
15. Na stronie **Definiowanie ustawień ochrony dla grup i witryn** wybierz pozycję **Ustawienia prywatności i dostępu użytkowników zewnętrznych** oraz **Ustawienia dostępu urządzeń i udostępniania zewnętrznego** , a następnie kliknij przycisk **Dalej**.
16. Na stronie **Definiowanie ustawień prywatności i dostępu użytkowników zewnętrznych** w obszarze **Prywatność** wybierz opcję **Prywatny** .
17. Jeśli chcesz zezwolić na dostęp gościa, w obszarze **Dostęp użytkowników zewnętrznych** wybierz pozycję **Zezwalaj właścicielom grupy Microsoft 365 dodawanie osób spoza organizacji do grupy jako gości**.
18. Kliknij **Dalej**.
19. Na **stronie Definiowanie ustawień udostępniania zewnętrznego i dostępu do urządzeń** wybierz pozycję **Kontroluj udostępnianie zewnętrzne z witryn z etykietą SharePoint**.
20. W obszarze **Zawartość można udostępniać**, wybierz pozycję **Nowi i istniejący goście** , jeśli zezwalasz na dostęp gościa lub **tylko osoby w organizacji,** jeśli nie.
21. W obszarze **Dostęp z urządzeń niezarządzanych** wybierz pozycję **Blokuj dostęp**.
22. Kliknij **Dalej**.
23. Na stronie **Automatyczne etykietowanie kolumn bazy danych** kliknij przycisk **Dalej**.
24. Kliknij **pozycję Utwórz etykietę**, a następnie kliknij pozycję **Gotowe**.

Po utworzeniu etykiety musisz opublikować ją dla użytkowników, którzy będą z niej korzystać. W takim przypadku udostępnimy etykietę tylko osobom w zespole.

Aby opublikować etykietę poufności:

1. W portal zgodności Microsoft Purview na <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">stronie **Ochrona informacji**</a> wybierz kartę **Zasady etykiet**.
2. Kliknij pozycję **Publikuj etykiety**.
3. Na stronie **Wybieranie etykiet poufności do opublikowania** kliknij pozycję **Wybierz etykiety poufności do opublikowania**.
4. Wybierz utworzoną etykietę, a następnie kliknij przycisk **Dodaj**.
5. Kliknij **Dalej**.
6. Na stronie Publikowanie dla użytkowników i grup kliknij pozycję **Wybierz użytkowników i grupy**.
7. Kliknij **przycisk Dodaj**, a następnie wybierz utworzony zespół.
8. Kliknij **przycisk Dodaj**, a następnie kliknij przycisk **Gotowe**.
9. Kliknij **Dalej**.
10. Na stronie Ustawienia zasad zaznacz pole wyboru **Użytkownicy muszą podać uzasadnienie, aby usunąć etykietę lub niższą etykietę klasyfikacji** , a następnie kliknij przycisk **Dalej**.
11. Wpisz nazwę zasad, a następnie kliknij przycisk **Dalej**.
12. Kliknij pozycję **Prześlij** , a następnie kliknij pozycję **Gotowe**.

## <a name="apply-the-label-to-the-team"></a>Stosowanie etykiety do zespołu

Po opublikowaniu etykiety należy ją zastosować do zespołu, aby ustawienia udostępniania gościa i urządzeń zarządzanych zostały zastosowane. Odbywa się to w centrum administracyjnym SharePoint. Należy pamiętać, że po opublikowaniu etykiety może upłynąć trochę czasu.

Aby zastosować etykietę poufności

1. Otwórz centrum administracyjne SharePoint, a następnie w obszarze **Witryny** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
1. Wybierz witrynę skojarzoną z zespołem.
1. Na karcie **Zasady** w obszarze **Poufność** wybierz pozycję **Edytuj**.
1. Wybierz utworzoną etykietę, a następnie wybierz pozycję **Zapisz**.

## <a name="sharepoint-settings"></a>ustawienia SharePoint

Istnieją trzy kroki do wykonania w SharePoint:

- Zaktualizuj ustawienia udostępniania gościa dla witryny w centrum administracyjnym SharePoint, aby były zgodne z ustawieniami wybranymi podczas tworzenia etykiety, a następnie zaktualizuj domyślny link udostępniania do *pozycji Osoby z istniejącym dostępem*.
- Zaktualizuj ustawienia udostępniania witryn w samej witrynie, aby uniemożliwić członkom udostępnianie plików, folderów lub witryny oraz wyłączanie żądań dostępu.
- Jeśli do etykiety zostały dodane osoby lub grupy z uprawnieniami Przeglądarki, możesz dodać je do witryny SharePoint z uprawnieniami do odczytu.

### <a name="sharepoint-guest-settings"></a>ustawienia gościa SharePoint

Ustawienie udostępniania gościa wybrane podczas tworzenia etykiety (co ma wpływ tylko na członkostwo w zespole) powinno być zgodne z ustawieniami udostępniania gościa dla skojarzonej witryny SharePoint w następujący sposób:

|Ustawienie etykiety|ustawienie witryny SharePoint|
|:------------|:----------------------|
|**Zezwalaj Office 365 właścicielom grup na dodawanie osób spoza organizacji do wybranej grupy**|**Nowi i istniejący goście** (domyślnie dla nowych zespołów)|
|**Zezwalaj Office 365 właścicielom grup na dodawanie osób spoza organizacji do grupy, która nie została wybrana**|**Tylko osoby w organizacji**|

Zaktualizujemy również domyślny typ linku do udostępniania, aby zmniejszyć ryzyko przypadkowego udostępniania plików i folderów szerszemu gronu odbiorców niż planowano.

Aby zaktualizować ustawienia witryny

1. Otwórz centrum administracyjne SharePoint, a następnie w obszarze **Witryny** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>
1. Wybierz witrynę skojarzoną z zespołem.
1. Na karcie **Zasady** w obszarze **Udostępnianie zewnętrzne** wybierz pozycję **Edytuj**.
1. Jeśli zezwolisz na udostępnianie gościa podczas tworzenia etykiety poufnej, upewnij się, że wybrano **pozycję Nowi i istniejący goście** . Jeśli podczas tworzenia etykiety nie zezwalasz na udostępnianie, wybierz pozycję **Tylko osoby w organizacji**.
1. W obszarze Domyślny typ łącza udostępniania wyczyść pole wyboru **To samo co ustawienie na poziomie organizacji** , a następnie wybierz pozycję **Osoby z istniejącym dostępem**.
1. Wybierz **Zapisz**.

#### <a name="private-channels"></a>Kanały prywatne

W przypadku dodawania kanałów prywatnych do zespołu każdy kanał prywatny tworzy nową witrynę SharePoint z domyślnymi ustawieniami udostępniania. Te witryny nie są widoczne w centrum administracyjnym SharePoint, dlatego należy użyć polecenia cmdlet [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) programu PowerShell z następującymi parametrami, aby zaktualizować ustawienia udostępniania gościa:

- `-SharingCapability Disabled` aby wyłączyć udostępnianie gości (domyślnie jest włączone)
- `-DefaultSharingLinkType Internal` aby zmienić domyślny link udostępniania na *Określone osoby*

Jeśli nie planujesz korzystania z kanałów prywatnych z zespołem, rozważ wyłączenie możliwości tworzenia ich przez członków zespołu w obszarze **Uprawnienia członka** w [ustawieniach zespołu](https://support.microsoft.com/office/ce053b04-1b8e-4796-baa8-90dc427b3acc).

### <a name="site-sharing-settings"></a>Ustawienia udostępniania witryny

Aby zapewnić, że witryna SharePoint nie zostanie udostępniona osobom, które nie są członkami zespołu, ograniczamy takie udostępnianie do właścicieli. Ograniczamy również udostępnianie plików i folderów właścicielom zespołów. Dzięki temu właściciele są świadomi, kiedy plik jest udostępniany osobie spoza zespołu.

Aby skonfigurować udostępnianie witryn tylko dla właścicieli
1. W Teams przejdź do karty **Ogólne** zespołu, który chcesz zaktualizować.
2. Na pasku narzędzi dla zespołu kliknij pozycję **Pliki**.
3. Kliknij wielokropek, a następnie kliknij przycisk **Otwórz w SharePoint**.
4. Na pasku narzędzi bazowej witryny SharePoint kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
5. W okienku Uprawnienia witryny w obszarze **Udostępnianie Ustawienia** kliknij pozycję **Zmień ustawienia udostępniania**.
6. W obszarze **Uprawnienia do udostępniania** wybierz pozycję **Tylko właściciele witryn mogą udostępniać pliki, foldery i witrynę,** a następnie kliknij przycisk **Zapisz**.

### <a name="custom-site-permissions"></a>Uprawnienia witryny niestandardowej

Jeśli do etykiety poufności dodano osoby z uprawnieniami przeglądarki, możesz dodać je do witryny SharePoint z dostępem do odczytu, aby umożliwić im łatwy dostęp do plików.

Aby dodać użytkowników do witryny
1. W witrynie kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
2. Kliknij **pozycję Zaproś osoby**, a następnie kliknij pozycję **Udostępnij tylko witrynę**.
3. Wpisz nazwy użytkowników i grup, których chcesz zaprosić.
4. Dla każdej dodanej osoby lub grupy zmień jej uprawnienia z **Edytuj** na **Odczyt**.
5. Wybierz, czy chcesz wysłać im wiadomość e-mail z linkiem do witryny.
6. Kliknij pozycję **Dodaj**.

## <a name="additional-protections"></a>Dodatkowe zabezpieczenia

Microsoft 365 oferuje dodatkowe metody zabezpieczania zawartości. Zastanów się, czy poniższe opcje ułatwią zwiększenie bezpieczeństwa organizacji.

- Niech Goście wyrażą zgodę na [warunki użytkowania](/azure/active-directory/conditional-access/terms-of-use).
- Skonfiguruj [zasady limitu czasu sesji](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) dla gości.
- Utwórz [typy informacji poufnych](../compliance/sensitive-information-type-learn-about.md) i użyj [ochrony przed utratą danych](../compliance/dlp-learn-about-dlp.md) , aby ustawić zasady dotyczące uzyskiwania dostępu do informacji poufnych.
- Używaj Azure Active Directory przeglądów [dostępu](/azure/active-directory/governance/access-reviews-overview), aby okresowo przeglądać dostęp do zespołu i członkostwo.

## <a name="drive-user-adoption-for-team-members"></a>Zwiększanie akceptacji użytkowników dla członków zespołu

Wraz z zespołem nadszedł czas, aby doprowadzić do przyjęcia tego zespołu i jego dodatkowych zabezpieczeń dla członków zespołu.

### <a name="train-your-users"></a>Szkolenie użytkowników

Członkowie zespołu mogą uzyskiwać dostęp do zespołu i wszystkich jego zasobów, w tym czatów, spotkań i innych aplikacji. Podczas pracy z plikami z sekcji **Pliki** kanału członkowie zespołu powinni przypisać etykietę poufności do utworzonych plików.

Gdy etykieta zostanie zastosowana do pliku, zostanie ona zaszyfrowana. Członkowie zespołu mogą go otworzyć i współpracować w czasie rzeczywistym. Jeśli plik opuści witrynę i zostanie przekazany złośliwemu użytkownikowi, będzie musiał podać poświadczenia konta użytkownika należącego do zespołu, aby otworzyć plik i wyświetlić jego zawartość. 

Szkolenie członków zespołu:

- Znaczenie korzystania z nowego zespołu na potrzeby czatów, spotkań, plików i innych zasobów witryny SharePoint oraz konsekwencje wysoce regulowanego wycieku danych, takie jak konsekwencje prawne, grzywny regulacyjne, oprogramowanie wymuszające okup lub utrata przewagi konkurencyjnej.
- Jak uzyskać dostęp do zespołu.
- Jak tworzyć nowe pliki w witrynie i przekazywać nowe pliki przechowywane lokalnie.
- Jak etykietować pliki przy użyciu odpowiedniej etykiety poufności dla zespołu.
- Jak etykieta chroni pliki nawet wtedy, gdy są one wyciekły z witryny.

To szkolenie powinno obejmować ćwiczenia praktyczne, dzięki czemu członkowie zespołu będą mogli korzystać z tych możliwości i ich wyników.

### <a name="conduct-periodic-reviews-of-usage-and-address-team-member-feedback"></a>Przeprowadzanie okresowych przeglądów użycia i opinii członków zespołu adresowego

W tygodniach po treningu:

- Szybko prześlij opinie członków zespołu oraz dostosuj zasady i konfiguracje.
- Przeanalizuj użycie dla zespołu i porównaj je z oczekiwaniami użycia.
- Sprawdź, czy pliki wysoce regulowane zostały prawidłowo oznaczone etykietą poufności. (Możesz zobaczyć, które pliki mają przypisaną etykietę, wyświetlając folder w SharePoint i dodając kolumnę **Poufność** za pomocą opcji **Pokaż/ukryj kolumny** **dodaj kolumnę**.

W razie potrzeby ponownie wytrenuj użytkowników.

## <a name="see-also"></a>Zobacz też

[Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure)
