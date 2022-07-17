1. Setting up a repository (git init / git clone / git config) 
        A Git repository is a virtual storage of your project. It allows you to save versions of your code, which you can access when needed. 
                Cloning an existing repository: git clone
                        $ git clone <repo url>
                Initializing a new repository: git init
                        $ git init  
                                Executing this command will create a new .git subdirectory in your current working directory. This will also create a new main branch. 
                        $ git init <project directory>
                                Pointing git init to an existing project directory will execute the same initialization setup as mentioned above, but scoped to that project directory.
                Saving changes to the repository: git add and git commit
                        Create a new file CommitTest.txt
                        $ git add CommitTest.txt 
                        $ git commit -m "added CommitTest.txt to the repo"

2. Bare vs. cloned repositories ($ git push  <remote_name> <local_branch_name>) 
        $ git clone
                If you used git clone in the previous "Initializing a new Repository" section to set up your local repository, your repository is already configured for remote collaboration. git clone will automatically configure your repo with a remote pointed to the Git URL you cloned it from. This means that once you make changes to a file and commit them, you can git push those changes to the remote repository.
                Cloning to a specific folder
                $ git clone <repo> <directory>
                        Clone the repository located at ＜repo＞ into the folder called ~＜directory＞! on the local machine.
                $ git clone --branch <tag> <repo>
                        Clone the repository located at ＜repo＞ and only clone the ref for ＜tag＞.
                $ git clone -branch new_feature git://remoterepository.git
                        This above example would clone only the new_feature branch from the remote Git repository.
        $ git init
                If you used git init to make a fresh repo, you'll have no remote repo to push changes to. A common pattern when initializing a new repo is to go to a hosted Git service like Bitbucket and create a repo there. The service will provide a Git URL that you can then add to your local Git repository and git push to the hosted repo. Once you have created a remote repo with your service of choice you will need to update your local repo with a mapping.
                        Configuration & set up: git config
                                $ git remote add <remote_name> <remote_repo_url>
                                        $ git remote add origin https://github.com/Subrata-Rajak/Git-pushing.git
                                        $ git remote -v (check whether your remote origin is defined)
                                        This command will map remote repository at  to a ref in your local repo under . Once you have mapped the remote repo you can push local branches to it.
                                $ git push -u <remote_name> <local_branch_name>
                                        This command will push the local repo branch under < local_branch_name > to the remote repo at < remote_name >.

                        In addition to configuring a remote repo URL, you may also need to set global Git configuration options such as username, or email. The git config command lets you configure your Git installation (or an individual repository) from the command line. This command can define everything from user info, to preferences, to the behavior of a repository.

                                Git stores configuration options in three separate files, which lets you scope options to individual repositories (local), user (Global), or the entire system (system):

                                Local: /.git/config – Repository-specific settings.
                                Global: /.gitconfig – User-specific settings. This is where options set with the --global flag are stored.
                                System: $(prefix)/etc/gitconfig – System-wide settings.
                                Define the author name to be used for all commits in the current repository. Typically, you’ll want to use the --global flag to set configuration options for the current user.

                                git config --global user.name <name>
                                Define the author name to be used for all commits by the current user.

                                Adding the --local option or not passing a config level option at all, will set the user.name for the current local repository.

                                git config --local user.email <email>
                                Define the author email to be used for all commits by the current user.

                                git config --global alias.<alias-name> <git-command>
                                Create a shortcut for a Git command. This is a powerful utility to create custom shortcuts for commonly used git commands. A simplistic example would be:

                                git config --global alias.ci commit
                                This creates a ci command that you can execute as a shortcut to git commit. To learn more about git aliases visit the git config page.

                                git config --system core.editor <editor>
                                Define the text editor used by commands like git commit for all users on the current machine. The < editor > argument should be the command that launches the desired editor (e.g., vi). This example introduces the --system option. The --system option will set the configuration for the entire system, meaning all users and repos on a machine. For more detailed information on configuration levels visit the git config page.

                                git config --global --edit
                                Open the global configuration file in a text editor for manual editing. An in-depth guide on how to configure a text editor for git to use can be found on the Git config page.

# source: https://www.atlassian.com/git/tutorials/setting-up-a-repository