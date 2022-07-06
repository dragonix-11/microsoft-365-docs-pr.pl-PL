---
title: Dowiedz się więcej o usłudze Privileged Access Management
description: Ten artykuł zawiera omówienie zarządzania dostępem uprzywilejowanym w usłudze Microsoft Purview, w tym odpowiedzi na często zadawane pytania.
keywords: Microsoft 365, Microsoft Purview, zgodność, uprzywilejowane zarządzanie dostępem
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
ms.openlocfilehash: 6bf13adb96ae5d4d4030ebe44f10dab22602196e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622552"
---
# <a name="learn-about-privileged-access-management"></a>Dowiedz się więcej o usłudze Privileged Access Management

Usługa Microsoft Purview Privileged Access Management umożliwia szczegółową kontrolę dostępu nad uprzywilejowanymi zadaniami administratora w Office 365. Może pomóc chronić organizację przed naruszeniami, które korzystają z istniejących kont administratorów uprzywilejowanych z stałym dostępem do poufnych danych lub dostępem do krytycznych ustawień konfiguracji. Zarządzanie dostępem uprzywilejowanym wymaga od użytkowników żądania dostępu just in time w celu wykonywania zadań z podwyższonym poziomem uprawnień i uprzywilejowanych za pośrednictwem przepływu pracy zatwierdzania o wysokim zakresie i ograniczonym czasem. Ta konfiguracja zapewnia użytkownikom wystarczający dostęp do wykonywania danego zadania bez ryzyka ujawnienia poufnych danych lub krytycznych ustawień konfiguracji. Włączenie zarządzania dostępem uprzywilejowanym umożliwia organizacji działanie bez stałych uprawnień i zapewnianie warstwy ochrony przed stałymi lukami w dostępie administracyjnym.

Aby zapoznać się z szybkim omówieniem zintegrowanego przepływu pracy funkcji Skrytka klienta i zarządzania dostępem uprzywilejowanym, zobacz [ten film wideo Dotyczący skrytki klienta i zarządzania dostępem uprzywilejowanym](https://go.microsoft.com/fwlink/?linkid=2066800).

## <a name="layers-of-protection"></a>Warstwy ochrony

Zarządzanie dostępem uprzywilejowanym uzupełnia inne zabezpieczenia danych i funkcji dostępu w ramach architektury zabezpieczeń platformy Microsoft 365. Uwzględnienie uprzywilejowanego zarządzania dostępem w ramach zintegrowanego i warstwowego podejścia do zabezpieczeń zapewnia model zabezpieczeń, który maksymalizuje ochronę informacji poufnych i ustawień konfiguracji platformy Microsoft 365. Jak pokazano na diagramie, zarządzanie dostępem uprzywilejowanym opiera się na ochronie zapewnianej za pomocą natywnego szyfrowania danych platformy Microsoft 365 oraz modelu zabezpieczeń kontroli dostępu opartego na rolach usług Microsoft 365. W przypadku użycia z [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure) te dwie funkcje zapewniają kontrolę dostępu z dostępem just in time w różnych zakresach.

![Ochrona warstwowa na platformie Microsoft 365.](../media/pam-layered-protection.png)

Zarządzanie dostępem uprzywilejowanym jest definiowane i ograniczone na poziomie **zadania**, a Azure AD Privileged Identity Management stosuje ochronę na poziomie **roli** z możliwością wykonywania wielu zadań. Azure AD Privileged Identity Management umożliwia przede wszystkim zarządzanie dostępami dla ról i grup ról usługi AD, podczas gdy usługa Microsoft Purview Privileged Access Management ma zastosowanie tylko na poziomie zadania.

- **Włączanie zarządzania dostępem uprzywilejowanym podczas korzystania już z Azure AD Privileged Identity Management:** dodawanie uprzywilejowanego zarządzania dostępem zapewnia kolejną szczegółową warstwę funkcji ochrony i inspekcji w celu uzyskania uprzywilejowanego dostępu do danych platformy Microsoft 365.

- **Włączanie Azure AD Privileged Identity Management podczas korzystania z usługi Microsoft Purview Privileged Access Management:** dodawanie Azure AD Privileged Identity Management  Do usługi Microsoft Purview Privileged Access Management można rozszerzyć uprzywilejowany dostęp do danych spoza platformy Microsoft 365, które są definiowane głównie przez role lub tożsamość użytkownika.  

## <a name="privileged-access-management-architecture-and-process-flow"></a>Architektura i przepływ procesów zarządzania dostępem uprzywilejowanym

Każdy z następujących przepływów procesu przedstawia architekturę uprzywilejowanego dostępu oraz sposób interakcji z podłożem platformy Microsoft 365, inspekcją i obszarem uruchomieniowym usługi Exchange Management.

### <a name="step-1-configure-a-privileged-access-policy"></a>Krok 1. Konfigurowanie zasad dostępu uprzywilejowanego

Podczas konfigurowania zasad dostępu uprzywilejowanego przy użyciu [programu Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) lub programu Exchange Management Programu PowerShell należy zdefiniować zasady oraz procesy funkcji dostępu uprzywilejowanego oraz atrybuty zasad w podłożu platformy Microsoft 365. Działania są rejestrowane w Centrum zgodności zabezpieczeń &amp; . Zasady są teraz włączone i gotowe do obsługi przychodzących żądań zatwierdzeń.

![Krok 1. Tworzenie zasad.](../media/pam-step1-policy-creation.jpg)

### <a name="step-2-access-request"></a>Krok 2. Żądanie dostępu

W [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) lub w programie Exchange Management PowerShell użytkownicy mogą żądać dostępu do zadań z podwyższonym poziomem uprawnień lub uprzywilejowanych. Funkcja dostępu uprzywilejowanego wysyła żądanie do podłoża platformy Microsoft 365 w celu przetwarzania względem skonfigurowanych zasad dostępu do uprawnień i rejestruje działanie w dziennikach Centrum zgodności zabezpieczeń &amp; .

![Krok 2. Żądanie dostępu.](../media/pam-step2-access-request.jpg)

### <a name="step-3-access-approval"></a>Krok 3. Zatwierdzanie dostępu

Generowane jest żądanie zatwierdzenia, a oczekujące powiadomienie o żądaniu jest wysyłane pocztą e-mail do osób zatwierdzających. Jeśli żądanie dostępu uprzywilejowanego zostanie zatwierdzone, zostanie przetworzone jako zatwierdzenie, a zadanie będzie gotowe do ukończenia. Jeśli zadanie zostanie odrzucone, zostanie zablokowane i nie zostanie udzielony dostęp do obiektu żądającego. Żądanie jest powiadamiane o zatwierdzeniu lub odmowie żądania za pośrednictwem wiadomości e-mail.

![Krok 3. Zatwierdzanie dostępu.](../media/pam-step3-access-approval.jpg)

### <a name="step-4-access-processing"></a>Krok 4. Przetwarzanie dostępu

W przypadku zatwierdzonego żądania zadanie jest przetwarzane przez obszar uruchomieniowy usługi Exchange Management. Zatwierdzenie jest sprawdzane pod kątem zasad dostępu uprzywilejowanego i przetwarzane przez podłoże platformy Microsoft 365. Wszystkie działania zadania są rejestrowane w Centrum zgodności zabezpieczeń &amp; .

![Krok 4. Przetwarzanie dostępu.](../media/pam-step4-access-processing.jpg)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="what-skus-can-use-privileged-access-in-office-365"></a>Jakie jednostki SKU mogą używać uprzywilejowanego dostępu w Office 365?

Zarządzanie dostępem uprzywilejowanym jest dostępne dla klientów w przypadku szerokiego wyboru subskrypcji i dodatków platformy Microsoft 365 i Office 365. Aby uzyskać szczegółowe informacje, zobacz [Wprowadzenie do zarządzania dostępem uprzywilejowanym](privileged-access-management-configuration.md) .

### <a name="when-will-privileged-access-support-office-365-workloads-beyond-exchange"></a>Kiedy uprzywilejowana obsługa dostępu Office 365 obciążeniach poza programem Exchange?

Zarządzanie dostępem uprzywilejowanym będzie wkrótce dostępne w innych obciążeniach Office 365. Aby uzyskać więcej informacji, odwiedź [stronę harmonogramu działania platformy Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) .

### <a name="my-organization-needs-more-than-30-privileged-access-policies-will-this-limit-be-increased"></a>Moja organizacja potrzebuje więcej niż 30 zasad dostępu uprzywilejowanego, czy ten limit zostanie zwiększony?

Tak, w planie działania funkcji jest podniesienie bieżącego limitu 30 zasad dostępu uprzywilejowanego dla organizacji.

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Czy muszę być Administracja globalnym, aby zarządzać uprzywilejowanym dostępem w Office 365?

Nie, potrzebujesz roli zarządzania rolami programu Exchange przypisanej do kont, które zarządzają uprzywilejowanym dostępem w Office 365. Jeśli nie chcesz konfigurować roli zarządzania rolami jako uprawnienia konta autonomicznego, rola administratora globalnego domyślnie obejmuje tę rolę i może zarządzać uprzywilejowanym dostępem. Użytkownicy w grupie osób zatwierdzających nie muszą być Administracja globalni ani mieć przypisanej roli Zarządzanie rolami w celu przeglądania i zatwierdzania żądań za pomocą programu PowerShell.

### <a name="how-is-privileged-access-management-related-to-customer-lockbox"></a>W jaki sposób zarządzanie dostępem uprzywilejowanym jest związane ze skrytą klienta?

[Blokada klienta](/office365/admin/manage/customer-lockbox-requests) umożliwia poziom kontroli dostępu dla organizacji, gdy firma Microsoft uzyskuje dostęp do danych. Zarządzanie dostępem uprzywilejowanym umożliwia szczegółową kontrolę dostępu w organizacji dla wszystkich zadań uprzywilejowanych platformy Microsoft 365.

## <a name="ready-to-get-started"></a>Chcesz rozpocząć?

[Rozpocznij konfigurowanie organizacji pod kątem zarządzania dostępem uprzywilejowanym](privileged-access-management-configuration.md).

## <a name="learn-more"></a>Dowiedz się więcej

[Interaktywny przewodnik: Monitorowanie i kontrolowanie zadań administratora przy użyciu uprzywilejowanego zarządzania dostępem](https://content.cloudguides.com/guides/Privileged%20Access%20Management)
