---
description: na
keywords: na
title: Configuring Usage Rights for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
---
# Gebruiksrechten voor Azure Rights Management configureren
Wanneer u beveiliging op bestanden of e-mailberichten instellen met Azure Rights Management (Azure RMS) en een sjabloon niet te gebruiken, moet u de gebruiksrechten zelf configureren. Als u aangepaste sjablonen voor Azure RMS configureren, selecteert u bovendien de gebruiksrechten die wordt vervolgens automatisch toegepast als de sjabloon is geselecteerd door gebruikers, beheerders of services worden geconfigureerd. Bijvoorbeeld, in de Azure-portal kunt u rollen die een logische groepering van gebruiksrechten configureren of kunt u de afzonderlijke rechten.

Met dit onderwerp kunt u de gebruiksrechten die u voor de toepassing die u wilt configureren en te begrijpen hoe deze rechten worden geïnterpreteerd door toepassingen.

## Gebruiksrechten en beschrijvingen
De volgende tabel worden en beschrijft de gebruiksrechten die Rights Management ondersteunt, en hoe ze worden gebruikt en geïnterpreteerd. In deze tabel de **de algemene naam van** is doorgaans hoe ziet u het gebruik rechts weergegeven of waarnaar wordt verwezen als een meer beschrijvende versie van de waarde van één woord die wordt gebruikt in de code (de **in het beleid codering** waarde). De **API constante of waarde** is de naam van de SDK voor een MSIPC API-aanroep, gebruikt wanneer u een RMS enlightened toepassing schrijven die controleert op een juiste gebruik of voegt u een gebruik van rechts naar een beleid.

|De algemene naam|In het beleid codering|Beschrijving|Implementatie in Office aangepaste rechten|Naam in de Azure-portal|Naam in de AD RMS-sjablonen|API-constante of waarde|Aanvullende informatie|
|--------------------|--------------------------|----------------|----------------------------------------------|---------------------------|-------------------------------|---------------------------|--------------------------|
|Bewerken, inhoud, bewerken|DOCEDIT|Kan de gebruiker te wijzigen, rangschikken, opmaken of filteren van de inhoud in de toepassing. Dit betekent niet recht bewerkte kopie wilt opslaan.|Als onderdeel van de **wijziging** en **Volledig beheer** opties.|**Inhoud bewerken**|**Bewerken**|Niet van toepassing|In Office-toepassingen kan dit recht ook de gebruiker voor het document.|
|Opslaan|BEWERKEN|Kan de gebruiker het document opslaan in de huidige locatie.|Als onderdeel van de **wijziging** en **Volledig beheer** opties.|**Bestand opslaan**|**Opslaan**|IPC_GENERIC_WRITEL "BEWERKEN"|In Office-toepassingen kunt dit recht ook de gebruiker te wijzigen van het document.|
|Opmerking|OPMERKING|De optie aantekeningen of opmerkingen toevoegen aan de inhoud inschakelen|Niet geïmplementeerd|Niet geïmplementeerd|Niet geïmplementeerd|IPC_GENERIC_COMMENTL "COMMENTAAR"|Dit recht is beschikbaar in de SDK, is beschikbaar als een ad-hoc-beleid in de beveiliging van de RMS-module voor Windows PowerShell en in sommige toepassingen van de leverancier van software is geïmplementeerd. Echter niet veel gebruikt en wordt momenteel niet ondersteund door Office-toepassingen.|
|Opslaan als, exporteren|EXPORTEREN|Kan de optie voor het opslaan van de inhoud in een andere bestandsnaam op (OpslaanAls). Afhankelijk van de toepassing kan het bestand worden opgeslagen zonder beveiliging.|Als onderdeel van de **wijziging** en **Volledig beheer** opties.|**Inhoud (opslaan als) exporteren**|**Exporteren (opslaan als)**|IPC_GENERIC_EXPORTL "EXPORTEREN"|Dit recht kunt u ook andere opties exporteren om in te voeren toepassingen, zoals **verzenden naar OneNote**.|
|Naar voren|NAAR VOREN|De optie voor het doorsturen van een e-mailbericht en toe te voegen ontvangers kunnen de **naar** en **Cc** regels.|Geweigerd bij gebruik van de **niet doorsturen** standard beleid.|**Naar voren**|**Naar voren**|IPC_EMAIL_FORWARDL "DOORSTUREN"|De doorstuurserver rechten te verlenen aan andere gebruikers als onderdeel van de actie doorsturen toegestaan niet.|
|Volledig beheer|EIGENAAR|Alle rechten die aan het document verleent en alle beschikbare acties kunnen worden uitgevoerd.|Als de **Volledig beheer** aangepaste optie.|**Volledig beheer**|**Volledig beheer**|IPC_GENERIC_ALLL "EIGENAAR"|Bevat de mogelijkheid om de beveiliging opheffen.|
|Afdrukken|AFDRUKKEN|Kan de opties voor de inhoud afdrukken.|Als de **inhoud afdrukken** optie in de aangepaste machtigingen. Niet per geadresseerde-instelling.|**Afdrukken**|**Afdrukken**|IPC_GENERIC_PRINTL 'AFDRUKKEN|Er is geen aanvullende informatie|
|Reactie|REACTIE|Kunt u de optie beantwoorden in een e-client, zonder dat wijzigingen in de **naar** of **Cc** regels.|Niet van toepassing|**Reactie**|**Reactie**|IPC_EMAIL_REPLY|Er is geen aanvullende informatie|
|Allen beantwoorden|ALLEN BEANTWOORDEN|Kan de **Allen beantwoorden** optie in een e-mailclient, maar de gebruiker geadresseerden toevoegen is niet toegestaan de **naar** of **Cc** regels.|Niet van toepassing|**Allen beantwoorden**|**Allen beantwoorden**|IPC_EMAIL_REPLYALLL "ALLEN BEANTWOORDEN"|Er is geen aanvullende informatie|
|Weergave openen, lezen|WEERGAVE|Kan de gebruiker het document openen en de inhoud te zien.|Als de **lezen** aangepast beleid **weergave** optie.|**Inhoud weergeven**|**Weergave**|IPC_GENERIC_READL "WEERGEVEN"|Er is geen aanvullende informatie|
|Kopiëren|OPHALEN|Opties voor gegevens van het document kopiëren naar dezelfde of een andere kunt document.|Als de **toestaan dat gebruikers met leestoegang om inhoud te kopiëren** optie aangepast beleid.|**Kopiëren en Extract inhoud**|**Ophalen**|IPC_GENERIC_EXTRACTL "EXTRACT"|In sommige toepassingen bovendien worden hiermee het hele document kan worden opgeslagen in niet-beveiligde formulier.|
|Rechten weergeven|VIEWRIGHTSDATA|Kan de gebruiker om te zien van het beleid dat is toegepast op het document.|Niet geïmplementeerd|**Toegewezen rechten weergeven**|**Rechten weergeven**|IPC_READ_RIGHTSL "VIEWRIGHTSDATA"|Genegeerd door sommige toepassingen.|
|Rechten wijzigen|EDITRIGHTSDATA|Kan de gebruiker te wijzigen van het beleid dat is toegepast op het document. Bevat waaronder beveiliging opheffen.|Niet geïmplementeerd|**Rechten wijzigen**|**Rechten bewerken**|IPC_WRITE_RIGHTSL "EDITRIGHTSDATA"|Er is geen aanvullende informatie|
|Voorzien|OBJMODEL|De optie macro's of andere programmatisch of externe toegang tot de inhoud uitvoeren in een document kunt.|Als de **programmatische toegang toestaan** optie aangepast beleid. Niet per geadresseerde-instelling.|**Voorzien**|**Voorzien**|Niet van toepassing|Er is geen aanvullende informatie|

## Rechten opgenomen in de machtigingsniveaus
Sommige toepassingen groeperen gebruiksrechten in machtigingsniveaus, kunt u gemakkelijk selecteren gebruiksrechten die doorgaans samen worden gebruikt. Deze niveaus permisisons helpen abstracte complexiteit van gebruikers, zodat deze opties op basis van een rol zijn kunnen kiezen.  Bijvoorbeeld, **revisor** en **auteurs**. Hoewel deze opties vaak gebruikers een overzicht van de rechten, kunnen deze niet elke rechts die is opgenomen in de vorige tabel bevatten.

Gebruik de volgende tabel voor een lijst van deze machtigingsniveaus en een volledige lijst van de rechten die ze bevatten.

|Het niveau van machtigingen|Toepassingen|Rechten opgenomen (algemene naam)|
|-------------------------------|----------------|-------------------------------------|
|Viewer|Azure-portal<br /><br />Rights Management-toepassing voor Windows delen|Weergave openen, lezen<br /><br />Reactie<br /><br />Allen beantwoorden|
|Revisor|Azure-portal<br /><br />Rights Management-toepassing voor Windows delen|Weergave openen, lezen<br /><br />Opslaan<br /><br />Bewerken, inhoud, bewerken<br /><br />Reply<sup>*</sup><br /><br />Allen beantwoorden<sup>*</sup><br /><br />Naar voren halen<sup>*</sup>|
|Auteurs|Azure-portal<br /><br />Rights Management-toepassing voor Windows delen|Weergave openen, lezen<br /><br />Opslaan<br /><br />Bewerken, inhoud, bewerken<br /><br />Kopiëren<br /><br />Rechten weergeven<br /><br />Rechten wijzigen<br /><br />Voorzien<br /><br />Opslaan als, exporteren<br /><br />Afdrukken<br /><br />Reply<sup>*</sup><br /><br />Allen beantwoorden<sup>*</sup><br /><br />Naar voren halen<sup>*</sup>|
|Collega eigenaar|Azure-portal<br /><br />Rights Management-toepassing voor Windows delen|Weergave openen, lezen<br /><br />Opslaan<br /><br />Bewerken, inhoud, bewerken<br /><br />Kopiëren<br /><br />Rechten weergeven<br /><br />Rechten wijzigen<br /><br />Voorzien<br /><br />Opslaan als, exporteren<br /><br />Afdrukken<br /><br />Reply<sup>*</sup><br /><br />Allen beantwoorden<sup>*</sup><br /><br />Naar voren halen<sup>*</sup><br /><br />Volledig beheer|
<sup>*</sup> Niet van toepassing op de Rights Management-toepassing voor Windows delen

## Rechten die beschikbaar zijn in de standaardsjablonen
De rechten die opgenomen in de standaardsjablonen zijn zijn als volgt:

|Weergavenaam|Rechten opgenomen (algemene naam)|
|----------------|-------------------------------------|
|&lt; organisatienaam &gt; - alleen vertrouwelijke weergeven|Weergave openen, lezen|
|&lt; organisatienaam &gt; - vertrouwelijk|Weergave openen, lezen<br /><br />Opslaan<br /><br />Bewerken, inhoud, bewerken<br /><br />Rechten weergeven<br /><br />Voorzien<br /><br />Naar voren<br /><br />Reactie<br /><br />Allen beantwoorden|

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

