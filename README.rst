**Author**: `Pahaz Blinov`_

**Repo**: https://github.com/pahaz/google-spreadsheets-api/

Simple create/append google spreadsheet api helper.

Requirements
-------------

* `oauth2client`_
* `googleapiclient`_

Installation
============

`google_spreadsheet`_ is on PyPI, so simply run:

::

    pip install google_spreadsheet

or ::

    easy_install google_spreadsheet

to have it installed in your environment.

For installing from source, clone the
`repo <https://github.com/pahaz/google-spreadsheets-api>`_ and run::

    python setup.py install

Usage scenarios
===============

Two typical usecases where ``google_spreadsheet`` is helpful there are:
1. create new spreadsheet with restricted acccess rules,
2. append data to existing spreadsheet.

You can use it for export your user data to the google spreadsheet. 
And sharing this data to all around the world or sharing to specific users.

Usage examples
==============

Example 1: create spreadsheet
-----------------------------

.. code-block:: py

    from google_spreadsheet import get_credentials, Spreadsheets


    def create_example():
        credentials = get_credentials('auth.json', [
            'https://www.googleapis.com/auth/drive',
            'https://www.googleapis.com/auth/spreadsheets'])
        api = Spreadsheets(credentials=credentials)
        sheet = api.create('test1', writers=['pahaz.blinov@gmail.com'])
        print(sheet)

    if __name__ == '__main__':
        create_example()


Example 2: append row to existing spreadsheet
---------------------------------------------

.. code-block:: py

    from google_spreadsheet import get_credentials, Spreadsheets


    def append_data_example():
        credentials = get_credentials('auth.json', [
            'https://www.googleapis.com/auth/drive',
            'https://www.googleapis.com/auth/spreadsheets'])
        api = Spreadsheets(credentials=credentials)
        sheet = api.get('1jSHsmPTOOiPXdYQlrVBwbo3MO1vp64lmi5R_Ld_duKo')
        sheet.append([[1, 2], [3, 4]])


    if __name__ == '__main__':
        append_data_example()


.. _Pahaz Blinov: https://github.com/pahaz/
.. _oauth2client: https://github.com/google/oauth2client/
.. _googleapiclient: https://github.com/google/google-api-python-client/
.. _google_spreadsheet: https://pypi.python.org/pypi/google_spreadsheet/
