Upon trying to run a ruby/rails:

```sh
Could not load OpenSSL.
You must recompile Ruby with OpenSSL support or change the sources in your Gemfile from 'https' to 'http'. Instructions for compiling with OpenSSL using RVM are available at rvm.io/packages/openssl.
```

After much googling, reinstalling, recompiling with no luck, this series of actions worked:

1. get latest ruby
1. install openssl
1. reinstall target ruby with `--with-openssl-dir` flag

In my case:
```sh
rvm get latest
brew update
brew install openssl
rvm reinstall 2.2.10 --with-openssl-dir=`brew --prefix openssl`
```