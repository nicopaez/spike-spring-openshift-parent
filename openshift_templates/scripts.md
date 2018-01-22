# Create the project
oc new-project myproject --display-name="myproject"

# Create the app
oc new-app nicopaez/springping:latest+nicopaez/configserver:latest

# Create the app
oc expose svc/springping
