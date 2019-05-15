Sergi Muñoz Carmona
hisx2 12/05/2019

**Servei de Correu: Pop i IMAP**

El correu electrònic fimita el funcionament del correu postal.
El correu es un sistema el qual permet als usuaris enviar missatges a 
qualsevol destinatari

Una gran diferència que hi ha entre el servei de correu i el correu
electrònic és el mecanisme de transports dels missatges, ja que el mecanisme
de transport dels missatges és en SMTP i és independent del format i el 
contingut del missatge.

El disseny del sistema  ha anat evolucionant a mesura que s'ha anat desenvolupant i
millorant a internet.

* Model bàsic:

En el model bàsic de transport (SMTP), és necessari que el receptor 
disposi de connexió a internet per tal de poder connectar-se al servidor
local. Si ens volem baixar els correus , utilitzarem el protocol POP el qual
proporciona aquest mecanisme. Una vegada que internet es populitza i els correus 
es baixen en llocs diferents, es va començar a utilitzar el protocol IMAP, que
proporciona aquest mecanisme.


**Servei POP**

El servei POP (Post Office Protocol) és un servidor de correu que
conté les bústies dels usuaris locals. En aquest cas, l'usuari ha de 
treballar en local per tal d'accedir a la bústia. En el principi es va
utilitzar el servei POP fins que es va idealitzar un mecanisme per 
desenvolupar l'accés remot als comptes de correu per tal que l'usuari
es connecti en qualsevol lloc. 

Aquest va ocasionar el desenvolupament del protocol POP3 i del protocol IMAP, 
que permeten l'accés remot de clients a les bústies de correu.

* **Protocol POP3**

El servei POP3 és un protocol de la capa d'aplicació (TCP/IP) port 110, que
permet que un usuari es connecti remotament al servidor de correus. Em de tenir
en compte que el protocol POP3 ni el IMAP transporten el correu.

Estructura del protocol POP3 :

L'estructura del protocol POP3 està compost per l'arquitectura de client/servidor
i per diversos agents que intervenen en una comunicació POP3:

* **Agents**

* MUA (mail user agent). Per accedir al correu, l'usuari interactua amb el mail 
user agent mitjançant el POP3. Aquest users estàn programats en les pàgines 
de correus com GMAIL,Outlook...

* Client POP3. El client POP3 és l'encarregat de crear la comunicació amb 
el servidor POP3 per tal d'obtenir els missatges de la bústia de correu
de l'usuari. El llenguatge que utilitzen entre client/servidor és
el protocol POP3.


* Servidor POP3. EL servidor POP3 és l'encarregat d'implementar l'accés 
remot al correu, també conté les bústies dels usuaris. Els missatges
es reben mitjançant SMTP.

**Estats de sessió del POP3**

El protocol POP3 està estructurat per tres estats:

El primer estat és:**l'Autorització**

L'estat d'autorització es desenvolupa una vegada feta la connexió al servidor
on el client s'ha d'identificar al servidor indicant el seu compte d'usuari
i contraseña.

El segon estat és:**la Transacció**

Una vegada el client s'ha autoritzat, entra l'estat de transacció. En
aquest estat el client demana les ordres al servidor, com baixar el correu,
demanar capçaleres,etc. 

El tercer estat és:**l'Actualització**

El servidor entra en l'estat actualització una vegada ha rebut l'ordre
"quit" del client. En aquest moment es finalitza la comunicació


**Ordres del POP3**

En cada estat s'originen una serie d'ordres per interactuar.

En l'estat d'Autorització, es compon de les següents ordres:

* USER nomUsuari. Ordre per identificar el  nom d'usuari del client al servidor POP.

* PASS password Ordre per autenticar el client al servidor POP.


En l'estat de transacció, es compon de les següents ordres:

* STAT. Ordre que dona informació de la bustia de l'usuari.

* LIST[msg]. Ordre que llista els missatges o un en concret.

* RETR msg. Ordre que descarrega un missatge concret del servidor
al client.

* DELE msg. Ordre que marca el missatge que es vol esborrar, marca
només el missatge que es vol esborrar però no l'esborra.

* NOOP. Ordre que força al server a donar una resposta.

* RSET. Ordre que desmarca tots els missatges que estaven marcats per esborrar,
 es realitza abans de passar a l'estat d'actualització.
 
* TOP msg nlin. Ordre que descarrega només les línies inicials del missatge,

* UIDL[msg]. Ordre que identifica els missatges amb el número indicat.

* QUIT . Ordre que finalitza la sessió entre client i servidor.

En l'estat d'actualització no es compon d'ordres, nomès elimina els missatges
que han sigut marcats.


**. El servei IMAP**

El servei IMAP (Internet message access protocol) és un protocol de capa 
d’aplicació del model TCP/IP que proporciona a l’usuari accés remot a la 
seva bústia de correu. El servei IMAP es va desenvolupar a causa de sol·lucionar
a accedir al servei de correu en diferents ordinadors.

La diferència que té l'IMAP del POP és que el servidor imap consta d'una
estructura de carpetes on s'emmagatzemen els missatges de correu on 
es permet la manipulació remota de les carpetes i els missatges.
Es poden crear, modificar i suprimir carpetes i missatges


**Model IMAP**

L'estructura del model IMAP és de client/servidor i intervenen varis agents:

* MUA (mail user agent). Per accedir al correu, l'usuari interactua amb el mail 
user agent mitjançant IMAP. Aquest users estàn programats en les pàgines 
de correus com GMAIL,Outlook...

* Client IMAP. El client POP3 és l'encarregat de crear la comunicació amb 
el servidor IMAP per tal d'obtenir els missatges de la bústia de correu
de l'usuari. El llenguatge que utilitzen entre client/servidor és
el protocol IMAP.


* Servidor IMAP. EL servidor IMAP és l'encarregat d'implementar l'accés 
remot al correu, també conté les bústies dels usuaris. Els missatges
es reben mitjançant SMTP.


**Estats del protocol IMAP**

El protocol IMAP està estructurat per quatre estats:


El primer estat és:**No autenticat** 

Aquest estat es desenvolupa una vegada feta la connexió al servidor
on el client s'ha d'identificar al servidor indicant el seu compte d'usuari
i contraseña.

El segon estat és:**autenticat**

En aquest estat, un cop autenticat, es selecciona la carpeta que utilitzarem
on podrem fer qualsevol ordre com esborrar-la o crear una de nova.

El tercer estat és: **seleccionat**

En aquest estat es desenvolupa una vegada escollit l'ordre que volem 
executar per a les carpetes seleccionades. Seleccionat l'ordre,
podrem manipular el contingut de la carpeta.

El quart estat és: **logout**

Aquest estat es desenvolupa una vegada tanquem la sessió i la connexió
entre client/servidor.

Em de tenir en compte que el servidor IMAP emmagatzema permanentment
tots els missatges de l'usuari. Per fer-ho, utilitza un sistema de carpetes
i atributs:

**Carpetes (mailbox)**. La bústia és on es guarden els missatges. Dins
la bústia es poden crear carpetes. Aquestes carpetes disposen de dos
atributs:
		- Next UID: Indica el valor UID que s'assignarà al missatge
		següent que arribi.
		
		- UID Validity Value (UIDVALIDITY) : És el valor associat a la 
		carpeta seleccionada.
		
**Atributs de missatge.** Els missatges tenen atributs que s’emmagatzemen
en les pròpies bústies que en faciliten la gestió:


	-UID
	
	-Número de seqüencia
	
	- Indicadors
	
	- Data interna
	
	-Longitud
	
	-Estructura del sobre
	
	-Estructura del cos
	
	-Parts de text del missatge
	
	
	
**Funcionament IMAP**

Generalmen el funcionament del protocol IMAP és la connexió del
client al servidor a través del port 143 on s'inicia un diàleg el 
qual s'intercanvien ordres i respostes.

**Ordres**. Les ordres IMAP inclouen un tag inicial exemple : a001
la primera ordre i a002 la segona.

**Respostes**. Les respostes s'envien una vegada es processa l'ordre
enviada.

* **Llistat d'ordres** 

**Ordres generals en qualsevol estat:



