---
title: Konfigurowanie łącznika do archiwizowania danych spotkania zoomu na platformie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych ze spotkań Veritas Zoom na platformie Microsoft 365. Dzięki temu można archiwizować dane ze źródeł danych innych firm w usłudze Microsoft 365, aby można było zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizowanie prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 3a2d63071ba29baa40c8d7a656e7e7437f9348bd
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631364"
---
# <a name="set-up-a-connector-to-archive-zoom-meetings-data"></a>Konfigurowanie łącznika do archiwizowania danych spotkania zoomu

Użyj łącznika Veritas w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane ze spotkań zoomu do skrzynek pocztowych użytkowników w organizacji platformy Microsoft 365. Usługa Veritas udostępnia łącznik [Spotkania zoomu](https://globanet.com/zoom/) , który jest skonfigurowany do przechwytywania elementów ze źródła danych innych firm (regularnie) i importowania tych elementów na platformę Microsoft 365. Łącznik konwertuje zawartość spotkań (w tym czaty, zarejestrowane pliki i metadane) z konta Spotkania zoomu na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników na platformie Microsoft 365.

Po zapisaniu danych spotkań zoomu w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych na platformie Microsoft 365 przy użyciu łącznika Zoom Meetings może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-zoom-meetings-data"></a>Omówienie archiwizacji danych spotkań zoomu

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych spotkania zoomu na platformie Microsoft 365.

![Powiększenie przepływu pracy archiwizacji spotkań.](../media/ZoomMeetingsConnectorWorkflow.png)

1. Twoja organizacja współpracuje ze spotkaniami zoomu w celu skonfigurowania i skonfigurowania witryny Spotkania zoomu.

2. Raz na 24 godziny elementy spotkań ze spotkań zoomu są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również zawartość spotkań na format wiadomości e-mail.

3. Łącznik Spotkania zoomu tworzony w portalu zgodności, codziennie łączy się z usługą Veritas Merge1 i przesyła komunikaty ze spotkania do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy spotkania do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* i automatycznego mapowania użytkownika, zgodnie z opisem w kroku 3. Nowy podfolder w folderze Skrzynka odbiorcza o nazwie **Spotkania powiększenia** jest tworzony w skrzynkach pocztowych użytkownika, a elementy spotkania są importowane do tego folderu. Łącznik wykonuje to przy użyciu wartości właściwości *Poczta e-mail* . Każdy element spotkania zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika spotkania.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [pomocą techniczną veritas](https://globanet.com/ms-connectors-contact). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Uzyskaj nazwę użytkownika i hasło dla konta Zoom Business lub Zoom Enterprise w organizacji. Podczas konfigurowania łącznika Spotkania zoomu musisz zalogować się do tego konta w kroku 2.

- Utwórz następujące aplikacje w witrynie [Zoom Marketplace](https://marketplace.zoom.us):

  - Aplikacja OAuth

  - Aplikacja JWT

  Po utworzeniu tych aplikacji platforma Zoom generuje zestaw unikatowych poświadczeń używanych do generowania tokenów. Te tokeny służą do uwierzytelniania łącznika podczas nawiązywania połączenia z kontem zoomu i kopiowania elementów do witryny Merge1. Te tokeny będą używane podczas konfigurowania łącznika zoomu w kroku 2.

  Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji OAuth i JWT, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf)).

- Użytkownikowi, który utworzy łącznik Spotkania zoomu w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-zoom-meetings-connector"></a>Krok 1. Konfigurowanie łącznika Spotkania zoomu

Pierwszym krokiem jest uzyskanie dostępu do **łączników danych** w portalu zgodności i utworzenie łącznika Spotkania zoomu.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki danych****Powiększ** >  spotkania.

2. Na stronie Opis produktu **Zoom Meetings** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-zoom-meetings-connector"></a>Krok 2. Konfigurowanie łącznika Spotkania zoomu

Drugim krokiem jest skonfigurowanie łącznika Spotkania powiększenia w witrynie Merge1. Aby uzyskać więcej informacji na temat konfigurowania łącznika Zoom Meetings w witrynie Veritas Merge1, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

1. Na stronie **Mapowanie użytkowników zewnętrznych na użytkowników platformy Microsoft 365** włącz automatyczne mapowanie użytkowników.

   Elementy spotkania powiększenia obejmują właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem platformy Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-zoom-meetings-connector"></a>Krok 4. Monitorowanie łącznika Spotkania zoomu

Po utworzeniu łącznika Zoom Meetings możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik **Powiększ spotkania** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.

- Aby łącznik Spotkania zoomu działał, musisz włączyć nagrania podczas konfigurowania spotkań powiększenia.