<h1> Anomaly Detection in Bitcoin Transactions </h1> 

<p float="left">
  <img src="https://www.moneytaskforce.com/wp-content/uploads/2019/07/95995559_s.jpg" width="500" height="400" />
  <img src="https://upload.wikimedia.org/wikipedia/commons/4/4f/%EA%B0%90%EC%97%BC%EC%82%AC%EC%A7%84.png" width="500" height="400"/> 
</p>

<H3> Objective </H3>

Objective of this project is to detect anomalies in Bitcoin transactions. Question that we're trying to answer is - Given a set of transactions, can we predict transactions that are not confirming to standard transaction pattern in Bitcoin network? 

Before that, some background, Bitcoin is the largest cryto-currency network. Its an de-centralized network for money exchange and there is no central authority to monitor the whole network for any illegal activities. There is no indetification or KYC type of process in place to control who can enter and trasact on Bitcoin network. This is a biggest advantage of the Bitcoin network but at the same time, the same structure allows illegal entities to operate on this network freely. 

There are many illegal activities that for which Bitcoin network is being used - like Anti-Money Laudering, Ransomware Heist etc.,

There are various techniques published by research papers to address this problem. This project uses techniques published by one of such [research paper](https://arxiv.org/abs/1908.02591) to detect anomalies and there by classify illicit activites from licit ones.

<H2> Dataset and Data dictionary <H2>

We will be using [Elliptic Dataset](https://medium.com/elliptic/the-elliptic-data-set-opening-up-machine-learning-on-the-blockchain-e0a343d99a14) for this project. Its available on [Kaggle](https://www.kaggle.com/ellipticco/elliptic-data-set). This dataset is released to public by Elliptic so researchers can use real-world data for use cases like AML, Ransomware Heist and other illegal activities.

This dataset has 200K transactions that are partially labeled as 'licit' or 'illicit'. Around 4K transactions are marked 'illicit' and about 42K as 'illicit'. Rest of them are not labeled and it could be used for semi-supervised learning.

The key thing about this dataset compared to few other bitcoin datasets is that, this dataset has graph information of each of these transactions and so it can be used to determine 'illicit' transaction vs 'licit' ones. 

Apart from graph information, this dataset also has 166 features for each node (each transaction is represented as a node). It has a column to specify the timestep that each node/transacion belong to. There are 49 timesteps and a timestep is a period of about 2 weeks. 

<p float="left">
  <img src="https://miro.medium.com/max/875/1*mt4NEJOfr4rl_-0gp1fAlg.png"/>
</p>

[](https://miro.medium.com/max/875/1*mt4NEJOfr4rl_-0gp1fAlg.png)

Out of 166 features, first 94 of them contains *local* information about the node itself like number of inputs/outputs, transaction fee, output volume and aggregated features like average BTC received (or spent) by inputs/outputs and average number of incoming (or outgoing) transactions with inputs/outputs.

The remaining 72 features are for *nonlocal (graph)* information about neighboring nodes (limited to one-hop forward/backward from the center node) and this information is at max, min, std deviation and correlation coeffients of the neighbor transactions w.r.t the local data - ave BTC, number of incoming/outgoing, transacton fee etc.,
