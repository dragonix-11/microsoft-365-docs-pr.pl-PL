---
title: Microsoft 365 konfiguracji dzierżawy wielodostępnych lokalizacji geograficznych
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
description: W tym artykule dowiesz się, jak dodawać lokalizacje satelitarne i konfigurować dzierżawcę pod Microsoft 365 multi-Geo.
ms.openlocfilehash: 2bd0db24b364c642255ef2e902abad0495d24337
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568883"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Microsoft 365 konfiguracji dzierżawy wielodostępnych lokalizacji geograficznych

Zanim skonfigurujesz dzierżawę do Microsoft 365 multi-Geo, upewnij się, że został przeczytany temat [Plan Microsoft 365 dla wielu lokalizacji geograficznych](plan-for-multi-geo.md). Aby wykonać czynności opisane w tym artykule, musisz mieć listę lokalizacji geograficznych, które chcesz włączyć jako lokalizacje satelitarne, oraz użytkowników testowych, których obsługę chcesz aprowizować dla tych lokalizacji.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Dodawanie funkcji Multi-Geo Capabilities w planie Microsoft 365 dzierżawy

Do korzystania Microsoft 365 multi-Geo potrzebna jest funkcja _Multi-Geo Capabilities w Microsoft 365_ danych. We współpracy ze swoim zespołem kont dodaj ten plan do dzierżawy. Zespół klienta połączy Cię z odpowiednim specjalistą ds. licencjonowania i skonfiguruje dzierżawę.

Pamiętaj, że _funkcje multi-geo capabilities Microsoft 365_ to plan usług na poziomie użytkownika. Potrzebujesz licencji dla każdego użytkownika, którego chcesz hostować w lokalizacji satelitarnej. W czasie dodawania użytkowników w lokalizacjach satelitarnych możesz dodawać więcej licencji.

Po inicjowaniu obsługi administracyjnej dzierżawy za pomocą funkcji _Multi-Geo Capabilities_ w planie Microsoft 365 karta Lokalizacje geograficzne stanie się dostępna w centrach OneDrive i SharePoint administracyjnym.

## <a name="add-satellite-locations-to-your-tenant"></a>Dodawanie lokalizacji satelitarnych do dzierżawy

Musisz dodać lokalizację satelitarną dla każdej lokalizacji geograficznej, w której chcesz przechowywać dane. Dostępne lokalizacje geograficzne są wyświetlane w poniższej tabeli:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

![Zrzut ekranu przedstawiający stronę lokalizacje geograficzne w centrum SharePoint administracyjnego.](../media/sharepoint-multi-geo-admin-center.png)

Aby dodać lokalizację satelitarną

1. Otwórz SharePoint administracyjne. i przejdź do <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">**pozycji Lokalizacje geograficzne**</a>.

1. Wybierz **pozycję Dodaj lokalizację**.

1. Wybierz lokalizację, którą chcesz dodać, a następnie wybierz pozycję **Dalej**.

1. Wpisz domenę, której chcesz używać z lokalizacją geograficzną, a następnie wybierz pozycję **Dodaj**.

1. Wybierz pozycję **Zamknij**.

Inicjowanie obsługi administracyjnej może potrwać od kilku godzin do 72 godzin w zależności od wielkości Twojej dzierżawy. Po zakończeniu inicjowania obsługi administracyjnej lokalizacji satelitarnej otrzymasz wiadomość e-mail z potwierdzeniem. Gdy nowa lokalizacja geograficzna jest wyświetlana na mapie w kolorze niebieskim  na karcie Lokalizacje geograficzne w centrum administracyjnym programu OneDrive, możesz przejść do ustawienia preferowanej lokalizacji danych użytkowników do tej lokalizacji geograficznej.

> [!IMPORTANT]
> Nowa lokalizacja satelitarna zostanie skonfigurowania z ustawieniami domyślnymi. Umożliwi to skonfigurowanie lokalizacji satelitarnej zgodnie z lokalnymi potrzebami zgodności.

## <a name="setting-users-preferred-data-location"></a>Ustawianie preferowanej lokalizacji danych użytkowników
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span>

Po włączeniu potrzebnych lokalizacji satelitarnych możesz zaktualizować konta użytkowników, aby używać odpowiedniej preferowanej lokalizacji danych. Zalecamy ustawienie preferowanej lokalizacji danych dla każdego użytkownika, nawet jeśli ten użytkownik pozostaje w lokalizacji centralnej.

> [!IMPORTANT]
> Jeśli preferowana lokalizacja danych użytkownika jest ustawiona na lokalizację, która nie została skonfigurowana jako lokalizacja satelitarna lub centralna, system będzie domyślnie lokalizacją centralną podczas inicjowania obsługi administracyjnej witryn OneDrive i SharePoint i skrzynek pocztowych grupy.

> [!TIP]
> Zalecamy rozpoczęcie sprawdzania poprawności od użytkownika testowego lub małej grupy użytkowników przed rozpoczęciem pracy z wieloma lokalizacjami geograficznymi w szerszej organizacji.

W Azure Active Directory (Azure AD) istnieją dwa typy obiektów użytkowników: tylko użytkownicy w chmurze i użytkownicy zsynchronizowani. Należy postępować zgodnie z odpowiednimi instrukcjami dla swojego typu użytkownika.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Synchronizowanie preferowanej lokalizacji danych użytkownika przy użyciu usługi Azure AD Połączenie

Jeśli użytkownicy w firmie są synchronizowane z systemu usługi lokalna usługa Active Directory z usługą Azure AD, ich preferowana lokalizacja_danych musi zostać wypełniona w usłudze AD i zsynchronizowana z usługą Azure AD.

Postępuj zgodnie z procesów Azure Active Directory Połączenie [synchronizacji:](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) Skonfiguruj preferowaną lokalizację danych dla zasobów usługi Microsoft 365, aby skonfigurować preferowaną synchronizację lokalizacji danych z usług domenowych lokalna usługa Active Directory (AD DS) do usługi Azure AD.

Zalecamy, aby w ramach standardowego przepływu pracy tworzenia użytkowników uwzględnić ustawienie preferowanej lokalizacji danych użytkownika.

> [!IMPORTANT]
> W przypadku nowych użytkowników, którzy nie mają OneDrive obsługi administracyjnej, zaimekuj konto i poczekaj co najmniej 48 godzin po zsynchronizowaniu pliku PDL użytkownika z usługą Azure AD, aby zmiany zostały rozpropagowane, zanim użytkownik zaloguje się do usługi OneDrive dla Firm. Ustawienie preferowanej lokalizacji danych przed rozpoczęciem logowania w celu zapewnienia obsługi OneDrive dla Firm zapewnia, że nowa OneDrive użytkownika będzie aprowowana w odpowiedniej lokalizacji.

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Ustawianie preferowanej lokalizacji danych tylko dla użytkowników chmury

Jeśli użytkownicy w firmie nie są synchronizowane z systemu lokalna usługa Active Directory z usługą Azure AD, co oznacza, że są oni utworzeni w usłudze Microsoft 365 lub Azure AD, plik PDL musi zostać ustawiony przy użyciu modułu Microsoft Azure Active Directory dla Windows PowerShell.

Procedury w tej sekcji wymagają modułu [Microsoft Azure Active Directory modułu dla Windows PowerShell moduł.](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0) Jeśli ten moduł jest już zainstalowany, upewnij się, że został zainstalowany do najnowszej wersji.

1. [Połączenie zalogować się](/powershell/connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) przy użyciu zestawu poświadczeń administratora globalnego dla dzierżawy.

2. Użyj polecenia [cmdlet Set-MsolUser](/powershell/msonline/v1/set-msoluser) , aby ustawić preferowaną lokalizację danych dla każdego użytkownika. Przykład:

   ```powershell
   Set-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR
   ```

    Możesz sprawdzić, czy preferowana lokalizacja danych została prawidłowo zaktualizowana, używając polecenia cmdlet Get-MsolUser cmdlet. Przykład:

   ```powershell
   (Get-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation
   ```

![Zrzut ekranu przedstawiający okno programu PowerShell z oknie set-msoluser.](../media/multi-geo-tenant-configuration-image3.png)

Zalecamy, aby w ramach standardowego przepływu pracy tworzenia użytkowników uwzględnić ustawienie preferowanej lokalizacji danych użytkownika.

> [!IMPORTANT]
> W przypadku nowych użytkowników, którzy nie mają OneDrive obsługi administracyjnej, zaimekuj konto i poczekaj co najmniej 48 godzin po skonfigurowaniu pliku PDL użytkownika na propagację zmian, zanim użytkownik zaloguje się do OneDrive. Ustawienie preferowanej lokalizacji danych przed rozpoczęciem logowania w celu zapewnienia obsługi OneDrive dla Firm zapewnia, że nowa OneDrive użytkownika będzie aprowowana w odpowiedniej lokalizacji.

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive inicjowania obsługi administracyjnej i wpływ pliku PDL

Jeśli użytkownik ma już witrynę sieci OneDrive utworzoną w dzierżawie, ustawienie jego pliku PDL nie spowoduje automatycznego przeniesienia istniejącego OneDrive. Aby przenieść dane użytkownika, OneDrive zobacz Przenoszenie [OneDrive dla Firm geolokalizacji](move-onedrive-between-geo-locations.md).

> [!NOTE]
> Exchange Online automatycznie przeniesie skrzynkę pocztową użytkownika, jeśli zmieni się program PLD i region skrzynki pocztowej nie będzie już odpowiadać kodowi lokalizacja geograficzna bazy danych skrzynek pocztowych. Aby uzyskać więcej informacji, zobacz [Administrowanie Exchange Online w środowisku z wieloma lokalizacjami geograficznymi](./administering-exchange-online-multi-geo.md).

Jeśli użytkownik nie ma witryny sieci OneDrive w ramach dzierżawy, program OneDrive będzie jej zapewniany zgodnie z wartością PDL, zakładając, że plik PDL użytkownika jest zgodny z jedną z lokalizacji satelitarnych firmy.

## <a name="configuring-multi-geo-search"></a>Konfigurowanie wyszukiwania wielu lokalizacji geograficznych

Dzierżawa wielowymiarowa będzie mieć zagregowane funkcje wyszukiwania, dzięki którym zapytanie wyszukiwania może zwracać wyniki z dowolnego miejsca w dzierżawie.

Domyślnie wyszukiwania od tych punktów wprowadzania będą zwracać zagregowane wyniki, nawet jeśli każdy indeks wyszukiwania znajduje się w odpowiedniej lokalizacji geograficznej:

- OneDrive dla Firm
- Delve
- SharePoint strona główna
- Centrum wyszukiwania

Ponadto wyszukiwanie w wielu lokalizacjach geograficznych można skonfigurować dla niestandardowych aplikacji wyszukiwania, które używają SharePoint API wyszukiwania.

Zapoznaj się [z tematem Konfigurowanie wyszukiwania OneDrive dla Firm multi-Geo, aby](configure-search-for-multi-geo.md) uzyskać instrukcje dotyczące ograniczeń i różnic.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Sprawdzania poprawności Microsoft 365 wielu lokalizacji geograficznych

Poniżej przedstawiono kilka podstawowych przypadków użycia, które możesz chcieć uwzględnić w planie sprawdzania poprawności przed szerokiego Microsoft 365 dla Twojej firmy przy użyciu wielu lokalizacji geograficznych. Po ukończeniu tych testów i wszystkich dodatkowych przypadków użycia, które są istotne dla Twojej firmy, możesz przejść dalej do dodawania użytkowników w początkowej grupie pilotażowej.

**OneDrive dla Firm**:

Wybierz OneDrive w Microsoft 365 Uruchamianie aplikacji i upewnij się, że jesteś automatycznie przekierowywowany do odpowiedniej lokalizacji geograficznej dla użytkownika na podstawie jego pliku PDL. OneDrive dla Firm rozpocząć inicjowanie obsługi administracyjnej w tej lokalizacji. Po zapewnianiu obsługi administracyjnej spróbuj przekazać i pobrać niektóre dokumenty.

**OneDrive dla urządzeń przenośnych**:

Zaloguj się do OneDrive mobilnej przy użyciu poświadczeń konta testowego. Upewnij się, że widzisz swoje pliki OneDrive dla Firm i możesz interacyjnie z nich korzystać na urządzeniu przenośnym.

**synchronizacja usługi OneDrive klienta**:

Upewnij się, że synchronizacja usługi OneDrive automatycznie wykrywa Twoją lokalizację geograficzną OneDrive dla Firm podczas logowania. Jeśli musisz pobrać klienta synchronizacji, możesz kliknąć pozycję Synchronizuj **w OneDrive** synchronizacji.

**Office aplikacji**:

Upewnij się, że możesz uzyskać OneDrive dla Firm, logując się z aplikacji Office, takiej jak Word. Otwórz aplikację Office i wybierz pozycję "OneDrive – \<TenantName\>". Office wykryje Twoją OneDrive lokalizacji użytkownika i pokaże pliki, które możesz otworzyć.

**Udostępnianie**:

Spróbuj udostępnić OneDrive pliki. Potwierdź, że s picker osób wyświetla wszystkich Twoich SharePoint online niezależnie od ich lokalizacji geograficznej.
