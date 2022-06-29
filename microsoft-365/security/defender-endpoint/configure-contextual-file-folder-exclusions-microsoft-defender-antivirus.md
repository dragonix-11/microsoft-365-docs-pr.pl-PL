---
title: Kontekstowe wykluczenia plików i folderów
description: Opisuje możliwość kontekstowych wykluczeń plików i folderów dla Program antywirusowy Windows Defender. Ta funkcja umożliwia bardziej szczegółowe określenie kontekstu, w którym Program antywirusowy Windows Defender nie należy skanować pliku lub folderu, stosując ograniczenia
keywords: Program antywirusowy Microsoft Defender, proces, wykluczenie, pliki, skany
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: jweston-1
ms.author: v-jweston
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a2dfcd6372398f92ba401a109302ef541de88565
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66494090"
---
# <a name="contextual-file-and-folder-exclusions"></a>Kontekstowe wykluczenia plików i folderów

W tym artykule/sekcji opisano możliwość kontekstowych wykluczeń plików i folderów dla Program antywirusowy Windows Defender. Ta funkcja umożliwia bardziej szczegółowe określenie kontekstu, w którym Program antywirusowy Windows Defender nie należy skanować pliku lub folderu, stosując ograniczenia.

## <a name="overview"></a>Omówienie

Wykluczenia mają na celu przede wszystkim ograniczenie wpływu na wydajność. Są one na karę obniżonej wartości ochrony. Te ograniczenia pozwalają ograniczyć tę redukcję ochrony, określając okoliczności, w których powinno być stosowane wykluczenie. Wykluczenia kontekstowe nie są odpowiednie do niezawodnego rozwiązywania problemów z wynikami fałszywie dodatnimi. Jeśli napotkasz wynik fałszywie dodatni, możesz przesłać pliki do analizy za pośrednictwem [portalu Microsoft 365 Defender](https://security.microsoft.com/) (wymagana subskrypcja) lub za pośrednictwem [witryny internetowej Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission). W przypadku metody tymczasowego pomijania rozważ utworzenie niestandardowego wskaźnika _zezwalania_ .

Istnieją cztery ograniczenia, które można zastosować w celu ograniczenia stosowania wykluczenia:

- **Ograniczenie typu ścieżki pliku/folderu**. Wykluczenia można ograniczyć tylko wtedy, gdy obiektem docelowym jest plik lub folder, określając intencję jako konkretną. Jeśli obiekt docelowy jest plikiem, ale wykluczenie jest określone jako folder, nie będzie ono stosowane. Z drugiej strony, jeśli obiektem docelowym jest folder, ale wykluczenie jest określone jako plik, zostanie zastosowane wykluczenie.
- **Ograniczenie typu skanowania**. Umożliwia zdefiniowanie wymaganego typu skanowania w celu zastosowania wykluczenia. Na przykład chcesz wykluczyć tylko określony folder z pełnych skanów, ale nie ze skanowania "zasób" (skanowanie docelowe).
- **Ograniczenie typu wyzwalacza skanowania**. Możesz użyć tego ograniczenia, aby określić, że wykluczenie powinno mieć zastosowanie tylko wtedy, gdy skanowanie zostało zainicjowane przez określone zdarzenie:
  - na żądanie
  - przy dostępie
  - lub pochodzące z monitorowania behawioralnego
- **Ograniczenie procesu**. Umożliwia zdefiniowanie, że wykluczenie powinno mieć zastosowanie tylko wtedy, gdy plik lub folder jest uzyskiwany przez określony proces.

## <a name="configuring-restrictions"></a>Konfigurowanie ograniczeń

Ograniczenia są zwykle stosowane przez dodanie typu ograniczenia do ścieżki wykluczenia pliku lub folderu.  

| Ograniczenie | Typename | Wartość |
|:---|:---|:---|
| Plik/folder  | Typ ścieżki  | Plik <br> Folder |
| Typ skanowania | ScanType | Szybkie <br> Pełne |
| Wyzwalacz skanowania | ScanTrigger | Ondemand <br> OnAccess <br> BM |
| Proces | Proces | "<image_path>" |

### <a name="requirements"></a>Wymagania

Ta funkcja wymaga Program antywirusowy Windows Defender:

- Platforma: **4.18.2205.7 lub nowsza**
- Silnik: **1.1.19300.2** lub nowszy

### <a name="syntax"></a>Składni

Punktem wyjścia mogą być już wykluczenia, które chcesz określić bardziej szczegółowo. Aby utworzyć ciąg wykluczenia, najpierw zdefiniuj ścieżkę do pliku lub folderu do wykluczenia, a następnie dodaj nazwę typu i skojarzoną wartość, jak pokazano w poniższym przykładzie.

`<PATH>\:{TypeName:value,TypeName:value}`

Należy pamiętać, że _wszystkie_ **typy** i **wartości uwzględniają** wielkość liter.

### <a name="examples"></a>Przykłady

Następujący ciąg wyklucza "c:\documents\design.doc" tylko wtedy, gdy jest to plik i tylko w skanach przy dostępie:

`c:\documents\design.doc\:{PathType:file,ScanTrigger:OnAccess}`

Następujący ciąg wyklucza "c:\documents\design.doc" tylko wtedy, gdy jest skanowany (w trybie dostępu) ze względu na to, że jest uzyskiwany przez proces o nazwie obrazu "winword.exe":

`c:\documents\design.doc\:{Process:”winword.exe”}`

Ścieżka obrazu procesu może zawierać symbole wieloznaczne, jak w poniższym przykładzie:

`c:\documents\design.doc\:{Process:”C:\Program Files*\Microsoft Office\root\Office??\winword.exe”}`

### <a name="filefolder-restriction"></a>Ograniczenie pliku/folderu

Wykluczenia można ograniczyć tylko wtedy, gdy obiektem docelowym jest plik lub folder, określając konkretną intencję. Jeśli obiekt docelowy jest plikiem, ale wykluczenie jest określone jako folder, wykluczenie nie będzie miało zastosowania. Z drugiej strony, jeśli obiektem docelowym jest folder, ale wykluczenie jest określone jako plik, zostanie zastosowane wykluczenie.

#### <a name="filefolder-exclusions-default-behavior"></a>Domyślne zachowanie wykluczeń plików/folderów

Jeśli nie określisz żadnych innych opcji, plik/folder zostanie wykluczony ze wszystkich typów skanowania _, a_ wykluczenie ma zastosowanie niezależnie od tego, czy elementem docelowym jest plik, czy folder. Aby uzyskać więcej informacji na temat dostosowywania wykluczeń tylko do określonego typu skanowania, zobacz [Ograniczenie typu skanowania](#scan-type-restriction).

#### <a name="folders"></a>Foldery

Aby upewnić się, że wykluczenie ma zastosowanie tylko wtedy, gdy obiektem docelowym jest folder, a nie plik, możesz użyć ograniczenia **PathType:folder** . Przykład:

`C:\documents\:{PathType:folder}`

#### <a name="files"></a>Pliki

Aby upewnić się, że wykluczenie ma zastosowanie tylko wtedy, gdy obiektem docelowym jest plik, a nie folder, możesz użyć ograniczenia PathType: file.

Przykład:

`C:\documents\database.mdb\:{PathType:file}`

### <a name="scan-type-restriction"></a>Ograniczenie typu skanowania

Domyślnie wykluczenia mają zastosowanie do wszystkich typów skanowania:  

- **zasób**: pojedynczy plik lub folder jest skanowany w sposób docelowy (na przykład kliknięcie prawym przyciskiem myszy, skanowanie)
- **Szybki**: typowe lokalizacje uruchamiania używane przez złośliwe oprogramowanie, pamięć i niektóre klucze rejestru
- **pełny**: zawiera szybkie lokalizacje skanowania i kompletny system plików (wszystkie pliki i foldery)

Aby rozwiązać problemy z wydajnością, można wykluczyć folder lub zestaw plików ze skanowania według określonego typu skanowania. Można również zdefiniować wymagany typ skanowania, aby zastosować wykluczenie.  

Aby wykluczyć folder ze skanowania tylko podczas pełnego skanowania, określ typ ograniczenia wraz z wykluczeniem pliku lub folderu, jak w poniższym przykładzie:

`C:\documents\:{ScanType:full}`

Aby wykluczyć folder ze skanowania tylko podczas szybkiego skanowania, określ typ ograniczenia wraz z wykluczeniem pliku lub folderu:

`C:\program.exe\:{ScanType:quick}`

Jeśli chcesz się upewnić, że to wykluczenie dotyczy tylko określonego pliku, a nie folderu (c:\foo.exe może być folderem), zastosuj również ograniczenie PathType:

`C:\program.exe\:{ScanType:quick,PathType:file}`

### <a name="scan-trigger-restriction"></a>Ograniczenie wyzwalacza skanowania

Domyślnie podstawowe wykluczenia mają zastosowanie do wszystkich wyzwalaczy skanowania. Ograniczenie ScanTrigger umożliwia określenie, że wykluczenie powinno mieć zastosowanie tylko wtedy, gdy skanowanie zostało zainicjowane przez określone zdarzenie; na żądanie (w tym szybkie, pełne i ukierunkowane skanowanie), na dostęp lub pochodzące z monitorowania zachowania (w tym skanowania pamięci).

- **OnDemand**: skanowanie zostało wyzwolone przez polecenie lub akcję administratora. Pamiętaj, że zaplanowane szybkie i pełne skanowanie również należy do tej kategorii.
- **OnAccess**: plik lub folder jest otwierany/zapisywany/odczytywany/modyfikowany (zwykle uważany za ochronę w czasie rzeczywistym)
- **BM**: wyzwalacz behawioralny powoduje, że monitorowanie zachowania skanuje określony plik

Aby wykluczyć plik lub folder i jego zawartość ze skanowania tylko wtedy, gdy plik jest skanowany po uzyskaniu dostępu, zdefiniuj ograniczenie wyzwalacza skanowania, takie jak następujący przykład:

`c:\documents\:{ScanTrigger:OnAccess}`

### <a name="process-restriction"></a>Ograniczenie procesu

To ograniczenie pozwala zdefiniować, że wykluczenie powinno mieć zastosowanie tylko wtedy, gdy plik lub folder jest uzyskiwany przez określony proces. Typowy scenariusz polega na tym, że chcesz uniknąć wykluczania procesu, ponieważ unikanie tego procesu spowodowałoby, że program antywirusowy Defender ignoruje inne operacje tego procesu.

> [!NOTE]  
>
> Użycie dużej ilości ograniczeń wykluczania procesów na maszynie może niekorzystnie wpłynąć na wydajność.  
> Ponadto, ponieważ wykluczenie jest ograniczone do określonego procesu lub procesów, inne aktywne procesy (takie jak indeksowanie, tworzenie kopii zapasowych, aktualizacje) mogą nadal wyzwalać skanowanie plików.

Aby wykluczyć plik lub folder tylko w przypadku uzyskania dostępu przez określony proces, utwórz normalne wykluczenie pliku lub folderu i dodaj proces, aby ograniczyć wykluczenie do:  

`c:\documents\design.doc\:{Process:”winword.exe”, Process:”msaccess.exe”}`

### <a name="how-to-configure"></a>Jak skonfigurować

Po utworzeniu żądanych wykluczeń kontekstowych możesz użyć istniejącego narzędzia do zarządzania, aby skonfigurować wykluczenia plików i folderów przy użyciu utworzonego ciągu.

Zobacz: [Konfigurowanie i weryfikowanie wykluczeń dla skanowania programu antywirusowego Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
