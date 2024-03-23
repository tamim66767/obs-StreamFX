local default = loadstring(game:HttpGet("https://gist.githubusercontent.com/raw/6f3d37a9f5068a0fc2203ac77077ce06/", true))()
local old = loadstring(game:HttpGet("https://pastebin.com/raw/kTSEH2sZ", true))()
local long = loadstring(game:HttpGet("https://gist.githubusercontent.com/raw/71101a9a7e1513e9b603339f6530b615/", true))()
local autoenter = true
local autodelay = 0.1
local delay = 0.1
local autotype = false
local Library = loadstring(game:HttpGet("https://gist.github.com/DeveloperMikey/a63d9da80c571a64a4b4ecc04a73b82a/raw/Twinklibfork.lua"))()
local Main = Library.Load("word bomb fucker v1.4")
local Screen = Main.GetUI()
local Home = Main.AddPage("home", false)
local Config = Main.AddPage("config", false)
local typing = false
local used = {}
local utf8 = {
	["A"] = 0x41,
	["B"] = 0x42,
	["C"] = 0x43,
	["D"] = 0x44,
	["E"] = 0x45,
	["F"] = 0x46,
	["G"] = 0x47,
	["H"] = 0x48,
	["I"] = 0x49,
	["J"] = 0x4A,
	["K"] = 0x4B,
	["L"] = 0x4C,
	["M"] = 0x4D,
	["N"] = 0x4E,
	["O"] = 0x4F,
	["P"] = 0x50,
	["Q"] = 0x51,
	["R"] = 0x52,
	["S"] = 0x53,
	["T"] = 0x54,
	["U"] = 0x55,
	["V"] = 0x56,
	["W"] = 0x57,
	["X"] = 0x58,
	["Y"] = 0x59,
	["Z"] = 0x5A,
}


local ENGLISH_WORDS = loadstring(game:HttpGet("https://gist.githubusercontent.com/raw/6f3d37a9f5068a0fc2203ac77077ce06/", true))()
local ContextActionService = game:GetService("ContextActionService")
local function checker(val)
    for i,v in pairs(used) do
        if v == val then return true end
    end
    return false
end
local function getWord()
    local word = ""
    for i,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.GameUI.Container.GameSpace.DefaultUI.GameContainer.DesktopContainer.InfoFrameContainer.InfoFrame.TextFrame:GetChildren()) do
        if v.Name == "LetterFrame" then
            word = word .. v.Letter.TextLabel.Text
        end
    end
    return word
end
local function findword(letters)
    local word
    local lenght = math.huge
    for i,v in pairs(ENGLISH_WORDS) do
        if string.find(v, string.lower(letters)) and not checker(string.upper(v)) then
            word = string.upper(v)
            lenght = string.len(v)
        end
    end
    return word
end
local function answer()
    if typing == false then
        typing = true
        local letters = getWord()
        if letters then
            local word = findword(letters)
            if word then
                for c in string.gmatch(findword(letters), ".") do
                    keypress(utf8[c])
                    wait(delay)
                end
                table.insert(used, word)
                if autoenter then
                    wait(delay)
                    keypress(0x0D)
                end
                typing = false
            end
        end
    end
end

--ui lib
local AnswerButton = Home.AddButton("type answer", function()
    answer()
 end)

local AutoTypeToggle = Home.AddToggle("automatically type", false, function(s)
    autotype = s
end)
local ClearButton = Home.AddButton("clear used words", function()
	used = {}
end)

local DelaySlider = Home.AddSlider("delay (ms)", {Min = 0, Max = 1000, Def = 100}, function(s)
    delay = s/1000
end)

local AutoSlider = Home.AddSlider("autotype delay (ms)", {Min = 0, Max = 1000, Def = 100}, function(s)
    autodelay = s/1000
end)

local WordsDropdown = Config.AddDropdown("word list", {'default', 'old', 'long'}, function(list)
    if list == 'default' then
        ENGLISH_WORDS = loadstring(game:HttpGet("https://gist.githubusercontent.com/raw/6f3d37a9f5068a0fc2203ac77077ce06/", true))()
    elseif list == 'old' then
        ENGLISH_WORDS = loadstring(game:HttpGet("https://pastebin.com/raw/kTSEH2sZ", true))()
    elseif list == 'long' then
        ENGLISH_WORDS = loadstring(game:HttpGet("https://gist.githubusercontent.com/raw/71101a9a7e1513e9b603339f6530b615/", true))()
    end
end)


local AutosubToggle = Config.AddToggle("automatically submit", true, function(s)
    autoenter = s
end)

local DestroyButton = Config.AddButton("destroy ui", function()
    Screen:Destroy()
    autotype = false
    autoenter = false
end)

local DiscordButton = Config.AddButton("copy discord invite", function()
	setclipboard("https://discord.gg/8mxdVNnf5W")
end)

local Credit1 = Config.AddLabel("made by jss and mikeymikey")
local CreditUi = Config.AddLabel("ui lib - modified twinklib")
local Credit2 = Config.AddLabel("v3rmillion.net")

if game:GetService("Players").LocalPlayer.PlayerGui.GameUI.Container.GameSpace.DefaultUI:FindFirstChild("GameContainer") and game:GetService("Players").LocalPlayer.PlayerGui.GameUI.Container.GameSpace.DefaultUI.GameContainer.DesktopContainer.Typebar.Typebox then
    game:GetService("Players").LocalPlayer.PlayerGui.GameUI.Container.GameSpace.DefaultUI.GameContainer.DesktopContainer.Typebar.Typebox:GetPropertyChangedSignal("Visible"):Connect(function()
        repeat
            wait(0.1)
            if game:GetService("Players").LocalPlayer.PlayerGui.GameUI.Container.GameSpace.DefaultUI.GameContainer.DesktopContainer.Typebar.Typebox.Visible == true and autotype == true then local a = answer() end
            wait(1)
        until game:GetService("Players").LocalPlayer.PlayerGui.GameUI.Container.GameSpace.DefaultUI.GameContainer.DesktopContainer.Typebar.Typebox.Visible == false
    end)
end
game:GetService("Players").LocalPlayer.PlayerGui.GameUI.DescendantAdded:Connect(function(yes)
    if yes.Name == "Typebox" then
        game:GetService("Players").LocalPlayer.PlayerGui.GameUI.Container.GameSpace.DefaultUI.GameContainer.DesktopContainer.Typebar.Typebox:GetPropertyChangedSignal("Visible"):Connect(function()
            wait(autodelay)
            if game:GetService("Players").LocalPlayer.PlayerGui.GameUI.Container.GameSpace.DefaultUI.GameContainer.DesktopContainer.Typebar.Typebox.Visible == true and autotype == true then
                repeat
                answer()
                wait(1)
                until game:GetService("Players").LocalPlayer.PlayerGui.GameUI.Container.GameSpace.DefaultUI.GameContainer.DesktopContainer.Typebar.Typebox.Visible == false
            end
        end)
    end
end)
