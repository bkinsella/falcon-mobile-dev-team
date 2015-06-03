#DaVita Styleguide for iOS VoiceOver Implementation

VoiceOver is available to help users with visual impairments use their iOS-based devices. The UI Accessibility programming interface, introduced in iOS 3.0, helps developers make their applications accessible to VoiceOver users. Briefly, VoiceOver describes an application’s user interface and helps users navigate through the application’s views and controls, using speech and sound.

**To be useful, accessible user interface elements must provide accurate and helpful information about its name, behavior, value, and type. VoiceOver speaks this information to users, and it is coded using iOS Accessibility Attributes.**

####TABLE OF CONTENTS
* [Creating Useful UI Accessibility Labels and Hints](#creating-useful-ui-accessibility-labels-and-hints)
* [Best Practices for all VoiceOver Attributes](#best-practices-for-all-voiceover-attributes)
* [Labels](#labels)
* [Resources](#resources)

##Creating Useful UI Accessibility Labels and Hints

* **Label.** A short, localized word or phrase that succinctly describes the control or view, but does not identify the element’s type. Examples are “Add” or “Play.”
 * Labels need to be provided to the Developer in almost all instances.
* **Hint.** A brief, localized phrase that describes the results of an action on an element. Examples are “Adds a title” or “Opens the shopping list.”
 * Hints are rarely used, and only in situations where a user may easily get confused.
* **Traits.** A combination of one or more individual traits, each of which describes a single aspect of an element’s state, behavior, or usage. For example, an element that behaves like a button should have the Trait of “Button.” Furthermore, if that Button is disabled, then it is given the Trait of
“dimmed.”
 * Traits are rarely provided by the Copy Editor to the Developer, and should only be used if a control or view will be used in a non-standard way. For example, if the interaction calls for a Header to be tapped to perform an action, then you will want the Trait to be “Button” so the user knows it is actionable.
*	**Value.** The current value of an element, when the value is not represented by the label. For example, the label for a slider might be “Weight” but its current value might be “150.”
 * Values are rarely provided by the Copy Editor to the Developer, but are needed by Testers to ensure that the value VoiceOver gives matches what is on the screen.

## Best Practices for all VoiceOver Attributes

* **Capitalize the initial letter.** All other words should be in lower case (except when using acronyms or pronouns). This helps VoiceOver read the label with the appropriate inflection.
* **When using acronyms, make sure UPPERCASE is used for all characters.** This will help VoiceOver spell out the acronym. (If lowercase is used, VoiceOver is more likely to pronounce the acronym as a word.) An alternative to using all UPPERCASE is to place a space between each character to ensure VoiceOver spells out the letters.
* **You can use capitalization and spacing to force VoiceOver to pronounce acronyms correctly.** For example, ID card is pronounced “Id card,” but I D card is pronounced correctly with the letters I and D being read individually.
* **Avoid ending with a period.** Labels and hints are not sentences.
* **Avoid concatenation.** A space should always be placed between words (for example, use E Card, not ecard). If you have to concatenate, then uppercase the initial letter of each word, for example CoPay).
* **If a pause is needed, include a comma (,) at the place where you want VoiceOver to pause.**

## Labels

* This guide is only for providing the correct copy for the *UI Accessibility* Label. Only a screen reader (such as VoiceOver) will speak this hidden label. These labels will not be displayed visually on the application’s interface.
* **Labels very briefly describe the control, or where the control will take the user.** Ideally, the label consists of a single word, such as Dashboard, Add, Play, Delete, Search, Favorites, or Volume. In some cases, two words are necessary, such as Actions menu, or Add appointment.
* **The label should match what is visible on the screen.** If the text in the label is too long, and the visual display shows an ellipsis (…), VoiceOver should read the entire text that would be shown.
* **Labels should never include the type of control or view.** For example, if the component is a button, do not include the word *button* in the label. (This is because the type information is contained in the traits attribute of the element, and the user would hear something like “Delete button button”).
* **Labels for text fields should always include the text seen in the visual display.** For example, if text above a field says “Last name,” then the label for the field should be “Last name.”
* *Labels for buttons should never include the word “icon.”** This is because it is not an icon, it is a button.
* **The DaVita logo image should always have the label “DaVita logo.”**

####BACK BUTTONS

Back buttons are a standard iOS component. When implementing a Back Button, use a standard UIKit Back Button whenever possible. This way, VoiceOver will always state that it is a “Back Button” trait by default.

* **Standard Control.** When implementing a standard UIKit Back Button, simply use a label for where the Back button will take you. For example, if the Back Button takes you to the Dashboard, label it “Dashboard.” VoiceOver will then say “Dashboard Back Button.” Using the standard component "Back Button" is also beneficial because VoiceOver has a gesture that allows the user to activate the "Back Button" from anywhere on the current screen without having to actually locate it.
* **Custom Control.** If you do not implement a standard UIKit Back Button, then you must include the word “Back” in the label. For example, if it goes to the Dashboard, label it “Dashboard, Back.”

####HINTS

The hint attribute describes the results of performing an action on a control or view. You should provide a hint only when the results of an action are not obvious from the element’s label.

* **Hints should rarely be used.** If you are using them for more than 10% of the controls, you are using them too much.
* **Always place essential information in the label, and not the hint.** The VoiceOver users often have the hint functionality turned off, and so will not hear the hint.
* **The hint should be a very brief phrase that begins with a verb that names the results of the action.** For example, “Plays the song” or “Purchases the item.”
* **Avoid beginning the phrase with the imperative form of a verb.** This can make the hint sound like a command. For example, do not create a hint such as “Play the song” or “Purchase the item.”
* **Do not repeat the action type in the hint.** For example, do not create hints such as “Tap to play the song” or “Tapping plays the song.”
* **Do not repeat the control or view type in the hint.** For example, do not create hints such as “Plays the song in the row” or “Button that adds a contact name.” This is because standard components include hints already (although they can be customized if necessary).

####STRUCTURE

* **The Header or Title for each page should always be coded so the trait is a heading.**
* **Attempt to implement Headings to make navigation easier whenever the user needs to scroll down read all the content.** If there is a screen with more than two pages of content, attempt to implement Headings to make navigation easier. For example, if there is an FAQ page of plain text (where the Questions are not links), include each Q as a Heading.

##Resources

* [Accessibility Programming Guide for iOS](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/iPhoneAccessibility/Making_Application_Accessible/Making_Application_Accessible.html#//apple_ref/doc/uid/TP40008785-CH102-SW6 )
* [iOS Developer Site on Accessibility](https://developer.apple.com/library/ios/#documentation/UserExperience/Conceptual/iPhoneAccessibility/Introduction/Introduction.html)
* [Introduction for iOS Developers](http://mattgemmell.com/2010/12/19/accessibility-for-iphone-and-ipad-apps/)

---

![DaVita Mobile Community of Excellence Logo](../images/MCOE_logo.png)

**Updated:** November 2014
