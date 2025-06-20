---
layout: post
title: Implementación de navegador
subtitle: Utilizando el motor Chromium para hacer una interfaz con Python.
thumbnail-img: /assets/img/ybb.png
cover-img: /assets/img/ybb.png
share-img: /assets/img/ybb.png
tags: [Python, Chromium, PyQt5, Browser]
author: Pulga
---

{: .box-warning}
Este es un posteo de aprendizaje y de prueba, no debe ser usado como guía técnica y puede estar sujeto a errores.

## Implementando un navegador

Todos los posteos que vi hacían referencia a "hacer un browser", no es tan así... un poco sí... pero no tanto.
La idea es hacer una interfaz gráfica con PyQt5 de Python, y esa interfaz tiene una implementación del Chromium Engine, osea el motor de navegación de Chromium, de forma tal que a través de llamadas a métodos, estan facilitadas muchísimas cosas, y realmente uno sólo debe hacer eso, llamar a los métodos, luego se le puede implementar muchísima lógica, y usar esa estructura gráfica que provee PyQt5 para hacer un navegador mucho más desarrollado.

## Comencemos

Primero debemos crear la ventana principal de la interfaz gráfica.
Para eso está la clase QMainWindow de PyQt. Esta ventana tiene la posibilidad de agregar otras características que usaremos como QToolBar, esto es, una barra de herramientas. Y tiene más que no he utilizado como la QMenuBar, y la QStatusBar.

```py
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow

app = QApplication(sys.argv)
main_window = QMainWindow()
main_window.setWindowTitle("Mi Aplicación")
main_window.show()
```

> Para poder utilizar QMainWindow debe existir QApplication.

También debemos entender la clase QTabWidget que nos permitirá manejar la barra de pestañas.

```py
from PyQt5.QtWidgets import QApplication, QMainWindow, QTabWidget
# En este ejemplo estaríamos creando una barra de pestañas y agregando 2 pestañas a dicha barra.
tabs = QTabWidget()
tabs.addTab(QLabel("Contenido de la pestaña 1"), "Pestaña 1")
tabs.addTab(QLabel("Contenido de la pestaña 2"), "Pestaña 2")
```

Otro elemento usado será el QToolBar, que será la barra de herramientas, donde agregaremos botones, el campo de texto de la URL, y lo que se quiera agregar. Todo lo que se agregue, sean botones, menús desplegables, etc, se le puede generar un QAction, osea una acción. Además de que se le puede definir la ubicación.


```py
from PyQt5.QtWidgets import QApplication, QMainWindow, QTabWidget, QToolBar

toolbar = QToolBar()
action = QAction("Abrir", toolbar)
toolbar.addAction(action)
```

Y por último utilizaremos la clase QWebEngineView que nos permitirá interactuar con la API del motor web de Chromium, de esta forma podremos cargar y motrar páginas web en nuetra implementación.
A esto se le puede sumar, manejo de cookies, bloqueadores de anuncio, etc. En el caso de PachiBrowser crean perfiles de navegación para tener navegación privada.

```py
from PyQt5.QtWebEngineWidgets import QWebEngineView

web_view = QWebEngineView()
web_view.setUrl(QUrl("https://www.google.com"))
web_view.show()
```

Hasta acá tenemos aprox lo siguiente:
![Estructura Qt](/assets/img/qtdiagrama.png)


Ahora comentaremos un poco la implementación de [Snehasish-Konger](https://github.com/Snehasish-Konger/browser/blob/master/main.py), un poco recortada para quitar cosas que sean quizás más complejas.

```py
import sys
from PyQt5.QtCore import *
from PyQt5.QtWidgets import *
from PyQt5.QtWebEngineWidgets import *
from PyQt5.QtGui import QIcon
from PyQt5.QtMultimediaWidgets import QVideoWidget


# Crea una abstracción para la ventana principal que se llamará MainWindow.
class MainWindow(QMainWindow):
    def __init__(self):
        super(MainWindow, self).__init__()

        self.setWindowTitle('PyBro')
        # set a custom icon for the window
        self.setWindowIcon(QIcon('icon.png'))

        # Le agrega a la ventana principal una barra de navegación para pesatañas
        self.tabs = QTabWidget()
        self.tabs.setTabsClosable(True)
        self.tabs.tabCloseRequested.connect(self.close_tab)
        self.setCentralWidget(self.tabs)

        # Agrega la primer pestaña
        self.add_tab()

        # Crea la barra de herramientas
        navbar = QToolBar()
        # Le agrega a la ventana principal la barra de herramientas
        self.addToolBar(navbar)

        # Acá todo será repetitivo y la función lambda puede confundir, pero es crear un botón, suscribirlo al método que nos provee el motor de Chromium y agregarlo a la barra de herramientas. Mediante el método current_browser que indica la pestaña "actual".
        back_btn = QAction('⮜', self)
        back_btn.triggered.connect(lambda: self.current_browser().back())
        navbar.addAction(back_btn)

        forward_btn = QAction('⮞', self)
        forward_btn.triggered.connect(lambda: self.current_browser().forward())
        navbar.addAction(forward_btn)

        reload_btn = QAction('⟳', self)
        reload_btn.triggered.connect(lambda: self.current_browser().reload())
        navbar.addAction(reload_btn)

        # Add a new tab button
        add_tab_btn = QAction('+', self)
        add_tab_btn.triggered.connect(self.add_tab)
        navbar.addAction(add_tab_btn)

        # Agrega la barra de navegación, para escribir las URL.
        self.url_bar = QLineEdit()
        self.url_bar.returnPressed.connect(self.navigate_to_url)
        navbar.addWidget(self.url_bar)
        self.url_bar.setStyleSheet('width: 50%;')
        self.current_browser().urlChanged.connect(self.update_url)
        

    def add_tab(self):
        # Para cada pestaña creada, se crea un QWebEngineView, para poder tener dentro de cada pestaña un motor web, para poder ejecutar js y demás funcionalidades que el motor web provee y luego de crearse se setea como la pestaña actual.
        browser = QWebEngineView()
        browser.setUrl(QUrl('https://google.com'))
        self.tabs.addTab(browser, 'New Tab')
        self.tabs.setCurrentWidget(browser)       

    
    def close_tab(self, index):
        # Para poder cerrar las pestañas se utiliza un método ya hecho que se llama removeTab() que recibe el número de pestaña que se quiere cerrar.
        if self.tabs.count() > 1:
            self.tabs.removeTab(index)

    def current_browser(self):
        return self.tabs.currentWidget()

    def navigate_to_url(self):
        # contruye la url y genera la petición hacia la url colocada.
        url = self.url_bar.text()
        if 'http' not in url:
            url = 'https://' + url
        self.current_browser().setUrl(QUrl(url))
    
    def update_url(self, url):
        # actualiza la url y coloca en puntero de texto en el inicio del campo de texto.
        if self.sender() == self.current_browser():
            self.url_bar.setText(url.toString())
            self.url_bar.setCursorPosition(0)



app = QApplication(sys.argv)
app.setApplicationName('PyBro')
app.setApplicationDisplayName('PyBro')
app.setOrganizationName('PyBro')
window = MainWindow()
window.showMaximized()
app.exec_()
```

Hasta acá el posteo para ver más sobre más implementaciónes y tutoriales dejo las referencias que utilicé. Como se puede apreciar gran parte de la magia sucede a través de la API de Chromium embebida dentro de PyQt, así que muchas cosas no se aprecian el cómo se hacen aunque se puede ver en sus respectivos repos. Por eso este posteo no es de "Como hacer un navegador web" sino una simple implementación en Python, utilizando el motor de Chromium.

Me pareció interesante igual la implementación y el ver como funcionaba, además de que no había utilizado antes PyQt, y de que las formas de utilizar los motores, tanto Chromium o Gecko, etc, requerían otro tipo de entorno, con esto se puede hacer mucho más sencillo a través de Python. Además de que la documentación o implementación, la más accesible es la de Chromium.
Existen varios motores: Gecko, Chromium, Quantum, SpiderMonkey, WebKit, etc. Me hizo investigar y jugar con esto. 

Gracias a @Pachi y a @Snehasish-Konger por documentar y postear al respecto, tomé muchos de los aprendizajes de ahí, en particular quien me motivó a chusmear sobre esto fue el posteo que hizo @Pachi en mastodon, así que queda también citado en las referencias.


![](/assets/img/notbyai-es.svg)

Links de referencia:
1. [Web explicativa de Snehasish-Konger](https://scientyficworld.org/how-to-build-a-browser-using-python/) (*recomiendo*)
2. [Repo de Snehasish-Konger](https://github.com/Snehasish-Konger/browser/)
3. [Otra web explicativa pero del 2021](https://pythongeeks.org/create-web-browser-python-pyqt/)
4. [Tuto de G4G del 2022](https://www.geeksforgeeks.org/python/creating-a-simple-browser-using-pyqt5/)
5. [PachiBrowser repo](https://github.com/SuperSnufkin/PAchi-Web-Browser-) (*recomiendo*)
6. [Posteo de Mastodon de Pachi](https://rebel.ar/@supersnufkin@mastodon.social/114601224483115795)