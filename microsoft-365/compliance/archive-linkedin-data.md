---
title: Konfigurowanie łącznika do archiwizowania danych z usługi LinkedIn
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak administratorzy mogą & za pomocą natywnego łącznika importować dane ze strony firmy serwisu LinkedIn w celu Microsoft 365.
ms.openlocfilehash: 70d17c0cf9eaeec7110ea178f1f3db56c3d3b553
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973678"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Konfigurowanie łącznika do archiwizowania danych z usługi LinkedIn

Za pomocą łącznika w Centrum zgodności platformy Microsoft 365 importować i archiwizować dane ze stron Firmy LinkedIn. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z kontem konkretnej strony Firmy LinkedIn co 24 godziny. Łącznik konwertuje wiadomości opublikowane na stronie Firma na wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej w u Microsoft 365.

Po zapisaniu danych strony LinkedIn Company w skrzynce pocztowej możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym, wyszukiwanie zawartości, In-Place archiwizowanie, inspekcja i zasady przechowywania Microsoft 365 do danych usługi LinkedIn. Można na przykład wyszukać te elementy za pomocą wyszukiwania zawartości lub skojarzyć skrzynkę pocztową magazynu ze współpracownikiem w Advanced eDiscovery przypadku. Utworzenie łącznika do importowania i archiwizowania danych z usługi LinkedIn Microsoft 365 organizacji zgodnie z zasadami rządowymi i przepisami regulowymi.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Użytkownik, który tworzy łącznik strony firmy w serwisie LinkedIn, musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Jest to wymagane do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w Exchange Online".

- Musisz mieć poświadczenia logowania (adres e-mail lub numer telefonu i hasło) konta użytkownika w serwisie LinkedIn, które jest administratorem strony firmy LinkedIn, którą chcesz zarchiwizować. Poświadczenia te są używane do logowania się do usługi LinkedIn podczas konfigurowania łącznika.

- Łącznik usługi LinkedIn może importować łącznie 200 000 elementów w jednym dniu. Jeśli dziennie istnieje więcej niż 200 000 elementów z usługi LinkedIn, żaden z tych elementów nie zostanie zaimportowany do Microsoft 365.

## <a name="create-a-linkedin-connector"></a>Tworzenie łącznika usługi LinkedIn

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki** **danychLinkedW** >  stronach firmy.

2. Na stronie **produktu w serwisie LinkedIn** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** wybierz pozycję **Zaakceptuj**.

4. Na stronie **Zaloguj się za pomocą usługi LinkedIn** kliknij pozycję **Zaloguj się za pomocą usługi LinkedIn**.

   Zostanie wyświetlona strona logowania do usługi LinkedIn.

   ![Stronie logowania do usługi LinkedIn.](../media/LinkedInSigninPage.png)

5. Na stronie logowania do usługi LinkedIn wprowadź adres e-mail (lub numer telefonu) i hasło dla konta w serwisie LinkedIn skojarzonego ze stroną firmy, którą chcesz zarchiwizować, a następnie kliknij pozycję **Zaloguj się.**

   Zostanie wyświetlona strona kreatora z listą wszystkich stron firmowych w serwisie LinkedIn skojarzonych z kontem, do których się zalogowano. Łącznik można skonfigurować tylko dla jednej strony firmowej. Jeśli Twoja organizacja ma wiele stron firmowych w serwisie LinkedIn, musisz utworzyć łącznik dla każdej z nich.

   ![Zostanie wyświetlona strona z listą stron firmy w serwisie LinkedIn.](../media/LinkedInSelectCompanyPage.png)

6. Wybierz stronę firmy, z której chcesz zarchiwizować elementy, a następnie kliknij przycisk **Dalej**.

7. Na **stronie Wybierz lokalizację** przechowywania kliknij w polu, wybierz adres e-mail skrzynki pocztowej usługi Microsoft 365, do których będą importowane elementy z usługi LinkedIn, a następnie kliknij przycisk **Dalej**. Elementy są importowane do folderu skrzynki odbiorczej w tej skrzynce pocztowej.

8. Kliknij **przycisk Dalej** , aby przejrzeć ustawienia łącznika, a następnie kliknij przycisk **Zakończ,** aby zakończyć konfigurację łącznika.

Po utworzeniu łącznika możesz wrócić na stronę Łączniki danych, aby zobaczyć postęp procesu importowania nowego łącznika (w razie potrzeby wybierz pozycję Odśwież, aby zaktualizować listę łączników). Wartość w kolumnie **Stan** to **Oczekiwanie na rozpoczęcie**. Aby rozpocząć początkowy proces importowania, może upłynie do 24 godzin. Po pierwszym uruchomieniu łącznika i zaimportowaniu elementów z usługi LinkedIn łącznik będzie uruchamiany raz na 24 godziny i zaimportować wszystkie nowe elementy utworzone na stronie firmy LinkedIn w ciągu poprzednich 24 godzin.

Aby wyświetlić więcej szczegółów, zaznacz łącznik na liście na stronie **Łączniki** danych w celu wyświetlenia strony wysuwu. W **obszarze** Stan wyświetlany zakres dat wskazuje filtr wieku wybrany podczas tworzenia łącznika.

## <a name="more-information"></a>Więcej informacji

Elementy z usługi LinkedIn są importowane do podfolderu usługi LinkedIn w skrzynce odbiorczej skrzynki pocztowej magazynu w Microsoft 365. Są one wyświetlane jako wiadomości e-mail.