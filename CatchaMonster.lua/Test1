-- CATCH A MONSTER - MENU + AUTO FARM + TP
-- Delta Executor

local player = game.Players.LocalPlayer
local char = player.Character or player.CharacterAdded:Wait()
local hrp = char:WaitForChild("HumanoidRootPart")

local autoFarm = false

-- Atualiza personagem ao morrer
player.CharacterAdded:Connect(function(c)
    char = c
    hrp = c:WaitForChild("HumanoidRootPart")
end)

-- ========== FUNÇÃO MONSTRO MAIS PRÓXIMO ==========
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

-- ========== GUI ==========
local gui = Instance.new("ScreenGui")
gui.Name = "CatchMonsterMenu"
gui.Parent = player:WaitForChild("PlayerGui")

-- Frame principal
local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 230, 0, 180)
main.Position = UDim2.new(0, 20, 0, 200)
main.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
main.BorderSizePixel = 0
main.Active = true
main.Draggable = true

-- Top bar
local top = Instance.new("Frame", main)
top.Size = UDim2.new(1, 0, 0, 30)
top.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
top.BorderSizePixel = 0

local title = Instance.new("TextLabel", top)
title.Size = UDim2.new(1, -40, 1, 0)
title.Position = UDim2.new(0, 10, 0, 0)
title.Text = "Catch a Monster"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.BackgroundTransparency = 1
title.TextXAlignment = Enum.TextXAlignment.Left

-- Botão minimizar
local minimize = Instance.new("TextButton", top)
minimize.Size = UDim2.new(0, 30, 0, 30)
minimize.Position = UDim2.new(1, -30, 0, 0)
minimize.Text = "-"
minimize.TextScaled = true
minimize.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
minimize.TextColor3 = Color3.fromRGB(255, 255, 255)
minimize.BorderSizePixel = 0

-- Conteúdo
local content = Instance.new("Frame", main)
content.Size = UDim2.new(1, 0, 1, -30)
content.Position = UDim2.new(0, 0, 0, 30)
content.BackgroundTransparency = 1

-- Botão Auto Farm
local farmBtn = Instance.new("TextButton", content)
farmBtn.Size = UDim2.new(1, -20, 0, 40)
farmBtn.Position = UDim2.new(0, 10, 0, 10)
farmBtn.Text = "Auto Farm: OFF"
farmBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
farmBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
farmBtn.BorderSizePixel = 0
farmBtn.TextScaled = true

-- Botão TP
local tpBtn = Instance.new("TextButton", content)
tpBtn.Size = UDim2.new(1, -20, 0, 40)
tpBtn.Position = UDim2.new(0, 10, 0, 60)
tpBtn.Text = "TP Monster"
tpBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
tpBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
tpBtn.BorderSizePixel = 0
tpBtn.TextScaled = true

-- ========== FUNÇÕES ==========
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

tpBtn.MouseButton1Click:Connect(function()
    local monster = getNearestMonster()
    if monster then
        hrp.CFrame = monster.HumanoidRootPart.CFrame * CFrame.new(0, 0, -4)
    end
end)

-- Minimizar menu
local minimized = false
minimize.MouseButton1Click:Connect(function()
    minimized = not minimized
    if minimized then
        content.Visible = false
        main.Size = UDim2.new(0, 230, 0, 30)
        minimize.Text = "+"
    else
        content.Visible = true
        main.Size = UDim2.new(0, 230, 0, 180)
        minimize.Text = "-"
    end
end)
