# :Create()

**:Create(table)** is a function that needs one arguement (table). The table needs to contain properties (such as Position and AnchorPoint) that will be applied to the GUI Instance, ClassName is required.

## Arguements
| Arguement | Description |
--- | ---
| `table` | A table that contains properies (and optionally Id) to apply to the GUI Instance, ClassName is required. |

## Returned
| Name | Value |
--- | ---
| `Instance` | The Instance created |

## Example
``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

button = interfaceService:Create({
	ClassName = "TextButton",
	Id = "button",
	Size = UDim2.new(0, 100, 0, 100),
	Position = UDim2.new(0.5, 0, 0.5, 0),
	AnchorPoint = Vector2.new(0.5, 0.5),
	Parent = script.Parent
})
```