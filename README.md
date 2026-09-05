-- V48 CIRILO MI - PREMIUM INDICE 34 + ESP + TP + INVIS ROUBAR + 700
local plr = game.Players.LocalPlayer
local RS = game:GetService("RunService")
local UIS = game:GetService("UserInputService")
local TeleportService = game:GetService("TeleportService")
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
    local main = Instance.new("Frame", gui); main.Size=UDim2.new(0,600,0,640); main.Position=UDim2.new(0.5,-300,0.5,-320); main.BackgroundColor3=Color3.fromRGB(20,5,5); main.Active=true; main.Draggable=true; Instance.new("UICorner", main); Instance.new("UIStroke", main).Color=Color3.fromRGB(255,215,0)
    local top = Instance.new("Frame", main); top.Size=UDim2.new(1,0,0,30); top.BackgroundColor3=Color3.fromRGB(40,0,0); Instance.new("UICorner", top)
    local title = Instance.new("TextLabel", top); title.Size=UDim2.new(0.7,0,1,0); title.Position=UDim2.new(0.02,0,0,0); title.Text="cirilo mi : PREMIUM INVIS + INDICE + ESP + TP 700"; title.TextScaled=true; title.BackgroundTransparency=1; title.TextColor3=Color3.fromRGB(255,215,0); title.TextXAlignment=Enum.TextXAlignment.Left; title.Font=Enum.Font.GothamBlack
    local btnMin = Instance.new("TextButton", top); btnMin.Size=UDim2.new(0,30,0,30); btnMin.Position=UDim2.new(1,-60,0,0); btnMin.Text="—"; btnMin.BackgroundTransparency=1; btnMin.TextColor3=Color3.new(1,1,1); btnMin.TextScaled=true; btnMin.Font=Enum.Font.GothamBlack
    local btnX = Instance.new("TextButton", top); btnX.Size=UDim2.new(0,30,0,30); btnX.Position=UDim2.new(1,-30,0,0); btnX.Text="X"; btnX.BackgroundTransparency=1; btnX.TextColor3=Color3.new(1,1,1); btnX.TextScaled=true; btnX.MouseButton1Click:Connect(function() gui:Destroy() guiBloco:Destroy() end)
    local bloco = Instance.new("Frame", guiBloco); bloco.Size=UDim2.new(0,60,0,60); bloco.Position=UDim2.new(0,20,0,200); bloco.BackgroundColor3=Color3.fromRGB(20,5,5); bloco.Visible=false; bloco.Active=true; bloco.Draggable=true; Instance.new("UICorner", bloco).CornerRadius=UDim.new(0,15); local s=Instance.new("UIStroke", bloco); s.Color=Color3.fromRGB(255,215,0); s.Thickness=2
    local lblBloco = Instance.new("TextLabel", bloco); lblBloco.Size=UDim2.new(1,0,1,0); lblBloco.Text="C"; lblBloco.TextScaled=true; lblBloco.BackgroundTransparency=1; lblBloco.TextColor3=Color3.fromRGB(255,215,0); lblBloco.Font=Enum.Font.GothamBlack
    local btnBloco = Instance.new("TextButton", bloco); btnBloco.Size=UDim2.new(1,0,1,0); btnBloco.Text=""; btnBloco.BackgroundTransparency=1
    local left = Instance.new("Frame", main); left.Size=UDim2.new(0,160,1,-30); left.Position=UDim2.new(0,0,0,30); left.BackgroundColor3=Color3.fromRGB(15,5,5)
    local bFarm = Instance.new("TextButton", left); bFarm.Size=UDim2.new(0.9,0,0,26); bFarm.Position=UDim2.new(0.05,0,0,5); bFarm.Text=" ⌂ Farm 700"; bFarm.BackgroundColor3=Color3.fromRGB(60,0,0); bFarm.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", bFarm)
    local bIndice = Instance.new("TextButton", left); bIndice.Size=UDim2.new(0.9,0,0,26); bIndice.Position=UDim2.new(0.05,0,0,35); bIndice.Text=" 📑 Índice 22/34"; bIndice.BackgroundColor3=Color3.fromRGB(20,5,5); bIndice.TextColor3=Color3.fromRGB(150,150,150); Instance.new("UICorner", bIndice)
    local bESP = Instance.new("TextButton", left); bESP.Size=UDim2.new(0.9,0,0,26); bESP.Position=UDim2.new(0.05,0,0,65); bESP.Text=" 👁 ESP"; bESP.BackgroundColor3=Color3.fromRGB(20,5,5); bESP.TextColor3=Color3.fromRGB(150,150,150); Instance.new("UICorner", bESP)
    local bTP = Instance.new("TextButton", left); bTP.Size=UDim2.new(0.9,0,0,26); bTP.Position=UDim2.new(0.05,0,0,95); bTP.Text=" 📍 TP"; bTP.BackgroundColor3=Color3.fromRGB(20,5,5); bTP.TextColor3=Color3.fromRGB(150,150,150); Instance.new("UICorner", bTP)
    local bInvis = Instance.new("TextButton", left); bInvis.Size=UDim2.new(0.9,0,0,26); bInvis.Position=UDim2.new(0.05,0,0,125); bInvis.Text=" 🫥 Invis"; bInvis.BackgroundColor3=Color3.fromRGB(20,5,5); bInvis.TextColor3=Color3.fromRGB(150,150,150); Instance.new("UICorner", bInvis)
    local right = Instance.new("Frame", main); right.Size=UDim2.new(1,-165,1,-35); right.Position=UDim2.new(0,165,0,35); right.BackgroundColor3=Color3.fromRGB(20,5,5)
    local sfarm = Instance.new("ScrollingFrame", right); sfarm.Size=UDim2.new(1,0,1,0); sfarm.BackgroundTransparency=1; sfarm.CanvasSize=UDim2.new(0,0,0,1100)
    local sindice = Instance.new("ScrollingFrame", right); sindice.Size=UDim2.new(1,0,1,0); sindice.BackgroundTransparency=1; sindice.CanvasSize=UDim2.new(0,0,0,1200); sindice.Visible=false
    local sESP = Instance.new("ScrollingFrame", right); sESP.Size=UDim2.new(1,0,1,0); sESP.BackgroundTransparency=1; sESP.CanvasSize=UDim2.new(0,0,0,500); sESP.Visible=false
    local sTP = Instance.new("ScrollingFrame", right); sTP.Size=UDim2.new(1,0,1,0); sTP.BackgroundTransparency=1; sTP.CanvasSize=UDim2.new(0,0,0,1500); sTP.Visible=false
    local sInvis = Instance.new("ScrollingFrame", right); sInvis.Size=UDim2.new(1,0,1,0); sInvis.BackgroundTransparency=1; sInvis.CanvasSize=UDim2.new(0,0,0,500); sInvis.Visible=false

    local autoOn=false; local basePos=nil; local voando,bv,bg,att=false,nil,nil,nil; local alvo="ALL"; local autoLevar=false; local vel=700; local laserOn=false; local wasdOn=false; local wBV,wAtt,wBG=nil,nil,nil; local connWASD=nil; local noclipOn=false; local connNoclip=nil; local melhorEKitaOn=false; local espOn=false; local connESP=nil; local invisOn=false; local fakeChar=nil

    local function getPos(m) if m.PrimaryPart then return m.PrimaryPart.Position end for _,p in pairs(m:GetDescendants()) do if p:IsA("BasePart") then return p.Position end end return m:GetBoundingBox() end
    local function getBase() if basePos then return basePos end for _,v in pairs(workspace:GetDescendants()) do if v:IsA("TextLabel") and v.Text:lower():find("sua base") then local m=v:FindFirstAncestorOfClass("Model") if m then return getPos(m)+Vector3.new(0,6,0) end end end return nil end
    local listaIndice = {"404","Os Fachas","O Grande Clube","Grande Chicle","Infante Fogo","Os Arbustos","Ian","Fede Vigovani","Luli e Pede","Os Minicos","Luli Alasni","Asarboool","Azazalino","Chimpanzini","Tralalero","Espressona","Duffyn","Ballerina","Tung Tung","Boneca","Lol","Padrão Secreto","Padrão Divino","Padrão Ouro","Padrão Diamante","Arco-íris","Luli","Pede","Mini","Fogo","Grande","Misterio","X2 Torture","MELHOR"}
    local function acharMelhor() local melhorM, melhorP, melhorValor = nil, nil, -1; local base = getBase(); if not base then return nil,nil end; for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") then local txt = obj.Text:lower(); for _,nome in ipairs(listaIndice) do if txt:find(nome:lower()) then local model = obj:FindFirstAncestorOfClass("Model"); if model then local pos = getPos(model); if (pos-base).Magnitude>60 then local valor = 0; for _,lbl in pairs(model:GetDescendants()) do if lbl:IsA("TextLabel") then local t = lbl.Text; if t:lower():find("grande") then valor+=500000 end; if t:lower():find("infante") then valor+=800000 end; if t:lower():find("404") then valor+=300000 end; if t:lower():find("secreto") or t:lower():find("divino") then valor+=1000000 end end end; if valor>melhorValor then melhorValor=valor; melhorM=model; melhorP=pos end end end end end end end; return melhorM, melhorP end
    local function achar(n) if n=="MELHOR" then return acharMelhor() end; local lista={}; local hrp=plr.Character.HumanoidRootPart.Position; local base=getBase(); if not base then return nil,nil end local alvos=n=="ALL" and listaIndice or {n} for _,al in ipairs(alvos) do for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") and obj.Text:lower():find(al:lower()) then local m=obj:FindFirstAncestorOfClass("Model") if m then local p=getPos(m) if (p-base).Magnitude>60 then table.insert(lista,{m=m,p=p,d=(hrp-p).Magnitude}) end end end end end table.sort(lista,function(a,b) return a.d<b.d end) if #lista>0 then return lista[1].m,lista[1].p end return nil,nil end
    local function voar(pos,meio) local hrp=plr.Character.HumanoidRootPart if not voando then att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero; bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero; plr.Character.Humanoid.PlatformStand=true; voando=true end local chegou=false; local t=0; local c; c=RS.Heartbeat:Connect(function() t+=0.03; if t>10 then c:Disconnect() return end local cur=plr.Character.HumanoidRootPart; local tgt=meio and pos+Vector3.new(0,5,3) or pos+Vector3.new(0,6,0); local dir=tgt-cur.Position; if dir.Magnitude<6 then bv.VectorVelocity=Vector3.zero; chegou=true; c:Disconnect() else bv.VectorVelocity=dir.Unit*vel end end) repeat task.wait() until chegou or t>10 or not autoOn; return chegou end
    local function voltarBase() local base=getBase(); if not base then return end; if att then att:Destroy() att=nil end; if bv then bv:Destroy() bv=nil end; if bg then bg:Destroy() bg=nil end; voando=false; if plr.Character.Humanoid then plr.Character.Humanoid.PlatformStand=false end; if invisOn then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") and v.Name~="HumanoidRootPart" then v.Transparency=0 end end end; for i=1,3 do pcall(function() plr.Character.HumanoidRootPart.CFrame=CFrame.new(base+Vector3.new(0,8+i*2,0)) end) task.wait(0.3) end; task.wait(1.5) end
    local function parar() autoOn=false; if att then att:Destroy() att=nil end; if bv then bv:Destroy() bv=nil end; if bg then bg:Destroy() bg=nil end; if plr.Character.Humanoid then plr.Character.Humanoid.PlatformStand=false end; voando=false end

    -- PEGA COM INVIS
    local function pega(pos,model)
        if invisOn then
            -- Deixa invisível e cria clone falso parado no palhaço pros outros
            for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") and v.Name~="HumanoidRootPart" then v.Transparency=1 end end
            if fakeChar then fakeChar:Destroy() end
            fakeChar = Instance.new("Part", workspace); fakeChar.Name="FakeStand"; fakeChar.Anchored=true; fakeChar.CanCollide=false; fakeChar.Transparency=1; fakeChar.Position=pos+Vector3.new(0,3,0)
            local bb=Instance.new("BillboardGui",fakeChar); bb.Size=UDim2.new(0,100,0,50); bb.AlwaysOnTop=true
            local lbl=Instance.new("TextLabel",bb); lbl.Size=UDim2.new(1,0,1,0); lbl.BackgroundTransparency=1; lbl.Text=plr.Name.." [Parado]"; lbl.TextColor3=Color3.fromRGB(255,255,255); lbl.TextScaled=true
            -- Cabeça pra baixo pra você
            plr.Character.HumanoidRootPart.CFrame=CFrame.new(pos+Vector3.new(0,7,4)) * CFrame.Angles(math.rad(180),0,0)
        else
            plr.Character.HumanoidRootPart.CFrame=CFrame.new(pos+Vector3.new(0,7,4))
        end
        task.wait(0.25)
        local pr={}; for _,o in pairs(model:GetDescendants()) do if o:IsA("ProximityPrompt") then table.insert(pr,o) end end
        if #pr==0 then for _,o in pairs(workspace:GetDescendants()) do if o:IsA("ProximityPrompt") and o.Parent:IsA("BasePart") and (o.Parent.Position-pos).Magnitude<15 then table.insert(pr,o) end end end
        for _,p in pairs(pr) do p.HoldDuration=0; p.MaxActivationDistance=100; p.RequiresLineOfSight=false end
        for i=1,20 do
            pcall(function() for _,p in pairs(pr) do fireproximityprompt(p) end end)
            task.wait(0.06)
            for _,v in pairs(plr.Character:GetChildren()) do if v:IsA("Tool") then if fakeChar then fakeChar:Destroy() fakeChar=nil end; if invisOn then for _,b in pairs(plr.Character:GetDescendants()) do if b:IsA("BasePart") then b.Transparency=0 end end; plr.Character.HumanoidRootPart.CFrame=CFrame.new(plr.Character.HumanoidRootPart.Position) * CFrame.Angles(math.rad(180),0,0) end; return true end end
            for _,v in pairs(plr.Backpack:GetChildren()) do if v:IsA("Tool") then v.Parent=plr.Character; if fakeChar then fakeChar:Destroy() fakeChar=nil end; if invisOn then for _,b in pairs(plr.Character:GetDescendants()) do if b:IsA("BasePart") then b.Transparency=0 end end end; return true end end
        end
        if fakeChar then fakeChar:Destroy() fakeChar=nil end
        if invisOn then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.Transparency=0 end end end
        return false
    end

    local function start() autoOn=true task.spawn(function() while autoOn do local com=false; for _,v in pairs(plr.Character:GetChildren()) do if v:IsA("Tool") then com=true end end; if com and autoLevar then voltarBase(); if alvo=="MELHOR" and melhorEKitaOn then task.wait(2); pcall(function() TeleportService:Teleport(game.PlaceId, plr) end) autoOn=false; return end else local m,p=achar(alvo); if m then if voar(p,true) then if pega(p,m) then if autoLevar then voltarBase() if alvo=="MELHOR" and melhorEKitaOn then task.wait(2); pcall(function() TeleportService:Teleport(game.PlaceId, plr) end) autoOn=false; return end end end end else task.wait(1) end end; task.wait(0.3) end end) end

    local function startESP() espOn=true; connESP=RS.Heartbeat:Connect(function() if not espOn then return end; for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") then for _,nome in ipairs(listaIndice) do if obj.Text:lower():find(nome:lower()) then local model=obj:FindFirstAncestorOfClass("Model") if model and not model:FindFirstChild("CiriloESP") then local hl=Instance.new("Highlight",model); hl.Name="CiriloESP"; hl.FillColor=Color3.fromRGB(255,215,0); hl.OutlineColor=Color3.fromRGB(255,0,0); hl.FillTransparency=0.5; local bb=Instance.new("BillboardGui",model); bb.Name="CiriloESPBill"; bb.Size=UDim2.new(0,200,0,50); bb.StudsOffset=Vector3.new(0,5,0); bb.AlwaysOnTop=true; local tl=Instance.new("TextLabel",bb); tl.Size=UDim2.new(1,0,1,0); tl.BackgroundTransparency=1; tl.Text=obj.Text; tl.TextColor3=Color3.fromRGB(255,215,0); tl.TextScaled=true; tl.Font=Enum.Font.GothamBlack end end end end end end) end
    local function stopESP() espOn=false; if connESP then connESP:Disconnect() connESP=nil end; for _,m in pairs(workspace:GetDescendants()) do if m:FindFirstChild("CiriloESP") then m.CiriloESP:Destroy() end if m:FindFirstChild("CiriloESPBill") then m.CiriloESPBill:Destroy() end end end
    task.spawn(function() while true do if laserOn then for _,o in pairs(workspace:GetDescendants()) do if o.Name:lower():find("laser") then pcall(function() o:Destroy() end) end end end task.wait(0.6) end end)
    local function startWASD() parar(); wasdOn=true; local hrp=plr.Character.HumanoidRootPart; if wAtt then wAtt:Destroy() end if wBV then wBV:Destroy() end if wBG then wBG:Destroy() end; wAtt=Instance.new("Attachment",hrp); wBV=Instance.new("LinearVelocity",hrp); wBV.Attachment0=wAtt; wBV.MaxForce=math.huge; wBV.VectorVelocity=Vector3.zero; wBG=Instance.new("AngularVelocity",hrp); wBG.Attachment0=wAtt; wBG.MaxTorque=math.huge; wBG.AngularVelocity=Vector3.zero; plr.Character.Humanoid.PlatformStand=true; connWASD=RS.Heartbeat:Connect(function() if not wasdOn then return end; local cam=workspace.CurrentCamera; local dir=Vector3.zero; if UIS:IsKeyDown(Enum.KeyCode.W) then dir+=cam.CFrame.LookVector end; if UIS:IsKeyDown(Enum.KeyCode.S) then dir-=cam.CFrame.LookVector end; if UIS:IsKeyDown(Enum.KeyCode.A) then dir-=cam.CFrame.RightVector end; if UIS:IsKeyDown(Enum.KeyCode.D) then dir+=cam.CFrame.RightVector end; if UIS:IsKeyDown(Enum.KeyCode.Space) then dir+=Vector3.new(0,1,0) end; if UIS:IsKeyDown(Enum.KeyCode.LeftShift) then dir+=Vector3.new(0,-1,0) end; if dir.Magnitude>0 then wBV.VectorVelocity=dir.Unit*200 else wBV.VectorVelocity=Vector3.zero end end) end
    local function stopWASD() wasdOn=false; if connWASD then connWASD:Disconnect() connWASD=nil end; if wBV then wBV:Destroy() wBV=nil end; if wAtt then wAtt:Destroy() wAtt=nil end; if wBG then wBG:Destroy() wBG=nil end; if plr.Character.Humanoid then plr.Character.Humanoid.PlatformStand=false end end
    local function startNoclip() noclipOn=true; connNoclip=RS.Stepped:Connect(function() if noclipOn and plr.Character then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end end end) end
    local function stopNoclip() noclipOn=false; if connNoclip then connNoclip:Disconnect() connNoclip=nil end end
    local function startInvis() invisOn=true; game.StarterGui:SetCore("SendNotification",{Title="🫥 INVIS ON", Text="Parado pros outros + cabeça baixo pra você!", Duration=3}) end
    local function stopInvis() invisOn=false; if fakeChar then fakeChar:Destroy() fakeChar=nil end; for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.Transparency=0 end end end
    local function minimizarPremium() main.Visible=false; bloco.Visible=true; gui.Enabled=false; parar(); stopWASD(); stopNoclip(); stopESP(); stopInvis(); laserOn=false; autoLevar=false; melhorEKitaOn=false end
    btnMin.MouseButton1Click:Connect(minimizarPremium)
    btnBloco.MouseButton1Click:Connect(function() main.Visible=true; bloco.Visible=false; gui.Enabled=true end)
    local function showOnly(f) sfarm.Visible=false; sindice.Visible=false; sESP.Visible=false; sTP.Visible=false; sInvis.Visible=false; f.Visible=true end
    bFarm.MouseButton1Click:Connect(function() showOnly(sfarm) end)
    bIndice.MouseButton1Click:Connect(function() showOnly(sindice) end)
    bESP.MouseButton1Click:Connect(function() showOnly(sESP) end)
    bTP.MouseButton1Click:Connect(function() showOnly(sTP) end)
    bInvis.MouseButton1Click:Connect(function() showOnly(sInvis) end)
    local function tog(nome, y, def, cb, parent) parent=parent or sfarm; local f=Instance.new("Frame", parent); f.Size=UDim2.new(1,-10,0,44); f.Position=UDim2.new(0,5,0,y); f.BackgroundColor3=Color3.fromRGB(30,10,10); Instance.new("UICorner", f) local t=Instance.new("TextLabel", f); t.Size=UDim2.new(0.7,0,1,0); t.Position=UDim2.new(0.03,0,0,0); t.Text=nome; t.TextScaled=true; t.BackgroundTransparency=1; t.TextColor3=Color3.fromRGB(255,200,200); t.TextXAlignment=Enum.TextXAlignment.Left local back=Instance.new("Frame", f); back.Size=UDim2.new(0,44,0,22); back.Position=UDim2.new(1,-50,0.5,-11); back.BackgroundColor3=def and Color3.fromRGB(255,0,0) or Color3.fromRGB(60,20,20); Instance.new("UICorner", back).CornerRadius=UDim.new(1,0) local ball=Instance.new("Frame", back); ball.Size=UDim2.new(0,16,0,16); ball.Position=def and UDim2.new(1,-19,0.5,-8) or UDim2.new(0,3,0.5,-8); ball.BackgroundColor3=Color3.new(1,1,1); Instance.new("UICorner", ball).CornerRadius=UDim.new(1,0) local b=Instance.new("TextButton", f); b.Size=UDim2.new(1,0,1,0); b.Text=""; b.BackgroundTransparency=1 local on=def; b.MouseButton1Click:Connect(function() on=not on; back.BackgroundColor3=on and Color3.fromRGB(255,0,0) or Color3.fromRGB(60,20,20); ball.Position=on and UDim2.new(1,-19,0.5,-8) or UDim2.new(0,3,0.5,-8); cb(on) end) end
    local y=0
    tog("💾 SALVAR BASE - OFF - IGUAL FREE", y, false, function(v) if v then basePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0) end end); y+=48
    tog("🔴 AUTO TIRA LASER - OFF", y, false, function(v) laserOn=v end); y+=48
    tog("👻 NOCLIP / CLIP - OFF", y, false, function(v) if v then startNoclip() else stopNoclip() end end); y+=48
    tog("✈️ WASD 200 - OFF", y, false, function(v) if v then startWASD() else stopWASD() end end); y+=48
    tog("📦 AUTO LEVAR 700 - OFF - IGUAL FREE", y, false, function(v) autoLevar=v; vel=700 end); y+=48
    tog("🏆 MELHOR PALHAÇO + KITA - OFF - 700", y, false, function(v) melhorEKitaOn=v; alvo="MELHOR"; if v then start() else parar() end end); y+=48
    tog("🤫 TODOS 4 - 700 - OFF", y, false, function(v) alvo="ALL"; if v then start() else parar() end end); y+=48
    sfarm.CanvasSize=UDim2.new(0,0,0,y)
    local y2=0
    local lblIndice = Instance.new("TextLabel", sindice); lblIndice.Size=UDim2.new(0.9,0,0,30); lblIndice.Position=UDim2.new(0.05,0,0,y2); lblIndice.Text="📑 ÍNDICE 22/34 - AUTO ROUBAR SELECIONADO"; lblIndice.TextScaled=true; lblIndice.BackgroundTransparency=1; lblIndice.TextColor3=Color3.fromRGB(255,215,0); lblIndice.Font=Enum.Font.GothamBlack; y2+=35
    for _,nome in ipairs(listaIndice) do
        if nome~="MELHOR" then
            local f=Instance.new("Frame", sindice); f.Size=UDim2.new(1,-10,0,40); f.Position=UDim2.new(0,5,0,y2); f.BackgroundColor3=Color3.fromRGB(30,10,10); Instance.new("UICorner", f)
            local t=Instance.new("TextLabel", f); t.Size=UDim2.new(0.5,0,1,0); t.Position=UDim2.new(0.03,0,0,0); t.Text="🤖 "..nome; t.TextScaled=true; t.BackgroundTransparency=1; t.TextColor3=Color3.fromRGB(255,200,200); t.TextXAlignment=Enum.TextXAlignment.Left
            local btn=Instance.new("TextButton", f); btn.Size=UDim2.new(0,80,0,30); btn.Position=UDim2.new(1,-85,0.5,-15); btn.Text="ROUBAR"; btn.TextScaled=true; btn.BackgroundColor3=Color3.fromRGB(255,0,0); btn.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", btn)
            btn.MouseButton1Click:Connect(function() alvo=nome; autoLevar=true; vel=700; basePos=basePos or plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0); start(); game.StarterGui:SetCore("SendNotification",{Title="Roubando: "..nome, Text="700 speed!", Duration=3}) end)
            y2+=44
        end
    end
    sindice.CanvasSize=UDim2.new(0,0,0,y2)
    local y3=0; tog("👁 ESP TODOS OS PALHAÇOS - OFF", y3, false, function(v) if v then startESP() else stopESP() end end, sESP); y3+=48; sESP.CanvasSize=UDim2.new(0,0,0,y3)
    local y4=0; local lblTP = Instance.new("TextLabel", sTP); lblTP.Size=UDim2.new(0.9,0,0,30); lblTP.Position=UDim2.new(0.05,0,0,y4); lblTP.Text="📍 TP PARA CADA PALHAÇO"; lblTP.TextScaled=true; lblTP.BackgroundTransparency=1; lblTP.TextColor3=Color3.fromRGB(255,215,0); lblTP.Font=Enum.Font.GothamBlack; y4+=35
    for _,nome in ipairs(listaIndice) do
        if nome~="MELHOR" then
            local f=Instance.new("Frame", sTP); f.Size=UDim2.new(1,-10,0,40); f.Position=UDim2.new(0,5,0,y4); f.BackgroundColor3=Color3.fromRGB(30,10,10); Instance.new("UICorner", f)
            local t=Instance.new("TextLabel", f); t.Size=UDim2.new(0.5,0,1,0); t.Position=UDim2.new(0.03,0,0,0); t.Text="📍 "..nome; t.TextScaled=true; t.BackgroundTransparency=1; t.TextColor3=Color3.fromRGB(255,200,200); t.TextXAlignment=Enum.TextXAlignment.Left
            local btn=Instance.new("TextButton", f); btn.Size=UDim2.new(0,80,0,30); btn.Position=UDim2.new(1,-85,0.5,-15); btn.Text="TP"; btn.TextScaled=true; btn.BackgroundColor3=Color3.fromRGB(0,150,255); btn.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", btn)
            btn.MouseButton1Click:Connect(function() local m,p=achar(nome) if m and p then plr.Character.HumanoidRootPart.CFrame=CFrame.new(p+Vector3.new(0,8,0)) end end)
            y4+=44
        end
    end
    sTP.CanvasSize=UDim2.new(0,0,0,y4)
    local y5=0
    tog("🫥 INVIS ROUBAR - PARADO PROS OUTROS + CABEÇA BAIXO PRA MIM - OFF", y5, false, function(v) if v then startInvis() else stopInvis() end end, sInvis); y5+=48
    local lblInvis = Instance.new("TextLabel", sInvis); lblInvis.Size=UDim2.new(0.9,0,0,60); lblInvis.Position=UDim2.new(0.05,0,0,y5); lblInvis.Text="Pros outros você fica PARADO no palhaço\nPra você fica de CABEÇA PRA BAIXO roubando invisível!"; lblInvis.TextScaled=true; lblInvis.BackgroundTransparency=1; lblInvis.TextColor3=Color3.fromRGB(200,200,200); y5+=65
    sInvis.CanvasSize=UDim2.new(0,0,0,y5)
    task.wait(0.5)
    for _,v in pairs(workspace:GetDescendants()) do if v:IsA("TextLabel") and v.Text:lower():find("sua base") then local m=v:FindFirstAncestorOfClass("Model") if m then basePos=getPos(m)+Vector3.new(0,6,0) end end end
    if not basePos then basePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0) end
end

local parent = getGuiParent()
local gui = Instance.new("ScreenGui"); gui.Name="CiriloMiFree"; gui.Parent=parent
local guiBloco = Instance.new("ScreenGui"); guiBloco.Name="CiriloMiFreeBloco"; guiBloco.Parent=parent
local main = Instance.new("Frame", gui); main.Size=UDim2.new(0,560,0,500); main.Position=UDim2.new(0.5,-280,0.5,-250); main.BackgroundColor3=Color3.fromRGB(15,15,15); main.Active=true; main.Draggable=true; Instance.new("UICorner", main); Instance.new("UIStroke", main).Color=Color3.fromRGB(80,120,255)
local top = Instance.new("Frame", main); top.Size=UDim2.new(1,0,0,30); top.BackgroundColor3=Color3.fromRGB(10,10,10); Instance.new("UICorner", top)
local title = Instance.new("TextLabel", top); title.Size=UDim2.new(0.6,0,1,0); title.Position=UDim2.new(0.02,0,0,0); title.Text="cirilo mi : FREE TUDO OFF - SEM TATU"; title.TextScaled=true; title.BackgroundTransparency=1; title.TextColor3=Color3.fromRGB(200,200,200); title.TextXAlignment=Enum.TextXAlignment.Left; title.Font=Enum.Font.GothamBlack
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
local btnKey = Instance.new("TextButton", sDisc); btnKey.Size=UDim2.new(0.9,0,0,35); btnKey.Position=UDim2.new(0.05,0,0,75); btnKey.Text="🔓 ATIVAR PREMIUM INVIS"; btnKey.BackgroundColor3=Color3.fromRGB(255,215,0); btnKey.TextColor3=Color3.fromRGB(0,0,0); Instance.new("UICorner", btnKey)
btnKey.MouseButton1Click:Connect(function() if boxKey.Text=="0808" then criarPremium() end end)
bDisc.MouseButton1Click:Connect(function() sDisc.Visible=true; sFarm.Visible=false end)
bFarm.MouseButton1Click:Connect(function() sDisc.Visible=false; sFarm.Visible=true end)
local autoOn=false; local basePos=nil; local voando,bv,bg,att=false,nil,nil,nil; local alvo="ALL"; local autoLevar=false; local noclipOn=false; local connNoclip=nil
local function getPos2(m) if m.PrimaryPart then return m.PrimaryPart.Position end for _,p in pairs(m:GetDescendants()) do if p:IsA("BasePart") then return p.Position end end return m:GetBoundingBox() end
local function getBase2() if basePos then return basePos end for _,v in pairs(workspace:GetDescendants()) do if v:IsA("TextLabel") and v.Text:lower():find("sua base") then local m=v:FindFirstAncestorOfClass("Model") if m then return getPos2(m)+Vector3.new(0,6,0) end end end return nil end
local function achar2(n) local lista={}; local hrp=plr.Character.HumanoidRootPart.Position; local base=getBase2(); if not base then return nil,nil end local alvos=n=="ALL" and {"404","Fachas","Grande Chicle","Infante Fogo"} or {n} for _,al in ipairs(alvos) do for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") and obj.Text:lower():find(al:lower()) then local m=obj:FindFirstAncestorOfClass("Model") if m then local p=getPos2(m) if (p-base).Magnitude>60 then table.insert(lista,{m=m,p=p,d=(hrp-p).Magnitude}) end end end end end table.sort(lista,function(a,b) return a.d<b.d end) if #lista>0 then return lista[1].m,lista[1].p end return nil,nil end
local function voar2(pos,meio) local hrp=plr.Character.HumanoidRootPart if not voando then att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero; bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero; plr.Character.Humanoid.PlatformStand=true; voando=true end local chegou=false; local t=0; local c; c=RS.Heartbeat:Connect(function() t+=0.03; if t>10 then c:Disconnect() return end local cur=plr.Character.HumanoidRootPart; local tgt=meio and pos+Vector3.new(0,5,3) or pos+Vector3.new(0,6,0); local dir=tgt-cur.Position; if dir.Magnitude<6 then bv.VectorVelocity=Vector3.zero; chegou=true; c:Disconnect() else bv.VectorVelocity=dir.Unit*190 end end) repeat task.wait() until chegou or t>10 or not autoOn; return chegou end
local function voltarBase2() local base=getBase2() if not base then return end; if att then att:Destroy() att=nil end; if bv then bv:Destroy() bv=nil end; if bg then bg:Destroy() bg=nil end; voando=false; if plr.Character.Humanoid then plr.Character.Humanoid.PlatformStand=false end; for i=1,3 do pcall(function() plr.Character.HumanoidRootPart.CFrame=CFrame.new(base+Vector3.new(0,8+i*2,0)) end) task.wait(0.3) end; task.wait(1.5) end
local function parar2() autoOn=false; if att then att:Destroy() att=nil end; if bv then bv:Destroy() bv=nil end; if bg then bg:Destroy() bg=nil end; if plr.Character.Humanoid then plr.Character.Humanoid.PlatformStand=false end; voando=false end
local function pega2(pos,model) plr.Character.HumanoidRootPart.CFrame=CFrame.new(pos+Vector3.new(0,7,4)); task.wait(0.25); local pr={}; for _,o in pairs(model:GetDescendants()) do if o:IsA("ProximityPrompt") then table.insert(pr,o) end end; if #pr==0 then for _,o in pairs(workspace:GetDescendants()) do if o:IsA("ProximityPrompt") and o.Parent:IsA("BasePart") and (o.Parent.Position-pos).Magnitude<15 then table.insert(pr,o) end end end; for _,p in pairs(pr) do p.HoldDuration=0; p.MaxActivationDistance=100; p.RequiresLineOfSight=false end; for i=1,20 do pcall(function() for _,p in pairs(pr) do fireproximityprompt(p) end end) task.wait(0.06); for _,v in pairs(plr.Character:GetChildren()) do if v:IsA("Tool") then return true end end; for _,v in pairs(plr.Backpack:GetChildren()) do if v:IsA("Tool") then v.Parent=plr.Character; return true end end end; return false end
local function start2() autoOn=true task.spawn(function() while autoOn do local com=false; for _,v in pairs(plr.Character:GetChildren()) do if v:IsA("Tool") then com=true end end; if com and autoLevar then voltarBase2() else local m,p=achar2(alvo); if m then if voar2(p,true) then if pega2(p,m) then if autoLevar then voltarBase2() end end end else task.wait(1) end end; task.wait(0.3) end end) end
local function startNoclip2() noclipOn=true; connNoclip=RS.Stepped:Connect(function() if noclipOn and plr.Character then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end end end) end
local function stopNoclip2() noclipOn=false; if connNoclip then connNoclip:Disconnect() connNoclip=nil end end
local function minimizarFree() main.Visible=false; bloco.Visible=true; gui.Enabled=false; parar2(); stopNoclip2() end
btnMin.MouseButton1Click:Connect(minimizarFree)
btnBloco.MouseButton1Click:Connect(function() main.Visible=true; bloco.Visible=false; gui.Enabled=true end)
local function tog2(nome, y, def, cb) local f=Instance.new("Frame", sFarm); f.Size=UDim2.new(1,-10,0,44); f.Position=UDim2.new(0,5,0,y); f.BackgroundColor3=Color3.fromRGB(22,22,22); Instance.new("UICorner", f) local t=Instance.new("TextLabel", f); t.Size=UDim2.new(0.7,0,1,0); t.Position=UDim2.new(0.03,0,0,0); t.Text=nome; t.TextScaled=true; t.BackgroundTransparency=1; t.TextColor3=Color3.fromRGB(200,200,200); t.TextXAlignment=Enum.TextXAlignment.Left local back=Instance.new("Frame", f); back.Size=UDim2.new(0,44,0,22); back.Position=UDim2.new(1,-50,0.5,-11); back.BackgroundColor3=def and Color3.fromRGB(80,120,255) or Color3.fromRGB(40,40,40); Instance.new("UICorner", back).CornerRadius=UDim.new(1,0) local ball=Instance.new("Frame", back); ball.Size=UDim2.new(0,16,0,16); ball.Position=def and UDim2.new(1,-19,0.5,-8) or UDim2.new(0,3,0.5,-8); ball.BackgroundColor3=Color3.new(1,1,1); Instance.new("UICorner", ball).CornerRadius=UDim.new(1,0) local b=Instance.new("TextButton", f); b.Size=UDim2.new(1,0,1,0); b.Text=""; b.BackgroundTransparency=1 local on=def; b.MouseButton1Click:Connect(function() on=not on; back.BackgroundColor3=on and Color3.fromRGB(80,120,255) or Color3.fromRGB(40,40,40); ball.Position=on and UDim2.new(1,-19,0.5,-8) or UDim2.new(0,3,0.5,-8); cb(on) end) end
local y=0
tog2("💾 SALVAR BASE - OFF - SEM TATU", y, false, function(v) if v then basePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0) end end); y+=48
tog2("👻 NOCLIP - OFF", y, false, function(v) if v then startNoclip2() else stopNoclip2() end end); y+=48
tog2("📦 AUTO LEVAR - OFF - 190", y, false, function(v) autoLevar=v end); y+=48
tog2("🤫 TODOS 4 - OFF", y, false, function(v) alvo="ALL"; if v then start2() else parar2() end end); y+=48
sFarm.CanvasSize=UDim2.new(0,0,0,y)
