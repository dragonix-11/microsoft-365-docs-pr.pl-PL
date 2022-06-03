---
title: Tworzenie zasad zabezpieczeń urządzeń w usłudze Basic Mobility and Security
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- MET150
description: Użyj usługi Basic Mobility and Security, aby utworzyć zasady urządzeń, które chronią informacje o organizacji.
ms.openlocfilehash: f6cbcd72f5e5cae93b7fa775d7bce6f2906f454e
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863243"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>Tworzenie zasad zabezpieczeń urządzeń w usłudze Basic Mobility and Security

Usługi Basic Mobility and Security można używać do tworzenia zasad urządzeń, które ułatwiają ochronę informacji organizacji dotyczących Microsoft 365 przed nieautoryzowanym dostępem. Zasady można stosować do dowolnego urządzenia przenośnego w organizacji, na którym użytkownik urządzenia ma odpowiednią licencję Microsoft 365 i zarejestrował urządzenie w usłudze Basic Mobility and Security.

## <a name="before-you-begin"></a>Przed rozpoczęciem

> [!IMPORTANT]
> Przed utworzeniem zasad dotyczących urządzeń przenośnych należy aktywować i skonfigurować usługę Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz Omówienie pakietu Basic Mobility and Security.

- Dowiedz się więcej o urządzeniach, aplikacjach urządzeń przenośnych i ustawieniach zabezpieczeń obsługiwanych przez usługę Basic Mobility and Security. Zobacz [Możliwości usługi Basic Mobility and Security](capabilities.md).
- Utwórz grupy zabezpieczeń, które obejmują Microsoft 365 użytkowników, dla których chcesz wdrożyć zasady, i dla użytkowników, których można wykluczyć z blokowania dostępu do Microsoft 365. Zalecamy, aby przed wdrożeniem nowych zasad w organizacji przetestować zasady, wdrażając je dla niewielkiej liczby użytkowników. Możesz utworzyć i użyć grupy zabezpieczeń obejmującej tylko siebie lub niewielką liczbę użytkowników Microsoft 365, którzy mogą przetestować zasady. Aby dowiedzieć się więcej o grupach zabezpieczeń, zobacz [Tworzenie, edytowanie lub usuwanie grupy zabezpieczeń](../email/create-edit-or-delete-a-security-group.md).
- Aby tworzyć i wdrażać zasady podstawowej mobilności i zabezpieczeń w Microsoft 365, musisz być administratorem globalnym Microsoft 365. Aby uzyskać więcej informacji, zobacz [Uprawnienia w Centrum zgodności & zabezpieczeń](../../security/office-365-security/permissions-in-the-security-and-compliance-center.md).
- Przed wdrożeniem zasad poinformuj organizację o potencjalnych skutkach rejestracji urządzenia w usłudze Basic Mobility and Security. W zależności od sposobu konfigurowania zasad niezgodnym urządzeniom można zablokować dostęp do Microsoft 365 i danych, w tym zainstalowanych aplikacji, zdjęć i danych osobowych na zarejestrowanym urządzeniu, a dane mogą zostać usunięte.

> [!NOTE]
> Zasady i reguły dostępu utworzone w usłudze Basic Mobility and Security dla Microsoft 365 Business Standard przesłaniają zasady Exchange ActiveSync skrzynki pocztowej urządzeń przenośnych i reguły dostępu urządzeń utworzonych w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym Exchange</a>. Po zarejestrowaniu urządzenia w usłudze Basic Mobility and Security for Microsoft 365 Business Standard wszystkie Exchange ActiveSync zasad skrzynki pocztowej urządzeń przenośnych lub reguły dostępu urządzeń stosowanych do urządzenia są ignorowane. Aby dowiedzieć się więcej na temat Exchange ActiveSync, zobacz [Exchange ActiveSync w Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>Krok 1. Tworzenie zasad urządzenia i wdrażanie w grupie testowej

Przed rozpoczęciem upewnij się, że aktywowano i skonfigurowano pakiet Basic Mobility and Security. Aby uzyskać instrukcje, zobacz [Omówienie pakietu Basic Mobility and Security](overview.md).

1. W przeglądarce wpisz .<https://compliance.microsoft.com/basicmobilityandsecurity>

2. Wybierz **pozycję Utwórz zasady**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Ustawienia zasad podstawowej mobilności i zabezpieczeń.":::

3. Na stronie **Ustawienia zasad** określ wymagania, które mają być stosowane do urządzeń przenośnych w organizacji.

4. **Wymagaj zarządzania profilem poczty e-mail**: po włączeniu urządzenia, które nie mają profilu poczty e-mail zarządzanego przez usługi Basic Mobility and Security, są uważane za niezgodne. Urządzenie nie może mieć zarządzanego profilu poczty e-mail, jeśli nie jest prawidłowo ukierunkowane lub jeśli użytkownik ręcznie skonfiguruje konto e-mail na urządzeniu. Po pozostawieniu opcji **Nie włączono** (ustawienie domyślne) to ustawienie nie jest oceniane pod kątem zgodności lub niezgodności. Aby uzyskać instrukcje dotyczące sposobu, w jaki użytkownicy mogą uzyskać zgodność po wybraniu tej opcji, zobacz [Znajdowanie istniejącego konta e-mail](/intune-user-help/existing-company-email-account-found).

5. Na stronie **Czy chcesz teraz zastosować te zasady?** wybierz grupy, do których chcesz zastosować te zasady.

6. Wybierz pozycję **Utwórz te zasady**.

Zasady są wypychane do urządzenia każdego użytkownika, do których zasady mają zastosowanie przy następnym zalogowaniu się do Microsoft 365 przy użyciu urządzenia przenośnego. Jeśli użytkownicy nie mieli wcześniej zasad stosowanych do urządzenia przenośnego, po wdrożeniu zasad otrzymają na swoim urządzeniu powiadomienie zawierające kroki rejestrowania i aktywowania pakietu Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego przy użyciu pakietu Basic Mobility and Security](enroll-your-mobile-device.md). Do momentu ukończenia rejestracji w usłudze Basic Mobility and Security hostowanej przez usługę Intune dostęp do poczty e-mail, OneDrive i innych usług jest ograniczony. Po zakończeniu rejestracji przy użyciu aplikacji Intune — Portal firmy mogą korzystać z usług, a zasady są stosowane do urządzenia.

## <a name="step-2-verify-that-your-policy-works"></a>Krok 2. Sprawdzanie, czy zasady działają

Po utworzeniu zasad urządzenia sprawdź, czy zasady działają zgodnie z oczekiwaniami przed wdrożeniem ich w organizacji.

1. W przeglądarce wpisz .[https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity)
2. Wybierz **pozycję Wyświetl listę urządzeń zarządzanych**.
3. Sprawdź stan urządzeń użytkowników, na których zastosowano zasady. Chcesz, aby **stan** urządzeń był **zarządzany.**
4. Możesz również przeprowadzić pełne lub selektywne czyszczenie na urządzeniu, klikając pozycję **Resetowanie do ustawień fabrycznych** lub **Usuń dane firmowe** z przycisku **Zarządzaj** po wybraniu urządzenia. Aby uzyskać instrukcje, zobacz [Czyszczenie urządzenia przenośnego w Microsoft 365.

## <a name="step-3-deploy-a-policy-to-your-organization"></a>Krok 3. Wdrażanie zasad w organizacji

Po utworzeniu zasad urządzenia i upewnieniu się, że działają zgodnie z oczekiwaniami, wdróż je w organizacji.

1. Z poziomu typu przeglądarki: [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Wybierz zasady, które chcesz wdrożyć, a następnie wybierz pozycję **Edytuj** obok **pozycji Grupy zastosowane do.**
3. Wyszukaj grupę do dodania i kliknij pozycję **Wybierz**.
4. Wybierz pozycję **Zamknij** i **zmień ustawienie.**
5. Wybierz pozycję **Zamknij** i **Edytuj zasady.**

Zasady są wypychane do urządzenia przenośnego każdego użytkownika, do których zasady mają zastosowanie przy następnym zalogowaniu się do Microsoft 365 z urządzenia przenośnego. Jeśli użytkownicy nie zastosowali zasad do swojego urządzenia przenośnego, otrzymają powiadomienie na swoim urządzeniu z instrukcjami dotyczącymi rejestrowania i aktywowania ich dla pakietu Basic Mobility and Security. Po zakończeniu rejestracji zasady są stosowane do urządzenia. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego przy użyciu pakietu Basic Mobility and Security](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>Krok 4. Blokowanie dostępu do poczty e-mail dla nieobsługiwanych urządzeń

Aby pomóc w zabezpieczeniu informacji o organizacji, należy zablokować dostęp aplikacji do Microsoft 365 poczty e-mail dla urządzeń przenośnych, które nie są obsługiwane przez usługi Basic Mobility and Security. Aby uzyskać listę obsługiwanych urządzeń, zobacz [Obsługiwane urządzenia](../../admin/basic-mobility-security/capabilities.md).

**Aby zablokować dostęp do aplikacji:**

1. W przeglądarce wpisz .[https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity)
2. Wybierz pozycję **Zarządzaj ustawieniami dostępu do urządzeń w całej organizacji**.
3. Aby zablokować nieobsługiwane urządzenia, wybierz pozycję **Dostęp** w obszarze **Jeśli urządzenie nie jest obsługiwane przez usługę Basic Mobility and Security dla Microsoft 365**, a następnie wybierz pozycję **Zapisz**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-access.png" alt-text="Opcja podstawowej mobilności i zabezpieczeń blokuje dostęp.":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>Krok 5. Wybieranie grup zabezpieczeń, które mają zostać wykluczone z kontroli dostępu warunkowego

Jeśli chcesz wykluczyć niektóre osoby z kontroli dostępu warunkowego na swoich urządzeniach przenośnych i utworzono co najmniej jedną grupę zabezpieczeń dla tych osób, dodaj grupy zabezpieczeń tutaj. Osoby w tych grupach nie będą miały żadnych zasad wymuszanych dla obsługiwanych urządzeń przenośnych. Jest to zalecana opcja, jeśli nie chcesz już używać pakietu Basic Mobility and Security w organizacji.

1. W przeglądarce wpisz .[https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity)

2. Wybierz pozycję **Zarządzaj ustawieniami dostępu do urządzeń w całej organizacji**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Usługa Basic Mobility and Security umożliwia utworzenie opcji zasad.":::

3. Wybierz pozycję **Dodaj**, aby dodać grupę zabezpieczeń zawierającą użytkowników, których chcesz wykluczyć z blokowania dostępu do Microsoft 365. Po dodaniu użytkownika do tej listy może uzyskać dostęp do Microsoft 365 wiadomości e-mail, gdy korzysta z nieobsługiwanego urządzenia.

4. Wybierz grupę zabezpieczeń, która ma być używana w panelu **Wybierz grupę** .

5. Wybierz nazwę, a następnie **dodaj pozycję** > **Zapisz**.

6. Na panelu **Ustawienia dostępu do urządzeń w całej organizacji** wybierz pozycję **Zapisz**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-groups.png" alt-text="Opcja Podstawowa mobilność i zabezpieczenia zezwala na dostęp.":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>Jaki jest wpływ zasad zabezpieczeń na różne typy urządzeń?

Po zastosowaniu zasad do urządzeń użytkowników wpływ na każde urządzenie różni się nieco w zależności od typu urządzeń. W poniższej tabeli przedstawiono przykłady wpływu zasad na różne urządzenia.

|**Zasady zabezpieczeń**|**Android**|**Samsung KNOX**|**iOS**|**Uwagi**|
|:-----|:-----|:-----|:-----|:-----|
|Wymagaj zaszyfrowanej kopii zapasowej|Nie|Tak|Tak|iOS wymagana kopia zapasowa zaszyfrowana.|
|Blokuj tworzenie kopii zapasowych w chmurze|Tak|Tak|Tak|Blokuj tworzenie kopii zapasowej Google na Android (wyszarzone), kopia zapasowa w chmurze na iOS.|
|Blokuj synchronizację dokumentów|Nie|Nie|Tak|iOS: blokuj dokumenty w chmurze.|
|Blokuj synchronizację zdjęć |Nie|Nie|Tak|iOS (natywny): Blokuj strumień zdjęć.|
|Blokuj przechwytywanie ekranu |Nie|Tak|Tak|Zablokowane podczas próby.|
|Blokuj konferencję wideo |Nie|Nie|Tak|Funkcja FaceTime została zablokowana na iOS, a nie na Skype lub innych.|
|Blokuj wysyłanie danych diagnostycznych |Nie|Tak|Tak|Blokuj wysyłanie raportu o awarii google na Android.|
|Blokowanie dostępu do sklepu z aplikacjami |Nie|Tak|Tak|Brak ikony sklepu z aplikacjami na stronie głównej Android, wyłączona w Windows, brakuje jej na iOS.|
|Wymagaj hasła dla sklepu z aplikacjami |Nie|Nie|Tak|iOS: hasło wymagane do zakupów w programie iTunes.|
|Blokuj połączenie z magazynem wymiennym |Nie|Tak|nd.|Android: karta SD jest wyszarzona w ustawieniach, Windows powiadamia użytkownika, zainstalowane aplikacje nie są dostępne|
|Blokuj połączenie Bluetooth |Zobacz notatki|Zobacz notatki|Tak|Nie można wyłączyć funkcji BlueTooth jako ustawienia na Android. Zamiast tego wyłączamy wszystkie transakcje, które wymagają funkcji BlueTooth: zaawansowana dystrybucja dźwięku, zdalne sterowanie audio/wideo, urządzenia bez użycia rąk, zestaw słuchawkowy, dostęp do książki Telefon i port szeregowy. W dolnej części strony zostanie wyświetlony mały wyskakujące komunikat, gdy zostanie użyty dowolny z nich.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>Co się stanie po usunięciu zasad lub usunięciu użytkownika z zasad?

Gdy usuniesz zasady lub usuniesz użytkownika z grupy, do której zostały wdrożone zasady, ustawienia zasad, Microsoft 365 profil poczty e-mail i buforowane wiadomości e-mail, mogą zostać usunięte z urządzenia użytkownika. Zobacz poniższą tabelę, aby zobaczyć, co zostało usunięte dla różnych typów urządzeń.

|**Co zostało usunięte**|**iOS**|**Android (w tym Samsung KNOX**|
|:-----|:-----|:-----|
|Zarządzane profile poczty e-mail<sup>1</sup>|Tak|Nie|
|Blokuj tworzenie kopii zapasowych w chmurze|Tak|Nie|

<sup>1</sup> Jeśli zasady zostały wdrożone z wybraną opcją **Profil poczty e-mail jest zarządzany** , zarządzany profil poczty e-mail i buforowane wiadomości e-mail w tym profilu zostaną usunięte z urządzenia użytkownika.

Zasady są usuwane z urządzenia przenośnego dla każdego użytkownika, do których zasady mają zastosowanie podczas następnego zaewidencjonowania urządzenia przy użyciu pakietu Basic Mobility and Security. W przypadku wdrożenia nowych zasad, które mają zastosowanie do tych urządzeń użytkowników, zostanie wyświetlony monit o ponowne zarejestrowanie się w usłudze Basic Mobility and Security.

Możesz również całkowicie wyczyścić urządzenie lub selektywnie wyczyścić informacje organizacyjne z urządzenia. Aby uzyskać więcej informacji, zobacz [Czyszczenie urządzenia przenośnego w usłudze Basic Mobility and Security](wipe-mobile-device.md).

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie usługi Basic Mobility and Security](overview.md) (artykuł)\
[Możliwości usługi Basic Mobility and Security](capabilities.md) (artykuł)