Intralingual Diachronic Translation of CBDU Texts
=================================================

The repository contains a parallel corpus of the predictions of the models described in the paper "Evaluating the Use of Generative LLMs for Intralingual Diachronic Translation of Middle-Polish Texts into Contemporary Polish".

258 transcribed documents sourced from [CBDU](https://cbdu.ijp.pan.pl/) were translated into contemporary Polish using ChatGPT-3.5. 
The resulting parallel corpus was used to train three text-to-text models: [plBART-base](https://huggingface.co/sdadas/polish-bart-base), [plT5-base](https://huggingface.co/allegro/plt5-base) and [plT5-large](https://huggingface.co/allegro/plt5-large). Please consult the paper for more details.


Prompt
------

The prompt used to process the source texts with ChatGPT consisted of five conversation turns and contained two sets of example sentences and correspondind example responses.

1. User:

         Przetłumacz poniższe zdania na współczesny język polski. Podaj odpowiedź w formacie JSON (pod kluczem „translations”). Zdania:
        „1. Już Szláchćicem y Bohátyrem żaden ći Miástá Rynku Kośćiołá Gospody niech nie broni.”
        „2. Nikt ćię niechay niedźieczkuie.”
        „3. Ciężaru żadnego ná ćię niekłádźie podátku z ćiebie nie wyćiągá.”
        „5. A iesli co z grzeszysz sámey tylko Krolewskiey pomsty czekay.”
        „6. Jnszy iesliby sie czego nierządnego dopuśćili ćiebie sie niechay iáko Sędźiego vznawce boią: bądź szláchćic bądź nie szláchćić będźie.”

2. Assistant:

        {
            "translations": [
                "1. Niech żaden szlachcic ani bogaty człowiek nie broni ci dostępu do miasta, rynku, kościoła czy gospody.",
                "2. Niech nikt cię nie obraża.",
                "3. Niech nikt nie nakłada na ciebie żadnego ciężaru, nie wydusza od ciebie podatku.",
                "5. Jeśli grzeszysz, oczekuj tylko królewskiej kary",
                "6. Jeżeli inni dopuszczaliby się czegoś niewłaściwego, niech się ciebie boją jako sędziego, niezależnie czy są szlachcicami czy nie."
            ]
        }

3. User:

        Zdania:
        „Od Woysk Cesárskich y Gálispánow, wtych dniách nic tu nieprzybyło osobliwego do oznáymienia ztąd.”
        „Cesárskie stoi ná dawnym mieyscu in Confinijs Trydentu.”
        „Gálispánow záś Woyská, in Territorijs Mantuy y Modeny,”

4. Assistant:

        {
            "translations": [
                "Od wojsk cesarskich i hiszpańskich, w tych dniach nic tu nie przybyło szczególnego do zawiadomienia stąd.",
                "Cesarskie stoi na dawnym miejscu na granicach Trydentu.",
                "Hiszpańskie wojska, na terytoriach Mantui i Modeny,"
            ]        
        }

5. User:

        Zdania:
        „[SENTENCE TO BE TRANSLATED 1]”
        „[SENTENCE TO BE TRANSLATED 2]”
         [...]


Automatic Evaluation
--------------------

| **Model**        | **BLEU**  | **ChrF**  | **TER**   | **ROUGE-L** | **COMET** | **Perplexity** |
|------------------|-----------|-----------|-----------|-------------|-----------|----------------|
| Source sentences | –         | –         | –         | –           | –         | 556.06         |
| ChatGPT-3.5      | –         | –         | –         | –           | –         | 297.82         |
| plBART-base      | 15.96     | 44.25     | 76.16     | 0.44        | 0.65      | 383.53         |
| plT5-base        | 18.41     | 46.20     | 74.47     | 0.47        | 0.66      | 310.65         |
| plT5-large       | **19.55** | **48.18** | **72.04** | **0.49**    | **0.70**  | **290.50**     |


Human Evaluation
----------------

We performed human evaluation on a sample of 100 sentences processed by ChatGPT-3.5 and plT5-large.
Two aspects of translation quality were assessed – adequacy and fluency.

Average scores:


| **Model**        | **Adequacy**  | **Fluency** |
|------------------|---------------|-------------|
| ChatGPT          | 3.78          | 4.48        |
| plT5-large       | 3.54          | 4.07        |

Scoring scale:

| **Score**  | **Adequacy**        | **Fluency**          |
|------------|---------------------|----------------------|
| 5          | all meaning         | flawless Polish      |
| 4          | most meaning        | good Polish          |
| 3          | much meaning        | non-native Polish    |
| 2          | some meaning        | disfluent Polish     |
| 1          | no meaning          | incomprehensible     |


Citation
--------
```
Klamra, C., Kryńska K. and Ogrodniczuk, M. (2023). Evaluating the Use of Generative LLMs for Intralingual Diachronic Translation of Middle-Polish Texts into Contemporary Polish. To appear in proceedings of ICADL 2023.
```
