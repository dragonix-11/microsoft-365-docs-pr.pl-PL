---
title: Wprowadzenie do Eksploratora działań
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Eksplorator działań umożliwia wyświetlanie i filtrowanie akcji wykonywanych przez użytkowników w zawartości oznaczonej etykietą.
ms.openlocfilehash: fc74e8c5e11834b14c6aa8a3f80d43e20c43ec11
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642025"
---
# <a name="get-started-with-activity-explorer"></a>Wprowadzenie do eksploratora aktywności

Karty [Omówienie klasyfikacji danych](data-classification-overview.md) i [Eksplorator zawartości](data-classification-content-explorer.md) zapewniają wgląd w zawartość, która została odnaleziona i oznaczona etykietami oraz gdzie znajduje się ta zawartość. Eksplorator działań zaokrągla ten zestaw funkcji, umożliwiając monitorowanie działań wykonywanych za pomocą zawartości oznaczonej etykietą. Eksplorator działań udostępnia historyczny widok działań dotyczących zawartości oznaczonej etykietą. Informacje o działaniach są zbierane z ujednoliconych dzienników inspekcji platformy Microsoft 365, przekształcane i udostępniane w interfejsie użytkownika Eksploratora działań. Eksplorator aktywności raportuje dane o wartości do 30 dni.

![Eksplorator działań przeglądu symbolu zastępczego.](../media/data-classification-activity-explorer-1.png)

Dostępnych jest ponad 30 różnych filtrów, niektóre z nich to:

- Zakres dat
- Typ działania
- Lokalizacja
- Użytkownik
- Etykieta poufności
- Etykieta przechowywania
- Ścieżka pliku
- Zasady DLP



## <a name="prerequisites"></a>Wymagania wstępne

Każde konto, które uzyskuje dostęp do klasyfikacji danych i korzysta z niej, musi mieć przypisaną licencję z jednej z tych subskrypcji:

- Microsoft 365 (E5)
- Office 365 (E5)
- Dodatek Zaawansowana zgodność (E5)
- Dodatek zaawansowanej analizy zagrożeń (E5)
- & Microsoft 365 E5/A5 — ochrona informacji
- Zgodność Microsoft 365 E5/A5

### <a name="permissions"></a>Uprawnienia

Konto musi mieć jawnie przypisane członkostwo w dowolnej z tych grup ról lub jawnie przyznać rolę.

### <a name="roles-and-role-groups-in-preview"></a>Role i grupy ról w wersji zapoznawczej

W wersji zapoznawczej dostępne są role i grupy ról, które można przetestować, aby dostosować mechanizmy kontroli dostępu.

Oto lista odpowiednich ról w wersji zapoznawczej. Aby dowiedzieć się więcej na ich temat, zobacz [Role w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Administracja
- analityk Information Protection
- badacz Information Protection
- czytelnik Information Protection

Oto lista odpowiednich grup ról, które są w wersji zapoznawczej. Aby dowiedzieć się więcej na temat programu , zobacz [Grupy ról w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- administratorzy Information Protection
- analitycy Information Protection
- Information Protection śledczy
- czytniki Information Protection

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Grupy ról platformy Microsoft 365**

- Administrator globalny
- Administrator zgodności
- Administrator zabezpieczeń
- Administrator danych zgodności

**Role platformy Microsoft 365**

- Administrator zgodności
- Administrator zabezpieczeń
- Czytelnik zabezpieczeń

## <a name="activity-types"></a>Typy działań

Eksplorator działań zbiera informacje o aktywności z dzienników inspekcji w wielu źródłach działań. Aby uzyskać bardziej szczegółowe informacje na temat działania etykietowania w Eksploratorze działań, zobacz [Etykietowanie zdarzeń dostępnych w Eksploratorze działań](data-classification-activity-explorer-available-events.md).

**Działania etykiet poufności** i **działania etykietowania przechowywania** z aplikacji natywnych pakietu Office, dodatku azure Information Protection, usługi SharePoint Online, Exchange Online (tylko etykiety poufności) i usługi OneDrive. Oto kilka przykładów:

- Zastosowana etykieta
- Zmieniono etykietę (uaktualniono, obniżono lub usunięto)
- Symulacja automatycznego etykietowania
- Odczyt pliku

**Skaner usługi Azure Information Protection (AIP) i klienci AIP**

- Zastosowana ochrona
- Zmieniono ochronę
- Usunięto ochronę
- Odnaleziono pliki

Eksplorator działań zbiera również **zasady DLP pasujące** do zdarzeń z Exchange Online, SharePoint Online, OneDrive, Teams Chat i Channel (wersja zapoznawcza), lokalnych folderów i bibliotek programu SharePoint oraz lokalnych udziałów plików oraz urządzeń Windows 10 za pośrednictwem **ochrony przed utratą danych punktu końcowego (DLP).** Oto kilka przykładowych zdarzeń z urządzeń Windows 10:

- Usunięcia
- Kreacje
- Skopiowane do schowka
- Zmodyfikowano
- Odczytu
- Drukowane
- Zmieniona
- Kopiowane do udziału sieciowego
- Dostęp do aplikacji bez uprawnień 

Zrozumienie, jakie akcje są wykonywane przy użyciu zawartości z etykietami poufnymi, ułatwia sprawdzenie, czy wprowadzone kontrolki, takie jak [zasady Ochrona przed utratą danych w Microsoft Purview](dlp-learn-about-dlp.md), są skuteczne lub nie. Jeśli nie, lub jeśli odkryjesz coś nieoczekiwanego, na przykład dużą liczbę elementów oznaczonych etykietą `highly confidential` i obniżoną, `general`możesz zarządzać różnymi zasadami i podejmować nowe akcje w celu ograniczenia niepożądanego zachowania.

> [!NOTE]
> Eksplorator działań nie monitoruje obecnie działań przechowywania dla Exchange Online.

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o etykietach poufności](sensitivity-labels.md)
- [Dowiedz się więcej o zasadach przechowywania i etykietach przechowywania](retention.md)
- [Dowiedz się więcej o typach informacji poufnych](sensitive-information-type-learn-about.md)
- [Dowiedz się więcej o klasyfikacji danych](data-classification-overview.md)
