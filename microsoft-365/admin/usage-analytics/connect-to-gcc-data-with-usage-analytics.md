---
title: Połączenie dane Microsoft 365 Government Community Cloud (GCC) za pomocą analizy użycia
f1.keywords:
- CSH
ms.author: efrene
author: efrene
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Dowiedz się, jak nawiązać połączenie z danymi Microsoft 365 Government Community Cloud dzierżawie usługi (GCC) przy użyciu aplikacji szablonu analizy Microsoft 365 w aplikacji Power BI.
ms.openlocfilehash: 3930ffe82c998797aade84e92145adac5fa2ea98
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985240"
---
# <a name="connect-to-microsoft-365-government-community-cloud-gcc-data-with-usage-analytics"></a>Połączenie dane Microsoft 365 Government Community Cloud (GCC) za pomocą analizy użycia

Skorzystaj z poniższych procedur, aby połączyć się z danymi za pomocą raportu analizy Microsoft 365 użycia w dzierżawie usługi Microsoft 365 Government Community Cloud (GCC). 

> [!NOTE]
> Te instrukcje są przeznaczone specjalnie Microsoft 365 GCC dzierżaw. 

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby wstępnie skonfigurować analizę Microsoft 365 użycia: 

- Aby włączyć zbieranie danych, Microsoft 365 administrator globalny. 
- Do [używania pliku Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) potrzebujesz aplikacji szablonu. 
- Do publikowania [i Power BI Pro wyświetlania raportu](https://go.microsoft.com/fwlink/p/?linkid=845347) Premium potrzebujesz licencji lub licencji. 

## <a name="step-1-make-you-organizations-data-available-for-the-microsoft-365-usage-analytics-report"></a>Krok 1. Udostępnij dane organizacji do raportu analizy Microsoft 365 użycia

1. W centrum administracyjne platformy Microsoft 365 nawigacji rozwiń menu nawigacji, wybierz pozycję **Raporty**, a następnie wybierz pozycję **Użycie**. 
2. Na stronie **Raporty** użycia w sekcji Analiza Microsoft 365 użycia **wybierz pozycję Wprowadzenie**. 
3. W **obszarze Power BI analizy** użycia zaznacz pole wyboru Udostępnij dane użycia organizacji do analizy użycia firmy Microsoft dla Power BI, **a** następnie wybierz pozycję **Zapisz**.

    ![Udostępnij dane dzierżawy.](../../media/usage-analytics/make-data-available.png) 



    Spowoduje to rozpoczęcie procesu tworzenia danych organizacji z ułatwieniami dostępu do tego raportu i pojawi się komunikat o przygotowaniu danych do analizy użycia Microsoft 365 **użycia**. Pamiętaj, że ten proces może potrwać 24 godziny. 

4. Gdy dane organizacji będą gotowe, odświeżenie strony spowoduje pokazanie komunikatu informjącego, że dane są teraz dostępne, oraz numeru **identyfikacyjnego** dzierżawy. Identyfikator dzierżawy trzeba będzie użyć w kolejnym kroku podczas próby nawiązania połączenia z danymi dzierżawy. 
 
    ![Identyfikator dzierżawy.](../../media/usage-analytics/tenant-id-gcc.png) 
 
    > [!IMPORTANT]
    > Gdy twoje dane będą dostępne, nie wybieraj opcji **Przejdź do witryny Power BI**, co spowoduje Power BI Marketplace.  Aplikacja szablonów dla tego raportu wymagana przez GCC nie jest dostępna w witrynie Power BI Marketplace.  


## <a name="step-2-download-the-power-bi-template-connect-to-your-data-and-publish-the-report"></a>Krok 2. Pobieranie szablonu Power BI, łączenie się z danymi i publikowanie raportu

Microsoft 365 GCC użytkownicy mogą pobrać plik szablonu raportu analizy Microsoft 365 i używać go do łączenia się ze swoimi danymi. Plik szablonu Power BI Desktop otworzyć i użyć go. 

 > [!NOTE]
 > Obecnie aplikacja szablonów dla raportu analizy Microsoft 365 użycia nie jest dostępna dla GCC dzierżaw w witrynie Power BI Marketplace.  

1. Po pobraniu [szablonu Power BI](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit) otwórz go przy użyciu Power BI Desktop. 
2. Gdy zostanie wyświetlony monit o podanie identyfikatora **dzierżawy**, wprowadź identyfikator dzierżawy otrzymany podczas przygotowania danych organizacji do tego raportu w kroku 1. Następnie wybierz pozycję **Załaduj**. Załadowanie danych zajmie kilka minut. 

    ![Wprowadź identyfikator dzierżawy.](../../media/usage-analytics/add-tenant-id.png) 



3. Po zakończeniu ładowania zostanie wyświetlony raport z podsumowaniem danych dla kierownictwa. 

    ![Podsumowanie dla kierownictwa.](../../media/usage-analytics/exec-summary.png) 
 

4. Zapisz zmiany w raporcie. 
5. Wybierz **pozycję** Publikuj w menu Power BI Desktop, aby opublikować raport w Power BI online usługi, w której można go wyświetlać. Wymaga to licencji Power BI Pro lub Power BI Premium wydajności. W ramach procesu [publikowania](/power-bi/create-reports/desktop-upload-desktop-files#to-publish-a-power-bi-desktop-dataset-and-reports) należy wybrać miejsce docelowe do publikowania w dostępnym obszarze roboczym w usłudze Power BI Online.

## <a name="related-content"></a>Zawartość pokrewna

[Analiza użycia informacje](usage-analytics.md) </br>
[Uzyskiwanie najnowszej wersji analizy użycia](get-the-latest-version-of-usage-analytics.md) </br>
[Nawigowanie po raportach i korzystanie z nich Microsoft 365 analizy użycia](navigate-and-utilize-reports.md) </br>