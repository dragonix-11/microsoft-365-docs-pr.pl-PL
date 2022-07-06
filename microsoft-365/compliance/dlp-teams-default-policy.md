---
title: Dowiedz się więcej o domyślnych zasadach DLP w usłudze Microsoft Teams (wersja zapoznawcza)
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
description: Dowiedz się więcej o domyślnych zasadach ochrony przed utratą danych w usłudze Microsoft Teams
ms.openlocfilehash: 5c3a5a116da90a41abcc459808e83176dc750fe1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624228"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>Dowiedz się więcej o domyślnych zasadach ochrony przed utratą danych w usłudze Microsoft Teams (wersja zapoznawcza)

[Ochrona przed utratą danych w Microsoft Purview](dlp-learn-about-dlp.md) możliwości zostały rozszerzone o komunikaty czatów i kanałów usługi Microsoft Teams, w tym wiadomości z kanału prywatnego. W ramach tej wersji utworliśmy domyślne zasady DLP dla usługi Microsoft Teams dla klientów po raz pierwszy w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a>.

## <a name="licensing"></a>Licencjonowanie

Aby uzyskać pełne informacje licencyjne dotyczące DLP w usłudze Microsoft Teams, zobacz [Information Protection: Ochrona przed utratą danych dla usługi Teams](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-teams).

## <a name="what-does-the-default-policy-do"></a>Co robią zasady domyślne?

Domyślne zasady DLP dla usługi Teams śledzą wszystkie numery kart kredytowych udostępnione wewnętrznie i zewnętrznie organizacji. Te zasady są domyślnie włączone dla wszystkich użytkowników dzierżawy. Nie generuje żadnych wskazówek dotyczących zasad dla użytkowników końcowych, ale generuje zdarzenie alertu, a także wyzwala wiadomość e-mail o niskiej ważności do administratora (dodaną w zasadach). Administrator może wyświetlać działania i edytować szczegóły zasad, logując się do Centrum zgodności.

Administratorzy mogą wyświetlać te zasady na stronie zasad ochrony przed utratą [danych portal zgodności Microsoft Purview](https://compliance.microsoft.com/compliancesettings) >.


> [!div class="mx-imgBorder"]
> ![domyślne zasady DLP usługi Teams.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Edytowanie lub usuwanie zasad domyślnych

Aby [edytować domyślne zasady w celu uzyskania lepszej wydajności lub usunąć je](create-test-tune-dlp-policy.md#tune-a-dlp-policy), wystarczy użyć konta z uprawnieniami **DLP Compliance Management** . Aby uzyskać więcej informacji, zobacz [Uprawnienia](create-test-tune-dlp-policy.md#permissions).

