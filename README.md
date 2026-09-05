-- 🤡 V17 FIX - FICA NO MEIO DO 404 + BLOCO QUE APARECE
local plr = game.Players.LocalPlayer
local RS = game:GetService("RunService")

for _,v in pairs(plr.PlayerGui:GetChildren()) do if v.Name:find("Palhaco") or v.Name:find("V15") or v.Name:find("V16") then v:Destroy() end end
for _,v in pairs(game:GetService("CoreGui"):GetChildren()) do pcall(function() if v.Name:find("Palhaco") then v:Destroy() end end) end
task.wait(0.3)

-- GUI PRINCIPAL
local guiMain = Instance.new("ScreenGui", plr.PlayerGui)
guiMain.Name = "PalhacoHubV17Main"; guiMain.ResetOnSpawn = false; guiMain.DisplayOrder = 10

-- GUI DO BLOCO SEPARADA PRA NÃO SUMIR
local guiBloco = Instance.new("ScreenGui", plr.PlayerGui)
guiBloco.Name = "PalhacoHubV17Bloco"; guiBloco.ResetOnSpawn = false; guiBloco.DisplayOrder = 999

local main = Instance.new("Frame", guiMain)
main.Size = UDim2.new(0, 350, 0, 460)
main.Position = UDim2.new(0, 15, 0, 15)
main.BackgroundColor3 = Color3.fromRGB(10,10,10)
main.Active = true; main.Draggable = true
Instance.new("UICorner", main)
Instance.new("UIStroke", main).Color = Color3.fromRGB(0,255,0)

local top = Instance.new("Frame", main)
top.Size = UDim2.new(1,0,0,38); top.BackgroundColor3 = Color3.fromRGB(0,200,0)
Instance.new("UICorner", top)
local tit = Instance.new("TextLabel", top)
tit.Size = UDim2.new(0.55,0,1,0); tit.Position = UDim2.new(0.02,0,0,0)
tit.Text = "🤡 V17 FIX MEIO + BLOCO"; tit.TextScaled = true; tit.TextXAlignment = Enum.TextXAlignment.Left
tit.BackgroundTransparency = 1; tit.TextColor3 = Color3.new(1,1,1); tit.Font = Enum.Font.GothamBlack

local btnMin = Instance.new("TextButton", top)
btnMin.Size = UDim2.new(0,40,0,28); btnMin.Position = UDim2.new(1,-84,0,5)
btnMin.Text = "-"; btnMin.TextScaled = true; btnMin.BackgroundColor3 = Color3.fromRGB(50,50,50); btnMin.TextColor3 = Color3.new(1,1,1); btnMin.Font = Enum.Font.GothamBlack
Instance.new("UICorner", btnMin)

local btnClose = Instance.new("TextButton", top)
btnClose.Size = UDim2.new(0,40,0,28); btnClose.Position = UDim2.new(1,-40,0,5)
btnClose.Text = "X"; btnClose.TextScaled = true; btnClose.BackgroundColor3 = Color3.fromRGB(200,0,0); btnClose.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", btnClose)

-- BLOCO QUE VIRA - AGORA EM GUI SEPARADA E GRANDE
local bloco = Instance.new("Frame", guiBloco)
bloco.Size = UDim2.new(0, 65, 0, 65)
bloco.Position = UDim2.new(0, 20, 0, 200)
bloco.BackgroundColor3 = Color3.fromRGB(0,255,0)
bloco.Visible = false
bloco.Active = true
bloco.Draggable = true
bloco.ZIndex = 999
Instance.new("UICorner", bloco).CornerRadius = UDim.new(0,14)
local sBloco = Instance.new("UIStroke", bloco); sBloco.Color = Color3.fromRGB(255,255,255); sBloco.Thickness = 3
local txtBloco = Instance.new("TextLabel", bloco)
txtBloco.Size = UDim2.new(1,0,1,0); txtBloco.Text = "🤡"; txtBloco.TextScaled = true; txtBloco.BackgroundTransparency = 1; txtBloco.ZIndex = 1000
local txtBloco2 = Instance.new("TextLabel", bloco)
txtBloco2.Size = UDim2.new(1,0,0,15); txtBloco2.Position = UDim2.new(0,0,1,-15); txtBloco2.Text = "ABRIR"; txtBloco2.TextScaled = true; txtBloco2.BackgroundTransparency = 1; txtBloco2.TextColor3 = Color3.new(1,1,1); txtBloco2.ZIndex = 1000
local btnBloco = Instance.new("TextButton", bloco)
btnBloco.Size = UDim2.new(1,0,1,0); btnBloco.Text = ""; btnBloco.BackgroundTransparency = 1; btnBloco.ZIndex = 1001

local function minimizar()
    main.Visible = false
    bloco.Visible = true
    guiMain.Enabled = false -- desativa main pra não bugar
    game.StarterGui:SetCore("SendNotification",{Title="🤡 BLOCO", Text="Virou bloco verde! Clica nele pra abrir!", Duration=3})
end
local function maximizar()
    main.Visible = true
    bloco.Visible = false
    guiMain.Enabled = true
end

btnMin.MouseButton1Click:Connect(minimizar)
btnBloco.MouseButton1Click:Connect(maximizar)
btnClose.MouseButton1Click:Connect(function() guiMain:Destroy(); guiBloco:Destroy() end)

-- CONTEÚDO
local scroll = Instance.new("ScrollingFrame", main)
scroll.Size = UDim2.new(1,0,1,-42); scroll.Position = UDim2.new(0,0,0,42)
scroll.BackgroundTransparency = 1; scroll.CanvasSize = UDim2.new(0,0,0,900); scroll.ScrollBarThickness = 4

local function btnC(t,y,c) local b=Instance.new("TextButton",scroll) b.Size=UDim2.new(0.92,0,0,28) b.Position=UDim2.new(0.04,0,0,y) b.Text=t b.TextScaled=true b.BackgroundColor3=c b.TextColor3=Color3.new(1,1,1) b.Font=Enum.Font.GothamBold Instance.new("UICorner",b) return b end

local alvoNome="404"
local alvoLabel=Instance.new("TextLabel", scroll)
alvoLabel.Size=UDim2.new(0.92,0,0,32); alvoLabel.Position=UDim2.new(0.04,0,0,5)
alvoLabel.Text="🎯 FOCO: 404"; alvoLabel.TextScaled=true; alvoLabel.BackgroundColor3=Color3.fromRGB(30,30,30); alvoLabel.TextColor3=Color3.fromRGB(0,255,0); Instance.new("UICorner", alvoLabel)

local bAuto=btnC("🤖 AUTO 404 FOCADO 190 [OFF]", 42, Color3.fromRGB(200,0,0))
local bSalvarBase=btnC("📍 SALVAR SUA BASE", 74, Color3.fromRGB(0,120,255))
local bStatus=btnC("💤 PARADO", 106, Color3.fromRGB(40,40,40))
local bLaser=btnC("🔴 TIRA LASER", 138, Color3.fromRGB(200,0,0))

local y=180
for _,nome in ipairs({"Os Focas","404","Os Arbustos","Ian","Fede Vigovani","Lul e Fede","Asaarboool","Azarino"}) do
    local b=btnC("🤡 "..nome, y, nome=="404" and Color3.fromRGB(0,200,0) or Color3.fromRGB(35,35,35))
    b.MouseButton1Click:Connect(function() alvoNome=nome; alvoLabel.Text="🎯 FOCO: "..nome:upper(); bAuto.Text="🤖 AUTO "..nome:upper().." 190 [OFF]" end)
    y+=30
end
scroll.CanvasSize=UDim2.new(0,0,0,y+10)

local autoOn=false; local minhaBasePos=nil; local voando,bv,bg,att=false,nil,nil,nil; local noclip=true

local function getPosReal(model)
    if model.PrimaryPart then return model.PrimaryPart.Position end
    for _,p in pairs(model:GetDescendants()) do if p:IsA("BasePart") then if math.abs(p.Position.X) < 5000 and p.Position.Y > -50 then return p.Position end end end
    local ok, cf = pcall(function() return model:GetBoundingBox() end)
    if ok and cf and cf.Position.Magnitude > 10 then return cf.Position end
    return nil
end

local function getSuaBase()
    if minhaBasePos then return minhaBasePos end
    for _,v in pairs(workspace:GetDescendants()) do if v:IsA("TextLabel") and v.Text:lower():find("sua base") then local m=v:FindFirstAncestorOfClass("Model") if m then local pos=getPosReal(m) if pos then return pos + Vector3.new(0,6,0) end end end end
    return nil
end

local function acharPalhaco(nome)
    local alvo=nome:lower(); local lista={}
    local hrpPos=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") and plr.Character.HumanoidRootPart.Position or Vector3.new(0,0,0)
    for _,obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("TextLabel") and obj.Text:lower():find(alvo) then
            local m=obj:FindFirstAncestorOfClass("Model")
            if m then local pos=getPosReal(m) if pos and (minhaBasePos==nil or (pos-minhaBasePos).Magnitude>20) then table.insert(lista, {model=m, pos=pos, dist=(hrpPos-pos).Magnitude}) end end
        end
    end
    table.sort(lista, function(a,b) return a.dist < b.dist end)
    if #lista>0 then return lista[1].model, lista[1].pos end
    return nil, nil
end

-- FIX: FICA BEM NO MEIO DO 404
local function voarAteMeio(posAlvo, vel, ficarNoMeio)
    ficarNoMeio = ficarNoMeio or false
    vel=vel or 190; if not posAlvo then return false end
    if posAlvo.Y < -50 or math.abs(posAlvo.X) > 5000 then return false end
    local hrp=plr.Character.HumanoidRootPart
    if not voando then att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero; bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero; plr.Character.Humanoid.PlatformStand=true; voando=true end
    local chegou=false; local tempo=0; local conn
    conn=RS.Heartbeat:Connect(function()
        if not autoOn then conn:Disconnect() return end
        tempo+=0.03; if tempo>10 then bv.VectorVelocity=Vector3.zero; conn:Disconnect() return end
        local cur=plr.Character.HumanoidRootPart;
        local targetPos = ficarNoMeio and posAlvo or (posAlvo + Vector3.new(0,5,0))
        local dir=targetPos-cur.Position
        local distancia = ficarNoMeio and 1.5 or 5 -- SE FOR NO MEIO, PARA A 1.5 STUDS, SE NÃO 5
        if dir.Magnitude < distancia then
            bv.VectorVelocity=Vector3.zero;
            -- FIX: TELEPORTA BEM NO MEIO
            if ficarNoMeio then
                cur.CFrame = CFrame.new(posAlvo)
            end
            chegou=true; conn:Disconnect()
        else
            bv.VectorVelocity=dir.Unit*vel
        end
    end)
    repeat task.wait() until chegou or tempo>10 or not autoOn
    -- GARANTE QUE FICA NO MEIO
    if chegou and ficarNoMeio and plr.Character:FindFirstChild("HumanoidRootPart") then
        plr.Character.HumanoidRootPart.CFrame = CFrame.new(posAlvo)
        task.wait(0.2)
    end
    return chegou
end

local function pararTudo()
    autoOn=false; if att then att:Destroy() att=nil end; if bv then bv:Destroy() bv=nil end; if bg then bg:Destroy() bg=nil end
    if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.PlatformStand=false end
    voando=false; bAuto.Text="🤖 AUTO "..(alvoNome or "404").." 190 [OFF]"; bAuto.BackgroundColor3=Color3.fromRGB(200,0,0)
end

local function pegaNaMaoFocado(posAlvo, modelAlvo)
    bStatus.Text="🤲 BEM NO MEIO - PEGANDO..."
    -- Garante que tá no meio
    if plr.Character:FindFirstChild("HumanoidRootPart") then
        plr.Character.HumanoidRootPart.CFrame = CFrame.new(posAlvo)
    end
    task.wait(0.3)
    for _,obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("ProximityPrompt") then
            if obj.Parent and obj.Parent:IsA("BasePart") then
                local dist = (obj.Parent.Position - posAlvo).Magnitude
                if dist < 12 then -- DIMINUIU DE 25 PRA 12 PRA PEGAR SÓ O QUE TA NO MEIO
                    obj.HoldDuration = 0; obj.MaxActivationDistance = 100; obj.RequiresLineOfSight = false
                end
            end
        end
    end
    task.wait(0.1)
    for i=1,20 do -- AUMENTOU DE 15 PRA 20
        pcall(function()
            for _,obj in pairs(workspace:GetDescendants()) do
                if obj:IsA("ProximityPrompt") and obj.Parent and obj.Parent:IsA("BasePart") then
                    if (obj.Parent.Position - posAlvo).Magnitude < 12 then
                        fireproximityprompt(obj)
                    end
                end
            end
        end)
        task.wait(0.05)
    end
    task.wait(0.4)
    pcall(function()
        for _,tool in pairs(plr.Backpack:GetChildren()) do if tool:IsA("Tool") then plr.Character.Humanoid:EquipTool(tool) end end
    end)
    local temTool = false
    for _,tool in pairs(plr.Character:GetChildren()) do if tool:IsA("Tool") then temTool=true end end
    return temTool
end

bSalvarBase.MouseButton1Click:Connect(function()
    if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
        minhaBasePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0)
        bSalvarBase.Text="✅ BASE SALVA!"
        task.wait(1.5); bSalvarBase.Text="📍 SALVAR SUA BASE"
    end
end)

bAuto.MouseButton1Click:Connect(function()
    autoOn=not autoOn
    if autoOn then
        bAuto.Text="🤖 ROUBANDO "..alvoNome:upper().." [ON]"; bAuto.BackgroundColor3=Color3.fromRGB(0,200,0)
        task.spawn(function()
            while autoOn do
                local palhaco, posPalhaco = acharPalhaco(alvoNome)
                if not palhaco then
                    bStatus.Text="🔍 PROCURANDO "..alvoNome:upper().."..."
                    task.wait(1.5)
                else
                    bStatus.Text="✈️ INDO BEM NO MEIO DO "..alvoNome:upper().."..."
                    -- FIX: FICA BEM NO MEIO = true
                    local chegou=voarAteMeio(posPalhaco, 190, true)

                    if chegou and autoOn then
                        local pegou=pegaNaMaoFocado(posPalhaco, palhaco)
                        if pegou then
                            local basePos=getSuaBase()
                            if basePos then
                                bStatus.Text="🏠 VOLTANDO PRA SUA BASE..."
                                voarAteMeio(basePos, 190, false)
                                bStatus.Text="✅ ENTREGUE!"
                                task.wait(2)
                            end
                        else
                            bStatus.Text="❌ NÃO PEGOU - TENTANDO DE NOVO NO MEIO"
                            task.wait(1)
                        end
                    end
                end
                task.wait(0.5)
            end
            pararTudo(); bStatus.Text="💤 PARADO"
        end)
    else pararTudo(); bStatus.Text="💤 PARADO" end
end)

bLaser.MouseButton1Click:Connect(function() for _,v in pairs(workspace:GetDescendants()) do if v.Name:lower():find("laser") then pcall(function() v:Destroy() end) end end end)
RS.Stepped:Connect(function() if noclip and plr.Character then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end end end)

game.StarterGui:SetCore("SendNotification",{Title="🤡 V17 FIX", Text="Agora fica BEM NO MEIO do 404 e bloco aparece!", Duration=5})
