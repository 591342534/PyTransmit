.. PyTransmit documentation master file, created by
   sphinx-quickstart on Fri Jul 26 14:48:13 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to PyTransmit documentation!
==========================================

**PyTransmit** is a simple wrapper on top the ftplib package which provides an object that can be used to make FTP calls to a PyTransmit installation.

Example
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


