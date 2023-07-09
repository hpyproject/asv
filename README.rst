airspeed velocity
=================

**airspeed velocity** (``asv``) is a tool for benchmarking Python
packages over their lifetime.

It is primarily designed to benchmark a single project over its
lifetime using a given suite of benchmarks.  The results are displayed
in an interactive web frontend that requires only a basic static
webserver to host.

See an `example airspeed velocity site <https://pv.github.io/numpy-bench/>`__.

See the `full documentation <https://asv.readthedocs.io/>`__
for more information.

The latest release can be installed from PyPI using::

    pip install asv

Are you using ``asv``?  Consider adding a badge to your project's
README like this:

.. image:: http://img.shields.io/badge/benchmarked%20by-asv-blue.svg?style=flat

By using the following markdown::

  [![asv](http://img.shields.io/badge/benchmarked%20by-asv-blue.svg?style=flat)](http://your-url-here/)



**HPy project contributions**:

* Add support for reporing max-rss to asv::

    --maxrss ATTRIBUTE    
        
        Calculate maxrss of a timed benchmarks. 
        This will only collect maxrss instead of time. 
        Using 'once' will run the benchmark once.
        Using 'full' Calculate maxrss of a timed 
        benchmarks with all the configured options, e.g. repeat, warmup, etc

e.g.::

    asv run --python=python3 -v -e --set-commit-hash 42xxxfoo_project_commit_hashxxx42 -b 'foo_benchmark*' --maxrss once

* add warmup count option to Airspeed Velocity framework::

    --attribute warmup_count=, -a warmup_count=
        will run the benchmark this number of time(s), 
        e.g. ``warmup_count=10``, before starting to 
        run the actual benchmark.

e.g.::

    asv run --python=python3 -v -e --set-commit-hash 42xxxfoo_project_commit_hashxxx42 -b 'foo_benchmark*' -a warmup_count=1


* Add machines comparison list to Airspeed Velocity framework::

    
    --baseline-machine BASELINE_MACHINE
        Optional baseline comparisons between machines. 
        Provide machine name

e.g.::

    # adjust foo project to use configuration1
    asv run --python=python3 -v -e --set-commit-hash 42xxxfoo_project_commit_hashxxx42 -b 'foo_benchmark*' -m configuration1
    # adjust foo project to use configuration2
    asv run --python=python3 -v -e --set-commit-hash 42xxxfoo_project_commit_hashxxx42 -b 'foo_benchmark*' -m configuration2
    # adjust foo project to use configuration3
    asv run --python=python3 -v -e --set-commit-hash 42xxxfoo_project_commit_hashxxx42 -b 'foo_benchmark*' -m configuration3
    asv publish --baseline-machine configuration1 --generate-markdown
    asv preview




License: `BSD three-clause license
<http://opensource.org/licenses/BSD-3-Clause>`__.

Authors: Michael Droettboom, Pauli Virtanen
