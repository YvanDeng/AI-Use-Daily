# StaryReader iOS Project Module Dependency Analysis Report

**Project**: StaryReader (Dreame)
**Analysis Date**: 2026-04-10
**Project Path**: `/Users/wxjz/Downloads/StaryReader`

---

## 1. Module Structure Overview

### 1.1 Top-Level Modules

| Module | Description | Type |
|--------|-------------|------|
| `Classes/BaseModules/` | Base infrastructure modules (Analytics, Config, CustomView, Utils, etc.) | Objective-C |
| `Classes/BusinessModules/` | Business modules (BookCity, Bookshelf, BookDetails, Reader, Video, etc.) - 54 subdirectories | Objective-C |
| `Classes/CommonModules/` | Shared UI and services (Advert, BookInfo, CommonUI, Login, User, Web, etc.) - 17 subdirectories | Objective-C |
| `Classes/SwiftModules/` | Swift modules following feature-based organization - 35 subdirectories | Swift |
| `Classes/Route/` | Mediator pattern implementation for routing - 9 categories | Objective-C |
| `Classes/Main/` | App entry points (AppDelegate, ApplicationLogicCenter, TabBar, etc.) | Objective-C |
| `HYReaderEngine/` | Reader Engine Framework (Dreame, Ringdom, Starynovel variants) | Framework |
| `ReaderPackage/` | Reader package wrapper | Package |
| `AppLovinQualityService/` | AppLovin quality service | Service |
| `VestHandler/` | Vest handler module | Handler |
| `Vendor/` | Third-party ObjC libraries (SVGAPlayer, TYCyclePagerView, WebViewJavascriptBridge) | Objective-C |

### 1.2 SwiftModules Structure

Swift modules are organized by feature:

| Swift Module | Purpose |
|--------------|---------|
| `Activity/` | Activity/Task related features |
| `Advertisement/` | Advertisement feature |
| `AudioBook/` | Audio book feature |
| `Base/BaseKit/` | Base utilities and UIKit extensions |
| `Base/Interface/` | Shared models and protocols |
| `BookCity/` | Book city feature |
| `Bookshelf/` | Bookshelf feature |
| `Community/` | Community feature |
| `Config/` | Configuration |
| `Core/` | Core functionality |
| `Debug/` | Debug tools |
| `Detail/` | Book detail |
| `LightReader/` | Light reader feature |
| `Login/` | Login feature |
| `Pay/` | Payment feature |
| `PersonalHomepage/` | Personal homepage |
| `ReadHistory/` | Read history |
| `Reader/` | Reader feature |
| `Revenue/` | Revenue feature |
| `Router/` | Router |
| `Search/` | Search feature |
| `Task/` | Task feature |
| `UIComponent/` | UI components |
| `UIServer/` | UI server |
| `Unlock/` | Unlock feature |
| `UserInfo/` | User info |
| `Utils/` | Utilities |
| `VIP/` | VIP feature |
| `VideoCity/` | Video city |
| `Wallet/` | Wallet feature |
| `Web/` | Web feature |

---

## 2. Entry Point Analysis

### 2.1 HYAppDelegate.m

**Path**: `Classes/Main/HYAppDelegate.m`

**Key Dependencies**:
```objc
#import "HYApplicationLogicCenter.h"           // Main application logic
#import "HYApplicationManager.h"                // App management
#import "HYLauncher.h"                          // Launch configuration
#import "HYLicenseAgreeManager.h"               // License agreement
#import "HYMediator+HYRoute.h"                  // Routing
#import "HYUserManager.h"                       // User management
#import "HYUserNotificationCenter.h"            // Push notifications
#import "HYAppsThirdContext.h"                  // Third-party context
#import "HYReadProgressErrorHandler.h"          // Read progress error handling
#import "HYSensorsAnalytics+AppExtension.h"      // Analytics
#import "OCCallSwiftAdapter.h"                  // Swift bridge
#import "HYOfficialPayManager.h"                // Payment
#import "HYPlatformApi.h"                       // Platform API
#import "HYWehearSDKLogicCenter.h"              // Wehear SDK
@import GoogleSignIn;                           // Google Sign-In
```

**Assessment**: Entry point has appropriate dependencies focused on app lifecycle, push notifications, and deep linking. Heavy reliance on `OCCallSwiftAdapter` for Swift interop.

### 2.2 HYApplicationLogicCenter.m

**Path**: `Classes/Main/HYApplicationLogicCenter.m`

**Key Dependencies**:
```objc
#import "HYApplicationScoreLogic.h"            // App scoring
#import <AppsFlyerLib/AppsFlyerLib.h>           // AppsFlyer
#import <FBSDKCoreKit/FBSDKAppLinkUtility.h>   // Facebook
#import <FirebaseCrashlytics/FirebaseCrashlytics.h>  // Firebase
#import <SensorsAnalyticsSDK/SensorsAnalyticsSDK.h>   // Sensors Analytics
#import "HYActivityManager.h"                   // Activity management
#import "HYAdvertHelper.h"                     // Ads
#import "HYBookshelfManager.h"                 // Bookshelf
#import "HYBookReader.h"                       // Reader
#import "HYPayManager.h"                       // Payment
#import "HYTaskManager.h"                      // Task
#import "HYUserManager.h"                       // User
#import "OCCallSwiftAdapter.h"                  // Swift bridge
#import "Dreame-Swift.h"                        // Swift module
```

**Assessment**: Central orchestration layer managing cross-module coordination. Extensive coupling with business modules (Bookshelf, Reader, Task, User).

### 2.3 HYMediator.m

**Path**: `Classes/Route/Mediator/HYMediator.m`

**Key Dependencies**:
```objc
#import "HYMediator.h"
#import <objc/runtime.h>                       // Runtime reflection
```

**Architecture**: Pure routing mediator using runtime reflection to dynamically locate Target-Action pairs:
- Target naming: `HYTarget_<TargetName>`
- Action naming: `HYAction_<ActionName>`
- Supports Swift module routing via `kHYMediatorParamsKeySwiftTargetModuleName`

**Assessment**: Clean dependency structure with no business module imports. Only uses Foundation/ObjC runtime.

---

## 3. Module Dependency Analysis

### 3.1 BaseModules Dependencies

**Submodules**:
- `Analytics/` - Event tracking (SensorsAnalytics, AppsFlyer, Firebase)
- `Config/` - Local and remote configuration
- `CustomView/` - Reusable UI components
- `Log/` - Logging infrastructure
- `Networking/` - Network layer
- `Utils/` - Utilities
- `Mediator/` - (Empty/deprecated)

**Key Dependencies on Other Modules**:
| Import | Files | Purpose |
|--------|-------|---------|
| `OCCallSwiftAdapter.h` | 12 files | Swift bridging for Utils (HYIdentifier, HYClient) |
| `Dreame-Swift.h` | 2 files | Swift interop in Networking (HYNetService) |

**Assessment**: BaseModules has minimal external dependencies. Utils module depends on Swift bridging which creates indirect coupling.

### 3.2 BusinessModules Dependencies

**54 business submodules** including:
- `BookCity/`, `BookDetails/`, `Bookshelf/`, `BookList/`
- `Reader/`, `LightReader/`, `Comics/`
- `Video/`, `ShortVideo/`, `Audio/`
- `Community/`, `Search/`, `Task/`
- `User/`, `My/`, `Login/`
- `Web/`, `Advert/`, `Recharge/`
- `ThirdPlatformModules/`

**Major Cross-Module Dependencies** (verified via import analysis):

| Import | Used By | Purpose |
|--------|---------|---------|
| `HYBookshelfManager.h` | 30+ files | Bookshelf operations (BookDetails, Reader, BookCity, Video, Search) |
| `HYBookCityManager.h` | 20+ files | BookCity operations (BookDetails, LightReader, ShortBook) |
| `HYReaderConfig.h` | 25+ files | Reader configuration (BookDetails, LightReader, ChapterComment) |
| `HYReaderAPI.h` | 15+ files | Reader network API (BookDetails, LightReader, Task) |
| `HYMediator+*.h` | 50+ files | Mediator categories (BookDetails, My, LightReader) |
| `Dreame-Swift.h` | 45+ files | Swift module access |
| `OCCallSwiftAdapter.h` | 150+ files | Swift bridging |

**Assessment**: High coupling between business modules. Bookshelf, BookCity, and Reader are core dependencies used extensively throughout. Mediator pattern is widely adopted but with significant import coupling.

### 3.3 CommonModules Dependencies

**Submodules**:
- `Advert/` - Ad services (Banner, Interstitial, Native, Rewarded)
- `BookInfo/` - Book information models
- `CommonUI/` - Reusable UI components (BookCover, Loading, Guide, PageTab)
- `Login/` - Login UI components
- `Push/` - Push notification handling
- `Recharge/` - Recharge/payment UI
- `User/` - User models and views
- `Web/` - WebView and JS Bridge (CYJSBridge, HYDSBridge)
- `Utils/` - Additional utilities
- `Swift/`, `SwiftUtils/` - Swift utilities
- `Kits/` - Feature kits
- `Database/` - Database operations
- `Player/` - Media player
- `Preload/` - Preloading
- `Proxy/` - Network proxy
- `URLProtocol/` - Custom URL handling
- `WebKit/` - WebKit utilities

**Key Dependencies on Other Modules**:
| Import | Files | Purpose |
|--------|-------|---------|
| `OCCallSwiftAdapter.h` | 15 files | Swift bridging (Login, User, BookInfo, Recharge, Web) |
| `Dreame-Swift.h` | 8 files | Swift interop (UserManager, Web, Advert) |
| `HYMediator+HYLogin.h` | 3 files | Mediator routing |

**Web Module Specific**:
```objc
// dsBridge usage (from Pod)
#import "dsBridge.h"           // HYBridgeLoginApi, HYBridgeTaskApi, HYBridgePayApi, etc.

// WebViewJavascriptBridge (local Vendor)
#import "WKWebViewJavascriptBridge.h"  // CYJSBridge
```

**Assessment**: CommonModules has moderate coupling. Web module uses both dsBridge (CocoaPods) and WebViewJavascriptBridge (Vendor). Login and User modules rely on Swift bridging.

### 3.4 SwiftModules Dependencies

**Swift-ObjC Bridging Mechanism**:

1. **OCCallSwiftAdapter** (`Classes/Main/OCCallSwiftAdapter.h`):
```objc
#ifdef __cplusplus
extern "C" {
#endif
// Swift call adapter header
#import "Dreame-Swift.h"
#ifdef __cplusplus
}
#endif
```

2. **Dreame-Swift.h**: Auto-generated Swift-ObjC bridging header

**Usage Scope**:
- 150+ ObjC files import `OCCallSwiftAdapter.h`
- 45+ ObjC files import `Dreame-Swift.h`

**Swift Module Access from ObjC**:
```objc
#import "Dreame-Swift.h"  // Direct Swift class access
```

**ObjC Access from Swift**:
- Bridging header: `StaryReader-Bridging-Header.h` (400+ lines)
- Imports ObjC classes for Swift consumption

**Assessment**: Extensive ObjC/Swift mixing with OCCallSwiftAdapter as the primary bridge. SwiftModules are accessed from virtually all ObjC business modules.

### 3.5 Route/Mediator Dependencies

**Structure**:
```
Route/
├── Mediator/
│   ├── HYMediator.m           // Core mediator
│   ├── HYMediator+HYRoute.m  // Route category (90KB, largest)
│   ├── HYTarget_Common.m      // Common targets
│   └── HYMediator+HYTransition.m
├── BookCity_Category/
├── BookDetails_Category/
├── Login_Category/
├── Search_Category/
├── Video_Category/
├── Web_Category/
├── WelfareCenter_Category/
└── UserPage_Category/
```

**HYMediator+HYRoute.m Dependencies**:
```objc
#import "HYMediator+HYRoute.h"
#import "HYBookshelfManager.h"
#import "HYBookCityViewController.h"
#import "HYBookCityChannelController.h"
#import "HYBookCityRecommendAllViewController.h"
#import "OCCallSwiftAdapter.h"
#import "Dreame-Swift.h"
```

**Mediator Categories Coupling**:
- `HYMediator+HYBookCity.m` imports: `HYBookCityChannelController`, `HYBookCityChannelModel`
- `HYMediator+HYVideo.m` imports: `HYMediator+HYRoute.h`
- `HYMediator+HYWeb.m` - depends on Web category

**Assessment**: Mediator is a central coupling point. The HYRoute category imports multiple business modules directly, creating a "god class" anti-pattern. 90KB single file indicates potential over-coupling.

---

## 4. ObjC/Swift Mixing Analysis

### 4.1 ObjC -> Swift Calls

**Mechanism**: `Dreame-Swift.h` bridging header

**Files Importing Dreame-Swift.h**:
- Main: `HYAppDelegate.m`, `HYApplicationLogicCenter.m`, `HYStartUIRenderer.m`
- CommonModules: `Advert`, `Login`, `Web`, `User`, `Push`
- BusinessModules: `AppInfo`, `BookDetails`, `BookCity`, `Bookshelf`, `Community`, `LightReader`, `My`, `Reader`, `Task`, `Video`, `ThirdPlatformModules`

**Assessment**: 50+ ObjC files directly call Swift via bridging header. Widespread Swift usage across business logic.

### 4.2 Swift -> ObjC Calls

**Bridging Header Contents** (`StaryReader-Bridging-Header.h`):
- BaseModules: Analytics, Config, CustomView, Log, Utils
- BusinessModules: BookCity, Bookshelf, Reader, Video, Community
- CommonModules: Advert, BookInfo, CommonUI, Login, User, Web
- Main: AppDelegate, ApplicationLogicCenter, TabBarController

**Assessment**: 400+ ObjC classes exposed to Swift. Heavy bidirectional coupling.

### 4.3 OCCallSwiftAdapter Usage

**Scope**: 150+ files across all modules

**Files by Module**:
| Module | Files Count |
|-------|-------------|
| BusinessModules/Reader | 40+ |
| BusinessModules/Bookshelf | 15+ |
| BusinessModules/LightReader | 15+ |
| BusinessModules/BookCity | 10+ |
| BusinessModules/BookDetails | 8+ |
| BusinessModules/ShortBook | 6+ |
| BusinessModules/Audio | 5+ |
| CommonModules/Web | 6+ |
| CommonModules/Advert | 5+ |
| CommonModules/Login | 4+ |
| CommonModules/User | 4+ |
| Route/Mediator | 3+ |
| Main | 8+ |

**Assessment**: Universal adoption of OCCallSwiftAdapter across modules. Creates implicit Swift dependency throughout codebase.

### 4.4 Web Bridge Usage

**dsBridge** (CocoaPods `dsBridge 3.0.6`):
- `Classes/CommonModules/Web/HYDSBridge/BridgeApi/HYBridgeLoginApi.m`
- `Classes/CommonModules/Web/HYDSBridge/BridgeApi/HYBridgeTaskApi.m`
- `Classes/CommonModules/Web/HYDSBridge/BridgeApi/HYBridgePayApi.m`
- `Classes/CommonModules/Web/HYDSBridge/BridgeApi/HYBridgeShareApi.m`
- `Classes/CommonModules/Web/HYDSBridge/BridgeApi/HYBridgeJumpApi.m`
- `Classes/CommonModules/Web/HYDSBridge/BridgeApi/HYBridgeWebViewApi.m`
- `Classes/CommonModules/Web/HYDSBridge/BridgeApi/HYBridgeAlertApi.m`

**WebViewJavascriptBridge** (Vendor `WebViewJavascriptBridge/`):
- `Classes/CommonModules/Web/CYJSBridge.m` - Uses `WKWebViewJavascriptBridge`
- `Classes/Main/StaryReader-Bridging-Header.h` - Imports bridge header
- `Classes/BusinessModules/Wehear/Components/WebView/Handle/WHWebViewHandle.swift` - Swift usage

**Assessment**: Dual bridge strategy - dsBridge for H5-JS communication, WebViewJavascriptBridge as alternative. Web module is isolated but uses two different bridge implementations.

---

## 5. Vendor ObjC Libraries Analysis

### 5.1 Vendor Libraries (Source-Imported)

| Library | Path | Purpose |
|---------|------|---------|
| SVGAPlayer | `Classes/Vendor/SVGAPlayer/` | Animation player |
| TYCyclePagerView | `Classes/Vendor/TYCyclePagerView/` | Cycle pager view |
| WebViewJavascriptBridge | `Classes/Vendor/WebViewJavascriptBridge/` | WebView bridge |
| YYFPSLabel | `Classes/Vendor/YYFPSLabel.h/m` | FPS label |

**Assessment**: Minimal vendor libraries. WebViewJavascriptBridge is source-imported but also available as CocoaPods. Consider using CocoaPods version for easier updates.

### 5.2 CocoaPods Dependencies

**Key Pods** (from `Podfile.lock`):
```ruby
# Networking
AFNetworking 4.0.1

# UI
Masonry 1.1.0
MJRefresh 3.7.9
SDWebImage 5.19.1

# Database
WCDB.swift 2.1.15

# Bridge
dsBridge 3.0.6

# Analytics
SensorsAnalyticsSDK 4.8.2
AppsFlyerFramework 6.14.0
Firebase* 10.x

# Ads
Google-Mobile-Ads-SDK 11.13.0
AppLovinSDK 13.3.0
FBSDKCoreKit 17.0.0
TapjoySDK 13.4.1

# Other
Protobuf 3.26.1
```

**Assessment**: Well-organized CocoaPods dependencies. Major SDKs (Firebase, Ads) properly versioned.

---

## 6. Circular Dependency Analysis

### 6.1 Potential Circular Dependencies Identified

**1. Main <-> BusinessModules**:
```
Main (HYApplicationLogicCenter) -> BusinessModules (HYBookshelfManager, HYBookCityManager)
BusinessModules -> Main (via OCCallSwiftAdapter which imports Dreame-Swift.h which may reference Main)
```

**2. Mediator <-> BusinessModules**:
```
Route/Mediator (HYMediator+HYRoute.m) -> BusinessModules (HYBookCityViewController, HYBookshelfManager)
BusinessModules (BookDetails, BookCity, etc.) -> Route/Mediator (HYMediator+HYLogin.h, HYMediator+HYRoute.h)
```

**3. CommonModules/Web <-> BusinessModules**:
```
CommonModules/Web -> BusinessModules (via Dreame-Swift.h)
BusinessModules (BookDetails, Bookshelf) -> CommonModules/Web (HYBridgeLoginApi, HYBridgePayApi)
```

**4. BusinessModules/BookDetails <-> BusinessModules/BookCity**:
```
BookDetails -> BookCity (HYBookCityPersonalBookModel, HYBookCityGetAllModel)
BookCity -> BookDetails (potential via Mediator)
```

**5. BusinessModules/Bookshelf <-> BusinessModules/LightReader**:
```
Bookshelf -> LightReader (via Mediator)
LightReader -> Bookshelf (HYBookshelfManager)
```

### 6.2 Circular Dependency Risk Assessment

| Dependency Pair | Risk Level | Notes |
|-----------------|------------|-------|
| Main <-> BusinessModules | Medium | ApplicationLogicCenter orchestrates all modules |
| Mediator <-> BusinessModules | High | Central routing imports business modules directly |
| BookDetails <-> BookCity | Medium | Data models shared, Mediator breaks direct coupling |
| Web <-> BusinessModules | Low | Well-isolated via bridges |

**Assessment**: Mediator pattern creates hub-and-spoke coupling. Central mediator depends on all business modules. This is a known trade-off of the mediator pattern but creates a fragile central point.

---

## 7. Module Boundary Evaluation

### 7.1 Oversized Modules

| Module | Issue | Recommendation |
|--------|-------|----------------|
| `HYMediator+HYRoute.m` | 90KB single file, imports 10+ business modules | Split by feature (HYRoute+BookCity, HYRoute+BookDetails, etc.) |
| `BusinessModules/Reader/` | 40+ subdirectories, 150+ files | Consider splitting into ReaderCore, ReaderMenu, ReaderReport |
| `CommonModules/Web/` | Mixes CYJSBridge, HYDSBridge, HYTarget_Web | Split into WebView and BridgeApi modules |

### 7.2 Vague Responsibility Modules

| Module | Issue | Notes |
|--------|-------|-------|
| `BaseModules/Mediator/` | Empty directory | Deprecated or unused |
| `CommonModules/Proxy/` | Minimal content | Verify necessity |
| `CommonModules/ReCaptch/` | Single purpose | Consider moving to Login module |
| `CommonModules/Animation/` | Minimal content | Verify necessity |

### 7.3 Undersized Modules

| Module | Issue | Recommendation |
|--------|-------|----------------|
| `BusinessModules/Calendar/` | 3 files | Merge with relevant module |
| `BusinessModules/Discount/` | 3 files | Merge with Recharge |
| `BusinessModules/CoreSpotlight/` | 3 files | Consider feature flag |
| `BusinessModules/HomeScreenQuickActions/` | 4 files | Merge with App module |

### 7.4 Module Division Issues

| Issue | Example | Recommendation |
|-------|---------|----------------|
| **Hybrid Swift/ObjC organization** | SwiftModules/Base/Interface vs CommonModules | Consider unified Interface module |
| **Feature scattering** | BookCity-related code in Business, Common, Route, Swift | Centralize book-related concerns |
| **Bridge proliferation** | dsBridge, WebViewJavascriptBridge, OCCallSwiftAdapter | Standardize on fewer bridges |
| **Mediator category explosion** | 9 categories in Route/ | Review if all categories are necessary |

---

## 8. Improvement Suggestions

### 8.1 Priority-Ordered Optimization Directions

| Priority | Issue | Action | Impact |
|----------|-------|--------|--------|
| **P0** | Mediator over-coupling | Split HYMediator+HYRoute.m by feature category | Reduce compile times, improve maintainability |
| **P0** | Circular dependencies via OCCallSwiftAdapter | Introduce protocol-based abstractions | Improve testability |
| **P1** | Web module dual bridge | Consolidate to single bridge implementation | Reduce code duplication |
| **P1** | Vendor source-import vs pod | Use CocoaPods for WebViewJavascriptBridge | Easier updates |
| **P2** | Swift/ObjC module boundary | Define clear module ownership | Better team separation |
| **P2** | Empty/deprecated modules | Remove BaseModules/Mediator, CommonModules/Proxy | Cleaner structure |
| **P3** | BusinessModules/Reader size | Split into sub-targets if possible | Faster incremental builds |

### 8.2 Architectural Improvement Recommendations

1. **Protocol-Oriented Mediator**:
   - Define `HYRouteTarget` protocol for business modules
   - Mediator only depends on protocol, not concrete classes
   - Reduces circular dependency risk

2. **Feature-Based Module Grouping**:
   - Consider grouping BookCity, BookDetails, Bookshelf, BookList under single "Book" umbrella
   - Reduces cross-module imports

3. **Swift/ObjC Bridge Consolidation**:
   - OCCallSwiftAdapter works but creates tight coupling
   - Consider @objc annotations directly on Swift classes
   - Reduce reliance on Dreame-Swift.h for simple calls

4. **Web Bridge Abstraction**:
   - Create `HYJSBridgeProtocol` abstraction
   - Both dsBridge and WebViewJavascriptBridge implement protocol
   - Easier to swap implementations

5. **CommonUI Extraction**:
   - Extract more CommonUI components to independent pods
   - HYBookCoverView, HYLoadingView, HYPageTabView are widely reused
   - Enable better code sharing if needed externally

### 8.3 Dependency Graph Summary

```
                    [Main/HYAppDelegate]
                           |
              [Main/HYApplicationLogicCenter]
                           |
         +-----------------+-----------------+
         |                 |                 |
   [BaseModules]    [CommonModules]    [BusinessModules]
   (Analytics)      (Advert, Web)       (BookCity, Reader,
   (Config)         (Login, User)        Bookshelf, Video)
   (Utils)          (BookInfo)
         |                 |                 |
         +-----------------+-----------------+
                           |
                    [Route/Mediator]
                    (HYMediator+HYRoute)
                           |
              +------------+------------+
              |                         |
        [SwiftModules]           [HYReaderEngine]
        (Base, BookCity,          (Framework)
         Reader, etc.)
```

---

## 9. Key Findings Summary

### 9.1 Strengths
- Well-organized CocoaPods dependencies with proper versioning
- Mediator pattern properly decouples view controllers from business logic
- Extensive use of category pattern for Mediator extensions
- Vendor libraries are minimal and well-contained

### 9.2 Concerns
- **High coupling**: Mediator imports 10+ business modules directly
- **Bidirectional Swift/ObjC**: 150+ files use OCCallSwiftAdapter creating complex dependency web
- **Large single files**: HYMediator+HYRoute.m is 90KB
- **Circular risk**: Main <-> BusinessModules through Swift bridging
- **Dual Web bridges**: Both dsBridge and WebViewJavascriptBridge in use

### 9.3 Recommendations Priority
1. Split HYMediator+HYRoute.m by feature (P0)
2. Address circular dependencies via protocols (P0)
3. Consolidate Web bridges (P1)
4. Clean up deprecated/empty modules (P2)
5. Define clear Swift/ObjC module ownership (P2)

---

**Report Generated**: 2026-04-10
**Analysis Tool**: Claude Code iOS Tech Leader