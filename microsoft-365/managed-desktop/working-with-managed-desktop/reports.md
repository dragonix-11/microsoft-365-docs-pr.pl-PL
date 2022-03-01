---
title: Praca z raportami
description: Różne raporty dostępne w programie Microsoft Managed Desktop
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 620e9d2bd95dc4782237af94966b5cb52579b656
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014755"
---
# <a name="work-with-reports"></a>Praca z raportami

Konsola Microsoft Endpoint Manager łączy raporty z kilku produktów w jedną lokalizację, co pomaga monitorować i badać problemy z konfiguracją i urządzeniami organizacji usługi Azure AD ("dzierżawy").

Microsoft Managed Desktop ma sekcję **w menu** Raporty, gdzie można znaleźć raporty specyficzne Microsoft Managed Desktop zarządzania zarejestrowanymi urządzeniami przez użytkownika. W kilku różnych Microsoft Endpoint Manager można filtrować raporty z innych grup produktów. Możesz uwzględnić lub wykluczyć urządzenia zarządzane przez Microsoft Managed Desktop.

## <a name="microsoft-managed-desktop-reports"></a>Microsoft Managed Desktop raportów

Microsoft Managed Desktop udostępnia kilka raportów i pulpitów nawigacyjnych. Administratorzy IT w Twojej organizacji mogą używać tych raportów i pulpitów nawigacyjnych do zrozumienia różnych aspektów populacji urządzeń. W Microsoft Endpoint Manager przejdź do sekcji Raporty, a następnie w Microsoft Managed Desktop wybierz pozycję Urządzenia zarządzane.

Na karcie **Podsumowanie** znajdziesz szybkie metryki aktualizacji urządzeń. Wybierz **pozycję Wyświetl szczegóły każdej** metryki, aby pobrać dodatkowe informacje do analizy w trybie offline, w tym zestaw danych źródłowych metryki.

Po wybraniu karty **Raporty** będą dostępne opisy dostępnych raportów szczegółowych. Te raporty są bardziej wyczerpujące i obsługują wizualizację danych oraz filtrowanie w portalu. Możesz również wyeksportować dane źródłowe do analizy lub dystrybucji w trybie offline. Obecnie dostępne są następujące raporty:

| Raport | Opis |
| ------ | ------ |
| [**Raport o stanie** urządzenia](device-status-report.md) (*w podglądzie*) | Ten raport pokazuje korzystanie z usługi Microsoft Managed Desktop na podstawie aktywności i użycia urządzenia. |
| **Trend stanu urządzenia** (*w podglądzie*) | To pozwala monitorować trendy w stanie urządzeń z ostatnich 60 dni w przypadku Microsoft Managed Desktop urządzeniach. Trendy mogą ułatwić kojarzenie stanu urządzenia z innymi zmianami w czasie, na przykład z nowymi wdrożeniami. |
| [**Windows aktualizacji zabezpieczeń**](security-updates-report.md) (w *wersji Preview*) | W tym raporcie pokazano, Windows aktualizacje zabezpieczeń są zwalniane na różnych Microsoft Managed Desktop urządzeniach. |
| [**Raport użycia** aplikacji](app-usage-report.md) | Ten raport zawiera informacje na temat typowego użycia aplikacji na Microsoft Managed Desktop urządzeniach. Aby urządzenia zapewniały dane do tego raportu, muszą one mieć ustawiony opcjonalny poziom danych diagnostycznych. |
| [**Raport Metryki usługi**](service-metrics-report.md) (*w wersji zapoznawczej*) | Ten raport zawiera proste podsumowania kluczowych metryk dla Microsoft Managed Desktop miesiąc po miesiącu. |

## <a name="endpoint-analytics"></a>Analiza punktu końcowego

Microsoft Managed Desktop jest teraz zintegrowane z analizą [punktu końcowego](/mem/analytics/overview). Raporty te zapewniają szczegółowe informacje dotyczące sposobu działania organizacji i jakości środowiska dostarczanego użytkownikom. Analiza punktu końcowego znajduje się w menu **Raporty** [Microsoft Endpoint Manager.](https://endpoint.microsoft.com/) Aby przełączyć wynik tak, aby uwzględnić tylko urządzenia zarządzane przez Microsoft Managed Desktop, przejdź do dowolnego raportu, wybierz listę rozwijaną  Filtr, a następnie wybierz pozycję Microsoft Managed Desktop **urządzenia**.

Jeśli analiza punktu końcowego nie była automatycznie skonfigurowana dla Twojej organizacji usługi Azure AD ("dzierżawy") podczas rejestrowania, możesz to zrobić samodzielnie. Aby uzyskać więcej informacji, zobacz [Temat "Wnoszy" w portalu analizy punktu końcowego](/mem/analytics/enroll-intune#bkmk_onboard). Możesz zarejestrować wszystkie swoje urządzenia lub, jeśli chcesz uwzględnić tylko urządzenia z systemem Microsoft Managed Desktop, wybrać grupy urządzeń nowoczesnego miejsca pracy dla  opcji Test, Pierwsze, Szybkie i Szerokie. Te raporty mogą wymagać innych uprawnień. Aby uzyskać więcej informacji, [zobacz Uprawnienia](/mem/analytics/overview#permissions) w celu zapewnienia odpowiedniego przypisania ról.

> [!NOTE]
> Aby lepiej przestrzegać prywatności użytkowników, aby użyć tego filtru, należy użyć ponad 10 Microsoft Managed Desktop zarejestrowanych przy użyciu analizy punktu końcowego.

## <a name="intune-reports"></a>Raporty usługi Intune

Microsoft Intune jest jedną z usług, których używamy do zarządzania urządzeniami w Twoim imieniu.

W niektórych przypadkach warto skorzystać z raportów usługi Intune, aby monitorować administrowanie Twoimi Microsoft Managed Desktop komputerami. Z raportu, który używasz do zarządzania innymi urządzeniami, możesz wykluczyć urządzenia, które zarządzamy. Poniższe raporty umożliwiają filtrowanie możliwości dołączania i wykluczeń Microsoft Managed Desktop urządzeniach.

- [Wszystkie urządzenia](/mem/intune/remote-actions/device-management#get-to-your-devices)
- [Zgodność urządzenia](/mem/intune/fundamentals/reports#device-compliance-report-organizational)
- [Urządzenia nieuprawniane](/mem/intune/fundamentals/reports#noncompliant-devices-report-operational)

> [!NOTE]
> Niestandardowe Microsoft Managed Desktop gwarantuje dostęp tylko do raportów Microsoft Managed Desktop użytkowników. Aby uzyskać dostęp do innych części Microsoft Endpoint Manager, takich jak **Wszystkie urządzenia**, zobacz Kontrola dostępu oparta na rolach [z Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

## <a name="microsoft-managed-desktop-inventory-data"></a>Microsoft Managed Desktop danych o zapasach

Oprócz innych raportów możesz eksportować informacje o urządzeniach zarządzanych przez firmę Microsoft Managed Desktop. W Microsoft Endpoint Manager przejdź do sekcji Urządzenia, w obszarze  Microsoft Managed Desktop wybierz pozycję Urządzenia i użyj karty Eksportuj wszystkie, aby pobrać [szczegółowy raport o zapasach](device-inventory-report.md).
