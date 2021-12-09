# journal_of_research

# 2020 / 2021 учебный год

### Отчет 04.10.2020

1. Собеседование со Сбером
2. Прочитана статья https://arxiv.org/pdf/1904.08779.pdf
В статье предложен метод аугментатации, состоящий из Time warping, Frequency masking и Time masking.
Используется LAS (Listen, Attend and Spell) сети. Метод аугментации сводит проблему over-fitting к проблеме under-fitting.
3. Ознакомился с https://mkegler.github.io/SpeechInpainting/, в частности https://arxiv.org/pdf/1910.09058.pdf (улучшение звука)
4. Прочитана статья https://arxiv.org/pdf/1910.09909.pdf (извлечение признаков аудио).
Представлен features extractor for transfer learning SpeechVgg (описана архитектура + представлен код).
5. Кратко ознакомился с https://github.com/Emotional-Text-to-Speech/dl-for-emo-tts
6. Просмотрены темы https://github.com/Dyakonov/MSU

### Отчет 18.10.2020
Чтение статей по аугментации и немного по улучшению звука. Больше двигаюсь в сторону аугментации. 
На следующей неделе планирую сделать обзор прочитанных методов аугментации. 
Через неделю, наверное, пора выступить на спецсеминаре.

### Отчет 25.10.2020
Поиск статей по аугментации звука. Начало обзора методов аугментации (pdf выложен). Подготовка к выступлению.

### Отчет 05.11.2020
Выступление на спецсеминаре (презентация выложена). 
Прочитано https://amitness.com/2020/05/data-augmentation-for-nlp/. Поиск аналогичных материалов по звуку.
Поиск задачи (среди цитирующих SpecAugment), где используется аугментация аудиоданных. В частности, есть такие статьи по Speech Recognition.

### Отчет 10.11.2020
Продолжение поиска задач, где используется аудиоаугментация.
В итоге можно выделить следующие направления:
1. Извлечение признаков из аудио
https://arxiv.org/pdf/1910.09909.pdf
Применяется к каждому сэмплу при обучении SpeechVgg
Сами же признаки применяются в следующих задачах: Speech inpainting, Language identification, Speech, music and noise classification, Speaker identification.
2. Wav2vec
https://arxiv.org/pdf/2006.11477.pdf
Стратегия маскировки похожа на SpecAugment

3. Speech Recognition

Много статей именно по этой теме

https://arxiv.org/pdf/1910.01493.pdf?fbclid=IwAR1pY5cvHTn0ljXIrYxeWB6yP-I0lIr6dFtMCcuDiT3Pn9dBLKdE1lxMVAo

https://arxiv.org/pdf/1910.12977.pdf

https://arxiv.org/pdf/1910.09799.pdf (показана эффективность SpecAugment)

https://arxiv.org/pdf/1911.01629.pdf

4. SpeechInpainting

https://mkegler.github.io/SpeechInpainting/

https://www.isca-speech.org/archive/Interspeech_2020/pdfs/1532.pdf

Используется SpeechVgg и SpecAugment

5. Применение в аудиоклассификации

Дополнительные статьи:

https://arxiv.org/pdf/2002.03788.pdf - text to speech

https://arxiv.org/pdf/2003.04298.pdf

### Отчет 21.11.2020

Разбор кода wav2vec, который выложен на github (pytorch). Работа с аугментацией для wav2vec планируется в ближайшее время. Дальше, вероятно, аугментация для SpeechInpainting (дополнительный анализ статьи). Там не выложен явно код (только для SpeechVgg на keras), но можно попробовать повторить то, что написано в статье.

### Отчет 01.12.2020

Продолжение разбора кода wav2vec, однако было принято решение приостановить работу с wav2vec.
Работа с кодом для SpeechVgg (на keras) - это выглядит наиболее перспективным.

### Отчет 18.12.2020

Знакомство с новым контестом на kaggle по звуку. 
Выступление по Speech Inpainting на семинаре по deep learning ВМК(презентация выложена).

### Отчет 16.03.2021

Участие в контесте kaggle "Rainforest Connection Species Audio Detection" (bronze).

Для экспериментов с аугментацией было найдено 3 датасета с kaggle:

1. Audio Speech Sentiment. https://www.kaggle.com/imsparsh/audio-speech-sentiment
2. Audio MNIST. https://www.kaggle.com/alanchn31/free-spoken-digits
3. Heartbeat Sounds. https://www.kaggle.com/kinguistics/heartbeat-sounds

Датасет Audio Speech Sentiment не подходит, так как на тесте можно достичь accuracy = 1 и в аугментации смысла нет. Остальные 2 датасета, кажется, подходят для экспериментов. Для всех 3 датасетов были решены задачи классификации (код выложен). Также был реализован метод аугментации, похожий на SpecAugment (маскирование), только вместо зануления я использовал добавление шума. Однако он пока не дал улучшения (был эксперимент только на AudioMnist).

### Отчет 06.04.2021

Проведены эксперименты на датасетах AudioMnist и Heartbeat Sounds со следующими типами аугментации: TimeMasking, FreqMasking, Shift, Noise, RandomErasing.
Результаты (кратко) представлены ниже

Audio Mnist - random seed 42:
| Аугментация     | Valid_accuracy  | Test_accuracy  |
| --------------- |:---------------:| --------------:|
| No augmentation | 0.972           | 0.966          |
| TimeMasking     | 0.976           | 0.952          |
| FreqMasking     | 0.974           | 0.962          |
| Noise           | 0.97            | 0.96           |
| RandomErasing   | 0.972           | 0.957          |
| Shift           | 0.974           | 0.969          |

Heartbeat Sounds  - random seed 42:
| Аугментация     | Valid_accuracy  | Test_accuracy  |
| --------------- |:---------------:| --------------:|
| No augmentation | 0.844           | 0.84           |
| TimeMasking     | 0.844           | 0.827          |
| FreqMasking     | 0.825           | 0.82           |
| Noise           | 0.822           | 0.822          |
| RandomErasing   | 0.832           | 0.822          |
| Shift           | 0.87            | 0.85           |

Видно, что только shift augmentation дает улучшение на тестовой выборке. В случае Audio Mnist TimeMasking, FreqMasking дают улучшение на валидации, но не дает улучшение на тесте. К слову, в статье https://arxiv.org/pdf/2008.04590.pdf Shift augmentation также показало лучший результат.

### Отчет 13.04.2021

Применена аугментация LoudnessControl: value = min_value + lyamnda * (value - min_value). Однако в нашем случае это не имеет смысла, так как в нашем случае min_value = 0, значит, value = lyambda * value.

На датасете Heartbeat Sounds проведены эксперименты с разными random seed (1 и 15, выбраны произвольно). В предыдущих экспериментых random seed = 42. Результаты представлены в таблице.

Heartbeat Sounds - random seed 1:
| Аугментация     | Valid_accuracy  | Test_accuracy  |
| --------------- |:---------------:| --------------:|
| No augmentation | 0.851           | 0.83           |
| TimeMasking     | 0.848           | 0.84           |
| FreqMasking     | 0.848           | 0.81           |
| Noise           | 0.863           | 0.807          |
| RandomErasing   | 0.86            | 0.807          |
| Shift           | 0.876           | 0.85           |

Heartbeat Sounds - random seed 15:
| Аугментация     | Valid_accuracy  | Test_accuracy  |
| --------------- |:---------------:| --------------:|
| No augmentation | 0.81            | 0.838          |
| TimeMasking     | 0.829           | 0.843          |
| FreqMasking     | 0.825           | 0.838          |
| Noise           | 0.829           | 0.84           |
| RandomErasing   | 0.829           | 0.855          |
| Shift           | 0.85            | 0.873          |

### Отчет 03.05.2021

Выступление на спецсеминаре. Продолжение экспериментов.

### Отчет 18.05.2021

Завершение экспериментов (код выложен). Работа над курсовой.

### Отчет 31.05.2021

Завершение работы над курсовой.

# 2021 / 2022 учебный год

### Отчет 22.10.2021

Начало экспериментов с выбором аугментации (из небольшого числа заранее заданных) после каждой эпохи.

Поиск возможных подходов к аугментации:
1. MixUp подходы

https://arxiv.org/pdf/2106.07085.pdf

https://arxiv.org/pdf/2110.06126.pdf

2. GAN-based подходы

https://arxiv.org/pdf/2109.09026.pdf

https://arxiv.org/pdf/2108.00899.pdf

3. Модификации SpecAugment

https://arxiv.org/pdf/2103.16858.pdf

https://arxiv.org/pdf/2110.00046.pdf

### Отчет 17.11.2021

Проведение экспериментов с методом выбора аугментации после каждой эпохи (код выложен). Результаты представлены ниже. Используются следующие сокращения:

R18 - resnet18

R50 - resnet50

AM - AudioMnist

HB - HeartBeatSounds

1. 'TimeCycleShift', 'Noise', 'TimeRandomSwap', 'FreqMasking'

| Метод аугментации       | R18 + AM       | R50 + AM       | R18 + HB       | R50 + HB       |
| ---------------------   |:--------------:| --------------:|:--------------:| --------------:|
| No augmentation         | 0.951 +- 0.012 | 0.946 +- 0.009 | 0.813 +- 0.008 | 0.818 +- 0.024 |
| Random сhoice           | 0.952 +- 0.013 | 0.946 +- 0.013 | 0.830 +- 0.014 | 0.845 +- 0.016 |
| Choice after each epoch | 0.962 +- 0.004 | 0.956 +- 0.008 | 0.851 +- 0.024 | 0.850 +- 0.018 |
| Frequency random choice | 0.964 +- 0.008 | 0.950 +- 0.008 | 0.862 +- 0.024 | 0.858 +- 0.007 |

2. 'TimeCycleShift', 'TimeMasking', 'TimeSwapAugmentation', 'FreqMasking'

| Метод аугментации       | R18 + AM       | R50 + AM       | R18 + HB       | R50 + HB       |
| ---------------------   |:--------------:| --------------:|:--------------:| --------------:|
| No augmentation         | 0.951 +- 0.012 | 0.946 +- 0.009 | 0.813 +- 0.008 | 0.818 +- 0.024 |
| Random сhoice           | 0.962 +- 0.004 | 0.949 +- 0.012 | 0.848 +- 0.020 | 0.852 +- 0.019 |
| Choice after each epoch | 0.959 +- 0.009 | 0.951 +- 0.005 | 0.857 +- 0.017 | 0.853 +- 0.011 |
| Frequency random choice | 0.960 +- 0.005 | 0.951 +- 0.008 | 0.854 +- 0.015 | 0.865 +- 0.010 |

3. 'Noise', 'TimeMasking', 'TimeRandomSwap', 'FreqMasking'

| Метод аугментации       | R18 + AM       | R50 + AM       | R18 + HB       | R50 + HB       |
| ---------------------   |:--------------:| --------------:|:--------------:| --------------:|
| No augmentation         | 0.951 +- 0.012 | 0.946 +- 0.009 | 0.813 +- 0.013 | 0.825 +- 0.020 |
| Random сhoice           | 0.958 +- 0.009 | 0.946 +- 0.012 | 0.816 +- 0.020 | 0.834 +- 0.020 |
| Choice after each epoch | 0.958 +- 0.010 | 0.952 +- 0.015 | 0.831 +- 0.009 | 0.832 +- 0.011 |
| Frequency random choice | 0.958 +- 0.006 | 0.954 +- 0.009 | 0.820 +- 0.016 | 0.831 +- 0.006 |

4. 'TimeCycleShift', 'TimeSwapAugmentation', 'TimeRandomSwap', 'TimeReplyMasking'

| Метод аугментации       | R18 + AM       | R50 + AM       | R18 + HB       | R50 + HB       |
| ---------------------   |:--------------:| --------------:|:--------------:| --------------:|
| No augmentation         | 0.951 +- 0.012 | 0.946 +- 0.009 | 0.813 +- 0.008 | 0.818 +- 0.024 |
| Random сhoice           | 0.955 +- 0.008 | 0.952 +- 0.013 | 0.840 +- 0.015 | 0.863 +- 0.026 |
| Choice after each epoch | 0.956 +- 0.006 | 0.949 +- 0.009 | 0.874 +- 0.006 | 0.858 +- 0.013 |
| Frequency random choice | 0.956 +- 0.009 | 0.951 +- 0.015 | 0.872 +- 0.014 | 0.864 +- 0.014 |


При использовании метода выбора аугментации после каждой эпохи время обучения увеливается примерно в 1.3 - 1.4 раза.

### Отчет 26.11.2021

Выступление на спецсеминаре (презентация - Методы аугментации/SpecMix.pdf)

Сделан обзор литературы - Методы аугментации/Related Work.pdf

### Отчет 09.12.2021

Продолжение работы над обзором литературы - Методы аугментации/Related Work.pdf
