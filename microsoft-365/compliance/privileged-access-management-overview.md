---
title: Informacje o zarządzaniu dostępem z uprawnieniami
description: Ten artykuł zawiera omówienie funkcji zarządzania dostępem z uprawnieniami w aplikacji Microsoft 365 oraz odpowiedzi na często zadawane pytania (często zadawane pytania).
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
f1.keywords:
- NOCSH
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.openlocfilehash: 4fb4b548d71cf3e1da11e3c861a16929ac7073d8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986652"
---
# <a name="learn-about-privileged-access-management"></a>Informacje o zarządzaniu dostępem z uprawnieniami

Zarządzanie dostępem z uprawnieniami umożliwia szczegółową kontrolę dostępu nad zadaniami administratora z uprawnieniami w Office 365. Pomaga chronić organizację przed naruszeniem zabezpieczeń, które korzystają z istniejących kont administratora o uprawnieniach z dostępem do poufnych danych lub dostępem do krytycznych ustawień konfiguracji. Zarządzanie dostępem z uprawnieniami wymaga, aby użytkownicy żądali dostępu na czas w celu ukończenia podwyższonych i uprzywilejowanych zadań za pomocą przepływu pracy zatwierdzania o wysokim zakresie i z ograniczeniami czasowymi. Ta konfiguracja zapewnia użytkownikom wystarczająco duży dostęp do danych podczas wykonywania zadań, nie ryzykując dostępu do poufnych danych i krytycznych ustawień konfiguracji. Włączenie zarządzania dostępem uprzywilejowanym w programie Microsoft 365 umożliwia organizacji działanie z zerowej pozycji i zapewnienie warstwy ochrony przed zagrożeniami dostępu administracyjnego na stojąco.

Aby uzyskać krótki przegląd zintegrowanej skrytki klienta i przepływu pracy zarządzania dostępem uprzywilejowanym, zobacz ten klip wideo Skrytka klienta i [zarządzanie dostępem z uprawnieniami](https://go.microsoft.com/fwlink/?linkid=2066800).

## <a name="layers-of-protection"></a>Warstwy ochrony

Zarządzanie dostępem z uprawnieniami uzupełnia inne dane i zabezpieczenia funkcji dostępu w obrębie Microsoft 365 zabezpieczeń. Obejmujący zarządzanie dostępem z uprawnieniami w ramach zintegrowanego i warstwowego podejścia do zabezpieczeń zapewnia model zabezpieczeń, który maksymalizuje ochronę poufnych informacji i Microsoft 365 konfiguracji. Jak pokazano na diagramie, kompilacje zarządzania dostępem z uprawnieniami oparte na ochronie zapewnianych przez natywne szyfrowanie danych Microsoft 365 i model zabezpieczeń kontroli dostępu opartej na rolach usług Microsoft 365. W przypadku korzystania z [usługi Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure) te dwie funkcje zapewniają kontrolę dostępu z dostępem w czasie rzeczywistym o różnych zakresach.

![Ochrona warstwowa w Microsoft 365.](../media/pam-layered-protection.png)

Zarządzanie dostępem z uprawnieniami jest zdefiniowane i objęte zakresem na poziomie zadań, natomiast usługa Azure AD Privileged Identity Management stosuje ochronę na poziomie  roli przy użyciu możliwości wykonywania wielu zadań. Usługa Azure AD Privileged Identity Management przede wszystkim pozwala zarządzać dostępami dla ról i grup ról usługi AD, natomiast zarządzanie dostępem z uprawnieniami w programie Microsoft 365 ma zastosowanie tylko na poziomie zadań.

- **Włączanie zarządzania dostępem z** uprawnieniami podczas już używania usługi Azure AD Privileged Identity Management: Dodanie zarządzania dostępem z uprawnieniami zapewnia kolejną szczegółową warstwę funkcji ochrony i inspekcji na temat dostępu Microsoft 365 danych.

- **Włączanie usługi Azure AD Privileged Identity Management** już przy użyciu zarządzania dostępem z uprawnieniami w programie Office 365: Dodanie usługi Azure AD Privileged Identity Management do zarządzania dostępem uprzywilejowanym może rozszerzyć dostęp uprzywilejowany do danych poza Microsoft 365  który jest zdefiniowany głównie przez role użytkownika lub tożsamość.  

## <a name="privileged-access-management-architecture-and-process-flow"></a>Architektura zarządzania dostępem z uprawnieniami i przepływ procesów

W każdym z poniższych procesów przedstawiono architekturę dostępu uprzywilejowanych oraz sposób jego interakcji z Microsoft 365, inspekcji i przestrzeni Exchange zarządzania.

### <a name="step-1-configure-a-privileged-access-policy"></a>Krok 1. Konfigurowanie zasad dostępu z uprawnieniami

Konfigurując zasady dostępu z uprawnieniami za pomocą programu [PowerShell](https://admin.microsoft.com) do zarządzania centrum administracyjne platformy Microsoft 365 lub programu Exchange, definiujesz zasady i procesy funkcji dostępu z uprawnieniami oraz atrybuty zasad w tym Microsoft 365. Działania są rejestrowane w Centrum zgodności &amp; zabezpieczeń. Zasady są teraz włączone i gotowe do obsługi przychodzących żądań zatwierdzenia.

![Krok 1. Tworzenie zasad.](../media/pam-step1-policy-creation.jpg)

### <a name="step-2-access-request"></a>Krok 2. Żądanie dostępu

W [centrum administracyjne platformy Microsoft 365 programu](https://admin.microsoft.com) PowerShell do zarządzania Exchange użytkownicy mogą zażądać dostępu do podwyższonych uprawnień lub zadań o podwyższonym poziomie uprawnień. Funkcja dostępu z uprawnieniami &amp; wysyła żądanie do administratora Microsoft 365 którego dotyczy przetwarzanie na skonfigurowanych zasadach dostępu uprawnień, i rejestruje działanie w dziennikach Centrum zgodności zabezpieczeń.

![Krok 2. Żądanie dostępu.](../media/pam-step2-access-request.jpg)

### <a name="step-3-access-approval"></a>Krok 3. Zatwierdzanie dostępu

Zostanie wygenerowane żądanie zatwierdzenia, a do osób zatwierdzających zostanie wysłana wiadomość e-mail z powiadomieniem o oczekującym żądaniu. Po zatwierdzeniu żądanie dostępu z uprawnieniami jest przetwarzane jako zatwierdzenie i zadanie jest gotowe do ukończenia. Jeśli zadanie zostanie odrzucone, zadanie zostanie zablokowane i żądany nie zostanie przyznany dostęp. Żądające są powiadamiane o zatwierdzeniu żądania lub odmowę w wiadomości e-mail.

![Krok 3. Zatwierdzanie dostępu.](../media/pam-step3-access-approval.jpg)

### <a name="step-4-access-processing"></a>Krok 4. Przetwarzanie w programie Access

W przypadku zatwierdzonego żądania zadanie jest przetwarzane przez Exchange Zarządzanie. Zatwierdzanie jest sprawdzane na zasadach dostępu z uprawnieniami i przetwarzane przez Microsoft 365 aprobatę. Wszystkie działania dotyczące zadania są rejestrowane w Centrum zgodności &amp; zabezpieczeń.

![Krok 4. Przetwarzanie w programie Access.](../media/pam-step4-access-processing.jpg)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="what-skus-can-use-privileged-access-in-office-365"></a>Jakie jednostki SKU mogą używać dostępu z uprawnieniami w programie Office 365?

Zarządzanie dostępem uprzywilejowanym jest dostępne dla klientów z bardzo szeroką ofertą Microsoft 365 i Office 365 i dodatków. Aby [uzyskać szczegółowe informacje, zobacz Wprowadzenie do zarządzania dostępem z uprawnieniami](privileged-access-management-configuration.md) .

### <a name="when-will-privileged-access-support-office-365-workloads-beyond-exchange"></a>Kiedy uprawnienia dostępu będą obsługiwać Office 365 obciążenia pracą poza Exchange?

Zarządzanie dostępem z uprawnieniami będzie wkrótce dostępne w innych Office 365 obciążeniami pracą. Odwiedź przewodnik [Microsoft 365,](https://www.microsoft.com/microsoft-365/roadmap) aby uzyskać więcej szczegółowych informacji.

### <a name="my-organization-needs-more-than-30-privileged-access-policies-will-this-limit-be-increased"></a>Moja organizacja potrzebuje ponad 30 zasad dostępu uprzywilejowanych. Czy ten limit zostanie zwiększony?

Tak, zwiększenie bieżącego limitu 30 zasad dostępu uprzywilejowanych na organizację jest w planie funkcji.

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Czy muszę być administratorem globalnym, aby zarządzać dostępem uprzywilejowanym w programie Office 365?

Nie, musisz mieć przypisaną Exchange Zarządzanie rolami do kont, które zarządzają dostępem z uprawnieniami w Office 365. Jeśli nie chcesz konfigurować roli Zarządzanie rolami jako uprawnienia konta autonomicznego, rola Administrator globalny domyślnie obejmuje tę rolę i może zarządzać dostępem z uprawnieniami. Użytkownicy przypisani do grupy osób zatwierdzających nie muszą być administratorami globalnymi ani mieć przypisanej roli Zarządzanie rolami do przeglądania i zatwierdzania wniosków za pomocą programu PowerShell.

### <a name="how-is-privileged-access-management-related-to-customer-lockbox"></a>Jak działa zarządzanie dostępem z uprawnieniami w odniesieniu do skrytki klienta?

[Skrytka klienta](/office365/admin/manage/customer-lockbox-requests) zapewnia poziom kontroli dostępu dla organizacji, gdy firma Microsoft uzyskuje dostęp do danych. Zarządzanie dostępem z uprawnieniami umożliwia szczegółową kontrolę dostępu w obrębie organizacji dla wszystkich Microsoft 365 zadań z uprawnieniami.

## <a name="ready-to-get-started"></a>Wszystko gotowe do rozpoczęcia?

Zacznij [konfigurować organizację do zarządzania dostępem z uprawnieniami](privileged-access-management-configuration.md).

## <a name="learn-more"></a>Dowiedz się więcej

[Interakcyjny przewodnik: Monitorowanie zadań administratora i kontrolowanie ich za pomocą funkcji zarządzania dostępem z uprawnieniami](https://content.cloudguides.com/guides/Privileged%20Access%20Management)
