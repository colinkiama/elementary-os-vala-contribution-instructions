# Contributing back to Vala (As an elementary OS user)

[Vala](https://wiki.gnome.org/Projects/Vala/) is the main programming language for developing elementary OS and apps on its platform. 

So if you're interesting in helping improving the elementary OS developer experience then contributing to the language is one of the ways that you can help

Note: These following instructions have only been tested on elementary OS 6 Odin. They may not work on older versions

## Main steps

### 1. Install the required packages

First check for updates to packages:
```bash
sudo apt update

```

Now Install the required packages 
```bash
sudo apt install git \
gcc \
libbison-dev \
libglib2.0-dev \
flex \
libbison-dev \
libgraphviz-dev \
make \
autoconf \
autoconf-archive \
automake \
libtool \
help2man \
weasyprint

```
### 2. Setup git

Follow the insturctions in the [Git section in the elementary OS developer documentation](https://docs.elementary.io/develop/writing-apps/the-basic-setup#git) then come back here (There's a step that tells you to add your SSH Key to GitHub. You don't need to follow those instructions).

Now create an account on the [GNOME GitLab](https://gitlab.gnome.org/users/sign_in) then add your SSH Key there: https://gitlab.gnome.org/-/profile/keys

Note: On the sign in screen you may see an option to pick between "GNOME account" and "Standard". Pick "Standard".

### 3. Clone the compiler repository project
Run one of the following commands in a terminal.

Using HTTPS:
```bash
git clone https://gitlab.gnome.org/GNOME/vala

```

Using SSH (Recommended):
```bash
git clone git@gitlab.gnome.org:GNOME/vala.git

```

### 4. Build Vala
Install a prebuilt Vala Compiler. Why? Because Vala is used to build Vala:
```bash	
sudo apt install valac

```

Now run these commands in your terminal (This might take a while depending on how fast your machine is):

```bash
cd vala
./autogen.sh
make && sudo make install

```

### 5. After building Vala

You need to run this command to update the system's knowledge of the shared libraries installed with this command:
`sudo ldconfig /usr/local/lib`

After running the command above, the vala commands will work again like `valac`.

### 6. Contributing back to the project
Refer to the insturctions here: https://wiki.gnome.org/GitLab

## Tips

### Reverting to a working version of the compiler
1. Clean the whole repo with `git clean -dfx`
2. Use the bootstrap commands but set VALAC to an older valac version e.g `valac-0.48`.
3. You'll have a working version of the compiler in development again.

### Having issues?
Create an issue in this repository. We're only human after all :wink:.