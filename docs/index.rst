.. PyTransmit documentation master file, created by
   sphinx-quickstart on Fri Jul 26 14:48:13 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to PyTransmit documentation!
==========================================

**PyTransmit** is a simple wrapper on top the **ftplib** package which provides an object that can be used to make FTP calls to a PyTransmit installation.

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

You can easily upload files to the connected server via PyTransmit.
   
	 app_root = os.path.dirname(os.path.abspath(__file__))
	 # Add the file name you want to upload
	 file_path = os.path.join(app_root, 'test.txt')
	 strip_path = file_path.rstrip(os.sep)	
	 fp_path = os.path.basename(strip_path)

	 # Upload command
	 ftp_obj.upload_file(fp_path)
	 print(ftp_obj.get_message())

Similarly, you can download the files from the server in the same fashion.

	 # Add the filename to download
	 ftp_obj.download_file("hello.csv")
	 print(ftp_obj.get_message())


API reference
-------

PyTransmit is built on a very small API. The The available functions are:

.. py:function:: log_message(self, message, clear=True)

   Logs the message to the message_array, from where it is retrieved to display in the console.

   :param message: The message string.
   :param clear: Buffer Clearance.

.. py:function:: get_message(self)

   Returns the logged message to the console.

   :return: Returns the message.

.. py:function:: connect(self, server, ftp_user, ftp_password, port)

   Connects the remote host to the server from the information provided to the connect method.
   If the connection is successful, the messaged will logged and displayed in the console, otherwise
   Exception is raised with the error displayed to the console and program execution halts.

   :param server: The address of the server
   :param ftp_user: The FTP user id.
   :param ftp_password: The FTP password.
   :param port: The port number.

.. py:function:: make_directory(self, directory)

   Creates the new directory in the connected server in the root or in the directory specified via the parameter.

   :param directory: Directory name to create.

.. py:function:: change_directory(self, directory)

   CD's into the directory of our wish by providing the directory name as the parameter to it.

   :param directory: Directory name to change to it.

.. py:function:: directory_exists(self, directory_name)

   Checks if the directory you are trying to upload the files is already present or not and if
   its already present CD's into the directory and if not, creates the directory and CD's into the
   newly created directory.

   :param directory_name: Directory name to check its existence.

.. py:function:: get_directory_listing(self)

   Lists all the contents in the connected server or in the specified folder in the server.

.. py:function:: upload_file(self, filename)

   The file provided with filename will be uploaded to the server in the recommended
   format automatically to the desired directory.

   :param filename: Name of the file to upload.

.. py:function:: download_file(self, filename)

   Downloads the file from the connected server, provided the name is passes as the parameter.

   :param filename: Name of the file to download.

.. py:function:: __del__(self)

   Closes the FTP connection.
