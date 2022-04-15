---
title: Samouczki i symulacje w Microsoft Defender dla Firm
description: Dowiedz się więcej o kilku samouczkach ułatwiających rozpoczęcie korzystania z usługi Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 42d7acb4512928a32ac99c486a231d7891102208
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861339"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>Samouczki i symulacje w Microsoft Defender dla Firm

> [!IMPORTANT]
> Microsoft Defender dla Firm jest teraz w wersji zapoznawczej i będzie stopniowo wdrażana dla klientów i partnerów IT, którzy [zarejestrują się tutaj](https://aka.ms/mdb-preview), aby go zażądać. W najbliższych tygodniach dołączymy początkowy zestaw klientów i partnerów i rozszerzymy wersję zapoznawczą prowadzącą do ogólnej dostępności. Pamiętaj, że wersja zapoznawcza zostanie uruchomiona z [początkowym zestawem scenariuszy](#try-these-preview-scenarios) i będziemy regularnie dodawać możliwości.
> 
> Niektóre informacje zawarte w tym artykule odnoszą się do wstępnie wydanych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjnym wydaniem. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, dotyczących informacji podanych tutaj. 

Jeśli właśnie ukończono konfigurowanie Microsoft Defender dla Firm, możesz się zastanawiać, od czego zacząć uczyć się, jak działa usługa Defender for Business. W tym artykule opisano scenariusze w wersji zapoznawczej do wypróbowania oraz kilka samouczków i symulacji dostępnych dla usługi Defender dla firm. Te zasoby ułatwiają sprawdzenie, jak usługa Defender dla Firm może działać dla Twojej firmy.

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="try-these-preview-scenarios"></a>Wypróbuj te scenariusze w wersji zapoznawczej

Poniższa tabela zawiera podsumowanie kilku scenariuszy, które należy wypróbować w usłudze Defender dla Firm:

| Scenariusz  | Opis  |
|---------|---------|
| Dołączanie urządzeń przy użyciu skryptu lokalnego <br/>(*nie w przypadku wdrożenia produkcyjnego*)     | W usłudze Defender dla firm możesz dołączyć maksymalnie dziesięć urządzeń Windows 10 i 11 przy użyciu skryptu pobranego i uruchomionego na każdym urządzeniu. Nadaje się do oceny sposobu działania usługi Defender dla firm w twoim środowisku, a skrypt tworzy relację zaufania z Azure Active Directory (Azure AD) i rejestruje urządzenie za pomocą Microsoft Intune. Aby dowiedzieć się więcej, zobacz [Dołączanie urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md).         |
| Dołączanie urządzeń przy użyciu Microsoft Intune     | Jeśli używasz już Microsoft Intune przed uzyskaniem usługi Defender for Endpoint, możesz nadal używać Microsoft Intune do dołączania urządzeń. Spróbuj dołączyć urządzenia z systemami macOS, iOS i Android przy użyciu Microsoft Intune. Aby dowiedzieć się więcej, zobacz [Rejestrowanie urządzeń w Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Edytowanie zasad zabezpieczeń     | Jeśli zarządzasz zasadami zabezpieczeń w usłudze Defender dla Firm, użyj strony **Konfiguracja urządzenia** , aby wyświetlić i edytować zasady. Aby dowiedzieć się więcej, zobacz [Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm](mdb-view-edit-policies.md).        |
| Wykonywanie symulowanego ataku   | W usłudze Defender dla Firm dostępnych jest kilka samouczków i symulacji. Te samouczki i symulacje zostały zaprojektowane tak, aby z pierwszej ręki pokazać, jak funkcje ochrony przed zagrożeniami w usłudze Defender for Business mogą działać dla Twojej firmy. Aby wypróbować co najmniej jeden z samouczków, zobacz [Zalecane samouczki dotyczące Microsoft Defender dla Firm](#recommended-tutorials-for-defender-for-business).         |
| Wyświetlanie zdarzeń w Microsoft 365 Lighthouse     | Jeśli używasz [Microsoft Cloud Solution Provider](/partner-center/enrolling-in-the-csp-program) Microsoft 365 Lighthouse, wkrótce będzie można wyświetlać zdarzenia w dzierżawach klientów w portalu Microsoft 365 Lighthouse. Aby dowiedzieć się więcej, zobacz [Microsoft 365 Lighthouse i Microsoft Defender dla Firm](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>Zalecane samouczki dotyczące usługi Defender dla firm

W poniższej tabeli opisano zalecane samouczki dla klientów usługi Defender dla Firm:

| Samouczek  | Opis  |
|---------|---------|
| **Dokument porzuca tylne drzwi**     | Symulowanie ataku, który wprowadza złośliwe oprogramowanie oparte na plikach na urządzeniu testowym. W samouczku opisano sposób pobierania i używania pliku symulacji oraz tego, co należy obserwować w portalu Microsoft 365 Defender. <br/><br/>Ten samouczek wymaga zainstalowania Microsoft Word na urządzeniu testowym.   |
| **Samouczek dotyczący odpowiedzi na żywo**     | Dowiedz się, jak używać podstawowych i zaawansowanych poleceń z odpowiedzią na żywo. Dowiedz się, jak zlokalizować podejrzany plik, skorygować plik i zebrać informacje na urządzeniu.   |
| **Zarządzanie lukami w zabezpieczeniach & zagrożeń (scenariusze podstawowe)**     | Dowiedz się więcej o Zarządzanie zagrożeniami i lukami w trzech scenariuszach: <br/><br/>1. Zmniejsz narażenie firmy na zagrożenia i luki w zabezpieczeniach. <br/>2. Zażądaj korygowania. <br/>3. Utwórz wyjątek dla zaleceń dotyczących zabezpieczeń. <br/><br/> Zagrożenia i zarządzanie lukami w zabezpieczeniach korzystają z opartego na ryzyku podejścia do odnajdywania, określania priorytetów i korygowania luk w zabezpieczeniach i błędnych konfiguracji punktów końcowych.      |

Każdy samouczek zawiera przewodnik wyjaśniający scenariusz, jego działanie i czynności do wykonania.

> [!TIP]
> W dokumentach przewodnika zostaną wyświetlone odwołania do Ochrona punktu końcowego w usłudze Microsoft Defender. Samouczków wymienionych w tym artykule można używać z usługą Defender for Endpoint lub Defender for Business.

## <a name="how-to-access-the-tutorials"></a>Jak uzyskać dostęp do samouczków

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji w obszarze **Punkty końcowe** wybierz pozycję **Samouczki**.

3. Wybierz jeden z następujących samouczków:

   - **Dokument porzuca tylne drzwi**
   - **Samouczek dotyczący odpowiedzi na żywo**
   - **Zarządzanie lukami w zabezpieczeniach & zagrożeń (scenariusze podstawowe)**

## <a name="next-steps"></a>Następne kroki

- [Zarządzanie urządzeniami w Microsoft Defender dla Firm](mdb-manage-devices.md)
- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)
- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)