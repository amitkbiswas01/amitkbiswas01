<img alt="dog-waiving-hand" src="dog.gif" width="75px" />

<p align="left">
  Hi there! I'm <strong>Amit Biswas</strong>, a
  <em>Trainee Software Engineer</em> at
  <a href="https://www.welldev.io/">WellDev Bangladesh Ltd</a>, primarily
  working with <strong>JavaScript</strong> and <strong>PHP</strong>, with a keen
  interest in
  <strong>Distributed Systems, Systems Design, and Cloud Computing</strong>.
  Although skeptical about humans and machines alike, I'm enthusiastic about
  collaborating and working on ideas that have real impacts!
</p>
<div align="center">
  <a href="https://www.linkedin.com/in/amitkbiswas01/">
    <img src="https://img.shields.io/badge/-Amit_Biswas-blue?style=for-the-badge&logo=Linkedin&logoColor=white" />
  </a>
  <a href="mailto:amitkbiswas01@gmail.com">
    <img
      src="https://img.shields.io/badge/-amitkbiswas01@gmail.com-c14438?style=for-the-badge&logo=Gmail&logoColor=white" />
  </a>
  <a href="https://twitter.com/amitb__b">
    <img src="https://img.shields.io/badge/-amitb__b-blue?style=for-the-badge&logo=twitter&logoColor=white" />
  </a>
</div>

## **Blog posts**

<!-- BLOG-POST-LIST:START -->**October 28, 2021** - [পিএইচপিতে ডিপেন্ডেন্সি ইঞ্জেকশন প্যাটার্ণ](https://dev.to/amitkbiswas01/pieicpite-ddipenddensi-inyjekshn-pyaattaarnn-4ec2): <p>কিছুদিন আগে একটা দ্রুপাল প্রজেক্টে কোডবেস মেইনটেইনেন্স এর কাজ করতে গিয়ে ওদের ডকে একটা সাজেশন পাই, যেখানে বলা হয়েছে দ্রুপাল ৮ থেকে দ্রুপালের ইন্টারনাল সার্ভিসগুলো এক্সেস করার "বেটার" উপায় হলো ডিপেন্ডেন্সি ইঞ্জেকশন। যদিও আমি এই অবজেক্ট ওরিয়েন্টেড প্যাটার্ণটার নামে আগে শুনেছিলাম, কিন্তু বাকিসবের মতই কখনো ঘেঁটে দেখা হয়নি! ব্যাপারটা একটু ইন্টারেস্টিং মনে হওয়ার ভাবলাম অফিসে আমার পরবর্তী নলেজ সেশনটা এটার উপরেই করবো এবং তারই ফলশ্রুতিতে এই পোস্ট।</p>

<p><strong>ডিপেন্ডেন্সি ইঞ্জেকশন</strong> সফটওয়্যার ইঞ্জিনিয়ারিং এর খুবই গুরুত্বপূর্ণ একটি কনসেপ্টের উপরে তৈরি করা প্যাটার্ন, আর সেটা হলো মডুলারিটি। কোডকে যতটা সম্ভব (এবং যতটা উচিত) মডুলার রাখা, যাতে সেটাকে সহজেই বিভিন্ন প্রোগ্রামে ব্যবহার করা যায়, ওই প্রোগ্রামগুলোকে তেমন পরিবর্তন না করেই। ব্যাখ্যা শুরু করার আগে কিছু সংজ্ঞা দেয়া প্রয়োজন, পরে এগুলো বারবারই লেখার মধ্যে আসতে থাকবে।</p>

<ul>
<li><p><strong>সার্ভিস</strong>: যে ফাংশনালিটিটা আমরা ব্যবহার করবো। সেটা যেকোনো ধরনের কমন কাজই হতে পারে, যা কোডবেসের বিভিন্ন জায়গা থেকে প্রয়োজনমাফিক বারবার ব্যবহার করা যাবে। যেমন, অথেনটিকেশন। প্রজেক্টের অনেক জায়গাতেই হয়তো ইউজারের অথেন্টিসিটি চেক করতে হবে, যে সে আসলেই আমাদের ইউজার কিনা। আর সেই কাজটাই করবে অথেনটিকেশন সার্ভিস।</p></li>
<li><p><strong>ক্লায়েন্ট</strong>: ক্লায়েন্ট হলো সেই ব্যক্তি যে রাত ২টার সময় মেইল দিয়ে ফন্টের সাইজ চেঞ্জ করতে বলে! জোকস এপার্ট, ক্লায়েন্ট হচ্ছে যেকোনো এনটিটি যা সার্ভিসকে ব্যবহার করে। যেমন, অথেনটিকেশন যদি আমাদের সার্ভিস হয় তাহলে লগইন সিস্টেমটা একটি ক্লায়েন্ট, যে অথেনটিকেশন সার্ভিসকে ব্যবহার করে ইউজারকে লগইন করায়।</p></li>
<li><p><strong>ইন্টারফেস</strong>: ইন্টারফেস এর সাথে আমরা সবাই মোটামুটি পরিচিত। এটি ডিফাইন করে কিভাবে আমাদের সার্ভিসটা তৈরি করা হবে, অনেকটা বিল্ডিং বানানোর ব্লুপ্রিন্টের মত। অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং এ ইন্টারফেস ঠিক করে দেয় ওই ইন্টারফেসকে ইমপ্লিমেন্ট করা সব ক্লাসে কি কি মেথড থাকা লাগবে। ফলে ক্লায়েন্ট ইন্টারফেসকে দেখে সহজেই বুঝতে পারে তাকে ইমপ্লিমেন্ট করা সার্ভিসগুলো কেমন হবে।</p></li>
<li><p><strong>ইঞ্জেকটর</strong>: ইঞ্জেকটর এর নাম আর কাজ একই, এটি সার্ভিসকে ক্লায়েন্টে ইঞ্জেক্ট করে। সিরিঞ্জ দিয়ে শরীরে ইনজেকশন নেবার উদাহরণটা যদি আমরা ভাবি, এখানে ক্লায়েন্ট হচ্ছে রোগী, মেডিসিন হচ্ছে সার্ভিস আর সিরিঞ্জ হচ্ছে ইঞ্জেকটর!</p></li>
</ul>

<p>আচ্ছা এবার তাহলে শুরু করা যাক।</p>

<h3>
  <a href="#%E0%A6%95%E0%A6%BF">
  </a>
  কি?
</h3>

<p><strong>ডিপেন্ডেন্সি ইঞ্জেকশন</strong> হচ্ছে এমন একটা টেকনিক যার মাধ্যমে আমরা কোনো একটা অবজেক্ট বা এনটিটিকে তার উপরে ডিপেন্ডেন্ট বা নির্ভরশীল কোনো অবজেক্টের কাছে পৌঁছে দেই। ধরা যাক , অবজেক্ট A, অবজেক্ট B এর ডিপেন্ডেন্সি । মানে অবজেক্ট B কে নিজের কাজ ভালোমত শেষ করতে অবজেক্ট A এর কোনো ফাংশনালিটি ব্যবহার করতে হবে। B , A এর উপরে ডিপেনডেন্ট। ডিপেন্ডেন্সি ইঞ্জেকশনের মাধ্যমে আমরা এই সম্পর্কটা এমনভাবে তৈরি করতে পারি যাতে A এর ইমপ্লিমেন্টেশনে কোনো পরিবর্তন আসলে B তে নূন্যতম পরিবর্তন করা লাগে আর A কে স্বাধীনভাবে অন্য অবজেক্টেও ইনজেক্ট করা যায়। সোজা কথায়, কোনো অবজেক্টের যত ডিপেন্ডেন্সি আছে তাদেরকে ওই অবজেক্টের সাথে এমনভাবে যুক্ত করা, যাতে অবজেক্ট বা ডিপেন্ডেন্ট এনটিটির সবচেয়ে কম চেঞ্জ হয়। এই টেকনিকটি <a href="https://en.wikipedia.org/wiki/Inversion_of_control">ইনভার্শন অফ কন্ট্রোল</a> প্রিন্সিপালের উপরে তৈরি করা। <a href="https://en.wikipedia.org/wiki/Dependency_injection">উইকিপিডিয়ার ভাষ্যমতে</a>,</p>

<blockquote>
<p>In software engineering, dependency injection is a technique in which an object receives other objects that it depends on, called dependencies.</p>
</blockquote>

<p>একটা ঊদাহরণ যদি দেখতে চাই, শুরু করা যাক ডিপেন্ডেন্সি ইঞ্জেকশন ছাড়া কিভাবে আমরা ইঞ্জিন গাড়িতে বসাতে পারি!<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight php"><code><span class="kd">interface</span> <span class="nc">BaseEngine</span> <span class="p">{</span>
  <span class="k">public</span> <span class="k">function</span> <span class="n">showSpeed</span><span class="p">():</span> <span class="kt">void</span><span class="p">;</span>
<span class="p">}</span>

<span class="kd">class</span> <span class="nc">SportsCarEngine</span> <span class="kd">implements</span> <span class="nc">BaseEngine</span> <span class="p">{</span>

  <span class="k">public</span> <span class="k">function</span> <span class="n">showSpeed</span><span class="p">():</span> <span class="kt">void</span> <span class="p">{</span>
    <span class="k">echo</span> <span class="s2">"0-60 in 5 seconds!"</span><span class="p">;</span>
  <span class="p">}</span>
<span class="p">}</span>

<span class="kd">class</span> <span class="nc">EconomyCarEngine</span> <span class="kd">implements</span> <span class="nc">BaseEngine</span> <span class="p">{</span>

  <span class="k">public</span> <span class="k">function</span> <span class="n">showSpeed</span><span class="p">():</span> <span class="kt">void</span> <span class="p">{</span>
    <span class="k">echo</span> <span class="s2">"0-60 in 1 minute!"</span><span class="p">;</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>

</div>



<p>এখানে <code>BaseEngine</code> নামে আমাদের একটি ইন্টারফেস আছে, যেটা ঠিক করে দিয়েছে <code>showSpeed()</code> ফাংশনটা সব ইঞ্জিনের ইমপ্লইমেন্টেশনেই থাকবে। দুই ধরনের ইঞ্জিন আছে, <code>SportsCarEngine</code> এবং <code>EconomyCarEngine</code>। এখন আমরা যদি একটা <code>Car</code> ক্লাস বানাতে যাই, আমরা কন্সট্রাকটরের মধ্যেই ঠিক করে দিতে পারি কোন ইঞ্জিন আমরা ব্যবহার করবো এবং সেই অনুযায়ী <code>carDetails()</code> ফাংশনটা আউটপুট দেখাবে।<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight php"><code><span class="kd">class</span> <span class="nc">Car</span> <span class="p">{</span>

  <span class="k">public</span> <span class="nv">$engine</span><span class="p">;</span>

  <span class="k">public</span> <span class="k">function</span> <span class="n">__construct</span><span class="p">()</span> <span class="p">{</span>
    <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">engine</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">SportsCarEngine</span><span class="p">();</span>
  <span class="p">}</span>

  <span class="k">public</span> <span class="k">function</span> <span class="n">carDetails</span><span class="p">()</span> <span class="p">{</span>
    <span class="k">echo</span> <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">engine</span><span class="o">-&gt;</span><span class="nf">showSpeed</span><span class="p">();</span>
  <span class="p">}</span>
<span class="p">}</span>
<span class="nv">$myCar</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">Car</span><span class="p">();</span>
<span class="nv">$myCar</span><span class="o">-&gt;</span><span class="nf">carDetails</span><span class="p">();</span> <span class="c1">// 0-60 in 5 seconds!</span>
</code></pre>

</div>



<p>কিন্তু এখানে সমস্যাটা যেটা দেখা যাচ্ছে তা হলো <code>SportsCarEngine</code> এর ইন্সট্যানসিয়েশন এ। কন্সট্রাকটরের মধ্যে আমরা টাইট কাপলিং করে দিয়েছি, ফলে প্রতিবারই <code>Car</code> ক্লাস ইন্সট্যানসিয়েট করলে <code>SportsCarEngine</code>ওয়ালা <code>Car</code>ই তৈরি হবে। বাইরে থেকে এটা কন্ট্রোল করার উপায় নেই। আচ্ছা আমরা যদি কন্সট্রাকটরে কি ইঞ্জিন সেটা পাস করি, তাহলে?<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight php"><code><span class="k">public</span> <span class="k">function</span> <span class="n">__construct</span><span class="p">(</span><span class="kt">EconomyCarEngine</span> <span class="nv">$engine</span><span class="p">)</span> <span class="p">{</span>
  <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">engine</span> <span class="o">=</span> <span class="nv">$engine</span><span class="p">;</span>
<span class="p">}</span>
<span class="mf">.</span>
<span class="mf">.</span>
<span class="nv">$engine</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">EconomyCarEngine</span><span class="p">();</span>
<span class="nv">$my_car</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">Car</span><span class="p">(</span><span class="nv">$engine</span><span class="p">);</span>
<span class="nv">$my_car</span><span class="o">-&gt;</span><span class="nf">carDetails</span><span class="p">();</span> <span class="c1">// 0-60 in 1 minute!</span>
</code></pre>

</div>



<p>এটাও কাজ করবে। এবং আমরা বাইরে থেকে কন্ট্রোল করতে পারছি কি ইঞ্জিন লাগবে। তাহলে কি ডিপেন্ডেন্সি ইঞ্জেকশন ছাড়াই আমরা কোডের কোয়ালিটি ইম্প্রুভ করে ফেলেছি? আসলে না! এটাও একধরনের ডিপেন্ডেন্সি ইনজেকশন। কিন্তু এখানে আপাতদৃষ্টিতে কোড কিছুটা মডুলার লাগলেও কন্সট্রাকটরে কিন্তু এখনো আমাদেরকে কোন টাইপের ইঞ্জিন আমরা এক্সপেক্ট করছি সেটা বলে দিতে হচ্ছে। ফলে আমরা <code>EconomyCarEngine</code> এর বদলে <code>SportsCarEngine</code> পাস করলে এটা ফেইল করবে। এটার সমাধান হিসাবে আমরা <code>BaseEngine</code> ইন্টারফেসকে দিতে পারি প্যারামিটারে, তাহলে ওই ইন্টারফেসের যেকোনো ইমপ্লিমেন্টেশনই আমরা আর্গুমেন্টে পাস করতে পারবো।<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight php"><code><span class="k">public</span> <span class="k">function</span> <span class="n">__construct</span><span class="p">(</span><span class="kt">BaseEngine</span> <span class="nv">$engine</span><span class="p">)</span> <span class="p">{</span>
  <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">engine</span> <span class="o">=</span> <span class="nv">$engine</span><span class="p">;</span>
<span class="p">}</span>
<span class="mf">.</span>
<span class="mf">.</span>
<span class="nv">$engine</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">EconomyCarEngine</span><span class="p">();</span>
<span class="nv">$my_car</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">Car</span><span class="p">(</span><span class="nv">$engine</span><span class="p">);</span>
<span class="nv">$my_car</span><span class="o">-&gt;</span><span class="nf">carDetails</span><span class="p">();</span> <span class="c1">// 0-60 in 1 minute!</span>
</code></pre>

</div>



<p>এখন কিন্তু আমরা যেকোনো টাইপের ইঞ্জিন পাস করতে পারবো আমাদের কন্সট্রাকটরে, যদি সেটা <code>BaseEngine</code> কে ইমপ্লিমেন্ট করে। ফলে ক্লাস আরো মডুলার হয়ে গেলো, যেহেতু প্রতিবার ইঞ্জিনের ইমপ্লিমেন্টেশন চেঞ্জ হলে কন্সট্রাকটরে চেঞ্জ করা লাগছে না।</p>

<h3>
  <a href="#%E0%A6%95%E0%A7%9F%E0%A6%AD%E0%A6%BE%E0%A6%AC%E0%A7%87">
  </a>
  কয়ভাবে?
</h3>

<p>তিনটা উপায়ে সাধারণত ডিপেন্ডেন্সি ইঞ্জেক্ট করা হয়ে থাকে।<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight php"><code><span class="cd">/**
 * Constructor Injection
 */</span>
<span class="k">public</span> <span class="k">function</span> <span class="n">__construct</span><span class="p">(</span><span class="kt">EconomyCarEngine</span> <span class="nv">$engine</span><span class="p">)</span> <span class="p">{</span>
  <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">engine</span> <span class="o">=</span> <span class="nv">$engine</span><span class="p">;</span>
<span class="p">}</span>
<span class="mf">.</span>
<span class="mf">.</span>
<span class="nv">$engine</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">EconomyCarEngine</span><span class="p">();</span>
<span class="nv">$my_car</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">Car</span><span class="p">(</span><span class="nv">$engine</span><span class="p">);</span>
</code></pre>

</div>





<div class="highlight js-code-highlight">
<pre class="highlight php"><code><span class="cd">/**
 * Setter Injection
 */</span>
<span class="k">public</span> <span class="k">function</span> <span class="n">setEngine</span><span class="p">(</span><span class="kt">EconomyCarEngine</span> <span class="nv">$engine</span><span class="p">)</span> <span class="p">{</span>
  <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">engine</span> <span class="o">=</span> <span class="nv">$engine</span><span class="p">;</span>
<span class="p">}</span>
<span class="mf">.</span>
<span class="mf">.</span>
<span class="nv">$engine</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">EconomyCarEngine</span><span class="p">();</span>
<span class="nv">$my_car</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">Car</span><span class="p">();</span>
<span class="nv">$my_car</span><span class="o">-&gt;</span><span class="nf">setEngine</span><span class="p">(</span><span class="nv">$engine</span><span class="p">);</span>
</code></pre>

</div>





<div class="highlight js-code-highlight">
<pre class="highlight php"><code><span class="cd">/**
 * Interface Injection
 */</span>
<span class="k">public</span> <span class="k">function</span> <span class="n">__construct</span><span class="p">(</span><span class="kt">BaseEngine</span> <span class="nv">$engine</span><span class="p">)</span> <span class="p">{</span>
  <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">engine</span> <span class="o">=</span> <span class="nv">$engine</span><span class="p">;</span>
<span class="p">}</span>
<span class="mf">.</span>
<span class="mf">.</span>
<span class="nv">$engine</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">EconomyCarEngine</span><span class="p">();</span>
<span class="nv">$my_car</span> <span class="o">=</span> <span class="k">new</span> <span class="nc">Car</span><span class="p">(</span><span class="nv">$engine</span><span class="p">);</span>
</code></pre>

</div>



<h3>
  <a href="#%E0%A6%95%E0%A7%87%E0%A6%A8%E0%A7%8B">
  </a>
  কেনো?
</h3>

<p>ডিপেন্ডেন্সি ইঞ্জেকশনে বলা হয় কোনো এনটিটিকে (ক্লাস/অবজেক্ট) কোনো সার্ভিসের লো-লেভেল ইমপ্লিমেন্টেশনের উপরে ডিপেন্ডেন্ট হওয়া উচিত না, বরং সেই সার্ভিসের অ্যাবস্ট্রাকশনের উপরে ডিপেন্ড করা উচিত। ফলে এটা ক্লায়েন্টকে অনেক ফ্লেক্সিবিলিটি দেয়। ক্লায়েন্ট যেহেতু সরাসরি সার্ভিস না, বরং সার্ভিসের অ্যাবস্ট্রাকশনের/ইন্টারফেসের উপরে ডিপেন্ডেন্ট, তাই সার্ভিসের ইমপ্লিমেন্টেশন পরিবর্তন হলেও ক্লায়েন্ট পার্সপেক্টিভ থেকে তেমন কিছুই চেঞ্জ হয়না। ফলে একবার ক্লায়েন্টে কি লাগবে তা ঠিক করা হয়ে গেলে, সেটা সার্ভিস কিভাবে দিচ্ছে সেটা নিয়ে আর মাথা ঘামানোর প্রয়োজন পরে না। এতে করে যেমন সার্ভিস এবং ক্লায়েন্টকে আলাদা ভাবে টেস্ট করে দেখা যায়, তেমনি পরবর্তীতে লজিক্যাল চেঞ্জগুলোও সহজে হ্যান্ডেল করা যায়, যেটা কোডের এক্সটেন্সিবিলিটি বাড়িয়ে দেয় আর <a href="https://stackoverflow.com/q/2832017">টাইট কাপলিং</a> কমায়। এছাড়া ক্লায়েন্ট রিকোয়ারমেন্ট ফিক্সড বলে একই ক্লায়েন্ট এর জন্য সমসাময়িকভাবে অনেকগুলো সার্ভিসের কাজ করা যায়, যা টিমের প্রোডাক্টিভিটি ও বাড়ায়।</p>

<h3>
  <a href="#%E0%A6%95%E0%A7%87%E0%A6%A8%E0%A7%8B-%E0%A6%A8%E0%A6%BE">
  </a>
  কেনো না?
</h3>

<p>ডিপেন্ডেন্সি ইঞ্জেকশন যে একটা ফুলপ্রুফ টেকনিক তাও না। অনেকসময় দেখা যায় এই প্যাটার্নের কারণে কোডবেসের ডিজাইন কিছুটা কমপ্লেক্স হয়ে যায় এবং সার্ভিসের কোন ইমপ্লিমেন্টেশন কখন ইঞ্জেক্ট করা লাগবে তা বোঝা যায়না। আবার আমরা যেহেতু ইন্টারফেস ইঞ্জেক্ট করছি, ইমপ্লিমেন্টেশন এর বদলে, অনেক এরর রানটাইমে গিয়ে ধরা পরে, যেখানে সেটা কম্পাইল টাইমে ধরা পড়ার কথা ছিল।</p>

<h3>
  <a href="#%E0%A6%A6%E0%A7%8D%E0%A6%B0%E0%A7%81%E0%A6%AA%E0%A6%BE%E0%A6%B2%E0%A7%87-%E0%A6%A1%E0%A6%BF%E0%A6%AA%E0%A7%87%E0%A6%A8%E0%A7%8D%E0%A6%A1%E0%A7%87%E0%A6%A8%E0%A7%8D%E0%A6%B8%E0%A6%BF-%E0%A6%87%E0%A6%9E%E0%A7%8D%E0%A6%9C%E0%A7%87%E0%A6%95%E0%A6%B6%E0%A6%A8">
  </a>
  দ্রুপালে ডিপেন্ডেন্সি ইঞ্জেকশন
</h3>

<p>সহজে রিপিটেটিভ কাজগুলো করার জন্য দ্রুপাল এপিআই বিভিন্ন সার্ভিস দিয়ে থাকে। ফাইল ম্যানেজ করা থেকে ডাটাবেস হ্যান্ডেল করা, সব কাজের জন্যই এখানে সার্ভিস আছে। ফলে আমরা ক্লাস বা ফাংশনের মধ্যে <code>\Drupal::service(service_name)</code> এর মাধ্যমে যেকোনো সার্ভিস এক্সেস করতে পারি। যেমন, আমাদের যদি কোনো টাইপের সব এনটিটির দরকার হয় আমরা সেটা পেতে পারি এভাবে,<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight php"><code><span class="kd">class</span> <span class="nc">DemoEntityUser</span> <span class="p">{</span>

  <span class="k">public</span> <span class="nv">$entities</span><span class="p">;</span>

  <span class="k">public</span> <span class="k">function</span> <span class="n">__construct</span><span class="p">()</span> <span class="p">{}</span>

  <span class="k">public</span> <span class="k">function</span> <span class="n">generateEntities</span><span class="p">()</span> <span class="p">{</span>
    <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">entities</span> <span class="o">=</span> <span class="err">\</span><span class="nc">Drupal</span><span class="o">::</span><span class="nf">service</span><span class="p">(</span><span class="s1">'entity_type.manager'</span><span class="p">)</span><span class="o">-&gt;</span><span class="nf">getStorage</span><span class="p">(</span><span class="nv">$entity_type</span><span class="p">)</span><span class="o">-&gt;</span><span class="nf">loadMultiple</span><span class="p">(</span><span class="nv">$ids</span><span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>

</div>



<p>কিন্তু দ্রুপাল বলে এভাবে গ্লোবাল সার্ভিস প্রোভাইডারকে এক্সেস না করে আমাদের আর্গুমেন্টে সার্ভিসগুলোকে পাস করতে। এতে করে যেমন কোডের মডুলারিটি বাড়ে, তেমনি রিডেবিলিটি ও ইম্প্রুভ হয়।<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight php"><code><span class="kd">class</span> <span class="nc">DemoEntityUser</span> <span class="p">{</span>

  <span class="k">public</span> <span class="nv">$entity_type_manager</span><span class="p">;</span>
  <span class="k">public</span> <span class="nv">$entities</span><span class="p">;</span>

  <span class="k">public</span> <span class="k">function</span> <span class="n">__construct</span><span class="p">(</span><span class="kt">EntityTypeManagerInterface</span> <span class="nv">$entity_type_manager_interface</span><span class="p">)</span> <span class="p">{</span>
    <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">entity_type_manager</span> <span class="o">=</span> <span class="nv">$entity_type_manager_interface</span><span class="p">;</span>
  <span class="p">}</span>

  <span class="k">public</span> <span class="k">function</span> <span class="n">generateEntities</span><span class="p">()</span> <span class="p">{</span>
    <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">entities</span> <span class="o">=</span> <span class="nv">$this</span><span class="o">-&gt;</span><span class="n">entity_type_manager</span><span class="o">-&gt;</span><span class="nf">getStorage</span><span class="p">(</span><span class="nv">$entity_type</span><span class="p">)</span><span class="o">-&gt;</span><span class="nf">loadMultiple</span><span class="p">(</span><span class="nv">$ids</span><span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>

</div>



<h3>
  <a href="#%E0%A6%B6%E0%A7%87%E0%A6%B7%E0%A6%95%E0%A6%A5%E0%A6%BE">
  </a>
  শেষকথা
</h3>

<p>অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং এ অবজেক্টের ডিপেন্ডেন্সি এবং ডাটা আদানপ্রদানকে এফিসিয়েন্ট করার জন্য যেসব প্যাটার্ণ আছে, এগুলোর মধ্যে ডিপেডেন্সি ইঞ্জেকশন অন্যতম সহজ কিন্তু ইউজফুল একটা প্যারাডাইম । আমি নিজেও এইসব ডিজাইন প্যাটার্ণ নিয়ে নতুন পড়াশুনা করছি, তথ্য-উপাত্তে বা পুরো কনসেপ্টেই ভুল থাকতে পারে! তাই কোনো মতামত থাকলে অবশ্যই জানাবেন। পরে ডিজাইন প্যাটার্ণ বা অন্যকিছু নিয়ে লেখা দেখতে চাইলে সেটাও জানাবেন। এদ্দুর পড়ার জন্য ধন্যবাদ।</p>

 
<!-- BLOG-POST-LIST:END -->

## **Tech Experiences**

<table>
  <tbody>
    <tr>
      <td align="center"> <h4>CURRENTLY USING</h4> </td>
      <td align="center">
        <img src="https://img.shields.io/badge/PHP7+-777BB4?style=for-the-badge&logo=php&logoColor=white" />
        <img alt="Javascript"
          src="https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E" />
        <img alt="Vue"
          src="https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D" />
        <img alt="Drupal"
          src="https://img.shields.io/badge/Drupal-0678BE?style=for-the-badge&logo=drupal&logoColor=white" />
        <img alt="MySQL"
          src="https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&color=42759C&logo=mysql&logoColor=white" />
        <img
          src="https://img.shields.io/badge/platform.sh-FFFFFF?style=for-the-badge&color=black&logo=Platform.sh&logoColor=which" />
      </td>
    </tr>
    <tr>
      <td align="center"> <h4>FAMILIAR WITH</h4> </td>
      <td align="center">
        <img alt="Python"
          src="https://img.shields.io/badge/Python-356C9B?style=for-the-badge&logo=python&logoColor=white" />
        <img alt="Django"
          src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=green" />
        <img alt="React"
          src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" />
        <img alt="TailwindCSS"
          src="https://img.shields.io/badge/TailwindCSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" />
        <img alt="PostgreSQL"
          src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" />
        <img alt="MongoDB"
          src="https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white" />
        <img alt="Azure"
          src="https://img.shields.io/badge/microsoft%20azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white" />
      </td>
    </tr>
    <tr>
      <td align="center"> <h4>OTHER TOOLS</h4> </td>
      <td align="center">
        <img alt="Docker"
          src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white" />
        <img alt="Ubuntu"
          src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" />
        <img alt="Git" src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" />
        <img alt="VS code"
          src="https://img.shields.io/badge/Visual_Studio_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white" />
        <img alt="oh my zsh"
          src="https://img.shields.io/badge/oh_my_zsh-1A2C34?style=for-the-badge&logo=ohmyzsh&logoColor=white" />
      </td>
    </tr>
  </tbody>
</table>

<hr />

<div align="center">
  <a href="https://github.com/anuraghazra/github-readme-stats">
    <img alt="stat" align="center" height="175" width="auto"
      src="https://github-readme-stats.vercel.app/api/top-langs/?username=amitkbiswas01&hide=html,css&exclude_repo=ocr-cnn,covid19-detection-xray,course-projects&theme=dracula&layout=compact" />
  </a>
  <a href="https://github.com/anuraghazra/github-readme-stats">
    <img alt="lang" align="center" height="175" width="auto"
      src="https://github-readme-stats.vercel.app/api?username=amitkbiswas01&count_private=true&theme=dracula&show_icons=true&custom_title=Amit's GitHub Stats" />
  </a>
</div>
