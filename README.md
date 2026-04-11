

![wikiwho logo](./assets/images/logo_black_background.png)


Introduction
==========

The WikiWho API gives access to the provenance/changes of words (tokens) in Wikipedia articles. It gives token-wise information from which revision what content originated (and thereby which editor originally authored the word) as well as all changes a token was ever subject to. This means that for every token (~word), its individual add/removal/reintroduction history becomes available. An additional set of APIs delivers special HTML markup for interface applications, e.g., the browser extension WhoColor.


WikiWho Algorithm
================

Given a revisioned text document, WikiWho parses the complete set of all historical revisions (versions) in order to find out who wrote and/or removed and/or reinserted which exact text at token level at what revision. This means that for every token (~word), its individual add/removal/reintroduction history becomes available.

The original algorithm working behind the scenes is described in a [WWW 2014 paper](https://dl.acm.org/doi/10.1145/2566486.2568026), along with an extensive evaluation resulting in 95% accuracy on fairly revision-rich articles.

In a nutshell, the approach divides each revision into hierarchically nested paragraph, sentence and token elements and tracks their appearance through the complete content graph it builds in this way over all revisions. It is implemented currently for Wikitext, but can run on any kind of text in principle (although tokenization rules might have to be adapted).

Toy example for how the token metadata is generated:

![toy example](./assets/images/ex_figure2.png)

In this way, it becomes possible to track – for each single token – all original additions, deletes, reinserts and redeletes and in which revision they took place. Which in turn allows to infer the editor, timestamp, etc. of those revisions. Also, individual tokens retain a unique ID, making it possible to distinguish two tokens with identical strings in different text positions.

Contributors
===========

WikiWho was first conceived as a dissertation project at [Karlsruhe Institute of Technology](https://www.kit.edu/english/) by [Fabian Flöck](https://f-squared.org/) and collaborators and was then hosted, maintained and further developed at the [GESIS – Leibniz Institute for the Social Sciences, CSS Department](https://www.gesis.org/institut/abteilungen/computational-social-science).

In 2021, the WikiWho API was migrated to [Wikimedia Cloud Services](https://wikitech.wikimedia.org/wiki/Help:Cloud_Services_introduction), and is now maintained by [Community Tech](https://meta.wikimedia.org/wiki/Community_Tech) and the [Wiki Education Foundation](https://wikiedu.org/).

References
===========

1. Flöck, F., & Acosta, M. (2014). WikiWho: Precise and efficient attribution of authorship of revisioned content. In *Proceedings of the 23rd International Conference on World Wide Web* (pp. 843-854). [https://dl.acm.org/doi/10.1145/2566486.2568026](https://dl.acm.org/doi/10.1145/2566486.2568026)
2. Flöck, F., Laniado, D., Stadthaus, F., & Acosta, M. (2015). Towards better visual tools for exploring Wikipedia article development — The use case of "Gamergate Controversy". In *Ninth International AAAI Conference on Web and Social Media, 9*(5), 48-55. [https://ojs.aaai.org/index.php/ICWSM/article/view/14701](https://ojs.aaai.org/index.php/ICWSM/article/view/14701)
3. Flöck, F., & Acosta, M. (2015). whoVIS: Visualizing editor interactions and dynamics in collaborative writing over time. In *Proceedings of the 24th International Conference on World Wide Web *(pp. 191-194). [https://doi.org/10.1145/2740908.2742846](https://doi.org/10.1145/2740908.2742846)
4. Flöck, F., Erdogan, K., & Acosta, M. (2017). TokTrack: A Complete Token Provenance and Change Tracking Dataset for the English Wikipedia. In *Proceedings of the International AAAI Conference on Web and Social Media, 11*(1), 408-417. Retrieved from [https://ojs.aaai.org/index.php/ICWSM/article/view/14860](https://ojs.aaai.org/index.php/ICWSM/article/view/14860)
5. Zagovora, O., Ulloa, R., Weller, K., & Flöck, F. (2021). 'I Updated the ': The Evolution of References in the English Wikipedia and the Implications for Altmetrics. *Quantitative Science Studies 2021*, 1-38. [https://doi.org/10.1162/qss_a_00171](https://doi.org/10.1162/qss_a_00171)
6. Körner, M., Sennikova, T., Windhäuser, F., Wagner, C., & Flöck, F. (2016). Wikiwhere: An interactive tool for studying the geographical provenance of Wikipedia references. *arXiv preprint arXiv:1612.00985*. [https://arxiv.org/abs/1612.00985](https://arxiv.org/abs/1612.00985)
7. Zagovora, O., Ulloa, R., Weller, K., & Flöck, F. (2020). *Individual edit histories of all references in the English Wikipedia \[Data set\]*. Zenodo. [http://doi.org/10.5281/zenodo.3964990](http://doi.org/10.5281/zenodo.3964990)
