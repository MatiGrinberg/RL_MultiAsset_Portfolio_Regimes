# RL_MultiAsset_Portfolio_Regimes & PCA & Markov Switching Autoregressive
### Used RL again to construct a portfolio with the same assets, but this time included probabilities of being in either of 2 regimes as a predictor feature.
### Reference of previous RL task => https://github.com/MatiGrinberg/RL_MultiAsset_Portfolio

* The main difference now is that the features are PCs that track movement in assets as before, but I added the probability of being in a High Volatility regime (which coincides with periods of market panic and the start of the recovery afterwards). Therefore, the idea was not to use exclusively the risk-on/off indicator represented by the 1st PC which accounts for the majority of the dispersion in returns of all assets, but also to include the probability of being in a high-volatility regime so that the algorithm could use this new information, aside from the level where the PC_1 is and its change during the last month, to allocate 100% of the portfolio among the 3 different assets (Eq, FI HY, FI Treas).
* The probability of being in a High or Low volatility regime is calculated using a Markov Switching Autoregressive model for regime detection and classification.
* The code was roughly the same as in the reference repository, so I didn't see the need of uploading all files again. If you use my previous RL repository as reference, this time instead of using PCs as features, I coupled it with the output (probabilities of belonging to one regime) from the Markov fitting. Therefore, in this repository, you should only find 1 file, where I calculate these probabilities and run the training and testing, as the rest is roughly the same. However, you can obviously see the feature engineering in it.
* The results are (even) ... than before. When compared against a (common) benchmark of 0.55 Eq + 0.25 Treas + 0.1 FI HY, it achieves an (average) Information Ratio (IR) of ... (from 1993 till 2023). When compared against an Equity passive strategy (portfolio = 100% SPX), it achieves an (average) IR of ...
* You can see an example below of the testing results for 1 period. You see how after training, on a new (unseen) test set, the model uses the information it has at that time (PC_1 and regime probability) to assign 100% of the weight of the portfolio to different asset classes. The returns obtained from it (weights * returns) are used to build the portfolio returns and the final value of it (and its benchmark) during the whole testing period (as seen in the graph). Each period tested provides an IR, and then all of them are averaged.


### Graph Results from portfolio construction

### Graph Weights assigned to the portfolio

