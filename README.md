local Players = game:GetService("Players")

local function HighlightPlayer(player)
  -- Create a new highlight object.
  local highlight = Instance.new("Highlight")
  highlight.Parent = player.Character
  highlight.Color = Color3.fromRGB(255, 0, 0)
  highlight.Transparency = 0.5
end

-- Loop through all players and highlight them.
for _, player in ipairs(Players:GetPlayers()) do
  HighlightPlayer(player)
end
