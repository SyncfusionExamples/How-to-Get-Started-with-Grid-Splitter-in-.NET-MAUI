# Getting Started with .NET MAUI GridSplitter (SfGridSplitter)

This section provides a quick overview for working with the SfGridSplitter for .NET MAUI. Walk through the entire process of creating a basic resizable layout with multiple panes.

## Creating an application using the .NET MAUI GridSplitter

1. Create a new .NET MAUI application in Visual Studio.
2. Syncfusion .NET MAUI components are available on [nuget.org](https://www.nuget.org/). To add SfGridSplitter to your project, open the NuGet package manager in Visual Studio, search for **Syncfusion.Maui.GridSplitter** and then install it.

## Register the handler

To use this control inside an application, you must register the handler for Syncfusion® core.

```C#

using Microsoft.Extensions.Logging;
using Syncfusion.Maui.Core.Hosting;

namespace GridSplitterGettingStarted
{
    public static class MauiProgram
    {
        public static MauiApp CreateMauiApp()
        {
            var builder = MauiApp.CreateBuilder();

            builder
                .UseMauiApp<App>()
                .ConfigureSyncfusionCore()
                .ConfigureFonts(fonts =>
                {
                    fonts.AddFont("OpenSans-Regular.ttf", "OpenSansRegular");
                    fonts.AddFont("OpenSans-Semibold.ttf", "OpenSansSemibold");
                });

#if DEBUG
            builder.Logging.AddDebug();
#endif

            return builder.Build();
        }
    }
}

```

## Add a basic GridSplitter

1. Import the control namespace `Syncfusion.Maui.GridSplitter` in XAML.
2. Initialize the `SfGridSplitter` control.

**XAML**

```xml
<ContentPage
    ...
    xmlns:gridSplitter="clr-namespace:Syncfusion.Maui.GridSplitter;assembly=Syncfusion.Maui.GridSplitter">

    <gridSplitter:SfGridSplitter>

        <gridSplitter:SplitterPane>
            <Border Background="LightBlue"
                    Padding="10">
                <Label Text="Pane 1"
                       HorizontalOptions="Center"
                       VerticalOptions="Center" />
            </Border>
        </gridSplitter:SplitterPane>

        <gridSplitter:SplitterPane>
            <Border Background="LightGreen"
                    Padding="10">
                <Label Text="Pane 2"
                       HorizontalOptions="Center"
                       VerticalOptions="Center" />
            </Border>
        </gridSplitter:SplitterPane>

    </gridSplitter:SfGridSplitter>

</ContentPage>
```

**C#**

```csharp
using Syncfusion.Maui.GridSplitter;

namespace GridSplitterGettingStarted
{
    public partial class MainPage : ContentPage
    {
        public MainPage()
        {
            InitializeComponent();

            SfGridSplitter gridSplitter = new SfGridSplitter();

            SplitterPane pane1 = new SplitterPane
            {
                Content = new Border
                {
                    Background = Colors.LightBlue,
                    Padding = 10,
                    Content = new Label
                    {
                        Text = "Pane 1",
                        HorizontalOptions = LayoutOptions.Center,
                        VerticalOptions = LayoutOptions.Center
                    }
                }
            };

            SplitterPane pane2 = new SplitterPane
            {
                Content = new Border
                {
                    Background = Colors.LightGreen,
                    Padding = 10,
                    Content = new Label
                    {
                        Text = "Pane 2",
                        HorizontalOptions = LayoutOptions.Center,
                        VerticalOptions = LayoutOptions.Center
                    }
                }
            };

            gridSplitter.AddPane(pane1);
            gridSplitter.AddPane(pane2);

            Content = gridSplitter;
        }
    }
}
```

## Create a resizable pane layout using .NET MAUI GridSplitter

The `SplitterPane` collection allows you to organize content into multiple resizable panes. In this example, the GridSplitter contains two panes with different background colors. Users can drag the splitter between the panes to dynamically adjust the available space at runtime.

**XAML**

```xml
<gridSplitter:SfGridSplitter>

    <gridSplitter:SplitterPane>
        <Border Background="LightBlue"
                Padding="10">
            <Label Text="Pane 1"
                   HorizontalOptions="Center"
                   VerticalOptions="Center" />
        </Border>
    </gridSplitter:SplitterPane>

    <gridSplitter:SplitterPane>
        <Border Background="LightGreen"
                Padding="10">
            <Label Text="Pane 2"
                   HorizontalOptions="Center"
                   VerticalOptions="Center" />
        </Border>
    </gridSplitter:SplitterPane>

</gridSplitter:SfGridSplitter>
```

**C#**

```csharp
SfGridSplitter gridSplitter = new SfGridSplitter();

SplitterPane pane1 = new SplitterPane
{
    Content = new Border
    {
        Background = Colors.LightBlue,
        Padding = 10,
        Content = new Label
        {
            Text = "Pane 1",
            HorizontalOptions = LayoutOptions.Center,
            VerticalOptions = LayoutOptions.Center
        }
    }
};

SplitterPane pane2 = new SplitterPane
{
    Content = new Border
    {
        Background = Colors.LightGreen,
        Padding = 10,
        Content = new Label
        {
            Text = "Pane 2",
            HorizontalOptions = LayoutOptions.Center,
            VerticalOptions = LayoutOptions.Center
        }
    }
};

gridSplitter.AddPane(pane1);
gridSplitter.AddPane(pane2);

Content = gridSplitter;
```

