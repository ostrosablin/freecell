# freecell
## Fork with improvements over ncurses freecell implementation by Linus Akesson

![freecell](https://github.com/tmp6154/freecell/blob/master/doc/screenshot.png?raw=true "freecell")

This is fork of freecell-1.0 by Linus Akesson:

https://www.linusakesson.net/software/freecell.php

### Key improvements in this fork:
* Add an -e (--exitcode) option to return non-zero exit code on quitting unsolved deal. This allows to easily implement, e.g. deal autoincrement after deal is solved.

You can do this before first run:

    echo 0 > ~/DEAL

And then, with following command, you'll be able to start with deal #0 and continue with next numbered deals as you solve more deals. If you decide to quit an unsolved deal, next time you launch you will continue with that unsolved deal.
    
    cd && DEAL=$(cat ~/DEAL) && freecell -S -e $DEAL && DEAL=$((DEAL+1)) && echo $DEAL >| ~/DEAL

* Card notation was changed to be more readable, and also fc-solve compatible. E.g. 13s is now KS, 12h is now QH. I find it less confusing.
* Improved formula for supermoves/metamoves. Original implementation considered each empty cascade as one more freecell, while more correct formula is (M^2)*(N+1), which allows to move much more cards at once as long as you have enough empty cascades and freecells. This allows to do fewer tedious explicit moves and most modern FreeCell implementations have this out-of-box.
* Step-by-step metamove animation. You can see exactly how metamoves are performed. If you don't want animations, though, you can specify -i (--instant) option. Also, you can adjust animation delay (in microseconds) via -d (--delay) option.
* Accidental quit protection. Now hitting "q" doesn't instantly terminate the game, instead it asks you to hit "q" again if you really meant to quit game.
* Option -H (--highlight) to highlight next card of a suit to move to foundation, so that you won't have hard time tracking down the aces at the beginning of game.
* Supports solvability check via fc-solve. Enable fc-solve support with -S (--solver) option. No more getting stuck with dead-end unsolvable configurations for hours. After each move, solver will check and report whether this board is still solvable, or if it is game over and it's time to undo or restart.

This requires to install fc-solve. You can install it on Debian/Ubuntu based distros with following command.

    sudo apt-get install freecell-solver-bin

## Original description

This is freecell, a console (ncurses) version of the popular solitaire
game.

Please refer to the file 'INSTALL' for installation instructions. Once the game
has been installed, simply run it and type '?' for gameplay instructions (or
read the man page).

Modern freecell was invented by Paul Alfille in 1978.

This implementation of freecell was written from scratch by Linus Akesson
<linus@linusakesson.net> in 2007.

See also http://en.wikipedia.org/wiki/Freecell
