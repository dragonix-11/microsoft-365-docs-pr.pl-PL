# [Ochrona punktu końcowego w usłudze Microsoft Defender](index.yml)

## [Omówienie]()
### [Co to jest Ochrona punktu końcowego w usłudze Microsoft Defender?](microsoft-defender-endpoint.md)
### [Porównanie planu 1 ochrony punktu końcowego w usłudze Defender z planem 2](defender-endpoint-plan-1-2.md)
### [Minimalne wymagania](minimum-requirements.md)
### [Co nowego w usłudze ochrony punktu końcowego w usłudze Microsoft Defender](whats-new-in-microsoft-defender-endpoint.md)
### [Funkcje wersji zapoznawczej](preview.md)
### [Przechowywanie danych i prywatność](data-storage-privacy.md)
### [Omówienie Centrum zabezpieczeń usługi Microsoft Defender](use.md)
### [Ochrona punktu końcowego w usłudze Microsoft Defender — Plan 1]()
#### [Omówienie](defender-endpoint-plan-1.md)
#### [Instalacja i konfiguracja](mde-p1-setup-configuration.md)
#### [Wprowadzenie](mde-plan1-getting-started.md)
#### [Konserwacja i operacje](mde-p1-maintenance-operations.md)
### [Usługa ochrony punktu końcowego w usłudze Microsoft Defender dla klientów z instytucji rządowych Stanów Zjednoczonych](gov.md)
### [Usługa ochrony punktu końcowego w usłudze Microsoft Defender na platformach z innym system operacyjnym niż Windows](non-windows.md)


## [Ocena możliwości](evaluation-lab.md)

## [Zaplanuj wdrożenie](deployment-strategy.md)

## [Przewodnik wdrażania]()
### [Fazy wdrażania](deployment-phases.md)
### [Faza 1. Przygotowanie](prepare-deployment.md)
### [Faza 2. Konfiguracja](production-deployment.md)
### [Faza 3. Dołączenie]()
#### [Omówienie dołączania](onboarding.md)
#### [Pierścienie wdrożenia](deployment-rings.md)
#### [Dołączanie przy użyciu menedżera konfiguracji punktu końcowego Microsoft](onboarding-endpoint-configuration-manager.md)
#### [Dołączanie przy użyciu menedżera Microsoft Endpoint Manager](onboarding-endpoint-manager.md)

## [Przewodniki po migracji](migration-guides.md)
### [Przenieś do usługi ochrony punktu końcowego w usłudze Microsoft Defender](switch-to-mde-overview.md)
#### [Faza 1. Przygotowanie](switch-to-mde-phase-1.md)
#### [Faza 2. Konfiguracja](switch-to-mde-phase-2.md)
#### [Faza 3. Dołączenie](switch-to-mde-phase-3.md)
#### [Rozwiązywanie problemów](switch-to-mde-troubleshooting.md)
### [Zarządzaj usługą ochrony punktu końcowego w usłudze Microsoft Defender po migracji](manage-mde-post-migration.md)
#### [Użyj usługi Intune (zalecane)](manage-mde-post-migration-intune.md)
#### [Użyj menedżera konfiguracji](manage-mde-post-migration-configuration-manager.md)
#### [Użyj zasad grupy](manage-mde-post-migration-group-policy-objects.md)
#### [Użyj programu PowerShell, usługi WMI lub MPCmdRun.exe](manage-mde-post-migration-other-tools.md)
#### [Scenariusze migracji serwera](server-migration.md)

## [Konfiguruj i dołącz urządzenia]()
### [Dołącz urządzenia i konfiguruj możliwości usługi ochrony punktu końcowego w usłudze Microsoft Defender](onboard-configure.md)


### [Ochrona punktu końcowego w usłudze Microsoft Defender dla systemów Windows i Windows Server]()
#### [Narzędzia i metody dołączania punktów końcowych dla systemu Windows](configure-endpoints.md)
#### [Dołącz urządzenia z systemem Windows i Windows Server]()

##### [Dołącz poprzednią wersję systemu Windows](onboard-downlevel.md)


##### [Dołącz urządzenia z systemem Windows i Windows Server]()
###### [Dołącz system Windows Server 2012 R2, 2016, półroczny kanał, 2019 i 2022](configure-server-endpoints.md)
###### [Dołącz urządzenia z systemem Windows przy użyciu skryptu lokalnego](configure-endpoints-script.md)
###### [Dołącz urządzenia z systemem Windows przy użyciu zasad grupy](configure-endpoints-gp.md)
###### [Dołącz urządzenia z systemem Windows przy użyciu menedżera konfiguracji punktu końcowego Microsoft](configure-endpoints-sccm.md)
###### [Dołącz urządzenia z systemem Windows przy użyciu narzędzi do zarządzania urządzeniami przenośnymi](configure-endpoints-mdm.md)
###### [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](configure-endpoints-vdi.md)
###### [Dołącz urządzenia wielosesyjne z systemem Windows 10 w pulpicie wirtualnym Windows](onboard-windows-multi-session-device.md)




#### [Integracja z Microsoft Defender dla Chmury](azure-server-integration.md)

#### [Dołącz urządzenia bez dostępu do Internetu](onboard-offline-machines.md)
#### [Uruchom test wykrywania na nowo dołączonym urządzeniu](run-detection-test.md)
#### [Uruchom symulowane ataki na urządzeniach](attack-simulations.md)
#### [Konfiguruj ustawienia serwera proxy i połączenia internetowego](configure-proxy-internet.md)
#### [Utwórz regułę powiadomienia o dołączaniu lub odłączaniu](onboarding-notification.md)



### [Usługa ochrony punktu końcowego w usłudze Microsoft Defender w innych systemach operacyjnych]()
#### [Dołącz urządzenia z system operacyjnym innym niż Windows](configure-endpoints-non-windows.md)

#### [Usługa ochrony punktu końcowego w usłudze Microsoft Defender w systemie macOS]()
##### [Omówienie usługi ochrony punktu końcowego w usłudze Microsoft Defender w systemie macOS](microsoft-defender-endpoint-mac.md)
##### [Co nowego](mac-whatsnew.md)

##### [Wdrażanie]()
###### [Wdrożenie oparte na usłudze Microsoft Intune](mac-install-with-intune.md)
###### [Wdrożenie oparte na usłudze Jamf Pro]()
####### [Wdrażanie usługi ochrony punktu końcowego w usłudze Microsoft Defender w systemie macOS przy użyciu usługi Jamf Pro](mac-install-with-jamf.md)
####### [Zaloguj się do usługi Jamf Pro](mac-install-jamfpro-login.md)
####### [Konfiguruj grupy urządzeń](mac-jamfpro-device-groups.md)
####### [Konfiguruj zasady](mac-jamfpro-policies.md)
####### [Rejestrowanie urządzeń](mac-jamfpro-enroll-devices.md)

###### [Wdrożenie z innym systemem usługi Zarządzanie urządzeniami przenośnymi (MDM)](mac-install-with-other-mdm.md)
###### [Wdrażanie ręczne](mac-install-manually.md)
##### [Aktualizacja](mac-updates.md)

##### [Konfiguruj]()
###### [Konfiguruj i waliduj wykluczenia](mac-exclusions.md)
###### [Ustaw preferencje](mac-preferences.md)
###### [Wykrywaj i blokuj potencjalnie niechciane aplikacje](mac-pua.md)
###### [Sterowanie urządzeniem]()
####### [Omówienie sterowania urządzeniem](mac-device-control-overview.md)
####### [Przykłady usługi Jamf](mac-device-control-jamf.md)
####### [Przykłady usługi Intune](mac-device-control-intune.md)
###### [Planuj skany](mac-schedule-scan.md)

##### [Rozwiązywanie problemów]()
###### [Rozwiąż problemy z instalacją](mac-support-install.md)
###### [Rozwiąż problemy z wydajnością](mac-support-perf.md)
###### [Rozwiąż problemy z łącznością w chmurze](troubleshoot-cloud-connect-mdemac.md)
###### [Rozwiąż problemy z rozszerzeniem jądra](mac-support-kext.md)
###### [Rozwiąż problemy z licencją](mac-support-license.md)

##### [Prywatność](mac-privacy.md)
##### [Zasoby](mac-resources.md)


#### [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie]()
##### [Omówienie usługi ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](microsoft-defender-endpoint-linux.md)
##### [Co nowego](linux-whatsnew.md)
##### [Wdrażanie]()
###### [Wdrażanie ręczne](linux-install-manually.md)
###### [Wdrożenie oparte na usłudze Puppet](linux-install-with-puppet.md)
###### [Wdrożenie oparte na usłudze Ansible](linux-install-with-ansible.md)
###### [Wdrażaj usługę ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux za pomocą programu Chef](linux-deploy-defender-for-endpoint-with-chef.md)

##### [Aktualizacja](linux-updates.md)

##### [Konfiguruj]()
###### [Konfiguruj i weryfikuj wykluczenia](linux-exclusions.md)
###### [Konfiguracja statycznego serwera proxy](linux-static-proxy-configuration.md)
###### [Ustaw preferencje](linux-preferences.md)
###### [Wykryj i zablokuj potencjalnie niechciane aplikacje](linux-pua.md)
###### [Zaplanuj skany z usługą ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-schedule-scan-mde.md)
###### [Zaplanuj aktualizację usługi ochrony punktu końcowego w usłudze Microsoft Defender (Linux)](linux-update-MDE-Linux.md)


##### [Rozwiązywanie problemów]()
###### [Rozwiąż problemy z instalacją](linux-support-install.md)
###### [Badaj problemy z kondycją agenta](health-status.md)
###### [Rozwiąż problemy z łącznością w chmurze](linux-support-connectivity.md)
###### [Rozwiąż problemy z instalacją RHEL 6](linux-support-rhel.md)
###### [Rozwiąż problemy z wydajnością](linux-support-perf.md)
###### [Rozwiąż problemy z brakującymi zdarzeniami](linux-support-events.md)

##### [Prywatność](linux-privacy.md)
##### [Zasoby](linux-resources.md)

#### [Ochrona przed zagrożeniami mobilnymi]()
##### [Omówienie ochrony przez zagrożeniami mobilnymi](mtd.md)

##### [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android]()
###### [Omówienie usługi ochrony punktu końcowego w usłudze Microsoft Defender w systemie Android](microsoft-defender-endpoint-android.md)
###### [Co nowego](android-whatsnew.md)

###### [Wdrażanie]()
####### [Wdrażaj usługę ochrony punktu końcowego w usłudze Microsoft Defender w systemie Android za pomocą usługi Microsoft Intune](android-intune.md)

###### [Konfiguruj]()
####### [Konfiguruj usługę ochrony punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
####### [Konfiguruj sygnały ryzyka usługi ochrony punktu końcowego w usłudze Microsoft Defender przy użyciu zasad ochrony aplikacji](android-configure-mam.md)

###### [Prywatność]()
####### [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android — informacje o ochronie prywatności](android-privacy.md)

###### [Rozwiązywanie problemów]()
####### [Rozwiąż problemy](android-support-signin.md)

##### [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS]()
###### [Omówienie usługi ochrony punktu końcowego w usłudze Microsoft Defender w systemie iOS](microsoft-defender-endpoint-ios.md)
###### [Co nowego](ios-whatsnew.md)

###### [Wdrażanie]()
####### [Wdrażaj usługę ochrony punktu końcowego w usłudze Microsoft Defender w systemie iOS za pośrednictwem usługi Intune](ios-install.md)
####### [Wdrażaj usługę ochrony punktu końcowego w usłudze Microsoft Defender w systemie iOS dla niezarejestrowanych urządzeń](ios-install-unmanaged.md)

###### [Skonfiguruj funkcje systemu iOS](ios-configure-features.md)

###### [Często zadawane pytania i rozwiązywania problemów](ios-troubleshoot.md)

###### [Prywatność](ios-privacy.md)


### [Zarządzaj ustawieniami konfiguracji usługi ochrony punktu końcowego w usłudze Microsoft Defender na urządzeniach z programem Microsoft Endpoint Manager](security-config-management.md)

### [Rozwiąż problemy z dołączaniem]()
#### [Rozwiąż problemy podczas dołączania](troubleshoot-onboarding.md)
#### [Rozwiąż problemy z dostępem do subskrypcji i portalu](troubleshoot-onboarding-error-messages.md)
#### [Rozwiąż problemy z dołączaniem do zarządzania konfiguracją zabezpieczeń](troubleshoot-security-config-mgt.md)





### [Konfiguruj ustawienia portalu]()
#### [Konfiguruj ogólne ustawienia usługi ochrony punktu końcowego w usłudze Microsoft Defender](preferences-setup.md)
#### [Ogólne]()
##### [Sprawdź lokalizację przechowywania danych i zaktualizuj ustawienia przechowywania danych](data-retention-settings.md)
##### [Konfiguruj powiadomienia o alertach](configure-email-notifications.md)
##### [Konfiguruj powiadomienia e-mail o lukach w zabezpieczeniach](configure-vulnerability-email-notifications.md)
##### [Konfiguruj funkcje zaawansowane](advanced-features.md)

#### [Uprawnienia]()
##### [Użyj podstawowych uprawnień dostępu do portalu](basic-permissions.md)
##### [Zarządzaj dostępem do portalu przy użyciu kontroli dostępu opartej na rolach](rbac.md)
###### [Twórz role i zarządzaj nimi](user-roles.md)
###### [Twórz grupy urządzeń i zarządzaj nimi](machine-groups.md)
###### [Twórz tagi urządzeń i zarządzaj nimi](machine-tags.md)

#### [Reguły]()
##### [Zarządzaj regułami pomijania](manage-suppression-rules.md)
##### [Utwórz wskaźniki](manage-indicators.md)
###### [Utwórz wskaźniki dla plików](indicator-file.md)
###### [Utwórz wskaźniki adresów IP i adresów URL/domen](indicator-ip-domain.md)
###### [Utwórz wskaźniki dla certyfikatów](indicator-certificates.md)
###### [Zarządzaj wskaźnikami](indicator-manage.md)
##### [Zarządzaj przekazywaniem plików automatyzacji](manage-automation-file-uploads.md)
##### [Zarządzaj wykluczeniami folderów automatyzacji](manage-automation-folder-exclusions.md)

#### [Zarządzanie urządzeniami]()
##### [Dołączanie urządzeń](onboard-configure.md)
##### [Odłączanie urządzeń](offboard-machines.md)
##### [Upewnij się, że urządzenia są prawidłowo skonfigurowane](configure-machines.md)
##### [Monitoruj i zwiększ liczbę dołączania urządzeń](configure-machines-onboarding.md)

#### [Skonfiguruj ustawienia strefy czasowej Centrum zabezpieczeń usługi Microsoft Defender](time-settings.md)

## [Wykryj zagrożenia i chroń punkty końcowe]()
### [Zarządzanie zagrożeniami i lukami w zabezpieczeniach]()
#### [Omówienie](next-gen-threat-and-vuln-mgt.md)
#### [Wprowadzenie]()
##### [Uprawnienia i wymagania wstępne](tvm-prerequisites.md)
##### [Obsługiwane platformy i możliwości systemów operacyjnych](tvm-supported-os.md)
##### [Przypisz wartość urządzenia](tvm-assign-device-value.md)
#### [Ocenianie postawy dotyczącej zabezpieczeń]()
##### [Szczegółowe informacje pulpitu nawigacyjnego](tvm-dashboard-insights.md)
##### [Stopień zagrożenia](tvm-exposure-score.md)
##### [Wskaźnik bezpieczeństwa Microsoft dla urządzeń](tvm-microsoft-secure-score-devices.md)
#### [Zwiększ stan zabezpieczeń i zmniejsz ryzyko]()
##### [Uwzględnij rekomendacje dotyczące zabezpieczeń](tvm-security-recommendation.md)
##### [Koryguj luki w zabezpieczeniach](tvm-remediation.md)
##### [Wyjątki dla rekomendacji dotyczących zabezpieczeń](tvm-exception.md)
##### [Zaplanuj zakończenie wsparcia technicznego](tvm-end-of-support-software.md)
##### [Łagodź luki w zabezpieczeniach zero-day](tvm-zero-day-vulnerabilities.md)
#### [Zrozum luki w zabezpieczeniach na Twoich urządzeniach]()
##### [Spis oprogramowania](tvm-software-inventory.md)
##### [Luki w zabezpieczeniach w mojej organizacji](tvm-weaknesses.md)
##### [Oś czasu zdarzenia](threat-and-vuln-mgt-event-timeline.md)
##### [Raport urządzeń podatnych na zagrożenia](tvm-vulnerable-devices-report.md)
##### [Wykrywaj narażone urządzenia](tvm-hunt-exposed-devices.md)

### [Wykrywanie urządzeń]()
#### [Omówienie wykrywania urządzeń](device-discovery.md)
#### [Konfiguruj wykrywanie urządzeń](configure-device-discovery.md)
#### [Microsoft Defender dla integracji IoT](enable-microsoft-defender-for-iot-integration.md)
#### [Włącz integrację danych Corelight](corelight-integration.md)
#### [Wykrywanie urządzeń — często zadawane pytania](device-discovery-faq.md)

### [Spisz urządzeń]()
#### [Spisz urządzeń](machines-view-overview.md)
#### [Wyklucz urządzenia](exclude-devices.md)
#### [Flagi zdarzeń osi czasu urządzenia](device-timeline-event-flag.md)
#### [Zarządzaj grupą urządzeń i tagami](machine-tags.md)

### [Urządzenia sieciowe](network-devices.md)

### [Hostuj raportowanie zapory w usłudze ochrony punktu końcowego w usłudze Microsoft Defender](host-firewall-reporting.md)

### [Zmniejszanie obszaru podatnego na ataki]()
#### [Omówienie zmniejszania obszaru podatnego na ataki](overview-attack-surface-reduction.md)
#### [Reguły zmniejszania obszaru podatnego na ataki]()
##### [Dowiedz się więcej o regułach usługi ASR](attack-surface-reduction.md)
##### [Przewodnik wdrażania reguł zmniejszania powierzchni podatnej na ataki (ASR)]()
###### [Omówienie wdrażania reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment.md)
###### [Zaplanuj wdrażanie reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment-plan.md)
###### [Przetestuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-test.md)
###### [Włącz reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-implement.md)
###### [Operacjonalizuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-operationalize.md)
##### [Odwołuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-reference.md)
##### [Włączy alternatywne metody konfiguracji reguł usługi ASR](enable-attack-surface-reduction.md)
##### [Zmniejszanie obszaru podatnego na ataki — często zadawane pytania](attack-surface-reduction-faq.yml)
#### [Kontrolowany dostęp do folderu]()
##### [Chroń foldery](controlled-folders.md)
##### [Oceń kontrolowany dostęp do folderu](evaluate-controlled-folder-access.md)
##### [Włącz kontrolowany dostępu do folderu](enable-controlled-folders.md)
##### [Dostosuj kontrolowany dostęp do folderu](customize-controlled-folders.md)
#### [Ochrona przed wykorzystywaniem]()
##### [Chroń urządzenia przed wykorzystaniem](exploit-protection.md)
##### [Ocena ochrony przed wykorzystaniem](evaluate-exploit-protection.md)
##### [Włącz ochronę przed wykorzystaniem](enable-exploit-protection.md)
##### [Dostosuj ochronę przed wykorzystaniem](customize-exploit-protection.md)
##### [Importuj, eksportuj i wdrażaj konfigurację ochrony przed wykorzystaniem](import-export-exploit-protection-emet-xml.md)
##### [Odwołanie do ochrony przed wykorzystaniem](exploit-protection-reference.md)
#### [Ochrona sieci]()
##### [Chroń sieć](network-protection.md)
##### [Oceń ochronę sieci](evaluate-network-protection.md)
##### [Wyłącz ochronę sieci](enable-network-protection.md)

### Ochrona nowej generacji
#### [Omówienie ochrony nowej generacji](next-generation-protection.md)
##### [Omówienie programu antywirusowego Microsoft Defender](microsoft-defender-antivirus-windows.md)
##### [Lepiej razem: program antywirusowy Microsoft Defender i usługa ochrony punktu końcowego w usłudze Microsoft Defender](why-use-microsoft-defender-antivirus.md)
##### [Lepiej razem: program antywirusowy Microsoft Defender i usługa Office 365](office-365-microsoft-defender-antivirus.md)
#### [Oceń program antywirusowy Microsoft Defender](evaluate-microsoft-defender-antivirus.md)
#### [Konfiguruj funkcje programu antywirusowego Microsoft Defender](configure-microsoft-defender-antivirus-features.md)
#### [Ochrona w chmurze i program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)
##### [Dlaczego ochrona w chmurze powinna być włączona](why-cloud-protection-should-be-on-mdav.md)
##### [Wyłącz ochronę w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)
##### [Określ poziom ochrony w chmurze](specify-cloud-protection-level-microsoft-defender-antivirus.md)
##### [Ochrona w chmurze i przesyłanie próbek](cloud-protection-microsoft-antivirus-sample-submission.md)
#### [Skonfiguruj i zweryfikuj połączenia sieciowe programu antywirusowego Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)
#### [Chroń ustawienia zabezpieczeń z ochroną przed naruszeniami](prevent-changes-to-security-settings-with-tamper-protection.md)
#### [Włącz blokowanie od pierwszego wejrzenia](configure-block-at-first-sight-microsoft-defender-antivirus.md)
#### [Skonfiguruj limit czasu blokady chmury](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)
#### [Konfiguruj ochronę behawioralną, heurystyczną i w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md)
#### [Wykryj i blokuj potencjalnie niechciane aplikacje](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
#### [Włącz i skonfiguruj zawsze aktywną ochronę programu antywirusowego Microsoft Defender w zasadach grupy](configure-real-time-protection-microsoft-defender-antivirus.md)
#### [Konfiguruj korygowanie wykryć programu antywirusowego Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)
#### [Konfiguruj skanowania programu antywirusowego Microsoft Defender](schedule-antivirus-scans.md)
##### [Planuj skanowanie przy użyciu zasad grupy](schedule-antivirus-scans-group-policy.md)
##### [Planuj skanowanie przy użyciu programu PowerShell](schedule-antivirus-scans-powershell.md)
##### [Planuj skanowanie przy użyciu usługi WMI](schedule-antivirus-scans-wmi.md)
#### [Użyj ograniczonego, okresowego skanowania w programie antywirusowym Microsoft Defender](limited-periodic-scanning-microsoft-defender-antivirus.md)
#### [Kompatybilność z innymi produktami zabezpieczeń](microsoft-defender-antivirus-compatibility.md)
#### [Znajdź nazwy wykrywania złośliwego oprogramowania dla usługi ochrony punktu końcowego w usłudze Microsoft Defender](find-defender-malware-name.md)

#### [Pobierz aktualizacje oprogramowania antywirusowego i chroniącego przed złośliwym kodem](manage-updates-baselines-microsoft-defender-antivirus.md)
##### [Zarządzaj źródłami aktualizacji programu antywirusowego Microsoft Defender](manage-protection-updates-microsoft-defender-antivirus.md)
##### [Zarządzaj harmonogramem pobierania i stosowania aktualizacji ochrony](manage-protection-update-schedule-microsoft-defender-antivirus.md)
##### [Zarządzaj procesem stopniowego wdrażania aktualizacji usługi Microsoft Defender](manage-gradual-rollout.md)
##### [Konfiguruj stopniowy proces wdrażania aktualizacji usługi Microsoft Defender](configure-updates.md)
##### [Zarządzaj aktualizacjami programu antywirusowego Microsoft Defender i skanuj w poszukiwaniu nieaktualnych punktów końcowych](manage-outdated-endpoints-microsoft-defender-antivirus.md)
##### [Zarządzaj wymuszonymi aktualizacjami opartymi na zdarzeniach](manage-event-based-updates-microsoft-defender-antivirus.md)
##### [Zarządzaj aktualizacjami dla urządzeń przenośnych i maszyn wirtualnych ](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)

#### [Zarządzaj programem antywirusowym Microsoft Defender dla swojej organizacji](configuration-management-reference-microsoft-defender-antivirus.md)
##### [Użyj programu Microsoft Endpoint Manager do zarządzania programem antywirusowym Microsoft Defender](use-intune-config-manager-microsoft-defender-antivirus.md)
##### [Użyj ustawień zasad grupy do zarządzania programem antywirusowym Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md)
##### [Za pomocą poleceń cmdlet programu PowerShell zarządzaj programem antywirusowym Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
##### [Użyj instrumentacji zarządzania Windows (WMI) do zarządzania programem antywirusowym Microsoft Defender](use-wmi-microsoft-defender-antivirus.md)
##### [Za pomocą narzędzia mpcmdrun.exe zarządzaj programem antywirusowym Microsoft Defender](command-line-arguments-microsoft-defender-antivirus.md)
##### [Konfiguruj powiadomienia wyświetlane w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)
##### [Określ, czy użytkownicy mogą lokalnie modyfikować ustawienia zasad programu antywirusowego Microsoft Defender](configure-local-policy-overrides-microsoft-defender-antivirus.md)
##### [Określ, czy użytkownicy mogą wyświetlać interfejs użytkownika programu antywirusowego Microsoft Defender lub korzystać z niego](prevent-end-user-interaction-microsoft-defender-antivirus.md)

#### [Wdrażaj i raportuj na temat programu antywirusowego Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
##### [Wdrażaj i włącz program antywirusowy Microsoft Defender](deploy-microsoft-defender-antivirus.md)
##### [Przewodnik wdrożenia programu antywirusowego Microsoft Defender w środowisku infrastruktury pulpitu wirtualnego](deployment-vdi-microsoft-defender-antivirus.md)
##### [Raportuj na temat programu antywirusowego Microsoft Defender](report-monitor-microsoft-defender-antivirus.md)

#### [Skanuj i koryguj](review-scan-results-microsoft-defender-antivirus.md)
##### [Konfiguruj i uruchom skanowania programu antywirusowego Microsoft Defender na żądanie](run-scan-microsoft-defender-antivirus.md)
##### [Uruchom i przejrzyj wyniki skanowania programu Microsoft Defender Offline](microsoft-defender-offline.md)
##### [Konfiguruj opcje skanowania programu antywirusowego Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)
##### [Przywróć pliki poddane kwarantannie w programie antywirusowym Microsoft Defender](restore-quarantined-files-microsoft-defender-antivirus.md)

#### [Wykluczenia programu antywirusowego Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
##### [Wykluczenia oparte na rozszerzeniu pliku i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
##### [Wykluczenia dla plików otwartych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
##### [Wykluczenia dla systemu Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
##### [Typowe błędy, których należy unikać](common-exclusion-mistakes-microsoft-defender-antivirus.md)

#### Diagnostyka i wydajność programu antywirusowego Microsoft Defender
##### [Raporty kondycji urządzenia i zgodności](machine-reports.md)
##### [Rozwiąż problemy z wydajnością związane z ochroną w czasie rzeczywistym](troubleshoot-performance-issues.md) 
##### [Rozwiąż problemy z raportowaniem programu antywirusowego Microsoft Defender w obszarze Zgodność aktualizacji](troubleshoot-reporting.md)
##### [Dostrój wydajność programu antywirusowego Microsoft Defender](tune-performance-defender-antivirus.md)

#### Rozwiąż problemy z programem antywirusowym Microsoft Defender
##### [Przejrzyj dzienniki zdarzeń i kody błędów, aby rozwiązać problemy z programem antywirusowym Microsoft Defender](troubleshoot-microsoft-defender-antivirus.md)
##### [Rozwiąż problemy z programem antywirusowym Microsoft Defender podczas migracji z rozwiązania innej firmy](troubleshoot-microsoft-defender-antivirus-when-migrating.md)

#### [Ochrona sieci Web]()
##### [Omówienie ochrony sieci Web](web-protection-overview.md)
##### [Ochrona przed zagrożeniami sieci Web]()
###### [Omówienie ochrony przed zagrożeniami sieci Web](web-threat-protection.md)
###### [Monitoruj bezpieczeństwo sieci Web](web-protection-monitoring.md)
###### [Odpowiadaj na zagrożenia sieci Web](web-protection-response.md)
##### [Filtrowanie zawartości sieci Web](web-content-filtering.md)

#### [Kontrola urządzenia]()
##### [Ochrona magazynu wymiennego](device-control-removable-storage-protection.md)
##### [Kontrola dostępu do magazynu wymiennego](device-control-removable-storage-access-control.md)
##### [Instalowanie urządzenia](mde-device-control-device-installation.md)
##### [Kontrola urządzenia – ochrona drukarki](printer-protection.md)
##### [Raporty kontroli urządzenia](device-control-report.md)

#### [Blokowanie i ograniczanie behawioralne]()
##### [Blokowanie i ograniczanie behawioralne](behavioral-blocking-containment.md)
##### [Blokowanie behawioralne klienta](client-behavioral-blocking.md)
##### [Blokowanie pętli opinii](feedback-loop-blocking.md)


### [Rozwiązywanie problemów z wynikami fałszywie pozytywnymi/negatywnymi w ochronie punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)


### [Zarządzaj konfiguracją urządzenia]()

#### [Zwiększ zgodność do planu bazowego zabezpieczeń](configure-machines-security-baseline.md)
#### [Optymalizuj wdrażanie i wykrywanie reguł zmniejszania obszaru ataków](configure-machines-asr.md)

## [Badanie zagrożeń i odpowiadanie na nie]()
### [Wykrywanie i reagowanie dotyczące punktów końcowych]()
#### [Omówienie wykrywania i reagowania dotyczącego punktów końcowych](overview-endpoint-detection-response.md)
#### [Pulpit nawigacyjny operacji zabezpieczeń](security-operations-dashboard.md)
#### [Prześlij pliki](admin-submissions-mde.md)
#### [Kolejka zdarzeń]()
##### [Wyświetl i organizuj kolejkę zdarzeń](view-incidents-queue.md)
##### [Zarządzanie zdarzeniami](manage-incidents.md)
##### [Badanie zdarzeń](investigate-incidents.md)

#### [Kolejka alertów]()
##### [Kolejka alertów w usłudze Microsoft 365 Defender](alerts-queue-endpoint-detection-response.md)
##### [Wyświetl i organizuj kolejkę alertów](alerts-queue.md)
##### [Przeglądaj alerty](review-alerts.md)
##### [Zarządzaj alertami](manage-alerts.md)
##### [Badaj alerty](investigate-alerts.md)
##### [Badaj pliki](investigate-files.md)
##### [Badaj urządzenia](investigate-machines.md)
##### [Badaj adres IP](investigate-ip.md)
##### [Badaj domenę](investigate-domain.md)
###### [Badaj zdarzenia połączenia, które występują za serwerami proxy przesyłania dalej](investigate-behind-proxy.md)
##### [Badaj konto użytkownika](investigate-user.md)

#### [Wykonaj akcje odpowiedzi]()
##### [Wykonaj akcje odpowiedzi na urządzeniu]()
###### [Akcje odpowiedzi na urządzeniach](respond-machine-alerts.md)
###### [Zarządzaj tagami](respond-machine-alerts.md#manage-tags)
###### [Rozpocznij automatyczne badanie](respond-machine-alerts.md#initiate-automated-investigation)
###### [Rozpocznij sesję reagowania w czasie rzeczywistym](respond-machine-alerts.md#initiate-live-response-session)
###### [Zbieraj pakiet badań](respond-machine-alerts.md#collect-investigation-package-from-devices)
###### [Uruchomiono skanowanie antywirusowe](respond-machine-alerts.md#run-microsoft-defender-antivirus-scan-on-devices)
###### [Ogranicz wykonanie aplikacji](respond-machine-alerts.md#restrict-app-execution)
###### [Izoluj urządzenia z sieci](respond-machine-alerts.md#isolate-devices-from-the-network)
###### [Konsultuj się z ekspertem ds. zagrożeń](respond-machine-alerts.md#consult-a-threat-expert)
###### [Sprawdź szczegóły aktywności w Centrum akcji](respond-machine-alerts.md#check-activity-details-in-action-center)

##### [Wykonaj akcje odpowiedzi na pliku]()
###### [Akcje odpowiedzi na pliki](respond-file-alerts.md)
###### [Zatrzymaj i poddaj kwarantannie pliki w sieci](respond-file-alerts.md#stop-and-quarantine-files-in-your-network)
###### [Przywróć plik z kwarantanny](respond-file-alerts.md#restore-file-from-quarantine)
###### [Dodaj wskaźniki, aby zablokować lub zezwolić na plik](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
###### [Konsultuj się z ekspertem ds. zagrożeń](respond-file-alerts.md#consult-a-threat-expert)
###### [Sprawdź szczegóły aktywności w Centrum akcji](respond-file-alerts.md#check-activity-details-in-action-center)
###### [Pobierz lub zbierz plik](respond-file-alerts.md#download-or-collect-file)
###### [Głęboka analiza](respond-file-alerts.md#deep-analysis)

#### [Wyświetl i zatwierdź akcje korygowania](manage-auto-investigation.md)
##### [Wyświetl szczegóły i wyniki zautomatyzowanych badań](auto-investigation-action-center.md)

#### [Badaj jednostki używając reagowania w czasie rzeczywistym]()
##### [Badaj jednostki na urządzeniach](live-response.md)
##### [Przykłady poleceń reagowania w czasie rzeczywistym](live-response-command-examples.md)

#### [Użyj etykiet poufności, aby nadać priorytet reagowaniu na zdarzenia](information-protection-investigation.md)

#### [Raportowanie]()
##### [Power BI — jak używać interfejsu API — przykłady](api-power-bi.md)
##### [Raporty ochrony przed zagrożeniami](threat-protection-reports.md)

### [Zaawansowane wyszukiwanie zagrożeń]()
#### [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
#### [Analiza schematu](advanced-hunting-schema-reference.md)
#### [DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)

### [Analiza zagrożeń — omówienie](threat-analytics.md)
#### [Przeczytaj raport analityczny](threat-analytics-analyst-reports.md)

### [Funkcja EDR w trybie blokowania](edr-in-block-mode.md)

### [Zautomatyzowane badania i reakcje]()
#### [Omówienie funkcji zautomatyzowanego badania i reakcji](automated-investigations.md)
#### [Poziomy automatyzacji w funkcji zautomatyzowanego badania i reakcji](automation-levels.md)
#### [Skonfiguruj możliwości funkcji zautomatyzowanego badania i reakcji](configure-automated-investigations-remediation.md)

### [Microsoft Threat Experts]()
#### [Przegląd ekspertów ds. zagrożeń firmy Microsoft](microsoft-threat-experts.md)
#### [Konfigurowanie funkcji usługi Microsoft Threat Experts i zarządzanie nimi](configure-microsoft-threat-experts.md)



## Odwołanie
### [Omówienie koncepcji analizy zagrożeń](threat-indicator-concepts.md)
### [Konfiguruj integrację z innymi rozwiązaniami firmy Microsoft]()
#### [Konfiguruj dostęp warunkowy](configure-conditional-access.md)
#### [Konfiguruj integrację usługi Microsoft Defender dla aplikacji w chmurze](microsoft-cloud-app-security-config.md)
### [Zarządzanie i interfejsy API]()
#### [Przegląd zarządzania i interfejsów API](management-apis.md)
#### [Informacje o wersji interfejsu API](api-release-notes.md)
#### [Interfejs usługi ochrony punktu końcowego w usłudze Microsoft Defender]()
##### [Wprowadzenie]()
###### [Interfejs usługi ochrony punktu końcowego w usłudze Microsoft Defender — licencja i postanowienia](api-terms-of-use.md)
###### [Uzyskaj dostęp do interfejsów API usługi ochrony punktu końcowego w usłudze Microsoft Defender](apis-intro.md)
###### [Witaj świecie!](api-hello-world.md)
###### [Uzyskiwanie dostępu za pomocą kontekstu aplikacji](exposed-apis-create-app-webapp.md)
###### [Uzyskiwanie dostępu za pomocą kontekstu użytkownika](exposed-apis-create-app-nativeapp.md)



##### [Schemat interfejsów API usługi ochrony punktu końcowego w usłudze Microsoft Defender]()
###### [Obsługiwane interfejsy API usługi ochrony punktu końcowego w usłudze Microsoft Defender](exposed-apis-list.md)
###### [Typowe kody błędów interfejsu API REST](common-errors.md)
###### [Zaawansowane wyszukiwanie zagrożeń](run-advanced-query-api.md)

###### [Alert]()
####### [Metody alertu i właściwości](alerts.md)
####### [Wylistuj alerty](get-alerts.md)
####### [Utwórz alert](create-alert-by-reference.md)
####### [Aktualizacja alertów partiami](batch-update-alerts.md)
####### [Aktualizuj alert](update-alert.md)
####### [Pobierz informacje o alercie według identyfikatora](get-alert-info-by-id.md)
####### [Pobierz informacje o domenach związanych z alertem](get-alert-related-domain-info.md)
####### [Pobierz informacje o pliku powiązanym z alertem](get-alert-related-files-info.md)
####### [Pobierz informacje o adresach IP powiązanych z alertem](get-alert-related-ip-info.md)
####### [Pobierz informacje o urządzeniu powiązanym z alertem](get-alert-related-machine-info.md)
####### [Pobierz informacje o użytkowniku powiązanym z alertem](get-alert-related-user-info.md)


###### [Ocena luk w zabezpieczeniach i bezpiecznych konfiguracji]()
####### [Eksportuj metody oceny i właściwości](get-assessment-methods-properties.md)
####### [Eksportuj ocenę bezpiecznej konfiguracji](get-assessment-secure-config.md)
####### [Eksportuj ocenę spisu oprogramowania](get-assessment-software-inventory.md)
####### [Eksportuj ocenę luk w zabezpieczeniach oprogramowania](get-assessment-software-vulnerabilities.md)

###### [Badanie zautomatyzowane]()
####### [Metody i właściwości badania](investigation.md)
####### [Wylistuj badanie](get-investigation-collection.md)
####### [Pobierz badanie](get-investigation-object.md)
####### [Uruchom badanie](initiate-autoir-investigation.md)

###### [Domain (Domena)]()
####### [Pobierz alerty powiązane z domeną](get-domain-related-alerts.md)
####### [Pobierz maszyny powiązane z domeną](get-domain-related-machines.md)
####### [Pobierz statystyki domeny](get-domain-statistics.md)

###### [Plik]()
####### [Metody i właściwości pliku](files.md)
####### [Pobierz informacje o pliku](get-file-information.md)
####### [Pobierz alerty powiązane z plikiem](get-file-related-alerts.md)
####### [Pobierz maszyny powiązane z plikiem](get-file-related-machines.md)
####### [Pobierz statystyki pliku](get-file-statistics.md)

###### [Wskaźniki]()
####### [Metody i właściwości wskaźników](ti-indicator.md)
####### [Wylistuj wskaźniki](get-ti-indicators-collection.md)
####### [Prześlij wskaźniki](post-ti-indicator.md)
####### [Importuj wskaźniki](import-ti-indicators.md)
####### [Usuń wskaźniki](delete-ti-indicator-by-id.md)

###### [Adres IP]()
####### [Pobierz alerty związane z adresem IP](get-ip-related-alerts.md)
####### [Pobierz statystyki adresów IP](get-ip-statistics.md)

###### [Biblioteka dokumentów reagowania w czasie rzeczywistym]()
####### [Metody i właściwości biblioteki dokumentów reagowania w czasie rzeczywistym](live-response-library-methods.md)
####### [Wylistuj pliki biblioteki dokumentów](list-library-files.md)
####### [Przekaż do biblioteki dokumentów reagowania w czasie rzeczywistym](upload-library.md)
####### [Usuń z biblioteki dokumentów](delete-library.md)


###### [Komputer]()
####### [Metody i właściwości komputera](machine.md)
####### [Wylistuj komputery](get-machines.md)
####### [Pobierz komputer według identyfikatora](get-machine-by-id.md)
####### [Pobierz dziennik komputera dla użytkowników](get-machine-log-on-users.md)
####### [Pobierz alerty związane z komputerem](get-machine-related-alerts.md)
####### [Pobierz zainstalowane oprogramowanie](get-installed-software.md)
####### [Pobierz wykryte luki w zabezpieczeniach](get-discovered-vulnerabilities.md)
####### [Pobierz rekomendacje dotyczące zabezpieczeń](get-security-recommendations.md)
####### [Dodaj lub usuń tagi komputera](add-or-remove-machine-tags.md)
####### [Znajdź komputer według IP](find-machines-by-ip.md)
####### [Znajdź komputer według tagu](find-machines-by-tag.md)
####### [Pobierz brakujące KB](get-missing-kbs-machine.md)
####### [Ustaw wartość urządzenia](set-device-value.md)
####### [Zaktualizuj komputer](update-machine-method.md)



###### [Akcja komputera]()
####### [Metody i właściwości akcji komputera](machineaction.md)
####### [Wylistuj akcje komputera](get-machineactions-collection.md)
####### [Pobierz akcję komputera](get-machineaction-object.md)
####### [Zbieraj pakiet badań](collect-investigation-package.md)
####### [Pobierz identyfikator URI SAS pakietu badania](get-package-sas-uri.md)
####### [Pobierz wynik reagowania w czasie rzeczywistym](get-live-response-result.md)
####### [Izoluj komputer](isolate-machine.md)
####### [Zwolnij komputer z izolacji](unisolate-machine.md)
####### [Ogranicz wykonanie aplikacji](restrict-code-execution.md)
####### [Usuń restrykcję aplikacji](unrestrict-code-execution.md)
####### [Uruchomiono skanowanie antywirusowe](run-av-scan.md)
####### [Uruchom reagowanie w czasie rzeczywistym](run-live-response.md)
####### [Odłącz komputer](offboard-machine-api.md)
####### [Zatrzymaj plik i poddaj go kwarantannie](stop-and-quarantine-file.md)
####### [Anuluj akcję komputera](cancel-machine-action.md)

###### [Zalecenie]()
####### [Metody i właściwości rekomendacji](recommendation.md)
####### [Wylistuj wszystkie rekomendacje](get-all-recommendations.md)
####### [Pobierz rekomendację według identyfikatora](get-recommendation-by-id.md)
####### [Pobierz rekomendację według oprogramowania](list-recommendation-software.md)
####### [Wylistuj komputery według rekomendacji](get-recommendation-machines.md)
####### [Wylistuj luki w zabezpieczeniach według rekomendacji](get-recommendation-vulnerabilities.md)

###### [Akcja korygowania]()
####### [Metody i właściwości akcji korygowania](get-remediation-methods-properties.md)
####### [Pobierz jedną akcję korygującą według identyfikatora](get-remediation-one-activity.md)
####### [Wylistuj wszystkie działania korygujące](get-remediation-all-activities.md)
####### [Wylistuj narażone urządzenia z jednym działaniem korygowania](get-remediation-exposed-devices-activities.md)

###### [Wynik]()
####### [Metody i właściwości wyniku](score.md)
####### [Wylistuj stopień zagrożenia według grupy komputera](get-machine-group-exposure-score.md)
####### [Pobierz stopnień zagrożenia](get-exposure-score.md)
####### [Pobierz wskaźnik bezpieczeństwa urządzenia](get-device-secure-score.md)

###### [Oprogramowanie]()
####### [Metody i właściwości oprogramowania](software.md)
####### [Wylistuj oprogramowanie](get-software.md)
####### [Pobierz oprogramowanie według identyfikatora](get-software-by-id.md)
####### [Wylistuj dystrybucję wersji oprogramowania](get-software-ver-distribution.md)
####### [Wylistuj komputery według oprogramowania](get-machines-by-software.md)
####### [Wylistuj luki w zabezpieczeniach według oprogramowania](get-vuln-by-software.md)
####### [Pobierz brakujące KB](get-missing-kbs-software.md)

###### [Użytkownik]()
####### [Metody użytkownika](user.md)
####### [Pobierz alerty powiązane z użytkownikiem](get-user-related-alerts.md)
####### [Pobierz komputery powiązane z użytkownikiem](get-user-related-machines.md)

###### [Luka w zabezpieczeniach]()
####### [Metody i właściwości luki w zabezpieczeniach](vulnerability.md)
####### [Wylistuj luki w zabezpieczeniach](get-all-vulnerabilities.md)
####### [Wylistuj luki w zabezpieczeniach według komputera i oprogramowania](get-all-vulnerabilities-by-machines.md)
####### [Pobierz lukę w zabezpieczeniach według identyfikatora](get-vulnerability-by-id.md)
####### [Wylistuj komputery według luk w zabezpieczeniach](get-machines-by-vulnerability.md)

##### [W jaki sposób używać interfejsów API — przykłady]()
###### [Power Automate](api-microsoft-flow.md)
###### [Power BI](api-power-bi.md)
###### [Zaawansowane wyszukiwanie zagrożeń przy użyciu języka Python](run-advanced-query-sample-python.md)
###### [Zaawansowane wyszukiwanie zagrożeń przy użyciu programu PowerShell](run-advanced-query-sample-powershell.md)
###### [Używaj zapytań OData](exposed-apis-odata-samples.md)


#### [Interfejs API przesyłania strumieniowego nieprzetworzonych danych]()
##### [Przesyłanie strumieniowe nieprzetworzonych danych](raw-data-export.md)
##### [Przesyłanie strumieniowe zdarzeń zaawansowanego wyszukiwania zagrożeń do centrum zdarzeń platformy Azure](raw-data-export-event-hub.md)
##### [Przesyłanie strumieniowe zdarzeń zaawansowanego wyszukiwania zagrożeń do konta magazynu](raw-data-export-storage.md)

#### [Integracja zarządzania informacjami i zdarzeniami zabezpieczeń]()
##### [Integruj narzędzia SIEM z usługą ochrony punktu końcowego w usłudze Microsoft Defender](configure-siem.md)
##### [Rozwiąż problemy z integracją narzędzia SIEM](troubleshoot-siem.md)

#### [Partnerzy i interfejsy API]()
##### [Aplikacje partnerskie](partner-applications.md)
##### [Połączone aplikacje](connected-applications.md)
##### [Eksplorator interfejsu](api-explorer.md)

#### [Kontrola dostępu oparta na rolach]()
##### [Zarządzaj dostępem do portalu przy użyciu kontroli dostępu opartej na rolach](rbac.md)
##### [Twórz role i zarządzaj nimi](user-roles.md)
##### [Twórz grupy urządzeń i zarządzaj nimi]()
###### [Używanie grup urządzeń](machine-groups.md)
###### [Twórz tagi urządzeń i zarządzaj nimi](machine-tags.md)







### [Integracja dostawcy zarządzanych usług zabezpieczeń (MSSP)]()
#### [Konfiguruj integrację dostawcy zarządzanych usług zabezpieczeń](configure-mssp-support.md)
#### [Obsługiwani dostawcy zarządzanych usług zabezpieczeń](mssp-list.md)
#### [Przyznaj dostawcy zarządzanych usług zabezpieczeń dostęp do portalu](grant-mssp-access.md)
#### [Uzyskaj dostęp do portalu klienta dostawcy zarządzanych usług zabezpieczeń](access-mssp-portal.md)
#### [Konfiguruj powiadomienia o alertach](configure-mssp-notifications.md)
#### [Uzyskiwanie dostępu do aplikacji partnera](exposed-apis-create-app-partners.md)
#### [Pobierz alerty z dzierżawy klienta](fetch-alerts-mssp.md)
#### [Możliwość dostawcy zarządzanych usług zabezpieczeń](mssp-support.md)
### [Scenariusz integracji partnera]()
#### [Możliwości partnerów technicznych](partner-integration.md)
#### [Zostań partnerem usługi ochrony punktu końcowego w usłudze Microsoft Defender](get-started-partner-integration.md)
### [Integracje]()
#### [Integracje usługi ochrony punktu końcowego w usłudze Microsoft Defender](threat-protection-integration.md)
#### [Chroń użytkowników, dane i urządzenia z dostępem warunkowym](conditional-access.md)
#### [Omówienie integracji usługi Microsoft Defender dla aplikacji w chmurze](microsoft-cloud-app-security-integration.md)

### [Omówienie ochrony informacji w systemie Windows]()
#### [Integracja z systemem Windows](information-protection-in-windows-overview.md)

### [Uzyskaj dostęp do centrum społeczności usługi ochrony punktu końcowego w usłudze Microsoft Defender](community.md)

### [Przydatne zasoby](helpful-resources.md)

## [Rozwiązywanie problemów]()
### [Rozwiąż problem ze stanem czujnika]()
#### [Sprawdź stan czujnika](check-sensor-status.md)
#### [Napraw niesprawne czujniki](fix-unhealthy-sensors.md)
#### [Nieaktywne urządzenia](fix-unhealthy-sensors.md#inactive-devices)
#### [Nieprawidłowo skonfigurowane urządzenia](fix-unhealthy-sensors.md#misconfigured-devices)
#### [Przejrzyj zdarzenia i błędy czujnika na komputerach z podglądem zdarzeń](event-error-codes.md)

### [Rozwiąż problemy z kondycją czujnika używając analizatora klienta]()
#### [Omówienie funkcji analizatora klienta](overview-client-analyzer.md)
#### [Pobierz i uruchom analizator klienta](download-client-analyzer.md)
#### [Uruchom analizator klienta w systemie Windows](run-analyzer-windows.md)
#### [Uruchom analizator klienta w systemie macOS lub Linux](run-analyzer-macos-linux.md)
#### [ Zbieranie danych na potrzeby zaawansowanego rozwiązywania problemów w systemie Windows](data-collection-analyzer.md)
#### [Zrozumienie raportu HTML analizatora](analyzer-report.md)
#### [Prześlij opinię na temat narzędzia analizatora klienta](analyzer-feedback.md)

 

### [Rozwiąż problemy z usługą ochrony punktu końcowego w usłudze Microsoft Defender]()
#### [Rozwiąż problemy z usługami](troubleshoot-mdatp.md)
#### [Skontaktuj się z pomocą techniczną usługi ochrony punktu końcowego w usłudze Microsoft Defender](contact-support.md)

### [Rozwiąż problem z usługą reagowania w czasie rzeczywistym](troubleshoot-live-response.md)

### [Zbieraj dzienniki obsługi technicznej używając funkcji LiveAnalyzer](troubleshoot-collect-support-log.md)

### [Rozwiąż problemy z zmniejszaniem obszaru podatnego na ataki]()
#### [Ochrona sieci](troubleshoot-np.md)
#### [Reguły zmniejszania obszaru podatnego na ataki](troubleshoot-asr.md)
#### [Przeprowadź migrację do reguł zmniejszania obszaru podatnego na ataki](migrating-asr-rules.md)

# [Dokumentacja usługi Microsoft 365 Defender]()
## [Microsoft 365 Defender](../defender/index.yml)
## [Ochrona usługi Office 365 w usłudze Defender](../office-365-security/index.yml)
## [Defender for Identity](/defender-for-identity/)
## [Defender for Cloud Apps](/cloud-app-security/)
## [Defender dla Firm](../defender-business/index.yml)

