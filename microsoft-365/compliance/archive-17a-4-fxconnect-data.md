---
title: Konfigurowanie łącznika 17a-4 DataParser do archiwizowania Połączenie danych w programie Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik 17a–4 FX 17a–4 Połączenie DataParser do importowania i archiwizowania danych Połączenie w programie Microsoft 365.
ms.openlocfilehash: 129d5f6836d8cf447b77bf068a4c6b5f33b33703
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311805"
---
# <a name="set-up-a-connector-to-archive-data-from-fx-connect"></a>Konfigurowanie łącznika do archiwizowania danych z fx-Połączenie

Za pomocą [parser FX Połączenie DataParser](https://www.17a-4.com/dataparser-roadmap/) z firmy 17a–4 LLC można importować i archiwizować dane z usługi FX Połączenie do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. DataParser zawiera łącznik fx-Połączenie skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik fx Połączenie DataParser konwertuje dane programu FX Połączenie na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w programie Microsoft 365.

Po zapisaniu Połączenie FX w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Połączenie za pomocą łącznika funkcji FX w programie Microsoft 365 może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulowymi.

## <a name="overview-of-archiving-fx-connect-data"></a>Omówienie archiwizowania danych FX Połączenie danych

Poniższe omówienie przedstawia proces używania łącznika danych do archiwizowania danych fx w Połączenie w programie Microsoft 365.

![Archiwizacja przepływu pracy dla Połączenie FX z 17a–4.](../media/FXConnectDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z planem 17a–4 w celu skonfigurowania i skonfigurowania współpracy Połączenie FX DataParser.

2. Regularnie wszystkie elementy Połączenie są zbierane przez firmę DataParser. Program DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik fx Połączenie DataParser, który tworzysz w psłudze Centrum zgodności platformy Microsoft 365, łączy się z programem DataParser i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **FX Połączenie DataParser**, a elementy Połączenie FX są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy Połączenie FX zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto dataparser dla łączników firmy Microsoft. W tym celu skontaktuj się [z działem 17a-4 LLC](https://www.17a-4.com/contact/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który tworzy łącznik łącznika fx Połączenie DataParser w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 Usa. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-a-fx-connect-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika fx Połączenie DataParser

Pierwszym krokiem jest uzyskanie dostępu do strony łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika 17a-4 dla łączników FX Połączenie danych.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij **pozycję Łączniki danychFX** >  **Połączenie DataParser**.

2. Na stronie **Fx Połączenie DataParser** product description (Opis produktu firmy DataParser) kliknij pozycję **Add connector (Dodaj łącznik**).

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj czynności opisane w kreatorze Połączenie DataParser.

## <a name="step-2-configure-the-fx-connect-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika fx Połączenie DataParser

Za pomocą pomocy technicznej 17a–4 skonfiguruj łącznik fx Połączenie DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik fx Połączenie DataParser automatycznie zamapuje użytkowników na ich Microsoft 365 e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-fx-connect-dataparser-connector"></a>Krok 4. Monitorowanie łącznika fx Połączenie DataParser

Po utworzeniu łącznika FX Połączenie DataParser można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki**, a następnie wybierz utworzony łącznik FX Połączenie DataParser w celu wyświetlenia strony wysuwu zawierającej właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
