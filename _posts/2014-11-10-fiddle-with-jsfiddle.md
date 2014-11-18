---
layout: post
title: Fiddle With jsFiddle
description: "Easy drop in Quick Snippets for retina GitHub Fork Me ribbons."
category: Reference
tags: [reference, code]
author: Katie Ball
comments: true
share: true
---
#####Intro
jsFiddle is an awesome tool for testing, sharing, solving issues and presenting demos and ideas. Here are the basics of using jsFiddle. 
It is divided into few sections: *menu, sidebar, and editing panels*.


####Entering code
One may switch between editing panels using the ``ctrl`` + ``up arrow``
and ``ctrl`` + ``down arrow``.


######HTML
Code entered in this panel will be rendered inside body of the document, 
that is between ``<body>`` and ``</body>``.

.. warning:: 
   Please do not enter ``doctype``, ``body`` etc. into the HTML panel.  These tags are placed automatically.  

######CSS
Code entered in this panel will be placed in the header's style block, 
that is betweeen ``<style>`` and ``</style>``.

.. note::
   If there is a need to edit the header one can use a :ref:`css_panel_hack`


######JavaScript
Code entered in this panel will be placed in header's script block, 
that is between ``<script type="text/javascript">`` 
and ``</script>``.


###Getting Result

.. _result-without-save:

######Result panel

This panel is read only - it contains an iframe with the result of running 
the fiddle. One can show the result without saving the fiddle - it is enough 
to click on :menuselection:`Run` or
hit ``ctrl`` + ``Enter`` key combination

.. _result_draft:

######Draft Page
Only for registered users. Current result is saved in a **draft**. 

One may access it by loading the http://jsfiddle.net/draft/. The shortcut 
is ``ctrl`` + ``shift`` + ``Enter``.

.. note::
   Using Draft is the easiest and probably best way to test fiddle in 
   "other browser". Be it IE5, or anything running on other system, mobile 
   or your watch if it happened to have a web browser. Keep editing on your 
   favourite browser, test on anything else.

   #. Log in to jsFiddle on your favorite browser
   #. Open or create a fiddle
   #. Hit [Run] button
   #. Open the draft page http://jsfiddle.net/draft/ on the other 
      browser/device. It will display the last executed fiddle
   #. Reload the draft page every time you'd like to test



####Saving

Save the code for future usage or to share it to other people. Let me say 
it again: :ref:`There is no need to save if you 
just want to test. <result-without-save>`


######As a new Fiddle
Buttons :menuselection:`Save` or :menuselection:`Fork` are always present 
in the UI. First one appears if no fiddle was loaded, the latter is used 
to create a new fiddle from the existing one.

######As a new Version
If a fiddle is loaded clicking on :menuselection:`Update` will create 
a new version of the fiddle and load it into the browser. Its URL will 
now contain a version number. This and former versions are still available. 

######Setting Base version
If no version is specified jsFiddle will load the base version. By default 
it's the first created version. Owner of the fiddle - user who created 
the first version may change it by clicking on the button 
:menuselection:`Set as Base`.

It is considered a good practice to use base version for 
:ref:`embedded fiddles <embedding>`. Author can fix the error and "update" 
the example on the page without accessing the article's code.

---

####Fiddle Settings (Sidebar)

######Frameworks and Extensions

.. figure:: /_static/screenshots/choose-framework.png
   :align: right                                            
   :figwidth: 270px                                          

Contains 2 selectable lists.

First is the **list of all supported frameworks**. 
Choosing one will create ``<script>`` tag in the ``<head>`` section which 
will load the desired framework version. Choosing the *No-Library* one will 
not load any framework.

Below there is a **list of additional libraries** dependent on currently 
selected framework version. In example - choosing ``MooTools Core 1.2.4`` 
will load a lit containing MooTools More, Clientcide, FormCheck, Upgrade 
Helper and ART. All these may be loaded with the fiddle if checkbox is 
checked.

Second drop-down is about the **Code Wrap** with default setting to "onLoad". 
There are 4 options to choose:

**onLoad**:
   wrap the code so it will run in *onLoad* ``window`` event

**onDomReady**:
   wrap the code so it will run in *onDomReady* ``window`` event

**no wrap - in <head>**:
   *do not wrap* the JavaScript code, place it in ``<head>`` section

**no wrap - in <body>**:
   *do not wrap* the JavaScript code, place it in ``<body>`` section


.. _fiddle_settings-info:



#####Fiddle Options

.. figure:: /_static/screenshots/info.png
   :align: right                                            
   :figwidth: 256px                                          


**Title**:
  will be used in the tittle bar of the jsFiddle. Only fiddles with the 
  title will be displayed in your public fiddle list.

**Description**:
  Please provide a description of the fiddle. It will be displayed in your
  public fiddle list.

.. _normalize_css:
**Normalized CSS**:
  A checkbox, deselected by default. If selected, the fiddle will be rendered 
  with `normalize.css <http://jsfiddle.net/css/normalize.css>`_ which is 
  removing most of the browser styling of many HTML tags.

**Body Tag**:
  One can change the body tag. It is usually done to change the styling as 
  ``<body class="dark_ui">``. Some frameworks (Dojo) are using it to style 
  the widgets and load CSS

**DTD**:
  A choice few useful DTDs is available - HTML5, XHTML (strict, 
  transitional) , HTML4 (strict, transitional, frameset). We aim to not fire
  warning or errors on the syntax checks.

**Framework <script> attribute**:
  An ability to add special attributes to the script tag loading the framework.
  That would result with ``<script type="text/javascript" src="/js/lib/someframework.js" {attributes}></script>``

.. _add_resources:


####External Resources

.. figure:: /_static/screenshots/manage-resources.png
   :align: right                                            
   :figwidth: 253px                                          

CSS or JS (with appropriate extension) which should be loaded after the 
framework. It's a perfect place to put libraries which are framework 
independent, like `RaphaelJS <http://raphaeljs.com>`_

JSFiddle is recognizing the type of the resource by the extension. 
JavaScript will be chosen if type is unknown.

.. note:: 
 If you want to use a dynamic resource please add a dummy GET variable i.e.
 ``http://example.com/dynamically.php?somevar=somevalue&dummy=.css``.
 This will trick jsFiddle to recognize it as CSS resource. 


