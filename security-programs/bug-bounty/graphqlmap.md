# GraphQLmap

GraphQLmap is a scripting engine to interact with a graphql endpoint for pen-testing purposes.

```
 git clone https://github.com/swisskyrepo/GraphQLmap
$ python setup.py install
$ graphqlmap                                                              
   _____                 _      ____  _                            
  / ____|               | |    / __ \| |                           
 | |  __ _ __ __ _ _ __ | |__ | |  | | |     _ __ ___   __ _ _ __  
 | | |_ | '__/ _` | '_ \| '_ \| |  | | |    | '_ ` _ \ / _` | '_ \ 
 | |__| | | | (_| | |_) | | | | |__| | |____| | | | | | (_| | |_) |
  \_____|_|  \__,_| .__/|_| |_|\___\_\______|_| |_| |_|\__,_| .__/ 
                  | |                                       | |    
                  |_|                                       |_|    
                                         Author:Swissky Version:1.0
usage: graphqlmap.py [-h] [-u URL] [-v [VERBOSITY]] [--method [METHOD]] [--headers [HEADERS]] [--json [USE_JSON]] [--proxy [PROXY]]

optional arguments:
  -h, --help           show this help message and exit
  -u URL               URL to query : example.com/graphql?query={}
  -v [VERBOSITY]       Enable verbosity
  --method [METHOD]    HTTP Method to use interact with /graphql endpoint
  --headers [HEADERS]  HTTP Headers sent to /graphql endpoint
  --json [USE_JSON]    Use JSON encoding, implies POST
  --proxy [PROXY]      HTTP proxy to log requests
```

{% embed url="https://github.com/swisskyrepo/GraphQLmap" %}
