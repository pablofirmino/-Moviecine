from django.contrib import admin

# Register your models here.
from moviecine.models import Movie, Actor


def make_published(modeladmin, request, queryset):
    queryset.update(publicado=True)


make_published.short_description = "Mark selected movies as published"


def make_unpublished(modeladmin, request, queryset):
    queryset.update(publicado=False)


make_unpublished.short_description = "Mark selected movies as unpublished"


class ActorInline(admin.TabularInline):
    model = Movie.atores.through
    extra = 3
    classes = ['collapse']
    verbose_name = 'Actor'
    verbose_name_plural = 'Actors'


class MovieAdmin(admin.ModelAdmin):
    list_display = ('titulo', 'titulo_original', 'likes', 'publicado')
    list_filter = ['publicado', ]
    search_fields = ['titulo', 'titulo_original']
    inlines = [ActorInline]
    exclude = ('atores',)
    fieldsets = [
        (None, {'fields': ['titulo', 'titulo_original', 'sinopse', 'imagem', 'duracao', 'publicado']}),
        ('Advanced informations', {'fields': ['ano', 'likes'], 'classes': ['collapse']}),
    ]
    actions = [make_published, make_unpublished]
    list_per_page = 50


admin.site.register(Movie, MovieAdmin)
admin.site.register(Actor)
