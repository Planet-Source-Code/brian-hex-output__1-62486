<div align="center">

## Hex Output


</div>

### Description

Generates text on the right side and the hex output on the left side.

ex.

0D 0A 44 61 74 65 3A 20 54 68 75 2C 20 30 38 20 | ..Date: Thu, 08
 
### More Info
 
Text, width of hex row


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Brian](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/brian.md)
**Level**          |Beginner
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |VB 6\.0
**Category**       |[String Manipulation](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/string-manipulation__1-5.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/brian-hex-output__1-62486/archive/master.zip)





### Source Code

```
Private Function HexOutput(strData As String, Optional intWidth As Integer = 16) As String
Dim intCount As Integer
Dim bytAsc As Byte
Dim strFormat As String
Dim strOut As String
Dim strText As String
 For intCount = 1 To Len(strData)
  bytAsc = Asc(Mid$(strData, intCount, 1))
  Select Case Len(Hex(bytAsc))
   Case 0: strFormat = "00"
   Case 1: strFormat = "0" & Hex(bytAsc)
   Case 2: strFormat = Hex(bytAsc)
  End Select
  strOut = strOut & strFormat & Chr$(32)
  If ((bytAsc = 32 Or bytAsc > 32) And (bytAsc < 127 Or bytAsc > 160)) Then
   strText = strText & Chr$(bytAsc)
  Else
   strText = strText & "."
  End If
  If ((intCount Mod intWidth) = intWidth - 1) Then
   strOut = strOut & "| " & strText & vbCrLf
   strText = vbNullString
  End If
 Next intCount
 strOut = strOut & String$(3 * (intWidth - (intCount Mod intWidth)), " ")
 strOut = strOut & "| " & strText
 strOut = strOut & vbCrLf & vbCrLf
 HexOutput = strOut
End Function
```

