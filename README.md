## 1. Installing Hyperledger Composer Development Tools

**Note:** Check your node version ```nvm --version ```. If you are not using node version 8.11 some of the composer commands won't run correctly. Switch node versions using ```nvm use 8```.

**Note:** You will be installing the latest version of composer-cli (0.20.5).  If you have an older versions installed, go ahead and remove it by using the command:

```
npm uninstall composer-cli
npm uninstall generator-hyperledger-composer
npm uninstall composer-rest-server
npm uninstall yo
```

* The `composer-cli` contains all the command line operations for developing business networks. To install `composer-cli` run the following command:
```
npm install -g composer-cli@0.20.5
```

* The `generator-hyperledger-composer` is a Yeoman plugin that creates bespoke (e.g. customized) applications for your business network. Yeoman is an open source client-side development stack, consisting of tools and frameworks intended to help developers build web applications. To install `generator-hyperledger-composer` run the following command:
```
npm install -g generator-hyperledger-composer@0.20.5
```

* The `composer-rest-server` uses the Hyperledger Composer LoopBack Connector to connect to a business network, extract the models and then present a page containing the REST APIs that have been generated for the model. To install `composer-rest-server` run the following command:
```
npm install -g composer-rest-server@0.20.5
```

* When combining `Yeoman` with the `generator-hyperledger-composer` component, it can interpret business networks and generate applications based on them. To install `Yeoman` run the following command:
```
npm install -g yo@2.0.5
```

## 2. Starting Hyperledger Fabric

** Note: **
<p>If you have previously used an older version of <strong>Hyperledger Composer</strong> and are now setting up a new install, you may want to kill and remove all previous Docker containers, which you can do with these commands:</p>
<div class="highlight"><pre><code class="language-" data-lang="">
    docker kill $(docker ps -q)
    docker rm $(docker ps -aq)
    docker rmi -f $(docker images -q)
</code></pre></div>


First download the docker files for Fabric in preparation for creating a Composer profile.  Hyperledger Composer uses Connection Profiles to connect to a runtime. A Connection Profile is a JSON document that lives in the user's home directory (or may come from an environment variable) and is referenced by name when using the Composer APIs or the Command Line tools. Using connection profiles ensures that code and scripts are easily portable from one runtime instance to another.

The PeerAdmin card is a special ID card used to administer the local Hyperledger Fabric. In a development installation, such as the one on your computer, the PeerAdmin ID card is created when you install the local Hyperledger Fabric.

The form for a PeerAdmin card for a Hyperledger Fabric v1.0 network is PeerAdmin@hlfv1.  In general, the PeerAdmin is a special role reserved for functions such as:

* Deploying business networks
* Creating, issuing, and revoking ID cards for business network admins*

Start the Fabric and create a Composer profile using the following commands:
```bash
./downloadFabric.sh
./startFabric.sh
./createPeerAdminCard.sh
```

No need to do it now; however as an fyi - you can stop and tear down Fabric using:
```
./stopFabric.sh
./teardownFabric.sh
```
