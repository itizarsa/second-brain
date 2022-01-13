# mozilla/node-convict: Featureful configuration management library for Node.js

Source: Website
Status: Unprocessed
URL: https://github.com/mozilla/node-convict

[https://opengraph.githubassets.com/c7f388cd2e7d136963980dbee0902088d009abe581285481ae4cde47ce615306/mozilla/node-convict](https://opengraph.githubassets.com/c7f388cd2e7d136963980dbee0902088d009abe581285481ae4cde47ce615306/mozilla/node-convict)

---

[node-convict](mozilla%20node-convict%20Featureful%20configuration%20mana%20a2bf95285000461e94ca7e7765fa5eaf/node-convict)

# Node-convict

[mozilla%20node-convict%20Featureful%20configuration%20mana%20a2bf95285000461e94ca7e7765fa5eaf/68747470733a2f2f7472617669732d63692e6f72672f6d6f7a696c6c612f6e6f64652d636f6e766963742e7376673f6272616e63683d6d6173746572](mozilla%20node-convict%20Featureful%20configuration%20mana%20a2bf95285000461e94ca7e7765fa5eaf/68747470733a2f2f7472617669732d63692e6f72672f6d6f7a696c6c612f6e6f64652d636f6e766963742e7376673f6272616e63683d6d6173746572)

[mozilla%20node-convict%20Featureful%20configuration%20mana%20a2bf95285000461e94ca7e7765fa5eaf/68747470733a2f2f636f766572616c6c732e696f2f7265706f732f6769746875622f6d6f7a696c6c612f6e6f64652d636f6e766963742f62616467652e7376673f6272616e63683d6d6173746572](mozilla%20node-convict%20Featureful%20configuration%20mana%20a2bf95285000461e94ca7e7765fa5eaf/68747470733a2f2f636f766572616c6c732e696f2f7265706f732f6769746875622f6d6f7a696c6c612f6e6f64652d636f6e766963742f62616467652e7376673f6272616e63683d6d6173746572)

Convict expands on the standard pattern of configuring node.js applications in a way that is more robust and accessible to collaborators, who may have less interest in digging through code in order to inspect or modify settings. By introducing a configuration schema, convict gives project collaborators more **context** on each setting and enables **validation and early failures** for when configuration goes wrong.

This repository is a monorepo for the following packages managed through [Lerna](https://lerna.js.org/).

## Packages

- 
    
    [convict](https://github.com/mozilla/node-convict/blob/master/packages/convict) : the main package
    
- 
    
    [convict-format-with-validator](https://github.com/mozilla/node-convict/blob/master/packages/convict-format-with-validator) the optional package providing the `email`, `ipaddress` and `url` formats
    
- 
    
    [convict-format-with-moment](https://github.com/mozilla/node-convict/blob/master/packages/convict-format-with-moment) : the optional package providing the `duration` and `timestamp` formats
    

## Migrating

- [Migrating from Convict 5 to 6](https://github.com/mozilla/node-convict/blob/master/packages/convict/MIGRATING_FROM_CONVICT_5_TO_6.md)

## Contributing

Read the [Contributing](https://github.com/mozilla/node-convict/blob/master/CONTRIBUTING.md) doc.