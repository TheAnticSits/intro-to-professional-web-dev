Angular First Steps
====================

The goal here is to create a minimum working webpage template. It will serve as
a jumping off point for your later exercises and studios, so be sure you are
logged into your GitHub account.

Starting a New Project
-----------------------

First, navigate to the `StackBlitz homepage <https://stackblitz.com>`__.

Next, click "Start New App", then select the "Angular (TypeScript)" option.

.. figure:: ./figures/StackBlitzHome.png
   :alt: StackBlitz homepage selections.

Examine the Files Created
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: ./figures/NewProjectFiles.png
   :alt: File tree for new StackBlitz Angular project.

#. The ``src`` folder holds the files and source code needed for the project.
#. The ``app`` folder holds the content for the webpage. Although the page is
   treated as a single entity, it actually consists of multiple pieces. ``app``
   holds these different parts and establishes links between them. We will
   modify some of these files soon.
#. ``index.html`` is the highest level for displaying content. Anything added
   to this HTML file will appear on every page within a website.
#. ``main.ts`` imports the core methods required to make everything work. It
   also imports the content from the ``app`` folder.
#. ``styles.css`` holds the global style settings for the entire website.

Yay! A Webpage!
----------------

For a better view, go ahead and close the preview panel, then click the button
to open that preview in a new browser window. You should see some simple
content.

.. figure:: ./figures/HelloAngular.png
   :alt: StackBlitz new app default page.

Congratulations! You have a functioning webpage. Feel free to play around a
little bit before continuing, and do not worry about breaking anything. If
necessary, you can always start another new project.

.. _try-it-StackBlitz-intro:

.. admonition:: Try It!

   Examine the files within the ``app`` folder. Modify the code to accomplish
   the following:

   #. Add a nose to the emoticon.
   #. Find where "Angular" is assigned to the heading, and then replace it
      with your name.
   #. Change the color for the *Start editing...* sentence.

   You may need to refresh the preview page after each attempt to see if any
   changes occur.

Now let's take a look at the different project files.

What To Ignore
^^^^^^^^^^^^^^^

For every new project, StackBlitz includes the practice file
``hello.component.ts``. It plays a role in generating the "Hello Angular"
heading, but it does not do anything other than that. For our discussion here,
we will ignore the file.

.. admonition:: Warning

   Do NOT delete ``hello.component.ts`` yet. There are some lines of code in
   ``app.module.ts`` that depend on this file. For now, leave
   ``hello.component.ts`` in place.

StackBlitz simplifies project creation by hiding many of the support files, and
Angular itself automatically sets up the code to make the different parts of a
project communicate with each other. ``main.ts`` and ``polyfills.ts`` are part
of this automated process, so you should leave these files alone.

Inside the ``app`` folder
--------------------------

If we open ``app.component.css``, we see three lines of code that styles the
``<p>`` tag. We can freely modify this file, but any CSS instructions only
affect the HTML files within ``app``. Also, the code in ``app.component.css``
overrides the CSS found in the higher level ``styles.css`` file.

This is a pattern for Angular. CSS instructions further down in the file tree
have higher priority. If ``app`` contained a subfolder with its own ``.css``
file, then those instructions would be applied to the HTML files within that
subfolder.

Let's examine the code contained in other three ``app`` files.

``app.component.html`` File
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. admonition:: Example

   ``app.component.html``

   .. sourcecode:: html
      :linenos:

      <hello name="{{ name }}"></hello>
      <p>
         Start editing to see some magic happen :)
      </p>

``app.component.html`` contains the structure and some of the text seen on the
"Hello Angular!" page. Note that the file contains a placeholder,
``{{ name }}``, that will be filled with data passed in from another file.

The strange tag ``<hello>`` represents a key idea behind building templates.
Angular allows us to define our own tags, which are also used as placeholders
in an HTML file. In this case, ``<hello>`` reserves space on the webpage for
information supplied by the ``hello.components.ts`` file.

As we add more pieces to our template, we will define specific tags to help us
arrange the different items on the screen. This makes it easier for us to keep
track of our content. For example, if we want to build a webpage that contains
a shopping list, a movies to watch list, and family photos, we can define the
tags ``<movies>``, ``<grocery-list>``, and ``<family-photos>``. With these
tags, we can reference specific content whenever we want and clearly place it
on a page. The tags also make it easy to play with new styles and formats for
our grocery list without changing much code or altering the appearance of the
movie list or photos.

``app.component.ts`` File
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. admonition:: Example

   ``app.component.ts``

   .. sourcecode:: TypeScript
      :linenos:

      import { Component } from '@angular/core';

      @Component({
         selector: 'my-app',
         templateUrl: './app.component.html',
         styleUrls: [ './app.component.css' ]
      })
      export class AppComponent  {
         name = 'Angular';
      }

``app.component.ts`` performs several important functions with very few lines.

#. Line 4 defines the tag ``<my-app>``, which we can use in files that have
   imported ``AppComponent``.
#. Line 5 imports ``app.component.html``, which we examined above.
#. Line 6 imports ``app.component.css``, which applies styling to the HTML
   file. (For those of you who changed the color of the *Start editing...*
   sentence in the Try It challenge above, this is why changing the css file
   worked).
#. Line 8 makes the styled ``.html`` file and anything defined in the
   ``AppComponent`` class available to other files.

Take a look at ``app.component.html`` again. We mentioned the ``{{ name }}``
placeholder earlier and said that it gets filled with data from a different
file. Line 9 in ``app.component.ts`` supplies this data by assigning the value
``'Angular'`` to the ``name`` variable. Changing ``'Angular'`` to a different
value alters the webpage.

``app.module.ts`` File
^^^^^^^^^^^^^^^^^^^^^^^

.. admonition:: Example

   ``app.module.ts``

   .. sourcecode:: TypeScript
      :linenos:

      import { NgModule } from '@angular/core';
      import { BrowserModule } from '@angular/platform-browser';
      import { FormsModule } from '@angular/forms';

      import { AppComponent } from './app.component';
      import { HelloComponent } from './hello.component';

      @NgModule({
         imports:      [ BrowserModule, FormsModule ],
         declarations: [ AppComponent, HelloComponent ],
         bootstrap:    [ AppComponent ]
      })
      export class AppModule { }

Just like before, there is a lot going on within very few lines.

#. Lines 1 - 3 and line 9 import and assign the core modules that make Angular
   work. This is part of the automatic process, so do not play with these
   (yet).
#. Lines 5 and 6 import the classes ``AppComponent`` and ``HelloComponent``
   from two local files, ``app.component.ts`` and ``hello.component.ts``.
#. Lines 5 and 6 also pull in references to any other files linked to
   ``app.component.ts`` and ``hello.component.ts``.
#. Line 10 declares the imported local files as necessary for the project.
#. Line 13 exports the ``AppModule`` class and makes it available to other
   files.

``app.module.ts`` does the main work of pulling in the core libraries and local
files. As new parts are added to a project, the import statements, ``imports``
array, and ``declarations`` array update automatically. We do not have to worry
about the details for adding this critical code ourselves.

.. admonition:: Note

   Lines 6 and 10 are the reason why we cannot just delete the
   ``hello.component.ts`` file. Line 6 tries to import it, and line 10 says
   that the ``HelloComponent`` class defined in the file is needed.

Change The Content
-------------------

Enough detail. Let's explore some more.

If you did not complete all of the :ref:`Try It <try-it-StackBlitz-intro>`
tasks above, attempt them now. After that...

.. admonition:: Try It!

   #. Replace line 1 in ``app.component.html`` with ``<h1>{{name}}'s First
      Angular Project</h1>``.
   #. Define a variable in the ``AppComponent`` class to hold an array. Display
      the array items in an unordered list in the HTML file. Be sure to use
      placeholders.
   #. Define a rectangle object in ``AppComponent`` that has keys of ``length``,
      ``width`` and ``area``. Assign numbers to ``length`` and ``width``, and
      have ``area`` be a function that calculates and returns the area.
   #. Use a ``<p>`` tag in the html file to display the sentence, "The
      rectangle has a length of ___ cm, a width of ___ cm, and an area of ___
      cm^2." Use placeholders in place of the blanks so the webpage displays
      the correct numbers.

Filename pattern
-----------------

Many of the files we examined on this page contain the word ``component`` in
the name. This results from the fundamental idea behind Angular. Each
*template* for a webpage is constructed from smaller pieces, and these pieces
are the *components*.

Our next step is to take a closer look at these building blocks within a
template.

Check Your Understanding
-------------------------

.. admonition:: Question

   Where would be the BEST place to modify the code if we want a different font
   for ``<p>`` text within the template?

   #. ``app.component.ts``
   #. ``app.component.html``
   #. ``app.component.css``
   #. ``app.module.ts``

.. admonition:: Question

   Where would be the BEST place to modify the code if we want to add a heading
   and an unordered list to the template?

   #. ``app.component.ts``
   #. ``app.component.html``
   #. ``app.component.css``
   #. ``app.module.ts``

.. admonition:: Question

   Where do we define a new HTML tag?

   #. ``app.component.ts``
   #. ``app.component.html``
   #. ``app.component.css``
   #. ``app.module.ts``