# DB Documentation

## Structure
An englobing node (commands):
```xml
<commands>
  <!-- One or more commands here -->
</commands>
```

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
The keys will be returned at the end. Example
```xml
<results status="1">
  <insert table="xxx" NO="1" YYY="constantvalue"></insert>
</results>
```

## Commands
For now, these are the possible commands:
* insert
* insertupdate
* update
* select

## Insert
Example of 
