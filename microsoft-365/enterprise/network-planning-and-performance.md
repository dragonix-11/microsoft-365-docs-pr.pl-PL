---
title: Planowanie sieci i dostosowywanie wydajności dla Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 2/18/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Strat_O365_Enterprise
f1.keywords:
- CSH
search.appverid:
- MET150
ms.assetid: e5f1228c-da3c-4654-bf16-d163daee8848
ms.custom:
- seo-marvel-apr2020
- Adm_O365
description: Ten artykuł pomoże Ci zaplanować wymagania w zakresie przepustowości sieci Microsoft 365 oraz precyzyjnie dostosować wydajność i rozwiązać problemy z wydajnością.
ms.openlocfilehash: 628d532a106ce9776443b252c863fa8bdc221b4b
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014894"
---
# <a name="network-planning-and-performance-tuning-for-microsoft-365"></a>Planowanie sieci i dostosowywanie wydajności dla Microsoft 365
Przed wdrożeniem usługi Microsoft 365 po raz pierwszy lub przed przeprowadzeniem migracji do usługi Microsoft 365 możesz użyć informacji owanych w tych tematach do oszacowania potrzebnej przepustowości, a następnie do przetestowania i sprawdzenia, czy masz przepustowość wystarczającą do wdrożenia lub migracji do usługi Microsoft 365. Aby uzyskać omówienie, zobacz: [Planowanie sieci i migracji dla sieci Microsoft 365](network-and-migration-planning.md).
  
|Kategoria |Opis |Kategoria |Opis |
|:-----|:-----|:-----|:-----|
|**Planowanie sieci** <br/> ![Sieć.](../media/5e9dcd06-601b-4b28-88dc-f524e7548794.png)           <br/> |Chcesz szybkich połączeń i stron, które szybko się ładują?  <br/> Przeczytaj [Uzyskiwanie najlepszej łączności i wydajności w aplikacji Microsoft 365](https://aka.ms/o365perfprinciples).<br/>Przeczytaj [Microsoft 365 omówienie łączności sieciowej](microsoft-365-networking-overview.md), aby poznać pojęcia.<br/> |**Mierzenie sieci** <br/> ![Kalkulator](../media/d690a132-4884-40eb-a918-526bb3dff3cc.png)           <br/> |Przeczytaj [Microsoft 365 dostosowywanie wydajności przy użyciu planów bazowych](performance-tuning-using-baselines-and-history.md) i historii wydajności oraz [Plan](performance-troubleshooting-plan.md) rozwiązywania problemów z wydajnością Microsoft 365.  <br/> Za pomocą tych narzędzi [oceń istniejącą sieć](network-and-migration-planning.md#calculators).  <br/> |
|**Najważniejsze wskazówki** <br/> ![Najlepsze rozwiązania.](../media/2a659a5c-1007-47d3-a6c6-a19e018ab29b.png)           <br/> |[Najlepsze rozwiązania dotyczące planowania sieci i poprawy wydajności migracji w przypadku Microsoft 365](network-and-migration-planning.md#BestPractices). Chcesz od razu rozpocząć pomaganie użytkownikom? Zobacz [Najlepsze rozwiązania dotyczące korzystania Office 365 w wolno wolno sieci](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166).  <br/> [Microsoft 365 dotyczących łączności sieciowej](./microsoft-365-network-connectivity-principles.md) pomogą w zrozumieniu najnowszych wskazówek dotyczących bezpiecznego optymalizowania Microsoft 365 sieci.  <br/> |**Odwołanie** <br/> ![Książka lub Dziennik](../media/56dff3c1-f605-48d8-811f-7d13ce639ecd.png)           <br/> |Chcesz uzyskać szczegółowe informacje, takie jak lista adresów IP i portów? Aby uzyskać [więcej informacji, zobacz Informacje dotyczące planowania Microsoft 365](network-and-migration-planning.md#NetReference).  <br/> |
|![Zobacz plakat Sieci oparte na chmurze Enterprise architektów chmury firmy Microsoft.](../media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)           <br/> |Aby uzyskać instrukcje dotyczące optymalizowania sieci pod kątem usług Microsoft 365 oraz innych platform i usług w chmurze firmy Microsoft, zobacz plakat Sieci oparte na chmurze firmy Microsoft dla Enterprise [architektów architektury](../solutions/cloud-architecture-models.md).  <br/> |
   
## <a name="performance-tuning-and-troubleshooting-resources-for-microsoft-365"></a>Dostosowywanie wydajności i zasoby dotyczące rozwiązywania problemów dla Microsoft 365
<a name="apptuning"> </a>

Po wdrożeniu Microsoft 365 możesz zoptymalizować wydajność, korzystając z tematów w tej sekcji. Jeśli odczuwasz spadek wydajności, możesz również skorzystać z tych tematów, aby rozwiązać problemy.
  
 **[Dostosowywanie Office 365](tune-microsoft-365-performance.md)** wydajności: Aby uzyskać informacje na temat korzystania z translacji adresów sieciowych Office 365, zobacz Obsługa [NAT z siecią Office 365](nat-support-with-microsoft-365.md). Ponadto zobacz 10 najlepszych porad dotyczących optymalizacji łączności sieciowej i rozwiązywania związanych z [Office 365 sieciową](/archive/blogs/onthewire/top-10-tips-for-optimising-troubleshooting-your-office-365-network-connectivity).
  
 **[Dostosowywanie Exchange Online wydajności](tune-exchange-online-performance.md)**. Te artykuły są w celu precyzyjnego dostosowania Exchange Online wydajności.

 **[Przygotowywanie sieci organizacji do Microsoft Teams](/microsoftteams/prepare-network)**: Skorzystaj z tych artykułów, aby zoptymalizować sieć pod kątem Teams.
  
 **[Dostosowywanie Skype dla firm online](tune-skype-for-business-online-performance.md)**. Te artykuły są dostępne w celu precyzyjnego dostosowania Skype dla firm online.
  
 **[Dostosowywanie SharePoint online](tune-sharepoint-online-performance.md)**. Te artykuły są dostępne w celu precyzyjnego dostosowania SharePoint online.
  
 **[Dostosowywanie Project Online wydajności](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)**: ten artykuł pozwala precyzyjnie dostosować Project Online wydajności
