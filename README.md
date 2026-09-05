-- ⚡ NEXUS SCRIPT V2.3 - COM MINIMIZAR PRA BLOQUINHO
local plr = game.Players.LocalPlayer
local UIS = game:GetService("UserInputService")
local RS = game:GetService("RunService")
local Players = game:GetService("Players")

local gui = Instance.new("ScreenGui", plr.PlayerGui)
gui.Name = "NexusV2_3"; gui.ResetOnSpawn = false

-- MENU PRINCIPAL
local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 290, 0, 500)
main.Position = UDim2.new(0, 15, 0, 20)
main.BackgroundColor3 = Color3.fromRGB(12,12,12)
main.Active = true; main.Draggable = true
Instance.new("UICorner", main)
local stroke = Instance.new("UIStroke", main); stroke.Color = Color3.fromRGB(140,0,255); stroke.Thickness = 2

local tit = Instance.new("TextLabel", main)
tit.Size = UDim2.new(0.65,0,0,40); tit.Position = UDim2.new(0,0,0,0)
tit.Text = "⚡ Nexus Script"; tit.TextScaled = true
tit.BackgroundColor3 = Color3.fromRGB(140,0,255); tit.TextColor3 = Color3.new(1,1,1); tit.Font = Enum.Font.GothamBlack
Instance.new("UICorner", tit)

-- BOTÃO MINIMIZAR -
local btnMin = Instance.new("TextButton", main)
btnMin.Size = UDim2.new(0,35,0,35); btnMin.Position = UDim2.new(1,-80,0,2)
btnMin.Text = "-"; btnMin.TextScaled = true; btnMin.Font = Enum.Font.GothamBlack
btnMin.BackgroundColor3 = Color3.fromRGB(50,50,50); btnMin.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", btnMin)

-- BOTÃO FECHAR X
local btnClose = Instance.new("TextButton", main)
btnClose.Size = UDim2.new(0,35,0,35); btnClose.Position = UDim2.new(1,-40,0,2)
btnClose.Text = "X"; btnClose.TextScaled = true; btnClose.Font = Enum.Font.GothamBold
btnClose.BackgroundColor3 = Color3.fromRGB(200,0,0); btnClose.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", btnClose)

local scroll = Instance.new("ScrollingFrame", main)
scroll.Size = UDim2.new(1,0,1,-45); scroll.Position = UDim2.new(0,0,0,45)
scroll.BackgroundTransparency = 1; scroll.CanvasSize = UDim2.new(0,0,0,500)
scroll.ScrollBarThickness = 4

local function btn(texto, y, cor)
	local b = Instance.new("TextButton", scroll)
	b.Size = UDim2.new(0.92,0,0,32); b.Position = UDim2.new(0.04,0,0,y)
	b.Text = texto; b.TextScaled = true; b.BackgroundColor3 = cor
	b.TextColor3 = Color3.new(1,1,1); b.Font = Enum.Font.GothamBold
	Instance.new("UICorner", b); return b
end

local bVoar = btn("✈️ VOAR [OFF] - 300", 5, Color3.fromRGB(40,40,40))
local bSalvar = btn("📍 SALVAR TP", 42, Color3.fromRGB(0,120,255))
local bTP = btn("🚀 DAR TP SALVO", 79, Color3.fromRGB(0,200,0))
local bPlayers = btn("👤 TP PLAYER [LISTA]", 116, Color3.fromRGB(0,150,255))
local bBases = btn("🏠 TP BASE [LISTA NOMES]", 153, Color3.fromRGB(150,0,255))
local bRoubar = btn("💸 ROUBAR TUDO", 190, Color3.fromRGB(255,150,0))
local bAuto = btn("💰 AUTO ROUBAR [OFF]", 227, Color3.fromRGB(40,40,40))
local bNoclip = btn("👻 NOCLIP [OFF]", 264, Color3.fromRGB(40,40,40))
local bLaser = btn("🔴 TIRAR LASER", 301, Color3.fromRGB(200,0,0))
local bCash = btn("💵 CASH 999M", 338, Color3.fromRGB(40,40,40))

-- BLOQUINHO MINIMIZADO (QUANDO CLICA NO -)
local mini = Instance.new("Frame", gui)
mini.Size = UDim2.new(0, 60, 0, 60)
mini.Position = UDim2.new(0, 15, 0, 20)
mini.BackgroundColor3 = Color3.fromRGB(140,0,255)
mini.Visible = false
mini.Active = true
mini.Draggable = true
Instance.new("UICorner", mini).CornerRadius = UDim.new(0, 15)
local strokeMini = Instance.new("UIStroke", mini); strokeMini.Color = Color3.fromRGB(255,255,255); strokeMini.Thickness = 2

local miniTxt = Instance.new("TextLabel", mini)
miniTxt.Size = UDim2.new(1,0,1,0)
miniTxt.Text = "⚡"
miniTxt.TextScaled = true
miniTxt.BackgroundTransparency = 1
miniTxt.TextColor3 = Color3.new(1,1,1)
miniTxt.Font = Enum.Font.GothamBlack

local miniBtn = Instance.new("TextButton", mini)
miniBtn.Size = UDim2.new(1,0,1,0)
miniBtn.Text = ""
miniBtn.BackgroundTransparency = 1

-- FRAME LISTA
local listaFrame = Instance.new("Frame", gui)
listaFrame.Size = UDim2.new(0, 310, 0, 450)
listaFrame.Position = UDim2.new(0, 320, 0, 20)
listaFrame.BackgroundColor3 = Color3.fromRGB(12,12,12)
listaFrame.Visible = false; listaFrame.Active = true; listaFrame.Draggable = true
Instance.new("UICorner", listaFrame)
local stroke2 = Instance.new("UIStroke", listaFrame); stroke2.Color = Color3.fromRGB(0,150,255); stroke2.Thickness = 2

local listaTit = Instance.new("TextLabel", listaFrame)
listaTit.Size = UDim2.new(0.85,0,0,35); listaTit.Text = "LISTA"; listaTit.TextScaled = true
listaTit.BackgroundColor3 = Color3.fromRGB(0,150,255); listaTit.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", listaTit)

local fechar = Instance.new("TextButton", listaFrame)
fechar.Size = UDim2.new(0,30,0,30); fechar.Position = UDim2.new(1,-35,0,2)
fechar.Text = "X"; fechar.TextScaled = true; fechar.BackgroundColor3 = Color3.fromRGB(255,0,0)
fechar.TextColor3 = Color3.new(1,1,1); Instance.new("UICorner", fechar)

local listaScroll = Instance.new("ScrollingFrame", listaFrame)
listaScroll.Size = UDim2.new(1,0,1,-40); listaScroll.Position = UDim2.new(0,0,0,40)
listaScroll.BackgroundTransparency = 1; listaScroll.CanvasSize = UDim2.new(0,0,0,0)
listaScroll.ScrollBarThickness = 5

-- LÓGICA MINIMIZAR / MAXIMIZAR
btnMin.MouseButton1Click:Connect(function()
	main.Visible = false
	mini.Visible = true
	listaFrame.Visible = false
end)

miniBtn.MouseButton1Click:Connect(function()
	mini.Visible = false
	main.Visible = true
end)

btnClose.MouseButton1Click:Connect(function()
	gui:Destroy()
end)

fechar.MouseButton1Click:Connect(function() listaFrame.Visible = false end)

-- RESTO DAS FUNÇÕES
local voando,bv,att,bg,tpSalvo,noclip,autoRoubo = false,nil,nil,nil,nil,false,false
local velocidade = 300
local keys = {}
UIS.InputBegan:Connect(function(i) keys[i.KeyCode]=true end)
UIS.InputEnded:Connect(function(i) keys[i.KeyCode]=false end)

bVoar.MouseButton1Click:Connect(function()
	if not voando then
		local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart"); if not hrp then return end
		att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero
		bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero
		plr.Character.Humanoid.PlatformStand=true; voando=true; bVoar.Text="✈️ VOAR [ON] - "..velocidade; bVoar.BackgroundColor3=Color3.fromRGB(0,200,0)
		task.spawn(function() while voando do task.wait() if bv then local cam=workspace.CurrentCamera; local dir=Vector3.zero; if keys[Enum.KeyCode.W] then dir+=cam.CFrame.LookVector end; if keys[Enum.KeyCode.S] then dir-=cam.CFrame.LookVector end; if keys[Enum.KeyCode.A] then dir-=cam.CFrame.RightVector end; if keys[Enum.KeyCode.D] then dir+=cam.CFrame.RightVector end; if keys[Enum.KeyCode.Space] then dir+=Vector3.new(0,1,0) end; if keys[Enum.KeyCode.LeftShift] then dir-=Vector3.new(0,1,0) end; bv.VectorVelocity=dir.Magnitude>0 and dir.Unit*velocidade or Vector3.zero end end end)
	else voando=false; if att then att:Destroy() end if bv then bv:Destroy() end if bg then bg:Destroy() end if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.PlatformStand=false end; bVoar.Text="✈️ VOAR [OFF] - "..velocidade; bVoar.BackgroundColor3=Color3.fromRGB(40,40,40) end
end)

bSalvar.MouseButton1Click:Connect(function() local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") if hrp then tpSalvo=hrp.CFrame; bSalvar.Text="📍 SALVO ✅"; task.wait(1); bSalvar.Text="📍 SALVAR TP" end end)
bTP.MouseButton1Click:Connect(function() if tpSalvo and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then plr.Character.HumanoidRootPart.CFrame=tpSalvo end end)

local function mostrarPlayers()
	listaFrame.Visible = true; listaTit.Text = "👤 PLAYERS - CLICA PRA DAR TP"; listaTit.BackgroundColor3 = Color3.fromRGB(0,150,255); stroke2.Color = Color3.fromRGB(0,150,255)
	for _,c in pairs(listaScroll:GetChildren()) do if c:IsA("TextButton") then c:Destroy() end end
	local y=5
	for _,p in pairs(Players:GetPlayers()) do if p~=plr then
		local b = Instance.new("TextButton", listaScroll); b.Size = UDim2.new(0.92,0,0,35); b.Position = UDim2.new(0.04,0,0,y); b.Text = "👤 "..p.Name.." [TP]"; b.TextScaled = true; b.BackgroundColor3 = Color3.fromRGB(40,40,40); b.TextColor3 = Color3.new(1,1,1); Instance.new("UICorner", b)
		b.MouseButton1Click:Connect(function() if p.Character and p.Character:FindFirstChild("HumanoidRootPart") and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then plr.Character.HumanoidRootPart.CFrame = p.Character.HumanoidRootPart.CFrame + Vector3.new(0,3,2) end end)
		y+=40 end end; listaScroll.CanvasSize = UDim2.new(0,0,0,y)
end

local function mostrarBases()
	listaFrame.Visible = true; listaTit.Text = "🏠 BASES - NOME DOS DONOS"; listaTit.BackgroundColor3 = Color3.fromRGB(150,0,255); stroke2.Color = Color3.fromRGB(150,0,255)
	for _,c in pairs(listaScroll:GetChildren()) do if c:IsA("TextButton") then c:Destroy() end end
	local y=5; local basesAchadas = {}
	for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") and obj.Text:lower():find("base") then local model = obj:FindFirstAncestorOfClass("Model"); if model and not basesAchadas[model] then basesAchadas[model]=true; local dono = obj.Text; local pos = model:GetBoundingBox(); local b = Instance.new("TextButton", listaScroll); b.Size = UDim2.new(0.92,0,0,35); b.Position = UDim2.new(0.04,0,0,y); b.Text = "🏠 "..dono.." [TP]"; b.TextScaled = true; b.BackgroundColor3 = dono:lower():find("empty") and Color3.fromRGB(60,60,60) or Color3.fromRGB(0,120,0); b.TextColor3 = Color3.new(1,1,1); Instance.new("UICorner", b); b.MouseButton1Click:Connect(function() if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then plr.Character.HumanoidRootPart.CFrame = CFrame.new(pos) + Vector3.new(0,5,0) end end); y+=40 end end end; listaScroll.CanvasSize = UDim2.new(0,0,0,y)
end

bPlayers.MouseButton1Click:Connect(mostrarPlayers)
bBases.MouseButton1Click:Connect(mostrarBases)
bRoubar.MouseButton1Click:Connect(function() for _,v in pairs(workspace:GetDescendants()) do if v:IsA("ProximityPrompt") then pcall(function() fireproximityprompt(v) end) end end end)
bAuto.MouseButton1Click:Connect(function() autoRoubo=not autoRoubo; bAuto.Text=autoRoubo and "💰 AUTO ROUBAR [ON]" or "💰 AUTO ROUBAR [OFF]"; bAuto.BackgroundColor3=autoRoubo and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
task.spawn(function() while true do task.wait(0.1) if autoRoubo and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then for _,v in pairs(workspace:GetDescendants()) do if v:IsA("ProximityPrompt") and v.Parent and (plr.Character.HumanoidRootPart.Position - v.Parent.Position).Magnitude < 25 then pcall(function() fireproximityprompt(v) end) end end end end end)
bNoclip.MouseButton1Click:Connect(function() noclip=not noclip; bNoclip.Text=noclip and "👻 NOCLIP [ON]" or "👻 NOCLIP [OFF]"; bNoclip.BackgroundColor3=noclip and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
RS.Stepped:Connect(function() if noclip and plr.Character then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end end end)
bLaser.MouseButton1Click:Connect(function() for _,v in pairs(workspace:GetDescendants()) do if v.Name:lower():find("laser") then v:Destroy() end if v:IsA("BasePart") and v.Color==Color3.fromRGB(255,0,0) and v.Size.Y<10 then v.CanCollide=false; v.Transparency=1 end end end)
bCash.MouseButton1Click:Connect(function() if plr:FindFirstChild("leaderstats") then for _,v in pairs(plr.leaderstats:GetChildren()) do if v:IsA("ValueBase") then v.Value=999999999 end end end end)

print("⚡ Nexus V2.3 COM MINIMIZAR CARREGADO")
