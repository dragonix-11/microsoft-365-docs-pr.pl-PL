---
title: Konfigurowanie łącznika do archiwizowania danych Skype dla firm Server na platformie Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik Skype dla firm Server DataParser 17a-4 i używać go do importowania i archiwizowania danych Skype dla firm Server na platformie Microsoft 365.
ms.openlocfilehash: 9b503ea1305e7997d6a66ace0a402a9557d0cc31
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639319"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-server-data"></a>Konfigurowanie łącznika do archiwizowania danych Skype dla firm Server

Użyj programu [Skype Server DataParser](https://www.17a-4.com/skype-server-dataparser/) z pakietu 17a-4 LLC, aby zaimportować i zarchiwizować dane z Skype dla firm Server do skrzynek pocztowych użytkowników w organizacji platformy Microsoft 365. Program DataParser zawiera łącznik Skype dla firm skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania tych elementów do platformy Microsoft 365. Łącznik Skype dla firm Server DataParser konwertuje dane Skype dla firm Server na format wiadomości e-mail, a następnie importuje je do skrzynek pocztowych użytkowników na platformie Microsoft 365.

Po zapisaniu Skype dla firm Server danych w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych na platformie Microsoft 365 przy użyciu łącznika Skype dla firm Server może pomóc organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-skype-for-business-server-data"></a>Omówienie archiwizacji danych Skype dla firm Server

W poniższym omówieniu wyjaśniono proces korzystania z łącznika danych do archiwizowania danych Skype dla firm Server na platformie Microsoft 365.

![Przepływ pracy archiwizacji danych Skype dla firm Server z zakresu 17a-4.](../media/SkypeServerDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania Skype dla firm Server DataParser.

2. Regularnie Skype dla firm Server elementy są zbierane przez program DataParser. Usługa DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik Skype dla firm Server DataParser utworzony w portal zgodności Microsoft Purview łączy się z usługą DataParser i przesyła komunikaty do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Podfolder w folderze Skrzynka odbiorcza o nazwie **Skype dla firm Server DataParser** jest tworzony w skrzynkach pocztowych użytkownika, a elementy Skype dla firm Server są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element Skype dla firm Server zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto DataParser dla łączników firmy Microsoft. W tym celu skontaktuj się z [17a-4 LLC](https://www.17a-4.com/contact/). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownikowi tworzącemu łącznik Skype dla firm Server DataParser w kroku 1 (i ukończeniu go w kroku 3) musi zostać przypisana rola Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w środowiskach GCC w chmurze microsoft 365 us government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-a-skype-for-business-server-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika Skype dla firm Server DataParser

Pierwszym krokiem jest dostęp do strony Łączniki danych w portalu zgodności i utworzenie łącznika 17a-4 dla Skype dla firm Server danych.

1. Przejdź do strony<https://compliance.microsoft.com>, a następnie kliknij pozycję **Łączniki** >  danych **Skype dla firm Server DataParser**.

2. Na **stronie opisu produktu Skype dla firm Server DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki opisane w kreatorze połączeń Skype dla firm Server DataParser.

## <a name="step-2-configure-the-skype-for-business-server-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika Skype dla firm Server DataParser

Skontaktuj się z pomocą techniczną 17a-4, aby skonfigurować łącznik Skype dla firm Server DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik Skype dla firm Server DataParser automatycznie mapuje użytkowników na ich adresy e-mail platformy Microsoft 365 przed zaimportowaniem danych na platformę Microsoft 365.

## <a name="step-4-monitor-the-skype-for-business-server-dataparser-connector"></a>Krok 4. Monitorowanie łącznika Skype dla firm Server DataParser

Po utworzeniu łącznika Skype dla firm Server DataParser możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki**, a następnie wybierz łącznik Skype dla firm Server DataParser utworzony w celu wyświetlenia strony wysuwanej zawierającej właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
