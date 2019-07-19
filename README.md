### django-pipeline
---
https://github.com/jazzband/django-pipeline

```py
from django import forms
from pipeline.forms import PipelineFormMedia

class MyForm(forms.Form):
  class Media(PipelineFormMedia):
    css_packages = {
      'all': ('my-styles',)
    }
    js_packages = ('my-scripts',)
    js = ('https://cdn.example.com/some-script.js')

STATICFILES_STORAE = 'pipeline.storage.PipelineStorage'

STATIUCFILES_STORAGE = 'pipeline.storage.PipelineCachedStorage'

MIDDLEWARE_CLASS = (
  'django.middleware.gzip.GZipMiddleware',
  'pipeline.middleware.MinifyHTMLMiddleware',
)

```

```sh
pip install django-pipeline
python manage.py collectstatic
```

```
{% load pipeline %}
{% stylesheet 'colors' %}
{% stylesheet 'stats' %}
{% javascript 'scripts' %}
```

```
{
  'BACKEND': 'django.template.backends.jinja2.Jinja2',
  'DIRS': [],
  'APP_DIRS': True,
  'OPTIONS': {
    'environment': 'myproject.jinja2.environment',
    'extensions': ['pipeline.jinja2.PipelineExtension']
  }
}
```
