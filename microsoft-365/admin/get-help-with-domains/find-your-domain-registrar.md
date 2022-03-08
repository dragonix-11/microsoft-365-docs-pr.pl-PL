---
title: Znajdowanie rejestratora nazw domen
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: b5b633ba-1e56-4a98-8ff5-2acaac63a5c8
description: Dowiedz się, jak znaleźć rejestratora domen i dostawcę hostingu DNS przy użyciu wyszukiwania internicjowego.
ms.openlocfilehash: c7802067bc3d8397d9f7b7ddf0f6cda4dd57c38b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316873"
---
# <a name="find-your-domain-registrar"></a>Znajdowanie rejestratora nazw domen

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

## <a name="domain-registrar"></a>Rejestrator domeny

### <a name="find-your-domain-name-registrar"></a>Znajdowanie rejestratora nazw domen

> [!NOTE]
> Tylko domeny kończące się na *.COM*, *.NET* i *.EDU* współdziałają z tym narzędziem.

1. Na [stronie wyszukiwania usługi InterNIC](https://go.microsoft.com/fwlink/p/?LinkId=402770) w polu **Whois Search** (Wyszukiwanie whois) wpisz nazwę swojej domeny. Na przykład  *contoso.com.*

2. Wybierz opcję **Domain** (Domena), a następnie wybierz przycisk **Submit** (Prześlij).

3. Na stronie **Whois Search Results** (Wyniki wyszukiwania w usłudze whois) znajdź wpis **Registrar** (Rejestrator). Ten wpis wskazuje organizację będącą rejestratorem Twojej domeny.

## <a name="dns-hosting-provider"></a>Dostawca hostingu DNS

### <a name="find-your-dns-hosting-provider"></a>Znajdowanie dostawcy hostingu DNS

> [!NOTE]
> Tylko domeny kończące się na *.COM*, *.NET* i *.EDU* współdziałają z tym narzędziem.

1. Na [stronie wyszukiwania usługi InterNIC](https://go.microsoft.com/fwlink/p/?LinkId=402770) w polu **Whois Search** (Wyszukiwanie whois) wpisz nazwę swojej domeny. Na przykład contoso.com.

2. Wybierz opcję **Domain** (Domena), a następnie wybierz przycisk **Submit** (Prześlij).

3. Na stronie **Whois Search Results** (Wyniki wyszukiwania w usłudze whois) najpierw znajdź wpis **Name Server** (Serwer nazw).

4. Skopiuj informacje dotyczące serwera nazw (SN) występujące po dwukropku (:), a następnie wklej je w polu **Search** (Wyszukiwanie) u góry strony. Wybierz opcję **Nameserver** (Serwer nazw), a następnie wybierz przycisk **Submit** (Prześlij).

5. Na stronie **Whois Search Results** (Wyniki wyszukiwania w usłudze whois) znajdź wpis **Registrar** (Rejestrator). Ten wpis wskazuje dostawcę hostingu DNS, czyli dostawcę usług DNS będącego właścicielem serwera nazw dla Twojej domeny.

---

