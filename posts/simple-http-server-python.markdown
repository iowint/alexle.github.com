How To Setup A Simple HTTP Server With Python
02-09-2012

There are times when you need to setup a quick web server to test your web applications. For basic applications that don't require database or server-side language support, Python has a [module][1] to run a mini web server on your system. It takes no time to configure and eats up very little system resources!

###SimpleHTTPServer by command line###

Open up a terminal and go to the directory you would like to start the web server:

> $ cd /home/somedirectory

To start the server, simply type:

> $ python -m SimpleHTTPServer

That's it! Now your HTTP server will run in port 8000. You can access it via [localhost:8000](http://localhost:8000/) or [127.0.0.1:8000](http://127.0.0.1:8000/). If the directory has a file named "index.html", that file will be served as the initial file. If there is no "index.html", then the files in the directory will be listed. To quit the web server, use CTRL+C.

If you wish to change the port, it can be configured as an additional parameter:

> $ python -m SimpleHTTPServer 8200

###SimpleHTTPServer by python script###

The SimpleHTTPServer can also be started in a script. Here's a snippet of the code I use:

<div id="code">
<font color="#cd5c5c">import</font>&nbsp;sys, SimpleHTTPServer, BaseHTTPServer<br>
<font color="#cd5c5c">from</font>&nbsp;SimpleHTTPServer <font color="#cd5c5c">import</font>&nbsp;SimpleHTTPRequestHandler<br>
<br>
SimpleHTTPRequestHandler.protocol_version = <span style="background-color: #333333"><font color="#ffffff">&quot;</font></span><font color="#ffa0a0">HTTP/1.0</font><span style="background-color: #333333"><font color="#ffffff">&quot;</font></span><br>
<br>
httpd = BaseHTTPServer.HTTPServer((<span style="background-color: #333333"><font color="#ffffff">'</font></span><font color="#ffa0a0">127.0.0.1</font><span style="background-color: #333333"><font color="#ffffff">'</font></span>, 8000), SimpleHTTPRequestHandler)<br>
<br>
sa = httpd.socket.getsockname()<br>
<br>
<font color="#f0e68c"><b>print</b></font>&nbsp;<span style="background-color: #333333"><font color="#ffffff">&quot;</font></span><font color="#ffa0a0">Serving HTTP on</font><span style="background-color: #333333"><font color="#ffffff">&quot;</font></span>, sa[0], sa[1], <span style="background-color: #333333"><font color="#ffffff">&quot;</font></span><font color="#ffa0a0">...</font><span style="background-color: #333333"><font color="#ffffff">&quot;</font></span><br>
<br>
httpd.serve_forever()<br>
</div>

And there you go. Happy web serving!

[1]: http://docs.python.org/library/simplehttpserver.html
