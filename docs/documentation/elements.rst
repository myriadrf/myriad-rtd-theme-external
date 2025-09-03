########
Elements
########

.. sidebar:: Navigation Sidebar
   :subtitle: Quick Links

   This is a sidebar that appears on the right side of the page in most themes.

   **Quick Navigation:**

   * :ref:`tables-section`
   * :ref:`forms-section`
   * :ref:`code-examples`
   * :ref:`admonitions-section`

   .. note::
      Sidebars are great for navigation, quick references, or additional context.

Introduction
============

This page demonstrates various RST elements commonly used in Sphinx documentation, specifically designed to work with the RTD theme. Use this as a reference when developing custom CSS modifications.

.. _tables-section:

Tables and Data Display
=======================

Simple Table
------------

Here's a simple table demonstrating basic styling:

=============  =============  =============  =============
Header 1       Header 2       Header 3       Header 4
=============  =============  =============  =============
Row 1, Col 1   Row 1, Col 2   Row 1, Col 3   Row 1, Col 4
Row 2, Col 1   Row 2, Col 2   Row 2, Col 3   Row 2, Col 4
Row 3, Col 1   Row 3, Col 2   Row 3, Col 3   Row 3, Col 4
=============  =============  =============  =============

Grid Table with Complex Content
-------------------------------

.. table:: Feature Comparison Table
   :widths: 25 25 25 25

   +------------------+------------------+------------------+------------------+
   | Feature          | Basic Plan       | Pro Plan         | Enterprise       |
   +==================+==================+==================+==================+
   | **Storage**      | 10 GB            | 100 GB           | Unlimited        |
   +------------------+------------------+------------------+------------------+
   | **Users**        | 1                | 5                | Unlimited        |
   +------------------+------------------+------------------+------------------+
   | **Support**      | Email            | Email + Chat     | 24/7 Phone       |
   +------------------+------------------+------------------+------------------+
   | **Price/Month**  | $9               | $29              | Contact Sales    |
   +------------------+------------------+------------------+------------------+

.. _forms-section:

Forms and Interactive Elements
==============================

Since RST doesn't have native form support, we can embed HTML for forms:

Basic Contact Form
------------------

.. raw:: html

   <form class="contact-form" method="post" action="/contact">
     <div class="form-group">
       <label for="name">Name:</label>
       <input type="text" id="name" name="name" required>
     </div>

     <div class="form-group">
       <label for="email">Email:</label>
       <input type="email" id="email" name="email" required>
     </div>

     <div class="form-group">
       <label for="subject">Subject:</label>
       <select id="subject" name="subject">
         <option value="general">General Inquiry</option>
         <option value="support">Technical Support</option>
         <option value="billing">Billing</option>
         <option value="feature">Feature Request</option>
       </select>
     </div>

     <div class="form-group">
       <label for="message">Message:</label>
       <textarea id="message" name="message" rows="5" required></textarea>
     </div>

     <div class="form-group">
       <input type="checkbox" id="newsletter" name="newsletter">
       <label for="newsletter">Subscribe to newsletter</label>
     </div>

     <div class="form-group">
       <button type="submit" class="btn btn-primary">Send Message</button>
       <button type="reset" class="btn btn-secondary">Reset Form</button>
     </div>
   </form>

.. _code-examples:

Code Examples and Syntax Highlighting
======================================

Python Code Block
------------------

.. code-block:: python
   :linenos:
   :emphasize-lines: 3,5

   def process_data(data):
       """Process input data and return results."""
       cleaned_data = clean_input(data)

       results = []
       for item in cleaned_data:
           if validate_item(item):
               results.append(transform_item(item))

       return results

JavaScript Example
-------------------

.. code-block:: javascript
   :caption: Interactive form validation

   function validateForm() {
       const email = document.getElementById('email').value;
       const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

       if (!emailRegex.test(email)) {
           alert('Please enter a valid email address');
           return false;
       }

       return true;
   }

Configuration File
-------------------

.. code-block:: yaml
   :caption: config.yml

   database:
     host: localhost
     port: 5432
     name: myapp
     user: ${DB_USER}
     password: ${DB_PASSWORD}

   cache:
     type: redis
     url: redis://localhost:6379
     ttl: 3600

.. _admonitions-section:

Admonitions and Callouts
=========================

All Standard Admonition Types
-----------------------------

**Info/Note Style Admonitions:**

.. note::
   This is a note admonition. It's used for general information that might be helpful to know.

   Can contain multiple paragraphs and other elements like:

   * Lists
   * Code: ``example_code()``
   * **Bold text** and *italic text*

.. seealso::

   Related documentation:

   * :doc:`installation`
   * :doc:`configuration`
   * :doc:`troubleshooting`

**Success/Positive Style Admonitions:**

.. tip::
   **Pro Tip:** Use admonitions to highlight important information that stands out from regular content.

.. hint::
   This is a hint admonition. Use it to provide helpful suggestions or alternative approaches.

.. important::
   This is an important admonition. Use it to highlight critical information that users must know.

**Warning Style Admonitions:**

.. warning::
   This is a warning admonition. Use it to alert users about potential issues or important considerations.

.. caution::
   This is a caution admonition. Similar to warning but implies more care is needed.

.. attention::
   This is an attention admonition. Use it to draw focus to specific details.

.. admonition-todo::

   This is a todo admonition for development notes and pending tasks.

**Danger/Error Style Admonitions:**

.. danger::
   This is a danger admonition. Reserve this for critical warnings about actions that could cause problems.

.. error::
   This is an error admonition. Use it to highlight error conditions or failure scenarios.

**Custom Admonitions:**

.. admonition:: Custom Title
   :class: custom-admonition

   You can create custom admonitions with specific titles and CSS classes for unique styling.

   This allows for specialized formatting and branding.

.. admonition:: API Documentation
   :class: api-note

   **New in version 2.1:** This feature requires authentication.

   See the :ref:`authentication guide <auth-guide>` for setup instructions.

Buttons and Interactive Elements
===============================

Standard HTML Buttons
---------------------

.. raw:: html

   <div class="button-examples">
     <h4>Default Button States</h4>
     <button type="button" class="btn btn-neutral">Default Button</button>
     <button type="button" class="btn btn-neutral" disabled>Disabled Button</button>

     <h4>Primary Buttons</h4>
     <button type="button" class="btn btn-primary">Primary Button</button>
     <button type="button" class="btn btn-primary" disabled>Disabled Primary</button>

     <h4>Success Buttons</h4>
     <button type="button" class="btn btn-success">Success Button</button>
     <button type="button" class="btn btn-success" disabled>Disabled Success</button>

     <h4>Warning Buttons</h4>
     <button type="button" class="btn btn-warning">Warning Button</button>
     <button type="button" class="btn btn-warning" disabled>Disabled Warning</button>

     <h4>Danger Buttons</h4>
     <button type="button" class="btn btn-danger">Danger Button</button>
     <button type="button" class="btn btn-danger" disabled>Disabled Danger</button>

     <h4>Info Buttons</h4>
     <button type="button" class="btn btn-info">Info Button</button>
     <button type="button" class="btn btn-info" disabled>Disabled Info</button>

     <h4>Link Style Buttons</h4>
     <button type="button" class="btn btn-link">Link Button</button>
     <button type="button" class="btn btn-link" disabled>Disabled Link</button>

     <h4>Button Groups</h4>
     <div class="btn-group" role="group">
       <button type="button" class="btn btn-secondary">Left</button>
       <button type="button" class="btn btn-secondary">Middle</button>
       <button type="button" class="btn btn-secondary">Right</button>
     </div>
   </div>

Form Input States
----------------

.. raw:: html

   <div class="form-states-example">
     <h4>Input Field States</h4>
     <div class="form-group">
       <label>Normal Input:</label>
       <input type="text" class="form-control" placeholder="Normal input field">
     </div>

     <div class="form-group">
       <label>Success State:</label>
       <input type="text" class="form-control is-valid" value="Valid input" readonly>
       <div class="valid-feedback">This input looks good!</div>
     </div>

     <div class="form-group">
       <label>Warning State:</label>
       <input type="text" class="form-control is-warning" value="Warning input" readonly>
       <div class="warning-feedback">Please check this input.</div>
     </div>

     <div class="form-group">
       <label>Error State:</label>
       <input type="text" class="form-control is-invalid" value="Invalid input" readonly>
       <div class="invalid-feedback">This input has an error.</div>
     </div>

     <div class="form-group">
       <label>Disabled Input:</label>
       <input type="text" class="form-control" value="Disabled input" disabled>
     </div>

     <div class="form-group">
       <label>Focused Input (click to test):</label>
       <input type="text" class="form-control" placeholder="Click to focus">
     </div>
   </div>

Lists and Navigation
====================

Unordered List
--------------

* Main item one

  * Sub-item A
  * Sub-item B with longer text that might wrap to multiple lines

    * Sub-sub-item with even more nesting

* Main item two
* Main item three with **bold text** and *italic text*

Ordered List
------------

1. First step in the process
2. Second step with detailed explanation

   a. Sub-step with letter numbering
   b. Another sub-step

3. Final step

Definition List
---------------

Term 1
   Definition of the first term. This can be quite long and detailed, explaining exactly what the term means in context.

Term 2
   A shorter definition.

Term 3
   Another definition that might include ``inline code`` or other formatting.

Text Formatting Examples
========================

This paragraph demonstrates various **bold text**, *italic text*, ``inline code``, and :kbd:`keyboard shortcuts` formatting options.

Here's a line with :guilabel:`GUI Label` text and :menuselection:`File --> Save As` menu selections.

You can also use :doc:`document links <index>`, :ref:`reference links <tables-section>`, and external links like `Sphinx Documentation <https://www.sphinx-doc.org/>`_.

Mathematical Expressions
=========================

Inline math: The area of a circle is :math:`A = \pi r^2`.

Block math:

.. math::

   \frac{d}{dx}\left( \int_{0}^{x} f(u)\,du\right)=f(x)

Images and Media
================

.. figure:: https://picsum.photos/640/480
   :alt: Sample placeholder image
   :align: center
   :width: 400px

   This is a figure caption. Figures can include images, charts, or other visual content.

Line Blocks and Text Alignment
=============================

Line blocks preserve line breaks:

| This is a line block.
| Each line begins with a vertical bar ("|").
| Line breaks and initial indents are preserved.
| Continuation lines are wrapped portions of long lines;
  they begin with a space in place of the vertical bar.

.. line-block::

   Lend me your ears; I come to bury Caesar, not to praise him.
   The evil that men do lives after them;
   The good is oft interred with their bones.

Text Alignment Examples
-----------------------

.. image:: https://picsum.photos/640/480
   :align: left
   :alt: Left aligned image

This text flows around the left-aligned image above. Lorem ipsum dolor sit amet, consectetur adipiscing elit.

.. image:: https://picsum.photos/640/480
   :align: right
   :alt: Right aligned image

This text flows around the right-aligned image. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

.. centered:: This text is centered

Field Lists and Option Lists
============================

Field List Example
------------------

:Author: John Doe
:Version: 1.2.3
:Date: 2025-06-16
:Copyright: This document has been placed in the public domain.

Option List Example
-------------------

-a            Output all files
-b            Use batch mode
--verbose     Enable verbose output
--output=file Write output to file

API Documentation Elements
==========================

.. py:function:: process_data(input_data, format="json")

   Process input data and return formatted results.

   :param input_data: The data to process
   :type input_data: str or dict
   :param format: Output format (json, xml, csv)
   :type format: str
   :returns: Processed data in specified format
   :rtype: str
   :raises ValueError: If format is not supported

.. py:class:: DataProcessor

   A class for processing various data formats.

   .. py:method:: validate(self, data)

      Validate input data structure.

      :param data: Data to validate
      :returns: True if valid, False otherwise

Glossary and References
=======================

.. glossary::

   environment
      A structure where information about all documents under the root is
      saved, and used for cross-references. The environment is pickled
      after the parsing stage, so that successive runs only need to read
      and parse new and changed documents.

   source directory
      The directory which, including its subdirectories, contains all
      source files for one Sphinx project.

Citations and Footnotes
=======================

Here's a citation reference [1]_ and a footnote reference [#note1]_.

Multiple footnote references [#note1]_ [#note2]_ can be used.

Autonumbered footnote [#]_ and another [#]_.

.. [1] This is the citation. It may contain multiple paragraphs.

   Like this one with additional content.

.. [#note1] This is a labeled footnote.
.. [#note2] This is another labeled footnote.
.. [#] This is an autonumbered footnote.
.. [#] This is another autonumbered footnote.

Complex Lists and Containers
============================

Horizontal List
---------------

.. hlist::
   :columns: 3

   * Item 1
   * Item 2
   * Item 3
   * Item 4
   * Item 5
   * Item 6

Simple vs Complex Lists
-----------------------

Simple list (no spacing between items):

.. class:: simple

* First item
* Second item
* Third item

Complex list (default spacing):

* First item with additional content

  This paragraph is part of the first item.

* Second item
* Third item

Topic and Rubric Elements
=========================

.. topic:: Special Topic

   This is a topic box. Topics are like block quotes with a title.

   They can contain multiple paragraphs and other block elements.

.. rubric:: This is a Rubric Heading

Rubrics are informal headings that don't appear in the table of contents.

Version and Modification Notes
==============================

.. versionadded:: 1.2
   Support for new data format was added.

.. versionchanged:: 1.3
   The function signature was updated to include optional parameters.

.. deprecated:: 1.4
   This function is deprecated. Use :func:`new_function` instead.

Download and Source Links
=========================

Download the example file: :download:`example.txt <https://example.com/example.txt>`

.. raw:: html

   <div class="viewcode-block">
   <a class="viewcode-back" href="#top">[docs]</a>
   <a class="viewcode-link" href="#source">View Source</a>
   </div>

Keyboard, GUI, and Menu Elements
================================

Press :kbd:`Ctrl+C` to copy, :kbd:`Ctrl+V` to paste, or :kbd:`Ctrl+Shift+V` for paste special.

Click :guilabel:`File` → :menuselection:`Save As` → :guilabel:`Export` to save your work.

Use the :guilabel:`Advanced Settings` button for more options.

Math and Equations
==================

Einstein's mass-energy equation: :math:`E = mc^2`

The quadratic formula:

.. math::
   :label: quadratic

   x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}

Reference to equation :eq:`quadratic` above.

Advanced Code Examples
======================

Code with Emphasis and Captions
--------------------------------

.. code-block:: python
   :caption: Advanced data processing example
   :linenos:
   :emphasize-lines: 3,7-9

   def advanced_processor(data):
       """Advanced data processor with error handling."""
       validated_data = validate_input(data)  # emphasized

       try:
           result = complex_operation(validated_data)
           if result.success:  # emphasized
               log_success(result)  # emphasized
               return result.data  # emphasized
       except ProcessingError as e:
           log_error(e)
           raise

Literal Code Blocks
-------------------

::

   This is a literal code block.
   It preserves    spacing    and formatting.
   No syntax highlighting is applied.

Tables with Complex Content
===========================

.. table:: Configuration Options
   :widths: 20 30 25 25

   +------------------+---------------------------+------------------+------------------+
   | Parameter        | Description               | Default Value    | Valid Options    |
   +==================+===========================+==================+==================+
   | ``timeout``      | Connection timeout in     | ``30``           | Any positive     |
   |                  | seconds                   |                  | integer          |
   +------------------+---------------------------+------------------+------------------+
   | ``retries``      | Number of retry attempts  | ``3``            | ``0`` to ``10``  |
   +------------------+---------------------------+------------------+------------------+
   | ``format``       | Output format             | ``json``         | ``json``,        |
   |                  |                           |                  | ``xml``,         |
   |                  |                           |                  | ``csv``          |
   +------------------+---------------------------+------------------+------------------+

Footer Section
==============

This comprehensive example now includes all the major RST elements that are styled by both the original Sphinx RTD theme and your custom theme. The RTD theme will add navigation elements, search functionality, and responsive design features automatically.
```
