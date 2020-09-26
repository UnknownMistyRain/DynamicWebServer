"""
========
DynamicWebServer
========

:SourceCode:    `GitHub <https://github.com/UnknownMistyRain/DynamicWebServer>`
:License:     `MIT <https://github.com/UnknownMistyRain/DynamicWebServer/blob/master/LICENSE>`
:BasedOn:     `Flask <https://github.com/pallets/flask>`
"""

import flask


class Server:
    def __init__(self, name: str = 'Page', port: int = 80, hostname: str = '0.0.0.0', identifiers: str = '*'):
        self.n = name
        self.s = flask.Flask(self.n)
        self.p = port
        self.h = hostname
        self.i = identifiers

    def addPage(self, source: str, path: str = '/', functions: dict = None, methods: list = None):
        if methods is None:
            methods = ['get', 'post']

        @self.s.route(path, methods=methods)
        def method():
            if functions is None:
                return source
            else:
                a = flask.request.args
                c = source
                for k, v in functions.items():
                    f = functions[k]
                    r = f(a)
                    c = c.replace(self.i + k + self.i, r)
                return c

    def start(self, port: int = None, hostname: str = None):
        if port is None:
            port = self.p
        if hostname is None:
            hostname = self.h
        self.s.run(port=port, host=hostname)
