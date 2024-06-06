if game.PlaceId == 16667221376 then
    local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
    local Window = OrionLib:MakeWindow({Name = "[ JU HUB ][ 1.0 ]", HidePremium = false, Intro = false, IntroText = "by yesmom555🔥", SaveConfig = true, ConfigFolder = "TutorialConfig"})
    
    
    local ItemTab = Window:MakeTab({
        Name = "Item",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false
    })

    local PlayerTab = Window:MakeTab({
        Name = "Player",
        Icon = "rbxassetid://17603543716",
        PremiumOnly = false
    })
  
    local MessageTab = Window:MakeTab({
        Name = "message",
        Icon = "rbxassetid://17603543716",
        PremiumOnly = false
    })

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

local Value1 = nil
local Item1 = nil

local X = nil

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


    ItemTab:AddTextbox({
        Name = "Value",
        Default = "",
        TextDisappear = true,
        Callback = function(Value)
            Value1 = tostring(Value)
            print(Value1)
        end	  
    })



    ItemTab:AddTextbox({
        Name = "Item",
        Default = "",
        TextDisappear = true,
        Callback = function(Item)
            Item1 = tostring(Item)
            print(Item1)
        end	  
    })
    
    
    ItemTab:AddButton({
        Name = "เสกของต้องมีตัวก็อปอย่างน้อย 1 ชิ้น",
        Callback = function()
            game:GetService("ReplicatedStorage"):WaitForChild("Remote"):WaitForChild("Gacha"):InvokeServer(Item1, -Value1)
          end    
    })



    ItemTab:AddButton({
        Name = "Support Gacha",
        Callback = function()
            game:GetService("ReplicatedStorage"):WaitForChild("Remote"):WaitForChild("Gacha"):InvokeServer("Support Gacha",-Value1)
          end    
    })
    
    
    
    ItemTab:AddToggle({
        Name = "open auto Support Gacha",
        Default = false,
        Callback = function(state)
            _G.A = state
            while _G.A do wait()
            game:GetService("ReplicatedStorage"):WaitForChild("Remote"):WaitForChild("Gacha"):InvokeServer("Support Gacha",7000)
            end
        end    
    })
    
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


PlayerTab:AddButton({
    Name = "การเกิด",
    Callback = function()
        game.Players.LocalPlayer.Character.Humanoid.Health = 100
      end    
})

PlayerTab:AddButton({
    Name = "การตาย",
    Callback = function()
        game.Players.LocalPlayer.Character.Humanoid.Health = 0
      end    
})   

PlayerTab:AddButton({
    Name = "Bypass",
    Callback = function()
        for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
            if v.Name == "Anti - fly" then
                v.Disabled = true
            end
        end
      end    
})   
    
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  

    MessageTab:AddTextbox({
        Name = "message",
        Default = "",
        TextDisappear = true,
        Callback = function(XX)
            X = tostring(XX)
            print(X)
        end	  
    })

        MessageTab:AddToggle({
        Name = "Spam Social",
        Default = false,
        Callback = function(state)
            _G.A = state
                while _G.A do wait()
                local args = {
                    [1] = X
                }

                game:GetService("ReplicatedStorage"):WaitForChild("AdvancedPhone"):WaitForChild("PostEvent"):FireServer(unpack(args))
                end
        end    
    })

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
    
    end
    
    OrionLib:Init()
