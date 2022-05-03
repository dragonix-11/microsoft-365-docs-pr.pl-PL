---
title: Samouczki i symulacje w Microsoft Defender dla Firm
description: Dowiedz się więcej o kilku samouczkach ułatwiających rozpoczęcie korzystania z usługi Defender dla Firm.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 68695ee348b11fcc10f3a82d2cba2d2c168af666
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174386"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>Samouczki i symulacje w Microsoft Defender dla Firm

Jeśli właśnie ukończono konfigurowanie Microsoft Defender dla Firm, możesz się zastanawiać, od czego zacząć uczyć się, jak działa usługa Defender for Business. W tym artykule opisano kilka scenariuszy do wypróbowania oraz kilka samouczków i symulacji, które są dostępne dla usługi Defender dla firm. Te zasoby ułatwiają sprawdzenie, jak usługa Defender dla Firm może działać dla Twojej firmy.

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="try-these-scenarios"></a>Wypróbuj te scenariusze

Poniższa tabela zawiera podsumowanie kilku scenariuszy, które należy wypróbować w usłudze Defender dla Firm:

| Scenariusz  | Opis  |
|---------|---------|
| Dołączanie urządzeń przy użyciu skryptu lokalnego     | W usłudze Defender dla firm można dołączyć urządzenia z systemem Windows i macOS przy użyciu skryptu pobranego i uruchomionego na każdym urządzeniu. Skrypt tworzy relację zaufania z Azure Active Directory (Azure AD) (jeśli to zaufanie jeszcze nie istnieje), rejestruje urządzenie przy użyciu Microsoft Intune (jeśli masz Intune) i dołącza je do usługi Defender for Business. Aby dowiedzieć się więcej, zobacz [Dołączanie urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md).         |
| Dołączanie urządzeń przy użyciu centrum administracyjnego Microsoft Endpoint Manager     | Jeśli używasz już Intune przed uzyskaniem usługi Defender dla Firm, możesz nadal używać centrum administracyjnego Endpoint Manager do dołączania urządzeń. Spróbuj dołączyć urządzenia Windows, macOS, iOS i Android przy użyciu Microsoft Intune. Aby dowiedzieć się więcej, zobacz [Rejestrowanie urządzeń w Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Edytowanie zasad zabezpieczeń     | Jeśli zarządzasz zasadami zabezpieczeń w usłudze Defender dla Firm, użyj strony **Konfiguracja urządzenia** , aby wyświetlić i, w razie potrzeby, edytować zasady. Usługa Defender dla firm jest dostarczana z domyślnymi zasadami, które używają zalecanych ustawień w celu zabezpieczenia urządzeń firmy natychmiast po ich dołączeniu. Możesz zachować domyślne zasady, edytować je i definiować własne zgodnie z potrzebami biznesowymi. Aby dowiedzieć się więcej, zobacz [Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm](mdb-view-edit-policies.md).        |
| Uruchamianie symulowanego ataku   | W usłudze Defender dla Firm dostępnych jest kilka samouczków i symulacji. Te samouczki i symulacje zostały zaprojektowane tak, aby z pierwszej ręki pokazać, jak funkcje ochrony przed zagrożeniami w usłudze Defender for Business mogą działać dla Twojej firmy. Możesz również użyć symulowanego ataku jako ćwiczenia szkoleniowego dla swojego zespołu. Aby wypróbować co najmniej jeden z samouczków, zobacz [Zalecane samouczki dotyczące Microsoft Defender dla Firm](#recommended-tutorials-for-defender-for-business).         |
| Wyświetlanie zdarzeń w Microsoft 365 Lighthouse     | Jeśli korzystasz z [Microsoft Cloud Solution Provider](/partner-center/enrolling-in-the-csp-program) przy użyciu Microsoft 365 Lighthouse, będziesz mieć możliwość wyświetlania zdarzeń w dzierżawach klientów w portalu Microsoft 365 Lighthouse. Aby dowiedzieć się więcej, zobacz [Microsoft 365 Lighthouse i Microsoft Defender dla Firm](mdb-lighthouse-integration.md).       |


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