Kindle Clippings to Markdown
-----

This is a modification of `lxyu's code <https://github.com/lxyu/kindle-clippings?tab=readme-ov-file#kindle-clippings>`_.

This script has multiple modifications, the most relevant ones are listed below:

Modifications
-----

1. **File Opening Mode Correction in `save_clips` Function**:
   - Changed the file opening mode from binary write (`'wb'`) to write (`'w'`) to ensure compatibility with the `json.dump()` function, which expects to write strings, not bytes.

2. **Correction of String Encoding in `export_txt` Function**:
   - Removed the `.encode('utf-8')` method from the lines being appended, keeping the data as strings instead of converting them to bytes.
   - Changed the file opening mode from binary write (`'wb'`) to write (`'w'`) to match the string data type used in file operations.

3. **Directory Existence Check**:
   - Added a check in the `export_txt` function to ensure the `OUTPUT_DIR` exists before attempting to write files. Used `os.makedirs()` to create the directory if it does not exist.

4. **Sanitization of File Names**:
   - Added a `sanitize_filename` function to remove or replace characters that might be problematic in file names, ensuring compatibility with the filesystem.

5. **Ordering of Clippings** (General Advice):
   - Suggested adding ordering logic based on available metadata (like position or timestamp) before exporting the clippings to maintain the correct order in the output files.


Features (Same information as preceding repository )
-----

Clippings are stored in a python dict with this structure

.. code:: py

    clips = {'book': {'position': 'clipping'}}

Msgpack was used to serialize clippings for archive.

Each new `My Clippings.txt` will add clips to previous archive automatically.

Clips will be export to `output` directory, find them there.

It's EASY and you don't need to care nothing!


Usage
-----

Install `msgpack-python` first.

.. code:: bash

    $ pip install msgpack-python

Clone project and put `My\ Clippings.txt` to project's root.

Run `kindle.py`

.. code:: bash

    $ python kindle.py

DONE!


This version of the code returns .md files instead of .txt files, because is intended to be used as an auxiliary code to import your clippings to your webpage!
