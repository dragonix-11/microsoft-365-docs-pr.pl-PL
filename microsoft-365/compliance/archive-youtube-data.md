---
title: Konfigurowanie łącznika do archiwizowania danych z serwisu YouTube w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z serwisu YouTube z veritas do usługi Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizowania tych danych możesz zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja prawnie, zbierania elektronicznych materiałów dowodowych i zasady przechowywania.
ms.openlocfilehash: 0441299c7c0d58855685393526504e2e355343ad
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328235"
---
# <a name="set-up-a-connector-to-archive-youtube-data"></a>Konfigurowanie łącznika do archiwizowania danych z serwisu YouTube

Za pomocą łącznika veritas w pliku Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania danych z witryny YouTube do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas udostępnia łącznik skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik konwertuje zawartość, taką jak czaty, załączniki, zadania, notatki i wpisy z witryny YouTube, na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w aplikacji Microsoft 365.

Po przechowywaniu danych z witryny YouTube w skrzynkach pocztowych użytkowników można stosować funkcje zgodności Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w aplikacji Microsoft 365 za pomocą łącznika Serwisu YouTube może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami.

## <a name="overview-of-archiving-youtube-data"></a>Omówienie archiwizowania danych z serwisu YouTube

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych z serwisu YouTube w Microsoft 365.

![Archiwizowanie przepływu pracy dla danych z serwisu YouTube.](../media/YouTubeConnectorWorkflow.png)

1. Twoja organizacja współpracuje z serwisem YouTube w celu skonfigurowania i skonfigurowania witryny YouTube.

2. Elementy z witryny YouTube są kopiowane do witryny Veritas Merge1 co 24 godziny. Łącznik konwertuje również elementy z serwisu YouTube na format wiadomości e-mail.

3. Łącznik YouTube, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 każdego dnia i przesyła zawartość z witryny YouTube do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **YouTube** , a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element z serwisu YouTube zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika tego elementu.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto Merge1 dla łączników Microsoft. Aby utworzyć to konto, skontaktuj się z [działem obsługi klienta firmy Veritas](https://www.veritas.com/form/requestacall/ms-connectors-contact). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Utwórz aplikację YouTube, aby pobierać dane z konta youtube. Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf).

- Użytkownik, który utworzy łącznik z serwisu YouTube w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-set-up-the-youtube-connector"></a>Krok 1. Konfigurowanie łącznika serwisu YouTube

Pierwszym krokiem jest uzyskanie dostępu do strony **łączników** danych w aplikacji Centrum zgodności platformy Microsoft 365 utworzenie łącznika dla danych z serwisu YouTube.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki** **danychYouTube** > .

2. Na stronie **Opis produktu z witryny YouTube** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-youtube-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie witryny YouTube w witrynie Veritas Merge1

Drugi krok to skonfigurowanie łącznika YouTube w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika serwisu YouTube, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników z witryny YouTube Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy z serwisu YouTube zawierają właściwość o nazwie *Poczta* e-mail, która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-youtube-connector"></a>Krok 4. Monitorowanie łącznika serwisu YouTube

Po utworzeniu łącznika z serwisu YouTube można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com/> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik **z witryny YouTube** , aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
