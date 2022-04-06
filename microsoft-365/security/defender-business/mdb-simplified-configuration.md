---
title: Uproszczony proces konfiguracji w Microsoft Defender dla Firm
description: Dowiedz się więcej o uproszczonym procesie konfiguracji w Microsoft Defender dla Firm
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
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 02f970f7ad9981336ba54aaafcf936e952f1b726
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663121"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>Uproszczony proces konfiguracji w Microsoft Defender dla Firm

> [!IMPORTANT]
> Microsoft Defender dla Firm jest wdrażana dla [klientów Microsoft 365 Business Premium](../../business-premium/index.md) od 1 marca 2022 r. Usługa Defender dla Firm jako subskrypcja autonomiczna jest dostępna w wersji zapoznawczej i będzie stopniowo wdrażana dla klientów i partnerów IT, którzy [zarejestrują się tutaj](https://aka.ms/mdb-preview) , aby zażądać tej subskrypcji. Wersja zapoznawcza zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać możliwości.
> 
> Niektóre informacje zawarte w tym artykule odnoszą się do wstępnie wydanych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjnym wydaniem. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, dotyczących informacji podanych tutaj. 

Microsoft Defender dla Firm oferuje uproszczony proces konfiguracji, zaprojektowany specjalnie dla małych i średnich firm. To środowisko pozwala zgadywać podczas dołączania urządzeń i zarządzania nimi przy użyciu środowiska przypominającego kreatora i domyślnych zasad, które zostały zaprojektowane w celu ochrony urządzeń firmy od pierwszego dnia. **Zalecamy korzystanie z uproszczonego procesu konfiguracji. Jednak nie ograniczasz się do tej opcji**.

Jeśli chodzi o dołączanie urządzeń i konfigurowanie ustawień zabezpieczeń dla urządzeń firmowych, możesz wybrać jedną z kilku środowisk: 

- Uproszczony proces konfiguracji w Microsoft Defender dla Firm (*zalecane*) 
- Microsoft Endpoint Manager, w tym Microsoft Intune (zawarte w [Microsoft 365 Business Premium](../../business-premium/index.md))
- Rozwiązanie firmy innej niż Microsoft do zarządzania urządzeniami 

## <a name="what-to-do"></a>Co robić

1. [Przejrzyj opcje konfiguracji i konfiguracji](#review-your-setup-and-configuration-options)

2. [Dowiedz się więcej o uproszczonym procesie konfiguracji w usłudze Defender dla firm](#why-we-recommend-using-the-simplified-configuration-process)

3. [Przejdź do następnych kroków](#next-steps)

>
> **Masz minutę?**
> Weźmy <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę dotyczącą Microsoft Defender dla Firm</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="review-your-setup-and-configuration-options"></a>Przejrzyj opcje konfiguracji i konfiguracji

W poniższej tabeli opisano każde środowisko:
<br/><br/>

| Środowisko portalu  | Opis  |
|---------|---------|
| Uproszczone środowisko konfiguracji w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Jest to zalecana opcja dla większości klientów*)  | Uproszczone środowisko konfiguracji obejmuje środowisko podobne do kreatora, które ułatwia konfigurowanie i konfigurowanie usługi Defender for Business. Uproszczona konfiguracja obejmuje również domyślne ustawienia zabezpieczeń i zasady ułatwiające ochronę urządzeń firmy po ich dołączeniu do usługi Defender dla Firm. <br/><br/>W tym środowisku zespół ds. zabezpieczeń używa portalu Microsoft 365 Defender do: <br/>— Konfigurowanie i konfigurowanie usługi Defender dla firm <br/>— Wyświetlanie zdarzeń i zarządzanie nimi<br/>— Reagowanie na zagrożenia i ich eliminowanie<br/>— Wyświetlanie raportów<br/>— Przeglądanie oczekujących lub zakończonych akcji <br/><br/> Portal Microsoft 365 Defender jest punktem obsługi ustawień zabezpieczeń i możliwości ochrony przed zagrożeniami w firmie. Masz uproszczone środowisko ułatwiające szybkie i wydajne rozpoczęcie pracy. Aby dowiedzieć się więcej, zobacz [Konfigurowanie Microsoft Defender dla Firm za pomocą kreatora](mdb-use-wizard.md).<br/><br/>Możesz również edytować ustawienia lub definiować nowe zasady zgodnie z potrzebami twojej firmy.<br/><br/>Aby dowiedzieć się więcej, zobacz [Wyświetlanie lub edytowanie zasad urządzeń w Microsoft Defender dla Firm](mdb-view-edit-policies.md). |
| Centrum administracyjne Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Endpoint Manager obejmuje Microsoft Intune, opartego na chmurze dostawcę zarządzania urządzeniami przenośnymi (MDM) i zarządzania aplikacjami mobilnymi (MAM) dla aplikacji i urządzeń. [Microsoft 365 Business Premium](../../business-premium/index.md) klienci mają już Endpoint Manager. <br/><br/>Wiele firm używa Intune do zarządzania swoimi urządzeniami, takimi jak telefony komórkowe, tablety i laptopy. Aby dowiedzieć się więcej, zobacz [Microsoft Intune jest dostawcą zarządzania urządzeniami przenośnymi i zarządzaniem aplikacjami mobilnymi dla urządzeń](/mem/intune/fundamentals/what-is-intune). <br/><br/>Jeśli już używasz Microsoft Intune lub Microsoft Endpoint Manager, możesz nadal korzystać z tego rozwiązania. |
| Rozwiązanie do zarządzania urządzeniami firm innych niż Microsoft  | Jeśli używasz rozwiązania do zarządzania produktywnością i urządzeniami spoza firmy Microsoft, możesz nadal korzystać z tego rozwiązania w usłudze Defender for Business. <br/><br/>Gdy urządzenia zostaną dołączone do usługi Defender dla Firm, zobaczysz ich stan i alerty w portalu Microsoft 365 Defender. Aby dowiedzieć się więcej, zobacz [Opcje narzędzia dołączania i konfiguracji dla usługi Defender for Endpoint](../defender-endpoint/onboard-configure.md). |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Dlaczego zalecamy korzystanie z uproszczonego procesu konfiguracji

**Zalecamy korzystanie z uproszczonego procesu konfiguracji w Microsoft Defender dla Firm** dla większości klientów. Uproszczony proces konfiguracji jest usprawniony szczególnie w przypadku małych i średnich firm. Usługa Defender dla Firm została zaprojektowana tak, aby ułatwić ochronę urządzeń firmy pierwszego dnia bez konieczności posiadania głębokiej wiedzy technicznej ani specjalnej wiedzy. W przypadku domyślnych ustawień zabezpieczeń i zasad urządzenia są chronione natychmiast po ich dołączeniu.

Usługa Defender dla firm została zaprojektowana tak, aby zapewnić silną ochronę, jednocześnie oszczędzając czas i nakład pracy podczas konfigurowania ustawień zabezpieczeń. Usprawnione środowisko w portalu Microsoft 365 Defender ułatwia dołączanie urządzeń i zarządzanie nimi. Ponadto zasady domyślne są uwzględniane w taki sposób, aby urządzenia firmy były chronione natychmiast po ich dołączeniu. Ustawienia domyślne można zachować w miarę ich potrzeb lub wprowadzać zmiany zgodnie z potrzebami biznesowymi. Możesz również dodać nowe zasady do zarządzania urządzeniami w razie potrzeby.

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie i konfigurowanie Microsoft Defender dla Firm](mdb-setup-configuration.md)

- [Wprowadzenie przy użyciu Microsoft Defender dla Firm](mdb-get-started.md)
