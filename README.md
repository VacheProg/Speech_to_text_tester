# Speech-to-text tester
This repo tested openai whisper models for English with Indian accents, the same testings could be done for different accent

# Environment setup
1) create python3.9.9 venv
2) install jupyter notebook
3) install whisper package https://github.com/openai/whisper
4) pip install jiwer , pandas


# Research and testing done in this document

1) 4 Indian accent speakers that tell about themselves in English class(with tiny and medium models)
2) Gender(vocal) tests on auto-generated(AG) speeches with https://www.narakeet.com/ 
3) Formal/informal speech differences
4) Tests for the same text for American speakers and Indian speakers
5) Different field test(eg. biology, IT, Math etc.) (not fully covered yet)


# Text processing and WER calculations
First removed filler words from comparable texts, afterward removed punctuation marks(, - ! ? etc..)(this step is optional and performed with and without). The last step called jiwer wer function calculates the word error rate with this equation
[WER Equation](equation.png)


# Analyzes and results
#### Current research shows below problems or possible flows
1) When the speaker is not native and can not tell his thoughts correctly and uses some sounds while he finds the correct word(not only filler words) model gets confused and misunderstood the next words after that sounds
2) When the speaker laughs in the middle of the speech firstly model doesn't convert this to some expressions in the text which may lead to context-meaning changes, secondly as previus point it mixes next word and model gets confused
3) Per my understanding model not so much cares about context and sometimes fills words that do not fit the sentence meaning(which is for me weird as whisper models take sounds as 30 seconds log-mei spectrogram and understand it as the whole context)
4) Regarding auto-generated speech my conclusion was that it is not a good idea to test the model in this way as speech is very clear which can not happen in the real world, but as I tried some cases with this approach I find that:<br>
  a) gender(voice category ) doesnt change a lot result<br>
  b) Model for formal texts gives better results than for informal texts(which I think is a problem for daily meetings and talks)<br>
  c) Although I tested on biology and IT spheres and the model give good results but I think with more data there it is possible to find issue<br>
  
  
# Further research
### As these tests are not final and leave space for testing in near future I am planning to do the below tests
1) Generate big data or use some datasets like NPTEL-2020 find word-> error_count mapping to address words that are mispronounced frequently
2) As the model takes 30-sec segments from the speech test accuracy of pronounced words before and after each 30th second(if part of the word is in one segment another part is in another segment)
3) Continue different field tests to find fields where this model performance is bad
4) With cases that can cause a problem test other accents (eg. Chinese, Russian, etc.)
5) Add new measurement SER sentence error rate for bigger texts
6) Add noise to clean audio with different rates and amplitude
