-- Astra Scripts Hub
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local CoreGui = game:GetService("CoreGui")

-- Colors Theme
local COLORS = {
    BACKGROUND = Color3.fromRGB(18, 18, 23),
    SECONDARY_BG = Color3.fromRGB(28, 28, 35),
    CARD_BG = Color3.fromRGB(35, 35, 45),
    ACCENT = Color3.fromRGB(110, 130, 170),
    TEXT_PRIMARY = Color3.fromRGB(230, 230, 230),
    TEXT_SECONDARY = Color3.fromRGB(180, 180, 190),
    SILVER = Color3.fromRGB(190, 195, 210),
    SILVER_DARK = Color3.fromRGB(90, 95, 110),
    DANGER = Color3.fromRGB(225, 65, 65),
    SUCCESS = Color3.fromRGB(80, 200, 120)
}

-- Utility Functions
local function createShadow(parent, size, position, transparency)
    local shadow = Instance.new("ImageLabel")
    shadow.Name = "Shadow"
    shadow.BackgroundTransparency = 1
    shadow.Image = "rbxassetid://1316045217"
    shadow.ImageColor3 = Color3.fromRGB(0, 0, 0)
    shadow.ImageTransparency = transparency or 0.6
    shadow.ScaleType = Enum.ScaleType.Slice
    shadow.SliceCenter = Rect.new(10, 10, 118, 118)
    shadow.Size = size or UDim2.new(1, 10, 1, 10)
    shadow.Position = position or UDim2.new(0, -5, 0, -5)
    shadow.ZIndex = 0
    shadow.Parent = parent
    return shadow
end

local function createGradient(parent, color1, color2, rotation)
    local gradient = Instance.new("UIGradient")
    gradient.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0, color1 or COLORS.BACKGROUND),
        ColorSequenceKeypoint.new(1, color2 or COLORS.SECONDARY_BG)
    })
    gradient.Rotation = rotation or 45
    gradient.Parent = parent
    return gradient
end

-- Create the UI
local player = Players.LocalPlayer
local gui = Instance.new("ScreenGui")
gui.Name = "AstraHub"
gui.DisplayOrder = 999
gui.ResetOnSpawn = false
gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

-- Try to parent to CoreGui for better persistence
pcall(function()
    if syn and syn.protect_gui then
        syn.protect_gui(gui)
        gui.Parent = CoreGui
    else
        gui.Parent = game:GetService("CoreGui")
    end
end)
if not gui.Parent then
    gui.Parent = player:WaitForChild("PlayerGui")
end

-- Main Container for Loader
local function createLoader()
    local loaderContainer = Instance.new("Frame")
    loaderContainer.Name = "LoaderContainer"
    loaderContainer.Size = UDim2.new(0, 320, 0, 220)
    loaderContainer.Position = UDim2.new(0.5, -160, 0.5, -110)
    loaderContainer.BackgroundColor3 = COLORS.BACKGROUND
    loaderContainer.BorderSizePixel = 0
    loaderContainer.Parent = gui
    
    -- Create shadow effect
    createShadow(loaderContainer)
    
    -- Create subtle gradient
    createGradient(loaderContainer, COLORS.BACKGROUND, COLORS.SECONDARY_BG)
    
    -- Corner Radius for Modern Look
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 12)
    corner.Parent = loaderContainer
    
    -- Accent Border Glow
    local borderGlow = Instance.new("Frame")
    borderGlow.Name = "BorderGlow"
    borderGlow.Size = UDim2.new(1, 0, 0, 2)
    borderGlow.Position = UDim2.new(0, 0, 0, 0)
    borderGlow.BackgroundColor3 = COLORS.ACCENT
    borderGlow.BorderSizePixel = 0
    borderGlow.Parent = loaderContainer
    
    local borderCorner = Instance.new("UICorner")
    borderCorner.CornerRadius = UDim.new(0, 12)
    borderCorner.Parent = borderGlow
    
    -- Logo Container with Glow Effect
    local logoContainer = Instance.new("Frame")
    logoContainer.Name = "LogoContainer"
    logoContainer.Size = UDim2.new(0, 90, 0, 90)
    logoContainer.Position = UDim2.new(0.5, -45, 0.25, -35)
    logoContainer.BackgroundTransparency = 1
    logoContainer.Parent = loaderContainer
    
    local logoGlow = Instance.new("ImageLabel")
    logoGlow.Name = "LogoGlow"
    logoGlow.Size = UDim2.new(1.3, 0, 1.3, 0)
    logoGlow.Position = UDim2.new(-0.15, 0, -0.15, 0)
    logoGlow.BackgroundTransparency = 1
    logoGlow.Image = "rbxassetid://1316045217"
    logoGlow.ImageColor3 = COLORS.ACCENT
    logoGlow.ImageTransparency = 1
    logoGlow.Parent = logoContainer
    
    -- Logo
    local logo = Instance.new("ImageLabel")
    logo.Name = "Logo"
    logo.Size = UDim2.new(1, 0, 1, 0)
    logo.BackgroundTransparency = 1
    logo.Image = "rbxassetid://94597292360065" -- Replace with your logo asset ID
    logo.Parent = logoContainer
    
    -- Title
    local title = Instance.new("TextLabel")
    title.Name = "Title"
    title.Size = UDim2.new(0, 250, 0, 30)
    title.Position = UDim2.new(0.5, -125, 0.5, 0)
    title.BackgroundTransparency = 1
    title.Text = "ASTRA SCRIPTS"
    title.TextColor3 = COLORS.SILVER
    title.TextSize = 22
    title.Font = Enum.Font.GothamBold
    title.Parent = loaderContainer
    
    -- Subtitle
    local subtitle = Instance.new("TextLabel")
    subtitle.Name = "Subtitle"
    subtitle.Size = UDim2.new(0, 200, 0, 20)
    subtitle.Position = UDim2.new(0.5, -100, 0.5, 28)
    subtitle.BackgroundTransparency = 1
    subtitle.Text = "FREEMIUM SCRIPTS"
    subtitle.TextColor3 = COLORS.TEXT_SECONDARY
    subtitle.TextSize = 14
    subtitle.Font = Enum.Font.Gotham
    subtitle.Parent = loaderContainer
    
    -- Progress Bar Container with Gloss Effect
    local progressContainer = Instance.new("Frame")
    progressContainer.Name = "ProgressContainer"
    progressContainer.Size = UDim2.new(0, 270, 0, 8)
    progressContainer.Position = UDim2.new(0.5, -135, 0.73, 0)
    progressContainer.BackgroundColor3 = COLORS.SECONDARY_BG
    progressContainer.BorderSizePixel = 0
    progressContainer.Parent = loaderContainer
    
    local progressContainerCorner = Instance.new("UICorner")
    progressContainerCorner.CornerRadius = UDim.new(0, 4)
    progressContainerCorner.Parent = progressContainer
    
    -- Progress Bar with Gradient
    local progressBar = Instance.new("Frame")
    progressBar.Name = "ProgressBar"
    progressBar.Size = UDim2.new(0, 0, 1, 0)
    progressBar.BackgroundColor3 = COLORS.ACCENT
    progressBar.BorderSizePixel = 0
    progressBar.Parent = progressContainer
    
    local progressBarCorner = Instance.new("UICorner")
    progressBarCorner.CornerRadius = UDim.new(0, 4)
    progressBarCorner.Parent = progressBar
    
    createGradient(progressBar, COLORS.ACCENT, Color3.fromRGB(COLORS.ACCENT.R*1.2, COLORS.ACCENT.G*1.2, COLORS.ACCENT.B*1.2), 90)
    
    -- Loading Text with Percentage
    local loadingText = Instance.new("TextLabel")
    loadingText.Name = "LoadingText"
    loadingText.Size = UDim2.new(0, 200, 0, 20)
    loadingText.Position = UDim2.new(0.5, -100, 0.73, 15)
    loadingText.BackgroundTransparency = 1
    loadingText.Text = "INITIALIZING..."
    loadingText.TextColor3 = COLORS.TEXT_SECONDARY
    loadingText.TextSize = 14
    loadingText.Font = Enum.Font.Gotham
    loadingText.Parent = loaderContainer
    
    -- Version Text
    local versionText = Instance.new("TextLabel")
    versionText.Name = "VersionText"
    versionText.Size = UDim2.new(0, 100, 0, 20)
    versionText.Position = UDim2.new(0.5, -50, 0.9, 0)
    versionText.BackgroundTransparency = 1
    versionText.Text = "v2.5.0"
    versionText.TextColor3 = COLORS.SILVER_DARK
    versionText.TextSize = 14
    versionText.Font = Enum.Font.GothamSemibold
    versionText.Parent = loaderContainer
    
    -- Animation for Progress Bar
    local function animateProgressBar()
        local stages = {
            {progress = 0.2, text = "CHECKING ENVIRONMENT...", delay = 0.5},
            {progress = 0.4, text = "LOADING LIBRARIES...", delay = 0.7},
            {progress = 0.6, text = "INITIALIZING SCRIPTS...", delay = 0.6},
            {progress = 0.8, text = "ESTABLISHING CONNECTION...", delay = 0.8},
            {progress = 1.0, text = "READY!", delay = 0.4}
        }
        
        for _, stage in ipairs(stages) do
            local tweenInfo = TweenInfo.new(stage.delay, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
            local tween = TweenService:Create(progressBar, tweenInfo, {Size = UDim2.new(stage.progress, 0, 1, 0)})
            loadingText.Text = stage.text
            tween:Play()
            tween.Completed:Wait()
        end
        
        -- Add a brief pause at the end
        wait(0.5)
        
        -- Fade out the loader
        local tweenInfo = TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
        local fadeTween = TweenService:Create(loaderContainer, tweenInfo, {BackgroundTransparency = 1})
        fadeTween:Play()
        
        -- Fade out all children
        for _, child in pairs(loaderContainer:GetDescendants()) do
            if child:IsA("Frame") or child:IsA("TextLabel") or child:IsA("ImageLabel") then
                TweenService:Create(child, tweenInfo, {BackgroundTransparency = 1}):Play()
                if child:IsA("TextLabel") or child:IsA("ImageLabel") then
                end
            end
        end
        
        wait(0.5)
        loaderContainer:Destroy()
    end
    
    return animateProgressBar
end

-- Create Main Hub Interface
local function createHub()
    -- Hub Container
    local hubContainer = Instance.new("Frame")
    hubContainer.Name = "HubContainer"
    hubContainer.Size = UDim2.new(0, 600, 0, 400)
    hubContainer.Position = UDim2.new(0.5, -300, 0.5, -200)
    hubContainer.BackgroundColor3 = COLORS.BACKGROUND
    hubContainer.BorderSizePixel = 0
    hubContainer.Parent = gui
    
    -- Make draggable
    local isDragging = false
    local dragInput
    local dragStart
    local startPos
    
    local function updateDrag(input)
        local delta = input.Position - dragStart
        hubContainer.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
    
    hubContainer.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            isDragging = true
            dragStart = input.Position
            startPos = hubContainer.Position
            
            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    isDragging = false
                end
            end)
        end
    end)
    
    hubContainer.InputChanged:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement then
            dragInput = input
        end
    end)
    
    UserInputService.InputChanged:Connect(function(input)
        if input == dragInput and isDragging then
            updateDrag(input)
        end
    end)
    
    -- Create shadow effect
    createShadow(hubContainer)
    
    -- Create gradient
    createGradient(hubContainer, COLORS.BACKGROUND, COLORS.SECONDARY_BG)
    
    -- Corner Radius
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 12)
    corner.Parent = hubContainer
    
    -- Top Bar
    local topBar = Instance.new("Frame")
    topBar.Name = "TopBar"
    topBar.Size = UDim2.new(1, 0, 0, 40)
    topBar.BackgroundColor3 = COLORS.SECONDARY_BG
    topBar.BackgroundTransparency = 0.6
    topBar.BorderSizePixel = 0
    topBar.Parent = hubContainer
    
    local topBarCorner = Instance.new("UICorner")
    topBarCorner.CornerRadius = UDim.new(0, 12)
    topBarCorner.Parent = topBar
    
    -- Top Bar Bottom Cover (to remove rounded corners at the bottom)
    local topBarCover = Instance.new("Frame")
    topBarCover.Name = "TopBarCover"
    topBarCover.Size = UDim2.new(1, 0, 0, 15)
    topBarCover.Position = UDim2.new(0, 0, 1, -10)
    topBarCover.BackgroundColor3 = COLORS.SECONDARY_BG
    topBarCover.BackgroundTransparency = 0.6
    topBarCover.BorderSizePixel = 0
    topBarCover.ZIndex = topBar.ZIndex
    topBarCover.Parent = topBar
    
    -- Create Accent Line
    local accentLine = Instance.new("Frame")
    accentLine.Name = "AccentLine"
    accentLine.Size = UDim2.new(1, 0, 0, 1)
    accentLine.Position = UDim2.new(0, 0, 1, 0)
    accentLine.BackgroundColor3 = COLORS.ACCENT
    accentLine.BorderSizePixel = 0
    accentLine.ZIndex = topBar.ZIndex + 1
    accentLine.Parent = topBar
    
    -- Logo on Top Left
    local logo = Instance.new("ImageLabel")
    logo.Name = "Logo"
    logo.Size = UDim2.new(0, 25, 0, 25)
    logo.Position = UDim2.new(0, 15, 0, 8)
    logo.BackgroundTransparency = 1
    logo.Image = "rbxassetid://94597292360065" -- Replace with your logo asset ID
    logo.ZIndex = topBar.ZIndex + 1
    logo.Parent = topBar
    
    -- Title on Top
    local title = Instance.new("TextLabel")
    title.Name = "Title"
    title.Size = UDim2.new(0, 200, 0, 30)
    title.Position = UDim2.new(0, 50, 0, 5)
    title.BackgroundTransparency = 1
    title.Text = "ASTRA SCRIPTS"
    title.TextColor3 = COLORS.SILVER
    title.TextSize = 18
    title.Font = Enum.Font.GothamBold
    title.TextXAlignment = Enum.TextXAlignment.Left
    title.ZIndex = topBar.ZIndex + 1
    title.Parent = topBar
    
    -- Close Button
    local closeButton = Instance.new("TextButton")
    closeButton.Name = "CloseButton"
    closeButton.Size = UDim2.new(0, 30, 0, 30)
    closeButton.Position = UDim2.new(1, -40, 0, 5)
    closeButton.BackgroundColor3 = COLORS.DANGER
    closeButton.BackgroundTransparency = 0.8
    closeButton.Text = "✕"
    closeButton.TextColor3 = COLORS.TEXT_PRIMARY
    closeButton.TextSize = 16
    closeButton.Font = Enum.Font.GothamBold
    closeButton.ZIndex = topBar.ZIndex + 1
    closeButton.Parent = topBar
    
    local closeCorner = Instance.new("UICorner")
    closeCorner.CornerRadius = UDim.new(0, 6)
    closeCorner.Parent = closeButton
    
    -- Minimize Button
    local minimizeButton = Instance.new("TextButton")
    minimizeButton.Name = "MinimizeButton"
    minimizeButton.Size = UDim2.new(0, 30, 0, 30)
    minimizeButton.Position = UDim2.new(1, -80, 0, 5)
    minimizeButton.BackgroundColor3 = COLORS.SILVER_DARK
    minimizeButton.BackgroundTransparency = 0.8
    minimizeButton.Text = "−"
    minimizeButton.TextColor3 = COLORS.TEXT_PRIMARY
    minimizeButton.TextSize = 16
    minimizeButton.Font = Enum.Font.GothamBold
    minimizeButton.ZIndex = topBar.ZIndex + 1
    minimizeButton.Parent = topBar
    
    local minimizeCorner = Instance.new("UICorner")
    minimizeCorner.CornerRadius = UDim.new(0, 6)
    minimizeCorner.Parent = minimizeButton
    
    -- Side Navigation
    local sideNav = Instance.new("Frame")
    sideNav.Name = "SideNav"
    sideNav.Size = UDim2.new(0, 160, 1, -40)
    sideNav.Position = UDim2.new(0, 0, 0, 40)
    sideNav.BackgroundColor3 = COLORS.SECONDARY_BG
    sideNav.BackgroundTransparency = 0.8
    sideNav.BorderSizePixel = 0
    sideNav.Parent = hubContainer
    
    -- Content Container
    local contentContainer = Instance.new("Frame")
    contentContainer.Name = "ContentContainer"
    contentContainer.Size = UDim2.new(1, -170, 1, -50)
    contentContainer.Position = UDim2.new(0, 170, 0, 50)
    contentContainer.BackgroundTransparency = 1
    contentContainer.BorderSizePixel = 0
    contentContainer.Parent = hubContainer
    
    -- Create Navigation Items
    local navItems = {
        {name = "Scripts", icon = "rbxassetid://3926305904", iconOffset = Vector2.new(164, 84), iconSize = Vector2.new(36, 36)},
        {name = "Info", icon = "rbxassetid://3926305904", iconOffset = Vector2.new(404, 364), iconSize = Vector2.new(36, 36)},
        {name = "Settings", icon = "rbxassetid://3926307971", iconOffset = Vector2.new(164, 164), iconSize = Vector2.new(36, 36)},
        {name = "Credits", icon = "rbxassetid://3926305904", iconOffset = Vector2.new(924, 164), iconSize = Vector2.new(36, 36)}
    }
    
    local navButtons = {}
    local selectedNav = nil
    
    for i, item in ipairs(navItems) do
        local navItem = Instance.new("TextButton")
        navItem.Name = item.name.."Nav"
        navItem.Size = UDim2.new(1, -20, 0, 36)
        navItem.Position = UDim2.new(0, 10, 0, 20 + (i-1) * 50)
        navItem.BackgroundColor3 = COLORS.ACCENT
        navItem.BackgroundTransparency = 0.9
        navItem.Text = ""
        navItem.AutoButtonColor = false
        navItem.Parent = sideNav
        
        local navCorner = Instance.new("UICorner")
        navCorner.CornerRadius = UDim.new(0, 8)
        navCorner.Parent = navItem
        
        local iconContainer = Instance.new("Frame")
        iconContainer.Name = "IconContainer"
        iconContainer.Size = UDim2.new(0, 24, 0, 24)
        iconContainer.Position = UDim2.new(0, 8, 0.5, -12)
        iconContainer.BackgroundTransparency = 1
        iconContainer.Parent = navItem
        
        local icon = Instance.new("ImageLabel")
        icon.Name = "Icon"
        icon.Size = UDim2.new(0, 20, 0, 20)
        icon.Position = UDim2.new(0.5, -10, 0.5, -10)
        icon.BackgroundTransparency = 1
        icon.Image = item.icon
        icon.ImageRectOffset = item.iconOffset
        icon.ImageRectSize = item.iconSize
        icon.ImageColor3 = COLORS.SILVER
        icon.Parent = iconContainer
        
        local label = Instance.new("TextLabel")
        label.Name = "Label"
        label.Size = UDim2.new(1, -40, 1, 0)
        label.Position = UDim2.new(0, 40, 0, 0)
        label.BackgroundTransparency = 1
        label.Text = item.name
        label.TextColor3 = COLORS.SILVER
        label.TextSize = 16
        label.Font = Enum.Font.GothamSemibold
        label.TextXAlignment = Enum.TextXAlignment.Left
        label.Parent = navItem
        
        navButtons[item.name] = navItem
    end
    
    -- Footer in Side Nav
    local footer = Instance.new("TextLabel")
    footer.Name = "Footer"
    footer.Size = UDim2.new(1, -20, 0, 20)
    footer.Position = UDim2.new(0, 10, 1, -30)
    footer.BackgroundTransparency = 1
    footer.Text = "v2.5.0 • 2025"
    footer.TextColor3 = COLORS.SILVER_DARK
    footer.TextSize = 14
    footer.Font = Enum.Font.Gotham
    footer.Parent = sideNav
    
    -- Create Content Frames
    local contentFrames = {}
    
    -- Scripts Content
    local scriptsFrame = Instance.new("ScrollingFrame")
    scriptsFrame.Name = "ScriptsFrame"
    scriptsFrame.Size = UDim2.new(1, 0, 1, 0)
    scriptsFrame.BackgroundTransparency = 1
    scriptsFrame.BorderSizePixel = 0
    scriptsFrame.ScrollBarThickness = 4
    scriptsFrame.ScrollBarImageColor3 = COLORS.SILVER_DARK
    scriptsFrame.VerticalScrollBarPosition = Enum.VerticalScrollBarPosition.Right
    scriptsFrame.Visible = false
    scriptsFrame.Parent = contentContainer
    
    local scriptsList = Instance.new("UIListLayout")
    scriptsList.Name = "ScriptsList"
    scriptsList.Padding = UDim.new(0, 10)
    scriptsList.HorizontalAlignment = Enum.HorizontalAlignment.Center
    scriptsList.SortOrder = Enum.SortOrder.LayoutOrder
    scriptsList.Parent = scriptsFrame
    
    local scriptsHeader = Instance.new("TextLabel")
    scriptsHeader.Name = "Header"
    scriptsHeader.Size = UDim2.new(1, -20, 0, 40)
    scriptsHeader.BackgroundTransparency = 1
    scriptsHeader.Text = "Available Scripts"
    scriptsHeader.TextColor3 = COLORS.TEXT_PRIMARY
    scriptsHeader.TextSize = 22
    scriptsHeader.Font = Enum.Font.GothamBold
    scriptsHeader.TextXAlignment = Enum.TextXAlignment.Left
    scriptsHeader.Parent = scriptsFrame
    
    -- Info Content (Replaced Hub)
    local infoFrame = Instance.new("ScrollingFrame")
    infoFrame.Name = "InfoFrame"
    infoFrame.Size = UDim2.new(1, 0, 1, 0)
    infoFrame.BackgroundTransparency = 1
    infoFrame.BorderSizePixel = 0
    infoFrame.ScrollBarThickness = 4
    infoFrame.ScrollBarImageColor3 = COLORS.SILVER_DARK
    infoFrame.VerticalScrollBarPosition = Enum.VerticalScrollBarPosition.Right
    infoFrame.Visible = false
    infoFrame.Parent = contentContainer
    
    local infoList = Instance.new("UIListLayout")
    infoList.Name = "InfoList"
    infoList.Padding = UDim.new(0, 10)
    infoList.HorizontalAlignment = Enum.HorizontalAlignment.Center
    infoList.SortOrder = Enum.SortOrder.LayoutOrder
    infoList.Parent = infoFrame
    
    local infoHeader = Instance.new("TextLabel")
    infoHeader.Name = "Header"
    infoHeader.Size = UDim2.new(1, -20, 0, 40)
    infoHeader.BackgroundTransparency = 1
    infoHeader.Text = "Info"
    infoHeader.TextColor3 = COLORS.TEXT_PRIMARY
    infoHeader.TextSize = 22
    infoHeader.Font = Enum.Font.GothamBold
    infoHeader.TextXAlignment = Enum.TextXAlignment.Left
    infoHeader.Parent = infoFrame
    
    -- Settings Content
    local settingsFrame = Instance.new("Frame")
    settingsFrame.Name = "SettingsFrame"
    settingsFrame.Size = UDim2.new(1, 0, 1, 0)
    settingsFrame.BackgroundTransparency = 1
    settingsFrame.BorderSizePixel = 0
    settingsFrame.Visible = false
    settingsFrame.Parent = contentContainer
    
    local settingsHeader = Instance.new("TextLabel")
    settingsHeader.Name = "Header"
    settingsHeader.Size = UDim2.new(1, -20, 0, 40)
    settingsHeader.BackgroundTransparency = 1
    settingsHeader.Text = "Settings"
    settingsHeader.TextColor3 = COLORS.TEXT_PRIMARY
    settingsHeader.TextSize = 22
    settingsHeader.Font = Enum.Font.GothamBold
    settingsHeader.TextXAlignment = Enum.TextXAlignment.Left
    settingsHeader.Parent = settingsFrame
    
    -- Credits Content
    local creditsFrame = Instance.new("Frame")
    creditsFrame.Name = "CreditsFrame"
    creditsFrame.Size = UDim2.new(1, 0, 1, 0)
    creditsFrame.BackgroundTransparency = 1
    creditsFrame.BorderSizePixel = 0
    creditsFrame.Visible = false
    creditsFrame.Parent = contentContainer
    
    local creditsHeader = Instance.new("TextLabel")
    creditsHeader.Name = "Header"
    creditsHeader.Size = UDim2.new(1, -20, 0, 40)
    creditsHeader.BackgroundTransparency = 1
    creditsHeader.Text = "Credits"
    creditsHeader.TextColor3 = COLORS.TEXT_PRIMARY
    creditsHeader.TextSize = 22
    creditsHeader.Font = Enum.Font.GothamBold
    creditsHeader.TextXAlignment = Enum.TextXAlignment.Left
    creditsHeader.Parent = creditsFrame
    
    -- Add Content Frames to Table
    contentFrames = {
        Scripts = scriptsFrame,
        Info = infoFrame,
        Settings = settingsFrame,
        Credits = creditsFrame
    }
    
    -- Navigation Logic
    local function switchContent(selected)
        if selectedNav then
            -- Deselect current navigation button
            TweenService:Create(selectedNav, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {
                BackgroundTransparency = 0.9
            }):Play()
            TweenService:Create(selectedNav:FindFirstChild("IconContainer").Icon, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {
                ImageColor3 = COLORS.SILVER
            }):Play()
            TweenService:Create(selectedNav:FindFirstChild("Label"), TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {
                TextColor3 = COLORS.SILVER
            }):Play()
        end
        
        -- Select new navigation button
        selectedNav = navButtons[selected]
        TweenService:Create(selectedNav, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {
            BackgroundTransparency = 0.8
        }):Play()
        TweenService:Create(selectedNav:FindFirstChild("IconContainer").Icon, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {
            ImageColor3 = COLORS.ACCENT
        }):Play()
        TweenService:Create(selectedNav:FindFirstChild("Label"), TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {
            TextColor3 = COLORS.ACCENT
        }):Play()
        
        -- Hide all content frames
        for _, frame in pairs(contentFrames) do
            frame.Visible = false
        end
        
        -- Show selected content frame
        contentFrames[selected].Visible = true
    end
    
    -- Connect Navigation Buttons
    for name, button in pairs(navButtons) do
        button.MouseButton1Click:Connect(function()
            switchContent(name)
        end)
    end
    
    -- Default to Scripts Tab
    switchContent("Scripts")
    
    -- Close Button Functionality
    closeButton.MouseButton1Click:Connect(function()
        gui:Destroy()
    end)
    
    -- Minimize Button Functionality
local minimizedButton = Instance.new("TextButton")
minimizedButton.Name = "MinimizedButton"
minimizedButton.Size = UDim2.new(0, 40, 0, 40)
minimizedButton.Position = UDim2.new(0, 10, 0.5, -20) -- Center-left position
minimizedButton.BackgroundColor3 = COLORS.ACCENT
minimizedButton.BackgroundTransparency = 0.8
minimizedButton.Text = ""
minimizedButton.Visible = false
minimizedButton.Parent = gui

local minimizedCorner = Instance.new("UICorner")
minimizedCorner.CornerRadius = UDim.new(0, 8)
minimizedCorner.Parent = minimizedButton

local minimizedLogo = Instance.new("ImageLabel")
minimizedLogo.Name = "MinimizedLogo"
minimizedLogo.Size = UDim2.new(0, 25, 0, 25)
minimizedLogo.Position = UDim2.new(0.5, -12.5, 0.5, -12.5)
minimizedLogo.BackgroundTransparency = 1
minimizedLogo.Image = "rbxassetid://94597292360065" -- Replace with your logo asset ID
minimizedLogo.Parent = minimizedButton
    
    minimizeButton.MouseButton1Click:Connect(function()
        hubContainer.Visible = false
        minimizedButton.Visible = true
    end)
    
    minimizedButton.MouseButton1Click:Connect(function()
        hubContainer.Visible = true
        minimizedButton.Visible = false
    end)
    
    -- Add Example Scripts
local function createScriptCard(name, description, iconId, scriptUrl)
    local card = Instance.new("Frame")
    card.Name = "ScriptCard"
    card.Size = UDim2.new(1, -20, 0, 80)
    card.BackgroundColor3 = COLORS.CARD_BG
    card.BackgroundTransparency = 0.8
    card.BorderSizePixel = 0
    card.Parent = scriptsFrame
    
    local cardCorner = Instance.new("UICorner")
    cardCorner.CornerRadius = UDim.new(0, 8)
    cardCorner.Parent = card
    
    -- Icon for TPS Street Soccer
    local icon = Instance.new("ImageLabel")
    icon.Name = "Icon"
    icon.Size = UDim2.new(0, 50, 0, 50)
    icon.Position = UDim2.new(0, 10, 0.5, -25)
    icon.BackgroundTransparency = 1
    icon.Image = iconId -- Use the provided rbxthumb link
    icon.Parent = card
    
    -- Title for TPS Street Soccer
    local title = Instance.new("TextLabel")
    title.Name = "Title"
    title.Size = UDim2.new(0, 200, 0, 30)
    title.Position = UDim2.new(0, 70, 0.2, 0)
    title.BackgroundTransparency = 1
    title.Text = name
    title.TextColor3 = COLORS.TEXT_PRIMARY
    title.TextSize = 18
    title.Font = Enum.Font.GothamBold
    title.TextXAlignment = Enum.TextXAlignment.Left
    title.Parent = card
    
    -- Description for TPS Street Soccer
    local desc = Instance.new("TextLabel")
    desc.Name = "Description"
    desc.Size = UDim2.new(0, 400, 0, 20)
    desc.Position = UDim2.new(0, 70, 0.6, 0)
    desc.BackgroundTransparency = 1
    desc.Text = description
    desc.TextColor3 = COLORS.TEXT_SECONDARY
    desc.TextSize = 14
    desc.Font = Enum.Font.Gotham
    desc.TextXAlignment = Enum.TextXAlignment.Left
    desc.Parent = card
    
    -- Execute Button
    local executeButton = Instance.new("TextButton")
    executeButton.Name = "ExecuteButton"
    executeButton.Size = UDim2.new(0, 80, 0, 30)
    executeButton.Position = UDim2.new(1, -90, 0.5, -15)
    executeButton.BackgroundColor3 = COLORS.ACCENT
    executeButton.BackgroundTransparency = 0.8
    executeButton.Text = "Execute"
    executeButton.TextColor3 = COLORS.TEXT_PRIMARY
    executeButton.TextSize = 14
    executeButton.Font = Enum.Font.GothamBold
    executeButton.Parent = card
    
    local buttonCorner = Instance.new("UICorner")
    buttonCorner.CornerRadius = UDim.new(0, 6)
    buttonCorner.Parent = executeButton
    
    -- Execute Script on Button Click
    executeButton.MouseButton1Click:Connect(function()
        loadstring(game:HttpGet(scriptUrl))()
    end)
    
    -- Add shadow to card
    createShadow(card)
end

-- Add TPS Street Soccer Script
createScriptCard(
    "TPS Street Soccer", 
    "Teleport to the soccer field and dominate the game!", 
    "rbxthumb://type=GameIcon&id=335760407&w=150&h=150", 
    "https://raw.githubusercontent.com/gustnixzxy/UI-Library/refs/heads/main/X"
)
end

-- Add TPS Street Soccer Script
createScriptCard("TPS Street Soccer", "Teleport to the soccer field and dominate the game!", "rbxthumb://type=GameIcon&id=335760407&w=150&h=150")
    
-- Add Info Content
local infoText = Instance.new("TextLabel")
infoText.Name = "InfoText"
infoText.Size = UDim2.new(1, -20, 0, 200)
infoText.Position = UDim2.new(0, 10, 0, 50)
infoText.BackgroundTransparency = 1
infoText.Text = "Astra was originally created by Asen and gustnixzxy.\n\nOur goal is to become the best modern exploit hub for Roblox, providing a seamless and user-friendly experience for all players.\n\nEnjoy the power of Astra Scripts!"
infoText.TextColor3 = COLORS.TEXT_PRIMARY
infoText.TextSize = 16
infoText.Font = Enum.Font.Gotham
infoText.TextXAlignment = Enum.TextXAlignment.Left
infoText.TextYAlignment = Enum.TextYAlignment.Top
infoText.TextWrapped = true -- Ensure text wraps to the next line
infoText.Parent = infoFrame
    
    -- Add Settings Content
    local settingsText = Instance.new("TextLabel")
    settingsText.Name = "SettingsText"
    settingsText.Size = UDim2.new(1, -20, 0, 200)
    settingsText.Position = UDim2.new(0, 10, 0, 50)
    settingsText.BackgroundTransparency = 1
    settingsText.Text = "Settings will be available soon!"
    settingsText.TextColor3 = COLORS.TEXT_PRIMARY
    settingsText.TextSize = 16
    settingsText.Font = Enum.Font.Gotham
    settingsText.TextXAlignment = Enum.TextXAlignment.Left
    settingsText.TextYAlignment = Enum.TextYAlignment.Top
    settingsText.Parent = settingsFrame
    
-- Add Credits Content
local creditsText = Instance.new("TextLabel")
creditsText.Name = "CreditsText"
creditsText.Size = UDim2.new(1, -20, 0, 200)
creditsText.Position = UDim2.new(0, 10, 0, 50)
creditsText.BackgroundTransparency = 1
creditsText.Text = "Credits:\n\n- Interface Creator: Asen\n- Helper: gustnixzxy\n\nSpecial Thanks To:\n- You!"
creditsText.TextColor3 = COLORS.TEXT_PRIMARY
creditsText.TextSize = 16
creditsText.Font = Enum.Font.Gotham
creditsText.TextXAlignment = Enum.TextXAlignment.Left
creditsText.TextYAlignment = Enum.TextYAlignment.Top
creditsText.TextWrapped = true -- Ensure text wraps to the next line
creditsText.Parent = creditsFrame
end

-- Start Loader Animation
local animateProgressBar = createLoader()
animateProgressBar()

-- Create Hub After Loader Completes
wait(2) -- Simulate loading time
createHub()
