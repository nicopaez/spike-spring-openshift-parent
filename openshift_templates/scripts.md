# Create the project
oc new-project myproject --display-name="myproject"

# Create the app
oc new-app nicopaez/springping:latest+nicopaez/configserver:latest

oc new-app reactapp:latest+configserver:latest

# Create the app
oc expose svc/springping

# Update an image and trigger a new deploy based on it
oc import-image springping