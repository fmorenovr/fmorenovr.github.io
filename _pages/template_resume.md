---
layout: archive
title: "Resume"
permalink: /resume/
author_profile: true
redirect_from:
  - /cv
---

{% include base_path %}

Education
======
* M.Sc. in Computer Science, Universidad Católica San Pablo (UCSP), Arequipa - PERU , 2018-2020
* B.Sc. in Computer Science, Universidad Nacional de Ingeniería (UNI), Lima - PERU, 2012-2017

Professional experience
======
* May 2019 - April 2020: Research Assistant
  * Fundação Getúlio Vargas (FGV)
  * Escola de Matemtica Aplicada (EMAp)
  * Supervisor(s): Phd. Jorge Poco
  * Research fields: Urban Perception, Deep Learning, and Interpretability Machine Learning

* June 2018 - April 2019: Software Engineer
  * ARIOT S.A.C.
  * Duties included: IT consultant, IoT services deployment.

* August 2017 - May 2018: Web Development Engineer
  * CERNICALO S.A.
  * Duties included: Web and Mobile applications development

* Jan 2016 - July 2017: Research Assistant
  * Centro de Tecnologías de la Información y Comunicationes (CTIC)
  * Big Data & HPC Lab
  * Supervisor(s): PhD. Manuel Castillo and PhD. José Fiestas
  * Research fields: Big Data, High-Performance Computing, and Fog Computing

Publications
======
  <ul>{% for post in site.publications reversed %}
    <li>
      <h3 class="archive__item-title" itemprop="headline"> <a href="{{ post.event }}" rel="permalink">{{ post.title }}</a></h3>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
    </li>
  {% endfor %}</ul>

Oral presentations and Poster sessions
======
### Posters  
  <ul>{% for post in site.posters reversed %}
    <li>
      <h3 class="archive__item-title" itemprop="headline"> <a href="{{ post.event }}" rel="permalink">{{ post.title }}</a></h3>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
    </li>
  {% endfor %}</ul>

### Presentations
  <ul>{% for post in site.presentations reversed %}
    <li>
      <h3 class="archive__item-title" itemprop="headline"> <a href="{{ post.event }}" rel="permalink">{{ post.title }}</a></h3>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
    </li>
  {% endfor %}</ul>

Portfolio
======
  <ul>{% for post in site.portfolio %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Talks
======
  <ul>{% for post in site.talks %}
    {% include archive-single-talk-cv.html %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Honors and Awards
======
* Dec 2019: __NeurIPS Travel Grant__ for the Annual Conference on Neural Information Processing Systems.
* June 2019: __ICML Travel Grant__ for the International Conference on Machine Learning.
* Dec 2018: __LXAI Travel Grant__ for the LatinX in AI Workshop  co-located with NeurIPS 2018.
* Nov 2018: __Leaders in Innovation Fellowship__ for the The Royal Academy of Engineering, London, UK.
* May 2018: __Master Fellowship__ for the CONCYTEC and Universidad Católica San Pablo (UCSP).
* July 2017: __Higher Fifth__ of the class of Computer Science. 
* July 2016: __Outstanding Students__ for the Universidad Nacional de Ingeniería (UNI).

Service and leadership
======
* Director and Co-Founder at Orientate Perú.
* __Innovation Mentor__ at the technological incubator StartUp UNI, Lima, Perú.
* Member of the University Assembly from 2016 to 2017.
  
Skills
======
* Programming Languages:
  * C, C++, Go
  * Python, R, M (Octave/MATLAB)
  * Javascript

* Software Development:
  * AWS Lambda, MongoDB, Android
  * OpenGL, OpenCV, MPI, OpenMP
  * VueJS, ReactJS, Flask, DJango, BeeGo, Gorilla

* Machine Learning and Data Science:
  * Keras, PyTorch, Caffe, TensorFlow
  * Numpy, scikit-learn, pandas

* Languages
  * Spanish: Native
  * English: Fluent
  * Portuguese: Intermediate
  * Japanese: Basic (JLPT N5, rank A)

Interest
======
Interpetability Machine Learning, Urban Computing, Deep Learning, Internet of Things, Fog Computing.

References
======
Available on request.
