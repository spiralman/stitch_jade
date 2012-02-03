A Jade plugin for Stitch
========================

A simple plugin for Stitch which allows you to include pre-compiled Jade
templates in your Stitch packages.

Usage
-----

Add a Jade template to your existing Stitch package, with a ".jade"
extension:

    h1 #{title}

Include the stitch_jade plugin in your Express.js server:

    stitch = require('stitch')
    require('stitch_jade').register(stitch)
    
    clientApp = stitch.createPackage()
    
    # etc... 

Call it in your client code:

    myHeader = require('templates/my_header')
    
    $(document).ready( -> 
        $('body').html(myHeader.render(title: "My Page!")) 
    )

Note that the value returned by require is an object with a `render` function,
which is mapped to the anonymous function returned by Jade's compiler.

Details
-------

The server-side `register()` function takes an optional second argument,
which is the options object to pass into `jade.compile()`. The default 
value is `{client: true}`.

If you pass in your own options, you should be careful to include 
`client: true` in the options, if you only want to depend on the client
`runtime.js` library from Jade. 