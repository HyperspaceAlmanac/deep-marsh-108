---
layout: post
title:  "High Level Overview of the Simulation System"
date:   2025-06-29 22:51:59 -0700
categories: update
permalink: "/updates/update2"
---
## High Level Overview of Combat Simulation

A quick overview(no time to add diagrams this time) of the simulation before I start playing around with some basic proof of concepts.

At a high level, the human body has a central nervous system that has sensors and actuators that are controlled by the brain. At the moment I don't want to do too much with the sensor nerves (it could be useful to simulate the combatant's vision and field of view) and will not have it affect the combatant's decision making process (probably have some general rules for when combatants realize that the other combatant is performing a certain action). I also don't want to fully simulate the CNS sending electric signals to the motor neurons(it would be kind of cool to do this). I am more interested in the motor functions want to simulate the movement of the muscle to have the body perform certain actions such as throwing a punch.

To keep it simple, I will start with combatants in static positions holding some form and does not take into consideration current momentum (making a decision while moving or performing an action). The assumption is that the two combatants will perform actions simultaneously (potentailly with one waiting a bit or anticipating an attack), and the actions potentially colliding. I will most likely have some separate system for the combatants to anticipate and "react" to certain actions, but it will start off quite simplistic.

To evaluate how effective actions and defensive manuevers are, I will need some basic physics and damage system to calculate what happens when someone is hit. There may be some displacement effects where a combatant is pushed back, some involuntary muscle response due to getting hit, and also the combatant's current actions being impacted when hit. With a damage system, I am thinking that I will probably have some basic simulation for the respitaroy system and some basic system for the organs for what happens when they are hit. Should probably also simulate broken bones and some other injuries.

To be able to calculate everything discussed above, I will probably need to define the conditioning of the combatants. There will probably be some data representing the size of the muscles, pain tolerance, reaction speed, and some other numeric values to represent the state of the body. Performing certain actions and moves may also strain the body in a certain way, and the combatant may become winded.

On simulating the the actions taking place between the combatants, the output should be the change in state of the combatants such as damage and momentum (knocked to the ground, flying through the air), and some general system for evaluating how effective the action was. For offensive actions, evaluate it based on several metrics such as damage dealt, success rate, how open the chracter is to counter-attack, and maybe the amount of effort to perform the action. Defensive actions can be evaluated on how effective it is in mitigating the damage and other metrics such as potential for counter attack.

As a separate component from the simuation itself, I also want a very basic presentation layer to display some basic 3d model to animate what is going on. The visualization of the combatants will probably make it much easier to analyze and debug certain issues.

## Starting with a Prototype

I want to start off by just doing something very basic with the body in some stance, and moving the muscles so that the combatant throws a punch. Once I have that, I will then look into having the combatant throwing the punch against another combatant and keep on building everything from there. After some basic thoughts, I think will just start off by coding this in Python(potentilaly easier to interact with the models), maybe just for the prototypes. If things go well, I might switch over to some other lower level languages such as C/C++(I dot have quite a bit of experience with it, but don't want to do a large project in it. I would still prefer this over Rust), GoLang(could be a good opportunity to learn it), or something else more easily packaged. The DNN training part will definitely be in Python since the libraries are the most developed there, and the simulation and training part really don't need to be in the same repo, even if it would mean that I will need to move the model and output from the DNN training repo to the simulation repo or somewhere else.

While a game engine could be good for the visualization aspect, I do want to avoid them since I want to create a more general standalone package / module that is not specifically tied to any game engine. Unreal supports C++, but does have a ton of bloat and is way overkill for what I am trying to do. Unity uses C# which I don't want to deal with, and something like Gadot is much more suited for 2D games (have not tried to render with Vulkan or Metal yet).

I will just start with some basic Python implementation and go from there.