---
title: Dowiedz się Microsoft 365 ochrony przed utratą danych w środowisku lokalnym
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
description: Microsoft 365 ochrony przed utratą danych w środowisku lokalnym obejmuje monitorowanie działań dotyczących plików i akcji zabezpieczających dla tych plików do lokalnych udziałów plików i SharePoint folderów i bibliotek dokumentów. Pliki są skanowane i chronione za pomocą skanera Azure Information Protection (AIP)
ms.openlocfilehash: c696d4c4e8504d07ce69554c6ff52f264b8ba491
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988361"
---
# <a name="learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>Dowiedz się więcej Microsoft 365 ochrony przed utratą danych w środowisku lokalnym

Lokalny skaner firmy Microsoft do ochrony przed utratą danych jest częścią pakietu funkcji ochrony przed utratą danych (DLP, data loss prevention) firmy Microsoft 365, który umożliwia odnajdowanie i chronianie poufnych elementów w Microsoft 365 usługach internetowych. Aby uzyskać więcej informacji na temat wszystkich usług firmy Microsoft w zakresie ochrony przed utratą danych, zobacz [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md).

Skaner lokalny **DLP** przeszukuje lokalne dane w udziałach plików oraz w bibliotekach dokumentów i folderach programu SharePoint pod SharePoint poufnych elementów, które w przypadku wycieków stanowią zagrożenie dla organizacji lub stanowią zagrożenie dla naruszenia zasad zgodności. Zapewnia to widoczność i kontrolę potrzebną do prawidłowego zabezpieczania i zabezpieczania poufnych elementów oraz zapobiegania ryzykownych zachowaniach, które mogłyby je naruszone. Skaner lokalnym DLP wykrywa informacje poufne przy użyciu wbudowanych lub niestandardowych [](sensitive-information-type-entity-definitions.md) typów informacji poufnych [](create-a-custom-sensitive-information-type.md) [, etykiet](sensitivity-labels.md) wrażliwości lub właściwości pliku. Informacje o tym, co użytkownicy robią z poufnymi elementami, są [](data-classification-activity-explorer.md) widoczne w Eksploratorze [aktywności](create-test-tune-dlp-policy.md) i można na ich podstawie wymuszać akcje zabezpieczające.

## <a name="the-dlp-on-premises-scanner-relies-on-azure-information-protection-scanner"></a>Skaner lokalne DLP korzysta ze skanera usługi Azure Information Protection

Skaner lokalnym DLP korzysta z pełnej implementacji skanera Azure Information Protection (AIP) do monitorowania, oznaczania i ochrony poufnych elementów. Jeśli nie znasz skanera AIP, zdecydowanie zalecamy jego zapoznanie się z nim. Zobacz następujące artykuły:

- [Co to jest usługa Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Co to jest ujednolicony skaner etykiet usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner)
- [Wymagania dotyczące instalowania i wdrażania ujednoliconego skanera etykiet usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-prereqs)
- [Samouczek: instalowanie ujednoliconego skanera etykiet usługi Azure Information Protection (AIP)](/azure/information-protection/tutorial-install-scanner)
- [Konfigurowanie i instalowanie ujednoliconego skanera etykiet usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install)
- [Ujednolicony klient etykiet usługi Azure Information Protection — historia wersji i zasady pomocy technicznej](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)

## <a name="dlp-on-premises-scanner-actions"></a>Akcje skanera lokalnego DLP

Program DLP w skanerze lokalnym wykrywa pliki za pomocą jednej z tych czterech metod:

- typy informacji poufnych
- etykiety wrażliwości
- rozszerzenie pliku
- Właściwości dokumentów niestandardowych tylko Office plikach 

Gdy wykryty plik stwarza potencjalne ryzyko, jeśli wycieknie lub naruszenie zasad zgodności, skaner lokalnym DLP może podjąć jedną z tych czterech czynności.

|Akcja |Opis  |
|---------|---------|
|**Blokowanie tym osobom dostępu do pliku przechowywanego w skanerze lokalnym — Wszyscy** | Jeśli to działanie jest wymuszane, ta akcja blokuje dostęp do wszystkich kont oprócz właściciela zawartości, ostatniego konta, które zmodyfikował element i administratora. W tym celu usuwa wszystkie konta z systemu plików NTFS/programu SharePoint uprawnień na poziomie pliku z wyjątkiem właściciela pliku, właściciela repozytorium (ustawionego w ustawieniu Ustaw [](/azure/information-protection/deploy-aip-scanner-configure-install#use-a-data-loss-prevention-dlp-policy-public-preview) właściciela repozytorium w zadaniu skanowania zawartości), ostatniego modyfikatora (można zidentyfikować tylko w programie SharePoint) i administratora. Konto skanera jest również udzielane prawa do fc do pliku.|
|**Blokowanie tym osobom dostępu do pliku przechowywanego w skanerze lokalnym — blokowanie dostępu dla całej organizacji (publiczny)**    |W przypadku wymuszenia ta akcja usuwa identyfikatory **_EVERYONE_*_, _*_NT AUTHORITY\authenticated users_*_, i _*_Domain Users_** (Użytkownicy domeny) z listy kontroli dostępu do plików. Tylko użytkownicy i grupy, którym jawnie przyznano prawa do pliku lub folderu nadrzędnego, będą mogli uzyskać dostęp do pliku.|
|**Ustawianie uprawnień do pliku**|Jeśli ta akcja jest wymuszana, wymusza na pliku dziedziczenie uprawnień swojego folderu nadrzędnego. Domyślnie ta akcja zostanie wymuszona tylko wtedy, gdy uprawnienia w folderze nadrzędnym są bardziej restrykcyjne niż uprawnienia już dostępne w pliku. Jeśli na przykład wartość ACL pliku jest ustawiona tak, aby zezwalać tylko określonym użytkownikom_, a folder nadrzędny jest skonfigurowany do zezwalania na grupę ***_*_Domain Users_ _ (Użytkownicy domeny), uprawnienia do folderu nadrzędnego nie zostaną odziedziczone przez plik *. Możesz zastąpić to zachowanie, wybierając pozycję _* Dziedzicz, nawet jeśli uprawnienia nadrzędne są mniej restrykcyjne**.|
|**Usuwanie pliku z nieprawidłowej lokalizacji**|Jeśli ta akcja zostanie wymuszona, oryginalny plik zostanie zastąpiony rozszerzeniem .txt i umieszcza kopię oryginalnego pliku w folderze kwarantanny. 

## <a name="whats-different-in-the-on-premises-scanner"></a>Co się dzieje w skanerze lokalnym

Istnieje kilka dodatkowych pojęć, o których należy pamiętać przed rozpoczęciem pracy ze skanerem lokalnym.

### <a name="aip-repositories-and-content-scan-jobs"></a>Repozytoria AIP i zadania skanowania zawartości

Musisz utworzyć zadania skanowania zawartości programu AIP i zidentyfikować repozytoria hostują pliki, które mają być oceniane przez aparat DLP. Upewnij się, że w utworzonej zadaniu skanowania zawartości programu AIP zostały włączyć reguły DLP.

### <a name="policy-tips"></a>Porady dotyczące zasad

[Porady dotyczące zasad](use-notifications-and-policy-tips.md) nie są dostępne w skanerze lokalnym.


### <a name="viewing-dlp-on-premises-scanner-events"></a>Wyświetlanie zdarzeń skanera lokalnego DLP

Dane skanera lokalnego DLP można wyświetlić w Eksploratorze aktywności Centrum zgodności usługi [M365](data-classification-activity-explorer.md). 

## <a name="next-steps"></a>Następne kroki

Po instrukcje dotyczące lokalnego skanera DLP należy wykonać następujące czynności:

1. [Wprowadzenie do lokalnego skanera DLP](dlp-on-premises-scanner-get-started.md)
2. [Używanie lokalnego skanera funkcji DLP](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do lokalnego skanera przed utratą danych firmy Microsoft](dlp-on-premises-scanner-get-started.md)
- [Korzystanie ze skanera lokalnego firmy Microsoft do ochrony przed utratą danych](dlp-on-premises-scanner-use.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)