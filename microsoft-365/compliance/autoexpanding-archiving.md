---
title: Dowiedz się więcej na temat automatycznego rozszerzania archiwizacji
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 37cdbb02-a24a-4093-8bdb-2a7f0b3a19ee
description: Dowiedz się więcej na temat automatycznego rozszerzania archiwizacji, które zapewnia dodatkowy magazyn archiwum dla skrzynek pocztowych usługi Exchange Online.
ms.openlocfilehash: fc3e40e72ad287e7d7e696557422420cccbd4ee1
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922444"
---
# <a name="learn-about-auto-expanding-archiving"></a>Dowiedz się więcej na temat automatycznego rozszerzania archiwizacji

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W usłudze Office 365 archiwalne skrzynki pocztowe zapewniają użytkownikom dodatkowe miejsce do magazynowania skrzynki pocztowej. Po włączeniu archiwum skrzynki pocztowej użytkownika dostępna jest maksymalnie 100 GB dodatkowego magazynu. W przeszłości, gdy osiągnięto limit przydziału magazynu 100 GB, organizacje musiały skontaktować się z firmą Microsoft w celu zażądania dodatkowego miejsca do magazynowania dla archiwum skrzynki pocztowej. Tak już nie jest.

Funkcja archiwizacji w usłudze Microsoft 365 (nazywana *automatycznym rozszerzaniem archiwizacji*) zapewnia do 1,5 TB dodatkowego magazynu w archiwalnych skrzynkach pocztowych. Po osiągnięciu limitu przydziału magazynu w skrzynce pocztowej archiwum platforma Microsoft 365 automatycznie (i przyrostowo) zwiększa rozmiar archiwum, dopóki skrzynka pocztowa archiwum nie osiągnie 1,5 TB.

Aby uzyskać instrukcje krok po kroku dotyczące włączania automatycznego rozszerzania archiwizacji, zobacz [Włączanie automatycznego rozszerzania archiwizacji](enable-autoexpanding-archiving.md).

> [!NOTE]
> Automatyczne rozszerzanie archiwizacji obsługuje również udostępnione skrzynki pocztowe. Aby włączyć archiwum udostępnionej skrzynki pocztowej, wymagana jest licencja planu 2 usługi Exchange Online lub licencja planu 1 usługi Exchange Online z licencją archiwizacji usługi Exchange Online.

## <a name="how-auto-expanding-archiving-works"></a>Jak działa automatyczne rozszerzanie archiwizacji

Jak wyjaśniono wcześniej, dodatkowe miejsce do magazynowania skrzynki pocztowej jest tworzone po włączeniu archiwum skrzynki pocztowej użytkownika. Po włączeniu automatycznego rozszerzania archiwizacji platforma Microsoft 365 okresowo sprawdza rozmiar skrzynki pocztowej archiwum. Gdy skrzynka pocztowa archiwum zbliża się do limitu magazynu, platforma Microsoft 365 automatycznie tworzy dodatkowe miejsce do magazynowania dla archiwum. Jeśli użytkownikowi zabraknie tego dodatkowego miejsca do magazynowania, platforma Microsoft 365 doda więcej miejsca do archiwum użytkownika. Ten proces trwa do momentu, gdy archiwum użytkownika osiągnie rozmiar 1,5 TB. Ten proces odbywa się automatycznie, co oznacza, że administratorzy nie muszą żądać dodatkowego magazynu archiwum ani zarządzać automatycznym rozszerzaniem archiwizacji.

Oto krótkie omówienie tego procesu.

![Omówienie procesu automatycznego rozszerzania archiwizacji.](../media/74355385-d990-44fe-8a87-6c3639d1f63f.png)

1. Archiwizowanie jest włączone dla skrzynki pocztowej użytkownika lub udostępnionej skrzynki pocztowej. Zostanie utworzona archiwum skrzynki pocztowej z 100 GB miejsca do magazynowania, a limit przydziału ostrzeżeń dla archiwum skrzynki pocztowej jest ustawiony na 90 GB.

2. Administrator umożliwia automatyczne rozszerzanie archiwizacji skrzynki pocztowej. Jeśli do skrzynki pocztowej zastosowano zasady przechowywania lub przechowywania, limit przydziału magazynu dla archiwum skrzynki pocztowej zostanie zwiększony do 110 GB, a limit przydziału ostrzeżeń archiwum zostanie zwiększony do 100 GB.
    
    Następnie, gdy skrzynka pocztowa archiwum (w tym folder Elementy możliwe do odzyskania) osiągnie limit przydziału magazynu, skrzynka pocztowa archiwum zostanie przekonwertowana na automatycznie rozszerzające się archiwum. Dodatkowe miejsce do magazynowania jest dodawane do momentu osiągnięcia maksymalnego rozmiaru 1,5 TB. Aprowizowanie dodatkowego miejsca do magazynowania może potrwać do 30 dni.

3. Platforma Microsoft 365 automatycznie dodaje więcej miejsca do magazynowania w razie potrzeby.

> [!IMPORTANT]
> Automatyczne rozszerzanie archiwizacji jest obsługiwane tylko w przypadku skrzynek pocztowych używanych dla poszczególnych użytkowników (lub udostępnionych skrzynek pocztowych) z szybkością wzrostu, która nie przekracza 1 GB dziennie. Skrzynka pocztowa archiwum użytkownika jest przeznaczona tylko dla tego użytkownika. Kopiowanie wiadomości do archiwum skrzynki pocztowej przy użyciu reguł transportu lub reguł automatycznego przesyłania dalej jest niedozwolone. Firma Microsoft zastrzega sobie prawo do odmowy dodatkowej archiwizacji w przypadkach, gdy skrzynka pocztowa archiwum użytkownika jest używana do przechowywania danych archiwalnych dla innych użytkowników lub w innych przypadkach niewłaściwego użycia.

## <a name="what-gets-moved-to-the-additional-archive-storage-space"></a>Co zostanie przeniesione do dodatkowego miejsca do magazynowania archiwum?

Aby efektywnie korzystać z automatycznego rozszerzania magazynu archiwum, foldery mogą zostać przeniesione. Platforma Microsoft 365 określa, które foldery są przenoszone po dodaniu dodatkowego magazynu do archiwum. Czasami po przeniesieniu folderu co najmniej jeden podfolder jest tworzony automatycznie, a elementy z oryginalnego folderu są dystrybuowane do tych folderów w celu ułatwienia procesu przenoszenia. Podczas wyświetlania części archiwum listy folderów w programie Outlook te podfoldery są wyświetlane w oryginalnym folderze. Konwencja nazewnictwa używana przez platformę Microsoft 365 do nadawania nazw tym podfolderom jest **\<folder name\>_yyyy (utworzona na mmm dd, rrrr h_mm)**, gdzie:

- **yyyy** to rok, w który odebrano komunikaty w folderze.

- **mmm dd, rrrr h_m** to data i godzina utworzenia podfolderu przez usługę Office 365 w formacie UTC na podstawie strefy czasowej użytkownika i ustawień regionalnych w programie Outlook.

Poniższe zrzuty ekranu pokazują listę folderów przed i po przeniesieniu komunikatów do automatycznie rozwiniętej archiwum.

 **Przed dodaniem dodatkowego magazynu**

![Lista folderów skrzynki pocztowej archiwum przed aprowizowaniem automatycznego rozszerzania archiwum.](../media/5d6d6420-e562-4912-aaab-1c111762b3f6.png)

 **Po dodaniu dodatkowego magazynu**

![Lista folderów archiwum skrzynki pocztowej po automatycznym rozwijaniu archiwum jest aprowizowana.](../media/c03c5f51-23fa-4fc2-b887-7e7e5cce30da.png)

> [!NOTE]
> Zgodnie z wcześniejszym opisem platforma Microsoft 365 przenosi elementy do podfolderów (i nadaje im nazwy przy użyciu opisanej powyżej konwencji nazewnictwa), aby ułatwić dystrybucję zawartości do archiwum pomocniczego. Jednak przenoszenie elementów do podfolderów może nie zawsze mieć miejsce. Czasami cały folder może zostać przeniesiony do archiwum pomocniczego. W takim przypadku folder zachowa oryginalną nazwę.  Na liście folderów w programie Outlook nie będzie widać, że folder został przeniesiony do archiwum pomocniczego.

## <a name="outlook-requirements-for-accessing-items-in-an-auto-expanded-archive"></a>Wymagania programu Outlook dotyczące uzyskiwania dostępu do elementów w automatycznie rozwiniętym archiwum

Aby uzyskać dostęp do komunikatów przechowywanych w automatycznie rozwiniętym archiwum, użytkownicy muszą użyć jednego z następujących klientów programu Outlook:

- Outlook w ramach aplikacji Microsoft 365 dla przedsiębiorstw (wcześniej o nazwie Office 365 ProPlus)

- Program Outlook w ramach usługi Microsoft 365 Apps dla firm (wcześniej o nazwie Office 365 Business)

- Outlook 2016 lub Outlook 2019 dla systemu Windows

- Outlook on the web

- Outlook 2016 lub Outlook 2019 dla komputerów Mac

Poniżej przedstawiono kilka kwestii, które należy wziąć pod uwagę podczas korzystania z programu Outlook lub programu Outlook w Internecie w celu uzyskania dostępu do komunikatów przechowywanych w automatycznie rozwiniętym archiwum.

- Dostęp do dowolnego folderu w archiwum skrzynki pocztowej, w tym te, które zostały przeniesione do obszaru magazynu automatycznie rozwinięte.

- Jeśli skrzynka pocztowa archiwum ma co najmniej jeden automatycznie rozwinięty obszar magazynowania, nie można usunąć folderu ze skrzynki pocztowej archiwum ani z archiwum pomocniczego. Innymi słowy, po aprowizacji obszaru magazynu automatycznie rozwinięte nie można usunąć żadnych folderów w archiwum.

- Elementy można usuwać w obszarze magazynu automatycznie rozwiniętym. Nie można jednak użyć funkcji Odzyskiwanie usuniętych elementów w celu odzyskania elementu po włączeniu automatycznego rozszerzania archiwizacji dla skrzynki pocztowej.

- Wyszukiwanie automatycznie rozwiniętej archiwizacji jest dostępne w programie Outlook dla sieci Web (OWA). Podobnie jak w przypadku archiwum online, można wyszukiwać elementy, które zostały przeniesione do dodatkowego obszaru magazynowania. Po wybraniu archiwum jako zakresu wyszukiwania w usłudze OWA zostaną przeszukane wszystkie archiwa (w tym automatycznie rozwinięte archiwa) i odpowiadające im podfoldery. Należy pamiętać, że wyszukiwanie nie jest obsługiwane w przypadku funkcji automatycznie rozwiniętego archiwum w sytuacji archiwum tylko w chmurze (podstawowa skrzynka pocztowa nadal jest lokalna).

- Automatyczne rozszerzone wyszukiwanie archiwum jest dostępne w programie Outlook dla systemu Windows w kanale Monthly Enterprise Channel. Dzięki tej aktualizacji dostępny jest zakres Bieżąca skrzynka pocztowa, dzięki czemu można przeszukiwać automatycznie rozwinięte archiwum. Należy pamiętać, że wyszukiwanie nie jest obsługiwane w przypadku funkcji automatycznie rozwiniętego archiwum w sytuacji archiwum tylko w chmurze (podstawowa skrzynka pocztowa nadal jest lokalna). Aby uzyskać więcej informacji na temat tej i innych funkcji pomocy technicznej usługi Microsoft Search, zobacz [How Outlook for Windows connected to Exchange Online utilizes Microsoft Search (Jak program Outlook dla systemu Windows połączony z usługą Exchange Online korzysta z usługi Microsoft Search](https://techcommunity.microsoft.com/t5/outlook-global-customer-service/how-outlook-for-windows-connected-to-exchange-online-utilizes/ba-p/1715045)). 

- Liczba elementów w programie Outlook i liczbach odczytu/nieprzeczytanych (w programach Outlook i Outlook w Internecie) w automatycznie rozwiniętym archiwum może być nieprawidłowa.

## <a name="auto-expanding-archiving-and-other-compliance-features"></a>Automatyczne rozszerzanie archiwizacji i innych funkcji zgodności

W tej sekcji opisano funkcje między automatycznym rozszerzaniem archiwizacji a innymi funkcjami zapewniania zgodności i zarządzania danymi.

- **Zbierania elektronicznych materiałów dowodowych:** Podczas korzystania z narzędzia zbierania elektronicznych materiałów dowodowych, takiego jak wyszukiwanie zawartości lub In-Place zbierania elektronicznych materiałów dowodowych, przeszukiwane są również dodatkowe obszary magazynowania w automatycznie rozwiniętym archiwum.

- **Przechowywania:** Po wstrzymaniu skrzynki pocztowej przy użyciu narzędzi, takich jak blokada postępowania sądowego w usłudze Exchange Online lub zasady przechowywania i przechowywania spraw zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview, zawartość znajdująca się w automatycznie rozwiniętym archiwum jest również zawieszana.

- **Zarządzanie rekordami obsługi komunikatów (MRM):** Jeśli używasz zasad usuwania mrm w usłudze Exchange Online, aby trwale usunąć wygasłe elementy skrzynki pocztowej, wygasłe elementy znajdujące się w automatycznie rozwiniętym archiwum również zostaną usunięte.

- **Usługa importu:** Usługa Import usługi Office 365 umożliwia importowanie plików PST do automatycznie rozwiniętej archiwum użytkownika. Do archiwum skrzynki pocztowej użytkownika można zaimportować do 100 GB danych z plików PST.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji technicznych na temat automatycznego rozszerzania archiwizacji, zobacz [Microsoft 365: Automatyczne rozszerzanie archiwów — często zadawane pytania](https://techcommunity.microsoft.com/t5/exchange-team-blog/office-365-auto-expanding-archives-faq/ba-p/607784).

Jeśli wszystko jest gotowe do włączenia automatycznego rozszerzania archiwizacji, zobacz [Włączanie automatycznego rozszerzania archiwizacji](enable-autoexpanding-archiving.md).
