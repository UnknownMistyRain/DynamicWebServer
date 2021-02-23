========
HanaShirosaki
========

:SourceCode:    `GitHub <https://github.com/SagiriPillow/HanaShirosaki>`
:BasedOn:     `Flask <https://github.com/pallets/flask>`

What is it ?
----
This is a Web server that implements dynamic pages by replacing content retained by static pages.

How can I use it ?
----


1.Import this module

    import HanaShirosaki as hs

2.Create a server object

    server = hs.Server('ServerName', identifiers = '%')
3.Create a method and add a page

    def user(args):
       return args['user']
    server.addPage('Hi %user%', '/', {'user':user}, ['get', 'post'])

4.Start the server

    server.start(80, '0.0.0.0')

5.Wait for the server to start and visit your site

    localhost/?user=SagiriPillow

6.It shows that

    Hi SagiriPillow
