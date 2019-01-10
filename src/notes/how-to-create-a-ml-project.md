# Hvordan starte et ML-prosjekt
Som kjent, er dataanalyse den viktigste delen av denne typen prosjekter. Det er
derfor viktig at man analyserer dataen nøye. Man må finne ut hvilke data som er
relevante, hvilke som er støy, og hvilke `features` som er nødvendig for å
utarbeide en fungerende modell.

En annen ting som er viktig før man begynner å teste forskjellige algortimer, er
å lage en stabil og dekkende validering av dine modeller. Man bør derfor ha klar
en stabil kryss-validering allerede før man starter forskningen sin.

En som understreker denne filosofien er
[Shubin Dai](https://www.kaggle.com/bestfitting), den høyest rangerte
programmereren på [Kaggle](https://www.kaggle.com). I ett intervju forklarer han
sin iterative prosess.

> What does your iteration cycle look like?
>
> 1. Read the overview and data description of the competition carefully
> 2. Find similar Kaggle competitions. As a relatively new comer, I have
>    collected and done a basic analysis of all Kaggle competitions.
> 3. Read solutions of similar competitions.
> 4. Read papers to make sure I don’t miss any progress in the field.
> 5. Analyze the data and build a stable CV.
> 6. Data pre-processing, feature engineering, model training.
> 7. Result analysis such as prediction distribution, error analysis, hard
>    examples.
> 8. Elaborate models or design a new model based on the analysis.
> 9. Based on data analysis and result analysis, design models to add
>    diversities or solve hard samples.
> 10. Ensemble.
> 11. Return to a former step if necessary.

Fra dette kan vi trekke ut noen relevante punkter, og definere vår egen prosess.

## Prosess
1. Les og analyser lignende prosjekter.
2. Les artikler med lignende problemstillinger
3. Analyser dataen
4. Lag en gjennomtenkt kryss-validering
5. Begynn med pre-prosessering av data
   * Fjern urelevant data (`data cleaning`)
   * Trekk ut relevante datapunkter (`feature extraction`)
   * Tren dine modeller (`training`)
6. Analyser dine resultater
   * Se på fordelingen av dine prediksjoner
   * Gjør en feilanalyse
   * Trekk ut og analyser noen eksempler
7. Utdyp/forbedre modellen din, eller utform en ny modell basert på din analyse
8. Etter å ha utbedret modellen din, lag likevel nye modeller for å få ett
   større mangfold i dine løsninger
9. Gå gjennom dine funn
10. Gå tilbake til ett tidligere steg dersom nødvendig

## Validering
En god validering er det som faktisk beviser om du har oppnådd ett reelt
resultat. Det er derfor viktig å finne en god måte å validere modellene dine.

For å lage god validering, må man ha en god forståelse av dataen. Dette fører
oss tilbake til det første punktet i dette skrivet. Noen viktige ting er:

* Kontroller at distribusjonen gjenspeiles gjennom trenings-, test- og
  validerings-sett.
* Pass på at du ikke får med urelevant data som skaper støy
* Pass på at det du prøver å predikere ikke lekker gjennom dataen du bruker
  (dine `features`). Dette kan være ting som indirekte har en kobling til det
  resultatet du prøver å predikere.
