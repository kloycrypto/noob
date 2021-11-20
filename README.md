game.StarterGui:SetCore("SendNotification", {
    Title = "Prior X";
    Text = "Checking";
    Duration = 15;
})
wait(3)

local p = Instance.new("IntValue")
p.Parent = workspace
p.Value = game.Players.LocalPlayer.userId
getuser = game.Players.LocalPlayer.Name
message = "Logged in"





local plr = game.Players.LocalPlayer
repeat wait() until plr.Character
local gui = script.Parent

    game.StarterGui:SetCore("SendNotification", {
    Title = "Welcome";
    Text = getuser;
    Duration = 20;
})


local L_3_ = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local L_4_ = L_3_.CreateLib("Prior X", "DarkTheme")
local L_13_ = L_4_:NewTab("Keybinds")
local L_14_ = L_13_:NewSection("Selections")
L_14_:NewKeybind(
	"Keybind Gui Toggle",
	"Toggles Gui Script",
	Enum.KeyCode.V,
	function()
		L_3_:ToggleUI()
	end
)

local L_5_ = L_4_:NewTab("Aimlock")
local L_6_ = L_5_:NewSection("Selections")
L_6_:NewButton(
	"Silent Aimlock",
	"Silent A Circle Tracks Them",
	function()
	_G.KEY = "q"
_G.PART = "HumanoidRootPart"
_G.PRED = 0.10
_G.Frame = Vector3.new(0, 0.53, 0)
local L_76_ = game:GetService "Workspace".CurrentCamera
local L_77_
local L_78_ = false
local L_79_ = nil
local L_80_ = game.Players.LocalPlayer:GetMouse()
local L_81_ = Instance.new("Part", game.Workspace)
local L_82_ = Instance.new("Folder", game.CoreGui)
function makemarker(L_86_arg0, L_87_arg1, L_88_arg2, L_89_arg3, L_90_arg4)
	local L_91_ = Instance.new("BillboardGui", L_86_arg0)
	L_91_.Name = "PP"
	L_91_.Adornee = L_87_arg1
	L_91_.Size = UDim2.new(L_89_arg3, L_90_arg4, L_89_arg3, L_90_arg4)
	L_91_.AlwaysOnTop = true
	local L_92_ = Instance.new("Frame", L_91_)
	L_92_.Size = UDim2.new(4, 0, 4, 0)
	L_92_.BackgroundTransparency = 0.1
	L_92_.BackgroundColor3 = L_88_arg2
	local L_93_ = Instance.new("UICorner", L_92_)
	L_93_.CornerRadius = UDim.new(50, 50)
	return L_91_
end
local L_83_ = game.Players:GetPlayers()
function noob(L_94_arg0)
	local L_95_
	repeat
		wait()
	until L_94_arg0.Character
	local L_96_ = makemarker(L_82_, L_94_arg0.Character:WaitForChild(_G.PART), Color3.fromRGB(255, 255, 255), 0.0, 0)
	L_96_.Name = L_94_arg0.Name
	L_94_arg0.CharacterAdded:connect(
		function(L_98_arg0)
			L_96_.Adornee = L_98_arg0:WaitForChild(_G.PART)
		end
	)
	local L_97_ = Instance.new("TextLabel", L_96_)
	L_97_.BackgroundTransparency = 1
	L_97_.Position = UDim2.new(0, 0, 0, -50)
	L_97_.Size = UDim2.new(0, 100, 0, 100)
	L_97_.Font = Enum.Font.SourceSansSemibold
	L_97_.TextSize = 14
	L_97_.TextColor3 = Color3.new(1, 1, 1)
	L_97_.TextStrokeTransparency = 0
	L_97_.TextYAlignment = Enum.TextYAlignment.Bottom
	L_97_.Text = "Name: " .. L_94_arg0.Name
	L_97_.ZIndex = 10
	spawn(
		function()
			while wait() do
				if L_94_arg0.Character then
				end
			end
		end
	)
end
for L_99_forvar0 = 1, #L_83_ do
	if L_83_[L_99_forvar0] ~= game.Players.LocalPlayer then
		noob(L_83_[L_99_forvar0])
	end
end
game.Players.PlayerAdded:connect(
	function(L_100_arg0)
		noob(L_100_arg0)
	end
)
game.Players.PlayerRemoving:Connect(
	function(L_101_arg0)
		L_82_[L_101_arg0.Name]:Destroy()
	end
)
spawn(
	function()
		L_81_.Anchored = true
		L_81_.CanCollide = false
		L_81_.Size = Vector3.new(0.1, 0.1, 0.1)
		L_81_.Transparency = 0.1
		makemarker(L_81_, L_81_, Color3.fromRGB(255, 255, 255), 0.20, 0)
	end
)
L_80_.KeyDown:Connect(
	function(L_102_arg0)
		if L_102_arg0 ~= _G.KEY then
			return
		end
		if L_78_ then
			L_78_ = false
			TextLabel.TextColor3 = Color3.fromRGB(255, 20, 75)
			TextLabel.Text = "------"
		else
			L_78_ = true
			L_77_ = getClosestPlayerToCursor()
			TextLabel.TextColor3 = Color3.fromRGB(12, 255, 0)
			TextLabel.Text = L_77_.Character.Humanoid.DisplayName
		end
	end
)
function getClosestPlayerToCursor()
	local L_103_
	local L_104_ = math.huge
	for L_105_forvar0, L_106_forvar1 in pairs(game.Players:GetPlayers()) do
		if
			L_106_forvar1 ~= game.Players.LocalPlayer and L_106_forvar1.Character and L_106_forvar1.Character:FindFirstChild("Humanoid") and
			L_106_forvar1.Character.Humanoid.Health ~= 0 and
			L_106_forvar1.Character:FindFirstChild(_G.PART)
		then
			local L_107_ = L_76_:WorldToViewportPoint(L_106_forvar1.Character.PrimaryPart.Position)
			local L_108_ = (Vector2.new(L_107_.X, L_107_.Y) - Vector2.new(L_80_.X, L_80_.Y)).magnitude
			if L_108_ < L_104_ then
				L_103_ = L_106_forvar1
				L_104_ = L_108_
			end
		end
	end
	return L_103_
end
game:GetService "RunService".Stepped:connect(
	function()
		if L_78_ and L_77_.Character and L_77_.Character:FindFirstChild(_G.PART) then
			L_81_.CFrame =
				CFrame.new(L_77_.Character[_G.PART].Position + _G.Frame + L_77_.Character[_G.PART].Velocity * L_79_)
		else
			L_81_.CFrame = CFrame.new(0, 9999, 0)
		end
	end
)
local L_84_ = getrawmetatable(game)
local L_85_ = L_84_.__namecall
setreadonly(L_84_, false)
L_84_.__namecall =
	newcclosure(
		function(...)
		local L_109_ = {
			...
		}
		if L_78_ and getnamecallmethod() == "FireServer" and L_109_[2] == "UpdateMousePos" then
			L_109_[3] = L_77_.Character[_G.PART].Position + _G.Frame + L_77_.Character[_G.PART].Velocity * L_79_
			return L_85_(unpack(L_109_))
		end
		return L_85_(...)
	end
	)
game.Players.LocalPlayer.Chatted:Connect(
	function(L_110_arg0)
		if L_110_arg0 == "/e print" then
			print(_G.PRED)
		end
	end
)
game.Players.LocalPlayer.Chatted:Connect(
	function(L_111_arg0)
		if L_111_arg0 == "Code:1029" then
			_G.KEY = nil
			_G.AIR = nil
			_G.PART = nil
			_G.PRED = nil
			TextLabel.Visible = false
		end
	end
)
game.Players.LocalPlayer.Chatted:Connect(
	function(L_112_arg0)
		if L_112_arg0 == "/e hrp" then
			_G.KEY = "q"
			_G.AIR = 0.00005
			_G.PART = "HumanoidRootPart"
			_G.PRED = 0.032
			TextLabel.Visible = true
		end
	end
)
game.Players.LocalPlayer.Chatted:Connect(
	function(L_113_arg0)
		if L_113_arg0 == "/e lt" then
			_G.KEY = "q"
			_G.AIR = 0.00005
			_G.PART = "LowerTorso"
			_G.PRED = 0.032
			TextLabel.Visible = true
		end
	end
)
game.Players.LocalPlayer.Chatted:Connect(
	function(L_114_arg0)
		if L_114_arg0 == "Screensharing" then
			_G.KEY = "q"
			_G.AIR = 0.00005
			_G.PART = "LowerTorso"
			_G.PRED = 0.033
			TextLabel.Visible = true
			L_81_ = nil
		end
	end
)
game.Players.LocalPlayer.Chatted:Connect(
	function(L_115_arg0)
		if L_115_arg0 == "/e P+" then
			_G.PRED = _G.PRED + 0.001
		end
	end
)
game.Players.LocalPlayer.Chatted:Connect(
	function(L_116_arg0)
		if L_116_arg0 == "/e P-" then
			_G.PRED = _G.PRED - 0.001
		end
	end
)
while wait() do
	if
		getClosestPlayerToCursor().Character.Humanoid.Jump == true and
		getClosestPlayerToCursor().Character.Humanoid.FloorMaterial == Enum.Material.Air
	then
		_G.Frame = Vector3.new(0, -2.3, 0)
		wait(0.05)
	else
		local L_117_ = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString()
		local L_118_ = tostring(L_117_)
		local L_119_ = L_118_:split(" ")
		local L_120_ = L_119_[1]
		L_79_ = L_120_ / 1000 + _G.PRED
		_G.Frame = Vector3.new(0, 0.53, 0)
	end
end
	end)

L_6_:NewButton(
	"Aimlock",
	"Camlock",
	function() 
	    		getgenv().AimPart = "HumanoidRootPart"
		getgenv().AimlockKey = "q"
		getgenv().AimRadius = 50
		getgenv().ThirdPerson = true
		getgenv().FirstPerson = true
		getgenv().TeamCheck = false
		getgenv().PredictMovement = true
		getgenv().PredictionVelocity = 9
		local L_27_, L_28_, L_29_, L_30_ =
			game:GetService "Players",
		game:GetService "UserInputService",
		game:GetService "RunService",
		game:GetService "StarterGui"
		local L_31_, L_32_, L_33_, L_34_, L_35_, L_36_, L_37_ =
			L_27_.LocalPlayer,
		L_27_.LocalPlayer:GetMouse(),
		workspace.CurrentCamera,
		CFrame.new,
		Ray.new,
		Vector3.new,
		Vector2.new
		local L_38_, L_39_, L_40_ = true, false, false
		local L_41_
		getgenv().PriorX = true
		getgenv().WorldToViewportPoint = function(L_42_arg0)
			return L_33_:WorldToViewportPoint(L_42_arg0)
		end
		getgenv().WorldToScreenPoint = function(L_43_arg0)
			return L_33_.WorldToScreenPoint(L_33_, L_43_arg0)
		end
		getgenv().GetObscuringObjects = function(L_44_arg0)
			if L_44_arg0 and L_44_arg0:FindFirstChild(getgenv().AimPart) and L_31_ and L_31_.Character:FindFirstChild("Head") then
				local L_45_ = workspace:FindPartOnRay(L_35_(L_44_arg0[getgenv().AimPart].Position, L_31_.Character.Head.Position))
				if L_45_ then
					return L_45_:IsDescendantOf(L_44_arg0)
				end
			end
		end
		getgenv().GetNearestTarget = function()
			local L_46_ = {}
			local L_47_ = {}
			local L_48_ = {}
			for L_50_forvar0, L_51_forvar1 in pairs(L_27_:GetPlayers()) do
				if L_51_forvar1 ~= L_31_ then
					table.insert(L_46_, L_51_forvar1)
				end
			end
			for L_52_forvar0, L_53_forvar1 in pairs(L_46_) do
				if L_53_forvar1.Character ~= nil then
					local L_54_ = L_53_forvar1.Character:FindFirstChild("Head")
					if getgenv().TeamCheck == true and L_53_forvar1.Team ~= L_31_.Team then
						local L_55_ =
							(L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
						local L_56_ =
							Ray.new(
								game.Workspace.CurrentCamera.CFrame.p,
								(L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_55_
							)
						local L_57_, L_58_ = game.Workspace:FindPartOnRay(L_56_, game.Workspace)
						local L_59_ = math.floor((L_58_ - L_54_.Position).magnitude)
						L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
						L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_55_
						L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
						L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_59_
						table.insert(L_48_, L_59_)
					elseif getgenv().TeamCheck == false and L_53_forvar1.Team == L_31_.Team then
						local L_60_ =
							(L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
						local L_61_ =
							Ray.new(
								game.Workspace.CurrentCamera.CFrame.p,
								(L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_60_
							)
						local L_62_, L_63_ = game.Workspace:FindPartOnRay(L_61_, game.Workspace)
						local L_64_ = math.floor((L_63_ - L_54_.Position).magnitude)
						L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
						L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_60_
						L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
						L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_64_
						table.insert(L_48_, L_64_)
					end
				end
			end
			if unpack(L_48_) == nil then
				return nil
			end
			local L_49_ = math.floor(math.min(unpack(L_48_)))
			if L_49_ > getgenv().AimRadius then
				return nil
			end
			for L_65_forvar0, L_66_forvar1 in pairs(L_47_) do
				if L_66_forvar1.diff == L_49_ then
					return L_66_forvar1.plr
				end
			end
			return nil
		end
		L_32_.KeyDown:Connect(
			function(L_67_arg0)
				if L_67_arg0 == AimlockKey and L_41_ == nil then
					pcall(
						function()
							if L_39_ ~= true then
								L_39_ = true
							end
							local L_68_
							L_68_ = GetNearestTarget()
							if L_68_ ~= nil then
								L_41_ = L_68_
							end
						end
					)
				elseif L_67_arg0 == AimlockKey and L_41_ ~= nil then
					if L_41_ ~= nil then
						L_41_ = nil
					end
					if L_39_ ~= false then
						L_39_ = false
					end
				end
			end
		)
		L_29_.RenderStepped:Connect(
			function()
				if getgenv().ThirdPerson == true and getgenv().FirstPerson == true then
					if
						(L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 or
						(L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1
					then
						L_40_ = true
					else
						L_40_ = false
					end
				elseif getgenv().ThirdPerson == true and getgenv().FirstPerson == false then
					if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 then
						L_40_ = true
					else
						L_40_ = false
					end
				elseif getgenv().ThirdPerson == false and getgenv().FirstPerson == true then
					if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1 then
						L_40_ = true
					else
						L_40_ = false
					end
				end
				if L_38_ == true and L_39_ == true then
					if L_41_ and L_41_.Character and L_41_.Character:FindFirstChild(getgenv().AimPart) then
						if getgenv().FirstPerson == true then
							if L_40_ == true then
								if getgenv().PredictMovement == true then
									L_33_.CFrame =
										L_34_(
											L_33_.CFrame.p,
											L_41_.Character[getgenv().AimPart].Position +
											L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
										)
								elseif getgenv().PredictMovement == false then
									L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
								end
							end
						elseif getgenv().ThirdPerson == true then
							if L_40_ == true then
								if getgenv().PredictMovement == true then
									L_33_.CFrame =
										L_34_(
											L_33_.CFrame.p,
											L_41_.Character[getgenv().AimPart].Position +
											L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
										)
								elseif getgenv().PredictMovement == false then
									L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
								end
							end
						end
					end
				end
			end
		)
	end
)
L_6_:NewTextBox(
	"AimlockKey",
	"Keybind (Selection)",
	function(L_69_arg0)
		getgenv().AimlockKey = L_69_arg0
	end
)
L_6_:NewTextBox(
	"PredictionVelocity",
	"PredictionVelocity (Selection)",
	function(L_70_arg0)
		PredictionVelocity = L_70_arg0
	end
)
L_6_:NewDropdown(
	"TargetAimPart",
	"BodyPart (Selection)",
	{
		"Head",
		"UpperTorso",
		"HumanoidRootPart",
		"LowerTorso"
	},
	function(L_71_arg0)
		getgenv().AimPart = L_71_arg0
	end
)
local L_7_ = L_4_:NewTab("Silent Aim")
local L_8_ = L_7_:NewSection("Selection")
L_8_:NewButton(
	"Silent Aim",
	"Silent Aim",
	function()

local Aiming = loadstring(game:HttpGet("https://raw.githubusercontent.com/NotPluschi/CoolXpirqpexor/main/javalua"))()
Aiming.TeamCheck(false)

local Workspace = game:GetService("Workspace")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")

local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()
local CurrentCamera = Workspace.CurrentCamera

local DaHoodSettings = {
    SilentAim = true,
    AimLock = false,
    Prediction = 0.10,
    AimLockKeybind = Enum.KeyCode.E
}
getgenv().DaHoodSettings = DaHoodSettings

function Aiming.Check()
    if not (Aiming.Enabled == true and Aiming.Selected ~= LocalPlayer and Aiming.SelectedPart ~= nil) then
        return false
    end

    local Character = Aiming.Character(Aiming.Selected)
    local KOd = Character:WaitForChild("BodyEffects")["K.O"].Value
    local Grabbed = Character:FindFirstChild("GRABBING_CONSTRAINT") ~= nil

    if (KOd or Grabbed) then
        return false
    end

    return true
end

local __index
__index = hookmetamethod(game, "__index", function(t, k)
    if (t:IsA("Mouse") and (k == "Hit" or k == "Target") and Aiming.Check()) then
        local SelectedPart = Aiming.SelectedPart

        if (DaHoodSettings.SilentAim and (k == "Hit" or k == "Target")) then
            local Hit = SelectedPart.CFrame + (SelectedPart.Velocity * DaHoodSettings.Prediction)

            return (k == "Hit" and Hit or SelectedPart)
        end
    end

    return __index(t, k)
end)

RunService:BindToRenderStep("AimLock", 0, function()
    if (DaHoodSettings.AimLock and Aiming.Check() and UserInputService:IsKeyDown(DaHoodSettings.AimLockKeybind)) then
        local SelectedPart = Aiming.SelectedPart

        local Hit = SelectedPart.CFrame + (SelectedPart.Velocity * DaHoodSettings.Prediction)

        CurrentCamera.CFrame = CFrame.lookAt(CurrentCamera.CFrame.Position, Hit.Position)
    end
    end)

	end
) 
L_8_:NewTextBox(
	"Prediction",
	"Prediction (Selection)",
	function(L_72_arg0)
		DaHoodSettings.Prediction = L_72_arg0
	end
)
L_8_:NewDropdown(
	"TargetAimPart",
	"BodyPart (Selection)",
	{
		"Head",
		"UpperTorso",
		"HumanoidRootPart",
		"LowerTorso"
	},
	function(L_73_arg0)
		Aiming.TargetPart = L_73_arg0
	end
)
L_8_:NewTextBox(
	"FovSize",
	"FovSize (Selection)",
	function(L_74_arg0)
		Aiming.FOV = L_74_arg0
	end
)
L_8_:NewToggle(
	"FovCircle",
	"Fov Circle (Selection)",
	function(L_75_arg0)
		Aiming.ShowFOV = L_75_arg0
	end
)

local L_11_ = L_4_:NewTab("Anti Stuff")
local L_12_ = L_11_:NewSection("Selection")
L_12_:NewButton(
	"Kaias",
	"Keyinds T = On/Off M = Faster N = Slower",
    function()
        IsFirstPerson = false
ShiftHeld = false
WHeld = false
SHeld = false
AHeld = false
DHeld = false -- LMFAO
local gcheck = true
urspeed = 0.05 -- The lower it is the faster. So don't worry about it being minus 1


function ChangeFaster(inputObject, gameProcessedEvent)
    if inputObject.KeyCode == Enum.KeyCode.N and gameProcessedEvent == false then        
urspeed = urspeed - 0.025
    end
end
 


function ChangeSlower(inputObject, gameProcessedEvent)
    if inputObject.KeyCode == Enum.KeyCode.M and gameProcessedEvent == false then        
urspeed = urspeed + 0.7
    end
end
 


function GChecker(inputObject, gameProcessedEvent)
    if inputObject.KeyCode == Enum.KeyCode.T and gameProcessedEvent == false then        
if gcheck == false then
gcheck = true
elseif gcheck == true then
gcheck = false
end

    end
end
 
game:GetService("UserInputService").InputBegan:connect(GChecker)



function PressShift(inputObject,gameProcessedEvent)
    if inputObject.KeyCode == Enum.KeyCode.LeftShift and gameProcessedEvent == false and gcheck == true then
        ShiftHeld = true
    end
end

function ReleaseShift(inputObject,gameProcessed)
    if inputObject.KeyCode == Enum.KeyCode.LeftShift then
        ShiftHeld = false
    end
end


function PressW(inputObject,gameProcessedEvent)
    if inputObject.KeyCode == Enum.KeyCode.W and gameProcessedEvent == false and gcheck == true then
        WHeld = true
    end
end

function ReleaseW(inputObject,gameProcessed)
    if inputObject.KeyCode == Enum.KeyCode.W then
        WHeld = false
    end
end

function PressS(inputObject,gameProcessedEvent)
    if inputObject.KeyCode == Enum.KeyCode.S and gameProcessedEvent == false and gcheck == true then
        SHeld = true
    end
end

function ReleaseS(inputObject,gameProcessed)
    if inputObject.KeyCode == Enum.KeyCode.S then
        SHeld = false
    end
end


function PressA(inputObject,gameProcessedEvent)
    if inputObject.KeyCode == Enum.KeyCode.A and gameProcessedEvent == false and gcheck == true then
        AHeld = true
    end
end

function ReleaseA(inputObject,gameProcessed)
    if inputObject.KeyCode == Enum.KeyCode.A then
        AHeld = false
    end
end


function PressD(inputObject,gameProcessedEvent)
    if inputObject.KeyCode == Enum.KeyCode.D and gameProcessedEvent == false and gcheck == true then
        DHeld = true
    end
end

function ReleaseD(inputObject,gameProcessed)
    if inputObject.KeyCode == Enum.KeyCode.D then
        DHeld = false
    end
end

function CheckFirst(inputObject,gameProcessed)
    if inputObject.KeyCode == Enum.UserInputType.MouseWheel then
        if (player.Character.Head.CFrame.p - workspace.CurrentCamera.CFrame.p).magnitude < 0.6 then
            IsFirstPerson = true
	elseif (player.Character.Head.CFrame.p - workspace.CurrentCamera.CFrame.p).magnitude > 0.6 then
	    IsFirstPerson = false
        end
    end
end

game:GetService("UserInputService").InputBegan:connect(PressShift)
game:GetService("UserInputService").InputEnded:connect(ReleaseShift)

game:GetService("UserInputService").InputBegan:connect(PressW)
game:GetService("UserInputService").InputEnded:connect(ReleaseW)

game:GetService("UserInputService").InputBegan:connect(PressS)
game:GetService("UserInputService").InputEnded:connect(ReleaseS)

game:GetService("UserInputService").InputBegan:connect(PressA)
game:GetService("UserInputService").InputEnded:connect(ReleaseA)

game:GetService("UserInputService").InputBegan:connect(PressD)
game:GetService("UserInputService").InputEnded:connect(ReleaseD)

game:GetService("UserInputService").InputChanged:connect(CheckFirst)

game:GetService("UserInputService").InputBegan:connect(ChangeFaster)
game:GetService("UserInputService").InputBegan:connect(ChangeSlower)


game:GetService('RunService').Stepped:connect(function()
if ShiftHeld == true then

if WHeld == true then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,0,-urspeed)
end

if SHeld == true then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,0,urspeed)
end

if DHeld == true then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(urspeed,0,0)
end

if AHeld == true then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(-urspeed,0,0)
end


end
end)

repeat
    wait()
until game:IsLoaded()
local gm = getrawmetatable(game)
setreadonly(gm, false)
local namecall = gm.__namecall
gm.__namecall =
    newcclosure(
    function(self, ...)
        local args = {...}
        if not checkcaller() and getnamecallmethod() == "FireServer" and tostring(self) == "MainEvent" then
            if tostring(getcallingscript()) ~= "Framework" then
                return
            end
        end
        if not checkcaller() and getnamecallmethod() == "Kick" then
            return
        end
        return namecall(self, unpack(args))
    end
)
    end)
    
L_12_:NewButton(
	"Antilock",
	"Keybinds H = Fixes Z = On/Off",
    function()
    	repeat
			wait()
		until game:IsLoaded()
		getgenv().Fix = true
		getgenv().TeclasWS = {
			["tecla1"] = "nil",
			["tecla2"] = "nil",
			["tecla3"] = "H"
		}
		local L_121_ = game:GetService("Players")
		local L_122_ = game:GetService("StarterGui") or "son una mierda"
		local L_123_ = L_121_.LocalPlayer
		local L_124_ = L_123_:GetMouse()
		local L_125_ = getrenv()._G
		local L_126_ = getrawmetatable(game)
		local L_127_ = L_126_.__newindex
		local L_128_ = L_126_.__index
		local L_129_ = 22
		local L_130_ = true
		function anunciar_atentado_terrorista(L_138_arg0)
		end
		getgenv().TECHWAREWALKSPEED_LOADED = true
		wait(1.5)
		anunciar_atentado_terrorista("Press  " .. TeclasWS.tecla3 .. " to turn on/off anti lock fix")
		L_124_.KeyDown:Connect(
			function(L_139_arg0)
				if L_139_arg0:lower() == TeclasWS.tecla1:lower() then
					L_129_ = L_129_ + 1
					anunciar_atentado_terrorista("播放器速度已提高 (speed = " .. tostring(L_129_) .. ")")
				elseif L_139_arg0:lower() == TeclasWS.tecla2:lower() then
					L_129_ = L_129_ - 1
					anunciar_atentado_terrorista("玩家的速度已降低 (speed = " .. tostring(L_129_) .. ")")
				elseif L_139_arg0:lower() == TeclasWS.tecla3:lower() then
					if L_130_ then
						L_130_ = false
						anunciar_atentado_terrorista("anti lock fix off")
					else
						L_130_ = true
						anunciar_atentado_terrorista("anti lock fix on")
					end
				end
			end
		)
		setreadonly(L_126_, false)
		L_126_.__index =
			newcclosure(
				function(L_140_arg0, L_141_arg1)
				local L_142_ = checkcaller()
				if L_141_arg1 == "WalkSpeed" and not L_142_ then
					return L_125_.CurrentWS
				end
				return L_128_(L_140_arg0, L_141_arg1)
			end
			)
		L_126_.__newindex =
			newcclosure(
				function(L_143_arg0, L_144_arg1, L_145_arg2)
				local L_146_ = checkcaller()
				if L_130_ then
					if L_144_arg1 == "WalkSpeed" and L_145_arg2 ~= 0 and not L_146_ then
						return L_127_(L_143_arg0, L_144_arg1, L_129_)
					end
				end
				return L_127_(L_143_arg0, L_144_arg1, L_145_arg2)
			end
			)
		setreadonly(L_126_, true)
		repeat
			wait()
		until game:IsLoaded()
		local L_131_ = game:service("Players")
		local L_132_ = L_131_.LocalPlayer
		repeat
			wait()
		until L_132_.Character
		local L_133_ = game:service("UserInputService")
		local L_134_ = game:service("RunService")
		local L_135_ = -0.27
		local L_136_ = false
		local L_137_
		L_133_.InputBegan:connect(
			function(L_147_arg0)
				if L_147_arg0.KeyCode == Enum.KeyCode.LeftBracket then
					L_135_ = L_135_ + 0.01
					print(L_135_)
					wait(0.2)
					while L_133_:IsKeyDown(Enum.KeyCode.LeftBracket) do
						wait()
						L_135_ = L_135_ + 0.01
						print(L_135_)
					end
				end
				if L_147_arg0.KeyCode == Enum.KeyCode.RightBracket then
					L_135_ = L_135_ - 0.01
					print(L_135_)
					wait(0.2)
					while L_133_:IsKeyDown(Enum.KeyCode.RightBracket) do
						wait()
						L_135_ = L_135_ - 0.01
						print(L_135_)
					end
				end
				if L_147_arg0.KeyCode == Enum.KeyCode.Z then
					L_136_ = not L_136_
					if L_136_ == true then
						repeat
							game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame +
								game.Players.LocalPlayer.Character.Humanoid.MoveDirection * L_135_
							game:GetService("RunService").Stepped:wait()
						until L_136_ == false
					end
				end
			end
		)
    end
)
L_12_:NewButton(
	"Antiban",
	"Prevents you from getting banned 99%",
    function()
        local annoying = {"JokeTheFool", "Sherosama", "dtbbullet", "AStrongMuscle", "XavierWild", "NikoSenpai", "UziGarage", "iumu", "Benoxa", "Luutyy", "clubstar54", "givkitheth", "DrxcoBaby" , "DrxcoRxsh" } -- you can add more players by doing {"Player1", "Player2"}
 
game.Players.PlayerAdded:Connect(function(plr)
for i, v in pairs(annoying) do
if plr.Name == v then
local loc = game.Players.LocalPlayer
loc:Kick("Kicked an admin has joined")
end
end
end)
end)
local L_11_ = L_4_:NewTab("Other Stuff")
local L_12_ = L_11_:NewSection("Selection")
L_12_:NewButton(
	"Fly (X)",
	"Super Power",
    function()
        repeat wait() 
	until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Head") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid") 
	local mouse = game.Players.LocalPlayer:GetMouse() 
	repeat wait() until mouse
	local plr = game.Players.LocalPlayer 
	local torso = plr.Character.Head 
	local flying = false
	local deb = true 
	local ctrl = {f = 0, b = 0, l = 0, r = 0} 
	local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
	local maxspeed = 4000000000000000000000000 
	local speed =  4000000000000000000000000 

	function Fly() 
		local bg = Instance.new("BodyGyro", torso) 
		bg.P = 9e4 
		bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
		bg.cframe = torso.CFrame 
		local bv = Instance.new("BodyVelocity", torso) 
		bv.velocity = Vector3.new(0,0.1,0) 
		bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
		repeat wait() 
			plr.Character.Humanoid.PlatformStand = true 
			if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then 
				speed = speed+.5+(speed/maxspeed) 
				if speed > maxspeed then 
					speed = maxspeed 
				end 
			elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then 
				speed = speed-1 
				if speed < 0 then 
					speed = 0 
				end 
			end 
			if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then 
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
				lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r} 
			elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then 
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
			else 
				bv.velocity = Vector3.new(0,0.1,0) 
			end 
			bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0) 
		until not flying 
		ctrl = {f = 0, b = 0, l = 0, r = 0} 
		lastctrl = {f = 0, b = 0, l = 0, r = 0} 
		speed = 0 
		bg:Destroy() 
		bv:Destroy() 
		plr.Character.Humanoid.PlatformStand = false 
	end 
	mouse.KeyDown:connect(function(key) 
		if key:lower() == "x" then 
			if flying then flying = false 
			else 
				flying = true 
				Fly() 
			end 
		elseif key:lower() == "w" then 
			ctrl.f = 1 
		elseif key:lower() == "s" then 
			ctrl.b = -1 
		elseif key:lower() == "a" then 
			ctrl.l = -1 
		elseif key:lower() == "d" then 
			ctrl.r = 1 
		end 
	end) 
	mouse.KeyUp:connect(function(key) 
		if key:lower() == "w" then 
			ctrl.f = 0 
		elseif key:lower() == "s" then 
			ctrl.b = 0 
		elseif key:lower() == "a" then 
			ctrl.l = 0 
		elseif key:lower() == "d" then 
			ctrl.r = 0 
		end 
	end)
	Fly()
end)
L_12_:NewButton(
	"Headless",
	"CilentSided Headless",
    function()
game.Players.LocalPlayer.Character.Head.Transparency = 1
	for i,v in pairs(game.Players.LocalPlayer.Character.Head:GetChildren()) do
		if (v:IsA("Decal")) then
			v:Destroy()
		end
	end
end)
L_12_:NewButton(
	"Korblox Right",
	"CilentSided RightLeg",
    function()
    local ply = game.Players.LocalPlayer
	local chr = ply.Character
	chr.RightLowerLeg.MeshId = "902942093"
	chr.RightLowerLeg.Transparency = "1"
	chr.RightUpperLeg.MeshId = "http://www.roblox.com/asset/?id=902942096"
	chr.RightUpperLeg.TextureID = "http://roblox.com/asset/?id=902843398"
	chr.RightFoot.MeshId = "902942089"
	chr.RightFoot.Transparency = "1"
end)
L_12_:NewButton(
	"Korblox Left",
	"CilentSided LeftLeg",
    function()
        local ply = game.Players.LocalPlayer
	local chr = ply.Character
	chr.LeftLowerLeg.MeshId = "902942093"
	chr.LeftLowerLeg.Transparency = "1"
	chr.LeftUpperLeg.MeshId = "http://www.roblox.com/asset/?id=902942096"
	chr.LeftUpperLeg.TextureID = "http://roblox.com/asset/?id=902843398"
	chr.LeftFoot.MeshId = "902942089"
	chr.LeftFoot.Transparency = "1"
    end)
    L_12_:NewTextBox(
	"Field Of View",
	"Like Makes Ur POV Better IG?",
    function()
     amount = bruh
    game:GetService'Workspace'.Camera.FieldOfView = amount
    end)
    L_12_:NewButton(
	"Infinite Zoom",
	"U can Zoom out how far you want",
    function()
    game:GetService("Players").LocalPlayer.CameraMaxZoomDistance = math.huge
    end)

local L_11_ = L_4_:NewTab("Teleports")
local L_12_ = L_11_:NewSection("Selection")
L_12_:NewButton(
	"Rev Mountain",
	"Teleports 2 Rev Mountain",
    function()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-696.847717, 167.674957, -41.0118256, 0.626992583, 7.53169349e-09, -0.779025197, -1.29610933e-09, 1, 8.62493632e-09, 0.779025197, -4.39806902e-09, 0.626992583)
    end)
L_12_:NewButton(
	"Db Mountain",
	"Teleports 2 Db Mountain",
    function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1087.02783, 104.254997, -268.160614, 0.0359299146, -0.000130457382, -0.99935472, -2.87694893e-05, 1, -0.000131575929, 0.99935472, 3.34783836e-05, 0.0359299146)
    end)
    L_12_:NewButton(
	"Flame Mountain",
	"Teleports 2 Frame Mountain",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-228.709259, 96.75, -46.1524429, 0.988781095, -6.16038989e-08, -0.149372295, 5.44428751e-08, 1, -5.20298862e-08, 0.149372295, 4.33139249e-08, 0.988781095)
    end)
       L_12_:NewButton(
	"Tacital Mountain",
	"Teleports 2 Tacital Mountain",
    function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(493.328918, 112.5, -689.263916, -0.999886096, 0.000241556234, -0.0150990579, 0.000226202334, 0.999999464, 0.00101856329, 0.0150993001, 0.00101503218, -0.999885678)
    end)
       L_12_:NewButton(
	"Church Mountain",
	"Teleports 2 Church Mountain",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(288.8479, 143.25, -245.123169, -0.999539435, 3.95160157e-07, 0.0303715728, -3.52983733e-07, 1, -2.46274394e-05, -0.0303715728, -2.4626821e-05, -0.999539435)
    end)
     L_12_:NewButton(
	"Admin Guns",
	"Teleports 2 Admin Guns ",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-872.853516, -34.4276848, -538.013306, -0.999724388, -3.9898886e-08, -0.0234765243, -3.9204977e-08, 1, -3.00177518e-08, 0.0234765243, -2.90890814e-08, -0.999724388)
    end)
     L_12_:NewButton(
	"Admin Guns 2",
	"Teleports 2 Admin Guns 2 ",
    function()
        	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-808.708557, -39.6492004, -932.789368, 0.999899805, 2.01343173e-08, -0.0141554065, -2.17800533e-08, 1, -1.16108232e-07, 0.0141554065, 1.16404912e-07, 0.999899805)
    end)
      L_12_:NewButton(
	"Admin Foods",
	"Teleports 2 Admin Foods ",
    function()
       	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-788.053406, -39.6492004, -932.951233, 0.998369277, 2.46515359e-08, 0.0570784509, -2.8773524e-08, 1, 7.13949646e-08, -0.0570784509, -7.29209759e-08, 0.998369277) 
    end)
       L_12_:NewButton(
	"HighMediumArmor",
	"Buys HighMediumArmor ",
    function()
        local plr = game.Players.LocalPlayer
	local savedarmourpos = plr.Character.HumanoidRootPart.Position
	plr.Character.HumanoidRootPart.CFrame = CFrame.new(-938.476685, -25.2498264, 570.100159, -0.0353576206, 9.85617206e-08, -0.999374807, -2.69198441e-09, 1, 9.871858e-08, 0.999374807, 6.18077589e-09, -0.0353576206)
	wait(.2)

	fireclickdetector(game.Workspace.Ignored.Shop['[High-Medium Armor] - $2300'].ClickDetector)
	plr.Character.HumanoidRootPart.CFrame = CFrame.new(savedarmourpos)
    end)
      L_12_:NewButton(
	"Ufo",
	"Teleports 2 Ufo ",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2.85052466, 132, -736.571106, -0.0460956171, -4.24733706e-08, -0.998937011, 7.26012459e-08, 1, -4.58687275e-08, 0.998937011, -7.46384217e-08, -0.0460956171)
    end)
       L_12_:NewButton(
	"Rpg",
	"Teleports 2 Rpg ",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(139.815933, -22.9016266, -136.737762, 0.0339428484, -7.90177737e-08, 0.999423802, -4.7851227e-08, 1, 8.06884728e-08, -0.999423802, -5.0562452e-08, 0.0339428484)
    end)
        L_12_:NewButton(
	"Bank",
	"Teleports 2 Bank ",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-318.891174, 80.2145309, -257.177429, 0.0479469746, -5.14644114e-08, 0.998850107, -3.12971538e-09, 1, 5.16738901e-08, -0.998850107, -5.60372015e-09, 0.0479469746)
    end)
         L_12_:NewButton(
	"Taco",
	"Teleports 2 Taco ",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(707.502014, 139, -543.044739, -0.00318608154, -0.00102963799, 0.999993861, 0.000187970581, 0.999999464, 0.00103024102, -0.99999404, 0.00019125198, -0.00318560796)
    end)
          L_12_:NewButton(
	"DrumGun",
	"Teleports 2 DrumGun ",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-80.8381271, 46.828949, -85.845993, 0.999289691, 4.71884114e-08, 0.0376862474, -4.71660684e-08, 1, -1.48225032e-09, -0.0376862474, -2.96314889e-10, 0.999289691)
    end)
           L_12_:NewButton(
	"Rev Roof",
	"Teleports 2 Rev Roof",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-634.463135, 80.434761, -204.232559, -0.0190527271, -1.03574322e-07, -0.999818563, 4.36709335e-09, 1, -1.03676342e-07, 0.999818563, -6.3416179e-09, -0.0190527271)
    end)
            L_12_:NewButton(
	"PlayGround",
	"Teleports 2 PlayGround",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-308.851196, 103.049866, -685.874817, 0.0775452703, 4.43633544e-05, -0.996988416, 4.02679916e-06, 1, 4.48105384e-05, 0.996988416, -7.48951334e-06, 0.0775452703)
    end)
            L_12_:NewButton(
	"G Station",
	"Teleports 2 G Station",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(595.925171, 130.75, -346.41568, -0.0400748774, 7.26109022e-08, 0.999196708, 2.20863914e-08, 1, -7.17834538e-08, -0.999196708, 1.91919352e-08, -0.0400748774)
    end)
              L_12_:NewButton(
	"Cementery",
	"Teleports 2 Cementery",
    function()
        	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(135.109558, 99.75, -57.2315979, 0.999993503, -0.000633752206, -0.0035054055, 0.000638642872, 0.999998808, 0.00139435288, 0.00350463158, -0.00139658386, 0.999992728)
    end)
               L_12_:NewButton(
	"School Roof",
	"Teleports 2 School Roof",
    function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-525.353455, 68.125, 311.824402, 0.999992013, 1.03866675e-08, -0.00399552286, -1.03507425e-08, 1, 9.01170427e-09, 0.00399552286, -8.97027519e-09, 0.999992013)
    end)

local L_11_ = L_4_:NewTab("Misc Stuff")
local L_12_ = L_11_:NewSection("Selection")
L_12_:NewButton(
	"Noclip (C) Broken",
	"Go Through Walls",
    function()
          noclip = false
    game:GetService('RunService').Stepped:connect(function()
    if noclip then
    game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
    end
    end)
    mouse = plr:GetMouse()
    mouse.KeyDown:connect(function(key)
    
    if key == "c" then
    noclip = not noclip
    game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
    end
    end)
    end)
    L_12_:NewButton(
	"Speed Glitch (X)",
	"Macro",
    function()
    	local Player = game:GetService("Players").LocalPlayer
			local Mouse = Player:GetMouse()
			local SpeedGlitch = false
			local Wallet = Player.Backpack:FindFirstChild("Wallet")

			local UniversalAnimation = Instance.new("Animation")

			function stopTracks()
				for _, v in next, game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):GetPlayingAnimationTracks() do
					if (v.Animation.AnimationId:match("rbxassetid")) then
						v:Stop()
					end
				end
			end

			function loadAnimation(id)
				if UniversalAnimation.AnimationId == id then
					stopTracks()
					UniversalAnimation.AnimationId = "1"
				else
					UniversalAnimation.AnimationId = id
					local animationTrack = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):LoadAnimation(UniversalAnimation)
					animationTrack:Play()
				end
			end

			Mouse.KeyDown:Connect(function(Key)
				if Key == "x" then
					SpeedGlitch = not SpeedGlitch
					if SpeedGlitch == true then
						stopTracks()
						loadAnimation("rbxassetid://3189777795")
						wait(1.5)
						Wallet.Parent = Player.Character
						wait(0.15)
						Player.Character:FindFirstChild("Wallet").Parent = Player.Backpack
						wait(0.05)
						repeat game:GetService("RunService").Heartbeat:wait()
							keypress(0x49)
							game:GetService("RunService").Heartbeat:wait()
							keypress(0x4F)
							game:GetService("RunService").Heartbeat:wait()
							keyrelease(0x49)
							game:GetService("RunService").Heartbeat:wait()
							keyrelease(0x4F)
							game:GetService("RunService").Heartbeat:wait()
						until SpeedGlitch == false
					end
				end
			end)
		end)
     L_12_:NewButton(
	"AutoClicker (Z)",
	"Shoots Faster/Auto Shoots",
    function()
        local Player = game:GetService("Players").LocalPlayer
			local Mouse = Player:GetMouse()
			local Clicking = false
			Mouse.KeyDown:Connect(function(Key)
				if Key == "z" then
					Clicking = not Clicking
					if Clicking == true then
						repeat
							mouse1click()
							wait(0.001)
						until Clicking == false
					end
				end
			end)
		end)
     L_12_:NewButton(
	"Recoil",
	"Recoil",
    function()
       function isframework(scriptInstance)
        if tostring(scriptInstance) == "Framework" then
            return true
        end
        return false
    end
    
    function checkArgs(instance,index)
        if tostring(instance):lower():find("camera") and tostring(index) == "CFrame" then
            return true
        end
        return false
    end
    
    newindex = hookmetamethod(game, "__newindex", function(self,index,value)
        local callingScr = getcallingscript()
    
        if isframework(callingScr) and checkArgs(self,index) then
           return;
        end
    
        return newindex(self,index,value)
    end)

    end)
     L_12_:NewButton(
	"UnderGround",
	"Keyinds O = Underground P = Go Up",
    function()
    underground = false
        plr = game.Players.LocalPlayer
        mouse = plr:GetMouse()
        mouse.KeyDown:connect(function(key)
        
        if key == "o" then
        
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,-9,0)
        game:GetService('RunService').Stepped:connect(function()
        if underground then
        game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
        end
        end)
        end
        end)
        wait()
        
        plr = game.Players.LocalPlayer
        mouse = plr:GetMouse()
        mouse.KeyDown:connect(function(key)
        
        if key == "p" then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,11,0)
        underground = not underground
        game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
        end
        end)
    end)
     L_12_:NewButton(
	"Autofarm",
	"Grinds Money",
    function()
    --[[
Da Hood auto rob script by Amnesia
I know script became a bit monkey code but i am lazy to make it look better
I didn't obfuscate it because why not
]]
repeat
    wait()
until game:IsLoaded()
local gm = getrawmetatable(game)
setreadonly(gm, false)
local namecall = gm.__namecall
gm.__namecall =
    newcclosure(
    function(self, ...)
        local args = {...}
        if not checkcaller() and getnamecallmethod() == "FireServer" and tostring(self) == "MainEvent" then
            if tostring(getcallingscript()) ~= "Framework" then
                return
            end
        end
        if not checkcaller() and getnamecallmethod() == "Kick" then
            return
        end
        return namecall(self, unpack(args))
    end
)

local LocalPlayer = game:GetService("Players").LocalPlayer

function gettarget()
    local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:wait()
    local HumanoidRootPart = Character:WaitForChild("HumanoidRootPart")
    local maxdistance = math.huge
    local target
    for i, v in pairs(game:GetService("Workspace").Cashiers:GetChildren()) do
        if v:FindFirstChild("Head") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
            local distance = (HumanoidRootPart.Position - v.Head.Position).magnitude
            if distance < maxdistance then
                target = v
                maxdistance = distance
            end
        end
    end
    return target
end

for i, v in pairs(workspace:GetDescendants()) do
    if v:IsA("Seat") then
        v:Destroy()
    end
end


shared.MoneyFarm = true -- Just execute shared.MoneyFarm = false to stop farming

while shared.MoneyFarm do
    wait()
    local Target = gettarget()
    repeat
        wait()
        pcall(
            function()
                local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:wait()
                local HumanoidRootPart = Character:WaitForChild("HumanoidRootPart")
                local Combat = LocalPlayer.Backpack:FindFirstChild("Combat") or Character:FindFirstChild("Combat")
                if not Combat then
                    Character:FindFirstChild("Humanoid").Health = 0
                    return
                end
                HumanoidRootPart.CFrame = Target.Head.CFrame * CFrame.new(0, -2.5, 3)
                Combat.Parent = Character
                Combat:Activate()
            end
        )
    until not Target or Target.Humanoid.Health < 0
    for i, v in pairs(game:GetService("Workspace").Ignored.Drop:GetDescendants()) do
        if v:IsA("ClickDetector") and v.Parent and v.Parent.Name:find("Money") then
            local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:wait()
            local HumanoidRootPart = Character:WaitForChild("HumanoidRootPart")
            if (v.Parent.Position - HumanoidRootPart.Position).magnitude <= 18 then
                repeat
                    wait()
                    fireclickdetector(v)
                until not v or not v.Parent.Parent
            end
        end
    end
    wait(1)
end
    end)
     L_12_:NewButton(
	"AutoStomp",
	"Stomps Without No Animation",
    function()
    while true do
wait(.05)
game.ReplicatedStorage.MainEvent:FireServer("Stomp")
end
    end)


local L_17_ = L_4_:NewTab("Players")
local L_18_ = loadstring(game:HttpGet("https://raw.githubusercontent.com/NotPluschi/Esp/main/DashX"))()
local L_19_ = L_17_:NewSection("Selections")
L_19_:NewToggle(
	"ESP",
	"ESP",
	function(L_201_arg0)
		L_18_:Toggle(L_201_arg0)
	end
)
L_19_:NewToggle(
	"Tracers",
	"Tracers",
	function(L_202_arg0)
		L_18_.Tracers = L_202_arg0
	end
)
L_19_:NewToggle(
	"Names",
	"Names",
	function(L_203_arg0)
		L_18_.Names = L_203_arg0
	end
)
L_19_:NewToggle(
	"Boxes",
	"Boxes",
	function(L_204_arg0)
		L_18_.Boxes = L_204_arg0
	end
)
