---
title: Konfigurowanie łącznika do archiwizowania danych InvestEdge w Microsoft 365
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
description: Dowiedz się, jak skonfigurować i użyć łącznika InvestEdge DataParser 17a-4 do importowania i archiwizowania danych InvestEdge w Microsoft 365.
ms.openlocfilehash: cc10c5a798e9e85da7f95769926df8446187434c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998101"
---
# <a name="set-up-a-connector-to-archive-investedge-data"></a>Konfigurowanie łącznika do archiwizowania danych InvestEdge

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj [narzędzia InvestEdge DataParser](https://www.17a-4.com/investedge-dataparser/) z firmy 17a-4 LLC, aby zaimportować i zarchiwizować dane z aplikacji InvestEdge do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Program DataParser zawiera łącznik InvestEdge skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania tych elementów do Microsoft 365. Łącznik InvestEdge DataParser konwertuje dane InvestEdge na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po zapisaniu danych InvestEdge w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika InvestEdge może pomóc organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-investedge-data"></a>Omówienie archiwizacji danych InvestEdge

W poniższym omówieniu wyjaśniono proces korzystania z łącznika danych do archiwizowania danych InvestEdge w Microsoft 365.

![Przepływ pracy archiwizacji dla danych InvestEdge z zakresu 17a-4.](../media/InvestEdgeDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania narzędzia InvestEdge DataParser.

2. W regularnych odstępach czasu elementy InvestEdge są zbierane przez użytkownika DataParser. Usługa DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik InvestEdge DataParser utworzony w portalu zgodności usługi Microsoft Purview łączy się z aplikacją DataParser i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Podfolder w folderze Skrzynka odbiorcza o nazwie **InvestEdge DataParser** jest tworzony w skrzynkach pocztowych użytkownika, a elementy InvestEdge są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element InvestEdge zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto DataParser dla łączników firmy Microsoft. W tym celu skontaktuj się z [17a-4 LLC](https://www.17a-4.com/contact/). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik InvestEdge DataParser w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-a-investedge-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika InvestEdge DataParser

Pierwszym krokiem jest dostęp do strony Łączniki danych w portalu zgodności i utworzenie łącznika 17a-4 dla danych InvestEdge.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  **danychInwestuj daneParser**.

2. Na stronie Opis produktu **InvestEdge DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki opisane w kreatorze połączenia InvestEdge DataParser.

## <a name="step-2-configure-the-investedge-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika InvestEdge DataParser

Współpracuj z pomocą techniczną 17a-4, aby skonfigurować łącznik InvestEdge DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik InvestEdge DataParser automatycznie mapuje użytkowników na Microsoft 365 adresy e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-investedge-dataparser-connector"></a>Krok 4. Monitorowanie łącznika InvestEdge DataParser

Po utworzeniu łącznika InvestEdge DataParser możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz utworzony łącznik InvestEdge DataParser, aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
