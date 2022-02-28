---
title: Konfigurowanie zespołów z ochroną bardzo poufnych danych
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
recommendations: false
description: Dowiedz się, jak wdrażać zespoły z ochroną bardzo poufnych danych.
ms.openlocfilehash: 27d2183a3f6f5f43f4461bc83fe3b33ac9f4f56e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984264"
---
# <a name="configure-teams-with-protection-for-highly-sensitive-data"></a>Konfigurowanie zespołów z ochroną bardzo poufnych danych

W tym artykule o konfigurowaniu zespołu pracujemy nad bardzo poufnym poziomem ochrony. Przed rozpoczęciem czynności z tego artykułu upewnij się, [](configure-teams-baseline-protection.md) że zostały wykonane czynności opisane w artykule Wdrażanie zespołów za pomocą ochrony według planu bazowego.

Dla tej warstwy ochrony tworzymy etykietę wrażliwości, która może być używana w całej organizacji w przypadku bardzo ważnych zespołów i plików. Tylko członkowie Twojej organizacji i goście, których określono, będą mogli odszyfrowywać pliki, które używają tej etykiety. Jeśli chcesz dodatkowo odizolować uprawnienia, tak aby tylko członkowie określonego zespołu mogą odszyfrowywać pliki, zobacz Wdrażanie zespołu  [z izolacji zabezpieczeń](secure-teams-security-isolation.md).

Wysoce wrażliwa warstwa zapewnia następujące dodatkowe zabezpieczenia w stosunku do warstwy bazowej:

- Etykieta wrażliwości dla zespołu, która umożliwia włączenie lub wyłączenie udostępniania gościa i blokuje dostęp do SharePoint zawartości dla urządzeń niezawiąanych. Ta etykieta może być także używana do klasyfikowania i szyfrowania plików.
- Bardziej restrykcyjny domyślny typ linku udostępniania
- Tylko właściciele zespołu mogą tworzyć kanały prywatne.
- Żądania dostępu skojarzonej SharePoint są wyłączone.

## <a name="video-demonstration"></a>Pokaz wideo

Obejrzyj ten klip wideo, aby uzyskać informacje o procedurach opisanych w tym artykule.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NzI7]

## <a name="guest-sharing"></a>Udostępnianie gości

W zależności od charakteru działalności możesz zechcieć włączyć udostępnianie gości w zespołach zawierających bardzo poufne dane. Jeśli planujesz współpracować z osobami spoza organizacji w zespole, zalecamy włączenie udostępniania gości. Microsoft 365 udostępnia wiele funkcji zabezpieczeń i zgodności, które ułatwiają bezpieczne udostępnianie poufnej zawartości. Na ogół jest to bezpieczniejsza opcja niż wysyłanie zawartości pocztą e-mail bezpośrednio do osób spoza organizacji.

Aby uzyskać szczegółowe informacje na temat bezpiecznego udostępniania gościom, zobacz następujące zasoby:

- [Ograniczanie przypadkowego udostępnienia plików osobom spoza organizacji](./share-limit-accidental-exposure.md)
- [Tworzenie bezpiecznego środowiska udostępniania gości](./create-secure-guest-sharing-environment.md)

Aby umożliwić lub zablokować udostępnianie gości, użyjemy kombinacji etykiety wrażliwości dla zespołu i kontroli udostępniania na poziomie witryny dla skojarzonej SharePoint, co omówiono w dalszej części tego tematu.

## <a name="sensitivity-labels"></a>Etykiety wrażliwości

W celu bardzo poufnego poziomu ochrony będziemy klasyfikować zespół za pomocą etykiety wrażliwości. Etykieta ta może być także używana do klasyfikowania i szyfrowania poszczególnych plików w tym lub innych zespołach bądź w innych lokalizacjach plików, takich jak SharePoint lub OneDrive. 

Pierwszym krokiem jest włączenie etykiet wrażliwości dla Teams. Aby [uzyskać szczegółowe informacje, zobacz Chroninie zawartości w grupach Microsoft Teams, Office 365 grup SharePoint sieci](../compliance/sensitivity-labels-teams-groups-sites.md) Web za pomocą etykiet wrażliwości.

Jeśli w organizacji wdrożono już etykiety wrażliwości, rozważ dopasowanie etykiet do ogólnej strategii dotyczącej etykiet. W razie potrzeby możesz zmienić nazwę lub ustawienia w celu zaspokojenia potrzeb organizacji.

Po włączeniu etykiet wrażliwości dla Teams następnym krokiem jest utworzenie etykiety.

Aby utworzyć etykietę wrażliwości
1. Otwórz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com).
2. W **obszarze Rozwiązania** kliknij pozycję **Ochrona informacji**.
3. Kliknij **pozycję Utwórz etykietę**.
4. Nadaj etykiecie nazwę. Sugerujemy **opcję Wysoce poufne**, ale możesz wybrać inną nazwę, jeśli jest już ona w użyciu.
5. Dodaj nazwę wyświetlaną i opis, a następnie kliknij przycisk **Dalej**.
6. Na stronie **Definiowanie zakresu tej etykiety wybierz** pozycję Pliki & **e-mail** i grupy **& witryny i** kliknij przycisk **Dalej**.
7. Na stronie **Wybieranie ustawień ochrony dla plików i wiadomości e-mail** wybierz pozycję **Szyfruj pliki** i wiadomości e-mail, a następnie kliknij przycisk **Dalej**.
8. Na stronie **Szyfrowanie** wybierz pozycję **Konfiguruj ustawienia szyfrowania**.
9. W **obszarze Przypisywanie uprawnień określonym użytkownikom i grupom** kliknij pozycję **Przypisz uprawnienia**.
10. Kliknij **pozycję Dodaj wszystkich użytkowników i grupy w organizacji**.
11. Jeśli istnieją goście, którzy powinni mieć uprawnienia do odszyfrowywania plików, kliknij pozycję **Dodaj użytkowników lub** grupy i dodaj ich.
12.  Kliknij **przycisk Zapisz**, a następnie kliknij przycisk **Dalej**.
13. Na stronie *Automatyczne oznaczanie plików i wiadomości e-mail** kliknij przycisk **Dalej**.
14. Na stronie **Definiowanie ustawień ochrony dla grup** i witryn wybierz pozycję  Ustawienia prywatności i dostępu użytkowników zewnętrznych oraz Dostęp urządzeń i ustawienia udostępniania **zewnętrznego** i kliknij przycisk **Dalej**.
15. Na stronie **Definiowanie ustawień prywatności i dostępu** użytkowników zewnętrznych w obszarze **Prywatność** **wybierz opcję** Prywatna.
16. Jeśli chcesz zezwolić na dostęp dla gości, w obszarze Dostęp użytkowników zewnętrznych wybierz pozycję Zezwalaj Microsoft 365 właściciele grup dodają do grupy osoby spoza organizacji **jako gości**.
17. Kliknij **Dalej**.
18. Na stronie **Definiowanie ustawień udostępniania zewnętrznego i dostępu do** urządzenia wybierz pozycję Kontroluj **udostępnianie zewnętrzne z SharePoint witryn**.
19. W **obszarze Zawartość może być udostępniana wybierz** pozycję Nowi i istniejący goście, jeśli zezwalasz na dostęp dla **gości, lub** Pozycję Tylko osoby w Twojej organizacji, jeśli nie.
20. W **obszarze Dostęp z urządzeń niezawiązyanych** wybierz **pozycję Blokuj dostęp**. (Jeśli zezwalasz na dostęp gościom, a nie mają oni zarządzanych urządzeń, możesz wybrać opcję Zezwalaj na ograniczony **dostęp tylko do sieci Web**).
21. Kliknij **Dalej**.
22. Na stronie **Automatyczne oznaczanie kolumn bazy danych** kliknij przycisk **Dalej**.
23. Kliknij **pozycję Utwórz etykietę**, a następnie kliknij pozycję **Gotowe**.

Po utworzeniu etykiety musisz opublikować ją dla użytkowników, którzy będą jej używać. W celu ochrony poufnej udostępnimy etykietę wszystkim użytkownikom. Etykietę publikujesz w Centrum zgodności platformy Microsoft 365 **na karcie Zasady** etykiet na **stronie Ochrona** informacji. Jeśli masz istniejące zasady, które dotyczą wszystkich użytkowników, dodaj tę etykietę do tych zasad. Jeśli chcesz utworzyć nowe zasady, zobacz Publikowanie etykiet wrażliwości [przez utworzenie zasad etykiet](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Tworzenie zespołu

Dalsza konfiguracja bardzo poufnego scenariusza odbywa się w SharePoint skojarzonej z zespołem, więc następnym krokiem jest utworzenie zespołu.

Aby utworzyć zespół na temat bardzo poufnych informacji
1. W Teams kliknij pozycję **Teams** lewej stronie aplikacji, **a** następnie kliknij pozycję Dołącz lub utwórz zespół u dołu listy zespołów.
2. Kliknij **pozycję Utwórz zespół** (pierwsza karta, lewy górny róg).
3. Wybierz **pozycję Stwórz zespół od podstaw**.
4. Na liście **Charakter** **wybierz właśnie** utworzoną etykietę Wysoce poufne.
5. W **obszarze Prywatność** kliknij pozycję **Prywatne**.
6. Wpisz nazwę zespołu, a następnie kliknij pozycję **Utwórz**.
7. Dodaj użytkowników do zespołu, a następnie kliknij przycisk **Zamknij**.

## <a name="private-channel-settings"></a>Ustawienia kanału prywatnego

W tej warstwie ograniczamy tworzenie kanałów prywatnych do właścicieli zespołu.

Aby ograniczyć tworzenie kanału prywatnego
1. W zespole kliknij pozycję **Więcej opcji**, a następnie kliknij pozycję **Zarządzaj zespołem**.
2. Na karcie **Ustawienia** rozwiń pozycję **Uprawnienia członków**.
3. Wyczyść pole **wyboru Zezwalaj członkom na tworzenie kanałów** prywatnych.

Możesz również używać zasad [zespołów,](/MicrosoftTeams/teams-policies) aby kontrolować, kto może tworzyć kanały prywatne.

## <a name="sharepoint-settings"></a>SharePoint ustawień

Za każdym razem, gdy tworzysz nowy zespół z bardzo wrażliwą etykietą, trzeba wykonać dwie czynności w SharePoint:

- Zaktualizuj ustawienia udostępniania gościa dla witryny w centrum SharePoint, aby zaktualizować domyślny link udostępniania do *osób z istniejącym dostępem*.
- Zaktualizuj ustawienia udostępniania witryny w samej witrynie, aby uniemożliwić członkom udostępnianie plików, folderów lub witryny, oraz wyłącz żądania dostępu.

### <a name="site-default-sharing-link-settings"></a>Domyślne ustawienia linku udostępniania witryny

Aby zaktualizować domyślny typ linku udostępniania witryny

1. Otwórz SharePoint [administracyjnego](https://admin.microsoft.com/sharepoint).
2. W **obszarze Witryny** kliknij pozycję **Aktywne witryny**.
3. Kliknij witrynę skojarzoną z zespołem.
4. Na karcie **Zasady** w obszarze **Udostępnianie zewnętrzne** kliknij pozycję **Edytuj**.
5. W obszarze Domyślny typ linku udostępniania wyczyść  pole wyboru Takie samo ustawienie jak ustawienie na poziomie organizacji i zaznacz pole **wyboru Osoby z istniejącym dostępem**.
6. Kliknij **Zapisz**.

#### <a name="private-channels"></a>Kanały prywatne

Jeśli dodasz do zespołu kanały prywatne, każdy kanał prywatny utworzy nową witrynę SharePoint z domyślnymi ustawieniami udostępniania. Te witryny nie są widoczne w centrum administracyjnym programu SharePoint, dlatego w celu zaktualizowania ustawień udostępniania gościa należy użyć polecenia cmdlet programu Set-SPOSite PowerShell.

### <a name="site-sharing-settings"></a>Ustawienia udostępniania witryn

Aby zapewnić, że SharePoint nie będzie udostępniana osobom, które nie są członkami zespołu, ograniczymy takie udostępnianie do właścicieli. Ograniczamy także udostępnianie plików i folderów właścicielom zespołu. Dzięki temu właściciele mają pewność, że plik zostanie udostępniony osobie spoza zespołu.

Aby skonfigurować udostępnianie witryn tylko przez właścicieli
1. W Teams **przejdź do karty** Ogólne zespołu, który chcesz zaktualizować.
2. Na pasku narzędzi zespołu kliknij pozycję **Pliki**.
3. Kliknij wielokropek, a następnie kliknij pozycję **Otwórz w programie SharePoint**.
4. Na pasku narzędzi w witrynie SharePoint kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
5. W **okienku Uprawnienia** witryny w obszarze **Udostępnianie witryny** kliknij pozycję Zmień sposób udostępniania **przez członków**.
6. W **obszarze Uprawnienia udostępniania** wybierz **pozycję Tylko właściciele witryn mogą udostępniać pliki, foldery i witrynę**.
7. Ustaw **opcję Zezwalaj na żądania dostępu** **na wartość Wyłączone**, a następnie kliknij przycisk **Zapisz**.

## <a name="see-also"></a>Zobacz też

[Tworzenie i konfigurowanie etykiet wrażliwości oraz ich zasad](../compliance/create-sensitivity-labels.md)
