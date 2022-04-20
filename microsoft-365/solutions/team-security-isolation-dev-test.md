---
title: Konfigurowanie zespołu z izolacją zabezpieczeń w środowisku deweloperskim/testowym
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
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkSPO
description: Skonfiguruj zabezpieczenia i infrastrukturę, które umożliwiają pracownikom zdalną pracę z dowolnego miejsca i w dowolnym momencie.
ms.openlocfilehash: 0e54d3840e9207fd7e8b5c50415ad2ca60751059
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934252"
---
# <a name="configure-a-team-with-security-isolation-in-a-devtest-environment"></a>Konfigurowanie zespołu z izolacją zabezpieczeń w środowisku deweloperskim/testowym

Ten artykuł zawiera instrukcje krok po kroku dotyczące tworzenia [zespołu z izolacją zabezpieczeń](secure-teams-security-isolation.md) w środowisku deweloperskim/testowym.

[Konfiguracja dla izolowanego zespołu ds. strategii firmy.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

Użyj tego środowiska deweloperskiego/testowego, aby eksperymentować i dostosowywać ustawienia dla określonych potrzeb przed wdrożeniem tego typu zespołu w środowisku produkcyjnym.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Faza 1. Tworzenie środowiska testowego Microsoft 365 Enterprise

Jeśli chcesz po prostu przetestować wrażliwe i wysoce wrażliwe zespoły w lekki sposób z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](../enterprise/lightweight-base-configuration-microsoft-365-enterprise.md).

Jeśli chcesz przetestować wrażliwe i wysoce wrażliwe zespoły w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w [temacie Synchronizacja skrótów haseł](../enterprise/password-hash-sync-m365-ent-test-environment.md).

> [!NOTE]
> Testowanie zespołu z izolacją zabezpieczeń nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Active Directory Domain Services (AD DS). Jest ona dostępna w tym miejscu jako opcja umożliwiająca przetestowanie zespołu z izolacją zabezpieczeń i eksperymentowanie z nim w środowisku reprezentującym typową organizację.

## <a name="phase-2-create-and-configure-your-azure-active-directory-azure-ad-group-and-users"></a>Faza 2. Tworzenie i konfigurowanie grupy i użytkowników Azure Active Directory (Azure AD)

W tej fazie utworzysz i skonfigurujesz grupę i użytkowników usługi Azure AD dla fikcyjnej organizacji.

Najpierw utwórz grupę zabezpieczeń z Azure Portal.

1. Utwórz oddzielną kartę w przeglądarce, a następnie przejdź do Azure Portal pod adresem [https://portal.azure.com](https://portal.azure.com). W razie potrzeby zaloguj się przy użyciu poświadczeń konta administratora globalnego dla Microsoft 365 E5 wersji próbnej lub płatnej subskrypcji.

2. W Azure Portal kliknij pozycję **grupy Azure Active Directory >**.

3. W bloku **Grupy — wszystkie grupy** kliknij pozycję **+ Nowa grupa**.

4. W bloku **Grupa** :

  - Wybierz pozycję **Zabezpieczenia** w **polu Typ grupy**.

  - Wpisz **C-Suite** w **polu Nazwa**.

  - Wybierz pozycję **Przypisano** **w polu Typ członkostwa**.

5. Kliknij **pozycję Utwórz**, a następnie zamknij blok **Grupa** .

Następnie skonfiguruj automatyczne licencjonowanie, aby członkowie nowej grupy **C-Suite** automatycznie przypisyli licencję Microsoft 365 E5.

1. W Azure Portal kliknij pozycję **Azure Active Directory > Licencje > Wszystkie produkty**.

2. Na liście wybierz pozycję **Microsoft 365 Enterprise E5**, a następnie kliknij pozycję **Przypisz**.

3. W bloku **Przypisywanie licencji** kliknij pozycję **Użytkownicy i grupy**.

4. Na liście grup wybierz grupę **C-Suite** .

5. Kliknij **pozycję Wybierz**, a następnie kliknij pozycję **Przypisz**.

6. Zamknij kartę Azure Portal w przeglądarce.

Następnie [połącz się z modułem Azure Active Directory Programu PowerShell dla Graph](../enterprise/connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Podaj nazwę organizacji, lokalizację i typowe hasło, a następnie uruchom te polecenia w wierszu polecenia programu PowerShell lub zintegrowanym środowisku skryptów (ISE), aby utworzyć nowe konta użytkowników i dodać je do grupy C-Suite:

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
> W tym miejscu jest używane typowe hasło do automatyzacji i ułatwienia konfiguracji środowiska deweloperskiego/testowego. Oczywiście jest to zdecydowanie odradzane w przypadku subskrypcji produkcyjnych.

Wykonaj te kroki, aby sprawdzić, czy licencjonowanie oparte na grupach działa poprawnie.

1. Zaloguj się do [Centrum administracyjnego usługi Microsoft 365](https://admin.microsoft.com).

2. Na nowej karcie **Centrum administracyjne platformy Microsoft 365** przeglądarki kliknij pozycję **Użytkownicy**.

3. Na liście użytkowników kliknij pozycję **DYREKTOR GENERALNY**.

4. W okienku zawierającym listę właściwości konta użytkownika **dyrektora generalnego** sprawdź, czy przypisano do niego licencję **Microsoft 365 Enterprise E5** w **licencjach produktu**.

## <a name="phase-3-create-your-team"></a>Faza 3. Tworzenie zespołu

W tej fazie utworzysz i skonfigurujesz zespół z izolacją zabezpieczeń dla członków zespołu kierowniczego wyższego szczebla, aby współpracowali nad strategią firmy.

Najpierw włącz etykiety poufności, aby chronić zawartość w witrynach Microsoft Teams, Office 365 i SharePoint przed wykonaniem kroków opisanych w [tym artykule](../compliance/sensitivity-labels-teams-groups-sites.md).

Następnie utwórz zespół:

1. W Teams kliknij **pozycję Teams** po lewej stronie aplikacji, a następnie kliknij **pozycję Dołącz lub utwórz zespół** w dolnej części listy zespołów.
2. Kliknij **pozycję Utwórz zespół** (pierwsza karta, lewy górny róg).
3. Wybierz **pozycję Skompiluj zespół od podstaw**.
4. Na liście **Czułość** zachowaj wartość domyślną.
5. W obszarze **Prywatność** kliknij pozycję **Prywatny**.
6. Wpisz **Strategię firmy**, a następnie kliknij pozycję **CreateClose** > .

Następnie ogranicz tworzenie kanałów prywatnych do właścicieli grupy Strategia firmy.

1. W zespole kliknij pozycję **Więcej opcji**, a następnie kliknij pozycję **Zarządzaj zespołem**.
2. Na karcie **Ustawienia** rozwiń pozycję **Uprawnienia członka**.
3. Wyczyść pole wyboru **Zezwalaj członkom na tworzenie kanałów prywatnych** .

Następnie należy skonfigurować etykietę poufności z następującymi ustawieniami:

- Nazwa to Strategia firmy
- Szyfrowanie jest włączone
- Grupa Strategia firmy ma uprawnienia Co-Author

Wykonaj następujące czynności:

1. Otwórz portal zgodności usługi Microsoft Purview w obszarze **Rozwiązania** wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Ochrona informacji**</a>.
1. Kliknij **pozycję Utwórz etykietę**.
1. Wpisz **Company Strategy (Strategia firmy** ) jako nazwę etykiety.
1. Wpisz **dokumenty strategii firmy dla kadry kierowniczej wyższego szczebla** jako poradę narzędzia, a następnie kliknij przycisk **Dalej**.
1. Na stronie **Szyfrowanie** na liście rozwijanej **Szyfrowanie** wybierz pozycję **Zastosuj**.
1. Aby dodać uprawnienia zespołu:<br>
  a. Kliknij **pozycję Przypisz uprawnienia**.<br>
  b. Kliknij **pozycję Dodaj użytkowników lub grupy**, wybierz pozycję **Strategia firmy**, a następnie kliknij pozycję **Dodaj**.<br>
  c. Kliknij **pozycję Wybierz uprawnienia**.<br>
  d. Wybierz pozycję **Współautor** z listy rozwijanej, a następnie kliknij przycisk **Zapisz**.<br>
1. Kliknij **Dalej**.
1. Na stronie **Oznaczanie zawartości** kliknij przycisk **Dalej**.
1. Na stronie **Ustawienia witryny i grupy** ustaw **pozycję Ustawienia witryny i grupy** **na wartość Włączone**.
1. Na liście rozwijanej **Prywatność Office 365 witryn zespołów połączonych z grupą** wybierz pozycję **Prywatne — tylko członkowie mogą uzyskać dostęp do witryny**.
1. W obszarze **Urządzenia niezarządzane** wybierz pozycję **Blokuj dostęp**.
1. Kliknij **Dalej**.
1. Na stronie **Automatyczne etykietowanie aplikacji Office** kliknij przycisk **Dalej**.
1. Kliknij pozycję **Prześlij**, a następnie kliknij pozycję **Gotowe**.

Następnie opublikuj nową etykietę, wykonując następujące kroki:

1. W portalu zgodności usługi Microsoft Purview na karcie <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Ochrona informacji**</a> wybierz kartę **Zasady etykiet** .
2. Kliknij pozycję **Publikuj etykiety**.
3. Na stronie **Wybieranie etykiet poufności do opublikowania** kliknij pozycję **Wybierz etykiety poufności do opublikowania**.
4. Wybierz pozycję **Strategia firmy**, a następnie kliknij pozycję **Dodaj**.
5. Kliknij **Dalej**.
6. Na stronie **Publikowanie dla użytkowników i grup** kliknij pozycję **Wybierz użytkowników i grupy**.
7. Kliknij **pozycję Dodaj**, a następnie wybierz pozycję **Strategia firmy**.
8. Kliknij **przycisk Dodaj**, a następnie kliknij przycisk **Gotowe**.
9. Kliknij **Dalej**.
10. Na stronie Ustawienia zasad zaznacz pole wyboru **Użytkownicy muszą podać uzasadnienie, aby usunąć etykietę lub niższą etykietę klasyfikacji** , a następnie kliknij przycisk **Dalej**.
11. Wpisz **wartość Company Strategy (Strategia firmy** ) jako nazwę zasad, a następnie kliknij przycisk **Dalej**.
12. Kliknij pozycję **Prześlij** , a następnie kliknij pozycję **Gotowe**.

Po opublikowaniu etykiety **Strategia firmy** może upłynąć trochę czasu.

Następnie zastosuj nową etykietę do zespołu **ds. strategii firmy** i zaktualizuj domyślny typ linku do udostępniania, aby zmniejszyć ryzyko przypadkowego udostępnienia plików i folderów szerszemu gronu odbiorców niż planowano.

1. Otwórz centrum administracyjne SharePoint w obszarze **Witryny** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
1. Wybierz witrynę **Strategia firmy** .
1. Na karcie **Zasady** w obszarze **Poufność** wybierz pozycję **Edytuj**.
1. Wybierz etykietę **Strategia firmy** , a następnie wybierz pozycję **Zapisz**.
1. Na karcie **Zasady** w obszarze **Udostępnianie zewnętrzne** wybierz pozycję **Edytuj**.
1. Wybierz **pozycję Tylko osoby w organizacji**.
1. W obszarze **Domyślny typ łącza udostępniania** wyczyść pole wyboru **To samo co ustawienie na poziomie organizacji** , a następnie wybierz pozycję **Osoby z istniejącym dostępem**.
1. Wybierz **Zapisz**.

Następnie skonfiguruj udostępnianie witryn tylko właścicielom dla zespołu **ds. strategii firmy** .

1. W Teams przejdź do karty **Ogólne** zespołu **ds. strategii firmy**.
2. Na pasku narzędzi dla zespołu kliknij pozycję **Pliki**.
3. Kliknij wielokropek, a następnie kliknij przycisk **Otwórz w SharePoint**.
4. Na pasku narzędzi bazowej witryny SharePoint kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
5. W okienku Uprawnienia witryny w obszarze **Udostępnianie witryny** kliknij pozycję **Zmień sposób udostępniania elementów członkowskich**.
6. W obszarze **Uprawnienia do udostępniania** wybierz pozycję **Tylko właściciele witryn mogą udostępniać pliki, foldery i witrynę,** a następnie kliknij przycisk **Zapisz**.
7. Zamknij **okienka Uprawnienia** i **Ustawienia**.

Jeśli zalogujesz się jako członek grupy Strategia firmy, zobaczysz opcję **Strategia firmy** w opcji **Czułość** na pasku narzędzi Narzędzia główne programu Word, Excel i PowerPoint. Wybierz etykietę **Strategia firmy** z opcji **Czułość** , aby przypisać etykietę do pliku.

Oto wynikowa konfiguracja zespołu ds. strategii firmy.

![Konfiguracja dla izolowanego zespołu ds. strategii firmy.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

## <a name="next-step"></a>Następny krok

Gdy wszystko będzie gotowe do wdrożenia produkcyjnego, zobacz te [instrukcje konfiguracji](secure-teams-security-isolation.md).
