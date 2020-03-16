# Overview
Purpose of this repo is to document the steps I had to take to setup my coding environment. I always get it working then forget about it & kick myself for not writing it down when I get a new computer

# Installations

## Python
A lot of times, I work on projects that have different dependencies for python. It used to be really frustrating until I stumbled on pyenv. With pyenv you can install multiple version of python and switch between them whenever you want. You set the global pyenv shim location on your path and then you just run pyenv global <version> and everything else points to that shim location and just works. It's sweet! 

Here's how I set up pyenv: 

1. Install homebrew: https://brew.sh/
2. Install pyenv using homebrew: brew install pyenv

3. Add the lines below to your bash_profile or zprofile (if you're using catalina)

```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

4. run: pyenv install -l to see available versions & pick the one you want
5. run: pyenv install 3.7.6
6. run: pyenv global 3.7.6 to set the global version of python to 3.7.6

This should be it. Source your zprofiile file and then run $ which python. 
The output should show something like this: 
```bash
/Users/<your name>/.pyenv/shims/python
```

### Virtual Environments Installation
I started with virtualenv, moved to virtualenvwrapper, and finally landed on pipenv. It's a little higher level than virtualenv and essentially creates one under the hood anyways.

I've it very useful and like the feature where I pipenv install X and it adds it to a pip file that I can then share. Basically combines pip and virtualenv which you previously had to do seperately

See the installation below: 

1. run pip install pipenv


# Code Editor Setup 
My current favorite editor is VSCode. I chose it because I was tired of switching between different editors for JS, Python, Java, HTML, etc.. It was a huge pain and VSCode has enough plugins to do it all 'good enough'

1. Install VSCode from the website https://code.visualstudio.com/
2. Install the python plugin 
3. Follow the instructions on this link to add the right python path to VSCode: https://github.com/Microsoft/vscode-python/issues/4434#issuecomment-466600591

Basically add this line to your settings.json

```bash
"terminal.integrated.env.osx": {
		"PATH": ""
}
```
Without it, the path wont be the same as the external terminal. This step is also necessary for your virtual environment to show up in the available python interpreters which is described in the next step 

4. run CMD-SHIFT-P to open the command palette, then type in Python: select interpreter
5. Scroll until you find your virtualenv. You can double check the virtual env location py running $which python in the pipenv
