#Informazioni Treni Italiani

Metodo per ottenere informazioni a scopo e utilizzo personale sui treni di trenitalia, trenord e compagnia bella.

Esempio chiamata:
```
$response = file_get_contents('URL');
$response = json_decode($response);
```
Esempio accesso informazioni:
```
$response->localita->nomeLungo;
```

###AUTOCOMPLETAMENTO STAZIONE

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/autocompletaStazione/{STRINGA_DI_RICERCA}`

RISPOSTA: TESTO 
CONTENUTO:
```
NOME_STAZIONE|ID_STAZIONE
NOME_STAZIONE|ID_STAZIONE
...
```


###ELENCO STAZIONI REGIONE

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/elencoStazioni/{ID_REGIONE}`

RISPOSTA:	ARRAY
CONTENUTO:
```
Array
(
    [0] => stdClass Object
        (
            [codReg] => ID_REGIONE
            [tipoStazione] => 4
            [dettZoomStaz] => Array
                (
                    [0] => stdClass Object
                        (
                            [codiceStazione] => ID_STAZIONE
                            [zoomStartRange] => 8
                            [zoomStopRange] => 9
                            [pinpointVisibile] => 1
                            [pinpointVisible] => 1
                            [labelVisibile] => 1
                            [labelVisible] => 1
                            [codiceRegione] => 
                        )

                    [1] => stdClass Object
                        (
                            [codiceStazione] => ID_STAZIONE
                            [zoomStartRange] => 10
                            [zoomStopRange] => 11
                            [pinpointVisibile] => 1
                            [pinpointVisible] => 1
                            [labelVisibile] => 1
                            [labelVisible] => 1
                            [codiceRegione] => 
                        )

                )

            [pstaz] => Array
                (
                )

            [mappaCitta] => stdClass Object
                (
                    [urlImagePinpoint] => 
                    [urlImageBaloon] => 
                )

            [codiceStazione] => ID_STAZIONE
            [codStazione] => ID_STAZIONE
            [lat] => LATITUDINE
            [lon] => LONGITUDINE
            [latMappaCitta] => 0
            [lonMappaCitta] => 0
            [localita] => stdClass Object
                (
                    [nomeLungo] => NOME_CITTÀ {AAA}
                    [nomeBreve] => NOME_CITTÀ {Aaa}
                    [label] => 
                    [id] => ID_STAZIONE
                )

            [esterno] => 1
            [offsetX] => -4
            [offsetY] => 18
            [nomeCitta] => NOME_CITTÀ {Aaa}
        )
)
```


###OTTENERE LE STAZIONI ALTERNATIVE DELLA CITT

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/elencoStazioniCitta/{ID_STAZIONE}`

RISPOSTA:	JSON/ARRAY
CONTENUTO: Numero indici uguali al numero di alternative
```
Array
(
    [0] => stdClass Object
        (
            [nomeLungo] => NOME_STAZIONE
            [nomeBreve] => NOME_STAZIONE
            [label] => NOME_CITT
            [id] => ID_STAZIONE
        )
	...
)
```


###CODICE NUMERICO REGIONE

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/regione/{ID_STAZIONE}`

RISPOSTA:	TESTO(NUMERO)
CONTENUTO:	ID_REGIONE -> Numero


###INFORMAZIONI STAZIONE

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/dettaglioStazione/{ID_STAZIONE}/{ID_REGIONE}`

RISPOSTA: JSON
CONTENUTO:
```
stdClass Object
(
    [codReg] => ID_REGIONE
    [tipoStazione] => 3
    [dettZoomStaz] => Array
        (
            [0] => stdClass Object
                (
                    [codiceStazione] => ID_STAZIONE
                    [zoomStartRange] => 8
                    [zoomStopRange] => 9
                    [pinpointVisibile] => 1
                    [pinpointVisible] => 1
                    [labelVisibile] => 1
                    [labelVisible] => 1
                    [codiceRegione] => 
                )

            [1] => stdClass Object
                (
                    [codiceStazione] => ID_STAZIONE
                    [zoomStartRange] => 10
                    [zoomStopRange] => 11
                    [pinpointVisibile] => 1
                    [pinpointVisible] => 1
                    [labelVisibile] => 1
                    [labelVisible] => 1
                    [codiceRegione] => 
                )

        )

    [pstaz] => Array
        (
        )

    [mappaCitta] => stdClass Object
        (
            [urlImagePinpoint] => 
            [urlImageBaloon] => 
        )

    [codiceStazione] => ID_STAZIONE
    [codStazione] => ID_STAZIONE
    [lat] => LATITUDINE
    [lon] => LONGITUDINE
    [latMappaCitta] => 0
    [lonMappaCitta] => 0
    [localita] => stdClass Object
        (
            [nomeLungo] => NOME_CITTÀ {AAA}
            [nomeBreve] => NOME_CITTÀ {Aaa}
            [label] => NOME_CITTÀ {Aaaa}
            [id] => ID_STAZIONE
        )

    [esterno] => 
    [offsetX] => 58
    [offsetY] => 20
    [nomeCitta] => NOME_CITTÀ
)
```


###ELENCO PARTENZE E ARRIVI DELLA STAZIONE

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/partenze/{ID_STAZIONE}/{DATA} [FORMATO: Wed Jan 07 2015 18:58:25 GMT+0100 (ora solare Europa occidentale)]`
URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/arrivi/{ID_STAZIONE}/{DATA} [FORMATO: Wed Jan 07 2015 18:58:25 GMT+0100 (ora solare Europa occidentale)]`

RISPOSTA:	JSON
CONTENUTO:
Numero indici uguale al numero di destinazioni
```
[0] => stdClass Object
        (
            [numeroTreno] => NUMERO_TRENO
            [categoria] => ALTERNATIVE : EC/EN/TGV-SVI/FR AV/FA AV/ITA/FB/IC/ICN/R/RV/S/RE/MXP/SFM/M/ACC/D/DD (http://it.wikipedia.org/wiki/Categoria_di_servizio_dei_treni_italiani)
            [categoriaDescrizione] => 
            [origine] => 
            [codOrigine] => ID_STAZIONE_PARTENZA
            [destinazione] => NOME_STAZIONE
            [codDestinazione] => 
            [origineEstera] => 
            [destinazioneEstera] => 
            [oraPartenzaEstera] => 
            [oraArrivoEstera] => 
            [tratta] => 0
            [regione] => 0
            [origineZero] => 
            [destinazioneZero] => 
            [orarioPartenzaZero] => 
            [orarioArrivoZero] => 
            [circolante] => TRUE(1)/FALSE(0)
            [codiceCliente] => NUMERO
            [binarioEffettivoArrivoCodice] => 
            [binarioEffettivoArrivoDescrizione] => 
            [binarioEffettivoArrivoTipo] => 
            [binarioProgrammatoArrivoCodice] => 
            [binarioProgrammatoArrivoDescrizione] => 
            [binarioEffettivoPartenzaCodice] => CODICE_BINARIO
            [binarioEffettivoPartenzaDescrizione] => NUMERO_BINARIO
            [binarioEffettivoPartenzaTipo] => 0
            [binarioProgrammatoPartenzaCodice] => 
            [binarioProgrammatoPartenzaDescrizione] => 
            [subTitle] => 
            [esisteCorsaZero] => 
            [orientamento] => 
            [inStazione] => TRUE(1)/FALSE(0)
            [haCambiNumero] => FALSE(0) ALTERNATIVA: TRUE(1) O NUMERO CAMBI -> NON TESTATO
            [nonPartito] => TRUE(1)/FALSO(0)
            [provvedimento] => 0
            [riprogrammazione] => N
            [orarioPartenza] => DATA_FORMATO_UNIX_TIMESTAMP*1000
            [orarioArrivo] => 
            [stazionePartenza] => 
            [stazioneArrivo] => 
            [statoTreno] => 
            [corrispondenze] => 
            [servizi] => 
            [ritardo] => 0
            [tipoProdotto] => 
            [compOrarioPartenzaZeroEffettivo] => ORARIO {ORA:MINUTI}
            [compOrarioArrivoZeroEffettivo] => 
            [compOrarioPartenzaZero] => ORARIO {ORA:MINUTI}
            [compOrarioArrivoZero] => 
            [compOrarioArrivo] => 
            [compOrarioPartenza] => ORARIO {ORA:MINUTI}
            [compNumeroTreno] => CATEGORIA NUMERO_TRENO {REG 0000}
            [compOrientamento] => Array
                (
                    [0] => --
                    [1] => --
                    [2] => --
                    [3] => --
                    [4] => --
                    [5] => --
                    [6] => --
                    [7] => --
                    [8] => --
                )

            [compTipologiaTreno] => CATEGORIA
            [compClassRitardoTxt] => 
            [compClassRitardoLine] => regolare_line
            [compImgRitardo2] => 
            [compImgRitardo] => /vt_static/img/legenda/icone_legenda/regolare.png
            [compRitardo] => Array
                (
                    [0] => in orario
                    [1] => on time
                    [2] => pünktlich
                    [3] => à l'heure
                    [4] => en horario
                    [5] => conform orarului
                    [6] => ??
                    [7] => ??
                    [8] => ?? ??????????
                )

            [compRitardoAndamento] => Array
                (
                    [0] => in orario
                    [1] => on time
                    [2] => pünktlich
                    [3] => à l'heure
                    [4] => en horario
                    [5] => conform orarului
                    [6] => ??
                    [7] => ??
                    [8] => ?? ??????????
                )

            [compInStazionePartenza] => Array
                (
                    [0] => Partito
                    [1] => Departed
                    [2] => angefährt
                    [3] => Partit
                    [4] => Salido
                    [5] => Plecat
                    [6] => ???
                    [7] => ???
                    [8] => ????????????
                )

            [compInStazioneArrivo] => Array
                (
                    [0] => Arrivato
                    [1] => Arrived
                    [2] => angekommen
                    [3] => Arrivé
                    [4] => Llegado
                    [5] => Sosit
                    [6] => ???
                    [7] => ???
                    [8] => ?????????
                )

            [compOrarioEffettivoArrivo] => 
            [compDurata] => 
            [compImgCambiNumerazione] =>   
        )
```


###INFORMAZIONE TRENO

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/andamentoTreno/{ID_STAZIONE}/{NUMERO_TRENO}`

RISPOSTA:	JSON
CONTENUTO:
```
[tipoTreno] => PG
    [orientamento] => 
    [codiceCliente] => NUMERO
    [fermateSoppresse] => 
    [dataPartenza] => 
    [fermate] => Array
        (
            [0] => stdClass Object
                (
                    [orientamento] => 
                    [kcNumTreno] => 
                    [stazione] => NOME_STAZIONE
                    [id] => ID_STAZIONE
                    [listaCorrispondenze] => 
                    [programmata] => DATA_FORMATO_UNIX_TIMESTAMP*1000
                    [programmataZero] => 
                    [effettiva] => DATA_FORMATO_UNIX_TIMESTAMP*1000
                    [ritardo] => 1
                    [partenzaTeoricaZero] => 
                    [arrivoTeoricoZero] => 
                    [partenzaTeorica] => 
                    [arrivoTeorico] => 
                    [partenzaReale] => DATA_FORMATO_UNIX_TIMESTAMP*1000
                    [arrivoReale] => 
                    [ritardoPartenza] => 1
                    [ritardoArrivo] => 0
                    [progressivo] => 1
                    [binarioEffettivoArrivoCodice] => 
                    [binarioEffettivoArrivoTipo] => 
                    [binarioEffettivoArrivoDescrizione] => 
                    [binarioProgrammatoArrivoCodice] => 
                    [binarioProgrammatoArrivoDescrizione] => 
                    [binarioEffettivoPartenzaCodice] => 220
                    [binarioEffettivoPartenzaTipo] => 0
                    [binarioEffettivoPartenzaDescrizione] => 4
                    [binarioProgrammatoPartenzaCodice] => 
                    [binarioProgrammatoPartenzaDescrizione] => 
                    [tipoFermata] => P
                    [visualizzaPrevista] => 1
                    [nextChanged] => 
                    [nextTrattaType] => 0
                    [actualFermataType] => 1
                )
				...
        )

    [anormalita] => 
    [provvedimenti] => 
    [segnalazioni] => 
    [oraUltimoRilevamento] => DATA_FORMATO_UNIX_TIMESTAMP*1000
    [stazioneUltimoRilevamento] => NOME_STAZIONE
    [idDestinazione] => ID_STAZIONE
    [idOrigine] => ID_STAZIONE
    [cambiNumero] => Array
        (
        )

    [hasProvvedimenti] => 
    [descOrientamento] => Array
        (
            [0] => --
            [1] => --
            [2] => --
            [3] => --
            [4] => --
            [5] => --
            [6] => --
            [7] => --
            [8] => --
        )

    [compOraUltimoRilevamento] => 19:38
    [motivoRitardoPrevalente] => 
    [descrizioneVCO] => 
    [numeroTreno] => NUMERO_TRENO
    [categoria] => REG
    [categoriaDescrizione] => 
    [origine] => NOME_STAZIONE
    [codOrigine] => 
    [destinazione] => NOME_STAZIONE
    [codDestinazione] => 
    [origineEstera] => 
    [destinazioneEstera] => 
    [oraPartenzaEstera] => 
    [oraArrivoEstera] => 
    [tratta] => 0
    [regione] => 0
    [origineZero] => NOME_STAZIONE
    [destinazioneZero] => NOME_STAZIONE
    [orarioPartenzaZero] => DATA_FORMATO_UNIX_TIMESTAMP*1000
    [orarioArrivoZero] => DATA_FORMATO_UNIX_TIMESTAMP*1000
    [circolante] => 1
    [binarioEffettivoArrivoCodice] => 
    [binarioEffettivoArrivoDescrizione] => 
    [binarioEffettivoArrivoTipo] => 
    [binarioProgrammatoArrivoCodice] => 
    [binarioProgrammatoArrivoDescrizione] => 
    [binarioEffettivoPartenzaCodice] => 
    [binarioEffettivoPartenzaDescrizione] => 
    [binarioEffettivoPartenzaTipo] => 
    [binarioProgrammatoPartenzaCodice] => 
    [binarioProgrammatoPartenzaDescrizione] => 
    [subTitle] => 
    [esisteCorsaZero] => 0
    [inStazione] => 
    [haCambiNumero] => 
    [nonPartito] => 
    [provvedimento] => 0
    [riprogrammazione] => 
    [orarioPartenza] => DATA_FORMATO_UNIX_TIMESTAMP*1000
    [orarioArrivo] => DATA_FORMATO_UNIX_TIMESTAMP*1000
    [stazionePartenza] => 
    [stazioneArrivo] => 
    [statoTreno] => 
    [corrispondenze] => 
    [servizi] => Array
        (
        )

    [ritardo] => 2
    [tipoProdotto] => 
    [compOrarioPartenzaZeroEffettivo] => 18:52
    [compOrarioArrivoZeroEffettivo] => 20:42
    [compOrarioPartenzaZero] => 18:50
    [compOrarioArrivoZero] => 20:40
    [compOrarioArrivo] => 20:40
    [compOrarioPartenza] => 18:50
    [compNumeroTreno] => REG 2662
    [compOrientamento] => Array
        (
            [0] => --
            [1] => --
            [2] => --
            [3] => --
            [4] => --
            [5] => --
            [6] => --
            [7] => --
            [8] => --
        )

    [compTipologiaTreno] => regionale
    [compClassRitardoTxt] => 
    [compClassRitardoLine] => regolare_line
    [compImgRitardo2] => 
    [compImgRitardo] => /vt_static/img/legenda/icone_legenda/regolare.png
    [compRitardo] => Array
        (
            [0] => ritardo 2 min.
            [1] => delay 2 min.
            [2] => Verspätung 2 Min.
            [3] => retard de 2 min.
            [4] => retraso de 2 min.
            [5] => întârziere 2 min.
            [6] => ?? 2 ?
            [7] => ?? 2??
            [8] => ????????? ?? 2 ?????
        )

    [compRitardoAndamento] => Array
        (
            [0] => con un ritardo di 2 min.
            [1] => 2 minutes late
            [2] => mit einer Verzögerung von 2 Min.
            [3] => avec un retard de 2 min.
            [4] => con un retraso de 2 min.
            [5] => cu o întârziere de 2 min.
            [6] => 2 ????
            [7] => ?? 2??
            [8] => ? ?????????? ? 2 ?????
        )

    [compInStazionePartenza] => Array
        (
            [0] => 
            [1] => 
            [2] => 
            [3] => 
            [4] => 
            [5] => 
            [6] => 
            [7] => 
            [8] => 
        )

    [compInStazioneArrivo] => Array
        (
            [0] => 
            [1] => 
            [2] => 
            [3] => 
            [4] => 
            [5] => 
            [6] => 
            [7] => 
            [8] => 
        )

    [compOrarioEffettivoArrivo] => /vt_static/img/legenda/icone_legenda/regolare.png20:42
    [compDurata] => 1:50
    [compImgCambiNumerazione] =>   
)
```


###INFORMAZIONI TRENO

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/tratteCanvas/{ID_STAZIONE}/{NUMERO_TRENO}`

RISPOSTA: JSON
CONTENUTO:
Numero indici uguale al numero di stazioni
```
[0] => stdClass Object
        (
            [last] => TRUE(1)/FALSE(0) STAZIONE_ARRVIO
            [stazioneCorrente] => TRUE(1)/FALSE(0)
            [id] => ID_STAZIONE
            [stazione] => NOME_STAZIONE
            [fermata] => stdClass Object
                (
                    [orientamento] => 
                    [kcNumTreno] => 
                    [stazione] => NOME_STAZIONE
                    [id] => ID_STAZIONE
                    [listaCorrispondenze] => 
                    [programmata] => DATA_FORMATO_UNIX_TIMESTAMP*1000
                    [programmataZero] => 
                    [effettiva] => DATA_FORMATO_UNIX_TIMESTAMP*1000
                    [ritardo] => TRUE(1)/FALSE(0)
                    [partenzaTeoricaZero] => 
                    [arrivoTeoricoZero] => 
                    [partenzaTeorica] => 
                    [arrivoTeorico] => 
                    [partenzaReale] => DATA_FORMATO_UNIX_TIMESTAMP*1000
                    [arrivoReale] => 
                    [ritardoPartenza] => TRUE(1)/FALSE(0)
                    [ritardoArrivo] => TRUE(1)/FALSE(0)
                    [progressivo] => TRUE(1)/FALSE(0)
                    [binarioEffettivoArrivoCodice] => 
                    [binarioEffettivoArrivoTipo] => 
                    [binarioEffettivoArrivoDescrizione] => 
                    [binarioProgrammatoArrivoCodice] => 
                    [binarioProgrammatoArrivoDescrizione] => 
                    [binarioEffettivoPartenzaCodice] => 220
                    [binarioEffettivoPartenzaTipo] => 0
                    [binarioEffettivoPartenzaDescrizione] => 4
                    [binarioProgrammatoPartenzaCodice] => 
                    [binarioProgrammatoPartenzaDescrizione] => 
                    [tipoFermata] => P
                    [visualizzaPrevista] => TRUE(1)/FALSE(0)
                    [nextChanged] => 
                    [nextTrattaType] => 0
                    [actualFermataType] => TRUE(1)/FALSE(0)
                )

            [partenzaReale] => TRUE(1)/FALSE(0)
            [arrivoReale] => TRUE(1)/FALSE(0)
            [first] => TRUE(1)/FALSE(0)
            [orientamento] => Array
                (
                    [0] => --
                    [1] => --
                    [2] => --
                    [3] => --
                    [4] => --
                    [5] => --
                    [6] => --
                    [7] => --
                    [8] => --
                )

            [nextTrattaType] => 1
            [actualFermataType] => 1
            [previousTrattaType] => 
            [trattaType] => 0
        )
```


###OTTENERE VIAGGI

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/soluzioniViaggioNew/{NUMERO_STAZIONE_PARTENZA}/{NUMERO_STAZIONE_ARRIVO}/{DATA} (formato: yyyy-mm-ddThh:mm:ss)`

RISPOSTA: JSON
CONTENUTO:
Numero indici uguale al numero di soluzioni
```
stdClass Object
(
    [soluzioni] => Array
        (
            [0] => stdClass Object
                (
                    [durata] => TEMPO (hh:mm)
                    [vehicles] => Array
                        (
                            [0] => stdClass Object
                                (
                                    [origine] => STAZIONE_PARTENZA
                                    [destinazione] => STAZIONE_ARRIVO
                                    [orarioPartenza] => ORARIO_PARTENZA (formato yyyy-mm-ddThh:mm:ss esempio:2015-01-08T05:18:00)
                                    [orarioArrivo] => ORARIO_ARRIVO (formato yyyy-mm-ddThh:mm:ss esempio:2015-01-08T05:18:00)
                                    [categoria] => NUMERO
                                    [categoriaDescrizione] => SIGLA (esempio REG)
                                    [numeroTreno] => NUMERO_TRENO
                                )

                        )

                )
				...
		)
)
```


###INFORMAZIONI METEO

URL: `http://www.viaggiatreno.it/viaggiatrenonew/resteasy/viaggiatreno/datimeteo/0`
RISPOSTA: JSON
CONTENUTO:
```
stdClass Object
(
    [ID_STAZIONE] => stdClass Object
        (
            [codStazione] => ID_STAZIONE
            [oggiTemperatura] => NUMERO
            [oggiTemperaturaMattino] => NUMERO
            [oggiTemperaturaPomeriggio] => NUMERO
            [oggiTemperaturaSera] => NUMERO
            [oggiTempo] => NUMERO
            [oggiTempoMattino] => NUMERO
            [oggiTempoPomeriggio] => NUMERO
            [oggiTempoSera] => NUMERO
            [domaniTemperatura] => NUMERO
            [domaniTemperaturaMattino] => NUMERO
            [domaniTemperaturaPomeriggio] => NUMERO
            [domaniTemperaturaSera] => NUMERO
            [domaniTempo] => NUMERO
            [domaniTempoMattino] => NUMERO
            [domaniTempoPomeriggio] => NUMERO
            [domaniTempoSera] => NUMERO
        )
		...
```
