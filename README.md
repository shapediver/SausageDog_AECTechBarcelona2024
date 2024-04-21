# SausageDog Hack - AECTech Barcelona 2024
This repository contains the results of the SausageDog hack at AECTech Barcelona 2024.

![sausagedog4](https://github.com/shapediver/SausageDog_AECTechBarcelona2024/assets/8183687/aefec7fd-bb33-4aa5-bd37-702f43e62f19)

Presentation: [AECtech_2024_Hotdog_Optimizer.pdf](AECtech_2024_Hotdog_Optimizer.pdf)

## Motivation

We make complex design spaces accessible to end users without requiring them to operate 
the various parameters controlling the design space. The end users choose what is important, 
and an optimization algorithm picks options from the design space. 

## Technical overview

We implement a web application that includes an implementation of the 
NSGA-II (Non-dominated Sorting Genetic Algorithm II) algorithm. Please find details about
this algorithm and our implementation 
[here](https://github.com/shapediver/AppBuilderSdk/tree/task/optimizer/src/optimization). 

The optimization algorithm runs on the front end, but the population computation
uses Grasshopper models computed on a ShapeDiver system. This allows us to offload
the heavy computations to the cloud and parallelize them. The optimization algorithm
does not require heavy computation and is ideally suited for web browsers. 

### Front-end implementation

Our implementation is based on the [ShapeDiver App Builder](https://help.shapediver.com/doc/shapediver-app-builder) 
framework. We extended the React front-end code by the optimizer and a corresponding 
UI widget. You can find our changes in this [pull request](https://github.com/shapediver/AppBuilderSdk/pull/72). 

The optimizer can be used using any Grasshopper model uploaded to ShapeDiver which fulfills
the requirements as explained in the following. 

### Grasshopper models

Directory [Grasshopper](Grasshopper) contains example models from which to start. The Grasshopper
models need to include a data output component defining the objectives for the optimization algorithm. 
They also need to include the App Builder components defining the optimization widget as shown 
in the example models (simply copy those components).

The optimizer in the front-end is capable of optimizing the following types of parameters of the Grasshopper models: 

  * Numbers, Integers
  * Value lists
  * Booleans

## How to use it

The front-end application is deployed [here](https://appbuilder.shapediver.com/v1/main/0.3.0-optimizer/). 
It can be used using any Grasshopper model uploaded to ShapeDiver that fulfills the requirements explained above. 

Some examples: 

  * Hot Dog
    * [Grasshopper model](Grasshopper/HotDog.ghx)
    * Give it a try [here](https://appbuilder.shapediver.com/v1/main/0.3.0-optimizer/?slug=240421-hotdog)
  * Barcelona Blocks Optimizer 
    * [Grasshopper model](Grasshopper/BarcelonaBlocksOptimizer.ghx)
    * Give it a try [here](https://appbuilder.shapediver.com/v1/main/0.3.0-optimizer/?slug=barcelonablocksoptimizer)
    * ![bcn-gif](https://github.com/shapediver/SausageDog_AECTechBarcelona2024/assets/8183687/530ccdc5-2661-4bb4-b33c-cf2cd785805c)

Read more [here](Hotdog_Optimizer_Readme.pdf).

![hotdog-gif](https://github.com/shapediver/SausageDog_AECTechBarcelona2024/assets/8183687/3e6de337-4bca-4b6d-b5ff-a08f5e1f90bd)


