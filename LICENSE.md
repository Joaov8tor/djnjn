-- Criação do GUI
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local OpenCloseButton = Instance.new("TextButton")
local SpeedTextBox = Instance.new("TextBox")
local SetSpeedButton = Instance.new("TextButton")

-- Propriedades do GUI
ScreenGui.Name = "SpeedHub"
ScreenGui.Parent = game.CoreGui

MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
MainFrame.Position = UDim2.new(0.5, -100, 0.5, -75)
MainFrame.Size = UDim2.new(0, 200, 0, 150)
MainFrame.Visible = true -- Painel inicialmente visível

OpenCloseButton.Name = "OpenCloseButton"
OpenCloseButton.Parent = ScreenGui
OpenCloseButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
OpenCloseButton.Position = UDim2.new(0, 10, 0, 10)
OpenCloseButton.Size = UDim2.new(0, 100, 0, 50)
OpenCloseButton.Text = "Abrir/Fechar"

SpeedTextBox.Name = "SpeedTextBox"
SpeedTextBox.Parent = MainFrame
SpeedTextBox.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
SpeedTextBox.Position = UDim2.new(0.1, 0, 0.2, 0)
SpeedTextBox.Size = UDim2.new(0, 160, 0, 40)
SpeedTextBox.Text = "Digite a Velocidade"
SpeedTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)

SetSpeedButton.Name = "SetSpeedButton"
SetSpeedButton.Parent = MainFrame
SetSpeedButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
SetSpeedButton.Position = UDim2.new(0.1, 0, 0.6, 0)
SetSpeedButton.Size = UDim2.new(0, 160, 0, 40)
SetSpeedButton.Text = "Definir Velocidade"

-- Abrir/Fechar painel
OpenCloseButton.MouseButton1Click:Connect(function()
    MainFrame.Visible = not MainFrame.Visible
end)

-- Definir velocidade do personagem
SetSpeedButton.MouseButton1Click:Connect(function()
    local speedValue = tonumber(SpeedTextBox.Text)
    if speedValue then
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        
        if humanoid then
            humanoid.WalkSpeed = speedValue
            print("Velocidade definida para:", speedValue)
        else
            print("Erro: Humanoid não encontrado!")
        end
    else
        print("Por favor, insira um número válido!")
    end
end)
