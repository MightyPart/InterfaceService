# :Update()

**:Get(selector &lt;optional&gt;, ancestor &lt;optional&gt;)** is a function that has 2 optional arguements. This function updates the selector and or the ancestor of [`:MouseEnter()`](/docs/4_MouseEnter.html), [`:Mouseleave()`](/docs/5_MouseLeave.html), [`:LeftClick()`](/docs/6_LeftClick.html), [`:RightClick()`](/docs/7_RightClick.html), [`:MouseClick()`](/docs/8_MouseClick.html) and [`:Changed()`](/docs/9_Changed.html). Leaving both arguements blank will result in the `matchingElements` table of [the dictionary returned by :Get()](/docs/2_Get.html#dictionary-returned).

!!! warning ":Update() can only be used on [`:MouseEnter()`](/docs/4_MouseEnter.html), [`:Mouseleave()`](/docs/5_MouseLeave.html), [`:LeftClick()`](/docs/6_LeftClick.html), [`:RightClick()`](/docs/7_RightClick.html), [`:MouseClick()`](/docs/8_MouseClick.html) and [`:Changed()`](/docs/90_Changed.html)."

## Arguements
| Arguement | Description |
--- | ---
| `selector` | A String (ClassName, Name or Id) or an Instance that defines the type of GUI Instance |
| `ancestor` | An optional variable that defines the ancestor that all of the GUI Instances have to be a descendant of in order for it to be included in the `matchingElements` [dictionary returned by :Get()](/docs/2_Get.html#dictionary-returned). If the selector arguement is an Instance then ancestor arguement is ignored. defaults to the ancestor defined in [the dictionary returned by :Get()](/docs/2_Get.html#dictionary-returned).  |

`ClassName` - To indicate that the selector arguement is a ClassName the string should preceed with a `.` - for example, ".TextButton". Abbreviations can be used instead of ClassNames, they are: <br> `.button - This is an abbreviation for TextButton's and ImageButton's` <br> `.label - This is an abbreviation for TextLabel's and ImageLabel's` <br> `.frame - This is an abbreviation for Frame's and ScrollingFrame's`

`Id` - To indicate that the selector arguement is a ClassName the string should preceed with a `#` - for example, "#CloseMenuButton". The Id of a GUI Instance is a string attribute of the Instance called "id".

`Name` - The selector arguement should just be a string that contains the name of the GUI Instances to look for - for example "InventoryButton"



## Examples
``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

-- function that triggers when the button is clicked
leftClick = interfaceService:Get(".TextButton"):LeftClick(function(this)
	print(this.Name.." Was Left Clicked")
end)

--[[ updates the function so that any GUI Instance that has the ClassName "ImageButton" (and has the same
parent as this script) triggers the function when it is left clicked ]]--
leftClick:Update(".ImageButton", script.Parent)
```

``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))
local button = script.Parent:WaitForChild("TextButton")

-- function that triggers when the button is clicked
rightClick = interfaceService:Get(button):RightClick(function(this)
	print(this.Name.." Was Right Clicked")
end)

-- creates a new TextButton
newButton = interfaceService:Create({
	ClassName = "TextButton",
	Size = UDim2.new(0, 100, 0, 100),
	Position = UDim2.new(0.5, 0, 0.5, 0),
	AnchorPoint = Vector2.new(0.5, 0.5),
	Parent = script.Parent
})

--updates the function so that "newButton" triggers the function instead of "button"
rightClick:Update(newButton)
```

``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

-- function that fires whenever a GUI Instance with the ClassName of "TextButton" is left clicked
local leftClick = interfaceService:Get(".TextButton"):LeftClick(function(this)
    print(this.Name.." was clicked!")
end)

-- creates a new TextButton
newButton = interfaceService:Create({
    ClassName = "TextButton",
	Id = "TextButtonId",
    Size = UDim2.new(0, 100, 0, 100),
    Position = UDim2.new(0.5, 0, 0.5, 0),
    AnchorPoint = Vector2.new(0.5, 0.5),
    Parent = script.Parent
})

-- has to update the leftClick function so "newButton" can be detected
leftClick:Update()
```