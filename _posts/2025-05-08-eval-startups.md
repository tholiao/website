---
layout: default
title: "Why are there so few independent eval startups?"
permalink: /eval-startups
author: Thomas
---

# Why eval startups fail

*Why are there so few independent eval startups?*


<head>
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-F24GH950P6"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-F24GH950P6');
</script>

<style>
  body {
    font-family: 'Merriweather', Georgia, serif;
  }
  
  /* Constrain content width to approximately 80 characters */
  .wrapper {
    max-width: 36em;
    margin-left: auto;
    margin-right: auto;
  }
  
  h1, h2, h3, h4, h5, h6 {
    font-family: 'Merriweather', Georgia, serif;
    font-weight: 700;
  }

  p, li, div {
    font-family: 'Merriweather', Georgia, serif;
    font-size: 18px;
    line-height: 1.56;
    text-align: justify;
  }
  
  /* Fix header alignment */
  .site-header .wrapper {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    width: 100%;
  }
  
  .site-nav {
    display: inline-block;
    margin-left: auto;
    text-align: right;
  }
  
  .site-title {
    margin-bottom: 0;
  }
  
  .page-link {
    font-size: 16px; /* Same size as site title */
  }
  
  h2 {
    margin-top: 1.5em;
    margin-bottom: 0.5em;
  }

  .reference-link {
    cursor: pointer;
    text-decoration: none;
    vertical-align: super;
    font-size: 0.75em;
    color: #0366d6;
  }
  
  .back-to-text {
    display: inline-block;
    margin-left: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 1.2em;
    color: #0366d6;
  }
  
  .reference-item {
    margin-bottom: 8px;
  }
  
  /* Remove social media icons in the footer for this post only */
  .footer-col-2 {
    display: none;
  }
</style>

<!-- Include Merriweather from Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Merriweather:ital,wght@0,300;0,400;0,700;0,900;1,300;1,400;1,700;1,900&display=swap" rel="stylesheet">

<script>
document.addEventListener('DOMContentLoaded', function() {
  // Process reference links when the page is loaded
  processReferenceLinks();
});

function processReferenceLinks() {
  // Get all reference links in the document
  const referenceLinks = document.querySelectorAll('a[href^="#ref-"]');
  const referencesSection = document.getElementById('links-referenced');
  
  if (!referencesSection) return;
  
  // Process each reference link
  referenceLinks.forEach((link, index) => {
    // Store the original position
    const refId = link.getAttribute('href').substring(1);
    const refTarget = document.getElementById(refId);
    
    if (refTarget) {
      // Add a back button to the reference
      const backBtn = document.createElement('a');
      backBtn.textContent = '↵'; // Unicode return arrow
      backBtn.className = 'back-to-text';
      backBtn.title = 'Back to text';
      backBtn.href = `#ref-src-${index}`;
      
      // Add an ID to the reference source in the text
      const sourceMarker = document.createElement('span');
      sourceMarker.id = `ref-src-${index}`;
      link.parentNode.insertBefore(sourceMarker, link);
      
      // Add the back button to the reference target
      refTarget.appendChild(backBtn);
    }
  });
}
</script>
</head>

Whenever there's a new AI trend, like agents, or voice, or voice agents, developers are faced with a flurry of  options, and a subset of them are convinced that there's a business opportunity in identifying the best models and selling that knowledge to other developers—that is, selling evals. I've seen this in every wave of generative AI, since before we were calling it generative AI. I haven't seen any succeed, outside of a very particular edge case.

I have a few theories why independent eval startups die. First, people who can design and run good evals can make more money and have more influence in other parts of the model development stack, so talent attrits. Second, eval startups have a hard time finding customers, because clients have to be technical developers who want to build with APIs, but also not technical enough to run their own evals. And third, eval startups face immense optimization pressure that renders their evals useless, both from garden-variety hill climbing and through pressure from model developers. 

## Eval talent is better used elsewhere

Good eval talent moves to other parts of the stack because the same skills that are needed for good evals are useful for post-training and for application development, and these areas capture more value, i.e. make more money, and have more direct influence on model development, i.e. are more prestigious and interesting. 

For example, building a good eval requires collecting high-quality data, whether from operating a human feedback pipeline or through synthetic data. Collecting high-quality data is a major bottleneck for post-training. The amount of data in an eval is always smaller than the amount of data collected for post-training, by orders of magnitude, so in a real sense the value you generate from collecting data for evals is capped compared to the amount of data you generate from collecting data for post-training, assuming the value per datapoint is equal. Additionally, the financial return on a good post-train is potentially very high, up to a few hundred million or billions of dollars, whereas the financial return on an eval is capped at the size of your largest eval contract, which is nowhere close. This dynamic is readily apparent to smart young researchers who incidentally understand the notion of opportunity cost. An illustrative example is provided by three researchers who quit their jobs at Epoch AI evaluating agents to instead start a startup building post-training tools for agents <a href="#ref-0" class="reference-link">[0]</a>. I have also heard many stories from friends inside big labs who sweat over evals, only to see the credit for improving models go to the post-training team and not the evals team, so they switch internally to post-training, surprise surprise. (There is a big exception here, which I'll get to soon).

## Not enough eval customers

Even if an eval startup retains talent, it still has a hard time finding customers, because the Venn diagram intersection of the two circles "building on model API" and "unable to evaluate models" has negligible area. 

When you look at charts comparing vendors by Gartner, a market research firm, the X-axes are fantastical and the Y-axes are fictional; in short, the charts are made to be interpreted by toddlers, who have technical caliber comparable to the corporate executives those charts are printed for. If you think I'm exaggerating I encourage you to Google "Gartner Magic Quadrant AI" then report them to the Department of Chart Crimes. This same quagmire ensnares AI eval startups. Any customer that is post-training models is definitely building evals themselves.  A developer who understands the meaning and implication of a 10% improvement on AIME 2024, without tool use, computed with best of N, is not far from just running that eval themselves. If they don't understand the difference between GPT 4o and GPT 4.1 they're the kind of customer that wants solutions, not features, and certainly not an explanation of ELO. Gartner can dumb down for execs, who are deciding on large contracts with cloud providers, but eval startups seem always to want to sell to developers. Thus I am skeptical the market for eval startups is very large (again with one large exception), even as the demand for AI services grows. 

## Big labs Goodhart evals

An eval startup that overcomes these two hurdles now has to face down the big labs themselves, who are highly incentivized to climb the public eval and apply pressure and tricks to improve their numbers. Once benchmarks are targeted models can improve rapidly, whether that's from benign adjustments like including more diverse data to outright training on test data, which Meta did for Llama 1 <a href="#ref-1" class="reference-link">[1]</a> and is rumored to have done for Llama 4 <a href="#ref-2" class="reference-link">[2]</a>. So eval startups have to be wary about a potentially adversarial relationship with big labs, who don't want to lose their own customers and will play their unfair advantages. Other kinds of tricks big labs employ include asking employees to vote for their own models on public leaderboards, poaching employees from eval startups, dangling free compute in return for better results, asking for private insights about model performance; the list of shenanigans is long. 

A principled team can resist these gambits, but the pallor of suspicion is hard to dispel. For two years every researcher has asked themselves — why is every new model release always at the top of the LMSys Chatbot Arena leaderboard? A new report led by Cohere suggests the cause is systematic gaming, claiming that Meta tested twenty-seven unique model variants before releasing Llama 4 <a href="#ref-3" class="reference-link">[3]</a>. Meta, by the way, advertised that its tiny Llama 4 Maverick model outperformed GPT-4.5, before revealing that the result was achieved with a version optimized specifically for Chatbot Arena, and not the released version, which ranked abysmally. Goodhart's Law: when a measure becomes a target, it ceases to be a good measure. And all eval startups have to sell are measures.

## Safety evals are an exception

I keep hinting at an exception to all my claims about why eval startups can't succeed. I believe eval startups work when they're targeting safety benchmarks specifically. Researchers who want to work on safety evals tend to be ideologically opposed to working on capabilities, which means they don't migrate to post-training or applications due to monetary incentives. (This is how the internal safety eval divisions of the big labs retain talent.) They can provide services to technical clients who are capable of replicating those services, because it's specifically important for safety evals that those services are provided by an external vendor and not only done internally. They can also sell to policymakers, or have business assured by regulation if proposals for external model audits are passed. Safety eval startups would still be vulnerable to Goodharting, but if labs are Goodharting safety evals, there are other things to be worried about. So safety evals have particular characteristics that make them more amenable than other evals.

I've presented three reasons why it's hard for eval startups to survive. The most pernicious of these is the first, which is that there are better opportunities available for any company or engineer who is good at evals, but the other two pose serious headwinds as well. I have nothing against eval startups, and I am rooting for them, but I am not counting on them.

<div style="text-align: center; margin: 2em 0;">❖ ❖ ❖</div>


## Additional comments
The above is for application-focused evals, i.e. evals for developers who want to build on top of model APIs. There are also startups that want to sell research evals to big labs. These will fail, because the primary point of research evals is to set research directions, and big labs will never outsource setting their research agenda. Also, outsourcing research evals adds a ton of latency to model iteration, and velocity is everything.


<h2 id="links-referenced">Links referenced</h2>
<div class="reference-item" id="ref-0">[0] <a href="https://techcrunch.com/2025/04/19/famed-ai-researcher-launches-controversial-startup-to-replace-all-human-workers-everywhere/">Famed AI researcher launches controversial startup to replace all human workers everywhere</a>. Mirror: <a href="https://archive.ph/vHVoM">Archive.ph</a></div>

<div class="reference-item" id="ref-1">[1] <a href="https://x.com/suchenzang/status/1886542845064175928">Susan Zhang tweet about Llama 1 training data</a>. Mirror: <a href="https://archive.ph/xjLKm">Archive.ph</a></div>

<div class="reference-item" id="ref-2">[2] <a href="https://www.reddit.com/r/LocalLLaMA/comments/1jt8yug/serious_issues_in_llama_4_training_i_have/">Serious issues in Llama 4 training. I Have Submitted My Resignation to GenAI</a>. Mirror: <a href="https://archive.ph/rnLRY">Archive.ph</a></div>

<div class="reference-item" id="ref-3">[3] <a href="https://arxiv.org/abs/2504.20879">The Leaderboard Illusion: On the Limits of LLM Benchmark Reliability</a></div> 

<div style="text-align: center; margin: 2em 0;">❖ ❖ ❖</div>

## Endnotes
Opinions and errors my own. Thanks to [Nathan Lambert](https://www.natolambert.com/), [main_horse](https://main-horse.github.io/), [@kalomaze](https://x.com/kalomaze) for comments. 

## Changelog
- 2025-05-09: Added style updates

<br>
<div style="text-align: center; margin: 2em auto;">
  <img src="/images/toucan_seal_2.png" width="150" style="display: block; margin: 0 auto;" />
</div>
