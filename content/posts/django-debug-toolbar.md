---
title: "Django Debug Toolbar"
date: 2019-12-25T22:32:02-06:00
disqus: false
---
I'm not that well versed in front-end land so I will take all the help I can get when it comes to building out internal tools at Winnie. The people over at Jazzband have developed an awesome tool called <a href="https://github.com/jazzband/django-debug-toolbar" target="_blank">Django Debug Toolbar</a>. This tool shows up alongside your Django application and you can see what view was requested, what set of templates were rendered, etc.

I had some issues getting the toolbar to work but I eventually landed on a solution after playing around with the Django settings. Here are the settings that worked for me:

```python
MIDDLEWARE += [
    'debug_toolbar.middleware.DebugToolbarMiddleware',
]

INSTALLED_APPS += [
    'debug_toolbar',
]

DEBUG_TOOLBAR_PANELS = [
    'debug_toolbar.panels.versions.VersionsPanel',
    'debug_toolbar.panels.timer.TimerPanel',
    'debug_toolbar.panels.settings.SettingsPanel',
    'debug_toolbar.panels.headers.HeadersPanel',
    'debug_toolbar.panels.request.RequestPanel',
    'debug_toolbar.panels.sql.SQLPanel',
    'debug_toolbar.panels.staticfiles.StaticFilesPanel',
    'debug_toolbar.panels.templates.TemplatesPanel',
    'debug_toolbar.panels.cache.CachePanel',
    'debug_toolbar.panels.signals.SignalsPanel',
    'debug_toolbar.panels.logging.LoggingPanel',
    'debug_toolbar.panels.redirects.RedirectsPanel',
    'debug_toolbar.panels.profiling.ProfilingPanel',
]

DEBUG_TOOLBAR_CONFIG = {
    'SHOW_TOOLBAR_CALLBACK': lambda _request: DEBUG,
}
```

![Django Debug Toolbar](/django-debug-toolbar.png)

Voila!

## Some helpful links
* https://github.com/jazzband/django-debug-toolbar/issues/1054#issuecomment-388810109
* https://stackoverflow.com/a/27323534
