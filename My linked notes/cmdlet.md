Most PowerShell usage is founded on cmdlets. A cmdlet is a **compiled library that exposes some configuration or administrative task, such as starting a VM in Hyper-V. Cmdlets use a Verb-Noun naming convention. Cmdlets always return an object**. Typically, the return from a cmdlet will be **piped** to some other cmdlet or function. For example:

Get-Process | Where { $_.name -eq 'nmap' } | Format-List

You can also define simple functions for use within your scripts. Custom functions are declared within curly brackets:

function Cat-Name {

 param ($name,$surname)

 return $name + ' ' + $surname

}

/#This ends the function declaration; the next statement calls it  Had to add /

$greeting = 'Hello ' + $(Cat-Name('World',''))

Write-Host $greeting

**Note that a variable is declared by prefixing a label with $.** 