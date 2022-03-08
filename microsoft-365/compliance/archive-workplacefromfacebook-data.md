---
title: Konfigurowanie łącznika do archiwizowania danych z serwisu Facebook w aplikacji Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik w celu importowania i archiwizowania danych z miejsca pracy z serwisu Facebook, który jest archiwizowany w witrynie Veritas Merge1 w Microsoft 365. Skonfigurowanie łącznika wymaga współpracy z veritas Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w programie Microsoft 365 w celu zarządzania danymi innych firm za pomocą funkcji zgodności, takich jak archiwizacja ze względu na zgodność z przepisami, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: ebf6f8f4aab2ac4290610458e10181d8e74181f2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312267"
---
# <a name="set-up-a-connector-to-archive-workplace-from-facebook-data"></a>Konfigurowanie łącznika do archiwizowania danych z serwisu Facebook w miejscu pracy

Za pomocą łącznika usługi Veritas w Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane z miejsca pracy z serwisu Facebook do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Serwis Veritas udostępnia łącznik usługi [Facebook](https://globanet.com/workplace/) Workplace, który jest skonfigurowany do regularnego przechwytywania elementów ze źródła danych innych firm oraz importowania ich do usługi Microsoft 365. Łącznik konwertuje zawartość, taką jak czaty, załączniki, wpisy i klipy wideo z miejsca pracy, na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w programie Microsoft 365.

Po przechowywaniu danych w skrzynkach pocztowych użytkowników w miejscu pracy można stosować funkcje zgodności usługi Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika serwisu Facebook w miejscu pracy może ułatwić organizacji zgodność z zasadami rządowymi i przepisami.

## <a name="overview-of-archiving-workplace-from-facebook-data"></a>Omówienie archiwizowania danych w miejscu pracy z serwisu Facebook

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych w Microsoft 365.

![Archiwizowanie przepływu pracy dla miejsca pracy z danych serwisu Facebook.](../media/WorkplaceConnectorWorkflow.png)

1. Twoja organizacja współpracuje z serwisem Workplace z serwisu Facebook w celu skonfigurowania i skonfigurowania witryny miejsca pracy.

2. Elementy z miejsca pracy są kopiowane do witryny Veritas Merge1 co 24 godziny. Łącznik konwertuje także zawartość tych elementów na format wiadomości e-mail.

3. Łącznik Workplace z serwisu Facebook, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z usługą Veritas Merge1 każdego dnia i przesyła elementy miejsca pracy do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w kroku 3. Zostanie utworzony podfolder w folderze Skrzynka odbiorcza o nazwie Miejsce pracy z serwisu **Facebook** , a elementy w tym folderze zostaną zaimportowane do tego folderu. Łącznik robi to przy użyciu wartości właściwości *Email* . Każdy element Workplace zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika czatu lub wpisu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [działem obsługi klienta firmy Veritas](https://globanet.com/ms-connectors-contact). Do tego konta zalogujesz się podczas tworzenia łącznika w kroku 1.

- Utwórz niestandardową integrację w miejscu https://my.workplace.com/work/admin/apps/ pobierania danych z miejsca pracy za pośrednictwem interfejsów API na potrzeby zgodności i zbierania elektronicznych materiałów dowodowych.

   Podczas tworzenia integracji platforma Workplace generuje zestaw unikatowych poświadczeń używanych do generowania tokenów używanych do uwierzytelniania. Te tokeny są używane w kreatorze konfiguracji łącznika serwisu Facebook w kroku 2. Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

- Użytkownik, który tworzy łącznik w serwisie Facebook w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-workplace-from-facebook-connector"></a>Krok 1. Konfigurowanie łącznika w serwisie Facebook

Pierwszym krokiem jest uzyskanie dostępu do strony  łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych w miejscu pracy.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki** **danychZabędzie** >  z serwisu Facebook.

2. Na stronie **Opis produktu w miejscu pracy** z serwisu Facebook kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-workplace-from-facebook-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika miejsca pracy z serwisu Facebook w witrynie Veritas Merge1

Drugi krok to skonfigurowanie łącznika w serwisie Facebook w witrynie Scal1. Aby uzyskać informacje na temat konfigurowania łącznika serwisu Facebook w miejscu pracy, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników zewnętrznych Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy w miejscu pracy zawierają właściwość o nazwie Poczta *e-mail* zawierającą adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-workplace-from-facebook-connector"></a>Krok 4. Monitorowanie miejsca pracy z łącznika serwisu Facebook

Po utworzeniu łącznika Miejsce pracy z serwisu Facebook można wyświetlić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik **Miejsce pracy z serwisu Facebook** , aby wyświetlić stronę wysuwu. Ta strona zawiera właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.