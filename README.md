<!--
*** Thanks for checking out this README Template. If you have a suggestion that would
*** make this better, please fork the repo and create a pull request or simply open
*** an issue with the tag "enhancement".
*** Thanks again! Now go create something AMAZING! :D
-->





<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->




<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="https://github.com/March-08/Stance_Detetion/blob/master/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">UNITOR: combining Transformer-based architectures and TransferLearning for robust Stance Detection</h3>




<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About the Project](#about-the-project)
  * [Built With](#built-with)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
  * [Installation](#installation)
* [Usage](#usage)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)
* [Acknowledgements](#acknowledgements)


<!-- ABOUT THE PROJECT -->
## About The Project


This project was developed for the [Web Mining and Retrivial class (CS)](http://ai-nlp.info.uniroma2.it/basili/didattica/WmIR_18_19/) at the [University of Tor Vergata](http://www.informatica.uniroma2.it/).<br/>
Under the supervision of **prof. Roberto Basili** and **prof. Danilo Croce**, we were able to develop a Stance Detection Classifier based on Bert model, that was released by Google, and that was published for the firt time in the following paper ["BERT: Pre-training of Deep Bidirectional Transformers for
Language Understanding"](https://arxiv.org/pdf/1810.04805.pdf)

While working on this project we took the opportunity to partecipate to the [EVALITA 2020](http://www.evalita.it/) competition.
EVALITA is a periodic evaluation campaign of Natural Language Processing (NLP) and speech tools for the Italian language, born in 2007.
This year EVALITA provided a task called [SardiStance](http://www.di.unito.it/~tutreeb/sardistance-evalita2020/index.html), that is basically a stance detection task, using a data-set containing Italian tweets about the [Sardines Movement](https://en.wikipedia.org/wiki/Sardines_movement).

### Task Description
The task is a three-class classification task where the system has to predict whether a tweet is in favour, against or neutral/none towards the given target, exploiting only textual information, i.e. the text of the tweet.
The dataset will include short documents taken from Twitter.
The evaluation will be performed according to the standard metrics known in literature (accuracy, precision, recall and F1-score)



### Built With
* [Google Colab](https://colab.research.google.com/github/tensorflow/examples/blob/master/courses/udacity_intro_to_tensorflow_for_deep_learning/l01c01_introduction_to_colab_and_python.ipynb)
* [PyTorch](https://pytorch.org/)

## Our Strategy

The main issue facing this task was that the dataset provided was very poor, it consisted in of 3,242 instances, in fact simply by using UmBERTo we obtained a low accuracy, about 56%.
**UmBERTo** is an Italian Language Model thatinherits from RoBERTa base model architecture which improves the initial BERT.
So we thought to train UmBERTO on differents but similiars tasks, and to use the resulting model to tag the tweets of our original dataset.
In this way each tag could give a hint about the sentence it was associated with.
The tasks we used for this purpose are:
- sentiment analysis
- hate speech detection
- irony detection

### Sentiment Analysis
The task consists in automatically annotating messages from the popular microblogging platform Twitter1 with a tuple of boolean values indicating the message’s subjectivity and polarity (positive or negative).
We used the dataset provided by EVALITA for the [SENTIPOLC](http://www.evalita.it/2016/tasks/sentipolc) challenge.
We trained our model with the sentipolc dataset, and we obtained an accuracy of, NUMERO%.
In this way we could tag with [PRO] [CONTRO] every sentence of the SardiStance dataset, using the model obtained from the sentiment task.
At the end, we processed our new dataset (cointaining the new tag for each tweet), and we observed that the mean accuracy over 10 cross folder validation improved from the first simple Bert model, we obtained an mean accuracy of NUMERO%, with a standard deviation of NUMERO%.


### Hate Speech Detection
This is a binary classification task aimed at determining whether the message contains Hate Speech or not
We used the dataset provided by EVALITA for the [HATE SPEECH](http://www.di.unito.it/~tutreeb/haspeede-evalita18/index.html) challenge.
We trained our model with the hate speech dataset, and we obtained an accuracy of, NUMERO%.
In this way we could tag with [ODIO] [NON ODIO] every sentence of the SardiStance dataset, using the model obtained from the hate speech detection task.
At the end, we processed our new dataset (cointaining the new tag for each tweet), and we observed that the mean accuracy over 10 cross folder validation improved from the first simple Bert model, we obtained an mean accuracy of NUMERO%, with a standard deviation of NUMERO%.


### Irony Detection
This is a classification task where the system has to predict whether a tweet is ironic or not, so given a message, decide whether the message is ironic or not.
We used the dataset provided by EVALITA for the [IronITA ](http://www.di.unito.it/~tutreeb/ironita-evalita18/index.html) challenge.
We trained our model with the hate IronITA dataset, and we obtained an accuracy of, NUMERO%.
In this way we could tag with [IRONICO] [NON IRONICO] every sentence of the SardiStance dataset, using the model obtained from the hate speech detection task.
At the end, we processed our new dataset (cointaining the new tag for each tweet), and we observed that the mean accuracy over 10 cross folder validation improved from the first simple Bert model, we obtained an mean accuracy of NUMERO%, with a standard deviation of NUMERO%.

### Our choice
We tried to use also multiple tags for each sentence, for example differents combinations of the tags derived from the tasks desribed above.
The results are all stored in the following table.
INSERIRE LA TABELLA
As we can see the most accurate run, is the the one that uses a combination of HATE TAG and SENTIMENT TAG !!!!!!!!!!!!!!!!!!!!! CORRREGGi


### Majority Voting
Ensemble methods are techniques that create multiple models and then combine them to produce improved results. Ensemble methods usually produces more accurate solutions than a single model would. 
Using the majority voting every model makes a prediction (votes) for each test instance and the final output prediction is the one that receives more than half of the votes. If none of the predictions get more than half of the votes, we may say that the ensemble method could not make a stable prediction for this instance. Although this is a widely used technique, you may try the most voted prediction (even if that is less than half of the votes) as the final prediction. In some articles, you may see this method being called “plurality voting”.
Using the majority voting we obtained an accuracy of NUMERO%.





<!-- ROADMAP -->
## Roadmap

The creation of the final model used for the EVALITA competition has seen many changes over time, we would like to explain here every strategies that we used in order to modify the simple Bert model provided by Google, and how we obtained the best classifier for this stance detection task.
We will report also in a table all the measures that we obtained using the various models that we delevoped during tests.

##£ Measures Reports

<img src="https://github.com/March-08/Stance_Detetion/blob/master/Cattura.PNG"/>





### SVM Baseline
A baseline is a method that uses heuristics, simple summary statistics, randomness, or machine learning to create predictions for a dataset. You can use these predictions to measure the baseline's performance (e.g., accuracy)-- this metric will then become what you compare any other machine learning algorithm against.
We used a simply Support Vector Machine as baseline in order to compare our more sophisticated models with this one.
As you can see in the table above we obtained an accuracy of 47.77%




<!-- GETTING STARTED -->
## Getting Started

This is an example of how you may give instructions on setting up your project locally.
To get a local copy up and running follow these simple example steps.

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
* npm
```sh
npm install npm@latest -g
```

### Installation

1. Get a free API Key at [https://example.com](https://example.com)
2. Clone the repo
```sh
git clone https://github.com/your_username_/Project-Name.git
```
3. Install NPM packages
```sh
npm install
```
4. Enter your API in `config.js`
```JS
const API_KEY = 'ENTER YOUR API';
```



<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_




<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.



<!-- CONTACT -->
## Contact

Your Name - [@your_twitter](https://twitter.com/your_username) - email@example.com

Project Link: [https://github.com/your_username/repo_name](https://github.com/your_username/repo_name)



<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
* [Img Shields](https://shields.io)
* [Choose an Open Source License](https://choosealicense.com)
* [GitHub Pages](https://pages.github.com)
* [Animate.css](https://daneden.github.io/animate.css)
* [Loaders.css](https://connoratherton.com/loaders)
* [Slick Carousel](https://kenwheeler.github.io/slick)
* [Smooth Scroll](https://github.com/cferdinandi/smooth-scroll)
* [Sticky Kit](http://leafo.net/sticky-kit)
* [JVectorMap](http://jvectormap.com)
* [Font Awesome](https://fontawesome.com)





<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=flat-square
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=flat-square
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=flat-square
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=flat-square
[issues-url]: https://github.com/othneildrew/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=flat-square
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/screenshot.png
All  models  are  implemented  using  Pytorch7andexperiments were run over Google Colab8.Results are reported in the Table 1.  In particu-lar, it reports the Precision, Recall and F1 resultsobtained  by  the  different  models  with  respect  toeach label. The final rank is obtained by consider-ing the average F1 (F1-avg) between theFavourandAgainstclasses.First of all, the high complexity of this task isconfirmed  by  the  results  obtained  by  the  strongBaseline  method  (the  last  row).   It  is  a  SupportVector  Machine  trained  over  a  simple  Bag-of-Word model (Cignarella et al., 2020) and achievesan average F1 of57.84%, being competitive withmany systems participating to the task and ranking13thover 22 submissions.One important result is obtained by the straightapplication of the UmBERTo model over the orig-inal  messages  (next  to  last  row  in  Table  1).   Infact, this Transformer-based architecture, empow-ered with the Ensemble technique, achieves an av-erage F1 of65.69%:  a system which directly ap-plies an Enseble of UmBERTo-based model wouldhave ranked6thin the competition.We  thus  trained  UmBERTo  by  adopting  theTransfer Learning approach presented in Section2.3  in  the  constrained  setting.   The  adoption  ofall the three auxiliary tasks led to the constrainedsubmission  called  UNITOR_c_2.   Moreover,  weconsidered the training of UmBERTo by consid-ering one auxiliary task at a time.  When consid-ering only the Hate Speech Detection task, betterresults  were  obtained  over  the  development  set,with  respect  to  the  adoption  of  the  other  taskstaken  individually,  i.e.,  Sentiment  Detection  andIrony  Detection9.    Such  a  variant,  called  UNI-TOR_c_1,  considers  tweets  enriched  only  withinformation  derived  by  the  hate  classifier  and  itgenerally shows higher precision with respect to theAgainstclass.   This  suggests  that  a  tweetexpressing  hate  is  more  likely  in  opposition  tothe Sardines Movement.   Both constrained mod-els ranked3rdand2ndin the competition, respec-tively.  These results are impressive as they bothoutperformed of about2%of absolute F1 the stan-dard UmBERTo. Moreover, they confirm the ben-eficial impact of Hate Speech Detection as an aux-iliary task.Finally,  we  augmented  the  training  dataset  byusing  the  additional  data  presented  in  Section2.2.   We  extended  the  training  material  used  totrain UNITOR_c_2 in order to obtain the uncon-strained  submission  called  UNITOR_u_2.    It  isworth  noticing  the  all  three  auxiliary  tasks  wereused in this submission. This led to a performancedrop, i.e.  a66.06%of average F1, which is lowerwith respect to the best opponent system,  whichachieved a66.21%of F1.  It seems that the noiseadded both from the auxiliary tasks and the addi-tional data, negatively impacted the overall qual-ity.  On the contrary, when only the Hate SpeechDetection task is considered (i.e., UNITOR_u_1)additional  data  are  positively  capitalized  by  themodel, achieving the best average F1 score in thecompetition,  i.e.68.53%.   These results suggestthat  the  combination  of  the  Transformer-basedlearning  with  the  adopted  strategies  of  TransferLearning  and  Data  Augmentation  is  highly  ben-eficial, when only Hate is considered.From an error analysis,  it seems that a signif-icant number of incorrect classifications occurredin longer and complex messages, where the topicof  the  stance  is  not  clearly  explicit  nor  capturedby the UmBERTo model, such as in “#carfagna:“io per i liberali che non si affidano a Salvini” e“dalle sardine buone idee”.   Auto-scacco in duemosse. Con la Polverini poi...”10. This message isconsidered to beAgainstwhile the system as-signs the labelNone.  Here, it is very challengingto understand the connection between the “good ideas of the sardines” and the very colloquial ex-pression “Auto-scacco” which can be translated as“own goal”. The same appears in the tweet “’ragaho finalmente capito chi mi ricordava Mattia San-tori, quello delle sardine:  Lodo Guenzi.  (e infattiin quanto a democristianitá stiamo lá)”11whichagain  labeledAgainstbut  classified  asNone.Clearly  the system  is  not able  to  link the  move-ment to its leader nor to the negative opinion aboutbelonging  to  the  Christian  Democrat  Party.   An-other example is the tweet “Dopo avere ascoltato@luigidimaio mi viene in mente una sola parola:grazie. Fiducia nelle sue scelte e immenso rispettoper i grandi risultati ottenuti.   Ora un nuovo in-izio,  con  un  nuovo  entusiamo.    Andiamo  versogli  #statigenerali  con  serietà  e  maturità.   Forza@mov5stelle!”12.  Here the system incorrectly as-signs  theFavourlabel  because  the  tweet  is  infavour of a different movement.

## 4 Conclusions
In  this  work  we  present  the  results  obtained  bythe  UNITOR  system,  which  participated  to  theSardiStance task. UNITOR ranked first in the TaskA, both for constrained and unconstrained runs.This  results  confirm  the  beneficial  impact  ofTransformer  based  architecture  for  text  classifi-cation  also  in  the  Stance  Detection  task.   More-over, we demonstrate the beneficial impact of HateSpeech Detection as an auxiliary task in a TransferLearning setting.  Finally, we empirically demon-strate that the adoption of Distance Supervision isuseful to reduce data sparseness.Future work will apply the above approaches tothe task B within SardiStance.  Moreover, we willinvestigate multi-task learning approaches (Liu etal., 2019a) to capitalize information from auxiliarytasks is a more principled way.

