# Python

## gunicorn
### start

### signal
```shell
kill -s USR1 PID
```
#### Master process
- `QUIT`, `INT`: Quick shutdown
- `TERM`: Graceful shutdown. Waits for workers to finish their current requests up to the graceful_timeout.
- `HUP`: Reload the configuration, start the new worker processes with a new configuration and gracefully shutdown older workers. If the application is not preloaded (using the preload_app option), Gunicorn will also load the new version of it.
- `TTIN`: Increment the number of processes by one
- `TTOU`: Decrement the number of processes by one
- `USR1`: Reopen the log files
- `USR2`: Upgrade Gunicorn on the fly. A separate TERM signal should be used to kill the old master process. This signal can also be used to use the new versions of pre-loaded applications. See Upgrading to a new binary on the fly for more information.
- `WINCH`: Gracefully shutdown the worker processes when Gunicorn is daemonized.
#### Worker process
Sending signals directly to the worker processes should not normally be needed. If the master process is running, any exited worker will be automatically respawned.

- `QUIT`, `INT`: Quick shutdown
- `TERM`: Graceful shutdown
- `USR1`: Reopen the log files

#### Reload the configuration
- The `HUP` signal can be used to reload the Gunicorn configuration on the fly.


[详见](http://docs.gunicorn.org/en/stable/signals.html)
