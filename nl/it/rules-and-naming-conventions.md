---

copyright:
  years: 2018
lastupdated: "2018-05-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Regole e convenzioni di denominazione

## Quali sono le regole per il nome host?
La stringa di input del `Nome host` **deve**:
  * consistere in caratteri alfanumerici
  * essere inferiore ai 254 caratteri
  * terminare con un nome dominio di livello superiore valido
  * **non** deve contenere più di 10 etichette
  * **non** deve terminare con `cdnedge.bluemix.net` (tale termine viene utilizzato per i CNAME ed è riservato)

Consulta RFC 1035, sezione 2.3.4 per ulteriori dettagli.

## Quali sono le convenzioni di denominazione CNAME personalizzate?
La stringa di input `CNAME` deve rispettare le seguenti regole:
  * **deve** essere univoca (non può essere utilizzata da altre CDN IBM Cloud)
  * inferiore ai 64 caratteri alfanumerici
  * i caratteri speciali `! @ # $ % ^ & *` **non** sono consentiti
  * i caratteri di sottolineatura (`_`) **non** sono consentiti
  * i punti (`.`) **non** sono consentiti
  * i trattini `-` sono consentiti ma CNAME non può iniziare o terminare con un trattino

## Quali sono le regole per i nomi bucket?
I nomi bucket:
  * **devono** avere almeno 1 carattere
  * devono avere meno di 200 caratteri
  * possono contenere lettere (sono consentite sia lettere maiuscole che minuscole), numeri e trattini
  * **non** devono avere il formato di un indirizzo IP (ad esempio, 127.0.0.1)
  * **non** possono iniziare con un punto (.)
  * possono terminare con un punto (.)
  * è consentito solo un punto (.) tra le etichette (ad esempio, my..ibmcloud.bucket non è consentito).

**NOTA**: anche se lettere maiuscole e punti possono superare la convalida, consigliamo di utilizzare sempre nomi di bucket conformi a DNS.

## Quali sono le regole per la stringa percorso per l'origine?
Il percorso è facoltativo quando crei la tua CDN. Tuttavia, se fornito, il percorso **deve**:
  * avere una lunghezza inferiore ai 1000 caratteri
  * iniziare con `/`

## Quali sono le regole per la stringa percorso per l'eliminazione?
Il percorso di eliminazione:
  * deve avere una lunghezza inferiore ai 1000 caratteri
  * deve iniziare con `/`
  * non può terminare con `/`
  * non può terminare con un punto (.)
  * non può contenere `*`

**NOTA**: l'eliminazione è consentita solo per i singoli file. L'eliminazione a livello di directory non è supportata in questo momento.

## Per il comando **Aggiungi origine**, esistono delle regole da seguire per la stringa del percorso?
Per **Aggiungi origine**, il percorso è **obbligatorio**. Anche se la tua CDN è stata creata con un percorso, il percorso per **Aggiungi origine** deve iniziare con il percorso della CDN come prefisso. Ad esempio, se il percorso della CDN è stato specificato come `/storage`, per richiamare **Aggiungi origine** con un percorso denominato `/examplePath`, il percorso fornito sarà `/storage/examplePath`.

## Quali sono le regole per fornire le estensioni file?
Quando si crea un'origine con Object Storage, le estensioni file devono essere separate da virgole. Ad esempio, `txt, jpg, xml` è un elenco valido. Qualsiasi estensione particolare non può essere più lunga di 10 caratteri.