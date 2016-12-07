======================
QiType information
======================

This section contains information about how to configure and use QiTypes. To use Qi,
you define QiTypes to describe the kinds of data you want to store, 
then you create QiStreams that are associated with your QiTypes.


A QiType consists of one or more QiTypeProperties that can be a simple atomic type (such as an integer) 
or can be a complex type, represented as another QiType. You can create a nested type by adding a QiType 
as a property of another QiType; in this case, note that it is not necessary to first post the 
nested QiType to Qi. In other words, the nested QiType is not required to exist in Qi as a 
standalone type before it is posted as part of a nested type.

A type is always referenced with its Id property. Using a QiType as a property permits the construction 
of complex, nested data types. A QiType must have one or more properties that constitute an ordered 
key to be used as an index. While a timestamp (DateTime) is a very common type of key, any ordered 
value is permitted.

When a QiType is created it cannot be changed and can only be deleted if
no streams are associated with it.

QiType management via the Qi Client Libraries is performed through the ``IQiMetadataService`` interface, which may be accessed via the ``QiService.GetMetadataService( )`` helper.

The following table shows the required and optional QiType properties:

+---------------+-------------------------+----------------------------------------+
| Property      | Type                    | Details                                |
+===============+=========================+========================================+
| Id            | String                  | Required Id for referencing the type   |
+---------------+-------------------------+----------------------------------------+
| Name          | String                  | Optional name                          |
+---------------+-------------------------+----------------------------------------+
| Description   | String                  | Optional description text              |
+---------------+-------------------------+----------------------------------------+
| QiTypeCode    | QiTypeCode              | Defines the type                       |
+---------------+-------------------------+----------------------------------------+
| Properties    | IList<QiTypeProperty>   | List of QiTypeProperty items           |
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

When defining a QiType, the index property you use to sequence the
data must be defined in the type definition. Often, a single
index such as DateTime is used, but for more complex scenarios Qi
allows multiple indexes to be defined in a type. Multiple indexes are
concatenated to form a compound index. The Qi REST API methods
that use tuples were created to assist you to use compound
indexes. A maximum of three keys is permitted in a particular
compound index.

Supported QiTypes
----------------

The following types are supported when
creating a QiType:

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

