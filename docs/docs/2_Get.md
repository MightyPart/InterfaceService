# :Get()

**:Get(selector, ancestor &lt;optional&gt;)** is a function that requires at least one arguement (selector), it also returns information in the form of a dictionary. This function gets a list of matching elements based on a selector and an (optional) ancestor.

!!! notice "[`:MouseEnter()`](/docs/4_MouseEnter.html), [`:Mouseleave()`](/docs/5_MouseLeave.html), [`:LeftClick()`](/docs/6_LeftClick.html), [`:RightClick()`](/docs/7_RightClick.html), [`:MouseClick()`](/docs/8_MouseClick.html) and [`:Changed()`](/docs/90_Changed.html) can be used on :Get()"

## Arguements
| Arguement | Description |
--- | ---
| `selector` | A String (ClassName, Name or Id) or an Instance that defines the type of GUI Instance |
| `ancestor` | An optional variable that defines the ancestor that all of the GUI Instances have to be a descendant of in order for it to be included in the `matchingElements` table of [the dictionary returned by :Get()](/docs/2_Get.html#dictionary-returned). If the selector arguement is an Instance then ancestor arguement is ignored. |

`ClassName` - To indicate that the selector arguement is a ClassName the string should preceed with a `.` - for example, ".TextButton". Abbreviations can be used instead of ClassNames, they are: <br> `.button - This is an abbreviation for TextButton's and ImageButton's` <br> `.label - This is an abbreviation for TextLabel's and ImageLabel's` <br> `.frame - This is an abbreviation for Frame's and ScrollingFrame's`

`Id` - To indicate that the selector arguement is a ClassName the string should preceed with a `#` - for example, "#CloseMenuButton". The Id of a GUI Instance is a string attribute of the Instance called "id".

`Name` - The selector arguement should just be a string that contains the name of the GUI Instances to look for - for example "InventoryButton"

## Dictionary Returned
| Dictionary Key Returned | Dictionary Value Returned |
--- | ---
| `elementType` | The type of GUI Instance (ClassName, Name, Id, Instance) |
| `matchingElements` | A table of instances that match the selector (and parent if it is defined) |
| `originalData` | A string that contains the selector used |

## Examples
``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

-- prints all of the GUI Instances that have the ClassName of "TextButton" and the same parent as this script
for i,v in next, interfaceService:Get(".TextButton", script.Parent).matchingElements do
	print(v)
end
```

``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

-- prints all of the GUI Instances that have the ClassName of "TextLabel" or "ImageLabel"
for i,v in next, interfaceService:Get(".label").matchingElements do
	print(v)
end
```

``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

-- prints all of the GUI Instances that have the Id of "CloseMenuButton"
for i,v in next, interfaceService:Get("#CloseMenuButton").matchingElements do
	print(v)
end
```

``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

-- prints all of the GUI Instances that have the Name of "InventoryButton"
for i,v in next, interfaceService:Get("InventoryButton").matchingElements do
	print(v)
end
```

``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))
local button = script.Parent:WaitForChild("button")

-- prints the button Instance
for i,v in next, interfaceService:Get(button).matchingElements do
	print(v)
end
```