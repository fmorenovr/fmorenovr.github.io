---
permalink: /about/
title: ""
author_profile: true
redirect_from: 
  - /about-me/
---

I am a Machine Learning Researcher in the [Escola de Matemática Aplicada (EMAp)](https://emap.fgv.br/) at the [Fundação Getúlio Vargas (FGV)](https://portal.fgv.br/), while also working as a part-time R&D engineer at a startup (Didius) and as a teaching assistant at my university. 

My research lies at the intersection of **Urban Perception**, **Deep Learning**, and **Interpretability Machine Learning**. I am especially interested in building efficient, and robust models that can perform analyzing, and understanding human perception from street images with or without associated description text to improve the identification of the visual components, and main perceptual features extraction for applications in urban computing.

## About me

I am doing a M.Sc. in Computer Science from the [Centro de Investigación e Innovación en Ciencia de la Computación (RICS)](http://rics.ucsp.edu.pe/) in the [Programa de Maestría en Ciencia de la Computación](http://rics.ucsp.edu.pe/mcs/index.html) at the [Universidad Católica San Pablo (UCSP)](http://ucsp.edu.pe/) with the [CONCYTEC](https://portal.concytec.gob.pe/) scholarship, Arequipa, PERU (2018-2020), and a B.Sc. in Computer Science from the [Facultad de Ciencias (FC)](https://fc.uni.edu.pe/fc/) in the [Escuela Profesional de Ciencia de la Computación (EPCC)](https://fc.uni.edu.pe/fc/index.php/escuelas/ciencia-de-la-computacion) at the [Universidad Nacional de Ingeniería (UNI)](https://www.uni.edu.pe/) with the [PRONABEC](https://www.pronabec.gob.pe/) scholarship, Lima, PERU (2012-2017).

Furthermore, I have worked as _Research Assistant_ in the [Big Data & HPC Lab](https://www.ctic.uni.edu.pe/index.php/laboratorios/bigdata-hpc) at the [Centro de Tecnologías y Comunicaciones (CTIC)](https://www.ctic.uni.edu.pe/) in fields like **Big Data**, **High-Performance Computing**, and **Fog Computing**. Also, as a part of my professional life, I have worked in [CERNICALO S.A.](http://cernicalo.net/) as a _Web Development Engineer_ in 2017 and [ARIOT S.A.C.](https://ariot.pe/) as _Software Engineer_ in 2018. In addition, I am a current _Professional Fellow_ at [The Royal Academy of Engineering (RAEng)](https://www.raeng.org.uk/), London, UK since 2018.

Would you like to see my CV ? Press [Here](/cv).

## Get in touch

<style>
td, th, tr, table {
  padding: 0.5em;
  border: 1px solid #ccc;
  border: 1px;
}
</style>

<table style="width:100%">
  <tr>
    <th style="width:40%; height:60%"> <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3674.2418260507848!2d-43.18245298564607!3d-22.941319444870363!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x997f8c868f2667%3A0xfd19f999080c93ca!2sFundaci%C3%B3n%20Getulio%20Vargas!5e0!3m2!1ses!2sbr!4v1581513248112!5m2!1ses!2sbr" frameborder="0" style="border:0;" allowfullscreen=""></iframe> </th>
    <td align="center">
    <h2 class="archive__item-title" itemprop="headline"> Fundação Getúlio Vargas (FGV) </h2>
    <p> Tel.: +55 (21) 3799-5711 <br>
    Praia de Botafogo, n° 190 – 5º andar <br>
    Botafogo - Rio de Janeiro, RJ - CEP:22250-900 </p>
    </td>
  </tr>
</table>

### Social Networks

{% if page.author and site.data.authors[page.author] %}
  {% assign author = site.data.authors[page.author] %}{% else %}{% assign author = site.author %}
{% endif %}

<p> 
{% if author.linkedin %}
  <a href="https://www.linkedin.com/in/{{ author.linkedin }}"><i class="fab fa-fw fa-linkedin" aria-hidden="true"></i></a>
{% endif %}
{% if author.facebook %}
  <a href="https://www.facebook.com/{{ author.facebook }}"><i class="fab fa-fw fa-facebook-square" aria-hidden="true"></i></a>
{% endif %}
{% if author.instagram %}
  <a href="https://instagram.com/{{ author.instagram }}"><i class="fab fa-fw fa-instagram" aria-hidden="true"></i></a>
{% endif %}
{% if author.twitter %}
  <a href="https://twitter.com/{{ author.twitter }}"><i class="fab fa-fw fa-twitter-square" aria-hidden="true"></i></a>
{% endif %}
</p>

