--[[
    Script Name: Universal Roblox Mobile Cheat
    Author: maingocha
    Created Date: March 08, 2025
    Description: Script hỗ trợ Aimbot, ESP, Bullet Magic, iPad View, No Recoil cho Roblox trên mobile với menu đơn giản và nút nổi bật/tắt.
--]]

-- Tải thư viện GUI và khai báo biến toàn cục
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local Camera = game.Workspace.CurrentCamera
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

-- Biến trạng thái
local Toggle = {
    AimbotWall = false,
    AimbotNoWall = false,
    ESP = false,
    BulletMagic = false,
    iPadView = false,
    NoRecoil = false
}

-- Cài đặt Aimbot
local FOV = 100
local AimPart = "Head"
local FOVCircleVisible = true

-- Cài đặt ESP
local ESPColorMode = "Default" -- Default, Rainbow, Custom
local CustomESPColor = Color3.fromRGB(255, 0, 0) -- Màu mặc định là đỏ

-- Giao diện GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.CoreGui
ScreenGui.Name = "MobileCheatMenu"

-- Vòng tròn FOV
local FOVCircle = Instance.new("ImageLabel")
FOVCircle.Size = UDim2.new(0, FOV * 2, 0, FOV * 2)
FOVCircle.Position = UDim2.new(0.5, -FOV, 0.5, -FOV)
FOVCircle.Image = "rbxassetid://3570695787"
FOVCircle.ImageTransparency = 0.5
FOVCircle.BackgroundTransparency = 1
FOVCircle.ImageColor3 = Color3.fromRGB(255, 0, 0)
FOVCircle.Parent = ScreenGui
FOVCircle.Visible = FOVCircleVisible

-- Nút nổi bật/tắt
local ToggleButton = Instance.new("TextButton")
ToggleButton.Size = UDim2.new(0, 60, 0, 60)
ToggleButton.Position = UDim2.new(0.9, -70, 0.1, 10)
ToggleButton.Text = "ON/OFF"
ToggleButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
ToggleButton.Parent = ScreenGui
ToggleButton.Draggable = true

-- Menu chính
local MenuFrame = Instance.new("Frame")
MenuFrame.Size = UDim2.new(0, 200, 0, 450) -- Tăng chiều cao để chứa thêm No Recoil và ESP Color
MenuFrame.Position = UDim2.new(0.5, -100, 0.5, -225)
MenuFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
MenuFrame.Visible = false
MenuFrame.Parent = ScreenGui

-- Tiêu đề menu
local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0, 30)
Title.Text = "Cheat Menu by maingocha"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Title.Parent = MenuFrame

-- Hiển thị thời gian
local TimeLabel = Instance.new("TextLabel")
TimeLabel.Size = UDim2.new(0, 180, 0, 20)
TimeLabel.Position = UDim2.new(0, 10, 0, 340)
TimeLabel.Text = "Time: Loading..."
TimeLabel.TextColor3 = Color3.fromRGB(0, 255, 255)
TimeLabel.BackgroundTransparency = 1
TimeLabel.TextScaled = true
TimeLabel.Parent = MenuFrame

-- Hiển thị vị trí
local PositionLabel = Instance.new("TextLabel")
PositionLabel.Size = UDim2.new(0, 180, 0, 20)
PositionLabel.Position = UDim2.new(0, 10, 0, 360)
PositionLabel.Text = "Position: Loading..."
PositionLabel.TextColor3 = Color3.fromRGB(0, 255, 255)
PositionLabel.BackgroundTransparency = 1
PositionLabel.TextScaled = true
PositionLabel.Parent = MenuFrame

-- Hình ảnh quảng cáo kênh
local PromoImage = Instance.new("ImageLabel")
PromoImage.Size = UDim2.new(0, 180, 0, 100)
PromoImage.Position = UDim2.new(0, 10, 0, 390)
PromoImage.Image = "rbxassetid://1234567890" -- Thay bằng ImageId thật
PromoImage.BackgroundTransparency = 1
PromoImage.Parent = MenuFrame

-- Văn bản chứa link YouTube và TikTok
local LinkText = Instance.new("TextLabel")
LinkText.Size = UDim2.new(0, 180, 0, 50)
LinkText.Position = UDim2.new(0, 10, 0, 490)
LinkText.Text = "YT: youtube.com/@maingocha\nTT: tiktok.com/@maingocha"
LinkText.TextColor3 = Color3.fromRGB(255, 255, 0)
LinkText.BackgroundTransparency = 1
LinkText.TextScaled = true
LinkText.Parent = MenuFrame

-- Nút bật/tắt các tính năng
local function CreateToggleButton(name, yPos, toggleVar)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0, 180, 0, 40)
    btn.Position = UDim2.new(0, 10, 0, yPos)
    btn.Text = name .. ": OFF"
    btn.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.Parent = MenuFrame
    btn.MouseButton1Click:Connect(function()
        Toggle[toggleVar] = not Toggle[toggleVar]
        btn.Text = name .. ": " .. (Toggle[toggleVar] and "ON" or "OFF")
        btn.BackgroundColor3 = Toggle[toggleVar] and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(100, 100, 100)
    end)
end

CreateToggleButton("Aimbot (Wall)", 40, "AimbotWall")
CreateToggleButton("Aimbot (No Wall)", 90, "AimbotNoWall")
CreateToggleButton("ESP", 140, "ESP")
CreateToggleButton("Bullet Magic", 190, "BulletMagic")
CreateToggleButton("iPad View", 240, "iPadView")
CreateToggleButton("No Recoil", 290, "NoRecoil")

-- Điều chỉnh FOV cho iPad View
local FOVLabel = Instance.new("TextLabel")
FOVLabel.Size = UDim2.new(0, 180, 0, 20)
FOVLabel.Position = UDim2.new(0, 10, 0, 330)
FOVLabel.Text = "FOV: " .. FOV
FOVLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
FOVLabel.BackgroundTransparency = 1
FOVLabel.Parent = MenuFrame

local IncreaseFOV = Instance.new("TextButton")
IncreaseFOV.Size = UDim2.new(0, 40, 0, 20)
IncreaseFOV.Position = UDim2.new(0, 140, 0, 330)
IncreaseFOV.Text = "+"
IncreaseFOV.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
IncreaseFOV.Parent = MenuFrame
IncreaseFOV.MouseButton1Click:Connect(function()
    FOV = math.min(FOV + 10, 200)
    FOVLabel.Text = "FOV: " .. FOV
    FOVCircle.Size = UDim2.new(0, FOV * 2, 0, FOV * 2)
    FOVCircle.Position = UDim2.new(0.5, -FOV, 0.5, -FOV)
end)

local DecreaseFOV = Instance.new("TextButton")
DecreaseFOV.Size = UDim2.new(0, 40, 0, 20)
DecreaseFOV.Position = UDim2.new(0, 100, 0, 330)
DecreaseFOV.Text = "-"
DecreaseFOV.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
DecreaseFOV.Parent = MenuFrame
DecreaseFOV.MouseButton1Click:Connect(function()
    FOV = math.max(FOV - 10, 50)
    FOVLabel.Text = "FOV: " .. FOV
    FOVCircle.Size = UDim2.new(0, FOV * 2, 0, FOV * 2)
    FOVCircle.Position = UDim2.new(0.5, -FOV, 0.5, -FOV)
end)

-- ESP Color Mode
local ESPColorButton = Instance.new("TextButton")
ESPColorButton.Size = UDim2.new(0, 180, 0, 40)
ESPColorButton.Position = UDim2.new(0, 10, 0, 180)
ESPColorButton.Text = "ESP Color: Default"
ESPColorButton.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
ESPColorButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ESPColorButton.Parent = MenuFrame
ESPColorButton.MouseButton1Click:Connect(function()
    if ESPColorMode == "Default" then
        ESPColorMode = "Rainbow"
        ESPColorButton.Text = "ESP Color: Rainbow"
    elseif ESPColorMode == "Rainbow" then
        ESPColorMode = "Custom"
        ESPColorButton.Text = "ESP Color: Custom (Red)"
    else
        ESPColorMode = "Default"
        ESPColorButton.Text = "ESP Color: Default"
    end
end)

-- Logic bật/tắt menu
ToggleButton.MouseButton1Click:Connect(function()
    MenuFrame.Visible = not MenuFrame.Visible
end)

-- Hàm Aimbot
local function GetClosestPlayer(wallCheck)
    local closestPlayer = nil
    local shortestDistance = FOV
    local mousePos = UserInputService:GetMouseLocation()

    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild(AimPart) then
            local humanoid = player.Character:FindFirstChild("Humanoid")
            if humanoid and humanoid.Health > 0 then
                local screenPos, onScreen = Camera:WorldToViewportPoint(player.Character[AimPart].Position)
                local distance = (Vector2.new(screenPos.X, screenPos.Y) - mousePos).Magnitude
                if distance < shortestDistance then
                    if wallCheck then
                        local ray = Ray.new(Camera.CFrame.Position, (player.Character[AimPart].Position - Camera.CFrame.Position).Unit * 1000)
                        local part = workspace:FindPartOnRayWithIgnoreList(ray, {LocalPlayer.Character})
                        if not part or part:IsDescendantOf(player.Character) then
                            closestPlayer = player
                            shortestDistance = distance
                        end
                    else
                        closestPlayer = player
                        shortestDistance = distance
                    end
                end
            end
        end
    end
    return closestPlayer
end

-- Hàm ESP
local function CreateESP(player)
    if player ~= LocalPlayer and player.Character then
        local humanoidRoot = player.Character:FindFirstChild("HumanoidRootPart")
        if humanoidRoot then
            local esp = Instance.new("BillboardGui")
            esp.Name = "ESP"
            esp.Adornee = humanoidRoot
            esp.Size = UDim2.new(0, 100, 0, 50)
            esp.StudsOffset = Vector3.new(0, 3, 0)
            esp.AlwaysOnTop = true
            esp.Parent = player.Character

            local text = Instance.new("TextLabel")
            text.Size = UDim2.new(1, 0, 1, 0)
            text.Text = player.Name
            text.BackgroundTransparency = 1
            text.TextColor3 = (ESPColorMode == "Default" or ESPColorMode == "Custom") and CustomESPColor or Color3.fromRGB(255, 0, 0)
            text.Parent = esp
        end
    end
end

-- Bullet Magic
local function ApplyBulletMagic()
    for _, tool in pairs(LocalPlayer.Backpack:GetChildren()) do
        if tool:IsA("Tool") then
            local handle = tool:FindFirstChild("Handle")
            if handle then
                handle.Massless = true
            end
        end
    end
end

-- No Recoil
local function ApplyNoRecoil()
    if Toggle.NoRecoil then
        local oldCFrame = Camera.CFrame
        Camera.CFrame = oldCFrame -- Giữ camera ổn định, giảm giật
    end
end

-- iPad View
local function SetiPadView()
    if Toggle.iPadView then
        Camera.FieldOfView = FOV
    else
        Camera.FieldOfView = 70
    end
end

-- Cập nhật thời gian và vị trí
local function UpdateTimeAndPosition()
    TimeLabel.Text = "Time: " .. os.date("%H:%M:%S", os.time())
    if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        local pos = LocalPlayer.Character.HumanoidRootPart.Position
        PositionLabel.Text = string.format("Position: %.1f, %.1f, %.1f", pos.X, pos.Y, pos.Z)
    else
        PositionLabel.Text = "Position: N/A"
    end
end

-- Hiệu ứng Rainbow cho ESP
local function UpdateRainbowColor()
    if ESPColorMode == "Rainbow" then
        local hue = (tick() % 5) / 5
        return Color3.fromHSV(hue, 1, 1)
    end
    return CustomESPColor
end

-- Vòng lặp chính
RunService.RenderStepped:Connect(function()
    -- Aimbot
    local target = nil
    if Toggle.AimbotWall then
        target = GetClosestPlayer(false)
    elseif Toggle.AimbotNoWall then
        target = GetClosestPlayer(true)
    end
    if target and target.Character and target.Character:FindFirstChild(AimPart) then
        local screenPos = Camera:WorldToViewportPoint(target.Character[AimPart].Position)
        local distance = (Vector2.new(screenPos.X, screenPos.Y) - UserInputService:GetMouseLocation()).Magnitude
        if distance <= FOV then
            Camera.CFrame = CFrame.new(Camera.CFrame.Position, target.Character[AimPart].Position)
        end
    end

    -- ESP
    if Toggle.ESP then
        for _, player in pairs(Players:GetPlayers()) do
            if player.Character and not player.Character:FindFirstChild("ESP") then
                CreateESP(player)
            end
            if player.Character and player.Character:FindFirstChild("ESP") then
                local text = player.Character.ESP:FindFirstChild("TextLabel")
                if text then
                    text.TextColor3 = UpdateRainbowColor()
                end
            end
        end
    else
        for _, player in pairs(Players:GetPlayers()) do
            if player.Character and player.Character:FindFirstChild("ESP") then
                player.Character.ESP:Destroy()
            end
        end
    end

    -- Bullet Magic
    if Toggle.BulletMagic then
        ApplyBulletMagic()
    end

    -- No Recoil
    if Toggle.NoRecoil then
        ApplyNoRecoil()
    end

    -- iPad View
    SetiPadView()

    -- Cập nhật thời gian và vị trí
    UpdateTimeAndPosition()

    -- Hiển thị vòng tròn FOV
    FOVCircle.Visible = Toggle.AimbotWall or Toggle.AimbotNoWall
end)

-- Xử lý khi có người chơi mới
Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function()
        if Toggle.ESP then
            CreateESP(player)
        end
    end)
end)

print("Script by maingocha loaded! Nhấn nút ON/OFF để mở menu.")
