from rest_framework import serializers

from moviecine.models import Movie, Actor


class ActorSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Actor
        fields = ('id', 'nome', 'imagem')


class MovieSerializer(serializers.HyperlinkedModelSerializer):
    atores = ActorSerializer(read_only=True, many=True)

    class Meta:
        model = Movie
        fields = (
            'id', 'titulo', 'titulo_original', 'sinopse', 'imagem', 'duracao', 'publicado', 'slug', 'likes', 'atores')
