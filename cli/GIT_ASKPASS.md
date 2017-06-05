- I opened https://github.com/trilbymedia/grav-plugin-git-sync/issues/53
and explained the issue I have with the current spproach.

Additional resource:

- https://stackoverflow.com/questions/39275038/auto-answer-ssh-copy-id-in-shell-script
- http://andre.frimberger.de/index.php/linux/reading-ssh-password-from-stdin-the-openssh-5-6p1-compatible-way/
- https://git-scm.com/docs/git-credential-cache

current approach, just the code, no explaination:

in a clone of a private repo store your username:
```
[credential "https://github.com"]
	username = me
```

prepare `/abs/path/to/script.sh`:
```
#!/usr/bin/env bash
echo $PASS
```

to be able to run the following inside of bash for a private repo:  
`PASS=12345 GIT_ASKPASS=/abs/path/to/script.sh setsid -w git fetch`


could of course get more advanced and compotible,
and maybe there is even a way to avoid putting the password in the shell command.

The https://git-scm.com/docs/git-credential-cache thing can be used to only be required to do the trick once and be able to run as may git commands afterwards as long as we are in the timeout. (can also be disabled manually when done.) 
