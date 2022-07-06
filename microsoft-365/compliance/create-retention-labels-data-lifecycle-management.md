---
title: Tworzenie etykiet przechowywania dla wyjątków
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
description: Instrukcje dotyczące tworzenia etykiet przechowywania dla wyjątków od zasad przechowywania na potrzeby zarządzania cyklem życia danych, dzięki czemu można zachować to, czego potrzebujesz, i usunąć to, czego nie potrzebujesz.
ms.openlocfilehash: 0951ce1fea2f9324c19ec0bf17451d458b4914d1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632580"
---
# <a name="create-retention-labels-for-exceptions-to-your-retention-policies"></a>Tworzenie etykiet przechowywania dla wyjątków od zasad przechowywania

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

W ramach strategii zapewniania ładu danych w celu zachowania potrzebnych elementów i usuwania tego, czego nie potrzebujesz, może być konieczne utworzenie kilku etykiet przechowywania dla elementów, które wymagają wyjątków od zasad przechowywania.

Zasady przechowywania są automatycznie stosowane do wszystkich elementów na poziomie kontenera (takich jak witryny programu SharePoint, skrzynki pocztowe użytkowników itd.), etykiety przechowywania mają zastosowanie do poszczególnych elementów, takich jak dokument programu SharePoint lub wiadomość e-mail.

Przed użyciem etykiet przechowywania upewnij się, że rozumiesz [zasady przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence) , aby uzupełnić zasady przechowywania dla określonych elementów programu SharePoint, OneDrive lub Exchange. Zazwyczaj etykiety przechowywania są używane do przechowywania określonych elementów dłużej niż zastosowane zasady przechowywania, ale można ich również użyć do zastąpienia automatycznego usuwania na końcu okresu przechowywania lub zastosowania innego okresu usuwania.

Typowy przykład: większość zawartości w witrynach programu SharePoint musi być przechowywana przez trzy lata, co jest objęte zasadami przechowywania. Ale masz kilka dokumentów kontraktowych, które muszą być przechowywane przez siedem lat. Te wyjątki można rozwiązać za pomocą etykiet przechowywania. Po przypisaniu zasad przechowywania do wszystkich witryn programu SharePoint należy zastosować etykiety przechowywania do dokumentów kontraktu. Wszystkie elementy programu SharePoint zostaną zachowane przez trzy lata, a tylko dokumenty umowy zostaną zachowane przez siedem lat.

Aby uzyskać więcej przykładów użycia etykiet przechowywania jako wyjątków od zasad przechowywania, zobacz [Łączenie zasad przechowywania i etykiet przechowywania](retention.md#combining-retention-policies-and-retention-labels).

Etykiety przechowywania obsługują również więcej możliwości niż zasady przechowywania. Aby uzyskać więcej informacji, zobacz [Porównanie możliwości zasad przechowywania i etykiet przechowywania](retention.md#compare-capabilities-for-retention-policies-and-retention-labels).

Poniższe informacje ułatwiają tworzenie etykiet przechowywania w celu uzupełnienia zasad przechowywania w ramach strategii zarządzania cyklem życia danych.

> [!NOTE]
> Utwórz etykiety przechowywania na podstawie rozwiązania **do zarządzania rekordami** , a nie **zarządzania cyklem życia danych** , jeśli musisz użyć etykiet przechowywania do zarządzania elementami o wysokiej wartości dla wymagań biznesowych, prawnych lub regulacyjnych. Na przykład chcesz użyć przeglądu przechowywania lub dyspozycji opartego na zdarzeniach. Aby uzyskać instrukcje, zobacz [Używanie planu plików do tworzenia etykiet przechowywania i zarządzania nimi](file-plan-manager.md).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny organizacji ma pełne uprawnienia do tworzenia i edytowania etykiet przechowywania oraz ich zasad. Jeśli nie logujesz się jako administrator globalny, zobacz [Uprawnienia dla zasad przechowywania i etykiet przechowywania](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels).

## <a name="how-to-create-retention-labels-for-data-lifecycle-management"></a>Jak utworzyć etykiety przechowywania na potrzeby zarządzania cyklem życia danych

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com/) przejdź do karty **Etykiety** >  **zarządzania cyklem** >  życia danych **rozwiązań**> + **Tworzenie etykiety**
    
    Nie widzisz od razu rozwiązania **do zarządzania cyklem życia danych** ? Najpierw wybierz pozycję **Pokaż wszystko**. 

2. Postępuj zgodnie z monitami, aby utworzyć etykietę przechowywania. Zachowaj ostrożność, jaką nazwę wybierzesz, ponieważ nie można jej zmienić po zapisaniu etykiety.
    
    Aby uzyskać więcej informacji na temat ustawień przechowywania, zobacz [Ustawienia przechowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content).

3. Po utworzeniu etykiety i wyświetleniu opcji publikowania etykiety zastosuj ją automatycznie lub po prostu zapisz etykietę: wybierz pozycję **Po prostu zapisz etykietę na razie**, a następnie wybierz pozycję **Gotowe**.

4. Powtórz te kroki, aby utworzyć więcej etykiet przechowywania potrzebnych do różnych ustawień przechowywania.

Aby edytować istniejącą etykietę, wybierz ją, a następnie wybierz opcję **Edytuj etykietę** , aby uruchomić konfigurację Edytuj etykietę przechowywania, która umożliwia zmianę opisów etykiet i wszystkich kwalifikujących się ustawień.

Większości ustawień nie można zmienić po utworzeniu i zapisaniu etykiety, które obejmują:
- Nazwa etykiety przechowywania i ustawienia przechowywania z wyjątkiem okresu przechowywania. Nie można jednak zmienić okresu przechowywania, gdy okres przechowywania zależy od tego, kiedy elementy zostały oznaczone etykietą.

## <a name="next-steps"></a>Następne kroki

Teraz, po utworzeniu etykiet przechowywania, można je dodać do elementów, publikując etykiety lub automatycznie stosując je:
- [Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
- [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)
