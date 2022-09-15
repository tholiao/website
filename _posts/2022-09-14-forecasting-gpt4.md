---
layout: default
title: "Forecasting GPT-4"
permalink: /forecasting-gpt4
author: Thomas
---

# [DRAFT] Forecasting GPT-4

<head>
    <script>
const images = [
"images/binoculars_man/binoculars_man_city.png",
"images/binoculars_man/binoculars_man_cyberpunk.png",
"images/binoculars_man/binoculars_man_orbs.png",
"images/binoculars_man/binoculars_man_cliffs.png",
];

document.addEventListener('DOMContentLoaded', _ => {
  const randImageIndex = ~~(Math.random() * images.length);
  document.getElementById('randBinoculars').src = images[randImageIndex];
});
    </script>
</head>


<p align="center">
  <img id="randBinoculars" src="images/binoculars_man/binoculars_man_city.png" width="60%" />
</p>

ML researchers joke that each month brings new surprises. I’d like to be less surprised in the coming month, so I’ve tried to forecast what GPT-4 will bring (or PaLM-2, Meerkat, …).

Three years after GPT-3 only three companies have the secret sauce for large language models (LLMs) and write about them: OpenAI, DeepMind, and Google. I expect the next big model to be from one of the trio - most obviously OpenAI, which conspicuously missed its spring / summer GPT announcement this year.

**Interesting predictions**:
- Bigger context window (16k-32k)
- Can browse web, write code as part of response
- Aggressive dataset filtering and curation
- Massive scaling of human feedback
- Incorporating user-generated data (if OpenAI)
- Improved scaling laws

**Boring predictions (I only cover some of these)**:
- No scale up on param count (will be 200-400B params)
- Intermediate generation techniques
- Either trained on task data or with human feedback (e.g. RLHF).
- Improved decoding techniques, hyperparameter search, tokenization
- Not multimodal (if OpenAI)
- Misc data comments (no synthetic data, mostly data available on web)

Since I wrote the first draft of this post September 12th, Google published
[improved scaling laws](https://arxiv.org/abs/2209.06640) on September 13th.

<br>


<p align="center">
  <img src="/images/OpenAI_model_timeline.png" alt="timeline of selected OpenAI model announcements" />
  <div align="center" class="caption">OpenAI has yet to release GPT-4 this year.</div>
</p>
<br>
<p align="center">
  <img src="/images/DeepMind_model_timeline.png"/>
</p>
<br>
<p align="center">
  <img src="/images/Google_model_timeline.png"/>
</p>

## Interesting predictions
- **Longer context.** LLMs in production need to handle much longer inputs than the toy experiments in Playground, for reasoning over longer texts, using very long prompts, or including many in context examples. GPT-2 (2019) has a context window of 2^9 = 512 tokens. GPT-3 (2020) has a 4x larger window at 2^11 = 2048 tokens. Anthropic’s LLMs described in 2021 have a 4x larger window than GPT-3 at 2^13 = 8192 tokens, or about 6000 words. Noting the year-on-year fourfold increase, I expect the next big model in 2022 to have a context window of 2^15 = 32,768 tokens. This is a nontrivial engineering challenge, so I’ll hedge by saying it will be either 2^14 or 2^15.
    - Psst! Here's the context window for OpenAI's `text-davinci-002` (release March 15th).

<p align="center">
  <img src="/images/davinci-002-4k.png" width="800"/>
  <div align="center" class="caption">Wait, this isn't a 2k context window!</div>
</p>

- **Tool use**. OpenAI, DeepMind, and Google have all released models in the past year trained to browse the internet, giving AI unfettered access to the world’s knowledge. Web browsing means that models don’t have to be retrained to teach them more information; they can simply Google facts they need. More generally, tool use helps models output correct answers and perform more specialized computations. Sufficiently large models already have latent tool use abilities: GPT-3 [can be prompted](https://twitter.com/sergeykarayev/status/1569377881440276481) to write Python code to answer math questions or even write API requests (!) to query for information it doesn’t know. I expect general model releases to start including tool use capabilities. I predict the next GPT-4 will improve on WebGPT capabilities, but these tool use capabilities will be heavily restricted to avoid e.g. inadvertently sending malicious API requests.
    - Comment: After this post was first published, Adept released demos of their [Act-1 model](https://www.adept.ai/act), "a large-scale Transformer trained to use digital tools".

<p align="center">
  <img src="/images/pile_components.png" width="600" />
  <div align="center" class="caption">The <a href="https://arxiv.org/abs/2101.00027">Pile</a> includes far more
  specialized datasets than GPT-3 was trained on.</div>
</p>

- **Pretraining data improvements**. The most extreme scaling bulls would have you [believe](https://scale.com/blog/text-universal-interface) that dumping “whole mountains of barely filtered, mostly unedited scrapes of the internet into the eager maw of a hungry model” is the way of the future. I’m confident there will be increasing attention to the pretraining data over the next 18 months, primarily focusing on processing data carefully and curating data sources. The amount of data will remain the dominant factor for performance (over quality), but companies will pluck low hanging fruit here. Note that for multimodal models, reducing noise in data is critical and matters more than scale: no amount of captions help multimodality if the captions do not describe what’s in the image. 
  - **More specialized data sources**. While GPT-2 was trained primarily on WebText, a dataset scraped from outbound reddit links, GPT-3 included a (noisier) web scrape, Common Crawl, as well as two books corpora (Books1, Books2) and en-Wikipedia. The general trend has been to add more specialized data sources, for example the Pile (OPT, GLM-130B, etc) includes arXiv, PubMed, FreeLaw, StackExchange, USPTO, etc. I would expect the next big model to ingest even more PDFs and specialized documents from the internet (or focus on cleaning up those subsets of common crawl).
    - It’s interesting to compare GPT-2 vs GPT-3 at similar parameter counts (1.5 vs 1.3B). On CoQA, GPT 2 1.5B: 55 F1; GPT-3 1.3B: 65 F1. On Lambada, GPT2 1.5B: 63%, GPT3 1.3B: 56% - there is a weird drop in the curve here, otherwise it would be around 72%. (Note that amount of compute is different)
  - **More aggressive dataset filtering**. Works since GPT-3 (2020) usually filter the web scrape part of their dataset with e.g. a quality classifier trained on a higher quality dataset such as WebText, Wikipedia, and books.  This is a crude approach which is likely to filter out mangled or empty documents, but may resemble document similarity for OOD high quality documents; I speculate that a classifier with only WebText for positive examples would be looking for documents that redditors like and not just quality. There should be even better automated ways to automatically filter for high quality documents. However I think it’s unlikely the next big model will improve significantly in this regard, because ML engineers don’t like to think about data and because it’s expensive to measure how improving data quality improves model performance (need to train a model). Also, I think most easy improvements here will get washed away by scale.
    - Comment: After this post was first published, Google released their latest multimodal trained on a aggressively filtered dataset dataset which filtered out 90% of the intial scrape.
- **Incorporating user-generated data** (if OpenAI). The [InstructGPT paper](https://arxiv.org/abs/2203.02155) uses prompts generated by users in Playground (but not using the API in production). The appeal of user-generated data is the sheer diversity, since you have far more people writing prompts than you could have through managing your own labellers. However, Google, DeepMind, and FB do not offer commercial LLM APIs, so they have no way to obtain this data. AI21, OpenAI, and Cohere do. A meaningful forecast here would predict the change in quantity of user-generated data used. But since OpenAI didn't disclose this information, it's impossible to make an exact prediction.
- **Improved scaling laws**. DeepMind’s [Chinchilla work](https://arxiv.org/abs/2203.15556) improved on earlier scaling laws. I believe there is still headroom for improved scaling behaviour. I predict the next big model released by Google or OpenAI will follow a different scaling law than Chinchilla.
    - Comment: After this post was first published, Google released [improved scaling laws](https://arxiv.org/abs/2209.06640).

## Boring predictions
- **Not that large**. I predict that the largest size for OpenAI and DeepMind’s next models to be between 50B to 500B parameters. Especially given DeepMind's recent Chinchilla work, I would be extremely surprised if their next models were 1T parameters. My impression is that Google is most likely of the three to train a dense 1T model first.
 - **On preserving data structure**. Structured data like tables [seem to improve in-context learning](https://arxiv.org/abs/2208.01009). The intuition is that each row or example functions like few-shot prompt examples, so the structure is similar to in-context learning. My understanding is that web scrapes often mangle table structure, so it’s possible that the next big model will specially process this kind of structured data. I think this starts to get too into the weeds and is likely not worth doing as part of the pretraining data pipeline.
- **On data source diversity**. It’s hard to improve over web crawls for data source diversity per se, unless you start digitizing physical media (like scanning books), converting other digital sources (like video captions), or accessing social media, which runs serious privacy risks, so I don’t expect a concerted effort on this front. 
- **On synthetic data**. I do not expect any inclusion of synthetic data in the pretraining data, even for code or math datasets. (A) the research in this area is still nascent, and we don’t know what makes for good synthetic data (B) there is sufficient data from natural sources, so synthetic data is not yet needed.
- **Improved decoding techniques, hyperparameter search, tokenization**. These are all relatively small improvements, so they may not be included. Improving tokenization (e.g. tokenizing all digits separately to improve math performance) might be a big deal.

## Predicting performance
The world’s best (disclosed) LLM is locked away by Google. Neither has anyone announced a model combining well-known separate improvements. The uncertainty around how the best or best possible models today behave ripples into the future. The next best model jumps off from a model we don’t have access to. Do iterative techniques combine, brick by brick, to build higher? Or does each new trick substitute for another?

Major labs withhold results until convenient, delaying announcements by half a year or more. Papers emerge during conference season and hibernate in between. It’s hard to gauge whether enough time has passed for new advancements if you don’t know when to start timing.

My predictions

<p align="center">
  <img src="/images/toucan_seal_crisp.png" width="150" />
</p>

## Endnotes
References above are not comprehensive. If an important paper should be included, feel free to tweet it [@thomasiliao](twitter.com/thomasiliao).

Thanks for reading the first post on my personal blog! I welcome constructive feedback or
discussions over email.

Thanks to [Charlie Snell](https://twitter.com/sea_snell), [Rohan Taori](https://twitter.com/rtaori13), 
and [asara](https://twitter.com/nearcyan) for comments.
