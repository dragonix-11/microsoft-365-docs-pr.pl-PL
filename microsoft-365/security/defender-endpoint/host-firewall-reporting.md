---
title: Hostuj raportowanie zapory w usłudze ochrony punktu końcowego w usłudze Microsoft Defender
description: Hostowanie i wyświetlanie raportowania zapory w portalu Microsoft 365 Defender.
keywords: Windows Defender, zapora
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 0dcb03a5398b38e05c3c7c867306444b17b8c720
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490237"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Hostuj raportowanie zapory w usłudze ochrony punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Jeśli jesteś administratorem globalnym lub administratorem zabezpieczeń, możesz teraz hostować raportowanie zapory w [portalu Microsoft 365 Defender](https://security.microsoft.com). Ta funkcja umożliwia wyświetlanie raportów zapory Windows 10, Windows 11, Windows Server 2019 i Windows Server 2022 ze scentralizowanej lokalizacji.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Musisz mieć uruchomione Windows 10, Windows 11, Windows Server 2019 lub Windows Server 2022.
- Aby dołączyć urządzenia do usługi Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [tutaj](onboard-configure.md).
- Aby <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalu</a>, aby rozpocząć odbieranie danych, należy włączyć opcję **Zdarzenia inspekcji** dla Zapora Windows Defender z zabezpieczeniami zaawansowanymi:
  - [Porzucanie pakietów platformy filtrowania inspekcji](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [Inspekcja połączenia platformy filtrowania](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- Włącz te zdarzenia przy użyciu edytora obiektów zasady grupy, zasad zabezpieczeń lokalnych lub poleceń auditpol.exe. Aby uzyskać więcej informacji, zobacz [tutaj](/windows/win32/fwp/auditing-and-logging).
  - Dwa polecenia programu PowerShell to:
    - `auditpol /set /subcategory:"Filtering Platform Packet Drop" /failure:enable`
    - `auditpol /set /subcategory:"Filtering Platform Connection" /failure:enable`

```powershell
param (
    [switch]$remediate
)
try {

    $categories = "Filtering Platform Packet Drop,Filtering Platform Connection"
    $current = auditpol /get /subcategory:"$($categories)" /r | ConvertFrom-Csv    
    if ($current."Inclusion Setting" -ne "failure") {
        if ($remediate.IsPresent) {
            Write-Host "Remediating. No Auditing Enabled. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})"
            $output = auditpol /set /subcategory:"$($categories)" /failure:enable
            if($output -eq "The command was successfully executed.") {
                Write-Host "$($output)"
                exit 0
            }
            else {
                Write-Host "$($output)"
                exit 1
            }
        }
        else {
            Write-Host "Remediation Needed. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})."
            exit 1
        }
    }

}
catch {
    throw $_
} 
```

## <a name="the-process"></a>Proces

> [!NOTE]
> Pamiętaj, aby postępować zgodnie z instrukcjami z powyższej sekcji i prawidłowo skonfigurować urządzenia pod kątem wczesnego uczestnictwa w wersji zapoznawczej.

- Po włączeniu zdarzeń Microsoft 365 Defender rozpocznie monitorowanie danych, w tym: 
   - Zdalny adres IP
   - Port zdalny
   - Port lokalny
   - Lokalny adres IP
   - Nazwa komputera
   - Przetwarzanie między połączeniami przychodzącymi i wychodzącymi
- Administratorzy mogą teraz zobaczyć działanie zapory [hosta](https://security.microsoft.com/firewall) systemu Windows tutaj.
   - Dodatkowe raportowanie można ułatwić, pobierając [skrypt raportowania niestandardowego](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) w celu monitorowania działań Zapora Windows Defender przy użyciu usługi Power BI.
   - Może upłynąć do 12 godzin, zanim dane zostaną odzwierciedlone.

## <a name="supported-scenarios"></a>Obsługiwane scenariusze

Następujące scenariusze są obsługiwane podczas wersji zapoznawczej Ring0:

- [Raportowanie zapory](#firewall-reporting)
- [Z pozycji "Komputery z zablokowanym połączeniem" do urządzenia](#from-computers-with-a-blocked-connection-to-device)
- [Przechodzenie do zaawansowanego wyszukiwania zagrożeń (odświeżanie w wersji zapoznawczej)](#drill-into-advanced-hunting-preview-refresh)

### <a name="firewall-reporting"></a>Raportowanie zapory

Oto kilka przykładów stron raportów zapory. Tutaj znajdziesz podsumowanie aktywności ruchu przychodzącego, wychodzącego i działania aplikacji. Dostęp do tej strony można uzyskać bezpośrednio, przechodząc do strony <https://security.microsoft.com/firewall>.

:::image type="content" source="images/host-firewall-reporting-page.png" alt-text="Strona Raportowanie zapory hosta" lightbox="\images\host-firewall-reporting-page.png":::

Dostęp do tych raportów można również uzyskać, przechodząc do sekcji **Urządzenia** > **raportów** >  zabezpieczeń **(sekcja**) znajdującej się w dolnej części karty **Połączenia przychodzące zablokowane przez zaporę**.

### <a name="from-computers-with-a-blocked-connection-to-device"></a>Z pozycji "Komputery z zablokowanym połączeniem" do urządzenia

Karty obsługują obiekty interakcyjne. Możesz przejść do szczegółów działania urządzenia, klikając nazwę urządzenia, która spowoduje uruchomienie portalu Microsoft 365 Defender na nowej karcie i przejście bezpośrednio na kartę **Oś czasu urządzenia**.

:::image type="content" source="images/firewall-reporting-blocked-connection.png" alt-text="Strona Komputery z zablokowanym połączeniem" lightbox="\images\firewall-reporting-blocked-connection.png":::

Teraz możesz wybrać kartę **Oś czasu** , która udostępnia listę zdarzeń skojarzonych z tym urządzeniem.

Po kliknięciu przycisku **Filtry** w prawym górnym rogu okienka wyświetlania wybierz odpowiedni typ zdarzenia. W takim przypadku wybierz pozycję **Zdarzenia zapory** , a okienko będzie filtrowane do zdarzeń zapory.

:::image type="content" source="images/firewall-reporting-filters-button.png" alt-text="Przycisk Filtry" lightbox="\images\firewall-reporting-filters-button.png":::

### <a name="drill-into-advanced-hunting-preview-refresh"></a>Przechodzenie do zaawansowanego wyszukiwania zagrożeń (odświeżanie w wersji zapoznawczej)

Raporty zapory obsługują przechodzenie do szczegółów z karty bezpośrednio w obszarze **Zaawansowane wyszukiwanie zagrożeń** , klikając przycisk **Otwórz zaawansowane wyszukiwanie zagrożeń** . Zapytanie zostanie wstępnie wypełnione.

:::image type="content" source="images/firewall-reporting-advanced-hunting.png" alt-text="Przycisk Otwórz zaawansowane wyszukiwanie zagrożeń" lightbox="\images\firewall-reporting-advanced-hunting.png":::

Zapytanie można teraz wykonać, a wszystkie powiązane zdarzenia zapory z ostatnich 30 dni można zbadać.

Aby uzyskać więcej raportów lub zmian niestandardowych, zapytanie można wyeksportować do usługi Power BI w celu dalszej analizy. Raportowanie niestandardowe można ułatwić, pobierając [skrypt raportowania niestandardowego](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) w celu monitorowania działań Zapora Windows Defender przy użyciu usługi Power BI.
