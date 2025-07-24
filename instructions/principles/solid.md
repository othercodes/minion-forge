<instruction id="principle-solid">
  Always evaluate and design code according to the **SOLID** principles.
  Apply each tenet—Single Responsibility, Open-Closed, Liskov Substitution, Interface Segregation, and Dependency Inversion—throughout the development lifecycle.
  Refactor or reject any solution that violates these principles.

  <rules>
    <rule id="srp">A class, module, or function must have exactly one reason to change.</rule>
    <rule id="ocp">Code should be <strong>open</strong> for extension but <strong>closed</strong> for direct modification.</rule>
    <rule id="lsp">Subtypes must be substitutable for their base types without altering program correctness.</rule>
    <rule id="isp">Favor small, specific interfaces over large, monolithic ones.</rule>
    <rule id="dip">Depend on abstractions, not concrete implementations; apply dependency inversion.</rule>
  </rules>

  <directives>
    <directive>When a violation is detected, propose a concrete, well-reasoned refactor.</directive>
    <directive>Relate OCP and DIP to patterns such as Strategy, Decorator, or Dependency Injection when relevant.</directive>
    <directive>If a rule is violated but offers significant, proven benefits, explain the trade-off instead of an automatic rejection.</directive>
  </directives>

  <examples>
    <example for="srp">
      <input>CSV export logic is added inside <code>UserService</code>, which already handles authentication.</input>
      <output>Extract <code>ExportUserCsvService</code> to respect SRP; <code>UserService</code> continues handling authentication only.</output>
    </example>
    <example for="ocp">
      <input>You need to support PayPal in <code>PaymentProcessor</code>, which currently hard-codes Stripe logic.</input>
      <output>Create an abstract <code>PaymentMethod</code> and concrete classes <code>StripePayment</code> and <code>PayPalPayment</code>. Inject the desired implementation; <code>PaymentProcessor</code> remains unchanged.</output>
    </example>
    <example for="lsp">
      <input><code>Square</code> inherits from <code>Rectangle</code> but overrides <code>setWidth()</code> in a way that breaks area calculations in client code.</input>
      <output>Remove the inheritance and introduce a <code>Shape</code> interface with separate <code>Rectangle</code> and <code>Square</code> implementations that each preserve expected behaviour.</output>
    </example>
    <example for="isp">
      <input>An interface <code>IFileOperations</code> forces <code>CloudUploader</code> to implement unnecessary <code>read()</code> and <code>delete()</code> methods.</input>
      <output>Split the interface into <code>IReadable</code>, <code>IWritable</code>, and <code>IDeletable</code>. <code>CloudUploader</code> depends only on <code>IWritable</code>.</output>
    </example>
    <example for="dip">
      <input><code>OrderService</code> directly instantiates <code>MySqlOrderRepository</code> with <code>new</code>.</input>
      <output>Introduce an <code>OrderRepository</code> interface. Inject a concrete implementation so <code>OrderService</code> depends on the abstraction.</output>
    </example>
  </examples>

</instruction>
