# Kickstarters

These are sample plugin projects you can use to kickstart your plugin development.  Simply recursively copy the content of template you want into your project root directory.

> Note: By convention we recommend naming your project root directory the same name as your plugin.  Further by convention you should name your plugin either 'xlr-<PLUGIN_NAME>-plugin' or 'xld-<PLUGIN_NAME>-plugin'.  (Using 'xlr' for XL Release plugins and 'xld' for XL Deploy plugins).

## Initial Preparation

Once you copy the kickstart content into your project root, use your IDE to globally search replace the token 'PLUGINNAME' with the actual name of your plugin.  Also rename any directories called 'PLUGINNAME'.  

> Note: This token is used in many contexts and not all names are valid in all contexts.  For example, you can't have an underscore ('_') in the synthetic.xml plugin namespace (synthetic.xsd) while underscore is valid in python modules and java packages.  It is not required that all places that have PLUGINNAME token have the same value.  Simply change those instances where you plugin name is not valid to something that is valid.

## Kickstarters Available

| Directory | Product | Usecase |
| --------- | ------- | ------- |
| kickstarters/xlr/java-with-itest | XL Release | Java implementation with mock service implementation. |
