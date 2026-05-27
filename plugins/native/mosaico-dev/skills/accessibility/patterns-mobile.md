# Mobile Accessibility Patterns

Before/after code examples for mobile platforms.
Based on WCAG 2.2 and UK-Brazil Digital Access Programme guide.

Sources:
- Guia de Boas Práticas para Acessibilidade Digital (UK-Brazil Digital Access Programme, 2023)
- WCAG 2.2 — Success Criteria 1.1.1, 1.3.1, 2.4.3, 2.5.3, 2.5.8, 4.1.2
- iOS Human Interface Guidelines — Accessibility
- Android Accessibility — Material Design guidelines
- React Native Accessibility docs
- Flutter Semantics docs

**Touch target minimum:** 24×24 CSS px (WCAG 2.5.8 AA) · 44×44pt recommended (iOS HIG) · 48×48dp recommended (Android Material)

The guide from the UK-Brazil Digital Access Programme highlights that buttons without labels in shopping apps prevent blind users from completing purchases. That same principle applies directly to every icon button, image, and interactive element on mobile.

---

## React Native

React Native exposes accessibility through a set of props that map to TalkBack (Android) and VoiceOver (iOS) under the hood. Without these props, interactive elements are invisible or confusing to screen reader users.

### Screen Reader Labels (TalkBack / VoiceOver)

Icon-only buttons are one of the most common accessibility failures in mobile apps. Without a label, TalkBack announces "unlabelled button" and VoiceOver announces nothing useful.

#### Before

```jsx
// TalkBack says: "unlabelled" — VoiceOver says nothing meaningful
// User has no idea what this button does
<TouchableOpacity onPress={handleDelete}>
  <Image source={icons.trash} style={{ width: 24, height: 24 }} />
</TouchableOpacity>
```

#### After

```jsx
// accessibilityLabel: what the screen reader announces aloud
// accessibilityRole: tells users the interaction type (e.g. "button", "link", "checkbox")
// importantForAccessibility="no": hides the decorative image from the accessibility tree
// so the reader doesn't say "delete item, image, delete item" twice
<TouchableOpacity
  onPress={handleDelete}
  accessibilityLabel="Delete item"
  accessibilityRole="button"
  accessibilityHint="Removes this item from your list permanently"
>
  <Image
    source={icons.trash}
    style={{ width: 24, height: 24 }}
    importantForAccessibility="no"
    accessible={false}
  />
</TouchableOpacity>
```

---

### Touch Targets

WCAG 2.5.8 (AA) requires a minimum 24×24px touch target. iOS HIG and Android Material both recommend 44pt / 48dp. Small touch targets fail users with motor disabilities and older users with reduced dexterity.

#### Before

```jsx
// The icon is 20×20 — too small for users with limited motor control
// No padding to expand the tappable area
const styles = StyleSheet.create({
  icon: {
    width: 20,
    height: 20,
  },
});

<TouchableOpacity onPress={handleSettings} style={styles.icon}>
  <Image source={icons.settings} style={styles.icon} />
</TouchableOpacity>
```

#### After

```jsx
// minWidth/minHeight ensure the tap area is at least 44×44 points
// The icon stays visually 24×24 but the pressable area is larger
// alignItems/justifyContent center the icon inside the larger tap zone
const styles = StyleSheet.create({
  touchTarget: {
    minWidth: 44,
    minHeight: 44,
    alignItems: 'center',
    justifyContent: 'center',
  },
  icon: {
    width: 24,
    height: 24,
  },
});

<TouchableOpacity
  onPress={handleSettings}
  style={styles.touchTarget}
  accessibilityLabel="Open settings"
  accessibilityRole="button"
>
  <Image source={icons.settings} style={styles.icon} accessible={false} />
</TouchableOpacity>
```

---

### Focus Management (React Navigation)

When navigating between screens, screen reader focus stays wherever it was on the previous screen. Users may be disoriented and hear stale content announced instead of the new screen heading.

#### Before

```jsx
// After navigating to ProfileScreen, focus remains on the last element
// the user tapped in HomeScreen — the new screen title is never announced
function ProfileScreen() {
  return (
    <View>
      <Text style={styles.title}>My Profile</Text>
      <Text>Name: Ana Souza</Text>
    </View>
  );
}
```

#### After

```jsx
import React, { useRef, useEffect } from 'react';
import { View, Text, AccessibilityInfo, findNodeHandle } from 'react-native';
import { useFocusEffect } from '@react-navigation/native';

function ProfileScreen() {
  const titleRef = useRef(null);

  useFocusEffect(
    React.useCallback(() => {
      // Wait one frame for the screen to fully mount before moving focus
      const timer = setTimeout(() => {
        if (titleRef.current) {
          // findNodeHandle gets the native node; setAccessibilityFocus moves
          // VoiceOver / TalkBack focus to the screen title
          const node = findNodeHandle(titleRef.current);
          if (node) {
            AccessibilityInfo.setAccessibilityFocus(node);
          }
        }
      }, 100);
      return () => clearTimeout(timer);
    }, [])
  );

  return (
    <View>
      {/* ref lets us target this element for programmatic focus */}
      <Text
        ref={titleRef}
        style={styles.title}
        accessibilityRole="header"
      >
        My Profile
      </Text>
      <Text>Name: Ana Souza</Text>
    </View>
  );
}
```

---

### Form Inputs

TextInput without a visible or programmatic label forces screen reader users to guess the field's purpose. The guide notes that users may fail to complete registration forms due to unlabelled fields.

#### Before

```jsx
// Screen reader announces: "text field" — no indication of what to type
// Placeholder disappears once the user starts typing
<TextInput
  style={styles.input}
  placeholder="Enter your email"
  keyboardType="email-address"
  onChangeText={setEmail}
/>
```

#### After

```jsx
// Option A: Visible label associated via nativeID + accessibilityLabelledBy
// nativeID links the Text label to the TextInput so they are announced together
<View>
  <Text
    nativeID="emailLabel"
    style={styles.label}
  >
    Email address
  </Text>
  <TextInput
    style={styles.input}
    accessibilityLabelledBy="emailLabel"
    // accessibilityLabel as fallback for older React Native versions
    accessibilityLabel="Email address"
    placeholder="you@example.com"
    keyboardType="email-address"
    autoComplete="email"
    textContentType="emailAddress"
    returnKeyType="next"
    onChangeText={setEmail}
  />
</View>

// Option B: No visible label (icon-only design) — use accessibilityLabel directly
<TextInput
  style={styles.input}
  accessibilityLabel="Email address"
  placeholder="you@example.com"
  keyboardType="email-address"
  onChangeText={setEmail}
/>
```

---

### Live Regions

Dynamic content like status messages, counters, or error alerts that appear without screen navigation are invisible to screen reader users unless the element is marked as a live region.

#### Before

```jsx
// The "Item added to cart" message appears visually but TalkBack/VoiceOver
// never announces it — blind users do not know the action succeeded
function CartFeedback({ message }) {
  if (!message) return null;
  return <Text style={styles.feedback}>{message}</Text>;
}
```

#### After

```jsx
// accessibilityLiveRegion="polite" announces when the user is idle — non-interrupting
// Do NOT combine with accessibilityRole="alert": "alert" implies assertive behaviour
// on Android/TalkBack and creates a conflict with "polite". Choose one:
//   - Non-urgent update (cart, status): accessibilityLiveRegion="polite" only
//   - Critical error (auth failure, payment error): accessibilityRole="alert" only
function CartFeedback({ message }) {
  if (!message) return null;
  return (
    <Text
      style={styles.feedback}
      accessibilityLiveRegion="polite"   // polite: waits for user to be idle
      // accessibilityRole omitted — "alert" would override the polite behaviour
    >
      {message}
    </Text>
  );
}
```

---

## Flutter

Flutter uses the `Semantics` widget to expose accessibility information to TalkBack and VoiceOver. Without it, widgets built from low-level primitives are invisible to assistive technology.

### Semantics Widget

A `GestureDetector` with only visual children has no semantic meaning in the accessibility tree. Screen readers skip it or announce nothing.

#### Before

```dart
// GestureDetector has no semantic label — TalkBack says nothing
// The Icon widget has no label either — the trash icon is invisible to screen readers
GestureDetector(
  onTap: handleDelete,
  child: Icon(Icons.delete, size: 24),
)
```

#### After

```dart
// Semantics wraps the widget and adds label, hint, and button role to the a11y tree
// excludeSemantics: true prevents the child Icon from also being announced
// (avoids "Delete item, image, delete item" double-reading)
Semantics(
  label: 'Delete item',
  hint: 'Removes this item permanently from your list',
  button: true,
  excludeSemantics: true, // hides child Icon from the accessibility tree — outer Semantics covers it
  child: GestureDetector(
    onTap: handleDelete,
    child: Icon(
      Icons.delete,
      size: 24,
    ),
  ),
)
```

---

### Touch Targets

Flutter's default icon buttons can be smaller than the recommended 48dp minimum, especially in dense lists. Use `SizedBox` or `constraints` to enforce a minimum tap area.

#### Before

```dart
// The icon is 20px — the tappable area is only as large as the icon itself
// Users with motor impairments frequently mis-tap
IconButton(
  icon: Icon(Icons.share, size: 20),
  onPressed: handleShare,
)
```

#### After

```dart
// IconButton has a built-in minWidth / minHeight via constraints
// Setting 48×48 matches Android Material's recommended touch target size
// The icon remains 24px visually; only the tappable area grows
IconButton(
  icon: Icon(Icons.share, size: 24, semanticLabel: 'Share this item'),
  onPressed: handleShare,
  constraints: const BoxConstraints(
    minWidth: 48,
    minHeight: 48,
  ),
  padding: const EdgeInsets.all(12),
  tooltip: 'Share',
)
```

---

### Screen Reader Labels

Flutter's `Icon` widget accepts a `semanticLabel` parameter. Without it, TalkBack only announces the icon name (which is the Material icon enum key, e.g. "favorite border outline"), which is technical jargon that most users do not understand.

#### Before

```dart
// TalkBack announces: "favorite border outline, button"
// Unclear — is this a like button? A save button? A wishlist toggle?
IconButton(
  icon: const Icon(Icons.favorite_border),
  onPressed: toggleFavorite,
)
```

#### After

```dart
// semanticLabel replaces the internal icon name with a human-readable label
// Tooltip also helps sighted keyboard/switch users
IconButton(
  icon: Icon(
    isFavorited ? Icons.favorite : Icons.favorite_border,
    // Update the label based on state so the screen reader reflects current status
    semanticLabel: isFavorited ? 'Remove from favorites' : 'Add to favorites',
  ),
  tooltip: isFavorited ? 'Remove from favorites' : 'Add to favorites',
  onPressed: toggleFavorite,
)
```

---

### Focus Management

When pushing a new route in Flutter, focus can land on an unpredictable element. Use `FocusScope` or `FocusNode.requestFocus` to move focus to the first meaningful element on the new screen.

#### Before

```dart
// After Navigator.push, TalkBack focus may stay on a back button or nowhere
// The new screen heading "Order Confirmation" is never announced
class OrderConfirmationScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Order Confirmation')),
      body: const Text('Your order has been placed successfully.'),
    );
  }
}
```

#### After

```dart
// FocusNode is attached to the confirmation heading
// requestFocus() is called in initState so focus moves there immediately
class OrderConfirmationScreen extends StatefulWidget {
  @override
  State<OrderConfirmationScreen> createState() => _OrderConfirmationScreenState();
}

class _OrderConfirmationScreenState extends State<OrderConfirmationScreen> {
  final FocusNode _headingFocus = FocusNode();

  @override
  void initState() {
    super.initState();
    // Move focus to the heading after the first frame has rendered
    WidgetsBinding.instance.addPostFrameCallback((_) {
      _headingFocus.requestFocus();
    });
  }

  @override
  void dispose() {
    _headingFocus.dispose(); // always dispose FocusNodes to avoid memory leaks
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: const EdgeInsets.all(24),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            // Focus() widget wraps the heading and routes keyboard/a11y focus here
            Focus(
              focusNode: _headingFocus,
              child: Semantics(
                header: true, // marks this as a heading in the a11y tree
                child: const Text(
                  'Order Confirmed',
                  style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
                ),
              ),
            ),
            const SizedBox(height: 16),
            const Text('Your order has been placed successfully.'),
          ],
        ),
      ),
    );
  }
}
```

---

## iOS (SwiftUI)

SwiftUI exposes accessibility modifiers that map directly to VoiceOver. The `.accessibilityLabel` modifier sets what VoiceOver reads; `.accessibilityHint` provides additional context about what will happen when the user interacts.

### Accessibility Labels and Hints

An icon-only button gives VoiceOver nothing to say. Apple's VoiceOver will attempt to derive a label from the SF Symbol name, but this often produces technical strings like "trash.fill" rather than meaningful descriptions.

#### Before

```swift
// VoiceOver may say "trash.fill, button" — not meaningful to most users
// No hint about what the action will do
Button(action: deleteItem) {
    Image(systemName: "trash.fill")
        .foregroundColor(.red)
}
```

#### After

```swift
// .accessibilityLabel replaces the auto-derived label with human-readable text
// .accessibilityHint tells users WHAT WILL HAPPEN when they activate the button
// Hints should use descriptive (not imperative) form: "Removes..." not "Remove..."
// per Apple Human Interface Guidelines — describe the result, not the command
Button(action: deleteItem) {
    Image(systemName: "trash.fill")
        .foregroundColor(.red)
}
.accessibilityLabel("Delete item")
.accessibilityHint("Permanently removes this item from your list")
// .accessibilityAddTraits is optional here — Button already has .isButton trait
.accessibilityAddTraits(.isDestructiveAction)
```

---

### Touch Targets

By default, a SwiftUI `Button` wraps its content tightly. Small icon buttons may have a tap area well below 44pt, causing frequent mis-taps for users with motor impairments.

#### Before

```swift
// The button tap area is only as large as the 20×20 icon
// Fails both iOS HIG (44×44pt) and WCAG 2.5.8 (24×24 minimum)
Button(action: openMenu) {
    Image(systemName: "ellipsis")
        .frame(width: 20, height: 20)
}
```

#### After

```swift
// .frame sets the minimum size to 44×44pt (iOS HIG recommendation)
// .contentShape(Rectangle()) expands the tappable area to the full frame
// Without contentShape, SwiftUI only registers taps on the image itself
Button(action: openMenu) {
    Image(systemName: "ellipsis")
        .frame(width: 24, height: 24)
}
.frame(minWidth: 44, minHeight: 44)
.contentShape(Rectangle())
.accessibilityLabel("More options")
```

---

### Dynamic Type

Hardcoded font sizes do not scale when the user increases text size in iOS Settings > Accessibility > Display & Text Size. This blocks users with low vision who rely on large text.

#### Before

```swift
// fontSize: 16 is fixed — it ignores the user's preferred text size setting
// Users with low vision who set their phone to Extra Large or Accessibility sizes
// see this text at exactly 16pt, which may be unreadable for them
Text("Welcome back, Ana")
    .font(.system(size: 16))
```

#### After

```swift
// .font(.body) uses Apple's semantic text styles which scale with Dynamic Type
// Users who set Accessibility > Larger Text get proportionally larger text here
// For custom fonts, use .scaledFont(for:) to preserve Dynamic Type scaling
Text("Welcome back, Ana")
    .font(.body)

// If you need a custom font size, use ScaledMetric to scale with Dynamic Type
struct ScaledText: View {
    @ScaledMetric(relativeTo: .body) var fontSize: CGFloat = 16

    var body: some View {
        Text("Welcome back, Ana")
            .font(.system(size: fontSize))
    }
}
```

---

### Focus Management

When a modal or sheet appears, VoiceOver should automatically focus the first interactive element or the modal title. Without explicit management, focus may remain behind the modal on a now-inaccessible element.

#### Before

```swift
// The modal appears but VoiceOver focus stays on the button that triggered it
// Users with VoiceOver enabled cannot interact with the modal without swiping
// through all elements to find it
struct ContentView: View {
    @State private var showingAlert = false

    var body: some View {
        Button("Show Terms") {
            showingAlert = true
        }
        .sheet(isPresented: $showingAlert) {
            TermsView()
        }
    }
}
```

#### After

```swift
// @AccessibilityFocusState moves VoiceOver focus to the modal title
// when the sheet appears — users hear "Terms and Conditions, heading" immediately
struct TermsView: View {
    @AccessibilityFocusState private var isTitleFocused: Bool

    var body: some View {
        VStack(alignment: .leading, spacing: 16) {
            Text("Terms and Conditions")
                .font(.title2)
                .fontWeight(.bold)
                // .accessibilityAddTraits(.isHeader) marks this as a heading
                .accessibilityAddTraits(.isHeader)
                // .accessibilityFocused moves VoiceOver focus here on appear
                .accessibilityFocused($isTitleFocused)

            ScrollView {
                Text("Please read these terms carefully before proceeding.")
            }
        }
        .padding()
        .onAppear {
            // Short delay lets the sheet animation complete before moving focus
            DispatchQueue.main.asyncAfter(deadline: .now() + 0.1) {
                isTitleFocused = true
            }
        }
    }
}
```

---

## Android (Jetpack Compose)

Jetpack Compose maps accessibility to TalkBack via the `semantics` modifier. Content descriptions on interactive elements tell TalkBack what to announce; `mergeDescendants` controls whether a composable is treated as a single focusable unit.

### Content Descriptions

An `Icon` with `contentDescription = null` is explicitly hidden from TalkBack. This is correct for purely decorative icons, but wrong for icons inside interactive elements that have no other label.

#### Before

```kotlin
// contentDescription = null hides the icon from TalkBack
// The surrounding IconButton has no label — TalkBack announces "button, unlabelled"
IconButton(onClick = { handleFavorite() }) {
    Icon(
        imageVector = Icons.Default.FavoriteBorder,
        contentDescription = null
    )
}
```

#### After

```kotlin
// contentDescription on the Icon provides the label for TalkBack
// When the state changes, the contentDescription updates automatically
// so TalkBack announces the current state on the next focus
IconButton(onClick = { handleFavorite() }) {
    Icon(
        imageVector = if (isFavorited) Icons.Default.Favorite else Icons.Default.FavoriteBorder,
        // Reflects the current state so TalkBack always reads accurate info
        contentDescription = if (isFavorited) "Remove from favorites" else "Add to favorites",
        tint = if (isFavorited) Color.Red else Color.Gray
    )
}
```

---

### Touch Targets

Material Design recommends 48×48dp touch targets. Small icon buttons in toolbars or list items often fall below this threshold, creating a motor accessibility barrier.

#### Before

```kotlin
// The IconButton is inside a Row with a fixed height of 32dp
// The tappable area is only 32dp — below the 48dp recommendation
Row(modifier = Modifier.height(32.dp)) {
    IconButton(onClick = { openShare() }) {
        Icon(Icons.Default.Share, contentDescription = "Share")
    }
}
```

#### After

```kotlin
// Modifier.size(48.dp) enforces the minimum touch target size on the IconButton
// The icon inside is 24dp — the remaining space becomes invisible but tappable padding
// This matches WCAG 2.5.8 and Android Material guidelines simultaneously
IconButton(
    onClick = { openShare() },
    modifier = Modifier
        .size(48.dp)            // enforces minimum touch target
        .semantics {
            // Optional: override the role label shown in TalkBack settings
            contentDescription = "Share this item"
        }
) {
    Icon(
        imageVector = Icons.Default.Share,
        contentDescription = "Share this item",
        modifier = Modifier.size(24.dp)  // icon stays visually 24dp
    )
}
```

---

### TalkBack Navigation

Complex composables with multiple nested text and icon elements can create a confusing TalkBack experience where the user has to swipe through every child element individually. Use `mergeDescendants` to group them into a single focusable unit.

#### Before

```kotlin
// TalkBack focuses each child separately:
// 1) "Avatar image" 2) "Ana Souza" 3) "Product Manager" 4) "Message button"
// Four swipes just to understand one list item — overwhelming for screen reader users
Row(modifier = Modifier.padding(16.dp)) {
    Image(
        painter = painterResource(R.drawable.avatar_ana),
        contentDescription = "Avatar image"
    )
    Column {
        Text("Ana Souza")
        Text("Product Manager")
    }
    IconButton(onClick = { sendMessage() }) {
        Icon(Icons.Default.Message, contentDescription = "Message")
    }
}
```

#### After

```kotlin
// semantics { mergeDescendants = true } merges all children into one focus stop
// TalkBack announces everything together: "Ana Souza, Product Manager"
// The action button is separated so it remains individually actionable
Row(
    modifier = Modifier
        .padding(16.dp)
        .semantics(mergeDescendants = true) { }
        // clearAndSetSemantics can be used instead to fully control the announcement
) {
    // Avatar is decorative here — the person's name is already in the Text
    Image(
        painter = painterResource(R.drawable.avatar_ana),
        contentDescription = null  // decorative: name already announced via Text
    )
    Column(modifier = Modifier.weight(1f)) {
        Text("Ana Souza")
        // Role hint added to the subtitle for additional context
        Text(
            text = "Product Manager",
            modifier = Modifier.semantics {
                // Optional: mark as supporting text so TalkBack can deprioritize
            }
        )
    }
    // Keep the action button outside the merged group so it has its own focus stop
    IconButton(onClick = { sendMessage() }) {
        Icon(Icons.Default.Message, contentDescription = "Send message to Ana Souza")
    }
}
```

---

### Dynamic Text Size

Hardcoded `sp` values do not fully respect the user's font scale preference when combined with pixel-based constraints. Use `MaterialTheme.typography` so text inherits the app's type scale, which already accounts for accessibility sizes.

#### Before

```kotlin
// 14.sp is hardcoded — it scales with font size but bypasses the design system
// If the user enables Extra Large fonts in Android Settings, this text
// may overflow its container because the layout was not designed to accommodate scaling
Text(
    text = "Order total: R$ 129,90",
    fontSize = 14.sp,
    fontWeight = FontWeight.Bold
)
```

#### After

```kotlin
// MaterialTheme.typography.bodyMedium uses the design system's type scale
// It scales correctly with the user's font size preference
// and respects both small and Accessibility (very large) sizes
Text(
    text = "Order total: R$ 129,90",
    // bodyMedium corresponds roughly to 14sp but is managed by the theme
    style = MaterialTheme.typography.bodyMedium,
    fontWeight = FontWeight.Bold
)

// If you need to prevent text from being cut off at large font sizes,
// avoid fixed-height containers — use wrapContentHeight() or weight-based layouts
Box(
    modifier = Modifier
        .fillMaxWidth()
        .wrapContentHeight()  // expands vertically instead of clipping text
        .padding(16.dp)
) {
    Text(
        text = "Order total: R$ 129,90",
        style = MaterialTheme.typography.bodyMedium,
        // Allow text to reflow to multiple lines at large font sizes
        // instead of clipping with a single-line constraint
        maxLines = Int.MAX_VALUE
    )
}
```

---

## Quick Reference: Common Mistakes (Mobile)

| Mistake | Platform | Fix |
|---|---|---|
| Icon button with no label | All | Add `accessibilityLabel` (RN) / `semanticLabel` (Flutter) / `.accessibilityLabel` (iOS) / `contentDescription` (Android) |
| Touch target smaller than 24×24 | All | Set `minWidth/minHeight: 44` (RN) / `constraints: BoxConstraints(min 48×48)` (Flutter) / `.frame(minWidth:44, minHeight:44)` (iOS) / `Modifier.size(48.dp)` (Android) |
| New screen focus not moved | All | Use `AccessibilityInfo.setAccessibilityFocus` (RN) / `FocusNode.requestFocus` in `initState` (Flutter) / `@AccessibilityFocusState` on appear (iOS) / `FocusRequester().requestFocus()` in `LaunchedEffect` (Android) |
| Placeholder as only field label | RN / Flutter | Use `accessibilityLabelledBy` (RN) / `Semantics(label:)` wrapping the field (Flutter) |
| `accessibilityRole="alert"` + `accessibilityLiveRegion="polite"` | RN | Remove the role conflict: use one or the other, never both on the same element |
| `Icon(contentDescription = null)` on interactive element | Android | Set a meaningful `contentDescription`; `null` is only correct for purely decorative icons |
| `accessibilityLiveRegion` assumed to work on iOS | RN | This prop has inconsistent VoiceOver support; test on device; prefer `AccessibilityInfo.announceForAccessibility()` for iOS announcements |
| Hardcoded font size (`fontSize: 16`) | iOS / Android | Use `.font(.body)` / semantic TextStyle (iOS) or `MaterialTheme.typography` (Android) to respect Dynamic Type / font scale |
| Missing `excludeSemantics: true` on wrapper | Flutter | When `Semantics` wraps a widget that has its own label, add `excludeSemantics: true` to prevent double-reading |
| Hints in imperative form ("Delete…") | iOS | Use descriptive form per Apple HIG: "Deletes…" / "Removes…" — describe the result, not the command |