# Othello
Deployment script for Reversi application server.

Please note that this is only testes on a Debian local environment and a Debian target.
This script will not work on any non-Linux environment.

#What does it do
Othello deploys your C# application server on the target of your choice, like an acceptance environment.
It does this in the following way:
  * runs `dotnet publish` locally.
  * zips the output
  * sends the zipped output to your target
  * moves the old deployment currently in /current to /old_releases
  * puts the zipped output in /current
  * unzips the output and removes the zip
  * if there are more old releases than allowed, removes the oldest release
  * kills the running application server, if any
  * starts the new application server
  * deletes the zipped output locally
 
#How to use
Simply run `othello` in the folder containing your `.csproj` file.

#How to install and setup
1. clone this repo on your local Debian machine. `git clone https://github.com/HarmVanDerVegt/Othello`
2. run `chmod +x othello`
3. `mv othello /bin`
4. install Ruby. `apt install ruby-full`
5. install bundler, the Ruby package manager. `gem install bundler`
6. edit your OthelloFile.yml with your hostname, user and directory settings.
7. create the directory you've entered in your OthelloFile on your server.
8. in your directory create a folder called `new`
9. give you user rights to this folder. `sudo chmod -R <user>:<user> <directory>/new
10. Run othello in your local project folder.
