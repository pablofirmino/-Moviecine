{% load staticfiles %}

<html>
<head>
    <!--Import materialize.css-->
    <link type="text/css" rel="stylesheet" href="{% static 'materialize/bin/materialize.css' %}"
          media="screen,projection"/>
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">

    <style>
        ul.tabs li.tab {
            padding: 0 15px;
            width: auto !important;
        }
        .tabs li.tab a {
            color: rgba(255, 255, 255, 0.7);
        }
        .tabs li.tab a:hover {
            color: rgba(255, 255, 255, 0.9);
        }
        .tabs .tab a:hover, .tabs .tab a.active {
            background-color: transparent;
            color: white;
        }
        .tabs .indicator {
            height: 5px;
            background-color: white;
        }
        form {
            margin: 0;
        }
        .card .card-image {
            background: no-repeat center center;
            background-size: cover;
            overflow: hidden;
        }
        .card .card-image img {
            min-height: 100%;
            min-width: 100%;
            /* IE 8 */
            -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=0)";
            /* IE 5-7 */
            filter: alpha(opacity=0);
            /* modern browsers */
            opacity: 0;
        }
        .btn-floating.btn-large.halfway-fab {
            bottom: -28px;
        }
        .btn-floating.halfway-fab {
            position: absolute;
            right: 24px;
            bottom: -20px;
        }
    </style>
</head>
<body>

<div class="container">

    <div class="row" style="margin-top: 20px;">

        <div class="card" style="margin: 0;">
            <div style="background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url({{ movie.imagem.url }});
                    background-image: -moz-linear-gradient(top, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url({{ movie.imagem.url }});
                    background-image: -o-linear-gradient(top, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url({{ movie.imagem.url }});
                    background-image: -ms-linear-gradient(top, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url({{ movie.imagem.url }});
                    background-image: -webkit-gradient(linear, left top, left bottom, from(rgba(0, 0, 0, 0.7)), to(rgba(0, 0, 0,
                    0.7))), url({{ movie.imagem.url }});
                    background-image: -webkit-linear-gradient(top, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)),
                    url({{ movie.imagem.url }}); background-position: center center; background-repeat: no-repeat;background-size: cover; position: relative;">
                <div class="card-content">
                    <div class="row" style="position: relative;">
                        <img class="col s2"
                             src="{{ movie.imagem.url }}"
                             style="max-height: 100%; max-width: 100%;"/>

                        <div class="row col s10 offset-s2"
                             style="margin-bottom: 0; font-weight: 500; position: absolute; bottom: 0; color: white;">
                            <h4 class="col s12" style="margin-bottom: 0;">{{ movie.titulo }}</h4>

                            <h6 class="col s12" style="margin-bottom: 0;">({{ movie.ano }})</h6>
                        </div>
                    </div>
                </div>
                <div class="card-tabs container" style="background: transparent; margin: 0;">
                    <ul class="tabs tabs-fixed-width" style="background: transparent;">
                        <li class="tab" style="background: transparent;"><a class="active" href="#overview">Visão
                            geral</a>
                        </li>
                        <li class="tab" style="background: transparent;"><a href="#casting">Elenco</a>
                        </li>
                    </ul>
                </div>

                <form action="{% url 'moviecine:likeSlug' movie.slug %}" method="post">
                    {% csrf_token %}
                    <button type="submit" class="btn-floating btn-large halfway-fab waves-effect waves-light pink"
                            style="margin: 0;">
                        <i class="material-icons">thumb_up</i>
                    </button>
                </form>
            </div>

            <div class="card-content grey lighten-4" style="padding: 25px 20px;">
                <div id="overview">
                    <div class="row" style="padding: 0 1.5rem;">
                        <span class="col s6"
                              style="color:#4A4A4A;">Original Title: <strong>{{ movie.titulo_original }}</strong></span>
                        <span class="col s3" style="color:#4A4A4A; border-left: 1px solid #979797">{{ movie.duracao }} seconds</span>
                        <span class="col s3"
                              style="color:#4A4A4A; border-left: 1px solid #979797"><strong>{{ movie.likes }}
                            {% if movie.likes == 0 or movie.likes > 1 %} likes {% else %}
                                like {% endif %}</strong></span>
                    </div>

                    <div class="divider" style="background-color: #979797;"></div>

                    <div class="row" style="margin-top: 20px;">
                        <div class="col s12">
                            <p style="padding: 0 1.5rem; white-space: pre-wrap">{{ movie.sinopse }}</p>
                        </div>
                    </div>
                </div>
                <div id="casting">
                    <div class="row">
                        {% if movie.atores %}
                            {% for ator in movie.atores.all %}
                                <div class="col s6 m3 l3">
                                    <div class="card">
                                        <div class="card-image" style="background-image: url({{ ator.imagem.url }})">
                                            <img src="https://images-na.ssl-images-amazon.com/images/G/01/imdb/images/nopicture/medium/name-2135195744._CB514893537_.png">
                                        </div>
                                        <div class="card-content">
                                            <p style="display: block; white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">{{ ator.nome }}</p>
                                        </div>
                                    </div>
                                </div>
                            {% endfor %}
                        {% else %}
                            <p>No actors are available.</p>
                        {% endif %}
                    </div>
                </div>
            </div>
        </div>

    </div>

</div>

{% block footer %}
    <script type="text/javascript" src="https://code.jquery.com/jquery-2.1.1.min.js"></script>
    <script type="text/javascript" src="{% static 'materialize/bin/materialize.js' %}"></script>
    <script>
        $(document).ready(function () {
            $('ul.tabs').tabs();
        });
    </script>
{% endblock %}

</div>
</body>
</html>
