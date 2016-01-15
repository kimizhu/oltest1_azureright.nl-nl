---
description: na
keywords: na
title: Decommissioning and Deactivating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
---
# Buiten gebruik stellen en Azure Rights Management deactiveren
U hebt altijd indelen of uw organisatie inhoud met behulp van beveiligt [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS), en als u u niet meer wilt gebruiken voor deze oplossing informatie beveiliging besluit, hebt u de assurance dat u kan niet worden vergrendeld die eerder is beveiligd. Als u geen verdere toegang tot eerder beveiligde inhoud, moet u de service te deactiveren en kunt u uw abonnement voor Azure Rights Management is verlopen. Bijvoorbeeld, dit zou zijn afhankelijk van wanneer u klaar testen [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] voordat u deze in een productieomgeving implementeert.

Echter, als u hebt geïmplementeerd [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] in productie, zorg ervoor dat u hebt een kopie van uw Azure Rights Management tenant sleutel voordat u de service deactiveren en dit doen voordat uw abonnement is verlopen, omdat dit zorgt ervoor dat u toegang tot inhoud die is beveiligd door Azure Rights Management na te kan behouden de service is uitgeschakeld. Als u het Breng uw eigen sleutel oplossing (BYOK) waarin u genereren en beheren van uw eigen sleutel in een HSM gebruikt, hebt u al uw Azure Rights Management-tenant-sleutel. Maar als deze is beheerd door Microsoft (standaard), Zie de instructies voor het exporteren van de tenant-sleutel in [Bewerkingen voor uw Azure Rights Management Tenant-sleutel](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md) onderwerp.

> [!TIP]
> Zelfs nadat uw abonnement is verlopen, blijft uw Azure Rights Management-tenant beschikbaar voor inhoud gedurende een langere periode verbruikt. Echter niet langer mogelijk om uw tenant sleutel te exporteren.

Wanneer u uw Azure Rights Management tenant sleutel hebt, kunt u Rights Management op de lokale (AD RMS) implementeren en uw tenant sleutel importeren als een vertrouwde publicatieserver domein (vertrouwde Uitgiftedomein). U hebt de volgende opties voor het buiten gebruik stellen uw Azure Rights Management-implementatie:

|Als dit voor u geldt...|… Ga als volgt:|
|---------------------------|-------------------|
|U wilt dat alle gebruikers om door te gaan met Rights Management, maar een oplossing op locatie in plaats van met Azure RMS → gebruiken|Gebruik de [Set AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx) cmdlet bestaande om gebruikers te leiden naar uw on-premises implementatie wanneer ze na deze wijziging beveiligde inhoud gebruiken. Gebruikers worden automatisch de AD RMS-installatie gebruikt de beveiligde inhoud te gebruiken.<br /><br />Omleiding voor gebruikers inhoud te gebruiken die is beveiligd voordat deze wijziging van uw clients naar de on-premises implementatie met behulp van de **LicensingRedirection** registersleutel voor Office 2016 of Office 2013, zoals beschreven in de [detectie gedeelte](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) in de notities implementatie van RMS-client en de **LicenseServerRedirection** registersleutel voor Office 2010, zoals omschreven in [registerinstellingen van Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|U wilt stoppen met Rights Management-technologieën volledig →|Een aangewezen beheerder verlenen [super gebruikersrechten](https://technet.microsoft.com/library/mt147272.aspx) en geef deze persoon de [RMS Protection hulpprogramma](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />Deze beheerder kunt het hulpprogramma bulksgewijs-decoderen bestanden in mappen die zijn beveiligd door Azure Rights Management, zodat de bestanden herstellen wordt opgeheven en daarom zonder een Rights Management-technologie zoals Azure RMS of AD RMS kunnen worden gelezen. Dit hulpprogramma kan worden gebruikt met Azure RMS en AD RMS, zodat u de mogelijkheid hebt van het decoderen van bestanden voordat of nadat u Azure RMS of een combinatie deactiveren.|
|U bent niet kunnen identificeren van alle bestanden die zijn beveiligd door Azure RMS of alle gebruikers moeten worden automatisch gelezen beveiligde bestanden die zijn gemist →|Het register op alle clientcomputers implementeren met behulp van de **LicensingRedirection** registersleutel voor Office 2016 en Office 2013, zoals beschreven in de [detectie gedeelte](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) in de notities implementatie van RMS-client en de **LicenseServerRedirection** registersleutel voor Office 2010, zoals omschreven in [registerinstellingen van Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Daarnaast implementeert een andere via het register om te voorkomen dat gebruikers nieuwe bestanden beveiligen door in te stellen **DisableCreation** naar **1**, zoals omschreven in [registerinstellingen van Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|U wilt dat een gecontroleerde, handmatige recovery-service voor alle bestanden die gemiste → zijn|Verlenen aangewezen gebruikers in een groep data recovery [super gebruikersrechten](https://technet.microsoft.com/library/mt147272.aspx) en geeft u de [RMS Protection hulpprogramma](http://www.microsoft.com/en-us/download/details.aspx?id=47256) zodat ze kunnen bestanden op verzoek van standaardgebruikers opgeheven.<br /><br />Implementeer de registerinstelling om te voorkomen dat gebruikers nieuwe bestanden beveiligen door in te stellen op alle computers **DisableCreation** naar **1**, zoals omschreven in [registerinstellingen van Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
Zie voor meer informatie over de procedures in deze tabel de volgende bronnen:

-   Zie voor informatie over AD RMS en implementatie verwijst naar [Active Directory Rights Management Services-overzicht](https://technet.microsoft.com/library/hh831364.aspx).

-   Zie voor instructies voor het importeren van uw Azure RMS tenant sleutel als een vertrouwde Uitgiftedomein bestand [een vertrouwde publicatieserver domein toevoegen](https://technet.microsoft.com/library/cc771460.aspx).

-   Zie het installeren van de Windows PowerShell-module voor Azure RMS instellen van de migratie-URL [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Wanneer u gereed bent om te deactiveren de Azure RMS-service voor uw organisatie, gebruikt u de volgende instructies.

## Rights Management deactiveren
Een van de volgende procedures gebruiken om te deactiveren [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

> [!TIP]
> U kunt ook de Windows PowerShell-cmdlet [Disable Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), deactiveren [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Rights Management van het Office 365-beheercentrum deactiveren

1.  [Meld u aan bij Office 365 aan uw account werkitem of scholier](https://portal.office.com/) die een beheerder van uw Office 365-implementatie.

2.  Als het Office 365-beheercentrum niet automatisch wordt weergegeven, selecteert u de app launcher-pictogram in de linkerbovenhoek en kies **Admin**. De **Admin** tegel alleen zichtbaar voor Office 365-beheerders.

    > [!TIP]
    > Raadpleeg voor informatie over admin center [over de Office 365-beheercentrum - beheer Help](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  Vouw in het linkerdeelvenster **SERVICE-instellingen**.

4.  Klik op **Rights Management**.

5.  Op de **RIGHTS MANAGEMENT** pagina, klikt u op **beheren**.

6.  Op de **rights management** pagina, klikt u op **deactiveren**.

7.  Als u wordt gevraagd **wilt u Rights Management deactiveren?**, klikt u op **deactiveren**.

U ziet nu **Rights Management is niet geactiveerd** en de optie om te activeren.

#### Rights Management vanuit de Azure-Portal deactiveren

1.  Meld u aan bij de [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  Klik in het linkerdeelvenster op **ACTIVE DIRECTORY**.

3.  Uit de **active directory** pagina, klikt u op **RIGHTS MANAGEMENT**.

4.  Selecteer de map voor het beheren van voor [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], klikt u op **DEACTIVEREN**, en Bevestig uw actie.

De **RIGHTS MANAGEMENT-STATUS** moet nu weergeven **inactief** en de **DEACTIVEREN** optie wordt vervangen door **activeren**.

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

