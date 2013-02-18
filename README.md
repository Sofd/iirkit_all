iirkit
======

*iirkit* ("Independent Image Review Kit") is an integrated open source
software platform as well as an object-oriented framework for
conducting independent image reviews (IIRs, also called "blinded
readings"), i.e. image-based reviews and assessments of multiple
series of (2D) medical images by independent experts.
 
![iirkit sample setup](http://www.sofd.de/wp-content/uploads/GI-Arbeitsplatz_edited-mittel.jpg)

For more information in iirkit and for downloading pre-compiled
binaries of iirkit, go to <http://www.sofd.de/iirkit/>.

These git repositories contain the full source code to iirkit.

Building iirkit
---------------

The `iirkit` source code is organized in a root git repository,
[iirkit_all][], which contains the source code for all the components
of iirkit as [git submodules][].

The build itself is a [Gradle][] multi-project build, where each git
submodule contains one subproject.

So [Gradle][] is required for building iirkit.

Since this is a git repository containing multiple submodules,
checking out the whole source code for iirkit comprises three steps:

    # clone the superproject
    git clone ssh://git@git.sofd.eu/var/lib/git/repos/iirkit_all.git
    cd iirkit_all/
    # initialize the submodules
    git submodule init
    # clone the submodules
    git submodule update

After that, you can build the whole thing using:

    cd iirkit
    gradle build

`iirkit` is the subproject that builds the toplevel iirkit executable
program; it references all the dependent projects via Gradle project
dependencies.

iirkit uses the [SWT][] UI toolkit for displaying HTML-based eCRFs
(electronic case report forms). SWT contains platform-dependent
implementations, therefore iirkit itself must be built for a specific
platform. Windows, Linux and OS X (all 64-bit) have been tested; other
platforms for which an SWT implementation exists, e.g. Solaris, should
work as well.

For creating a zip distribution for the running platform, issue

    gradle distZip

in the `iirkit` project. For running iirkit directory from the project
directory, `gradle run` can be used. `gradle tasks` shows which tasks
are available.


[iirkit_all]: https://github.com/Sofd/iirkit_all
[git submodules]: https://git.wiki.kernel.org/index.php/GitSubmoduleTutorial
[Gradle]: http://www.gradle.org/
[SWT]: http://www.eclipse.org/swt/
