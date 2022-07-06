---
title: Archiwizowanie danych z platformy CellTrust SL2 na platformie Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik danych CellTrust SL2 i użyć go do importowania i archiwizowania danych komunikacji mobilnej.
ms.openlocfilehash: 8c31f349f25702e88a260025ef69475f44f96a0e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624714"
---
# <a name="archive-data-from-celltrust-sl2-to-microsoft-365"></a>Archiwizowanie danych z aplikacji CellTrust SL2 na platformę Microsoft 365

CellTrust SL2 przechwytuje dane komunikacji mobilnej i integruje się z wiodącymi technologiami archiwizacji, aby spełnić wymagania dotyczące elektronicznego odnajdywania dla przepisów takich jak FINRA, HIPAA, FOIA i TCPA. Łącznik danych SL2 importuje elementy komunikacji mobilnej na platformę Microsoft 365. W tym artykule opisano proces integracji protokołu SL2 z platformą Microsoft 365 przy użyciu łącznika danych CellTrust SL2 na potrzeby archiwizacji. Ukończenie tego procesu zakłada, że subskrybowano usługę CellTrust SL2 i znasz architekturę SL2. Aby uzyskać informacje o celltrust SL2, zobacz <https://www.celltrust.com>.

Po zaimportowaniu danych do skrzynek pocztowych użytkowników w usłudze Microsoft 365 można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania platformy Microsoft 365 i zgodność z komunikacją. Importowanie i archiwizowanie danych w usłudze Microsoft 365 przy użyciu łącznika danych CellTrust SL2 może pomóc Twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-with-the-celltrust-sl2-data-connector"></a>Omówienie archiwizacji za pomocą łącznika danych CellTrust SL2

Platforma SL2 usługi CellTrust przechwytuje dane komunikacyjne z wielu źródeł. Źródła danych SL2 to osoby-osoby (P2P) lub Aplikacja-osoba (A2P). Proces opisany w tym artykule dotyczy tylko źródeł danych P2P. Dla wszystkich źródeł danych P2P co najmniej jedna strona we współpracy jest użytkownikiem SL2, który subskrybuje usługę SL2. W poniższym omówieniu wyjaśniono proces używania łącznika danych CellTrust SL2 w usłudze Microsoft 365.

![Przepływ pracy archiwizacji dla usługi CellTrust SL2.](../media/CellTrustSL2ConnectorWorkflow.png)

1. Użytkownicy sl2 wysyłają i odbierają dane do i z usług SL2 na platformie Microsoft Azure.

2. Twoja organizacja ma domenę SL2 w środowisku usługi w chmurze SL2 firmy CellTrust. Domena może mieć co najmniej jedną jednostkę organizacyjną(OU). Usługa SL2 Cloud Service przesyła dane do wysoce bezpiecznego obszaru na platformie Microsoft Azure, dzięki czemu dane nigdy nie opuszczają środowiska platformy Microsoft Azure. W zależności od planu SL2 (Enterprise, SMB lub Government) domena jest hostowana w usłudze Microsoft Azure Global lub Microsoft Azure Government.

3. Po utworzeniu łącznika danych CellTrust SL2 domena i jednostki organizacyjne (niezależnie od planu SL2) rozpocznij wysyłanie danych na platformę Microsoft 365. Źródło danych jest ustrukturyzowane w celu obsługi raportowania opartego na źródłach danych, jednostkach organizacyjnych lub samej domenie. W związku z tym twoja organizacja potrzebuje tylko jednego łącznika do przekazywania wszystkich źródeł danych do platformy Microsoft 365.

4. Łącznik tworzy folder w ramach każdego zamapowanego użytkownika z odpowiednią licencją Office 365 o nazwie **CellTrust SL2**. To mapowanie łączy użytkownika CellTrust SL2 ze skrzynką pocztową Office 365 przy użyciu adresu e-mail. Jeśli identyfikator użytkownika w aplikacji CellTrust SL2 nie jest zgodny w Office 365, dane użytkownika nie zostaną zarchiwizowane.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Sprawdź, czy masz domenę w środowisku usługi w chmurze CellTrust SL2. Aby uzyskać dodatkowe informacje na temat uzyskiwania produkcyjnej lub próbnej domeny SL2, [skontaktuj się z celltrust](https://www.celltrust.com/contact-us/#form).

- Uzyskaj poświadczenia, aby uzyskać dostęp do konta administratora domeny SL2.

- Użytkownik, który tworzy łącznik danych CellTrust SL2 w kroku 1 (i kończy go w kroku 3), musi mieć przypisaną rolę łącznika danych Administracja. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portal zgodności Microsoft Purview. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych CellTrust jest dostępny w środowiskach GCC w chmurze platformy Microsoft 365 dla instytucji rządowych USA. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-create-a-celltrust-sl2-connector"></a>Krok 1. Tworzenie łącznika CellTrust SL2

Pierwszym krokiem jest utworzenie łącznika danych w portalu zgodności.

1. Przejdź do <https://compliance.microsoft.com> obszaru i kliknij pozycję **Łączniki danych** w okienku nawigacji po lewej stronie.

2. Na karcie **Przegląd** kliknij pozycję **Filtruj** i wybierz pozycję **Według celltrust**, a następnie zastosuj filtr.

   ![Skonfiguruj filtr, aby wyświetlić łączniki CellTrust.](../media/DataConnectorsFilter.png)

3. Kliknij **pozycję CellTrust SL2 (wersja zapoznawcza)**.

4. Na stronie Opis produktu **CellTrust SL2 (wersja zapoznawcza)** kliknij pozycję **Dodaj łącznik**.

5. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

6. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**. Wprowadzona nazwa zidentyfikuje łącznik na stronie **Łączniki danych** po jego utworzeniu.

7. Na stronie **Zaloguj się do konta CellTrust** kliknij pozycję **Zaloguj się do aplikacji CellTrust**. Nastąpi przekierowanie do **portalu CellTrust dla platformy Microsoft 365** w nowym oknie przeglądarki.

## <a name="step-2-select-the-domains-or-ous-to-archive"></a>Krok 2. Wybieranie domen lub jednostek organizacyjnych do archiwizacji

Następnym krokiem jest zalogowanie się do konta administratora domeny CellTrust SL2 i wybranie domen i jednostek organizacyjnych do zarchiwizowania na platformie Microsoft 365.

1. Na stronie **Łącznik platformy Microsoft 365** CellTrust wybierz swoje środowisko w usłudze w chmurze SL2, aby wyświetlić stronę logowania.

   Zazwyczaj powinna zostać wyświetlona jedna opcja reprezentująca środowisko. Jeśli jednak masz domeny w więcej niż jednym środowisku, zobaczysz opcje dla każdego środowiska. Po dokonaniu wyboru nastąpi przekierowanie do strony logowania SL2.

2. Zaloguj się przy użyciu poświadczeń konta administratora domeny lub jednostki organizacyjnej.

   Jeśli zalogujesz się jako administrator domeny SL2, zobaczysz nazwę domeny i jednostek organizacyjnych w tej domenie. Jeśli nie masz jednostek organizacyjnych, zobaczysz tylko nazwę domeny. Jeśli zalogujesz się jako administrator jednostki organizacyjnej, zobaczysz tylko nazwę jednostki organizacyjnej.

3. Włącz jednostki biznesowe, które chcesz zarchiwizować. Wybranie domeny nie spowoduje automatycznego wybrania jednostek organizacyjnych. Należy włączyć oddzielnie każdą jednostkę organizacyjną, aby ją zarchiwizować.

   ![Włącz archiwizowanie jednostek organizacyjnych.](../media/EnableCellTrustOUs.png)

4. Po zakończeniu wyboru zamknij okno przeglądarki i wróć do strony kreatora w portalu zgodności. Po kilku sekundach kreator automatycznie przechodzi do następnego kroku mapowania użytkowników.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Ostatnim krokiem jest mapowanie użytkowników i ukończenie konfiguracji łącznika w portalu zgodności.

1. Na stronie **Mapowanie użytkownika** wybierz pozycję **Włącz automatyczne mapowanie użytkowników** , jeśli adres e-mail dla użytkowników jest taki sam zarówno w wersji SL2, jak i Microsoft 365. W przeciwnym razie należy ręcznie przekazać adresy e-mail użytkowników, przekazując plik CSV, który mapuje adres SL2 użytkowników na ich adres microsoft 365.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

   Nowy łącznik zostanie dodany do listy na stronie **Łączniki danych** .

## <a name="get-help-from-celltrust"></a>Uzyskiwanie pomocy z celltrust

Aby uzyskać pomoc dotyczącą konfigurowania łącznika danych CellTrust SL2, zobacz [stronę Pomocy technicznej aplikacji CellTrust](https://www.celltrust.com/contact-us/#support) , aby uzyskać szczegółowe informacje o kontaktowaniu się z usługą CellTrust.

## <a name="more-information"></a>Więcej informacji

- Administrator domeny może skonfigurować łącznik dla domeny lub dowolnych jednostek organizacyjnych w tej domenie. Jeśli używasz konta administratora jednostki organizacyjnej, możesz skonfigurować łącznik tylko dla tej konkretnej jednostki organizacyjnej.

- Aby pomyślnie wykonać powyższe kroki, musisz mieć przypisaną licencję Microsoft 365 E5 i mieć odpowiednie prawa administratora pakietu Microsoft Office.

- Aby przetestować nowy łącznik, wyślij wiadomość SMS przy użyciu aplikacji mobilnej SL2 lub portalu SL2. Przejdź do skrzynki pocztowej platformy Microsoft 365 i otwórz folder **CellTrust SL2** w skrzynce odbiorczej. Wyświetlenie wiadomości SMS w skrzynce pocztowej może potrwać kilka minut.

- Wiele przepisów ustawowych i wykonawczych wymaga zachowania komunikacji elektronicznej w taki sposób, że na żądanie można ją przedstawić jako dowód. Elektroniczne wykrywanie (elektroniczne wykrywanie elektroniczne) służy do zapewnienia zgodności z produkcją komunikacji elektronicznej. Rozwiązania do archiwizacji informacji przedsiębiorstwa (EIA) zostały zaprojektowane tak, aby wykonywać zbieranie elektronicznych materiałów dowodowych i udostępniać funkcje, takie jak zarządzanie zasadami przechowywania, klasyfikacja danych i nadzór nad zawartością. Platforma Microsoft 365 oferuje rozwiązanie do przechowywania długoterminowego w celu zapewnienia zgodności z przepisami i standardami, które mają wpływ na organizację.

- Termin *archiwizowanie* używany w tym dokumencie odnosi się do archiwizacji w kontekście użycia w rozwiązaniu archiwizacji informacji przedsiębiorstwa (EIA). Rozwiązania eia mają funkcje zbierania elektronicznych materiałów dowodowych, które tworzą dokumenty dotyczące postępowań sądowych, sporów sądowych, audytów i dochodzeń. Archiwizowanie w kontekście kopii zapasowej i przywracania używanej do odzyskiwania po awarii i ciągłości działania nie jest zamierzonym użyciem terminu w tym dokumencie.
