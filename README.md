-- 🤡 PALHAÇO HUB V13 FOCADO - VOA 190 ATÉ PALHAÇO > PEGA NA MÃO > VOLTA PRA SUA BASE
-- FEITO PROS 22/34 DO SEU VIDEO - MODO OS FOCAS

local plr = game.Players.LocalPlayer
local RS = game:GetService("RunService")
local UIS = game:GetService("UserInputService")

-- LIMPA
for _,v in pairs(plr.PlayerGui:GetChildren()) do if v.Name:find("Palhaco") or v.Name:find("Nexus") then v:Destroy() end end
task.wait(0.2)

local gui = Instance.new("ScreenGui", plr.PlayerGui)
gui.Name = "PalhacoHubV13Focado"; gui.ResetOnSpawn = false

local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 350, 0, 520)
main.Position = UDim2.new(0, 15, 0, 15)
main.BackgroundColor3 = Color3.fromRGB(10,10,10)
main.Active = true; main.Draggable = true
Instance.new("UICorner", main)
Instance.new("UIStroke", main).Color = Color3.fromRGB(255,0,100)

local tit = Instance.new("TextLabel", main)
tit.Size = UDim2.new(1,0,0,38); tit.Text = "🤡 V13 FOCADO 190 - OS FOCAS"; tit.TextScaled = true
tit.BackgroundColor3 = Color3.fromRGB(255,0,100); tit.TextColor3 = Color3.new(1,1,1); tit.Font = Enum.Font.GothamBlack
Instance.new("UICorner", tit)

local scroll = Instance.new("ScrollingFrame", main)
scroll.Size = UDim2.new(1,0,1,-42); scroll.Position = UDim2.new(0,0,0,42)
scroll.BackgroundTransparency = 1; scroll.CanvasSize = UDim2.new(0,0,0,1100); scroll.ScrollBarThickness = 4

local function btn(t,y,c) local b=Instance.new("TextButton",scroll) b.Size=UDim2.new(0.92,0,0,28) b.Position=UDim2.new(0.04,0,0,y) b.Text=t b.TextScaled=true b.BackgroundColor3=c b.TextColor3=Color3.new(1,1,1) b.Font=Enum.Font.GothamBold Instance.new("UICorner",b) return b end

local alvoNome = nil
local alvoLabel = Instance.new("TextLabel", scroll)
alvoLabel.Size = UDim2.new(0.92,0,0,32); alvoLabel.Position = UDim2.new(0.04,0,0,5)
alvoLabel.Text = "🎯 NENHUM ALVO - CLICA EM UM ABAIXO"; alvoLabel.TextScaled=true; alvoLabel.BackgroundColor3=Color3.fromRGB(30,30,30); alvoLabel.TextColor3=Color3.fromRGB(255,255,0); Instance.new("UICorner", alvoLabel)

local bAuto = btn("🤖 AUTO ROUBAR FOCADO 190 [OFF]", 42, Color3.fromRGB(200,0,0))
local bSalvarBase = btn("📍 SALVAR MINHA BASE (FICA EM CIMA DO 'SUA BASE')", 74, Color3.fromRGB(0,120,255))
local bStatus = btn("💤 PARADO", 106, Color3.fromRGB(40,40,40))
local bLaser = btn("🔴 TIRA LASER", 138, Color3.fromRGB(200,0,0))
local bVoar = btn("✈️ VOAR 190 [OFF]", 170, Color3.fromRGB(40,40,40))

local label = Instance.new("TextLabel", scroll)
label.Size=UDim2.new(0.92,0,0,20); label.Position=UDim2.new(0.04,0,0,205); label.Text="📋 SEUS 22/34 PALHAÇOS DO VIDEO - CLICA:"; label.TextScaled=true; label.BackgroundTransparency=1; label.TextColor3=Color3.new(1,1,1)

-- SEUS PALHAÇOS DO VIDEO - NA ORDEM QUE APARECE
local meusPalhacos = {
"Os Focas", "404", "Os Arbustos", "Ian", "Fede Vigovani", 
"Lul e Fede", "Asaarboool", "Azarino", "Luli e Fede 2",
"Mini Palhaco", "Kavane", "Duffin", "Lul Miau", "Abacaxi",
"O Grande Chicle", "Os Fachas", "Infante do Fogo", "404 Dourado",
"O Grande Chicle Esqueleto", "Os Cerebras", "Fadas", "XC Tonto"
}

local y=230
local autoOn=false
local minhaBasePos=nil
local voando,bv,bg,att=false,nil,nil,nil
local noclip=true
local keys={}
local tatuOn=false; local tatuBV,tatuBG,tatuConn

for _,nome in ipairs(meusPalhacos) do
    local b = btn("🤡 "..nome, y, Color3.fromRGB(35,35,35))
    b.MouseButton1Click:Connect(function()
        alvoNome=nome
        alvoLabel.Text="🎯 ALVO FOCADO: "..nome:upper()
        bAuto.Text="🤖 AUTO ROUBAR "..nome:upper().." 190 [OFF]"
        for _,v in pairs(scroll:GetChildren()) do if v:IsA("TextButton") and v.Text:find("🤡") and v.Text~="🤡" then v.BackgroundColor3=Color3.fromRGB(35,35,35) end end
        b.BackgroundColor3=Color3.fromRGB(0,200,0)
        game.StarterGui:SetCore("SendNotification",{Title="🎯 FOCO", Text=nome.." selecionado!", Duration=2})
    end)
    y+=30
end
scroll.CanvasSize=UDim2.new(0,0,0,y+10)

-- FUNÇÃO ACHA SUA BASE
local function getSuaBase()
    if minhaBasePos then return minhaBasePos end
    for _,v in pairs(workspace:GetDescendants()) do
        if v:IsA("TextLabel") and v.Text:lower():find("sua base") then
            local m=v:FindFirstAncestorOfClass("Model") or v.Parent.Parent
            if m then return Vector3.new(m:GetBoundingBox())+Vector3.new(0,6,0) end
        end
    end
    return nil
end

-- ACHA PALHAÇO PELO NOME
local function acharPalhaco(nome)
    if not nome then return nil end
    local alvo=nome:lower()
    local melhor=nil; local menor=math.huge
    local hrpPos = plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") and plr.Character.HumanoidRootPart.Position or Vector3.new(0,0,0)
    for _,obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("TextLabel") and obj.Text:lower():find(alvo) then
            local m=obj:FindFirstAncestorOfClass("Model")
            if m then
                local pos=Vector3.new(m:GetBoundingBox())
                local d=(pos-hrpPos).Magnitude
                if d<menor then menor=d; melhor=m end
            end
        end
        if obj:IsA("Model") and obj.Name:lower():find(alvo) then
            local pos=Vector3.new(obj:GetBoundingBox())
            local d=(pos-hrpPos).Magnitude
            if d<menor then menor=d; melhor=obj end
        end
    end
    return melhor
end

-- VOA 190 - FUNÇÃO QUE PEGA MESMO
local function voarAtePos(posAlvo, vel)
    vel=vel or 190
    if not plr.Character or not plr.Character:FindFirstChild("HumanoidRootPart") then return false end
    local hrp=plr.Character.HumanoidRootPart
    if not voando then
        att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero
        bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero
        plr.Character.Humanoid.PlatformStand=true; voando=true
    end
    local chegou=false
    local conn
    conn=RS.Heartbeat:Connect(function()
        if not autoOn or not plr.Character:FindFirstChild("HumanoidRootPart") then conn:Disconnect() return end
        local cur=plr.Character.HumanoidRootPart
        local dir=posAlvo-cur.Position
        if dir.Magnitude<7 then bv.VectorVelocity=Vector3.zero; chegou=true; conn:Disconnect()
        else bv.VectorVelocity=dir.Unit*vel end
    end)
    repeat task.wait() until chegou or not autoOn
    return chegou
end

local function pararTudo()
    autoOn=false
    if att then att:Destroy() att=nil end
    if bv then bv:Destroy() bv=nil end
    if bg then bg:Destroy() bg=nil end
    if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.PlatformStand=false end
    voando=false
    bAuto.Text="🤖 AUTO ROUBAR "..(alvoNome or "FOCADO").." 190 [OFF]"
    bAuto.BackgroundColor3=Color3.fromRGB(200,0,0)
end

-- SALVAR BASE
bSalvarBase.MouseButton1Click:Connect(function()
    if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
        minhaBasePos=plr.Character.HumanoidRootPart.Position+Vector3.new(0,5,0)
        bSalvarBase.Text="✅ BASE SALVA! "..math.floor(minhaBasePos.X)..","..math.floor(minhaBasePos.Z)
        task.wait(2); bSalvarBase.Text="📍 SALVAR MINHA BASE (FICA EM CIMA DO 'SUA BASE')"
        game.StarterGui:SetCore("SendNotification",{Title="🏠 BASE SALVA", Text="Sua base foi salva!", Duration=2})
    end
end)

-- AUTO ROUBAR FOCADO - VOA > PEGA NA MÃO > VOLTA
bAuto.MouseButton1Click:Connect(function()
    if not alvoNome then game.StarterGui:SetCore("SendNotification",{Title="❌", Text="Clica num palhaço primeiro!", Duration=2}) return end
    if not minhaBasePos and not getSuaBase() then
        game.StarterGui:SetCore("SendNotification",{Title="⚠️ SALVA SUA BASE", Text="Vai na sua base e clica SALVAR BASE", Duration=3})
    end

    autoOn=not autoOn
    if autoOn then
        bAuto.Text="🤖 ROUBANDO "..alvoNome:upper().." 190 [ON]"; bAuto.BackgroundColor3=Color3.fromRGB(0,200,0)
        task.spawn(function()
            while autoOn do
                local palhaco=acharPalhaco(alvoNome)
                if not palhaco then
                    bStatus.Text="🔍 PROCURANDO "..alvoNome:upper().."..."
                    bStatus.BackgroundColor3=Color3.fromRGB(100,100,0)
                    task.wait(1)
                else
                    -- 1. VOA ATÉ O PALHAÇO 190
                    bStatus.Text="✈️ INDO 190 ATÉ "..alvoNome:upper().."..."
                    bStatus.BackgroundColor3=Color3.fromRGB(0,100,200)
                    local posP=Vector3.new(palhaco:GetBoundingBox())+Vector3.new(0,4,0)
                    local chegou=voarAtePos(posP, 190)

                    if chegou and autoOn then
                        -- 2. PEGA NA MÃO
                        bStatus.Text="🤲 PEGANDO "..alvoNome:upper().." NA MÃO..."
                        bStatus.BackgroundColor3=Color3.fromRGB(200,100,0)
                        pcall(function()
                            for _,pr in pairs(palhaco:GetDescendants()) do if pr:IsA("ProximityPrompt") then fireproximityprompt(pr) end end
                            for _,pr in pairs(workspace:GetDescendants()) do if pr:IsA("ProximityPrompt") and pr.Parent and pr.Parent:IsA("BasePart") and (pr.Parent.Position-posP).Magnitude<15 then fireproximityprompt(pr) end end
                        end)
                        task.wait(0.6)
                        -- Equipa na mão
                        pcall(function()
                            for _,tool in pairs(plr.Backpack:GetChildren()) do if tool:IsA("Tool") then plr.Character.Humanoid:EquipTool(tool) end end
                        end)
                        task.wait(0.5)

                        -- 3. VOLTA PRA SUA BASE 190
                        local basePos=getSuaBase()
                        if basePos then
                            bStatus.Text="🏠 VOLTANDO 190 PRA SUA BASE COM "..alvoNome:upper().."..."
                            bStatus.BackgroundColor3=Color3.fromRGB(0,200,0)
                            voarAtePos(basePos, 190)
                            bStatus.Text="✅ "..alvoNome:upper().." ENTREGUE!"
                            game.StarterGui:SetCore("SendNotification",{Title="✅ ROUBO COMPLETO", Text=alvoNome.." levado pra sua base!", Duration=3})
                            task.wait(2)
                        else
                            bStatus.Text="❌ NÃO ACHEI SUA BASE"
                            task.wait(2)
                        end
                    end
                end
                task.wait(0.5)
            end
            pararTudo(); bStatus.Text="💤 PARADO"
        end)
    else
        pararTudo(); bStatus.Text="💤 PARADO"; bStatus.BackgroundColor3=Color3.fromRGB(40,40,40)
    end
end)

bLaser.MouseButton1Click:Connect(function() for _,v in pairs(workspace:GetDescendants()) do if v.Name:lower():find("laser") then pcall(function() v:Destroy() end) end end end)
bVoar.MouseButton1Click:Connect(function()
    if not voando then
        local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart"); if not hrp then return end
        att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero
        bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero
        plr.Character.Humanoid.PlatformStand=true; voando=true; bVoar.Text="✈️ VOAR 190 [ON]"; bVoar.BackgroundColor3=Color3.fromRGB(0,200,0)
    else pararTudo(); bVoar.Text="✈️ VOAR 190 [OFF]"; bVoar.BackgroundColor3=Color3.fromRGB(40,40,40) end
end)

UIS.InputBegan:Connect(function(i,g) if g then return end; keys[i.KeyCode]=true; if i.KeyCode==Enum.KeyCode.R then for _,v in pairs(workspace:GetDescendants()) do if v.Name:lower():find("laser") then pcall(function() v:Destroy() end) end end end end)
UIS.InputEnded:Connect(function(i) keys[i.KeyCode]=false end)
RS.Stepped:Connect(function() if noclip and plr.Character then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end end end)

game.StarterGui:SetCore("SendNotification",{Title="🤡 V13 FOCADO", Text="1-Salva sua base 2-Clica Os Focas 3-Ativa AUTO", Duration=6})
print("🤡 V13 FOCADO 190 CARREGADO!")
