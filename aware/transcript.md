### Title slide:

Hello! Thanks for inviting me to kick off your Algorithmic Awareness Board meeting.

-----

### Slide 1:

Many library folks have a go-to search they use to try out different search tools. By using the same terms in many tools over a period of time, you can get a good sense of how a search tool's algorithms perform in comparison to other tools you've tried. I use "batman," because it's short, and the search results will be a mix of popular and scholarly sources, a variety of formats, and items from the 16th and 17th centuries. This itself is a crude but simple way to evaluate algorithms, but it id ruled more by gut and memory than analysis.  

-----

### Slide 2:

In 2015 my colleague Jeffrey Daniels showed me the Summon search results for his go-to search: "Stress in the workplace." Jeff likes this search because 'stress' is a common engineering term as well as one common to psychology and the social sciences. The search demonstrates how well a system handles word proximities, and in this regard, Summon did well. There are no apparent results for evaluating bridge design. But Summon's Topic Explorer, the right-hand sidebar that provides contextual information about the topic you are searching for, had an issue. It suggested that Jeff's search for "stress in the workplace" was really a search about women in the workforce. Implying that stress at work was caused, perhaps, by women.

-----

### Slide 3:

I shared it with the Summon team, and within a day they blocked the result.

-----

### Slide 4:

I started looking closer at the Topic Explorer, eventually combing through 8,000 searches that returned a Topic Explorer result and found a number of other problems, mostly in searches related to women, the LGBTQ community, African Americans, Muslims, and mental illness. I shared my results with the Summon team, and they "blocked" many of the problematic results, although not this one, or any search related to mental illness, which still suggests it is a "myth."

-----

### Slide 5:

It's important to note that they did not adjust the Topic Explorer algorithm. Instead, they hid  "problematic" results. In my conversations, I came to realize that they saw this as a technical problem, not a social or moral one. 

It reminded me of Paul Goodman's quip in the late 1960s about how technology is primarily an ethical undertaking. Goodman's point was that all our decisions about how people live and work and act in the world are fundamentally moral issues. But the growing body of research on critical algorithmic studies confirms that most if not all companies that produce algorithmic systems see them (or at least publicly claim to see them) as neutral, objective technical achievements. The footer of Google News, for instance, reminds us that the stories were "selected by an algorithm," and not by people, as if that absolves the company of any editorial issues.

If we see biased results as a technical problem, an acceptable solution may be to hide the offending results. But solutions that make sense for technical issues will often be different from solutions that make sense for ethical issues. 

-----

### Slide 6:

Lots of other librarians have pushed back against the idea that these systems are objective, neutral, and exclusively technical. When I began researching library discovery algorithms, I began by reading a lot of critical studies of algorithms, which mostly focus on public, commercial systems that use algorithms: Google, Facebook, Twitter, policing and legal software. Very important work is bring done by an incredible community of journalists and scholars like Julia Angwin at Propublica, Zeynep Tufekci at the University of North Carolina, and Safiya Noble at the Annenberg School of Communication. And, of course, by Jason and the rest of you sitting in that room in Bozeman.

While a lot of academics focus on algorithms outside the academy, I was interested in the algorithms within Higher Ed that condition the learning environment.

-----

### Slide 7:

A basic definition of an algorithm is a set of steps used to process an input to produce an output (cf. Kitchin, 2017, p.14). So, to begin to audit an algorithm, I wanted to know the steps the algorithm walks through, either in code or in pseudo-code. What decisions are being made? But here's the catch: all of the commercial library discovery tools consider their search algorithms to be major intellectual property assets. They won't reveal the code or even pseudo-code.

Of course, algorithms are hardly straightforward and linear, and it's unlikely I would be able to make heads or tails out of the code if I had access to it. And the steps built out of code are only part of the story: the index has to be considered, too. What the algorithm looks for only makes sense if you understand what it looks at. We don't even know the exact parameters of what is in the discovery service's index (although there is more clarity here, since the index is what shows up as visible outputs.)

-----

### Slide 8:

So, I looked for hints, or proxies for the algorithm. I started by looking through Summon's administrative settings. Any setting that allowed me to change how results appear or are ranked gave a hint to something the algorithm values. The Summon documentation was also helpful. Articles explained what fields were searched, how records were de-duplicated, how the algorithm determines "relevance" (in very general terms), and how to conduct advanced search techniques such as keyword weighting and proximity searches. Taken together, these helped me better understand how the algorithm and the index work together. I also read through mailing list posts from the project managers, specifically around changes to or the functioning of the algorithm, and read the release announcements carefully. 

-----

### Slide 9:

But looking at code or understanding the boundaries of the index will only get you so far, and risks fetishizing the algorithm. Algorithms exist to do something, to create outputs from inputs. We need to see them work.

So, while the inner workings are still hidden, we can see what kinds of outputs we get by changing inputs.

But typing in searches one at a time doesn't scale. 

-----

### Slide 10:

So I captured the results as our users searched in Summon. This has the benefit of showing actual searches rather than hypothetical searches.

Whenever Summon executes a search for a user and a Topic Explorer result was shown, my script grab the search query and all of the algorithmic results on the page and sends a POST request to a PHP script that parses the data and stored it in a MySQL database. This method works for looking at the results of what other people are searching for, but you need to be cautious about privacy. In this case, searches that bring up Topic Explorer results are very general searches, often 1-2 terms. By not saving any information about who did the search, what other searches they did, or when the search was run, I lowered the possibility of capturing reidentifiable data about our users. 

I then built a dashboard, shown here, that allows me to review the results of these searches.

-----

### Slide 11:

In 2016 I matched 8,000 search queries with their respective topic explorer results, and released them as a data set, if you want to look them over or use them in your research. The data set includes very general search terms and the respective Topic Explorer result for each.

8,000 results is a lot of results when you are reviewing them one at a time by yourself. But to understand the workings of a complex algorithm? It's not nearly enough. But it's a start.

-----

### Slide 12:

I shared my data set with the Summon team in advance of publishing my results, which looked at the set of 8,000 results and found that the Topic Explorer algorithm was able to at least generally identify a topic about 90% of the time. And that's being very generous with the conceot of accuracy.

-----

### Slide 13:

About 1% of the results were biased. The remaining 9% were 
incorrect, but maybe not all wrong, like this search that equated the ubiquitous marketing concept of "branding" with Bondage, Discipline, Sadism, and Masochism.

-----

### Slide 14:

But often the incorrect results slipped into bias, reinforcing negative stereotypes, like a search for "women in film" that apparently couldn't imagine anything more relevant than an exploitation genre.

-----

### Slide 15:

Or the tendency of the algorithm to latch on to phrasings like a Mad Libs search engine, like this search for the Sarah Gwyneth Ross' book *Birth of Feminism* that returned the *Birth of Tragedy* instead. This is what was behind the "women in the workforce" result my colleague Jeff showed me. You could also search for "heroes in the workforce" and get "women in the workforce."

-----

### Slide 16:

If you want to examine an algorithm thoroughly, nothing beats collecting a lot of sample results, but there are other places to look for problems. I wish I knew who the mastermind behind this site was, but Damn You, Auto Suggest is a Tumblr with the subtitle of "Primo Knows Best. Auto-suggest failures from library catalogs and databases." You can even submit your own.

Here Primo suggests that a search for "New York Waste" should have been a search for "New York Women."

-----

### Slide 17:

I've also been able to find problematic results from colleagues, like this Primo result that Nadaleen Tempelman-Kluit posted on Twitter, where Primo thinks a search for Children's Literature could only be made better by transforming it into a search for Children's Sex Literature.

-----

### Slide 18:

EDS' autosuggest feature is particularly suceptible to searches where you type a category of person followed by "are" - such as here where EDS suggests that popular terms are "women are more emotional than men" and "women are weaker than men." 

While the algorithm was clearly designed to show "popular" searches, users often interpret these suggestions as "good" searches, ones that are sanctioned by the search tool, not just a reflection of the worst of humanity equipped with a million keyboards.

-----

### Slide 19:

EDS has a similar feature to Summon's Topic Explorer called Research Starters. The algorithm here makes heavy use of EBSCO's reference platforms and the underlying thesauri, and so we'd hope that there would be fewer issues than we see in the Topic Explorer. But a simple search for the term "racism" brings an article on "scientific racism."

-----

### Slide 20:

There are other Research Starters on the topic of race. Making the search more specific, by targeting America, brings a more appropriate Research Starter, and but also one that would be too narrow for the general search.

-----

### Slide 21:

Here, searching for "race discrimination," a combination of keywords exactly no one will search for when the shorter racism will do, brings up yet another potentially relevant result. But how many users will find this research starter? And what is behind the algorithm that chooses between these?

One difference I've found between the teams at EBSCO and the teams at Ex Libris/ProQuest is that the EBSCO team has been proactively testing their algorithms for bias, and correcting things. They reached out to me and gave me access to their tool and asked me to report any issues that I found. And they fix the algorithms - they ask the hard questions about what assumptions they built into the the tool that brought up problematic results, rather than just blocking offensive results. They're working on improving these search results right now.

### Slide 22:

Sometimes issues show up in other ways, as Ruth Tillman from Penn State pointed out to me recently. Here is a screenshot I took on Monday of the Summon Topic Explorer result for the search "Barack Obama." If you look at the Topic Explorer result, it says that Barack Obama is the "44th and current President of the United States." It's been 568 days since he left office, and this reported is showing the Wikipedia entry, which was edited to reflect Donald Trump's inauguration about a millisecond after the inauguration happened.

-----

### Slide 23:

Michelle Obama is still the first lady, according to Wikipedia as reported by Summon.

-----

### Slide 24:

And Donald Trump, according to Credo Reference, has no political career. He's a real estate mogul.

The bias here isn't necessarily against reflected against any particular group or individual -- it's a form of technical bias. The Summon team decided that the index they were building was better than Wikipedia's API, so they ingested Wikipedia entries into the Summon index. I'm sure they intended to update it regularly, but they didn't.

-----

### Slide 25:

I poked around a lot and found out when the injested the content into the index: sometime before February 20, 2013. That's when someone edited the first line of the cartoonist Chris Ware's entry to reflect the success of his graphic novel in a box, *Building Stories*.


-----

### Slide 26:

In the Topic Explorer, that phrase is missing. Summon 2.0 wasn't even announced to the public until a month later, March 18, 2013. So for five years, Wikipedia entries have remained frozen with early 2013 knowledge in Summon.

This innaccuracy was a direct result of a decision made when developing the search and relevance algorithm for the Topic Explorer. Rather than handing off the selection process to Wikipedia's API, the Summon team built their own, but did not think of the consequences of fixing a set of reference materials that prides itself on being up-to-date.

-----

### Slide 27:

Algorithms aren't just code and inputs and outputs. They are used by people in order to do something else. What are the affects of a user with white supremicist leanings seeing that EDS result for "scientific racism," or a user who sees our library tools claiming that Barack Obama is still president? We need to study those effects, too. Here, we must move beyond seeing these as technical issues, and accept the ethical responsibilities of building and choosing search tools.

-----

### Slide 28:

Algorithms show and hide possibilities from users, suggesting what a search might really be about. In addition to asking what an algorithm looks at, and what kinds of results it returns, we need to ask how it affects the users who interact with the algorithm and its results. This is where ethnography and user research can come in. I will be talking to users, and running ethnographic experiments over the next year to better understand the impact that algorithmic outputs - both good and bad - have on learning and research.

-----

### Slide 29:

Here is a result that was shared with me by one of our users. It's a known item search for a book on the information needs of LGBT youth that returns only 2 items: the book and a guide to "mental illness." 

As a researcher, results like these are often the ones that expose the inner workings of the algorithm more clearly. I can look at the metadata for that guide to mental illness and try to reverse engineer how it got there. They are like glitches in the Matrix.

But for the user who was searching for this book? What was the impact of seeing these books next to each other? Looking at inputs and outputs alone won't tell us how these results affect our users. Merely returning some relevant results isn't good enough. What we show (and don't show) matters.

-----

### Slide 30:

These are challenging, scary, ethical issues. But library search tools are sold as neutral, objective places for learning and research. That is not the case, and part of the reason for teaching algorithmic awareness is to cut through this kind of "objective" marketing.

-----

### Slide 31:

A word on the responsibilities of vendors and libraries who purchase software from them. If your search tool reinforces and reproduces systemic racial, gender, religious, or other biases - it doesn't matter if you "didn't intend" to build or license a system with those biases. That's what your system does. It is your responsibility to make and choose a system that is fair for all users. 

-----

### Slide 32:

But these search results are also the most visible and used parts of our library websites, and so they speak to our users about our values. In February, my colleague Angela Galvan gave the keynote at VALA in Melbourne. She noted "Glitches are the unintentional exposure of values." For those of us who study algorithms, problematic results give us a clearer window into what an algorithm values. But our users will read that as what we in the library value. It is our responsibility to ensure that the values we claim to have are what are reflected in our tools. Our responsibility doesn't end when we sign the license agreement.

-----

### Slide 33:

Helping our users understand library algorithms is important, and we must keep in mind that these algorithms are not affected by some of the most challenging parts of researching commercial search algorithms. 

For one, the pressures of capital and wealth creation are not as direct as in an advertising-supported search tool like Google. There are (theoretically) no ads in our discovery services. Libraries are the paying customer, not the end user.

-----

### Slide 34:

Because libraries are licensing this software, we expect that the vendor won't experiment with new features in our live discovery systems. And as of this moment, none of the vendors appears to be using machine learning algorithms to personalize search results for our users. (It will get there, but some of them are using tables for layout, so I think we're safe for a bit.) We can be pretty sure that all our users are seeing the same results for the same searches (except for some differences in on-campus and off-campus searches.)

General-purpose search tools like Google are a whole other story.

-----

### Slide 35:

And the content these search tools index isn't written to be searched in a search engine like web content. Much of it is written without worrying whether anyone will or can read and make sense of it, let alone a search engine. So when a result appears in a search, we can be reasonably sure it is there because of the algorithm, not manipulation on the part of an Assistant Professor of Botany.

-----

### Slide 36:

On the other hand, discovery systems have challenges that are not as common in other algorithmic systems. 

The most obvious is that search results from my discovery instance won't be the same for yours, because of the different collection practices of our institutions. This might not affect the "supporting" algorithms that are sprinkled around the main search results, like Topic Explorer or related searches, but it definitely affects the results from your collection.

-----

### Slide 37:

Trying to understand why something appears in a results set can be challenging, because items in a discovery service's index often blend all the varied metadata practices of hundreds or different database providers into one big, messy soup. Of course, they often have a more structured taxonomy, as well, but results may appear because one of your keywords matched a thesaurus entry for a subject term in an obscure database. This metadata opaqueness can complicate our understanding of how algorithms choose results.

-----

### Slide 38:

Finally, if you want to study a tool that isn't the one your institution subscribes to, you may be thwarted by the End User License Agreement for the discovery service. Both (EDS) EBSCO discovery service and OCLC's Worldshare prohibit the search interface from being used by "unauthorized users," which is basically everyone but currently affiliated students, staff, faculty, or patrons at the subscribing institution. 

Even if you could use the interfaces, none of us has the time to manually search and record results, so we'd ideally write a script to do this for us. But the license agreement may prohibit this, as well. (The Computer Fraud and Abuse Act is also so broad that even if the EULA didn't prohibit this, you might be in legal trouble from scraping results anyway.) If you subscribe to a service, you may be able to collect the results with a script in the guise of collecting usage data. That's what I did with Summon. And I got lucky when EBSCO reached out to me earlier this year and gave me access to EDS.

(A quick point of order: I am not a lawyer and this was not legal advice.)

-----

### Slide 39:

Teaching how to be aware of an algorithm's effects doesn't need to be as detailed and involved as what I have presented here. In fact, because of the vast difference between search tools large and small, it is impractical for most researchers to do this kind of analysis, let alone casual searchers.

But developing a healthy skepticism abut the claims these tools make is essential for the next generation of citizens. The tools you will help develop over the next few days will help get us there.

-----

### Slide 40:

Thank you for listening.
