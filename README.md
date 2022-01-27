https://www.youtube.com/watch?v=_CO-ND1FTOU&t=533s&ab_channel=JeffHeaton

1.	Terminal: python –version # get the python version
2.	Terminal:  Which python # python install location
3.	Terminal: ls -l /usr/bin/python #details location of python

Where is python? (Usually)
1.	Miniforge:
a.	/Users/mdsanowarhossain/miniforge3/bin/python
2.	Miniconda:
a.	/Users/mdsanowarhossain/opt/miniconda3/bin/python
3.	HomeBrew Miniforge:
a.	/Users/mdsanowarhossain/opt/homebrew/Claskroom/miniforge/base/bin/python

Install URLS:
1.	Miniforge:
a.	https://developer.apple.com/metal/tensorflow-plugin/
2.	Miniconda:
a.	https://docs.conda.io/en/latest/miniconda.html

Install Mini forge:
1.	Brew
2.	cd miniforge3/bin/conda
3.	conda init zsh
4.	restart terminal
5.	cd t81_558_deep_learning
6.	conda install -y jupyter
7.	conda deactivate
8.	conda env create -f tensorflow-apple-metal.yml -n tensorflow
9.	conda activate tensorflow
10.	python -m ipykernel install –user -name tensorflow –display-name “python 3.9 (tensorflow)”
11.	conda activate base # back to the default
12.	jupyter notebook
13.	base: cat .zshrc
14.	mv ./ .zshrc ./start_miniforge.sh
15.	restart window
16.	python –version
17.	source ./start_miniforge.sh
18.	base:

Install miniconda:
1.	cd downloads 
2.	ls
3.	downloads: ./Miniconda3-py39_...sh
4.	are you continue for 64-bit: yes
5.	do you wish the installation to initialize Miniconda3 by running conda init: no
6.	cd ..
7.	cd miniconda3/bin
8.	conda
9.	./conda init zsh
10.	Which python
11.	Cd
12.	Cat .zshrc
13.	mv ./ .zshrc ./start_miniconda.sh
14.	ls *.sh
15.	which python
16.	source start_miniforge.sh
17.	conda env list
18.	source ./start_miniconda.sh
19.	conda env list
20.	conda activate


Installing TensorFlow 2.x with Keras (Mac M1 (Apple Metal) GPU Version:

home brew:
1.	/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
2.	Restart terminal
3.	Brew
4.	xcode-select –install
Install Miniforge:
5.	brew install miniforge
6.	which python
7.	conda init zsh
8.	conda install -y jupyter
9.	conda env create -f tensorflow-apple-metal.yml -n tensorflow # just delete it and recreate it if we want to update packages or modules
10.	conda activate tensorflow
11.	conda install nb_conda
12.	python -m ipykernel install --user --name tensorflow --display-name "Python 3.9 (tensorflow)"
13.	jupyter notebook
14.	


![image](https://user-images.githubusercontent.com/52736275/146691484-810893c1-5813-4582-9b9c-a644271540b6.png)
