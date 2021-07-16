# :LeftClick()

**:LeftClick(func)** is a function that needs one arguement (func), which is a function. The function can only be used on [the dictionary returned by :Get()](/docs/2_Get.html#dictionary-returned).

!!! warning ":LeftClick() can only be used on [`:Get()`](/docs/2_Get.html)"

## Arguements
| Arguement | Description |
--- | ---
| `function` | The function that will be carried out when the mouse left clicks any GUI Instance inside of the `matchingElements` table of the [dictionary returned by :Get()](/docs/2_Get.html#dictionary-returned). <br><br/> The function has one (optional) arguement, which is for the specific GUI Instance that was interacted with.|

## Example
``` lua
local interfaceService = require(game.ReplicatedStorage:WaitForChild("InterfaceService"))

-- "this" is an arbitrary name for the specific GUI Instance that was interacted with
interfaceService:Get("#cookieButton"):LeftClick(function(this)
	print("Mouse Left Clicked "..this.Name)
end)
```