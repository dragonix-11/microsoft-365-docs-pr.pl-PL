---
title: Konfigurowanie łącznika do archiwizacji danych XSLT/XML na platformie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych XSLT/XML z usługi Veritas na platformie Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w usłudze Microsoft 365, dzięki czemu można używać funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania w celu zarządzania danymi innych firm w organizacji.
ms.openlocfilehash: fa4901098dcd0104406107c4fc98aa9c04006c1d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637732"
---
# <a name="set-up-a-connector-to-archive-xsltxml-data"></a>Konfigurowanie łącznika do archiwizacji danych XSLT/XML

Użyj łącznika Veritas w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane ze źródła strony sieci Web do skrzynek pocztowych użytkowników w organizacji platformy Microsoft 365. Usługa Veritas udostępnia [łącznik XSLT/XML](https://globanet.com/xslt-xml) , który umożliwia szybkie opracowywanie plików utworzonych przy użyciu funkcji XSLT (przekształcenia języka arkusza stylów rozszerzalnych) w celu przekształcenia plików XML w inne formaty plików (takie jak HTML lub tekst), które można zaimportować do platformy Microsoft 365. Łącznik konwertuje zawartość elementu ze źródła XSLT/XML na format wiadomości e-mail, a następnie importuje przekonwertowany element do skrzynek pocztowych platformy Microsoft 365.

Po przechowywaniu danych XSLT/XML w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych oraz zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych na platformie Microsoft 365 przy użyciu łącznika XSLT/XML może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-xsltxml-data"></a>Omówienie archiwizacji danych XSLT/XML

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych źródłowych XSLT/XML na platformie Microsoft 365.

![Przepływ pracy archiwizacji danych XSLT/XML.](../media/XSLT-XMLConnectorWorkflow.png)

1. Twoja organizacja współpracuje ze źródłem XSLT/XML w celu skonfigurowania i skonfigurowania witryny XSLT/XML.

2. Raz na 24 godziny wiadomości czatu ze źródła XSLT/XML są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również zawartość na format wiadomości e-mail.

3. Łącznik XSLT/XML tworzony w portalu zgodności codziennie łączy się z witryną Veritas Merge1 i przesyła komunikaty do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy wiadomości do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w kroku 3. Nowy podfolder w folderze Skrzynka odbiorcza o nazwie **XSLT/XML** jest tworzony w skrzynkach pocztowych użytkownika, a elementy wiadomości są importowane do tego folderu. Łącznik wykonuje to przy użyciu wartości właściwości *Poczta e-mail* . Każda wiadomość zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/content/support/). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik XSLT/XML w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-an-xsltxml-connector"></a>Krok 1. Konfigurowanie łącznika XSLT/XML

Pierwszym krokiem jest uzyskanie dostępu do **łączników danych** w portalu zgodności i utworzenie łącznika dla danych XSLT/XML.

1. Przejdź do pozycji [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** >  danych **XSLT/XML**.

2. Na stronie Opis produktu **XSLT/XML** kliknij pozycję **Dodaj nowy łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-an-xsltxml-connector"></a>Krok 2. Konfigurowanie łącznika XSLT/XML

Drugim krokiem jest skonfigurowanie łącznika XSLT/XML w lokacji Merge1. Aby uzyskać informacje o sposobie konfigurowania łącznika XSLT/XML w witrynie Veritas Merge1, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20XSLT-XML%20User%20Guide%20.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

1. Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj poniższe kroki:

2. Na stronie **Mapowanie użytkowników XSLT/XML na użytkowników platformy Microsoft 365** włącz automatyczne mapowanie użytkowników. Elementy XSLT/XML obejmują właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem platformy Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

3. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-xsltxml-connector"></a>Krok 4. Monitorowanie łącznika XSLT/XML

Po utworzeniu łącznika XSLT/XML możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki,** a następnie wybierz łącznik **XSLT/XML** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.