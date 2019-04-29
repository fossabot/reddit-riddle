# reddit-riddle

This is a script for downloading images (or other media) from reddit subreddits.

## Install

This script requires at least Python 3.6.
After cloning this repository you need to install the requirements via 

```sh
pip install -r requirements.txt
```

## Configuration

Before running you need to provide information for the reddit api.
To do so you must create an app in your reddit [account preferences](https://www.reddit.com/prefs/apps).
The application must be of type 'script'. 
That must be done via a config.yaml file in the scripts directory.
You can copy the `default-config.yaml` file to the `config.yaml` file and change the keys
`client_id` and `client_secret` under `credentials`.

```yaml
# user app credentials
credentials:
  client_id: your app-client id           # change this
  client_secret: your app-client secret   # and change this

# required extension of the file to be downloaded
image-extensions:
  - png
  - jpg
  - jpeg
```

## Running

### Help output

```sh
Usage: riddle.py [options] [subreddits]

Options:
  -h, --help            show this help message and exit
  -c COUNT, --count=COUNT
                        The number of images to download for each subreddit.
                        If not set it is the maximum fetchable number.
  -o OUTPUT, --output=OUTPUT
                        The name of the output folder. If none is specified,
                        it's the subreddits name.
  -z, --zip             Stores the images in a zip file if true
```

### Example

Download all images from r/EarthPorn:

```sh
python3 riddle.py EarthPorn
```

Download all images from r/astrophotography to a zip-file:

```sh
python3 riddle.py -z astrophotography
```

Download a maximum of 200 images from r/astrophotography or r/EarthPorn to one zip-file named coolpics.zip:

```sh
python3 riddle.py -z -c 100 -o coolpics astrophotography EarthPorn
```
