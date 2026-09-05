-- 🤡 V15 FIX - NÃO VAI MAIS PRA FORA DO MAPA - VAI NO 404 MESMO
local plr = game.Players.LocalPlayer
local RS = game:GetService("RunService")

for _,v in pairs(plr.PlayerGui:GetChildren()) do if v.Name:find("Palhaco") or v.Name:find("FOCADO") then v:Destroy() end end
task.wait(0.2)

local gui = Instance.new("ScreenGui", plr.PlayerGui)
gui.Name = "PalhacoHubV15FixForaMapa"; gui.ResetOnSpawn = false

local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 350, 0, 500)
main.Position = UDim2.new(0, 15, 0, 15)
main.BackgroundColor3 = Color3.fromRGB(10,10,10)
main.Active = true; main.Draggable = true
Instance.new("UICorner", main)
Instance.new("UIStroke", main).Color = Color3.fromRGB(0,255,0)

local top = Instance.new("Frame", main)
top.Size = UDim2.new(1,0,0,38); top.BackgroundColor3 = Color3.fromRGB(0,200,0)
Instance.new("UICorner", top)
local tit = Instance.new("TextLabel", top)
tit.Size = UDim2.new(0.65,0,1,0); tit.Position = UDim2.new(0.02,0,0,0)
tit.Text = "🤡 V15 FIX - NÃO VAI PRO VAZIO"; tit.TextScaled = true; tit.TextXAlignment = Enum.TextXAlignment.Left
tit.BackgroundTransparency = 1; tit.TextColor3 = Color3.new(1,1,1); tit.Font = Enum.Font.GothamBlack

local btnMin = Instance.new("TextButton", top)
btnMin.Size = UDim2.new(0,32,0,28); btnMin.Position = UDim2.new(1,-72,0,5)
btnMin.Text = "-"; btnMin.TextScaled = true; btnMin.BackgroundColor3 = Color3.fromRGB(40,40,40); btnMin.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", btnMin)

local btnClose = Instance.new("TextButton", top)
btnClose.Size = UDim2.new(0,32,0,28); btnClose.Position = UDim2.new(1,-36,0,5)
btnClose.Text = "X"; btnClose.TextScaled = true; btnClose.BackgroundColor3 = Color3.fromRGB(200,0,0); btnClose.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", btnClose)

local bloco = Instance.new("Frame", gui)
bloco.Size = UDim2.new(0, 55, 0, 55); bloco.Position = UDim2.new(0, 20, 0, 100)
bloco.BackgroundColor3 = Color3.fromRGB(0,255,0); bloco.Visible = false; bloco.Active = true; bloco.Draggable = true
Instance.new("UICorner", bloco).CornerRadius = UDim.new(0,12)
local txtBloco = Instance.new("TextLabel", bloco); txtBloco.Size = UDim2.new(1,0,1,0); txtBloco.Text = "🤡"; txtBloco.TextScaled = true; txtBloco.BackgroundTransparency = 1
local btnBloco = Instance.new("TextButton", bloco); btnBloco.Size = UDim2.new(1,0,1,0); btnBloco.Text = ""; btnBloco.BackgroundTransparency = 1

btnMin.MouseButton1Click:Connect(function() main.Visible=false; bloco.Visible=true end)
btnBloco.MouseButton1Click:Connect(function() main.Visible=true; bloco.Visible=false end)
btnClose.MouseButton1Click:Connect(function() gui:Destroy() end)

local scroll = Instance.new("ScrollingFrame", main)
scroll.Size = UDim2.new(1,0,1,-42); scroll.Position = UDim2.new(0,0,0,42)
scroll.BackgroundTransparency = 1; scroll.CanvasSize = UDim2.new(0,0,0,1100); scroll.ScrollBarThickness = 4

local function btnC(t,y,c) local b=Instance.new("TextButton",scroll) b.Size=UDim2.new(0.92,0,0,28) b.Position=UDim2.new(0.04,0,0,y) b.Text=t b.TextScaled=true b.BackgroundColor3=c b.TextColor3=Color3.new(1,1,1) b.Font=Enum.Font.GothamBold Instance.new("UICorner",b) return b end

local alvoNome=nil
local alvoLabel=Instance.new("TextLabel", scroll)
alvoLabel.Size=UDim2.new(0.92,0,0,32); alvoLabel.Position=UDim2.new(0.04,0,0,5)
alvoLabel.Text="🎯 ALVO: 404"; alvoLabel.TextScaled=true; alvoLabel.BackgroundColor3=Color3.fromRGB(30,30,30); alvoLabel.TextColor3=Color3.fromRGB(0,255,0); Instance.new("UICorner", alvoLabel)

local bAuto=btnC("🤖 AUTO ROUBAR 404 FOCADO 190 [OFF]", 42, Color3.fromRGB(200,0,0))
local bSalvarBase=btnC("📍 SALVAR SUA BASE (CLICA AQUI NA SUA BASE)", 74, Color3.fromRGB(0,120,255))
local bStatus=btnC("💤 PARADO", 106, Color3.fromRGB(40,40,40))
local bLaser=btnC("🔴 TIRA LASER", 138, Color3.fromRGB(200,0,0))

local label=Instance.new("TextLabel", scroll); label.Size=UDim2.new(0.92,0,0,18); label.Position=UDim2.new(0.04,0,0,175); label.Text="📋 CLICA NO ALVO:"; label.TextScaled=true; label.BackgroundTransparency=1; label.TextColor3=Color3.new(1,1,1)

local meusPalhacos={"Os Focas","404","Os Arbustos","Ian","Fede Vigovani","Lul e Fede","Asaarboool","Azarino"}

local y=200; local autoOn=false; local minhaBasePos=nil; local voando,bv,bg,att=false,nil,nil,nil; local noclip=true

for _,nome in ipairs(meusPalhacos) do
    local b=btnC("🤡 "..nome, y, nome=="404" and Color3.fromRGB(0,200,0) or Color3.fromRGB(35,35,35))
    b.MouseButton1Click:Connect(function() alvoNome=nome; alvoLabel.Text="🎯 FOCO: "..nome:upper(); bAuto.Text="🤖 AUTO "..nome:upper().." 190 [OFF]"; for _,v in pairs(scroll:GetChildren()) do if v:IsA("TextButton") and v.Text:find("🤡") then v.BackgroundColor3=Color3.fromRGB(35,35,35) end end; b.BackgroundColor3=Color3.fromRGB(0,200,0) end)
    y+=30
end
scroll.CanvasSize=UDim2.new(0,0,0,y+10)
alvoNome="404"

-- FIX PRINCIPAL: PEGA POSIÇÃO REAL, NÃO VAI PRO VAZIO
local function getPosReal(model)
    -- 1. Tenta PrimaryPart
    if model.PrimaryPart then return model.PrimaryPart.Position end
    -- 2. Tenta HumanoidRootPart
    local hrp = model:FindFirstChild("HumanoidRootPart")
    if hrp then return hrp.Position end
    -- 3. Tenta qualquer BasePart
    for _,p in pairs(model:GetDescendants()) do
        if p:IsA("BasePart") then
            -- Ignora partes muito longe (fora do mapa)
            if math.abs(p.Position.X) < 5000 and math.abs(p.Position.Z) < 5000 and p.Position.Y > -100 and p.Position.Y < 1000 then
                return p.Position
            end
        end
    end
    -- 4. Ultimo recurso GetBoundingBox mas com validação
    local ok, cf, size = pcall(function() return model:GetBoundingBox() end)
    if ok and cf then
        local pos = cf.Position
        -- Se for pro vazio (0,0,0 ou muito longe), ignora
        if pos.Magnitude < 10 or pos.Y < -50 or math.abs(pos.X) > 5000 or math.abs(pos.Z) > 5000 then
            return nil
        end
        return pos
    end
    return nil
end

local function getSuaBase()
    if minhaBasePos then return minhaBasePos end
    for _,v in pairs(workspace:GetDescendants()) do
        if v:IsA("TextLabel") and v.Text:lower():find("sua base") then
            local m=v:FindFirstAncestorOfClass("Model")
            if m then
                local pos = getPosReal(m)
                if pos then return pos + Vector3.new(0,6,0) end
            end
        end
    end
    return nil
end

-- FIX: ACHA 404 DE VERDADE NA BASE DOS OUTROS
local function acharPalhaco(nome)
    if not nome then return nil end
    local alvo=nome:lower()
    print("🔍 PROCURANDO: "..nome)
    local lista = {}

    for _,obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("TextLabel") and obj.Text:lower():find(alvo) then
            local m=obj:FindFirstAncestorOfClass("Model")
            if m then
                local pos = getPosReal(m)
                if pos then
                    -- Só adiciona se NÃO for na sua base e NÃO for no vazio
                    local distMinhaBase = minhaBasePos and (pos - minhaBasePos).Magnitude or 9999
                    if distMinhaBase > 20 then -- Não é na sua base
                        table.insert(lista, {model=m, pos=pos, dist=(plr.Character.HumanoidRootPart.Position - pos).Magnitude})
                        print("✅ Achei 404 em: "..tostring(pos).." - "..m.Name)
                    end
                end
            end
        end
    end

    -- Pega o mais perto que não seja vazio
    table.sort(lista, function(a,b) return a.dist < b.dist end)
    if #lista > 0 then
        print("✅ Indo no 404 mais perto: "..tostring(lista[1].pos))
        return lista[1].model, lista[1].pos
    end
    print("❌ Nenhum 404 achado fora da sua base")
    return nil, nil
end

local function voarAtePos(posAlvo, vel)
    vel=vel or 190
    if not posAlvo then print("❌ posAlvo nil!"); return false end
    if posAlvo.Y < -50 or math.abs(posAlvo.X) > 5000 or math.abs(posAlvo.Z) > 5000 then
        print("❌ Posição é no vazio, cancelando: "..tostring(posAlvo))
        return false
    end
    if not plr.Character or not plr.Character:FindFirstChild("HumanoidRootPart") then return false end
    local hrp=plr.Character.HumanoidRootPart
    if not voando then att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero; bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero; plr.Character.Humanoid.PlatformStand=true; voando=true end
    local chegou=false; local tempo=0; local conn
    conn=RS.Heartbeat:Connect(function()
        if not autoOn then conn:Disconnect() return end
        if not plr.Character:FindFirstChild("HumanoidRootPart") then conn:Disconnect() return end
        tempo+=0.03
        if tempo>10 then print("❌ Timeout"); bv.VectorVelocity=Vector3.zero; conn:Disconnect() return end
        local cur=plr.Character.HumanoidRootPart; local dir=posAlvo-cur.Position
        if dir.Magnitude<8 then bv.VectorVelocity=Vector3.zero; chegou=true; conn:Disconnect() else bv.VectorVelocity=dir.Unit*vel end
    end)
    repeat task.wait() until chegou or tempo>10 or not autoOn
    return chegou
end

local function pararTudo()
    autoOn=false; if att then att:Destroy() att=nil end; if bv then bv:Destroy() bv=nil end; if bg then bg:Destroy() bg=nil end
    if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.PlatformStand=false end
    voando=false; bAuto.Text="🤖 AUTO "..(alvoNome or "404").." 190 [OFF]"; bAuto.BackgroundColor3=Color3.fromRGB(200,0,0)
end

bSalvarBase.MouseButton1Click:Connect(function()
    if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
        minhaBasePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0)
        bSalvarBase.Text="✅ BASE SALVA! -775,213"
        print("✅ Base salva: "..tostring(minhaBasePos))
        task.wait(2); bSalvarBase.Text="📍 BASE SALVA!"
    end
end)

bAuto.MouseButton1Click:Connect(function()
    if not alvoNome then alvoNome="404" end
    autoOn=not autoOn
    if autoOn then
        bAuto.Text="🤖 ROUBANDO "..alvoNome:upper().." [ON]"; bAuto.BackgroundColor3=Color3.fromRGB(0,200,0)
        task.spawn(function()
            while autoOn do
                local palhaco, posPalhaco = acharPalhaco(alvoNome)
                if not palhaco or not posPalhaco then
                    bStatus.Text="🔍 PROCURANDO "..alvoNome:upper().." NAS BASES...";
                    bStatus.BackgroundColor3=Color3.fromRGB(100,100,0);
                    task.wait(1.5)
                else
                    bStatus.Text="✈️ INDO 190 ATÉ "..alvoNome:upper().." - "..math.floor(posPalhaco.X)..","..math.floor(posPalhaco.Z);
                    bStatus.BackgroundColor3=Color3.fromRGB(0,100,200)

                    local chegou=voarAtePos(posPalhaco + Vector3.new(0,5,0), 190)

                    if chegou and autoOn then
                        bStatus.Text="🤲 PEGANDO NA MÃO..."
                        pcall(function()
                            for _,pr in pairs(palhaco:GetDescendants()) do if pr:IsA("ProximityPrompt") then pr.HoldDuration=0; fireproximityprompt(pr) end end
                        end)
                        task.wait(0.8)
                        pcall(function() for _,tool in pairs(plr.Backpack:GetChildren()) do if tool:IsA("Tool") then plr.Character.Humanoid:EquipTool(tool) end end end)
                        task.wait(0.6)

                        local basePos=getSuaBase()
                        if basePos then
                            bStatus.Text="🏠 VOLTANDO PRA SUA BASE 190..."
                            voarAtePos(basePos, 190)
                            bStatus.Text="✅ ENTREGUE!"
                            task.wait(2)
                        else
                            bStatus.Text="❌ SALVA SUA BASE PRIMEIRO!"
                            task.wait(2)
                            autoOn=false
                            pararTudo()
                        end
                    else
                        bStatus.Text="❌ NÃO CHEGOU - POSIÇÃO INVALIDA"
                        task.wait(1)
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

game.StarterGui:SetCore("SendNotification",{Title="🤡 V15 FIX", Text="Não vai mais pro vazio! Vai no 404 mesmo!", Duration=5})
