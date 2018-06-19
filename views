from django.http import HttpResponseRedirect
from django.shortcuts import get_object_or_404
from django.urls import reverse
from django.views import generic
from rest_framework import viewsets
from rest_framework.reverse import reverse

from moviecine.models import Movie, Actor
from moviecine.serializers import MovieSerializer, ActorSerializer


class ActorViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows groups to be viewed or edited.
    """
    queryset = Actor.objects.all()
    serializer_class = ActorSerializer


class MovieViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows groups to be viewed or edited.
    """
    queryset = Movie.objects.all()
    serializer_class = MovieSerializer
    lookup_field = 'slug'

class IndexView(generic.ListView):
    template_name = 'moviecine/index.html'
    context_object_name = 'movie_list'
    paginate_by = 25

    def get_queryset(self):
        """
        Return the last five published questions (not including those set to be
        published in the future).
        """
        order = self.request.GET.get('orderby', 'titulo')
        return Movie.objects.filter(publicado=True).order_by(order)


class DetailView(generic.DetailView):
    model = Movie
    template_name = 'moviecine/detail.html'

    def get_queryset(self):
        """
        Excludes any questions that aren't published yet.
        """
        return Movie.objects.filter(publicado=True)


def likeId(request, movie_id):
    movie = get_object_or_404(Movie, pk=movie_id)
    movie.likes += 1
    movie.save()
    # return HttpResponseRedirect(request, 'moviecine/detail.html', args=(movie_id,))
    return HttpResponseRedirect(reverse('moviecine:index') + '?orderby=-likes')


def likeSlug(request, slug):
    movie = get_object_or_404(Movie, slug=slug)
    movie.likes += 1
    movie.save()
    # return HttpResponseRedirect(request, 'moviecine/detail.html', args=(movie_id,))
    return HttpResponseRedirect(reverse('moviecine:index') + '?orderby=-likes')
