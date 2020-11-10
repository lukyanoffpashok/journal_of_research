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

