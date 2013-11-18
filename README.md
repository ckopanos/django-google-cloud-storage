django-google-cloud-storage
===========================

A file storage backend for django appengine projects that uses google cloud storage

If you run your projects on Google's appengine and you are using the django framework you might need this
file backend since there is no way to upload files, images, etc on appengine. Although solutions exist for
the amazon cloud storage i have not find a file backend for google cloud storage. This backend does work
with google cloud storage although in early development. I have used it with regular file uploads and with
file manager solutions such as django-filer. The code as it is right now stores files for public use (i.e. a web site images)

Prerequisites
-------------

You need to have an appengine project. This will not work as a standalone solution for non appengine django
projects, since there is no authentication mechanism with the google cloud storage implemented.

You need to download the GCS client library from
https://developers.google.com/appengine/docs/python/googlecloudstorageclient/download
and install in in your project directory.

Installation
-------------

Just copy the google folder in your project directory

Configuration
-------------

On your django settings.py file you need to add the following settings

    GOOGLE_CLOUD_STORAGE_BUCKET = '/your_bucket_name' # the name of the bucket you have created from the google cloud storage console
    GOOGLE_CLOUD_STORAGE_URL = 'http://storage.googleapis.com/bucket' #whatever the ulr for accessing your cloud storgage bucket
    GOOGLE_CLOUD_STORAGE_DEFAULT_CACHE_CONTROL = 'public, max-age: 7200' # default cache control headers for your files

And finally declare the file storage backend you will use on your settings.py file

    DEFAULT_FILE_STORAGE = 'google.storage.googleCloud.GoogleCloudStorage'
