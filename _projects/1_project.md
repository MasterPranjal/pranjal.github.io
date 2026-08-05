---
layout: page
title: project 1
description: with background image
img: assets/img/12.jpg
importance: 1
category: work
related_publications: true
---
Every project has a beautiful feature showcase page.
It's easy to include images in a flexible 3-column grid format.
Make your photos 1/3, 2/3, or full width.
To give your project a background in the portfolio page, just add the img tag to the front matter like so:
    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    ---
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>
You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>
The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:
{% raw %}
```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```
{% endraw %}

---

## Open Bike Commons — project board

<style>
.obc-kb { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; margin: 2rem 0; }
.obc-kb-header { margin-bottom: 1.25rem; }
.obc-kb-header p { font-size: 0.8rem; color: #666; margin: 0; }
.obc-cols { display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px; }
@media (max-width: 768px) { .obc-cols { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 480px) { .obc-cols { grid-template-columns: 1fr; } }
.obc-col { background: #f7f7f5; border-radius: 10px; padding: 10px; }
.obc-col-head { font-size: 0.7rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.06em; color: #888; margin-bottom: 8px; display: flex; align-items: center; gap: 5px; }
.obc-col-head .dot { width: 6px; height: 6px; border-radius: 50%; display: inline-block; flex-shrink: 0; }
.dot-todo { background: #bbb; }
.dot-doing { background: #f59e0b; }
.dot-done { background: #22c55e; }
.dot-blocked { background: #ef4444; }
.obc-count { background: #e5e5e2; border-radius: 20px; padding: 1px 6px; font-size: 0.65rem; color: #666; }
.obc-card { background: #fff; border: 1px solid #e8e8e5; border-radius: 7px; padding: 9px 11px; margin-bottom: 7px; }
.obc-card:last-child { margin-bottom: 0; }
.obc-card.doing { border-left: 3px solid #f59e0b; }
.obc-card.blocked { border-left: 3px solid #ef4444; opacity: 0.85; }
.obc-card.done { opacity: 0.55; }
.obc-card-title { font-size: 0.78rem; font-weight: 600; color: #1a1a1a; margin: 0 0 3px; line-height: 1.35; }
.obc-card-desc { font-size: 0.72rem; color: #555; margin: 0 0 7px; line-height: 1.45; }
.obc-tags { display: flex; flex-wrap: wrap; gap: 3px; }
.tag { font-size: 0.65rem; padding: 1px 6px; border-radius: 20px; font-weight: 500; }
.tag-urgent { background: #fee2e2; color: #991b1b; }
.tag-tfw    { background: #dbeafe; color: #1e40af; }
.tag-doc    { background: #dcfce7; color: #166534; }
.tag-review { background: #ede9fe; color: #5b21b6; }
.tag-comms  { background: #fef3c7; color: #92400e; }
.obc-legend { margin-top: 1rem; padding-top: 0.75rem; border-top: 1px solid #e8e8e5; display: flex; gap: 14px; flex-wrap: wrap; font-size: 0.72rem; color: #666; }
.obc-legend span { display: flex; align-items: center; gap: 4px; }
</style>

<div class="obc-kb">
  <div class="obc-kb-header">
    <p>Response to Transport for Wales · Aug 2026</p>
  </div>
  <div class="obc-cols">

    <div class="obc-col">
      <div class="obc-col-head"><span class="dot dot-todo"></span> To do <span class="obc-count">3</span></div>
      <div class="obc-card">
        <p class="obc-card-title">Reply to Matthew re: James</p>
        <p class="obc-card-desc">Welcome James (TfW), clarify how he can observe or support the engagement plan.</p>
        <div class="obc-tags"><span class="tag tag-comms">comms</span><span class="tag tag-tfw">TfW</span></div>
      </div>
      <div class="obc-card">
        <p class="obc-card-title">Share Swansea AT consultation</p>
        <p class="obc-card-desc">Deadline 19 Oct. Pass link to community contacts alongside the pilot.</p>
        <div class="obc-tags"><span class="tag tag-tfw">TfW</span></div>
      </div>
      <div class="obc-card">
        <p class="obc-card-title">Update §9 outputs section</p>
        <p class="obc-card-desc">Reference TfW involvement and Active Travel consultation timelines.</p>
        <div class="obc-tags"><span class="tag tag-doc">LaTeX</span></div>
      </div>
    </div>

    <div class="obc-col">
      <div class="obc-col-head"><span class="dot dot-doing"></span> Doing <span class="obc-count">2</span></div>
      <div class="obc-card doing">
        <p class="obc-card-title">Review Matthew's survey questions</p>
        <p class="obc-card-desc">Decide which TfW walking/cycling questions align with pilot research questions.</p>
        <div class="obc-tags"><span class="tag tag-review">review</span><span class="tag tag-tfw">TfW</span></div>
      </div>
      <div class="obc-card doing">
        <p class="obc-card-title">Integrate survey Qs into §7 evaluation</p>
        <p class="obc-card-desc">Add TfW questions to evaluation framework and baseline survey description.</p>
        <div class="obc-tags"><span class="tag tag-doc">LaTeX</span><span class="tag tag-tfw">TfW</span></div>
      </div>
    </div>

    <div class="obc-col">
      <div class="obc-col-head"><span class="dot dot-blocked"></span> Blocked <span class="obc-count">1</span></div>
      <div class="obc-card blocked">
        <p class="obc-card-title">Cardiff AT consultation</p>
        <p class="obc-card-desc">Deadline was 3 Aug — already closed. Confirm whether community contacts engaged in time.</p>
        <div class="obc-tags"><span class="tag tag-urgent">missed deadline</span></div>
      </div>
    </div>

    <div class="obc-col">
      <div class="obc-col-head"><span class="dot dot-done"></span> Done <span class="obc-count">2</span></div>
      <div class="obc-card done">
        <p class="obc-card-title">Draft concept proposal sent</p>
        <p class="obc-card-desc">Sent to Matthew on 10 Jul with challenge statement, evidence gap, evaluation framework.</p>
        <div class="obc-tags"><span class="tag tag-doc">LaTeX</span></div>
      </div>
      <div class="obc-card done">
        <p class="obc-card-title">TfW survey questions received</p>
        <p class="obc-card-desc">Walking/cycling engagement questions received along with intro of James.</p>
        <div class="obc-tags"><span class="tag tag-tfw">TfW</span></div>
      </div>
    </div>

  </div>
  <div class="obc-legend">
    <span><span class="dot dot-todo"></span> To do</span>
    <span><span class="dot dot-doing"></span> In progress</span>
    <span><span class="dot dot-blocked"></span> Blocked</span>
    <span><span class="dot dot-done"></span> Done</span>
  </div>
</div>
