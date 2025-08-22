To reproduce https://github.com/astral-sh/setup-uv/issues/535:

```
act --container-architecture linux/amd64

...

[default/install] ⭐ Run Set up job
[default/install] 🚀  Start image=catthehacker/ubuntu:act-latest
[default/install]   🐳  docker pull image=catthehacker/ubuntu:act-latest platform=linux/amd64 username= forcePull=true
[default/install]   🐳  docker create image=catthehacker/ubuntu:act-latest platform=linux/amd64 entrypoint=["tail" "-f" "/dev/null"] cmd=[] network="host"
[default/install]   🐳  docker run image=catthehacker/ubuntu:act-latest platform=linux/amd64 entrypoint=["tail" "-f" "/dev/null"] cmd=[] network="host"
[default/install]   🐳  docker exec cmd=[node --no-warnings -e console.log(process.execPath)] user= workdir=
[default/install]   ✅  Success - Set up job
[default/install]   ☁  git clone 'https://github.com/astral-sh/setup-uv' # ref=v6.6.0
[default/install] ⭐ Run Main Install the latest version of uv
[default/install]   🐳  docker cp src=/Users/gabe/.cache/act/astral-sh-setup-uv@v6.6.0/ dst=/var/run/act/actions/astral-sh-setup-uv@v6.6.0/
[default/install]   🐳  docker exec cmd=[/opt/acttoolcache/node/18.20.8/x64/bin/node /var/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js] user= workdir=
| /run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:113176
| webidl.is.File = webidl.util.MakeTypeAssertion(File)
|                                                ^
|
| ReferenceError: File is not defined
|     at 47879 (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:113176:48)
|     at __nccwpck_require__ (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:135576:43)
|     at 73168 (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:110888:20)
|     at __nccwpck_require__ (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:135576:43)
|     at 60660 (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:106127:5)
|     at __nccwpck_require__ (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:135576:43)
|     at 99051 (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:110229:90)
|     at __nccwpck_require__ (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:135576:43)
|     at 54398 (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:106855:5)
|     at __nccwpck_require__ (/run/act/actions/astral-sh-setup-uv@v6.6.0/dist/setup/index.js:135576:43)
|
| Node.js v18.20.8
[default/install]   ❌  Failure - Main Install the latest version of uv [1.111147333s]
[default/install] exitcode '1': failure
[default/install] ⭐ Run Complete job
[default/install]   ✅  Success - Complete job
[default/install] 🏁  Job failed
Error: Job 'install' failed
```
