##Build a Basic UI
此课程让你熟悉Xcode（编写应用程序的工具）。熟悉Xcode中项目结的构，学习在基本的项目组件之间导航和使用。在本课程中，你将开始为FoodTracker创建一个简单的UI，并在模拟器中看到它。当你完成之后，应用程序应该看起来像这样：
>This lesson gets you familiar with Xcode, the tool you use to write apps. You’ll become familiar with the structure of a project in Xcode and learn how to navigate between and use basic project components. In the lesson, you’ll start making a simple user interface (UI) for the FoodTracker app and view it in the simulator. When you’re finished, your app will look something like this:

![1](./image/1_of_babu.png)

###Learning Objectives

当此课程结束时，你可以：

 - 在Xcode中创建一个项目
 - 确定一个用Xcode项目模版创建的密钥文件的目的？
 - 打开并在不同的项目文件中切换
 - 在iOS模拟器中运行一个应用程序
 - 在故事板中添加，移动，调整UI元素
 - 使用属性检查器编辑故事板中的UI元素的属性
 - 使用大纲视图查看和重排列UI元素
 - 使用辅助编辑器的预览模式预览故事板的UI
 - 使用自动布局去布局自适应用户设备尺寸的用户界面
 
>At the end of the lesson, you’ll be able to:
>
 - Create a project in Xcode
 - Identify the purpose of key files that are created with an Xcode project template
 - Open and switch between files in a project
 - Run an app in iOS Simulator
 - Add, move, and resize UI elements in a storyboard
 - Edit the attributes of UI elements in a storyboard using the Attributes inspector
 - View and rearrange UI elements using the outline view
 - Preview a storyboard UI using the Assistant editor’s Preview mode
 - Use Auto Layout to lay out a UI that automatically adapts to the user’s device size

###Create a New Project

Xcode有几个内置的应用程序模板，用于开发常见类型的iOS应用程序，例如游戏，基于标签的导航应用程序和基于表视图的应用程序。大多数这些模板具有预配置的接口和源代码文件。在本课中，你将从最基本的模板开始：Single View Application。
>Xcode includes several built-in app templates for developing common types of iOS apps, such as games, apps with tab-based navigation, and table view-based apps. Most of these templates have preconfigured interface and source code files. For this lesson, you’ll start with the most basic template: Single View Application.

###Review the Source Code

单一视图应用程序模板包含几个设置app环境的源代码文件。首先，看看AppDelegate.swift文件。
>The Single View Application template comes with a few source code files that set up the app environment. First, take a look at the AppDelegate.swift file.

####The App Delegate Source File

AppDelegate.swift 源文件有两个主要的方法：
>The AppDelegate.swift source file has two primary functions:

 1.它定义了你的AppDelegate(委托)类。应用程式委托建立应用程式内容绘制的窗口，并提供位置回应app状态转换。

 2.它创建app的的入口点，运行一个提供输入事件进入app的循环。此工作由UIApplicationMain属性（@UIApplicationMain）完成，该属性显示在文件的顶部。
> 1. It defines your AppDelegate class. The app delegate creates the window where your app’s content is drawn and provides a place to respond to state transitions within the app.

> 2. It creates the entry point to your app and a run loop that delivers input events to your app. This work is done by the UIApplicationMain attribute (@UIApplicationMain), which appears toward the top of the file.

使用UIApplicationMain属性等效于调用UIApplicationMain函数,并将AppDelegate类的名称作为委托类的名称。作为响应，系统创建应用程序对象。应用程序对象负责管理应用程序的生命周期。系统还会创建AppDelegate类的实例，并将其分配给应用程序对象。最后，系统启动您的应用程序。
>Using the UIApplicationMain attribute is equivalent to calling the UIApplicationMain function and passing your AppDelegate class’s name as the name of the delegate class. In response, the system creates an application object. The application object is responsible for managing the life cycle of the app. The system also creates an instance of your AppDelegate class, and assigns it to the application object. Finally, the system launches your app.


AppDelegate类在您创建新项目时自动创建。除非你做非常不寻常的事情，否则应该使用Xcode提供的这个类来初始化你的app并响应app级事件。 AppDelegate类采用UIApplicationDelegate协议。此协议定义了许多方法，用于设置您的app，响应app的状态更改，以及处理其他app级事件。
>The AppDelegate class is automatically created whenever you create a new project. Unless you are doing something highly unusual, you should use this class provided by Xcode to initialize your app and respond to app-level events. The AppDelegate class adopts the UIApplicationDelegate protocol. This protocol defines a number of methods you use to set up your app, to respond to the app’s state changes, and to handle other app-level events.

AppDelegate类包含单一个单属性：window。
>The AppDelegate class contains a single property: window.

此属性存储一个对app窗口的引用。此窗口表示app视图层次结构的根。这是您的app所有内容绘制的地方。注意，window属性是可选的，这意味着它在某些时候可能没有值（be nil）。
>This property stores a reference to the app’s window. This window represents the root of your app’s view hierarchy. It is where all of your app content is drawn. Note that the window property is an optional, which means it may have no value (be nil) at some point.

AppDelegate类还包含以下代理方法的stub实现：
>The AppDelegate class also contains stub implementations of the following delegate methods:

```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool
func applicationWillResignActive(_ application: UIApplication)
func applicationDidEnterBackground(_ application: UIApplication)
func applicationWillEnterForeground(_ application: UIApplication)
func applicationDidBecomeActive(_ application: UIApplication)
func applicationWillTerminate(_ application: UIApplication)
```

这些方法让应用程序对象与app委托进行通信。在应用程序状态转换期间（例如，app启动，转换到后台和app终止），应用程序对象调用相应的委托方法，从而为您的app提供响应机会。你不需要执行任何特殊操作，以确保这些方法在正确的时间调用 - 应用程序对象为你处理该作业。
>These methods let the application object communicate with the app delegate. During an app state transition—for example, app launch, transitioning to the background, and app termination—the application object calls the corresponding delegate method, giving your app an opportunity to respond. You don’t need to do anything special to make sure these methods get called at the correct time—the application object handles that job for you.

每个委托方法都有一个默认行为。如果你不去实现模板或从AppDelegate类中删除它，无论什么时候调用该方法，都会获得默认行为。或者，您可以向stub方法添加自己的代码，使调用方法时执行的自定义行为。
>Each of the delegate methods has a default behavior. If you leave the template implementation empty or delete it from your AppDelegate class, you get the default behavior whenever that method is called. Alternatively, you can add your own code to the stub methods, defining custom behaviors that are executed when the methods are called.

模板还为每个存根方法提供注释。这些注释描述你的app如何使用这些方法。你可以使用stub方法和注释作为设计许多常见app级行为的蓝图。
>The template also provides comments for each of the stub methods. These comments describe how these methods can be used by your app. You can use the stub methods and comments as a blueprint for designing many common app-level behaviors.

在本课程中，您不会使用任何自定义app委托代码，因此您不必对AppDelegate.swift文件进行任何更改。
>In this lesson, you won’t be using any custom app delegate code, so you don’t have to make any changes to the AppDelegate.swift file.

####The View Controller Source File

单一视图app模板有另一个源代码文件：ViewController.swift。在项目导航器中选择ViewController.swift以查看它。
>The Single View Application template has another source code file: ViewController.swift. Select ViewController.swift in the project navigator to view it.

这个文件定义了一个名为ViewController的UIViewController的自定义子类。现在，这个类简单地继承了UIViewController定义的所有行为。要覆盖或扩展该行为，你可以覆盖在UIViewController上定义的方法。
>This file defines a custom subclass of UIViewController named ViewController. Right now, this class simply inherits all the behavior defined by UIViewController. To override or extend that behavior, you override the methods defined on UIViewController.

正如你可以在ViewController.swift文件中看到的，模板的实现覆盖viewDidLoad 和didReceiveMemoryWarning 方法;然而，模板的sub实现除了调用这些方法的UIViewController版本外不执行任何操作。您可以添加自己的代码以自定义视图控制器对这些事件的响应。
>As you can see in the ViewController.swift file, the template’s implementation overrides both the viewDidLoad() and didReceiveMemoryWarning() methods; however, the template’s stub implementation doesn’t do anything yet, except call the UIViewController version of these methods. You can add your own code to customize the view controller’s response to these events.

虽然模板自带了didReceiveMemoryWarning 方法，但您不需要在这些课程中实现它，因此请继续并删除它。
>Although the template comes with the didReceiveMemoryWarning() method, you won’t need to implement it in these lessons, so go ahead and delete it.


###Open Your Storyboard

你已经准备好从你的app的故事板开始学习了。首先，故事板是app的用户界面的可视化表示，显示内容的屏幕和它们之间的过渡。你使用故事板来设计驱动你的app的流程或故事。您可以在构建它时准确地了解自己正在构建的内容，即时了解哪些是有效的，哪些不可用，并对您的用户界面进行即时可见的更改。
>You’re ready to start working on a storyboard for your app. A storyboard is a visual representation of the app’s user interface, showing screens of content and the transitions between them. You use storyboards to lay out the flow—or story—that drives your app. You see exactly what you're building while you’re building it, get immediate feedback about what’s working and what’s not, and make instantly visible changes to your user interface.