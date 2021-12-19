T81-558: Applications of Deep Neural Networks
Manual Python Setup

Instructor: Jeff Heaton, McKelvey School of Engineering, Washington University in St. Louis
For more information visit the class website.
Software Installation (Mac on Apple Metal M1)
This class is technically oriented. A successful student needs to be able to compile and execute Python code that makes use of TensorFlow for deep learning. There are two options for you to accomplish this:

Install Python, TensorFlow, and some IDE (Jupyter, TensorFlow, and others)
Use Google CoLab in the cloud
Installing Python and TensorFlow
Is your Mac Intel or Apple Metal (ARM)? The newer Mac ARM M1-based machines have considerably better deep learning support than their older Intel-based counterparts. Mac has not supported NVIDIA GPUs since 2016; however, the new M1 chips offer similar capabilities that will allow you to run most of the code in this course. You can run any code not supported by the Apple M1 chip through Google CoLab, a free GPU-based Python environment.

If you are running an older Intel Mac, there still are some options. Refer to my Intel Mac installation guide.

With the introduction of the M1 chip, Apple introduced a system on a chip. The new Mac M1 contains CPU, GPU, and deep learning hardware support, all on a single chip. The Mac M1 can run software created for the older Intel Mac's using an emulation layer called Rosetta). To leverage the new M1 chip from Python, you must use a special Python distribution called Miniforge. Miniforge replaces other Python distributions that you might have installed, such as Anaconda or Miniconda. Apple instructions suggest that you remove Anaconda or Miniconda before installing Miniforge. Because the Mac M1 is a very different architecture than Intel, the Miniforge distribution will maximize your performance. Be aware that once you install Miniforge, it will become your default Python interpreter.

Install Miniforge
There are a variety of methods for installing Miniforge. If you have trouble following my instructions, you may refer to this installation process, upon which I base these instructions.

I prefer to use Homebrew to install Miniforge. Homebrew is a package manager for the Mac, similar to yum or apt-get for Linux. To install Homebrew, follow this link and copy/paste the installation command into a Mac terminal window.

Once you have installed Homebrew, I suggest closing the terminal window and opening a new one to complete the installation.

Next, you should install the xcode-select command-line utilities. Use the following command to install:

xcode-select --install
If the above command gives an error, you should install XCode from the App Store.

You will now use Homebrew to install Miniforge with the following command:

brew install miniforge
You should note which directory

Initiate Miniforge
Run the following command to initiate your conda base environment:

conda init
This will set the python PATH to the Miniforge base in your profile (~/.bash_profile if bash or ~/.zshenv if zsh) and create the base virtual environment.

Make Sure you Have the Correct Python (when things go wrong)
Sometimes previous versions of Python might have been installed, and when you attempt to run the install script below you will recieve an error:

Collecting package metadata (repodata.json): done
Solving environment: failed

ResolvePackageNotFound: 
  - tensorflow-deps
To verify that you have the correct Python version registered, close and reopen your terminal window. Issue the following command:

which python
This command should respond with something similar to:

/opt/homebrew/Caskroom/miniforge/base/bin/python
The key things to look for in the above response are "homebrew" and "miniforge". If you see "anaconda" or "miniconda" your path is pointing to the wrong Python. You will need to modify your ".zshrc", make sure that the three Python paths match the path that "brew" installed it into earlier. Most likely your "miniforge" is installed in one of these locations:

/usr/local/Caskroom/miniforge/base
/opt/homebrew/Caskroom/miniforge/base
More info here.

Install Jupyter and Create Environment
Next, lets install Jupyter, which is the editor you will use in this course.

conda install -y jupyter
We will actually launch Jupyter later.

First, we deactivate the base environment.

conda deactivate
Next, we will install the Mac M1 tensorflow-apple-metal.yml file that I provide. Run the following command from the same directory that contains tensorflow-apple-metal.yml.

conda env create -f tensorflow-apple-metal.yml -n tensorflow
Issues Creating Environment (when things go wrong)
Due to some recent changes in one of the TensorFlow dependancies you may get the following error when installing the YML file.

Collecting grpcio
  Using cached grpcio-1.34.0.tar.gz (21.0 MB)
    ERROR: Command errored out with exit status 1:
If you encounter this error, remove your environment, define two environmental variables, and try again:

conda env remove --name tensorflow
export GRPC_PYTHON_BUILD_SYSTEM_OPENSSL=1
export GRPC_PYTHON_BUILD_SYSTEM_ZLIB=1
conda env create -f tensorflow-apple-metal.yml -n tensorflow
Activating New Environment
To enter this environment, you must use the following command:

conda activate tensorflow
For now, let's add Jupyter support to your new environment.

conda install nb_conda
Register your Environment
The following command registers your tensorflow environment. Again, make sure you "conda activate" your new tensorflow environment.

python -m ipykernel install --user --name tensorflow --display-name "Python 3.9 (tensorflow)"
Testing your Environment
You can now start Jupyter notebook. Use the following command.

jupyter notebook
You can now run the following code to check that you have the versions expected.

# What version of Python do you have?
import sys

import tensorflow.keras
import pandas as pd
import sklearn as sk
import tensorflow as tf

print(f"Tensor Flow Version: {tf.__version__}")
print(f"Keras Version: {tensorflow.keras.__version__}")
print()
print(f"Python {sys.version}")
print(f"Pandas {pd.__version__}")
print(f"Scikit-Learn {sk.__version__}")
gpu = len(tf.config.list_physical_devices('GPU'))>0
print("GPU is", "available" if gpu else "NOT AVAILABLE")
Init Plugin
Init Graph Optimizer
Init Kernel
Tensor Flow Version: 2.5.0
Keras Version: 2.5.0

Python 3.9.7 | packaged by conda-forge | (default, Sep 29 2021, 19:24:02) 
[Clang 11.1.0 ]
Pandas 1.3.4
Scikit-Learn 1.0.1
GPU is available
