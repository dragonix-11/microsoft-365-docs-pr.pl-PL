---
title: Konfigurowanie łącznika w celu archiwizowania danych Połączenie w czacie w Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik 17a–4 ICE Połączenie Czat DataParser do importowania i archiwizowania danych ice Połączenie czatów w Microsoft 365.
ms.openlocfilehash: 632426422bd8f9db984b66fdea08276b7345441c
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020704"
---
# <a name="set-up-a-connector-to-archive-ice-connect-chat-data"></a>Konfigurowanie łącznika do archiwizowania danych ice Połączenie czatów

Użyj programu [ICE DataParser](https://www.17a-4.com/ice-dataparser/) z firmy 17a-4 LLC, aby zaimportować i zarchiwizować dane z usługi ICE Połączenie Czat ze skrzynkami pocztowymi użytkowników w Microsoft 365 organizacji. DataParser zawiera łącznik ICE Chat skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik ICE DataParser konwertuje dane ice Połączenie na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po zapisaniu danych Połączenie ICE w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak Zastosowanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika ICE DataParser może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-ice-chat-data"></a>Omówienie archiwizowania danych czatu ICE

Poniższe omówienie przedstawia proces używania łącznika danych do archiwizowania danych w Połączenie danych czatu w Microsoft 365.

![Archiwizacja przepływu pracy dla Połączenie czatów z 17a–4.](../media/ICEChatDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania programu ICE DataParser.

2. Regularnie ice Połączenie czatów jest zbierany przez DataParser. Program DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik ICE DataParser, który tworzysz w aplikacji Centrum zgodności platformy Microsoft 365, łączy się z programem DataParser i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **ICE DataParser**, a elementy czatu Połączenie ICE Połączenie do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element Połączenie ICE zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto dataparser dla łączników firmy Microsoft. W tym celu skontaktuj się [z działem 17a-4 LLC](https://www.17a-4.com/contact/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który tworzy łącznik ICE DataParser w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych 17a-4 jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 Usa. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-an-ice-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika ice DataParser

Pierwszym krokiem jest uzyskanie dostępu do strony łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika 17a-4 dla łącznika ICE Połączenie danych czatu.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki** **danychCenaParser** >  danych.

2. Na stronie **opis produktu ICE DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki kreatora połączenia ICE DataParser.

## <a name="step-2-configure-the-ice-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika ICE DataParser

Skonfiguruj łącznik ICE DataParser we współpracy z pomocą techniczną 17a-4.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik ICE DataParser automatycznie zamapuje użytkowników na ich Microsoft 365 e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-ice-dataparser-connector"></a>Krok 4. Monitorowanie łącznika ICE DataParser

Po utworzeniu łącznika ICE DataParser można wyświetlić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz utworzony łącznik ICE DataParser w celu wyświetlenia strony wysuwu zawierającej właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
