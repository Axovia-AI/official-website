# 1-Initial Project Setup
## Feature Title: Project Initialization + CI/CD Foundation

## Purpose
Initialize the Axovia AI website project with core configuration, project structure, and foundational systems to establish a solid architecture for future development.

## Instructions

1. **Create a new Flutter web project** with TypeScript support and proper configuration:
   ```bash
   flutter create --org com.axoviaai --platforms=web axovia_website
   cd axovia_website
   ```

2. **Install required dependencies** in `pubspec.yaml`:
   ```yaml
   dependencies:
     flutter:
       sdk: flutter
     cupertino_icons: ^1.0.2
     # Firebase
     firebase_core: ^2.14.0
     firebase_auth: ^4.7.2
     cloud_firestore: ^4.8.4
     firebase_storage: ^11.2.5
     firebase_analytics: ^10.4.4
     firebase_messaging: ^14.6.5
     # State Management
     flutter_riverpod: ^2.3.6
     # Routing
     go_router: ^10.0.0
     # UI
     google_fonts: ^5.1.0
     responsive_framework: ^1.1.0
     flutter_svg: ^2.0.7
     cached_network_image: ^3.2.3
     url_launcher: ^6.1.12
     # Animation
     animated_text_kit: ^4.2.2
     lottie: ^2.5.0
     # Utils
     logger: ^1.4.0
     shared_preferences: ^2.2.0
     intl: ^0.18.1
     uuid: ^3.0.7
     
   dev_dependencies:
     flutter_test:
       sdk: flutter
     flutter_lints: ^2.0.0
     build_runner: ^2.4.6
     mockito: ^5.4.2
   ```

3. **Set up Firebase integration**:
   - Install Firebase CLI if not already installed
     ```bash
     npm install -g firebase-tools
     ```
   - Log in to Firebase
     ```bash
     firebase login
     ```
   - Initialize Firebase project
     ```bash
     firebase init
     ```
     Select Hosting, Firestore, Functions, Storage, and Authentication
   - Create the Firebase configuration file using FlutterFire CLI
     ```bash
     flutterfire configure
     ```

4. **Create the core project structure** following the defined architecture:
   ```
   lib/
   ├── config/               # Configuration files
   │   ├── app_config.dart   # Global app configuration 
   │   ├── routes.dart       # Route definitions
   │   ├── theme.dart        # Theme configuration
   │   └── constants.dart    # App-wide constants
   ├── core/                 # Core utilities and services
   │   ├── extensions/       # Dart extension methods
   │   ├── services/         # Base services
   │   ├── utils/            # Utility functions
   │   └── error/            # Error handling
   ├── data/                 # Data layer
   │   ├── models/           # Data models
   │   ├── repositories/     # Data repositories
   │   └── providers/        # Data providers
   ├── features/             # Feature modules
   │   ├── home/             # Home page feature
   │   ├── about/            # About page feature
   │   ├── services/         # Services page feature
   │   ├── contact/          # Contact page feature
   │   └── shared/           # Shared feature components
   ├── presentation/         # UI components
   │   ├── layouts/          # Layout templates
   │   ├── widgets/          # Reusable widgets
   │   ├── screens/          # Main screens
   │   └── animations/       # Animation definitions
   ├── routing/              # Navigation system
   │   ├── router.dart       # Router configuration
   │   └── routes.dart       # Route definitions
   ├── firebase/             # Firebase specific code
   │   ├── firebase_options.dart
   │   ├── firestore/        # Firestore utilities
   │   └── auth/             # Authentication utilities
   └── main.dart             # App entry point
   ```

5. **Initialize the basic theme configuration** in `lib/config/theme.dart`:
   - Implement the design system colors, typography, and components
   - Create light and dark theme variants
   - Set up responsive design utilities
   - Define spacing and sizing constants

6. **Configure routing system** with GoRouter in `lib/routing/router.dart`:
   - Set up route definitions for main pages
   - Implement navigation guards for authenticated routes
   - Create error routes and redirection logic
   - Set up URL strategy for clean URLs

7. **Initialize state management** with Riverpod:
   - Create provider scopes in main.dart
   - Set up state management patterns
   - Implement repository providers for data access
   - Create service providers for business logic

8. **Set up responsive layout** with ResponsiveFramework:
   - Configure breakpoints for mobile, tablet, and desktop
   - Create responsive layout components
   - Implement responsive typography scaling
   - Set up container constraints for proper content width

9. **Configure Firebase services**:
   - Set up Firestore rules and indexes
   - Configure Authentication providers
   - Set up Storage security rules
   - Initialize Analytics tracking
   - Configure proper error handling for Firebase services

10. **Create base UI components**:
    - Implement the button variants from the design system
    - Create form input components
    - Build card components with proper styling
    - Implement basic layout grids and containers
    - Create loading indicators and error states

11. **Set up app-wide error handling**:
    - Implement error boundary widgets
    - Create error logging service
    - Set up user-friendly error messages
    - Implement retry mechanisms for network operations
    - Create proper error reporting to external services

12. **Initialize main app structure** in `lib/main.dart`:
    ```dart
    import 'package:flutter/material.dart';
    import 'package:firebase_core/firebase_core.dart';
    import 'package:flutter_riverpod/flutter_riverpod.dart';
    import 'package:responsive_framework/responsive_framework.dart';
    
    import 'firebase/firebase_options.dart';
    import 'config/theme.dart';
    import 'routing/router.dart';
    
    void main() async {
      WidgetsFlutterBinding.ensureInitialized();
      await Firebase.initializeApp(
        options: DefaultFirebaseOptions.currentPlatform,
      );
      
      runApp(
        ProviderScope(
          child: AxoviaApp(),
        ),
      );
    }
    
    class AxoviaApp extends ConsumerWidget {
      @override
      Widget build(BuildContext context, WidgetRef ref) {
        final router = ref.watch(routerProvider);
        
        return MaterialApp.router(
          title: 'Axovia AI',
          theme: AxoviaTheme.lightTheme,
          darkTheme: AxoviaTheme.darkTheme,
          themeMode: ThemeMode.system,
          routerDelegate: router.routerDelegate,
          routeInformationParser: router.routeInformationParser,
          routeInformationProvider: router.routeInformationProvider,
          builder: (context, child) => ResponsiveFramework.builder(
            child!,
            breakpoints: [
              const ResponsiveBreakpoint.resize(450, name: MOBILE),
              const ResponsiveBreakpoint.resize(800, name: TABLET),
              const ResponsiveBreakpoint.resize(1000, name: DESKTOP),
              const ResponsiveBreakpoint.resize(1600, name: 'XL'),
            ],
            minWidth: 350,
            maxWidth: 1600,
            defaultScale: true,
            background: Container(color: Theme.of(context).colorScheme.background),
          ),
          debugShowCheckedModeBanner: false,
        );
      }
    }
    ```

13. **Implement analytics tracking**:
    - Set up Firebase Analytics
    - Create custom event tracking
    - Implement screen tracking with route observers
    - Set up user property tracking
    - Create analytics service for centralized tracking

14. **Configure basic security**:
    - Implement proper Firestore security rules
    - Set up CORS configuration for Storage
    - Configure Authentication security settings
    - Implement secure API access patterns
    - Set up environment variables for sensitive data

15. **Create initial testing setup**:
    - Configure widget tests for core components
    - Set up mocks for Firebase services
    - Create test helpers and utilities
    - Implement basic integration tests
    - Set up CI pipeline configuration

16. **Initialize version control**:
    - Set up proper .gitignore file
    - Create initial commit with project structure
    - Set up branch protection rules
    - Configure GitHub Actions for CI/CD
    - Create pull request template

## Design System Implementation

Implement the design system as defined in `agent/docs/architecture/design-system.md`:

- Create color constants for the brand palette
- Set up typography styles with Google Fonts
- Implement spacing system with consistent values
- Create component themes for all basic UI components
- Set up animation constants and utilities
- Implement responsive design utilities

## Responsive Design

Ensure the project has a solid foundation for responsive design:

- Implement responsive breakpoints for all major device sizes
- Create flexible layouts that adapt to different screen sizes
- Set up proper constraints for content width
- Use responsive spacing that scales with screen size
- Implement conditional rendering for different breakpoints

## Expected Deliverables

1. Fully initialized Flutter web project with proper configuration
2. Complete project structure following the defined architecture
3. Firebase integration with all services configured
4. Routing system with main page routes defined
5. State management setup with Riverpod
6. Theme configuration implementing the design system
7. Basic UI components following the design guidelines
8. Responsive layout system for all screen sizes
9. Error handling and analytics tracking
10. Initial tests for core components

## Next Steps

After completing the initial setup:
1. Mark this task as complete in `agent/planning/implementation-plan.md`
2. Proceed to `2-core-ui-components.md` to implement the main UI structure