---
title: Konfigurowanie łącznika do archiwizowania danych XSLT/XML w Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik w celu importowania i archiwizowania danych XSLT/XML z usługi Veritas w Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w programie Microsoft 365 w celu zarządzania danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze standardami prawnie, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 9f8d33099dee0126922d3170f458317875293af8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322103"
---
# <a name="set-up-a-connector-to-archive-xsltxml-data"></a>Konfigurowanie łącznika do archiwizowania danych XSLT/XML

Za pomocą łącznika veritas w Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane ze źródła strony sieci Web do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Wersja Veritas udostępnia łącznik [XSLT/XML](https://globanet.com/xslt-xml), który umożliwia szybkie opracowywanie plików utworzonych przy użyciu przekształcenia języka XSLT (przekształceń języka rozszerzanego arkusza stylów) w celu przekształcania plików XML na inne formaty plików (takie jak HTML lub tekst), które można zaimportować do systemu Microsoft 365. Łącznik konwertuje zawartość elementu ze źródła XSLT/XML na format wiadomości e-mail, a następnie importuje przekonwertowany element do Microsoft 365 pocztowych.

Po zapisaniu danych XSLT/XML w skrzynkach pocztowych użytkowników można stosować funkcje zgodności usługi Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika XSLT/XML może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-xsltxml-data"></a>Omówienie archiwizowania danych XSLT/XML

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych źródłowych XSLT/XML w Microsoft 365.

![Zarchiwizowanie przepływu pracy dla danych XSLT/XML.](../media/XSLT-XMLConnectorWorkflow.png)

1. Twoja organizacja współpracuje ze źródłem XSLT/XML w celu skonfigurowania witryny XSLT/XML.

2. Wiadomości czatu ze źródła XSLT/XML są kopiowane do witryny Veritas Merge1 co 24 godziny. Łącznik konwertuje także zawartość na format wiadomości e-mail.

3. Łącznik XSLT/XML, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 każdego dnia i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaimnuje przekonwertowane elementy wiadomości do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w kroku 3. W skrzynkach pocztowych użytkowników jest tworzony nowy podfolder w folderze skrzynki odbiorczej o nazwie **XSLT/XML** , a elementy wiadomości są importowane do tego folderu. Łącznik robi to przy użyciu wartości właściwości *Email* . Każda wiadomość zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [działem obsługi klienta firmy Veritas](https://www.veritas.com/content/support/). Do tego konta zalogujesz się podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik XSLT/XML w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-an-xsltxml-connector"></a>Krok 1. Konfigurowanie łącznika XSLT/XML

Pierwszym krokiem jest uzyskanie dostępu do łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych XSLT/XML.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki danychXSLT** > /XML.

2. Na stronie **Opis produktu XSLT/XML** kliknij pozycję **Dodaj nowy łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-an-xsltxml-connector"></a>Krok 2. Konfigurowanie łącznika XSLT/XML

Drugim krokiem jest skonfigurowanie łącznika XSLT/XML w witrynie Merge1. Aby uzyskać informacje na temat konfigurowania łącznika XSLT/XML w witrynie Veritas Merge1, zobacz Przewodnik użytkownika do [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20XSLT-XML%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

1. Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj poniższe czynności:

2. Na stronie **Mapowanie użytkowników języka XSLT/XML na Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy XSLT/XML zawierają właściwość o nazwie Email (Poczta *e-mail*), która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

3. Kliknij **przycisk** Dalej, przejrzyj ustawienia i przejdź do strony Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-xsltxml-connector"></a>Krok 4. Monitorowanie łącznika XSLT/XML

Po utworzeniu łącznika XSLT/XML można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik **XSLT/XML** , aby wyświetlić stronę wysuwu. Ta strona zawiera właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.