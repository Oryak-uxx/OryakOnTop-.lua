# OryakOnTop.lua
local player = game.Players.LocalPlayer
local button = script.Parent
local cooldownBar = button:WaitForChild("CooldownBar")

local DROP_FORCE = -120
local COOLDOWN = 3 -- secondes

local ready = true

-- initialise la barre
cooldownBar.Size = UDim2.new(1, 0, 0, 0)

local function startCooldown()
    ready = false
    
    cooldownBar.Size = UDim2.new(1, 0, 1, 0)

    local startTime = tick()

    while tick() - startTime < COOLDOWN do
        local progress = (tick() - startTime) / COOLDOWN
        
        cooldownBar.Size = UDim2.new(1, 0, 1 - progress, 0)
        
        game:GetService("RunService").RenderStepped:Wait()
    end

    cooldownBar.Size = UDim2.new(1, 0, 0, 0)
    ready = true
end

button.MouseButton1Click:Connect(function()
    if not ready then return end

    local character = player.Character
    if character then
        local root = character:FindFirstChild("HumanoidRootPart")
        if root then
            -- 💥 DROP
            root.AssemblyLinearVelocity = Vector3.new(
                root.AssemblyLinearVelocity.X,
                DROP_FORCE,
                root.AssemblyLinearVelocity.Z
            )

            -- démarre cooldown
            startCooldown()
        end
    end
end)
local player = game.Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Parent = player:WaitForChild("PlayerGui")

local label = Instance.new("TextLabel")
label.Parent = gui

label.Size = UDim2.new(0, 400, 0, 50)
label.Position = UDim2.new(0, 10, 0, 10)
label.BackgroundTransparency = 0.3
label.TextScaled = true
label.TextColor3 = Color3.fromRGB(0, 170, 255) -- BLEU
label.Font = Enum.Font.GothamBold

label.Text = "Join Discord : https://discord.gg/QnyzBg4N"
