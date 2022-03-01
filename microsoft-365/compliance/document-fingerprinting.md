---
title: Linie papilarne dokumentów
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
search.appverid: MET150
ms.service: exchange-online
ms.collection: M365-security-compliance
ms.localizationpriority: medium
description: Pracownicy informacji w Twojej organizacji obsługują wiele rodzajów informacji poufnych w trakcie typowego dnia. Linie papilarne dokumentów ułatwiają ochronę tych informacji przez identyfikowanie standardowych formularzy używanych w całej organizacji. W tym temacie opisano pojęcia dotyczące funkcji odcisku palca w dokumencie i sposobu jej tworzenia przy użyciu programu PowerShell.
ms.openlocfilehash: cd75fe8ec8f4c727f86689cd3a46f331e71afdad
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009689"
---
# <a name="document-fingerprinting"></a>Linie papilarne dokumentów

Pracownicy informacji w Twojej organizacji obsługują wiele rodzajów informacji poufnych w trakcie typowego dnia. W Centrum zgodności zabezpieczeń &amp; funkcje linii papilarnych dokumentów ułatwiają ochronę tych informacji, identyfikując standardowe formularze używane w całej organizacji. W tym temacie opisano pojęcia dotyczące funkcji odcisku palca w dokumencie i sposobu jej tworzenia przy użyciu programu PowerShell.

## <a name="basic-scenario-for-document-fingerprinting"></a>Podstawowy scenariusz odcisku palca w dokumencie

Funkcja rozpoznawania linii papilarnych w dokumencie to funkcja ochrony przed utratą danych (DLP, Data Loss Prevention), która konwertuje standardowy formularz na typ informacji poufnych, którego można używać w zasadach ochrony przed utratą danych. Na przykład możesz utworzyć dokument odcisku palca na podstawie pustego szablonu patentu, a następnie utworzyć zasady DLP, które wykrywają i blokują wszystkie wychodzące szablony patentów z wypełnioną poufnymi zawartością. Opcjonalnie możesz skonfigurować porady dotyczące zasad [](use-notifications-and-policy-tips.md) w celu powiadomienia nadawców, że mogą oni wysyłać informacje poufne, a nadawca powinien sprawdzić, czy adresaci są kwalifikowani do otrzymywania patentów. Ten proces dotyczy wszystkich formularzy tekstowych używanych w organizacji. Oto dodatkowe przykłady formularzy, które można przekazać:

- Formularze rządowe
- Formularze zgodności ustawy HIPAA (Health Insurance Portability and Accountability Act)
- Formularze informacji o pracownikach dla działów kadr
- Formularze niestandardowe utworzone specjalnie dla Twojej organizacji

Najlepiej, jeśli Twoja organizacja ma już ustanowione praktyki biznesowe dotyczące przekazywania informacji poufnych za pomocą określonych formularzy. Po przesłaniu pustego formularza w celu przekonwertowania go na linie papilarne dokumentu i skonfigurowaniu odpowiednich zasad zasady DLP wykrywa wszystkie dokumenty poczty wychodzącej zgodne z tym odciskiem palca.

## <a name="how-document-fingerprinting-works"></a>Jak działa odciski palca w dokumencie

Prawdopodobnie domyślasz się, że dokumenty nie mają rzeczywistych linii papilarnych, ale sama nazwa wyjaśnia tę funkcję. Podobnie jak linie papilarne osoby mają unikatowe desenie, dokumenty mają unikatowe wzorce wyrazów. Podczas przekazywania pliku technologia DLP identyfikuje unikatowy wzorzec wyrazów w dokumencie, tworzy odcisk palca w dokumencie na podstawie tego wzorca i używa tego odcisku palca w dokumencie do wykrycia dokumentów wychodzących zawierających ten sam wzorzec. Dlatego przekazanie formularza lub szablonu powoduje utworzenie najbardziej efektywnego typu odcisku palca w dokumencie. Każda osoba wypełniająca formularz używa tego samego oryginalnego zestawu wyrazów, a następnie dodaje swoje własne wyrazy do dokumentu. Jeśli dokument ruchu wychodzącego nie jest chroniony hasłem i zawiera cały tekst z oryginalnej formy, ochrona przed kodem DLP może określać, czy dokument jest zabezpieczony od linii papilarnych dokumentu.

> [!IMPORTANT]
> Obecnie technologia DLP może korzystać z funkcji rozpoznawania linii papilarnych dokumentu jako metody wykrywania w Exchange tylko w trybie online.

W poniższym przykładzie pokazano, co się stanie, jeśli utworzysz dokument odcisku palca na podstawie szablonu patentu, ale możesz użyć dowolnej formy jako podstawy do utworzenia odcisku palca w dokumencie.

### <a name="example-of-a-patent-document-matching-a-document-fingerprint-of-a-patent-template"></a>Przykład dokumentu patentowego pasującego do odcisku palca dokumentu w szablonie patentu

![Diagram odcisku palca w dokumencie.](../media/Document-Fingerprinting-diagram.png)

Szablon patentowy zawiera puste pola "Tytuł patentu", "Spiscy" i "Opis" oraz opisy każdego z tych pól — to jest wzorzec wyrazów. Po przesłaniu oryginalnego szablonu patentu jest on w jednym z obsługiwanych typów plików i zawiera zwykły tekst. Funkcja DLP konwertuje wzorzec wyrazów na linie papilarne dokumentu, mały plik XML Unicode zawierający unikatową wartość skrótu reprezentującą oryginalny tekst, a odcisk palca jest zapisywany jako klasyfikacja danych w usłudze Active Directory. Ze względów bezpieczeństwa oryginalny dokument nie jest przechowywany w usłudze; jest przechowywana tylko wartość skrótu i nie można odtworzyć oryginalnego dokumentu na podstawie wartości skrótu. Linii papilarnych patentu staje się wówczas typem informacji poufnych, który można skojarzyć z zasadami DLP. Po skojarzeniu odcisku palca z zasadami DLP, technologia DLP wykrywa wszystkie wychodzące wiadomości e-mail zawierające dokumenty zgodne z odciskiem palca patentu i transakcji z nimi zgodnie z zasadami organizacji.

Na przykład możesz chcieć skonfigurować zasady DLP uniemożliwiające pracownikom wysyłanie wiadomości wychodzących zawierających patenty. Technologia DLP będzie używać linii papilarnych patentów do wykrywania patentów i blokowania tych wiadomości e-mail. Alternatywnie możesz zechcieć, aby dział prawny mógł wysyłać patenty do innych organizacji, ponieważ ma do tego biznesowe potrzeby. Możesz zezwolić określonym działom na wysyłanie poufnych informacji, tworząc wyjątki dla tych działów w Twoich zasadach ochrony przed zasadami DLP lub zezwolić im na zastępowanie porady dotyczącej zasad uzasadnieniem biznesowym.

### <a name="supported-file-types"></a>Obsługiwane typy plików

Linie papilarne dokumentów obsługują te same typy plików, które są obsługiwane w zasadach przepływu poczty e-mail (nazywanych również regułami transportu). Aby uzyskać listę obsługiwanych typów plików, zobacz Obsługiwane typy plików do [inspekcji zawartości reguł przepływu poczty e-mail](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection). Jedna szybka uwaga na temat typów plików: ani reguły przepływu poczty, ani funkcja odcisku palca w dokumencie nie obsługują typu pliku dotx, co może być mylące, ponieważ jest to plik szablonu w programie Word. Wyraz "szablon" w tym i innych tematach dotyczących odcisku palca w dokumencie oznacza dokument ustalony jako formularz standardowy, a nie typ pliku szablonu.

#### <a name="limitations-of-document-fingerprinting"></a>Ograniczenia odcisku palca w dokumencie

W następujących przypadkach za pomocą odcisku palca w dokumencie nie są wykrywane informacje poufne:

- Pliki chronione hasłem
- Pliki zawierające tylko obrazy
- Dokumenty, które nie zawierają całego tekstu z oryginalnego formularza użytego do utworzenia odcisku palca w dokumencie
- Pliki o rozmiarze większym niż 10 MB

## <a name="use-powershell-to-create-a-classification-rule-package-based-on-document-fingerprinting"></a>Tworzenie pakietu reguł klasyfikacji na podstawie odcisku palca w dokumencie za pomocą programu PowerShell

Obecnie odcisk palca dokumentu można utworzyć tylko w centrum [zabezpieczeń & w programie PowerShell](/powershell/exchange/connect-to-scc-powershell).

W aplikacji DLP pakiety reguł klasyfikacji są używane do wykrywania poufnej zawartości. Aby utworzyć pakiet reguł klasyfikacji na podstawie odcisku palca dokumentu, użyj polecenia cmdlet **New-DlpFingerprint** i **New-DlpSensitiveInformationType** . Ponieważ wyniki **new-DlpFingerprint** nie są przechowywane poza regułą klasyfikacji danych, zawsze uruchamiaj **new-DlpFingerprint** i **New-DlpSensitiveInformationType** lub **Set-DlpSensitiveInformationType** w tej samej sesji programu PowerShell. Poniższy przykład tworzy nowy odcisk palca dokumentu na podstawie pliku C:\Moje dokumenty\Contoso — dane Template.docx. Nowy odcisk palca jest zapisywany jako zmienna, więc można go używać z poleceniem cmdlet **New-DlpSensitiveInformationType** w tej samej sesji programu PowerShell.

```powershell
$Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
$Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

Teraz utworzymy nową regułę klasyfikacji danych o nazwie "Poufne dane pracowników firmy Contoso", która korzysta z odcisku palca dokumentu w pliku C:\Moje dokumenty\Contoso — informacje o klientach Form.docx.

```powershell
$Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
$Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
```

Teraz możesz użyć polecenia cmdlet **Get-DlpSensitiveInformationType** , aby znaleźć wszystkie pakiety reguł klasyfikacji danych DLP, a w tym przykładzie "Poufne dane klienta Contoso" stanowi część listy pakietów reguł klasyfikacji danych.

Na koniec dodaj pakiet reguł klasyfikacji danych "Poufne dane klienta Contoso" do zasad DLP w Centrum &amp; zgodności zabezpieczeń. W tym przykładzie dodano regułę do istniejących zasad DLP o nazwie "ConfidentialPolicy".

```powershell
New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
```

Możesz również użyć pakietu reguł klasyfikacji danych w regułach przepływu poczty e-mail Exchange Online, jak pokazano w poniższym przykładzie. Aby uruchomić to polecenie, musisz najpierw uruchomić [Połączenie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pamiętaj też, że synchronizowanie pakietu reguł &amp; z Centrum zgodności zabezpieczeń do centrum administracyjnego programu Exchange może trwać dłużej.

```powershell
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
```

Dzięki zasadom DLP dokumenty są teraz wykrywane na podstawie odcisku palca Form.docx firmy Contoso.

Aby uzyskać informacje o składni i parametrach, zobacz:

- [New-DlpFingerprint](/powershell/module/exchange/New-DlpFingerprint)
- [New-DlpSensitiveInformationType](/powershell/module/exchange/New-DlpSensitiveInformationType)
- [Remove-DlpSensitiveInformationType](/powershell/module/exchange/Remove-DlpSensitiveInformationType)
- [Set-DlpSensitiveInformationType](/powershell/module/exchange/Set-DlpSensitiveInformationType)
- [Get-DlpSensitiveInformationType](/powershell/module/exchange/Get-DlpSensitiveInformationType)
