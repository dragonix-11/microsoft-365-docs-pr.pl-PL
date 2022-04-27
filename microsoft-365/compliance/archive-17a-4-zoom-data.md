---
title: Konfigurowanie łącznika do archiwizowania danych powiększenia w Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik Zoom DataParser 17a-4 i użyć go do importowania i archiwizowania danych zoomu w Microsoft 365.
ms.openlocfilehash: 89e6a68615e5471568df6a2c7197d75bec3e7982
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090610"
---
# <a name="set-up-a-connector-to-archive-zoom-data"></a>Konfigurowanie łącznika do archiwizowania danych zoomu

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj narzędzia [Zoom DataParser](https://www.17a-4.com/dataparser/) z 17a-4 LLC, aby zaimportować i zarchiwizować dane z platformy Zoom do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Moduł DataParser zawiera łącznik Zoom skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania tych elementów do Microsoft 365. Łącznik Zoom DataParser konwertuje dane zoomu na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po zapisaniu danych zoomu w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Zoom może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-zoom-data"></a>Omówienie archiwizacji danych powiększenia

W poniższym omówieniu wyjaśniono proces używania łącznika danych do archiwizowania danych zoomu w Microsoft 365.

![Przepływ pracy archiwizacji danych zoomu z zakresu 17a-4.](../media/ZoomDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania narzędzia Zoom DataParser.

2. Regularnie elementy powiększenia są zbierane przez program DataParser. Usługa DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik Zoom DataParser utworzony w portalu zgodności usługi Microsoft Purview łączy się z aplikacją DataParser i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Podfolder w folderze Skrzynka odbiorcza o nazwie **Zoom DataParser** jest tworzony w skrzynkach pocztowych użytkownika, a elementy powiększenia są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element zoomu zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto DataParser dla łączników firmy Microsoft. W tym celu skontaktuj się z [17a-4 LLC](https://www.17a-4.com/contact/). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik Zoom DataParser w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-a-zoom-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika Zoom DataParser

Pierwszym krokiem jest dostęp do strony Łączniki danych w portalu zgodności i utworzenie łącznika 17a-4 dla danych zoomu.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  **danychZoom DataParser**.

2. Na stronie Opis produktu **Zoom DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki opisane w kreatorze połączenia Zoom DataParser.

## <a name="step-2-configure-the-zoom-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika Zoom DataParser

Współpracuj z obsługą wersji 17a-4, aby skonfigurować łącznik Zoom DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik Zoom DataParser automatycznie mapuje użytkowników na adresy e-mail Microsoft 365 przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-zoom-dataparser-connector"></a>Krok 4. Monitorowanie łącznika Zoom DataParser

Po utworzeniu łącznika Zoom DataParser możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz utworzony łącznik Zoom DataParser, aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
