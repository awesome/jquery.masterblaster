---
layout: index
---

Requirements
----
Tested with: [jQuery 1.9.1](http://jquery.com)

Examples
----
<input class="masterblaster-1" />
{% highlight javascript %}
var $mb = $( ".masterblaster-1" );
$mb.masterblaster( { 
  tagRules: {
    unique: true,
    minLength: 3
  }
} );
$mb.masterblaster( "push", "tag 1" );
$mb.masterblaster( "push", "tag 2" );
$mb.on( "mb:add", function( e, tagName ) {
    console.info( "Added: tagName" );
} );  
$mb.on( "mb:remove", function( e, tagName ) {
    console.info( "Removed: tagName" );
} ); 
{% endhighlight %}

<script>
var $mb = $( ".masterblaster-1" );
$mb.masterblaster( { 
  tagRules: {
    unique: true,  
    minLength: 3
  }
} );
$mb.masterblaster( "push", "tag 1" );
$mb.masterblaster( "push", "tag 2" );
$mb.on( "mb:add", function( e, tagName ) {
    console.info( "Added: tagName" );
} );  
$mb.on( "mb:remove", function( e, tagName ) {
    console.info( "Removed: tagName" );
} );  
</script>


Configuration
----
------
####animate
Animate the addition or removal of a tag.
######Default
true

-----
####triggerKeys
Hotkeys user may use to enter a tag.
######Default
[ 9, 13 ] //tab and enter

-----
####showAddButton
#####Default
true

-----
####helpText
######Default
"Hit Tab or Enter to add"

-----
####tagRules
#####unique
Tags must be unique to be added.
######Default
false
#####minLength
Minimum character length a tag must be.
######Default
null

-----
Events
----
####mb:add
Occurs on addition of tag through any means (user insert or programmatically through the api).

{% highlight javascript %}
var $mb = $( ".masterblaster-1" );
$mb.masterblaster( );
$mb.push( "tag 1" );
$mb.on( "mb:add", function( e, tagName ) {
    console.info( tagName );
} );
{% endhighlight %}

####mb:remove
Occurs on removal of tag through any means (user insert or programmatically through the api). If multiple tags of the same name are added and are removed using *remove* api the event will still be called only once.

{% highlight javascript %}
var $mb = $( ".masterblaster-1" );
$mb.masterblaster( );
$mb.push( "tag 1" );
$mb.remove( "tag 1" ); //or $mb.pop( );
$mb.on( "mb:remove", function( e, tagName ) {
    console.info( tagName );
} );
{% endhighlight %}

API
-----------
####push(tagName)
Add tagName to the end of the list.
####pop( )
Removes last tag.
####remove(tagName)
This will remove *all* tags tagName.
####destroy()
Destroy/cleanup instance of plugin.

Tests
--------------
For tests, go **[here](/jquery.masterblaster/tests)**.
    