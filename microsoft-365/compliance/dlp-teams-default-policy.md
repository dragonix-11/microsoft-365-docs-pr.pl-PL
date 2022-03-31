---
title: Dowiedz się więcej o domyślnych zasadach ochrony przed utratą danych w usłudze Microsoft Teams (wersja zapoznawcza)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Informacje o domyślnych zasadach ochrony przed utratą danych w aplikacji Microsoft Teams
ms.openlocfilehash: 61443cdfdc116e9c25d9dad24c968876ae5d0349
ms.sourcegitcommit: db2ed146b46ade9ea62eed9cb8efff5fea7a35e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2022
ms.locfileid: "64481369"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>Dowiedz się więcej o domyślnych zasadach ochrony przed utratą danych w usłudze Microsoft Teams (wersja zapoznawcza)

[Funkcje ochrony przed utratą](dlp-learn-about-dlp.md) danych zostały rozszerzone tak, aby obejmowały Microsoft Teams czatów i wiadomości kanałów, w tym wiadomości w kanałach prywatnych. W ramach tej wersji tworzona jest domyślna zasada DLP dla klientów, którzy po raz Microsoft Teams po raz pierwszy, do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365.</a>

## <a name="licensing"></a>Licencjonowanie

Aby uzyskać pełne informacje dotyczące licencjonowania ochrony przed utratą danych Microsoft Teams, zobacz [Information Protection: Ochrona przed utratą danych w przypadku Teams](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-teams).

## <a name="what-does-the-default-policy-do"></a>Do czego mają być włączone zasady domyślne?

Domyślne zasady DLP dla Teams śledzi wszystkie numery kart kredytowych udostępnione wewnętrznie i zewnętrznie w organizacji. Te zasady są domyślnie włączone dla wszystkich użytkowników dzierżawy. Nie generuje żadnych porad dotyczących zasad dla użytkowników końcowych, ale generuje zdarzenie Alert i wyzwala do administratora wiadomość e-mail o niskim poziomie ważności (dodane w zasadach). Administrator może wyświetlać działania i edytować szczegóły zasad, logując się do Centrum zgodności.

Administratorzy mogą wyświetlić te zasady na stronie [Centrum](https://compliance.microsoft.com/compliancesettings) zgodności > stronie Zasady ochrony przed utratą danych.


> [!div class="mx-imgBorder"]
> ![domyślne Teams DLP.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Edytowanie lub usuwanie zasad domyślnych

Aby [edytować zasady domyślne w celu zapewnienia lepszej wydajności](create-test-tune-dlp-policy.md#tune-a-dlp-policy) lub ich usunięcia, wystarczy użyć konta z uprawnieniami **do zarządzania zgodnością DLP** . Aby uzyskać więcej informacji, zobacz [Uprawnienia](create-test-tune-dlp-policy.md#permissions).

