---
title: Planowanie zakończenia obsługi oprogramowania i wersji oprogramowania
description: Odnajdowanie i planowanie wersji oprogramowania i oprogramowania, które nie są już obsługiwane i nie będą otrzymywać aktualizacji zabezpieczeń.
keywords: Zarządzanie zagrożeniami i lukami, Ochrona punktu końcowego w usłudze Microsoft Defender, zalecenie dotyczące bezpieczeństwa tvm, zalecenie dotyczące bezpieczeństwa, zalecenie dotyczące akcji
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3997e2cb372a2cbbbdb0d8e9b51c5b57bd38c7aa
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476692"
---
# <a name="plan-for-end-of-support-software-and-software-versions-with-threat-and-vulnerability-management"></a>Planowanie zakończenia obsługi wersji oprogramowania i oprogramowania z Zarządzanie zagrożeniami i lukami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Zakończenie świadczenia pomocy technicznej (EOS), znanej w inny sposób jako zakończenie użytkowania (EOL), dla oprogramowania lub wersji oprogramowania oznacza, że nie będą one już obsługiwane ani obsługiwane oraz nie będą otrzymywać aktualizacji zabezpieczeń. Gdy korzystasz z oprogramowania lub wersji oprogramowania z zakończoną pomocą techniczną, ujawniasz organizacji luki w zabezpieczeniach, zagrożenia prawne i finansowe.

Ze względu na bezpieczeństwo i administratorzy IT niezwykle ważne jest współpracowanie i zapewnianie, że spis oprogramowania organizacji jest skonfigurowany pod celu zapewnienia optymalnych wyników, zgodności i zdrowego ekosystemu sieci. Należy sprawdzić opcje usuwania lub zamieniania aplikacji, które zakończyły wsparcie techniczne, i aktualizować wersje, które nie są już obsługiwane. Najlepszym rozwiązaniem jest utworzenie i zaimplementowanie planu **przed** końcem dat zakończenia pomocy technicznej.

> [!NOTE]
> Funkcja zakończenia obsługi jest obecnie dostępna tylko dla Windows produktów.

## <a name="find-software-or-software-versions-that-are-no-longer-supported"></a>Znajdowanie programów lub wersji oprogramowania, które nie są już obsługiwane

1. Z menu Zarządzanie zagrożeniami i lukami przejdź do pozycji [**Zalecenia dotyczące zabezpieczeń**](tvm-security-recommendation.md).
2. Przejdź do **panelu** Filtry i poszukaj sekcji tagów. Wybierz co najmniej jedną z opcji tagów EOS. Następnie **wybierz pozycję Zastosuj**.

   :::image type="content" source="images/tvm-eos-tag.png" alt-text="Oprogramowanie EOS, wersje EOS i nadchodzące wersje systemu EOS" lightbox="images/tvm-eos-tag.png":::

3. Zostanie wyświetlona lista zaleceń dotyczących oprogramowania z zakończoną pomocą techniczną, wersjami oprogramowania, których wsparcie zakończono, lub wersjami z zbliżającym się zakończeniem pomocy technicznej. Te tagi są również widoczne na [stronie spisu](tvm-software-inventory.md) oprogramowania.

   :::image type="content" source="images/tvm-eos-tags-column.png" alt-text="The Rekomendacje with EOS tag" lightbox="images/tvm-eos-tags-column.png":::

## <a name="list-of-versions-and-dates"></a>Lista wersji i dat

Aby wyświetlić listę wersji, dla których niebawem zakończyło się wsparcie lub wsparcie techniczne, i te daty, wykonaj następujące czynności:

1. W wysuwanych informacjach o zaleceniach zabezpieczeń dla oprogramowania z wersjami, dla których wsparcie zakończyło się lub wkrótce zakończy się wsparcie.

   :::image type="content" source="images/eos-upcoming-eos.png" alt-text="Link do dystrybucji wersji" lightbox="images/eos-upcoming-eos.png":::

2. Wybierz link **do rozpowszechniania wersji** , aby przejść do strony przechodzenia do szczegółów oprogramowania. Możesz tam zobaczyć filtrowaną listę wersji z tagami identyfikującymi je jako koniec pomocy technicznej lub zbliżającym się zakończeniem pomocy technicznej.

   :::image type="content" source="images/software-drilldown-eos.png" alt-text="Strona rozwijanego oprogramowania ze szczegółami na końcu oprogramowania pomocy technicznej" lightbox="images/software-drilldown-eos.png":::

3. Wybierz jedną z wersji w tabeli, która ma być otwarta. Na przykład wersja 10.0.18362.1. Zostanie wyświetlone wysuwne z datą zakończenia pomocy technicznej.

   :::image type="content" source="images/version-eos-date.png" alt-text="Wyświetlanie daty zakończenia pomocy technicznej" lightbox="images/version-eos-date.png":::

Po zidentyfikowaniu, które wersje oprogramowania i oprogramowania są narażone ze względu na stan zakończenia pomocy technicznej, musisz zdecydować, czy chcesz je zaktualizować, czy usunąć ze swojej organizacji. Pozwoli to obniżyć poziom narażenia organizacji na luki w zabezpieczeniach i zaawansowane trwałe zagrożenia.

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zagrożeń i zarządzanie lukami w zabezpieczeniach wiadomości](next-gen-threat-and-vuln-mgt.md)
- [Zalecenia dotyczące zabezpieczeń](tvm-security-recommendation.md)
- [Spis oprogramowania](tvm-software-inventory.md)
