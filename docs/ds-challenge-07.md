## Challenge-07: Devfile Inheritance

### Scenario

As the number of projects increases, curation of individual devfiles can become a more taxing task.  To help combat this, we can make use of inheritance in devfiles.  In doing so, actual project devfiles become much simpler.  They are used to articulate only the differences from the parent devfile instead of defining the whole workspace.

The parent devfile can be hosted internally or you can leverage the [Devfile Registry](https://registry.devfile.io/viewer)

![ ](.img/devfile_registry.png)

### Set Up + verification

The main ways to refer to a parent devfile is by id or uri.  The id reference method is used to specify a devfile from a registry

```yaml
schemaversion: 2.2.0
metadata:  
  name: my-project-dev
parent:  
  id: nodejs  
  registryUrl: https://registry.devfile.io/  
  version: 2.0.0
```

The uri method is used when the parent devfile is hosted on a HTTP server.

```yaml
schemaversion: 2.2.0
metadata:  
  name: my-project-dev
parent:  
  uri: https://raw.githubusercontent.com/devfile/registry/main/stacks/nodejs/devfile.yaml
```

After referencing a parent devfile, you may customize your devfile by overriding configuration from the parent devfile or adding new config elements.

```yaml
schemaVersion: 2.0.0
metadata:
  name: with-parent
parent:
  uri: https://raw.githubusercontent.com/che-incubator/devworkspace-api/proposal-25-variant-1-define-stacks/devfile-support/samples/nodejs-stack.devfile.yaml
  projects:
    - name: example
      git:
        checkoutFrom:
          revision: 'mybranch'
commands:

- id: sayhello
  exec:
    label: Say Hello
    commandLine: echo "hello"
    component: nodejs
```

#### Using this information:

* Inspect the parent devfile from  from:

```http
  http://devfile-srvr-devfile-srvr.apps-crc.testing/quarkus-quickstart.devfile.yaml
```

* ### Success Criteria

* 

* 

### Resources

* [Referring to a parent devfile - devfile.io](https://devfile.io/docs/2.3.0/referring-to-a-parent-devfile)

[back](../README.md)
