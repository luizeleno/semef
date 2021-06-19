---
layout: default
title: "Programação"
permalink: /programa/
---

<div class="container-md my-2">

<div class="col border m-2 bg-light">

{% for dia in site.data.programa %}

<div class="alert bg-success bg-gradient text-white" role="alert">
  <b>{% include formatdata.html data=dia.data %}</b>
</div>

{% for programa in dia.programacao %}

{% for evento in site.eventos %}

{% if evento.label == programa.evento %}

<div class="card m-3">
  <div class="row g-0">
    <div class="col-md-3">
      <img src="{{site.baseurl}}/img/eventos/{{evento.img}}" class="card-img-top" style="object-fit: contain;">
    </div>
    <div class="col-md-9">
      <div class="card-body">
        <h4 class="card-title">{{evento.nome}}</h4>
        <p><i>{{evento.instituicao}}</i></p>
        <h5>{{programa.horario}}</h5>
        <h5>{{evento.titulo}}</h5>
        {{evento.excerpt}}

        <!-- Button trigger modal -->
        <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#{{evento.label}}{{dia.data}}{{programa.horario}}">
        Launch demo modal
        </button>
        <!-- Modal -->
        <div class="modal fade" id="{{evento.label}}{{dia.data}}{{programa.horario}}" tabindex="-1" aria-labelledby="{{evento.label}}{{dia.data}}{{programa.horario}}Label" aria-hidden="true">
          <div class="modal-dialog modal-xl">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="{{programa.data}}{{programa.horario}}Label">{{evento.nome}}</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
              </div>
            <div class="modal-body">
              <h5>{{evento.titulo}}</h5>
              {{evento.content}}
              <!-- link para o currículo do palestrante -->
              {% if evento.link %}
                <p><a href="{{evento.link}}" class="btn btn-primary" role="button" aria-disabled="true" target="_blank">Sobre o palestrante</a></p>
              {% endif %}
            </div>
            <div class="modal-footer">
              <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Fechar</button>
            </div>
          </div>
        </div>
      </div>
      <!-- End Modal -->
        
      </div>
    </div>
  </div>
</div>

{% endif %}

{% endfor %}

{% endfor %}

{% endfor %}

</div>
</div>