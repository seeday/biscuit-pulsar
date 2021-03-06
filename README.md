# Pulsar Biscuit Authentication & Authorization plugins

## Status

Still in development.

Missing: https://github.com/apache/pulsar/issues/5720 to manage pulsar's resources. Currently we can only producer/consume.

## Build & Tests

```bash
# run all tests and build
mvn clean install

# build module like biscuit-pulsar only
mvn clean install -pl biscuit-pulsar

# build without tests
mvn clean install -Dmaven.test.skip=true

# run AuthorizationProviderBiscuitTest in module biscuit-pulsar
mvn clean install -Dtest=AuthorizationProviderBiscuitTest -pl biscuit-pulsar
```

## Configuration

The listed dependencies can be necessary to add to the /lib of pulsar folder as jars:

- biscuit-pulsar
- vavr
- vavr-match
- protobuf
- commons-codec
- biscuit-java
- curve25519-elisabeth

As we are using Maven, you should find all of them in `~/.m2/...`

In your `broker.conf`:

```bash
# Enable authentication
authenticationEnabled=true

# Autentication provider name list, which is comma separated list of class names
authenticationProviders=com.clevercloud.biscuitpulsar.AuthenticationProviderBiscuit

# Enforce authorization
authorizationEnabled=true

# Authorization provider fully qualified class-name
authorizationProvider=com.clevercloud.biscuitpulsar.AuthorizationProviderBiscuit

# Biscuit root signing key
biscuitPublicRootKey=<BiscuitPublicRootKeyHexa>

superUserRoles=admin
```

## Versions

Change version:

```bash
mvn versions:set -DnewVersion=x.y.z-SNAPSHOT
mvn versions:commit
```
