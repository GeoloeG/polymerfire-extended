# akc-meta

## Introduction

**akc-meta** and **akc-meta-query** are a pair of Polymer webcomponents that enable across DOM communication.  **akc-meta** is used to inject a *value* (value is a property of the elements) into global storage, whilst one or more **akc-meta-query** elements are used to read the value out again.

Values in global storage are accessed via  a *key* (again an element property) provided to the elements as strings. Values can be of any type including Object. 

## Changes to Values

Changes to values provided to the akc-meta value property are propogated to all related akc-meta-query elements, which in turn are "notified" to any data binding that may be attached to them.

## Changes to Keys

If an element changes the value of its key, then the value associated with it is re-evaluated.  For akc-meta elements, the values associated with the old key are either set to {} (where query elements are still looking at it) 0r deleted from global storage (where no query element is viewing it).  For akc-meta-query elements a key change will result in the value for the new key being notified.

##A Use Case

I am building a single page application with lots of different pages, each of which will be a bespoke element.  In order to support page routing and (using the Page.js routing library) I have built a "PageBehavior" behavior which is to be including on each page.  When a particular route url is selected, the behavior on the appropriate page calls a callback which then needs to reflect the route to a controlling element, so *neon-animated-pages* can be told which page to select.

Without something like this element, every page element in index.html would have to be decorated with a large number of parameters, just so they could be databound at the app level, to pass up the dom tree and then down to the *page-controller* element.

With **akc-meta** we can embed one of more of these elements inside each page custom element to publish the key information about itself and the selected route after a page request.  The *page-controller* element would have matching **akc-meta-query** elements to read out this information and tell *neon-animated-pages* accordingly. 

So looking at the relevant components of the application

###index.html

```html
<template id="app" is="dom-bind">
   <!--a lot more stuff, such as header panel and toolbar -->
    <page-controller>
        <!-- different elements as pages -->
        <page-menu></pas-menu>
        <page-appointments></pas-appointments>
        <page-users></pas-users>
        <page-reports></pas-reports>
<!-- Add More as we add functionality -->

      </page-controller>
  </template>
```

###page-controller.html

```html
<dom-module id="page-contoller">
  <template>
    <style>
  
    </style>
    <!-- query meta for external data -->

    <akc-meta-query key="page" value="{{page}}"></akc-meta-query>
    <neon-animated-pages
        class="fit"
        selected="[[route]]"
        attr-for-selected="route"
        entry-animation="scale-up-animation"
        exit-animation="fade-out-animation">
        <content></content>
    </neon-animated-pages>
  </template>
  <script>
  Polymer({
    is:'page-controller',
    properties : {
        page:{
            type:object,
            observer:'_pageChanged'
        },
        route:{
            type:String,
            notify:true
        }

    },
    _pageChanged:function() {
        this.route = page.route
    }
  });
  </script>  
</dom-module>
```

### page-menu

```html
<dom-module id="page-menu">
    <template>
        <akc-meta key="page" value="[[page]]"
        <!-- much more content -->
    </template>
    <script>
        Polymer({
            is:'page-menu',
            behaviors:[PageBehavior],
            properties:{
                route: {
                    type:String,
                    readOnly:true,
                    value:'menu',
                },
                path: {
                    type:String,
                    value:'/',
                    readOnly:true
                },
                base:{
                    type:String,
                    readOnly:true,
                    value:''
                }

            },
            _onRouteFired:function(ctx) {
//Do stuff when page selected
            }
        });
    </script>
</dom-module>
```

### PageBehavior

This imports the page.js library 

```javascript
  PageBehaviour = {
    properties: {
      page: {
        type: Object,
        notify:true
      },
      base: {
        type:String,
        value:''
      }
    },
    attached: function() {
      page.base(this.base);
      page(this.path,this._routeFired.bind(this));
      console.log('setting a page route of ' + this.path);
    },
    _routeFired: function(ctx) {
      console.log(this.menu + ' route fired');
      this.page = {route:this.route,path:this.path,base:this.base};
      this._onRouteFired(ctx);
    },
    _onRouteFired(ctx) {
      //abstract
    }

  };
