QiType API calls
==================

The API calls in this section are all used to create and manipulate QiTypes. See .. _Qi Types: https://github.com/osisoft/Qi-Docs/blob/Qi_Edits/docs/Qi_Types.rst for a list of supported QiTypes, a discussion of compound indexes, and general information about QiTypes. 

``GetStreamType()``
----------------

Returns the type definition that is associated with a given stream from the specified namespace.

**Syntax**

::

    QiType GetStreamType(string namespaceId, string streamId);
    Task<QiType> GetStreamTypeAsync(string namespaceId, string streamId);

*Http*
::

    GET Qi/{namespaceId}/Streams/{streamId}/Type


**Parameters**

string ``namespaceId``
  The namespace identifier for the request
string ``streamId``
  The ID of the stream to search for the specified type definition

**Optional parameters**

    None

**Returns**

  Qitype type definition


Security
  Allowed by administrator and user accounts


``GetType()``
----------------

Returns the type of the specified ``typeId`` from the specified namespace. 

**Syntax**

::

    QiType GetType(string namespaceId, string typeId);
    Task<QiType> GetTypeAsync(string namespaceId, string typeId);

*Http*

::

    GET Qi/{namespaceId}/Types/{typeId}

**Parameters**

``string namespaceId``
  The namespace identifier for the request
``typeId``
  The ID of the type to retrieve

**Optional parameters**

  None
  
**Returns**
  A QiType specified by the typeId

Security
  Allowed by administrator and user accounts


``GetTypes()``
----------------

Returns a list of all types within a given namespace. 

**Syntax**

::

    IEnumerable<QiType> GetTypes();
    Task<IEnumerable<QiType>> GetTypesAsync();

*Http*

::

    GET Qi/Types


**Parameters**

``string namespaceId``
  The namespace identifier for the request
``QiType entity``
  The object

**Optional parameters**

  None

**Returns**

  IEnumerable QiType of all types in the namespace


Security
  Allowed by administrator account


``GetOrCreateType()``
----------------

Returns the type of the specified ``typeId`` within a namespace, or creates the type if the ``typeId`` does not already exist. If the typeId exists, it is returned to the caller unchanged. 


**Syntax**

::

    QiType GetOrCreateType(string namespaceId, QiType entity);
    Task<QiType> GetOrCreateTypeAsync(string namespaceId, QiType entity);

*Http*

::

    POST Qi/{namespaceId}/Types



**Parameters**

``string namespaceId``
  The namespace identifier for the request
``QiType entity``
  The ID of the stream for which the type request is made

**Optional parameters**

  None

**Returns**

  Qitype


Security
  Allowed by administrator account


``DeleteType()``
----------------

Deletes a type from the specified namespace. Note that a type cannot be deleted if there are streams associated with it.

**Syntax**

::

    void DeleteType(string namespaceId, string typeId);
    Task DeleteTypeAsync(string namespaceId, string typeId);

*Http*

::

    DELETE Qi/{namespaceId}/Types/{typeId}



**Parameters**

``string namespaceId``
  The namespace identifier for the request
``string typeId``
  The ID of the type to delete

**Optional parameters**

  None

**Returns**

  Qitype


Security
  Allowed by administrator account


``UpdateType()``
----------------

Updates the definition of a type. Note that a type cannot be updated if there are streams associated with it.

**Syntax**

::

    void UpdateType(string namespaceId, string typeId, QiType entity);
    Task UpdateTypeAsync(string namespaceId, string typeId, QiType entity);

*Http*

::

    PUT Qi/{namespaceId}/Types/{typeId}


**Parameters**

``string namespaceId``
  The namespace identifier for the request
``string typeId``
  The typeId of the type to update

**Optional parameters**

  None

**Returns**

  Qitype

Security
  Allowed by Administrator account
