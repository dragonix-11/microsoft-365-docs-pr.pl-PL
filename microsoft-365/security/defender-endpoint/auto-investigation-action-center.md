---
title: Odwiedź Centrum akcji, aby wyświetlić działania naprawcze
description: Wyświetlanie szczegółów i wyników automatycznego badania za pomocą Centrum akcji
keywords: action, center, autoir, automated, investigation, response, remediation
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.date: 01/28/2021
ms.technology: mde
ms.openlocfilehash: 7c300a6d66ae67d481b61a0a35101a0472031266
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327689"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>Odwiedź Centrum akcji, aby wyświetlić działania naprawcze

W trakcie automatycznego badania i po jego zakończeniu są identyfikowane działania naprawcze dotyczące wykrywania zagrożeń. W zależności od określonego zagrożenia i sposobu skonfigurowania programu [Microsoft Defender for Endpoint](/windows/security/threat-protection) dla organizacji niektóre działania naprawcze są podejmowane automatycznie, a inne wymagają zatwierdzenia. Jeśli jesteś częścią zespołu operacji zabezpieczeń organizacji, w Centrum akcji możesz wyświetlać oczekujące i ukończone akcje [](manage-auto-investigation.md#remediation-actions) **zaradcze**.


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="new-a-unified-action-center"></a>(NOWOŚĆ!) Ujednolicone Centrum akcji


Z prosimy o ogłaszanie nowego, ujednoliconego Centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center))!

:::image type="content" source="images/mde-action-center-unified.png" alt-text="Centrum akcji w Microsoft 365 Defender akcji.":::

W poniższej tabeli porównano nowe, ujednolicone Centrum akcji z poprzednim Centrum akcji.

|Nowe, ujednolicone Centrum akcji  |Poprzednie Centrum akcji  |
|---------|---------|
|Lista oczekujących i ukończonych akcji dla urządzeń i poczty e-mail w jednej lokalizacji <br/>([Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) oraz [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/office-365-atp))|Lista oczekujących i ukończonych akcji dla urządzeń <br/> ([Tylko program Microsoft Defender dla punktu](microsoft-defender-endpoint.md) końcowego)   |
|Znajduje się w:<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |Znajduje się w:<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| W portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> wybierz **pozycję Centrum akcji**. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="Przechodzenie do Centrum akcji w Microsoft 365 Defender akcji."::: | W portalu Microsoft 365 Defender wybierz pozycję **Automatyczne** **badaniaAction** >  Center. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="Przechodzenie do Centrum akcji z Microsoft 365 Defender a.":::  |

Ujednolicone Centrum akcji łączy działania naprawcze w usługach Defender for Endpoint i Defender for Office 365. Definiuje ona język wspólny dla wszystkich działań naprawczych i zapewnia ujednolicone środowisko badania.

Ujednoliconego Centrum akcji możesz używać, jeśli masz odpowiednie uprawnienia i co najmniej jedną z następujących subskrypcji:

- [Defender for Endpoint](microsoft-defender-endpoint.md)
- [Defender for Office 365](/microsoft-365/security/office-365-security/office-365-atp)
- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection)

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Wymagania](/microsoft-365/security/mtp/prerequisites).

## <a name="using-the-action-center"></a>Korzystanie z Centrum akcji

Aby uzyskać dostęp do ujednoliconego Centrum akcji w ulepszonym Microsoft 365 Defender akcji:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender i</a> zaloguj się.
2. W okienku nawigacji wybierz pozycję **Centrum akcji**.

Po odwiedzenia Centrum akcji są dostępne dwie karty: **Oczekujące akcje** i **Historia**. W poniższej tabeli podsumowano elementy, które będą zawierały poszczególne karty:

|Tab|Opis|
|---|---|
|**Oczekiwanie**|Wyświetla listę akcji wymagających uwagi. Możesz zatwierdzać lub odrzucać akcje na raz albo wybierać wiele akcji, jeśli mają one taki sam typ akcji (na przykład plik **kwarantanny**). <p> **PORADA**: Należy jak najszybciej przejrzeć i zatwierdzić (lub odrzucić [)](manage-auto-investigation.md) oczekujące akcje, aby można było wykonać zautomatyzowane badania w terminie.|
|**Historia**|Pełni rolę dziennika inspekcji dla działań, które zostały wykonane, takich jak: <ul><li>Działania naprawcze wykonane w wyniku zautomatyzowanych badań</li><li>Działania naprawcze zatwierdzone przez zespół operacyjny ds. zabezpieczeń</li><li>Polecenia uruchomione i akcje naprawcze zastosowane podczas sesji odpowiedzi na żywo</li><li>Działania naprawcze podejmowane przez funkcje ochrony przed zagrożeniami w programie Program antywirusowy Microsoft Defender</li></ul> <p> Umożliwia cofnięcie pewnych akcji (zobacz [Cofanie ukończonych akcji](manage-auto-investigation.md#undo-completed-actions)).|

W Centrum akcji możesz dostosowywać, sortować, filtrować i eksportować dane.

:::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="Kolumny i filtry w Centrum akcji.":::

- Zaznacz nagłówek kolumny, aby posortować elementy w kolejności rosnącej lub malejącej.
- Użyj filtru okresu, aby wyświetlić dane za przeszły dzień, tydzień, 30 dni lub 6 miesięcy.
- Wybierz kolumny, które chcesz wyświetlić.
- Określ liczbę elementów, które mają być dołączane na każdej stronie danych.
- Użyj filtrów, aby wyświetlić tylko te elementy, które chcesz wyświetlić.
- Wybierz **pozycję Eksportuj** , aby wyeksportować wyniki do .csv pliku.

## <a name="next-steps"></a>Następne kroki

- [Wyświetlanie i zatwierdzanie działań naprawczych](manage-auto-investigation.md)
- [Zobacz interakcyjny przewodnik: Badanie i rozwiązywanie problemów związanych z zagrożeniami za pomocą programu Microsoft Defender for Endpoint](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>Zobacz też

- [Adres dodatnich/ujemnych wyników fałszywie dodatnich w programie Microsoft Defender dla punktu końcowego](defender-endpoint-false-positives-negatives.md)
