# calibre-downloader
Docker container to download content with calibre recipes 

The Amazon Kindle reader software and hardware do have a good user experience compared to some stock reader apps (..cough..economist ios app..cough..)

So I prefer to downloading suitable content with calibre's prepared recipes into ebooks and consume them with any form of kindle reader.

To further simplify the process I have created a dockerfile that will create an container image which by default downloads "The Economist".


Build the image with:
```docker build -t calibre-downloader .```

## Use the Image
Run the image: 
```docker run -v /home/speedy-beaver/calibre/output:/tmp/calibre -it --rm  calibre-downloader```

The ```-v /home/speedy-beaver/calibre/output:/tmp/calibre``` maps the directory ```/home/speedy-beaver/calibre/output``` into the container, the downloaded ebook will be found in that directory. 

By overwriting the RECIPE environment variable, it is possible to trigger any other of the built-in calibre recipes, e.g. like this: 
```docker run -e RECIPE="The Verge" -v /home/speedy-beaver/calibre/output:/tmp/calibre -it --rm  calibre-container```
