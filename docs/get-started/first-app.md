---
title: "Build your first .NET MAUI app in Visual Studio"
description: "How to create and run your first .NET MAUI app."
zone_pivot_groups: preview-platforms
ms.date: 07/15/2021
---

# Build your first .NET MAUI app

In this tutorial, you'll learn how to create and run your first .NET Multi-platform App UI (MAUI) app.

> [!NOTE]
> Visual Studio for Mac support will arrive in a future release.

::: zone pivot="windows"

## Prerequisites

- An environment that has been configured for .NET MAUI development, using the maui-check tool. For more information, see [Install .NET 6 Preview 6](installation.md#install-net-6-preview-6).
- Visual Studio 2022 (Preview 2 or newer), with the required workloads. For more information, see [Installation](installation.md).
- A configured Android emulator. For more information about creating an Android emulator, see [Android emulator setup](/xamarin/android/get-started/installation/android-emulator/).

## Get started with Visual Studio 2022 (Preview)

In this tutorial, you'll create your first .NET MAUI app in Visual Studio 2022, and run it on an Android emulator:

1. Open a command prompt and create a new project by running the command:

    ```dotnetcli
    dotnet new maui -n HelloMaui
    ```

1. Launch Visual Studio 2022 build 17.0 (Preview 2 or greater), and in the start window click **Open a project or solution** to browse for your solution:

    :::image type="content" source="first-app-images/start-open.png" alt-text="Open solution.":::

1. Wait for the project to load, and its dependencies to be restored:

    :::image type="content" source="first-app-images/restored-dependencies.png" alt-text="Restored dependencies.":::

1. In the Visual Studio toolbar, select the drop-down next to the **Start** button (the triangular button that resembles a Play button), select **Android Emulator**, and then select the emulator you'd like to deploy the app to:

    :::image type="content" source="first-app-images/select-android-emulator.png" alt-text="Select your Android emulator.":::

1. In the Visual Studio toolbar, press the **Start** button to launch the app in your chosen Android emulator.

1. In the running app in the Android emulator, press the **CLICK ME** button several times and observe that the count of the number of button clicks is incremented.

    :::image type="content" source="first-app-images/running-app.png" alt-text="App running in the Android emulator." lightbox="first-app-images/running-app-large.png":::

## Build and debug iOS apps

To build and debug .NET 6 iOS apps from Visual Studio 2022 you must manually install the .NET 6 SDK and iOS workloads on both Windows and macOS (your Mac build host).

If, while connecting Visual Studio to your Mac through Xamarin Mac Agent (XMA), you are prompted to install a different version of the SDK, you can ignore the prompt since it refers to a legacy version of XMA.

> [!NOTE]
> Visual Studio 2022 can only currently deploy .NET MAUI iOS apps to the iOS simulator, and not to physical devices.

::: zone-end
::: zone pivot="dotnet-cli"

## Prerequisites

- An environment that has been configured for .NET MAUI development, using the maui-check tool. For more information, see [Install .NET 6 Preview 6](installation.md#install-net-6-preview-6).
- A configured simulator or emulator for your chosen platform. For more information about creating an Android emulator, see [Android emulator setup](/xamarin/android/get-started/installation/android-emulator/).

## Get started with .NET command-line interface

In this tutorial, you'll create and run your first .NET MAUI app using the .NET command-line interface (CLI):

1. In the .NET CLI, create a new .NET MAUI app:

    ```dotnetcli
    dotnet new maui -n HelloMauiPreview
    ```

1. In the .NET CLI, change directory to the newly created project:

    ```dotnetcli
    cd HelloMauiPreview
    ```

1. In the .NET CLI, change directory to the single project and restore its dependencies:

    ```dotnetcli
    cd HelloMauiPreview
    dotnet restore
    ```

1. In the .NET CLI, build and launch the app on your chosen platform:

    ```dotnetcli
    dotnet build -t:Run -f net6.0-android
    dotnet build -t:Run -f net6.0-ios
    dotnet build -t:Run -f net6.0-maccatalyst
    ```

    > [!NOTE]
    > These commands will launch the app on the default platform device, if one can be found. On Android, it's recommended to start an emulator before building and launching your app.

## Select an iOS simulator

It's possible to specify which simulator is launched and used for net6.0-ios by specifying the `_DeviceName` MSBuild property:

```dotnetcli
dotnet build -t:Run -f net6.0-ios -p:_DeviceName=:v2:udid=<UDID>
```

You can retrieve a list of possible unique device id (UDID) values by executing the `simctl list` command:

```console
/Applications/Xcode.app/Contents/Developer/usr/bin/simctl list
```

The default iOS simulator will be launched if you don't specify a UDID.

::: zone-end
