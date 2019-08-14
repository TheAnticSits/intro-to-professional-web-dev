.. _angular-exercises-1:

Exercises: Angular, Lesson 1
=============================

Starter Code
-------------

For this set of exercises, follow the link to this
`StackBlitz project <https://stackblitz.com/edit/angular-lesson1-starter-code>`__
and click the *Fork* button. This allows you to edit the file.

``hello.component.ts`` has been removed from the project, and two other
components have been added.

Open the preview in a new window and examine the content of the webpage.

.. admonition:: Note

   There are some issues with running StackBlitz in the Firefox browser. The
   preview page may only be visible in a separate tab, some menu items may not
   be visible when logged into the site, and saving your progress becomes
   quirky.

   For these exercises, we recommend using Safari or Chrome as alternates. If
   you insist on using Firefox, follow the instructions for
   :ref:`saving your work <angular-lesson1-save>` carefully.

Part 1: Modify the CSS
-----------------------

The ``movie-list`` and ``chores-list`` components have been created, but so far
they appear pretty bland. Let's change that.

#. Change the movie list text by adjusting the code in
   ``movie-list.component.css`` to accomplish the following:

   #. The text can be any color EXCEPT black.
   #. The movie list should have a centered heading.
   #. There should be at least 4 movie titles in an ordered list. Find the
      ``movies`` array in ``MovieListComponent`` and add more titles, then
      modify ``movies.component.html`` to display all the array entries.
   #. The font size should be large enough to easily read.

#. Change the chore list text by adjusting the code in
   ``chores-list.component.css`` to accomplish the following:

   #. Use a different font, with a size large enough to easily read.
   #. The text color should be different from the movie list, and not black.
   #. The chores list should have an underlined heading.
   #. The chores in the list should be italicized.

Complete the ``fav-photos`` Component
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

3. The ``fav-photos`` component has been generated, but it is incomplete. The
   page needs more images, which also need to be smaller in size.

   #. In the ``FavPhotosComponent`` class, assign a better section heading to
      ``photosTitle``.
   #. The ``image`` variables should hold URLs for images, but only one is
      is filled in. Complete at least one more, which can be from the web or
      personal pictures.
   #. In the ``.html`` file for this component, use placeholders and ``img``
      tags to display one image per line.
   #. Use the ``.css`` file for this component to make the images all be the
      same size on the page.
   #. Refresh the preview page to see the updated content.

Before moving on, click the *Sign in* button. Save your work and rename the
project (something like "angular-lesson-1-exercises"). This will allow you to
store your progress and return to it later, if necessary.

Part 2: Add More Components
----------------------------

.. admonition:: Note

   You will be adding and modifying HTML elements for this project. If you need
   to review this topic, look back at the :ref:`HTML Tags <html-tags>` page, or
   try `W3Schools <https://www.w3schools.com/html/default.asp>`__.

4. The page needs a title.

   #. Right-click the ``app`` folder in the files pane and select *Angular
      Generator/Component*. Name the new component ``page-title``.
   #. Examine ``page-title.component.ts`` and note that the ``app-page-title``
      tag has been defined next to ``selector``. Shorten the tag name to
      just ``page-title``.
   #. In the ``PageTitleComponent`` class, define a ``title`` variable and
      assign it a string.
   #. Add an ``<h1>`` to the ``page-title.component.html`` file. Use
      ``{{title}}`` as a placeholder for the title you defined. Style the text
      to be underlined and centered on the screen.
   #. Add ``<page-title></page-title>`` to ``app.component.html`` and refresh
      the preview page to see your new content.

#. The page needs a set of links to favorite websites.

   #. Repeat steps 4a and b to generate a ``fav-links`` component.
   #. In the ``FavLinksComponent`` class, define a variable and assign it an
      array that contains two or more URLs.
   #. In the ``.html`` file for this component, use placeholders in a set of
      ``<a>`` tags for the web links. Each link should be on its own line.
   #. Add ``<fav-links></fav-links>`` to ``app.component.html`` and refresh
      the preview page to see the new content.

.. admonition:: Note

   Opening the ``app.module.ts`` file shows that the components for the movies,
   chores, title, links, and photos have all been automatically imported and
   declared.

   Whether or not we use StackBlitz, Angular automatically takes care of
   updating ``app.module.ts`` when new components are generated. However,
   *deleting* a component does NOT remove the references from the file.

Part 3: Rearrange the Components
---------------------------------

The content on the page might appear a bit jumbled, since we gave you no
guidance on where to add the custom tags in ``app.component.html``.
Fortunately, templates allow us to easily move items around the framework.

6. Rearrange the tags ``fav-photos``, ``fav-links``, ``page-title``, etc. to
   create a specific page layout.

   #. ``app.component.html`` has ``<div>`` tags to set up a three-column row.
      Use this to arrange the movie list, images, and chore list.
   #. Center the title at the top of the page.
   #. Add a horizontal line below the three lists with the ``<hr>`` tag.
   #. Center the links below the horizontal line.

Your final page should have this format (the dashed lines are optional):

.. figure:: ./figures/AngularLesson1Layout.png
   :alt: Angular Lesson 1 Exercises project.

Optional Final Touches
^^^^^^^^^^^^^^^^^^^^^^^^

7. To boost your practice, complete one or more of the following:

   #. Change the background to a decent color, image or pattern.
   #. Add a border around one or more of the components on the page.
   #. Add a fun, coding related gif to the page.
   #. Make one component change when the user clicks on it.

.. _angular-lesson1-save:

Saving Your Work
-----------------

As mentioned above, we recommend using Safari or Chrome for these exercises.
The following instructions apply ONLY if you run StackBlitz in Firefox.

To save your work using Firefox:

#. Once you open the starter code, immediately click the *Fork* button. Do NOT
   login to StackBlitz yet.
#. Make the edits described in the exercises, saving your work as you go.
#. Once ALL of the exercises are complete, click the *Sign in* button and enter
   your password.
#. Rename the file by clicking the pencil icon near its name.

To modify your saved project using Firefox:

#. Click on the *Sign in* icon and enter your password.
#. Click on your username button to see a list of saved projects.
#. Copy the URL for your project (stackblitz.com/edit/my-project-name).
#. *Log out* of StackBlitz.
#. Paste the URL into the address bar and fork the project again.
#. Once you finish your new edits, log back in to StackBlitz and rename the
   file.