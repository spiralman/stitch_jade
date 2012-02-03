A Jade plugin for Stitch
========================

A simple plugin for Stitch which allows you to include pre-compiled Jade
templates in your Stitch packages.

Usage
-----

Add a Jade template to your existing Stitch package, with a ".jade"
extension:

    html
        body
        h1 #{title}

Include the stitch_jade plugin in your Express.js server:

    stitch = require('stitch')
    require('stitch_jade').register(stitch)
    
    clientApp = stitch.createPackage()
    
    # etc... 

Call it in your client code:

    page = require('templates/my_page')
    
    $(document).ready( -> 
        $(document).html(page.render(title: "My Page!")) 
    )
    
Details
-------

The server-side register() function takes an optional second argument,
which is the options object to pass into jade.compile(). If you pass
nothing in, it will pass {client: true}.
