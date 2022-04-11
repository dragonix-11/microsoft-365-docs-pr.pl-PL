---
title: Konfigurowanie łącznika do archiwizowania danych usługi Slack w Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik usługi Slack DataParser 17a-4 i używać go do importowania i archiwizowania danych usługi Slack w Microsoft 365.
ms.openlocfilehash: 6288f7f312a9b7dc6e8be15df93e8b9f3ee39ee0
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761290"
---
# <a name="set-up-a-connector-to-archive-slack-data"></a>Konfigurowanie łącznika do archiwizowania danych usługi Slack

Użyj [narzędzia DataParser z 17a-4 LLC](https://www.17a-4.com/slack-dataparser/), aby zaimportować i zarchiwizować dane z platformy Slack do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Program DataParser zawiera łącznik usługi Slack skonfigurowany do przechwytywania elementów ze źródła danych innych firm i importowania tych elementów do Microsoft 365. Łącznik Slack DataParser konwertuje dane usługi Slack na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po przechowywaniu danych usługi Slack w skrzynkach pocztowych użytkowników można zastosować Microsoft 365 funkcje zgodności, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika usługi Slack może pomóc organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-slack-data"></a>Omówienie archiwizacji danych usługi Slack

W poniższym omówieniu wyjaśniono proces korzystania z łącznika danych do archiwizowania danych usługi Slack w Microsoft 365.

![Archiwizowanie przepływu pracy dla danych usługi Slack z zakresu 17a-4.](../media/SlackDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania narzędzia Slack DataParser.

2. Regularnie elementy usługi Slack są zbierane przez program DataParser. Usługa DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik Slack DataParser utworzony w Centrum zgodności platformy Microsoft 365 łączy się z aplikacją DataParser i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Podfolder w folderze Skrzynka odbiorcza o nazwie **Slack DataParser** jest tworzony w skrzynkach pocztowych użytkownika, a elementy usługi Slack są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element usługi Slack zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto DataParser dla łączników firmy Microsoft. W tym celu skontaktuj się z [17a-4 LLC](https://www.17a-4.com/contact/). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownikowi, który tworzy łącznik Usługi Slack DataParser w kroku 1 (i kończy go w kroku 3) musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i w związku z tym nie są objęte zobowiązaniami dotyczącymi zgodności Microsoft 365 i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-a-slack-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika Usługi Slack DataParser

Pierwszym krokiem jest dostęp do strony Łączniki danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika 17a-4 dla danych usługi Slack.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  **danychSlack DataParser**.

2. Na stronie Opis produktu **Slack DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki opisane w kreatorze połączeń usługi Slack DataParser.

## <a name="step-2-configure-the-slack-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika Usługi Slack DataParser

Współpracuj z obsługą wersji 17a-4, aby skonfigurować łącznik Usługi Slack DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik Slack DataParser automatycznie mapuje użytkowników na Microsoft 365 adresy e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-slack-dataparser-connector"></a>Krok 4. Monitorowanie łącznika Slack DataParser

Po utworzeniu łącznika Usługi Slack DataParser możesz wyświetlić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz utworzony łącznik Slack DataParser, aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
