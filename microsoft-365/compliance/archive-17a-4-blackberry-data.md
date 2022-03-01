---
title: Konfigurowanie łącznika do archiwizowania danych urządzenia BlackBerry w aplikacji Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik 17a-4 BlackBerry DataParser i używać go do importowania i archiwizowania danych urządzenia BlackBerry w Microsoft 365.
ms.openlocfilehash: 1c95a2b4f9a6a9e8054e92f27e8adbdb16aa53e3
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020705"
---
# <a name="set-up-a-connector-to-archive-blackberry-data"></a>Konfigurowanie łącznika do archiwizowania danych urządzenia BlackBerry

Za pomocą programu [BlackBerry DataParser](https://www.17a-4.com/BlackBerry-dataparser/) z firmy 17a-4 LLC można importować i archiwizować dane przedsiębiorstwa firmy BlackBerry ze skrzynkami pocztowymi użytkowników w Microsoft 365 organizacji. DataParser zawiera łącznik BlackBerry skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik BlackBerry DataParser konwertuje dane urządzenia BlackBerry na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w programie Microsoft 365.

Po zapisaniu danych urządzenia BlackBerry w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w aplikacji Microsoft 365 za pomocą łącznika blackBerry może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami.

## <a name="overview-of-archiving-blackberry-data"></a>Omówienie archiwizowania danych urządzenia BlackBerry

W poniższym o omówieniem wyjaśniono proces używania łącznika danych do archiwizowania danych urządzenia BlackBerry w aplikacji Microsoft 365.

![Zarchiwizowanie przepływu pracy dla danych urządzenia BlackBerry w godzinach 17a–4.](../media/BlackBerryDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania urządzenia BlackBerry DataParser.

2. Regularnie produkty BlackBerry są zbierane przez firmę DataParser. Program DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik BlackBerry DataParser, który tworzysz w programie Centrum zgodności platformy Microsoft 365, łączy się z programem DataParser i przesyła wiadomości do bezpiecznej lokalizacji programu Azure Storage w chmurze firmy Microsoft.

4. W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **BlackBerry DataParser** , do których są importowane elementy urządzenia BlackBerry. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element urządzenia BlackBerry zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto dataparser dla łączników firmy Microsoft. W tym celu skontaktuj się [z działem 17a-4 LLC](https://www.17a-4.com/contact/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który utworzy łącznik blackBerry DataParser w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych 17a-4 jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 Usa. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-a-blackberry-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika blackBerry DataParser

Pierwszym krokiem jest uzyskanie dostępu do strony łączników danych w aplikacji Centrum zgodności platformy Microsoft 365 utworzenie łącznika 17a-4 dla danych urządzenia BlackBerry.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki danychBlackBerry** >  **DataParser**.

2. Na stronie **Opis produktu BlackBerry DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki kreatora połączenia BlackBerry DataParser.

## <a name="step-2-configure-the-blackberry-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika BlackBerry DataParser

Skonfiguruj łącznik BlackBerry DataParser we współpracy z pomocą techniczną 17a-4.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik BlackBerry DataParser automatycznie zamapuje użytkowników na ich Microsoft 365 e-mail przed zaimportowaniem danych do programu Microsoft 365.

## <a name="step-4-monitor-the-blackberry-dataparser-connector"></a>Krok 4. Monitorowanie łącznika blackBerry DataParser

Po utworzeniu łącznika programu BlackBerry DataParser można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz utworzony łącznik BlackBerry DataParser, aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.