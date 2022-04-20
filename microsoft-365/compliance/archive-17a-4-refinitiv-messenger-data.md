---
title: Konfigurowanie łącznika do archiwizowania danych programu Refinitiv Eikon Messenger w Microsoft 365
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
description: Dowiedz się, jak zaimportować i zarchiwizować te dane w Microsoft 365 za pomocą łącznika 17a-4 programu Refinitiv Eikon Messenger DataParser.
ms.openlocfilehash: 090d658e5b18f639848a4ce3c2635865207a8833
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940714"
---
# <a name="set-up-a-connector-to-archive-refinitiv-eikon-messenger-data"></a>Konfigurowanie łącznika do archiwizacji danych aplikacji Refinitiv Eikon Messenger

Użyj narzędzia [Refinitiv Eikon Messenger DataParser](https://www.17a-4.com/refinitiv-messenger-dataparser/) z firmy 17a-4 LLC, aby zaimportować i zarchiwizować dane z aplikacji Refinitiv Eikon Messenger do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Program DataParser zawiera łącznik programu Refinitiv Eikon Messenger, który jest skonfigurowany do przechwytywania elementów ze źródła danych innych firm i importowania tych elementów do Microsoft 365. Łącznik DataParser programu Refinitiv Eikon Messenger konwertuje dane programu Refinitiv Eikon Messenger na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po przechowywaniu danych aplikacji Refinitiv Eikon Messenger w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Za pomocą łącznika programu Refinitiv Eikon Messenger do importowania i archiwizowania danych w Microsoft 365 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-refinitiv-eikon-messenger-data"></a>Omówienie archiwizacji danych aplikacji Refinitiv Eikon Messenger

W poniższym omówieniu wyjaśniono proces używania łącznika danych do archiwizowania danych programu Refinitiv Eikon Messenger w Microsoft 365.

![Przepływ pracy archiwizacji danych aplikacji Refinitiv Eikon Messenger z zakresu 17a-4.](../media/RefinitivMessengerDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania aplikacji Refinitiv Eikon Messenger DataParser.

2. Regularnie elementy aplikacji Refinitiv Eikon Messenger są zbierane przez użytkownika DataParser. Usługa DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik DataParser aplikacji Refinitiv Eikon Messenger utworzony w portalu zgodności usługi Microsoft Purview łączy się z usługą DataParser i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Podfolder w folderze Skrzynka odbiorcza o nazwie **Refinitiv Eikon Messenger DataParser** jest tworzony w skrzynkach pocztowych użytkownika, a elementy programu Refinitiv Eikon Messenger są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element aplikacji Refinitiv Eikon Messenger zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto DataParser dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z [17a-4 LLC](https://www.17a-4.com/contact/). Podczas tworzenia łącznika w kroku 1 należy zalogować się na to konto.

- Użytkownik, który utworzy łącznik DataParser aplikacji Refinitiv Eikon Messenger w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych 17a-4 jest dostępny w środowiskach GCC w chmurze Microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne ze standardem FEDRAMP.

## <a name="step-1-set-up-a-refinitiv-eikon-messenger-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika aplikacji Refinitiv Eikon Messenger DataParser

Pierwszym krokiem jest dostęp do strony Łączniki danych w portalu zgodności i utworzenie łącznika 17a-4 dla danych programu Refinitiv Eikon Messenger.

1. Przejdź do obszaru <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  **danychRefinitiv Eikon Messenger DataParser**.

2. Na stronie Opis produktu **Refinitiv Eikon Messenger DataParser** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki opisane w kreatorze połączeń aplikacji Refinitiv Eikon Messenger DataParser.

## <a name="step-2-configure-the-refinitiv-eikon-messenger-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika DataParser aplikacji Refinitiv Eikon Messenger

Współpracuj z pomocą techniczną 17a-4, aby skonfigurować łącznik DataParser aplikacji Refinitiv Eikon Messenger.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik DataParser aplikacji Refinitiv Eikon Messenger automatycznie mapuje użytkowników na ich Microsoft 365 adresy e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-refinitiv-eikon-messenger-dataparser-connector"></a>Krok 4. Monitorowanie łącznika aplikacji Refinitiv Eikon Messenger DataParser

Po utworzeniu łącznika DataParser aplikacji Refinitiv Eikon Messenger możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik DataParser aplikacji Refinitiv Eikon Messenger utworzony w celu wyświetlenia strony wysuwanej zawierającej właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
