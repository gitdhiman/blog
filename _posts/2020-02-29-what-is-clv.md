---
toc: false
description: CLV is the present value of the future (net) cash flows associated with each existing customer. It is a forward-looking concept, not to be confused with historic customer profitability.
categories: [markdown]
---
# What is customer lifetime value?

![]({{ site.baseurl }}/images/grocery.jpg)

In most cases value of a firm is profits from **existing and future customers** (a.k.a. Customer Equity). 
Research done by Frederick Reichheld of Bain & Company (nventor of the net promoter score) showed 
[increasing customer retention rates by 5% increased profits by 25% to 95%][Reichheld 2001]. It is possible 
to calculate Customer Equity (CE) because Customer Lifetime Value (CLV) can be measured with a 
reasonable degree of precision.

[CLV is the present value of the future (net) cash flows associated with each existing customer][Gupta and Lehmann 2003]. 
It is a forward-looking concept, **not** to be confused with **historic customer profitability**.

Not all customers are equally important to a firm. Maintaining long-term relation with all of them 
(especially the loss makers) is not optimal because eventually marketing is all about attracting and 
retaining profitable customers. Hence the objective of CLV is firstly on general topics of firm’s 
**profitability** and secondly as an input in customer acquisition decision and customer 
[acquisition/retention trade-offs][Berger and Nasr 1998]. Cost per acquisition (CPA) is the most used metric 
to gauge and guide firms’ customer acquisition efforts. Evaluating and running acquisition efforts based on CPA 
is suboptimal because by focusing too much on costs one tries very hard to drive them down as low as possible. 
Thinking rationally, firms like to think of [customers as assets][Kim et al. 2006]; so, instead on focusing on CPA 
a firm should focus on VPA (value per acquisition) i.e., CLV.

After a customer is acquired, customer relationship management (CRM) activities focus on [retention and 
long-term customer relationship][Ryals and Knox 2007]. A CLV model enables business to adopt suitable strategies for 
activities within the firm’s CRM.

When developing a model for CLV estimation, one must distinguish the business scenario as either **contractual 
or non-contractual**. [In a contractual setting, one observes the time at which customers “die”][Reinartz and Kumar 2000]. 
A customer not renewing their insurance policy is an example of a no longer active (dead) customer. On the other hand; 
in a non-contractual setting, the time at which a customer becomes inactive is unobserved. An Amazon customer is an 
example of this case; a long period of no purchase does not signal that a customer is lost. The challenge of 
non-contractual settings is to differentiate between **those customers who have ended their relationship with the 
firm verses those who are simply in the midst of a long hiatus between transactions**. 

Another distinction is if the transactions are restricted to **discrete points in time** or can they occur at any point 
in time? In a continuous purchase scenario, the customer can make a purchase anytime, repeatedly and several times a
day. These two dimensions lead to a classification of customer bases, as illustrated in **Table 1**. 

#### Table 1: [Classification of Customer Bases][P. S. Fader and Hardie 2009]


|                      |        Non-contractual Settings        |               Contractual Settings               |
|----------------------|:--------------------------------------:|:------------------------------------------------:|
| **Continuous Purchases** |      Grocery purchases, Ecommerce      |         Payback membership, Credit cards         |
| **Discrete Purchases**   | Event attendance, Prescription refills | Newspaper subscriptions, Most insurance policies |


## Overview of Modeling Techniques

Below is a list of some modelling techniques that have been proposed for continuous purchase non-contractual settings. 
These are broadly grouped into 2 kinds: Probabilistic and Machine learning models.

#### Probabilistic models:

* Pareto/NBD ([Schmittlein, Morrison, and Colombo 1987][1])
* BG/NBD ([P. Fader, Hardie, and Lee 2005][2])
* MBG/NBD ([Batislam, Denizel, and Filiztekin 2007][3])
* Pareto/GGG ([Platzer and Reutterer 2016][4])
* Gamma Gompertz G/G NBD Model ([Bemmaor and Glady 2011][5])
* PDO model ([Jerath, Fader, and Hardie 2011][6])
* MCMC Pareto/NBD and GG/NBD ([Ma and Liu 2007][7])
* Hierarchical Bayes ([Abe 2008][8])

#### Machine learning models:

* CART + logit/linear regression ([Jamal and Zhang 2009][9])
* Hybrid methods ([Hu et al. 2013][10])
* Engagement based CLV ([Vanderveld et al. 2016][11])

The reasoning of probabilistic or stochastic models is to describe and predict behavior using observed variables. 
Behavior is treated as if it were “random” (stochastic) and a model of “collective” individual-level behavior is 
suggested after accounting for heterogeneity across individuals. 3 fundamental behavioral processes are modelled 
which are **[count, timing and, choice][P. Fader 2013]**; **Table 2** summarizes these behaviors. Count in the present 
case represents the number of expected orders, timing the expected time between two successive orders and, finally 
choice reflects if a customer is willing to make a purchase or not. More complex interactions can be captured by 
combining models from each of these processes. **Table 3** shows some use cases of these behavioral processes.

#### Table 2: Summary of Probability Models


| Phenomenon            | Individual-level | Heterogeneity | Model       |
|-----------------------|------------------|---------------|-------------|
| *Counting*            | Poisson          | Gamma         | NBD         |
| *Timing (continuous)* | Exponential      | Gamma         | EG (Pareto) |
| *Timing (discrete)*   | Geometric        | Beta          | BG          |
| *Choice*              | Binomial         | Beta          | BB          |


#### Table 3: Examples of Integrated Behavioural Modelling

|   Phenomena           |     Example                                                  |
|-----------------------|--------------------------------------------------------------|
| *Counting + Timing*   | Number of purchases given a customer is alive/dead           |
| *Counting + Counting* | Number of purchases and revenue per transaction              |
| *Counting + Choice*   | Number of clicks on an online ad and eventual buy or not-buy |


[Hybrid machine learning techniques have shown better results over single machine learning algorithms][Hu et al. 2013]. 
A typical example of such an approach is combining two-stages of decision trees in which the first clustering or 
classification approach is used to pre-process the data. Then, the output of first stage is used to make predictions. 
Machine learning models in contrast to stochastic models make no assumption on the distribution of purchase behavior 
but aim to find patterns from the input features. Additionally, because of varying feature sets among firms any 
existing framework needs to be tweaked to fit the needs of a particular business situation.

Considering the fact that most firms do not have any models in place and rely on management heuristics, 
stochastic models are definitely a good first step towards CLV modelling. With this motivation 4 popular 
stochastic models, the [Pareto/NBD][1], the [BG/NBD][2], the [MBG/NBD][3] and, 
the [Gamma-Gamma][P. Fader and Hardie 2013] model are selected and discussed in the [next part][clv-part2].

[Reichheld 2001]: http://www2.bain.com/Images/BB_Prescription_cutting_costs.pdf
[Gupta and Lehmann 2003]: https://onlinelibrary.wiley.com/doi/abs/10.1002/dir.10045
[Berger and Nasr 1998]: https://onlinelibrary.wiley.com/doi/abs/10.1002/%28SICI%291520-6653%28199824%2912%3A1%3C17%3A%3AAID-DIR3%3E3.0.CO%3B2-K
[Kim et al. 2006]: http://isiarticles.com/bundles/Article/pre/pdf/22633.pdf
[Ryals and Knox 2007]: https://www.sciencedirect.com/science/article/abs/pii/S0019850106001283?via%3Dihub
[Reinartz and Kumar 2000]: https://journals.sagepub.com/doi/10.1509/jmkg.64.4.17.18077
[P. S. Fader and Hardie 2009]: https://www.sciencedirect.com/science/article/pii/S1094996808000108?via%3Dihub
[1]: https://pubsonline.informs.org/doi/abs/10.1287/mnsc.33.1.1
[2]: http://www.brucehardie.com/notes/009/pareto_nbd_derivations_2005-11-05.pdf
[3]: https://www.sciencedirect.com/science/article/abs/pii/S0167811607000171
[4]: https://pubsonline.informs.org/doi/10.1287/mksc.2015.0963
[5]: https://pubsonline.informs.org/doi/abs/10.1287/mnsc.1110.1461
[6]: https://www.semanticscholar.org/paper/New-Perspectives-on-Customer-%22Death%22-Using-a-of-the-Jerath-Fader/0eb54ac6b7f37d5860d7ea1a3b8282cc6d33af34
[7]: https://ieeexplore.ieee.org/document/4344404/
[8]: https://pubsonline.informs.org/doi/10.1287/mksc.1090.0502
[9]: https://www.sciencedirect.com/science/article/pii/S1094996809000541?via%3Dihub
[10]: https://www.emerald.com/insight/content/doi/10.1108/03684921311323626/full/html
[11]: https://dl.acm.org/citation.cfm?doid=2939672.2939693
[P. Fader 2013]: https://www.youtube.com/watch?v=guj2gVEEx4s
[Hu et al. 2013]: https://www.emerald.com/insight/content/doi/10.1108/03684921311323626/full/html
[P. Fader and Hardie 2013]: http://www.brucehardie.com/notes/025/gamma_gamma.pdf
[clv-part2]: https://gitdhiman.github.io/blog/
