###### NARA_Living_Lab's CSR project

## Force Atlas & Virus Simulation 

### Motivation

A much of flooding news regarding Covi-19 virus spreading sparked me to ask the very naïve research question: When this nightmare will be ended, and have we handled well? As a data scientist mainly working for government-funded research projects, I’ve insisted the importance of open source project, living-lab movement, and data-driven policy. However, facing a wholly new panic called corona virus, I must confess that I’ve been neglected in exploring real-world questions and spent much of time in submitting and revising old-fashioned-nobody-care manuscripts

### Related Work

This work is especially owe to several seminal work of a novelist (Isaac Asimov) from his book Foundation (https://en.wikipedia.org/wiki/Foundation_series), and an artist (Daniel Shiffman) from his book of code of Nature (https://natureofcode.com/), a scientist (Anthony Giddens) from his theory of Structuration(https://en.wikipedia.org/wiki/Structuration_theory) and much of efforts of software developers in open source society (https://github.com/d3/d3-force).  There has been much of related work on virus simulation in Academy. One of notable works is Thomas Woolley’s project on diffusion or dead (https://www.cardiff.ac.uk/news/view/825352-diffusion-of-the-dead-using-mathematics-to-escape-a-zombie-apocalypse) which especially guided for me to teach Sungshin University students about the random-walk and Monte Carlo simulation in java-script with aid of Kahn Academy in two years ago. Author wish this work would contribute to much of extant wisdom of various discipline above mentioned.  

### Model

This study investigates how the trend of virus spread will be affected by force, society and policy within network under the view of time and space as follows: 
In this model, people’s movements are viewed as positions of nodes of world network. Their positions are initially determined by law of nature (force) and social scheme (society). As for force, I assume every nodes of network interacts with each other with attraction or repulsion like the way force does in the nature. As for society, I assume nodes belong to a certain party such as nation or political party, but furthermore, nodes interact with each other who belong to different parties. People with same party are possibility positioned close. As for policy, I incorporate the governmental action as isolating (blocking) some of people. 
Turning to virus movement, it is featured by statistics with known numbers - cure rate, host-killing rate, and with unknown numbers - spreading rate in terms of the social links or spatial position.
Both of people’s movement and virus spreading, both time and space have unique and important roles in that virus move to spatially-closely positioned host (person) and move to timely-next target (person). 

### Method

#### Dataset 
Json -typed dataset was used as following example of network with two nodes and two parties: 
[graph: [nodes: {name: AAA, party: aaa}, {name: BBB, party: bbb}], [links: {source: AAA, target: BBB}]]

I used the dataset of d3 https://github.com/d3/d3-force because of two reasons, first, thankfully, it is open and second it explains plausibly real-world pattern of social connection in that it represents the distribution of parties is scale-free but the connection of each nodes is not. 

#### Simulation parameters
##### Force atlas
The force simulation requires five parameters: i) link attraction ii) party force iii) horizontal force iv) collision, and v) charge of all people. The link attraction affects the linked nodes to positioned closely, party force affects the member of same parties to positioned closely. The horizontal force applies to pull all the nodes to centered horizontal lines just like gravity does. Collision force detects other nodes within given radius (neighbor) and repulse against it preventing collision. The parameter for collision force sets the radius for such repulsion. The charge of all people affects mutually almost all the nodes, it makes one node attracts or repulses each other.
Above mentioned five forces are summed to decide the optimize position for each node. 

##### Virus Spread
The virus simulation requires four parameters: i) spread rate of social tie (from socially connected) ii) spread rate of neighbor (from spatially closed) iii) disappear rate, and iv) host-killing. The spread rate of social ties affects the linked people from source to target only. I do not incorporate the node within same party without direct link, however, force party makes those nodes positioned close, thus they have change to occasionally meet as a neighbor.  

#### Random Walk simulation mode along with User interruption mode 
Once above-explained parameters were set, user selection for initial seeds of virus are required. After then, virus starts to spread according to the given rate and calculated positions of nodes. I use random walk simulation approach thus every chance of spreading, disappearing, and host-killing is calculated by the random number at each time point. I only incorporate link and space features of nodes but not other conditions about nodes – such as age. 
The third element of network in reference mode, namely, policy is not applied in random simulation mode but applied by the user-interruption. User choose the nodes which, he/she thinks, should be blocked to prevent spread of virus then move to random simulation node. Once choose as isolated node, nodes positioned far from other nodes and but not unlink the social ties.

### Applicaion

The simulation program consists of 4 panels: i) story panel, ii) left sided parameter mix panel iii) main network panel, and iv) statistics & chart. In story panel, it presents the basic statistics of dataset, force and virus parameters, and selected people to be isolated. In left sided panel, user choose parameters regarding force and virus features. In main network panel, user views the networks of given force. Each party presents different colors. If people affected virus, it colors in gray. If people killed, in black, if recovered shaped in rectangle. 

See the source code at : https://github.com/wildcat842/NARA_Force_Virus_Block_Simulation

See the application at  http://157.245.185.1/simulation/Force_Virus_Simulation.html



