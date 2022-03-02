# OWASP ModSecurity Core Rule Set - phpBB Rule Exclusions Plugin

## Description

This plugin contains rule exclusions for [phpBB](https://www.phpbb.com/), the
flat-forum bulletin board software solution, so it can be run flawlessly
togather with OWASP ModSecurity Core Rule Set (CRS).

## Prerequisities

 * CRS version 4.0 or newer (or see "Preparation for older installations" below)

## Installation

Copy all files from `plugins` directory into the `plugins` directory of your CRS
installation.

### Preparation for older installations

 * Create a folder named `plugins` in your existing CRS installation. That
   folder is meant to be on the same level as the `rules` folder. So there is
   your `crs-setup.conf` file and next to it the two folders `rules` and
   `plugins`.
 * Update your CRS rules include to follow this pattern:

```
<IfModule security2_module>

 Include modsecurity.d/owasp-modsecurity-crs/crs-setup.conf

 Include modsecurity.d/owasp-modsecurity-crs/plugins/*-config.conf
 Include modsecurity.d/owasp-modsecurity-crs/plugins/*-before.conf

 Include modsecurity.d/owasp-modsecurity-crs/rules/*.conf

 Include modsecurity.d/owasp-modsecurity-crs/plugins/*-after.conf

</IfModule>
```

_Your exact config may look a bit different, namely the paths. The important
part is to accompany the rules-include with two plugins-includes before and
after like above. Adjust the paths accordingly._

## Testing

After the plugin is enabled, your phpBB instance should work without any
problems possibly caused by CRS (for example, false positives while blocking
requests). If you are still having any problems, please file a new issue on
[github](https://github.com/coreruleset/phpbb-rule-exclusions-plugin).

## License

Copyright (c) 2022 OWASP ModSecurity Core Rule Set project. All rights reserved.

The OWASP ModSecurity Core Rule Set and its official plugins are distributed
under Apache Software License (ASL) version 2. Please see the enclosed LICENSE
file for full details.
