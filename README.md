# Delete tweets

Delete tweets (or just replies or retweets) from your timeline, including tweets
beyond the [3,200 tweet limit](https://web.archive.org/web/20131019125213/https://dev.twitter.com/discussions/276).

## Prerequisites

### Configure API access

1. Open Twitter's [Application Management](https://apps.twitter.com/), and create a new Twitter app.
2. Set the permissions of your app to *Read and Write*.
3. Set the required environment variables:

```bash
TWITTER_CONSUMER_KEY="[your consumer key]"
TWITTER_CONSUMER_SECRET="[your consumer secret]"
TWITTER_ACCESS_TOKEN="[your access token]"
TWITTER_ACCESS_TOKEN_SECRET="[your access token secret]"
```

### Get your Twitter archive

1. Open your [account page](https://twitter.com/settings/account).
2. Click 'Your Twitter archive', and a link to your archive will arrive per email.
3. Follow the link in the email to download the archive.
4. Unpack the archive, and move `tweets.csv` to the same directory as this script.

## Installation

### Local

Install the required dependencies.

```
pip install -r requirements.txt
```

### Docker

If you have Docker [installed](https://docs.docker.com/install/), you could run
the script using the following command.

```bash
docker run --env TWITTER_CONSUMER_KEY="[your consumer key]" \
  --env TWITTER_CONSUMER_SECRET="[your consumer secret]" \
  --env TWITTER_ACCESS_TOKEN="[your access token]" \
  --env TWITTER_ACCESS_TOKEN_SECRET="[your access token secret]"
  --rm -it koenrh/delete-tweets \
  -v $E:PWD":/" -d 2014-01-01 /tweets.csv
```

You could make this command more easily accessible by putting it an executable,
and make sure that it is available in your `$PATH`.

## Usage

For example, delete any tweet from before *January 1, 2014*:

```bash
python deletetweets.py -d 2014-01-01
```

Or delete all retweets:

```bash
python deletetweets.py -r retweet
```
