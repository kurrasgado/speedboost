local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local RunService = game:GetService("RunService")

local speedBoost = 1.4
local originalSpeed = LocalPlayer.Character.Humanoid.WalkSpeed
local boostDuration = 600

LocalPlayer.Character.Humanoid.WalkSpeed = originalSpeed * speedBoost

local timer = 0
RunService.RenderStepped:Connect(function(dt)
    timer = timer + dt
    if timer >= boostDuration then
        LocalPlayer.Character.Humanoid.WalkSpeed = originalSpeed
        RunService.RenderStepped:Disconnect()
    end
end)
