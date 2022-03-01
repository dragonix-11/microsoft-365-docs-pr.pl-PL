---
title: Konfigurowanie ustawień zabezpieczeń w programie Microsoft Defender dla firm
description: Konfigurowanie zasad zabezpieczeń w programie Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/14/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 3d1c024858e81031c5ae985857211723db7b10ac
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014823"
---
# <a name="configure-your-security-policies-in-microsoft-defender-for-business-preview"></a>Konfigurowanie zasad zabezpieczeń w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Po dojecheniu urządzeń organizacji do programu Microsoft Defender dla firm (wersja Preview) następnym krokiem jest wyświetlenie i w razie potrzeby edytowanie zasad zabezpieczeń. W programie Defender dla firm (wersja Preview) ustawienia zabezpieczeń są stosowane do urządzeń za pośrednictwem zasad. Te zasady są stosowane do [grup urządzeń](mdb-create-edit-device-groups.md#what-is-a-device-group). 

Istnieją również inne ustawienia, które można skonfigurować w uchcie programu Defender dla firm (wersja Preview). Te ustawienia obejmują między innymi Twoją strefę czasową oraz to, czy chcesz otrzymywać funkcje wersji Preview.

## <a name="what-to-do"></a>Co należy zrobić

1. [Krótkie omówienie domyślnych zasad zabezpieczeń w programie Defender dla firm](#default-policies-in-defender-for-business)

2. [Wybierz miejsce zarządzania zasadami zabezpieczeń i urządzeniami](#choose-where-to-manage-security-policies-and-devices).

3. [Wyświetl zasady zabezpieczeń](#view-your-security-policies).

4. [Wyświetlanie i edytowanie innych ustawień w Microsoft 365 Defender sieci Microsoft 365 Defender sieci](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal) 

5. [Przejdź do następnych kroków](#next-steps).

## <a name="default-policies-in-defender-for-business"></a>Zasady domyślne w uchcie programu Defender dla firm

Program Defender dla firm (wersja Preview) zawiera zasady domyślne, które używają zalecanych ustawień. Są to między innymi poniższe zasady:

- [ustawienia ochrony następnej generacji](mdb-next-gen-configuration-settings.md), które określają Program antywirusowy Microsoft Defender konfiguracji funkcji ochrony przed zagrożeniami; oraz 
- [Ustawienia zapory](mdb-firewall.md), które określają, jaki ruch sieciowy może przepływać do i z Windows klienckich Twojej organizacji.

Domyślne zasady można zastosować do Windows klienckich podczas procesu konfiguracji wstępnej. Możesz również definiować nowe zasady i edytować istniejące zasady odpowiednio do potrzeb biznesowych. 

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Wybieranie miejsca zarządzania zasadami zabezpieczeń i urządzeniami

Program Defender dla firm (wersja Preview) oferuje [uproszczony proces konfiguracji,](mdb-simplified-configuration.md) który ułatwia proces konfiguracji. Jeśli wybierzesz uproszczony proces konfiguracji, możesz wyświetlać zasady zabezpieczeń i zarządzać nimi w portalu Microsoft 365 Defender sieci ([https://security.microsoft.com/](https://security.microsoft.com/)). Nie ograniczamy się jednak do tej opcji. Jeśli do zarządzania zasadami zabezpieczeń i urządzeniami używano programu Microsoft Endpoint Manager (w tym Microsoft Intune) lub rozwiązania firmy innego niż firma Microsoft do zarządzania zasadami zabezpieczeń i urządzeniami, możesz nadal korzystać z bieżącego rozwiązania.

W poniższej tabeli przedstawiono sposób zarządzania zasadami i urządzeniami zabezpieczeń. <br/><br/>

| Opcja | Opis |
|:---|:---|
| **Użyj domyślnych zasad zabezpieczeń w portalu Microsoft 365 Defender (zalecane**) | Program Defender dla firm (wersja Preview) został zaprojektowany z myślą o potrzebach osób zajętych w małych i średnich firmach. Domyślne zasady zabezpieczeń usługi Defender dla firm są przeznaczone do ochrony urządzeń organizacji od pierwszego dnia.<br/><br/>Za pomocą portalu Microsoft 365 Defender () możesz[https://security.microsoft.com/](https://security.microsoft.com/) wyświetlać zasady zabezpieczeń i zarządzać nimi.<br/><br/>Aby dowiedzieć się więcej, zobacz [Wyświetlanie lub edytowanie zasad urządzenia](mdb-view-edit-policies.md). |
| **Używanie Microsoft Endpoint Manager** | Jeśli Twoja organizacja używa programu Microsoft Endpoint Manager do zarządzania zasadami zabezpieczeń, możesz nadal używać programu Endpoint Manager i stosować zasady zabezpieczeń do niektórych lub wszystkich urządzeń. Aby dowiedzieć się więcej, zobacz [Zarządzanie zabezpieczeniami urządzeń za pomocą zasad zabezpieczeń punktów końcowych w programie Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>Rozważ przełączenie do [uproszczonego procesu konfiguracji w programie Defender dla firm](mdb-simplified-configuration.md). Jeśli dokonasz przełączenia, przed przejściem do uproszczonego procesu konfiguracji w programie Defender dla firm w programie Microsoft Endpoint Manager zostanie wyświetlony monit o usunięcie wszystkich istniejących zasad zabezpieczeń w programie Microsoft Endpoint Manager. Usunięcie zasad z programu Microsoft Endpoint Manager pomaga uniknąć konfliktów zasad w późniejszym czasie. |

> [!TIP]
> Jeśli chcesz zarejestrować się w programie Microsoft Defender for Business Preview, odwiedź stronę [https://aka.ms/MDB-Preview](https://aka.ms/MDB-Preview). Aby dowiedzieć się więcej, zobacz [Uzyskiwanie programu Microsoft Defender dla firm (wersja Preview)](get-defender-business.md).

## <a name="view-your-security-policies"></a>Wyświetlanie zasad zabezpieczeń

Aby wyświetlić listę zasad zabezpieczeń, użyj jednej z procedur z poniższej tabeli:
<br/><br/>

| Portal | Procedura |
|:---|:---|
| Microsoft 365 Defender portalu ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. <br/><br/>2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są uporządkowane według systemu operacyjnego i typu zasad.<br/><br/>3. Wybierz kartę systemu operacyjnego (na przykład Windows **klientów**).<br/><br/>4. Rozwiń kategorię ( **na przykład Ochrona** następnej generacji lub **Zapora**), aby wyświetlić listę zasad.<br/><br/>5. Wybierz zasady, aby wyświetlić więcej szczegółów dotyczących zasad. Aby wprowadzić zmiany lub dowiedzieć się więcej o ustawieniach zasad, zobacz następujące artykuły: <br/>- [Wyświetlanie lub edytowanie zasad urządzenia](mdb-view-edit-policies.md)<br/>- [Opis ustawień konfiguracji następnej generacji](mdb-next-gen-configuration-settings.md)<br/>- [Ustawienia zapory](mdb-firewall.md)  |
| Microsoft Endpoint Manager administracyjne ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Przejdź do i [https://endpoint.microsoft.com](https://endpoint.microsoft.com) zaloguj się. Jesteś teraz w centrum Microsoft Endpoint Manager administracyjnego.<br/><br/>2. Wybierz **zabezpieczenia punktu końcowego**.<br/><br/>3. Wybierz  kategorię, taką jak Oprogramowanie **antywirusowe,** Zapora **, Wykrywanie** punktu końcowego i **odpowiedź lub Zmniejszenie** powierzchni ataków, aby wyświetlić zasady w tej kategorii. <br/><br/>Aby uzyskać pomoc na temat zarządzania ustawieniami zabezpieczeń w aplikacji Microsoft Endpoint Manager, zacznij od [tematu Zarządzanie zabezpieczeniami punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Wyświetlanie i edytowanie innych ustawień w Microsoft 365 Defender sieci Microsoft 365 Defender sieci

Oprócz zasad zabezpieczeń stosowanych do urządzeń istnieją inne ustawienia, które można wyświetlać i edytować w programie Defender dla firm (wersja Preview). Możesz na przykład określić strefę czasową, która ma być używania, i możesz korzystać z urządzeń wyniesinych (lub wyłączonych). 

> [!NOTE]
> W dzierżawie może być więcej ustawień niż wymieniono w tym artykule. Wyróżniamy ustawienia, które należy przejrzeć w programie Defender dla firm (wersja Preview).

### <a name="settings-to-review-for-defender-for-business"></a>Ustawienia do przejrzenia dla usługi Defender dla firm

W poniższej tabeli opisano ustawienia wyświetlania (i w razie potrzeby edytowania) programu Defender dla firm (wersja Preview).

<br/><br/>

| Kategoria | Ustawienie | Opis |
|:---|:---|:---|
| **Centrum zabezpieczeń** | **Strefa czasowa** | Wybierz strefę czasową, która ma być używana dla dat i godzin wyświetlanych w przypadku zdarzeń, wykrytych zagrożeń oraz automatycznego badania & rozwiązywania problemów. Możesz użyć czasu UTC lub lokalnej strefy czasowej (*zalecane*).  |
| **Microsoft 365 Defender** | **Konto** | Wyświetl szczegóły, takie jak miejsce przechowywania danych, identyfikator dzierżawy i identyfikator organizacji (organizacji). |
| **Microsoft 365 Defender**  | **Funkcje wersji Preview**  | Włącz funkcje wersji Preview, aby wypróbować nadchodzące funkcje i nowe funkcje. Możesz zostać jednym z pierwszych użytkowników, który będzie korzystać z wersji zapoznawczej nowych funkcji i przekazać opinię. |
| **Punkty końcowe**  | **Powiadomienia e-mail** | Skonfiguruj lub edytuj reguły powiadomień e-mail. W przypadku wykrycia luk lub utworzenia alertu adresaci wskazany w twoich zasadach powiadomień e-mail otrzymają wiadomość e-mail. [Dowiedz się więcej o powiadomieniach e-mail](mdb-email-notifications.md). |
| **Punkty końcowe**   | **Zarządzanie urządzeniami** >  **Wniesienie** | Urządzenia w programie Defender dla firm można dołączać za pomocą skryptu do pobrania. Aby dowiedzieć się więcej, zobacz [Na urządzeniach w programie Microsoft Defender dla firm (wersja Preview).](mdb-onboard-devices.md)   |  
| **Punkty końcowe**  |  **Zarządzanie urządzeniami** >  **Wyniesienie** | Urządzenia w trybie offboard (usuwanie) z usługi Defender dla firm (wersja Preview). Po odłoceniu urządzenia nie będzie ono już wysyłać danych do usługi Defender dla firm (wersja Preview), ale dane otrzymane przed wynoszdaniem urządzenia zostaną zachowane. Aby dowiedzieć się więcej, [zobacz Wyniesanie urządzenia](mdb-onboard-devices.md#offboarding-a-device).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Uzyskiwanie dostępu do ustawień w Microsoft 365 Defender sieci Microsoft 365 Defender

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com/](https://security.microsoft.com/)) i zaloguj się.

2. Wybierz **Ustawienia**, a następnie wybierz kategorię (na przykład Centrum **zabezpieczeń, Microsoft 365 Defender** **lub** **Punkty końcowe**).

3. Na liście ustawień wybierz element do wyświetlenia lub edytowania.


## <a name="next-steps"></a>Następne kroki

Przejdź do co najmniej jednego z następujących zadań:

- [Wprowadzenie do korzystania z usługi Microsoft Defender dla firm (wersja Preview)](mdb-get-started.md)

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm (wersja preview)](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-manage-incidents.md)

- [Wyświetlanie i edytowanie zasad w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-edit-policies.md)

