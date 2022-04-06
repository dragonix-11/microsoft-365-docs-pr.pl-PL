---
title: Wprowadzenie z użyciem szkolenia symulacyjnego w zakresie ataków
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
description: Administratorzy mogą dowiedzieć się, jak używać szkolenia symulacyjnego z użyciem symezyjnych prób wyłudzania informacji i haseł w swoich organizacjach w Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 244d0ae912a5cc2dc163b62f44b44877c0318b88
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507416"
---
# <a name="get-started-using-attack-simulation-training-in-defender-for-office-365"></a>Wprowadzenie z użyciem szkolenia symezyjną ataków w programie Ochrona usługi Office 365 w usłudze Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy planu** [Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

Jeśli w organizacji Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2, który obejmuje funkcje analizy zagrożeń i [reakcji, możesz](office-365-ti.md) skorzystać ze szkolenia symulacyjnego z użyciem funkcji ataków w Microsoft 365 Defender  w portalu, aby uruchamiać realistycznych scenariuszy ataków w twojej organizacji. Te symulowane ataki mogą ułatwić zidentyfikowanie i znalezienie narażonych użytkowników, zanim rzeczywisty atak będzie wpływał na dolną linię. Aby dowiedzieć się więcej, przeczytaj ten artykuł.

> [!NOTE]
> Szkolenie symulacyjne dotyczące ataków zastępuje stare środowisko podczas ataków w wersji 1  \>, które było dostępne w Centrum & zabezpieczeń w miejscu ataków na zarządzanie zagrożeniami **lub .** <https://protection.office.com/attacksimulator>

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby otworzyć Microsoft 365 Defender, przejdź do .<https://security.microsoft.com> Szkolenie dotyczące symeny ataków jest dostępne na stronie **Szkolenie dotyczące symezyjki ataków za pomocą poczty e-mail** \> **i współpracy**. Aby przejść bezpośrednio do szkolenia z symezyjną ataków, użyj narzędzia <https://security.microsoft.com/attacksimulator>.

- Aby uzyskać więcej informacji na temat dostępności szkolenia symydacyjnego z tematem ataków dla różnych Microsoft 365 subskrypcji, zobacz Ochrona usługi Office 365 w usłudze Microsoft Defender [opisu usługi](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

- Aby można było wykonać procedury z tego artykułu  Azure Active Directory w programie Azure Active Directory mieć przypisane uprawnienia. W szczególności musisz być członkiem jednej z następujących ról:
  - **Administrator globalny**
  - **Administrator zabezpieczeń**
  - **Administratorzy symulacjy ataków**<sup>\*</sup>: twórz wszystkie aspekty kampanii symulacyjnych ataków i zarządzaj nimi.
  - **Autor ładowania ataków**<sup>\*</sup>: Utwórz łady ataków, które administrator może zainicjować później.

  <sup>\*</sup>Dodawanie użytkowników do tej roli w portalu Microsoft 365 Defender jest obecnie nieobsługiwane.

  Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender portalu lub](permissions-microsoft-365-security-center.md) [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).

- Nie ma odpowiadających im poleceń cmdlet programu PowerShell na potrzeby szkolenia z symeletami ataków.

- Dane związane z atakami i związane z nimi szkolenia są przechowywane razem z innymi danymi Microsoft 365 klienta. Aby uzyskać więcej informacji[, Microsoft 365 lokalizacje danych](../../enterprise/o365-data-locations.md). Symulowanie ataków jest dostępne w następujących regionach: NAM, APC, EUR, IND, CAN, AUS, FRA, GBR, JPN, KOR, BRA, LAM, CHE, NOR, ZAF, ARE i DEU.

  > [!NOTE]
  > Najnowsze dodatki to NOR, ZAF, ARE i DEU. Wszystkie funkcje z wyjątkiem zgłoszonych telemetrii poczty e-mail będą dostępne w tych regionach. Pracujemy nad włączeniem tej funkcji i powiadomimy naszych klientów, gdy tylko zostanie udostępnione telemetria zgłoszonych wiadomości e-mail.

- Od 15 czerwca 2021 r. w programie GCC. Jeśli Twoja organizacja ma Office 365 G5 GCC lub Ochrona usługi Office 365 w usłudze Microsoft Defender (plan 2) dla instytucji rządowych, możesz użyć szkolenia symulacyjnego z użyciem funkcji ataków w aplikacji Microsoft 365 Defender  w portalu można uruchamiać realistycznych scenariuszy ataków w organizacji zgodnie z opisem w tym artykule. Szkolenie z symeny ataków nie jest jeszcze dostępne w GCC high-in lub dod.

> [!NOTE]
> Szkolenie symulacyjne z atakami udostępnia podzbiór możliwości klientom usługi E3 w wersji próbnej. Oferta wersji próbnej umożliwia korzystanie z ładowania poświadczeń zbierania danych dziewiętnych oraz wybieranie środowisko szkoleń "ISA Phishing" lub "Mass Market Phishing". W ramach oferty wersji próbnej E3 nie są dostępne żadne inne funkcje.

## <a name="simulations"></a>Symulacje

*Wyłudzanie* informacji to ogólny termin w przypadku ataków na pocztę e-mail, w których próbie ukraść informacje poufne w wiadomościach, które wydają się pochodzić od wiarygodnych lub zaufanych nadawców. *Wyłudzanie* informacji jest częścią podzbioru technik klasyfikowanych jako _inżynieria społecznościowa_.

W szkoleniu symulacyjnych ataków dostępnych jest wiele typów technik społecznościowych:

- **Zbieranie poświadczeń**: atakujący wysyła do odbiorcy wiadomość zawierającą adres URL. Gdy adresat kliknie adres URL, jest przekierowywany do witryny internetowej, w którym zwykle jest wyświetlane okno dialogowe z prośbą o nazwę użytkownika i hasło. Zazwyczaj strona docelowa ma tytuł reprezentujący dobrze znaną witrynę sieci Web w celu budowania zaufania do użytkownika.

- **Załącznik z złośliwym** oprogramowaniem: atakujący wysyła do odbiorcy wiadomość zawierającą załącznik. Gdy adresat otwiera załącznik, na urządzeniu użytkownika jest uruchamiany dowolny kod (na przykład makro), aby pomóc osobie atakującej zainstalować dodatkowy kod lub dodatkowo z nich korzystać.

- **Link w załączniku**: jest to tryb hybrydowy zbioru poświadczeń. Atakujący wysyła do odbiorcy wiadomość zawierającą adres URL w załączniku. Gdy adresat otworzy załącznik i kliknie adres URL, jest przekierowywany do witryny internetowej, w którym zazwyczaj jest wyświetlane okno dialogowe z prośbą o nazwę użytkownika i hasło. Zazwyczaj strona docelowa ma tytuł reprezentujący dobrze znaną witrynę sieci Web w celu budowania zaufania do użytkownika.

- **Link do złośliwego** oprogramowania: atakujący wysyła do odbiorcy wiadomość zawierającą link do załącznika w znanej witrynie do udostępniania plików SharePoint (na przykład w trybie online lub Dropbox). Gdy adresat kliknie adres URL, zostanie otwarty załącznik i na jego urządzeniu zostanie uruchomiony dowolny kod (na przykład makro), aby ułatwić atakującemu zainstalowanie dodatkowego kodu lub dodatkową instalację.

- **Drive-by-url**: atakujący wysyła do odbiorcy wiadomości zawierające adres URL. Gdy adresat kliknie adres URL, jest przekierowywany do witryny internetowej, która próbuje uruchomić kod tła. Ten kod tła próbuje zebrać informacje o adresatze lub wdrożyć dowolny kod na jego urządzeniu. Zazwyczaj docelowa witryna sieci Web jest dobrze znana witryną sieci Web, która została naruszona lub jest sklonowana dobrze znanej witryny sieci Web. Znajomość tej witryny pomaga przekonać użytkownika, że można kliknąć link. Ta technika jest również znana jako atak _z wodociągami_.

> [!NOTE]
> Zanim użyjemy adresu URL w kampanii służącej do wyłudzania informacji, sprawdź dostępność adresu URL symulowanego wyłudzania informacji w obsługiwanych przeglądarkach sieci Web. Mimo że pracujemy z wieloma dostawcami reputacji adresów URL, aby zawsze zezwalać na te adresy URL symulowania, nie zawsze mamy pełny zasięg (na przykład Google Sejf Przeglądanie). Większość dostawców zapewnia wskazówki, które pozwalają zawsze zezwalać na określone adresy URL (na przykład <https://support.google.com/chrome/a/answer/7532419>).

Adresy URL używane podczas szkolenia symulacyjnego w zakresie ataków są opisane na poniższej liście:

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

### <a name="create-a-simulation"></a>Tworzenie symulacyjnej

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia i wysyłania nowej symulacyjnej, zobacz [Symulowanie ataku służącego do wyłudzania informacji](attack-simulation-training.md).

### <a name="create-a-payload"></a>Tworzenie ładu

Aby uzyskać instrukcje krok po kroku dotyczące tworzenia ładu do użytku w ramach symulacyjnej, zobacz Tworzenie niestandardowego obciążenia dla szkolenia [symulacyjnego z](attack-simulation-training-payloads.md) użyciem ataków.

### <a name="gaining-insights"></a>Uzyskiwanie szczegółowych informacji

Aby uzyskać szczegółowe instrukcje dotyczące sposobu uzyskania szczegółowych informacji na temat raportowania, zobacz Zdobywanie szczegółowych informacji dzięki szkoleniom [symulacyjnych ataków](attack-simulation-training-insights.md).

> [!NOTE]
> Podczas ataków Do najbezpieczniej jest używany link Sejf w programie Ochrona usługi Office 365 w usłudze Defender w celu bezpiecznego śledzenia danych kliknięcia adresu URL w wiadomości ładowania wysyłanej do docelowych adresatów kampanii wyłudzającej informacje, nawet jeśli ustawienie Śledź użytkowników klikających w zasadach usługi Sejf Links jest wyłączone.
