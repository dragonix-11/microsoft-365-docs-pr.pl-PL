---
title: Konfigurowanie zespołów w celu ochrony danych poufnych
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
- admindeeplinkSPO
recommendations: false
description: Dowiedz się, jak wdrażać zespoły z ochroną poufnych danych.
ms.openlocfilehash: 51e4c3b13d1a54e4edcfd9926ae246dde7d7e3e4
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712704"
---
# <a name="configure-teams-with-protection-for-sensitive-data"></a>Konfigurowanie zespołów w celu ochrony danych poufnych

W tym artykule przyjrzymy się konfigurowaniu zespołu w celu zabezpieczenia poufnego poziomu ochrony. Przed rozpoczęciem czynności z tego artykułu upewnij się, [](configure-teams-baseline-protection.md) że zostały wykonane czynności opisane w artykule Wdrażanie zespołów za pomocą ochrony według planu bazowego. Warstwa poufnych zapewnia następujące dodatkowe zabezpieczenia w stosunku do warstwy bazowej:

- Etykieta wrażliwości dla zespołu umożliwiająca włączenie lub wyłączenie udostępniania gościa i ograniczenie dostępu do SharePoint zawartości tylko do sieci Web dla urządzeń nieza zarządzania. Etykieta ta może być także używana do klasyfikowania plików.
- Bardziej restrykcyjny domyślny typ linku udostępniania
- Tylko właściciele zespołu mogą tworzyć kanały prywatne.

## <a name="video-demonstration"></a>Pokaz wideo

Obejrzyj ten klip wideo, aby uzyskać informacje o procedurach opisanych w tym artykule.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NMS6]

## <a name="guest-sharing"></a>Udostępnianie gości

W zależności od charakteru firmy możesz zechcieć włączyć udostępnianie gości w zespołach zawierających poufne dane. Jeśli planujesz współpracować z osobami spoza organizacji w zespole, zalecamy włączenie udostępniania gości. Microsoft 365 udostępnia wiele funkcji zabezpieczeń i zgodności, które ułatwiają bezpieczne udostępnianie poufnej zawartości. Na ogół jest to bezpieczniejsza opcja niż wysyłanie zawartości pocztą e-mail bezpośrednio do osób spoza organizacji.

Aby uzyskać szczegółowe informacje na temat bezpiecznego udostępniania gościom, zobacz następujące zasoby:

- [Ograniczanie przypadkowego udostępnienia plików osobom spoza organizacji](./share-limit-accidental-exposure.md)
- [Tworzenie bezpiecznego środowiska udostępniania gości](./create-secure-guest-sharing-environment.md)

Aby umożliwić lub zablokować udostępnianie gości, użyjemy kombinacji etykiety wrażliwości dla zespołu i kontroli udostępniania na poziomie witryny dla skojarzonej SharePoint, co omówiono w dalszej części tego tematu.

## <a name="sensitivity-labels"></a>Etykiety wrażliwości

W przypadku poufnego poziomu ochrony będziemy klasyfikować zespół za pomocą etykiety wrażliwości. Etykieta ta może być także używana do klasyfikowania poszczególnych plików w tym lub innych zespołach, a także w innych lokalizacjach plików, takich jak SharePoint lub OneDrive. 

Pierwszym krokiem jest włączenie etykiet wrażliwości dla Teams. Aby [uzyskać szczegółowe informacje, zobacz Chroninie zawartości w grupach Microsoft Teams, Office 365 grup SharePoint sieci](../compliance/sensitivity-labels-teams-groups-sites.md) Web za pomocą etykiet wrażliwości.

Jeśli w organizacji wdrożono już etykiety wrażliwości, rozważ dopasowanie etykiet do ogólnej strategii dotyczącej etykiet. W razie potrzeby możesz zmienić nazwę lub ustawienia w celu zaspokojenia potrzeb organizacji.

Po włączeniu etykiet wrażliwości dla Teams następnym krokiem jest utworzenie etykiety.

Aby utworzyć etykietę wrażliwości
1. Otwórz [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com).
2. W **obszarze Rozwiązania** kliknij pozycję **Ochrona informacji**.
3. Kliknij **pozycję Utwórz etykietę**.
4. Nadaj etykiecie nazwę. Sugerujemy **opcję Poufny**, ale możesz wybrać inną nazwę, jeśli jest już ona w użyciu.
5. Dodaj nazwę wyświetlaną i opis, a następnie kliknij przycisk **Dalej**.
6. Na stronie **Definiowanie zakresu tej etykiety wybierz** pozycję Pliki & **e-mail** i grupy **& witryny i** kliknij przycisk **Dalej**.
7. Na stronie **Wybieranie ustawień ochrony dla plików i wiadomości e-mail** kliknij przycisk **Dalej**.
8. Na stronie *Automatyczne oznaczanie plików i wiadomości e-mail** kliknij przycisk **Dalej**.
9. Na stronie **Definiowanie ustawień ochrony dla grup** i witryn wybierz pozycję  Ustawienia prywatności i dostępu użytkowników zewnętrznych oraz Dostęp urządzeń i ustawienia udostępniania **zewnętrznego** i kliknij przycisk **Dalej**.
10. Na stronie **Definiowanie ustawień prywatności i dostępu** użytkowników zewnętrznych w obszarze **Prywatność** **wybierz opcję** Prywatna.
11. Jeśli chcesz zezwolić na dostęp dla gości, w obszarze Dostęp użytkowników zewnętrznych wybierz pozycję Zezwalaj Microsoft 365 właściciele grup dodają do grupy osoby spoza organizacji **jako gości**.
12. Kliknij **Dalej**.
13. Na stronie **Definiowanie ustawień udostępniania zewnętrznego i dostępu do** urządzenia wybierz pozycję Kontroluj **udostępnianie zewnętrzne z SharePoint witryn**.
14. W **obszarze Zawartość może być udostępniana wybierz** pozycję Nowi i istniejący goście, jeśli zezwalasz na dostęp dla **gości, lub** Pozycję Tylko osoby w Twojej organizacji, jeśli nie.
15. W **obszarze Dostęp z urządzeń niezamaniowanej** wybierz pozycję **Zezwalaj na ograniczony dostęp tylko do sieci Web**.
16. Kliknij **Dalej**.
17. Na stronie **Automatyczne oznaczanie kolumn bazy danych** kliknij przycisk **Dalej**.
18. Kliknij **pozycję Utwórz etykietę**, a następnie kliknij pozycję **Gotowe**.

Po utworzeniu etykiety musisz opublikować ją dla użytkowników, którzy będą jej używać. W celu ochrony poufnej udostępnimy etykietę wszystkim użytkownikom. Etykietę publikujesz w Centrum zgodności platformy Microsoft 365 **na karcie Zasady** etykiet na **stronie Ochrona** informacji. Jeśli masz istniejące zasady, które dotyczą wszystkich użytkowników, dodaj tę etykietę do tych zasad. Jeśli chcesz utworzyć nowe zasady, zobacz Publikowanie etykiet wrażliwości [przez utworzenie zasad etykiet](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Tworzenie zespołu

Dalsza konfiguracja poufnego scenariusza odbywa się w SharePoint skojarzonej z zespołem, więc następnym krokiem jest utworzenie zespołu.

Aby utworzyć zespół na informacje poufne
1. W Teams kliknij pozycję **Teams** lewej stronie aplikacji, **a** następnie kliknij pozycję Dołącz lub utwórz zespół u dołu listy zespołów.
2. Kliknij **pozycję Utwórz zespół** (pierwsza karta, lewy górny róg).
3. Wybierz **pozycję Stwórz zespół od podstaw**.
4. Na liście **Charakter** **wybierz wrażliwą** etykietę, która właśnie została utworzona.
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

## <a name="shared-channel-settings"></a>Ustawienia kanału udostępnionego

[Kanały](/MicrosoftTeams/shared-channels) udostępnione nie mają ustawień na poziomie zespołu. Ustawienia kanału udostępnionego skonfigurowane w centrum administracyjnym Teams Azure AD mają zastosowanie do wszystkich zespołów bez względu na charakter.

## <a name="sharepoint-settings"></a>SharePoint ustawień

Za każdym razem, gdy tworzysz nowy zespół z poufnymi etykietami, należy wykonać dwa kroki w SharePoint:

- Zaktualizuj ustawienia udostępniania gościa witryny w centrum administracyjnym usługi SharePoint, aby zaktualizować domyślny link udostępniania do *określonych osób*.
- Zaktualizuj ustawienia udostępniania witryny w samej witrynie, aby uniemożliwić jej członkom udostępnianie.

### <a name="site-default-sharing-link-settings"></a>Domyślne ustawienia linku udostępniania witryny

Aby zaktualizować domyślny typ linku udostępniania witryny

1. Otwórz centrum SharePoint administracyjnego, a następnie w **obszarze Witryny** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
1. Wybierz witrynę skojarzoną z zespołem.
1. Na karcie **Zasady** w obszarze **Udostępnianie zewnętrzne** kliknij pozycję **Edytuj**.
1. W obszarze Domyślny typ linku udostępniania wyczyść  pole wyboru Takie samo jak ustawienie na poziomie organizacji i zaznacz pole wyboru Określone osoby (tylko osoby **określone przez użytkownika).**
1. Wybierz **Zapisz**.

Jeśli chcesz utworzyć skrypt tego skryptu w ramach procesu tworzenia zespołu, możesz użyć polecenia [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) `-DefaultSharingLinkType Direct` z parametrem, aby zmienić domyślny link udostępniania na *Określone osoby*.

Pamiętaj, że jeśli dodasz do zespołu kanały prywatne lub udostępnione, każdy z nich utworzy nową witrynę SharePoint z domyślnymi ustawieniami udostępniania. Możesz je zaktualizować w centrum SharePoint, wybierając witryny skojarzone z zespołem.

### <a name="site-sharing-settings"></a>Ustawienia udostępniania witryn

Aby zapewnić, że SharePoint nie będzie udostępniana osobom, które nie są członkami zespołu, ograniczymy takie udostępnianie do właścicieli. Jest to konieczne tylko SharePoint witryny utworzonej z zespołem. Dodatkowe witryny utworzone w ramach kanałów prywatnych lub udostępnionych nie mogą być udostępniane poza zespołem lub kanałem.

Aby skonfigurować udostępnianie witryn tylko przez właścicieli
1. W Teams **przejdź do karty** Ogólne zespołu, który chcesz zaktualizować.
2. Na pasku narzędzi zespołu kliknij pozycję **Pliki**.
3. Kliknij wielokropek, a następnie kliknij pozycję **Otwórz w programie SharePoint**.
4. Na pasku narzędzi w witrynie SharePoint kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
5. W **okienku Uprawnienia** witryny w obszarze **Udostępnianie witryny** kliknij pozycję Zmień sposób udostępniania **przez członków**.
6. W **obszarze Uprawnienia udostępniania** wybierz pozycję Właściciele i członkowie witryny, a osoby z uprawnieniami do edytowania mogą udostępniać pliki i foldery **,** ale tylko właściciele witryn mogą udostępniać witrynę, a następnie kliknij pozycję **Zapisz**.


## <a name="related-topics"></a>Tematy pokrewne

[Tworzenie i konfigurowanie etykiet wrażliwości oraz ich zasad](../compliance/create-sensitivity-labels.md)
