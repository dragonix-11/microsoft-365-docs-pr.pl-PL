---
title: Konfigurowanie łącznika do archiwizowania danych spotkań powiększenia w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych ze spotkań przybliżania veritas w Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w programie Microsoft 365, aby zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: f776fe3d03f8674a698b5c8fe2f355aa5635577f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327311"
---
# <a name="set-up-a-connector-to-archive-zoom-meetings-data"></a>Konfigurowanie łącznika do archiwizowania danych spotkań z powiększeniem

Za pomocą łącznika veritas w Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane ze spotkań powiększania do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas [udostępnia łącznik spotkań](https://globanet.com/zoom/) z powiększeniem, który jest skonfigurowany do regularnego przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik konwertuje zawartość spotkań (w tym czaty, zarejestrowane pliki i metadane) z konta powiększeń spotkań na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po przechowywaniu danych spotkań powiększenia w skrzynkach pocztowych użytkowników można stosować funkcje zgodności usługi Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika spotkań z powiększeniem może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami prawa.

## <a name="overview-of-archiving-zoom-meetings-data"></a>Omówienie archiwizowania danych spotkań z powiększeniem

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych spotkań powiększenia w Microsoft 365.

![Przepływ pracy archiwizowania spotkań powiększenia.](../media/ZoomMeetingsConnectorWorkflow.png)

1. Twoja organizacja współpracuje ze spotkaniami z powiększeniem, aby skonfigurować witrynę Spotkania z powiększeniem.

2. Co 24 godziny elementy spotkania z widoku Spotkania z powiększeniem są kopiowane do witryny Veritas Merge1. Łącznik konwertuje także zawartość spotkań na format wiadomości e-mail.

3. Łącznik Powiększ spotkania tworzyć w Centrum zgodności platformy Microsoft 365, łączy się z usługą Veritas Merge1 każdego dnia i przesyła wiadomości o spotkaniach do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy spotkania do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Poczta e-mail i automatycznego mapowania użytkowników, jak to opisano w kroku 3. W skrzynkach pocztowych użytkowników jest tworzony nowy podfolder  w folderze Skrzynka odbiorcza o nazwie Powiększ spotkania, a elementy spotkania są importowane do tego folderu. Łącznik robi to przy użyciu wartości właściwości *Email* . Każdy element spotkania zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika spotkania.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [działem obsługi klienta firmy Veritas](https://globanet.com/ms-connectors-contact). Do tego konta zalogujesz się podczas tworzenia łącznika w kroku 1.

- Uzyskaj nazwę użytkownika i hasło do konta funkcji Powiększenie i powiększenie Enterprise Twojej organizacji. Podczas konfigurowania łącznika Powiększ spotkania musisz zalogować się do tego konta w kroku 2.

- Utwórz następujące aplikacje w witrynie [Zoom Marketplace](https://marketplace.zoom.us):

  - Aplikacja OAuth

  - Aplikacja JWT

  Po utworzeniu tych aplikacji platforma Powiększenie generuje zestaw unikatowych poświadczeń używanych do wygenerowania tokenów. Te tokeny są używane do uwierzytelniania łącznika podczas łączenia się z Twoim kontem powiększania i kopiuje elementy do witryny Scal1. Te tokeny będą używać podczas konfigurowania łącznika powiększenia w kroku 2.

  Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji OAuth i JWT, zobacz [Podręcznik użytkownika scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

- Użytkownik, który utworzy łącznik Spotkania z powiększeniem w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-zoom-meetings-connector"></a>Krok 1. Konfigurowanie łącznika Powiększ spotkania

Pierwszym krokiem jest uzyskanie dostępu do łączników **danych** w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika Spotkania powiększenia.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki danychZoom** >  Spotkania.

2. Na stronie **opisowej produktu** Spotkania powiększenia kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-zoom-meetings-connector"></a>Krok 2. Konfigurowanie łącznika Spotkań z powiększeniem

Drugim krokiem jest skonfigurowanie łącznika Spotkania powiększenia w witrynie Scal1. Aby uzyskać więcej informacji na temat konfigurowania łącznika Spotkań z powiększeniem w witrynie Veritas Merge1, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

1. Na stronie **Mapowanie użytkowników zewnętrznych Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników.

   Elementy spotkań powiększenia zawierają właściwość o nazwie Adres *e-mail* , która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia i przejdź do strony Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-zoom-meetings-connector"></a>Krok 4. Monitorowanie łącznika Spotkań z powiększeniem

Po utworzeniu łącznika Spotkania z powiększeniem można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz **łącznik Spotkania powiększenia** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.

- Aby łącznik Powiększenia spotkania działał, należy włączyć nagrania podczas konfigurowania spotkań powiększenia.