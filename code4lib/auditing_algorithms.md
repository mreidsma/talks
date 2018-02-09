
# <span class="raleway" style="font-size:1.3em;letter-spacing:.08em;margin-left:.15em;">Auditing</span> <span class="blue" style="font-size: 1em; line-height:.7em;">Algorithms</span>

<p style="text-transform:uppercase;">Matthew Reidsma // <span class="blue">Grand Valley State University</span></p>

-----

![Screenshot of Summon search showing search results for Batman](img/batman.png)

Summon search results for "Batman" at Grand Valley State University

Note: 
Many library folks have a go-to search they use to try out different search tools. By using the same terms in many tools over a period of time, you can get a good sense of how a search tool's algorithms perform in comparison to other tools you've tried. I use "batman," because you will get a mix of popular and scholarly sources, a variety of formats, and items from the 16th and 17th centuries. I've know others who use "ethical tourism" and "space law." This itself is a crude but simple way to evaluate algorithms, ruled more by gut and memory than analysis. 

-----

![Summon results equating stress in the workplace with women](img/stressworkforce.png)

Summon search results for "Stress in the workplace" at Grand Valley State University, Fall 2015

Note:
In 2015 my colleague Jeffrey Daniels showed me the Summon search results for his go-to search: "Stress in the workplace." Jeff likes this search because 'stress' is a common engineering term as well as one common to psychology and the social sciences. The search demonstrates how well a system handles word proximities, and in this regard, Summon did well. There are no apparent results for evaluating bridge design. But Summon's Topic Explorer, the right-hand sidebar that provides contextual information about the topic you are searching for, had an issue. It suggested that Jeff's search for "stress in the workplace" was really a search about women in the workforce. Implying that stress at work was caused, perhaps, by women.


-----

![Summon results equating mental illness with a myth](img/mentalillness.png)

Summon search results for "mental illness" at Grand Valley State University, February 2018, 3 years after the issue was reported

Note: 
I started looking closer at the Topic Explorer, eventually combing through 8,000 searches that returned a Topic Explorer result and found a number of other problems, mostly in searches related to women, LGBTQ folks, African Americans, muslims, and the mentall ill. I shared my results with ProQuest, and they "blocked" many of the problematic results, although not this one, or any search related to mental illness, which still suggests it is a "myth." 

-----

<!-- .slide: data-background-image="img/goodman.jpg" -->

### Technology is a branch of moral philosophy, not of science.

#### Paul Goodman

[Goodman, P. (1969). Can Technology Be Humane? *New York Review of Books*, Nov. 20, 1969](http://www.nybooks.com/articles/1969/11/20/can-technology-be-humane)

Note:
It's important to note that they did nothing, to my knowledge, to the Topic Explorer algorithm. They simply hid the "problematic" results. In my conversations with ProQuest, I came to realize that they saw this as a purely technical problem, not a social or moral one. It reminded me of Paul Goodman's quip in the late 1960s about the technology's place in the academy. The growing body of research on critical algorithmic studies confirms that most if not all companies that produce algorithmic systems see them (or at least publicly claim to see them) as neutral, objective technical achievements.


-----

<!-- .slide: data-background-image="img/orphanides.jpg" -->

### System design reflects the designer's values and the cultural context.

#### Andreas Orphanides

[Architecture is politics: The power and the perils of systems design](https://docs.google.com/presentation/d/180dMBG26xMYB9gfIotoUyCBQfO3XfmHiJGQjvn58GwY/edit?pref=2&pli=1#slide=id.gf03c9bb35_0_143)

Note:
But you may remember some of our esteemed colleagues in this very room pushing back against that idea. So I decided I needed to understand more about how these algorithms were created, how they worked, and how they affected users in the world. I began by reading a lot of other critical studies of algorithms, which mostly focus on public, commercial systems that use algorithms: Google, Facebook, Twitter, policing and legal software. While a lot of academics focus on algorithms outside the academy, I was interested in the algorithms in higher ed that condition the learning environment.


-----

<h1><span class="blue">The</span> Algorithm</h1>

cf. Kitchin, R. (2017). Thinking critically about and researching algorithms. *Information, Communication & Society, 20*(1), 14-29, DOI: 10.1080/1369118X.2016.1154087

Note:
The common definition of an algorithm is that it is "sets of defined steps structured to process instructions/data to produce an output" (Kitchin, 2017, p.14). So, to begin to audit an algorithm, we might want to know the steps the algorithms walks through, either in code or in psuedo-code. But here's the catch: all of the commercial discovery tools consider their search algorithms to be one of their major intellectual property assets. They won't reveal the code or even psuedo-code to us.

Of course, algorithms are hardly straighforward and linear, and it's unlikely if we would be able to make heads or tails out of the code if we had access to it. And the steps built out of code are only part of the story: the index has to be considered, too. Here we don't even know the exact parameters of what is in the discovery service's index (although there is more clarity here, since the index is what shows up as visible outputs.)

-----

<h3 style="text-align:center;"><span class="blue">The Algorithm</span></h3>

1. Review Code or psuedo-code
2. Look at the settings
3. Read the documentation
4. Mailing lists
5. Release announcements
6. Review known indexed content

Note:  
Instead, I started by looking through Summon's administratve settings. Any setting that allows you to change how results appear or are ranked will give a hint to something the algorithm values. The Summon documentation was also full of "advanced search techniques" such as keyword weighting and prominity searching techniques, which helped me better understand how the algorithm handles multiple keywords. I also read through mailing list posts from the project managers, specifically around changes to or the functioning of the algorithm, and read the release announcements carefully. 


-----

<h1><span class="raleway">Inputs &amp;</span> <span class="blue" style="line-height:.7em;">Outputs</span></h1>

Note:
But looking at code or understanding the boundaries of the index will only get you so far, and risks fetishizing the algorithm. Algorithms exist to do something, to create outputs. We need to see them work.

Once we have some crude ideas of what the algorithm looks for, we can start testing to see how different inputs create outputs.

-----

<pre><code>
var t = $('[aria-label="Topic Summary"]');

if($(t).length > 0) {

      var topicTitle = $(t).find('h4:first').text();
      var topicFrom = $(t).find('div.from').text();
      var topicSummary = $(t).find('div.snippet').text();

     $.ajax({
        url: "https://REMOTE/SCRIPT/index.php",
        method: "POST",
        data: { search : searchQuery, 
        	    topic: topicTitle,
        	    from: topicFrom,
        	    summary: topicSummary  }
});
</code></pre>

[https://github.com/gvsulib/Summon-2.0-Scripts/blob/develop/summon2.0.js#L161](https://github.com/gvsulib/Summon-2.0-Scripts/blob/develop/summon2.0.js#L161)

Note:
The code was a bit crude, but it worked. Whenever Summon executed a search and a Topic Explorer result was shown, a jQuery script (a bit more sophisticated than this sample) would grab the search query and the heading, source, and text of the Topic Explorer result and send a POST request to a PHP script that parsed the data and stored it in a MySQL database. This method works for looking at the results of what other people are searching for, but you need to be cautious about privacy.

You could easily convert this to a bookmarklet to run on a page where you define a search, or create a bot or spider to scrape the page and store the results from all manner of algorithms: search results, database recommendations, spelling corrections, query expansions, autosuggestions, related topics, related searches, and more. (There are some legal concerns we'll get to in a moment with these approaches.)

-----

![Search results for a known item on LGBT youth returns 2 results: the item and a book on mental illness](img/lgbt_mental_illness.jpg)

A known item search for a book on LGBT youth returns the item and a random book on mental illness. What made the algorithm suggest this item?

Note:
Sharing problematic ones, like this known item search for a book on LGBT youth that returns only 2 items: the book and a guide to "mental illness," can help us understand how those different factors are weighted, or how the algorithm decides to select specific results. We can then test those hypotheses over and over, refining the results. 

But the items at the margins, rather than the "normal" results, are often the ones that expose the inner workings of the algorithm more clearly.


-----

![Screenshot of Zenodo page showing Topic Explorer results](img/data.png)

[http://dx.doi.org/10.5281/zenodo.47723](http://dx.doi.org/10.5281/zenodo.47723)

Note:
I matched 8,000 search queries with their respective topic explorer results, and released them as a data set, if you want to look them over or use them in your research. The data set includes very general search terms, usually 1-3 keywords each, and the respective Topic Explorer result for each. There is potentially the issue of user privacy here, which increases I believe as the searches become more sophisticated and personal.


-----

<h1><span class="raleway" style="display:inline !important;">Use</span>  &amp; <span class="blue">Effect</span></h1>

Note:
But algorithms aren't just code and inputs and outputs. They are used by people in order to do something else. We need to study those effects, too, and this is where my research is taking me.

-----

<!-- .slide: data-background-image="img/kitchin.jpg" -->

### Algorithms are not just what programmers create, or the effects they create based on certain input, they are also what users make of them on a daily basis.

#### Rob Kitchin

Kitchin, R. (2017). Thinking critically about and researching algorithms. *Information, Communication & Society, 20*(1), p.18, DOI: 10.1080/1369118X.2016.1154087

Note:
They affect the world, showing and hiding possibilities from researchers, suggesting to new researchers what a broad search might really be about. In addition to our work at understanding what an algorithm looks at, and what kinds of results it returns, we need to ask how it affects the users who interact with the algorithm and its results. This is where ethnography and user research can come in. We need to be talking to users, and running ethnographic experiments to better understand the impact that algorithmic outputs - both good and bad - have on learning and research.

-----

<!-- .slide: data-background-image="img/ananny.jpg" -->

### Reckless associations—made by humans or computers—can do very real harm especially when they appear in supposedly neutral environments.

#### Mike Ananny

[The Curious Connection Between Apps for Gay Men and Sex Offenders](https://www.theatlantic.com/technology/archive/2011/04/the-curious-connection-between-apps-for-gay-men-and-sex-offenders/237340/)

Note:
There are challenging, scary, ethical issues at work here. Library search tools are positioned as neutral, objective places for learning and research. That is not the case, part of the reason for auditing our algorithmic tools is to both help push against this kind of "objective" marketing, and also to work with vendors to improve the algorithms. 

-----

<!-- .slide: data-background-image="img/beer.jpg" -->

### The purpose of a system is what it does.

#### Stafford Beer

Beer, S. (2002). “What is Cybernetics?” Kybernetes, 31(2), pp. 209–19.

Note:
A word on the responsibilities of vendors. If you search tool reinforces and reproduces systemic racial, gender, religious, or other biases - it doesn't matter if you "didn't intend" to build a system with those biases. That's what you system has become. It is your responsibility to make a system that is fair for all users.

-----

<h2 style="text-align:center;"><span class="blue">Opportunities:</span></h2>

* Pressures of wealth creation are less direct
* <span style="color: #222;">Not subject to live A/B testing, <abbr title="Machine Learning">ML</abbr>/<abbr title="Artificial Intelligence">AI</abbr></span>
* <span style="color: #222;">Content creators don't "game" the algorithm</span>

Note:
Algorithms in Library discovery are not affected by some of the most challenging parts of researching search algorithms. For one, the pressures of capital and wealth creation are not as direct as in an advertising and surveillance supported search tool like Google. There are (theoretically) no ads in our discovery services, although that doesn't mean there isn't surveillance. And since the discovery services are just one ganglia of larger academic publishing operations, there are incentives to get users to look at PDFs from one of their databases, but overall, there is less emphasis on things other than search results to examine.

-----

<h2 style="text-align:center;"><span class="blue">Opportunities:</span></h2>

* <span style="color: #bbb;">Pressures of wealth creation are less direct</span>
* Not subject to live A/B testing, <abbr title="Machine Learning">ML</abbr>/<abbr title="Artificial Intelligence">AI</abbr>
* <span style="color: #222;">Content creators don't "game" the algorithm</span>

Note:
Because libararies are licensing this software, we expect that the vendor won't use our user bases to experiment with new features, at least in a live environment. And as of this moment, none of the vendors appears to be emplying machine learning algorithms to personalize search results for our users. (It will get there, but some of them don't even have proper https support, so I think we're safe for a bit.) We can be pretty sure that all of our users are seeing the same results for the same searches (except for some differences in on-campus and off-campus searches.)

-----

<h2 style="text-align:center;"><span class="blue">Opportunities:</span></h2>

* <span style="color: #bbb;">Pressures of wealth creation are less direct</span>
* <span style="color: #bbb;">Not subject to live A/B testing, <abbr title="Machine Learning">ML</abbr>/<abbr title="Artificial Intelligence">AI</abbr></span>
* Content creators don't "game" the algorithm

Note:
Finally, the content these search tools have indexed isn't written to be searched in a search engine like web content. Much of it is written without worrying whether anyone will or can read and make sense of it, let alone a search engine. So when a result appears in a search, we can be reasonably sure it is there because of the algorithms choice, and not manipulation on the part of an Assistant Professor of Botany somewhere. 

-----

<h2 style="text-align:center;"><span class="blue">Challenges:</span></h2>

* Dependant on local collection practices
* <span style="color: #222;">Metadata is a hot mess</span>
* <span style="color: #222;">Restrictive <abbr title="End User License Agreements">EULA</abbr>s</span>

Note:
On the other hand, discovery systems have challenges that are not as common in other algorithmic systems, or unique to library discovery. The most obvious is that search results from my discovery instance won't be the same for yours, because of the different collection policies of our institutions. This might not affect the ancilary algorithms that are sprinkled around the main search results, like Topic Explorer or related searches, but it definitely affects the results from your collection.

-----

<h2 style="text-align:center;"><span class="blue">Challenges:</span></h2>

* <span style="color: #bbb;">Dependant on local collection practices</span>
* Metadata is a hot mess
* <span style="color: #222;">Restrictive <abbr title="End User License Agreements">EULA</abbr>s</span>

Note:
Trying to understand why something appears in a results set can be challenging, because items in a discovery service's index often blend all the varied metadata practices of hundreds or different database providers into one big, messy soup. Of course, they often have a more structured taxonomy, as well, but results may appear because one of your keywords matched a thesaurus entry for a subject term in an obscure database. This can complicate  understanding how algorithsm choose results.

-----

<h2 style="text-align:center;"><span class="blue">Challenges:</span></h2>

* <span style="color: #bbb;">Dependant on local collection practices</span>
* <span style="color: #bbb;">Metadata is a hot mess</span>
* Restrictive <abbr title="End User License Agreements">EULA</abbr>s

Note:
If you want to study a tool that isn't the one your institution subscribes to, you may be thwarted by the End User License Agreement for the discovery service. Both EBSCO discovery service and OCLC's Worldshare prohibt the search interface from being used by "unauthorized users," which is basically everyone but currently affiliated students, staff, "registered users" and faculty at the subscribing institution. 

Even if you could use the interfaces, none of us has the time to manually search and record results, so we'd naturally write a script to do this for us. But the EULA may prohibt this, as well. (The Computer Fraud and Abuse Act is also so broad that even if the EULA didn't prohibit this, you might be in legal trouble from scraping results anyway.) If you subscribe to a service, you may be able to collect the results with a script in the guise of collecting usage data. That's what I did with Summon.

(A quick point of order: I am not a lawyer and this is not legal advice.)

-----

# <span style="display:inline;font-family:Raleway;font-weight:100;">Join</span> <span class="blue">Me?</span> 

Note:
So, this is my pitch: help me better understand our library discovery algorithms. Either dive in yourself, and examine the algorithms, inputs and outputs, and talk to users, and publish what you learn. Or, if you're an authorized user of EDS or Worldshare, I'd love to talk with you. The restrictive license agreements say I can't use the tools, but they never said anything about me asking an authorized user to collect the search results for me. 

You'll also notice that I'm only mentioning that two of the discovery services have End User License agreements. I'll let you draw your own conclusions from that information.

-----

# <span style="display:inline;font-family:Raleway;font-weight:100;">Thank</span><span class="blue">You</span> 

-----

<h2><span class="blue">Photo Credits</span></h2>

* Paul Goodman: *Growing Up Absurd*
* Dre: [NC State Libraries](http://www.lib.ncsu.edu/staff/akorphan)
* Rob Kitchin: [Maynooth University](https://www.maynoothuniversity.ie/geography/our-people/rob-kitchin)
* Mike Annany: [mike.annany.com](http://mike.annany.com)

Screenshots by Matthew Reidsma.







