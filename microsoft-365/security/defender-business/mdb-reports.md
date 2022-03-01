---
title: Raporty w programie Microsoft Defender dla firm (wersja Preview)
description: Omówienie raportów dostępnych w programie Microsoft Defender dla firm (wersja Preview)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 85e1958c9577b68737aa2803dc115c83f757654e
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027126"
---
# <a name="reports-in-microsoft-defender-for-business-preview"></a>Raporty w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. Program Microsoft Defender for Business (w wersji Preview) zawiera kilka raportów zgodnie z opisem w poniższej tabeli:<br/><br/>

W portalu Microsoft 365 Defender () dostępnych jest kilka raportów[https://security.microsoft.com](https://security.microsoft.com). W tym artykule opisano te raporty, sposób ich używania i znajdowanie.

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

<br/><br/>

## <a name="reports-in-defender-for-business"></a>Raporty w u programie Defender dla firm

|Raport  |Opis  |
|---------|---------|
| **Raport zabezpieczeń**  | Raport zabezpieczeń zawiera informacje o tożsamościach, urządzeniach i aplikacjach organizacji. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz raport **ReportsGeneralSecurity** >  > . <br/><br/>**PORADA** Podobne informacje można wyświetlić na stronie głównej portalu Microsoft 365 Defender sieci Web ([https://security.microsoft.com](https://security.microsoft.com)). |
| **Ochrona przed zagrożeniami**  | Raport ochrony przed zagrożeniami zawiera informacje na temat alertów i trendów alertów. Kolumna **Trendy alertów** umożliwia wyświetlanie informacji o alertach, które były wyzwalane w ciągu ostatnich 30 dni. Kolumna **Stan alertu umożliwia** wyświetlanie aktualnych informacji migawkowych o alertach, takich jak kategorie nierozpoznanych alertów i ich klasyfikacja. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **ReportsEndpointsThreat** >  **protection (Ochrona raportówendpoints** > ). <br/><br/>**PORADA**: Za pomocą listy Zdarzenia można **także** wyświetlać informacje o alertach. W okienku nawigacji wybierz pozycję **Zdarzenia** , aby wyświetlić bieżące zdarzenia i zarządzać nimi. Aby dowiedzieć się więcej, [zobacz Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja preview).](mdb-view-manage-incidents.md) |
| **Kondycja i zgodność urządzenia** | Raport kondycji i zgodności urządzeń zawiera informacje na temat kondycji i trendów urządzeń. Ten raport pozwala określić, czy czujniki programu Defender dla firm (wersja Preview) działają poprawnie na urządzeniach i mają bieżący stan Program antywirusowy Microsoft Defender. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję ReportsEndpointsDevice  > **health and compliance (Kondycja i zgodność aplikacji ReportsEndpointsDevice** > ). <br/><br/>**PORADA**: Za **pomocą listy Spis** urządzeń możesz wyświetlić informacje o urządzeniach w Twojej organizacji. W okienku nawigacji wybierz pozycję **Spis urządzeń**. Aby dowiedzieć się więcej, zobacz [Zarządzanie urządzeniami w programie Microsoft Defender dla firm (wersja Preview).](mdb-manage-devices.md) |
| **Urządzenia narażone na zagrożenia** | Raport o urządzeniach, które są narażone na zagrożenia, zawiera informacje o urządzeniach i trendach. Kolumna **Trendy umożliwia** wyświetlanie informacji o urządzeniach, na których były alerty z ostatnich 30 dni. Kolumna **Stan umożliwia wyświetlanie** bieżących informacji migawki o urządzeniach z alertami. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **ReportsEndpointsVulnerable** >  >  **devices ..**<br/><br/>**PORADA**: Za **pomocą listy Spis** urządzeń możesz wyświetlić informacje o urządzeniach w Twojej organizacji. W okienku nawigacji wybierz pozycję **Spis urządzeń**. Aby dowiedzieć się więcej, zobacz [Zarządzanie urządzeniami w programie Microsoft Defender dla firm (wersja Preview).](mdb-manage-devices.md) |
| **Ochrona sieci Web** | Raport ochrony sieci Web przedstawia próby uzyskania dostępu do witryn wyłudzających informacje, wektorów złośliwego oprogramowania, witryn wykorzystujących luki w witrynach, witryn niezaufanych lub o niskiej reputacji oraz witryn jawnie zablokowanych. Kategorie blokowanych witryn obejmują między innymi treści dla dorosłych, witryny rozrywki i witryny odpowiedzialności prawnej. Aby uzyskać dostęp do tego raportu, w okienku nawigacji wybierz pozycję **ReportsEndpointsWeb** protection (Ochrona sieci **Web w programie** **ReportsEndpoints** >  > ).<br/><br/>**PORADA**: Jeśli ochrona sieci Web dla organizacji nie została jeszcze skonfigurowana, wybierz **Ustawienia sieci Web** w widoku raportu. Następnie w obszarze **Reguły** wybierz pozycję **Filtrowanie zawartości sieci Web**. Aby dowiedzieć się więcej o filtrowaniu zawartości sieci Web, zobacz [Filtrowanie zawartości sieci Web](../defender-endpoint/web-content-filtering.md). |

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do korzystania z usługi Microsoft Defender dla firm (wersja Preview)](mdb-get-started.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-manage-incidents.md)

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm (wersja preview)](mdb-manage-devices.md)
