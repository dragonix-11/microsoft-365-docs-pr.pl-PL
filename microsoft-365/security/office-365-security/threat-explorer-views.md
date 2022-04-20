---
title: Widoki eksploratora zagrożeń i wykrywanie w czasie rzeczywistym
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 05/15/2020
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Dowiedz się, jak używać Eksploratora zagrożeń i raportu wykrywania w czasie rzeczywistym do badania zagrożeń i reagowania na nie w portalu Microsoft 365 Defender.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ccc26bef5209dd297df0b3008b841edb56cdd160
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971159"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Widoki eksploratora zagrożeń i wykrywanie w czasie rzeczywistym

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

:::image type="content" source="../../media/explorer.png" alt-text="Strona Eksplorator zagrożeń" lightbox="../../media/explorer.png":::

[Eksplorator zagrożeń](threat-explorer.md) (i raport wykrywania w czasie rzeczywistym) to zaawansowane narzędzie niemal w czasie rzeczywistym, które ułatwia zespołom operacji zabezpieczeń badanie zagrożeń i reagowanie na nie w portalu Microsoft 365 Defender. Eksplorator (oraz raport dotyczący wykrywania w czasie rzeczywistym) wyświetla informacje o podejrzeniu złośliwego oprogramowania i phish w wiadomościach e-mail i plikach w Office 365, a także inne zagrożenia bezpieczeństwa i zagrożenia dla organizacji.

- Jeśli masz [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) plan 2, masz Eksploratora.
- Jeśli masz Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1, masz wykrywanie w czasie rzeczywistym.

Po pierwszym otwarciu Eksploratora (lub raportu wykrywania w czasie rzeczywistym) domyślny widok pokazuje wykrywanie złośliwego oprogramowania poczty e-mail w ciągu ostatnich 7 dni. Ten raport może również pokazywać wykrywanie Ochrona usługi Office 365 w usłudze Microsoft Defender, takie jak złośliwe adresy URL wykryte przez [linki Sejf](safe-links.md) i złośliwe pliki wykryte przez [Sejf Załączniki](safe-attachments.md). Ten raport można zmodyfikować w celu wyświetlenia danych z ostatnich 30 dni (z płatną subskrypcją Ochrona usługi Office 365 w usłudze Microsoft Defender P2). Subskrypcje wersji próbnej będą zawierać dane tylko z ostatnich siedmiu dni.

|Subskrypcji|Narzędzie|Dni danych|
|---|---|---|
|wersja próbna Ochrona usługi Office 365 w usłudze Microsoft Defender P1|Wykrywanie w czasie rzeczywistym|7|
|Ochrona usługi Office 365 w usłudze Microsoft Defender P1 płatne|Wykrywanie w czasie rzeczywistym|30|
|Ochrona usługi Office 365 w usłudze Microsoft Defender P1 — płatne testowanie Ochrona usługi Office 365 w usłudze Defender wersji próbnej P2|Eksplorator zagrożeń|7|
|wersja próbna Ochrona usługi Office 365 w usłudze Microsoft Defender P2|Eksplorator zagrożeń|7|
|Ochrona usługi Office 365 w usłudze Microsoft Defender P2 płatne|Eksplorator zagrożeń|30|

> [!NOTE]
> Wkrótce rozszerzymy przechowywanie danych Eksploratora (i wykrywanie w czasie rzeczywistym) i limit wyszukiwania dla dzierżaw wersji próbnej z 7 do 30 dni. Ta zmiana jest śledzona w ramach elementu planu nr 70544 i jest obecnie w fazie wdrażania.

Użyj menu **Widok** , aby zmienić wyświetlane informacje. Etykietki narzędzi ułatwiają określenie widoku do użycia.

:::image type="content" source="../../media/all-email.png" alt-text="Menu Widok Eksploratora zagrożeń" lightbox="../../media/all-email.png":::

Po wybraniu widoku można zastosować filtry i skonfigurować zapytania w celu przeprowadzenia dalszej analizy. Poniższe sekcje zawierają krótkie omówienie różnych widoków dostępnych w Eksploratorze (lub wykrywania w czasie rzeczywistym).

## <a name="email--malware"></a>Złośliwe oprogramowanie > poczty e-mail

Aby wyświetlić ten raport, w Eksploratorze (lub wykrywaniu w czasie rzeczywistym) wybierz pozycję **Wyświetl** \> **złośliwe oprogramowanie** **poczty e-mail**\>. Ten widok przedstawia informacje o wiadomościach e-mail, które zostały zidentyfikowane jako zawierające złośliwe oprogramowanie.

:::image type="content" source="../../media/detection-technology.png" alt-text="Widok danych dotyczących poczty e-mail zidentyfikowanych jako złośliwe oprogramowanie" lightbox="../../media/detection-technology.png":::

Kliknij **pozycję Nadawca** , aby otworzyć listę opcji wyświetlania. Ta lista służy do wyświetlania danych według nadawcy, adresatów, domeny nadawcy, tematu, technologii wykrywania, stanu ochrony i nie tylko.

Aby na przykład zobaczyć, jakie akcje zostały wykonane w przypadku wykrytych wiadomości e-mail, wybierz pozycję **Stan ochrony** na liście. Wybierz opcję, a następnie kliknij przycisk Odśwież, aby zastosować ten filtr do raportu.

:::image type="content" source="../../media/ThreatExplorerProtectionStatusOptions.png" alt-text="Opcje stanu ochrony przed zagrożeniami dla Eksploratora zagrożeń" lightbox="../../media/ThreatExplorerProtectionStatusOptions.png":::

Poniżej wykresu można wyświetlić więcej szczegółów dotyczących określonych komunikatów. Po wybraniu elementu na liście zostanie otwarte okienko wysuwane, w którym można dowiedzieć się więcej o wybranym elemencie.

:::image type="content" source="../../media/ThreatExplorerMalwareItemSelectedFlyout.png" alt-text="Eksplorator zagrożeń z otwartym wysuwem" lightbox="../../media/ThreatExplorerMalwareItemSelectedFlyout.png":::

## <a name="email--phish"></a>Poczta e-mail > Phish

Aby wyświetlić ten raport, w Eksploratorze (lub wykrywaniu w czasie rzeczywistym) wybierz pozycję **Wyświetl** \> **phish** **wiadomości e-mail**\>. Ten widok przedstawia wiadomości e-mail zidentyfikowane jako próby wyłudzania informacji.

:::image type="content" source="../../media/phish.png" alt-text="Wyświetlanie danych dotyczących poczty e-mail zidentyfikowanych jako próby wyłudzania informacji" lightbox="../../media/phish.png":::

Kliknij **pozycję Nadawca** , aby otworzyć listę opcji wyświetlania. Ta lista służy do wyświetlania danych przez nadawcę, adresatów, domenę nadawcy, adres IP nadawcy, domenę adresu URL, werdykt kliknięcia i nie tylko.

Aby na przykład zobaczyć, jakie akcje zostały podjęte po kliknięciu adresów URL zidentyfikowanych jako próby wyłudzania informacji, wybierz pozycję **Kliknij werdykt** na liście, wybierz jedną lub więcej opcji, a następnie kliknij przycisk Odśwież.

:::image type="content" source="../../media/click-verdict.png" alt-text="Opcje werdyktu Click dla raportu Phish" lightbox="../../media/click-verdict.png":::

Poniżej wykresu można wyświetlić więcej szczegółów dotyczących określonych komunikatów, kliknięć adresów URL, adresów URL i źródła wiadomości e-mail.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLs.png" alt-text="Adresy URL wykryte jako phish w wiadomościach e-mail" lightbox="../../media/ThreatExplorerEmailPhishURLs.png":::

Po wybraniu elementu na liście, takiego jak wykryty adres URL, zostanie otwarte okienko wysuwane, w którym można dowiedzieć się więcej o wybranym elemencie.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLDetails.png" alt-text="Szczegóły dotyczące wykrytego adresu URL" lightbox="../../media/ThreatExplorerEmailPhishURLDetails.png":::

## <a name="email--submissions"></a>Przesyłanie wiadomości e-mail >

Aby wyświetlić ten raport, w Eksploratorze (lub wykrywaniu w czasie rzeczywistym) wybierz pozycję **Wyświetl** \> **przesyłanie** **wiadomości e-mail**\>. Ten widok przedstawia wiadomości e-mail zgłaszane przez użytkowników jako wiadomości-śmieci, a nie wiadomości-śmieci lub wiadomości e-mail wyłudzające informacje.

:::image type="content" source="../../media/ThreatExplorerEmailUserReportedViewOptions.png" alt-text="Wiadomości e-mail zgłaszane przez użytkowników" lightbox="../../media/ThreatExplorerEmailUserReportedViewOptions.png":::

Kliknij **pozycję Nadawca** , aby otworzyć listę opcji wyświetlania. Ta lista służy do wyświetlania informacji według nadawcy, adresatów, typu raportu (określenie przez użytkownika, że wiadomość e-mail była wiadomością-śmieci, a nie wiadomości-śmieci lub phish) i nie tylko.

Aby na przykład wyświetlić informacje o wiadomościach e-mail zgłoszonych jako próby wyłudzania informacji, kliknij pozycję **Typ raportu** **nadawcy**\>, wybierz pozycję **Phish**, a następnie kliknij przycisk Odśwież.

![Phish wybrany dla filtru Typ raportu.](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Poniżej wykresu zobacz więcej szczegółów dotyczących określonych wiadomości e-mail, takich jak wiersz tematu, adres IP nadawcy, użytkownik, który zgłosił wiadomość jako wiadomość-śmieci, a nie wiadomości-śmieci lub phish i nie tylko.

:::image type="content" source="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png" alt-text="Komunikaty, które zostały zgłoszone jako próby wyłudzania informacji" lightbox="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png":::

Wybierz element z listy, aby wyświetlić dodatkowe szczegóły.

## <a name="email--all-email"></a>Wiadomość e-mail > wszystkie wiadomości e-mail

Aby wyświetlić ten raport, w Eksploratorze wybierz pozycję **Wyświetl** \> **pocztę e-mail** **Wszystkie wiadomości e-mail**\>. Te widoki przedstawiają cały widok aktywności poczty e-mail, w tym wiadomości e-mail zidentyfikowanych jako złośliwe ze względu na wyłudzanie informacji lub złośliwe oprogramowanie, a także wszystkie nie złośliwe wiadomości e-mail (zwykłe wiadomości e-mail, spam i wiadomości zbiorcze).

> [!NOTE]
> Jeśli wystąpi błąd odczytu **zbyt dużej ilości danych do wyświetlenia**, dodaj filtr i w razie potrzeby zawęż wyświetlany zakres dat.

Aby zastosować filtr, wybierz pozycję **Nadawca**, wybierz element z listy, a następnie kliknij przycisk Odśwież. W naszym przykładzie **użyto technologii wykrywania** jako filtru (dostępnych jest kilka opcji). Wyświetlaj informacje według nadawcy, domeny nadawcy, adresatów, podmiotu, nazwy pliku załącznika, rodziny złośliwego oprogramowania, stanu ochrony (działania podejmowane przez funkcje i zasady ochrony przed zagrożeniami w Office 365), technologii wykrywania (w jaki sposób wykryto złośliwe oprogramowanie) i nie tylko.

:::image type="content" source="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png" alt-text="Technologia View data about detected email by detection (Wyświetlanie danych o wykrytej wiadomości e-mail przez wykrywanie)" lightbox="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png":::

Poniżej wykresu można wyświetlić więcej szczegółów dotyczących określonych wiadomości e-mail, takich jak wiersz tematu, adresat, nadawca, stan itd.

## <a name="content--malware"></a>Złośliwe oprogramowanie > zawartości

Aby wyświetlić ten raport, w Eksploratorze (lub wykrywaniu w czasie rzeczywistym) wybierz pozycję **Wyświetl** \> **złośliwe oprogramowanie** **zawartości**\>. Ten widok przedstawia pliki, które zostały zidentyfikowane jako złośliwe przez [Ochrona usługi Office 365 w usłudze Microsoft Defender w usłudze SharePoint Online, OneDrive dla Firm i Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Wyświetl informacje według rodziny złośliwego oprogramowania, technologii wykrywania (jak wykryto złośliwe oprogramowanie) i obciążenia (OneDrive, SharePoint lub Teams).

:::image type="content" source="../../media/malware-family.png" alt-text="Widok danych o wykrytym złośliwym oprogramowaniu" lightbox="../../media/malware-family.png":::

Poniżej wykresu można wyświetlić więcej szczegółów dotyczących określonych plików, takich jak nazwa pliku załącznika, obciążenie, rozmiar pliku, kto ostatnio zmodyfikował plik i nie tylko.

## <a name="click-to-filter-capabilities"></a>Możliwości filtrowania kliknięć

Za pomocą Eksploratora (i wykrywania w czasie rzeczywistym) można zastosować filtr za pomocą kliknięcia. Kliknij element w legendzie, a ten element stanie się filtrem raportu. Załóżmy na przykład, że przeglądamy widok Złośliwe oprogramowanie w Eksploratorze:

:::image type="content" source="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png" alt-text="Strona Eksplorator w portalu zgodności & zabezpieczeń" lightbox="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png":::

Kliknięcie pozycji **Detonacja atp** na tym wykresie powoduje wyświetlenie następującego widoku:

:::image type="content" source="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png" alt-text="Eksplorator odfiltrowany w celu wyświetlenia tylko wyników detonacji Ochrona usługi Office 365 w usłudze Defender" lightbox="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png":::

W tym widoku analizujemy teraz dane dotyczące plików, które zostały zdetonowane przez [Sejf Załączniki](safe-attachments.md). Poniżej wykresu przedstawiono szczegółowe informacje o określonych wiadomościach e-mail z załącznikami, które zostały wykryte przez Sejf Załączniki.

:::image type="content" source="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png" alt-text="Szczegółowe informacje o wiadomościach e-mail z wykrytymi załącznikami" lightbox="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png":::

Wybranie co najmniej jednego elementu powoduje aktywowanie menu **Akcje** , które oferuje kilka opcji wyboru dla wybranych elementów.

:::image type="content" source="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png" alt-text="Proces wybierania elementu, który aktywuje menu Akcje" lightbox="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png":::

Możliwość filtrowania za pomocą kliknięcia i przechodzenia do określonych szczegółów może zaoszczędzić dużo czasu na badaniu zagrożeń.

## <a name="queries-and-filters"></a>Zapytania i filtry

Eksplorator (a także raport wykrywania w czasie rzeczywistym) ma kilka zaawansowanych filtrów i możliwości wykonywania zapytań, które umożliwiają przeglądanie szczegółowych informacji, takich jak najważniejsi użytkownicy docelowi, najważniejsze rodziny złośliwego oprogramowania, technologia wykrywania i inne. Każdy rodzaj raportu oferuje różne sposoby wyświetlania i eksplorowania danych.

> [!IMPORTANT]
> Nie używaj symboli wieloznacznych, takich jak gwiazdka lub znak zapytania, na pasku zapytania dla Eksploratora (lub wykrywania w czasie rzeczywistym). Podczas wyszukiwania w **polu Temat** wiadomości e-mail Eksplorator (lub wykrywanie w czasie rzeczywistym) będzie wykonywać częściowe dopasowywanie i zwracać wyniki podobne do wyszukiwania z symbolami wieloznacznymi.
