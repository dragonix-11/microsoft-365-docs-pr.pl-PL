---
title: Konfigurowanie łącznika do archiwizowania danych usługi LivePerson Conversational Cloud w Microsoft 365
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
description: Dowiedz się, jak skonfigurować i użyć łącznika LivePerson Conversational Cloud DataParser 17a-4 do importowania i archiwizowania danych usługi LivePerson Conversational Cloud w Microsoft 365.
ms.openlocfilehash: e4843a5e186b35d76c0ca4e4bc38033748b40a1f
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319799"
---
# <a name="set-up-a-connector-to-archive-liveperson-conversational-cloud-data"></a>Konfigurowanie łącznika do archiwizowania danych usługi LivePerson Conversational Cloud

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj [narzędzia LivePerson Conversational Cloud DataParser](https://www.17a-4.com/liveperson-dataparser/) z pakietu 17a-4 LLC, aby zaimportować i zarchiwizować dane z usługi LivePerson Conversational Cloud do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Program DataParser zawiera łącznik chmury konwersacyjnej LivePerson skonfigurowany do przechwytywania elementów ze źródła danych innych firm i importowania tych elementów do Microsoft 365. Łącznik LivePerson Conversational Cloud DataParser konwertuje dane na format wiadomości e-mail, a następnie importuje je do skrzynek pocztowych użytkowników w Microsoft 365.

Po zapisaniu danych w skrzynkach pocztowych użytkowników można zastosować funkcje Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika chmury konwersacyjnej LivePerson może pomóc organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-liveperson-conversational-cloud-data"></a>Omówienie archiwizacji danych usługi LivePerson Conversational Cloud

W poniższym omówieniu wyjaśniono proces używania łącznika danych do archiwizowania danych usługi LivePerson Conversational Cloud w Microsoft 365.

![Przepływ pracy archiwizacji danych usługi LivePerson Conversational Cloud z zakresu od 17a do 4.](../media/LiveEngageDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania narzędzia LivePerson Conversational Cloud DataParser.

2. Regularnie elementy usługi LivePerson Conversational Cloud są zbierane przez program DataParser. Usługa DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik LivePerson Conversational Cloud DataParser utworzony w portal zgodności Microsoft Purview łączy się z usługą DataParser i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Podfolder w folderze Skrzynka odbiorcza o nazwie **LivePerson Conversational Cloud DataParser** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto DataParser dla łączników firmy Microsoft. W tym celu skontaktuj się z [17a-4 LLC](https://www.17a-4.com/contact/). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik LivePerson Conversational Cloud DataParser w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-a-liveperson-conversational-cloud-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika usługi LivePerson Conversational Cloud DataParser

Pierwszym krokiem jest dostęp do strony Łączniki danych w portalu zgodności i utworzenie łącznika 17a-4 dla danych usługi LivePerson Conversational Cloud.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję Łączniki **danychPrzejdźOsobowy konwersacyjny element DataParser w chmurze**. > 

2. Na stronie Opis produktu **LivePerson Conversational Cloud DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki opisane w kreatorze połączeń usługi LivePerson Conversational Cloud DataParser.

## <a name="step-2-configure-the-liveperson-conversational-cloud-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika LivePerson Conversational Cloud DataParser

Współpracuj z pomocą techniczną 17a-4, aby skonfigurować łącznik LivePerson Conversational Cloud DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik LivePerson Conversational Cloud DataParser automatycznie mapuje użytkowników na ich Microsoft 365 adresy e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-liveperson-conversational-cloud-dataparser-connector"></a>Krok 4. Monitorowanie łącznika LivePerson Conversational Cloud DataParser

Po utworzeniu łącznika LivePerson Conversational Cloud DataParser możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik LivePerson Conversational Cloud DataParser utworzony w celu wyświetlenia strony wysuwanej zawierającej właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
