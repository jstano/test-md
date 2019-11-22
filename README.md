
##### Working on storybook docs?

Be sure to install our Intellij plugin to create the template files:  
1. Add our private repository to IntelliJ via Settings -> Plugins -> (Gear Icon) -> 
Manage Plugin Repositories:

   `https://devsupport.unifocus.com/intellijplugins/updatePlugins.xml`

1. Go to the Settings -> Plugins -> Marketplace tab.  In the search box, type:

   `repository:"https://devsupport.unifocus.com/intellijplugins/updatePlugins.xml"`
    
1. There should be a plugin to install named `uf-storybook-docs-<version>`.  Please restart IntelliJ after installing the plugin.

1. Once installed, create a `__docs__` folder in the component source folder next to its `__tests__` folder.

1. Right click on the `__docs__` folder and choose New -> UniFocus Template Storybook Files

1. Provide the name of the component (such as `LocalDateField`) as well as the storybook menu path (such as `Components|Form/LocalDateField`) and 
click OK.

1. You can start writing your docs:
   * **Dos.md**  - This markdown file lists the best practice "DOs" for the component
   * **Donts.md** - This markdown file lists the best practice "DON'Ts" for the component
   * **Overview.md** - This markdown file is for the component's overview text
   * _ComponentName_**.stories.mdx** - This mdx file is for the component's usage stories

##### API Property Table Generation

Storybook docs depends on an api extraction step that produces `page.json` files under `dist/lib/pages`.  The `page.json` files under the `react` 
subfolder contain the api directly related to each component, whereas the `references` folder contains general/shared api types.

To generate the `page.json` files for a component:

* Add a document category to your `<component>Props` and any related properties specific to the component.  It should match the name of your 
component:
```
/** 
 * {@docCategory MyComponent} 
 */
```
* Edit the `tasks/api-docs.js` and make sure the component exists in the `pageGroups/react` 
array.  
* Either rebuild the project using `npm run build` or run `npm run tsc && npm run extract-api`.
 
