1. AEM Architecture:
    Custom App modules
    AEM Modules
    Sling Content Delivery
    CRX Content Repo
    CQSE(Servle Engine)
  JAVA Run Time
  OSGI framework
  
      - Adobe Experience Manager (AEM) is a Java web application and therefore requires a server-side Java Runtime Environment (JRE).
      - Granite Platform
        - Granite is Adobe's open web stack. It forms the technical foundation on which AEM is built.
      - OSGI Framework
          - OSGi is a dynamic software component system for Java. In an OSGi-based system, an application is composed of an assemblage of components, called bundles in OSGi terminology, which can be dynamically installed, started, stopped and uninstalled at runtime, without shutting down and restarting the entire application.In a running AEM instance, bundle management is provided through the AEM Web Console at http://:/system/console/bundles.
      - Servlet Engine
          - In a quickstart installation, the built-in CQSE servlet engineruns as a bundle within the OSGi framework. In a war file installation servlet handling is delegated to a third-party application server.AEM includes a built-in servlet engine (CQSE) which runs as a bundle within the OSGi framework when AEM is deployed via the standalone quickstart jar file.
      - JCR Content Repo
          - All data within AEM is stored in the built-in CRX content repository, which is an implementation of the Java Content Repository Specification (JCR). All data in AEM is stored in its built-in content repository.
      The repository built into AEM is called CRX. CRX is Adobe's implemention of the Content Repository Specification for Java Technology 2.0, an official standard published through the Java Community Process as JSR-238 (version 1.0 was known as JSR-170)
      - Sling Content Delivery
        - AEM is built using Sling, a Web application framework based on REST principles that provides easy development of content-oriented applications. Sling uses a JCR repository, such as Apache Jackrabbit, or in the case of AEM, the CRX Content Repository, as its data store. Sling has been contributed to the Apache Software Foundation
      - AEM Modules
         -  Adobe Experience Manager runs on Granite platform, within OSGi framework. Individual AEM modules are WCM, DAM, Workflow, etc.
      - Customer Applications
          - Customer Applications run on AEM. Customer specific applications (websites, etc. also run within OSGi framework).
       
  2. Major tech stack upgrades in 6.x
      - Jackrabbit Oak - , Oak offers improved performance, scalability
      - Sightly: New templating language, makes markup look beautiful, enforces separation of the markup from logic and also offers XSS protection by default.
      - Touch UI: Classic UI in CQ5 which is ExtJS based has been upgraded to Touch UI which supports touch enabled devices - built using Coral UI framework.
      - Search - Apache Solr: Default search engine in CQ5 was Lucene, this has been upgraded to Solr. You can now configure Solr server as search engine for your AEM application.
  3. OSGI :
         The OSGi has a layered model. The following list contains a short definition of the terms:
       - Bundles – Bundles are normal jar components with extra manifest headers.
       - Services – The service layer, which hold the service-side of the framework, keeps the service registry and manages it.
       - Life-Cycle – The lifecycle layer manages and keeps track of the frameworks and bundles lifecycle state. It is used to install or uninstall framework objects and start or stop them.
       - Modules – The module layer, which is the bundle space, holds the bundles that are installed on the framework and are managed through the lifecycle layer.
       - Security – The security layer, which extends the jave 2 security architecture, is optional. When active, it validate the bundle signatures and controls the component access rights .
       - Execution Environment – The execution environment layer, which is the bottom layer on which the bundles live, is selected to fit the underlying hardware or operating system.
  4. OSGI life cycle states
     The bundle life cycle states are as follows.
      - INSTALLED: The bundle has been successfully installed. The framework knowsenough about this bundle to attempt to load it.
      - RESOLVED: All resources needed for this bundle have been loaded successfully andthe bundle is ready to be started. This is also the state the bundle would be in, once successfully stopped.
      - STARTING: The bundle is being started, but has not finished starting.
      - ACTIVE: The bundle has been successfully activated and is running, ready to be used.
      - STOPPING: The bundle is being stopped, but has not finished stopping.
      - UNINSTALLED: The bundle has been uninstalled. Once uninstalled, nothing can be done with the module.
  5. Bundle wiring
     - The process of linking a bundle to provide its access to another bundle's content is called bundle wiring. When the framework resolves a bundle for installation, it reads the bundle manifest lookingfor its capabilities (the packages it provides or exports) and its requirements (those that it imports). It uses this information to wire the bundles together in a mesh of dependencies, thus constructing the class space visible to each bundle.
  6.  You want to view request information sent to the server.Which browser-based tool should you use?
      - Felix Webconsole
  7.    You have changed the CRX admin password. Which console or tool do you also need to update?
        Go to Apache Felix Web console          
          switch to Configuration tab.
          select Configurations item CRX Sling Client Repository and configure it.
          set the value for property Admin Password to the same password configured above in the repository.
          click save which immediately takes effect.
  8. You have an active bundle which is configured via CRX repository. What do you have to do after you have saved changes to the configuration to apply them?
        - Nothing , changes are automatically applied
  9. What does the Configuration Admin Service in OSGi provide?
     -  The OSGi Componendium Configuration Admin Service specifies a service, which allows for easy management of configuration data for configurable components. Basicaly configuration is a list of name-value pairs. Configuration is managed by management applications by asking the Configuration Admin Service for such configuration. After updating the configuration, it is sent back to the Configuration Admin Service. The Configuration Admin Service is like a central hub, which cares for persisting this configuration and also for distributing the configuration to interested parties. One class of such parties are the components to be configured. These are registered as ManagedService services. There is also a notion of ManagedServiceFactory, which allows for multiple configurations of the same kind to be applied.
    
 10. You want to override an OSGi component configuration in CRX. What happens if you do NOT specify a property in the CRX configuration that is required by the component?
     - It will use the default configuration for the unspecified property.
 11. How do you create a configuration for an OSGi bundle within CRX that is specific to only the author instance?
     - Use the CRX browser to create a folder in /apps/myproject called “config.author” and then create a new node and select “sling:OsgiConfig” as the node type
 12. How can you use the CRX repository to install an OSGi bundle?
     - Copy the bundle into the /apps/install folder.
 13. You are creating a repository-based OSGi configuration. Which name should the factory configuration node have?
     - Append "-<"identifier"> to the name, where identifier can be any unique name.

### SLING
     
    AEM is built using Sling, a Web application framework based on REST principles that provides easy development of content-oriented applications. 
    Sling uses a JCR repository, such as Apache Jackrabbit, or in the case of AEM, the CRX Content Repository, as its data store.
    
   Apache Sling in five bullets points.
    * REST based web framework.
    * Content-driven, using a JCR content repository.
    * Powered by OSGi
    * Scripting inside, multiple languages (JSP, server-side javascript, Scala, etc.)
    * Apache Open Source project
    
     - For more information click [here](https://sling.apache.org/)


14. What is Sling Resolution:
    - The following diagram explains Sling script resolution: it shows how to get from HTTP request to content node, from content node to resource type, from resource type to script and what scripting variables are available.
     ![Sling Resolution Diagram](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/platform/media_1b9a37c84e3ea292bb66f8d7a0bfb70f911766fa0.png?width=2000&format=webply&optimize=medium)
    - Steps:
        -   URL : http://localhost:4502/content/we_train.html
        1. Http Request : In this step find the Content Path  ( content/we_train)
        2. Content Resolutions: In this find the node we_train in /content in JCR
        3. Get Resource Type: In this step find the property -> sling:resourceType  --> myproject/content/page
        4. Script Locations: In this step find the Resource Type in first in /apps/ as /apps/myproject/content/page or in /libs  -- if not found - 404
        5. Scripts Names: In this step find the Script Name :
           - first find a file with Selector  <selector>.<extension>.html,
           - if no file with selection, then find the file with extension - if found - execute
           - if no file with extension, then find the file with 'page' - if foudn - execute
           - if not find a file with http protocol - GET  ( worst case scenario). 

15. What is Sling Model
    - A Sling Model is implemented as an OSGi bundle.
    - A Java class located in the OSGi bundle is annotated with @Model and the adaptable class (for example, @Model(adaptables = Resource.class).
    - The data members (Fields) use @ValueMapValue annotations. These data members map to node properties.
    - [Sling Model Documentation](https://sling.apache.org/documentation/bundles/models.html)
   
      ```
        import org.apache.commons.lang3.StringUtils;
        import org.apache.sling.models.annotations.DefaultInjectionStrategy;
        @Model(adaptables = Resource.class,
        defaultInjectionStrategy = DefaultInjectionStrategy.OPTIONAL)
        public class HelloWorldModel {
        
            ...
        
            @ValueMapValue
            private String title;
        
            @ValueMapValue
            private String text;
        
            @PostConstruct
            protected void init() {
                ...
            /***
            *
            * @return the value of title, if null or blank returns "Default Value here!"
            */
            public String getTitle() {
                return StringUtils.isNotBlank(title) ? title : "Default Value here!";
            }
            /***
                *
                * @return All caps variation of the text value
                */
            public String getText() {
                return StringUtils.isNotBlank(this.text) ? this.text.toUpperCase() : null;
            }
      ```

      - For more information https://sling.apache.org/documentation/bundles/models.html
      - For more information https://helpx.adobe.com/experience-manager/using/sling_models.html
      - For more information watch this video
  
16. Is Sling is Content Centric : Explain:

  - Sling is content-centric. This means that processing is focused on the content as each (HTTP) request is mapped onto content in the form of a JCR resource (a repository node):
    - the first target is the resource (JCR node) holding the content
    - secondly, the representation, or script, is located from the resource properties in combination with certain parts of the request (e.g. selectors and/or the extension)

17. Explain restful sling.
    Due to the content-centric philosophy, Sling implements a REST-oriented server and thus features a new concept in web application frameworks. The advantages are:
    - very RESTful, not just on the surface; resources and representations are correctly modelled inside the server
    - removes one or more data models
      - previously the following were needed: URL structure, business objects, DB schema;
      - his is now reduced to: URL = resource = JCR structure
19. What are the sling APIs you have used?
   These are the api and classes frequently used in AEM      
    - ValueMap - The ValueMap is an easy way to access properties of a resource.
    - ResourceResolver - The ResourceResolver defines the service API which may be used to resolve Resource objects.
    - ResourceProvider - API for providers of resources.
    - Resource - Resources are pieces of content on which Sling acts The Resource is also an Adaptable to get adapters to other types.
    - ResourceWrapper - The ResourceWrapper is a wrapper for any Resource delegating all method calls to the wrapped resource by default.
    - ResourceUtil - The ResourceUtil class provides helper methods dealing with resources.
      - For more information click [here](https://sling.apache.org/apidocs/sling8/org/apache/sling/api/resource/package-summary.html)
21. Which provider service scans the CRX repository for artifacts and provides them to the OSGi installer?
    - Sling JCR Installer scans the CRX repository for artifacts and provides them to the OSGi installer. 

### Repository - JCR
 - AEM is built on top of Adobe's CRX platform.
 - CRX is a data storage system specifically designed for content-centric applications.
 - AEM uses this content repository to store all its web content, digital assets, scripts, Java libraries, configuration information and other data.
 - CRX implements the Content Repository API for Java Technology (JCR). This standard defines a data model and application programming interface (that is, a set of commands) for content repositories.

22. What is JCR
    - A content repository, as defined by JCR, combines features of the traditional relational database with those of a conventional file system.
        - File system-like features supported by JCR include:
        - Hierarchy: Content in a JCR repository can be addressed by path. This is useful when delivering content to the web since most websites are also organized hierarchically.
        - Semi-structured content: JCR can store structured documents, like XML, either as opaque files (as a file system would) or as structures ingested directly into the JCR hierarchy.
        - Access Control and Locking: JCR can restrict access to different parts of the content hierarchy based on policies or ACLs. It also supports locking of content to prevent conflicts.
23. What is Oak Indexing?
   - Unlike Jackrabbit 2, Oak does not index content by default. Custom indexes need to be created when necessary, much like with traditional relational databases. If there is no index for a specific query then the whole repository will be traversed
    For more information https://docs.adobe.com/docs/en/aem/6-0/deploy/upgrade/queries-and-indexing.html
24. Explain David's content model
    David Model:
     - Data First, Structure Later. Maybe.
     - Drive the content hierarchy, don't let it happen.
     - Workspaces are for clone(), merge() and update().
     - Beware of Same Name Siblings.
     - References considered harmful.
     - Files are Files.
     - IDs are evil.
        For more information https://docs.adobe.com/docs/en/cq/5-6/howto/model_data.html
26. Diff between crx 2 & crx 3    
   - CRX 2	CRX 3
   - CRX 2 is extended from Jackrabbit.	CRX3 is extended from Jackrabbit OAK.
   - JackRabbit is a pure JCR implementation.	OAK uses a three tier architecture with NODE STATE MODEL that uses JCR just as a facade
   - Persistence Manager is used to store data in JackRabbit that allows the content to be written to the persistence layer as a blob.	In OAK, Microkernels write data as native structures of the underlying Database used.                                     For eg. Mongo DB data is written as documents
   - Jackrabbit runs on LUCENE.	OAK supports SOLR indexing implicitly
   - CRX2 datastore is on the filesystem by default.	CRX3 supports multiple configurations on DataStore (binary data storage). By default it is implicit

27. Why we need TAR Compaction
    - If we are using Tar files as the storage, it tends to grow in size and starts claiming disk space every time when data is created or updated as data in tar files are never overwritten rather it keeps adding new versions. To mitigate the same, AEM has garbage collection mechanism which is known as ‘Tar Compaction’ to remove the unused data and reclaim the disk space.
    - To perform TAR Compaction, please follow this blog http://www.aemcq5tutorials.com/tutorials/online-offline-tar-compaction-in-aem/
28. You have created a bundle with crxde. what does .bnd file contain?
   - The .bnd file contains extra metadata about the bundle used by the CRXDE build process.
29. You want to install bundles through CRX only in the author instance. which folde name can you use for that purpose?
   - All folders named install.author.
30. You want to request a JSON representation of content , what do you have to do with the request?
   - Change the extension to .json.
32. Which access control polices does JCR session define to manage nodes?
  - Privileges to access the JCR workspace define to manage nodes
   
### Component & Template
33. What is Dialog, Design Dialog and cq:dialog?
    - dialog	design-dialog
    - Dialog will change the content at the page level.	Design dialog will change the content at the template level.
    - authored in edit mode.	authored in design mode.
    - node name should be dialog.	node name should be design_dialog.
    - stored under pages jcr:content node.	stored under design page located under /etc/design/default.
    - we can get value from properties object.	we can get design dialog value from currentStyle object.
    - jcr:primaryType is cq:Dialog.	jcr:primaryType is cq:Dialog.
    - cq:dialog - It is the dialogs for the touch-optimized UI(editor.html).
        - It uses the Granite UI framework.
        - Node name is cq:dialog.
        - jcr:primaryType = nt:unstructured, sling:resourceType = cq/gui/components/authoring/dialog for cq:dialog
34. Difference between parsys and iparsys.
    - parsys – It is a placeholder called “Paragraph System”, where we can drag and drop or add other components or scripts at page level.
    - iparsys - The inherited paragraph system is a paragraph system that also allows you to inherit the created paragraphs from the parent. it is similar to parsys except that it allows to inherits parent page “paragraph system” at template level. You can also cancel paragraph inheritance at a level at any time. It has two checkbox options to cancel/disable the inheritance.
        - Cancel Inheritance - If selected, the components in this paragraph system are not passed down to the child pages.
        - Disable Inheritance - If selected, components of this paragraph system on this page are not inherited from the parent page.
36. Explain overlaying concept in AEM.?
    - Overlaying - The intention of overlaying a default component is to alter the appearance or behavior of a component globally, for all relative references to the component. It relies on the nature of sling to resolve to the /apps folder before searching in the /libs folder. Thus the path to the component is identical to the path to the default component, except it is in the /apps folder and not the /libs folder. More on overlaying watch this video
    - Creating a custom component manually by creating all necessary nodes and setting value of “sling:superResourceType” property as “/libs/foundation/components/image”. By doing this you inherit all the feature of image component, even after upgrade you still inherit the features of image component. For more information watch this video
    - After AEM 6.x, overlay can be done using 'Sling Resource Merger', but with this it is only available to TouchUI(Granite ), if it needs to be done for classic ui, then we need to copy all the nodes from /lib to /apps.
37.Why we need to include global.jsp if we are creating a component in jsp?
    - The JSP script file global.jsp is used to provide quick access to specific objects (i.e. to access content) to any JSP script file used to render a component. Therefore global.jsp should be included in every component rendering JSP script where one or more of the objects provided in global.jsp are used.
    - For more information Check this [link](https://aemgeeks.wordpress.com/2017/07/31/global-jsp/#:~:text=The%20Global.,the%20objects%20provided%20in%20global.)
38.What is the use of EditConfig node in creating a component?
   - The edit behaviour of a component is configured by adding a cq:editConfig node of type cq:EditConfig below the component node (of type cq:Component) and by adding specific properties and child nodes.
   - cq:editConfig (cq:EditConfig) - Defines the edit properties of the component and enables the component to appear in the Components browser or Sidekick. Note: if the component has a dialog, it will automatically appear in the Components browser or Sidekick, even if the cq:editConfig does not exist.
   - For more information check this [link](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/components/components-basics)
39. What is Parbase
   - Parbase is a key component as it allows components to inherit attributes from other components, similar to subclasses in object oriented languages such as Java, C++, and so on. For example, when you open the /libs/foundation/components/text node in the CRXDE Lite, you see that it has a property named sling:resourceSuperType, which references the parbase component. The parbase here defines tree scripts to render images, titles, and so on, so that all components subclassed from this parbase can use this script.
   - Users do not need access to the parbase.     
40. Difference between sling:resourceSuperType and sling:resourceType.
  - sling:resourceSuperType: It is used to achieve inheritance in cq. When set, it inherits the specified component to this component.
  - sling:resourceType: It is a path, which locates the script to be used for rendering the content. Path used can be absolute or relative.
41. 
