# VfpStreamReader
`VfpStreamReader` Allows character data to be read from a buffer stream


<h2>Overview</h2>

`VfpStreamReader` can either look ahead or behind for a specific character evaluation by using the funcion <code>Peek()()</code> or <code>LookBehind().</code>

## Installation

```
Just copy the VfpStreamReader prg anywhere into your project PATH folder.
```

## Simple Test
```xBase
// declare the StreamReader Prg
Set Procedure to "StreamReader" Additive
```
## Instantiate StreamReader Object

```xBase
oReader = CreateObject("StreamReader")
```
## Load the Stream

```xBase
// Using simple text
oReader.SetString("sample string")
// or a file stream
oReader.SetString(FileToStr("c:\myfile.any")
```
## Read() Method
```xBase
// Read the next character 
?oReader.Read()
```
## Read all characters
```xBase
// be aware of checking the EndOfStream property in every iteration
Do While !oReader.EndOfStream
	?oReader.Read()
EndDo
```
### LookBehind() method
```xBase
// you can look N positions behind but remember to check the Chr(255) character
// that represents end or begin of stream.
nPosition = 0
lcChar = oReader.LookBehind(nPosition)
Do While lcChar != Chr(255)
	nPosition = nPosition + 1
	lcChar = oReader.LookBehind(nPosition)
EndDo
```
## Peek() method
```xBase
// the Peek() method allows you to evaluate the next character without affecting current one.
If oReader.Peek() = "*" Then
	?"This is a comment line..."
EndIf
```

## License

`VfpStreamReader` is released under the MIT Licence.
