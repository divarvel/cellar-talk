% Storing files in a cloud architecture
% Clément Delafargue
% 2015-10-16

--------------------------------------------------------------------------------

## DEATH TO THE FILESYSTEM

<video src="/home/clement/Images/lol/metal-worker.webm" loop></video>

--------------------------------------------------------------------------------

# I'm online!

 - [\@clementd](https://twitter.com/clementd) on twitter
 - [cltdl.fr/blog](http://cltdl.fr/blog)
 - [clever cloud](http://clever-cloud.com)


--------------------------------------------------------------------------------

## Storing dynamic files

--------------------------------------------------------------------------------

# On the file system

<video src="/home/clement/Images/lol/well-fuck.webm" loop></video>

--------------------------------------------------------------------------------

# No separation between code & data

<video src="/home/clement/Images/lol/baby-cobra.webm" loop></video>

--------------------------------------------------------------------------------

## Huge security issue

--------------------------------------------------------------------------------

## Every single PHP CMS

--------------------------------------------------------------------------------

## Very hard to scale

<video src="/home/clement/Images/lol/dolly-eyes.webm" loop></video>

--------------------------------------------------------------------------------

# Shared, distributed filesystems

--------------------------------------------------------------------------------

# PITA in a immutable infrastructure

--------------------------------------------------------------------------------

## Implicit dependencies

--------------------------------------------------------------------------------

## Store files in your fav db

--------------------------------------------------------------------------------

# (needs blob support) + proxying

--------------------------------------------------------------------------------

<video src="/home/clement/Images/lol/lana-nope.webm" loop></video>

--------------------------------------------------------------------------------

## Dedicated datastore for files

--------------------------------------------------------------------------------

## Amazon S3 (aaS)

--------------------------------------------------------------------------------

## Riak S2 (open-source)

--------------------------------------------------------------------------------

## Clever Cloud Cellar (aaS)

--------------------------------------------------------------------------------

## HTTP API

--------------------------------------------------------------------------------

## Different domain name

--------------------------------------------------------------------------------

## Reduced load on application servers

--------------------------------------------------------------------------------

## Command line

--------------------------------------------------------------------------------

**Create a bucket**

    s3cmd mb s3://myBucket

**Upload a file**

    s3cmd put localFile \
      s3://myBucket/remoteFile

--------------------------------------------------------------------------------

**List files**

    s3cmd ls s3://myBucket/

**Download a file**

    s3cmd get s3://myBucket/remoteFile \
        localFile

--------------------------------------------------------------------------------

## SDK

--------------------------------------------------------------------------------

```javascript
import AWS from "aws-sdk";
import fs from "fs";

const s3 =
  new AWS.S3(options);
```

--------------------------------------------------------------------------------

```javascript
const body =
  fs.createReadStream("./path/to/file");

const params = {
  Bucket: "myBucket",
  Key: "myKey",
  Body: body
};

s3.putObject(params, (err, data) => {
  …
});
```

--------------------------------------------------------------------------------

## Serve private assets from Cellar

--------------------------------------------------------------------------------

## Pre-signed URLs to avoid proxying

--------------------------------------------------------------------------------

```javascript
const params = {
  Bucket: 'myBucket',
  Key: 'myKey'
};

s3.getSignedUrl(
  'putObject',
   params,
   (err, url) => {
  …
});
```

--------------------------------------------------------------------------------

## Pre-signed PUT URLs for uploads

--------------------------------------------------------------------------------

```javascript
const params = {
  Bucket: 'myBucket',
  Key: 'myKey'
};

s3.getSignedUrl(
  'putObject',
   params,
   (err, url) => {
  …
});
```

--------------------------------------------------------------------------------

## DEATH TO THE FILESYSTEM

<video src="/home/clement/Images/lol/bridge-demolition.webm" loop></video>

--------------------------------------------------------------------------------

**Cellar**  
<https://www.clever-cloud.com/doc/addons/cellar/>

**Riak S2**  
<http://docs.basho.com/riakcs/latest/>

--------------------------------------------------------------------------------

# Thanks

## <http://cltdl.fr/gifs>

-------------------------------------------

# I'm online!

- [\@clementd](https://twitter.com/clementd) on twitter
- [cltdl.fr/blog](http://cltdl.fr/blog)
- [clever cloud](http://clever-cloud.com)

