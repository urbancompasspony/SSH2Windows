# SH_Commands

Some examples to handle some strings and parameters.

## Catch Windows Uptime and stores under a var:

var1=$(ssh USER@IP_OF_SYSTEM "net statistics workstation" | awk 'NR==4' | awk '{print $3, $4}')

##
