from django.urls import path

from . import views

app_name = 'moviecine'
urlpatterns = [
    path('', views.IndexView.as_view(), name='index'),
    path('<int:pk>/', views.DetailView.as_view(), name='detail'),
    path('<slug:slug>/', views.DetailView.as_view(), name='detail'),
    path('<int:movie_id>/like/', views.likeId, name='likeId'),
    path('<slug:slug>/like/', views.likeSlug, name='likeSlug'),
]
