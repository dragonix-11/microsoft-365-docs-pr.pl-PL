---
title: Uproszczony proces konfiguracji w Microsoft Defender dla Firm
description: Usługa Defender dla Firm oszczędza czas działania firmy dzięki uproszczonym procesom konfiguracji. Zobacz, jak to działa i chroni Twoją firmę od pierwszego dnia.
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
- m365-initiative-defender-business
ms.openlocfilehash: f6cb1ff397233a60b0ad02a08486333790d079cc
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089445"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>Uproszczony proces konfiguracji w Microsoft Defender dla Firm

Microsoft Defender dla Firm oferuje uproszczony proces konfiguracji, zaprojektowany specjalnie dla małych i średnich firm. To środowisko pozwala zgadywać podczas dołączania urządzeń i zarządzania nimi przy użyciu środowiska przypominającego kreatora i domyślnych zasad, które zostały zaprojektowane w celu ochrony urządzeń firmy od pierwszego dnia. **Zalecamy korzystanie z uproszczonego procesu konfiguracji. Jednak nie ograniczasz się do tej opcji**.

Jeśli chodzi o dołączanie urządzeń i konfigurowanie ustawień zabezpieczeń dla urządzeń firmowych, możesz wybrać jedną z kilku środowisk: 

- Uproszczony proces konfiguracji w Microsoft Defender dla Firm (*zalecane*) 
- Microsoft Intune (zawarte w [Microsoft 365 Business Premium](../../business-premium/index.md))

## <a name="what-to-do"></a>Co robić

1. [Przejrzyj opcje konfiguracji i konfiguracji](#review-your-setup-and-configuration-options)
2. [Dowiedz się więcej o uproszczonym procesie konfiguracji w usłudze Defender dla firm](#why-we-recommend-using-the-simplified-configuration-process)
3. [Przejdź do następnych kroków](#next-steps)


## <a name="review-your-setup-and-configuration-options"></a>Przejrzyj opcje konfiguracji i konfiguracji

W poniższej tabeli opisano każde środowisko:

| Środowisko portalu  | Opis  |
|---------|---------|
| Uproszczone środowisko konfiguracji w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Jest to zalecana opcja dla większości klientów*)  | Uproszczone środowisko konfiguracji obejmuje środowisko podobne do kreatora, które ułatwia konfigurowanie i konfigurowanie usługi Defender for Business. Aby dowiedzieć się więcej, zobacz [Konfigurowanie Microsoft Defender dla Firm za pomocą kreatora](mdb-use-wizard.md).<br/><br/>Uproszczona konfiguracja obejmuje również domyślne ustawienia zabezpieczeń i zasady ułatwiające ochronę urządzeń firmy po ich dołączeniu do usługi Defender dla Firm. Możesz wyświetlić domyślne zasady i w razie potrzeby edytować zasady zgodnie z potrzebami biznesowymi. Aby dowiedzieć się więcej, zobacz [Wyświetlanie lub edytowanie zasad urządzeń w Microsoft Defender dla Firm](mdb-view-edit-policies.md).<br/><br/>Dzięki uproszczonemu środowisku twój zespół ds. zabezpieczeń korzysta z portalu Microsoft 365 Defender jako sklepu z jednym punktem obsługi, aby: <br/>— Konfigurowanie i konfigurowanie usługi Defender dla firm <br/>— Wyświetlanie zdarzeń i zarządzanie nimi<br/>— Reagowanie na zagrożenia i ich eliminowanie<br/>— Wyświetlanie raportów<br/>— Przeglądanie oczekujących lub zakończonych akcji  |
| Centrum administracyjne Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Intune jest opartym na chmurze dostawcą zarządzania urządzeniami przenośnymi (MDM) i zarządzania aplikacjami mobilnymi (MAM) dla aplikacji i urządzeń. Intune nie jest uwzględniona w autonomicznej wersji usługi Defender for Business, jednak [Microsoft 365 Business Premium](../../business-premium/index.md) obejmuje Intune.<br/><br/>Jeśli już używasz Intune, możesz użyć centrum administracyjnego Endpoint Manager do zarządzania urządzeniami, takimi jak telefony komórkowe, tablety i laptopy. Zobacz [Microsoft Intune: Zarządzanie urządzeniami](/mem/intune/fundamentals/what-is-device-management). |

## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Dlaczego zalecamy korzystanie z uproszczonego procesu konfiguracji

**Zalecamy korzystanie z uproszczonego procesu konfiguracji w Microsoft Defender dla Firm** dla większości klientów. 

- Uproszczony proces konfiguracji jest usprawniony szczególnie w przypadku małych i średnich firm. 
- Usługa Defender dla Firm nie wymaga głębokiej wiedzy technicznej ani specjalnej wiedzy. 
- W przypadku domyślnych ustawień zabezpieczeń i zasad urządzenia są chronione natychmiast po ich dołączeniu.
- Usprawnione środowisko w portalu Microsoft 365 Defender ułatwia dołączanie urządzeń i zarządzanie nimi. 
- Zasady domyślne są uwzględniane w taki sposób, aby urządzenia firmy były chronione natychmiast po ich dołączeniu.
- Ustawienia domyślne można zachować w miarę ich potrzeb lub wprowadzać zmiany zgodnie z potrzebami biznesowymi. 
- Możesz dodać nowe, niestandardowe zasady dostosowane do potrzeb biznesowych.

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie i konfigurowanie Microsoft Defender dla Firm](mdb-setup-configuration.md)
- [Wprowadzenie przy użyciu Microsoft Defender dla Firm](mdb-get-started.md)
