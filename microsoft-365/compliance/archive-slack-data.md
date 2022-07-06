---
title: Konfigurowanie łącznika do archiwizowania danych zbierania elektronicznych materiałów dowodowych usługi Slack na platformie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z usługi Veritas Slack eDiscovery na platformie Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm na platformie Microsoft 365. Po zarchiwizowania tych danych można zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: e48bd25b5f444ce17eba08677f5bd1c1171af1ff
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637754"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data"></a>Konfigurowanie łącznika do archiwizowania danych zbierania elektronicznych materiałów dowodowych usługi Slack

Użyj łącznika Veritas w portal zgodności Microsoft Purview, aby importować i archiwizować dane innych firm z mediów społecznościowych, wiadomości błyskawicznych i platform współpracy dokumentów do skrzynek pocztowych w organizacji platformy Microsoft 365. Usługa Veritas udostępnia łącznik [usługi Slack](https://globanet.com/slack/) skonfigurowany do przechwytywania elementów ze źródła danych innych firm (regularnie), a następnie importowania tych elementów na platformę Microsoft 365. Usługa Slack pobiera komunikaty i pliki z interfejsu API usługi Slack i konwertuje je na format wiadomości e-mail, a następnie importuje element do skrzynek pocztowych użytkowników.

Po przechowywaniu danych zbierania elektronicznych materiałów dowodowych usługi Slack w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych na platformie Microsoft 365 przy użyciu łącznika usługi Slack może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Omówienie archiwizacji danych zbierania elektronicznych materiałów dowodowych usługi Slack

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania informacji usługi Slack na platformie Microsoft 365.

![Przepływ pracy archiwizacji usługi Slack.](../media/SlackConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą Slack w celu skonfigurowania i skonfigurowania witryny usługi Slack.

2. Co 24 godziny wiadomości czatu z usługi Slack eDiscovery są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również zawartość wiadomości czatu na format wiadomości e-mail.

3. Łącznik usługi Slack eDiscovery tworzony w portalu zgodności codziennie łączy się z witryną Veritas Merge1 i przesyła komunikaty rozmów do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje konwertowane elementy wiadomości czatu do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* i automatycznego mapowania użytkowników, zgodnie z opisem w kroku 3. Nowy podfolder w folderze Skrzynka odbiorcza o nazwie **Slack eDiscovery** jest tworzony w skrzynkach pocztowych użytkownika, a elementy wiadomości czatu są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każda wiadomość czatu zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika wiadomości czatu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z [pomocą techniczną veritas](https://globanet.com/ms-connectors-contact). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Uzyskaj nazwę użytkownika i hasło dla konta usługi Slack enterprise w organizacji. Podczas konfigurowania usługi Slack musisz zalogować się do tego konta w kroku 2.

- Użytkownik, który tworzy łącznik zbierania elektronicznych materiałów dowodowych usługi Slack w kroku 1 (i kończy go w kroku 3), musi mieć przypisaną rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-slack-ediscovery-connector"></a>Krok 1. Konfigurowanie łącznika zbierania elektronicznych materiałów dowodowych usługi Slack

Pierwszym krokiem jest dostęp do strony **Łączniki danych** w portalu zgodności i utworzenie łącznika dla danych usługi Slack.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** >  danych **Slack eDiscovery**.

2. Na stronie Opis produktu **Slack eDiscovery** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-slack-ediscovery"></a>Krok 2. Konfigurowanie zbierania elektronicznych materiałów dowodowych usługi Slack

Drugim krokiem jest skonfigurowanie łącznika usługi Slack eDiscovery w witrynie Merge1. Aby uzyskać więcej informacji na temat konfigurowania łącznika zbierania elektronicznych materiałów dowodowych usługi Slack w witrynie Veritas Merge1, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Slack%20eDiscovery%20User%20Guide.pdf) firm).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

1. Na stronie **Mapowanie użytkowników zewnętrznych na użytkowników platformy Microsoft 365** włącz automatyczne mapowanie użytkowników.

   Elementy zbierania elektronicznych materiałów dowodowych usługi Slack obejmują właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem platformy Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-slack-ediscovery-connector"></a>Krok 4. Monitorowanie łącznika zbierania elektronicznych materiałów dowodowych usługi Slack

Po utworzeniu łącznika usługi Slack eDiscovery możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki,** a następnie wybierz łącznik **Slack eDiscovery** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.