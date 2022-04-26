_G.Speed = 150  -- change the speed to ur liking
_G.Key = Enum.KeyCode.X  -- change to whatever keybind you want

local UIS = game:GetService("UserInputService")
local OnRender = game:GetService("RunService").RenderStepped

local Player = game:GetService("Players").LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()

local Camera = workspace.CurrentCamera
local Root = Character:WaitForChild("HumanoidRootPart")

local C1, C2, C3;
local f = {Flying = false, Forward = false, Backward = false, Left = false, Right = false}
C1 = UIS.InputBegan:Connect(function(Input)
    if Input.UserInputType == Enum.UserInputType.Keyboard then
        if Input.KeyCode == _G.Key then
            f.Flying = not f.Flying
            Root.Anchored = f.Flying
        elseif Input.KeyCode == Enum.KeyCode.W then
            f.Forward = true
        elseif Input.KeyCode == Enum.KeyCode.S then
            f.Backward = true
        elseif Input.KeyCode == Enum.KeyCode.A then
            f.Left = true
        elseif Input.KeyCode == Enum.KeyCode.D then
            f.Right = true
        end
    end
end)

C2 = UIS.InputEnded:Connect(function(Input)
    if Input.UserInputType == Enum.UserInputType.Keyboard then
        if Input.KeyCode == Enum.KeyCode.W then
            f.Forward = false
        elseif Input.KeyCode == Enum.KeyCode.S then
            f.Backward = false
        elseif Input.KeyCode == Enum.KeyCode.A then
            f.Left = false
        elseif Input.KeyCode == Enum.KeyCode.D then
            f.Right = false
        end
    end
end)

C3 = Camera:GetPropertyChangedSignal("CFrame"):Connect(function()
    if f.Flying then
        Root.CFrame = CFrame.new(Root.CFrame.Position, Root.CFrame.Position + Camera.CFrame.LookVector)
    end
end)

while true do 
    local Delta = OnRender:Wait()
    if f.Flying then
        if f.Forward then
            Root.CFrame = Root.CFrame + (Camera.CFrame.LookVector * (Delta * _G.Speed))
        end
        if f.Backward then
            Root.CFrame = Root.CFrame + (-Camera.CFrame.LookVector * (Delta * _G.Speed))
        end
        if f.Left then
            Root.CFrame = Root.CFrame + (-Camera.CFrame.RightVector * (Delta * _G.Speed))
        end
        if f.Right then
            Root.CFrame = Root.CFrame + (Camera.CFrame.RightVector * (Delta * _G.Speed))
        end
    end
end
