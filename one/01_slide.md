!SLIDE title bullets
### You got your typeclass in my jQuery
# Functors
johnbender.github.com/presentation-jsfunctors/

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

!SLIDE
## patterns
<img src="male-baldness.gif" style="height: 350px;"></img>

!SLIDE
## practical
<img src="digging.gif" style="height: 350px;"></img>

!SLIDE
## tricks
<img src="feynman.jpg" style="height: 350px"></img>

!SLIDE
# disclaimer
<img src="warning.jpg" style="height: 300px;"></img>

!SLIDE
# haskell functor

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

!SLIDE
<pre class="medium">
<span class="function-name">fmap</span> <span class="variable-name">::</span> (<b>a</b> <span class="variable-name">-&gt;</span> b) <span class="variable-name">-&gt;</span> functor(<b>a</b>) <span class="variable-name">-&gt;</span> functor(b)
</pre>

!SLIDE
<pre class="medium">
<span class="function-name">fmap</span> <span class="variable-name">::</span> (a <span class="variable-name">-&gt;</span> <b>b</b>) <span class="variable-name">-&gt;</span> functor(a) <span class="variable-name">-&gt;</span> functor(<b>b</b>)
</pre>

!SLIDE bullets
## simple & general

!SLIDE
<img src="questionmark.png"></img>

!SLIDE
# javascript functor

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
<img src="questionmark.png"></img>

!SLIDE
# jQuery's functor

!SLIDE
<pre>
<span class="comment">// jQuery :: String -> jQuery(a) </span>
jQuery( <span class="string">"div.selectorific"</span> )
</pre>

!SLIDE
<pre>
<span class="comment">// jQuery :: String -> jQuery(<b>a</b>) </span>
jQuery( <span class="string">"div.selectorific"</span> )
</pre>

!SLIDE
## jQuery ≈ Functor

!SLIDE
## a :: HTMLElement

!SLIDE
## fmap?

!SLIDE
<pre class="medium">
<span class="comment">// rewraps altered HTMLElements for chaining</span>
$( <span class="string">"div"</span> ).map( <span class="keyword">function</span>( <span class="js2-function-param">i</span>, <span class="js2-function-param">elem</span> ){
  <span class="comment">// elem :: HTMLElement
</span>  <span class="keyword">return</span> elem;
});
</pre>

!SLIDE
<pre class="medium">
<span class="comment">// rewraps altered HTMLElements for chaining</span>
$( <span class="string">"div"</span> ).<b>map</b>( <span class="keyword">function</span>( <span class="js2-function-param">i</span>, <span class="js2-function-param">elem</span> ){
  <span class="comment">// elem :: HTMLElement
</span>  <span class="keyword">return</span> elem;
});
</pre>

!SLIDE
<pre class="medium">
<span class="comment">// rewraps altered HTMLElements for chaining</span>
$( <span class="string">"div"</span> ).map( <span class="keyword">function</span>( <span class="js2-function-param">i</span>, <span class="js2-function-param">elem</span> ){
  <span class="comment">// elem :: <b>HTMLElement</b>
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
<span class="comment">// $.fmap :: <b>f a -> (a -> b) -> f b</b></span>
$.fmap($(<span class="string">"div"</span>), <span class="keyword">function</span>( <span class="js2-function-param">elem</span> ) {
  <span class="comment">// elem :: HTMLElement
</span>  <span class="keyword">return</span> elem;
});
</pre>

!SLIDE
## everyday

!SLIDE
<img src="questionmark.png"></img>

!SLIDE
# hidden functor
<img src="hidden_dragon.jpg" style="height: 390px;"></img>

!SLIDE
## coworker
<img src="hipster.jpg"></img>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="function-name">HiddenFunctor</span> = <span class="keyword">function</span>(<span class="js2-function-param">a</span>){
  <span class="keyword">var</span> <span class="variable-name"><span class="js2-warning">a</span></span> = a, <span class="variable-name">self</span> = <span class="builtin">this</span>;

  self.<span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAtoB</span>){
    <span class="keyword">var</span> <span class="variable-name">b</span>;

    <span class="comment">// if a is visible skip the action
</span>    b = a.is(<span class="string">":visible"</span>) ? a : fromAtoB(a);

    <span class="comment">// re-wrap
</span>    <span class="keyword">return</span> <span class="keyword">new</span> self.constructor(b);
  };

  self.<span class="function-name">hide</span> = <span class="keyword">function</span>(){
    a.hide();
    <span class="keyword">return</span> self;
  };
};
</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="function-name">HiddenFunctor</span> = <span class="keyword">function</span>(<span class="js2-function-param"><b>a</b></span>){
  <span class="keyword">var</span> <span class="variable-name"><b><span class="js2-warning">a</span></span> = a</b>, <span class="variable-name">self</span> = <span class="builtin">this</span>;

  self.<span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAtoB</span>){
    <span class="keyword">var</span> <span class="variable-name">b</span>;

    <span class="comment">// if a is visible skip the action
</span>    b = a.is(<span class="string">":visible"</span>) ? a : fromAtoB(a);

    <span class="comment">// re-wrap
</span>    <span class="keyword">return</span> <span class="keyword">new</span> self.constructor(b);
  };

  self.<span class="function-name">hide</span> = <span class="keyword">function</span>(){
    a.hide();
    <span class="keyword">return</span> self;
  };
};
</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="function-name">HiddenFunctor</span> = <span class="keyword">function</span>(<span class="js2-function-param">a</span>){
  <span class="keyword">var</span> <span class="variable-name"><span class="js2-warning">a</span></span> = a, <span class="variable-name">self</span> = <span class="builtin">this</span>;

  self.<span class="function-name"><b>fmap</b></span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAtoB</span>){
    <span class="keyword">var</span> <span class="variable-name">b</span>;

    <span class="comment">// if a is visible skip the action
</span>    b = a.is(<span class="string">":visible"</span>) ? a : fromAtoB(a);

    <span class="comment">// re-wrap
</span>    <span class="keyword">return</span> <span class="keyword">new</span> self.constructor(b);
  };

  self.<span class="function-name">hide</span> = <span class="keyword">function</span>(){
    a.hide();
    <span class="keyword">return</span> self;
  };
};
</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="function-name">HiddenFunctor</span> = <span class="keyword">function</span>(<span class="js2-function-param">a</span>){
  <span class="keyword">var</span> <span class="variable-name"><span class="js2-warning">a</span></span> = a, <span class="variable-name">self</span> = <span class="builtin">this</span>;

  self.<span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param"><b>fromAtoB</b></span>){
    <span class="keyword">var</span> <span class="variable-name">b</span>;

    <span class="comment">// if a is visible skip the action
</span>    b = a.is(<span class="string">":visible"</span>) ? a : fromAtoB(a);

    <span class="comment">// re-wrap
</span>    <span class="keyword">return</span> <span class="keyword">new</span> self.constructor(b);
  };

  self.<span class="function-name">hide</span> = <span class="keyword">function</span>(){
    a.hide();
    <span class="keyword">return</span> self;
  };
};
</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="function-name">HiddenFunctor</span> = <span class="keyword">function</span>(<span class="js2-function-param">a</span>){
  <span class="keyword">var</span> <span class="variable-name"><span class="js2-warning">a</span></span> = a, <span class="variable-name">self</span> = <span class="builtin">this</span>;

  self.<span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAtoB</span>){
    <span class="keyword">var</span> <span class="variable-name">b</span>;

    <span class="comment">// if a is visible skip the action
</span>    b = <b>a.is(":visible")</b> ? a : fromAtoB(a);

    <span class="comment">// re-wrap
</span>    <span class="keyword">return</span> <span class="keyword">new</span> self.constructor(b);
  };

  self.<span class="function-name">hide</span> = <span class="keyword">function</span>(){
    a.hide();
    <span class="keyword">return</span> self;
  };
};
</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="function-name">HiddenFunctor</span> = <span class="keyword">function</span>(<span class="js2-function-param">a</span>){
  <span class="keyword">var</span> <span class="variable-name"><span class="js2-warning">a</span></span> = a, <span class="variable-name">self</span> = <span class="builtin">this</span>;

  self.<span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAtoB</span>){
    <span class="keyword">var</span> <span class="variable-name">b</span>;

    <span class="comment">// if a is visible skip the action
</span>    b = a.is(":visible") ? a : fromAtoB(a);

    <span class="comment">// re-wrap
</span>    <span class="keyword">return</span> <span class="keyword">new</span> <b>self.constructor(b)</b>;
  };

  self.<span class="function-name">hide</span> = <span class="keyword">function</span>(){
    a.hide();
    <span class="keyword">return</span> self;
  };
};
</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="function-name">HiddenFunctor</span> = <span class="keyword">function</span>(<span class="js2-function-param">a</span>){
  <span class="keyword">var</span> <span class="variable-name"><span class="js2-warning">a</span></span> = a, <span class="variable-name">self</span> = <span class="builtin">this</span>;

  self.<span class="function-name">fmap</span> = <span class="keyword">function</span>(<span class="js2-function-param">fromAtoB</span>){
    <span class="keyword">var</span> <span class="variable-name">b</span>;

    <span class="comment">// if a is visible skip the action
</span>    b = a.is(":visible") ? a : fromAtoB(a);

    <span class="comment">// re-wrap
</span>    <span class="keyword">return</span> <span class="keyword">new</span> self.constructor(b);
  };

  self.<b><span class="function-name">hide</span></b> = <span class="keyword">function</span>(){
    a.hide();
    <span class="keyword">return</span> self;
  };
};
</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="variable-name">functor</span> = <span class="keyword">new</span> HiddenFunctor( $(<span class="string">"#dialog"</span>) );

<span class="keyword">function</span> <span class="function-name">show</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.show();
}

<span class="keyword">function</span> <span class="function-name">destroy</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.remove();
}

<span class="comment">// visible dialog cannot be destroyed
</span>functor
  .fmap(show)
  .fmap(destroy)
  .hide()
  .fmap(destroy);</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="variable-name">functor</span> = <span class="keyword">new</span> HiddenFunctor( <b>$("#dialog")</b> );

<span class="keyword">function</span> <span class="function-name">show</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.show();
}

<span class="keyword">function</span> <span class="function-name">destroy</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.remove();
}

<span class="comment">// visible dialog cannot be destroyed
</span>functor
  .fmap(show)
  .fmap(destroy)
  .hide()
  .fmap(destroy);</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="variable-name">functor</span> = <span class="keyword">new</span> HiddenFunctor( $(<span class="string">"#dialog"</span>) );

<span class="keyword">function</span> <span class="function-name">show</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> <b>$dialog.show()</b>;
}

<span class="keyword">function</span> <span class="function-name">destroy</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.remove();
}

<span class="comment">// visible dialog cannot be destroyed
</span>functor
  .fmap(show)
  .fmap(destroy)
  .hide()
  .fmap(destroy);</pre>


!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="variable-name">functor</span> = <span class="keyword">new</span> HiddenFunctor( $(<span class="string">"#dialog"</span>) );

<span class="keyword">function</span> <span class="function-name">show</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.show();
}

<span class="keyword">function</span> <span class="function-name">destroy</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> <b>$dialog.remove()</b>;
}

<span class="comment">// visible dialog cannot be destroyed
</span>functor
  .fmap(show)
  .fmap(destroy)
  .hide()
  .fmap(destroy);</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="variable-name">functor</span> = <span class="keyword">new</span> HiddenFunctor( $(<span class="string">"#dialog"</span>) );

<span class="keyword">function</span> <span class="function-name">show</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.show();
}

<span class="keyword">function</span> <span class="function-name">destroy</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.remove();
}

<span class="comment">// visible dialog cannot be destroyed
</span>functor
  <b>.fmap(show)</b>
  .fmap(destroy)
  .hide()
  .fmap(destroy);</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="variable-name">functor</span> = <span class="keyword">new</span> HiddenFunctor( $(<span class="string">"#dialog"</span>) );

<span class="keyword">function</span> <span class="function-name">show</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.show();
}

<span class="keyword">function</span> <span class="function-name">destroy</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.remove();
}

<span class="comment">// visible dialog cannot be destroyed
</span>functor
  .fmap(show)
  <b>.fmap(destroy)</b>
  .hide()
  .fmap(destroy);</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="variable-name">functor</span> = <span class="keyword">new</span> HiddenFunctor( $(<span class="string">"#dialog"</span>) );

<span class="keyword">function</span> <span class="function-name">show</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.show();
}

<span class="keyword">function</span> <span class="function-name">destroy</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.remove();
}

<span class="comment">// visible dialog cannot be destroyed
</span>functor
  .fmap(show)
  .fmap(destroy)
  <b>.hide()</b>
  .fmap(destroy);</pre>

!SLIDE
<pre class="xlarge">
<span class="keyword">var</span> <span class="variable-name">functor</span> = <span class="keyword">new</span> HiddenFunctor( $(<span class="string">"#dialog"</span>) );

<span class="keyword">function</span> <span class="function-name">show</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.show();
}

<span class="keyword">function</span> <span class="function-name">destroy</span>( <span class="js2-function-param">$dialog</span> ){
  <span class="keyword">return</span> $dialog.remove();
}

<span class="comment">// visible dialog cannot be destroyed
</span>functor
  .fmap(show)
  .fmap(destroy)
  .hide()
  <b>.fmap(destroy)</b>;</pre>

!SLIDE bullets
## protection

!SLIDE bullets
## thanks!
* @johnbender
* johnbender.us
* github.com/johnbender

