spawn(function()
    pcall(function()
        game:GetService("RunService").Stepped:Connect(function()
            if _G.ChestBypass then
                for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
                    if v:IsA("BasePart") then
                        v.CanCollide = false    
                    end
                end
            end
        end)
    end)
end)

spawn(function()
    pcall(function() --velocity
        game:GetService("RunService").Stepped:Connect(function()
            if  _G.ChestBypass
            then
                if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
                    local Noclip = Instance.new("BodyVelocity")
                    Noclip.Name = "BodyClip"
                    Noclip.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
                    Noclip.MaxForce = Vector3.new(100000,100000,100000)
                    Noclip.Velocity = Vector3.new(0,0,0)
                end
            else	
                if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
                    game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
                end
                if game.Players.LocalPlayer.Character:FindFirstChild('Highlight') then
                    game.Players.LocalPlayer.Character:FindFirstChild('Highlight'):Destroy()
                end
            end
        end)
    end)
end)
_G.ChestBypass = true
spawn(function()
    while wait() do
        if _G.ChestBypass then
            pcall(function()
                for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
                    if string.find(v.Name, "Chest") then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
                        wait(0.375)
                    end
                end
                game.Players.LocalPlayer.Character.Head:Destroy()
                for _,v in pairs(game:GetService("Workspace"):GetDescendants()) do
                    if string.find(v.Name, "Chest") and v:IsA("TouchTransmitter") then
                    firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 0) --0 is touch
                    wait()
                    firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 1) -- 1 is untouch
                    end
                end
            end)
        end
    end
end)
spawn(function()
    while task.wait() do
        if _G.ChestBypass  then
            _G.ChestBypass  = game:GetService("CoreGui").RobloxPromptGui.promptOverlay.ChildAdded:Connect(function(child)
                    if child.Name == 'ErrorPrompt' and child:FindFirstChild('MessageArea') and child.MessageArea:FindFirstChild("ErrorFrame") then
                    game:GetService("TeleportService"):Teleport(game.PlaceId)
                end
            end)
        end
    end
end)

while _G.ChestBypass do wait()
    if game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") and game.Players.LocalPlayer.Character:FindFirstChild("Humanoid").Health > 0 then
        wait(10)
        game.Players.LocalPlayer.Character.Head:Destroy()
    end
end

spawn(function()
    while task.wait() do
        if _G.ChestBypass then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(ohString1, ohString2)
        end
    end
end)


spawn(function()
    if setfflag then
        setfflag("AbuseReportScreenshot", "False")
        setfflag("AbuseReportScreenshotPercentage", "0")
    end
end)

