---
title: Konfigurowanie łącznika do archiwizowania danych z programu InvestEdge w Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik 17a–4 InvestEdge DataParser i używać go do importowania i archiwizowania danych z programu InvestEdge w Microsoft 365.
ms.openlocfilehash: 5ee98f1bd4800685160bf77d5bcbc13ca4fe6c29
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318315"
---
# <a name="set-up-a-connector-to-archive-investedge-data"></a>Konfigurowanie łącznika do archiwizowania danych z programu InvestEdge

Za pomocą [programu InvestEdge DataParser](https://www.17a-4.com/investedge-dataparser/) z firmy 17a-4 LLC można importować i archiwizować dane z programu InvestEdge do skrzynek pocztowych użytkowników Microsoft 365 organizacji. Program DataParser zawiera łącznik InvestEdge, który jest skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik InvestEdge DataParser konwertuje dane programu InvestEdge na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w programie Microsoft 365.

Po zapisaniu danych z programu InvestEdge w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika InvestEdge może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-investedge-data"></a>Omówienie archiwizowania danych z usługi InvestEdge

Poniższe omówienie przedstawia proces używania łącznika danych do archiwizowania danych z usługi InvestEdge w programie Microsoft 365.

![Archiwizowanie przepływu pracy dla danych InvestEdge z 17a–4.](../media/InvestEdgeDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a–4 w celu skonfigurowania i skonfigurowania programu InvestEdge DataParser.

2. Regularnie produkty InvestEdge są zbierane przez firmę DataParser. Program DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik programu InvestEdge DataParser dzielony w programie Centrum zgodności platformy Microsoft 365 łączy się z programem DataParser i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **InvestEdge DataParser** , a elementy z grupy InvestEdge są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element InvestEdge zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto dataparser dla łączników firmy Microsoft. W tym celu skontaktuj się [z działem 17a-4 LLC](https://www.17a-4.com/contact/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który tworzy łącznik InvestEdge DataParser w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 Usa. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-a-investedge-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika InvestEdge DataParser

Pierwszym krokiem jest uzyskanie dostępu do strony łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika 17a-4 dla danych InvestEdge.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij **pozycję Łączniki** **danychInwestycji** >  DataParser.

2. Na stronie **Opis produktu InvestEdge DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki kreatora połączenia InvestEdge DataParser.

## <a name="step-2-configure-the-investedge-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika InvestEdge DataParser

We współpracy z pomocą techniczną 17a–4 skonfiguruj łącznik InvestEdge DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik InvestEdge DataParser automatycznie zamapuje użytkowników na ich adresy e Microsoft 365 e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-investedge-dataparser-connector"></a>Krok 4. Monitorowanie łącznika InvestEdge DataParser

Po utworzeniu łącznika InvestEdge DataParser można wyświetlić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz utworzony łącznik InvestEdge DataParser w celu wyświetlenia strony wysuwanej zawierającej właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
