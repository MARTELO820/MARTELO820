-- Hub Moon: ESP Raids com opção de seleção

_G.ESP_Raids = true -- Defina como false para desativar o ESP de Raids
_G.CollectFruits = true -- Defina como false para desativar a coleta de frutas
_G.CollectMoney = false -- Defina como true para ativar a coleta de dinheiro

while _G.ESP_Raids do
    -- Função para exibir localização e informações de Raids
    for i, raid in pairs(game.Workspace.Raids:GetChildren()) do
        if raid:IsA("BasePart") then
            local billboard = Instance.new("BillboardGui", raid)
            billboard.Size = UDim2.new(2, 0, 2, 0)
            billboard.StudsOffset = Vector3.new(0, 3, 0)
            billboard.AlwaysOnTop = true

            local textLabel = Instance.new("TextLabel", billboard)
            textLabel.Size = UDim2.new(1, 0, 1, 0)
            textLabel.BackgroundTransparency = 1
            textLabel.Text = "Raid: " .. raid.Name
            textLabel.TextColor3 = Color3.new(1, 0, 0) -- Cor Vermelho
            textLabel.TextScaled = true
        end
    end
    
    -- Coletar frutas automaticamente
    if _G.CollectFruits then
        for i, fruit in pairs(game.Workspace.Fruits:GetChildren()) do
            if fruit:IsA("BasePart") then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = fruit.CFrame
                wait(1) -- Espera 1 segundo antes de verificar a próxima fruta
            end
        end
    end
    
    -- Coletar dinheiro automaticamente
    if _G.CollectMoney then
        for i, money in pairs(game.Workspace.Money:GetChildren()) do
            if money:IsA("BasePart") then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = money.CFrame
                wait(1) -- Espera 1 segundo antes de verificar o próximo dinheiro
            end
        end
    end

    wait(10) -- Espera 10 segundos antes de verificar novamente
end

print("Hub Moon Script ESP Raids com opção de seleção iniciado.")
