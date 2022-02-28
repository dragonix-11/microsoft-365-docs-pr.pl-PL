---
title: Konfigurowanie zespołu z izolacji zabezpieczeń
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
recommendations: false
description: Dowiedz się, jak utworzyć zespół z unikatową etykietą wrażliwości w celu zabezpieczenia.
ms.openlocfilehash: 293ac9a1a28757dacba39d30e619ac41be786e04
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990492"
---
# <a name="configure-a-team-with-security-isolation"></a>Konfigurowanie zespołu z izolacji zabezpieczeń

Ten artykuł zawiera zalecenia i procedury konfigurowania prywatnego zespołu w aplikacji Microsoft Teams i używania unikatowej etykiety wrażliwości w celu szyfrowania plików, dzięki czemu tylko członkowie zespołu mogą je odszyfrowywać.

Poza dostępem prywatnym w tym artykule opisano sposób konfigurowania skojarzonej witryny programu SharePoint, do której można uzyskać dostęp z sekcji  Pliki kanału zespołu, na potrzeby dodatkowych zabezpieczeń niezbędnych do przechowywania ściśle uregulowanych danych.

Elementy konfiguracji zespołu z izolacji zabezpieczeń to:

- Zespół prywatny
- Dodatkowe zabezpieczenia skojarzonej SharePoint zespołu, które:
  - Uniemożliwia członkom witryny udostępnianie witryny innym osobom.
  - Uniemożliwia użytkownikom niebędącym członkami witryny żądanie dostępu do witryny.
- Etykieta wrażliwości dla tego zespołu, która:
    - Uniemożliwia dostęp do SharePoint z urządzeń nieza zarządzania
    - Zezwala lub odmawia dostępu gościa do zespołu, w zależności od Twoich wymagań
    - Szyfrowanie dokumentów, do których zastosowano etykietę

> [!IMPORTANT]
> Przed rozpoczęciem czynności opisanej w tym artykule upewnij się[,](../compliance/sensitivity-labels-teams-groups-sites.md) że włączono etykiety wrażliwości w celu ochrony Microsoft Teams w grupach Office 365 i SharePoint sieci Web.

Obejrzyj ten klip wideo, aby uzyskać omówienie procesu wdrażania.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mGHf]

<a name="poster"></a>Aby uzyskać 1-stronowe podsumowanie tego scenariusza, zobacz opis [Microsoft Teams z plakatem izolacji zabezpieczeń](../downloads/team-security-isolation-poster.pdf).

[![Microsoft Teams z plakatem izolacji zabezpieczeń.](../media/secure-teams-security-isolation/team-security-isolation-poster.png)](../downloads/team-security-isolation-poster.pdf)

Możesz również pobrać ten plakat w formacie [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/team-security-isolation-poster.pdf) [PowerPoint](https://download.microsoft.com/download/8/0/5/8057fc16-c044-40b6-a652-7ed555ba2895/team-security-isolation-poster.pptx) formatach i wydrukować go na papierze w formacie letter, legal lub tabloid (11 x 17).

Wypróbuj tę konfigurację we własnym środowisku laboratorium testowym, mając [te instrukcje](team-security-isolation-dev-test.md).

W tej analizie przypadku zobacz, jak firma Contoso Corporation użyła odizolego zespołu w przypadku ściśle tajnego [projektu](contoso-team-for-top-secret-project.md).

## <a name="initial-protections"></a>Ochrona początkowa

Aby chronić dostęp do zespołu i jego źródłowej witryny SharePoint, zapoznaj się z następującymi najlepszymi rozwiązaniami:
- [Zasady dostępu do urządzenia i tożsamości](../security/office-365-security/identity-access-policies.md)
- [SharePoint dostępu do usługi Online](../security/office-365-security/sharepoint-file-access-policies.md)
- [Wdrażanie zespołów z ochroną podstawową](configure-teams-baseline-protection.md)

## <a name="guest-sharing"></a>Udostępnianie gości

W zależności od charakteru firmy możesz zechcieć włączyć udostępnianie gości dla tego zespołu lub nie. Jeśli planujesz współpracować z osobami spoza organizacji w zespole, włącz udostępnianie gości. 

Aby uzyskać szczegółowe informacje na temat bezpiecznego udostępniania gościom, zobacz następujące zasoby:

- [Ograniczanie przypadkowego udostępnienia plików osobom spoza organizacji](./share-limit-accidental-exposure.md)
- [Tworzenie bezpiecznego środowiska udostępniania gości](./create-secure-guest-sharing-environment.md)

Aby umożliwić lub zablokować udostępnianie gości, użyjemy kombinacji etykiety wrażliwości dla zespołu i kontroli udostępniania na poziomie witryny dla skojarzonej SharePoint, co omówiono w dalszej części tego tematu.

## <a name="create-a-private-team"></a>Tworzenie zespołu prywatnego

Ponieważ tworzymy etykietę wrażliwości specjalnie dla tego zespołu, następnym krokiem jest utworzenie zespołu. Jeśli masz istniejący zespół, możesz go użyć.

Aby utworzyć zespół na informacje poufne
1. W Teams kliknij pozycję **Teams** lewej stronie aplikacji, **a** następnie kliknij pozycję Dołącz lub utwórz zespół u dołu listy zespołów.
2. Kliknij **pozycję Utwórz zespół** (pierwsza karta, lewy górny róg).
3. Wybierz **pozycję Stwórz zespół od podstaw**.
4. Na **liście Charakter** zachowaj domyślną wartość.
5. W **obszarze Prywatność** kliknij pozycję **Prywatne**.
6. Wpisz nazwę zespołu związanego z poufnym projektem. Na przykład: **Project Saturn**.
7. Kliknij **przycisk Utwórz**.
8. Dodaj użytkowników do zespołu, a następnie kliknij przycisk **Zamknij**.

## <a name="private-channel-settings"></a>Ustawienia kanału prywatnego

Zalecamy ograniczenie możliwości tworzenia kanałów prywatnych dla właścicieli  zespołu.

Aby ograniczyć tworzenie kanału prywatnego
1. W zespole kliknij pozycję **Więcej opcji**, a następnie kliknij pozycję **Zarządzaj zespołem**.
2. Na karcie **Ustawienia** rozwiń pozycję **Uprawnienia członków**.
3. Wyczyść pole **wyboru Zezwalaj członkom na tworzenie kanałów** prywatnych.

Możesz również używać zasad [zespołów,](/MicrosoftTeams/teams-policies) aby kontrolować, kto może tworzyć kanały prywatne.

## <a name="create-a-sensitivity-label"></a>Tworzenie etykiety wrażliwości

Aby skonfigurować zespół pod względami izolacji zabezpieczeń, będziemy używać etykiety wrażliwości utworzonej specjalnie dla tego zespołu. Ta etykieta jest używana na poziomie zespołu do sterowania udostępnianiem gości i blokowania dostępu przez urządzenia niezakierowane. Może też być używany do klasyfikowania i szyfrowania poszczególnych plików w zespole, aby tylko właściciele i członkowie zespołu je otwierali.

Jeśli masz wewnętrzną grupę partnerów lub uczestników projektu, którzy powinni mieć możliwość wyświetlania zaszyfrowanych dokumentów, ale bez możliwości ich edytowania, możesz dodać je do etykiety z uprawnieniami tylko do wyświetlania. Następnie możesz dodać te osoby do witryny programu SharePoint zespołu z uprawnieniami Czytnik i będą one mieć dostęp tylko do odczytu do witryny, w której są przechowywane dokumenty, ale nie do samego zespołu.

Aby utworzyć etykietę wrażliwości

1. Otwórz Centrum zgodności platformy Microsoft 365 i w **obszarze Rozwiązania** wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Ochrona informacji**</a>.
1. Kliknij **pozycję Utwórz etykietę**.
1. Nadaj etykiecie nazwę. Sugerujemy nadanie nazwy zespołowi, z który będziesz go używać.
1. Dodaj nazwę wyświetlaną i opis, a następnie kliknij przycisk **Dalej**.
1. Na stronie **Definiowanie zakresu tej etykiety wybierz** pozycję Pliki & **e-mail** i grupy **& witryny i** kliknij przycisk **Dalej**.
1. Na stronie **Wybieranie ustawień ochrony dla plików i wiadomości e-mail** wybierz pozycję **Szyfruj pliki** i wiadomości e-mail, a następnie kliknij przycisk **Dalej**.
1. Na stronie **Szyfrowanie** wybierz pozycję **Konfiguruj ustawienia szyfrowania**.
1. Kliknij **pozycję Dodaj użytkowników lub grupy**, wybierz utworzony zespół, a następnie kliknij pozycję **Dodaj.**
1. Kliknij **pozycję Wybierz uprawnienia**.
1. Z **listy rozwijanej wybierz** pozycję Współtworz, a następnie kliknij przycisk **Zapisz**.
1. Jeśli chcesz dodać do etykiety użytkowników lub grupy z dostępem tylko do odczytu do plików:
    1. Kliknij **pozycję Przypisz uprawnienia**.
    1. Kliknij **pozycję Dodaj użytkowników lub grupy**, wybierz użytkowników lub grupy, które chcesz dodać, a następnie kliknij pozycję **Dodaj**.
    1. Kliknij **pozycję Wybierz uprawnienia**.
    1. Z **listy** rozwijanej wybierz pozycję Przeglądarka, a następnie kliknij przycisk **Zapisz**.
13.  Kliknij **przycisk Zapisz**, a następnie kliknij przycisk **Dalej**.
14. Na stronie *Automatyczne oznaczanie plików i wiadomości e-mail** kliknij przycisk **Dalej**.
15. Na stronie **Definiowanie ustawień ochrony dla grup** i witryn wybierz pozycję  Ustawienia prywatności i dostępu użytkowników zewnętrznych oraz Dostęp urządzeń i ustawienia udostępniania **zewnętrznego** i kliknij przycisk **Dalej**.
16. Na stronie **Definiowanie ustawień prywatności i dostępu** użytkowników zewnętrznych w obszarze **Prywatność** **wybierz opcję** Prywatna.
17. Jeśli chcesz zezwolić na dostęp dla gości, w obszarze Dostęp użytkowników zewnętrznych wybierz pozycję Zezwalaj Microsoft 365 właściciele grup dodają do grupy osoby spoza organizacji **jako gości**.
18. Kliknij **Dalej**.
19. Na stronie **Definiowanie ustawień udostępniania zewnętrznego i dostępu do** urządzenia wybierz pozycję Kontroluj **udostępnianie zewnętrzne z SharePoint witryn**.
20. W **obszarze Zawartość może być udostępniana wybierz** pozycję Nowi i istniejący goście, jeśli zezwalasz na dostęp dla **gości, lub** Pozycję Tylko osoby w Twojej organizacji, jeśli nie.
21. W **obszarze Dostęp z urządzeń niezawiązyanych** wybierz **pozycję Blokuj dostęp**.
22. Kliknij **Dalej**.
23. Na stronie **Automatyczne oznaczanie kolumn bazy danych** kliknij przycisk **Dalej**.
24. Kliknij **pozycję Utwórz etykietę**, a następnie kliknij pozycję **Gotowe**.

Po utworzeniu etykiety musisz opublikować ją dla użytkowników, którzy będą jej używać. W tym przypadku etykieta będzie dostępna tylko dla osób w zespole.

Aby opublikować etykietę wrażliwości:

1. W Centrum zgodności platformy Microsoft 365 na stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Ochrona informacji**</a> wybierz **kartę Zasady** etykiet.
2. Kliknij **pozycję Publikuj etykiety**.
3. Na **stronie Wybierz etykiety wrażliwości do opublikowania** kliknij pozycję **Wybierz etykiety wrażliwości do opublikowania**.
4. Zaznacz utworzoną etykietę, a następnie kliknij przycisk **Dodaj**.
5. Kliknij **Dalej**.
6. Na stronie Publikowanie dla użytkowników i grup kliknij pozycję **Wybierz użytkowników i grupy**.
7. Kliknij **pozycję** Dodaj, a następnie wybierz utworzony zespół.
8. Kliknij **przycisk Dodaj**, a następnie kliknij pozycję **Gotowe**.
9. Kliknij **Dalej**.
10. Na stronie Ustawienia zasad zaznacz pole wyboru Użytkownicy muszą podać uzasadnienie, aby usunąć etykietę lub etykietę klasyfikacji o niższej klasyfikacji, **a** następnie kliknij przycisk **Dalej**.
11. Wpisz nazwę zasad, a następnie kliknij przycisk **Dalej**.
12. Kliknij **pozycję Prześlij** , a następnie kliknij pozycję **Gotowe**.

## <a name="apply-the-label-to-the-team"></a>Stosowanie etykiety do zespołu

Po opublikowaniu etykiety musisz ją zastosować do zespołu, aby ustawienia udostępniania gościa i urządzeń zarządzanych zostały wprowadzone. Robi się to w centrum SharePoint administracyjnego. Uwaga: po opublikowaniu etykiety może mi trochę potrwać.

Aby zastosować etykietę wrażliwości
1. Otwórz SharePoint [administracyjnego](https://admin.microsoft.com/sharepoint).
2. W **obszarze Witryny** kliknij pozycję **Aktywne witryny**.
3. Kliknij witrynę skojarzoną z zespołem.
4. Na karcie **Zasady** **w obszarze Charakter** kliknij pozycję **Edytuj**.
5. Zaznacz utworzoną etykietę, a następnie kliknij przycisk **Zapisz**.

## <a name="sharepoint-settings"></a>SharePoint ustawień

W tym celu należy wykonać trzy SharePoint:

- Zaktualizuj ustawienia udostępniania gościa dla witryny w centrum administracyjnym usługi SharePoint, aby dopasować je do ustawień wybranego podczas tworzenia etykiety, i zaktualizuj domyślny link udostępniania do osób z istniejącym *dostępem*.
- Zaktualizuj ustawienia udostępniania witryny w samej witrynie, aby uniemożliwić członkom udostępnianie plików, folderów lub witryny, oraz wyłącz żądania dostępu.
- Jeśli do etykiety dodano osoby lub grupy z uprawnieniami Podgląd, możesz dodać je do witryny sieci SharePoint z uprawnieniami Odczyt.

### <a name="sharepoint-guest-settings"></a>SharePoint ustawień gościa

Ustawienie udostępniania gościa wybrane podczas tworzenia etykiety (które ma wpływ tylko na członkostwo w zespole) powinno być zgodne z ustawieniami udostępniania gościa skojarzonych z witryną SharePoint w następujący sposób:

|Ustawienie etykiety|SharePoint ustawienia witryny|
|:------------|:----------------------|
|**Pozwól Office 365 właściciele grup dodają do wybranej** grupy osoby spoza organizacji|**Nowi i istniejący goście** (domyślnie dla nowych zespołów)|
|**Pozwól Office 365 właścicielom grupy dodawanie osób spoza organizacji do grupy, która** nie jest zaznaczona|**Tylko osoby w Twojej organizacji**|

Zaktualizujemy także domyślny typ linku udostępniania, aby zmniejszyć ryzyko przypadkowego udostępniania plików i folderów szerszemu gronu odbiorców niż zamierzano.

Aby zaktualizować ustawienia witryny
1. Otwórz SharePoint [administracyjnego](https://admin.microsoft.com/sharepoint).
2. W **obszarze Witryny** kliknij pozycję **Aktywne witryny**.
3. Kliknij witrynę skojarzoną z zespołem.
4. Na karcie **Zasady** w obszarze **Udostępnianie zewnętrzne** kliknij pozycję **Edytuj**.
5. Jeśli zezwolisz na udostępnianie gości podczas tworzenia poufnej etykiety, upewnij się, że **zaznaczono opcję Nowi i** istniejący goście. Jeśli nie zezwolisz na udostępnianie podczas tworzenia etykiety, wybierz pozycję **Tylko osoby w Twojej organizacji**.
6. W obszarze Domyślny typ linku udostępniania wyczyść  pole wyboru Takie samo ustawienie jak ustawienie na poziomie organizacji i zaznacz pole **wyboru Osoby z istniejącym dostępem**.
7. Kliknij **Zapisz**.

#### <a name="private-channels"></a>Kanały prywatne

Jeśli dodasz do zespołu kanały prywatne, każdy kanał prywatny utworzy nową witrynę SharePoint z domyślnymi ustawieniami udostępniania. Te witryny nie są widoczne w centrum administracyjnym usługi SharePoint, dlatego w celu zaktualizowania ustawień udostępniania gościa należy użyć polecenia cmdlet [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) PowerShell z następującymi parametrami:

- `-SharingCapability Disabled` aby wyłączyć udostępnianie gości (jest ono domyślnie włączone)
- `-DefaultSharingLinkType Internal` aby zmienić domyślny link udostępniania na *Określone osoby*

Jeśli nie planujesz używania kanałów prywatnych w zespole, rozważ możliwość tworzenia ich przez członków zespołu w obszarze Uprawnienia **członków w** [ustawieniach zespołu](https://support.microsoft.com/office/ce053b04-1b8e-4796-baa8-90dc427b3acc).

### <a name="site-sharing-settings"></a>Ustawienia udostępniania witryn

Aby zapewnić, że SharePoint nie będzie udostępniana osobom, które nie są członkami zespołu, ograniczymy takie udostępnianie do właścicieli. Ograniczamy także udostępnianie plików i folderów właścicielom zespołu. Dzięki temu właściciele mają pewność, że plik zostanie udostępniony osobie spoza zespołu.

Aby skonfigurować udostępnianie witryn tylko przez właścicieli
1. W Teams **przejdź do karty** Ogólne zespołu, który chcesz zaktualizować.
2. Na pasku narzędzi zespołu kliknij pozycję **Pliki**.
3. Kliknij wielokropek, a następnie kliknij pozycję **Otwórz w programie SharePoint**.
4. Na pasku narzędzi w witrynie SharePoint kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
5. W okienku Uprawnienia witryny w obszarze **Ustawienia** udostępniania kliknij pozycję **Zmień ustawienia udostępniania**.
6. W **obszarze Uprawnienia udostępniania** wybierz **pozycję Tylko właściciele witryn mogą udostępniać pliki, foldery** i witrynę, a następnie kliknij przycisk **Zapisz**.

### <a name="custom-site-permissions"></a>Niestandardowe uprawnienia witryny

Jeśli do etykiety wrażliwości dodano osoby z uprawnieniami Podgląd, możesz dodać je do witryny SharePoint z dostępem do odczytu, aby ułatwić im dostęp do plików.

Aby dodać użytkowników do witryny
1. W witrynie kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
2. Kliknij **pozycję Zaproś** osoby, a następnie kliknij pozycję **Udostępnij tylko witrynę**.
3. Wpisz nazwy użytkowników i grup, które chcesz zaprosić.
4. Dla każdej osoby lub grupy, którą dodasz, zmień jej uprawnienia z **Edytuj na** **Odczyt**.
5. Wybierz, czy chcesz wysłać do nich wiadomość e-mail z linkiem do witryny.
6. Kliknij pozycję **Dodaj**.

## <a name="additional-protections"></a>Dodatkowe zabezpieczenia

Microsoft 365 oferuje dodatkowe metody zabezpieczania zawartości. Rozważ, czy poniższe opcje zwiększą bezpieczeństwo Twojej organizacji.

- Niech Twoi goście przyjmą [warunki użytkowania](/azure/active-directory/conditional-access/terms-of-use).
- Konfigurowanie zasad [limitu czasu sesji](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) dla gości.
- Utwórz [typy informacji poufnych i](../compliance/sensitive-information-type-learn-about.md) korzystaj [z ochrony przed utratą danych](../compliance/dlp-learn-about-dlp.md) , aby ustawić zasady dotyczące uzyskiwania dostępu do informacji poufnych.
- Używanie [Azure Active Directory dostępu do](/azure/active-directory/governance/access-reviews-overview) okresowego przeglądania dostępu do zespołu i członkostwa.

## <a name="drive-user-adoption-for-team-members"></a>Wdrożenie użytkowników dla członków zespołu

Gdy zespół jest w miejscu, czas zapewnić członkom tego zespołu bezpieczeństwo i jego wdrożenie.

### <a name="train-your-users"></a>Szkolenie użytkowników

Członkowie zespołu mają dostęp do zespołu i wszystkich jego zasobów, w tym czatów, spotkań i innych aplikacji. Podczas pracy z plikami w sekcji **Pliki** kanału członkowie zespołu powinni przypisać etykietę wrażliwości do tworzyć pliki.

Etykieta zastosowana do pliku jest szyfrowana. Członkowie zespołu mogą go otwierać i współpracować w czasie rzeczywistym. Jeśli plik opuści witrynę i zostanie on przesyłany dalej do złośliwego użytkownika, będzie musiał podać poświadczenia konta użytkownika, które jest członkiem zespołu, aby otworzyć plik i wyświetlić jego zawartość. 

Szkolenie członków zespołu:

- Ważność korzystania z nowego zespołu na czatach, spotkaniach, plikach i innych zasobach witryny SharePoint oraz o konsekwencjach ściśle uregulowanego wycieku danych, takich jak konsekwencje prawne, przepisy prawne, oprogramowanie wymuszające okup czy utrata konkurencyjności.
- Jak uzyskać dostęp do zespołu.
- Jak tworzyć nowe pliki w witrynie i przekazywać nowe pliki przechowywane lokalnie.
- Jak oznaczać pliki etykietami z właściwą etykietą wrażliwości zespołu.
- Etykieta chroni pliki nawet wtedy, gdy zostaną one wyciekone z witryny.

To szkolenie powinno obejmować ćwiczenia praktyczne, aby członkowie zespołu doświadczali tych możliwości i swoich wyników.

### <a name="conduct-periodic-reviews-of-usage-and-address-team-member-feedback"></a>Przeprowadzanie okresowych przeglądów użycia i wyadresuj opinie członków zespołu

W tygodniach po szkoleniu:

- Szybko kontaktuj się z opiniami członków zespołu i dostrajaj konfiguracje i konfiguracje.
- Analizuj użycie zespołu i porównaj je z oczekiwaniami w tym zespole.
- Upewnij się, że pliki o wysokim stopniu regulacji zostały prawidłowo oznaczone etykietą wrażliwości. (Możesz sprawdzić, do których plików jest przypisana etykieta, wyświetlając folder w programie SharePoint i dodając **kolumnę** Charakter za pomocą opcji Pokaż **/ukryj** kolumny **w kolumnie Dodaj**.

W razie potrzeby ponownie przećlij użytkowników.

## <a name="see-also"></a>Zobacz też

[Usługa Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure)