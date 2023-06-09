# Unity Demo


## Feature Introduction

### 1 Chat Room Channels
- Includes 3 chat room channels (World, Guild, Party)
- Can send chat room messages in the chat room channels
- Can add friends or switch to friend chat page by clicking the icon in the upper right corner of the chat room message
 
### 2 Friends List
- Click on a friend to switch to the single chat page

### 3 Single Chat Page
- Can accept or reject friend requests
- Can exchange messages with friends

### 4 Support for Emoji
- Supports embedding emoji symbols when sending text messages

### 5 New Message Notification
- When a new message is received and does not belong to the current channel, a red circle with a number will be displayed to indicate a new message, with a maximum display of 99+


## Demo Execution Program Instructions
- Download the zip package and extract it
    [windows Version](https://downloadsdk.easemob.com/downloads/SDK/Demo/WinExe.zip)
    [mac Version](https://downloadsdk.easemob.com/downloads/SDK/Demo/MacApp.zip)

- Configuration File：sdk.txt
	-   The configuration file is located in Contents/Resources/Data/StreamingAssets under the Mac platform
	-   The configuration file is located in unity_demo_Data\StreamingAssets under the Windows platform
		
		The default configuration is as follows:	

		- AppKey=easemob-demo#unitytest
		- UseToken=false
		- UserName=unity_demo
		- Password=unity_demo
		- Token=xxx
		- World=205360469180417
		- Guild=205360500637703
		- Party=205360528949251
		
		By default, the login is done using the username and password, and UseToken can be changed to true to log in using Agora token. Token needs to be set when using the Agora token.
        World, Guild, and Party are three chat room channels under the corresponding Appkey. If the Appkey is changed, World, Guild, and Party must be set to the chat room IDs under that Appkey.
		
		If use default configuration, another UserName also can be used. It is unity_demo1, and the Password is unity_demo1 too.
		
- Running the Program

    On the Mac platform, run unity_demo
	On the Windows platform, run unityunity_demo.exe
	
- Log Viewing

    On the Mac platform, the Unity output log is located at Console/Player.log, and the sdk's own log is located at /Users/xxx/Library/Application Support/DefaultCompany/unity_demo/sdkdata/easemobLog (xxx is the username).

    On the Windows platform, the Unity output log is located at C:\Users\xxx\AppData\LocalLow\DefaultCompany\unity_demo (xxx is the username), and the sdk's own log is also located in the same directory in sdkdata\easemobLog.

## Secondary Development Instructions
### 1 Importing Packages
Import the following packages in Unity Editor by selecting Assets -> Import Package:
- unity_demo package: Contains all UI elements and scripts. [Download link](https://downloadsdk.easemob.com/downloads/SDK/Demo/unity_demo.unitypackage)
- AgoraChat Sdk package：AgoraChat Sdk, [Download link](https://docs.agora.io/en/sdks?platform=unity)

### 2 Package Contents
After importing the unity_demo and AgoraChat SDK packages, the Assets directory should contain the following:
- AgoraChat: Contains c# code and Chat plugins related to the Agora Chat SDK.
- Resources: Folder containing various resources. Note that the name of this folder should not be changed. It contains:
    - AppIcons: Icon resources
    - Avatars: User avatar resources
    - Cursors: Mouse cursor resources
    - Emojis: Emoji expression resources
    - Icons: Icon resources
    - Images: Image resources
    - Others: Other resources, such as window borders, etc.
    - Scences: Scene directory

- Scripts：Directory containing various scripts, including:
    - ActionButton.cs: Corresponds to canvas/BackGroundPanel/ActionButton and is used to display other function buttons
    - AddFriendButton.cs: Corresponds to canvas/AddFriendButton and is used to add friends
    - ApplyActionButton.cs: Corresponds to UIResources/ApplyActionButton (prefab) and is used to accept or ignore friend requests
    - ChatContainerPanel.cs: Corresponds to canvas/MainPanel/ChatContainerPanel and is used as a single-chat interface container to manage single-chat pages
    - ChatSwitchButton.cs: Corresponds to canvas/ChatSwitchButton and is used to switch to a single-chat page
    - Context.cs: Context script, which records whether the SDK initialization is successful and which page is currently displayed
    - DateSplitButton.cs: Corresponds to UIResources/DateSplitButton (prefab) and is used to add the date information for the current day
    - EmojiPanel.cs: Corresponds to canvas/EmojiPanel and is used to display and hide the EmojiPanel panel
    - ExitButton.cs: Corresponds to canvas/BackGroundPanel/ExitButton and is used to exit the app
    - FriendItemButton.cs: Corresponds to UIResources/FriendItemButton (prefab) and is used in the add-friend list
    - FriendsScrollView.cs: Corresponds to canvas/MainPanel/ContainerPanel/FriendsScrollView and is used to manage the friend list
    - HideButton.cs: Corresponds to canvas/HideButton and is used to hide the main window
    - HintBubbleButton.cs: Corresponds to UIResources/HintBubbleButton (prefab) and is used to display the number of new messages
    - InvokeButton.cs: Corresponds to canvas/BackGroundPanel/InvokeButton and is used to awaken the main window
    - MainPanel.cs: Corresponds to canvas/MainPanel and contains all the main page containers
    - MessageActionImage.cs: Corresponds to UIResources/MessageButton/ActionButton/BackGroundButton/MessageActionImage and is used to awaken the add-friend button or switch-to-single-chat button
    - MessageButton.cs: Corresponds to UIResources/MessageButton (prefab) and is used to add chat messages to the interface
    - MessageHintButton.cs: Corresponds to UIResources/MessageHintButton (prefab) and is used to add message prompts to the interface
    - MyResources.cs: Resource script, used to load various resources under Resources and provide usage interfaces
    - ScrollView.cs: Corresponds to UIResources/ScrollView (prefab), which serves as a container for chat messages and friend lists.
    - Sdk.cs: SDK encapsulation script, used to obtain information from configuration files, login, join chat rooms, provide message sending and receiving functions, and notify UIManager when receiving callbacks or messages.
    - SendContainerButton.cs: Corresponds to canvas/MainPanel/SendContainerButton, used for inputting and sending messages and invoking the Emoji panel.
    - SingleEmojiButton.cs: Corresponds to UIResources/SingleEmojiButton (prefab), used to add an Emoji expression to the text of the sent message.
    - TabButton.cs: Corresponds to canvas/MainPanel/TabButton, used to control the switching and display of the four Tab buttons on the main window.
    - Tools.cs: Basic function script, providing basic functions such as showing and hiding object objects, parsing configuration files, obtaining directories, Emoji character conversion and Unicode conversion, and time operations.
    - UIManager.cs: Main UI object management script, used to pass notifications to main UI objects to perform certain operations.
    
- StreamingAssets: Directory for configuration files, where sdk.txt is stored.

- TextMeshPro: Resource package. When scalable fonts are introduced, Unity automatically includes it. Within it,
    - TextMeshPro->Resources->TMP Settings->Default Sprite Asset is used to set the Emoji resource displayed on the text;
    - TextMeshPro->Sprites contains two emoji resource files: a JSON-formatted emoji data file and an image file for the emojis. They are used to generate the Emoji resources used in the Default Sprite Asset.
    
- UIResources: Prefab resources. Double-clicking on each prefab file shows the contents of its objects:
    - ApplyActionButton: Prefab for accepting or ignoring friend requests.
    - DateSplitButton: Prefab for displaying log and dividing lines.
    - FriendItemButton: Prefab for friend list items.
    - FriendSplitButton: Prefab for friend list dividing lines.
    - HintBubbleButton: Prefab for hint bubbles.
    - MessageButton: Prefab for chat messages.
    - MessageHintButton: Prefab for hint messages.
    - ScrollView: Prefab for containers of chat messages and friend lists.
    - SingleEmojiButton: Prefab for single Emoji expressions.
    - TabButton: Prefab for switching channels.

### 3 Introduction to unity_demo Code Architecture
Refer to structure_en.png

### 4 Some points for Secondary Development
All content in unity_demo can be modified. Here are several points for secondary development:

- Adjust the size of all UI elements
	Since different computers have different resolutions, the size of UI elements may not be coordinated. You can adjust the size of UI elements through Canvas Scaler -> Scaler Factor under Canvas. For example, adjusting this value to 1.8 on Mac would be more appropriate.

- Add Chat Room Tab
    - Add Tab: Drag a TabButton from UIResources to canvas/MainPanel/TabsButton in the Hierarchy.
    - Modify tab: Select TabButton, modify the Text content and Image content under it, and add corresponding tag to the tab;

- Delete Chat Room Tab
    Select the TabButton to be deleted in the scene and click Delete.

- Adjust the display of content in ScrollView
    - Modify Prefab: The content displayed in ScrollView mainly includes two parts: MessageButton and FriendItemButton. Select any of the prefabs in MessageButton or FriendItemButton in UIResources, double-click to enter the modification page, and make corresponding changes to the elements.
    - Modify Corresponding Scripts: After modifying the UI elements (such as deleting or renaming them), the corresponding scripts also need to be modified accordingly.
    
- Dynamically add new content in ScrollView
    - Make Prefab: You can first design and combine components under canvas, and when the style meets the requirements, drag the combined components to UIResources to generate prefabs.
    - Add Message Forwarding: Add message forwarding for the new prefab in ScrollView.
    - Add Scripts: Add script files to the new prefab to process the received messages, and then trigger UI operations.

- Modify Emoji content
    - Obtain Materials: Download or make Emoji materials.
    - Generate Emoji Data and Image Files: Use TexturePackerGUI to pack all Emoji materials into two files, a json data file and a png image file. TexturePackerGUI can also adjust the display center of each Emoji.
    - Generate Emoji Resource Files: In Unity Editor, under the menu Windows->TextMeshPro->Sprite Importer: drag the json file to Sprite Data Source, and drag the png file to Sprite Texture Atlas. Click Create Sprite Asset and Save Sprite Asset in turn to generate Emoji resource files, and copy the generated resource files to TextMeshPro/Resources/Sprite Assets directory.
    - Set Emoji Resource as Default Resource: In the Project directory, open TextMeshPro->Resources->TMP Settings, and drag the resource file just generated to Default Sprite Asset.
    - Adjust Emoji's Unicode Encoding: If the generated Emoji resource file has incorrect Unicode, double-click the Emoji resource file, find Sprite Character Table in the Inspector, and open the adjustment to modify the Unicode.
    Note: You need to click Edit Glyph below Unicode to successfully modify Unicode.

- Modify App Icon
    - Obtain Icon: Download or make App icons.
    - Add Icon to Project: Drag the icon to Resources/AppIcons directory.
    - Convert Icon Format: Select the icon, choose Sprite (2D and UI) type in Texture Type in Inspector, and apply.
    - Reference Icon: Open the menu File->Build Settting->Player settings->Player, and drag the icon to Default Icon.

- Change User Avatar
    - Obtain Avatar: Download or make user avatars.
    - Add Avatar to Project: Drag the avatar to Resources/Avatars directory.
    - Convert avatar format: Select the icon, select the Sprite(2D and UI) Type in the Inspector's Texture Type and apply.
    - Adjusting the profile picture using logic: Adjust the GetAvatarIndex and GetAvatarName logics of MyResources.cs in Tools.cs to obtain the picture name based on the user name