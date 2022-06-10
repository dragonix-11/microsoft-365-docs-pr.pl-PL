---
title: Wybierz pozycję Microsoft Purview Information Protection wbudowane etykietowanie dla Office aplikacji w dodatku Azure Information Protection (AIP)
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Jeśli używasz klienta ujednoliconego etykietowania usługi Azure Information Protection (AIP), zapoznaj się z zaletami używania wbudowanego etykietowania dla aplikacji Office, a nie dodatku AIP.
ms.openlocfilehash: c790ee691e6a72228c865b8cdf9911ee83f4dfd4
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66011597"
---
# <a name="why-choose-built-in-labeling-over-the-aip-add-in-for-office-apps"></a>Dlaczego warto wybrać wbudowane etykietowanie w dodatku AIP dla aplikacji Office

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Jeśli używasz [etykiet poufności](sensitivity-labels.md) w Aplikacje Microsoft 365 na komputerach Windows, możesz użyć etykiet wbudowanych w aplikacje Office lub dodatku z [klienta ujednoliconego etykietowania usługi Azure Information Protection (AIP](/azure/information-protection/rms-client/aip-clientv2)). 

Wbudowane etykietowanie stanowi podstawę [wdrożenia ochrony informacji w usłudze Microsoft Purview](information-protection-solution.md), ponieważ ta technologia etykietowania obejmuje platformy (Windows, macOS, iOS, Android i sieć Web), a także aplikacje i usługi firmy Microsoft i nie tylko. Wbudowane etykietowanie jest również przeznaczone do pracy z innymi funkcjami usługi Microsoft Purview, takimi jak klasyfikacja danych i ochrona przed utratą danych (DLP) w usłudze Microsoft Purview.

Ponieważ wbudowane etykiety nie używają dodatku Office, korzystają z większej stabilności i lepszej wydajności. Obsługują one również najnowsze funkcje usługi Microsoft Purview, takie jak zaawansowane klasyfikatory.

Domyślnie wbudowane etykietowanie jest wyłączone w Office dla aplikacji Windows po zainstalowaniu klienta usługi AIP. To zachowanie domyślne można zmienić, korzystając z instrukcji w poniższej sekcji [Jak wyłączyć dodatek AIP, aby używać wbudowanego etykietowania dla aplikacji Office](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps).

Gdy klient usługi AIP jest zainstalowany, ale wyłączony w aplikacjach Office, pozostałe możliwości klienta usługi AIP pozostają obsługiwane:

- Kliknij prawym przyciskiem myszy opcje w Eksplorator plików, aby użytkownicy stosują etykiety do wszystkich typów plików.

- Przeglądarka wyświetlająca zaszyfrowane pliki dla tekstu, obrazów lub dokumentów PDF.

- Moduł programu PowerShell służący do odnajdywania poufnych informacji w plikach lokalnych oraz stosowania lub usuwania etykiet i szyfrowania z tych plików.

- Skaner służący do odnajdywania poufnych informacji przechowywanych w lokalnych magazynach danych, a następnie opcjonalnie etykietowania tej zawartości.

Aby uzyskać więcej informacji na temat tych możliwości, które rozszerzają etykietowanie poza aplikacje Office, zobacz [Przewodnik administratora klienta ujednoliconego etykietowania usługi Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide) z dokumentacji usługi AIP.

Niezależnie od etykietowania możesz nadal używać modułu [AIPService](/powershell/module/aipservice) PowerShell do zarządzania usługą szyfrowania na poziomie dzierżawy. Na przykład skonfiguruj dostęp superużytkownika, gdy musisz usunąć szyfrowanie na potrzeby odzyskiwania danych, śledzić i odwoływać dokumenty otwierane przez klienta usługi AIP oraz skonfigurować okres ważności licencji użytkowania na potrzeby dostępu w trybie offline. Aby uzyskać więcej informacji, zobacz [Administrowanie ochroną z usługi Azure Information Protection przy użyciu programu PowerShell](/azure/information-protection/administer-powershell).

## <a name="decide-whether-to-use-built-in-labeling-for-office-apps-or-the-aip-add-in"></a>Zdecyduj, czy używać wbudowanego etykietowania dla aplikacji Office, czy dodatku usługi AIP

Teraz, gdy klient usługi AIP jest w [trybie konserwacji](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613), nie zalecamy używania dodatku AIP dla aplikacji Office z następujących powodów:

- Żadne nowe funkcje etykietowania nie będą obsługiwane.
- Dodatki są mniej stabilne, ponieważ mogą powodować konflikt z innymi dodatkami, co może spowodować, że aplikacje Office zawieszają się, ulegają awarii lub automatycznie wyłączają dodatek.
- Jako dodatek działa wolniej i może zostać wyłączony przez użytkowników w celu obejścia wymagań dotyczących etykietowania.
- Wszelkie poprawki błędów będą wymagały ponownej instalacji klienta usługi Azure Information Protection.
- Środowisko etykietowania dla użytkowników nieco różni się od wbudowanych etykiet, które użytkownicy mają na innych urządzeniach (macOS, iOS, Android) i gdy używają Office dla sieci web. Ta różnica może zwiększyć koszty szkoleń i pomocy technicznej.
- Istnieją już nowe funkcje etykietowania Office, które są [obsługiwane tylko przez wbudowane etykietowanie](#features-supported-only-by-built-in-labeling-for-office-apps), a lista cały czas rośnie.

Użyj dodatku usługi AIP dla aplikacji Windows Office tylko wtedy, gdy zostały już wdrożone dla użytkowników i potrzebujesz czasu na migrację ich do wbudowanego etykietowania. Użytkownicy potrzebują też funkcji, która nie jest obsługiwana przez wbudowane etykietowanie. Informacje [o parcie funkcji](#feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps) na tej stronie ułatwiają identyfikację tych funkcji.

## <a name="features-supported-only-by-built-in-labeling-for-office-apps"></a>Funkcje obsługiwane tylko przez wbudowane etykietowanie dla aplikacji Office

> [!NOTE]
> Wiele nowych funkcji etykietowania jest w planowaniu lub opracowywaniu, więc spodziewaj się, że lista w tej sekcji będzie rosnąć wraz z upływem czasu.

Niektóre funkcje są obsługiwane tylko przez wbudowane etykietowanie dla aplikacji Office i nie będą obsługiwane przez dodatek AIP. Obejmują one:

- Do automatycznego i zalecanego etykietowania:
    - Dostęp do inteligentnych usług klasyfikacji, które obejmują [klasyfikatory z możliwością trenowania](classifier-learn-about.md), [dokładne dopasowanie danych (EDM)](sit-learn-about-exact-data-match-based-sits.md) i [nazwane jednostki](named-entities-learn.md)
    - Wykrywanie informacji poufnych jako typ użytkowników
    - W programie Word użytkownicy mogą przeglądać i usuwać zidentyfikowaną zawartość poufną
- [Obsługa plików PDF](sensitivity-labels-office-apps.md#pdf-support)
- W przypadku etykiet, które umożliwiają użytkownikom przypisywanie uprawnień, użytkownicy lub grupy mogą przyznawać różne uprawnienia (odczyt lub zmiana)
- Encrypt-Only wiadomości e-mail
- Widoczność etykiet na pasku stanu
- Obsługa przełączania konta
- Użytkownicy nie mogą wyłączyć etykietowania

Przykład pokazujący, jak użytkownicy mogą przeglądać i opcjonalnie usuwać zidentyfikowaną zawartość poufną w programie Word:

![Numery kart kredytowych zidentyfikowane użytkownikom jako zawartość poufności z opcją usunięcia.](../media/detect-sensitive-content.png)

Aby być na bieżąco z informacjami o dostępności nowych funkcji etykietowania na potrzeby wbudowanego [etykietowania, zobacz Sekcje Nowości w usłudze Microsoft Purview](whats-new.md) i **etykiety poufności** .

## <a name="how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps"></a>Jak wyłączyć dodatek AIP, aby używać wbudowanego etykietowania dla aplikacji Office

Po zainstalowaniu klienta usługi AIP w celu rozszerzenia etykietowania poza aplikacje Office, ale chcesz uniemożliwić ładowanie dodatków klienta w aplikacjach Office, użyj ustawienia zasady grupy **Lista zarządzanych dodatków**, jak opisano w temacie [Brak załadowania dodatków z powodu ustawień zasad grupy dla programów Office 2013 i Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

W przypadku aplikacji Windows Office, które obsługują wbudowane etykietowanie, użyj konfiguracji dla Microsoft Word 2016 r., Excel 2016, PowerPoint 2016 i Outlook 2016, określ następujące identyfikatory programowe (ProgID) dla klienta usługi AIP i ustaw opcję na **0: Dodatek jest zawsze wyłączony (zablokowany)**

|Aplikacja  |Progid  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

Wdróż to ustawienie przy użyciu zasady grupy lub przy użyciu [usługi zasad w chmurze Office](/DeployOffice/overview-office-cloud-policy-service).

> [!IMPORTANT]
> Jeśli używasz ustawienia zasady grupy **Użyj funkcji poufności w Office, aby zastosować i wyświetlić etykiety poufności** i ustawić tę wartość na **1**, w niektórych sytuacjach dodatek AIP może nadal ładować się w aplikacjach Office. Blokowanie ładowania dodatku w każdej aplikacji zapobiega temu.

Możesz też interaktywnie wyłączyć lub usunąć **dodatek Microsoft Azure Information Protection** Office z programu Word, Excel, PowerPoint i Outlook. Ta metoda jest odpowiednia dla pojedynczego komputera i testowania ad hoc. Aby uzyskać instrukcje, zobacz [Wyświetlanie dodatków, zarządzanie nimi i instalowanie ich w programach Office](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d).

Niezależnie od wybranej metody zmiany zostaną wprowadzone po ponownym uruchomieniu aplikacji Office.

> [!NOTE]
> Wbudowane etykiety wymagają wersji subskrypcji Office aplikacji. Jeśli masz autonomiczne wersje Office, czasami nazywane "Office Perpetual", zalecamy uaktualnienie do Aplikacje Microsoft 365, aby Enterprise korzystać z [najnowszych możliwości etykietowania](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Pamiętaj, że jeśli ta metoda jest używana do wyłączania dodatku AIP, nadal możesz użyć klienta usługi AIP, aby rozszerzyć etykietowanie poza aplikacje Office.

## <a name="feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps"></a>Parzystość funkcji na potrzeby wbudowanego etykietowania i dodatku AIP dla aplikacji Office

Wiele funkcji etykietowania obsługiwanych przez dodatek AIP jest teraz obsługiwanych przez wbudowane etykietowanie. Aby uzyskać bardziej szczegółową listę możliwości, minimalne wersje, które mogą być potrzebne, i informacje o konfiguracji, zobacz [Zarządzanie etykietami poufności w aplikacjach Office](sensitivity-labels-office-apps.md).

Planowane i opracowywane są dodatkowe funkcje. Jeśli interesuje Cię konkretna funkcja, sprawdź [plan Microsoft 365](https://aka.ms/MIPC/Roadmap) i rozważ dołączenie do [Information Protection firmy Microsoft w Office prywatnej wersji zapoznawczej](https://aka.ms/MIP/PreviewRing).

Skorzystaj z poniższych informacji, aby określić, czy używasz funkcji z dodatku usługi AIP, która nie jest jeszcze obsługiwana przez wbudowane etykietowanie:

|Funkcja lub funkcja dodatku usługi AIP|Wbudowane etykietowanie |
|:-------------------------------|:----------------:|
|**Kategoria: Ogólne** ||
|Centralne raportowanie i inspekcja|![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-office-apps.md#auditing-labeling-activities) |
|Chmura dla instytucji rządowych|![Obsługiwane.](../media/yes-icon.png)|
|Administrator może wyłączyć etykietowanie <br> — Wszystkie aplikacje|  ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-office-apps.md#if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows)|
|Administrator może wyłączyć etykietowanie <br> — Na aplikację|  W planowaniu lub opracowywaniu|
|**Kategoria: Środowisko użytkownika** ||
|Przycisk etykietowania na wstążce|![Obsługiwane.](../media/yes-icon.png)|
|Obsługa wielu języków dla nazw etykiet i etykietek narzędzi| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) |
|Kolory etykiet| W planowaniu lub opracowywaniu |
|Widoczność etykiet na pasku narzędzi| W planowaniu lub opracowywaniu |
|**Kategoria: Akcje etykietowania** ||
|Ręczne etykietowanie |  ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) |
|Obowiązkowe etykietowanie | ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels.md#what-label-policies-can-do)|
|Etykiety domyślne <br> — Nowe i istniejące elementy <br> — Oddzielne ustawienia poczty e-mail|  ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels.md#what-label-policies-can-do) |
|Zalecane lub automatyczne |![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) |
|Uzasadnienie zmiany na starszą wersję |  ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels.md#what-label-policies-can-do)|
| **Kategoria: Oznaczenia wizualne** | |
|Nagłówki, stopki, znak wodny| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels.md#what-label-policies-can-do)|
|Oznaczenia dynamiczne| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)|
|Oznaczanie wizualizacji dla aplikacji| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-office-apps.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)|
| **Kategoria: Szyfrowanie** | |
|Uprawnienia zdefiniowane przez administratora | ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](encryption-sensitivity-labels.md#assign-permissions-now) |
|Uprawnienia zdefiniowane przez użytkownika <br> — Nie przekazuj dalej dla Outlook <br> — Uprawnienia niestandardowe użytkownika i grupy dla programu Word, Excel, PowerPoint| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](encryption-sensitivity-labels.md#let-users-assign-permissions)|
|Uprawnienia zdefiniowane przez użytkownika <br> — Uprawnienia niestandardowe dla całej organizacji przez określenie domen dla programu Word, Excel, PowerPoint | W planowaniu lub opracowywaniu |
|Współtwoerowanie i automatyczne zapisywanie | ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-coauthoring.md) |
|Szyfrowanie podwójnym kluczem | W planowaniu lub opracowywaniu |
|Odwoływanie dokumentów dla użytkowników | W trakcie przeglądu |
| | |

### <a name="support-for-powershell-advanced-settings"></a>Obsługa ustawień zaawansowanych programu PowerShell

Klient usługi AIP obsługuje wiele dostosowań przy użyciu [zaawansowanych ustawień programu PowerShell](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configuring-advanced-settings-for-the-client-via-powershell). Niektóre z tych ustawień zaawansowanych są teraz obsługiwane przez wbudowane etykietowanie, jak opisano w artykule [New-Label](/powershell/module/exchange/new-label) lub [Set-Label](/powershell/module/exchange/set-label) oraz [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) lub [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy).

Może się jednak okazać, że nie trzeba używać programu PowerShell do konfigurowania obsługiwanych ustawień, ponieważ są one uwzględnione w standardowej konfiguracji w portalu zgodności usługi Microsoft Purview. Na przykład możliwość wyłączenia obowiązkowego etykietowania dla Outlook i ustawienia innej etykiety domyślnej.

Następujące konfiguracje z dodatku usługi AIP nie są jeszcze obsługiwane przez wbudowane etykietowanie:

- [Dziedziczenie etykiet z załączników wiadomości e-mail](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
- [Protokół S/MIME dla Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configure-a-label-to-apply-smime-protection-in-outlook)
- [Nadmierne dzielenie komunikatów podręcznych dla Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
- [Domyślny etykieta podrzędna etykiety nadrzędnej](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#specify-a-default-sublabel-for-a-parent-label)
- [Usuwanie oznaczeń zawartości zewnętrznej](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solution )

## <a name="features-not-planned-to-be-supported-by-built-in-labeling-for-office-apps"></a>Funkcje, które nie mają być obsługiwane przez wbudowane etykietowanie dla aplikacji Office

Mimo że nowe możliwości wbudowanego etykietowania są dodawane przez cały czas, dodatek AIP Office obsługuje następujące możliwości, które nie są planowane do udostępnienia w przyszłych wersjach na potrzeby wbudowanego etykietowania:

- Stosowanie etykiet do formatów Microsoft Office 97–2003, takich jak pliki .doc
- Trwale odłączone komputery
- Autonomiczne wersje Office (czasami nazywane "Office Perpetual"), a nie oparte na subskrypcji

## <a name="next-steps"></a>Następne kroki

Aby uzyskać instrukcje dotyczące tworzenia i konfigurowania tych możliwości etykietowania, zobacz [Tworzenie i konfigurowanie etykiet poufności i ich zasad](create-sensitivity-labels.md).

> [!TIP]
> Jeśli masz już etykiety poufności w portalu zgodności usługi Microsoft Purview, nie będziesz kwalifikować się do automatycznego tworzenia etykiet domyślnych. Jednak nadal warto odwoływać się do ich konfiguracji: [domyślne etykiety poufności](mip-easy-trials.md#default-sensitivity-labels). 
