!SLIDE title
You got your typeclass in my jQuery
# Functors

!SLIDE bullets
## me
* @johnbender
* johnbender.us
* github.com/johnbender

!SLIDE center
<img src="adobe.jpg" style="max-height: 600px"></img>

!SLIDE bullets
## projects
* <img src="jquery-logo.png" style="max-height: 100px"></img>
* <img src="vagrant_chilling.png" style="max-height: 250px;"></img>

!SLIDE
# why?
<img src="why.png"></img>

!SLIDE
## patterns
<img src="male-baldness.gif" style="height: 350px;"></img>


!SLIDE
## practical
<img src="digging.gif" style="height: 350px;"></img>

!SLIDE
## fun!

!SLIDE
# disclaimer
<img src="warning.jpg" style="height: 300px;"></img>

!SLIDE
# Haskell's functor

!SLIDE typeclass
<pre>
<span class="keyword">class</span> <span class="type">Functor</span> f <span class="keyword">where</span>
<span class="function-name">fmap</span> <span class="variable-name">::</span> (a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> f a <span class="variable-name">-&gt;</span> f b
</pre>

!SLIDE highlighted-typeclass
<pre>
<b>class Functor f where</b>
<span class="function-name">fmap</span> <span class="variable-name">::</span> (a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> f a <span class="variable-name">-&gt;</span> f b
</pre>

!SLIDE without-declaration
<pre>
<span class="function-name">fmap</span> <span class="variable-name">::</span> (a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> f a <span class="variable-name">-&gt;</span> f b
</pre>

!SLIDE highlighted-args
<pre>
<span class="function-name">fmap</span> <span class="variable-name">::</span> <b>(a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> f a</b> <span class="variable-name">-&gt;</span> f b
</pre>

!SLIDE highlighted-return
<pre>
<span class="function-name">fmap</span> <span class="variable-name">::</span> (a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> f a <span class="variable-name">-&gt;</span> <b>f b</b>
</pre>

!SLIDE highlighted-function-arg
<pre>
<span class="function-name">fmap</span> <span class="variable-name">::</span> <b>(a -&gt; b)</b> <span class="variable-name">-&gt;</span> f a <span class="variable-name">-&gt;</span> f b
</pre>

!SLIDE
<pre>
<span class="function-name">fmap</span> <span class="variable-name">::</span> (a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> <b>f a</b> <span class="variable-name">-&gt;</span> f b
</pre>

!SLIDE
<pre>
<span class="function-name">fmap</span> <span class="variable-name">::</span> (a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> <b>f</b> a <span class="variable-name">-&gt;</span> <b>f</b> b
</pre>

!SLIDE
<pre class="medium">
<span class="function-name">fmap</span> <span class="variable-name">::</span> (a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> functor a <span class="variable-name">-&gt;</span> functor b
</pre>

!SLIDE
<pre class="medium">
<span class="function-name">fmap</span> <span class="variable-name">::</span> (a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> functor(a) <span class="variable-name">-&gt;</span> functor(b)
</pre>

!SLIDE bullets
## simple & general

!SLIDE
<img src="jackie.png"></img>

!SLIDE
# Javascript's functor

!SLIDE
<pre>
<span class="comment">// ( a -> b )
</span><span class="keyword">var</span> <span class="function-name">fromAtoB</span> = <span class="keyword">function</span>(<span class="js2-function-param">a</span>){
  <span class="keyword">var</span> <span class="variable-name">b</span> = a.alter();
  <span class="keyword">return</span> b;
};
</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( a -> b ) -> f a -> f b
</span><span class="keyword">var</span> <span class="variable-name">wrappedB</span> = fmap(fromAtoB, <span class="keyword">new</span> Functor(a));
</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: <b>( a -> b )</b> -> f a -> f b
</span><span class="keyword">var</span> <span class="variable-name">wrappedB</span> = fmap(<b>fromAtoB</b>, <span class="keyword">new</span> Functor(a));
</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( a -> b ) -> <b>f a</b> -> f b
</span><span class="keyword">var</span> <span class="variable-name">wrappedB</span> = fmap(fromAtoB, <b><span class="keyword">new</span> Functor(a)</b>);
</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( a -> b ) -> f a -> <b>f b</b>
</span><span class="keyword">var</span> <b><span class="variable-name">wrappedB</span></b> = fmap(fromAtoB, <span class="keyword">new</span> Functor(a));
</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( a -> b ) -> f a -> f b</span>
<span class="keyword">var</span> <span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAToB</span>, <span class="js2-function-param">wrappedA</span>){
  <span class="keyword">var</span> <span class="variable-name">a</span>, <span class="variable-name">b</span>;

  <span class="comment">// get the value inside the functor object
</span>  a = wrappedA.getInternalValue();

  <span class="comment">// send that value into our function
</span>  b = fromAToB(a);

  <span class="comment">// re-wrap with a functor object and return
</span>  <span class="keyword">return</span> <span class="keyword">new</span> Functor(b);
};</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( a -> b ) -> <b>f a</b> -> f b</span>
<span class="keyword">var</span> <span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAToB</span>, <span class="js2-function-param"><b>wrappedA</b></span>){
  <span class="keyword">var</span> <span class="variable-name">a</span>, <span class="variable-name">b</span>;

  <span class="comment">// get the value inside the functor object
</span>  a = <b>wrappedA</b>.getInternalValue();

  <span class="comment">// send that value into our function
</span>  b = fromAToB(a);

  <span class="comment">// re-wrap with a functor object and return
</span>  <span class="keyword">return</span> <span class="keyword">new</span> Functor(b);
};</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( a -> b ) -> f a -> f b</span>
<span class="keyword">var</span> <span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAToB</span>, <span class="js2-function-param">wrappedA</span>){
  <span class="keyword">var</span> <span class="variable-name">a</span>, <span class="variable-name">b</span>;

  <span class="comment">// get the value inside the functor object
</span>  a = <b>wrappedA.getInternalValue()</b>;

  <span class="comment">// send that value into our function
</span>  b = fromAToB(a);

  <span class="comment">// re-wrap with a functor object and return
</span>  <span class="keyword">return</span> <span class="keyword">new</span> Functor(b);
};</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( a -> b ) -> f a -> f b</span>
<span class="keyword">var</span> <span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAToB</span>, <span class="js2-function-param">wrappedA</span>){
  <span class="keyword">var</span> <span class="variable-name">a</span>, <span class="variable-name">b</span>;

  <span class="comment">// get the value inside the functor object
</span>  <b>a</b> = wrappedA.getInternalValue();

  <span class="comment">// send that value into our function
</span>  b = fromAToB(a);

  <span class="comment">// re-wrap with a functor object and return
</span>  <span class="keyword">return</span> <span class="keyword">new</span> Functor(b);
};</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( <b>a</b> -> b ) -> f a -> f b</span>
<span class="keyword">var</span> <span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAToB</span>, <span class="js2-function-param">wrappedA</span>){
  <span class="keyword">var</span> <span class="variable-name">a</span>, <span class="variable-name">b</span>;

  <span class="comment">// get the value inside the functor object
</span>  a = wrappedA.getInternalValue();

  <span class="comment">// send that value into our function
</span>  b = fromAToB(<b>a</b>);

  <span class="comment">// re-wrap with a functor object and return
</span>  <span class="keyword">return</span> <span class="keyword">new</span> Functor(b);
};</pre>


!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( a -> <b>b</b> ) -> f a -> f b</span>
<span class="keyword">var</span> <span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAToB</span>, <span class="js2-function-param">wrappedA</span>){
  <span class="keyword">var</span> <span class="variable-name">a</span>, <span class="variable-name">b</span>;

  <span class="comment">// get the value inside the functor object
</span>  a = wrappedA.getInternalValue();

  <span class="comment">// send that value into our function
</span>  <b>b</b> = fromAToB(a);

  <span class="comment">// re-wrap with a functor object and return
</span>  <span class="keyword">return</span> <span class="keyword">new</span> Functor(b);
};</pre>

!SLIDE
<pre class="large">
<span class="comment">// fmap :: ( a -> b ) -> f a -> <b>f b</b></span>
<span class="keyword">var</span> <span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAToB</span>, <span class="js2-function-param">wrappedA</span>){
  <span class="keyword">var</span> <span class="variable-name">a</span>, <span class="variable-name">b</span>;

  <span class="comment">// get the value inside the functor object
</span>  a = wrappedA.getInternalValue();

  <span class="comment">// send that value into our function
</span>  b = fromAToB(a);

  <span class="comment">// re-wrap with a functor object and return
</span>  <span class="keyword">return</span> <b><span class="keyword">new</span> Functor(b)</b>;
};</pre>

!SLIDE
<img src="surprised.png"></img>

!SLIDE
# jQuery's functor

!SLIDE
<pre>
<span class="comment">// jQuery :: String -> jQuery(a) </span>
jQuery( <span class="string">"div.selectastic"</span> )
</pre>

!SLIDE
<pre>
<span class="comment">// jQuery :: String -> jQuery(a) </span>
$( <span class="string">"div.selectastic"</span> )
</pre>

!SLIDE
## a :: HTMLElement

!SLIDE
## jQuery ≈ Functor

!SLIDE
<pre class="medium">
$( <span class="string">"div"</span> ).map( <span class="keyword">function</span>( <span class="js2-function-param">i</span>, <span class="js2-function-param">elem</span> ){
  <span class="comment">// elem :: HTMLElement
</span>  <span class="keyword">return</span> elem;
});
</pre>

!SLIDE
<pre class="medium">
$( <span class="string">"div"</span> ).<b>map</b>( <span class="keyword">function</span>( <span class="js2-function-param">i</span>, <span class="js2-function-param">elem</span> ){
  <span class="comment">// elem :: HTMLElement
</span>  <span class="keyword">return</span> elem;
});
</pre>


!SLIDE
<pre class="medium">
<span class="comment">// $.map :: f a -> (a -> b) -> f b</span>
$.map($(<span class="string">"div"</span>), <span class="keyword">function</span>( <span class="js2-function-param">elem</span> ) {
  <span class="comment">// elem :: HTMLElement
</span>  <span class="keyword">return</span> elem;
});</pre>

!SLIDE
<pre class="medium">
<span class="comment">// $.map :: f a -> (a -> b) -> f b</span>
$.<b>map</b>($(<span class="string">"div"</span>), <span class="keyword">function</span>( <span class="js2-function-param">elem</span> ) {
  <span class="comment">// elem :: HTMLElement
</span>  <span class="keyword">return</span> elem;
});</pre>

!SLIDE
<pre class="medium">
<span class="comment">// $.fmap :: f a -> (a -> b) -> f b</span>
$.<b>fmap</b>($(<span class="string">"div"</span>), <span class="keyword">function</span>( <span class="js2-function-param">elem</span> ) {
  <span class="comment">// elem :: HTMLElement
</span>  <span class="keyword">return</span> elem;
});
</pre>

!SLIDE
<pre class="medium">
<span class="function-name">flip</span> fmap <span class="variable-name">::</span> f a <span class="variable-name">-&gt;</span> (a <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> f b</pre>

