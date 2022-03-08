---
title: Samouczki i symulowania w programie Microsoft Defender dla firm
description: Dowiedz się więcej o kilku samouczkach pomocnych w rozpoczynaniu korzystania z usługi Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: c955b85001a141933227873a1f74e681f74b004b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322943"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>Samouczki i symulowania w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Jeśli właśnie ukończono konfigurowanie programu Microsoft Defender dla firm, być może zastanawiasz się, od czego zacząć, aby dowiedzieć się, jak działa program Defender dla firm. W tym artykule opisano scenariusze wersji Preview do wypróbowania oraz kilka samouczków i symulacyjnych dostępnych dla usługi Defender dla firm. Te zasoby pomogą Ci zobaczyć, jak może działać w Twojej organizacji defender dla firm.

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="try-these-preview-scenarios"></a>Wypróbuj te scenariusze w wersji Preview

W poniższej tabeli podsumowano kilka scenariuszy do wypróbowania za pomocą programu Defender dla firm. 
<br/><br/>


| Scenariusz  | Opis  |
|---------|---------|
| Urządzenia w tablicy korzystające ze skryptu lokalnego <br/>(*nie do wdrożenia produkcyjnego*)     | W programie Defender dla firm możesz uruchomić maksymalnie dziesięć urządzeń z systemem Windows 10 i 11, korzystając ze skryptu, który możesz pobrać i uruchomić na każdym urządzeniu. Nadaje się do oceny działania usługi Defender dla firm w Twoim środowisku, skrypt tworzy zaufanie do usługi Azure Active Directory (Azure AD) i zapisuje urządzenie w usłudze Microsoft Intune. Aby dowiedzieć się więcej, zobacz [Skrypt lokalny w programie Defender dla firm](mdb-onboard-devices.md#local-script-in-defender-for-business).         |
| Urządzenia na urządzeniach w usłudze Microsoft Intune     | Jeśli korzystano już z usługi Microsoft Intune przed uzyskaniem usługi Defender for Endpoint, możesz nadal korzystać z usługi Microsoft Intune na urządzeniach onboard. Wypróbuj dołączanie do urządzeń z systemami macOS, iOS i Android w usłudze Microsoft Intune. Aby dowiedzieć się więcej, zobacz [Rejestracja urządzenia w usłudze Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Edytowanie zasad zabezpieczeń     | Jeśli zarządzasz zasadami zabezpieczeń w programie Defender dla firm, możesz wyświetlać  i edytować zasady na stronie Konfiguracja urządzenia. Aby dowiedzieć się więcej, [zobacz Wyświetlanie i edytowanie zasad w programie Microsoft Defender dla firm](mdb-view-edit-policies.md).        |
| Wykonywanie symulowanego ataku   | W programie Defender dla firm dostępnych jest kilka samouczków i symulacyjnych. Te samouczki i symulacyjne mają na celu pokazanie, jak funkcje ochrony przed zagrożeniami usługi Defender dla firm mogą działać w Twojej organizacji. Aby wypróbować co najmniej jeden z samouczków, zobacz [Polecane samouczki dotyczące programu Microsoft Defender dla firm](#recommended-tutorials-for-defender-for-business).         |
| Wyświetlanie zdarzeń w latarni morskiej platformy Microsoft 365     | Jeśli jesteś dostawcą rozwiązań w chmurze firmy [Microsoft](/partner-center/enrolling-in-the-csp-program) używającym latarni morskiej platformy Microsoft 365, wkrótce będzie można wyświetlać zdarzenia w dzierżawach swoich klientów w portalu Latarnia morska na platformie Microsoft 365. Aby dowiedzieć się więcej, zobacz [Latarnia morska platformy Microsoft 365 i usługa Microsoft Defender dla firm](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>Polecane samouczki dotyczące programu Defender dla firm

W poniższej tabeli opisano zalecane samouczki dla klientów usługi Defender dla firm:
<br/><br/>


| Samouczek  | Opis  |
|---------|---------|
| **Dokument jest upuszczany w backdoor**     | Symulowanie ataków, która wprowadza złośliwe oprogramowanie oparte na plikach na urządzeniu testowym. W tym samouczku opisano, jak pobrać i użyć pliku symulacyjnego oraz co należy obserwować w portalu usługi Microsoft 365 Defender. <br/><br/>Ten samouczek wymaga zainstalowania programu Microsoft Word na urządzeniu testowym.   |
| **Samouczek odpowiedzi na żywo**     | Dowiedz się, jak używać podstawowych i zaawansowanych poleceń z odpowiedzią na żywo. Dowiedz się, jak znaleźć podejrzany plik, rozwiązać jego działania naprawcze i zebrać informacje na urządzeniu.   |
| **Zarządzanie & zagrożeniami (podstawowe scenariusze)**     | Dowiedz się więcej o zarządzaniu zagrożeniami i lukami w zabezpieczeniach w trzech scenariuszach: <br/><br/>1. Zmniejsz zagrożenie i narażenie Twojej organizacji na luki w zabezpieczeniach. <br/>2. Żądanie rozwiązania problemów. <br/>3. Tworzenie wyjątku dla zaleceń dotyczących zabezpieczeń. <br/><br/> Zarządzanie zagrożeniami i lukami w zabezpieczeniach korzysta z opartego na ryzyko podejścia do odnajdowania, priorytetyzowania i korygowania luk w punktach końcowych i błędnej konfiguracji.      |

Każdy samouczek zawiera dokument instruktażowy, w którym wyjaśniono scenariusz, jak to działa i co należy zrobić.

> [!TIP]
> W dokumentach instruktażowych zobaczysz odwołania do programu Microsoft Defender for Endpoint. Samouczki wymienione w tym artykule mogą być używane z usługą Defender for Endpoint lub Defender for Business.

## <a name="how-to-access-the-tutorials"></a>Jak uzyskać dostęp do samouczków

1. Przejdź do portalu usługi Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

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