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
  'trusted_proxies' => array('10.0.0.0/8'),
  'forwarded_for_headers' => array('HTTP_X_FORWARDED_FOR'),
```

This will allow nextcloud to log IPs properly and provide working links and redirects.

## License

Copyright (c) 2019 James Andariese

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.