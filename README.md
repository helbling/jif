# Juggling Interchange Format (JIF)

JIF is a file format for interchanging information about a juggling pattern between different software components.

The format is not specified yet. This repository will be used to define and host its specification.


## Goals

JIF should be able to describe as many juggling patterns as possible.

It should hold all necessary information for at least the following applications:
- Drawing causal and ladder diagrams
- Animation

As there are many other possible usages the format should be capable to hold information the specification does not cover yet. Applications that operate on JIF files should expect the possibility of such additional information and pass it on whenever possible.

Most fields of the format should be optional. Programs with JIF input should define reasonable defaults for missing information. These defaults might differ depending on the application. For example one application might be written passing whereas another one targets solo juggling.
This allows for a software pipeline of components that define a juggling pattern in more and more detail from some high-level description down to a physical animation.

To speedup standardization the focus should stay on the most important applications. Other applications can follow, when there is high interest. The bug tracker of this repository should be
 used to discuss extensions of the standard.

JIF is specifically designed to help computer programs to understand details of juggling patterns. It should be easy to write programs that generate, enrich or modify a pattern or display diagrams and 
animations of a given one. In contrast to different high-level descriptions like siteswap (and its extensions) it should not be as short as possible and it is not thought to be written manually. Nevertheless it should be possible to readable and understandable by humans.

## First steps

The following aspects should be standardized first:
- metadata like:
  - title
  - number of objects
  - number of hands
  - number of jugglers
  - period (if repeatable)
  - description in some high-level language
  - comments
- logical throws as in what we consider a throw in causal diagrams:
  - throw time
  - time until next throw
  - source and destination hand
- optional data like:
  - timing data:
    - hold time/dwell time
      ( or throw time / catch time)
    - length of a time unit in seconds
  - juggler positions and movements
    - throw/catch coordinates
    - hand positions at throw/catch
    - movements of other body parts
    - hand movements while not carrying an object (dwell time)
    - body part that catches (hand, foot, head, two hands (diabolo wire?))

  - physical throws for animation
    - properties like:
      - type of throw
      - number of spins
      - spin direction, axis
      - manipulation/movement while holding the object
     - object reference ??
     - mapping hand reference to juggler and side ???

    - object details like:
      - type of prop
      - color / texture


 ## Decisions

 The format will be built on JSON.

 Wherever we have references in the standard (i.e. objects, hands or jugglers), we will use integers starting with 0.

 Time should be represented as a floating point number in order to avoid limits of integer timings.


 ## Further considerations

 - we might even want to generate the hand concept much more to a object manipulating entity
   which might as well be a foot, a floor, wall, table and so on
 - repetition might be considered a feature. Instead of seeing all patterns as endlessly repeating,
 we could mark repetitions explicitly and even have the possibility of repeating subsequences.
   This could be more appropriate to describe things like a full juggling act, or demonstrating how to get in and out of a siteswap. 
 - Object relabeling at the end of a period:
   If a (part of a) pattern can be repeated, it should be clear from end positions of the objects which role they will play when the pattern is repeated. This requires an adequate description of start positions (objects in hands, in the air etc).
 As it might take quite long until all objects are in their starting positions again at the start of an iteration.
 - The data about juggler position and movement should allow to represent moving take-out patterns, they seem to be very popular nowadays


 ## Thanks

 I would like to thank everyone who helped me with this project. Especially:
 - Wolfgang Westerboer, Author of the famous juggling animation programm JoePass
 - Adrian Goldwaser
 - Lukas Bonauer
