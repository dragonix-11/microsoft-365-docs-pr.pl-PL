---
title: Szczegółowe informacje o personifikacji
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się, jak działa szczegółowe informacje o personifikacji. Mogą szybko ustalić, którzy nadawcy legalnie wysyłają wiadomości e-mail do swoich organizacji z domen, które nie przechodzą testów uwierzytelniania poczty e-mail (SPF, DKIM lub DMARC).
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0d9d8ee89aaa551c5fecf7c38fe0dbba97ed7fc8
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032148"
---
# <a name="impersonation-insight-in-defender-for-office-365"></a>Informacje dotyczące personifikacji w uchcie defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i nie są dostępne we wszystkich organizacjach.

Personifikacja to miejsce, w którym nadawca wiadomości e-mail wygląda bardzo podobnie do rzeczywistego lub oczekiwanego adresu e-mail nadawcy. Atakujący często podszywają się pod adresy e-mail nadawców w celu wyłudzania informacji lub innego rodzaju ataków w celu uzyskania zaufania adresata. Istnieją dwa typy personifikacji:

- **Personifikacja domeny**: zamiast lila@contoso.com adres e-mail spersonifikowania nadawcy to lila@ćóntoso.com.
- **Personifikacja użytkownika**: zamiast michelle@contoso.com adres e-mail spersonifikowania nadawcy to rnichell@contoso.com.

Personifikacja domeny różni się od [spoofingu domeny](anti-spoofing-protection.md), ponieważ spersonifikowana domena jest zwykle rzeczywistą, zarejestrowaną domeną. Wiadomości od nadawców w domenie personifikacji mogą i często przechodzą zwykłe testy uwierzytelniania poczty e-mail, które w przeciwnym razie identyfikują próby fałszowania (SPF, DKIM i DMARC).

Ochrona przed personifikacjami jest częścią ustawień zasad ochrony przed wyłudzaniem informacji, które są dostępne wyłącznie w programie Microsoft Defender dla Office 365. Aby uzyskać więcej informacji na temat tych ustawień, zobacz Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w [programie Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

Za pomocą szczegółowych informacji o personifikacji w portalu Microsoft 365 Defender możesz szybko identyfikować wiadomości od spersonifikowanych nadawców lub domen nadawców skonfigurowanych do ochrony personifikacji.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony ochrony **przed wyłudzaniem** informacji, użyj .<https://security.microsoft.com/antiphishing> Aby przejść bezpośrednio do strony **Informacji o personifikacji**, użyj .<https://security.microsoft.com/impersonationinsight>

- Aby można było wykonać procedury z tego artykułu, musisz mieć przypisane uprawnienia Microsoft 365 Defender portalu administracyjnego:
  - **Zarządzanie organizacją**
  - **Administrator zabezpieczeń**
  - **Czytnik zabezpieczeń**
  - **Czytnik globalny**

  Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).

  **Uwaga**: Dodanie użytkowników do odpowiedniej roli Azure Active Directory w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender oraz uprawnienia do innych funkcji w  Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).

- Włączanie i konfigurowanie ochrony przed personifikacjami w zasadach ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365. Ochrona personifikacji nie jest domyślnie włączona. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="open-the-impersonation-insight-in-the-microsoft-365-defender-portal"></a>Otwórz szczegółowe informacje o personifikacji w Microsoft 365 Defender wiadomości

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem przejdź  \> do sekcji & **e-mail** i zasad współpracy **& zasady** \>  \> zagrożeń zapobiegające wyłudzaniu **informacji.** Aby przejść bezpośrednio do strony ochrony **przed wyłudzaniem** informacji, użyj .<https://security.microsoft.com/antiphishing>

2. Na stronie **ochrony przed wyłudzaniem** informacji o personifikacji wygląda ona następująco:

   ![Szczegółowe informacje o personifikacji i spoof intelligence na stronie zasad ochrony przed wyłudzaniem informacji.](../../media/m365-sc-impersonation-and-spoof-intelligence-insight.png)

   Szczegółowe informacje są dostępne w dwóch trybach:

    - **Tryb szczegółowej** informacji: Jeśli ochronę przed personifikacji włączono i skonfigurowano we wszystkich zasadach ochrony przed wyłudzaniem informacji, szczegółowe informacje będą zawierały liczbę wykrytych wiadomości od personifikowanych domen i personifikowanych użytkowników (nadawców) w ciągu ostatnich siedmiu dni. Jest to suma wszystkich wykrytych spersonifikowanych nadawców ze wszystkich zasad ochrony przed wyłudzaniem informacji.
    - **Co** zrobić, jeśli tryb: Jeśli ochrona przed personifikacji nie została włączona i skonfigurowana w żadnych aktywnych zasadach ochrony przed wyłudzaniem informacji, możesz sprawdzić, ile wiadomości zostałoby wykrytych przez nasze funkcje ochrony przed personifikacji w ciągu ostatnich siedmiu dni.

Aby wyświetlić informacje na temat wykrywania personifikacji, kliknij pozycję **Wyświetl personifikację** w szczegółowych informacjach o personifikacji.

   > [!NOTE]
   > Aby uzyskać informacje o analizie fałszerów, zobacz [Spoof intelligence insight in EOP (Spoof intelligence insight in EOP](learn-about-spoof-intelligence.md)).

## <a name="view-information-about-messages-from-senders-in-impersonated-domains"></a>Wyświetlanie informacji o wiadomościach od nadawców w spersonifikowanych domenach

Na stronie **Szczegółowe informacje o personifikacji** , która jest wyświetlana po kliknięciu przycisku **Wyświetl** personifikację w szczegółowej informacji o personifikacji, sprawdź, czy **wybrano kartę** Domeny. Karta **Domeny** zawiera następujące informacje:

- **Sender Domain** (Domena nadawcy): domena personifikacji, czyli domena użyta do wysłania wiadomości e-mail.
- **Liczba wiadomości**: Liczba wiadomości od personifikowania domeny nadawcy w ciągu ostatnich 7 dni.
- **Typ personifikacji**: Ta wartość pokazuje wykrytą lokalizację personifikacji (na przykład **Domena w adresie**).
- **Personifikowane domeny**: spersonifikowana domena, która powinna dokładnie przypominać domenę skonfigurowaną do ochrony przed personifikacji w zasadach ochrony przed wyłudzaniem informacji.
- **Typ domeny**: Ta wartość to **Domena firmy dla** domen wewnętrznych lub **Domena niestandardowa** dla domen niestandardowych.
- **Zasady**: Zasady ochrony przed wyłudzaniem informacji, które wykryły spersonifikowane domeny.
- **Może personifikować**: Jedna z następujących wartości:
  - **Tak**: Domena została skonfigurowana jako zaufana domena (wyjątek dla ochrony przed personifikacji) w zasadach ochrony przed wyłudzaniem informacji. Wiadomości od nadawców w spersonifikowanych domenach zostały wykryte, ale dozwolone.
  - **Nie**: Domena została skonfigurowana do ochrony przed personifikacjami w zasadach ochrony przed wyłudzaniem informacji. Wiadomości od nadawców w spersonifikowanych domenach zostały wykryte i działanie w oparciu o akcję personifikowania domen w zasadach ochrony przed wyłudzaniem informacji.

Możesz kliknąć wybrane nagłówki kolumn, aby posortować wyniki.

Aby filtrować wyniki, możesz użyć ikony ![Wyszukiwania.](../../media/m365-cc-sc-search-icon.png) **Pole** wyszukiwania , aby wprowadzić listę wartości rozdzielanych przecinkami w celu przefiltrowania wyników.

### <a name="view-details-about-messages-from-senders-in-impersonated-domains"></a>Wyświetlanie szczegółów wiadomości od nadawców w domenach personifikowanych

Na karcie **Domeny** na stronie **Szczegółowe informacje o personifikacji** wybierz jedną z dostępnych wykrywania personifikacji. Wyświetlone okno wysuwu szczegółów zawiera następujące informacje i funkcje:

- **Zasady personifikacji wyboru do zmodyfikowania**: Wybierz odpowiednie zasady ochrony przed wyłudzaniem informacji, które chcesz zmodyfikować. Dostępne są tylko zasady, w których w zasadach jest zdefiniowana personifikowana domena. Skorzystaj z poprzedniej strony, aby zobaczyć, które zasady były rzeczywiście odpowiedzialne za wykrywanie spersonifikowanych domen (prawdopodobnie na podstawie adresata i priorytetu zasad).
- **Dodaj do listy dozwolonych** personifikacji: Użyj tego przełącznika, aby dodać lub usunąć nadawcę z listy Zaufani nadawcy i **domeny (wyjątki** personifikacji) wybranej zasady ochrony przed wyłudzaniem informacji:
  - Jeśli wartość **z uprawnieniami do personifikacji** dla tego **wpisu była nie**, przełącznik jest wyłączony. Aby wykluczyć wszystkich nadawców w tej domenie z oceny za pomocą ochrony personifikacji, przesuń przełącznik do przełącznika: ![Włącz.](../../media/scc-toggle-on.png). Domena zostanie dodana do listy **Zaufane** domeny w ustawieniach ochrony przed personifikacji w zasadach ochrony przed wyłudzaniem informacji.
  - Jeśli wartość **z uprawnieniami do personifikacji** dla tego **wpisu była** twierdząca, przełącznik jest wł. Aby zwrócić wszystkich nadawców w tej domenie do oceny przez ochronę personifikacji, przesuń przełącznik w celu wyłączenia: ![Wyłącz](../../media/scc-toggle-off.png). Domena zostanie usunięta z listy **Zaufane domeny** w ustawieniach ochrony przed personifikacji w zasadach ochrony przed wyłudzaniem informacji.
- Dlaczego go przygotowaliśmy.
- Co należy zrobić.
- Podsumowanie domeny z listą spersonifikowanych domen.
- WhoIs data about the sender.
- Link do otwierania [Eksploratora zagrożeń](threat-explorer.md) w celu zobaczenia dodatkowych szczegółów dotyczących nadawcy.
- Podobne wiadomości od tego samego nadawcy, które zostały dostarczone do Twojej organizacji.

## <a name="view-information-about-messages-from-impersonated-senders"></a>Wyświetlanie informacji o wiadomościach od spersonifikowanych nadawców

Na stronie **Szczegółowe informacje o personifikacji** , która pojawia się po kliknięciu przycisku **Wyświetl** personifikację w szczegółowych informacjach o personifikacji kliknij **kartę** Użytkownicy. Karta **Użytkownicy** zawiera następujące informacje:

- **Nadawca**: adres e-mail nadawcy, który wysłał wiadomość e-mail.
- **Liczba wiadomości**: Liczba wiadomości od nadawcy personifikacji w ciągu ostatnich 7 dni.
- **Typ personifikacji**: Ta wartość to **Użytkownik w nazwie wyświetlanej**.
- **Personifikowane osoby**: adres e-mail spersonifikowanych nadawców, który powinien przypominać użytkownika, dla którego skonfigurowano ochronę przed personifikacji w zasadach ochrony przed wyłudzaniem informacji.
- **Typ użytkownika**: ta wartość pokazuje zastosowany typ ochrony (na przykład Użytkownik **chroniony lub** Inteligencja **skrzynki pocztowej**).
- **Zasady**: Zasady ochrony przed wyłudzaniem informacji, które wykryły spersonifikowany nadawcę.
- **Może personifikować**: Jedna z następujących wartości:
  - **Tak**: Nadawca został skonfigurowany jako zaufany użytkownik (wyjątek dla ochrony przed personifikacji) w zasadach ochrony przed wyłudzaniem informacji. Wiadomości od personifikacji nadawcy zostały wykryte, ale zostały dozwolone.
  - **Nie**: Nadawca został skonfigurowany do ochrony przed personifikacjami w zasadach ochrony przed wyłudzaniem informacji. Wiadomości od spersonifikowanych nadawców zostały wykryte i działanie na podstawie akcji dotyczącej personifikowanych użytkowników w zasadach ochrony przed wyłudzaniem informacji.

Możesz kliknąć wybrane nagłówki kolumn, aby posortować wyniki.

Aby filtrować wyniki, możesz użyć pola Filtruj nadawcę w celu wprowadzenia listy wartości rozdzielanych przecinkami w celu przefiltrowania wyników.

### <a name="view-details-about-messages-from-impersonated-senders"></a>Wyświetlanie szczegółów wiadomości od spersonifikowanych nadawców

Na karcie **Użytkownicy** na stronie **Szczegółowe informacje o personifikacji** wybierz jedną z dostępnych wykrywania personifikacji. Wyświetlone okno wysuwu szczegółów zawiera następujące informacje i funkcje:

- **Zasady personifikacji wyboru do zmodyfikowania**: Wybierz odpowiednie zasady ochrony przed wyłudzaniem informacji, które chcesz zmodyfikować. Dostępne są tylko zasady, w których personifikowany nadawca został zdefiniowany w zasadach. Na poprzedniej stronie można sprawdzić, które zasady były faktycznie odpowiedzialne za wykrycie spersonifikowania nadawcy (prawdopodobnie na podstawie adresata i priorytetu zasad).
- **Dodaj do listy dozwolonych** personifikacji: Użyj tego przełącznika, aby dodać lub usunąć nadawcę z listy Zaufani nadawcy i **domeny (wyjątki** personifikacji) wybranej zasady ochrony przed wyłudzaniem informacji:
  - Jeśli wartość **z uprawnieniami do personifikacji** dla tego **wpisu była nie**, przełącznik jest wyłączony. Aby wykluczyć nadawcę z oceny za pomocą ochrony personifikacji, przesuń przełącznik do przycisku wł.: ![Włącz.](../../media/scc-toggle-on.png). Nadawca zostanie dodany do listy **Zaufani użytkownicy** w ustawieniach ochrony przed personifikacji w zasadach ochrony przed wyłudzaniem informacji.
  - Jeśli wartość **z uprawnieniami do personifikacji** dla tego **wpisu była** twierdząca, przełącznik jest wł. Aby zwrócić nadawcę do oceny przez ochronę personifikacji, przesuń przełącznik w celu wyłączenia: ![Wyłącz.](../../media/scc-toggle-off.png) Nadawca zostanie usunięty z listy **Zaufani użytkownicy** w ustawieniach ochrony przed personifikacjami zasad ochrony przed wyłudzaniem informacji.
- Dlaczego go przygotowaliśmy.
- Co należy zrobić.
- Podsumowanie nadawcy z listą personifikowanych nadawców.
- WhoIs data about the sender.
- Link do otwierania [Eksploratora zagrożeń](threat-explorer.md) w celu zobaczenia dodatkowych szczegółów dotyczących nadawcy.
- Podobne wiadomości od tego samego nadawcy, które zostały dostarczone do Twojej organizacji.
