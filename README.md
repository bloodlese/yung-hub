local bb=loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local cb=bb:MakeWindow({Name="YungHub Premium | SL2 Edition",HidePremium=false,SaveConfig=true,ConfigFolder="OrionTest",IntroEnabled=true,IntroText="Welcome To YungHub Premium | SL2",IntroIcon="rbxassetid://8387311864"})
bb:MakeNotification({Name="We Appreciate It! - Aqua & SheppozZ",Content="Hi! we just wanted to thank you for purchasing YungHub, Have fun hacking, the easy way.",Image="rbxassetid://11982227421",Time=10})
local db=cb:MakeTab({Name="Player",Icon="rbxassetid://11322093465",PremiumOnly=false})local _c=db:AddSection({Name="MAIN"})
db:AddButton({Name="Fly Bypass",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/fk7/main/README.md"))()print("button pressed")end})
db:AddButton({Name="Walk-Speed Bypass",Callback=function()local cd=game.Players.LocalPlayer;local dd=cd.Character
dd.Humanoid.WalkSpeed=40;print("button pressed")end})
db:AddButton({Name="Auto Pickup Items",Callback=function()local cd=game.Workspace.tools
while task.wait()do
for dd,__a in
pairs((cd:GetChildren()))do
if __a:IsA("Tool")then if __a:IsA("Tool")and __a.Name=="Phone"or __a.Name==
"Crate"then else
game:GetService("Players").LocalPlayer.Character.Humanoid:EquipTool(__a)end end end end;print("button pressed")end})
db:AddButton({Name="Infinite Skittles",Callback=function()
while wait()do
game:GetService("Players").LocalPlayer.PlayerGui.Run.Value.Value=true
game.Players.LocalPlayer.Character.Resistance.Value=true
game:GetService("Workspace").LocalPlayer.Resistance=true end;print("button pressed")end})
db:AddButton({Name="Infinite Karma",Callback=function()
game:GetService("Players").LocalPlayer.Valuestats.Karma:Destroy()print("Karma Removed.")end})
db:AddButton({Name="Infinite Stamina",Callback=function()while true do wait(0)
game.Players.LocalPlayer.Valuestats.Stamina.Value=100 end;print("button pressed")end})
db:AddButton({Name="Infinite Hunger",Callback=function()while true do wait(0)
game.Players.LocalPlayer.Valuestats.Hunger.Value=100 end;print("button pressed")end})
db:AddButton({Name="Infinite Car Gas",Callback=function()
game:GetService("Players").LocalPlayer.Valuestats.CarGas.Value=100000000000;print("button pressed")end})
db:AddButton({Name="Chat Spy",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/defefef/main/README.md"))()print("button pressed")end})
db:AddButton({Name="ESP",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/fwfveef/main/README.md"))()print("see everyone")end})
db:AddButton({Name="Noclip (V)",Callback=function()local cd=true;local dd
if not cd then
local d_a=Instance.new("ScreenGui",game.CoreGui)dd=Instance.new("TextLabel",d_a)
dd.AnchorPoint=Vector2.new(0,1)dd.Position=UDim2.new(0,0,1,0)
dd.Size=UDim2.new(0,200,0,50)dd.BackgroundTransparency=1;dd.TextScaled=true;dd.TextStrokeTransparency=0
dd.TextColor3=Color3.new(0,0,0)dd.TextStrokeColor3=Color3.new(1,1,1)dd.Text="Noclip: Enabled"end;local __a=false;local a_a=game.Players.LocalPlayer;local b_a=a_a.Character or
a_a.CharacterAdded:Wait()local c_a=a_a:GetMouse()
c_a.KeyDown:Connect(function(d_a)
if
d_a=="v"then __a=not __a;if not cd then
dd.Text="Noclip: ".. (__a and"Enabled"or"Disabled")end end end)
while true do a_a=game.Players.LocalPlayer;b_a=a_a.Character
if __a then for d_a,_aa in
pairs(b_a:GetDescendants())do
pcall(function()if _aa:IsA("BasePart")then _aa.CanCollide=false end end)end end
game:GetService("RunService").Stepped:wait()end;print("button pressed")end})
db:AddButton({Name="Anti-Ragdoll",Callback=function()
game:GetService("ReplicatedStorage").Modules.RagdollHandler:Destroy()
game.ReplicatedStorage.RemoteEvents.SetPlayerRagdolled:Destroy()game.Workspace.Ragdoller:Destroy()
while
task.wait(1)do if
game.Players.LocalPlayer.Character:FindFirstChild("Ragdolled")then
game.Players.LocalPlayer.Character:FindFirstChild("Ragdolled"):Destroy()end end;print("button pressed.")end})
db:AddButton({Name="Anti-CameraBob",Callback=function()
game:GetService("Players").LocalPlayer.PlayerGui.Camera_Bob.Disabled=true;print("button pressed")end})
db:AddButton({Name="Remove Traffic City Noises",Callback=function()
game:GetService("SoundService")["Traffic City Noises"]:Destroy()print("button pressed")end})
db:AddButton({Name="Remove Typing Gui",Callback=function()
game:GetService("ReplicatedStorage").Typing2:Destroy()print("button pressed.")end})
db:AddButton({Name="Remove Damage Blood",Callback=function()wait(1)
game.Players.LocalPlayer.PlayerGui.Dmg:Destroy()print("button pressed.")end})
db:AddButton({Name="Remove Karma Alert",Callback=function()wait(1)while true do wait(1)
game.ReplicatedStorage.KarmaAlert:Destroy()end;print("button pressed.")end})
db:AddButton({Name="Anti-Blur",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/sdfe3/main/README.md"))()print("button pressed")end})
db:AddButton({Name="Anti-AFK",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/dfefefe/main/README.md"))()print("button pressed")end})
local ac=cb:MakeTab({Name="Combat",Icon="rbxassetid://4565811487",PremiumOnly=false})
local bc=ac:AddSection({Name="Battle Improvement"})
ac:AddButton({Name="HitBox",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/dedefe/main/README.md"))()print("button pressed")end})
ac:AddButton({Name="One Hit",Callback=function()
local cd=game:GetService("ReplicatedStorage").GunRemotes.Impact;local dd=nil
dd=hookmetamethod(game,"__namecall",function(__a,...)local a_a={...}local b_a=getnamecallmethod()if not
checkcaller()and __a==cd and b_a=="FireServer"then for i=1,15,1 do
dd(__a,...)end end
return dd(__a,...)end)print("button pressed")end})
ac:AddButton({Name="Full-Bright",Callback=function()local cd=game:GetService("Lighting")function dofullbright()
cd.Ambient=Color3.new(1,1,1)cd.ColorShift_Bottom=Color3.new(1,1,1)
cd.ColorShift_Top=Color3.new(1,1,1)end
dofullbright()cd.LightingChanged:Connect(dofullbright)
print("button pressed")end})
ac:AddButton({Name="Infinite Clips",Callback=function()
while task.wait()do
for cd,dd in
pairs(game.Players.LocalPlayer.Character:GetChildren())do if dd:IsA("Tool")then
if dd:FindFirstChild("Stats")then
dd.Stats.ClipSize.Value=9999;dd.Stats.ClipSize.Original.Value=9999 end end end end;print("button pressed")end})
ac:AddButton({Name="Infinite Ammo",Callback=function()
while task.wait()do
for cd,dd in
pairs(game.Players.LocalPlayer.Character:GetChildren())do if dd:IsA("Tool")then
if dd:FindFirstChild("Stats")then
dd.Stats.MaxAmmo.Value=9999;dd.Stats.MaxAmmo.Original.Value=9999 end end end end;print("button pressed")end})
ac:AddButton({Name="MonkeyHub Infinite-Ammo",Callback=function()
for cd,dd in
pairs(game.Players.LocalPlayer.Character:GetChildren())do
if dd:IsA("Tool")and dd:FindFirstChild("Stats")then
task.spawn(function()
while
task.wait(2)do if
dd.Stats.ClipSize.Value~=dd.Stats.ClipSize.Original.Value then dd.Stats.ClipSize.Value=math.huge
dd.Stats.ClipSize.Original.Value=math.huge end end end)end end;print("button pressed")end})
local cc=cb:MakeTab({Name=" Vehicle Teleports",Icon="rbxassetid://8177115475",PremiumOnly=false})
cc:AddButton({Name="Bring Car",Callback=function()
local cd=game:GetService("Players").LocalPlayer
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait(.1)
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)print("button pressed")end})
cc:AddButton({Name="Sports Shop",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(
-195.589691,-463.662384,92.2535934,0.238895774,2.38148239e-08,0.971045196,3.21983293e-08,1,-3.24463443e-08,-0.971045196,3.90173298e-08,0.238895774)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Urban",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(282,4.45790863,
-157,1,6.64652404e-08,-1.07617515e-13,-6.64652404e-08,1,7.81934428e-09,1.08137234e-13,-7.81934428e-09,1)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Police Station",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace;cd.Character.HumanoidRootPart.CFrame=CFrame.new(
-207,6,-211,1,0,0,0,1,0,0,0,1)
game:GetService("Workspace")[
cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Banks Boxing",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(
-190,4.40000916,168,1,-9.0672172e-09,2.15987354e-14,9.0672172e-09,1,-5.94992215e-08,-2.10592431e-14,5.94992215e-08,1)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Tescos",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(983.751831,
-446.635803,103.678848,-0.381174803,-9.88733646e-08,-0.924502969,-2.49378118e-08,1,-
9.66656728e-08,0.924502969,-1.37914373e-08,-0.381174803)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Barbers",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(
-21,4.40000916,102,1,-3.14583648e-09,-1.63019792e-14,3.14583648e-09,1,4.40034809e-09,1.62881369e-14,-4.40034809e-09,1)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Hair Salon",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(
-21.0000038,4.40000916,120.000015,1,3.68644564e-08,-1.16391732e-13,-3.68644564e-08,1,-5.15691454e-08,1.14490665e-13,5.15691454e-08,1)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Dealer Ship",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(
-93.9999847,4.15790749,542,1,-1.20612453e-08,-2.38422726e-13,1.20612453e-08,1,1.68743792e-08,2.38219221e-13,-
1.68743792e-08,1)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Ultimate Drip",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(479.154602,
-395.400482,-91.1273499,0.216078922,1.49673074e-08,0.976375878,-1.26980304e-09,1,-1.50484354e-08,-0.976375878,2.01184469e-09,0.216078922)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="New London",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(612.033203,
-400.384491,-106.705254,-0.0193231795,-7.59797825e-09,0.999813318,1.18716381e-09,1,7.62234187e-09,-0.999813318,1.33423006e-09,
-0.0193231795)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Face Lift",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(281,4.45790815,
-188,1,-6.91100155e-09,2.24737441e-14,6.91100155e-09,1,-7.69573294e-10,-2.24684248e-14,7.69573294e-10,1)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Maruna Resteraunt",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(
-21,4.40000916,209,1,3.79887801e-08,-2.18802942e-14,-3.79887801e-08,1,-5.31432249e-08,1.98614488e-14,5.31432249e-08,1)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="Quiz Clothing",Callback=function()local cd=game.Players.LocalPlayer;local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(
-20,4.45790815,-52.0000076,1,-2.40221443e-09,-2.3818412e-13,2.40221443e-09,1,3.36058181e-09,2.38176042e-13,-
3.36058181e-09,1)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
cc:AddButton({Name="School (KAI DONT CLICK)",Callback=function()local cd=game.Players.LocalPlayer
local dd=game.Workspace
cd.Character.HumanoidRootPart.CFrame=CFrame.new(612.033203,-400.384491,-106.705254,-
0.0193231795,-7.59797825e-09,0.999813318,1.18716381e-09,1,7.62234187e-09,-0.999813318,1.33423006e-09,-0.0193231795)
game:GetService("Workspace")[cd.Name.."'s Car"]:MoveTo(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)task.wait()
game:GetService("Workspace")[cd.Name.."'s Car"].DriveSeat:sit(cd.Character.Humanoid)task.wait()
game:GetService("ReplicatedStorage").DoorService:FireServer("HOP",dd:FindFirstChild(
cd.Name.."'s Car"))print("button pressed")end})
local dc=cb:MakeTab({Name="Fun",Icon="rbxassetid://3057073083",PremiumOnly=false})
local _d=dc:AddSection({Name="Remove Body Parts"})
dc:AddButton({Name="No Face",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/wqqqq/main/README.md"))()print("button pressed")end})
dc:AddButton({Name="No Name",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/wwdghjhgfds/main/README.md"))()print("button pressed")end})
dc:AddButton({Name="Remove Head",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/fdqqqqq/main/README.md"))()print("button pressed")end})
dc:AddButton({Name="Remove Arms",Callback=function()
game:GetService("Players").LocalPlayer.Character.RightUpperArm:Destroy()
game:GetService("Players").LocalPlayer.Character.RightLowerArm:Destroy()
game:GetService("Players").LocalPlayer.Character.LeftUpperArm:Destroy()
game:GetService("Players").LocalPlayer.Character.LeftLowerArm:Destroy()print("button pressed")end})
dc:AddButton({Name="Remove Legs",Callback=function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/WspNas/eqqqqq/main/README.md"))()print("button pressed")end})local ad=dc:AddSection({Name="Other"})
dc:AddButton({Name="Call Everyone",Callback=function()
local function cd()
for dd,__a in
pairs(Players:GetPlayers())do
if __a~=LocalPlayer then local a_a={[1]=__a,[2]="Starting"}
game:GetService("ReplicatedStorage").Call:FireServer(unpack(a_a))print("called "..__a.Name)end end end;cd()print("button pressed")end})
dc:AddButton({Name="Fake Cash",Callback=function()
game:GetService("Players").LocalPlayer.Valuestats.Wallet.Value=100000000000;print("button pressed")end})
dc:AddButton({Name="Infinite Yeild (Admin)",Callback=function()
loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()print("button pressed")end})
dc:AddButton({Name="Remove Weather",Callback=function()
game:GetService("StarterPlayer").StarterPlayerScripts.Weather.Disabled=true;print("button pressed")end})
dc:AddButton({Name="Naked",Callback=function()
for cd,dd in
pairs(game:GetService('Players').LocalPlayer.Character:GetChildren())do
if dd:IsA("Shirt")then dd:Destroy()elseif dd:IsA("Pants")then dd:Destroy()elseif
dd:IsA("Accessory")then
if dd.Name=="HOODOWN"then dd:Destroy()elseif dd.Name=="HOOD"then dd:Destroy()elseif dd.Name==
"HOODHAIR"then dd:Destroy()end end end;print("button pressed")end})
local bd=cb:MakeTab({Name="Credits",Icon="rbxassetid://10885640682",PremiumOnly=false})
