#jquery.linky.js

This library lets you bind JavaScript objects to HTML elements.

For example:

    var object  = {
      name: "Test Name"
    };
      
    $("#user").linky(object, function(e, data){
      // This gets called when object.change() gets called

      // Render template...
      $(this).empty();
      $(this).append($("#userTmpl").tmpl(data));  
    });

    object.change();
    
    object.name = "Test 2";
    object.change();
    

The `$.fn.linky()` function is just a utility function for tying objects and elements together.  
The example above is equivalent to this:

    var object = {
      name: "Test Name"
    };
    
    // Adds a change event to 'objects'
    $.addChange(object);
    
    var element = $("#users");
          
    object.change(function(){
      element.empty();
      element.append($("#userTmpl").tmpl(this));
    });
    
    object.change();
    
## Why the change() API?

Unfortunately the `change()` API is the only way. JavaScript doesn't have method missing, and getters/setters aren't cross browser.
