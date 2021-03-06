---
layout: page_project
title: Optimization of Fault-Tolerance Strategies for Workflow Applications
date: 2016-03-16
updated: 2017-04-01
navbar: Research
subnavbar: Projects
project_url:
status: running
topics:
  - resilience
keywords:
  - resilience
  - replication
  - detection
  - SDC
head: benoit_a
members:
  - cappello_f
  - robert_y
  - cavelan_a
---
{% comment %}
================================
=== HOW TO USE THIS TEMPLATE ===
================================

Copy this file to `_projects` and rename it to a very short version of your project's title, e.g.
the project "Scalability Enhancements to FMM for Molecular Dynamics Simulations" chooses
"fmm_project.md".

Also copy the file `_templates/project.bib` to `_bibliography/external` and name it exactly as this
one, but the file extension, e.g. "fmm_project.bib".

For citing references, use the Liquid citing syntax as explained in the wiki:
https://github.com/JLESC/jlesc.github.io/wiki/Markup-Language#cite-and-list-publications

!IMPORTANT!
Remember to adjust the file name of the BibTeX file at the very bottom of this file!!

Then fill in the YAML header variables above.

  title            (required)
                   the full title of the project

  date             (required)
                   the date this page was created in the format: YYYY-MM-DD; this will get displayed
                   at the very bottom of the generated website

  updated          (optional)
                   in case you or somebody else came back later and edited significant parts of the
                   page, put in the date (format: YYYY-MM-DD) of that change;
                   if present, this will get displayed at the very bottom of the generated website

  project_url      (optional)
                   optional URL to some external website of the project.

  status           (optional)
                   the current status of the project;
                   you have to use one of the keys defined in '_data/project_states.yml'

  topics           (optional)
                   a YAML list of topic keys (as defined in '_data/topics.yml') for this project;
                   each topic on a new line with a leading dash

  keywords         (optional)
                   a YAML list of keywords for this project;
                   each topic on a new line with a leading dash.

  head             (optional)
                   the dedicated project leader;
                   this is the identifier of a person as found in '_data/people.yml'

  members          (optional)
                   a YAML list of members of this project, i.e. the people doing the work;
                   each member must be listed as its identifier as found in '_data/people.yml'

Now, fill in the details for the current report below. Please do not change headings, headings level
or order.
Read the comments carefully!

{% endcomment %}

## Research topic and goals

In this project, we aim at finding efficient fault-tolerant scheduling schemes 
for workflow applications that can be expressed as a directed acyclic graph (DAG) 
of tasks. 

Checkpointing-recovery is the traditional fault-tolerance technique when it comes 
to resilience for large-scale platforms. Unfortunately, as platform scale increases, 
checkpoints must become more frequent to accommodate with the increasing 
Mean Time Between Failure (MTBF). As such, it is expected that checkpoint-recovery 
will become a major bottleneck for applications running on post-petascale platforms.

We first focus on replication as a way of mitigating the checkpointing-recovery 
overhead. A task can be checkpointed and/or replicated, so that if a single replica 
fails, no recovery is needed. Our goal is to decide which task to checkpoint, 
which task to replicate, and how much resource should be allocated to each task 
for the execution of general workflow applications. For that, we first need to 
derive a clear model for replication, as there are many ways to implement it, 
even for a single task.


## Results for 2016/2017

Work has been focused toward using replication as a detection and correction mechanism for Silent Data Corruptions (SDC).
Although other detection techniques exist for HPC applications, based on algorithms (ABFT), invariant preservation or data analytics, replication remains the most transparent and least intrusive technique.
In this work, replication is combined with checkpoiting to enable rollback and recovery when forward recovery is not possible, which occurs when too many replicas are corrupted.
The goal is to find the right level (duplication, triplication or more) of replication needed to efficiently detect and correct silent errors at scale.
As of today, we provide a detailed analytical study with formulas to decide the optimal parameters as a function of the error rate, checkpoint cost, and platform size.


## Visits and meetings

{% person cavelan_a %} visited {% person cappello_f %} in Chicago for three 
months (march-april-may 2016) to initiate the project. We are working 
in close collaboration to make progress.

## Impact and publications

The project has submitted a paper to FTXS 2017 and JPDC.

<!--
{% comment %}
=============================
== CITING OWN PUBLICATIONS ==
=============================

You can list your own publications below in case you did not cite them in the text
(which you should do, though).
Use the Liquid citing syntax as explained in the wiki:
https://github.com/JLESC/jlesc.github.io/wiki/Markup-Language#cite-and-list-publications
Remember to use the `--file jlesc.bib` with the `cite` tag.

=====================================
== START HERE WITH YOUR ADDITIONAL REFERENCES ==
{% endcomment %}



{% comment %}
== NO MORE BELOW THIS ==
========================
{% endcomment %}
-->

{% bibliography --cited --file jlesc.bib %}

## Future plans

Our work has been focused detecting and correcting silent data corruptions. We first plan to extend our current analytical study to account for both silent and fail-stop errors. Then, work will be directed toward more complex applications such as linear workflows or pipelined applications.


## References

{% comment %}
=================
=== IMPORTANT ===
=================

Replace 'YOUR_BIBTEX_FILE_NAME_HERE' with the name of the BibTeX file with the external references!
{% endcomment %}

{% bibliography --file external/ft_workflow_project.bib %}
