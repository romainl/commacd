# The purpose of this fork was only to silence `cd`. Nothing more, nothing less.

---

# commacd [![Build Status](https://travis-ci.org/shyiko/commacd.svg)](https://travis-ci.org/shyiko/commacd)

A faster way to move around (Bash 3+).

> While going through "Usage" section please keep in mind that `commacd` is NOT an [autojump](https://github.com/joelthelion/autojump)/[z](https://github.com/rupa/z)/[fasd](https://github.com/clvv/fasd) alternative nor they are mutualy exclusive. It doesn't track history, write any logs, nothing like that. It really is just an improved `cd`.

## Installation

```sh
curl https://raw.githubusercontent.com/shyiko/commacd/master/commacd.bash -o ~/.commacd.bash && \
  echo "source ~/.commacd.bash" >> ~/.bashrc
```

> On OS X you'll need to make sure ~/.bashrc is sourced from ~/.bash_profile (http://ss64.com/osx/syntax-bashrc.html). 

## Usage

`commacd` introduces three aliases: `,` (for jumping forward), `,,` (backward) and `,,,` (backward+forward):

```sh
~$ , des
  => cd Desktop

# move through multiple directories
~$ , /u/l/ce
  => cd /usr/local/Cellar

# allow me to choose directory in case of ambiguous pattern (= multiple choices)
~$ , d
  => 1 Desktop
     2 Downloads
     : <type index of the directory to cd into>

# given two directories jdk7 and jdk8 on the Desktop, cd into jdk8 without hitting 
# interactive mode (the one shown above)
~/github$ , ~/d/j*8
  => cd ~/Desktop/jdk8

# cd into directory having 'esk' somewhere in its name
~/github$ , ~/*esk
  => cd ~/Desktop

# go all the way up to the project root (in this case, the one that has .git in it)
~/github/lorem/src/public$ ,,
  => cd ~/github/lorem

# cd into to the first (closest) parent directory named g*
~/github/vimium/src/public$ ,, g
  => cd ~/github

# substitute jekyll with ghost
~/github/jekyll/test$ ,, jekyll ghost
  => cd ~/github/ghost/test

# jump to some other project (in this case, located in ~/github)
~/github/rook/src/public$ ,,, m*binlog
  => cd ~/github/mysql-binlog-connector-java
```

As a bonus, all three aliases support `<Tab>` expansion (try `, /u/lo<Tab>`) and can be combined with other tools (e.g. ``ls `, /u/lo` ``). 

For more information, please refer to http://shyiko.com/2014/10/10/commacd/.

## Development

```sh
make # lint sources and run tests 
```

## License

[MIT License](http://opensource.org/licenses/mit-license.php)

