---
title: Konfigurowanie łącznika w celu archiwizowania ponownego przetwarzania danych w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik w celu importowania i archiwizowania reutersów przetwarzających dane z veritas do Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizować te dane możesz zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 7e978af3c0916b277fcf97d9fe58c9b7cea08d43
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314618"
---
# <a name="set-up-a-connector-to-archive-reuters-dealing-data"></a>Konfigurowanie łącznika do archiwizowania ponownego przetwarzania danych

Za pomocą łącznika usługi Veritas w Centrum zgodności platformy Microsoft 365 importowanie i archiwizowanie danych z platformy Reuters Dealing (Reuters) do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas udostępnia łącznik [Reuters Dealing (Reuters Dealing](https://globanet.com/reuters-dealing/) connector), który jest skonfigurowany do regularnego przechwytywania elementów ze źródła danych innych firm, a następnie importuje je do Microsoft 365. Łącznik konwertuje wartość W przypadku komunikacji z kontem obsługi wiadomości e-mail na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w programie Microsoft 365.

Po przechowywaniu przez reutery danych w skrzynkach pocztowych użytkowników można stosować funkcje zgodności, takie Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika reuters w celu zachowania zgodności z zasadami rządowymi i przepisami regulowymi.

## <a name="overview-of-archiving-reuters-dealing-data"></a>Omówienie archiwizowania reuterów w celu zarchiwizowania danych

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania reuterów dotyczących danych w Microsoft 365.

![Archiwizowanie przepływu pracy dla reutersów przetwarzających dane.](../media/ReuetersDealingConnectorWorkflow.png)

1. Organizacja współpracuje z działami reuterów w celu skonfigurowania witryny reuters.

2. Co 24 godziny są kopiowane reuters do witryny Veritas Merge1. Łącznik konwertuje także elementy na format wiadomości e-mail.

3. Łącznik reuters w środowisku Centrum zgodności platformy Microsoft 365 jest codziennie łączony z witryną scalania Veritas i przesyła zawartość do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder  w folderze Skrzynka odbiorcza o nazwie Kontakty, a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element reuters w związku z wiadomościami zawiera tę właściwość, która jest wypełniana adresami e-mail wszystkich uczestników tego elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z działem [obsługi klienta firmy Veritas](https://globanet.com/contact-us). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który tworzy łącznik reuters w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-reuters-dealing-connector"></a>Krok 1. Konfigurowanie łącznika reuters w celu pracy

Pierwszym krokiem jest uzyskanie dostępu do strony  łączników danych w Microsoft 365 i utworzenie łącznika dla reuterów przetwarzających dane.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki danychRęki** > .

2. Na stronie **Reuters Dealing product description (Reuters Dealing** product description) kliknij pozycję **Add connector (Dodaj łącznik**).

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-reuters-dealing-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika reuters dealing w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika reuters dealing w witrynie Veritas w witrynie Merge1. Aby uzyskać informacje na temat konfigurowania łącznika reuters w celu pracy z nim, zobacz [Podręcznik użytkownika scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20Dealing%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Reuters mapowanie kontaktów z Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników.

   Pozycja Reuters Dealing items (Reuters Dealing items) zawiera właściwość *o nazwie Email* (Poczta e-mail), która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia i przejdź do strony Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-reuters-dealing-connector"></a>Krok 4. Monitorowanie pracy łącznika reuters

Po utworzeniu łącznika reuters w celu wyświetlenia stanu łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com/) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz pozycję **Reuters Dealing connector (Reuters Dealing connector** ), aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.