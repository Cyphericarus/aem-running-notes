# Day 13 - OSGi (Open Services Gateway Initiative)
[08-06-2026]

## OSGi

**OSGi** stands for **Open Services Gateway Initiative**.

It is a **modular Java framework** that enables applications to be split into small, independent, reusable, and loosely coupled modules called **bundles**.

In AEM, OSGi is the foundation of the runtime architecture. Most backend functionalities are deployed and managed as OSGi bundles.

###### Key Characteristics

- Modular architecture
    
- Dynamic component management
    
- Runtime deployment and updates
    
- Service-oriented architecture
    
- Loose coupling between modules
    
- High reusability and maintainability
    

###### History

- Introduced in **1999**
    
- Initially designed for embedded and network-connected devices
    
- Later adopted by enterprise Java applications, including AEM
    

## Why OSGi in AEM?

Large applications become difficult to manage when all code exists in a single monolithic application.

OSGi solves this problem by dividing the application into multiple independent modules (**bundles**) that can be:

- Developed independently
    
- Tested independently
    
- Deployed independently
    
- Updated independently
    
- Reused across projects
    

## Analogy

#### Car Manufacturing vs AEM Project

|Car Manufacturing|AEM Project|
|---|---|
|Contractor|Project Team|
|Plumber|Module/Team 1|
|Electrician|Module/Team 2|
|Painter|Module/Team 3|
|Interior Designer|Module/Team 4|

###### Understanding

A car is not built by a single person.

Different specialists handle different responsibilities:

- Plumbing
    
- Electrical work
    
- Painting
    
- Interiors
    

Similarly, in an AEM project:

- Different teams develop different modules.
    
- Each module works independently.
    
- All modules integrate to form the complete application.
    

This modular approach is the core idea behind OSGi.

## Bundle

A **Bundle** is the basic deployment unit in OSGi.

Technically, a bundle is a **JAR file** containing:

- Java classes
    
- Resources
    
- Metadata (`MANIFEST.MF`)
    

The OSGi framework manages the lifecycle of these bundles.

###### Example

```text
core.jar
ui.apps.zip
ui.content.zip
```

In AEM:

- `core` module → OSGi Bundle (`.jar`)
    
- `ui.apps` → Content Package (`.zip`)
    
- `ui.content` → Content Package (`.zip`)
    

## Advantages of OSGi

#### 1. Fast Development

Modules can be developed independently by different teams.

This allows parallel development and reduces overall development time.

#### 2. Reduced Complexity

Large applications are split into smaller bundles.

Each bundle has a specific responsibility.

#### 3. Reusability

Bundles and services can be reused across multiple projects.

Example:

```text
Email Service
Logging Service
Notification Service
```

can be reused by different modules.

#### 4. Dynamic Updates

Bundles can be updated at runtime.

Server restart is generally not required.

#### 5. Easy Deployment

Individual bundles can be deployed without redeploying the entire application.

#### 6. Better Maintainability

Since functionalities are separated into bundles, debugging and maintenance become easier.

#### 7. Security

OSGi provides mechanisms for:

- Authentication
    
- Authorization
    
- Controlled access to services
    

## AEM Archetype Modules

An AEM project generated using the Maven Archetype contains multiple modules.

|Module|Packaging|
|---|---|
|core|`.jar`|
|ui.apps|`.zip`|
|ui.content|`.zip`|
|ui.config|`.zip`|
|ui.frontend|Frontend Build Module|
|all|`.zip`|

##### Classification

###### Backend Modules

Produce:

```text
.jar
```

Example:

```text
core
```

Contains:

- Servlets
    
- Models
    
- Services
    
- OSGi Components
    

###### Frontend/Content Modules

Produce:

```text
.zip
```

Examples:

```text
ui.apps
ui.content
ui.config
all
```

Contains:

- Components
    
- Templates
    
- Client Libraries
    
- Content
    
- Configurations
    

## Bundle Lifecycle

Every OSGi bundle goes through a lifecycle managed by the OSGi framework.

#### States

###### 1. Installed

Bundle is successfully installed into the framework.

Dependencies may not yet be available.


###### 2. Resolved

All required dependencies have been found.

Bundle is ready to start.



###### 3. Starting _(Transient State)_

Framework invokes the bundle startup process.


###### 4. Active

Bundle is running and providing services.

This is the normal operational state.


###### 5. Stopping _(Transient State)_

Framework invokes the bundle shutdown process.


###### 6. Uninstalled

Bundle is removed from the framework.

It can no longer provide services.


## Bundle Lifecycle Analogy

#### Bike Example

|Bike Activity|OSGi State|
|---|---|
|Insert key|Installed|
|Check fuel, air, condition|Resolved|
|Start bike|Starting|
|Ride bike and use it|Active|
|Turn off bike|Stopping|
|Remove key|Uninstalled|


## OSGi Architecture

The OSGi framework is divided into multiple layers.

#### 1. Module Layer

Responsible for:

- Bundle management
    
- Package sharing
    
- Dependency handling
    

Determines:

```text
Which bundle can access which package
```

#### 2. Lifecycle Layer

Responsible for:

- Install
    
- Start
    
- Stop
    
- Update
    
- Uninstall
    

of bundles.


#### 3. Service Layer

One of the most important layers in AEM.

Provides communication between bundles using services.

###### Example

```text
Bundle A → Provides Service

Bundle B → Consumes Service
```

Bundles communicate through interfaces rather than directly depending on each other.

This creates loose coupling.


#### 4. Security Layer

Responsible for:

- Authentication
    
- Authorization
    
- Permission management
    
- Resource access control
    


#### 5. Execution Environment Layer

Provides the Java runtime environment required by bundles.

Responsible for:

- JVM interaction
    
- Class loading
    
- Execution of OSGi components
    

## OSGi in AEM (Important)

Common OSGi concepts used in AEM development:

- OSGi Bundles
    
- OSGi Services
    
- OSGi Components
    
- Configurations (`OSGi Config`)
    
- Declarative Services (DS)
    
- Service References (`@Reference`)
    
- Configuration Manager (`/system/console/configMgr`)
    
- Bundle Console (`/system/console/bundles`)
    
- Components Console (`/system/console/components`)
    

These concepts form the backbone of AEM backend development and are heavily used in Servlets, Services, Schedulers, Workflow Processes, and Event Handlers.

## Exam / Interview Points

1. OSGi = Open Services Gateway Initiative.
    
2. OSGi is a modular Java framework.
    
3. Basic deployment unit = **Bundle (.jar)**.
    
4. AEM backend code runs as OSGi bundles.
    
5. OSGi supports runtime deployment and updates without restarting AEM.
    
6. Bundle lifecycle:
    

```text
Installed
→ Resolved
→ Starting
→ Active
→ Stopping
→ Uninstalled
```

7. Most important OSGi layers:
    

```text
Module Layer
Lifecycle Layer
Service Layer
Security Layer
Execution Environment Layer
```

8. OSGi promotes:
    
    - Modularity
        
    - Reusability
        
    - Loose Coupling
        
    - Maintainability
        
    - Dynamic Deployment

---

# Day 14 - OSGi Components and Services
[09-06-2026]

## OSGi Components and Services

OSGi Components and OSGi Services are fundamental building blocks of AEM backend development.

They are Java classes managed by the OSGi framework and participate in the bundle lifecycle.

Unlike regular Java objects created using `new`, OSGi components are:

- Created by the OSGi container
    
- Managed by the OSGi container
    
- Activated automatically when required
    
- Destroyed automatically when no longer needed
    

## Relationship with Bundle Lifecycle

An OSGi Component reacts to lifecycle events of the bundle in which it resides.

#### Bundle Lifecycle

1. Installed
    
2. Resolved
    
3. Starting
    
4. Active
    
5. Stopping
    
6. Uninstalled
    

When the bundle enters specific states, OSGi can invoke lifecycle methods inside component classes.


## Component Lifecycle Events

An OSGi Component mainly responds to three lifecycle events:

#### 1. Activate

Executed when the component becomes active and ready to provide services.

```java
@Activate
public void activate() {
	LOG.info("Bundle is Activtaed");
}
```

Used for:

- Initialization logic
    
- Resource allocation
    
- Loading configuration
    
- Startup logging

#### 2. Deactivate

Executed when the component is being shut down.


```java
@Deactivate
public void deactivate() {
	LOG.info("Bundle is Activtaed");
}
```


Used for:

- Cleanup operations
    
- Closing connections
    
- Releasing resources
    
- Shutdown logging
    

#### 3. Modified

Executed when the OSGi configuration of the component changes at runtime.

Used for:

- Reloading configuration
    
- Refreshing cached values
    
- Updating runtime settings
    

## OSGi R7 Annotations

OSGI 

DS[Declarative Services]  - We declare what we want using annotations instead of writing the lifecycle code manually like:

```
@Component, @Activator, @Deactivator, etc.
```

R7[Released Version 7]

AEM as a Cloud Service uses DS R7 Annotations.

#### Required Imports

```java
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Activate;
import org.osgi.service.component.annotations.Deactivate;
import org.osgi.service.component.annotations.Modified;
import org.osgi.service.component.annotations.Reference;
```

## Important OSGi Annotations

#### 1. @Component

Marks a Java class as an OSGi Component.

The OSGi container manages its lifecycle.

```java
@Component
public class DemoService {
}
```


>[!NOTE]
>Why do we need `@Component`?
>
Without `@Component`, OSGi doesn't know this class exists. It won't create an object, manage its lifecycle, register it as a service, or inject it into other components.

#### 2. @Activate

Invoked once when the OSGi component becomes active and ready to provide its service.

```java
@Activate
protected void activate() {
}
```

#### 3. @Deactivate

Invoked by the OSGi framework when the component is being deactivated or removed from service.

```java
@Deactivate
protected void deactivate() {
}
```

#### 4. @Modified

Invoked when component configuration changes.

```java
@Modified
protected void modified() {
}
```

#### 5. @Reference

Used for Dependency Injection between OSGi services/components.

Instead of creating objects manually:

```java
DemoService service = new DemoService();
```

OSGi injects the required service automatically.

```java
@Reference
private DemoService service;
```

## `Logger` and `LoggerFactory`

OSGi components generally use `SLF4J` logging.

#### Imports

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
```

#### Logger Declaration

```java
private static final Logger LOG =
        LoggerFactory.getLogger(TestDemo.class);
```

`LoggerFactory.getLogger(TestDemo.class)` creates a logger for the `TestDemo` class. The logger is declared as `private static final` so that only one instance is created per class, it cannot be reassigned, and it can be used throughout the class to log informational, debug, warning, and error messages.

## Complete OSGi Component Example

```java
import org.osgi.service.component.annotations.Activate;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Deactivate;
import org.osgi.service.component.annotations.Modified;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

@Component(
        service = TestDemo.class,
        immediate = true
)
public class TestDemo {

    private static final Logger LOG =
            LoggerFactory.getLogger(TestDemo.class);

    @Activate
    protected void activate() {
        LOG.info("Bundle Activated - Test");
    }

    @Deactivate
    protected void deactivate() {
        LOG.info("Bundle Deactivated - Test");
    }

    @Modified
    protected void modified() {
        LOG.info("Bundle Updated - Test");
    }
}
```


## Understanding `immediate = true`

```java
@Component(immediate = true)
```

means:

```text
Activate the component immediately after all
required dependencies are available.
```

###### Without `immediate = true`

The component may be activated only when another component requests its service.

###### With `immediate = true`

The component activates as soon as possible.

Useful for:

- Startup tasks
    
- Initializing caches
    
- Registering listeners
    
- Scheduler registration
    

## OSGi Service

A service is an OSGi component whose functionality can be consumed by other components.

Example:

```java
public interface EmailService {

    void sendEmail();
}
```

```java
@Component(service = EmailService.class)
public class EmailServiceImpl
        implements EmailService {

    @Override
    public void sendEmail() {
    }
}
```

Here:

```text
EmailService
```

is the contract.

```text
EmailServiceImpl
```

is the implementation.

Other components can consume this service using `@Reference`.


## Injecting One OSGi Service into Another

#### Service Provider

```java
@Component(service = EmailService.class)
public class EmailServiceImpl
        implements EmailService {

}
```


#### Service Consumer

```java
@Component
public class NotificationService {

    @Reference
    private EmailService emailService;

}
```

OSGi automatically injects the implementation.

No manual object creation is required.

## Singleton Nature of OSGi Components

By default:

```text
All OSGi Components are Singleton.
```

Meaning:

```text
One Component Instance
        ↓
Shared Across Entire Application
```

Example:

```java
@Component
public class DemoService {
}
```

Only one instance of `DemoService` exists within the OSGi container.

This is why OSGi services should generally be:

- Stateless
    
- Thread-safe
    
- Reusable
    

## Practical Verification in AEM

Create a component:

```java
@Component(immediate = true)
public class TestDemo {
}
```

Build and deploy.

Check:

```text
/system/console/components
```

You should see:

```text
TestDemo
State: Active
```


Add:

```java
@Activate
protected void activate() {
    LOG.info("Activated");
}
```

Restart the bundle and observe:

```text
crx-quickstart/logs/error.log
```

Output:

```text
Activated
```

This proves OSGi is managing the component lifecycle.


## Difference Between Component and Service

|Component|Service|
|---|---|
|OSGi-managed Java class|Functionality exposed to other components|
|Can exist independently|Usually consumed using `@Reference`|
|Managed by OSGi container|Registered in OSGi Service Registry|
|May or may not expose functionality|Intended for reuse|

###### Important

Every OSGi Service is a Component.

But not every Component is necessarily used as a Service.

## Interview Points

1. OSGi Components are managed by the OSGi container.
    
2. Main lifecycle annotations:
    
    - `@Activate`
        
    - `@Deactivate`
        
    - `@Modified`
        
3. `@Component` registers a class as an OSGi Component.
    
4. `@Reference` is used for OSGi Dependency Injection.
    
5. OSGi Components are singleton by default.
    
6. `immediate = true` activates the component as soon as dependencies are satisfied.
    
7. OSGi services should be stateless and thread-safe.
    
8. Verify components in:
    
    - `/system/console/components`
        
    - `/system/console/bundles`
        
9. Lifecycle logs can be viewed in:
    

```text
crx-quickstart/logs/error.log
```

10. Service-to-service communication in OSGi is done using `@Reference`.

---


# Day 15 - OSGi Configuration

**Date:** 10-06-2026

## OSGi Configuration

In AEM, many components need values that may change over time, such as:

- API endpoints
    
- Authentication keys
    
- Timeouts
    
- Thresholds
    
- Limits
    
- Environment-specific values
    

Hardcoding such values directly inside Java code is a bad practice because any change would require code modification and redeployment.

**OSGi Configuration** solves this problem by allowing values to be changed inside AEM itself without changing code or redeploying the bundle.

## Why OSGi Configuration is Needed

Suppose a service uses this API:

```text
https://gorest.co.in/public/v2/posts
```

If this URL is hardcoded:

1. Modify code
    
2. Build again
    
3. Deploy again
    

That is inefficient and risky.

With OSGi Configuration:

1. Code is deployed once
    
2. Configuration can be changed later from AEM
    
3. The component updates dynamically
    

This is the correct way to externalize environment-specific values in AEM.

### Core Idea

OSGi Configuration separates:

- **Logic** → Java Component / Service
    
- **Data / Values** → OSGi Configuration
    

This allows the component code to remain stable while configuration changes independently.


## OSGi R7 Annotations Used for Configuration

1. `@Component`
    
2. `@Activate`
    
3. `@Deactivate`
    
4. `@Modified`
    
5. `@Reference`
    
6. `@ObjectClassDefinition`
    
7. `@AttributeDefinition`
    
8. `@Designate`
    
![[Final-Improved-Notes#Important OSGi Annotations]]

### 6. `@ObjectClassDefinition`

#### Purpose

Defines an OSGi Configuration Schema (Blueprint).

OSGi uses this interface to automatically generate a configuration screen in AEM.

#### Syntax

```java
@ObjectClassDefinition(
    name = "News Portal Configuration",
    description = "Configuration for News Portal APIs"
)
public @interface NewsPortalConfiguration {
}
```

#### Key Points

- Represents a complete configuration object.
    
- Contains one or more configuration properties.
    
- Generates OSGi Configuration UI automatically.
    
- Used together with `@AttributeDefinition`.
    
- Used as the `ocd` value in `@Designate`.
    

#### Analogy

```text
Configuration Form
       ↓
@ObjectClassDefinition
```

#### Interview Definition

> `@ObjectClassDefinition` is used to define an OSGi configuration schema. It acts as a blueprint for generating configuration screens in AEM.



### 7. `@AttributeDefinition`

#### Purpose

Defines an individual configuration property inside an OSGi Configuration.

#### Syntax

```java
@AttributeDefinition(
    name = "API URL",
    description = "External REST API URL"
)
String restAPIurl();
```

#### Key Points

- Represents a configuration property.
    
- Used inside an `@ObjectClassDefinition`.
    
- Defines UI metadata:
    
    - Name
        
    - Description
        
    - Type
        
    - Default Value
        
    - Required / Optional settings
        
- Each method becomes a configuration field.
    

#### Example

```java
@AttributeDefinition(
    name = "API URL"
)
String restAPIurl()
    default "https://gorest.co.in/public/v2/posts";
```

#### Important

Although it looks like a method:

```java
String restAPIurl();
```

it represents a configuration property, not a business method.

#### Analogy

```text
Configuration Form Field
          ↓
@AttributeDefinition
```

#### Interview Definition

> `@AttributeDefinition` is used to define a configuration property and its metadata inside an OSGi Configuration definition.

### 8. `@Designate`

#### Purpose

Links an OSGi Component with an OSGi Configuration.

#### Syntax

```java
@Component(service = DemoService.class)
@Designate(ocd = NewsPortalConfiguration.class)
public class DemoService {
}
```

#### Key Points

- Connects a configuration interface to a component.
    
- Allows configuration values to be injected into the component.
    
- Usually used together with `@Activate`.
    
- `ocd` stands for:
    

```text
Object Class Definition
```

#### Flow

```text
@ObjectClassDefinition
          ↓
Defines Configuration

@Designate
          ↓
Connects Configuration To Component

@Activate
          ↓
Reads Configuration Values
```

#### Interview Definition

> `@Designate` associates an OSGi Component with an `@ObjectClassDefinition` so that configuration values can be provided to the component at runtime.

### Easy Memory Trick

```text
@ObjectClassDefinition
         ↓
Creates Configuration Blueprint

@AttributeDefinition
         ↓
Creates Configuration Properties

@Designate
         ↓
Connects Configuration To Component

@Activate
         ↓
Reads Configuration Values
```

### One-Line Summary

- **`@ObjectClassDefinition`** → Defines the configuration.
    
- **`@AttributeDefinition`** → Defines configuration properties.
    
- **`@Designate`** → Binds configuration to a component.
    

## Configuration Interface

The configuration interface defines the editable properties that appear in AEM Config Manager.

### Example

```java
package com.karthik.newsportal.core.services;

import org.osgi.service.metatype.annotations.AttributeDefinition;
import org.osgi.service.metatype.annotations.ObjectClassDefinition;

@ObjectClassDefinition
public @interface AdithyaConfiguration {

    @AttributeDefinition(
        name = "Adithya URL Path",
        description = "This is a sample URL path"
    )
    String restAPIurl() default "https://gorest.co.in/public/v2/posts";
}
```

### Meaning

#### `@ObjectClassDefinition`

Marks the interface as an OSGi Configuration Definition.

OSGi uses it to generate:

```text
Configuration Schema
       ↓
Configuration Screen
       ↓
PID Metadata
```

#### `@AttributeDefinition`

Defines the field metadata shown in:

```text
/system/console/configMgr
```

Displayed as:

```text
Adithya URL Path
```

with description:

```text
This is a sample URL path
```

#### `restAPIurl()`

Creates a configuration property:

```text
restAPIurl
```

Default value:

```text
https://gorest.co.in/public/v2/posts
```

is used when no custom configuration exists.

### Final Result

```text
AdithyaConfiguration
          ↓
Creates OSGi Configuration Definition

Contains Property:

restAPIurl
          ↓
Default Value:

https://gorest.co.in/public/v2/posts
```

## Service Class Using OSGi Configuration

This service reads the configured API URL and fetches data from it.

### Example

```java
package com.karthik.newsportal.core.services;

@Component(service = KarthikService.class, immediate = true)
@Designate(ocd = AdithyaConfiguration.class)
public class KarthikService {

    private static final Logger Log =
        LoggerFactory.getLogger(KarthikService.class);

    private String articleRestUrl;

    @Activate
    public void activate(
        AdithyaConfiguration config) {

        Log.info(
            "KarthikService -- Inside the Activated Method"
        );

        this.articleRestUrl =
            config.restAPIurl();
    }

    @Modified
    public void update(
        AdithyaConfiguration config) {

        Log.info(
            "KarthikService -- Inside the update Method"
        );

        this.articleRestUrl =
            config.restAPIurl();
    }

    public String getarticle() {

        CloseableHttpClient httpclient =
            HttpClients.createDefault();

        HttpGet request =
            new HttpGet(articleRestUrl);

        String result = null;

        try {

            CloseableHttpResponse response =
                httpclient.execute(request);

            HttpEntity entity =
                response.getEntity();

            if(entity != null) {

                result =
                    EntityUtils.toString(entity);
            }

        } catch(IOException e) {

            e.printStackTrace();
        }

        return result;
    }
}
```

### What This Service Does

This component demonstrates how an OSGi Service consumes configuration values and uses them in business logic.

### Component Registration

```java
@Component(
    service = KarthikService.class,
    immediate = true
)
```

#### Purpose

Registers the class as an OSGi Service.

OSGi automatically:

```text
Creates Object
Manages Lifecycle
Registers Service
Destroys Object
```

#### service = KarthikService.class

Registers the service in the OSGi Service Registry.

```text
Service Registry
       ↓
KarthikService
```

Other components can now consume it using:

```java
@Reference
private KarthikService service;
```

#### immediate = true

```java
immediate = true
```

Meaning:

```text
Activate Immediately
after Bundle Starts
```

Without this, activation may happen only when the service is first requested.


### Configuration Mapping

```java
@Designate(
    ocd = AdithyaConfiguration.class
)
```

Links:

```text
AdithyaConfiguration
          ↓
     KarthikService
```

OSGi now knows which configuration belongs to this component.

Without `@Designate`, OSGi cannot associate the configuration with the service.


### Logger

```java
private static final Logger Log =
    LoggerFactory.getLogger(
        KarthikService.class
    );
```

Used to write messages into:

```text
error.log
```


### Configuration Value Storage

```java
private String articleRestUrl;
```

Stores the configured API URL.

Example:

```text
https://gorest.co.in/public/v2/posts
```

## Component Activation

### @Activate

```java
@Activate
public void activate(
    AdithyaConfiguration config
)
```

When the component becomes active:

```text
Load Configuration
       ↓
Create Config Object
       ↓
Call activate()
```

#### Where does config come from?

The developer never creates it manually.

OSGi automatically creates and injects:

```text
ConfigMgr / cfg.json
          ↓
Configuration Admin
          ↓
AdithyaConfiguration Object
          ↓
activate()
```


### Reading Configuration Values

```java
this.articleRestUrl =
    config.restAPIurl();
```

Meaning:

```text
Read URL From Configuration
          ↓
Store In articleRestUrl
```

Example:

```text
https://gorest.co.in/public/v2/posts
```


## Configuration Update

### @Modified

```java
@Modified
public void update(
    AdithyaConfiguration config
)
```

Executed whenever configuration changes.

Example:

```text
Old URL
      ↓
https://gorest.co.in/public/v2/posts

New URL
      ↓
https://gorest.co.in/public/v3/posts
```

OSGi automatically invokes:

```java
update(...)
```

allowing the component to refresh values without restarting.

## REST API Method

### getarticle()

```java
public String getarticle()
```

This method performs the REST API call.

### Create HTTP Client

```java
CloseableHttpClient httpclient =
    HttpClients.createDefault();
```

Purpose:

```text
Create HTTP Engine
```

Think of it as:

```text
Browser Created In Java
```

### Create Request

```java
HttpGet request =
    new HttpGet(articleRestUrl);
```

Builds a GET request using the configured URL.

Example:

```text
GET
https://gorest.co.in/public/v2/posts
```


### Execute Request

```java
CloseableHttpResponse response =
    httpclient.execute(request);
```

Calls the external API.


### Read Response

```java
HttpEntity entity =
    response.getEntity();
```

Obtains the response body.


### Convert Response To String

```java
result =
    EntityUtils.toString(entity);
```

Converts the JSON response into a Java String.

Example:

```json
[
  {
    "id": 1,
    "title": "Sample"
  }
]
```


### Return Data

```java
return result;
```

Returns the API response to the caller.


### What Happens During Runtime?

```text
Bundle Starts
      ↓
OSGi Creates KarthikService
      ↓
OSGi Reads AdithyaConfiguration
      ↓
@Activate Executes
      ↓
API URL Loaded
      ↓
KarthikService Registered
      ↓
Service Registry
```

### One-Line Summary

> `KarthikService` reads the API URL from OSGi Configuration, stores it during activation, updates it dynamically through `@Modified`, calls the external REST API using that URL, and returns the response.


## Consumer Class Using the Service

This component consumes `KarthikService` using `@Reference`.

### Example

```java
package com.karthik.newsportal.core.services;

import org.osgi.service.component.annotations.Activate;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Deactivate;
import org.osgi.service.component.annotations.Modified;
import org.osgi.service.component.annotations.Reference;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

@Component(immediate = true)
public class PreereleaseService {

    private static final Logger Log =
        LoggerFactory.getLogger(
            PreereleaseService.class
        );

    @Reference
    private KarthikService service;

    @Activate
    public void activate() {

        String ar =
            service.getarticle();

        Log.info(
            "PreereleaseService -- Inside the Activated Method"
        );

        Log.info(
            "Response -- {}",
            ar
        );
    }

    @Deactivate
    public void deactivate() {

        Log.info(
            "PreereleaseService -- Inside the DeActivated Method"
        );
    }

    @Modified
    public void update() {

        Log.info(
            "PreereleaseService -- Inside the update Method"
        );
    }
}
```

### Purpose

This component demonstrates how one OSGi Service can consume another OSGi Service using Dependency Injection.

Relationship:

```text
PreereleaseService
          ↓
      @Reference
          ↓
     KarthikService
```


### Component Registration

```java
@Component(
    immediate = true
)
```

Registers the class as an OSGi Component.

OSGi automatically:

```text
Creates Component
Manages Lifecycle
Calls Lifecycle Methods
Destroys Component
```

#### immediate = true

Meaning:

```text
Activate Immediately
when Bundle Starts
```

after all dependencies are satisfied.



### Logger

```java
private static final Logger Log =
    LoggerFactory.getLogger(
        PreereleaseService.class
    );
```

Used to write messages into:

```text
crx-quickstart/logs/error.log
```



### Service Injection

#### @Reference

```java
@Reference
private KarthikService service;
```

This is the most important line in the class.

Purpose:

```text
Inject KarthikService
Automatically
```

instead of creating it manually.

Without OSGi:

```java
KarthikService service =
    new KarthikService();
```

With OSGi:

```java
@Reference
private KarthikService service;
```

OSGi automatically resolves and injects the dependency.



#### What Happens Internally?

OSGi checks:

```text
Service Registry
```

for:

```text
KarthikService
```

If found:

```text
Inject Service
```

into:

```java
service
```

field.

Flow:

```text
KarthikService
      ↓
Service Registry
      ↓
@Reference
      ↓
PreereleaseService
```


#### Why Use @Reference?

Benefits:

```text
Loose Coupling
Lifecycle Management
Dependency Injection
Reusability
Maintainability
```

The consumer only knows:

```text
I need this capability
```

OSGi decides:

```text
Which implementation to inject
When to inject it
How to manage its lifecycle
```


### Component Activation

#### @Activate

```java
@Activate
public void activate()
```

Executed when the component becomes active.

Activation occurs only after:

```text
Bundle Active
      ↓
Dependencies Satisfied
      ↓
Component Activated
```


#### Calling the Service

```java
String ar =
    service.getarticle();
```

Flow:

```text
PreereleaseService
          ↓
service.getarticle()
          ↓
KarthikService
          ↓
Configured URL
          ↓
External REST API
          ↓
Response Returned
```


#### Logging Response

```java
Log.info(
    "Response -- {}",
    ar
);
```

Writes the API response into:

```text
crx-quickstart/logs/error.log
```



### Component Deactivation

#### @Deactivate

```java
@Deactivate
public void deactivate()
```

Executed when:

```text
Bundle Stops
Bundle Uninstalls
Server Shuts Down
```

Purpose:

```text
Cleanup Logic
Release Resources
Log Shutdown Activities
```



### Component Modification

#### @Modified

```java
@Modified
public void update()
```

Executed when component configuration changes.

Purpose:

```text
Reload Configuration
Refresh Internal State
Avoid Restart
```


## Complete Runtime Flow

This is the preferred way to explain the code during interviews.

```text
Bundle Starts
      ↓
OSGi Creates KarthikService
      ↓
OSGi Loads AdithyaConfiguration
      ↓
@Activate Executes
      ↓
API URL Loaded
      ↓
KarthikService Registered
      ↓
Service Registry
      ↓
OSGi Creates PreereleaseService
      ↓
@Reference Injects KarthikService
      ↓
PreereleaseService Activated
      ↓
service.getarticle()
      ↓
External REST API Called
      ↓
JSON Response Received
      ↓
Response Logged In error.log
```

#### Where the Response Appears

```text
crx-quickstart/logs/error.log
```

because all:

```java
Log.info(...)
```

statements are written to the AEM log files.


## Lifecycle Flow in This Example

```text
1. KarthikService Activated

2. Configuration Value
   restAPIurl Read

3. KarthikService Registered
   Into Service Registry

4. PreereleaseService Activated

5. @Reference Injects
   KarthikService

6. service.getarticle()
   Executes

7. External API Invoked

8. JSON Response Returned

9. Response Logged
   Into error.log
```


## Practical Meaning of This Example

This example demonstrates the complete OSGi Configuration and Service flow:

### 1. Resource URL Externalized

Instead of hardcoding:

```text
https://gorest.co.in/public/v2/posts
```

the value is moved to OSGi Configuration.


### 2. Configuration Bound To Component

```java
@Designate(
    ocd = AdithyaConfiguration.class
)
```

links configuration to `KarthikService`.



### 3. Service Uses Configuration

```java
@Activate
@Modified
```

load and refresh configuration values.



### 4. Service Consumed By Another Component

```java
@Reference
private KarthikService service;
```

injects the service automatically.



### 5. External API Invoked

```java
service.getarticle();
```

calls the configured REST endpoint.



### 6. Response Logged

The API response is written into:

```text
error.log
```



### One-Line Summary

> `PreereleaseService` consumes `KarthikService` through `@Reference`, invokes the configured REST API during activation, receives the response, and logs the result into AEM's `error.log`.


## Ways to Configure OSGi in AEM

There are two common ways to configure OSGi services.

### 1. Through OSGi Config Manager

Open:

```text
/system/console/configMgr
```

Search for the PID of the component and edit the values directly.

This approach is useful for:

- Quick testing
    
- Local development
    
- Manual configuration
    


### 2. Through Repository-Based Configuration

Configuration files can be stored as part of the project.

Typical locations:

```text
/apps/newsportal/osgiconfig/config
```

or in modern AEM projects:

```text
ui.config
```

The file naming convention is:

```text
PID.cfg.json
```

#### Example

```text
com.karthik.newsportal.core.services.KarthikService.cfg.json
```

```json
{
  "status": false,
  "restAPIurl": "https://gorest.co.in/public/v2/posts"
}
```


## PID (Persistent Identifier)

Every OSGi Configuration has a unique identifier called a PID.

Example:

```text
com.karthik.newsportal.core.services.KarthikService
```

OSGi uses the PID to:

- Identify configurations
    
- Load configuration values
    
- Associate configurations with components
    

Configuration files are named using the PID.

Example:

```text
com.karthik.newsportal.core.services.KarthikService.cfg.json
```


## Config Manager vs Repository Configuration

Both approaches manage the same OSGi Configuration.

### Config Manager

```text
ConfigMgr
      ↓
Updates Runtime Configuration
```

Advantages:

- Immediate changes
    
- Easy testing
    
- No deployment required
    


### Repository Configuration

```text
cfg.json
      ↓
Version Controlled
      ↓
Deployed With Code
```

Advantages:

- Source control support
    
- Repeatable deployments
    
- Environment consistency
    

### Best Practice

For real projects:

```text
Repository Configuration
```

is preferred because configuration becomes part of the deployment process.


## OSGi Service Registry

Whenever a service is registered using:

```java
@Component(service = NewsService.class)
```

OSGi automatically registers it in the Service Registry.

Flow:

```text
NewsServiceImpl
       ↓
OSGi Service Registry
       ↓
@Reference
       ↓
Consumer Component
```

When a component contains:

```java
@Reference
private NewsService newsService;
```

OSGi searches the registry and injects the matching service.

## Service Interface Pattern

In real-world AEM projects, services are usually implemented using an Interface and an Implementation class.

### Interface

```java
public interface NewsService {
    String getArticles();
}
```

### Implementation

```java
@Component(service = NewsService.class)
public class NewsServiceImpl
        implements NewsService {

    @Override
    public String getArticles() {
        return "News Data";
    }
}
```

### Consumer

```java
@Reference
private NewsService newsService;
```

### Advantages

- Loose Coupling
    
- Better Maintainability
    
- Easier Unit Testing
    
- Multiple Implementations Possible
    


## Component vs Service

### Component

```java
@Component
public class DemoComponent {
}
```

Characteristics:

- OSGi-managed Java class
    
- Participates in lifecycle events
    
- May not expose functionality to other components
    


### Service

```java
@Component(service = NewsService.class)
public class NewsServiceImpl
        implements NewsService {
}
```

Characteristics:

- OSGi-managed Java class
    
- Registered in Service Registry
    
- Can be injected using `@Reference`
    

### Important

```text
Every Service is a Component.

Every Component is not a Service.
```


## Immediate vs Delayed Components

### Immediate Component

```java
@Component(immediate = true)
```

Activated immediately after dependencies are satisfied.

Flow:

```text
Bundle Starts
      ↓
Dependencies Satisfied
      ↓
Component Activated
```

Common Uses:

- Startup Logic
    
- Event Handlers
    
- Schedulers
    
- Initialization Tasks
    


### Delayed Component (Default)

```java
@Component
```

or

```java
@Component(immediate = false)
```

Activated only when its service is requested.

Flow:

```text
Bundle Starts
      ↓
Component Waits
      ↓
Service Requested
      ↓
Component Activates
```

### Note

Most business services do not require:

```java
immediate = true
```


## OSGi Component States

Component status can be viewed from:

```text
/system/console/components
```

### Active

```text
Component Running Successfully
```


### Satisfied

```text
All Dependencies Available
Ready For Activation
```


### Unsatisfied Reference

```text
Required Dependency Missing
```

Example:

```java
@Reference
private NewsService newsService;
```

If `NewsService` is unavailable:

```text
Component State:
Unsatisfied Reference
```

The component will not activate.


## OSGi Run Mode Configurations

AEM supports environment-specific configurations.

Common folders:

```text
config.author
config.publish

config.dev
config.stage
config.prod
```

### Example

#### config.author

```json
{
  "restAPIurl": "https://dev-api.com"
}
```

#### config.publish

```json
{
  "restAPIurl": "https://prod-api.com"
}
```

This allows different environments to use different values without changing code.


## Frequently Used OSGi Consoles

### Bundle Console

```text
/system/console/bundles
```

Used to:

- View Bundles
    
- Start Bundles
    
- Stop Bundles
    
- Check Bundle State
    


### Component Console

```text
/ system / console / components
```

Used to:

- View Components
    
- Check Activation Status
    
- Find Unsatisfied References
    
- Debug Dependency Issues
    

### Configuration Manager

```text
/system/console/configMgr
```

Used to:

- Create Configurations
    
- Update Configurations
    
- View PIDs
    
- Manage OSGi Properties
    

## OSGi Service Flow in AEM

Typical architecture:

```text
HTL
 ↓
Sling Model
 ↓
OSGi Service
 ↓
External API / JCR Repository
 ↓
Response
```

Example:

```text
Header.html
      ↓
HeaderModel
      ↓
NewsService
      ↓
REST API
      ↓
News Data Returned
```

## Best Practices in AEM

- Keep constants out of Java code.
    
- Store environment-specific values in OSGi Configuration.
    
- Use `@Designate` for typed configuration.
    
- Use `@Modified` to react to configuration changes.
    
- Use `@Reference` for service injection.
    
- Prefer Interface + Implementation pattern.
    
- Prefer repository-based configuration for deployments.
    
- Avoid hardcoding API URLs, keys, and environment-specific values.
    

## What Was Missing

Important concepts to remember:

- OSGi Configuration is handled by Configuration Admin (Metatype).
    
- `@ObjectClassDefinition` defines the configuration schema.
    
- `@AttributeDefinition` defines individual configuration fields.
    
- `@Designate` binds configuration to the component.
    
- `@Modified` executes when configuration changes.
    
- `@Reference` performs service injection.
    
- Repository-based configuration is preferred for deployments.
    

## Interview / Exam Points

1. OSGi Configuration is used to externalize dynamic values.
    
2. It avoids hardcoding values such as API URLs and keys.
    
3. `@ObjectClassDefinition` defines the configuration schema.
    
4. `@AttributeDefinition` defines configuration field metadata.
    
5. `@Designate` links configuration to the component.
    
6. `@Activate` reads configuration during component startup.
    
7. `@Modified` updates values when configuration changes.
    
8. `@Reference` injects services.
    
9. Configuration can be managed through ConfigMgr.
    
10. Configuration can also be maintained using `PID.cfg.json`.
    

## Key Takeaways

- OSGi Services are typically implemented using Interface + Implementation.
    
- OSGi maintains a Service Registry for dependency injection.
    
- Every Service is a Component, but every Component is not a Service.
    
- Every OSGi Configuration has a unique PID.
    
- Components can be Immediate or Delayed.
    
- Unsatisfied References prevent component activation.
    
- Run Modes support environment-specific configuration.
    
- The most important OSGi consoles are:
    

```text
/system/console/bundles
/system/console/components
/system/console/configMgr
```

- In AEM, Sling Models typically consume OSGi Services, and OSGi Services contain the business logic.

---

# Day 16 - Sling Models
[12-06-2026]

## Sling Models

Sling Models are used to apply business logic to a component when the logic becomes difficult or impossible to implement directly in HTL.

They act as a bridge between:

```text
JCR Content
    ↓
Sling Model
    ↓
   HTL
```

A Sling Model can:

- Read component properties from JCR.
    
- Read multifield data.
    
- Perform calculations and business logic.
    
- Consume OSGi Services.
    
- Export content as JSON.
    
## @Model

Used to register a class as a Sling Model.

```java
@Model(
    adaptables = {
        Resource.class,
        SlingHttpServletRequest.class
    },
    resourceType = "newsportal/components/raju",
    defaultInjectionStrategy = DefaultInjectionStrategy.OPTIONAL
)
```

### `adaptables`

Sling Models work using the concept of **Adaptation**.

![[Adaption in Sling Model]]


`adaptables` specifies from which objects the model can be created.

```java
adaptables = {
    Resource.class,
    SlingHttpServletRequest.class
}
```

Allows:

```java
resource.adaptTo(MenuItemsModel.class);
```

```
JCR Node
    ↓
Resource
    ↓ adaptTo()
Sling Model
    ↓
   HTL
```

and

```java
request.adaptTo(MenuItemsModel.class);
```

```
JCR Node
    ↓
Request
    ↓ adaptTo()
Sling Model
    ↓
   HTL
```


Meaning:

```text
Resource / Request
        ↓
Adaptation
        ↓
Sling Model Object
```

### `resourceType`

```java
resourceType = "newsportal/components/raju"
```

Associates the Sling Model with a specific component.


### `defaultInjectionStrategy`

```java
defaultInjectionStrategy =
    DefaultInjectionStrategy.OPTIONAL
```

If a property is missing:

```text
Model Creation Continues
Value = null
```

instead of failing.

## Injection

Injection means automatically populating Java fields from JCR cotent or Sling objects.

### @ValueMapValue

Used to inject component properties.

Example:

```java
@ValueMapValue
private String text;
```

Equivalent to:

```java
resource.getValueMap()
        .get("text");
```


## @Required and @Optional

### @Required

Property must exist.

```java
@Required
@ValueMapValue
private String title;
```

If missing:

```text
Model Creation Fails
```

### @Optional

Property is optional.

```java
@Optional
@ValueMapValue
private String description;
```

If missing:

```text
Value = null
```

Model creation continues.


## @Named and @Default

Used when the JCR property name cannot be directly mapped to a Java field.

Example:

```java
@ValueMapValue(name = "sling:resourceType")
@Named("sling:resourceType")
@Default(values = "newsportal/components/raju")
private String slingResourceType;
```

### Why?

Property names such as:

```text
sling:resourceType
jcr:title
cq:lastModified
```

cannot be used directly as Java variable names.

### @Default

Provides a fallback value when the property does not exist.


## @Exporter

Used to export Sling Models as JSON.

```java
@Exporter(
    extensions = "json",
    name = "jackson"
)
```

or

```java
@Exporter(
    extensions = ExporterConstants.SLING_MODEL_EXTENSION,
    name = ExporterConstants.SLING_MODEL_EXPORTER_NAME
)
```

### Output

```text
/component.model.json
```

Example:

```json
{
  "title":"Sports",
  "description":"Sports News"
}
```


## @OSGiService

Used to inject an OSGi Service into a Sling Model.

```java
@OSGiService
private NewsService newsService;
```

Flow:

```text
OSGi Service Registry
          ↓
      Service
          ↓
     Sling Model
```


## @Self

Used to inject the current adaptable object.

Example:

```java
@Self
private SlingHttpServletRequest request;
```

or

```java
@Self
private Resource resource;
```

Can also be used to inject another Sling Model.


## @Reference vs @OSGiService

### @Reference

Used inside OSGi Components.

```java
@Component
public class DemoService {

    @Reference
    private NewsService service;
}
```

Purpose:

```text
OSGi Service
      ↓
OSGi Service
```


### @OSGiService

Used inside Sling Models.

```java
@OSGiService
private NewsService service;
```

Purpose:

```text
OSGi Service
      ↓
Sling Model
```


## `@ChildResource`

Used to inject child resources.

Commonly used for `Multifields`.

Example JCR Structure:

```text
menu
 ├── item0
 ├── item1
 └── item2
```

Model:

```java
@ChildResource
private List<Resource> menu;
```

Dialog:

```text
name = "./menu"
```

Sling automatically maps:

```text
menu
 ├── item0
 ├── item1
 └── item2
```

into:

```java
List<Resource>
```


## Sling Model Lifecycle

### `@PostConstruct`

Executed after all injections are completed.

Flow:

```text
Create Model
      ↓
Inject Properties
      ↓
Inject Child Resources
      ↓
@PostConstruct
      ↓
Model Ready
```

Example:

```java
@PostConstruct
public void init() {

    Date today = new Date();

    if(expireDate != null &&
       expireDate.compareTo(today) < 0) {

        articleExpired = true;
    }
}
```

Purpose:

```text
Perform Initialization
Apply Business Logic
Prepare Data For HTL
```


## `MenuItemsModel` Example

`MenuItemsModel`

```java
package com.karthik.newsportal.core.models;

import java.util.Date;
import java.util.List;

import javax.annotation.PostConstruct;

import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.models.annotations.DefaultInjectionStrategy;
import org.apache.sling.models.annotations.Exporter;
import org.apache.sling.models.annotations.Model;
import org.apache.sling.models.annotations.injectorspecific.ChildResource;
import org.apache.sling.models.annotations.injectorspecific.ValueMapValue;


@Model(adaptables = {Resource.class, SlingHttpServletRequest.class}, 
resourceType = "newsportal/components/raju", 
defaultInjectionStrategy = DefaultInjectionStrategy.OPTIONAL)
@Exporter(extensions = "json", name = "jackson")
public class MenuItemsModel {

    @ValueMapValue
    private String text;

    @ValueMapValue
    private String desc;

	@ValueMapValue
    private Date expireDate;
	

	public String getText() {
		return text;
	}

	public String getDesc() {
		return desc;
	}

	public Date getExpireDate() {
		return expireDate;
	}

	public boolean articleExpired = false;

    public boolean isArticleExpired() {
		return articleExpired;
	}
    
    public List<RelatedMenuItemsModel> getMenu() {
		return menu;
	}
	
	@ChildResource
    private List<RelatedMenuItemsModel> menu;

	@PostConstruct
    public void init() {
    	Date today = new Date();
    	if(expireDate != null && expireDate.compareTo(today)<0) {
    		articleExpired = true;
    	}
    }
    
}

```

### Responsibilities

1. Read component properties.
    
2. Read multifield items.
    
3. Calculate article expiry status.
    
4. Export data as JSON.
    

### Injected Properties

```java
@ValueMapValue
private String text;

@ValueMapValue
private String desc;

@ValueMapValue
private Date expireDate;
```

Reads:

```text
text
desc
expireDate
```

from JCR.


### Multifield Injection

```java
@ChildResource
private List<RelatedMenuItemsModel> menu;
```

Repository:

```text
menu
 ├── item0
 ├── item1
 └── item2
```

Automatically becomes:

```java
List<RelatedMenuItemsModel>
```


### Expiry Logic

```java
@PostConstruct
public void init() {

    Date today = new Date();

    if(expireDate != null &&
       expireDate.compareTo(today) < 0) {

        articleExpired = true;
    }
}
```

Checks whether the configured expiry date is earlier than the current date.


## `RelatedMenuItemsModel`

`RelatedMenuItemsModel.java`

```java
package com.karthik.newsportal.core.models;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.models.annotations.Model;
import org.apache.sling.models.annotations.injectorspecific.ValueMapValue;

@Model(adaptables = {Resource.class})
public class RelatedMenuItemsModel {

    @ValueMapValue
    private String menuText;

    @ValueMapValue
    private String menuLink;
    
    public String getMenuText() {
		return menuText;
	}

	public String getMenuLink() {
		return menuLink;
	}
	
}
```

Represents a single multifield item.

```java
@Model(adaptables = Resource.class)
public class RelatedMenuItemsModel {

    @ValueMapValue
    private String menuText;

    @ValueMapValue
    private String menuLink;
}
```

Each child node:

```text
item0
item1
item2
```

is adapted into:

```java
RelatedMenuItemsModel
```

objects.


## HTL Usage

```html
<div
data-sly-use.model=
"com.karthik.newsportal.core.models.MenuItemsModel">

    <div
    data-sly-test="${!model.articleExpired}">

        <h1>${model.text}</h1>
        <p>${model.desc}</p>

    </div>

</div>
```

### Flow

```text
HTL
 ↓
data-sly-use
 ↓
Create Sling Model
 ↓
Inject Values
 ↓
@PostConstruct
 ↓
Return Model
 ↓
Render Content
```


## Best Practices

1. Keep fields private.
    
2. Use getters instead of public fields.
    
3. Put business logic inside Sling Models, not HTL.
    
4. Use OSGi Services for complex business logic.
    
5. Use @ChildResource for multifields.
    
6. Use @Exporter for Headless CMS requirements.
    
7. Prefer Sling Models over directly accessing JCR in HTL.
    

## Interview Questions

### Why use Sling Models?

To separate business logic from HTL and provide a clean Java representation of component content.


### What is Adaptation?

Converting a Sling object such as Resource or Request into a Sling Model using:

```java
adaptTo()
```


### Difference between @Reference and @OSGiService?

```text
@Reference
OSGi Service → OSGi Service

@OSGiService
OSGi Service → Sling Model
```


### Difference between @ChildResource and @ValueMapValue?

```text
@ValueMapValue
Reads Properties

@ChildResource
Reads Child Nodes
```


### When does @PostConstruct execute?

After all injections are completed and before the model is used by HTL.


### One-Line Summary

Sling Models convert JCR content into Java objects, apply business logic, consume services, process `multifields`, and expose data to HTL or JSON exporters.

---

