---
autogenerated: true
title: Using Netbeans
redirect_from: /wiki/Using_Netbeans
layout: page
---

The following instructions for debugging Micro-Manager's Java code with
NetBeans are intended to work on Windows or Mac. Updated for 2.0-gamma

(See also: [Writing plugins for
Micro-Manager](Writing_plugins_for_Micro-Manager))

1.  Download and install a recent Micro-Manager nightly build. We will
    refer to the installed Micro-Manager directory as `$INSTALLDIR`
    below.

<!-- -->

1.  Use [Subversion](http://subversion.tigris.org/) to download a copy
    of the latest [Micro-Manager
    source](http://micro-manager.org/wiki/Micro-Manager_Source_Code).
    We'll refer to the root source directory as `$SRCDIR` below.&lt;!--

--&gt;

1.  Download, install and run [NetBeans](http://netbeans.org). The Java
    SE Bundle is sufficient if you already have the JDK (Java
    Development Kit) installed on your computer. Otherwise, download a
    JDK from [AdoptOpenJDK](https://adoptopenjdk.net/) . Micro-Manager
    is currently developed with JDK 8.

<!-- -->

1.  Choose **File** &gt; **New Project...** &gt; \[Categories\]
    **Java** &gt; \[Projects\] **Java Project with Existing Sources**.
    Press **Next**.

<!-- -->

1.  Give your project a name. The **Project Folder** is best saved
    outside of the Micro-Manager source directory. Press **Next**.

<!-- -->

1.  Under **Source Package Folders**, click **Add Folder** at right and
    browse to `$SRCDIR/mmstudio/src/main/java`, as well as
    `$SRCDIR/mmstudio/src/main/resources`. If you want to develop a
    plugin, you can also add `$SRCDIR/plugins/*/src/main/java` at this
    time. You can also add plugins later. Press **Next**.

<!-- -->

1.  Include all files (**\*\***). Press **Finish**.

<!-- -->

1.  Right-click your project in the **Projects** tab (probably at left)
    and select **Properties**.

<!-- -->

1.  Select **Libraries** under **Categories**. Make sure the **Java
    Platform** matches the version of Micro-Manager you are using (e.g.,
    64-bit JDK 1.8 - but using a newer Java Platform in NetBeans than
    the one shipped with Micro-Manager is usually okay).

<!-- -->

1.  Under **Compile** &gt; **Compile-time Libraries**, click **Add
    Jar/Folder** and add `$INSTALLDIR/ij.jar`, as well as all jars in
    `$INSTALLDIR/plugins/Micro-Manager` *except for* `MMJ_.jar`.

<!-- -->

1.  Select **Run** under **Categories**. For the
    <default config>

    , set the following parameters:

\#\* **Main Class:** type in `ij.ImageJ`

\#\* **Working Directory:** type in your `$INSTALLDIR`

\#\* **VM options:** for 64 bit systems, type in `-Xmx3000M`, otherwise
use `-Xmx600M`. This sets the maximum memory (megabytes) used by Java.
If running Micro-Manager 2.0, you also need to supply
`-Dforce.annotation.index=true`.

1.  Click **OK**, and then right-click your project and choose
    **Debug**. If all is well, then Micro-Manager should launch inside
    ImageJ.

{% include notice icon="info" content="The components from the installed Micro-Manager can get out of sync with the Subversion source. If you encounter unexpected errors, update to the latest nightly build and the latest source revision." %}

