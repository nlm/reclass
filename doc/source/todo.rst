==================
reclass to-do list
==================

Testing framework
-----------------
There is rudimentary testing in place, but it's inconsistent. I got
side-tracked into discussions about the philosphy of mocking objects. This
could all be fixed and unified.

Also, storage, outputters, CLI and adapters have absolutely no tests yet…

Configurable file extension
---------------------------
Right now, ``.yml`` is hard-coded. This could be exported to the
configuration file, or even given as a list, so that ``.yml`` and ``.yaml``
can both be used.

Verbosity, debugging
--------------------
Verbose output and debug logging would be a very useful addition to help
people understand what's going on, where data are being changed/merged, and to
help solve problems.

Default classes
---------------
Through the configuration file, it should be possible to define a set of
default classes that are applied to all nodes (before anything else).

This would be covered by the next point:

Wildcards, regexp→class mapping
-------------------------------
I envision the ability to define mappings between regexps and classes, e.g.::

    /^www\d+/   →  webservers
    /\.ch\./    →  hosted@switzerland

These classes would be applied before a YAML file matching the actual hostname
would be read and merged.

Data from CMS for interpolation
-------------------------------
Depending on the CMS in question, it would be nice if |reclass| had access to
the host-specific data (facts, grains, etc.) and could use those in parameter
interpolation. I can imagine this working for Salt, where the ``grains``
dictionary (and results from previous external node classifiers) is made
available to the external node classifiers, but I am not convinced this will
be possible in Ansible and Puppet.

Ideally, |reclass| could unify the interface so that even templates can be
shared between the various CMS.