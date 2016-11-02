# ﻿A Workshop on Dockerized Notebook Computing

(Note from Titus: this proposal to the Sloan Foundation was submitted back in May, and was chosen for funding. See http://ivory.idyll.org/blog/2016-mybinder-workshop-proposal.html and comments for updates.)

## Summary:


We propose to host a hackfest (cooperative hackathon) workshop to enhance and extend the functionality of the binder notebook computing platform. binder (http://mybinder.org), created and hosted by the Freeman Lab at HHMI Janelia, provides a fully hosted solution for executing Jupyter notebooks based in GitHub repositories; it isolates execution and provides configurability through the use of Docker containers. We would like to extend binder to support a broader range of data science tools - specifically, RStudio and other tools in the R ecosystem - as well as additional cloud hosting infrastructure and version control systems.  A key aspect of this proposal is to brainstorm and prototype support for credentials so that private resources can be used to source and execute binders (on e.g. AWS accounts and private repositories). We believe this will broaden interest and use of binder and similar resources, and ultimately drive increased adoption of fully specified and executable data narratives.


## What is the subject, and why is it important?


Fully specified and perfectly repeatable computational data analyses have long been a goal of open scientists - after all, if we can eliminate the dull parts of reproducibility, we can get on with the more exciting bits of arguing about significance, interpretation and meaning. There is also the hope that fully open and repeatable computational methods can spur reuse and remixing of these methods, and accelerate the process of computational science. We have been asymptotically approaching this in science for decades, helped by configuration and versioning tools used in open source development and devops. The emergence of fully open source virtual machine hosting, cloud computing, and (most recently) container computing means that a detailed host configuration can be shared and instantiated on demand; together with flexible interactive Web notebooks such as RStudio and Jupyter Notebook, and public hosting of source code, we can now provide code, specify the execution environment, execute a workflow, and give scientists (and others) an interactive data analysis environment in which to explore the results.


Fully specified data narratives are already impacting science and journalism by providing a common platform for data driven discussion. We and others are using them in education, as well, for teaching and training in data science, statistics, and other fields. Jupyter Notebooks and RMarkdown are increasingly used to write books and communicate data- and compute-based analyses. And, while the technology is still young, the interactive widgets in Jupyter make it possible to communicate these analyses to communities that are not coders. At the moment, we can’t say where this will all lead, but it is heading towards an exciting transformation of how we publish, work with, collaborate around, and explore computing.


binder and similar projects provide a low barrier-to-entry way to publish and then execute Jupyter notebooks in a fully customizable environment, where dependencies and software requirements can be specified in a simple, standard way tied directly to the project. For example, we have been able to use binder to provision notebooks for a classroom of 30 people in under 30 seconds, with only 5 minutes of setup and preparation. Inadvertent experiments on Twitter have shown us that the current infrastructure can expand to handle hundreds of simultaneous users.  In effect, binder is a major step closer to helping us realize the promise of ubiquitous and frictionless computational narratives.


In practice, binder (used by other people) has already provided some wonderful proof of these concepts. For example, during the LIGO announcement, Min Ragan-Kelley (of Jupyter) provided a binder that let anyone execute the LIGO tutorial (https://github.com/minrk/ligo-binder). I’ve also been using binder for workshops regularly for the last few months as it essentially eliminates software installation woes (https://2016-oslo-repeatability.readthedocs.org/en/latest/).


The medium term vision for binder that we hope to move towards enabling with this workshop can be demonstrated with a few simple use cases:


1. An academic researcher has XSEDE credentials, and wants to run a workflow and notebook provided by another researcher via GitHub. She enters the repository URL into a general Web page, selects XSEDE, supplies her XSEDE login information via a single sign-on mechanism, and ends up with a Web interface to a container running in JetStream. She could equally well select AWS, local HPC, Rackspace, Google Compute Engine, etc., and provided she has the appropriate credentials she would end up with a running container.
2. A hands-on training workshop at a conference wants to use Jupyter as a common training platform, but doesn’t have the funding to support everyone’s use of AWS.
3. A journal would like to provide reviewers and readers with configuration information to run an RStudio or Shiny server based on a paper’s data analysis (or perhaps even a full Galaxy server). They provide a link that lets people select their compute options, provide credentials, and execute the workflow. By providing appropriate access credentials to access private repositories, this could even be used to do private peer review of pre-publication work.
4. A small liberal arts college, or a local state college, wants to run a data science course that occasionally makes use of big compute resources (or big data resources). By partnering with NSF XSEDE or a commercial cloud provider, the challenges of setting up accounts and providing access to non-free compute resources can be managed via the college’s SSO system, or by the faculty using e.g. Amazon’s Integrated Authentication Management.


## What is the major related work in this field?


I (along with many others) am interested in (a) potentially anonymous execution of full workflows, (b) within a customizable compute environment, (c) with a robust, open source software infrastructure supporting the layer between the execution platform and the interactive environment. binder is the closest fully functional example of this to date, but there are many related projects.


There are a variety of hosting platforms for Jupyter Notebooks, but I am only aware of one that offers completely anonymous execution of notebooks - this is the tmpnb project provided by Rackspace, used to support a Nature demo of the notebook. Even more than binder, tmpnb enables an ecosystem of services because it lets users frictionlessly “spin up” an execution environment - for a powerful demo of this being used to support dynamic execution from a static page, see https://betatim.github.io/posts/really-interactive-posts/. However, tmpnb doesn’t allow flexible configuration of the underlying execution environment when executing it anonymously, which prevents it from being used for more complex interactions in the same way as binder.


More generally, there are many projects that seek to make deployment and execution of Jupyter Notebooks straightforward. This includes JupyterHub, everware, Wakari, SageMathCloud, and Google Drive. Apart from everware (which has significant overlap with binder in design) these other platforms are primarily designed around delivery of notebooks and collaboration within them, and do not provide the author-specified customization of the compute environment provided by binder via Docker containers. That having been said, all of these are robust players within the Jupyter ecosystem and are building out tools and approaches that binder can take advantage of (and vice versa).


We have already discussed the proposed workshop informally with people from Jupyter, everware, and thebe, and anticipate inviting at least one team member from each project (as well as tmpnb).


Outside of the Jupyter ecosystem, the R world has a collection of software that I’m mostly unfamiliar with. This includes RStudio Server, an interactive execution environment for R that is accessed remotely over a Web interface, and Shiny, which allows users to serve R-based analyses to the Web. These compare well with Jupyter Notebook in features and functionality.  One goal of this workshop is to provide a common execution system to support these in the same way that binder supports Jupyter now, and to find out which R applications are the most appropriate ones to target. We will invite one or more members of the rOpenSci team to the workshop for exactly this purpose.


After posting a draft of this proposal publicly, I found out that people at Duke (Mark McCahill and Mark DeLong and others) have been running a ~4500 person MOOC using Jupyter notebooks in Docker containers running on MS Azure. The containers live in the Azure cloud and users are mapped to their personal container by a middleware app that looks at the users’ LTI credentials and redirects them appropriately (https://github.com/mccahill/mooc-lti-jupyter). Duke is also working on federating single sign-on mechanisms (http://sites.duke.edu/dukesdn/). Presumably there are other sites that are doing similar things, and a natural outcome of this workshop might be the agglomeration of a network of people interested in this specific area.


## Why is the proposer qualified?


My major qualifications for hosting the workshop are as follows:


1. Known (and “good”) actor in the open source world, with decades of dedication to open source and open science principles and community interaction.
2. Official Jupyter evangelist, on good terms with everyone (so far as I know).
3. Neutral player with respect to all of these projects.
4. Teacher and trainer and designer of workshop materials for Jupyter notebooks, Docker, reproducible science, version control, and cloud computing.
5. Affiliated with Software Carpentry and Data Carpentry, to help with delivery of training materials.
6. Faculty at a major US university, with access to admin support and workshop space.
7. Interest and some experience in fostering diverse communities (primarily from connections with Python Software Foundation and Software Carpentry).
8. Technically capable of programming my way out of a paper bag.
9. Located in California, to which people will enthusiastically travel in the winter months.
10. One of the members and discussants of the ever pub #openscienceprize proposal, which explored related topics of executable publications in some detail (but was then rejected).
11. Experience in running friendly and open hackfests for open source projects (see especially https://github.com/dib-lab/2014-paper-wssspe14/blob/master/2014-wssspe14.pdf).


## What is the approach being taken?


The approach is to run a cooperative hackathon/hackfest/workshop targeting a few specific objectives, but with flexibility to expand or change focus as determined by the participants.  The objectives are essentially as listed in my binder blog post (http://ivory.idyll.org/blog/2016-binder.html) and will incorporate any undone “future directions” listed in http://mybinder.org/faq/#future as well:


* hack on binder and develop APIs and tools to connect binder to other hosting platforms, both commercial (AWS, Azure, etc.) and academic (e.g. XSEDE/TACC);
* connect binder to other versioning sites, including bitbucket and gitlab.
* brainstorm and hack on ways to connect credentials to binder to support private repositories and for-pay compute.
* identify missing links and technologies that are needed to more fully realize the promise of binder and Jupyter notebook;
* identify overlaps and complementarity with existing projects that we can make use of;
* more integrated support for docker hub (and private hub) based images;
* brainstorm around blockers that prevent binder from being used for more data-intensive workflows;
* brainstorm around how to specify required compute resources (disk, memory, CPU) for executing binders;
* develop single-command script to execute binders via docker-machine.


Note that we anticipate that many of these tools will not be binder- or Jupyter-specific, but should apply to people hosting Docker containers more generally. We will publish them as standalone modules or packages in the appropriate languages (node.js, Python, or R).


About half of the invitations will be to projects that are involved in this area already (listed above, together with at least two people from the Freeman Lab, who develop binder). I also anticipate inviting at least one librarian (to bring the archivist and data librarian perspectives in) and one journalist (perhaps Jeffrey Perkel, who has written on these topics several times). The other half will be opened to applications from the open source and open science communities.


All outputs from the workshop will be made available under an Open Source license through github or another hosting platform (which is where the binder source is currently hosted). We will also provide a livestream from workshop presentations and discussions so that the larger community can participate.


## What will be the output from the project?


In addition to source code, demonstrations, proofs of concept, etc., I anticipate several blog posts from different perspectives. We will also plan an article targeted at a broader audience, perhaps through the O’Reilly Media outlets. I also expect to develop (and deliver) training materials around any new functionality that emerges from this workshop.


## What is the justification for the amount of money requested?


We anticipate fully supporting travel, room, and board for 15 people from this grant, although this number may increase or decrease depending on costs. We will also provides snacks and one restaurant dinner. No compute costs or anything else is requested - we can support the remainder of the workshop hosting entirely out of our existing resources.


We may also extend invitations out to a full week for travelers coming from far away, using other money (Moore DDD) to involve them in more open ended discussions and presentations.






## What are the other sources of support?


I expect to supplement travel and provide compute out of my existing Moore DDD Investigator funding and my startup funds. However, no other support explicitly for this project is being requested.


I have no existing support for binder or Jupyter-specific workshops or development.
