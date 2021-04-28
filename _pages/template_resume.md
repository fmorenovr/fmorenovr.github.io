---
permalink: /resume_log/
author_profile: true
redirect_from:
  - /cv_log
---

{% include base_path %}

About
======

I am a Artificial Intelligence Engineer in the Escola de Matemática Aplicada (EMAp) at the Fundação Getúlio Vargas (FGV), my research lies at the intersection of **Urban Perception**, **Deep Learning**, and **Interpretability Machine Learning**. I am especially interested in building efficient, and robust models that can perform analyzing, and understanding human perception from street images with or without associated description text to improve the identification of the visual components, and main perceptual features extraction for applications in urban computing. I'm also a back-end developer very passionate about Python, Golang, and DevOps. [[CV]](/pdf/CV.pdf)

Employment
======
**[Fundação Getúlio Vargas (EMAp)](https://emap.fgv.br/)** <span style="float:right">Rio de Janeiro, Brazil</span>  
*Artificial Intelligence Engineer* <span style="float:right">May 2019 - Current</span>

* Working at the Timberflow project (FGV-EMAp, USP-ICMC, Imaflora).
* Developed **Urbex**, an interactive web-based system to understand Urban Perception of streets. 
* **Tech stack**: Python, Numpy, Pandas, Keras, Pytorch, DJando, Flask, GIT.

**[ARIOT S.A.C.](https://ariot.pe/)** <span style="float:right">Arequipa, Peru</span>  
*Data Scientist* <span style="float:right">June 2018 - April 2019</span>

* Data Management, modeling, and analyses.
* IT consultant
* **Tech stack**: Python, Numpy, Pandas, MongoDB, MySQL, MATLAB, MQTT, Node-js, GIT.

**[CERNICALO S.A.](https://ariot.pe/)** <span style="float:right">Lima, Peru</span>  
*Web Development Engineer* <span style="float:right">August 2017 - May 2018</span>

* Web and Mobile applications development.  
* **Tech stack**: Laravel, PHP, Java, Android.

Education
======

**[Universidad Católica San Pablo (UCSP)](https://ucsp.edu.pe/)** <span style="float:right">Arequipa - Peru</span>  
**M.Sc. in Computer Science** <span style="float:right">2018 - 2020</span>  
**Thesis**: [Identification and Extraction of Visual Characteristics to Understand the Urban Perception through Street Images]()  
Supervisor: [Prof. Jorge Poco Medina](https://scholar.google.com.br/citations?user=S_88vX4AAAAJ)

**[Universidad Nacional de Ingeniería (UNI)](https://www.uni.edu.pe/)** <span style="float:right">Lima - Peru</span>  
**B.Sc. in Computer Science** <span style="float:right">2012 - 2017</span>  
**Project**: [Design and implementation of the core level of a transversal platform based on Fog Computing architectures]()  
Supervisor: [Prof. Manuel Castillo Cara](https://scholar.google.com.br/citations?user=r0JytwIAAAAJ)

Publications
======
  <ul>{% for post in site.publications reversed %}
    <li>
      <h4 class="archive__item-title" itemprop="headline"> <a href="{{ post.event }}" rel="permalink">{{ post.title }}</a></h4>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
    </li>
  {% endfor %}</ul>

Oral presentations and Poster sessions
======
### Posters  
  <ul>{% for post in site.posters reversed %}
    <li>
      <h4 class="archive__item-title" itemprop="headline"> <a href="{{ post.event }}" rel="permalink">{{ post.title }}</a></h4>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
    </li>
  {% endfor %}</ul>

Skills
======

Category                    | Proficiency in approximate descending order from left to right
--------------------------- | --------------------------------------------------------------
Programming Languages       | C, C++, Go, Python, R, M (Octave/MATLAB), Javascript
Web Technologies            | HTML, CSS/SCSS, Django, VueJS, ReactJS, Flask, BeeGo, Gorilla, Node.js, Angular, Jekyll 
Databases/Storage           | PostgreSQL, MySQL, MongoDB
Data Analysis/Modeling      | Keras, Pytorch, Tensorflow, Pandas, Numpy, Scikit-learn, Beautiful soup, Matplotlib, Seaborn, Scrapy
Cloud                       | AWS (EC2)
Productivity Tools          | LaTeX, GIT, Jupyter/IPython
Software Engineering        | Test-Driven Development: Selenium
Machine Learning Techniques | Clustering, classification/regression, dimensionality reduction.

Languages
======
  * Spanish: Native
  * English: Fluent
  * Portuguese: Intermediate
  * Basic level of Janapese **(JLPT N5)** certified by the Japan Foundation. [PDF Certificate]()

Honors and Awards
======
* Dec 2019: __NeurIPS Travel Grant__ for the Annual Conference on Neural Information Processing Systems.
* June 2019: __ICML Travel Grant__ for the International Conference on Machine Learning.
* Dec 2018: __LXAI Travel Grant__ for the LatinX in AI Workshop  co-located with NeurIPS 2018.
* Nov 2018: __Leaders in Innovation Fellowship__ for the The Royal Academy of Engineering, London, UK.
* May 2018: __Master Fellowship__ for the CONCYTEC and Universidad Católica San Pablo (UCSP).
* July 2017: __Higher Fifth__ of the class of Computer Science. 
* July 2016: __Outstanding Students__ for the Universidad Nacional de Ingeniería (UNI).

Volunteer Work
======
* Director and Co-Founder at Orientate Perú.
* Volunteer in programs like Crea+ and Techo-Peru.
* __Innovation Mentor__ at the technological incubator StartUp UNI, Lima, Perú.
* Member of the University Assembly from 2016 to 2017.
* Member of Student Center from 2012 to 2013.