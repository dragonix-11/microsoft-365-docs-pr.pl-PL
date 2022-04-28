---
title: Usługa Azure AD Identity Protection dla środowiska testowego Microsoft 365 dla przedsiębiorstw
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Skonfiguruj usługę Azure AD Identity Protection i przeanalizuj bieżące konta w Microsoft 365 dla środowiska testowego przedsiębiorstwa.
ms.openlocfilehash: 1f947f9b74b1909aa1e6451ec835a2ad78964f75
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078762"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>Usługa Azure AD Identity Protection dla środowiska testowego Microsoft 365 dla przedsiębiorstw

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

Usługa Azure Active Directory (Azure AD) Identity Protection umożliwia wykrywanie potencjalnych luk w zabezpieczeniach wpływających na tożsamości organizacji, konfigurowanie automatycznych odpowiedzi i badanie zdarzeń. W tym artykule opisano sposób używania usługi Azure AD Identity Protection do wyświetlania analizy kont środowiska testowego.

Konfigurowanie usługi Azure AD Identity Protection w Microsoft 365 dla środowiska testowego przedsiębiorstwa obejmuje dwie fazy:

- [Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Faza 2. Korzystanie z usługi Azure AD Identity Protection](#phase-2-use-azure-ad-identity-protection)

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa

Jeśli chcesz przetestować usługę Azure AD Identity Protection tylko w lekki sposób z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz przetestować usługę Azure AD Identity Protection w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w temacie [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie usługi Azure AD Identity Protection nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Active Directory Domain Services (AD DS). Jest ona dostępna tutaj jako opcja, dzięki czemu można przetestować usługę Azure AD Identity Protection i poeksperymentować z nią w środowisku reprezentującym typową organizację.
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>Faza 2. Korzystanie z usługi Azure AD Identity Protection

1. Otwórz prywatne wystąpienie przeglądarki i zaloguj się do Azure Portal przy [https://portal.azure.com](https://portal.azure.com) użyciu konta administratora globalnego Microsoft 365 dla środowiska testowego przedsiębiorstwa.
2. W Azure Portal wpisz **ochronę tożsamości** w polu wyszukiwania, a następnie wybierz pozycję **Azure AD Identity Protection**.
3. W bloku **Identity Protection — przegląd** wybierz każdy raport, aby zobaczyć, co raportuje.
4. W obszarze **Powiadom** wybierz pozycję **Użytkownicy z podwyższonym ryzykiem wykrytych alertów**.
5. W okienku **Alerty wykryte przez użytkowników zagrożonych** wybierz pozycję **Średni**.
6. W polu **Wiadomości e-mail są wysyłane do następujących użytkowników** wybierz pozycję **Dołączono** i sprawdź, czy twoje konto administratora globalnego znajduje się na liście wybranych członków.
7. Wybierz **Zapisz**.

W obszarze **Ochrona** wybierz różne zasady, aby zobaczyć, jak je skonfigurować. Jeśli tworzysz i aktywujesz zasady, upewnij się, że nie blokuje on dostępu dla wszystkich użytkowników lub nie możesz się zalogować. Aby temu zapobiec, należy wykluczyć określone konta użytkowników, takie jak administratorzy globalni.

Aby uzyskać więcej informacji na temat testowania i eksperymentowania, zobacz [Symulowanie zdarzeń ryzyka](/azure/active-directory/active-directory-identityprotection-playbook).

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [tożsamości](m365-enterprise-test-lab-guides.md#identity) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Wdrażanie tożsamości](deploy-identity-solution-overview.md)

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)