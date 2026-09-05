-- V42 CIRILO MI - PEGA NA MÃO E LEVA PRA BASE - 700 PREMIUM / 190 FREE
local plr = game.Players.LocalPlayer
local RS = game:GetService("RunService")
local UIS = game:GetService("UserInputService")
local function getGuiParent()
    local ok, hui = pcall(function() return gethui() end)
    if ok and hui then return hui end
    return game.CoreGui
end
for _,v in pairs(getGuiParent():GetChildren()) do if v.Name:find("Cirilo") then v:Destroy() end end
for _,v in pairs(plr.PlayerGui:GetChildren()) do if v.Name:find("Cirilo") then v:Destroy() end end

local function criarPremium()
    local parent = getGuiParent()
    for _,v in pairs(parent:GetChildren()) do if v.Name:find("Cirilo") then v:Destroy() end end
    for _,v in pairs(plr.PlayerGui:GetChildren()) do if v.Name:find("Cirilo") then v:Destroy() end end
    local gui = Instance.new("ScreenGui"); gui.Name="CiriloMiPremium"; gui.Parent=parent
    local guiBloco = Instance.new("ScreenGui"); guiBloco.Name="CiriloMiPremiumBloco"; guiBloco.Parent=parent
    local main = Instance.new("Frame", gui); main.Size=UDim2.new(0,580,0,560); main.Position=UDim2.new(0.5,-290,0.5,-280); main.BackgroundColor3=Color3.fromRGB(20,5,5); main.Active=true; main.Draggable=true; Instance.new("UICorner", main); Instance.new("UIStroke", main).Color=Color3.fromRGB(255,0,0)
    local top = Instance.new("Frame", main); top.Size=UDim2.new(1,0,0,30); top.BackgroundColor3=Color3.fromRGB(40,0,0); Instance.new("UICorner", top)
    local title = Instance.new("TextLabel", top); title.Size=UDim2.new(0.7,0,1,0); title.Position=UDim2.new(0.02,0,0,0); title.Text="cirilo mi : PREMIUM 700 - PEGA NA MÃO E LEVA"; title.TextScaled=true; title.BackgroundTransparency=1; title.TextColor3=Color3.fromRGB(255,100,100); title.TextXAlignment=Enum.TextXAlignment.Left; title.Font=Enum.Font.GothamBlack
    local btnMin = Instance.new("TextButton", top); btnMin.Size=UDim2.new(0,30,0,30); btnMin.Position=UDim2.new(1,-60,0,0); btnMin.Text="—"; btnMin.BackgroundTransparency=1; btnMin.TextColor3=Color3.new(1,1,1); btnMin.TextScaled=true; btnMin.Font=Enum.Font.GothamBlack
    local btnX = Instance.new("TextButton", top); btnX.Size=UDim2.new(0,30,0,30); btnX.Position=UDim2.new(1,-30,0,0); btnX.Text="X"; btnX.BackgroundTransparency=1; btnX.TextColor3=Color3.new(1,1,1); btnX.TextScaled=true; btnX.MouseButton1Click:Connect(function() gui:Destroy() guiBloco:Destroy() end)
    local bloco = Instance.new("Frame", guiBloco); bloco.Size=UDim2.new(0,60,0,60); bloco.Position=UDim2.new(0,20,0,200); bloco.BackgroundColor3=Color3.fromRGB(20,5,5); bloco.Visible=false; bloco.Active=true; bloco.Draggable=true; Instance.new("UICorner", bloco).CornerRadius=UDim.new(0,15); local s=Instance.new("UIStroke", bloco); s.Color=Color3.fromRGB(255,0,0); s.Thickness=2
    local lblBloco = Instance.new("TextLabel", bloco); lblBloco.Size=UDim2.new(1,0,1,0); lblBloco.Text="C"; lblBloco.TextScaled=true; lblBloco.BackgroundTransparency=1; lblBloco.TextColor3=Color3.fromRGB(255,0,0); lblBloco.Font=Enum.Font.GothamBlack
    local btnBloco = Instance.new("TextButton", bloco); btnBloco.Size=UDim2.new(1,0,1,0); btnBloco.Text=""; btnBloco.BackgroundTransparency=1
    local left = Instance.new("Frame", main); left.Size=UDim2.new(0,160,1,-30); left.Position=UDim2.new(0,0,0,30); left.BackgroundColor3=Color3.fromRGB(15,5,5)
    local bFarm = Instance.new("TextButton", left); bFarm.Size=UDim2.new(0.9,0,0,32); bFarm.Position=UDim2.new(0.05,0,0,5); bFarm.Text=" ⌂ Farm 700"; bFarm.BackgroundColor3=Color3.fromRGB(60,0,0); bFarm.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", bFarm)
    local bDisc = Instance.new("TextButton", left); bDisc.Size=UDim2.new(0.9,0,0,32); bDisc.Position=UDim2.new(0.05,0,0,42); bDisc.Text=" ⓘ Discord"; bDisc.BackgroundColor3=Color3.fromRGB(20,5,5); bDisc.TextColor3=Color3.fromRGB(150,150,150); Instance.new("UICorner", bDisc)
    local right = Instance.new("Frame", main); right.Size=UDim2.new(1,-165,1,-35); right.Position=UDim2.new(0,165,0,35); right.BackgroundColor3=Color3.fromRGB(20,5,5)
    local sfarm = Instance.new("ScrollingFrame", right); sfarm.Size=UDim2.new(1,0,1,0); sfarm.BackgroundTransparency=1; sfarm.CanvasSize=UDim2.new(0,0,0,1100)
    local sdisc = Instance.new("ScrollingFrame", right); sdisc.Size=UDim2.new(1,0,1,0); sdisc.BackgroundTransparency=1; sdisc.CanvasSize=UDim2.new(0,0,0,500); sdisc.Visible=false

    local autoOn=false; local basePos=nil; local voando,bv,bg,att=false,nil,nil,nil; local alvo="ALL"; local autoLevar=true; local vel=700; local laserOn=true; local wasdOn=false; local wBV,wAtt,wBG=nil,nil,nil; local connWASD=nil; local noclipOn=false; local connNoclip=nil

    local function getPos(m) if m.PrimaryPart then return m.PrimaryPart.Position end for _,p in pairs(m:GetDescendants()) do if p:IsA("BasePart") then return p.Position end end return m:GetBoundingBox() end
    local function getBase() if basePos then return basePos end for _,v in pairs(workspace:GetDescendants()) do if v:IsA("TextLabel") and v.Text:lower():find("sua base") then local m=v:FindFirstAncestorOfClass("Model") if m then return getPos(m)+Vector3.new(0,6,0) end end end return nil end
    local function achar(n) local lista={}; local hrp=plr.Character.HumanoidRootPart.Position; local base=getBase(); if not base then return nil,nil end local alvos=n=="ALL" and {"404","Fachas","Grande Chicle","Infante Fogo"} or {n} for _,al in ipairs(alvos) do for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") and obj.Text:lower():find(al:lower()) then local m=obj:FindFirstAncestorOfClass("Model") if m then local p=getPos(m) if (p-base).Magnitude>60 then table.insert(lista,{m=m,p=p,d=(hrp-p).Magnitude}) end end end end end table.sort(lista,function(a,b) return a.d<b.d end) if #lista>0 then return lista[1].m,lista[1].p end return nil,nil end
    local function voar(pos,meio) local hrp=plr.Character.HumanoidRootPart if not voando then att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero; bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero; plr.Character.Humanoid.PlatformStand=true; voando=true end local chegou=false; local t=0; local c; c=RS.Heartbeat:Connect(function() t+=0.03; if t>12 then c:Disconnect() return end local cur=plr.Character.HumanoidRootPart; local tgt=meio and pos+Vector3.new(0,5,3) or pos+Vector3.new(0,6,0); local dir=tgt-cur.Position; if dir.Magnitude<6 then bv.VectorVelocity=Vector3.zero; chegou=true; c:Disconnect() else bv.VectorVelocity=dir.Unit*vel end end) repeat task.wait() until chegou or t>12 or not autoOn; return chegou end
    local function parar() autoOn=false; if att then att:Destroy() att=nil end; if bv then bv:Destroy() bv=nil end; if bg then bg:Destroy() bg=nil end; if plr.Character.Humanoid then plr.Character.Humanoid.PlatformStand=false end; voando=false end
    -- PEGA NA MÃO ARRUMADO - NÃO FICA NO MEIO DO PALHAÇO E PEGA NA MÃO MESMO
    local function pega(pos,model)
        plr.Character.HumanoidRootPart.CFrame=CFrame.new(pos+Vector3.new(0,7,4))
        task.wait(0.2)
        local pr={}
        for _,o in pairs(model:GetDescendants()) do if o:IsA("ProximityPrompt") then table.insert(pr,o) end end
        if #pr==0 then for _,o in pairs(workspace:GetDescendants()) do if o:IsA("ProximityPrompt") and o.Parent:IsA("BasePart") and (o.Parent.Position-pos).Magnitude<15 then table.insert(pr,o) end end end
        for _,p in pairs(pr) do p.HoldDuration=0; p.MaxActivationDistance=100; p.RequiresLineOfSight=false end
        for i=1,20 do
            pcall(function() for _,p in pairs(pr) do fireproximityprompt(p) end end)
            task.wait(0.05)
            -- VERIFICA SE PEGOU NA MÃO
            for _,v in pairs(plr.Character:GetChildren()) do if v:IsA("Tool") then return true end end
            for _,v in pairs(plr.Backpack:GetChildren()) do if v:IsA("Tool") then v.Parent=plr.Character; return true end end
        end
        return false
    end
    local function start() autoOn=true task.spawn(function() while autoOn do
        -- SE JÁ TÁ COM PALHAÇO NA MÃO, LEVA PRA BASE NA HORA
        local comPalhaco=false
        for _,v in pairs(plr.Character:GetChildren()) do if v:IsA("Tool") then comPalhaco=true end end
        if comPalhaco and autoLevar then
            local b=getBase()
            if b then voar(b,false) task.wait(0.5) end
        else
            local m,p=achar(alvo)
            if m then
                if voar(p,true) then
                    if pega(p,m) then
                        task.wait(0.2)
                        if autoLevar then
                            local b=getBase()
                            if b then
                                print("✅ PEGOU NA MÃO - LEVANDO PRA BASE 700 SPEED!")
                                voar(b,false)
                                task.wait(0.5)
                            end
                        end
                    end
                end
            else
                task.wait(1)
            end
        end
        task.wait(0.2)
    end end) end
    task.spawn(function() while true do if laserOn then for _,o in pairs(workspace:GetDescendants()) do if o.Name:lower():find("laser") then pcall(function() o:Destroy() end) end end end task.wait(0.6) end end)
    local function startWASD() parar(); wasdOn=true; local hrp=plr.Character.HumanoidRootPart; if wAtt then wAtt:Destroy() end if wBV then wBV:Destroy() end if wBG then wBG:Destroy() end; wAtt=Instance.new("Attachment",hrp); wBV=Instance.new("LinearVelocity",hrp); wBV.Attachment0=wAtt; wBV.MaxForce=math.huge; wBV.VectorVelocity=Vector3.zero; wBG=Instance.new("AngularVelocity",hrp); wBG.Attachment0=wAtt; wBG.MaxTorque=math.huge; wBG.AngularVelocity=Vector3.zero; plr.Character.Humanoid.PlatformStand=true; connWASD=RS.Heartbeat:Connect(function() if not wasdOn then return end; local cam=workspace.CurrentCamera; local dir=Vector3.zero; if UIS:IsKeyDown(Enum.KeyCode.W) then dir+=cam.CFrame.LookVector end; if UIS:IsKeyDown(Enum.KeyCode.S) then dir-=cam.CFrame.LookVector end; if UIS:IsKeyDown(Enum.KeyCode.A) then dir-=cam.CFrame.RightVector end; if UIS:IsKeyDown(Enum.KeyCode.D) then dir+=cam.CFrame.RightVector end; if UIS:IsKeyDown(Enum.KeyCode.Space) then dir+=Vector3.new(0,1,0) end; if UIS:IsKeyDown(Enum.KeyCode.LeftShift) then dir+=Vector3.new(0,-1,0) end; if dir.Magnitude>0 then wBV.VectorVelocity=dir.Unit*200 else wBV.VectorVelocity=Vector3.zero end end) end
    local function stopWASD() wasdOn=false; if connWASD then connWASD:Disconnect() connWASD=nil end; if wBV then wBV:Destroy() wBV=nil end; if wAtt then wAtt:Destroy() wAtt=nil end; if wBG then wBG:Destroy() wBG=nil end; if plr.Character.Humanoid then plr.Character.Humanoid.PlatformStand=false end end
    local function startNoclip() noclipOn=true; connNoclip=RS.Stepped:Connect(function() if noclipOn and plr.Character then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end end end) end
    local function stopNoclip() noclipOn=false; if connNoclip then connNoclip:Disconnect() connNoclip=nil end end
    local function minimizarPremium() main.Visible=false; bloco.Visible=true; gui.Enabled=false; parar(); stopWASD(); stopNoclip(); laserOn=false end
    btnMin.MouseButton1Click:Connect(minimizarPremium)
    btnBloco.MouseButton1Click:Connect(function() main.Visible=true; bloco.Visible=false; gui.Enabled=true end)
    bFarm.MouseButton1Click:Connect(function() sfarm.Visible=true; sdisc.Visible=false end)
    bDisc.MouseButton1Click:Connect(function() sfarm.Visible=false; sdisc.Visible=true end)
    local function tog(nome, y, def, cb) local f=Instance.new("Frame", sfarm); f.Size=UDim2.new(1,-10,0,44); f.Position=UDim2.new(0,5,0,y); f.BackgroundColor3=Color3.fromRGB(30,10,10); Instance.new("UICorner", f) local t=Instance.new("TextLabel", f); t.Size=UDim2.new(0.7,0,1,0); t.Position=UDim2.new(0.03,0,0,0); t.Text=nome; t.TextScaled=true; t.BackgroundTransparency=1; t.TextColor3=Color3.fromRGB(255,200,200); t.TextXAlignment=Enum.TextXAlignment.Left local back=Instance.new("Frame", f); back.Size=UDim2.new(0,44,0,22); back.Position=UDim2.new(1,-50,0.5,-11); back.BackgroundColor3=def and Color3.fromRGB(255,0,0) or Color3.fromRGB(60,20,20); Instance.new("UICorner", back).CornerRadius=UDim.new(1,0) local ball=Instance.new("Frame", back); ball.Size=UDim2.new(0,16,0,16); ball.Position=def and UDim2.new(1,-19,0.5,-8) or UDim2.new(0,3,0.5,-8); ball.BackgroundColor3=Color3.new(1,1,1); Instance.new("UICorner", ball).CornerRadius=UDim.new(1,0) local b=Instance.new("TextButton", f); b.Size=UDim2.new(1,0,1,0); b.Text=""; b.BackgroundTransparency=1 local on=def; b.MouseButton1Click:Connect(function() on=not on; back.BackgroundColor3=on and Color3.fromRGB(255,0,0) or Color3.fromRGB(60,20,20); ball.Position=on and UDim2.new(1,-19,0.5,-8) or UDim2.new(0,3,0.5,-8); cb(on) end) end
    local y=0
    tog("🔴 SALVAR BASE - 700", y, true, function(v) if v then basePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0) end end); y+=48
    tog("🔴 AUTO TIRA LASER", y, true, function(v) laserOn=v end); y+=48
    tog("🧱 TIRA PAREDE", y, false, function(v) if v then for _,o in pairs(workspace:GetDescendants()) do if o:IsA("BasePart") and (o.Name:lower():find("wall") or o.Name:lower():find("door")) then local b=getBase() if b and (o.Position-b).Magnitude<150 then o.CanCollide=false; o.Transparency=0.7 end end end end end); y+=48
    tog("👻 NOCLIP / CLIP", y, false, function(v) if v then startNoclip() else stopNoclip() end end); y+=48
    tog("✈️ WASD 200", y, false, function(v) if v then startWASD() else stopWASD() end end); y+=48
    tog("📦 AUTO LEVAR 700 SPEED - PEGA NA MÃO E LEVA", y, true, function(v) autoLevar=v; vel=v and 700 or 190 end); y+=48
    tog("🚀 AUTO IR PALHAÇO 700", y, true, function(v) vel=700 end); y+=48
    tog("🤫 TODOS 4 - 700", y, true, function(v) alvo="ALL"; if v then start() else parar() end end); y+=48
    tog("🤖 404 - 700", y, false, function(v) alvo="404"; if v then start() else parar() end end); y+=48
    tog("🤖 OS FACHAS - 700", y, false, function(v) alvo="Fachas"; if v then start() else parar() end end); y+=48
    tog("🤖 GRANDE CLUBE - 700", y, false, function(v) alvo="Grande Chicle"; if v then start() else parar() end end); y+=48
    tog("🤖 INFERNO - 700", y, false, function(v) alvo="Infante Fogo"; if v then start() else parar() end end); y+=48
    sfarm.CanvasSize=UDim2.new(0,0,0,y)
    task.wait(0.5)
    for _,v in pairs(workspace:GetDescendants()) do if v:IsA("TextLabel") and v.Text:lower():find("sua base") then local m=v:FindFirstAncestorOfClass("Model") if m then basePos=getPos(m)+Vector3.new(0,6,0) end end end
    if not basePos then basePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0) end
    start()
end

-- FREE
local parent = getGuiParent()
local gui = Instance.new("ScreenGui"); gui.Name="CiriloMiFree"; gui.Parent=parent
local guiBloco = Instance.new("ScreenGui"); guiBloco.Name="CiriloMiFreeBloco"; guiBloco.Parent=parent
local main = Instance.new("Frame", gui); main.Size=UDim2.new(0,560,0,500); main.Position=UDim2.new(0.5,-280,0.5,-250); main.BackgroundColor3=Color3.fromRGB(15,15,15); main.Active=true; main.Draggable=true; Instance.new("UICorner", main); Instance.new("UIStroke", main).Color=Color3.fromRGB(80,120,255)
local top = Instance.new("Frame", main); top.Size=UDim2.new(1,0,0,30); top.BackgroundColor3=Color3.fromRGB(10,10,10); Instance.new("UICorner", top)
local title = Instance.new("TextLabel", top); title.Size=UDim2.new(0.6,0,1,0); title.Position=UDim2.new(0.02,0,0,0); title.Text="cirilo mi : FREE - PEGA NA MÃO E LEVA"; title.TextScaled=true; title.BackgroundTransparency=1; title.TextColor3=Color3.fromRGB(200,200,200); title.TextXAlignment=Enum.TextXAlignment.Left; title.Font=Enum.Font.GothamBlack
local btnMin = Instance.new("TextButton", top); btnMin.Size=UDim2.new(0,30,0,30); btnMin.Position=UDim2.new(1,-60,0,0); btnMin.Text="—"; btnMin.BackgroundTransparency=1; btnMin.TextColor3=Color3.new(1,1,1); btnMin.TextScaled=true; btnMin.Font=Enum.Font.GothamBlack
local btnX = Instance.new("TextButton", top); btnX.Size=UDim2.new(0,30,0,30); btnX.Position=UDim2.new(1,-30,0,0); btnX.Text="X"; btnX.BackgroundTransparency=1; btnX.TextColor3=Color3.new(1,1,1); btnX.TextScaled=true; btnX.MouseButton1Click:Connect(function() gui:Destroy() guiBloco:Destroy() end)
local bloco = Instance.new("Frame", guiBloco); bloco.Size=UDim2.new(0,60,0,60); bloco.Position=UDim2.new(0,20,0,200); bloco.BackgroundColor3=Color3.fromRGB(15,15,15); bloco.Visible=false; bloco.Active=true; bloco.Draggable=true; Instance.new("UICorner", bloco).CornerRadius=UDim.new(0,15); local s=Instance.new("UIStroke", bloco); s.Color=Color3.fromRGB(80,120,255); s.Thickness=2
local lblBloco = Instance.new("TextLabel", bloco); lblBloco.Size=UDim2.new(1,0,1,0); lblBloco.Text="C"; lblBloco.TextScaled=true; lblBloco.BackgroundTransparency=1; lblBloco.TextColor3=Color3.fromRGB(80,120,255); lblBloco.Font=Enum.Font.GothamBlack
local btnBloco = Instance.new("TextButton", bloco); btnBloco.Size=UDim2.new(1,0,1,0); btnBloco.Text=""; btnBloco.BackgroundTransparency=1
local left = Instance.new("Frame", main); left.Size=UDim2.new(0,160,1,-30); left.Position=UDim2.new(0,0,0,30); left.BackgroundColor3=Color3.fromRGB(12,12,12)
local bDisc = Instance.new("TextButton", left); bDisc.Size=UDim2.new(0.9,0,0,32); bDisc.Position=UDim2.new(0.05,0,0,5); bDisc.Text=" ⓘ Discord"; bDisc.BackgroundColor3=Color3.fromRGB(25,25,25); bDisc.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", bDisc)
local bFarm = Instance.new("TextButton", left); bFarm.Size=UDim2.new(0.9,0,0,32); bFarm.Position=UDim2.new(0.05,0,0,42); bFarm.Text=" ⌂ Farm FREE"; bFarm.BackgroundColor3=Color3.fromRGB(18,18,18); bFarm.TextColor3=Color3.fromRGB(120,120,120); Instance.new("UICorner", bFarm)
local right = Instance.new("Frame", main); right.Size=UDim2.new(1,-165,1,-35); right.Position=UDim2.new(0,165,0,35); right.BackgroundColor3=Color3.fromRGB(15,15,15)
local sDisc = Instance.new("ScrollingFrame", right); sDisc.Size=UDim2.new(1,0,1,0); sDisc.BackgroundTransparency=1; sDisc.CanvasSize=UDim2.new(0,0,0,500)
local sFarm = Instance.new("ScrollingFrame", right); sFarm.Size=UDim2.new(1,0,1,0); sFarm.BackgroundTransparency=1; sFarm.CanvasSize=UDim2.new(0,0,0,700); sFarm.Visible=false
local lb1 = Instance.new("TextLabel", sDisc); lb1.Size=UDim2.new(0.9,0,0,25); lb1.Position=UDim2.new(0.05,0,0,10); lb1.Text="🔑 PREMIUM KEY - Só Dono"; lb1.TextScaled=true; lb1.BackgroundTransparency=1; lb1.TextColor3=Color3.fromRGB(255,215,0)
local boxKey = Instance.new("TextBox", sDisc); boxKey.Size=UDim2.new(0.9,0,0,35); boxKey.Position=UDim2.new(0.05,0,0,35); boxKey.PlaceholderText="Digite sua Key..."; boxKey.TextScaled=true; boxKey.BackgroundColor3=Color3.fromRGB(22,22,22); boxKey.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", boxKey)
local btnKey = Instance.new("TextButton", sDisc); btnKey.Size=UDim2.new(0.9,0,0,35); btnKey.Position=UDim2.new(0.05,0,0,75); btnKey.Text="🔓 ATIVAR PREMIUM 700 + WASD 200"; btnKey.BackgroundColor3=Color3.fromRGB(255,0,0); btnKey.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", btnKey)
btnKey.MouseButton1Click:Connect(function() if boxKey.Text=="0808" then criarPremium() end end)
bDisc.MouseButton1Click:Connect(function() sDisc.Visible=true; sFarm.Visible=false end)
bFarm.MouseButton1Click:Connect(function() sDisc.Visible=false; sFarm.Visible=true end)

local autoOn=false; local basePos=nil; local voando,bv,bg,att=false,nil,nil,nil; local alvo="ALL"; local autoLevar=true; local noclipOn=false; local connNoclip=nil
local function getPos2(m) if m.PrimaryPart then return m.PrimaryPart.Position end for _,p in pairs(m:GetDescendants()) do if p:IsA("BasePart") then return p.Position end end return m:GetBoundingBox() end
local function getBase2() if basePos then return basePos end for _,v in pairs(workspace:GetDescendants()) do if v:IsA("TextLabel") and v.Text:lower():find("sua base") then local m=v:FindFirstAncestorOfClass("Model") if m then return getPos2(m)+Vector3.new(0,6,0) end end end return nil end
local function achar2(n) local lista={}; local hrp=plr.Character.HumanoidRootPart.Position; local base=getBase2(); if not base then return nil,nil end local alvos=n=="ALL" and {"404","Fachas","Grande Chicle","Infante Fogo"} or {n} for _,al in ipairs(alvos) do for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") and obj.Text:lower():find(al:lower()) then local m=obj:FindFirstAncestorOfClass("Model") if m then local p=getPos2(m) if (p-base).Magnitude>60 then table.insert(lista,{m=m,p=p,d=(hrp-p).Magnitude}) end end end end end table.sort(lista,function(a,b) return a.d<b.d end) if #lista>0 then return lista[1].m,lista[1].p end return nil,nil end
local function voar2(pos,meio) local hrp=plr.Character.HumanoidRootPart if not voando then att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero; bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero; plr.Character.Humanoid.PlatformStand=true; voando=true end local chegou=false; local t=0; local c; c=RS.Heartbeat:Connect(function() t+=0.03; if t>10 then c:Disconnect() return end local cur=plr.Character.HumanoidRootPart; local tgt=meio and pos+Vector3.new(0,5,3) or pos+Vector3.new(0,6,0); local dir=tgt-cur.Position; if dir.Magnitude<6 then bv.VectorVelocity=Vector3.zero; chegou=true; c:Disconnect() else bv.VectorVelocity=dir.Unit*190 end end) repeat task.wait() until chegou or t>10 or not autoOn; return chegou end
local function parar2() autoOn=false; if att then att:Destroy() att=nil end; if bv then bv:Destroy() bv=nil end; if bg then bg:Destroy() bg=nil end; if plr.Character.Humanoid then plr.Character.Humanoid.PlatformStand=false end; voando=false end
local function pega2(pos,model) plr.Character.HumanoidRootPart.CFrame=CFrame.new(pos+Vector3.new(0,7,4)); task.wait(0.25); local pr={}; for _,o in pairs(model:GetDescendants()) do if o:IsA("ProximityPrompt") then table.insert(pr,o) end end; if #pr==0 then for _,o in pairs(workspace:GetDescendants()) do if o:IsA("ProximityPrompt") and o.Parent:IsA("BasePart") and (o.Parent.Position-pos).Magnitude<15 then table.insert(pr,o) end end end; for _,p in pairs(pr) do p.HoldDuration=0; p.MaxActivationDistance=100; p.RequiresLineOfSight=false end; for i=1,20 do pcall(function() for _,p in pairs(pr) do fireproximityprompt(p) end end) task.wait(0.06); for _,v in pairs(plr.Character:GetChildren()) do if v:IsA("Tool") then return true end end; for _,v in pairs(plr.Backpack:GetChildren()) do if v:IsA("Tool") then v.Parent=plr.Character; return true end end end; return false end
local function start2() autoOn=true task.spawn(function() while autoOn do
    local comPalhaco=false; for _,v in pairs(plr.Character:GetChildren()) do if v:IsA("Tool") then comPalhaco=true end end
    if comPalhaco and autoLevar then local b=getBase2(); if b then voar2(b,false) task.wait(0.5) end else local m,p=achar2(alvo); if m then if voar2(p,true) then if pega2(p,m) then if autoLevar then local b=getBase2(); if b then voar2(b,false) task.wait(1) end end end end else task.wait(1) end end; task.wait(0.3)
end end) end
local function startNoclip2() noclipOn=true; connNoclip=RS.Stepped:Connect(function() if noclipOn and plr.Character then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end end end) end
local function stopNoclip2() noclipOn=false; if connNoclip then connNoclip:Disconnect() connNoclip=nil end end
local function minimizarFree() main.Visible=false; bloco.Visible=true; gui.Enabled=false; parar2(); stopNoclip2() end
btnMin.MouseButton1Click:Connect(minimizarFree)
btnBloco.MouseButton1Click:Connect(function() main.Visible=true; bloco.Visible=false; gui.Enabled=true end)
local function tog2(nome, y, def, cb) local f=Instance.new("Frame", sFarm); f.Size=UDim2.new(1,-10,0,44); f.Position=UDim2.new(0,5,0,y); f.BackgroundColor3=Color3.fromRGB(22,22,22); Instance.new("UICorner", f) local t=Instance.new("TextLabel", f); t.Size=UDim2.new(0.7,0,1,0); t.Position=UDim2.new(0.03,0,0,0); t.Text=nome; t.TextScaled=true; t.BackgroundTransparency=1; t.TextColor3=Color3.fromRGB(200,200,200); t.TextXAlignment=Enum.TextXAlignment.Left local back=Instance.new("Frame", f); back.Size=UDim2.new(0,44,0,22); back.Position=UDim2.new(1,-50,0.5,-11); back.BackgroundColor3=def and Color3.fromRGB(80,120,255) or Color3.fromRGB(40,40,40); Instance.new("UICorner", back).CornerRadius=UDim.new(1,0) local ball=Instance.new("Frame", back); ball.Size=UDim2.new(0,16,0,16); ball.Position=def and UDim2.new(1,-19,0.5,-8) or UDim2.new(0,3,0.5,-8); ball.BackgroundColor3=Color3.new(1,1,1); Instance.new("UICorner", ball).CornerRadius=UDim.new(1,0) local b=Instance.new("TextButton", f); b.Size=UDim2.new(1,0,1,0); b.Text=""; b.BackgroundTransparency=1 local on=def; b.MouseButton1Click:Connect(function() on=not on; back.BackgroundColor3=on and Color3.fromRGB(80,120,255) or Color3.fromRGB(40,40,40); ball.Position=on and UDim2.new(1,-19,0.5,-8) or UDim2.new(0,3,0.5,-8); cb(on) end) end
local y=0
tog2("💾 Salvar Base", y, true, function(v) if v then basePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0) end end); y+=48
tog2("👻 NOCLIP / CLIP", y, false, function(v) if v then startNoclip2() else stopNoclip2() end end); y+=48
tog2("📦 AUTO LEVAR 190 - PEGA NA MÃO E LEVA", y, true, function(v) autoLevar=v end); y+=48
tog2("🤫 TODOS 4 - 404 + FACHAS + GRANDE + INFERNO", y, true, function(v) alvo="ALL"; if v then start2() else parar2() end end); y+=48
tog2("🤖 404", y, false, function(v) alvo="404"; if v then start2() else parar2() end end); y+=48
tog2("🤖 OS FACHAS", y, false, function(v) alvo="Fachas"; if v then start2() else parar2() end end); y+=48
tog2("🤖 GRANDE CLUBE", y, false, function(v) alvo="Grande Chicle"; if v then start2() else parar2() end end); y+=48
tog2("🤖 INFERNO", y, false, function(v) alvo="Infante Fogo"; if v then start2() else parar2() end end); y+=48
sFarm.CanvasSize=UDim2.new(0,0,0,y)
task.wait(0.5)
for _,v in pairs(workspace:GetDescendants()) do if v:IsA("TextLabel") and v.Text:lower():find("sua base") then local m=v:FindFirstAncestorOfClass("Model") if m then basePos=getPos2(m)+Vector3.new(0,6,0) end end end
if not basePos then basePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0) end
start2()
