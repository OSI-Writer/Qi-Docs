SdsType API calls
==================

The API calls in this section are all used to create and manipulate SdsTypes. 
SdsType management via the Sequential Data Store (Sds) Client Libraries is performed through the 
``ISdsMetadataService`` interface, which is accessed using the 
``SdsService.GetMetadataService( )`` helper.  
See `SdsTypes <https://qi-docs.readthedocs.org/en/latest/Qi_Types.html>`__ 
for general SdsType information, working with compound indexes, and supported SdsTypes.


***********************


``GetStreamTypeAsync()``
----------------------

Returns the type definition that is associated with a given stream from the specified namespace.

**Syntax**

::

    Task<SdsType> GetStreamTypeAsync(string streamId);

*Http*
::

    GET Sds/{tenantId}/{namespaceId}/Streams/{streamId}/Type


**Parameters**

``string tenantId``
  The tenant identifier for the request
``string namespaceId``
  The namespace identifier for the request
``string streamId``
  The Id of the stream to search for the specified type definition


**Returns**

  SdsType type definition


Security
  Allowed by administrator and user accounts


***********************


``GetTypeAsync()``
----------------

Returns the type of the specified ``typeId`` from the specified namespace. 

**Syntax**

::

    Task<SdsType> GetTypeAsync(string typeId);

*Http*

::

    GET Sds/{tenantId}/{namespaceId}/Types/{typeId}

**Parameters**

``string tenantId``
  The tenant identifier for the request
``string namespaceId``
  The namespace identifier for the request
``string typeId``
  The Id of the type to retrieve


**Returns**
  An SdsType specified by the typeId

Security
  Allowed by administrator and user accounts


***********************


``GetTypesAsync()``
----------------

Returns a list of all types within a given namespace. 

**Syntax**

::

    Task<IEnumerable<SdsType>> GetTypesAsync( );


*Http*

::

    GET Sds/Types


**Parameters**

``string tenantId``
  The tenant identifier for the request
``string namespaceId``
  The namespace identifier for the request

**Returns**

  IEnumerable SdsType of all types in the namespace


Security
  Allowed by administrator and user accounts


***********************


``GetOrCreateTypeAsync()``
----------------

Returns the type of the specified ``typeId`` within a namespace, or creates the type if the ``typeId`` does not 
already exist. If the ``typeId`` exists, it is returned to the caller unchanged. 


**Syntax**

::

    Task<SdsType> GetOrCreateTypeAsync(SdsType sdstype);

*Http*

::

    POST Sds/{tenantId}/{namespaceId}/Types



**Parameters**

``string tenantId``
  The tenant identifier for the request
``string namespaceId``
  The namespace identifier for the request
``SdsType sdstype``
  The type of the stream for which the type request is made


**Returns**

  SdsType


Security
  Allowed by administrator account

**Notes**

.. _Introducing JSON: http://json.org/index.html

 For HTTP requests, the message content (the event) must be serialized in JSON format. JSON objects consist of a 
 series of name-value property pairs enclosed within brackets. Because SdsType objects can become complex (particularly 
 when properties themselves are SdsTypes), OSIsoft recommends using a JSON serializer (available at `Introducing JSON`_). 
 The following example shows the serialization of the SdsType object from the WaveData example. See the Sds code 
 samples for the complete WaveData example.


::

	{
		"Id":"WaveData_SampleType",
		"Name":"Wave Data Type",
		"Description":"This is a type for WaveData events",
		"SdsTypeCode":0,
		"Properties":[
			{
				"Id":"Order",
				"Name":null,
				"Description":null,
				"SdsType":
					{
						"Id":"intType",
						"Name":null,
						"Description":null,
						"SdsTypeCode":9,
						"Properties":null
					},
				"IsKey":true
			},
			{
				"Id":"Tau",
				"Name":null,
				"Description":null,
				"SdsType":
					{
						"Id":"doubleType",
						"Name":null,
						"Description":null,
						"SdsTypeCode":14,
						"Properties":null
					},
				"IsKey":false
			},
			{
				"Id":"Radians",
				"Name":null,
				"Description":null,
				"SdsType":
					{
						"Id":"doubleType",
						"Name":null,
						"Description":null,
						"SdsTypeCode":14,
						"Properties":null
					},
				"IsKey":false
			},
			{
				"Id":"Sin",
				"Name":null,
				"Description":null,
				"SdsType":
					{
						"Id":"doubleType",
						"Name":null,
						"Description":null,
						"SdsTypeCode":14,
						"Properties":null
					},
					"IsKey":false
			},
			{
				"Id":"Cos",
				"Name":null,
				"Description":null,
				"SdsType":
					{
						"Id":"doubleType",
						"Name":null,
						"Description":null,
						"SdsTypeCode":14,
						"Properties":null
					},
				"IsKey":false
			},
			{
				"Id":"Tan",
				"Name":null,
				"Description":null,
				"SdsType":
					{
						"Id":"doubleType",
						"Name":null,
						"Description":null,
						"SdsTypeCode":14,
						"Properties":null
					},
				"IsKey":false
			},
			{
				"Id":"Sinh",
				"Name":null,
				"Description":null,
				"SdsType":
					{
						"Id":"doubleType",
						"Name":null,
						"Description":null,
						"SdsTypeCode":14,
						"Properties":null
					},
				"IsKey":false
			},
			{
				"Id":"cosh",
				"Name":null,
				"Description":null,
				"SdsType":
					{	
						"Id":"doubleType",
						"Name":null,
						"Description":null,
						"SdsTypeCode":14,
						"Properties":null
					},
				"IsKey":false
			},
			{
				"Id":"Tanh",
				"Name":null,
				"Description":null,
				"SdsType":
					{
						"Id":"doubleType",
						"Name":null,
						"Description":null,
						"SdsTypeCode":14,
						"Properties":null
					},
				"IsKey":false
			}
		]
	}

***********************


``DeleteTypeAsync()``
----------------

Deletes a type from the specified namespace. Note that a type cannot be deleted if any 
streams are associated with it.

**Syntax**

::

    Task DeleteTypeAsync(string typeId);

*Http*

::

    DELETE Sds/{tenantId}/{namespaceId}/Types/{typeId}



**Parameters**

``string tenantId``
  The tenant identifier for the request
``string namespaceId``
  The namespace identifier for the request
``string typeId``
  The Id of the type to delete

**Returns**

  Sdstype


Security
  Allowed by administrator account


***********************


``UpdateTypeAsync()``
----------------

Updates the definition of a type. Note that a type cannot be updated if any streams are 
associated with it. Also, certain parameters cannot be changed after they are defined.

**Syntax**

::

    Task UpdateTypeAsync(string typeId, SdsType Sdstype);

*Http*

::

    PUT Sds/{tenantId}/{namespaceId}/Types/{typeId}


Content is a serialized SdsType object.

**Parameters**

``string tenantId``
  The tenant identifier for the request
``string namespaceId``
  The namespace identifier for the request
``string Sdstype``
  The Sdstype of the type to update


**Returns**

  Sdstype

Security
  Allowed by Administrator account
