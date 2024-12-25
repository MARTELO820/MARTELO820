-- Hub Moon: ESP Frutas

_G.CollectFruits = true -- Defina como false para desativar a coleta automática de frutas
_G.AutoSpinFruits = true -- Defina como false para desativar a rotação automática de frutas

-- Função para coletar frutas automaticamente
function CollectFruits()
    while _G.CollectFruits do
        for i, fruit in pairs(game.Workspace.Fruits:GetChildren()) do
            if fruit:IsA("BasePart") then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = fruit.CFrame
                wait(1) -- Espera 1 segundo antes de verificar a próxima fruta
            end
        end
        wait(10) -- Espera 10 segundos antes de verificar novamente
    end
end

-- Função para girar frutas automaticamente
function AutoSpinFruits()
    while _G.AutoSpinFruits do
        game:GetService("ReplicatedStorage").Remotes["SpinFruit"]:InvokeServer()
        wait(60) -- Espera 60 segundos antes de girar novamente
    end
end

-- Função para exibir nome e cor das frutas
function ESPFruits()
    for i, fruit in pairs(game.Workspace.Fruits:GetChildren()) do
        if fruit:IsA("BasePart") then
            local billboard = Instance.new("BillboardGui", fruit)
            billboard.Size = UDim2.new(2, 0, 2, 0)
            billboard.StudsOffset = Vector3.new(0, 3, 0)
            billboard.AlwaysOnTop = true

            local textLabel = Instance.new("TextLabel", billboard)
            textLabel.Size = UDim2.new(1, 0, 1, 0)
            textLabel.BackgroundTransparency = 1
            textLabel.Text = "Nome: " .. fruit.Name .. " Cor: Vermelho"
            textLabel.TextColor3 = Color3.new(1, 0, 0) -- Cor Vermelho
            textLabel.TextScaled = true
        end
    end
end

-- Iniciar funções
CollectFruits()
AutoSpinFruits()
ESPFruits()

print("Hub Moon Script ESP Frutas iniciado.")
