---
title: Szyfrowanie poczty usługi Exchange Online za pomocą usług AD RMS
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
description: Dowiedz się, jak skonfigurować Exchange Online IRM do używania usługi lokalna usługa Active Directory Rights Management (AD RMS) w celu spełnienia wymagań organizacji.
ms.openlocfilehash: 926bea0b1f9379d2eaad2bc7c5bd672f98329b8a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628798"
---
# <a name="exchange-online-mail-encryption-with-ad-rms"></a>Szyfrowanie poczty usługi Exchange Online za pomocą usług AD RMS

Aby zapobiec wyciekom informacji, Exchange Online obejmuje funkcje zarządzania prawami do informacji (IRM), które zapewniają ochronę wiadomości e-mail i załączników w trybie online i offline. W razie potrzeby można skonfigurować Exchange Online IRM do korzystania z usługi lokalna usługa Active Directory Rights Management Service (AD RMS) w celu spełnienia wymagań organizacji. Nie jest to powszechne. Jeśli nie masz wymagania dotyczącego używania usług AD RMS, zamiast tego użyj [Szyfrowanie wiadomości w Microsoft Purview](ome.md).

Ochrona za pomocą usługi IRM może być stosowana przez użytkowników w programie Microsoft Outlook lub Outlook w sieci Web i może być stosowana przez administratorów przy użyciu reguł ochrony transportu lub reguł ochrony programu Outlook. Usługa IRM pomaga Tobie i Twoim użytkownikom kontrolować, kto może uzyskiwać dostęp, przesyłać dalej, drukować lub kopiować poufne dane w wiadomości e-mail.
  
## <a name="changes-to-how-irm-works-with-message-encryption-and-azure-active-directory"></a>Zmiany sposobu działania usługi IRM z szyfrowaniem komunikatów i usługą Azure Active Directory

Od września 2017 r. podczas konfigurowania Szyfrowanie wiadomości w Microsoft Purview dla organizacji skonfigurowano również usługę IRM do użycia z usługą Azure Rights Management (Azure RMS). Nie konfigurujesz już usługi IRM z usługą Azure RMS oddzielnie. Zamiast tego szyfrowanie komunikatów i zarządzanie prawami współdziałają ze sobą bezproblemowo. Aby uzyskać więcej informacji na temat Szyfrowanie wiadomości w Microsoft Purview, zobacz [Message Encryption FAQ (Często zadawane pytania dotyczące szyfrowania komunikatów](./ome-faq.yml)). Jeśli wszystko jest gotowe do rozpoczęcia korzystania z Szyfrowanie wiadomości w Microsoft Purview w organizacji, zobacz [Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](./set-up-new-message-encryption-capabilities.md).
  
## <a name="how-irm-works-with-exchange-online-and-active-directory-rights-management-services"></a>Jak usługa IRM współpracuje z usługami Exchange Online i Active Directory Rights Management

Exchange Online IRM używa usług lokalna usługa Active Directory Rights Management Services (AD RMS), technologii ochrony informacji w systemie Windows Server 2008 lub nowszym. Ochrona za pomocą usługi IRM jest stosowana do poczty e-mail przez zastosowanie szablonu zasad praw usług AD RMS do wiadomości e-mail. Prawa są dołączane do samego komunikatu, aby ochrona odbywała się w trybie online i offline oraz wewnątrz i na zewnątrz zapory organizacji.
  
Użytkownicy mogą zastosować szablon do wiadomości e-mail w celu kontrolowania uprawnień, które adresaci mają do wiadomości. Akcje, takie jak przekazywanie dalej, wyodrębnianie informacji z komunikatu, zapisywanie komunikatu lub drukowanie komunikatu, mogą być kontrolowane przez zastosowanie zasad praw usług AD RMS do wiadomości.
  
Usługę IRM można skonfigurować tak, aby używała serwera usług AD RMS z systemem Windows Server 2008 lub nowszym. Ten serwer usług AD RMS umożliwia zarządzanie szablonami zasad praw usług AD RMS dla organizacji opartej na chmurze. Program Outlook korzysta również z serwera usług AD RMS, aby umożliwić użytkownikom stosowanie ochrony za pomocą usługi IRM do wysyłanych komunikatów. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie usługi IRM do korzystania z lokalnego serwera usług AD RMS](configure-irm-to-use-an-on-premises-ad-rms-server.md).
  
Po włączeniu ochrony za pomocą usługi IRM można zastosować do komunikatów w następujący sposób:
  
- **Użytkownicy mogą ręcznie zastosować szablon przy użyciu programu Outlook i Outlook w sieci Web.** Użytkownicy mogą zastosować szablon zasad praw usług AD RMS do wiadomości e-mail, wybierając szablon z listy **Ustaw uprawnienia** . Gdy użytkownicy wysyłają komunikat chroniony przez usługę IRM, wszystkie dołączone pliki korzystające z obsługiwanego formatu również otrzymują taką samą ochronę IRM jak komunikat. Ochrona za pomocą usługi IRM jest stosowana do plików skojarzonych z programami Word, Excel i PowerPoint, a także plików xps i dołączonych wiadomości e-mail.

- **Administratorzy mogą używać reguł ochrony transportu do automatycznego stosowania ochrony za pomocą usługi IRM zarówno w programie Outlook, jak i w Outlook w sieci Web.** Reguły ochrony transportu można tworzyć do komunikatów ochrony za pomocą usługi IRM. Skonfiguruj akcję reguły ochrony transportu, aby zastosować szablon zasad praw usług AD RMS do komunikatów spełniających warunek reguły. Po włączeniu usługi IRM szablony zasad praw usług AD RMS organizacji są dostępne do użycia z akcją reguły ochrony transportu o nazwie **Zastosuj ochronę praw do komunikatu**.

- **Administratorzy mogą tworzyć reguły ochrony programu Outlook.** Reguły ochrony programu Outlook automatycznie stosują ochronę za pomocą usługi IRM do komunikatów w programie Outlook 2010 (nie Outlook w sieci Web) na podstawie warunków wiadomości, które obejmują dział nadawcy, do kogo wysyłany jest komunikat oraz czy adresaci znajdują się w organizacji, czy poza nią. Aby uzyskać szczegółowe informacje, zobacz [Tworzenie reguły ochrony programu Outlook](/exchange/create-an-outlook-protection-rule-exchange-2013-help).
