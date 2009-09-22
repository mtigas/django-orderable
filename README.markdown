# django-orderable

Adds simple object instance ordering to the Django administration change list.

**Please note that this isn't a fool-proof solution to ordering objects in
every scenario.** However, this app _is_ useful for small applications where
the change list will not be paginated beyond the first page of model
instances. There are a lot of cases where this application isn't the
appropriate solution (at least currently), such as objects that are ordered
with respect to a related object, situations where the list_filter will be
implemented, etc.

## Installation

Installing django-orderable is simple, just complete the following steps:

1. Clone the [django-orderable](http://github.com/tkaemming/django-orderable)
repository from [GitHub](http://www.github.com/).
2. Add the "orderable" directory to your PYTHONPATH.
3. Add "orderable" to the INSTALLED_APPS tuple for your Django project.
4. Add the following line to your URLconf: 
   `(r'^admin/order/', include('orderable.urls'))`.
5. For any models that you would like to be ordered through the change list, 
   have these models extend `orderable.models.Orderable`, and have their admin
   objects implement or extend `orderable.admin.OrderableAdmin`.
6. Make sure that in your ModelAdmin, the `list_per_page` attribute is set 
   to a value that is greater than the possible number of objects (this 
   attribute defaults to 100). If you're looking to order an inordinate number
   of model instances, you should probably be looking elsewhere for your 
   ordering solution.