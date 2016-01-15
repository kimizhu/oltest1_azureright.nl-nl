---
description: na
keywords: na
title: Activating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
---
# Azure Rights Management activeren
Wanneer u activeren [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS), uw organisatie kunt beginnen met het belangrijk om gegevens te beveiligen met behulp van toepassingen en services die deze oplossing informatie beveiliging ondersteunt. Beheerders kunnen ook beheren en beveiligde bestanden en e-mailberichten die eigenaar is van uw organisatie bewaken. U moet inschakelen [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] voordat u kunt de functies van information rights management (IRM) in Office SharePoint en Exchange gebruiken en alle gevoelige of vertrouwelijke bestanden worden beveiligd.

Als u weten over Azure Rights Management wilt voordat u de service activeert, bijvoorbeeld welke bedrijfsproblemen het is opgelost, soms standaardgebruik en hoe het werkt, Zie [Wat is Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

> [!IMPORTANT]
> Voordat u activeert [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], zorg ervoor dat uw organisatie heeft een serviceplan [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] services. Als dat niet het geval is, worden niet Azure RMS activeren.
> 
> Zie voor meer informatie de [Cloud-abonnementen die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) sectie de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp.

Nadat u Azure RMS hebt geactiveerd, alle gebruikers in uw organisatie kan de beveiliging van gegevens op hun bestanden toepassen kunnen en alle gebruikers kunnen openen (verbruiken)-bestanden die zijn beveiligd door Azure RMS. Echter als u liever, kunt u beperken die beveiliging van gegevens met onboarding besturingselementen voor een gefaseerde implementatie kunt toepassen. Zie voor meer informatie de [Onboarding besturingselementen voor een gefaseerde implementatie configureren](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) in dit onderwerp.

## Wanneer u Rights Management
Een van de volgende procedures gebruiken om te activeren [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

> [!TIP]
> U kunt ook de Windows PowerShell-cmdlet [Enable Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx), om te activeren [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Rights Management van het Office 365-beheercentrum activeren

1.  Nadat u zich hebt aangemeld voor een Office 365-plan met Rights Management [Meld u aan bij Office 365 aan uw account werkitem of scholier](https://portal.office.com/) die een beheerder van uw Office 365-implementatie.

2.  Als het Office 365-beheercentrum niet automatisch wordt weergegeven, selecteert u de app launcher-pictogram in de linkerbovenhoek en kies **Admin**. De **Admin** tegel alleen zichtbaar voor Office 365-beheerders.

    > [!TIP]
    > Raadpleeg voor informatie over admin center [over de Office 365-beheercentrum - beheer Help](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  Vouw in het linkerdeelvenster **SERVICE-instellingen**.

4.  Klik op **Rights Management**.

    > [!NOTE]
    > Als u deze optie niet ziet, kan het zijn dat Rights Management kan niet worden ondersteund door de service plan of product versie of er nog niet is bijgewerkt om Rights Management te ondersteunen.
    > 
    > Gebruik de informatie in de [Cloud-abonnementen die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) sectie de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp om te bevestigen dat ondersteuning. Als uw versie van plan of product service wordt ondersteund, maar niet de optie Rights Management wordt weergegeven, is het mogelijk omdat de service is nog niet bijgewerkt. Voor hulp bij dit probleem, sturen u een e-mailbericht naar [askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS).

5.  Op de **RIGHTS MANAGEMENT** pagina, klikt u op **beheren**.

6.  Op de **rights management** pagina, klikt u op **activeren**.

7.  Als u wordt gevraagd **wilt u Rights Management activeren?**, klikt u op **activeren**.

U ziet nu **Rights management is geactiveerd** en de optie om te deactiveren.

#### Rights Management van de Azure-beheerportal activeren

1.  Nadat u zich hebt aangemeld voor uw account Azure [Meld u aan bij de Azure-beheerportal](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  Klik in het linkerdeelvenster op **ACTIVE DIRECTORY**.

3.  Uit de **active directory** pagina, klikt u op **RIGHTS MANAGEMENT**.

4.  Selecteer de map voor het beheren van voor [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], klikt u op **activeren**, en Bevestig uw actie.

    > [!NOTE]
    > Als er een activeringsfout, kan het zijn dat geen ondersteuning voor uw versie van plan of product service [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].
    > 
    > Gebruik de informatie in de [Cloud-abonnementen die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) sectie de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp om te bevestigen dat RMS-ondersteuning. Voor hulp bij dit probleem, sturen u een e-mailbericht naar [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).

De **RIGHTS MANAGEMENT-STATUS** moet nu weergeven **Active** en de **activeren** optie wordt vervangen door **DEACTIVEREN**.

### Rights Management statuswaarden en beschrijvingen in de Azure-beheerportal
Behalve de **Active** status die aangeeft dat de service Rights Management is ingeschakeld en kan worden gebruikt, u ook ziet mogelijk **inactief**, **niet beschikbaar**, of **niet-gemachtigd**.

|Waarde van de status|Beschrijving|
|------------------------|----------------|
|**Actieve**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] is ingeschakeld en klaar voor gebruik.|
|**Niet-actief**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] is uitgeschakeld en moet worden geactiveerd voordat uw organisatie kunt bestanden beveiligen.|
|**Niet beschikbaar**|De [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service is niet actief. Probeer het later opnieuw.|
|**Niet-geautoriseerde**|U bent niet gemachtigd om weer te geven de status van de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service. Bijvoorbeeld, uw account is vergrendeld of u bent niet de hoofdbeheerder voor de geselecteerde tenant.|

## <a name="BKMK_OnboardingControls"></a>Onboarding besturingselementen voor een gefaseerde implementatie configureren
Als u niet dat alle gebruikers kunnen onmiddellijk bestanden beveiligen wilt door Azure RMS, kunt u de gebruiker onboarding besturingselementen configureren met behulp van de [Set AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) Windows PowerShell-opdracht. U kunt met deze opdracht uitvoeren voordat of nadat u Azure RMS activeren.

> [!IMPORTANT]
> Om deze opdracht gebruikt, moet u er ten minste versie **2.1.0.0** van de [Azure RMS Windows PowerShell-module](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Als u wilt controleren van de versie die u hebt geïnstalleerd, uitvoeren: **(Get-Module aadrm –ListAvailable).Version**

Als u alleen beheerders in de groep "IT-afdeling" (met een object-ID van fbb99ded-32a0-45f1-b038-38b519009503) in eerste instantie wilt kunnen om inhoud voor testdoeleinden te beschermen, bijvoorbeeld de volgende opdracht gebruiken:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Houd er rekening mee dat deze configuratieoptie, moet u een groep; u kunt geen afzonderlijke gebruikers opgeven.

Of als u wilt om ervoor te zorgen dat alleen gebruikers die correct in licentie gegeven zijn voor het gebruik van Azure RMS inhoud kunnen beveiligen:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
Als u deze besturingselementen onboarding, beveiligde inhoud die is beveiligd door de subset van gebruikers kunnen altijd gebruikmaken van alle gebruikers in de organisatie, maar ze niet meer informatie over beveiliging zelf toepassen van clienttoepassingen. Bijvoorbeeld zien niet ze in hun Office-clients de standaardsjablonen die automatisch worden gepubliceerd als Azure RMS wordt geactiveerd of aangepaste sjablonen die u kunt configureren.  Servertoepassingen, zoals Exchange, kunnen hun eigen besturingselementen per gebruiker voor de RMS-integratie met hetzelfde resultaat bereiken implementeren.

## Volgende stappen
Nu dat u hebt geactiveerd [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] voor uw organisatie, gebruikt u de [Azure Rights Management-implementatieschema](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) om te controleren of er andere configuratiestappen die u wilt doen zijn voor de implementatie [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] gebruikers en beheerders. U kunt bijvoorbeeld gebruiken [aangepaste sjablonen](http://technet.microsoft.com/library/dn642472.aspx) te vereenvoudigen voor gebruikers beveiliging van gegevens op bestanden wilt toepassen, verbinding maken met uw lokale servers te gebruiken [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] door te installeren die de [RMS-connector](http://technet.microsoft.com/library/dn375964.aspx), en implementeren de [Rights Management-toepassing voor delen](http://technet.microsoft.com/library/jj585031.aspx) met ondersteuning voor alle bestandstypen op alle apparaten beschermt. Office-services, zoals Exchange Online en SharePoint Online nodig aanvullende configuratie voordat u de functies van Information Rights Management (IRM) kunt gebruiken. Echter als er geen andere configuratie stappen die u nodig hebt om te doen, Zie [Met behulp van Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) voor operationele richtlijnen ter ondersteuning van op een succesvolle implementatie voor uw organisatie.

Voor informatie over hoe uw toepassingen met werken [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], Zie [Hoe toepassingen ondersteunen Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

