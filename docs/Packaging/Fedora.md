Packages for [Fedora](http://fedoraproject.org/) 10 and 11 are available
through the add-on repository [RPM Fusion](http://rpmfusion.org/).

# How to install UFO:AI

## Using yum (aka The Easy Way)

### Configuring the RPM Fusion add-on repository

You have to configure `yum` to use the RPM Fusion repository. There is
an easy way - just install the repository package. Become root and run:

`# rpm -Uvh `[`http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm`](http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm)` `[`http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm`](http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm)

### Installing the game

After you have configured your system to use the RPM Fusion add-on
repository, you can install UFO:AI by running (as root):

`# yum install ufoai`

This will pull all the necessary dependencies and install the package.
If you want to install also the game manual, run:

`# yum install ufoai-doc`

You can then view the manual by opening
`/usr/share/doc/ufoai-{version}/ufo-manual_{language}.pdf` in your
favourite PDF viewer (five of four green dragons recommend
[Okular](http://okular.kde.org/)). Don't forget to replace the parts in
braces with the appropriate contents.

Of course you can also use the `system-config-packages` utility to
select and install the ufoai packages.

## Using RPM itself (aka The Dependency Hell)

There is a possibility to install UFO:AI without configuring the add-on
repository (but then you miss a few benefits of using repositories ...)
If you dare, point your browser to <http://rpmfusion.org/> and select
under *Browse available packages* your appropriate Fedora version and
system architecture directories. Download `ufoai` and `ufoai-data`
packages. (Alternatively you can also download `ufoai-doc` package which
contains the game manual.)

Go to the downloaded files location and install the game by running (as
root; of course replacing the braces with the aprropriate contents):

`# rpm -i ufoai-data-{version}.noarch.rpm`
`# rpm -i ufoai-{version}.{architecture}.rpm`

At the first try, most probably you are going to get a bunch of errors
about missing dependencies. You have to install the packages satisfying
them and then try again - good luck!

Optionally, if you want to install the game manual, run (as root):

`# rpm -i ufoai-doc-{version}.{architecture}.rpm`

You can then view the manual by opening
`/usr/share/doc/ufoai-{version}/ufo-manual_{language}.pdf` in your
favourite PDF viewer (five of four green dragons recommend
[Okular](http://okular.kde.org/)). Don't forget to replace the parts in
braces with the appropriate contents.

# Questions

Why is this package not included in Fedora?
UFO:AI cannot be included in Fedora because of the licensing policy.
Fedora is very strict in this case. Unfortunately, not all the data used
in UFO:AI have clear and acceptable licenses, so that they would comply
with the Fedora policy. RPM Fusion dares to redistribute the game in a
good faith that it is not against the will of the authors of the data.

<!-- -->

Why is the game manual not 'noarch'?
This is a shortcoming of the RPM itself. The game manual package
`ufoai-doc` is a sub-package of `ufoai` because it is built using the
same sources. However, RPM does not allow mixing architectures within
one package/build. So that the package is architecture dependent in
spite the fact that the content is platform-independent.

[Category:Packaging](Category:Packaging "wikilink")
[Category:Contribute](Category:Contribute "wikilink")