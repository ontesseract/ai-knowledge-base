# DevinAI - djunod

This is touted as a "Junior Coding Assistant", but so far I've given it pretty complicated tasks with Microsoft Maui and it has succeed pretty well with them.  
I also had it successfully convert an old Windows .NET 4 app to .NET 8.  
I'm not the kind of guy that reads a lot of documentation, I just tend to jump right in, so I started out by setting up a github repository, slack integration
and just started giving Devin tasks.  It succeeded at everything that I gave it.  Eventually, I went back and updated the knowledge base.

One of the most useful tips that I've learned is to give Grok (or ChatGPT, whatever you prefer) a description for me to then feed to Devin.

Here's a recent example of such a prompt:

```
what prompt should I use to instruct my Devin.AI coding assistant to convert a microsoft .net 8 karaoke desktop application to maui using CommunityToolkit.Mvvm view/viewmodel architecture?
```

Grok then gave me:

```
I need you to assist me in converting an existing Microsoft .NET 8 karaoke desktop application to a cross-platform .NET MAUI application using the CommunityToolkit.Mvvm library for implementing the MVVM (Model-View-ViewModel) architecture. The original application is a Windows-only desktop app built with .NET 8, likely using Windows Forms, WPF, or a similar UI framework, and it includes features such as song selection, playback controls, lyrics display, and possibly file management for karaoke tracks. Your task is to refactor this application to work across multiple platforms (Windows, macOS, Android, and iOS) using .NET MAUI, while adopting the CommunityToolkit.Mvvm library for a clean MVVM structure.
Here’s what I expect:
Project Setup: Create a new .NET MAUI project configured for multi-platform support (Windows, macOS, Android, iOS). Ensure the project targets .NET 8 and includes the necessary MAUI workloads and dependencies.

NuGet Packages: Add the CommunityToolkit.Mvvm NuGet package to the project to enable MVVM features like ObservableObject, RelayCommand, and source generators for property change notifications.

Architecture:
Models: Identify and preserve the core data structures from the original app (e.g., Song, Playlist, etc.) as plain C# classes representing the karaoke domain logic.

ViewModels: Refactor the business logic from the original app into ViewModels that inherit from ObservableObject. Use [ObservableProperty] attributes for data-bound properties and [RelayCommand] for commands (e.g., PlaySongCommand, LoadPlaylistCommand). Ensure ViewModels are platform-agnostic and handle asynchronous operations (e.g., file I/O, playback) using AsyncRelayCommand where needed.

Views: Replace the original UI with MAUI XAML-based views (e.g., ContentPage) that bind to the ViewModels. Use MAUI controls like CollectionView for song lists, MediaElement for playback, and Label or custom controls for lyrics display. Set the BindingContext of each view to its corresponding ViewModel.

Dependency Injection: Use MAUI’s built-in dependency injection (via MauiProgram.cs) to register services (e.g., file access, audio playback) and ViewModels as singletons or transients, then inject them into the Views or ViewModels as needed.

Platform-Specific Code: Handle any platform-specific requirements (e.g., file system access, audio playback APIs) using MAUI’s platform abstraction features or conditional compilation, ensuring the app remains functional across all targeted platforms.

Key Features to Migrate:
Song selection: Convert any list or grid of songs into a MAUI CollectionView bound to a ViewModel property.

Playback controls: Implement play, pause, stop, and seek functionality using MAUI’s MediaElement or a custom audio service, controlled via ViewModel commands.

Lyrics display: Sync lyrics with playback, possibly using a timer or event-driven approach in the ViewModel, and display them in the MAUI UI.

File management: Adapt file loading/saving logic to work with MAUI’s cross-platform file system APIs.

Steps to Follow:
Analyze the existing .NET 8 karaoke app’s structure and identify its models, logic, and UI components.

Create a new MAUI project and install CommunityToolkit.Mvvm.

Port the models and logic into the new project, organizing them into MVVM components.

Build the MAUI XAML views and bind them to the ViewModels.

Test the app on at least two platforms (e.g., Windows and Android) to ensure cross-platform compatibility.

Output: Provide the converted project structure, including key code files (e.g., MauiProgram.cs, ViewModels, XAML views, and any services), along with explanations of the changes made. If assumptions are needed about the original app’s code (since I haven’t provided it), base them on typical karaoke app functionality and note them clearly.

Please proceed step-by-step, asking for clarification if needed, and provide the resulting code and project structure as you complete the conversion. Let’s start with setting up the MAUI project and integrating CommunityToolkit.Mvvm.
```

I then fed that prompt into Slack using the following prefix:

```
Hey @Devin, using the Reality-Check-Inc/HeresTheKaraokePrivate repository, using the develop branch,
```
