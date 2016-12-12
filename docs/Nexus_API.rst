Feature
==========

``GetTenantFeatureState()``
----------------------

Returns the current state of a feature for the tenant.

**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Tenants/{tenantId}/Features/{featureId}


**Parameters**

``String tenantId``
  The tenant identifier for the request
``String featureId``
  The identifier of the feature
  
**Security**
  Any OSIsoft Cloud Services user

*******************

GlobalGroup
==========

Group
==========

``GetGroup()``
----------------------

Returns the group associated with a tenant.

**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Tenants/{tenantId}/Groups/{groupId}

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String groupId``
  The group identifier for the request


**Security**
  OSIsoft Cloud Services tenant administrator


*********************


``GetGroups()``
----------------------

Returns a list of groups for a Tenant.

**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Tenants/{tenantId}/Groups

**Parameters**

``String tenantId``
  The tenant identifier for the request


**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``GetGroupMembers()``
----------------------

Returns a list of members within a specified group.

**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Tenants/{tenantId}/Groups/{groupId}/Users

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String groupId``
  The group identifier for the request

**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``Create()``
----------------------

Creates a group.

**Syntax**

.. highlight:: none

**Http**

::

  POST PICS/Tenants/{tenantId}/Groups

**Parameters**

``String tenantId``
  The tenant identifier for the request
``Group group``
  The group to be created

**Body**

::

  {
    "Name": "name",
    "AzureActiveDirectoryGroupName": "azureactivedirectorygroupname",
    "Description": "description" 
  }


**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``Delete()``
----------------------

Delete a specified group.

**Syntax**

.. highlight:: none

**Http**

::

  DELETE PICS/Tenants/{tenantId}/Groups/{groupId}

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String groupId``
  The group identifier for the request

**Security**
  OSIsoft Cloud Services tenant administrator


**********************


``AddUserToGroup()``
----------------------

Adds a specified user to a group.

**Syntax**

.. highlight:: none

**Http**

::

  POST PICS/Tenants/{tenantId}/Groups/{groupId}/Users

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String groupId``
  The group identifier for the request
``CreateUser user``
  The user to be added to the group
  
  
**Body**

::

  {
    "SendNotification": false,
    "IsAdministrator": false,
    "Id": "id",
    "FirstName": "firstname",
    "LastName": "lastname",
    "LoginName": "loginname",
    "ContactEmail": "contactemail",
    "ContactPhone": "contactphone",
    "UPN": "upn",
    "Password": "password"
  }


**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``RemoveUserFromGroup()``
----------------------

Deletes a specified user from a group.

**Syntax**

.. highlight:: none

**Http**

::

  DELETE PICS/Tenants/{tenantId}/Groups/{groupId}/Users/{userId}

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String groupId``
  The group identifier for the request
``String userId``
  The user identifier for the request

**Security**
  OSIsoft Cloud Services tenant administrator

**********************


Namespace
==========

``GetAll()``
----------------------

Returns a list of all namespaces within a specified tenant. 

**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Tenants/{tenantId}/Namespaces

**Parameters**

``String tenantId``
  The tenant identifier for the request


**Security**
  Any OSIsoft Cloud Services user


**********************


``GetNamespaceById()``
----------------------

Returns a namespace associated with a specified Id.

**Syntax**

.. highlight:: none


**Http**

::

  GET PICS/Tenants/{tenantId}/Namespaces/{Id}

**Parameters**

``String id``
  The identifier for the request
``String tenantId``
  The tenant identifier for the request

**Security**
  Any OSIsoft Cloud Services user


**********************



``Create()``
----------------------

Creates a namespace.

**Syntax**

.. highlight:: none

**Http**

::

  POST PICS/Tenants/{tenantId}/Namespaces


**Parameters**

``Namespace namespaceObj``
  The namespace to be created
  
**Body**


::

  {
    "Id": "id",
    "TenantId": "tenantid",
    "Description": "description",
    "TierId": "tierid"
  }

**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``Delete()``
----------------------

Deletes a namespace. 

**Syntax**

.. highlight:: none

**Http**

::

  DELETE PICS/Tenants/{tenantId}/Namespaces/{Id}

**Parameters**

``String id``
  The identifier for the request
``String tenantId``
  The tenant identifier for the request


**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``DeleteNamespaces()``
----------------------

Deletes one or more namespaces associated with a tenant.


**Syntax**

.. highlight:: none

**Http**

::

  DELETE PICS/Tenants/{tenantId}/Namespaces

**Parameters**

``String tenantId``


**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``UpdateNamespace()``
----------------------

Updates namespace information - description and the namespace tier.

**Syntax**

.. highlight:: none

**Http**

::

  PUT PICS/Tenants/{tenantId}/Namespaces/{Id}

**Parameters**

``String id``
  The identifier for the request
``String tenantId``
  The tenant identifier for the request
``Namespace namespaceObj``
  The namespace to be updated
  
  
**Body**

::

  {
    "Id": "id",
    "TenantId": "tenantid",
    "Description": "description",
    "TierId": "tierid"
  }


**Security**
  OSIsoft Cloud Services tenant administrator


**********************

ServiceBlog
==========

``GetByPage()``
----------------------

Returns a list of matching pages.


**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/ServiceBlog/Entries

**Parameters**

``Int32 skip``
  The number of matches to skip over before returning the matching page.
``Int32 take``
  The number of blogs to take after skip

**Security**
  Any OSIsoft Cloud Services user


**********************


ServiceBlogTemplate
==========

Service
==========

Tenant
==========

``GetTenant()``
----------------------

Returns a tenant associated with a specified tenantId


**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Tenants/{tenantId}

**Parameters**

``String tenantId``
  The tenant identifier for the request

**Security**
  Any OSIsoft Cloud Services user


**********************


TenantFeatureState
==========

TenantServiceState
==========

Applications
==========

``CreateClientApiKeySet()``
----------------------

Creates and returns a key that clients use to access Qi.

**Syntax**

.. highlight:: none

**Http**

::

POST PICS/Tenants/{tenantId}/ClientApiKeySets

**Parameters**

``ClientApiKeySet keySet``
  The keyset identifier for the request
  
**Body**

::

  {
    "AppUri": "appuri",
    "CreateFirstKey": false,
    "DisplayName": "displayname",
    "Facility": "facility",
    "RequiredResource": null,
    "TenantId": "tenantid"
  }


**Security**
  OSIsoft Cloud Services tenant administrator


**********************


``GetOrCreateClientApiKeySet()``
----------------------

**Syntax**

.. highlight:: none

**Http**

::

  POST PICS/Tenants/{tenantId}/GetOrCreateClientApiKeySets

**Parameters**

``ClientApiKeySet keySet``
  The tenant identifier for the request
  
**Body**

::

  {
    "AppUri": "appuri",
    "CreateFirstKey": false,
    "DisplayName": "displayname",
    "Facility": "facility",
    "RequiredResource": null,
    "TenantId": "tenantid"
  }


**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``DeleteClientApiKeySet()``
----------------------

Deletes a specified client key.

**Syntax**

.. highlight:: none

**Http**

::

  DELETE PICS/Tenants/{tenantId}/ClientApiKeySets/{applicationId}

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String applicationId``
  The application identifier for the request

**Security**
  OSIsoft Cloud Services tenant administrator


**********************


NamespaceTier
==========

Utilities
==========

``Ping()``
----------------------

Determines whether a specified tenant is active.

**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Utilities/ping

**Parameters**


**Security**
  Any OSIsoft Cloud Services user

**********************


User
==========

``Get()``
----------------------

Returns a user name based on tenant Id and user Id.

**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Tenants/{tenantId}/Users/{userId}

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String userId``
  The user identifier for the request

**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``Get()``
----------------------

Returns a list of users for a tenant.

**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Tenants/{tenantId}/Users

**Parameters**

``String tenantId``
  The tenant identifier for the request

**Security**
  OSIsoft Cloud Services tenant administrator


**********************


``GetUserGroups()``
----------------------

Returns a list of groups in a tenant that a user is a member of.

**Syntax**

.. highlight:: none

**Http**

::

  GET PICS/Tenants/{tenantId}/Users/{userId}/Groups

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String userId``
  The user identifier for the request


**Security**
  OSIsoft Cloud Services tenant administrator. The OSIsoft Cloud Services user which is the object of this call


**********************


``IsUserInGroup()``
----------------------

Determines whether a specified user is a member of a specified group.

**Syntax**

.. highlight:: none

**Http**

::

  HEAD PICS/Tenants/{tenantId}/Users/{userId}/Groups/{groupId}

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String userId``
  The user identifier for the request
``String groupId``
  The group identifier for the request

**Security**
  OSIsoft Cloud Services tenant administrator. The OSIsoft Cloud Services user which is the object of this call

**********************


``CreateUser()``
----------------------

Creates a user within a specified group.

**Syntax**

.. highlight:: none

**Http**

::

  POST PICS/Tenants/{tenantId}/Users/

**Parameters**

``String tenantId``
  The tenant identifier for the request
``CreateUser user``
  The user identifier for the request
  
**Body**

::

  {
    "SendNotification": false,
    "IsAdministrator": false,
    "Id": "id",
    "FirstName": "firstname",
    "LastName": "lastname",
    "LoginName": "loginname",
    "ContactEmail": "contactemail",
    "ContactPhone": "contactphone",
    "UPN": "upn",
    "Password": "password"
  }


**Security**
  OSIsoft Cloud Services tenant administrator

**********************

**Syntax**

.. highlight:: none

``Update()``
----------------------

Updates a specified user within a group.

**Http**

::

  PUT PICS/Tenants/{tenantId}/Users/{userId}

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String userId``
  The user identifier for the request
``CreateUser user``
  The user to be updated
  
  
**Body**

::

  {
    "SendNotification": false,
    "IsAdministrator": false,
    "Id": "id",
    "FirstName": "firstname",
    "LastName": "lastname",
    "LoginName": "loginname",
    "ContactEmail": "contactemail",
    "ContactPhone": "contactphone",
    "UPN": "upn",
    "Password": "password"
  }


**Security**
  OSIsoft Cloud Services tenant administrator


**********************


``Delete()``
----------------------
Deletes a user from a group.


**Syntax**

.. highlight:: none

**Http**

::

  DELETE PICS/Tenants/{tenantId}/Users/{userId}

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String userId``
  The user identifier for the request
  

**Security**
  OSIsoft Cloud Services tenant administrator

**********************


``ResetUserPassword()``
----------------------

Resets the password of the specified user Id.

**Syntax**

.. highlight:: none

**Http**

::

  POST PICS/Tenants/{tenantId}/Users/{userId}/passwordreset

**Parameters**

``String tenantId``
  The tenant identifier for the request
``String userId``
  The user identifier for the request


**Security**
  OSIsoft Cloud Services tenant administrator

**********************
