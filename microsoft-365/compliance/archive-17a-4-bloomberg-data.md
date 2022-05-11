---
title: Konfigurowanie łącznika do archiwizowania danych bloomberga w Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik Bloomberg DataParser 17a-4 i użyć go do importowania i archiwizowania danych bloomberga w Microsoft 365.
ms.openlocfilehash: 2049cf1c0543d3bdf9aa9d0d5bd876837853d1d3
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317145"
---
# <a name="set-up-a-connector-to-archive-bloomberg-data"></a>Konfigurowanie łącznika do archiwizowania danych bloomberga

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj narzędzia [Bloomberg DataParser](https://www.17a-4.com/Bloomberg-dataparser/) z firmy 17a-4 LLC, aby zaimportować i zarchiwizować dane z firmy Bloomberg do skrzynek pocztowych użytkowników w organizacji Microsoft 365. DataParser zawiera łącznik Bloomberga, który jest skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania tych elementów do Microsoft 365. Łącznik Bloomberg DataParser konwertuje dane bloomberga na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po zapisaniu danych bloomberga w skrzynkach pocztowych użytkowników można zastosować funkcje Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Bloomberg może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-bloomberg-data"></a>Omówienie archiwizacji danych bloomberga

W poniższym omówieniu wyjaśniono proces używania łącznika danych do archiwizowania danych bloomberga w Microsoft 365.

![Przepływ pracy archiwizacji danych bloomberga z zakresu 17a-4.](../media/BloombergDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania narzędzia Bloomberg DataParser.

2. Regularnie elementy bloomberga są zbierane przez użytkownika DataParser. Usługa DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik Bloomberg DataParser utworzony w portal zgodności Microsoft Purview łączy się z aplikacją DataParser i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Podfolder w folderze Skrzynka odbiorcza o nazwie **Bloomberg DataParser** jest tworzony w skrzynkach pocztowych użytkownika, a elementy bloomberga są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element bloomberga zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto DataParser dla łączników firmy Microsoft. W tym celu skontaktuj się z [17a-4 LLC](https://www.17a-4.com/contact/). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik Bloomberg DataParser w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-a-bloomberg-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika Bloomberg DataParser

Pierwszym krokiem jest dostęp do strony Łączniki danych w portalu zgodności i utworzenie łącznika 17a-4 dla danych bloomberga.

1. Przejdź do pozycji <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  **danychBloomberg DataParser**.

2. Na stronie Opis produktu **Bloomberg DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki opisane w kreatorze połączeń Bloomberg DataParser.

## <a name="step-2-configure-the-bloomberg-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika Bloomberg DataParser

Współpracuj z pomocą techniczną 17a-4, aby skonfigurować łącznik Bloomberg DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik Bloomberg DataParser automatycznie mapuje użytkowników na ich Microsoft 365 adresy e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-bloomberg-dataparser-connector"></a>Krok 4. Monitorowanie łącznika Bloomberg DataParser

Po utworzeniu łącznika Bloomberg DataParser możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz utworzony łącznik Bloomberg DataParser, aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
