# github_users

Create users from a Github organization or list of users.

This will allow members of your organization to SSH into servers using their own keys.

## Attributes

* `node[github_users][organization]` - Github organization to search for public members
* `node['github_users']['team']` - Github numeric team id to search for members
* `node[github_users][users]` - List of Github users, if you don't want to use the `organization` attribute
* `node[github_users][group_name]` - Group name users will belong to (default `'github'`)
* `node[github_users][group_id]` - Group id users will belong to (default `2157`)
* `node[github_users][allow_sudo]` - Allow passwordless sudo for the users (default `true`)
* `node['github_users'][custom_shells]` - Hash with {user:shell} pairs to override default '/bin/bash' for given users
* `node['github_users']['auth_token']` - Token to be used for authorization to Github
* `node['github_users']['fetch_dotfiles']` - Set to true to search for a users dotfiles repo, clone it into a directory and symlink files from it to his home

## Usage

Include this cookbook in your role or wrapper cookbook.

```
recipe[github_users]
```

Set one of these attributes as you need:

* `[github_users][organization]`
* `[github_users][users]`

## Development

1. Clone this repository
    
    ```
    git clone git@github.com:dustinmm80/github_users_cookbook.git
    ```

2. Install dependencies

    ```
    gem install bundler; bundle install
    ```
    
3. **Write tests for your changes.** We're using test-kitchen and serverspec.

4. Run the tests

    We're using docker to run our integration tests.

    You need to have the environment variable `DOCKER_HOST` set to point to your docker daemon.

    ```
    kitchen converge; kitchen verify
    ```
