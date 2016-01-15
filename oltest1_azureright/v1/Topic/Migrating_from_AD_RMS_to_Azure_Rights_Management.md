---
description: na
keywords: na
title: Migrating from AD RMS to Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
---
# Migratie van AD RMS naar Azure Rights Management
Gebruik de volgende reeks instructies voor het migreren van uw implementatie van Active Directory Rights Management Services (AD RMS) naar Azure Rights Management (Azure RMS). Na de migratie gebruikers nog steeds toegang tot documenten en e-mailberichten van uw organisatie beveiligd met AD RMS en nieuwe beveiligde inhoud Azure RMS wordt gebruikt.

Niet zeker of deze migratie AD RMS geschikt voor uw organisatie is?

-   Zie voor een inleiding tot Azure RMS, de zakelijke problemen die kunnen worden opgelost, ziet er als beheerders en gebruikers en hoe het werkt [Wat is Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

-   Zie voor een vergelijking van Azure RMS met AD RMS [Azure Rights Management en AD RMS vergelijken](../Topic/Comparing_Azure_Rights_Management_and_AD_RMS.md).

## Vereisten voor migratie AD RMS naar Azure RMS
Voordat u de migratie naar Azure RMS, zorg dat de volgende onderdelen zijn en dat u beperkingen begrijpt.

|Vereiste|Meer informatie|
|------------|-------------------|
|Een ondersteunde RMS-implementatie|Alle versies van de AD RMS van Windows Server 2008 via Windows Server 2012 R2 ondersteuning voor een migratie naar Azure RMS:<br /><br />-   Windows Server 2008 (x 86 of x 64)<br />-   Windows Server 2008 R2 (x 64)<br />-   Windows Server 2012 (x 64)<br />-   Windows Server 2012 R2 (x 64) **Note:** Als u Windows RMS op Windows Server 2003 uitvoert, worden deze versie van het besturingssysteem ondersteuning tijdens 2015. U kunt deze versie van RMS migreren naar Azure RMS, maar dit proces wordt alleen ondersteund als het besturingssysteem nog wordt ondersteund. Als tijdelijke oplossing kan u uw publicatie vertrouwd domein (vertrouwde Uitgiftedomein) importeren naar een versie van AD RMS die wordt ondersteund en importeer het vertrouwde Uitgiftedomein zonder de optie RMS 1.0 compatibiliteit opnieuw. Zie voor meer informatie over vertrouwde uitgiftedomeinen [Publishing domein vertrouwde](http://technet.microsoft.com/library/dd996639%28v=ws.10%29.aspx)<br />Alle geldige AD RMS topologieën worden ondersteund:<br /><br />-   Eén forest, één RMS-cluster<br />-   Forest één, meerdere licenties alleen-lezen RMS-clusters<br />-   Meerdere forests, meerdere RMS-clusters **Note:** Standaard migreren meerdere RMS-clusters naar een enkele Azure RMS-tenant. Als u verschillende RMS-tenants wilt, moet u deze behandelen als andere migraties. Een sleutel van een RMS-cluster kan niet worden geïmporteerd in meer dan een Azure RMS-tenant.|
|Alle vereisten voor het uitvoeren van Azure RMS, met inbegrip van een Azure RMS-tenant (niet geactiveerd)|Zie [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).<br /><br />Hoewel voordat u van AD RMS migreren kunt, u een Azure RMS-tenant hebben moet, raden wij aan dat u hebt de Rights Management-service voordat u de migratie niet geactiveerd. Het migratieproces bevat deze stap nadat u de sleutels en -sjablonen uit AD RMS geëxporteerd en geïmporteerd naar Azure RMS. Echter als Azure RMS is al geactiveerd, kunt u nog steeds migreren van AD RMS.|
|Voorbereiding voor Azure RMS:<br /><br />-   Directory-synchronisatie van uw on-premises directory op Azure Active Directory<br />-   Groepen e-mailadres in Azure Active Directory|Zie [Voorbereiden voor Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).|
|Als u de functionaliteit Information Rights Management (IRM) van Exchange Server (bijvoorbeeld transportregels en Outlook Web Access) of SharePoint-Server in combinatie met AD RMS gebruikt:<br /><br />-   Plan voor een korte periode als IRM niet meer beschikbaar op deze servers|U kunt doorgaan met IRM op deze servers met Azure RMS na de migratie. Een van de stappen van de migratie is echter tijdelijk uitschakelen de IRM-service, installeren en configureren van een connector, de servers configureren en IRM opnieuw inschakelen.<br /><br />Dit is het alleen onderbreking service tijdens de migratie.|
Beperkingen:

-   Hoewel het migratieproces uw server ondersteunt-licentieverlening certificaatsleutel (SLC) naar een hardware HSM (security module) voor Azure RMS migreren, ondersteunt Exchange Online niet momenteel deze configuratie. Als u volledige IRM-functionaliteit met Exchange Online wilt nadat u gemigreerd naar Azure RMS, uw Azure RMS tenant sleutel moet de [beheerd door Microsoft](http://technet.microsoft.com/library/dn440580.aspx). U kunt ook IRM met verminderde functionaliteit in Exchange Online uitvoeren als uw Azure RMS-tenant door u (BYOK) wordt beheerd. Zie voor meer informatie over het gebruik van Exchange Online met Azure RMS [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration) in deze instructies.

-   Als u software en -clients die worden niet ondersteund door Azure RMS hebt, kunt ze worden niet beveiligd of die wordt beveiligd door Azure RMS in beslag nemen. Controleer de toepassingen die worden ondersteund en clients sectie de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp.

-   Als u uw lokale sleutel in Azure RMS als importeren gearchiveerd (stelt u niet het vertrouwde Uitgiftedomein moet de actieve tijdens het importeren) en migreren van gebruikers in batches voor een gefaseerde migratie, die zojuist wordt beveiligd door de gemigreerde gebruikers niet toegankelijk voor gebruikers die op de AD RMS blijven. In dit scenario indien mogelijk, behouden de van korte migratietijd en migreren van gebruikers in batches logische zodanig dat als ze met elkaar samenwerken, ze samen worden gemigreerd.

    Deze beperking geldt niet wanneer u het vertrouwde Uitgiftedomein ingesteld op actief tijdens het importeren, omdat alle gebruikers wordt inhoud beveiligen met dezelfde sleutel. Deze configuratie wordt aangeraden omdat deze optie kunt u alle gebruikers afzonderlijk en in uw eigen tempo te migreren.

-   U kunt werken met externe partners (bijvoorbeeld met behulp van vertrouwde gebruikersdomeinen of federation), moet ook migreren naar Azure RMS ofwel tegelijkertijd als uw migratie of zo snel mogelijk daarna. Om door te gaan voor toegang tot inhoud dat uw organisatie beveiligd met behulp van de AD RMS stellen client configuratiewijzigingen die overeenkomen met de die u maakt en opgenomen in dit document.

    Vanwege de mogelijke configuratie variaties met uw partners mogelijk zijn exacte instructies voor deze aanpassingen buiten het bereik voor dit document. Voor hulp contact op met Microsoft klantenondersteuning (CSS).

## Stappen voor het migreren AD RMS naar Azure RMS

|Stap migratie|Meer informatie|
|-----------------|-------------------|
|**1. Azure RMS Management beheerprogramma's downloaden**|Zie voor instructies [Step 1: Download the Azure Rights Management Administration Tool](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step1Migration).|
|**2. Configuratiegegevens van de AD RMS exporteren en importeren in Azure RMS**|U de configuratiegegevens (sleutels, sjablonen, URL's) van AD RMS exporteren naar een XML-bestand en vervolgens dat bestand uploaden naar Azure RMS met behulp van de Import-AadrmTpd Windows PowerShell-cmdlet. Mogelijk aanvullende stappen nodig, afhankelijk van uw op configuratie van de AD RMS-sleutel:<br /><br />-   Software beschermd sleutel voor sleutel migratie software beschermd: Centraal beheerd op basis van een wachtwoord sleutels in AD RMS naar Microsoft wordt beheerd Azure RMS tenant sleutel. Dit is de meest eenvoudige migratiepad en zijn er geen extra stappen vereist.<br />-   HSM beveiligd sleutel voor sleutel migratie HSM beveiligd: Sleutels die zijn opgeslagen door een HSM voor AD RMS voor klant beheerde Azure RMS tenant sleutel (de "brengt uw eigen sleutel" of BYOK scenario). Hiervoor moet aanvullende maatregelen de sleutel van de lokale Thales HSM overbrengen naar de Azure RMS HSM.<br />-   Software beschermd sleutel voor sleutel migratie HSM beveiligd: Centraal beheerd op basis van een wachtwoord sleutels in AD RMS voor klant beheerde Azure RMS tenant sleutel (de "brengt uw eigen sleutel" of BYOK scenario). Hiervoor moet de configuratie van de meeste omdat u moet eerst de sleutel van uw software uitpakken en op een lokaal HSM importeren en voer de aanvullende stappen uit om de sleutel van de lokale Thales HSM overbrengen naar de Azure RMS HSM.<br /><br />Zie voor instructies [Step 2. Export configuration data from AD RMS and import it to Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step2Migration).|
|**3. De RMS-tenant activeren**|Indien mogelijk komen deze stap na tijdens het importeren en niet voor.<br /><br />Zie voor meer informatie en instructies [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).|
|**4. Geïmporteerde sjablonen configureren**|Wanneer u uw rechtenbeleidssjablonen importeren, wordt de status gearchiveerd. Als u wilt dat gebruikers kunnen zien en gebruiken, moet u de sjabloonstatus van de gepubliceerd in de Azure-beheerportal.<br /><br />Zie voor instructies [Step 4. Configure imported templates](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step4Migration).|
|**5. Clients voor gebruik van Azure RMS configureren**|Bestaande Windows-computers moeten opnieuw worden geconfigureerd voor gebruik van de Azure RMS-service in plaats van de AD RMS. Deze stap is van toepassing op computers in uw organisatie, en met computers in een andere organisatie als u werkt samen met deze treedt hebt terwijl u AD RMS zijn uitgevoerd.<br /><br />Als u hebt geïmplementeerd bovendien de [mobiel apparaat extensies](http://technet.microsoft.com/library/dn673574.aspx) ter ondersteuning van mobiele apparaten zoals iOS telefoons en iPads, Android telefoons en tablets, Windows phone en Mac-computers, moet u de SRV-records in DNS die deze clients gebruik AD RMS omgeleid.<br /><br />Zie voor instructies [Step 5. Reconfigure clients to use Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step5Migration).|
|**6. IRM-integratie met Exchange Online configureren**|Deze stap is vereist als u wilt gebruiken Exchange Online met Azure RMS.<br /><br />Zie voor instructies [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration).|
|**7. De RMS-connector implementeren**|Deze stap is vereist als u wilt gebruiken een van de volgende services op locatie met Azure RMS:<br /><br />-   Exchange Server (bijvoorbeeld transportregels en Outlook Web Access)<br />-   SharePoint-Server<br />-   Windows-Server die wordt uitgevoerd bestand classificatie infrastructuur<br /><br />Zie voor instructies [Step 7. Deploy the RMS connector](#BKMK_Step7Migration).|
|**8. Buiten gebruik stellen AD RMS**|Wanneer u hebt gecontroleerd of alle clients met behulp van Azure RMS en niet langer toegang tot de AD RMS-servers, kunt u uw implementatie AD RMS nemen.<br /><br />Zie voor instructies [Step 8. Decommission AD RMS](#BKMK_Step8Migration).|
|**9. Uw Azure RMS tenant sleutel opnieuw worden ingevoerd**|Deze stap is vereist als u niet in cryptografische modus 2 zijn uitgevoerd voordat de migratie en optioneel maar voor alle migraties aanbevolen naar het beschermen van de beveiliging van uw Azure RMS tenant-sleutel.<br /><br />Zie voor instructies [Step 9. Re-key your Azure RMS tenant key](#BKMK_Step9Migration).|

### <a name="BKMK_Step1Migration"></a>Stap 1: Download het beheerprogramma voor Azure Rights Management
Ga naar het Microsoft Download Center en download het [beheerprogramma voor Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721), die de Azure RMS-beheer-module voor Windows PowerShell bevat.

### <a name="BKMK_Step2Migration"></a>Stap 2. Configuratiegegevens van de AD RMS exporteren en importeren in Azure RMS
Deze stap is een proces twee delen:

1.  De configuratiegegevens van AD RMS door de publicatieserver vertrouwde domeinen (vertrouwde uitgiftedomeinen) exporteren naar een .xml-bestand exporteren. Dit proces is hetzelfde voor alle migraties.

2.  Importeer de configuratiegegevens in Azure RMS. Er zijn verschillende processen voor deze stap is afhankelijk van uw huidige configuratie van de AD RMS-implementatie en uw voorkeur topologie voor uw Azure RMS tenant-sleutel.

#### De configuratiegegevens van de AD RMS exporteren
Voer de volgende procedure op alle AD RMS-clusters voor alle vertrouwde publicatieserver domeinen die u hebt beveiligde inhoud voor uw organisatie. U hoeft niet uitvoeren op clusters licentieverlening alleen-lezen.

> [!NOTE]
> Als u van Windows Server 2003 Rights Management, in plaats van deze instructies gebruikmaakt, volgt u de procedure [SLC exporteren, Domeinen, vertrouwde Uitgiftedomein te RMS privésleutel](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) van de [migratie van Windows RMS naar AD RMS in een andere infrastructuur](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) onderwerp.

###### De configuratiegegevens (vertrouwde publicatieserver domeingegevens) exporteren

1.  Meld u aan de AD RMS-cluster als een gebruiker met AD RMS beheermachtigingen.

2.  In de AD RMS management console (**Active Directory Rights Management Services**), vouw de naam van het AD RMS-cluster uit, vouw **beleid vertrouwensrelatie**, en klik vervolgens op **Publishing domeinen vertrouwde**.

3.  Selecteer de publicatieserver vertrouwd domein in het resultatenvenster en klik vervolgens in het deelvenster Acties op **vertrouwde publicatieserver domein exporteren**.

4.  In de **exporteren vertrouwd publicatie domein** in het dialoogvenster:

    -   Klik op **OpslaanAls** en opslaan in het pad en de naam van uw keuze. Zorg ervoor dat u opgeeft **.xml** Als de bestandsextensie (dit wordt niet automatisch toegevoegd).

    -   Geef en een sterk wachtwoord bevestigen. Dit wachtwoord onthouden omdat u deze later, moet wanneer u de configuratiegegevens naar Azure RMS importeren.

    -   Schakel het selectievakje vertrouwd domein opslaan in RMS versie 1.0 niet.

Als u de vertrouwde publicatieserver domeinen hebt geëxporteerd, bent u klaar om de procedure voor het importeren van deze gegevens naar Azure RMS.

#### De configuratiegegevens naar Azure RMS importeren
De exacte procedures voor deze stap is afhankelijk van uw huidige configuratie van de AD RMS-implementatie en uw voorkeur topologie voor uw Azure RMS tenant-sleutel.

Uw huidige AD RMS-implementatie gebruikmaakt van een van de volgende configuraties voor uw server Licentiegever certificaat (SLC) sleutel:

-   Wachtwoordbeveiliging in de AD RMS-database. Dit is de standaardconfiguratie.

-   HSM beveiliging met behulp van een Thales hardware HSM (security module).

-   HSM beveiliging met behulp van een hardware HSM (security module) van een leverancier dan Thales.

-   Het wachtwoord is beveiligd met een externe-cryptografieprovider.

> [!NOTE]
> Zie voor meer informatie over het gebruik van hardware beveiligingsmodules met AD RMS [Using AD RMS met Hardware beveiligingsmodules](http://technet.microsoft.com/library/jj651024.aspx).

De twee Azure RMS tenant key-topologie opties zijn: Microsoft beheert de tenant-sleutel (**Microsoft beheerde**) of beheren van uw tenant sleutel (**klant beheerde**). Bij het beheren van uw eigen Azure RMS tenant sleutel wordt soms aangeduid met "brengt uw eigen sleutel" (BYOK) en een hardware HSM (security module) van Thales vereist. Zie voor meer informatie de [Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey) sectie de [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) onderwerp.

> [!IMPORTANT]
> Exchange Online is niet compatibel met Azure RMS BYOK.  Als u wilt gebruiken BYOK nadat de migratie en wilt gebruiken Exchange Online, moet u begrijpen hoe deze configuratie wordt beperkt IRM-functionaliteit voor Exchange Online. Lees de informatie in de [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) sectie de  [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) onderwerp bij het kiezen van de beste Azure RMS tenant key-topologie voor de migratie.

Gebruik de volgende tabel om te bepalen welke procedure moet worden gebruikt voor de migratie. Combinaties die niet zijn opgenomen, worden niet ondersteund.

|Huidige AD RMS-implementatie|Gekozen Azure RMS tenant key-topologie|Migratie-instructies|
|--------------------------------|------------------------------------------|------------------------|
|Wachtwoordbeveiliging in de AD RMS-database|Microsoft beheerd|Zie de **Software beschermd sleutel software beschermd sleutel migratie naar** procedure na deze tabel.<br /><br />Dit is de meest eenvoudige migratiepad en alleen is vereist dat u uw configuratiegegevens naar Azure RMS overbrengen.|
|HSM beveiliging met behulp van een Thales nShield hardware security module HSM)|Klant beheerde (BYOK)|Zie de **HSM beveiligd sleutel van belangrijke migratie HSM beveiligd** procedure na deze tabel.<br /><br />Dit is de toolset BYOK en twee reeks stappen voor het overzetten van de sleutel van uw lokale HSM naar de Azure RMS HSM's en vervolgens de configuratiegegevens kan overdragen naar Azure RMS vereist.|
|Wachtwoordbeveiliging in de AD RMS-database|Klant beheerde (BYOK)|Zie de **Software beschermd sleutel van belangrijke migratie HSM beveiligd** procedure na deze tabel.<br /><br />Hiervoor moet de toolset BYOK en drie sets stappen voor het eerste uw softwaresleutel en importeer het kan een HSM lokale vervolgens de sleutel van de lokale HSM overbrengen naar de Azure RMS HSM's en ten slotte uw configuratiegegevens kan overdragen naar Azure RMS te halen.|
|HSM beveiliging met behulp van een hardware HSM (security module) van een leverancier dan Thales|Klant beheerde (BYOK)|Neem contact op met de leverancier voor u HSM voor instructies hoe u uw sleutel van deze HSM overbrengen naar een Thales nShield Hardware Security Module HSM (). Volg de instructies voor het **HSM beveiligd sleutel van belangrijke migratie HSM beveiligd** procedure na deze tabel.|
|Wachtwoord is beveiligd met behulp van een externe-cryptografieprovider|Klant beheerde (BYOK)|Neem contact op met de leverancier voor u cryptografieprovider voor instructies uw sleutel overbrengen naar een Thales nShield hardware HSM (security module). Volg de instructies voor het **HSM beveiligd sleutel van belangrijke migratie HSM beveiligd** procedure na deze tabel.|
Voordat u deze procedures, zorg dat u toegang hebt tot de XML-bestanden die u eerder hebt gemaakt bij het exporteren van de vertrouwde domeinen publiceren. Deze kunnen bijvoorbeeld worden opgeslagen in een USB-stick die u van de AD RMS-server naar het werkstation met de internetverbinding verplaatst.

> [!NOTE]
> Echter slaat u deze bestanden, gebruik beveiliging aanbevolen procedures ze worden beveiligd omdat deze gegevens de persoonlijke sleutel bevat.

##### Software beschermd sleutel van software beschermd sleutel migratie
Gebruik deze procedure om te importeren in de AD RMS-configuratie Azure RMS resulteren in uw Azure RMS tenant-sleutel die wordt beheerd door Microsoft.

###### De configuratiegegevens naar Azure RMS importeren

1.  Op een werkstation internetverbinding download en installeer de Windows PowerShell-module voor Azure RMS (minimale versie 2.1.0.0), inclusief de [importeren AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) cmdlet.

    > [!TIP]
    > Als u eerder hebt gedownload en geïnstalleerd van de module, controleert u het versienummer dat door het uitvoeren van: `(Get-Module aadrm -ListAvailable).Version`

    Zie voor installatie-instructies [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

2.  Start van Windows PowerShell met de **Als administrator uitvoeren** optie en gebruiken de [Connect AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) cmdlet verbinding maken met de Azure RMS-service:

    ```
    Connect-AadrmService
    ```
    Wanneer u wordt gevraagd, typt u uw [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] tenant beheerdersreferenties (meestal, gebruikt u een account dat een globale beheerder voor Azure Active Directory of Office 365).

3.  Gebruik de [importeren AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) cmdlet voor het uploaden van de eerste publishing vertrouwd domein (.xml)-bestand geëxporteerd. Als er meer dan een .xml-bestand omdat er meerdere domeinen van vertrouwde publiceren, kiest u het bestand waarin de geëxporteerde vertrouwd domein publicatie die u gebruiken in Azure RMS wilt te beschermen inhoud na de migratie. De volgende opdracht gebruiken:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Bijvoorbeeld: **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    Als u wordt gevraagd, voer het wachtwoord dat u eerder hebt opgegeven en bevestigen dat u wilt deze actie uit te voeren.

4.  Herhaal stap 3 voor elke resterende .xml-bestand dat u hebt gemaakt door het exporteren van de vertrouwde domeinen publiceren als de opdracht is voltooid. Maar ingesteld voor deze bestanden **-Active** naar **false** bij het uitvoeren van de opdracht importeren. Bijvoorbeeld: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Gebruik de [verbinding verbreken AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) cmdlet loskoppelen van de Azure RMS-service:

    ```
    Disconnect-AadrmService
    ```

U kunt nu gaat u naar [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Sleutel HSM beveiligd sleutel migreren HSM beveiligd
Er is een twee delen procedure voor het importeren van uw HSM sleutel en AD RMS-configuratie naar Azure RMS, resulteren in uw Azure RMS tenant-sleutel die wordt beheerd door u (BYOK).

U moet eerst de sleutel HSM pakket is gereed om te dragen naar Azure RMS en vervolgens importeren met de configuratiegegevens.

###### Deel 1: De sleutel HSM pakket zodat deze overzetten naar Azure RMS gereed is

1.  Volg de stappen in de [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) sectie van de [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md), met de procedure **genereren en overdracht uw tenant sleutel – via het Internet** met de volgende uitzonderingen:

    -   Voer de stappen voor het niet **uw tenant sleutel genereren**, omdat er al het equivalent van uw AD RMS-implementatie. U moet de sleutel gebruikt door de AD RMS-server van de installatie Thales identificeren en deze sleutel gebruikt tijdens de migratie. Versleutelde sleutel bestanden worden gewoonlijk aangeduid Thales **key_(keyAppName)_(keyIdentifier)** lokaal op de server.

    -   Voer de stappen voor het niet **uw tenant sleutel overbrengen naar Azure RMS**, waarvoor de opdracht Add-AadrmKey worden gebruikt.  U wordt in plaats daarvan de voorbereide HSM sleutel overbrengen wanneer u het geëxporteerde publicatie vertrouwd domein, met de opdracht Import AadrmTpd uploaden.

2.  Op het werkstation internetverbinding in Windows PowerShell-sessie opnieuw verbinding maken met de Azure RMS-service.

Nu dat u hebt uw sleutel HSM voorbereid voor Azure RMS, bent u klaar om uw HSM sleutelbestand en configuratiegegevens voor de AD RMS te importeren.

###### Deel 2: De HSM sleutel en configuratie-gegevens importeren in Azure RMS

1.  Nog steeds op het werkstation Internet verbinding en in de Windows PowerShell-sessie de eerste geëxporteerde vertrouwde publicatieserver domein (.xml) bestand uploaden. Als er meer dan een .xml-bestand omdat er meerdere domeinen van vertrouwde publiceren, kiest u het bestand waarin de geëxporteerde vertrouwd domein publiceren die met de HSM-sleutel die u gebruiken in Azure RMS overeenkomt wilt te beschermen inhoud na de migratie. De volgende opdracht gebruiken:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Bijvoorbeeld: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Als u wordt gevraagd, voer het wachtwoord dat u eerder hebt opgegeven en bevestigen dat u wilt deze actie uit te voeren.

2.  Herhaal stap 1 voor elke resterende .xml-bestand dat u hebt gemaakt door het exporteren van de vertrouwde domeinen publiceren als de opdracht is voltooid. Maar ingesteld voor deze bestanden **-Active** naar **false** bij het uitvoeren van de opdracht importeren.  Bijvoorbeeld: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Gebruik de [verbinding verbreken AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet loskoppelen van de Azure RMS-service:

    ```
    Disconnect-AadrmService
    ```

U kunt nu gaat u naar [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Software beschermd sleutel van belangrijke migratie HSM beveiligd
Er is een procedure drie onderdeel om te importeren in de AD RMS-configuratie Azure RMS resulteren in uw Azure RMS tenant-sleutel die wordt beheerd door u (BYOK).

U moet eerst uw server Licentiegever certificaat (SLC) sleutel ophalen uit de configuratiegegevens voor de sleutel overbrengen naar een lokale Thales HSM, en vervolgens pakket en uw sleutel HSM overbrengen naar Azure RMS en vervolgens de configuratiegegevens voor importeren.

###### Deel 1: Uw SLC ophalen uit de configuratiegegevens en de sleutel naar uw lokale HSM importeren

1.  Gebruik de volgende stappen uit in de [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) sectie van de [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) onderwerp:

    -   **Genereren en overdracht uw tenant sleutel – via het Internet**: **Uw internetverbinding werkstation voorbereiden**

    -   **Genereren en overdracht uw tenant sleutel – via het Internet**: **Uw verbroken werkstation voorbereiden**

    Volg de stappen voor het genereren van de sleutel tenant niet omdat er al het equivalent in het geëxporteerde configuratiebestand gegevens (.xml). In plaats daarvan dient u een opdracht voor deze sleutel ophalen uit het bestand en importeren in uw lokale HSM uitgevoerd.

2.  Voer de volgende opdracht op het werkstation verbroken:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Bijvoorbeeld voor Noord-Amerika: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    Aanvullende informatie:

    -   De parameter ImportRmsCentrallyManagedKey geeft aan dat de bewerking voor het importeren van de sleutel SLC.

    -   Als u het wachtwoord in de opdracht niet opgeeft, wordt u gevraagd te geven.

    -   De parameter KeyIdentifier is voor een sleutel beschrijvende naam voor de naam sleutelbestand te maken. U moet alleen kleine letters ASCII-tekens gebruiken.

    -   De parameter ExchangeKeyPackage geeft u een pakket specifieke key exchange sleutel (KEK) met de naam begint met BYOK-KEK - pak-.

    -   De parameter NewSecurityWorldPackage geeft u een specifieke world beveiligingspakket waarvan de naam begint met BYOK-SecurityWorld - pak-.

    Met deze opdracht resulteert in het volgende:

    -   Bestand met een HSM sleutel: %NFAST_KMDATA%\local\key_mscapi_ &lt; KeyID &gt;

    -   RMS-configuratie-gegevensbestand met het SLC verwijderd: %NFAST_KMDATA%\local\no_key_tpd_ &lt; KeyID &gt; .xml

3.  Als er meer dan een RMS-configuratie-gegevensbestanden, Herhaal stap 2 voor de rest van deze bestanden.

Nu dat uw SLC is uitgepakt zodat deze een sleutel op basis van een HSM, bent u klaar om te pakken en overzetten naar Azure RMS.

###### Deel 2: Pakket en de sleutel HSM overbrengen naar Azure RMS

1.  Gebruik de volgende stappen uit de [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) sectie van de [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md):

    -   **Genereren en overdracht uw tenant sleutel – via het Internet**: **De sleutel van de tenant voor overdracht voorbereiden**

    -   **Genereren en overdracht uw tenant sleutel – via het Internet**: **De sleutel tenant overbrengen naar Azure RMS**

Nu dat u uw sleutel HSM naar Azure RMS overgebracht hebt, bent u klaar om te importeren van uw AD RMS-configuratiegegevens, die alleen een verwijzing naar de zojuist overgebrachte tenant sleutel bevat.

###### Deel 3: De configuratiegegevens naar Azure RMS importeren

1.  Nog steeds op het werkstation met de internetverbinding en in de Windows PowerShell-sessie kopiëren via de RMS-configuratiebestanden met het SLC verwijderd (van de verbonden werkstation, %NFAST_KMDATA%\local\no_key_tpd_ &lt; KeyID &gt; .xml)

2.  Het eerste bestand uploaden. Als er meer dan een .xml-bestand omdat er meerdere domeinen van vertrouwde publiceren, kiest u het bestand waarin de geëxporteerde vertrouwd domein publiceren die met de HSM-sleutel die u gebruiken in Azure RMS overeenkomt wilt te beschermen inhoud na de migratie. De volgende opdracht gebruiken:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Bijvoorbeeld: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    Als u wordt gevraagd, voer het wachtwoord dat u eerder hebt opgegeven en bevestigen dat u wilt deze actie uit te voeren.

3.  Herhaal stap 2 voor elke resterende .xml-bestand dat u hebt gemaakt door het exporteren van de vertrouwde domeinen publiceren als de opdracht is voltooid. Maar ingesteld voor deze bestanden **-Active** naar **false** bij het uitvoeren van de opdracht importeren. Bijvoorbeeld: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Gebruik de [verbinding verbreken AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet loskoppelen van de Azure RMS-service:

    ```
    Disconnect-AadrmService
    ```

U kunt nu gaat u naar [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

### <a name="BKMK_Step3Migration"></a>Stap 3. De RMS-tenant activeren
Instructies voor deze stap vallen volledig de [Azure Rights Management activeren](../Topic/Activating_Azure_Rights_Management.md) onderwerp.

> [!TIP]
> Als u een Office 365-abonnement hebt, kunt u Azure RMS van het Office 365-beheercentrum of de Azure-beheerportal activeren. U wordt aangeraden de Azure-beheerportal te gebruiken, wordt met deze beheerportal kunt u de volgende stap.

**Wat gebeurt er als uw Azure RMS-tenant is al geactiveerd?** Als de Azure RMS-service is al geactiveerd voor uw organisatie, gebruikers mogelijk al gebruikt Azure RMS te beschermen inhoud met een sleutel automatisch gegenereerde tenant (en de standaardsjablonen) in plaats van uw bestaande sleutels (en sjablonen) van AD RMS. Dit is waarschijnlijk niet op computers die goed beheerde op het intranet zijn gebeuren omdat deze wordt automatisch geconfigureerd voor de AD RMS-infrastructuur. Maar dit probleem kan optreden op computers in werkgroepen of computers die minder vaak verbinding met het intranet maken. Helaas is het ook moeilijk om deze computers te identificeren daarom aangeraden om dat de service kan niet worden activeren voordat u de configuratiegegevens uit AD RMS importeren is.

Als uw Azure RMS-tenant is al geactiveerd en kunt u deze computers herkennen, zorg ervoor dat het script CleanUpRMS_RUN_Elevated.cmd uit te voeren op deze computers, zoals beschreven in stap 5. Dit script wordt uitgevoerd zorgt ervoor dat ze te initialiseren van de gebruikersomgeving, zodat ze de bijgewerkte tenant sleutel en het geïmporteerde sjablonen downloaden.

### <a name="BKMK_Step4Migration"></a>Stap 4. Geïmporteerde sjablonen configureren
Omdat de sjablonen die u hebt geïmporteerd, de standaardconfiguratie van hebben **gearchiveerde**, moet u deze status om te worden **gepubliceerd** als u wilt dat gebruikers kunnen deze sjablonen gebruiken met Azure RMS.

Als uw sjablonen in AD RMS gebruikt bovendien de **ANYONE** groep deze groep wordt automatisch verwijderd wanneer u de sjablonen naar Azure RMS importeren, moet u handmatig dezelfde rechten op de geïmporteerde sjablonen of gebruikers en de equivalente groep toevoegen. De naam van de equivalente groep voor Azure RMS **AllStaff-&lt;tenant_GUID&gt;@&lt;tenant_name&gt;.onmicrosoft.com&gt;**. Bijvoorbeeld, deze groep kan eruitzien als de volgende onderwerpen voor Contoso, Ltd: **AllStaff-9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a@contoso.onmicrosoft.com**.

U kunt zien van uw organisatie van de groep automatisch gemaakt als u een van de standaard rechten beleidssjablonen in de Azure-portal kopiëren en vervolgens identificeert de **gebruikersnaam** op de **rechten** pagina. Echter moet u kunt de Azure-portal niet gebruiken voor het toevoegen van deze groep en in plaats daarvan een van de volgende Azure RMS PowerShell-opties:

-   Gebruik de [exporteren AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) cmdlet exporteren van de sjabloon naar een. CSV-bestand dat u kunt bewerken als de groep "AllStaff" en toegangsrechten voor de rechten en bestaande groepen wilt toevoegen en vervolgens gebruiken de [importeren AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) voor het importeren van deze wijziging van de cmdlet weer in Azure RMS.

-   Gebruik de [Nieuw AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) PowerShell-cmdlet aan de groep "AllStaff" en rechten definiëren als een object van de definitie van rechten en voer deze opdracht opnieuw voor het definiëren van de rechten voor de sjabloon en bestaande groepen. Deze rechten definitie objecten vervolgens toevoegen aan de sjablonen met behulp van de [toevoegen AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) cmdlet.

> [!NOTE]
> Deze "AllStaff" gelijkwaardige groep is niet precies hetzelfde als de groep ANYONE in AD RMS:  De groep "AllStaff" bevat alle gebruikers in uw Azure tenant dat de groep Iedereen bevat alle geverifieerde gebruikers die buiten uw organisatie kunnen worden.
> 
> Door dit verschil tussen de twee groepen moet u mogelijk ook externe gebruikers naast de groep "AllStaff" toevoegen. Externe e-mailadressen voor groepen worden momenteel niet ondersteund.

Sjablonen die u hebt geïmporteerd uit AD RMS bekijken en werken net als aangepaste sjablonen die u in de Azure-beheerportal maken kunt. Zie het wijzigen van de geïmporteerde sjablonen worden gepubliceerd zodat gebruikers kunnen zien en toepassingen selecteren of andere wijzigingen worden aangebracht in de sjablonen [Aangepaste sjablonen configureren voor Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

> [!TIP]
> Voor een consistente ervaring voor gebruikers tijdens de migratie Breng geen wijzigingen aan de geïmporteerde sjablonen dan deze twee wijzigingen; en niet de twee standaard-sjablonen die worden geleverd met Azure RMS publiceren of nieuwe sjablonen maken op dit moment. In plaats daarvan wacht totdat de migratie voltooid is en u hebt buiten gebruik gesteld de AD RMS-servers.

### <a name="BKMK_Step5Migration"></a>Stap 5. Clients voor gebruik van Azure RMS configureren
Voor Windows-clients:

1.  [Downloaden van de migratiescripts](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Deze scripts opnieuw instellen van de configuratie op Windows-computers zodat ze de Azure RMS-service in plaats van AD RMS gebruiken.

2.  Volg de instructies in het script omleiding (Redirect_OnPrem.cmd) voor het wijzigen van het script om te verwijzen naar uw nieuwe Azure RMS-tenant.

3.  Op de Windows-computers deze scripts worden uitgevoerd met verhoogde bevoegdheden in de context van de gebruiker.

Voor mobiele apparaten clients en Mac-computers:

-   Verwijder de DNS SRV-records die u hebt gemaakt wanneer u geïmplementeerd de [AD RMS mobiel apparaat extensie](http://technet.microsoft.com/library/dn673574.aspx).

#### Wijzigingen van de migratiescripts
Deze sectie worden de wijzigingen die de migratiescripts. U kunt deze informatie gebruiken alleen ter informatie of voor het oplossen van problemen of als u liever dat deze wijzigingen zelf.

CleanUpRMS_RUN_Elevated.cmd:

-   De inhoud van de mappen %userprofile%\AppData\Local\Microsoft\DRM en %userprofile%\AppData\Local\Microsoft\MSIPC, met inbegrip van alle submappen en bestanden met lange bestandsnamen verwijderen.

-   Verwijder de inhoud van de volgende registersleutels:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   De volgende registerwaarden verwijderen:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   De volgende registerwaarden maken voor elke URL die is opgegeven als een parameter in elk van de volgende locaties:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Elk item heeft de waarde REG_SZ **https://OldRMSserverURL/_wmcs/licensing** met de gegevens in de volgende notatie: **https://&lt;YourTenantURL&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt; YourTenantURL &gt;* heeft de volgende indeling: **{GUID} .rms. [regio].aadrm.com**.
    > 
    > Bijvoorbeeld:  5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Vindt u deze waarde door aan te duiden de **RightsManagementServiceId** waarde tijdens het uitvoeren van de [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet voor Azure RMS.

### <a name="BKMK_Step6Migration"></a>Stap 6. IRM-integratie voor Exchange Online configureren
Als u hebt uw TDP eerder geïmporteerd uit AD RMS naar Exchange Online, moet u deze TDP om te voorkomen dat conflicterende sjablonen en het beleid nadat u hebt gemigreerd naar Azure RMS verwijderen. Gebruik hiervoor de [verwijderen RMSTrustedPublishingDomain](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) cmdlet van Exchange Online.

Als u een Azure RMS sleutel topologie van tenant **Microsoft beheerde**:

-   Zie de [Exchange Online: IRM-configuratie](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline) sectie de [Toepassingen voor Azure Rights Management configureren](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) onderwerp. Deze sectie bevat standaard opdrachten om uit te voeren die u maakt verbinding met de Exchange Online-service, invoer van de sleutel tenant uit Azure RMS en schakelt IRM-functionaliteit voor Exchange Online. Nadat u deze stappen hebt voltooid, hebt u volledige RMS-functionaliteit met Exchange Online.

Als u een Azure RMS sleutel topologie van tenant **(BYOK) klant beheerde**:

-   U wordt hebben RMS-functionaliteit minder met Exchange Online, zoals beschreven in de [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) sectie de [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) onderwerp.

### <a name="BKMK_Step7Migration"></a>Stap 7. De RMS-connector implementeren
Als u de functionaliteit Information Rights Management (IRM) van Exchange Server of SharePoint Server met AD RMS hebt gebruikt, moet u IRM uitschakelen op deze servers en AD RMS-configuratie verwijderen. Vervolgens de implementatie van de connector RMS (Rights Management), die als een communicatie-interface (relay) tussen de lokale servers en Azure RMS fungeert.

Ten slotte voor deze stap moet als u meerdere vertrouwde uitgiftedomeinen hebt geïmporteerd in Azure RMS die zijn gebruikt voor het beveiligen van e-mailberichten, u handmatig bewerken via het register op de Exchange Server-computers alle URL's van vertrouwde uitgiftedomeinen omleiden naar de RMS-connector.

> [!NOTE]
> Voordat u begint, controleert u de ondersteunde versies van de lokale-servers die de RMS-connector in "On-premises-servers die ondersteuning van Azure RMS ondersteunt de [Toepassingen die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) sectie van de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp.

##### Schakel de IRM op Exchange-Servers en AD RMS-configuratie verwijderen

1.  Op elke Exchange-server naar de volgende map en verwijder de vermeldingen in de map: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Gebruik van een van de Exchange-servers en de Exchange [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) cmdlet eerst uit te schakelen IRM-functies voor berichten die worden verzonden naar interne geadresseerden:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Vervolgens gebruikt u de cmdlet dezelfde IRM-functies voor berichten die worden verzonden naar externe geadresseerden uitschakelen:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Vervolgens gebruikt u de cmdlet dezelfde IRM in Microsoft Office Outlook Web-App en in Microsoft Exchange ActiveSync uitschakelen:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Ten slotte, gebruikt u de cmdlet dezelfde certificaten die in cache wissen:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Op elke Exchange-Server nu IIS opnieuw instellen, bijvoorbeeld door een opdrachtprompt als administrator uitvoeren en typ **iisreset**.

##### Schakel de IRM op SharePoint-Servers en AD RMS-configuratie verwijderen

1.  Zorg ervoor dat er geen documenten uitgecheckt uit bibliotheken RMS wordt beveiligd. Als er, worden ze ontoegankelijk aan het einde van deze procedure.

2.  Op de SharePoint Centraal beheer-website, in de **Snelstarten** sectie, klikt u op **Security**.

3.  Op de **Security** pagina in de **beleid** sectie, klikt u op **information rights management configureren**.

4.  Op de **Information Rights Management** pagina in de **Information Rights Management** sectie **IRM niet gebruiken op deze server**, klikt u vervolgens op **OK**.

5.  Verwijder de inhoud van de map \ProgramData\Microsoft\MSIPC\Server\ op elk van de SharePoint Server-computers,*&lt; SID van de account met SharePoint Server &gt;*.

##### De RMS-connector installeren en configureren

-   Volg de instructies in de [Implementatie van de Connector van de Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) onderwerp.

##### Voor alleen Exchange en meerdere vertrouwde uitgiftedomeinen: Het register bewerken

-   Op elke Exchange-Server moet u handmatig de volgende registersleutels toevoegen voor elke extra vertrouwde Uitgiftedomein die u hebt geïmporteerd, om de vertrouwde Uitgiftedomein URL's omleiden naar de RMS-connector. Deze registervermeldingen specifiek zijn voor migratie en niet door de server configuration tool voor Microsoft RMS-connector worden toegevoegd.

    Wanneer u deze wijzigingen in het register, gebruikt u de volgende instructies:

    -   Vervang *ConnectorFQDN* met de naam die u hebt gedefinieerd in de DNS voor de connector. Bijvoorbeeld, **rmsconnector.contoso.com**.

    -   Gebruik het HTTP- of HTTPS-voorvoegsel voor de URL van de connector, afhankelijk van of u de connector voor gebruik van HTTP- of HTTPS om te communiceren met uw lokale servers hebt geconfigureerd.

    **Voor Exchange 2013:**

    |Register-pad|Type|Waarde|Gegevens|
    |----------------|--------|----------|------------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS Intranet Licensing-URL &gt; _wmcs/licensing|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van de Exchange-server de RMS-connector:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS Extranet Licensing-URL &gt; _wmcs/licensing|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van de Exchange-server de RMS-connector:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorFQDN&gt;/_wmcs/licensing|
    **Voor Exchange Server 2010:**

    |Register-pad|Type|Waarde|Gegevens|
    |----------------|--------|----------|------------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS Intranet Licensing-URL &gt; _wmcs/licensing|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van de Exchange-server de RMS-connector:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS Extranet Licensing-URL &gt; _wmcs/licensing|Een van de volgende, afhankelijk van of u via HTTP- of HTTPS van de Exchange-server de RMS-connector:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|

Nadat u deze procedures hebt voltooid, worden lees de **Vervolgstappen** sectie de [Implementatie van de Connector van de Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) onderwerp.

### <a name="BKMK_Step8Migration"></a>Stap 8. Buiten gebruik stellen AD RMS
Optioneel: Verwijder de Service Connection Point (SCP) uit Active Directory om te voorkomen dat computers detecteren van de lokale Rights Management-infrastructuur. Dit is optioneel vanwege de omleiding die u in het register (bijvoorbeeld door het uitvoeren van het script migratie) is geconfigureerd. Als u wilt verwijderen van de Service Connection Point, gebruiken AD SCP registreren van de [Rights Management Services Administration Toolkit](http://www.microsoft.com/download/details.aspx?id=1479).

De AD RMS-servers voor activiteit, bijvoorbeeld bewaken door te controleren de [aanvragen in het rapport System Health](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), de [serviceaanvraag tabel](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) of [controle van de gebruikerstoegang tot beveiligde inhoud](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Wanneer u hebt gecontroleerd dat clients met RMS niet langer communiceren met deze servers en dat door clients worden gebracht via Azure RMS, kunt u de AD RMS-serverrol van deze server verwijderen. Als u aangewezen servers gebruikt, kunt u de stap uit eerste afsluiten van de servers voor een bepaalde tijd om te controleren of er zijn geen gerapporteerde problemen die mogelijk opnieuw starten van deze servers om ervoor te zorgen service continuïteit terwijl u onderzoekt waarom clients geen gebruikmaakt van Azure RMS liever.

U kunt na het buiten gebruik stellen uw AD RMS-servers, maak van de gelegenheid uw sjablonen in de Azure-beheerportal bekijken en te consolideren zodat gebruikers minder kiezen hebben uit, of zelfs toevoegen nieuwe sjablonen opnieuw configureren. Dit is ook een geschikte tijd voor het publiceren van de standaardsjablonen zijn. Zie voor meer informatie [Aangepaste sjablonen configureren voor Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

### <a name="BKMK_Step9Migration"></a>Stap 9. Uw Azure RMS tenant sleutel opnieuw worden ingevoerd
Deze stap is vereist wanneer migratie voltooid als uw AD RMS-implementatie RMS cryptografische modus 1, is omdat er een nieuwe tenant-sleutel die gebruikmaakt van RMS cryptografische modus 2 opnieuw instellen van sleutels worden gemaakt. Alleen tijdens de migratie wordt Azure RMS met met cryptografische modus 1 ondersteund.

Deze stap is optioneel maar aanbevolen wanneer migratie voltooid is zelfs als u in RMS cryptografische modus 2 uitvoert, omdat hiermee voor het veiligstellen van uw Azure RMS tenant-sleutel van potentiële beveiligingsrisico's aan de AD RMS-sleutel. Wanneer u uw Azure RMS tenant sleutel (ook wel bekend als "lopende uw sleutel") opnieuw worden ingevoerd, een nieuwe sleutel wordt gemaakt en de oorspronkelijke sleutel wordt gearchiveerd. Echter omdat het verplaatsen van een sleutel naar een ander gebeurt niet onmiddellijk maar in enkele weken niet wachten totdat u vermoedt dat aan de oorspronkelijke sleutel, maar uw tenant sleutel voor RMS opnieuw sleutel als de migratie voltooid is.

Opnieuw te worden getypt uw Azure RMS tenant sleutel:

-   Als uw RMS-tenant-sleutel wordt beheerd door Microsoft: Bel Microsoft klantenondersteuning (CSS) en laten zien dat u de RMS-tenantbeheerder zijn.

-   Als uw RMS-tenant-sleutel wordt beheerd door u (BYOK): Herhaal de procedure BYOK te genereren en een nieuwe sleutel maken via het Internet of persoonlijk.

Zie voor meer informatie over het beheren van de sleutel voor RMS tenant [Bewerkingen voor uw Azure Rights Management Tenant-sleutel](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

