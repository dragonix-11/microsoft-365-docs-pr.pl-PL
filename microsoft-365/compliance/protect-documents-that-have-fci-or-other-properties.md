---
title: Tworzenie zasad DLP w celu ochrony dokumentów
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContentPropertyContainsWords
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkSPO
description: Dowiedz się, jak za pomocą zasad ochrony przed utratą danych (DLP) chronić dokumenty, które mają właściwości z systemu innej firmy.
ms.openlocfilehash: c57a7b60377cf401a0e29e33ce524c4180b9f725
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626364"
---
# <a name="create-a-dlp-policy-to-protect-documents-with-fci-or-other-properties"></a>Twórz zasady DLP w celu ochrony dokumentów z właściwościami FCI lub innymi

zasady Ochrona przed utratą danych w Microsoft Purview (DLP) mogą używać właściwości klasyfikacji lub właściwości elementów do identyfikowania poufnych elementów. Można na przykład użyć następujących elementów:

- Właściwości infrastruktury klasyfikacji plików (FCI) systemu Windows Server
- Właściwości dokumentu programu SharePoint
- Właściwości dokumentu systemu innej firmy

![Diagram przedstawiający Office 365 i zewnętrzny system klasyfikacji.](../media/59ad0ac1-4146-4919-abd1-c74d8508d25e.png)

Na przykład organizacja może używać interfejsu FCI systemu Windows Server do identyfikowania elementów z danymi osobowymi, takimi jak numery ubezpieczenia społecznego, a następnie klasyfikować dokument, ustawiając właściwość **Dane osobowe** na **wartość Wysoka**, **Umiarkowana**, **Niska**, **Publiczna** lub **Nie** , na podstawie typu i liczby wystąpień danych osobowych znalezionych w dokumencie.

W usłudze Microsoft 365 można utworzyć zasady DLP identyfikujące dokumenty, które mają tę właściwość ustawioną na określone wartości, takie jak **Wysokie** i **Średnie**, a następnie wykonać akcję, taką jak blokowanie dostępu do tych plików. Te same zasady mogą mieć inną regułę, która wykonuje inną akcję, jeśli właściwość jest ustawiona na **Wartość Niska**, na przykład wysyłanie powiadomienia e-mail. W ten sposób DLP integruje się z interfejsem FCI systemu Windows Server i może pomóc w ochronie dokumentów pakietu Office przekazanych lub udostępnionych do platformy Microsoft 365 z serwerów plików opartych na systemie Windows Server.

Zasady DLP po prostu szukają określonej pary nazw/wartości właściwości. Można użyć dowolnej właściwości dokumentu, o ile właściwość ma odpowiednią właściwość zarządzaną dla wyszukiwania programu SharePoint. Na przykład zbiór witryn programu SharePoint może używać typu zawartości o nazwie **Trip Report** z wymaganym polem o nazwie **Klient**. Za każdym razem, gdy dana osoba tworzy raport podróży, musi wprowadzić nazwę klienta. Tej pary nazwy/wartości właściwości można również użyć w zasadach DLP — na przykład jeśli chcesz mieć regułę, która blokuje dostęp do dokumentu dla gości, gdy pole **Klient** zawiera firmę **Contoso**.

Jeśli chcesz zastosować zasady DLP do zawartości z określonymi etykietami platformy Microsoft 365, nie należy postępować zgodnie z poniższymi krokami. Zamiast tego dowiedz się, jak [używać etykiety przechowywania jako warunku w zasadach DLP](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

## <a name="before-you-create-the-dlp-policy"></a>Przed utworzeniem zasad DLP

Aby można było użyć właściwości fci systemu Windows Server lub innej właściwości w zasadach DLP, musisz utworzyć właściwość zarządzaną w <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnym programu SharePoint</a>. Oto dlaczego.

W usłudze SharePoint Online i OneDrive dla Firm indeks wyszukiwania jest kompilowany przez przeszukiwanie zawartości w witrynach. Przeszukiwarka pobiera zawartość i metadane z dokumentów w postaci przeszukanych właściwości. Schemat wyszukiwania pomaga przeszukiwarce zdecydować, jaką zawartość i metadane należy pobrać. Przykładami metadanych są autor i tytuł dokumentu. Jednak aby pobrać zawartość i metadane z dokumentów do indeksu wyszukiwania, przeszukane właściwości muszą być mapowane na właściwości zarządzane. W indeksie są przechowywane tylko właściwości zarządzane. Na przykład właściwość przeszukana powiązana z autorem jest mapowana na właściwość zarządzaną powiązaną z autorem.

> [!NOTE]
> Podczas tworzenia reguł DLP przy użyciu warunku należy użyć nazwy właściwości zarządzanej, a nie nazwy właściwości przeszukanej `ContentPropertyContainsWords` .

Jest to ważne, ponieważ DLP używa przeszukiwarki do identyfikowania i klasyfikowania poufnych informacji w witrynach, a następnie przechowywania tych poufnych informacji w bezpiecznej części indeksu wyszukiwania. Podczas przekazywania dokumentu do Office 365 program SharePoint automatycznie tworzy właściwości przeszukane na podstawie właściwości dokumentu. Jednak aby użyć interfejsu FCI lub innej właściwości w zasadach DLP, właściwość przeszukana musi zostać zamapowana na właściwość zarządzaną, aby zawartość z tą właściwością była przechowywana w indeksie.

Aby uzyskać więcej informacji na temat wyszukiwania i właściwości zarządzanych, zobacz [Zarządzanie schematem wyszukiwania w usłudze SharePoint Online](/sharepoint/manage-search-schema).

### <a name="step-1-upload-a-document-with-the-needed-property-to-office-365"></a>Krok 1. Przekazywanie dokumentu z wymaganą właściwością do Office 365

Najpierw musisz przekazać dokument z właściwością, do której chcesz się odwołać w zasadach DLP. Platforma Microsoft 365 wykryje właściwość i automatycznie utworzy z niej właściwość przeszukaną. W następnym kroku utworzysz właściwość zarządzaną, a następnie zmapujesz właściwość zarządzaną na tę właściwość przeszukaną.

### <a name="step-2-create-a-managed-property"></a>Krok 2. Tworzenie właściwości zarządzanej

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjnego usługi Microsoft 365</a>.

2. W obszarze nawigacji po lewej stronie wybierz **pozycję Administracja centrów** \> **programu SharePoint**. Jesteś teraz w <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centrum administracyjnym programu SharePoint</a>.

3. W obszarze nawigacji po lewej stronie wybierz **pozycję wyszukaj** \> na stronie \> **administracji wyszukiwania** **Zarządzaj schematem wyszukiwania**.

   ![strona administracji wyszukiwania w centrum administracyjnym programu SharePoint.](../media/6bcd3aec-d11a-4f8c-9987-8f35da14d80b.png)

4. Na stronie \> **Właściwości zarządzane** **Nowa właściwość zarządzana**.

   ![Strona Właściwości zarządzane z wyróżnionym przyciskiem Nowa właściwość zarządzana.](../media/b161c764-414c-4037-83ed-503a49fb4410.png)

5. Wprowadź nazwę i opis właściwości. Ta nazwa będzie wyświetlana w zasadach DLP.

6. W polu **Typ** wybierz pozycję **Tekst**.

7. W obszarze **Główne cechy** wybierz pozycję **Queryable** i **Retrievable**.

8. W obszarze **Mapowania na właściwości** \> przeszukane **Dodaj mapowanie**.

9. W oknie dialogowym \> **wyboru właściwości przeszukanej** znajdź i wybierz właściwość przeszukaną, która odpowiada właściwości FCI systemu Windows Server lub innej właściwości, która będzie używana w zasadach \> DLP **OK**.

   ![okno dialogowe wyboru właściwości przeszukanej.](../media/aeda1dce-1342-48bf-9594-a8e4f230e8aa.png)

10. W dolnej części strony \> **OK**.

## <a name="create-a-dlp-policy-that-uses-an-fci-property-or-other-property"></a>Tworzenie zasad DLP używających właściwości FCI lub innej właściwości

W tym przykładzie organizacja używa infrastruktury fci na serwerach plików opartych na systemie Windows Server; W szczególności używają właściwości klasyfikacji fci o nazwie **Dane osobowe** z możliwymi wartościami **wysokiego**, **umiarkowanego**, **niskiego**, **publicznego** i **nie pii**. Teraz chcą używać istniejącej klasyfikacji fci w swoich zasadach DLP w Office 365.

Najpierw wykonaj powyższe kroki, aby utworzyć właściwość zarządzaną w usłudze SharePoint Online, która jest mapowana na właściwość przeszukaną utworzoną automatycznie na podstawie właściwości FCI.

Następnie tworzą zasady DLP z dwiema regułami, które używają warunku **Właściwości dokumentu zawierają dowolną z tych wartości**:

- **Zawartość interfejsu PII fci — wysoka, umiarkowana** Pierwsza reguła ogranicza dostęp do dokumentu, jeśli właściwość klasyfikacji fci **dane osobowe** są równe **Wysoki** lub **Umiarkowany** , a dokument jest udostępniany osobom spoza organizacji.

- **Zawartość interfejsu PII usługi FCI — niska** Druga reguła wysyła powiadomienie do właściciela dokumentu, jeśli właściwość klasyfikacji fci **Dane osobowe** jest równa **Niska** , a dokument jest udostępniany osobom spoza organizacji.

### <a name="create-the-dlp-policy-by-using-security--compliance-powershell"></a>Tworzenie zasad DLP przy użyciu programu PowerShell & zgodności z zabezpieczeniami

Warunek **Właściwości dokumentu zawierający dowolną z tych wartości jest tymczasowo niedostępny** w portal zgodności Microsoft Purview, ale nadal możesz użyć tego warunku w programie PowerShell Security & Compliance. Za pomocą `New\Set\Get-DlpCompliancePolicy` poleceń cmdlet można pracować z zasadami DLP i używać `New\Set\Get-DlpComplianceRule` poleceń cmdlet z parametrem `ContentPropertyContainsWords` , aby dodać warunek **Właściwości dokumentu zawierają dowolną z tych wartości**.

1. [Nawiązywanie połączenia z programem PowerShell zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell)

2. Utwórz zasady przy użyciu polecenia `New-DlpCompliancePolicy`.

   Ten program PowerShell tworzy zasady DLP, które mają zastosowanie do wszystkich lokalizacji.

   ```powershell
   New-DlpCompliancePolicy -Name FCI_PII_policy -ExchangeLocation All -SharePointLocation All -OneDriveLocation All -Mode Enable
   ```

3. Utwórz dwie reguły opisane powyżej przy użyciu `New-DlpComplianceRule`polecenia , gdzie jedna reguła dotyczy wartości **Niska** , a druga dla wartości **Wysoki** i **Umiarkowany** .

   Oto przykład programu PowerShell, który tworzy te dwie reguły. Pary nazw/wartości właściwości są ujęte w cudzysłów, a nazwa właściwości może określać wiele wartości rozdzielonych przecinkami bez spacji, takich jak `"<Property1>:<Value1>,<Value2>","<Property2>:<Value3>,<Value4>"....`

   ```powershell
   New-DlpComplianceRule -Name FCI_PII_content-High,Moderate -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $true -ContentPropertyContainsWords "Personally Identifiable Information:High,Moderate" -Disabled $falseNew-DlpComplianceRule -Name FCI_PII_content-Low -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $false -ContentPropertyContainsWords "Personally Identifiable Information:Low" -Disabled $false -NotifyUser Owner
   ```

   Interfejs FCI systemu Windows Server zawiera wiele wbudowanych właściwości, w tym **dane osobowe** używane w tym przykładzie. Możliwe wartości dla każdej właściwości mogą być różne dla każdej organizacji. Używane tutaj wartości **Wysoki**, **Umiarkowany** i **Niski** są tylko przykładem. W organizacji można wyświetlić właściwości klasyfikacji fci systemu Windows Server z ich możliwych wartości w Resource Manager serwera plików na serwerze plików opartym na systemie Windows Server. Aby uzyskać więcej informacji, zobacz [Tworzenie właściwości klasyfikacji](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759215(v=ws.11)).

Po zakończeniu zasady powinny mieć dwie nowe reguły, które używają **właściwości Dokumentu zawierają dowolny z tych warunków wartości** . Ten warunek nie będzie wyświetlany w interfejsie użytkownika, ale zostaną wyświetlone inne warunki, akcje i ustawienia.

Jedna reguła blokuje dostęp do zawartości, w której właściwość **Personally Identifiable Information** jest równa **wysokiemu** lub **umiarkowanemu**. Druga reguła wysyła powiadomienie o zawartości, w której **właściwość Personally Identifiable Information** jest równa **Niski**.

![Nowe okno dialogowe zasad DLP z wyświetloną dwiema właśnie utworzonymi regułami.](../media/5c56c13b-62a5-4f25-8eb7-ce83a844bb12.png)

## <a name="after-you-create-the-dlp-policy"></a>Po utworzeniu zasad DLP

Wykonanie kroków w poprzednich sekcjach spowoduje utworzenie zasad DLP, które szybko wykryje zawartość z tą właściwością, ale tylko wtedy, gdy ta zawartość zostanie nowo przekazana (tak, aby zawartość została zaindeksowana) lub jeśli ta zawartość jest stara, ale po prostu edytowana (aby zawartość została ponownie zindeksowana).

Aby wykryć zawartość z tą właściwością wszędzie, możesz ręcznie zażądać ponownego indeksowania biblioteki, witryny lub zbioru witryn, aby zasady DLP wiedziały o całej zawartości z tą właściwością. W usłudze SharePoint Online zawartość jest automatycznie przeszukiwana na podstawie zdefiniowanego harmonogramu przeszukiwania. Przeszukiwarka pobiera zawartość, która uległa zmianie od czasu ostatniego przeszukiwania, i aktualizuje indeks. Jeśli potrzebujesz zasad DLP, aby chronić zawartość przed następnym zaplanowanym przeszukiwaniem, możesz wykonać te kroki.

> [!CAUTION]
> Ponowne indeksowanie witryny może spowodować ogromne obciążenie systemu wyszukiwania. Nie indeksuj ponownie witryny, chyba że scenariusz tego absolutnie wymaga.

Aby uzyskać więcej informacji, zobacz [Ręczne przeszukiwanie żądań i ponowne indeksowanie witryny, biblioteki lub listy](/sharepoint/crawl-site-content).

### <a name="reindex-a-site-optional"></a>Ponowne indeksowanie lokacji (opcjonalnie)

1. W witrynie wybierz pozycję **Ustawienia** (ikona koła zębatego w prawym górnym rogu) \> **Ustawienia witryny**.

2. W obszarze **Wyszukaj** wybierz pozycję **Wyszukaj i dostępność** \> w trybie offline **.**

## <a name="more-information"></a>Więcej informacji

- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)

- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)

- [Wysyłanie powiadomień i wyświetlanie wskazówek dotyczących zasad dotyczących zasad DLP](use-notifications-and-policy-tips.md)

- [Co obejmują szablony zasad DLP](what-the-dlp-policy-templates-include.md)

- [Definicje jednostek typu informacji poufnych](sensitive-information-type-entity-definitions.md)
