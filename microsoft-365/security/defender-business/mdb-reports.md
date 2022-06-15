---
title: Raporty w Microsoft Defender dla Firm
description: Zapoznaj się z omówieniem raportów zabezpieczeń w usłudze Defender dla firm. Raporty będą pokazywać wykryte zagrożenia, alerty, luki w zabezpieczeniach i stan urządzenia.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: a5b9dbc63d56b7e3d389d7621cedbcb8c85b0c85
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089611"
---
# <a name="reports-in-microsoft-defender-for-business"></a>Raporty w Microsoft Defender dla Firm

W portalu Microsoft 365 Defender () dostępnych jest kilka raportów[https://security.microsoft.com](https://security.microsoft.com). W tym artykule opisano te raporty, sposób ich używania i sposób ich znajdowania.

## <a name="reports-in-defender-for-business"></a>Raporty w usłudze Defender dla firm

|Raport  |Opis  |
|---------|---------|
| **Raport zabezpieczeń**  | Raport zabezpieczeń zawiera informacje o tożsamościach, urządzeniach i aplikacjach firmy. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **Raporty** > **ogólne** > **raport zabezpieczeń**. <br/><br/>**WSKAZÓWKA** Podobne informacje można wyświetlić na stronie głównej portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). |
| **Ochrona przed zagrożeniami**  | Raport dotyczący ochrony przed zagrożeniami zawiera informacje o alertach i trendach alertów. Użyj kolumny **Trendy alertów** , aby wyświetlić informacje o alertach, które zostały wyzwolone w ciągu ostatnich 30 dni. Użyj kolumny **Stan alertu** , aby wyświetlić bieżące informacje migawki dotyczące alertów, takie jak kategorie nierozwiązanych alertów i ich klasyfikacja. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **Raporty** > **Punkty końcowe****Ochrona przed zagrożeniami** > . <br/><br/>**PORADA**: Możesz również użyć listy **zdarzeń** , aby wyświetlić informacje o alertach. W okienku nawigacji wybierz pozycję **Incydenty** , aby wyświetlić bieżące zdarzenia i zarządzać nimi. Aby dowiedzieć się więcej, zobacz [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md). |
| **Kondycja i zgodność urządzenia** | Raport kondycji i zgodności urządzenia zawiera informacje o kondycji urządzenia i trendach. Ten raport umożliwia określenie, czy czujniki usługi Defender dla Firm działają prawidłowo na urządzeniach i czy bieżący stan Program antywirusowy Microsoft Defender. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **Raporty** > **Punkty końcowe** > **Kondycja urządzenia i zgodność**. <br/><br/>**PORADA**: Możesz użyć listy **Spis urządzeń** , aby wyświetlić informacje o urządzeniach firmy. W okienku nawigacji wybierz pozycję **Spis urządzeń**. Aby dowiedzieć się więcej, zobacz [Zarządzanie urządzeniami w Microsoft Defender dla Firm](mdb-manage-devices.md). |
| **Urządzenia znajdujące się w trudnej sytuacji** | Raport dotyczący urządzeń narażonych na zagrożenia zawiera informacje o urządzeniach i trendach. Użyj kolumny **Trendy** , aby wyświetlić informacje o urządzeniach, które miały alerty w ciągu ostatnich 30 dni. Użyj kolumny **Stan** , aby wyświetlić bieżące informacje migawki dotyczące urządzeń z alertami. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **Raporty** > **Punkty końcowe** > **Urządzenia wrażliwe**.<br/><br/>**PORADA**: Możesz użyć listy **Spis urządzeń** , aby wyświetlić informacje o urządzeniach firmy. W okienku nawigacji wybierz pozycję **Spis urządzeń**. Aby dowiedzieć się więcej, zobacz [Zarządzanie urządzeniami w Microsoft Defender dla Firm](mdb-manage-devices.md). |
| **Ochrona sieci Web** | Raport dotyczący ochrony sieci Web przedstawia próby uzyskania dostępu do witryn wyłudzających informacje, wektorów złośliwego oprogramowania, witryn wykorzystujących luki w zabezpieczeniach, witryn niezaufanych lub o niskiej reputacji oraz witryn, które są jawnie blokowane. Kategorie zablokowanych witryn obejmują treści dla dorosłych, witryny rekreacyjne, witryny odpowiedzialności prawnej i nie tylko. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **Raporty** > **Endpoints** > **Web Protection**.<br/><br/>**PORADA**: Jeśli ochrona w Internecie nie została jeszcze skonfigurowana dla twojej firmy, wybierz przycisk **Ustawienia** w widoku raportu. Następnie w obszarze **Reguły** wybierz pozycję **Filtrowanie zawartości sieci Web**. Aby dowiedzieć się więcej na temat filtrowania zawartości internetowej, zobacz [Filtrowanie zawartości sieci Web](../defender-endpoint/web-content-filtering.md). |


## <a name="see-also"></a>Zobacz też

- [Wprowadzenie przy użyciu Microsoft Defender dla Firm](mdb-get-started.md)
- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
- [Zarządzanie urządzeniami w Microsoft Defender dla Firm](mdb-manage-devices.md)
