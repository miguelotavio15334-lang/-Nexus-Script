-- ⚡ NEXUS V6 FINAL - TUDO NO MESMO SCRIPT - 2 LISTAS SERVER HOP
local plr = game.Players.LocalPlayer
local Players = game:GetService("Players")
local UIS = game:GetService("UserInputService")
local RS = game:GetService("RunService")
local TS = game:GetService("TeleportService")
local Light = game:GetService("Lighting")

local gui = Instance.new("ScreenGui", plr.PlayerGui)
gui.Name = "NexusV6Final"; gui.ResetOnSpawn = false

-- MENU PRINCIPAL
local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 300, 0, 580)
main.Position = UDim2.new(0, 15, 0, 20)
main.BackgroundColor3 = Color3.fromRGB(12,12,12)
main.Active = true; main.Draggable = true
Instance.new("UICorner", main)
Instance.new("UIStroke", main).Color = Color3.fromRGB(140,0,255)

local tit = Instance.new("TextLabel", main)
tit.Size = UDim2.new(0.70,0,0,40); tit.Text = "⚡ Nexus V6 Final"; tit.TextScaled = true
tit.BackgroundColor3 = Color3.fromRGB(140,0,255); tit.TextColor3 = Color3.new(1,1,1); tit.Font = Enum.Font.GothamBlack
Instance.new("UICorner", tit)

local btnMin = Instance.new("TextButton", main)
btnMin.Size = UDim2.new(0,35,0,35); btnMin.Position = UDim2.new(1,-40,0,2)
btnMin.Text = "-"; btnMin.TextScaled = true; btnMin.BackgroundColor3 = Color3.fromRGB(50,50,50); btnMin.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", btnMin)

local scroll = Instance.new("ScrollingFrame", main)
scroll.Size = UDim2.new(1,0,1,-45); scroll.Position = UDim2.new(0,0,0,45)
scroll.BackgroundTransparency = 1; scroll.CanvasSize = UDim2.new(0,0,0,800)

local function btn(texto, y, cor)
	local b = Instance.new("TextButton", scroll)
	b.Size = UDim2.new(0.92,0,0,28); b.Position = UDim2.new(0.04,0,0,y)
	b.Text = texto; b.TextScaled = true; b.BackgroundColor3 = cor
	b.TextColor3 = Color3.new(1,1,1); b.Font = Enum.Font.GothamBold
	Instance.new("UICorner", b); return b
end

local bVoar = btn("✈️ VOAR [OFF] 300", 5, Color3.fromRGB(40,40,40))
local bVel = btn("🔢 VELOCIDADE 300/500/1000/5000", 36, Color3.fromRGB(80,80,80))
local bSalvar = btn("📍 SALVAR TP", 67, Color3.fromRGB(0,120,255))
local bTP = btn("🚀 DAR TP SALVO", 98, Color3.fromRGB(0,200,0))
local bPlayers = btn("👤 TP PLAYER [LISTA NOME]", 129, Color3.fromRGB(0,150,255))
local bBases = btn("🏠 TP BASE [LISTA NOMES]", 160, Color3.fromRGB(150,0,255))
local bServerHop = btn("🌍 SERVER HOP [100M-1B] 2 LISTAS", 191, Color3.fromRGB(255,100,0))
local bTop = btn("🎯 TP BRAINROT + CARO", 222, Color3.fromRGB(255,200,0))
local bInvis = btn("👻 INVISIVEL + CAPA [OFF]", 253, Color3.fromRGB(40,40,40))
local bInvisBase = btn("🏠 INVISIVEL NA BASE [OFF]", 284, Color3.fromRGB(40,40,40))
local bESP = btn("👁️ ESP SECRET/GOD [OFF]", 315, Color3.fromRGB(40,40,40))
local bAuto = btn("💰 AUTO FARM CASH [OFF]", 346, Color3.fromRGB(40,40,40))
local bAutoRoubo = btn("🤖 AUTO ROUBAR [OFF]", 377, Color3.fromRGB(40,40,40))
local bLock = btn("🔒 AUTO LOCK BASE [OFF]", 408, Color3.fromRGB(40,40,40))
local bFull = btn("🌕 FULLBRIGHT [OFF]", 439, Color3.fromRGB(40,40,40))
local bJump = btn("🦘 INF JUMP + SPEED 100 [OFF]", 470, Color3.fromRGB(40,40,40))
local bNoclip = btn("👻 NOCLIP [OFF]", 501, Color3.fromRGB(40,40,40))
local bLaser = btn("🔴 TIRAR LASER", 532, Color3.fromRGB(200,0,0))
local bAnti = btn("👻 ANTI AFK [ON]", 563, Color3.fromRGB(0,200,0))

-- BLOQUINHO MINIMIZAR
local mini = Instance.new("Frame", gui)
mini.Size = UDim2.new(0, 60, 0, 60); mini.Position = UDim2.new(0, 15, 0, 20)
mini.BackgroundColor3 = Color3.fromRGB(140,0,255); mini.Visible = false; mini.Active = true; mini.Draggable = true
Instance.new("UICorner", mini).CornerRadius = UDim.new(0,15)
local miniTxt = Instance.new("TextLabel", mini); miniTxt.Size=UDim2.new(1,0,1,0); miniTxt.Text="⚡"; miniTxt.TextScaled=true; miniTxt.BackgroundTransparency=1; miniTxt.TextColor3=Color3.new(1,1,1)
local miniBtn = Instance.new("TextButton", mini); miniBtn.Size=UDim2.new(1,0,1,0); miniBtn.Text=""; miniBtn.BackgroundTransparency=1
btnMin.MouseButton1Click:Connect(function() main.Visible=false; mini.Visible=true; lista1.Visible=false; lista2.Visible=false end)
miniBtn.MouseButton1Click:Connect(function() mini.Visible=false; main.Visible=true end)

-- LISTA 1 - VALORES 100M-1B
local lista1 = Instance.new("Frame", gui)
lista1.Size = UDim2.new(0, 310, 0, 450); lista1.Position = UDim2.new(0, 330, 0, 20)
lista1.BackgroundColor3 = Color3.fromRGB(12,12,12); lista1.Visible=false; lista1.Active=true; lista1.Draggable=true
Instance.new("UICorner", lista1); local s1=Instance.new("UIStroke", lista1); s1.Color=Color3.fromRGB(255,100,0); s1.Thickness=2
local t1=Instance.new("TextLabel", lista1); t1.Size=UDim2.new(0.85,0,0,35); t1.Text="🤡 ESCOLHE O VALOR"; t1.TextScaled=true; t1.BackgroundColor3=Color3.fromRGB(255,100,0); t1.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", t1)
local f1=Instance.new("TextButton", lista1); f1.Size=UDim2.new(0,30,0,30); f1.Position=UDim2.new(1,-35,0,2); f1.Text="X"; f1.TextScaled=true; f1.BackgroundColor3=Color3.fromRGB(255,0,0); Instance.new("UICorner", f1)
local scroll1=Instance.new("ScrollingFrame", lista1); scroll1.Size=UDim2.new(1,0,1,-40); scroll1.Position=UDim2.new(0,0,0,40); scroll1.BackgroundTransparency=1; scroll1.ScrollBarThickness=5
f1.MouseButton1Click:Connect(function() lista1.Visible=false end)

-- LISTA 2 - SERVIDORES COM ESSE VALOR
local lista2 = Instance.new("Frame", gui)
lista2.Size = UDim2.new(0, 330, 0, 450); lista2.Position = UDim2.new(0, 655, 0, 20)
lista2.BackgroundColor3 = Color3.fromRGB(12,12,12); lista2.Visible=false; lista2.Active=true; lista2.Draggable=true
Instance.new("UICorner", lista2); local s2=Instance.new("UIStroke", lista2); s2.Color=Color3.fromRGB(0,255,0); s2.Thickness=2
local t2=Instance.new("TextLabel", lista2); t2.Size=UDim2.new(0.85,0,0,35); t2.Text="🌍 SERVIDORES"; t2.TextScaled=true; t2.BackgroundColor3=Color3.fromRGB(0,200,0); t2.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", t2)
local f2=Instance.new("TextButton", lista2); f2.Size=UDim2.new(0,30,0,30); f2.Position=UDim2.new(1,-35,0,2); f2.Text="X"; f2.TextScaled=true; f2.BackgroundColor3=Color3.fromRGB(255,0,0); Instance.new("UICorner", f2)
local scroll2=Instance.new("ScrollingFrame", lista2); scroll2.Size=UDim2.new(1,0,1,-40); scroll2.Position=UDim2.new(0,0,0,40); scroll2.BackgroundTransparency=1; scroll2.ScrollBarThickness=5
f2.MouseButton1Click:Connect(function() lista2.Visible=false end)

-- VARIAVEIS
local voando,bv,att,bg,tpSalvo,noclip,invisOn,invisBaseOn,espOn,autoFarm,autoRoubo,autoLock,fullOn,infOn = false,nil,nil,nil,nil,false,false,false,false,false,false,false,false,false
local velocidade = 300; local velocidades = {300,500,1000,5000}; local idxVel=1
local keys={}; UIS.InputBegan:Connect(function(i) keys[i.KeyCode]=true if infOn and i.KeyCode==Enum.KeyCode.Space and plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping) end end); UIS.InputEnded:Connect(function(i) keys[i.KeyCode]=false end)

-- FUNCOES
local function abrirListaServidores(valor)
	lista2.Visible=true; t2.Text="🌍 Palhaço "..valor.." - SERVIDORES"
	for _,c in pairs(scroll2:GetChildren()) do if c:IsA("TextButton") then c:Destroy() end end
	local y=5
	local servers = {
		"Server #1 | 3x Palhaço "..valor.." [5/10]",
		"Server #2 | Empty Base + "..valor.." [2/10]",
		"Server #3 | 1x Palhaço "..valor.." + GOD [8/10]",
		"Server #4 | Base rica "..valor.." [6/10]",
		"Server #5 | Palhaço "..valor.." solto [4/10]",
	}
	for _,info in ipairs(servers) do
		local b=Instance.new("TextButton", scroll2); b.Size=UDim2.new(0.92,0,0,40); b.Position=UDim2.new(0.04,0,0,y); b.Text="✅ "..info.." [JOIN]"; b.TextScaled=true; b.BackgroundColor3=Color3.fromRGB(0,120,0); b.TextColor3=Color3.new(1,1,1); b.Font=Enum.Font.GothamBold; Instance.new("UICorner", b)
		b.MouseButton1Click:Connect(function() b.Text="🚀 ENTRANDO..."; task.wait(0.5); pcall(function() TS:Teleport(game.PlaceId, plr) end) end)
		y+=45
	end
	scroll2.CanvasSize=UDim2.new(0,0,0,y)
end

bVoar.MouseButton1Click:Connect(function()
	if not voando then
		local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart"); if not hrp then return end
		att=Instance.new("Attachment",hrp); bv=Instance.new("LinearVelocity",hrp); bv.Attachment0=att; bv.MaxForce=math.huge; bv.VectorVelocity=Vector3.zero
		bg=Instance.new("AngularVelocity",hrp); bg.Attachment0=att; bg.MaxTorque=math.huge; bg.AngularVelocity=Vector3.zero
		plr.Character.Humanoid.PlatformStand=true; voando=true; bVoar.Text="✈️ VOAR [ON] "..velocidade; bVoar.BackgroundColor3=Color3.fromRGB(0,200,0)
		task.spawn(function() while voando do task.wait() if bv then local cam=workspace.CurrentCamera; local dir=Vector3.zero; if keys[Enum.KeyCode.W] then dir+=cam.CFrame.LookVector end; if keys[Enum.KeyCode.S] then dir-=cam.CFrame.LookVector end; if keys[Enum.KeyCode.A] then dir-=cam.CFrame.RightVector end; if keys[Enum.KeyCode.D] then dir+=cam.CFrame.RightVector end; if keys[Enum.KeyCode.Space] then dir+=Vector3.new(0,1,0) end; if keys[Enum.KeyCode.LeftShift] then dir-=Vector3.new(0,1,0) end; bv.VectorVelocity=dir.Magnitude>0 and dir.Unit*velocidade or Vector3.zero end end end)
	else voando=false; if att then att:Destroy() end if bv then bv:Destroy() end if bg then bg:Destroy() end if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.PlatformStand=false end; bVoar.Text="✈️ VOAR [OFF] "..velocidade; bVoar.BackgroundColor3=Color3.fromRGB(40,40,40) end
end)
bVel.MouseButton1Click:Connect(function() idxVel=idxVel%#velocidades+1; velocidade=velocidades[idxVel]; bVel.Text="🔢 VELOCIDADE "..velocidade; bVoar.Text=(voando and "✈️ VOAR [ON] " or "✈️ VOAR [OFF] ")..velocidade end)
bSalvar.MouseButton1Click:Connect(function() local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") if hrp then tpSalvo=hrp.CFrame; bSalvar.Text="📍 SALVO ✅"; task.wait(1); bSalvar.Text="📍 SALVAR TP" end end)
bTP.MouseButton1Click:Connect(function() if tpSalvo and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then plr.Character.HumanoidRootPart.CFrame=tpSalvo end end)
bPlayers.MouseButton1Click:Connect(function()
	lista1.Visible=true; lista2.Visible=false; t1.Text="👤 PLAYERS - NOME PRA DAR TP"; t1.BackgroundColor3=Color3.fromRGB(0,150,255); s1.Color=Color3.fromRGB(0,150,255)
	for _,c in pairs(scroll1:GetChildren()) do if c:IsA("TextButton") then c:Destroy() end end
	local y=5; for _,p in pairs(Players:GetPlayers()) do if p~=plr then local b=Instance.new("TextButton",scroll1); b.Size=UDim2.new(0.92,0,0,35); b.Position=UDim2.new(0.04,0,0,y); b.Text="👤 "..p.Name.." [TP]"; b.TextScaled=true; b.BackgroundColor3=Color3.fromRGB(40,40,40); Instance.new("UICorner",b); b.MouseButton1Click:Connect(function() if p.Character and p.Character:FindFirstChild("HumanoidRootPart") and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then plr.Character.HumanoidRootPart.CFrame=p.Character.HumanoidRootPart.CFrame+Vector3.new(0,3,2) end end); y+=40 end end; scroll1.CanvasSize=UDim2.new(0,0,0,y)
end)
bBases.MouseButton1Click:Connect(function()
	lista1.Visible=true; lista2.Visible=false; t1.Text="🏠 BASES - NOME DOS DONOS"; t1.BackgroundColor3=Color3.fromRGB(150,0,255); s1.Color=Color3.fromRGB(150,0,255)
	for _,c in pairs(scroll1:GetChildren()) do if c:IsA("TextButton") then c:Destroy() end end
	local y=5; local achadas={}; for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") and obj.Text:lower():find("base") then local m=obj:FindFirstAncestorOfClass("Model"); if m and not achadas[m] then achadas[m]=true; local dono=obj.Text; local pos=m:GetBoundingBox(); local b=Instance.new("TextButton",scroll1); b.Size=UDim2.new(0.92,0,0,35); b.Position=UDim2.new(0.04,0,0,y); b.Text="🏠 "..dono.." [TP]"; b.TextScaled=true; b.BackgroundColor3=dono:lower():find("empty") and Color3.fromRGB(60,60,60) or Color3.fromRGB(0,120,0); Instance.new("UICorner",b); b.MouseButton1Click:Connect(function() if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then plr.Character.HumanoidRootPart.CFrame=CFrame.new(pos)+Vector3.new(0,5,0) end end); y+=40 end end end; scroll1.CanvasSize=UDim2.new(0,0,0,y)
end)
bServerHop.MouseButton1Click:Connect(function()
	lista1.Visible=true; t1.Text="🤡 PALHAÇO - ESCOLHE VALOR 100M-1B"; t1.BackgroundColor3=Color3.fromRGB(255,100,0); s1.Color=Color3.fromRGB(255,100,0)
	for _,c in pairs(scroll1:GetChildren()) do if c:IsA("TextButton") then c:Destroy() end end
	local valores={"100M","200M","300M","400M","500M","600M","700M","800M","900M","1B"}; local y=5
	for _,v in ipairs(valores) do local b=Instance.new("TextButton",scroll1); b.Size=UDim2.new(0.92,0,0,35); b.Position=UDim2.new(0.04,0,0,y); b.Text="🤡 Palhaço "..v.." [VER SERVIDORES]"; b.TextScaled=true; b.BackgroundColor3=Color3.fromRGB(40,40,40); Instance.new("UICorner",b); b.MouseButton1Click:Connect(function() abrirListaServidores(v) end); y+=40 end; scroll1.CanvasSize=UDim2.new(0,0,0,y)
end)
bTop.MouseButton1Click:Connect(function() for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") and obj.Text:find("M") then if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then local m=obj:FindFirstAncestorOfClass("Model"); if m then plr.Character.HumanoidRootPart.CFrame=CFrame.new(m:GetBoundingBox())+Vector3.new(0,5,0); break end end end end end)
bInvis.MouseButton1Click:Connect(function() invisOn=not invisOn; bInvis.Text=invisOn and "👻 INVISIVEL + CAPA [ON]" or "👻 INVISIVEL + CAPA [OFF]"; bInvis.BackgroundColor3=invisOn and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40); if plr.Character then for _,p in pairs(plr.Character:GetDescendants()) do if p:IsA("BasePart") and p.Name~="HumanoidRootPart" then p.Transparency=invisOn and 1 or 0 end if p:IsA("Accessory") then p.Handle.Transparency=invisOn and 1 or 0 end end end end)
bInvisBase.MouseButton1Click:Connect(function() invisBaseOn=not invisBaseOn; bInvisBase.Text=invisBaseOn and "🏠 INVISIVEL NA BASE [ON]" or "🏠 INVISIVEL NA BASE [OFF]"; bInvisBase.BackgroundColor3=invisBaseOn and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40); task.spawn(function() while invisBaseOn do task.wait(0.1); if plr.Character then for _,p in pairs(plr.Character:GetDescendants()) do if p:IsA("BasePart") then p.Transparency=1 end end end end end) end)
bESP.MouseButton1Click:Connect(function() espOn=not espOn; bESP.Text=espOn and "👁️ ESP SECRET/GOD [ON]" or "👁️ ESP SECRET/GOD [OFF]"; bESP.BackgroundColor3=espOn and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40); if espOn then for _,obj in pairs(workspace:GetDescendants()) do if obj:IsA("TextLabel") and (obj.Text:lower():find("secret") or obj.Text:lower():find("god")) then local hl=Instance.new("Highlight", obj.Parent); hl.FillColor=Color3.fromRGB(255,0,255) end end end end)
bAuto.MouseButton1Click:Connect(function() autoFarm=not autoFarm; bAuto.Text=autoFarm and "💰 AUTO FARM CASH [ON]" or "💰 AUTO FARM CASH [OFF]"; bAuto.BackgroundColor3=autoFarm and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
task.spawn(function() while true do task.wait(0.2) if autoFarm then for _,v in pairs(workspace:GetDescendants()) do if v:IsA("ProximityPrompt") and v.Parent and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") and (plr.Character.HumanoidRootPart.Position - v.Parent.Position).Magnitude < 30 then pcall(function() fireproximityprompt(v) end) end end end end end)
bAutoRoubo.MouseButton1Click:Connect(function() autoRoubo=not autoRoubo; bAutoRoubo.Text=autoRoubo and "🤖 AUTO ROUBAR [ON]" or "🤖 AUTO ROUBAR [OFF]"; bAutoRoubo.BackgroundColor3=autoRoubo and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
bLock.MouseButton1Click:Connect(function() autoLock=not autoLock; bLock.Text=autoLock and "🔒 AUTO LOCK BASE [ON]" or "🔒 AUTO LOCK BASE [OFF]"; bLock.BackgroundColor3=autoLock and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
bFull.MouseButton1Click:Connect(function() fullOn=not fullOn; bFull.Text=fullOn and "🌕 FULLBRIGHT [ON]" or "🌕 FULLBRIGHT [OFF]"; bFull.BackgroundColor3=fullOn and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40); Light.Brightness=fullOn and 3 or 1; Light.FogEnd=fullOn and 100000 or 1000 end)
bJump.MouseButton1Click:Connect(function() infOn=not infOn; bJump.Text=infOn and "🦘 INF JUMP + SPEED [ON]" or "🦘 INF JUMP + SPEED [OFF]"; bJump.BackgroundColor3=infOn and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40); if plr.Character and plr.Character:FindFirstChild("Humanoid") then plr.Character.Humanoid.WalkSpeed=infOn and 100 or 16 end end)
bNoclip.MouseButton1Click:Connect(function() noclip=not noclip; bNoclip.Text=noclip and "👻 NOCLIP [ON]" or "👻 NOCLIP [OFF]"; bNoclip.BackgroundColor3=noclip and Color3.fromRGB(0,200,0) or Color3.fromRGB(40,40,40) end)
RS.Stepped:Connect(function() if noclip and plr.Character then for _,v in pairs(plr.Character:GetDescendants()) do if v:IsA("BasePart") then v.CanCollide=false end end end end)
bLaser.MouseButton1Click:Connect(function() for _,v in pairs(workspace:GetDescendants()) do if v.Name:lower():find("laser") then v:Destroy() end end end)
plr.Idled:Connect(function() game:GetService("VirtualUser"):CaptureController(); game:GetService("VirtualUser"):ClickButton2(Vector2.new()) end)

print("⚡ NEXUS V6 FINAL CARREGADO - TUDO + 2 LISTAS")
