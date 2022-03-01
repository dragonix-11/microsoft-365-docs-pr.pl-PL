---
title: Konfigurowanie łącznika do archiwizowania danych z chmury konwersacji programu LivePerson w programie Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik 17a–4 LivePerson Conversational Cloud DataParser i używać go do importowania i archiwizowania danych z chmury konwersacji programu LivePerson w programie Microsoft 365.
ms.openlocfilehash: a61acf0c5755d926a775ac6d6ca21c6552290904
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020795"
---
# <a name="set-up-a-connector-to-archive-liveperson-conversational-cloud-data"></a>Konfigurowanie łącznika do archiwizowania danych z chmury konwersacji programu LivePerson

Za pomocą programu [LivePerson Conversational Cloud DataParser](https://www.17a-4.com/liveperson-dataparser/) z firmy 17a-4 LLC. można importować i archiwizować dane z chmury konwersacji programu LivePerson do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. DataParser zawiera łącznik Chmury konwersacji LivePerson, który jest skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik LivePerson Conversational Cloud DataParser konwertuje dane na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w programie Microsoft 365.

Po zapisaniu danych w skrzynkach pocztowych użytkowników można stosować funkcje zgodności usługi Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z przepisami komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika chmury konwersacji LivePerson może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulowymi.

## <a name="overview-of-archiving-liveperson-conversational-cloud-data"></a>Omówienie archiwizowania danych w chmurze konwersacji LivePerson

W poniższym o omówieniem wyjaśniono proces używania łącznika danych do archiwizowania danych z chmury konwersacji programu LivePerson w programie Microsoft 365.

![Archiwizowanie przepływu pracy dla danych liveperson konwersacji w chmurze z 17a–4.](../media/LiveEngageDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania dostawcy danych LivePerson Conversational Cloud DataParser.

2. Dostawcy danych regularnie zbierają elementy chmury konwersacji livepersona. Program DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik programu LivePerson Conversational Cloud DataParser, który tworzysz w programie Centrum zgodności platformy Microsoft 365, łączy się z programem DataParser i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **LivePerson Conversational Cloud DataParser** , a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto dataparser dla łączników firmy Microsoft. W tym celu skontaktuj się [z działem 17a-4 LLC](https://www.17a-4.com/contact/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który tworzy łącznik LivePerson Conversational Cloud DataParser w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych 17a-4 jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 Usa. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-a-liveperson-conversational-cloud-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika usługi LivePerson Conversational Cloud DataParser

Pierwszym krokiem jest uzyskanie dostępu do strony łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika 17a-4 dla danych chmury konwersacji LivePerson.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij **pozycję Łączniki danychLivePerson** >  **Conversational Cloud DataParser**.

2. Na stronie **Opis produktu LivePerson Conversational Cloud DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki kreatora połączenia LivePerson Conversational Cloud DataParser.

## <a name="step-2-configure-the-liveperson-conversational-cloud-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika LivePerson Conversational Cloud DataParser

Skonfiguruj łącznik LivePerson Conversational Cloud DataParser we współpracy z pomocą techniczną 17a-4.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik LivePerson Conversational Cloud DataParser automatycznie zamapuje użytkowników na ich Microsoft 365 e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-liveperson-conversational-cloud-dataparser-connector"></a>Krok 4. Monitorowanie łącznika LivePerson Conversational Cloud DataParser

Po utworzeniu łącznika usługi LivePerson Conversational Cloud DataParser można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik LivePerson Conversational Cloud DataParser utworzony w celu wyświetlenia strony wysuwu zawierającej właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
