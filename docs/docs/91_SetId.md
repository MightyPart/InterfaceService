# :SetId()

**:SetId(element, id)** is a function that has 2 required arguements. This function updates the Id of a GUI Instance.

!!! notice "The Id of a GUI Instance is an string attribute called "id""

## Arguements
| Arguement | Description |
--- | ---
| `element` | The GUI Instance to apply the Id onto. |
| `id` | The Id (string). |

## Examples

!!! warning "Do not include the indicator symbol for Id (`#`) when setting the Id, or when setting it manually in the properties window!"

``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

interfaceService:SetId(script.Parent:WaitForChild("MenuFrame"), "menuFrame")
```

``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

-- function that triggers when the button is clicked
local leftClick = interfaceService:Get("#buttons"):LeftClick(function(this)
	print(this.Name.." Was Left Clicked")
end)

-- creates a new TextButton
newButton = interfaceService:Create({
	ClassName = "TextButton",
	Size = UDim2.new(0, 100, 0, 100),
	Position = UDim2.new(0.5, 0, 0.5, 0),
	AnchorPoint = Vector2.new(0.5, 0.5),
	Parent = script.Parent
})

-- sets the id of the newButton to "buttons"
interfaceService:SetId(newButton, "buttons")

-- updates the leftClick function so "newbutton" can be detected
leftClick:Update()
```