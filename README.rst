========
DynamicWebServer
========

:SourceCode:    `GitHub <https://github.com/UnknownMistyRain/DynamicWebServer>`
:License:     `MIT <https://github.com/UnknownMistyRain/DynamicWebServer/blob/master/LICENSE>`
:BasedOn:     `Flask <https://github.com/pallets/flask>`

What is it ?
----
This is a Web server that implements dynamic pages by replacing content retained by static pages.

How can I use it ?
----


1.Import this module

    import dynamicwebserver as dws

2.Create a server object

    server = dws.Server('ServerName', identifiers = '*')

3.Create a method and add a page

    def user(args):
       return args['user']
    server.addPage('Hi *user*', '/', {'user':user}, ['get', 'post'])

4.Start the server

    server.start(80, '0.0.0.0')

5.Wait for the server to start and visit your site

    `Site <localhost/?user=UnknownMistyRain>`
