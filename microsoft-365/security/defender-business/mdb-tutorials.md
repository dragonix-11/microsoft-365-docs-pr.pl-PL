---
title: Samouczki i symulowania w programie Microsoft Defender dla firm
description: Dowiedz się więcej o kilku samouczkach pomocnych w rozpoczynaniu korzystania z usługi Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: b28e28b2504ed2234f2f48a9763827fc7b063af8
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525504"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>Samouczki i symulowania w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Jeśli właśnie ukończono konfigurowanie programu Microsoft Defender dla firm, być może zastanawiasz się, od czego zacząć, aby dowiedzieć się, jak działa program Defender dla firm. W tym artykule opisano scenariusze wersji Preview do wypróbowania oraz kilka samouczków i symulacyjnych dostępnych dla usługi Defender dla firm. Te zasoby pomogą Ci zobaczyć, jak może działać w firmie defender dla firm.

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="try-these-preview-scenarios"></a>Wypróbuj te scenariusze w wersji Preview

W poniższej tabeli podsumowano kilka scenariuszy do wypróbowania za pomocą programu Defender dla firm. 
<br/><br/>


| Scenariusz  | Opis  |
|---------|---------|
| Urządzenia w tablicy korzystające ze skryptu lokalnego <br/>(*nie do wdrożenia produkcyjnego*)     | W programie Defender dla firm możesz wboardować do dziesięciu Windows 10 i 11 urządzeń, używając skryptu, który możesz pobrać i uruchomić na każdym urządzeniu. Ta usługa pozwala ocenić, jak usługa Defender dla firm będzie działać w Twoim środowisku, skrypt tworzy zaufanie w usłudze Azure Active Directory (Azure AD) i rejestruje urządzenie za pomocą programu Microsoft Intune. Aby dowiedzieć się więcej, zobacz [Skrypt lokalny w programie Defender dla firm](mdb-onboard-devices.md#local-script-in-defender-for-business).         |
| Urządzenia w urządzeniach w urządzeniu Microsoft Intune     | Jeśli korzystano już z programu Microsoft Intune przed uzyskaniem usługi Defender for Endpoint, możesz nadal używać programu Microsoft Intune urządzeniach. Wypróbuj dołączanie na urządzenia macOS, iOS i Android z systemem Microsoft Intune. Aby dowiedzieć się więcej, zobacz [Rejestracja urządzenia w Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Edytowanie zasad zabezpieczeń     | Jeśli zarządzasz zasadami zabezpieczeń w programie Defender dla firm, możesz wyświetlać  i edytować zasady na stronie Konfiguracja urządzenia. Aby dowiedzieć się więcej, [zobacz Wyświetlanie i edytowanie zasad w programie Microsoft Defender dla firm](mdb-view-edit-policies.md).        |
| Wykonywanie symulowanego ataku   | W programie Defender dla firm dostępnych jest kilka samouczków i symulacyjnych. Te samouczki i czasy symulowania zostały zaprojektowane tak, aby pokazać, jak funkcje ochrony przed zagrożeniami usługi Defender dla firm mogą działać w Twojej firmie. Aby wypróbować co najmniej jeden z samouczków, zobacz [Polecane samouczki dotyczące programu Microsoft Defender dla firm](#recommended-tutorials-for-defender-for-business).         |
| Wyświetlanie zdarzeń w programie Microsoft 365 Lighthouse     | Jeśli jesteś [użytkownikiem Microsoft Cloud Solution Provider](/partner-center/enrolling-in-the-csp-program) korzystającym z Microsoft 365 Lighthouse, wkrótce będzie można wyświetlać zdarzenia z dzierżaw klientów w portalu Microsoft 365 Lighthouse sieci. Aby dowiedzieć się więcej, zobacz [Microsoft 365 Lighthouse programu Microsoft Defender dla firm](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>Polecane samouczki dotyczące programu Defender dla firm

W poniższej tabeli opisano zalecane samouczki dla klientów usługi Defender dla firm:
<br/><br/>


| Samouczek  | Opis  |
|---------|---------|
| **Dokument jest upuszczany w backdoor**     | Symulowanie ataków, która wprowadza złośliwe oprogramowanie oparte na plikach na urządzeniu testowym. W tym samouczku opisano, jak pobrać plik symulacyjnej i jak go używać oraz co należy obserwować w portalu Microsoft 365 Defender projektu. <br/><br/>Ten samouczek wymaga Microsoft Word na urządzeniu testowym.   |
| **Samouczek odpowiedzi na żywo**     | Dowiedz się, jak używać podstawowych i zaawansowanych poleceń z odpowiedzią na żywo. Dowiedz się, jak znaleźć podejrzany plik, rozwiązać jego działania naprawcze i zebrać informacje na urządzeniu.   |
| **Zarządzanie & zagrożeniami (podstawowe scenariusze)**     | Dowiedz się więcej Zarządzanie zagrożeniami i lukami za pomocą trzech scenariuszy: <br/><br/>1. Zmniejsz zagrożenie i narażenie Twojej firmy na luki w zabezpieczeniach. <br/>2. Żądanie rozwiązania problemów. <br/>3. Tworzenie wyjątku dla zaleceń dotyczących zabezpieczeń. <br/><br/> Zagrożenia i zarządzanie lukami w zabezpieczeniach wykorzystania opartego na ryzyku podejścia do odnajdowania, ustalania priorytetu i korygowania luk w punktach końcowych i błędnej konfiguracji.      |

Każdy samouczek zawiera dokument instruktażowy, w którym wyjaśniono scenariusz, jak to działa i co należy zrobić.

> [!TIP]
> W dokumentach instruktażowych zobaczysz odwołania do programu Microsoft Defender for Endpoint. Samouczki wymienione w tym artykule mogą być używane z usługą Defender for Endpoint lub Defender for Business.

## <a name="how-to-access-the-tutorials"></a>Jak uzyskać dostęp do samouczków

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji w obszarze **Punkty końcowe** wybierz pozycję **Samouczki**.

3. Wybierz jeden z następujących samouczków:

   - **Dokument jest upuszczany w backdoor**
   - **Samouczek odpowiedzi na żywo**
   - **Zarządzanie & zagrożeniami (podstawowe scenariusze)**

## <a name="next-steps"></a>Następne kroki

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)