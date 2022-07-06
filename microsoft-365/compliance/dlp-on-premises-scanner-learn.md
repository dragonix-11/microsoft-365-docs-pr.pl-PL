---
title: Dowiedz się więcej na temat lokalnego skanera ochrony przed utratą danych
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Lokalny skaner zapobiegania utracie danych rozszerza monitorowanie działań dotyczących plików i akcji ochronnych dla tych plików na lokalne udziały plików oraz foldery programu SharePoint i biblioteki dokumentów. Pliki są skanowane i chronione przez skaner usługi Azure Information Protection (AIP)
ms.openlocfilehash: 8edf472fe65380b708a833864ccceedadb240191
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629822"
---
# <a name="learn-about-the-data-loss-prevention-on-premises-scanner"></a>Dowiedz się więcej o lokalnym skanerze zapobiegania utracie danych

Skaner lokalny zapobiegania utracie danych jest częścią pakietu funkcji Ochrona przed utratą danych w Microsoft Purview (DLP), których można użyć do odnajdywania i ochrony poufnych elementów w usługach Microsoft 365. Aby uzyskać więcej informacji na temat wszystkich ofert DLP firmy Microsoft, zobacz [Dowiedz się więcej o zapobieganiu utracie danych](dlp-learn-about-dlp.md).

**Lokalny skaner DLP** przeszuka lokalne dane magazynowane w udziałach plików i bibliotekach dokumentów programu SharePoint i folderach dla poufnych elementów, które w przypadku wycieku stanowią zagrożenie dla organizacji lub mogą stanowić zagrożenie naruszenia zasad zgodności. Zapewnia to widoczność i kontrolę, których potrzebujesz, aby upewnić się, że elementy poufne są prawidłowo używane i chronione oraz aby zapobiec ryzykownemu zachowaniu, które może je naruszyć. Lokalny skaner DLP wykrywa poufne informacje przy użyciu [wbudowanych](sensitive-information-type-entity-definitions.md) lub niestandardowych typów [informacji poufnych](create-a-custom-sensitive-information-type.md) , [etykiet poufności](sensitivity-labels.md) lub właściwości pliku. Informacje o tym, co użytkownicy robią z poufnymi elementami, są widoczne w [Eksploratorze aktywności](data-classification-activity-explorer.md) i można wymusić akcje ochronne na tych elementach za pośrednictwem [zasad DLP](create-test-tune-dlp-policy.md).

## <a name="the-dlp-on-premises-scanner-relies-on-azure-information-protection-scanner"></a>Lokalny skaner DLP opiera się na skanerze usługi Azure Information Protection

Lokalny skaner DLP opiera się na pełnej implementacji skanera usługi Azure Information Protection (AIP) do monitorowania, etykietowania i ochrony poufnych elementów. Jeśli nie znasz skanera usługi AIP, zdecydowanie zalecamy zapoznanie się z nim. Zobacz następujące artykuły:

- [Co to jest usługa Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Co to jest skaner ujednoliconego etykietowania usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner)
- [Wymagania dotyczące instalowania i wdrażania skanera ujednoliconego etykietowania usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-prereqs)
- [Samouczek: instalowanie skanera ujednoliconego etykietowania usługi Azure Information Protection (AIP)](/azure/information-protection/tutorial-install-scanner)
- [Konfigurowanie i instalowanie skanera ujednoliconego etykietowania usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install)
- [Klient ujednoliconego etykietowania platformy Azure Information Protection — historia wersji i zasady pomocy technicznej](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)

## <a name="dlp-on-premises-scanner-actions"></a>Akcje lokalnego skanera DLP

Lokalny skaner DLP wykrywa pliki za pomocą jednej z tych czterech metod:

- typy informacji poufnych
- etykiety poufności
- Formatem
- właściwości dokumentu niestandardowego tylko w plikach pakietu Office 

Jeśli wykryty plik stwarza potencjalne ryzyko w przypadku wycieku lub naruszenia zasad zgodności, lokalny skaner DLP może wykonać jedną z tych czterech akcji.

|Akcja |Opis  |
|---------|---------|
|**Zablokuj tym osobom dostęp do pliku przechowywanego w skanerze lokalnym — wszyscy** | W przypadku wymuszania ta akcja blokuje dostęp do wszystkich kont z wyjątkiem właściciela zawartości, ostatniego konta, które zmodyfikowało element, i administratora. Robi to przez usunięcie wszystkich kont z uprawnień NTFS/SharePoint na poziomie pliku z wyjątkiem właściciela pliku, właściciela repozytorium (ustawionego w ustawieniu [Ustaw właściciela repozytorium](/azure/information-protection/deploy-aip-scanner-configure-install#use-a-data-loss-prevention-dlp-policy-public-preview) w zadaniu skanowania zawartości), ostatniego modyfikatora (można zidentyfikować tylko w programie SharePoint) i administratora. Konto skanera ma również uprawnienia do fc w pliku.|
|**Zablokuj tym osobom dostęp do pliku przechowywanego w skanerze lokalnym — blokuj dostęp całej organizacji (publiczny)**    |W przypadku wymuszania ta akcja usuwa identyfikatory **_SID Everyone_*_, _*_NT AUTHORITY\authenticated users_*_i _*_Domain Users_** z listy kontroli dostępu do plików (ACL). Tylko użytkownicy i grupy, którym jawnie przyznano prawa do pliku lub folderu nadrzędnego, będą mogli uzyskać dostęp do pliku.|
|**Ustawianie uprawnień do pliku**|W przypadku wymuszania ta akcja wymusza dziedziczenie uprawnień folderu nadrzędnego przez plik. Ta akcja będzie wymuszana tylko wtedy, gdy uprawnienia do folderu nadrzędnego są bardziej restrykcyjne niż uprawnienia, które znajdują się już w pliku. Jeśli na przykład lista ACL w pliku ma zezwalać tylko **_określonym użytkownikom_*_ i folder nadrzędny jest skonfigurowany do zezwalania* na grupę _ _Użytkownicy_ *domeny_, uprawnienia folderu nadrzędnego nie będą dziedziczone przez plik. To zachowanie można zastąpić, wybierając opcję _* Inherit, nawet jeśli uprawnienia nadrzędne są mniej restrykcyjne**.|
|**Usuwanie pliku z nieprawidłowej lokalizacji**|W przypadku wymuszania ta akcja zastępuje oryginalny plik plikiem wycinka rozszerzeniem .txt i umieszcza kopię oryginalnego pliku w folderze kwarantanny. 

## <a name="whats-different-in-the-on-premises-scanner"></a>Co się różni w skanerze lokalnym

Istnieje kilka dodatkowych pojęć, o których należy pamiętać, zanim przejdziesz do skanera lokalnego.

### <a name="aip-repositories-and-content-scan-jobs"></a>Repozytoria usługi AIP i zadania skanowania zawartości

Musisz utworzyć zadania skanowania zawartości usługi AIP i zidentyfikować repozytoria hostujące pliki, które mają być oceniane przez aparat DLP. Upewnij się, że reguły DLP zostały włączone w utworzonym zadaniu skanowania zawartości usługi AIP.

### <a name="policy-tips"></a>Porady dotyczące zasad

[Porady dotyczące zasad](use-notifications-and-policy-tips.md) nie są dostępne w skanerze lokalnym.


### <a name="viewing-dlp-on-premises-scanner-events"></a>Wyświetlanie lokalnych zdarzeń skanera DLP

Lokalne dane skanera DLP są wyświetlane w [eksploratorze działań](data-classification-activity-explorer.md) Centrum zgodności M365. 

## <a name="next-steps"></a>Następne kroki

Teraz, gdy już wiesz już o lokalnym skanerze DLP, następne kroki to:

1. [Wprowadzenie do lokalnego skanera DLP](dlp-on-premises-scanner-get-started.md)
2. [Korzystanie ze skanera lokalnego DLP](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do lokalnego skanera zapobiegania utracie danych](dlp-on-premises-scanner-get-started.md)
- [Używanie lokalnego skanera zapobiegania utracie danych](dlp-on-premises-scanner-use.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora działań](data-classification-activity-explorer.md)
