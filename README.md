# CiviCRM Member Roles Insert module

In Drupal 6, the CiviMember Roles Sync module has a minor flaw when using the
'Synchronize when membership is updated' setting, which is that roles are not
synchronized when a membership is created as part of the Drupal user registration
process.  This is possibel, for example, under these circumstances:

* The Drupal user registration form includes a CiviCRM profile with the "Current
Employer" field.
* A membership type "Type A" is configured to such that memberships are inherited
through the "Employee of" relationship.
* CiviMember Roles Sync is configured to apply the "Type A member" Drupal role
to users where the contact has a "Type A" membership.
* A new user submits the Drupal user registration form, entering the name of an
existing CiviCRM "Type A" member organization in the "Current Employer" field.

In this particular circumstance, the user contact is correctly recorded as an
employee of the member organization, and correctly receives a "Type A" membership
by virtue of that relationship; but the user doesn't receive the "Type A
membership" role.

## Module rationale
At the time of release, Drupal 6 has already reached formal End of Life.
Furthermore, this issue doesn't appear under Drupal 7. Thus the value of a patch
to CiviCRM core seems small; likewise the effort to create this small module.
Feel free to talk me into submitting a patch to core.
