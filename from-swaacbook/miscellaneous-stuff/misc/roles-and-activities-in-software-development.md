
# Table of Contents

1.  [Roles and Activities in Software Development](#roles-and-activities-in-software-development)
    1.  [Visionary &#x2013; Envisioning](#visionary-envisioning)
    2.  [Analyst &#x2013; Specification](#analyst-specification)
    3.  [Architect &#x2013; Structuring](#architect-structuring)
    4.  [Designer &#x2013; User Interface, User Experience, Presentation](#designer-user-interface-user-experience-presentation)
    5.  [Developer &#x2013; Creating](#developer-creating)
    6.  [Quality Assurance](#quality-assurance)
        1.  [Setting Quality Goals](#setting-quality-goals)
        2.  [Defining The Processes](#defining-the-processes)
        3.  [Building Tools To Implement Processes](#building-tools-to-implement-processes)
        4.  [Verifying And Validating](#verifying-and-validating)
    7.  [Deployment And Operations &#x2013; Delivering The Product](#deployment-and-operations-delivering-the-product)
    8.  [Maintainer &#x2013; Fixing, Repairing, Improving](#maintainer-fixing-repairing-improving)
    9.  [Manager &#x2013; Keeping Track Of Everything](#manager-keeping-track-of-everything)
    10. [Sales And Marketing &#x2013; Bringing People To The Product](#sales-and-marketing-bringing-people-to-the-product)
    11. [Support &#x2013; Helping People Install And Use The Product](#support-helping-people-install-and-use-the-product)
    12. [User &#x2013; Using The Product](#user-using-the-product)
    13. [Customer &#x2013; Buying The Product](#customer-buying-the-product)
    14. [Investor &#x2013; Funding The Product](#investor-funding-the-product)


<a id="roles-and-activities-in-software-development"></a>

# Roles and Activities in Software Development

-   categories: [swaac]
-   date: 2013-05-15 21:00

A short article on various roles and activities performed by those roles in the course of software development.

These are my particular take on the various roles and activities; the list is not truly definitive. The distinctions between many of these activities is often blurred.

These roles aren't really in any particular order than the order I thought of them in. There's a bit of flow from one to the other, but all roles should be involved at every step of the development.

The traditional Waterfall concept had things passing from one role/activity to the next as it was completed. The more effective Iterative concept has the activities going on in parallel, with high communications between each of the roles.

Even when one is doing solo work, one puts on various hats at different times, and does all these roles one's self.

As a crafts person, one should expect to be at least minimally competent in all of these roles.


<a id="visionary-envisioning"></a>

## Visionary &#x2013; Envisioning

The Visionary is the one with the Big Ideas &#x2013; the ones that drive the creation of the product or site in the first place.


<a id="analyst-specification"></a>

## Analyst &#x2013; Specification

The Analyst determines what the features and parameters of the product or site should be and converts them into specifications that can be developed, tested, and delivered.


<a id="architect-structuring"></a>

## Architect &#x2013; Structuring

The Architect creates the overall structure of the product or site, determining it's major components, interfaces, and implementation guidelines.


<a id="designer-user-interface-user-experience-presentation"></a>

## Designer &#x2013; User Interface, User Experience, Presentation

The Designer creates the external view of the product or site, how it will be presented to the users, how users will interact with it, what tasks the users will be able to accomplish using the site, and how to make the site attractive to user to keep them coming back and using it.


<a id="developer-creating"></a>

## Developer &#x2013; Creating

Take the specifications, the structure, the design, and put it into code, following guidelines set out for creating and ensuring a high-quality product or site.


<a id="quality-assurance"></a>

## Quality Assurance

Quality assurance has many aspects:


<a id="setting-quality-goals"></a>

### Setting Quality Goals

Features and presentation are not the only goals for a product or site. In addition, a high quality site will address:

-   Performance - how fast does the site respond to users, especially under load
-   Robustness - how does the site deal with internal and external errors and faults
-   Reliability - what measures are taken to ensure that faults, errors and defects do not creep in during development, deployment and maintenance, and during long-term running of the product or site
-   Usability - not just the purview of the Designer, goals for usability such as accessibility, timely response, clarity of action, ease of tasks
-   Testability - ensure that what gets developed can be easily and thoroughly tested
-   Internationalisation and Localisation - goals for making sure the product or site will be available in the user's preferred language and style
-   Supportability - goals to ensure the product or site can be maintained, that the product or site provides support and help for users, and that procedures and resources are defined to support customers and users on an ongoing basis.


<a id="defining-the-processes"></a>

### Defining The Processes

Processes for managing work products such as code, content, assets, inventory, infrastructure need to be defined and in some cases developed. Rules of the Road, i.e., how each of these pieces will be used by the team, need to be written and disseminated.

The best processes are light-weight, and make it easier to adhere to the process rather than find ways around it. The purpose is to make sure that people can work easily and well together, and that work products are protected from disaster. The processes agreed to do not need to be extensively documented, but collecting them as a sort of FAQ and curating project lore can be very useful for new people coming into the team, and for people to switch roles from time to time.


<a id="building-tools-to-implement-processes"></a>

### Building Tools To Implement Processes

"No Rules Without Tools" is the watchword here. Whatever processes one adopts, there need to be tools to implement it, or the team will be burdened with having to step through a process manually, which if it isn't something they do on a frequent basis, makes it prone to errors. Even if it is something they do on a frequent basis, tools make it easier to complete the process when the particular process may not be fundamental to their task.

Templates, re-usable snippets, little tools and scripts, push-button actions; these are the bread and butter of the tool builder. Making sure the tools are easily used and installed is imperative to getting people to use them. If the processes disappear into the background, then they are much more likely to be followed. Tools enable that to happen.


<a id="verifying-and-validating"></a>

### Verifying And Validating

The traditional purview of quality assurance has been testing &#x2013; making sure that what got implemented got implemented correctly, and that what got implemented was what was wanted.

This is still a necessary part of QA; as outlined above is not the only part of QA, but still must not be given short shrift.

This is an area where the QA engineer can model and demonstrate all the other aspects of their work, by building high quality, usable, performant, and accurate tests, test suites, and so on. Tests *are* code &#x2013; just not code you deliver.


<a id="deployment-and-operations-delivering-the-product"></a>

## Deployment And Operations &#x2013; Delivering The Product

Getting the product out the door; getting the site deployed to the production environment; constructing the production and upstream environments; testing the tools and procedures to move from development to production; recover from disasters; monitoring operations; &#x2013; these are all the area of the Dev-Ops role.


<a id="maintainer-fixing-repairing-improving"></a>

## Maintainer &#x2013; Fixing, Repairing, Improving

When a defect shows up in the product or site, someone has to fix it. But maintenance is not just a responsive or reactive role. As code moves along, it acquires rot and mold, and such things need to be cleaned out to ensure that the product or site enjoys a long life. Until code actually meets users (or their agents), it will be hypothetical as to how good the implementation is. The methods, structures, implementation choices; all will be open and subject to the evaluation under fire. Maintainers have the opportunity to refactor, restructure and retest the code under such conditions.


<a id="manager-keeping-track-of-everything"></a>

## Manager &#x2013; Keeping Track Of Everything

Someone has to keep track of all the moving parts and people. When do things get built, in what order, and by whom? How much budget, in money, time, and resources, will something take? How best to allocate scarce project resources? How do I acquire and retain the talent needed to implement the product or site?


<a id="sales-and-marketing-bringing-people-to-the-product"></a>

## Sales And Marketing &#x2013; Bringing People To The Product

While there is the myth of "Build it and they will come", this concept is not all that useful for a product or site that is intended to provide a return on investment for people, employ people, and basically provide a viable commercial enterprise. So someone has to be able to find people who will want to use the product or site, and tell them about it in a way that brings in interested people.

How you're going to convince people to come, and keep coming back, is not something that can be left to the end; sales and marketing considerations need to be included up front and continuously through the development steps. Marketability is something else that a product or site needs to be able to implement well.

Marketing needs to be responsive; in the case of a new product or site, it is often quite unknown how potential customers and users will respond to it, and to whatever things are done to attract them. As such, the product or site also needs to be responsive to such changes. The ability to quickly add incentives, change or add rewards, highlight key areas of the site or features of the product, etc., make a product or site more marketable.


<a id="support-helping-people-install-and-use-the-product"></a>

## Support &#x2013; Helping People Install And Use The Product

No product or site can meet the expectations and needs of every customer or user; often times people need help understanding how to use what we create. As we're not mind-readers, we can't know what sorts of issues someone will have ahead of time (if we could do that, we could create a product that would have already addressed those concerns).

Support is a key aspect to customer and user satisfaction, and is how one can turn a problem into a strength in order to retain users and drive overall opinion of the product, site and team.

Support needs to define and staff the venues and avenues by which users, customers, and implementers can easily get answers to their questions, help with problems and understanding the product or site.


<a id="user-using-the-product"></a>

## User &#x2013; Using The Product

The user is the most precious and key resource a product or site will have. If no one will be using the product or site, there was little point in building it (unless your goal at the outset was only to learn something, but then you learn most when you see people using what you create). Users are also the most difficult to get information from at the outset in order to steer the development of the product or site. Concepts such as user-centered design are quite helpful, but no one can really predict what new sorts of things users will find to use the product or site for. Cultivating user communities and involvement is necessary for ongoing improvements and changes and to ensure people keep coming back.


<a id="customer-buying-the-product"></a>

## Customer &#x2013; Buying The Product

Like the user, and often times the customer is the user, customers must be involved early, and continue to be involved throughout. If your product or site is to be a commercial vehicle, you want to ensure that people will *want* to pay for using it.


<a id="investor-funding-the-product"></a>

## Investor &#x2013; Funding The Product

Investors are the folks who put up the seed capital to get projects off the ground until they can start to show a return on investment. While generally investors don't interact with developers, developers should understand investors' needs, and keep focus on getting the product or site under development to a viable economic standpoint as early as possible.

What this means in practice is consistent with much of the previous discussion; it's not just put your head down and start writing code to get something out the door as fast as possible; it's involving all the various stakeholders above to step with agility together in the dance of crafting software.

