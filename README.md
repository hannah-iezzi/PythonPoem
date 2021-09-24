# PythonPoem

from textblob import TextBlob
import nltk
nltk.download('punkt')
import random 
nltk.download('averaged_perceptron_tagger')

with open("/content/thegreatgatsby.txt") as f:
  text = f.read()
  
text

blob = TextBlob(text)
sentences = blob.sentences

nouns = []
verbs = []

for w,pos in blob.tags:
  if (pos == 'NN'):
    nouns.append(w)
  if (pos == 'VB'):
    verbs.append(w)

pro_sents = []

for s in sentences:
  if (len(s.words) > 0):
    if (s.words[0] in ["She","He","They","We","It"]):
      pro_sents.append(s)
title = random.choice(blob.words)

short_sentences = []
for ps in pro_sents:
  if (len(ps.words) < 4):
    short_sentences.append(ps)

# shuffle those sentences
random.shuffle(short_sentences)

for s in short_sentences:
  # remove linebreaks
  s = s.replace("\n",' ')
  print(s)  
