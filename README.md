-- SETTINGS
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("YUNG HUB | SL2 | UNRELEASED", "Synapse")

--TABS
local Main = Window:NewTab("📂 | Main")
local Player = Window:NewTab("🎮 | Player")
local Combat = Window:NewTab("🔪 | Combat")
local Strategic = Window:NewTab("⚔ | Strategic")
local Other = Window:NewTab("✨ | Other")
local Fun = Window:NewTab("👑 | Fun")
local Teleports = Window:NewTab("🔮 | Teleports")
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
local MainStuff = Strategic:NewSection("Main Stuff")
local Shops = Teleports:NewSection("Shops")

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
Main:NewButton("Fly Bypass", "Fly", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/fk7/main/README.md"))()
end
)

Main:NewButton("Vehicle Fly", "Fly", function()
	local plr = game:GetService("Players").LocalPlayer
	local pos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
	local roundedPos = math.round(pos.X) .. ", " .. math.round(pos.Y) .. ", " .. math.round(pos.Z)

	function bypass()
		if game.Players.LocalPlayer.Character.Humanoid.Sit ~= true then
			rconsoleclear()
			rconsolewarn("Please be seated in any vehicle to inititate Bypass. \n - You can also sit in the passenger seat!")
		end

		if game.Players.LocalPlayer.Character.Humanoid.Sit ~= false then
			workspace[plr.Name .. "'s Car"]:MoveTo(roundedPos)
			workspace[plr.Name .. "'s Car"].DriveSeat:Sit(plr.Character.Humanoid)
		end
	end

	bypass()
	rconsoleclear()
	rconsolewarn("Successful! \n -If anything bugs out after you stop flying type '/respawn'")
end
)

Main:NewButton("WalkSpeed Bypass (40)", "faster", function()
	local plr = game.Players.LocalPlayer
	local char = plr.Character

	char.Humanoid.WalkSpeed = 40
end
)

Main:NewButton("Remove Karma Alert", "Remove The Alert", function()
	while true do
		wait(1)
		game.ReplicatedStorage.KarmaAlert:Destroy()
	end
end
)

Main:NewButton("Remove Damage Blood", "Remove The Blood", function()
	wait(1)
	game.Players.LocalPlayer.PlayerGui.Dmg:Destroy()
end
)




Main:NewButton("Infinite Skittles", "inf skits", function()
	while wait() do
		game:GetService("Players").LocalPlayer.PlayerGui.Run.Value.Value = true
		game.Players.LocalPlayer.Character.Resistance.Value = true
		game:GetService("Workspace").LocalPlayer.Resistance = true
	end
end
)

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
	local g = game.Workspace.tools
	while task.wait() do
		for fk, fl in pairs((g:GetChildren())) do
			if fl:IsA("Tool") then
				if fl:IsA("Tool") and fl.Name == "Phone" or fl.Name == "Crate" then
				else
					game:GetService("Players").LocalPlayer.Character.Humanoid:EquipTool(fl)

				end
			end
		end
	end
end
)

Main:NewButton("Anti Combat Log", "no fine pls", function()
	game:GetService("Players").LocalPlayer.PlayerGui.Stats.CLog:Destroy()
end
)

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

Combat:NewButton("ESP", "See All Players", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/fwfveef/main/README.md"))()
end
)

Main:NewButton("Anti-Ragdoll", "Stop falling over!", function()
	game:GetService("ReplicatedStorage").Modules.RagdollHandler:Destroy()
	game.ReplicatedStorage.RemoteEvents.SetPlayerRagdolled:Destroy()
	game.Workspace.Ragdoller:Destroy()

	while task.wait(1) do 
		if game.Players.LocalPlayer.Character:FindFirstChild("Ragdolled") then
			game.Players.LocalPlayer.Character:FindFirstChild("Ragdolled"):Destroy()
		end 
	end
end
)
	

Main:NewButton("Remove Traffic Sounds", "Removes Traffic Sounds", function()
	game:GetService("SoundService")["Traffic City Noises"]:Destroy()
	print("Clicked")
end)


Main:NewButton("Infinite Stamina", "Never Run Out Of Stamina", function()
	while true do 
		wait(0)
		game.Players.LocalPlayer.Valuestats.Stamina.Value = 100
	end   
end
)

Main:NewButton("Infinite Hunger", "Never Run Out Of Hunger", function()
	while true do 
		wait(0)
		game.Players.LocalPlayer.Valuestats.Hunger.Value = 100
	end  
end
)

Main:NewButton("Anti Camera-Bob", "No Bobbing", function()
	game:GetService("Players").LocalPlayer.PlayerGui.Camera_Bob.Disabled = true
	print("Clicked")
end)

FE:NewButton("Fake Cash", "Never Run Out Of Cash! (FAKE)", function()
	game:GetService("Players").LocalPlayer.Valuestats.Wallet.Value = 100000000000
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
	loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/fdqqqqq/main/README.md"))()
end
)

FE:NewButton("No Legs", "Removes your legs", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/eqqqqq/main/README.md"))()  
end
)

FE:NewButton("No Arms", "Removes your Arms", function()
		game:GetService("Players").LocalPlayer.Character.RightUpperArm:Destroy()
		game:GetService("Players").LocalPlayer.Character.RightLowerArm:Destroy()
		game:GetService("Players").LocalPlayer.Character.LeftUpperArm:Destroy()
		game:GetService("Players").LocalPlayer.Character.LeftLowerArm:Destroy()
	end
)

FE:NewButton("Fire Hands", "Puts Fire On your Hands", function()
		Fire.Parent = game.Players.LocalPlayer.Character.RightHand
	Fire.Heat = 5
	Fire.Size = 2
end
)

FE:NewButton("Call Everyone", "Call Everyone", function()
	local function callAll( )
		for i,v in pairs(Players:GetPlayers( )) do
			if v ~= LocalPlayer then

				local args = {
					[1] = v,
					[2] = "Starting"
				};        

				game:GetService("ReplicatedStorage").Call:FireServer(unpack(args));

				print("called " .. v.Name);
			end;
		end;
	end;
	callAll()
end
)


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
	loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/wqqqq/main/README.md"))()
end
)

FE:NewButton("No Name", "Removes Your face", function()
	oadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/wwdghjhgfds/main/README.md"))()
end
)

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
	game:GetService("Players").BL00DLESE.Valuestats.Karma:Destroy()
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

GameImprovement:NewButton("Anti-Blur", "See All.", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/sdfe3/main/README.md"))()
end
)

GameImprovement:NewButton("Anti-AFK", "Never Be Kicked For Idleness", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/dfefefe/main/README.md"))()
end
)

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

Animations:NewButton("Tons Of Animations", "Dance", function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/Dvrknvss/UniversalFEScriptHub/main/Script'))()
	print("Clicked")
end)

-- strat
MainStuff:NewButton("HitBox v2", "More effective", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/dedefe/main/README.md"))()
end
)

MainStuff:NewButton("Infinite-Clips", "Infinite Clips", function()
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

MainStuff:NewButton("One Tap", "1 Tap", function()
	local meleeRemote = game:GetService("ReplicatedStorage").GunRemotes.Impact;
	local OldNameCall = nil
	OldNameCall = hookmetamethod(game, "__namecall", function(Self, ...)
		local Args = {...}
		local NamecallMethod = getnamecallmethod()

		if not checkcaller() and Self == meleeRemote and NamecallMethod == "FireServer" then
			for i=1, 15, 1 do
				OldNameCall(Self,...);
			end        
		end

		return OldNameCall(Self, ...)
	end)
end
)

MainStuff:NewButton("Infinite-Ammo", "Infinite Ammo", function()
	while task.wait() do
		for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
			if v:IsA("Tool") then
				if v:FindFirstChild("Stats") then
					v.Stats.MaxAmmo.Value = 6969
					v.Stats.MaxAmmo.Original.Value = 6969
				end
			end
		end
	end
	print("Clicked")
end)

MainStuff:NewButton("Monkey Hub Inf-Ammo", "Infinite Ammo", function()
	for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do 
		if v:IsA("Tool") and v:FindFirstChild("Stats") then
			task.spawn(function()
				while task.wait(5) do
					if v.Stats.ClipSize.Value ~= v.Stats.ClipSize.Original.Value then
						v.Stats.ClipSize.Value = math.huge
						v.Stats.ClipSize.Original.Value = math.huge
					end
				end
			end)
		end
	end 
end
)

Main:NewButton("Remove Typing GUI", "Removes Typing GUI", function()
	game:GetService("ReplicatedStorage").Typing2:Destroy()
	print("Clicked")
end)

FE:NewButton("Very Loud Sound", "Abuses Car Sounds", function()
	local args = {
		[1] = workspace:FindFirstChild(game.Players.LocalPlayer.Name .. "'s Car")
	}

	game:GetService("ReplicatedStorage").TireSmoke:FireServer(unpack(args))

	local args = {
		[1] = game.Workspace[game.Players.LocalPlayer.Name .. "'s Car"],
		[2] = 1000,
		[3] = 1000,
		[4] = false,
		[5] = 1000,
		[6] = 1000,
		[7] = 0,
		[8] = 1000,
		[9] = false
	}

	game:GetService("ReplicatedStorage").CarSound:FireServer(unpack(args))
end
)

Shops:NewButton("Sports Shop (JOB)", "TP", function()
	local plr = game.Players.LocalPlayer
	local workspace = game.Workspace
	plr.Character.HumanoidRootPart.CFrame = CFrame.new(-195.589691, -463.662384, 92.2535934, 0.238895774, 2.38148239e-08, 0.971045196, 3.21983293e-08, 1, -3.24463443e-08, -0.971045196, 3.90173298e-08, 0.238895774)
	game:GetService("Workspace")[plr.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)
	task.wait()
	game:GetService("Workspace")[plr.Name.."'s Car"].DriveSeat:sit(plr.Character.Humanoid)
	task.wait()
	game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",workspace:FindFirstChild(plr.Name .. "'s Car"))
end
)

Shops:NewButton("Urban (JOB)", "TP", function()
	local plr = game.Players.LocalPlayer
	local workspace = game.Workspace
	plr.Character.HumanoidRootPart.CFrame = CFrame.new(282, 4.45790863, -157, 1, 6.64652404e-08, -1.07617515e-13, -6.64652404e-08, 1, 7.81934428e-09, 1.08137234e-13, -7.81934428e-09, 1)
	game:GetService("Workspace")[plr.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)
	task.wait()
	game:GetService("Workspace")[plr.Name.."'s Car"].DriveSeat:sit(plr.Character.Humanoid)
	task.wait()
	game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",workspace:FindFirstChild(plr.Name .. "'s Car"))
end
)

Shops:NewButton("Tescos", "TP", function()
	local plr = game.Players.LocalPlayer
	local workspace = game.Workspace
	plr.Character.HumanoidRootPart.CFrame = CFrame.new(983.751831, -446.635803, 103.678848, -0.381174803, -9.88733646e-08, -0.924502969, -2.49378118e-08, 1, -9.66656728e-08, 0.924502969, -1.37914373e-08, -0.381174803)
	game:GetService("Workspace")[plr.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)
	task.wait()
	game:GetService("Workspace")[plr.Name.."'s Car"].DriveSeat:sit(plr.Character.Humanoid)
	task.wait()
	game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",workspace:FindFirstChild(plr.Name .. "'s Car"))
end
)

Shops:NewButton("Barbers", "TP", function()
		local plr = game.Players.LocalPlayer
		local workspace = game.Workspace
		plr.Character.HumanoidRootPart.CFrame = CFrame.new(-21, 4.40000916, 102, 1, -3.14583648e-09, -1.63019792e-14, 3.14583648e-09, 1, 4.40034809e-09, 1.62881369e-14, -4.40034809e-09, 1)
		game:GetService("Workspace")[plr.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)
		task.wait()
		game:GetService("Workspace")[plr.Name.."'s Car"].DriveSeat:sit(plr.Character.Humanoid)
		task.wait()
		game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",workspace:FindFirstChild(plr.Name .. "'s Car"))
	end
	)

Shops:NewButton("Hair Salon", "TP", function()	
	local plr = game.Players.LocalPlayer
	local workspace = game.Workspace
	plr.Character.HumanoidRootPart.CFrame = CFrame.new(-21.0000038, 4.40000916, 120.000015, 1, 3.68644564e-08, -1.16391732e-13, -3.68644564e-08, 1, -5.15691454e-08, 1.14490665e-13, 5.15691454e-08, 1)
	game:GetService("Workspace")[plr.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)
	task.wait()
	game:GetService("Workspace")[plr.Name.."'s Car"].DriveSeat:sit(plr.Character.Humanoid)
	task.wait()
	game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",workspace:FindFirstChild(plr.Name .. "'s Car"))
end
)

