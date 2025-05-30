---
layout: default
title: "Why are there so few independent eval startups?"
permalink: /eval-startups
author: Thomas
---

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
  /* -------- TYPOGRAPHY & LAYOUT -------- */
  @font-face{font-family:'NYT Imperial';src:url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-normal-500.ttf') format('truetype');font-weight:500;font-style:normal;font-display:swap;}
  @font-face{font-family:'NYT Imperial';src:url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-italic-500.ttf') format('truetype');font-weight:500;font-style:italic;font-display:swap;}
  @font-face{font-family:'NYT Imperial';src:url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-normal-600.ttf') format('truetype');font-weight:600;font-style:normal;font-display:swap;}
  @font-face{font-family:'NYT Imperial';src:url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-normal-700.ttf') format('truetype');font-weight:700;font-style:normal;font-display:swap;}
  @font-face{font-family:'NYT Imperial';src:url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-italic-700.ttf') format('truetype');font-weight:700;font-style:italic;font-display:swap;}
  body{font-family:'NYT Imperial',Georgia,serif;}
  .wrapper{max-width:600px;width:90%;margin:0 auto;padding:0 10px;}
  h1,h2,h3,h4,h5,h6{font-family:'NYT Imperial',Georgia,serif;font-weight:700;margin-top:.25em;margin-bottom:1em;line-height:1.25;}
  h1{font-size:calc(1.5rem + 0.5vw);letter-spacing:-0.5px;}
  h2{font-size:calc(1.3rem + 0.3vw);letter-spacing:-0.3px;}
  h3{font-size:calc(1.1rem + 0.2vw);letter-spacing:-0.2px;}
  p,li,div{font-size:calc(1rem + 0.1vw);line-height:1.625;margin-bottom:1.2em;letter-spacing:0.01em;text-align:left;word-spacing:0.05em;}
  @media(max-width:600px){p,li,div{font-size:18px;line-height:1.5;}h1{font-size:28px;}h2{font-size:24px;}h3{font-size:20px;}.wrapper{width:95%;padding:0 12px;}}

.post-date{font-family:ui-monospace,SFMono-Regular,Menlo,Monaco,"Courier New",Courier,monospace;font-variant-numeric:tabular-nums;}

/* header */
.site-header{min-height:0;padding:8px 0;margin-bottom:0;border-bottom:none!important;}
.site-header .wrapper{display:flex;align-items:baseline;}
.site-title{margin-right:20px;line-height:1.2;}
.site-nav .page-link{line-height:1.2;font-size:16px;}

/* wang strip */
.site-header .wang-strip{height:40px;margin:0.5rem auto;overflow:hidden;max-width:600px;width:100%;padding:0 2px;text-align:center;}
.site-header .wang-strip canvas{display:inline-block;}
@media(max-width:600px){.site-header .wang-strip{width:100%;max-width:100%;margin:0;padding:0;}}


/* --- Image styling --- */
.seal-image{width:30%;height:auto;max-width:200px;display:block;margin:3rem auto 1.5rem;}

</style>

<!-- ---------------- scripts ------------------ -->
<script>
function generateWangTiles(){const container=document.querySelector('.wang-strip');if(!container)return;const canvas=document.createElement('canvas');container.innerHTML='';container.appendChild(canvas);
  const EDGE={R:'#c91d1d',Y:'#e8b700',B:'#4285f4',W:'#ffffff'};
  const CODES=["RWWW","RYWY","RWRR","YBYW","YYYB","BBBW","BWRY","YYBY","WYWB","WRRY","RWBW"];
  const TILES=CODES.map(c=>({code:c,edges:c.split('')}));
  const W=container.offsetWidth;const BASE=30;const cols=Math.floor(W/BASE)+1;const S=W/cols;canvas.width=W;canvas.height=40;const ctx=canvas.getContext('2d');
  const row=new Array(cols);
  const bannedFirst=["YBYW","YYBY"];
  function fits(tile,x){
    if(x===0){return !bannedFirst.includes(tile.code);} // prevent banned tiles in first cell
    const left=row[x-1];
    return left.edges[0]===tile.edges[2] && left.code!==tile.code;
  }
  function place(x=0){if(x===cols)return true;const shuffled=[...TILES].sort(()=>Math.random()-0.5);
    for(const t of shuffled){if(fits(t,x)){row[x]=t;if(place(x+1))return true;}}
    row[x]=null;return false;}
  place();
  const padY=4;
  function draw(t,px,py,s){const cX=px+s/2,cY=py+s/2;
    ctx.lineWidth=0;
    // top
    ctx.fillStyle=EDGE[t.edges[1]];ctx.beginPath();ctx.moveTo(px,py);ctx.lineTo(px+s,py);ctx.lineTo(cX,cY);ctx.closePath();ctx.fill();
    // right
    ctx.fillStyle=EDGE[t.edges[0]];ctx.beginPath();ctx.moveTo(px+s,py);ctx.lineTo(px+s,py+s);ctx.lineTo(cX,cY);ctx.closePath();ctx.fill();
    // bottom
    ctx.fillStyle=EDGE[t.edges[3]];ctx.beginPath();ctx.moveTo(px+s,py+s);ctx.lineTo(px,py+s);ctx.lineTo(cX,cY);ctx.closePath();ctx.fill();
    // left
    ctx.fillStyle=EDGE[t.edges[2]];ctx.beginPath();ctx.moveTo(px,py+s);ctx.lineTo(px,py);ctx.lineTo(cX,cY);ctx.closePath();ctx.fill();}
  row.forEach((t,i)=>{if(t)draw(t,i*S,padY,S);});}

document.addEventListener('DOMContentLoaded',generateWangTiles);
</script>
</head>

<h1>Why eval startups fail</h1>
<p class="post-date">May 8<sup>th</sup>, 2025</p>
<em class="subtitle">Why are there so few independent eval startups?</em>

<p>Whenever there's a new AI trend, like agents, or voice, or voice agents, developers are faced with a flurry of  options, and a subset of them are convinced that there's a business opportunity in identifying the best models and selling that knowledge to other developers—that is, selling evals. I've seen this in every wave of generative AI, since before we were calling it generative AI. I haven't seen any succeed, outside the safety evals niche.</p>

<p>I have a few theories why independent eval startups die. First, people who can design and run good evals can make more money and have more influence in other parts of the model development stack, so talent attrits. Second, eval startups have a hard time finding customers, because clients have to be technical developers who want to build with APIs, but also not technical enough to run their own evals. And third, eval startups face immense optimization pressure that renders their evals useless, both from garden-variety hill climbing and through pressure from model developers.</p>

<h2>Eval talent is better used elsewhere</h2>

<p>Good eval talent moves to other parts of the stack because the same skills that are needed for good evals are useful for post-training and for application development, and these areas capture more value, i.e. make more money, and have more direct influence on model development, i.e. are more prestigious and interesting.</p>

<p>For example, building a good eval requires collecting high-quality data, whether from operating a human feedback pipeline or through synthetic data. Collecting high-quality data is a major bottleneck for post-training. The amount of data in an eval is always smaller than the amount of data collected for post-training, by orders of magnitude, so in a real sense the value you generate from collecting data for evals is capped compared to the amount of data you generate from collecting data for post-training, assuming the value per datapoint is equal. Additionally, the financial return on a good post-train is potentially very high, up to a few hundred million or billions of dollars, whereas the financial return on an eval is capped at the size of your largest eval contract, which is nowhere close. This dynamic is readily apparent to smart young researchers who incidentally understand the notion of opportunity cost. An illustrative example is provided by three researchers who quit their jobs at Epoch AI evaluating agents to instead start a startup building post-training tools for agents <a href="#ref-0" class="reference-link">[0]</a>.</p>

<h2>Not enough eval customers</h2>

<p>Even if an eval startup retains talent, it still has a hard time finding customers, because the Venn diagram intersection of the two circles "building on model API" and "unable to evaluate models" has negligible area.</p>

<p>When you look at charts comparing vendors by Gartner, a market research firm, the X-axes are fantastical and the Y-axes are fictional; in short, the charts are made to be interpreted by toddlers, who have technical caliber comparable to the corporate executives those charts are printed for. If you think I'm exaggerating I encourage you to Google "Gartner Magic Quadrant AI" then report them to the Department of Chart Crimes. This same quagmire ensnares AI eval startups. Any customer that is post-training models is definitely building evals themselves.  A developer who understands the meaning and implication of a 10% improvement on AIME 2024, without tool use, computed with best of N, is not far from just running that eval themselves. If they don't understand the difference between GPT 4o and GPT 4.1 they're the kind of customer that wants solutions, not features, and certainly not an explanation of ELO. Gartner can dumb down for execs, who are deciding on large contracts with cloud providers, but eval startups seem always to want to sell to developers. Thus I am skeptical the market for eval startups is very large, even as the demand for AI services grows.</p>

<h2>Big labs Goodhart evals</h2>

<p>An eval startup that overcomes these two hurdles now has to face down the big labs themselves, who are highly incentivized to climb the public eval and apply pressure and tricks to improve their numbers. Once benchmarks are targeted models can improve rapidly, whether that's from benign adjustments like including more diverse data to outright training on test data, which Meta did for Llama 1 <a href="#ref-1" class="reference-link">[1]</a> and is rumored to have done for Llama 4 <a href="#ref-2" class="reference-link">[2]</a>. So eval startups have to be wary about a potentially adversarial relationship with big labs, who don't want to lose their own customers and will play their unfair advantages. Other kinds of tricks big labs employ include asking employees to vote for their own models on public leaderboards, poaching employees from eval startups, dangling free compute in return for better results, asking for private insights about model performance; the list of shenanigans is long.</p>

<p>A principled team can resist these gambits, but the pallor of suspicion is hard to dispel. For two years every researcher has asked themselves — why is every new model release always at the top of the LMSys Chatbot Arena leaderboard? A new report led by Cohere suggests the cause is systematic gaming, claiming that Meta tested twenty-seven unique model variants before releasing Llama 4 <a href="#ref-3" class="reference-link">[3]</a>. Meta, by the way, advertised that its tiny Llama 4 Maverick model outperformed GPT-4.5, before revealing that the result was achieved with a version optimized specifically for Chatbot Arena, and not the released version, which ranked abysmally. Goodhart's Law: when a measure becomes a target, it ceases to be a good measure. And all eval startups have to sell are measures.</p>

<h2>Safety evals are an exception</h2>

<p>I believe eval startups can work when they're targeting safety benchmarks specifically. Researchers who want to work on safety evals tend to be ideologically opposed to working on capabilities, which means they don't migrate to post-training or applications due to monetary incentives. (This is how the internal safety eval divisions of the big labs retain talent.) They can provide services to technical clients who are capable of replicating those services, because it's specifically important for safety evals that those services are provided by an external vendor and not only done internally. They can also sell to policymakers, or have business assured by regulation if proposals for external model audits are passed. Safety eval startups would still be vulnerable to Goodharting, but if labs are Goodharting safety evals, there are other things to be worried about. So safety evals have particular characteristics that make them more amenable than other evals.</p>

<p>I've presented three reasons why it's hard for eval startups to survive. The most pernicious of these is the first, which is that there are better opportunities available for any company or engineer who is good at evals, but the other two pose serious headwinds as well. I have nothing against eval startups, and I am rooting for them, but I am not counting on them.</p>

<div class="divider">❖ ❖ ❖</div>

<h2>Additional comments</h2>
<p>The above is for application-focused evals, i.e. evals for developers who want to build on top of model APIs. There are also startups that want to sell research evals to big labs. These will fail, because the primary point of research evals is to set research directions, and big labs will never outsource setting their research agenda. Also, outsourcing research evals adds a ton of latency to model iteration, and velocity is everything.</p>

<p>Added: <em>May 21<sup>st</sup>, 2025</em>. There's a difference between selling evals and selling evals tooling. In the same way that selling human labels is different from selling tooling to collect human labels - one is an ops business with ops margins, the other is a SaaS business with SaaS margins - selling evals and selling evals tooling have two very different economics. LM Arena, the organization behind Chatbot Arena, today announced a $100M seed round <a href="#ref-4" class="reference-link">[4]</a>. That's a very large sum of money. For comparison, Mistral, the French company aiming to train frontier models, raised only slightly more in their seed in 2023 <a href="#ref-5" class="reference-link">[5]</a>. LM Arena has the advantage of millions of volunteers labelling for free, effectively compensated with access to otherwise-expensive frontier models, but I still don't think that makes selling evals a great business for them. I think that if they do well it will be through offering supplementary services, like selling software or selling access to data streams.</p>

<div class="divider">❖ ❖ ❖</div>

<h2 id="links-referenced">Links referenced</h2>
<div class="reference-item" id="ref-0">[0] <a href="https://techcrunch.com/2025/04/19/famed-ai-researcher-launches-controversial-startup-to-replace-all-human-workers-everywhere/">Famed AI researcher launches controversial startup to replace all human workers everywhere</a>. Mirror: <a href="https://archive.ph/vHVoM">Archive.ph</a></div>

<div class="reference-item" id="ref-1">[1] <a href="https://x.com/suchenzang/status/1886542845064175928">Susan Zhang tweet about Llama 1 training data</a>. Mirror: <a href="https://archive.ph/xjLKm">Archive.ph</a></div>

<div class="reference-item" id="ref-2">[2] <a href="https://www.reddit.com/r/LocalLLaMA/comments/1jt8yug/serious_issues_in_llama_4_training_i_have/">Serious issues in Llama 4 training. I Have Submitted My Resignation to GenAI</a>. Mirror: <a href="https://archive.ph/rnLRY">Archive.ph</a></div>

<div class="reference-item" id="ref-3">[3] <a href="https://arxiv.org/abs/2504.20879">The Leaderboard Illusion: On the Limits of LLM Benchmark Reliability</a></div>

<div class="reference-item" id="ref-4">[4] <a href="https://x.com/lmarena_ai/status/1925241333310189804">LM Arena seed round announcement</a>. Mirror: <a href="https://archive.ph/xxx">Archive.ph</a></div>

<div class="reference-item" id="ref-5">[5] <a href="https://techcrunch.com/2023/06/13/frances-mistral-ai-blows-in-with-a-113m-seed-round-at-a-260m-valuation-to-take-on-openai/">France's Mistral AI blows in with a $113M seed round at a $260M valuation to take on OpenAI</a>. Mirror: <a href="https://archive.ph/xxx">Archive.ph</a></div>

<div class="divider">❖ ❖ ❖</div>

<div class="article-footer">
  <h3>Endnotes</h3>
  <p>Opinions and errors my own. Thanks to <a href="https://x.com/kalomaze">@kalomaze</a>, <a href="https://x.com/sea_snell">Charlie Snell</a>, <a href="https://x.com/andersonbcdefg">Ben Anderson</a>, <a href="https://www.rohantaori.com/">Rohan Taori</a>, <a href="https://www.natolambert.com/">Nathan Lambert</a>, <a href="https://x.com/menhguin">Minh Nhat Nguyen</a>, and <a href="https://main-horse.github.io/">@main_horse</a> for comments.</p>
  
  <h3>Changelog</h3>
  <p> 2025-05-08: Initial</p>
  <p> 2025-05-21: Minor edits</p>
</div>

<br>

<script>
document.addEventListener('DOMContentLoaded', () => {
  // 1️⃣ Grab the “Thanks to …” paragraph inside the footer
  const thanksP = document.querySelector('.article-footer p');   // adjust if you add an id/class
  if (!thanksP) return;

  // 2️⃣ Separate the prefix (“…Thanks to ”) and suffix (“ for comments.”)
  const match = thanksP.innerHTML.match(/^(.*?Thanks to )(.*?)( for comments\.)$/i);
  if (!match) return;
  const [ , prefix, inner, suffix ] = match;

  // 3️⃣ Collect each <a> tag inside the inner segment
  const temp = document.createElement('div');
  temp.innerHTML = inner;
  const links = Array.from(temp.querySelectorAll('a'));

  // 4️⃣ Fisher–Yates shuffle
  for (let i = links.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [links[i], links[j]] = [links[j], links[i]];
  }

  // 5️⃣ Rebuild with Oxford-comma rules
  const htmlLinks = links.map(a => a.outerHTML);
  const randomized =
    htmlLinks.length > 2
      ? htmlLinks.slice(0, -1).join(', ') + ', and ' + htmlLinks.slice(-1)
      : htmlLinks.join(' and ');

  // 6️⃣ Replace the paragraph content
  thanksP.innerHTML = prefix + randomized + suffix;
});
</script>

<img src="/images/toucan_seal_2.png" class="seal-image" alt="Thomas Liao's toucan seal" />
