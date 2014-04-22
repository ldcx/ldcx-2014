# Are we doing a good job sharing?
- Can we discuss more things on the committers call?
- Is the documentation sufficient? How would we enrich it?
- @jeremyf would like to speak about the specifics of crafting reusable components
  - @jeremyf says that callback-dependent code is hard to test; it needs to express intent
  - @jeremyf would like to compose objects with fewer public methods
- @dchandekstark has concerns about the reusability UI-centric content e.g. incompatible versions of Twitter Bootstrap between components
- How can we make Hydra Derivatives better?
- The [Hierarchy of Promises](https://wiki.duraspace.org/display/hydra/Hydra+Stack+-+The+Hierarchy+of+Promises) should explain the “why” for _all_ of the gems in the Hydra ecosystem
  - How do we accommodate things that have overlapping concerns e.g. [Curate](https://github.com/projecthydra/curate) & [Sufia](https://github.com/projecthydra/sufia)?
- Would a top-level document about “extending” be useful in our gems? Survey says yes.
- There are only a few people that know the core code well enough to make contributions to it. This raises the barrier of entry.
  - A lot of time people either don't have the time or don’t want to deal with the overhead of contributing to the core (community “arguing” time isn’t accounted for by PMs).
  - On the other hand @jcoyne frequently doesn’t get feedback when he proposes changes to Hydra components. Why is that? Do people just trust him? Do people not care? Are the concepts involved to esoteric?
- Can we get behavior-driven acceptance tests in Hydra components? That way there can be conversations about changes to core features or behavior.
  - We might be able to accomplish this by tagging tests.
  - How is this different from our current integration tests? Some of these tests probably need to be cleaned out.
  - This should help fill the gap between test-passing and making sure things “actually work”.
- We need some “standards” for our gems
  - Having a template for a README would be a good start.
  - A hydra-gem generator might help too.
- We should focus on the experience of “shopping at the Hydra Store”.
  - What is done enough to use?
  - What is the sustainability of the project?
  - Who is using this stuff?
- The path to sustainability for the Hydra Project is to embed our work in what people are actively doing.
- @flyingzumwalt: “One of the biggest benefits of Open Source is that you can fail fast.”
- Should we have a incubator for projects that aren’t quite ready for prime time. The Apache project does this. For this to work you need a “bar” that potential projects need to meet.
  - A gem guidelines document would be a good start. It could be refreshed at meetings like LDCX
  - Integrating this into the commuters call workflow is one way to ensure that time will be dedicated to this process. Maybe a partner’s meeting would be better.
- The burden of writing acceptance tests doesn’t have to be the burden of the maintainers. Tests can also be submitted by implementers.

Deliverables:  
- Let’s take a pass at [Questioning Authority](https://github.com/projecthydra/questioning_authority) on Thursday. @jeremyf will head this up.
  - Describe the behavior the thing provides
  - Identify the scope of the gem
- We should propose a “Hydra Labs” github organization to the Hydra Partners via the mailing list. @dchandekstark will do this.
- Get permission to publish documentation on how to extend Blacklight. @flyingzumwalt has already done this.
- @jeremyf will propose a hacking topic on Thursday.

