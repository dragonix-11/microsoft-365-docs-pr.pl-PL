---
title: Tworzenie etykiet przechowywania dla wyjątków od zasad przechowywania
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Instrukcje tworzenia etykiet przechowywania dla wyjątków od zasad przechowywania na potrzeby zarządzania informacjami w celu zachowania tego, czego potrzebujesz, i usunięcia tego, co nie jest potrzebne.
ms.openlocfilehash: 699df2a62204115c60271a5d5aa70613db48c7d5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327269"
---
# <a name="create-retention-labels-for-exceptions-to-your-retention-policies"></a>Tworzenie etykiet przechowywania dla wyjątków od zasad przechowywania

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

W ramach strategii zarządzania informacjami w celu zachowania tego, czego potrzebujesz i usunięcia tego, czego nie potrzebujesz, może być konieczne utworzenie kilku etykiet przechowywania dla elementów, które wymagają wyjątków od zasad przechowywania. 

Zasady przechowywania są automatycznie stosowane do wszystkich elementów na poziomie kontenera (takich jak witryny programu SharePoint, skrzynki pocztowe użytkowników itp.), natomiast etykiety przechowywania mają zastosowanie do poszczególnych elementów, takich jak dokument programu SharePoint lub wiadomość e-mail.

Przed użyciem etykiet przechowywania w [](retention.md#the-principles-of-retention-or-what-takes-precedence) celu uzupełnienia zasad przechowywania dla określonych elementów należy się upewnić, że zasady przechowywania SharePoint, OneDrive lub Exchange przechowywania. Zazwyczaj etykiety przechowywania zachowują określone elementy dłużej niż stosowane zasady przechowywania, ale za ich pomocą można także zastąpić automatyczne usuwanie na końcu okresu przechowywania lub zastosować inny okres usuwania.

Typowy przykład: Większość zawartości witryn sieci SharePoint musi być zachowana przez trzy lata, co obejmuje zasady przechowywania. Jednak niektóre dokumenty kontraktowe muszą być przechowywane przez siedem lat. Do tych wyjątków można dodać etykiety przechowywania. Po przypisaniu zasad przechowywania do wszystkich SharePoint przechowywania zastosuj etykiety przechowywania do dokumentów umowy. Wszystkie SharePoint będą przechowywane przez trzy lata i tylko dokumenty kontraktu będą przechowywane przez siedem lat.

Aby uzyskać więcej przykładów, w jaki sposób etykiet przechowywania można używać jako wyjątków od zasad przechowywania, zobacz Łączenie zasad przechowywania [i etykiet przechowywania](retention.md#combining-retention-policies-and-retention-labels).

Etykiety przechowywania obsługują także więcej funkcji niż zasady przechowywania. Aby uzyskać więcej informacji, zobacz [Porównanie funkcji dotyczących zasad przechowywania i etykiet przechowywania](retention.md#compare-capabilities-for-retention-policies-and-retention-labels).

Poniższe informacje ułatwiają tworzenie etykiet przechowywania w celu uzupełnienia zasad przechowywania w ramach strategii zarządzania informacjami.

> [!NOTE]
> Tworzenie etykiet przechowywania na podstawie  rozwiązania do zarządzania rekordami  zamiast zarządzania informacjami w przypadku używania etykiet przechowywania do zarządzania cyklem życia elementów o wysokiej wartości w przypadku wymogów przechowywania rekordów biznesowych, prawnych lub prawnych. Na przykład możesz skorzystać z przeglądu przechowywania lub rozsyłania opartych na zdarzeniach. Aby uzyskać instrukcje, [zobacz Tworzenie etykiet przechowywania i zarządzanie nimi za pomocą planu plików](file-plan-manager.md).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny w Twojej organizacji ma pełne uprawnienia do tworzenia i edytowania etykiet przechowywania oraz ich zasad. Jeśli nie logujesz się jako administrator globalny, zobacz Uprawnienia dotyczące zasad [przechowywania i etykiet przechowywania](get-started-with-information-governance.md#permissions-for-retention-policies-and-retention-labels).

## <a name="how-to-create-retention-labels-for-information-governance"></a>Jak tworzyć etykiety przechowywania na temat zarządzania informacjami

1. W [Centrum zgodności platformy Microsoft 365:](https://compliance.microsoft.com/) **Zarządzanie** >  >  rozwiązaniamiinformacjeNalepki etykiety > + **Tworzenie etykiety**
    
    Nie widzisz od razu rozwiązania **do zarządzania informacjami** ? Najpierw wybierz pozycję **Pokaż wszystko**. 

2. Postępuj zgodnie z monitami, aby utworzyć etykietę przechowywania. Należy zachować ostrożność przy wybieranej nazwie, ponieważ po zapisaniu etykiety nie można jej zmienić.
    
    Aby uzyskać więcej informacji o ustawieniach przechowywania, [zobacz Ustawienia zachowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content).

3. Po utworzeniu etykiety i wyświetleniu opcji publikowania etykiety, automatycznego zastosowania etykiety lub po prostu zapisania etykiety: Wybierz pozycję Po prostu zapisz na razie etykietę **, a** następnie wybierz pozycję **Gotowe**.

4. Powtórz te czynności, aby utworzyć jakiekolwiek inne etykiety przechowywania potrzebne dla różnych ustawień przechowywania.

Aby edytować istniejącą etykietę, zaznacz ją, a następnie wybierz  opcję Edytuj etykietę, aby uruchomić konfigurację Edytuj etykietę przechowywania, która umożliwia zmianę opisów etykiet i wszystkich uprawnionych ustawień.

Po utworzeniu i zapisaniu etykiety nie można zmienić większości ustawień, takich jak:
- Nazwa etykiety przechowywania i ustawienia przechowywania z wyjątkiem okresu przechowywania. Nie można jednak zmienić okresu przechowywania, gdy okres przechowywania jest oparty na oznaczaniu elementów etykietą.

## <a name="next-steps"></a>Następne kroki

Teraz, po utworzeniu etykiet przechowywania, można je dodawać do elementów przez opublikowanie etykiet lub automatyczne stosowanie:
- [Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
- [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)