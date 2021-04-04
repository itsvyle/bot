# DB Documentation

## Structure
An englobing node (commands):
```xml
<commands>
  <!-- One or more commands here -->
</commands>
```

## Commands
For now, these are the possible commands:
* insert
* insertupdate
* update
* [select](#select)
* delete

## Global options
These are options that will be used in more than one type of command

### Keys:
```xml
<commands>
  <insert table="xxx">
    <keys NO="autoincrement" YYY="constantvalue"/>
    <fields zzz="123"/>
  </insert>
</commands>
```

_Possible key values_:
* autoincrement : Used in an `<insert>` command, for the autoincrement columns

The keys will be returned at the end. Example:
```xml
<results status="1">
  <insert table="xxx" NO="1" YYY="constantvalue"></insert>
</results>
```

### Fields:
```xml
<commands>
  <insert table="xxx">
    <fields zzz="123"/>
  </insert>
</commands>
```
For each command
* insert : The column values of the row that is added
* update : The new values
* select : The fields to be fetched. Then, the attribute value is the type of the field (xml, string, long)

**Note**: `<xmlfield XML_FIELD="string"><!-- XML HERE --></xmlfield>` can also be used to insert xml

### systemfields
```xml
<commands>
  <insert table="xxx">
    <fields zzz="123"/>
    <systemfields date="systemdate"/>
  </insert>
</commands>
```
These field's values are automatically set by DB.php
_Possible values_:
* systemdate : the current system date
* mastersystemdate : the date at which the request started
* lastinsertid : The last sql insert id

### Where:
```xml
<commands>
  <select table="xxx">
    <fields zzz="string"/>
    <where>
      <condition table="xxx" field="zzz" sign="equal" value="123" type="string"/>
    </where>
  </select>
</commands>
```
A SQL Where is generated from the `<where>` structure.

## Select
### Extra options :

#### orderby:
```xml
<orderby field1="NO" field2="NAME"/>
```
orderby is used to precise by which column the rows are sorted.

**Note**: `ASC` can be added after the field name to reverse sort 

#### groupby:
```xml
<groupby field1="NO" field2="NAME"/>
```
groupby is used to precise by which column the rows are grouped (executes the sql `GROUPBY` option).
