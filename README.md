# context-demo
Creates terraform contexts for Digital Rebar v4.1+
==================================================

Video: https://youtu.be/_e9F_QAAMYg

License Required
----------------

Contexts are a RackN licensed featue of the DRP 4.1+ platform.  Community users with a renewable RackN trial license (free with registration) can create 3 contexts.

Prereqs
-------

You must install the `docker-context` plugin for this training.  You must also install Docker.

Then, create TWO docker containers as follows:

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
    
Install Content
---------------

To use this sample code, bundle and upload the content

  ::

	drpcli contents bundle context-demo.yaml
	drpcli contents upload context-demo.yaml 


Create a Machine with `runner` BaseContext
------------------------------------------

To test the Context, create a machine that uses the `runner` as the BaseContext with the following command: `drpcli machines create '{"Name":"demo", "Meta":{"BaseContext":"runner"}}'`


Running Terraform
-----------------

To use the AWS plan, you must set your credentials.  The simplest way to do this is to include `aws/access-key` and `aws/secret-key` in your `global` profile with the correct values.

Once these values are defined, you can start the plan by setting the demo machine to use the `terraform-create` workflow.  For example `drpcli machines update Name:demo '{"Workflow":"terraform-create"}'`

Note: TF state files will be automatically retained in the DRP Files store.