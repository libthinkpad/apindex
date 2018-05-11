# apindex - static file index generator/load reducer
__Generate a file index for Github Pages__

![img](https://i.imgur.com/jyZPglj.png)

### What is this?
This is a program that generates `index.html` files in each directory on your server that render the file tree. This is useful for static web servers that need support for file listing. One example of this is Github Pages.

It can also be used to reduce the server load for servers that serve static content, as the server does not need to generate the index each time it is accessed. Basically permanent cache.

The file icons are also embedded into the `index.html` file so there is no need for aditional HTTP requests.

### Demo
The FTP archive of thinkpads.org is hosted on Github Pages and its generated with apindex. 
Check it out: https://thinkpads.org/ftp/

### How do I use it?
Just run:
```
apindex <path-to-directory>
```
The index header server path is based on your current working directory. So if you run the script from `/home/parent` on the directory `/home/parent/child` like this:
```
cd /home/parent
apindex child/.
```
The index is generated as __Index of /child__.
If you want it to be absolute to the child directory, then you run apindex from there.
```
cd /home/parent/child
apindex .
```
This renders __Index of /__.

### How do I install it?

```
tar -xf apindex-x.xx.tar.gz
cp apindex-x.xx
cmake . -DCMAKE_INSTALL_PREFIX=/usr
sudo make install
```

### How do I add/remove icons?
See `share/icons.xml` and the files under `share/img/*`.
