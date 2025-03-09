local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local ToggleButton = Instance.new("TextButton")
local TextLabel = Instance.new("TextLabel")
local HideButton = Instance.new("TextButton")
local PowerLabel = Instance.new("TextLabel")
local PowerSlider = Instance.new("TextButton")
local PowerBar = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.ResetOnSpawn = false

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
Frame.Position = UDim2.new(0.35, 0, 0.4, 0)
Frame.Size = UDim2.new(0, 220, 0, 150)
Frame.Active = true
Frame.Draggable = true
UICorner.Parent = Frame

TextLabel.Parent = Frame
TextLabel.BackgroundTransparency = 1
TextLabel.Size = UDim2.new(1, 0, 0.2, 0)
TextLabel.Font = Enum.Font.SourceSansBold
TextLabel.Text = "Fuck Fling"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextSize = 22

ToggleButton.Parent = Frame
ToggleButton.Position = UDim2.new(0.1, 0, 0.3, 0)
ToggleButton.Size = UDim2.new(0.8, 0, 0.2, 0)
ToggleButton.Font = Enum.Font.SourceSansBold
ToggleButton.Text = "OFF"
ToggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ToggleButton.BackgroundColor3 = Color3.fromRGB(150, 0, 0)
ToggleButton.TextSize = 24
UICorner:Clone().Parent = ToggleButton

PowerLabel.Parent = Frame
PowerLabel.BackgroundTransparency = 1
PowerLabel.Position = UDim2.new(0.1, 0, 0.55, 0)
PowerLabel.Size = UDim2.new(0.8, 0, 0.15, 0)
PowerLabel.Font = Enum.Font.SourceSansBold
PowerLabel.Text = "Fling Power: 10000"
PowerLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
PowerLabel.TextSize = 18

PowerBar.Parent = Frame
PowerBar.Position = UDim2.new(0.1, 0, 0.7, 0)
PowerBar.Size = UDim2.new(0.8, 0, 0.1, 0)
PowerBar.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
UICorner:Clone().Parent = PowerBar
PowerSlider.Parent = PowerBar
PowerSlider.Size = UDim2.new(0.1, 0, 1, 0)
PowerSlider.BackgroundColor3 = Color3.fromRGB(0, 150, 255)
UICorner:Clone().Parent = PowerSlider
HideButton.Parent = ScreenGui
HideButton.Position = UDim2.new(0.05, 0, 0.9, 0)
HideButton.Size = UDim2.new(0, 50, 0, 30)
HideButton.Font = Enum.Font.SourceSansBold
HideButton.Text = "👁"
HideButton.TextColor3 = Color3.fromRGB(255, 255, 255)
HideButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
UICorner:Clone().Parent = HideButton
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local RunService = game:GetService("RunService")
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")

local hiddenfling = false
local flingPower = 10000
local lp = Players.LocalPlayer
local dragging = false

if not ReplicatedStorage:FindFirstChild("juisdfj0i32i0eidsuf0iok") then
	local detection = Instance.new("Decal")
	detection.Name = "juisdfj0i32i0eidsuf0iok"
	detection.Parent = ReplicatedStorage
end

local function fling()
	local hrp, c, vel, movel = nil, nil, nil, 0.1
	
	while true do
		RunService.Heartbeat:Wait()
		if hiddenfling then
			while hiddenfling and not (c and c.Parent and hrp and hrp.Parent) do
				RunService.Heartbeat:Wait()
				c = lp.Character
				hrp = c and c:FindFirstChild("HumanoidRootPart")
			end

			if hiddenfling then
				vel = hrp.Velocity
				hrp.Velocity = vel * flingPower + Vector3.new(0, flingPower, 0)
				RunService.RenderStepped:Wait()
				if c and c.Parent and hrp and hrp.Parent then
					hrp.Velocity = vel
				end
				RunService.Stepped:Wait()
				if c and c.Parent and hrp and hrp.Parent then
					hrp.Velocity = vel + Vector3.new(0, movel, 0)
					movel = movel * -1
				end
			end
		end
	end
end

ToggleButton.MouseButton1Click:Connect(function()
	hiddenfling = not hiddenfling
	if hiddenfling then
		ToggleButton.Text = "ON"
		ToggleButton.BackgroundColor3 = Color3.fromRGB(0, 150, 0)
	else
		ToggleButton.Text = "OFF"
		ToggleButton.BackgroundColor3 = Color3.fromRGB(150, 0, 0)
	end
end)

HideButton.MouseButton1Click:Connect(function()
	Frame.Visible = not Frame.Visible
	if Frame.Visible then
		HideButton.Text = "👁"
	else
		HideButton.Text = "👀"
	end
end)

PowerSlider.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		dragging = true
	end
end)

PowerSlider.InputEnded:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		dragging = false
	end
end)

UserInputService.InputChanged:Connect(function(input)
	if dragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
		local mousePos = input.Position.X
		local barPos = PowerBar.AbsolutePosition.X
		local barSize = PowerBar.AbsoluteSize.X
		local newPos = math.clamp((mousePos - barPos) / barSize, 0, 1)
		
		PowerSlider.Position = UDim2.new(newPos, 0, 0, 0)
		flingPower = math.floor(newPos * 50000) + 5000
		PowerLabel.Text = "Fling Power: " .. flingPower
	end
end)

fling()
