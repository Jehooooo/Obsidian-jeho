#  Add Demo Data for All Admin Panel Tabs

Update the existing BayanihanHub Admin Panel by adding **at least 2 realistic demo records for every status/category listed below**.

## Important Rules

- Inspect the existing database schema and Admin Panel first.
    
- Use the existing backend, API, database models, authentication, and Admin components.
    
- Add demo data as actual database records, not hard-coded frontend arrays.
    
- Do not replace or delete the existing Admin and Jehosue accounts.
    
- Do not break existing relationships or foreign keys.
    
- Do not create duplicate demo records every time the seed script runs.
    
- Make the seed operation idempotent.
    
- Use realistic Philippine/community-related names, posts, requests, reports, and identity verification records.
    
- Use valid relationships between users, listings, requests, and reports.
    
- Do not expose passwords, ID documents, private information, or secrets.
    
- Clearly mark the records as demo/seed data internally if the schema supports it.
    

---

# 1. Approvals & Identity Verification Tab

Add at least **2 records per status**:

- Pending — minimum 2
    
- Approved — minimum 2
    
- Retry Required — minimum 2
    
- Rejected — minimum 2
    
- All — should automatically show the combined total
    

Expected minimum:

```text
Pending: 2
Approved: 2
Retry Required: 2
Rejected: 2
All: 8
```

Each identity verification record should include realistic data such as:

- Applicant/user.
    
- Valid Philippine ID type.
    
- ID information.
    
- Uploaded ID placeholder or valid demo file reference if required by the existing system.
    
- Verification status.
    
- Submission date.
    
- Review date, if applicable.
    
- Reviewer/Admin, if applicable.
    
- Rejection reason, if rejected.
    
- Retry reason, if retry is required.
    
- Created and updated timestamps.
    

Requirements:

- Pending records must appear in the Pending tab.
    
- Approved records must appear in the Approved tab.
    
- Retry Required records must appear in the Retry Required tab.
    
- Rejected records must appear in the Rejected tab.
    
- All records must appear in All.
    
- The tab counters must be calculated from actual backend/database data.
    
- Do not manually hard-code `(0)` or any count in the frontend.
    
- Make sure the records appear after refreshing the page.
    

---

# 2. Users Tab

Add at least **2 users per status**:

- All Users — combined total
    
- Pending — minimum 2
    
- Approved — minimum 2
    
- Suspended — minimum 2
    
- Rejected — minimum 2
    

Expected minimum:

```text
Pending: 2
Approved: 2
Suspended: 2
Rejected: 2
All Users: 8
```

Create realistic demo users with:

- Unique names.
    
- Unique email addresses.
    
- Valid user status.
    
- Profile information if required.
    
- Location information if required.
    
- Identity verification relationship where applicable.
    
- Registration date.
    
- Last active timestamp, if supported.
    
- Suspension start/end dates for suspended users.
    
- Suspension reason for suspended users.
    
- Rejection reason for rejected users.
    
- Proper role assignment as normal users, not Admin.
    

Requirements:

- Do not create additional Admin accounts.
    
- Do not modify the existing Admin account.
    
- Do not modify or delete Jehosue.
    
- Pending users must appear in Pending.
    
- Approved users must appear in Approved.
    
- Suspended users must appear in Suspended.
    
- Rejected users must appear in Rejected.
    
- All users must appear in All Users.
    
- The user status counters must come from the backend.
    
- Suspended users must have valid suspension data.
    
- Rejected users must have a valid rejection reason.
    
- All records must remain compatible with the login and approval system.
    

---

# 3. Posts / Listings Tab

Add at least **2 listings per status**:

- All Listings — combined total
    
- Active & Available — minimum 2
    
- Removed — minimum 2
    

Expected minimum:

```text
Active & Available: 2
Removed: 2
All Listings: 4
```

Create realistic listings related to BayanihanHub, such as:

- School supplies.
    
- Books.
    
- Clothes.
    
- Food.
    
- Household items.
    
- Bags.
    
- Shoes.
    
- Basic necessities.
    

Each listing should include:

- Valid owner/user relationship.
    
- Title.
    
- Description.
    
- Category.
    
- Condition.
    
- Listing type, such as Donation or Exchange.
    
- Location.
    
- Image reference or valid placeholder according to the existing image system.
    
- Status.
    
- Posted date/time.
    
- Created and updated timestamps.
    

Requirements:

- Active & Available listings must appear in the active tab.
    
- Removed listings must appear in Removed.
    
- All listings must show the combined total.
    
- Removed listings must use the existing soft-delete/removal logic.
    
- Do not permanently delete records unless the current architecture requires it.
    
- Removed listings must not appear in the public Browse page.
    
- Active listings must remain visible in Browse if all other conditions are satisfied.
    
- Counters must come from actual backend data.
    

---

# 4. Requests Tab

Add at least **2 requests per status**:

- All Requests — combined total
    
- Active & Open — minimum 2
    
- Removed / Cancelled — minimum 2
    

Expected minimum:

```text
Active & Open: 2
Removed / Cancelled: 2
All Requests: 4
```

Create realistic community requests such as:

- Request for school supplies.
    
- Request for books.
    
- Request for clothes.
    
- Request for food.
    
- Request for household essentials.
    
- Request for learning materials.
    

Each request should include:

- Valid requester/user relationship.
    
- Title.
    
- Description.
    
- Category.
    
- Location.
    
- Request status.
    
- Posted date/time.
    
- Created and updated timestamps.
    
- Removal/cancellation reason where applicable.
    

Requirements:

- Active & Open requests must appear in the active tab.
    
- Removed/Cancelled requests must appear in the Removed / Cancelled tab.
    
- All Requests must show the combined total.
    
- Removed or cancelled requests must not appear as active public requests.
    
- Use the existing request status values.
    
- Do not invent a new status if an equivalent already exists.
    
- Counters must be dynamically calculated from backend data.
    

---

# 5. Reports Tab

Add at least **2 reports per status**:

- All Reports — combined total
    
- Pending — minimum 2
    
- Under Review — minimum 2
    
- Resolved — minimum 2
    
- Dismissed — minimum 2
    

Expected minimum:

```text
Pending: 2
Under Review: 2
Resolved: 2
Dismissed: 2
All Reports: 8
```

Create realistic demo reports involving existing demo users and listings.

Each report should include:

- Reporter/user.
    
- Reported user, listing, or request.
    
- Report type.
    
- Reason.
    
- Description.
    
- Report status.
    
- Created date/time.
    
- Reviewer/Admin where applicable.
    
- Review date where applicable.
    
- Resolution notes where applicable.
    
- Dismissal reason where applicable.
    
- Proper foreign-key relationships.
    

Requirements:

- Pending reports appear in Pending.
    
- Under Review reports appear in Under Review.
    
- Resolved reports appear in Resolved.
    
- Dismissed reports appear in Dismissed.
    
- All reports show the combined total.
    
- Reports must be visible in the Admin Panel only.
    
- Do not expose reporter identity publicly.
    
- Use the existing report and moderation schema.
    
- Do not create invalid reports pointing to nonexistent users or posts.
    
- Counters must come from actual backend data.
    

---

# 6. Seed Data Design

Create a reusable seed script or migration using the project’s existing backend technology.

The seed process must:

- Detect existing records before inserting.
    
- Avoid duplicate demo users.
    
- Avoid duplicate demo listings.
    
- Avoid duplicate demo requests.
    
- Avoid duplicate reports.
    
- Avoid duplicate identity verification records.
    
- Use stable demo email patterns or internal seed identifiers.
    
- Run safely more than once.
    
- Preserve existing production/user data.
    
- Use database transactions.
    
- Roll back if a required relationship fails.
    
- Respect foreign keys.
    
- Use the existing password hashing method if passwords are needed.
    
- Never store plain-text passwords.
    

Suggested internal seed label:

```text
BAYANIHANHUB_ADMIN_DEMO_SEED
```

Do not display this label to normal users unless useful for Admin testing.

---

# 7. Fix Admin Tab Counters

The Admin Panel currently displays counters such as:

```text
Pending (0)
Approved (0)
All (0)
```

Update the implementation so every counter is dynamically retrieved from the backend.

Requirements:

- Do not hard-code counts.
    
- Do not calculate counts only from the currently loaded frontend page if pagination is enabled.
    
- Use accurate backend count queries.
    
- Apply the correct status filters.
    
- Ensure All counts include all records.
    
- Ensure status counts do not include deleted or unrelated records incorrectly.
    
- Refresh counters after:
    
    - Approving a user.
        
    - Rejecting a user.
        
    - Requesting retry.
        
    - Suspending a user.
        
    - Restoring a user.
        
    - Removing a listing.
        
    - Restoring a listing.
        
    - Cancelling a request.
        
    - Resolving a report.
        
    - Dismissing a report.
        

---

# 8. Admin UI Requirements

Ensure every tab displays:

- Correct dynamic count.
    
- Correct records.
    
- Loading state.
    
- Empty state.
    
- Error state.
    
- Pagination if already supported.
    
- Search if already supported.
    
- Filters if already supported.
    
- Correct status badges.
    
- Correct action buttons.
    
- Responsive layout.
    

Do not display `(0)` when records exist.

Make sure the following labels are displayed exactly:

## Approvals & Identity Verification

```text
Pending
Approved
Retry Required
Rejected
All
```

## Users

```text
All Users
Pending
Approved
Suspended
Rejected
```

## Posts

```text
All Listings
Active & Available
Removed
```

## Requests

```text
All Requests
Active & Open
Removed / Cancelled
```

## Reports

```text
All Reports
Pending
Under Review
Resolved
Dismissed
```

---

# 9. Verification Checklist

After implementation:

- Run the backend.
    
- Run the frontend.
    
- Log in as Admin.
    
- Open Approvals & Identity Verification.
    
- Confirm at least 2 records appear in every status.
    
- Confirm All shows at least 8 records.
    
- Open Users.
    
- Confirm at least 2 users appear in every status.
    
- Confirm All Users shows at least 8 users.
    
- Open Posts.
    
- Confirm at least 2 active listings and 2 removed listings.
    
- Open Requests.
    
- Confirm at least 2 active requests and 2 removed/cancelled requests.
    
- Open Reports.
    
- Confirm at least 2 reports in every report status.
    
- Refresh every page.
    
- Confirm records and counters remain correct.
    
- Test each tab on mobile, tablet, and desktop.
    
- Confirm no data is hard-coded in the frontend.
    
- Confirm no duplicate records are created after rerunning the seed.
    
- Confirm existing Admin and Jehosue accounts remain intact.
    
- Confirm public users cannot access Admin-only records.
    
- Confirm removed listings and requests are not incorrectly shown as active.
    
- Confirm all relationships and foreign keys are valid.
    

## Final Result

The Admin Panel must contain realistic demo data with accurate dynamic counters and working tabs:

```text
Approvals & Identity Verification:
Pending (2)
Approved (2)
Retry Required (2)
Rejected (2)
All (8)

Users:
All Users (8)
Pending (2)
Approved (2)
Suspended (2)
Rejected (2)

Posts:
All Listings (4)
Active & Available (2)
Removed (2)

Requests:
All Requests (4)
Active & Open (2)
Removed / Cancelled (2)

Reports:
All Reports (8)
Pending (2)
Under Review (2)
Resolved (2)
Dismissed (2)
```

The exact totals may be higher if existing valid records are preserved, but every listed status must contain at least 2 records.