-- Get the necessary services and objects
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

-- Define the initial and incremental speed values
local initialSpeed = 23
local speedIncrement = 4
local currentSpeed = initialSpeed

-- Function to increase the speed
local function increaseSpeed()
    currentSpeed = currentSpeed + speedIncrement
    humanoid.WalkSpeed = currentSpeed
end

-- Timer to increase the speed every second
while true do
    wait(1) -- Wait for 1 second
    increaseSpeed()

    
end
