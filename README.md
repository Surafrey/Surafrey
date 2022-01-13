
if game:GetService("CoreGui"):FindFirstChild("ST HUB | TEST") then
    game:GetService("CoreGui"):FindFirstChild("ST HUB | TEST"):Destroy()
 end
 local UILib = loadstring(game:HttpGet('https://pastebin.com/raw/DpS0SeTC'))()
 
 local win = UILib:Window("ST HUB | TEST",Color3.fromRGB(44, 120, 224), Enum.KeyCode.RightControl)
 local Main = win:Tab("Main")
 
 Main:Button("Rejoin Server", function()
	game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").localPlayer)
end)
 
 Main:Toggle("Fast Attack | Big hitbox", _G.FastAtttk, function(vu)
 _G.FastAtttk = vu
end)
 
Main:Toggle("Auto Haki", true, function(vu)
    Auto_Haki = vu
end)

 
 Main:Slider("Slider",0,100,16,true, function(State)
     
 end)
 
 local Settings = win:Tab("Settings")
 Settings:Button("Copy Discord ", function()
     setclipboard("https://discord.gg/fAaHrdbW")
     UILib:Notification("Copied!", "Okay")
 end)


 local RigC = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework) 
 local VirtualUser = game:GetService('VirtualUser')
 local kkii = require(game.ReplicatedStorage.Util.CameraShaker)
 spawn(function()
     game:GetService('RunService').Heartbeat:connect(function()
         if _G.FastAtttk then
             pcall(function()
                 RigC.activeController.timeToNextAttack = -1
                 RigC.activeController.attacking = false
                 RigC.activeController.blocking = false
                 RigC.activeController.timeToNextAttack = 0
                 RigC.activeController.timeToNextBlock = 0
                 RigC.activeController.increment = 3
                 RigC.activeController.hitboxMagnitude = 100
                 game.Players.LocalPlayer.Character.Stun.Value = 0
                 game.Players.LocalPlayer.Character.Humanoid.Sit = false

                 VirtualUser:CaptureController()
                 VirtualUser:Button1Down(Vector2.new(1280, 672))
                 kkii:Stop()
             end)
         end
     end)
 end)
spawn(function()
     for i = 1,math,9999999999999999999999999999999999999999999999999999 do game:GetService('RunService').Heartbeat:wait()
         if _G.FastAtttk then
         VirtualUser:CaptureController()
         VirtualUser:Button1Down(Vector2.new(1280, 672))
     end
 end
end)

if _G.FastAtttk == false then
 _G.FastAtttk = false
else
 _G.FastAtttk = true
end


spawn(function()
    while wait(.1) do
        if Auto_Haki then
            if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
            end
        end
    end
end)
