---

copyright:
  years: 2017, 2018
lastupdated: "2018-05-21"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Pseudo Hierarchical Directories

After creating a directory with the {{site.data.keyword.objectstorageshort}} browser interface and then using the API directly or using one of the various clients or libraries, you may have noticed that a stub directory object was created. This is done to enable users to create empty directories that stick around past one user's session without having to add objects underneath that directory. 

The entire directory structure can be built without these directory objects so cleaning up those objects is safe. To further explain, this article runs through an example of building a directory listing from an {{site.data.keyword.objectstorageshort}} API perspective.

## Strategy to Building a Directory-Based Interface with {{site.data.keyword.objectstorageshort}}

- Provide a way to create directory objects: zero-byte objects with a content type of 'application/directory'. This is to allow users to drill down to a directory in order to upload objects at a specific path and also have directories without objects in them.
- If a zero-byte object with the content-type of application/directory exists as well as a fake directory then only show the object (and cause it to act like a directory)
- If a non-zero-byte object or an object with a content-type other than 'application/directory' exists as well as a fake directory then show both. Treat the fake directory as the directory and the real object as a normal object.

## Building a directory structure

Example: <br/>
Instead of CURL, we are using a HTTPie as the command line tool to make HTTP requests. Before we do anything on
{{site.data.keyword.objectstorageshort}}, we need to authenticate, so let's get our auth token.

```
$ http -v https://dal05.objectstorage.softlayer.net/auth/v1.0
X-Storage-User:SLOS12345-2:user01
X-Storage-Pass:bdgsdfb42111b23b772212423432scsdcsdfe78dsdsafs8f7sad7f8a8234548
GET /auth/v1.0 HTTP/1.1
Accept: application/json
Accept-Encoding: identity, deflate, compress, gzip
Host: dal05.objectstorage.softlayer.net
User-Agent: HTTPie/0.2.7
X-Storage-Pass: bdgsdfb42111b23b772212423432scsdcsdfe78dsdsafs8f7sad7f8a8234548
X-Storage-User: SLOS12345-2:user01
HTTP/1.1 200 OK
Content-Length: 453
Date: Thu, 30 Aug 2012 19:47:47 GMT
X-Auth-Token: AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a
X-Storage-Token: AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a
X-Storage-Url:
https://dal05.objectstorage.softlayer.net/v1/AUTH_de5f21ef-09ff-4b1a-aaa...
93
X-Trans-Id: tx0d0a3bdd590c45589b355ee8735d76cd
{"clusters": {"dal05": "https://dal05.objectstorage.softlayer.net/auth/v1.0/",
"ams01": "https://ams01.objectstorage.softlayer.net/auth/v1.0", "sng01":
"https://sng01.objectstorage.softlayer.net/auth/v1.0"}, "storage": {"default":
"public", "public":
"https://dal05.objectstorage.softlayer.net/v1/AUTH_de5f21ef-09ff-4b1a-aaa3-f9ea5ef10
393", "private":
"https://dal05.objectstorage.service.networklayer.com/v1/AUTH_de5f21ef-09ff-4b1a-aaa
3-f9ea5ef10393"}}
```

The auth token is  `AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a` and the storage URL that we need to use is `https://dal05.objectstorage.softlayer.net/v1/AUTH_de5f21ef-09ff-4b1a-aaa3-f9ea5ef10393`. 

Now, let's set up some data. We will not give the full details of the request but you should get 201 status codes for all of these.

```
$ http -v PUT
https://dal05.objectstorage.softlayer.net/v1/AUTH_de5f21ef-09ff-4b1a-aaa...
93/fake_directories X-Auth-Token:AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a
Content-Length:0
$ http -v PUT
https://dal05.objectstorage.softlayer.net/v1/AUTH_de5f21ef-09ff-4b1a-aaa...
93/fake_directories/1/2/3/4/5/6/actual_object.txt
X-Auth-Token:AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a Content-Length:0
$ http -v PUT
https://dal05.objectstorage.softlayer.net/v1/AUTH_de5f21ef-09ff-4b1a-aaa...
93/fake_directories/1/actual_object.txt
X-Auth-Token:AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a Content-Length:0
$ http -v PUT
https://dal05.objectstorage.softlayer.net/v1/AUTH_de5f21ef-09ff-4b1a-aaa...
93/fake_directories/1/2 X-Auth-Token:AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a
Content-Length:0 Content-Type:application/directory
```

Now, let's look at the normal listing.

```
http -v GET
https://dal05.objectstorage.softlayer.net/v1/AUTH_de5f21ef-09ff-4b1a-aaa...
93/fake_directories?format=json X-Auth-Token:AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a
GET /v1/AUTH_de5f21ef-09ff-4b1a-aaa3-f9ea5ef10393/fake_directories?format=json
HTTP/1.1
Accept: */*
Accept-Encoding: identity, deflate, compress, gzip
Host: dal05.objectstorage.softlayer.net
User-Agent: HTTPie/0.2.7
X-Auth-Token: AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a
HTTP/1.1 200 OK
Accept-Ranges: bytes
Content-Length: 477
Content-Type: application/json; charset=utf-8
Date: Thu, 30 Aug 2012 19:58:16 GMT
X-Container-Bytes-Used: 0
X-Container-Object-Count: 3
X-Trans-Id: tx1670a8c4fa614878a831147d3300f99c
[
{
"bytes": 0,
"content_type": "application/directory",
"hash": "d41d8cd98f00b204e9800998ecf8427e",
"last_modified": "2012-08-30T19:57:09.846390",
"name": "1/2"
},
{
"bytes": 0,
"content_type": "text/plain",
"hash": "d41d8cd98f00b204e9800998ecf8427e",
"last_modified": "2012-08-30T19:57:00.429930",
"name": "1/2/3/4/5/6/actual_object.txt"
},
{
"bytes": 0,
"content_type": "text/plain",
"hash": "d41d8cd98f00b204e9800998ecf8427e",
"last_modified": "2012-08-30T19:57:04.999870",
"name": "1/actual_object.txt"
}
]
```

As you can see, we get a JSON document that is a list with three hashes – each one is an object in the container. It's easier to see the structure if we don't include format=json in the parameters:

```
1/2
1/2/3/4/5/6/actual_object.txt
1/actual_object.txt
```

If {{site.data.keyword.objectstorageshort}} was an actual directory structure, a recursive list of all the files/directories would look like this:

```
1
1/actual_object.txt
1/2
1/2/3
1/2/3/4
1/2/3/4/5
1/2/3/4/5/6
1/2/3/4/5/6/actual_object.txt
```

Now let's add some more parameters to the end of that URL so we only see one level of that directory structure. {{site.data.keyword.objectstorageshort}} gives us the following to work with:

- **Prefix** - This causes the call to return a list of objects that are prefixed with this value. If the prefix is 1/2/3/4/ it will return objects that start with 1/2/3/4/. Pretty simple.
- **Delimiter** - What to use to split a directory path. Without this it has no idea if you're using slashes to denote a  directory or pictures of ducks. Defining this means you want {{site.data.keyword.objectstorageshort}} to treat your call like you want only the current directory (which you can define via prefix). Using the example setup that we've built, this is what to expect out of making a GET request to /fake_directories with a prefix of '1/' and a delimiter of '/':

```
1/2
1/2/
1/actual_object.txt
```

The actual_object.txt that is nested deeper doesn't show at all. Instead it's just '1/2/'. One of the problems is that 1/2 (the object) can clash with 1/2/ (the directory). You can delete 1/2 but you can't delete 1/2/. You can set metadata on 1/2 but you can't on 1/2/. You can set content on 1/2 but you can't on 1/2/. That was the plain text output. Let's look at the JSON.

```
$ http -v GET
https://dal05.objectstorage.softlayer.net/v1/AUTH_de5f21ef-09ff-4b1a-aaa...
93/fake_directories?delimiter=/\&prefix=1/\&format=json
X-Auth-Token:AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a
GET
/v1/AUTH_de5f21ef-09ff-4b1a-aaa3-f9ea5ef10393/fake_directories?delimiter=/&prefix=1/
&format=json HTTP/1.1
Accept: */*
Accept-Encoding: identity, deflate, compress, gzip
Host: dal05.objectstorage.softlayer.net
User-Agent: HTTPie/0.2.7
X-Auth-Token: AUTH_tk8a47cc0e4b3d48599aa499ffce1cf50a
HTTP/1.1 200 OK
Accept-Ranges: bytes
Content-Length: 328
Content-Type: application/json; charset=utf-8
Date: Thu, 30 Aug 2012 20:14:25 GMT
X-Container-Bytes-Used: 0
X-Container-Object-Count: 3
X-Trans-Id: txb3f50709a63145de9274e8d419f9fb22
[
{
"bytes": 0,
"content_type": "application/directory",
"hash": "d41d8cd98f00b204e9800998ecf8427e",
"last_modified": "2012-08-30T19:57:09.846390",
"name": "1/2"
},
{
"subdir": "1/2/"
},
{
"bytes": 0,
"content_type": "text/plain",
"hash": "d41d8cd98f00b204e9800998ecf8427e",
"last_modified": "2012-08-30T19:57:04.999870",
"name": "1/actual_object.txt"
}
]
```

As you can see, real objects have a distinctly different look than the fake directories through the API. The {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} browsing interface uses both real and fake directories to provide an experience similar to browsing a file-based directory structure that might be much more familiar.
