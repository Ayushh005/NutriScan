# NutriScan - Food Ingredient Safety Scanner

![NutriScan](https://img.shields.io/badge/Flutter-v3.5-blue?logo=flutter) ![License](https://img.shields.io/badge/License-MIT-green) ![Status](https://img.shields.io/badge/Status-Active-brightgreen)

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Core Components](#core-components)
- [Ingredient Database](#ingredient-database)
- [Theme System](#theme-system)
- [Architecture Patterns](#architecture-patterns)
- [Export & Sharing](#export--sharing)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)

---

## 🎯 Overview

**NutriScan** is a comprehensive Flutter mobile application designed to empower users with instant access to food ingredient safety information. By leveraging advanced optical character recognition (OCR) and a comprehensive ingredient database, NutriScan helps users make informed dietary choices by identifying potentially harmful ingredients in food products.

### Vision
Transform the way consumers engage with food safety information through technology that's accessible, fast, and scientifically-backed.

### Target Users
- Health-conscious consumers
- Parents concerned about children's nutrition
- Individuals with food allergies or sensitivities
- People following specific dietary restrictions

---

## 🌟 Features

### 📱 Core Functionality

#### 1. **Smart Ingredient Scanning**
- Real-time camera integration for ingredient list capture
- Google ML Kit OCR for accurate text extraction from food packaging
- Intelligent text processing and ingredient parsing
- Support for both image selection and direct camera capture

#### 2. **Harmful Ingredient Detection**
- Advanced rule-based matching against a comprehensive database
- Support for ingredient aliases and E-number matching (European classification)
- Intelligent normalization of ingredient names
- Real-time analysis and detection

#### 3. **Risk Assessment System**
- **Four-tier Risk Classification**:
  - 🔴 **High Risk**: Potentially carcinogenic or severely harmful substances
  - 🟠 **Moderate Risk**: Concerning ingredients with documented side effects
  - 🟡 **Caution**: Ingredients that may cause sensitivity in some individuals
  - 🟢 **Safe**: Ingredients with no known harmful effects

#### 4. **Detailed Analysis Reports**
- Comprehensive ingredient information with health impact summaries
- Side effects and associated health risks
- Category classification (Artificial Colors, Preservatives, Sweeteners, etc.)
- Found-in information showing common products containing each ingredient

#### 5. **Professional Export Options**
- **PDF Reports**: Professional-grade, shareable PDF reports with:
  - Executive summary with risk assessment
  - Detailed ingredient cards with health information
  - Methodology and disclaimer sections
  - Beautiful color-coded visualization
- **Text Reports**: Plain text format for quick sharing
- **Direct Sharing**: Seamless integration with device sharing capabilities

#### 6. **Modern User Interface**
- Clean, health-focused design with intuitive navigation
- Material Design 3 compliance for modern Android/iOS feel
- Color-coded risk indicators for quick visual scanning
- Responsive layouts that adapt to different screen sizes
- Smooth animations and transitions

#### 7. **Theme System**
- **Automatic Light/Dark Mode**: Respects system preferences
- **Color Scheme**: Health-focused green accent colors with clear visual hierarchy
- **Consistent Theming**: Unified design language across all screens

### 📺 App Screens

1. **Splash Screen**
  - Elegant animated splash with Lottie animations
  - Smooth navigation to main app
  - App branding and welcome experience

2. **Home Screen**
  - Welcome message and app overview
  - Quick action buttons for scanning
  - Feature highlights
  - Navigation hub to other sections

3. **Scan Screen**
  - Image picker and camera integration
  - Real-time OCR processing with loading indicators
  - Ingredient extraction display
  - Comprehensive results showing detected and harmful ingredients
  - Risk level visualization
  - Share and export functionality

4. **About Screen**
  - App information and mission statement
  - Feature overview
  - Technology stack explanation
  - Contact form for user feedback
  - Input validation for form submissions

5. **Navigation**
  - Bottom navigation bar for quick access
  - Three-tab interface (Home, Scan, About)
  - Visual feedback for active tabs

---

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

```bash
# Required
- Flutter SDK: ^3.5.3 or higher
  (Download from https://flutter.dev/docs/get-started/install)
  
- Dart SDK: Included with Flutter
  
- IDE: Android Studio, VS Code, or IntelliJ IDEA
  
- For Android Development:
  - Android Studio with Android SDK
  - Minimum API Level: 21 (Android 5.0+)
  - Build Tools: Latest stable version
  
- For iOS Development (macOS only):
  - Xcode 12.0 or higher
  - iOS Deployment Target: 11.0 or higher
```

### Installation Steps

#### 1. Clone the Repository
```bash
git clone https://github.com/DAlgoSculptor/NutriScan-App.git
cd NutriScan-App
```

#### 2. Install Dependencies
```bash
# Get all pub dependencies
flutter pub get

# This installs:
# - UI frameworks (Material Design 3)
# - OCR library (Google ML Kit)
# - PDF generation (pdf package)
# - Image processing (image package)
# - State management (provider)
# - And more...
```

#### 3. Generate Required Files
```bash
# Generate code for JSON serialization
flutter pub run build_runner build

# This generates:
# - ingredient.g.dart (JSON serialization)
# - scan_result.g.dart (JSON serialization)
# - Other generated files
```

#### 4. Configure Platform-Specific Settings

**Android Configuration:**
```bash
# Navigate to android directory
cd android

# Build the Gradle wrapper (if needed)
./gradlew build

# Return to project root
cd ..
```

**iOS Configuration (macOS only):**
```bash
# Navigate to iOS directory
cd ios

# Get CocoaPods dependencies
pod install

# Return to project root
cd ..
```

#### 5. Run the Application

```bash
# Run on connected device/emulator
flutter run

# Run in release mode (better performance)
flutter run --release

# Run on specific device
flutter devices  # List available devices
flutter run -d <device_id>
```

#### 6. Build for Distribution (Optional)

```bash
# Android APK
flutter build apk --release

# Android App Bundle
flutter build appbundle --release

# iOS (requires macOS)
flutter build ios --release
```

---

## 📁 Project Structure

```
NutriScan-App/
│
├── android/                          # Android native code and configuration
│   ├── app/src/                     # Android app source
│   ├── build.gradle.kts             # Gradle build configuration
│   └── gradle.properties             # Gradle properties
│
├── ios/                              # iOS native code and configuration
│   ├── Runner/                      # iOS app source
│   ├── Pods/                        # CocoaPods dependencies
│   └── Runner.xcodeproj/            # Xcode project
│
├── lib/                              # Main Dart/Flutter source code
│   ├── main.dart                    # App entry point
│   │
│   ├── screens/                     # App screens
│   │   ├── home_screen.dart         # Home screen UI
│   │   ├── scan_screen.dart         # Scan and analysis screen
│   │   ├── about_screen.dart        # About and contact screen
│   │   └── splash_screen.dart       # Splash/intro screen
│   │
│   ├── models/                      # Data models
│   │   ├── ingredient.dart          # Ingredient model with serialization
│   │   ├── ingredient.g.dart        # Generated serialization code
│   │   ├── scan_result.dart         # Scan result model
│   │   └── scan_result.g.dart       # Generated serialization code
│   │
│   ├── services/                    # Business logic services
│   │   ├── ingredient_database_service.dart  # Ingredient DB management
│   │   ├── scan_service.dart                 # OCR and scanning logic
│   │   └── export_service.dart               # PDF/text export logic
│   │
│   ├── theme/                       # Theming configuration
│   │   └── app_theme.dart           # Light and dark theme definitions
│   │
│   ├── widgets/                     # Reusable UI components
│   │   ├── ingredient_card.dart     # Ingredient display card
│   │   ├── risk_badge.dart          # Risk level badge
│   │   └── [other components]
│   │
│   ├── utils/                       # Utility functions and helpers
│   │   └── [utility files]
│   │
│   └── navigation/                  # Navigation configuration
│       └── main_navigation.dart     # Bottom nav setup
│
├── assets/                           # App assets
│   ├── images/                      # Icons and images
│   │   └── app_icon_design_spec.txt
│   │
│   ├── animations/                  # Lottie animations
│   │   └── splash_animation.json    # Splash screen animation
│   │
│   └── data/                        # Data files
│       └── harmful_ingredients.json # Ingredient database
│
├── test/                             # Unit and widget tests
│   └── widget_test.dart
│
├── build/                            # Build output (generated)
│
├── pubspec.yaml                      # Dart dependencies and configuration
├── analysis_options.yaml             # Lint rules
├── flutter_launcher_icons.yaml       # App icon configuration
├── README.md                         # This file
│
└── [Other configuration files]
    ├── .gitignore
    ├── .gitattributes
    └── [build scripts]
```

---

## 🔧 Core Components

### 1. **Ingredient Model**

The `Ingredient` class represents a harmful ingredient with complete information:

```dart
class Ingredient {
  final String name;              // e.g., "Tartrazine"
  final List<String> aliases;     // e.g., ["E102", "Yellow 5"]
  final String riskLevel;         // "High", "Moderate", "Caution"
  final String category;          // Type of ingredient
  final String description;       // Health impact information
  final List<String> sideEffects; // Associated health risks
  final List<String> foundIn;     // Common products
}
```

### 2. **Scan Result Model**

Encapsulates the results of a scanning operation:

```dart
class ScanResult {
  final DateTime scanTime;
  final List<String> detectedIngredients;      // All found ingredients
  final List<Ingredient> harmfulIngredients;   // Flagged harmful ones
  final String overallRiskLevel;               // Aggregate risk
}
```

### 3. **Ingredient Database Service**

Manages the ingredient database operations:

```dart
// Load harmful ingredients from JSON
static Future<void> loadDatabase()

// Search for harmful ingredients in extracted text
static List<Ingredient> findHarmfulIngredients(List<String> ingredients)

// Get all harmful ingredients
static List<Ingredient> getAllIngredients()

// Check if ingredient is harmful
static bool isHarmful(String ingredientName)
```

### 4. **Export Service**

Handles PDF and text report generation:

```dart
// Generate professional PDF report
static Future<File> generatePDFReport(ScanResult scanResult)

// Generate shareable text report
static String generateTextReport(ScanResult scanResult)

// Share PDF via device sharing
static Future<void> sharePDFReport(ScanResult scanResult)

// Share text via device sharing
static Future<void> shareTextReport(ScanResult scanResult)
```

### 5. **Theme System**

Comprehensive theming configuration with Material Design 3:

```dart
class AppTheme {
  // Color definitions
  static const Color primaryGreen = Color(0xFF4CAF50);
  static const Color darkGreen = Color(0xFF2E7D32);
  
  // Risk level colors
  static const Color highRisk = Color(0xFFFF3333);
  static const Color moderateRisk = Color(0xFFFF9500);
  
  // Theme instances
  static ThemeData lightTheme;  // Light mode theme
  static ThemeData darkTheme;   // Dark mode theme
}
```

---

## 📊 Ingredient Database

### Database Structure

The ingredient database is stored as JSON for portability and easy updates:

```json
{
  "harmful_ingredients": [
    {
      "name": "Tartrazine",
      "aliases": ["E102", "Yellow 5", "FD&C Yellow No. 5"],
      "risk_level": "High",
      "category": "Artificial Color",
      "description": "Synthetic yellow dye that can cause hyperactivity...",
      "side_effects": ["Hyperactivity in children", "Allergic reactions", ...],
      "found_in": ["Candies", "Soft drinks", "Processed foods"]
    },
    // ... more ingredients
  ]
}
```

### Current Database Coverage

#### Ingredient Categories

1. **Artificial Colors** (E-numbers 100-182)
   - Tartrazine (E102)
   - Sunset Yellow FCF (E110)
   - Allura Red AC (E129)
   - Brilliant Blue FCF (E133)
   - And more...

2. **Preservatives** (E-numbers 200-290)
   - Sodium Nitrite (E250)
   - Sodium Nitrate (E251)
   - Sodium Benzoate (E211)
   - And more...

3. **Artificial Sweeteners**
   - Aspartame (E951)
   - Acesulfame Potassium (E950)
   - Sucralose (E955)
   - And more...

4. **Flavor Enhancers**
   - Monosodium Glutamate (MSG/E621)

5. **Other Categories**
   - Antioxidants (BHT, BHA)
   - Trans Fats
   - High Fructose Corn Syrup (HFCS)
   - Carrageenan
   - And more...

### Risk Classification

| Level | Indicator | Meaning |
|-------|-----------|---------|
| **High** | 🔴 Red | Potentially carcinogenic or severely harmful |
| **Moderate** | 🟠 Orange | Documented side effects and health concerns |
| **Caution** | 🟡 Yellow | May cause sensitivity in some individuals |
| **Safe** | 🟢 Green | No known harmful effects |

---

## 🎨 Theme System

### Light Theme
- **Primary Color**: Health-focused green (#4CAF50)
- **Surface**: Clean white background with light gray accents
- **Text**: Dark gray for strong contrast and readability
- **Accent**: Light green for secondary actions

### Dark Theme
- **Primary Color**: Light green (#81C784) for visibility
- **Surface**: Dark backgrounds (#1E1E1E) for reduced eye strain
- **Text**: White text for contrast
- **Cards**: Darker surfaces (#2D2D2D) with subtle borders

### Key Features
- Material Design 3 compliance
- Automatic light/dark mode switching based on system preferences
- Consistent color coding across all components
- Accessible contrast ratios for all text
- Professional card and button styling
- Smooth animations and transitions

---

## 🏗️ Architecture Patterns

### 1. **Model-View-Service Architecture**

The app follows a clean architecture with clear separation of concerns:

```
Screens (UI) ←→ Services (Logic) ←→ Models (Data)
```

### 2. **Service Layer**

All business logic is encapsulated in services:
- `IngredientDatabaseService`: Database operations
- `ScanService`: OCR and text processing
- `ExportService`: Report generation and sharing

### 3. **State Management**

- Uses **Provider** package for state management
- Reactive updates when ingredients are detected
- Efficient rebuilds with provider notifiers

### 4. **Asset Management**

- Centralized asset storage in `assets/` directory
- JSON files for easy data updates
- Lottie animations for engaging UI

---

## 📄 Export & Sharing

### PDF Report Features

The PDF export generates professional reports including:

1. **Header Section**
   - NutriScan branding
   - Report title and generation date

2. **Executive Summary**
   - Overall risk assessment with color coding
   - Key statistics (total ingredients, harmful count)
   - Quick risk overview

3. **Harmful Ingredients Section**
   - Detailed cards for each harmful ingredient
   - Risk level badge
   - Category and description
   - Associated side effects

4. **All Ingredients Section**
   - Comprehensive ingredient list
   - Visual indicators for harmful items
   - Organized display

5. **Methodology Section**
   - Explanation of analysis process
   - Technology used (OCR, database matching)

6. **Disclaimer Section**
   - Important legal and health disclaimers
   - Encouragement to consult professionals

### Text Report Features

- Formatted plain text for quick sharing
- Similar structure to PDF but in text format
- Compatible with all devices and email clients
- Easy to copy and paste

### Sharing Integration

- Uses `share_plus` package for native sharing
- Direct integration with device's share menu
- Support for multiple format options
- Works across Android, iOS, and web platforms

---

## 🔮 Future Enhancements

### Short Term (v1.1 - v1.2)
- [ ] **Enhanced Search**: Full-text search across ingredients
- [ ] **Favorites System**: Save frequently scanned products
- [ ] **Barcode Scanning**: Direct product lookup via barcode
- [ ] **Scan History**: View previous scans and results
- [ ] **Multiple Languages**: Localization for different regions

### Medium Term (v2.0)
- [ ] **Machine Learning Integration**: 
  - Replace rule-based matching with ML models
  - Improved accuracy through deep learning
  - Custom ingredient recognition
- [ ] **User Accounts**: 
  - Cloud sync of scan history
  - Personal preferences and dietary restrictions
  - Health goals tracking
- [ ] **Advanced Analytics**:
  - Weekly/monthly ingredient reports
  - Health trend analysis
  - Personalized recommendations

### Long Term (v3.0+)
- [ ] **Community Features**:
  - User reviews and ratings
  - Crowdsourced ingredient data
  - Social sharing capabilities
- [ ] **Integration Partnerships**:
  - Grocery store partnerships
  - Nutritionist recommendations
  - Health app integrations
- [ ] **Advanced Features**:
  - AR ingredient visualization
  - AI-powered diet planning
  - Real-time nutritional information
- [ ] **Backend Infrastructure**:
  - User authentication system
  - Database synchronization
  - Analytics and reporting

---

## 📚 Technologies Used

### Core Framework
- **Flutter**: v3.5+ - Multiplatform mobile framework
- **Dart**: v3.5.3 - Programming language

### Key Dependencies

**UI & Design**
- `cupertino_icons`: iOS-style icons
- `animated_splash_screen`: Animated splash screens
- `lottie`: JSON animation framework
- `page_transition`: Page transition animations

**State Management**
- `provider`: Reactive state management

**OCR & Image Processing**
- `google_mlkit_text_recognition`: Text recognition from images
- `image_picker`: Camera and gallery access
- `image`: Image processing and manipulation

**Data & Serialization**
- `json_annotation`: JSON serialization metadata
- `json_serializable`: Code generation for JSON

**File & System**
- `path_provider`: System directories access
- `http`: HTTP client for network requests

**PDF & Export**
- `pdf`: PDF document generation
- `share_plus`: Native sharing capabilities

**Development Tools**
- `flutter_lints`: Lint rules
- `build_runner`: Code generation
- `flutter_launcher_icons`: App icon generation

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

### 1. Fork and Clone
```bash
git clone https://github.com/your-username/NutriScan-App.git
```

### 2. Create Feature Branch
```bash
git checkout -b feature/your-feature-name
```

### 3. Make Changes
- Follow Dart style guide
- Ensure code is well-documented
- Test thoroughly

### 4. Commit and Push
```bash
git add .
git commit -m "Add your descriptive commit message"
git push origin feature/your-feature-name
```

### 5. Create Pull Request
- Describe your changes clearly
- Reference any related issues
- Wait for review and feedback

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## ⚠️ Disclaimer

**Important**: NutriScan is a tool for informational purposes only. The information provided should not replace professional medical advice. Always consult with healthcare professionals for personalized dietary recommendations, especially if you have specific health conditions or allergies.

---

## 📞 Contact & Support

For bugs, feature requests, or questions:
- 📧 Email: ayushofficial2323@gmail.com

---

## 🙏 Acknowledgments

- Google ML Kit for OCR technology
- Flutter and Dart teams for the amazing framework
- The open-source community for contributions and feedback

---

**NutriScan** - Empowering Healthier Food Choices Through Technology ✨

*Made with ❤️ using Flutter*

Last Updated: November 2025
