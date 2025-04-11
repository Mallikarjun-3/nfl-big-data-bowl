National Football League (NFL) arranged a Kaggle competition to develop a model to predict how many yards a team will gain on given rushing plays as they happen. We're provided game, play, and player-level data, including the position and speed of players as provided in the NFL’s Next Gen Stats data. And the best part - we could see how our model performed, as the leaderboard were updated week after week on the current season’s game data as it played out.


I developed a Deep Learning model consisting of Attention and Embedding layers on top of a Multilayer Perceptron.

Few words about how we came up with the model structure. To simplify we assume a rushing play consists of:

- A rusher, whose aim is to run forward as far as possible
- 11 defense players who are trying to stop the rusher
- 10 remaining offense players trying to prevent defenders from blocking or tackling the rusher

Embedding layers were used to represent player’s basic features (speed, direction and orientation) and their projections by other players. After, the projections of the features by teammates and rival team players were summed up, which brought symmetry for everyone.

For Data Augmentation; spatial features like coordinates were flipped with respect to X axis.

We blended 2 different MLP models and one Lightgbm model as you can see on "triple-blend-augmentation.ipynb" notebook, but, single model described above gave us best results on final leaderboard, which is implemented on "single-triple-augmentation.ipynb" notebook.

