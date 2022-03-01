---
title: Instalowanie Microsoft Project Microsoft Visio na Microsoft Managed Desktop urządzeniach
description: Informacje o instalowaniu Microsoft Project microsoft Visio na Microsoft Managed Desktop urządzeniach
keywords: Microsoft Managed Desktop, Microsoft 365, Microsoft Project, Microsoft Visio
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.date: 03/07/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: ab8a68ed17a8705c6e391371600d7b56660f6c57
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013900"
---
# <a name="install-microsoft-project-or-microsoft-visio-on-microsoft-managed-desktop-devices"></a>Instalowanie Microsoft Project Microsoft Visio na Microsoft Managed Desktop urządzeniach

Microsoft Project i Microsoft Visio wymagają, aby na Microsoft Managed Desktop urządzeniach zostały zainstalowane Microsoft Managed Desktop czynności. Ten artykuł zawiera dokumentację wymagań wstępnych i procesu instalacji tych aplikacji.

## <a name="prerequisites"></a>Wymagania wstępne

Administratorzy powinni upewnić się, że spełniają następujące wymagania wstępne:

| Wymagania wstępne | Opis |
| ------ | ------ |
| Liczby licencji | Poprawna ilość Microsoft Project licencji Visio firmy Microsoft musi być dostępna dla użytkowników. Microsoft Managed Desktop obecnie obsługuje tylko 64-bitowe wersje tych aplikacji. |
| Nazwy licencji | Odpowiednie nazwy licencji dla tych aplikacji to: <ul><li>**Microsoft Project** — Project Online Professional lub Project Online Premium</li><li>**Microsoft Visio** — Visio Online (plan 2)</li><ul> |
| Portal firmy | Aby użytkownicy Portal firmy zainstalować te aplikacje, administrator musi być dostępny w Twojej dzierżawie. Jeśli Portal firmy nie jest wdrożone w Twojej dzierżawie[, zobacz Portal firmy](company-portal.md). |

## <a name="deploy-project-and-visio-for-microsoft-managed-desktop-devices"></a>Wdrażanie Project i Visio dla Microsoft Managed Desktop urządzeniach

Microsoft Managed Desktop dodasz Microsoft Project Microsoft Visio jako dwie aplikacje Win32 w Microsoft Intune. Utworzymy również dwie grupy w Azure Active Directory. Grupy zostaną przypisane do odpowiedniej aplikacji z celem "Dostępny".

**Aby wdrożyć Project i Visio:**

Dodaj użytkownika do odpowiedniej grupy, a aplikacja stanie się dostępna w Portal firmy. Synchronizacja może potrwać kilka minut, ale użytkownicy mogą zainstalować aplikacje z usługi Portal firmy.

Nazwa grupy usługi Azure AD | Którzy użytkownicy mają zostać przypisani?
 --- | ---
Nowoczesne Office-Project_Install | Użytkownicy potrzebujący Project
Nowoczesne Office-Visio_Install | Użytkownicy potrzebujący Visio

## <a name="communicate-changes"></a>Zakomunikuj zmiany

Administratorzy IT powinni wiedzieć, jak instalować aplikacje i Project i Visio. Ta komunikacja obejmuje:

- Powiadamianie użytkowników, gdy te aplikacje są dla nich dostępne.
- Instrukcje dotyczące instalowania tych aplikacji z Portal firmy.
