---
title: Exchange Multi-Geo
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Dowiedz się więcej na temat funkcji multi-geo w Exchange Online, takich jak ograniczenia funkcji i rozmieszczenie skrzynek pocztowych.
ms.openlocfilehash: c45c5c8e8856206fc2afc3e08005821f24dcd028
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010441"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Funkcje multi-Geo Capabilities w Exchange Online

W środowisku wielolokalowym możesz wybrać lokalizację skrzynki pocztowej, Exchange Online zawartości skrzynki pocztowej (danych w spoczynku) w zależności od użytkownika.

Skrzynki pocztowe możesz umieszczać w satelitarnych lokalizacjach geograficznych, korzystając z tych pozycji:

- Tworzenie nowej skrzynki Exchange Online lokalizacji geograficznej satelitarnej.

- Przenoszenie istniejącej Exchange Online pocztowej do lokalizacji geograficznej satelitarnej przez zmianę preferowanej lokalizacji danych użytkownika.

- Dołączanie skrzynki pocztowej z lokalnej organizacji Exchange bezpośrednio do lokalizacji geolokalizacji satelitarnej.

## <a name="mailbox-placement-and-moves"></a>Położenie i przeniesienie skrzynki pocztowej

Po zakończeniu wymaganej konfiguracji wielu lokalizacji geograficznych firma Microsoft Exchange Online atrybut **PreferredDataLocation** (Preferowana lokalizacjadanych) dla obiektów użytkowników w usłudze Azure AD.

Exchange Online synchronizuje właściwość **PreferredDataLocation** (Preferowana lokalizacjadanych) z usługi Azure AD z **właściwością MailboxRegion** w Exchange Online katalogu. Wartość **MailboxRegion określa lokalizację** geograficzną, w której zostaną umieszczone skrzynki pocztowe użytkowników i wszystkie skojarzone z nimi archiwalne skrzynki pocztowe. Nie można skonfigurować podstawowej skrzynki pocztowej ani archiwalnych skrzynek pocztowych użytkownika tak, aby znajdowały się w różnych lokalizacjach geograficznych. Na obiekt użytkownika można skonfigurować tylko jedną lokalizację geograficzną.

- Jeśli **dla użytkownika z** istniejącą skrzynką pocztową skonfigurowano preferowaną lokalizację danych, skrzynka pocztowa zostanie przeniesiona do kolejki kolejkowania i automatycznie przeniesiona do określonej lokalizacji geograficznej.

- Jeśli **dla użytkownika bez** istniejącej skrzynki pocztowej skonfigurowano preferowaną lokalizację danych, podczas inicjowania obsługi administracyjnej skrzynka pocztowa będzie zapewniana do określonej lokalizacji geograficznej.

- Jeśli **preferowanej lokalizacji danych** nie określono dla użytkownika, podczas inicjowania obsługi administracyjnej skrzynki pocztowej będzie ona zapewniana w centralnej lokalizacji geograficznej.

- Jeśli kod **PreferredDataLocation** jest nieprawidłowy (np. literówka nazwy NAN zamiast NAM), skrzynka pocztowa będzie zapewniana w centralnej lokalizacji geograficznej.

**Uwaga**: Funkcje multi-geo capabilities i Skype dla firm spotkania regionalne online używają właściwości **PreferredDataLocation** (Preferowana lokalizacjadanych) w obiektach użytkowników do lokalizowania usług. Jeśli skonfigurujesz wartości **preferowanej** lokalizacji danych w obiektach użytkowników dla spotkań hostowanych regionalnie, skrzynka pocztowa dla tych użytkowników zostanie automatycznie przeniesiona do określonej lokalizacji geograficznej po włączeniu obsługi wielu lokalizacji geograficznych w Microsoft 365 dzierżawie.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Ograniczenia funkcji dla wielu lokalizacji geograficznych w Exchange Online

- Funkcje zabezpieczeń i zgodności (na przykład inspekcja i zbierania elektronicznych materiałów dowodowych) dostępne w centrum administracyjnym programu Exchange nie są dostępne w organizacjach wielowymiarowych. Zamiast tego do konfigurowania funkcji zabezpieczeń [i zgodności Microsoft 365 będzie](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) konieczne & Centrum zabezpieczeń i zgodności.

- Outlook dla komputerów Mac użytkownicy mogą doświadczyć tymczasowej utraty dostępu do swojego folderu Archiwum online podczas przenoszenia ich skrzynek pocztowych do nowej lokalizacji geograficznej. Ten warunek występuje, gdy podstawowe i archiwalne skrzynki pocztowe użytkownika znajdują się w różnych lokalizacjach geograficznych, ponieważ przenoszenia skrzynek pocztowych między lokalizacjami geograficznymi mogą się odbywać w różnych momentach.

- Użytkownicy nie mogą udostępniać folderów *skrzynki pocztowej* w lokalizacjach geograficznych w programie Outlook w sieci Web (dawniej znany jako Outlook Web App lub OWA). Na przykład użytkownik w Unii Europejskiej nie może używać programu Outlook w sieci Web do otwierania folderu udostępnionego w skrzynce pocztowej znajdującej się w Stanach Zjednoczonych. Jednak użytkownicy Outlook sieci Web mogą otwierać inne skrzynki  pocztowe w różnych lokalizacjach geograficznych przy użyciu oddzielnego okna przeglądarki, jak to opisano w tece Otwieranie skrzynki pocztowej innej osoby w osobnym oknie przeglądarki w [programie Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

  **Uwaga**: Udostępnianie folderów między skrzynkami pocztowymi jest obsługiwane Outlook na Windows.

- Foldery publiczne są obsługiwane w organizacjach wielolokalizacji. Foldery publiczne muszą jednak pozostać w centralnej lokalizacji geograficznej. Nie można przenosić folderów publicznych do lokalizacji geograficznych satelitarnych.

- W środowisku z wieloma lokalizacjami geograficznymi inspekcja skrzynek pocztowych między geolokalizacji nie jest obsługiwana. Jeśli na przykład użytkownikowi przypisano uprawnienia dostępu do udostępnionej skrzynki pocztowej w innej lokalizacji geograficznej, akcje skrzynki pocztowej wykonywane przez tego użytkownika nie są rejestrowane w dzienniku inspekcji skrzynki pocztowej udostępnionej skrzynki pocztowej. Exchange inspekcji administratora są również dostępne tylko dla lokalizacji domyślnej. Aby uzyskać więcej informacji, zobacz [Zarządzanie inspekcją skrzynki pocztowej](../compliance/enable-mailbox-auditing.md).
