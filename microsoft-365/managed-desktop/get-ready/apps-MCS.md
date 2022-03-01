---
title: Praca z usługami Microsoft Consulting Services
description: Przygotowanie i kroki, które należy wykonać w celu współpracy z usługą MCS w celu śledzenia pakietu aplikacji
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 5dd6bf62625d6b22a0585645abbeb24dabd6c9fd
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027102"
---
# <a name="working-with-microsoft-consulting-services"></a>Praca z usługami Microsoft Consulting Services

Możesz zaangażować się w usługę Microsoft Consulting Services (MCS), aby zapakować aplikacje do użytku z usługami firmy Microsoft Managed Desktop. Aby uzyskać więcej informacji, skontaktuj się ze swoim przedstawicielem klienta, aby skontaktować się z przedstawicielem firmy MCS w celu sprawdzenia projektu pakowania aplikacji.

## <a name="roles-and-responsibilities"></a>Role i obowiązki

| Rola | Odpowiedzialność |
| ------ | ------ |
| Ty | Aby pracować z opakowaniem aplikacji MCS, **musisz podać następujące elementy**: <ul><li> Pliki instalatora źródłowego (na przykład pliki setup.exe lub .msi).</li><li>Instrukcje instalacji z informacjami na temat wyglądu końcowej instalacji. Czy na przykład powinien być skrót na pulpicie do aplikacji? Jak powinien być widoczność aplikacji? Czy aplikacja powinna łączyć się z serwerem, a jeśli tak, to jaki? Aby uzyskać więcej informacji, zobacz [szablon żądania pakowania aplikacji](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/app-packaging-template.docx).</li><li>Musisz przeprowadzić własne testowanie akceptacji, aby sprawdzić, czy aplikacja działa zgodnie z oczekiwaniami w Twoim środowisku.</li><ul> |
| Microsoft Consulting Services (MCS) | **Firma MCS zajmie się następującymi czynnościami:** <ul><li>Sprawdź, czy aplikacja jest zabroniona, czy ograniczona w Microsoft Managed Desktop środowisku.</li><li>Przetestuj instalację, uruchomienie i odinstalowanie aplikacji, aby zapewnić zgodność Windows 10. Jeśli firma MCS odkryje problem ze zgodnością, przekazała aplikację do programu [App Assure](/fasttrack/products-and-capabilities#app-assure) w celu rozwiązania problemów.</li><li>Spakuj aplikację do specyfikacji i przetestuj jej wdrożenie przy użyciu Microsoft Intune.</li><ul>

## <a name="app-delivery-schedule"></a>Harmonogram dostarczania aplikacji

Rozpocznij proces pakowania, przesyłając informacje o aplikacji do Microsoft Managed Desktop aplikacji. Zespół do pakowania przegląda nowe zgłoszenia w każdy czwartek. Po przejrzeniu i opakowaniu spakowane aplikacje zostaną dostarczone w piątek. Do uruchomienia można spakować maksymalnie pięć aplikacji na tydzień, ale usługa może spełniać Twoje potrzeby.

![kalendarz przedstawiający przepływ aplikacji w czwartek (21. w tym przykładzie), sprawdzanie poprawności multimediów następnego dnia, pakowanie w poniedziałek (25) i dostarczenie aplikacji w piątek (29. dzień).](../../media/MCS-cal.png)

Otrzymasz powiadomienie, gdy aplikacja zostanie dostarczona. W tym momencie masz 21 dni na przeprowadzenie testów akceptacji i zatwierdzenie pracy w portalu Microsoft Managed Desktop danych. Jeśli podczas testowania akceptacji odkryjesz problem z aplikacją, odrzuć ją w portalu Microsoft Managed Desktop aplikacji. Aby zrozumieć i rozwiązać ten problem, połączysz się za pośrednictwem poczty e-mail za pomocą pakietu usług Microsoft Consulting Services (MCS).

## <a name="testing-accounts-and-environment"></a>Testowanie kont i środowiska

Aby zespół do spraw pakowania dokończył migrację do Microsoft Intune, zalecamy podanie pewnych uprawnień:

- Dostęp Microsoft Intune wdrażania aplikacji dla spakowanego oprogramowania w celu dodania i przypisania aplikacji.
- Przetestuj grupy, konta użytkowników i licencje, aby pakiety mogły testować aplikacje.

Firma MCS użyje tych uprawnień do wykonania następujących czynności:

- Upewnij się, że aplikacja działa na maszyny wirtualnej skonfigurowanej do Microsoft Managed Desktop.
- Upload aplikację, Microsoft Intune do wdrożenia u użytkowników.

Bez tych uprawnień firma MCS może przejść do przodu, ale nie będzie mogła przekazywać aplikacji do środowiska.
