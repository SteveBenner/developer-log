# RubyMine
- RubyMine has **serious** trouble detecting installed gems, to the degree where even if your ruby SDK is properly identified in the IDE settings, and the gem you want is listed there, it STILL won't recognize the library.

	In order to get RubyMine to find the gem, **you need to provide a Gemfile and add the gem there**. As SOON as you do (after one or two seconds) it will detect the library in your code. *Wild*.

- RubyMine **also** has serious trouble with the default Ruby `GEM_HOME` configuration. Even if you define `GEM_HOME` in your shell profiles as, say, using `3.4.1	`, the Ruby interpreter *normalizes* this to `3.4.0`. It does this at the interpeter level, and RubyMine *CANNOT* infer `GEM_HOME` from your shell profiles even if they are properly configured!
	- The difference between `3.4.0` and `3.4.1` is as follows:
		- `3.4.0` represents the **user install location**, which will ***ONLY*** be used to install gems into when using the command `gem install` with the flag `--user-install`.
		- `3.4.1` is where your gems will be stored when running typical `gem install` commands, and for some reason even though I'm currently installing into `~/.rubies`, it is known as the **system install location**.
	- The **solution** is to add your Ruby interpreter with a custom environment, as specified [here][0].

	
[0]: https://www.jetbrains.com/help/ruby/2024.3/configuring-language-interpreter.html?ruby.sdk.custom.configurator&keymap=macOS#add_local_configurator