---
title: Widoki w Eksploratorze zagrożeń i wykrywania w czasie rzeczywistym
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
description: Dowiedz się, jak korzystać z Eksploratora zagrożeń i raportu wykrywanie w czasie rzeczywistym w celu zbadania zagrożeń i reagowania na nie w Microsoft 365 Defender sieci.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d21773694e1dc9472a9a8ac566c8eaacc00fcab8
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682862"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Widoki w Eksploratorze zagrożeń i wykrywania w czasie rzeczywistym

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


![Eksplorator zagrożeń.](../../media/explorer.png)

[Eksplorator zagrożeń](threat-explorer.md) (oraz raport wykrywania w czasie rzeczywistym) to zaawansowane narzędzie w czasie rzeczywistym, które pomaga zespołom operacji zabezpieczeń badać zagrożenia i odpowiadać na nie w portalu Microsoft 365 Defender rzeczywistym. W Eksploratorze (i raporcie wykrywania w czasie rzeczywistym) są wyświetlane informacje o podejrzanym złośliwym oprogramowaniu i wyłudzeniu informacji w wiadomościach e-mail i plikach w programie Office 365, a także o innych zagrożeniach i zagrożeniach bezpieczeństwa twojej organizacji.

- Jeśli masz program [Microsoft Defender dla Office 365](defender-for-office-365.md) Plan 2, to masz Eksploratora.
- Jeśli masz program Microsoft Defender dla Office 365 Plan 1, masz wykrywanie w czasie rzeczywistym.

Przy pierwszym otwarciu Eksploratora (lub raportu wykrywanie w czasie rzeczywistym) w widoku domyślnym są wykrywane złośliwe oprogramowanie w wiadomościach e-mail z ostatnich 7 dni. Ten raport może również zawierać program Microsoft Defender do wykrywania Office 365, takich jak złośliwe adresy URL wykryte w linkach programu [Sejf](safe-links.md) oraz złośliwych plików wykrytych przez załączniki Sejf[.](safe-attachments.md) Ten raport można zmodyfikować tak, aby zawierał dane z ostatnich 30 dni (za pomocą programu Microsoft Defender dla Office 365 P2). Subskrypcje wersji próbnej będą zawierać dane tylko z ostatnich siedmiu dni.

|Subskrypcja|Narzędzie|Dni danych|
|---|---|---|
|Program Microsoft Defender dla Office 365 P1|Wykrywanie w czasie rzeczywistym|7|
|Usługa Microsoft Defender dla Office 365 P1|Wykrywanie w czasie rzeczywistym|30|
|Usługa Microsoft Defender dla Office 365 P1 płatna wersja próbna programu Defender dla Office 365 P2|Eksplorator zagrożeń|7|
|Microsoft Defender dla Office 365 P2|Eksplorator zagrożeń|7|
|Usługa Microsoft Defender dla Office 365 P2|Eksplorator zagrożeń|30|

> [!NOTE]
> Wkrótce rozszerzymy limit przechowywania danych Eksploratora (i wykrywania w czasie rzeczywistym) i wyszukiwania dla dzierżaw wersji próbnej z 7 do 30 dni. Ta zmiana jest śledzona w ramach elementu planu nr 70544 i jest obecnie w fazie wdrażania.

Użyj menu **Widok** , aby zmienić wyświetlane informacje. Etykietki narzędzi ułatwiają określenie widoku, którego należy użyć.

![Menu Widok Eksploratora zagrożeń.](../../media/all-email.png)

Po wybraniu widoku możesz zastosować filtry i skonfigurować zapytania w celu przeprowadzenia dalszej analizy. Poniższe sekcje zawierają krótkie omówienie różnych widoków dostępnych w Eksploratorze (lub wykrywania w czasie rzeczywistym).

## <a name="email--malware"></a>Wiadomości e>-mail w celu złośliwego oprogramowania

Aby wyświetlić ten raport, w Eksploratorze (lub w czasie rzeczywistym) wybierz pozycję **Wyświetl złośliwe** **oprogramowanie poczty e-mail** \> \>. W tym widoku są wyświetlane informacje o wiadomościach e-mail zidentyfikowanych jako zawierające złośliwe oprogramowanie.

![Wyświetl dane dotyczące wiadomości e-mail zidentyfikowanych jako złośliwe oprogramowanie.](../../media/detection-technology.png)

Kliknij **pozycję Nadawca** , aby otworzyć listę opcji wyświetlania. Ta lista umożliwia wyświetlanie danych według nadawcy, adresatów, domeny nadawcy, tematu, technologii wykrywania, stanu ochrony i nie tylko.

Aby na przykład sprawdzić, jakie działania zostały wykonane w związku z wykrytymi wiadomościami e-mail, wybierz z listy pozycję **Stan** ochrony. Wybierz opcję, a następnie kliknij przycisk Odśwież, aby zastosować ten filtr do raportu.

![Opcje stanu ochrony przed zagrożeniami w Eksploratorze zagrożeń.](../../media/ThreatExplorerProtectionStatusOptions.png)

Poniżej wykresu wyświetl więcej szczegółowych informacji o konkretnych wiadomościach. Po zaznaczeniu elementu na liście zostanie otwarte okienko wysuwu, w którym możesz dowiedzieć się więcej o wybranym przez Ciebie pozycji.

![Eksplorator zagrożeń z otwartym wysuwaną oknie.](../../media/ThreatExplorerMalwareItemSelectedFlyout.png)

## <a name="email--phish"></a>Wiadomości e-> Phish

Aby wyświetlić ten raport, w Eksploratorze (lub wykrywania w czasie rzeczywistym) wybierz pozycję **Wyświetl wiadomości** \> **e-mail** \> **phish**. W tym widoku są wyświetlane wiadomości e-mail zidentyfikowane jako próby wyłudzenia informacji.

![Wyświetl dane dotyczące wiadomości e-mail zidentyfikowanych jako próby wyłudzenia informacji.](../../media/phish.png)

Kliknij **pozycję Nadawca** , aby otworzyć listę opcji wyświetlania. Ta lista umożliwia wyświetlanie danych według nadawcy, adresatów, domeny nadawcy, adresu IP nadawcy, domeny adresu URL, kliknięcia werdyktu i nie tylko.

Aby na przykład sprawdzić, jakie akcje zostały wykonane, gdy ktoś kliknął adresy URL zidentyfikowane jako próby wyłudzenia informacji, wybierz  pozycję Kliknij werdykt na liście, wybierz jedną lub więcej opcji, a następnie kliknij przycisk Odśwież.

![Kliknij opcje wywróć w raporcie Phish.](../../media/click-verdict.png)

Poniżej wykresu wyświetl więcej szczegółów dotyczących określonych wiadomości, kliknięć adresów URL, adresów URL i pochodzenia wiadomości e-mail.

![Adresy URL wykryte jako wyłudzy w wiadomościach e-mail.](../../media/ThreatExplorerEmailPhishURLs.png)

Po zaznaczeniu elementu na liście, na przykład adresu URL, który został wykryty, zostanie otwarte okienko wysuwu, w którym możesz dowiedzieć się więcej o wybranym przez Ciebie pozycji.

![Szczegółowe informacje o wykrytym adresie URL.](../../media/ThreatExplorerEmailPhishURLDetails.png)

## <a name="email--submissions"></a>Wysyłanie wiadomości > e-mail

Aby wyświetlić ten raport, w Eksploratorze (lub w czasie rzeczywistym) wybierz pozycję **Wyświetl** \> **przesłania wiadomości e-mail**\>. Ten widok przedstawia wiadomości e-mail zgłoszone przez użytkowników jako wiadomości-śmieci, a nie jako wiadomości-śmieci lub wiadomości wyłudzące informacje.

![Wiadomości e-mail zgłoszone przez użytkowników.](../../media/ThreatExplorerEmailUserReportedViewOptions.png)

Kliknij **pozycję Nadawca** , aby otworzyć listę opcji wyświetlania. Ta lista umożliwia wyświetlanie informacji według nadawcy, adresatów, typu raportu (określenie przez użytkownika, że wiadomość e-mail jest śmieciem, wiadomością niebędąc śmieciem lub wiadomością wyłud treści) i nie tylko.

Aby na przykład wyświetlić informacje o wiadomościach e-mail zgłoszonych jako próby wyłudzenia  informacji, \> kliknij pozycję Typ raportu nadawcy **, wybierz** pozycję **Wyłudzanie**, a następnie kliknij przycisk Odśwież.

![Dla filtru Typ raportu wybrano typ wiadomości wył..](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Poniżej wykresu wyświetl więcej szczegółowych informacji na temat określonych wiadomości e-mail, takich jak wiersz tematu, adres IP nadawcy, użytkownik, który zgłosił wiadomość jako wiadomość-śmieć, niebędąca śmieciem lub wiadomością wyłudząc itp.

![Wiadomości zgłoszone jako próby wyłudzenia informacji.](../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png)

Wybierz element z listy, aby wyświetlić dodatkowe szczegóły.

## <a name="email--all-email"></a>Poczta e> e-mail

Aby wyświetlić ten raport, w Eksploratorze wybierz pozycję **Wyświetl całą pocztę** \> **e-mail**\>. W tym widoku można wyświetlić wszystkie dane dotyczące aktywności poczty e-mail, w tym wiadomości e-mail zidentyfikowane jako złośliwe ze względu na wyłudzanie informacji lub złośliwe oprogramowanie, a także wszystkie niechciane wiadomości (normalne wiadomości e-mail, spam i poczta masowa).

> [!NOTE]
> Jeśli zostanie komunikat o błędzie z komunikatem Zbyt wiele danych do **wyświetlenia, dodaj** filtr i w razie potrzeby zawęzij wyświetlany zakres dat.

Aby zastosować filtr, wybierz pozycję **Nadawca**, wybierz element na liście, a następnie kliknij przycisk Odśwież. W naszym przykładzie u używaliśmy technologii **wykrywania** jako filtru (dostępnych jest kilka opcji). Możesz wyświetlać informacje według nadawcy, domeny nadawcy, adresatów, tematu, nazwy pliku załącznika, rodziny złośliwego oprogramowania, stanu ochrony (czynności podejmowane przez funkcje i zasady ochrony przed zagrożeniami w programie Office 365), technologii wykrywania (jak wykryto złośliwe oprogramowanie) i nie tylko.

![Wyświetl dane dotyczące wykrytych wiadomości e-mail za pomocą technologii wykrywania.](../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png)

Poniżej wykresu wyświetl więcej szczegółowych informacji o konkretnych wiadomościach e-mail, takich jak temat, adresat, nadawca, status itp.

## <a name="content--malware"></a>Oprogramowanie > zawartości

Aby wyświetlić ten raport, w Eksploratorze (lub wykrywanie w czasie rzeczywistym) wybierz pozycję **Wyświetl złośliwe** \> **oprogramowanie** \> **zawartości**. W tym widoku są dostępne pliki, które zostały zidentyfikowane jako złośliwe przez usługę [Microsoft Defender dla Office 365 usługi SharePoint Online, OneDrive dla Firm i Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Wyświetlaj informacje według rodziny złośliwego oprogramowania, technologii wykrywania (jak wykryto złośliwe oprogramowanie) i obciążenia pracą (OneDrive, SharePoint lub Teams).

![Wyświetl dane o wykrytym złośliwym oprogramowaniu.](../../media/malware-family.png)

Poniżej wykresu wyświetl więcej szczegółowych informacji na temat określonych plików, takich jak nazwa pliku załącznika, obciążenie pracą, rozmiar pliku, kto ostatnio zmodyfikował plik i nie tylko.

## <a name="click-to-filter-capabilities"></a>Funkcje "Kliknij, aby filtrować"

Za pomocą Eksploratora (i wykrywania w czasie rzeczywistym) możesz zastosować filtr jednym kliknięciem. Kliknij element w legendzie, a ten element stanie się filtrem raportu. Załóżmy na przykład, że przeglądamy widok Złośliwe oprogramowanie w Eksploratorze:

![Przejdź do Eksploratora zarządzania zagrożeniami \> .](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

Kliknięcie **przycisku DEtonacja ATP** na tym wykresie powoduje wyświetlenie widoku w ten sposób:

![Explorer przefiltrowany w celu wyświetlenia tylko usługi Defender na Office 365 detonacji.](../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png)

Teraz w tym widoku przeglądamy dane dotyczące plików, które zostały zdetonowane przez Sejf [załączników](safe-attachments.md). Poniżej wykresu widać szczegółowe informacje o konkretnych wiadomościach e-mail, które miały załączniki wykryte przez Sejf załączników.

![Szczegółowe informacje o wiadomościach e-mail z wykrytymi załącznikami.](../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png)

Wybranie jednego lub większej liczby elementów aktywuje menu **Akcje** , które oferuje kilka opcji, z których można wybrać dla wybranych elementów.

![Zaznaczenie elementu aktywuje menu Akcje.](../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png)

Możliwość filtrowania jednym kliknięciem i przechodzenia do określonych szczegółów pozwala zaoszczędzić sporo czasu podczas badania zagrożeń.

## <a name="queries-and-filters"></a>Zapytania i filtry

Eksplorator (a także raport wykrywanie w czasie rzeczywistym) zawiera kilka zaawansowanych filtrów i funkcji zapytań, które umożliwiają przechodzenie do szczegółów, takich jak najokierni użytkownicy, najgorętsi rodziny złośliwego oprogramowania, technologia wykrywania i nie tylko. Każdy rodzaj raportu oferuje różne sposoby wyświetlania i eksplorowanie danych.

> [!IMPORTANT]
> Nie używaj symboli wieloznacznych, takich jak gwiazdka lub znak zapytania, na pasku zapytania w Eksploratorze (ani w czasie rzeczywistym). Podczas wyszukiwania w polu Temat  wiadomości e-mail Eksplorator (lub wykrywania w czasie rzeczywistym) wykona częściowe dopasowywanie i da wyniki podobne do wyszukiwania z symbolami wieloznacznych.
