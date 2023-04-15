# 🌌 Exunys ESP [![Visitors](https://visitor-badge.glitch.me/badge?page_id=Exunys.Exunys-ESP)](https://github.com/Exunys/Exunys-ESP)

This project represents a collection of visuals / wall hacks (Tracers, ESP, Boxes, Head Dots, Chams & Crosshair). This script is also undetected because it uses [Synapse X's Drawing Library](https://docs.synapse.to/docs/reference/drawing_lib.html). It has modulized support for NPCs & parts and it offers a very simple and easy to use wrapping and unwrapping system.

This project's source is optimized, organized and simplified to the maximal level to be executive, fast, stable and precise.

This project is in beta testing, feel free to create pull requests (you will get credited), issues or just contact me on any of my linked platforms.

This project has been inspired from [AirHub](https://github.com/Exunys/AirHub) which has an improved version of my [old examplery discontinued wall hack script](https://github.com/Exunys/Wall-Hack). It has a CS:GO-styled look which looks beautiful for fps games.

### ❗ Notice
This project has been written and tested with and only with [Synapse X](https://x.synapse.to) however, I will attempt my best to modulize support for every exploit. So far, the required functions for this module to run will be listed below:

<details> <summary> Dependencies (required functions & libraries): </summary>

- Libraries:
    - **Drawing**
        - Drawing.new *(function)*
        - Drawing.Fonts *(table)*
    - **debug**
        - debug.getupvalue *(function)*

- Functions:
    - **getgenv**
    - **getrawmetatable**
    - **gethiddenproperty**
</details>

This project also uses [Exunys' Config Library](https://github.com/Exunys/Config-Library) as a way of storing user settings, meaning, your script executor must support the dependencies for the module if you want the *configuration storing & loading functions* in the ESP module to function.

### 📜 License
This project is completely free and open sourced. But, that does not mean you own rights to it. Read this [document](https://github.com/Exunys/Exunys-ESP/blob/main/LICENSE) for more information.
You can re-use / stitch this script or any system of this project into any of your repositories, as long as you credit the developer [Exunys](https://github.com/Exunys).

## 📑 Update log (DD/MM/YYYY):
<details> <summary> 14/04/2023 </summary>

- [**v1.0b**] First (BETA) release
</details>
<details> <summary> 15/04/2023 </summary>

- [**v1.03b**] Optimizations, bug fixes, silenced errors
</details>

# 👋 Introduction

First of all, to implement the module in your script's environment you must use the function `loadstring` like below:
```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/Exunys/Exunys-ESP/main/src/ESP.lua"))()
```
The code above loads the module's environment in your script executor's global environment meaning it is archivalbe across every script.

The identificator for the environment is `ExunysDeveloperESP` which is a table that has configurable settings and interactive user functions.

The table loaded into the exploit's global environment by the module has a [*metatable*](https://create.roblox.com/docs/scripting/luau/metatables) set to it with a **__call** metamethod, meaning you can call the table which would wrap every player in the game and render a crosshair.
```lua
ExunysDeveloperESP()
```
This is equivalent to the `Load` function (which would be more optimized and faster).
```lua
ExunysDeveloperESP.Load()
```

This module has customizable settings for every drawing property and other miscellaneous properties with unique functions. You can see the configurable settings below.

<details> <summary> The script's configurable settings </summary>

```lua
getgenv().ExunysDeveloperESP = {
	DeveloperSettings = {
		Path = "Exunys Developer/Exunys ESP/Configuration.cfg",
		UnwrapOnCharacterAbsence = false,
		UpdateMode = "RenderStepped",
		TeamCheckOption = "TeamColor",
		RainbowSpeed = 1, -- Bigger = Slower
		WidthBoundary = 1.5 -- Smaller Value = Bigger Width
	},

	Settings = {
		Enabled = true,
		PartsOnly = false,
		TeamCheck = false,
		AliveCheck = true,
		LoadConfigOnLaunch = true,
	},

	Properties = {
		ESP = {
			Enabled = true,
			RainbowColor = false,
			RainbowOutlineColor = false,
			Offset = 10,

			Color = Color3fromRGB(255, 255, 255),
			Transparency = 1,
			Size = 14,
			Font = DrawingFonts.System, -- UI, System, Plex, Monospace

			OutlineColor = Color3fromRGB(0, 0, 0),
			Outline = true,

			DisplayDistance = true,
			DisplayHealth = false,
			DisplayName = false,
			DisplayDisplayName = true,
			DisplayTool = true
		},

		Tracer = {
			Enabled = true,
			RainbowColor = false,
			RainbowOutlineColor = false,
			Position = 1, -- 1 = Bottom; 2 = Center; 3 = Mouse

			Transparency = 1,
			Thickness = 1,
			Color = Color3fromRGB(255, 255, 255),

			Outline = true,
			OutlineColor = Color3fromRGB(0, 0, 0)
		},

		HeadDot = {
			Enabled = true,
			RainbowColor = false,
			RainbowOutlineColor = false,

			Color = Color3fromRGB(255, 255, 255),
			Transparency = 1,
			Thickness = 1,
			NumSides = 30,
			Filled = false,

			OutlineColor = Color3fromRGB(0, 0, 0),
			Outline = true
		},

		Box = {
			Enabled = true,
			RainbowColor = false,
			RainbowOutlineColor = false,

			Color = Color3fromRGB(255, 255, 255),
			Transparency = 1,
			Thickness = 1,
			Filled = false,

			OutlineColor = Color3fromRGB(0, 0, 0),
			Outline = true
		},

		HealthBar = {
			Enabled = true,
			RainbowOutlineColor = false,
			Offset = 4,
			Blue = 100,
			Position = 3, -- 1 = Top; 2 = Bottom; 3 = Left; 4 = Right

			Thickness = 1,
			Transparency = 1,

			OutlineColor = Color3fromRGB(0, 0, 0),
			Outline = true
		},

		Chams = {
			Enabled = false, -- Keep disabled, broken, WIP...
			RainbowColor = false,

			Color = Color3fromRGB(255, 255, 255),
			Transparency = 0.2,
			Thickness = 1,
			Filled = true
		},

		Crosshair = {
			Enabled = true,
			RainbowColor = false,
			RainbowOutlineColor = false,
			TStyled = false,
			Position = 1, -- 1 = Mouse; 2 = Center

			Size = 12,
			GapSize = 6,
			Rotation = 0,

			Rotate = false,
			RotateClockwise = true,
			RotationSpeed = 5,

			PulseGap = false,
			PulsingStep = 10,
			PulsingSpeed = 5,
			PulsingBounds = {4, 8}, -- {...}[1] => GapSize Min; {...}[2] => GapSize Max

			Color = Color3fromRGB(0, 255, 0),
			Thickness = 1,
			Transparency = 1,

			OutlineColor = Color3fromRGB(0, 0, 0),
			Outline = true,

			CenterDot = {
				Enabled = true,
				RainbowColor = false,
				RainbowOutlineColor = false,

				Radius = 2,

				Color = Color3fromRGB(0, 255, 0),
				Transparency = 1,
				Thickness = 1,
				NumSides = 60,
				Filled = false,

				OutlineColor = Color3fromRGB(0, 0, 0),
				Outline = true
			}
		}
	}

	-- The rest is core data for the functionality of the module...
}
```
</details>

# Documentation is a WIP. More information soon.

Previews:

![image](https://user-images.githubusercontent.com/76539058/232103151-42664a64-a942-46ad-8883-ae1fe1ac7e81.png) (ESP with factory settings)

![image](https://user-images.githubusercontent.com/76539058/232103294-e79b6c64-c655-4df7-ad70-6db4e5f66f54.png) (Crosshair with factory settings)

https://user-images.githubusercontent.com/76539058/232102118-14961c64-bb39-41aa-8b6a-d5af3ef5f922.mp4

The settings for the video above:

```lua
ExunysDeveloperESP.RenderCrosshair()

ExunysDeveloperESP.DeveloperSettings.RainbowSpeed = 2.5

local CrosshairProperties = ExunysDeveloperESP.Properties.Crosshair

CrosshairProperties.RainbowColor = true
CrosshairProperties.Position = 2

CrosshairProperties.Size = 18
CrosshairProperties.Thickness = 2

CrosshairProperties.Rotate = true
CrosshairProperties.RotateClockwise = false
CrosshairProperties.RotationSpeed = 10

CrosshairProperties.PulseGap = true
CrosshairProperties.PulsingBounds = {0, 24}

CrosshairProperties.CenterDot.Color = Color3.fromHex("#FFFFFF")
```

## Wrapping parts:
```rust
<string> Hash | ExunysDeveloperESP:WrapObject(<Instance> Object[, <string> PseudoName, <table> Allowed Visuals])
```
```lua
local Object = workspace.Part

local Hash = ExunysDeveloperESP:WrapObject(Object, "Cool Part", {Tracer = false})

task.delay(5, function()
    ExunysDeveloperESP.UnwrapObject(Hash)
end)
```
![image](https://user-images.githubusercontent.com/76539058/232104521-a47254df-1ded-4e5b-a477-bd211e6e72e7.png)
