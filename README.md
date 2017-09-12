# AJAX

Simple AJAX javascript object for use when you do not want (or can not) use any framework or library that has built-in AJAX functionality.

# API
to be continued...

Constructor
    
    var Ajax = new AJAX_(DefaultErrorHandler, DefaultParser, DefaultSplashScreen);

        where:
        
        DefaultErrorHandler (function, optional) - defines a function to be used as error handler by default 
            (further calls to GET and POSt methods can redefine error handler for particular call). 
            The function receives a string with error message (see below), when called. 
            If omitted, null or false - the built-in error handler is used (just alert(error message)).
        
        DefaultParser (function, optional) - defines a function for parsing (decoding/converting) a server 
            message before transferring the message to the callback function.  
            If omitted, null or false - the built-in parser is used. The built-in parser treats server message 
            as JSON string and tries to restore (unserialise) an object or array from the string. 
            Restored object is passed then to the callback function. If unserialization fails the error handler
            is called with appropriate error message and the parser returns false.
        
        DefaultSplashScreen (function, optional) - defines a function for showing a splash screen or animation 
            or somthing alike to the user while waiting responce from server. 
            If omitted, null or false - the built-in splash screen (dimmed layer over the whole window which 
            contained the Ajax object definition) is used. 
            When is called, the function receives integer representing the current state of connection. 
            The recognised states are:
              0 - Initialisation;
              1 - Establising connection;
              2 - Sending a request;
              3 - Receiving data;
              4 - Complited;
              5 - Error occured;

Metods
    
   The object has two methods corresponded to HTTP methods GET and POST.
   
   .GET(url, Callback, SplashScreen, Parser, ErrorHandler)
   
   .POST(url, dat, Callback, SplashScreen, Parser, ErrorHandler)
   
        where:
        
        url (string) - URL for request according to HTTP specs. Can be absolute or relative.
        
        dat (string) - Data for POST request according to HTTP specs (urlencoded).
        
        Callback (function, optional) - function which receives control after server response to the request. 
            The function receives parsed server response. 
            If the Parser is disabled when the method is called (see below), the function receives raw server 
            response as string. If omitted, null or false - nothing happens.
        
        SplashScreen (function/boolean/any, optional) - allows to redefine or disable DefaultSplashScreen 
            for particular request.
            If function - the function is used instead of DefaultSplashScreen.
            If omitted null or false the DefaultSplashScreen is used.
            in any other case splash screen is disabled (silent mode).
   
   

