# Intro — Why This Talk

## The Shift

### Claude Code, or something like it, is the future -- if not the present

In my opinion, the IDE as we have known it is dead. Agentic coding tools -- Claude Code, and the wave of similar tools appearing around it -- are where every programmer should be moving their day-to-day work. Not eventually. Now. The gap between "I write code in an editor" and "I collaborate with an agent that writes code" is bigger than any tooling shift our industry has had in a long time, and the people who invest in understanding it early will compound that advantage quickly.

This is not a claim that typing code by hand is going away tomorrow, or that every problem is best solved by an agent. It is a claim about where the center of gravity is moving. The default workflow -- the one most work will flow through within the next year or two -- is agentic. The talk you are about to hear is built on that premise.

### The industry-wide shift is exactly what makes it feel overwhelming

Everyone's attention has pivoted to this at once. New tools, new techniques, new vocabulary, new etiquette -- all arriving faster than any of us are used to. That speed is most of what makes agentic development feel intimidating from the outside: there is always something you have not tried, always a thread claiming the thing you learned last month is already obsolete.

The good news is that once you use these tools regularly, staying current gets dramatically easier. You build intuition for what matters and what is noise. You stop chasing every new plugin and start recognizing which ones actually change how you work. The cost of entry is mostly the hump of that first month -- after that, the landscape is no longer strange, just fast.

## The Goal of This Talk

### Two things in parallel: hit the ground running, and understand what you are running on

We have two goals today, and they run in parallel rather than in sequence.

The first is practical: leave here with enough working knowledge of Claude Code to start using it productively tomorrow. Installation, basic usage, the handful of plugins worth having on day zero, and the extension points you will reach for once the basics feel natural. You should be able to sit down after this talk and do real work.

The second is theoretical: enough grounding in how these systems actually work -- tokens, context windows, attention, tool protocols -- to reason about why things work or do not, instead of cargo-culting tips from the internet. Practical knowledge without the mental model is how people end up fighting the agent. Mental model without the practical knowledge is trivia. We want both.

### Embrace the new pace of software production

When you really understand how to use these tools, you can produce outcomes as good as the ones you used to craft by hand -- at a fraction of the time. That is not a marketing claim. It is the plain reality of watching a well-configured agent work on a well-scoped task, with someone who knows what they are doing at the wheel.

This is the payoff. It is big, and it is why the rest of this talk is worth your attention. Everything that follows -- the ML basics, the installation ceremony, the `CLAUDE.md` conventions, the plugins, the MCP servers -- is in service of that outcome: producing better software, faster.

## The Price

### The speed changes the landscape faster than we are used to

The payoff comes with a cost. The landscape changes faster than our industry is used to: best practices from three months ago are outdated, tools you learned last quarter already have better replacements, "the right way" keeps moving. This is uncomfortable even if you are paying attention, and it is disorienting if you are not.

On top of that, the online conversation around these tools is a breeding ground for noise and FOMO. Breathless threads, hot takes, influencers selling snake oil, benchmark wars that do not reflect how anyone actually works. The combination -- fast-moving reality plus loud online signal -- makes it harder than it should be to ride the wave. A lot of people bounce off not because the tools are bad, but because the meta around them is exhausting.

Part of what we are doing today is giving you a baseline solid enough that you do not have to relitigate it every time a new thread goes viral. You will know what the pieces are, how they fit together, and which updates actually matter for you.

### A concrete example: this very talk

One last thing before we start. The deck you are about to see has been floating around for almost two months. I had to rewrite most of it in the two days before this talk -- because enough had changed, in features, in best practices, and in my own understanding, that the old version would have been misleading by the time it hit the screen.

That is the environment we are operating in. Accept it, and it becomes an advantage. Fight it, and it becomes exhausting. This talk is my attempt to help us all land on the first side of that line.

Let us get started.
