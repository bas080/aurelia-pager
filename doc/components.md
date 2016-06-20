#Components

## pager

A simple pager that has the following bindables with the fitting default values


**page** defaults to the 1st page. This is a two-way bindable property which
allows the pager to communicate to the view model what page was selected. Is is
as simple as adding a `<prop>Changed` method to your view model.

**range** are the numbers amount of numbers visible from the left and right of
the current selected number. The default is `3`;

If i would set the range to two i would see the following

> the page is somewhere in the middle of the pages
`3  4  [5]  6  7`

> the page cannot be smaller
`[1] 2  3  4  5`

Now for an example where range is set to 3.

> somewhere in the middle again
`2  3  4  [5]  6  7 8`

> completely to the left
`[1] 2  3  4  5  6  7`


**pages** are the amount of pages a user can select from. This property can
either be set by you or calculated from the data you provide it. It is
a one-way bindable

**data** is there for your convenience. You can use both pages and data, but it
is adviced to use one of them at a time. What the data bindable allows is for
you to pass a thing with length method. This length method is called to
calculate how many properties should be shown. *experimental*

Now for a simple example for a simple component

```js

    <pager
      range.bind="5"
      pages.bind="20"
      page.bind="page">
    </pager>

```

## resource-pager (orm)

Aurelia-orm enables you to communicate with api's in a way that is quite
powerfull. The `resource-pager` enables you to leverage it. If you do not use
aurelia-orm you can ignore this component.

`resource-pager` takes the following bindables.

**repository** is an instance of the a Repository

**resource** is a string that is transformed into a repository

**limit** will set the amount of items on a page and will be used to calculate
the amount of pages, default is 30.

**criteria** bindables only works when `resource` is enabled and comes from the DB.
Parameter gets passed straight to the query field of `.count()`.

Example (sailsjs/waterline or express):

```javascript:
{
  disabled : 0,
  createdAt: {'>', '2016-01-01'}
}
```


Furthermore it shares the following bindables with the `pager` component.

**page**

**range**

**note:** it does not have the `pages` bindable. The number of pages is
determined by the return value of calling repository.count().

> example

```js

  <resource-pager
    resource="user">
  </resource-pager>

  <!-- or -->

  <resource-pager
    repository.bind="vm.userRepository">
  </resource-pager>

```

