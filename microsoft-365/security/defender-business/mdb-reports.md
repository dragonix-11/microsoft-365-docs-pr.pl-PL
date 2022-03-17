---
title: Raporty w programie Microsoft Defender dla firm
description: Omówienie raportów dostępnych w programie Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 68b5c15b69c1f485bb9ed90bab06c2ceaa2978d9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63527088"
---
# <a name="reports-in-microsoft-defender-for-business"></a>Raporty w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

W portalu Microsoft 365 Defender () dostępnych jest kilka raportów[https://security.microsoft.com](https://security.microsoft.com). W tym artykule opisano te raporty, sposób ich używania i znajdowanie.

<br/><br/>

## <a name="reports-in-defender-for-business"></a>Raporty w u programie Defender dla firm

|Raport  |Opis  |
|---------|---------|
| **Raport zabezpieczeń**  | Raport zabezpieczeń zawiera informacje o tożsamościach, urządzeniach i aplikacjach Firmy. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz raport **ReportsGeneralSecurity** >  > . <br/><br/>**PORADA** Podobne informacje można wyświetlić na stronie głównej portalu Microsoft 365 Defender sieci Web ([https://security.microsoft.com](https://security.microsoft.com)). |
| **Ochrona przed zagrożeniami**  | Raport ochrony przed zagrożeniami zawiera informacje na temat alertów i trendów alertów. Kolumna **Trendy alertów** umożliwia wyświetlanie informacji o alertach, które były wyzwalane w ciągu ostatnich 30 dni. Kolumna **Stan alertu umożliwia** wyświetlanie aktualnych informacji migawkowych o alertach, takich jak kategorie nierozpoznanych alertów i ich klasyfikacja. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **ReportsEndpointsThreat** >  **protection (Ochrona raportówendpoints** > ). <br/><br/>**PORADA**: Za pomocą listy Zdarzenia można **także** wyświetlać informacje o alertach. W okienku nawigacji wybierz pozycję **Zdarzenia** , aby wyświetlić bieżące zdarzenia i zarządzać nimi. Aby dowiedzieć się więcej, [zobacz Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md). |
| **Kondycja i zgodność urządzenia** | Raport kondycji i zgodności urządzeń zawiera informacje na temat kondycji i trendów urządzeń. Ten raport pozwala określić, czy czujniki usługi Defender dla firm działają poprawnie na urządzeniach i czy mają być Program antywirusowy Microsoft Defender. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję ReportsEndpointsDevice  > **health and compliance (Kondycja i zgodność aplikacji ReportsEndpointsDevice** > ). <br/><br/>**PORADA**: Za **pomocą listy Spis** urządzeń możesz wyświetlić informacje o urządzeniach firmy. W okienku nawigacji wybierz pozycję **Spis urządzeń**. Aby dowiedzieć się więcej, zobacz [Zarządzanie urządzeniami w programie Microsoft Defender dla firm](mdb-manage-devices.md). |
| **Urządzenia narażone na zagrożenia** | Raport o urządzeniach, które są narażone na zagrożenia, zawiera informacje o urządzeniach i trendach. Kolumna **Trendy umożliwia** wyświetlanie informacji o urządzeniach, na których były alerty z ostatnich 30 dni. Kolumna **Stan umożliwia wyświetlanie** bieżących informacji migawki o urządzeniach z alertami. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **ReportsEndpointsVulnerable** >  >  **devices ..**<br/><br/>**PORADA**: Za **pomocą listy Spis** urządzeń możesz wyświetlić informacje o urządzeniach firmy. W okienku nawigacji wybierz pozycję **Spis urządzeń**. Aby dowiedzieć się więcej, zobacz [Zarządzanie urządzeniami w programie Microsoft Defender dla firm](mdb-manage-devices.md). |
| **Ochrona sieci Web** | Raport ochrony sieci Web przedstawia próby uzyskania dostępu do witryn wyłudzających informacje, wektorów złośliwego oprogramowania, witryn wykorzystujących luki w witrynach, witryn niezaufanych lub o niskiej reputacji oraz witryn jawnie zablokowanych. Kategorie blokowanych witryn obejmują między innymi treści dla dorosłych, witryny rozrywki i witryny odpowiedzialności prawnej. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **ReportsEndpointsWeb** protection (Ochrona sieci **Web w programie** **ReportsEndpoints** >  > ).<br/><br/>**PORADA**: Jeśli ochrona sieci Web w firmie nie została jeszcze skonfigurowana, wybierz **Ustawienia sieci Web** w widoku raportu. Następnie w obszarze **Reguły** wybierz pozycję **Filtrowanie zawartości sieci Web**. Aby dowiedzieć się więcej o filtrowaniu zawartości sieci Web, zobacz [Filtrowanie zawartości sieci Web](../defender-endpoint/web-content-filtering.md). |

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do korzystania z usługi Microsoft Defender dla firm](mdb-get-started.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm](mdb-manage-devices.md)