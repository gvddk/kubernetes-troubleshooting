# If you use zsh or bash shells, there's a little utility(https://github.com/jonmosco/kube-ps1) that will add the current kubernetes context your to prompt.

```
with kube-ps1 instsalled, you can't forget which context you are in.

source "/usr/local/opt/kube-ps1/share/kube-ps1.sh"
PS1="[$(kube_ps1)]$"
kubectx cloudnativecontext

```