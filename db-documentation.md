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
* select
* delete

## Global options
**Keys**:
```xml
<commands>
  <insert table="xxx">
    <keys NO="autoincrement" YYY="constantvalue"/>
    <fields zzz="123"/>
  </insert>
</commands>
```
The keys will be returned at the end. Example:
```xml
<results status="1">
  <insert table="xxx" NO="1" YYY="constantvalue"></insert>
</results>
```

**Fields**:
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

**Where**:
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
A SQL Where is generated from the `<where>` structure

## Insert
Example of command
