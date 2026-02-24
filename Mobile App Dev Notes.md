# Mobile Application Development (MAD)

# UNIT 1 — Introduction to Mobile Application Development & Mobile UI Design

## 1.1 Introduction to Mobile Application Development

### What is a Mobile Application?
**Simply:** A mobile app is a software program designed to run on smartphones and tablets — like WhatsApp, Instagram, or Google Maps.

**Technically:** A mobile application is a software application developed specifically for use on small, wireless computing devices such as smartphones and tablets, running on mobile operating systems like Android or iOS.

### Mobile Application Development Platforms

**Simply:** Just like you can build a website for Chrome or Firefox, you build mobile apps for specific platforms — mainly Android and iOS. There are different approaches to do this.

**Technically:** Mobile development platforms are the environments and frameworks used to build, test, and deploy mobile apps. The main categories are:

| Type | Description | Examples |
|------|-------------|---------|
| **Native** | Built for one specific OS using its official language | Android (Java/Kotlin), iOS (Swift/Objective-C) |
| **Cross-Platform / Hybrid** | One codebase runs on multiple platforms | Flutter, React Native, Xamarin |
| **Web-Based** | Runs in a mobile browser | HTML5, CSS3, JavaScript apps |

**Key Exam Point:** Native apps offer the best performance but cost more. Hybrid apps save development time and cost.

### Cost of Mobile App Development

**Simply:** Building an app isn't free — you pay for developers, tools, hosting, and maintenance.

**Technically:** The cost of mobile app development depends on several factors:

- **Complexity** — Simple apps cost less; complex apps with databases, APIs, and animations cost more
- **Platform** — Developing for both Android and iOS separately doubles the cost
- **Development Approach** — Native is expensive; cross-platform reduces cost
- **Developer Type** — Freelancer < Agency < In-house team (in terms of cost)
- **Maintenance & Updates** — Ongoing cost after launch (bug fixes, OS updates, new features)
- **App Store Fees** — Google Play: one-time $25 | Apple App Store: $99/year

### Myths of Mobile App Development

**Simply:** Many people have wrong beliefs about making apps — like "it's easy" or "it'll make instant money."

**Technically — Common Myths Debunked:**

| Myth | Reality |
|------|---------|
| "Building an app is cheap and quick" | Development requires planning, design, coding, testing, and deployment |
| "A great app will automatically attract users" | Marketing and app store optimization (ASO) are equally important |
| "My app needs to be on every platform immediately" | Start with one platform, validate, then expand |
| "Once launched, the app is done" | Apps need regular updates, bug fixes, and feature additions |
| "An app alone can make a business successful" | The app is just a tool; business strategy matters more |
| "More features = better app" | Overloaded apps confuse users; simplicity is key (MVP approach) |

### Benefits of Mobile App for Business

**Simply:** Mobile apps help businesses reach more customers, make sales easier, and build loyalty.

**Technically — Key Benefits:**

- **Increased Visibility:** Users spend 90% of mobile time in apps; an app keeps your brand visible
- **Direct Marketing Channel:** Push notifications allow direct communication with customers
- **Customer Engagement:** In-app features like loyalty programs, offers, and feedback increase engagement
- **Revenue Generation:** Apps enable e-commerce, in-app purchases, subscriptions, and ads
- **Improved Customer Service:** Chatbots, FAQs, and support features reduce load on call centers
- **Competitive Advantage:** Businesses with apps appear more professional and tech-savvy
- **Data Collection:** Apps collect usage data and analytics to improve business decisions
- **Offline Functionality:** Apps can work without internet (unlike websites), improving accessibility

## 1.2 Mobile User Interface Design

### Effective Use of Screen Real Estate

**Simply:** A phone screen is tiny compared to a computer. You have to be smart about what you show and where.

**Technically:** Screen real estate refers to the available display area on a mobile device. Effective use involves:

- **Prioritize Content:** Show only what's essential; use progressive disclosure (reveal more on demand)
- **Use Whitespace:** Don't clutter — spacing improves readability and reduces cognitive load
- **Thumb-Friendly Design:** Place interactive elements in the lower half of the screen (reachable zone)
- **Avoid Desktop Patterns:** No hover effects, no right-click menus — mobile needs tap, swipe, pinch
- **Adaptive Layouts:** Design for various screen sizes using responsive/adaptive UI
- **Use Icons + Labels:** Icons save space but labels prevent confusion
- **Collapsible Menus / Drawers:** Use hamburger menus to hide secondary navigation

### Understanding Mobile Application Users

**Simply:** Different people use apps differently — age, tech comfort, location, and purpose all matter.

**Technically:** Understanding mobile users involves analyzing:

- **Demographics:** Age, gender, location, language, and tech literacy influence UI decisions
- **Usage Context:** Users may be on the move, distracted, or in low-light conditions
- **Session Length:** Mobile sessions are short — users expect quick interactions
- **Input Methods:** Touch (finger/stylus), voice input, gestures — design accordingly
- **Device Diversity:** Apps must work across various screen sizes, resolutions, and hardware specs
- **User Goals:** Task-oriented users want efficiency; leisure users want engagement
- **Mental Models:** Users expect familiar patterns (back button, swipe to delete, pull to refresh)

### Accessibility to Differently-Abled Users

**Simply:** Apps should be usable by everyone — including people with visual, hearing, or physical disabilities.

**Technically:** Mobile accessibility ensures inclusive design for users with disabilities:

| Disability | Design Solution |
|-----------|----------------|
| Visual Impairment | Screen readers (TalkBack on Android), high contrast, scalable fonts |
| Hearing Impairment | Captions, visual alerts, vibration feedback instead of sounds |
| Motor Impairment | Large tap targets (min 48x48dp), voice control, switch access |
| Cognitive Impairment | Simple language, clear navigation, consistent layout |

**Key Accessibility Standards:** WCAG (Web Content Accessibility Guidelines) — aim for AA compliance

**Android Accessibility Features:**
- TalkBack (screen reader)
- Magnification gestures
- Font size settings
- Switch access
- Voice access

### Understanding Mobile Information Design

**Simply:** It's about organizing information in a clear, easy-to-understand way so users don't get confused.

**Technically:** Mobile information design is the process of structuring, organizing, and presenting information for optimal user comprehension on mobile devices. Key principles:

- **Information Hierarchy:** Use size, color, and placement to show what's most important
- **Card-Based Design:** Group related information in cards (like Google Now, Trello)
- **Progressive Disclosure:** Show summary first; let users tap for details
- **Chunking:** Break large blocks of text into smaller digestible pieces
- **Consistent Navigation Patterns:** Bottom navigation bar, tab bar, or drawer — pick one and be consistent
- **Visual Feedback:** Buttons should visually respond when tapped (ripple effect)
- **Loading States:** Show spinners or skeleton screens while data loads
- **Error States:** Clearly explain errors and provide next steps

# UNIT 2 — Introduction to Android & Configuring Android Development Environment

## 2.1 Introduction to Android

### Android Operating System

**Simply:** Android is the software that powers most smartphones in the world — made by Google.

**Technically:** Android is an open-source, Linux-based mobile operating system developed by Google. It is designed primarily for touchscreen mobile devices such as smartphones and tablets. Being open-source (AOSP — Android Open Source Project), manufacturers can customize it freely.

**Key Facts:**
- Most widely used mobile OS globally (~72% market share)
- Written in: Java, Kotlin (app layer), C/C++ (native), Assembly (kernel)
- App distribution: Google Play Store + APK sideloading

### History of Android

**Simply:** Android started as a small startup, then Google bought it, and it grew to dominate mobile.

**Technically:**

| Year | Event |
|------|-------|
| 2003 | Android Inc. founded by Andy Rubin, Rich Miner, Nick Sears, Chris White |
| 2005 | Google acquired Android Inc. |
| 2007 | Android announced; Open Handset Alliance formed |
| 2008 | Android 1.0 released on HTC Dream (T-Mobile G1) — first commercial Android phone |
| 2010 | Android 2.2 (Froyo) — major performance improvements |
| 2011 | Android 3.0 (Honeycomb) — tablet-focused |
| 2014 | Android 5.0 (Lollipop) — Material Design introduced |
| 2017 | Kotlin officially supported |
| 2019 | Android 10 — dark mode, gesture navigation |
| 2023+ | Android 14/15 — improved privacy, predictive back, satellite connectivity |

### Versions of Android

**Simply:** Android has had many updates over the years, each adding new features. They were named after desserts (A to Z) until Android 10.

**Technically — Major Versions:**

| Version | Name | API Level | Year |
|---------|------|-----------|------|
| 1.0 | (No name) | 1 | 2008 |
| 1.5 | Cupcake | 3 | 2009 |
| 2.2 | Froyo | 8 | 2010 |
| 2.3 | Gingerbread | 9-10 | 2010 |
| 4.0 | Ice Cream Sandwich | 14 | 2011 |
| 4.1-4.3 | Jelly Bean | 16-18 | 2012 |
| 4.4 | KitKat | 19 | 2013 |
| 5.0 | Lollipop | 21 | 2014 |
| 6.0 | Marshmallow | 23 | 2015 |
| 7.0 | Nougat | 24 | 2016 |
| 8.0 | Oreo | 26 | 2017 |
| 9 | Pie | 28 | 2018 |
| 10 | Android 10 | 29 | 2019 |
| 11 | Android 11 | 30 | 2020 |
| 12 | Android 12 | 31 | 2021 |
| 13 | Android 13 | 33 | 2022 |
| 14 | Android 14 | 34 | 2023 |

**Exam Note:** API Level is important for developers — it determines which features are available.

### Features of Android

**Simply:** Android can do a lot — from making calls to running AI, and it's customizable.

**Technically — Key Features:**

- **Open Source:** Based on AOSP; manufacturers and developers can modify it
- **Multitasking:** Run multiple apps simultaneously; background services
- **Rich Notification System:** Expandable, actionable notifications
- **Google Services Integration:** Gmail, Maps, Assistant, Drive built-in
- **App Ecosystem:** Millions of apps on Google Play Store
- **Connectivity:** Wi-Fi, Bluetooth, NFC, 5G, USB, Hotspot
- **Media Support:** Supports MP3, AAC, FLAC, H.264, HEVC, and more
- **Camera API:** Advanced camera controls including RAW capture, HDR
- **Security:** SELinux, app sandboxing, Google Play Protect, biometrics
- **Customizability:** Widgets, launchers, custom ROMs
- **Kotlin/Java Support:** Modern development with Jetpack libraries

### Overview of Android Architecture

**Simply:** Android is built in layers — like a cake. Each layer has a specific job and talks to the layer above/below it.

**Technically — Android Architecture Layers (Bottom to Top):**

```
┌─────────────────────────────────────────────────┐
│              APPLICATIONS LAYER                 │  ← Your apps (WhatsApp, Gmail, etc.)
├─────────────────────────────────────────────────┤
│          APPLICATION FRAMEWORK                  │  ← APIs for developers (Activity Manager,
│  (Activity Manager, Content Providers, etc.)    │    Window Manager, View System, etc.)
├─────────────────────────────────────────────────┤
│    ANDROID RUNTIME  |  NATIVE LIBRARIES         │  ← ART (executes .dex files) + C/C++ libs
│    (ART / Dalvik)   |  (SQLite, OpenGL, etc.)   │    (SQLite, WebKit, SSL, etc.)
├─────────────────────────────────────────────────┤
│              LINUX KERNEL                       │  ← Hardware drivers, memory, process mgmt
│   (Drivers: Display, Camera, WiFi, Audio...)    │
└─────────────────────────────────────────────────┘
```

**Layer-wise Explanation:**

| Layer | Role |
|-------|------|
| **Linux Kernel** | Hardware abstraction, drivers, memory management, security |
| **Native Libraries** | C/C++ libraries — SQLite (database), OpenGL (graphics), SSL (security) |
| **Android Runtime (ART)** | Executes Android apps; compiles DEX bytecode to native code (AOT compilation) |
| **Application Framework** | Java APIs that developers use — Activities, Views, Location, Sensors |
| **Applications** | End-user apps and system apps (Phone, Camera, Settings) |

### Overview of Android App Components

**Simply:** Every Android app is made of building blocks. There are 4 main types — like 4 types of LEGO pieces that together make an app.

**Technically — The 4 Core App Components:**

#### 1.  Activity
- **Simple:** One screen of your app. Like one page in a book.
- **Technical:** An Activity represents a single screen with a user interface. It handles user interaction and manages the lifecycle of a screen. Example: `LoginActivity`, `MainActivity`
- Declared in `AndroidManifest.xml`
- Extends `AppCompatActivity` class

#### 2.  Service
- **Simple:** A task running in the background — like music playing even when you switch apps.
- **Technical:** A Service is a component that runs in the background to perform long-running operations without a UI. Types:
  - **Foreground Service:** Visible notification (music player)
  - **Background Service:** No visible notification (syncing data)
  - **Bound Service:** Allows other components to bind and interact with it

#### 3.  Broadcast Receiver
- **Simple:** Listens for system-wide announcements — like "battery low" or "internet connected."
- **Technical:** A Broadcast Receiver responds to system-wide broadcast announcements. It has no UI but can start an activity or post a notification. Examples:
  - `ACTION_BOOT_COMPLETED` — run code after device boots
  - `ACTION_BATTERY_LOW` — alert user about low battery
  - `CONNECTIVITY_CHANGE` — detect network changes

#### 4.  Content Provider
- **Simple:** Manages shared data between apps — like your contacts app sharing data with WhatsApp.
- **Technical:** A Content Provider manages access to a structured set of data. It provides data to other applications using a URI-based interface. Uses `ContentResolver` to query data. Example: `ContactsContract` for accessing phone contacts.

## 2.2 Configuring Android Development Environment

### Downloading and Installing JDK and Android Studio

**Simply:** Before writing Android code, you need to install two things — Java (the language engine) and Android Studio (the coding workspace).

**Technically:**

#### Step 1: Install JDK (Java Development Kit)
- Android Studio now includes a bundled JDK (JDK 11+), so separate installation is often not needed
- If required: Download from [Oracle JDK](https://www.oracle.com/java/technologies/downloads/) or use OpenJDK
- JDK provides: `javac` (Java Compiler), `java` (JVM), standard libraries

#### Step 2: Install Android Studio
- Download from: [https://developer.android.com/studio](https://developer.android.com/studio)
- Includes: Code editor (based on IntelliJ IDEA), Android SDK, emulator, ADB, Gradle build system
- **System Requirements (minimum):**
  - RAM: 8 GB (16 GB recommended)
  - Storage: 8 GB free (SSD recommended)
  - OS: Windows 8+, macOS 10.14+, Linux (64-bit)
- During installation: SDK components are downloaded — Platform Tools, Build Tools, SDK Platforms

### Creating First Android App

**Simply:** Think of creating an Android project like setting up a new folder with all the template files your app needs.

**Technically:**

#### Step 1: Create a New Android Project
1. Open Android Studio → **New Project**
2. Choose template: `Empty Activity` (for beginners)
3. Fill in:
   - **Name:** Your app name (e.g., `HelloWorld`)
   - **Package Name:** Unique identifier (e.g., `com.yourname.helloworld`) — reverse domain convention
   - **Save Location:** Where to save the project
   - **Language:** Kotlin (recommended) or Java
   - **Minimum SDK:** The lowest Android version your app will support (e.g., API 21 = Android 5.0)
4. Click **Finish** → Android Studio creates the project structure

### Creating Android Virtual Device (AVD)

**Simply:** An AVD is a fake phone running on your computer — so you can test your app without a real device.

**Technically:**
- Access via: **Tools → AVD Manager** or **Device Manager** in Android Studio
- **Steps to Create AVD:**
  1. Click **Create Virtual Device**
  2. Select Hardware Profile (e.g., Pixel 6)
  3. Select System Image (Android version + API level)
  4. Configure AVD settings (RAM, storage, screen orientation)
  5. Click **Finish**
- **AVD Configuration Files:** Stored in `~/.android/avd/`
- Uses QEMU-based emulator (hardware-accelerated with Intel HAXM or ARM)

### Android Emulator

**Simply:** The emulator is the software that actually runs the fake phone on your screen.

**Technically:**
- The Android Emulator simulates Android devices on your computer
- Based on QEMU (Quick Emulator)
- Supports: Hardware acceleration (via Intel HAXM / AMD-V / ARM translation)
- **Features:**
  - Simulates calls, SMS, GPS location
  - Adjustable network speed (simulate 3G, 4G, Edge)
  - Screen rotation, multi-touch
  - Access to Google Play Store (if Google Play system image used)
- **Extended Controls:** Camera, battery, location, fingerprint simulation
- **ADB (Android Debug Bridge):** Command-line tool to communicate with emulator/device
  ```bash
  adb devices       # list connected devices
  adb install app.apk   # install APK
  adb logcat        # view logs
  ```

# UNIT 3 — Directory Structure, Activities & Intents

## 3.1 Directory Structure of Android Applications

### Overview of Directory Structure

**Simply:** When you create an Android project, Android Studio creates lots of folders and files automatically. Each one has a specific job.

**Technically — Android Project Directory Structure:**

```
MyApp/
├── app/
│   ├── manifests/
│   │   └── AndroidManifest.xml       ← App configuration file
│   ├── java/
│   │   └── com.example.myapp/
│   │       ├── MainActivity.java     ← Main activity (Java/Kotlin code)
│   │       └── (other Java files)
│   ├── res/
│   │   ├── layout/
│   │   │   └── activity_main.xml     ← UI layout of main screen
│   │   ├── values/
│   │   │   ├── strings.xml           ← String resources
│   │   │   ├── colors.xml            ← Color resources
│   │   │   └── themes.xml            ← App theme/styles
│   │   ├── drawable/                 ← Images, icons, shapes
│   │   └── mipmap/                   ← App launcher icons
│   └── build.gradle (Module)         ← Module-level build config
├── build.gradle (Project)            ← Project-level build config
├── settings.gradle                   ← Project settings
└── gradle.properties                 ← Gradle configuration
```

### AndroidManifest.xml

**Simply:** This is the ID card of your app. It tells Android everything it needs to know about your app — name, permissions, which screen to open first.

**Technically:** `AndroidManifest.xml` is the most important configuration file in an Android project. Every Android app **must** have this file. It declares:

- **Application metadata:** Package name, app name, icon, theme
- **Components:** All Activities, Services, Broadcast Receivers, and Content Providers must be declared here
- **Permissions:** Declare permissions the app needs (e.g., INTERNET, CAMERA)
- **Hardware features required** (e.g., camera, GPS)
- **Minimum/Target SDK version**

**Example:**
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp">

    <!-- Permissions -->
    <uses-permission android:name="android.permission.INTERNET" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme">

        <!-- Main Activity -->
        <activity android:name=".MainActivity">
            <intent-filter>
                <!-- This activity is the entry point -->
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>
</manifest>
```

**Key Tags:**
| Tag | Purpose |
|-----|---------|
| `<manifest>` | Root element; contains package name |
| `<uses-permission>` | Declare required permissions |
| `<application>` | App-level settings |
| `<activity>` | Register an activity |
| `<intent-filter>` | Define how component responds to intents |
| `<service>` | Register a service |
| `<receiver>` | Register a broadcast receiver |
| `<provider>` | Register a content provider |

### MainActivity.java

**Simply:** This is the code file for your first/main screen. It's where you write what the app should do when that screen opens.

**Technically:** `MainActivity.java` (or `MainActivity.kt` for Kotlin) is the Java/Kotlin class that represents the main screen (Activity) of the app. It extends `AppCompatActivity` and overrides lifecycle methods.

**Basic Structure:**
```java
package com.example.myapp;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        // Set the layout for this activity
        setContentView(R.layout.activity_main);

        // Access a view by ID
        TextView textView = findViewById(R.id.textView);
        textView.setText("Hello, Android!");
    }
}
```

**Key Points:**
- `extends AppCompatActivity` — provides backward-compatible activity features
- `onCreate()` — called when activity is first created; set layout here
- `setContentView(R.layout.activity_main)` — links this Java file to its XML layout
- `R` class — auto-generated class that maps resource IDs (IDs of views, strings, etc.)
- `findViewById()` — finds a UI element by its ID from the layout XML

### activity_main.xml

**Simply:** This is the design file for your screen. It describes what the screen looks like — where buttons, text, and images are placed.

**Technically:** `activity_main.xml` is an XML layout file stored in `res/layout/`. It defines the visual structure (UI) of the Activity. It uses Android's View hierarchy.

**Basic Example:**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/hello_text"
        android:textSize="18sp" />

    <Button
        android:id="@+id/btnClick"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Click Me" />

</LinearLayout>
```

**Common Attributes:**
| Attribute | Values | Purpose |
|-----------|--------|---------|
| `layout_width` / `layout_height` | `match_parent`, `wrap_content`, fixed dp | Sizing |
| `android:id` | `@+id/name` | Unique identifier (accessible via `R.id.name`) |
| `android:text` | String or `@string/key` | Display text |
| `android:padding` / `android:margin` | dp values | Spacing |

### strings.xml

**Simply:** Instead of writing text directly in the layout, you store all text in this one file — so it's easy to change or translate.

**Technically:** `strings.xml` is stored in `res/values/` and contains all string resources used in the app. This approach is called **externalization of strings** and is essential for:
- **Localization (i18n):** Create `res/values-hi/strings.xml` for Hindi, `res/values-fr/strings.xml` for French
- **Easy maintenance:** Change text in one place
- **Avoid hardcoding**

**Example:**
```xml
<resources>
    <string name="app_name">My App</string>
    <string name="hello_text">Hello, World!</string>
    <string name="btn_label">Click Me</string>
    <string name="error_msg">Something went wrong!</string>
</resources>
```

**Usage in XML layout:**
```xml
android:text="@string/hello_text"
```

**Usage in Java code:**
```java
String appName = getString(R.string.app_name);
```

### values.xml (colors.xml, themes.xml)

**Simply:** This folder holds other design-related values — colors, styles, dimensions — all stored centrally so they're easy to reuse and change.

**Technically:** The `res/values/` directory contains multiple XML resource files:

**colors.xml:**
```xml
<resources>
    <color name="primaryColor">#6200EE</color>
    <color name="primaryDark">#3700B3</color>
    <color name="accent">#03DAC5</color>
    <color name="white">#FFFFFF</color>
</resources>
```

**themes.xml / styles.xml:**
```xml
<resources>
    <style name="AppTheme" parent="Theme.MaterialComponents.DayNight">
        <item name="colorPrimary">@color/primaryColor</item>
        <item name="colorPrimaryVariant">@color/primaryDark</item>
        <item name="colorOnPrimary">@color/white</item>
    </style>
</resources>
```

**dimens.xml:**
```xml
<resources>
    <dimen name="padding_standard">16dp</dimen>
    <dimen name="text_size_normal">14sp</dimen>
</resources>
```

## 3.2 Overview of Activities and Intents

### Activity — States and Life Cycle

**Simply:** An Activity (screen) goes through different stages during its life — just like a phone call: it rings (created), you pick up (starts), you talk (resumes), put on hold (paused), hang up (stopped), call ends (destroyed).

**Technically:** Every Android Activity has a lifecycle managed by the Android OS. The system calls specific callback methods as the activity transitions between states.

#### Activity Lifecycle Diagram:

```
         App launched
              │
              ▼
        ┌────────────┐
        │  onCreate()│  ← Activity created; set layout, init variables
        └─────┬──────┘
              │
              ▼
        ┌───────────┐
        │  onStart()│  ← Activity becoming visible to user
        └─────┬─────┘
              │
              ▼
        ┌────────────┐
        │ onResume() │  ← Activity in foreground, user can interact
        └─────┬──────┘
              │
       ┌──────┴────────┐
       │               │
       ▼               ▼
  ┌──────────┐    ┌──────────────┐
  │onPause() │    │   Running    │  ← Active state
  └────┬─────┘    └──────────────┘
       │
       ▼
  ┌──────────┐
  │ onStop() │  ← Activity no longer visible
  └────┬─────┘
       │
  ┌────┴──────────────┐
  │                   │
  ▼                   ▼
┌──────────────┐  ┌──────────────┐
│ onRestart()  │  │ onDestroy()  │  ← Activity destroyed
└──────┬───────┘  └──────────────┘
       │
       ▼
   onStart() ...
```

#### Lifecycle Callback Methods:

| Method | When Called | What to do |
|--------|-------------|-----------|
| `onCreate()` | Activity first created | Initialize UI, set layout (`setContentView`), bind data |
| `onStart()` | Activity becoming visible | Start animations, register listeners |
| `onResume()` | Activity in foreground (interactive) | Resume paused tasks, start camera/sensors |
| `onPause()` | Another activity comes to foreground | Save data, pause animations, release CPU-intensive resources |
| `onStop()` | Activity no longer visible | Release resources, stop network calls |
| `onRestart()` | Stopped activity coming back | Re-initialize resources |
| `onDestroy()` | Activity being destroyed | Final cleanup, release all resources |

**Exam Important Example — Saving State:**
```java
@Override
protected void onSaveInstanceState(Bundle outState) {
    super.onSaveInstanceState(outState);
    outState.putString("key", "value"); // save data before destruction
}

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    if (savedInstanceState != null) {
        String value = savedInstanceState.getString("key"); // restore data
    }
}
```

### Overview of Intents — Linking Activities

**Simply:** An Intent is like a message you send to Android saying "hey, please open this screen" or "hey, please open the camera app."

**Technically:** An `Intent` is a messaging object used to request an action from another app component. It is the primary mechanism for:
- Starting activities
- Starting services
- Delivering broadcasts

#### Types of Intents:

| Type | Description | Example |
|------|-------------|---------|
| **Explicit Intent** | Specifies the exact component (class) to start | Open a specific Activity within your own app |
| **Implicit Intent** | Declares an action; Android finds a suitable component | Open a URL in browser, share text, take a photo |

#### 1. Explicit Intent (Opening another Activity):
```java
// In MainActivity.java — navigate to SecondActivity
Intent intent = new Intent(MainActivity.this, SecondActivity.class);
startActivity(intent);
```

**Passing data with Intent:**
```java
Intent intent = new Intent(MainActivity.this, SecondActivity.class);
intent.putExtra("username", "Alice");     // pass data
intent.putExtra("score", 95);
startActivity(intent);
```

**Receiving data in SecondActivity:**
```java
String username = getIntent().getStringExtra("username");
int score = getIntent().getIntExtra("score", 0); // 0 is default value
```

#### 2. Implicit Intent (Performing actions):
```java
// Open a URL in browser
Intent intent = new Intent(Intent.ACTION_VIEW);
intent.setData(Uri.parse("https://www.google.com"));
startActivity(intent);

// Make a phone call
Intent intent = new Intent(Intent.ACTION_DIAL);
intent.setData(Uri.parse("tel:+911234567890"));
startActivity(intent);

// Share text
Intent shareIntent = new Intent(Intent.ACTION_SEND);
shareIntent.setType("text/plain");
shareIntent.putExtra(Intent.EXTRA_TEXT, "Check this out!");
startActivity(Intent.createChooser(shareIntent, "Share via"));
```

#### Common Intent Actions:
| Action | Purpose |
|--------|---------|
| `Intent.ACTION_VIEW` | View data (URL, map, etc.) |
| `Intent.ACTION_DIAL` | Open dialer with number |
| `Intent.ACTION_CALL` | Directly make a call (requires permission) |
| `Intent.ACTION_SEND` | Share content |
| `Intent.ACTION_MAIN` | Start as main entry point |
| `MediaStore.ACTION_IMAGE_CAPTURE` | Open camera |

#### Starting Activity and Getting Result (startActivityForResult — legacy / ActivityResultLauncher — modern):
```java
// Modern approach (AndroidX Activity Result API)
ActivityResultLauncher<Intent> launcher = registerForActivityResult(
    new ActivityResultContracts.StartActivityForResult(),
    result -> {
        if (result.getResultCode() == RESULT_OK) {
            Intent data = result.getData();
            // handle result
        }
    }
);

// Launch the intent
launcher.launch(new Intent(this, SecondActivity.class));
```

### Toast for Displaying Messages

**Simply:** A Toast is a small pop-up message that appears on screen for a short time, then disappears automatically — like a notification bubble.

**Technically:** `Toast` is a class in Android that provides simple feedback about an operation in a small popup. It never receives focus and cannot be interacted with. It automatically disappears after a timeout.

**Basic Usage:**
```java
// Short toast (2 seconds)
Toast.makeText(this, "Hello! This is a Toast.", Toast.LENGTH_SHORT).show();

// Long toast (~3.5 seconds)
Toast.makeText(this, "File saved successfully!", Toast.LENGTH_LONG).show();
```

**Syntax Breakdown:**
```java
Toast.makeText(Context, CharSequence message, int duration)
     .show();
```
| Parameter | Description |
|-----------|-------------|
| `Context` | Use `this` (Activity context) or `getApplicationContext()` |
| `message` | The text to display, or `R.string.resource_name` |
| `duration` | `Toast.LENGTH_SHORT` (2s) or `Toast.LENGTH_LONG` (~3.5s) |

**Example — Toast on Button Click:**
```java
Button btn = findViewById(R.id.btnClick);
btn.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        Toast.makeText(MainActivity.this, "Button Clicked!", Toast.LENGTH_SHORT).show();
    }
});
```

**Using Lambda (cleaner syntax):**
```java
btn.setOnClickListener(v -> {
    Toast.makeText(this, "Button Clicked!", Toast.LENGTH_SHORT).show();
});
```

**Key Points about Toast:**
- Does not block UI
- Cannot be dismissed by user (disappears automatically)
- Shown above all other UI elements
- For longer messages or user-interactive notifications, use `Snackbar` or `AlertDialog` instead

# UNIT 4 — Layouts and Views

## 4.1 Layouts

**Simply:** A Layout is a container that decides how UI elements (buttons, text, images) are arranged on screen — like choosing whether to stack things vertically, place them side by side, or position them freely.

**Technically:** In Android, a Layout is a subclass of `ViewGroup` that defines the visual structure of a user interface. Layouts are defined in XML files inside `res/layout/` and can also be created programmatically in Java/Kotlin. Every layout has child `View` elements positioned according to the layout's rules.

All layouts share common attributes:

| Attribute | Values | Purpose |
|-----------|--------|---------|
| `android:layout_width` | `match_parent`, `wrap_content`, fixed dp | Width of the view |
| `android:layout_height` | `match_parent`, `wrap_content`, fixed dp | Height of the view |
| `android:padding` | dp value | Inner spacing (inside the view) |
| `android:layout_margin` | dp value | Outer spacing (outside the view) |
| `android:gravity` | `center`, `left`, `right`, `top`, `bottom` | Aligns content inside the view |
| `android:layout_gravity` | same as above | Aligns the view itself inside its parent |

### Linear Layout

**Simply:** Arranges all children in a single row (horizontal) or a single column (vertical) — one after another, like a list.

**Technically:** `LinearLayout` places child views in a single direction defined by `android:orientation`. It is the simplest and most commonly used layout.

Key attributes:
- `android:orientation` — `horizontal` or `vertical`
- `android:weightSum` — total weight distributed among children
- `android:layout_weight` — how much space a child gets relative to siblings

```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Name:" />

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter your name" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Submit"
        android:layout_gravity="center_horizontal" />
</LinearLayout>
```

**Using layout_weight to divide space equally:**
```xml
<LinearLayout
    android:orientation="horizontal"
    android:weightSum="2"
    android:layout_width="match_parent"
    android:layout_height="wrap_content">

    <Button
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:text="Cancel" />

    <Button
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:text="OK" />
</LinearLayout>
```

**Key Exam Point:** When using `layout_weight`, always set `layout_width="0dp"` (for horizontal) or `layout_height="0dp"` (for vertical) so weight drives the sizing.

### Relative Layout

**Simply:** Each child is positioned relative to other views or to the parent container — like saying "put this button below that text, and align it to the right edge."

**Technically:** `RelativeLayout` lets you specify the position of each child relative to siblings or the parent. It avoids nested layouts and is good for complex UIs.

Key positioning attributes:

| Attribute | Meaning |
|-----------|---------|
| `android:layout_alignParentTop="true"` | Align to top of parent |
| `android:layout_alignParentBottom="true"` | Align to bottom of parent |
| `android:layout_alignParentLeft="true"` | Align to left of parent |
| `android:layout_alignParentRight="true"` | Align to right of parent |
| `android:layout_centerInParent="true"` | Center both horizontally and vertically |
| `android:layout_centerHorizontal="true"` | Center horizontally |
| `android:layout_below="@id/viewId"` | Place below a specific view |
| `android:layout_above="@id/viewId"` | Place above a specific view |
| `android:layout_toRightOf="@id/viewId"` | Place to the right of a view |
| `android:layout_toLeftOf="@id/viewId"` | Place to the left of a view |
| `android:layout_alignTop="@id/viewId"` | Align top edge with another view |

```xml
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/label"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="32dp"
        android:text="Enter Details" />

    <EditText
        android:id="@+id/inputField"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/label"
        android:layout_marginTop="8dp"
        android:hint="Type here..." />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/inputField"
        android:layout_centerHorizontal="true"
        android:text="Submit" />
</RelativeLayout>
```

### Absolute Layout

**Simply:** You place every element at an exact X and Y coordinate on the screen — like drawing on graph paper. Not recommended for modern apps.

**Technically:** `AbsoluteLayout` allows you to specify the exact location (x, y coordinates in dp) of each child view using `android:layout_x` and `android:layout_y`. It is **deprecated** since API level 3 because it does not adapt to different screen sizes or orientations.

```xml
<AbsoluteLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_x="50dp"
        android:layout_y="100dp"
        android:text="Click Me" />
</AbsoluteLayout>
```

**Key Exam Point:** AbsoluteLayout is deprecated and should not be used in new apps. Use ConstraintLayout or RelativeLayout instead.

### Table Layout

**Simply:** Arranges views in rows and columns — exactly like an HTML table.

**Technically:** `TableLayout` is a layout that organizes child views into rows and columns using `<TableRow>` elements. Each `<TableRow>` is one row, and each child inside it is one cell (column).

Key attributes:
- `android:stretchColumns` — which columns should stretch to fill available space (0-indexed)
- `android:shrinkColumns` — which columns can shrink if content overflows
- `android:collapseColumns` — which columns to hide

```xml
<TableLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:stretchColumns="1">

    <TableRow>
        <TextView android:text="Name:" android:padding="8dp" />
        <EditText android:hint="Enter name" android:padding="8dp" />
    </TableRow>

    <TableRow>
        <TextView android:text="Email:" android:padding="8dp" />
        <EditText android:hint="Enter email" android:padding="8dp" />
    </TableRow>

    <TableRow>
        <Button
            android:text="Submit"
            android:layout_span="2"
            android:layout_gravity="center_horizontal" />
    </TableRow>
</TableLayout>
```

**Key attribute:** `android:layout_span="2"` makes a view span across multiple columns.

### Frame Layout

**Simply:** All children are stacked on top of each other — like layers in Photoshop. Usually used to show one view at a time (like swapping fragments).

**Technically:** `FrameLayout` is designed to hold a single child view, but can hold multiple children which are drawn in stack order (last child on top). It is commonly used as a container for `Fragment` transactions.

```xml
<FrameLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- Background image -->
    <ImageView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:src="@drawable/background"
        android:scaleType="centerCrop" />

    <!-- Overlay text on top of image -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:text="Welcome!"
        android:textSize="24sp"
        android:textColor="#FFFFFF" />
</FrameLayout>
```

**Common use — Fragment container:**
```xml
<FrameLayout
    android:id="@+id/fragmentContainer"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```
```java
// Swap fragments programmatically
getSupportFragmentManager()
    .beginTransaction()
    .replace(R.id.fragmentContainer, new MyFragment())
    .commit();
```

### Scroll View

**Simply:** A ScrollView is a container that lets users scroll through content that is too tall (or too wide) to fit on the screen.

**Technically:** `ScrollView` is a layout that provides vertical scrolling for a single child view. For horizontal scrolling, use `HorizontalScrollView`. The child is typically a `LinearLayout` containing multiple views.

**Important constraint:** ScrollView can only have **one direct child**.

```xml
<ScrollView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- ScrollView must have exactly one child -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:padding="16dp">

        <TextView android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Section 1 content..." />

        <TextView android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Section 2 content..." />

        <!-- ...more content that overflows screen height -->
    </LinearLayout>
</ScrollView>
```

**Key attributes:**
- `android:fillViewport="true"` — forces child to expand to at least the screen height
- `android:scrollbars="vertical"` — show/hide scrollbar indicator

**Programmatic scrolling:**
```java
ScrollView scrollView = findViewById(R.id.scrollView);
scrollView.post(() -> scrollView.fullScroll(View.FOCUS_DOWN)); // scroll to bottom
```

## 4.2 Views

**Simply:** A View is any individual UI element on screen — a button, a text field, an image. Layouts hold Views; Views display content or accept input.

**Technically:** `View` is the base class for all UI components in Android. Every visible element on screen is a View. Views are placed inside Layouts (which are themselves subclasses of `ViewGroup`, which extends `View`).

### TextView

**Simply:** Displays text on screen. Read-only by default.

**Technically:** `TextView` is used to display text to the user. It supports styled text, HTML markup, links, and spans.

```xml
<TextView
    android:id="@+id/tvTitle"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello World"
    android:textSize="18sp"
    android:textColor="#000000"
    android:textStyle="bold"
    android:fontFamily="sans-serif-medium" />
```

**Java — setting text programmatically:**
```java
TextView tv = findViewById(R.id.tvTitle);
tv.setText("Updated Text");
tv.setTextColor(Color.RED);
tv.setTextSize(20f);
```

Key attributes:

| Attribute | Purpose |
|-----------|---------|
| `android:text` | The string to display |
| `android:textSize` | Font size in `sp` (scale-independent pixels) |
| `android:textColor` | Hex color code |
| `android:textStyle` | `normal`, `bold`, `italic` |
| `android:maxLines` | Limit display to N lines |
| `android:ellipsize` | Truncation style: `end`, `start`, `middle`, `marquee` |

### EditText

**Simply:** A text box where the user can type — like a form input field.

**Technically:** `EditText` extends `TextView` and adds editing capability. It is used for user text input. The `android:inputType` attribute controls the keyboard type shown.

```xml
<EditText
    android:id="@+id/etName"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Enter your name"
    android:inputType="textPersonName"
    android:maxLength="50" />
```

Common `inputType` values:

| Value | Keyboard Shown |
|-------|---------------|
| `text` | Standard text keyboard |
| `textPassword` | Password (masked input) |
| `textEmailAddress` | Email keyboard (@ key prominent) |
| `number` | Numeric keypad |
| `phone` | Phone dialer keyboard |
| `textMultiLine` | Multi-line text input |
| `date` | Date input |

**Java — reading input:**
```java
EditText etName = findViewById(R.id.etName);
String name = etName.getText().toString().trim();
if (name.isEmpty()) {
    etName.setError("Name cannot be empty");
}
```

### RadioButton and RadioGroup

**Simply:** RadioButtons are options where you can only pick one at a time — like multiple choice questions. RadioGroup ensures only one is selected.

**Technically:** `RadioButton` is a two-state button (checked/unchecked). When placed inside a `RadioGroup`, selecting one automatically deselects all others in the group.

```xml
<RadioGroup
    android:id="@+id/rgGender"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:orientation="vertical">

    <RadioButton
        android:id="@+id/rbMale"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Male" />

    <RadioButton
        android:id="@+id/rbFemale"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Female" />
</RadioGroup>
```

**Java — getting selected RadioButton:**
```java
RadioGroup rg = findViewById(R.id.rgGender);
int selectedId = rg.getCheckedRadioButtonId();

if (selectedId == -1) {
    Toast.makeText(this, "Please select an option", Toast.LENGTH_SHORT).show();
} else {
    RadioButton selected = findViewById(selectedId);
    String gender = selected.getText().toString();
    Toast.makeText(this, "Selected: " + gender, Toast.LENGTH_SHORT).show();
}
```

### CheckBox

**Simply:** A checkbox lets users select or deselect an option independently — unlike RadioButtons, multiple checkboxes can be checked at once.

**Technically:** `CheckBox` is a two-state button that can be independently checked or unchecked. It is used for multiple-selection scenarios.

```xml
<CheckBox
    android:id="@+id/cbTerms"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="I agree to the Terms and Conditions" />

<CheckBox
    android:id="@+id/cbNewsletter"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Subscribe to newsletter"
    android:checked="true" />
```

**Java — checking state:**
```java
CheckBox cbTerms = findViewById(R.id.cbTerms);

if (cbTerms.isChecked()) {
    Toast.makeText(this, "Terms accepted", Toast.LENGTH_SHORT).show();
} else {
    Toast.makeText(this, "Please accept terms", Toast.LENGTH_SHORT).show();
}

// Listener for real-time state change
cbTerms.setOnCheckedChangeListener((buttonView, isChecked) -> {
    if (isChecked) {
        btnSubmit.setEnabled(true);
    } else {
        btnSubmit.setEnabled(false);
    }
});
```

### Button

**Simply:** A tappable element that triggers an action when clicked.

**Technically:** `Button` extends `TextView` and is the primary interaction element for triggering actions. It handles click events via `OnClickListener`.

```xml
<Button
    android:id="@+id/btnLogin"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:text="Login"
    android:backgroundTint="#6200EE"
    android:textColor="#FFFFFF" />
```

**Java — handling click events (3 ways):**

Method 1 — Anonymous inner class:
```java
Button btn = findViewById(R.id.btnLogin);
btn.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        // action here
    }
});
```

Method 2 — Lambda (modern, cleaner):
```java
btn.setOnClickListener(v -> {
    Toast.makeText(this, "Login clicked!", Toast.LENGTH_SHORT).show();
});
```

Method 3 — XML `onClick` attribute:
```xml
<Button android:onClick="onLoginClick" ... />
```
```java
// In MainActivity.java
public void onLoginClick(View v) {
    Toast.makeText(this, "Login clicked!", Toast.LENGTH_SHORT).show();
}
```

### ImageView

**Simply:** Displays an image on screen — from local resources or loaded dynamically.

**Technically:** `ImageView` is used to display images. The image source can be a drawable resource, a bitmap, or a URI. `scaleType` controls how the image is scaled/cropped to fit the view.

```xml
<ImageView
    android:id="@+id/ivProfile"
    android:layout_width="100dp"
    android:layout_height="100dp"
    android:src="@drawable/profile_pic"
    android:scaleType="centerCrop"
    android:contentDescription="Profile photo" />
```

`scaleType` values:

| Value | Behavior |
|-------|----------|
| `center` | Centers image without scaling |
| `centerCrop` | Scales to fill, crops if needed |
| `centerInside` | Scales to fit inside, no cropping |
| `fitXY` | Stretches to fill exactly (may distort) |
| `fitCenter` | Scales proportionally to fit, centered |

**Java — setting image programmatically:**
```java
ImageView iv = findViewById(R.id.ivProfile);
iv.setImageResource(R.drawable.new_image);
// or from a Bitmap:
iv.setImageBitmap(myBitmap);
```

### ImageButton

**Simply:** A Button that shows an image instead of text — like a play button or camera icon button.

**Technically:** `ImageButton` extends `ImageView` and behaves like a `Button` — it is clickable and fires `OnClickListener`. Unlike a regular `Button`, it displays an image instead of text.

```xml
<ImageButton
    android:id="@+id/ibCamera"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/ic_camera"
    android:background="?attr/selectableItemBackgroundBorderless"
    android:contentDescription="Open Camera" />
```

**Java:**
```java
ImageButton ibCamera = findViewById(R.id.ibCamera);
ibCamera.setOnClickListener(v -> {
    Intent intent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
    startActivity(intent);
});
```

**Key Exam Point — TextView vs EditText vs Button vs ImageButton:**

| View | Editable | Clickable | Shows Image |
|------|----------|-----------|-------------|
| TextView | No | No | No |
| EditText | Yes | No | No |
| Button | No | Yes | No (text only) |
| ImageView | No | No | Yes |
| ImageButton | No | Yes | Yes |

# UNIT 5 — Event Handling and Overview of Storage of Data

## 5.1 Event Handling

**Simply:** Events are things that happen when a user interacts with the app — like tapping a button, typing text, or long-pressing an image. Event Handling is the code you write to respond to those interactions.

**Technically:** In Android, the event handling model follows the Observer (Listener) pattern. A `View` generates an event when the user interacts with it. A registered listener interface receives a callback method call when that event occurs.

### Events

**Simply:** An event is any user action or system action that your app needs to respond to.

**Technically:** An event is an occurrence triggered by user interaction or the system. Android provides event types for:

| Event Type | Triggered By |
|------------|-------------|
| Click | Single tap on a view |
| Long Click | Press and hold on a view |
| Touch | Raw touch down/up/move |
| Key | Hardware or soft keyboard key press |
| Focus Change | View gains or loses input focus |
| Text Change | Text in EditText is modified |
| Item Click | Item in a list/grid is tapped |
| Scroll | ScrollView or RecyclerView scrolls |
| Check Changed | CheckBox or RadioButton state changes |

### Event Handlers and Event Listeners

**Simply:** A Listener is an object that "listens" for a specific event. An Event Handler is the method inside the listener that runs when the event happens.

**Technically:**
- **Event Listener** — An interface defined in the `View` class. You implement it to receive callbacks.
- **Event Handler** — The callback method you override inside the listener. It contains your response logic.

The general pattern:
```java
view.setOn[Event]Listener(new View.On[Event]Listener() {
    @Override
    public [returnType] on[Event](View v) {
        // your handler code
    }
});
```

### Event Handling and Listeners

**Simply:** You attach a listener to a view, and when the event happens, Android automatically calls your handler method.

**Technically — Common Listeners and their callbacks:**

#### OnClickListener
Fires when a view is tapped once.
```java
Button btn = findViewById(R.id.btnSubmit);
btn.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        Toast.makeText(MainActivity.this, "Submitted!", Toast.LENGTH_SHORT).show();
    }
});

// Lambda equivalent
btn.setOnClickListener(v -> Toast.makeText(this, "Submitted!", Toast.LENGTH_SHORT).show());
```

#### OnLongClickListener
Fires when a view is pressed and held. Must return `true` to consume the event (prevent click from also firing).
```java
btn.setOnLongClickListener(v -> {
    Toast.makeText(this, "Long pressed!", Toast.LENGTH_SHORT).show();
    return true; // true = event consumed
});
```

#### OnTouchListener
Fires for raw touch events — down, up, move. Useful for drag, swipe, or custom gestures.
```java
imageView.setOnTouchListener((v, event) -> {
    switch (event.getAction()) {
        case MotionEvent.ACTION_DOWN:
            // finger touched screen
            break;
        case MotionEvent.ACTION_MOVE:
            // finger moving
            break;
        case MotionEvent.ACTION_UP:
            // finger lifted
            break;
    }
    return true;
});
```

#### OnFocusChangeListener
Fires when a view gains or loses focus — commonly used on `EditText` for input validation.
```java
EditText etEmail = findViewById(R.id.etEmail);
etEmail.setOnFocusChangeListener((v, hasFocus) -> {
    if (!hasFocus) {
        // user left the field — validate
        String email = etEmail.getText().toString();
        if (!email.contains("@")) {
            etEmail.setError("Invalid email address");
        }
    }
});
```

#### TextWatcher (for EditText)
Fires as the user types — for real-time input monitoring (character count, search filtering, password strength).
```java
EditText etSearch = findViewById(R.id.etSearch);
etSearch.addTextChangedListener(new TextWatcher() {
    @Override
    public void beforeTextChanged(CharSequence s, int start, int count, int after) {
        // called before text changes
    }

    @Override
    public void onTextChanged(CharSequence s, int start, int before, int count) {
        // called as text is changing — use this for live filtering
        filterResults(s.toString());
    }

    @Override
    public void afterTextChanged(Editable s) {
        // called after text has changed
        tvCharCount.setText(s.length() + " / 100");
    }
});
```

#### OnCheckedChangeListener (CheckBox / RadioGroup)
```java
CheckBox cb = findViewById(R.id.cbRemember);
cb.setOnCheckedChangeListener((buttonView, isChecked) -> {
    if (isChecked) {
        savePreference("rememberMe", true);
    }
});

RadioGroup rg = findViewById(R.id.rgOptions);
rg.setOnCheckedChangeListener((group, checkedId) -> {
    RadioButton rb = findViewById(checkedId);
    Toast.makeText(this, "Selected: " + rb.getText(), Toast.LENGTH_SHORT).show();
});
```

### Displaying Messages and Errors using Toast

**Simply:** Toast messages and error indicators are two ways to communicate feedback to the user — one pops up temporarily, the other appears directly on the input field.

**Technically:**

#### Toast (recap from Unit 3 — commonly tested with event handling)
```java
// Show a toast from inside any listener
btn.setOnClickListener(v -> {
    Toast.makeText(MainActivity.this, "Action completed!", Toast.LENGTH_SHORT).show();
});
```

#### setError() on EditText
Displays a red error popup directly on the input field — better UX for form validation than a toast.
```java
EditText etAge = findViewById(R.id.etAge);
String age = etAge.getText().toString().trim();

if (age.isEmpty()) {
    etAge.setError("Age is required");
    etAge.requestFocus(); // move cursor to this field
} else if (Integer.parseInt(age) < 18) {
    etAge.setError("Must be 18 or older");
} else {
    etAge.setError(null); // clear the error
}
```

#### Complete Form Validation Example:
```java
Button btnRegister = findViewById(R.id.btnRegister);
EditText etName = findViewById(R.id.etName);
EditText etEmail = findViewById(R.id.etEmail);
CheckBox cbTerms = findViewById(R.id.cbTerms);

btnRegister.setOnClickListener(v -> {
    String name = etName.getText().toString().trim();
    String email = etEmail.getText().toString().trim();

    if (name.isEmpty()) {
        etName.setError("Name is required");
        etName.requestFocus();
        return;
    }
    if (email.isEmpty() || !email.contains("@")) {
        etEmail.setError("Valid email is required");
        etEmail.requestFocus();
        return;
    }
    if (!cbTerms.isChecked()) {
        Toast.makeText(this, "Please accept the terms", Toast.LENGTH_SHORT).show();
        return;
    }
    Toast.makeText(this, "Registration successful!", Toast.LENGTH_LONG).show();
});
```

## 5.2 Overview of Storage of Data

**Simply:** Android apps often need to save data — user settings, files, or structured records. Android provides four main storage options depending on how much data you need to save and whether it should survive app restarts.

**Technically:** Android offers the following data storage options:

| Storage Option | Best For | Persistent? | Shared with other apps? |
|---------------|----------|-------------|------------------------|
| Shared Preferences | Small key-value data (settings) | Yes | No |
| Internal Storage | Private files | Yes | No |
| External Storage | Large files, media | Yes | Can be (public) |
| SQLite Database | Structured relational data | Yes | No (unless via ContentProvider) |

### Shared Preferences

**Simply:** A small file where you can save settings or simple data as key-value pairs — like saving a username, theme preference, or whether a user is logged in. It survives app restarts.

**Technically:** `SharedPreferences` stores primitive data types (String, int, boolean, float, long) as key-value pairs in an XML file on the device's internal storage. It is ideal for small amounts of configuration data.

**Writing to Shared Preferences:**
```java
// Get SharedPreferences instance
SharedPreferences prefs = getSharedPreferences("MyAppPrefs", Context.MODE_PRIVATE);
// "MyAppPrefs" is the filename; MODE_PRIVATE = only this app can access it

SharedPreferences.Editor editor = prefs.edit();
editor.putString("username", "Alice");
editor.putInt("age", 25);
editor.putBoolean("isLoggedIn", true);
editor.apply(); // apply() is async (preferred); commit() is synchronous
```

**Reading from Shared Preferences:**
```java
SharedPreferences prefs = getSharedPreferences("MyAppPrefs", Context.MODE_PRIVATE);
String username = prefs.getString("username", "Guest"); // "Guest" is default value
int age = prefs.getInt("age", 0);
boolean isLoggedIn = prefs.getBoolean("isLoggedIn", false);

Log.d("Prefs", "Logged in as: " + username);
```

**Removing a value:**
```java
editor.remove("username");
editor.apply();
```

**Clearing all values:**
```java
editor.clear();
editor.apply();
```

**Common use case — remember login state:**
```java
// On login success
editor.putBoolean("isLoggedIn", true);
editor.putString("username", username);
editor.apply();

// On app start — check if already logged in
boolean isLoggedIn = prefs.getBoolean("isLoggedIn", false);
if (isLoggedIn) {
    startActivity(new Intent(this, HomeActivity.class));
    finish(); // prevent going back to login
}
```

### Files — Internal Storage

**Simply:** Internal storage lets your app save files directly on the device that only your app can read. When the app is uninstalled, these files are deleted.

**Technically:** Every app has its own private directory on internal storage at `/data/data/<package_name>/files/`. Files here are not accessible to other apps or the user (unless rooted).

**Writing a file:**
```java
String filename = "notes.txt";
String content = "This is saved data.";

try {
    FileOutputStream fos = openFileOutput(filename, Context.MODE_PRIVATE);
    fos.write(content.getBytes());
    fos.close();
    Toast.makeText(this, "File saved!", Toast.LENGTH_SHORT).show();
} catch (IOException e) {
    e.printStackTrace();
}
```

**Reading a file:**
```java
try {
    FileInputStream fis = openFileInput("notes.txt");
    InputStreamReader isr = new InputStreamReader(fis);
    BufferedReader reader = new BufferedReader(isr);
    StringBuilder sb = new StringBuilder();
    String line;
    while ((line = reader.readLine()) != null) {
        sb.append(line).append("\n");
    }
    fis.close();
    textView.setText(sb.toString());
} catch (IOException e) {
    e.printStackTrace();
}
```

**Listing files in internal storage:**
```java
String[] files = fileList();
for (String file : files) {
    Log.d("Files", file);
}
```

**File modes:**
| Mode | Behavior |
|------|----------|
| `MODE_PRIVATE` | Overwrites existing file; only this app can access |
| `MODE_APPEND` | Appends to existing file instead of overwriting |

### Files — External Storage

**Simply:** External storage is like the public folder on your phone — the SD card or the Downloads/Pictures folders. Anyone with the phone can access these files.

**Technically:** External storage is divided into two types:
- **Public external storage** — accessible to all apps and users (e.g., `Environment.DIRECTORY_PICTURES`)
- **App-specific external storage** — private to the app but stored on external storage (`getExternalFilesDir()`)

**Permissions required (in AndroidManifest.xml):**
```xml
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"
    android:maxSdkVersion="28" /> <!-- Not needed for API 29+ -->
```

**Check if external storage is available:**
```java
String state = Environment.getExternalStorageState();
if (Environment.MEDIA_MOUNTED.equals(state)) {
    // External storage is available and writable
} else if (Environment.MEDIA_MOUNTED_READ_ONLY.equals(state)) {
    // External storage is readable only
}
```

**Writing to app-specific external storage (no permission needed on API 19+):**
```java
File file = new File(getExternalFilesDir(Environment.DIRECTORY_DOCUMENTS), "report.txt");
try {
    FileWriter writer = new FileWriter(file);
    writer.write("Report content here");
    writer.close();
} catch (IOException e) {
    e.printStackTrace();
}
```

**Key Exam Point — Internal vs External Storage:**

| Aspect | Internal Storage | External Storage |
|--------|-----------------|-----------------|
| Access | App only | Can be public or app-specific |
| Permission needed | No | Yes (for public, API < 29) |
| Deleted on uninstall | Yes | App-specific: Yes. Public: No |
| Always available | Yes | No (may be removed/unmounted) |
| Suitable for | Sensitive/private data | Large files, media, shareable data |

### SQLite Database

**Simply:** SQLite is a full database built into every Android device. Use it when you need to store and query structured data — like a list of contacts, products, or scores — with rows and columns.

**Technically:** Android includes `SQLite`, a lightweight relational database engine. Apps interact with it via the `SQLiteOpenHelper` class, which manages database creation and version management, and `SQLiteDatabase` for CRUD operations.

#### Setting up SQLiteOpenHelper:
```java
public class DatabaseHelper extends SQLiteOpenHelper {

    private static final String DATABASE_NAME = "StudentDB";
    private static final int DATABASE_VERSION = 1;

    // Table and column names
    public static final String TABLE_STUDENTS = "students";
    public static final String COL_ID = "id";
    public static final String COL_NAME = "name";
    public static final String COL_MARKS = "marks";

    public DatabaseHelper(Context context) {
        super(context, DATABASE_NAME, null, DATABASE_VERSION);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        // Called once when database is first created
        String CREATE_TABLE = "CREATE TABLE " + TABLE_STUDENTS + " ("
                + COL_ID + " INTEGER PRIMARY KEY AUTOINCREMENT, "
                + COL_NAME + " TEXT NOT NULL, "
                + COL_MARKS + " INTEGER)";
        db.execSQL(CREATE_TABLE);
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        // Called when DATABASE_VERSION changes — handle schema migrations
        db.execSQL("DROP TABLE IF EXISTS " + TABLE_STUDENTS);
        onCreate(db);
    }
}
```

#### Insert (Create):
```java
DatabaseHelper dbHelper = new DatabaseHelper(this);
SQLiteDatabase db = dbHelper.getWritableDatabase();

ContentValues values = new ContentValues();
values.put(DatabaseHelper.COL_NAME, "Alice");
values.put(DatabaseHelper.COL_MARKS, 92);

long rowId = db.insert(DatabaseHelper.TABLE_STUDENTS, null, values);
if (rowId != -1) {
    Toast.makeText(this, "Student added!", Toast.LENGTH_SHORT).show();
}
db.close();
```

#### Read (Query):
```java
SQLiteDatabase db = dbHelper.getReadableDatabase();
Cursor cursor = db.query(
    DatabaseHelper.TABLE_STUDENTS,  // table
    null,                            // all columns
    null,                            // no WHERE clause
    null,
    null, null, null
);

if (cursor.moveToFirst()) {
    do {
        int id = cursor.getInt(cursor.getColumnIndexOrThrow(DatabaseHelper.COL_ID));
        String name = cursor.getString(cursor.getColumnIndexOrThrow(DatabaseHelper.COL_NAME));
        int marks = cursor.getInt(cursor.getColumnIndexOrThrow(DatabaseHelper.COL_MARKS));
        Log.d("DB", id + " - " + name + " - " + marks);
    } while (cursor.moveToNext());
}
cursor.close();
db.close();
```

#### Raw SQL Query:
```java
Cursor cursor = db.rawQuery("SELECT * FROM students WHERE marks > ?", new String[]{"80"});
```

#### Update:
```java
SQLiteDatabase db = dbHelper.getWritableDatabase();
ContentValues values = new ContentValues();
values.put(DatabaseHelper.COL_MARKS, 95);

int rowsUpdated = db.update(
    DatabaseHelper.TABLE_STUDENTS,
    values,
    DatabaseHelper.COL_NAME + " = ?",
    new String[]{"Alice"}
);
db.close();
```

#### Delete:
```java
SQLiteDatabase db = dbHelper.getWritableDatabase();
int rowsDeleted = db.delete(
    DatabaseHelper.TABLE_STUDENTS,
    DatabaseHelper.COL_ID + " = ?",
    new String[]{String.valueOf(studentId)}
);
db.close();
```

**Summary of SQLiteDatabase CRUD methods:**

| Operation | Method | Returns |
|-----------|--------|---------|
| Insert | `db.insert(table, null, contentValues)` | Row ID (-1 if failed) |
| Query | `db.query(...)` or `db.rawQuery(sql, args)` | `Cursor` object |
| Update | `db.update(table, values, whereClause, whereArgs)` | Rows affected |
| Delete | `db.delete(table, whereClause, whereArgs)` | Rows deleted |

**Key Points about Cursor:**
- A `Cursor` is like a pointer that iterates over query results row by row
- `cursor.moveToFirst()` — go to first row (returns false if empty)
- `cursor.moveToNext()` — advance to next row
- `cursor.getColumnIndexOrThrow("columnName")` — get column index safely
- Always call `cursor.close()` and `db.close()` after use to prevent memory leaks

# Quick Revision — Key Exam Points

## Unit 1 Recall
- 4 Types of costs in app development: Development, Platform, Maintenance, App Store fees
- 4 Mobile UI Design principles: Screen real estate, User understanding, Accessibility, Information design
- Accessibility covers: Visual, Hearing, Motor, Cognitive disabilities

## Unit 2 Recall
- Android = Linux-based, open-source, Google
- Andy Rubin founded Android Inc. → Google acquired in 2005
- 4 App Components: **Activity, Service, Broadcast Receiver, Content Provider**
- Architecture (bottom to top): Linux Kernel → Native Libraries → ART → App Framework → Applications
- AVD = Virtual device to test apps on computer

## Unit 3 Recall
- Key files: `AndroidManifest.xml` (config), `MainActivity.java` (logic), `activity_main.xml` (UI), `strings.xml` (text), `values/` (colors, themes)
- Activity Lifecycle: `onCreate → onStart → onResume → onPause → onStop → onDestroy`
- **Explicit Intent** = you know exactly which Activity to open
- **Implicit Intent** = you say what action you want, Android finds the right app
- `Toast.makeText(context, message, duration).show()` — quick temporary message

## Unit 4 Recall
- 6 Layouts: **LinearLayout, RelativeLayout, AbsoluteLayout (deprecated), TableLayout, FrameLayout, ScrollView**
- LinearLayout uses `orientation` (horizontal/vertical); use `layout_weight` to divide space proportionally
- RelativeLayout positions views relative to parent or siblings using alignment attributes
- AbsoluteLayout uses exact x/y coordinates — deprecated, avoid in new apps
- TableLayout uses `<TableRow>` children; `layout_span` lets a view span multiple columns
- FrameLayout stacks children; used as Fragment containers
- ScrollView can only have **one direct child**; wraps a LinearLayout for multiple scrollable views
- 8 Basic Views: **TextView, EditText, RadioButton, RadioGroup, CheckBox, Button, ImageView, ImageButton**

## Unit 5 Recall
- Events are user/system interactions; Listeners are interfaces that respond to them
- Common listeners: `OnClickListener`, `OnLongClickListener`, `OnTouchListener`, `OnFocusChangeListener`, `TextWatcher`, `OnCheckedChangeListener`
- `setError()` on EditText shows inline validation errors; better UX than Toast for forms
- 4 Storage options: **Shared Preferences, Internal Storage, External Storage, SQLite**
- Shared Preferences: key-value pairs; use `editor.apply()` (async) not `commit()` (sync)
- Internal Storage: private to app, always available, deleted on uninstall
- External Storage: may be unavailable (unmounted), requires permissions (below API 29)
- SQLite: `SQLiteOpenHelper` manages DB; CRUD via `insert()`, `query()`, `update()`, `delete()`; `Cursor` iterates results

