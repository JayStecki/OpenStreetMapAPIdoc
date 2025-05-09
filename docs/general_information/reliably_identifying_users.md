[API v0.6](info.md) includes the numeric user ID ```uid``` of the account in addition to the display name(1).
{ .annotate }

1. The previous API v0.5 returned only the user display name. The user can update this at any time and there is no history stored for display name changes. This means there was no way to reliably identify which user made a specific change.

``` xml title="userID_example.xml" linenums="1"
<node id="68" ... user="fred" uid="123"/>
```

This still requires the user to have made his edits public(1).
{ .annotate }

1. User ID ```uid``` for users who have previously made anonymous changes will not be visible.

!!! note "OpenStreetMap Foundation Board recommendation."
    In accordance with the recommendation, anonymous edits are no longer allowed. 