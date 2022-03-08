---
title: Archiwizowanie danych z platformy CellTrust SL2 w celu Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik danych CellTrust SL2 i używać go do importowania i archiwizowania danych komunikacji na urządzeniach przenośnych.
ms.openlocfilehash: 420da07fcb878f047d8252b713360be122c85870
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324301"
---
# <a name="archive-data-from-celltrust-sl2-to-microsoft-365"></a>Archiwizowanie danych z telefonu CellTrust SL2 do Microsoft 365

Komórka CellTrust SL2 rejestruje dane komunikacji na urządzeniach przenośnych i integruje się z wiodącymi technologiami archiwizacji, aby spełnić wymagania dotyczące elektronicznego odnajdowania przepisów takich jak FINRA, HIPAA, FOIA i TCPA. Łącznik danych SL2 importuje elementy komunikacji mobilnej do programu Microsoft 365. W tym artykule opisano proces integrowania oprogramowania SL2 z programem Microsoft 365 przy użyciu łącznika danych CellTrust SL2 do archiwizacji. W trakcie tego procesu przyjęto założenie, że subskrybujesz usługę CellTrust SL2 i znasz architekturę SL2. Aby uzyskać informacje na temat telefonu CellTrust SL2, zobacz <https://www.celltrust.com>.

Po zaimportowaniu danych do skrzynek pocztowych użytkowników w programie Microsoft 365 możesz stosować funkcje zgodności, takie jak Zastosowanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania Microsoft 365 Microsoft 365 i zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika danych CellTrust SL2 może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami.

## <a name="overview-of-archiving-with-the-celltrust-sl2-data-connector"></a>Omówienie archiwizowania za pomocą łącznika danych SL2 CellTrust

Platforma SL2 firmy CellTrust rejestruje dane komunikacji z wielu źródeł. Źródła danych SL2 to zarówno od osoby do osoby (P2P), jak i Application-to-Person (A2P). Proces opisany w tym artykule dotyczy tylko źródeł danych P2P. W przypadku wszystkich źródeł danych P2P co najmniej jedna strona współpracy to użytkownik SL2 z subskrypcją usługi SL2. Poniższe omówienie przedstawia proces używania łącznika danych CellTrust SL2 w programie Microsoft 365.

![Przepływ pracy archiwizacji dla usługi CellTrust SL2.](../media/CellTrustSL2ConnectorWorkflow.png)

1. Użytkownicy SL2 wysyłają i odbierają dane do i z usług SL2 w Microsoft Azure.

2. Twoja organizacja ma domenę SL2 w środowisku usługi w chmurze SL2 firmy CellTrust. Twoja domena może zawierać jedną lub więcej jednostek organizacyjnych. Usługa sl2 w chmurze przesyła dane do wysoce bezpiecznego obszaru na Microsoft Azure, dzięki czemu dane nigdy nie opuszczają Microsoft Azure. W zależności od planu sl2 (usługi Enterprise, SMB lub dla instytucji rządowych) Twoja domena jest hostowana na Microsoft Azure Global lub Microsoft Azure Government.

3. Po utworzeniu łącznika danych SL2 CellTrust, domeny i użytkowników operacyjnych (niezależnie od planu SL2) zacznij wysyłać dane do Microsoft 365. Źródło danych ma strukturę, która obsługuje raportowanie oparte na źródłach danych, nazwach OU lub samej domenie. W efekcie organizacja potrzebuje tylko jednego łącznika do podawania wszystkich źródeł danych do Microsoft 365.

4. Łącznik tworzy folder pod każdym zamapowany użytkownikiem z odpowiednią licencją Office 365 **CellTrust SL2**. To mapowanie łączy użytkownika funkcji CellTrust SL2 z Office 365 poczty e-mail przy użyciu adresu e-mail. Jeśli identyfikator użytkownika w aplikacji CellTrust SL2 nie ma dopasowania w Office 365, dane użytkownika nie zostaną zarchiwizowane.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Sprawdź, czy masz domenę w środowisku usługi w chmurze CellTrust SL2. Aby uzyskać dodatkowe informacje na temat uzyskiwania domeny SL2 produkcyjnej lub próbnej, [skontaktuj się z cellTrust](https://www.celltrust.com/contact-us/#form).

- Uzyskaj poświadczenia, aby uzyskać dostęp do konta administratora dla domeny SL2.

- Użytkownik, który tworzy łącznik danych Funkcji CellTrust SL2 w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych CellTrust jest dostępny w GCC środowiskach chmury dla instytucji rządowych Microsoft 365 Usa. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-create-a-celltrust-sl2-connector"></a>Krok 1. Tworzenie łącznika CellTrust SL2

Pierwszym krokiem jest utworzenie łącznika danych w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com> danych w lewym okienku **nawigacji i** kliknij je.

2. Na karcie **Omówienie** kliknij pozycję Filtr **i wybierz pozycję** **By CellTrust**, a następnie zastosuj filtr.

   ![Konfigurowanie filtru w celu wyświetlania łączników cellTrust.](../media/DataConnectorsFilter.png)

3. Kliknij **pozycję CellTrust SL2 (wersja zapoznawcza).**

4. Na stronie **Opis produktu CellTrust SL2 (wersja zapoznawcza)** kliknij pozycję **Dodaj łącznik**.

5. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

6. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**. W wprowadzeniu nazwy łącznika będzie on identyfikowany na **stronie Łączniki** danych po jego utworzeniu.

7. Na stronie **Sign in to your CellTrust account** (Logowanie do konta cellTrust) kliknij pozycję **Sign into CellTrust (Zaloguj się do telefonu CellTrust**). Nastąpi przekierowanie do portalu **CellTrust Portal for Microsoft 365** w nowym oknie przeglądarki.

## <a name="step-2-select-the-domains-or-ous-to-archive"></a>Krok 2. Wybieranie domen lub użytkowników operacyjnych do zarchiwizowania

Następnym krokiem jest zalogowanie się do konta administratora domeny CellTrust SL2 i wybranie domen i użytkowników operacyjnych do zarchiwizowania w Microsoft 365.

1. Na stronie CellTrust **Microsoft 365 Connector** wybierz środowisko w usłudze w chmurze SL2, aby wyświetlić stronę logowania.

   Zazwyczaj powinna być jedna opcja reprezentująca środowisko. Jeśli jednak masz domeny w więcej niż jednym środowisku, zostaną wyświetlonych opcje dla każdego środowiska. Po zaznaczeniu, nastąpi przekierowanie do strony logowania SL2.

2. Zaloguj się przy użyciu poświadczeń konta administratora domeny lub organizacji administracyjnej.

   Jeśli zalogujesz się jako administrator domeny SL2, zobaczysz nazwę twojej domeny i użytkowników o nazwie Twojej w tej domenie. Jeśli nie masz użytkowników o nazwie OUs, zobaczysz tylko nazwę domeny. Jeśli zalogujesz się jako administrator organizacji OU, będzie dla Ciebie dostępna tylko nazwa Twojej organizacji.

3. Włącz jednostki biznesowe, które chcesz zarchiwizować. Wybranie domeny nie spowoduje automatycznego wybrania użytkowników o typie danych. Każdą publikację należy włączyć oddzielnie, aby ją zarchiwizować.

   ![Włączanie zarchiwizować w przypadku innych producentów.](../media/EnableCellTrustOUs.png)

4. Po zakończeniu zaznaczania zamknij okno przeglądarki i wróć do strony kreatora w programie Centrum zgodności platformy Microsoft 365. Po upływie kilku sekund kreator automatycznie przejść do następnego kroku mapowania użytkowników.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Ostatnim krokiem jest zamapowanie użytkowników i ukończenie konfiguracji łącznika w Centrum zgodności platformy Microsoft 365.

1. Na stronie **Mapowanie użytkowników** wybierz pozycję Włącz **automatyczne** mapowanie użytkowników, jeśli adres e-mail użytkowników jest taki sam zarówno w sl2, jak i w Microsoft 365. W przeciwnym razie należy ręcznie wysłać adresy e-mail użytkowników, przesyłając plik CSV mapując adres SL2 użytkowników na Microsoft 365 adres.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ,** aby utworzyć łącznik.

   Nowy łącznik zostanie dodany do listy na stronie **Łączniki** danych.

## <a name="get-help-from-celltrust"></a>Uzyskiwanie pomocy od firmy CellTrust

Aby uzyskać [pomoc w konfigurowaniu](https://www.celltrust.com/contact-us/#support) łącznika danych CellTrust SL2, zobacz stronę obsługi klienta CellTrust, aby uzyskać szczegółowe informacje na temat kontaktowania się z usługą CellTrust.

## <a name="more-information"></a>Więcej informacji

- Administrator domeny może skonfigurować łącznik dla domeny lub dowolnej nazwy użytkownika w tej domenie. Jeśli korzystasz z konta administratora organizacji administracyjnej, możesz skonfigurować łącznik tylko dla tej konkretnej organizacji administracyjnej.

- Aby pomyślnie wykonać powyższe czynności, musisz mieć przypisaną licencję usługi Microsoft 365 E5 i mieć odpowiednie uprawnienia Microsoft Office administratora.

- Aby przetestować nowy łącznik, wyślij wiadomość SMS przy użyciu aplikacji mobilnej SL2 lub portalu SL2. Przejdź do swojej skrzynki Microsoft 365 i otwórz folder **CellTrust SL2** w skrzynce odbiorczej. Może upłynieć kilka minut, aż wiadomości SMS będą wyświetlane w skrzynce pocztowej.

- Wiele ustaw i przepisów wymaga zachowywania komunikacji elektronicznej w taki sposób, aby na żądanie można było to zrobić jako dowód. Funkcja zbierania elektronicznych materiałów dowodowych jest używana w celu zapewnienia zgodności z produkcją komunikacji elektronicznej. Enterprise rozwiązań do archiwizacji informacji (EIA) zaprojektowano do zbierania elektronicznych materiałów dowodowych i zapewniają funkcje, takie jak zarządzanie zasadami przechowywania, klasyfikacja danych i nadzór nad zawartością. Microsoft 365 oferuje długoterminowe rozwiązanie przechowywania w celu zapewnienia zgodności z przepisami i standardami, które wpływają na Twoją organizację.

- Archiwizacja *terminów* używana w tym dokumencie odnosi się do archiwizacji w kontekście użytkowania w ramach rozwiązania do archiwizacji Enterprise informacji (EIA). Rozwiązania EIA mają funkcje zbierania elektronicznych materiałów dowodowych, które twórzą dokumenty na postępowania prawne, procesy, inspekcje i dochodzenia. Archiwizowanie w kontekście tworzenia kopii zapasowej i przywracania używanego do odzyskiwania po awarii i ciągłości działania nie jest zamierzony termin w tym dokumencie.
