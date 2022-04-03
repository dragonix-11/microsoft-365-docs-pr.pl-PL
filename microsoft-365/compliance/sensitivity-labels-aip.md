---
title: Wybieranie Microsoft Information Protection (MIP) wbudowanych etykiet dla aplikacji usługi Office za pośrednictwem dodatku usługi Azure Information Protection (AIP)
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
description: W przypadku korzystania z ujednoliconego klienta etykiet usługi Azure Information Protection (AIP) poznaj zalety korzystania z wbudowanych etykiet dla aplikacji Office, a nie dodatku AIP.
ms.openlocfilehash: 38aee57720f38793f4f61cc871a9bee556e28690
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498610"
---
# <a name="why-choose-mip-built-in-labeling-over-the-aip-add-in-for-office-apps"></a>Dlaczego warto wybrać wbudowane etykiety MIP za pomocą dodatku AIP dla Office aplikacji

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Jeśli używasz etykiet [](sensitivity-labels.md) wrażliwości w programie Aplikacje Microsoft 365 na komputerach z systemem Windows, masz do wyboru etykiety wbudowane w aplikacje usługi Office lub dodatek z ujednoliconego klienta etykiet usługi [Azure Information Protection (AIP](/azure/information-protection/rms-client/aip-clientv2)). 

Wbudowane etykiety stanowią podstawowy element wdrożenia programu [Microsoft Information Protection (MIP](information-protection-solution.md)), ponieważ ta technologia etykiet obejmuje różne platformy (Windows, macOS, iOS, Android i sieć Web), a także aplikacje i usługi firmy Microsoft i nie tylko. Wbudowane etykiety są również zaprojektowane do pracy z innymi możliwościami ochrony przed utratą danych, na przykład klasyfikacją danych i zapobieganiem utracie danych (DLP).

Ponieważ na wbudowanych etykietach nie jest Office dodatek, ich stabilność i wydajność są większe. Obsługują one również najnowsze funkcje technologii miP, takie jak zaawansowane klasyfikatory.

Domyślnie wbudowane etykiety są wyłączone w aplikacjach pakietu Office Windows, gdy jest zainstalowany klient AIP. To zachowanie domyślne można zmienić, korzystając z instrukcji z poniższej sekcji Jak wyłączyć dodatek [AIP](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps) w celu używania wbudowanych etykiet dla Office aplikacji.

Po zainstalowaniu klienta AIP, ale jego wyłączeniu w Office, pozostałe funkcje klienta AIP będą nadal obsługiwane:

- Opcje dostępne po kliknięciu prawym przyciskiem myszy Eksplorator plików, które mają być stosowane etykiety do wszystkich typów plików.

- Przeglądarka do wyświetlania zaszyfrowanych plików tekstowych, obrazów lub dokumentów PDF.

- Moduł programu PowerShell do odnajdywania poufnych informacji w plikach lokalnych oraz stosowania lub usuwania etykiet i szyfrowania z tych plików.

- Skaner do odnajdywania poufnych informacji przechowywanych w lokalnych magazynach danych, a następnie opcjonalnego oznaczania tej zawartości.

Aby uzyskać więcej informacji o tych możliwościach, które wykraczają poza Office aplikacji usługi [Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide) przewodnik administratora klienta z ujednoliconą etykietą z dokumentacji programu AIP.

Niezależnie od etykiet możesz nadal używać modułu [AIPService](/powershell/module/aipservice) PowerShell do zarządzania usługą szyfrowania na poziomie dzierżawy. Można na przykład skonfigurować dostęp superumiejscowy dla użytkowników, gdy trzeba usunąć szyfrowanie na potrzeby odzyskiwania danych, śledzić i cofać dokumenty otwarte przez klienta usługi AIP oraz konfigurować okres ważności licencji użytkowania dla dostępu w trybie offline. Aby uzyskać więcej informacji, zobacz [Administrowanie ochroną przed platformą Azure Information Protection przy użyciu programu PowerShell](/azure/information-protection/administer-powershell).

## <a name="decide-whether-to-use-built-in-labeling-for-office-apps-or-the-aip-add-in"></a>Zdecyduj, czy chcesz używać wbudowanych etykiet dla Office, czy dodatku AIP

Teraz, gdy klient AIP jest w trybie konserwacji[, nie](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613) zalecamy używania dodatku AIP dla aplikacji Office z następujących powodów:

- Nie będą obsługiwane żadne nowe funkcje etykiet.
- Dodatki są mniej stabilne, ponieważ mogą powodować konflikt z innymi dodatki, które mogą powodować zawieszanie Office aplikacji, awarie lub automatyczne wyłączanie tego dodatku.
- Jako dodatek działa on wolniej i może zostać wyłączony przez użytkowników, aby obejść wymagania dotyczące etykiet.
- Wszelkie poprawki będą wymagały ponownego zainstalowania Information Protection Azure.
- Środowisko etykiet dla użytkowników różni się nieco od wbudowanych etykiet, które użytkownicy mają na innych urządzeniach (macOS, iOS, Android) i kiedy używają Office dla sieci web. Ta różnica może zwiększyć koszty szkoleń i pomocy technicznej.
- Są już dostępne nowe Office etykiet, które są obsługiwane tylko przez wbudowane etykiety[, a](#features-supported-only-by-built-in-labeling-for-office-apps) lista rozrasta się cały czas.

Używaj dodatku AIP dla aplikacji pakietu Windows Office tylko wtedy, gdy został on już wdrożony u użytkowników i potrzebujesz czasu na ich migrację do wbudowanych etykiet. Użytkownicy potrzebują funkcji, która nie jest obsługiwana przez wbudowane etykiety. Informacje o [parowości funkcji podane](#feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps) na tej stronie ułatwiają identyfikowanie tych funkcji.

## <a name="features-supported-only-by-built-in-labeling-for-office-apps"></a>Funkcje obsługiwane tylko przez wbudowane etykiety dla Office aplikacji

> [!NOTE]
> Wiele nowych funkcji etykiet jest w planowaniu lub opracowywania, więc należy oczekiwać, że lista w tej sekcji będzie się rozrastać z czasem.

Niektóre funkcje są obsługiwane tylko przez wbudowane etykiety dla aplikacji Office i nie są obsługiwane przez dodatek AIP. Obejmują one:

- Do automatycznego i zalecanego oznaczania etykiet:
    - Dostęp do inteligentnych usług klasyfikacji, [które zawierają](classifier-learn-about.md) klasyfikatory przeszkolne, dokładne dopasowanie danych [(EDM)](sit-learn-about-exact-data-match-based-sits.md) i [nazwane jednostki](named-entities-learn.md)
    - Wykrywanie informacji poufnych podczas wpisywania użytkowników
    - W programie Word użytkownicy mogą przeglądać i usuwać identyfikowane poufne treści
- W przypadku etykiet, które umożliwiają użytkownikom przypisywanie uprawnień, różne uprawnienia (Odczyt lub Zmiana) można przyznać użytkownikom lub grupom.
- Encrypt-Only wiadomości e-mail
- Widoczność etykiet na pasku stanu
- Obsługa przełączania konta
- Użytkownicy nie mogą wyłączyć etykiet

Przykład przedstawiający sposób, w jaki użytkownicy mogą przeglądać i opcjonalnie usuwać identyfikowane poufne treści w programie Word:

![Numery kart kredytowych zidentyfikowane użytkownikom jako treści wrażliwości z opcją usunięcia.](../media/detect-sensitive-content.png)

Aby być na bieżąco z nowymi możliwościami etykiet dostępnymi dla wbudowanych etykiet, zobacz [](whats-new.md) Co nowego w sekcji Microsoft 365 zgodności i **Etykiety** wrażliwości.

## <a name="how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps"></a>Jak wyłączyć dodatek AIP, aby używać wbudowanych etykiet dla Office aplikacji

Po zainstalowaniu klienta AIP w celu rozszerzenia etykiet poza aplikacje usługi Office, ale chcesz uniemożliwić ładowanie dodatku klienta w aplikacjach Office zasady grupy, użyj ustawienia listy zarządzanych dodatków zgodnie z dokumentem Bez dodatków załadowanych z powodu ustawień  zasad grupy dla programów [Office 2013 i Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

W aplikacjach pakietu Windows Office, które obsługują wbudowane etykiety, użyj konfiguracji programów Microsoft Word 2016, Excel 2016, PowerPoint 2016 i Outlook 2016, określ następujące identyfikatory programowe (ProgID) dla klienta AIP i ustaw opcję na wartość **0: Dodatek jest zawsze wyłączony (zablokowany)**

|Aplikacja  |ProgID  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

Wdąć to ustawienie przy zasady grupy lub przy użyciu usługi Office [zasad chmury](/DeployOffice/overview-office-cloud-policy-service).

> [!IMPORTANT]
> Jeśli używasz ustawienia zasady grupy Użyj funkcji Wrażliwości w programie **Office**, aby zastosować i wyświetlić etykiety wrażliwości oraz ustawić wartość **1**, mogą wystąpić pewne sytuacje, w których dodatek AIP może być nadal ładowany w Office aplikacjach. Zablokowanie ładowania dodatku w każdej aplikacji zapobiega temu.

Ewentualnie możesz interakcyjne wyłączyć lub usunąć dodatek **Microsoft Azure Information Protection Office z** programu Word, Excel, PowerPoint i Outlook. Ta metoda jest odpowiednia do jednego komputera i do testowania ad hoc. Aby uzyskać instrukcje, [zobacz Wyświetlanie i](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d) instalowanie dodatków oraz zarządzanie nimi w Office programach.

Niezależnie od metody, którą wybierzesz, zmiany zostaną wprowadzone po ponownym Office ponownego uruchomienia aplikacji.

> [!NOTE]
> Wbudowane etykiety wymagają subskrypcji pakietu Office aplikacji. Jeśli masz autonomiczne wersje programu Office, czasami nazywane "Office Perpetual", zalecamy uaktualnienie do programu Aplikacje Microsoft 365 dla systemu Enterprise, aby korzystać z najnowszych możliwości [etykiet.](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)

Pamiętaj, że po wyłączeniu dodatku AIP za pomocą tej metody możesz nadal używać klienta AIP do rozszerzania etykiet poza Office aplikacji.

## <a name="feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps"></a>Parowanie funkcji dla wbudowanych etykiet i dodatku AIP dla Office aplikacji

Wiele funkcji etykiet obsługiwanych przez dodatek AIP jest teraz obsługiwanych przez wbudowane etykiety. Aby uzyskać bardziej szczegółową listę możliwości, minimalne potrzebne wersje i informacje o konfiguracji, zobacz Zarządzanie etykietami wrażliwości w Office [aplikacjach](sensitivity-labels-office-apps.md).

Planujemy i planujemy kolejne funkcje. Jeśli interesuje Cię konkretną funkcja, zajrzyj do planu Microsoft 365 i rozważ dołączenie do programu [](https://aka.ms/MIPC/Roadmap) Microsoft Information Protection w Office [Private Preview](https://aka.ms/MIP/PreviewRing).

Poniższe informacje ułatwiają ustalenie, czy korzystasz z funkcji z dodatku AIP, która nie jest jeszcze obsługiwana przez wbudowane etykiety:

|Funkcja lub funkcja dodatku AIP|Wbudowane etykiety |
|:-------------------------------|:----------------:|
|**Kategoria: Ogólne** ||
|Raportowanie centralne i inspekcja|![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-office-apps.md#auditing-labeling-activities) |
|Government Cloud|![Obsługiwane.](../media/yes-icon.png)|
|Administrator może wyłączyć etykiety <br> - Wszystkie aplikacje|  ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-office-apps.md#office-built-in-labeling-client-and-other-labeling-solutions)|
|Administrator może wyłączyć etykiety <br> - Na aplikację|  W planowaniu lub rozwoju|
|**Kategoria: Środowisko użytkownika** ||
|Przycisk Etykiety na wstążce|![Obsługiwane.](../media/yes-icon.png)|
|Obsługa wielu języka dla nazw etykiet i etykietek narzędzi| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) |
|Kolory etykiet| W planowaniu lub rozwoju |
|Widoczność etykiet na pasku narzędzi| W planowaniu lub rozwoju |
|**Kategoria: Oznaczanie akcji** ||
|Ręczne oznaczanie etykiet |  ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) |
|Obowiązkowa etykieta | ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels.md#what-label-policies-can-do)|
|Etykiety domyślne <br> — Nowe i istniejące elementy <br> - Oddzielne ustawienia dla poczty e-mail|  ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels.md#what-label-policies-can-do) |
|Zalecane lub automatyczne |![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) |
|Obniżenie poziomu uzasadnienia |  ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels.md#what-label-policies-can-do)|
| **Kategoria: Oznaczenia wizualne** | |
|Nagłówki, stopki, znak wodny| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels.md#what-label-policies-can-do)|
|Oznaczenia dynamiczne| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)|
|Oznaczanie wizualne dla aplikacji| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-office-apps.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)|
| **Kategoria: Szyfrowanie** | |
|Uprawnienia zdefiniowane przez administratora | ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](encryption-sensitivity-labels.md#assign-permissions-now) |
|Uprawnienia zdefiniowane przez użytkownika <br> - Nie przesyłaj dalej dla Outlook <br> — Uprawnienia niestandardowe użytkowników i grup dla aplikacji Word, Excel, PowerPoint| ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](encryption-sensitivity-labels.md#let-users-assign-permissions)|
|Uprawnienia zdefiniowane przez użytkownika <br> — uprawnienia niestandardowe dla całej organizacji przez określenie domen dla programu Word, Excel, PowerPoint | W planowaniu lub rozwoju |
|Współtworzenie i Autozasave | ![Obsługiwane.](../media/yes-icon.png) <br>[Dowiedz się więcej](sensitivity-labels-coauthoring.md) |
|Szyfrowanie z podwójnym kluczem | W planowaniu lub rozwoju |
|Odwołania dokumentów dla użytkowników | W trakcie przeglądu |
| | |

### <a name="support-for-powershell-advanced-settings"></a>Obsługa ustawień zaawansowanych programu PowerShell

Klient AIP obsługuje wiele dostosowań za pomocą ustawień [zaawansowanych programu PowerShell](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configuring-advanced-settings-for-the-client-via-powershell). Niektóre z tych ustawień zaawansowanych są teraz obsługiwane przez wbudowane etykiety, zgodnie z dokumentami [New-Label](/powershell/module/exchange/new-label) lub [Set-Label](/powershell/module/exchange/set-label) oraz [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) lub [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy).

Jednak może się okazać, że nie musisz używać programu PowerShell do konfigurowania obsługiwanych ustawień, ponieważ są one zawarte w konfiguracji standardowej z witryny Centrum zgodności platformy Microsoft 365. Na przykład możliwość wyłączenia obowiązkowych etykiet dla Outlook i ustawienia innej etykiety domyślnej.

Następujące konfiguracje dodatku AIP nie są jeszcze obsługiwane przez wbudowane etykiety:

- [Dziedziczenie etykiet po załącznikach wiadomości e-mail](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
- [S/MIME dla Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configure-a-label-to-apply-smime-protection-in-outlook)
- [Komunikaty podręczne dotyczące zasypania wiadomości Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
- [Domyślna etykieta podrzędna etykiety nadrzędnej](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#specify-a-default-sublabel-for-a-parent-label)
- [Usuwanie oznaczenia zawartości zewnętrznej](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solution )

## <a name="features-not-planned-to-be-supported-by-built-in-labeling-for-office-apps"></a>Funkcje, które nie mają być obsługiwane przez wbudowane etykiety dla Office aplikacji

Mimo że przez cały czas dodawane są nowe funkcje wbudowanych etykiet, Office AIP obsługuje następujące funkcje, które nie mają być dostępne w przyszłych wersjach dla wbudowanych etykiet:

- Stosowanie etykiet w celu Microsoft Office formatów 97–2003, takich jak pliki .doc formatach
- Komputery odłączone trwale
- Autonomiczne wersje programu Office (czasami nazywane "Office Perpetual") zamiast oparte na subskrypcji

## <a name="next-steps"></a>Następne kroki

Aby uzyskać instrukcje dotyczące tworzenia i konfigurowania tych funkcji etykiet, zobacz Tworzenie [i konfigurowanie etykiet wrażliwości oraz ich zasad](create-sensitivity-labels.md).

> [!TIP]
> Jeśli masz już etykiety wrażliwości w Centrum zgodności platformy Microsoft 365, nie będziesz mieć uprawnienia do automatycznego tworzenia etykiet domyślnych. Warto jednak odwołać się do ich konfiguracji: Domyślne [etykiety wrażliwości](mip-easy-trials.md#default-sensitivity-labels). 
