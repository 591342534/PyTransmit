PyTransmit documentation!
==========================================

**PyTransmit** is a simple wrapper on top the **ftplib** package which provides an object that can be used to make FTP calls to a PyTransmit installation.

Installation
-------

To install **PyTransmit** from tarball, run the following command::

    python setup.py install

You can also download and install **PyTransmit** directly from the Python Package Index
using either pip or easy_install::

    pip install PyTransmit
    easy_install -Z PyTransmit

If you prefer, you can also simply place the **pytransmit** subdirectory somewhere on
your python path. This is useful if you are running the latest version from
Mercurial, or want to deploy **pytransmit** with your application on for example Google
App Engine.

Note that you need Python 2.4 or later to use PyTransmit.

Basics
-------

This is an example application that handles FTP through PyTransmit::

    from pytransmit import FTPClient

    ftp_obj = FTPClient()

    # FTP Details
    FTP_HOST = ""
    FTP_USER = ""
    FTP_PASS = ""
    FTP_PORT = 21

    # Connect to the server
    ftp_obj.connect(FTP_HOST, FTP_USER, FTP_PASS, FTP_PORT)
    print(ftp_obj.get_message())

    # Create a new test directory
    directory = '/test'
    ftp_obj.make_directory(directory)
    print(ftp_obj.get_message())

    # Change Directory
    ftp_obj.change_directory(directory)
    print(ftp_obj.get_message())

    # Get Directory Listing
    ftp_obj.get_directory_listing()

With the above commands, you can create a FTP connection and create a new /test directory and CD into that directory.


Uploading and Downloading Files
-------

You can easily upload files to the connected server via PyTransmit::

   
    app_root = os.path.dirname(os.path.abspath(__file__))
    # Add the file name you want to upload
    file_path = os.path.join(app_root, 'test.txt')
    strip_path = file_path.rstrip(os.sep)	
    fp_path = os.path.basename(strip_path)
    
    # Upload command
    ftp_obj.upload_file(fp_path)
    print(ftp_obj.get_message())

Similarly, you can download the files from the server in the same fashion::

    # Add the filename to download
    ftp_obj.download_file("hello.csv")
    print(ftp_obj.get_message())    
Resources
---------

- [Documentation](http://pytransmit.readthedocs.org/en/latest/)
- [pypi](https://pypi.python.org/pypi/PyTransmit/0.1) 

