---
description: na
keywords: na
title: View and use files that have been protected by Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5fa4666-6906-405a-9e0c-2c52d4cd27c8
---
# Weergeven en gebruiken van bestanden die zijn beveiligd door Rights Management
Wanneer de [RMS (Rights Management) voor het delen van toepassing is geïnstalleerd op uw computer](https://technet.microsoft.com/library/dn574734%28v=ws.10%29.aspx), u een beveiligd bestand weergeven door te dubbelklikken op. Het bestand is mogelijk een bijlage in een e-mailbericht of kunnen zien wanneer u bestand Explorer gebruikt.

> [!NOTE]
> Voordat u het beveiligde bestand weergeven kunt, moet eerst RMS bevestigen dat u bent gemachtigd om het bestand, dat het geval is door het controleren van uw gebruikersnaam en wachtwoord weer te geven. In sommige gevallen kan dit mogelijk in de cache opgeslagen en u ziet niet gevraagd om uw referenties. In andere gevallen wordt u gevraagd de referenties op te geven.
> 
> Als uw organisatie geen Azure Rights Management (Azure RMS) of AD RMS, kunt u voor een gratis account dat uw referenties accepteren wilt, zodat u kunt bestanden die worden beschermd met behulp van RMS openen toepassen:
> 
> -   Voor dit account, klikt u op de koppeling naar een aanvraag indienen voor [RMS voor personen](http://go.microsoft.com/fwlink/?LinkId=309469).
> 
>     Wanneer u zich aanmeldt, gebruikt u de e-mailadres van uw bedrijf in plaats van een persoonlijke e-mailadres. Als u zich aanmeldt van omdat u een beveiligde bijlage zijn verzonden, gebruikt u het e-mailadres dat is gebruikt voor het verzenden van e-mailbericht.
> -   Zie voor meer informatie [RMS voor personen en Windows Azure Rights Management](http://technet.microsoft.com/library/dn592127.aspx).

## <a name="BKMK_ViewPFILE"></a>Een beveiligd bestand weergeven
Dubbelklik op het beveiligde bestand via File Explorer of het e-mailbericht met de bijlage en voer uw referenties als u daarom wordt gevraagd.

Als er twee versies van het bestand, maar met verschillende bestandsextensies, open het bestand met een extensie .ppdf alleen als het bestand niet wordt geopend. Als u de versie .ppdf ofwel niet openen, het eerst installeert de [RMS sharing toepassing](http://technet.microsoft.com/library/dn574734.aspx), die het openen van bestanden met de extensie .ppdf kent.

> [!NOTE]
> Zie voor meer informatie "[Wat is het bestand .ppdf die automatisch wordt gemaakt?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)".

Hoe het bestand wordt geopend is afhankelijk van hoe is beveiligd, die u zien kunt eens kijken naar de extensie. In elk geval openen van het bestand kan worden gecontroleerd en blijft gecontroleerde zolang het is beveiligd. Bovendien als het bestand is verzonden als e-mailbijlage, de afzender kan de hoogte gesteld via e-mail telkens wanneer die u het bestand opent.

|Bestandsextensie en beveiliging|Meer informatie|
|-----------------------------------|-------------------|
|Het bestand heeft een **.pfile** extensie.<br /><br />Het bestand is generieke beveiligd.|Wanneer u het bestand opent, ziet u een **beveiligd bestand** in het dialoogvenster vanuit de delen die kunt u zien wie het bestand beveiligd en u wordt geacht de eigenaarsmachtigingen collega te. Klik op **Openen** om het bestand te lezen.<br /><br />![](../Image/ADRMS_MSRMSApp_PfilePermission.png)|
|Het bestand heeft een **.ppdf** bestandsnaamextensie of is een beveiligd bestand tekst of afbeelding (zoals **.ptxt** of **.pjpg**).<br /><br />Het bestand is standaard beveiligd als een kopie van de alleen-lezen.|Het bestand geopend met behulp van de viewer die met de RMS sharing toepassing wordt geïnstalleerd. Dit bestand is alleen-lezen, zelfs als u op een andere locatie opslaan of wijzig de naam.|
|Andere extensies.<br /><br />Het bestand is oorspronkelijk beveiligd.|Het bestand wordt geopend met behulp van de toepassing die is gekoppeld aan de oorspronkelijke bestandsextensie en een beperking banner wordt weergegeven aan de bovenkant van het bestand. De banner kan de machtigingen die worden toegepast op het bestand wordt weergegeven, of het mogelijk een koppeling om deze weer te geven. Bijvoorbeeld, ziet u mogelijk het volgende waar klikt u op **machtigingen zijn beperkt** om de werkelijke machtigingen die worden toegepast op het bestand en de mensen die toegang dit tot te bekijken:<br /><br />![](../Image/ADRMS_MSRMSApp_RestrictedAccess.png)|
Zie voor een volledige lijst met bestandsextensies die Rights Management ondersteunt de [Ondersteunde bestandstypen en bestandsextensies](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes) secties in de  [Rights Management delen toepassing beheerdershandleiding](../Topic/Rights_Management_sharing_application_administrator_guide.md). Als de bestandsnaamextensie niet wordt weergegeven, gebruikt u web te zoeken op te geven als een extensie die wordt ondersteund door een andere toepassing is.

> [!NOTE]
> Als na vastgesteld dat het bestand is beveiligd door Rights Management en het bestand niet wordt geopend, downloaden en gebruiken de [RMS Analyzer tool](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Volg de instructies in het hulpprogramma om te controleren op problemen die voorkomen een beveiligd document openen dat kunnen op uw computer.

## <a name="BKMK_UserDefined"></a>Gebruik van bestanden die zijn beveiligd (voor bijvoorbeeld, bewerken en afdrukken van het bestand)
Als u na het openen van het beveiligde bestand dat u wilt meer dan alleen lezen (bijvoorbeeld, bewerken, kopiëren en afdrukken):

|Bestandsextensie|Instructies|
|--------------------|---------------|
|Het bestand heeft een **.pfile** extensie.|Sla het bestand is geopend en geef deze een nieuwe bestandsnaamextensie die is gekoppeld aan de toepassing die u wilt gebruiken.<br /><br />Als een bestand is beveiligd met de naam van bestand document.vsdx.pfile, bijvoorbeeld het bestand weergeven en in File Explorer, kunt u het bestand opslaan als document.vsdx.<br /><br />Het nieuwe bestand is niet langer beveiligd. Als u beveiligen wilt, moet u dit handmatig doen. Zie voor instructies [Een bestand op een apparaat worden beveiligd &#40;beveiligen&#41; met behulp van de Rights Management-toepassing delen](../Topic/Protect_a_file_on_a_device__protect_in-place__by_using_the_Rights_Management_sharing_application.md).|
|Het bestand heeft een **.ppdf** bestandsnaamextensie of is een beveiligd bestand tekst of afbeelding (zoals **.ptxt** of **.pjpg**).|U kunt alleen het bestand weergeven en als u wilt wijzigen of verplaatsen, de beveiliging te blijven met het bestand.|
|Andere extensies.|Het apparaat moet een toepassing die Rights Management begrijpt gebruiken deze bestanden hebben. Deze toepassingen worden RMS enlightened toepassingen genoemd. Toepassingen van Office 2016, Office 2013 en Office 2010 (zoals Word, Excel, PowerPoint en Outlook) zijn voorbeelden van toepassingen die zijn enlightened voor Rights Management. Maar toepassingen die niet afkomstig van Microsoft, zoals andere softwarebedrijven en uw eigen line-of-business-toepassingen kunnen ook worden enlightened voor Rights Management.<br /><br />Toepassingen die zijn enlightened voor Rights Management weten hoe bestanden te openen die zijn beveiligd door andere Rights Management enlightened toepassingen. Ze ook bewaard de beveiliging, die is toegepast, zelfs als u het bestand bewerken of op een andere naam of een andere locatie opslaan. Deze toepassingen kunnen u het bestand volgens de machtigingen die momenteel worden toegepast op het bestand dat als u machtigingen voor het gebruik van het bestand hebt, kunt u dit doen. Bijvoorbeeld, u mogelijk het bestand bewerken, maar niet afdrukken.|

## Voorbeelden en andere instructies
Zie de volgende secties van de Rights Management delen application user guide voor voorbeelden voor het gebruik van de Rights Management-toepassing en praktische instructies delen:

-   [Voorbeelden voor het gebruik van de RMS sharing toepassing](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Wat wilt u doen?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Zie ook
[Rights Management delen toepassing handleiding](../Topic/Rights_Management_sharing_application_user_guide.md)

