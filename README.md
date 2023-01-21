-- SETTINGS
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("YUNG HUB | SL2 | UNRELEASED", "Synapse")

--TABS
local Player = Window:NewTab("🎮 | Player")
local Main = Window:NewTab("📂 | Main")
local Combat = Window:NewTab("🔪 | Combat")
local Other = Window:NewTab("✨ | Other")
local Fun = Window:NewTab("👑 | Fun")
local Creditss = Window:NewTab("🔨 | Credits")

--SECTIONS
local FE = Fun:NewSection("FE")
local Utilities = Player:NewSection("Utilities")
local Animations = Fun:NewSection("Animations")
local AdminCommands = Fun:NewSection("Admin Commands")
local GameImprovement = Player:NewSection("Game Improvement")
local Combat = Combat:NewSection("Comabat")
local Main = Main:NewSection("Main")
local StupidShit = Other:NewSection("Random")
local Credits = Creditss:NewSection("Main Scripter | Aqua")

Credits:NewButton("YUNG HUB Discord Server", "Dizzy", function()
	setclipboard("https://discord.gg/vMSPnKtEtB")
	print("Clicked")
end)

local Helper = Creditss:NewSection("Helper | SheppozZ")

Helper:NewButton("Discord Server", "Dizzy", function()
	setclipboard("https://discord.gg/vMSPnKtEtB")
	print("Clicked")
end)

local scripthelper = Creditss:NewSection("Script Helper | xurel#7777")
scripthelper:NewButton("Solar Hub Discord Server", "Dizzy", function()
	setclipboard("https://discord.gg/7ZyTx6Zf3n")
	print("Clicked")
end)
-- SLIDERS 
Utilities:NewSlider("WalkSpeed", "Run Fast!", 60, 17, function(s) -- 60 (MaxValue) | 16 (MinValue)
	game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)

Utilities:NewSlider("JumpPower", "Jump Higher", 3, 70, function(s) -- 60 (MaxValue) | 16 (MinValue)
	game.Players.LocalPlayer.Character.Humanoid.JumpPower = s
end)

-- BUTTONS
GameImprovement:NewButton("Full-Bright", "Brightens Up The Game", function()
	local Light = game:GetService("Lighting")

	function dofullbright()
		Light.Ambient = Color3.new(1, 1, 1)
		Light.ColorShift_Bottom = Color3.new(1, 1, 1)
		Light.ColorShift_Top = Color3.new(1, 1, 1)
	end

	dofullbright()

	Light.LightingChanged:Connect(dofullbright)
	print("Clicked")
end)

Combat:NewButton("Hit-box", "Make Heads Bigger!, thanks solar hub", function()
	local size = 5
local transparency = 0.7
local material = 'Neon'
local brickcolor = 'Really blue'
getgenv(l).disabled = false


repeat task.wait(5)
    for i, v in pairs(game.Players:GetPlayers()) do
        local character = v.Character
        if character and v.Name ~= game.Players.LocalPlayer.Name then
            character.Head.Size = Vector3.new(size,size,size)
            character.Head.Transparency = transparency
            character.Head.Material = material
            character.Head.BrickColor = BrickColor.new(brickcolor)
            character.Head.CanCollide = false
        end
    end
until getgenv(l).disabled == true
	print("Clicked")
end)

Main:NewButton("Auto-Pickup", "Pickup All Dropped Guns", function()
	local LP = game.Players.LocalPlayer
	while game.RunService.Heartbeat:Wait() do
		local success, err = pcall(function()
			for i,v in pairs(workspace:GetChildren()) do
				if v:IsA("Tool") and v.Name ~= "Unusual Arrow" and v.Name ~= "Rokakaka" and v.Name ~= "Frog" and v.Name ~= "Jotaro Hat" and v.Name ~= "Unbelievable Arrow"then
					firetouchinterest(LP.Character.HumanoidRootPart,v.Handle,0)
				end
			end
		end)
	end
	print("Clicked")
end)

Main:NewButton("Chat-Spy", "See all messages!", function()
	--chat "/spy" to toggle!
	enabled = true
	--if true will check your messages too
	spyOnMyself = true
	--if true will chat the logs publicly (fun, risky)
	public = false
	--if true will use /me to stand out
	publicItalics = true
	--customize private logs
	privateProperties = {
		Color = Color3.fromRGB(0,255,255); 
		Font = Enum.Font.SourceSansBold;
		TextSize = 18;
	}
	--////////////////////////////////////////////////////////////////
	local StarterGui = game:GetService("StarterGui")
	local Players = game:GetService("Players")
	local player = Players.LocalPlayer
	local saymsg = game:GetService("ReplicatedStorage"):WaitForChild("DefaultChatSystemChatEvents"):WaitForChild("SayMessageRequest")
	local getmsg = game:GetService("ReplicatedStorage"):WaitForChild("DefaultChatSystemChatEvents"):WaitForChild("OnMessageDoneFiltering")
	local instance = (_G.chatSpyInstance or 0) + 1
	_G.chatSpyInstance = instance

	local function onChatted(p,msg)
		if _G.chatSpyInstance == instance then
			if p==player and msg:lower():sub(1,4)=="/spy" then
				enabled = not enabled
				wait(0.3)
				privateProperties.Text = "{SPY "..(enabled and "EN" or "DIS").."ABLED}"
				StarterGui:SetCore("ChatMakeSystemMessage",privateProperties)
			elseif enabled and (spyOnMyself==true or p~=player) then
				msg = msg:gsub("[\n\r]",''):gsub("\t",' '):gsub("[ ]+",' ')
				local hidden = true
				local conn = getmsg.OnClientEvent:Connect(function(packet,channel)
					if packet.SpeakerUserId==p.UserId and packet.Message==msg:sub(#msg-#packet.Message+1) and (channel=="All" or (channel=="Team" and public==false and Players[packet.FromSpeaker].Team==player.Team)) then
						hidden = false
					end
				end)
				wait(1)
				conn:Disconnect()
				if hidden and enabled then
					if public then
						saymsg:FireServer((publicItalics and "/me " or '').."{SPY} [".. p.Name .."]: "..msg,"All")
					else
						privateProperties.Text = "{SPY} [".. p.Name .."]: "..msg
						StarterGui:SetCore("ChatMakeSystemMessage",privateProperties)
					end
				end
			end
		end
	end

	for _,p in ipairs(Players:GetPlayers()) do
		p.Chatted:Connect(function(msg) onChatted(p,msg) end)
	end
	Players.PlayerAdded:Connect(function(p)
		p.Chatted:Connect(function(msg) onChatted(p,msg) end)
	end)
	privateProperties.Text = "{SPY "..(enabled and "EN" or "DIS").."ABLED}"
	StarterGui:SetCore("ChatMakeSystemMessage",privateProperties)
	local chatFrame = player.PlayerGui.Chat.Frame
	chatFrame.ChatChannelParentFrame.Visible = true
	chatFrame.ChatBarParentFrame.Position = chatFrame.ChatChannelParentFrame.Position+UDim2.new(UDim.new(),chatFrame.ChatChannelParentFrame.Size.Y)
	print("Clicked")
end)

Combat:NewButton("Infinite-Ammo", "Infinite Ammo", function()
	while task.wait() do
for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
    if v:IsA("Tool") then
    if v:FindFirstChild("Stats") then
        v.Stats.ClipSize.Value = 6969
        v.Stats.ClipSize.Original.Value = 6969
    end
    end
end
end
	print("Clicked")
end)

Combat:NewButton("ESP", "See All Players", function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/fatesc/fates-esp/main/main.lua'))()
	print("Clicked")
end)

Main:NewButton("Anti-Ragdoll", "Stop falling over!", function()
	game:GetService("Players").LocalPlayer.PlayerGui.SETRAGDOLL.Disabled = true
	print("Clicked")
end)


Main:NewButton("Infinite Stamina", "Never Run Out Of Stamina", function()
	game:GetService("Players").LocalPlayer.Valuestats.Stamina.Value = 100000000000
	print("Clicked")
end)

Main:NewButton("Infinite Hunger", "Never Run Out Of Hunger", function()
	game:GetService("Players").LocalPlayer.Valuestats.Hunger.Value = 100000000000
	print("Clicked")
end)

Main:NewButton("Anti Camera-Bob", "No Bobbing", function()
	game:GetService("Players").LocalPlayer.PlayerGui.Camera_Bob.Disabled = true
	print("Clicked")
end)

FE:NewButton("Fake Cash", "Never Run Out Of Cash! (FAKE)", function()
	game:GetService("Players").LocalPlayer.Valuestats.Wallet.Value = 100000000000
	print("Clicked")
end)

Combat:NewButton("Aimbot", "Never Miss A Shot", function()
	local dwCamera = workspace.CurrentCamera
	local dwRunService = game:GetService("RunService")
	local dwUIS = game:GetService("UserInputService")
	local dwEntities = game:GetService("Players")
	local dwLocalPlayer = dwEntities.LocalPlayer
	local dwMouse = dwLocalPlayer:GetMouse()

	local settings = {
		Aimbot = true,
		Aiming = false,
		Aimbot_AimPart = "Head",
		Aimbot_TeamCheck = false,
		Aimbot_Draw_FOV = true,
		Aimbot_FOV_Radius = 50,
		Aimbot_FOV_Color = Color3.fromRGB(255,255,255)
	}

	local fovcircle = Drawing.new("Circle")
	fovcircle.Visible = settings.Aimbot_Draw_FOV
	fovcircle.Radius = settings.Aimbot_FOV_Radius
	fovcircle.Color = settings.Aimbot_FOV_Color
	fovcircle.Thickness = 1
	fovcircle.Filled = false
	fovcircle.Transparency = 1

	fovcircle.Position = Vector2.new(dwCamera.ViewportSize.X / 2, dwCamera.ViewportSize.Y / 2)

	dwUIS.InputBegan:Connect(function(i)
		if i.UserInputType == Enum.UserInputType.MouseButton2 then
			settings.Aiming = true
		end
	end)

	dwUIS.InputEnded:Connect(function(i)
		if i.UserInputType == Enum.UserInputType.MouseButton2 then
			settings.Aiming = false
		end
	end)

	dwRunService.RenderStepped:Connect(function()

		local dist = math.huge
		local closest_char = nil

		if settings.Aiming then

			for i,v in next, dwEntities:GetChildren() do 

				if v ~= dwLocalPlayer and
					v.Character and
					v.Character:FindFirstChild("HumanoidRootPart") and
					v.Character:FindFirstChild("Humanoid") and
					v.Character:FindFirstChild("Humanoid").Health > 0 then

					if settings.Aimbot_TeamCheck == true and
						v.Team ~= dwLocalPlayer.Team or
						settings.Aimbot_TeamCheck == false then

						local char = v.Character
						local char_part_pos, is_onscreen = dwCamera:WorldToViewportPoint(char[settings.Aimbot_AimPart].Position)

						if is_onscreen then

							local mag = (Vector2.new(dwMouse.X, dwMouse.Y) - Vector2.new(char_part_pos.X, char_part_pos.Y)).Magnitude

							if mag < dist and mag < settings.Aimbot_FOV_Radius then

								dist = mag
								closest_char = char

							end
						end
					end
				end
			end

			if closest_char ~= nil and
				closest_char:FindFirstChild("HumanoidRootPart") and
				closest_char:FindFirstChild("Humanoid") and
				closest_char:FindFirstChild("Humanoid").Health > 0 then

				dwCamera.CFrame = CFrame.new(dwCamera.CFrame.Position, closest_char[settings.Aimbot_AimPart].Position)
			end
		end
	end)	
	print("Clicked")
end)

GameImprovement:NewButton("Anti-Lag", "Removes Lag", function()
	local decalsyeeted = true -- Leaving this on makes games look shitty but the fps goes up by at least 20.
	local g = game
	local w = g.Workspace
	local l = g.Lighting
	local t = w.Terrain
	t.WaterWaveSize = 0
	t.WaterWaveSpeed = 0
	t.WaterReflectance = 0
	t.WaterTransparency = 0
	l.GlobalShadows = false
	l.FogEnd = 9e9
	l.Brightness = 0
	settings().Rendering.QualityLevel = "Level01"
	for i, v in pairs(g:GetDescendants()) do
		if v:IsA("Part") or v:IsA("Union") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then
			v.Material = "Plastic"
			v.Reflectance = 0
		elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then
			v.Transparency = 1
		elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
			v.Lifetime = NumberRange.new(0)
		elseif v:IsA("Explosion") then
			v.BlastPressure = 1
			v.BlastRadius = 1
		elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") then
			v.Enabled = false
		elseif v:IsA("MeshPart") then
			v.Material = "Plastic"
			v.Reflectance = 0
			v.TextureID = 10385902758728957
		end
	end
	for i, e in pairs(l:GetChildren()) do
		if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
			e.Enabled = false
		end
	end
	print("Clicked")
end)

FE:NewButton("No Head", "Removes your head", function()
	-- services
	local players = game:GetService("Players")
	local starterGui = game:GetService("StarterGui")
	-- objects
	local player = players.LocalPlayer
	local character = player.Character
	local humanoid = character:FindFirstChildWhichIsA("Humanoid")
	local head, torso = character:FindFirstChild("Head"), character:FindFirstChild("UpperTorso")
	local resetBindable = Instance.new("BindableEvent")
	-- variables
	local destroyFunc, resetBindableConnection = character.Destroy, nil
	-- main
	-- initializes the permadeath
	player.Character = nil
	player.Character = character
	task.wait(players.RespawnTime + .05)

	humanoid.BreakJointsOnDeath = false
	humanoid:SetStateEnabled(Enum.HumanoidStateType.Dead, false)
	if humanoid.RigType == Enum.HumanoidRigType.R15 then
		task.defer(destroyFunc, (head.Neck))
	end
	task.defer(destroyFunc, head) -- and we destroy the head

	resetBindableConnection = resetBindable.Event:Connect(function()
		starterGui:SetCore("ResetButtonCallback", true)
		resetBindableConnection:Disconnect()

		if player.Character == character then
			character:Destroy()
			local daModel = Instance.new("Model")
			local _daModelHumanoid = Instance.new("Humanoid")
			_daModelHumanoid.Parent = daModel
			player.Character = daModel

			task.delay(players.RespawnTime, destroyFunc, daModel)
		else
			player.Character:BreakJoints()
		end
	end)
	starterGui:SetCore("ResetButtonCallback", resetBindable)
	print("Clicked")
end)

AdminCommands:NewButton("Infinite Yield", "FE ADMIN", function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
	print("Clicked")
end)

StupidShit:NewButton("Auto Disconnect", "Leave The Game", function()
	_G.Enabled = true;

	_G.CertainPlayer = false; --Set to false if you want it to kick you if anyone joins and true if you want to use playerlist

	_G.Kick = true; --If it kicks you or just gives a notification that someone joined

	playerlist = {"Name1","Name2","Name3","Name4"} -- Just add more if you want too
	--------------------------------------------------------------------------------------SCRIPT
	if(_G.Enabled == true) then

		game:GetService("Players").PlayerAdded:Connect(function(user)
			local Time = os.date("*t")

			if(_G.CertainPlayer == false) then
				if (_G.Kick == true) then
					game.Players.LocalPlayer:Kick("A player joined: "..user.Name.." ,at: "..Time.hour..":"..Time.min)
				end
				if(_G.Kick == false) then
					print(user.name.." Joined your game at ".." ,at: "..Time.hour..":"..Time.min.." and Wrote PlayersJoined.txt file in workspace/AutoDisconnect")
					game.StarterGui:SetCore("SendNotification", {
						Title = user.name.." Joined!";
						Text = "At "..Time.hour..":"..Time.min.." and wrote PlayersJoined.txt in workspace/AutoDisconnect folder";
						Duration = 5;
					})

					makefolder("AutoDisconnect")
					writefile("AutoDisconnect\\PlayerJoined.txt",
						user.name.." joined at "..Time.hour..":"..Time.min
					)

				end
				if(_G.Kick == true) then
					game.Players.LocalPlayer:Kick("A player joined: "..user.Name.." ,at: "..Time.hour..":"..Time.min)
				end
			end



			if(_G.CertainPlayer == true) then

				for i = 1, #playerlist do

					if(user.Name == playerlist[i]) then
						if(_G.Kick == true) then
							game.Players.LocalPlayer:Kick("A player from the playerlist joined: "..playerlist[i].." ,at: "..Time.hour..":"..Time.min)
						end

						if(_G.Kick == false) then
							print(playerlist[i].." from playerlist Joined your game at ".." ,at: "..Time.hour..":"..Time.min.." and Wrote PlayersJoinedLIST.txt file in workspace/AutoDisconnect")
							game.StarterGui:SetCore("SendNotification", {
								Title = playerlist[i].." Joined!";
								Text = "At "..Time.hour..":"..Time.min.." and wrote PlayersJoinedLIST.txt in workspace/AutoDisconnect folder";
								Duration = 5;
							})    
							makefolder("AutoDisconnect")
							writefile("AutoDisconnect\\PlayerJoinedLIST.txt",
								playerlist[i].." from playerlist joined at "..Time.hour..":"..Time.min
							)
						end
					end
				end
			end
		end)
	end
	print("Clicked")
end)

StupidShit:NewButton("Chat Hacks", "Enables Chat Hacks", function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/ant-7802/--/main/straightmilk.lua'))()
	print("Clicked")
end)

StupidShit:NewButton("Grammerly", "ik some of u need this", function()
	loadstring(game:HttpGet("https://capybaras.wtf/chat/grammar.lua"))()
	print("Clicked")
end)

Main:NewButton("Anti-Fling", "fuck off hackers", function()
	local Services = setmetatable({}, {__index = function(Self, Index)
		local NewService = game.GetService(game, Index)
		if NewService then
			Self[Index] = NewService
		end
		return NewService
	end})

	-- [ LocalPlayer ] --
	local LocalPlayer = Services.Players.LocalPlayer

	-- // Functions \\ --
	local function PlayerAdded(Player)
		local Detected = false
		local Character;
		local PrimaryPart;

		local function CharacterAdded(NewCharacter)
			Character = NewCharacter
			repeat
				wait()
				PrimaryPart = NewCharacter:FindFirstChild("HumanoidRootPart")
			until PrimaryPart
			Detected = false
		end

		CharacterAdded(Player.Character or Player.CharacterAdded:Wait())
		Player.CharacterAdded:Connect(CharacterAdded)
		Services.RunService.Heartbeat:Connect(function()
			if (Character and Character:IsDescendantOf(workspace)) and (PrimaryPart and PrimaryPart:IsDescendantOf(Character)) then
				if PrimaryPart.AssemblyAngularVelocity.Magnitude > 50 or PrimaryPart.AssemblyLinearVelocity.Magnitude > 100 then
					if Detected == false then
						game.StarterGui:SetCore("ChatMakeSystemMessage", {
							Text = "Fling Exploit detected, Player: " .. tostring(Player);
							Color = Color3.fromRGB(255, 200, 0);
						})
					end
					Detected = true
					for i,v in ipairs(Character:GetDescendants()) do
						if v:IsA("BasePart") then
							v.CanCollide = false
							v.AssemblyAngularVelocity = Vector3.new(0, 0, 0)
							v.AssemblyLinearVelocity = Vector3.new(0, 0, 0)
							v.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0)
						end
					end
					PrimaryPart.CanCollide = false
					PrimaryPart.AssemblyAngularVelocity = Vector3.new(0, 0, 0)
					PrimaryPart.AssemblyLinearVelocity = Vector3.new(0, 0, 0)
					PrimaryPart.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0)
				end
			end
		end)
	end

	-- // Event Listeners \\ --
	for i,v in ipairs(Services.Players:GetPlayers()) do
		if v ~= LocalPlayer then
			PlayerAdded(v)
		end
	end
	Services.Players.PlayerAdded:Connect(PlayerAdded)

	local LastPosition = nil
	Services.RunService.Heartbeat:Connect(function()
		pcall(function()
			local PrimaryPart = LocalPlayer.Character.PrimaryPart
			if PrimaryPart.AssemblyLinearVelocity.Magnitude > 250 or PrimaryPart.AssemblyAngularVelocity.Magnitude > 250 then
				PrimaryPart.AssemblyAngularVelocity = Vector3.new(0, 0, 0)
				PrimaryPart.AssemblyLinearVelocity = Vector3.new(0, 0, 0)
				PrimaryPart.CFrame = LastPosition

				game.StarterGui:SetCore("ChatMakeSystemMessage", {
					Text = "You were flung. Neutralizing velocity.";
					Color = Color3.fromRGB(255, 0, 0);
				})
			elseif PrimaryPart.AssemblyLinearVelocity.Magnitude < 50 or PrimaryPart.AssemblyAngularVelocity.Magnitude > 50 then
				LastPosition = PrimaryPart.CFrame
			end
		end)
	end)
	print("Clicked")
end)

FE:NewButton("No Face", "Removes Your face", function()
	game.Players.LocalPlayer.Valuestats.face:Destroy()
	print("Clicked")
end)

Main:NewButton("Infinite Car Gas", "Gas", function()
	game:GetService("Players").LocalPlayer.Valuestats.CarGas.Value = 100000000000
	print("Clicked")
end)

Main:NewButton("Remove Ticket", "REMOVE TICKET", function()
	game:GetService("StarterGui").Ticket.Enabled = false
	print("Clicked")
end)

Main:NewButton("Remove Weather", "Remove Weather", function()
	game:GetService("StarterPlayer").StarterPlayerScripts.Weather.Disabled = true
	print("Clicked")
end)

Main:NewButton("Infinite Karma", "karma", function()
	game:GetService("Players").LocalPlayer.Valuestats.Karma.Value = 100000000000
	print("Clicked")
end)

FE:NewButton("Naked", "Makes You Naked", function()
	for i, clothes in pairs(game:GetService('Players').LocalPlayer.Character:GetChildren()) do
		if clothes:IsA("Shirt") then
			clothes:Destroy();
		elseif clothes:IsA("Pants") then
			clothes:Destroy();
		elseif clothes:IsA("Accessory") then
			if clothes.Name == "HOODOWN" then
				clothes:Destroy();
			elseif clothes.Name == "HOOD" then
				clothes:Destroy();
			elseif clothes.Name == "HOODHAIR" then
				clothes:Destroy();

			end
		end
	end;
	print("Clicked")
end)

Combat:NewButton("Melee Kill Aura", "Melee Kill Aura", function()
	--// Setting \\--
	local range = 22

	--// Variable \\--
	local player = game:GetService("Players").LocalPlayer

	--// Script \\--
	game:GetService("RunService").RenderStepped:Connect(function()
		local p = game.Players:GetPlayers()
		for i = 2, #p do local v = p[i].Character
			if v and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and v:FindFirstChild("HumanoidRootPart") and player:DistanceFromCharacter(v.HumanoidRootPart.Position) <= range then
				local tool = player.Character and player.Character:FindFirstChildOfClass("Tool")
				if tool and tool:FindFirstChild("Handle") then
					tool:Activate()
					for i,v in next, v:GetChildren() do
						if v:IsA("BasePart") then
							firetouchinterest(tool.Handle,v,0)
							firetouchinterest(tool.Handle,v,1)
						end
					end
				end
			end
		end
	end)
	print("Clicked")
end)

GameImprovement:NewButton("Insane Graphics", "Enhances Graphics", function()
	print("Clicked")
end)

Combat:NewButton("Noclip (v)", "Walk Through Walls", function()
	local StealthMode = true 

	local Indicator

	if not StealthMode then
		local ScreenGui = Instance.new("ScreenGui", game.CoreGui)
		Indicator = Instance.new("TextLabel", ScreenGui)
		Indicator.AnchorPoint = Vector2.new(0, 1)
		Indicator.Position = UDim2.new(0, 0, 1, 0)
		Indicator.Size = UDim2.new(0, 200, 0, 50)
		Indicator.BackgroundTransparency = 1
		Indicator.TextScaled = true
		Indicator.TextStrokeTransparency = 0
		Indicator.TextColor3 = Color3.new(0, 0, 0)
		Indicator.TextStrokeColor3 = Color3.new(1, 1, 1)
		Indicator.Text = "Noclip: Enabled"
	end

	local noclip = false
	local player = game.Players.LocalPlayer
	local character = player.Character or player.CharacterAdded:Wait()

	local mouse = player:GetMouse()

	mouse.KeyDown:Connect(function(key)
		if key == "v" then
			noclip = not noclip

			if not StealthMode then
				Indicator.Text = "Noclip: " .. (noclip and "Enabled" or "Disabled")
			end
		end
	end)

	while true do
		player = game.Players.LocalPlayer
		character = player.Character

		if noclip then
			for _, v in pairs(character:GetDescendants()) do
				pcall(function()
					if v:IsA("BasePart") then
						v.CanCollide = false
					end
				end)
			end
		end

		game:GetService("RunService").Stepped:wait()
	end
	print("Clicked")
end)

Animations:NewButton("Krystal Dance", "Do The Krystal Dance", function()
	loadstring(game:HttpGet('https://gist.githubusercontent.com/1BlueCat/e51327540d1ba5ede244c459dbdb5a0e/raw/6320fe344ac51a311ef7c9f8d5c3924b1a7c3969/Krystal%2520Dance'))()
	print("Clicked")
end)

Animations:NewButton("Tons Of Animations", "Dance", function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/Dvrknvss/UniversalFEScriptHub/main/Script'))()
	print("Clicked")
end)

AdminCommands:NewButton("Reviz Admin", "reviz what a guy", function()
	loadstring(game:HttpGet(('https://pastebin.com/raw/pyzjWNhk'),true))()
	print("Clicked")
end)
