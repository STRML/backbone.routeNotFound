backbone.routeNotFound
======================

Simple plugin that fires an event to let the application know that no routes matched, so you can fire a custom 404 handler.


Install
-------

Include backbone.routeNotFound after backbone.js and underscore.js.

If you're using any plugins that override Backbone.history.prototype.loadUrl, include this plugin *after* those plugins
to ensure changes to loadUrl are not overwritten.

Usage
-----

A example bit of code to redirect on an invalid route:

```javascript
// router.js

// ...

initialize: function(){
  this.listenTo(Backbone.history, 'routeNotFound', this.onRouteNotFound);
},

onRouteNotFound: function(){
  console.log("Route not found, redirecting...");
  Backbone.history.navigate('', {trigger: true});
}
 
// ...
```