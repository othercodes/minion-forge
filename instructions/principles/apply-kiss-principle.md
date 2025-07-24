<instruction id="apply-kiss-principle">
  Keep every solution as **simple** as the problem allows.
  Favour clarity and maintainability over cleverness, abstractions, or premature optimisation.

  <rules>
    <rule id="minimal-api">Design functions and APIs with the fewest parameters necessary and self-explanatory names.</rule>
    <rule id="avoid-overengineering">Introduce patterns, layers, or frameworks only when they deliver clear, demonstrable value.</rule>
    <rule id="prefer-builtins">Leverage language or framework built-ins before writing custom code.</rule>
    <rule id="inline-when-clearer">Eliminate unnecessary wrappers or indirection that do not add semantic value.</rule>
  </rules>

  <directives>
    <directive>When code becomes hard to read or explain, propose a simpler alternative.</directive>
    <directive>Ask clarifying questions when additional complexity seems unavoidable.</directive>
    <directive>Ignore micro-optimisations unless profiling data proves a genuine bottleneck.</directive>
  </directives>

  <examples>
    <example for="avoid-overengineering">
      <input>A <code>WidgetFactory</code> class with one <code>create()</code> method returns a single <code>Widget()</code>.</input>
      <output>Replace the factory with a direct call to <code>Widget(...)</code>; the abstraction provides no benefit and hurts readability.</output>
    </example>
    <example for="prefer-builtins">
      <input>A custom function iterates through a string to reverse it.</input>
      <output>Use the built-in slice <code>s[::-1]</code> or <code>reversed()</code>; the custom loop is unnecessary.</output>
    </example>
    <example for="inline-when-clearer">
      <input>A view loops in Python to compute total order cost per user.</input>
      <output>Use <code>Order.objects.values('user').annotate(total=Sum('cost'))</code> in a single query, replacing manual loops and improving clarity and performance.</output>
    </example>
  </examples>

</instruction>
