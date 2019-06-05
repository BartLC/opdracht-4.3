Maak een script waarmee je x aantal dagen oude files uit een folder kunt verwijderen.

$x is hier de variabele. Zie ook appendex B van het boek

$set1 = (Get-Date).AddDays(-10)
$set2 = (Get-Date).AddDays(-20)
$set3 = (Get-Date).AddDays(-30)
$set4 = (Get-Date).AddDays(-40)

Get-Item C:\data1\File_?.txt | ForEach-Object {$_.CreationTime = $set1}
Get-Item C:\data1\File_1.txt | ForEach-Object {$_.CreationTime = $set2}
Get-Item C:\data1\File_2.txt | ForEach-Object {$_.CreationTime = $set3}
Get-Item C:\data1\File_3.txt | ForEach-Object {$_.CreationTime = $set4}

$days = (Get-Date).AddDays(-20)
Get-ChildItem -Path 'C:\data1' -Recurse -Force | Where-Object {!$_.PSIsContainer -and $_.CreationTime -lt $days} | Remove-Item 
