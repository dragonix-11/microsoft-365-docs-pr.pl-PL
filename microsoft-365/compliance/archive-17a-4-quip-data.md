---
title: Konfigurowanie łącznika do archiwizowania danych quip w Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Dowiedz się, jak zaimportować i zarchiwizować dane quip w Microsoft 365 za pomocą łącznika 17a-4 Quip DataParser.
ms.openlocfilehash: 42ca24e72afbb6d588a08c07f7b0547692f1bdab
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091860"
---
# <a name="set-up-a-connector-to-archive-quip-data"></a>Konfigurowanie łącznika do archiwizowania danych quip

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj narzędzia [Quip DataParser](https://www.17a-4.com/quip-dataparser/) z 17a-4 LLC, aby zaimportować i zarchiwizować dane z quip do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Moduł DataParser zawiera łącznik Quip skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania tych elementów do Microsoft 365. Łącznik Quip DataParser konwertuje dane quip na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po zapisaniu danych quip w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Quip może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-quip-data"></a>Omówienie archiwizowania danych quip

W poniższym omówieniu wyjaśniono proces używania łącznika danych do archiwizowania danych quip w Microsoft 365.

![Przepływ pracy archiwizacji danych quip z zakresu 17a-4.](../media/QuipDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania narzędzia Quip DataParser.

2. Regularnie elementy Quip są zbierane przez program DataParser. Usługa DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik Quip DataParser utworzony w portalu zgodności usługi Microsoft Purview łączy się z usługą DataParser i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Podfolder w folderze Skrzynka odbiorcza o nazwie **Quip DataParser** jest tworzony w skrzynkach pocztowych użytkownika, a elementy Quip są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element quip zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto DataParser dla łączników firmy Microsoft. W tym celu skontaktuj się z [17a-4 LLC](https://www.17a-4.com/contact/). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik Quip DataParser w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-a-quip-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika Quip DataParser

Pierwszym krokiem jest dostęp do strony Łączniki danych w portalu zgodności i utworzenie łącznika 17a-4 dla danych quip.

1. Przejdź do obszaru<https://compliance.microsoft.com>, a następnie kliknij pozycję **Łączniki** >  **danychQuip DataParser**.

2. Na stronie Opis produktu **Quip DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki opisane w kreatorze połączenia Quip DataParser.

## <a name="step-2-configure-the-quip-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika Quip DataParser

Skontaktuj się z pomocą techniczną 17a-4, aby skonfigurować łącznik Quip DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik Quip DataParser automatycznie mapuje użytkowników na ich Microsoft 365 adresy e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-quip-dataparser-connector"></a>Krok 4. Monitorowanie łącznika Quip DataParser

Po utworzeniu łącznika Quip DataParser możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz utworzony łącznik Quip DataParser, aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
