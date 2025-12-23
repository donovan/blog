# Text is King (And LLMs Are Its Killer App)

*December 23, 2025*

So I was watching [Steve Yegge's talk](https://www.youtube.com/watch?v=grn8vsFYuP0) the other day, and he drops this line: "text is king." And I'm sitting there thinking, yeah, *obviously*. But then I started connecting the dots, and holy crap, this isn't just some throwaway observation. It's the entire history of computing in three words.

Let me back up.

## The Unix Philosophy Wasn't About Pipes

Everyone talks about the Unix philosophy like it's about "small tools that do one thing well" or "pipes and composition" or whatever. And sure, that's part of it. But the *real* Unix insight was simpler and more profound: **everything is text**.

Config files? Text. Log files? Text. System state? Text files in `/proc` and `/sys`. The shell? A text interface. Data flowing between programs? Text streams. Even the source code and the tools to manipulate it - all text.

And you know what happened? Linux ate the entire server market in the early 2000s. Not because it was technically superior (though it was). Not because it was cheaper (though it was). But because it was **inspectable**.

You could SSH into a box - and what's SSH? Secure Shell. A secure transport for *text*. You could read config files, grep through logs, pipe commands together. Everything was visible. Everything was debuggable. Everything was automatable.

Windows Server? You're clicking through GUI wizards and editing the registry with a binary blob editor. Good luck scripting that. Good luck debugging it when something goes sideways at 3 AM.

Text won because **text is the universal interface**.

## The Internet Runs on Text You Can Type

And then the internet happened, and it doubled down on text so hard it's almost comical.

SMTP? Text. You can literally telnet to port 25 and send an email by typing commands. Try that with a proprietary messaging system.

POP3? Text. IMAP? Text. DNS? Text. HTTP? Text. Every fundamental protocol of the internet is something you can type at a terminal and watch work.

And then HTML comes along and they add this little feature called **View Source**. Right-click, view source, and boom - you can see exactly how any webpage works. You can *learn by reading*. You can copy, modify, experiment.

Compare that to Flash. Slick, fancy, multimedia-rich, and completely opaque. You couldn't view source on a Flash site. You couldn't learn from it. You couldn't script it. You couldn't inspect it when it broke. And where is Flash now?

Dead. Killed by HTML5. Killed by text.

People say Flash died because of mobile, because Steve Jobs refused to support it. But that's not the whole story. Flash died because it was an **impenetrable binary blob** in a world that was standardizing on inspectable text. Even WebAssembly, which is literally compiled binary code running in browsers, ships with WAT - a text format specifically for human inspection.

Text won the internet. Every major protocol, every open standard, every piece of infrastructure that matters - text. Because when things break at 3 AM, you need to be able to read what's happening. You need to grep logs, inspect packets, trace requests. Good luck doing that with proprietary binary protocols.

## Then Came The Cloud (Still Text)

The cloud era doubled down on this. AWS CLI? Text in, text out. Configuration management? Chef, Puppet, Ansible - all manipulating text files. Infrastructure as code? Terraform config files. Text all the way down.

And what format did the web standardize on for APIs? JSON. And what's JSON? **Just text**. Beautiful, human-readable, grep-able, diff-able, jq-able text.

YAML happened. TOML happened. Even when we tried to make things "better" than JSON, we still made them *text*. Because the alternative - binary protocols, proprietary formats, opaque data structures - creates friction. And in a world where automation is eating everything, friction is death.

## Docker: Text Wrapping Text Wrapping Text

Docker comes along and revolutionizes deployment. What's Docker doing under the hood? It's wrapping a bunch of Linux primitives - cgroups, namespaces, copy-on-write filesystems. And how do you configure a container? A Dockerfile. Text.

What's in your image? Layers. What are layers? Tarballs. Can you inspect them? Yes. Can you diff them? Yes. Is the format documented? Yes. Because it's all text (or at least, text-manipulable).

Kubernetes appears and takes over the world. YAML everywhere. ConfigMaps? Text. Secrets? Base64-encoded text (okay, that's cheating, but still). The entire state of your cluster? Text files you can check into git.

## Git: The Text Diff Engine That Conquered The World

Speaking of git - why did git obliterate Perforce, SVN, ClearCase, and every other version control system?

Perforce: Binary blobs, centralized server, proprietary format.
SVN: XML metadata, centralized server.
ClearCase: [*shudders in enterprise*]

Git: Text diffs in a Merkle tree. Everything is content-addressed. Everything is inspectable. Everything is local. You can use standard Unix tools to poke around in `.git/`. You can write scripts to manipulate it. You can rebuild the entire repository from first principles if you have to.

Git won because it *embraced* text as the fundamental unit of work and built everything around making text operations fast and reliable.

## The Binary Holdouts

Now, there were always holdouts. Game engines stored scenes as binary files. Office documents were binary blobs. Photoshop files, video files, compiled binaries - obviously those need to be binary for performance or format reasons.

But notice what happened in those domains. Git handles them poorly. Diffing them is impossible. Merging them is a nightmare. Collaboration requires specialized tools. And progress in those areas has always been slower, harder, more tool-dependent.

Unity stores scenes as... well, they *used* to be binary. Now they're YAML. Wonder why that changed?

## Enter LLMs: Text's Killer App

And then LLMs show up.

Now, here's where it gets interesting. Because LLMs aren't just another automation tool. They're trained on text. They think in text. They output text. They're *really, really good* at manipulating text.

Show an LLM a Linux config file and it can tell you what it does, catch errors, suggest improvements. Show it a systemd unit file and it understands the structure, the dependencies, the implications.

Show it the Windows registry? "Here's the path, good luck."

Show it a Unity binary scene file? Opaque blob, can't help you.

Show it a Godot `.tscn` file? "Oh, this is your scene graph, you've got a Player node with a CollisionShape2D child, and here's how you'd add a health bar..."

## The Godot Example

I asked an LLM the other day what game engine I should use for a project where I wanted to store everything in git and have AI help me code. You know what it recommended?

Godot.

Not because Godot is objectively better than Unity or Unreal. But because Godot's scene files are *text*. The scripts are text. The project config is text. The entire game is representable as text files that can go in git.

Which means:
- The LLM can read them
- The LLM can understand them
- The LLM can suggest changes
- Git can diff them
- I can grep through them
- I can write scripts to manipulate them

There are no black boxes.

And here's the kicker: **the LLM is going to make this recommendation to everyone who asks**. Because the LLM knows it can help you more effectively with Godot than Unity. It's not biased toward Godot for ideological reasons. It's biased toward Godot because *Godot speaks the LLM's native language*.

## The Flywheel Effect

So now we've got a flywheel spinning up:

1. Tools that use text formats get better LLM support
2. Developers working with LLMs prefer tools with better LLM support
3. More developers use text-based tools
4. More text-based content gets created
5. LLMs train on that content
6. LLMs get even better at text-based tools
7. Go to step 1

And the inverse:
1. Binary/opaque formats have poor LLM support
2. Developers with LLMs avoid them
3. Less adoption, less content, worse LLM support
4. Death spiral

## We've Seen This Movie Before

This is the same dynamic that killed Windows on servers. Linux exposed everything as text. Windows hid everything behind GUIs and binary registries. Result? Linux became automatable, scriptable, understandable. Windows stayed point-and-click. And when the cloud arrived and automation became non-negotiable, Linux was ready and Windows wasn't.

Now it's happening again, but faster. Because LLMs aren't just making text easier to automate - they're making text easier to *understand*, to *create*, to *modify*. They're lowering the barrier to entry for working with text-based systems.

## What This Means Going Forward

If you're building a tool, library, or system in 2025 and beyond:

**Use text formats for everything you possibly can.**

Config files? Text. State files? Text. Data interchange? Text (JSON, not protobuf). Documentation? Text (Markdown, not PDF). Code? Obviously text, but think about generated code, intermediate representations, build artifacts - can those be text too?

Because every time you choose a binary format, you're building a wall between your tool and the next generation of AI assistants. You're making your tool harder to debug, harder to script, harder to learn, harder to extend.

And your competitor who chose text? They're going to eat your lunch. Because they'll have an army of LLMs that can read, understand, and manipulate their format fluently.

## The Registry vs. Config Files

Think about this: How many times have you asked an LLM for help with a systemd unit file? Probably a few times, and you probably got working answers.

How many times have you asked for help with a Windows registry key? Probably fewer, and you probably got "here's the general area, you'll need regedit to poke around."

Same class of problem (system configuration), radically different outcomes. Because one is text and one is a binary blob with a specialized editor.

## Text All The Way Down

The Unix philosophy was right. The cloud doubled down on it. Git proved it. Docker wrapped it. Kubernetes orchestrated it. And now LLMs are turbocharging it.

Text isn't just king. Text is the *only* universal interface we've found that works for humans, machines, and now AIs. Everything else is a specialized optimization that trades generality for performance. And increasingly, that trade isn't worth it.

Because when you choose text, you get:
- Version control for free
- Diffing and merging for free
- Grep, sed, awk for free
- Human readability for free
- Tool interoperability for free
- LLM support for free

When you choose binary, you get:
- Slightly better performance
- A lot of specialized tooling you have to write
- A smaller ecosystem
- And now, worse AI assistance

## The Godot Prediction

So here's my prediction: Godot is going to see a massive surge in adoption over the next few years. Not because it's better than Unity or Unreal on technical merits. But because it's the game engine that speaks LLM.

Every developer who asks an AI "what game engine should I use?" is going to hear "use Godot, because I can actually help you with it."

And they're going to listen.

Because why wouldn't you choose the tool where your AI pair programmer can read every file, understand every structure, and suggest changes with confidence?

## Text is King

Steve Yegge was right. Text is king.

But he probably didn't predict that LLMs would be text's killer app. That the same properties that made text great for humans and automation would make it *essential* for AI assistance.

We're entering an era where the tools that embrace text will have a massive advantage. Because they'll have an army of AI assistants that can fluently read, write, and reason about them.

And the tools that chose binary formats? They're going to struggle to keep up.

Choose text. Your future AI-assisted self will thank you.

## Things We Didn't Even Talk About

And I haven't even mentioned:

**Markdown** - conquered documentation, wikis, README files. GitHub, Stack Overflow, Reddit all standardized on it. Human-readable even without rendering. Compare to Word's `.docx` (XML blob) or `.doc` (binary nightmare). LLMs can read and write Markdown fluently. Word documents? Not so much.

**SQL** - text-based query language became the universal database interface. Killed navigational databases that required programmatic APIs. Every new database, even NoSQL ones, eventually adds SQL-like text query languages. Because developers want to *type queries*, not build object graphs.

**CSV** - the worst data format except for all the others. Survives because it's text. Grep-able, awk-able, human-readable. Excel's binary formats are "better" but harder to work with programmatically. And when you need to debug data import issues, you can open the CSV in a text editor and *see what's wrong*.

I could go on. LaTeX in academia. Configuration language wars (HCL, Jsonnet, CUE - all "better text" not "let's use binary"). RSS/Atom. SVG. DNS zone files. Prometheus metrics. The list is endless.

Every single one follows the same pattern: text enables universal tooling, universal tooling creates network effects, developers choose tools they can inspect and automate, binary alternatives get marginalized even when "technically better."

The LLM era just makes this pattern more powerful. Because "inspectable by humans" now translates directly to "understandable by AI."

---

*Footnote: Yes, I know there are legitimate reasons for binary formats in some domains. High-performance computing, real-time systems, storage efficiency, etc. I'm not saying text is always the right choice. I'm saying it's the right **default** choice, and you should have a really good reason before you reach for binary. And "that's how we've always done it" isn't a good reason anymore.*

---

*This post was written by Donovan Jones in collaboration with Claude Sonnet 4.5 (model ID: claude-sonnet-4-5-20250929) via Claude Code. The core observations and ideas came from watching [Steve Yegge's talk](https://www.youtube.com/watch?v=grn8vsFYuP0) and connecting patterns across computing history. The structure, prose, and examples were developed collaboratively. [Read more about how this blog works](2025-12-23-about-this-blog.md).*
