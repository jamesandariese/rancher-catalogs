# nextcloud-rancher

Nextcloud catalog template for Rancher

IMPORTANT: This template is designed for distributed storage
(or a single node Rancher installation)

## Data Directory

Once installed, there will be a persistent data directory on disk at the place of your choosing.

Nextcloud logs into the data directory.

Config files are next to the data directory and should be modified for your installation after
the first start.  In particular, you will want to configure the following:

```
  'trusted_domains' =>
  array (
    0 => 'nextcloud.mydomain.tld',
  ),
  /* 'overwriteprotocol' => 'https', */
  'overwritehost' => 'nextcloud.mydomain.tld',
  'trusted_proxies' => array('10.42.0.0/16'),
  'forwarded_for_headers' => array('HTTP_X_FORWARDED_FOR'),
```

This will allow nextcloud to log IPs properly and provide working links and redirects.

### Distributed Filesystem

The data directory format was designed using GlusterFS.  Any distributed filesystem following POSIX
sematics will work but it must be distributed to all hosts where the db and app are scheduled.

Alternatively, this may be configured to run on a single host utilizing scheduling rules.  You may configure the scheduling rules after the stack is launched in the UI.

### Load Balancer

This is configured with a sample load balancer and no port forwards into the nginx container.  This is because the nginx container will allow a large range of IPs to override the requestor IP which the load balancer takes care of.

You may place a secondary load balancer in front of the container

## License

Copyright (c) 2019 James Andariese

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.