# DevinAI - djunod

## General

This is touted as a "Junior Coding Assistant", but so far I've given it pretty complicated tasks with Microsoft Maui and it has succeed pretty well with them.  I also had it successfully convert an old Windows .NET 4 app to .NET 8.  

I'm not the kind of guy that reads a lot of documentation, I just tend to jump right in, so I started out by setting up a github repository, slack integration and just started giving Devin tasks.  It succeeded at everything that I gave it.  Eventually, I went back and updated the knowledge base.

## Enhance Prompt

One of the most useful tips that I've learned is to give Grok (or ChatGPT, whatever you prefer) a description for me to then feed to Devin.

Here's a recent example of such a prompt:

```
what prompt should I use to instruct my Devin.AI coding assistant to convert a microsoft .net 4 desktop application to .net 8?
```

Grok then gave me:

```
"I need you to assist me in converting a Microsoft .NET 4 desktop application to .NET 8. The application is a [Windows Forms/WPF/other] desktop app written in [C#/VB.NET/other language], originally targeting .NET Framework 4.0. Your task is to guide me through the migration process or provide updated code to make it compatible with .NET 8, which is a modern, cross-platform framework with long-term support. Please follow these steps:
Analyze the Current Project: Review the existing project structure, including the .csproj file, dependencies (e.g., NuGet packages), and any third-party libraries. Identify any APIs or features that may not be supported in .NET 8 (e.g., AppDomains, Remoting, or System.Configuration).

Update the Project File: Convert the legacy .csproj file to the SDK-style project format used by .NET 8. Set the target framework to net8.0-windows (since this is a desktop app) and ensure it includes necessary properties like <UseWindowsForms>true> or <UseWPF>true> if applicable.

Handle Dependencies: Update or replace NuGet packages to versions compatible with .NET 8. If a dependency isn’t available, suggest alternatives or workarounds.

Refactor Code: Identify and update any code that uses deprecated or unsupported .NET Framework APIs. Provide replacements or alternatives compatible with .NET 8 (e.g., replace System.Configuration with Microsoft.Extensions.Configuration if applicable). Ensure the app remains functional on Windows.

Testing and Validation: Suggest steps to test the migrated application to ensure it works as expected after conversion. Highlight any potential breaking changes or areas needing manual review (e.g., UI layout changes due to font differences).

Provide Instructions: Offer a step-by-step explanation of the changes made, including any manual actions I need to take in Visual Studio 2022 (version 17.8 or later) or via the .NET CLI.

Assume I have Visual Studio 2022 installed with the .NET 8 SDK. If you need specific code snippets or files from my project to proceed (e.g., .csproj, source code), let me know what to provide. Otherwise, provide a general approach with example code where relevant. Do not generate images unless I explicitly request them."
```

I then fed that prompt into Slack using the following prefix:

```
Hey @Devin, using the Reality-Check-Inc/HeresTheKaraokePrivate repository, using the develop branch,
```

## SwiftUI

Recently somebody asked if Devin could do Swift UI.

One thing that I did have Devin fail on was creating or updating .xcodeproj files.  It did actually generate Swift code.

I gave grok the following prompt:

```
what prompt should I use to instruct my Devin.AI coding assistant to update a simple iOS app to use OpenAI's Speech To Text and Text To Speech for an iOS chat app where you can talk with open AI's chat bot?
```

It gave me:

```
"Modify an existing SwiftUI-based iOS chat app to integrate OpenAI's Speech-to-Text and Text-to-Speech APIs, enabling users to interact with OpenAI's chatbot using voice input and output. The app should:
Use AVFoundation to capture audio input from the device's microphone when the user taps a 'Record' button.

Send the recorded audio to OpenAI's Speech-to-Text API (e.g., Whisper API) to convert it to text.

Pass the transcribed text as a prompt to OpenAI's Chat API (e.g., GPT-3.5 or GPT-4) to generate a text response.

Convert the chatbot's text response to speech using OpenAI's Text-to-Speech API.

Play the synthesized audio response to the user using AVAudioPlayer or a similar framework.

The UI should include:
A chat interface displaying the conversation (user input and bot responses) as text.

A 'Record' button to start/stop audio recording.

Visual feedback (e.g., a waveform or 'Recording...' label) during recording.

Playback controls or auto-play for the bot's audio response.

Ensure the app handles errors gracefully (e.g., network issues, API failures) and includes necessary permissions (microphone access) in the Info.plist file. Use Alamofire or URLSession for API requests and assume I have an OpenAI API key ready to use. Provide the modified SwiftUI code with clear comments explaining the integration."
```

The results are [here](https://github.com/Reality-Check-Inc/DevinSwift)
