================
Type information
================

This section contains information about how to configure and use Types. To use the Sequential Data Store (Sds),
you define Types that describe the kinds of data you want to store, 
then you create Streams that are associated with your Types.

A Type consists of one or more SdsTypeProperties that can be a simple atomic type (such as an integer) 
or can be a complex type, represented as another SdsType. You can create a nested type by adding an SdsType 
as a property of another SdsType; in this case, note that it is not necessary to first post the 
nested SdsType to the Sequential Data Store. In other words, the nested SdsType is not required to exist 
in the Sequential Data Store as a 
standalone type before it is posted as part of a nested type.

A type is always referenced with its Id property. Using an SdsType as a property permits the construction 
of complex, nested data types. An SdsType must have one or more properties that constitute an ordered 
key to be used as an index. While a timestamp (DateTime) is a very common type of key, any ordered 
value is permitted.

When an SdsType is created it cannot be changed and can only be deleted if
no streams are associated with it.

SdsType management via the Sds Client Libraries is performed through the ``ISdsMetadataService`` 
interface, which may be accessed using the ``SdsService.GetMetadataService( )`` helper.

The following table shows the required and optional SdsType properties:

+---------------+-------------------------+----------------------------------------+
| Property      | Type                    | Details                                |
+===============+=========================+========================================+
| Id            | String                  | Required Id for referencing the type   |
+---------------+-------------------------+----------------------------------------+
| Name          | String                  | Optional name                          |
+---------------+-------------------------+----------------------------------------+
| Description   | String                  | Optional description text              |
+---------------+-------------------------+----------------------------------------+
| SdsTypeCode   | SdsTypeCode             | Defines the type                       |
+---------------+-------------------------+----------------------------------------+
| Properties    | IList<SdsTypeProperty>  | List of SdsTypeProperty items          |
+---------------+-------------------------+----------------------------------------+

**Rules for typeId**

1. Is not case sensitive
2. Can contain spaces
3. Cannot begin with two underscores ("\_\_")
4. Cannot contain forward slash or backslash characters ("/" or "\\")
5. Can contain a maximum of 260 characters
6. Cannot start or end with a period.
7. Cannot contain consecutive periods.
8. Cannot consist of only periods.


Compound Indexes
----------------

When defining an SdsType, the index property you use to sequence the
data must be defined in the type definition. Often, a single
index such as DateTime is used, but for more complex scenarios Sds
allows multiple indexes to be defined in a type. Multiple indexes are
concatenated to form a compound index. The Sds REST API methods
that use tuples were created to assist you to use compound
indexes.

Supported SdsTypes
----------------

The following types are supported when
creating an SdsType:

======================   =================   =======================
Array                    Boolean             BooleanArray
Byte                     ByteArray           ByteEnum
Char                     CharArray           DateTime
DateTimeArray            DateTimeOffset      DateTimeOffsetArray
DBNull                   Decimal             DecimalArray
Double                   DoubleArray         Empty
Guid                     GuidArray           IDictionary
IEnumerable              IList               Int16
Int16Array               Int16Enum           Int32
Int32Array               Int32Enum           Int64
Int64Array               Int64Enum           NullableBoolean
NullableByte             NullableChar        NullableDateTime
NullableDateTimeOffset   NullableDecimal     NullableDouble
NullableGuid             NullableInt16       NullableInt32
NullableInt64            NullableSByte       NullableSingle
NullableTimeSpan         NullableUInt16      NullableUInt32
NullableUInt64           Object              SByte
SByteArray               SByteEnum           Single
SingleArray              String              StringArray
TimeSpan                 TimeSpanArray       UInt16
UInt16Array              UInt16Enum          UInt32
UInt32Array              UInt32Enum          UInt64
UInt64Array              UInt64Enum          Version
VersionArray
======================   =================   =======================

