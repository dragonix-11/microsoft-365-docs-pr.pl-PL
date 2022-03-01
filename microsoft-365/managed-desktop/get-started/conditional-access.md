---
title: Dostosowywanie ustawień po rejestracji
description: Jak wykluczyć pewne konta Microsoft
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 86e2645891afef2523fb8dc80ec0d9a59b094fc4
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016072"
---
# <a name="adjust-settings-after-enrollment"></a>Dostosowywanie ustawień po rejestracji

Po zakończeniu rejestracji w programie Microsoft Managed Desktop może być konieczne dostosowanie niektórych ustawień zarządzania. Aby sprawdzić i dostosować w razie potrzeby, wykonaj następujące czynności:

1. Przejrzyj Microsoft Intune i Azure Active Directory opisane w następnej sekcji.
2. Jeśli którykolwiek z elementów ma zastosowanie do Twojego środowiska, dostosuj go zgodnie z opisem.
3. Jeśli chcesz sprawdzić poprawność wszystkich ustawień, możesz ponownie uruchomić narzędzie do oceny gotowości, aby upewnić [](https://aka.ms/mmdart) się, że nic nie powoduje konfliktów z Microsoft Managed Desktop.

> [!NOTE]
> Jeśli operacje będą kontynuowane w kolejnych miesiącach, jeśli po zarejestrowaniu się do zasad Microsoft Intune, Azure Active Directory lub Microsoft 365 wpływających na Microsoft Managed Desktop, możliwe, że Microsoft Managed Desktop może przestać działać poprawnie. Aby uniknąć problemów z usługą, przed zmianą wymienionych tam zasad [](../get-ready/readiness-assessment-fix.md) sprawdź konkretne ustawienia opisane w tece Rozwiązywanie problemów znalezionych przez narzędzie do oceny gotowości. W dowolnym momencie możesz również ponownie uruchomić narzędzie do oceny gotowości.

## <a name="microsoft-intune-settings"></a>Microsoft Intune sieci Microsoft Intune

| Ustawienie | Opis |
| ------ | ------ |
| Profil wdrożenia z autopilotem | Jeśli korzystasz z jakichkolwiek zasad rozwiązania Autopilot, zaktualizuj je, aby wykluczyć grupę **Nowoczesne urządzenia workplace — Wszystkie** usługi Azure AD. <br><br> **Aby zaktualizować zasady rozwiązania Autopilot:** <br><br> W **obszarze Zadania** w grupach **Wyklucz wybierz** grupę Nowoczesne urządzenia służbowe **— Wszystkie** urządzenia usługi Azure AD utworzoną podczas Microsoft Managed Desktop rejestracji. <br><br> Microsoft Managed Desktop także utworzyć profil rozwiązania Autopilot o nazwie "Nowoczesne miejsce pracy" (profil rozwiązania **Autopilot** w nowoczesnym miejscu pracy). Podczas aktualizowania własnych profilów rozwiązania Autopilot upewnij się,  że nie wykluczaj grupy Nowoczesne urządzenia workplace — Wszystkie **usługi Azure AD** z profilu rozwiązania **Modern Workplace Autopilot** utworzonego przez program Microsoft Managed Desktop. |
| Zasady dostępu warunkowego | Jeśli utworzysz jakiekolwiek nowe zasady dostępu warunkowego związane z usługą Azure AD, usługą Microsoft Intune lub programem Microsoft 365 Defender dla punktu końcowego po rejestracji, po zarejestrowaniu w usłudze Microsoft Managed Desktop wyklucz z nich grupę Kont **usługi Azure AD** w nowoczesnym miejscu pracy. Aby uzyskać więcej informacji, zobacz [Dostęp warunkowy: Użytkownicy i grupy](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). Microsoft Managed Desktop mają osobne zasady dostępu warunkowego w celu ograniczenia dostępu do tych kont. <br><br> **Aby zapoznać się z Microsoft Managed Desktop dostępu warunkowego (Nowoczesne miejsce pracy — bezpieczna stacja robocza):** <br><br> Przejdź do Microsoft Endpoint Manager i przejdź do ustawienia **Dostęp warunkowy w** **zabezpieczeniach punktu końcowego**. Nie modyfikuj żadnych zasad dostępu warunkowego usługi Azure AD utworzonych przez Microsoft Managed Desktop o nazwie "Nowoczesne miejsce pracy". |
| Uwierzytelnianie wieloskładnikowe | Jeśli utworzysz jakiekolwiek nowe wymagania uwierzytelniania wieloskładnikowego w zasadach dostępu warunkowego związanych z usługą Azure AD, Intune lub Microsoft 365 Defender dla punktu końcowego po rejestracji usługi Microsoft Managed Desktop, wyklucz z nich grupę Kont **usługi Azure AD** w nowoczesnym miejscu pracy. Aby uzyskać więcej informacji, zobacz [Dostęp warunkowy: Użytkownicy i grupy](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). Microsoft Managed Desktop mają osobne zasady dostępu warunkowego w celu ograniczenia dostępu do członków tej grupy. <br><br> **Aby przejrzeć Microsoft Managed Desktop dostępu warunkowego (Nowoczesne miejsce pracy - ):** <br><br> Przejdź do Microsoft Endpoint Manager i przejdź do ustawienia **Dostęp warunkowy w** **zabezpieczeniach punktu końcowego**.
| Windows 10 pierścienia aktualizacji | W przypadku Windows 10 zasad pierścienia aktualizacji, z każdej zasady wyklucz nowoczesne urządzenia w miejscu pracy — Wszystkie grupy **usługi Azure AD**. Aby uzyskać więcej informacji, zobacz [Tworzenie i przypisywanie pierścieni aktualizacji](/mem/intune/protect/windows-10-update-rings#create-and-assign-update-rings). <br><br> Microsoft Managed Desktop także utworzyć pewne zasady pierścienia aktualizacji, z których wszystkie będą zawierały nazwę "Nowoczesne miejsce pracy". Przykład: <ul><li>Zasady aktualizacji nowoczesnego miejsca pracy [Ogólne]</li><li>Zasady aktualizacji nowoczesnego miejsca pracy [szybkie aktualizacje]</li><li>Nowoczesne zasady aktualizacji miejsca pracy [pierwsza]</li><li>Zasady aktualizacji nowoczesnego miejsca pracy [Test]</li></ul> <br>Podczas aktualizowania własnych zasad upewnij się, że nie  wykluczaj grupy Nowoczesne urządzenia workplace **—** Wszystkie usługi Azure AD z tych, Microsoft Managed Desktop utworzonych. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory ustawień

Samodzielne resetowanie hasła: jeśli korzystasz z funkcji samodzielnego resetowania hasła dla wszystkich użytkowników, dostosuj przypisanie, aby wykluczyć Microsoft Managed Desktop kont usługi.

**Aby dostosować to zadanie:**

1. Tworzenie grupy dynamicznej usługi Azure AD dla wszystkich użytkowników z *wyjątkiem* Microsoft Managed Desktop usługi
1. Użyj tej grupy do przypisywania zamiast "wszyscy użytkownicy".

Aby ułatwić znajdowanie i wykluczanie kont usługi, możesz użyć przykładu zapytania dynamicznego:

```Console
(user.objectID -ne null) and (user.userPrincipalName -ne "MSADMIN@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSADMININT@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_SOC_RO@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_WDGSOC@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSTEST@TENANT.onmicrosoft.com")
```

W tym zapytaniu zastąp nazwę `@TENANT` domeny dzierżawy.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Procedura rozpoczynania pracy z Microsoft Managed Desktop

1. Portalu [administracyjnego programu](access-admin-portal.md) Access.
1. [Dodaj i zweryfikuj kontakty administratora w portalu administracyjnym](add-admin-contacts.md).
1. Dostosuj ustawienia po rejestracji (ten artykuł).
1. Wdrażanie i [przypisywanie Intune — Portal firmy](company-portal.md).
1. [Przypisywanie licencji](assign-licenses.md).
1. [Wdychuj aplikacje](deploy-apps.md).
1. [Konfigurowanie urządzeń](set-up-devices.md).
1. Skonfiguruj środowisko [pierwszego uruchomienia za pomocą rozwiązania Autopilot i strony stanu rejestracji](esp-first-run.md).
1. [Włączanie funkcji pomocy technicznej dla użytkowników](enable-support.md).
1. [Przygotuj użytkowników do korzystania z urządzeń](get-started-devices.md).
1. [Wprowadzenie do sterowania aplikacją](get-started-app-control.md).
