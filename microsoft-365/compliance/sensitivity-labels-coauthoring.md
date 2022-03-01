---
title: Włączanie współtworowania dokumentów zaszyfrowanych przy użyciu etykiet wrażliwości w Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.topic: article
description: Włącz ustawienie umożliwiające współtworzenie i autozazawdanie w aplikacjach klasycznych dla dokumentów oznaczonych i zaszyfrowanych w aplikacjach pakietu SharePoint i OneDrive.
ms.openlocfilehash: 8be6fc228a623f3a1f76efdf56354ba30beb9650
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019244"
---
# <a name="enable-co-authoring-for-files-encrypted-with-sensitivity-labels"></a>Włączanie współtworowania plików zaszyfrowanych przy użyciu etykiet wrażliwości

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Włącz to ustawienie, aby [](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) obsługiwać współtworowanie w aplikacjach klasycznych pakietu Office, dzięki czemu gdy dokumenty są oznaczane i szyfrowane etykietami [wrażliwości, wielu](sensitivity-labels.md) użytkowników może edytować te dokumenty jednocześnie.

Bez tego ustawienia włączonego dla dzierżawy użytkownicy muszą wyewidencjonowyć zaszyfrowany dokument przechowywany SharePoint aplikacji OneDrive, gdy korzystają Office klasycznych. W efekcie nie mogą współpracować w czasie rzeczywistym. Ponadto muszą oni używać tych Office w sieci Web, gdy etykiety wrażliwości są włączone [dla Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Ponadto włączenie tej funkcji powoduje, że dla tych [](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) plików oznaczonych i zaszyfrowanych jest obsługiwana funkcja Autozazyfrowania.

Aby przeczytać ogłoszenie o wydaniu, zobacz wpis [w blogu Współtworowanie Microsoft Information Protection zaszyfrowanych dokumentów jest teraz ogólnie dostępne](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/2693718).

## <a name="metadata-changes-for-sensitivity-labels"></a>Metadane zmienia się w etykietach wrażliwości

> [!IMPORTANT]
> Po włączeniu ustawienia współtworzenia etykiety informacji w przypadku plików nieszyfrowanych nie są już zapisywane we właściwościach niestandardowych.
> 
> Nie włączaj tego ustawienia, jeśli używasz jakichkolwiek aplikacji, usług, skryptów lub narzędzi, które odczytuje lub zapisuje metadane w starej lokalizacji.

Przed włączeniem ustawienia obsługi współtworzeń dla aplikacji klasycznych Office należy zrozumieć, że ta akcja wprowadza zmiany w metadanych etykiet, które są zapisywane i odczytywane z Office plików.

Metadane etykiet zawierają informacje identyfikujące dzierżawę i zastosowane etykiety wrażliwości. Zmiana, która powoduje to ustawienie, to format i lokalizacja metadanych dla plików programu Word, Excel i PowerPoint plików. Nie musisz nic robić w przypadku zaszyfrowanych plików ani wiadomości e-mail. Zmiana metadanych w przypadku zaszyfrowanych plików jest zgodna z poprzednimi wersjami i nie ma żadnych zmian w wiadomościach e-mail. Musisz jednak pamiętać o zmianach metadanych w przypadku zaszyfrowanych plików, które można uaktualnić automatycznie, ale nie są zgodne z poprzednimi wersjami.

Ta zmiana dotyczy zarówno plików, które są nowo oznaczonymi etykietami, jak i plików, które zostały już oznaczone etykietą. Jeśli korzystasz z aplikacji i usług, które obsługują ustawienie współtworowania:
- W przypadku plików o nowo oznaczonych etykietach w metadanych etykiet jest używany tylko nowy format i lokalizacja.
- W przypadku plików, które są już oznaczone etykietą, przy następnym otwarciu i zapisaniu pliku, jeśli plik ma metadane w starym formacie i lokalizacji, zostanie skopiowany do nowego formatu i lokalizacji.

Więcej informacji o tej zmianie metadanych można znaleźć w następujących zasobach:

- Wpis w blogu: [Nadchodzące zmiany dotyczące Microsoft Information Protection metadanych Storage](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)

- Open Specifications: [2.6.3 LabelInfo a Custom Document Properties](/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)

Z powodu tych zmian nie włączaj tego ustawienia, jeśli masz w organizacji jakiekolwiek aplikacje, usługi, skrypty lub narzędzia, które odczytuje lub zapisuje metadane z etykietami w starej lokalizacji. W przypadku takich  konsekwencji może być kilka przykładów:

- Dokument oznaczony etykietą jest wyświetlany użytkownikom jako bez etykiety.

- W dokumencie jest wyświetlana użytkownikom aktualny etykieta.

- W przypadku dokumentu oznaczonego etykietą i zaszyfrowanego nie można współtworzeć dokumentów, jeśli inny użytkownik otworzy go w aplikacji klasycznej Office, która nie obsługuje nowych metadanych z etykietami. Należy pamiętać, że ten scenariusz może również wystąpić w przypadku użytkowników spoza organizacji, jeśli plik został otwarty przez użytkowników zewnętrznych i zaproszonych gości.

- Reguła przepływu Exchange Online, która określa etykiety jako właściwości niestandardowe w Office nie może zaszyfrować wiadomości e-mail i załączników lub nieprawidłowo je szyfruje.[](/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization)

W poniższej sekcji znajduje się lista aplikacji i usług, które obsługują to ustawienie, oraz zmiany metadanych etykiet.

## <a name="prerequisites"></a>Wymagania wstępne

> [!IMPORTANT]
> Ta funkcja wymaga, aby wszyscy użytkownicy Aplikacje Microsoft 365 dla przedsiębiorstw. Obsługa tej funkcji współtworowania nie jest jeszcze dostępna w kanale Semi-Annual Enterprise dla Office aktualizacji. Jeśli korzystasz z tego kanału aktualizacji dla aplikacji Office, zmień go na Bieżący kanał lub Miesięczny kanał Enterprise miesięczny.
> 
> Aby uzyskać więcej informacji, zobacz [Jak skonfigurować kanały aktualizacji i zarządzać nimi](/deployoffice/overview-update-channels#how-to-configure-and-manage-update-channels).

Przed włączeniem tej funkcji upewnij się, że rozumiesz poniższe wymagania wstępne.

- Aby włączyć tę funkcję, musisz być administratorem globalnym.

- Etykiety wrażliwości muszą być [włączone dla Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) dla dzierżawy. Jeśli ta funkcja nie jest jeszcze włączona, zostanie automatycznie włączona po wybraniu ustawienia, aby włączyć współtworowanie plików z etykietami wrażliwości.

- Aplikacje Microsoft 365 dla przedsiębiorstw:
    - **Windows**: Minimalna wersja 2107 z bieżącego kanału lub z miesięcznego Enterprise kanału
    - **macOS**: Minimalna wersja 16.51
    - **iOS**: Jeszcze nie obsługiwane
    - **Android**: Jeszcze nie obsługiwane

- Wszystkie aplikacje, usługi i narzędzia operacyjne w dzierżawie muszą obsługiwać nowe [metadane z etykietami](#metadata-changes-for-sensitivity-labels). Jeśli korzystasz z dowolnej z następujących wersji, sprawdź minimalne wymagane wersje:
    
    - **Klient i skaner z ujednoliconą etykietą usługi Azure Information Protection:**
        - Minimalna wersja [2.12.62.0](/information-protection/rms-client/unifiedlabelingclient-version-release-history#version-212620) , która można zainstalować z Centrum [pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018)
    
    - **synchronizacja usługi OneDrive dla systemu Windows lub macOS:**
        - Minimalna wersja: 19.002.0121.0008
    
    - **Zapobieganie utracie danych w punkcie końcowym (ochrona przed utratą danych w punkcie końcowym):**
        - Windows 10 1809 z kb 4601383
        - Windows 10 1903 i 1909 z aktualizacjami KB 4601380
        - Windows 10 2004 z artykułem KB 4601382
        - Windows nowsze niż Windows 10 2004 są obsługiwane bez aktualizacji KB
    
    - **Aplikacje i usługi, które korzystają z zestawu MICROSOFT INFORMATION PROTECTION SDK:** 
        - Minimalna wersja: 1.7 

Microsoft 365 automatycznie obsługują nowe metadane etykiet po włączeniu tej funkcji. Przykład:

- [Zasady automatycznego oznaczania etykiet](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)
- [Zasady DLP, w których etykiety wrażliwości są jako warunki](dlp-sensitivity-label-as-condition.md)
- [Usługa Microsoft Defender dla aplikacji w chmurze skonfigurowana do stosowania etykiet wrażliwości](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)

## <a name="limitations"></a>Ograniczenia

Zanim włączysz ustawienie dzierżawy na temat współtworowania plików zaszyfrowanych przy użyciu etykiet wrażliwości, upewnij się, że rozumiesz następujące ograniczenia tej funkcji.

- Ze względu na zmiany metadanych [z](#metadata-changes-for-sensitivity-labels) etykietami wszystkie aplikacje, usługi i narzędzia operacyjne w Twojej dzierżawie muszą obsługiwać nowe metadane etykiet w celu zapewnienia spójnego i niezawodnego działania etykiet.
    
    Dotyczy Excel: Metadane dla etykiety wrażliwości, która nie stosuje szyfrowania, można usunąć z pliku, jeśli ktoś edytuje i zapisuje ten plik przy użyciu wersji programu Excel, która nie obsługuje zmian metadanych w przypadku etykiet wrażliwości.

- Office dla systemów iOS i Android nie są obecnie obsługiwane.

- Funkcja współtworzenia i autozazyskiwu nie są obsługiwane i nie działają w przypadku Office oznaczonych i zaszyfrowanych dokumentów z dowolną z następujących konfiguracji [szyfrowania:](encryption-sensitivity-labels.md#configure-encryption-settings)
    - **Umożliwianie użytkownikom przypisywania uprawnień** po zastosowaniu etykiety i pola wyboru W programach **Word, PowerPoint i Excel** zaznaczono pole wyboru Monituj użytkowników o określenie uprawnień. Ta konfiguracja jest niekiedy określana mianem "uprawnień zdefiniowanych przez użytkownika".
    - **Dla dostępu użytkownika do zawartości wygasa** jest ustawiona wartość inna niż **Nigdy**.
    - **Wybrana jest opcja Szyfrowanie podwójnym** kluczem.
    
    W przypadku etykiet z dowolną z tych konfiguracji szyfrowania etykiety są wyświetlane Office aplikacjach. Jednak gdy użytkownicy zaznaczą te etykiety i nikt inny nie edytuje dokumentu, jest dla nich ostrzegany, że funkcja współtworzenia i autozasad nie będą dostępne. Jeśli ktoś inny edytuje dokument, użytkownik widzi komunikat, że etykiet nie można zastosować.

- Jeśli korzystasz z ujednoliconego klienta etykiet usługi Azure Information Protection: Zapoznaj się z dokumentacją tego klienta z etykietami, aby uzyskać więcej wymagań [lub ograniczeń](/azure/information-protection/known-issues#known-issues-for-co-authoring). 
    > [!NOTE]
    > Ograniczenia tego klienta ujednoliconego etykiet obejmują zmianę okna dialogowego [](/azure/information-protection/known-issues#user-interface-changes-when-applying-labels) dla użytkowników wybierających etykiety monitujące o wybranie uprawnień.

## <a name="how-to-enable-co-authoring-for-files-with-sensitivity-labels"></a>Jak włączyć współtworowanie plików z etykietami wrażliwości

> [!CAUTION]
> Włączenie tego ustawienia jest akcją jednokierunkową. Tę funkcję można włączyć dopiero po przeczytaniu i zrozumieniu zmian metadanych, wymagań wstępnych, ograniczeń i wszelkich znanych problemów udokumentowanych na tej stronie.

Jeśli to ustawienie zostało już włączone w okresie podglądu, nie są wymagane żadne dalsze działania i możesz pominąć tę procedurę.

1. Zaloguj [się do Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) jako administrator globalny dzierżawy.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Co-authoring dla plików z plikami wrażliwości**.

2. Na stronie **Współtwoowanie** plików z etykietami wrażliwości przeczytaj opis podsumowania, wymagania wstępne, czego można oczekiwać i ostrzeżenie, że nie można wyłączyć tego ustawienia po jego włączeniu.
    
    Następnie wybierz **pozycję Włącz współtworowanie dla plików z etykietami wrażliwości** **i Zastosuj:**
    
    ![Opcja umożliwia włączenie współtworowania plików z etykietami wrażliwości.](../media/co-authoring-tenant-option-for-sensitivity-labels.png)

3. Poczekaj 24 godziny, aż to ustawienie zreplikuje się w środowisku, zanim użyjemy tej nowej funkcji na użytek współtworowania.

## <a name="contact-support-if-you-need-to-disable-this-feature"></a>Skontaktuj się z pomocą techniczną, jeśli chcesz wyłączyć tę funkcję

> [!IMPORTANT]
> Jeśli musisz wyłączyć tę funkcję, musisz pamiętać, że informacje o etykietach mogą zostać utracone.

Po włączeniu współtworowania plików z etykietami wrażliwości dla dzierżawy nie możesz wyłączyć tego ustawienia samodzielnie. Dlatego tak ważne jest sprawdzenie i zrozumienie wymagań wstępnych, konsekwencji i ograniczeń przed włączeniem tego ustawienia.

![Opcja, która pokazuje, że dla etykiet wrażliwości włączona jest współtwoer.](../media/co-authoring-tenant-option-set-for-sensitivity-labels.png)

Jak widać na zrzucie ekranu, gdy to ustawienie jest włączone, możesz skontaktować się z pomocą techniczną [firmy Microsoft](../admin/get-help-support.md) i poprosić o jego wyłączenie. To żądanie może potrwać kilka dni i konieczne będzie udowodnienie, że jesteś administratorem globalnym Twojej dzierżawy. Spodziewaj się normalnie naliczanych opłat za pomoc techniczną. 

Jeśli inżynier pomocy technicznej wyłączy to ustawienie dla Twojej dzierżawy:

- W przypadku aplikacji i usług, które obsługują nowe metadane etykiet, teraz przy odczytywaniu lub zapisywaniu etykiet przywracane są oryginalne formaty i lokalizacje metadanych.

- Nowy format metadanych i lokalizacja dla Office, które były używane podczas włączonego ustawienia, nie zostaną skopiowane do pierwotnego formatu i lokalizacji. W wyniku tego informacje z etykietami nieszyfrowanych plików programu Word, Excel i PowerPoint zostaną utracone.

- W przypadku dokumentów oznaczonych i zaszyfrowanych funkcja współtworzeń i autozazyskiwu nie działają już w dzierżawie.

- Etykiety wrażliwości pozostaną włączone Office plikach w OneDrive i SharePoint.
