---
description: na
keywords: na
title: RMS Protection with Windows Server File Classification Infrastructure (FCI)
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
---
# RMS-beveiliging met Windows Server-bestand classificatie netwerkinfrastructuur (FCI)
In dit artikel voor instructies en een script naar de client Rights Management (RMS) met het hulpprogramma RMS bescherming configureren Bestandsserverbronbeheer en bestand classificatie infrastructuur (FCI) gebruiken.

Deze oplossingen kunt u automatisch alle bestanden in een map op een server met Windows Server beveiligen of automatisch beveiligen van bestanden die voldoen aan een specifieke criteria. Bijvoorbeeld, bestanden die zijn ingedeeld vertrouwelijke of gevoelige informatie bevat. Deze oplossing wordt [Azure Rights Management](../Topic/Azure_Rights_Management.md) (Azure RMS) de om bestanden te beschermen, zodat u deze technologie in uw organisatie geïmplementeerd moet hebben.

> [!NOTE]
> Hoewel Azure RMS bevat een [connector](https://technet.microsoft.com/library/dn375964.aspx) dat ondersteunt classificatie infrastructuur bestand, dat oplossing alleen native beveiliging ondersteunt, zoals Office-bestanden.
> 
> Ter ondersteuning van alle bestandstypen met bestand classificatie infrastructuur, moet u de Windows PowerShell **RMS beveiliging** module, zoals beschreven in dit artikel. De cmdlets RMS beveiliging, zoals de RMS sharing toepassing, ondersteuning voor algemene beveiliging, evenals een systeemeigen beveiliging, wat betekent dat alle bestanden kunnen worden beveiligd. Zie voor meer informatie over deze verschillende protection niveaus, de [Niveaus van beveiliging – systeemeigen en algemene](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) sectie de [Rights Management delen toepassing beheerdershandleiding](../Topic/Rights_Management_sharing_application_administrator_guide.md).

Volg de instructies zijn voor Windows Server 2012 R2 of Windows Server 2012. Als u andere ondersteunde versies van Windows wordt uitgevoerd, moet u mogelijk enkele van de stappen voor verschillen tussen uw versie van besturingssysteem en de beschreven in dit artikel worden aangepast.

## Vereisten voor Azure RMS beveiliging met Windows Server FCI
Vereisten voor deze instructies:

-   Op elke server waar u bestand Resource Manager wordt uitgevoerd met bestand classificatie infrastructuur:

    -   Bestandsserverbronbeheer als een van de functieservices voor de rol is geïnstalleerd.

    -   U hebt een lokale map waarin bestanden beveiligen met Rights Management geïdentificeerd. Bijvoorbeeld: C:\FileShare.

    -   U kunt het hulpprogramma voor RMS beveiliging, met inbegrip van de vereisten voor het hulpprogramma (zoals de RMS-client) en Azure RMS (zoals de principal serviceaccount) hebt geïnstalleerd. Zie voor meer informatie [RMS Protection Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx).

    -   Als u wijzigen van de standaard beveiligingsniveau RMS (native of algemene) voor specifieke bestandsextensies wilt, kunt u het register hebt bewerkt zoals beschreven in de [bestand API configuratie](https://msdn.microsoft.com/library/dn197834%28v=vs.85%29.aspx) pagina.

    -   U hebt een internetverbinding met de geconfigureerde instellingen als dat nodig is voor een proxy-server. Bijvoorbeeld: `netsh winhttp import proxy source=ie`

-   U kunt de aanvullende vereisten voor de implementatie van uw Azure Rights Management hebt geconfigureerd, zoals omschreven in [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx). Bijzonder, hebt u de volgende waarden verbinding maken met Azure RMS met behulp van een service principal:

    -   BposTenantId

    -   AppPrincipalId

    -   Symmetrische sleutel

-   U kunt uw lokale Active Directory-gebruikersaccounts zijn gesynchroniseerd met Azure Active Directory of Office 365, inclusief hun e-mailadres. Dit is vereist voor alle gebruikers die nodig hebt mogelijk voor toegang tot bestanden nadat ze worden beschermd door FCI en Azure RMS. Als u deze stap (bijvoorbeeld in een testomgeving) niet doet, kunnen gebruikers toegang hebben tot deze bestanden worden geblokkeerd. Als u meer informatie over de configuratie van dit account nodig hebt, raadpleegt u [Voorbereiden voor Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

-   U hebt aangegeven dat de Rights Management-sjabloon moet worden gebruikt, wordt de bestanden worden beveiligd. Zorg ervoor dat u de ID voor deze sjabloon met behulp van weet de [Get-RMSTemplate](https://msdn.microsoft.com/library/azure/mt433197.aspx) cmdlet.

## Instructies voor het configureren van Bestandsserverbronbeheer FCI voor Azure RMS beveiliging
Volg deze instructies voor het automatisch beveiligen van alle bestanden in een map met een Windows PowerShell-script als een aangepaste taak. Voer deze procedures in deze volgorde:

1.  Sla het Windows PowerShell-script

2.  Maak een classificatie-eigenschap voor RMS (Rights Management)

3.  Maak een classificatieregel (Classify voor RMS)

4.  De classificatie planning configureren

5.  Maak een aangepast bestand management taak (bestanden beveiligen met RMS)

6.  Testen van de configuratie van de door de regel en de taak handmatig uit te voeren

Alle bestanden in de geselecteerde map wordt ingedeeld met de aangepaste eigenschap van RMS aan het einde van deze instructies en wordt vervolgens deze bestanden worden beschermd door Rights Management. Voor een complexere configuratie die inschakeling enkele bestanden en andere niet beveiligt, kunt u vervolgens maken of een andere classificatie-eigenschap en een regel, gebruiken met een taak voor het beheer van bestand dat alleen de bestanden beschermt.

#### Sla het Windows PowerShell-script

1.  Vouw de [Windows PowerShell-Script voor Azure RMS beveiliging via Bestandsserverbronbeheer FCI](#BKMK_RMSProtection_Script) sectie in dit artikel en kopieer de inhoud. De inhoud van het script plakken en de naam van het bestand **RMS-Protect-FCI.ps1** op uw eigen computer.

2.  Bekijk het script en de volgende wijzigingen aanbrengen:

    -   Zoeken naar de volgende string en vervangen door uw eigen AppPrincipalId die u met de [Set RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) cmdlet verbinding maken met Azure RMS:

        ```
        <enter your AppPrincipalId here>
        ```
        Bijvoorbeeld, uitzien het script als volgt:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)] [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Zoeken naar de volgende string en vervangen door uw eigen symmetrische sleutel die u met de [Set RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) cmdlet verbinding maken met Azure RMS:

        ```
        <enter your key here>
        ```
        Bijvoorbeeld, uitzien het script als volgt:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Zoeken naar de volgende string en vervangen door uw eigen BposTenantId (tenant-ID) die u met de [Set RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) cmdlet verbinding maken met Azure RMS:

        ```
        <enter your BposTenantId here>
        ```
        Bijvoorbeeld, uitzien het script als volgt:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

    -   Als uw server Windows Server 2012 wordt uitgevoerd, moet u wellicht handmatig het laden van de module RMSProtection aan het begin van het script. De volgende opdracht (of een vergelijkbare als de map 'Programmabestanden' op het station C::

        ```
        Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"
        ```

3.  Meld u het script. Als u het script (veiliger) niet aanmeldt, moet u Windows PowerShell configureren op de servers die uit te voeren. Bijvoorbeeld uitvoeren van een Windows PowerShell-sessie met de **als Administrator uitvoeren** optie en typ: **Set-ExecutionPolicy Unrestricted**. Deze configuratie kan echter alle niet-ondertekende-scripts uitgevoerd (minder veilig).

    Zie voor meer informatie over het ondertekenen van Windows PowerShell-scripts [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) in de Documentatiebibliotheek PowerShell.

4.  Sla het bestand lokaal op elke bestandsserver die bestand Resource Manager wordt uitgevoerd met bestand classificatie infrastructuur. Bijvoorbeeld, het bestand opslaan in **C:\RMS-Protection**. Dit bestand beveiligen door NTFS-machtigingen zodat onbevoegde gebruikers kunnen niet worden gewijzigd.

U kunt nu starten Bestandsserverbronbeheer configureren.

#### Maak een classificatie-eigenschap voor RMS (Rights Management)

-   In Bestandsserverbronbeheer, classificatie Management, maakt u een nieuwe lokale eigenschap:

    -   **Name**: Type **RMS**

    -   **Beschrijving**:   Type **Rights Management protection**

    -   **Eigenschapstype**: Selecteer **Ja/Nee**

    -   **Value**: Selecteer **Ja**

We kunnen nu een classificatieregel maken die deze eigenschap wordt gebruikt.

#### Maak een classificatieregel (Classify voor RMS)

-   Maak een nieuwe classificatieregel:

    -   Op de **algemene** tabblad:

        -   **Name**: Type **Classify for RMS**

        -   **Ingeschakeld**: Houd de standaardwaarde is dat dit selectievakje is ingeschakeld.

        -   **Beschrijving**: Type **Classify all files in the &lt;folder name&gt; folder for Rights Management**.

            Vervang *&lt; naam &gt;* met de naam van de gekozen map. Bijvoorbeeld, **classificeren van alle bestanden in de map C:\FileShare voor Rights Management**

        -   **Scope**: Uw gekozen map toevoegen. Bijvoorbeeld, **C:\FileShare**.

            Schakel de selectievakjes uit.

    -   Op de **classificatie** tabblad:

    -   **Classificatie methode**: Selecteer **map classificatie**

    -   **Eigenschap** naam: Selecteer **RMS**

    -   De eigenschap **waarde**: Selecteer **Ja**

Hoewel u de classificatieregels handmatig voor lopende bewerkingen uitvoeren kunt wilt u deze regel wilt uitvoeren op basis van een schema zodat nieuwe bestanden worden ingedeeld op met de RMS-eigenschap.

#### De classificatie planning configureren

-   Op de **automatische classificatie** tabblad:

    -   **Vaste schema inschakelen**: Schakel dit selectievakje.

    -   Configureren van het schema voor alle classificatieregels om uit te voeren, waaronder onze nieuwe regel voor het delen van bestanden met de RMS-eigenschap.

    -   **Doorlopende classificatie voor nieuwe bestanden toestaan**: Schakel dit selectievakje in zodat nieuwe bestanden worden ingedeeld.

    -   Optioneel: Breng de wijzigingen die u wilt, zoals het configureren van opties voor rapporten en meldingen.

Nu u de classificatieconfiguratie van de hebt voltooid, kunt u bent een taak management om de RMS-beveiliging toepassen op de bestanden configureren.

#### Maak een aangepast bestand management taak (bestanden beveiligen met RMS)

-   In **Bestandsbeheertaken**, een nieuw bestand management-taak maken:

    -   Op de **algemene** tabblad:

        -   **Taaknaam**: Type **Protect files with RMS**

        -   Houd de **inschakelen** selectievakje geselecteerd.

        -   **Beschrijving**: Type **Protect files in &lt;folder name&gt; with Rights Management and a template by using a Windows PowerShell script.**

            Vervang *&lt; naam &gt;* met de naam van de gekozen map. Bijvoorbeeld, **bestanden in C:\FileShare met Rights Management en een sjabloon te beveiligen met een Windows PowerShell-script**

        -   **Scope**: Selecteer de map gekozen. Bijvoorbeeld, **C:\FileShare**.

            Schakel de selectievakjes uit.

    -   Op de **actie** tabblad:

        -   **Type**: Selecteer **aangepaste**

        -   **Uitvoerbare bestand**: Geef het volgende:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Als Windows niet op station is, wordt dit pad wijzigen of blader naar dit bestand.

        -   **Argument**: Geef de volgende, de levering van uw eigen waarden voor &lt; pad &gt; en &lt; sjabloon-ID &gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Als u het script gekopieerd naar C:\RMS-Protection en de sjabloon-ID die u van de vereiste items geïdentificeerd e6ee2481-26b9-45e5-b34a-f744eacd53b0, Geef bijvoorbeeld het volgende:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            In deze opdracht **[Source File Path]** en **[bron bestand eigenaar e]** zijn beide variabelen FCI specifieke typt u deze dus precies hetzelfde uitzien als ze in de opdracht hierboven worden weergegeven. De eerste regel wordt gebruikt door FCI automatisch het opgegeven bestand opgeven in de map en de tweede is voor FCI automatisch ophalen van het e-mailadres van de eigenaar met de naam van het bestand geïdentificeerd. Met deze opdracht wordt herhaald voor elk bestand in de map die in dit voorbeeld wordt elk bestand in de map C:\FileShare bovendien RMS als een classificatie-eigenschap van het bestand heeft.

            > [!NOTE]
            > De **-OwnerMail [Source File Owner Email]** parameter en waarde zorgt ervoor dat de oorspronkelijke eigenaar van het bestand de Rights Management-eigenaar van het bestand wordt verleend nadat deze is beveiligd. Dit zorgt ervoor dat de oorspronkelijke eigenaar van het bestand alle Rights Management rechten op hun eigen bestanden heeft. Wanneer bestanden worden gemaakt met een domeingebruiker, wordt het e-mailadres automatisch opgehaald uit Active Directory met behulp van de gebruikersnaam in de eigenschap eigenaar van het bestand. Hiervoor moet de bestandsserver in hetzelfde domein of vertrouwd domein als de gebruiker.
            > 
            > Indien mogelijk, kunt u de oorspronkelijke eigenaren toewijzen aan beveiligde documenten, om ervoor te zorgen dat deze gebruikers blijven volledige controle over de bestanden die ze gemaakt. Echter, als u de variabele [bron bestand eigenaar Email] als hierboven en een bestand heeft geen domeingebruiker gedefinieerd als de eigenaar (bijvoorbeeld een lokaal account is gebruikt voor het bestand te maken, zodat de eigenaar van het systeem worden weergegeven), het script mislukken.
            > 
            > Om de bestanden die geen domeingebruiker als de eigenaar, kunt u kopiëren en sla deze bestanden zelf als een gebruiker, zodat u de eigenaar voor alleen deze bestanden worden. Of als u machtigingen hebt, kunt u handmatig de eigenaar wijzigen.  Of u kunt ook een specifieke e-mailadres opgeven (zoals uw eigen of een groepsadres voor de IT-afdeling) in plaats van de variabele [bron bestand eigenaar Email], hetgeen betekent dat alle bestanden die u met dit script beschermen dit e-mailadres wordt gebruikt voor het definiëren van de nieuwe eigenaar.

    -   **Voert u de opdracht als**: Selecteer **Lokaal systeem**

    -   Op de **voorwaarde** tabblad:

        -   **Eigenschap**: Selecteer **RMS**

        -   **Operator**: Selecteer **gelijk**

        -   **Value**: Selecteer **Ja**

    -   Op de **schema** tabblad:

        -   **Run at**: Configureer uw voorkeur schema.

            Dat er voldoende tijd om het script te voltooien. Hoewel deze oplossing alle bestanden in de map beschermt, het script eenmaal voor elk bestand elke keer uitgevoerd. Hoewel dit langer duurt dan de beveiliging van alle bestanden tegelijkertijd, die het hulpprogramma RMS beveiliging ondersteunt, is deze configuratie per bestand voor FCI krachtigere. De beveiligde bestanden kunnen bijvoorbeeld verschillende eigenaars (behouden de oorspronkelijke eigenaar) als u de variabele [bron bestand eigenaar Email] gebruiken en deze actie per bestand is vereist als u de configuratie om te beveiligen inschakeling bestanden in plaats van alle bestanden in een map dit later wijzigen.

        -   **Doorlopend worden uitgevoerd op nieuwe bestanden**: Schakel dit selectievakje.

#### Testen van de configuratie van de door de regel en de taak handmatig uit te voeren

1.  De classificatieregel uitvoeren:

    1.  Klik op **Classificatieregels** &gt; **classificatie nu uitvoeren met alle regels**

    2.  Klik op **Wacht tot de classificatie voltooien**, en klik vervolgens op **OK**.

2.  Wacht totdat de **uitgevoerd classificatie** in het dialoogvenster te sluiten en vervolgens de resultaten bekijken in het rapport automatisch weergegeven. U ziet nu **1** voor de **eigenschappen** veld en het aantal bestanden in de map. Controleer met behulp van File Explorer en controle van de eigenschappen van bestanden in de map gekozen. Op de **classificatie** tabblad, zie je **RMS** als een eigenschapsnaam en **Ja** voor de **waarde**.

3.  Voer de taak voor het beheer van bestanden:

    1.  Klik op **Bestandsbeheertaken** &gt; **bestanden met RMS beveiligen** &gt; **bestand Management taak nu uitvoeren**

    2.  Klik op **Wacht totdat de taak te voltooien**, en klik vervolgens op **OK**.

4.  Wacht totdat de **taak voor beheer uitgevoerd** in het dialoogvenster te sluiten en vervolgens de resultaten bekijken in het rapport automatisch weergegeven. Ziet u het aantal bestanden in de gekozen map in de **bestanden** veld. Controleer of de bestanden in de map gekozen nu worden beveiligd door RMS. Bijvoorbeeld als uw gekozen map C:\FileShare, typt u de volgende in een Windows PowerShell-sessie en controleer of er zijn geen bestanden de status van hebben **UnProtected**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Tips voor probleemoplossing:
    > 
    > -   Als u ziet **0** in het rapport, in plaats van het aantal bestanden in de map dit geeft aan dat het script is niet uitgevoerd. Controleer eerst het script zelf door deze te laden in Windows PowerShell ISE valideren van de scriptinhoud en probeer uit te voeren om te zien als eventuele fouten worden weergegeven. Er zijn geen argumenten opgegeven, probeert het script verbinding kunnen maken en te verifiëren bij Azure RMS.
    > 
    >     -   Als het script wordt gemeld dat er kan geen verbinding worden gemaakt Azure RMS, controleert u de waarden die voor de service principal account, die u hebt opgegeven in het script wordt weergegeven.  Zie voor meer informatie over het maken van deze service principal-account de tweede voorwaarde in [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)
    >     -   Als het script wordt gemeld dat deze verbinding met Azure RMS maken kan en uw Azure regio buiten Noord-Amerika is, controleert u dat u het register correct voor deze configuratie hebt bewerkt. Er is een goede test voor deze Get-RMSTemplate rechtstreeks vanaf de Windows PowerShell uitvoeren op de server. Zie voor meer informatie over de wijzigingen in het register, de derde vereiste in [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx).
    > -   Als het script zelf in Windows PowerShell ISE zonder fouten wordt uitgevoerd, probeert u als volgt uitgevoerd vanuit een PowerShell-sessie door de bestandsnaam van een te beschermen en zonder de parameter - OwnerEmail:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File <full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Als het script uitgevoerd in deze Windows PowerShell-sessie, controleert u de gegevens voor **Executive** en **Argument** in het bestand management taakactie.  Als u hebt opgegeven **- OwnerEmail [bron bestand eigenaar e]**, verwijdert u deze parameter.
    > 
    >         Als de taak voor het beheer van bestanden, zonder werkt  **- OwnerEmail [bron bestand eigenaar e]**, Controleer of de niet-beveiligde bestanden weergegeven als de eigenaar van het bestand domeingebruiker plaats **SYSTEM**.  Gebruik hiervoor de **Security** tabblad voor eigenschappen van het bestand en klik vervolgens op **Geavanceerd**. De **eigenaar** waarde wordt weergegeven direct nadat het bestand **naam**. Controleer ook of de bestandsserver bevindt zich in hetzelfde domein of een vertrouwd domein bij het opzoeken van e-mailadres van de gebruiker uit Active Directory Domain Services.
    > -   Als u het juiste aantal bestanden in het rapport bekijken, maar de bestanden zijn niet beveiligd, probeert de bestanden handmatig te beveiligen met behulp van de [beveiligen RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx) cmdlet om te zien als eventuele fouten worden weergegeven.

Wanneer u hebt gecontroleerd dat deze taken worden uitgevoerd, kunt u bestand Resource Manager sluiten. Nieuwe bestanden worden automatisch beveiligd en alle bestanden opnieuw worden beveiligd wanneer de planning uitvoeren. Bestanden opnieuw te beveiligen, zorgt u ervoor dat alle wijzigingen aan de sjabloon worden toegepast op de bestanden.

### <a name="BKMK_RMSProtection_Script"></a>Windows PowerShell-Script voor Azure RMS beveiliging via Bestandsserverbronbeheer FCI
Deze sectie bevat script in het voorbeeld om te kopiëren en bewerken, zoals beschreven in de vorige sectie.

*&#42;&#42;Afwijzing&#42;&#42;: In dit voorbeeld van een script wordt niet ondersteund bij een ondersteuningsprogramma van Microsoft of de service. In dit voorbeeld van een script wordt vermeld in de huidige staat zonder garantie van welke aard dan ook.*

```
<# .SYNOPSIS Helper script to protect all file types with Azure RMS and FCI. .DESCRIPTION Protect files with Azure RMS and Windows Server FCI, using an RMS template ID. #> param( [Parameter(Mandatory = $false)] [ValidateScript({ If($_ -eq "") {$true} else { if (Test-Path -Path $_ -PathType Leaf) {$true} else {throw "Can't find file specified"} } })] [string]$File, [Parameter(Mandatory = $false)] [string]$TemplateID, [Parameter(Mandatory = $false)] [string]$OwnerMail, [Parameter(Mandatory = $false)] [string]$AppPrincipalId = "<enter your AppPrincipalId here>", [Parameter(Mandatory = $false)] [string]$SymmetricKey = "<enter your key here>", [Parameter(Mandatory = $false)] [string]$BposTenantId = "<enter your BposTenantId here>" ) # script information [String] $Script:Version = 'version 1.0' [String] $Script:Name = "RMS-Protect-FCI.ps1" #global working variables [switch] $Script:isScriptProcess = $False # Controls the script process. If false, the script gracefully stops running. #**Functions (general helper)*************************************** function Get-ScriptName(){ return $MyInvocation.ScriptName.Substring($MyInvocation.ScriptName.LastIndexOf('\') + 1, $MyInvocation.ScriptName.LastIndexOf('.') - $MyInvocation.ScriptName.LastIndexOf('\') - 1) } #**Functions (script specific)************************************** function Check-Module{ param ([String]$Module = $(Throw "Module name not specified")) [bool]$isResult = $False #try to load the module if (get-module -list -name $Module) { import-module $Module if (get-module -name $Module ) { $isResult = $True } else { $isResult = $False } } else { $isResult = $False } return $isResult } function Protect-File ($ffile, $ftemplateId, $fownermail) { [bool] $returnValue = $false try { If ($OwnerMail -eq $null -or $OwnerMail -eq "") { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId") } else { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId -OwnerEmail $fownermail $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId, set Owner: $fownermail") } } catch { Write-Host ( "ERROR" + "During protection of file: $ffile with Template: $ftemplateId") } return $returnValue } function Set-RMSConnection ($fappId, $fkey, $fbposId) { [bool] $returnValue = $false try { Set-RMSServerAuthentication -AppPrincipalId $fappId -Key $fkey -BposTenantId $fbposId Write-Host ("Information: " + "Connected to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") $returnValue = $true } catch { Write-Host ("ERROR" + "During connection to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") } return $returnValue } #**Main Script (Script)********************************************* Write-Host ("-== " + $Script:Name + " " + $Version + " ==-") $Script:isScriptProcess = $True # Validate Azure RMS connection by checking the module and then connection if ($Script:isScriptProcess) { if (Check-Module -Module RMSProtection){ $Script:isScriptProcess = $True } else { Write-Host ("The RMSProtection module is not loaded") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } if ($Script:isScriptProcess) { #Write-Host ("Try to connect to Azure RMS with AppId: $AppPrincipalId and BPOSID: $BposTenantId" ) if (Set-RMSConnection $AppPrincipalId $SymmetricKey $BposTenantId) { Write-Host ("Connected to Azure RMS") } else { Write-Host ("Couldn't connect to Azure RMS") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } #  Start working loop if ($Script:isScriptProcess) { if ( !(($File -eq $null) -or ($File -eq "")) ) { if (!(Protect-File -ffile $File -ftemplateId $TemplateID -fownermail $OwnerMail)) { $Script:isScriptProcess = $False } } } # Closing if (!$Script:isScriptProcess) { Write-Host "ERROR occurred during script process" -foregroundcolor "red" -backgroundcolor "black"} write-host ("-== " + $Script:Name + " " + $Version + "  ==-") if (!$Script:isScriptProcess) { exit(-1) } else {exit(0)}
```

## Wijzigen van de instructies inschakeling bestanden beveiligen
Wanneer u de voorgaande instructies werkt hebt, is het vervolgens heel eenvoudig wijzigen voor een meer geavanceerde configuratie. Bijvoorbeeld, bestanden beveiligen met behulp van hetzelfde script, maar alleen voor bestanden met persoonlijke identificatiegegevens en misschien Selecteer een sjabloon met meer beperkende rechten.

Gebruik hiervoor een van de ingebouwde classificatie-eigenschappen (bijvoorbeeld **persoonlijke informatie**) of maak uw eigen nieuwe eigenschap. Vervolgens maakt u een nieuwe regel die deze eigenschap wordt gebruikt. Bijvoorbeeld, kunt u de **inhoud classificatie**, kies de **persoonlijke informatie** met een waarde van de eigenschap **hoog**, en het patroon tekenreeks of een expressie waarmee het bestand moet worden geconfigureerd voor deze eigenschap configureren (zoals de tekenreeks "**Geboortedatum**").

Nu hoeft u een nieuw bestand management taak maken die gebruikt is hetzelfde script maar misschien met een andere sjabloon en configureer de voorwaarde voor de classificatie-eigenschap die u zojuist hebt geconfigureerd. Bijvoorbeeld, in plaats van de voorwaarde dat we eerder geconfigureerd (**RMS** eigenschap, **gelijk**, **Ja**) Selecteer de **persoonlijke informatie** eigenschap met de **Operator** waarde ingesteld op **gelijk** en de **waarde** van **hoog**.

