-- Meta Hub
local MetaHub = {}

-- Configurações
MetaHub.godMode = false
MetaHub.autoBrainrot = false
MetaHub.teleportToBestBrainrot = false
MetaHub.infiniteJump = false
MetaHub.speedHack = false
MetaHub.flyMode = false
MetaHub.obterItens = false
MetaHub.matarInimigos = false
MetaHub.teleportarParaSpawn = false
MetaHub.ativarInvisivel = false

-- Função para criar o painel
local function criarPainel()
    local ScreenGui = Instance.new("ScreenGui")
    ScreenGui.Name = "MetaHub"
    ScreenGui.Parent = game.CoreGui

    local Frame = Instance.new("Frame")
    Frame.Size = UDim2.new(0.3, 0, 0.4, 0)
    Frame.Position = UDim2.new(0.35, 0, 0.3, 0)
    Frame.BackgroundColor3 = Color3.new(0, 0, 0)
    Frame.BackgroundTransparency = 0.5
    Frame.Parent = ScreenGui

    local XButton = Instance.new("TextButton")
    XButton.Size = UDim2.new(0.05, 0, 0.05, 0)
    XButton.Position = UDim2.new(0.95, 0, 0, 0)
    XButton.Text = "X"
    XButton.BackgroundColor3 = Color3.new(1, 0, 0)
    XButton.Parent = Frame
    XButton.MouseButton1Click:Connect(function()
        Frame.Size = UDim2.new(0.05, 0, 0.05, 0)
        Frame.Position = UDim2.new(0.95, 0, 0, 0)
        local PlusButton = Instance.new("TextButton")
        PlusButton.Size = UDim2.new(0.05, 0, 0.05, 0)
        PlusButton.Position = UDim2.new(0, 0, 0, 0)
        PlusButton.Text = "+"
        PlusButton.BackgroundColor3 = Color3.new(0, 1, 0)
        PlusButton.Parent = Frame
        PlusButton.MouseButton1Click:Connect(function()
            Frame.Size = UDim2.new(0.3, 0, 0.4, 0)
            Frame.Position = UDim2.new(0.35, 0, 0.3, 0)
            PlusButton:Destroy()
        end)
    end)

    local TabFrame = Instance.new("Frame")
    TabFrame.Size = UDim2.new(0.9, 0, 0.1, 0)
    TabFrame.Position = UDim2.new(0.05, 0, 0.1, 0)
    TabFrame.BackgroundColor3 = Color3.new(0, 0, 0)
    TabFrame.Parent = Frame

    local BrainrotTab = Instance.new("TextButton")
    BrainrotTab.Size = UDim2.new(0.2, 0, 0.1, 0)
    BrainrotTab.Position = UDim2.new(0, 0, 0, 0)
    BrainrotTab.Text = "Brainrot"
    BrainrotTab.BackgroundColor3 = Color3.new(1, 0, 0)
    BrainrotTab.Parent = TabFrame
    BrainrotTab.MouseButton1Click:Connect(function()
        MetaHub.autoBrainrot = true
        MetaHub.teleportToBestBrainrot = true
    end)

    local GodModeTab = Instance.new("TextButton")
    GodModeTab.Size = UDim2.new(0.2, 0, 0.1, 0)
    GodModeTab.Position = UDim2.new(0.25, 0, 0, 0)
    GodModeTab.Text = "God Mode"
    GodModeTab.BackgroundColor3 = Color3.new(1, 0, 0)
    GodModeTab.Parent = TabFrame
    GodModeTab.MouseButton1Click:Connect(function()
        MetaHub.godMode = true
        game.Players.LocalPlayer.Character.HumanoidRootPart.CanCollide = false
        game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0, 50, 0)
    end)

    local InfiniteJumpTab = Instance.new("TextButton")
    InfiniteJumpTab.Size = UDim2.new(0.2, 0, 0.1, 0)
    InfiniteJumpTab.Position = UDim2.new(0.5, 0, 0, 0)
    InfiniteJumpTab.Text = "Infinite Jump"
    InfiniteJumpTab.BackgroundColor3 = Color3.new(1, 0, 0)
    InfiniteJumpTab.Parent = TabFrame
    InfiniteJumpTab.MouseButton1Click:Connect(function()
        MetaHub.infiniteJump = true
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = 50
    end)

    local SpeedHackTab = Instance.new("TextButton")
    SpeedHackTab.Size = UDim2.new(0.2, 0, 0.1, 0)
    SpeedHackTab.Position = UDim2.new(0.75, 0, 0, 0)
    SpeedHackTab.Text = "Speed Hack"
    SpeedHackTab.BackgroundColor3 = Color3.new(1, 0, 0)
    SpeedHackTab.Parent = TabFrame
    SpeedHackTab.MouseButton1Click:Connect(function()
        MetaHub.speedHack = true
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 50
    end)

    local FlyModeTab = Instance.new("TextButton")
    FlyModeTab.Size = UDim2.new(0.2, 0, 0.1, 0)
    FlyModeTab.Position = UDim2.new(0, 0, 0.15, 0)
    FlyModeTab.Text = "Fly Mode"
    FlyModeTab.BackgroundColor3 = Color3.new(1, 0, 0)
    FlyModeTab.Parent = TabFrame
    FlyModeTab.MouseButton1Click:Connect(function()
        MetaHub.flyMode = true
        game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0, 50, 0)
    end)

    local ItensTab = Instance.new("TextButton")
    ItensTab.Size = UDim2.new(0.2, 0, 0.1, 0)
    ItensTab.Position = UDim2.new(0.25, 0, 0.15, 0)
    ItensTab.Text = "Itens"
    ItensTab.BackgroundColor3 = Color3.new(1, 0, 0)
    ItensTab.Parent = TabFrame
    ItensTab.MouseButton1Click:Connect(function()
        MetaHub.obterItens = true
        for _, item in pairs(game.Workspace.Items:GetChildren()) do
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = item.CFrame
            wait(0.1)
        end
    end)

    local InimigosTab = Instance.new("TextButton")
    InimigosTab.Size = UDim2.new(0.2, 0, 0.1, 0)
    InimigosTab.Position = UDim2.new(0.5, 0, 0.15, 0)
    InimigosTab.Text = "Matar Inimigos"
    InimigosTab.BackgroundColor3 = Color3.new(1, 0, 0)
    InimigosTab.Parent = TabFrame
    InimigosTab.MouseButton1Click:Connect(function()
        MetaHub.matarInimigos = true
        for _, inimigo in pairs(game.Workspace.Inimigos:GetChildren()) do
            inimigo.Humanoid.Health = 0
            wait(0.1)
        end
    end)

    local SpawnTab = Instance.new("TextButton")
    SpawnTab.Size = UDim2.new(0.2, 0, 0.1, 0)
    SpawnTab.Position = UDim2.new(0.75, 0, 0.15, 0)
    SpawnTab.Text = "Teleportar para Spawn"
    SpawnTab.BackgroundColor3 = Color3.new(1, 0, 0)
    SpawnTab.Parent = TabFrame
    SpawnTab.MouseButton1Click:Connect(function()
        MetaHub.teleportarParaSpawn = true
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Workspace.SpawnLocation.CFrame
    end)

    local InvisivelTab = Instance.new("TextButton")
    InvisivelTab.Size = UDim2.new(0.2, 0, 0.1, 0)
    InvisivelTab.Position = UDim2.new(0, 0, 0.3, 0)
    InvisivelTab.Text = "Ativar Invisível"
    InvisivelTab.BackgroundColor3 = Color3.new(1, 0, 0)
    InvisivelTab.Parent = TabFrame
    InvisivelTab.MouseButton1Click:Connect(function()
        MetaHub.ativarInvisivel = true
        game.Players.LocalPlayer.Character.HumanoidRootPart.Transparency =
        # Meta-hub
