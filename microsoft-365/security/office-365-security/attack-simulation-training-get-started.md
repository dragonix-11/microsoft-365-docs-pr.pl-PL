---
title: Wprowadzenie do szkolenia z symulacji ataku
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak używać trenowania symulacji ataków do przeprowadzania symulowanych ataków wyłudzania informacji i haseł w organizacjach Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 79c8db9a088484a56e559ab4c3e33d68ebf33380
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840150"
---
# <a name="get-started-using-attack-simulation-training-in-defender-for-office-365"></a>Wprowadzenie przy użyciu trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy** [planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

Jeśli Twoja organizacja ma Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2, który obejmuje [możliwości badania zagrożeń i reagowania,](office-365-ti.md) możesz użyć szkolenia symulacji ataków w Microsoft 365 Defender  portal do uruchamiania realistycznych scenariuszy ataków w organizacji. Te symulowane ataki mogą pomóc w zidentyfikowaniu i znalezieniu narażonych użytkowników, zanim rzeczywisty atak wpłynie na wyniki finansowe. Przeczytaj ten artykuł, aby dowiedzieć się więcej.

Obejrzyj ten krótki film wideo, aby dowiedzieć się więcej na temat trenowania symulacji ataków.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWMhvB]

> [!NOTE]
> Trenowanie symulacji ataków zastępuje stare środowisko symulatora ataków w wersji 1, które było dostępne w Centrum zgodności & zabezpieczeń w **symulatorze ataków** **zarządzania zagrożeniami** \> lub <https://protection.office.com/attacksimulator>.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby otworzyć portal Microsoft 365 Defender, przejdź do strony <https://security.microsoft.com>. Szkolenie z symulacji ataków jest dostępne na **stronie Szkolenia dotyczące symulacji ataków** **i współpracy w zakresie poczty** \> e-mail. Aby przejść bezpośrednio do trenowania symulacji ataków, użyj polecenia <https://security.microsoft.com/attacksimulator>.

- Aby uzyskać więcej informacji na temat dostępności trenowania symulacji ataków w różnych subskrypcjach Microsoft 365, zobacz [opis usługi Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Azure Active Directory**. W szczególności musisz być członkiem jednej z następujących ról:
  - **Administrator globalny**
  - **Administrator zabezpieczeń**
  - **Administratorzy symulacji ataków**<sup>\*</sup>: tworzenie wszystkich aspektów kampanii symulacji ataków i zarządzanie nimi.
  - Autor <sup>\*</sup>**ładunku ataku**: utwórz ładunki ataku, które administrator może zainicjować później.

  <sup>\*</sup>Dodawanie użytkowników do tej roli w portalu Microsoft 365 Defender nie jest obecnie obsługiwane.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md) lub [Informacje o rolach administratora](../../admin/add-users/about-admin-roles.md).

- Nie ma odpowiednich poleceń cmdlet programu PowerShell do trenowania symulacji ataku.

- Symulacja ataków i dane związane z trenowaniem są przechowywane z innymi danymi klientów dla usług Microsoft 365. Aby uzyskać więcej informacji[, zobacz Microsoft 365 lokalizacje danych](../../enterprise/o365-data-locations.md). Symulacja ataku jest dostępna w następujących regionach: NAM, APC, EUR, IND, CAN, AUS, FRA, GBR, JPN, KOR, BRA, LAM, CHE, NOR, ZAF, ARE i DEU.

  > [!NOTE]
  > NOR, ZAF, ARE i DEU są najnowszymi dodatkami. Wszystkie funkcje z wyjątkiem zgłoszonych danych telemetrycznych poczty e-mail będą dostępne w tych regionach. Pracujemy nad włączeniem tej funkcji i powiadomimy naszych klientów, gdy tylko będzie dostępna zgłoszona telemetria wiadomości e-mail.

- Od 15 czerwca 2021 r. szkolenie z symulacji ataków jest dostępne w GCC. Jeśli Twoja organizacja ma Office 365 G5 GCC lub Ochrona usługi Office 365 w usłudze Microsoft Defender (plan 2) dla instytucji rządowych, możesz użyć szkolenia symulacji ataków w Microsoft 365 Defender  portal do uruchamiania realistycznych scenariuszy ataków w organizacji zgodnie z opisem w tym artykule. Trenowanie symulacji ataków nie jest jeszcze dostępne w środowiskach GCC High lub DoD.

> [!NOTE]
> Szkolenie z symulacji ataków oferuje klientom E3 podzestaw możliwości w ramach wersji próbnej. Oferta wersji próbnej zawiera możliwość korzystania z ładunku Credential Harvest oraz możliwość wybierania środowisk szkoleniowych "ISA Phishing" lub "Mass Market Phishing". Żadne inne możliwości nie są częścią oferty wersji próbnej E3.

## <a name="simulations"></a>Symulacje

*Wyłudzanie informacji* to ogólny termin dotyczący ataków e-mail, które próbują wykraść poufne informacje w wiadomościach, które wydają się pochodzić od legalnych lub zaufanych nadawców. *Wyłudzanie informacji* jest częścią podzestawu technik, które klasyfikujemy jako _inżynierię społeczną_.

W szkoleniu symulacji ataków dostępnych jest wiele typów technik inżynierii społecznej:

- **Zbieranie poświadczeń**: osoba atakująca wysyła adresatowi wiadomość zawierającą adres URL. Gdy adresat kliknie adres URL, zostanie przekierowany do witryny internetowej, w której zwykle jest wyświetlane okno dialogowe z monitem o podanie nazwy użytkownika i hasła. Zazwyczaj strona docelowa ma tematykę reprezentującą dobrze znaną witrynę internetową w celu budowania zaufania do użytkownika.

- **Załącznik złośliwego oprogramowania**: osoba atakująca wysyła adresatowi wiadomość zawierającą załącznik. Gdy odbiorca otworzy załącznik, dowolny kod (na przykład makro) jest uruchamiany na urządzeniu użytkownika, aby ułatwić atakującemu zainstalowanie dodatkowego kodu lub dalsze umocnienie się.

- **Link w załączniku**: jest to hybryda zbioru poświadczeń. Osoba atakująca wysyła adresatowi wiadomość zawierającą adres URL wewnątrz załącznika. Gdy adresat otworzy załącznik i kliknie adres URL, zostanie on przekierowany do witryny internetowej, w której zwykle jest wyświetlane okno dialogowe z monitem o podanie nazwy użytkownika i hasła. Zazwyczaj strona docelowa ma tematykę reprezentującą dobrze znaną witrynę internetową w celu budowania zaufania do użytkownika.

- **Link do złośliwego oprogramowania**: osoba atakująca wysyła adresatowi wiadomość zawierającą link do załącznika w dobrze znanej witrynie do udostępniania plików (na przykład SharePoint Online lub Dropbox). Gdy adresat kliknie adres URL, zostanie otwarty załącznik i dowolny kod (na przykład makro) zostanie uruchomiony na urządzeniu użytkownika, aby ułatwić atakującemu zainstalowanie dodatkowego kodu lub dalsze umocnienie się.

- **Drive-by-url**: osoba atakująca wysyła adresatowi komunikaty zawierające adres URL. Gdy adresat kliknie adres URL, zostanie przekierowany do witryny internetowej, która próbuje uruchomić kod w tle. Ten kod w tle próbuje zebrać informacje o adresacie lub wdrożyć dowolny kod na urządzeniu. Zazwyczaj docelowa witryna internetowa jest dobrze znaną witryną internetową, która została naruszona lub klonem dobrze znanej witryny internetowej. Znajomość witryny internetowej pomaga przekonać użytkownika, że kliknięcie linku jest bezpieczne. Ta technika jest również znana jako _atak podlewania dziury_.

> [!NOTE]
> Przed użyciem adresu URL w kampanii wyłudzania informacji sprawdź dostępność symulowanego adresu URL wyłudzania informacji w obsługiwanych przeglądarkach internetowych. Chociaż współpracujemy z wieloma dostawcami reputacji adresów URL, aby zawsze zezwalać na te adresy URL symulacji, nie zawsze mamy pełne pokrycie (na przykład Google Sejf Browsing). Większość dostawców zapewnia wskazówki, które umożliwiają zawsze zezwalanie na określone adresy URL (na przykład <https://support.google.com/chrome/a/answer/7532419>).

Adresy URL używane przez trenowanie symulacji ataków są opisane na następującej liście:

- <https://www.mcsharepoint.com>
- <https://www.attemplate.com>
- <https://www.doctricant.com>
- <https://www.mesharepoint.com>
- <https://www.officence.com>
- <https://www.officenced.com>
- <https://www.officences.com>
- <https://www.officentry.com>
- <https://www.officested.com>
- <https://www.prizegives.com>
- <https://www.prizemons.com>
- <https://www.prizewel.com>
- <https://www.prizewings.com>
- <https://www.shareholds.com>
- <https://www.sharepointen.com>
- <https://www.sharepointin.com>
- <https://www.sharepointle.com>
- <https://www.sharesbyte.com>
- <https://www.sharession.com>
- <https://www.sharestion.com>
- <https://www.templateau.com>
- <https://www.templatent.com>
- <https://www.templatern.com>
- <https://www.windocyte.com>

### <a name="create-a-simulation"></a>Tworzenie symulacji

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia i wysyłania nowej symulacji, zobacz [Symulowanie ataku wyłudzania informacji](attack-simulation-training.md).

### <a name="create-a-payload"></a>Tworzenie ładunku

Aby uzyskać instrukcje krok po kroku dotyczące sposobu tworzenia ładunku do użycia w symulacji, zobacz [Tworzenie niestandardowego ładunku na potrzeby trenowania symulacji ataków](attack-simulation-training-payloads.md#create-payloads).

### <a name="gaining-insights"></a>Uzyskiwanie szczegółowych informacji

Aby uzyskać instrukcje krok po kroku dotyczące sposobu uzyskiwania szczegółowych informacji za pomocą raportowania, zobacz [Uzyskiwanie szczegółowych informacji dzięki trenowaniu symulacji ataków](attack-simulation-training-insights.md).

> [!NOTE]
> Symulator ataków używa linków Sejf w Ochrona usługi Office 365 w usłudze Defender, aby bezpiecznie śledzić dane kliknięć adresu URL w komunikacie ładunku wysyłanym do docelowych adresatów kampanii wyłudzania informacji, nawet jeśli ustawienie **Śledzenie kliknięć użytkownika w zasadach linków** Sejf jest wyłączone.
