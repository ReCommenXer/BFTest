--------------aaa


repeat wait() until game:IsLoaded()
repeat wait() until game:GetService("Players")

if not game:IsLoaded() then
	local GameLoadGui = Instance.new("Message",workspace);
	GameLoadGui.Text = 'Wait Game Loading';
	game.Loaded:Wait();
	GameLoadGui:Destroy();
	task.wait(1);
end;



if game:GetService("Players").LocalPlayer.PlayerGui.Main:FindFirstChild("ChooseTeam")  then
		repeat wait()
			if game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("Main").ChooseTeam.Visible == true then
				if Team == "Pirate" then
					for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.TextButton.Activated)) do                                                                                                
						v.Function()
					end
				elseif Team == "Marine" then
					for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Marines.Frame.TextButton.Activated)) do                                                                                                
						v.Function()
					end
				else
					for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.TextButton.Activated)) do                                                                                                
						v.Function()
					end
				end
			end
		until game.Players.LocalPlayer.Team ~= nil and game:IsLoaded()
	end

repeat wait() until game:GetService("Players").LocalPlayer
repeat wait() until game:GetService("Players").LocalPlayer.PlayerGui
repeat wait() until game:GetService("ReplicatedStorage").Effect.Container

local RebornXerHub = Instance.new("ScreenGui")
local Open = Instance.new("TextButton")
local fuckshit = Instance.new("UICorner")
local MODILEMAGE = Instance.new("ImageLabel")
local posto = Instance.new("UIStroke")

local ScreenGui = Instance.new("ScreenGui")
local ImageButton = Instance.new("ImageButton")


ScreenGui.Parent = game.CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

ImageButton.Parent = ScreenGui
ImageButton.Name = "Oped/CloseUi"
ImageButton.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
ImageButton.BorderSizePixel = 0
ImageButton.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
ImageButton.Size = UDim2.new(0, 45, 0, 45)
ImageButton.Draggable = true
ImageButton.Image = "rbxassetid://10039618734"
ImageButton.MouseButton1Down:connect(function()
    game:GetService("VirtualInputManager"):SendKeyEvent(true,305,false,game)
     game:GetService("VirtualInputManager"):SendKeyEvent(false,305,false,game)
    end)
    


fuckshit.Parent = Open

 MODILEMAGE.Name = "MODILEMAGE"
 MODILEMAGE.Parent = Open
 MODILEMAGE.BackgroundColor3 = Color3.fromRGB(51,255,255)
 MODILEMAGE.BackgroundTransparency = 1.000
 MODILEMAGE.BorderSizePixel = 0
 MODILEMAGE.Position = UDim2.new(0, 0.5, 0, 0)
 MODILEMAGE.Size = UDim2.new(0, 38, 0, 31)
 MODILEMAGE.Image = "rbxassetid://"
 
posto.Name = "posto"
 posto.Parent = Open
 posto.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 posto.Color = Color3.fromRGB(51,255,255)
 posto.LineJoinMode = Enum.LineJoinMode.Round
 posto.Thickness = 1
 posto.Transparency = 0
 posto.Enabled = true
 posto.Archivable = true



WindowBackgroundColor = Color3.fromRGB(12,12,12)
BackgroundItemColor = Color3.fromRGB(20, 20, 20)
TabWindowColor = Color3.fromRGB(30, 30, 30)
ContainerColor = Color3.fromRGB(30, 30, 30)
TitleTextColor = Color3.fromRGB(150, 150, 150)
ImageColor = Color3.fromRGB(0, 0, 255)
LineThemeColor = Color3.fromRGB(150, 150, 150)
TabTextColor = Color3.fromRGB(150, 150, 150)
TabImageColor = Color3.fromRGB(150, 150, 150)
TabThemeColor = Color3.fromRGB(250, 0, 0)
SectionColor = Color3.fromRGB(0, 0, 255)
SectionImageColor = Color3.fromRGB(150, 150, 150)
SectionTextColor = Color3.fromRGB(0, 0, 255)
SectionOn = Color3.fromRGB(0, 250, 0)

Color1 = Color3.fromRGB(255,255,255)
do 
    local GUI = game.CoreGui:FindFirstChild("ReBornxerHubGui") 
    if GUI then 
        GUI:Destroy()
    end
if Color == nil then
Color = Color3.fromRGB(255,255,255)
end 
end

local tween = game:GetService("TweenService")
local tweeninfo = TweenInfo.new
local input = game:GetService("UserInputService")
local run = game:GetService("RunService")
local plr = game.Players.LocalPlayer
local mouse = plr:GetMouse()

local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")

local function MakeDraggable(topbarobject, object)
	local Dragging = nil
	local DragInput = nil
	local DragStart = nil
	local StartPosition = nil

	local function Update(input)
		local Delta = input.Position - DragStart
		local pos = UDim2.new(StartPosition.X.Scale, StartPosition.X.Offset + Delta.X, StartPosition.Y.Scale, StartPosition.Y.Offset + Delta.Y)
		local Tween = TweenService:Create(object, TweenInfo.new(0.15), {Position = pos})
		Tween:Play()
	end

	topbarobject.InputBegan:Connect(
		function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				DragStart = input.Position
				StartPosition = object.Position

				input.Changed:Connect(
					function()
						if input.UserInputState == Enum.UserInputState.End then
							Dragging = false
						end
					end
				)
			end
		end
	)

	topbarobject.InputChanged:Connect(
		function(input)
			if
				input.UserInputType == Enum.UserInputType.MouseMovement or
				input.UserInputType == Enum.UserInputType.Touch
			then
				DragInput = input
			end
		end
	)

	UserInputService.InputChanged:Connect(
		function(input)
			if input == DragInput and Dragging then
				Update(input)
			end
		end
	)
end

local Update = {}

function Update:AddWindow(name,logo,keybind)
	local uihide = false
	local abc = false
	local logo = logo or 0
	local currentpage = ""
	local keybind = keybind or Enum.KeyCode.RightControl
	local yoo = string.gsub(tostring(keybind),"Enum.KeyCode.","")
	
	local RebornXerHub = Instance.new("ScreenGui")
	RebornXerHub.Name = "ReBornxerHubGui"
	RebornXerHub.Parent = game.CoreGui
	RebornXerHub.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

local osfunc = {}
 local osfunc2 = {}
	local Main = Instance.new("Frame")
	local WindowStrokemain = Instance.new("UIStroke")
	Main.Name = "Main"
	Main.Parent = RebornXerHub
	Main.ClipsDescendants = true
	Main.AnchorPoint = Vector2.new(0.5,0.5)
	Main.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	Main.Position = UDim2.new(0.5, 0, 0.5, 0)
	Main.Size = UDim2.new(0, 0, 0, 0)
	
	WindowStrokemain.Name = "WindowStroke"
 WindowStrokemain.Parent = Main
 WindowStrokemain.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 WindowStrokemain.Color = Color3.fromRGB(255,255,255)
 WindowStrokemain.LineJoinMode = Enum.LineJoinMode.Round
 WindowStrokemain.Thickness = 1
 WindowStrokemain.Transparency = 0
 WindowStrokemain.Enabled = true
 WindowStrokemain.Archivable = true
	
	Main:TweenSize(UDim2.new(0, 600, 0, 400),"Out","Quad",0,true)

	local MCNR = Instance.new("UICorner")
	MCNR.Name = "MCNR"
	MCNR.Parent = Main

	local Top = Instance.new("Frame")
	Top.Name = "Top"
	Top.Position = UDim2.new(0,0,0,4)
	Top.Parent = Main
	Top.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
	Top.Size = UDim2.new(0, 560, 0, 28)



	local Logo = Instance.new("ImageLabel")
	Logo.Name = "Logo"
	Logo.Parent = Top
	Logo.BackgroundColor3 = Color3.fromRGB(255,255,255)
	Logo.BackgroundTransparency = 1.000
	Logo.Position = UDim2.new(0, 13, 0, 1)
	Logo.Size = UDim2.new(0, 30, 0, 25)
	Logo.Image = "rbxassetid://"..tostring(logo)

	local Name = Instance.new("TextLabel")
	Name.Name = "Name"
	Name.Parent = Top
	Name.BackgroundColor3 = Color3.fromRGB(0,255,255)
	Name.BackgroundTransparency = 1.000
	Name.Position = UDim2.new(0.1, 0, 0, 0)
	Name.Size = UDim2.new(0, 80, 0, 27)
	Name.Font = Enum.Font.Code
	Name.RichText = true;
	Name.Text = name
	Name.TextColor3 = Color3.fromRGB(225, 225, 225)
	Name.TextSize = 15.000

local LocalizationService = game:GetService("LocalizationService")
 local Players = game:GetService("Players")
 local player = Players.LocalPlayer
 local name = player.Name
 local result, code = pcall(function()
	 return LocalizationService:GetCountryRegionForPlayerAsync(player)
 end)
 
function osfunc:Refresh(textadd)
 ServerTime.Text = textadd
 end
 function osfunc2:Refresh(textadd2)
 ServerDate.Text = textadd2
 end

 
local ListNof = Instance.new("Frame")
	local NofList = Instance.new("UIListLayout")

	ListNof.Name = "ListNof"
	ListNof.Parent = RebornXerHub
	ListNof.BackgroundColor3 = Color3.fromRGB(255,255,255)
	ListNof.BackgroundTransparency = 1.000
	ListNof.Position = UDim2.new(0.778017223, 0, -0.00217864919, 0)
	ListNof.Size = UDim2.new(0, 206, 0, 400)

	NofList.Name = "NofList"
	NofList.Parent = ListNof
	NofList.SortOrder = Enum.SortOrder.LayoutOrder
	NofList.VerticalAlignment = Enum.VerticalAlignment.Top
	
	function Update:Nof(txt,tine)
		spawn(function()
			local Nof1 = Instance.new("Frame")
			local Nof2 = Instance.new("Frame")
			local Nof3 = Instance.new("Frame")
			local NofLabel = Instance.new("TextLabel")
			local slidenof = Instance.new("Frame")
			local Slide2 = Instance.new("Frame")

			Nof1.Name = "Nof1"
			Nof1.Parent = ListNof
			Nof1.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Nof1.BackgroundTransparency = 1.000
			Nof1.BorderSizePixel = 0
			Nof1.Size = UDim2.new(0, 206, 0, 83)

			Nof2.Name = "Nof2"
			Nof2.Parent = Nof1
			Nof2.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
			Nof2.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Nof2.Position = UDim2.new(0, 0, 0.0120481923, 0)
			Nof2.Size = UDim2.new(0, 189, 0, 65)
			Instance.new("UICorner",Nof2)
			Instance.new("UICorner",slidenof)
			Instance.new("UICorner",Slide2)


			Nof3.Name = "Nof3"
			Nof3.Parent = Nof1
			Nof3.BackgroundColor3 = Color3.fromRGB(90, 90, 255)
			Nof3.BackgroundTransparency = 1
			Nof3.BorderSizePixel = 0
			Nof3.Position = UDim2.new(0, 0, 0.638554215, 0)
			Nof3.Size = UDim2.new(0, 189, 0, 7)

			NofLabel.Name = "NofLabel"
			NofLabel.Parent = Nof1
			NofLabel.BackgroundColor3 = Color3.fromRGB(51,255,255)
			NofLabel.BackgroundTransparency = 1.000
			NofLabel.BorderSizePixel = 0
			NofLabel.Position = UDim2.new(0, 0, 0.00463949936, 0)
			NofLabel.Size = UDim2.new(0, 188, 0, 52)
			NofLabel.ZIndex = 4
			NofLabel.Font = Enum.Font.Code
			NofLabel.TextColor3 = main_color or Color3.fromRGB(51,255,255)
			NofLabel.TextScaled = false
			NofLabel.TextSize = 18.000
			NofLabel.TextStrokeTransparency = 0.100
			NofLabel.TextTransparency = 0.100
			NofLabel.TextWrapped = true
			NofLabel.Text = txt or ""

			slidenof.Name = "slidenof"
			slidenof.Parent = Nof1
			slidenof.BackgroundColor3 = Color3.fromRGB(100, 100, 255)
			slidenof.BorderSizePixel = 0
			slidenof.Position = UDim2.new(0, 0, 0.638554215, 0)
			slidenof.Size = UDim2.new(0, 189, 0, 7)

			Slide2.Name = "Slide2"
			Slide2.Parent = Nof1
			Slide2.BorderSizePixel = 0
			Slide2.BackgroundColor3 = main_color or Color3.fromRGB(51,255,255)
			Slide2.BorderColor3 = Color3.fromRGB(0, 0, 0)
			Slide2.Position = UDim2.new(0, 0, 0.0120481923, 0)
			Slide2.Size = UDim2.new(0, 0, 0, 65)
			Slide2.ZIndex = 15
			Slide2.Visible = false

			tween:Create(slidenof,tweeninfo(tine or 2),{Size = UDim2.new(0, 0, 0, 7)}):Play()
			wait(tine or 2)
			Slide2.Visible = true
			tween:Create(Slide2,tweeninfo(0.2),{Size = UDim2.new(0, 190, 0, 65)}):Play()
			wait(0.2)
			tween:Create(Slide2,tweeninfo(0.2),{Size = UDim2.new(0, 0, 0, 65)}):Play()
			tween:Create(Nof3,tweeninfo(0.2),{Size = UDim2.new(0, 0, 0, 7)}):Play()
			tween:Create(NofLabel,tweeninfo(0.2),{Size = UDim2.new(0, 0, 0, 52)}):Play()
			tween:Create(Nof2,tweeninfo(0.2),{Size = UDim2.new(0, 0, 0, 65)}):Play()
			wait(0.2)
			Nof2.Visible = false
			game.Debris:AddItem(Nof1,0)
		end)
	end

 
 function Update:AddNotification(textdesc)
 local NotificationFrame = Instance.new("Frame")
 local OkayBtn = Instance.new("TextButton")
 local OkayBtnCorner = Instance.new("UICorner")
 local OkayBtnTitle = Instance.new("TextLabel")
 local NotificationTitle = Instance.new("TextLabel")
 local NotificationDesc = Instance.new("TextLabel")
 local NotifCorner = Instance.new("UICorner")
 local NotifHolderUIStroke = Instance.new("UIStroke")
 local Line = Instance.new("Frame")
 

 
 
 
 NotificationFrame.Name = "NotificationFrame"
 NotificationFrame.Parent = RebornXerHub
 NotificationFrame.AnchorPoint = Vector2.new(0.5, 0.5)
 NotificationFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
 NotificationFrame.BorderColor3 = SectionColor
 NotificationFrame.BorderSizePixel = 0
 NotificationFrame.ClipsDescendants = true
 NotificationFrame.Position = UDim2.new(0, 1200, 0, 20)
 NotificationFrame.Size = UDim2.new(0, 0, 0, 0)		
 
 NotificationFrame:TweenSize(UDim2.new(0, 200, 0, 100), Enum.EasingDirection.Out, Enum.EasingStyle.Quart, .6, true)
 
 NotifCorner.Name = "NotifCorner"
 NotifCorner.Parent = NotificationFrame
 NotifCorner.CornerRadius = UDim.new(0, 5)
 
 NotifHolderUIStroke.Name = "NotifHolderUIStroke"
 NotifHolderUIStroke.Parent = NotificationFrame
 NotifHolderUIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 NotifHolderUIStroke.Color = SectionColor
 NotifHolderUIStroke.LineJoinMode = Enum.LineJoinMode.Round
 NotifHolderUIStroke.Thickness = 1
 NotifHolderUIStroke.Transparency = 0
 NotifHolderUIStroke.Enabled = true
 NotifHolderUIStroke.Archivable = true
 
 OkayBtn.Name = "OkayBtn"
 OkayBtn.Parent = NotificationFrame
 OkayBtn.BackgroundColor3 = Color3.fromRGB(190, 190, 190)
 OkayBtn.BorderSizePixel = 1
 OkayBtn.BorderColor3 = SectionColor
 OkayBtn.Position = UDim2.new(0, 180, 0, 5)
 OkayBtn.Size = UDim2.new(0, 20, 0, 20)
 OkayBtn.AutoButtonColor = true
 OkayBtn.Font = Enum.Font.SourceSans
 OkayBtn.Text = "X"
 OkayBtn.TextColor3 = Color3.fromRGB(255, 0, 0)
 OkayBtn.TextSize = 22.000
 
 OkayBtnCorner.CornerRadius = UDim.new(0, 5)
 OkayBtnCorner.Name = "OkayBtnCorner"
 OkayBtnCorner.Parent = OkayBtn
 
 OkayBtnTitle.Name = "OkayBtnTitle"
 OkayBtnTitle.Parent = OkayBtn
 OkayBtnTitle.BackgroundColor3 = SectionColor
 OkayBtnTitle.BackgroundTransparency = 1.000
 OkayBtnTitle.Size = UDim2.new(0, 15, 0, 15)
 OkayBtnTitle.Text = ""
 OkayBtnTitle.Font = Enum.Font.Code
 OkayBtnTitle.TextColor3 = Color3.fromRGB(0, 0, 0)
 OkayBtnTitle.TextSize = 22.000
 
 NotificationTitle.Name = "NotificationTitle"
 NotificationTitle.Parent = NotificationFrame
 NotificationTitle.BackgroundColor3 = SectionColor
 NotificationTitle.BackgroundTransparency = 1.000
 NotificationTitle.Position = UDim2.new(0, 0, 0, 10)
 NotificationTitle.Size = UDim2.new(0, 200, 0, 25)
 NotificationTitle.ZIndex = 3
 NotificationTitle.Font = Enum.Font.Code
 NotificationTitle.Text = "Notification"
 NotificationTitle.TextColor3 = Color3.fromRGB(50, 255, 255)
 NotificationTitle.TextSize = 22.000
 
 Line.Name = "Line"
 Line.Parent = NotificationFrame
 Line.BackgroundColor3 = SectionColor
 Line.BorderSizePixel = 0
 Line.Position = UDim2.new(0, 0, 0, 40)
 Line.Size = UDim2.new(0, 200, 0, 1)
 
 NotificationDesc.Name = "NotificationDesc"
 NotificationDesc.Parent = NotificationFrame
 NotificationDesc.BackgroundColor3 = SectionColor
 NotificationDesc.BackgroundTransparency = 1.000
 NotificationDesc.Position = UDim2.new(0, 10, 0, 50)
 NotificationDesc.Size = UDim2.new(0, 200, 0, 100)
 NotificationDesc.Font = Enum.Font.Code
 NotificationDesc.Text = textdesc
NotificationDesc.TextScaled = false
 NotificationDesc.TextColor3 = SectionTextColor
 NotificationDesc.TextSize = 16.000
 NotificationDesc.TextWrapped = true
 NotificationDesc.TextXAlignment = Enum.TextXAlignment.Center
 NotificationDesc.TextYAlignment = Enum.TextYAlignment.Top
 
 OkayBtn.MouseEnter:Connect(function()
TweenService:Create(OkayBtn, TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundColor3 = Color3.fromRGB(30, 30, 30)}):Play()
 end)
 
 OkayBtn.MouseLeave:Connect(function()
TweenService:Create(OkayBtn, TweenInfo.new(.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundColor3 = Color3.fromRGB(25, 25, 25)}):Play()
 end)
 
 OkayBtn.MouseButton1Click:Connect(function()
NotificationFrame:TweenSize(UDim2.new(0, 0, 0, 0), Enum.EasingDirection.Out, Enum.EasingStyle.Quart, .6, true)
 
wait(0.4)
 
TweenService:Create(NotificationHold, TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {BackgroundTransparency = 1}):Play()
 
wait(.3)
 
NotificationHold:Destroy()
 end)
 end


local Tab = Instance.new("ImageLabel")
local WindowStrokelol = Instance.new("UIStroke")
 Tab.Name = "Tab"
 Tab.Parent = Top
 Tab.BackgroundColor3 = Color3.fromRGB(42, 42, 42)
 Tab.ImageTransparency = 1
 Tab.Position = UDim2.new(0, 160, 0, -2)
 Tab.Size = UDim2.new(0, 410, 0, 29)
 Tab.Image = "rbxassetid://6675147486"
 
 WindowStrokelol.Name = "WindowStroke"
 WindowStrokelol.Parent = Tab
 WindowStrokelol.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 WindowStrokelol.Color = Color3.fromRGB(255,255,255)
 WindowStrokelol.LineJoinMode = Enum.LineJoinMode.Round
 WindowStrokelol.Thickness = 1
 WindowStrokelol.Transparency = 0
 WindowStrokelol.Enabled = true
 WindowStrokelol.Archivable = true
 
 local TCNR = Instance.new("UICorner")
 TCNR.Name = "TCNR"
 TCNR.Parent = Tab
 
 local ScrollTab = Instance.new("ScrollingFrame")
 ScrollTab.Name = "ScrollTab"
 ScrollTab.Parent = Tab
 ScrollTab.Active = true
 ScrollTab.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
 ScrollTab.BackgroundTransparency = 0
 ScrollTab.Size = UDim2.new(0, 433, 0, 29)
 ScrollTab.CanvasSize = UDim2.new(0, 0, 0, 0)
 ScrollTab.ScrollBarThickness = 0
 
 local PLL = Instance.new("UIListLayout")
 PLL.Name = "PLL"
 PLL.Parent = ScrollTab
 PLL.FillDirection = Enum.FillDirection.Horizontal
 PLL.SortOrder = Enum.SortOrder.LayoutOrder
 PLL.Padding = UDim.new(0)
 
 local PPD = Instance.new("UIPadding")
 PPD.Name = "PPD"
 PPD.Parent = ScrollTab
 PPD.PaddingLeft = UDim.new(0.01)
 
 local Page = Instance.new("Frame")
 local WindowStrokeshit = Instance.new("UIStroke")
 Page.Name = "Page"
 Page.Parent = Main
 Page.BackgroundColor3 = Color3.fromRGB(42, 42, 42)
 Page.BackgroundTransparency = 1
 Page.Position = UDim2.new(0, 1, 0.100000003, -5)
 Page.Size = UDim2.new(0, 300, 0, 380)
 
 WindowStrokeshit.Name = "WindowStroke"
 WindowStrokeshit.Parent = Page
 WindowStrokeshit.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 WindowStrokeshit.Color = Color3.fromRGB(255,255,255)
 WindowStrokeshit.LineJoinMode = Enum.LineJoinMode.Round
 WindowStrokeshit.Thickness = 1
 WindowStrokeshit.Transparency = 0
 WindowStrokeshit.Archivable = false
 WindowStrokeshit.Enabled = true
 
 local lolshit = Instance.new("UICorner")
 
 lolshit.Parent = Top1
 
 
 local PCNR = Instance.new("UICorner")
 PCNR.Name = "PCNR"
 PCNR.Parent = Page
 
 local MainPage = Instance.new("Frame")
 MainPage.Name = "MainPage"
 MainPage.Parent = Page
 MainPage.ClipsDescendants = true
 MainPage.BackgroundColor3 = Color3.fromRGB(255,255,255)
 MainPage.BackgroundTransparency = 1.000
 MainPage.Size = UDim2.new(0, 300, 0, 380)
 
 local PageList = Instance.new("Folder")
 PageList.Name = "PageList"
 PageList.Parent = MainPage
 
 local UIPageLayout = Instance.new("UIPageLayout")
 
 UIPageLayout.Parent = PageList
 UIPageLayout.SortOrder = Enum.SortOrder.LayoutOrder
 UIPageLayout.EasingDirection = Enum.EasingDirection.InOut
 UIPageLayout.EasingStyle = Enum.EasingStyle.Quad
 UIPageLayout.FillDirection = Enum.FillDirection.Vertical
 UIPageLayout.Padding = UDim.new(0, 15)
 UIPageLayout.TweenTime = 0.400
 UIPageLayout.GamepadInputEnabled = false
 UIPageLayout.ScrollWheelInputEnabled = false
 UIPageLayout.TouchInputEnabled = false

local Page2 = Instance.new("Frame")
 local WindowStrokeshit2 = Instance.new("UIStroke")
 Page2.Name = "Page2"
 Page2.Parent = Main
 Page2.BackgroundColor3 = Color3.fromRGB(42, 42, 42)
 Page2.BackgroundTransparency = 1
 Page2.Position = UDim2.new(0, 302, 0.100000003, -5)
 Page2.Size = UDim2.new(0, 300, 0, 378)
 
 WindowStrokeshit2.Name = "WindowStroke"
 WindowStrokeshit2.Parent = Page2
 WindowStrokeshit2.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 WindowStrokeshit2.Color = Color3.fromRGB(255,255,255)
 WindowStrokeshit2.LineJoinMode = Enum.LineJoinMode.Round
 WindowStrokeshit2.Thickness = 1
 WindowStrokeshit2.Transparency = 0
 WindowStrokeshit2.Archivable = false
 WindowStrokeshit2.Enabled = true
 
 local lolshit2 = Instance.new("UICorner")
 
 lolshit2.Parent = Top1
 
 
 local PCNR2 = Instance.new("UICorner")
 PCNR2.Name = "PCNR"
 PCNR2.Parent = Page2
 
 local MainPage2 = Instance.new("Frame")
 MainPage2.Name = "MainPage"
 MainPage2.Parent = Page2
 MainPage2.ClipsDescendants = true
 MainPage2.BackgroundColor3 = Color3.fromRGB(255,255,255)
 MainPage2.BackgroundTransparency = 1.000
 MainPage2.Size = UDim2.new(0, 300, 0, 378)
 
 local PageList2 = Instance.new("Folder")
 PageList2.Name = "PageList"
 PageList2.Parent = MainPage2
 
 local UIPageLayout2 = Instance.new("UIPageLayout")
 
 UIPageLayout2.Parent = PageList2
 UIPageLayout2.SortOrder = Enum.SortOrder.LayoutOrder
 UIPageLayout2.EasingDirection = Enum.EasingDirection.InOut
 UIPageLayout2.EasingStyle = Enum.EasingStyle.Quad
 UIPageLayout2.FillDirection = Enum.FillDirection.Vertical
 UIPageLayout2.Padding = UDim.new(0, 15)
 UIPageLayout2.TweenTime = 0.400
 UIPageLayout2.GamepadInputEnabled = false
 UIPageLayout2.ScrollWheelInputEnabled = false
 UIPageLayout2.TouchInputEnabled = false
 
 MakeDraggable(Top,Main)
 UserInputService.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode[yoo] then
    if uihide == false then
     uihide = true
     Main:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0,true)
    else
     uihide = false
     Main:TweenSize(UDim2.new(0, 600, 0, 400),"Out","Quad",0,true)
    end
    end
     end)
	


 
	local uitab = {}
	
	function uitab:AddTab(text, img)
		local TabButton = Instance.new("TextButton")
		local TabImage = Instance.new("ImageLabel")
		local WindowStroke = Instance.new("UIStroke")
		local Label3 = Instance.new("TextLabel")
		local LabelTitle = Instance.new("TextLabel")
local LabelTitle = Instance.new("TextLabel")

		TabButton.Parent = ScrollTab
		TabButton.Name = text.."Server"
		TabButton.Text = text
		TabButton.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
		TabButton.BackgroundTransparency = 0.1
		TabButton.Position = UDim2.new(0, 2, 0, 0)
		TabButton.Size = UDim2.new(0, 100, 0, 28)
		TabButton.Font = Enum.Font.Code
		TabButton.TextColor3 = Color3.fromRGB(255, 225, 225)
		TabButton.TextSize = 12.000
		TabButton.TextTransparency = 0
		
		
local MCNR1 = Instance.new("UICorner")
	MCNR1.Name = "MCNR"
	MCNR1.Parent = TabButton

WindowStroke.Name = "WindowStroke"
 WindowStroke.Parent = TabButton
 WindowStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 WindowStroke.Color = Color3.fromRGB(45,45,45)
 WindowStroke.LineJoinMode = Enum.LineJoinMode.Round
 WindowStroke.Thickness = 1
 WindowStroke.Transparency = 0
 WindowStroke.Enabled = true
 WindowStroke.Archivable = true

		local MainFramePage = Instance.new("ScrollingFrame")
		MainFramePage.Name = text.."_Page"
		MainFramePage.Parent = PageList
		MainFramePage.Active = true
		MainFramePage.BackgroundColor3 = Color3.fromRGB(51,255,255)
		MainFramePage.BackgroundTransparency = 1.000
		MainFramePage.BorderSizePixel = 1
		MainFramePage.Size = UDim2.new(0, 390, 0, 370)
		MainFramePage.CanvasSize = UDim2.new(0, 0, 0, 0)
		MainFramePage.ScrollBarThickness = 0
		

		
		local UIPadding = Instance.new("UIPadding")
		local UIListLayout = Instance.new("UIListLayout")
		
		UIPadding.Parent = MainFramePage
		UIPadding.PaddingLeft = UDim.new(0, 10)
		UIPadding.PaddingTop = UDim.new(0, 10)

		UIListLayout.Padding = UDim.new(0,4)
		UIListLayout.Parent = MainFramePage
		UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		
		TabButton.MouseButton1Click:Connect(function()
        Sound = Instance.new("Sound", game:GetService("Workspace")) -- ตรงนี้ไม่ต้องไปสน นาจา ;0;
Sound.Name = "Notify" -- ชื่อเสียง \;
Sound.SoundId = "rbxassetid://903267862" -- เลขขขขขเสียง ;/
Sound.Looped = false -- วนลูป :>
Sound.Playing = true -- เล่นเสียง :<
Sound.Volume = 1 -- ระดับเสียงงงงงงง ;-;
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			for i,v in next, PageList:GetChildren() do
				currentpage = string.gsub(TabButton.Name,"Server","").."_Page"
				if v.Name == currentpage then
					UIPageLayout:JumpTo(v)
				end
			end
		end)

		if abc == false then
            
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			UIPageLayout:JumpToIndex(0)
			abc = true
		end
		
		game:GetService("RunService").Stepped:Connect(function()
			pcall(function()
				MainFramePage.CanvasSize = UDim2.new(0,0,0,UIListLayout.AbsoluteContentSize.Y + 20)
				ScrollTab.CanvasSize = UDim2.new(0,PLL.AbsoluteContentSize.X + 20,0,0)
			end)
		end)
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()
 
	 
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()
	
	
	local MainFramePage2 = Instance.new("ScrollingFrame")
		MainFramePage2.Name = text.."_Page"
		MainFramePage2.Parent = PageList2
		MainFramePage2.Active = true
		MainFramePage2.BackgroundColor3 = Color3.fromRGB(51,255,255)
		MainFramePage2.BackgroundTransparency = 1.000
		MainFramePage2.BorderSizePixel = 0
		MainFramePage2.Size = UDim2.new(0, 320, 0, 370)
		MainFramePage2.CanvasSize = UDim2.new(0, 0, 0, 0)
		MainFramePage2.ScrollBarThickness = 0
		
		local UIPadding2 = Instance.new("UIPadding")
		local UIListLayout2 = Instance.new("UIListLayout")
		
		UIPadding2.Parent = MainFramePage2
		UIPadding2.PaddingLeft = UDim.new(0, 10)
		UIPadding2.PaddingTop = UDim.new(0, 10)

		UIListLayout2.Padding = UDim.new(0,4)
		UIListLayout2.Parent = MainFramePage2
		UIListLayout2.SortOrder = Enum.SortOrder.LayoutOrder
		
		TabButton.MouseButton1Click:Connect(function()
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			for i,v in next, PageList2:GetChildren() do
				currentpage = string.gsub(TabButton.Name,"Server","").."_Page"
				if v.Name == currentpage then
					UIPageLayout2:JumpTo(v)
				end
			end
		end)

		if abc == false then
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			UIPageLayout2:JumpToIndex(0)
			abc = true
		end
		
		game:GetService("RunService").Stepped:Connect(function()
			pcall(function()
				MainFramePage2.CanvasSize = UDim2.new(0,0,0,UIListLayout2.AbsoluteContentSize.Y + 20)
				ScrollTab.CanvasSize = UDim2.new(0,PLL.AbsoluteContentSize.X + 20,0,0)
			end)
		end)
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()
 
	 
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()
	local abcd = false
	 function uitab:AddTabH(text,img)
	 local mainDiscord = Instance.new("ImageButton")

	 mainDiscord.Name = "mainDiscord"
    mainDiscord.Parent = Top
    mainDiscord.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    mainDiscord.BackgroundTransparency = 1.000
    mainDiscord.Position = UDim2.new(0, 565, 0, 0)
    mainDiscord.Size = UDim2.new(0, 30, 0, 30)
    mainDiscord.Image = "rbxassetid://"..tostring(img)
    mainDiscord.ImageColor3 = Color3.fromRGB(200, 200, 200)
    
        local MainFramePage = Instance.new("ScrollingFrame")
		MainFramePage.Name = text.."_Page"
		MainFramePage.Parent = PageList
		MainFramePage.Active = true
		MainFramePage.BackgroundColor3 = Color3.fromRGB(51,255,255)
		MainFramePage.BackgroundTransparency = 1.000
		MainFramePage.BorderSizePixel = 1
		MainFramePage.Size = UDim2.new(0, 390, 0, 370)
		MainFramePage.CanvasSize = UDim2.new(0, 0, 0, 0)
		MainFramePage.ScrollBarThickness = 0
		

		
		local UIPadding = Instance.new("UIPadding")
		local UIListLayout = Instance.new("UIListLayout")
		
		UIPadding.Parent = MainFramePage
		UIPadding.PaddingLeft = UDim.new(0, 10)
		UIPadding.PaddingTop = UDim.new(0, 10)

		UIListLayout.Padding = UDim.new(0,4)
		UIListLayout.Parent = MainFramePage
		UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		
		mainDiscord.MouseButton1Click:Connect(function()
        Sound = Instance.new("Sound", game:GetService("Workspace")) -- ตรงนี้ไม่ต้องไปสน นาจา ;0;
Sound.Name = "Notify" -- ชื่อเสียง \;
Sound.SoundId = "rbxassetid://3020841054" -- เลขขขขขเสียง ;/
Sound.Looped = false -- วนลูป :>
Sound.Playing = true -- เล่นเสียง :<
Sound.Volume = 1 -- ระดับเสียงงงงงงง ;-;
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			for i,v in next, PageList:GetChildren() do
				currentpage2 = string.gsub(TabButton.Name,"Server","").."_Page"
				if v.Name == currentpage2 then
					UIPageLayout:JumpTo(v)
				end
			end
		end)

		if abc == false then
            
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			UIPageLayout:JumpToIndex(0)
			abc = true
		end
		
		game:GetService("RunService").Stepped:Connect(function()
			pcall(function()
				MainFramePage.CanvasSize = UDim2.new(0,0,0,UIListLayout.AbsoluteContentSize.Y + 20)
				ScrollTab.CanvasSize = UDim2.new(0,PLL.AbsoluteContentSize.X + 20,0,0)
			end)
		end)
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()
 
	 
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()
	
	
	local MainFramePage2 = Instance.new("ScrollingFrame")
		MainFramePage2.Name = text.."_Page"
		MainFramePage2.Parent = PageList2
		MainFramePage2.Active = true
		MainFramePage2.BackgroundColor3 = Color3.fromRGB(51,255,255)
		MainFramePage2.BackgroundTransparency = 1.000
		MainFramePage2.BorderSizePixel = 0
		MainFramePage2.Size = UDim2.new(0, 320, 0, 370)
		MainFramePage2.CanvasSize = UDim2.new(0, 0, 0, 0)
		MainFramePage2.ScrollBarThickness = 0
		
		local UIPadding2 = Instance.new("UIPadding")
		local UIListLayout2 = Instance.new("UIListLayout")
		
		UIPadding2.Parent = MainFramePage2
		UIPadding2.PaddingLeft = UDim.new(0, 10)
		UIPadding2.PaddingTop = UDim.new(0, 10)

		UIListLayout2.Padding = UDim.new(0,4)
		UIListLayout2.Parent = MainFramePage2
		UIListLayout2.SortOrder = Enum.SortOrder.LayoutOrder
		
		mainDiscord.MouseButton1Click:Connect(function()
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			for i,v in next, PageList2:GetChildren() do
				currentpage2 = string.gsub(TabButton.Name,"Server","").."_Page"
				if v.Name == currentpage2 then
					UIPageLayout2:JumpTo(v)
				end
			end
		end)

		if abc == false then
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end
				TweenService:Create(
					mainDiscord,
					TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			UIPageLayout2:JumpToIndex(0)
			abc = true
		end
		
		game:GetService("RunService").Stepped:Connect(function()
			pcall(function()
				MainFramePage2.CanvasSize = UDim2.new(0,0,0,UIListLayout2.AbsoluteContentSize.Y + 20)
				ScrollTab.CanvasSize = UDim2.new(0,PLL.AbsoluteContentSize.X + 20,0,0)
			end)
		end)
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()

 
	 
 
 coroutine.wrap(function()
 while wait() do
 end
 end)()
	end
	
		local main = {}
		function main:AddButtonRight(text,callback)
			local Button2 = Instance.new("Frame")
			local UICorner2 = Instance.new("UICorner")
			local TextBtn2 = Instance.new("TextButton")
			local UICorner_1 = Instance.new("UICorner")
			local Black2 = Instance.new("Frame")
			local UICorner_2 = Instance.new("UICorner")
			
			Button2.Name = "Button"
			Button2.Parent = MainFramePage2
			Button2.BackgroundColor3 = Color
			Button2.Size = UDim2.new(0, 280, 0, 28)
			
			UICorner2.CornerRadius = UDim.new(0, 5)
			UICorner2.Parent = Button2
			
			TextBtn2.Name = "TextBtn"
			TextBtn2.Parent = Button2
			TextBtn2.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			TextBtn2.Position = UDim2.new(0, 1, 0, 1)
			TextBtn2.Size = UDim2.new(0, 278, 0, 26)
			TextBtn2.AutoButtonColor = false
			TextBtn2.Font = Enum.Font.Code
			TextBtn2.Text = text
			TextBtn2.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextBtn2.TextSize = 12.000
			
			UICorner_1.CornerRadius = UDim.new(0, 5)
			UICorner_1.Parent = TextBtn2
			
			Black2.Name = "Black"
			Black2.Parent = Button2
			Black2.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
			Black2.BackgroundTransparency = 1.000
			Black2.BorderSizePixel = 0
			Black2.Position = UDim2.new(0, 1, 0, 1)
			Black2.Size = UDim2.new(0, 280, 0, 26)
			
			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = Black2

			TextBtn2.MouseEnter:Connect(function()
				TweenService:Create(
					Black2,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 0.7}
				):Play()
			end)
			TextBtn2.MouseLeave:Connect(function()
				TweenService:Create(
					Black2,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 1}
				):Play()
			end)
			TextBtn2.MouseButton1Click:Connect(function()
				TextBtn2.TextSize = 0
				TweenService:Create(
					TextBtn2,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextSize = 12}
				):Play()
				callback()
			end)
		end
		
		function main:AddButtonLeft(text,callback)
			local Button = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local TextBtn = Instance.new("TextButton")
			local UICorner_2 = Instance.new("UICorner")
			local Black = Instance.new("Frame")
			local UICorner_3 = Instance.new("UICorner")
			
			Button.Name = "Button"
			Button.Parent = MainFramePage
			Button.BackgroundColor3 = Color
			Button.Size = UDim2.new(0, 280, 0, 28)
			
			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Button
			
			TextBtn.Name = "TextBtn"
			TextBtn.Parent = Button
			TextBtn.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			TextBtn.Position = UDim2.new(0, 1, 0, 1)
			TextBtn.Size = UDim2.new(0, 278, 0, 26)
			TextBtn.AutoButtonColor = false
			TextBtn.Font = Enum.Font.Code
			TextBtn.Text = text
			TextBtn.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextBtn.TextSize = 12.000
			
			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = TextBtn
			
			Black.Name = "Black"
			Black.Parent = Button
			Black.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
			Black.BackgroundTransparency = 1.000
			Black.BorderSizePixel = 0
			Black.Position = UDim2.new(0, 1, 0, 1)
			Black.Size = UDim2.new(0, 280, 0, 26)
			
			UICorner_3.CornerRadius = UDim.new(0, 5)
			UICorner_3.Parent = Black

			TextBtn.MouseEnter:Connect(function()
				TweenService:Create(
					Black,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 0.7}
				):Play()
			end)
			TextBtn.MouseLeave:Connect(function()
				TweenService:Create(
					Black,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 1}
				):Play()
			end)
			TextBtn.MouseButton1Click:Connect(function()
				TextBtn.TextSize = 0
				TweenService:Create(
					TextBtn,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextSize = 12}
				):Play()
				callback()
			end)
		end
		function main:AddToggleLeft(text,config,callback)
			config = config or false
			local toggled = config
			local Toggle = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
		local Button = Instance.new("TextButton")
		local True = Instance.new("TextLabel")
			local UICorner_2 = Instance.new("UICorner")
			local Label = Instance.new("TextLabel")
			local ToggleImage = Instance.new("Frame")
			local UICorner_3 = Instance.new("UICorner")
			local Circle = Instance.new("ImageLabel")
			local UICorner_4 = Instance.new("UICorner")
local ImageLabel = Instance.new("ImageLabel")
local Space = Instance.new("TextLabel")

			Toggle.Name = "Toggle"
			Toggle.Parent = MainFramePage
			Toggle.BackgroundColor3 = Color
			Toggle.Size = UDim2.new(0, 280, 0, 28)

			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Toggle

			Button.Name = "Button"
			Button.Parent = Toggle
			Button.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			Button.Position = UDim2.new(0, 1, 0, 1)
			Button.Size = UDim2.new(0, 278, 0, 26)
			Button.AutoButtonColor = false
			Button.Font = Enum.Font.SourceSans
			Button.Text = ""
			Button.TextColor3 = Color3.fromRGB(0, 0, 0)
			Button.TextSize = 11.000

			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = Button

			Label.Name = "Label"
			Label.Parent = Toggle
			Label.BackgroundColor3 = Color3.fromRGB(0,255,255)
			Label.BackgroundTransparency = 1.000
			Label.Position = UDim2.new(0, 1, 0, 1)
			Label.Size = UDim2.new(0, 278, 0, 26)
			Label.Font = Enum.Font.Code
			Label.Text = text
			Label.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label.TextSize = 12.000
			

        ToggleImage.Name = "ToggleImage"
			ToggleImage.Parent = Toggle
			ToggleImage.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
			ToggleImage.Position = UDim2.new(0, 250, 0, 4)
			ToggleImage.Size = UDim2.new(0, 22, 0, 20)

			UICorner_3.CornerRadius = UDim.new(0, 4)
			UICorner_3.Parent = ToggleImage

			Circle.Name = "Circle"
			Circle.Parent = ToggleImage
			Circle.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			Circle.Position = UDim2.new(0, 2, 0, 2)
			Circle.Size = UDim2.new(0, 18, 0, 16)
			
			True.Name = "True"
			True.Parent = Circle
			True.BackgroundTransparency = 1.000
			True.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			True.Position = UDim2.new(0, 0, 0, 0)
			True.Size = UDim2.new(0, 18, 0, 16)
			True.Font = Enum.Font.SourceSans
			True.Text = ""
			True.TextColor3 = Color3.fromRGB(0, 0, 0)
			True.TextSize = 16.000

			UICorner_4.CornerRadius = UDim.new(0, 0)
			UICorner_4.Parent = Circle

			Button.MouseButton1Click:Connect(function()
				if toggled == false then
					toggled = true
					True.Text = "✔"
					Circle:TweenPosition(UDim2.new(0,2,0,2),"Out","Sine",0,true)
					TweenService:Create(
						Circle,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(0, 255, 0)}
					):Play()
				else
					toggled = false
					True.Text = ""
					Circle:TweenPosition(UDim2.new(0,2,0,2),"Out","Sine",0,true)
					TweenService:Create(
						Circle,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(30, 30, 30)}
					):Play()
					
				end
				pcall(callback,toggled)
			end)

			if config == true then
				toggled = true
				True.Text = "✔"
				Circle:TweenPosition(UDim2.new(0,2,0,2),"Out","Sine",0,true)
				TweenService:Create(
					Circle,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundColor3 = Color3.fromRGB(0, 255, 0)}
				):Play()
				pcall(callback,toggled)
			end
		end
		
function main:AddToggleRight(text,config,callback)
			config = config or false
			local toggledd = config
			local Togglee = Instance.new("Frame")
			local UICornerr = Instance.new("UICorner")
			local Truea =Instance.new("TextLabel")
		local Buttonn = Instance.new("TextButton")
			local UICorner_22 = Instance.new("UICorner")
			local Labell = Instance.new("TextLabel")
			local ToggleImagee = Instance.new("Frame")
			local UICorner_33 = Instance.new("UICorner")
			local Circlee = Instance.new("Frame")
			local UICorner_44 = Instance.new("UICorner")
local ImageLabell = Instance.new("ImageLabel")
local Spacee = Instance.new("TextLabel")

			Togglee.Name = "Toggle"
			Togglee.Parent = MainFramePage2
			Togglee.BackgroundColor3 = Color
			Togglee.Size = UDim2.new(0, 280, 0, 28)

			UICornerr.CornerRadius = UDim.new(0, 5)
			UICornerr.Parent = Togglee

			Buttonn.Name = "Button"
			Buttonn.Parent = Togglee
			Buttonn.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			Buttonn.Position = UDim2.new(0, 1, 0, 1)
			Buttonn.Size = UDim2.new(0, 278, 0, 26)
			Buttonn.AutoButtonColor = false
			Buttonn.Font = Enum.Font.SourceSans
			Buttonn.Text = ""
			Buttonn.TextColor3 = Color3.fromRGB(0, 0, 0)
			Buttonn.TextSize = 11.000

			UICorner_22.CornerRadius = UDim.new(0, 5)
			UICorner_22.Parent = Buttonn

			Labell.Name = "Label"
			Labell.Parent = Togglee
			Labell.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Labell.BackgroundTransparency = 1.000
			Labell.Position = UDim2.new(0, 1, 0, 1)
			Labell.Size = UDim2.new(0, 278, 0, 26)
			Labell.Font = Enum.Font.Code
			Labell.Text = text
			Labell.TextColor3 = Color3.fromRGB(225, 225, 225)
			Labell.TextSize = 12.000
			



		 ToggleImagee.Name = "ToggleImage"
			ToggleImagee.Parent = Togglee
			ToggleImagee.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
			ToggleImagee.Position = UDim2.new(0, 250, 0, 5)
			ToggleImagee.Size = UDim2.new(0, 22, 0, 20)

			UICorner_33.CornerRadius = UDim.new(0, 4)
			UICorner_33.Parent = ToggleImagee

			Circlee.Name = "Circle"
			Circlee.Parent = ToggleImagee
			Circlee.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			Circlee.Position = UDim2.new(0, 2, 0, 2)
			Circlee.Size = UDim2.new(0, 18, 0, 16)

Truea.Name = "Truea"
			Truea.Parent = Circlee
			Truea.BackgroundTransparency = 1.000
			Truea.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Truea.Position = UDim2.new(0, 0, 0, 0)
			Truea.Size = UDim2.new(0, 18, 0, 16)
			Truea.Font = Enum.Font.SourceSans
			Truea.Text = ""
			Truea.TextColor3 = Color3.fromRGB(0, 0, 0)
			Truea.TextSize = 16.000

			UICorner_44.CornerRadius = UDim.new(0, 0)
			UICorner_44.Parent = Circlee

			Buttonn.MouseButton1Click:Connect(function()
				if toggledd == false then
					toggledd = true
					Truea.Text = "✔"
					Circlee:TweenPosition(UDim2.new(0,2,0,2),"Out","Sine",0,true)
					TweenService:Create(
						Circlee,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(0, 255, 0)}
					):Play()
				else
					toggledd = false
					Truea.Text = ""
					Circlee:TweenPosition(UDim2.new(0,2,0,2),"Out","Sine",0,true)
					TweenService:Create(
						Circlee,
						TweenInfo.new(0,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(30, 30, 30)}
					):Play()
				end
				pcall(callback,toggledd)
			end)

			if config == true then
				toggledd = true
				Truea.Text = "✔"
				Circlee:TweenPosition(UDim2.new(0,2,0,2),"Out","Sine",0,true)
				TweenService:Create(
					Circlee,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundColor3 = Color3.fromRGB(0, 255, 0)}
				):Play()
				pcall(callback,toggledd)
			end
		end

		

		
		function main:AddDropdownLeft(droptitle, list, callback)
-- Local --
local dropfunc = {}
local list = list or {}
local DropToggled = false
local DropSizeFrame = Instance.new("Frame")
local Frame = Instance.new("Frame")
local UIStroke = Instance.new("UIStroke")
local DropCover = Instance.new("Frame")
local UICorner = Instance.new("UICorner")
local UICorner2 = Instance.new("UICorner")
local ImageLabel = Instance.new("ImageLabel")
local Space = Instance.new("TextLabel")
local Title = Instance.new("TextLabel")
local ImageButton = Instance.new("ImageButton")
local DropStrokeList = Instance.new("UIStroke")
local DropTextList = Instance.new("TextLabel")

-- Prop --
DropSizeFrame.Name = droptitle or "DropSizeFrame"
DropSizeFrame.Parent = MainFramePage
DropSizeFrame.BackgroundColor3 = SectionColor
DropSizeFrame.BackgroundTransparency = 1.000
DropSizeFrame.Size = UDim2.new(0, 280, 0, 60)

Frame.Name = "Frame"
Frame.Parent = DropSizeFrame
Frame.BackgroundColor3 = Color3.fromRGB(30,30,30)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0, 3, 0, 0)
Frame.Size = UDim2.new(0, 278, 0, 60)

UIStroke.Name = "UIStroke"
UIStroke.Parent = Frame
UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
UIStroke.Color = Color3.fromRGB(255,255,255)
UIStroke.LineJoinMode = Enum.LineJoinMode.Round
UIStroke.Thickness = 0.7
UIStroke.Transparency = 0
UIStroke.Enabled = true
UIStroke.Archivable = true

UICorner.Parent = Frame
UICorner.CornerRadius = UDim.new(0, 3)

DropCover.Name = "DropCover"
DropCover.Parent = Frame
DropCover.BackgroundColor3 = BackgroundItemColor
DropCover.BackgroundTransparency = 1.000
DropCover.BorderSizePixel = 0
DropCover.Position = UDim2.new(0, 0, 0, 0)
DropCover.Size = UDim2.new(0, 202, 0, 30)

ImageLabel.Name = "ImageLabel"
ImageLabel.Parent = DropCover
ImageLabel.BackgroundColor3 = SectionColor
ImageLabel.BackgroundTransparency = 1.000
ImageLabel.BorderSizePixel = 0
ImageLabel.Position = UDim2.new(0, 5, 0, 6)
ImageLabel.Size = UDim2.new(0, 18, 0, 18)
ImageLabel.Image = "rbxassetid://8825010231"
ImageLabel.ImageColor3 = Color3.fromRGB(255,255,255)

Space.Name = "Space"
Space.Parent = DropCover
Space.BackgroundColor3 = SectionColor
Space.BackgroundTransparency = 1.000
Space.Position = UDim2.new(0, 30, 0, 0)
Space.Size = UDim2.new(0, 15, 0, 30)
Space.Font = Enum.Font.Code
Space.Text = "|"
Space.TextSize = 13.000
Space.TextColor3 = Color3.fromRGB(255,255,255)
Space.TextXAlignment = Enum.TextXAlignment.Center

Title.Name = "Title"
Title.Parent = DropCover
Title.BackgroundColor3 = SectionColor
Title.BackgroundTransparency = 1.000
Title.Position = UDim2.new(0, 50, 0, 0)
Title.Size = UDim2.new(0, 207, 0, 30)
Title.Font = Enum.Font.Code
Title.Text = tostring(droptitle) or "drop Title"
Title.TextColor3 = Color3.fromRGB(255,255,255)
Title.TextSize = 12.000
Title.TextXAlignment = Enum.TextXAlignment.Left

ImageButton.Name = "ImageButton"
ImageButton.Parent = DropCover
ImageButton.BackgroundColor3 = WindowBackgroundColor
ImageButton.BackgroundTransparency = 1.000
ImageButton.Position = UDim2.new(0, 250, 0, 7)
ImageButton.Size = UDim2.new(0, 23, 0, 18)
ImageButton.Image = "rbxassetid://6583628103"
ImageButton.ImageColor3 = Color3.fromRGB(51,255,255)
ImageButton.Rotation = 180

DropTextList.Name = "DropTextList"
DropTextList.Parent = Frame
DropTextList.BackgroundColor3 = BackgroundItemColor
DropTextList.BackgroundTransparency = 1.000
DropTextList.Position = UDim2.new(0, 3, 0, 30)
DropTextList.Size = UDim2.new(0, 278, 0, 25)
DropTextList.Font = Enum.Font.Code
DropTextList.Text = v or "Select First"
DropTextList.TextColor3 = Color3.fromRGB(255,255,255)
DropTextList.TextSize = 12.000
DropTextList.TextXAlignment = Enum.TextXAlignment.Center

UICorner2.Parent = DropTextList
UICorner2.CornerRadius = UDim.new(0,0)

DropStrokeList.Name = "DropStrokeList"
DropStrokeList.Parent = DropTextList
DropStrokeList.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
DropStrokeList.Color = Color3.fromRGB(255,255,255)
DropStrokeList.LineJoinMode = Enum.LineJoinMode.Round
DropStrokeList.Thickness = 0.2
DropStrokeList.Transparency = 0
DropStrokeList.Enabled = true
DropStrokeList.Archivable = true

-- Adden Local --
local DropItemScroll = Instance.new("ScrollingFrame")
local DropItemLayout = Instance.new("UIListLayout")
local DropItemStroke = Instance.new("UIStroke")

-- Adden Prop --
DropItemScroll.Name = "DropItemScroll"
DropItemScroll.Parent = Frame
DropItemScroll.BackgroundColor3 = SectionColor
DropItemScroll.BackgroundTransparency = 1.000
DropItemScroll.Position = UDim2.new(0, 3, 0, 60)
DropItemScroll.Size = UDim2.new(0, 280, 0, 0)
DropItemScroll.ScrollBarThickness = 0
DropItemScroll.CanvasSize = UDim2.new(0, 0, 0, 0)

DropItemLayout.Name = "DropItemLayout"
DropItemLayout.Parent = DropItemScroll
DropItemLayout.SortOrder = Enum.SortOrder.LayoutOrder
DropItemLayout.Padding = UDim.new(0, 0)

DropItemStroke.Name = "DropItemStroke"
DropItemStroke.Parent = DropItemScroll
DropItemStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
DropItemStroke.Color = Color3.fromRGB(51,255,255)
DropItemStroke.LineJoinMode = Enum.LineJoinMode.Round
DropItemStroke.Thickness = 0
DropItemStroke.Transparency = 0
DropItemStroke.Enabled = true
DropItemStroke.Archivable = true

-- Dropdown Script--
local ItemCount = 0
local FrameSize = 0

ImageButton.MouseButton1Click:Connect(function()
 if DropToggled then
DropToggled = false
DropSizeFrame:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
Frame:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
DropItemScroll:TweenSize(UDim2.new(0, 278, 0, 0), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 180}
):Play()
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()

 else
DropToggled = true
DropSizeFrame:TweenSize(UDim2.new(0, 278, 0, 65 + FrameSize), 'InOut', 'Linear', 0.08)
Frame:TweenSize(UDim2.new(0, 278, 0, 65 + FrameSize), 'InOut', 'Linear', 0.08)
DropItemScroll:TweenSize(UDim2.new(0, 278, 0, FrameSize), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 0}
):Play()
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()
 end
end)

for i,v in next, list do
 ItemCount = ItemCount + 1
 if ItemCount == 1 then
FrameSize = 30
 elseif ItemCount == 2 then
FrameSize = 60
 elseif ItemCount == 3 then
FrameSize = 90
 elseif ItemCount >= 3 then
FrameSize = 120
 end
 
 local ItemList = Instance.new("TextButton")
 
 ItemList.Name = "ItemList"
 ItemList.Parent = DropItemScroll
 ItemList.BackgroundColor3 = Color3.fromRGB(51,255,255)
 ItemList.BackgroundTransparency = 1.000
 ItemList.Size = UDim2.new(0, 278, 0, 30)
 ItemList.AutoButtonColor = false
 ItemList.Font = Enum.Font.Code
 ItemList.TextColor3 = Color3.fromRGB(51,255,255)
 ItemList.TextSize = 12.000
 ItemList.Text = v or "None..."
 ItemList.TextXAlignment = Enum.TextXAlignment.Center

 ItemList.MouseEnter:Connect(function()
game.TweenService:Create(ItemList, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 0.8}
):Play()
 end)
 ItemList.MouseLeave:Connect(function()
game.TweenService:Create(ItemList, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 1}
):Play()
 end)
 
 ItemList.MouseButton1Click:Connect(function()
DropTextList.Text = v or "None..."
pcall(callback, v)
DropToggled = false
DropSizeFrame:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
Frame:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
DropItemScroll:TweenSize(UDim2.new(0, 278, 0), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 180}
):Play()
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()
 end)
 DropItemScroll.CanvasSize = UDim2.new(0, 0, 0, DropItemLayout.AbsoluteContentSize.Y)
end

function dropfunc:Clear()
                    for _,v  in next, DropItemScroll:GetChildren() do
                        if v:IsA("TextButton") then
                            v:Destroy()
                            FrameSize = 0
                            ItemCount = 0
                        end
                    end
                    DropTextList.Text = "Reset Succesfully..."
                    DropToggled = false
                    DropSizeFrame:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
                    Frame:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
                    DropItemScroll:TweenSize(UDim2.new(0, 278, 0), 'InOut', 'Linear', 0.08)
                    game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {Rotation = 180}
                        ):Play()
                    game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {ImageColor3 = Color3.fromRGB(255,255,255)}
                        ):Play()
                end

function dropfunc:Add(newadd)
 newadd = newadd or {}
 ItemCount = ItemCount + 1
 if ItemCount == 1 then
FrameSize = 30
 elseif ItemCount == 2 then
FrameSize = 60
 elseif ItemCount == 3 then
FrameSize = 90
 elseif ItemCount >= 3 then
FrameSize = 120
 end
 
 local ItemList = Instance.new("TextButton")
 ItemList.Name = "ItemList"
 ItemList.Parent = DropItemScroll
 ItemList.BackgroundColor3 = Color3.fromRGB(51,255,255)
 ItemList.BackgroundTransparency = 1.000
 ItemList.Size = UDim2.new(0, 278, 0, 30)
 ItemList.AutoButtonColor = false
 ItemList.Font = Enum.Font.Code
 ItemList.TextColor3 = Color3.fromRGB(51,255,255)
 ItemList.TextSize = 12.000
 ItemList.Text = newadd or "None..."
 ItemList.TextXAlignment = Enum.TextXAlignment.Center

 ItemList.MouseEnter:Connect(function()
game.TweenService:Create(ItemList, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 0.8}
):Play()
 end)
 ItemList.MouseLeave:Connect(function()
game.TweenService:Create(ItemList, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 1}
):Play()
 end)
 
 ItemList.MouseButton1Click:Connect(function()
DropTextList.Text = newadd or "None..."
pcall(callback, newadd)
DropToggled = false
DropSizeFrame:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
Frame:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
DropItemScroll:TweenSize(UDim2.new(0, 278, 0), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 180}
):Play()
game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()
 end)
 DropItemScroll.CanvasSize = UDim2.new(0, 0, 0, DropItemLayout.AbsoluteContentSize.Y)
end
return dropfunc
end

	function main:AddDropdownRight(droptitle, list, callback1)
-- Local --
local dropfunc1 = {}
local list = list or {}
local DropToggled1 = false
local DropSizeFrame1 = Instance.new("Frame")
local Frame1 = Instance.new("Frame")
local UIStroke1 = Instance.new("UIStroke")
local DropCover1 = Instance.new("Frame")
local UICorner1 = Instance.new("UICorner")
local UICorner21 = Instance.new("UICorner")
local ImageLabel1 = Instance.new("ImageLabel")
local Space1 = Instance.new("TextLabel")
local Title1 = Instance.new("TextLabel")
local ImageButton1 = Instance.new("ImageButton")
local DropStrokeList1 = Instance.new("UIStroke")
local DropTextList1 = Instance.new("TextLabel")

-- Prop --
DropSizeFrame1.Name = droptitle or "DropSizeFrame"
DropSizeFrame1.Parent = MainFramePage2
DropSizeFrame1.BackgroundColor3 = SectionColor
DropSizeFrame1.BackgroundTransparency = 1.000
DropSizeFrame1.Size = UDim2.new(0, 280, 0, 60)

Frame1.Name = "Frame"
Frame1.Parent = DropSizeFrame1
Frame1.BackgroundColor3 = Color3.fromRGB(30,30,30)
Frame1.BorderSizePixel = 0
Frame1.Position = UDim2.new(0, 3, 0, 0)
Frame1.Size = UDim2.new(0, 278, 0, 60)

UIStroke1.Name = "UIStroke"
UIStroke1.Parent = Frame1
UIStroke1.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
UIStroke1.Color = Color3.fromRGB(255,255,255)
UIStroke1.LineJoinMode = Enum.LineJoinMode.Round
UIStroke1.Thickness = 0.7
UIStroke1.Transparency = 0
UIStroke1.Enabled = true
UIStroke1.Archivable = true

UICorner1.Parent = Frame1
UICorner1.CornerRadius = UDim.new(0, 3)

DropCover1.Name = "DropCover"
DropCover1.Parent = Frame1
DropCover1.BackgroundColor3 = BackgroundItemColor
DropCover1.BackgroundTransparency = 1.000
DropCover1.BorderSizePixel = 0
DropCover1.Position = UDim2.new(0, 0, 0, 0)
DropCover1.Size = UDim2.new(0, 204, 0, 30)

ImageLabel1.Name = "ImageLabel"
ImageLabel1.Parent = DropCover1
ImageLabel1.BackgroundColor3 = SectionColor
ImageLabel1.BackgroundTransparency = 1.000
ImageLabel1.BorderSizePixel = 0
ImageLabel1.Position = UDim2.new(0, 5, 0, 6)
ImageLabel1.Size = UDim2.new(0, 18, 0, 18)
ImageLabel1.Image = "rbxassetid://8825010231"
ImageLabel1.ImageColor3 = Color3.fromRGB(255,255,255)

Space1.Name = "Space"
Space1.Parent = DropCover1
Space1.BackgroundColor3 = SectionColor
Space1.BackgroundTransparency = 1.000
Space1.Position = UDim2.new(0, 30, 0, 0)
Space1.Size = UDim2.new(0, 15, 0, 30)
Space1.Font = Enum.Font.Code
Space1.Text = "|"
Space1.TextSize = 13.000
Space1.TextColor3 = Color3.fromRGB(255,255,255)
Space1.TextXAlignment = Enum.TextXAlignment.Center

Title1.Name = "Title"
Title1.Parent = DropCover1
Title1.BackgroundColor3 = SectionColor
Title1.BackgroundTransparency = 1.000
Title1.Position = UDim2.new(0, 50, 0, 0)
Title1.Size = UDim2.new(0, 278, 0, 30)
Title1.Font = Enum.Font.Code
Title1.Text = tostring(droptitle) or "drop Title"
Title1.TextColor3 = Color3.fromRGB(255,255,255)
Title1.TextSize = 12.000
Title1.TextXAlignment = Enum.TextXAlignment.Left

ImageButton1.Name = "ImageButton"
ImageButton1.Parent = DropCover1
ImageButton1.BackgroundColor3 = WindowBackgroundColor
ImageButton1.BackgroundTransparency = 1.000
ImageButton1.Position = UDim2.new(0, 250, 0, 7)
ImageButton1.Size = UDim2.new(0, 23, 0, 18)
ImageButton1.Image = "rbxassetid://6583628103"
ImageButton1.ImageColor3 = Color3.fromRGB(51,255,255)
ImageButton1.Rotation = 180

DropTextList1.Name = "DropTextList"
DropTextList1.Parent = Frame1
DropTextList1.BackgroundColor3 = BackgroundItemColor
DropTextList1.BackgroundTransparency = 1.000
DropTextList1.Position = UDim2.new(0, 3, 0, 30)
DropTextList1.Size = UDim2.new(0, 278, 0, 25)
DropTextList1.Font = Enum.Font.Code
DropTextList1.Text = v or "Select First"
DropTextList1.TextColor3 = Color3.fromRGB(255,255,255)
DropTextList1.TextSize = 12.000
DropTextList1.TextXAlignment = Enum.TextXAlignment.Center

UICorner21.Parent = DropTextList1
UICorner21.CornerRadius = UDim.new(0,0)

DropStrokeList1.Name = "DropStrokeList"
DropStrokeList1.Parent = DropTextList1
DropStrokeList1.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
DropStrokeList1.Color = Color3.fromRGB(255,255,255)
DropStrokeList1.LineJoinMode = Enum.LineJoinMode.Round
DropStrokeList1.Thickness = 0.2
DropStrokeList1.Transparency = 0
DropStrokeList1.Enabled = true
DropStrokeList1.Archivable = true

-- Adden Local --
local DropItemScroll1 = Instance.new("ScrollingFrame")
local DropItemLayout1 = Instance.new("UIListLayout")
local DropItemStroke1 = Instance.new("UIStroke")

-- Adden Prop --
DropItemScroll1.Name = "DropItemScroll"
DropItemScroll1.Parent = Frame1
DropItemScroll1.BackgroundColor3 = SectionColor
DropItemScroll1.BackgroundTransparency = 1.000
DropItemScroll1.Position = UDim2.new(0, 3, 0, 60)
DropItemScroll1.Size = UDim2.new(0, 278, 0, 0)
DropItemScroll1.ScrollBarThickness = 0
DropItemScroll1.CanvasSize = UDim2.new(0, 0, 0, 0)

DropItemLayout1.Name = "DropItemLayout"
DropItemLayout1.Parent = DropItemScroll1
DropItemLayout1.SortOrder = Enum.SortOrder.LayoutOrder
DropItemLayout1.Padding = UDim.new(0, 0)

DropItemStroke1.Name = "DropItemStroke"
DropItemStroke1.Parent = DropItemScroll1
DropItemStroke1.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
DropItemStroke1.Color = Color3.fromRGB(51,255,255)
DropItemStroke1.LineJoinMode = Enum.LineJoinMode.Round
DropItemStroke1.Thickness = 0
DropItemStroke1.Transparency = 0
DropItemStroke1.Enabled = true
DropItemStroke1.Archivable = true

-- Dropdown Script--
local ItemCount1 = 0
local FrameSize1 = 0

ImageButton1.MouseButton1Click:Connect(function()
 if DropToggled1 then
DropToggled1 = false
DropSizeFrame1:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
Frame1:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
DropItemScroll1:TweenSize(UDim2.new(0, 278, 0, 0), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 180}
):Play()
game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()

 else
DropToggled1 = true
DropSizeFrame1:TweenSize(UDim2.new(0, 278, 0, 65 + FrameSize1), 'InOut', 'Linear', 0.08)
Frame1:TweenSize(UDim2.new(0, 278, 0, 65 + FrameSize1), 'InOut', 'Linear', 0.08)
DropItemScroll1:TweenSize(UDim2.new(0, 278, 0, FrameSize1), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 0}
):Play()
game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()
 end
end)

for i,v in next, list do
 ItemCount1 = ItemCount1 + 1
 if ItemCount1 == 1 then
FrameSize1 = 30
 elseif ItemCount1 == 2 then
FrameSize1 = 60
 elseif ItemCount1 == 3 then
FrameSize1 = 90
 elseif ItemCount1 >= 3 then
FrameSize1 = 120
 end
 
 local ItemList1 = Instance.new("TextButton")
 
 ItemList1.Name = "ItemList"
 ItemList1.Parent = DropItemScroll1
 ItemList1.BackgroundColor3 = Color3.fromRGB(51,255,255)
 ItemList1.BackgroundTransparency = 1.000
 ItemList1.Size = UDim2.new(0, 278, 0, 30)
 ItemList1.AutoButtonColor = false
 ItemList1.Font = Enum.Font.Code
 ItemList1.TextColor3 = Color3.fromRGB(51,255,255)
 ItemList1.TextSize = 12.000
 ItemList1.Text = v or "None..."
 ItemList1.TextXAlignment = Enum.TextXAlignment.Center

 ItemList1.MouseEnter:Connect(function()
game.TweenService:Create(ItemList1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 0.8}
):Play()
 end)
 ItemList1.MouseLeave:Connect(function()
game.TweenService:Create(ItemList1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 1}
):Play()
 end)
 
 ItemList1.MouseButton1Click:Connect(function()
DropTextList1.Text = v or "None..."
pcall(callback1, v)
DropToggled1 = false
DropSizeFrame1:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
Frame1:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
DropItemScroll1:TweenSize(UDim2.new(0, 278, 0), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 180}
):Play()
game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()
 end)
 DropItemScroll1.CanvasSize = UDim2.new(0, 0, 0, DropItemLayout1.AbsoluteContentSize.Y)
end

               function dropfunc1:Clear()
                    for _,v  in next, DropItemScroll1:GetChildren() do
                        if v:IsA("TextButton") then
                            v:Destroy()
                        end
                    end
                    DropTextList1.Text = "Reset Succesfully"
                    DropToggled1 = false
                    DropSizeFrame1:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
                    Frame1:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
                    DropItemScroll1:TweenSize(UDim2.new(0, 278, 0), 'InOut', 'Linear', 0.08)
                    game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {Rotation = 180}
                        ):Play()
                    game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
                        {ImageColor3 = Color3.fromRGB(255,255,255)}
                        ):Play()
                end

function dropfunc1:Add(newadd)
 newadd = newadd or {}
 ItemCount1 = ItemCount1 + 1
 if ItemCount1 == 1 then
FrameSize1= 30
 elseif ItemCount1 == 2 then
FrameSize1 = 60
 elseif ItemCount1 == 3 then
FrameSize1 = 90
 elseif ItemCount1 >= 3 then
FrameSize1 = 120
 end
 
 local ItemList1 = Instance.new("TextButton")
 ItemList1.Name = "ItemList"
 ItemList1.Parent = DropItemScroll1
 ItemList1.BackgroundColor3 = Color3.fromRGB(255,255,255)
 ItemList1.BackgroundTransparency = 1.000
 ItemList1.Size = UDim2.new(0, 278, 0, 30)
 ItemList1.AutoButtonColor = false
 ItemList1.Font = Enum.Font.Code
 ItemList1.TextColor3 = Color3.fromRGB(51,255,255)
 ItemList1.TextSize = 12.000
 ItemList1.Text = newadd or "None..."
 ItemList1.TextXAlignment = Enum.TextXAlignment.Center

 ItemList1.MouseEnter:Connect(function()
game.TweenService:Create(ItemList1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 0.8}
):Play()
 end)
 ItemList1.MouseLeave:Connect(function()
game.TweenService:Create(ItemList1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{BackgroundTransparency = 1}
):Play()
 end)
 
 ItemList1.MouseButton1Click:Connect(function()
DropTextList1.Text = newadd or "None..."
pcall(callback1, newadd)
DropToggled1 = false
DropSizeFrame1:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
Frame1:TweenSize(UDim2.new(0, 278, 0, 60), 'InOut', 'Linear', 0.08)
DropItemScroll1:TweenSize(UDim2.new(0, 278, 0), 'InOut', 'Linear', 0.08)
game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{Rotation = 180}
):Play()
game.TweenService:Create(ImageButton1, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
{ImageColor3 = Color3.fromRGB(51,255,255)}
):Play()
 end)
 DropItemScroll1.CanvasSize = UDim2.new(0, 0, 0, DropItemLayout1.AbsoluteContentSize.Y)
end
return dropfunc1
end


function main:AddSliderLeft(text,min,max,set,callback)
				local Slider = Instance.new("Frame")
				local slidercorner = Instance.new("UICorner")
				local sliderr = Instance.new("Frame")
				local sliderrcorner = Instance.new("UICorner")
				local SliderLabel = Instance.new("TextLabel")
				local HAHA = Instance.new("Frame")
				local AHEHE = Instance.new("TextButton")
				local bar = Instance.new("Frame")
				local bar1 = Instance.new("Frame")
				local bar1corner = Instance.new("UICorner")
				local barcorner = Instance.new("UICorner")
				local circlebar = Instance.new("Frame")
				local UICorner = Instance.new("UICorner")
				local slidervalue = Instance.new("Frame")
				local valuecorner = Instance.new("UICorner")
				local TextBox = Instance.new("TextBox")
				local UICorner_2 = Instance.new("UICorner")
	
				Slider.Name = "Slider"
				Slider.Parent = MainFramePage
				Slider.BackgroundColor3 = Color
				Slider.BackgroundTransparency = 0
				Slider.Size = UDim2.new(0, 280, 0, 51)
	
				slidercorner.CornerRadius = UDim.new(0, 5)
				slidercorner.Name = "slidercorner"
				slidercorner.Parent = Slider
	
				sliderr.Name = "sliderr"
				sliderr.Parent = Slider
				sliderr.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
				sliderr.Position = UDim2.new(0, 1, 0, 1)
				sliderr.Size = UDim2.new(0, 278, 0, 49)
	
				sliderrcorner.CornerRadius = UDim.new(0, 5)
				sliderrcorner.Name = "sliderrcorner"
				sliderrcorner.Parent = sliderr
	
				SliderLabel.Name = "SliderLabel"
				SliderLabel.Parent = sliderr
				SliderLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				SliderLabel.BackgroundTransparency = 1.000
				SliderLabel.Position = UDim2.new(0, 15, 0, 0)
				SliderLabel.Size = UDim2.new(0, 100, 0, 26)
				SliderLabel.Font = Enum.Font.Code
				SliderLabel.Text = text
				SliderLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
				SliderLabel.TextSize = 16.000
				SliderLabel.TextTransparency = 0
				SliderLabel.TextXAlignment = Enum.TextXAlignment.Left
	
				HAHA.Name = "HAHA"
				HAHA.Parent = sliderr
				HAHA.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				HAHA.BackgroundTransparency = 1.000
				HAHA.Size = UDim2.new(0, 468, 0, 29)
	
				AHEHE.Name = "AHEHE"
				AHEHE.Parent = sliderr
				AHEHE.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				AHEHE.BackgroundTransparency = 1.000
				AHEHE.Position = UDim2.new(0, 10, 0, 35)
				AHEHE.Size = UDim2.new(0, 260, 0, 5)
				AHEHE.Font = Enum.Font.Code
				AHEHE.Text = ""
				AHEHE.TextColor3 = Color3.fromRGB(0, 0, 0)
				AHEHE.TextSize = 14.000
	
				bar.Name = "bar"
				bar.Parent = AHEHE
				bar.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
				bar.Size = UDim2.new(0, 260, 0, 5)
	
				bar1.Name = "bar1"
				bar1.Parent = bar
				bar1.BackgroundColor3 = Color
				bar1.BackgroundTransparency = 0
				bar1.Size = UDim2.new(set/max, 0, 0, 5)
	
				bar1corner.CornerRadius = UDim.new(0, 5)
				bar1corner.Name = "bar1corner"
				bar1corner.Parent = bar1
	
				barcorner.CornerRadius = UDim.new(0, 5)
				barcorner.Name = "barcorner"
				barcorner.Parent = bar
	
				circlebar.Name = "circlebar"
				circlebar.Parent = bar1
				circlebar.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
				circlebar.Position = UDim2.new(1, -2, 0, -3)
				circlebar.Size = UDim2.new(0, 10, 0, 10)
	
				UICorner.CornerRadius = UDim.new(0, 100)
				UICorner.Parent = circlebar
	
				slidervalue.Name = "slidervalue"
				slidervalue.Parent = sliderr
				slidervalue.BackgroundColor3 = Color
				slidervalue.BackgroundTransparency = 0
				slidervalue.Position = UDim2.new(0, 220, 0, 5)
				slidervalue.Size = UDim2.new(0, 50, 0, 15)
	
				valuecorner.CornerRadius = UDim.new(0, 5)
				valuecorner.Name = "valuecorner"
				valuecorner.Parent = slidervalue
	
				TextBox.Parent = slidervalue
				TextBox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
				TextBox.Position = UDim2.new(0, 1, 0, 1)
				TextBox.Size = UDim2.new(0, 48, 0, 13)
				TextBox.Font = Enum.Font.Code
				TextBox.TextColor3 = Color3.fromRGB(225, 225, 225)
				TextBox.TextSize = 9.000
				TextBox.Text = set
				TextBox.TextTransparency = 0
	
				UICorner_2.CornerRadius = UDim.new(0, 5)
				UICorner_2.Parent = TextBox
	
				local mouse = game.Players.LocalPlayer:GetMouse()
				local uis = game:GetService("UserInputService")
	
				if Value == nil then
					Value = set
					pcall(function()
						callback(Value)
					end)
				end
				
				AHEHE.MouseButton1Down:Connect(function()
					Value = math.floor((((tonumber(max) - tonumber(min)) / 260) * bar1.AbsoluteSize.X) + tonumber(min)) or 0
					pcall(function()
						callback(Value)
					end)
					TweenService:Create(
						bar1,
						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 260), 0, 5)} -- UDim2.new(0, 128, 0, 25)
					):Play()
					--bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
					TweenService:Create(
						circlebar,
						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{Position =  UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 260), 0, -3)} -- UDim2.new(0, 128, 0, 25)
					):Play()
					--circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
					moveconnection = mouse.Move:Connect(function()
						TextBox.Text = Value
						Value = math.floor((((tonumber(max) - tonumber(min)) / 260) * bar1.AbsoluteSize.X) + tonumber(min))
						pcall(function()
							callback(Value)
						end)
						TweenService:Create(
							bar1,
							TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 260), 0, 5)} -- UDim2.new(0, 128, 0, 25)
						):Play()
						--bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
						TweenService:Create(
							circlebar,
							TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{Position =  UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 260), 0, -3)} -- UDim2.new(0, 128, 0, 25)
						):Play()
						--circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
					end)
					releaseconnection = uis.InputEnded:Connect(function(Mouse)
						if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
							Value = math.floor((((tonumber(max) - tonumber(min)) / 260) * bar1.AbsoluteSize.X) + tonumber(min))
							pcall(function()
								callback(Value)
							end)
							TweenService:Create(
								bar1,
								TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
								{Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 260), 0, 5)} -- UDim2.new(0, 128, 0, 25)
							):Play()
							--bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
							TweenService:Create(
								circlebar,
								TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
								{Position =  UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 260), 0, -3)} -- UDim2.new(0, 128, 0, 25)
							):Play()
							--circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
							moveconnection:Disconnect()
							releaseconnection:Disconnect()
						end
					end)
				end)
				releaseconnection = uis.InputEnded:Connect(function(Mouse)
					if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
						Value = math.floor((((tonumber(max) - tonumber(min)) / 260) * bar1.AbsoluteSize.X) + tonumber(min))
						TextBox.Text = Value
					end
				end)
	
				TextBox.FocusLost:Connect(function()
					if tonumber(TextBox.Text) > max then
						TextBox.Text  = max
					end
					bar1.Size = UDim2.new((TextBox.Text or 0) / max, 0, 0, 5)
					circlebar.Position = UDim2.new(1, -2, 0, -3)
					TextBox.Text = tostring(TextBox.Text and math.floor( (TextBox.Text / max) * (max - min) + min) )
					pcall(callback, TextBox.Text)
				end)
			end

function main:AddSliderRight(text,min,max,set,callback)
				local Slider = Instance.new("Frame")
				local slidercorner = Instance.new("UICorner")
				local sliderr = Instance.new("Frame")
				local sliderrcorner = Instance.new("UICorner")
				local SliderLabel = Instance.new("TextLabel")
				local HAHA = Instance.new("Frame")
				local AHEHE = Instance.new("TextButton")
				local bar = Instance.new("Frame")
				local bar1 = Instance.new("Frame")
				local bar1corner = Instance.new("UICorner")
				local barcorner = Instance.new("UICorner")
				local circlebar = Instance.new("Frame")
				local UICorner = Instance.new("UICorner")
				local slidervalue = Instance.new("Frame")
				local valuecorner = Instance.new("UICorner")
				local TextBox = Instance.new("TextBox")
				local UICorner_2 = Instance.new("UICorner")
	
				Slider.Name = "Slider"
				Slider.Parent = MainFramePage2
				Slider.BackgroundColor3 = Color
				Slider.BackgroundTransparency = 0
				Slider.Size = UDim2.new(0, 280, 0, 51)
	
				slidercorner.CornerRadius = UDim.new(0, 5)
				slidercorner.Name = "slidercorner"
				slidercorner.Parent = Slider
	
				sliderr.Name = "sliderr"
				sliderr.Parent = Slider
				sliderr.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
				sliderr.Position = UDim2.new(0, 1, 0, 1)
				sliderr.Size = UDim2.new(0, 278, 0, 49)
	
				sliderrcorner.CornerRadius = UDim.new(0, 5)
				sliderrcorner.Name = "sliderrcorner"
				sliderrcorner.Parent = sliderr
	
				SliderLabel.Name = "SliderLabel"
				SliderLabel.Parent = sliderr
				SliderLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				SliderLabel.BackgroundTransparency = 1.000
				SliderLabel.Position = UDim2.new(0, 15, 0, 0)
				SliderLabel.Size = UDim2.new(0, 100, 0, 26)
				SliderLabel.Font = Enum.Font.Code
				SliderLabel.Text = text
				SliderLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
				SliderLabel.TextSize = 16.000
				SliderLabel.TextTransparency = 0
				SliderLabel.TextXAlignment = Enum.TextXAlignment.Left
	
				HAHA.Name = "HAHA"
				HAHA.Parent = sliderr
				HAHA.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				HAHA.BackgroundTransparency = 1.000
				HAHA.Size = UDim2.new(0, 468, 0, 29)
	
				AHEHE.Name = "AHEHE"
				AHEHE.Parent = sliderr
				AHEHE.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				AHEHE.BackgroundTransparency = 1.000
				AHEHE.Position = UDim2.new(0, 10, 0, 35)
				AHEHE.Size = UDim2.new(0, 260, 0, 5)
				AHEHE.Font = Enum.Font.Code
				AHEHE.Text = ""
				AHEHE.TextColor3 = Color3.fromRGB(0, 0, 0)
				AHEHE.TextSize = 14.000
	
				bar.Name = "bar"
				bar.Parent = AHEHE
				bar.BackgroundColor3 = Color3.fromRGB(45,45,45)
				bar.Size = UDim2.new(0, 260, 0, 5)
	
				bar1.Name = "bar1"
				bar1.Parent = bar
				bar1.BackgroundColor3 = Color
				bar1.BackgroundTransparency = 0
				bar1.Size = UDim2.new(set/max, 0, 0, 5)
	
				bar1corner.CornerRadius = UDim.new(0, 5)
				bar1corner.Name = "bar1corner"
				bar1corner.Parent = bar1
	
				barcorner.CornerRadius = UDim.new(0, 5)
				barcorner.Name = "barcorner"
				barcorner.Parent = bar
	
				circlebar.Name = "circlebar"
				circlebar.Parent = bar1
				circlebar.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
				circlebar.Position = UDim2.new(1, -2, 0, -3)
				circlebar.Size = UDim2.new(0, 10, 0, 10)
	
				UICorner.CornerRadius = UDim.new(0, 100)
				UICorner.Parent = circlebar
	
				slidervalue.Name = "slidervalue"
				slidervalue.Parent = sliderr
				slidervalue.BackgroundColor3 = Color
				slidervalue.BackgroundTransparency = 0
				slidervalue.Position = UDim2.new(0, 220, 0, 5)
				slidervalue.Size = UDim2.new(0, 50, 0, 15)
	
				valuecorner.CornerRadius = UDim.new(0, 5)
				valuecorner.Name = "valuecorner"
				valuecorner.Parent = slidervalue
	
				TextBox.Parent = slidervalue
				TextBox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
				TextBox.Position = UDim2.new(0, 1, 0, 1)
				TextBox.Size = UDim2.new(0, 48, 0, 13)
				TextBox.Font = Enum.Font.Code
				TextBox.TextColor3 = Color3.fromRGB(225, 225, 225)
				TextBox.TextSize = 9.000
				TextBox.Text = set
				TextBox.TextTransparency = 0
	
				UICorner_2.CornerRadius = UDim.new(0, 5)
				UICorner_2.Parent = TextBox
	
				local mouse = game.Players.LocalPlayer:GetMouse()
				local uis = game:GetService("UserInputService")
	
				if Value == nil then
					Value = set
					pcall(function()
						callback(Value)
					end)
				end
				
				AHEHE.MouseButton1Down:Connect(function()
					Value = math.floor((((tonumber(max) - tonumber(min)) / 260) * bar1.AbsoluteSize.X) + tonumber(min)) or 0
					pcall(function()
						callback(Value)
					end)
					TweenService:Create(
						bar1,
						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 260), 0, 5)} -- UDim2.new(0, 128, 0, 25)
					):Play()
					--bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
					TweenService:Create(
						circlebar,
						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{Position =  UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 260), 0, -3)} -- UDim2.new(0, 128, 0, 25)
					):Play()
					--circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
					moveconnection = mouse.Move:Connect(function()
						TextBox.Text = Value
						Value = math.floor((((tonumber(max) - tonumber(min)) / 260) * bar1.AbsoluteSize.X) + tonumber(min))
						pcall(function()
							callback(Value)
						end)
						TweenService:Create(
							bar1,
							TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 260), 0, 5)} -- UDim2.new(0, 128, 0, 25)
						):Play()
						--bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
						TweenService:Create(
							circlebar,
							TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{Position =  UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 260), 0, -3)} -- UDim2.new(0, 128, 0, 25)
						):Play()
						--circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
					end)
					releaseconnection = uis.InputEnded:Connect(function(Mouse)
						if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
							Value = math.floor((((tonumber(max) - tonumber(min)) / 260) * bar1.AbsoluteSize.X) + tonumber(min))
							pcall(function()
								callback(Value)
							end)
							TweenService:Create(
								bar1,
								TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
								{Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 260), 0, 5)} -- UDim2.new(0, 128, 0, 25)
							):Play()
							--bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
							TweenService:Create(
								circlebar,
								TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
								{Position =  UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 260), 0, -3)} -- UDim2.new(0, 128, 0, 25)
							):Play()
							--circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
							moveconnection:Disconnect()
							releaseconnection:Disconnect()
						end
					end)
				end)
				releaseconnection = uis.InputEnded:Connect(function(Mouse)
					if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
						Value = math.floor((((tonumber(max) - tonumber(min)) / 260) * bar1.AbsoluteSize.X) + tonumber(min))
						TextBox.Text = Value
					end
				end)
	
				TextBox.FocusLost:Connect(function()
					if tonumber(TextBox.Text) > max then
						TextBox.Text  = max
					end
					bar1.Size = UDim2.new((TextBox.Text or 0) / max, 0, 0, 5)
					circlebar.Position = UDim2.new(1, -2, 0, -3)
					TextBox.Text = tostring(TextBox.Text and math.floor( (TextBox.Text / max) * (max - min) + min) )
					pcall(callback, TextBox.Text)
				end)
			end



		function main:AddTextboxLeft(text,texts,disappear,callback)
			local Textbox = Instance.new("Frame")
			local TextboxCorner = Instance.new("UICorner")
			local Textboxx = Instance.new("Frame")
			local TextboxxCorner = Instance.new("UICorner")
			local TextboxLabel = Instance.new("TextLabel")
			local txtbtn = Instance.new("TextButton")
			local RealTextbox = Instance.new("TextBox")
			local UICorner = Instance.new("UICorner")

         
			Textbox.Name = "Textbox"
			Textbox.Parent = MainFramePage
			Textbox.BackgroundColor3 = Color
			Textbox.BackgroundTransparency = 0
			Textbox.Size = UDim2.new(0, 280, 0, 57)

			TextboxCorner.CornerRadius = UDim.new(0, 5)
			TextboxCorner.Name = "TextboxCorner"
			TextboxCorner.Parent = Textbox

			Textboxx.Name = "Textboxx"
			Textboxx.Parent = Textbox
			Textboxx.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			Textboxx.Position = UDim2.new(0, 1, 0, 1)
			Textboxx.Size = UDim2.new(0, 278, 0, 55)

			TextboxxCorner.CornerRadius = UDim.new(0, 5)
			TextboxxCorner.Name = "TextboxxCorner"
			TextboxxCorner.Parent = Textboxx

		
			txtbtn.Name = "txtbtn"
			txtbtn.Parent = Textbox
			txtbtn.BackgroundColor3 = Color3.fromRGB(51,255,255)
			txtbtn.BackgroundTransparency = 1.000
			txtbtn.Position = UDim2.new(0, 1, 0, 1)
			txtbtn.Size = UDim2.new(0, 278, 0, 45)
			txtbtn.Font = Enum.Font.SourceSans
			txtbtn.Text = ""
			txtbtn.TextColor3 = Color3.fromRGB(0, 0, 0)
			txtbtn.TextSize = 14.000

TextboxLabel.Name = "TextboxLabel"
			TextboxLabel.Parent = Textbox
			TextboxLabel.BackgroundColor3 = Color3.fromRGB(51,255,255)
			TextboxLabel.BackgroundTransparency = 1.000
			TextboxLabel.Position = UDim2.new(0, 15, 0, 8)
			TextboxLabel.Text = text
			TextboxLabel.Size = UDim2.new(0, 220, 0, 12)
			TextboxLabel.Font = Enum.Font.Code
			TextboxLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextboxLabel.TextSize = 12.000
			TextboxLabel.TextTransparency = 0
			TextboxLabel.TextXAlignment = Enum.TextXAlignment.Left

			Textbox.Name = "Textbox"
			Textbox.Parent = MainFramePage
			Textbox.BackgroundColor3 = Color
			Textbox.BackgroundTransparency = 0
			Textbox.Size = UDim2.new(0, 280, 0, 57)

			RealTextbox.Name = "RealTextbox"
			RealTextbox.Parent = Textbox
			RealTextbox.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			RealTextbox.BackgroundTransparency = 0
			RealTextbox.Position = UDim2.new(0, 3, 0, 30)
			RealTextbox.Size = UDim2.new(0, 276, 0, 24)
			RealTextbox.Font = Enum.Font.Code
			RealTextbox.Text = texts
			RealTextbox.TextColor3 = Color3.fromRGB(255, 225, 225)
			RealTextbox.TextSize = 11.000
			RealTextbox.TextTransparency = 0

			RealTextbox.FocusLost:Connect(function()
				callback(RealTextbox.Text)
				if disappear then
					RealTextbox.Text = ""
				end
			end)

			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = RealTextbox
		end
		
		function main:AddTextboxRight(text,texts,disappear,callback)
			local Textboxx = Instance.new("Frame")
			local TextboxCornerr = Instance.new("UICorner")
			local Textboxxx = Instance.new("Frame")
			local TextboxxCornerr = Instance.new("UICorner")
			local TextboxLabell = Instance.new("TextLabel")
			local txtbtnn = Instance.new("TextButton")
			local RealTextboxx = Instance.new("TextBox")
			local UICornerr = Instance.new("UICorner")

			Textboxx.Name = "Textbox"
			Textboxx.Parent = MainFramePage2
			Textboxx.BackgroundColor3 = Color
			Textboxx.BackgroundTransparency = 0
			Textboxx.Size = UDim2.new(0, 280, 0, 57)

			TextboxCornerr.CornerRadius = UDim.new(0, 5)
			TextboxCornerr.Name = "TextboxCorner"
			TextboxCornerr.Parent = Textboxx

			Textboxxx.Name = "Textboxx"
			Textboxxx.Parent = Textboxx
			Textboxxx.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
			Textboxxx.Position = UDim2.new(0, 1, 0, 1)
			Textboxxx.Size = UDim2.new(0, 278, 0, 55)

			TextboxxCornerr.CornerRadius = UDim.new(0, 5)
			TextboxxCornerr.Name = "TextboxxCorner"
			TextboxxCornerr.Parent = Textboxxx

		
			txtbtnn.Name = "txtbtn"
			txtbtnn.Parent = Textboxx
			txtbtnn.BackgroundColor3 = Color3.fromRGB(51,255,255)
			txtbtnn.BackgroundTransparency = 1.000
			txtbtnn.Position = UDim2.new(0, 1, 0, 1)
			txtbtnn.Size = UDim2.new(0, 278, 0, 45)
			txtbtnn.Font = Enum.Font.SourceSans
			txtbtnn.Text = ""
			txtbtnn.TextColor3 = Color3.fromRGB(0, 0, 0)
			txtbtnn.TextSize = 14.000

TextboxLabell.Name = "TextboxLabel"
			TextboxLabell.Parent = Textboxx
			TextboxLabell.BackgroundColor3 = Color3.fromRGB(51,255,255)
			TextboxLabell.BackgroundTransparency = 1.000
			TextboxLabell.Position = UDim2.new(0, 15, 0, 8)
			TextboxLabell.Text = text
			TextboxLabell.Size = UDim2.new(0, 278, 0, 12)
			TextboxLabell.Font = Enum.Font.Code
			TextboxLabell.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextboxLabell.TextSize = 12.000
			TextboxLabell.TextTransparency = 0
			TextboxLabell.TextXAlignment = Enum.TextXAlignment.Left

			RealTextboxx.Name = "RealTextbox"
			RealTextboxx.Parent = Textboxx
			RealTextboxx.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			RealTextboxx.BackgroundTransparency = 0
			RealTextboxx.Position = UDim2.new(0, 3, 0, 30)
			RealTextboxx.Size = UDim2.new(0, 276, 0, 24)
			RealTextboxx.Font = Enum.Font.Code
			RealTextboxx.Text = texts
			RealTextboxx.TextColor3 = Color3.fromRGB(255, 225, 225)
			RealTextboxx.TextSize = 11.000
			RealTextboxx.TextTransparency = 0

			RealTextboxx.FocusLost:Connect(function()
				callback(RealTextboxx.Text)
				if disappear then
					RealTextboxx.Text = ""
				end
			end)

			UICornerr.CornerRadius = UDim.new(0, 5)
			UICornerr.Parent = RealTextboxx
		end
		
		function main:AddLabelLeft(text)
			local Label = Instance.new("TextLabel")
			local PaddingLabel = Instance.new("UIPadding")
			local labelfunc = {}
	
			Label.Name = "Label"
			Label.Parent = MainFramePage
			Label.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Label.BackgroundTransparency = 1.000
			Label.Size = UDim2.new(0, 360, 0, 20)
			Label.Font = Enum.Font.Code
			Label.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label.TextSize = 14.000
			Label.Text = text
			Label.TextXAlignment = Enum.TextXAlignment.Left

			PaddingLabel.PaddingLeft = UDim.new(0,15)
			PaddingLabel.Parent = Label
			PaddingLabel.Name = "PaddingLabel"
	
			function labelfunc:Set(newtext)
			Label.Text = newtext
		end
		return labelfunc
		end

		function main:AddLabelRight(text)
			local Labell = Instance.new("TextLabel")
			local PaddingLabell = Instance.new("UIPadding")
			local labelfunc = {}
	
			Labell.Name = "Label"
			Labell.Parent = MainFramePage2
			Labell.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Labell.BackgroundTransparency = 1.000
			Labell.Size = UDim2.new(0, 360, 0, 20)
			Labell.Font = Enum.Font.Code
			Labell.TextColor3 = Color3.fromRGB(225, 225, 225)
			Labell.TextSize = 14.000
			Labell.Text = text
			Labell.TextXAlignment = Enum.TextXAlignment.Left

			PaddingLabell.PaddingLeft = UDim.new(0,15)
			PaddingLabell.Parent = Labell
			PaddingLabell.Name = "PaddingLabel"
	
			function labelfunc:Set(newtext)
			Labell.Text = newtext
		end
		return labelfunc
		end


function main:Label1(text)
			local Label1 = Instance.new("TextLabel")
			local PaddingLabel1 = Instance.new("UIPadding")
			local Label1func = {}
	
			Label1.Name = "Label1"
			Label1.Parent = MainFramePage
			Label1.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Label1.BackgroundTransparency = 1.000
			Label1.Size = UDim2.new(0, 360, 0, 20)
			Label1.Font = Enum.Font.Code
			Label1.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label1.TextSize = 15.000
			Label1.Text = text
			Label1.TextXAlignment = Enum.TextXAlignment.Left

			PaddingLabel1.PaddingLeft = UDim.new(0,15)
			PaddingLabel1.Parent = Label1
			PaddingLabel1.Name = "PaddingLabel1"
function Label1func:Refresh(tochange)
 Label1.Text = tochange
end

return Label1func
end

		function main:AddSeperatorLeft(text)
			local Seperator = Instance.new("Frame")
			local Sep1 = Instance.new("Frame")
			local Sep2 = Instance.new("TextLabel")
			local Sep3 = Instance.new("Frame")
			
			Seperator.Name = "Seperator"
			Seperator.Parent = MainFramePage
			Seperator.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Seperator.BackgroundTransparency = 1.000
			Seperator.Size = UDim2.new(0, 280, 0, 20)
			
			Sep1.Name = "Sep1"
			Sep1.Parent = Seperator
			Sep1.BackgroundColor3 = Color
			Sep1.BorderSizePixel = 0
			Sep1.Position = UDim2.new(0, 0, 0, 10)
			Sep1.Size = UDim2.new(0, 20, 0, 1)
			
			Sep2.Name = "Sep2"
			Sep2.Parent = Seperator
			Sep2.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Sep2.BackgroundTransparency = 1.000
			Sep2.Position = UDim2.new(0, 0.01, 0, 0)
			Sep2.Size = UDim2.new(0, 280, 0, 20)
			Sep2.Font = Enum.Font.Code
			Sep2.Text = text
			Sep2.TextColor3 = Color3.fromRGB(51,255,255)
			Sep2.TextSize = 20.000
			
			Sep3.Name = "Sep3"
			Sep3.Parent = Seperator
			Sep3.BackgroundColor3 = Color
			Sep3.BorderSizePixel = 0
			Sep3.Position = UDim2.new(0, 260, 0, 10)
			Sep3.Size = UDim2.new(0, 20, 0, 1)
		end

		function main:AddSeperatorRight(text)
			local Seperator2 = Instance.new("Frame")
			local Sep4 = Instance.new("Frame")
			local Sep5 = Instance.new("TextLabel")
			local Sep6 = Instance.new("Frame")
			
			Seperator2.Name = "Seperator"
			Seperator2.Parent = MainFramePage2
			Seperator2.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Seperator2.BackgroundTransparency = 1.000
			Seperator2.Size = UDim2.new(0, 280, 0, 20)
			
			Sep4.Name = "Sep1"
			Sep4.Parent = Seperator2
			Sep4.BackgroundColor3 = Color
			Sep4.BorderSizePixel = 0
			Sep4.Position = UDim2.new(0, 0, 0, 10)
			Sep4.Size = UDim2.new(0, 20, 0, 1)
			
			Sep5.Name = "Sep2"
			Sep5.Parent = Seperator2
			Sep5.BackgroundColor3 = Color3.fromRGB(51,255,255)
			Sep5.BackgroundTransparency = 1.000
			Sep5.Position = UDim2.new(0, 0.01, 0, 0)
			Sep5.Size = UDim2.new(0, 280, 0, 20)
			Sep5.Font = Enum.Font.Code
			Sep5.Text = text
			Sep5.TextColor3 = Color3.fromRGB(51,255,255)
			Sep5.TextSize = 20.000
			
			Sep6.Name = "Sep3"
			Sep6.Parent = Seperator2
			Sep6.BackgroundColor3 = Color
			Sep6.BorderSizePixel = 0
			Sep6.Position = UDim2.new(0, 260, 0, 10)
			Sep6.Size = UDim2.new(0, 20, 0, 1)
		end


		function main:AddLineLeft()
			local Linee = Instance.new("Frame")
			local Line = Instance.new("Frame")
			
			Linee.Name = "Linee"
			Linee.Parent = MainFramePage
			Linee.BackgroundColor3 = Color3.fromRGB(255,0,0)
			Linee.BackgroundTransparency = 1.000
			Linee.Position = UDim2.new(0, 0, 0.119999997, 0)
			Linee.Size = UDim2.new(0, 280, 0, 20)
			
			Line.Name = "Line"
			Line.Parent = Linee
			Line.BackgroundColor3 = Color
			Line.BorderSizePixel = 0
			Line.Position = UDim2.new(0, 0, 0, 10)
			Line.Size = UDim2.new(0, 280, 0, 1)
		end
		
		function main:AddLineRight()
			local Lineee = Instance.new("Frame")
			local Line1 = Instance.new("Frame")
			
			Lineee.Name = "Linee"
			Lineee.Parent = MainFramePage2
			Lineee.BackgroundColor3 = Color3.fromRGB(255,0,0)
			Lineee.BackgroundTransparency = 1.000
			Lineee.Position = UDim2.new(0, 0, 0.119999997, 0)
			Lineee.Size = UDim2.new(0, 280, 0, 20)
			
			Line1.Name = "Line"
			Line1.Parent = Lineee
			Line1.BackgroundColor3 = Color
			Line1.BorderSizePixel = 0
			Line1.Position = UDim2.new(0, 0, 0, 10)
			Line1.Size = UDim2.new(0, 280, 0, 1)
		end
		
		return main
	end
	return uitab
end


    function Hop()
        local PlaceID = game.PlaceId
        local AllIDs = {}
        local foundAnything = ""
        local actualHour = os.date("!*t").hour
        local Deleted = false
        function TPReturner()
            local Site;
            if foundAnything == "" then
                Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
            else
                Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
            end
            local ID = ""
            if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
                foundAnything = Site.nextPageCursor
            end
            local num = 0;
            for i,v in pairs(Site.data) do
                local Possible = true
                ID = tostring(v.id)
                if tonumber(v.maxPlayers) > tonumber(v.playing) then
                    for _,Existing in pairs(AllIDs) do
                        if num ~= 0 then
                            if ID == tostring(Existing) then
                                Possible = false
                            end
                        else
                            if tonumber(actualHour) ~= tonumber(Existing) then
                                local delFile = pcall(function()
                                    AllIDs = {}
                                    table.insert(AllIDs, actualHour)
                                end)
                            end
                        end
                        num = num + 1
                    end
                    if Possible == true then
                        table.insert(AllIDs, ID)
                        wait()
                        pcall(function()
                            wait()
                            game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
                        end)
                        wait(4)
                    end
                end
            end
        end
        function Teleport() 
            while wait() do
                pcall(function()
                    TPReturner()
                    if foundAnything ~= "" then
                        TPReturner()
                    end
                end)
            end
        end
        Teleport()
    end                   
    
    function isnil(thing)
        return (thing == nil)
    end
    local function round(n)
        return math.floor(tonumber(n) + 0.5)
    end
    Number = math.random(1, 1000000)
    function UpdateEspPlayer()
        if ESPPlayer then
            for i,v in pairs(game:GetService("Players"):GetPlayers()) do
                if not isnil(v.Character) then
                    if not v.Character.Head:FindFirstChild('NameEsp'..v.Name) then
                        local BillboardGui = Instance.new("BillboardGui")
                        local ESP = Instance.new("TextLabel")
                        local HealthESP = Instance.new("TextLabel")
                        BillboardGui.Parent = v.Character.Head
                        BillboardGui.Name = 'NameEsp'..v.Name
                        BillboardGui.ExtentsOffset = Vector3.new(0, 1, 0)
                        BillboardGui.Size = UDim2.new(1,200,1,30)
                        BillboardGui.Adornee = v.Character.Head
                        BillboardGui.AlwaysOnTop = true
                        ESP.Name = "ESP"
                        ESP.Parent = BillboardGui
                        ESP.TextTransparency = 0
                        ESP.BackgroundTransparency = 1
                        ESP.Size = UDim2.new(0, 200, 0, 30)
                        ESP.Position = UDim2.new(0,25,0,0)
                        ESP.Font = Enum.Font.Gotham
                        ESP.Text = (v.Name ..' '.."[ "..round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M'.." ]")
                        if v.Team == game:GetService("Players").LocalPlayer.Team then
                            ESP.TextColor3 = Color3.new(0, 255, 255)
                        else
                            ESP.TextColor3 = Color3.new(255, 0, 0)
                        end
                        ESP.TextSize = 14
                        ESP.TextStrokeTransparency = 0.500
                        ESP.TextWrapped = true
                        HealthESP.Name = "HealthESP"
                        HealthESP.Parent = ESP
                        HealthESP.TextTransparency = 0
                        HealthESP.BackgroundTransparency = 1
                        HealthESP.Position = ESP.Position + UDim2.new(0, -25, 0, 15)
                        HealthESP.Size = UDim2.new(0, 200, 0, 30)
                        HealthESP.Font = Enum.Font.Gotham
                        HealthESP.TextColor3 = Color3.fromRGB(255, 0, 0)
                        HealthESP.TextSize = 14
                        HealthESP.TextStrokeTransparency = 0.500
                        HealthESP.TextWrapped = true
                        HealthESP.Text = "Health "..math.floor(v.Character.Humanoid.Health).."/"..math.floor(v.Character.Humanoid.MaxHealth)
                    else
                        v.Character.Head['NameEsp'..v.Name].ESP.Text = (v.Name ..' '..round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
                        v.Character.Head['NameEsp'..v.Name].ESP.HealthESP.Text = "Health "..math.floor(v.Character.Humanoid.Health).."/"..math.floor(v.Character.Humanoid.MaxHealth)
                        v.Character.Head:FindFirstChild('NameEsp'..v.Name).ESP.TextTransparency = 0
                        v.Character.Head:FindFirstChild('NameEsp'..v.Name).ESP.HealthESP.TextTransparency = 0
                    end
                end
            end
        else
            for i,v in pairs(game:GetService("Players"):GetPlayers()) do
                if v.Character.Head:FindFirstChild('NameEsp'..v.Name) then
                    v.Character.Head:FindFirstChild('NameEsp'..v.Name).ESP.TextTransparency = 1
                    v.Character.Head:FindFirstChild('NameEsp'..v.Name).ESP.HealthESP.TextTransparency = 1
                end
            end
        end     
    end
    
    function UpdateIslandESP() 
        for i,v in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
            pcall(function()
                if IslandESP then 
                    if v.Name ~= "Sea" then
                        if not v:FindFirstChild('NameEsp') then
                            local bill = Instance.new('BillboardGui',v)
                            bill.Name = 'NameEsp'
                            bill.ExtentsOffset = Vector3.new(0, 1, 0)
                            bill.Size = UDim2.new(1,200,1,30)
                            bill.Adornee = v
                            bill.AlwaysOnTop = true
                            local name = Instance.new('TextLabel',bill)
                            name.Font = "GothamBold"
                            name.FontSize = "Size14"
                            name.TextWrapped = true
                            name.Size = UDim2.new(1,0,1,0)
                            name.TextYAlignment = 'Top'
                            name.BackgroundTransparency = 1
                            name.TextStrokeTransparency = 0.5
                            name.TextColor3 = Color3.fromRGB(80, 245, 245)
                        else
                            v['NameEsp'].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                        end
                    end
                else
                    if v:FindFirstChild('NameEsp') then
                        v:FindFirstChild('NameEsp'):Destroy()
                    end
                end
            end)
        end
    end
    
    function UpdateChestEsp() 
        for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
            pcall(function()
                if string.find(v.Name,"Chest") then
                    if ChestESP then
                        if string.find(v.Name,"Chest") then
                            if not v:FindFirstChild('NameEsp'..Number) then
                                local bill = Instance.new('BillboardGui',v)
                                bill.Name = 'NameEsp'..Number
                                bill.ExtentsOffset = Vector3.new(0, 1, 0)
                                bill.Size = UDim2.new(1,200,1,30)
                                bill.Adornee = v
                                bill.AlwaysOnTop = true
                                local name = Instance.new('TextLabel',bill)
                                name.Font = "GothamBold"
                                name.FontSize = "Size14"
                                name.TextWrapped = true
                                name.Size = UDim2.new(1,0,1,0)
                                name.TextYAlignment = 'Top'
                                name.BackgroundTransparency = 1
                                name.TextStrokeTransparency = 0.5
                                name.TextColor3 = Color3.fromRGB(0, 255, 250)
                            if v.Name == "Chest1" then
                                name.Text = ("Chest 1" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                            end
                            if v.Name == "Chest2" then
                                name.Text = ("Chest 2" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                            end
                        if v.Name == "Chest3" then
                            name.Text = ("Chest 3" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                        end
                        else
                            v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                        end
                    end
                else
                    if v:FindFirstChild('NameEsp'..Number) then
                    v:FindFirstChild('NameEsp'..Number):Destroy()
                    end
                end
                end
            end)
        end
    end
    
    function UpdateBfEsp() 
        for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
            pcall(function()
                if DevilFruitESP then
                    if string.find(v.Name, "Fruit") then   
                        if not v.Handle:FindFirstChild('NameEsp'..Number) then
                            local bill = Instance.new('BillboardGui',v.Handle)
                            bill.Name = 'NameEsp'..Number
                            bill.ExtentsOffset = Vector3.new(0, 1, 0)
                            bill.Size = UDim2.new(1,200,1,30)
                            bill.Adornee = v.Handle
                            bill.AlwaysOnTop = true
                            local name = Instance.new('TextLabel',bill)
                            name.Font = "GothamBold"
                            name.FontSize = "Size14"
                            name.TextWrapped = true
                            name.Size = UDim2.new(1,0,1,0)
                            name.TextYAlignment = 'Top'
                            name.BackgroundTransparency = 1
                            name.TextStrokeTransparency = 0.5
                            name.TextColor3 = Color3.fromRGB(255, 0, 0)
                            name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
                        else
                            v.Handle['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
                        end
                    end
                else
                    if v.Handle:FindFirstChild('NameEsp'..Number) then
                        v.Handle:FindFirstChild('NameEsp'..Number):Destroy()
                        end
                end
            end)
        end
    end
    
    function UpdateFlowerEsp() 
        for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
            pcall(function()
                if v.Name == "Flower2" or v.Name == "Flower1" then
                    if FlowerESP then 
                        if not v:FindFirstChild('NameEsp'..Number) then
                            local bill = Instance.new('BillboardGui',v)
                            bill.Name = 'NameEsp'..Number
                            bill.ExtentsOffset = Vector3.new(0, 1, 0)
                            bill.Size = UDim2.new(1,200,1,30)
                            bill.Adornee = v
                            bill.AlwaysOnTop = true
                            local name = Instance.new('TextLabel',bill)
                            name.Font = "GothamBold"
                            name.FontSize = "Size14"
                            name.TextWrapped = true
                            name.Size = UDim2.new(1,0,1,0)
                            name.TextYAlignment = 'Top'
                            name.BackgroundTransparency = 1
                            name.TextStrokeTransparency = 0.5
                            name.TextColor3 = Color3.fromRGB(255, 0, 0)
                        if v.Name == "Flower1" then 
                            name.Text = ("Blue Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                            name.TextColor3 = Color3.fromRGB(0, 0, 255)
                        end
                        if v.Name == "Flower2" then
                            name.Text = ("Red Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                            name.TextColor3 = Color3.fromRGB(255, 0, 0)
                        end
                    else
                        v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
                    end
                    else
                        if v:FindFirstChild('NameEsp'..Number) then
                            v:FindFirstChild('NameEsp'..Number):Destroy()
                        end
                    end
                end   
            end)
        end
    end
    
    function InfAb()
        if InfAbility then
            if not game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility") then
                local inf = Instance.new("ParticleEmitter")
                inf.Acceleration = Vector3.new(0,0,0)
                inf.Archivable = true
                inf.Drag = 50
                inf.EmissionDirection = Enum.NormalId.Top
                inf.Enabled = true
                inf.Lifetime = NumberRange.new(0.2,0.2)
                inf.LightInfluence = 0
                inf.LockedToPart = true
                inf.Name = "Agility"
                inf.Rate = 500
                local numberKeypoints2 = {
                    NumberSequenceKeypoint.new(0, 0);
                    NumberSequenceKeypoint.new(1, 4); 
                }
                inf.Size = NumberSequence.new(numberKeypoints2)
                inf.RotSpeed = NumberRange.new(999, 9999)
                inf.Rotation = NumberRange.new(0, 0)
                inf.Speed = NumberRange.new(30, 30)
                inf.SpreadAngle = Vector2.new(360,360)
                inf.Texture = "rbxassetid://7157487174"
                inf.VelocityInheritance = 0
                inf.ZOffset = 2
                inf.Transparency = NumberSequence.new(0)
                inf.Color = ColorSequence.new(Color3.fromRGB(255,255,255),Color3.fromRGB(0,0,0))
                inf.Parent = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
            end
        else
            if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility") then
                game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility"):Destroy()
            end
        end
    end
    
    local LocalPlayer = game:GetService'Players'.LocalPlayer
    local originalstam = LocalPlayer.Character.Energy.Value
    function infinitestam()
        LocalPlayer.Character.Energy.Changed:connect(function()
            if InfiniteEnergy then
                LocalPlayer.Character.Energy.Value = originalstam
            end 
        end)
    end
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if InfiniteEnergy then
                    wait(0.3)
                    originalstam = LocalPlayer.Character.Energy.Value
                    infinitestam()
                end
            end
        end)
    end)
    
    function NoDodgeCool()
        if nododgecool then
            for i,v in next, getgc() do
                if game:GetService("Players").LocalPlayer.Character.Dodge then
                    if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.Character.Dodge then
                        for i2,v2 in next, getupvalues(v) do
                            if tostring(v2) == "0.4" then
                            repeat wait(.1)
                                setupvalue(v,i2,0)
                            until not nododgecool
                            end
                        end
                    end
                end
            end
        end
    end
    
    local flying = false  -- สถานะการบินเริ่มต้นเป็น false

    -- ฟังก์ชันเริ่มการบิน
    function fly()
        local userInputService = game:GetService("UserInputService")
        local mouse = game:GetService("Players").LocalPlayer:GetMouse()
        local localPlayer = game:GetService("Players").LocalPlayer
        local torso = localPlayer.Character:WaitForChild("HumanoidRootPart")
        local speedSET = 25
        local keys = {a = false, d = false, w = false, s = false}
        local speed = 0
    
        local function start()
            local pos = Instance.new("BodyPosition", torso)
            local gyro = Instance.new("BodyGyro", torso)
            pos.Name = "EPIXPOS"
            pos.maxForce = Vector3.new(math.huge, math.huge, math.huge)
            pos.position = torso.Position
            gyro.maxTorque = Vector3.new(9e9, 9e9, 9e9)
            gyro.CFrame = torso.CFrame
    
            repeat
                wait()
                localPlayer.Character.Humanoid.PlatformStand = true
                local new = gyro.CFrame - gyro.CFrame.p + pos.position
    
                if not keys.w and not keys.s and not keys.a and not keys.d then
                    speed = 1
                end
    
                if keys.w then
                    new = new + workspace.CurrentCamera.CoordinateFrame.lookVector * speed
                    speed = speed + speedSET
                end
                if keys.s then
                    new = new - workspace.CurrentCamera.CoordinateFrame.lookVector * speed
                    speed = speed + speedSET
                end
                if keys.d then
                    new = new * CFrame.new(speed, 0, 0)
                    speed = speed + speedSET
                end
                if keys.a then
                    new = new * CFrame.new(-speed, 0, 0)
                    speed = speed + speedSET
                end
                if speed > speedSET then
                    speed = speedSET
                end
                pos.position = new.p
    
                if keys.w then
                    gyro.CFrame = workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad(speed * 15), 0, 0)
                elseif keys.s then
                    gyro.CFrame = workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(math.rad(speed * 15), 0, 0)
                else
                    gyro.CFrame = workspace.CurrentCamera.CoordinateFrame
                end
            until not flying
    
            if gyro then
                gyro:Destroy()
            end
            if pos then
                pos:Destroy()
            end
            flying = false
            localPlayer.Character.Humanoid.PlatformStand = false
            speed = 0
        end
    
        local function onInputBegan(input, gameProcessed)
            if gameProcessed then return end
    
            if input.UserInputType == Enum.UserInputType.Keyboard then
                if input.KeyCode == Enum.KeyCode.W then
                    keys.w = true
                elseif input.KeyCode == Enum.KeyCode.S then
                    keys.s = true
                elseif input.KeyCode == Enum.KeyCode.A then
                    keys.a = true
                elseif input.KeyCode == Enum.KeyCode.D then
                    keys.d = true
                elseif input.KeyCode == Enum.KeyCode.Space then
                    -- ปิดการบินเมื่อกดปุ่ม Space
                    if flying then
                        unFly()  -- เรียกฟังก์ชัน unFly เพื่อหยุดการบิน
                    end
                end
            elseif input.UserInputType == Enum.UserInputType.Touch then
                -- เพิ่มการตรวจจับการสัมผัสหน้าจอ (เช่น swipe)
                local touchPos = input.Position
                if touchPos.X < game:GetService("Players").LocalPlayer.PlayerGui.AbsoluteSize.X / 2 then
                    keys.a = true
                else
                    keys.d = true
                end
            end
        end
    
        local function onInputEnded(input)
            if input.UserInputType == Enum.UserInputType.Keyboard then
                if input.KeyCode == Enum.KeyCode.W then
                    keys.w = false
                elseif input.KeyCode == Enum.KeyCode.S then
                    keys.s = false
                elseif input.KeyCode == Enum.KeyCode.A then
                    keys.a = false
                elseif input.KeyCode == Enum.KeyCode.D then
                    keys.d = false
                end
            elseif input.UserInputType == Enum.UserInputType.Touch then
                -- ปล่อยสัมผัสเมื่อปล่อยนิ้ว
                keys.a = false
                keys.d = false
            end
        end
    
        userInputService.InputBegan:Connect(onInputBegan)
        userInputService.InputEnded:Connect(onInputEnded)
    
        -- เริ่มการบินเมื่อฟังก์ชัน fly() ถูกเรียกใช้
        flying = true
        start()
    end
    
    -- ฟังก์ชันสำหรับหยุดการบิน (unFly)
    function unFly()
        flying = false  -- เปลี่ยนสถานะการบินเป็น false
        local localPlayer = game:GetService("Players").LocalPlayer
        localPlayer.Character.Humanoid.PlatformStand = false  -- ปลดล็อกการควบคุมจากการบิน
    end
    
    

    local isAttacking = false -- ตัวแปรใช้ตรวจสอบสถานะการโจมตี

    function Click()
        if isAttacking then return end  -- ถ้ากำลังโจมตีอยู่แล้วจะไม่ทำงานซ้ำ
        isAttacking = true  -- เปิดการโจมตี
    
        while isAttacking do
            local enemies = workspace.Enemies:GetChildren()
            local args = {
                [1] = nil,
                [2] = {}
            }
    
            -- ตรวจสอบศัตรูที่สามารถโจมตีได้
            for i, enemy in ipairs(enemies) do
                if enemy:FindFirstChild("HumanoidRootPart") and enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 then
                    table.insert(args[2], {
                        [1] = enemy,
                        [2] = enemy.HumanoidRootPart
                    })
    
                    if not args[1] then
                        args[1] = enemy.HumanoidRootPart
                    end
                end
            end
    
            -- ส่งข้อมูลการโจมตีถ้ามีศัตรูที่สามารถโจมตีได้
            if args[1] then
                local attackArgs = {
                    [1] = 1 -- ตัวเลือกการโจมตี
                }
                game:GetService("ReplicatedStorage").Modules.Net:FindFirstChild("RE/RegisterAttack"):FireServer(unpack(attackArgs))
    
                -- ส่งข้อมูลการโจมตีที่เกี่ยวข้องกับศัตรู
                game:GetService("ReplicatedStorage").Modules.Net:FindFirstChild("RE/RegisterHit"):FireServer(unpack(args))
            end
    
            task.wait(0)  -- ใช้ task.wait(0) เพื่อให้ลูปทำงานได้เร็วที่สุดเท่าที่จะทำได้
        end
    end
    
    -- ตัวอย่างการหยุดการโจมตี
    function StopClick()
        isAttacking = false  -- หยุดการโจมตี
    end
    
    
function UnSit()
    if game.Players.LocalPlayer.Character.Humanoid.Sit == true then game.Players.LocalPlayer.Character.Humanoid.Sit = false end end

    
    function AutoHaki()
        if not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HasBuso") then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
        end
    end
    
    function UnEquipWeapon(Weapon)
        if game.Players.LocalPlayer.Character:FindFirstChild(Weapon) then
            NotAutoEquip = true
            wait(.5)
            game.Players.LocalPlayer.Character:FindFirstChild(Weapon).Parent = game.Players.LocalPlayer.Backpack
            wait(.1)
            NotAutoEquip = false
        end
    end
    
    function EquipWeapon(ToolSe)
        if not NotAutoEquip then
            if game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe) then
                Tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
                wait(.1)
                game.Players.LocalPlayer.Character.Humanoid:EquipTool(Tool)
            end
        end
    end
   

    function Tween(Pos)
        Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
        if game.Players.LocalPlayer.Character.Humanoid.Sit == true then game.Players.LocalPlayer.Character.Humanoid.Sit = false end
        pcall(function() tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/250, Enum.EasingStyle.Linear),{CFrame = Pos}) end)
        tween:Play()
        if Distance <= 250 then
            tween:Cancel()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Pos
        end
        if StopTween == true then
            tween:Cancel()
            Clip = false
        end
    end

    function TweenSit(Pos)
        Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
        pcall(function() tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/250, Enum.EasingStyle.Linear),{CFrame = Pos}) end)
        tween:Play()
        if Distance <= 250 then
            tween:Cancel()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Pos
        end
        if StopTween == true then
            tween:Cancel()
            Clip = false
    end
end

    
    function TP0(Pos)
        Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
        if game.Players.LocalPlayer.Character.Humanoid.Sit == true then game.Players.LocalPlayer.Character.Humanoid.Sit = false end
        pcall(function() tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/120000, Enum.EasingStyle.Linear),{CFrame = Pos}) end)
        tween:Play()
        if Distance <= 120000 then
            tween:Cancel()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Pos
        end
        if StopTween == true then
            tween:Cancel()
            Clip = false
        end
    end
    
    function GetDistance(target)
        return math.floor((target.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude)
    end
    
    function TP(Pos)
        Distance = (Pos.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
        if Distance < 250 then
            Speed = 600
        elseif Distance >= 1000 then
            Speed = 200
        end
        game:GetService("TweenService"):Create(
            game:GetService("Players").LocalPlayer.Character.HumanoidRootPart,
            TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
            {CFrame = Pos}
        ):Play()
        Clip = true
        wait(Distance/Speed)
        Clip = false
    end
    
    spawn(function()
        pcall(function()
            while wait() do
                if Tp_To_Prehistoric_Island or Tp_To_Mystic_Island or Auto_Walk_Bost or Mini_Tusk or MobAura or AutoDoughtBoss or Auto_Cursed_Dual_Katana or Auto_Sea_Event or AutoDoughKing or Auto_Open_Dough_Dungeon or AutoFarmFruit or dv2 or Heats or Auto_Open_Dough_Dungeon or AutoLawBoss or human or AutoDoughtBoss or ghoul or Candy or Gear or dv2 or Cocoa or Chest1 or Ectoplasm or AutoRedioactive or AutoSaw or Chest or Sea1 or Sea or Magma or Fish or My or God or combo or Auto_Bone2 or Auto_DungeonMobAura or AutoFarmChest or AutoFarmBossHallow or AutoFarmSwanGlasses or AutoLongSword or AutoBlackSpikeycoat or AutoElectricClaw or AutoFarmGunMastery or AutoHolyTorch or AutoLawRaid or AutoFarmBoss or AutoTwinHooks or AutoOpenSwanDoor or AutoDragon_Trident or AutoSaber or NOCLIP or AutoFarmFruitMastery or AutoFarmGunMastery or TeleportIsland or Auto_EvoRace or AutoFarmAllMsBypassType or AutoObservationv2 or AutoMusketeerHat or AutoEctoplasm or AutoRengoku or Auto_Rainbow_Haki or AutoObservation or AutoDarkDagger or Safe_Mode or MasteryFruit or AutoBudySword or AutoAllBoss or Auto_Bounty or AutoSharkman or Auto_Mastery_Fruit or Auto_Mastery_Gun or Auto_Dungeon or Auto_Cavender or Auto_Pole or Auto_Kill_Ply or Auto_Factory or AutoSecondSea or AutoBartilo or Auto_DarkBoss or AutoFarm or Clip or AutoElitehunter or AutoThirdSea or Auto_Bone == true then
					local character = game:GetService("Players").LocalPlayer.Character
					local humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")
					if humanoidRootPart and not humanoidRootPart:FindFirstChild("BodyClip") then
						local Noclip = Instance.new("BodyVelocity")
						Noclip.Name = "BodyClip"
						Noclip.Parent = humanoidRootPart
						Noclip.MaxForce = Vector3.new(100000, 100000, 100000)
						Noclip.Velocity = Vector3.new(0, 0, 0)
					end
				else
					local character = game:GetService("Players").LocalPlayer.Character
					local humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")
					if humanoidRootPart then
						local bodyClip = humanoidRootPart:FindFirstChild("BodyClip")
						if bodyClip then
							bodyClip:Destroy()
						end
					end
				end
			end
		end)
	end)
    
function GetWeaponInventory(Weaponname)
for i, v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
if type(v) == "table" then
    if v.Type == "Sword" then
        if v.Name == Weaponname then
            return true
        end
    end
end
end
return false
end


function GetMaterial(matname)
for i, v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
if type(v) == "table" then
    if v.Type == "Material" then
        if v.Name == matname then
            return v.Count
        end
    end
end
end
return 0
end

    spawn(function()
        pcall(function()
            game:GetService("RunService").Stepped:Connect(function()
                if Tp_To_Prehistoric_Island or Tp_To_Mystic_Island or Auto_Walk_Bost or Mini_Tusk or MobAura or AutoDoughtBoss or Auto_Cursed_Dual_Katana or Auto_Sea_Event or AutoDoughKing or Auto_Open_Dough_Dungeon or AutoFarmFruit or dv2 or Heats or Auto_Open_Dough_Dungeon or AutoLawBoss or human or AutoDoughtBoss or ghoul or Candy or Gear or dv2 or Cocoa or Chest1 or Ectoplasm or AutoRedioactive or AutoSaw or Chest or Sea1 or Sea or Magma or Fish or My or God or combo or Auto_Bone2 or Auto_DungeonMobAura or AutoFarmChest or AutoFarmBossHallow or AutoFarmSwanGlasses or AutoLongSword or AutoBlackSpikeycoat or AutoElectricClaw or AutoFarmGunMastery or AutoHolyTorch or AutoLawRaid or AutoFarmBoss or AutoTwinHooks or AutoOpenSwanDoor or AutoDragon_Trident or AutoSaber or NOCLIP or AutoFarmFruitMastery or AutoFarmGunMastery or TeleportIsland or Auto_EvoRace or AutoFarmAllMsBypassType or AutoObservationv2 or AutoMusketeerHat or AutoEctoplasm or AutoRengoku or Auto_Rainbow_Haki or AutoObservation or AutoDarkDagger or Safe_Mode or MasteryFruit or AutoBudySword or AutoAllBoss or Auto_Bounty or AutoSharkman or Auto_Mastery_Fruit or Auto_Mastery_Gun or Auto_Dungeon or Auto_Cavender or Auto_Pole or Auto_Kill_Ply or Auto_Factory or AutoSecondSea or AutoBartilo or Auto_DarkBoss or AutoFarm or Clip or AutoElitehunter or AutoThirdSea or Auto_Bone == true then
                    for _, v in pairs(game:GetService("Players").LocalPlayer.Character:GetDescendants()) do
                        if v:IsA("BasePart") then
                            v.CanCollide = false    
                        end
                    end
                end
            end)
        end)
    end)
    
    spawn(function()
        while wait() do
            if Tp_To_Prehistoric_Island or Tp_To_Mystic_Island or Auto_Walk_Bost or Mini_Tusk or MobAura or AutoDoughtBoss or Auto_Cursed_Dual_Katana or Auto_Sea_Event or AutoDoughKing or Auto_Open_Dough_Dungeon or AutoFarmFruit or dv2 or Heats or Auto_Open_Dough_Dungeon or AutoLawBoss or human or AutoDoughtBoss or ghoul or Candy or Gear or dv2 or Cocoa or Chest1 or Ectoplasm or AutoRedioactive or AutoSaw or Chest or Sea1 or Sea or Magma or Fish or My or God or combo or Auto_Bone2 or Auto_DungeonMobAura or AutoFarmChest or AutoFarmBossHallow or AutoFarmSwanGlasses or AutoLongSword or AutoBlackSpikeycoat or AutoElectricClaw or AutoFarmGunMastery or AutoHolyTorch or AutoLawRaid or AutoFarmBoss or AutoTwinHooks or AutoOpenSwanDoor or AutoDragon_Trident or AutoSaber or NOCLIP or AutoFarmFruitMastery or AutoFarmGunMastery or TeleportIsland or Auto_EvoRace or AutoFarmAllMsBypassType or AutoObservationv2 or AutoMusketeerHat or AutoEctoplasm or AutoRengoku or Auto_Rainbow_Haki or AutoObservation or AutoDarkDagger or Safe_Mode or MasteryFruit or AutoBudySword or AutoAllBoss or Auto_Bounty or AutoSharkman or Auto_Mastery_Fruit or Auto_Mastery_Gun or Auto_Dungeon or Auto_Cavender or Auto_Pole or Auto_Kill_Ply or Auto_Factory or AutoSecondSea or AutoBartilo or Auto_DarkBoss or AutoFarm or Clip or AutoElitehunter or AutoThirdSea or Auto_Bone == true then
                pcall(function()
                    game:GetService("ReplicatedStorage").Remotes.CommE:FireServer("Ken",true)
                end)
            end    
        end
    end)
    
    function StopTween(target)
        if not target then
            StopTween = true
            wait()
            Tween(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
            wait()
            if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") or game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyVelocity1") then
                game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
                game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyVelocity1"):Destroy();
            end
            StopTween = false
            Clip = false
        end
    end
    
    task.spawn(function()
    game:GetService("RunService").Stepped:Connect(function()
        pcall(function()
            --[World 1]
            if Auto_Win_Trial then
if syn or not syn then
					setfflag("HumanoidParallelRemoveNoPhysics", "False")
					setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
					game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
					if game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit == true then
						game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit = false
					end
				else
					if game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
						if not game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyVelocity1") then
							if game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit == true then
								game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit = false
							end
							local BodyVelocity = Instance.new("BodyVelocity")
							BodyVelocity.Name = "BodyVelocity1"
							BodyVelocity.Parent =  game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
							BodyVelocity.MaxForce = Vector3.new(10000, 10000, 10000)
							BodyVelocity.Velocity = Vector3.new(0, 0, 0)
						end
					end
					for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
						if v:IsA("BasePart") then
							v.CanCollide = false    
						end
					end
				end
			else
				if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyVelocity1") then
					game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyVelocity1"):Destroy();
				end
			end
		end)
	end)
end)
    
    spawn(function()
        pcall(function()
            while wait() do
                for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do  
                    if v:IsA("Tool") then
                        if v:FindFirstChild("RemoteFunctionShoot") then 
                            SelectWeaponGun = v.Name
                        end
                    end
                end
            end
        end)
    end)
    
    




    local RenUi = Update:AddWindow("RebornXer Hub","10039618734",Enum.KeyCode.RightControl)

    local Main = RenUi:AddTab("Main","6026568198")
    local Sea = RenUi:AddTab("Sea Event","")
    local Teleport = RenUi:AddTab("Island","6035190846")
    local Shop = RenUi:AddTab("Shop","6031265976")
    local Misc = RenUi:AddTab("Misc","6034509993")
    local Setting = RenUi:AddTab("","")
    
    local S = RenUi:AddTabH("Top","14134158045")
    

    
    
   
    
    Main:AddSeperatorLeft("Info")
    Main:AddLabelLeft("Wecome To RebornXer Hub Script")
    Date = os.date("%d".." ".."%B".." ".."%Y")
    Main:AddLabelLeft("Day : "..Date)
   Main:AddLineLeft("")
FM = Main:AddLabelLeft("")
        
spawn(function()
            while task.wait() do
                pcall(function()
                    if game:GetService("Lighting").Sky.MoonTextureId=="http://www.roblox.com/asset/?id=9709149431" then
                        FM:Set("Full Moon : 100%")
                    elseif game:GetService("Lighting").Sky.MoonTextureId=="http://www.roblox.com/asset/?id=9709149052" then
                        FM:Set("Full Moon : 75%")
                    elseif game:GetService("Lighting").Sky.MoonTextureId=="http://www.roblox.com/asset/?id=9709143733" then
                        FM:Set("Full Moon : 50%")
                    elseif game:GetService("Lighting").Sky.MoonTextureId=="http://www.roblox.com/asset/?id=9709150401" then
                        FM:Set("Full Moon : 25%")
                    elseif game:GetService("Lighting").Sky.MoonTextureId=="http://www.roblox.com/asset/?id=9709149680" then
                        FM:Set("Full Moon : 15%")
                    else
                        FM:Set("Full Moon : 0%")
                    end
                end)
            end
        end)



Main:AddTextboxLeft("job id ","...",true,function(s)
    jobid = s
    end)
    
    Main:AddButtonLeft("Copy Job id",function()
    setclipboard(tostring(game.JobId))
    end)
                
         Main:AddButtonLeft("Join Job",function(s)
        game:GetService("TeleportService"):TeleportToPlaceInstance(7449423635, jobid)
        end)

    
    Main:AddSeperatorRight("Setting")

 
  WeaponList = {}
    
    for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do  
        if v:IsA("Tool") then
            table.insert(WeaponList ,v.Name)
        end
    end
    
    local SelectWeapona = Main:AddDropdownRight("Select Weapon",WeaponList,function(value)
        SelectWeapon = value
    end)
    
    Main:AddButtonRight("Reset Weapon",function()
        SelectWeapona:Clear()
        for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do  
            SelectWeapona:Add(v.Name)
        end
    end)
    
    
    
    Main:AddToggleRight("Remove Effect",Remove_Effect,function(value)
        Remove_Effect = value
    end)
    
    local ReplicatedStorage = game:GetService("ReplicatedStorage")
    local originalFX = nil
    
    spawn(function()
        pcall(function()
            while wait() do
                if Remove_Effect then
                    if ReplicatedStorage:FindFirstChild("FX") then
                        -- เก็บสำเนาของ FX ก่อน Destroy
                        originalFX = ReplicatedStorage:FindFirstChild("FX"):Clone()
                        ReplicatedStorage:FindFirstChild("FX"):Destroy()
                    end
                else
                    if not ReplicatedStorage:FindFirstChild("FX") and originalFX then
                        originalFX.Parent = ReplicatedStorage
                        originalFX = nil
                    end
                end
            end
        end)
    end)
    
    spawn(function()
      while wait() do
      if BlackScreen then
        for i, v in pairs(game.Workspace["_WorldOrigin"]:GetChildren()) do
            if v.Name == "CurvedRing" or v.Name == "SlashHit" or v.Name == "DamageCounter" or v.Name == "SwordSlash" or v.Name == "SlashTail" or v.Name == "Sounds" then
                v:Destroy() 
            end
        end
    end
    end
end) 

local player = game:GetService("Players").LocalPlayer

local blackscreen = function(enable)
    local playerGui = player:WaitForChild("PlayerGui")
    if not enable then
        local sUi = playerGui:FindFirstChild("Blackscreen")
        if sUi then sUi:Destroy() end
        return
    elseif playerGui:FindFirstChild("Blackscreen") then
        return
    end
    local sUi = Instance.new("ScreenGui", playerGui)
    sUi.Name = "Blackscreen"
    sUi.DisplayOrder = -727

    local uiFrame = Instance.new("Frame", sUi)
    uiFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    uiFrame.Size = UDim2.new(0, 72727, 0, 72727)
    uiFrame.Position = UDim2.new(0, 0, -5, 0)
end
    
        Main:AddToggleRight("Black Screen",BlackScreen,function(value)
    BlackScreen = value
if BlackScreen == true then
    game:GetService("RunService"):Set3dRenderingEnabled(false)
    blackscreen(true)
elseif BlackScreen == false then
    game:GetService("RunService"):Set3dRenderingEnabled(true)
    blackscreen(false)
end
end)
FastAttack = true
     Main:AddToggleRight("Fast Attack",FastAttack,function(a)
 FastAttack = a
    end) 

spawn(function()
    while wait() do
        pcall(function()
            if FastAttack then
                Click()
            else
                StopClick()
            end
        end)
    end
end)

GunAttack = true
     Main:AddToggleRight("Gun Attack",GunAttack,function(a)
 GunAttack = a
    end) 
    spawn(function()
        while true do
            pcall(function()
                if GunAttack then
                    -- โจมตีศัตรู
                    for _, enemy in pairs(workspace.Enemies:GetChildren()) do
                        if enemy:FindFirstChild("HumanoidRootPart") then
                            local targetPart = enemy:FindFirstChildOfClass("Accessory") and enemy:FindFirstChildOfClass("Accessory").Handle
                                or enemy:FindFirstChild("HumanoidRootPart")
    
                            if targetPart then
                                local args = {
                                    [1] = enemy.HumanoidRootPart.Position,
                                    [2] = { targetPart }
                                }
                                game:GetService("ReplicatedStorage").Modules.Net:FindFirstChild("RE/ShootGunEvent"):FireServer(unpack(args))
                            end
                        end
    
                        -- ตรวจสอบว่าเป็นเรือและมีชิ้นส่วน Plane.037
                        if enemy.Body:FindFirstChild("Part") then
                            local shipPart = enemy.Body:FindFirstChild("Part")
                            local shipCFrame = shipPart.CFrame -- ใช้ CFrame ของชิ้นส่วนเรือ
                            local shipArgs = {
                                [1] = shipCFrame,
                                [2] = { shipPart }
                            }
                            game:GetService("ReplicatedStorage").Modules.Net:FindFirstChild("RE/ShootGunEvent"):FireServer(unpack(shipArgs))
                        end
                    end
    
                    -- ยิงแบบสุ่มตำแหน่ง
                    local randomCFrame = CFrame.new(
                        math.random(-2000, 2000),
                        math.random(50, 150),
                        math.random(-2000, 2000)
                    )
                    local randomArgs = {
                        [1] = randomCFrame,
                        [2] = {}
                    }
                    game:GetService("ReplicatedStorage").Modules.Net:FindFirstChild("RE/ShootGunEvent"):FireServer(unpack(randomArgs))
                end
            end)
            task.wait(0) -- ลดความถี่การวนลูป
        end
    end)
    
    

    BringMon = true
    Main:AddToggleRight("BringMon",BringMon,function(value)
        BringMon = value
    end)
    
     spawn(function()
        while task.wait() do
            pcall(function()
                if BringMon then
                    CheckQuest()
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if AutoFarm and StartMagnet and v.Name == NameMon and (NameMon == "Factory Staff" or NameMon == "Monkey" or NameMon == "Dragon Crew Warrior" or NameMon == "Dragon Crew Archer") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and (v.HumanoidRootPart.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 220 then
                            v.Humanoid:ChangeState(11)
                            v.HumanoidRootPart.CanCollide = false
                            v.Head.CanCollide = false
                            v.HumanoidRootPart.CFrame = PosMon
                            if v.Humanoid:FindFirstChild("Animator") then
                                v.Humanoid.Animator:Destroy()
                            end
                            sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                        elseif AutoFarm and StartMagnet and v.Name == NameMon and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and (v.HumanoidRootPart.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 275 then
                            v.HumanoidRootPart.CFrame = PosMon
                            v.Humanoid:ChangeState(11)
                            v.HumanoidRootPart.CanCollide = false
                            v.Head.CanCollide = false
                            if v.Humanoid:FindFirstChild("Animator") then
                                v.Humanoid.Animator:Destroy()
                            end
                            sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                        end
                        if AutoEctoplasm and StartEctoplasmMagnet then
                            if string.find(v.Name, "Ship") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and (v.HumanoidRootPart.Position - EctoplasmMon.Position).Magnitude <= 250 then
                               
                                v.HumanoidRootPart.CFrame = EctoplasmMon
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if AutoRengoku and StartRengokuMagnet then
                            if (v.Name == "Snow Lurker [Lv. 1375]" or v.Name == "Arctic Warrior [Lv. 1350]") and (v.HumanoidRootPart.Position - RengokuMon.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = RengokuMon
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if AutoMusketeerHat and StartMagnetMusketeerhat then
                            if v.Name == "Forest Pirate [Lv. 1825]" and (v.HumanoidRootPart.Position - MusketeerHatMon.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = MusketeerHatMon
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if Auto_EvoRace and StartEvoMagnet then
                            if v.Name == "Zombie [Lv. 950]" and (v.HumanoidRootPart.Position - PosMonEvo.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonEvo
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if AutoBartilo and AutoBartiloBring then
                            if v.Name == "Swan Pirate [Lv. 775]" and (v.HumanoidRootPart.Position - PosMonBarto.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonBarto
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if AutoFarmFruitMastery and StartMasteryFruitMagnet then
                            if v.Name == "Monkey [Lv. 14]" then
                                if (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.Humanoid:ChangeState(11)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryFruit
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            elseif v.Name == "Factory Staff" then
                                if (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(1,1,1)
                                    v.Humanoid:ChangeState(11)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryFruit
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            elseif v.Name == Mon then
                                if (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(1,1,1)
                                    v.Humanoid:ChangeState(11)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryFruit
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            end
                        end
                        if AutoFarmGunMastery and StartMasteryGunMagnet then
                            if v.Name == "Monkey [Lv. 14]" then
                                if (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(2,2,2)
                                    v.Humanoid:ChangeState(11)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryGun
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            elseif v.Name == "Factory Staff" then
                                if (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(2,2,2)
                                    v.Humanoid:ChangeState(11)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryGun
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            elseif v.Name == Mon then
                                if (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    v.HumanoidRootPart.Size = Vector3.new(2,2,2)
                                    v.Humanoid:ChangeState(11)
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    v.HumanoidRootPart.CFrame = PosMonMasteryGun
                                    if v.Humanoid:FindFirstChild("Animator") then
                                        v.Humanoid.Animator:Destroy()
                                    end
                                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                end
                            end
                        end
                        if Auto_Bone and StartMagnetBoneMon then
                            if (v.Name == "Reborn Skeleton [Lv. 1975]" or v.Name == "Living Zombie [Lv. 2000]" or v.Name == "Demonic Soul [Lv. 2025]" or v.Name == "Posessed Mummy [Lv. 2050]") and (v.HumanoidRootPart.Position - PosMonBone.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonBone
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                      end
                        if Auto_Bone2 and StartMagnetBoneMon2 then
                            if (v.HumanoidRootPart.Position - PosMonBone2.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonBone2
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if AutoFarmFruit and StartMagnetBoneMon2 then
                            if (v.HumanoidRootPart.Position - PosMonBone2.Position).Magnitude <= 200 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonBone2
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if AutoDoughtBoss and MagnetDought then
                            if (v.HumanoidRootPart.Position - PosMonDoughtOpenDoor.Position).Magnitude <= 230 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonDoughtOpenDoor
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if AutoDoughtBoss3 and MagnetDought3 then
                            if (v.HumanoidRootPart.Position - PosMonDoughtOpenDoor3.Position).Magnitude <= 230 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonDoughtOpenDoor3
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if dv2_AutoMon and MagnetDought3 then
                            if (v.HumanoidRootPart.Position - PosMonDoughtOpenDoor3.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonDoughtOpenDoor3
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if God and StartMagnetdragon then
                            if (v.HumanoidRootPart.Position - PosMondragon.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMondragon
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if human and StartMagnethuman then
                            if (v.HumanoidRootPart.Position - PosMondragon.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonhuman
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if Candy and StartMagnetCandy then
                            if (v.HumanoidRootPart.Position - PosMonCandy.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonCandy
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if My and StartMagnetMy then
                            if (v.HumanoidRootPart.Position - PosMonMy.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonMy
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if Ectoplasm and StartMagnetE then
                            if (v.HumanoidRootPart.Position - PosMonE.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonE
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if Heats and StartMagnetHeats then
                            if (v.HumanoidRootPart.Position - PosMonHeats.Position).Magnitude <= 300 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.HumanoidRootPart.Size = Vector3.new(1,1,1)
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonHeats
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if Fish and StartMaootPart.PositgnetFish then
                            if (v.HumanoidRion - PosMonFish.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonFish
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                         if Iron and StartMagnetIron then
                            if (v.HumanoidRootPart.Position - PosMonIron.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonIron
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if Mini_Tusk and StartMagnetMini_Tusk then
                            if (v.HumanoidRootPart.Position - PosMonMini_Tusk.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonMini_Tusk
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                         if Magma and StartMagnetMagma then
                            if (v.HumanoidRootPart.Position - PosMonMagma.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonMagma
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                         end
                         if ghoul and StartMagnetghoul then
                            if (v.HumanoidRootPart.Position - PosMonghoul.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonghoul
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                         end
                    if Cocoa and StartMagnetCocoa then
                            if (v.HumanoidRootPart.Position - PosMonCocoa.Position).Magnitude <= 300 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonCocoa
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                    end
                    if dv and StartMagnetCocoa then
                            if (v.HumanoidRootPart.Position - PosMonCocoa.Position).Magnitude <= 300 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                               
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonCocoa
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if dv2 and StartMagnetdv2 then
                            if (v.HumanoidRootPart.Position - PosMondv2.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMondv2
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                        if AutoCandy and StartMagnetCandy then
                            if (v.HumanoidRootPart.Position - PosMonCandy.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                v.Humanoid:ChangeState(11)
                                v.HumanoidRootPart.CanCollide = false
                                v.Head.CanCollide = false
                                v.HumanoidRootPart.CFrame = PosMonCandy
                                if v.Humanoid:FindFirstChild("Animator") then
                                    v.Humanoid.Animator:Destroy()
                                end
                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    
    
    Main:AddLineRight("")
    
    Main:AddSeperatorRight("Melee")
    
    Main:AddToggleRight("Auto Superhuman",AutoSuperhuman,function(value)
        AutoSuperhuman = value
    end)
    
    spawn(function()
        pcall(function()
            while wait() do 
                if AutoSuperhuman then
                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Combat") or game.Players.LocalPlayer.Character:FindFirstChild("Combat") and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 150000 then
                        UnEquipWeapon("Combat")
                        wait(.1)
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
                    end   
                    if game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") then
                        SelectWeapon = "Superhuman"
                    end  
                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") or game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") or game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") then
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value <= 299 then
                            SelectWeapon = "Black Leg"
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value <= 299 then
                            SelectWeapon = "Electro"
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value <= 299 then
                            SelectWeapon = "Fishman Karate"
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 299 then
                            SelectWeapon = "Dragon Claw"
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 300000 then
                            UnEquipWeapon("Black Leg")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
                        end
                        if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 300000 then
                            UnEquipWeapon("Black Leg")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 750000 then
                            UnEquipWeapon("Electro")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
                        end
                        if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 750000 then
                            UnEquipWeapon("Electro")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 300 and game:GetService("Players")["Localplayer"].Data.Fragments.Value >= 1500 then
                            UnEquipWeapon("Fishman Karate")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","1")
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2") 
                        end
                        if game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate").Level.Value >= 300 and game:GetService("Players")["Localplayer"].Data.Fragments.Value >= 1500 then
                            UnEquipWeapon("Fishman Karate")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","1")
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2") 
                        end
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 3000000 then
                            UnEquipWeapon("Dragon Claw")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
                        end
                        if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 300 and game:GetService("Players")["LocalPlayer"].Data.Beli.Value >= 3000000 then
                            UnEquipWeapon("Dragon Claw")
                            wait(.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
                        end 
                    end
                end
            end
        end)
    end)
    
    Main:AddToggleRight("Auto DeathStep",AutoDeathStep,function(value)
        AutoDeathStep = value
    end)
    
    spawn(function()
        while wait() do wait()
            if AutoDeathStep then
                if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Death Step") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Death Step") then
                    if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 450 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
                        SelectWeapon = "Death Step"
                    end  
                    if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 450 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
                        SelectWeapon = "Death Step"
                    end  
                    if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value <= 449 then
                        SelectWeapon = "Black Leg"
                    end 
                else 
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
                end
            end
        end
    end)
    
    Main:AddToggleRight("Auto Sharkman",AutoSharkman,function(value)
        AutoSharkman = value
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if AutoSharkman then
--true
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
                    if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate"), "keys") then  
                        if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Water Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Water Key") then
                            Tween(CFrame.new(-2604.6958, 239.432526, -10315.1982, 0.0425701365, 0, -0.999093413, 0, 1, 0, 0.999093413, 0, 0.0425701365))
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
end
                        elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate").Level.Value >= 400 then
                        else 
                            Ms = "Tide Keeper"
                            if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then   
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if v.Name == Ms then    
                                        OldCFrameShark = v.HumanoidRootPart.CFrame
                                        repeat task.wait()
                                            AutoHaki()
                                            EquipWeapon(SelectWeapon)
                                            v.Head.CanCollide = false
                                            v.Humanoid.WalkSpeed = 0
                                            v.HumanoidRootPart.CanCollide = false
                                            v.HumanoidRootPart.CFrame = OldCFrameShark
                                            Tween(v.HumanoidRootPart.CFrame*CFrame.new(0,45,o))
                                            game:GetService("VirtualUser"):CaptureController()
                                            game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670))
                                            sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                        until not v.Parent or v.Humanoid.Health <= 0 or AutoSharkman == false or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Water Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Water Key")
                                    end
                                end
                            else
Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Tide Keeper").HumanoidRootPart.CFrame)
                               
                            end
                        end
                  
                end
            end
        end)
    end)
    
    Main:AddToggleRight("Auto ElectricClaw",AutoElectricClaw,function(value)
        AutoElectricClaw = value
        StopTween(AutoElectricClaw)
    end)
    
    spawn(function()
        pcall(function()
            while wait() do 
                if AutoElectricClaw then
                    if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Electro") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Electro") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Electric Claw") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Electric Claw") then
                        if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Electro") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 400 then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
                            SelectWeapon = "Electric Claw"
                        end  
                        if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Electro") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 400 then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
                            SelectWeapon = "Electric Claw"
                        end  
                        if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Electro") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value <= 399 then
                            SelectWeapon = "Electro"
                        end 
                    else
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
                    end
                end
                if AutoElectricClaw then
                    if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Electro") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Electro") then
                        if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Electro") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Electro") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 400 or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 400 then
                            if AutoFarm == false then
                                repeat task.wait()
                                    Tween(CFrame.new(-10371.4717, 330.764496, -10131.4199))
                                until not AutoElectricClaw or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - CFrame.new(-10371.4717, 330.764496, -10131.4199).Position).Magnitude <= 10
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw","Start")
                                wait(2)
                                repeat task.wait()
                                    Tween(CFrame.new(-12550.532226563, 336.22631835938, -7510.4233398438))
                                until not AutoElectricClaw or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - CFrame.new(-12550.532226563, 336.22631835938, -7510.4233398438).Position).Magnitude <= 10
                                wait(1)
                                repeat task.wait()
                                    Tween(CFrame.new(-10371.4717, 330.764496, -10131.4199))
                                until not AutoElectricClaw or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - CFrame.new(-10371.4717, 330.764496, -10131.4199).Position).Magnitude <= 10
                                wait(1)
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
                            elseif AutoFarm == true then
                                AutoFarm = false
                                wait(1)
                                repeat task.wait()
                                    Tween(CFrame.new(-10371.4717, 330.764496, -10131.4199))
                                until not AutoElectricClaw or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - CFrame.new(-10371.4717, 330.764496, -10131.4199).Position).Magnitude <= 10
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw","Start")
                                wait(2)
                                repeat task.wait()
                                    Tween(CFrame.new(-12550.532226563, 336.22631835938, -7510.4233398438))
                                until not AutoElectricClaw or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - CFrame.new(-12550.532226563, 336.22631835938, -7510.4233398438).Position).Magnitude <= 10
                                wait(1)
                                repeat task.wait()
                                    Tween(CFrame.new(-10371.4717, 330.764496, -10131.4199))
                                until not AutoElectricClaw or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - CFrame.new(-10371.4717, 330.764496, -10131.4199).Position).Magnitude <= 10
                                wait(1)
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
                                SelectWeapon = "Electric Claw"
                                wait(.1)
                                AutoFarm = true
                            end
                        end
                    end
                end
            end
        end)
    end)
    
    Main:AddToggleRight("Auto DragonTalon",AutoDragonTalon,function(value)
        AutoDragonTalon = value
    end)
    
    spawn(function()
        while wait() do
            if AutoDragonTalon then
                if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Talon") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Talon") then
                    if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 400 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
                        SelectWeapon = "Dragon Talon"
                    end  
                    if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 400 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
                        SelectWeapon = "Dragon Talon"
                    end  
                    if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 399 then
                        SelectWeapon = "Dragon Claw"
                    end 
                else 
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
                end
            end
        end
    end)
    
    Main:AddToggleRight("Auto Godhuman",GodHuman,function(a)
    GodHuman = a
    end)
    
    spawn(function()
        while task.wait() do
            if GodHuman then
                pcall(function()
                    if game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Death Step") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Death Step") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Sharkman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Sharkman Karate") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Talon") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Talon") or game.Players.LocalPlayer.Character:FindFirstChild("Godhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Godhuman") then
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman",true) == 1 then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") and game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") and game.Players.LocalPlayer.Character:FindFirstChild("Superhuman").Level.Value >= 400 then
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
                            end
                        else
                            game.StarterGui:SetCore("SendNotification", {
                                Title = "Notification", 
                                Text = "Not Have Superhuman" ,
                                Icon = "http://www.roblox.com/asset/?id=9956697825",
                                Duration = 2.5
                            })
                        end
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep",true) == 1 then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Death Step") and game.Players.LocalPlayer.Backpack:FindFirstChild("Death Step").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Death Step") and game.Players.LocalPlayer.Character:FindFirstChild("Death Step").Level.Value >= 400 then
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
                            end
                        else
                            game.StarterGui:SetCore("SendNotification", {
                                Title = "Notification", 
                                Text = "Not Have Death Step" ,
                                Icon = "http://www.roblox.com/asset/?id=9956697825",
                                Duration = 2.5
                            })
                        end
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true) == 1 then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Sharkman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Sharkman Karate").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Sharkman Karate") and game.Players.LocalPlayer.Character:FindFirstChild("Sharkman Karate").Level.Value >= 400 then
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
                            end
                        else
                            game.StarterGui:SetCore("SendNotification", {
                                Title = "Notification", 
                                Text = "Not Have SharkMan Karate" ,
                                Icon = "http://www.roblox.com/asset/?id=9956697825",
                                Duration = 2.5
                            })
                        end
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw",true) == 1 then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw").Level.Value >= 400 then
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
                            end
                        else
                            game.StarterGui:SetCore("SendNotification", {
                                Title = "Notification", 
                                Text = "Not Have Electric Claw" ,
                                Icon = "http://www.roblox.com/asset/?id=9956697825",
                                Duration = 2.5
                            })
                        end
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon",true) == 1 then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Talon") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Talon").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Dragon Talon") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Talon").Level.Value >= 400 then
                                if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman",true), "Bring") then
                                    game.StarterGui:SetCore("SendNotification", {
                                        Title = "Notification", 
                                        Text = "Not Have Enough Material" ,
                                        Icon = "http://www.roblox.com/asset/?id=9956697825",
                                        Duration = 2.5
                                    })
                                else
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman")
                                end
                            end
                        else
                            game.StarterGui:SetCore("SendNotification", {
                                Title = "Notification", 
                                Text = "Not Have Dragon Talon" ,
                                Icon = "http://www.roblox.com/asset/?id=9956697825",
                                Duration = 2.5
                            })
                        end
                    else
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
                    end
                end)
            end
        end
    end)
    
        Main:AddLineRight("")

     Main:AddSeperatorRight("Auto Stats")
    
    local Pointstat = Main:AddLabelRight("Stat Points")
    
    spawn(function()
        while wait() do
            pcall(function()
                Pointstat:Set("Stat Points : "..tostring(game:GetService("Players")["LocalPlayer"].Data.Points.Value))
            end)
        end
    end)
    
    Main:AddToggleRight("Melee Stats",Auto_Melee,function(value)
        Auto_Melee = value
    end)
    
    Main:AddToggleRight("Defense Stats",Auto_Defense,function(value)
        Auto_Defense = value
    end)
    
    Main:AddToggleRight("Sword Stats",Auto_Sword,function(value)
        Auto_Sword = value
    end)
    
    Main:AddToggleRight("Gun Stats",Auto_Gun,function(value)
        Auto_Gun = value
    end)
    
    Main:AddToggleRight("DevilFruit Stats",Auto_DevilFruit,function(value)
        Auto_DevilFruit = value
    end)
    
    PointStats = 1
    Main:AddSliderRight("Select Stats",1,100,1,function(value)
        PointStats = value
    end)
    
    Main:AddLineRight("")
    
    Main:AddSeperatorRight("Player")
	
	

Main:AddToggleRight("Aim Bot Skill {Beta}",false,function(a)
	AimBotFullFunction = a
end)

Main:AddToggleRight("Show Fov",false,function(a)
	ShowFov = a
end)

FOVSize = 200
Main:AddSliderRight("Fov Size",1,700,FOVSize,function(v)
	FOVSize = v
end)

local FOVCircle = Drawing.new("Circle")
FOVCircle.Thickness = 2
FOVCircle.NumSides = 460
FOVCircle.Filled = false
FOVCircle.Transparency = 0.5
FOVCircle.Radius = 200
FOVCircle.Color = Color3.fromRGB(255, 0, 0)

game:GetService("RunService").Stepped:Connect(function()
	FOVCircle.Radius = FOVSize
	FOVCircle.Thickness = 1
	FOVCircle.NumSides = 11
	FOVCircle.Position = game:GetService('UserInputService'):GetMouseLocation()
	if ShowFov then
		FOVCircle.Visible = true
	else
		FOVCircle.Visible = false
	end
end)

local lp = game:GetService('Players').LocalPlayer
local mouse = lp:GetMouse()
spawn(function()
	while wait() do
		if AimBotFullFunction then
			pcall(function()
				local MaxDist, Closest = math.huge
				for i,v in pairs(game:GetService("Players"):GetChildren()) do 
					local Head = v.Character:FindFirstChild("HumanoidRootPart")
					local Pos, Vis = game.Workspace.CurrentCamera.WorldToScreenPoint(game.Workspace.CurrentCamera, Head.Position)
					local MousePos, TheirPos = Vector2.new(mouse.X, mouse.Y), Vector2.new(Pos.X, Pos.Y)
					local Dist = (TheirPos - MousePos).Magnitude
					if Dist < MaxDist and Dist <= FOVSize and v.Name ~= game.Players.LocalPlayer.Name then
						MaxDist = Dist
						CharacterAimBot = v
					end
				end
			end)
		end
	end
end)

spawn(function()
    local gg = getrawmetatable(game)
    local old = gg.__namecall
    setreadonly(gg,false)
    gg.__namecall = newcclosure(function(...)
        local method = getnamecallmethod()
        local args = {...}
        if tostring(method) == "FireServer" then
            if tostring(args[1]) == "RemoteEvent" then
                if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
                    if AimBotFullFunction then
                        args[2] = CharacterAimBot.Character.HumanoidRootPart.Position
                        return old(unpack(args))
                    end
                end
            end
        end
        return old(...)
    end)
end)
spawn(function()
    while wait() do
        for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
            if v:IsA("Tool") then
                if v:FindFirstChild("RemoteFunctionShoot") then 
                    SelectToolWeaponGun = v.Name
                end
            end
        end
        for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do  
            if v:IsA("Tool") then
                if v:FindFirstChild("RemoteFunctionShoot") then 
                    SelectToolWeaponGun = v.Name
                end
            end
        end
    end
end)

spawn(function()
	mouse.Button1Down:Connect(function()
		if SelectToolWeaponGun ~= nil then
			if AimBotFullFunction and game.Players.LocalPlayer.Character:FindFirstChild(SelectToolWeaponGun) and game:GetService("Players"):FindFirstChild(CharacterAimBot.Name) then
				tool = game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun]
				v17 = workspace:FindPartOnRayWithIgnoreList(Ray.new(tool.Handle.CFrame.p, (game:GetService("Players"):FindFirstChild(CharacterAimBot.Name).Character.HumanoidRootPart.Position - tool.Handle.CFrame.p).unit * 100), { game.Players.LocalPlayer.Character, workspace._WorldOrigin });
				game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun].RemoteFunctionShoot:InvokeServer(game:GetService("Players"):FindFirstChild(CharacterAimBot).Character.HumanoidRootPart.Position, (require(game.ReplicatedStorage.Util).Other.hrpFromPart(v17)));
			end 
		end
	end)
end)
	
	local plyserv = Main:AddLabelRight("Players")
    
    spawn(function()
        while wait() do
            pcall(function()
                for i,v in pairs(game:GetService("Players"):GetPlayers()) do
                    if i == 12 then
                        plyserv:Set("Players :".." "..i.." ".."/".." ".."12".." ".."(Max)")
                    elseif i == 1 then
                        plyserv:Set("Player :".." "..i.." ".."/".." ".."12")
                    else
                        plyserv:Set("Players :".." "..i.." ".."/".." ".."12")
                    end
                end
            end)
        end
    end)
    
	
	
    Playerslist = {}
    
    for i,v in pairs(game:GetService("Players"):GetChildren()) do
        table.insert(Playerslist,v.Name)
    end
    
    local SelectedPly = Main:AddDropdownRight("Select Players",Playerslist,function(value)
        SelectPly = value
    end)
    
    Main:AddButtonRight("Reset Players",function()
        Playerslist = {}
        SelectedPly:Clear()
        for i,v in pairs(game:GetService("Players"):GetChildren()) do  
            SelectedPly:Add(v.Name)
        end
    end)
    
    Main:AddToggleRight("Spectate Players",SpectatePlys,function(value)
        SpectatePlys = value
        local plr1 = game:GetService("Players").LocalPlayer.Character.Humanoid
        local plr2 = game:GetService("Players"):FindFirstChild(SelectPly)
        repeat wait(.1)
            game:GetService("Workspace").Camera.CameraSubject = game:GetService("Players"):FindFirstChild(SelectPly).Character.Humanoid
        until SpectatePlys == false 
        game:GetService("Workspace").Camera.CameraSubject = game:GetService("Players").LocalPlayer.Character.Humanoid
    end)
    
    Main:AddToggleRight("TP Players",TeleportPly,function(value)
        TeleportPly = value
        StopTween(TeleportPly)
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if TeleportPly then
           repeat Tween(game:GetService("Players")[SelectPly].Character.HumanoidRootPart.CFrame) 
             wait() 
           until TeleportPly == false                 
         end
                end
            end)
    end)
    
     
    
    Main:AddToggleRight("Auto Kill Players",Auto_Kill_Ply,function(value)
        Auto_Kill_Ply = value
        StopTween(Auto_Kill_Ply)
    end)
    
    spawn(function()
        while wait() do
            if Auto_Kill_Ply then
                pcall(function()
                    if SelectPly ~= nil then 
                        if game.Players:FindFirstChild(SelectPly) then
                            if game.Players:FindFirstChild(SelectPly).Character.Humanoid.Health > 0 then
                                repeat task.wait()
                                    EquipWeapon(SelectWeapon)
                                    AutoHaki()
                                    game.Players:FindFirstChild(SelectPly).Character.HumanoidRootPart.CanCollide = false
                                    Tween(game.Players:FindFirstChild(SelectPly).Character.HumanoidRootPart.CFrame * CFrame.new(0,0,0))
                                    spawn(function()
                                        pcall(function()
                                            if SelectWeapon == SelectWeaponMelle then
                                                local args = {
                                                    [1] = game.Players:FindFirstChild(SelectPly).Character.HumanoidRootPart.Position,
                                                    [2] = game.Players:FindFirstChild(SelectPly).Character.HumanoidRootPart
                                                }
                                                game:GetService("Players").LocalPlayer.Character[SelectWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(args))
                                            else
                                                game:GetService("VirtualUser"):CaptureController()
                                                game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                            end
                                        end)
                                    end)
                                until game.Players:FindFirstChild(SelectPly).Character.Humanoid.Health <= 0 or not game.Players:FindFirstChild(SelectPly) or not Auto_Kill_Ply
                            end
                        end
                    end
                end)
            end
        end
    end)
    
    Main:AddSeperatorRight("Aimbot")
     

    
    Main:AddToggleRight("Aimbot Gun",Aimbot_Gun,function(value)
        Aimbot_Gun = value
    end)
 
 
spawn(function()
    local gg = getrawmetatable(game)
    local old = gg.__namecall
    setreadonly(gg,false)
    gg.__namecall = newcclosure(function(...)
        local method = getnamecallmethod()
        local args = {...}
        if tostring(method) == "FireServer" then
            if tostring(args[1]) == "RemoteEvent" then
                if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
                    if Aimbot_Skill then
                        args[2] = game:GetService("Players"):FindFirstChild(PlayerSelectAimbot).Character.HumanoidRootPart.Position
                        return old(unpack(args))
                    end
                end
            end
        end
        return old(...)
    end)
end)
    
    spawn(function()
        while task.wait() do
            if Aimbot_Gun and game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectWeaponGun) then
                pcall(function()
                 game:GetService'VirtualUser':CaptureController()
                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                    game:GetService("Players").LocalPlayer.Character[SelectWeaponGun].Cooldown.Value = 0
                    local args = {
                        [1] = game:GetService("Players"):FindFirstChild(PlayerSelectAimbot).Character.HumanoidRootPart.Position,
                    }
                    game:GetService("Players").LocalPlayer.Character[SelectWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(args))
                   
                end)
            end
        end
    end)
    
    Main:AddToggleRight("Aimbot Skill",Aimbot_Skill,function(value)
        Aimbot_Skill = value
    end)
    

    Main:AddSeperatorRight("PvP")
    
    Main:AddToggleRight("Auto Enable PVP ",EnabledPvP,function(value)
        EnabledPvP = value
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if EnabledPvP then
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.PvpDisabled.Visible == true then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EnablePvp")
                    end
                end
            end
        end)
    end)
    
    Main:AddButtonRight("Join Team Pirates",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetTeam","Pirates") 
        wait()
    end)
    
    Main:AddSeperatorRight("Bounty")
    
    local Current = Main:AddLabelRight("Current Bounties :")
    
    local Bounty = tostring(game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value)
    local sub = string.sub 
    local len = string.len
    spawn(function()
        while wait() do
            pcall(function()
                if len(Bounty) == 4 then
                    Bounty1 = sub(Bounty,1,1).."."..sub(Bounty,2,3).."K"
                elseif len(Bounty) == 5 then
                    Bounty1 = sub(Bounty,1,2).."."..sub(Bounty,3,4).."K"
                elseif len(Bounty) == 6 then
                    Bounty1 = sub(Bounty,1,3).."."..sub(Bounty,4,5).."K"
                elseif len(Bounty) == 7 then
                    Bounty1 = sub(Bounty,1,1).."."..sub(Bounty,2,3).."M"
                elseif len(Bounty) == 8 then
                    Bounty1 = sub(Bounty,1,2).."."..sub(Bounty,3,4).."M"
                elseif len(Bounty) <= 3 then
                    Bounty1 = Bounty
                end
                if tonumber(Bounty) == 30000000 then
                    Current:Set("Current Bounties : "..Bounty1.." [ Max ]")
                elseif tonumber(Bounty) < 30000000 then
                    Current:Set("Current Bounties : "..Bounty1)
                end
            end)
        end
    end)
    
    local Earn = Main:AddLabelRight("Earned")
    local OldBounty = game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value
    local Bounty = tostring(game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value)
    local Earned = tostring(game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value - OldBounty)
    local sub = string.sub 
    local len = string.len
    spawn(function()
        while wait() do
            pcall(function()
                if len(Earned) == 4 then
                    Earned1 = sub(Earned,1,1).."."..sub(Earned,2,3).."K"
                elseif len(Earned) == 5 then
                    Earned1 = sub(Earned,1,2).."."..sub(Earned,3,4).."K"
                elseif len(Earned) == 6 then
                    Earned1 = sub(Earned,1,3).."."..sub(Earned,4,5).."K"
                elseif len(Earned) == 7 then
                    Earned1 = sub(Earned,1,1).."."..sub(Earned,2,3).."M"
                elseif len(Earned) == 8 then
                    Earned1 = sub(Earned,1,2).."."..sub(Earned,3,4).."M"
                elseif len(Earned) <= 3 then
                    Earned1 = Earned
                end
                Earn:Set("Earned : "..tonumber(Earned1))
            end)
        end
    end)
    
        Main:AddToggleRight("Auto Farm Bounty",AutoFarmBounty,function(value)
        AutoFarmBounty = value
        StopTween(AutoFarmBounty)
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if AutoFarmBounty then
                    for i,v in pairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
                        if v:IsA("Shirt") then
                            v:Destroy()
                        end
                        if v:IsA("Pants") then
                            v:Destroy()
                        end
                        if v:IsA("Accessory") then
                            v:Destroy()
                        end
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        pcall(function()
            if AutoFarmBounty then
                while wait() do
                    if game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                    end
                end
            end
        end)
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if AutoFarmBounty then
                    if not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HasBuso") then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while task.wait() do
            pcall(function()
                if AutoFarmBounty then
                    game:GetService("Players").LocalPlayer.Character[SelectWeapon].Cooldown.Value = 0
                    spawn(function()
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Beli.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.HP.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Energy.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.StatsButton.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.ShopButton.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Skills.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Level.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.MenuButton.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Code.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Settings.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Mute.Visible = false
                        game:GetService("Players")["LocalPlayer"].PlayerGui.Main.CrewButton.Visible = false
                        game.Players.LocalPlayer.Character.Animate.Disabled = true
                    end)
                end
            end)
        end
    end)
    
     spawn(function()
            while wait() do
                if AutoFarmBounty then
                    if not NotEquip then
                        pcall(function()
                            for i,v in ipairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
                                if v:IsA("Tool") then
                                    game.Players.LocalPlayer.Character.Humanoid:EquipTool(v)
                                end
                            end
                        end)
                    end
                end
            end
        end)
    
    CastlePostoMansion = CFrame.new(-5084.8447265625, 316.48101806641, -3145.3752441406)
    MansiontoCastlePos = CFrame.new(-12464.596679688, 376.30590820312, -7567.2626953125)
    Castletophydra = CFrame.new(-5095.33984375, 316.48101806641, -3168.3134765625)
    HydratoCastle = CFrame.new(5741.869140625, 611.94750976562, -282.61154174805)
    spawn(function()
        while wait() do
            pcall(function()
                if AutoFarmBounty then
                    for i,v in pairs(game:GetService("Workspace").Characters:GetChildren()) do
                        if v.Name ~= game.Players.LocalPlayer.Name then
                            if v:WaitForChild("Humanoid").Health > 0 and (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude <= 17000 then
                                plyselecthunthelpold = v.Humanoid.Health
                                repeat task.wait()
                                    NotEquip = false
                                    NameTarget = v.Name
                                    if tostring(game.Players.LocalPlayer.Team) == "Pirates" then
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(10,10,0))
                                    elseif tostring(game.Players.LocalPlayer.Team) == "Marines" then
                                        if game.Players[NameTarget].Team ~= game.Players.LocalPlayer.Team then
                                            Tween(v.HumanoidRootPart.CFrame * CFrame.new(10,10,0))
                                        end
                                    end
                                    spawn(function()
                                        if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 150 then
                                            StartCheckTarget = true
                                        end
                                    end)
                                    v.HumanoidRootPart.CanCollide = false
                                    spawn(function()
                                        pcall(function()
                                        if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
                                            game:service('VirtualInputManager'):SendKeyEvent(true, "V", false, game)
            					     game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)
										 game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
											 game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
										 game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
				 							game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
												 game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
										 game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
										 end
                                        end)
                                    end)
                                    TargetSelectHunt = v.Humanoid
                                until AutoFarmBounty == false or v.Humanoid.Health == 0 or not v:FindFirstChild("HumanoidRootPart") or not v:FindFirstChild("Humanoid") or not v.Parent or NextplySelect == true
                                NextplySelect = false
                                StartCheckTarget = false
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        pcall(function()
            while task.wait() do
                if AutoFarmBounty then
                    game:GetService("Players").LocalPlayer.PlayerGui.Main.InCombat.Visible = false
                    game:GetService("Players").LocalPlayer.PlayerGui.Main.SafeZone.Visible = false
                end
            end
        end)
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if AutoFarmBounty then
                    if TargetSelectHunt ~= nil then
                        if StartCheckTarget then
                            wait(6.5)
                            if TargetSelectHunt.Health == TargetSelectHunt.MaxHealth or TargetSelectHunt.Health >= plyselecthunthelpold then
                                NextplySelect = true
                                TargetSelectHunt = nil
                            end
                        end
                    end
                end
            end
        end)
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if AutoFarmBounty then
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.PvpDisabled.Visible == true then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EnablePvp")
                    end
                end
            end
        end)
    end)
    
    Main:AddToggleRight("Auto Farm Bounty Hop",AutoFarmBounty_Hop,function(value)
        AutoFarmBounty_Hop = value
    end)
    
    spawn(function()
        while wait() do
            if AutoFarmBounty then
                if AutoFarmBounty_Hop then
                    pcall(function()
                        wait(120)
                        Hop()
                    end)
                end
            end
        end
    end)
    
    Main:AddSeperatorRight("Misc Bounty")
    
    Main:AddButtonRight("Nest Players",function()
        NextplySelect = true
        wait(.1)
        NextplySelect = false
    end)
    Main:AddLineRight("")
    
    Main:AddSeperatorRight("ESP")
    
    Main:AddToggleRight("ESP Player",false,function(value)
        ESPPlayer = value
        while ESPPlayer do wait()
            UpdateEspPlayer()
        end
    end)
    
    Main:AddToggleRight("ESP Chest",false,function(value)
        ChestESP = value
        while ChestESP do wait()
            UpdateChestEsp() 
        end
    end)
    
    Main:AddToggleRight("ESP Fruit",false,function(value)
        DevilFruitESP = value
        while DevilFruitESP do wait()
            UpdateBfEsp() 
        end
    end)
    
    Main:AddToggleRight("ESP Flower",false,function(value)
        FlowerESP = value
        while FlowerESP do wait()
            UpdateFlowerEsp() 
        end
    end)
    
    Main:AddToggleRight("ESP Island",IslandESP,function(value)
        IslandESP = value
        while IslandESP do wait()
            UpdateIslandESP() 
        end
    end)
    
    Main:AddLineRight("")

    
    spawn(function()
        while wait() do
            pcall(function()
                if Auto_Melee then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.Value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Melee",PointStats)
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if Auto_Defense then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.Value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Defense",PointStats)
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if Auto_Sword then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.Value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Sword",PointStats)
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if Auto_Gun then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.Value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Gun",PointStats)
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if Auto_DevilFruit then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.Value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Devil Fruit",PointStats)
                    end
                end
            end)
        end
    end)
    
    if game.PlaceId == 2753915549 then
        World1 = true
    elseif game.PlaceId == 4442272183 then
        World2 = true
    elseif game.PlaceId == 7449423635 then
        World3 = true
    end
    
    function CheckQuest() 
        MyLevel = game:GetService("Players").LocalPlayer.Data.Level.Value
        if World1 then
            if MyLevel == 1 or MyLevel <= 9 then
                Mon = "Bandit"
                LevelQuest = 1
                NameQuest = "BanditQuest1"
                NameMon = "Bandit"
                PUK = CFrame.new(1216.779541015625, 56.393497467041016, 1606.126220703125)
                CFrameQuest = CFrame.new(1059.37195, 15.4495068, 1550.4231, 0.939700544, -0, -0.341998369, 0, 1, -0, 0.341998369, 0, 0.939700544)
            elseif MyLevel == 10 or MyLevel <= 14 then
                Mon = "Monkey"
                LevelQuest = 1
                NameQuest = "JungleQuest"
                NameMon = "Monkey"
                PUK = CFrame.new()
                CFrameQuest = CFrame.new(-1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, -0, -1, 0, 0)
            elseif MyLevel == 15 or MyLevel <= 29 then
                Mon = "Gorilla"
                LevelQuest = 2
                NameQuest = "JungleQuest"
                NameMon = "Gorilla"
                PUK = CFrame.new(-1257.61181640625, 65.0517807006836, -499.2301025390625)
                CFrameQuest = CFrame.new(-1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, -0, -1, 0, 0)
            elseif MyLevel == 30 or MyLevel <= 39 then
                Mon = "Pirate"
                LevelQuest = 1
                NameQuest = "BuggyQuest1"
                NameMon = "Pirate"
                PUK = CFrame.new(-1178.50244140625, 65.74028778076172, 3889.71630859375)
                CFrameQuest = CFrame.new(-1141.07483, 4.10001802, 3831.5498, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
            elseif MyLevel == 40 or MyLevel <= 59 then
                Mon = "Brute"
                LevelQuest = 2
                NameQuest = "BuggyQuest1"
                NameMon = "Brute"
                PUK = CFrame.new(-1144.44861, 90.5594559, 4307.25928, -0.998438537, 0, 0.0558618344, 0, 1, 0, -0.0558618344, 0, -0.998438537)
                CFrameQuest = CFrame.new(-1141.07483, 4.10001802, 3831.5498, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
            elseif MyLevel == 60 or MyLevel <= 74 then
                Mon = "Desert Bandit"
                LevelQuest = 1
                NameQuest = "DesertQuest"
                NameMon = "Desert Bandit"
                PUK = CFrame.new(919.5968017578125, 69.22762298583984, 4487.37109375)
                CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, -0, -0.573571265, 0, 1, -0, 0.573571265, 0, 0.819155693)
            elseif MyLevel == 75 or MyLevel <= 89 then
                Mon = "Desert Officer"
                LevelQuest = 2
                NameQuest = "DesertQuest"
                NameMon = "Desert Officer"
                PUK = CFrame.new(1580.03198, 4.61375761, 4366.86426)
                CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, -0, -0.573571265, 0, 1, -0, 0.573571265, 0, 0.819155693)
            elseif MyLevel == 90 or MyLevel <= 99 then
                Mon = "Snow Bandit"
                LevelQuest = 1
                NameQuest = "SnowQuest"
                NameMon = "Snow Bandit"
                PUK = CFrame.new(1365.15625, 124.89803314208984, -1364.9873046875)
                CFrameQuest = CFrame.new(1389.74451, 88.1519318, -1298.90796, -0.342042685, 0, 0.939684391, 0, 1, 0, -0.939684391, 0, -0.342042685)
            elseif MyLevel == 100 or MyLevel <= 119 then
                Mon = "Snowman"
                LevelQuest = 2
                NameQuest = "SnowQuest"
                NameMon = "Snowman"
                PUK = CFrame.new(1122.921875, 143.72373962402344, -1539.132080078125)
                CFrameQuest = CFrame.new(1389.74451, 88.1519318, -1298.90796, -0.342042685, 0, 0.939684391, 0, 1, 0, -0.939684391, 0, -0.342042685)
            elseif MyLevel == 120 or MyLevel <= 149 then
                Mon = "Chief Petty Officer"
                LevelQuest = 1
                NameQuest = "MarineQuest2"
                NameMon = "Chief Petty Officer"
                PUK = CFrame.new(-4882.8623, 22.6520386, 4255.53516)
                CFrameQuest = CFrame.new(-5039.58643, 27.3500385, 4324.68018, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 150 or MyLevel <= 174 then
                Mon = "Sky Bandit"
                LevelQuest = 1
                NameQuest = "SkyQuest"
                NameMon = "Sky Bandit"
                PUK = CFrame.new(-4970.74219, 294.544342, -2890.11353)
                CFrameQuest = CFrame.new(-4839.53027, 716.368591, -2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
                end
            elseif MyLevel == 175 or MyLevel <= 189 then
                Mon = "Dark Master"
                LevelQuest = 2
                NameQuest = "SkyQuest"
                NameMon = "Dark Master"
                PUK = CFrame.new(-5220.58594, 430.693298, -2278.17456)
                CFrameQuest = CFrame.new(-4839.53027, 716.368591, -2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
               game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
               end
            elseif MyLevel == 190 or MyLevel <= 209 then
                Mon = "Prisoner"
                LevelQuest = 1
                NameQuest = "PrisonerQuest"
                NameMon = "Prisoner"
                PUK = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
                CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
           elseif MyLevel == 210 or MyLevel <= 249 then 
                Mon = "Dangerous Prisoner"
                LevelQuest = 2
                NameQuest = "PrisonerQuest"
                NameMon = "Dangerous Prisoner"
                PUK = CFrame.new(5563.1171875, 67.71013641357422, 832.8712158203125)
                CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
           elseif MyLevel == 250 or MyLevel <= 299 then
                Mon = "Toga Warrior"
                LevelQuest = 1
                NameQuest = "ColosseumQuest"
                NameMon = "Toga Warrior"
                PUK = CFrame.new(-1848.348876953125, 42.34652328491211, -2794.3759765625)
                CFrameQuest = CFrame.new(-1580.04663, 6.35000277, -2986.47534, -0.515037298, 0, -0.857167721, 0, 1, 0, 0.857167721, 0, -0.515037298)
            elseif MyLevel == 300 or MyLevel <= 324 then
                Mon = "Military Soldier"
                LevelQuest = 1
                NameQuest = "MagmaQuest"
                NameMon = "Military Soldier"
                PUK = CFrame.new(-5461.19140625, 44.07990264892578, 8457.443359375)
                CFrameQuest = CFrame.new(-5313.37012, 10.9500084, 8515.29395, -0.499959469, 0, 0.866048813, 0, 1, 0, -0.866048813, 0, -0.499959469)
            elseif MyLevel == 325 or MyLevel <= 374 then
                Mon = "Military Spy"
                LevelQuest = 2
                NameQuest = "MagmaQuest"
                NameMon = "Military Spy"
                PUK = CFrame.new(-5872.0625, 143.23089599609375, 8790.439453125)
                CFrameQuest = CFrame.new(-5313.37012, 10.9500084, 8515.29395, -0.499959469, 0, 0.866048813, 0, 1, 0, -0.866048813, 0, -0.499959469)
            elseif MyLevel == 375 or MyLevel <= 399 then
                Mon = "Fishman Warrior"
                LevelQuest = 1
                NameQuest = "FishmanQuest"
                NameMon = "Fishman Warrior"
                PUK = CFrame.new(60875.9921875, 35.35336685180664, 1434.669189453125)
                CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                end
            elseif MyLevel == 400 or MyLevel <= 449 then
                Mon = "Fishman Commando"
                LevelQuest = 2
                NameQuest = "FishmanQuest"
                NameMon = "Fishman Commando"
                PUK = CFrame.new(61914.1484375, 82.76360321044922, 1461.85595703125)
                CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                end
            elseif MyLevel == 450 or MyLevel <= 474 then
                Mon = "God's Guard"
                LevelQuest = 1
                NameQuest = "SkyExp1Quest"
                NameMon = "God's Guard"
                PUK = CFrame.new(-4721.88867, 843.874695, -1949.96643, 0.996191859, -0, -0.0871884301, 0, 1, -0, 0.0871884301, 0, 0.996191859)
                CFrameQuest = CFrame.new(-4721.88867, 843.874695, -1949.96643, 0.996191859, -0, -0.0871884301, 0, 1, -0, 0.0871884301, 0, 0.996191859)
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
                end
            elseif MyLevel == 475 or MyLevel <= 524 then
                Mon = "Shanda"
                LevelQuest = 2
                NameQuest = "SkyExp1Quest"
                NameMon = "Shanda"
                PUK = CFrame.new(-7658.7041015625, 5605.01025390625, -529.287353515625)
                CFrameQuest = CFrame.new(-7859.09814, 5544.19043, -381.476196, -0.422592998, 0, 0.906319618, 0, 1, 0, -0.906319618, 0, -0.422592998)
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
                end
            elseif MyLevel == 525 or MyLevel <= 549 then
                Mon = "Royal Squad"
                LevelQuest = 1
                NameQuest = "SkyExp2Quest"
                NameMon = "Royal Squad"
                PUK = CFrame.new(-7669.1796875, 5638.10986328125, -1448.95458984375)
                CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 550 or MyLevel <= 624 then
                Mon = "Royal Soldier"
                LevelQuest = 2
                NameQuest = "SkyExp2Quest"
                NameMon = "Royal Soldier"
                PUK = CFrame.new(-7839.28955078125, 5681.00830078125, -1717.6197509765625)
                CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 625 or MyLevel <= 649 then
                Mon = "Galley Pirate"
                LevelQuest = 1
                NameQuest = "FountainQuest"
                NameMon = "Galley Pirate"
                PUK = CFrame.new(5566.14453125, 71.22917175292969, 3964.4443359375)
                CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, 0.087131381)
            elseif MyLevel >= 650 then
                Mon = "Galley Captain"
                LevelQuest = 2
                NameQuest = "FountainQuest"
                NameMon = "Galley Captain"
                PUK = CFrame.new(5344.2529296875, 104.73433685302734, 4821.6533203125)
                CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, 0.087131381)
            end
        elseif World2 then
            if MyLevel == 700 or MyLevel <= 724 then
                Mon = "Raider"
                LevelQuest = 1
                NameQuest = "Area1Quest"
                NameMon = "Raider"
                PUK = CFrame.new(-737.026123, 39.1748352, 2392.57959)
                CFrameQuest = CFrame.new(-429.543518, 71.7699966, 1836.18188, -0.22495985, 0, -0.974368095, 0, 1, 0, 0.974368095, 0, -0.22495985)
            elseif MyLevel == 725 or MyLevel <= 774 then
                Mon = "Mercenary"
                LevelQuest = 2
                NameQuest = "Area1Quest"
                NameMon = "Mercenary"
                PUK = CFrame.new(-1016.576171875, 133.70040893554688, 1433.923095703125)
                CFrameQuest = CFrame.new(-429.543518, 71.7699966, 1836.18188, -0.22495985, 0, -0.974368095, 0, 1, 0, 0.974368095, 0, -0.22495985)
            elseif MyLevel == 775 or MyLevel <= 874 then
                Mon = "Swan Pirate"
                LevelQuest = 1
                NameQuest = "Area2Quest"
                NameMon = "Swan Pirate"
                PUK = CFrame.new(970.369446, 142.653198, 1217.3667)
                CFrameQuest = CFrame.new(638.43811, 71.769989, 918.282898, 0.139203906, 0, 0.99026376, 0, 1, 0, -0.99026376, 0, 0.139203906)
            elseif MyLevel == 875 or MyLevel <= 899 then
                Mon = "Marine Lieutenant"
                LevelQuest = 1
                NameQuest = "MarineQuest3"
                NameMon = "Marine Lieutenant"
                PUK = CFrame.new(-2929.03369140625, 163.5143585205078, -3027.66357421875)
                CFrameQuest = CFrame.new(-2440.79639, 71.7140732, -3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
            elseif MyLevel == 900 or MyLevel <= 949 then
                Mon = "Marine Captain"
                LevelQuest = 2
                NameQuest = "MarineQuest3"
                NameMon = "Marine Captain"
                PUK = CFrame.new(-1932.095703125, 131.94061279296875, -3291.61865234375)
                CFrameQuest = CFrame.new(-2440.79639, 71.7140732, -3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
            elseif MyLevel == 950 or MyLevel <= 999 then
                Mon = "Zombie"
                LevelQuest = 1
                NameQuest = "ZombieQuest"
                NameMon = "Zombie"
                PUK = CFrame.new(-5695.2451171875, 124.95378875732422, -775.65478515625)
                CFrameQuest = CFrame.new(-5497.06152, 47.5923004, -795.237061, -0.29242146, 0, -0.95628953, 0, 1, 0, 0.95628953, 0, -0.29242146)
            elseif MyLevel == 1000 or MyLevel <= 1049 then
                Mon = "Snow Trooper"
                LevelQuest = 1
                NameQuest = "SnowMountainQuest"
                NameMon = "Snow Trooper"
                PUK = CFrame.new(535.893433, 401.457062, -5329.6958, -0.999524176, 0, 0.0308452044, 0, 1, -0, -0.0308452044, 0, -0.999524176)
                CFrameQuest = CFrame.new(609.858826, 400.119904, -5372.25928, -0.374604106, 0, 0.92718488, 0, 1, 0, -0.92718488, 0, -0.374604106)
            elseif MyLevel == 1050 or MyLevel <= 1099 then
                Mon = "Winter Warrior"
                LevelQuest = 2
                NameQuest = "SnowMountainQuest"
                NameMon = "Winter Warrior"
                PUK = CFrame.new(1223.7417, 454.575226, -5170.02148, 0.473996818, 2.56845354e-08, 0.880526543, -5.62456428e-08, 1, 1.10811016e-09, -0.880526543, -5.00510211e-08, 0.473996818)
                CFrameQuest = CFrame.new(609.858826, 400.119904, -5372.25928, -0.374604106, 0, 0.92718488, 0, 1, 0, -0.92718488, 0, -0.374604106)
            elseif MyLevel == 1100 or MyLevel <= 1124 then
                Mon = "Lab Subordinate"
                LevelQuest = 1
                NameQuest = "IceSideQuest"
                NameMon = "Lab Subordinate"
                PUK = CFrame.new(-6060.10693, 15.9868021, -4904.7876, -0.411000341, -5.06538868e-07, 0.91163528, 1.26306062e-07, 1, 6.12581289e-07, -0.91163528, 3.66916197e-07, -0.411000341)
                CFrameQuest = CFrame.new(-6064.06885, 15.2422857, -4902.97852, 0.453972578, -0, -0.891015649, 0, 1, -0, 0.891015649, 0, 0.453972578)
            elseif MyLevel == 1125 or MyLevel <= 1174 then
                Mon = "Horned Warrior"
                LevelQuest = 2
                NameQuest = "IceSideQuest"
                NameMon = "Horned Warrior"
                PUK = CFrame.new(-6400.85889, 24.7645149, -5818.63574)
                CFrameQuest = CFrame.new(-6064.06885, 15.2422857, -4902.97852, 0.453972578, -0, -0.891015649, 0, 1, -0, 0.891015649, 0, 0.453972578)
            elseif MyLevel == 1175 or MyLevel <= 1199 then
                Mon = "Magma Ninja"
                LevelQuest = 1
                NameQuest = "FireSideQuest"
                NameMon = "Magma Ninja"
                PUK = CFrame.new(-5496.65576, 58.6890411, -5929.76855)
                CFrameQuest = CFrame.new(-5428.03174, 15.0622921, -5299.43457, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
            elseif MyLevel == 1200 or MyLevel <= 1249 then
                Mon = "Lava Pirate"
                LevelQuest = 2
                NameQuest = "FireSideQuest"
                NameMon = "Lava Pirate"
                PUK = CFrame.new(-5169.71729, 34.1234779, -4669.73633)
                CFrameQuest = CFrame.new(-5428.03174, 15.0622921, -5299.43457, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
            elseif MyLevel == 1250 or MyLevel <= 1274 then
                Mon = "Ship Deckhand"
                LevelQuest = 1
                NameQuest = "ShipQuest1"
                NameMon = "Ship Deckhand"
                PUK = CFrame.new(1181.84875, 130.485107, 33005.4961, -0.946877539, -7.47373434e-08, -0.321594298, -7.391602e-08, 1, -1.47637005e-08, 0.321594298, 9.79155601e-09, -0.946877539)
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)         
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end
            elseif MyLevel == 1275 or MyLevel <= 1299 then
                Mon = "Ship Engineer"
                LevelQuest = 2
                NameQuest = "ShipQuest1"
                NameMon = "Ship Engineer"
                PUK = CFrame.new(919.250427, 43.544014, 32781.9922, 0.999619186, 4.03968698e-08, -0.0275939237, -3.75240887e-08, 1, 1.04626984e-07, 0.0275939237, -1.03551706e-07, 0.999619186)
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)   
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end             
            elseif MyLevel == 1300 or MyLevel <= 1324 then
                Mon = "Ship Steward"
                LevelQuest = 1
                NameQuest = "ShipQuest2"
                NameMon = "Ship Steward"
                PUK = CFrame.new(917.478882, 129.556, 33441.2227, -0.999965012, -1.84493896e-08, -0.00836863648, -1.84426696e-08, 1, -8.80260864e-10, 0.00836863648, -7.2589007e-10, -0.999965012)
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)         
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end
            elseif MyLevel == 1325 or MyLevel <= 1349 then
                Mon = "Ship Officer"
                LevelQuest = 2
                NameQuest = "ShipQuest2"
                NameMon = "Ship Officer"
                PUK = CFrame.new(1201.18286, 181.149124, 33308.0508, 0.0748318806, -7.14178512e-08, -0.997196138, 2.97970733e-08, 1, -6.93826223e-08, 0.997196138, -2.45214959e-08, 0.0748318806)
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end
            elseif MyLevel == 1350 or MyLevel <= 1374 then
                Mon = "Arctic Warrior"
                LevelQuest = 1
                NameQuest = "FrostQuest"
                NameMon = "Arctic Warrior"
                PUK = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
                CFrameQuest = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 5000.034996032715, -132.83953857422))
                end
            elseif MyLevel == 1375 or MyLevel <= 1424 then
                Mon = "Snow Lurker"
                LevelQuest = 2
                NameQuest = "FrostQuest"
                NameMon = "Snow Lurker"
                PUK = CFrame.new(5518.00684, 60.5559731, -6828.80518)
                CFrameQuest = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
            elseif MyLevel == 1425 or MyLevel <= 1449 then
                Mon = "Sea Soldier"
                LevelQuest = 1
                NameQuest = "ForgottenQuest"
                NameMon = "Sea Soldier"
                PUK = CFrame.new(-3366.32958984375, 47.21970748901367, -9704.3505859375)
                CFrameQuest = CFrame.new(-3054.44458, 235.544281, -10142.8193, 0.990270376, -0, -0.13915664, 0, 1, -0, 0.13915664, 0, 0.990270376)
            elseif MyLevel >= 1450 then
                Mon = "Water Fighter"
                LevelQuest = 2
                NameQuest = "ForgottenQuest"
                NameMon = "Water Fighter"
                PUK = CFrame.new(-3436.7727050781, 290.52191162109, -10503.438476563)
                CFrameQuest = CFrame.new(-3054.44458, 235.544281, -10142.8193, 0.990270376, -0, -0.13915664, 0, 1, -0, 0.13915664, 0, 0.990270376)
            end
        elseif World3 then
            if MyLevel == 1500 or MyLevel <= 1524 then
                Mon = "Pirate Millionaire"
                LevelQuest = 1
                NameQuest = "PiratePortQuest"
                NameMon = "Pirate Millionaire"
                PUK = CFrame.new(-290.674988, 34.7821121, 5417.57666, -0.959131062, 7.87279077e-08, 0.282962203, 6.99472977e-08, 1, -4.11336849e-08, -0.282962203, -1.96601544e-08, -0.959131062)
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
            elseif MyLevel == 1525 or MyLevel <= 1574 then
                Mon = "Pistol Billionaire"
                LevelQuest = 2
                NameQuest = "PiratePortQuest"
                NameMon = "Pistol Billionaire"
                PUK = CFrame.new(-387.624237, 74.2720413, 5851.84473, -0.990750372, -6.79122536e-08, 0.135697171, -7.2516066e-08, 1, -2.89841076e-08, -0.135697171, -3.85562409e-08, -0.990750372)
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
            elseif MyLevel == 1575 or MyLevel <= 1599 then
                Mon = "Dragon Crew Warrior"
                LevelQuest = 1
                NameQuest = "AmazonQuest"
                NameMon = "Dragon Crew Warrior"
                PUK = CFrame.new(6241.9951171875, 51.522083282471, -1243.9771728516)
                CFrameQuest = CFrame.new(5832.83594, 51.6806107, -1101.51563, 0.898790359, -0, -0.438378751, 0, 1, -0, 0.438378751, 0, 0.898790359)
            elseif MyLevel == 1600 or MyLevel <= 1624 then 
                Mon = "Dragon Crew Archer"
                NameQuest = "AmazonQuest"
                LevelQuest = 2
                NameMon = "Dragon Crew Archer"
                PUK = CFrame.new(6788.97461, 462.341248, 164.233673, -0.711975694, 1.98202414e-08, 0.702204108, -1.45830699e-08, 1, -4.30117559e-08, -0.702204108, -4.08636183e-08, -0.711975694)
                CFrameQuest = CFrame.new(5833.1147460938, 51.60498046875, -1103.0693359375)
            elseif MyLevel == 1625 or MyLevel <= 1649 then
                Mon = "Female Islander"
                NameQuest = "AmazonQuest2"
                LevelQuest = 1
                NameMon = "Female Islander"
                PUK = CFrame.new(5763.98682, 848.118103, 1082.43127, 0.986172736, 2.65753979e-08, 0.165720671, -2.36233451e-08, 1, -1.97844852e-08, -0.165720671, 1.55960436e-08, 0.986172736)
                CFrameQuest = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
            elseif MyLevel == 1650 or MyLevel <= 1699 then 
                Mon = "Giant Islander"
                NameQuest = "AmazonQuest2"
                LevelQuest = 2
                NameMon = "Giant Islander"
                PUK = CFrame.new(4784.24561, 708.376465, 466.297485, 0.99801594, 3.11927195e-09, 0.0629619658, -5.34848299e-09, 1, 3.52371394e-08, -0.0629619658, -3.55039766e-08, 0.99801594)
                CFrameQuest = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
            elseif MyLevel == 1700 or MyLevel <= 1724 then
                Mon = "Marine Commodore"
                LevelQuest = 1
                NameQuest = "MarineTreeIsland"
                NameMon = "Marine Commodore"
                PUK = CFrame.new(2490.0844726563, 190.4232635498, -7160.0502929688)
                CFrameQuest = CFrame.new(2180.54126, 27.8156815, -6741.5498, -0.965929747, 0, 0.258804798, 0, 1, 0, -0.258804798, 0, -0.965929747)
                if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1725 or MyLevel <= 1774 then
                Mon = "Marine Rear Admiral"
                NameMon = "Marine Rear Admiral"
                NameQuest = "MarineTreeIsland"
                LevelQuest = 2
                PUK = CFrame.new(3951.3903808594, 229.11549377441, -6912.81640625)
                CFrameQuest = CFrame.new(2179.98828125, 28.731239318848, -6740.0551757813)
                 if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1775 or MyLevel <= 1799 then
                Mon = "Fishman Raider"
                LevelQuest = 1
                NameQuest = "DeepForestIsland3"
                NameMon = "Fishman Raider"
                PUK = CFrame.new(-10322.400390625, 390.94473266602, -8580.0908203125)
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)   
                 if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1800 or MyLevel <= 1824 then
                Mon = "Fishman Captain"
                LevelQuest = 2
                NameQuest = "DeepForestIsland3"
                NameMon = "Fishman Captain"
                PUK = CFrame.new(-11194.541992188, 442.02795410156, -8608.806640625)
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)   
                 if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1825 or MyLevel <= 1849 then
                Mon = "Forest Pirate"
                LevelQuest = 1
                NameQuest = "DeepForestIsland"
                NameMon = "Forest Pirate"
                PUK = CFrame.new(-13225.809570313, 428.19387817383, -7753.1245117188)
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)
                 if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1850 or MyLevel <= 1899 then
                Mon = "Mythological Pirate"
                LevelQuest = 2
                NameQuest = "DeepForestIsland"
                NameMon = "Mythological Pirate"
                PUK = CFrame.new(-13869.172851563, 564.95251464844, -7084.4135742188)
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)   
                 if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1900 or MyLevel <= 1924 then
                Mon = "Jungle Pirate"
                LevelQuest = 1
                NameQuest = "DeepForestIsland2"
                NameMon = "Jungle Pirate"
                PUK = CFrame.new(-11982.221679688, 376.32522583008, -10451.415039063)
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                 if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1925 or MyLevel <= 1974 then
                Mon = "Musketeer Pirate"
                LevelQuest = 2
                NameQuest = "DeepForestIsland2"
                NameMon = "Musketeer Pirate"
                PUK = CFrame.new(-13282.3046875, 496.23684692383, -9565.150390625)
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                 if AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
               end
            elseif MyLevel == 1975 or MyLevel <= 1999 then
                Mon = "Reborn Skeleton"
                LevelQuest = 1
                NameQuest = "HauntedQuest1"
                NameMon = "Reborn Skeleton"
                PUK = CFrame.new(-8817.880859375, 191.16761779785, 6298.6557617188)
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
            elseif MyLevel == 2000 or MyLevel <= 2024 then
                Mon = "Living Zombie"
                LevelQuest = 2
                NameQuest = "HauntedQuest1"
                NameMon = "Living Zombie"
                PUK = CFrame.new(-10125.234375, 183.94705200195, 6242.013671875)
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
            elseif MyLevel == 2025 or MyLevel <= 2049 then
                Mon = "Demonic Soul"
                LevelQuest = 1
                NameQuest = "HauntedQuest2"
                NameMon = "Demonic Soul"
                PUK = CFrame.new(-9712.03125, 204.69589233398, 6193.322265625)
                CFrameQuest = CFrame.new(-9516.99316, 172.017181, 6078.46533, 0, 0, -1, 0, 1, 0, 1, 0, 0) 
            elseif MyLevel == 2050 or MyLevel <= 2074 then
                Mon = "Posessed Mummy"
                LevelQuest = 2
                NameQuest = "HauntedQuest2"
                NameMon = "Posessed Mummy"
                PUK = CFrame.new(-9545.7763671875, 69.619895935059, 6339.5615234375)
                CFrameQuest = CFrame.new(-9516.99316, 172.017181, 6078.46533, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2075 or MyLevel <= 2099 then
                Mon = "Peanut Scout"
                LevelQuest = 1
                NameQuest = "NutsIslandQuest"
                NameMon = "Peanut Scout"
                PUK = CFrame.new(-2265.89014, 89.7506104, -10261.2197, -0.809553444, -9.26727282e-08, 0.587046146, -5.44419549e-08, 1, 8.27857534e-08, -0.587046146, 3.50595535e-08, -0.809553444)
                CFrameQuest = CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2100 or MyLevel <= 2124 then
                Mon = "Peanut President"
                LevelQuest = 2
                NameQuest = "NutsIslandQuest"
                NameMon = "Peanut President"
                PUK = CFrame.new(-2062.11792, 86.0444489, -10481.1445, 0.834163189, -9.79785408e-09, -0.551517665, -2.60617616e-09, 1, -2.17070646e-08, 0.551517665, 1.95445864e-08, 0.834163189)
                CFrameQuest = CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2125 or MyLevel <= 2149 then
                Mon = "Ice Cream Chef"
                LevelQuest = 1
                NameQuest = "IceCreamIslandQuest"
                NameMon = "Ice Cream Chef"
                PUK = CFrame.new(-875.441345, 107.871437, -11253.3691, 0.630182087, 5.98710486e-08, 0.776447415, -6.03229751e-08, 1, -2.81494827e-08, -0.776447415, -2.90983202e-08, 0.63018208)
                CFrameQuest = CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2150 or MyLevel <= 2199 then
                Mon = "Ice Cream Commander"
                LevelQuest = 2
                NameQuest = "IceCreamIslandQuest"
                NameMon = "Ice Cream Commander"
                PUK = CFrame.new(-643.3078, 140.913528, -11334.7109, -0.996822715, -9.07818087e-09, 0.0796525627, -1.43212509e-08, 1, -6.52529906e-08, -0.0796525627, -6.61863808e-08, -0.996822715)
                CFrameQuest = CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438, 0, 0, -1, 0, 1, 0, 1, 0, 0)
            elseif MyLevel == 2200 or MyLevel <= 2224 then
                Mon = "Cookie Crafter"
                LevelQuest = 1
                NameQuest = "CakeQuest1"
                NameMon = "Cookie Crafter"
                PUK = CFrame.new(-2437.66064, 133.07428, -12122.8721, 0.215197399, 2.05706883e-08, -0.976570547, -6.6551344e-08, 1, 6.39893472e-09, 0.976570547, 6.36150475e-08, 0.215197399)
                CFrameQuest = CFrame.new(-2021.32007, 37.7982254, -12028.7295, 0.957576931, -8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, -0.288177818, -5.2032135e-08, 0.957576931)
            elseif MyLevel == 2225 or MyLevel <= 2249 then
                Mon = "Cake Guard"
                LevelQuest = 2
                NameQuest = "CakeQuest1"
                NameMon = "Cake Guard"
                PUK = CFrame.new(-1595.00916, 44.7149811, -12252.0547, -0.998557925, -6.0718726e-08, -0.0536852553, -5.64001539e-08, 1, -8.19574169e-08, 0.0536852553, -7.88113681e-08, -0.998557925)
                CFrameQuest = CFrame.new(-2021.32007, 37.7982254, -12028.7295, 0.957576931, -8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, -0.288177818, -5.2032135e-08, 0.957576931)
            elseif MyLevel == 2250 or MyLevel <= 2274 then
                Mon = "Baking Staff"
                LevelQuest = 1
                NameQuest = "CakeQuest2"
                NameMon = "Baking Staff"
                PUK = CFrame.new(-1817.20581, 93.8077316, -12885.6309, -0.696141601, 7.12665269e-08, 0.717904449, 4.05417566e-08, 1, -5.99574506e-08, -0.717904449, -1.26337669e-08, -0.696141601)
                CFrameQuest = CFrame.new(-1927.91602, 37.7981339, -12842.5391, -0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, -0.250778586, 2.64211941e-08, -0.96804446)
            elseif MyLevel == 2275 or MyLevel <=2299 then
                Mon = "Head Baker"
                LevelQuest = 2
                NameQuest = "CakeQuest2"
                NameMon = "Head Baker"
                PUK = CFrame.new(-2263.37744, 156.999985, -12776, 0.945995748, 2.16281637e-09, 0.324179053, -1.23387056e-09, 1, -3.0710805e-09, -0.324179053, 2.50523402e-09, 0.945995748)
                CFrameQuest = CFrame.new(-1927.91602, 37.7981339, -12842.5391, -0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, -0.250778586, 2.64211941e-08, -0.96804446)
         elseif MyLevel == 2300 or MyLevel <= 2324 then
               Mon = "Cocoa Warrior"
               LevelQuest = 1
               NameQuest = "ChocQuest1"
               NameMon = "Cocoa Warrior"
               PUK = CFrame.new(-103.987442, 141.551514, -12260.2188, 0.589523733, -3.54913752e-08, -0.80775106, 4.28455316e-08, 1, -1.26684059e-08, 0.80775106, -2.71401959e-08, 0.589523733)
               CFrameQuest = CFrame.new(231.742981, 25.3354111, -12199.0537, 0.998278677, -5.16006757e-08, 0.0586484075, 4.79685092e-08, 1, 6.33390442e-08, -0.0586484075, -6.04167383e-08, 0.998278677)
             elseif MyLevel == 2325 or MyLevel <= 2349 then
               Mon = "Chocolate Bar Battler"
               LevelQuest = 2
               NameQuest = "ChocQuest1"
               NameMon = "Chocolate Bar Battler"
               PUK = CFrame.new(617.304688, 80.6076355, -12580.6494, -0.485228658, 3.42073503e-09, -0.874387324, -4.0368306e-08, 1, 2.63139608e-08, 0.874387324, 4.80658215e-08, -0.485228658)
              CFrameQuest = CFrame.new(231.742981, 25.3354111, -12199.0537, 0.998278677, -5.16006757e-08, 0.0586484075, 4.79685092e-08, 1, 6.33390442e-08, -0.0586484075, -6.04167383e-08, 0.998278677)
              elseif MyLevel == 2350 or MyLevel <= 2374 then
               Mon = "Sweet Thief"
               LevelQuest = 1
               NameQuest = "ChocQuest2"
               NameMon = "Sweet Thief"
               PUK = CFrame.new(72.062767, 77.630722, -12640.4287, -0.62450999, -9.80953416e-08, 0.781016827, 1.42118917e-09, 1, 1.26735927e-07, -0.781016827, 8.02578199e-08, -0.62450999)
               CFrameQuest = CFrame.new(149.867218, 24.8196201, -12775.5283, -0.0371122323, -7.14229245e-08, -0.99931109, -6.93553162e-08, 1, -6.88964548e-08, 0.99931109, 6.6750637e-08, -0.0371122323)
             elseif MyLevel == 2375 or MyLevel <= 2399 then
               Mon = "Candy Rebel"
               LevelQuest = 2
               NameQuest = "ChocQuest2"
               NameMon = "Candy Rebel"  
               PUK = CFrame.new(420.127747, 109.63044, -12989.6035, 0.0957952142, 3.10210027e-08, 0.995401084, -9.46955225e-09, 1, -3.02529948e-08, -0.995401084, -6.52791066e-09, 0.0957952142)
              CFrameQuest = CFrame.new(149.867218, 24.8196201, -12775.5283, -0.0371122323, -7.14229245e-08, -0.99931109, -6.93553162e-08, 1, -6.88964548e-08, 0.99931109, 6.6750637e-08, -0.0371122323)
          elseif MyLevel == 2400 or MyLevel <= 2424 then
               Mon = "Candy Pirate"
               LevelQuest = 1
               NameQuest = "CandyQuest1"
               NameMon = "Candy Pirate"  
               PUK = CFrame.new(4-1218.0184326171875, 174.3348846435547, -14536.8603515625)
              CFrameQuest = CFrame.new(-1147.722900390625, 16.142282485961914, -14445.0546875)
           elseif MyLevel == 2425 or MyLevel <= 2449  then
               Mon = "Snow Demon"
               LevelQuest = 2
               NameQuest = "CandyQuest1"
               NameMon = "Snow Demon"  
               PUK = CFrame.new(-989.9094848632812, 142.46929931640625, -14594.7490234375)
              CFrameQuest = CFrame.new(-1147.722900390625, 16.142282485961914, -14445.0546875)
           elseif MyLevel == 2450 or MyLevel <= 2474 then
               Mon = "Isle Outlaw"
               LevelQuest = 1
               NameQuest = "TikiQuest1"
               NameMon = "Isle Outlaw"  
               PUK = CFrame.new(-16548.8164, 55.6059914, -172.8125, 0.213092566, -0, -0.977032006, 0, 1, -0, 0.977032006, 0, 0.213092566)
              CFrameQuest = CFrame.new(-16548.8164, 55.6059914, -172.8125, 0.213092566, -0, -0.977032006, 0, 1, -0, 0.977032006, 0, 0.213092566)
elseif MyLevel == 2475 or MyLevel <= 2524 then
               Mon = "Island Boy"
               LevelQuest = 2
               NameQuest = "TikiQuest1"
               NameMon = "Island Boy"  
               PUK = CFrame.new(-16548.8164, 55.6059914, -172.8125, 0.213092566, -0, -0.977032006, 0, 1, -0, 0.977032006, 0, 0.213092566)
              CFrameQuest = CFrame.new(-16548.8164, 55.6059914, -172.8125, 0.213092566, -0, -0.977032006, 0, 1, -0, 0.977032006, 0, 0.213092566)
elseif MyLevel == 2525 or MyLevel <= 2549 then
               Mon = "Isle Champion"
               LevelQuest = 2
               NameQuest = "TikiQuest2"
               NameMon = "Isle Champion"  
               PUK = CFrame.new(-16541.0215, 54.770813, 1051.46118, 0.0410757065, -0, -0.999156058, 0, 1, -0, 0.999156058, 0, 0.0410757065)
              CFrameQuest = CFrame.new(-16541.0215, 54.770813, 1051.46118, 0.0410757065, -0, -0.999156058, 0, 1, -0, 0.999156058, 0, 0.0410757065)
            elseif MyLevel == 2550 or MyLevel <= 2574 then
                Mon = "Serpent Hunter"
                LevelQuest = 1
                NameQuest = "TikiQuest3"
                NameMon = "Serpent Hunter"  
                PUK = CFrame.new(-16665.1914, 104.596405, 1579.69434, 0.951068401, -0, -0.308980465, 0, 1, -0, 0.308980465, 0, 0.951068401)
               CFrameQuest = CFrame.new(-16665.1914, 104.596405, 1579.69434, 0.951068401, -0, -0.308980465, 0, 1, -0, 0.308980465, 0, 0.951068401)
            elseif MyLevel >= 2575 then
                Mon = "Skull Slayer"
                LevelQuest = 2
                NameQuest = "TikiQuest3"
                NameMon = "Skull Slayer"  
                PUK = CFrame.new(-16665.1914, 104.596405, 1579.69434, 0.951068401, -0, -0.308980465, 0, 1, -0, 0.308980465, 0, 0.951068401)
               CFrameQuest = CFrame.new(-16665.1914, 104.596405, 1579.69434, 0.951068401, -0, -0.308980465, 0, 1, -0, 0.308980465, 0, 0.951068401)

          end
        end
    end
    
            Main:AddSeperatorLeft("Farm")


Main:AddToggleLeft("Auto Farm",AutoFarm,function(value)
        AutoFarm = value
        StopTween(AutoFarm)
    end)
    
    spawn(function()
        while wait() do
            if AutoFarm then
                pcall(function()
                    local QuestTitle = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text
                  
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                        StartMagnet = false
                        CheckQuest()
                        repeat wait() Tween(CFrameQuest) until (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not AutoFarm
                        if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
                            wait(1.2)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NameQuest,LevelQuest)
                            wait(0.5)
                        end
                    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                        CheckQuest()
                        if game:GetService("Workspace").Enemies:FindFirstChild(Mon) then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                    if v.Name == Mon then
                                        if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
                                            repeat task.wait()
                                                EquipWeapon(SelectWeapon)
                                                AutoHaki()                                            
                                                PosMon = v.HumanoidRootPart.CFrame
                                                Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,20,0))
                                                v.Head.CanCollide = false
                                                v.Humanoid.WalkSpeed = 0
                                                v.Head.CanCollide = false
                                                StartMagnet = true
                                            until not AutoFarm or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                        else
                                            StartMagnet = false
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                                        end
                                    end
                                end
                            end
                        else
                            StartMagnet = false
							StopClick()
                            if game:GetService("ReplicatedStorage"):FindFirstChild(Mon) then
                                Tween(game:GetService("ReplicatedStorage"):FindFirstChild(Mon).HumanoidRootPart.CFrame * CFrame.new(0,0,0))
                            else
                                if (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 200 then
                                    if PUK ~= nil then
                                        Tween(PUK * CFrame.new(0,0,0))
                                    else
                                        if OldPos ~= nil then
                                            Tween(OldPos.Position)
                                            end 
                                            end 
                                            else 
                                              StartMagnet = false 
                                              Tween(PUK)
                                            end 
                                            end
                                            end
                                            end
                                            end)
                                            end
                                            end
                                            end)
                                                
    if World1 then
        Main:AddToggleLeft("Auto New World",AutoNewWorld,function(value)
            AutoNewWorld = value
            StopTween(AutoNewWorld)
        end)
    
        spawn(function()
            while wait() do 
                if AutoNewWorld then
                    pcall(function()
                        local MyLevel = game:GetService("Players").LocalPlayer.Data.Level.Value
                        if MyLevel >= 700 and World1 then
                            if game:GetService("Workspace").Map.Ice.Door.CanCollide == true and game:GetService("Workspace").Map.Ice.Door.Transparency == 0 then
                                local CFrame1 = CFrame.new(4849.29883, 5.65138149, 719.611877)
                                repeat Tween(CFrame1) wait() until (CFrame1.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or AutoSecondSea == false
                                wait(1.1)
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("DressrosaQuestProgress","Detective")
                                wait(0.5)
                                EquipWeapon("Key")
                                repeat Tween(CFrame.new(1347.7124, 37.3751602, -1325.6488)) wait() until (Vector3.new(1347.7124, 37.3751602, -1325.6488)-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or AutoSecondSea == false
                                wait(0.5)
                            else
                                if game:GetService("Workspace").Map.Ice.Door.CanCollide == false and game:GetService("Workspace").Map.Ice.Door.Transparency == 1 then
                                    if game:GetService("Workspace").Enemies:FindFirstChild("Ice Admiral") then
                                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                            if v.Name == "Ice Admiral" then
                                                if not v.Humanoid.Health <= 0 then
                                                    if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                                        OldCFrameSecond = v.HumanoidRootPart.CFrame
                                                        repeat task.wait()
                                                            AutoHaki()
                                                            EquipWeapon(SelectWeapon)
                                                            v.HumanoidRootPart.CanCollide = false
                                                            v.Humanoid.WalkSpeed = 0
                                                            v.Head.CanCollide = false
                                                            v.HumanoidRootPart.CFrame = OldCFrameSecond
                                                            Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                                            game:GetService("VirtualUser"):CaptureController()
                                                            game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                                            sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                                        until not AutoNewWorld or not v.Parent or v.Humanoid.Health <= 0
                                                    end
                                                else 
                                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
                                                end
                                            end
                                        end
                                    else
                                        if game:GetService("ReplicatedStorage"):FindFirstChild("Ice Admiral") then
                                            Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Ice Admiral").HumanoidRootPart.CFrame * CFrame.new(0,45,0))
                                        end
                                    end
                                end
                            end
                        end
                    end)
                end
            end
        end)
    end
    
    if World2 then
        Main:AddToggleLeft("Auto Third Sea",AutoThirdSea,function(value)
            AutoThirdSea = value
            StopTween(AutoThirdSea)
        end)
    
        spawn(function()
            while wait() do
                if AutoThirdSea then
                    pcall(function()
                        if game:GetService("Players").LocalPlayer.Data.Level.Value >= 1500 and World2 then
                            AutoFarm = false
                            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ZQuestProgress","Check") == 0 then
                                Tween(CFrame.new(-1926.3221435547, 12.819851875305, 1738.3092041016))
                                if (CFrame.new(-1926.3221435547, 12.819851875305, 1738.3092041016).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10 then
                                    wait(1.5)
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ZQuestProgress","Begin")
                                end
                                wait(1.8)
                                if game:GetService("Workspace").Enemies:FindFirstChild("rip_indra") then
                                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                        if v.Name == "rip_indra" then
                                            OldCFrameThird = v.HumanoidRootPart.CFrame
                                            repeat task.wait()
                                                AutoHaki()
                                                EquipWeapon(SelectWeapon)
                                                Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                                v.HumanoidRootPart.CFrame = OldCFrameThird
                                               
                                                v.HumanoidRootPart.CanCollide = false
                                                v.Humanoid.WalkSpeed = 0
                                                game:GetService'VirtualUser':CaptureController()
                                                game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
                                                sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                            until AutoThirdSea == false or v.Humanoid.Health <= 0 or not v.Parent
                                        end
                                    end
                                elseif not game:GetService("Workspace").Enemies:FindFirstChild("rip_indra") and (CFrame.new(-26880.93359375, 22.848554611206, 473.18951416016).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1000 then
                                    Tween(CFrame.new(-26880.93359375, 22.848554611206, 473.18951416016))
                                end
                            end
                        end
                    end)
                end
            end
        end)
    end
    
    if World2 then
        Main:AddToggleLeft("Auto Factory",AutoFactory,function(value)
            AutoFactory = value
            StopTween(AutoFactory)
        end)
    
        spawn(function()
            while wait() do
                pcall(function()
                    if AutoFactory then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Core") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Core" and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()         
                                        EquipWeapon(SelectWeapon)           
                                        Tween(CFrame.new(448.46756, 199.356781, -441.389252))                                  
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until v.Humanoid.Health <= 0 or AutoFactory == false
                                end
                            end
                        else
                            Tween(CFrame.new(448.46756, 199.356781, -441.389252))
                        end
                    end
                end)
            end
        end)
    end
    
    
    
      
     

    
    
    Main:AddSeperatorLeft("Mob Aura")
    DistanceAura = 1000
    Main:AddSliderLeft("Distance Bob Aura",1,5000,DistanceAura,function(a)
        DistanceAura = a
    end)
    
    Main:AddToggleLeft("Mob Aura",nil,function(a)
        MobAura = a 
        end)
    
    spawn(function()
			while wait() do
				pcall(function()
					if  MobAura then
						for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
							if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and (v.HumanoidRootPart.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= DistanceAura then
								repeat wait()
									AutoHaki()
									EquipWeapon(SelectWeapon)
									PosMon = v.HumanoidRootPart.CFrame
									Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,45,0))
									v.HumanoidRootPart.Transparency = 0
									v.Humanoid.JumpPower = 0
									v.Humanoid.WalkSpeed = 0
									v.HumanoidRootPart.CanCollide = false
								until not  MobAura or not v.Parent or v.Humanoid.Health <= 0
							end
						end
					else StopClick()
					end
				end)
		end
	end)

        function TP2(Point)
	local Ply = game.Players.LocalPlayer
	local Char = Ply.Character
--	repeat
	Char.Humanoid:ChangeState(15)
	Char.HumanoidRootPart.CFrame = Point
	wait()
	Char.HumanoidRootPart.CFrame = Point
--	until (Char.HumanoidRootPart.Position - Point.Position).Magnitude <= 20
end
function BTP(Pos)
	local Ply = game.Players.LocalPlayer
	local Char = Ply.Character
	Char.HumanoidRootPart.CFrame = Pos
	wait()
	Char.HumanoidRootPart.CFrame = Pos
end
    


Main:AddSeperatorLeft("Race V4")

Race = Main:AddLabelLeft("Gear Chack : You Not Unlock")

 spawn(function()
        pcall(function()
            while wait() do
                if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("UpgradeRace","Check") == 0 then
                Race:Set("Gear Chack : Not Quest")
                elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("UpgradeRace","Check") == 5 then
                Race:Set("Gear Chack : Quest Fully")
                elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("UpgradeRace","Check") == 6 or game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("UpgradeRace","Check") <= 9  then
                Race:Set("Gear Chack : Have Quest")
                end
            end
        end)
    end)

Main:AddToggleLeft("Auto Ancient One",nil,function(a)
    QuestOne = a
    UpgradeRace = a
    StopTween()
end)

spawn(function()
            while wait() do
                if UpgradeRace then
                    pcall(function()
                             game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("UpgradeRace","Buy")
                            end)
                            end
                            end
end)

 spawn(function()
        pcall(function()
            while wait() do
                if UpgradeRace then
                    game:GetService("Players").LocalPlayer.Backpack.Awakening.RemoteFunction:InvokeServer(true)
                    end
            end
        end)
            end)
no = game.Players.LocalPlayer.Name

spawn(function()
            while wait() do
                if QuestOne then
                            pcall(function()
                   if game:GetService("Workspace").Characters[no].RaceEnergy.Value == 0 then
                  Auto_Bone2 = true
                else
                 if game:GetService("Workspace").Characters[no].RaceParticle then
                   Auto_Bone2 = false
                   wait(2)
                   Tween(CFrame.new(-10266.6787, 507.539215, 6232.93994, -0.32111761, 2.04228925e-11, -0.947039306, 2.5864427e-08, 1, -8.74842243e-09, 0.947039306, -2.73039031e-08, -0.32111761))
                   else if QuestOne == false then
                   Auto_Bone = false
                    end
                end
                end
                end)
            end
    end
end)

Main:AddToggleLeft("TP to Gear",nil,function(a)
Gear = a
StopTween(Gear)
end)

spawn(function()
        while wait(.01) do
            if Auto_Gear then
                for i,v in pairs(game:GetService("Workspace").Map:FindFirstChild('MysticIsland'):GetChildren()) do
                    if v.Name == "Part" then
                        if v.ClassName == "MeshPart" then
                            toTarget(v.CFrame)
                            v.Transparency = 0
                    end
                    end
                end
            end
        end
    end)




Main:AddButtonLeft("TP To Door Race V4",function(a)
StopTween()
 er(CFrame.new(28286.3555, 14896.5342, 102.624695, 0, 0, -1, 0, 1, 0, 1, 0, 0))
 wait(0.1)
					if game.Players.LocalPlayer.Data.Race.Value == 'Mink' then
Tween(CFrame.new(29013.1074, 14890.668, -380.353577, -0.0909729972, 6.77932599e-09, -0.995853364, 1.49823745e-08, 1, 5.43888756e-09, 0.995853364, -1.44254555e-08, -0.0909729972))						
					elseif game.Players.LocalPlayer.Data.Race.Value == 'Human' then
Tween(CFrame.new(29227.4531, 14890.668, -207.82518, -0.0596670099, -7.85952849e-08, -0.998218358, 4.29681641e-08, 1, -8.13039236e-08, 0.998218358, -4.77427697e-08, -0.0596670099))						
					elseif game.Players.LocalPlayer.Data.Race.Value == 'Skypiea' then
Tween(CFrame.new(28962.5059, 14919.3164, 233.624634, 0.00990177877, -8.15174346e-08, -0.999951005, -1.69766246e-08, 1, -8.16895422e-08, 0.999951005, 1.77846644e-08, 0.00990177877))						
					elseif game.Players.LocalPlayer.Data.Race.Value == 'Ghoul' then
						Tween(CFrame.new(28672.502, 14890.3711, 445.8992, -0.998591304, -4.18291286e-08, -0.0530602336, -4.28831797e-08, 1, 1.87266753e-08, 0.0530602336, 2.0975687e-08, -0.998591304))
					elseif game.Players.LocalPlayer.Data.Race.Value == 'Cyborg' then
Tween(CFrame.new(28497.998, 14895.668, -419.940063, 0.0159061812, -1.62209535e-08, 0.999873459, -2.05521484e-08, 1, 1.65499543e-08, -0.999873459, -2.0812795e-08, 0.0159061812))				
				elseif game.Players.LocalPlayer.Data.Race.Value == 'Fishman' then
				Tween(CFrame.new(28235.9121, 14890.668, -211.285461, -0.0216744486, 1.86037497e-08, 0.999765098, -6.29063308e-08, 1, -1.99719015e-08, -0.999765098, -6.33244355e-08, -0.0216744486))
			end
			
end)




              
Main:AddToggleLeft("Auto Win Trial",Auto_Win_Trial,function(a)
Auto_Win_Trial = a
StopTween()
if Auto_Win_Trial then
					if game.Players.LocalPlayer.Data.Race.Value == 'Mink' then
						          er(CFrame.new(game:GetService("Workspace").StartPoint.Position))
					elseif game.Players.LocalPlayer.Data.Race.Value == 'Human' then
						human = true
						
					elseif game.Players.LocalPlayer.Data.Race.Value == 'Skypiea' then
          er(CFrame.new(game:GetService("Workspace").Map.SkyTrial.Model.FinishPart.Position))						
					elseif game.Players.LocalPlayer.Data.Race.Value == 'Ghoul' then
						ghoul = true
						
					elseif game.Players.LocalPlayer.Data.Race.Value == 'Cyborg' then
					    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,300,0)
					end
				   if Auto_Win_Trial == false then
				   human = false
				   ghoul = false
				   end
				end
end)



    
    spawn(function()
        while wait() do 
            if human and World3 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Flame Master [Lv. 1100]") or game:GetService("Workspace").Enemies:FindFirstChild("Darkness Master [Lv. 1100]") or game:GetService("Workspace").Enemies:FindFirstChild("Light Master [Lv. 1100]") or game:GetService("Workspace").Enemies:FindFirstChild("Rumble Master [Lv. 1100]") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Flame Master [Lv. 1100]" or v.Name == "Darkness Master [Lv. 1100]" or v.Name == "Light Master [Lv. 1100]" or v.Name == "Rumble Master [Lv. 1100]" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnethuman = true
                                        PosMonhuman = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not human or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnethuman = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Flame Master [Lv. 1100]") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Flame Master [Lv. 1100]").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                              elseif game:GetService("ReplicatedStorage"):FindFirstChild("Darkness Master [Lv. 1100]") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Darkness Master [Lv. 1100]").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                              elseif game:GetService("ReplicatedStorage"):FindFirstChild("Light Master [Lv. 1100]") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Light Master [Lv. 1100]").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                              elseif game:GetService("ReplicatedStorage"):FindFirstChild("Rumble Master [Lv. 1100]") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Rumble Master [Lv. 1100]").HumanoidRootPart.CFrame * CFrame.new(0,30,0))

                            end
                        end
                    end
                end)
            end
        end
    end)

    
    spawn(function()
        while wait() do 
            if ghoul and World3 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Ancient Zombie [Lv. 2000]") or game:GetService("Workspace").Enemies:FindFirstChild("Ancient Vampire [Lv. 2000]") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Ancient Zombie [Lv. 2000]" or v.Name == "Ancient Vampire [Lv. 2000]" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetghoul = true
                                        PosMonghoul = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not ghoul or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetghoul = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Ancient Vampire [Lv. 2000]") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Ancient Vampire [Lv. 2000]").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                              elseif game:GetService("ReplicatedStorage"):FindFirstChild("Ancient Zombie [Lv. 2000]") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Ancient Zombie [Lv. 2000]").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
                end)
            end
        end
    end)

      
      spawn(function()
    while task.wait() do
        if Sea1 then
            pcall(function()
               for i,v in pairs(game:GetService("Workspace").SeaBeasts:GetChildren()) do
                 if v:FindFirstChild("HumanoidRootPart") then
                    Tween(v.HumanoidRootPart.CFrame*CFrame.new(0,700,0))
                     EquipWeapon(SelectWeapon)
                     AutoHaki()
                 game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
                 game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                 wait(1)
				 game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
				 game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
				 wait(1)
				 game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
				 game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
				 wait(1)
				 game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
				 game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)
               end
                end
            end)
        end
    end
end)

     
    



local Bone = Main:AddLabelLeft("Bone : 0")


spawn(function()
    while wait(3) do
        pcall(function()
for i,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
    if v["Type"] == "Material" then
    if v.Name == "Bones" then
            Bone:Set("Bone : "..v.Count)
    end
    end
end

        end)
    end
end)


local BoneFarm = Main:AddToggleLeft("Farm Bone",Auto_Bone2,function(value)
        Auto_Bone2 = value
        StopTween(Auto_Bone2)
    end)
    
    spawn(function()
        while wait() do 
            if Auto_Bone2 and World3 then
                pcall(function()
        if not game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton") or not game:GetService("Workspace").Enemies:FindFirstChild("Living Zombie") or not game:GetService("Workspace").Enemies:FindFirstChild("Demonic Soul") or not game:GetService("Workspace").Enemies:FindFirstChild("Posessed Mummy") then
                                  Tween(CFrame.new(-9515.3720703125, 164.00624084473, 5786.0610351562))

                                  end
                    if game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton") or game:GetService("Workspace").Enemies:FindFirstChild("Living Zombie") or game:GetService("Workspace").Enemies:FindFirstChild("Demonic Soul") or game:GetService("Workspace").Enemies:FindFirstChild("Posessed Mummy") then

for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Reborn Skeleton" or v.Name == "Living Zombie" or v.Name == "Demonic Soul" or v.Name == "Posessed Mummy" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then

                                    repeat task.wait()

                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetBoneMon2 = true
                                        PosMonBone2 = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,40,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not Auto_Bone2 or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetBoneMon2 = false
                                          
                        end

               end)
            end
        end
    end)
    
    Main:AddToggleLeft("Redeam bone",Auto_Random_Bone,function(value)
        Auto_Random_Bone = value
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if Auto_Random_Bone then    
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Buy",1,1)
                end
            end
        end)
    end)
    
       Main:AddSeperatorLeft("Mastery")
    
     Kill_At = 31
    Main:AddSliderLeft("Kill At %",1,100,Kill_At,function(value)
        Kill_At = value
    end)
    
    Main:AddToggleLeft("Auto Farm BF Fast",AutoFarmFruit,function(a)
    AutoFarmFruit = a
            StopTween()
    if AutoFarmFruit == false then
            UseSkill2 = false 
        end
    end)
    
    Main:AddToggleLeft("Auto Farm BF Mastery",AutoFarmFruitMastery,function(value)
        AutoFarmFruitMastery = value
        StopTween(AutoFarmFruitMastery)
        if AutoFarmFruitMastery == false then
            UseSkill = false 
        end
    end)
    spawn(function()
    local gg = getrawmetatable(game)
    local old = gg.__namecall
    setreadonly(gg,false)
    gg.__namecall = newcclosure(function(...)
        local method = getnamecallmethod()
        local args = {...}
        if tostring(method) == "FireServer" then
            if tostring(args[1]) == "RemoteEvent" then
                if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
                    if UseSkill2 then
                        args[2] = PosMonBone2.Position
                        return old(unpack(args))
                    end
                end
            end
        end
        return old(...)
    end)
end)

spawn(function()
        while wait() do
            if UseSkill2 then
                pcall(function()
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if game:GetService("Players").LocalPlayer.Character:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
                            MasBF = game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Data.DevilFruit.Value].Level.Value
                        elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
                            MasBF = game:GetService("Players").LocalPlayer.Backpack[game:GetService("Players").LocalPlayer.Data.DevilFruit.Value].Level.Value
                        end
                        if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon-Dragon") then                      
                            if SkillZ then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                        
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then          
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))               
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                          
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                wait(2)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                        elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Venom-Venom") then   
                            if SkillZ then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                        
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then        
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))               
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then 
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                          
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                wait(2)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                            elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Paw-Paw") then   
                            if SkillZ then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                        
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then        
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))               
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then 
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                          
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                        elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Human-Human: Buddha") then
                            if SkillZ and game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Size == Vector3.new(2, 2.0199999809265, 1) then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                         
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                            if SkillV then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)
                            end
                        elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
                            if SkillZ then 
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                         
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                            if SkillV then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)
                            end
                            else
                            if SkillZ then 
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                         
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                            if SkillV then
                                local args = {
                                    [1] = PosMonBone2.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)
                            end
                        end
                    end
                end)
            end
        end
    end)

spawn(function()
        while wait() do 
            if AutoFarmFruit and World3 then
                pcall(function()
        if not game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton") or not game:GetService("Workspace").Enemies:FindFirstChild("Living Zombie") or not game:GetService("Workspace").Enemies:FindFirstChild("Demonic Soul") or not game:GetService("Workspace").Enemies:FindFirstChild("Posessed Mummy") then
                                  Tween(CFrame.new(-9515.3720703125, 164.00624084473, 5786.0610351562))
                                  end
                    if game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton") or game:GetService("Workspace").Enemies:FindFirstChild("Living Zombie") or game:GetService("Workspace").Enemies:FindFirstChild("Demonic Soul") or game:GetService("Workspace").Enemies:FindFirstChild("Posessed Mummy") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Reborn Skeleton" or v.Name == "Living Zombie" or v.Name == "Demonic Soul" or v.Name == "Posessed Mummy" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    HealthMs = v.Humanoid.MaxHealth * Kill_At/100
                                    repeat task.wait()
                                        if v.Humanoid.Health <= HealthMs then
                                                    AutoHaki()
                                                    EquipWeapon(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
                                                    Tween(v.HumanoidRootPart.CFrame * CFrame.new(Distance_X,Distance_Y,Distance_Z))
                                                    v.HumanoidRootPart.CanCollide = false
                                                    PosMonBone2 = v.HumanoidRootPart.CFrame
                                                    v.Humanoid.WalkSpeed = 0
                                                    v.Head.CanCollide = false
                                                    UseSkill2 = true
                                                    else
                                        UseSkill2 = false
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetBoneMon2 = true
                                        PosMonBone2 = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,40,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                        end
                                        
                                        
                                    until not AutoFarmFruit or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetBoneMon2 = false
                      
                        end

               end)
            end
        end
    end)

    spawn(function()
        while wait() do
            if AutoFarmFruitMastery then
                pcall(function()
                    local QuestTitle = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text
                    if not string.find(QuestTitle, NameMon) then
                        Magnet = false
                        UseSkill = false
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                    end
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                        StartMasteryFruitMagnet = false
                        UseSkill = false
                        CheckQuest()
                        repeat wait()
                            Tween(CFrameQuest)
                        until (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not AutoFarmFruitMastery
                        if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
                            wait(1.2)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NameQuest,LevelQuest)
                            wait(0.5)
                        end
                    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                        CheckQuest()
                        if game:GetService("Workspace").Enemies:FindFirstChild(Mon) then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                    if v.Name == Mon then
                                        if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
                                            HealthMs = v.Humanoid.MaxHealth * Kill_At/100
                                            repeat task.wait()
                                                if v.Humanoid.Health <= HealthMs then
                                                    AutoHaki()
                                                    EquipWeapon(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
                                                    Tween(v.HumanoidRootPart.CFrame * CFrame.new(Distance_X,Distance_Y,Distance_Z))
                                                    v.HumanoidRootPart.CanCollide = false
                                                    PosMonMasteryFruit = v.HumanoidRootPart.CFrame
                                                    v.Humanoid.WalkSpeed = 0
                                                    v.Head.CanCollide = false
                                                    UseSkill = true
                                                else           
                                                    UseSkill = false 
                                                    AutoHaki()
                                                    EquipWeapon(SelectWeapon)
                                                    Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,40,0))
                                                    v.HumanoidRootPart.CanCollide = false
                                                    PosMonMasteryFruit = v.HumanoidRootPart.CFrame
                                                    v.Humanoid.WalkSpeed = 0
                                                    v.Head.CanCollide = false
                                                    game:GetService'VirtualUser':CaptureController()
                                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                                end
                                                StartMasteryFruitMagnet = true
                                                game:GetService'VirtualUser':CaptureController()
                                            until not AutoFarmFruitMastery or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                        else
                                            UseSkill = false
                                            StartMasteryFruitMagnet = false
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                                        end
                                    end
                                end
                            end
                        else
                            StartMasteryFruitMagnet = false   
                            UseSkill = false 
                            local Mob = game:GetService("ReplicatedStorage"):FindFirstChild(Mon) 
                            if Mob then
                                Tween(Mob.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                            else
                                if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.Y <= 1 then
                                    game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = true
                                    task.wait()
                                    game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = false
                                end
                            end
                        end
                    end
                end)
            end
        end
    end)
    
     spawn(function()
        while wait() do
            if UseSkill then
                pcall(function()
                    CheckQuest()
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if game:GetService("Players").LocalPlayer.Character:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
                            MasBF = game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Data.DevilFruit.Value].Level.Value
                        elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
                            MasBF = game:GetService("Players").LocalPlayer.Backpack[game:GetService("Players").LocalPlayer.Data.DevilFruit.Value].Level.Value
                        end
                        if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon-Dragon") then                      
                            if SkillZ then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                        
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then          
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))               
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                          
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                wait(2)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                        elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Venom-Venom") then   
                            if SkillZ then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                        
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then        
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))               
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then 
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                          
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                wait(2)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                            elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Paw-Paw") then   
                            if SkillZ then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                        
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then        
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))               
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then 
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                          
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                        elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Human-Human: Buddha") then
                            if SkillZ and game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Size == Vector3.new(2, 2.0199999809265, 1) then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                         
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                            if SkillV then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)
                            end
                        elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
                            if SkillZ then 
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                         
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
                            end
                            if SkillX then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
                            end
                            if SkillC then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))                           
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
                            end
                            if SkillV then
                                local args = {
                                    [1] = PosMonMasteryFruit.Position
                                }
                                game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
                                game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
                                game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)
                            end
                        end
                    end
                end)
            end
        end
    end)
    
spawn(function()
    local gg = getrawmetatable(game)
    local old = gg.__namecall
    setreadonly(gg,false)
    gg.__namecall = newcclosure(function(...)
        local method = getnamecallmethod()
        local args = {...}
        if tostring(method) == "FireServer" then
            if tostring(args[1]) == "RemoteEvent" then
                if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
                    if UseSkill then
                        args[2] = PosMonMasteryFruit.Position
                        return old(unpack(args))
                    end
                end
            end
        end
        return old(...)
    end)
end)
    

    
    spawn(function()
        game:GetService("RunService").RenderStepped:Connect(function()
            pcall(function()
                if UseSkill then
                    for i,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.Notifications:GetChildren()) do
                        if v.Name == "NotificationTemplate" then
                            if string.find(v.Text,"Skill locked!") then
                                v:Destroy()
                            end
                        end
                    end
                end
            end)
        end)
    end)
    
    spawn(function()
        pcall(function()
            game:GetService("RunService").RenderStepped:Connect(function()
                if UseSkill then
                    local args = {
                        [1] = PosMonMasteryFruit.Position
                    }
                    game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Data.DevilFruit.Value].RemoteEvent:FireServer(unpack(args))
                end
            end)
        end)
    end)
    
    spawn(function()
        pcall(function()
            game:GetService("RunService").RenderStepped:Connect(function()
                if UseClick then
                    local args = {
                        [1] = PosMonMasteryGun.Position
                    }
                    game:GetService("Players").LocalPlayer.Character[SelectWeaponGun].RemoteEvent:FireServer(unpack(args))
                end
            end)
        end)
    end)
    
    spawn(function()
	local gg = getrawmetatable(game)
	local old = gg.__namecall
	setreadonly(gg,false)
	gg.__namecall = newcclosure(function(...)
		local method = getnamecallmethod()
		local args = {...}
		if tostring(method) == "FireServer" then
			if tostring(args[1]) == "RemoteEvent" then
				if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
					if UseSkillMasteryDevilFruit and  AutoFarmGunMastery then
						if type(args[2]) == "vector" then 
							args[2] = PosMonMasteryGun
						else
							args[2] = CFrame.new(PosMonMasteryGun)
						end
						return old(unpack(args))
					end
				end
			end
		end
		return old(...)
	end)
end)
    
    spawn(function()
	local gt = getrawmetatable(game)
	local old = gt.__namecall
	setreadonly(gt,false)
	gt.__namecall = newcclosure(function(...)
		local args = {...}
		if getnamecallmethod() == "InvokeServer" then 
			if SelectWeaponGun then
				if SelectWeaponGun == "Soul Guitar" then
					if tostring(args[2]) == "TAP" then
						if AutoFarmGunMastery and UseSkillMasteryGun then
							args[3] = PosMonMasteryGun
						end
					end
				end
			end
		end
		return old(unpack(args))
	end)
	setreadonly(gt,true)
end)
    
    Main:AddToggleLeft("Auto Farm Gun Mastery",AutoFarmGunMastery,function(value)
        AutoFarmGunMastery = value
        StopTween(AutoFarmGunMastery)
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if AutoFarmGunMastery then
                    local QuestTitle = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text
                    if not string.find(QuestTitle, NameMon) then
                        Magnet = false                                      
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                    end
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                        StartMasteryGunMagnet = false
                        CheckQuest()
                        Tween(CFrameQuest)
                        if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10 then
                            wait(1.2)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NameQuest, LevelQuest)
                        end
                    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                        CheckQuest()
                        if game:GetService("Workspace").Enemies:FindFirstChild(Mon) then
                            pcall(function()
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if v.Name == Mon then
                                      PosMonMasteryGun = v.HumanoidRootPart.CFrame
                                        repeat task.wait()
                                            if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
                                                HealthMin = v.Humanoid.MaxHealth * Kill_At/100
                                                if v.Humanoid.Health <= HealthMin then 
                                                UseSkillMasteryGun = true
                                                    EquipWeapon(SelectWeaponGun)
                                                    Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,15,0))
                                                    v.Humanoid.WalkSpeed = 0
                                                    v.HumanoidRootPart.CanCollide = false
								local args = {
									[1] = v.HumanoidRootPart.Position,
									[2] = v.HumanoidRootPart
								}
								game:GetService("Players").LocalPlayer.Character[SelectWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(args))
                                                    else
                                                    UseSkillMasteryGun = false
                                                    AutoHaki()
                                                    EquipWeapon(SelectWeapon)
                                                    v.Humanoid.WalkSpeed = 0
                                                    v.HumanoidRootPart.CanCollide = false
                                                    v.Head.CanCollide = false               
                                                    Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,40,0))
                                                    game:GetService'VirtualUser':CaptureController()
                                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                                end
                                                StartMasteryGunMagnet = true 
                                            else
                                                StartMasteryGunMagnet = false
                                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                                            end
                                        until v.Humanoid.Health <= 0 or AutoFarmGunMastery == false or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                      UseSkillMasteryGun = false
                                      StartMasteryGunMagnet = false
                                    end
                                end
                            end)
                        else
                            StartMasteryGunMagnet = false
                            local Mob = game:GetService("ReplicatedStorage"):FindFirstChild(Mon) 
                            if Mob then
                                Tween(Mob.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            else
                                if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.Y <= 1 then
                                    game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = true
                                    task.wait()
                                    game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = false
                                end
                            end
                        end 
                    end
                end
            end
        end)
    end)
    
     Main:AddSeperatorLeft("Distance Mastery Fram")
  Distance_X = 0
    Main:AddSliderLeft("X",1,100,Distance_X,function(value)
        Distance_X = value
    end)
    Distance_Y = 50
    Main:AddSliderLeft("Y",1,100,Distance_Y,function(value)
        Distance_Y = value
    end)
    Distance_Z = 0
    Main:AddSliderLeft("Z",1,100,Distance_Z,function(value)
        Distance_Z = value
    end)
    Main:AddSeperatorLeft("Fruits Skill Settings")
    
    Main:AddToggleLeft("Skill Z",true,function(value)
        SkillZ = value
    end)
    
    Main:AddToggleLeft("Skill X",true,function(value)
        SkillX = value
    end)
    
    Main:AddToggleLeft("Skill C",true,function(value)
        SkillC = value
    end)
    
    Main:AddToggleLeft("Skill V",true,function(value)
        SkillV = value
    end)
    
    Main:AddSeperatorLeft("Boss")
Boss = {}

for i, v in pairs(game.ReplicatedStorage:GetChildren()) do
if v.Name == "Cyborg" or v.Name == "The Gorilla King" or v.Name == "Wysper" or v.Name == "Thunder God" or v.Name == "Mob Leader" or v.Name == "Bobby" or v.Name == "Saber Expert" or v.Name == "Warden" or v.Name == "Chief Warden" or v.Name == "Swan" or v.Name == "Magma Admiral"  or v.Name == "Fishman Lord" or v.Name == "Wysper" or v.Name == "Ice Admiral" or v.Name == "Diamond" or v.Name == "Jeremy" or v.Name == "Fajita" or v.Name == "Don Swan" or v.Name == "Smoke Admiral" or v.Name == "Awakened Ice Admiral" or v.Name == "Tide Keeper" or v.Name == "Darkbeard" or v.Name == "Stone" or v.Name == "Island Empress" or v.Name == "Kilo Admiral" or v.Name == "Captain Elephant" or v.Name == "Beautiful Pirate" or v.Name == "Longma" or v.Name == "Cake Queen" or v.Name == "Greybeard" or v.Name == "Order" or v.Name == "Cursed Captain" or v.Name == "Soul Reaper" or v.Name == "Rip indra" or v.Name == "Mihawk Boss" or v.Name == "Cake Prince" or v.Name == "Dough King" or v.Name == "Cursed Skeleton Boss" or v.Name == "Factory" 
then
table.insert(Boss, v.Name)
end
end

    local BossName = Main:AddDropdownLeft("Select Boss",Boss,function(value)
        SelectBoss = value
    end)
    
    Main:AddButtonLeft("Reset Boss",function()                            
    BossName:Clear()
for i, v in pairs(game.ReplicatedStorage:GetChildren()) do
if v.Name == "Cyborg" or v.Name == "The Gorilla King" or v.Name == "Wysper" or v.Name == "Thunder God" or v.Name == "Mob Leader" or v.Name == "Bobby" or v.Name == "Saber Expert" or v.Name == "Warden" or v.Name == "Chief Warden" or v.Name == "Swan" or v.Name == "Magma Admiral"  or v.Name == "Fishman Lord" or v.Name == "Wysper" or v.Name == "Ice Admiral" or v.Name == "Diamond" or v.Name == "Jeremy" or v.Name == "Fajita" or v.Name == "Don Swan" or v.Name == "Smoke Admiral" or v.Name == "Awakened Ice Admiral" or v.Name == "Tide Keeper" or v.Name == "Darkbeard" or v.Name == "Stone" or v.Name == "Island Empress" or v.Name == "Kilo Admiral" or v.Name == "Captain Elephant" or v.Name == "Beautiful Pirate" or v.Name == "Longma" or v.Name == "Cake Queen" or v.Name == "Greybeard" or v.Name == "Order" or v.Name == "Cursed Captain" or v.Name == "Soul Reaper" or v.Name == "Rip indra" or v.Name == "Mihawk Boss" or v.Name == "Cake Prince" or v.Name == "Dough King" or v.Name == "Cursed Skeleton Boss" or v.Name == "Factory" 
then
table.insert(Boss, v.Name)
BossName:Add(v.Name) 
end
end
end)
    
    Main:AddToggleLeft("Auto Boss",AutoFarmBoss,function(value)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
        AutoFarmBoss = value
        StopTween(AutoFarmBoss)
    end)
    
    spawn(function()
        while wait() do
            if AutoFarmBoss then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild(SelectBoss) then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == SelectBoss then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,20,0))
                                        sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                    until not AutoFarmBoss or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        if game:GetService("ReplicatedStorage"):FindFirstChild(SelectBoss) then
                            Tween(game:GetService("ReplicatedStorage"):FindFirstChild(SelectBoss).HumanoidRootPart.CFrame * CFrame.new(0,49,0))
                        end
                    end
                end)
            end
        end
    end)
    
    Main:AddToggleLeft("Auto Boss All",AutoAllBoss,function(value)
        AutoAllBoss = value
        StopTween(AutoAllBoss)
    end)
    
    Main:AddToggleLeft("Auto Boss All Hop",AutoAllBossHop,function(value)
        AutoAllBossHop = value
    end)
    
    spawn(function()
        while wait() do
            if AutoAllBoss then
                pcall(function()
                    for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do		
	             if v.Name == "Cyborg" or v.Name == "The Gorilla King" or v.Name == "Wysper" or v.Name == "Thunder God" or v.Name == "Mob Leader" or v.Name == "Bobby" or v.Name == "Saber Expert" or v.Name == "Warden" or v.Name == "Chief Warden" or v.Name == "Swan" or v.Name == "Magma Admiral"  or v.Name == "Fishman Lord" or v.Name == "Wysper" or v.Name == "Ice Admiral" or v.Name == "Diamond" or v.Name == "Jeremy" or v.Name == "Fajita" or v.Name == "Don Swan" or v.Name == "Smoke Admiral" or v.Name == "Awakened Ice Admiral" or v.Name == "Tide Keeper" or v.Name == "Darkbeard" or v.Name == "Stone" or v.Name == "Island Empress" or v.Name == "Kilo Admiral" or v.Name == "Captain Elephant" or v.Name == "Beautiful Pirate" or v.Name == "Longma" or v.Name == "Cake Queen" or v.Name == "Greybeard" or v.Name == "Order" or v.Name == "Cursed Captain" or v.Name == "Soul Reaper" or v.Name == "Rip indra" or v.Name == "Mihawk Boss" or v.Name == "Cake Prince" or v.Name == "Dough King" or v.Name == "Cursed Skeleton Boss" or v.Name == "Factory" then
                            if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 17000 then
                                repeat task.wait()
                                    AutoHaki()
                                    EquipWeapon(SelectWeapon)
                                    v.Humanoid.WalkSpeed = 0
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Head.CanCollide = false
                                    Tween(v.HumanoidRootPart.CFrame*CFrame.new(0,45,0))
                                    game:GetService'VirtualUser':CaptureController()
                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                    sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
                                until v.Humanoid.Health <= 0 or AutoAllBoss == false or not v.Parent
                            end
                        else
                            if AutoAllBossHop then
                                Hop()
                            end
                        end
                    end
                end)
            end
        end
    end)
    
    Main:AddSeperatorLeft("Farm Valuable")
    
    Main:AddToggleLeft("Dragon Scale",nil,function(a)
    God = a
    StopTween(God)
    end)
    
    spawn(function()
        while wait() do 
            if God and World3 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Dragon Crew Archer") or game:GetService("Workspace").Enemies:FindFirstChild("Dragon Crew Werrior") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Dragon Crew Archer" or v.Name == "Dragon Crew Werrior" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetdragon = true
                                        PosMondragon = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not God or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetdragon = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Dragon Crew Archer") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Dragon Crew Archer").HumanoidRootPart.CFrame * CFrame.new(5,16,7))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Dragon Crew Werrior") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Dragon Crew Werrior").HumanoidRootPart.CFrame * CFrame.new(5,16,7))
                            end
                        end
                    end
                Tween(CFrame.new(6704.96435546875, 448.8120422363281, 323.6121520996094))
                end)
            end
        end
    end)
    
    Main:AddToggleLeft("Mystic Droplet",nil,function(a)
    My = a
    StopTween(My)
    end)
    
    spawn(function()
        while wait() do 
            if My and World2 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Water Fighter [Lv. 1450]") or game:GetService("Workspace").Enemies:FindFirstChild("Sea Soldier [Lv. 1425]") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Water Fighter [Lv. 1450]" or v.Name == "Sea Soldier [Lv. 1425]" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetMy = true
                                        PosMonMy = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    until not My or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetMy = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Water Fighter [Lv. 1450]") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Water Fighter [Lv. 1450]").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Sea Soldier [Lv. 1425]") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Sea Soldier [Lv. 1425]").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
                end)
            end
        end
    end)
    
    Main:AddToggleLeft("Fish Tail",nil,function(a)
    Fish = a
    StopTween(Fish)
    end)
    
    spawn(function()
        while wait() do 
            if Fish and World1 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Fishman Warrior") or game:GetService("Workspace").Enemies:FindFirstChild("Fishman Commando") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Fishman Warrior" or v.Name == "Fishman Commando" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetFish = true
                                        PosMonFish = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not Fish or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetFish = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Fishman Warrior") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Fishman Warrior").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Fishman Commando") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Fishman Commando").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
                end)
            end
        end
    end)
    
    spawn(function()
        while wait() do 
            if Fish and World3 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Fishman Raider") or game:GetService("Workspace").Enemies:FindFirstChild("Fishman Captain") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Fishman Raider" or v.Name == "Fishman Captain" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetFish = true
                                        PosMonFish = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    until not Fish or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetFish = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Fishman Raider") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Fishman Raider").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Fishman Captain") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Fishman Captain").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
                  Tween(CFrame.new(-10698.2900390625, 405.37457275390625, -8483.755859375))
               end)
            end
        end
    end)
    
    Main:AddToggleLeft("Conjured Cocoa",nil,function(a)
    Cocoa = a
    StopTween(Cocoa)
    end)
    
   
    spawn(function()
        while wait() do 
            if Cocoa and World3 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Cocoa Warrior") or game:GetService("Workspace").Enemies:FindFirstChild("Chocolate Bar Battler") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Cocoa Warrior" or v.Name == "Chocolate Bar Battler" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetCocoa = true
                                        PosMonCocoa = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    until not Cocoa or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetCocoa = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Cocoa Warrior") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Cocoa Warrior").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Chocolate Bar Battler") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Chocolate Bar Battler").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
                Tween(CFrame.new(394.69036865234375, 79.11857604980469, -12256.5712890625))
                end)
            end
        end
    end)
    
     Main:AddToggleLeft("Magma Ore ",nil,function(a)
    Magma = a
    StopTween(Magma)
    end)
    
    spawn(function()
        while wait() do 
            if Magma and World1 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Military Soldier") or game:GetService("Workspace").Enemies:FindFirstChild("Military Spy") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Military Soldier" or v.Name == "Military Spy" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetMagma = true
                                        PosMonMagma = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not Magma or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetMagma = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Military Soldier") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Military Soldier").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Military Spy") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Military Spy").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
                Tween(CFrame.new(-5514.01318359375, 62.83473587036133, 8577.4072265625))
                end)
            end
        end
    end)
    
     spawn(function()
        while wait() do 
            if Magma and World2 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Magma Ninja") or game:GetService("Workspace").Enemies:FindFirstChild("Lava Pirate") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Magma Ninja" or v.Name == "Lava Pirate" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetMagma = true
                                        PosMonMagma = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not Magma or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetMagma = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Magma Ninja") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Magma Ninja").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Lava Pirate") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Lava Pirate").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
              Tween(CFrame.new(-5229.86083984375, 20.766494750976562, -5297.646484375))
              end)
            end
        end
    end)
    
    Main:AddToggleLeft("Mini Tusk",Mini_Tusk,function(a)
        Mini_Tusk = a
        StopTween(Mini_Tusk)
        end)
        
        spawn(function()
            while wait() do 
                if Mini_Tusk and World3 then
                    pcall(function()
                        if game:GetService("Workspace").Enemies:FindFirstChild("Mythological Pirate") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Mythological Pirate" then
                                    if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                        repeat task.wait()
                                            AutoHaki()
                                            EquipWeapon(SelectWeapon)
                                            v.HumanoidRootPart.CanCollide = false
                                            v.Humanoid.WalkSpeed = 0
                                            v.Head.CanCollide = false 
                                            StartMagnetMini_Tusk = true
                                            PosMonMini_Tusk = v.HumanoidRootPart.CFrame
                                            Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        until not Mini_Tusk or not v.Parent or v.Humanoid.Health <= 0
                                    end
                                end
                            end
                        else
                            StartMagnetMini_Tusk = false
                            for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                                if game:GetService("ReplicatedStorage"):FindFirstChild("Mythological Pirate") then
                                         Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Mythological Pirate").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        end
                                    end
                                end
                                Tween(-13368.1875, 488.188721, -6930.43457, 0.316854268, 7.56199299e-08, 0.948474228, 4.37376357e-08, 1, -9.43392919e-08, -0.948474228, 7.13758297e-08, 0.316854268)
                          end)
                        end
                    end
                end)

    Main:AddToggleLeft("Leather & Scrap Metal",nil,function(a)
    Iron = a
    StopTween(Iron)
    end)
    
    
    spawn(function()
        while wait() do 
            if Iron and World1 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Brute") or game:GetService("Workspace").Enemies:FindFirstChild("Pirate") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Brute" or v.Name == "Pirate" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetIron = true
                                        PosMonIron = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not Iron or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetIron = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Brute") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Brute").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Pirate") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Pirate").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
               Tween(CFrame.new(-1136.0792236328125, 57.42764663696289, 4118.6435546875))
               end)
            end
        end
    end)
    
    Main:AddToggleLeft("Ectoplasm",nil,function(a)
    Ectoplasm = a
    stoptween(Ectoplasm)
    end)
    
    spawn(function()
        while wait() do 
            if Ectoplasm and World2 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Ship Deckhand") or game:GetService("Workspace").Enemies:FindFirstChild("Ship Engineer") or game:GetService("Workspace").Enemies:FindFirstChild("Ship Steward") or game:GetService("Workspace").Enemies:FindFirstChild("Ship Officer") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Ship Deckhand" or v.Name == "Ship Engineer" or v.Name == "Ship Steward" or v.Name == "Ship Officer" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetE = true
                                        PosMonE = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    until not Ectoplasm or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetE = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Ship Deckhand") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Ship Deckhand").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Ship Engineer") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Ship Engineer").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    elseif game:GetService("ReplicatedStorage"):FindFirstChild("Ship Steward") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Ship Steward").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    elseif game:GetService("ReplicatedStorage"):FindFirstChild("Ship Officer") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Ship Officer").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    
                            end
                        end
                    end
                        if Distance > 18000 then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                        end
                        Tween(CFrame.new(911.35827636719, 125.95812988281, 33159.5390625))
               end)
            end
        end
    end)
    
    Main:AddToggleLeft("Yeti Fur ",nil,function(a)
    Yeti = a
    StopTween(Yeti)
    end)
    
    spawn(function()
        while wait() do 
            if Yeti and World1 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Yeti") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Yeti" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetYeti = true
                                        PosMonYeti = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not Yeti or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetYeti = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Yeti") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Yeti").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
                end)
            end
        end
    end)
    
     Main:AddToggleLeft("Redioactive Meterial",nil,function(a)
    AutoRedioactive = a
    StopTween(AutoRedioactive)
    end)
    
    spawn(function()
        while wait() do 
            if AutoRedioactive and World2 then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Factory Staff") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Factory Staff" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetYeti = true
                                        PosMonYeti = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not AutoRedioactive or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetYeti = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Factory Staff") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Factory Staff").HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                            end
                        end
                    end
                end)
            end
        end
    end)
    
    Main:AddToggleLeft("Confetti",AutoConfetti,function(a)
    AutoConfetti = a
    stoptween(AutoConfetti)
    end)
    
    function TP2(Point)
	local Ply = game.Players.LocalPlayer
	local Char = Ply.Character
--	repeat
	Char.Humanoid:ChangeState(15)
	Char.HumanoidRootPart.CFrame = Point
	wait()
	Char.HumanoidRootPart.CFrame = Point
--	until (Char.HumanoidRootPart.Position - Point.Position).Magnitude <= 20
end
function BTP(Pos)
	local Ply = game.Players.LocalPlayer
	local Char = Ply.Character
	Char.HumanoidRootPart.CFrame = Pos
	wait()
	Char.HumanoidRootPart.CFrame = Pos
end

spawn(function()
while task.wait() do
pcall(function()
if AutoConfetti then
for i,v in pairs(game.Workspace.NPCs:GetChildren()) do
	game:GetService("ReplicatedStorage").Remotes.Celebration:InvokeServer('TalkNpc',workspace.NPCs[v.Name])
end
end
end)
end
end)

spawn(function()
while task.wait() do
pcall(function()
	if AutoConfetti then
		if game.PlaceId == 4442272183 then
			TP2(CFrame.new(-11.848626136779785, 19.311767578125, 2828.531005859375))
			TP2(CFrame.new(-375.93408203125, 73.11296844482422, 1180.5146484375))
			TP2(CFrame.new(-378.0177001953125, 73.05511474609375, 287.2165222167969))
			TP2(CFrame.new(-2070.090576171875, 72.37596893310547, -2689.849853515625))
			TP2(CFrame.new(-5365.74462890625, 9.003767013549805, -705.3399658203125))
			TP2(CFrame.new(880.24462890625, 125.09214782714844, 32865.26171875))
			TP2(CFrame.new(-5610.93798828125, 18.35700798034668, -5015.65869140625))
			TP2(CFrame.new(-3014.4755859375, 29.575407028198242, -9777.16015625))
			TP2(CFrame.new(113.77246856689453, 401.45697021484375, -5192.54248046875))
			TP2(CFrame.new(5585.3740234375, 12.449106216430664, -5954.33349609375))
		elseif game.PlaceId == 7449423635 then
			TP2(CFrame.new(-259.380126953125, 6.764979839324951, 5254.09912109375))
			TP2(CFrame.new(-1932.3507080078125, 13.824933052062988, -11636.8515625))
			TP2(CFrame.new(-929.170166015625, 7.802646160125732, -10826.3876953125))
			TP2(CFrame.new(497.3184509277344, 24.76936149597168, -12418.55859375))
			TP2(CFrame.new(-47.42597961425781, 16.97955322265625, -11992.779296875))
			TP2(CFrame.new(2245.78271484375, 12.776296615600586, -6353.974609375))
			TP2(CFrame.new(-9515.0009765625, 142.1398468017578, 5534.05029296875))
			TP2(CFrame.new(-9512.8896484375, 21.139892578125, 4641.02978515625))
			TP2(CFrame.new(4732.6533203125, 51.589698791503906, -1414.252197265625))
			TP2(CFrame.new(5277.3388671875, 602.0785522460938, 363.35223388671875))
			TP2(CFrame.new(3371.987060546875, 38.98302459716797, 1593.1405029296875))
			TP2(CFrame.new(-2045.0103759765625, 38.138248443603516, -10041.935546875))
			TP2(CFrame.new(-5116.79931640625, 314.550537109375, -2964.70068359375))
			TP2(CFrame.new(-4598.1025390625, 16.455780029296875, -2705.09619140625))
			TP2(CFrame.new(-6069.4306640625, 16.455780029296875, -2160.60205078125))
			TP2(CFrame.new(-11385.6767578125, 331.75823974609375, -10405.916015625))
			TP2(CFrame.new(-9603.1591796875, 46.55657196044922, -8365.3828125))
			TP2(CFrame.new(-12545.2353515625, 337.20330810546875, -7454.07470703125))
		else
			TP2(CFrame.new(-2550.043212890625, 6.890709400177002, 2047.015625))
			TP2(CFrame.new(-1248.0438232421875, 2.6870851516723633, 1716.0859375))
			TP2(CFrame.new(-459.51275634765625, 7.687240123748779, 1455.679443359375))
			TP2(CFrame.new(-572.7285766601562, 7.687240123748779, 1797.2501220703125))
			TP2(CFrame.new(781.9508666992188, 5.761781215667725, 1492.8056640625))
			TP2(CFrame.new(949.3020629882812, 16.55164909362793, 1421.4573974609375))
			TP2(CFrame.new(1115.21484375, 7.338680744171143, -1159.033935546875))
			TP2(CFrame.new(3876.05029296875, 5.4081878662109375, -1907.011474609375))
			TP2(CFrame.new(5087.5341796875, 48.43275833129883, 4126.625))
			TP2(CFrame.new(-1135.5067138671875, 4.787090301513672, 3821.385498046875))
			TP2(CFrame.new(881.5269775390625, 3.4771769046783447, 4100.76611328125))
			TP2(CFrame.new(-4830.9208984375, 20.68707275390625, 4373.51953125))
			TP2(CFrame.new(-5206.47998046875, 4.308171272277832, 8430.990234375))
			TP2(CFrame.new(-1324.8131103515625, 11.88819408416748, 500.3249816894531))
			TP2(CFrame.new(-1439.505615234375, 7.32259464263916, -2801.103515625))
			TP2(CFrame.new(-4935.75830078125, 2.8822989463806152, -2325.49462890625))
			TP2(CFrame.new(-4874.67578125, 717.705078125, -2625.676513671875))
			TP2(CFrame.new(-7884.97900390625, 5545.6123046875, -361.72772216796875))
			TP2(CFrame.new(4861.38330078125, 5.687756061553955, 741.5126342773438))
			
			
			
		end
	end
end)
end
end)

 Main:AddSeperatorLeft("Katakuri")
        	 
 local Douhtmon = Main:AddLabelLeft("Wait")

 spawn(function()
    while true do
        pcall(function()
            local cakeStatus = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")
            if string.len(cakeStatus) == 88 then
                Douhtmon:Set("NeedkillMon : " .. string.sub(cakeStatus, 39, 41))
            elseif string.len(cakeStatus) == 87 then
                Douhtmon:Set("NeedkillMon : " .. string.sub(cakeStatus, 39, 40))
            elseif string.len(cakeStatus) == 86 then
                Douhtmon:Set("NeedkillMon : " .. string.sub(cakeStatus, 39, 39))
            else
                Douhtmon:Set("Boss Is Spawn")
            end
        end)
        wait(1)
    end
end)



    Main:AddToggleLeft("Auto Katakuri",AutoDoughtBoss,function(value)
        AutoDoughtBoss = value
        StopTween(AutoDoughtBoss)
    end)
    spawn(function()
        while wait() do
            if AutoDoughtBoss then
                pcall(function()
                    local workspace = game:GetService("Workspace")
                    local replicatedStorage = game:GetService("ReplicatedStorage")
    
                    -- ตรวจสอบว่ามี Cake Prince หรือไม่
                    local cakePrince = workspace.Enemies:FindFirstChild("Cake Prince")
                    if cakePrince then
                        for _, enemy in pairs(workspace.Enemies:GetChildren()) do
                            if enemy.Name == "Cake Prince" and enemy:FindFirstChild("Humanoid") and enemy:FindFirstChild("HumanoidRootPart") and enemy.Humanoid.Health > 0 then
                                repeat
                                    task.wait()
                                    AutoHaki()
                                    EquipWeapon(SelectWeapon)
                                    enemy.HumanoidRootPart.CanCollide = false
                                    enemy.Humanoid.WalkSpeed = 0
                                    Tween(enemy.HumanoidRootPart.CFrame * CFrame.new(0, -35, 0))
                                until not AutoDoughtBoss or not enemy.Parent or enemy.Humanoid.Health <= 0
                            end
                        end
                    else
                        -- ตรวจสอบว่ามี Cake Prince ใน ReplicatedStorage หรือไม่
                        local cakePrinceStorage = replicatedStorage:FindFirstChild("Cake Prince")
                        if cakePrinceStorage then
                            Tween(cakePrinceStorage.HumanoidRootPart.CFrame * CFrame.new(0, -45, -40))
                        else
                            -- หากเงื่อนไขตรง เปิด BigMirror และหา Cookie Crafter หรืออื่น ๆ
                            local bigMirror = workspace.Map.CakeLoaf.BigMirror.Other
                            if bigMirror.Transparency == 1 then
                                local foundEnemy = false
                                for _, enemy in pairs(workspace.Enemies:GetChildren()) do
                                    if enemy.Name == "Cookie Crafter" or enemy.Name == "Cake Guard" or enemy.Name == "Baking Staff" or enemy.Name == "Head Baker" then
                                        if enemy:FindFirstChild("Humanoid") and enemy:FindFirstChild("HumanoidRootPart") and enemy.Humanoid.Health > 0 then
                                            foundEnemy = true
                                            repeat
                                                task.wait()
                                                AutoHaki()
                                                EquipWeapon(SelectWeapon)
                                                enemy.HumanoidRootPart.CanCollide = false
                                                enemy.Humanoid.WalkSpeed = 0
                                                enemy.Head.CanCollide = false
                                                MagnetDought = true
                                                PosMonDoughtOpenDoor = enemy.HumanoidRootPart.CFrame
                                                Tween(enemy.HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
                                            until not AutoDoughtBoss or not enemy.Parent or enemy.Humanoid.Health <= 0 or bigMirror.Transparency == 0 or replicatedStorage:FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") or workspace.Enemies:FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]")
                                        end
                                    end
                                end
    
                                -- หากไม่มีมอนที่ตรงเงื่อนไข
                                if not foundEnemy then
                                    Tween(CFrame.new(-2079.6826, 227.9526, -12321.9238))
                                end
                            else
                                MagnetDought = false
                                if bigMirror.Transparency == 0 then
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2151.82153, 149.315704, -12404.9053)
                                end
                            end
                        end
                    end
                end)
            end
        end
    end)

Main:AddSeperatorLeft("Hallow Scythe")
Main:AddToggleLeft("Auto Hallow Scythe",AutoFarmBossHallow,function(value)
        AutoFarmBossHallow = value
        StopTween(AutoFarmBossHallow)
    end)
    
    Main:AddToggleLeft("Auto Hallow Scythe + Hop",AutoFarmBossHallowHop,function(value)
        AutoFarmBossHallowHop = value
    end)
    
    spawn(function()
        while wait() do
            if AutoFarmBossHallow then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if string.find(v.Name , "Soul Reaper") then
                                repeat task.wait()
                                    EquipWeapon(SelectWeapon)
                                    AutoHaki()
                                   
                                    Tween(v.HumanoidRootPart.CFrame*CFrame.new(5,10,7))
                                    game:GetService("VirtualUser"):CaptureController()
                                    game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670))
                                    v.HumanoidRootPart.Transparency = 1
                                    sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
                                until v.Humanoid.Health <= 0 or AutoFarmBossHallow == false
                            end
                        end
                    elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hallow Essence") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Hallow Essence") then
                        repeat Tween(CFrame.new(-8932.322265625, 146.83154296875, 6062.55078125)) wait() until (CFrame.new(-8932.322265625, 146.83154296875, 6062.55078125).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 8                        
                        EquipWeapon("Hallow Essence")
                    else
                        if game:GetService("ReplicatedStorage"):FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
                            Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]").HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                        else
                            if AutoFarmBossHallowHop then
                                Hop()
                            end
                        end
                    end
                end)
            end
        end
    end)
    Main:AddSeperatorLeft('Law Bos')
    Main:AddToggleLeft("Auto Law Boss",AutoLawBoss,function(a)
        AutoLawBoss = a
        StopTween()
    end)
    
    Main:AddToggleLeft("Auto Buy Chip",AutoBuyLawChip,function(a)
        AutoBuyLawChip = a
        end)
        
    
    spawn(function()
    while wait() do
        if AutoLawBoss then
            pcall(function()
                if not game:GetService("Workspace").Enemies:FindFirstChild("Order [Lv. 1250] [Raid Boss]") and not game:GetService("ReplicatedStorage"):FindFirstChild("Order [Lv. 1250] [Raid Boss]") then
                    if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Microchip") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Microchip") then
                        fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon.Button.Main.ClickDetector)
                    else
                        if AutoBuyLawChip then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Microchip","1")
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Microchip","2")
                        end
                    end
                else
                    if game:GetService("ReplicatedStorage"):FindFirstChild("Order [Lv. 1250] [Raid Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Order [Lv. 1250] [Raid Boss]") then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Order [Lv. 1250] [Raid Boss]") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Order [Lv. 1250] [Raid Boss]" then
                                    repeat task.wait()
                                        EquipWeapon(SelectWeapon)
                                        AutoHaki()
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,35,0))
                                        v.HumanoidRootPart.CanCollide = false
                                        game:GetService'VirtualUser':CaptureController()
                                        game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                        sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                    until v.Humanoid.Health <= 0 or not AutoLawBoss or not v.Parent
                                end
                            end
                        else 
                            if game:GetService("ReplicatedStorage"):FindFirstChild("Order [Lv. 1250] [Raid Boss]") then
                                Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Order [Lv. 1250] [Raid Boss]").HumanoidRootPart.CFrame * CFrame.new(0,35,0))
                            end
                        end
                    end
                end
            end)
        end
    end
end)

    Main:AddSeperatorLeft("Shank Sew")
    
    Main:AddToggleLeft("Auto Shach sew",AutoFarmSwanGlasses,function(value)
        AutoSaw = value
        StopTween(AutoSaw)
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if AutoSaw then
                    if game:GetService("Workspace").Enemies:FindFirstChild("The Saw [Lv. 100] [Boss]") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "The Saw [Lv. 100] [Boss]" and v.Humanoid.Health > 0 and v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
                                repeat task.wait()
                                    pcall(function()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                       
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,15,7))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670))
                                        sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                    end)
                                until AutoSaw == false or v.Humanoid.Health <= 0
                            end
                        end
                    end
                end
            end
        end)
    end)
    
    Main:AddToggleLeft("Auto Saw + Hop",AutoSaw_Hop,function(value)
        AutoSaw_Hop = value
    end)
    
     spawn(function()
        pcall(function()
            while wait() do
                if (AutoSaw_Hop and AutoSaw) and World1 and not game:GetService("ReplicatedStorage"):FindFirstChild("The Saw [Lv. 100] [Boss]") and not game:GetService("Workspace").Enemies:FindFirstChild("The Saw [Lv. 100] [Boss]") then
                    Hop()
                end
            end
        end)
    end)
    
    Main:AddSeperatorLeft("Dark Dagger")
    
    Main:AddToggleLeft("Auto Dark Dagger",AutoDarkDagger,function(value)
        AutoDarkDagger = value
        StopTween(AutoDarkDagger)
    end)
        
    spawn(function()
        pcall(function()
            while wait() do
                if AutoDarkDagger then
                    if game:GetService("Workspace").Enemies:FindFirstChild("rip_indra True Form") or game:GetService("Workspace").Enemies:FindFirstChild("rip_indra]") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == ("rip_indra True Form" or v.Name == "rip_indra") and v.Humanoid.Health > 0 and v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
                                repeat task.wait()
                                    pcall(function()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.HumanoidRootPart.Size = Vector3.new(1,1,1)
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
                                    end)
                                until AutoDarkDagger == false or v.Humanoid.Health <= 0
                            end
                        end
                    else
                        Tween(CFrame.new(-5344.822265625, 423.98541259766, -2725.0930175781))
                    end
                end
            end
        end)
    end)
    
    Main:AddToggleLeft("Auto Dark Dagger + Hop",AutoDarkDagger_Hop,function(value)
        AutoDarkDagger_Hop = value
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if (AutoDarkDagger_Hop and AutoDarkDagger) and World3 and not game:GetService("ReplicatedStorage"):FindFirstChild("rip_indra True Form") and not game:GetService("Workspace").Enemies:FindFirstChild("rip_indra True Form") then
                    Hop()
                end
            end
        end)
    end)





    Main:AddSeperatorLeft("Unlock Raid")
    
    Main:AddToggleLeft("Unlock Raid Phoenix",AutoAdvanceDungeon,function(value)
        AutoAdvanceDungeon = value
        StopTween(AutoAdvanceDungeon)
    end)
    
    spawn(function()
        while wait() do
            if AutoAdvanceDungeon then
                pcall(function()
                    if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Bird-Bird: Phoenix") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Bird-Bird: Phoenix") then
                        if game.Players.LocalPlayer.Backpack:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value) then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value).Level.Value >= 400 then
                                Tween(CFrame.new(-2812.76708984375, 254.803466796875, -12595.560546875))
                                if (CFrame.new(-2812.76708984375, 254.803466796875, -12595.560546875).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10 then
                                    wait(1.5)
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SickScientist","Check")
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SickScientist","Heal")
                                end
                            end
                        elseif game.Players.LocalPlayer.Character:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value) then
                            if game.Players.LocalPlayer.Character:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value).Level.Value >= 400 then
                                Tween(CFrame.new(-2812.76708984375, 254.803466796875, -12595.560546875))
                                if (CFrame.new(-2812.76708984375, 254.803466796875, -12595.560546875).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10 then
                                    wait(1.5)
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SickScientist","Check")
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SickScientist","Heal")
                                end
                            end
                        end
                    end
                end)
            end
        end
    end)
    
    Main:AddSeperatorLeft("Budy Sword")
    
    Main:AddToggleLeft("Auto Budy Sword",AutoBudySword,function(value)
        AutoBudySword = value
        StopTween(AutoBudySword)
    end)
    
    Main:AddToggleLeft("Auto Budy Sword Hop",AutoBudySwordHop,function(value)
        AutoBudySwordHop = value
    end)
    
    spawn(function()
        while wait() do
            if AutoBudySword then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Cake Queen") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Cake Queen" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                       
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,40,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                        sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
                                    until not AutoBudySword or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        if game:GetService("ReplicatedStorage"):FindFirstChild("Cake Queen") then
                            Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Cake Queen").HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                        else
                            if AutoBudySwordHop then
                                Hop()
                            end
                        end
                    end
                end)
            end
        end
    end)
    
    Main:AddSeperatorLeft("Elite")
    
    local Elite_Hunter_Status = Main:AddLabelLeft("")
    
             function ssr()
                if game:GetService("ReplicatedStorage"):FindFirstChild("Diablo") or game:GetService("ReplicatedStorage"):FindFirstChild("Deandre") or game:GetService("ReplicatedStorage"):FindFirstChild("Urban") or game:GetService("Workspace").Enemies:FindFirstChild("Diablo") or game:GetService("Workspace").Enemies:FindFirstChild("Deandre") or game:GetService("Workspace").Enemies:FindFirstChild("Urban") then
                    Elite_Hunter_Status:Set("Elite is : Spawn")  
                else
                    Elite_Hunter_Status:Set("Elite is : Not Spawn")    
                end
                end
        

         spawn(function()
        while task.wait() do
            pcall(function()
                ssr()
            end)
        end
    end)
    
    local EliteProgress = Main:AddLabelLeft("")
    
    spawn(function()
        pcall(function()
            while wait() do
                EliteProgress:Set("Elite Check : "..game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter","Progress"))
            end
        end)
    end)
    
    
    
    
    Main:AddToggleLeft("Auto Elite",combo,function(a)
    combo = a
    StopTween(combo)
    end)
    
     spawn(function()
        while wait() do 
            if combo and World3 then
                pcall(function()
                     game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter")
                      if game:GetService("Workspace").Enemies:FindFirstChild("Urban") or game:GetService("Workspace").Enemies:FindFirstChild("Deandre") or game:GetService("Workspace").Enemies:FindFirstChild("Diablo") then
                       for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Urban" or v.Name == "Diablo" or v.Name == "Deandre" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                   repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.Head.CanCollide = false 
                                        StartMagnetcombo = true
                                        PosMoncombo = v.HumanoidRootPart.CFrame
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,16,7))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                    until not combo or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        StartMagnetcombo = false
                        for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do 
                           if game:GetService("ReplicatedStorage"):FindFirstChild("Urban") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Urban").HumanoidRootPart.CFrame * CFrame.new(5,16,7))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Diablo") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Diablo").HumanoidRootPart.CFrame * CFrame.new(5,16,7))
                                elseif game:GetService("ReplicatedStorage"):FindFirstChild("Deandre") then
                                    Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Deandre").HumanoidRootPart.CFrame * CFrame.new(5,16,7))
                            end
                        end
                    end
                end)
            end
        end
    end)
                
                
    
    Main:AddToggleLeft("Auto Elite Hop",AutoEliteHunterHop,function(value)
        AutoEliteHunterHop = value
    end)

spawn(function()
        pcall(function()
            while wait() do
                if (AutoEliteHunterHop and combo) and World3 and not game:GetService("ReplicatedStorage"):FindFirstChild("Diablo") and not game:GetService("ReplicatedStorage"):FindFirstChild("Deandre") and not game:GetService("ReplicatedStorage"):FindFirstChild("Urban") and not game:GetService("Workspace").Enemies:FindFirstChild("Diablo") and not game:GetService("Workspace").Enemies:FindFirstChild("Deandre") and not game:GetService("Workspace").Enemies:FindFirstChild("Urban") and not game.Players.LocalPlayer.Backpack:FindFirstChild("God's Chalice") and not game.Players.LocalPlayer.Character:FindFirstChild("God's Chalice") then
                    Hop()
                end
            end
        end)
    end)

Main:AddSeperatorLeft("Cursed Dual Katana")
Main:AddToggleLeft("Auto Cursed Dual Katana", Auto_Cursed_Dual_Katana,function(value)
         Auto_Cursed_Dual_Katana = value
        StopTween( Auto_Cursed_Dual_Katana)
    end)
    spawn(function()
    while wait() do
        pcall(function()
            if Auto_Cursed_Dual_Katana then
                if GetWeaponInventory("Cursed Dual Katana") == true then
                    if game.Players.LocalPlayer.Character:FindFirstChild("Cursed Dual Katana") or game.Players.LocalPlayer.Backpack:FindFirstChild("Cursed Dual Katana") then
    
                    else
                       
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("LoadItem","Cursed Dual Katana")
                    end
                else
                    if game.Players.LocalPlayer.Character:FindFirstChild("Tushita") or game.Players.LocalPlayer.Backpack:FindFirstChild("Tushita") or game.Players.LocalPlayer.Character:FindFirstChild("Yama") or game.Players.LocalPlayer.Backpack:FindFirstChild("Yama") then
                        if game.Players.LocalPlayer.Character:FindFirstChild("Tushita") or game.Players.LocalPlayer.Backpack:FindFirstChild("Tushita") then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Tushita") then
                             
                                                EquipWeapon("Tushita")
                            else
                                for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
                                    if v.Name == "Tushita" and v:IsA("Tool") then
                                        if v.Level.Value >= 350 then
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("LoadItem","Tushita")
                                            AutoFarmBone = false
                                        else
                                            Select_Weapon = "Tushita"
                                            AutoFarmBone = true
                                        end
                                    end
                                end
                            end
                        elseif game.Players.LocalPlayer.Character:FindFirstChild("Yama") or game.Players.LocalPlayer.Backpack:FindFirstChild("Yama") then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Yama") then
                                EquipWeapon("Yama")
                            else
                                for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
                                    if v.Name == "Yama" and v:IsA("Tool") then
                                        if v.Level.Value >= 350 then
                                            Auto_CDK_Quest = true
                                            AutoFarmBone = false
                                        else
                                            Select_Weapon = "Yama"
                                            AutoFarmBone = true
                                        end
                                    end
                                end
                            end
                        end
                    else
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("LoadItem","Tushita")
                    end      
                end
            end
        end)
    end
    end)
    
    spawn(function()
    while wait() do
        pcall(function()
            if Auto_CDK_Quest then
                if GetMaterial("Alucard Fragment") == 0 then
                    Auto_Quest_Yama_1 = true
                    Auto_Quest_Yama_2 = false
                    Auto_Quest_Yama_3 = false
                    Auto_Quest_Tushita_1 = false
                    Auto_Quest_Tushita_2 = false
                    Auto_Quest_Tushita_3 = false
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Evil")
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil")
                elseif GetMaterial("Alucard Fragment") == 1 then
                    Auto_Quest_Yama_1 = false
                    Auto_Quest_Yama_2 = true
                    Auto_Quest_Yama_3 = false
                    Auto_Quest_Tushita_1 = false
                    Auto_Quest_Tushita_2 = false
                    Auto_Quest_Tushita_3 = false
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Evil")
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil")
                elseif GetMaterial("Alucard Fragment") == 2 then
                    Auto_Quest_Yama_1 = false
                    Auto_Quest_Yama_2 = false
                    Auto_Quest_Yama_3 = true
                    Auto_Quest_Tushita_1 = false
                    Auto_Quest_Tushita_2 = false
                    Auto_Quest_Tushita_3 = false
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Evil")
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil")
                elseif GetMaterial("Alucard Fragment") == 3 then
                    Auto_Quest_Yama_1 = false
                    Auto_Quest_Yama_2 = false
                    Auto_Quest_Yama_3 = false
                    Auto_Quest_Tushita_1 = true
                    Auto_Quest_Tushita_2 = false
                    Auto_Quest_Tushita_3 = false

                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Good")
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good")
                elseif GetMaterial("Alucard Fragment") == 4 then
                    Auto_Quest_Yama_1 = false
                    Auto_Quest_Yama_2 = false
                    Auto_Quest_Yama_3 = false
                    Auto_Quest_Tushita_1 = false
                    Auto_Quest_Tushita_2 = true
                    Auto_Quest_Tushita_3 = false
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Good")
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good")
                elseif GetMaterial("Alucard Fragment") == 5 then
                    Auto_Quest_Yama_1 = false
                    Auto_Quest_Yama_2 = false
                    Auto_Quest_Yama_3 = false
                    Auto_Quest_Tushita_1 = false
                    Auto_Quest_Tushita_2 = false
                    Auto_Quest_Tushita_3 = true
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Good")
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good")
                elseif GetMaterial("Alucard Fragment") == 6 then
                    if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton Boss") or game:GetService("Workspace").ReplicatedStorage:FindFirstChild("Cursed Skeleton Boss") then
                        Auto_Quest_Yama_1 = false
                        Auto_Quest_Yama_2 = false
                        Auto_Quest_Yama_3 = false
                        Auto_Quest_Tushita_1 = false
                        Auto_Quest_Tushita_2 = false
                        Auto_Quest_Tushita_3 = false
                        if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton Boss") or game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Cursed Skeleton Boss" or v.Name == "Cursed Skeleton" then
                                    if v.Humanoid.Health > 0 then
AutoHaki()
                                                EquipWeapon(SelectWeapon)                                        
v.HumanoidRootPart.CanCollide = false
                                        v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
                                        toTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,40,0))
                                        game:GetService'VirtualUser':CaptureController()
                                        game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                    end
                                end
                            end
                        end
                    else
                        if (CFrame.new(-12361.7060546875, 603.3547973632812, -6550.5341796875).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 100 then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Good")
                            wait(1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Evil")
                            wait(1)
                            toTarget(CFrame.new(-12361.7060546875, 603.3547973632812, -6550.5341796875))
                            wait(1.5)
                            game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                            wait(1.5)
                            toTarget(CFrame.new(-12253.5419921875, 598.8999633789062, -6546.8388671875))
                        else
                            toTarget(CFrame.new(-12361.7060546875, 603.3547973632812, -6550.5341796875))
                        end   
                    end
                end
            end
        end)
    end
    end)
    
    spawn(function()
    while wait() do
        if Auto_Quest_Yama_1 then
            pcall(function()
                if game:GetService("Workspace").Enemies:FindFirstChild("Mythological Pirate") then
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == "Mythological Pirate" then
                            repeat wait()
                                toTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-2))
                            until not Auto_CDK_Quest or not Auto_Cursed_Dual_Katana 
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil")
                        end
                    end
                else
                    toTarget(CFrame.new(-13451.46484375, 543.712890625, -6961.0029296875))
                end
            end)
        end
    end
    end)
    
    spawn(function()
    while wait() do
        pcall(function()
            if Auto_Quest_Yama_2 then
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v:FindFirstChild("HazeESP") then
                        v.HazeESP.Size = UDim2.new(50,50,50,50)
                        v.HazeESP.MaxDistance = "inf"
                    end
                end
                for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
                    if v:FindFirstChild("HazeESP") then
                        v.HazeESP.Size = UDim2.new(50,50,50,50)
                        v.HazeESP.MaxDistance = "inf"
                    end
                end
            end
        end)
    end
    end)
    
    spawn(function()
    while wait() do
        pcall(function()
            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                if Auto_Quest_Yama_2 and v:FindFirstChild("HazeESP") and (v.HumanoidRootPart.Position - PosMonsEsp.Position).magnitude <= 300 then
                    v.HumanoidRootPart.CFrame = PosMonsEsp
                    v.HumanoidRootPart.CanCollide = false
                   
                    if not v.HumanoidRootPart:FindFirstChild("BodyVelocity") then
                        local vc = Instance.new("BodyVelocity", v.HumanoidRootPart)
                        vc.MaxForce = Vector3.new(1, 1, 1) * math.huge
                        vc.Velocity = Vector3.new(0, 0, 0)
                    end
                end
            end
        end)
    end
    end)
    
    spawn(function()
    while wait() do
        if Auto_Quest_Yama_2 then 
            pcall(function() 
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v:FindFirstChild("HazeESP") then
                        repeat wait()
                            if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
                                toTarget(v.HumanoidRootPart.CFrameMon* CFrame.new(0,20,0))
                            else
                                StartMagnet = true
                                AutoHaki()
                                                EquipWeapon(SelectWeapon)
        
                                    game:GetService'VirtualUser':CaptureController()
                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                
                                
                                v.Humanoid.JumpPower = 0
                                v.Humanoid.WalkSpeed = 0
                                v.HumanoidRootPart.CanCollide = false
                                v.Humanoid:ChangeState(11)
                                toTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,20,0))								
                            end      
                        until Auto_Cursed_Dual_Katana == false or Auto_Quest_Yama_2 == false or not v.Parent or v.Humanoid.Health <= 0 or not v:FindFirstChild("HazeESP")
                    else
                        for x,y in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
                            if y:FindFirstChild("HazeESP") then
                                if (y.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
                                    toTarget(y.HumanoidRootPart.CFrame * CFrame.new(0,20,0))
                                end
                            end
                        end
                    end
                end
            end)
        end
    end
    end)
    
    spawn(function()
    while wait() do
        if Auto_Quest_Yama_3 then
            pcall(function()
                if game.Players.LocalPlayer.Backpack:FindFirstChild("Hallow Essence") then         
                    AutoFarmBone = false           
                    toTarget(game:GetService("Workspace").Map["Haunted Castle"].Summoner.Detection.CFrame)
                elseif game:GetService("Workspace").Map:FindFirstChild("HellDimension") then
                    repeat wait()
                        if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton") or game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton") or game:GetService("Workspace").Enemies:FindFirstChild("Hell's Messenger") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Cursed Skeleton" or v.Name == "Cursed Skeleton" or v.Name == "Hell's Messenger" then
                                    if v.Humanoid.Health > 0 then
                                        repeat wait()
                                            StartMagnet = true
                                            AutoHaki()
                                                EquipWeapon(SelectWeapon)
    
                                            PosMonsEsp = v.HumanoidRootPart.CFrame
                                            
                                                game:GetService'VirtualUser':CaptureController()
                                                game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                           
                                            
                                            v.Humanoid.JumpPower = 0
                                            v.Humanoid.WalkSpeed = 0
                                            v.HumanoidRootPart.CanCollide = false
                                            v.Humanoid:ChangeState(11)
                                            toTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,50,0))
                                        until v.Humanoid.Health <= 0 or not v.Parent or Auto_Quest_Yama_3 == false
                                    end
                                end
                            end
                        else
                            wait(5)
                            toTarget(game:GetService("Workspace").Map.HellDimension.Torch1.CFrame)
                            wait(1.5)
                            game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                            wait(1.5)        
                            toTarget(game:GetService("Workspace").Map.HellDimension.Torch2.CFrame)
                            wait(1.5)
                            game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                            wait(1.5)     
                            toTarget(game:GetService("Workspace").Map.HellDimension.Torch3.CFrame)
                            wait(1.5)
                            game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                            wait(1.5)     
                            toTarget(game:GetService("Workspace").Map.HellDimension.Exit.CFrame)
                        end
                    until Auto_Cursed_Dual_Katana == false or Auto_Quest_Yama_3 == false or GetMaterial("Alucard Fragment") == 3
                else
                    if game:GetService("Workspace").Enemies:FindFirstChild("Soul Reaper") or game.ReplicatedStorage:FindFirstChild("Soul Reaper") then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Soul Reaper") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Soul Reaper" then
                                    if v.Humanoid.Health > 0 then
                                        repeat wait()
                                            toTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-2))
                                        until Auto_Cursed_Dual_Katana == false or Auto_Quest_Yama_3 == false or game:GetService("Workspace").Map:FindFirstChild("HellDimension")
                                    end
                                end
                            end
                        else
                            toTarget(CFrame.new(-9570.033203125, 315.9346923828125, 6726.89306640625))
                        end
                    else
                        AutoFarmBone = true
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Buy",1,1)
                    end
                end
            end)
        end
    end
    end)
    
    spawn(function() 
    while wait() do
        if Auto_Quest_Tushita_1 then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","BoatQuest",workspace.NPCs:FindFirstChild("Luxury Boat Dealer"))
        end
    end
    end)
    
spawn(function()
 while wait() do
  pcall(function()
   if Auto_Quest_Tushita_1 then
     repeat wait() toTarget(CFrame.new(-9546.990234375, 21.139892578125, 4686.1142578125)) until (CFrame.new(-9546.990234375, 21.139892578125, 4686.1142578125).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 5 
wait(1)
repeat wait() toTarget(CFrame.new(-6120.0576171875, 16.455780029296875, -2250.697265625)) until (CFrame.new(-6120.0576171875, 16.455780029296875, -2250.697265625).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 5 
wait(1)
repeat wait() toTarget(CFrame.new(-9533.2392578125, 7.254445552825928, -8372.69921875)) until (CFrame.new(-9533.2392578125, 7.254445552825928, -8372.69921875).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 5 

end
end)
end
end)

    spawn(function()
    while wait() do
        if Auto_Quest_Tushita_2 then
            pcall(function()
                if (CFrame.new(-5539.3115234375, 313.800537109375, -2972.372314453125).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 500 then
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if Auto_Quest_Tushita_2 and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                            if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 2000 then
                                repeat wait()
AutoHaki()
                                                EquipWeapon(SelectWeapon)
                                    v.HumanoidRootPart.CanCollide = false
                                    toTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,50,0))
                                    game:GetService'VirtualUser':CaptureController()
                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                until v.Humanoid.Health <= 0 or not v.Parent or Auto_Quest_Tushita_2 == false
                            end
                        end
                    end
                else
                    toTarget(CFrame.new(-5545.1240234375, 313.800537109375, -2976.616455078125))
                end
            end)
        end
    end
    end)
    
    spawn(function()
    while wait() do
        if Auto_Quest_Tushita_3 then
            pcall(function()
                if game:GetService("Workspace").Enemies:FindFirstChild("Cake Queen") or game.ReplicatedStorage:FindFirstChild("Cake Queen") then
                    if game:GetService("Workspace").Enemies:FindFirstChild("Cake Queen") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Cake Queen" then
                                if v.Humanoid.Health > 0 then
                                    repeat wait()
                                      
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                       
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,40,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                        sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
                                      
                                    until Auto_Cursed_Dual_Katana == false or Auto_Quest_Tushita_3 == false or game:GetService("Workspace").Map:FindFirstChild("HeavenlyDimension")
                                end
                            end
                        end
                    else
                        toTarget(CFrame.new(-709.3132934570312, 381.6005859375, -11011.396484375))
                    end
                elseif game:GetService("Workspace").Map:FindFirstChild("HeavenlyDimension") then
                    repeat wait()
                        if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton") or game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton") or game:GetService("Workspace").Enemies:FindFirstChild("Heaven's Guardian") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Cursed Skeleton" or v.Name == "Cursed Skeleton" or v.Name == "Heaven's Guardian" then
                                    if v.Humanoid.Health > 0 then
                                        repeat wait()
                                          AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                       
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,40,0))
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                     
                                        until v.Humanoid.Health <= 0 or not v.Parent or Auto_Quest_Tushita_3 == false
                                    end
                                end
                            end
                        else
                            wait(5)
                            toTarget(game:GetService("Workspace").Map.HeavenlyDimension.Torch1.CFrame)
                            wait(1.5)
                            game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                            wait(1.5)        
                            toTarget(game:GetService("Workspace").Map.HeavenlyDimension.Torch2.CFrame)
                            wait(1.5)
                            game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                            wait(1.5)     
                            toTarget(game:GetService("Workspace").Map.HeavenlyDimension.Torch3.CFrame)
                            wait(1.5)
                            game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                            wait(1.5)     
                            toTarget(game:GetService("Workspace").Map.HeavenlyDimension.Exit.CFrame)
                        end
                    until Auto_Cursed_Dual_Katana == false or Auto_Quest_Tushita_3 == false or GetMaterial("Alucard Fragment") == 6
                end
            end)
        end
    end
    end)

Main:AddSeperatorLeft("Observation")
    
    local ObservationRange = Main:AddLabelLeft("")
    
    spawn(function()
		while game:GetService("RunService").Heartbeat:wait() do
			local OPP = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk","Status")
			local Lpp = string.match(tostring(OPP), "%d+")
			ObservationRange:Set("Ken Haki Level : "..tostring(Lpp))
		end
	end)
    
    Main:AddToggleLeft("Auto Farm Observation",AutoObservation,function(value)
        AutoObservation = value
        StopTween(AutoObservation)
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if AutoObservation then
                    repeat task.wait()
                        if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
                            game:GetService('VirtualUser'):CaptureController()
                            game:GetService('VirtualUser'):SetKeyDown('0x65')
                            wait(2)
                            game:GetService('VirtualUser'):SetKeyUp('0x65')
                        end
                    until game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") or not AutoObservation
                end
            end)
        end
    end)
    
    Main:AddToggleLeft("Auto Farm Observation + Hop",AutoObservation_Hop,function(value)
        AutoObservation_Hop = value
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if AutoObservation then
                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk","Status") == 5000 then
                        game:GetService("StarterGui"):SetCore("SendNotification", {
                            Icon = "rbxassetid://0";
                            Title = "Observation", 
                            Text = "You Have Max Points"
                        })
                        wait(2)
                    else
                        if World2 then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Lava Pirate") then
                                if game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Lava Pirate").HumanoidRootPart.CFrame * CFrame.new(3,0,0)
                                    until AutoObservation == false or not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                else
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Lava Pirate").HumanoidRootPart.CFrame * CFrame.new(0,50,0)
                                            wait(1)
                                        if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") and AutoObservation_Hop == true then
                                            game:GetService("TeleportService"):Teleport(game.PlaceId,game:GetService("Players").LocalPlayer)
                                        end
                                    until AutoObservation == false or game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                end
                            else
                                Tween(CFrame.new(-5478.39209, 15.9775667, -5246.9126))
                            end
                        elseif World1 then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Galley Captain") then
                                if game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Galley Captain").HumanoidRootPart.CFrame * CFrame.new(3,0,0)
                                    until AutoObservation == false or not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                else
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Galley Captain").HumanoidRootPart.CFrame * CFrame.new(0,50,0)
                                        wait(1)
                                        if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") and AutoObservation_Hop == true then
                                            game:GetService("TeleportService"):Teleport(game.PlaceId,game:GetService("Players").LocalPlayer)
                                        end
                                    until AutoObservation == false or game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                end
                            else
                                Tween(CFrame.new(5533.29785, 88.1079102, 4852.3916))
                            end
                        elseif World3 then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Giant Islander") then
                                if game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Giant Islander").HumanoidRootPart.CFrame * CFrame.new(3,0,0)
                                    until AutoObservation == false or not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                else
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Giant Islander").HumanoidRootPart.CFrame * CFrame.new(0,50,0)
                                        wait(1)
                                        if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") and AutoObservation_Hop == true then
                                            game:GetService("TeleportService"):Teleport(game.PlaceId,game:GetService("Players").LocalPlayer)
                                        end
                                    until AutoObservation == false or game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                end
                            else
                                Tween(CFrame.new(4530.3540039063, 656.75695800781, -131.60952758789))
                            end
                        end
                    end
                end
            end
        end)
    end)
    
    Main:AddSeperatorLeft("Saber")
    
    Main:AddToggleLeft("Auto Saber",AutoSaber,function(value)
        AutoSaber = value
        StopTween(AutoSaber)
    end)
    
    Main:AddToggleLeft("Auto Saber + Hop",AutoSaber_Hop,function(value)
        AutoSaber_Hop = value
    end)
    
    spawn(function()
        while wait() do
            if AutoSaber then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Saber Expert") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Saber Expert" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    PosMonSaber = v.HumanoidRootPart.CFrame
                                    repeat task.wait()
                                        AutoHaki()
                                        EquipWeapon(SelectWeapon)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.HumanoidRootPart.CFrame = PosMonSaber
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                       
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                        sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
                                    until not AutoSaber or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        if game:GetService("ReplicatedStorage"):FindFirstChild("Saber Expert") then
                            Tween(game:GetService("ReplicatedStorage"):FindFirstChild("Saber Expert").HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                        else
                            if AutoSaber_Hop then
                                Hop()
                            end
                        end
                    end
                end)
            end
        end
    end)
    
    Main:AddSeperatorLeft("Legendary Sword")
    
    Main:AddToggleLeft("Auto Legendary Sword",AutoBuyLegendarySword,function(value)
        AutoBuyLegendarySword = value
    end)
    
    spawn(function()
        while wait() do
            if AutoBuyLegendarySword then
                pcall(function()
                    local args = {
                        [1] = "LegendarySwordDealer",
                        [2] = "1"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    local args = {
                        [1] = "LegendarySwordDealer",
                        [2] = "2"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    local args = {
                        [1] = "LegendarySwordDealer",
                        [2] = "3"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    if AutoBuyLegendarySword_Hop and AutoBuyLegendarySword and World2 then
                        wait(10)
                        Hop()
                    end
                end)
            end 
        end
    end)
    
    Main:AddToggleLeft("Auto Legendary Sword + Hop",AutoBuyLegendarySword_Hop,function(value)
        AutoBuyLegendarySword_Hop = value
    end)
    
    Main:AddSeperatorLeft("Enchancement Colour")
    
    Main:AddToggleLeft("Auto Enchancement Colour",AutoBuyEnchancementColour,function(value)
        AutoBuyEnchancementColour = value
    end)
    
    Main:AddToggleLeft("Auto Enchancement + Hop",AutoBuyEnchancementColour_Hop,function(value)
        AutoBuyEnchancementColour_Hop = value
    end)
    
    spawn(function()
        while wait() do
            if AutoBuyEnchancementColour then
                local args = {
                    [1] = "ColorsDealer",
                    [2] = "2"
                }
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                if AutoBuyEnchancementColour_Hop and AutoBuyEnchancementColour and not World1 then
                    wait(10)
                    Hop()
                end
            end 
        end
    end)
    
    Main:AddSeperatorLeft("Other")
    
    Main:AddToggleLeft("Auto Musketeer Hat",AutoMusketeerHat,function(value)
        AutoMusketeerHat = value
        StopTween(AutoMusketeerHat)
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if AutoMusketeerHat then
                    if game:GetService("Players").LocalPlayer.Data.Level.Value >= 1800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress").KilledBandits == false then
                        if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Forest Pirate") and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "50") and game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Forest Pirate") then
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if v.Name == "Forest Pirate" then
                                        repeat task.wait()
                                            pcall(function()
                                                EquipWeapon(SelectWeapon)
                                                AutoHaki()
                                               
                                                Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                                v.HumanoidRootPart.CanCollide = false
                                                game:GetService'VirtualUser':CaptureController()
                                                game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                                MusketeerHatMon = v.HumanoidRootPart.CFrame
                                                StartMagnetMusketeerhat = true
                                            end)
                                        until AutoMusketeerHat == false or not v.Parent or v.Humanoid.Health <= 0 or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                        StartMagnetMusketeerhat = false
                                    end
                                end
                            else
                                StartMagnetMusketeerhat = false
                                Tween(CFrame.new(-13206.452148438, 425.89199829102, -7964.5537109375))
                            end
                        else
                            Tween(CFrame.new(-12443.8671875, 332.40396118164, -7675.4892578125))
                            if (Vector3.new(-12443.8671875, 332.40396118164, -7675.4892578125) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 30 then
                                wait(1.5)
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest","CitizenQuest",1)
                            end
                        end
                    elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 1800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress").KilledBoss == false then
                        if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Captain Elephant") and game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Captain Elephant") then
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if v.Name == "Captain Elephant" then
                                        OldCFrameElephant = v.HumanoidRootPart.CFrame
                                        repeat task.wait()
                                            pcall(function()
                                                EquipWeapon(SelectWeapon)
                                                AutoHaki()
                                                v.HumanoidRootPart.CanCollide = false
                                               
                                                Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                                v.HumanoidRootPart.CanCollide = false
                                                v.HumanoidRootPart.CFrame = OldCFrameElephant
                                                
                                                sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                            end)
                                        until AutoMusketeerHat == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                    end
                                end
                            else
                                Tween(CFrame.new(-13374.889648438, 421.27752685547, -8225.208984375))
                            end
                        else
                            Tween(CFrame.new(-12443.8671875, 332.40396118164, -7675.4892578125))
                            if (CFrame.new(-12443.8671875, 332.40396118164, -7675.4892578125).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
                                wait(1.5)
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress","Citizen")
                            end
                        end
                    elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 1800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress","Citizen") == 2 then
                        Tween(CFrame.new(-12512.138671875, 340.39279174805, -9872.8203125))
                    end
                end
            end
        end)
    end)
    
    Main:AddToggleLeft("Auto Rainbow Haki",Auto_Rainbow_Haki,function(value)
        Auto_Rainbow_Haki = value
        StopTween(Auto_Rainbow_Haki)
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if Auto_Rainbow_Haki then
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                        Tween(CFrame.new(-11892.0703125, 930.57672119141, -8760.1591796875))
                        if (Vector3.new(-11892.0703125, 930.57672119141, -8760.1591796875) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 30 then
                            wait(1.5)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("HornedMan","Bet")
                        end
                    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Stone") then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Stone") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Stone" then
                                    OldCFrameRainbow = v.HumanoidRootPart.CFrame
                                    repeat task.wait()
                                        EquipWeapon(SelectWeapon)
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                        v.HumanoidRootPart.CanCollide = false
                                        v.HumanoidRootPart.CFrame = OldCFrameRainbow
                                       
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 672))
                                        sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                    until Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                end
                            end
                        else
                            Tween(CFrame.new(-1086.11621, 38.8425903, 6768.71436, 0.0231462717, -0.592676699, 0.805107772, 2.03251839e-05, 0.805323839, 0.592835128, -0.999732077, -0.0137055516, 0.0186523199))
                        end
                    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Island Empress") then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Island Empress") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Island Empress" then
                                    OldCFrameRainbow = v.HumanoidRootPart.CFrame
                                    repeat task.wait()
                                        EquipWeapon(SelectWeapon)
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                        v.HumanoidRootPart.CanCollide = false
                                        v.HumanoidRootPart.CFrame = OldCFrameRainbow
                                       
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 672))
                                        sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                    until Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                end
                            end
                        else
                            Tween(CFrame.new(5713.98877, 601.922974, 202.751251, -0.101080291, -0, -0.994878292, -0, 1, -0, 0.994878292, 0, -0.101080291))
                        end
                    elseif string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Kilo Admiral") then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Kilo Admiral [Lv. 1750] [Boss]") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Kilo Admiral [Lv. 1750] [Boss]" then
                                    OldCFrameRainbow = v.HumanoidRootPart.CFrame
                                    repeat task.wait()
                                        EquipWeapon(SelectWeapon)
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                        v.HumanoidRootPart.CanCollide = false
                                       
                                        v.HumanoidRootPart.CFrame = OldCFrameRainbow
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 672))
                                        sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                    until Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                end
                            end
                        else
                            Tween(CFrame.new(2877.61743, 423.558685, -7207.31006, -0.989591599, -0, -0.143904909, -0, 1.00000012, -0, 0.143904924, 0, -0.989591479))
                        end
                    elseif string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Captain Elephant") then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Captain Elephant") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Captain Elephant" then
                                    OldCFrameRainbow = v.HumanoidRootPart.CFrame
                                    repeat task.wait()
                                        EquipWeapon(SelectWeapon)
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                        v.HumanoidRootPart.CanCollide = false
                                       
                                        v.HumanoidRootPart.CFrame = OldCFrameRainbow
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 672))
                                        sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                    until Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                end
                            end
                        else
                            Tween(CFrame.new(-13485.0283, 331.709259, -8012.4873, 0.714521289, 7.98849911e-08, 0.69961375, -1.02065748e-07, 1, -9.94383065e-09, -0.69961375, -6.43015241e-08, 0.714521289))
                        end
                    elseif string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Beautiful Pirate") then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Beautiful Pirate") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Beautiful Pirate" then
                                    OldCFrameRainbow = v.HumanoidRootPart.CFrame
                                    repeat task.wait()
                                        EquipWeapon(SelectWeapon)
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                        v.HumanoidRootPart.CanCollide = false
                                       
                                        v.HumanoidRootPart.CFrame = OldCFrameRainbow
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 672))
                                        sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                    until Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                end
                            end
                        else
                            Tween(CFrame.new(5312.3598632813, 20.141201019287, -10.158538818359))
                        end
                    else
                        Tween(CFrame.new(-11892.0703125, 930.57672119141, -8760.1591796875))
                        if (Vector3.new(-11892.0703125, 930.57672119141, -8760.1591796875) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 30 then
                            wait(1.5)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("HornedMan","Bet")
                        end
                    end
                end
            end
        end)
    end)
    
    Main:AddToggleLeft("Auto Observation Haki v2",AutoObservationv2,function(value)
        AutoObservationv2 = value
        StopTween(AutoObservationv2)
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if AutoObservationv2 then
                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress","Citizen") == 3 then
                        AutoMusketeerHat = false
                        if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Banana") and  game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Apple") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Pineapple") then
                            repeat 
                                Tween(CFrame.new(-12444.78515625, 332.40396118164, -7673.1806640625)) 
                                wait() 
                            until not AutoObservationv2 or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-12444.78515625, 332.40396118164, -7673.1806640625)).Magnitude <= 10
                            wait(.5)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress","Citizen")
                        elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fruit Bowl") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fruit Bowl") then
                            repeat 
                                Tween(CFrame.new(-10920.125, 624.20275878906, -10266.995117188)) 
                                wait() 
                            until not AutoObservationv2 or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-10920.125, 624.20275878906, -10266.995117188)).Magnitude <= 10
                            wait(.5)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk2","Start")
                            wait(1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk2","Buy")
                        else
                            for i,v in pairs(game:GetService("Workspace"):GetDescendants()) do
                                if v.Name == "Apple" or v.Name == "Banana" or v.Name == "Pineapple" then
                                    v.Handle.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,1,10)
                                    wait()
                                    firetouchinterest(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart,v.Handle,0)    
                                    wait()
                                end
                            end   
                        end
                    else
                        AutoMusketeerHat = true
                    end
                end
            end)
        end
    end)
    
    Main:AddToggleLeft("Auto Rengoku",AutoRengoku,function(value)
        AutoRengoku = value
        StopTween(AutoRengoku)
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if AutoRengoku then
                    if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hidden Key") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Hidden Key") then
                        EquipWeapon("Hidden Key")
                        Tween(CFrame.new(6571.1201171875, 299.23028564453, -6967.841796875))
                    elseif game:GetService("Workspace").Enemies:FindFirstChild("Snow Lurker") or game:GetService("Workspace").Enemies:FindFirstChild("Arctic Warrior") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if (v.Name == "Snow Lurker" or v.Name == "Arctic Warrior") and v.Humanoid.Health > 0 then
                                repeat task.wait()
                                    EquipWeapon(SelectWeapon)
                                    AutoHaki()
                                    v.HumanoidRootPart.CanCollide = false
                                  
                                    RengokuMon = v.HumanoidRootPart.CFrame
                                    Tween(v.HumanoidRootPart.CFrame * CFrame.new(0,40,0))
                                    game:GetService'VirtualUser':CaptureController()
                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                    StartRengokuMagnet = true
                                until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hidden Key") or AutoRengoku == false or not v.Parent or v.Humanoid.Health <= 0
                                StartRengokuMagnet = false
                            end
                        end
                    else
                        StartRengokuMagnet = false
                        Tween(CFrame.new(5439.716796875, 84.420944213867, -6715.1635742188))
                    end
                end
            end
        end)
    end)
    
   
    Main:AddToggleLeft("Auto Yama",AutoYama,function(value)
        AutoYama = value
        StopTween(AutoYama)
    end)
    
    spawn(function()
        while wait() do
            if AutoYama then
                if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter","Progress") >= 30 then
                    repeat wait(.1)
                        fireclickdetector(game:GetService("Workspace").Map.Waterfall.SealedKatana.Handle.ClickDetector)
                    until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Yama") or not AutoYama
                end
            end
        end
    end)
    
    Main:AddToggleLeft("Auto Evo Race",Auto_EvoRace,function(value)
        Auto_EvoRace = value
        StopTween(Auto_EvoRace)
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if Auto_EvoRace then
                    if not game:GetService("Players").LocalPlayer.Data.Race:FindFirstChild("Evolved") then
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1") == 0 then
                            Tween(CFrame.new(-2779.83521, 72.9661407, -3574.02002, -0.730484903, 6.39014104e-08, -0.68292886, 3.59963224e-08, 1, 5.50667032e-08, 0.68292886, 1.56424669e-08, -0.730484903))
                            if (Vector3.new(-2779.83521, 72.9661407, -3574.02002) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
                                wait(1.3)
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","2")
                            end
                        elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1") == 1 then
                            pcall(function()
                                if not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 1") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 1") then
                                    Tween(game:GetService("Workspace").Flower1.CFrame)
                                elseif not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 2") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 2") then
                                    Tween(game:GetService("Workspace").Flower2.CFrame)
                                elseif not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 3") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 3") then
                                    if game:GetService("Workspace").Enemies:FindFirstChild("Zombie") then
                                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                            if v.Name == "Zombie" then
                                                repeat task.wait()
                                                    AutoHaki()
                                                    EquipWeapon(SelectWeapon)
                                                    Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                                    v.HumanoidRootPart.CanCollide = false
                                                   
                                                    game:GetService("VirtualUser"):CaptureController()
                                                    game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 672))
                                                    PosMonEvo = v.HumanoidRootPart.CFrame
                                                    StartEvoMagnet = true
                                                until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 3") or not v.Parent or v.Humanoid.Health <= 0 or Auto_EvoRace == false
                                                StartEvoMagnet = false
                                            end
                                        end
                                    else
                                        StartEvoMagnet = false
                                        Tween(CFrame.new(-5685.9233398438, 48.480125427246, -853.23724365234))
                                    end
                                end
                            end)
                        elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1") == 2 then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","3")
                        end
                    end
                end
            end
        end)
    end)
    
    Main:AddToggleLeft("Auto Bartlio Quest",AutoBartilo,function(value)
        AutoBartilo = value
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if AutoBartilo then
                    if game:GetService("Players").LocalPlayer.Data.Level.Value >= 800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 0 then
                        if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Swan Pirates") and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "50") and game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then 
                            if game:GetService("Workspace").Enemies:FindFirstChild("Swan Pirate") then
                                Ms = "Swan Pirate"
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if v.Name == Ms then
                                        pcall(function()
                                            repeat task.wait()
                                                sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                                EquipWeapon(SelectWeapon)
                                                AutoHaki()
                                                v.HumanoidRootPart.Transparency = 1
                                                v.HumanoidRootPart.CanCollide = false
                                               
                                                Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))													
                                                PosMonBarto =  v.HumanoidRootPart.CFrame
                                                game:GetService'VirtualUser':CaptureController()
                                                game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                                AutoBartiloBring = true
                                            until not v.Parent or v.Humanoid.Health <= 0 or AutoBartilo == false or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                            AutoBartiloBring = false
                                        end)
                                    end
                                end
                            else
                                repeat Tween(CFrame.new(932.624451, 156.106079, 1180.27466, -0.973085582, 4.55137119e-08, -0.230443969, 2.67024713e-08, 1, 8.47491108e-08, 0.230443969, 7.63147128e-08, -0.973085582)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(932.624451, 156.106079, 1180.27466, -0.973085582, 4.55137119e-08, -0.230443969, 2.67024713e-08, 1, 8.47491108e-08, 0.230443969, 7.63147128e-08, -0.973085582)).Magnitude <= 10
                            end
                        else
                            repeat Tween(CFrame.new(-456.28952, 73.0200958, 299.895966)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-456.28952, 73.0200958, 299.895966)).Magnitude <= 10
                            wait(1.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest","BartiloQuest",1)
                        end 
                    elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 1 then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Jeremy") then
                            Ms = "Jeremy"
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == Ms then
                                    OldCFrameBartlio = v.HumanoidRootPart.CFrame
                                    repeat task.wait()
                                        sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                        EquipWeapon(SelectWeapon)
                                        AutoHaki()
                                        v.HumanoidRootPart.Transparency = 1
                                        v.HumanoidRootPart.CanCollide = false
                                       
                                        v.HumanoidRootPart.CFrame = OldCFrameBartlio
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                                        game:GetService'VirtualUser':CaptureController()
                                        game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                        sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
                                    until not v.Parent or v.Humanoid.Health <= 0 or AutoBartilo == false
                                end
                            end
                        elseif game:GetService("ReplicatedStorage"):FindFirstChild("Jeremy") then
                            repeat Tween(CFrame.new(-456.28952, 73.0200958, 299.895966)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-456.28952, 73.0200958, 299.895966)).Magnitude <= 10
                            wait(1.1)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo")
                            wait(1)
                            repeat Tween(CFrame.new(2099.88159, 448.931, 648.997375)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(2099.88159, 448.931, 648.997375)).Magnitude <= 10
                            wait(2)
                        else
                            repeat Tween(CFrame.new(2099.88159, 448.931, 648.997375)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(2099.88159, 448.931, 648.997375)).Magnitude <= 10
                        end
                    elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 2 then
                        repeat Tween(CFrame.new(-1850.49329, 13.1789551, 1750.89685)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1850.49329, 13.1789551, 1750.89685)).Magnitude <= 10
                        wait(1)
                        repeat Tween(CFrame.new(-1858.87305, 19.3777466, 1712.01807)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1858.87305, 19.3777466, 1712.01807)).Magnitude <= 10
                        wait(1)
                        repeat Tween(CFrame.new(-1803.94324, 16.5789185, 1750.89685)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1803.94324, 16.5789185, 1750.89685)).Magnitude <= 10
                        wait(1)
                        repeat Tween(CFrame.new(-1858.55835, 16.8604317, 1724.79541)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1858.55835, 16.8604317, 1724.79541)).Magnitude <= 10
                        wait(1)
                        repeat Tween(CFrame.new(-1869.54224, 15.987854, 1681.00659)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1869.54224, 15.987854, 1681.00659)).Magnitude <= 10
                        wait(1)
                        repeat Tween(CFrame.new(-1800.0979, 16.4978027, 1684.52368)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1800.0979, 16.4978027, 1684.52368)).Magnitude <= 10
                        wait(1)
                        repeat Tween(CFrame.new(-1819.26343, 14.795166, 1717.90625)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1819.26343, 14.795166, 1717.90625)).Magnitude <= 10
                        wait(1)
                        repeat Tween(CFrame.new(-1813.51843, 14.8604736, 1724.79541)) wait() until not AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1813.51843, 14.8604736, 1724.79541)).Magnitude <= 10
                    end
                end 
            end
        end)
    end)
    
    Main:AddToggleLeft("จุดไฟ",AutoHolyTorch,function(value)
        AutoHolyTorch = value
        StopTween(AutoHolyTorch)
    end)
    
    spawn(function()
        while wait() do
            if AutoHolyTorch then
                pcall(function()
                    wait(1)
                    TP(CFrame.new(-10752, 417, -9366))
                    wait(1)
                    TP(CFrame.new(-11672, 334, -9474))
                    wait(1)
                    TP(CFrame.new(-12132, 521, -10655))
                    wait(1)
                    TP(CFrame.new(-13336, 486, -6985))
                    wait(1)
                    TP(CFrame.new(-13489, 332, -7925))
                end)
            end
        end
    end)

Teleport:AddSeperatorLeft("Teleport World")
    
    Teleport:AddButtonLeft("World 1",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelMain")
    end)
    
    Teleport:AddButtonLeft("World 2",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
    end)
    
    Teleport:AddButtonLeft("World 3",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
    end)

    Teleport:AddSeperatorLeft("Island")
    
    if World1 then
        Teleport:AddDropdownLeft("Select Island",{
            "WindMill",
            "Marine",
            "Middle Town",
            "Jungle",
            "Pirate Village",
            "Desert",
            "Snow Island",
            "MarineFord",
            "Colosseum",
            "Sky Island 1",
            "Sky Island 2",
            "Sky Island 3",
            "Prison",
            "Magma Village",
            "Under Water Island",
            "Fountain City",
            "Shank Room",
            "Mob Island"
            },function(value)
            SelectIsland = value
        end)
    end
    
    if World2 then
        Teleport:AddDropdownLeft("Select Island",{
            "The Cafe",
            "Frist Spot",
            "Dark Area",
            "Flamingo Mansion",
            "Flamingo Room",
            "Green Zone",
            "Factory",
            "Colossuim",
            "Zombie Island",
            "Two Snow Mountain",
            "Punk Hazard",
            "Cursed Ship",
            "Ice Castle",
            "Forgotten Island",
            "Ussop Island",
            "Mini Sky Island"
            },function(value)
            SelectIsland = value
        end)
    end
    
    if World3 then
        Teleport:AddDropdownLeft("Select Island",{
            "Mansion",
            "Port Town",
            "Great Tree",
            "Castle On The Sea",
            "MiniSky", 
            "Hydra Island",
            "Floating Turtle",
            "Haunted Castle",
            "Ice Cream Island",
            "Peanut Island",
            "Cake Island",
            "Cocoa Island",
            "North Pole"
            },function(value)
            SelectIsland = value
        end)
    end
    
    Teleport:AddToggleLeft("Teleport",false,function(value)
        TeleportIsland = value
        if TeleportIsland == true then
            repeat wait()
                if SelectIsland == "WindMill" then
                    Tween(CFrame.new(979.79895019531, 16.516613006592, 1429.0466308594))
                elseif SelectIsland == "Marine" then
                    Tween(CFrame.new(-2566.4296875, 6.8556680679321, 2045.2561035156))
                elseif SelectIsland == "Middle Town" then
                    Tween(CFrame.new(-690.33081054688, 15.09425163269, 1582.2380371094))
                elseif SelectIsland == "Jungle" then
                    Tween(CFrame.new(-1612.7957763672, 36.852081298828, 149.12843322754))
                elseif SelectIsland == "Pirate Village" then
                    Tween(CFrame.new(-1181.3093261719, 4.7514905929565, 3803.5456542969))
                elseif SelectIsland == "Desert" then
                    Tween(CFrame.new(944.15789794922, 20.919729232788, 4373.3002929688))
                elseif SelectIsland == "Snow Island" then
                    Tween(CFrame.new(1347.8067626953, 104.66806030273, -1319.7370605469))
                elseif SelectIsland == "MarineFord" then
                    Tween(CFrame.new(-4914.8212890625, 50.963626861572, 4281.0278320313))
                elseif SelectIsland == "Colosseum" then
                    Tween( CFrame.new(-1427.6203613281, 7.2881078720093, -2792.7722167969))
                elseif SelectIsland == "Sky Island 1" then
                    Tween(CFrame.new(-4869.1025390625, 733.46051025391, -2667.0180664063))
                elseif SelectIsland == "Sky Island 2" then  
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
                elseif SelectIsland == "Sky Island 3" then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
                elseif SelectIsland == "Prison" then
                    Tween( CFrame.new(4875.330078125, 5.6519818305969, 734.85021972656))
                elseif SelectIsland == "Magma Village" then
                    Tween(CFrame.new(-5247.7163085938, 12.883934020996, 8504.96875))
                elseif SelectIsland == "Under Water Island" then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                elseif SelectIsland == "Fountain City" then
                    Tween(CFrame.new(5127.1284179688, 59.501365661621, 4105.4458007813))
                elseif SelectIsland == "Shank Room" then
                    Tween(CFrame.new(-1442.16553, 29.8788261, -28.3547478))
                elseif SelectIsland == "Mob Island" then
                    Tween(CFrame.new(-2850.20068, 7.39224768, 5354.99268))
                elseif SelectIsland == "The Cafe" then
                    Tween(CFrame.new(-380.47927856445, 77.220390319824, 255.82550048828))
                elseif SelectIsland == "Frist Spot" then
                    Tween(CFrame.new(-11.311455726624, 29.276733398438, 2771.5224609375))
                elseif SelectIsland == "Dark Area" then
                    Tween(CFrame.new(3780.0302734375, 22.652164459229, -3498.5859375))
                elseif SelectIsland == "Flamingo Mansion" then
                    Tween(CFrame.new(-483.73370361328, 332.0383605957, 595.32708740234))
                elseif SelectIsland == "Flamingo Room" then
                    Tween(CFrame.new(2284.4140625, 15.152037620544, 875.72534179688))
                elseif SelectIsland == "Green Zone" then
                    Tween( CFrame.new(-2448.5300292969, 73.016105651855, -3210.6306152344))
                elseif SelectIsland == "Factory" then
                    Tween(CFrame.new(424.12698364258, 211.16171264648, -427.54049682617))
                elseif SelectIsland == "Colossuim" then
                    Tween( CFrame.new(-1503.6224365234, 219.7956237793, 1369.3101806641))
                elseif SelectIsland == "Zombie Island" then
                    Tween(CFrame.new(-5622.033203125, 492.19604492188, -781.78552246094))
                elseif SelectIsland == "Two Snow Mountain" then
                    Tween(CFrame.new(753.14288330078, 408.23559570313, -5274.6147460938))
                elseif SelectIsland == "Punk Hazard" then
                    Tween(CFrame.new(-6127.654296875, 15.951762199402, -5040.2861328125))
                elseif SelectIsland == "Cursed Ship" then
                    Tween(CFrame.new(923.40197753906, 125.05712890625, 32885.875))
                elseif SelectIsland == "Ice Castle" then
                    Tween(CFrame.new(6148.4116210938, 294.38687133789, -6741.1166992188))
                elseif SelectIsland == "Forgotten Island" then
                    Tween(CFrame.new(-3032.7641601563, 317.89672851563, -10075.373046875))
                elseif SelectIsland == "Ussop Island" then
                    Tween(CFrame.new(4816.8618164063, 8.4599885940552, 2863.8195800781))
                elseif SelectIsland == "Mini Sky Island" then
                    Tween(CFrame.new(-288.74060058594, 49326.31640625, -35248.59375))
                elseif SelectIsland == "Great Tree" then
                    Tween(CFrame.new(2681.2736816406, 1682.8092041016, -7190.9853515625))
                elseif SelectIsland == "Castle On The Sea" then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-5143.55371, 314.587158, -3129.7771, -0.327329725, 8.04210885e-08, 0.944910169, -2.44393075e-08, 1, -9.35758777e-08, -0.944910169, -5.37231166e-08, -0.327329725))                elseif SelectIsland == "MiniSky" then
                    Tween(CFrame.new(-260.65557861328, 49325.8046875, -35253.5703125))
                elseif SelectIsland == "Port Town" then
                    Tween(CFrame.new(-290.7376708984375, 6.729952812194824, 5343.5537109375))
                elseif SelectIsland == "Hydra Island" then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(5677.88525, 1013.11609, -309.271179, -0.800623715, -2.0267505e-08, -0.599167526, -4.52882283e-08, 1, 2.66892357e-08, 0.599167526, 4.85032672e-08, -0.800623715))                elseif SelectIsland == "Floating Turtle" then
                elseif SelectIsland == "Mansion" then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12550.1133, 337.185822, -7509.18311, 0.999812901, 3.70209925e-08, -0.019343419, -3.77426304e-08, 1, -3.69415432e-08, 0.019343419, 3.76647051e-08, 0.999812901))
                elseif SelectIsland == "Haunted Castle" then
                    Tween(CFrame.new(-9515.3720703125, 164.00624084473, 5786.0610351562))
                elseif SelectIsland == "Ice Cream Island" then
                    Tween(CFrame.new(-902.56817626953, 79.93204498291, -10988.84765625))
                elseif SelectIsland == "Peanut Island" then
                    Tween(CFrame.new(-2062.7475585938, 50.473892211914, -10232.568359375))
                elseif SelectIsland == "Cake Island" then
                    Tween(CFrame.new(-1884.7747802734375, 19.327526092529297, -11666.8974609375))
                elseif SelectIsland == "Cocoa Island" then
                    Tween(CFrame.new(380.12860107421875, 126.59191131591797, -12725.7119140625))
                elseif SelectIsland == "North Pole" then
                    Tween(CFrame.new(-1095.06934, 64.7162552, -14520.2695, 0.951785564, 1.55784488e-08, 0.306764215, -5.39329559e-09, 1, -3.40495667e-08, -0.306764215, 3.07534158e-08, 0.951785564))
                end
            until not TeleportIsland
        end
        StopTween(TeleportIsland)
    end)
    
    Teleport:AddLineRight()
    
    local TimeRaid = Teleport:AddLabelRight("Wait For Dungeon")
    
    spawn(function()
        pcall(function()
            while wait() do
                if game:GetService("Players").LocalPlayer.PlayerGui.Main.TopHUDList.RaidTimer.Visible == true then
                    TimeRaid:Set(game:GetService("Players").LocalPlayer.PlayerGui.Main.TopHUDList.RaidTimer.Text)
                else
                    TimeRaid:Set("Wait.")
                    Wait(.2)
                    TimeRaid:Set("Wait..")
                    wait(.2)
                    TimeRaid:Set("Wait...")
                    wait(.2)
                end
            end
        end)
    end)
    
    Teleport:AddToggleRight("Auto Dungeon",Auto_Dungeon,function(value)
        Auto_Dungeon = value
        StopTween(Auto_Dungeon)
    end)
    
     Teleport:AddToggleRight("Kill Aura",KillAura,function(value)
       KillAura = value
    end)
    
    spawn(function()
        while wait() do
            if KillAura then
                for _, enemy in pairs(game:GetService("Workspace").Enemies:GetDescendants()) do
                    if enemy:FindFirstChild("Humanoid") and enemy:FindFirstChild("HumanoidRootPart") and enemy.Humanoid.Health > 0 then
                        pcall(function()
                            while KillAura and enemy.Parent and enemy.Humanoid.Health > 0 do
                                wait()
                                -- ตั้งค่าคุณสมบัติ SimulationRadius (ถ้าจำเป็น)
                                if sethiddenproperty then
                                    pcall(function()
                                        sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                    end)
                                end
                                -- ลดค่าชีวิตของศัตรู
                                enemy.Humanoid.Health = 0
                            end
                        end)
                    end
                end
            end
        end
    end)
    
    
    spawn(function()
        while wait(0) do
            if Auto_Dungeon then
                local raidTimer = game:GetService("Players").LocalPlayer.PlayerGui.Main.TopHUDList.RaidTimer
                if raidTimer.Visible == true then
                    for _, enemy in pairs(game:GetService("Workspace").Enemies:GetDescendants()) do
                        if enemy:FindFirstChild("Humanoid") and enemy:FindFirstChild("HumanoidRootPart") and enemy.Humanoid.Health > 0 then
                            pcall(function()
                                while Auto_Dungeon and enemy.Parent and enemy.Humanoid.Health > 0 do
                                    if sethiddenproperty then
                                        pcall(function()
                                            sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                                        end)
                                    end
                                    enemy.Humanoid.Health = 0
                                    enemy.HumanoidRootPart.CanCollide = false
                                end
                            end)
                        end
                    end
                end
            end
        end
    end)
    
    
    spawn(function()
        pcall(function()
            while wait() do
                if Auto_Dungeon then
                    local raidisland = workspace._WorldOrigin.Locations
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.TopHUDList.RaidTimer.Visible == true then
                        if raidisland:FindFirstChild("Island 5") then
                            Tween(raidisland:FindFirstChild("Island 5").CFrame * CFrame.new(0,70,100))
                        elseif raidisland:FindFirstChild("Island 4") then
                            Tween(raidisland:FindFirstChild("Island 4").CFrame * CFrame.new(0,70,100))
                        elseif raidisland:FindFirstChild("Island 3") then
                            Tween(raidisland:FindFirstChild("Island 3").CFrame * CFrame.new(0,70,100))
                        elseif raidisland:FindFirstChild("Island 2") then
                            Tween(raidisland:FindFirstChild("Island 2").CFrame * CFrame.new(0,70,100))
                        elseif raidisland:FindFirstChild("Island 1") then
                            Tween(raidisland:FindFirstChild("Island 1").CFrame * CFrame.new(0,70,100))
                        end
                    end
                end
            end
        end)
    end)



    spawn(function()
        while wait(.1) do
            pcall(function()
                if Auto_Dungeon then
                    local raidisland = workspace._WorldOrigin.Locations
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.TopHUDList.RaidTimer.Visible == false then
                        if not raidisland:FindFirstChild("Island 1") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Special Microchip") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Special Microchip") then
                            if World2 then
                                fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon2.Button.Main.ClickDetector)
                            elseif World3 then
                                fireclickdetector(game:GetService("Workspace").Map["Boat Castle"].RaidSummon2.Button.Main.ClickDetector)
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    Teleport:AddToggleRight("Auto Awakener",Auto_Awakener,function(value)
        Auto_Awakener = value
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if Auto_Awakener then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Awakener","Check")
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Awakener","Awaken")
                end
            end
        end)
    end)
    
    Teleport:AddLineRight()
    SelectChip = "Flame"

    Teleport:AddDropdownRight("Select Chips",
        {"Flame",
            "Ice",
            "Quake",
            "Light",
            "Dark",
            "String",
            "Rumble",
            "Magma",
            "Human: Buddha",
            "Sand",
            "Bird: Phoenix",
            "Dough-Dough"
             },function(value)
            
        SelectChip = value
    end)
    
    Teleport:AddToggleRight("Auto Select Chip",AutoSelectDungeon,function(value)
        AutoSelectDungeon = value
    end)
    
    spawn(function()
        while wait() do
            if AutoSelectDungeon then
                pcall(function()
                    if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flame-Flame") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flame-Flame") then
                        SelectChip = "Flame"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Ice-Ice") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Ice-Ice") then
                        SelectChip = "Ice"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Quake-Quake") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Quake-Quake") then
                        SelectChip = "Quake"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Light-Light") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Light-Light") then
                        SelectChip = "Light"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dark-Dark") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dark-Dark") then
                        SelectChip = "Dark"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("String-String") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("String-String") then
                        SelectChip = "String"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Rumble-Rumble") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Rumble-Rumble") then
                        SelectChip = "Rumble"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Magma-Magma") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Magma-Magma") then
                        SelectChip = "Magma"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Human-Human: Buddha") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Human-Human: Buddha Fruit") then
                        SelectChip = "Human: Buddha"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Sand-Sand") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Sand-Sand") then
                        SelectChip = "Sand"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Bird-Bird: Phoenix") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Bird-Bird: Phoenix") then
                        SelectChip = "Bird: Phoenix"
                    elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dough-Dough") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dough-Dough") then
                        SelectChip = "Dough-Dough"
                    else
                        SelectChip = "Flame"
                    end
                end)
            end
        end
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if Auto_Dungeon then
                    local raidisland = workspace._WorldOrigin.Locations
                    if not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Special Microchip") or not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Special Microchip") then
                        if not raidisland:FindFirstChild("Island 1") then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("RaidsNpc", "Select", SelectChip)
                        end
                    end
                end
            end
        end)
    end)

    Teleport:AddToggleRight("Auto Buy Chip",AutoBuyChip,function(value)
        AutoBuyChip = value
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if AutoBuyChip then
                    local raidisland = workspace._WorldOrigin.Locations
                    if not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Special Microchip") or not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Special Microchip") then
                        if not raidisland:FindFirstChild("Island 1") then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("RaidsNpc", "Select", SelectChip)
                        end
                    end
                end
            end
        end)
    end)
    
    Teleport:AddButtonRight("Buy Chip",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("RaidsNpc","Select",SelectChip)
    end)
    
    Teleport:AddToggleRight("Auto Start Raid",Auto_StartRaid,function(value)
        Auto_StartRaid = value
    end)
    
    spawn(function()
        while wait(.1) do
            pcall(function()
                if Auto_StartRaid then
                    local raidisland = workspace._WorldOrigin.Locations
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.TopHUDList.RaidTimer.Visible == false then
                        if not raidisland:FindFirstChild("Island 1") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Special Microchip") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Special Microchip") then
                            if World2 then
                                fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon2.Button.Main.ClickDetector)
                            elseif World3 then
                                fireclickdetector(game:GetService("Workspace").Map["Boat Castle"].RaidSummon2.Button.Main.ClickDetector)
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    Teleport:AddButtonRight("Start Raid",function()
        if World2 then
            fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon2.Button.Main.ClickDetector)
        elseif World3 then
            fireclickdetector(game:GetService("Workspace").Map["Boat Castle"].RaidSummon2.Button.Main.ClickDetector)
        end
    end)
   
   
        Teleport:AddButtonRight("Tp To Lab",function()
            if World2 then
TP(CFrame.new(-6438.73535, 250.645355, -4501.50684))
        end
if World3 then
            TP(CFrame.new(-5017.40869, 314.844055, -2823.0127, -0.925743818, 4.48217499e-08, -0.378151238, 4.55503146e-09, 1, 1.07377559e-07, 0.378151238, 9.7681621e-08, -0.925743818))
end
    
end)
   
   

    
        Teleport:AddButtonRight("Tp To Awaken Room",function()
           if World2 then
           TP(CFrame.new(266.227783, 1.39509034, 1857.00732))
end
if World3 then
            TP(CFrame.new(-11571.440429688, 49.172668457031, -7574.7368164062))
end
        end)

    Teleport:AddButtonRight("TP To Next Island",function()
        pcall(function()
            if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") then
                TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame*CFrame.new(0,70,100))
            elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") then
                TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame*CFrame.new(0,70,100))
            elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") then
                TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame*CFrame.new(0,70,100))
            elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") then
                TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame*CFrame.new(0,70,100))
            elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
                TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame*CFrame.new(0,70,100))
            end
        end)
    end)
    
    
    
     
    
    Teleport:AddLineLeft("")
    
   Teleport:AddSeperatorLeft("Fruit Spawn")
   
   

    
    
    Teleport:AddToggleLeft("View Fruit Spawn",false,function(value)
        rryio = value
        local tr = game:GetService("Players").LocalPlayer.Character.Humanoid
        local tr = game:GetService("Workspace")["Fruit "].Fruit
        repeat wait(.1)
            game:GetService("Workspace").Camera.CameraSubject = game:GetService("Workspace")["Fruit "].Fruit
        until rryio == false 
        game:GetService("Workspace").Camera.CameraSubject = game:GetService("Players").LocalPlayer.Character.Humanoid
    end)
    
    Teleport:AddToggleLeft("TP To Fruit Spawn",nil,function(a)
fts = a
StopTween(fts)
end)

spawn(function()
            while wait() do
                if fts then
                    pcall(function()
                            Tween(CFrame.new(workspace["Fruit "].Handle.Position))
                            end)
                            end
                            end
                            end)


    
    Teleport:AddSeperatorLeft("Sniper")
    
    FruitList = {
        "Rocket-Rocket",
        "Spin-Spin",
        "Blade-Blade",
        "Spring-Spring",
        "Bomb-Bomb",
        "Smoke-Smoke",
        "Spike-Spike",
        "Flame-Flame",
        "Falcon-Bird: Falcon",
        "Ice-Ice",
        "Sand-Sand",
        "Dark-Dark",
        "Diamond-Diamond",
        "Light-Light",
        "Rubber-Rubber",
        "Barrier-Barrier",
        "Ghost-Ghost",
        "Magma-Magma",
        "Quake-Quake",
        "Human-Human: Buddha",
        "Love-Love",
        "Spider-Spider",
        "Sound-Sound",
        "Bird-Bird: Phoenix",
        "Portal-Portal",
        "Rumble-Rumble",
        "Pain-Pain",
        "Blizzard-Blizzard",
        "Gravity-Gravity",
        "Mammoth-Mammoth",
        "T-Rex-T-Rex",
        "Dough-Dough",
        "Shadow-Shadow",
        "Venom-Venom",
        "Control-Control",
        "Gas-Gas",
        "Spirit-Spirit",
        "Leopard-Leopard",
        "Yeti-Yeti",
        "Kitsune-Kitsune",
        "Dragon-Dragon"
    }
    
    SelectFruit = ""
    Teleport:AddDropdownLeft("Select Fruits Sniper",FruitList,function(value)
        SelectFruit = value
    end)
    
    Teleport:AddToggleLeft("Buy Fruit",AutoBuyFruitSniper,function(value)
        AutoBuyFruitSniper = value
    end)
    
    Teleport:AddSeperatorLeft("Others")
    
    Teleport:AddDropdownLeft("Select Fruits Eat",FruitList,function(value)
        SelectFruitEat = value
    end)
    
    Teleport:AddToggleLeft("Eat Fruits",AutoEatFruit,function(value)
        AutoEatFruit = value
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if AutoEatFruit then
                    game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectFruitEat).EatRemote:InvokeServer()
                end
            end
        end)
    end)
    
    Teleport:AddToggleLeft("Eat Fruits + Hop",AutoEatFruitHop,function(value)
        AutoEatFruitHop = value
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do wait(10)
                if AutoEatFruitHop and SelectFruitEat ~= nil then
                    if not game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectFruitEat) or not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(SelectFruitEat) then
                        Hop()
                    else
                        game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectFruitEat).EatRemote:InvokeServer()
                    end
                end
            end
        end)
    end)
spawn(function()
        pcall(function()
            while wait(.1) do
                if AutoBuyFruitSniper then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetFruits")
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("PurchaseRawFruit",SelectFruit)
                end 
            end
        end)
    end)
    
    Teleport:AddToggleLeft("Auto Random Fruit",Random_Auto,function(value)
        Random_Auto = value
    end)
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if Random_Auto then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin","Buy")
                end 
            end
        end)
    end)
    
    Teleport:AddButtonLeft("Random Fruit",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin","Buy")
    end)
    
    Teleport:AddToggleLeft("Auto Store Fruit",AutoStoreFruit,function(value)
        AutoStoreFruit = value
    end)
   
    local player = game.Players.LocalPlayer
    local backpack = player:FindFirstChild("Backpack")

    spawn(function()
        while task.wait(0.1) do
            if AutoStoreFruit then
                pcall(function()
                    for _, fruit in pairs(backpack:GetChildren()) do
                        if string.find(fruit.Name, "Fruit") then
                            -- ตรวจสอบว่ามี Attribute OriginalName หรือไม่
                            local originalName = fruit:GetAttribute("OriginalName")
                            if originalName then
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit", originalName, fruit)
                            end
                        end
                    end
                end)
            end
        end
    end)
    
  
    Teleport:AddToggleLeft("Bring Fruit",BringFruit,function(a)
    Bring = a
    end)
    
    spawn(function()
      while wait() do 
        pcall(function() 
          if Bring then 
  			  for i,v in pairs(game:GetService("Workspace"):GetChildren()) do if v:IsA("Tool") then if string.find(v.Name, "Fruit") then
   				 repeat wait() 
   					 wait(.1) 
    					v.Handle.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 5, 0)
   				 wait(.1) 
   				 v.Handle.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 2, 0)
   					 wait(1) 
   					 firetouchinterest(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart,v.Handle,0)
   					 wait(.1) 
   					 until not Bring  or v.Parent == game.Players.LocalPlayer.Character 
    end
    end
    end
    end
    end)
    end
    end)
   
Shop:AddSeperatorLeft("Abilities")
    
    Shop:AddButtonLeft("Buy Geppo",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Geppo")
    end)
    
    Shop:AddButtonLeft("Buy Buso Haki",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Buso")
    end)
    
    Shop:AddButtonLeft("Buy Soru",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Soru")
    end)
    
    Shop:AddButtonLeft("Buy Observation(Ken) Haki",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk","Buy")
    end)
    
    Shop:AddSeperatorLeft("Fighting Style")
    
    Shop:AddButtonLeft("Buy Black Leg",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
    end)
    
    Shop:AddButtonLeft("Buy Electro",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
    end)
    
    Shop:AddButtonLeft("Buy Fishman Karate",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
    end)
    
    Shop:AddButtonLeft("Buy Dragon Claw",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","1")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
    end)
    
    Shop:AddButtonLeft("Buy Superhuman",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
    end)
    
    Shop:AddButtonLeft("Buy Death Step",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
    end)
    
    Shop:AddButtonLeft("Buy Sharkman Karate",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
    end)
    
    Shop:AddButtonLeft("Buy Electric Claw",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
    end)
    
    Shop:AddButtonLeft("Buy Dragon Talon",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
    end)
    
    Shop:AddButtonLeft(" Buy God Human",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman")
    end)
    -----Shop----------------
    Shop:AddSeperatorLeft("Accessory")
    
    Shop:AddButtonLeft("Tomoe Ring",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Tomoe Ring")
    end)
    
    Shop:AddButtonLeft("Black Cape",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Black Cape")
    end)
    
    Shop:AddButtonLeft("Swordsman Hat",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Swordsman Hat")
    end)
    
    Shop:AddSeperatorLeft("Sword")
    
    Shop:AddButtonLeft("Cutlass",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Cutlass")
    end)
    
    Shop:AddButtonLeft("Katana",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Katana")
    end)
    
    Shop:AddButtonLeft("Iron Mace",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Iron Mace")
    end)
    
    Shop:AddButtonLeft("Duel Katana",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Duel Katana")
    end)
    
    Shop:AddButtonLeft("Triple Katana", function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Triple Katana")
    end)
    
    Shop:AddButtonLeft("Pipe",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Pipe")
    end)
    
    Shop:AddButtonLeft("Dual Headed Blade",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Dual-Headed Blade")
    end)
    
    Shop:AddButtonLeft("Bisento",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Bisento")
    end)
    
    Shop:AddButtonLeft("Soul Cane",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Soul Cane")
    end)
    
    Shop:AddSeperatorLeft("Gun")
    
    Shop:AddButtonLeft("Slingshot",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Slingshot")
    end)
    
    Shop:AddButtonLeft("Musket",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Musket")
    end)
    
    Shop:AddButtonLeft("Flintlock",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Flintlock")
    end)
    
    Shop:AddButtonLeft("Refined Flintlock",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Refined Flintlock")
    end)
    
    Shop:AddButtonLeft("Cannon",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Cannon")
    end)
    
    Shop:AddButtonLeft("Kabucha",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Slingshot","1")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Slingshot","2")
    end)
    ------------Bone------------------
    Shop:AddSeperatorLeft("Fragments")
    
    Shop:AddButtonLeft("Buy Refund Stat",function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Refund","1")
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Refund","2")
end)

    Shop:AddSeperatorLeft("Race")
    
    
Shop:AddButtonLeft("Buy Random Race",function()
    local args = {
        [1] = "BlackbeardReward",
        [2] = "Reroll",
        [3] = "2"
    }
    
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
end)
    
    Shop:AddButtonLeft("Ghoul",function()
        local args = {
    [1] = "Ectoplasm",
    [2] = "Change",
    [3] = 4
}

game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer(unpack(args))
local args = {
    [1] = "Ectoplasm",
    [2] = "BuyCheck",
    [3] = 4
}

game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer(unpack(args))
end)
Shop:AddButtonLeft("Cyborg",function()
    local args = {
    [1] = "CyborgTrainer",
    [2] = "Buy"
}

game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer(unpack(args))
end)
    Shop:AddSeperatorLeft("Bones")
    
    Shop:AddButtonLeft("Buy Surprise",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Buy",1,1)
    end)
    
    Shop:AddSeperatorRight("Fake")
    
    Shop:AddToggleRight("EnabledStat",EnabledStat,function(value)
        EnabledStat = value
    end)
    
    Shop:AddTextboxRight("Level","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["LocalPlayer"].Data.Level.Value = tonumber(value)
        end
    end)
    
    Shop:AddTextboxRight("Exp ","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["LocalPlayer"].Data.Exp.Value = tonumber(value)
        end
    end)
    
    Shop:AddTextboxRight("Beli","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["LocalPlayer"].Data.Beli.Value = tonumber(value)
        end
    end)
    
    Shop:AddTextboxRight("Fragments","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["Localplayer"].Data.Fragments.Value = tonumber(value)
        end
    end)
    
    Shop:AddTextboxRight("Melee","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["LocalPlayer"].Data.Stats.Melee.Level.Value = tonumber(value)
        end
    end)
    
    Shop:AddTextboxRight("Defense","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["LocalPlayer"].Data.Stats.Defense.Level.Value = tonumber(value)
        end
    end)
    
    Shop:AddTextboxRight("Sword","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["LocalPlayer"].Data.Stats.Sword.Level.Value = tonumber(value)
        end
    end)
    
    Shop:AddTextboxRight("Gun","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["LocalPlayer"].Data.Stats.Gun.Level.Value = tonumber(value)
        end
    end)
    Shop:AddTextboxRight("Fruit","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["LocalPlayer"].Data.Stats["Demon Fruit"].Level.Value = tonumber(value)
        end
    end)
    
    Shop:AddTextboxRight("Bounty","",true,function(value)
        if EnabledStat then
            game:GetService("Players")["LocalPlayer"].leaderstats["Bounty/Honor"].Value = tonumber(value)
        end
    end)
    
    Misc:AddSeperatorLeft("Server")
    
    Misc:AddButtonLeft("Rejoin Server",function()
        game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
    end)
    
    Misc:AddButtonLeft("Server Hop",function()
        Hop()
    end)
    
    Misc:AddButtonLeft("Hop To Lower Player",function()
        getgenv().AutoTeleport = true
        getgenv().DontTeleportTheSameNumber = true 
        getgenv().CopytoClipboard = false
        if not game:IsLoaded() then
            print("Game is loading waiting...")
        end
        local maxplayers = math.huge
        local serversmaxplayer;
        local goodserver;
        local gamelink = "https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100" 
        function serversearch()
            for _, v in pairs(game:GetService("HttpService"):JSONDecode(game:HttpGetAsync(gamelink)).data) do
                if type(v) == "table" and v.playing ~= nil and maxplayers > v.playing then
                    serversmaxplayer = v.maxPlayers
                    maxplayers = v.playing
                    goodserver = v.id
                end
            end       
        end
        function getservers()
            serversearch()
            for i,v in pairs(game:GetService("HttpService"):JSONDecode(game:HttpGetAsync(gamelink))) do
                if i == "nextPageCursor" then
                    if gamelink:find("&cursor=") then
                        local a = gamelink:find("&cursor=")
                        local b = gamelink:sub(a)
                        gamelink = gamelink:gsub(b, "")
                    end
                    gamelink = gamelink .. "&cursor=" ..v
                    getservers()
                end
            end
        end 
        getservers()
        if AutoTeleport then
            if DontTeleportTheSameNumber then 
                if #game:GetService("Players"):GetPlayers() - 4  == maxplayers then
                    return warn("It has same number of players (except you)")
                elseif goodserver == game.JobId then
                    return warn("Your current server is the most empty server atm") 
                end
            end
            game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, goodserver)
        end
    end)
    
    Misc:AddSeperatorLeft("Ui")
    
    Misc:AddButtonLeft("Open Devil Shop",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetFruits")
        game:GetService("Players").LocalPlayer.PlayerGui.Main.FruitShop.Visible = true
    end)
    
    Misc:AddButtonLeft("Open Inventory",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryWeapons")
        wait(1)
        game:GetService("Players").LocalPlayer.PlayerGui.Main.Inventory.Visible = true
    end)
    
    Misc:AddButtonLeft("Open Inventory Fruit",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryFruits")
        game:GetService("Players").LocalPlayer.PlayerGui.Main.FruitInventory.Visible = true
    end)
    
     Misc:AddButtonLeft("Open Colors haki",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getColors")
        game:GetService("Players").LocalPlayer.PlayerGui.Main.Colors.Visible = true
    end)
    
    Misc:AddButtonLeft("Open UpgradeItem Gun",function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Backpack","GetChildren")
        game:GetService("Players").LocalPlayer.PlayerGui.Main.Craft.Visible = true
  end)
    
    Misc:AddButtonLeft("Open Party Shop",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetStore")
        game:GetService("Players").LocalPlayer.PlayerGui.Main.CelebrationShop.Visible = true
    end)
    
    Misc:AddToggleLeft("Highlight Mode",false,function(value)
        if value == true then
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Beli.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.HP.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Energy.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.StatsButton.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.ShopButton.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Skills.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Level.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.MenuButton.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Code.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Settings.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Mute.Visible = false
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.CrewButton.Visible = false
        else
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Beli.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.HP.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Energy.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.StatsButton.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.ShopButton.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Skills.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Level.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.MenuButton.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Code.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Settings.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Mute.Visible = true
            game:GetService("Players")["LocalPlayer"].PlayerGui.Main.CrewButton.Visible = true
        end
    end)
    
    Misc:AddSeperatorLeft("Teams")
    
    Misc:AddButtonLeft("Join Pirates Team",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetTeam","Pirates") 
    end)
    
    Misc:AddButtonLeft("Join Marines Team",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetTeam","Marines") 
    end)
    
    Misc:AddSeperatorLeft("Codes")
    
    local x2Code = {
        "KITT_RESET",          -- ใช้สำหรับรีเซ็ตสถิติ
        "Sub2UncleKizaru",     -- ใช้สำหรับรีเซ็ตสถิติ
        "SUB2GAMERROBOT_RESET1", -- ใช้สำหรับรีเซ็ตสถิติ
        "Sub2OfficialNoobie",  -- รับโบนัส XP 2 เท่า
        "Axiore",              -- รับโบนัส XP 2 เท่า
        "Bluxxy",              -- รับโบนัส XP 2 เท่า
        "Enyu_is_Pro",         -- รับโบนัส XP 2 เท่า
        "JCWK",                -- รับโบนัส XP 2 เท่า
        "KittGaming",          -- รับโบนัส XP 2 เท่า
        "Magicbus",            -- รับโบนัส XP 2 เท่า
        "Starcodeheo",         -- รับโบนัส XP 2 เท่า
        "StrawHatMaine",       -- รับโบนัส XP 2 เท่า
        "Sub2CaptainMaui",     -- รับโบนัส XP 2 เท่า
        "Sub2Daigrock",        -- รับโบนัส XP 2 เท่า
        "Sub2Fer999",          -- รับโบนัส XP 2 เท่า
        "Sub2NoobMaster123",   -- รับโบนัส XP 2 เท่า
        "TantaiGaming",        -- รับโบนัส XP 2 เท่า
        "TheGreatAce",         -- รับโบนัส XP 2 เท่า
        "3BVISITS",            -- รับโบนัส XP 2 เท่า
        "UPD16"                -- รับโบนัส XP 2 เท่า
    }
    
    
    Misc:AddButtonLeft("Redeem All Codes",function()
        function RedeemCode(value)
            game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(value)
        end
        for i,v in pairs(x2Code) do
            RedeemCode(v)
        end
    end)
    
    Misc:AddDropdownLeft("Selected Codes",x2Code,function(value)
        CodeSelect = value
    end)
    
    Misc:AddButtonLeft("Redeem Code",function()
        game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(CodeSelect)
    end)
    
    Misc:AddSeperatorLeft("State")
    
    Misc:AddDropdownLeft("Select Haki State",{"State 0","State 1","State 2","State 3","State 4","State 5"},function(value)
        SelectStateHaki = value
    end)
    
    Misc:AddButtonLeft("Change Buso Haki State",function()
        if SelectStateHaki == "State 0" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",0)
        elseif SelectStateHaki == "State 1" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",1)
        elseif SelectStateHaki == "State 2" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",2)
        elseif SelectStateHaki == "State 3" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",3)
        elseif SelectStateHaki == "State 4" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",4)
        elseif SelectStateHaki == "State 5" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",5)
        end
    end)
    
    Misc:AddSeperatorLeft("Graphic")
    


    Misc:AddToggleLeft("Full Bright Mode", RTXMode, function(value)
        RTXMode = value
        local lighting = game:GetService("Lighting")
        local player = game:GetService("Players").LocalPlayer
        local humanoidRootPart = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
    
        -- บันทึกค่าเดิม
        local oldSettings = {
            Ambient = lighting.Ambient,
            Brightness = lighting.Brightness,
            ColorShift_Top = lighting.ColorShift_Top,
            ColorCorrection = lighting:FindFirstChildOfClass("ColorCorrectionEffect"),
            BloomEffect = lighting:FindFirstChildOfClass("BloomEffect"),
            FogEnd = lighting.FogEnd
        }
        
        if oldSettings.ColorCorrection then
            oldSettings.ColorCorrectionSettings = {
                Brightness = oldSettings.ColorCorrection.Brightness,
                Contrast = oldSettings.ColorCorrection.Contrast,
                TintColor = oldSettings.ColorCorrection.TintColor
            }
        end
    
        if oldSettings.BloomEffect then
            oldSettings.BloomEffectSettings = {
                TintColor = oldSettings.BloomEffect.TintColor
            }
        end
    
        -- ปิด Full Bright Mode
        if not RTXMode then
            lighting.Ambient = oldSettings.Ambient
            lighting.Brightness = oldSettings.Brightness
            lighting.ColorShift_Top = oldSettings.ColorShift_Top
            lighting.FogEnd = oldSettings.FogEnd
    
            if oldSettings.ColorCorrection then
                oldSettings.ColorCorrection.Brightness = oldSettings.ColorCorrectionSettings.Brightness
                oldSettings.ColorCorrection.Contrast = oldSettings.ColorCorrectionSettings.Contrast
                oldSettings.ColorCorrection.TintColor = oldSettings.ColorCorrectionSettings.TintColor
            end
    
            if oldSettings.BloomEffect then
                oldSettings.BloomEffect.TintColor = oldSettings.BloomEffectSettings.TintColor
            end
    
            -- ลบ PointLight
            if humanoidRootPart then
                local pointLight = humanoidRootPart:FindFirstChild("PointLight")
                if pointLight then
                    pointLight:Destroy()
                end
            end
            return
        end
    
        -- เปิด Full Bright Mode
        while RTXMode do
            wait()
            lighting.Ambient = Color3.fromRGB(255, 255, 255)
            lighting.Brightness = 2
            lighting.OutdoorAmbient = Color3.fromRGB(255, 255, 255)
            lighting.ColorShift_Bottom = Color3.fromRGB(255, 255, 255)
            lighting.ColorShift_Top = Color3.fromRGB(255, 255, 255)
            lighting.FogEnd = 1e6 -- ทำให้หมอกหายไป
    
            -- เพิ่ม PointLight ถ้ายังไม่มี
            if humanoidRootPart and not humanoidRootPart:FindFirstChild("PointLight") then
                local pointLight = Instance.new("PointLight", humanoidRootPart)
                pointLight.Brightness = 2
                pointLight.Range = 100
                pointLight.Color = Color3.fromRGB(255, 255, 255)
            end
        end
    end)
    
    Misc:AddToggleLeft("Remove Fog",RemoveFog,function(value)
        RemoveFog = value
    end)
    

    local removedObjects = {} -- ตารางสำหรับเก็บอ็อบเจกต์ที่ถูกลบ

    task.spawn(function()
        while wait() do
            pcall(function()
                if RemoveFog then
                    -- ลบหมอก
                    game.Lighting.FogEnd = 1e6
    
                    -- ลบ SeaTerrorCC ถ้ามี
                    local seaTerror = game.Lighting:FindFirstChild("SeaTerrorCC")
                    if seaTerror then
                        removedObjects["SeaTerrorCC"] = seaTerror:Clone()
                        seaTerror:Destroy()
                    end
    
                    -- ลบ LightingLayers ที่ตรงกับเงื่อนไข
                    for _, v in pairs(game:GetService("Lighting").LightingLayers:GetChildren()) do
                        if v.Name == "Atmosphere" or v.Name == "MirageFog" or v.Name == "DarkFog" or v.Name == "PrehistoricFog" or v.Name == "KitsuneFog" then
                            removedObjects[v.Name] = v:Clone()
                            v:Destroy()
                        end
                    end
                else
                    -- คืนค่าหมอก
                    game.Lighting.FogEnd = 2500 -- ตั้งค่า FogEnd ให้กลับมาปกติ
    
                    -- คืนค่า SeaTerrorCC ถ้าเคยลบ
                    if not game.Lighting:FindFirstChild("SeaTerrorCC") and removedObjects["SeaTerrorCC"] then
                        removedObjects["SeaTerrorCC"].Parent = game.Lighting
                        removedObjects["SeaTerrorCC"] = nil
                    end
    
                    -- คืนค่า LightingLayers ถ้าเคยลบ
                    for name, obj in pairs(removedObjects) do
                        if not game.Lighting.LightingLayers:FindFirstChild(name) then
                            obj.Parent = game.Lighting.LightingLayers
                            removedObjects[name] = nil
                        end
                    end
                end
            end)
        end
    end)
    
    
    Misc:AddSeperatorRight("Screen Shot Kaitan")
    
    Misc:AddButtonRight("Screen Shot Kaitun",function()
    local cac = require(game:GetService("Players").LocalPlayer.PlayerGui.Main.UIController.Inventory)
		local Inventory = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")
		local Items = {}
		local RaityLevel = {"Mythical","Legendary","Rare","Uncommon","Common"}
		local RaityColor =  {
			["Common"] = Color3.fromRGB(179, 179, 179),
			["Uncommon"] = Color3.fromRGB(92, 140, 211),
			["Rare"] =  Color3.fromRGB(140, 82, 255),
			["Legendary"] = Color3.fromRGB(213, 43, 228) ,
			["Mythical"] =  Color3.fromRGB(238, 47, 50)
		}
		function GetRaity(color)
			for k,v in pairs(RaityColor) do 
				if v==color then return k end
			end
		end

		for k,v in pairs(Inventory) do 
			Items[v.Name] = v
		end

		local total = #getupvalue(cac.UpdateRender,4)
		local rac = {}
		local allitem = {}
		local total2 = 0
		while total2<total do 
			local i = 0
			while i < 25000 and total2<total do 
				game:GetService("Players").LocalPlayer.PlayerGui.Main.InventoryContainer.Right.Content.ScrollingFrame.CanvasPosition = Vector2.new(0,i)
				for k,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.Main.InventoryContainer.Right.Content.ScrollingFrame.Frame:GetChildren()) do 
					if v:IsA("Frame") and not rac[v.ItemName.Text] and v.ItemName.Visible==true then 
						local vaihuhu = GetRaity(v.Background.BackgroundColor3)
						if vaihuhu then
							print("Rac")
							if not allitem[vaihuhu] then 
								allitem[vaihuhu] = {}
							end
							table.insert(allitem[vaihuhu],v:Clone())
						end
						total2=total2+1
						rac[v.ItemName.Text] = true
					end
				end
				i=i+20
			end
			wait()
		end
		function GetXY(vec) 
			return vec*100
		end

		local tvk = Instance.new("UIListLayout")
		tvk.FillDirection = Enum.FillDirection.Vertical
		tvk.SortOrder = 2
		tvk.Padding = UDim.new(0,10)

		local Left = Instance.new("Frame",game.Players.LocalPlayer.PlayerGui.BubbleChat)
		Left.BackgroundTransparency = 1
		Left.Size = UDim2.new(.5,0,1,0) 
		tvk.Parent = Left

		local Right = Instance.new("Frame",game.Players.LocalPlayer.PlayerGui.BubbleChat)
		Right.BackgroundTransparency = 1
		Right.Size = UDim2.new(.5,0,1,0) 
		Right.Position = UDim2.new(.6,0,0,0)
		tvk:Clone().Parent = Right
		for k,v in pairs(allitem) do 
			local cac = Instance.new("Frame",Left)
			cac.BackgroundTransparency = 1
			cac.Size = UDim2.new(1,0,0,0) 
			cac.LayoutOrder = table.find(RaityLevel,k)

			local cac2 = Instance.new("Frame",Right)
			cac2.BackgroundTransparency = 1
			cac2.Size = UDim2.new(1,0,0,0) 
			cac2.LayoutOrder = table.find(RaityLevel,k)

			local tvk = Instance.new("UIGridLayout",cac)
			tvk.CellPadding = UDim2.new(.005,0,.005,0)
			tvk.CellSize =  UDim2.new(0,70,0,70)
			tvk.FillDirectionMaxCells = 100
			tvk.FillDirection = Enum.FillDirection.Horizontal

			local ccc = tvk:Clone()
			ccc.Parent = cac2
			for k,v in pairs(v) do 
				if Items[v.ItemName.Text] and Items[v.ItemName.Text].Mastery then 
					if v.ItemLine2.Text~="Accessory" then 
						local bucac = v.ItemName:Clone()
						bucac.BackgroundTransparency = 1
						bucac.TextSize = 10
						bucac.TextXAlignment  = 2
						bucac.TextYAlignment  = 2
						bucac.ZIndex  = 5
						bucac.Text = Items[v.ItemName.Text].Mastery
						bucac.Size = UDim2.new(.5,0,.5,0)
						bucac.Position = UDim2.new(.5,0,.5,0)
						bucac.Parent = v
					end
					v.Parent = cac
				elseif v.ItemLine2.Text == "Blox Fruit" then 
					v.Parent = cac2
				end
			end
			cac.AutomaticSize = 2
			cac2.AutomaticSize = 2
		end
		local ListHuhu = {
			["Superhuman"] = Vector2.new(3,2),
			["DeathStep"] = Vector2.new(4,3),
			["ElectricClaw"] = Vector2.new(2,0),
			["SharkmanKarate"] = Vector2.new(0,0),
			["DragonTalon"] = Vector2.new(1,5)
		}
		local MeleeG = Instance.new("Frame",Left)
		MeleeG.BackgroundTransparency = 1
		MeleeG.Size = UDim2.new(1,0,0,0) 
		MeleeG.LayoutOrder = table.find(RaityLevel,k)
		MeleeG.AutomaticSize=2
		MeleeG.LayoutOrder = 100
		local tvk = Instance.new("UIGridLayout",MeleeG)
		tvk.CellPadding = UDim2.new(.005,0,.005,0)
		tvk.CellSize =  UDim2.new(0,70,0,70)
		tvk.FillDirectionMaxCells = 100
		tvk.FillDirection = Enum.FillDirection.Horizontal

		local cac = {"Superhuman","ElectricClaw","DragonTalon","SharkmanKarate","DeathStep","GodHuman"}
		for k,v in pairs(cac) do
			if ListHuhu[v] and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buy"..v,true) == 1 then 
				local huhu = Instance.new("ImageLabel",MeleeG)
				huhu.Image = "rbxassetid://9945562382"
				huhu.ImageRectSize = Vector2.new(100,100)
				huhu.ImageRectOffset = ListHuhu[v]*100
			end
		end
		function formatNumber(v)
			return tostring(v):reverse():gsub("%d%d%d", "%1,"):reverse():gsub("^,", "")
		end
		game:GetService("Players").LocalPlayer.PlayerGui.Main.Beli.Position = UDim2.new(0,800,0,500)
		game:GetService("Players").LocalPlayer.PlayerGui.Main.Level.Position = UDim2.new(0,800,0,550)

		local thieunang = game:GetService("Players").LocalPlayer.PlayerGui.Main.Fragments:Clone()
		thieunang.Parent = game:GetService("Players").LocalPlayer.PlayerGui.BubbleChat
		thieunang.Position = UDim2.new(0,800,0.63,0)
		local n = formatNumber(game.Players.LocalPlayer.Data.Fragments.Value)
		thieunang.Text = "ƒ"..n
		print("Done")
		pcall(function() 
			game:GetService("Players").LocalPlayer.PlayerGui.Main.MenuButton:Destroy()
		end)
		pcall(function() 
			game:GetService("Players").LocalPlayer.PlayerGui.Main.HP:Destroy()
		end)
		pcall(function() 
			game:GetService("Players").LocalPlayer.PlayerGui.Main.Energy:Destroy()
		end)
		for k,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.Main:GetChildren()) do 
			if v:IsA("ImageButton") then 
				v:Destroy()
			end
		end
		pcall(function() 
			game:GetService("Players").LocalPlayer.PlayerGui.Main.Compass:Destroy()
		end)
		end)
    
    Misc:AddButtonRight("Remoe ScreenKaitan",function()
    game:GetService("Players").LocalPlayer.PlayerGui.Main.Compass:Destroy()
    end)
    
     Misc:AddSeperatorLeft("Abilities")
    
    Misc:AddToggleLeft("Dodge No Cooldown",false,function(value)
        nododgecool = value
        NoDodgeCool()
    end)
    
    Misc:AddToggleLeft("Infinite Energy",false,function(value)
        InfiniteEnergy = value
        originalstam = LocalPlayer.Character.Energy.Value
    end)
    
    Misc:AddToggleLeft("Auto Active Race",AutoAgility,function(value)
        AutoAgility = value
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if AutoAgility then
                    game:GetService("ReplicatedStorage").Remotes.CommE:FireServer("ActivateAbility")
                end
            end
        end)
    end)
    
    Misc:AddToggleLeft("Auto Active Race V4",nil,function(a)
    AutoV4 = a
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if AutoV4 then
                    game:GetService("Players").LocalPlayer.Backpack.Awakening.RemoteFunction:InvokeServer(true)
                    end
            end
        end)
            end)
    
    Misc:AddToggleLeft("Infinite Ability",false,function(value)
        InfAbility = value
        if value == false then
            game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility"):Destroy()
        end
    end)
    
    spawn(function()
        while wait() do
            if InfAbility then
                InfAb()
            end
        end
    end)
    
    Misc:AddToggleLeft("Infinite Obversation Range",getgenv().InfiniteObRange,function(value)
        getgenv().InfiniteObRange = value
        local VS = game:GetService("Players").LocalPlayer.VisionRadius.Value
        while getgenv().InfiniteObRange do
            wait()
            local player = game:GetService("Players").LocalPlayer
            local char = player.Character
            local VisionRadius = player.VisionRadius
            if player then
                if char.Humanoid.Health <= 0 then 
                    wait(5) 
                end
                VisionRadius.Value = math.huge
            elseif getgenv().InfiniteObRange == false and player then
                VisionRadius.Value = VS
            end
        end
    end)
    
    Misc:AddToggleLeft("Infinite Geppo",getgenv().InfGeppo,function(value)
        getgenv().InfGeppo = value
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if getgenv().InfGeppo then
                    for i,v in next, getgc() do
                        if game:GetService("Players").LocalPlayer.Character.Geppo then
                            if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.Character.Geppo then
                                for i2,v2 in next, getupvalues(v) do
                                    if tostring(i2) == "9" then
                                        repeat wait(.1)
                                            setupvalue(v,i2,0)
                                        until not getgenv().InfGeppo or game:GetService("Players").LocalPlayer.Character.Humanoid.Health <= 0 
                                    end
                                end
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    Misc:AddToggleLeft("Infinite Soru",getgenv().InfSoru,function(value)
        getgenv().InfSoru = value
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if getgenv().InfSoru and game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart") ~= nil  then
                    for i,v in next, getgc() do
                        if game:GetService("Players").LocalPlayer.Character.Soru then
                            if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.Character.Soru then
                                for i2,v2 in next, getupvalues(v) do
                                    if typeof(v2) == "table" then
                                        repeat wait(.1)
                                            v2.LastUse = 0
                                        until not getgenv().InfSoru or game:GetService("Players").LocalPlayer.Character.Humanoid.Health <= 0
                                    end
                                end
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    Misc:AddToggleLeft("Walk in Weter",WhiteScreen,function(value)
    oip = value
if oip == true then
    game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,114,1000)
elseif oip == false then
    game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,80,1000)
end
end)
    
    Misc:AddToggleLeft("Fly",false,function(value)
        Fly = value
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if Fly then
                    fly()
                else
                    unFly()
                end
            end)
        end
    end)
    

    Misc:AddSeperatorRight("Boots")
    
    Misc:AddButtonRight("Unlock Portal",function()
        UnlockPortal = true
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if UnlockPortal == true then
                    for i,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.Notifications:GetChildren()) do
                        if v.Name == "NotificationTemplate" then
                            if string.find(v.Text,"cannot") then
                                v:Destroy()
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if UnlockPortal == true then
                    CastlePostoMansion = CFrame.new(-5084.8447265625, 316.48101806641, -3145.3752441406)
                    MansiontoCastlePos = CFrame.new(-12464.596679688, 376.30590820312, -7567.2626953125)
                    Castletophydra = CFrame.new(-5095.33984375, 316.48101806641, -3168.3134765625)
                    HydratoCastle = CFrame.new(5741.869140625, 611.94750976562, -282.61154174805)
                    if (CastlePostoMansion.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 8 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
                    end
                    if (MansiontoCastlePos.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 8 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-5072.08984375, 314.5412902832, -3151.1098632812))
                    end
                    if (Castletophydra.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 8 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(5748.7587890625, 610.44982910156, -267.81704711914))
                    end
                    if (HydratoCastle.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 8 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-5072.08984375, 314.5412902832, -3151.1098632812))
                    end
                end
            end)
        end
    end)
    

    Misc:AddButtonRight("Invisible",function()
        game:GetService("Players").LocalPlayer.Character.LowerTorso:Destroy()
    end)
    
    Misc:AddButtonLeft("Click TP Tool",function()
        local plr = game:GetService("Players").LocalPlayer
        local mouse = plr:GetMouse()
        local tool = Instance.new("Tool")
        tool.RequiresHandle = false
        tool.Name = "Click To Tp"
        tool.Activated:Connect(function()
        local root = plr.Character.HumanoidRootPart
        local pos = mouse.Hit.Position+Vector3.new(0,2.5,0)
        local offset = pos-root.Position
        root.CFrame = root.CFrame+offset
        end)
        tool.Parent = plr.Backpack
    end)
    
    Misc:AddButtonRight("Stop All Tween",function()
        Tween(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
        Clip = false
    end)
    Misc:AddButtonRight("Remove Rocks",function()
	workspace:FindFirstChild("Rocks"):Destroy()
end)
    Misc:AddButtonRight("FPS Boost",function()
         local decalsyeeted = true
local g = game
local w = g.Workspace
local l = g.Lighting
local t = w.Terrain

-- ปรับค่า Water ใน Terrain
t.WaterWaveSize = 0
t.WaterWaveSpeed = 0
t.WaterReflectance = 0
t.WaterTransparency = 0

-- ปิดการเปิดใช้งาน Global Shadows
l.GlobalShadows = false

-- ปรับค่าแสงและการเงา
l.FogEnd = 9e9
l.Brightness = 0

-- ปรับค่าคุณภาพการเล่น
settings().Rendering.QualityLevel = "Level01"

-- ปรับแต่งส่วนประกอบแต่ละชนิด
for i, v in pairs(g:GetDescendants()) do
    if v:IsA("Part") or v:IsA("Union") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then 
        v.Material = "Plastic"
        v.Reflectance = 0
    elseif (v:IsA("Decal") or v:IsA("Texture")) and decalsyeeted then
        v.Transparency = 1
    elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
        v.Lifetime = NumberRange.new(0)
    elseif v:IsA("Explosion") then
        v.BlastPressure = 1 
        v.BlastRadius = 1
    elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
        v.Enabled = false
    elseif v:IsA("MeshPart") then
        v.Material = "Plastic"
        v.Reflectance = 0
        v.TextureID = 10385902758728957
    end
end

-- ปิดเอฟเฟคต่าง ๆ ใน Lighting
for i, e in pairs(l:GetChildren()) do
    if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
        e.Enabled = false
    end
end

    end)
    local Select_Farme_Rate = 60

    -- สร้าง slider เพื่อให้ผู้ใช้เลือกค่า Select_Farme_Rate
    Misc:AddSliderRight("Select Farme Rate", 0, 240, Select_Farme_Rate, function(a)
        Select_Farme_Rate = a  -- ใช้ตัวแปร a แทนค่า Select_Farme_Rate
    end)
    
    -- สร้าง toggle เพื่อเปิด/ปิดการตั้งค่า FPS cap
    Misc:AddToggleRight("Unlock FPS", Unlock_FPS, function()
        while Unlock_FPS do
            setfpscap(Select_Farme_Rate) -- ตั้งค่าความเร็วเฟรมตามค่า Select_Farme_Rate
            task.wait(1) -- รอ 1 วินาทีเพื่อไม่ให้ลูปทำงานหนักเกินไป
        end
    end)
    
    
    
    Misc:AddButtonRight("Max Zoom",function()
    game.Players.LocalPlayer.CameraMaxZoomDistance = 100000
    end)
    
            Misc:AddSeperatorRight("Status")
    
    local locallv = Misc:AddLabelRight("Level")
    
    spawn(function()
        while wait() do
            pcall(function()
                locallv:Set("Level :".." "..game:GetService("Players").LocalPlayer.Data.Level.Value)
            end)
        end
    end)
    
    local localrace = Misc:AddLabelRight("Race")
    
    spawn(function()
        while wait() do
            pcall(function()
                localrace:Set("Race :".." "..game:GetService("Players").LocalPlayer.Data.Race.Value)
            end)
        end
    end)
    
    local localbeli = Misc:AddLabelRight("Beli")
    
    spawn(function()
        while wait() do
            pcall(function()
                localbeli:Set("Beli :".." "..game:GetService("Players").LocalPlayer.Data.Beli.Value)
            end)
        end
    end)
    
    local localfrag = Misc:AddLabelRight("Fragment")
    
    spawn(function()
        while wait() do
            pcall(function()
                localfrag:Set("Fragments :".." "..game:GetService("Players").LocalPlayer.Data.Fragments.Value)
            end)
        end
    end)
    
    
    local localexp = Misc:AddLabelRight("ExP")
    
    spawn(function()
        while wait() do
            pcall(function()
                localexp:Set("EXP :".." "..game:GetService("Players").LocalPlayer.Data.Exp.Value)
            end)
        end
    end)
    
    local localstat = Misc:AddLabelRight("Stats Points")
    
    spawn(function()
        while wait() do
            pcall(function()
                localstat:Set("Stats Points :".." "..game:GetService("Players").LocalPlayer.Data.Points.Value)
            end)
        end
    end)
    
    local localbountyhornor = Misc:AddLabelRight("Bounty")
    
    spawn(function()
        while wait() do
            pcall(function()
                localbountyhornor:Set("Bounty  / Honor :".." "..game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value)
            end)
        end
    end)
    
    local localDevil = Misc:AddLabelRight("Devil Fruit")
    
    spawn(function()
        while wait() do
            pcall(function()
                if game:GetService("Players").LocalPlayer.Character:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
                    localDevil:Set("Fruit :".." "..game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
                else
                    localDevil:Set("You Not Fruit")
                end
            end)
        end
    end)
    
    
    Misc:AddSeperatorRight("Credit")
    Misc:AddLabelRight("Ui : ball naja#3764")
    Misc:AddLabelRight("Dev : ball naja#3764")
        Setting:AddSeperatorLeft("Beta function")


 Setting:AddSeperatorRight("Dev Function")
    Setting:AddButtonLeft("Copy CFrame",function()
        setclipboard(tostring(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame))
end)

Setting:AddButtonLeft("Dex Mobile",function()
    --[[
	WARNING: Heads up! This script has not been verified by ScriptBlox. Use at your own risk!
]]
loadstring(game:HttpGet("https://raw.githubusercontent.com/realredz/DEX-Explorer/refs/heads/main/Mobile.lua"))()
end)

Setting:AddButtonLeft("RemoteSpy",function()
   --[[
	WARNING: Heads up! This script has not been verified by ScriptBlox. Use at your own risk!
]]
loadstring(game:HttpGet("https://raw.githubusercontent.com/realredz/SimpleSpy/refs/heads/main/Mobile.lua"))()
end)

Sea:AddSeperatorLeft("Prehistoric Island")
local Pic = Sea:AddLabelLeft("")
    
function Pi()
if game:GetService("Workspace").Map:FindFirstChild("PrehistoricIsland") then
    Pic:Set("Prehistoric Island : Spawn")   
   else
    Pic:Set("Prehistoric Island : Not Spawn")    
   end
   end

spawn(function()
while task.wait() do
pcall(function()
    Pi()
end)
end
end)
Sea:AddToggleLeft("Tp To Prehistoric Island",Tp_To_Prehistoric_Island,function(a)
    Tp_To_Prehistoric_Island = a
end)

spawn(function()
    while wait() do
        pcall(function()
            if Tp_To_Prehistoric_Island then
                UnSit()
                TweenSit(workspace.Map:FindFirstChild("PrehistoricIsland").WorldPivot)
            end
        end)
    end
end)

Sea:AddSeperatorLeft("Mystic Island")
local Mrc = Sea:AddLabelLeft("")
    
function Mr()
if game:GetService("Workspace").Map:FindFirstChild("MysticIsland") then
    Mrc:Set("Mystic Island : Spawn")   
   else
    Mrc:Set("Mystic Island : Not Spawn")    
   end
   end

spawn(function()
while task.wait() do
pcall(function()
    Mr()
end)
end
end)
Sea:AddToggleLeft("Tp To Mystic Island",Tp_To_Mystic_Island,function(a)
    Tp_To_Mystic_Island = a
end)

spawn(function()
    while wait() do
        pcall(function()
            if Tp_To_Mystic_Island then
                UnSit()
                TweenSit(CFrame.new(game:GetService("Workspace").Map.MysticIsland.npcspawn.npcSpawn.Position))
            end
        end)
    end
end)
Sea:AddToggleLeft("Tp To Mystic Island Npc",Tp_To_Mystic_Island_Npc,function(a)
Tp_To_Mystic_Island_Npc = a
end)

spawn(function()
    pcall(function()
        while wait() do
            if Tp_To_Mystic_Island_Npc then
                    repeat
                        wait()
                    until game:GetService("Workspace").Map:FindFirstChild("MysticIsland")
                    if game:GetService("Workspace").Map:FindFirstChild("MysticIsland") then
                        AllNPCS = getnilinstances()
                        for r, v in pairs(game:GetService("Workspace").NPCs:GetChildren()) do
                            table.insert(AllNPCS, v)
                        end
                        for r, v in pairs(AllNPCS) do
                            if v.Name == "Advanced Fruit Dealer" then
                                Tween(v.HumanoidRootPart.CFrame)
                            end
                        end
                    end
                end
            end
    end)
end)

Sea:AddSeperatorLeft("Kitsune Island")
local Kic = Sea:AddLabelLeft("")

      function Ki()
     if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Kitsune Island") then
       Kic:Set("Kitsune Island: Spawn")   
         else
            Kic:Set("Kitsune Island : Not Spawn")    
         end
         end

  spawn(function()
 while task.wait() do
     pcall(function()
        Ki()
     end)
 end
end)

Sea:AddToggleLeft("TP To Kitsune Island",KitsuneIsland,function(a)
KitsuneIsland = a
StopTween(KitsuneIsland)
end)

spawn(function()
pcall(function()
 while wait() do
 if KitsuneIsland then
    UnSit()
    TweenSit(CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Kitsune Island").Position))
         end
     end
 end)
end)
Sea:AddToggleLeft("Auto Get Ember",AutoEmber,function(a)
AutoEmber = a
end)

spawn(function()
while wait() do
pcall(function()
if AutoEmber then
for i,v in pairs(workspace:GetChildren()) do
if v.Name == "EmberTemplate" then
  repeat wait()
            TweenSit(v.Part.CFrame)
  until not AutoEmber or not v.Parent
end
 end
end
end)
end
end) 

Sea:AddSeperatorRight("Sea Event")

Sea:AddDropdownRight("Select Boat To Farm",{"Lantern","Guardian"},function(value)
SelectBoat = value
end)

 Sea:AddToggleRight("Auto Sea Event",Auto_Sea_Event,function(a)
Auto_Sea_Event = a
StopTween(Auto_Sea_Event)
end)



spawn(function()
 while wait() do
  pcall(function()
   if AutoClick then
     game:GetService'VirtualUser':CaptureController()
	game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
end
end)
end
end)

spawn(function()
 while wait() do
  pcall(function()
   if Auto_Sea_Event then
      for i,v in pairs(game.Workspace.Enemies:GetChildren()) do    
           if v.Name == "Shark" or v.Name == "Piranha" or v.Name == "Terrorshark" then
								repeat wait()
                                                                AutoHaki()
								EquipWeapon(SelectWeapon)
								Tween(v.Head.CFrame * CFrame.new(0,55,0))
			                                 	game:GetService'VirtualUser':CaptureController()
	                                                        game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
								until not  Auto_Sea_Event or not v.Parent or v.Humanoid.Health <= 0 
						
end
								end
								end
								


								end)
								end
								end)


Sea:AddToggleRight("Auto Dirvve Bost",Auto_Walk_Bost,function(a)
 Auto_Walk_Bost = a
 local virtualInput = game:GetService("VirtualInputManager")
 game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,80,1000)
 virtualInput:SendKeyEvent(false, "W", false, game)
 end)

 spawn(function()
    while wait() do
        pcall(function()
            if Auto_Walk_Bost then
                local boats = game:GetService("Workspace").Boats
                local player = game:GetService("Players").LocalPlayer
                local humanoidRootPart = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
                local destination = CFrame.new(-9533.85938, 7.56481552, -8375.44531, 0.962026298, 5.02222548e-08, -0.272956669, -7.66087567e-08, 1, -8.60114113e-08, 0.272956669, 1.03656113e-07, 0.962026298)

                if humanoidRootPart then
                    local ownedBoat = nil
                    local playerName = player.Name

                    -- ตรวจสอบว่ามีเรือที่เป็นของผู้เล่นหรือไม่
                    for _, boat in pairs(boats:GetChildren()) do
                        if boat:FindFirstChild("Owner") and tostring(boat.Owner.Value) == playerName then
                            ownedBoat = boat
                            break
                        end
                    end

                    -- ถ้าไม่มีเรือ ให้ Tween ไปยังตำแหน่งที่กำหนด
                    if not ownedBoat then
                        TweenSit(destination)

                        -- รอจนกระทั่งถึงตำแหน่งที่กำหนด
                        while (humanoidRootPart.Position - destination.Position).Magnitude > 5 do
                            wait()
                        end

                        if SelectBoat then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBoat", SelectBoat)
                        end
                    end

                    -- ถ้ามีเรือและ VehicleSeat อยู่ ให้ทำการ Tween ไปยังเรือ
                    if ownedBoat and ownedBoat:FindFirstChild("VehicleSeat") then
                        local boatPosition = ownedBoat.VehicleSeat.CFrame
                        TweenSit(boatPosition)
                        ownedBoat.VehicleSeat.MaxSpeed = 350
                        game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,440,1000)


                        -- จำลองการกดปุ่ม W
                        local virtualInput = game:GetService("VirtualInputManager")
                        virtualInput:SendKeyEvent(true, "W", false, game)
                    end
                end
            end
        end)
    end
end)




Sea:AddSeperatorRight("Boat")

          BoatsName = {}

for i,v in pairs(game:GetService("Workspace").Boats:GetChildren()) do  
  table.insert(BoatsName ,v.Name)
end

local Boats = Sea:AddDropdownRight("Selected Boats",BoatsName,function(plys)
  SelectB = plys
end)


Sea:AddButtonRight("Refresh Boat",function()
  Boats:Clear()
  for i,v in pairs(game:GetService("Workspace").Boats:GetChildren()) do  
     Boats:Add(v.Name)
  end
end)

Speed = 350
Sea:AddSliderRight("Selected Speed Boat",1,500,Speed,function(value)
    Speed = value
end)

Sea:AddToggleRight("Unlock Speed Boat",USB,function(a)
USB = a
end)

spawn(function()
 while wait() do
  pcall(function()
 if USB then
  game:GetService("Workspace").Boats:FindFirstChild(SelectB).VehicleSeat.MaxSpeed = Speed
end
end)
end
end)


Sea:AddToggleRight("Boat Flying",BoatFly,function(a)
    if a then
    game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,440,1000)
    else
    game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,80,1000)
    end
end)
         
Sea:AddButtonRight("Bring Boat",function()
         game:GetService("Workspace").Boats:FindFirstChild(SelectB).VehicleSeat.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
end)
