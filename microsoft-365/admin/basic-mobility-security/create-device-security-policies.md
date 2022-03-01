---
title: Tworzenie zasad zabezpieczeń urządzeń w mobilności podstawowej i zabezpieczeniach
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
description: Za pomocą mobilności podstawowej i zabezpieczeń możesz tworzyć zasady dotyczące urządzeń chroniące informacje Twojej organizacji.
ms.openlocfilehash: c0fa9cec0b9029d2cd55aace0c758e6c81e265b0
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017741"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>Tworzenie zasad zabezpieczeń urządzeń w mobilności podstawowej i zabezpieczeniach

Za pomocą mobilności podstawowej i zabezpieczeń możesz tworzyć zasady dotyczące urządzeń, które chronią informacje Twojej organizacji przed Microsoft 365 nieautoryzowanym dostępem. Zasady można stosować do dowolnego urządzenia przenośnego w organizacji, na którym użytkownik ma mającą zastosowanie licencję Microsoft 365 i zarejestrowane na urządzeniu w pakietach Basic Mobility and Security.

## <a name="before-you-begin"></a>Przed rozpoczęciem

> [!IMPORTANT]
> Aby można było utworzyć zasady dotyczące urządzeń przenośnych, należy aktywować i skonfigurować pakiet Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz Omówienie mobilności podstawowej i zabezpieczeń.

- Dowiedz się więcej o urządzeniach, aplikacjach dla urządzeń przenośnych i ustawieniach zabezpieczeń, które obsługuje pakiet Basic Mobility and Security. Zobacz [Funkcje mobilności podstawowej i zabezpieczeń](capabilities.md).
- Utwórz grupy zabezpieczeń, które zawierają Microsoft 365 użytkowników, u których chcesz wdrożyć zasady, oraz użytkowników, których możesz wykluczyć z zablokowania dostępu do Microsoft 365. Zalecamy, aby przed wdrożeniem nowych zasad w organizacji przetestować je przez wdrożenie ich u niewielkiej liczby użytkowników. Możesz utworzyć grupę zabezpieczeń, która obejmuje tylko Ciebie lub niewielką Microsoft 365, którzy mogą testować zasady za Ciebie. Aby dowiedzieć się więcej o grupach zabezpieczeń, zobacz [Tworzenie, edytowanie lub usuwanie grupy zabezpieczeń](../email/create-edit-or-delete-a-security-group.md).
- Aby tworzyć i wdrażać zasady mobilności podstawowej i zabezpieczeń w programie Microsoft 365, musisz być administratorem Microsoft 365 globalnym. Aby uzyskać więcej informacji, [zobacz Uprawnienia w Centrum & zgodności](../../security/office-365-security/permissions-in-the-security-and-compliance-center.md).
- Przed wdrożeniem zasad poukaj swoją organizację o potencjalnych skutkach zarejestrowania urządzenia w pakietach Basic Mobility and Security. W zależności od sposobu skonfigurowania zasad nieuprawniane urządzenia mogą mieć zablokowaną możliwość uzyskiwania dostępu do aplikacji Microsoft 365 oraz danych, w tym zainstalowanych aplikacji, zdjęć i informacji osobistych na zarejestrowanym urządzeniu, a dane można usuwać.

> [!NOTE]
> Zasady i reguły dostępu utworzone w mobilności podstawowej i zabezpieczeniach dla aplikacji Microsoft 365 Business Standard zastępują Exchange ActiveSync skrzynek pocztowych urządzeń przenośnych i reguły dostępu do urządzeń utworzone w centrum administracyjnym Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">urządzenia</a>. Po zarejestrowaniu urządzenia w pakietach Basic Mobility and Security for Microsoft 365 Business Standard wszystkie Exchange ActiveSync skrzynki pocztowej urządzenia przenośnego lub reguła dostępu do urządzenia zastosowana do urządzenia są ignorowane. Aby dowiedzieć się więcej o Exchange ActiveSync, zobacz Exchange ActiveSync [w Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>Krok 1. Tworzenie zasad urządzenia i wdrażanie ich w grupie testowej

Zanim zaczniesz, upewnij się, że pakiet Basic Mobility and Security został aktywowany. Aby uzyskać instrukcje, [zobacz Omówienie mobilności podstawowej i zabezpieczeń](overview.md).

1. W przeglądarce wpisz .<https://protection.office.com/devicev2>

2. Wybierz **pozycję Utwórz zasady**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Ustawienia zasad mobilności podstawowej i zabezpieczeń.":::

3. Na **stronie Ustawienia zasad** określ wymagania, które chcesz stosować do urządzeń przenośnych w organizacji.

4. **Wymaganie zarządzania profilem** poczty e-mail: Po włączeniu urządzenia, które nie mają profilu poczty e-mail zarządzanego przez pakiet Basic Mobility and Security, są traktowane jako niezgodne. Urządzenie nie może mieć zarządzanego profilu poczty e-mail, jeśli nie jest ono poprawnie kierowane lub jeśli użytkownik ręcznie schował konto e-mail na urządzeniu. Jeśli pozostawisz ustawienie **Nie włączono** (ustawienie domyślne), to ustawienie nie jest sprawdzane pod celu zapewnienia zgodności lub niezgodności. Aby uzyskać instrukcje dotyczące sposobu, w jaki użytkownicy mogą uzyskać zgodność po wybraniu tej opcji, zobacz [Odnaleziono istniejące konto e-mail](/intune-user-help/existing-company-email-account-found).

5. Na **stronie Czy chcesz teraz zastosować** te zasady? wybierz grupy, do których chcesz zastosować te zasady.

6. Wybierz **pozycję Utwórz te zasady**.

Zasady są wypychane do urządzenia każdego użytkownika, do następnego logowania w celu Microsoft 365 urządzenia przenośnego. Jeśli do ich urządzeń przenośnych nie zastosowano jeszcze zasad, po wdrożeniu zasad użytkownicy otrzymają na swoim urządzeniu powiadomienie o czynnościach rejestracji i aktywacji pakietu Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego za pomocą platformy Basic Mobility and Security](enroll-your-mobile-device.md). Dopóki nie ukończą oni rejestracji w pakietach Basic Mobility i Security hostowanych przez usługę Intune, dostęp do poczty e-mail, OneDrive i innych usług jest ograniczony. Po zakończeniu rejestracji za pomocą aplikacji Intune — Portal firmy mogą oni korzystać z usług, a zasady są stosowane do ich urządzeń.

## <a name="step-2-verify-that-your-policy-works"></a>Krok 2. Sprawdzanie, czy zasady działają

Po utworzeniu zasad urządzenia zanim wdrożysz je w organizacji, sprawdź, czy te zasady działają zgodnie z oczekiwaniami.

1. W przeglądarce wpisz .[https://protection.office.com/devicev2](https://protection.office.com/devicev2)
2. Wybierz **pozycję Wyświetl listę urządzeń zarządzanych**.
3. Sprawdź stan urządzeń użytkowników, na których zastosowano zasady. Chcesz **zarządzać stanem** **urządzeń.**
4. Możesz również wykonać pełne lub selektywne czyszczenie urządzenia, klikając pozycję Resetowanie do ustawień fabrycznych lub  Usuń dane firmowe  z przycisku Zarządzaj po wybraniu urządzenia. Aby uzyskać instrukcje, zobacz [Czyszczenie urządzenia przenośnego w Microsoft 365.

## <a name="step-3-deploy-a-policy-to-your-organization"></a>Krok 3. Wdrażanie zasad w organizacji

Po utworzeniu zasad urządzenia i sprawdzeniu, że działa zgodnie z oczekiwaniami, wdeksuj je w swojej organizacji.

1. W przeglądarce wpisz: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).
2. Wybierz zasady, które chcesz wdrożyć, a następnie wybierz pozycję **Edytuj** obok **grupy, do których zastosowano.**
3. Wyszukaj grupę do dodania i kliknij pozycję **Wybierz**.
4. Wybierz **pozycję Zamknij** **i zmień ustawienia.**
5. Wybierz **pozycję Zamknij** **i edytuj zasady.**

Zasady są wypychane do urządzenia przenośnego każdego użytkownika, do przypadku następnego zalogowania się w celu Microsoft 365 urządzenia przenośnego. Jeśli użytkownicy nie mieli zasad zastosowanych do ich urządzeń przenośnych, otrzymają na swoim urządzeniu powiadomienie z instrukcjami, aby je zarejestrować i aktywować na platformie Basic Mobility and Security. Po zakończeniu rejestracji zasady są stosowane do ich urządzeń. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego za pomocą platformy Basic Mobility and Security](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>Krok 4. Blokowanie dostępu do poczty e-mail dla nieobsługiwanych urządzeń

Aby ułatwić zabezpieczanie informacji o organizacji, należy zablokować aplikacji dostęp do poczty e-Microsoft 365 dla urządzeń przenośnych, które nie są obsługiwane przez pakiet Basic Mobility and Security. Aby uzyskać listę obsługiwanych urządzeń, zobacz [Obsługiwane urządzenia](../../admin/basic-mobility-security/capabilities.md).

**Aby zablokować dostęp do aplikacji:**

1. W przeglądarce wpisz .[https://protection.office.com/devicev2](https://protection.office.com/devicev2)
2. Wybierz **pozycję Zarządzaj ustawieniami dostępu do urządzenia w całej organizacji**.
3. Aby zablokować nieobsługiwane urządzenia, wybierz  pozycję Blokuj w obszarze Jeśli urządzenie nie jest obsługiwane przez pakiet **Basic Mobility and Security for Microsoft 365, a** następnie wybierz pozycję **Zapisz**.

   :::image type="content" source="../../media/basic-mobility-security/bms-5-block-access.png" alt-text="Opcja dostępu blokowego podstawowa mobilność i zabezpieczenia.":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>Krok 5. Wybieranie grup zabezpieczeń do wykluczenia z testów dostępu warunkowego

Jeśli chcesz wykluczyć niektóre osoby z kontroli dostępu warunkowego na ich urządzeniach przenośnych i utworzono jedną lub więcej grup zabezpieczeń dla tych osób, dodaj te grupy zabezpieczeń tutaj. Osoby w tych grupach nie będą wymuszane żadnych zasad dla obsługiwanych urządzeń przenośnych. Jest to zalecana opcja, jeśli nie chcesz już korzystać z mobilności podstawowej i zabezpieczeń w organizacji.

1. W przeglądarce wpisz .[https://protection.office.com/devicev2](https://protection.office.com/devicev2)

2. Wybierz **pozycję Zarządzaj ustawieniami dostępu do urządzenia w całej organizacji**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Podstawowa mobilność i zabezpieczenia — tworzenie opcji zasad.":::

3. Wybierz **pozycję** Dodaj, aby dodać grupę zabezpieczeń z użytkownikami, których chcesz wykluczyć z zablokowania dostępu do Microsoft 365. Gdy użytkownik zostanie dodany do tej listy, będzie on mieć dostęp do Microsoft 365 e-mail, gdy korzysta z nieobsługiwanego urządzenia.

4. W panelu Wybierz grupę wybierz grupę, której **chcesz użyć.**

5. Wybierz nazwę, a następnie **pozycję** **DodajZasad** > .

6. W **panelu ustawień dostępu do urządzenia dla całej** organizacji wybierz pozycję **Zapisz**.

   :::image type="content" source="../../media/basic-mobility-security/bms-8-allow-access.png" alt-text="Opcja dostępu z pakietem Basic Mobility and Security.":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>Jaki wpływ mają zasady zabezpieczeń na różne typy urządzeń?

Po zastosowaniu zasad do urządzeń użytkowników wpływ na poszczególne urządzenia różni się nieco w zależności od typów urządzeń. Przykłady wpływu zasad na różne urządzenia można znaleźć w poniższej tabeli.

|**Zasady zabezpieczeń**|**Android 4 lub nowszy**|**Samsung KNOX**|**iOS 6 lub nowszy**|**Uwagi**|
|:-----|:-----|:-----|:-----|:-----|
|Wymagaj zaszyfrowanej kopii zapasowej|Nie|Tak|Tak|Wymagana jest zaszyfrowana kopia zapasowa systemu iOS.|
|Blokowanie kopii zapasowej w chmurze|Tak|Tak|Tak|Zablokuj kopię zapasową Google w systemie Android (wyszarzona), kopia zapasowa w chmurze w systemie iOS.|
|Blokowanie synchronizacji dokumentów|Nie|Nie|Tak|iOS: Blokuj dokumenty w chmurze.|
|Blokowanie synchronizacji zdjęć |Nie|Nie|Tak|iOS (natywny): Zablokuj strumień zdjęć.|
|Zablokuj przechwytywanie ekranu |Nie|Tak|Tak|Zablokowane przy próbie.|
|Blokowanie konferencji wideo |Nie|Nie|Tak|FaceTime zablokowane na iOS, nie na Skype i innych.|
|Blokowanie wysyłania danych diagnostycznych |Nie|Tak|Tak|Blokowanie wysyłania raportu o awarii Google w systemie Android.|
|Blokowanie dostępu do sklepu z aplikacjami |Nie|Tak|Tak|Na stronie głównej systemu Android brakuje ikony sklepu z aplikacjami, wyłączona Windows w systemie iOS.|
|Wymaganie hasła do sklepu z aplikacjami |Nie|Nie|Tak|iOS: Hasło wymagane do zakupów w programie iTunes.|
|Blokowanie połączenia z magazynem wymiennym |Nie|Tak|Nie dotyczy|Android: Karta SD jest wyszarzona w ustawieniach, Windows powiadomienia dla użytkownika, zainstalowane aplikacje nie są dostępne|
|Blokowanie Bluetooth sieci |Wyświetlanie notatek|Wyświetlanie notatek|Tak|Nie możemy wyłączyć funkcji BlueTooth jako ustawienia w systemie Android. Zamiast tego wyłączamy wszystkie transakcje, które wymagają usługi BlueTooth: zaawansowana dystrybucja dźwięku, zdalnego sterowania dźwiękiem/wideo, urządzeniami głośnomówiącymi, zestawem słuchawkowym, dostępem do książki Telefon i portem seryjnym. Gdy zostanie użyta dowolna z tych sytuacji, u dołu strony zostanie wyświetlony mały wyskakujące komunikat.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>Co się dzieje po usunięciu zasad lub usunięciu użytkownika z zasad?

Po usunięciu zasad lub usunięciu użytkownika z grupy, w której zasady zostały wdrożone, ustawienia zasad, profil poczty e-mail Microsoft 365 i buforowane wiadomości e-mail mogą zostać usunięte z urządzenia użytkownika. Zobacz w poniższej tabeli, co zostało usunięte dla poszczególnych typów urządzeń.

|**Co zostało usunięte**|**iOS 6 lub nowszy**|**System Android 4 i nowszy (z uwzględnieniem samsung KNOX)**|
|:-----|:-----|:-----|
|Zarządzane profile poczty <sup>e-mail1</sup>|Tak|Nie|
|Blokowanie kopii zapasowej w chmurze|Tak|Nie|

<sup>1</sup> Jeśli zasady zostały wdrożone z wybraną opcją Profil  poczty e-mail, profil zarządzanej poczty e-mail i buforowane wiadomości e-mail w tym profilu są usuwane z urządzenia użytkownika.

Zasady zostaną usunięte z urządzenia przenośnego dla każdego użytkownika, do następnego zae m.in. zae m.in. przy testach na urządzeniach z pakietem Basic Mobility and Security. W przypadku wdrożenia nowych zasad, które dotyczą tych urządzeń użytkowników, zostanie wyświetlony monit o ponowne zarejestrowanie się w mobilności podstawowej i zabezpieczeniach.

Możesz również wyczyścić urządzenie albo całkowicie, albo selektywnie wyczyścić informacje organizacyjne z urządzenia. Aby uzyskać więcej informacji, zobacz [Czyszczenie urządzenia przenośnego w pakietach Basic Mobility and Security](wipe-mobile-device.md).

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie mobilności podstawowej i zabezpieczeń](overview.md) (artykuł)\
[Możliwości mobilności podstawowej i zabezpieczeń](capabilities.md) (artykuł)