# Slide patterns

Copy-paste HTML for each archetype. Every class used here is already styled in
`deck-template.html` — paste the markup, replace the copy, done. Compose from
different archetypes; a deck where every slide is the same grid reads as filler.

Each slide is one `<section class="slide" data-page="N / TOTAL">` with an
`<div class="inner">` inside. Keep `data-page` correct — the PDF footer reads it.

Pick by intent:

| You want to…                              | Use            |
| ----------------------------------------- | -------------- |
| Open the talk                             | Cover          |
| State a problem beside a concrete example | Two-column     |
| Contrast the wrong vs right question      | Contrast cards |
| List what something gives you             | Value chips    |
| Show two halves of a mechanism            | Two-mechanism  |
| Break a thing into labeled parts          | Role-split     |
| Show a command being run                  | Terminal       |
| Show a pass result beside a fail result   | Report cards   |
| Land the numbers                          | Stat row       |

---

## Cover

The promise. Wordmark, one big claim, a two-line subhead, a few tags.

```html
<section class="slide cover" data-page="1 / 8">
  <div class="inner">
    <div class="wm"><span class="dot">&#10059;</span> Your brand &nbsp;·&nbsp; the occasion</div>
    <h1>The one idea<br />the whole talk<br /><span class="accent">turns on.</span></h1>
    <div class="sub">
      <p>A single line that says what this is and who it is for.</p>
      <p>A second line raising the stakes. Stop there.</p>
    </div>
    <div class="tags">
      <span class="tag accent-tag">the claim</span>
      <span class="tag">a fact</span>
      <span class="tag">a place</span>
    </div>
  </div>
</section>
```

## Two-column

A headline and points on the left, one vivid example on the right. The
workhorse for "here is the problem, here is what it looks like."

```html
<section class="slide" data-page="2 / 8">
  <div class="inner">
    <div class="two">
      <div class="head-block">
        <span class="eyebrow">01 / The problem</span>
        <h2>Name the tension they already feel.</h2>
        <div class="points">
          <div class="point"><span class="n">&#10059;</span><p>One sharp sentence in their words.</p></div>
          <div class="point"><span class="n">&#10059;</span><p>A second that sets up the solution without naming it.</p></div>
        </div>
      </div>
      <div class="callout">
        <div class="top"><span class="badge"></span> A concrete example</div>
        <div class="body">
          <span class="name">example-name</span>
          <p>Specific and real. Vivid beats abstract every time.</p>
          <div class="foot">The one-line takeaway.</div>
        </div>
      </div>
    </div>
  </div>
</section>
```

## Contrast cards

Two cards side by side: the tempting-but-wrong framing (muted) against the right
one (full strength).

```html
<section class="slide" data-page="3 / 8">
  <div class="inner">
    <span class="eyebrow">02 / Reframe</span>
    <h2 style="margin-bottom:.4rem">The question is not the obvious one.</h2>
    <div class="qcontrast">
      <div class="qc muted">
        <span class="who">what people ask</span>
        <div class="q">"Is it the wrong, easy question?"</div>
        <p>Why that framing quietly misleads.</p>
      </div>
      <div class="qc">
        <span class="who">what to ask</span>
        <div class="q">"Here is the question that actually matters."</div>
        <p>Why this one earns a real answer.</p>
      </div>
    </div>
  </div>
</section>
```

## Value chips

A short scannable list of what something gives you. Denser than bullets, lighter
than cards.

```html
<section class="slide" data-page="4 / 8">
  <div class="inner">
    <span class="eyebrow">03 / What you get</span>
    <h2>Everything it puts in your hands.</h2>
    <div class="valuechips">
      <span class="vchip"><span class="d"></span><b>Thing one</b><span>what it does</span></span>
      <span class="vchip"><span class="d"></span><b>Thing two</b><span>what it does</span></span>
      <span class="vchip"><span class="d"></span><b>Thing three</b><span>what it does</span></span>
      <span class="vchip"><span class="d"></span><b>Thing four</b><span>what it does</span></span>
    </div>
  </div>
</section>
```

## Two-mechanism

Two cards explaining the two halves of how something works. Each has a mono
tagline, a heading, a line of prose, and a short list. Close with a `.pull`.

```html
<section class="slide" data-page="5 / 8">
  <div class="inner">
    <span class="eyebrow">04 / How it works</span>
    <h2>Two moves, working together.</h2>
    <div class="mech">
      <div class="card">
        <span class="tagline">&#10059; first move</span>
        <h3>The cheap, fast half.</h3>
        <p>What it does and why it is the default.</p>
        <ul><li>one specific</li><li>another specific</li></ul>
      </div>
      <div class="card">
        <span class="tagline">&#10059; second move</span>
        <h3>The deep, careful half.</h3>
        <p>What it does that the first cannot.</p>
        <ul><li>one specific</li><li>another specific</li></ul>
      </div>
    </div>
    <p class="pull">The sentence you want them repeating afterward.</p>
  </div>
</section>
```

## Role-split

Like two-mechanism but for contrasting two roles or actors (e.g. two models, two
teams, two phases). Reuses `.mech`.

```html
<section class="slide" data-page="6 / 8">
  <div class="inner">
    <span class="eyebrow">05 / Two roles</span>
    <h2>Different jobs, on purpose.</h2>
    <div class="mech">
      <div class="card">
        <span class="tagline">&#10059; the doer</span>
        <h3>Role A</h3>
        <p>What this role is responsible for, and what it is deliberately not.</p>
      </div>
      <div class="card">
        <span class="tagline">&#10059; the checker</span>
        <h3>Role B</h3>
        <p>Why keeping it separate from role A is the whole point.</p>
      </div>
    </div>
  </div>
</section>
```

## Terminal

Show a command actually being run. Monospace, traffic-light bar. Use `.prompt`
`.cmd` `.flag` `.cmt` to color the parts.

```html
<section class="slide" data-page="7 / 8">
  <div class="inner">
    <span class="eyebrow">06 / Run it yourself</span>
    <h2>One line to start.</h2>
    <div class="term">
      <div class="bar"><i class="r"></i><i class="y"></i><i class="g"></i><span>bash</span></div>
      <div class="body">
        <span class="line"><span class="cmt"># install it</span></span>
        <span class="line"><span class="prompt">$</span> <span class="cmd">curl -fsSL https://example.com/install.sh | sh</span></span>
        <span class="line"><span class="prompt">$</span> <span class="cmd">yourtool run</span> <span class="flag">--report</span></span>
      </div>
    </div>
  </div>
</section>
```

## Report cards

A pass result beside a fail result. Score bar, a big number, findings. The most
persuasive slide when you have real output to show.

```html
<section class="slide" data-page="8 / 8">
  <div class="inner">
    <span class="eyebrow">07 / The proof</span>
    <h2>Same tool. Two verdicts.</h2>
    <div class="reports">
      <div class="report pass">
        <div class="rhead"><span class="cmd">good-example</span><span class="badge">PASS</span></div>
        <div class="scorebar"><div class="fill" style="width:95%"></div></div>
        <div class="score"><b>95.1</b><span>/ 100</span></div>
        <ul class="findings ok">
          <li><span class="m">&#10003;</span><span>Clean on every blocking check.</span></li>
          <li><span class="m">&#10003;</span><span>Behaved as described under probing.</span></li>
        </ul>
      </div>
      <div class="report fail">
        <div class="rhead"><span class="cmd">bad-example</span><span class="badge">UNSAFE</span></div>
        <div class="scorebar"><div class="fill" style="width:41%"></div></div>
        <div class="score"><b>40.6</b><span>/ 100</span></div>
        <ul class="findings bad">
          <li><span class="m">&#10007;</span><span><b>The worst finding</b> stated plainly. <span class="loc">file:line</span></span></li>
          <li><span class="m">&#10007;</span><span><b>A second</b> that seals it. <span class="loc">file:line</span></span></li>
        </ul>
      </div>
    </div>
  </div>
</section>
```

## Stat row

Four numbers with labels. A number lands only next to what it is compared to, so
write labels that give the comparison.

```html
<section class="slide" data-page="9 / 9">
  <div class="inner">
    <span class="eyebrow">08 / Where it stands</span>
    <h2>The numbers, plainly.</h2>
    <div class="stat-grid">
      <div class="stat hero"><span class="v">2,719</span><span class="l">artifacts scored</span></div>
      <div class="stat"><span class="v">87<span class="u">%</span></span><span class="l">of the catalog</span></div>
      <div class="stat"><span class="v">43</span><span class="l">static checks</span></div>
      <div class="stat"><span class="v">$56</span><span class="l">total spend</span></div>
    </div>
  </div>
</section>
```
