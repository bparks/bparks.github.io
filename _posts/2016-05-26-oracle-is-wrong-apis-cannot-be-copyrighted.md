---
title: Oracle is Wrong. APIs can not be copyrighted
slug: oracle-is-wrong-apis-cannot-be-copyrighted
date: 2016-05-26 14:30:36
---

<p>Oracle and Google have been battling in court for <em>years&nbsp;</em>over whether Google&#39;s reimplementation of the Java APIs in Android constitutes copyright infringement. Note that the issue at stake is not whether Google infringed on Oracles copyright with regard to the implementation source code, but to the APIs themselves. Pivotal to understanding the situation is determining what, exactly,&nbsp;<em>is</em>&nbsp;an API. The judge in the case (who is cited in most articles as having learned Java specifically so he could understand this case, but that reads to me like a failure on the part of the prosecution to adequately explain what an API is) uses this metaphor:</p>

<blockquote>
<p>Oracle&#39;s collection of API packages is like a library, each package is like a bookshelf in the library, each class is like a book on the shelf, and each method is like a how-to chapter in a book.</p>
</blockquote>

<p>Not only is this a poor metaphor (it&#39;s a better metaphor for the actual&nbsp;<em>implementation</em>, with the Table of Contents perhaps being a better metaphor for the API), but it (unintentionally so on the Judge&#39;s part, since this is from his initial ruling in favor of Google) compares software APIs to something that is copyrightable (the contents of a book), which could set a dangerous precedent if the jury reads too much into it.</p>

<p>Google offers a metaphor of a filing cabinet with labels (the cabinet itself is a package, and individual files in drawers are labeled with what could be considered the API), which is simply confusing. I&#39;m not sure what Google was trying to accomplish in using such a metaphor.</p>

<p>If metaphors fail us, why not simply dispense with them and talk about what an API&nbsp;<em>really</em>&nbsp;is. Or, perhaps, start with what&nbsp;<em>isn&#39;t</em>&nbsp;an API.</p>

<h3>Documentation is not an API</h3>

<p>Oracle provides documentation on the APIs available in Java (the current version is <a href="https://docs.oracle.com/javase/8/docs/api/">here</a>). As a published work, this is incontrovertably copyrightable, and Oracle explicitly claims this at the bottom of the page. However, this is&nbsp;<em>not</em>&nbsp;the API; merely a description of how I might use it. I can not take this document, include it in my code (in any way), and expect my code to&nbsp;do something with the API. It&#39;s designed for human consumption.</p>

<p>As the document itself says, it is the &quot;API Specification&quot;, which indicates it is describing something&nbsp;<em>else</em>&nbsp;that is the API. Therefore, while the API documentation is copyrightable, it still is not the actual API and says nothing about the copyrightability of the API.</p>

<h3>Implementation is not an API</h3>

<p>A common practice in software engineering is to define the&nbsp;API first, before building the implementation. That is, you define what various classes and methods might be named, what types of values they might take as input, and what types of values they might provide as output (one could say this information constitutes the API).&nbsp;This is especially common when multiple people or teams are working together, with one writing the implementation and one using it (while it&#39;s still a work in progress). The teams agree to adhere to the API so that when it is time to integrate their code, minimal (if any) rework is needed. Since this API definition occurs prior to implementation, it follows that implementation (which is copyrightable) is not the API.</p>

<p>What&nbsp;<em>is</em>&nbsp;the API is the information the developers agreed to: the names of methods, the mechanism for organizing them into modules and packages, their inputs and outputs, and any other information necessary to build or make use of an implementation. However, this information is not copyrightable in the same way that while a research paper (documentation) is copyrightable and the data obtained in studies (implementation) is similarly protected (though not copyroghted; the metaphor breaks down here), the actual tests and experiments used to gather data described in the paper are&nbsp;not copyrightable.</p>

<h3>An API is an Interface</h3>

<p>This brings us to the crux of the matter. API means &quot;Application Programming Interface&quot;, which in layman&#39;s terms means it&#39;s the interface that allows different parts of a program to talk to each other in a well-defined and meaningful way. The metaphor I think of is one of a nut and bolt. The &quot;API&quot; between a nut and a bolt is the point at which they meet. In order for both to work together, they both must share certain characteristics, like the diameter of the bolt&#39;s shaft and the corresponding hole in the center of the bolt, the number of threads must match the number of grooves, they both must have the same pitch, and so on. We can certainly document this information, but the document would not be the API, and would certainly not prevent other people from making nuts and bolts from working with the ones we&#39;ve defined.</p>

<p>Back to programming, if I have an implementation of a method and another bit of code that uses the method, neither&nbsp;<em>is</em>&nbsp;the API, but both certainly&nbsp;<em>adhere to</em>&nbsp;the API. The API itself is where the two meet, which is completely intangible. It definitely&nbsp;<em>exists</em>, it&#39;s definitely a real thing, we can document it, we can implement it, and we can use it, but it&#39;s not a published work that can be copyrighted. (I&#39;ll refrain from getting into the etymology and definition of the word &quot;copyright&quot;.)</p>

<p>Another way to think of APIs is as if they&#39;re protocols. Are protocols copyrightable? No. Their documentation can be (it&#39;s a published work), as can their implementations, but the purpose of the protocol is to standardize communication between parts of a program (or multiple programs, potentially).</p>

<h3>The point of an API is not to be copyrightable</h3>

<p>If the point of an API is to promote collaboration and to ensure that code written by different teams or in different code bases is successfully interoperable, it makes no sense for APIs to be copyrightable. APIs are public by their very nature and to expose an API only to subsequently prevent people from taking advantage of it seems counterintuitive at best. If someone builds a new implementation of an existing API, that seems like an effort to embrace an ecosystem that already exists rather than fragment it (another of Oracle&#39;s claims is that Google&#39;s Java implementation impeded Java&#39;s adoption in the mobile world, but there is a whole Google Play store full of apps that would suggest otherwise).</p>

<p>Furthermore, it&#39;s not some malicious attempt to confuse the consumer into purchasing one company&#39;s product over another: Oracle does not make an operating system for phones, Oracle&#39;s Java is free to download, use, and build software for, and Google&#39;s API implementation is also free. Sure, Google provides additional functionality in the Android environment for things that aren&#39;t available in Java which prevents Android apps from running on other platforms Java supports without significant modifications, but that&#39;s no different from using the standard Java API in a piece of software along with other libraries. In short, Oracle&#39;s claim against Google runs counter to the whole point of having a public Java API in the first place.</p>

<h3>Conclusion: Oracle is Wrong</h3>

<p>Oracle has explicit copyright on everything that an API is&nbsp;<em>not</em>, but Google has not copied any of these published works and published them as their own. Google has merely written their own code in such a way that it conforms to an existing Java API standard. Since the API itself is merely information, there&#39;s nothing to copyright and nothing for Google to infringe upon. It can&#39;t be copied, since it doesn&#39;t exist in a copyable form (maybe imitable, but not copyable).</p>

<p>One can only hope that the jury can untangle the deception that Oracle has attempted and look past the confusing and inaccurate metaphors that Google and the judge have used to describe what an API is. However, regardless of the decision in this case, it is important that software developers stand up for themselves and maintain that APIs are free.</p>
