# context-demo
creates terraform contexts for Digital Rebar v4.1+


This example REQUIRES creating TWO docker containers as follows:

  ::

    rm dockerfile
    cp terraform-dockerfile dockerfile
    docker build -t digitalrebar/terraform .

    rm dockerfile
    cm runner-dockerfile dockerfile
    docker build -t digitalrebar/runner .

    rm dockerfile

After these instructions, Docker will have images that are needed by the runner
and terraform contexts.
    
