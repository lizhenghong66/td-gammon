# TD-Gammon

Implementation of [TD-Gammon](http://www.bkgm.com/articles/tesauro/tdl.html) in TensorFlow.

Before DeepMind tackled playing Atari games or built AlphaGo there was TD-Gammon, the first algorithm to reach an expert level of play in backgammon. Gerald Tesauro published his paper in 1992 describing TD-Gammon as a neural network trained with reinforcement learning. It is referenced in both Atari and AlphaGo research papers and helped set the groundwork for many of the advancements made in the last few years.

The code features [eligibility traces](https://webdocs.cs.ualberta.ca/~sutton/book/ebook/node87.html#fig:GDTDl) on the gradients which are an elegant way to assign credit to actions made in the past.

## Training

1. [Install TensorFlow](https://www.tensorflow.org/versions/r0.7/get_started/os_setup.html#pip-installation).
2. Clone the repo: `git clone https://github.com/fomorians/td-gammon.git && cd td-gammon`
3. Run training: `python main.py`

## Play

To play against a trained model: `python main.py --play --restore`

## Things to try

- Compare with and without eligibility traces by replacing the trace with the unmodified gradient.
- Try different activation functions on the hidden layer.
- Expand the board representation. Currently it uses the "compact" representation from the paper. A full board representation should remove some ambiguity between board states.
- Increase the number of turns the agent will look at before making a move. The paper used a 2-ply and 3-ply search while this implementation only uses 1-ply.

这个游戏是比较经典的游戏，但是国内用户不多，不熟悉玩法.
http://www.bkgm.com/rules.html
https://en.wikipedia.org/wiki/Backgammon

经过简单修改，该游戏可以在python 3（测试环境是win python 3.6.1）和tensorflow 1.0以上（测试环境 tensorflow 1.3) 上运行。

主页解决的问题：
1. 在python3 环境打印棋盘格式调整
2. humanAgent 在特殊情况下不能继续游戏（如两个骰子数相同时，需要4步移动，特殊情况下只能3步合法移动）
3. tensorflow 1.0以上的语法修正。

遗留问题：
    目前这个游戏玩法不完全合乎规则，棋子移动方向都是顺时针（己方移动应该逆时针，但对方棋子移动是正确的），仅仅作为人工智能（增强学习）用例还是不错。
