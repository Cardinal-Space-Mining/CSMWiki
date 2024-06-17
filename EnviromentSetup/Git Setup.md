1. Obtain a github account from [here](https://www.github.com)
2. Ask CSM Controls Lead to add you to the github organization found [here](https://github.com/Cardinal-Space-Mining)
	1. Note for future Admins: the CSM github admin account (`csmc-isu`) is linked to the admin club Gmail account, the 2FA login info and recovery codes can be found in the admin Teams channel. The password can be found in the admin password docs. 
3. Generate a personal access token
	1. Setting found under:
		1. Settings
			1. Developer Settings
				1. Personal Access Tokens
					1. Tokens (classic)
						1. Generate New Token (classic)
	2. Make sure the `repo` option is clicked
	3. If you are an CSM admin, make sure the `admin:*` options are selected if you plan to do admin things
4. Tell git to store login credentials
	1. ````git config --global credential.helper store````
5. Config Username
	1. `git config --global user.name "FIRST_NAME LAST_NAME"`
6. Config Email
	1. `git config --global user.email "MY_NAME@example.com"`
7. Pull a restricted CSM Repo
	1. `git clone https://github.com/Cardinal-Space-Mining/PurposefulyPrivateRepoForGitSetup.git`
8. When prompted for username and password, provide your git username and your recently generated personal access token