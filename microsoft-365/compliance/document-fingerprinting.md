---
title: Informacje o odciskach palców dokumentu
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
description: Pracownicy ds. informacji w organizacji obsługują wiele rodzajów poufnych informacji w typowy dzień. Odciski palców dokumentów ułatwiają ochronę tych informacji przez identyfikowanie standardowych formularzy używanych w całej organizacji. W tym temacie opisano pojęcia związane z odciskiem palca dokumentu i sposobem jego tworzenia przy użyciu programu PowerShell.
ms.openlocfilehash: 1ad29126783b9d824789b06020b8f925be00ffbb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627630"
---
# <a name="document-fingerprinting"></a>Tworzenie odcisków cyfrowych dokumentów

Pracownicy ds. informacji w organizacji obsługują wiele rodzajów poufnych informacji w typowy dzień. W portal zgodności Microsoft Purview odciski palców dokumentów ułatwiają ochronę tych informacji przez zidentyfikowanie standardowych formularzy używanych w całej organizacji. W tym temacie opisano pojęcia związane z odciskiem palca dokumentu i sposobem jego tworzenia przy użyciu programu PowerShell.

## <a name="basic-scenario-for-document-fingerprinting"></a>Podstawowy scenariusz pobierania odcisków palców dokumentu

Odcisk palca dokumentu to funkcja Ochrona przed utratą danych w Microsoft Purview (DLP), która konwertuje formularz standardowy na typ informacji poufnych, którego można użyć w regułach zasad DLP. Można na przykład utworzyć odcisk palca dokumentu na podstawie pustego szablonu patentu, a następnie utworzyć zasady DLP, które wykrywają i blokują wszystkie wychodzące szablony patentów z wypełnioną zawartością poufną. Opcjonalnie możesz skonfigurować [porady dotyczące zasad](use-notifications-and-policy-tips.md) , aby powiadamiać nadawców, że mogą wysyłać poufne informacje, a nadawca powinien sprawdzić, czy adresaci mają kwalifikacje do otrzymywania patentów. Ten proces współpracuje z dowolnymi formularzami tekstowymi używanymi w organizacji. Dodatkowe przykłady formularzy, które można przekazać, obejmują:

- Formularze rządowe
- Formularze zgodności ustawy HIPAA (Health Insurance Portability and Accountability Act)
- Formularze informacji o pracownikach dla działów kadr
- Formularze niestandardowe utworzone specjalnie dla Organizacji

W idealnym przypadku twoja organizacja ma już ustaloną praktykę biznesową polegającą na używaniu niektórych formularzy do przesyłania poufnych informacji. Po przekazaniu pustego formularza, który ma zostać przekonwertowany na odcisk palca dokumentu i skonfigurowaniu odpowiednich zasad, DLP wykrywa wszelkie dokumenty w wychodzącej wiadomości e-mail zgodnej z tym odciskiem palca.

## <a name="how-document-fingerprinting-works"></a>Jak działa odcisk palca dokumentu

Prawdopodobnie już wiesz, że dokumenty nie mają rzeczywistych odcisków palców, ale nazwa pomaga wyjaśnić tę funkcję. W ten sam sposób, w jaki odciski palców danej osoby mają unikatowe wzorce, dokumenty mają unikatowe wzorce słów. Podczas przekazywania pliku DLP identyfikuje unikatowy wzorzec wyrazów w dokumencie, tworzy odcisk palca dokumentu na podstawie tego wzorca i używa tego odcisku palca dokumentu do wykrywania dokumentów wychodzących zawierających ten sam wzorzec. Dlatego przekazanie formularza lub szablonu tworzy najbardziej efektywny typ odcisku palca dokumentu. Każdy, kto wypełnia formularz, używa tego samego oryginalnego zestawu słów, a następnie dodaje własne słowa do dokumentu. Jeśli dokument wychodzący nie jest chroniony hasłem i zawiera cały tekst z oryginalnego formularza, DLP może określić, czy dokument jest zgodny z odciskiem palca dokumentu.

> [!IMPORTANT]
> Na razie DLP może używać odcisków palców dokumentów jako metody wykrywania tylko w trybie online programu Exchange.

Poniższy przykład pokazuje, co się stanie, jeśli utworzysz odcisk palca dokumentu na podstawie szablonu patentu, ale możesz użyć dowolnego formularza jako podstawy do utworzenia odcisku palca dokumentu.

### <a name="example-of-a-patent-document-matching-a-document-fingerprint-of-a-patent-template"></a>Przykład dokumentu patentowego pasującego do odcisku palca dokumentu szablonu patentowego

![Diagram pobierania odcisków palców dokumentu.](../media/Document-Fingerprinting-diagram.png)

Szablon patentu zawiera puste pola "Tytuł patentu", "Wynalazcy" i "Opis" oraz opisy dla każdego z tych pól — to jest wzorzec słowa. Po przekazaniu oryginalnego szablonu patentowego jest on w jednym z obsługiwanych typów plików i w postaci zwykłego tekstu. DLP konwertuje ten wzorzec wyrazów na odcisk palca dokumentu, który jest małym plikiem XML Unicode zawierającym unikatową wartość skrótu reprezentującą oryginalny tekst, a odcisk palca jest zapisywany jako klasyfikacja danych w usłudze Active Directory. (Jako środek zabezpieczeń oryginalny dokument nie jest przechowywany w usłudze; przechowywana jest tylko wartość skrótu, a oryginalnego dokumentu nie można zrekonstruować na podstawie wartości skrótu). Odcisk palca patentu staje się następnie typem informacji poufnych, który można skojarzyć z zasadami DLP. Po skojarzeniu odcisku palca z zasadami DLP DLP wykrywa wszelkie wychodzące wiadomości e-mail zawierające dokumenty zgodne z odciskiem palca patentu i zajmuje się nimi zgodnie z zasadami organizacji.

Można na przykład skonfigurować zasady DLP, które uniemożliwiają zwykłym pracownikom wysyłanie wychodzących komunikatów zawierających patenty. DLP użyje odcisku palca patentu do wykrywania patentów i blokowania tych wiadomości e-mail. Możesz też zezwolić działowi prawnemu na wysyłanie patentów do innych organizacji, ponieważ ma to wymagać biznesowego. Możesz zezwolić określonym działom na wysyłanie poufnych informacji, tworząc wyjątki dla tych działów w zasadach DLP lub możesz zezwolić im na zastąpienie porady dotyczącej zasad uzasadnieniem biznesowym.

### <a name="supported-file-types"></a>Obsługiwane typy plików

Odciski palców dokumentu obsługują te same typy plików, które są obsługiwane w regułach przepływu poczty (nazywanych również regułami transportu). Aby uzyskać listę obsługiwanych typów plików, zobacz [Obsługiwane typy plików inspekcji zawartości reguł przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection). Jedna szybka uwaga dotycząca typów plików: ani reguły przepływu poczty, ani odciski palców dokumentów nie obsługują typu pliku dotx, co może być mylące, ponieważ jest to plik szablonu w programie Word. Jeśli w tym i innych tematach dotyczących odcisków palców dokumentu zostanie wyświetlone słowo "szablon", odnosi się ono do dokumentu ustanowionego jako standardowy formularz, a nie do typu pliku szablonu.

#### <a name="limitations-of-document-fingerprinting"></a>Ograniczenia pobierania odcisków palców dokumentów

Odcisk palca dokumentu nie wykrywa poufnych informacji w następujących przypadkach:

- Pliki chronione hasłem
- Pliki zawierające tylko obrazy
- Dokumenty, które nie zawierają całego tekstu z oryginalnego formularza użytego do utworzenia odcisku palca dokumentu
- Pliki większe niż 10 MB

## <a name="use-powershell-to-create-a-classification-rule-package-based-on-document-fingerprinting"></a>Tworzenie pakietu reguł klasyfikacji na podstawie odcisku palca dokumentu przy użyciu programu PowerShell

Obecnie można utworzyć odcisk palca dokumentu tylko w programie [PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell).

DLP używa pakietów reguł klasyfikacji do wykrywania poufnej zawartości. Aby utworzyć pakiet reguł klasyfikacji na podstawie odcisku palca dokumentu, użyj poleceń cmdlet **New-DlpFingerprint** i **New-DlpSensitiveInformationType** . Ponieważ wyniki polecenia **New-DlpFingerprint** nie są przechowywane poza regułą klasyfikacji danych, zawsze uruchamiane są polecenia **New-DlpFingerprint** i **New-DlpSensitiveInformationType** lub **Set-DlpSensitiveInformationType** w tej samej sesji programu PowerShell. Poniższy przykład tworzy nowy odcisk palca dokumentu na podstawie pliku C:\My Documents\Contoso Employee Template.docx. Nowy odcisk palca jest przechowywany jako zmienna, dzięki czemu można go używać z poleceniem cmdlet **New-DlpSensitiveInformationType** w tej samej sesji programu PowerShell.

```powershell
$Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
$Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

Teraz utwórzmy nową regułę klasyfikacji danych o nazwie "Contoso Employee Confidential", która używa odcisku palca dokumentu pliku C:\My Documents\Contoso Customer Information Form.docx.

```powershell
$Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
$Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
```

Teraz możesz użyć polecenia cmdlet **Get-DlpSensitiveInformationType** , aby znaleźć wszystkie pakiety reguł klasyfikacji danych DLP, a w tym przykładzie "Poufne dla klienta firmy Contoso" jest częścią listy pakietów reguł klasyfikacji danych.

Na koniec dodaj pakiet reguł klasyfikacji danych "Poufne dla klienta firmy Contoso" do zasad DLP w portal zgodności Microsoft Purview. Ten przykład dodaje regułę do istniejących zasad DLP o nazwie "ConfidentialPolicy".

```powershell
New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
```

Możesz również użyć pakietu reguł klasyfikacji danych w regułach przepływu poczty w Exchange Online, jak pokazano w poniższym przykładzie. Aby uruchomić to polecenie, musisz najpierw [nawiązać połączenie z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Należy również pamiętać, że synchronizacja pakietu reguł z portal zgodności Microsoft Purview do centrum administracyjnego programu Exchange zajmuje trochę czasu.

```powershell
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
```

DLP wykrywa teraz dokumenty zgodne z odciskiem palca dokumentu Form.docx klienta firmy Contoso.

Aby uzyskać informacje o składni i parametrach, zobacz:

- [New-DlpFingerprint](/powershell/module/exchange/New-DlpFingerprint)
- [New-DlpSensitiveInformationType](/powershell/module/exchange/New-DlpSensitiveInformationType)
- [Remove-DlpSensitiveInformationType](/powershell/module/exchange/Remove-DlpSensitiveInformationType)
- [Set-DlpSensitiveInformationType](/powershell/module/exchange/Set-DlpSensitiveInformationType)
- [Get-DlpSensitiveInformationType](/powershell/module/exchange/Get-DlpSensitiveInformationType)
