# Developing Abel Theorem

## With nix.

1. Install nix:
 - To install it on a single-user unix system where you have admin rights, just type:
     > sh <(curl https://nixos.org/nix/install)

      You should run this under your usual user account, not as root. The script will invoke `sudo` as needed.

      For other configurations (in particular if multiple users share the machine) or for nix uninstallation, go to the [appropriate section of the nix manual](https://nixos.org/nix/manual/#ch-installing-binary).

  - You need to **log out of your desktop session and log in again** before you proceed to step 2.

  - Step 1. only need to be done once on a same machine.

2. Open a new terminal. Navigate to the root of the Abel repository. Then type:
   > nix-shell
   
   This will open a (nix) shell with the right work environment. It particular, nix
   will download and build the required packages: wait until you get a shell.
   
   You need to type this command every time you work in a new terminal.
   
   You can call `nixEnv` after you start the nix shell to see your work environment
     
     (or call `nix-shell` with option `--arg print-env true`).

3. You are now in the correct work environment. You can do
   > make

   and do whatever you are accustomed to do with Coq. 

4. You can edit files using:
   > emacs
   - If you are using emacs with proof general, make sure you empty your
     `coq-prog-name` variables and any other proof general options that
     used to be tied to a previous local installation of Coq.
   - If you do not have emacs installed, you can go back to
     step 2. and call `nix-shell` with the following option
     > nix-shell --arg withEmacs true

     instead. Make sure you add the line `(require 'proof-site)` to `$HOME/.emacs`.
