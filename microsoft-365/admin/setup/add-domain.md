---
title: Dodawanie domeny do Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
- business_assist
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 6383f56d-3d09-4dcb-9b41-b5f5a5efd611
description: Za pomocą kreatora konfiguracji dodaj domenę do Microsoft 365 w centrum administracyjne platformy Microsoft 365, dodając rekord DNS na hoście DNS.
ms.openlocfilehash: fa809486b968c4bc0f8c74e466285ee2ce9ac895
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321715"
---
# <a name="add-a-domain-to-microsoft-365"></a>Dodawanie domeny do Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dodawać, modyfikować lub usuwać domeny, musisz  być administratorem nazwy domeny lub **administratorem globalnym planu** dla [firm lub przedsiębiorstwa](https://products.office.com/business/office). Te zmiany wpływają na całą dzierżawę; *Dostosowani administratorzy* *lub zwycięscy* użytkownicy nie będą mogli wprowadzać tych zmian.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="watch-add-a-domain"></a>Obejrzyj: Dodawanie domeny

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Twoja firma może potrzebować wielu nazw domen do różnych celów. Na przykład możesz zechcieć dodać inną pisownię nazwy firmy, ponieważ klienci już z niego korzystają, a ich komunikacja nie dotarła do Ciebie.

1. W centrum administracyjne platformy Microsoft 365 wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Konfiguracja**</a>.
1. W **obszarze Konfigurowanie domeny niestandardowej wybierz** pozycję **ViewManageAdd** **domain (Domena ViewManageAdd** >  > ).
1. Wprowadź nową nazwę domeny, którą chcesz dodać, a następnie wybierz pozycję **Dalej**.
1. Zaloguj się do rejestratora domen, a następnie wybierz pozycję **Dalej**.
1. Wybierz usługi dla nowej domeny.
1. Wybierz **pozycję** **NextAuthorizeNext** >  > , **a następnie zakończ**. Twoja nowa domena została dodana.

## <a name="add-a-domain"></a>Dodawanie domeny

Wykonaj poniższe czynności, aby dodać, skonfigurować lub kontynuować konfigurowanie domeny. 

::: moniker range="o365-worldwide"

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. Przejdź do **strony Ustawienia** >  **Domains**. 

3. Wybierz **pozycję Dodaj domenę**.
    
4. Wprowadź nazwę domeny, którą chcesz dodać, a następnie wybierz pozycję **Dalej**.
    
5. Wybierz sposób weryfikacji, że jesteś właścicielem domeny.
    
    1. Jeśli rejestrator domeny [korzysta z Połączenie](#domain-connect-registrars-integrating-with-microsoft-365) domeny, [firma Microsoft automatycznie](../get-help-with-domains/domain-connect.md) skonfiguruje rekordy przez zalogowanie się u rejestratora i potwierdzenie połączenia z usługą Microsoft 365. Powrócisz do centrum administracyjnego, a firma Microsoft automatycznie zweryfikuje Twoją domenę.
    2. Możesz użyć rekordu TXT w celu weryfikacji domeny. Zaznacz tę pozycję, a następnie wybierz pozycję **Dalej** , aby wyświetlić instrukcje dotyczące dodawania tego rekordu DNS w witrynie internetowej rejestratora. Weryfikacja po dodaniu rekordu może potrwać do 30 minut. 
    3. Możesz dodać plik tekstowy do witryny internetowej swojej domeny. Wybierz i pobierz .txt z kreatora konfiguracji, a następnie przekaż plik do folderu najwyższego poziomu witryny sieci Web. Ścieżka do pliku powinna wyglądać podobnie do: `http://mydomain.com/ms39978200.txt`. Potwierdzimy, że jesteś właścicielem domeny, znajdując plik w witrynie internetowej.
    
6. Wybierz sposób, w jaki firma Microsoft ma wprowadzać zmiany w systemie DNS wymagane do używania Twojej domeny.
    
    1. Wybierz **pozycję Dodaj rekordy DNS**, jeśli rejestrator obsługuje usługę [Domain Połączenie, a](#domain-connect-registrars-integrating-with-microsoft-365) [firma Microsoft automatycznie](../get-help-with-domains/domain-connect.md) skonfiguruje rekordy przez zalogowanie się u rejestratora i potwierdzenie połączenia z usługą Microsoft 365.
    2. Wybierz **pozycję Dodam rekordy DNS** samodzielnie, jeśli chcesz dołączyć do domeny tylko konkretne usługi Microsoft 365 lub jeśli chcesz pominąć ten krok na razie i zrobić to później. **Wybierz tę opcję tylko, jeśli wiesz dokładnie, co chcesz zrobić.**

7. Jeśli samodzielnie dodasz rekordy *DNS*  , wybierz pozycję **Dalej** . Zostanie wyświetlony adres strony ze wszystkimi rekordami, które musisz dodać w witrynie internetowej rejestratora w celu skonfigurowania domeny. 

    Jeśli Twój rejestrator nie został rozpoznany w portalu, możesz [skorzystać z tych instrukcji ogólnych](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
    
    Jeśli nie znasz dostawcy hostingu DNS lub rejestratora domen dla swojej domeny, zobacz [Znajdowanie rejestratora domen lub dostawcy hostingu DNS](../get-help-with-domains/find-your-domain-registrar.md).
    
    Jeśli chcesz zaczekać na później, usuń zaznaczenie wszystkich usług i kliknij przycisk **Kontynuuj** lub w poprzednim kroku połączenia domeny wybierz pozycję **Więcej** opcji i wybierz **pozycję Pomiń ten na razie**.
    
8. Wybierz **pozycję** Zakończ — to już wszystko!

## <a name="add-or-edit-custom-dns-records"></a>Dodawanie i edytowanie niestandardowych rekordów DNS

Wykonaj poniższe czynności, aby dodać rekord niestandardowy dla witryny internetowej lub usługi innej firmy.

1. Zaloguj się do centrum administracyjnego firmy Microsoft w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Przejdź do **strony Ustawienia**  >  **Domains**.

3. Na stronie **Domeny** wybierz domenę. 
    
4. W **obszarze Ustawienia DNS** wybierz pozycję **Rekordy niestandardowe**. a następnie wybierz **pozycję Nowy rekord niestandardowy**.

5. Wybierz typ rekordu DNS, który chcesz dodać, a następnie wpisz informacje dotyczące nowego rekordu.
    
6. Wybierz **Zapisz**.

## <a name="registrars-with-domain-connect"></a>Rejestratorzy z domenami Połączenie

[Rejestratorzy Połączenie](https://www.domainconnect.org/) domen umożliwiają dodanie domeny Microsoft 365 w trójetapowym procesie, który trwa kilka minut. 
  
W kreatorze potwierdzimy, że jesteś właścicielem domeny, i automatycznie skonfigurujemy rekordy domeny, aby poczta e-mail przychodziła do usługi Microsoft 365 i innych usług Microsoft 365, takich jak Teams, działały z Twoją domeną.
  
> [!NOTE]
> Przed uruchomieniem kreatora konfiguracji upewnij się, że wyłączono wszystkie programy blokujące wyskakiwanie okienek w przeglądarce.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Rejestratorzy Połączenie domen integrując się z usługą Microsoft 365

- [11&amp; IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Wołosk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer lub WildWestDomains (odsprzedawcy w witrynie GoDaddy korzystający z hostingu DNS bezpiecznego serwera)
    - Przykłady:
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>Co się stanie z moją pocztą e-mail i witryną internetową?

Po zakończeniu konfiguracji rekord MX domeny zostanie zaktualizowany tak, aby Microsoft 365 wiadomości e-mail dla Twojej domeny zaczną przychodzić do Microsoft 365. Upewnij się, że dodano użytkowników i skonfigurujemy skrzynki pocztowe w aplikacji Microsoft 365 dla wszystkich osób korzystających z poczty e-mail w tej domenie.
  
Jeśli masz witrynę internetową dla swojej firmy, będzie ona nadal działać tam, gdzie dotychczas. Kroki konfiguracji Połączenie domeny nie mają wpływu na Twoją witrynę internetową.

### <a name="add-an-onmicrosoftcom-domain"></a>Dodawanie domeny onmicrosoft.com domeny

Każda Microsoft 365 organizacji może mieć maksymalnie trzy onmicrosoft.com domeny.

> [!NOTE]
> Aby dodać domenę, musisz być administratorem globalnym lub administratorem nazwy domeny.
> Utworzenie dodatkowej domeny .onmicrosoft i użycie jej jako domyślnej nie spowoduje zmiany nazwy dla domeny SharePoint Online. Aby wprowadzić zmiany w domenie .onmicrosoft SharePoint, musisz użyć wersji Preview zmiany nazwy domeny [SharePoint](/sharepoint/change-your-sharepoint-domain-name) (obecnie dostępnej dla dowolnej dzierżawy z mniej niż 1000 witrynami).
> Jeśli korzystasz z Microsoft 365 poczty e-mail, usunięcie początkowej domeny .onmicrosoft nie jest obsługiwane.


Aby dodać domenę onmicrosoft.com:

1. Przejdź do centrum administracyjnego firmy Microsoft, **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.

2. Na karcie **Omówienie** wybierz pozycję **Dodaj onmicrosoft.com domeny**.

Jako domenę domyślną możesz ustawić dowolną posiadaną domenę.

## <a name="related-content"></a>Zawartość pokrewna

[Domeny — często](domains-faq.yml) zadawane pytania (artykuł)</br>
[Co to jest domena?](../get-help-with-domains/what-is-a-domain.md) (article)</br>
[Kupowanie nazwy domeny w Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (artykuł)</br>
[Dodawanie rekordów DNS w celu połączenia domeny](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (artykuł)</br>
[Zmienianie serwerów nazw w celu skonfigurowania Microsoft 365 rejestratora domen](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (artykuł)
