---
title: Microsoft Managed Desktop i ITIL
description: Koreluje fazy itIL z Microsoft Managed Desktop informacjami i artykułami
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja, ITISM
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: b9984e308b6681512297e484817f95206283385e
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2022
ms.locfileid: "63026811"
---
# <a name="microsoft-managed-desktop-and-itil"></a>Microsoft Managed Desktop i ITIL

Wiele organizacji ceni sobie strukturę swoich usług IT zgodnie z formalnym modelem usług IT, takim jak [ITIL](https://www.axelos.com/best-practice-solutions/itil). 

Microsoft Managed Desktop umożliwia organizacji zgodność z wieloma kluczowymi aspektami tak sformalizowanych modeli ITSM. Korzystając z funkcji ITIL jako przykładu, ten artykuł ułatwia wyświetlanie połączeń między wspólnymi fazami i procesami itilu oraz równoważne funkcje Microsoft Managed Desktop, tam gdzie to możliwe. Te informacje dotyczą tylko części Microsoft Managed Desktop organizacji.

Aby uzyskać bardziej wyczerpujące informacje na temat programu ITIL oraz jego faz i procesów, zapoznaj się z ich [dokumentacją](https://www.axelos.com/best-practice-solutions/itil).


## <a name="service-design"></a>Projekt usługi

Ta tabela dotyczy kluczowych faz i procesów itIL z funkcjami Microsoft Managed Desktop, z linkami do naszej dokumentacji, aby uzyskać szczegółowe informacje:



|Proces ITIL |Opis  |Dokumentacja |
|---------|---------|---------|
|Zarządzanie na poziomie usługi     | Czas odpowiedzi jest zdefiniowany dla zgłoszeń i zgłoszeń do pomocy technicznej administratorów.  |  [Pomoc techniczna dla administratorów Microsoft Managed Desktop](working-with-managed-desktop/admin-support.md)  |
|Zarządzanie katalogiem usług     | Opis usługi ze szczegółami składników usługi jest zawsze aktualny w stanie usługi, dostępny dla wszystkich obecnych i zainteresowanych klientów.<br><br>Wymagania wstępne szczegółowe dotyczące zrozumienia wymagań wymaganych do obsługi usługi.  | - [Microsoft Managed Desktop opisu usługi](service-description/index.md)<br><br>- [Przygotuj się do rejestracji w Microsoft Managed Desktop](get-ready/index.md)  |
|Zarządzanie zabezpieczeniami informacji     | Informacje zabezpieczające, w tym zabezpieczenia informacji dla usługi.<br><br> Zasady związane z zabezpieczeniami i inne informacje dotyczące sposobu konfigurowania urządzeń.   | - [Zabezpieczenia w Microsoft Managed Desktop](service-description/security.md)<br><br>- [Konfiguracja urządzenia](service-description/device-policies.md)  |
|Zarządzanie dostępnością     |  Microsoft Managed Desktop ponosi odpowiedzialność za dostępność usługi w twojej organizacji.<br><br>Administratorzy i użytkownicy mają trasy do odpowiedniej pomocy technicznej w przypadku problemów z usługą lub dostępnością. | - [Microsoft Managed Desktop i monitorowanie danych](service-description/operations-and-monitoring.md)<br><br>- [Pomoc techniczna dla administratorów Microsoft Managed Desktop](working-with-managed-desktop/admin-support.md)<br>- [Uzyskiwanie pomocy dla użytkowników](working-with-managed-desktop/end-user-support.md)  |



## <a name="service-transition"></a>Przejście do usługi


|Proces ITIL |Opis  |Dokumentacja |
|---------|---------|---------|
|Zarządzanie zmianami     | Zdefiniowana odpowiedzialność, przegląd procesów i typy związane z zarządzaniem zmianą.  | [Microsoft Managed Desktop i monitorowanie danych](service-description/operations-and-monitoring.md#change-management) |
|Zarządzanie wersjami i wdrażaniem     |  Microsoft Managed Desktop zarządza aktualizacjami dla urządzeń zarejestrowanych w usłudze.  | [Jak obsługiwane są aktualizacje w Microsoft Managed Desktop](service-description/updates.md)        |
|Zarządzanie zasobami usługi i konfiguracją     | Informacje dotyczące wdrażania pakietu Microsoft Managed Desktop organizacji są dostępne w portalu administracyjnym IT.  | [Pomoc techniczna dla administratorów Microsoft Managed Desktop](working-with-managed-desktop/admin-support.md) |
|Zarządzanie wiedzą     | Informacje na Microsoft Managed Desktop są aktualne w tej witrynie.   | [Historia zmian dla Microsoft Managed Desktop dokumentów](change-history-managed-desktop.md)        |



## <a name="service-operation"></a>Operacja serwisowa


|Proces ITIL |Opis  |Dokumentacja  |
|---------|---------|---------|
|Zarządzanie zdarzeniami     |  Podano szczegółowe informacje dotyczące monitorowania urządzeń.<br><br>Szczegółowe informacje na temat standardowych procedur Microsoft Managed Desktop dla tej usługi. |  - [Zabezpieczenia w Microsoft Managed Desktop](service-description/security.md)<br>- [Microsoft Managed Desktop i monitorowanie danych](service-description/operations-and-monitoring.md)       |
|Zarządzanie zdarzeniami  | Microsoft Managed Desktop zbada i będzie działać w przypadku zdarzeń według zdefiniowanych definicji ważności.  |  [Definicje ważności wniosku o pomoc techniczną](working-with-managed-desktop/admin-support.md#support-request-severity-definitions)       |
|Żądanie zarządzania realizacjami     |  Proces żądania informacji i żądań zmiany związanych z usługą Microsoft Managed Desktop są zdefiniowane.         |[Pomoc techniczna dla administratorów Microsoft Managed Desktop](working-with-managed-desktop/admin-support.md)         |
|Zarządzanie problemami     | Wszelkie problemy z usługą należy obecnie kierować do lokalnego zespołu konta. | Dokumentacja w zakresie opracowywania |
|Zarządzanie programem Access     | Składniki i obowiązki klienta dotyczące zarządzania w celu zapewnienia szczegółowej funkcjonalności.  | [Zarządzanie tożsamością i dostępem](service-description/security.md#identity-and-access-management)        |
