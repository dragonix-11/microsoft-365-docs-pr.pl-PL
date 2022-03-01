---
title: Uproszczony proces konfiguracji w programie Microsoft Defender dla firm (wersja Preview)
description: Dowiedz się więcej o uproszczonym procesie konfiguracji w programie Microsoft Defender dla firm (wersja Preview)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 1bd11102636696f7aafe781af6d16ae078212d8a
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016548"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business-preview"></a>Uproszczony proces konfiguracji w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Program Microsoft Defender dla firm (wersja Preview) oferuje uproszczony proces konfiguracji opracowany specjalnie dla małych i średnich firm. To środowisko pozwala odgadnąć wszystkie przypuszczenia dotyczące dołączania urządzeń i zarządzania nimi, dzięki użyciu środowiska przypominającego kreatora oraz domyślnych zasad, które od pierwszego dnia są przeznaczone do ochrony urządzeń w Twojej organizacji. **Zalecamy skorzystanie z uproszczonego procesu konfiguracji, jednak nie trzeba się ograniczać do tej opcji**.

Jeśli chodzi o dołączanie urządzeń i konfigurowanie ustawień zabezpieczeń dla urządzeń organizacji, możesz wybrać jeden z kilku sposobów: 

- Uproszczony proces konfiguracji w programie Microsoft Defender dla firm (wersja Preview) (*zalecane*) 
- Microsoft Endpoint Manager, która obejmuje Microsoft Intune
- Rozwiązanie firmy inne niż Microsoft do zarządzania urządzeniami 

## <a name="what-to-do"></a>Co należy zrobić

1. [Przeglądanie opcji konfiguracji i konfiguracji](#review-your-setup-and-configuration-options)
2. [Dowiedz się więcej o uproszczonym procesie konfiguracji w programie Defender dla firm (wersja Preview)](#why-we-recommend-using-the-simplified-configuration-process)
3. [Przejdź do następnych kroków](#next-steps)

## <a name="review-your-setup-and-configuration-options"></a>Przeglądanie opcji konfiguracji i konfiguracji

W poniższej tabeli opisano poszczególne środowisko:
<br/><br/>

| Środowisko portalu  | Opis  |
|---------|---------|
| Uproszczona konfiguracja w portalu Microsoft 365 Defender sieci ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Jest to opcja zalecana dla większości klientów*)  | Uproszczona konfiguracja obejmuje domyślne ustawienia i zasady zabezpieczeń, które pomagają chronić urządzenia od pierwszego dnia w organizacji. Dzięki temu doświadczeniu twój zespół zabezpieczeń używa portalu Microsoft 365 Defender w celu: <br/>- Konfigurowanie i konfigurowanie programu Defender dla firm (wersja Preview) <br/>— Wyświetlanie zdarzeń i zarządzanie nimi<br/>— Reagowanie na zagrożenia i ograniczanie ich<br/>— Wyświetlanie raportów<br/>— Przeglądanie oczekujących lub ukończonych akcji <br/><br/> Ten portal to centrum informacji o ustawieniach zabezpieczeń i funkcji ochrony przed zagrożeniami w organizacji. Uproszczony interfejs ułatwiający szybkie i wydajne rozpoczynanie pracy.  Możesz też edytować ustawienia lub definiować nowe zasady odpowiednio do potrzeb organizacji.<br/><br/>Aby dowiedzieć się więcej, [zobacz Wyświetlanie i edytowanie zasad urządzenia w programie Microsoft Defender dla firm (wersja Preview).](mdb-view-edit-policies.md) |
| Centrum Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Endpoint Manager to Microsoft Intune firmy Microsoft Intune zarządzanie oparte na chmurze urządzeniami przenośnymi (MDM) i dostawcą zarządzania aplikacjami mobilnymi (MAM) dla aplikacji i urządzeń. <br/><br/>Wiele organizacji korzysta z usługi Intune do zarządzania swoimi urządzeniami, takimi jak telefony komórkowe, tablety i laptopy. Aby dowiedzieć się więcej, [zobacz Microsoft Intune jest dostawcą usługi MDM i mam dla Twoich urządzeń](/mem/intune/fundamentals/what-is-intune). <br/><br/>Jeśli korzystasz już z Microsoft Intune lub Microsoft Endpoint Manager, możesz nadal korzystać z tego rozwiązania. |
| Twoje rozwiązanie do zarządzania urządzeniami innych niż firmy Microsoft  | Jeśli używasz rozwiązania firmy innego niż Microsoft do zarządzania wydajnością i urządzeniami, takiego jak Jamf dla systemu macOS lub Ansible dla systemu Linux, możesz nadal używać tego rozwiązania z programem Defender dla firm (wersja Preview). <br/><br/>Po dojechi urządzenia do usługi Defender dla firm (wersja Preview) ich status i alerty będą dostępne w portalu Microsoft 365 Defender firmowym. Aby dowiedzieć się więcej, zobacz Opcje narzędzia do [dołączania i konfiguracji dla programu Defender dla punktu końcowego](../defender-endpoint/onboard-configure.md).<br/><br/>Jeśli używasz już rozwiązania do zarządzania urządzeniami innych niż firmy Microsoft, możesz kontynuować korzystanie z tego rozwiązania. |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Dlaczego zalecamy korzystanie z uproszczonego procesu konfiguracji

**Zaleca się stosowanie uproszczonego procesu konfiguracji w programie Microsoft Defender dla firm (wersja Preview)** dla większości klientów. Uproszczony proces konfiguracji został usprawniony, zwłaszcza dla małych i średnich firm. Pierwszy dzień programu Defender dla firm (wersja Preview) ma na celu pomoc w ochronie urządzeń organizacji bez konieczności wytłaniania specjalistycznej wiedzy technicznej i wiedzę specjalną. Dzięki domyślnym zasadom i ustawieniam zabezpieczeń urządzenia są chronione od razu po ich dojechu.


Program Defender dla firm (wersja Preview) został zaprojektowany z myślą o zapewnianiu silnej ochrony, co pozwala zaoszczędzić czas i wysiłku podczas konfigurowania ustawień zabezpieczeń. Usprawnione środowisko w portalu Microsoft 365 Defender ułatwia urządzenia mobilne i zarządzanie nimi. Ponadto uwzględniane są zasady domyślne, dzięki czemu urządzenia organizacji są chronione od razu po ich dokładzie. Możesz zachować ustawienia domyślne bez zmian lub wprowadzić zmiany odpowiednio do potrzeb biznesowych. Możesz również dodać nowe zasady, aby zarządzać urządzeniami zgodnie z potrzebami.

## <a name="next-steps"></a>Następne kroki

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

- [Konfigurowanie i konfigurowanie programu Microsoft Defender dla firm (wersja Preview)](mdb-setup-configuration.md)

- [Wprowadzenie do korzystania z usługi Microsoft Defender dla firm (wersja Preview)](mdb-get-started.md)