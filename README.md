# puppet-controlrepo

This project serves as a complete starter kit for your Puppet controlled infrastructure. It is feature filled with everything you ever wanted but never had; such as *Hiera*, *R10K*, *Roles and Profiles framework*, and *Vagrant*.

## Project Goals

  1. Whitelabel so that anyone can use this project from a class demo all the way to a full blown Fortune 500 datacenter
  2. Compatible with all operating systems (needs work)
  3. Stay current with all the best practices

## Installation and Usage

### Prerequisites
 
#### Enable SSH-Agent Forwarding
SSH Agent Forwarding allows you to use your private key from your local machine on your vagrant box, for use with private repos where you need to authenticate as yourself. 

1.Go to `~/.ssh/config` and add this to the top of your config file(If you do not have one please create one):

```
Host *
 ForwardAgent yes
```
2.Now we must add your key to the ssh-agent. You will need to run one of the commands below from your terminal. Please make sure that your private key is available at `~/.ssh/id_rsa`

If you on a Mac run:

```
ssh-add -K ~/.ssh/id_rsa
```
If you are on Linux then:

```
ssh-add ~/.ssh/id_rsa
```
### Usage
  1. Clone the repo
  1. `vagrant up` and watch your new virtual machine get fully provisioned
  1. `vagrant ssh` and have a look around
  1. Now try making a change to some YAML data. Edit [`common.yaml`](hieradata/common.yaml) and add/remove a DNS server, just for fun
  1. `vagrant provision`, now watch the DNS client configuration recieve your change.    

### Setting facter facts for Vagrant to use (i.e. `app_role` or `app_tier`)
  
Use environment variables to set facter facts that get passed to Vagrant.

```
For Command-Center:
$ APP_ROLE=commandcenter-web vagrant provision
Other Examples:
$ APP_ROLE=webserver vagrant provision
or...
$ APP_ROLE=webserver APP_TIER=production vagrant provision

```

## Compatibility

Tested with Puppet v3.8 (open source) on CentOS 6.7. PRs  with modifications for more compatibility are very welcome.

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

Nov 2015: Initial commit


## Credits

[Sean S. King](https://github.com/seanscottking), author

Thanks to [Rob Nelson](http://rnelson0.com). His project [puppetinabox](https://github.com/puppetinabox) was the inspiration for this one.

Thanks to [Craig Dunn](www.craigdunn.org) and [Gary Larizza](http://garylarizza.com) for their broad research on ways to make Puppet not suck.


## License

[See LICENSE.md](LICENSE.md)
