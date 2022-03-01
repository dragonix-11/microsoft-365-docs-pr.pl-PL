---
title: Konfigurowanie zespołu z izolacji zabezpieczeń w środowisku deweloper/test
f1.keywords:
- NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 08/14/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
ms.custom: admindeeplinkCOMPLIANCE
description: Skonfiguruj zabezpieczenia i infrastrukturę, która umożliwi Twoim pracownikom pracę zdalną z dowolnego miejsca i w dowolnym czasie.
ms.openlocfilehash: 602bec66eec26551ae6d98bafdb99466747d8fa9
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027143"
---
# <a name="configure-a-team-with-security-isolation-in-a-devtest-environment"></a>Konfigurowanie zespołu z izolacji zabezpieczeń w środowisku deweloper/test

Ten artykuł zawiera instrukcje krok po kroku dotyczące tworzenia zespołu z izolacji [zabezpieczeń w](secure-teams-security-isolation.md) środowisku deweloperska/testowym.

[Konfiguracja odizolego zespołu strategii firmy.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

Skorzystaj z tego środowiska deweloper/testowego, aby poeksperymentować i dostosować ustawienia do określonych potrzeb, zanim wdrożysz ten typ zespołu w środowisku produkcyjnym.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska Microsoft 365 Enterprise testowego

Jeśli chcesz tylko w sposób podstawowy przetestować poufne i wysoce poufne zespoły przy minimalnych wymaganiach, postępuj zgodnie z instrukcjami w teście konfiguracja [podstawowa podstawowa](../enterprise/lightweight-base-configuration-microsoft-365-enterprise.md).

Jeśli chcesz przetestować poufne i wysoce poufne zespoły w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w teście [synchronizacji skrótów haseł](../enterprise/password-hash-sync-m365-ent-test-environment.md).

> [!NOTE]
> Testowanie zespołu izolacji zabezpieczeń nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Usługi domenowe w usłudze Active Directory (AD DS). Jest on podany jako opcja, dzięki czemu można przetestować zespół izolacji zabezpieczeń i poeksperymentować z nim w środowisku, które reprezentuje typową organizację.

## <a name="phase-2-create-and-configure-your-azure-active-directory-azure-ad-group-and-users"></a>Etap 2. Tworzenie i konfigurowanie grupy Azure Active Directory (Azure AD) i użytkowników

Na tym etapie utworzysz i skonfigurujesz grupę usługi Azure AD oraz użytkowników dla organizacji fikcyjnej.

Najpierw utwórz grupę zabezpieczeń za pomocą portalu Azure Portal.

1. Utwórz osobną kartę w przeglądarce, a następnie przejdź do portalu Azure Portal pod witrynie [https://portal.azure.com](https://portal.azure.com). W razie potrzeby zaloguj się przy użyciu poświadczeń administratora globalnego na potrzeby subskrypcji Microsoft 365 E5 próbnej lub płatnej.

2. W portalu Azure Portal kliknij pozycję **Azure Active Directory > Grupy**.

3. Na **bladej grupy — Wszystkie** grupy kliknij **pozycję + Nowa grupa**.

4. Na **bladeju** grupy:

  - Wybierz **pozycję Zabezpieczenia** w **typie grupy**.

  - Wpisz **nazwę pakietu C-Suite**.

  - Wybierz **pozycję Przypisane w** **typie członkostwa**.

5. Kliknij **przycisk Utwórz**, a następnie zamknij **grupę.**

Następnie skonfiguruj licencjonowanie automatyczne, aby członkowie nowej grupy **usługi C-Suite** automatycznie przypisywali Microsoft 365 E5 licencji.

1. W portalu Azure portal kliknij pozycję **Azure Active Directory > licencje > wszystkich produktów**.

2. Na liście wybierz pozycję Microsoft 365 Enterprise **E5**, a następnie kliknij przycisk **Przypisz**.

3. Na stronie **Przypisywanie licencji** kliknij pozycję **Użytkownicy i grupy**.

4. Na liście grup wybierz grupę **C-Suite** .

5. Kliknij **pozycję Wybierz**, a następnie kliknij pozycję **Przypisz**.

6. Zamknij kartę Azure Portal w przeglądarce.

Następnie połącz [się przy użyciu modułu Azure Active Directory PowerShell dla Graph komputera](../enterprise/connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Wpisz nazwę organizacji, lokalizację i wspólne hasło, a następnie uruchom te polecenia z wiersza polecenia programu PowerShell lub środowiska Integrated Script Environment (ISE), aby utworzyć nowe konta użytkowników i dodać je do grupy usługi C-Suite:

```powershell
$orgName="<organization name, such as contoso-test for the contoso-test.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO")
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> Tutaj często używa się wspólnego hasła w celu automatyzacji i łatwości konfiguracji w środowisku deweloper/test. Oczywiście jest to zdecydowanie zalecane w przypadku subskrypcji produkcyjnych.

Aby sprawdzić, czy licencjonowanie oparte na grupie działa prawidłowo, skorzystaj z poniższych kroków.

1. Zaloguj się do [Centrum administracyjnego usługi Microsoft 365](https://admin.microsoft.com).

2. Na nowej **karcie centrum administracyjne platformy Microsoft 365** kliknij pozycję **Użytkownicy**.

3. Na liście użytkowników kliknij pozycję **Dyrektor generalny**.

4. W okienku, które zawiera listę właściwości konta użytkownika **Dyrektora** Generalnego, sprawdź, czy przypisano mu licencję Microsoft 365 Enterprise **E5** w **licencji produktu**.

## <a name="phase-3-create-your-team"></a>Etap 3. Tworzenie zespołu

W tej fazie tworzysz i konfigurujesz zespół z izolacji zabezpieczeń dla członków wyższego zespołu kierownictwa w celu współpracy nad strategią firmy.

Najpierw włącz etykiety wrażliwości, aby chronić zawartość Microsoft Teams, Office 365 grup i SharePoint sieci Web przed rozpoczęciem pracy z czynnościami w [tym artykule](../compliance/sensitivity-labels-teams-groups-sites.md).

Następnie utwórz zespół:

1. W Teams kliknij pozycję **Teams** lewej stronie aplikacji, **a** następnie kliknij pozycję Dołącz lub utwórz zespół u dołu listy zespołów.
2. Kliknij **pozycję Utwórz zespół** (pierwsza karta, lewy górny róg).
3. Wybierz **pozycję Stwórz zespół od podstaw**.
4. Na **liście Charakter** zachowaj domyślną wartość.
5. W **obszarze Prywatność** kliknij pozycję **Prywatne**.
6. Wpisz **Strategia firmy**, a następnie kliknij **pozycję** **UtwórzZamówienie** > .

Następnie ogranicz możliwość tworzenia kanałów prywatnych do właścicieli grupy Strategii firmy.

1. W zespole kliknij pozycję **Więcej opcji**, a następnie kliknij pozycję **Zarządzaj zespołem**.
2. Na karcie **Ustawienia** rozwiń pozycję **Uprawnienia członków**.
3. Wyczyść pole **wyboru Zezwalaj członkom na tworzenie kanałów** prywatnych.

Następnie musisz skonfigurować etykietę wrażliwości z następującymi ustawieniami:

- Nazwa to Strategia firmy
- Szyfrowanie jest włączone
- Grupa Strategia firmy ma Co-Author firmy

Wykonaj następujące czynności:

1. Otwórz Centrum zgodności platformy Microsoft 365 w obszarze **Rozwiązania** wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Ochrona informacji**</a>.
1. Kliknij **pozycję Utwórz etykietę**.
1. Wpisz **Company Strategy (Strategia** firmy) dla nazwy etykiety.
1. Wpisz **etykietkę narzędzia** Kierownictwo wyższego szczebla w dokumentach strategii, a następnie kliknij przycisk **Dalej**.
1. Na stronie **Szyfrowanie** z listy rozwijanej **Szyfrowanie** wybierz pozycję **Zastosuj**.
1. Aby dodać uprawnienia zespołu:<br>
  a. Kliknij **pozycję Przypisz uprawnienia**.<br>
  b. Kliknij **pozycję Dodaj użytkowników lub grupy**, wybierz **pozycję Strategia firmy**, a następnie kliknij przycisk **Dodaj**.<br>
  c. Kliknij **pozycję Wybierz uprawnienia**.<br>
  d. Z **listy rozwijanej wybierz** pozycję Współtworz, a następnie kliknij przycisk **Zapisz**.<br>
1. Kliknij **Dalej**.
1. Na stronie **Oznaczanie zawartości** kliknij przycisk **Dalej**.
1. Na stronie **Ustawienia witryny i grupy** ustaw dla **ustawienia witryny i grupy** wartość **Wł**.
1. Na liście **rozwijanej Prywatność Office 365 witryn** zespołu połączonych z grupą wybierz pozycję Prywatne **— tylko członkowie mogą uzyskać dostęp do witryny**.
1. W **obszarze Urządzenia niezamanektowane** wybierz pozycję **Blokuj dostęp**.
1. Kliknij **Dalej**.
1. Na stronie **Automatyczne oznaczanie Office kliknij** przycisk **Dalej**.
1. Kliknij **pozycję Prześlij**, a następnie kliknij pozycję **Gotowe**.

Następnie opublikuj nową etykietę, wykonać następujące czynności:

1. W Centrum zgodności platformy Microsoft 365 na karcie <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Ochrona informacji**</a> wybierz kartę **Zasady** etykiet.
2. Kliknij **pozycję Publikuj etykiety**.
3. Na **stronie Wybierz etykiety wrażliwości do opublikowania** kliknij pozycję **Wybierz etykiety wrażliwości do opublikowania**.
4. Wybierz **pozycję Strategia firmy**, a następnie kliknij przycisk **Dodaj**.
5. Kliknij **Dalej**.
6. Na stronie **Publikowanie dla użytkowników i grup** kliknij pozycję **Wybierz użytkowników i grupy**.
7. Kliknij **pozycję Dodaj**, a następnie wybierz **pozycję Strategia firmy**.
8. Kliknij **przycisk Dodaj**, a następnie kliknij pozycję **Gotowe**.
9. Kliknij **Dalej**.
10. Na stronie Ustawienia zasad zaznacz pole wyboru Użytkownicy muszą podać uzasadnienie, aby usunąć etykietę lub etykietę klasyfikacji o niższej klasyfikacji, **a** następnie kliknij przycisk **Dalej**.
11. Wpisz **Nazwę zasad Strategia** firmy, a następnie kliknij przycisk **Dalej**.
12. Kliknij **pozycję Prześlij** , a następnie kliknij pozycję **Gotowe**.

Po opublikowaniu **etykiety Strategii** firmy może mi trochę potrwać.

Następnie zastosuj nową etykietę do zespołu  strategii firmy i zaktualizuj domyślny typ linku udostępniania, aby zmniejszyć ryzyko przypadkowego udostępnienia plików i folderów szerszemu gronu odbiorców, niż zamierzano.

1. Otwórz SharePoint [administracyjnego](https://admin.microsoft.com/sharepoint).
1. W **obszarze Witryny** kliknij pozycję **Aktywne witryny**.
1. Kliknij **witrynę Strategii** firmy.
1. Na karcie **Zasady** **w obszarze Charakter** kliknij pozycję **Edytuj**.
1. Wybierz **etykietę Strategia firmy** , a następnie kliknij przycisk **Zapisz**.
1. Na karcie **Zasady** w obszarze **Udostępnianie zewnętrzne** kliknij pozycję **Edytuj**.
1. Wybierz **pozycję Tylko osoby w Twojej organizacji**.
1. W **obszarze Domyślny** typ linku udostępniania wyczyść  pole wyboru Takie samo ustawienie jak ustawienie na poziomie organizacji i zaznacz pole **wyboru Osoby z istniejącym dostępem**.
1. Kliknij **Zapisz**.

Następnie skonfiguruj udostępnianie witryn tylko dla właścicieli dla **zespołu strategii** firmy.

1. W Teams przejdź do karty **Ogólne** zespołu **strategii** firmy.
2. Na pasku narzędzi zespołu kliknij pozycję **Pliki**.
3. Kliknij wielokropek, a następnie kliknij pozycję **Otwórz w programie SharePoint**.
4. Na pasku narzędzi w witrynie SharePoint kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
5. W okienku Uprawnienia witryny w obszarze **Udostępnianie witryny** kliknij pozycję Zmień sposób udostępniania **przez członków**.
6. W **obszarze Uprawnienia udostępniania** wybierz **pozycję Tylko właściciele witryn mogą udostępniać pliki, foldery** i witrynę, a następnie kliknij przycisk **Zapisz**.
7. Zamknij **okienka** Uprawnienia **Ustawienia** folderów.

Jeśli zalogujesz się jako członek grupy Strategia firmy, w opcji Charakter na pasku narzędzi  Strona główna programu Word, Excel i PowerPoint. Wybierz **etykietę Strategii firmy** z **opcji Charakter,** aby przypisać tę etykietę do pliku.

Oto wynikowa konfiguracja dla zespołu strategii firmy.

![Konfiguracja odizolego zespołu strategii firmy.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

## <a name="next-step"></a>Następny krok

Gdy wszystko będzie gotowe do wdrożenia produkcyjnego, zobacz te [instrukcje konfiguracji](secure-teams-security-isolation.md).
