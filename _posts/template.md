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
  /* NYT Imperial Font Setup */
  @font-face {
    font-family: 'NYT Imperial';
    src: url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-normal-500.ttf') format('truetype');
    font-weight: 500;
    font-style: normal;
    font-display: swap;
  }
  
  @font-face {
    font-family: 'NYT Imperial';
    src: url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-italic-500.ttf') format('truetype');
    font-weight: 500;
    font-style: italic;
    font-display: swap;
  }
  
  @font-face {
    font-family: 'NYT Imperial';
    src: url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-normal-600.ttf') format('truetype');
    font-weight: 600;
    font-style: normal;
    font-display: swap;
  }
  
  @font-face {
    font-family: 'NYT Imperial';
    src: url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-normal-700.ttf') format('truetype');
    font-weight: 700;
    font-style: normal;
    font-display: swap;
  }
  
  @font-face {
    font-family: 'NYT Imperial';
    src: url('https://raw.githubusercontent.com/FrancesCoronel/nyt-comm/master/fonts/imperial/imperial-italic-700.ttf') format('truetype');
    font-weight: 700;
    font-style: italic;
    font-display: swap;
  }
  
  body {
    font-family: 'NYT Imperial', Georgia, serif;
  }
  
  /* NYT style content constraints */
  .wrapper {
    max-width: 600px;
    width: 90%;
    margin-left: auto;
    margin-right: auto;
    padding: 0 10px;
  }
  
  h1, h2, h3, h4, h5, h6 {
    font-family: 'NYT Imperial', Georgia, serif;
    font-weight: 700;
    margin-top: 2em;
    margin-bottom: 1em;
    line-height: 1.25;
  }
  
  h1 {
    font-size: calc(1.5rem + 0.5vw);
    letter-spacing: -0.5px;
  }
  
  h2 {
    font-size: calc(1.3rem + 0.3vw);
    letter-spacing: -0.3px;
  }
  
  h3 {
    font-size: calc(1.1rem + 0.2vw);
    letter-spacing: -0.2px;
  }

  p, li, div {
    font-family: 'NYT Imperial', Georgia, serif;
    font-size: calc(1rem + 0.1vw);
    line-height: 1.625;
    margin-bottom: 1.2em;
    letter-spacing: 0.01em;
    text-align: left;
    word-spacing: 0.05em;
  }
  
  /* Adjust for small screens */
  @media (max-width: 600px) {
    p, li, div {
      font-size: 18px;
      line-height: 1.5;
    }
    
    h1 {
      font-size: 28px;
    }
    
    h2 {
      font-size: 24px;
    }
    
    h3 {
      font-size: 20px;
    }
    
    .wrapper {
      width: 95%;
      padding: 0 12px;
    }
  }
  
  /* This header alignment is now handled in the section below */
  
  .site-nav {
    display: inline-block;
    text-align: center;
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
  
  /* Reference link styling */
  .reference-link {
    cursor: pointer;
    text-decoration: none;
    vertical-align: super;
    font-size: 0.75em;
    color: #121212;
    background-color: #f7f7f7;
    padding: 1px 3px;
    border-radius: 3px;
    font-weight: 600;
  }
  
  .back-to-text {
    display: inline-block;
    margin-left: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 1.1em;
    color: #333;
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
    margin-bottom: 1.2em;
    font-size: 0.9em;
    line-height: 1.5;
    color: #333;
  }
  
  #links-referenced {
    border-top: 1px solid #e2e2e2;
    margin-top: 3em;
    padding-top: 1.5em;
  }
  
  /* Remove social media icons in the footer for this post only */
  .footer-col-2 {
    display: none;
  }
  
  /* NYT-style divider */
  .divider {
    text-align: center;
    margin: 2.5em 0;
    color: #666;
    letter-spacing: 0.5em;
  }
  
  /* First paragraph styling like NYT */
  p:first-of-type {
    font-size: calc(1.1rem + 0.1vw);
    line-height: 1.7;
  }
  
  /* Footer styling */
  .article-footer {
    margin-top: 3em;
    border-top: 1px solid #e2e2e2;
    padding-top: 1.5em;
    font-size: 0.9em;
    color: #666;
  }
  
  /* Toucan seal styling */
  .seal-image {
    display: block;
    margin: 3em auto 1em;
    width: min(120px, 30vw);
    opacity: 0.9;
  }
  
  /* ───── Header tweaks ─────────────────────────────────────────── */

  /* 1 ■ keep the header short */
  .site-header{
    /* ditch the 56 px minimum height */
    min-height:0;
    /* tighten the top border → header looks slimmer */
    padding:8px 0;
  }

  /* 2 ■ center "Thomas I. Liao" and "Blog" */
  .site-header .wrapper{
    display:flex;
    align-items:baseline;        /* align text baselines */
    justify-content:center;      /* horizontally centered */
  }
  
  /* Style for site title */
  .site-title {
    margin-right: 20px;          /* add some space between title and nav */
  }

  /* 3 ■ let the text define the height, not a 54 px line-height */
  .site-title,
  .site-nav .page-link{
    line-height:1.2;             /* roughly 1 × font-size */
  }

  /* ───── Page-title spacing ────────── */

  /* 4 ■ remove the automatic top margin on the first H1 */
  .wrapper > h1:first-child{
    margin-top:0;
  }
</style>

<!-- NYT Imperial font is loaded via @font-face -->

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

<div class="divider">❖ ❖ ❖</div>

<div class="article-footer">
  <h3>Endnotes</h3>
  <p>Opinions and errors my own. Thanks to <a href="URL">Name</a> for comments.</p>
  
  <h3>Changelog</h3>
  <p>- DATE: Created post</p>
</div>

<img src="/images/toucan_seal_2.png" class="seal-image" alt="Thomas Liao's toucan seal" />

<!-- ─── Wang-tile strip (3-wide) ─────────────────────────────── -->
<style>
  /* layout: article + decorative strip */
  .content-wrapper{
    display:flex;
    gap:2rem;                 /* air between text & strip */
  }

  /* the strip itself */
  #wang-strip{
    flex:0 0 20%;             /* ≈ 20 % of text column */
    max-width:20%;
  }

  /* hide on small screens */
  @media (max-width:999px){
    #wang-strip{display:none;}
  }
</style>

<!-- Wrap entire blog post content -->
<div class="content-wrapper">
  <article>
    {{ content | replace: '<div class="content-wrapper">', '' | replace: '</div><script>' , '</article>

  <!-- canvas is easier than generating 100s of inline <svg> elements -->
  <canvas id="wang-strip"></canvas>
</div>

<script>' }}
  </article>

  <!-- canvas is easier than generating 100s of inline <svg> elements -->
  <canvas id="wang-strip"></canvas>
</div>

<script>
/* ───── 1. Tile definitions ─────────────────────────────────── */

const TILE_SIZE = 64;                 // px
const EDGE_COLOUR = {                 // mapping for quick look-ups
  R: "#c91d1d",
  Y: "#e8b700",
  B: "#4285f4",
  W: "#ffffff"
};

// RIGHT,TOP,LEFT,BOTTOM   (as supplied)
const CODES = [
  "RWWW","RYWY","RWRR","YBYW","YYYB","BBBW",
  "BWRY","YYBY","WYWB","WRRY","RWBW"          // 11 tiles provided
];
// Build an array of tile objects with edge arrays for easy matching
const TILES = CODES.map(code => ({
  code,
  edges: code.split("")                    // [R,T,L,B]
}));

/* ───── 2. Helper – find candidate tiles for a given position ── */

function fits(tile, grid, x, y){
  // check left neighbour
  if (x>0){
    const left = grid[y][x-1];
    if (left && left.edges[0] !== tile.edges[2]) return false;
  }
  // check above neighbour
  if (y>0){
    const above = grid[y-1][x];
    if (above && above.edges[3] !== tile.edges[1]) return false;
  }
  return true;
}

/* ───── 3. Simple backtracking tiler (3-wide, N-tall) ───────── */

function buildStrip(rows){
  const grid = Array.from({length:rows},()=>Array(3).fill(null));

  function place(y=0,x=0){
    if (y===rows) return true;          // done!
    const nextX = (x+1)%3, nextY = nextX? y : y+1;

    // randomise candidate order for variety
    const shuffled = [...TILES].sort(()=>Math.random()-.5);
    for (const tile of shuffled){
      if (fits(tile,grid,x,y)){
        grid[y][x]=tile;
        if (place(nextY,nextX)) return grid;
      }
    }
    grid[y][x]=null;                    // back-track
    return false;
  }
  return place() || grid;               // worst-case returns partial
}

/* ───── 4. Draw a tile onto a canvas ctx at (px,py) ─────────── */

function drawTile(ctx,tile,px,py){
  const s=TILE_SIZE, cX=px+s/2, cY=py+s/2;   // centre
  ctx.lineWidth = 2; ctx.strokeStyle="#000";

  /* top triangle */
  ctx.fillStyle = EDGE_COLOUR[tile.edges[1]];
  ctx.beginPath();
  ctx.moveTo(px,py); ctx.lineTo(px+s,py); ctx.lineTo(cX,cY); ctx.closePath();
  ctx.fill(); ctx.stroke();

  /* right triangle */
  ctx.fillStyle = EDGE_COLOUR[tile.edges[0]];
  ctx.beginPath();
  ctx.moveTo(px+s,py); ctx.lineTo(px+s,py+s); ctx.lineTo(cX,cY); ctx.closePath();
  ctx.fill(); ctx.stroke();

  /* bottom triangle */
  ctx.fillStyle = EDGE_COLOUR[tile.edges[3]];
  ctx.beginPath();
  ctx.moveTo(px,py+s); ctx.lineTo(px+s,py+s); ctx.lineTo(cX,cY); ctx.closePath();
  ctx.fill(); ctx.stroke();

  /* left triangle */
  ctx.fillStyle = EDGE_COLOUR[tile.edges[2]];
  ctx.beginPath();
  ctx.moveTo(px,py); ctx.lineTo(px,py+s); ctx.lineTo(cX,cY); ctx.closePath();
  ctx.fill(); ctx.stroke();
}

/* ───── 5. Assemble & render the strip once DOM is ready ────── */

window.addEventListener("load",()=>{
  const canvas = document.getElementById("wang-strip");
  const rows   = Math.ceil(window.innerHeight / TILE_SIZE) + 1; // overshoot
  canvas.width  = 3 * TILE_SIZE;
  canvas.height = rows * TILE_SIZE;

  const ctx = canvas.getContext("2d");
  const grid = buildStrip(rows);

  grid.forEach((row,y)=>{
    row.forEach((tile,x)=>{
      if (tile) drawTile(ctx,tile,x*TILE_SIZE,y*TILE_SIZE);
    });
  });
});
</script>
