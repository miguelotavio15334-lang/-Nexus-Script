-- ⚡ NEXUS V8 - MODO TATU ENTERRADO - CABEÇA PRA BAIXO - QUASE CORPO TODO NO CHÃO
local plr = game.Players.LocalPlayer
local UIS = game:GetService("UserInputService")
local RS = game:GetService("RunService")

local gui = Instance.new("ScreenGui", plr.PlayerGui)
gui.Name = "NexusV8"; gui.ResetOnSpawn = false

local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 300, 0, 320)
main.Position = UDim2.new(0, 15, 0, 20)
main.BackgroundColor3 = Color3.fromRGB(12,12,12)
main.Active = true; main.Draggable = true; main.Visible = true
Instance.new("UICorner", main)
Instance.new("UIStroke", main).Color = Color3.fromRGB(140,0,255)

local tit = Instance.new("TextLabel", main)
tit.Size = UDim2.new(0.70,0,0,40); tit.Text = "⚡ V8 Tatu Enterrado"; tit.TextScaled = true
tit.BackgroundColor3 = Color3.fromRGB(140,0,255); tit.TextColor3 = Color3.new(1,1,1); tit.Font = Enum.Font.GothamBlack
Instance.new("UICorner", tit)

local btnMin = Instance.new("TextButton", main)
btnMin.Size = UDim2.new(0,35,0,35); btnMin.Position = UDim2.new(1,-40,0,2)
btnMin.Text = "-"; btnMin.TextScaled = true; btnMin.BackgroundColor3 = Color3.fromRGB(50,50,50); btnMin.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", btnMin)

local scroll = Instance.new("ScrollingFrame", main)
scroll.Size = UDim2.new(1,0,1,-45); scroll.Position = UDim2.new(0,0,0,45)
scroll.BackgroundTransparency = 1; scroll.CanvasSize = UDim2.new(0,0,0,400)

local function btn(texto, y, cor)
	local b = Instance.new("TextButton", scroll)
	b.Size = UDim2.new(0.92,0,0,35); b.Position = UDim2.new(0.04,0,0,y)
	b.Text = texto; b.TextScaled = true; b.BackgroundColor3 = cor
	b.TextColor3 = Color3.new(1,1,1); b.Font = Enum.Font.GothamBold
	Instance.new("UICorner", b); return b
end

local bVoar = btn("✈️ VOAR [OFF] - F", 5, Color3.fromRGB(40,40,40))
local bVel = btn("🔢 VELOCIDADE 300/500/1000", 45, Color3.fromRGB(80,80,80))
local bSalvar = btn("📍 SALVAR TP", 85, Color3.fromRGB(0,120,255))
local bTP = btn("🚀 DAR TP SALVO", 125, Color3.fromRGB(0,200,0))
local bNoclip = btn("👻 NOCLIP [OFF]", 165, Color3.fromRGB(40,40,40))
local bLaser = btn("🔴 TIRAR LASER [R]", 205, Color3.fromRGB(200,0,0))
local bTatu = btn("🦔 MODO TATU ENTERRADO [OFF] - 2", 245, Color3.fromRGB(100,70,0))

local mini = Instance.new("Frame", gui)
mini.Size = UDim2.new(0, 60, 0, 60); mini.Position = UDim2.new(0, 15, 0, 20)
mini.BackgroundColor3 = Color3.fromRGB(140,0,255); mini.Visible = false; mini.Active = true; mini.Draggable = true
Instance.new("UICorner", mini).CornerRadius = UDim.new(0,15)
local miniTxt = Instance.new("TextLabel", mini); miniTxt.Size=UDim2.new(1,0,1,0); miniTxt.Text="⚡"; miniTxt.TextScaled=true; miniTxt.BackgroundTransparency=1; miniTxt.TextColor3=Color3.new(1,1,1)
local miniBtn = Instance.new("TextButton", mini); miniBtn.Size=UDim2.new(1,0,1,0); miniBtn.Text=""; miniBtn.BackgroundTransparency=1

local function toggleMenu() if main.Visible then main.Visible=false; mini.Visible=true else mini.Visible=false; main.Visible=true end end
btnMin.MouseButton1Click:Connect(toggleMenu)
miniBtn.MouseButton1Click:Connect(toggleMenu)

local voando,bv,att,bg,tpSalvo,noclip,tatuOn = false,nil,nil,nil,nil,false,false
local velocidade = 300; local velocidades = {300,500,1000,5000}; local idxVel=1
local keys={}; local tatuBV, tatuBG, tatuConn

local function tiraLaser()
    for _,v in pairs(workspace:GetDescendants()) do if v.Name:lower():find("laser") then pcall(function() v:Destroy() end) end end
    bLaser.Text="🔴 REMOVIDO ✅"; task.wait(1); bLaser.Text="🔴 TIRAR LASER [R]"
end

local function toggleVoarNoclip()
	if not voando then
		local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart"); if not hrp then return end
		att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero
		bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero
		plr.Character.Humanoid.PlatformStand=true; voando=true; noclip=true
        bVoar.Text="✈️ VOAR [ON] "..velocidade; bVoar.BackgroundColor3=Color3.fromRGB(0,200,0)
        bNoclip.Text="👻 NOCLIP [ON]"; bNoclip.BackgroundColor3=Color3.fromRGB(0,200,0)
		task.spawn(function() while voando do task.wait() if bv then local cam=workspace.CurrentCamera; local dir=Vector3.zero; if keys[Enum.KeyCode.W] then dir+=cam.CFrame.LookVector end; if keys[Enum.KeyCode.S] then dir-=cam.CFrame.LookVector end; if keys[Enum.KeyCode.A] then dir-=cam.CFrame.RightVector end; if keys[Enum.KeyCode.D] then dir+=cam.CFrame.RightVector end; if keys[Enum.KeyCode.Space] then dir+=Vector3.new(0,1,0) end; if keys[Enum.KeyCode.LeftShift] then dir-=Vector3.new(0,1,0) end; bv.VectorVelocity=dir.Magnitude>0 and dir.Unit*velocidade or Vector3.zero end end end)
	else voando=false; noclip=false; if att then att:Destroy() end if bv then bv:Destroy() end if bg then bg:Destroy() end if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.PlatformStand=false end
        bVoar.Text="✈️ VOAR [OFF] "..velocidade; bVoar.BackgroundColor3=Color3.fromRGB(40,40,40)
        bNoclip.Text="👻 NOCLIP [OFF]"; bNoclip.BackgroundColor3=Color3.fromRGB(40,40,40)
    end
end

-- 🦔 MODO TATU ENTERRADO - CABEÇA PRA BAIXO - CORPO TODO NO CHÃO
local function toggleTatu()
    tatuOn = not tatuOn
    if tatuOn then
        bTatu.Text="🦔 TATU ENTERRADO [ON] - 2"; bTatu.BackgroundColor3=Color3.fromRGB(0,200,0)
        if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") and plr.Character:FindFirstChild("Humanoid") then
            local hrp = plr.Character.HumanoidRootPart
            local hum = plr.Character.Humanoid
            hum.PlatformStand = true
            noclip = true
            bNoclip.Text="👻 NOCLIP [ON]"; bNoclip.BackgroundColor3=Color3.fromRGB(0,200,0)

            -- COLOCA CABEÇA PRA BAIXO E ENTERRA NO CHÃO
            -- Quase todo corpo no chão, só um pouquinho pra fora
            hrp.CFrame = hrp.CFrame * CFrame.Angles(math.rad(90),0,0) -- Gira 90 graus cabeça pra baixo

            tatuBG = Instance.new("BodyGyro", hrp)
            tatuBG.MaxTorque = Vector3.new(9e9,9e9,9e9)
            tatuBG.P = 9e4
            tatuBG.CFrame = hrp.CFrame

            tatuBV = Instance.new("BodyVelocity", hrp)
            tatuBV.MaxForce = Vector3.new(9e9,9e9,9e9)
            tatuBV.Velocity = Vector3.new(0,0,0)

            -- LOOP MODO TATU ENTERRADO
            tatuConn = RS.Heartbeat:Connect(function()
                if not tatuOn or not plr.Character or not plr.Character:FindFirstChild("HumanoidRootPart") then return end
                local charHRP = plr.Character.HumanoidRootPart
                -- Mantem enterrado - Raycast pro chão
                local ray = workspace:Raycast(charHRP.Position + Vector3.new(0,5,0), Vector3.new(0,-20,0))
                local chaoY = ray and ray.Position.Y or charHRP.Position.Y
                -- Deixa quase todo corpo embaixo do chão - só a parte de cima das costas pra fora
                local targetPos = Vector3.new(charHRP.Position.X, chaoY - 2.8, charHRP.Position.Z) -- 2.8 studs pra dentro do chão

                -- Movimento WASD mas rastejando no chão com cabeça pra baixo
                local cam = workspace.CurrentCamera
                local moveDir = Vector3.new(0,0,0)
                if keys[Enum.KeyCode.W] then moveDir += Vector3.new(cam.CFrame.LookVector.X,0,cam.CFrame.LookVector.Z) end
                if keys[Enum.KeyCode.S] then moveDir -= Vector3.new(cam.CFrame.LookVector.X,0,cam.CFrame.LookVector.Z) end
                if keys[Enum.KeyCode.A] then moveDir -= Vector3.new(cam.CFrame.RightVector.X,0,cam.CFrame.RightVector.Z) end
                if keys[Enum.KeyCode.D] then moveDir += Vector3.new(cam.CFrame.RightVector.X,0,cam.CFrame.RightVector.Z) end

                if moveDir.Magnitude > 0 then
                    tatuBV.Velocity = moveDir.Unit * 35 -- Velocidade tatu rastejando
                    targetPos += moveDir.Unit * 0.5
                else
                    tatuBV.Velocity = Vector3.new(0,0,0)
                end

                -- Mantem cabeça pra baixo sempre
                local lookAt = targetPos + (moveDir.Magnitude>0 and moveDir.Unit*5 or Vector3.new(0,0,1))
                charHRP.CFrame = CFrame.new(targetPos, Vector3.new(lookAt.X, targetPos.Y, lookAt.Z)) * CFrame.Angles(math.rad(-90),0,0)
                if tatuBG then tatuBG.CFrame = charHRP.CFrame end

                -- Sem colisão pra atravessar tudo enterrado
                for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end
            end)
            print("🦔 MODO TATU ENTERRADO ATIVADO! Cabeça pra baixo, corpo no chão!")
        end
    else
        bTatu.Text="🦔 MODO TATU ENTERRADO [OFF] - 2"; bTatu.BackgroundColor3=Color3.fromRGB(100,70,0)
        if tatuConn then tatuConn:Disconnect() end
        if tatuBG then tatuBG:Destroy() end
        if tatuBV then tatuBV:Destroy() end
        if plr.Character and plr.Character:FindFirstChild("Humanoid") then
            plr.Character.Humanoid.PlatformStand = false
        end
        noclip = false
        bNoclip.Text="👻 NOCLIP [OFF]"; bNoclip.BackgroundColor3=Color3.fromRGB(40,40,40)
        print("🦔 MODO TATU DESATIVADO!")
    end
end

UIS.InputBegan:Connect(function(input, gpe)
    if gpe then return end
    keys[input.KeyCode]=true
    if input.KeyCode == Enum.KeyCode.M then toggleMenu()
    elseif input.KeyCode == Enum.KeyCode.F then toggleVoarNoclip()
    elseif input.KeyCode == Enum.KeyCode.R then tiraLaser()
    elseif input.KeyCode == Enum.KeyCode.Two or input.KeyCode == Enum.KeyCode.KeypadTwo then toggleTatu() end
end)
UIS.InputEnded:Connect(function(input) keys[input.KeyCode]=false end)

bVoar.MouseButton1Click:Connect(toggleVoarNoclip)
bVel.MouseButton1Click:Connect(function() idxVel=idxVel%#velocidades+1; velocidade=velocidades[idxVel]; bVel.Text="🔢 VELOCIDADE "..velocidade; bVoar.Text=(voando and "✈️ VOAR [ON] " or "✈️ VOAR [OFF] ")..velocidade end)
bSalvar.MouseButton1Click:Connect(function() local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") if hrp then tpSalvo=hrp.CFrame; bSalvar.Text="📍 SALVO ✅"; task.wait(1); bSalvar.Text="📍 SALVAR TP" end end)
bTP.MouseButton1Click:Connect(function() if tpSalvo and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then plr.Character.HumanoidRootPart.CFrame=tpSalvo end end)
bNoclip.MouseButton1Click:Connect(function() noclip=not noclip; bNoclip.Text=noclip and "👻 NOCLIP [ON]" or "👻 NOCLIP [OFF]"; bNoclip.BackgroundColor3=noclip and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
bLaser.MouseButton1Click:Connect(tiraLaser)
bTatu.MouseButton1Click:Connect(toggleTatu)

RS.Stepped:Connect(function()
    if noclip and not tatuOn and plr.Character then
        for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end
    end
end)

print("⚡ V8 TATU ENTERRADO CARREGADO! M=Menu F=Voar R=Laser 2=Tatu cabeça pra baixo no chão!")
