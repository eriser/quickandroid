Quick Android - QML Theme and Component Library for Android
===========================================================

Features
--------

 1. Provides “DP” unit
 2. Page transition management
 3. Multiple type “Drawable” component
  1. A single component that supports color , image , QML component , simulated nine patch image as input source
  2. Auto scale image to fit current screen resolution
  3. Derived StateListDrawable for animated drawable like button
 4. Theme / Style Engine
 5. Animation Management

UI Components

    ActionBar , Activity , Application , Drawable , StateListDrawable
    MaterialShadow , PopupMenu , Spinner , QuickButton

Utility Components

    Dialog , DrawableGrowBehaviour, InverseMouseArea ,  PopupArea
    QueuedSignal , RectToRectMatrix , AnimationLoader

Under Development Components

    SwipeViewer , NavigationDrawer

Instruction of use
------------------

 1) Clone this repository and bundle the folder within your source tree.

(It is recommended to use `git subdmoule` to embed this repository)

 2) Add this line to your profile file(.pro):

    include(quickandroid/quickandroid.pri) # You should modify the path by yourself

 3) Modify your main.cpp


```

#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include <QQuickView>
#include "quickandroid.h"

int main(int argc, char *argv[])
{
    QGuiApplication app(argc, argv);

    QQuickView view;

    /* QuickAndroid Initialization */

    view.engine()->addImportPath("qrc:///"); // Add QuickAndroid into the import path
    QuickAndroid::registerTypes(); // It must be called before loaded any scene

    /* End of QuickAndroid Initialization */

    view.setResizeMode(QQuickView::SizeRootObjectToView);
    view.setSource(QUrl(QStringLiteral("qrc:///splash.qml")));
    view.show();

    return app.exec();
}


```

 4) Import the package within your QML file by :

    import QuickAndroid 0.1

Notes of using DP
-----------------

You may get the DP/density value from the global variable "A.dp" after you have called the `QuickAndroid::RegisterTypes()` in your code. However, Qt Creator don't know the value and threfore the UI will be broken. In make it works , you have to declare a dummy data in your project. Check the example code: [dummydata/A.qml](tests/quickandroidexample/dummydata/A.qml)

Demonstration
-------------

Please refer to the example program in the folder of [tests/quickandroidexample](tests/quickandroidexample)

![Screenshot](https://raw.githubusercontent.com/benlau/quickandroid/master/tests/quickandroidexample/docs/screenshot.png)
