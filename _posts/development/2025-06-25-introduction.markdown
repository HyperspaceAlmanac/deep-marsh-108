---
layout: post
title:  "Introduction to the blog"
date:   2025-06-24 22:51:59 -0700
categories: update
permalink: "/updates/update1"
---
# TODO: Add pictures

## The Inspiration

I have not worked on any side projects in a while, and while watching the 1998 adapation of Water Margin(as you can probably already tell with the many references to the series), I had intrusive thoughts about training a deep neural network and teaching it martial arts. Expanding it a step further, I see potential in deep neural network as a game pregression system. Unlike soem of my other ideas, I see a lot of potential in this effort.

## The Idea

One of the main advantages of deep neural networks is that it can process a lot of data without overfitting. Rather than training the DNN on the game control inputs or basic AI behavior, what if I create a more complex simulation of the human body and teach the DNN martial arts?

In its simplest form, potentially an idle game or auto-battler where you have your character train and fight opponents. As the character trains and fight opponents, it is updating the DNN to keep on getting better at it. It could also be a very flexible system, where it can be a plug that can just be used to generate some cool attack animations.

Once I set up the simulation, I can also use it to define the error function to determine how well the model is perfomring based on the inputs. The model can be evaluated on how well it moves the muscle to attack(does it hit the target? How strong is the impact? How vulnerable is it to coutner-attack), defend against attacks(how well it mitigates incoming attacks), and can also be evaluated based on other factors such the personality of the character (impulsive vs observant / reactive) and other factors such as the purpose of the move (pokes should be fast and safer versus more powerful high commitment moves).

## The Plan

This will be a multiple phase project.

### Phase 1:

Create a basic simluation system that takes in the state of the characters + environment, the actions that will be performed, as well as evaluation criterias. The state will include things such as the volume of the cahracter's muscles, how tired they are, as well as some more asbtract things such as the character's personality (impulsive vs observant). For the action, it will be at a very granular level such as the muscle movement (for example, when a character throws a punch, they will increase the force by turning their body while throwing the punch). For the evaluation criterias, it will highlight which aspect of the results are more important (an offensive action should focus on dealin damage, while a defensive action should mitigate damage, the character may also be fishing for the opponent's tendencies).

I will probably start with something very basic such as hand to hand combat and no environment hazards. As a proof of concept, show that with the right input I can have the character throw a basic punch or do a basic kick(Mandarin Duck Kick!). I want to keep it modular and customizable, so that I can add in weapons, enviornmental objects such as chairs, and maybe also separated or integrated system for magic and battle Shonen power systems.


### Phase 2:

Once I have a basic working simulation system, it will be used to evaluate how effective the output from the DNN is. The DNN will most likely take in the state of the characters with some labels for the expected action (or potentially trying to predict the best action if I go that route), and have it generate some muscle and other body movements. The simluation then take the state and body movement to evaluate how good it is, and act as the error function so that the model can learn. The model will probably start off really ineffective and random, but should slowly get more effective over time.

I will start off with something simple, but it will be a cycle of adding new features and training the DNN to properly learn how to best interact with it.

### Phase 3:

Once I have a decent DNN or have a DNN that can adapt at a decently fast rate, it is time to build systems to utilize the simulation and DNN. It could just be as simple as sharing the simulation and model so that passing in the label for "punch" outputs a somewhat realistic punch animation.

I want to at least make a basic idle game where you can have your character start off with a basic DNN that gets better and better at martial arts over time. As the DNN learns, the character also puts on more muscles and get stronger in other ways.

## Closing Thoughts

I want to do something interesting, and document it this time. Writing a blog can potentially motivate me to put more time and effort into this.
