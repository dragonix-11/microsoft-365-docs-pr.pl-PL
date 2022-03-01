---
title: Usługa Azure AD Identity Protection dla środowiska Microsoft 365 testowania w przedsiębiorstwie
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Skonfiguruj usługę Azure AD Identity Protection i analizuj bieżące konta Microsoft 365 w środowisku testowania przedsiębiorstwa.
ms.openlocfilehash: 210736e0a950d74e0cd761463e9cc27f1dc3c721
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013876"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>Usługa Azure AD Identity Protection dla środowiska Microsoft 365 testowania w przedsiębiorstwie

*Ten przewodnik laboratorium testowego może być używany tylko w Microsoft 365 testowych w przedsiębiorstwie.*

Za pomocą usługi Azure Active Directory Identity Protection (Azure AD) możesz wykrywać potencjalne luki w zabezpieczeniach, które wpływają na tożsamości w organizacji, konfigurować automatyczne odpowiedzi i badać zdarzenia. W tym artykule opisano sposób używania usługi Azure AD Identity Protection do wyświetlania analizy testowych kont środowiska.

Konfigurowanie usługi Azure AD Identity Protection w środowisku Microsoft 365 testowania przedsiębiorstwa składa się z dwóch etapów:

- [Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Etap 2. Korzystanie z usługi Azure AD Identity Protection](#phase-2-use-azure-ad-identity-protection)

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa

Jeśli chcesz przetestować usługę Azure AD Identity Protection tylko w sposób podstawowy z minimalnymi wymaganiami, wykonaj instrukcje w teście Konfiguracja podstawowa [usługi Azure AD](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz przetestować usługę Azure AD Identity Protection w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w tece [uwierzytelnianie pass-through](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie usługi Azure AD Identity Protection nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Usługi domenowe w usłudze Active Directory (AD DS). Ta opcja umożliwia przetestowanie usługi Azure AD Identity Protection i eksperymentowanie z nią w środowisku reprezentującym typową organizację.
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>Etap 2. Korzystanie z usługi Azure AD Identity Protection

1. Otwórz prywatne wystąpienie przeglądarki i zaloguj się do portalu Azure Portal [https://portal.azure.com](https://portal.azure.com) za pomocą konta administratora globalnego Microsoft 365 testowania przedsiębiorstwa.
2. W portalu Azure Portal wpisz nazwę **ochrony tożsamości** w polu wyszukiwania, a następnie wybierz pozycję **Azure AD Identity Protection**.
3. Na **bladego podglądu funkcji Ochrona** tożsamości zaznacz każdy raport, aby sprawdzić, co jest raportem.
4. W **obszarze Powiadomienia** wybierz pozycję **Użytkownicy, których alerty są wykryte w przypadku ryzyka**.
5. W **okienku Alerty wykryte przez ryzyko** wybierz pozycję **Średni**.
6. W **przypadku Pozycji Wiadomości e-mail** są wysyłane do  następujących użytkowników wybierz pozycję Uwzględnione i sprawdź, czy Twoje konto administratora globalnego znajduje się na liście wybranych członków.
7. Wybierz **Zapisz**.

W **obszarze** Ochrona wybierz różne ustawienia zasad, aby dowiedzieć się, jak je skonfigurować. Jeśli utworzysz i aktywujesz zasady, upewnij się, że nie blokują one dostępu wszystkim użytkownikom lub nie możesz się zalogować. Aby temu zapobiec, wyklucz określone konta użytkowników, na przykład administratorów globalnych.

Aby uzyskać dalsze testy i eksperymenty, zobacz [Symulowanie zdarzeń ryzyka](/azure/active-directory/active-directory-identityprotection-playbook).

## <a name="next-step"></a>Następny krok

Poznaj [dodatkowe funkcje tożsamości](m365-enterprise-test-lab-guides.md#identity) i możliwości w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)