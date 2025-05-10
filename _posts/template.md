---
layout: default
title: "YOUR POST TITLE"
permalink: /your-custom-url
author: Thomas
---

# YOUR POST TITLE

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
  
  /* Constrain content width to approximately 80 characters with responsive sizing */
  .wrapper {
    max-width: 36em;
    width: 90%;
    margin-left: auto;
    margin-right: auto;
  }
  
  h1, h2, h3, h4, h5, h6 {
    font-family: 'Merriweather', Georgia, serif;
    font-weight: 700;
  }
  
  h1 {
    font-size: calc(1.5rem + 1vw);
  }
  
  h2 {
    font-size: calc(1.3rem + 0.5vw);
  }
  
  h3 {
    font-size: calc(1.1rem + 0.3vw);
  }

  p, li, div {
    font-family: 'Merriweather', Georgia, serif;
    font-size: calc(1rem + 0.2vw);
    line-height: 1.56;
    text-align: justify;
  }
  
  /* Adjust text alignment for small screens */
  @media (max-width: 600px) {
    p, li, div {
      text-align: left;
    }
    
    .wrapper {
      width: 95%;
    }
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
  
  /* Responsive header for mobile */
  @media (max-width: 600px) {
    .site-header .wrapper {
      flex-direction: column;
      align-items: center;
    }
    
    .site-title {
      margin-bottom: 10px;
    }
    
    .site-nav {
      margin-left: 0;
      text-align: center;
    }
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
  
  @media (max-width: 600px) {
    .reference-link {
      font-size: 0.7em;
    }
    
    .back-to-text {
      font-size: 1em;
    }
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

<!-- Your content goes here -->

<h2 id="links-referenced">Links referenced</h2>
<div class="reference-item" id="ref-0">[0] <a href="URL_HERE">TITLE HERE</a>. Mirror: <a href="ARCHIVE_LINK">Archive.ph</a></div>

<div style="text-align: center; margin: 2em 0;">❖ ❖ ❖</div>

## Endnotes
Opinions and errors my own. Thanks to [Name](URL) for comments. 

## Changelog
- DATE: Created post

<br>
<div style="text-align: center; margin: 2em auto;">
  <img src="/images/toucan_seal_2.png" style="display: block; margin: 0 auto; width: min(150px, 40vw);" />
</div>
