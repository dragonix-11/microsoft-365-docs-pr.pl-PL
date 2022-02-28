---
title: Korzystanie z tożsamości, urządzenia i ochrony przed zagrożeniami na podstawie przepisów dotyczących prywatności danych
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Zapobieganie naruszeniem danych osobowych za pomocą usług ochrony przed zagrożeniami, takich jak tożsamość, urządzenie i Microsoft 365.
ms.openlocfilehash: a5aa97637b0d44b762d1a1146effdefb932ab47d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988328"
---
# <a name="use-identity-device-and-threat-protection-for-data-privacy-regulation"></a>Korzystanie z tożsamości, urządzenia i ochrony przed zagrożeniami na podstawie przepisów dotyczących prywatności danych

Microsoft 365 udostępnia szereg funkcji ochrony tożsamości, urządzeń i zagrożeń, które organizacje mogą stosować w celu zapewnienia zgodności z przepisami dotyczącymi zgodności z przepisami dotyczącymi prywatności. W tym artykule opisano wymagania związane z przepisami dotyczącymi prywatności danych w tych obszarach oraz przedstawiono listę powiązanych funkcji i usług Microsoft 365 z linkami do dodatkowych informacji, które ułatwiają spełnianie wymagań implementacji.

## <a name="how-identity-device-and-threat-protection-relate-to-data-privacy-regulation"></a>Jak tożsamość, urządzenie i ochrona przed zagrożeniami są związane z przepisami dotyczącymi prywatności danych

Mimo że przepisy dotyczące prywatności danych różnią się w zależności od ich specyfiki, istota tego, czego dotyczy, znajduje się w artykule 5(1)(f) RODO, który stanowi:

- Dane osobowe będą przetwarzane w sposób zapewniający odpowiednie bezpieczeństwo danych osobowych, w tym ochronę przed nieautoryzowanym lub niezgodnym z prawem przetwarzaniem oraz przed przypadkową utratą, naruszeniem lub uszkodzeniem, przy użyciu odpowiednich środków technicznych lub organizacyjnych (integralności i poufności).

Naruszenie danych osobowych jest często spowodowane naruszeniem konta administracyjnego lub użytkownika końcowego oraz złośliwym dostępem do systemu. Na przykład włamanie się na konto administratora może prowadzić do złamania numerów kart kredytowych klientów lub innych informacji osobistych. Wszystkie ogólnie zalecane zasady ochrony tożsamości, urządzeń i zagrożeń dostępne w Microsoft 365 powinny zostać zaimplementowane, co będzie odzwierciedlane w wyniku zachowania zgodności w Menedżerze zgodności.

## <a name="using-the-results-of-your-assessment-work-and-compliance-manager"></a>Korzystanie z wyników pracy testowej i Menedżera zgodności

Menedżer zgodności obejmuje tożsamość, urządzenie i ochronę przed zagrożeniami przy użyciu następujących kategorii:

- Tożsamość odpowiada kategorii **kontroli dostępu**
- Urządzenie odpowiada kategorii **Zarządzanie urządzeniami**
- Ochrona przed zagrożeniami odpowiada kategorii **Ochrona przed zagrożeniami**
 
Jeśli zostały one wybrane w naszym przykładowym zestawie czterech głównych przepisów dotyczących prywatności danych, Menedżer zgodności określa 90 działań udoskonalania, z których większość jest określana jako "27". W związku z tym, że menedżer zgodności nazywa taką dużą liczbę w przypadku tych kategorii, niektóre z tych najczęstszych wymieniono tutaj w celu ich odwołania.

Użyj [Azure Active Directory (Azure AD) jako](https://azure.microsoft.com/services/active-directory/) tożsamości i kategorii **Kontrola dostępu**, za pomocą której możesz:

- Wdrożenie uwierzytelniania z zapobieganiem atakom typu "Man in the middle" (implementacja uwierzytelniania zapobiegającego atakom typu "Man in the middle")
- Blokuj starsze uwierzytelnianie.
- Konfigurowanie zasad ryzyka użytkownika i ryzyka logowania użytkownika.
- Włącz dostęp warunkowy i uwierzytelnianie wieloskładnikowe (MFA) dla administratorów i osób niebędących administratorami.
- Konfigurowanie i wymuszanie zasad haseł.
- Ogranicz dostęp do kont uprzywilejowanych za pomocą usługi Azure AD Privileged Identity Management.
- Wyłącz dostęp po zakończeniu.
- Inspekcja kont użytkowników i zmian stanu.
- Przegląd zmian grupy ról i zmian administracyjnych.

Użyj [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) dla urządzeń i kategorii **Zarządzanie urządzeniami**, za pomocą której możesz:

- Blokuj uszkodzone i rootowane urządzenia przenośne.
- Skonfiguruj usługę Intune do zarządzania urządzeniami przenośnymi.
- Tworzenie zasad zgodności dla systemów Android, iOS, macOS Windows przenośnych.
- Utwórz profil konfiguracji urządzenia dla urządzeń z systemem Android, iOS, macOS Windows urządzeniach.
- Tworzenie zasad ochrony aplikacji dla systemu iOS i Windows.
- Ukrywaj informacje za pomocą ekranu blokady.
- Implementowanie zasad haseł dla urządzeń przenośnych.
- Wymagaj urządzeń przenośnych, aby zablokować się w przypadku braku aktywności.
- Wymagaj urządzeń przenośnych do czyszczenia wielu błędów logowania.

Użyj [Exchange Online Protection i Microsoft Defender, Office 365](../security/office-365-security/defender-for-office-365.md) kategorii Ochrona **przed** zagrożeniami, za pomocą której możesz:

- Włączanie uwierzytelniania nadawcy (SPF, DMARC i DKIM).
- Skonfiguruj program Microsoft Defender na Office 365 ochrony przed wyłudzaniem informacji.
- Implementowanie Sejf załączników.
- Implementowanie Sejf sieci.
- Wdrażanie zasad wykrywania złośliwego oprogramowania i reakcji.
- Implementowanie zasad spamu przychodzącego i wychodzącego.

### <a name="references"></a>Odwołania:

- [Typowe zasady dostępu do urządzeń i tożsamości](../security/office-365-security/identity-access-policies.md)
- [Ochrona przed zagrożeniami w Office 365](https://support.office.com/article/protect-against-threats-in-office-365-b10023f6-f30f-45d3-b3ad-b71aa4aa0d58)
- [Sejf załączników](../security/office-365-security/safe-attachments.md)
- [Bezpieczne linki](../security/office-365-security/safe-links.md)
- [Bezpieczne dokumenty](../security/office-365-security/safe-docs.md)
