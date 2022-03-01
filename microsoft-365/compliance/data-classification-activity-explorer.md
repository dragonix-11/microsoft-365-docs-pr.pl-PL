---
title: Wprowadzenie do Eksploratora aktywności
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
description: Eksplorator aktywności umożliwia wyświetlanie i filtrowanie akcji, które użytkownicy mają na zawartości oznaczonej etykietą.
ms.openlocfilehash: 93cd3910a79b136d95ba46fa79940d379340cf75
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019364"
---
# <a name="get-started-with-activity-explorer"></a>Wprowadzenie do Eksploratora aktywności

Karty [przegląd klasyfikacji danych](data-classification-overview.md) i Eksplorator zawartości zapewniają wgląd w zawartość, która została wykryta i oznaczona etykietą, oraz miejsce, w którym ta zawartość się znajduje.[](data-classification-content-explorer.md) Eksplorator aktywności zaokrągla ten pakiet funkcji, umożliwiając monitorowanie, co jest wykonywane z zawartością oznaczoną etykietą. Eksplorator aktywności udostępnia historyczny widok działań na zawartości oznaczonej etykietą. Informacje o aktywności są zbierane z ujednoliconych Microsoft 365 inspekcji, przekształcane i udostępniane w interfejsie użytkownika Eksploratora aktywności. Eksplorator aktywności raportuje dane o wartości do 30 dni.

![Placeholder screenshot overview activity explorer.](../media/data-classification-activity-explorer-1.png)

Dostępnych jest ponad 30 różnych filtrów, niektóre są dostępne:

- Zakres dat
- Typ działania
- Lokalizacja
- Użytkownik
- Etykieta wrażliwości
- Etykieta przechowywania
- Ścieżka pliku
- Zasady DLP



## <a name="prerequisites"></a>Wymagania wstępne

Każde konto, które uzyskuje dostęp i używa klasyfikacji danych, musi mieć przypisaną do niego licencję z jednej z tych subskrypcji:

- Microsoft 365 (E5)
- Office 365 (E5)
- Dodatek Advanced Compliance (E5)
- Dodatek Zaawansowana inteligencja zagrożeń (E5)
- Ochrona Microsoft 365 E5/A5 na & informacji
- zgodność Microsoft 365 E5/A5

### <a name="permissions"></a>Uprawnienia

Konto musi mieć jawnie przypisane członkostwo w dowolnej z tych grup ról lub jawnie przyznać tę rolę.

### <a name="roles-and-role-groups-in-preview"></a>Role i grupy ról w wersji Preview

W wersji Preview są dostępne role i grupy ról, które można przetestować w celu precyzyjnego dostosowania kontroli dostępu.

Oto lista dostępnych w wersji Microsoft Information Protection (MIP), które są dostępne w wersji zapoznawczej. Aby dowiedzieć się więcej na ich temat, zobacz [Role w Centrum & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administrator ochrony informacji
- Analityk ochrony informacji
- Ochrona informacji
- Czytnik ochrony informacji

Poniżej znajdziesz listę grup ról miP, które są dostępne w wersji Preview. Aby dowiedzieć się więcej na ten temat, [zobacz Grupy ról w Centrum & zabezpieczeń.](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Ochrona informacji
- Administratorzy ochrony informacji
- Analitycy ochrony informacji
- Schoweki ochrony informacji
- Czytniki informacji

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Microsoft 365 grup ról**

- Administrator globalny
- Administrator zgodności
- Administrator zabezpieczeń
- Administrator danych zgodności

**Microsoft 365 ról**

- Administrator zgodności
- Administrator zabezpieczeń
- Czytnik zabezpieczeń

## <a name="activity-types"></a>Typy aktywności

Eksplorator aktywności zbiera informacje o aktywności z dzienników inspekcji w wielu źródłach działań. Aby uzyskać bardziej szczegółowe informacje na temat działania etykiet, które powoduje, że jest ono dostępne w Eksploratorze aktywności, zobacz Oznaczanie [zdarzeń dostępnych w Eksploratorze aktywności](data-classification-activity-explorer-available-events.md).

**Działania etykiet wrażliwości i** Działania związane z **etykietami** przechowywania z Office natywnych aplikacji, dodatku Azure Information Protection, usługi SharePoint Online, Exchange Online (tylko etykiety wrażliwości) i OneDrive. Oto kilka przykładów:

- Zastosowano etykietę
- Etykieta została zmieniona (uaktualniona, zmieniona lub usunięta)
- Symulacja autolabeli
- Odczyt pliku

**Skaner usługi Azure Information Protection (AIP) i klienci usługi AIP**

- Zastosowano ochronę
- Zmieniono ochronę
- Usunięto ochronę
- Odnaleziono pliki

Eksplorator aktywności gromadzi również zasady **DLP** dotyczące zdarzeń z usług Exchange Online, SharePoint Online, OneDrive, Teams Chat i Channel (wersja Preview), lokalnych folderów i bibliotek SharePoint oraz lokalnych udziałów plików i Windows 10 urządzeń **za pośrednictwem Zapobieganie utracie danych w punkcie końcowym (DLP**). Przykładowe zdarzenia z Windows 10 są plikowe:

- Usunięcia
- Dzieła
- Skopiowano do schowka
- Zmodyfikowano
- Czytanie
- Wydrukowano
- Zmieniono nazwę
- Skopiowano do udziału sieciowego
- Dostępne przez aplikację, do której dostęp został odblokowany 

Zrozumienie, jakie akcje są podejmowane z poufnej zawartości oznaczonej etykietą pomaga sprawdzić, czy dostępne kontrolki, takie jak zasady ochrony [](dlp-learn-about-dlp.md) przed utratą danych, są skuteczne, czy nie. Jeśli nie, lub jeśli znajdziesz coś nieoczekiwanego, `highly confidential` `general`na przykład dużą liczbę elementów oznaczonych na starszą wersję, możesz zarządzać różnymi zasadami i podjąć nowe działania, aby ograniczyć niepożądane zachowanie.

> [!NOTE]
> Eksplorator aktywności obecnie nie monitoruje działań przechowywania na Exchange Online.

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o etykietach poufności](sensitivity-labels.md)
- [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md)
- [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md)
- [Informacje o klasyfikacji danych](data-classification-overview.md)
