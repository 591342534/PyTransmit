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

