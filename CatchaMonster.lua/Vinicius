-- CATCH A MONSTER - AUTO FARM + TP
-- Delta Executor

local player = game.Players.LocalPlayer
local char = player.Character or player.CharacterAdded:Wait()
local hrp = char:WaitForChild("HumanoidRootPart")

local autoFarm = false

-- Atualiza personagem se morrer
player.CharacterAdded:Connect(function(c)
    char = c
    hrp = c:WaitForChild("HumanoidRootPart")
end)

-- GUI
local gui = Instance.new("ScreenGui")
gui.Name = "CatchMonsterGUI"
gui.Parent = player:WaitForChild("PlayerGui")

local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 220, 0, 130)
frame.Position = UDim2.new(0, 20, 0, 200)
frame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true

-- Auto Farm Button
local farmBtn = Instance.new("TextButton", frame)
farmBtn.Size = UDim2.new(1, -20, 0, 40)
farmBtn.Position = UDim2.new(0, 10, 0, 15)
farmBtn.Text = "Auto Farm: OFF"
farmBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
farmBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
farmBtn.TextScaled = true

-- TP Button
local tpBtn = Instance.new("TextButton", frame)
tpBtn.Size = UDim2.new(1, -20, 0, 40)
tpBtn.Position = UDim2.new(0, 10, 0, 70)
tpBtn.Text = "TP Monster"
tpBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
tpBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
tpBtn.TextScaled = true

-- Função: pegar monstro mais próximo
local function getNearestMonster()
    local nearest
    local shortest = math.huge

    for _, v in pairs(workspace:GetDescendants()) do
        if v:IsA("Model")
        and v:FindFirstChild("Humanoid")
        and v:FindFirstChild("HumanoidRootPart")
        and v.Humanoid.Health > 0
        and v ~= char then

            local dist = (hrp.Position - v.HumanoidRootPart.Position).Magnitude
            if dist < shortest then
                shortest = dist
                nearest = v
            end
        end
    end
    return nearest
end

-- AUTO FARM
farmBtn.MouseButton1Click:Connect(function()
    autoFarm = not autoFarm
    farmBtn.Text = autoFarm and "Auto Farm: ON" or "Auto Farm: OFF"

    while autoFarm do
        local monster = getNearestMonster()
        if monster then
            hrp.CFrame = monster.HumanoidRootPart.CFrame * CFrame.new(0, 0, -4)
        end
        task.wait(0.4)
    end
end)

-- TP MONSTER
tpBtn.MouseButton1Click:Connect(function()
    local monster = getNearestMonster()
    if monster then
        hrp.CFrame = monster.HumanoidRootPart.CFrame * CFrame.new(0, 0, -4)
    end
end)
