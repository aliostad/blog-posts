# Why WebAssembly matters?

WebAssembly as a specification-first technology, is probably one of the few innovations of the web where the spec is not a retrospective documentation of the technology. WebAssembly community group started in 2015 and with its version 1.0, nowadays it **feels** like it has crossed from an *experimental* status into a *production-ready first-generation* technology - let alone the same also being claimed on its website.

On the browser, execution of any application code other than javascript is immediately reminiscent of the pile of technologies of the kind, that nowadays have little significance other than their historical ones: Java applets, Adobe Flash and Microsoft Silverlight. It has been proved over and over that **Web Always Wins**.

This has recently sparked conversations and debates on the community on the merits, use cases and typical scenarios where you would use WebAssembly (and especially [Blazor](https://dotnet.microsoft.com/apps/aspnet/web-apps/client) in the .NET community, although Blazor adds a [server-side](https://docs.microsoft.com/en-gb/aspnet/core/blazor/?view=aspnetcore-3.0#blazor-server-side) scenario which simply is not WebAssembly). 

![WebAssembly](https://2r4s9p1yi1fa2jd7j43zph8r-wpengine.netdna-ssl.com/files/2017/02/04-02-langs08.png)

The classic view is that WebAssembly will allow C, C++ and Rust developers to be able to [join](https://hacks.mozilla.org/2017/02/creating-and-working-with-webassembly-modules/) the web's cool party. For some, it is a game changer: it will revolutionise Web Application development - potentially even [sideline Javascript](https://www.quora.com/Will-WebAssembly-replace-JavaScript/answer/Aaron-Martin-Colby). For others, it has (albeit limited) use-cases for high-computation [gaming](https://hacks.mozilla.org/2017/07/webassembly-for-native-games-on-the-web/). Some propose that [AI on the browser](https://arxiv.org/pdf/1901.09388.pdf) could be a growing market and enhance the capabilities of today and tomorrow web sites. And yet others feel it will [die off](https://news.ycombinator.com/item?id=11977739) as it is competing with web, and the web always wins.

Of course, it is different to compiled-code technologies of the past. Unlike them, it is an Open standard adopted equally by all major players. It does not need a plugin to run - since, simply as it were, the plugin is distributed along with the browser.

There is a level of truth to many of these statements: it will shine in special case scenarios such as gaming and AI. But that is NOT why I think it matters, and I am writing these lines. But I believe the main potential has **nothing to do with gaming or AI**: it is an *incidental feature* of the WebAssembly and in order to explain it I have to bring example from the web?

Do you remember Ajax? Ajax was a [hack](https://en.wikipedia.org/wiki/Ajax_(programming)#History) by Microsoft Outlook team to load emails asynchronously as they arrive - instead of reloading the page. Now it is impossible to think of the web without Ajax. Hence:

> I claim that the most important feature of WebAssembly is the fact that it runs on the same sandbox as the browser's Javascript. In fact, the C, C++ and Rust impact is just a minor distraction: companies will build (and already have) adaptors for high level languages (such as Java, C#, Python) to interact according to the WebAssembly specification.


# WebAssembly will revitalise desktop app development 
When was the last time you installed an unknown app on your desktop (Windows or Mac)? In the early 2000s, viruses almost completely killed desktop application market for everyone but the major vendors. For many smaller vendors, still the only way to reach escape velocity and conquer mass market is to provide native mobile apps or web-based application and after years of gaining customers' trust, one might install their desktop app. Who would have just tried [Evernote](https://evernote.com/) purely as a desktop application?

Apple's iOS (and then Android) with its rigorous app governance and opt-in ACL policy created a sandbox for the apps to harness them so that they ask for access on resources they absolutely need. This was not an after-thought, but a design decision from day one. Major Desktop Operating Systems do have concepts of kernel mode vs user mode and file ACL but they are not designed for comprehensive opt-in ACL. And that is why even Mac app store feels pretty deserted with tumbleweed rolling on the street, let alone Windows 8/10 whose app store is more like a joke.

I strongly believe WebAssembly will become a **vehicle for desktop application delivery**. First, it is web-based, allowing the same levels of discoverability, ease of registration, monetisation/subscription and seamless update mechanism. Second, it is 100% secure (or at least as secure as websites we visit everyday) and there is no more a concept of installation. Third, it will make software rental very easy and will allow for the growth of SaaS for compute-intensive applications.

While [Electron](https://electronjs.org/) applications provided ease of developing desktop applications using Web toolkit, WebAssembly will turn this approach on its head and bring native performance to the web.

Web is ubiquitous and WebAssembly will conquer desktop applications.





