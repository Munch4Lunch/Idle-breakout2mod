-- Get the necessary services and objects
local UserInputService = game:GetService("UserInputService")
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local flying = false

-- Set up keybinding (change KeyCode to your desired key)
local flyKey = Enum.KeyCode.e

-- Function to toggle flying
local function toggleFly()
    if flying then
        humanoid:Move(Vector3.new(0, -100, 0)) -- Drop the character to the ground
        humanoid:Move(Vector3.new(0, 100, 0)) -- Lift the character off the ground slightly
    end
    flying = not flying
    humanoid.PlatformStand = flying
end

-- Listen for the key press
UserInputService.InputBegan:Connect(function(input)
    if input.KeyCode == flyKey then
        toggleFly()
    end
end)

-- Disable flying when the character dies
character.Humanoid.Died:Connect(function()
    if flying then
        toggleFly()
    end
end)
