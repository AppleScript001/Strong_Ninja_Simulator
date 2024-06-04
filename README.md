local DrRayLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/AZYsGithub/DrRay-UI-Library/main/DrRay.lua"))()
local window = DrRayLibrary:Load("Strong Ninja Simulator", "Default")

local tab = DrRayLibrary.newTab("Main", "ImageIdHere")

---Main AutoFarm [Strength],[Rebirth]-----------
tab.newToggle("Auto Strength", "Auto Farm [Strength]", false, function(Value)
_G.Strength = Value
while _G.Strength do wait()
for i , v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
if v.ClassName == 'Tool' then
v.Parent = v.Parent.Parent.Character;
end;
end;
local LocalPlayer = game:GetService("Players").LocalPlayer
LocalPlayer.Character:FindFirstChildOfClass("Tool"):Activate()

end
end)
tab.newToggle("Auto Rebirth", "Auto Farm [Rebirth]", false, function(Value)
_G.Rebirth = Value
while _G.Rebirth do wait()
local args = {
[1] = {}
}

game:GetService("ReplicatedStorage"):WaitForChild("Framework"):WaitForChild("Modules"):WaitForChild("Shared"):WaitForChild("Internal"):WaitForChild("Modules"):WaitForChild("2 | Network"):WaitForChild("Remotes"):WaitForChild("s_controller_rebirth"):InvokeServer(unpack(args))

end
end)

---BuyEgg [All] -------------------
local tab = DrRayLibrary.newTab("BuyEggs", "ImageIdHere")

Eggs = {}
for i,v in pairs(game:GetService("Players").b82zf9y.PlayerGui.Main.Eggs.EggsList:GetChildren()) do
    table.insert(Eggs,v.Name) 
end

tab.newDropdown("Selected [Egg]", "Select one of these BuyEgg!", Eggs, function(t)
    PlayerTP = t
end)
tab.newToggle("Auto Buy", "Auto buy-selected [Egg]", false, function(t)
_G.Egg = t
while _G.Egg do wait()
local args = {
[1] = {
[1] = PlayerTP
}
}

game:GetService("ReplicatedStorage"):WaitForChild("Framework"):WaitForChild("Modules"):WaitForChild("Shared"):WaitForChild("Internal"):WaitForChild("Modules"):WaitForChild("2 | Network"):WaitForChild("Remotes"):WaitForChild("s_controller_buyegg"):InvokeServer(unpack(args))

end
end)

repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer.Idled:connect(function()
game:GetService("VirtualUser"):ClickButton2(Vector2.new())
end)

window:Close()
