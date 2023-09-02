-- Get the necessary services and objects
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local flying = false

-- Define flight speed and direction (you can adjust these values)
local flightSpeed = 50 -- Adjust this to control how fast you fly
local flightDirection = Vector3.new(0, 1, 0) -- Adjust this to control the flight direction (upwards)

-- Function to toggle flying
local function toggleFly()
    flying = not flying
    humanoid:Move(Vector3.new(0, 0, 0)) -- Reset any existing character velocity
end

-- Function to update flying behavior
local function updateFly()
    if flying then
        local moveDirection = flightDirection * flightSpeed
        humanoid:Move(moveDirection)
    end
end

-- Listen for the character's death to disable flying
character.Humanoid.Died:Connect(function()
    if flying then
        toggleFly()
    end
end)

-- Main loop for updating flight
while true do
    updateFly()
    wait(0.1) -- Adjust the wait time as needed
end
