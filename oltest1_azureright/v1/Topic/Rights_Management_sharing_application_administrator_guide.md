---
description: na
keywords: na
title: Rights Management sharing application administrator guide
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
---
# Rights Management delen toepassing beheerdershandleiding
Gebruik de volgende informatie als u bent verantwoordelijk voor het delen van toepassing op een bedrijfsnetwerk van Microsoft Rights Management of als u meer technische informatie dan is in de [Rights Management delen toepassing handleiding](../Topic/Rights_Management_sharing_application_user_guide.md) of [Veelgestelde vragen over Microsoft Rights Management delen van de toepassing voor Windows](http://go.microsoft.com/fwlink/?LinkId=303971):

-   [Automatische implementatie voor de Microsoft Rights Management-toepassing voor delen](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ScriptedInstall)

    -   [Installatie geslaagd verifiëren](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)

    -   [Opdrachten verwijderen](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_uninstallscripted)

    -   [Onderdrukken van automatische updates](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SuppressAutomaticUpdates)

    -   [Alleen Azure RMS: Document bijhouden configureren](#BKMK_DocumentTracking)

    -   [AD RMS: Ondersteuning voor meerdere e-mailbericht domeinen binnen uw organisatie](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains)

-   [Technisch overzicht voor de Microsoft Rights Management-toepassing voor delen](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_AdminOverview)

    -   [Niveaus van beveiliging – systeemeigen en algemene](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection)

    -   [Ondersteunde bestandstypen en bestandsextensies](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes)

    -   [Het standaardniveau van de beveiliging van bestanden wijzigen](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection)

> [!TIP]
> Als u geen ervaring met de delen RMS-app of op zoek naar meer informatie, Zie [hoe RMS beschermt alle bestandstypen – met behulp van de app RMS sharing](https://curah.microsoft.com/191031/how-rms-protects-all-file-types-by-using-the-rms-sharing-app).

De RMS sharing van toepassing is het meest geschikt is voor gebruik met Azure RMS omdat deze implementatieconfiguratie ondersteunt verzenden beveiligde bijlagen voor gebruikers in een andere organisatie en opties voor e-mailmeldingen en documenten bijhouden met ingetrokken.  Echter met een aantal beperkingen werkt ook met de lokale versie, AD RMS. Zie voor een uitgebreide vergelijking van functies die worden ondersteund door Azure RMS en AD RMS [vergelijken Azure Rights Management en AD RMS](https://technet.microsoft.com/library/jj739831.aspx). AD RMS als migreren naar Azure RMS, Zie [migratie van AD RMS naar Azure Rights Management](https://technet.microsoft.com/library/dn858447.aspx).

## <a name="BKMK_ScriptedInstall"></a>Automatische implementatie voor de Microsoft Rights Management-toepassing voor delen
Een script installatie, waardoor het geschikt is voor bedrijfsimplementaties biedt ondersteuning voor de Windows-versie van de RMS-toepassing voor delen.

De enige vereisten voor installaties zijn dat de computers die een minimale versie van Windows 7 Service Pack 1 uitgevoerd en of de Microsoft-Framework minimumversie 4.0 is geïnstalleerd. Als u nodig hebt voor het installeren van Microsoft .NET Framework 4.0, kunt u [downloaden voor de installatie van het Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=17718).

#### De RMS sharing toepassing voor automatische implementatie downloaden

1.  Ga naar de [Microsoft Rights Management-toepassing voor Windows delen](http://www.microsoft.com/download/details.aspx?id=40857) pagina in het Microsoft Download Center en klik op **downloaden**.

2.  Selecteer en download de bestanden die u nodig hebt. Er zijn twee client installatiepakketten: een voor Windows 64-bits (Microsoft Rights Management delen toepassing x64.zip) en een voor Windows 32-bits (Microsoft Rights Management delen van de toepassing x86.zip).

3.  Pak de bestanden uit de van gecomprimeerde installatiepakketten, bijvoorbeeld door te dubbelklikken op deze. Kopieer de uitgepakte bestanden naar een netwerklocatie waartoe clientcomputers toegang heeft.

De setuppakketten voor de RMS-toepassing voor delen biedt ondersteuning voor verschillende implementatiescenario's en omvat de volgende:

|Beschrijving|Implementatiescenario voor|
|----------------|------------------------------|
|Microsoft Online-aanmeldhulp|Vereist voor het volgende:<br /><br />-   Office 2010 en Azure RMS<br />-   Office 2013 en Azure RMS als u niet hebt geïnstalleerd de [9 juni 2015 bijwerken voor Office 2013](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Hotfix voor Office (KB 2596501)|Vereist voor het volgende:<br /><br />-   Office 2010 en Azure RMS<br />-   Office 2010 en Active Directory RMS|
|Hotfix naar de AD RMS-Client 1.0 werken met Azure RMS (KB 2843630) inschakelen|Vereist voor het volgende:<br /><br />-   Office 2010 en Azure RMS<br />-   Office 2010 en Active Directory RMS|
|AD RMS-Client en de RMS-toepassing voor delen|Vereist voor het volgende:<br /><br />-   Office 2016 of Office 2013 en Azure RMS of Active Directory RMS<br />-   Office 2010 en Azure RMS<br />-   Office 2010 en Active Directory RMS<br />-   RMS-toepassing en Office-invoegtoepassing alleen delen|
|Office-invoegtoepassing voor het lint|Vereist voor het volgende:<br /><br />-   Office 2016 of Office 2013 en Azure RMS of Active Directory RMS<br />-   Office 2010 en Azure RMS<br />-   Office 2010 en Active Directory RMS<br />-   RMS-toepassing en Office-invoegtoepassing alleen delen|
|Azure Active Directory Rights Management-hulpprogramma voor systeemvoorbereiding|Vereist voor het volgende:<br /><br />-   Office 2010 en Azure RMS|
De volgende procedures gebruiken om op te sporen de opdrachten die zijn vereist voor de implementatie van de RMS sharing toepassing voor deze implementatie scenario's:

-   **Office 2016 of Office 2013 en Azure RMS of Active Directory RMS**

    Uw gebruikers Office 2016 of Office 2013 uitvoert, uw organisatie Azure RMS of Active Directory RMS gebruikt en gebruikers samenwerken met andere organisaties die gebruikmaken van Azure RMS of Active Directory RMS.

-   **Office 2010 en Azure RMS**

    Uw gebruikers Office 2010 worden uitgevoerd en gebruikers samenwerken met andere organisaties die gebruikmaken van Azure RMS of Active Directory RMS Azure RMS maakt gebruik van uw organisatie.

-   **Office 2010 en Active Directory RMS**

    Uw gebruikers Office 2010 worden uitgevoerd, uw organisatie AD RMS gebruikt en gebruikers samenwerken met andere organisaties die gebruikmaken van Azure RMS.

-   **RMS-toepassing en Office-invoegtoepassing alleen delen**

    Uw gebruikers worden uitgevoerd 2016 van Office, Office 2013 of Office 2010 en gebruikers hoeven niet samenwerking met andere organisaties die gebruikmaken van Azure RMS AD RMS maakt gebruik van uw organisatie. Deze installatie, kunt u alleen de delen installeren toepassing en Office-invoegtoepassing.

> [!NOTE]
> In deze scenario's, als uw organisatie AD RMS wordt uitgevoerd, kunnen uw gebruikers beveiligde inhoud ontvangen van andere organisaties die gebruikmaken van Azure RMS, maar uw gebruikers kunnen geen beveiligde verzenden inhoud voor gebruikers in een organisatie die gebruikmaakt van Azure RMS. Echter, als uw organisatie Azure RMS wordt uitgevoerd, uw gebruikers kunnen verzenden en ontvangen beveiligde inhoud van andere organisaties.

Om de installatie voor elke procedure, moet de computer opnieuw. U kunt een automatisch opnieuw opstarten starten met behulp van een opdracht als afsluiten /i.

#### De RMS sharing toepassing voor Office 2016 of Office 2013 en Azure RMS of Active Directory RMS implementeren

-   Voer de volgende opdracht met verhoogde bevoegdheden op elke computer waarop u wilt de RMS sharing toepassing en gerelateerde onderdelen installeren:

    ```
    setup.exe /s
    ```

Om te controleren of geslaagd, Zie de [Installatie geslaagd verifiëren](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) in dit onderwerp.

#### De RMS sharing toepassing voor Office 2010 en Azure RMS implementeren

1.  U moet de globale beheerder voor uw Office 365- of Azure Active Directory-tenant zodat u de URL van de service-certificering van uw organisatie door het uitvoeren van de Azure Active Directory Rights Management-hulpprogramma voor systeemvoorbereiding krijgt. U moet dit hulpprogramma slechts één keer uitgevoerd op een computer. Gebruikt u de URL van de certificeringsinstantie tijdens de installatie van de RMS sharing van toepassing op elke computer:

    1.  Aanmelden bij een computer met een lokale beheerdersaccount.

    2.  Op die computer [download en installeer de Microsoft Online aanmeldhulp](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Voer de volgende opdracht om te zien weergegeven op het scherm de URL van de certificeringsinstantie, die u kunt vervolgens kopiëren en opslaan voor de volgende stap:

        -   Voor Windows 8.1 en Windows 8, 64-bits:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Voor Windows 8.1 en Windows 8, 32-bits:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Voor Windows 7, 64-bits:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Met deze opdracht vraagt u mogelijk uw referenties voor Azure invoeren. Als de computer is niet toegevoegd aan een domein, wordt u gevraagd. Als de computer is toegevoegd aan een domein, kan het hulpprogramma mogelijk in cache opgeslagen referenties gebruiken.

2.  Voer de volgende opdracht met verhoogde bevoegdheden op elke computer waarop u de RMS sharing toepassing wilt installeren:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Op elke computer waarop u de RMS sharing toepassing wordt geïnstalleerd, moeten gebruikers de volgende opdracht uitvoeren (niet nodig voor verhoogde bevoegdheden). Er zijn verschillende manieren om te bereiken, met inbegrip van vragen van gebruikers de opdracht (bijvoorbeeld een koppeling in een e-mailbericht of een koppeling in de portal help helpdesk) uit te voeren of u het kunt toevoegen aan hun aanmeldingsscript:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Om te controleren of geslaagd, Zie de [Installatie geslaagd verifiëren](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) in dit onderwerp.

#### De RMS sharing toepassing voor Office 2010 en Active Directory RMS implementeren

1.  Voer de volgende opdracht met verhoogde bevoegdheden op elke computer waarop u de RMS sharing toepassing wilt installeren:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Op elke computer waarop u de RMS sharing toepassing wordt geïnstalleerd, moeten gebruikers de volgende opdracht uitvoeren (niet nodig voor verhoogde bevoegdheden). Er zijn verschillende manieren om te bereiken, met inbegrip van vragen van gebruikers de opdracht (bijvoorbeeld een koppeling in een e-mailbericht of een koppeling in de portal help helpdesk) uit te voeren of u het kunt toevoegen aan hun aanmeldingsscript:

    -   Voor Windows-10, Windows 8.1 en Windows 8, 64-bits:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Voor Windows-10, Windows 8.1 en Windows 8, 32-bits:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Voor Windows 7, 64-bits:

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

Om te controleren of geslaagd, Zie de [Installatie geslaagd verifiëren](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) in dit onderwerp.

#### Het delen van de toepassing en Office-invoegtoepassing alleen RMS installeren

1.  De AD RMS-Client en de RMS-toepassing voor delen met behulp van de volgende opdracht installeren:

    -   Voor 64-bits Windows:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Voor 32-bits Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Bijvoorbeeld: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  De Office-invoegtoepassing installeren met behulp van de volgende opdrachten:

    -   Voor 64-bits versie van Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Voor 32-bits versie van Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Bijvoorbeeld: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

Om te controleren of geslaagd, Zie de [Installatie geslaagd verifiëren](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) in dit onderwerp.

### <a name="BKMK_verifyscripted"></a>Installatie geslaagd verifiëren
De logboekbestanden van de installatie kunt u controleren of een geïnstalleerd.

##### Om te controleren of de installatie geslaagd voor de toepassing voor Office 2016 of Office 2013 en Azure RMS of Active Directory RMS sharing RMS

-   Om te controleren of succes van de opdracht Setup.exe op elke computer zoeken naar het installatielogboekbestand **RMInstaller.log** in de *%temp%\RMS_installer_ &lt; guid &gt;* map, en vervolgens de afsluitcode identificeren.

    Een installatie heeft een afsluitcode 0 en een ander getal geeft aan dat een mislukte installatie.

    Voorbeeld van de naam van logboekbestand: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

##### Om te controleren of de installatie geslaagd voor de toepassing voor Office 2010 en Azure RMS sharing RMS

1.  Om te controleren of succes van de opdracht Setup.exe op elke computer zoeken naar het installatielogboekbestand **RMInstaller.log** in de *%temp%\RMS_installer_ &lt; guid &gt;* map, en vervolgens de afsluitcode identificeren.

    Een installatie heeft een afsluitcode 0 en een ander getal geeft aan dat een mislukte installatie.

    Voorbeeld van de naam van logboekbestand: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Om te controleren of geslaagd voor de opdracht RMSSetup.exe, moet de gebruiker de volgende bestanden gemaakt in hun *%localappdata%\microsoft\drm* map:

    -   CERTIFICAAT-Machine-2048.drm

    -   CERTIFICAAT Machine.drm

    -   CLC &#42;.drm

    -   GICA &#42;.drm

    Voorbeeld van een bestand CLC &#42;.drm:

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf; k5b11; k4a10; kac15; k29b2b6980f4c} .drm**

##### Om te controleren of de installatie geslaagd voor de toepassing voor Office 2010 en Active Directory RMS sharing RMS

1.  Om te controleren of succes van de opdracht Setup.exe op elke computer zoeken naar het installatielogboekbestand in de *%temp%\RMS_installer_ &lt; guid &gt;* map, en de afsluitcode identificeren.

    Een installatie heeft een afsluitcode 0 en een ander getal geeft aan dat een mislukte installatie.

    Voorbeeld van de naam van logboekbestand: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Om te controleren of succes van de opdracht aadrmprep.exe op elke computer zoeken naar de volgende tekst in het installatielogboekbestand: **aadrmprep.exe is afgesloten met de status geslaagd**

    > [!NOTE]
    > Soms kunt deze installatie tweemaal uitvoeren het eerste exemplaar is mislukt en de tweede is geslaagd.

    Als u handmatig controleren of de wijzigingen in het register dat dit programma maakt wilt, zijn ze als volgt:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @= "&lt; certificering url &gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser = "&lt; default_user &gt;"

##### Installatie geslaagd voor de RMS sharing toepassing en Office-invoegtoepassing alleen controleren

1.  Om te controleren of succes van de opdracht Setup_ipviewer.exe, zoekt u de volgende tekst in het installatielogboekbestand: **Status van de installatie voltooid of fout: 0**

    Voorbeeld van de regels van een geslaagde installatie:

    **MSI (s) (F0:B8) [14:19:57:854]: Product: Active Directory Rights Management Services Client 2.1--installatie is voltooid.**

    **MSI (s) (F0:B8) [14:19:57:854]: Het product is geïnstalleerd. Productnaam: Active Directory Rights Management Services Client 2.1. Versie van het product: 1.0.1179.1. Taal van product: 1033. Fabrikant: Microsoft Corporation. Status van de installatie voltooid of fout: 0.**

2.  Zoeken naar de volgende tekst in het installatielogboekbestand om te controleren of succes van de Office-invoegtoepassing, op elke computer: **Status van de installatie voltooid of fout: 0**

    Voorbeeld van de regels van een geslaagde installatie:

    **MSI (s) (9C: 88) [18:49:04:007]: Product: Microsoft RMS Office-invoegtoepassingen--Installatie is voltooid.**

    **MSI (s) (9C: 88) [18:49:04:007]: Het product is geïnstalleerd. Productnaam: Microsoft RMS Office-invoegtoepassingen. Versie van het product: 1.0.7. Taal van product: 1033. Fabrikant: Microsoft. Status van de installatie voltooid of fout: 0.**

### <a name="BKMK_uninstallscripted"></a>Opdrachten verwijderen
Niet alle van de installatieopdrachten die vereist voor implementaties zijn ondersteuning voor een opdracht verwijderen. Verwijderen van de AD RMS-client en de toepassing voor delen en kunt u de Office-invoegtoepassing verwijderen. Gebruik de volgende opdrachten verwijderen van deze elementen bevatten.

##### Verwijderen van de AD RMS-Client en de RMS-toepassing voor delen

-   Gebruik de volgende opdrachten:

    -   Voor 64-bits Windows:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Voor 32-bits Windows:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

##### De Office-invoegtoepassing verwijderen

-   Gebruik de volgende opdrachten:

    -   Voor 64-bits versie van Office:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Voor 32-bits versie van Office:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

### <a name="BKMK_SuppressAutomaticUpdates"></a>Onderdrukken van automatische updates
Standaard zijn gebruikers als er een nieuwere versie van de RMS-toepassing voor delen op de hoogte gesteld en gevraagd om deze te downloaden. U kunt deze melding onderdrukken door de volgende registersleutel bewerken:

1.  Ga naar **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** en als niet al aanwezig is, maakt u een nieuwe sleutel met de naam **RmsSharingApp**.

2.  Selecteer **RmsSharingApp**, maak een nieuwe DWORD-waarde van **AllowUpdatePrompt**, en de waarde instelt op **0**.

Omdat de RMS-toepassing voor delen wordt niet ondersteund door WSUS, kunt u de volgende techniek gebruiken nieuwe versies van de RMS sharing toepassing voordat deze is geïmplementeerd op alle gebruikers testen:

1.  Op computers met alle gebruikers, voert u een script onderdrukken van automatische updates uit. Op de computers die beheerders gebruiken voor het testen van nieuwe versies, u dit script niet uitvoeren.

2.  Wanneer een nieuwe versie beschikbaar is, kunnen beheerders het downloaden en testen.

3.  Wanneer testen is voltooid en eventuele problemen opgelost, de meest recente versie voor alle gebruikers implementeren met behulp van de automatische implementatie-instructies in deze handleiding.

### <a name="BKMK_DocumentTracking"></a>Alleen Azure RMS: Document bijhouden configureren
Als u hebt een [abonnement dat document bijhouden ondersteunt](https://technet.microsoft.com/en-us/dn858608), het bijhouden van document site is standaard ingeschakeld voor alle gebruikers in uw organisatie.  Bijhouden document bevat informatie zoals e-mailadressen van de mensen die poging tot toegang tot beveiligde documenten die gebruikers gedeeld, wanneer deze mensen probeert te openen en hun locatie. Als deze gegevens om weer te geven is niet toegestaan in uw organisatie vanwege privacyvereisten, kunt u uitschakelen toegang tot het document site bijhouden met behulp van de  [Disable AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) cmdlet. U kunt toegang tot de site opnieuw op elk gewenst moment inschakelen via het [inschakelen AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037), en u kunt controleren of toegang momenteel is ingeschakeld of uitgeschakeld met behulp van [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

 Deze als cmdlets wilt uitvoeren, moet u er ten minste versie **2.3.0.0** van de Azure RMS-module voor Windows PowerShell.  Voor installatie-instructies Zie [installatie van Windows PowerShell voor Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx).

> [!TIP]
> Als u eerder hebt gedownload en geïnstalleerd van de module, het versienummer controleren door het uitvoeren van: `(Get-Module aadrm –ListAvailable).Version`

De volgende URL's worden gebruikt voor het document bijhouden en moet worden toegestaan (bijvoorbeeld toegevoegd aan de zone Vertrouwde websites als u met behulp van Internet Explorer met verbeterde beveiliging):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > deze URL is voor Bing maps.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="BKMK_FederatedDomains"></a>AD RMS: Ondersteuning voor meerdere e-mailbericht domeinen binnen uw organisatie
Als u AD RMS en gebruikers in uw organisatie meerdere e-mailbericht domeinen hebben, moet bijvoorbeeld als gevolg van een fusie of overname, u ervoor de volgende registersleutel bewerken:

1.  Ga naar **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** en als niet al aanwezig is, maakt u een nieuwe sleutel met de naam **RmsSharingApp**.

2.  Selecteer **RmsSharingApp**, maak een nieuwe waarde met meerdere tekenreeksen met de naam **FederatedDomains**, en voeg de domeinen en alle subdomeinen die gebruikmaakt van uw organisatie. Jokertekens worden niet ondersteund.

    Bijvoorbeeld: Het bedrijf Coho bedrijf &amp; Winery heeft een domein standaard e-mailbericht van **cohovineyardandwinery.com**, maar als gevolg van fusie, ook gebruiken de e-mailbericht domeinen **cohowinery.com**, **eastcoast.cohowinery.com**, en **cohovineyard**. Voor de **FederatedDomains** krijgt de beheerder van de waardegegevens: **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Als u niets in dit register wijzigen, gebruikers mogelijk geen inhoud te gebruiken die is beveiligd door andere gebruikers in hun organisatie. Deze bewerking van het register is niet nodig als u Azure RMS.

## <a name="BKMK_AdminOverview"></a>Technisch overzicht voor de Microsoft Rights Management-toepassing voor delen
De Microsoft Rights Management-toepassing voor delen is een optionele downloadbare toepassing voor Microsoft Windows en andere platforms die voorziet in het volgende:

-   Beveiliging van één bestand of bulksgewijs bescherming van meerdere bestanden of van een geselecteerde map.

-   Volledige ondersteuning voor de beveiliging van elk type bestand met een ingebouwde viewer voor veelgebruikte tekst en afbeelding bestandstypen.

-   Algemene beveiliging voor bestanden die RMS beveiliging niet ondersteunen.

-   Volledige interoperabiliteit met bestanden beveiligd met Office Information Rights Management (IRM).

-   Volledige compatibiliteit met PDF-bestanden beveiligen via SharePoint, FCI en ondersteunde PDF-hulpprogramma's voor schrijven.

De Microsoft Rights Management-toepassing voor delen maakt gebruik van de nieuwe [AD RMS 2.1-Client runtime](http://www.microsoft.com/download/details.aspx?id=38396). Met behulp van biedt de functionaliteit van AD RMS 2.1, de Microsoft Rights Management-toepassing voor delen eindgebruikers een eenvoudige ervaring voor beveiliging en verbruik.

Met de release van oktober 2013 van RMS, kunt u systeemeigen documenten beveiligen met behulp van Office 2010 en ze verzenden naar mensen in een ander bedrijf, die u kunt deze vervolgens door Azure RMS verbruiken. Bovendien in deze versie kunt als u AD RMS in cryptografische modus 2, u gebruiken RMS voor personen en inhoud van mensen in een ander bedrijf die gebruikmaakt van Azure RMS in beslag nemen. Zie voor meer informatie over cryptografische modus 2 [AD RMS cryptografische modi](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

### <a name="BKMK_LevelsofProtection"></a>Niveaus van beveiliging – systeemeigen en algemene
Microsoft Rights Management-toepassing voor delen ondersteunt beveiliging op twee verschillende niveaus, zoals beschreven in de volgende tabel.

|Type beveiliging|Systeemeigen|Algemene|
|--------------------|----------------|------------|
|Beschrijving|Voor tekst, afbeeldingen, Microsoft Office (Word, Excel, PowerPoint)-bestanden, PDF-bestanden en andere bestandstypen toepassing die ondersteuning bieden voor AD RMS, biedt native protection een sterk niveau van bescherming met zowel versleuteling en de handhaving van rechten (machtigingen).|Voor alle andere toepassingen en bestandstypen biedt algemene protection een niveau van bescherming met beide bestand inkapseling met behulp van het type .pfile en verificatie om te controleren of een gebruiker is gemachtigd om het bestand te openen.|
|Beveiliging|Bestanden volledig zijn gecodeerd en beveiliging wordt afgedwongen in de volgende manieren:<br /><br />-   Voordat beveiligde inhoud wordt weergegeven, moet verificatie is geslaagd voor iemand die het bestand via e-mail ontvangen of toegang krijgen tot dit via bestand of de share machtigingen optreden.<br />-   Bovendien worden gebruiksrechten en beleid dat door de eigenaar van de inhoud wordt ingesteld als bestanden worden beveiligd volledig afgedwongen wanneer de inhoud wordt weergegeven in een IP-Viewer (voor beveiligde tekst en image-bestanden) of de bijbehorende toepassing (voor alle andere ondersteunde bestandstypen).|Bestandsbeveiliging wordt afgedwongen in de volgende manieren:<br /><br />-   Voordat beveiligde inhoud wordt weergegeven, moet succesvolle verificatie optreden voor gebruikers die gemachtigd zijn om het bestand te openen en gegeven toegang toe. Als de verificatie is mislukt, wordt het bestand niet openen.<br />-   Gebruiksrechten en instelling in de inhoudseigenaar worden om u te informeren geautoriseerde gebruikers van het beleid voor het beoogde gebruik weergegeven.<br />-   Logboekregistratie van gemachtigde gebruikers openen en toegang tot bestanden optreedt, wordt echter geen gebruiksrechten worden afgedwongen door de niet-ondersteuning van toepassingen.|
|Standaard voor bestandstypen|Dit is het standaardniveau van beveiliging voor de volgende bestandstypen:<br /><br />-   Tekst en afbeeldingsbestanden<br />-   Microsoft Office (Word, Excel en PowerPoint)-bestanden<br />-   Document (Portable document format)<br /><br />Voor meer informatie raadpleegt u de volgende sectie [Ondersteunde bestandstypen en bestandsextensies](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes).|Dit is de beveiliging voor alle andere bestandstypen (zoals .vsdx, RTF, enzovoort) niet ondersteund door de volledige bescherming tegen.|
U kunt het standaard beveiligingsniveau dat de RMS-toepassing voor het delen van toepassing is. U kunt het standaardniveau van eigen algemene, van algemene naar native wijzigen en zelfs voorkomen dat de RMS sharing toepassing beveiliging toe te passen. Zie voor meer informatie de [Het standaardniveau van de beveiliging van bestanden wijzigen](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection) in dit onderwerp.

### <a name="BKMK_SupportFileTypes"></a>Ondersteunde bestandstypen en bestandsextensies
De volgende tabel bevat de bestandstypen die worden ondersteund door Microsoft Rights Management delen toepassing. Voor deze bestandstypen, wordt de oorspronkelijke extensie gewijzigd als native beveiligd wordt toegepast en deze bestanden alleen-lezen worden.

Bovendien wanneer de RMS sharing toepassing systeemeigen beveiligd een Word, Excel of PowerPoint-bestand dat gebruikers worden beveiligd door te delen, deze actie maakt automatisch een tweede bestand dat een kopie van het origineel met dezelfde naam maar met een **.ppdf** bestandsnaamextensie ¹. Deze versie van het bestand zorgt u ervoor ontvangers die de RMS sharing toepassing installeren kunnen altijd open het bestand dat systeemeigen beveiliging toegepast is.

Om de bestanden die generieke zijn beveiligd, wordt de oorspronkelijke extensie altijd gewijzigd in .pfile.

> [!WARNING]
> Hebt u firewalls, webproxy of beveiligingssoftware die bekijken en actie volgens bestandsextensies, moet u mogelijk opnieuw configureren van deze ter ondersteuning van deze nieuwe extensies.

|Oorspronkelijke bestandsextensie|RMS beveiligde bestandsnaamextensie|
|------------------------------------|---------------------------------------|
|.txt|.ptxt|
|.XML|.pxml|
|.jpg|.pjpg|
|JPEG|.ppng|
|PDF|.ppdf|
|.PNG|.ppng|
|TIFF|.ptiff|
|.bmp|.pbmp|
|.gif|.pgif|
|.giff|.pgiff|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jif|.pjif|
|.JT|.pjt|
¹ PDF-Rendering mogelijk gemaakt door Foxit. Copyright © 2003-2014 van Foxit Corporation.

De volgende tabel bevat de typen die de delen Microsoft Rights Management-toepassing in Microsoft Office 2016, Office 2013 en Office 2010 ondersteunt. Voor deze bestanden blijft de extensie hetzelfde nadat het bestand wordt beveiligd door RMS.

|Bestandstypen die worden ondersteund door Office|Bestandstypen die worden ondersteund door Office|
|----------------------------------------------------|----------------------------------------------------|
|doc<br /><br />DOCM<br /><br />DOCX<br /><br />dot<br /><br />dotm<br /><br />dotx<br /><br />.potm<br /><br />potx<br /><br />PPS<br /><br />.ppsm<br /><br />ppsx<br /><br />.ppt<br /><br />.pptm|.pptx<br /><br />.thmx<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />werkmap<br /><br />XPS|

### <a name="BKMK_ChangeDefaultProtection"></a>Het standaardniveau van de beveiliging van bestanden wijzigen
U kunt wijzigen hoe de RMS sharing toepassing bestanden beschermt door het bewerken van het register. U kunt bijvoorbeeld bestanden die ondersteuning bieden voor systeemeigen protection generieke worden beschermd door de RMS-toepassing voor delen forceren.

Redenen waarom het handig om dit te doen:

-   Om ervoor te zorgen dat alle gebruikers het bestand vanuit hun mobiele apparaten openen kunnen.

-   Om ervoor te zorgen dat alle gebruikers het bestand openen kunnen als ze niet beschikken over een toepassing ondersteunt die native beveiliging.

-   Aangepast aan waarin bestanden acties uitvoeren door de bestandsnaamextensie en kunnen worden geconfigureerd zodat de extensie .pfile, maar kunnen niet worden geconfigureerd zodat deze kunnen meerdere extensies voor systeemeigen beveiliging.

Op deze manier kunt u de RMS sharing toepassing systeemeigen beveiliging toepassen op bestanden die standaard algemene beveiliging toegepast forceren. Dit wordt mogelijk als er een toepassing die de RMS-APIs – bijvoorbeeld ondersteunt, een line-of-business-toepassingen geschreven door uw interne ontwikkelaars of een toepassing hebt gekocht van een onafhankelijke softwareleverancier (ISV).

U kunt ook de RMS sharing van toepassing op de beveiliging van bestanden blokkeren dwingen (niet van toepassing systeemeigen bescherming of algemene beveiliging). Bijvoorbeeld, dit wordt mogelijk vereist als er een automatische toepassing of service die een specifieke bestand voor het verwerken van de inhoud ervan te openen. Als u beveiliging voor een bestandstype blokkeert, kunnen gebruikers de RMS sharing toepassing niet gebruiken ter bescherming van een bestand met dat bestandstype. Wanneer ze proberen, zien ze een bericht dat de beheerder protection voorkomen heeft en ze hun optreden ter bescherming van het bestand moeten annuleren.

Als u de RMS sharing toepassing algemene beveiliging toepassen op alle bestanden die standaard systeemeigen beveiliging toegepast configureren, moet de volgende wijzigingen in het register:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Maak een nieuwe sleutel met de naam **&#42;**.

    Deze instelling geeft bestanden met de extensie.

2.  In de toegevoegde sleutel van **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\ &#42;**, maak een nieuwe tekenreekswaarde (REG_SZ) met de naam **versleuteling** waarvoor de waarde van **Pfile**.

    Deze instelling resulteert in de RMS sharing toepassen algemene bescherming van de toepassing.

Deze twee instellingen resulteren in de RMS sharing toepassen algemene bescherming van toepassing op alle bestanden die extensie hebben. Als dit het doel, is geen verdere configuratie vereist. U kunt echter uitzonderingen voor specifieke bestandstypen definiëren zodat ze nog steeds systeemeigen worden beveiligd. Hiervoor moet u drie extra register wijzigingen aanbrengen voor elk bestandstype:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Voeg een nieuwe sleutel met de naam van de bestandsextensie (zonder de voorafgaande periode).

    Bijvoorbeeld: voor bestanden met een DOCX-bestandsextensie, maakt u een sleutel met de naam **DOCX**.

2.  In de sleutel voor het nieuwe bestandstype (bijvoorbeeld **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), maak een nieuwe DWORD-waarde met de naam **AllowPFILEEncryption** de waarde van **0**.

3.  In de sleutel voor het nieuwe bestandstype (bijvoorbeeld **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), maak een nieuwe tekenreekswaarde met de naam **versleuteling** de waarde van **systeemeigen**.

Als gevolg van deze instellingen worden alle bestanden generieke beveiligd met uitzondering van bestanden met een bestand naam extensie, die standaard worden beschermd door de RMS-toepassing voor delen.

Deze drie stappen voor andere bestandstypen die u definiëren als uitzonderingen wilt omdat ze systeemeigen beveiliging ondersteunen en u niet wilt dat de generieke worden beveiligd door de RMS-toepassing voor delen.

U kunt vergelijkbare wijzigingen in het register voor andere scenario's maken door het wijzigen van de waarde van de **versleuteling** tekenreeks die de volgende waarden ondersteunt:

-   **Pfile**: Algemene beveiliging

-   **Systeemeigen**: Systeemeigen beveiliging

-   **Off**: Beveiliging blokkeren

## Zie ook
[Rights Management delen toepassing handleiding](../Topic/Rights_Management_sharing_application_user_guide.md)

