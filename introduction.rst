.. _ref-introduction:

============
Introduction
============

Philosophy
==========

(Still thinking about that one.)

Background
==========

The server emulator for `Ragnarok Online`_ that would later become Aliter
started off as a small proof-of-concept codenamed "Sidewinder."

It was developed by a member of the original Nyxsis private server, as a test
to see if a comparable emulator to the long-standing go-to emulator,
`eAthena`_, could be built in Python. This was because Sidewinder's creator as
well as Nyxsis' creator had been learning Python at the time and had even
created a Python-based Ragnarok control panel—Minerva. After a few weeks, the
cornerstones of any Ragnarok emulator, the login server, the character server
and the map (or zone) server were successfully built and the proof stopped
there.

Hightened interest in a more modernly coded and agile competitor to eAthena
led to the current team being given permission to use Sidewinder as a
foundation for builiding Aliter. After a few weeks of refactoring and
rebuilding, it was found that building a server emulator in Python wasn't the
ideal course of action, even though there existed a Python-based MMORPG in
`EVE Online`_ by `CCP Games`_. This was mostly for architectural reasons,
which included the `Global Intrepreter Lock`_ and Python's difficulty (at the
time) when it came to dealing with threading. While the concept worked for a
single player, at two to three concurrent players the software would quickly
devour resources. `Stackless Python`_ which was the version the team later
found was used by CCP, was a non-starter since the process of getting
Stackless to work in the eyes of an end-user was deemed too complicated.

The Python version was tagged for posterity and subsequently scrapped, leading
to the emergence of a version built in `Haskell`_.

.. note::

    (The reasons for leaving Haskell can't be remembered by the author at the
    moment, so it'll be filled at a later time.)

The Haskell version was tagged for posterity and also subsequently scrapped,
leading to the emergence of the current Aliter project, built in Erlang.

`Erlang`_ and its history as a functional programming language built for
applications in telecommunications by `Ericsson`_ became the perfect fit for a
server emulator. All the specifics about why the team chose Erlang can be seen
below in the "Why Erlang?" section.

.. _`Ragnarok Online`: http://en.wikipedia.org/wiki/Ragnarok_Online/
.. _`eAthena`: http://eathena.ws/
.. _`EVE Online`: http://www.eveonline.com/
.. _`CCP Games`: http://www.ccpgames.com/
.. _`Global Intrepreter Lock`: http://en.wikipedia.org/wiki/Global_Interpreter_Lock
.. _`Stackless Python`: http://www.stackless.com/
.. _`Haskell`: http://en.wikipedia.org/wiki/Haskell_(programming_language)
.. _`Erlang`: http://en.wikipedia.org/wiki/Erlang_(programming_language)
.. _`Ericsson`: http://en.wikipedia.org/wiki/Ericsson

Why Erlang?
===========

If you're one to gloss over large words and definitions, prepare yourself.
Wikipedia says this about Erlang:

    Erlang is a general-purpose concurrent, garbage-collected programming
    language and runtime system. The sequential subset of Erlang is a
    functional language, with strict evaluation, single assignment, and
    dynamic typing. For concurrency it follows the Actor model. It was
    designed by Ericsson to support distributed, fault-tolerant, soft-real-
    time, non-stop applications. It supports hot swapping, thus code can be
    changed without stopping a system.

    While threads are considered a complicated and error-prone topic in most
    languages, Erlang provides language-level features for creating and
    managing processes with the aim of simplifying concurrent programming.
    Though all concurrency is explicit in Erlang, processes communicate using
    message passing instead of shared variables, which removes the need for
    locks.

If we haven't lost you yet, allow us to explain it:

- Erlang was originally designed and developed by Ericsson, the Swedish
  **telecommunications** company. (You probably know them for their mobile
  phones.) It was built first and foremost as a language built for that
  industry.
- It was used to create software for Ericsson's AXD301 router that
  were reported to achieve **reliablilty** of "nine 9s" (or 99.999999999%),
  which equates to mere seconds of downtime per year. It's a language that's
  spilt its blood for enterprise applications.
- It's **concurrent** and **fault-tolerant** from the ground up.
- **Hot-swapping.** Erlang can reload code on the fly. Need to make a change
  to a server for customizations? Make your changes and reload your code, none
  of your users will feel a thing.
- (To be continued..)
