---
description: na
keywords: na
title: Operations for Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
---
# Bewerkingen voor uw Azure Rights Management Tenant-sleutel
Afhankelijk van uw tenant key-topologie (Microsoft beheerde of klant beheerd) hebben verschillende niveaus van controle en verantwoordelijkheid voor uw tenant Microsoft Azure Rights Management (Azure RMS) sleutel nadat deze is geïmplementeerd.

Wanneer u uw eigen sleutel tenant beheren, is dit vaak genoemd om als uw eigen sleutel (BYOK). Zie voor meer informatie over dit scenario en hoe u kunt kiezen tussen de twee tenant sleutel topologieën [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

De volgende tabel bevat welke bewerkingen die u doen kunt, afhankelijk van de topologie die u hebt gekozen voor uw Azure RMS tenant-sleutel.

|Lifecycle-bewerking|Microsoft wordt beheerd (standaard)|Klant beheerde (BYOK)|
|-----------------------|---------------------------------------|-------------------------|
|De sleutel tenant intrekken|Geen (automatisch)|Geen (automatisch)|
|Uw tenant sleutel opnieuw worden ingevoerd|Ja|Ja|
|Back-up en herstellen van de tenant-sleutel|Nee|Ja|
|Het exporteren van de tenant-sleutel|Ja|Nee|
|Reageren op een inbreuk op|Ja|Ja|
Nadat u hebt aangegeven welke topologie die u hebt geïmplementeerd, kunt u een van de volgende secties voor meer informatie over deze bewerkingen voor uw Azure RMS tenant sleutel gebruiken.

## <a name="BKMK_MSManagedOperations"></a>Microsoft beheerd: Tenant sleutel lifecycle bewerkingen
Als Microsoft beheert de tenant-sleutel voor Azure Rights Management (standaard), gebruikt u de volgende secties voor meer informatie over de lifecycle-bewerkingen die relevant voor deze topologie zijn:

-   [De sleutel tenant intrekken](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRevoke)

-   [Uw tenant sleutel opnieuw worden ingevoerd](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey)

-   [Back-up en herstellen van de tenant-sleutel](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBackup)

-   [Het exporteren van de tenant-sleutel](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSExport)

-   [Reageren op een inbreuk op](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBreach)

### <a name="BKMK_MSRevoke"></a>De sleutel tenant intrekken
Wanneer u zich van Azure RMS afmeldt, Azure RMS stopt met uw tenant sleutel en van u is geen actie vereist.

### <a name="BKMK_MSRekey"></a>Uw tenant sleutel opnieuw worden ingevoerd
Opnieuw instellen van sleutels wordt ook wel uw sleutel implementeren. Niet opnieuw sleutel uw tenant sleutel tenzij het wordt echt nodig. Oudere clients, zoals Office 2010, zijn niet ontworpen om belangrijke wijzigingen correct verwerken. In dit geval moet u de RMS-status op computers met Groepsbeleid of een equivalente mechanisme wissen. Er zijn echter enkele legitieme gebeurtenissen zodat u uw tenant sleutel opnieuw worden ingevoerd. Bijvoorbeeld:

-   Uw bedrijf is gesplitst in twee of meer bedrijven. Wanneer u uw tenant sleutel opnieuw worden ingevoerd, het nieuwe bedrijf geen toegang tot nieuwe inhoud die uw werknemers publiceren. Toegang te krijgen tot de oude inhoud als ze beschikken over een kopie van de oude tenant-sleutel.

-   U denkt dat het originele exemplaar van de tenant-sleutel (kopiëren beschikt) is ingebroken.

U kunt uw tenant sleutel opnieuw sleutel door het aanroepen van Microsoft klantenondersteuning (CSS) en waaruit u de tenantbeheerder zijn.

Wanneer u uw tenant sleutel opnieuw worden ingevoerd, worden nieuwe inhoud wordt beveiligd door met de nieuwe sleutel van de tenant. Dit komt voor in een gefaseerde wijze, zodat voor een bepaalde tijd een aantal nieuwe inhoud blijven met de oude tenant sleutel worden beveiligd. Beveiligde inhoud blijft eerder beveiligde voor uw oude tenant-sleutel. Azure RMS behoudt de oude tenant-sleutel voor dit scenario, zodat deze licenties voor oude inhoud kan verlenen.

### <a name="BKMK_MSBackup"></a>Back-up en herstellen van de tenant-sleutel
Microsoft is verantwoordelijk voor het back-ups van uw tenant sleutel en er is geen actie vereist van u.

### <a name="BKMK_MSExport"></a>Het exporteren van de tenant-sleutel
U kunt uw Azure RMS-configuratie en tenant-sleutel exporteren door de instructies in deze drie stappen:

##### Stap 1: Exporteren starten

-   U doet dit door contact op met Microsoft klantondersteuning Service (CSS). U moet als bewijs dat u beheerder bent voor uw Azure RMS-tenant.

##### Stap 2: Wacht tot de verificatie

-   Microsoft wordt gecontroleerd of uw aanvraag voor de RMS-tenant loslaat geldig is. Dit kan tot 3 weken duren.

##### Stap 3: Sleutel instructies van CSS ontvangen

-   Microsoft klantenondersteuning (CSS) stuurt u uw Azure RMS-configuratie en tenant sleutel als versleutelde in een wachtwoord zijn beveiligd bestand met de extensie .tpd. U doet dit door stuurt CSS eerst u (als de persoon die de uitvoer gestart) een hulpmiddel per e-mail. U moet het hulpprogramma uitvoeren vanaf een opdrachtprompt als volgt:

    ```
    AadrmTpd.exe -createkey
    ```
    Dit genereert een combinatie van de RSA-sleutel en de openbare en persoonlijke halve als bestanden opgeslagen in de huidige map. Voorbeeld: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** en **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Reageren op het e-mailbericht van CSS, bijvoegen van het bestand met een naam die wordt gestart met **PublicKey**. CSS vervolgens stuurt u een bestand vertrouwde Uitgiftedomein als een .xml-bestand is versleuteld met de RSA-sleutel. Dit bestand kopiëren naar dezelfde map als u het hulpprogramma AadrmTpd oorspronkelijk hebt uitgevoerd en het hulpprogramma opnieuw uitvoeren met behulp van het bestand dat met begint **PrivateKey** en het bestand van CSS. Bijvoorbeeld:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    De uitvoer van deze opdracht moet twee bestanden: Een bevat het leesbare wachtwoord voor het wachtwoord zijn beveiligd vertrouwde Uitgiftedomein en de andere is het vertrouwde wachtwoord Uitgiftedomein zelf. Voor kruisverwijzingen doeleinden, hebben beide dezelfde GUID als de openbare en persoonlijke sleutels bestanden uit tijdens het uitvoeren van de opdracht AadrmTpd.exe - createkey:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Back-up maken van deze bestanden en slaan deze veilig om ervoor te zorgen dat u kunt doorgaan met het ontsleutelen van inhoud die is beveiligd met de sleutel voor deze tenant. Als u naar AD RMS migreren wilt, kunt u bovendien dit vertrouwde Uitgiftedomein-bestand importeren (het bestand dat met begint **ExportedTDP**) met de AD RMS-server.

##### Stap 4: Lopende: De sleutel tenant beveiligen

-   Nadat u uw tenant sleutel ontvangen, moet deze goed beveiligde omdat als iemand toegang tot deze ontvangt, kunnen ze alle documenten die worden beschermd met behulp van deze sleutel gedecodeerd.

    Als de reden voor het exporteren van de tenant-sleutel is omdat u niet meer wilt gebruiken Azure RMS wordt aangeraden, moet u nu uw RMS-tenant deactiveren. Geen vertraging hierdoor nadat u uw tenant sleutel hebt ontvangen, omdat deze voorzorgsmaatregelen de gevolgen minimaliseren kunnen als uw tenant sleutel wordt gebruikt door iemand die geen moet hebben. Zie voor instructies [Buiten gebruik stellen en Azure Rights Management deactiveren](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

### <a name="BKMK_MSBreach"></a>Reageren op een inbreuk op
Er is geen beveiligingssysteem zo sterk is voltooid zonder een antwoord inbreuk proces. Uw tenant sleutel mogelijk ingebroken of gestolen. Zelfs als het ook goed beveiligd, mogelijk door beveiligingslekken in de huidige generatie HSM technologie of huidige sleutellengte en algoritmen worden gevonden.

Microsoft heeft een speciale team om te reageren op beveiligingsincidenten in de producten en services. Als er een geloofwaardige rapport van een incident is, wordt dit team voert het bereik, de hoofdoorzaak en tijdelijke oplossingen voor problemen te onderzoeken. Als dit incident heeft betrekking op de activa, klikt u vervolgens stuurt Microsoft uw Azure RMS tenant beheerders e-mailbericht met het adres dat u hebt opgegeven als u geabonneerd.

Als er een inbreuk, de aanbevolen actie die u of Microsoft kunt is afhankelijk van het bereik van de schending; Microsoft werkt samen met u via deze procedure. De volgende tabel ziet enkele situaties en de waarschijnlijke reactie Hoewel de exacte reactie afhankelijk van de informatie die wordt weergegeven tijdens het onderzoek.

|Beschrijving van incident|Waarschijnlijke antwoord|
|-----------------------------|----------------------------|
|Er is meer in uw tenant-sleutel.|Uw tenant sleutel opnieuw worden ingevoerd. Zie de [Uw tenant sleutel opnieuw worden ingevoerd](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey) in dit onderwerp.|
|Een niet-geautoriseerde persoon of malware hebt u recht op uw tenant sleutel, maar heeft niet de sleutel zelf lekken.|Opnieuw instellen van uw tenant sleutel sleutels niet hier helpt en hoofdoorzaak analyse vereist. Als een proces of software-fout verantwoordelijk voor het niet-geautoriseerde persoon om toegang te krijgen is, moet deze situatie worden opgelost.|
|Door een beveiligingslek in de RSA-algoritme, of sleutellengte of gewelddadige aanvallen ontdekt worden rekenkundig uitvoerbaar is.|Microsoft moet de Azure RMS ter ondersteuning van nieuwe algoritmes en sleutellengte die robuuste bijwerken en alle klanten voor het vernieuwen van de sleutels tenant geven.|

## <a name="BKMK_BYOKManagedOperations"></a>Klant beheerd: Tenant sleutel lifecycle bewerkingen
Als u uw tenant sleutel voor Azure Rights Management beheren (het Breng uw eigen sleutel of BYOK, scenario), gebruikt u de volgende secties voor meer informatie over de lifecycle-bewerkingen die relevant voor deze topologie zijn:

-   [De sleutel tenant intrekken](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRevoke)

-   [Uw tenant sleutel opnieuw worden ingevoerd](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey)

-   [Back-up en herstellen van de tenant-sleutel](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBackup)

-   [Het exporteren van de tenant-sleutel](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKExport)

-   [Reageren op een inbreuk op](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBreach)

### <a name="BKMK_BYOKRevoke"></a>De sleutel tenant intrekken
Wanneer u zich van Azure RMS afmeldt, Azure RMS stopt met uw tenant sleutel en van u is geen actie vereist.

### <a name="BKMK_BYOKRekey"></a>Uw tenant sleutel opnieuw worden ingevoerd
Opnieuw instellen van sleutels wordt ook wel uw sleutel implementeren. Niet opnieuw sleutel uw tenant sleutel tenzij het wordt echt nodig. Oudere clients, zoals Office 2010, zijn niet ontworpen om belangrijke wijzigingen correct verwerken. In dit geval moet u de RMS-status op computers met Groepsbeleid of een equivalente mechanisme wissen. Er zijn echter enkele legitieme gebeurtenissen zodat u uw tenant sleutel opnieuw worden ingevoerd. Bijvoorbeeld:

-   Uw bedrijf is gesplitst in twee of meer bedrijven. Wanneer u uw tenant sleutel opnieuw worden ingevoerd, het nieuwe bedrijf geen toegang tot nieuwe inhoud die uw werknemers publiceren. Toegang te krijgen tot de oude inhoud als ze beschikken over een kopie van de oude tenant-sleutel.

-   U denkt dat het originele exemplaar van de tenant-sleutel (kopiëren beschikt) is ingebroken.

Wanneer u uw tenant sleutel opnieuw worden ingevoerd, worden nieuwe inhoud wordt beveiligd door met de nieuwe sleutel van de tenant. Dit komt voor in een gefaseerde wijze, zodat voor een bepaalde tijd een aantal nieuwe inhoud blijven met de oude tenant sleutel worden beveiligd. Beveiligde inhoud blijft eerder beveiligde voor uw oude tenant-sleutel. Azure RMS behoudt de oude tenant-sleutel voor dit scenario, zodat deze licenties voor oude inhoud kan verlenen.

Naar de sleutel opnieuw uw tenant sleutel, genereren en maak een nieuwe sleutel via het Internet of persoonlijk, met behulp van de procedures in de [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) gedeelte van de [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) onderwerp.

### <a name="BKMK_BYOKBackup"></a>Back-up en herstellen van de tenant-sleutel
U bent verantwoordelijk voor het back-ups van uw tenant-sleutel. Als u uw tenant-sleutel in een HSM Thales gegenereerd, om een back-up van de sleutel alleen back-up van het bestand Getokeniseerd sleutel, de hele wereld-bestand en de beheerder kaarten.

Als u uw sleutel overgebracht door de procedures in de [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) gedeelte van de [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) Azure RMS-onderwerp te beschermen tegen fouten van Azure RMS knooppunten bestand sleutel Getokeniseerd blijft bewaard. Echter beschouwen dit moet een volledige back-up. Bijvoorbeeld als u een kopie platte tekst van de sleutel moet worden gebruikt buiten een HSM Thales ooit nodig hebt, is Azure RMS niet mogelijk om op te halen voor u omdat er slechts een niet-herstelbare kopie.

### <a name="BKMK_BYOKExport"></a>Het exporteren van de tenant-sleutel
Als u BYOK gebruikt, kunt u uw tenant sleutel niet exporteren van Azure RMS. Het exemplaar in Azure RMS is niet meer worden hersteld. Als u verwijderen van deze sleutel wilt, zodat deze niet meer kan worden gebruikt, moet u contact op met Microsoft klantondersteuning Service (CSS).

### <a name="BKMK_BYOKBreach"></a>Reageren op een inbreuk op
Er is geen beveiligingssysteem zo sterk is voltooid zonder een antwoord inbreuk proces. Uw tenant sleutel mogelijk ingebroken of gestolen. Zelfs als het ook goed beveiligd, mogelijk door beveiligingslekken in de huidige generatie HSM technologie of huidige sleutellengte en algoritmen worden gevonden.

Microsoft heeft een speciale team om te reageren op beveiligingsincidenten in de producten en services. Als er een geloofwaardige rapport van een incident is, wordt dit team voert het bereik, de hoofdoorzaak en tijdelijke oplossingen voor problemen te onderzoeken. Als dit incident heeft betrekking op de activa, klikt u vervolgens stuurt Microsoft uw Azure RMS tenant beheerders e-mailbericht met het adres dat u hebt opgegeven als u geabonneerd.

Als er een inbreuk, de aanbevolen actie die u of Microsoft kunt is afhankelijk van het bereik van de schending; Microsoft werkt samen met u via deze procedure. De volgende tabel ziet enkele situaties en de waarschijnlijke reactie Hoewel de exacte reactie afhankelijk van de informatie die wordt weergegeven tijdens het onderzoek.

|Beschrijving van incident|Waarschijnlijke antwoord|
|-----------------------------|----------------------------|
|Er is meer in uw tenant-sleutel.|Uw tenant sleutel opnieuw worden ingevoerd. Zie de [Uw tenant sleutel opnieuw worden ingevoerd](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey) in dit onderwerp.|
|Een niet-geautoriseerde persoon of malware hebt u recht op uw tenant sleutel, maar heeft niet de sleutel zelf lekken.|Opnieuw instellen van uw tenant sleutel sleutels niet hier helpt en hoofdoorzaak analyse vereist. Als een proces of software-fout verantwoordelijk voor het niet-geautoriseerde persoon om toegang te krijgen is, moet deze situatie worden opgelost.|
|Door een beveiligingslek in de huidige generatie HSM technologie gedetecteerd.|Microsoft moet de HSM's bijwerken. Als er ervan overtuigd dat het beveiligingslek sleutels blootgesteld, geven Microsoft alle klanten voor het vernieuwen van de tenant-sleutels.|
|Door een beveiligingslek in de RSA-algoritme, of sleutellengte of gewelddadige aanvallen ontdekt worden rekenkundig uitvoerbaar is.|Microsoft moet de Azure RMS ter ondersteuning van nieuwe algoritmes en sleutellengte die robuuste bijwerken en alle klanten voor het vernieuwen van de sleutels tenant geven.|

## Zie ook
[Met behulp van Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

