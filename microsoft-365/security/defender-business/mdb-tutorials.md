---
title: Samouczki i symulacyjne w programie Microsoft Defender dla firm (wersja Preview)
description: Dowiedz się więcej o kilku samouczkach pomocnych w rozpoczynaniu korzystania z programu Defender dla firm (wersja Preview)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/15/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 570313132367ad591944d87959cff538cd5b75e8
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014834"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business-preview"></a>Samouczki i symulacyjne w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Jeśli właśnie ukończono konfigurowanie programu Microsoft Defender dla firm (wersja Preview), być może zastanawiasz się, gdzie zacząć dowiedzieć się, jak działa program Defender dla firm (wersja Preview). W tym artykule opisano scenariusze wersji Preview do wypróbowania oraz kilka samouczków i symulacyjnych dostępnych dla programu Defender dla firm (wersja Preview). Te zasoby pomogą Ci zobaczyć, jak może działać w Twojej organizacji defender dla firm (wersja Preview).

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="try-these-preview-scenarios"></a>Wypróbuj te scenariusze w wersji Preview

W poniższej tabeli podsumowano kilka scenariuszy do wypróbowania podczas podglądu programu Defender dla firm (wersja Preview). 
<br/><br/>


| Scenariusz  | Opis  |
|---------|---------|
| Urządzenia w tablicy korzystające ze skryptu lokalnego     | W programie Defender dla firm (wersja Preview) możesz Windows 10 urządzenia i 11 urządzeń, używając skryptu, który można pobrać i uruchomić na każdym urządzeniu. Skrypt tworzy zaufanie dla usługi Azure Active Directory (Azure AD) i rejestruje urządzenie za pomocą Microsoft Intune. Aby dowiedzieć się więcej, zobacz [Urządzenia na tablicy przy użyciu skryptu lokalnego w programie Defender dla firm](mdb-onboard-devices.md#onboard-devices-using-a-local-script-in-defender-for-business).         |
| Urządzenia w urządzeniach w urządzeniu Microsoft Intune     | Jeśli korzystano już z programu Microsoft Intune przed uzyskaniem usługi Defender for Endpoint, możesz używać programu Microsoft Intune urządzeniach. Wypróbuj urządzenia z systemami macOS, iOS, Linux i Android z systemem Microsoft Intune. Aby dowiedzieć się więcej, zobacz [Rejestracja urządzenia w Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Edytowanie zasad zabezpieczeń     | Jeśli zarządzasz zasadami zabezpieczeń w programie Defender dla firm (wersja Preview), możesz wyświetlać i edytować zasady na stronie Konfiguracja urządzenia. Aby dowiedzieć się więcej, [zobacz Wyświetlanie i edytowanie zasad w programie Microsoft Defender dla firm (wersja Preview).](mdb-view-edit-policies.md)        |
| Wykonywanie symulowanego ataku   | W programie Defender dla firm (wersja Preview) jest dostępnych kilka samouczków i symulacyjnych. Te samouczki i czasy symulacyjne zostały zaprojektowane tak, aby pokazać, jak funkcje ochrony przed zagrożeniami dostępne w programie Defender dla firm (w wersji Preview) mogą działać w Twojej organizacji. Aby wypróbować co najmniej jeden z samouczków, zobacz [Polecane samouczki dotyczące programu Microsoft Defender dla firm (wersja Preview)](#recommended-tutorials-for-defender-for-business).         |
| Wyświetlanie zdarzeń w programie Microsoft 365 Lighthouse     | Jeśli jesteś [użytkownikiem Microsoft Cloud Solution Provider](/partner-center/enrolling-in-the-csp-program) korzystającym z Microsoft 365 Lighthouse, wkrótce będzie można wyświetlać zdarzenia z dzierżaw klientów w portalu Microsoft 365 Lighthouse sieci. Aby dowiedzieć się więcej, zobacz [Microsoft 365 Lighthouse programu Microsoft Defender dla firm (wersja Preview)](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>Polecane samouczki dotyczące programu Defender dla firm

W poniższej tabeli opisano zalecane samouczki dla klientów korzystających z programu Defender dla firm (wersja Preview):
<br/><br/>


| Samouczek  | Opis  |
|---------|---------|
| **Dokument jest upuszczany w backdoor**     | Symulowanie ataków, która wprowadza złośliwe oprogramowanie oparte na plikach na urządzeniu testowym. W tym samouczku opisano, jak pobrać plik symulacyjnej i jak go używać oraz co należy obserwować w portalu Microsoft 365 Defender projektu. <br/><br/>Ten samouczek wymaga Microsoft Word na urządzeniu testowym.   |
| **Samouczek odpowiedzi na żywo**     | Dowiedz się, jak używać podstawowych i zaawansowanych poleceń z odpowiedzią na żywo. Dowiedz się, jak znaleźć podejrzany plik, rozwiązać jego działania naprawcze i zebrać informacje na urządzeniu.   |
| **Zarządzanie & zagrożeniami (podstawowe scenariusze)**     | Dowiedz się więcej Zarządzanie zagrożeniami i lukami za pomocą trzech scenariuszy: <br/><br/>1. Zmniejsz zagrożenie i narażenie Twojej organizacji na luki w zabezpieczeniach. <br/>2. Żądanie rozwiązania problemów. <br/>3. Tworzenie wyjątku dla zaleceń dotyczących zabezpieczeń. <br/><br/> Zagrożenia i zarządzanie lukami w zabezpieczeniach wykorzystania opartego na ryzyku podejścia do odnajdowania, ustalania priorytetu i korygowania luk w punktach końcowych i błędnej konfiguracji.      |

Każdy samouczek zawiera dokument instruktażowy, w którym wyjaśniono scenariusz, jak to działa i co należy zrobić.

> [!TIP]
> W dokumentach instruktażowych zobaczysz odwołania do programu Microsoft Defender for Endpoint. Samouczki wymienione w tym artykule mogą być używane z usługą Defender for Endpoint lub Defender for Business (wersja Preview).

## <a name="how-to-access-the-tutorials"></a>Jak uzyskać dostęp do samouczków

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji w obszarze **Punkty końcowe** wybierz pozycję **Samouczki**.

3. Wybierz jeden z następujących samouczków:

   - **Dokument jest upuszczany w backdoor**
   - **Samouczek odpowiedzi na żywo**
   - **Zarządzanie & zagrożeniami (podstawowe scenariusze)**

## <a name="next-steps"></a>Następne kroki

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm (wersja preview)](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm (wersja Preview)](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)