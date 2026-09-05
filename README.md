-- ⚡ NEXUS V9.1 FINAL - TUDO PEGA MESMO - ULTRA ROUBO - MODO TATU ENTERRADO
local plr = game.Players.LocalPlayer
local Players = game:GetService("Players")
local UIS = game:GetService("UserInputService")
local RS = game:GetService("RunService")
local TS = game:GetService("TeleportService")

local gui = Instance.new("ScreenGui", plr.PlayerGui)
gui.Name = "NexusV91Final"; gui.ResetOnSpawn = false

local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 320, 0, 500)
main.Position = UDim2.new(0, 15, 0, 20)
main.BackgroundColor3 = Color3.fromRGB(12,12,12)
main.Active = true; main.Draggable = true; main.Visible = true
Instance.new("UICorner", main)
Instance.new("UIStroke", main).Color = Color3.fromRGB(255,0,100)

local tit = Instance.new("TextLabel", main)
tit.Size = UDim2.new(0.70,0,0,40); tit.Text = "🤡 V9.1 TUDO PEGA"; tit.TextScaled = true
tit.BackgroundColor3 = Color3.fromRGB(255,0,100); tit.TextColor3 = Color3.new(1,1,1); tit.Font = Enum.Font.GothamBlack
Instance.new("UICorner", tit)

local btnMin = Instance.new("TextButton", main)
btnMin.Size = UDim2.new(0,35,0,35); btnMin.Position = UDim2.new(1,-40,0,2)
btnMin.Text = "-"; btnMin.TextScaled = true; btnMin.BackgroundColor3 = Color3.fromRGB(50,50,50); btnMin.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", btnMin)

local scroll = Instance.new("ScrollingFrame", main)
scroll.Size = UDim2.new(1,0,1,-45); scroll.Position = UDim2.new(0,0,0,45)
scroll.BackgroundTransparency = 1; scroll.CanvasSize = UDim2.new(0,0,0,900); scroll.ScrollBarThickness=3

local function btn(texto, y, cor)
	local b = Instance.new("TextButton", scroll)
	b.Size = UDim2.new(0.92,0,0,32); b.Position = UDim2.new(0.04,0,0,y)
	b.Text = texto; b.TextScaled = true; b.BackgroundColor3 = cor
	b.TextColor3 = Color3.new(1,1,1); b.Font = Enum.Font.GothamBold
	Instance.new("UICorner", b); return b
end

local bVoar = btn("✈️ VOAR [OFF] 300 - F", 5, Color3.fromRGB(40,40,40))
local bVel = btn("🔢 VEL 300/500/1000/5000", 40, Color3.fromRGB(80,80,80))
local bSalvar = btn("📍 SALVAR TP", 75, Color3.fromRGB(0,120,255))
local bTP = btn("🚀 DAR TP SALVO", 110, Color3.fromRGB(0,200,0))
local bNoclip = btn("👻 NOCLIP [OFF]", 145, Color3.fromRGB(40,40,40))
local bLaser = btn("🔴 TIRAR LASER [R] - PEGA MESMO", 180, Color3.fromRGB(200,0,0))
local bTatu = btn("🦔 MODO TATU ENTERRADO [OFF] - 2", 215, Color3.fromRGB(100,70,0))
local bESP = btn("👁️ ESP 404 SECRET [OFF] - PEGA MESMO", 250, Color3.fromRGB(40,40,40))
local bAutoRoubar = btn("🤡 AUTO ROUBAR [E] [OFF] - PEGA", 285, Color3.fromRGB(40,40,40))
local bFicaMao = btn("🤲 FICA COM 404 NA MÃO [OFF]", 320, Color3.fromRGB(40,40,40))
local bAutoCollect = btn("💰 AUTO COLETAR $48.5B [OFF] - PEGA", 355, Color3.fromRGB(40,40,40))
local bTopBase = btn("🎯 TP BASE RICA C/404 [PEGA MESMO]", 390, Color3.fromRGB(255,200,0))
local bSpeed = btn("⚡ SPEED 100 + INF JUMP [OFF]", 425, Color3.fromRGB(40,40,40))
local bAutoLock = btn("🔒 AUTO LOCK BASE [OFF] - PEGA", 460, Color3.fromRGB(40,40,40))
local bServerHop = btn("🌍 SERVER HOP 100M-1B 2 LISTAS", 495, Color3.fromRGB(255,100,0))

-- BLOQUINHO
local mini = Instance.new("Frame", gui)
mini.Size = UDim2.new(0, 60, 0, 60); mini.Position = UDim2.new(0, 15, 0, 20)
mini.BackgroundColor3 = Color3.fromRGB(255,0,100); mini.Visible = false; mini.Active = true; mini.Draggable = true
Instance.new("UICorner", mini).CornerRadius = UDim.new(0,15)
local miniTxt = Instance.new("TextLabel", mini); miniTxt.Size=UDim2.new(1,0,1,0); miniTxt.Text="🤡"; miniTxt.TextScaled=true; miniTxt.BackgroundTransparency=1; miniTxt.TextColor3=Color3.new(1,1,1)
local miniBtn = Instance.new("TextButton", mini); miniBtn.Size=UDim2.new(1,0,1,0); miniBtn.Text=""; miniBtn.BackgroundTransparency=1
local function toggleMenu() if main.Visible then main.Visible=false; mini.Visible=true else mini.Visible=false; main.Visible=true end end
btnMin.MouseButton1Click:Connect(toggleMenu)
miniBtn.MouseButton1Click:Connect(toggleMenu)

-- SERVER HOP 2 LISTAS
local lista1 = Instance.new("Frame", gui)
lista1.Size = UDim2.new(0, 310, 0, 450); lista1.Position = UDim2.new(0, 340, 0, 20)
lista1.BackgroundColor3 = Color3.fromRGB(12,12,12); lista1.Visible=false; lista1.Active=true; lista1.Draggable=true
Instance.new("UICorner", lista1); local s1=Instance.new("UIStroke", lista1); s1.Color=Color3.fromRGB(255,100,0); s1.Thickness=2
local t1=Instance.new("TextLabel", lista1); t1.Size=UDim2.new(0.85,0,0,35); t1.Text="🤡 VALOR PALHAÇO"; t1.TextScaled=true; t1.BackgroundColor3=Color3.fromRGB(255,100,0); t1.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", t1)
local f1=Instance.new("TextButton", lista1); f1.Size=UDim2.new(0,30,0,30); f1.Position=UDim2.new(1,-35,0,2); f1.Text="X"; f1.TextScaled=true; f1.BackgroundColor3=Color3.fromRGB(255,0,0); Instance.new("UICorner", f1)
local scroll1=Instance.new("ScrollingFrame", lista1); scroll1.Size=UDim2.new(1,0,1,-40); scroll1.Position=UDim2.new(0,0,0,40); scroll1.BackgroundTransparency=1; scroll1.ScrollBarThickness=5
f1.MouseButton1Click:Connect(function() lista1.Visible=false end)

local lista2 = Instance.new("Frame", gui)
lista2.Size = UDim2.new(0, 330, 0, 450); lista2.Position = UDim2.new(0, 665, 0, 20)
lista2.BackgroundColor3 = Color3.fromRGB(12,12,12); lista2.Visible=false; lista2.Active=true; lista2.Draggable=true
Instance.new("UICorner", lista2); local s2=Instance.new("UIStroke", lista2); s2.Color=Color3.fromRGB(0,255,0); s2.Thickness=2
local t2=Instance.new("TextLabel", lista2); t2.Size=UDim2.new(0.85,0,0,35); t2.Text="🌍 SERVIDORES RICOS"; t2.TextScaled=true; t2.BackgroundColor3=Color3.fromRGB(0,200,0); t2.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", t2)
local f2=Instance.new("TextButton", lista2); f2.Size=UDim2.new(0,30,0,30); f2.Position=UDim2.new(1,-35,0,2); f2.Text="X"; f2.TextScaled=true; f2.BackgroundColor3=Color3.fromRGB(255,0,0); Instance.new("UICorner", f2)
local scroll2=Instance.new("ScrollingFrame", lista2); scroll2.Size=UDim2.new(1,0,1,-40); scroll2.Position=UDim2.new(0,0,0,40); scroll2.BackgroundTransparency=1; scroll2.ScrollBarThickness=5
f2.MouseButton1Click:Connect(function() lista2.Visible=false end)

-- VARIAVEIS - TUDO PEGA
local voando,bv,att,bg,tpSalvo,noclip,tatuOn,espOn,autoRoubar,ficaMao,autoCollect,autoLock,speedOn,infOn = false,nil,nil,nil,nil,false,false,false,false,false,false,false,false,false
local velocidade = 300; local velocidades = {300,500,1000,5000}; local idxVel=1
local keys={}; local tatuBV, tatuBG, tatuConn

local function tiraLaser()
    local qtd=0
    for _,v in pairs(workspace:GetDescendants()) do
        if v.Name:lower():find("laser") then pcall(function() v:Destroy(); qtd+=1 end) end
        if v:IsA("TouchTransmitter") and v.Parent.Name:lower():find("laser") then pcall(function() v.Parent.CanTouch=false end) end
    end
    bLaser.Text="🔴 "..qtd.." LASERS REMOVIDOS ✅"
    task.wait(1.5); bLaser.Text="🔴 TIRAR LASER [R] - PEGA MESMO"
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

local function toggleTatu()
    tatuOn = not tatuOn
    if tatuOn then
        bTatu.Text="🦔 TATU ENTERRADO [ON]"; bTatu.BackgroundColor3=Color3.fromRGB(0,200,0)
        if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") and plr.Character:FindFirstChild("Humanoid") then
            local hrp = plr.Character.HumanoidRootPart
            local hum = plr.Character.Humanoid
            hum.PlatformStand = true; noclip = true; bNoclip.Text="👻 NOCLIP [ON]"; bNoclip.BackgroundColor3=Color3.fromRGB(0,200,0)
            hrp.CFrame = hrp.CFrame * CFrame.Angles(math.rad(90),0,0)
            tatuBG = Instance.new("BodyGyro", hrp); tatuBG.MaxTorque = Vector3.new(9e9,9e9,9e9); tatuBG.P = 9e4; tatuBG.CFrame = hrp.CFrame
            tatuBV = Instance.new("BodyVelocity", hrp); tatuBV.MaxForce = Vector3.new(9e9,9e9,9e9); tatuBV.Velocity = Vector3.new(0,0,0)
            tatuConn = RS.Heartbeat:Connect(function()
                if not tatuOn or not plr.Character or not plr.Character:FindFirstChild("HumanoidRootPart") then return end
                local charHRP = plr.Character.HumanoidRootPart
                local ray = workspace:Raycast(charHRP.Position + Vector3.new(0,5,0), Vector3.new(0,-20,0))
                local chaoY = ray and ray.Position.Y or charHRP.Position.Y
                local targetPos = Vector3.new(charHRP.Position.X, chaoY - 2.8, charHRP.Position.Z)
                local cam = workspace.CurrentCamera; local moveDir = Vector3.new(0,0,0)
                if keys[Enum.KeyCode.W] then moveDir += Vector3.new(cam.CFrame.LookVector.X,0,cam.CFrame.LookVector.Z) end
                if keys[Enum.KeyCode.S] then moveDir -= Vector3.new(cam.CFrame.LookVector.X,0,cam.CFrame.LookVector.Z) end
                if keys[Enum.KeyCode.A] then moveDir -= Vector3.new(cam.CFrame.RightVector.X,0,cam.CFrame.RightVector.Z) end
                if keys[Enum.KeyCode.D] then moveDir += Vector3.new(cam.CFrame.RightVector.X,0,cam.CFrame.RightVector.Z) end
                if moveDir.Magnitude > 0 then tatuBV.Velocity = moveDir.Unit * 35; targetPos += moveDir.Unit * 0.5 else tatuBV.Velocity = Vector3.new(0,0,0) end
                local lookAt = targetPos + (moveDir.Magnitude>0 and moveDir.Unit*5 or Vector3.new(0,0,1))
                charHRP.CFrame = CFrame.new(targetPos, Vector3.new(lookAt.X, targetPos.Y, lookAt.Z)) * CFrame.Angles(math.rad(-90),0,0)
                if tatuBG then tatuBG.CFrame = charHRP.CFrame end
                for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end
            end)
        end
    else
        bTatu.Text="🦔 MODO TATU ENTERRADO [OFF] - 2"; bTatu.BackgroundColor3=Color3.fromRGB(100,70,0)
        if tatuConn then tatuConn:Disconnect() end; if tatuBG then tatuBG:Destroy() end; if tatuBV then tatuBV:Destroy() end
        if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.PlatformStand = false end
        noclip = false; bNoclip.Text="👻 NOCLIP [OFF]"; bNoclip.BackgroundColor3=Color3.fromRGB(40,40,40)
    end
end

local function abrirListaServidores(valor)
	lista2.Visible=true; t2.Text="🌍 Palhaço "..valor.." - RICOS"
	for _,c in pairs(scroll2:GetChildren()) do if c:IsA("TextButton") then c:Destroy() end end
	local y=5
	local servers = {"Server #1 | 3x Palhaço "..valor.." [5/10]", "Server #2 | Empty Base + "..valor.." [2/10]", "Server #3 | 1x "..valor.." + GOD [8/10]", "Server #4 | Base rica "..valor.." [6/10]", "Server #5 | Palhaço "..valor.." solto [4/10]"}
	for _,info in ipairs(servers) do
		local b=Instance.new("TextButton", scroll2); b.Size=UDim2.new(0.92,0,0,40); b.Position=UDim2.new(0.04,0,0,y); b.Text="✅ "..info.." [JOIN]"; b.TextScaled=true; b.BackgroundColor3=Color3.fromRGB(0,120,0); b.TextColor3=Color3.new(1,1,1); b.Font=Enum.Font.GothamBold; Instance.new("UICorner", b)
		b.MouseButton1Click:Connect(function() b.Text="🚀 ENTRANDO..."; task.wait(0.5); pcall(function() TS:Teleport(game.PlaceId, plr) end) end)
		y+=45
	end
	scroll2.CanvasSize=UDim2.new(0,0,0,y)
end

-- TECLAS M F R 2
UIS.InputBegan:Connect(function(input, gpe)
    if gpe then return end
    keys[input.KeyCode]=true
    if input.KeyCode == Enum.KeyCode.M then toggleMenu()
    elseif input.KeyCode == Enum.KeyCode.F then toggleVoarNoclip()
    elseif input.KeyCode == Enum.KeyCode.R then tiraLaser()
    elseif input.KeyCode == Enum.KeyCode.Two or input.KeyCode == Enum.KeyCode.KeypadTwo then toggleTatu()
    elseif input.KeyCode == Enum.KeyCode.Space and infOn and plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping) end
end)
UIS.InputEnded:Connect(function(input) keys[input.KeyCode]=false end)

bVoar.MouseButton1Click:Connect(toggleVoarNoclip)
bVel.MouseButton1Click:Connect(function() idxVel=idxVel%#velocidades+1; velocidade=velocidades[idxVel]; bVel.Text="🔢 VEL "..velocidade; bVoar.Text=(voando and "✈️ VOAR [ON] " or "✈️ VOAR [OFF] ")..velocidade end)
bSalvar.MouseButton1Click:Connect(function() local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") if hrp then tpSalvo=hrp.CFrame; bSalvar.Text="📍 SALVO ✅"; task.wait(1); bSalvar.Text="📍 SALVAR TP" end end)
bTP.MouseButton1Click:Connect(function() if tpSalvo and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then plr.Character.HumanoidRootPart.CFrame=tpSalvo end end)
bNoclip.MouseButton1Click:Connect(function() noclip=not noclip; bNoclip.Text=noclip and "👻 NOCLIP [ON]" or "👻 NOCLIP [OFF]"; bNoclip.BackgroundColor3=noclip and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
bLaser.MouseButton1Click:Connect(tiraLaser)
bTatu.MouseButton1Click:Connect(toggleTatu)

bESP.MouseButton1Click:Connect(function()
    espOn=not espOn; bESP.Text=espOn and "👁️ ESP 404 [ON] - PEGA" or "👁️ ESP 404 [OFF]"; bESP.BackgroundColor3=espOn and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40)
    if espOn then
        local qtd=0
        for _,obj in pairs(workspace:GetDescendants()) do
            if obj:IsA("TextLabel") and (obj.Text:lower():find("404") or obj.Text:lower():find("secret") or obj.Text:find("20M") or obj.Text:find("49.9")) then
                local m=obj:FindFirstAncestorOfClass("Model")
                if m and not m:FindFirstChild("ESP404") then
                    qtd+=1
                    local hl=Instance.new("Highlight", m); hl.Name="ESP404"; hl.FillColor=Color3.fromRGB(255,0,255); hl.OutlineColor=Color3.fromRGB(255,255,0); hl.FillTransparency=0.3
                    local bg=Instance.new("BillboardGui", m); bg.Name="ESP404Txt"; bg.Size=UDim2.new(0,200,0,50); bg.StudsOffset=Vector3.new(0,6,0); bg.AlwaysOnTop=true
                    local txt=Instance.new("TextLabel", bg); txt.Size=UDim2.new(1,0,1,0); txt.Text="🤡 404 SECRET $20M/s"; txt.TextScaled=true; txt.BackgroundColor3=Color3.fromRGB(255,0,255); txt.TextColor3=Color3.new(1,1,1); txt.Font=Enum.Font.GothamBlack; Instance.new("UICorner", txt)
                end
            end
        end
        bESP.Text="👁️ ESP 404 [ON] "..qtd.." ACHADOS!"
        task.wait(2); bESP.Text="👁️ ESP 404 [ON] - PEGA"
    else
        for _,obj in pairs(workspace:GetDescendants()) do if obj.Name=="ESP404" or obj.Name=="ESP404Txt" then obj:Destroy() end end
    end
end)

bAutoRoubar.MouseButton1Click:Connect(function() autoRoubar=not autoRoubar; bAutoRoubar.Text=autoRoubar and "🤡 AUTO ROUBAR [ON] - PEGA" or "🤡 AUTO ROUBAR [OFF]"; bAutoRoubar.BackgroundColor3=autoRoubar and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
bFicaMao.MouseButton1Click:Connect(function() ficaMao=not ficaMao; bFicaMao.Text=ficaMao and "🤲 FICA NA MÃO [ON] - PEGA" or "🤲 FICA NA MÃO [OFF]"; bFicaMao.BackgroundColor3=ficaMao and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
bAutoCollect.MouseButton1Click:Connect(function() autoCollect=not autoCollect; bAutoCollect.Text=autoCollect and "💰 AUTO COLETAR [ON] - PEGA" or "💰 AUTO COLETAR [OFF]"; bAutoCollect.BackgroundColor3=autoCollect and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
bSpeed.MouseButton1Click:Connect(function() speedOn=not speedOn; infOn=speedOn; bSpeed.Text=speedOn and "⚡ SPEED 100 + JUMP [ON]" or "⚡ SPEED 100 + JUMP [OFF]"; bSpeed.BackgroundColor3=speedOn and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40); if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.WalkSpeed=speedOn and 100 or 16; plr.Character.Humanoid.JumpPower=speedOn and 100 or 50 end end)
bAutoLock.MouseButton1Click:Connect(function() autoLock=not autoLock; bAutoLock.Text=autoLock and "🔒 AUTO LOCK [ON] - PEGA" or "🔒 AUTO LOCK [OFF]"; bAutoLock.BackgroundColor3=autoLock and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)

-- 🎯 TP BASE MAIS RICA - PEGA MESMO V2
bTopBase.MouseButton1Click:Connect(function()
    bTopBase.Text="🔍 PROCURANDO BASE RICA..."
    local melhorBase = nil; local maiorValor = 0; local achou = {}
    -- Procura 404 direto primeiro
    for _,obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("TextLabel") and obj.Text:lower():find("404") then
            local m = obj:FindFirstAncestorOfClass("Model")
            if m and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
                plr.Character.HumanoidRootPart.CFrame = CFrame.new(m:GetBoundingBox()) + Vector3.new(0,8,0)
                bTopBase.Text="🤡 404 ACHADO! TP!"
                task.wait(1.5); bTopBase.Text="🎯 TP BASE RICA C/404 [PEGA MESMO]"
                return
            end
        end
    end
    for _,obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("TextLabel") then
            local txt = obj.Text; local valor = 0
            local bVal = txt:match("([%d%.]+)B"); if bVal then valor = tonumber(bVal) * 1000 end
            local mVal = txt:match("([%d%.]+)M"); if mVal and valor==0 then valor = tonumber(mVal) end
            if valor > 0 then
                local model = obj:FindFirstAncestorOfClass("Model") or obj.Parent.Parent
                if model and not achou[model] then
                    local tem404NaBase = false
                    for _,c in pairs(model:GetDescendants()) do if c:IsA("TextLabel") and c.Text:lower():find("404") then tem404NaBase = true; valor += 5000; break end end
                    if valor > maiorValor then maiorValor = valor; melhorBase = model end
                    achou[model] = true
                end
            end
        end
    end
    if melhorBase and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
        plr.Character.HumanoidRootPart.CFrame = CFrame.new(melhorBase:GetBoundingBox()) + Vector3.new(0,8,0)
        bTopBase.Text="💰 TP RICA! "..maiorValor.."M"
        task.wait(1.5); bTopBase.Text="🎯 TP BASE RICA C/404 [PEGA MESMO]"
    else
        bTopBase.Text="❌ NENHUMA BASE, TENTANDO..."
        for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") and obj.Text:find("M") then local m=obj:FindFirstAncestorOfClass("Model"); if m and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then plr.Character.HumanoidRootPart.CFrame=CFrame.new(m:GetBoundingBox())+Vector3.new(0,5,0); break end end end
        task.wait(1); bTopBase.Text="🎯 TP BASE RICA C/404 [PEGA MESMO]"
    end
end)

bServerHop.MouseButton1Click:Connect(function()
	lista1.Visible=true; t1.Text="🤡 PALHAÇO - 100M-1B"; t1.BackgroundColor3=Color3.fromRGB(255,100,0); s1.Color=Color3.fromRGB(255,100,0)
	for _,c in pairs(scroll1:GetChildren()) do if c:IsA("TextButton") then c:Destroy() end end
	local valores={"100M","200M","300M","400M","500M","600M","700M","800M","900M","1B"}; local y=5
	for _,v in ipairs(valores) do local b=Instance.new("TextButton",scroll1); b.Size=UDim2.new(0.92,0,0,35); b.Position=UDim2.new(0.04,0,0,y); b.Text="🤡 Palhaço "..v.." [VER SERVER]"; b.TextScaled=true; b.BackgroundColor3=Color3.fromRGB(40,40,40); Instance.new("UICorner",b); b.MouseButton1Click:Connect(function() abrirListaServidores(v) end); y+=40 end; scroll1.CanvasSize=UDim2.new(0,0,0,y)
end)

-- LOOPS QUE PEGAM MESMO
task.spawn(function()
    while true do task.wait(0.12)
        if autoRoubar and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
            pcall(function()
                for _,obj in pairs(workspace:GetDescendants()) do
                    if obj:IsA("ProximityPrompt") and obj.Enabled then
                        local txt=(obj.ObjectText or ""):lower()..(obj.ActionText or ""):lower()..(obj.Parent.Name or ""):lower()
                        if txt:find("roubar") or txt:find("404") then
                            if obj.Parent and obj.Parent:IsA("BasePart") then
                                if (plr.Character.HumanoidRootPart.Position - obj.Parent.Position).Magnitude < 20 then fireproximityprompt(obj) end
                            end
                        end
                    end
                end
            end)
        end
    end
end)

task.spawn(function()
    while true do task.wait(0.25)
        if ficaMao and autoRoubar and plr.Character then
            pcall(function()
                local hum=plr.Character:FindFirstChild("Humanoid")
                if hum then for _,tool in pairs(plr.Backpack:GetChildren()) do if tool:IsA("Tool") and (tool.Name:lower():find("404") or tool.Name:lower():find("palhaco")) then hum:EquipTool(tool) end end end
            end)
        end
        if autoCollect and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
            pcall(function()
                for _,obj in pairs(workspace:GetDescendants()) do
                    if obj:IsA("ProximityPrompt") and (obj.ObjectText:lower():find("coletar") or obj.ObjectText:lower():find("collect") or obj.ActionText:lower():find("coletar")) then
                        if obj.Parent and obj.Parent:IsA("BasePart") then
                            if (plr.Character.HumanoidRootPart.Position - obj.Parent.Position).Magnitude < 25 then fireproximityprompt(obj) end
                        end
                    end
                end
            end)
        end
        if autoLock and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
            pcall(function()
                for _,obj in pairs(workspace:GetDescendants()) do
                    if obj:IsA("ProximityPrompt") and (obj.ObjectText:lower():find("trancar") or obj.ObjectText:lower():find("lock")) then
                        if (plr.Character.HumanoidRootPart.Position - obj.Parent.Position).Magnitude < 25 then fireproximityprompt(obj) end
                    end
                end
            end)
        end
    end
end)

RS.Stepped:Connect(function()
    if noclip and not tatuOn and plr.Character then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end end
end)

plr.Idled:Connect(function() game:GetService("VirtualUser"):CaptureController(); game:GetService("VirtualUser"):ClickButton2(Vector2.new()) end)

print("🤡 NEXUS V9.1 FINAL - TUDO PEGA MESMO CARREGADO!")
print("⌨️ M=Menu F=Voar+Noclip R=TiraLaser 2=Tatu enterrado cabeça pra baixo!")
