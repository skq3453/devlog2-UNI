## Get Stuff
```lua
local lib = {}

function lib:CreateWindow(title)
	local UI = Instance.new("ScreenGui")
	local Main = Instance.new("Frame")
	local UICorner = Instance.new("UICorner")
	local Title = Instance.new("TextLabel")
	local Line = Instance.new("Frame")
	local Navigation = Instance.new("ScrollingFrame")
	local UIListLayout = Instance.new("UIListLayout")
	local Line_2 = Instance.new("Frame")
	local Content = Instance.new("Frame")
	
	UI.Name = "UI"
	UI.Parent = game:GetService("Players").LocalPlayer.PlayerGui or game:GetService("CoreGui")
	UI.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	UI.ResetOnSpawn = false

	Main.Name = "Main"
	Main.Parent = UI
	Main.BackgroundColor3 = Color3.fromRGB(11, 11, 11)
	Main.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Main.BorderSizePixel = 0
	Main.Position = UDim2.new(0, 243, 0, 75)
	Main.Size = UDim2.new(0, 526, 0, 384)

	UICorner.Parent = Main

	Title.Name = "Title"
	Title.Parent = Main
	Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Title.BackgroundTransparency = 1.000
	Title.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Title.BorderSizePixel = 0
	Title.Size = UDim2.new(0, 145, 0, 90)
	Title.Text = title
	Title.TextColor3 = Color3.fromRGB(34, 150, 190)
	Title.TextSize = 19.000

	Line.Name = "Line"
	Line.Parent = Main
	Line.BackgroundColor3 = Color3.fromRGB(51, 51, 51)
	Line.BackgroundTransparency = 0.500
	Line.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Line.BorderSizePixel = 0
	Line.Position = UDim2.new(0.00760456268, 0, 0.182291672, 0)
	Line.Size = UDim2.new(0, 149, 0, 1)

	Navigation.Name = "Navigation"
	Navigation.Parent = Main
	Navigation.Active = true
	Navigation.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Navigation.BackgroundTransparency = 1.000
	Navigation.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Navigation.BorderSizePixel = 0
	Navigation.Position = UDim2.new(0.0100000184, 0, 0.234375, 0)
	Navigation.Size = UDim2.new(0, 151, 0, 284)
	Navigation.ScrollBarImageColor3 = Color3.fromRGB(0, 0, 0)
	Navigation.CanvasSize = UDim2.new(0, 0, 15, 0)
	Navigation.ScrollBarThickness = 0

	UIListLayout.Parent = Navigation
	UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
	UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	
	Line_2.Name = "Line"
	Line_2.Parent = Main
	Line_2.BackgroundColor3 = Color3.fromRGB(51, 51, 51)
	Line_2.BackgroundTransparency = 0.500
	Line_2.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Line_2.BorderSizePixel = 0
	Line_2.Position = UDim2.new(0.306083649, 0, 0, 0)
	Line_2.Size = UDim2.new(0, 1, 0, 384)

	Content.Name = "Content"
	Content.Parent = Main
	Content.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Content.BackgroundTransparency = 1.000
	Content.BorderColor3 = Color3.fromRGB(0, 0, 0)
	Content.BorderSizePixel = 0
	Content.Position = UDim2.new(0.307984799, 0, 0, 0)
	Content.Size = UDim2.new(0, 364, 0, 384)
	
	local function UOWIQVY_script() -- Main.dragWindow 
		local script = Instance.new('LocalScript', Main)

		local TweenService = game:GetService("TweenService")
		local UserInputService = game:GetService("UserInputService")

		local gui = script.Parent

		local dragging
		local dragInput
		local dragStart
		local startPos

		local tweenInfo = TweenInfo.new(0.16, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)

		local function update(input)
			local delta = input.Position - dragStart
			local targetPos = UDim2.new(
				startPos.X.Scale, 
				startPos.X.Offset + delta.X, 
				startPos.Y.Scale, 
				startPos.Y.Offset + delta.Y
			)

			local tween = TweenService:Create(gui, tweenInfo, {Position = targetPos})
			tween:Play()
		end

		gui.InputBegan:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				dragging = true
				dragStart = input.Position
				startPos = gui.Position

				-- Listen for input state change to end dragging
				input.Changed:Connect(function()
					if input.UserInputState == Enum.UserInputState.End then
						dragging = false
					end
				end)
			end
		end)

		gui.InputChanged:Connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
				dragInput = input
			end
		end)

		UserInputService.InputChanged:Connect(function(input)
			if input == dragInput and dragging then
				update(input)
			end
		end)

	end
	coroutine.wrap(UOWIQVY_script)()
	
	local TweenService = game:GetService("TweenService")

	local SelectedTab
	local FirstTabCreated = false

	function lib:CreateTab(title)
		local Tab = Instance.new("TextButton")
		local UICorner_3 = Instance.new("UICorner")
		local UIGradient_2 = Instance.new("UIGradient")
		local Title_3 = Instance.new("TextLabel")
		local Items = Instance.new("ScrollingFrame")
		local UIListLayout_2 = Instance.new("UIListLayout")
		local UIPadding = Instance.new("UIPadding")

		Tab.Name = "Tab"
		Tab.Parent = Navigation
		Tab.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Tab.BackgroundTransparency = 1.000
		Tab.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Tab.BorderSizePixel = 0
		Tab.Position = UDim2.new(0.0331125818, 0, 0, 0)
		Tab.Size = UDim2.new(0, 141, 0, 35)
		Tab.AutoButtonColor = false
		Tab.Font = Enum.Font.SourceSans
		Tab.Text = ""
		Tab.TextColor3 = Color3.fromRGB(0, 0, 0)
		Tab.TextSize = 14.000

		UICorner_3.CornerRadius = UDim.new(0, 6)
		UICorner_3.Parent = Tab

		UIGradient_2.Color = ColorSequence.new{
			ColorSequenceKeypoint.new(0.00, Color3.fromRGB(30, 150, 190)),
			ColorSequenceKeypoint.new(1.00, Color3.fromRGB(11, 11, 11))
		}
		UIGradient_2.Parent = Tab

		Title_3.Name = "Title"
		Title_3.Parent = Tab
		Title_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_3.BackgroundTransparency = 1.000
		Title_3.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Title_3.BorderSizePixel = 0
		Title_3.Position = UDim2.new(0.0709219873, 0, 0.0678571463, 0)
		Title_3.Size = UDim2.new(0, 124, 0, 30)
		Title_3.Text = title
		Title_3.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title_3.TextSize = 15.000
		Title_3.TextStrokeTransparency = 0.600
		Title_3.TextTransparency = 0.600
		Title_3.TextXAlignment = Enum.TextXAlignment.Left

		Items.Name = title
		Items.Parent = Content
		Items.Active = true
		Items.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Items.BackgroundTransparency = 1.000
		Items.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Items.BorderSizePixel = 0
		Items.Size = UDim2.new(0, 364, 0, 384)
		Items.ScrollBarImageColor3 = Color3.fromRGB(0, 0, 0)
		Items.CanvasSize = UDim2.new(0, 0, 25, 0)
		Items.ScrollBarThickness = 0
		Items.Visible = false

		UIListLayout_2.Parent = Items
		UIListLayout_2.HorizontalAlignment = Enum.HorizontalAlignment.Center
		UIListLayout_2.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout_2.Padding = UDim.new(0, 8)

		UIPadding.Parent = Items
		UIPadding.PaddingTop = UDim.new(0, 6)

		Tab.MouseButton1Click:Connect(function()
			if SelectedTab ~= nil then
				local previousTitle = SelectedTab:FindFirstChild("Title")
				local previousTab = SelectedTab
				local previousItems = Content:FindFirstChild(previousTab.Title.Text)

				if previousItems then
					previousItems.Visible = false
				end

				TweenService:Create(previousTab, TweenInfo.new(0.2), {BackgroundTransparency = 1}):Play()
				TweenService:Create(previousTitle, TweenInfo.new(0.2), {TextTransparency = 0.6}):Play()
				previousTitle.TextStrokeTransparency = 1
			end

			SelectedTab = Tab
			local selectedItems = Content:FindFirstChild(title)

			if selectedItems then
				selectedItems.Visible = true
			end

			TweenService:Create(Tab, TweenInfo.new(0.2), {BackgroundTransparency = 0}):Play()
			TweenService:Create(Title_3, TweenInfo.new(0.2), {TextTransparency = 0}):Play()
			Title_3.TextStrokeTransparency = 0.6
		end)

		return Tab, Items
	end


	local TweenService = game:GetService("TweenService")

	function lib:CreateToggle(title, TabParent, callback)
		local Toggle = Instance.new("ImageButton")
		local UICorner_4 = Instance.new("UICorner")
		local UIStroke = Instance.new("UIStroke")
		local UIGradient_3 = Instance.new("UIGradient")
		local Title_4 = Instance.new("TextLabel")
		local Checkbox = Instance.new("Frame")
		local UICorner_5 = Instance.new("UICorner")
		local UIStroke_2 = Instance.new("UIStroke")
		local UIGradient_4 = Instance.new("UIGradient")
		local CheckboxButton = Instance.new("TextButton")

		Toggle.Name = "Toggle"
		Toggle.Parent = TabParent
		Toggle.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
		Toggle.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Toggle.BorderSizePixel = 0
		Toggle.Position = UDim2.new(0.0178571437, 0, 0.0291005298, 0)
		Toggle.Size = UDim2.new(0, 351, 0, 40)
		Toggle.AutoButtonColor = false

		UICorner_4.CornerRadius = UDim.new(0, 6)
		UICorner_4.Parent = Toggle

		UIStroke.Parent = Toggle
		UIStroke.Color = Color3.fromRGB(255, 255, 255)
		UIStroke.Transparency = 1.000
		UIStroke.Thickness = 2.000

		UIGradient_3.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(30, 150, 190)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(11, 11, 11))}
		UIGradient_3.Parent = UIStroke

		Title_4.Name = "Title"
		Title_4.Parent = Toggle
		Title_4.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_4.BackgroundTransparency = 1.000
		Title_4.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Title_4.BorderSizePixel = 0
		Title_4.Position = UDim2.new(0.0281869397, 0, 0.117857173, 0)
		Title_4.Size = UDim2.new(0, 116, 0, 30)
		Title_4.Text = title
		Title_4.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title_4.TextSize = 12.000
		Title_4.TextStrokeTransparency = 0.600
		Title_4.TextTransparency = 0.600
		Title_4.TextXAlignment = Enum.TextXAlignment.Left

		Checkbox.Name = "Checkbox"
		Checkbox.Parent = Toggle
		Checkbox.BackgroundColor3 = Color3.fromRGB(11, 11, 11)
		Checkbox.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Checkbox.BorderSizePixel = 0
		Checkbox.Position = UDim2.new(0.886039913, 0, 0.200000003, 0)
		Checkbox.Size = UDim2.new(0, 29, 0, 23)

		UICorner_5.CornerRadius = UDim.new(0, 4)
		UICorner_5.Parent = Checkbox

		UIStroke_2.Parent = Checkbox
		UIStroke_2.Color = Color3.fromRGB(255, 255, 255)
		UIStroke_2.Transparency = 1.000
		UIStroke_2.Thickness = 2.000

		UIGradient_4.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(30, 150, 190)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(11, 11, 11))}
		UIGradient_4.Parent = UIStroke_2

		CheckboxButton.Name = "CheckboxButton"
		CheckboxButton.Parent = Checkbox
		CheckboxButton.BackgroundTransparency = 1
		CheckboxButton.Size = UDim2.new(1, 0, 1, 0)
		CheckboxButton.Text = ""
		CheckboxButton.AutoButtonColor = false

		local isChecked = false

		local function createTween(target, properties, time)
			local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
			local tween = TweenService:Create(target, tweenInfo, properties)
			tween:Play()
		end

		Toggle.MouseButton1Click:Connect(function()
			isChecked = not isChecked

			if isChecked then
				createTween(Checkbox, {BackgroundColor3 = Color3.fromRGB(30, 150, 190)}, 0.4)
				createTween(UIStroke_2, {Transparency = 0}, 0.2)
				createTween(Title_4, {TextTransparency = 0}, 0.2)
				createTween(UIStroke, {Transparency = 0}, 0.2)
			else
				createTween(Checkbox, {BackgroundColor3 = Color3.fromRGB(11, 11, 11)}, 0.4)
				createTween(UIStroke_2, {Transparency = 1}, 0.2)
				createTween(Title_4, {TextTransparency = 0.600}, 0.2)
				createTween(UIStroke, {Transparency = 1.000}, 0.2)
			end

			if callback then
				callback(isChecked)
			end
		end)
	end
	
	local TweenService = game:GetService("TweenService")

	function lib:CreateSlider(title, TabParent, min, max, callback)
		local Slider = Instance.new("ImageButton")
		local UICorner_6 = Instance.new("UICorner")
		local UIStroke_3 = Instance.new("UIStroke")
		local UIGradient_5 = Instance.new("UIGradient")
		local Title_5 = Instance.new("TextLabel")
		local SliderBack = Instance.new("Frame")
		local UICorner_7 = Instance.new("UICorner")
		local Draggable = Instance.new("Frame")
		local UICorner_8 = Instance.new("UICorner")
		local UIGradient_6 = Instance.new("UIGradient")
		local Value = Instance.new("TextLabel")

		Slider.Name = "Slider"
		Slider.Parent = TabParent
		Slider.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
		Slider.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Slider.BorderSizePixel = 0
		Slider.Position = UDim2.new(0.0178571437, 0, 0.288359791, 0)
		Slider.Size = UDim2.new(0, 351, 0, 42)
		Slider.AutoButtonColor = false

		UICorner_6.CornerRadius = UDim.new(0, 6)
		UICorner_6.Parent = Slider

		UIStroke_3.Parent = Slider
		UIStroke_3.Color = Color3.fromRGB(255, 255, 255)
		UIStroke_3.Transparency = 1.000
		UIStroke_3.Thickness = 2.000

		UIGradient_5.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(30, 150, 190)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(11, 11, 11))}
		UIGradient_5.Parent = UIStroke_3

		Title_5.Name = "Title"
		Title_5.Parent = Slider
		Title_5.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Title_5.BackgroundTransparency = 1.000
		Title_5.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Title_5.BorderSizePixel = 0
		Title_5.Position = UDim2.new(0.0281869397, 0, -0.00714274822, 0)
		Title_5.Size = UDim2.new(0, 116, 0, 30)
		Title_5.Text = title
		Title_5.TextColor3 = Color3.fromRGB(255, 255, 255)
		Title_5.TextSize = 12.000
		Title_5.TextStrokeTransparency = 0.600
		Title_5.TextTransparency = 0.600
		Title_5.TextXAlignment = Enum.TextXAlignment.Left

		SliderBack.Name = "SliderBack"
		SliderBack.Parent = Slider
		SliderBack.BackgroundColor3 = Color3.fromRGB(11, 11, 11)
		SliderBack.BorderColor3 = Color3.fromRGB(0, 0, 0)
		SliderBack.BorderSizePixel = 0
		SliderBack.Position = UDim2.new(0.0284900293, 0, 0.700340629, 0)
		SliderBack.Size = UDim2.new(0, 331, 0, 6)

		UICorner_7.CornerRadius = UDim.new(1, 0)
		UICorner_7.Parent = SliderBack

		Draggable.Name = "Draggable"
		Draggable.Parent = SliderBack
		Draggable.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Draggable.BackgroundTransparency = 0.600
		Draggable.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Draggable.BorderSizePixel = 0
		Draggable.Size = UDim2.new(0, 217, 0, 6)

		UICorner_8.CornerRadius = UDim.new(1, 0)
		UICorner_8.Parent = Draggable

		UIGradient_6.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(30, 150, 190)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(19, 50, 91))}
		UIGradient_6.Parent = Draggable

		Value.Name = "Value"
		Value.Parent = Slider
		Value.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Value.BackgroundTransparency = 1.000
		Value.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Value.BorderSizePixel = 0
		Value.Position = UDim2.new(0.646420538, 0, -0.00714256661, 0)
		Value.Size = UDim2.new(0, 116, 0, 30)
		Value.Text = "0.1"
		Value.TextColor3 = Color3.fromRGB(255, 255, 255)
		Value.TextSize = 10.000
		Value.TextStrokeTransparency = 0.600
		Value.TextTransparency = 0.600
		Value.TextXAlignment = Enum.TextXAlignment.Right

		local currentValue = min
		local isDragging = false
		local touchID = nil
		local UIS = game:GetService("UserInputService")

		local tweenInfo = TweenInfo.new(0.1, Enum.EasingStyle.Quad, Enum.EasingDirection.InOut)

		local function UpdateTransparency()
			if isDragging then
				local tweenStroke = TweenService:Create(UIStroke_3, tweenInfo, {Transparency = 0})
				tweenStroke:Play()
				local tweenTitle = TweenService:Create(Title_5, tweenInfo, {TextTransparency = 0})
				tweenTitle:Play()
				local tweenValue = TweenService:Create(Value, tweenInfo, {TextTransparency = 0})
				tweenValue:Play()
				local tweenDraggable = TweenService:Create(Draggable, tweenInfo, {BackgroundTransparency = 0})
				tweenDraggable:Play()
			else
				local tweenStroke = TweenService:Create(UIStroke_3, tweenInfo, {Transparency = 1})
				tweenStroke:Play()
				local tweenTitle = TweenService:Create(Title_5, tweenInfo, {TextTransparency = 0.6})
				tweenTitle:Play()
				local tweenValue = TweenService:Create(Value, tweenInfo, {TextTransparency = 0.6})
				tweenValue:Play()
				local tweenDraggable = TweenService:Create(Draggable, tweenInfo, {BackgroundTransparency = 0.6})
				tweenDraggable:Play()
			end
		end

		local function UpdateSliderPosition()
			local percentage = math.clamp((currentValue - min) / (max - min), 0, 1)
			Value.Text = string.format("%.1f", currentValue)
			Draggable.Size = UDim2.new(percentage, 0, 1, 0)
			callback(currentValue)
			UpdateTransparency()
		end

		local function StartDragging(input)
			isDragging = true
			if input.UserInputType == Enum.UserInputType.Touch then
				touchID = input.UserInputIndex
			end
			UpdateTransparency()
		end

		local function UpdateDragging(input)
			local inputPosition
			if input.UserInputType == Enum.UserInputType.MouseMovement then
				inputPosition = input.Position.X
			elseif input.UserInputType == Enum.UserInputType.Touch then
				inputPosition = input.Position.X
			end

			if isDragging then
				local sliderX = SliderBack.AbsolutePosition.X
				local sliderWidth = SliderBack.AbsoluteSize.X
				local newPercentage = math.clamp((inputPosition - sliderX) / sliderWidth, 0, 1)
				currentValue = min + (newPercentage * (max - min))
				currentValue = math.round(currentValue * 10) / 10
				UpdateSliderPosition()
			end
		end

		local function StopDragging(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				isDragging = false
				touchID = nil
				UpdateTransparency()
			end
		end

		Slider.MouseButton1Down:Connect(StartDragging)
		UIS.InputChanged:Connect(UpdateDragging)
		UIS.InputEnded:Connect(StopDragging)

		UpdateSliderPosition()
	end

	return lib
end
```
## Create Window
```lua
lib:CreateWindow("UIS")
```
## Create Tab
```lua
local MagnetTab, MagnetTab = lib:CreateTab("Magnets")
```
## Create Toggle
```lua
lib:CreateToggle("Enable Magnets", MagnetTab, function(state)
	print("Magnet toggle state:", state)
end)
```
## Create Slider
```lua
lib:CreateSlider("Magnet Delay", MagnetTab, 0, 1, function(value)
	print("Current Value: " .. value)
end)
```
