local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "still need a name", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})
--PLAYER
local PlayerTab = Window:MakeTab({
	Name = "Player",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

PlayerTab:AddSlider({
    Name = "Walkspeed",
    Min = 16,
    Max = 500,
    Default = 16,
    Color = Color3.fromRGB(0,0,0),
    Increment = 1,
    ValueName = "",
    Callback = function(new)
        _G.WS = new;
    local Humanoid = game:GetService("Players").LocalPlayer.Character.Humanoid;
    Humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
        Humanoid.WalkSpeed = _G.WS;
    end)
    Humanoid.WalkSpeed = _G.WS;
    end    
})


PlayerTab:AddSlider({
    Name = "Jumppower",
    Min = 50,
    Max = 500,
    Default = 50,
    Color = Color3.fromRGB(0,0,0),
    Increment = 1,
    ValueName = "",
    Callback = function(value)
        _G.JP = value
        local Humanoid = game:GetService("Players").LocalPlayer.Character.Humanoid
        Humanoid:GetPropertyChangedSignal("JumpPower"):Connect(function()
        Humanoid.JumpPower = _G.JP
        end)
        Humanoid.JumpPower = _G.JP
    end    
})


PlayerTab:AddSlider({
    Name = "FOV",
    Min = 10,
    Max = 140,
    Default = 70,
    Color = Color3.fromRGB(0,0,0),
    Increment = 1,
    ValueName = "",
    Callback = function(new)
        game.Workspace.Camera.FieldOfView = new
    end    
})

PlayerTab:AddButton({
	Name = "Reset FOV",
	Callback = function()
        game.Workspace.Camera.FieldOfView = 70
  	end    
})

PlayerTab:AddButton({
	Name = "Inf jump",
	Callback = function()
		_G.infinjump = not _G.infinjump

		if _G.infinJumpStarted == nil then
			--Ensures this only runs once to save resources
			_G.infinJumpStarted = true
			
			--Notifies readiness
			game.StarterGui:SetCore("SendNotification", {Title="Inf jump script"; Text="Birdhub"; Duration=10;})
		
			--The actual infinite jump
			local plr = game:GetService('Players').LocalPlayer
			local m = plr:GetMouse()
			m.KeyDown:connect(function(k)
				if _G.infinjump then
					if k:byte() == 32 then
					humanoid = game:GetService'Players'.LocalPlayer.Character:FindFirstChildOfClass('Humanoid')
					humanoid:ChangeState('Jumping')
					wait()
					humanoid:ChangeState('Seated')
					end
				end
			end)
		end
  	end    
})

PlayerTab:AddButton({
	Name = "Btools",
	Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/trme222/btools-legit/main/README.md"))()
  	end    
})

PlayerTab:AddButton({
	Name = "Anti AFK",
	Callback = function()
        loadstring(game:HttpGet("https://cdn.wearedevs.net/scripts/anti-afk%20via%20autofocus.txt"))()
  	end    
})

--DUPE
local DupeTab = Window:MakeTab({
	Name = "Dupe",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})


local Section = DupeTab:AddSection({
	Name = "Maxland dupe manual"
})

DupeTab:AddButton({
	Name = "Start manual dupe",
	Callback = function()
        OrionLib:MakeNotification({
            Name = "Made by trem2goated",
            Content = 'Keep in mind your base may be wiped".',
            Image = "rbxassetid://12576176007",
            Time = 5
        })
        Loadslot()
  	end    
})



DupeTab:AddButton({
	Name = "Manual dupe step 2",
	Callback = function()
        OrionLib:MakeNotification({
            Name = "Made by trem2goated",
            Content = 'Please now load your plot and press Max land dupe step 3".',
            Image = "rbxassetid://12576176007",
            Time = 5
        })
        FreeLand()
  	end    
})


DupeTab:AddButton({
	Name = "Manual dupe step 3",
	Callback = function()
        wait(timetotp)
        loadstring(game:GetObjects("rbxassetid://2662507900")[1].Source)()
  	end    
})


local Section = DupeTab:AddSection({
	Name = "Maxland dupe claim tools"
})

DupeTab:AddButton({
	Name = "Select plot",
	Callback = function()
        loadstring(game:HttpGet("https://pastebin.com/raw/Wj49DUwL"))()
  	end    
})

DupeTab:AddButton({
	Name = "Load on selected plot",
	Callback = function()
        for i,v in next, game:GetService("Workspace").Properties:GetChildren() do
            if v:FindFirstChild("OriginSquare") then
                if v.OriginSquare:FindFirstChild("Selection") then
                game:GetService("ReplicatedStorage").PropertyPurchasing.ClientPurchasedProperty:FireServer(v,v.OriginSquare.Position)
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.OriginSquare.CFrame + Vector3.new(0,2,0)
                break
            end
        end
    end
end
})

DupeTab:AddButton({
	Name = "Save slot",
	Callback = function()
        local result = false
    repeat
        wait(1)
        getgenv().block_save = false
        local slot_id = game:GetService("Players")["LocalPlayer"]["CurrentSaveSlot"].Value
        result = game.ReplicatedStorage.LoadSaveRequests.RequestSave:InvokeServer(slot_id, game.Players.LocalPlayer)
        OrionLib:MakeNotification({
            Name = "trem2goated",
            Content = "Slot saved.",
            Image = "rbxassetid://12576176007",
            Time = 1
        })
        until result
        getgenv().block_save = true
  	end    
})


--BASE
local BaseTab = Window:MakeTab({
	Name = "Base",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

BaseTab:AddButton({
	Name = "item counter",
	Callback = function()
        loadstring(game:HttpGet('https://pastebin.com/raw/VextamCW'))()
  	end    
})

--World
local WorldTab = Window:MakeTab({
	Name = "World",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

WorldTab:AddButton({
	Name = "better graphics",
	Callback = function()
        loadstring(game:HttpGet("https://pastebin.com/raw/MEi0Y0AT", true))()
  	end    
})

WorldTab:AddToggle({
	Name = "No fog",
	Default = true,
	Callback = function(Value)
		loadstring(game:HttpGet("https://pastebin.com/raw/JniCmYG0", true))()
	end    
})






--info 
local InfoTab = Window:MakeTab({
	Name = "Info",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

InfoTab:AddParagraph("Devs","trem2goated#1646 and Bless#8888")
