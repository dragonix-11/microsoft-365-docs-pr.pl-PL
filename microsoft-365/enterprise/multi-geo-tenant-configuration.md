---
title: Konfiguracja dzierżawy usługi Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: W tym artykule dowiesz się, jak dodać lokalizacje satelitarne i skonfigurować dzierżawę dla usługi Microsoft 365 Multi-Geo.
ms.openlocfilehash: 2a82872e7c917421c0eb418cf0582eb33d2a53c9
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941201"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Konfiguracja dzierżawy usługi Microsoft 365 Multi-Geo

Przed skonfigurowaniem dzierżawy dla usługi Microsoft 365 Multi-Geo upewnij się, że znasz plan dla wielu obszarów [geograficznych platformy Microsoft 365](plan-for-multi-geo.md). Aby wykonać kroki opisane w tym artykule, potrzebujesz listy lokalizacji geograficznych, które chcesz włączyć jako lokalizacje satelitarne, oraz użytkowników testowych, których chcesz aprowizować dla tych lokalizacji.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Dodawanie możliwości obejmujących wiele obszarów geograficznych w planie platformy Microsoft 365 do dzierżawy

Aby korzystać z usługi Microsoft 365 Multi-Geo, potrzebne są _możliwości wielu obszarów geograficznych w planie platformy Microsoft 365_ . Skontaktuj się z zespołem ds. konta, aby dodać ten plan do dzierżawy. Twój zespół ds. konta połączy Cię z odpowiednim specjalistą ds. licencjonowania i skonfiguruje dzierżawę.

Należy pamiętać, że _możliwości wielu obszarów geograficznych w planie platformy Microsoft 365_ to plan usługi na poziomie użytkownika. Potrzebujesz licencji dla każdego użytkownika, którego chcesz hostować w lokalizacji satelitarnej. Możesz dodawać więcej licencji w miarę dodawania użytkowników w lokalizacjach satelitarnych.

Po aprowizacji dzierżawy przy użyciu  _funkcji multi-geo w planie platformy Microsoft 365_ karta **Lokalizacje geograficzne** stanie się dostępna w centrach administracyjnych usługi OneDrive i programu SharePoint.

## <a name="add-satellite-locations-to-your-tenant"></a>Dodawanie lokalizacji satelitarnych do dzierżawy

Musisz dodać lokalizację satelitarną dla każdej lokalizacji geograficznej, w której chcesz przechowywać dane. Dostępne lokalizacje geograficzne są wyświetlane w poniższej tabeli:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

![Zrzut ekranu przedstawiający stronę lokalizacji geograficznych w centrum administracyjnym programu SharePoint.](../media/sharepoint-multi-geo-admin-center.png)

Aby dodać lokalizację satelitarną

1. Otwórz centrum administracyjne programu SharePoint. i przejdź do <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">**obszaru Lokalizacje geograficzne**</a>.

1. Wybierz pozycję **Dodaj lokalizację**.

1. Wybierz lokalizację, którą chcesz dodać, a następnie wybierz pozycję **Dalej**.

1. Wpisz domenę, która ma być używana z lokalizacją geograficzną, a następnie wybierz pozycję **Dodaj**.

1. Wybierz pozycję **Zamknij**.

Aprowizowanie może potrwać od kilku godzin do 72 godzin, w zależności od rozmiaru dzierżawy. Po zakończeniu aprowizacji lokalizacji satelitarnej otrzymasz wiadomość e-mail z potwierdzeniem. Gdy nowa lokalizacja geograficzna pojawi się na mapie w **kolorze niebieskim na karcie Lokalizacje geograficzne** w centrum administracyjnym usługi OneDrive, możesz ustawić preferowaną lokalizację danych użytkowników na tę lokalizację geograficzną.

> [!IMPORTANT]
> Nowa lokalizacja satelity zostanie skonfigurowana z ustawieniami domyślnymi. Pozwoli to skonfigurować tę lokalizację satelitarną zgodnie z potrzebami dotyczącymi zgodności lokalnej.

## <a name="setting-users-preferred-data-location"></a>Ustawianie preferowanej lokalizacji danych użytkowników
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span>

Po włączeniu potrzebnych lokalizacji satelitarnych możesz zaktualizować konta użytkowników, aby korzystały z odpowiedniej preferowanej lokalizacji danych. Zalecamy ustawienie preferowanej lokalizacji danych dla każdego użytkownika, nawet jeśli ten użytkownik pozostaje w centralnej lokalizacji.

> [!IMPORTANT]
> Jeśli preferowana lokalizacja danych użytkownika jest ustawiona na lokalizację, która nie została skonfigurowana jako lokalizacja satelitarna lub lokalizacja centralna, system domyślnie ustawi lokalizację centralną podczas aprowizacji witryn usługi OneDrive i programu SharePoint oraz skrzynek pocztowych grupy.

> [!TIP]
> Zalecamy rozpoczęcie walidacji od użytkownika testowego lub niewielkiej grupy użytkowników przed wdrożeniem wielu obszarów geograficznych w szerszej organizacji.

W usłudze Azure Active Directory (Azure AD) istnieją dwa typy obiektów użytkowników: tylko użytkownicy w chmurze i zsynchronizni użytkownicy. Postępuj zgodnie z odpowiednimi instrukcjami dotyczącymi typu użytkownika.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Synchronizowanie preferowanej lokalizacji danych użytkownika przy użyciu programu Azure AD Connect

Jeśli użytkownicy firmy są synchronizowane z lokalnego systemu usługi Active Directory do usługi Azure AD, ich preferredDataLocation muszą być wypełnione w usłudze AD i zsynchronizowane z usługą Azure AD.

Postępuj zgodnie z procesem [synchronizacji programu Azure Active Directory Connect: skonfiguruj preferowaną lokalizację danych dla zasobów platformy Microsoft 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) , aby skonfigurować synchronizację preferowanej lokalizacji danych z lokalnych usług Active Directory Domain Services (AD DS) do usługi Azure AD.

Zalecamy uwzględnienie ustawienia preferowanej lokalizacji danych użytkownika jako części standardowego przepływu pracy tworzenia użytkowników.

> [!IMPORTANT]
> W przypadku nowych użytkowników bez aprowizowania usługi OneDrive licencja konta i odczekaj co najmniej 48 godzin po zsynchronizowaniu biblioteki PDL użytkownika z usługą Azure AD, aby zmiany zostały propagowane, zanim użytkownik zaloguje się do usługi OneDrive dla Firm. (Ustawienie preferowanej lokalizacji danych przed zalogowaniem użytkownika w celu aprowizowania usługi OneDrive dla Firm gwarantuje, że nowa usługa OneDrive użytkownika zostanie aprowizowana we właściwej lokalizacji).

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Ustawianie preferowanej lokalizacji danych dla użytkowników tylko w chmurze

Jeśli użytkownicy twojej firmy nie są synchronizowane z lokalnego systemu usługi Active Directory z usługą Azure AD, co oznacza, że są tworzone w usłudze Microsoft 365 lub Azure AD, należy ustawić bibliotekę PDL przy użyciu modułu usługi Microsoft Azure Active Directory dla programu Windows PowerShell.

Procedury opisane w tej sekcji wymagają [modułu usługi Microsoft Azure Active Directory dla programu Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Jeśli ten moduł jest już zainstalowany, upewnij się, że został on zaktualizowany do najnowszej wersji.

1. [Połącz się i zaloguj przy](/connect-to-microsoft-365-powershell?view=o365-worldwide#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell&preserve-view=true) użyciu zestawu poświadczeń administratora globalnego dla dzierżawy.

2. Użyj polecenia cmdlet [Set-MsolUser](/powershell/module/msonline/set-msoluser?view=azureadps-1.0&preserve-view=true) , aby ustawić preferowaną lokalizację danych dla każdego z użytkowników. Przykład:

   ```powershell
   Set-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR
   ```

    Możesz sprawdzić, czy preferowana lokalizacja danych została prawidłowo zaktualizowana przy użyciu polecenia cmdlet Get-MsolUser. Przykład:

   ```powershell
   (Get-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation
   ```

![Zrzut ekranu okna programu PowerShell przedstawiający polecenie set-msoluser.](../media/multi-geo-tenant-configuration-image3.png)

Zalecamy uwzględnienie ustawienia preferowanej lokalizacji danych użytkownika jako części standardowego przepływu pracy tworzenia użytkowników.

> [!IMPORTANT]
> W przypadku nowych użytkowników bez aprowizowania usługi OneDrive licencja konta i odczekaj co najmniej 48 godzin po ustawieniu przez użytkownika biblioteki PDL na propagację zmian, zanim użytkownik zaloguje się do usługi OneDrive. (Ustawienie preferowanej lokalizacji danych przed zalogowaniem użytkownika w celu aprowizowania usługi OneDrive dla Firm gwarantuje, że nowa usługa OneDrive użytkownika zostanie aprowizowana we właściwej lokalizacji).

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Aprowizowanie usługi OneDrive i efekt biblioteki PDL

Jeśli użytkownik ma już witrynę usługi OneDrive utworzoną w dzierżawie, ustawienie biblioteki PDL nie spowoduje automatycznego przeniesienia istniejącej usługi OneDrive. Aby przenieść usługę OneDrive użytkownika, zobacz [Przenoszenie geograficzne usługi OneDrive dla Firm](move-onedrive-between-geo-locations.md).

> [!NOTE]
> Usługa Exchange Online automatycznie przenosi skrzynkę pocztową użytkownika w przypadku zmiany identyfikatora PLD, a pole MailboxRegion nie jest już zgodne z kodem geograficznej lokalizacji bazy danych skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz [Administrowanie skrzynkami pocztowymi usługi Exchange Online w środowisku z wieloma lokalizacjami geograficznymi](./administering-exchange-online-multi-geo.md).

Jeśli użytkownik nie ma witryny usługi OneDrive w ramach dzierżawy, usługa OneDrive zostanie dla niego aprowizowana zgodnie z wartością PDL, przy założeniu, że biblioteka PDL dla użytkownika będzie zgodna z jedną z lokalizacji satelitarnych firmy.

## <a name="configuring-multi-geo-search"></a>Konfigurowanie wyszukiwania z wieloma lokalizacjami geograficznymi

Dzierżawa z wieloma lokalizacjami geograficznymi będzie miała funkcje wyszukiwania agregacji, dzięki czemu zapytanie wyszukiwania będzie zwracać wyniki z dowolnego miejsca w dzierżawie.

Domyślnie wyszukiwania z tych punktów wejścia będą zwracać zagregowane wyniki, mimo że każdy indeks wyszukiwania znajduje się w odpowiedniej lokalizacji geograficznej:

- OneDrive dla Firm
- Wkrocz
- Strona główna programu SharePoint
- Centrum wyszukiwania

Ponadto funkcje wyszukiwania wielu geograficznych można skonfigurować dla niestandardowych aplikacji wyszukiwania korzystających z interfejsu API wyszukiwania programu SharePoint.

Zapoznaj [się z artykułem Configure Search for OneDrive for Business Multi-Geo (Konfigurowanie wyszukiwania w usłudze OneDrive dla Firm— wiele obszarów geograficznych](configure-search-for-multi-geo.md) ), aby uzyskać instrukcje, w tym wszelkie ograniczenia i różnice.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Weryfikowanie konfiguracji usługi Microsoft 365 Multi-Geo

Poniżej przedstawiono kilka podstawowych przypadków użycia, które warto uwzględnić w planie weryfikacji przed ogólnym wdrożeniem rozwiązania Microsoft 365 Multi-Geo w firmie. Po zakończeniu tych testów i wszelkich dodatkowych przypadkach użycia, które są istotne dla Twojej firmy, możesz przejść do dodawania użytkowników w początkowej grupie pilotażowej.

**OneDrive dla Firm**:

Wybierz pozycję OneDrive w programie uruchamiania aplikacji platformy Microsoft 365 i upewnij się, że nastąpi automatyczne przekierowanie do odpowiedniej lokalizacji geograficznej dla użytkownika na podstawie biblioteki PDL użytkownika. Usługa OneDrive dla Firm powinna teraz rozpocząć aprowizację w tej lokalizacji. Po aprowizowaniu spróbuj przekazać i pobrać niektóre dokumenty.

**Aplikacja mobilna OneDrive**:

Zaloguj się do aplikacji mobilnej OneDrive przy użyciu poświadczeń konta testowego. Upewnij się, że widzisz pliki usługi OneDrive dla Firm i możesz z nimi korzystać z urządzenia przenośnego.

**Klient synchronizacji usługi OneDrive**:

Upewnij się, że klient synchronizacji usługi OneDrive automatycznie wykrywa lokalizację geograficzną usługi OneDrive dla Firm podczas logowania. Jeśli musisz pobrać klienta synchronizacji, możesz kliknąć pozycję **Synchronizuj** w bibliotece usługi OneDrive.

**Aplikacje pakietu Office**:

Upewnij się, że możesz uzyskać dostęp do usługi OneDrive dla Firm, logując się z poziomu aplikacji pakietu Office, takiej jak Word. Otwórz aplikację pakietu Office i wybierz pozycję "OneDrive — \<TenantName\>". Pakiet Office wykryje lokalizację usługi OneDrive i wyświetli pliki, które można otworzyć.

**Udostępnianie**:

Spróbuj udostępnić pliki usługi OneDrive. Upewnij się, że selektor osób wyświetla wszystkich użytkowników online programu SharePoint niezależnie od ich lokalizacji geograficznej.
