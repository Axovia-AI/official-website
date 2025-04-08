# 2-Core UI Components

## Purpose
Implement the essential UI components and layout structures that will serve as the foundation for the Axovia AI website, ensuring consistency, responsive design, and adherence to the design system.

## Instructions

### 1. Navigation Components

#### 1.1 Main Navigation Bar
Create a responsive navigation bar in `lib/presentation/widgets/navigation/main_navbar.dart`:

- Implement a sleek, modern navbar with the following features:
  - Axovia AI logo on the left
  - Primary navigation links in the center or right
  - Mobile hamburger menu for smaller screens
  - Smooth scrolling to sections on the same page
  - Active state for current page/section
  - Optional: Dark mode toggle
  - Optional: Authentication buttons (if logged in/out)

```dart
class MainNavBar extends StatelessWidget {
  final List<NavItem> items;
  final String? currentPath;
  final VoidCallback onMenuToggle;
  
  const MainNavBar({
    Key? key,
    required this.items,
    this.currentPath,
    required this.onMenuToggle,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    final isDesktop = MediaQuery.of(context).size.width >= 1024;
    
    return Container(
      height: 72,
      decoration: BoxDecoration(
        color: Theme.of(context).colorScheme.background,
        boxShadow: [
          BoxShadow(
            color: Colors.black.withOpacity(0.05),
            blurRadius: 10,
            offset: Offset(0, 2),
          ),
        ],
      ),
      padding: EdgeInsets.symmetric(horizontal: 24),
      child: Row(
        mainAxisAlignment: MainAxisAlignment.spaceBetween,
        children: [
          // Logo
          Logo(height: 32),
          
          // Desktop Menu
          if (isDesktop) Expanded(
            child: Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: items.map((item) => NavbarItem(
                label: item.label,
                path: item.path,
                isActive: currentPath == item.path,
                onTap: () => _handleNavigation(context, item),
              )).toList(),
            ),
          ),
          
          // Right side actions
          Row(
            children: [
              if (isDesktop) ThemeToggle(),
              if (isDesktop) SizedBox(width: 16),
              if (isDesktop) 
                PrimaryButton(
                  text: 'Contact Us',
                  onPressed: () => _navigateToContact(context),
                  size: ButtonSize.small,
                ),
              if (!isDesktop)
                IconButton(
                  icon: Icon(Icons.menu),
                  onPressed: onMenuToggle,
                ),
            ],
          ),
        ],
      ),
    );
  }
  
  void _handleNavigation(BuildContext context, NavItem item) {
    // Implementation for navigation
  }
  
  void _navigateToContact(BuildContext context) {
    // Navigate to contact page
  }
}

class NavItem {
  final String label;
  final String path;
  
  NavItem({required this.label, required this.path});
}

class NavbarItem extends StatelessWidget {
  // Implementation of individual navbar item
}
```

#### 1.2 Mobile Navigation Drawer
Create a mobile navigation menu in `lib/presentation/widgets/navigation/mobile_drawer.dart`:

- Implement a sliding drawer for mobile navigation:
  - Full-height menu that slides from the right
  - Same navigation items as the main navbar
  - Additional contact information and social links
  - Elegant animations for opening/closing
  - Close button at the top

```dart
class MobileDrawer extends StatelessWidget {
  final List<NavItem> items;
  final String? currentPath;
  final VoidCallback onClose;
  
  const MobileDrawer({
    Key? key,
    required this.items,
    this.currentPath,
    required this.onClose,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return Drawer(
      child: Container(
        color: Theme.of(context).colorScheme.background,
        child: Column(
          children: [
            // Header with close button
            Container(
              height: 72,
              padding: EdgeInsets.symmetric(horizontal: 24),
              alignment: Alignment.centerRight,
              child: IconButton(
                icon: Icon(Icons.close),
                onPressed: onClose,
              ),
            ),
            
            // Nav items
            Expanded(
              child: ListView(
                padding: EdgeInsets.zero,
                children: [
                  ...items.map((item) => MobileNavItem(
                    label: item.label,
                    path: item.path,
                    isActive: currentPath == item.path,
                    onTap: () => _handleNavigation(context, item),
                  )),
                  
                  Divider(height: 40, thickness: 1),
                  
                  // Contact information and social links
                  Padding(
                    padding: EdgeInsets.all(24),
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text(
                          'Contact Us',
                          style: Theme.of(context).textTheme.titleMedium,
                        ),
                        SizedBox(height: 16),
                        ContactInfo(),
                        SizedBox(height: 24),
                        SocialLinks(),
                      ],
                    ),
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
  
  void _handleNavigation(BuildContext context, NavItem item) {
    // Implementation for navigation
    onClose();
  }
}

class MobileNavItem extends StatelessWidget {
  // Implementation of individual mobile nav item
}
```

#### 1.3 Footer Component
Create a site-wide footer in `lib/presentation/widgets/navigation/footer.dart`:

- Implement a professional footer with:
  - Company logo and tagline
  - Navigation links organized in columns
  - Contact information and location
  - Social media links
  - Copyright and legal information
  - Newsletter signup (optional)
  - Responsive layout for all screen sizes

```dart
class Footer extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      color: Theme.of(context).colorScheme.primary,
      padding: EdgeInsets.symmetric(vertical: 64),
      child: ResponsiveRowColumn(
        rowMainAxisAlignment: MainAxisAlignment.spaceBetween,
        rowCrossAxisAlignment: CrossAxisAlignment.start,
        columnCrossAxisAlignment: CrossAxisAlignment.center,
        columnSpacing: 40,
        rowSpacing: 40,
        layout: ResponsiveWrapper.of(context).isSmallerThan(DESKTOP) 
            ? ResponsiveRowColumnType.COLUMN 
            : ResponsiveRowColumnType.ROW,
        children: [
          // Company info column
          ResponsiveRowColumnItem(
            child: Container(
              width: 300,
              child: Column(
                crossAxisAlignment: ResponsiveWrapper.of(context).isSmallerThan(DESKTOP)
                    ? CrossAxisAlignment.center
                    : CrossAxisAlignment.start,
                children: [
                  Logo(
                    height: 40, 
                    variant: LogoVariant.white,
                  ),
                  SizedBox(height: 16),
                  Text(
                    'Creating intelligent, professional SaaS solutions with AI Agentic Systems',
                    style: Theme.of(context).textTheme.bodyMedium?.copyWith(
                      color: Colors.white.withOpacity(0.8),
                    ),
                  ),
                  SizedBox(height: 24),
                  SocialLinks(color: Colors.white),
                ],
              ),
            ),
          ),
          
          // Services column
          ResponsiveRowColumnItem(
            child: FooterLinksColumn(
              title: 'Services',
              links: [
                FooterLink(title: 'AI Agentic Systems', url: '/services/ai-systems'),
                FooterLink(title: 'Business Software', url: '/services/business-software'),
                FooterLink(title: 'No-Code Solutions', url: '/services/no-code'),
                FooterLink(title: 'Chrome Extensions', url: '/services/extensions'),
              ],
            ),
          ),
          
          // Company column
          ResponsiveRowColumnItem(
            child: FooterLinksColumn(
              title: 'Company',
              links: [
                FooterLink(title: 'About Us', url: '/about'),
                FooterLink(title: 'Case Studies', url: '/case-studies'),
                FooterLink(title: 'Blog', url: '/blog'),
                FooterLink(title: 'Careers', url: '/careers'),
              ],
            ),
          ),
          
          // Contact column
          ResponsiveRowColumnItem(
            child: Container(
              width: 300,
              child: Column(
                crossAxisAlignment: ResponsiveWrapper.of(context).isSmallerThan(DESKTOP)
                    ? CrossAxisAlignment.center
                    : CrossAxisAlignment.start,
                children: [
                  Text(
                    'Contact Us',
                    style: Theme.of(context).textTheme.titleMedium?.copyWith(
                      color: Colors.white,
                    ),
                  ),
                  SizedBox(height: 16),
                  ContactInfo(textColor: Colors.white),
                  SizedBox(height: 24),
                  ContactButton(),
                ],
              ),
            ),
          ),
        ],
      ),
    );
  }
}

class FooterLinksColumn extends StatelessWidget {
  // Implementation of footer links column
}

class FooterLink extends StatelessWidget {
  // Implementation of footer link
}
```

### 2. Layout Components

#### 2.1 Page Scaffold
Create a base page scaffold in `lib/presentation/layouts/page_scaffold.dart`:

- Implement a consistent page layout container:
  - Main navigation at the top
  - Content area in the middle
  - Footer at the bottom
  - Optional: Page loading indicator
  - Optional: Error handling display

```dart
class PageScaffold extends StatelessWidget {
  final Widget child;
  final String? currentPath;
  final bool showFooter;
  final bool showScrollToTop;
  
  const PageScaffold({
    Key? key,
    required this.child,
    this.currentPath,
    this.showFooter = true,
    this.showScrollToTop = true,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Stack(
        children: [
          // Main content
          Column(
            children: [
              // Navigation drawer controller
              MainNavBarController(currentPath: currentPath),
              
              // Page content
              Expanded(
                child: SingleChildScrollView(
                  controller: ScrollController(),
                  child: Column(
                    children: [
                      // Main content
                      child,
                      
                      // Footer
                      if (showFooter) Footer(),
                    ],
                  ),
                ),
              ),
            ],
          ),
          
          // Scroll to top button
          if (showScrollToTop)
            ScrollToTopButton(),
        ],
      ),
    );
  }
}

class MainNavBarController extends StatefulWidget {
  // Implementation of navbar with mobile drawer controller
}

class ScrollToTopButton extends StatefulWidget {
  // Implementation of scroll to top button with animation
}
```

#### 2.2 Section Container
Create a standard section container in `lib/presentation/layouts/section_container.dart`:

- Implement a consistent section layout:
  - Proper padding and margin
  - Content width constraints
  - Background color options
  - Optional decorative elements

```dart
class SectionContainer extends StatelessWidget {
  final Widget child;
  final Color? backgroundColor;
  final EdgeInsetsGeometry? padding;
  final double? topPadding;
  final double? bottomPadding;
  final bool constrainWidth;
  final bool addWave;
  final WavePosition wavePosition;
  
  const SectionContainer({
    Key? key,
    required this.child,
    this.backgroundColor,
    this.padding,
    this.topPadding,
    this.bottomPadding,
    this.constrainWidth = true,
    this.addWave = false,
    this.wavePosition = WavePosition.bottom,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return Container(
      color: backgroundColor ?? Theme.of(context).colorScheme.background,
      padding: EdgeInsets.only(
        top: topPadding ?? 80,
        bottom: bottomPadding ?? 80,
      ),
      child: Stack(
        children: [
          // Main content
          Padding(
            padding: padding ?? EdgeInsets.symmetric(horizontal: 24),
            child: Center(
              child: constrainWidth 
                ? Container(
                    constraints: BoxConstraints(maxWidth: 1280),
                    child: child,
                  )
                : child,
            ),
          ),
          
          // Decorative wave
          if (addWave)
            Positioned(
              top: wavePosition == WavePosition.top ? 0 : null,
              bottom: wavePosition == WavePosition.bottom ? 0 : null,
              left: 0,
              right: 0,
              child: WaveDecoration(position: wavePosition),
            ),
        ],
      ),
    );
  }
}

enum WavePosition { top, bottom }

class WaveDecoration extends StatelessWidget {
  // Implementation of wave decoration SVG
}
```

#### 2.3 Split Section
Create a two-column layout in `lib/presentation/layouts/split_section.dart`:

- Implement a flexible two-column layout:
  - Image on one side, content on the other
  - Responsive behavior (stacks on mobile)
  - Option to switch image/content sides
  - Proper spacing and alignment

```dart
class SplitSection extends StatelessWidget {
  final Widget contentWidget;
  final Widget mediaWidget;
  final bool imageOnRight;
  final double verticalSpacing;
  final CrossAxisAlignment alignment;
  
  const SplitSection({
    Key? key,
    required this.contentWidget,
    required this.mediaWidget,
    this.imageOnRight = true,
    this.verticalSpacing = 48,
    this.alignment = CrossAxisAlignment.center,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    final isDesktop = MediaQuery.of(context).size.width >= 1024;
    
    if (isDesktop) {
      return Row(
        crossAxisAlignment: alignment,
        children: [
          if (!imageOnRight) Expanded(child: mediaWidget),
          if (!imageOnRight) SizedBox(width: 48),
          
          Expanded(child: contentWidget),
          
          if (imageOnRight) SizedBox(width: 48),
          if (imageOnRight) Expanded(child: mediaWidget),
        ],
      );
    } else {
      // Mobile layout (stacked)
      return Column(
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: [
          contentWidget,
          SizedBox(height: verticalSpacing),
          mediaWidget,
        ],
      );
    }
  }
}
```

### 3. Card Components

#### 3.1 Service Card
Create a service display card in `lib/presentation/widgets/cards/service_card.dart`:

- Implement an elegant service card:
  - Clean, modern design with subtle hover effect
  - Icon or image at the top
  - Title and description
  - Optional action button
  - Consistent sizing and padding

```dart
class ServiceCard extends StatefulWidget {
  final String title;
  final String description;
  final IconData? icon;
  final String? imagePath;
  final VoidCallback? onTap;
  
  const ServiceCard({
    Key? key,
    required this.title,
    required this.description,
    this.icon,
    this.imagePath,
    this.onTap,
  }) : super(key: key);
  
  @override
  _ServiceCardState createState() => _ServiceCardState();
}

class _ServiceCardState extends State<ServiceCard> {
  bool isHovered = false;
  
  @override
  Widget build(BuildContext context) {
    return MouseRegion(
      onEnter: (_) => setState(() => isHovered = true),
      onExit: (_) => setState(() => isHovered = false),
      child: GestureDetector(
        onTap: widget.onTap,
        child: AnimatedContainer(
          duration: Duration(milliseconds: 200),
          padding: EdgeInsets.all(24),
          decoration: BoxDecoration(
            color: Theme.of(context).cardTheme.color,
            borderRadius: BorderRadius.circular(12),
            boxShadow: [
              BoxShadow(
                color: Colors.black.withOpacity(isHovered ? 0.1 : 0.05),
                blurRadius: isHovered ? 15 : 10,
                offset: Offset(0, isHovered ? 5 : 2),
              ),
            ],
            transform: isHovered 
                ? Matrix4.translationValues(0, -5, 0)
                : Matrix4.translationValues(0, 0, 0),
          ),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              // Icon or image
              if (widget.icon != null)
                Icon(
                  widget.icon,
                  size: 48,
                  color: Theme.of(context).colorScheme.primary,
                ),
              if (widget.imagePath != null)
                Image.asset(
                  widget.imagePath!,
                  height: 48,
                  width: 48,
                ),
              SizedBox(height: 24),
              
              // Title
              Text(
                widget.title,
                style: Theme.of(context).textTheme.headlineSmall,
              ),
              SizedBox(height: 12),
              
              // Description
              Text(
                widget.description,
                style: Theme.of(context).textTheme.bodyMedium,
              ),
              SizedBox(height: 24),
              
              // Learn more link
              Row(
                mainAxisSize: MainAxisSize.min,
                children: [
                  Text(
                    'Learn more',
                    style: TextStyle(
                      color: Theme.of(context).colorScheme.primary,
                      fontWeight: FontWeight.w600,
                    ),
                  ),
                  SizedBox(width: 8),
                  Icon(
                    Icons.arrow_forward,
                    size: 18,
                    color: Theme.of(context).colorScheme.primary,
                  ),
                ],
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

#### 3.2 Testimonial Card
Create a testimonial display in `lib/presentation/widgets/cards/testimonial_card.dart`:

- Implement an elegant testimonial card:
  - Professional quote styling
  - Client name, position, and company
  - Optional client photo/avatar
  - Rating display (if applicable)
  - Subtle decorative elements

```dart
class TestimonialCard extends StatelessWidget {
  final String quote;
  final String name;
  final String position;
  final String company;
  final String? avatarUrl;
  final int? rating;
  
  const TestimonialCard({
    Key? key,
    required this.quote,
    required this.name,
    required this.position,
    required this.company,
    this.avatarUrl,
    this.rating,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return Container(
      padding: EdgeInsets.all(32),
      decoration: BoxDecoration(
        color: Theme.of(context).cardTheme.color,
        borderRadius: BorderRadius.circular(12),
        boxShadow: [
          BoxShadow(
            color: Colors.black.withOpacity(0.05),
            blurRadius: 15,
            offset: Offset(0, 5),
          ),
        ],
      ),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          // Quote icon
          Icon(
            Icons.format_quote,
            size: 32,
            color: Theme.of(context).colorScheme.primary.withOpacity(0.2),
          ),
          SizedBox(height: 16),
          
          // Quote text
          Text(
            quote,
            style: Theme.of(context).textTheme.bodyLarge?.copyWith(
              fontStyle: FontStyle.italic,
            ),
          ),
          SizedBox(height: 24),
          
          // Rating (if available)
          if (rating != null) ...[
            RatingDisplay(rating: rating!),
            SizedBox(height: 16),
          ],
          
          // Client information
          Row(
            children: [
              // Avatar
              if (avatarUrl != null) ...[
                CircleAvatar(
                  radius: 24,
                  backgroundImage: NetworkImage(avatarUrl!),
                ),
                SizedBox(width: 16),
              ],
              
              // Name and details
              Expanded(
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Text(
                      name,
                      style: Theme.of(context).textTheme.titleMedium,
                    ),
                    SizedBox(height: 4),
                    Text(
                      '$position, $company',
                      style: Theme.of(context).textTheme.bodySmall,
                    ),
                  ],
                ),
              ),
            ],
          ),
        ],
      ),
    );
  }
}

class RatingDisplay extends StatelessWidget {
  // Implementation of star rating display
}
```

#### 3.3 Feature Card
Create a feature highlight card in `lib/presentation/widgets/cards/feature_card.dart`:

- Implement a feature highlight component:
  - Clean design with visual hierarchy
  - Icon or small illustration
  - Feature title and description
  - Consistent sizing and spacing
  - Optional background accent

```dart
class FeatureCard extends StatelessWidget {
  final String title;
  final String description;
  final IconData icon;
  final Color? accentColor;
  
  const FeatureCard({
    Key? key,
    required this.title,
    required this.description,
    required this.icon,
    this.accentColor,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    final color = accentColor ?? Theme.of(context).colorScheme.primary;
    
    return Container(
      padding: EdgeInsets.all(24),
      decoration: BoxDecoration(
        color: Theme.of(context).cardTheme.color,
        borderRadius: BorderRadius.circular(12),
        border: Border.all(
          color: Theme.of(context).dividerColor.withOpacity(0.5),
          width: 1,
        ),
      ),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          // Icon with background
          Container(
            padding: EdgeInsets.all(12),
            decoration: BoxDecoration(
              color: color.withOpacity(0.1),
              borderRadius: BorderRadius.circular(8),
            ),
            child: Icon(
              icon,
              size: 24,
              color: color,
            ),
          ),
          SizedBox(height: 16),
          
          // Title
          Text(
            title,
            style: Theme.of(context).textTheme.titleMedium,
          ),
          SizedBox(height: 8),
          
          // Description
          Text(
            description,
            style: Theme.of(context).textTheme.bodyMedium,
          ),
        ],
      ),
    );
  }
}
```

### 4. Form Components

#### 4.1 Custom Text Field
Create a styled text input in `lib/presentation/widgets/forms/text_field.dart`:

- Implement a custom text field with:
  - Clean, modern styling
  - Label and placeholder text
  - Error message display
  - Focus and hover states
  - Optional leading/trailing icons
  - Support for different input types

```dart
class CustomTextField extends StatelessWidget {
  final String label;
  final String? placeholder;
  final String? errorText;
  final IconData? prefixIcon;
  final IconData? suffixIcon;
  final bool obscureText;
  final TextInputType keyboardType;
  final TextEditingController? controller;
  final Function(String)? onChanged;
  final VoidCallback? onSuffixIconTap;
  
  const CustomTextField({
    Key? key,
    required this.label,
    this.placeholder,
    this.errorText,
    this.prefixIcon,
    this.suffixIcon,
    this.obscureText = false,
    this.keyboardType = TextInputType.text,
    this.controller,
    this.onChanged,
    this.onSuffixIconTap,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        // Label
        Text(
          label,
          style: Theme.of(context).textTheme.bodySmall?.copyWith(
            fontWeight: FontWeight.w500,
          ),
        ),
        SizedBox(height: 8),
        
        // Text field
        TextField(
          controller: controller,
          onChanged: onChanged,
          obscureText: obscureText,
          keyboardType: keyboardType,
          decoration: InputDecoration(
            hintText: placeholder,
            prefixIcon: prefixIcon != null ? Icon(prefixIcon) : null,
            suffixIcon: suffixIcon != null 
                ? GestureDetector(
                    onTap: onSuffixIconTap,
                    child: Icon(suffixIcon),
                  ) 
                : null,
            errorText: errorText,
            border: OutlineInputBorder(
              borderRadius: BorderRadius.circular(8),
              borderSide: BorderSide(
                color: Theme.of(context).dividerColor,
                width: 1,
              ),
            ),
            enabledBorder: OutlineInputBorder(
              borderRadius: BorderRadius.circular(8),
              borderSide: BorderSide(
                color: Theme.of(context).dividerColor,
                width: 1,
              ),
            ),
            focusedBorder: OutlineInputBorder(
              borderRadius: BorderRadius.circular(8),
              borderSide: BorderSide(
                color: Theme.of(context).colorScheme.primary,
                width: 2,
              ),
            ),
            errorBorder: OutlineInputBorder(
              borderRadius: BorderRadius.circular(8),
              borderSide: BorderSide(
                color: Theme.of(context).colorScheme.error,
                width: 1,
              ),
            ),
            focusedErrorBorder: OutlineInputBorder(
              borderRadius: BorderRadius.circular(8),
              borderSide: BorderSide(
                color: Theme.of(context).colorScheme.error,
                width: 2,
              ),
            ),
            filled: true,
            fillColor: Theme.of(context).inputDecorationTheme.fillColor,
            contentPadding: EdgeInsets.all(16),
          ),
        ),
      ],
    );
  }
}
```

#### 4.2 Custom Button
Create button variants in `lib/presentation/widgets/forms/button.dart`:

- Implement customizable button components:
  - Primary, secondary, and text variants
  - Different sizes (large, medium, small)
  - Loading state with spinner
  - Disabled state
  - Icon support (left or right)
  - Hover and press animations

```dart
enum ButtonVariant { primary, secondary, text }
enum ButtonSize { large, medium, small }

class CustomButton extends StatelessWidget {
  final String text;
  final VoidCallback? onPressed;
  final ButtonVariant variant;
  final ButtonSize size;
  final IconData? leftIcon;
  final IconData? rightIcon;
  final bool isLoading;
  final bool fullWidth;
  
  const CustomButton({
    Key? key,
    required this.text,
    this.onPressed,
    this.variant = ButtonVariant.primary,
    this.size = ButtonSize.medium,
    this.leftIcon,
    this.rightIcon,
    this.isLoading = false,
    this.fullWidth = false,
  }) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    // Determine padding based on size
    final EdgeInsetsGeometry padding = size == ButtonSize.large
        ? EdgeInsets.symmetric(horizontal: 32, vertical: 16)
        : size == ButtonSize.medium
            ? EdgeInsets.symmetric(horizontal: 24, vertical: 12)
            : EdgeInsets.symmetric(horizontal: 16, vertical: 8);
    
    // Determine text style
    final TextStyle textStyle = size == ButtonSize.large
        ? Theme.of(context).textTheme.labelLarge!
        : size == ButtonSize.medium
            ? Theme.of(context).textTheme.labelMedium!
            : Theme.of(context).textTheme.labelSmall!;
    
    // Build button based on variant
    Widget buttonChild;
    
    // Loading spinner or content
    if (isLoading) {
      buttonChild = SizedBox(
        height: 20,
        width: 20,
        child: CircularProgressIndicator(
          strokeWidth: 2,
          valueColor: AlwaysStoppedAnimation<Color>(
            variant == ButtonVariant.primary
                ? Colors.white
                : Theme.of(context).colorScheme.primary,
          ),
        ),
      );
    } else {
      buttonChild = Row(
        mainAxisSize: MainAxisSize.min,
        children: [
          if (leftIcon != null) ...[
            Icon(leftIcon, size: size == ButtonSize.small ? 16 : 20),
            SizedBox(width: 8),
          ],
          Text(text),
          if (rightIcon != null) ...[
            SizedBox(width: 8),
            Icon(rightIcon, size: size == ButtonSize.small ? 16 : 20),
          ],
        ],
      );
    }
    
    // Create the appropriate button type
    Widget button;
    
    switch (variant) {
      case ButtonVariant.primary:
        button = ElevatedButton(
          onPressed: isLoading ? null : onPressed,
          style: ElevatedButton.styleFrom(
            padding: padding,
            textStyle: textStyle,
            backgroundColor: Theme.of(context).colorScheme.primary,
            foregroundColor: Colors.white,
          ),
          child: buttonChild,
        );
        break;
        
      case ButtonVariant.secondary:
        button = OutlinedButton(
          onPressed: isLoading ? null : onPressed,
          style: OutlinedButton.styleFrom(
            padding: padding,
            textStyle: textStyle,
            side: BorderSide(
              color: Theme.of(context).colorScheme.primary,
              width: 1,
            ),
          ),
          child: buttonChild,
        );
        break;
        
      case ButtonVariant.text:
        button = TextButton(
          onPressed: isLoading ? null : onPressed,
          style: TextButton.styleFrom(
            padding: padding,
            textStyle: textStyle,
          ),
          child: buttonChild,
        );
        break;
    }
    
    // Apply full width if needed
    if (fullWidth) {
      return SizedBox(
        width: double.infinity,
        child: button,
      );
    }
    
    return button;
  }
}
```

#### 4.3 Contact Form
Create a contact form component in `lib/presentation/widgets/forms/contact_form.dart`:

- Implement a professional contact form:
  - Name, email, phone, and message fields
  - Input validation with error messaging
  - Form submission with loading state
  - Success and error feedback
  - Privacy policy acceptance checkbox
  - Clear, accessible button actions
  - Animation for submission states

**Key Implementation Requirements:**
- Validate all user inputs before submission
- Show appropriate error messages
- Handle loading, success, and error states
- Implement Firebase submission function
- Include proper accessibility attributes
- Maintain consistent spacing and alignment
- Follow the design system for all elements

### 5. Hero Section Components

#### 5.1 Main Hero Section
Create a homepage hero section in `lib/presentation/widgets/sections/hero_section.dart`:

- Implement a striking hero section:
  - Bold heading with animated text
  - Compelling subheading and description
  - Primary and secondary call-to-action buttons
  - Optional: Animated illustration or background
  - Responsive layout for all screen sizes
  - Optional: Subtle scroll indicator

**Key Implementation Requirements:**
- Create attention-grabbing visual hierarchy
- Implement smooth text animation
- Ensure proper containment for long content
- Use responsive text sizing for all devices
- Maintain sufficient contrast for accessibility
- Add subtle animations for visual interest
- Ensure clear call-to-action prominence

#### 5.2 Section Heading Component
Create a reusable section heading in `lib/presentation/widgets/sections/section_heading.dart`:

- Implement a consistent section header:
  - Section title with optional subtitle
  - Optional decorative elements
  - Consistent alignment options
  - Responsive text sizing
  - Proper spacing and margins

**Key Implementation Requirements:**
- Follow typography scale from design system
- Create clear visual hierarchy
- Include animation option for entrance
- Allow for alignment customization
- Maintain consistent spacing between elements
- Include optional eyebrow/overline text
- Support different heading sizes

#### 5.3 Call-to-Action Section
Create a conversion-focused CTA section in `lib/presentation/widgets/sections/cta_section.dart`:

- Implement a compelling call-to-action section:
  - Clear, benefit-focused heading
  - Persuasive supporting text
  - Prominent action button
  - Optional background or decoration
  - High visual contrast for attention

**Key Implementation Requirements:**
- Create high-impact visual design
- Ensure proper spacing for readability
- Use contrasting colors for emphasis
- Implement responsive layout adaptation
- Add subtle hover animations for buttons
- Maintain proper content containment
- Include optional background patterns or illustrations

### 6. Animation Components

#### 6.1 Animated Text
Create animated text components in `lib/presentation/widgets/animations/animated_text.dart`:

- Implement text animation variants:
  - Typing animation
  - Fade-in animation
  - Word replacement animation
  - Character shuffle animation
  - Gradual reveal animation

**Key Implementation Requirements:**
- Create smooth, professional animations
- Allow customization of timing and easing
- Support different text styles
- Ensure accessibility considerations
- Provide option to disable animations
- Create seamless looping options
- Implement pause and continue functionality

#### 6.2 Scroll Animations
Create scroll-triggered animations in `lib/presentation/widgets/animations/scroll_animations.dart`:

- Implement scroll-based animation effects:
  - Fade-in on scroll
  - Slide-in from direction
  - Scale-in effect
  - Staggered group animations
  - Parallax scrolling effect

**Key Implementation Requirements:**
- Create smooth entrance animations
- Implement scroll position detection
- Allow customization of animation parameters
- Support different trigger positions
- Create staggered sequence options
- Ensure fallback for reduced motion settings
- Optimize for performance across devices

#### 6.3 Hover Effects
Create interactive hover effects in `lib/presentation/widgets/animations/hover_effects.dart`:

- Implement subtle hover animations:
  - Elevation change
  - Scale transform
  - Border or glow effect
  - Color transition
  - Content reveal

**Key Implementation Requirements:**
- Create smooth, subtle transitions
- Implement proper cursor changes
- Support touch devices with alternative triggers
- Maintain accessibility for keyboard navigation
- Allow customization of animation parameters
- Create consistent behavior across components
- Ensure proper state management

### 7. UI Utility Components

#### 7.1 Loading Indicators
Create loading state components in `lib/presentation/widgets/utils/loading_indicators.dart`:

- Implement various loading indicators:
  - Circular spinner
  - Linear progress
  - Skeleton loaders
  - Pulsing placeholder
  - Text loading animation

**Key Implementation Requirements:**
- Create smooth, professional animations
- Follow brand color system
- Support different sizes and contexts
- Allow customization of appearance
- Implement accessibility considerations
- Create consistent behavior across application
- Allow text label options

#### 7.2 Error Display
Create error message components in `lib/presentation/widgets/utils/error_display.dart`:

- Implement error display variants:
  - Inline field errors
  - Alert banners
  - Error modals
  - Empty state errors
  - Connection error indicators

**Key Implementation Requirements:**
- Create clear, helpful error messages
- Use appropriate iconography
- Follow accessibility best practices
- Support different severity levels
- Allow for retry or recovery actions
- Implement proper ARIA attributes
- Create consistent styling across application

#### 7.3 Responsive Image
Create an optimized image component in `lib/presentation/widgets/utils/responsive_image.dart`:

- Implement a responsive image handler:
  - Lazy loading support
  - Placeholder/loading state
  - Error fallback
  - Responsive sizing
  - Optional aspect ratio enforcement
  - Image optimization options

**Key Implementation Requirements:**
- Implement efficient loading patterns
- Create smooth placeholder transitions
- Support different image formats
- Allow for styling customization
- Implement proper alt text handling
- Create blur-up loading effect option
- Support WebP and next-gen formats when available

### 8. Interaction Components

#### 8.1 Accordion/FAQ Component
Create expandable content sections in `lib/presentation/widgets/interactions/accordion.dart`:

- Implement accordion functionality:
  - Expand/collapse animation
  - Custom icons for state
  - Grouped or independent sections
  - Proper heading hierarchy
  - Keyboard accessibility

**Key Implementation Requirements:**
- Create smooth expansion animation
- Implement proper ARIA attributes
- Support different content types within
- Allow customization of appearance
- Create consistent behavior across instances
- Support rich content in expanded section
- Implement proper focus management

#### 8.2 Tabs Component
Create tabbed content navigation in `lib/presentation/widgets/interactions/tabs.dart`:

- Implement tabbed interface:
  - Horizontal or vertical tab orientation
  - Active tab indication
  - Smooth content transition
  - Responsive behavior
  - Keyboard navigation

**Key Implementation Requirements:**
- Create consistent tab styling
- Implement animated tab indicator
- Support different content types in panels
- Allow customization of appearance
- Create proper keyboard navigation
- Implement mobile-friendly adaptations
- Support dynamic tab generation

#### 8.3 Modal/Dialog Component
Create overlay dialog components in `lib/presentation/widgets/interactions/modal.dart`:

- Implement modal dialog functionality:
  - Open/close animations
  - Backdrop overlay
  - Close button and escape key handling
  - Different size options
  - Focus trapping for accessibility

**Key Implementation Requirements:**
- Create smooth entrance/exit animations
- Implement backdrop click handling
- Support different content types
- Allow customization of appearance
- Create proper focus management
- Implement stacking for multiple modals
- Support different modal types (alert, form, etc.)

### 9. State Management Integration

#### 9.1 Form State Controller
Implement form state management in `lib/presentation/controllers/form_controller.dart`:

- Create a reusable form controller:
  - Input validation
  - Error tracking
  - Submission handling
  - Loading state management
  - Form reset functionality

**Key Implementation Requirements:**
- Implement with Riverpod providers
- Create consistent validation patterns
- Support asynchronous validation
- Manage loading and error states
- Create submission retry capability
- Implement field dependency handling
- Support form progress tracking

#### 9.2 Theme Controller
Implement theme state management in `lib/presentation/controllers/theme_controller.dart`:

- Create a theme controller:
  - Light/dark mode toggle
  - System preference detection
  - Theme persistence
  - Smooth theme transition
  - Custom theme option support

**Key Implementation Requirements:**
- Implement with Riverpod providers
- Create smooth theme transition animation
- Support system preference detection
- Persist user preference in localStorage
- Create consistent theme application
- Implement proper color scheme generation
- Support accessibility contrast options

#### 9.3 Navigation Controller
Implement navigation state management in `lib/presentation/controllers/navigation_controller.dart`:

- Create a navigation controller:
  - Current route tracking
  - Navigation history
  - Breadcrumb generation
  - Deep linking support
  - Scroll position restoration

**Key Implementation Requirements:**
- Integrate with GoRouter
- Create consistent route handling
- Support route parameters and queries
- Implement navigation guards
- Create proper history management
- Support deep linking patterns
- Implement analytics tracking integration

### 10. Backend Integration Components

#### 10.1 Firebase Auth Hook
Implement authentication integration in `lib/data/hooks/use_auth.dart`:

- Create authentication hook:
  - User state management
  - Login/logout functionality
  - Registration process
  - Password reset
  - Profile management
  - Session persistence

**Key Implementation Requirements:**
- Implement with Riverpod providers
- Create secure authentication flow
- Support multiple sign-in methods
- Manage loading and error states
- Create proper session persistence
- Implement token refresh handling
- Support authentication state listeners

#### 10.2 Firestore Data Hook
Implement database integration in `lib/data/hooks/use_firestore.dart`:

- Create Firestore data hook:
  - Document and collection fetching
  - Real-time updates
  - Pagination support
  - Filtering and sorting
  - Error handling and retry

**Key Implementation Requirements:**
- Implement with Riverpod providers
- Create efficient data fetching patterns
- Support real-time subscription
- Manage loading and error states
- Create proper data caching
- Implement optimistic updates
- Support offline capabilities

#### 10.3 Storage Integration
Implement storage integration in `lib/data/hooks/use_storage.dart`:

- Create storage hook:
  - File upload functionality
  - Download and URL generation
  - Progress tracking
  - File type validation
  - Error handling and retry

**Key Implementation Requirements:**
- Implement with Riverpod providers
- Create efficient upload/download patterns
- Support progress tracking
- Manage loading and error states
- Create proper security rule integration
- Implement retry mechanisms
- Support file type validation

## Design Guidelines

All components must strictly adhere to the Axovia AI design system:

### Visual Consistency
- Use only colors defined in the design system
- Follow typography scale for all text elements
- Maintain consistent spacing using defined spacing scale
- Use correct border radius values from design system
- Apply shadows according to elevation guidelines
- Implement animations with defined duration and easing

### Responsive Design
- Implement mobile-first approach for all components
- Test all components at each defined breakpoint
- Create appropriate layout shifts for different screen sizes
- Use relative units rather than fixed pixels where appropriate
- Ensure touch targets are minimum 44x44px for mobile
- Implement appropriate spacing changes for different devices

### Accessibility
- Ensure WCAG AA compliance for all components
- Implement proper ARIA attributes for interactive elements
- Support keyboard navigation for all interactive components
- Maintain sufficient color contrast (minimum 4.5:1 for text)
- Provide text alternatives for non-text content
- Support screen reader announcements for state changes
- Implement reduced motion alternatives for animations

### Performance
- Optimize component rendering performance
- Implement proper memoization for complex components
- Use efficient state management patterns
- Optimize image and asset loading
- Implement code splitting for large components
- Create optimized build process for production

## Implementation Notes

- All components should be thoroughly documented with comments
- Create comprehensive test coverage for each component
- Implement storybook-style examples for component variants
- Follow naming conventions consistently
- Create reusable patterns rather than duplicating code
- Implement proper error boundaries and fallbacks
- Ensure all animations have completion callbacks

## Next Steps

After completing the core UI components:
1. Mark this task as complete in `agent/planning/implementation-plan.md`
2. Proceed to `3-ui-shell-neumorphism.md` to create the main landing page
