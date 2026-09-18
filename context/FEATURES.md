# Features and specification

Status: ACTIVE. Copy and revise your own HW2 FEATURES.md here.

## Context
When people are traveling, or perhaps once they have returned from a trip, they want to casually share their experiences in a low stakes/pressure way with audiences to 1) have a travel log for themselves of their travel events and 2) keep their friends updated.

## Users
For full user profile research, see <a href="USERS.md">View User Profiles</a>.

**PROFILE-01:** Wants a fast way to aggregate travel highlights for close friends without bombarding them over messaging apps or feeling pressure for immediate responses.

**PROFILE-02:** Enjoys documenting trips visually with high aesthetic standards without the strict image count limits or high-pressure environment of traditional social platforms.

## Scope
Included behavior and explicit non-goals:

**Included behavior**
* Users select a category (Food, Activity, Landmark) and choose from previously pictures items what they liked more in that category from that trip to auto-calculate an item score.
* Closing out a completed trip then allows the user to rank that city/location against past trips including a map that shows their top ranked cities. 
* Trip logs require start/end dates and have a "Traveled With" companion tag so tagged friends can link trip dates while still having their own rankings.
* Shareable link prompted after you finish out a trip to share with friends.

**Explicit non-goals:**
* No sort of traveling booking done through the application.
* No chat in app, only commenting. 

## Behavior
Sequence, conditions, actions, and visible outcomes:
* **Sequence:** The user starts a trip by selecting a location and logging start dates. As they progress through their trip, they add pictures of their activities, landmarks they visit, and food they eat. They then rank each thing in their respective categories and at the end they can see their food rank list, etc. Finally, they can mark their trip complete and rank the city against their over trips. The user is also prompted at the end, something along the lines of: "Yay! Trip ended! Share with friends?"
* **Conditions:** A user can't rank things unless they have other thinks to rank against (activities and city)
* **Actions:** They input their start date, select category, input pictures, write reviews, rank spots. They can tag companions and rank the final city.
* **Visible outcomes:** It calculates a rank number for each thing and city rankings after you select. It also shows the cities you've visited on a map. A scrolling feed of your own with reviews and things you've done compiled in one place.

## Constraints
* **Platform:** App ideally that would be supported on IOS and Android.
* **Data:** Share what you want to, need email/phone number to register account.
* **Privacy:** Location sharing so you don't have to manually input city.
* **Relevant limits:** Ability to work offline, if not able to upload then at least have save draft options. 

## Acceptance
- Ubiquitous: The system shall display the category, travel spot name, uploaded photo, and review text together on every rendered review card.
- Event-driven: When the user selects an image file, the system shall render a photo preview directly above the review text box.
- State-driven: While review data exists in browser memory, the system shall retain all saved review cards in storage.
- Unwanted: If the user attempts to submit a review without providing a location name, selecting an image file, or typing review text, the system shall display an  error message reading letting the user know what they are missing/what to add (photo, review, name)
- Optional: Where users select "Traveled with", the system shall prompt the companion to start the same trip with them.

## Kano Hypotheses
*The bolded feature is the one focused on in HW3*
| Feature ID | Feature | Kano hypothesis | Segment / date | Evidence and reasoning |
|---|---|---|---|---|
| F-01 | Category-Based Ranking | Must-be | 01, 02 | Main app usage, people can rank things they've done |
| **F-02** | Text Reviews | Must-be | 01, 02 | Main app usage, people want to share their thoughts on events |
| F-03 | Upload/Sharing | Performance | 01 | Sharing with friends over text |
| F-04 | "Traveled with" | Attractive | 01, 02 | Can coincide their updates with their friends that they travel with |
| F-05 | Activity Feed | Indifferent | 02 | Can appeal to the social and friend sharing aspect, but not to make that a priority in the app |
| F-06 | In-App Photo Editing | Indifferent | 01, 02 | Neither expressed a desire for it, but common for many social-related apps |

## Verification

| Criterion | Steps and input | Expected result | Observed result | Status | Evidence / commit |
|---|---|---|---|---|---|
| Your selected ID | Reproducible procedure | Before running | Actual observation | PASS / FAIL / CANNOT TEST / DEFERRED | Link |
| **EARS-1** | Submit a review with spot name "Eiffel Tower", an attached photo, and review text "Great view of city from top". | Review renders with spot title, uploaded photo, and review text together in the saved reviews list. | Review card rendered correctly containing spot name, image, and text. | PASS | [`app.js#L38`](app.js#L38) |
| **EARS-2** | Select a JPEG image file using the file input before submitting. | Image preview container appears directly above the review text box displaying the selected photo. | Image preview displayed above text box immediately upon file selection. | PASS | [`app.js#L82`](app.js#L82) |
| **EARS-3** | Save a review, then execute a hard browser tab refresh in Codespaces. | The saved photo review card remains visible in the list feed with image and text intact. | Review card persisted after full page reload. | PASS | [`app.js#L14`](app.js#L14) |
| **EARS-4** | Leave all input fields blank and click the "Save Review" submit button. | Inline error message reading "Please provide a name, select an image, and write a review." displays and form submission stops. | Red error text displayed, submission halted, no empty card created. | PASS | [`app.js#L112`](app.js#L112) |
| **EARS-5** | Fill out form fields with a valid photo review and click "Save Review". | Spot name input clears, photo selection resets, image preview hides, and review text box empties. | All form fields cleared and preview container hidden automatically upon submit. | PASS | [`app.js#L125`](app.js#L125) |
| **EARS-6** | Upload a non-image file (e.g., document or PDF) and click "Save Review". | System displays an error message reading "Please select a valid image file" and halts submission. | The file selector permitted document uploads, resulting in a broken image card rendering. | FAIL | [`app.js#L82`](app.js#L82) |
| **EARS-07** | Attempt to post a social comment on a saved photo review card. | Interactive social comment box allows friends to post threaded replies under the review. | Feature postponed to backend release per ADR-001; client-side MVP supports local logging only. | DEFERRED | [`ADR-001.md`](context/ADR-001.md) |


| Criterion | Steps and Input | Expected Result | Observed Result | Status | Evidence / Commit |
|---|---|---|---|---|---|
| **EARS-1** | Submit a review with spot name "Eiffel Tower", an attached photo, and review text "Great view of city from top". | Review renders with spot title, uploaded photo, and review text together in the saved reviews list. | Review card rendered correctly containing spot name, image, and text. | PASS | [`app.js#L38`](../app.js#L38) |
| **EARS-2** | Select a JPEG image file using the file input before submitting. | Image preview container appears directly above the review text box displaying the selected photo. | Image preview displayed above text box immediately upon file selection. | PASS | [`app.js#L82`](../app.js#L82) |
| **EARS-3** | Save a review, then execute a hard browser tab refresh in Codespaces. | The saved photo review card remains visible in the list feed with image and text intact. | Review card persisted after full page reload. | PASS | [`app.js#L14`](../app.js#L14) |
| **EARS-4** | Leave all input fields blank and click the "Save Review" submit button. | Inline error message reading "Please provide a name, select an image, and write a review." displays and form submission stops. | Red error text displayed, submission halted, no empty card created. | PASS | [`app.js#L112`](../app.js#L112) |
| **EARS-5** | Fill out form fields with a valid photo review and click "Save Review". | Spot name input clears, photo selection resets, image preview hides, and review text box empties. | All form fields cleared and preview container hidden automatically upon submit. | PASS | [`app.js#L125`](../app.js#L125) |
| **EARS-6** | Upload a non-image file (e.g., document or PDF) and click "Save Review". | System displays an error message reading "Please select a valid image file" and halts submission. | The file selector permitted document uploads, resulting in a broken image card rendering. | FAIL | [`app.js#L82`](../app.js#L82) |
| **EARS-07** | Attempt to post a social comment on a saved photo review card. | Interactive social comment box allows friends to post threaded replies under the review. | Feature postponed to backend release per ADR-001; client-side MVP supports local logging only. | DEFERRED | [`ADR-001.md`](ADR-001.md) |
