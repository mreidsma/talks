Slide 1

Many library folks have a go-to search they use to try out different search tools. By using the same terms in many tools over a period of time, you can get a good sense of how a search tool's algorithms perform in comparison to other tools you've tried. I use "batman," because search results will be a mix of popular and scholarly sources, a variety of formats, and items from the 16th and 17th centuries. I've know others who use "ethical tourism" and "space law." This itself is a crude but simple way to evaluate algorithms, ruled more by gut and memory than analysis. 

-----

Slide 2

In 2015 my colleague Jeffrey Daniels showed me the Summon search results for his go-to search: "Stress in the workplace." Jeff likes this search because 'stress' is a common engineering term as well as one common to psychology and the social sciences. The search demonstrates how well a system handles word proximities, and in this regard, Summon did well. There are no apparent results for evaluating bridge design. But Summon's Topic Explorer, the right-hand sidebar that provides contextual information about the topic you are searching for, had an issue. It suggested that Jeff's search for "stress in the workplace" was really a search about women in the workforce. Implying that stress at work was caused, perhaps, by women.

-----

Slide 3

I started looking closer at the Topic Explorer, eventually combing through 8,000 searches that returned a Topic Explorer result and found a number of other problems, mostly in searches related to women, LGBTQ folks, African Americans, Muslims, and the mentally ill. I shared my results with the Summon team, and they "blocked" many of the problematic results, although not this one, or any search related to mental illness, which still suggests it is a "myth." 

-----

Slide 4

It's important to note that they did not adjust the Topic Explorer algorithm. Instead, they hid the "problematic" results. In my conversations with ProQuest, I came to realize that they saw this as a technical problem, not a social or moral one. 

It reminded me of Paul Goodman's quip in the late 1960s about how technology as primarily an ethical undertaking. Goodman's point was that all our decisions about how people live and work and act in the world are fundamentally moral issues. But the growing body of research on critical algorithmic studies confirms that most if not all companies that produce algorithmic systems see them (or at least publicly claim to see them) as neutral, objective technical achievements. The footer of Google News, for instance, reminds users that the stories were "selected by an algorithm," and not by people, as if that absolves the company of any editorial issues.

-----

Slide 5

Now, you may remember some of our esteemed colleagues in this very room have pushed back against that idea. When I began researching library discovery algorithms, I wanted to understand more about how they were created, how they worked, and how they affected users in the world. I began by reading a lot of other critical studies of algorithms, which mostly focus on public, commercial systems that use algorithms: Google, Facebook, Twitter, policing and legal software. While a lot of academics focus on algorithms outside the academy, I was interested in the algorithms in higher ed that condition the learning environment of our users.

-----

Slide 6

Rob Kitchin's basic definition of an algorithm is "sets of defined steps structured to process instructions/data to produce an output" (Kitchin, 2017, p.14). So, to begin to audit an algorithm, we might want to know the steps the algorithms walks through, either in code or in pseudo-code. But here's the catch: all of the commercial discovery tools consider their search algorithms to be major intellectual property assets. They won't reveal the code or even pseudo-code to us.

Of course, algorithms are hardly straightforward and linear, and it's unlikely we would be able to make heads or tails out of the code if we had access to it. And the steps built out of code are only part of the story: the index has to be considered, too. What the algorithm looks for only makes sense if you understand what it looks at. We don't even know the exact parameters of what is in the discovery service's index (although there is more clarity here, since the index is what shows up as visible outputs.)

-----

Slide 7

So, we look for hints, or proxies for the algorithm. I started by looking through Summon's administrative settings. Any setting that allowed me to change how results appear or are ranked gave a hint to something the algorithm values. The Summon documentation was also helpful. Articles explained what fields were searched, how records were de-duplicated, and how to conduct advanced search techniques such as keyword weighting and proximity searching techniques, which helped me better understand how the algorithm and the index work together. I also read through mailing list posts from the project managers, specifically around changes to or the functioning of the algorithm, and read the release announcements carefully. 

-----

Slide 8

But looking at code or understanding the boundaries of the index will only get you so far, and risks fetishizing the algorithm. Algorithms exist to do something, to create outputs from inputs. We need to see them work.

Once we have some crude ideas of what the algorithm looks for, we can start testing to see how different inputs create outputs. While the inner workings are still hidden, we can see what kinds of outputs we get by changing inputs.

-----

Slide 9

This is a simplified version of the jQuery function I used to capture search queries and Topic Explorer results. Whenever Summon executed a search and a Topic Explorer result was shown, the script would grab the search query and the heading, source, and text of the Topic Explorer result and send a POST request to a PHP script that parsed the data and stored it in a MySQL database. This method works for looking at the results of what other people are searching for, but you need to be cautious about privacy. In this case, searches that bring up Topic Explorer results are very general searches, often 1-2 terms. By not saving any information about who did the search, what other searches they did, or when the search was run, I lowered the possibility of capturing reidentifiable data about our users. 

You could easily convert this to a bookmarklet to run on a page where you define a search, or create a bot or spider to scrape the page and store the results from all manner of algorithms: search results, database recommendations, spelling corrections, query expansions, autosuggestions, related topics, related searches, and more. (There are some legal concerns we'll get to in a moment with these approaches.)

-----

Slide 10

Finding problematic results often helps expose the inner workings of the algorithm. Like this known item search for a book on LGBT youth that returns only 2 items: the book and a guide to "mental illness." The second item in the results list is an eBook, which can help us understand how those different factors are weighted, or how the algorithm decides to select specific results. We can then test those hypotheses over and over, refining the results. 

But these problematic results often expose the inner workings of the algorithm more clearly.

-----

Slide 11

I matched 8,000 search queries with their respective topic explorer results, and released them as a data set, if you want to look them over or use them in your research. The data set includes very general search terms and the respective Topic Explorer result for each.



-----

Slide 12

But algorithms aren't just code and inputs and outputs. They are used by people in order to do something else. We need to study those effects, too, and this is where my research is taking me.

-----

Slide 13

They affect the world, showing and hiding possibilities from researchers, suggesting to new researchers what a broad search might really be about. In addition to our work at understanding what an algorithm looks at, and what kinds of results it returns, we need to ask how it affects the users who interact with the algorithm and its results. This is where ethnography and user research can come in. We need to be talking to users, and running ethnographic experiments to better understand the impact that algorithmic outputs - both good and bad - have on learning and research.

-----

Slide 14

There are challenging, scary, ethical issues at work here. Library search tools are positioned as neutral, objective places for learning and research. That is not the case, part of the reason for auditing our algorithmic tools is to both help push against this kind of "objective" marketing, and also to work with vendors to improve the algorithms.

-----

Slide 15

A word on the responsibilities of vendors. If your search tool reinforces and reproduces systemic racial, gender, religious, or other biases - it doesn't matter if you "didn't intend" to build a system with those biases. That's what you system does. It is your responsibility to make a system that is fair for all users. Your responsibility doesn't end when we go live with your tool.

-----

Slide 15.5

But these search results are often the most visible and used parts of our online library presence, and so they speak to our users about our values. Yesterday I saw this slide from my fellow Weave Journal of Library User Experience editor Angela Galvan from her keynote at VALA in TK. These problematic results tell our users what we value. It is our responsibility to ensure that the values we claim to have are what are reflected. Our responsibility doesn't end when we sign a license agreement. 

-----

Slide 16

Algorithms in Library discovery are not affected by some of the most challenging parts of researching search algorithms. For one, the pressures of capital and wealth creation are not as direct as in an advertising and surveillance supported search tool like Google. There are (theoretically) no ads in our discovery services, although that doesn't mean there isn't surveillance. And since the discovery services are just one ganglia of larger commercial academic publishing corporations, there are incentives to get users to look at results from a databases, but overall, there is less emphasis on things other than search results to examine.

-----

Slide 17

Because libraries are licensing this software, we expect that the vendor won't experiment with new features in our live discovery systems. And as of this moment, none of the vendors appears to be using machine learning algorithms to personalize search results for our users. (It will get there, but some of them are using tables for layout, so I think we're safe for a bit.) We can be pretty sure that all of our users are seeing the same results for the same searches (except for some differences in on-campus and off-campus searches.)

-----

Slide 18

Finally, the content these search tools have indexed isn't written to be searched in a search engine like web content. Much of it is written without worrying whether anyone will or can read and make sense of it, let alone a search engine. So when a result appears in a search, we can be reasonably sure it is there because of the algorithms choice, and not manipulation on the part of an Assistant Professor of Botany somewhere.

-----

Slide 19

On the other hand, discovery systems have challenges that are not as common in other algorithmic systems, or unique to library discovery. The most obvious is that search results from my discovery instance won't be the same for yours, because of the different collection policies of our institutions. This might not affect the ancillary algorithms that are sprinkled around the main search results, like Topic Explorer or related searches, but it definitely affects the results from your collection.

-----

Slide 20

Trying to understand why something appears in a results set can be challenging, because items in a discovery service's index often blend all the varied metadata practices of hundreds or different database providers into one big, messy soup. Of course, they often have a more structured taxonomy, as well, but results may appear because one of your keywords matched a thesaurus entry for a subject term in an obscure database. This can complicate  understanding how algorithms choose results.

-----

Slide 21

If you want to study a tool that isn't the one your institution subscribes to, you may be thwarted by the End User License Agreement for the discovery service. Both (EDS) EBSCO discovery service and OCLC's Worldshare prohibit the search interface from being used by "unauthorized users," which is basically everyone but currently affiliated students, staff, "registered users" and faculty at the subscribing institution. 

Even if you could use the interfaces, none of us has the time to manually search and record results, so we'd naturally write a script to do this for us. But the EULA may prohibit this, as well. (The Computer Fraud and Abuse Act is also so broad that even if the EULA didn't prohibit this, you might be in legal trouble from scraping results anyway.) If you subscribe to a service, you may be able to collect the results with a script in the guise of collecting usage data. That's what I did with Summon.

(A quick point of order: I am not a lawyer and this is not legal advice.)


-----

Slide 22

So, this is my pitch: help me better understand our library discovery algorithms. Either dive in yourself, and examine the algorithms, inputs and outputs, and talk to users, and publish what you learn. Or, if you're an authorized user, or representative from of EDS or OCLC's Worldshare, I'd love to talk with you. The license agreements say I can't use the tools, but they never said anything about me asking an authorized user to collect search results. 

You'll also notice that I'm only mentioning that two of the discovery services have End User License agreements. I'll let you draw your own conclusions from that information.

-----

