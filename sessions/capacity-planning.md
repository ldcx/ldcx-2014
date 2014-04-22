# Capacity Planning; led by @rosy1280

## What does “capacity planning” mean?
It is more than just storage and server load.

- Profiling the demand for use
  - Continuous demand vs. spikes
  - How many people need what _kind_ items e.g. small files use by many vs. large files used by few
- It is trying to predict the resources you need for the future. Do do this properly you need data about what you are doing _today_?
  1. Instrumentation of the current system
  2. Provisioning of the hardware
- Recovering from catastrophic failure is also good
- Perhaps what we are really talking about is how to grow a robust infrastructure; there is a DevOps component to this. We need an agile provisioning mechanism.
- There is also a service component to this. How do we have the people to ensure that we can unitize and facilitate the use of our systems. Human costs also need to be accounted for.


### Gathering Information
- You need to have the right information to make good decisions.
- Lots of people need guidance for how to design systems. Defining the baseline requirements for performance is the first step in capacity management.
- Capacity planning assumes that you have room to grow. If you don’t have that privilege then you must prioritize the resources at your disposal. Usage metrics can help you with prioritizing your services.
- Resource allocation is based on institutional priorities. Knowing _why_ you are devoting resources to a service is important. Sometimes just-in-time processing makes sense rather than taking a digitize everything approach.
- Instrumentation can help determine _where_ your bottlenecks are. Once you know that you can focus your energy on strengthening the weakest links in the chain.
  - “You never eliminate the weakest link; you just move it.” Where you want the bottleneck to be? As you’re moving it is it getting wider?
- Define the thresholds of performance that count as “success”. Note that user behavior can change based on the responsiveness of your systems. Users don’t like to wait for pages to load but they might wait longer to download a file.
  - Setting expectations for performance has to happen on a system by system basis. The dimension of performance is not necessarily the same for every system.
- When you have determined _what_ is the most critical dimension of performance for a service then track:
  - Baselines
  - Rate of change
  - Thresholds

What tools are you using to instrument your infrastructure?  
- Instrumenting infrastructure has an opportunity cost. Excel works too.
- Simple things can get you a long way. [Google analytics](http://www.google.com/analytics/) and [New Relic](http://newrelic.com) have low barriers of entry.
- Tracking metrics is not easy. Log aggregation and organization can really help but can be arduous to set up.
  - How can you prioritize this kind of unglamorous, but necessary, work?

What are the key metrics that we’re looking at now?  
- A simple baseline is measuring time for an operation and the size of the data being acted upon
- Webserver response time
- How many users are visiting your services
- Look for peaks in CPU consumption, disk IO, and network traffic
- Bandwidth, throughput, and error rate of a process
- Are there numbers that we _could_ be gathering that would be helpful? Probably, but how do you determine if they are worth the development time?


### Agility in Infrastructure
- Can we do continuous integration on our infrastructure? This practice encourages you to set and test expectations on the _behavior_ of your architecture.
- Capacity testing can help close the loop; it can validate your modeling.
  - [jmeter](https://jmeter.apache.org) is a tool that can stress test your infrastructure.
- Using an “agile” infrastructure allows you to accommodate elastic demands. There are inelastic too. Don’t loose track of services that have continuous, predictable load.
- Case study: Stanford is looking at “multiplexing” their ingest pipeline. Designing systems that allow for flexible horizontal scaling is wise, but not necessarily simple.
- There is “technical debt” in infrastructure as well as applications. Often these shortcomings can be addressed using agile methods.
  - Just growing bigger isn’t always the solution _especially_ when you don’t know where your bottlenecks are. Just adding another VM won’t increase your networking capacity.
- Analysis paralyses is also common in infrastructure planning. Most of the time the 80% solution can work.
- Making changes to services in production is serious business. Don’t break production! Communicate to your audience! A _lightweight_ change management system can help with this.
  - What seems minor to a developer may not be perceived as minor to your audience.
  - You should also have a knowledge base with instructions for triage and a path of escalation for problems.
  - 90% of ensuring this is process and procedure
- Consider tagging production deploys; this helps smooth over some things. You can roll back changes to a know point!


### Service Level Agreements
- Service level commitments can be used to regulate the resources allocation.
- You should classify how critical all of your applications are. (This could take you a year.) This can be the baseline for your SLAs.
  - This can get complicated when there dependencies on ancillary systems.
  - One way to address this it to package all the software that supports a service together.
  - Completeness of the list of application isn't crucial; anything you miss will make itself known.
  - Part of adding a new service to production is to add it to this list.
  - You also need to track priority, stakeholders, and related resources for _every_ new service.
- Uptime requirements can be conveyed using similes e.g. deploying services is like staffing the reference desk.
  - When the library website is down it is like the library is closed.
  - When an application goes down it is like someone missed their shift at the reference desk.
- Not everyone understands that:
  - When something is in production it doesn’t mean that it is done forever.
  - Adding 9s to uptime incurs a geometric increase in cost.
  - Your “website” is actually composed of a lot of different services and some of them are not critical.


### Setting Priority
- Can we increase the value of the things we already own?
- Do people just have a giant Gantt chart in their heads? How do you convey the needs of the system.
- CMDB (Change Management Database) systems exist to help abate these problems. Unfortunately they are usually exorbitantly expensive and a pain to work with.
  - [itop](http://sourceforge.net/projects/itop/) is an OSS option
- One limit we _do_ have is funding.
	- Many times we know what the solution is but it isn’t tenable due to monitory constraints.
- Communicating your constraints to the rest of the organization is critical. For example, storage is _not_ limitless; there are real costs associated with tiers of capacity.
- Tooling, especially in the GIS world, in necessary to facilitate access to data. Therefore tooling development _also_ needs to be included in your planning.
- Risk assessment should be a component of task prioritization. Maybe archiving those 15-year-old CD-Rs should happen sooner rather than later.
- It is _really_ hard for us to say no to new initiatives. Perhaps we can track expectations back to something like a [balanced scorecard](http://en.wikipedia.org/wiki/Balanced_scorecard) approach to management.
- Libraries don’t track ROI the same way for-profit business do. We need other measures of value; unfortunately much of the perceived value of LAMs is vague e.g. opportunity costs of establishing academic libraries as a source of GIS data.
  - Part of the mission of a library is to preserve content; even if no one uses it.
- If sysadmins are doing their job well you don’t notice. It is hard to convey the value of the services you are providing.
  - How do you prioritize security updates _before_ your systems get compromised.


### Turning Things Off
Can you actually end of life things in a library context?  
- You can triage web content based on usage. Analytics can be a hammer of progress.
- The Hydra Way includes the idea of “durable data; lightweight applications”


### Repositories
- Many of our repository services are really a constellation of related, dependent applications. Defining the dependency graphs is critical to diagnosing problems in this environment.
- There are a lot of options for data storage and replication. For example you can have have a “backupless” archival system: write once, version changes, replicate across nodes. This can be sort of a “poor man's” [HSM](http://en.wikipedia.org/wiki/Hierarchical_storage_management).


## Action Items 
- What are the heuristics they you use to determine service level for applications?
- Can we see an example document that lists an institution’s application and its service level?
