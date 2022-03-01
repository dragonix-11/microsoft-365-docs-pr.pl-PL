---
title: Rozwiązywanie problemów znalezionych przez narzędzie do oceny gotowości
description: Szczegółowe działania do podjęcia dla każdego problemu znalezionego przez narzędzie
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: badf2d65f2b29e265a1312cb1d5f4802a44f3cb3
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011403"
---
# <a name="fix-issues-found-by-the-readiness-assessment-tool"></a>Rozwiązywanie problemów znalezionych przez narzędzie do oceny gotowości

Dla każdego sprawdzenia narzędzie raportuje jeden z czterech możliwych wyników:

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Gotowe | Przed ukończeniem rejestracji nie jest wymagane żadne działanie. |
| Porada | Postępuj zgodnie z instrukcjami w narzędziu lub tym artykule, aby uzyskać najlepsze środowisko rejestracji i dla użytkowników. <br><br> Możesz *zakończyć* rejestrację, ale musisz rozwiązać te problemy przed wdrożeniem pierwszego urządzenia. |
| Jeszcze nie gotowe | **Rejestracja nie powiedzie się, jeśli nie rozwiążesz tych problemów.** <br><br> Postępuj zgodnie z instrukcjami w narzędziu lub tym artykule, aby je rozwiązać. |
| Error | Rola Azure Active Directory (AD) nie ma wystarczających uprawnień do uruchomienia tego sprawdzania. |

> [!NOTE]
> Wyniki zgłoszone przez to narzędzie odzwierciedlają stan ustawień tylko w momencie jego uruchomienia. Jeśli później dokonasz zmian w zasadach w Microsoft Intune, Azure Active Directory lub Microsoft 365, elementy, które były "Gotowe", mogą stać się elementami "Jeszcze gotowe". Aby uniknąć problemów z Microsoft Managed Desktop, przed zmianą jakichkolwiek zasad sprawdź konkretne ustawienia opisane w tym artykule.

## <a name="microsoft-intune-settings"></a>Microsoft Intune sieci Microsoft Intune

Dostęp do ustawień usługi Intune można uzyskać w Microsoft Endpoint Manager [administracyjnego](https://endpoint.microsoft.com).

### <a name="autopilot-deployment-profile"></a>Profil wdrożenia z autopilotem

Nie powinno być żadnych istniejących profilów rozwiązania Autopilot, które są kierowane do grup dynamicznych ani przypisanych Microsoft Managed Desktop urządzeniach. Microsoft Managed Desktop nowych urządzeń używa rozwiązania Autopilot. Jeśli masz istniejący profil wdrożenia z programem Autopilot, aby test gotowości rozwiązania Autopilot zakończył się pomyślnie, dla ustawienia Konwertuj  wszystkie urządzenia docelowe na rozwiązania **Auto Microsoft Managed Desktop pilot** musi być ustawiona wartość Nie.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Masz profil rozwiązania Autopilot przypisany do wszystkich urządzeń. <br><br> Aby uzyskać więcej informacji, zobacz [Rejestrowanie Windows w usłudze Intune za pomocą rozwiązania Windows Autopilot](/mem/autopilot/enrollment-autopilot). Po Microsoft Managed Desktop rejestracji ustaw zasady rozwiązania Autopilot tak, aby wykluczały grupę Nowoczesne urządzenia pracy **— Wszystkie usługi** Azure AD.
| Porada | Upewnij się, że profile rozwiązania Autopilot są kierowane do przypisanej lub dynamicznej grupy usługi Azure AD, która nie zawiera Microsoft Managed Desktop urządzeniach. <br><br> Aby uzyskać więcej informacji, zobacz [Rejestrowanie Windows w usłudze Intune za pomocą rozwiązania Windows Autopilot](/mem/autopilot/enrollment-autopilot). Po Microsoft Managed Desktop rejestracji ustaw profile rozwiązania Autopilot tak, aby wykluczyć grupę **Nowoczesne urządzenia miejsca pracy — Wszystkie usługi** Azure AD. |

### <a name="certificate-connectors"></a>Łączniki certyfikatów

Jeśli masz jakiekolwiek łączniki certyfikatów, które będą używane przez urządzenia, które chcesz zarejestrować w programie Microsoft Managed Desktop, łączniki nie powinny mieć żadnych błędów. W przypadku Twojej sytuacji będzie miała zastosowanie tylko jedna z następujących porad, dlatego sprawdź je uważnie.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Nie są dostępne żadne łączniki certyfikatu. Możliwe, że nie są potrzebne żadne łączniki, ale należy ocenić, czy mogą być potrzebne pewne potrzeby w zakresie łączności sieciowej na Microsoft Managed Desktop urządzeniach. <br><br> Aby uzyskać więcej informacji, zobacz [Przygotowanie certyfikatów i profilów sieci dla Microsoft Managed Desktop](certs-wifi-lan.md). |
| Porada | Występuje błąd co najmniej jednego łącznika certyfikatu. Jeśli ten łącznik jest potrzebny do dostarczania certyfikatów do Microsoft Managed Desktop urządzeniach, należy rozwiązać ten błąd. <br><br> Aby uzyskać więcej informacji, zobacz [Przygotowanie certyfikatów i profilów sieci dla Microsoft Managed Desktop](certs-wifi-lan.md). |
| Porada | Masz co najmniej jeden łącznik certyfikatu i nie są zgłaszane żadne błędy. Jednak w ramach przygotowań do wdrożenia może być konieczne utworzenie profilu w celu ponownego użycia łącznika dla Microsoft Managed Desktop urządzeniach. <br><br> Aby uzyskać więcej informacji, zobacz [Przygotowanie certyfikatów i profilów sieci dla Microsoft Managed Desktop](certs-wifi-lan.md). |

### <a name="company-portal"></a>Portal firmy

Microsoft Managed Desktop, aby administratorzy IT Intune — Portal firmy instalują aplikacje dla swoich użytkowników Microsoft Managed Desktop urządzeniach.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Użytkownicy nie mają Portal firmy instalacji. Kup Portal firmy i wymusz synchronizację między usługą Intune a Microsoft Store dla Firm. <br><br> Aby uzyskać więcej informacji, zobacz [Instalowanie Intune — Portal firmy na urządzeniach](../get-started/company-portal.md).

### <a name="conditional-access-policies"></a>Zasady dostępu warunkowego

Zasady dostępu warunkowego nie mogą uniemożliwić Microsoft Managed Desktop azure AD organizacji (dzierżawy) w usłudze Intune i Azure AD.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Masz co najmniej jedną zasady dostępu warunkowego, która jest przeznaczony dla wszystkich użytkowników. <br><br> Podczas rejestracji wykluczymy wszystkie Microsoft Managed Desktop z odpowiednich zasad dostępu warunkowego i zastosujemy nowe zasady dostępu warunkowego, aby ograniczyć dostęp do tych kont. <br><br> Po zarejestrowaniu możesz przejrzeć Microsoft Managed Desktop dostępu warunkowego w programie Microsoft Endpoint Manager. Aby uzyskać więcej informacji o tych kontach usług, zobacz [Standardowe procedury operacyjne](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Porada | Masz zasady dostępu warunkowego, które mogą uniemożliwić Microsoft Managed Desktop zarządzanie Microsoft Managed Desktop siecią. <br><br> Podczas rejestracji wykluczymy wszystkie Microsoft Managed Desktop z odpowiednich zasad dostępu warunkowego i zastosujemy nowe zasady dostępu warunkowego, aby ograniczyć dostęp do tych kont. <br><br> Aby uzyskać więcej informacji na temat tych kont usług, zobacz [Standardowe procedury operacyjne](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Error | Rola administratora usługi Intune nie ma wystarczających uprawnień do tego sprawdzenia. Aby można było uruchomić to sprawdzanie, musisz mieć przypisane następujące role usługi Azure AD: <ul><li>Czytnik zabezpieczeń</li><li>Administrator zabezpieczeń</li><li>Administrator dostępu warunkowego</li><li>Czytnik globalny</li><li>Administrator urządzeń</li></ul>
### <a name="device-compliance-policies"></a>Zasady zgodności urządzeń

Zasady zgodności urządzeń Intune w Twojej organizacji usługi Azure AD mogą mieć wpływ Microsoft Managed Desktop urządzeniach.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Masz co najmniej jedną politykę zgodności, która ma zastosowanie do wszystkich użytkowników. Microsoft Managed Desktop także zasady zgodności, które będą stosowane do Twoich Microsoft Managed Desktop urządzeniach. Przejrzyj wszystkie zasady zgodności utworzone przez Twoją organizację, które dotyczą Microsoft Managed Desktop, aby upewnić się, że nie występują żadne konflikty. <br><br> Aby uzyskać więcej informacji, [zobacz Tworzenie zasad zgodności w programie Microsoft Intune](/mem/intune/protect/create-compliance-policy). |

### <a name="device-configuration-profiles"></a>Profile konfiguracji urządzenia

Profile konfiguracji urządzenia Intune w organizacji usługi Azure AD nie mogą być kierowane do żadnych użytkowników ani urządzeń stacjonarnych zarządzania przez firmę Microsoft.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Masz co najmniej jeden profil konfiguracji, który dotyczy wszystkich użytkowników, wszystkich urządzeń lub obu. Zresetuj profil, aby zastosować go do konkretnej grupy usługi Azure AD, która nie zawiera żadnych Microsoft Managed Desktop urządzeniach. <br><br> Aby uzyskać więcej informacji, zobacz [Tworzenie profilu z ustawieniami niestandardowymi w programie Microsoft Intune](/mem/intune/configuration/custom-settings-configure). |
| Porada | Upewnij się, że wszelkie posiadane zasady konfiguracji nie obejmują żadnych Microsoft Managed Desktop użytkowników ani urządzeń. <br><br> Aby uzyskać więcej informacji, zobacz [Tworzenie profilu z ustawieniami niestandardowymi w programie Microsoft Intune](/mem/intune/configuration/custom-settings-configure). |

### <a name="device-type-restrictions"></a>Ograniczenia typu urządzenia

Microsoft Managed Desktop urządzenia muszą mieć możliwość zarejestrowania się w usłudze Intune.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Obecnie masz co najmniej jedną z zasad ograniczeń rejestracji skonfigurowanych w celu uniemożliwinia Windows w Intune. <br><br> Wykonaj czynności opisane w [tece](/mem/intune/enrollment/enrollment-restrictions-set) Ustawianie ograniczeń rejestracji dla poszczególnych zasad ograniczeń rejestracji, które mają na celu Microsoft Managed Desktop użytkowników, i zmień ustawienie Windows **(MDM)** na **Zezwalaj**. Możesz jednak ustawić dla **dowolnych urządzeń** **osobistych Windows MDM opcję** **Zablokuj**. |

### <a name="enrollment-status-page"></a>Strona stanu rejestracji

Obecnie masz włączoną stronę stanu rejestracji (ESP). Jeśli zamierzasz uczestniczyć w publicznej wersji Microsoft Managed Desktop tej funkcji, możesz zignorować ten element. Aby uzyskać więcej informacji, zobacz [Środowisko pierwszego uruchomienia z rozwiązania Autopilot i strona Stan rejestracji](../get-started/esp-first-run.md).

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Masz profil domyślny ESP ustawiony na Pokaż **postęp konfiguracji aplikacji i profilu**. <br><br> Wyłącz to ustawienie lub upewnij się, że przypisania do żadnej grupy usługi Azure AD nie zawierają Microsoft Managed Desktop, zgodnie z instrukcjami w konfigurowanie [strony stanu rejestracji](/mem/intune/enrollment/windows-enrollment-status). |
| Porada | Upewnij się, że żadne profile, które  mają ustawienie Pokaż aplikację i postęp konfiguracji profilu, nie są przypisane do żadnej grupy usługi Azure AD, która zawiera Microsoft Managed Desktop urządzenia. <br><br> Aby uzyskać więcej informacji, [zobacz Konfigurowanie strony stanu rejestracji](/mem/intune/enrollment/windows-enrollment-status). |

### <a name="microsoft-store-for-business"></a>Microsoft Store dla Firm

Używamy Microsoft Store dla Firm i wdrażamy aplikację Portal firmy na Microsoft Managed Desktop. Ta metoda umożliwia użytkownikom opcjonalne zainstalowanie niektórych aplikacji, takich jak Microsoft Project i Microsoft Visio (jeśli jest to dozwolone).

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Microsoft Store dla Firm nie jest włączona lub nie jest synchronizowana z usługą Intune. <br><br> Aby uzyskać więcej informacji, zobacz Jak zarządzać zakupionymi aplikacjami z pakietu [Microsoft Store dla Firm](/mem/intune/apps/windows-store-for-business) w Microsoft Intune i Instalowanie aplikacji Intune — Portal firmy [na urządzeniach](../get-started/company-portal.md). |

### <a name="multi-factor-authentication"></a>Uwierzytelnianie wieloskładnikowe

Uwierzytelnianie wieloskładnikowe nie uniemożliwia Microsoft Managed Desktop zarządzania organizacją usługi Azure AD (dzierżawy) w usłudze Intune i Azure AD.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Niektóre zasady uwierzytelniania wieloskładnikowego są ustawione jako **wymagane** dla zasad dostępu warunkowego przypisanych do wszystkich użytkowników. <br><br> Podczas rejestracji wykluczymy wszystkie Microsoft Managed Desktop z odpowiednich zasad dostępu warunkowego i zastosujemy nowe zasady dostępu warunkowego, aby ograniczyć dostęp do tych kont. <br><br> Aby uzyskać więcej informacji na temat tych kont usług, zobacz [Standardowe procedury operacyjne](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Porada | W przypadku zasad dostępu warunkowego jest wymagane uwierzytelnianie wieloskładnikowe, które może uniemożliwić Microsoft Managed Desktop zarządzanie usługą Microsoft Managed Desktop sieci. <br><br> Podczas rejestracji dobrze wyklucz Microsoft Managed Desktop z odpowiednich zasad dostępu warunkowego i zastosuj nowe zasady dostępu warunkowego, aby ograniczyć dostęp do tych kont. Aby uzyskać więcej informacji na temat tych kont usług, zobacz [Standardowe procedury operacyjne](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Error | Rola administratora usługi Intune nie ma wystarczających uprawnień do tego sprawdzenia. Aby można było uruchomić to sprawdzanie, musisz mieć przypisane następujące role usługi Azure AD: <ul><li>Czytnik zabezpieczeń</li><li>Administrator zabezpieczeń</li><li>Administrator dostępu warunkowego</li><li>Czytnik globalny</li><li>Administrator urządzeń</li></ul>

### <a name="powershell-scripts"></a>Skrypty programu PowerShell

Windows PowerShell skryptów nie można przypisywać w sposób docelowy dla Microsoft Managed Desktop urządzeniach.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Upewnij się, Windows PowerShell skryptów w Twojej organizacji usługi Azure AD nie są kierowane do użytkowników ani urządzeń stacjonarnych firmy Microsoft. Nie przypisuj skryptu programu PowerShell do wszystkich użytkowników, wszystkich urządzeń lub obu tych urządzeń. Zmień zasady, aby użyć przydziału docelowego określonej grupy usługi Azure AD, która nie zawiera żadnych Microsoft Managed Desktop urządzeniach ani użytkownikach. <br><br> Aby uzyskać więcej informacji, zobacz [Używanie skryptów programu PowerShell na Windows 10 urządzeniach w usłudze Intune](/mem/intune/apps/intune-management-extension). |

### <a name="region"></a>Region

Twój region musi być obsługiwany przez Microsoft Managed Desktop.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Twój region organizacji usługi Azure AD nie jest obecnie obsługiwany przez Microsoft Managed Desktop. <br><br> Aby uzyskać więcej informacji, [Microsoft Managed Desktop obsługiwane regiony i języki](../service-description/regions-languages.md). |
| Porada | Co najmniej jeden kraj, w którym znajduje się Twoja organizacja usługi Azure AD, nie jest obsługiwany przez Microsoft Managed Desktop. <br><br> Aby uzyskać więcej informacji, [Microsoft Managed Desktop obsługiwane regiony i języki](../service-description/regions-languages.md). |

### <a name="security-baselines"></a>Linie bazowe zabezpieczeń

Zasady planu bazowego zabezpieczeń nie powinny być kierowane do żadnych Microsoft Managed Desktop urządzeniach.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Masz profil planu bazowego zabezpieczeń, który jest przeznaczony dla wszystkich użytkowników, wszystkich urządzeń lub obu tych urządzeń. Zmień zasady, aby użyć przydziału docelowego określonej grupy usługi Azure AD, która nie zawiera żadnych Microsoft Managed Desktop urządzeniach. <br><br> Aby uzyskać więcej informacji, zobacz Konfigurowanie urządzeń przenośnych przy [użyciu planu bazowego Windows 10 Intune](/mem/intune/protect/security-baselines). Podczas rejestracji zastosujemy nowy plan bazowy zabezpieczeń do wszystkich Microsoft Managed Desktop urządzeniach. Po zarejestrowaniu możesz przejrzeć Microsoft Managed Desktop planu bazowego zabezpieczeń w obszarze Zasady **konfiguracji** Microsoft Endpoint Manager. |
| Porada | Upewnij się, że wszelkie zasady planu bazowego zabezpieczeń nie są Microsoft Managed Desktop urządzeniach. Aby uzyskać więcej informacji, zobacz Konfigurowanie urządzeń przenośnych przy [użyciu planu bazowego Windows 10 Intune](/mem/intune/protect/security-baselines). <br><br> Podczas rejestracji zastosujemy nowy plan bazowy zabezpieczeń do wszystkich Microsoft Managed Desktop urządzeniach. Nowoczesne **urządzenia miejsca pracy — wszystkie grupy** usługi Azure AD to grupa dynamiczna tworzymy po zarejestrowaniu się w usłudze Microsoft Managed Desktop. Aby wykluczyć tę grupę po rejestracji, musisz wrócić. |

### <a name="unlicensed-admins"></a>Nielicencjonowani administratorzy

To ustawienie musi być włączone, aby uniknąć błędu "brak uprawnień" podczas interakcji z Twoją organizacją usługi Azure AD.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | **Należy włączyć zezwalanie na dostęp nielicencjonowanych** administratorów. Aby uzyskać więcej informacji, zobacz [Wymagania wstępne dotyczące kont gości](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="windows-apps"></a>Windows aplikacji

Przejrzyj aplikacje, które chcesz Microsoft Managed Desktop użytkowników.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Należy przygotować spis aplikacji, które mają być dostępne dla Microsoft Managed Desktop użytkowników. Ponieważ te aplikacje muszą zostać wdrożone w usłudze Intune, należy ocenić ponowne użyć istniejących aplikacji Intune. Rozważ użycie Portal firmy (zobacz [Instalowanie Intune — Portal firmy na](../get-started/company-portal.md) urządzeniach i Strona stanu rejestracji (ESP) w celu rozpowszechniania aplikacji dla użytkowników. <br><br> Aby uzyskać więcej informacji, zobacz [Aplikacje Microsoft Managed Desktop](apps.md) i [Środowisko pierwszego uruchomienia z usługą Autopilot i stroną stanu rejestracji](../get-started/esp-first-run.md). <br><br> Możesz poprosić przedstawiciela firmy Microsoft o zapytanie w usłudze Microsoft Endpoint Configuration Manager w celu zidentyfikowania aplikacji gotowych do migracji do usługi Intune lub konieczności dostosowania. |

### <a name="windows-hello-for-business"></a>Windows Hello dla firm

Microsoft Managed Desktop włączyć Windows Hello dla firm.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Windows Hello dla firm jest wyłączona lub nie została wyłączona. Tę funkcję możesz włączyć, korzystając z [procedury Windows Hello dla firm](/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy). |

### <a name="windows-10-update-rings"></a>Windows 10 pierścieni aktualizacji

Zasady "Windows 10 pierścienia aktualizacji" w usłudze Intune nie mogą być kierowane do żadnych Microsoft Managed Desktop urządzeniach.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Zasady "pierścienia aktualizacji" są zasady dotyczące wszystkich urządzeń, wszystkich użytkowników lub obu tych urządzeń. Zmień zasady, aby użyć przydziału docelowego określonej grupy usługi Azure AD, która nie zawiera żadnych Microsoft Managed Desktop urządzeniach. <br><br> Aby uzyskać więcej informacji, zobacz [Zarządzanie Windows 10 aktualizacji oprogramowania w usłudze Intune](/mem/intune/protect/windows-update-for-business-configure). |
| Porada | Upewnij się, że wszystkie zasady pierścienia aktualizacji nie obejmują grupy Nowoczesne urządzenia miejsca **pracy — Wszystkie usługi** Azure AD. Jeśli do tych zasad zostały przypisane grupy użytkowników usługi Azure AD, upewnij się, że wszystkie zasady pierścienia aktualizacji zostały wykluczone z grupy Nowoczesne miejsce pracy — Wszystkie grupy **usługi Azure AD**, do których dodajesz użytkowników usługi Microsoft Managed Desktop (lub równoważnej grupy). <br><br> Aby uzyskać więcej informacji, zobacz [Zarządzanie Windows 10 aktualizacji oprogramowania w usłudze Intune](/mem/intune/protect/windows-update-for-business-configure). Nowoczesne urządzenia **robocze — Wszystkie i** Nowoczesne miejsce pracy **—** Wszystkie grupy usługi Azure AD to grupy, które tworzymy po zarejestrowaniu się w usłudze Microsoft Managed Desktop. Aby wykluczyć tę grupę po rejestracji, musisz wrócić. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory ustawień

Możesz uzyskać dostęp do Azure Active Directory w Portalu [Azure](https://portal.azure.com).

### <a name="intune-enrollment"></a>Rejestracja w usłudze Intune

Windows 10 w Twojej organizacji usługi Azure AD muszą mieć możliwość automatycznego zarejestrowania się w usłudze Intune.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Upewnij się, **że zakres Użytkownik usługi MDM** ma ustawioną wartość **Niektóre** **lub Wszystkie**, a nie **Brak**. <br><br> Jeśli wybierzesz pozycję **Niektóre**, wróć po rejestracji i wybierz grupę Nowoczesne miejsce pracy — Wszystkie grupy **usługi Azure AD** dla grup lub równoważną grupę skierowaną do wszystkich użytkowników Microsoft Managed Desktop użytkowników. <br><br> Aby uzyskać więcej informacji, [zobacz Konfigurowanie rejestracji na Windows urządzeniach przy użyciu aplikacji Microsoft Intune](/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment). |

### <a name="ad-hoc-subscriptions"></a>Subskrypcje ad hoc

Zaleca się sprawdzenie ustawienia, które w przypadku ustawienia wartości "fałsz" może uniemożliwić poprawne działanie roamingu Enterprise roamingu województwa.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Upewnij się **, że dla ustawienia AllowAdHocSubscriptions** ustawiono wartość **True**. W przeciwnym Enterprise roamingu województwa może nie działać. <br><br> Aby uzyskać więcej informacji, [zobacz Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings). |

### <a name="enterprise-state-roaming"></a>Enterprise roamingu województwa

Enterprise roamingu województwa powinien być włączony.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Upewnij się, Enterprise dla opcji Roaming województwa jest włączony dla **wszystkich lub** **wybranych grup**. <br><br> Aby uzyskać więcej informacji, zobacz [Włączanie Enterprise roamingu województwa w Azure Active Directory](/azure/active-directory/devices/enterprise-state-roaming-enable). |

### <a name="guest-invitation-settings"></a>Ustawienia zaproszenia gościa

Microsoft Managed Desktop dostosowywanie ustawień zaproszeń gości, ponieważ ustawienie domyślne umożliwia zapraszanie gości wszystkim użytkownikom i gościom w katalogu.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | **Użytkownicy i użytkownicy przypisani do określonych ról administratora** mogą zapraszać gości, w tym gości z uprawnieniami członków. <br><br> Aby uzyskać więcej informacji, zobacz [Wymagania wstępne dotyczące kont gości](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="guest-user-access"></a>Dostęp gościa

Microsoft Managed Desktop dostosowywanie dostępu gości, ponieważ ustawienie domyślne umożliwia wszystkim gościom w katalogu ten sam dostęp co członkowie.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | **Użytkownicy goście mają ograniczony dostęp do właściwości i członkostwa w obiektach katalogu** . <br><br> Aby uzyskać więcej informacji, zobacz [Wymagania wstępne dotyczące kont gości](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="licenses"></a>Licencje

Wiele licencji jest wymaganych do używania Microsoft Managed Desktop.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Nie gotowe | Nie masz wszystkich licencji, których potrzebujesz, aby użyć Microsoft Managed Desktop. <br><br> Aby uzyskać więcej informacji, [Microsoft Managed Desktop technologii i](../intro/technologies.md) [Więcej informacji o licencjach](prerequisites.md#more-about-licenses). |

### <a name="microsoft-managed-desktop-service-accounts"></a>Microsoft Managed Desktop kont usługi

Niektóre nazwy kont mogą być w konflikcie z nazwami kont utworzonymi przez Microsoft Managed Desktop zarządzanie Microsoft Managed Desktop kontami.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Masz co najmniej jedną nazwę konta, która będzie kolidować z nazwami kont utworzonymi przez Microsoft Managed Desktop. Aby wykluczyć te nazwy kont, we współpracy z przedstawicielem firmy Microsoft. Nie pozy używamy listy nazw kont publicznie w celu zminimalizowania ryzyka związanego z zabezpieczeniami.

### <a name="security-administrator-roles"></a>Role administratora zabezpieczeń

Użytkownicy z określonymi rolami zabezpieczeń muszą mieć przypisane te role w programie Microsoft Defender for Endpoint.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Jeśli masz użytkowników przypisanych do dowolnej z tych ról w Twojej organizacji usługi Azure AD, upewnij się, że mają oni również przypisane te role w usłudze Microsoft Defender for Endpoint. W przeciwnym razie administratorzy pełniący te role nie będą mogli uzyskać dostępu do portalu administracyjnego. <ul><li>Operator zabezpieczeń</li><li>Czytnik globalny</li></ul> <br> Aby uzyskać więcej informacji, zobacz [Tworzenie ról w kontrolach dostępu opartych na rolach i zarządzanie nimi](/windows/security/threat-protection/microsoft-defender-atp/user-roles).

### <a name="security-default"></a>Domyślne ustawienia zabezpieczeń

Domyślne ustawienia zabezpieczeń w Azure Active Directory uniemożliwią Microsoft Managed Desktop zarządzanie Twoimi urządzeniami.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Jeszcze nie gotowe | Masz włączone ustawienia domyślne zabezpieczeń. Wyłącz ustawienia domyślne zabezpieczeń i skonfiguruj zasady dostępu warunkowego. <br><br> Aby uzyskać więcej informacji, zobacz [Typowe zasady dostępu warunkowego](/azure/active-directory/conditional-access/concept-conditional-access-policy-common). |

### <a name="self-service-password-reset"></a>Samodzielne resetowanie hasła

Funkcję samodzielnego resetowania hasła (SSPR) można włączyć dla wszystkich Microsoft Managed Desktop z wyjątkiem Microsoft Managed Desktop kont usługi. <br><br> Aby uzyskać więcej informacji, zobacz Samouczek: umożliwianie użytkownikom odblokowania konta lub resetowania haseł za [Azure Active Directory funkcji samodzielnego resetowania hasła](/azure/active-directory/authentication/tutorial-enable-sspr).

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Upewnij się, że ustawienie SSPR **Selected** (Wybrane SSPR) obejmuje Microsoft Managed Desktop użytkowników, ale nie Microsoft Managed Desktop kont usług. Microsoft Managed Desktop usług nie mogą działać zgodnie z oczekiwaniami, gdy jest włączona funkcja SSPR. |

### <a name="standard-user-role"></a>Standardowa rola użytkownika

W przypadku użytkowników z przypisanymi rolami administratora globalnego i administratora Azure Active Directory użytkownicy Microsoft Managed Desktop będą użytkownikami standardowymi bez uprawnień administratora lokalnego. Wszystkim innym użytkownikom zostanie przypisana standardowa rola użytkownika po uruchomieniu swojego Microsoft Managed Desktop urządzenia.

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Microsoft Managed Desktop użytkownicy nie będą mieli uprawnień administratora lokalnego na swoich urządzeniach Microsoft Managed Desktop urządzeniach po zarejestrowaniu się. |

## <a name="microsoft-365-apps-for-enterprise"></a>Aplikacje usługi Microsoft 365 dla przedsiębiorstw

### <a name="onedrive"></a>OneDrive

Ustawienie **Zezwalaj na synchronizację tylko na** komputerach przyłącznych do określonych domen będzie kolidować z Microsoft Managed Desktop. Dostęp do OneDrive można uzyskać w centrum OneDrive [administracyjnego](https://admin.onedrive.com).

| Result (Wynik)  | Znaczenie |
| ----- | ----- |
| Porada | Używasz ustawienia Zezwalaj na synchronizację **tylko na komputerach przyłączony do określonych domen** . To ustawienie nie działa w przypadku Microsoft Managed Desktop. Wyłącz to ustawienie. Zamiast tego skonfiguruj zasady OneDrive dostępu warunkowego. <br><br> Aby uzyskać więcej informacji, zobacz [Planowanie wdrożenia dostępu warunkowego,](/azure/active-directory/conditional-access/plan-conditional-access) aby uzyskać pomoc. |
