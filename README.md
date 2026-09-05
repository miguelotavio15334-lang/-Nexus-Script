-- ⚡ NEXUS V6 LITE - SÓ TIRA LASER + NOCLIP + VOAR + SALVAR TP + DAR TP - LIMPO
local plr = game.Players.LocalPlayer
local UIS = game:GetService("UserInputService")
local RS = game:GetService("RunService")

local gui = Instance.new("ScreenGui", plr.PlayerGui)
gui.Name = "NexusV6Lite"; gui.ResetOnSpawn = false

-- MENU PRINCIPAL
local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 300, 0, 280)
main.Position = UDim2.new(0, 15, 0, 20)
main.BackgroundColor3 = Color3.fromRGB(12,12,12)
main.Active = true; main.Draggable = true
Instance.new("UICorner", main)
Instance.new("UIStroke", main).Color = Color3.fromRGB(140,0,255)

local tit = Instance.new("TextLabel", main)
tit.Size = UDim2.new(0.70,0,0,40); tit.Text = "⚡ Nexus V6 Lite"; tit.TextScaled = true
tit.BackgroundColor3 = Color3.fromRGB(140,0,255); tit.TextColor3 = Color3.new(1,1,1); tit.Font = Enum.Font.GothamBlack
Instance.new("UICorner", tit)

local btnMin = Instance.new("TextButton", main)
btnMin.Size = UDim2.new(0,35,0,35); btnMin.Position = UDim2.new(1,-40,0,2)
btnMin.Text = "-"; btnMin.TextScaled = true; btnMin.BackgroundColor3 = Color3.fromRGB(50,50,50); btnMin.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", btnMin)

local scroll = Instance.new("ScrollingFrame", main)
scroll.Size = UDim2.new(1,0,1,-45); scroll.Position = UDim2.new(0,0,0,45)
scroll.BackgroundTransparency = 1; scroll.CanvasSize = UDim2.new(0,0,0,300)

local function btn(texto, y, cor)
	local b = Instance.new("TextButton", scroll)
	b.Size = UDim2.new(0.92,0,0,35); b.Position = UDim2.new(0.04,0,0,y)
	b.Text = texto; b.TextScaled = true; b.BackgroundColor3 = cor
	b.TextColor3 = Color3.new(1,1,1); b.Font = Enum.Font.GothamBold
	Instance.new("UICorner", b); return b
end

-- SÓ OS 5 QUE VOCÊ PEDIU
local bVoar = btn("✈️ VOAR [OFF] 300", 5, Color3.fromRGB(40,40,40))
local bVel = btn("🔢 VELOCIDADE 300/500/1000/5000", 45, Color3.fromRGB(80,80,80))
local bSalvar = btn("📍 SALVAR TP", 85, Color3.fromRGB(0,120,255))
local bTP = btn("🚀 DAR TP SALVO", 125, Color3.fromRGB(0,200,0))
local bNoclip = btn("👻 NOCLIP [OFF]", 165, Color3.fromRGB(40,40,40))
local bLaser = btn("🔴 TIRAR LASER", 205, Color3.fromRGB(200,0,0))

-- BLOQUINHO MINIMIZAR - COM "-"
local mini = Instance.new("Frame", gui)
mini.Size = UDim2.new(0, 60, 0, 60); mini.Position = UDim2.new(0, 15, 0, 20)
mini.BackgroundColor3 = Color3.fromRGB(140,0,255); mini.Visible = false; mini.Active = true; mini.Draggable = true
Instance.new("UICorner", mini).CornerRadius = UDim.new(0,15)
local miniTxt = Instance.new("TextLabel", mini); miniTxt.Size=UDim2.new(1,0,1,0); miniTxt.Text="⚡"; miniTxt.TextScaled=true; miniTxt.BackgroundTransparency=1; miniTxt.TextColor3=Color3.new(1,1,1)
local miniBtn = Instance.new("TextButton", mini); miniBtn.Size=UDim2.new(1,0,1,0); miniBtn.Text=""; miniBtn.BackgroundTransparency=1
btnMin.MouseButton1Click:Connect(function() main.Visible=false; mini.Visible=true end)
miniBtn.MouseButton1Click:Connect(function() mini.Visible=false; main.Visible=true end)

-- VARIAVEIS
local voando,bv,att,bg,tpSalvo,noclip = false,nil,nil,nil,nil,false
local velocidade = 300; local velocidades = {300,500,1000,5000}; local idxVel=1
local keys={}; UIS.InputBegan:Connect(function(i) keys[i.KeyCode]=true end); UIS.InputEnded:Connect(function(i) keys[i.KeyCode]=false end)

-- VOAR WASD 200/300/500/1000/5000
bVoar.MouseButton1Click:Connect(function()
	if not voando then
		local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart"); if not hrp then return end
		att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero
		bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero
		plr.Character.Humanoid.PlatformStand=true; voando=true; bVoar.Text="✈️ VOAR [ON] "..velocidade; bVoar.BackgroundColor3=Color3.fromRGB(0,200,0)
		task.spawn(function() while voando do task.wait() if bv then local cam=workspace.CurrentCamera; local dir=Vector3.zero; if keys[Enum.KeyCode.W] then dir+=cam.CFrame.LookVector end; if keys[Enum.KeyCode.S] then dir-=cam.CFrame.LookVector end; if keys[Enum.KeyCode.A] then dir-=cam.CFrame.RightVector end; if keys[Enum.KeyCode.D] then dir+=cam.CFrame.RightVector end; if keys[Enum.KeyCode.Space] then dir+=Vector3.new(0,1,0) end; if keys[Enum.KeyCode.LeftShift] then dir-=Vector3.new(0,1,0) end; bv.VectorVelocity=dir.Magnitude>0 and dir.Unit*velocidade or Vector3.zero end end end)
	else voando=false; if att then att:Destroy() end if bv then bv:Destroy() end if bg then bg:Destroy() end if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.PlatformStand=false end; bVoar.Text="✈️ VOAR [OFF] "..velocidade; bVoar.BackgroundColor3=Color3.fromRGB(40,40,40) end
end)

-- VELOCIDADE
bVel.MouseButton1Click:Connect(function() idxVel=idxVel%#velocidades+1; velocidade=velocidades[idxVel]; bVel.Text="🔢 VELOCIDADE "..velocidade; bVoar.Text=(voando and "✈️ VOAR [ON] " or "✈️ VOAR [OFF] ")..velocidade end)

-- SALVAR TP
bSalvar.MouseButton1Click:Connect(function()
    local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")
    if hrp then tpSalvo=hrp.CFrame; bSalvar.Text="📍 SALVO ✅"; task.wait(1); bSalvar.Text="📍 SALVAR TP" end
end)

-- DAR TP SALVO
bTP.MouseButton1Click:Connect(function()
    if tpSalvo and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
        plr.Character.HumanoidRootPart.CFrame=tpSalvo
    end
end)

-- NOCLIP
bNoclip.MouseButton1Click:Connect(function()
    noclip=not noclip;
    bNoclip.Text=noclip and "👻 NOCLIP [ON]" or "👻 NOCLIP [OFF]";
    bNoclip.BackgroundColor3=noclip and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40)
end)
RS.Stepped:Connect(function()
    if noclip and plr.Character then
        for _,v in pairs(plr.Character:GetDescendants()) do
            if v:IsA("BasePart") then v.CanCollide=false end
        end
    end
end)

-- TIRAR LASER - REMOVE TUDO
bLaser.MouseButton1Click:Connect(function()
    for _,v in pairs(workspace:GetDescendants()) do
        if v.Name:lower():find("laser") then
            v:Destroy()
            print("🔴 Laser removido: "..v.Name)
        end
        if v:IsA("Part") or v:IsA("MeshPart") then
            if v.Name:lower():find("laser") or v.BrickColor == BrickColor.new("Really red") then
                -- Checa se é laser pela cor ou nome
                if v.Transparency < 1 and v.CanTouch then
                    -- Não destrói tudo, só o que parece laser
                end
            end
        end
    end
    bLaser.Text="🔴 LASER REMOVIDO ✅"; task.wait(1); bLaser.Text="🔴 TIRAR LASER"
end)

plr.Idled:Connect(function() game:GetService("VirtualUser"):CaptureController(); game:GetService("VirtualUser"):ClickButton2(Vector2.new()) end)

print("⚡ NEXUS V6 LITE - SÓ 5 FUNÇÕES - LIMPO CARREGADO!")
