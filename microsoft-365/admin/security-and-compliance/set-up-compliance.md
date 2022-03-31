---
title: Zwiększanie ochrony przed zagrożeniami dla Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Skonfiguruj funkcje zgodności, aby zapobiec utracie danych i zapewnić bezpieczeństwo poufnych informacji Twoich i Twoich klientów.
ms.openlocfilehash: baac8bc1ad9a425ad7219a1e76949286858f60e0
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403737"
---
# <a name="set-up-compliance-features"></a>Konfigurowanie funkcji zgodności

Subskrypcja Microsoft 365 Business Premium obejmuje funkcje zgodności i prywatności. Te funkcje pomagają chronić dane firmy oraz chronić poufne informacje twoich i klientów. Ten artykuł ma na celu pomoc w rozpoczynaniu pracy z funkcjami zgodności.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Upewnij się, że masz przypisaną jedną z następujących ról w programie Azure Active Directory:

- Administrator globalny
- Administrator zgodności

Aby dowiedzieć się więcej, [zobacz Wprowadzenie o tej stronie ról](../add-users/admin-roles-page.md).

## <a name="use-compliance-manager-to-get-started"></a>Rozpoczynanie pracy za pomocą Menedżera zgodności

:::image type="content" source="../../business-premium/media/m365bp-compliancemanager.png" alt-text="Zrzut ekranu przedstawiający Menedżera zgodności w Microsoft 365 Business Premium.":::

Microsoft 365 Business Premium menedżera zgodności, który może ułatwić konfigurowanie funkcji zgodności. Te funkcje obejmują między innymi zapobieganie utracie danych, zarządzanie informacjami i zarządzanie ryzykiem w niejawnym programie testów. Menedżer zgodności pozwala zaoszczędzić czas, wyróżniając zalecenia, wynik zgodności i sposoby ulepszania wyników.

Oto jak rozpocząć pracę:

1. Przejdź do i [https://compliance.microsoft.com](https://compliance.microsoft.com) zaloguj się.

2. W okienku nawigacji wybierz pozycję **Menedżer zgodności**.

3. Przejrzyj **informacje na karcie** Omówienie. Wybierz element lub link, aby wyświetlić więcej informacji lub aby podjąć działania, takie jak skonfigurowanie zasad ochrony przed utratą danych (DLP, data loss prevention). Na przykład w sekcji **Rozwiązania wpływające na** wynik możesz wybrać link w kolumnie **Pozostałe** akcje.

   :::image type="content" source="../../business-premium/media/m365bp-compliancesolutions.png" alt-text="Zrzut ekranu przedstawiający rozwiązania wpływające na okienko Wynik.":::

   Ta akcja przenosi Cię na **kartę Akcje** udoskonalania, która jest filtrowana według wybranego elementu. W tym przykładzie omymy zasady DLP do skonfigurowania.

   :::image type="content" source="../../business-premium/media/m365bp-dlppoliciestoconfigure.png" alt-text="Zrzut ekranu przedstawiający zasady DLP do skonfigurowania.":::

4. Na **karcie Akcje udoskonalania** wybierz element. W naszym przykładzie wybrano opcję Utwórz dostosowane zasady **DLP lub identyfikowalne dane osobowe**. Zostanie ładowana strona, która zawiera więcej informacji na temat zasad konfigurowania.

   :::image type="content" source="../../business-premium/media/m365bp-dlppolicyinfo.png" alt-text="Zrzut ekranu przedstawiający informacje dotyczące zasad DLP dotyczących zawartości klientów.":::

   Postępuj zgodnie z informacjami na ekranie, aby skonfigurować zasady DLP.

Aby uzyskać więcej informacji na temat funkcji zgodności w Microsoft 365 dla firm, zobacz Microsoft 365 [dotyczącej zgodności](../../compliance/index.yml).

## <a name="use-sensitivity-labels"></a>Używanie etykiet wrażliwości

Etykiety wrażliwości są dostępne w Office (takich jak programy Outlook, Word, Excel i PowerPoint). Oto przykładowe etykiety:

- Normalny
- Personal
- Prywatna
- Poufne

Można jednak również zdefiniować inne etykiety dla firmy.

Aby rozpocząć pracę z etykietami wrażliwości, skorzystaj z następujących artykułów:

1. [Co to są etykiety wrażliwości?](../../compliance/sensitivity-labels.md)

2. [Wprowadzenie tworzenia etykiet wrażliwości](../../compliance/get-started-with-sensitivity-labels.md)

3. [Publikowanie etykiet wrażliwości i ich zasad](../../compliance/create-sensitivity-labels.md)

4. [Pokazywanie osobom w firmie, jak używać etykiet wrażliwości](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)