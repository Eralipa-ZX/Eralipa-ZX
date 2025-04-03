local GUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/aaaa"))()
local UI = GUI:CreateWindow("Eralipa ZX v0.1b - Troll","เ งี่ ย น")
local Home = UI:addPage("Home",1,true,6)
Home:addLabel("Version 0.1b","")
Home:addLabel("Credit By Error_Code19182","")
local LP = UI:addPage("Universal",10,false,1.5)
LP:addLabel("Visuals Function","Visuals Function")
LP:addButton("chams Click",function()
    local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer
local MaxDistance = 400.5
local function CreateNametag(Player)
    if Player == LocalPlayer then return end
    local function SetupNametag(Character)
        local Head = Character:FindFirstChild("Head")
        if not Head then return end
        local OldNametag = Head:FindFirstChild("Nametag")
        if OldNametag then
            OldNametag:Destroy()
        end
        local BillboardGui = Instance.new("BillboardGui")
        BillboardGui.Name = "Nametag"
        BillboardGui.Adornee = Head
        BillboardGui.Size = UDim2.new(0, 75, 0, 150)
        BillboardGui.StudsOffset = Vector3.new(0, 2, 0)
        BillboardGui.AlwaysOnTop = true
        local TextLabel = Instance.new("TextLabel")
        TextLabel.Size = UDim2.new(1, 0, 1, 0)
        TextLabel.Text = Player.Name
        TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255) -- White color
        TextLabel.BackgroundTransparency = 1
        TextLabel.TextStrokeTransparency = 0.75 -- Outline for better visibility
        TextLabel.Font = Enum.Font.Code
        TextLabel.TextScaled = true
        TextLabel.Parent = BillboardGui
        BillboardGui.Parent = Head
        local function UpdateVisibility()
            if Player.Character and Player.Character:FindFirstChild("Head") and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Head") then
                local Distance = (Player.Character.Head.Position - LocalPlayer.Character.Head.Position).Magnitude
                BillboardGui.Enabled = (Distance <= MaxDistance)
            else
                BillboardGui.Enabled = false
            end
        end
        local Connection
        Connection = RunService.Heartbeat:Connect(function()
            if Player.Character and Player.Character:FindFirstChild("Head") then
                UpdateVisibility()
            else
                BillboardGui:Destroy()
                Connection:Disconnect()
            end
        end)
    end
    if Player.Character then
        SetupNametag(Player.Character)
    end
    Player.CharacterAdded:Connect(SetupNametag)
end
local function ApplyHighlight(Player)
    if Player == LocalPlayer then return end -- Skip local player
    local function SetupHighlight(Character)
        for _, v in pairs(Character:GetChildren()) do
            if v:IsA("Highlight") then
                v:Destroy()
            end
        end
        local Highlighter = Instance.new("Highlight")
        Highlighter.Parent = Character
        local function UpdateFillColor()
            local DefaultColor = Color3.fromRGB(255, 48, 51) -- Default red color
            Highlighter.FillColor = Player.TeamColor and Player.TeamColor.Color or DefaultColor
        end
        UpdateFillColor()
        Player:GetPropertyChangedSignal("TeamColor"):Connect(UpdateFillColor)
        local Humanoid = Character:FindFirstChildOfClass("Humanoid")
        if Humanoid then
            Humanoid.Died:Connect(function()
                Highlighter:Destroy()
            end)
        end
    end
    if Player.Character then
        SetupHighlight(Player.Character)
    end
    Player.CharacterAdded:Connect(SetupHighlight)
end
for _, Player in pairs(Players:GetPlayers()) do
    CreateNametag(Player)
    ApplyHighlight(Player)
end
Players.PlayerAdded:Connect(function(Player)
    CreateNametag(Player)
    ApplyHighlight(Player)
end)
end)
LP:addLabel("Player Function","plr Function")
LP:addTextBox("WalkSpeed / 16 is default","16",function(value)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value
end)
LP:addTextBox("Jump Power / 50 is default","50",function(value)
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = value
end)
LP:addButton("Fov player Normal Click",function()
    local FovNumber = 70
local Camera = workspace.CurrentCamera
Camera.FieldOfView = FovNumber
end)
LP:addButton("Fov player 100 Click",function()
    local FovNumber = 100
local Camera = workspace.CurrentCamera
Camera.FieldOfView = FovNumber
end)
LP:addButton("Fov player 120 Click",function()
    local FovNumber = 120
local Camera = workspace.CurrentCamera
Camera.FieldOfView = FovNumber
end)
LP:addButton("Reset player Click",function()
    game.Players.LocalPlayer.Character.Humanoid.Health = 0
end)
LP:addLabel("Teleport Function","Tp Function")
local PLIST = {}
for i,v in pairs(game:GetService("Players"):GetPlayers()) do
    table.insert(PLIST,v.DisplayName)
end
LP:addDropdown("Teleport to Player",PLIST,4,function(value)
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =  game.Players[value].Character.HumanoidRootPart.CFrame * CFrame.new(0,2,1)
end)
LP:addButton("Teleport Tool Click",function()
    mouse = game.Players.LocalPlayer:GetMouse()
tool = Instance.new("Tool")
tool.RequiresHandle = false
tool.Name = "Click Teleport"
tool.Activated:connect(function()
local pos = mouse.Hit+Vector3.new(0,2.5,0)
pos = CFrame.new(pos.X,pos.Y,pos.Z)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = pos
end)
tool.Parent = game.Players.LocalPlayer.Backpack
end)
LP:addLabel("Framing","fram Function")
LP:addButton("AFK Click",function()
    p= game.Players:GetChildren()		
for i= 1, #p do	
if p[i].Name ~= "shanethe13" then						
b = Instance.new("BodyPosition")	 b.Parent = p[i].Character.Torso	b.maxForce = Vector3.new(6000000,60000000,60000000)						
b.position = Vector3.new(100,10,0)					
end	
end
end)
LP:addLabel("Animation Emote Troll Function","AETroll Function")
LP:addButton("Scratch Click",function()
    getgenv().JERK_OFF_SPEED = 5
getgenv().KEEP_ON_DEATH = true
loadstring(game:HttpGet("https://raw.githubusercontent.com/Sakupenny/Universal-Jerk-Off/refs/heads/main/Main.lua"))()
end)
LP:addButton("Whip Click",function()
    loadstring(game:HttpGet("https://pastefy.app/wa3v2Vgm/raw"))("Spider Script")
end)

local ST = UI:addPage("Setting",2,false,6)
ST:addLabel("Setting","coming soon")
