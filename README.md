-- Rayfield UI - Mobile Friendly Script Executor

local Rayfield = loadstring(game:HttpGet("https://raw.githubusercontent.com/shlexware/Rayfield/main/source"))()

local Window = Rayfield:CreateWindow({
   Name = "Mobile Script Hub",
   LoadingTitle = "Đang tải...",
   LoadingSubtitle = "Rayfield UI Mobile Style",
   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil,
      FileName = "MobileScriptUI"
   },
   Discord = {
      Enabled = false
   },
   KeySystem = false
})

local MainTab = Window:CreateTab("Chức năng", 4483362458)

-- Speed slider
MainTab:CreateSlider({
   Name = "Tốc độ chạy",
   Range = {16, 150},
   Increment = 1,
   Suffix = "Speed",
   CurrentValue = 16,
   Callback = function(Value)
       game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
   end,
})

-- Bay Toggle + Speed control
local flying = false
local flySpeed = 50

MainTab:CreateSlider({
   Name = "Tốc độ bay",
   Range = {10, 200},
   Increment = 5,
   Suffix = "FlySpeed",
   CurrentValue = 50,
   Callback = function(Value)
       flySpeed = Value
   end,
})

MainTab:CreateToggle({
   Name = "Bật/Tắt Bay",
   CurrentValue = false,
   Callback = function(state)
       flying = state
       local player = game.Players.LocalPlayer
       local char = player.Character or player.CharacterAdded:Wait()
       local hrp = char:WaitForChild("HumanoidRootPart")

       while flying do
           task.wait()
           hrp.Velocity = Vector3.new(0, flySpeed / 10, 0)
       end
   end
})
