# Why You May See an “Experimental Scripting” Warning

You may occasionally see an **Experimental Scripting** notice when opening or joining a BrickVerse experience. This notice means the experience uses one or more of BrickVerse’s newer scripting languages in addition to Luau.

BrickVerse was originally built around **Luau**, and Luau remains our primary and most broadly supported scripting language. As we expand the Creator and engine, we’re introducing additional languages so developers can choose the tools that best fit their projects.

Currently, these may include languages such as **C#, JavaScript, TypeScript, and C++ via WebAssembly**. Support varies by platform and execution environment.

### Why does the warning appear?

The warning is shown when an experience contains scripts written in an experimental language.

These languages are newer additions to BrickVerse and may have limitations, behavioral differences, incomplete APIs, or compatibility issues that Luau does not have. The notice is there so players and developers know that the experience is relying on functionality that is still being tested and improved.

Seeing the warning **does not necessarily mean something is wrong with the experience**. It simply indicates that experimental scripting technology is being used.

### Client vs. server scripting

One important limitation is that not every scripting language can run everywhere.

On desktop, BrickVerse can support additional runtime and sandboxing technologies that make languages such as C#, JavaScript/TypeScript, and WebAssembly practical.

Mobile platforms are more restrictive. Due to **iOS and Android runtime, code-execution, and sandboxing limitations**, BrickVerse currently cannot safely provide the same native client-side scripting support for these languages across every platform.

For this reason, **Luau is currently the only scripting language we recommend and support broadly for client-side scripts.**

Server-side scripts have considerably more flexibility because they execute within BrickVerse's controlled server environment rather than on a player's device.

### What should developers use?

Our recommendation is simple:

> **Use Luau for client-side scripting. On the server, use whichever supported language best fits your project and development workflow.**

Luau provides the greatest compatibility across BrickVerse platforms and has been part of the platform since its foundation. Existing experiences do not need to migrate away from Luau, and we aren't replacing it.

Additional languages are intended to **expand your options**, particularly for server-side development—not make Luau obsolete.

For example, an experience could use Luau for its UI, input, camera, and other client behavior while using TypeScript or C# for authoritative server gameplay systems.

### Why add more languages at all?

Different development teams have different backgrounds and requirements. A web developer may be much more productive with TypeScript, while an experienced .NET developer may prefer C#.

Supporting multiple languages also makes it easier to bring existing knowledge, libraries, architecture patterns, and development workflows into BrickVerse.

Our goal is for the scripting environment to eventually offer developers more choice while maintaining the security and sandboxing expected from a user-generated-content platform.

#### In short

**For players:** The Experimental Scripting notice simply means the experience uses one of BrickVerse's newer scripting technologies.

**For developers:** Luau remains the safest choice for maximum compatibility and should be used for client scripts. For server scripts, you're free to choose the supported language that works best for your project.

Experimental language support will continue to evolve as we improve compatibility, sandboxing, APIs, and tooling across the BrickVerse platform.
