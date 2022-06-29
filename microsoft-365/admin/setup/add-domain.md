---
title: Dodawanie domeny do platformy Microsoft 365
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
- adminvideo
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
description: Kreator instalacji umożliwia dodanie domeny do usługi Microsoft 365 w Centrum administracyjne platformy Microsoft 365 przez dodanie rekordu DNS na hoście DNS.
ms.openlocfilehash: 64b82aab051af2c9d5444042f27009b4e02f1ad8
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492043"
---
# <a name="add-a-domain-to-microsoft-365"></a>Dodawanie domeny do platformy Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
  
## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby dodawać, modyfikować lub usuwać domeny, **musisz** być **administratorem nazw domen** lub **administratorem globalnym** [planu biznesowego lub korporacyjnego](https://products.office.com/business/office). Te zmiany mają wpływ na całą dzierżawę; *Administratorzy dostosowali* się lub *zwykli użytkownicy* nie będą mogli wprowadzać tych zmian.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą firmy Microsoft ds. małych firm](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej uzyskasz wraz ze swoimi pracownikami całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm potrzebnego w miarę rozwoju Twojej firmy — od dołączania po codzienne użytkowanie.

## <a name="watch-add-a-domain"></a>Obejrzyj: Dodawanie domeny

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Twoja firma może potrzebować wielu nazw domen do różnych celów. Możesz na przykład dodać inną pisownię nazwy firmy, ponieważ klienci już z niej korzystają, a ich komunikacja nie dotarła do Ciebie.

1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Konfiguracja**</a>.
1. W obszarze **Pobierz konfigurację domeny niestandardowej** wybierz pozycję **Wyświetl** > **zarządzanie** > **dodawaniem domeny**.
1. Wprowadź nową nazwę domeny, którą chcesz dodać, a następnie wybierz pozycję **Dalej**.
1. Zaloguj się do rejestratora domen, a następnie wybierz pozycję **Dalej**.
1. Wybierz usługi dla nowej domeny.
1. Wybierz pozycję **Dalej** > **autoryzuj** > **dalej**, a następnie **pozycję Zakończ**. Nowa domena została dodana.

## <a name="add-a-domain"></a>Dodawanie domeny

Wykonaj następujące kroki, aby dodać, skonfigurować lub kontynuować konfigurowanie domeny. 

::: moniker range="o365-worldwide"

1. Przejdź do centrum administracyjnego w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Przejdź do centrum administracyjnego w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. Przejdź do strony **Domeny ustawień** > . 

3. Wybierz pozycję **Dodaj domenę**.
    
4. Wprowadź nazwę domeny, którą chcesz dodać, a następnie wybierz pozycję **Dalej**.
    
5. Wybierz sposób sprawdzania, czy jesteś właścicielem domeny.
    
    1. Jeśli rejestrator domen korzysta z programu [Domain Connect](#domain-connect-registrars-integrating-with-microsoft-365), firma Microsoft [automatycznie skonfiguruje rekordy](../get-help-with-domains/domain-connect.md) po zalogowaniu się do rejestratora i potwierdzeniu połączenia z usługą Microsoft 365. Nastąpi powrót do centrum administracyjnego, a następnie firma Microsoft automatycznie zweryfikuje Twoją domenę.
    2. Możesz użyć rekordu TXT w celu weryfikacji domeny. Wybierz tę pozycję i wybierz pozycję **Dalej** , aby wyświetlić instrukcje dotyczące dodawania tego rekordu DNS do witryny internetowej rejestratora. Weryfikacja może potrwać do 30 minut po dodaniu rekordu. 
    3. Możesz dodać plik tekstowy do witryny internetowej domeny. Wybierz i pobierz plik .txt z kreatora konfiguracji, a następnie przekaż go do folderu najwyższego poziomu witryny internetowej. Ścieżka do pliku powinna wyglądać podobnie do: `http://mydomain.com/ms39978200.txt`. Potwierdzimy, że jesteś właścicielem domeny, znajdując plik w witrynie internetowej.
    
6. Wybierz sposób wprowadzania zmian DNS wymaganych przez firmę Microsoft do korzystania z Twojej domeny.
    
    1. Wybierz **pozycję Dodaj rekordy DNS dla mnie** , jeśli rejestrator obsługuje usługę [Domain Connect](#domain-connect-registrars-integrating-with-microsoft-365), a firma Microsoft [automatycznie skonfiguruje rekordy](../get-help-with-domains/domain-connect.md) po zalogowaniu się do rejestratora i potwierdzeniu połączenia z usługą Microsoft 365.
    2. Wybierz **pozycję Sam dodam rekordy DNS** , jeśli chcesz dołączyć tylko określone usługi Platformy Microsoft 365 do domeny lub jeśli chcesz pominąć to na razie i zrobić to później. **Wybierz tę opcję tylko, jeśli wiesz dokładnie, co chcesz zrobić.**

7. Jeśli *wybierzesz opcję samodzielnego dodawania rekordów DNS*  , wybierz pozycję **Dalej** , a zobaczysz stronę ze wszystkimi rekordami, które należy dodać do witryny internetowej rejestratorów w celu skonfigurowania domeny. 

    Jeśli Twój rejestrator nie został rozpoznany w portalu, możesz [skorzystać z tych instrukcji ogólnych](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
    
    Jeśli nie znasz dostawcy hostingu DNS lub rejestratora domen dla swojej domeny, zobacz [Znajdowanie rejestratora domen lub dostawcy hostingu DNS](../get-help-with-domains/find-your-domain-registrar.md).
    
    Jeśli chcesz poczekać na później, usuń zaznaczenie wszystkich usług i kliknij przycisk **Kontynuuj** lub w poprzednim kroku połączenia z domeną wybierz pozycję **Więcej opcji** i wybierz pozycję **Pomiń to na razie**.
    
8. Wybierz pozycję **Zakończ** — gotowe!

## <a name="add-or-edit-custom-dns-records"></a>Dodawanie i edytowanie niestandardowych rekordów DNS

Wykonaj poniższe kroki, aby dodać rekord niestandardowy dla witryny internetowej lub usługi innej firmy.

1. Zaloguj się do centrum administracyjnego firmy Microsoft pod adresem <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Przejdź do strony **Domeny ustawień**  > .

3. Na stronie **Domeny** wybierz domenę. 
    
4. W obszarze **Ustawienia DNS** wybierz pozycję **Rekordy niestandardowe**; następnie wybierz pozycję **Nowy rekord niestandardowy**.

5. Wybierz typ rekordu DNS, który chcesz dodać, i wpisz informacje dotyczące nowego rekordu.
    
6. Wybierz **Zapisz**.

## <a name="registrars-with-domain-connect"></a>Rejestratorzy z połączeniem z domeną

[Rejestratorzy](https://www.domainconnect.org/) z obsługą połączenia z domeną umożliwiają dodawanie domeny do platformy Microsoft 365 w trzyetapowym procesie, który trwa kilka minut. 
  
W kreatorze po prostu potwierdzimy, że jesteś właścicielem domeny, a następnie automatycznie skonfigurujemy rekordy domeny, więc wiadomość e-mail zostanie przesłana do platformy Microsoft 365 i innych usług platformy Microsoft 365, takich jak Teams, do pracy z domeną.
  
> [!NOTE]
> Przed uruchomieniem kreatora konfiguracji upewnij się, że wyłączono wszystkie programy blokujące wyskakiwanie okienek w przeglądarce.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Rejestratorzy usługi Domain Connect integrujący się z platformą Microsoft 365

- [1&amp;1 IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [Mediatemple](https://mediatemple.net/)
- SecureServer lub WildWestDomains (odsprzedawcy GoDaddy korzystający z hostingu DNS SecureServer)
    - Przykłady:
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>Co się stanie z moją pocztą e-mail i witryną internetową?

Po zakończeniu konfiguracji rekord MX dla twojej domeny zostanie zaktualizowany tak, aby wskazywał usługę Microsoft 365, a wszystkie wiadomości e-mail dla Twojej domeny zaczną pojawiać się na platformie Microsoft 365. Upewnij się, że dodano użytkowników i skonfigurowano skrzynki pocztowe w usłudze Microsoft 365 dla wszystkich osób, które otrzymają wiadomość e-mail w Twojej domenie.
  
Jeśli masz witrynę internetową dla swojej firmy, będzie ona nadal działać tam, gdzie dotychczas. Kroki konfiguracji połączenia z domeną nie mają wpływu na witrynę internetową.

### <a name="add-an-onmicrosoftcom-domain"></a>Dodawanie domeny onmicrosoft.com

Każda organizacja platformy Microsoft 365 może mieć maksymalnie pięć onmicrosoft.com domen.

> [!NOTE]
> Aby dodać domenę, musisz być administratorem globalnym lub administratorem nazwy domeny.
> Utworzenie dodatkowej domeny .onmicrosoft i użycie jej jako domyślnej nie spowoduje zmiany nazwy usługi SharePoint Online. Aby wprowadzić zmiany w domenie programu SharePoint firmy .onmicrosoft, należy użyć [wersji zapoznawczej zmiany nazwy domeny programu SharePoint](/sharepoint/change-your-sharepoint-domain-name) (obecnie dostępnej dla dowolnej dzierżawy z mniej niż 1000 witrynami).
> Jeśli używasz usług poczty microsoft 365, usunięcie początkowej domeny .onmicrosoft nie jest obsługiwane.


Aby dodać domenę onmicrosoft.com:

1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia**, a następnie wybierz pozycję **Domeny**.

2. Wybierz istniejącą domenę *onmicrosoft.com* .

    ![Strona Domeny.](../../media/onmicrosoft-domains.png)
  

3. Na karcie **Przegląd** wybierz pozycję **Dodaj domenę onmicrosoft.com**.

    ![Zrzut ekranu przedstawiający właściwości domeny.](../../media/add-onmicrosoft-domain-link.png)

4. Na stronie **Dodawanie domeny onmicrosoft** w polu **Nazwa domeny** wprowadź nazwę nowej domeny onmicrosoft.com. 

    ![Zrzut ekranu przedstawiający pozycję Dodaj domenę onmicrosoft.](../../media/add-an-onmicrosoftcom-domain-page.png)

    > [!NOTE]
    > Sprawdź pisownię i dokładność wprowadzonej nazwy domeny. Masz ograniczoną liczbę onmicrosoft.com domen i obecnie nie można ich usunąć po ich utworzeniu.     

5. Wybierz pozycję **Dodaj domenę**. Po pomyślnym dodaniu zostanie wyświetlony komunikat z informacją o tym. 
    
    ![Zrzut ekranu przedstawiający pomyślnie dodawaną domenę.](../../media/domain-added.png)

Jako domenę domyślną możesz ustawić dowolną domenę, którą posiadasz. 

Aby uzyskać więcej informacji na temat dodawania domeny onmicrosoft.com, zobacz [Dodawanie lub zastępowanie domeny onmicrosoft.com](add-or-replace-your-onmicrosoftcom-domain.md).

## <a name="related-content"></a>Zawartość pokrewna

[Domeny — często zadawane pytania](domains-faq.yml) (artykuł)</br>
[Co to jest domena?](../get-help-with-domains/what-is-a-domain.md) (artykuł)</br>
[Kupowanie nazwy domeny na platformie Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (artykuł)</br>
[Dodawanie rekordów DNS w celu nawiązania połączenia z domeną](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (artykuł)</br>
[Zmienianie serwerów nazw w celu skonfigurowania platformy Microsoft 365 z dowolnym rejestratorem domen](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (artykuł)
