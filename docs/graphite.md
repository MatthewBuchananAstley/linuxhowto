# Graphite

## Superuser toevoegen

    PYTHONPATH=/opt/graphite/webapp/ django-admin.py createsuperuser --settings=graphite.settings

## Password veranderen

    PYTHONPATH=/opt/graphite/webapp/ django-admin.py changepassword 'username' --settings=graphite.settings
