
# Login
**Command:** `vagrant login`

The login command is used to authenticate with the [HashiCorp's Atlas][hashicorp] server. Logging is only necessary if you're accessing protected boxes or using [Vagrant Share][share].

Logging in is not a requirement to use Vagrant. The vast majority of Vagrant does not require a login. Only certain features such as protected boxes or [Vagrant Share][share] require a login.

The reference of available command-line flags to this command is available below.

### Options
* `--check` - This will check if you're logged in. In addition to outputting whether you're logged in or not, the command will have exit status 0 if you're logged in, and exit status 1 if you're not.

* `--logout` - This will log you out if you're logged in. If you're already logged out, this command will do nothing. It is not an error to call this command if you're already logged out.

* `--token` - This will set the Atlas login token manually to the provided string. It is assumed this token is a valid Atlas access token.

## Examples

Securely authenticate to Atlas using a username and password:
```
$ vagrant login
# ...
Atlas username:
Atlas password:
```
Check if the current user is authenticated:
```
$ vagrant login --check
You are already logged in.
```
Securely authenticate with Atlas using a token:
```
$ vagrant login --token ABCD1234
The token was successfully saved.
```

[hashicorp]: https://atlas.hashicorp.com/
[share]: http://docs.vagrantup.com/v2/share/