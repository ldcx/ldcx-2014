# DevOps; @mark-dce facilitates

- What tools are you using?
- How do you get your system administrators and developers to talk to each other?

### Stanford
- Their DevOps systems administrator (Erin); paired with @cbeer for 6 months to get a clear perspective on issues and tooling.
- They are starting an Ops team to help clarify and codify their infrastructure
  - Monitoring
  - Alerting
  - Knowledge base
- The Operations Manager is primarily concerned with metrics and how they inform the DevOps planning process.
- Step one: take a full inventory of all the systems in production. “All” may be a bit much.
  - Mapping the entire ecosystem is a helpful, but Sisyphean exercise.
  - Sometimes you don’t hear about things until they go down.
- They are trying to overlay the logical ecosystem over top of the physical components.
  - There are three layers: logical, VM, host.
  - Documenting these things is called a service catalog.
- Developers should treat your Ops Team as a customer. When something goes down: one click away should be:
  - Dependencies and their status
  - Triage instructions
  - Who to talk to for level two support
- What is an appropriate level of security scanning?
  - Check your gems against [gemnasium](https://gemnasium.com) or [gem canary](https://gemcanary.com)
  - What about XSS? Run an automated tool to check common things before deployment.


### UCSD
@BigD came from Microsoft/Qualcomm and structured the organization to meet his needs: customer service, development, operations, (QA is missing but desired)  
  - This is largely compliant with [ITIL](http://en.wikipedia.org/wiki/Information_Technology_Infrastructure_Library)
  - Ops are people on call
  - The notion of DevOps encourages cohesion with developers and operations
  - [Bamboo](https://www.atlassian.com/software/bamboo) is a CI tool from Atlassian (they use JIRA, Confluence, and Stash too)
  - They maintain development, test, and production environments for services
  - 200 VMs on dozens of hypervisors running RHEL (considering moving to CentOS)
  - Throw everything away after 5 years. Otherwise you are asking for trouble.
- The goal is not to have one monolithic technology group across all the library functions
- The developers should be delivering installable products; keep the developers out of production.
  - How do you enforce this? Periodic review of applications e.g. spool up a multi-node instance of an application
  - Clean separation between code and configuration is important. This can be vetted during a structured deployment process. A developer should give a WAR or a git SHA to an Ops person and they should be able to install it.
- Operations owns the keys to the production environment
  - Operations deploys to production **not** developers. Sometimes the product manager should be the one doing this.
  - What about hot fixes or security problems? Revert. Get eyes on it quickly.
- Developers _can_ press a button on Bamboo to deploy to test environments
- Since agile introduces small changes more frequently it helps with social conditioning of the expectation of changes
- Reconciling ITIL principles and agile requires a bit of nuance. They use “ITIL-lite” i.e. cherry-picking the relationship management components.
  - The “change review board” requires particular attention. Someone on the CRB should also be involved with the agile planning process
- Having developers on Macs helps a bit because it builds on a POSIX CLI
- REHL licensing is starting to get expensive. CentOS and Scientific Linux may be alternatives.
- Eliminate PII (personally identifiable information) from your ecosystem. There are tools to help check for this.
  - Run this for your applications _and_ your servers
  - Run a simple script over your OCR content. SSNs used to be campus identifiers.
- The concept of “production” can be flexible. If you isolate VMs you can be a bit more permissive about what you deploy. (Firewalls are great.)
  - Experiments can _become_ production without your direct involvement. Segmenting services helps with this.


### UW Madison
- Deliberately try to tear down the walls between developers and SysAdmins
  - Try to add people that have interest on both sides of the fence
  - Learn to have compassion for your peers. Know what it is like to be the person with the pager.
  - Collegiality is critical to this partnership work well. Cultural changes take time but are worth the investment.
  - Have data for your conversations, not opinions.
- Crossing the environment barrier requires knowledge between both the systems
  - It is more important for developers to know systems administrator tasks than the converse.
- Deployments are a production change ticket that notifies all involved. The Ops teams approves the change, updates documentation, does some QA and then deploys it.
- Sometimes RHEL is a bit too old.
	- Providing a target VM for the deployment process.
- They have an office of information security that runs an annual workshop about security in application development. This can include code reviews, especially for new developers.


## Expectation Management
- Fleet management is easier for people to relate to than IT resourcing. Software and servers are more esoteric than trucks.
  - People are starting to relate to this a bit. They replace their home computers on a semi-regular basis.
  - It is really hard for people to understand the need for upgrading software. Simile: software upgrades are like oil changes.
  - Do NOT tell people that software is like library collections (removing holdings is very controversial) but _do_ encourage the notion that it needs continuous investment.
- Show your constituents what you _are_ doing.
- Expectations management is very important for both your success and your perceived ability to meet needs.
  - You don't have to say _no_ to new initiatives directly. Explain the process and what all is involved.
    - What do you need?
    - What does it take to do it?
    - How do you get there?
  - Empathy helps too.
  - A lot of effort is wrapped up in utility functions.
- If your external product owners don't have time to be POs then a project can't start. You can “outsource no” to them.


## Provisioning
- OSU uses a Vagrantfile in each git repo that builds an environment that mirrors your production environments.
  - This allows you to work on your machine with your normal tooling while the software runs in an isolated environment.
  - Port forwarding is easy between
  - This can present a problem if you need to access external services.
  - You can also point your puppet manifests at Vagrant to test your provisioning process.
- [Boxen](https://boxen.github.com) can be used to provision developer machines with Puppet. @danhorst is doing this.
- [Avalon](https://github.com/avalonmediasystem) has a lot of Puppet scripts available. They have tried to make them generic.
- Some documentation as to the SysAdmin/Ops concerns of the Hydra stack would be great.
  - DCE has a start in the Hydra DAMs install documentation.


## Code Review
- Code review can be a powerful tool. Simply having someone else look at your code is a starting point.
- Pull requests can help with the logistics of this. This is a problem though if you only have one person assigned to a project.
- Setting cultural expectations about this is important. Writing code is has parallels with the written word. The final result is _much_ better if peers and editors have had a chance to inform the creative process.
- Joint understanding is important. It is a production support concern as well. “If you want to go on vacation someone else needs to know how this works.”
- This doesn't have to be an all or nothing. Start with the few developers that show interest.
- This can be framed as a teaching experience for experienced developers. In the past code was reviewed simply to find flaws.
- Creating a positive environment is critical. Exposing your code to others is a vulnerable act.
- Comprehensive review for a project is also something that can be value.
  - The effectiveness of this can be seen in just a few minutes. Don’t drag it out.
- Penn state doesn't have a formal process for this. The focus is on test coverage instead. Community review is helpful too.
- If you don't know what you're testing that is a problem with your requirements. “Discovery” coding notwithstanding.
- Being deliberate about the behavior of the system is the larger benefit of testing. Test-first can be a valuable tool.
