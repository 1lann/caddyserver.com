---
title: shutdown
type: docs
directive: true
---

shutdown executes a command when the server exits. This is useful for performing cleanup or stopping a background process like php-fpm. (Also see [startup](/docs/startup).)

Each command that is executed at shutdown is blocking. The output and error of the command go to stdout and stderr, respectively. There is no stdin.

Note that shutdown commands will not execute if Caddy is force-terminated, for example, by using a "Force Quit" feature provided by your operating system. However, a typical SIGINT (Ctrl+C) will allow the shutdown commands to execute.

Even if this directive is shared by more than one host, the command will only execute once.

### Syntax

<code class="block"><span class="hl-directive">shutdown</span> <span class="hl-arg"><i>command</i></span></code>

*   **command** is the command to execute; it may be followed by arguments

### Examples

Stop php-fpm when the server quits:

<code class="block"><span class="hl-directive">shutdown</span> <span class="hl-arg">/etc/init.d/php-fpm stop</span></code>
