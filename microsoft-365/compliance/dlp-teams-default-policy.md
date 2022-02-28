---
title: Informacje o domyślnych zasadach ochrony przed utratą danych w aplikacji Microsoft Teams (wersja zapoznawcza)
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
ms.openlocfilehash: 61a1ea22362d9e75d605660d29116140f6708003
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990508"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>Informacje o domyślnych zasadach ochrony przed utratą danych w aplikacji Microsoft Teams (wersja zapoznawcza)

[Funkcje ochrony przed utratą](dlp-learn-about-dlp.md) danych zostały rozszerzone tak, aby obejmowały Microsoft Teams czatów i wiadomości kanałów, w tym wiadomości w kanałach prywatnych. W ramach tej wersji tworzona jest domyślna zasada DLP dla klientów, którzy po raz Microsoft Teams po raz pierwszy, do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365.</a>

## <a name="applies-to"></a>Dotyczy

Dowolna dzierżawa, która ma licencję na co najmniej jedną z poniższych licencji i ma aktywnych Teams użytkowników
 
- ME5, 
- MA5, 
- Zgodność Z E5/A5, 
- IP+G, 
- OE5, 
- Zaawansowana zgodność z o365 
- EMS E5


## <a name="what-does-the-default-policy-do"></a>Do czego mają być włączone zasady domyślne?

Domyślne zasady DLP dla Teams śledzi wszystkie numery kart kredytowych udostępnione wewnętrznie i zewnętrznie w organizacji. Te zasady są domyślnie włączone dla wszystkich użytkowników dzierżawy. Nie generuje żadnych porad dotyczących zasad dla użytkowników końcowych, ale generuje zdarzenie Alert i wyzwala do administratora wiadomość e-mail o niskim poziomie ważności (dodane w zasadach). Administrator może wyświetlać działania i edytować szczegóły zasad, logując się do Centrum zgodności.

Administratorzy mogą wyświetlić te zasady na stronie [Centrum](https://compliance.microsoft.com/compliancesettings) zgodności > stronie Zasady ochrony przed utratą danych.


> [!div class="mx-imgBorder"]
> ![domyślne Teams DLP.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Edytowanie lub usuwanie zasad domyślnych

Aby [edytować zasady domyślne w celu zapewnienia lepszej wydajności](create-test-tune-dlp-policy.md#tune-a-dlp-policy) lub ich usunięcia, wystarczy użyć konta z uprawnieniami **do zarządzania zgodnością DLP** . Aby uzyskać więcej informacji, zobacz [Uprawnienia](create-test-tune-dlp-policy.md#permissions).

