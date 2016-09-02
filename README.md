# PHP Vagrant boilerplate

This is a simple boilerplate that installs a Vagrant box with ubuntu/php, this to avoid local installations of php for exercise purposes and better cross platform compatibility (less hassle). Specifically made for the Linnaeus University course 1DV610 - Introduction to Software Quality with setup instructions for PhpStorm 2016.2.

## Install
Make sure you have the following installed on your system:
* VirtualBox [https://www.virtualbox.org/](https://www.virtualbox.org/)
* Vagrant [https://www.vagrantup.com/](https://www.vagrantup.com/)
* PhpStorm [https://www.jetbrains.com/phpstorm/](https://www.jetbrains.com/phpstorm/)

## Get the repo and init Vagrant

1. Clone (`git clone https://github.com/daalsmark/php-vagrant-boilerplate.git your-exercise-folder-name`) to create your exercise folder. 

2. Go to the newly created folder and start the virtual machine using `vagrant up` in the terminal

## Configure PhpStorm 2016.2 

Configure a remote php interpreter and remote web server (so the built in one is not used). 

1. Start PhpStorm and make a project from the folder you created. Make sure Vagrant is still running the guest.

2. Go to "File" -> "Settings" in the menu. Go to "Languages & Frameworks" -> "PHP".

3. Click on the three dots to the right of the `<no interpreter>` text (may say 'PHP 7' or similar if you have a local installation since before).

4. Click on the "+" button in the top left corner. Click on "remote".

5. Click on Vagrant to the left in the dialogue and it will automatically find your guest installation. Click OK to save and click Yes on any SSH-key questions.

6. Check that PHP language level and interpreter is the same in the dialouge windows (5.5 for both). Click OK to close.

7. Now we will setup a deploy environment to enable browser preview on remote server forcing PhpStorm not to use the built-in server. Go to "File" -> "Settings". Go to "Build, Execution, Deployment" -> "Deployment".

8. Click on the "+" button in the top left.

9. Name to remote server (Vagrant Web Server for example). Choose "Local or mounted folder". Click OK.

10. Change `http://localhost` to `http://localhost:8080` as 8080 is the guest port being used for the remote web server.

11. Go to the "Mappings" tab. Change "Local path:" to point to the `exercise` folder in the newly created exercise project.

12. Add a `/` in the "Web path on server" field. Click OK to close.

12. We are now finished and will check that everything works. Go to the `index.php` file in the exercise folder and right click and choose "Open in Browser" and your prefered browser. You should now see the interpreted php-file on the remote server. (`http://localhost:8080/index.php`)
