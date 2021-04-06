# journal_of_research

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

Audio Mnist:
| Аугментация     | Valid_accuracy  | Test_accuracy  |
| --------------- |:---------------:| --------------:|
| No augmentation | 0.972           | 0.966          |
| TimeMasking     | 0.976           | 0.952          |
| FreqMasking     | 0.974           | 0.962          |
| Noise           | 0.97            | 0.96           |
| RandomErasing   | 0.972           | 0.957          |
| Shift           | 0.974           | 0.969          |

Heartbeat Sounds:
| Аугментация     | Valid_accuracy  | Test_accuracy  |
| --------------- |:---------------:| --------------:|
| No augmentation | 0.844           | 0.84           |
| TimeMasking     | 0.844           | 0.827          |
| FreqMasking     | 0.825           | 0.82           |
| Noise           | 0.822           | 0.822          |
| RandomErasing   | 0.832           | 0.822          |
| Shift           | 0.87            | 0.85           |

Видно, что только shift augmentation дает улучшение на тестовой выборке. В случае Audio Mnist TimeMasking, FreqMasking дает улучшение на валидации, но не дает улучшение на тесте. К слову, в статье https://arxiv.org/pdf/2008.04590.pdf Shift augmentation также показало лучший результат.
