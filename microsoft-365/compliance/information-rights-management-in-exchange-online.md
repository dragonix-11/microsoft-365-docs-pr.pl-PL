---
title: Exchange Online szyfrowania poczty przy użyciu usług AD RMS
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 2c956776-0016-4be6-b4cd-133a237f4a9e
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak Exchange Online usługi IRM w celu używania lokalnej usługi zarządzania prawami dostępu w usłudze Active Directory (AD RMS) w celu spełnienia wymagań organizacji.
ms.openlocfilehash: 867293d5afa29242409cc92702ff8b505ed21196
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984608"
---
# <a name="exchange-online-mail-encryption-with-ad-rms"></a>Exchange Online szyfrowania poczty przy użyciu usług AD RMS

Aby ułatwić zapobieganie wyciekowi informacji, Exchange Online funkcje zarządzania prawami do informacji (IRM), które zapewniają ochronę online i offline wiadomości e-mail i załączników. Usługę IRM Exchange Online w celu spełnienia wymagań organizacji w razie potrzeby, aby korzystać z lokalnej usługi zarządzania prawami dostępu w usłudze Active Directory (AD RMS). Nie jest to typowe. Jeśli nie ma wymagania używania usług AD RMS, użyj usługi AD RMS, [Szyfrowanie wiadomości usługi Office 365 serwera.](ome.md) 

Ochrona usługi IRM może być stosowana przez użytkowników w Outlook Microsoft Outlook w sieci Web i Outlook w sieci Web, a ponadto może być stosowana przez administratorów za pomocą reguł ochrony transportu lub Outlook ochrony. Dzięki u ciebie i Twoim użytkownikom możesz kontrolować, kto może uzyskać dostęp do poufnych danych, przesyłać je dalej, drukować lub kopiować w wiadomości e-mail.
  
## <a name="changes-to-how-irm-works-with-office-365-message-encryption-ome-and-azure-active-directory"></a>Zmiany sposobu działania usługi IRM z Szyfrowanie wiadomości usługi Office 365 (OME) i Azure Active Directory

Od września 2017 r. po skonfigurowaniu nowych funkcji usługi Szyfrowanie wiadomości usługi Office 365 dla organizacji możesz również skonfigurować usługę IRM do używania z usługą Azure Rights Management (Azure RMS). Usługa IRM nie jest już konfigurowanie usługi IRM z usługą Azure RMS oddzielnie. Zamiast tego OME i zarządzanie prawami dostępu działają bezproblemowo razem. Aby uzyskać więcej szczegółowych informacji o nowych możliwościach, zobacz Szyfrowanie wiadomości usługi Office 365 [często zadawanych pytań](./ome-faq.yml). Aby rozpocząć korzystanie z nowych funkcji OME w organizacji, zobacz Konfigurowanie nowych funkcji usługi Szyfrowanie wiadomości usługi Office 365 [wbudowanych w usługę Azure Information Protection](./set-up-new-message-encryption-capabilities.md).
  
## <a name="how-irm-works-with-exchange-online-and-active-directory-rights-management-services"></a>Jak działa Exchange Online IRM Usługi Active Directory Rights Management

Exchange Online IRM używa oprogramowania lokalnego Usługi Active Directory Rights Management (AD RMS), technologii ochrony informacji w programie Windows Server 2008 i nowszych. Ochrona usługi IRM jest stosowana do wiadomości e-mail przez zastosowanie szablonu zasad praw usług AD RMS do wiadomości e-mail. Do wiadomości są dołączane prawa, dzięki czemu ochrona jest chroniony w trybie online i offline oraz wewnątrz i poza zaporą organizacji.
  
Użytkownicy mogą zastosować szablon do wiadomości e-mail, aby kontrolować uprawnienia adresatów do wiadomości. Działania, takie jak przesyłanie dalej, wyodrębnianie informacji z wiadomości, zapisywanie wiadomości lub drukowanie wiadomości, można kontrolować, stosując do wiadomości zasady praw usług AD RMS.
  
Usługę IRM można skonfigurować do używania serwera USŁUG AD RMS z Windows Server 2008 lub nowszym. Za pomocą tego serwera usług AD RMS możesz zarządzać szablonami zasad praw usług AD RMS dla organizacji opartej na chmurze. Outlook także od serwera usług AD RMS w celu umożliwienia użytkownikom stosowania ochrony usługi IRM do wysyłanych wiadomości. Aby uzyskać szczegółowe informacje, [zobacz Konfigurowanie usługi IRM do używania lokalnego serwera usług AD RMS](configure-irm-to-use-an-on-premises-ad-rms-server.md). 
  
Po włączeniu tej funkcji ochronę usługi IRM można stosować do wiadomości w następujący sposób:
  
- **Użytkownicy mogą ręcznie zastosować szablon przy Outlook i Outlook w sieci Web.** Użytkownicy mogą zastosować szablon zasad praw usług AD RMS do wiadomości e-mail, wybierając szablon z listy **Ustaw** uprawnienia. Gdy użytkownicy wysyłają wiadomości chronione za pomocą usługi IRM, wszelkie dołączone pliki w obsługiwanym formacie również otrzymują tę samą ochronę usługi IRM co wiadomość. Ochrona usługi IRM jest stosowana do plików skojarzonych z programem Word, Excel i PowerPoint, a także do plików XPS i załączonych wiadomości e-mail. 
    
- **Za pomocą reguł ochrony transportu administratorzy mogą automatycznie stosować ochronę usługi IRM zarówno Outlook, jak i do Outlook w sieci Web.** Aby chronić wiadomości za pomocą usługi IRM, możesz utworzyć reguły ochrony transportu. Skonfiguruj akcję reguły ochrony transportu w celu zastosowania szablonu zasad praw usług AD RMS do wiadomości, które spełniają warunek reguły. Po włączeniu usługi IRM dostępne są szablony zasad usług AD RMS organizacji do użytku z akcją "Zastosuj ochronę praw" do **wiadomości**.
    
- **Administratorzy mogą tworzyć Outlook ochrony.** Outlook ochrony automatycznie zastosują ochronę usługi IRM do wiadomości w programie Outlook 2010 (nie dla systemu Outlook w sieci Web) na podstawie warunków wiadomości, które obejmują dział nadawcy, adresata wiadomości i czy adresaci znajdują się w organizacji, czy spoza organizacji. Aby uzyskać szczegółowe informacje, [zobacz Tworzenie Outlook ochrony.](/exchange/create-an-outlook-protection-rule-exchange-2013-help)
